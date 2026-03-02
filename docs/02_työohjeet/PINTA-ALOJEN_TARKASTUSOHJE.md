# Pinta-alojen tarkastus- ja korjausohje

Tämä ohje opastaa käyttämään KiinteistöveroApuri-työkalua rakennusten ja kiinteistöjen pinta-alojen tarkastamiseen ja korjaamiseen. Työkalu vertaa kunnan rekisterin ja verottajan pinta-alatietoja, visualisoi erot ja auttaa korjaamaan virheelliset tiedot.

## Miksi pinta-alojen tarkastus on tärkeää?

- **Verotuksen oikeellisuus:** Väärät pinta-alat johtavat virheelliseen verotukseen
- **Taloudellinen vaikutus:** Pienetkin pinta-ala-erot voivat merkitä suuria euromääriä
- **Rekisterin luotettavuus:** Oikeat pinta-alat varmistavat tietokannan laadun
- **Lakisääteiset velvoitteet:** Virheelliset tiedot voivat aiheuttaa oikeudellisia ongelmia

---

## Käytettävät työkalut

### 1. Rakennusten pinta-ala erotus -visualisointi

**Taso:** Rakennukset_Yhdistetty_vero_ja_tietokanta (prosessoitu), Area_difference (Tax - database)

**Karttasymbolit:** Timanttikuviot, väri kertoo eron suuruuden ja suunnan:

| Väri | Ero (m²) | Merkitys |
|------|----------|----------|
| 🔴 **Tummanpunainen** | < -18000 | Verotiedoissa paljon pienempi kuin rekisterissä (kriittinen) |
| 🟠 **Oranssi** | -18000 - -500 | Verotiedoissa huomattavasti pienempi |
| 🟡 **Vaalean oranssi** | -500 - -25 | Verotiedoissa jonkin verran pienempi |
| 🟨 **Keltainen** | -25 - -1 | Verotiedoissa hieman pienempi |
| ⚪ **Valkoinen** | -1 - 1 | Pinta-alat täsmäävät (OK) |
| 🟩 **Vaaleanvihreä** | 1 - 25 | Verotiedoissa hieman suurempi |
| 🟢 **Vihreä** | 25 - 100 | Verotiedoissa jonkin verran suurempi |
| 🔵 **Turkoosi** | 100 - 500 | Verotiedoissa huomattavasti suurempi |
| 🔷 **Sininen** | > 500 | Verotiedoissa paljon suurempi kuin rekisterissä (kriittinen) |

**Tulkinta:**
- **Negatiiviset arvot (punaiset/oranssit):** Veroaineistossa pienempi pinta-ala → mahdollinen veronmenetys
- **Positiiviset arvot (vihreät/siniset):** Veroaineistossa suurempi pinta-ala → mahdollisesti liikaa veroa
- **Lähellä nollaa (valkoinen):** Pinta-alat täsmäävät, ei tarvetta toimenpiteisiin

### 2. Vertailu-työkalu - kahden sarakkeen automaattinen vertailu

KiinteistöveroApurissa on sisäänrakennettu **Vertaa**-työkalu, joka suodattaa automaattisesti rivit joissa kahden sarakkeen arvot eroavat toisistaan.

**Miten käyttää:**

1. **Avaa Vertaa-työkalu:**
   - Klikkaa yläpalkin **"Vertailu"** -valikko
   - Valitse **"Vertaa"**
   
   ![](\img\logo.svg)

2. **Valitse vertailtavat sarakkeet:**
   
   Vertaa-ikkuna aukeaa kolmella kentällä:
   
   - **Sarake A:** Valitse ensimmäinen sarake (esim. `Kokonaisala_Kunta`)
   - **Sarake B:** Valitse toinen sarake (esim. `Kokonaisala_Vero`)
   - **Toleranssi (numeroille):** Anna sallittu ero numeroarvoksi (esim. `10` tai `0.5`)
   
   ![](\img\logo.svg)

3. **Klikkaa OK** → Taulukko suodattuu automaattisesti

**Mitä tapahtuu:**
- ✅ Näytetään vain rivit joissa sarakkeet **eivät täsmää**
- ✅ Toleranssi huomioidaan: jos ero ≤ toleranssi → rivi piilotetaan (täsmää)
- ✅ Tekstikentät: näytetään jos arvot eivät ole identtiset
- ✅ Tyhjät arvot: huomioidaan vertailussa (NULL vs arvo = ei täsmää)

