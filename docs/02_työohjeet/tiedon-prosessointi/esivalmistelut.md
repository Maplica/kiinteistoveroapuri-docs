---
sidebar_position: 1
---

# Esivalmistelut

## 1. Valmistele lähtötiedot
Varmista että jokaisen vuoden tarkastus on omalla QGIS projektissa!

Parhaat käytännöt tiedostojen nimeämisessä:
- ✅ Käytä kuvaavia nimiä: `kiinteistot_2025.shp`
- ✅ Välttää välilyöntejä: käytä `ala_viivaa` tai `CamelCase`
- ✅ Lisää päivämäärä: `rakennukset_2025-01-15.shp`
- ❌ Vältä erikoismerkkejä: `äö!@$%`
- ❌ Älä käytä liian lyhyitä nimiä: `data.shp`

 Tarkista shapefile-tiedostojen eheys

Jokaisen .shp-tiedoston tulee sisältää vähintään:
- `.shp` - geometria
- `.dbf` - attribuuttitiedot
- `.prj` - koordinaattijärjestelmä
- `.shx` - indeksitiedosto

Tarkistus QGIS:ssä:
1. Avaa shapefile QGIS:iin (vedä ja pudota tai Add Layer)
2. Tarkista että:
   - Taso latautuu ilman virheitä
   - Geometriat näkyvät kartalla
   - Attribuuttitaulu avautuu (oikea klikkaus → Open Attribute Table)
   - Koordinaattijärjestelmä on määritelty (katso Layer Properties → Source)

Yleisimmät ongelmat:
- 🔴 Puuttuva .prj-tiedosto → koordinaattijärjestelmä tuntematon
- 🔴 Korruptoitunut .dbf → attribuutit eivät avaudu
- 🔴 Epäyhteensopivat tiedostot → väärät tiedostot eri lähteistä


## 2. Tutki tietosisältö

Ennen prosessoinnin aloittamista, tutustu datan rakenteeseen:

 Avaa attribuuttitaulut QGIS:ssä:

Kiinteistöjen palstatiedosto:
- Etsi sarakkeet:
  - `Kiinteistötunnus` (esim. "091-001-0001-0001")
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


 Tarkista koordinaattijärjestelmät (CRS)

Miksi tämä on tärkeää?
- Eri tiedostoilla voi olla eri koordinaattijärjestelmät
- Väärä CRS johtaa virheellisiin sijainteihin
- Prosessointi muuntaa automaattisesti, mutta lähtötilan täytyy olla oikein

QGIS:ssä:
1. Oikea klikkaus taso → Properties → Source
2. Katso "Coordinate Reference System (CRS)"

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

