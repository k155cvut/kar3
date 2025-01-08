# Pokročilé metody tematické kartografie

## Zadání 

Na úvod cvičení si zopakujeme tvorbu jednoduchého kvalifikačního/klasifikačního kartogramu (Mapa 1). Hlavní náplní cvičení však bude tvorba plošné anamorfózy – geografické nespojité (Mapa 2) a spojité (Mapa 3), a schematické, tzv. Dorlingovy anamorfózy (Mapa 4). Vzhledem k tomu, že v ArcGIS Pro dosud neexistuje nástroj pro tvorbu plošné geografické spojité anamorfózy (Mapa 3), budeme tuto část úlohy řešit v QGIS. Postup tvorby kartogramu (Mapa 1) a ostatních typů anamorfózy (Mapa 2 a 4) bude představen v ArcGIS Pro, stejně jako finální kompozice map. Na závěr si ukážeme tvorbu multivariantní mapy (Mapa 5).

**S využitím software QGIS či ArcGIS vytvořte pět autorských konceptů tematických mapy na papír velikosti A4.**

1.  **Mapa 1** bude s využitím jednoduchého kvalifikačního/klasifikačního kartogramu zobrazovat vybraný jev (**náskok vítěze v %**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)

<figure markdown>
  ![Mapa 1](../assets/Uloha2/Kartogram.png "Mapa 1"){ width=400px }
  <figcaption>Mapa 1</figcaption>
</figure>

2.  **Mapa 2** bude s využitím plošné geografické spojité anamorfózy obrazovat vybraný jev (**počet platných voličských hlasů, náskok vítěze v %**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)

<figure markdown>
  ![Mapa 2](../assets/Uloha2/Spojita.png "Mapa 2"){ width=400px }
  <figcaption>Mapa 2</figcaption>
</figure>

3.  **Mapa 3** bude s využitím plošné schematické (tzv. Dorlingovy) anamorfózy zobrazovat vybraný jev (**počet platných voličských hlasů, náskok vítěze v %**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)

<figure markdown>
  ![Mapa 3](../assets/Uloha2/Kartogram.png "Mapa 3"){ width=400px }
  <figcaption>Mapa 3</figcaption>
</figure>

4.  **Mapa 4** bude s využitím kartogramu a plošného kartodiagramu zobrazovat vybraný jev (**náskok vítěze v %, počet platných voličských hlasů, volební účast v % a vítěze 1.  kola**) dle obcí pro vybrané ORP (dle individuálního zadání, viz níže)

<figure markdown>
  ![Mapa 4](../assets/Uloha2/Multi.png "Mapa 4"){ width=400px }
  <figcaption>Mapa 4</figcaption>
</figure>

5.  **Mapa 5** bude s využitím kartogramu a kartodiagramu zobrazovat **volební účast v krajích a výsledky voleb do poslanecké sněmovny.**

6.  **Mapa 6** bude s využitím kartogramu a kartodiagramu zobrazovat **aktuální míru nezaměstnanosti a vývoj růstu mezd a průměrné ceny bytů za kvartály v krajích pro období posledních 4 let.**

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

#### Postup

**Příprava dat**

-   úprava tabulky z VD ČSÚ (ponechat jen záhlaví sloupců a data) 
-   připojení upravené tabulky k vrstvě obcí v daném ORP *(nastavení Definition Query)*
-   export nové vrstvy *(Data-Export Features)*
-   výpočet nových atributů (PP_podil, AB_podil, vitez_rozdil_rel) 

!!! warning "K odevzdání"
    Pomocí Moodle **elektronicky** odevzdejte v **zazipovaném souboru**:

    1.Technickou zprávu (PDF), která bude obsahovat:

    -   stručný postup řešení úlohy (použitý sw, nástroje apod.),
    -   zdůvodnění případných "neobvyklých" kroků v úpravě dat (např. výpočet škálovacího faktoru apod.),
    -   vztah pro výpočet velikosti prvků při tvorbě plošné geografické nespojité anamorfózy + zdůvodnění,
    -   tabulku s daty a mezivýpočty,
    -   zhodnocení vhodnosti použití aplikovaných metod (která je názornější, lépe vystihuje skutečnost apod.),
    -   zhodnocení vhodnosti softwaru pro tvorbu dané metody,
    -   **všechny vytvořené tematické mapy na formát A4 **(lze i jako samostatná PDF);

    2.  MPKX package pro všechny mapy či kompletní projekt **APRX s GDB se všemi použitými daty**.