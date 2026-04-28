---
sidebar_position: 1
---

# Esivalmistelut

## Yleiskatsaus

KiinteistöveroApuri yhdistää kunnan tietokannasta saatavat tiedot verottajan tietoihin ja tuottaa vertailukelpoisen aineiston kiinteistöverotarkastusta varten.

## Miksi hyvä valmistelu säästää aikaa?

Hyvä valmistelu tarkoittaa käytännössä sitä, että tiedostot aukeavat QGIS:ssä ongelmitta ja sarakkeiden nimet vastaavat prosessoinnin odottamia kentänimiä. Kun lähtödata on kunnossa, prosessointi menee useimmiten läpi ensimmäisellä yrityksellä eikä arvaile virheellä tuottamattomaan tulosta.

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

<!-- PLACEHOLDER: Kuvakaappaus QGIS:n Add Layer -dialogista tai tason lataamisesta -->

Yleisimmät ongelmat:
- 🔴 Puuttuva .prj-tiedosto (Shapefile) → koordinaattijärjestelmä tuntematon
- 🔴 Korruptoitunut .dbf (Shapefile) → attribuutit eivät avaudu
- 🔴 Epäyhteensopivat tiedostot → väärät tiedostot eri lähteistä
- 🔴 GeoPackage sisältää väärän tason → varmista oikea taso valittuna


### Vaaditut sarakkeet tasoittain

:::warning Tärkeää
Seuraavien tasojen sarakkeet **täytyä löytyä tiedostosta**, jotta prosessointi toimii. Tarkista jokainen taso ennen käynnistystä.
:::

**Kiinteistöjen palstatiedosto:**
- Pakolliset sarakkeet:
  - `Kiinteistötunnus` (esim. "XXX-001-0001-0001")
  - `Palstan pinta-ala`
  - `Kaavan käyttötarkoitus` (esim. "AO", "AP", "VL")
  - `Vesialueen pinta-ala`

**Rakennusten tiedosto:**
- Pakolliset sarakkeet:
  - `Pysyvä rakennustunnus (PRT)`
  - `Kiinteistötunnus` (linkki kiinteistöön)
  - `Rakennuksen numero`
  - `Kokonaisala`
  - `Kerrosala`
  - `Tilavuus`

**Määräalojen tiedosto:**
- Pakollinen sarake: `Määräalatunnus` (esim. "XXX-001-0001-0001-M501")

**Aluejakojen tiedosto:**
- Pakollinen sarake: `Alueen tunniste` (esim. Alueen nimi)


### Parhaat käytännöt tiedostojen nimeämisessä:
- ✅ Käytä kuvaavia nimiä: `kiinteistot_2025.shp` tai `kiinteistot_2025.gpkg`
- ✅ Välttää välilyöntejä: käytä `ala_viivaa` tai `CamelCase`
- ✅ Lisää päivämäärä: `rakennukset_2025-01-15.gpkg`
- ❌ Vältä erikoismerkkejä: `äö!@$%`
- ❌ Älä käytä liian lyhyitä nimiä: `data.gpkg`

---

## 2. Tutki tietosisältö

Avaa attribuuttitaulut QGIS:ssä ja varmista, että vaaditut sarakkeet löytyvät (ks. kohta 1 yllä). Jos sarakkeet ovat olemassa mutta nimetty eri tavalla kuin listassa, voit määrittää vastineet prosessointiasetuksissa.

### Tarkista koordinaattijärjestelmät (CRS)

Miksi tämä on tärkeää?
- Eri tiedostoilla voi olla eri koordinaattijärjestelmät
- Väärä CRS johtaa virheellisiin sijainteihin
- Prosessointi muuntaa automaattisesti, mutta lähtötilan täytyy olla oikein

QGIS:ssä:
1. Oikea klikkaus taso → Properties → Source
2. Katso "Coordinate Reference System (CRS)"

<!-- PLACEHOLDER: Kuvakaappaus Layer Properties → Source -välilehdestä jossa CRS näkyy -->

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

![Esimerkki oikein muotoillusta verottajan Excel-tiedostosta](/img/system_images/example_tax_excel_file.svg)

---

:::tip Seuraava vaihe
Kun esivalmistelut on tehty, siirry seuraavaan osioon: [Prosessoinnin käynnistys](./01_kaynnistys.md)
:::
