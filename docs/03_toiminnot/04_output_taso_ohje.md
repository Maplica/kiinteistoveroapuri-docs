---
sidebar_position: 4
---

# Tulosaineistojen opas

## GeoPackage-tulosaineiston rakenne

KiinteistöveroApurin prosessointityökalu tuottaa kattavan GeoPackage-tiedoston, joka sisältää **12 järjestettyä tasoa**. Nämä tasot tarjoavat kokonaisvaltaisen näkymän kunnan kiinteistöverotiedoista. Tasot korostavat verotietoja, tietojen attribuutteja, poikkeamia ja tilastollisia yhteenvetoja. Jokaisella tasolla on oma erityinen roolinsa verotietojen tarkastus- ja hallintaprosessissa.

Jokaiselle tasolle on määritelty valmiit **QML-karttatyylit**, jotka ladataan tasoille automaattisesti ensimmäisen kerran, kun ne avataan prosessoinnin jälkeen. Tyylit on suunniteltu niin, että tärkeimmät havainnot erottuvat kartalta välittömästi. Tyylejä voi jälkeenpäin muokata itse paremmin sopimaan omaa tulkintaa. Kun tyylejä on muokattu ja tallentaa projektiin ne aukevat tallennetulla tavalla uudelleen seuraavan kerran, kun projekti avataan. Alukeperäiset tyylit saadan tämän jälkeen takaisin vain prosessoimalla tiedot uudestaan.


## Tasojen yleiskuvaus

### **Rakennukset – 5 tasoa**

#### 1. **Rakennukset_Yhdistetty_vero_ja_tietokanta**
*(Yhdistetyt rakennukset: vero + tietokanta)*

**Tarkoitus:** Tästä tasosta löytyy, rakennukset, jotka löytyvät sekä kunnan tietokannasta että Verohallinnon aineistosta ja on onnistuneesti yhdistetty toisiinsa. Taso sisältää molempien järjestelmien tiedot rinnakkain, joten pinta-aloja, tilavuuksia, valmistumisvuosia, omistajatietoja ja kiinteistöveroja voi vertailla suoraan. Automaattisesti lasketut erotuskentät (`Building_Area_difference`, `Building_Volume_difference`) osoittavat numeraalisesti, kuinka paljon tietokannan ja verotuksen pinta-ala- ja tilavuusarvot poikkeavat toisistaan rakennuskohtaisesti.
Tasolle löytyy lisäksi kolme erillaista kuvastyyliä. 1. Pinta-alaero (Area_difference), 2. Kiinteistövero (euroina) ja 3. Verotusarvo (euroina). Näitä voi käyttää visualisoidakseen kartalle miten tiedot sjioittuvat ja tehdä karttapohjista tutkimusta tiedoista. Alla selitys tason tyyleistä, mitä ne esittävät ja millä tavalla. 

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa näkyy Rakennukset_Yhdistetty-taso pinta-alaerojen värityksellä (punainen-keltainen-sininen) -->

---

**🎨 Käytettävissä olevat karttatyylit**

Tälle tasolle on määritelty **3 erilaista karttatyyliä**, jotka korostavat eri tietoja:

**Tyyli 1: Pinta-alaero (Area_difference)**
Tyyli esittää kunnan rakennustietokannan ja Verohallinnon pinta-alatietojen välisen eron timanttisymboleilla. Väriskaala etenee **punaisesta keltaisen kautta siniseen** (ns. Hot–Cold), jolloin poikkeamat erottuvat visuaalisesti selkeästi.

Tyylin avulla voidaan tunnistaa rakennusten pinta-alaerot ja tarvittaessa tarkistaa sekä korjata tiedot rakennusrekisterin mukaisiksi, mikäli verotiedoissa esiintyy virheitä. Koska rakennuksen pinta-ala vaikuttaa suoraan verotukseen, tietojen oikeellisuus on tärkeää, jotta kunta ei menetä verotuloja.

Tyyli on kuitenkin riippuvainen kunnan rakennustietokannan oikeellisuudesta. Mikäli rekisterin tiedot eivät ole ajan tasalla tai paikkansapitäviä, tulkinnassa on noudatettava erityistä huolellisuutta. Toisaalta samaa visualisointia voidaan hyödyntää myös oman rekisterin laadun parantamiseen, sillä se korostaa selkeitä pinta-alaeroja rakennusten välillä.

Alla tyylin väriskaala ja miten värit jakautuvat arvoväleihin:

| Luokka | Arvoväli (m²) | Väri |
|--------|--------------|------|
| Suuri negatiivinen ero | < −18 000 | 🔴 Punainen |
| Keskisuuri negatiivinen | −18 000 – −500 | 🟠 Oranssinpunainen |
| Pieni negatiivinen | −500 – −25 | 🟡 Oranssi |
| Lähes nolla (neg.) | −25 – −1 | 🟡 Vaaleankeltainen |
| Lähes nolla (pos.) | −1 – 25 | 🔵 Vaaleansininen |
| Pieni positiivinen | 25 – 500 | 🔵 Keskisininen |
| Keskisuuri positiivinen | 500 – 18 000 | 🔵 Sininen |
| Suuri positiivinen ero | > 18 000 | 🔵 Tummansininen |

> **Tulkinta:** 
Punaiset ja oranssit timantit tarkoittavat, että verotuksen pinta-ala on pienempi kuin kunnan rekisterin – tämä on kriittinen havainto, koska verosaatavaa voi puuttua. 
Siniset timantit tarkoittavat, että verotuksessa on enemmän pinta-alaa kuin rekisterissä – syy voi olla yliverotus tai virheellinen tieto tietokannassa. 
Keltainen väri tarkoittaa, että erotus on lähellä nollaa eikä välitöntä toimenpidetarvetta ole.

<!-- PLACEHOLDER: Kuvakaappaus pinta-alaeron karttatyylistä, jossa timanttisymbolit punaisesta siniseen -->

**Tyyli 2: Kiinteistövero (euroina)**
Esittää rakennuksen kiinteistöveron suuruuden **keltaisena ympyränä**, jonka koko kasvaa veron määrän mukaan. Kaikki ympyrät ovat samankeltaisia — koko on ainoa muuttuva tekijä.

Tyylin avulla voidaan tunnistaa kartalta nopeasti eniten veroa tuottavat rakennukset. Suuret ympyrät osoittavat kohteet, joihin kannattaa kohdistaa tarkempi tarkistus tai jotka ovat tärkeitä budjettiarviossa.

Luokitus perustuu Jenks-menetelmään (luonnolliset rajat), joten raja-arvot mukautuvat aineiston jakaumaan eivätkä ole kiinteää arvoja.

Alla tyylin luokitusrajat ja symbolien koot:

| Luokka | Vero (€) | Symboli |
|--------|----------|--------|
| Hyvin pieni | 0 – 417 | <font size="1">●</font> |
| Pieni | 417 – 1 907 | <font size="2">●</font> |
| Keskisuuri | 4 699 – 13 959 | <font size="3">●</font> |
| Suuri | 30 407 – 64 394 | <font size="4">●</font> |
| Erittäin suuri | 90 226 – 191 130 | <font size="5">●</font> |
| Poikkeuksellinen | > 191 130 | <font size="6">●</font> |

> **Tulkinta:** Suuret keltaiset ympyrät osoittavat merkittävät verokohteet – kohdista niihin tarkempi tarkistus.

<!-- PLACEHOLDER: Kuvakaappaus kiinteistöveron karttatyylistä, jossa erikokoiset keltaiset ympyrät -->

**Tyyli 3: Verotusarvo (euroina)**
Esittää rakennuksen verotusarvon suuruuden **keltaisena ympyränä**, jonka koko kasvaa arvon mukaan. Kaikki ympyrät ovat samankeltaisia — koko on ainoa muuttuva tekijä.

Tyylin avulla voidaan vertailla rakennusten arvostustasoja kartalla ja tunnistaa kohteet, joiden verotusarvo on poikkeuksellisen korkea. Verotusarvo on kiinteistöveron laskentaperuste, joten se kertoo myös, mitkä rakennukset ovat potentiaalisesti merkittäviä verokohteita.

Huomio: Verotusarvo ei ole sama kuin kiinteistövero — korkea verotusarvo voi silti tuottaa pienen veron, jos veroprosentti on alhainen. Luokitus perustuu Jenks-menetelmään kuten kiinteistövero-tyylissäkin.

Alla tyylin luokitusrajat ja symbolien koot:

| Luokka | Verotusarvo (€) | Symboli |
|--------|----------------|--------|
| Pieni arvo | 0 – 49 891 | <font size="1">●</font> |
| Keskiarvo | 155 875 – 653 548 | <font size="3">●</font> |
| Korkea arvo | 980 198 – 2 776 980 | <font size="4">●</font> |
| Erittäin korkea | 3 724 117 – 11 700 917 | <font size="5">●</font> |
| Poikkeuksellinen | > 11 700 917 | <font size="6">●</font> |

> **Tulkinta:** Suuret keltaiset ympyrät osoittavat rakennukset, joiden verotusarvo on korkein. Vertaa kiinteistövero-tyyliin (tyyli 2) — jos suuri ympyrä verotusarvolla on pieni ympyrä verolla, voi veroprosentti olla poikkeuksellisen matala.

<!-- PLACEHOLDER: Kuvakaappaus verotusarvon karttatyylistä -->

---

**Sisältää:**
- **Täydelliset rakennustiedot molemmista lähteistä:**
  - Pysyvä rakennustunnus (PRT) – valtakunnallinen, standardoitu rakennustunniste
  - Kiinteistötunnus – yhdistää rakennuksen kiinteistöönsä
  - Rakennusnumero – paikallinen tunniste kiinteistön sisällä

- **Pinta-alatiedot molemmista järjestelmistä:**
  - Kerrosala kunnan tietokannasta
  - Kokonaisala kunnan tietokannasta  
  - Verohallinnon käyttämä rakennusala
  - Mahdollistaa suoran vertailun kunnan tietojen ja verotuksessa käytettyjen arvojen välillä

