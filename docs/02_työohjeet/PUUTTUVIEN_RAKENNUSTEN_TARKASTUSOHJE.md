---
sidebar_position: 2
---
# Puuttuvien rakennusten tarkastusohje

Tämä ohje opastaa käyttämään KiinteistöveroApuri-työkalua puuttuvien rakennusten tunnistamiseen. Työkalu vertaa kunnan rekisteriä ja verottajan tietoja, tunnistaa erot ja tuottaa raportit korjaamista varten.

Prosessointi luo kolme keskeistä tasoa puuttuvien rakennusten tarkastukseen:

## Taso 1: Veroaineiston_rakennukset_puuttuvat_rekisteristä

**Sisältö:** Rakennukset, joilla verotiedot mutta ei rekisteritietoja, joku maksaa veroa rakennuksesta, jota ei ole tietokannassa.

**Käyttö:**

1. Avaa taso QGISissä
2. **Karttasymboli:** !!!Tähän KUVA!!! Vihreä ympyrä
3. **Suodata ja priorisoi:** Järjestä verosumman tai kiinteistötunnuksen mukaan. Suodata ulos vähemmän tärkeät rakennukset tyypin tai pinta-alan mukaan.
4. **Tunnista syyt:** Uusi rakennus / Väärä PRT / Todella puuttuu rekisteristä
5. **Tutki:** Klikkaa kartalla, tarkista ilmakuvasta, etsi rekisteristä manuaalisesti
6. **Korjaa:**
   - Jos löydät → korjaa PRT/tunnisteet.
   - Jos ei löydy → lisää rekisteriin.
   - Valitsemalla rivi vasemmassa tieto-ikkunassa ja siirtämällä se oikeaan käsittelyikkunaan painikkeella:
   
   ![](\img\logo.svg)
   
   Jos tulee virhe voi rivin siirtää takaisin toisella painikkeella.
   
   ![](\img\logo.svg)
   
   - Korjaa tiedot ja tallenna

**Vinkki 1:** Kannattaa pitää taso Rekisterin_rakennukset_puuttuvat_verotiedosta auki samalla.

**Vinkki 2:** Tarkista, onko kiinteistöllä rekisterin rakennuksia, jotka puuttuvat verotiedoista (symboli 🔶 oranssi kuusikulmio). Voi olla, että rakennus löytyy, mutta rekisteritiedot eivät täsmää. Korjaa tällöin tiedot oikein oikeassa paikassa.

## Taso 2: Rekisterin_rakennukset_puuttuvat_verotiedosta

**Sisältö:** Rakennukset, joilla rekisteritiedot mutta ei verotietoja – veronmenetysriski.

**Käyttö:**

1. Avaa taso QGISissä (tuplaklikkaa GeoPackage)
2. **Karttasymboli:** 🔶 Oranssi kuusikulmio (Status=0 "Check") tai 🟩 Vihreä kuusikulmio (Status=1 "OK")

   ![](\img\logo.svg)

3. **Suodata ja priorisoi:** Järjestä verosumman tai kiinteistötunnuksen mukaan. Suodata ulos vähemmän tärkeät rakennukset tyypin tai pinta-alan mukaan.
4. **Tunnista syyt:** Uusi rakennus / Väärä PRT / Todella puuttuu verorekisteristä
5. **Korjaa:** Jos ei verovapaa → ilmoita verottajalle
   - Valitsemalla rivi vasemmassa tieto-ikkunassa ja siirtämällä se oikeaan käsittelyikkunaan painikkeella
   
    ![Kuva Rekisterin_rakennukset_puuttuvat_verotiedosta (prosessoitu) symbooleista](/img/TasojenSymbooleja/Rekisterin_rakennukset_puuttuvat_verotiedosta (prosessoitu)/Rekisterin_rakennukset_puuttuvat_verotiedosta (prosessoitu).png)
   
   Jos tulee virhe voi rivin siirtää takaisin toisella painikkeella.
   
   ![](\img\logo.svg)
   
   - Korjaa tiedot tarvittaessa, kommentoi ja tallenna
   - Tallenna tasomuokkaukset

**Vinkki 1:** Tarkista samalla kiinteistöltä Taso 1 (Veroaineiston_rakennukset_puuttuvat_rekisteristä, symboli 🟢 vihreä ympyrä). Voi olla, että rakennuksen tiedot eivät täsmää, jolloin se näkyy molemmissa tasoissa.

