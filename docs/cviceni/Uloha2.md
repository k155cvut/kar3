# Kartografická anamorfóza

## Zadání 

Na úvod cvičení si zopakujeme tvorbu jednoduchého kvalifikačního/klasifikačního kartogramu (Mapa 1). Hlavní náplní cvičení však bude tvorba plošné anamorfózy – geografické nespojité (Mapa 2) a spojité (Mapa 3), a schematické, tzv. Dorlingovy anamorfózy (Mapa 4). Vzhledem k tomu, že v ArcGIS Pro dosud neexistuje nástroj pro tvorbu plošné geografické spojité anamorfózy (Mapa 3), budeme tuto část úlohy řešit v QGIS. Postup tvorby kartogramu (Mapa 1) a ostatních typů anamorfózy (Mapa 2 a 4) bude představen v ArcGIS Pro, stejně jako finální kompozice map. Na závěr si ukážeme tvorbu multivariantní mapy (Mapa 5).

**S využitím software QGIS či ArcGIS vytvořte pět autorských konceptů tematických mapy na papír velikosti A4.**

1.  **Mapa 1** bude s využitím jednoduchého kvalifikačního/klasifikačního kartogramu zobrazovat vybraný jev (**náskok vítěze v %**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)
2.  **Mapa 2** bude s využitím plošné geografické nespojité anamorfózy zobrazovat vybraný jev (**počet platných voličských hlasů, náskok vítěze v %**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)
3.  **Mapa 3** bude s využitím plošné geografické spojité anamorfózy obrazovat vybraný jev (**počet platných voličských hlasů, náskok vítěze v %**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)
4.  **Mapa 4** bude s využitím plošné schematické (tzv. Dorlingovy) anamorfózy zobrazovat vybraný jev (**počet platných voličských hlasů, náskok vítěze v %**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)
5.  **Mapa 5** bude s využitím kartogramu a plošného kartodiagramu zobrazovat vybraný jev (**náskok vítěze v %, počet platných voličských hlasů, volební účast v % a vítěze 1.  kola**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)

**Zdroje dat:**\

