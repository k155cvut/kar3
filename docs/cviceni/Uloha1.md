# Digitální modely terénu

## Zadání 

V této úloze si vyzkoušíte práci s daty LLS (letecké laserové skenování, LiDAR).

Pomocí stahovací služby ATOM si z Geoportálu ČÚZK opatřete data LLS za příslušný mapový list níže dle zadání:

!!! tip "**Jednotlivá zadání:** "   
    Bořík:	Nový Bor 1–3 <br />
    Černohousová:  	Litoměřice 3–3<br />
    Hádlík:	Mimoň 1–3<br />
    Klimeš:	Beroun 2–8<br />
    Kovář:	Dubá 4–8      <br />
    Mihal:	Teplice 5–8<br />
    Mlejnek:	Žlutice 5–4<br />
    Nedoma:	Litoměřice 9–7<br />
    Pokorný:	Křivoklát 9–2<br />
    Rabasová:	Beroun 7–1<br />
    Roučka:	Kralovice 6–1<br />
    Sedlák:	Dubá 5–0<br />
    Skořepa:	Chomutov  2–3<br />
    Slabá:	Nový Bor 0–6<br />
    Soukupová:	Karlovy Vary 4–1<br />
    Šimek:	Aš 8–2<br />
    Tomášková:	Děčín 1–5<br />
    Turek:	Manětín 0–2<br />
    Zbíral:	Varnsdorf 9–8
  

Soubory obsahují data ve formátu LAZ.

**Existují tři generace modelů:**

- DMR 4G –   digitální model terénu 4. generace – grid výškově určených bodů o rozměru 5×5 m;
- DMR 5G  –  digitální model terénu 5. generace – nepravidelná síť výškově určených bodů o hustotě zhruba 1 bod/m^2^;
- DMP 1G   – digitální model povrchu 1. generace – nepravidelná síť výškově určených bodů o hustotě zhruba 1 bod/m^2^.

Využitím nástrojů software OCAD a ArcGIS vytvořte:

-   vrstevnicový plán z dat DMT 5G s ekvidistancí 2 m, doplněný popisy, se zvýrazněnými vrstevnicemi po 10 m; vyexportujte v měřítku 1 : 10 000;
-   srovnejte s ZTM10 – liší se vrstevnice? – a do TZ vyexportujte tři detaily území, kde dochází k výrazným rozdílům mezi vámi vygenerovanými vrstevnicemi a těmi, které obsahují Mapy.cz;
-   spočítejte rozdílový model DMT 5G – využijte [Image Service](https://ags.cuzk.cz/arcgis2/rest/services/dmr5g/ImageServer) s rozlišením 2 m;
    
-   spočítejte rozdílový model DMT 5G – DMP 1G a klasifikujte u něj vegetaci: <br />
    vytvořte třídy 0 – 0,1 m \| 0,1 – 2 m \| 2 – 4 m \| 4 – 7 m \| 7 – 10 m \| 10 – 15 m \| 15 – 20 m \| nad 20 m.

Můžete využít [návod ke konstrukci vrstevnic z digitálních modelů terénu v prostředí ArcGIS](../dmt.md).

!!! warning "K odevzdání"

    ## Požadované výstupy

    - Vytištěnou technickou zprávu, obsahující stručný popis úlohy, zadanou oblast, obrázek klasifikované vegetace (včetně jednoduché legendy a tiráže), tři detaily území o velkých rozdílech v obrazu vrstevnic;

    - Vrstevnicový plán na velikost A4 (včetně popisu a tiráže);
    - Obraz rozdílového modelu (včetně jednoduché legendy a tiráže).

    Do Moodle nahrajte TZ elektronicky včetně všech výstupů. Tištěná verze není třeba.
