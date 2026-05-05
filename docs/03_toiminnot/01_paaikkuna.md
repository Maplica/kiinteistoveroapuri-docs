---
sidebar_position: 1
---

# Pääikkuna

![kuva käyttöliittymästä](/img/paaikkuna.png)

## Pääikkunan painikkeet

### Tason valintavalikko

![kuva käyttöliittymästä](/img/tasonValinta.png)

Tarkoitus: Mahdollistaa sen QGIS-karttatason valinnan, jonka kanssa haluat työskennellä.
Mitä se tekee: Kun valitset tason tästä valikosta, ohjelma lataa kaikki kyseisen tason kohteet vasempaan taulukkoon. Se suodattaa automaattisesti näyttääkseen vain tiettyjen ryhmien tasoja (Rakennukset, Rakennuksen Osat, Kiinteistöjen Palstat). Kun taso on valittu, sen kohteet näytetään sivutuksella, ja voit suodattaa, lajitella ja työskennellä datan kanssa. Valikko näyttää paikkamerkin "--- Valitse Taso ---" kun mitään ei ole valittuna.

### Sarakkeiden valintapainike

![kuva käyttöliittymästä](/img/sarakkeidenValinta.png)

Teksti: Näyttää "N/M ▼" ja "____", missä N on valittujen sarakkeiden määrä, M on sarakkeiden kokonaismäärä
Mitä se tekee: Avaa valintaikkunan, jossa voit valita, mitkä sarakkeet valitusta tasosta tulisi näyttää vasemmassa taulukossa. Valintaikkuna näyttää valintaruudut jokaiselle kentälle, "Valitse kaikki" ja "Poista valinnat" -vaihtoehdoilla. Sarakkeiden nimet näytetään ilman teknisiä päätteitä (__vero, __kunta, __added) helpomman lukemisen vuoksi. Valintasi muistetaan tasokohtaisesti, joten kun palaat samaan tasoon, aikaisemmat valintasi palautetaan.

### Valitse kartalta -painike

![kuva käyttöliittymästä](/img/valitseKartalta.png)

Kuvake: Käsi-osoitinkuvake
Vihjeteksti: "Valitse haluamasi kohde kartalta"
Mitä se tekee: Vaihtaa kartan tunnistustilan päälle/pois. Kun aktivoitu (painike pysyy painettuna ja muuttuu vihreäksi), voit napsauttaa kohteita suoraan QGIS-karttapohjalla. Napsautettu kohde valitaan automaattisesti vasemmassa taulukossa, ja ohjelma siirtyy oikealle sivulle, jos sivutus on aktiivinen. Kartta keskitetään automaattisesti valittuun kohteeseen. Napsauta painiketta uudelleen tämän tilan poistamiseksi. Painike on pois käytöstä, kunnes valitset tason.

### Tyhjennä suodattimet -painike

![kuva käyttöliittymästä](/img/tyhjennaSuodattimet.png)

Teksti: "Tyhjennä suodattimet"
Mitä se tekee: Poistaa kaikki aktiiviset sarakesuodattimet ja vertailusuodattimet vasemmasta taulukosta. Tyhjennyksen jälkeen kaikki valitun tason kohteet tulevat jälleen näkyviin (sivutusta noudattaen). Taulukko palautuu sivulle 1, ja kaikki suodattimen merkkipisteet (•) tai vertailumerkit (≠) poistetaan sarakeotsikoista.

### Edellinen rivi -painike

![Edellinen rivi -painike](/img/system_images/btn_prev_row.svg)

Kuvake: Ylöspäin osoittava nuoli (käännetty vasen nuoli)
Mitä se tekee: Valitsee edellisen näkyvän rivin vasemmasta taulukosta ja keskittää kartan automaattisesti kyseiseen kohteeseen mittakaavassa 1:1000. Jos olet ensimmäisellä rivillä, se siirtyy viimeiselle rivillä (kehäkierto). Karttapohja jäädytetään toimenpiteen ajaksi valkoisten välähdysten estämiseksi, ja kohde korostetaan punaisella merkillä (ympyrä pisteille, ääriviiva monikulmioille).

### Seuraava rivi -painike

![Seuraava rivi -painike](/img/system_images/btn_next_row.svg)

