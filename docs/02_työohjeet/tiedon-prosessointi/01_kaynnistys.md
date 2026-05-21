---
sidebar_position: 2
---

# Prosessoinnin käynnistys

Tässä osiossa käydään läpi prosessoinnin aloittaminen vaihe vaiheelta. Varmista ensin, että olet suorittanut [esivalmistelut](./esivalmistelut.md).

:::tip Tutustuitko alkuaineistoihin?
Jos et ole vielä tutustunut alkuaineistoihin, **nyt on hyvä hetki tehdä se** ennen prosessoinnin käynnistystä. Lataa jokainen aineisto erikseen QGIS:iin ja avaa attribuuttitaulukko (oikea klikkaus → Open Attribute Table) – näin tunnistat sarakkeiden nimet ja sisällön, ja osaat valita alla olevissa vaiheissa oikeat sarakkeet varmuudella.

👉 Tarkemmat ohjeet aineiston tarkastamiseen löydät [esivalmisteluista](./esivalmistelut.md#2-tutki-tietosisält%C3%B6).
:::

---

## Vaihe 1: Avaa KiinteistöveroApuri-plugin QGIS:ssä

1. Käynnistä QGIS
2. Valitse valikosta `Plugins` → `KiinteistöveroApuri`
3. Paina "Tiedon prosessointi" -nappia, joka avaa prosessointi-ikkunan
4. Plugin-ikkuna avautuu kolmella välilehdellä

![Tiedon prosessointi -napin sijainti](/img/tiedonProsessointi.png)

---

## Vaihe 2: Täytä Välilehti 1 - Kunnan tietokanta

<!-- PLACEHOLDER: Kuvakaappaus Välilehti 1 - Kunnan tietokanta kokonaisuudessaan -->

![Prosessointivälilehdet](/img/system_images/tabs_prosessointi.svg)

### A. Kiinteistöjen palsta tiedosto:

1. **Valitse tiedosto:**
   - Klikkaa "Selaa" nappia
   - Navigoi kiinteistöjen paikkatietotiedostoon
   - Valitse `.shp` (Shapefile) tai `.gpkg` (GeoPackage) -tiedosto
     - Jos käytät GeoPackagea, valitse avautuvasta listasta oikea taso
   - Huom! Tiedostossa pitäisi olla kaikki kiinteistöjen palstat eriteltynä toisistaan → yksi rivi per kiinteistön palsta

2. **Valitse sarakkeet pudotusvalikoista:**
   - **Kiinteistötunnus** → valitse sarake joka sisältää kiinteistötunnukset
   - **Palstan pinta-ala** → valitse numeerinen pinta-ala sarake
   - **Kaavan käyttötarkoitus** → valitse käyttötarkoitus sarake
     - Klikkaa "Valitse arvot" nappia

       ![Valitse arvot -painike](/img/system_images/btn_valitse_arvot.svg)
     - Valitse checkbox-listasta ne **kaavamerkinnät jotka tarkoittavat yleisiä alueita** (julkiset alueet, joilla ei tyypillisesti ole verotettavaa kiinteistöä)
     - Esim: `VL` (Virkistysalue), `VP` (Puisto), katualueet

     :::warning Miksi tämä on tärkeää?
     Merkityt kaavamerkinnät **jätetään pois kiinteistöverolaskennasta**. Jos yleinen alue jää merkitsemättä, se voi virheellisesti näyttää verotettavalta kohteelta. Jos taas vääriä merkintöjä valitaan, oikeita verotettavia kiinteistöjä voi jäädä pois tuloksista. Tarkista valinnat aina kunnan kaava-aineiston perusteella.
     :::
   - **Vesialueen pinta-ala** → valitse vesialueen sarake

![Kiinteistöt-ryhmä](/img/system_images/groupbox_kiinteistot.svg)

### B. Määräalojen palstatiedot:

![Määrä-alat-ryhmä](/img/system_images/groupbox_maaraalat.svg)

1. Valitse `.shp`- tai `.gpkg`-tiedosto
2. Valitse **Määräalatunnus** sarake

### C. Rakennusten tiedot:

![Rakennukset-ryhmä](/img/system_images/groupbox_rakennukset.svg)

1. Valitse `.shp`- tai `.gpkg`-tiedosto
2. Valitse sarakkeet:
   - **PRT** (Pysyvä rakennustunnus)
   - **Kiinteistötunnus**
   - **Rakennuksen numero**
   - **Kokonaisala**
   - **Kerrosala**
   - **Tilavuus**

### D. Aluejakojen tiedot:

![Aluejaot-ryhmä](/img/system_images/groupbox_aluejaot.svg)

1. Valitse `.shp`- tai `.gpkg`-tiedosto
2. Valitse **Alueen tunniste** sarake (Sarake, joka erottaa alueen toisistaan esim. Nimi)

### E. Koordinaattijärjestelmä:

1. Klikkaa "CRS"-nappia ja valitse koordinaattijärjestelmä

   :::warning Valitse ennalta määritelty koordinaattijärjestelmä
   Valitse koordinaattijärjestelmä aina **ennalta määriteltyjen koordinaattijärjestelmien listasta** (Predefined CRS). Älä käytä muokattuja tai käyttäjän määrittelemiä koordinaattijärjestelmiä (User-defined CRS) – ne voivat aiheuttaa virheitä sijaintilaskennassa tai yhteensovittamisessa muiden aineistojen kanssa.

   Suomessa yleisin käytössä oleva järjestelmä on **ETRS89 / TM35FIN (EPSG:3067)**. Varmista, että kaikilla aineiston tasoilla on sama koordinaattijärjestelmä ennen prosessoinnin käynnistystä.
   :::

:::tip Vinkki
Plugin muistaa aiemmat valinnat. Jos olet jo prosessoinut dataa aiemmin, kentät saattavat täyttyä automaattisesti.
:::

---

## Vaihe 3: Täytä Välilehti 2 - Verottajan tiedot

![Verottajan tiedostot](/img/system_images/groupbox_verottajan_tiedostot.svg)

1. **Verottajan kiinteistöverotiedot:**
   - Valitse verottajan CSV-tiedosto, joka sisältää kaikki kunnan kiinteistöverotiedot.

2. **Verottajan kiinteistöveron tietue:**
   - Valitse verottajan toimittama tietuekuvaus, joka määrittelee miten CSV-tiedostoa luetaan. Yleensä tämä on Excel-tiedosto (.xlsx).

---

## Vaihe 4: Täytä Välilehti 3 - Tallennus

![Tallennuspaikat](/img/system_images/groupbox_tallennuspaikat.svg)

### A. Tulostiedostot:

Tallennusvälilehdellä **valitset kansion**, johon kaikki prosessoinnin lopputiedostot tallennetaan. Klikkaa "Selaa"-nappia ja valitse tai luo haluamasi kohdekansio – prosessointi tallentaa kaikki alla listatut tiedostot automaattisesti sinne.

- **GeoPackage-tiedosto** - Sisältää kaikki paikkatiedon tasot (rakennukset, rakennusosat, kiinteistöt, määräalat) sekä yhdistetyt tiedot että puuttuvat/yhdistelemättömät kohteet
- **Excel-tiedostot** - Puuttuvien ja yhdistelemättömien kohteiden yksityiskohtaisemmat listat taulukkomuodossa
- **Tilastotiedot** - Alueittain lasketut tilastot (min, max, keskiarvo, summa) rakennuksista ja kiinteistöistä

:::tip Kansion valinta
Käytä selkeästi nimettyjä kansioita, esim. `tarkastus_2025/` tai `kiinteistovero_output_2025-05/`. Näin löydät tulostiedostot helposti myöhemmin ja eri vuosien tarkastukset pysyvät erillään.
:::

### B. Henkilötunnukset:

- ☑️ **"Sisällytä henkilötunnukset"** 
  - Rasti päällä (Kyllä) → Kaikki omistajatiedot mukana tuloksissa (Myös HETU)

    ![Henkilötunnukset mukana](/img/system_images/checkbox_hetu_kylla.svg)
  - Rasti pois (Ei) → Kaikki omistajatiedot poistetaan tuloksista

    ![Henkilötunnukset pois](/img/system_images/checkbox_hetu_ei.svg)

### C. Koordinaattijärjestelmä tulosteille:

- Valitse koordinaattijärjestelmä, jolla lopputulos näkyy.
- Suositus: käytä samaa kuin alkuaineisto, tai samaa kuin muu aineisto jossa haluat toimia.

---

## Vaihe 5: Käynnistä prosessointi

1. Tarkista että kaikki kentät on täytetty (plugin validoi automaattisesti)
2. Klikkaa **"RUN"** nappia

   ![RUN-painike](/img/system_images/btn_run.svg)
3. Plugin:
   - Käynnistää prosessointiohjelman taustalla
   - Näyttää edistymis-ikkunan

![Prosessoinnin edistymisikkuna](/img/system_images/dialog_progress_loading.svg)

4. **Odota prosessoinnin valmistumista**
   - Prosessointi voi kestää muutamasta sekunnista useisiin minuutteihin aineiston koosta riippuen
   - **Älä sulje QGIS:iä** prosessoinnin aikana

5. **Valmis!**
   - Saat ilmoituksen kun prosessointi on valmis
   - Tulostiedostot löytyvät määrittämistäsi sijainneista
   - Tiedostot aukeavat painamalla suurta vihreää **"Avaa tiedostot"** nappia

![Valmis-ilmoitus ja Avaa tiedostot](/img/system_images/dialog_completion_avaa_tiedostot.svg)

---

:::tip Seuraava vaihe
Tutustu [parhaisiin käytäntöihin](./03_parhaat_kaytannot.md) prosessoinnin tulosten käsittelyssä.
:::
