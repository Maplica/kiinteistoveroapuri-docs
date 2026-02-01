# Kiinteistöjen ja maapohjien tarkastusohje

Tämä ohje opastaa käyttämään KiinteistöveroApuri-työkalua kiinteistöjen ja maapohjien tarkastamiseen. Työkalu vertaa kunnan rekisteriä ja verottajan tietoja, tunnistaa erot kiinteistötiedoissa ja auttaa korjaamaan virheellisiä tietoja.

Prosessointi luo kolme keskeistä tasoa kiinteistöjen tarkastukseen:

## Tasojen kuvaukset

### Taso 1: Kiinteistöt_Yhdistetty_vero_ja_tietokanta

**Sisältö:** Kiinteistöt joilla sekä rekisteritiedot että verotiedot täsmäävät.

**Käyttö:**
Taso sisältää yhdistetyt tiedot molemmista lähteistä ja mahdollistaa erojen analysoinnin:
- Aluehinta-analysointi (eri visualisointitapoja)
- Ranta-kiinteistöjen tunnistus
- Kaava-alueiden tarkastelu
- Kiinteistöverosummien vertailu

**Karttasymboolit:**
Visualisointitapa riippuu valitusta analyysistä (Aluehinta, Ranta, Kaava_alue, Kiinteistövero). Kaikki käyttävät graduated/categorized symbologiaa.

**Kentät:**
- Kiinteistötunnus (molemmista lähteistä)
- Pinta-ala (kunta ja vero)
- Aluehinta (€/m²)
- Kiinteistövero (€)
- Kaavan käyttötarkoitus
- Ranta (Kyllä/Ei)

### Taso 2: Rekisterin_Kiinteistöt_puuttuvat_verotiedosta

**Sisältö:** Kiinteistöt joilla on rekisteritiedot mutta ei verotietoja - mahdollisia veronmenetysriskejä tai verovapaa kiinteistöjä.

**Käyttö:**
Tunnista kiinteistöt jotka:
- Ovat verovelvollisia mutta puuttuvat verotuksesta
- Ovat verovapaa ja dokumentoitava sellaiseksi
- Ovat uusia kiinteistöjä joita ei ole vielä verotettu
- Sisältävät virheellisiä kiinteistötunnuksia

**Karttasymboolit:**
🟧 **Oranssi täyttö** = Tarkistettava kiinteistö

**Kentät:**
- Kiinteistötunnus (kunta)
- Pinta-ala (kunta)
- Kaavan käyttötarkoitus

### Taso 3: Maara-ala_Yhdistetty_vero_ja_tietokanta (prosessoitu)

**Sisältö:** Määrä-alojen tiedot yhdistettynä vero- ja rekisteritiedoista.

**Käyttö:**
Taso sisältää yhdistetyt tiedot molemmista lähteistä ja mahdollistaa erojen analysoinnin:
- Aluehinta-analysointi (eri visualisointitapoja)
- Ranta-kiinteistöjen tunnistus
- Kaava-alueiden tarkastelu
- Kiinteistöverosummien vertailu

**Karttasymboolit:**
Visualisointitapa riippuu valitusta analyysistä (Aluehinta, Ranta, Kaava_alue, Kiinteistövero). Kaikki käyttävät graduated/categorized symbologiaa.

**Kentät:**
- Kiinteistötunnus (molemmista lähteistä)
- Pinta-ala (kunta ja vero)
- Aluehinta (€/m²)
- Kiinteistövero (€)
- Kaavan käyttötarkoitus
- Ranta (Kyllä/Ei)


## Käytännön työnkulku

Aloita avaamalla tallenettu verotarkastus QGIS-projekti. Voit valita kaksi työskentelytapaa:

**Listapohjaisesti:** Suodata suoraan Taso 1 ja Taso 2 listoja (Vasen ikkuna) ja käy kohteet läpi listasta. Suodatus aukeaa oikea-klikkaamalla sarakkeen otsikkoa. Käytä "Näytä kartalla" -nappia tarkastellaksesi valittua kohdetta kartalla.

