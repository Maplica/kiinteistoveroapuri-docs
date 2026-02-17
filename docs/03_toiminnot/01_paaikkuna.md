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

![kuva käyttöliittymästä](/img/edellinenSeuraavaRivi.png)

Kuvake: Ylöspäin osoittava nuoli (käännetty vasen nuoli)
Mitä se tekee: Valitsee edellisen näkyvän rivin vasemmasta taulukosta ja keskittää kartan automaattisesti kyseiseen kohteeseen mittakaavassa 1:1000. Jos olet ensimmäisellä rivillä, se siirtyy viimeiselle rivillä (kehäkierto). Karttapohja jäädytetään toimenpiteen ajaksi valkoisten välähdysten estämiseksi, ja kohde korostetaan punaisella merkillä (ympyrä pisteille, ääriviiva monikulmioille).

### Seuraava rivi -painike

![kuva käyttöliittymästä](/img/edellinenSeuraavaRivi.png)

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

![kuva käyttöliittymästä](/img/siirraLisattyihin.png)

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
Syöttää kunnan yhteystiedot (kaupunki, yhteyshenkilö, tehtävänimike, puhelin, sähköposti)
Valita, mitkä raporttityypit luodaan (4 vaihtoehtoa: Rakennukset - uudet/muokatut, Maapohja - uudet/muokatut)
Valita tulostekansio selaus-painikkeen avulla
Luoda CSV- tai Excel-raportteja korostuksineen muokatuille kentille
Ohjelma jakaa lisätyt kohteesi kategorian ja muokkaustilan mukaan ja luo sitten erilliset tiedostot kullekin valitulle raporttityypille. "Uudet" raportit sisältävät kohteet, joilla ei ole muokattuja kenttiä (vain kommentti sallittu). "Muokatut" raportit ovat Excel-tiedostoja, joissa muutetut solut korostetaan keltaisella. Jos tiedosto on jo olemassa, ohjelma kysyy haluatko korvata vai lisätä (CSV:lle) vai peruuttaa.

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

### Asetukset-pudotusvalikko

![kuva käyttöliittymästä](/img/asetukset.png)

Kuvake:
 Vihjeteksti: "Avaa asetukset"
