<script>
  MathJax = {
    tex: {inlineMath: [['$', '$'], ['\\(', '\\)']]},
    svg: {fontCache: 'global'}
  };
</script>
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js">
</script>

# Generování modelů terénu a vrstevnicového plánu z dat LLS

Tento návod popisuje postup pro vytvoření vrstevnicového plánu s ekvidistancí 2 m z dat DMR 5G (Digitální model reliéfu 5. generace) ve formátu LAS, s následnou vizualizací a exportem.

### Převod dat LAS do formátu zpracovatelného v ArcGIS Pro

Data DMR 5G jsou často dodávána ve formátu LAS (LASer file format), což je binární formát pro ukládání dat z laserového skenování. ArcGIS Pro s tímto formátem umí pracovat, ale pro efektivnější zpracování, zejména pro generování rastrů nebo TIN, je vhodné nejprve vytvořit **LAS Dataset**. V okně *Catalog* klikneme pravým tlačítkem na složku, kam chceme LAS Dataset uložit, zvolíme *New* a následně *LAS Dataset*. Vytvoří se prázdný LAS Dataset, do kterého následně přidáme LAS soubory pomocí pravého tlačítka a volby *Add Files*. LAS Dataset pak slouží jako odkaz na původní LAS soubory a umožňuje s nimi pracovat, aniž by se musely kopírovat nebo konvertovat do jiných formátů. Pokud jsou zdrojem soubory LAZ (nezaměňovat s *ZLAS*, což je pouze zazipovaný soubor LAS), je možné je převést funkcí *Convert LAS*.

### Převod do výškového rastru nebo do TIN

Pro generování vrstevnic je potřeba data převést do formátu, se kterým umí pracovat nástroje pro tvorbu vrstevnic – tedy do rastru (formát *Raster*) nebo do TIN (Triangulated Irregular Network). Pokud pracujeme s daty z laserového skenování (LAS), je obvykle efektivnější a přesnější použít **TIN**. Pro převod LAS Datasetu do TIN použijeme nástroj *LAS Dataset To TIN* (v toolboxu *3D Analyst Tools* -> *Conversion*). Nastavíme vstupní LAS Dataset a výstupní umístění pro TIN. Pokud bychom chtěli použít rastr, použili bychom nástroj *LAS Dataset To Raster*. Při použití rastru je vhodné nastavit rozlišení rastru dostatečně podrobné, aby nedošlo k redukci přesnosti vstupních dat, ale zároveň ne příliš, aby se pouze neúměrně nezvětšila velikost rastru. Pro data DMR postačí rozlišení 0,2 m.

### Generování vrstevnic pomocí funkce *Contour* / *Surface Contour*

Pro generování vrstevnic použijeme nástroj *Contour* (v toolboxu *Spatial Analyst Tools* > *Surface*), pokud jsme použili rastr, nebo *Surface Contour* (v toolboxu *3D Analyst Tools* > *Raster and TIN Surface*), pokud pracujeme s TIN. V obou případech nastavíme vstupní data (rastr nebo TIN) a *Contour interval* (ekvidistanci) na 2 m. V tomto kroku je důležité si uvědomit pravidlo pro volbu intervalu vrstevnic, které se často uvádí jako $I = \frac{M}{5000}$. <br />Je-li tedy např. požadováno měřítko plánu  1 : 10 000, vhodný interval vrstevnic by činil 2 m.

### Proředění a vyhlazení vrstevnic

Vygenerované vrstevnice mohou být v některých oblastech příliš husté a obsahovat drobné, neestetické detaily. Pro proředění vrstevnic a odstranění těch, které jsou z pohledu měřítka mapy příliš drobné, můžeme použít obyčejný cenzální výběr. Uvažujeme-li např. vrstevnici ve formě kroužku o průměru 1 mm jako minimální, která se ještě má zobrazit, můžeme délku přepočíst měřítkem – tedy $d = M \pi p$, kde <br /> $d$ je prahová hodnota délky v *m*, $M$ měřítkové číslo v tisících a $p$ prahový průměr kroužku v *mm*,<br /> a použít ji jako nejmenší délku, kterou ještě budeme zobrazovat.

!!! tip "Některé drobné vrstevnice zachovat chceme"
    Zde je dobré prověřit, zda se tyto drobné vyfiltrované vrstevnice nenacházejí na vrcholech kopců nebo dnech proláklin, a případně je z výběru odebrat.

Pro následné kartografické **vyhlazení** vrstevnic použijeme nástroj *Smooth Line* (také v *Cartography Tools* -> *Generalization*). Zde můžeme zvolit metodu vyhlazení (vhodná je PAEK) a toleranci vyhlazení. Tolerance závisí na měřítku mapy a stylu terénu a nelze ji jednoznačně odvodit – lepší je empiricky zkoušet, kdy vrstevnice vypadají *kartograficky pěkně*. Vhodné je začít např. s hodnotou M v tisících a případně postupně toleranci zvětšovat. 

### Vizualizace vrstevnic

Pro **zvýraznění každé páté vrstevnice** (tedy např. pro vrstevnice po 2 m se jedná o ty s výškou dělitelnou 10) použijeme symboliku založenou na dotazech. Vlastnosti vrstvy vrstevnic, záložka *Symbology*, sekce *Primary symbology*, zvolíme *Unique Values*. Vytvoříme dva symboly: jeden pro běžné vrstevnice a druhý pro zvýrazněné. Pro zvýrazněné vrstevnice použijeme dotaz (Query) `"VYSKA" MOD 10 = 0` (za předpokladu, že pole s výškou vrstevnice se jmenuje *VYSKA*). Nastavíme sílu linií: pro zvýrazněné vrstevnice 0,35 mm a pro běžné 0,15 mm.

### Aplikace popisu

Pro **aplikaci popisu** použijeme nástroje popsané např. [v tomto samostatném návodu](../../kar2/popisy). V okně *Label Class* nastavíme popis z pole *VYSKA*, zvolíme vhodné písmo, velikost a barvu (měla by odpovídat barvě samotných vrstevnic). Důležité je také nastavení umístění popisků podél vrstevnic. Vhodné je použít styl umístění *Contour* a případně upravit.

!!! note
    Pozor, vrstevnice podléhají specifickým konvencím pro jejich popisování. Není vhodné použít volbu *Laddering*, kterou ArcGIS implicitně zapíná – popisy se pak příliš shlukují do několika málo oblastí mapy.

### Export v měřítku na papír

Pro **export mapy** v daném měřítku na formát A4 použijeme *Layout*. Vytvoříme nový *Layout* ve formátu A4. Přidáme mapu do layoutu a nastavíme měřítko na 1 : 10 000. Následně exportujeme layout do požadovaného formátu PDF. Více v [podrobnějším postupu](../../kar2/layout)

<figure markdown>
  ![Radiální anamorfóza](../assets/Uloha2/radial.png "Radiální anamorfóza"){ width=500px }
  <figcaption>Radiální anamorfóza</figcaption>
</figure>

