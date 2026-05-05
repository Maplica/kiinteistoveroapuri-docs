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
2. **Karttatyyli:** 🟢 Kirkkaan vihreä bullseye-ympyrä rakennusta per piste
3. **Suodata ja priorisoi:** Järjestä verosumman tai kiinteistötunnuksen mukaan. Suodata ulos vähemmän tärkeät rakennukset tyypin tai pinta-alan mukaan.
4. **Tunnista syyt:** Uusi rakennus / Väärä PRT / Todella puuttuu rekisteristä
5. **Tutki:** Klikkaa kartalla, tarkista ilmakuvasta, etsi rekisteristä manuaalisesti
6. **Korjaa:**
   - Jos löydät → korjaa PRT/tunnisteet.
   - Jos ei löydy → lisää rekisteriin.
   - Valitsemalla rivi vasemmassa tieto-ikkunassa ja siirtämällä se oikeaan käsittelyikkunaan painikkeella:
   
   ![Siirrä lisättyihin -painike](/img/system_images/btn_move_right.svg)
   
   Jos tulee virhe voi rivin siirtää takaisin toisella painikkeella.
   
   ![Siirrä kohteisiin -painike](/img/system_images/btn_move_left.svg)
   
   - Korjaa tiedot ja tallenna

**Vinkki 1:** Kannattaa pitää taso Rekisterin_rakennukset_puuttuvat_verotiedosta auki samalla.

**Vinkki 2:** Tarkista, onko kiinteistöllä rekisterin rakennuksia, jotka puuttuvat verotiedoista (symboli 🔶 oranssi kuusikulmio). Voi olla, että rakennus löytyy, mutta rekisteritiedot eivät täsmää. Korjaa tällöin tiedot oikein oikeassa paikassa.

## Taso 2: Rekisterin_rakennukset_puuttuvat_verotiedosta

**Sisältö:** Rakennukset, joilla rekisteritiedot mutta ei verotietoja – veronmenetysriski.

**Käyttö:**

1. Avaa taso QGISissä (tuplaklikkaa GeoPackage)
2. **Karttasymboli:** 🔶 Oranssi kuusikulmio (Status=0 "Check") tai 🟩 Vihreä kuusikulmio (Status=1 "OK")
   

3. **Suodata ja priorisoi:** Järjestä verosumman tai kiinteistötunnuksen mukaan. Suodata ulos vähemmän tärkeät rakennukset tyypin tai pinta-alan mukaan.
4. **Tunnista syyt:** Uusi rakennus / Väärä PRT / Todella puuttuu verorekisteristä
5. **Korjaa:** Jos ei verovapaa → ilmoita verottajalle
   - Valitsemalla rivi vasemmassa tieto-ikkunassa ja siirtämällä se oikeaan käsittelyikkunaan painikkeella
   
   ![Siirrä lisättyihin -painike](/img/system_images/btn_move_right.svg)
   
   Jos tulee virhe voi rivin siirtää takaisin toisella painikkeella.
   
   ![Siirrä kohteisiin -painike](/img/system_images/btn_move_left.svg)
   
   - Korjaa tiedot tarvittaessa, kommentoi ja tallenna
   - Tallenna tasomuokkaukset

**Vinkki 1:** Tarkista samalla kiinteistöltä Taso 1 (Veroaineiston_rakennukset_puuttuvat_rekisteristä, symboli 🟢 vihreä ympyrä). Voi olla, että rakennuksen tiedot eivät täsmää, jolloin se näkyy molemmissa tasoissa.

**Vinkki 2:** Hyödynnä suodatusta löytääksesi ne rakennukset, joilla on suurin todennäköisyys tuottaa lisätuloja (omakotitalot, kerrostalot, rivitalot, teollisuusrakennukset).

**Vinkki 3:** Tarkistukseen voi hyödyntää kunnan ilmakuvia varmistaakseen, että rakennus on olemassa. Lataa se QGIS-taustaksi. 

## Taso 3: Rakennukset_Pistepuutteet_lkm_Vero_vs_Rekisteri

**Sisältö:** Tilastollinen näkymä – kiinteistökohtaiset lukumääräerot.

**Kartatyylit:**
- 🟨 **Keltainen** = Verotuksessa enemmän rakennuksia kuin tietokannassa
- 🟥 **Pinkki/magenta** = Tietokannassa enemmän rakennuksia kuin verotuksessa
- 🟩 **Vihreä** = Lukumäärä täsmää kummassakin järjestelmässä