Kuvake: Alaspäin osoittava nuoli (käännetty oikea nuoli)
Mitä se tekee: Valitsee seuraavan näkyvän rivin vasemmasta taulukosta ja keskittää kartan automaattisesti kyseiseen kohteeseen mittakaavassa 1:1000. Jos olet viimeisellä rivillä, se pysyy viimeisellä rivillä. Karttapohja jäädytetään toimenpiteen ajaksi, ja kohde korostetaan punaisella merkillä.

### Näytä kartalla -painike

![kuva käyttöliittymästä](/img/naytaKartalla.png)

Teksti: "Näytä kartalla"
Vihjeteksti: Kohdenna karttanäkymä valittuun kohteeseen
Mitä se tekee: Keskittää QGIS-karttapohjan valittuun kohteeseen (joko vasemmasta tai oikeasta taulukosta) mittakaavassa 1:1000. Jos vasemmasta taulukosta ei ole mitään valittuna, se valitsee ensimmäisen näkyvän rivin. Kohde korostetaan punaisella merkillä (ympyrä pisteille, ääriviiva monikulmioille). Tämä ei muuta nykyistä valintaa. Toimii molemmissa taulukoissa: vasemmassa (kohteet) ja oikeassa (lisätyt kohteet).

### Siirrä lisättyihin -painike

![kuva käyttöliittymästä](/img/siirraLisattyihin.png)

Kuvake: Oikea nuoli
Teksti: "→"
Mitä se tekee: Siirtää valitut kohteet vasemmasta taulukosta oikeaan taulukkoon (lisättyjen kohteiden luettelo). Useita kohteita voidaan valita käyttämällä Ctrl+napsautus tai Shift+napsautus. Jokainen siirretty kohde merkitään "raportoiduksi" (lisää pisteen • "Raportissa"-sarakkeeseen vasempaan taulukkoon) ja määritetään aktiiviseen kategoriaan (Rakennus tai Maapohja). Kohteen alkuperäinen taso, kenttäarvot ja metatiedot tallennetaan myöhempää muokkausta ja raportointia varten. Jos taso on nimeltään "Rekisterin_rakennukset_puuttuvat_verotiedosta (prosessoitu)", kohteen status-kenttä päivitetään arvoon 1.

### Siirrä kohteisiin -painike

![Siirrä kohteisiin -painike](/img/system_images/btn_move_left.svg)

Kuvake: Vasen nuoli
Teksti: "←"
Mitä se tekee: Poistaa valitut kohteet oikeasta taulukosta (lisättyjen kohteiden luettelo) ja siirtää ne takaisin tavalliseen kohteiden joukkoon. "Raportoitu"-merkki (•) poistetaan vasemmasta taulukosta, jos mikään muu merkintä ei viittaa kyseiseen kohteeseen. Myös poistettujen kohteiden keltaiset muokkauskorostukset kartalla poistetaan. Voit valita useita rivejä kerralla napsauttamalla mitä tahansa solua kyseisiltä riveiltä. Jos taso on "Rekisterin_rakennukset_puuttuvat_verotiedosta (prosessoitu)", kohteen status-kenttä päivitetään arvoon 0.

### Rakennus-kategoriapainike

![kuva käyttöliittymästä](/img/rakennusKategoria.png)

Teksti: "Rakennus"
Mitä se tekee: Toimii vaihtopainikkeena (kuin radiopainike), joka vaihtaa oikean taulukon näyttämään vain rakennuksiin liittyviä kohteita. Kun aktiivinen (vihreä), oikea taulukko näyttää rakennuksille ominaisia sarakkeita (Pysyvä rakennustunnus, Kiinteistötunnus, Rakennuksen numero, Taso, Kommentti). Vain yksi kategoriapainike (Rakennus tai Maapohja) voi olla aktiivinen kerrallaan. Painike toimii eksklusiivisesti Maapohja-painikkeen kanssa samalla tavalla kuin "Valitse kartalta" -painike (vihreä korostus aktiivisena).

### Maapohja-kategoriapainike

![kuva käyttöliittymästä](/img/maapohjaKategoria.png)