**Karttapohjaisesti:** Tutki Taso 1:n eri visualisointeja (Aluehinta, Ranta, Kaava_alue, Kiinteistövero) karttaa saadaksesi kokonaiskuvan tilanteesta. Käytä "Valitse kartalta" -työkalua, joka näyttää valitut kohteet listassa (vasen ikkuna). Priorisoi tarkastettavat kiinteistöt haluamallasi tavalla.

Kiinteistöjen käsittelyjärjestystä kannattaa priorisoida käyttämällä suodatusta. Suodatus aukeaa oikea-klikkaamalla sarakkeen otsikkoa. Hae ja valitse haluamasi arvot ja paina OK. Suodatuksen saa pois joko menemällä takaisin kyseisen sarakkeen suodatus-ikkunaan ja poistamalla suodatus tai painamalla "Tyhjennä suodatus" -nappia, joka poistaa kaiken suodatuksen. Näkyviä sarakkeita voi muuttaa painamalla XX/XX-nappia ja valitsemalla ne sarakkeet jotka haluaa näkyvän.

### Taso 2: Puuttuvien kiinteistöjen käsittely

Käsittele Taso 2 (Rekisterin_Kiinteistöt_puuttuvat_verotiedosta):
Aloita haluamallasi tavalla:
 - Karttapohjainen käsittely (Valitse kartalta työkalun avulla)
 - Lista pohjainen työskentely (Näytä kartalla työkalun avulla)

Tarkista kiinteistö ja arvioi puuttuuko kiinteistö oikeasti verotiedoista:
- **Verovelvollinen kiinteistö:** Jos kiinteistö on verovelvollinen (esim. rakennettu, asuin-, liike-, tai teollisuuskiinteistö) → ilmoita verottajalle
- **Verovapaa kiinteistö:** Jos kiinteistö on verovapaa (julkinen rakennus, kirkko, maatalouskiinteistö alle rajan) → dokumentoi verovapaus.
- **Uusi kiinteistö:** Jos kiinteistö on vasta perustettu → seuraa ja tarkista seuraavassa prosessoinnissa
- **Virheellinen kiinteistötunnus:** Jos kiinteistötunnus on väärä → korjaa tunnus rekisterissä

Valitse rivi vasemmasta ikkunasta, siirrä oikeaan käsittelyikkunaan. Tuplaklikkaa siirrettyä riviä jolloin aukeaa käsiteltävä ikkuna, korjaa tiedot tarvittaessa, lisää kommentti ja tallenna. Merkitse Status = 1 kun tarkastettu. Tallenna muokkaukset.

### Taso 1: Yhdistettyjen kiinteistöjen analysointi

Käsittele Taso 1 (Kiinteistöt_Yhdistetty_vero_ja_tietokanta):
Aloita haluamallasi tavalla:
 - Karttapohjainen käsittely (Valitse kartalta työkalun avulla)
 - Lista pohjainen työskentely (Näytä kartalla työkalun avulla)

**Tärkeimmät tarkistuskohteet:**

1. **Aluehinta-erot:** Tarkista onko alueellisa eroja aluehinnassa. (Karttapohjainen tarkistus)
   - Suuret erot (esim. >10 €/m²) vaativat tarkastusta

2. **Käyttötarkoitus-ristiriidat:** Analysoi onko kiinteistön käyttötarkoitus oikein
   - Tarkista Kaava_alue kenttä
   - Varmista että verotus vastaa käyttötarkoitusta

3. **Ranta-kiinteistöt:** Tarkista rantakiinteistöjen verotus
   - Käytä Ranta-visualisointia
   - Varmista että rantakiinteistöt on tunnistettu oikein molemmissa järjestelmissä

