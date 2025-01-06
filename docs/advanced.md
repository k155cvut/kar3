# Pokročilé metody TK (JM+PJ)

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


### Anamorfózy
### Multivariate mapping
### Kartodiagramy
#### Waffle
#### Coxcombs