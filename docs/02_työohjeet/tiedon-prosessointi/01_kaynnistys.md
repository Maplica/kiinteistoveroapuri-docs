---
sidebar_position: 2
---

# Prosessoinnin käynnistys

Tässä osiossa käydään läpi prosessoinnin aloittaminen vaihe vaiheelta. Varmista ensin, että olet suorittanut [esivalmistelut](./esivalmistelut.md).

---

## Vaihe 1: Avaa KiinteistöveroApuri-plugin QGIS:ssä

1. Käynnistä QGIS
2. Valitse valikosta `Plugins` → `KiinteistöveroApuri`
3. Paina "Tiedon prosessointi" -nappia, joka avaa prosessointi-ikkunan
4. Plugin-ikkuna avautuu kolmella välilehdellä

![Tiedon prosessointi -napin sijainti](/img/tiedonProsessointi.png)

---

## Vaihe 2: Täytä Välilehti 1 - Kunnan tietokanta

<!-- TODO: Lisää kuvakaappaus - Välilehti 1 kokonaisuudessaan -->
![Välilehti 1 - Kunnan tietokanta](/img/placeholder_valilehti1.png)

### A. Kiinteistöjen palsta tiedosto:

1. **Valitse tiedosto:**
   - Klikkaa "Selaa" nappia
   - Navigoi kiinteistöjen shapefile-tiedostoon
   - Valitse `.shp` tiedosto (Huom! tiedostossa pitäisi olla kaikki kiinteistöjen palstat eriteltynä toisistaan → Eli tiedostossa yksi rivi per kiinteistön palsta)

2. **Valitse sarakkeet pudotusvalikoista:**
   - **Kiinteistötunnus** → valitse sarake joka sisältää kiinteistötunnukset
   - **Palstan pinta-ala** → valitse numeerinen pinta-ala sarake
   - **Kaavan käyttötarkoitus** → valitse käyttötarkoitus sarake
     - Klikkaa "Valitse arvot" nappia
     - Valitse checkbox-listasta ne **kaavamerkinnät jotka ovat yleisiä alueita**
     - **Tärkeää:** Valitut kaavamerkinnät vaikuttavat siihen, miten nämä alueet huomioidaan prosessoinnissa
     - Esim: VL (Virkistysalue), VP (Puisto), Katualueet
   - **Vesialueen pinta-ala** → valitse vesialueen sarake

<!-- TODO: Lisää kuvakaappaus - Kiinteistöjen palsta -osion täytetyt kentät -->
![Kiinteistöjen palsta -sarakkeiden valinta](/img/placeholder_palsta_sarakkeet.png)

### B. Määräalojen palstatiedot:

1. Valitse tiedosto
2. Valitse **Määräalatunnus** sarake

### C. Rakennusten tiedot:

1. Valitse tiedosto
2. Valitse sarakkeet:
   - **PRT** (Pysyvä rakennustunnus)
   - **Kiinteistötunnus**
   - **Rakennuksen numero**
   - **Kokonaisala**
   - **Kerrosala**
   - **Tilavuus**

### D. Aluejakojen tiedot:

1. Valitse tiedosto
2. Valitse **Alueen tunniste** sarake (Sarake, joka erottaa alueen toisistaan esim. Nimi)

### E. Koordinaattijärjestelmä:

1. Valitse "CRS" napista koordinaattijärjestelmä (Huolehdi, että kaikilla tasoilla on sama koordinaattijärjestelmä)

:::tip Vinkki
Plugin muistaa aiemmat valinnat. Jos olet jo prosessoinut dataa aiemmin, kentät saattavat täyttyä automaattisesti.
:::

---

## Vaihe 3: Täytä Välilehti 2 - Verottajan tiedot

<!-- TODO: Lisää kuvakaappaus - Välilehti 2 kokonaisuudessaan -->
![Välilehti 2 - Verottajan tiedot](/img/placeholder_valilehti2.png)

1. **Verottajan kiinteistöverotiedot:**
   - Valitse verottajan kiinteistövero tiedosto. CSV-tiedosto, joka sisältää kaikki kunnan verotiedot.

2. **Verottajan kiinteistöveron tietue:**
   - Valitse verottajan antama tietue tiedosto, joka kertoo miten CSV-tiedostoa luetaan. Yleensä tämä on Excel-tiedosto (.xlsx).

---

## Vaihe 4: Täytä Välilehti 3 - Tallennus

<!-- TODO: Lisää kuvakaappaus - Välilehti 3 kokonaisuudessaan -->
![Välilehti 3 - Tallennus](/img/placeholder_valilehti3.png)

### A. Tulostiedostot:

Tallennusvälilehdellä määrityt polut määrittävät, minne prosessoinnin tulokset tallennetaan:

- **GeoPackage-tiedosto** - Sisältää kaikki paikkatiedon tasot (rakennukset, rakennusosat, kiinteistöt, määräalat) sekä yhdistetyt tiedot että puuttuvat/yhdistelemättömät kohteet
- **Excel-tiedostot** - Puuttuvien ja yhdistelemättömien kohteiden yksityiskohtaisemmat listat taulukkomuodossa
- **Tilastotiedot** - Alueittain lasketut tilastot (min, max, keskiarvo, summa) rakennuksista ja kiinteistöistä

### B. Henkilötunnukset:

- ☑️ **"Sisällytä henkilötunnukset"** 
  - Rasti päällä (Kyllä) → Kaikki omistajatiedot mukana tuloksissa (Myös HETU)
  - Rasti pois (Ei) → Kaikki omistajatiedot poistetaan tuloksista

### C. Koordinaattijärjestelmä tulosteille:

- Valitse koordinaattijärjestelmä, jolla lopputulos näkyy.
- Suositus: käytä samaa kuin alkuaineisto, tai samaa kuin muu aineisto jossa haluat toimia.

---

## Vaihe 5: Käynnistä prosessointi

1. Tarkista että kaikki kentät on täytetty (plugin validoi automaattisesti)
2. Klikkaa **"RUN"** nappia
3. Plugin:
   - Käynnistää prosessointiohjelman taustalla
   - Näyttää edistymis-ikkunan

<!-- TODO: Lisää kuvakaappaus - Edistymis-ikkuna prosessoinnin aikana -->
![Prosessoinnin edistymisikkuna](/img/placeholder_edistymisikkuna.png)

4. **Odota prosessoinnin valmistumista**
   - Prosessointi voi kestää muutamasta sekunnista useisiin minuutteihin riippuen datan koosta
   - **Älä sulje QGIS:ia** prosessoinnin aikana

5. **Valmis!**
   - Saat ilmoituksen kun prosessointi on valmis
   - Tulostiedostot löytyvät määrittämistäsi sijainneista
   - Tiedostot aukeavat painamalla suurta vihreää **"Avaa tiedostot"** nappia

<!-- TODO: Lisää kuvakaappaus - Valmis-ilmoitus ja "Avaa tiedostot" -nappi -->
![Prosessointi valmis](/img/placeholder_prosessointi_valmis.png)

---

:::tip Seuraava vaihe
Tutustu [parhaisiin käytäntöihin](./03_parhaat_kaytannot.md) prosessoinnin tulosten käsittelyssä.
:::