- **Tilavuustiedot:**
  - Rakennuksen tilavuus kunnan tietokannasta
  - Rakennuksen tilavuus Verohallinnolta
  - Erityisen tärkeä tietyissä verolaskelmissa ja rakennusten luokittelussa

- **Automaattisesti lasketut vertailukentät:**
  - `Building_Area_difference (vero – tietokanta)` – näyttää, kuinka monta neliömetriä Verohallinnon käyttämä pinta-ala poikkeaa kunnan tiedoista. Positiivinen arvo tarkoittaa, että verotuksen pinta-ala on suurempi, negatiivinen että kunnan tietokannan pinta-ala on suurempi. Auttaa priorisoimaan tarkistettavat rakennukset.
  - `Building_Volume_difference (vero – tietokanta)` – vastaava vertailu tilavuustiedoille. Suuret erot voivat viitata tiedonsyöttövirheisiin tai erilaisiin mittaustapoihin.

- **Vero- ja luokitustiedot:**
  - Kiinteistöveron arvot – vuosittainen kiinteistöveron määrä
  - Rakennuksen käyttötarkoitusluokat – asuin-, liike-, teollisuusrakennus jne.
  - Rakennusvuosi – mahdollistaa ikäperusteiset analyysit

- **Tietojen alkuperä (provenienssi):**
  - Kaikki sarakkeet on merkitty lähdejärjestelmän mukaan (`__kunta` = kunnan tietokanta, `__vero` = verotiedot, `__added` = lasketut kentät)
  - Mahdollistaa jokaisen arvon jäljittämisen lähdejärjestelmään

- **Omistajatiedot (jos henkilötietojen käsittely sallittu):**
  - Omistajan nimi tai nimet
  - Osoite- ja yhteystiedot
  - Omistajaluokka (yksityinen, yritys, julkinen)
  - Tietosuoja: mukana vain, mikäli GDPR asetus on ollut päällä aineiston käsittelyssä

**Käyttötapaukset:**
- **Rakennusten ensisijainen yhdistymisaineisto:** Aloita tästä nähdäksesi kaikki rakennukset, joissa yhdistys on onnistunut
- **Poikkeamaanalyysi:** Järjestä erotuskenttien mukaan löytääksesi merkittävät poikkeamat (esim. pinta-alaero > 10 m²)
- **Tietojen laadun varmistus:** Vertaa rakennuksen ominaisuuksia eri järjestelmien välillä ja tunnista päivitystarpeet
- **Vuosittainen vertailupohja:** Käytä lähtökohtana vuosittaiseen vertailuun ja seuraa tiedonlaadun kehittymistä
- **Verotuksen validointi:** Tarkista, että veron määrät vastaavat rakennuksen ominaisuuksia

---

#### 2. **Veroaineiston_rakennukset_puuttuvat_rekisteristä**
*(Verotuksen rakennukset, joita ei löydy kunnan rekisteristä)*

**Tarkoitus:** Rakennukset, jotka esiintyvät Verohallinnon aineistossa mutta joille ei löydy vastaavaa rakennusta kunnan rakennusrekisteristä. Rakennuksista maksetaan kiinteistöveroa, mutta niitä ei ole rekisteröity kunnan järjestelmään. Tasoa voi käyttää rakennusrekisterin täydentämiseen. Taso on myös yksi keskeinen taso, kun etsitään verotuksesta puuttuvia rakennuksia. Tällöin on tarksitettava löytyykö kiintiestöltä rakennuksia tältä tasolta jotka saattavat olla jo verotuksen piirissä, mutta jostain syystä eivät ole yhdistyneet kunnan tietokantaan esim. puuttuvien PRT:den takia. 

Tasolle on määritelty yksi karttatyyli. Alla selitys siitä, mitä se esittää ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa näkyy kirkkaanvihreitä ympyräsymboleita (puuttuvat rakennukset) kiinteistöjen päällä -->

---

**🎨 Karttatyyli**

**Tyyli:**
Esittää puuttuvat rakennukset **kirkkaanvihreänä bullseye-ympyränä**, joka muodostuu ulkoympyrästä ja pienestä sisäpisteestä. Kirkkaan vihreä väri on valittu tarkoituksella erottumaan selkeästi muista tasoista.

Tyylin avulla voidaan hahmottaa kartalta yhdellä silmäyksellä, millä kiinteistöillä on verotuksessa rakennuksia, joita ei löydy rekisteristä. Symboli sijoitetaan kiinteistön keskipisteeseen, joten se ei kuvaa rakennuksen tarkkaa sijaintia.

Alla tyylin symbolien kuvaukset:

<!-- PLACEHOLDER: Lähikuva bullseye-ympyräsymbolista ilmakuvan päällä -->


> **Tulkinta:** Kirkkaat vihreät ympyrät kartalla merkitsevät rakennuksia, jotka ovat verotuksessa mutta puuttuvat kunnan rekisteristä. Jokainen ympyrä sijaitsee sen kiinteistön keskipisteessä, johon rakennus veroaineistossa kuuluu.

---

**Sisältää:**
- **Kaikki Verohallinnon käytettävissä olevat rakennustiedot:**
  - Kiinteistötunnus veroaineistosta
  - Rakennuksen tunnistetiedot verorekisteristä (PRT, jos saatavilla, sekä rakennusnumero)
  - Verotusarvot, jotka osoittavat näihin rakennuksiin liittyvän verotuoton
  - Rakennuksen ominaisuudet (pinta-ala, tilavuus, käyttötarkoitus) Verohallinnon tietojen mukaisesti

- **Sijaintiesitys kartalla:**
  - Geometria: pistekohteet sijoitettuna kiinteistön keskipisteeseen, jolla verotietojen mukaan rakennus sijaitsee
  - Koska rakennusta ei voitu yhdistää todelliseen rakennusgeometriaan, järjestelmä muodostaa sijainnin kiinteistön perusteella
  - Mahdollistaa karttanäkymässä tarkastelun siitä, missä "puuttuvien" rakennusten oletetaan sijaitsevan

**Miksi rakennuksia päätyy tähän tasoon:**
- Rakennus on rakennettu, mutta sitä ei ole koskaan rekisteröity kunnan rakennusrekisteriin
- Rakennus on olemassa, mutta tunnistetiedot (esim. PRT) poikkeavat järjestelmien välillä
- Uudisrakentaminen, jossa verotusilmoitus on tehty ennen kuin kunnan tietokanta on päivitetty
- Rakennus on purettu, mutta ei poistettu verotuksen piiristä

**Käyttötapaukset:**
- **Tietokannan kattavuuden auditointi:** Jokainen kohde edustaa rakennusta, jonka tulisi todennäköisesti löytyä kunnan rekisteristä
- **Verotulojen varmistaminen:** Rakennuksista kertyy verotuloja – varmista, että ne on asianmukaisesti rekisteröity
- **Selvitys- ja tarkastusprosessi:**  
  1. Järjestä kohteet kiinteistötunnuksen mukaan ryhmitelläksesi rakennukset sijainnin perusteella  
  2. Käytä ilmakuvia tai maastokäyntejä rakenteen fyysisen olemassaolon varmistamiseen  
  3. Jos rakennus on olemassa, lisää se rekisteriin oikeilla tunnistetiedoilla  
  4. Jos rakennusta ei ole, selvitä asia Verohallinnon kanssa (purettu? koskaan rakennettu?)  
- **Tiedonlaadun mittarit:** Seuraa puuttuvien rakennusten määrää ajassa – tavoitteena on tämän tason pienentyminen vuosittain

---

#### 3. **Rekisterin_rakennukset_puuttuvat_verotiedosta**
*(Kunnan rekisterin rakennukset, joita ei löydy verotiedoista)*

**Tarkoitus:** Rakennukset, jotka löytyvät kunnan rakennusrekisteristä mutta joille ei löydy vastaavaa tietoa Verohallinnon aineistosta. Rakennukset voivat olla ilmoittamatta jääneitä verovelvollisia kohteita tai verovapaita rakennuksia, joiden vapautusperuste tulee varmistaa. Tasoa voi käyttää verotuksen kattavuuden tarkistamiseen. Taso on myös yksi keskeinen taso, kun etsitään rakennuksia, jotka saattavat olla verotuksen ulkopuolella ilman perustetta. Tällöin on tarkistettava, löytyykö kiinteistöltä rakennuksia tältä tasolta, jotka saattavat olla verovelvollisia mutta jostain syystä eivät näy Verohallinnon aineistossa — esim. puuttuvien tai virheellisten tunnistetietojen takia. 

Tasolle on määritelty yksi karttatyyli. Alla selitys siitä, mitä se esittää ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa oranssi "Check"-symboli ja vihreä "OK"-symboli näkyvät kiinteistöjen päällä -->

---

**🎨 Karttatyyli**
Esittää rakennukset **kuusikulmiosymboleina** (hexagoni), joiden väri kertoo, onko kohde jo käsitelty vai ei. Oranssi tarkoittaa vielä käsittelemätöntä kohdetta ja vihreä jo tarkistettua.

Rivin siirtäminen käsittely ikkunaan vaihtaa symboolin automaattisesti. Tällöin oletetaan, että rakennus on tarkistettu ja on puuttuva kohde. Tämä mahdollistaa selvitystyön etenemisen seuraamisen suoraan kartalla ilman erillisiä listoja.

Alla tyylin symbolit ja värit:

| Status-arvo | Merkitys | Symboli | Väri |
|-------------|----------|---------|------|
| **0** | ⚠️ Tarkistettava (Check) | Kuusikulmio 4,4 mm + sisäkuusikulmio 1,8 mm | 🟠 Oranssi + beige |
| **"1"** (tyhjä) | ✅ OK (käsitelty) | Kuusikulmio 4,4 mm | 🟢 Vihreä |

