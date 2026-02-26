# Tiedon prosessoinnin aloitusohje ja parhaat käytännöt

## Yleiskatsaus

KiinteistöveroApuri-sovellus yhdistää kunnan tietokannasta saatavat tiedot Verottajan tietoihin ja luo kattavat raportit kiinteistöverotusta varten.

## Miksi hyvä valmistelu on tärkeää?
- Säästää aikaa - oikein valmisteltu data prosessoituu ensimmäisellä yrityksellä
- Varmistaa tiedon laadun - estää virheelliset tulokset
- Helpottaa tulosten tulkintaa - johdonmukainen data tuottaa selkeitä raportteja
- Mahdollistaa toistettavuuden

---

## Esivalmistelut

:::warning Tärkeää
Varmista että jokaisen vuoden tarkastus on omalla QGIS projektissa!
:::

### 1. Valmistele lähtötiedot
#### Tuetut tiedostomuodot

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

Yleisimmät ongelmat:
- 🔴 Puuttuva .prj-tiedosto (Shapefile) → koordinaattijärjestelmä tuntematon
- 🔴 Korruptoitunut .dbf (Shapefile) → attribuutit eivät avaudu
- 🔴 Epäyhteensopivat tiedostot → väärät tiedostot eri lähteistä
- 🔴 GeoPackage sisältää väärän tason → varmista oikea taso valittuna


#### Vaaditut sarakkeet tasoittain

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

#### Parhaat käytännöt tiedostojen nimeämisessä:
- ✅ Käytä kuvaavia nimiä: `kiinteistot_2025.shp` tai `kiinteistot_2025.gpkg`
- ✅ Välttää välilyöntejä: käytä `ala_viivaa` tai `CamelCase`
- ✅ Lisää päivämäärä: `rakennukset_2025-01-15.gpkg`
- ❌ Vältä erikoismerkkejä: `äö!@$%`
- ❌ Älä käytä liian lyhyitä nimiä: `data.gpkg`

### 2. Tutki tietosisältö

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


Tarkista koordinaattijärjestelmät (CRS)

Miksi tämä on tärkeää?
- Eri tiedostoilla voi olla eri koordinaattijärjestelmät
- Väärä CRS johtaa virheellisiin sijainteihin
- Prosessointi muuntaa automaattisesti, mutta lähtötilan täytyy olla oikein

QGIS:ssä:
1. Oikea klikkaus taso → Properties → Source
2. Katso "Coordinate Reference System (CRS)"

### 3. Tutki Excel-tiedostot (Verottajan tiedot)
Avaa Excel-tiedostot ja tarkista:
- Tiedostot aukeavat normaalisti
- Ensimmäisellä rivillä on otsikot (sarakkeiden nimet)
- Tiedot alkavat toiselta riviltä
- Ei ole tyhjiä sarakkeita välissä
- Ei ole yhdistettyjä soluja

Yleisimmät ongelmat:
- 🔴 Tiedot alkavat väärältä riviltä (esim. rivi 1 on tyhjä)
- 🔴 Erikoismerkit otsikoissa

---

## Prosessoinnin aloittaminen

### Vaihe 1: Avaa KiinteistöveroApuri-plugin QGIS:ssä

1. Käynnistä QGIS
2. Valitse valikosta `Plugins` → `KiinteistöveroApuri`
3. Paina "Tiedon prosessointi" -nappia, joka avaa prosessointi-ikkunan
4. Plugin-ikkuna avautuu kolmella välilehdellä

### Vaihe 2: Täytä Välilehti 1 - Kunnan tietokanta

**A. Kiinteistöjen palsta tiedosto:**

1. **Valitse tiedosto:**
   - Klikkaa "Selaa" nappia
   - Navigoi kiinteistöjen shapefile-tiedostoon
   - Valitse `.shp` tiedosto (Huom! tiedostossa pitäisi olla kaikki kiinteistöjen palstat eriteltynä toisistaan -> Eli tiedostossa yksi rivi per kiinteistön palsta)