Valitse rivi vasemmasta ikkunasta, siirrä oikeaan käsittelyikkunaan. Tuplaklikkaa siirrettyä riviä jolloin aukeaa käsiteltävä ikkuna. Tarkista tiedot, vertaa kunnan ja verottajan tietoja, korjaa virheelliset tiedot tarvittaessa, lisää kommentti ja tallenna. Tallenna muokkaukset.

### Raportointi

Luo valmis raportti verottajalle painamalla "Luo tiedosto" -nappia. Tämä tekee kaikista käsitellyistä kiinteistöistä raportin.
Lähetä lista verottajalle, päivitä rekisteri ja korjaa virheelliset tiedot jatkotoimina.

Muista tallentaa käsitellyt kohteet ja QGIS-projekti lopettaessa.

## Yleisimmät syyt ja ratkaisut

### Kiinteistöt puuttuvat verotiedoista

| Syy | Toimenpide |
|-----|------------|
| Uusi kiinteistö | Merkitse seurantaan, tarkista seuraavassa prosessoinnissa |
| Verovapaa (julkinen/kirkko/maatalouskiinteistö) | Tarkista verovapaus, dokumentoi |
| Lakkautettu kiinteistö | Poista rekisteristä jos kiinteistö on lakkautettu |
| Väärä kiinteistötunnus | Korjaa tunnus rekisterissä ja synkronoi verottajan kanssa |

### Tietojen ristiriidat yhdistetyssä tasossa

| Syy | Toimenpide |
|-----|------------|
| Aluehinta eroaa | Tarkista oikea aluehinta, korjaa väärä tieto |
| Pinta-ala eroaa | Tarkista mittaustiedot, korjaa virheellinen tieto |
| Käyttötarkoitus eroaa | Tarkista kaavamääräykset, päivitä oikea käyttötarkoitus |
| Ranta-status eroaa | Tarkista kiinteistön sijainti, korjaa rantakiinteistömerkintä |

## Analyysityökalut

### Aluehinta-analyysi

Käytä Taso 1:n Aluehinta-visualisointia:
- Tunnista kiinteistöt joiden aluehinta poikkeaa alueellisesta keskiarvosta
- Vertaa naapurikiinteistöjen aluehintoja
- Havaitse mahdolliset virheelliset hinnoittelut

### Ranta-analyysi

Käytä Taso 1:n Ranta-visualisointia:
- Tunnista rantakiinteistöt kartalta
- Varmista että kaikki rantakiinteistöt on merkitty oikein
- Tarkista rantakiinteistöjen verotus

### Kaava-alue-analyysi

Käytä Taso 1:n Kaava_alue-visualisointia:
- Ryhmittele kiinteistöt käyttötarkoituksen mukaan
- Tunnista virheelliset käyttötarkoitusmerkinnät
- Varmista että verotus vastaa käyttötarkoitusta

### Kiinteistövero-analyysi

Käytä Taso 1:n Kiinteistövero-visualisointia:
- Tunnista korkean verotuksen kiinteistöt
- Vertaa verosummia alueellisesti
- Havaitse poikkeamat verotuksessa

## Parhaat käytännöt

**Tee näin:**
- Priorisoi kiinteistöt verosumman mukaan → Maksimoi verotulot
- Käytä kartan eri visualisointeja → Nopea erojen havaitseminen
- Dokumentoi kommentti-kenttään ja lisää huomiot
- Työstä alueittain → Tehokkaampi tarkastus
- Kommunikoi verottajan kanssa säännöllisesti
- Tallenna

**Vältä näitä:**
- Älä oleta verovapauksia - tarkista aina
- Älä luota pelkkiin tunnuksiin - vahvista kartalta
- Älä poista mitään rekisteristä ennen varmistusta
- Älä jaa henkilötietoja
- Älä unohda tallentaa muutoksia


## Lisätietoja

Katso tarkemmat tiedot:
- Järjestelmän kokonaiskuvaus
- Yksityiskohtaiset tasokuvaukset
- Yleinen prosessointiohje
- Tekninen dokumentaatio

