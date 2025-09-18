# Úloha I – Digitální modely terénu

## Zadání 

V této úloze si vyzkoušíte práci s daty LLS (letecké laserové skenování, LiDAR).

Pomocí stahovací služby ATOM si z Geoportálu ČÚZK opatřete data LLS za příslušný mapový list níže dle zadání:

!!! tip "**Jednotlivá zadání:** "   
    01 | Louny 1–2 <br />
    02 | Most 4–8 <br />
    03 | Most 2–7 <br />
    04 | Litoměřice 6–5 <br />
    05 | Louny 0–1 <br />
    06 | Most 5–9 <br />
    07 | Louny 1–1 <br />
    08 | Most 3–9 <br />
    09 | Louny 1–0 <br />
    10 | Most 3–8 <br />
    11 | Louny 2–1 <br />
    12 | Most 5–9 <br />
    13 | Most 1–7 <br />
    14 | Louny 0–0 <br />
    15 | Litoměřice 6–7 <br />
    16 | Most 1–9 <br />
    17 | Most 2–8 <br />
    18 | Louny 3–0 <br />
    19 | Most 3–7 <br />
    20 | Louny 2–2 <br />
    21 | Most 4–9 <br />
    22 | Louny 2–0
  

Soubory obsahují data ve formátu LAZ.

**Existují tři generace modelů:**

- DMR 4G – digitální model terénu 4. generace – grid výškově určených bodů o rozměru 5×5 m;
- DMR 5G – digitální model terénu 5. generace – nepravidelná síť výškově určených bodů o hustotě zhruba 1 bod/m^2^;
- DMP 1G – digitální model povrchu 1. generace – nepravidelná síť výškově určených bodů o hustotě zhruba 1 bod/m^2^.

Využitím nástrojů software ArcGIS vytvořte:

-  **Mapa I** – vrstevnicový plán z dat DMT 5G s ekvidistancí 2 m, doplněný popisy, se zvýrazněnými vrstevnicemi po 10 m; vyexportujte v měřítku 1 : 10 000;
-  porovnejte tento Váš výstup s mapou na portálu Mapy.cz. Liší se vrstevnice? Do TZ vyexportujte tři detaily území, kde dochází k výrazným rozdílům mezi vámi vygenerovanými vrstevnicemi a těmi, které obsahují Mapy.cz;
-  **Mapa II** – spočítejte LRM – *local relief model* jako rozdíl dat DMR 5G a vyhlazeného modelu pomocí 5m vyhlazovacího okna (funkce *Focal Statistics*: *Rectangle 5×5*, statistika *Mean*); rastry odečtete od sebe pomocí funkce *Minus* nebo s využitím *Raster calculator*;
-  spočítejte pomocí nástroje [*Terrain Tools*](https://www.arcgis.com/home/item.html?id=4b2ea7c5f87d476a8849c804b81667aa) stínovaný reliéf (využijte metodu *MDOW*);    
-  **Mapa III** – vizualizujte pomocí kompozitního obrazu "50% LRM nad MDOW" v měřítku 1 : 5000 oblast, kde se v největší míře objevují výrazné terénní příznaky struktur jako jsou agrární terasy, valy apod.

Můžete využít [návod ke konstrukci vrstevnic z digitálních modelů terénu v prostředí ArcGIS](../dmt.md).

!!! warning "K odevzdání"

    ## Požadované výstupy

    - Vytištěnou technickou zprávu, obsahující stručný popis úlohy, zadanou oblast;
    - tři detaily území o velkých rozdílech v obrazu vrstevnic;
    - vrstevnicový plán na velikost A4 (včetně popisu a tiráže);
    - obraz LRM modelu (včetně popisu a tiráže);
    - kompozitní obraz vizualizující terénní hrany (včetně popisu a tiráže).

    Do Moodle nahrajte TZ elektronicky včetně všech výstupů. Tištěná verze není třeba.