2. **Valitse sarakkeet pudotusvalikoista:**
   - **Kiinteistötunnus** → valitse sarake joka sisältää kiinteistötunnukset
   - **Palstan pinta-ala** → valitse numeerinen pinta-ala sarake
   - **Kaavan käyttötarkoitus** → valitse käyttötarkoitus sarake
     - Klikkaa "Valitse arvot" nappia
     - Valitse checkbox-listasta ne **kaavamerkinnät jotka ovat yleisiä alueita**
     - **Tärkeää:** Valitut kaavamerkinnät vaikuttavat siihen, miten nämä alueet huomioidaan prosessoinnissa
     - Esim: VL (Virkistysalue), VP (Puisto), Katualueet
   - **Vesialueen pinta-ala** → valitse vesialueen sarake

**B. Määräalojen palstatiedot:**

1. Valitse tiedosto
2. Valitse **Määräalatunnus** sarake

**C. Rakennusten tiedot:**

1. Valitse tiedosto
2. Valitse sarakkeet:
   - **PRT** (Pysyvä rakennustunnus)
   - **Kiinteistötunnus**
   - **Rakennuksen numero**
   - **Kokonaisala**
   - **Kerrosala**
   - **Tilavuus**

**D. Aluejakojen tiedot:**

1. Valitse tiedosto
2. Valitse **Alueen tunniste** sarake (Sarake, joka erottaa alueen toisistaan esim. Nimi)

**E. Koordinaattijärjestelmä:**

1. Valitse "CRS" napista koordinaattijärjestelmä (Huolehdi, että kaikilla tasoilla on sama koordinaattijärjestelmä)

**💡 Vinkki:** Plugin muistaa aiemmat valinnat. Jos olet jo prosessoinut dataa aiemmin, kentät saattavat täyttyä automaattisesti.

### Vaihe 3: Täytä Välilehti 2 - Verottajan tiedot

1. **Verottajan kiinteistöverotiedot:**
   - Valitse verottajan kiinteistövero tiedosto. CSV-tiedosto, joka sisältää kaikki kunna verotiedot.

2. **Verottajan kiinteistöveron tietue:**
   - Valitse verottajan antama tietue tiedosto, joka kertoo miten CSV-tiedostoa luetaan. Yleensä tämä on Excel-tiedosto (.xlsx).

### Vaihe 4: Täytä Välilehti 3 - Tallennus

**A. Tulostiedostot:**

Tallennusvälilehdellä määrityt polut määrittävät, minne prosessoinnin tulokset tallennetaan:

- **GeoPackage-tiedosto** - Sisältää kaikki paikkatiedon tasot (rakennukset, rakennusosat, kiinteistöt, määräalat) sekä yhdistetyt tiedot että puuttuvat/yhdistelemättömät kohteet
- **Excel-tiedostot** - Puuttuvien ja yhdistelemättömien kohteiden yksityiskohtaisemmat listat taulukkomuodossa
- **Tilastotiedot** - Alueittain lasketut tilastot (min, max, keskiarvo, summa) rakennuksista ja kiinteistöistä

**B. Henkilötunnukset:**

- ☑️ **"Sisällytä henkilötunnukset"** 
  - Rasti päällä (Kyllä) → Kaikki omistajatiedot mukana tuloksissa (Myös HETU)
  - Rasti pois (Ei) → Kaikki omistajateidot poistetaan tuloksista

**C. Koordinaattijärjestelmä tulosteille:**

- Valitse koordinaattijärjestelmä, jolla lopputulos näkyy.
- Suositus, käytä samaa kuin alkuaineisto, tai samaa kuin muu aineisto jossa haluat toimia.


**D. Käynnistä prosessointi**

1. Tarkista että kaikki kentät on täytetty (plugin validoi automaattisesti)
2. Klikkaa **"RUN"** nappia
3. Plugin:
   - Käynnistää prosessointiohjelman taustalla
   - Näyttää edistymis-ikkunan