**Vertailun hyödyt:**
- 🎯 **Automaattinen suodatus:** Vain erot näkyvissä, ei tarvetta manuaaliseen järjestelyyn
- 📊 **Toleranssi:** Voit hyväksyä pienet erot (esim. pyöristyserot)
- 🔄 **Tallennetaan automaattisesti:** Seuraavalla kerralla samat sarakkeet valmiina
- 🚀 **Nopea tarkastus:** Näet heti montako rakennusta vaatii korjausta

**Esimerkkejä:**

**Esimerkki 1: Pinta-alojen vertailu, toleranssi 2 m²**
- Sarake A: `Kokonaisala_Kunta`
- Sarake B: `Kokonaisala_Vero`
- Toleranssi: `2`
- **Tulos:** Näytetään vain rakennukset joissa ero > 2 m² (pienet pyöristyserot hyväksytään)

**Esimerkki 2: Rakennusvuosien vertailu, ei toleranssia**
- Sarake A: `Rakennusvuosi_Kunta`
- Sarake B: `Rakennusvuosi_Vero`
- Toleranssi: *(jätetään tyhjäksi)*
- **Tulos:** Näytetään vain rakennukset joissa vuosiluku eri

**Esimerkki 3: Kerrosalojen vertailu, toleranssi 0.5 m²**
- Sarake A: `Kerrosala_Kunta`
- Sarake B: `Kerrosala_Vero`
- Toleranssi: `0.5`
- **Tulos:** Hyvin tarkkaa vertailua, vain todelliset erot näytetään

**Palauta normaali näkymä:**
1. Avaa **Vertailu → Vertaa** uudelleen
2. Klikkaa **"Palauta"** (Reset) -nappia
3. Tai klikkaa **"Tyhjennä suodatin"** -nappia vasemman ikkunan yläpuolella

**Sarakkeiden otsikot:**
- Vertailun aikana sarakkeet A ja B **korostetaan otsikkoriveillä**
- Näet helposti mitkä sarakkeet ovat vertailussa

Vinkki: Laita näkyville vain ne sarakkeet mitkä sinä tarvitset.

---

## Käytännön työnkulku

### Vaihe 1: Tunnista ja suodata ongelmakohteet

Pinta-alojen tarkastus tehdään pääasiassa **listapohjaisesti** käyttäen KiinteistöveroApurin Vertailu-työkalua.

#### **Listapohjaisesti (suositeltu):**

1. **Avaa taso KiinteistöveroApurissa:**
   - Valitse **Rakennukset_Yhdistetty_vero_ja_tietokanta (prosessoitu)** -taso
   - Taso näkyy vasemmassa ikkunassa

2. **Käytä Vertailu-työkalua:**
   - Klikkaa yläpalkin **"Vertailu"** → **"Vertaa"**
   - Valitse sarakkeet:
     - **Sarake A:** `Kokonaisala_Kunta`
     - **Sarake B:** `Kokonaisala_Vero`
     - **Toleranssi:** `10` (hyväksyy pienet pyöristyserot)
   - Klikkaa **OK** → Näytetään vain rakennukset joissa pinta-alat eroavat

   ![](\img\logo.svg)

3. **Valitse näytettävät sarakkeet:**
   - Klikkaa sarakevalitsinta (esim. "8/45 ▼")
   - Valitse vain tarvitsemasi sarakkeet:
     - Kiinteistötunnus
     - PRT (Pysyvä rakennustunnus)
     - Kokonaisala_Kunta
     - Kokonaisala_Vero
     - Area_difference (Tax - database)
     - Rakennuksen käyttötarkoitus

4. **Lisäsuodatus (tarvittaessa):**
   - Oikea klikkaus sarakkeen otsikkoa (esim. `Building_Area_difference (Tax - database)__added`)
   - Valitse **"Suodata"** tai **"Järjestä"**
   - Suodata esim. vain erot > 100 m² tai < -100 m²
   - Järjestä suurimmasta pienimpään priorisoidaksesi kriittisimmät

5. **Tarkastele kohdetta kartalla:**
   - Valitse rivi vasemmasta ikkunasta
   - Klikkaa **"Näytä kartalla"** -nappia
   - Kartta zoomaa rakennukseen ja korostaa sen

#### **Karttapohjaisesti:**

⚠️ **Ei saatavilla kiinteistöjen pinta-ala-tarkastukseen.**

Ota käyttöön Area_difference (Tax - database) tyyli tasolle rakennukset_Yhdistetty_vero_ja_tietokanta (prosessoitu). Löydä korjattava kohde kartalta värien avulla. Käytä "Valitse kartalta" -työkalua, joka näyttää valitut kohteet listassa (Vasen ikkuna). Priorisoi arvokkaimmat alueet käsittelyyn ensin hyödyntäen kartan värityksiä.