Teksti: "Maapohja"
Mitä se tekee: Toimii vaihtopainikkeena, joka vaihtaa oikean taulukon näyttämään vain maa-alueisiin liittyviä kohteita (palstat, määrä-ala). Kun aktiivinen (vihreä), oikea taulukko näyttää maa-alueille ominaisia sarakkeita (Kiinteistötunnus, Maapohjan Numero, Taso, Kommentti). Vain yksi kategoriapainike voi olla aktiivinen kerrallaan. Rakennus on oletuskategoria käynnistyksen jälkeen.

### Näytä muokkauskorostukset -valintaruutu

![kuva käyttöliittymästä](/img/naytaKorostukset.png)

Teksti: "Näytä/piilota muokattujen kohteiden korostukset kartalla"
Mitä se tekee: Vaihtaa kartalla kaikkien muokattujen kohteiden keltaisten korostusmerkkien näkyvyyttä oikeassa taulukossa. Kun valittuna, muokatut kohteet (joilla on muokattuja verotietokenttiä, ei pelkästään kommentteja) näytetään keltaisilla X-merkeillä (pisteille) tai keltaisilla ääriviivoilla (monikulmioille). Kun valitsematon, kaikki muokkauskorostukset piilotetaan. Tämä auttaa visualisoimaan, mitä kohteita on muokattu. Korostukset päivittyvät automaattisesti kun muokkaat kohteita tai lataat istunnon.

### Prosessointiasetukset-painike

![kuva käyttöliittymästä](/img/tiedonProsessointi.png)

Kuvake: Hammasrataskuvake
Vihjeteksti: Avaa Prosessointi-laajennuksen valintaikkunan
Mitä se tekee: Avaa erillisen valintaikkunan Prosessointi-laajennuksesta. Tämä mahdollistaa datan käsittely- ja muunnostyökalujen käytön verotutkintaprosessin rinnalla. Tämä on integrointipiste toisen laajennuksen kanssa QGIS-ympäristössäsi. Valintaikkuna aukeaa erilliseksi ikkunaksi, eikä se vaikuta nykyiseen sessioon.

### Luo tiedosto -painike

![kuva käyttöliittymästä](/img/luoTiedosto.png)

Teksti: "Luo tiedosto"
Mitä se tekee: Avaa raportin asetusten valintaikkunan, jossa voit:
- Syöttää kunnan yhteystiedot (kaupunki, yhteyshenkilö, tehtävänimike, puhelin, sähköposti)
- Valita, mitkä raporttityypit luodaan (6 vaihtoehtoa: puuttuvat / rekisterikorjaus kunnan rekisteriin / rekisterikorjaus verottajan rekisteriin — erikseen rakennuksille ja maapohjalle)
- Valita tulostekansio selaus-painikkeen avulla