**Vinkki 2:** Hyödynnä suodatusta löytääksesi ne rakennukset, joilla on suurin todennäköisyys tuottaa lisätuloja (omakotitalot, kerrostalot, rivitalot, teollisuusrakennukset).

**Vinkki 3:** Tarkistukseen voi hyödyntää kunnan ilmakuvia varmistaakseen, että rakennus on olemassa. Lataa se QGIS-taustaksi. 

## Taso 3: Rakennukset_Pistepuutteet_lkm_Vero_vs_Rekisteri

**Sisältö:** Tilastollinen näkymä – kiinteistökohtaiset lukumääräerot.

**Karttasymbolit:**
- 🟨 **Keltainen** = Tietokannassa enemmän rakennuksia kuin verotuksessa
- 🟪 **Pinkki/magenta** = Verotuksessa enemmän rakennuksia kuin tietokannassa
- 🟩 **Vihreä** = Rakennukset tietokanta = verotus (OK)

**Käyttö:**

Auttaa tunnistamaan ongelmakohteet kartalla. Pystyy käymään arvokkaammat alueet ensin läpi.


## 4. Käytännön työnkulku

Aloita avaamalla tallennettu verotarkastus QGIS-projekti. Voit valita kaksi työskentelytapaa:

**Listapohjaisesti:** Suodata suoraan Taso 1 ja Taso 2 -listoja (Vasen ikkuna) ja käy kohteet läpi listasta. Suodatus aukeaa oikea-klikkaamalla sarakkeen otsikkoa. Käytä "Näytä kartalla" -nappia tarkastellaksesi valittua kohdetta kartalla.

![](\img\logo.svg)

**Karttapohjaisesti:** Tutki Taso 3 -karttaa saadaksesi kokonaiskuvan tilanteesta – keltaiset ja pinkit alueet näyttävät ongelmakiinteistöt. Käytä "Valitse kartalta" -työkalua, joka näyttää valitut kohteet listassa (Vasen ikkuna). Priorisoi arvokkaimmat alueet käsittelyyn ensin hyödyntäen kartan värityksiä.

![](\img\logo.svg)

Rakennusten käsittelyjärjestystä kannattaa priorisoida suodatusta käyttäen. Suodatus aukeaa oikea-klikkaamalla sarakkeen otsikkoa. Valitse haluamasi arvot ja paina OK.

![](\img\logo.svg)

Suodatuksen saa pois joko menemällä takaisin kyseisen sarakkeen suodatusikkunaan ja poistamalla suodatuksen tai painamalla "Tyhjennä suodatus" -nappia. Näkyviä sarakkeita voi muuttaa painamalla XX/XX-nappia ja valitsemalla halutut sarakkeet.

![](\img\logo.svg)

### Käsittele Taso 2 (Rekisterin_rakennukset_puuttuvat_verotiedosta) – oranssit kuusikulmiot:

Aloita haluamallasi tavalla:
- Karttapohjainen käsittely (Valitse kartalta -työkalulla) tai
- Listapohjainen työskentely (Näytä kartalla -työkalulla)

Listapohjaisessa läpikäynnissä kannattaa hyödyntää suodatusta löytääksesi rakennukset, joilla on suurin todennäköisyys tuottaa lisätuloja. Tarkista rakennus ja arvioi, puuttuuko se oikeasti verotiedoista.

- Onko samalla kiinteistöllä tasolla Veroaineiston_rakennukset_puuttuvat_rekisteristä piste, joka vastaa kyseistä pistettä tasolla Rekisterin_rakennukset_puuttuvat_verotiedosta? Jos näin on, kyse on rekisterivirheestä.
- Ainoa piste kiinteistöllä, rakennuksella oikea kiinteistötunnus ja rakennus on olemassa (ei purettu) = ilmoita verottajalle.

Valitse rivi vasemmasta ikkunasta, siirrä oikeaan käsittelyikkunaan. Tuplaklikkaa siirrettyä riviä, jolloin aukeaa käsittelyikkuna; korjaa tiedot tarvittaessa, lisää kommentti ja tallenna. Tallenna muokkaukset.

### Käsittele seuraavaksi Taso 1 (Veroaineiston_rakennukset_puuttuvat_rekisteristä) – vihreät ympyrät:

Aloita haluamallasi tavalla:
- Karttapohjainen käsittely (Valitse kartalta) tai
- Listapohjainen työskentely (Näytä kartalla)