4. **Odota prosessoinnin valmistumista**
   - Prosessointi voi kestää muutamasta sekunnista useisiin minuutteihin riippuen datan koosta
   - **Älä sulje QGIS:ia** prosessoinnin aikana

5. **Valmis!**
   - Saat ilmoituksen kun prosessointi on valmis
   - Tulostiedostot löytyvät määrittämistäsi sijainneista
   - Tiedostot aukeavat painamalla suurta vihreää **"Avaa tiedostot"** nappia

---

## Parhaat käytännöt

### 1. Tietojen valmistelu

### Ennen ensimmäistä prosessointia:

**🔍 Validoi lähtödata:**
- Tarkista että geometriat ovat valideja (QGIS → Vector → Geometry Tools → Check Validity)
- Poista tyhjät rivit Verottajan CSV-tiedostosta
- Tarkista että pakolliset sarakkeet eivät sisällä tyhjiä arvoja

### 2. Prosessoinnin aikana

**⏱️ Varaa riittävästi aikaa:**
- Älä aloita prosessointia kiireessä
- Pidä tietokone päällä koko prosessoinnin ajan

**💾 Tallenna välivaiheet:**
- Tallenna projekti ennen prosessointia
- Tallenna projekti prosessoinnin jälkeen
- Älä poista vanhoja tulostiedostoja heti (nimeä uudet eri nimellä)

### 3. Tulosten tarkistus

**Heti prosessoinnin jälkeen:**

1. **Tarkista että kaikki tulostiedostot luotiin:**
   - GeoPackage-tiedostot (10-tasoa)
   - Excel-raportit kohteista jotka eivät yhdisty (2-tiedostoa)
   - Tilastot (2-tasoa)
   - Alkuperäiset aineistot (4-tasoa)

2. **Tarkista puuttuvat rakennukset -raportti:**
   - Kuinka monta rakennusta ei löytynyt?
   - Onko tämä odotettu määrä?
   - Tutki miksi rakennukset puuttuvat

**🚩 Punaiset liput (merkkejä ongelmista):**
- Tyhjät tulostiedostot
- Huomattavan vähän rivejä tulosteissa
- Kaikki rakennukset "puuttuvat"
- Geometriat väärässä paikassa kartalla
- NULL-arvoja paljon sarakekkeissa jotka pitäisi olla täytetty

### 4. Datan hallinta

**📁 Järjestä tiedostot loogisesti:**

```
Esim.

C:\Kiinteistovero\
├── 2025\
│   ├── 01_Helmikuu\
│   │   ├── Lahtotiedot\
│   │   │   ├── Kunnan_data\
│   │   │   └── Verottaja_data\
│   │   └── Tulokset\
│   └── 02_Maaliskuu\
│       └── ...
└── Arkisto\
    └── 2024\
```

**🔒 Tietoturva ja varmuuskopiointi:**
- Henkilötunnukset: poista käytöstä jos ei tarvetta
- Säilytä arkaluontoista dataa suojatussa verkkolevyllä
- !!!Älä jaa tulostiedostoja sähköpostitse (käytä turvallista tiedostonsiirtoa)!!!

---

## Yleisimmät virheet ja niiden välttäminen

### 1. Tiedosto-ongelmat

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "File not found" | Väärä polku tai tiedosto puuttuu | Tarkista polku, kokeile kopioida tiedosto uuteen sijaintiin |
| "Cannot read shapefile" | Puuttuva .dbf, .prj tai .shx | Varmista että kaikki oheistiedostot ovat samassa kansiossa |
| "Encoding error" | Väärä merkistö (ääkköset) | Yritä tallentaa shapefile UTF-8 koodauksella |
| "Excel cannot be opened" | Tiedosto auki toisessa ohjelmassa | Sulje Excel, kokeile uudestaan |

### 2. Sarake-ongelmat

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "Column not found" | Väärä sarakkeen nimi | Tarkista tarkka kirjoitusasu (isot/pienet kirjaimet) |
| "Empty column selected" | Valittu sarake joka ei ole käytössä | Valitse oikea sarake jossa on dataa |
| "Invalid data type" | Sarake ei ole numeerinen | Tarkista että pinta-alat yms. ovat numeroina ei tekstinä |
| "NULL values" | Tyhjiä arvoja pakollisissa kentissä | Täytä tyhjät arvot tai poista rivit |