---

### Vaihe 2: Tutki ja tunnista syy

**Yleisimmät syyt pinta-ala-eroihin:**

| Syy | Tunnistaminen | Ratkaisu |
|-----|---------------|----------|
| **Yksikkövirhe** | Ero täsmälleen 10x tai 100x | Korjaa kerrotuimman näköinen virheellinen arvo |
| **Mittausvirhe** | Ero 5-20%, ei systemaattinen | Tarkista mittaustiedot, tilaa uusi mittaus |
| **Vanha tieto** | Rakennusvuosi eri, laajennus tehty | Päivitä uudempi tieto molempiin |
| **Laajennus/purku** | Suuri ero, rakennushistoria muuttunut | Selvitä todellinen pinta-ala, korjaa kumpikin |
| **Väärä rakennusosa** | Ero pieni, kerrosala vs kokonaisala sekaantunut | Tarkista oikea mittausperuste |
| **Kirjoitusvirhe** | Ero satunnainen, ei looginen | Vertaa alkuperäisiin dokumentteihin |

---

### Vaihe 3: Korjaa virheelliset tiedot

**Siirry käsittelyikkunaan:**

1. Valitse virheellinen rivi vasemmasta ikkunasta
2. Klikkaa nuolinappia → siirrä oikeaan käsittelyikkunaan

   ![](\img\logo.svg)

3. Tuplaklikkaa siirrettyä riviä → aukeaa käsittelyikkuna

**Korjaa tiedot:**

1. **Selvitä oikea pinta-ala:**
   - Tarkista rakennusvalvonnan asiakirjat
   - Tarkista mittauspöytäkirja

2. **Korjaa kumpaankin järjestelmään:**
   - Jos **rekisteri väärä:** Korjaa kunnan tietokantaan, merkitse kommenttiin
   - Jos **veroaineisto väärä:** Merkitse kommenttiin "Ilmoita verottajalle", tallenna

3. **Lisää kommentti:**
   - Kirjoita selkeä selitys:
     - "Korjattu: Kokonaisala 250 m² → 2500 m², oli yksikkövirhe"
     - "Laajennus 2023: pinta-ala 120 m² → 180 m²"
     - "Ilmoita verottajalle: veroaineistossa virheellinen 1200 m², oikea 120 m²"

4. **Tallenna:**
   - Paina "Tallenna"-nappia käsittelyikkunassa
   - Paina "Tallenna muokkaukset" vasemmassa ikkunassa

---

## Parhaat käytännöt

**Tee näin:**
- ✅ Priorisoi suuret erot ja arvokkaiden rakennusten erot
- ✅ Käytä vertailuikkunaa - visualisoi erot vierekkäin
- ✅ Dokumentoi kaikki korjaukset kommentteihin
- ✅ Tarkista ilmakuvista ennen korjaamista
- ✅ Korjaa sekä rekisteriin että ilmoita verottajalle
- ✅ Tallenna säännöllisesti
- ✅ Käytä suodatusta tehokkaaseen työskentelyyn

**Vältä näitä:**
- ❌ Älä korjaa pinta-aloja arvaamalla
- ❌ Älä jätä dokumentoimatta miksi korjasit
- ❌ Älä luota pelkkiin numeroihin - tarkista ilmakuvasta
- ❌ Älä unohda ilmoittaa verottajalle kun veroaineisto väärä
- ❌ Älä korjaa kaikkia pieniä eroja - keskity merkittäviin

**Tehostusvinkit:**
- 🔍 Käytä "Building_Area_difference" -visualisointia karttapohjaiseen priorisoitiin
- 📊 Järjestä attribuuttitaulu eron mukaan suurimmasta pienimpään
- 🎯 Suodata vain erot > 50 m² tai > 10%
- 🗂️ Käsittele alueittain - tehokkaampi työnkulku
- 💾 Vie väliraportteja - älä tee kaikkea kerralla

---

## Lisätietoja

Katso myös:
- [Puuttuvien rakennusten tarkastusohje](/työohjeet/PUUTTUVIEN_RAKENNUSTEN_TARKASTUSOHJE) - Rakennusten tunnistaminen ja yhdistäminen
- [Kiinteistöjen tarkastusohje](/työohjeet/KIINTEISTOJEN_TARKASTUSOHJE) - Kiinteistöjen pinta-alojen tarkastus

**Tuki:**
- contact.maplica@gmail.com

---

**Muista:** Pinta-ala-erot vaikuttavat suoraan verotukseen - huolellinen tarkastus on tärkeää sekä kunnan että veronmaksajan kannalta!