> **Tulkinta:** Oranssit kuusikulmiot ovat vielä käsittelemättä ja vaativat tarkistuksen. Vihreät kuusikulmiot on jo tarkistettu. Status-kenttää muokkaamalla voi seurata selvitystyön etenemistä kartalla reaaliajassa.

<!-- PLACEHOLDER: Kuvakaappaus, jossa näkyy oransseja ja vihreitä kuusikulmioita rinnakkain – havainnollistaa työnkulkua -->

---

**Sisältää:**
- **Täydelliset kunnan rakennusrekisterin tiedot:**
  - Rakennuksen täydellinen geometria kunnan paikkatietoaineistosta (todelliset rakennusjäljet tai pisteet)
  - Kiinteistötunnus ja rakennusnumero
  - Rakennuksen ominaisuudet kunnan tietokannasta (pinta-ala, tilavuus, ja muuta mitä on itse halunnut mukaan)
  - Kaikki kunnalla käytettävissä olevat tiedot näistä rakennuksista

**Miksi rakennuksia päätyy tähän tasoon:**
- **Puuttuvat rakennukset:** verotuksesta puuttuvat rakennukset jotka löytyvät rakennusrekisteristä
- **Verovapaat rakennukset:** julkiset rakennukset, kirkot, tietyt maatalousrakennukset – varmista, että vapautusta koskeva dokumentaatio on olemassa
- **Äskettäin rakennetut kohteet:** rakennus on rekisterissä, mutta verotusta koskevaa ilmoitusta ei ole vielä tehty
- **Puretut rakennukset:** rakennus on poistettu fyysisesti, mutta rekisteriä ei ole päivitetty – edellyttää tietokannan siivousta
- **Kynnyksen alittavat rakennukset:** pienet rakennukset, jotka jäävät verotettavan vähimmäiskoon alle
- **Tietojen ajoitus:** rakennus on lisätty rekisteriin verotussyklien välissä
- **Hallinnolliset virheet:** virheellinen kiinteistötunnus tai muu tunnistetieto, joka estää täsmäytyksen

**Kriittiset selvitysvaiheet:**
1. **Vapautusluetteloiden tarkistus:** Selvitä, kuuluuko rakennus verovapauden piiriin (esim. uskonnollinen, julkinen tai maatalouskäyttö)
2. **Nykytilan varmistaminen:** Käytä ilmakuvia tai maastokäyntiä sen toteamiseksi, onko rakennus edelleen olemassa
3. **Rakennuksen ominaisuuksien arviointi:** Onko rakennus kooltaan verotettava ja mikä on sen käyttötarkoitus?

**Käyttötapaukset:**
- **Verotulojen vuotoriskin tunnistaminen:** Ilmoittamatta jääneet verovelvollisuudet tarkoittavat menetettyjä kunnan tuloja
- **Verovapauden varmistaminen:** Tarkista, että vapautetuille rakennuksille on asianmukaiset perusteet ja päivitä luokitus tarvittaessa
- **Rekisteritiedon ajantasaisuus:** Tunnista puretut tai käyttötarkoitukseltaan muuttuneet rakennukset, jotka edellyttävät päivityksiä
- **Yhteistyö Verohallinnon kanssa:** Laadi ilmoituslistoja rakennuksista, jotka tulisi ottaa verotuksen piiriin
- **Vuosittainen seuranta:** Vertaa eri vuosien aineistoja ja seuraa, ratkeaako puuttuvien rakennusten tilanne vai jatkuuko se

---

#### 4. **Veroaineiston_muut_kohteet**
*(Muut erityiset verotettavat kohteet)*

**Tarkoitus:** Verohallinnon aineistossa esiintyvät verotettavat kohteet, jotka ovat luokiteltu muiksi kohteiksi. Nämä voivat olla esimerkiksi maaviljelyrakennukset, voimalaitoksia ja muut erikoisrakenteet, joista peritään kiinteistöveroa. Taso sisältää verotuslaskennan tiedot ja kohteiden sijainnin kiinteistön keskipisteessä. Tasolle on määritelty kaksi karttatyyliä: 1. Kiinteistövero (euroina) ja 2. Verotusarvo (euroina). Alla selitys siitä, mitä ne esittävät ja millä tavalla. Taso on tarkoitus käyttää samalla tavalla kuin Yhdistetyt rakennukset. Ainoana erona, että nämä on yhdistetty vain kiinteistöön, jolloin on tarkistettava puuttuvasta rakennustasosta onko tälle oma rakennus kunnan teitokannassa.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa näkyy erikokoisia keltaisia ympyröitä "muut kohteet" kiinteistöjen päällä -->

---

**🎨 Käytettävissä olevat karttatyylit**

Tälle tasolle on määritelty **2 karttatyyliä**, molemmat käyttävät keltaisia kokoasteikollisia ympyröitä:

**Tyyli 1: Kiinteistövero (euroina)**
Keltaiset ympyrät, joiden koko kasvaa kiinteistöveron mukaan. Luokitus: **Jenks** (luonnolliset rajat).

Tyylin avulla voidaan tunnistaa kartalta nopeasti eniten veroa tuottavat erikoiskohteet ja verrata niitä keskenään sekä muihin alueen rakennuksiin.
Huomio: Kohteet esitetään kiinteistön keskipisteessä, ei todellisessa sijainnissaan.

Alla tyylin symbolin koot verotusarvojen mukaan (12 luokkaa, 6–25 pt):

| Luokka | Vero (€) | Symboli |
|--------|----------|--------|
| Pienin | 0 – 417 | <font size="1">●</font> |
| Keskitaso | ~5 000 – 14 000 | <font size="3">●</font> |
| Suuri | ~30 000 – 64 000 | <font size="5">●</font> |
| Erittäin suuri | > 191 130 | <font size="6">●</font> |

> **Tulkinta:** Muut kohteet esitetään kiinteistön keskipisteessä (todellista geometriaa ei ole). Suuret ympyrät = merkittävät verokohteet.

**Tyyli 2: Verotusarvo (euroina)**
Esittää erikoiskohteen verotusarvon **keltaisena ympyränä**, jonka koko kasvaa verotusarvon mukaan. Tyyli on muuten samanlainen kuin Kiinteistövero-tyyli, mutta perustuu verotusarvoon eikä lopulliseen veron määrään.

Tyyliä voi käyttää vertailemaan erikoiskohteiden arvostustasoja tai tarkistamaan, onko kohteen verotusarvo suhteessa muihin alueen kohteisiin. Tyyliä voi käyttää vertailemaan erikoiskohteiden arvostustasoja tai tarkistamaan, onko kohteen verotusarvo suhteessa muihin alueen kohteisiin. Korkea verotusarvo ei aina tarkoita korkeaa veroa, jos veroprosentti on matala.

Huomio: Kohteet esitetään kiinteistön keskipisteessä, ei todellisessa sijainnissaan.

Alla tyylin symbolin koot verotusarvojen mukaan (12 luokkaa, 6–25 pt):

| Luokka | Verotusarvo | Symboli |
|--------|------------|--------|
| Pienin | Alueen pienimmät | <font size="1">●</font> |
| Kasvava | → | <font size="3">●</font> |
| Suuri | → | <font size="5">●</font> |
| Suurin | Alueen suurimmat | <font size="6">●</font> |

> **Tulkinta:** Muut kohteet esitetään kiinteistön keskipisteessä (todellista geometriaa ei ole). Suuret ympyrät = merkittävät verokohteet.

<!-- PLACEHOLDER: Kuvakaappaus verotusarvon karttatyylistä muiden kohteiden osalta -->

---

**Sisältää**
- **Verotiedot:**
  - Kiinteistötunnus
  - Veroteidot euroissa
  - Käyttötarkoitus

- **Geometrinen esitys:**
  - Pistegeometria sijoitettuna kiinteistön keskipisteeseen (todellista rakennusjälkeä ei ole saatavilla)
  - Mahdollistaa kohteiden tarkastelun kartalla ja suhteessa muihin rekisteritietoihin

**Tyypillisiä kohdetyyppejä tässä tasossa:**
- **Maaviljelyrakennukset:** maatalouskäytössä olevat rakennukset ja rakennelmat, joista peritään kiinteistöveroa
- **Voimalaitokset:** sähköntuotanto- ja energialaitokset sekä niihin liittyvät rakenteet
- **Erikoisrakenteet:** muut Verohallinnon muiksi kohteiksi luokittelemat verotettavat rakennelmat, jotka eivät sovi tavalliseen rakennusluokitteluun

**Miksi erillinen seuranta on tärkeää:**
- Veronlaskentamenetelmät poikkeavat merkittävästi tavanomaisista rakennuksista
- Kohteilla voi olla erityisiä vero- tai vapautusperusteita
- Ne jäävät helposti huomiotta perinteisissä rakennusinventaarioissa

**Käyttötapaukset:**
- **Erikoiskohteiden verotarkistus:** Tunnista kartalta merkittävimmät muut kohteet ja tarkista, että niiden verotus on oikein
- **Yhdistäminen rakennusrekisteriin:** Tarkista jokaiselle kohteelle, löytyykö vastaava rakennus kunnan tietokannasta — käytä puuttuvien rakennusten tasoa apuna
- **Verotusarvojen vertailu:** Vertaa erikoiskohteiden verotusarvoja muihin alueen kohteisiin ja tunnista poikkeukselliset arvot
- **Vuosittainen seuranta:** Seuraa muuttuuko kohteiden määrä ja verotaso vuosittain

---

#### 5. **Rakennukset_Pistepuutteet_lkm_Vero_vs_Rekisteri**
*(Rakennusten lukumääräpoikkeamat: veroaineisto vs. rekisteri)*

