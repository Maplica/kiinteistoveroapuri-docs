---
sidebar_position: 1
---

# Esivalmistelut

## Yleiskatsaus

KiinteistöveroApuri-sovellus yhdistää kunnan tietokannasta saatavat tiedot Verottajan tietoihin ja luo kattavat raportit kiinteistöverotusta varten.

## Miksi hyvä valmistelu on tärkeää?
- Säästää aikaa - oikein valmisteltu data prosessoituu ensimmäisellä yrityksellä
- Varmistaa tiedon laadun - estää virheelliset tulokset
- Helpottaa tulosten tulkintaa - johdonmukainen data tuottaa selkeitä raportteja
- Mahdollistaa toistettavuuden

:::warning Tärkeää
Varmista että jokaisen vuoden tarkastus on omalla QGIS projektissa!
:::

---

## 1. Valmistele lähtötiedot
### Tuetut tiedostomuodot

Prosessointi tukee sekä **Shapefile**- että **GeoPackage**-tiedostoja:

**Shapefile (.shp)**
Jokaisen .shp-tiedoston tulee sisältää vähintään:
- `.shp` - geometria
- `.dbf` - attribuuttitiedot
- `.prj` - koordinaattijärjestelmä
- `.shx` - indeksitiedosto

**GeoPackage (.gpkg)**
Yksi .gpkg-tiedosto voi sisältää useita tasoja. Suositellaan erityisesti silloin, kun aineisto toimitetaan yhtenä pakettina.

Tarkistus QGIS:ssä:
1. Avaa tiedosto QGIS:iin (vedä ja pudota tai Add Layer)
2. Tarkista että:
   - Taso latautuu ilman virheitä
   - Geometriat näkyvät kartalla
   - Attribuuttitaulu avautuu (oikea klikkaus → Open Attribute Table)
   - Koordinaattijärjestelmä on määritelty (katso Layer Properties → Source)

<!-- TODO: Lisää kuvakaappaus - QGIS:n Add Layer -dialogi tai tason lataaminen -->
![QGIS tason lataaminen](/img/placeholder_qgis_add_layer.png)

Yleisimmät ongelmat:
- 🔴 Puuttuva .prj-tiedosto (Shapefile) → koordinaattijärjestelmä tuntematon
- 🔴 Korruptoitunut .dbf (Shapefile) → attribuutit eivät avaudu
- 🔴 Epäyhteensopivat tiedostot → väärät tiedostot eri lähteistä
- 🔴 GeoPackage sisältää väärän tason → varmista oikea taso valittuna


### Vaaditut sarakkeet tasoittain

:::warning Tärkeää
Seuraavien tasojen sarakkeiden **täytyy olla olemassa** oikeilla nimillä, jotta prosessointi toimii. Tarkista jokainen taso ennen käynnistystä.
:::

**Kiinteistöjen palstatiedosto:**
- Pakolliset sarakkeet:
  - `Kiinteistötunnus` (esim. "XXX-001-0001-0001")
  - `Palstan pinta-ala` (numeerinen arvo)
  - `Kaavan käyttötarkoitus` (esim. "AO", "AP", "VL")
  - `Vesialueen pinta-ala` (numeerinen arvo)

**Rakennusten tiedosto:**
- Pakolliset sarakkeet:
  - `Pysyvä rakennustunnus (PRT)` (numero)
  - `Kiinteistötunnus` (linkki kiinteistöön)
  - `Rakennuksen numero`
  - `Kokonaisala`
  - `Kerrosala`
  - `Tilavuus`

**Määräalojen tiedosto:**
- Pakollinen sarake: `Määräalatunnus`

**Aluejakojen tiedosto:**
- Pakollinen sarake: `Alueen tunniste`

<!-- TODO: Lisää kuvakaappaus - esimerkki attribuuttitaulusta jossa vaaditut sarakkeet näkyvät -->
![Esimerkki attribuuttitaulusta](/img/placeholder_attribuuttitaulu.png)

### Parhaat käytännöt tiedostojen nimeämisessä:
- ✅ Käytä kuvaavia nimiä: `kiinteistot_2025.shp` tai `kiinteistot_2025.gpkg`
- ✅ Välttää välilyöntejä: käytä `ala_viivaa` tai `CamelCase`
- ✅ Lisää päivämäärä: `rakennukset_2025-01-15.gpkg`
- ❌ Vältä erikoismerkkejä: `äö!@$%`
- ❌ Älä käytä liian lyhyitä nimiä: `data.gpkg`

---

## 2. Tutki tietosisältö

Ennen prosessoinnin aloittamista, tutustu datan rakenteeseen:

Avaa attribuuttitaulut QGIS:ssä ja varmista, että vaaditut sarakkeet löytyvät (ks. kohta 1 yllä).

Kiinteistöjen palstatiedosto:
- Etsi sarakkeet:
  - `Kiinteistötunnus` (esim. "XXX-001-0001-0001")
  - `Palstan pinta-ala` (numeerinen arvo)
  - `Kaavan käyttötarkoitus` (esim. "AO", "AP", "VL")
  - `Vesialueen pinta-ala` (numeerinen arvo)

Rakennusten tiedosto:
- Etsi sarakkeet:
  - `Pysyvä rakennustunnus (PRT)` (numero)
  - `Kiinteistötunnus` (linkki kiinteistöön)
  - `Rakennuksen numero`
  - `Kokonaisala`
  - `Kerrosala`
  - `Tilavuus`

Määräalojen tiedosto:
- Etsi `Määräalatunnus` sarake

Aluejakojen tiedosto:
- Etsi `Alueen tunniste` sarake

### Tarkista koordinaattijärjestelmät (CRS)

Miksi tämä on tärkeää?
- Eri tiedostoilla voi olla eri koordinaattijärjestelmät
- Väärä CRS johtaa virheellisiin sijainteihin
- Prosessointi muuntaa automaattisesti, mutta lähtötilan täytyy olla oikein

QGIS:ssä:
1. Oikea klikkaus taso → Properties → Source
2. Katso "Coordinate Reference System (CRS)"

<!-- TODO: Lisää kuvakaappaus - Layer Properties → Source -välilehti jossa CRS näkyy -->
![CRS tarkistus QGIS:ssä](/img/placeholder_crs_tarkistus.png)

---

## 3. Tutki Excel-tiedostot (Verottajan tiedot)
Avaa Excel-tiedostot ja tarkista:
- Tiedostot aukeavat normaalisti
- Ensimmäisellä rivillä on otsikot (sarakkeiden nimet)
- Tiedot alkavat toiselta riviltä
- Ei ole tyhjiä sarakkeita välissä
- Ei ole yhdistettyjä soluja

Yleisimmät ongelmat:
- 🔴 Tiedot alkavat väärältä riviltä (esim. rivi 1 on tyhjä)
- 🔴 Erikoismerkit otsikoissa

<!-- TODO: Lisää kuvakaappaus - esimerkki oikein muotoillusta Excel-tiedostosta -->
![Esimerkki Verottajan Excel-tiedostosta](/img/placeholder_verottaja_excel.png)

---

:::tip Seuraava vaihe
Kun esivalmistelut on tehty, siirry seuraavaan osioon: [Prosessoinnin käynnistys](./01_kaynnistys.md)
:::
