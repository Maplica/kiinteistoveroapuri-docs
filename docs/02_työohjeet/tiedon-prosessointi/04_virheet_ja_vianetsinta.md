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

<!-- PLACEHOLDER: Kuvakaappaus geometria-ongelmasta kartalla (esim. rakennukset väärässä paikassa) -->

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

<!-- PLACEHOLDER: Kuvakaappaus virheilmoituksesta prosessoinnin aikana -->

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