**Tarkoitus:** Taso korostaa kiinteistöjä sen perusteella, miten puuttuvat rakennusmäärät jakautuvat verotusaineiston ja kunnan rekisterin välillä. Tarkoituksena on helpottaa puutteiden havaitsemista. Kiinteistöt, joilla rakennusmäärä täsmää molemmissa järjestelmissä, voivat silti sisältää ongelmia — sama lukumäärä viittaa siihen, että rakennukset ovat todennäköisesti samoja, mutta eivät ole yhdistyneet toisiinsa esim. tunnistetietojen puutteiden takia. Eri lukumäärä puolestaan viittaa suoraan puutteisiin: joko rekisteristä tai verotuksesta puuttuu rakennuksia. Tasoa voi käyttää priorisoimaan, mitkä kiinteistöt kaipaavat tarkempaa selvitystä. Tasolle on määritelty yksi karttatyyli. Alla selitys siitä, mitä se esittää ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa kiinteistöpolygonit on väritetty keltaisella, magentalla ja vihreällä pistepuutetason mukaan -->

---

**🎨 Karttatyyli**
Värjää kiinteistöpolygonit **kolmella selkeällä värillä** sen mukaan, täsmääkö kiinteistön rakennusten lukumäärä järjestelmien välillä.

Tyylin avulla saa nopeasti yleiskuvan siitä, millä kiinteistöillä lukumäärä täsmää ja missä on ero. Kaikki värit voivat viitata selvitystarpeeseen — vihreäkin kiinteistö voi sisältää rakennuksia, jotka eivät ole yhdistyneet toisiinsa tunnistetietojen puutteiden takia.

Huomio: Tason väritys perustuu pelkkään rakennusten lukumäärään. Sama lukumäärä ei tarkoita, että rakennukset on oikein yhdistetty — vain että yhdistämättömiä on yhtä monta kummassakin tietokannassa.

Alla tyylin luokitusarvot ja värit:

| Merkitys | Väri | Kuvaus |
|----------|------|--------|
| Verotuksessa enemmän rakennuksia | 🟡 Keltainen | Veroaineistossa enemmän rakennuksia kuin rekisterissä → rekisteristä puuttuu rakennuksia |
| Tietokannassa enemmän rakennuksia | 🟣 Magenta | Rekisterissä enemmän rakennuksia kuin veroaineistossa → verotuksesta puuttuu rakennuksia |
| Lukumäärä täsmää | 🟢 Vihreä | Sama määrä kummallakin puolella — rakennukset ovat todennäköisesti samoja, mutta saattavat silti olla yhdistämättä toisiinsa |

> **Tulkinta:** Keltainen ja magenta osoittavat suoran puutteen — toisella puolella on enemmän rakennuksia. Vihreä tarkoittaa, että lukumäärä täsmää, mutta se ei vielä takaa oikeaa yhdistymistä. Vihreillä kiinteistöillä kannattaa tarkistaa yhdistymättömät rakennukset tasolta 2 ja 3.

<!-- PLACEHOLDER: Yleiskuva kartasta, jossa kaikki kolme väriä näkyvät - erityisesti keltaisten ja magentojen alueiden korostus -->

---
- **Erotus (vero – rekisteri):**
  - **Positiivinen erotus:** Verohallinnon tiedoissa on enemmän rakennuksia kuin kunnan rekisterissä → mahdollisesti puuttuvia kunnan rakennusrekisterissä
  - **Negatiivinen erotus:** Kunnan rekisterissä on enemmän rakennuksia kuin veroaineistossa → mahdollinen ilmoittamaton verovelvollisuus tai verovapaa rakennus
  - **Nollaerotus:** Rakennusten lukumäärä täsmää (huom. tämä ei vielä takaa, että yksittäiset rakennukset täsmäävät keskenään)

**Miksi tämä taso on arvokas:**
- **Nopeampi kuin yksittäistarkastelu:**  
  - Sen sijaan, että tarkistetaan tuhansia rakennuksia yksitellen, voidaan keskittyä vain niihin kiinteistöihin, joilla lukumäärät eivät täsmää
- **Järjestelmällisten ongelmien havaitseminen:**  
  - Jos tietyllä alueella esiintyy toistuvasti samanlaisia poikkeamia, se voi viitata alueelliseen tai prosessikohtaiseen tiedonkeruuongelmaan

---

### 🏠 **Rakennusosat – 2 tasoa**

#### 6. **Rakennusosat_Yhdistetty_vero_ja_tietokanta**
*(Yhdistetyt rakennusosat: vero + tietokanta)*

**Tarkoitus:** Tästä tasosta löytyvät Verohallinnon rakennusosat, jotka on onnistuneesti yhdistetty kunnan rakennusrekisterin rakennuksiin. Taso sisältää molempien järjestelmien kaikki tiedot rinnakkain rakennusosakohtaisesti — kunnan tietokannasta täydelliset rakennustiedot ja Verohallinnolta kaikki rakennusosatiedot — joten pinta-aloja, käyttötarkoituksia ja muita rakennusosan ominaisuuksia voi vertailla suoraan. Tätä voi tarkistella jos kiinnostaa verottajalle ilmoitetut rakennusten ominasiuudet. Rakennusten pinta-alat löytyvät verottajan rakennusosatiedoista, pinta-ala tiedot ovat prosessoinssa tuotu myös rakennustasolle. Mikäli joku rakennus on rakennettu eri aikaan tai laajennettu, kannattaa tarkastella tätä tasoa. Tasolle on määritelty yksi karttatyyli. Alla selitys siitä, mitä se esittää ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa näkyy erityyppisiä timanttisymboleita rakennusosien eri väreillä -->

---

**🎨 Karttatyyli**
Esittää rakennusosat **timanttisymboleina**, joiden väri vaihtelee **rakennusosan numeron** mukaan. Jokaiselle rakennusosan numerolle on oma värinsä, joten eri osia voi erottaa toisistaan kartalla.

Tyylin avulla voidaan nähdä yhdellä silmäyksellä, kuinka monta eri rakennusosaa samalla rakennuksella on. Useita eri värisiä timantteja samassa kohdassa tarkoittaa, että rakennuksella on verottajan teidoissa useampia osia — tyypillisesti kerrostaloissa tai sekakäyttökohteissa.

Huomio: Kohteet sijoitetaan emärakennuksen tai emäkiinteistön keskipisteeseen, ei rakennusosan tarkkaan sijaintiin. Symbolit voivat olla päällekkäin, jos samalla kiinteistöllä on useita osia.

Alla tyylin osakohtaiset värit:

| Osan numero | Väri | Kuvaus |
|-------------|------|--------|
| **1** | ⬜ Valkoinen | Ensimmäinen rakennusosa (pääosa) |
| **2** | 🟢 Vihreä | Toinen rakennusosa |
| **3** | 🔵 Sininen | Kolmas rakennusosa |
| **4** | 🟦 Syaani | Neljäs rakennusosa |
| **5** | 🟣 Violetti | Viides rakennusosa |
| **6–** | 🎨 Väripaletti | Harvinaisemmat osat, kullakin oma sävynsä |

> **Tulkinta:** Jokainen timantti on yksi rakennusosa. Valkoinen timantti tarkoittaa ensimmäistä eli päärakennusosaa, muut värit merkitsevät lisäosia. Useita eri värisiä timantteja samassa paikassa näkee kerrostaloissa ja sekakäyttökohteissa, joissa on useampi osa.

<!-- PLACEHOLDER: Kuvakaappaus, jossa saman rakennuksen useita erikrävisiä timanttisymboleita näkyy vierekkäin -->

---
**Sisältää**
- **Verotietoja**
  - Rakennuksen PRT (pysyvä rakennustunnus)
  - Rakennuksen rakennusnumero
  - Rakennusosannumeron
  - Koko rakennuksen verotiedot euroina
  - Rakennusosan ominaisteitoja (pinta-ala, materiaali, sauna, hissi...)
  - Liike- tai toimistotunnukset, vuokratilat
  - Rakennusosan käyttötarkoitusluokka (asuminen, liike, muu)

**Milloin tämä taso on erityisen tärkeä:**
- **Asunto-osakeyhtiöt:** jokaisella huoneistolla voi olla oma omistaja ja veroperuste
- **Sekakäyttörakennukset:** alakerrassa liiketiloja, ylemmissä kerroksissa asuntoja
- **Jaetut rakennukset:** rakennukset, jotka on jaettu erikseen verotettaviin osiin

**Käyttötapaukset:**
- **Rakennusosien lisäykset:** tunnista uudet yksiköt (esim. kellaritilan muutto asunnoksi)
- **Sekakäyttöanalyysi:** analysoi asuin- ja liiketilojen osuuksia

---

#### 7. **Veroaineiston_rakennusosat_puuttuvat_rekisteristä**
*(Veroaineiston rakennusosat, joita ei löydy rekisteristä)*

**Tarkoitus:** Rakennusosat, jotka esiintyvät Verohallinnon aineistossa mutta joille ei löydy vastaavaa kohdetta kunnan rakennusrekisteristä. Rakennuosat korjautuvat kun rakennusten PRT:t korjataan. Tämä taso on enemmän vain katselua varten. Ei anna mitään enemmän lisäarvoa kuin taso 2 Veroaineiston_rakennukset_puuttuvat_rekisteristä. Taso voi hyödyntää, jos tutkitaan rakennustietokannasta puuttuvan rakennuksen ominaispiirteitä.

Tasolle on määritelty yksi karttatyyli. Alla selitys siitä, mitä se esittää ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa punaisia kolmiosymboleita näkyy rakennusten kohdalla -->

---

**🎨 Karttatyyli**
Esittää puuttuvat rakennusosat **punaisina kolmioina**. Punainen väri ja kolmiomuoto on valittu selkeäksi varoitussymboliksi, joka erottuu muista tasoista.

Tyylin avulla voidaan nähdä, missä rakennuksissa tai kiinteistöillä on verotuksessa rakennusosia, joita ei löydy kunnan rekisteristä. Useita kolmioita samassa rakennuksessa tarkoittaa useampaa puuttuvaa rakennusosaa.

Alla tyylin symbolin kuvaus:

<font size="5">🔺</font> : Puuttuva rakennusosa