**Käyttö:**

Taso antaa nopean yleiskuvan tilanteesta alueittain. Käytä sitä tarkastuksen alussa priorisoimaan, mistä lähdeä liikkeelle:

1. Avaa taso ja ota käyttöön `Valitse kartalta` -työkalu
2. Keltaiset ja pinkit kiinteistöt ovat sellaiä, joilla lukumäärät eivät täsmää — näistä kannattaa aloittaa
3. Vihreät kiinteistöt näyttävät tasaiselta, mutta voivat silti sisältää yhdistämättömiä rakennuksia — tarkista myös ne, jos aikaa jää
4. Klikkaa kiinteistöä kartalta — tiedot näytetään listassa (vasen ikkuna), josta voit siirtää kohteen käsittelyyn

Taso ei itsessään käynnistä käsittelytoimenpiteitä — sen perusteella priorisoidaan, minkä kiinteistöjen rakennukset otetaan tarkasteluun tasoilta 1 ja 2.


## 4. Käytännön työnkulku

Aloita avaamalla tallennettu verotarkastus QGIS-projekti. Voit valita kaksi työskentelytapaa:

**Listapohjaisesti:** Suodata suoraan Taso 1 ja Taso 2 -listoja (Vasen ikkuna) ja käy kohteet läpi listasta. Suodatus aukeaa oikea-klikkaamalla sarakkeen otsikkoa. Käytä “Näytä kartalla” -nappia tarkastellaksesi valittua kohdetta kartalla.

![Näytä kartalla -painike](/img/system_images/btn_nayta_kartalla.svg)

**Karttapohjaisesti:** Tutki Taso 3 -karttaa saadaksesi kokonaiskuvan tilanteesta – keltaiset ja pinkit alueet näyttävät ongelmakiinteistöt. Käytä "Valitse kartalta" -työkalua, joka näyttää valitut kohteet listassa (Vasen ikkuna). Priorisoi arvokkaimmat alueet käsittelyyn ensin hyödyntäen kartan värityksiä.

![Valitse kartalta -painike](/img/system_images/btn_valitse_kartalta.svg)

Rakennusten käsittelyjärjestystä kannattaa priorisoida suodatusta käyttäen. Suodatus aukeaa oikea-klikkaamalla sarakkeen otsikkoa. Valitse haluamasi arvot ja paina OK.

Suodatuksen saa pois joko menemällä takaisin kyseisen sarakkeen suodatusikkunaan ja poistamalla suodatuksen tai painamalla "Tyhjennä suodatus" -nappia. Näkyviä sarakkeita voi muuttaa painamalla XX/XX-nappia ja valitsemalla halutut sarakkeet.

![Tyhjennnä suodattimet](/img/system_images/btn_tyhjenna_suodatus.svg) ![Sarakkeiden valintapainike](/img/system_images/btn_column_selector.svg)

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

Luo raportit painamalla "Luo tiedosto" -nappia. Ohjelma luo automaattisesti oikeat tiedostot käsittelemienne kohteiden perusteella:

- Kohteet tasolta **Rekisterin_rakennukset_puuttuvat_verotiedosta** päätyvät tiedostoon `Rakennus_puuttuvat.csv` — lähetä tämä verottajalle.
- Kohteet tasolta **Veroaineiston_rakennukset_puuttuvat_rekisteristä** päätyvät tiedostoon `Rakennus_Rekisterikorjaus_Kunta.csv` — päivitä kunnan rekisteri.
- Jos olet muokannut kohteen kenttiä, kohde lisätään myös asianomaiseen rekisterikorjaustiedostoon muutostietoineen.

Lähetä raportit eteenpäin, päivitä rekisterit ja korjaa tunnisteet jatkotoimina.

![Luo tiedosto -painike](/img/system_images/btn_luo_tiedosto.svg)

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

Katso myös:
- [Kiinteistöjen tarkastusohje](./KIINTEISTOJEN_TARKASTUSOHJE.md)
- [Pinta-alojen tarkastusohje](./PINTA-ALOJEN_TARKASTUSOHJE.md)
- [Tulosaineistojen opas](../03_toiminnot/04_output_taso_ohje.md)
- [Pääikkuna](../03_toiminnot/01_paaikkuna.md) — painikkeiden toiminnot

**Tuki:** contact.maplica@gmail.com