Ohjelma jakaa lisätyt kohteet kategorian ja muokkaustietojen perusteella eri CSV-tiedostoihin. Tiedostonimeen lisätään automaattisesti luontipäivämäärä, esim. `Rakennus_puuttuvat_2026-05-05.csv`. Katso tarkempi selitys [Raportin asetukset -ikkunasta](#raportin-asetukset--ikkuna). Jos tiedosto on jo olemassa kohdekansiossa, ohjelma kysyy haluatko korvata sen vai tallentaa uuden tiedoston juoksevalla numerolla (esim. `Rakennus_puuttuvat_2026-05-05 (1).csv`).

### Sivutusohjaimet
#### Sivukoko-valikko

![kuva käyttöliittymästä](/img/sivukoko1.png)
![kuva käyttöliittymästä](/img/sivukoko2.png)
 
Vaihtoehdot: 25, 50, 100, 250, 500, 1000, "Kaikki"

Mitä se tekee: Ohjaa, kuinka monta kohdetta näytetään sivua kohden vasemmassa taulukossa. Oletusarvo on 100. "Kaikki"-vaihtoehdon valitseminen poistaa sivutuksen käytöstä ja näyttää kaikki suodatetut kohteet kerralla (voi olla hidas suurilla aineistoilla). Sivukoon muuttaminen palauttaa sivulle 1. Tämä auttaa hallitsemaan suorituskykyä suurten aineistojen kanssa työskennellessä. Suodattimet ja lajittelu säilyvät sivukokoa vaihdettaessa.

#### Sivuvalintapainikkeet

![kuva käyttöliittymästä](/img/sivuvalinta.png)

Toiminto: Siirry kohdetaulukon edelliselle (←) tai seuraavalle (→) sivulle. Painike on pois käytöstä (harmaa) kun valittuna on taulukon äärimmäinen sivu. Sivuosoitinteksti (Sivu X/Y) kuvaa valitun sivun numeroa ja päivittyy sivua vaihtaessa.

## Valikkopalkin valinnat

![Valikkopalkin rakenne](/img/system_images/menubar.svg)

### Tiedosto-pudotusvalikko

![kuva käyttöliittymästä](/img/tiedosto_lataa.png)

| Painike | Toiminto |
|---------|----------|
| Lataa   | Avaa tiedostovalintaikkunan aiemmin tallennetun istunnon lataamiseksi (.json-tiedosto). Kysyy haluatko korvata nykyiset lisätyt kohteet vai liittää ladatut kohteet olemassa oleviin. Ohjelma yrittää sovittaa ladatut kohteet nykyisen projektin tasoihin geometrian ja avainkenttien avulla (1 metrin säde). Palauttaa kaiken muokkaushistorian ja korostukset. Jos ladatun istunnon projekti ei täsmää nykyiseen projektiin, ohjelma varoittaa sinua. Jos kohteen FID ja taso on tallennettu, ohjelma käyttää niitä suoraan; muuten etsitään vastaavuutta avaintietojen perusteella.
| Tallenna| Tallentaa nykyisen istunnon aiemmin valittuun tiedostopolkuun. Jos polkua ei ole vielä olemassa (ensimmäinen tallennus), se käyttää "Tallenna nimellä" -toimintoa ja pyytää valitsemaan sijainnin. Kaikki lisätyt kohteet, niiden muokkaukset, kommentit, kategoriat ja geometriatiedot tallennetaan JSON-muotoon. Istunto sisältää myös projektin metatiedot (polku, otsikko, muokkausaika) tunnistamista varten. Tämä painike on harmaa kunnes olet käyttänyt "Tallenna nimellä" tai "Lataa" vähintään kerran.
| Tallenna nimellä | Avaa tiedostovalintaikkunan uuden sijainnin ja tiedostonimen valitsemiseksi nykyisen istunnon tallentamiseen. Oletustiedostonimi on "verosession.json" projektin kansiossa tai kotikansiossasi. Tallentamisen jälkeen tästä polusta tulee "Tallenna"-vaihtoehdon oletusarvo nopeatallennusta varten. Istunto sisältää: <ul><li>Projektin metatiedot (polku, otsikko, viimeisin muokkaus)</li><li>Kaikki lisätyt kohteet kategorioittain</li><li>Alkuperäiset arvot ja muokatut arvot jokaiselle kentälle</li><li>Geometriatiedot (WKT, tyyppi, CRS) spatiaalista sovitusta varten</li><li>Kommentit ja tasotiedot</li><li>Versio 2 -skeema merkinnöillä (__vero, __kunta, __added)</li></ul>
| Luo tiedosto | Sama toiminnallisuus kuin painike [Luo tiedosto](#luo-tiedosto--painike) - avaa raportin luomisen valintaikkunan. Tämä on pikanäppäin valikkopalkista raportointiin.


### Vertailu-pudotusvalikko

![kuva käyttöliittymästä](/img/vertailu.png)

| Painike | Toiminto |
|---------|----------|
| Vuosivertailu | Avaa itsenäisen [kolmivälilehtisen vertailun valintaikkunan](03_vuosivertailu.md). |
| Vertaa | Avaa valintaikkunan, jossa voit valita kaksi saraketta vertailtavaksi. Ohjelma suodattaa pois (piilottaa) rivit, joilla kahden valitun sarakkeen arvot ovat yhtä suuret. Numeerisille sarakkeille voit määrittää toleranssiarvon (esim. 2 tai 0.5), jolloin arvot, jotka eroavat alle toleranssin verran, käsitellään yhtäläisinä ja piilotetaan. Hyödyllinen veroaineiston ja kuntien tietokannan välisten erojen löytämiseen. Vertailuasetukset tallennetaan ja ne voidaan palauttaa käyttämällä valintaikkunan "Palauta"-painiketta. |

### Tyylit-pudotusvalikko

Tyylivalikko listaa esimääritellyt kuvaustyylit prosessoidulle aineistolle.  
Valitsemalla tasoa vastaavan kuvaustyylin valikon listauksesta ohjelma muuttaa tason kuvauksen vastaamaan valittua tyyliä.

:::tip Vinkki
Tyylit helpottavat tiedon tarkastelua. Erilaisten tyylien avulla voit ohjata tarkastelua oleellisiin kohteisiin, tai havainnollistettua alueellisia eroja aineistossa.
:::

### Asetukset-pudotusvalikko

![kuva käyttöliittymästä](/img/asetukset.png)

Mitä se tekee: Avaa monisivuisen [asetusten valintaikkunan](./02_prosessointiasetukset.md). Asetukset on jaettu seuraaviin kategorioihin:
- **Yleiset**: Ikkunakoon muisti (palauta edellisen istunnon koko)
- **Tietokanta**: Kenttien kartoitus kiinteistötunnukselle, PRT:lle, rakennusnumerolle, määrä-alan kentille. Täällä määrität mitkä tietokantakentät vastaavat mitäkin avaintietoja.
- **Pudotusvalikot** täytetään automaattisesti projektin tasojen kentillä.
- **Taulukko**: Automaattinen sarakkeiden koon muutos, lisättyjen kohteiden näyttötila (verokentät/tietokantakentät/molemmat)
- **Raportit**: Oletustulostekansio raporteille
- **Lisäasetukset**: Varattu tuleville asetuksille (tyhjä tällä hetkellä)

Muutokset otetaan käyttöön välittömästi kun napsautat "Käytä" tai "OK". Asetukset säilyvät istuntojen välillä. "Käytä"-painike tallentaa muutokset mutta pitää ikkunan auki; "OK" tallentaa ja sulkee; "Peruuta" sulkee tallentamatta.

## Taulukkotoiminnot

### Kohdetaulukon sarakeotsikot

#### Hiiren vasen painike

Napautus järjestää rivit sarakkeen arvojen perusteella. Uusi napautus muuttaa järjestyksen arvojen mukaan laskevaksi.

#### Hiiren oikea painike

Napautus avaa suodatinvalintaikkunan kyseiselle sarakkeelle vaihtoehdoilla:

Luettelotila (kaikille sarakkeille):
- Näyttää listan yksilöllisistä arvoista sarakkeessa
- Hakukenttä suodattaa listaa reaaliajassa
- "Valitse kaikki" / "Tyhjennä valinnat" -painikkeet
- Suurille sarakkeille (>50 arvoa): lista alkaa tyhjänä, täyttyy haun mukaan (≤50 tulosta kerralla)
- Voit valita useita arvoja ja vain ne rivit, joissa on valitut arvot, näytetään
- Aikaisemmat valinnat muistetaan ja esitäytetään

Numeerinen alue (numeerisille sarakkeille):
- Min/Max -kentät alarajan ja ylärajan asettamiseen
- Sisältävä alue (inclusive): rivit joissa arvo on välillä [min, max]
- Tyhjä kenttä = ei rajoitusta kyseiseltä puolelta
- Käsittelee eurooppalaisia numeroformaatteja (pilkku desimaalierottimena)

Palauta-painike: Tyhjentää suodattimen tälle sarakkeelle

Suodatetut sarakkeet näyttävät pisteen (•) otsikossaan. Suodattimet toimivat yhdessä: kaikki aktiiviset suodattimet on täytettävä.

### Kohdetaulukon rivit

Hiiren vasemmalla-, oikealla- ja keskipainikkeella on kaikilla samat toiminnot.

Napautus korostaa osoitetun rivin valituksi. Valitun rivin voi lisätä raporttiin painamalla [Siirrä lisättyihin](#siirrä-lisättyihin--painike) -painikkeella.

Kaksoisnapautus avaa rivin kohteen tiedot katseltavaksi uuteen ikkunaan.

### Valintataulukon sarakeotsikot

#### Hiiren vasen painike

Napautus korostaa sarakkeen arvot taulukossa.

#### Hiiren oikea painike

Toimii samoin kuin [Kohdetaulukon sarakeotsikot](#kohdetaulukon-sarakeotsikot) — avaa saman suodatinvalintaikkunan listaus- ja numeerinen alue -toiminnoilla.

### Valintataulukon rivit

#### Hiiren vasen painike

Napautus korostaa yksittäisen taulukon solun valituksi esimerkiksi arvojen kopiointia varten.

Kaksoisnapautus avaa kohteen tiedot erilliseen ikkunaan muokkausta varten.

#### Hiiren oikea painike

Mitä se tekee: Avaa valikon kontekstivalikon vaihtoehdolla:
- Tallenna: Pikatallenna nykyiseen istuntotiedostoon (harmaa jos ei polkua vielä valittu)
- Tallenna nimellä: Valitse uusi tiedosto ja tallenna
- Lataa: Lataa aiempi istunto (kysyy korvataanko vai liitetäänkö)

Tämä tarjoaa nopean pääsyn istuntojen hallintaan ilman valikkopalkkia. Sama toiminnallisuus kuin valikkopalkissa, mutta kätevämpää kun työskentelet oikean taulukon kanssa.

## Alaikkunoiden painikkeet

### Sarakeotsikon suodatinvalintaikkunan painikkeet

Avautuu kun: Napsautat hiiren oikealla [kohdetaulukon otsikoita](#kohdetaulukon-sarakeotsikot) tai [valintataulukon otsikoita](#valintataulukon-sarakeotsikot)

**Hakukenttä:**  
- Suodattaa listan arvoja reaaliajassa  
- Piilottaa ei-täsmäävät arvot (pienille listoille)  
- Näyttää vain täsmäävät arvot (≤50, suurille listoille)

**Arvolista:**
- Näyttää yksilölliset arvot sarakkeessa
- Useita arvoja voi valita (ExtendedSelection)
- Suuret listat (>50): alkaa tyhjänä, täyttyy haun mukaan
- Pienet listat (≤50): esitäytetty kaikilla arvoilla
- Esitäytetty edellisten valintojen mukaan

**Numeerinen alue -rivi (vain numeeriset sarakkeet):**
- Min-kenttä: "min" placeholder
- Max-kenttä: "max" placeholder
- Väliteksti: "Väli:" ja "–" kenttien välissä
- Piilotettu oletuksena, näytetään kun sarake on numeerinen
- Esitäytetty jos aikaisempi aluesuodatin aktiivinen

**Valitse kaikki -painike:**

- Valitsee kaikki näkyvät arvot listasta
- Toimii haun jälkeen - valitsee vain hakutulokset

**Tyhjennä valinnat -painike:**
- Poistaa kaikki valinnat listasta
- Nollaa valintasi

**OK-painike:**
- Käyttää suodatinta:
  - Numeerinen alue (jos annettu) ottaa etusijan
  - Muuten käyttää lista-arvoja
  - Tyhjä valinta = tyhjentää suodattimen
- Sulkee ikkunan
- Päivittää vasemman taulukon välittömästi
- Lisää •-merkin sarakeotsikoihin

**Peruuta-painike:**
- Sulkee ikkunan tallentamatta muutoksia
- Ei muuta aktiivista suodatinta


**Palauta-painike:**
- Tyhjentää suodattimen tälle sarakkeelle
- Sulkee ikkunan
- Poistaa •-merkin sarakeotsikoista

### Muokkausvalintaikkunan painikkeet

**Avautuu kun:** Kaksoisnapsautat riviä kohdetaulukossa

**Kentät (kaikki muokattavissa):**
- Vasemman palstan kentät: tietokanta-arvot (`__kunta`-kentät)
- Oikean palstan kentät: verotiedot (`__vero`- ja `__added`-kentät)
- Aiemmin muokatut kentät näkyvät keltaisella taustalla
- Muutoksia seurataan automaattisesti

**Kommenttikenttä:** Avoin tekstikenttä vapaiden muistiinpanojen tallettamiseen

**OK:** Tallentaa muutokset, päivittää keltaiset korostukset kartalla ja sulkee ikkunan.

**Peruuta:** Hylkää kaikki muutokset ja sulkee ikkunan.

### Vain luku -näkymä

**Avautuu kun:** Shift+kaksoisnapsautat riviä oikeassa taulukossa

![Vain luku -näkymä](/img/system_images/dialog_vain_luku.svg)

#### Data-välilehti

- Yläreunassa sininen taustatieto: "Tasolta: [tason nimi]"
- Kaksi palstaa:
  - Vasemmalla: tietokanta-arvot (`__kunta`-kentät)
  - Oikealla: verotiedot (`__vero`/`__added`-kentät)
- Kaikki kentät vain luku
- Värjäys:
  - Keltainen: kenttä muokattu istunnossa
  - Oranssi: kenttä ei täsmää kandidaatin kanssa (jos validoitu)
  - Valkoinen: muut kentät
- Tunnistavat avaimet alareunassa (PRT, Kiinteistötunnus, Rakennuksen numero jne.) keltaisella taustalla
- Kommenttikenttä alareunassa (vain luku)

#### Candidate Data -välilehti

- Näkyy vain jos validointi on suoritettu ja kandidaatti löytynyt
- Yläreunassa sininen taustatieto: "Löydetty tasolta: [tason nimi]"
- Sama rakenne kuin Data-välilehdessä, mutta näyttää projektin nykyiset tiedot
- Värjäys: Valkoinen = täsmää istunnon arvoon, Oranssi = ei täsmää
- Hyödyllinen vertailuun: näet mitä projektissa on vs. mitä istunnossa on

**Sulku-painike:** Sulkee ikkunan tallentamatta muutoksia.

### Vertaa sarakkeita -ikkuna

**Avautuu kun:** Napsautat valikkopalkista Vertailu > Vertaa

![Vertaa sarakkeita -ikkuna](/img/system_images/dialog_vertaa_sarakkeita.svg)

**Sarake A / Sarake B:** Valitse kaksi saraketta vertailuun. Sarakkeet eivät voi olla samat. Esitäytetty viimeisimmästä vertailusta.

**Toleranssi:** Numeerinen kynnysarvo – rivit joissa sarakkeiden ero ≤ toleranssi piilotetaan. Toimii vain numeerisilla sarakkeilla. Hyväksyy pilkun desimaalierottimena.

**OK:** Käyttää vertailusuodatinta, lisää ≠-merkin sarakeotsikoihin ja tallentaa asetukset.

**Peruuta:** Sulkee ikkunan tallentamatta muutoksia.

**Palauta:** Tyhjentää vertailusuodattimen, poistaa ≠-merkit ja nollaa valinnat oletuksiin.



### Raportin asetukset -ikkuna

**Avautuu kun:** Napsautat [Luo tiedosto](#luo-tiedosto--painike) -painiketta tai valikkopalkista Tiedosto > Luo tiedosto

![Raportin asetukset -ikkuna](/img/system_images/dialog_raportin_asetukset.svg)

**Yhteystietokentät:** Kaupunki, Yhteyshenkilö, Tehtävänimike, Puhelin, Sähköposti.

**Raporttityypit** (vähintään yksi valittava):

**Rakennukset**
- Rakennukset – puuttuvat (ilmoitetaan verottajalle): Rakennukset, jotka puuttuvat verottajan rekisteristä. Tiedosto: `Rakennus_puuttuvat_VVVV-KK-PP.csv`.
- Rakennukset – Rekisterikorjaus (Verottajan rekisteri): Rakennukset, joiden verottajan puolen tietoja on muokattu. Tiedosto: `Rakennus_Rekisterikorjaus_Vero_VVVV-KK-PP.csv`.
- Rakennukset – Rekisterikorjaus (Kunnan rekisteri): Rakennukset, joiden kunnan puolen tietoja on muokattu. Tiedosto: `Rakennus_Rekisterikorjaus_Kunta_VVVV-KK-PP.csv`.

**Maapohja**
- Maapohja – puuttuvat (ilmoitetaan verottajalle): Kiinteistöt, jotka puuttuvat verottajan rekisteristä. Tiedosto: `Maapohja_puuttuvat_VVVV-KK-PP.csv`.
- Maapohja – Rekisterikorjaus (Verottajan rekisteri): Kiinteistöt, joiden verottajan puolen tietoja on muokattu. Tiedosto: `Maapohja_Rekisterikorjaus_Vero_VVVV-KK-PP.csv`.
- Maapohja – Rekisterikorjaus (Kunnan rekisteri): Kiinteistöt, joiden kunnan puolen tietoja on muokattu. Tiedosto: `Maapohja_Rekisterikorjaus_Kunta_VVVV-KK-PP.csv`.

*(VVVV-KK-PP = luontipäivämäärä, esim. 2026-05-05)*

**Puuttuvat-raportit** (lähetetään verottajalle) sisältävät: Kaupunki, Yhteyshenkilö, Tehtävänimike, Puhelin, Sähköposti, Kiinteistötunnus.

**Rekisterikorjaus-raportit** (sisäinen käyttö) eivät sisällä yhteystietoja. Kukin muutos on omalla rivillään, jotta tiedostoa on helppo suodattaa ja lajitella. Rakennus-rekisterikorjausraportit sisältävät: Kiinteistötunnus, PRT, Rakennuksen numero, Kenttä, Alkuperäinen arvo, Uusi arvo, Kommentti. Maapohja-rekisterikorjausraportit sisältävät: Kiinteistötunnus, Kenttä, Alkuperäinen arvo, Uusi arvo, Kommentti. Kenttien nimet näkyvät ilman teknisiä päätteitä. Kukin raportti näyttää vain sen puolen muutokset (kunta tai vero), jota raportti koskee.

**Miten kohde päätyy kuhunkin raporttiin:**

| Tilanne | Raportti |
|---------|----------|
| Kohde on tasolta `Rekisterin_rakennukset_puuttuvat_verotiedosta (prosessoitu)` | Rakennukset – puuttuvat |
| Kohde on tasolta `Veroaineiston_rakennukset_puuttuvat_rekisteristä (prosessoitu)` | Rakennukset – Rekisterikorjaus (Kunnan rekisteri) |
| Kohde on tasolta `Rekisterin_Kiinteistöt_puuttuvat_verotiedosta (prosessoitu)` | Maapohja – puuttuvat |
| Kohde muulta tasolta, ei muokkauksia | Puuttuvat (kategorian mukaan) |
| Kohde muulta tasolta, `__kunta`-kenttiä muokattu | Rekisterikorjaus (Kunnan rekisteri) |
| Kohde muulta tasolta, `__vero`-kenttiä muokattu | Rekisterikorjaus (Verottajan rekisteri) |
| Kohde muulta tasolta, molempia muokattu | Sekä Kunnan että Verottajan rekisteri |

Jos kohde on tunnetulta tasolta ja siihen on tehty muokkauksia, se lisätään sekä puuttuvat-raporttiin että asianomaiseen rekisterikorjausraporttiin.

**Tulostekansio:** Valitse kohdekansio Selaa…-painikkeella tai kirjoita polku suoraan.

**OK:** Validoi valinnat ja luo raportit. Jos tiedosto on jo olemassa kohdekansiossa, ohjelma kysyy haluatko korvata sen vai tallentaa juoksevalla numerolla (esim. `Rakennus_puuttuvat_2026-05-05 (1).csv`). Näyttää lopuksi yhteenvedon luoduista tiedostoista.

**Peruuta:** Sulkee ikkunan luomatta raportteja.

### Vuosivertailu-ikkuna

**Avautuu kun:** Napsautat valikkopalkista Vertailu > Vuosivertailu

![Vuosivertailu-ikkuna](/img/system_images/dialog_vuosivertailu.svg)

**Lataa sessio…:** Avaa tiedostovalintaikkunan `.json`-istuntotiedoston lataamiseksi. Päivittää kaikki välilehdet, muttei vaikuta pääikkunan dataan.

**Sulku:** Sulkee ikkunan tallentamatta muutoksia.

#### Korjaus tarkistus -välilehti

- **Vaihda kategoria:** Vaihtaa näkymän Rakennus ↔ Maapohja välillä (kehäkierto).
- **Tarkista tiedot:** Suorittaa geometriapohjaisen validoinnin (1 m säde). Värjää rivit: vihreä = OK, punainen = Check. Näyttää yhteenvedon ponnahdusikkunassa.
- **Taulukko:** Listaa ladatut kohteet nykyiselle kategorialle. Kaksoisnapsautus avaa [vain luku -näkymän](#vain-luku--näkymä).

#### Tilastot & kaaviot -välilehti

Näyttää yhteenvetotilastot sekä Rakennuksille että Maapohjalle:
- OK ja Check kohteiden määrät
- Kiinteistövero-lisä (siirrot) ja -erot (päivitetyt) euroina

#### Info-välilehti

Näyttää ladatun istunnon ja nykyisen projektin metatiedot (otsikko, polku, muokkausaika), kohteiden täsmäystilastoinnin sekä selityksen kaikille mahdollisille Huomio-viesteille.