> **Tulkinta:** Jokainen punainen kolmio on yksi rakennusosa, joka on verotuksessa mutta vastaavaa tunnsta ei löydy kunnan rakennusrekisteristä. Useita kolmioita samassa rakennuksessa tarkoittaa, että osia on useampi yhdelle rakennukselle, joka ei löytynt kunnan rakennuskannasta.

<!-- PLACEHOLDER: Lähikuva punaisesta kolmiosymbolista rakennuksen päällä -->

---

- **Viittaukset rakennukseen:**
  - Linkitys rakennuksen PRT tunnukseen tai kiinteistötunnukseen
  - Osoittaa, mihin rakennukseen rakennusosa kuuluu
  - Rakennus voi olla mukana pääasiallisessa rakennusosassa

- **Rakennusosien ominaisuudet veroaineiston mukaan:**
  - Osan pinta-ala verotuksessa
  - Käyttötarkoitus (asuin, liike)
  - Rakennuspäivämäärät

**Miksi rakennusosia päätyy tähän tasoon:**
- **Tietokannan tarkkuusero:** Vastaavaa rakennustunnusta ei löytynyt kunnan tietokannasta

---

### 🌍 **Kiinteistöt – 2 tasoa**

#### 8. **Kiinteistöt_Yhdistetty_vero_ja_tietokanta**
*(Yhdistetyt kiinteistöt: vero + tietokanta)*

**Tarkoitus:** Kiinteistöt, jotka löytyvät sekä kunnan kiinteistötietokannasta että Verohallinnon aineistosta ja on onnistuneesti yhdistetty toisiinsa. Taso sisältää molempien järjestelmien kiinteistötiedot, kuten pinta-alat, omistajatiedot, kaavamerkinnät ja kiinteistöverot, rinnakkain vertailua varten. Taso toimii pääsäntöisenä tasona kun tarkastellaan maapohjan verotusta. Tähän kuuluu kaikki yhdistyneet tiedot, joten tämä antaa parhaan kuvan kunnan maapohjan kiintiestöveron jakautumisesta. Tasolle on määritelty viisi karttatyyliä: 1. Aluehinta (HotnCold), 2. Aluehinta (kategorinen), 3. Kaava-alue, 4. Kiinteistövero (euroina) ja 5. Ranta. Alla selitys siitä, mitä ne esittävät ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa kiinteistöpolygonit näkyvät Kiinteistövero-tyylillä (sinisestä punaiseen) -->

---

**🎨 Käytettävissä olevat karttatyylit**

Tälle tasolle on määritelty **5 erilaista karttatyyliä**, jotka korostavat kiinteistöjen eri ominaisuuksia:

**Tyyli 1: Aluehinta (HotnCold) – lämpökartta**
Näyttää kiinteistön aluehinnan **Turbo-värirampin** avulla 20 luokassa. Värit etenevät tumman violetista sinisen ja vihreän kautta keltaiseen ja tummanpunaiseen — kalleimmat kiinteistöt näkyvät punaisina, halvimmat violetin sävyissä.

Tyylin avulla voidaan hahmottaa nopeasti maan arvon jakautuminen alueella. Tyyli on erityisen hyödyllinen, kun halutaan verrata miten maapohjan arvo on kunnassa jakautunut.
Aluehinta on kiinteistön maapohjan yksikköhinta (€/m²) — se ei sisällä rakennusten arvoa.

Alla tyylin väriskaala ja miten värit jakautuvat aluehinnan mukaan:

| Luokka | Arvoväli | Väri |
|--------|----------|------|
| Matalin | Alueen matalimmat | 🟣 Tumma violetti |
| Matala | → | 🔵 Sininen |
| Keskitaso | → | 🟢 Vihreä |
| Korkea | → | 🟡 Keltainen |
| Korkein | Alueen korkeimmat | 🔴 Tummanpunainen |

> **Tulkinta:** Tumman violetti tarkoittaa matalinta aluehintaa ja tummanpunainen korkeinta. Tyyli näyttää tonttimaan arvon jakautumisen yhdellä silmäyksellä – kalleimmat alueet erottuvat punaisina ja halvimmat violetin sävyissä.

<!-- PLACEHOLDER: Kuvakaappaus Aluehinta HotnCold -tyylistä, jossa tubo-värirampin koko kirjo näkyy kartalla -->

**Tyyli 2: Aluehinta (kategorinen)**
Näyttää aluehinnan **71 erillisenä luokkana**, joista jokaisella on oma värinsä (HSV-pohjainen satunnaisväritys). Jokainen yksittäinen aluehinta-arvo saa oman värinsä, joten saman värisiä kiinteistöjä yhdistää sama hinta.

Tyyliä käytetään tilanteissa, joissa halutaan erottaa eri aluehintaisten kiinteistöjen rajat selkeästi toisistaan. HotnCold-tyyli (tyyli 1) sopii paremmin yleiskuvan saamiseen, mutta kategorinen tyyli on tarkempi silloin, kun tarkastella eroja enemmän paikallisesti.

Huomio: Värit ovat HSV-pohjaisia satunnaisvärejä — ne eivät edusta hinnan suuruutta eikä vierekkäisillä väreillä ole välttämättä yhteyttä toisiinsa.

<!-- PLACEHOLDER: Kuvakaappaus Aluehinta -tyylistä, jossa HSV näkyy kartalla --> 
<!-- PLACEHOLDER: Kuvakaappaus Aluehinta -tyylistä, jossa skaala näkyy -->

**Tyyli 3: Kaava-alue**
Näyttää kiinteistön kaavalajin **4 selkeällä värillä**: keltainen (ei kaavaa), sininen (rantakaava), pinkki-violetti (asemakaava) ja harmaa (tieto puuttuu). Luokitus perustuu `Kaavan_laji`-kenttään.

Tyylin avulla näkee nopeasti, onko kiinteistölle merkitty asemakaava tai rantaasemakaava. Tieto on tärkeä, koska veroprosentti voi vaihdella kaavalajin mukaan.

Alla tyylin kaavalajit ja niitä vastaavat värit:

| Kaavan laji | Väri | Kuvaus |
|-------------|------|--------|
| **NONE** | 🟡 Keltainen | Ei kaava-aluetta – haja-asutusalue |
| **SHORE** | 🔵 Vaaleansininen | Rantakaava-alue |
| **TOWN** | 🟣 Pinkki-violetti | Asemakaava-alue (taajama) |
| **NULL** | ⬜ Harmaa | Tieto puuttuu |

> **Tulkinta:** Keltainen tarkoittaa aluetta ilman kaavaa, sininen rantakaava-aluetta, pinkki-violetti asemakaava-aluetta ja harmaa kohdetta, jolta kaavatieto puuttuu. Kaavalaji voi vaikuttaa kiinteistön veroprosenttiin, joten tyyli auttaa nopeasti hahmottamaan, millä alueilla veroprosentti määräytyy minkäkin kaavaluokan mukaan.

<!-- PLACEHOLDER: Kuvakaappaus Kaava_alue -tyylistä, jossa keltaiset, siniset ja pinkit alueet näkyvät selkeästi -->

**Tyyli 4: Kiinteistövero (euroina)**
Värjää kiinteistöpolygonit **sinisestä punaiseen** veron suuruuden mukaan (11 luokkaa). Matalan veron kiinteistöt näkyvät sinisinä ja korkean veron kiinteistöt punaisina.

Tyylin avulla voidaan tunnistaa alueelta eniten veroa tuottavat kiinteistöt nopeasti. Tyyli sopii erityisesti budjettiarvioon ja tärkeimpien verokohteiden paikantamiseen kartalta. Tämän avulla voidaan myös yrittää tulkita miten eri kaavamuutokset ovat vaikuttaneet maapohjan kiinitestöverotuloihin.

Alla tyylin luokitusrajat ja värit:

| Luokka | Vero (€) | Väri |
|--------|----------|------|
| Hyvin matala | 0 – 60 | 🔵 Tummansininen |
| Matala | 60 – 150 | 🔵 Keskisininen |
| Keskitaso | 150 – 700 | 🟢 Turkoosi–vihreä |
| Kohtuullinen | 700 – 4 300 | 🟡 Vihreänkeltainen |
| Korkea | 4 300 – 27 000 | 🟠 Oranssi |
| Erittäin korkea | 27 000 – 70 000 | 🔴 Punainen |
| Poikkeuksellinen | > 70 000 | 🔴 Tummanpunainen |

> **Tulkinta:** Siniset kiinteistöt tuottavat vähän kiinteistöveroa ja punaiset eniten. Tyyli näyttää nopeasti, millä alueilla kiinteistöverotuotto on suurinta ja missä pienintä.

<!-- PLACEHOLDER: Kuvakaappaus Kiinteistövero-tyylistä sinisestä punaiseen -->

**Tyyli 5: Ranta (kyllä/ei)**
Näyttää kiinteistön rantastatuksen **kahdella värillä**: vihreä (ei rantaa) ja syaani (rantakiinteistö). Luokitus perustuu `Ranta`-kenttään.

Rantakiinteistöillä on usein eri veroprosentti kuin muilla kiinteistöillä. Tyylin avulla voidaan tarkistaa nopeasti, onko verotiedoissa rantaluokittelu tehty oikein. 

Alla tyylin arvot ja värit:

| Arvo | Väri | Kuvaus |
|------|------|--------|
| **NO SHORE** | 🟢 Vihreä | Ei rantaviivaa – sisämaan kiinteistö |
| **SHORE** | 🔵 Syaaninsininen | Rantakiinteistö |

> **Tulkinta:** Vihreät kiinteistöt eivät ole rantakiinteistöjä, siniset ovat. Rantakiinteistöillä on usein eri veroprosentti, joten tyyli auttaa tarkistamaan, onko luokittelu tehty oikein.

<!-- PLACEHOLDER: Kuvakaappaus Ranta-tyylistä, jossa vihreät ja syaaninväriset kiinteistöt erottuvat -->

---
**Sisältää**
- **Kiinteistön pinta-alat molemmista lähteistä:**
  - Kunnan kiinteistörekisterin kokonaispinta-ala (m²)
  - Verohallinnon käyttämä pinta-ala (Voi myös olla rakennuspaikan suuruus)