Mitä se tekee: Avaa monisivuisen [asetusten valintaikkunan](./02_prosessointiasetukset.md) kategorioilla:
Yleiset: Ikkunakoon muisti (palauta edellisen istunnon koko)
Tietokanta: Kenttien kartoitus kiinteistötunnukselle, PRT:lle, rakennusnumerolle, määrä-alan kentille. Täällä määrität mitkä tietokantakentät vastaavat mitäkin avaintietoja. Pudotusvalikot täytetään automaattisesti projektin tasojen kentillä.
Taulukko: Automaattinen sarakkeiden koon muutos, lisättyjen kohteiden näyttötila (verokentät/tietokantakentät/molemmat)
Raportit: Oletustulostekansio raporteille
Lisäasetukset: Varattu tuleville asetuksille (tyhjä tällä hetkellä)
Muutokset otetaan käyttöön välittömästi kun napsautat "Käytä" tai "OK". Asetukset säilyvät istuntojen välillä. "Käytä"-painike tallentaa muutokset mutta pitää ikkunan auki; "OK" tallentaa ja sulkee; "Peruuta" sulkee tallentamatta.

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
| Vuosivertailu | Avaa itsenäisen [kolmivälilehtisen vertailun valintaikkunan](#vuosivertailu-ikkuna). |
| Vertaa | Avaa valintaikkunan, jossa voit valita kaksi saraketta vertailtavaksi. Ohjelma suodattaa pois (piilottaa) rivit, joilla kahden valitun sarakkeen arvot ovat yhtä suuret. Numeerisille sarakkeille voit määrittää toleranssiarvon (esim. 2 tai 0.5), jolloin arvot, jotka eroavat alle toleranssin verran, käsitellään yhtäläisinä ja piilotetaan. Hyödyllinen veroaineiston ja kuntien tietokannan välisten erojen löytämiseen. Vertailuasetukset tallennetaan ja ne voidaan palauttaa käyttämällä valintaikkunan "Palauta"-painiketta. |

#### Vuosivertailu-ikkuna

Korjaus tarkistus -välilehti:
- Lataa istuntotiedoston "Lataa sessio…" -painikkeella
- Näyttää ladatut kohteet taulukossa nykyisen kategorian mukaan
- "Vaihda kategoria" -painike vaihtaa Rakennus/Maapohja välillä
- "Tarkista tiedot" -painike suorittaa geometriapohjaisen validoinnin (1 m säde)
- Validointi käyttää ryhmärajoitteita: Rakennus → Rakennukset/Rakennuksen Osat, Maapohja → Määrä-alat
- Näyttää kunkin kohteen tilan (OK/Check), nykyisen tason ja huomiot
- Rivit värjätään: vihreä (OK), punainen (Check), valkoinen (ei validoitu)
- Kaksoisnapsautus avaa vain luku -näkymän kaikista tiedoista + Candidate Data -välilehden

Tilastot & kaaviot -välilehti:
- Näyttää OK/Check-määrät kategoriaa kohden (Rakennus, Maapohja)
- Näyttää Kiinteistövero-summia:
  - Kiinteistövero lisä: summa siirroista puuttuvat→yhdistetty
  - Kiinteistövero erot: summa päivitetyistä arvoista joissa ero
- Sisältää selityksen laskentalogiikasta

Info-välilehti:
- Näyttää ladatun istunnon metatiedot (otsikko, polku, muokkausaika)
- Näyttää nykyisen projektin metatiedot
- Näyttää yhteenvedon (yhteensä kohteet, löydetty, ei löydetty)
- Sisältää selitykset kaikista Huomio-viesteistä

Tämä valintaikkuna toimii itsenäisesti eikä vaikuta pääikkunan oikeaan taulukkoon. Sitä käytetään aiemmin tallennettujen istuntojen tarkasteluun ja validointiin päivitettyä projektiaineistoa vastaan.

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
- Lisää •-merkin sarakeotikkoon

**Peruuta-painike:**
- Sulkee ikkunan tallentamatta muutoksia
- Ei muuta aktiivista suodatinta


**Palauta-painike:**
- Tyhjentää suodattimen tälle sarakkeelle
- Sulkee ikkunan
- Poistaa •-merkin sarakeotikosta

### Muokkausvalintaikkunan painikkeet
Avautuu kun: Kaksoisnapsautat riviä kohdetaulukossa

Kentät (kaikki muokattavissa):
- Vasemman palstan kentät: Database values (__kunta-kentät)
- Oikean palstan kentät: Tax data (__vero ja __added-kentät)
- Jokainen kenttä on QLineEdit
- Aiemmin muokatut kentät keltaisella taustalla
- Teksti muuttuu samalla kun kirjoitat
- Muutokset seurataan automaattisesti

Kommenttikenttä:
- Avoin tekstikenttä vapaiden muistiinpanojen tallettamiseen

OK-painike:
- Tallentaa kaikki muutokset
- Päivittää tax_data vain muuttuneille kentille
- Päivittää kommentin
- Lisää/päivittää keltaiset korostukset kartalla
- Päivittää oikean taulukon näkymän
- Sulkee valintaikkunan

Peruuta-painike:
- Hylkää kaikki muutokset
- Ei tallenna mitään
- Sulkee valintaikkunan

34. Vain luku -näkymän painikkeet (ReadOnlyFeatureViewDialog)
Avautuu kun: Shift+kaksoisnapsautat riviä oikeassa taulukossa

Välilehdet:
Data-välilehti:
Näyttää taustietorivi yläreunassa: "Tasolta: [tason nimi]" sinisellä taustalla
Kaksi palstaa kuten muokkausikkunassa:
Vasemmalla: Database values (__kunta)
Oikealla: Tax data (__vero/__added)
Kaikki kentät vain luku (QLineEdit read-only)
Värjäys:
Keltainen: kenttä muokattu istunnossa
Oranssi: kenttä ei täsmää kandidaatin kanssa (jos validoitu)
Valkoinen: muut kentät
Tunnistavat avaimet -osio alareunassa:
Näyttää PRT, Kiinteistötunnus, Rakennuksen numero jne.
Keltaisella taustalla
Näyttää alkuperäisen arvon (muokatun jos muokattu)
Kommentti-osio alareunassa (vain luku, ~2 riviä)
Candidate Data -välilehti:
Näkyy vain jos validointi on suoritettu ja kandidaatti löytynyt
Taustietorivi: "Löydetty tasolta: [tason nimi]" sinisellä taustalla
Sama kaksi palstaa kuten Data-välilehdessä
Näyttää nykyisen tason tiedot (ei istunnon tietoja)
Värjäys:
Valkoinen: kenttä täsmää istunnon arvoon
Oranssi: kenttä ei täsmää istunnon arvoon
Sisältää myös tagaamattomat kentät (ilman __vero/__kunta)
Erotinviiva tagaamattomien ja __kunta-kenttien välillä vasemmassa palstassa
Tunnistavat avaimet -osio alareunassa kandidaatin avaimilla
Hyödyllinen vertailuun: näet mitä projektissa on vs. mitä istunnossa on
Sulku-painike:
Sulkee valintaikkunan
Ei tallenna mitään (kaikki vain luku)

35. Vertaa sarakkeita -valintaikkunan painikkeet (CompareColumnsDialog)
Avautuu kun: Napsautat valikkopalkista Vertailu > Vertaa

Sarake A -pudotusvalikko:
Listaa kaikki sarakkeet vasemmasta taulukosta (paitsi "Raportissa")
Valitse ensimmäinen sarake vertailuun
Esitäytetty viimeisimmästä vertailusta jos saatavilla
Sarake B -pudotusvalikko:
Sama listaus kuin Sarake A
Valitse toinen sarake vertailuun
Esitäytetty viimeisimmästä vertailusta jos saatavilla
Ei saa olla sama kuin Sarake A
Toleranssi-kenttä:
QLineEdit numeeriselle toleranssille
Placeholder: "esim. 2 tai 0.5"
Käytetään vain kun molemmat sarakkeet ovat numeerisia
Rivit, joissa erotus ≤ toleranssi, piilotetaan
Esitäytetty viimeisimmästä vertailusta
Hyväksyy pilkun desimaalierottimena
OK-painike:
Käyttää vertailusuodatinta
Piilottaa rivit joissa sarakkeet ovat yhtä suuret (toleranssin sisällä)
Lisää ≠-merkin molempien sarakkeiden otsikoihin
Tallentaa asetukset seuraavaa kertaa varten
Sulkee valintaikkunan
Päivittää vasemman taulukon välittömästi
Peruuta-painike:
Sulkee valintaikkunan tallentamatta muutoksia
Ei muuta aktiivista vertailua
Palauta-painike:
Tyhjentää vertailusuodattimen
Poistaa ≠-merkit sarakeotsikoista
Nollaa valinnat oletusarvoihin (sarake 0, 0, ei toleranssia)
Päivittää vasemman taulukon
Sulkee valintaikkunan



37. Raportin asetusvalintaikkunan painikkeet (ReportOptionsDialog)

Avautuu kun: Napsautat painiketta #15 tai valikkopalkista Tiedosto > Luo tiedosto
Yhteystietokentät:
Kaupunki: Tekstikenttä kunnan nimelle, placeholder "Kaupunki / Kunta"
Yhteyshenkilö: Tekstikenttä nimelle, placeholder "Yhteyshenkilö"
Tehtävänimike: Tekstikenttä nimikkeelle, placeholder "Tehtävänimike"
Puhelin: Tekstikenttä puhelinnumerolle, placeholder "Puhelin"
Sähköposti: Tekstikenttä sähköpostille, placeholder "Sähköposti"
Raporttityyppien valintaruudut:
"Valitse raportit (voit valita useita)" -ryhmälaatikko
4 valintaruutua:
Rakennukset – uudet (ei muokattuja kenttiä): CSV-raportti ilman muokattuja kenttiä
Rakennukset – muokatut (korostus): Excel-raportti keltaisilla korostuksilla
Maapohja – uudet (ei muokattuja kenttiä): CSV-raportti ilman muokattuja kenttiä
Maapohja – muokatut (korostus): Excel-raportti keltaisilla korostuksilla
Voit valita useita raportteja kerralla
Tulostekansio:
Tekstikenttä kansion polulle, placeholder "Tulostekansio"
Selaa…-painike: Avaa kansion valintaikkunan
Valitse mihin raportit tallennetaan
Esitäytetty asetuksista jos määritelty
OK-painike:
Validoi että:
Vähintään yksi raporttityyppi valittu
Tulostekansio määritelty
Luo valitut raportit
Kysyy ylikirjoitusta jos tiedosto on olemassa:
Korvaa: Ylikirjoittaa vanhan tiedoston
Lisää: Lisää loppuun (vain CSV)
Peruuta: Ohittaa tämän tiedoston
Näyttää yhteenvedon luoduista/virheellisistä raporteista
Muistutus lähettää raportit Ilmoitin-palvelussa
Peruuta-painike:
Sulkee valintaikkunan luomatta raportteja
Ei tallenna mitään

38. Vertailutulokset-valintaikkunan painikkeet (CompareResultsDialog)
Avautuu kun: Napsautat valikkopalkista Vertailu > Vuosi vertailu

Yleiset painikkeet (alareunassa):
Lataa sessio…-painike:
Avaa tiedostovalintaikkunan
Lataa .json-istuntotiedoston
Päivittää kaikki kolme välilehteä
Näyttää ladatun istunnon metatiedot
Ei vaikuta pääikkunan dataan
Sulku-painike:
Sulkee vertailuikkunan
Ei tallenna mitään
Korjaus tarkistus -välilehti:
Nykyinen kategoria -teksti:
Näyttää "Kategoria: [Rakennus/Maapohja]"
Päivittyy kun vaihdat kategoriaa
Vaihda kategoria -painike:
Vaihtaa näkymän Rakennus ↔ Maapohja välillä
Kehäkierto: Rakennus → Maapohja → Rakennus
Päivittää taulukon välittömästi
Pois käytöstä jos vain yksi kategoria
Tarkista tiedot -painike:
Suorittaa geometriapohjaisen validoinnin
Etsii kohteita 1 metrin säteellä
Käyttää ryhmärajoitteita:
Rakennus → Rakennukset/Rakennuksen Osat
Maapohja → Määrä-alat
Laskee OK/Check-määrät
Laskee Kiinteistövero-summia
Värjää taulukon rivit:
Vihreä (#e8f5e9): OK
Punainen (#ffebee): Check
Valkoinen: Ei validoitu
Päivittää kaikki tilastot
Näyttää yhteenvedon ponnahdusikkunassa
Taulukko (QTableView):
Näyttää ladatut kohteet nykyiselle kategorialle
Sarakkeet (Rakennus): Pysyvä rakennustunnus, Kiinteistötunnus, Rakennuksen numero, Taso, Kommentti
Sarakkeet (Maapohja): Kiinteistötunnus, Maapohjan Numero, Taso, Kommentti
Lisäsarakkeet validoinnin jälkeen: Tila, Nykyinen taso, Huomio
Vain luku (ei muokattavissa)
Kaksoisnapsautus avaa vain luku -näkymän + Candidate Data
Tilastot & kaaviot -välilehti:

Rakennus - Tarkistus tilastot -ryhmä:
OK kohteita: [määrä]
Check kohteita: [määrä]
Kiinteistövero lisä (siirrot): [summa] €
Kiinteistövero erot (päivittyneet): [summa] €
Maapohja - Tarkistus tilastot -ryhmä:
OK kohteita: [määrä]
Check kohteita: [määrä]
Kiinteistövero lisä (siirrot): [summa] €
Kiinteistövero erot (päivittyneet): [summa] €
Kiinteistövero tilastojen laskenta -ryhmä:
Selitysteksti laskentalogiikasta
Kuvaa milloin lisä lasketaan (siirrot)
Kuvaa milloin erot lasketaan (päivitetyt)
Info-välilehti:


Ladattu sessio -ryhmä:
Otsikko: [istunnon projektin nimi]
Polku: [istunnon projektin polku]
Muokattu: [istunnon viimeisin muokkaus]
Nykyinen projekti -ryhmä:
Otsikko: [nykyisen projektin nimi]
Polku: [nykyisen projektin polku]
Muokattu: [nykyisen projektin viimeisin muokkaus]
Yhteenveto-ryhmä:
Kohteita: [kokonaismäärä]
Täsmäsi: [löydetty]
Ei täsmännyt: [ei löydetty]
Huomio-viestien selitykset -ryhmä:
Pitkä selitysteksti kaikista mahdollisista Huomio-viesteistä
Kuvaa mitä kukin viesti tarkoittaa
Auttaa tulkitsemaan validointituloksia