Tarkista ilmakuvasta, että rakennus on olemassa. Tunnista syy: onko kyseessä uusi rakennus, väärä PRT-tunnus vai todella rekisteristä puuttuva rakennus. Jos löydät rakennuksen, korjaa PRT-tunnisteet siirtämällä rivi käsittelyikkunaan ja tallentamalla. Jos rakennusta ei löydy, lisää se rekisteriin ja hanki tarvittavat mittaustiedot. Tallenna muokkaukset.

Pidä samalla Taso 2 auki – tarkista onko samalla kiinteistöllä oransseja kuusikulmioita, sillä samat rakennukset voivat näkyä molemmissa tasoissa, jos tiedot eivät täsmää.

### Raportointi

Luo valmis raportti verottajalle painamalla "Luo tiedosto" -nappia. Tämä tekee kaikista käsitellyistä puuttuvista rakennuksista raportin. Lähetä lista verottajalle, päivitä rekisteri ja korjaa tunnisteet jatkotoimina.

![](\img\logo.svg)

Muista tallentaa käsitellyt kohteet ja QGIS-projekti lopettaessa.


## 5. Yleisimmät syyt ja ratkaisut

### Verotiedoista puuttuvat

| Syy | Toimenpide |
|-----|------------|
| Uusi rakennus (&lt;2 v) | Merkitse seurantaan, tarkista seuraavassa prosessoinnissa |
| Verovapaa (julkinen/kirkko/maatalous/pieni) | Tarkista verovapaus, dokumentoi |
| Purettu rakennus | Poista rekisteristä |
| Omistajan laiminlyönti | Ota yhteyttä/ilmoita verottajalle |

### Rekisteristä puuttuvat

| Syy | Toimenpide |
|-----|------------|
| Väärä PRT-tunnus | Korjaa PRT, synkronoi verottajan kanssa |
| Puutteellinen rekisteri | Lisää rakennus, hanki mittaustiedot |
| Väärä kiinteistötunnus | Korjaa tunnus, tarkista omistajuus |
| Luvaton rakennus | Selvitä lupa-asia, lisää kun lupa myönnetty |


## 6. Excel-raportit

Prosessointi luo kaksi Excel-raporttia taulukkolaskentakäsittelyä varten:

**Raportti 1: Rekisterin rakennukset puuttuvat verotiedosta**
- Sisältää: Kiinteistötunnus, PRT, rakennusvuosi, pinta-ala
- Valmiiksi lähetettävissä verottajalle (Veroilmoitin)

## 7. Parhaat käytännöt

**Tee näin:**
- Priorisoi isot euromäärät → maksimoi verotulot
- Käytä ilmakuvia → nopea visuaalinen tarkastus
- Dokumentoi kommenttikenttään ja lisää huomiot
- Työstä alueittain → tehokkaampi kenttätyö
- Kommunikoi verottajan kanssa säännöllisesti
- Tallenna

**Vältä näitä:**
- Älä oleta verovapauksia – tarkista aina
- Älä jätä >3 v vanhoja rakennuksia selvittämättä
- Älä luota pelkkiin tunnuksiin – vahvista ilmakuvista
- Älä poista mitään rekisteristä ennen varmistusta
- Älä jaa henkilötietoja

**Tehostusvinkit:**
- Käytä suodattimia
- Tallenna QGIS-projekti asetuksineen toistuvaa käyttöä varten

## 8. Ongelmatilanteita

**Kaikki rakennukset näkyvät puuttuvina:**
- Syy: PRT-tunnukset eivät täsmää, väärät sarakkeet
- Ratkaisu: Tarkista PRT-sarakkeen valinta, vertaa tunnusmuotoja

**Liikaa puuttuvia verotiedoista:**
- Syy: Verovapaat mukana, paljon pieniä sivurakennuksia, maatalousalue
- Ratkaisu: Suodata pienet (&lt;15 m²), tunnista verovapaat käyttötarkoituksesta

**Sama rakennus puuttuu molemmista:**
- Syy: PRT-tunnus eri muodossa kummassakin, kirjoitusvirhe
- Ratkaisu: Etsi manuaalisesti kummastakin, vertaa tunnuksia, korjaa virhe

## 10. Lisätietoja

Katso tarkemmat tiedot:
- Järjestelmän kokonaiskuvaus
- Yksityiskohtaiset tasokuvaukset
- Yleinen prosessointiohje
- Tekninen dokumentaatio