- **Maankäyttö- ja kaavamerkinnät (Kaavan käyttötarkoitus):**
  - Kunnan kaavoitusjärjestelmän mukainen käyttötarkoitus
  - Asuin-, liike-, teollisuus-, maa- ja metsätalousalueet jne.

- **Omistajatiedot (jos henkilötietojen käsittely sallittu):**
  - Omistajan nimi tai nimet
  - Osoite- ja yhteystiedot
  - Omistajaluokka (yksityinen, yritys, julkinen)
  - Tietosuoja: mukana vain, mikäli GDPR asetus on ollut päällä aineiston käsittelyssä

- **Verotustiedot (Kiinteistövero):**
  - Vuosittainen kiinteistöveron määrä
  - Verotusarvo
  - Veroluokka ja mahdolliset vapautukset

- **Kiinteistön ominaisuudet:**
  - Vesialueen osuus (jos soveltuu)
  - Käyttöluonne (rakennettu, rakentamaton, erityiskohde)

- **Kiinteistön geometria (polygonit):**
  - Viralliset rajat kiinteistötoimitusten perusteella
  - Tuki moniosaisille kohteille

**Miksi tämä taso on keskeinen:**
- **Omistusyhteys:** Kiinteistö yhdistyy verovelvolliseen
- **Kiinitestöveron jakautuminen:** Päätaso maapohjan kiintiestöveron tarkastusta varten

**Käyttötapaukset:**
- **Ensisijainen kiinteistörekisteri:** Virallinen lähde yhdistyneille kiinteistötiedoille
- **Kaavanmukaisuuden valvonta:** Tarkista, että kiinteistöjä verotetaan käyttötarkoituksen mukaan
- **Omistajaviestintä:** Tarivttaessa toimii lisäselvitysmenettelynä kiintiestöjen omistuksiin
- **Arvostusvertailut:** Vertaa verotusarvoja samankaltaisten kiinteistöjen välillä
- **Vuosittainen tarkistus:** Vertailupiste eri vuosien aineistoille

---

#### 9. **Rekisterin_Kiinteistöt_puuttuvat_verotiedosta**
*(Kunnan rekisterin kiinteistöt, joita ei löydy verotiedoista)*

**Tarkoitus:** Rakennettu kiinteistöt, jotka löytyvät kunnan paikkatietokannasta mutta joille ei löydy vastaavaa tietoa Verohallinnon aineistosta. Syy voi olla verovapautus, uusi kiinteistö jota ei ole vielä verotettu tai tunnisteiden ero järjestelmien välillä. Tämä taso auttaa havaitsemaan mahdolliset kiinteistöt jotka ovat jääneet kiintiestöverotuksen ulkopuolelle. Tasolle on määritelty yksi karttatyyli. Alla selitys siitä, mitä se esittää ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa ristikkokuvioisia ja pistekuvioisia kiinteistöpolygoneja näkyy -->

---

**🎨 Karttatyyli**
Esittää kiinteistöt **kuvioiduilla täytöillä** eikä tasavärillä, jolloin pohjalla olevat karttatasot näkyvät kuvioiden läpi. Oranssi ristikkokuvio tarkoittaa vielä selvittämätöntä kohdetta ja vihreä pistekuvio jo tarkistettua.

Symbooli vaihtuu siirtämällä kiintiestörivin käsittelyikkunaan. Tämä mahdollistaa selvitystyön etenemisen seuraamisen suoraan kartalla.

Huomio: Kuvioitu täyttö tarkoittaa, että taso kannattaa pitää päällimmäisenä tai lähes päällimmäisenä tasojärjestyksessä, jotta se näkyy selkeästi muiden tasojen päällä.

Alla tyylin Status-arvot, kuviotyypit ja värit:

| Merkitys | Kuviotyyppi | Väri |
|----------|-------------|------|
| ⚠️ Tarkistettava (Check) | Ristikkokuvio | 🟠 Ruskean oranssi |
| ✅ OK (käsitelty) | Pistekuvio | 🟢 Vihreä |

> **Tulkinta:** Oranssiristikuvioiset kiinteistöt ovat vielä selvittämättä. Vihreäpistekuvioiset on jo tarkistettu. Kuviot näkyvät muiden karttatasojen ja ilmakuvien päällä, joten taso voidaan pitää auki samaan aikaan muiden tasojen kanssa.

<!-- PLACEHOLDER: Lähikuva ristikko- ja pistekuviosta kiinteistöpolygonissa -->

---
**Sisältää**
  - Kunnan rekisteriteidot

- **Selvityksen tilaseuranta:**
  - Statustieto selvitystyön etenemiselle
  - Mahdollistaa puuttuvien verotietojen käsittelyn seurannan

**Keskeiset kysymykset jokaista kiinteistöä varten:**
- Onko kiinteistö verovapaa (esim. yleiset alueet, puistot, kirkot)?
- Onko kiinteistö muodostettu äskettäin?
- Onko tunnistetiedoissa virhe?

**Käyttötapaukset:**
- **Verotulojen palauttaminen:** tunnista verotettavat kiinteistöt verojärjestelmän ulkopuolella
- **Verovapauden valvonta:** varmista vapautusten voimassaolo ja perusteet
- **Tietojen synkronointiongelmat:** tunnista järjestelmien väliset tunnus virheet
- **Uudisalueiden seuranta:** seuraa uusien kiinteistöjen verotuksen aloitusta
- **Yhteistyö Verohallinnon kanssa:** tuota aineistot verotuksen kohdentamiseksi

---

### **Määräalat – 1 taso**

#### 10. **Maara-ala_Yhdistetty_vero_ja_tietokanta**
*(Yhdistetyt määräalat: vero + tietokanta)*

**Tarkoitus:** Määräalat, jotka löytyvät sekä kunnan kiinteistörekisteristä että Verohallinnon aineistosta ja on onnistuneesti yhdistetty toisiinsa. Taso sisältää molempien järjestelmien tiedot rinnakkain vertailua varten — pinta-alat, kaavamerkinnät ja kiinteistöverot. Taso toimii pääasiallisena tasona maapohjan verotuksen tarkasteluun määräalojen osalta. Taso käyttää samoja karttatyylejä kuin Kiinteistöt-taso (taso 8): 1. Aluehinta (HotnCold), 2. Aluehinta (kategorinen), 3. Kaava-alue, 4. Kiinteistövero (euroina) ja 5. Ranta. Alla selitys siitä, mitä ne esittävät ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa määräalojen polygonit näkyvät kiinteistöjen sisällä -->

---

**🎨 Käytettävissä olevat karttatyylit**

Tälle tasolle käytetään **samoja karttatyylejä kuin kiinteistötasolle (taso 8)**, katso tarkempi kuvaus sieltä:

---

**Sisältää**
- **Pinta-alat molemmista lähteistä:**
  - Kunnan kiinteistörekisterin kokonaispinta-ala (m²)
  - Verohallinnon käyttämä pinta-ala

- **Maankäyttö- ja kaavamerkinnät:**
  - Kunnan kaavoitusjärjestelmän mukainen käyttötarkoitus

- **Verotustiedot:**
  - Vuosittainen kiinteistöveron määrä
  - Verotusarvo ja veroluokka

- **Geometria (polygonit):**
  - Viralliset rajat kiinteistötoimitusten perusteella

**Miksi tämä taso on keskeinen:**
- **Omistusyhteys:** Määräala yhdistyy verovelvolliseen
- **Kiinteistöveron jakautuminen:** Päätaso maapohjan kiinteistöveron tarkastusta varten määräalojen osalta

**Käyttötapaukset:**
- **Ensisijainen määräalarekisteri:** Virallinen lähde yhdistyneille määräalatiedoille
- **Kaavanmukaisuuden valvonta:** Tarkista, että määräaloja verotetaan käyttötarkoituksen mukaan
- **Arvostusvertailut:** Vertaa verotusarvoja samankaltaisten määräalojen välillä
- **Vuosittainen tarkistus:** Vertailupiste eri vuosien aineistoille

---

### **Tilastolliset aggregaatiot – 2 tasoa**

#### 11. **Rakennukset_Tilastot**
*(Rakennustilastot alueittain)*

**Tarkoitus:** Aluejaon mukaan lasketut tilastotiedot rakennuksista. Taso kokoaa rakennusten pinta-alaerot, tilavuuserot ja kiinteistöverot alueittain vertailua varten. Tason tarkoitus on antaa parempi ymmärrys alueellisista eroista. Tasolle on määritelty neljä karttatyyliä: 1. Kiinteistövero – keskiarvo, 2. Kiinteistövero – summa, 3. Pinta-alaero – keskiarvo ja 4. Tilavuusero – keskiarvo. Alla selitys siitä, mitä ne esittävät ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa alueet on väritetty Turbo-rampilla kiinteistöveron keskiarvon mukaan -->

---

**🎨 Käytettävissä olevat karttatyylit**

Rakennustilastoille on määritelty **4 karttatyyliä**, jotka kaikki käyttävät **Turbo-värirampia** (violetista → sininen → vihreä → keltainen → oranssi → punainen).

**Tyyli 1: Kiinteistövero – keskiarvo (€/rakennus)**
Näyttää alueen rakennusten **keskimääräisen kiinteistöveron**. Violetti tarkoittaa matalaa keskimääräistä kiinteistöveroa ja punainen korkeaa.

Tyylin avulla voidaan vertailla kiintiestöveron kesskimääräistä jakautumista eri alueiden välillä. Korkea keskim. vero ei välttämättä tarkoita kalliita rakennuksia — se voi myös kertoa, että alueella on muutama hyvin korkean veron rakennus, jotka nostavat keskiarvoa.

Alla tyylin luokitusrajat ja värit:

