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

**Taso:** Rakennukset_Yhdistetty_vero_ja_tietokanta (prosessoitu), Pinta-ala ero (vero - tietokanta)

**Karttasymbolit:** Rakennustyyppikohtaiset ikonit. **Ikonin koko** kertoo pinta-ala-eron suuruuden ja suunnan – mitä suurempi ikoni, sitä suurempi ero. Ikonin muoto kertoo rakennuksen tyypin.

**Ikonin koko kertoo pinta-ala-eron (vero − tietokanta):**

| Koko | Ero (m²) | Merkitys |
|------|----------|----------|
| **Erittäin suuri** | < −18 000 | Kriittinen: veroaineistossa paljon pienempi kuin rekisterissä |
| **Suuri** | −18 000 – −500 | Veroaineistossa huomattavasti pienempi |
| **Keskisuuri** | −500 – −25 | Veroaineistossa selkeästi pienempi |
| **Normaali** | −25 – −1 | Veroaineistossa hieman pienempi |
| **Pieni** | −1 – 1 | Pinta-alat täsmäävät (OK) |
| **Pienempi** | 1 – 25 | Veroaineistossa hieman suurempi |
| **Pienin** | 25 – 500 | Veroaineistossa huomattavasti suurempi |
| **Hyvin pieni** | > 500 | Kriittinen: veroaineistossa paljon suurempi kuin rekisterissä |

**Ikonin tyyppi kertoo rakennuslajin:**

| Ikoni | Rakennustyyppi |
|-------|----------------|
| ![Omakotitalo](/map_icons/omakotitalot.svg) | Omakotitalot |
| ![Paritalo](/map_icons/paritalot.svg) | Paritalot |
| ![Rivitalo](/map_icons/rivitalo.svg) | Rivitalot |
| ![Asuinrakennus](/map_icons/asuinrakennukset.svg) | Kerros- ja muut asuinrakennukset |
| ![Vapaa-ajan rakennus](/map_icons/vapaa_ajan_asuinrakennukset.svg) | Vapaa-ajan asuinrakennukset |
| ![Liikerakennus](/map_icons/liikerakennukset.svg) | Liike- ja majoitusrakennukset |
| ![Toimistorakennus](/map_icons/toimistorakennukset.svg) | Toimistorakennukset |
| ![Liikenteen rakennus](/map_icons/liikenteen_rakennukset.svg) | Liikenteen rakennukset |
| ![Hoitoalan rakennus](/map_icons/hoitoalan_rakennukset.svg) | Hoitoalan rakennukset |
| ![Kulttuurirakennus](/map_icons/kulttuurirakennukset.svg) | Kulttuuri- ja kokoontumisrakennukset |
| ![Uskonnollinen rakennus](/map_icons/uskonnollisten_rakennukset.svg) | Uskonnolliset rakennukset |
| ![Opetusrakennus](/map_icons/opetusrakennukset.svg) | Opetusrakennukset |
| ![Teollisuusrakennus](/map_icons/teollisuuden_rakennukset.svg) | Teollisuusrakennukset |
| ![Energiahuoltorakennus](/map_icons/energiahuoltorakennukset.svg) | Energiahuollon rakennukset |
| ![Vesihuoltorakennus](/map_icons/vesihuollon_rakennukset.svg) | Vesihuollon rakennukset |
| ![Jätehuoltorakennus](/map_icons/jätehuollon_rakennukset.svg) | Jätehuollon rakennukset |
| ![Varastorakennus](/map_icons/varastorakennukset.svg) | Varastorakennukset |
| ![Pelastustoimen rakennus](/map_icons/pelastustoimen_rakennukset.svg) | Pelastustoimen rakennukset |
| ![Maatalousrakennus](/map_icons/maatalousrakennukset.svg) | Maatalousrakennukset |
| ![Saunarakennus](/map_icons/saunarakennukset.svg) | Saunarakennukset |
| ![Talousrakennus](/map_icons/talousrakennukset.svg) | Talousrakennukset |

**Tulkinta:**
- **Suuret ikonit (negatiivinen ero):** Veroaineistossa pienempi pinta-ala kuin rekisterissä → mahdollinen veronmenetys
- **Pienet ikonit (positiivinen ero):** Veroaineistossa suurempi pinta-ala kuin rekisterissä → mahdollisesti liikaa veroa
- **Normaalikokoiset ikonit:** Pinta-alat täsmäävät, ei tarvetta toimenpiteisiin

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
   - Oikea klikkaus sarakkeen otsikkoa (esim. `Pinta-ala ero (vero - tietokanta)__added`)
   - Valitse **"Suodata"** tai **"Järjestä"**
   - Suodata esim. vain erot > 100 m² tai < -100 m²
   - Järjestä suurimmasta pienimpään priorisoidaksesi kriittisimmät

5. **Tarkastele kohdetta kartalla:**
   - Valitse rivi vasemmasta ikkunasta
   - Klikkaa **"Näytä kartalla"** -nappia
   - Kartta zoomaa rakennukseen ja korostaa sen

#### **Karttapohjaisesti:**

Ota käyttöön **Pinta-ala ero (vero - tietokanta)** -tyyli tasolle Rakennukset_Yhdistetty_vero_ja_tietokanta (prosessoitu). Löydä korjattavat kohteet kartalta **ikonien koon** perusteella – suuret ikonit osoittavat suurimmat erot. Käytä "Valitse kartalta" -työkalua, joka näyttää valitut kohteet listassa (Vasen ikkuna). Priorisoi arvokkaimmat alueet käsittelyyn ensin.

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
- 🔍 Käytä **Pinta-ala ero (vero - tietokanta)** -tyyliä karttapohjaiseen priorisointiin – etsi suurimmat ikonit
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