-   polygonová vrstva obcí *(OBCE_UAP)* z ArcČR 4.1
-   výsledky prezidentských voleb z [**Veřejné databáze ČSÚ**](https://vdb.czso.cz/vdbvo2/faces/cs/index.jsf?page=vystup-objekt-parametry&z=T&f=TABULKA&sp=A&skupId=5033&katalog=34015&pvo=VOLDPR202302-OB-OR&str=v103&v=v101__VOLKOLO__1059__1){target="_blank"} dle ORP (platné hlasy, druhé kolo)

**Jednotlivá zadání**

-   viz [tabulka](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/155KAT3_Uloha2_zadani_2024.xlsx){target="_blank"}

**Hodnocení:**

-   úplnost technické zprávy (obsah TZ viz níže)
-   tematické mapy (splnění zásad tematické kartografie: správná aplikace metody, klasifikace dat, kompoziční prvky, popis)
-   max. 2 opravy (oprava vždy nejpozději do 7 dní od vrácení úlohy)
-   splněno/nesplněno

**Layout **

Ddodržujte [**zásady pro kompozici tematických map**](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/MAPK_kompozice_mapy.pdf){target="_blank"}:

-   název (co?, kde?, kdy?);
-   mapové pole;
-   legenda ([barevná stupnice](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/KAT3_stupnice_ChybejiciInterval.pdf){target="_blank"}, intervaly, diagramové měřítko);
-   grafické měřítko;
-   směrovka;
-   tiráž (jméno autora, předmět, datum vyhotovení, zdroj dat).

\

#### Postup

**Příprava dat**

-   úprava tabulky z VD ČSÚ (ponechat jen záhlaví sloupců a data) 
-   připojení upravené tabulky k vrstvě obcí v daném ORP *(nastavení Definition Query)*
-   export nové vrstvy *(Data-Export Features)*
-   výpočet nových atributů (PP_podil, AB_podil, vitez_rozdil_rel)

**Mapa 1 – jednoduchý kvalifikační/klasifikační kartogram (ArcGIS)**

-   tvorba jednoduchého kvalifikačního kartogramu viz [návod z KAT2](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/jednoduchy_kartogram.pdf){target="_blank"}
-   tvorba layoutu, vložení a úprava základních kompozičních prvků (název, legenda, grafické měřítko, směrovka, tiráž; viz [návod z KAT2](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/layout_navod.pdf){target="_blank"}
-   export mapy ve formátu PDF

**Mapa 2 - plošná geografické nespojitá anamorfóza (QGIS, ArcGIS)**

Pro výpočet nespojité geografické anamorfózy použijeme tzv. projektorovou metodu, která podobnostním zobrazením zvětší/zmenší velikost obcí tak, aby jejich výsledná plocha
odpovídala velikosti zvoleného atributu, tj. celkovému počtu voličských hlasů v našem případě. Více [viz přednáška](https://moodle-vyuka.cvut.cz/pluginfile.php/824458/mod_resource/content/1/KAR3_predn11_anamorfoza.pdf){target="_blank"} (slide 20) či [odborný článek (Olson, 1976)](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/olson1976.pdf).

**Postup:**

-   tvorba kopie vizualizované vrstvy obcí v zadaném ORP (přes *Data-Export Features*)
-   vytvoření a výpočet nového atributu "pocet_hlasu_celkem" (potřebujeme znát celkový počet voličských hlasů v dané obci, dle tohoto jevu budeme určovat novou plochu obce)
-   vytvoření a výpočet nového atributu "value_density_sqrt" (druhá odmocnina hustoty zkoumaného jevu, tj. počtu hlasů, na km^2^ původní plochy – `math.sqrt(!pocet_hlasu_celkem!/(!Shape_Area!/1000000))`
-   Nyní potřebujeme najít obce s vysokou hodnotou nově vypočteného atributu *value_density_sqrt*, z nichž vybereme tu obec, která má největší původní rozlohu. Tato obec bude sloužit jako referenční hodnota, vůči které budeme relativně zvětšovat/zmenšovat ostatní obce. Velikost této obce zůstane nezměněna. Hodnotu *value_density_sqrt* této obce pak zvolíme jako konstantu při výpočtu lineárního měřítka, na jehož základě budeme zvětšovat/zmenšovat jednotlivé obce. (postup [viz ukázka](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/Nespojit%C3%A1%20anamorf%C3%B3za%20-%20postup.png), odvození vzorce [viz ukázka](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/Nespojit%C3%A1%20anamorf%C3%B3za%20-%20odvozen%C3%AD%20vzorce.png))
-   vytvoření a výpočet nového atributu *scale_factor* (`(1/d)\*!* *value_density_sqrt!`), kde d = hodnota *value_density_sqrt* vybrané obce z předchozího kroku
-   nastavení symboliky – zaškrtnout *Allow symbol property connections* (záložka *Vary symbology by attribute*), přidat globální efekt *Scale* (vlastnosti symbolu), 
 nastavit *Scale X* a *Scale Y* dle hodnoty vypočteného atributu *ScaleFactor*
-   jednotlivé obce zároveň vizualizovat pomocí kartogramu dle náskoku vítěze v % *(Graduated colors*, *vitez_rozdil_proc)* dle stejné barevné stupnice jako byla použita na Mapě 1 (lze převzít z původní vrstvy přes *Import symbology*)
-   přidat popis obcí, zobrazit původní hranice obcí pro porovnání (umístit vrstvu nad anamorfované obce)

**Mapa 2 – Layout:**

- vytvořit kopii layoutu z předchozího cvičení
- ponecháme barevnou stupnici pro kartogram (náskok vítěze v %)
- k legendě doplníme měřítko pro anamorfózu a slovně uvedeme, jaká obec byla zvolena jako referenční 

- měřítko pro anamorfózu (tj. čtverec o určité ploše = např. 100 volebních hlasů) vypočteme z plochy obce použité jako vztažný bod (\"scale_factor\" = 1) následovně: `ctverec_km2 = *100/!pocet_hlasu_celkem!\*(!shape_Area!/1000000)` – výsledná hodnota udává velikost plochy (v km^2^), která odpovídá 100 voličským hlasům – je nutné přepočítat na cm/mm dle měřítka mapy, abychom daný obrazec o správných rozměrech vytvořili v layoutu *(Insert > Graphics)*

- do legendy přidáme také symboly pro původní a anamorfované hranice obcí


**Mapa 3 – plošná geografická spojitá anamorfóza (QGIS)**

-   generalizace hranic vrstvy obcí *(Simplify Polygon)*
-   export vrstvy obcí zadaného ORP do geojson *(Feature to JSON)*
-   pro nový projekt v QGIS nastavit Křovákovo zobrazení, přidání vrstvy obcí, instalace pluginu *cartogram3*
-   použití pluginu *cartogram3* (videonávod [**zde**](https://www.youtube.com/watch?v=tggv-3XlDVU){target="_blank"}, popis
    pluginu [**zde**](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/MetodyTK_TvorbaMap1-0.pdf){target="_blank"})
-   export výsledné vrstvy do zvoleného formátu *(ESRI Shapefile)* pro potřeby finálního zpracování mapy v ArcGIS Pro
-   ArcGIS Pro – přidat popis obcí, zobrazit původní hranice obcí pro porovnání (umístit vrstvu nad anamorfované obce)

**Mapa 3 - Layout (ArcGIS Pro):**

-   vytvořit kopii layoutu z předchozího cvičení
-   ponecháme barevnou stupnici pro kartogram (náskok vítěze v %)
-   k legendě doplníme měřítko pro anamorfózu 
-   měřítko pro anamorfózu (tj. čtverec o určité ploše = např. 100 volebních hlasů) vypočteme z nové anamorfované plochy celého ORP a celkového počtu hlasů za ORP `ctverec_km2 = 100/!pocet_hlasu_celkem_ORP! - !shape_Area_ORP!/1000000)` výsledná hodnota udává velikost plochy (v km2), která odpovídá 100 voličským hlasům – je nutné přepočítat na cm/mm dle měřítka mapy, abychom daný obrazec o správných rozměrech vytvořili v layoutu (Insert-Graphics)
-   do legendy přidáme také symboly pro původní a anamorfované hranice obcí

**Mapa 4 – Schematická (Dorlingova/Demersova) anamorfóza (ArcGIS Pro)**


-   download toolboxu [Graphical Cartogram](https://carto.maps.arcgis.com/home/item.html?id=f36049083ce947b08935a67f7184863d) z Esri galerie.
-   přidání staženého toolboxu do projektu ArcGIS Pro (*Toolbox – Add New*)
-   použití nástroje *Create Cartogram,* který se po importu toolboxu objeví mezi nástroji geoprocessingu (na vstupu bude vrstva obcí, jako *Property* vybrat sumu platných hlasů a tvar lze zvolit kruh či čtverec
-   z důvodu navazující tvorby legendy je však nutné do vrstvy obcí pomocí editace přidat tři polygony (umístit je s jistým odstupem od ORP). Není nutné u nich vyplnit jiné atributy než sumu platných hlasů: zde by měly být obsaženy tři hodnoty vhodně vystihující rozsah hodnot tohoto pole (např. 50, 500, 1000 – pokud minimum = 63 a maximum = 987 nebo 5781). Ideálně tedy volit hodnotu těsně pod minimem a těsně nad maximem, avšak pokud je hodnota maxima velmi odlehlá, není (vzhledem k zachování rozumných rozměrů legendy) nutné obsáhnout velikost symbolu pro takovou hodnotu).
-   jakmile nástroj proběhne, vznikne nová anamorfovaná vrstva, u níž pomocí výběru označíme tři přidané prvky pro legendy a pomocí nástroje *Feature to Graphic* překonvertujeme na grafické objekty. S nimi lze pracovat přes lištu *Graphic:* umístíme kruhy tak, aby měly společný dotyk v jejich nejspodnějším bodě a nastavíme transparentní vnitřní výplň (v Layoutu k nim dodáme popisky a linky, inspirace pro legendu například [zde](https://www.esri.com/arcgis-blog/wp-content/uploads/2023/06/cartogram3.jpg))
-   dále je potřeba nastavit barvu pro výplň jednotlivých kruhů (analogicky k předchozím mapám), avšak nástroj *Create Cartogram* bohužel nezachovává veškeré atributy původní vrstvy, proto je nutné nejprve pomocí *Join* připojit informace o procentním rozdílu ve výsledku volebních kandidátů z původní vrstvy obcí (připojit obce a jejich anamorfované verze na základě ID, které zůstává nezměněno).
-   legendu vytvořte pomocí nástroje <https://radiat.pythonanywhere.com/> (export do SVG a v layoutu vložit jako grafický objekt; poté nesmíte měnit velikost, aby byla legenda platná!)

**Mapa 5 – Multivariate mapping**

-   jako podklad využijeme kvalifikační kartogram (mapa 1)
-   k vrstvě obcí přidáme data o vítězi prvního kola z [databáze ČSÚ](https://vdb.czso.cz/vdbvo2/faces/cs/index.jsf?page=vystup-objekt-parametry&z=T&f=TABULKA&sp=A&skupId=5033&katalog=34015&pvo=VOLDPR202302-OB-OR&str=v103&v=v101__VOLKOLO__1059__1) (nutná úprava v Excelu, ke každé obci stačí vhodnou funkcí vypočíst jméno vítěze 1. kola prezidentské volby)
-   dále se ujistíme, že vrstva obsahuje volební účast (za 2. kolo v %) a počet hlasujících voličů
-   tuto vrstvu převedeme pomocí *Feature to point* na bodovou vrstvu
-   v atributové tabulce přidáme dva sloupce typu string: první bude obsahovat textový přepis volební účasti zaokrouhlený na 1 desetinné místo, druhý bude obsahovat [název barvy](https://www.w3.org/TR/css-color-3/#svg-color) zvolené pro vítězného kandidáta 1. kola (při výběru barvy kontrolujte čitelnost nad celou paletou divergentní stupnice podkladového kartogramu)
-   v symbolice povolit *Allow symbol property connections\
-   primární symboliku nastavit na *Graduated symbols*, přičemž samotný znak (*Template*) nastavit na *Text Marker* (kategorie ArcGIS 2D)
-   Ve vlastnostech symbolu nastavit propojit *Text string* s atributem obsahujícím textový přepis procent volební účasti; poté definovat vhodné velikosti pro každou kategorii, font, halo, apod.
-   Ve vlastnostech symbolu propojit *Color* s atributem obsahujícím definovaný název barvy pro vítěze 1. kola\
-   zvolit vhodnou minimální a maximální velikost symbolu
-   přidat anotace, vytvořit legendu a dokončit layout
    



!!! warning "K odevzdání"

### Požadované výstupy

Pomocí Moodle **elektronicky** odevzdejte v **zazipovaném souboru**:

**1) Technickou zprávu (PDF)**, která bude obsahovat:

-   stručný postup řešení úlohy (použitý sw, nástroje apod.),
-   zdůvodnění případných "neobvyklých" kroků v úpravě dat (např. výpočet škálovacího faktoru apod.),
-   vztah pro výpočet velikosti prvků při tvorbě plošné geografické nespojité anamorfózy + zdůvodnění,
-   tabulku s daty a mezivýpočty,
-   zhodnocení vhodnosti použití aplikovaných metod (která je názornější, lépe vystihuje skutečnost apod.),
-   zhodnocení vhodnosti softwaru pro tvorbu dané metody,
-   **všechny vytvořené tematické mapy na formát A4 **(lze i jako samostatná PDF);

**2) MPKX package** pro všechny mapy či kompletní projekt **APRX s GDB se všemi použitými daty**.


### Pro inspiraci

![kvalifikační kartogram](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/kvalifika%C4%8Dn%C3%AD.png){.img-fluid .atto_image_button_text-bottom width="500px"}

![nespojitá anamorfóza](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/nespojit%C3%A1.png){.img-fluid .atto_image_button_text-bottom width="500px"}

![spojitá anamorfóza](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/spojit%C3%A1.png){.img-fluid .atto_image_button_text-bottom width="500px"}

![dorlingova anamorfóza](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/dorling.png){.img-fluid .atto_image_button_text-bottom width="500px"}

![aa](https://moodle-vyuka.cvut.cz/draftfile.php/12299/user/draft/671901552/multivariate.png){.img-fluid .atto_image_button_text-bottom width="500px"}