| Luokka | Arvoväli (€) | Väri |
|--------|-------------|------|
| Hyvin matala | 0 – 250 | 🟣 Tumma violetti |
| Matala | 250 – 500 | 🔵 Sininen |
| Keskitaso | 500 – 1 000 | 🟢 Turkoosi |
| Kohtalainen | 1 000 – 2 500 | 🟢 Vihreänkeltainen |
| Korkea | 2 500 – 5 000 | 🟡 Keltainen |
| Hyvin korkea | 5 000 – 7 500 | 🟠 Oranssinpunainen |
| Poikkeuksellinen | > 7 500 | 🔴 Tummanpunainen |

> **Tulkinta:** Violetti tarkoittaa alueen rakennusten matalinta keskimääräistä kiinteistöveroa ja punainen korkeinta. Tyyli näyttää, millä alueilla rakennusten verotaso on korkeimillaan.

**Tyyli 2: Kiinteistövero – summa (€/alue)**
Näyttää alueen rakennuksista kertyvän **kokonaisverotuoton**. Violetti tarkoittaa matalaa summaveroa ja punainen korkeaa.

Tyylin avulla voidaan tunnistaa verotuoton kannalta tärkeimmät alueet. Suuri summa voi tarkoittaa paljon rakennuksia, muutamaa hyvin arvokasta rakennusta tai näitä molempia.

Alla tyylin luokitusrajat ja värit:

| Luokka | Arvoväli (€) | Väri |
|--------|-------------|------|
| Matala | 0 – 150 000 | 🟣 Tumma violetti |
| Keskitaso | 150 000 – 500 000 | 🔵 Syaaninsininen |
| Kohtalainen | 500 000 – 1 000 000 | 🟢 Vihreänkeltainen |
| Korkea | 1 000 000 – 1 500 000 | 🟠 Oranssi |
| Erittäin korkea | > 1 500 000 | 🔴 Tummanpunainen |

> **Tulkinta:** Violetti tarkoittaa alueen matalinta rakennusverotuottoa yhteensä ja punainen korkeinta. Tyyli näyttää, millä alueilla rakennuksista kertyy eniten kiinteistöveroa kokonaisuutena.

**Tyyli 3: Pinta-alaero – keskiarvo (m²)**
Näyttää alueen rakennusten **keskimääräisen pinta-alaeron** (vero − tietokanta). Sininen tarkoittaa, että kunnan rekisterissä on suurempi pinta-ala kuin verotuksessa, ja punainen tarkoittaa päinvastaista. Valkoinen tarkoittaa, että erotus on lähellä nollaa.

Tyylin avulla voidaan tunnistaa alueet, joilla pinta-alatietojen välinen ero on systemaattista. Jos kokonainen alue on tummansininen tai tummanpunainen, se voi viitata laajempaan tietojenkeruuvirheeseen tai alueen erityispiirteeseen.

Alla tyylin luokitusrajat ja värit:

| Luokka | Arvoväli (m²) | Väri |
|--------|-------------|------|
| Suuri negatiivinen | < −185 | 🟣 Tumma violetti |
| Negatiivinen | −185 – −90 | 🔵 Sininen |
| Pieni negatiivinen | −90 – −25 | 🔵 Vaaleansininen |
| Marginaali neg. | −25 – −1 | 🟢 Vihreä |
| **Nollaero** | **−1 – 1** | ⬜ **Valkoinen** |
| Marginaali pos. | 1 – 25 | 🟢 Vaaleanvihreä |
| Pieni positiivinen | 25 – 90 | 🟡 Keltainen |
| Positiivinen | 90 – 185 | 🟠 Oranssi |
| Suuri positiivinen | > 185 | 🔴 Tummanpunainen |

> **Tulkinta:** Valkoinen tarkoittaa, että alueen rakennusten pinta-alat täsmäävät keskimäärin. Tummat violetit tarkoittavat, että rekisterissä on selvästi enemmän pinta-alaa kuin verotuksessa. Tummat punaiset tarkoittavat, että verotuksessa on selvästi enemmän pinta-alaa kuin rekisterissä.

**Tyyli 4: Tilavuusero – keskiarvo (m³)**
Näyttää alueen rakennusten **keskimääräisen tilavuuseron** (vero − tietokanta). Sininen tarkoittaa, että kunnan rekisterissä on suurempi tilavuus kuin verotuksessa, ja punainen päinvastaista. Vihreä/valkoinen tarkoittaa, että erotus on pieni.

Tyylin avulla voidaan tunnistaa alueet, joilla tilavuustiedoissa on systemaattisia eroja järjestelmien välillä. Tilavuusero voi kertoa esimerkiksi erilaisista mittaustavoista tai puuttuvista kerroksista toisessa järjestelmässä.

Alla tyylin luokitusrajat ja värit:

| Luokka | Arvoväli (m³) | Väri |
|--------|-------------|------|
| Suuri negatiivinen | < −6 000 | 🟣 Tumma violetti |
| Negatiivinen | −6 000 – −1 000 | 🔵 Sininen |
| Lähes nolla | −200 – −50 | 🟢 Vihreä |
| Nollaero | −50 – 50 | 🟢 Vaaleanvihreä |
| Positiivinen | > 1 000 | 🟠 – 🔴 |

> **Tulkinta:** Valkoinen ja vihreä tarkoittavat, että tilavuuserot ovat pieniä. Tummat violetit tarkoittavat, että rekisterin tilavuusarvo on selvästi suurempi kuin verotuksen. Tummat punaiset tarkoittavat, että verotuksen tilavuusarvo on selvästi suurempi kuin rekisterin.

---

**Käyttötapaukset:**
- **Johdon raportointi:** veropohjan yhteenvetoraportit alueittain
- **Aluevertailut:** korkean ja matalan arvon alueiden tunnistaminen resurssien kohdentamiseksi
- **Datan laadun seuranta:** tilastolliset poikkeamat ohjaavat tarkempaan selvitykseen
- **Kehityksen seuranta:** alueiden muutokset ajan myötä (uusi rakentaminen, purkamiset)

---

#### 12. **Kiinteistöt_Tilastot**
*(Kiinteistötilastot alueittain)*

**Tarkoitus:** Aluejaon mukaan lasketut yhteenvetotiedot kiinteistöistä. Taso kokoaa kiinteistöjen aluehinnat, kiinteistöverot ja tonttitehokkuudet alueittain vertailua varten. Tason tarkoitus on antaa parempi ymmärrys alueellisista eroista. Tasolle on määritelty neljä karttatyyliä: 1. Aluehinta – keskiarvo, 2. Kiinteistövero – keskiarvo, 3. Kiinteistövero – summa ja 4. Tonttitehokkuus. Alla selitys siitä, mitä ne esittävät ja millä tavalla.

<!-- PLACEHOLDER: Kuvakaappaus kartalta, jossa alueet on väritetty Turbo-rampilla kiinteistöveron tai tonttitehokkuuden mukaan -->

---

**🎨 Käytettävissä olevat karttatyylit**

Kiinteistötilastoille on määritelty **4 karttatyyliä**, kaikki käyttävät **Turbo-värirampia** alueiden polygonitäyttönä:

**Tyyli 1: Aluehinta – keskiarvo (€/m²)**
Näyttää alueen **keskimääräisen tonttimaan aluehinnan**. Violetti tarkoittaa matalinta aluehintaa ja tummanpunainen korkeinta.

Tyylin avulla voidaan vertailla maan arvon jakautumista eri alueiden välillä. Korkea arvo tarkoittaa, että alueen kiinteistöjen maa on arvokkaampaa.

Alla tyylin luokitusrajat ja värit:

| Luokka | Arvoväli (€/m²) | Väri |
|--------|----------------|------|
| Erittäin matala | 0 – 1 | 🟣 Tumma violetti |
| Matala | 1 – 4 | 🔵 Sininen |
| Kohtuullinen | 4 – 8 | 🔵 Vaaleansininen |
| Keskitaso | 8 – 15 | 🟢 Turkoosi |
| Kohtalainen | 15 – 25 | 🟢 Vihreänkeltainen |
| Korkea | 25 – 40 | 🟡 Keltainen |
| Hyvin korkea | 40 – 60 | 🟠 Oranssi |
| Erittäin korkea | 60 – 90 | 🔴 Punainen |
| Poikkeuksellinen | > 90 | 🔴 Tummanpunainen |

> **Tulkinta:** Tummanvioletit alueet tarkoittavat matalinta aluehintaa ja tummanpunaiset korkeinta. Tyyli näyttää maan arvon jakautumisen alueittain – kalleimmat alueet erottuvat punaisina ja halvimmat violetin sävyissä.

**Tyyli 2: Kiinteistövero – keskiarvo (€/kiinteistö)**
Näyttää alueen kiinteistöjen **keskimääräisen kiinteistöveron**. Violetti tarkoittaa matalaa keskim. veroa ja punainen korkeaa.

Tyylin avulla voidaan vertailla, millä alueilla kiinteistöt maksavat eniten veroa keskim. Korkea arvo voi kertoa kalliista maa-alueista tai korkeammasta veroprosentista kyseisellä alueella.

Alla tyylin luokitusrajat ja värit:

| Luokka | Arvoväli (€) | Väri |
|--------|-------------|------|
| Matala | 0 – 100 | 🟣 Tumma violetti |
| Keskitaso | 100 – 210 | 🔵 – 🟢 Sininen–turkoosi |
| Kohtalainen | 210 – 1 100 | 🟢 Vihreänkeltainen |
| Korkea | 1 100 – 3 200 | 🟠 Oranssinpunainen |
| Erittäin korkea | > 3 200 | 🔴 Tummanpunainen |

> **Tulkinta:** Violetti tarkoittaa alueen kiinteistöjen matalinta keskimääräistä veroa ja punainen korkeinta. Tyyli näyttää, millä alueilla kiinteistöt maksavat eniten veroa keskimäärin.

**Tyyli 3: Kiinteistövero – summa (€/alue)**
Näyttää alueen kiinteistöistä kertyvän **kokonaisverotuoton**. Violetti tarkoittaa matalaa summaveroa ja punainen korkeaa.

