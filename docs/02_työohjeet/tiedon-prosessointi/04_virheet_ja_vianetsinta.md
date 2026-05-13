---
sidebar_position: 4
---

# Virheet ja vianetsintä

Tässä osiossa käydään läpi yleisimmät virhetilanteet ja niiden ratkaisut prosessoinnin eri vaiheissa.

---

## 1. Tiedosto-ongelmat

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "File not found" | Väärä polku tai tiedosto puuttuu | Tarkista polku, kokeile kopioida tiedosto uuteen sijaintiin |
| "Cannot read shapefile" | Puuttuva .dbf, .prj tai .shx | Varmista että kaikki oheistiedostot ovat samassa kansiossa |
| "Encoding error" | Väärä merkistö (ääkköset) | Yritä tallentaa shapefile UTF-8 koodauksella |
| "Excel cannot be opened" | Tiedosto auki toisessa ohjelmassa | Sulje Excel, kokeile uudestaan |

---

## 2. Sarake-ongelmat

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "Column not found" | Väärä sarakkeen nimi | Tarkista tarkka kirjoitusasu (isot/pienet kirjaimet) |
| "Empty column selected" | Valittu sarake joka ei ole käytössä | Valitse oikea sarake jossa on dataa |
| "Invalid data type" | Sarake ei ole numeerinen | Tarkista että pinta-alat yms. ovat numeroina ei tekstinä |
| "NULL values" | Tyhjiä arvoja pakollisissa kentissä | Täytä tyhjät arvot tai poista rivit |

---

## 3. Geometria-ongelmat

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "Invalid geometry" | Korruptoitunut geometria | QGIS: Vector → Geometry Tools → Fix Geometries |
| "Empty geometry" | Taso ei sisällä geometrioita | Tarkista että .shp ei ole tyhjä |
| "CRS mismatch" | Eri koordinaattijärjestelmät | Plugin muuntaa automaattisesti, mutta tarkista että lähtö-CRS on oikein |
| "Buildings outside parcels" | Koordinaatit väärin | Tarkista että kaikki tasot ovat samassa CRS:ssä |

**Kunta-aineiston M-geometria (Measured 3D Polygon):** Jos palsta- tai määräalashapefile on tallennettu M-geometria-muodossa, pyogrio muuntaa sen Polygon Z:ksi, mistä voi aiheutua null- tai tyhjiä geometrioita. Prosessointi havaitsee nämä automaattisesti ja tulostaa lokiin `[Kunta data quality]`-rivit:

```
[Kunta data quality] palsta rows with null/empty geometry: N
[Kunta data quality] määräala rows with null/empty geometry: N
```

Vaikuttuneet verotietueet kirjoitetaan erilliseen `TaxBuildings_BadKuntaGeometry_<date>.xlsx`-tiedostoon (ks. [Excel-lisäraportit](../../../docs/03_toiminnot/04_output_taso_ohje.md)). Prosessoinnin valmistumisdialogi näyttää oranssin varoituksen, jos null-geometrioita löytyi.

**Ratkaisu:** Vie kunta-aineisto uudelleen ilman M-koordinaatteja (QGIS: tallenna shapefile, poista valinta "Include Z dimension" ja "Include M dimension"), tai käytä suoraan GeoPackage-muotoa.

---

## 4. Excel-ongelmat

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "Cannot read Excel file" | Viallinen tiedosto tai väärä muoto | Tallenna uudelleen .xlsx-muodossa |
| "No data found" | Tyhjä työkirja tai väärä välilehti | Varmista että data on ensimmäisellä välilehdellä |
| "Header row missing" | Otsikot puuttuvat | Lisää otsikkorivi (rivi 1) |
| "Duplicate columns" | Sama sarakenimi kahdesti | Nimeä sarakkeet uudelleen yksilöllisesti |

---

## 5. Prosessointivirheet

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "Out of memory" | Liian suuri dataset | Prosessoi pienemmissä osissa tai lisää RAM-muistia |
| "Process timeout" | Prosessointi kesti liian kauan | Varmista että ei muita raskaita ohjelmia käynnissä |
| "Write permission denied" | Ei oikeutta kirjoittaa tuloshakemistoon | Valitse hakemisto johon sinulla on kirjoitusoikeus |
| "Executable not found" | Prosessointiohjelma ei löydy | Tarkista että .exe on rakennettu ja oikeassa paikassa |

![Prosessointivirhe-ilmoitus](/img/system_images/dialog_processing_error.svg)

---

## Vianetsintä

### Jos prosessointi epäonnistuu:

**1. Lue virheilmoitus huolellisesti**
- Kopioi virheilmoitus talteen

**2. Tarkista perusteet**
- Ovatko kaikki tiedostot olemassa?
- Avautuvatko tiedostot manuaalisesti?
- Oletko valinnut oikeat sarakkeet?

**3. Yksinkertaista**
- Kokeile pienemmällä datasetilla (yksi kortteli)

**4. Kysy apua**
- contact.maplica@gmail.com

### Jos mikään ei auta:

1. Kerää yhteen:
   - Virheilmoitus (kopio/kuvakaappaus)
   - Käyttämäsi asetukset (kuvakaappaukset)
   - Tiedostojen nimet ja sarakkeiden nimet
   - Mitä olet jo kokeillut