### 3. Geometria-ongelmat

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "Invalid geometry" | Korruptoitunut geometria | QGIS: Vector → Geometry Tools → Fix Geometries |
| "Empty geometry" | Taso ei sisällä geometrioita | Tarkista että .shp ei ole tyhjä |
| "CRS mismatch" | Eri koordinaattijärjestelmät | Plugin muuntaa automaattisesti, mutta tarkista että lähtö-CRS on oikein |
| "Buildings outside parcels" | Koordinaatit väärin | Tarkista että kaikki tasot ovat samassa CRS:ssä |

### 4. Excel-ongelmat

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "Cannot read Excel file" | Viallinen tiedosto tai väärä muoto | Tallenna uudelleen .xlsx-muodossa |
| "No data found" | Tyhjä työkirja tai väärä välilehti | Varmista että data on ensimmäisellä välilehdellä |
| "Header row missing" | Otsikot puuttuvat | Lisää otsikkorivi (rivi 1) |
| "Duplicate columns" | Sama sarakenimi kahdesti | Nimeä sarakkeet uudelleen yksilöllisesti |

### 5. Prosessointivirheet

| Virhe | Syy | Ratkaisu |
|-------|-----|----------|
| "Out of memory" | Liian suuri dataset | Prosessoi pienemmissä osissa tai lisää RAM-muistia |
| "Process timeout" | Prosessointi kesti liian kauan | Varmista että ei muita raskaita ohjelmia käynnissä |
| "Write permission denied" | Ei oikeutta kirjoittaa tuloshakemistoon | Valitse hakemisto johon sinulla on kirjoitusoikeus |
| "Executable not found" | Prosessointiohjelma ei löydy | Tarkista että .exe on rakennettu ja oikeassa paikassa |

---

## Tarkistuslista ennen prosessointia

### ✅ Lähtötiedot

- [ ] Kaikki 4 shapefile-tiedostoa (kiinteistöt, määräalat, rakennukset, alueet) löytyvät
- [ ] Jokainen shapefile sisältää .shp, .dbf, .prj, .shx -tiedostot
- [ ] Shapefile-tiedostot avautuvat QGIS:ssa ilman virheitä
- [ ] Geometriat näkyvät oikein kartalla
- [ ] Attribuuttitaulut avautuvat ja sisältävät dataa
- [ ] Verottajan tiedot löytyvät ja avautuvat

### ✅ Sarakkeet ja sisältö

- [ ] Tiedän tarkat sarakkeiden nimet (dokumentoin ne)
- [ ] Pakolliset sarakkeet sisältävät dataa (eivät tyhjiä)
- [ ] Käyttötarkoituskoodit ovat valideja

### ✅ Koordinaattijärjestelmät

- [ ] Tiedän kaikkien shapefile-tiedostojen koordinaattijärjestelmät:n ja ne ovat samat kaikilla
- [ ] Valitsin oikean CRS:n tulosteille

### ✅ Työympäristö

- [ ] Riittävästi levytilaa tulosteille (arvioi ~2x lähtödatan koko)
- [ ] Tietokone ei sammunnu kesken prosessoinnin (virransäästöasetukset)

### ✅ Tulostiedostot

- [ ] Määrittelin tulostiedostojen sijainnit
- [ ] Minulla on kirjoitusoikeudet kyseisiin hakemistoihin
- [ ] Tiedän mitä teen HETU-tiedoilla (mukaan vai pois)
- [ ] Tuloshakemistossa on tilaa

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

Jos mikään ei auta:

1. Kerää yhteen:
   - Virheilmoitus (kopio/kuvakaappaus)
   - Käyttämäsi asetukset (Kuvakaappaukset)
   - Tiedostojen nimet ja sarakkeiden nimet
   - Mitä olet jo kokeillut

---