Tyylin avulla voidaan tunnistaa verotuoton kannalta tärkeimmät alueet kiinteistöverotuksen näkökulmasta. Suuri summa voi kertoa paljon kiinteistöjä, arvokkaita maa-alueita tai näitä molempia.

Alla tyylin luokitusrajat ja värit:

| Luokka | Arvoväli (€) | Väri |
|--------|-------------|------|
| Matala | 0 – 28 000 | 🟣 Tumma violetti |
| Keskitaso | 28 000 – 70 000 | 🔵 – 🟢 Sininen–turkoosi |
| Kohtalainen | 70 000 – 200 000 | 🟢 – 🟡 Vihreä–keltainen |
| Korkea | 200 000 – 320 000 | 🟠 Oranssinpunainen |
| Erittäin korkea | > 320 000 | 🔴 Tummanpunainen |

> **Tulkinta:** Violetti tarkoittaa alueen matalinta kiinteistöverotuottoa yhteensä ja punainen korkeinta. Tyyli näyttää, millä alueilla kiinteistöistä kertyy eniten veroa kokonaisuutena.

**Tyyli 4: Tonttitehokkuus (keskiarvo)**
Näyttää alueen **keskimääräisen tonttitehokkuuden**. Violetti tarkoittaa matalaa tehokkuutta ja punainen korkeaa.

Tonttitehokkuus kertoo, kuinka paljon maalle on rakennettu suhteessa tontin kokoon. Matala arvo tarkoittaa väljää rakentamista, korkea arvo tiivistä kaupunkimaista rakentamista.

Alla tyylin luokitusrajat, tehokkuusarvot ja tyypilliset alueet:

| Luokka | Tonttitehokkuus | Väri | Tyypillinen alue |
|--------|----------------|------|-----------------|
| Hyvin matala | 0 – 0.07 | 🟣 Tumma violetti | Maaseutu, haja-asutus |
| Matala | 0.07 – 0.74 | 🔵 Syaaninsininen | Pientalovaltaiset alueet |
| Keskitaso | 0.74 – 1.4 | 🟢 Vihreänkeltainen | Tiiviit pientaloalueet |
| Korkea | 1.4 – 2.0 | 🟠 Oranssi | Kerrostaloalueet |
| Erittäin korkea | 2.0 – 4.7 | 🔴 Tummanpunainen | Intensiivinen kaupunkirakentaminen |

> **Tulkinta:** Matala tonttitehokkuus (violetti/sininen) tarkoittaa väljää, usein maaseutumaista rakentamista. Korkea arvo (oranssi/punainen) tarkoittaa tiivistä kaupunkimaista rakentamista. Tyyli näyttää, kuinka tehokkaasti eri alueiden maa-alue on rakennettu.

<!-- PLACEHOLDER: Kuvakaappaus tonttitehokkuuden karttatyylistä, jossa aluejaon värit vaihtelevat violetista punaiseen -->

---

**Käyttötapaukset:**
- **Johdon raportointi:** veropohjan yhteenvetoraportit kiinteistöistä alueittain
- **Aluevertailut:** korkean ja matalan arvon alueiden tunnistaminen resurssien kohdentamiseksi
- **Maankäytön suunnittelu:** omistusrakenteiden ja kehityspotentiaalin ymmärtäminen
- **Kehityksen seuranta:** alueiden muutokset ajan myötä

---

## Excel-lisäraportit

GeoPackage-tasojen lisäksi tuotetaan kaksi Excel-tiedostoa niille tietueille, joita ei saatu yhdistettyä ja jotka vaativat manuaalista selvitystä. Nämä ovat niin sanottuja "viimeisen keinon" tapauksia, joissa automaattinen spatiaalinen ja attribuuttipohjainen yhdistys epäonnistui. Tyypillisesti ne viittaavat datan laatuongelmiin, jotka edellyttävät asiantuntijan harkintaa.

### **TaxBuildings_not_Combined_[date].xlsx**

**Tarkoitus:** Verotuksen rakennustietueet, joita ei voitu linkittää mihinkään geometriaan. Rakennukset esiintyvät veroaineistossa, mutta järjestelmä ei pysty määrittämään niiden sijaintia tai oikeaa kohdetta. Kyseessä on kriittinen ongelma, joka vaatii manuaalista yhdistämistä tai tietojen korjaamista.

**Sisältää:**
- **Kaikki verohallinnon kentät yhdistämättömille rakennuksille:**
  - Kiinteistötunnus veroaineistosta (voi olla virheellinen tai vanhentunut)
  - Rakennuksen tunnisteet (PRT, rakennusnumero verohallinnon ilmoittamana)
  - Rakennusvuosi, käyttötarkoitus, pinta-alatiedot
  - Verotusarvot, jotka osoittavat aktiivisen verotuksen

- **Rakennuksen ominaisuudet:**
  - Kerrosala, kokonaisala ja tilavuus verotiedoista
  - Rakennusluokitus (asuin-, liike-, teollisuusrakennus jne.)
  - Kerrosluku, rakennusmateriaalit (jos saatavilla)

- **Verotiedot:**
  - Vuotuinen kiinteistövero
  - Verotuksen ajankohdat (milloin arviointi on tehty)

**Miksi rakennus päätyy Exceliin GeoPackagen sijaan:**
- Yhdistäminen tietokantaan epäonnistui: ei tunnisteosumaa eikä kelvollista sijaintia
- Virheelliset kiinteistötunnukset: veroaineiston tunnusta ei ole tietokannassa
- Orvot tietueet: verotetaan purettuja rakennuksia, joita ei ole vielä poistettu järjestelmästä
- Syöttövirheet: kirjoitusvirheet keskeisissä tunnistekentissä
- Kuntarajasekaannukset: rakennus sijaitsee todellisuudessa naapurikunnassa
- Historialliset tiedot: hyvin vanhat verotietueet rakennuksista, joita ei enää ole

---

### **Property_Not_Combined_[date].xlsx**

**Tarkoitus:** Verotuksen kiinteistötietueet, joita ei voitu linkittää mihinkään palstageometriaan. Kiinteistöt esiintyvät veroaineistossa, mutta järjestelmä ei pysty yhdistämään niitä paikkatietopohjaiseen kiinteistörekisteriin. Kyseessä on kriittinen ongelma, joka vaatii manuaalista selvitystä tai tietojen korjaamista.

**Sisältää:**
- **Kaikki verohallinnon kentät yhdistämättömille kiinteistöille:**
  - Kiinteistötunnus veroaineistosta (voi olla virheellinen tai vanhentunut)
  - Veroluokitus ja maankäyttöluokitus verohallinnon näkökulmasta
  - Maapohjan pinta-ala verotuksessa (m²)

- **Verotiedot:**
  - Vuotuinen kiinteistövero
  - Verotuksen ajankohdat (milloin arviointi on tehty)

**Miksi kiinteistö päätyy Exceliin GeoPackagen sijaan:**
- Yhdistäminen tietokantaan epäonnistui: ei tunnisteosumaa eikä vastaavaa GIS-kohdetta
- Virheelliset kiinteistötunnukset: veroaineiston tunnusta ei löydy kiinteistörekisteristä
- Uudet kiinteistöt: hiljattain lohkotut palstat, joita ei ole vielä rekisteröity
- Historialliset kiinteistöt: yhdistetyt tai lakkautetut palstat, jotka ovat yhä verotuksessa
- Syöttövirheet: kirjoitusvirheet keskeisissä tunnistekentissä

---

## Tasojen tyylit – yhteenveto

| Taso | QML-tyylejä | Päätyyli |
|------|-------------|---------|
| 1. Rakennukset_Yhdistetty | 3 | Pinta-alaero (timantti), Kiinteistövero (ympyrä), Verotusarvo (ympyrä) |
| 2. Veroaineiston_rakennukset_puuttuvat | 1 | Vihreä bullseye-ympyrä |
| 3. Rekisterin_rakennukset_puuttuvat | 1 | Oranssi/vihreä kuusikulmio (Status) |
| 4. Veroaineiston_muut_kohteet | 2 | Keltainen ympyrä (vero/arvo) |
| 5. Pistepuutteet | 1 | Keltainen/magenta/vihreä polygoni |
| 6. Rakennusosat_Yhdistetty | 1 | Värikoodattu timantti (osan numero) |
| 7. Veroaineiston_rakennusosat_puuttuvat | 1 | Punainen kolmio |
| 8. Kiinteistöt_Yhdistetty | 5 | Aluehinta, Kaava, Kiinteistövero, Ranta |
| 9. Rekisterin_Kiinteistöt_puuttuvat | 1 | Ristikko/pistekuvio (Status) |
| 10. Määräalat_Yhdistetty | 5 | Samat kuin taso 8 |
| 11. Rakennukset_Tilastot | 4 | Turbo-ramppi (vero, pinta-ala, tilavuus) |
| 12. Kiinteistöt_Tilastot | 4 | Turbo-ramppi (aluehinta, vero, tehokkuus) |

---

## Sarakkeiden tunnistejärjestelmä

Kaikki GeoPackage-tasojen sarakkeet on merkitty alkuperän mukaan:

- **`__kunta`** – kunnan tietokannan kentät (shapefile-aineistosta)
- **`__vero`** – verohallinnon kentät (viranomaisen Excel-aineistosta)
- **`__added`** – lasketut ja johdetut kentät (erot, aggregaatit, tilakentät)

**Huomio:** QGISin kenttien aliakset piilottavat nämä päätteet käyttöliittymässä, mutta ne säilyvät datassa seuraavia tarkoituksia varten:

- Tiedon alkuperän jäljitettävyys
- Ohjelmallinen suodatus työkaluissa
- Audit trail -dokumentaatio
- JSON-vientien rakenteistus

*Tämä opas kuvaa tulosaineistojen rakennetta. Tietoja näiden tasojen käyttämisestä selvitysprosessissa löytyy KiintiestöveroApurin käyttöohjeesta.*
