# Veroarvio-työkalut — Käyttöohje (VANHENTUNUT)

> **Tämä tiedosto on vanhentunut ja korvattu kattavammalla ohjeella.**
>
> Katso ajantasainen ohje kaikista 12 työkalusta täältä:
> **[KIINTEISTOVEROANALYYSI_OHJE.md](KIINTEISTOVEROANALYYSI_OHJE.md)**

---

<!-- Alla oleva sisältö on säilytetty arkistointitarkoituksessa. -->

Kiinteistöveroanalyysi-dialogi sisältää kaksi vertailevaa veroarviotyökalua:

- **Maapohja – Veroarvio** — arvioi uuden maapohjapalstan kiinteistöveron lähialueen rekisterikiinteistöjen aluehintoja vertailuna.
- **Rakennus – Veroarvio (vertaileva)** — arvioi uuden rakennuksen kiinteistöveron lähialueen olemassa olevien rakennusten vero-per-m²-tasoa vertailuna.

Molemmat työkalut käyttävät prosessoitua GPKG-tiedostoa (tai vastaavaa yhdistetyistä tasoista koostuvaa QGIS-projektia) ja toimivat kartalta valitun pisteen ympärillä määritetyllä hakusäteellä.

> **Huomio:** Nämä työkalut tuottavat **arvioita**, eivät virallisia verotuspäätöksiä. Viralliset verotusarvot vahvistaa ainoastaan Verohallinto.

---

## Dialogi-ikkuna

Avaa Kiinteistöveroanalyysi-ikkuna KiinteistöveroApuri-liitännäisen päävalikon kautta. Ikkuna on ei-modaalinen — se voi olla auki samanaikaisesti kartan ja päätyökalupalkin kanssa.

Ikkunan yläreunassa on **laskentatyökalujen valintaruutu**. Valitse pudotusvalikosta joko:

- `Maapohja – Veroarvio`
- `Rakennus – Veroarvio (vertaileva)`

---

## Maapohja – Veroarvio

![Maapohja Veroarvio -käyttöliittymä](../system_images/panel_maapohja_veroarvio.svg)

### Mitä työkalu tekee

Työkalu hakee QGIS-karttatasolta kaikki maapohjapalstat, joiden geometrian keskipiste on valitun karttapisteen ympyrän sisällä (hakusäde metreissä). Löydetyistä palstoja lasketaan:

- Aluehinta-statistiikka (minimi, keskiarvo, maksimi)
- Arvioitu kiinteistövero hypoteettiselle uudelle palstalle käyttäen kaavaa:

$$\text{KV} = \text{Aluehinta} \times \text{Pinta-ala} \times 0{,}75 \times \frac{\text{Veroprosentti}}{100}$$

Kerroin **0,75** on arvostamislain § 29 mukainen tavoitearvokerroin, jota sovelletaan kaikkiin asemakaavoitettuihin kiinteistöihin (haja-asutusalueilla se on jo sisäänrakennettu alennuskaavaan).

Tulostaulukko näyttää jokaisen löydetyn referenssipalstan tiedot — kiinteistötunnus, pinta-ala, aluehinta, verotusarvo, toteutunut kiinteistövero sekä arvio ko. aluehinnalla uudelle palstalle.

---

### Vasemman paneelin syöttökentät

| Kenttä | Kuvaus |
|---|---|
| **Maapohja-taso** | Valitse QGIS-projektin taso, josta referenssikiinteistöt haetaan. Yleensä `Kiinteistot_Yhdistetty_vero_ja_tietokanta` tai vastaava. |
| **Valitse sijainti kartalta** | Aktivoi karttapistepoimintatyökalun. Klikkaa kartalla kohtaa, johon hypoteettinen uusi palsta sijoittuisi. Koordinaatit näkyvät kentässä välittömästi. |
| **Pinta-ala (m²)** | Syötä hypoteettisen uuden palstan pinta-ala neliömetreinä. |
| **Käyttötarkoitus** | Monivalintalista. Valitse yksi tai useampi kaavan mukainen käyttötarkoitusluokka, jotka kelpuutetaan referensseiksi. Kun kaikki tai ei yhtään on valittuna, kaikki luokat hyväksytään. Klikkaamalla **"Valitse kaikki"** tai **"Poista kaikki valinnat"** -linkkiä voit vaihtaa kaikkien valintaa kerralla. |
| **Veroprosentti** | Valitse kunnan soveltama maapohjaveroprosentti (yleinen maapohja, vakituinen asunto tms.). Arvot luetaan Asetukset-dialogin veroprosenttitaulukon arvoista. |
| **Hakusäde (m)** | Säde metreissä, jolla referenssikiinteistöjä haetaan valitun pisteen ympäriltä. Oletus 1 000 m. Pienennä sädettä tiiviissä kaupunkiympäristössä, suurenna harvaan asutuilla alueilla. |

Paina **"Laske arvio"** -nappia käynnistääksesi haun ja laskennan.

---

### Tulospaneeli (oikea puoli)

#### Tuloskenttä

Kun laskenta on valmis, suuri sininen kenttä näyttää **arvioidun kiinteistöveron keskiarvon** (`Ka: X €`). Tämä vastaa hypoteettisen palstan kiinteistöveroa käyttäen referenssien aluehintakeskiarvoa.

Alapuolella oleva harmaa tekstikenttä näyttää:
- Laskentakaavan auki kirjoitettuna (aluehinta-ka × pinta-ala × 0,75 × veroprosentti)
- Vaihteluvälin (minimi–maksimi referenssien perusteella)
- Referenssikiinteistöjen lukumäärän

#### Näytä referenssit kartalla

Painike aktivoituu, kun haku on tuottanut tuloksia. Klikkaamalla se korostaa kaikki nykyisessä tuloslistassa olevat referenssikiinteistöt kartalla vihreänä korostuksena. Poistetut rivit **eivät** näy korostuksessa.

#### Referenssitaulukko

Taulukko listaa jokaisen löydetyn referenssipalstan. Sarakkeet:

| Sarake | Kuvaus |
|---|---|
| **Kiinteistötunnus** | Palstan virallinen kiinteistötunnus |
| **Pinta-ala (m²)** | Referenssipalstan rekisterin mukainen pinta-ala |
| **Aluehinta (€/m²)** | Verottajan rekisterin mukainen yksikköhinta |
| **Verotusarvo (€)** | Referenssipalstan laskettu verotusarvo (aluehinta × pinta-ala × 0,75) |
| **Kiint.vero (€)** | Referenssipalstan toteutunut kiinteistövero verottajan tiedoissa |
| **KV tällä aluehinnalla (€)** | **Arvio:** paljonko uusi palstasi maksaisi, jos sen aluehinta olisi tämän referenssin mukainen |

Rivit on järjestetty nousevaan aluehintajärjestykseen (edullisin ensin).

#### Poista valittu rivi

Valitse yksi tai useampi rivi taulukosta (Ctrl+klikkaus useammalle) ja paina **"Poista valittu rivi"**. Poistettu rivi:
- Poistuu taulukosta välittömästi
- Poistuu tilastolaskennasta (ka, min, max päivittyvät automaattisesti)
- Poistetaan karttakorostuksesta (seuraava "Näytä kartalla" -klikkaus ei enää korosta sitä)

Käytä tätä poistamaan selvästi poikkeavia tai epärelevantteja referenssejä ennen lopullisen arvion tekemistä.

> **Vinkki:** Jos poistat liikaa rivejä tai haluat aloittaa alusta, paina uudelleen **"Laske arvio"** — se hakee koko referenssilistan uudelleen.

---

### Käyttöesimerkki — Maapohja

**Tilanne:** Kunta harkitsee uuden 3 000 m² teollisuuspalstan myyntiä. Halutaan arvioida, minkä suuruinen kiinteistövero siitä peritään.

1. Avaa `Maapohja – Veroarvio`.
2. Valitse **Maapohja-taso**: `Kiinteistot_Yhdistetty_vero_ja_tietokanta`.
3. Klikkaa **"Valitse sijainti kartalta"** ja osoita kartalta tontin suunniteltu sijainti.
4. Syötä **Pinta-ala**: `3000`.
5. Valitse **Käyttötarkoitus**: rastita ainoastaan `T – Teollisuus` (poista muut).
6. Valitse **Veroprosentti**: `Maapohja – yleinen`.
7. Aseta **Hakusäde**: `1500` (teollisuusalueilla etäisyydet voivat olla suurempia).
8. Paina **"Laske arvio"**.
9. Tarkastele tulosta. Jos jokin referenssi on selvästi poikkeava (esim. aluehinta 2 €/m² muiden ollessa 25–35 €/m²), valitse se ja paina **"Poista valittu rivi"**.
10. Lopullinen `Ka:`-arvo on arvioitu kiinteistövero.

---

## Rakennus – Veroarvio (vertaileva)

![Rakennus Veroarvio -käyttöliittymä](../system_images/panel_rakennus_veroarvio.svg)

### Mitä työkalu tekee

Työkalu hakee lähialueen olemassa olevat rakennukset ja laskee niiden toteutuneen **vero per kerrosneliömetri** -suhteen. Tätä vertailusuhdetta käytetään arvioimaan uuden rakennuksen kiinteistövero:

$$\text{KV-arvio} = \frac{\text{Vero}_{\text{ref}}}{\text{Kerrosala}_{\text{ref}}} \times \text{Kerrosala}_{\text{uusi}}$$

Työkalu soveltuu erityisesti tilanteisiin, joissa rakennuksen jälleenhankinta-arvoa ei tiedetä tai halutaan nopeasti vertaileva arvio ilman täyttä verotusarvolaskentaa.

Rakennukset, joilta puuttuu verotusarvo tai kiinteistövero verottajan rekisterissä, **näkyvät silti taulukossa** (arvot "–"), jotta käyttäjä tietää niiden olemassaolosta. Ne eivät kuitenkaan vaikuta statistiikkaan.

---

### Vasemman paneelin syöttökentät

| Kenttä | Kuvaus |
|---|---|
| **Rakennukset-taso** | Valitse QGIS-projektin rakennus-taso. Yleensä `Rakennukset_Yhdistetty_vero_ja_tietokanta` tai vastaava. |
| **Valitse sijainti kartalta** | Kuten maapohjatyökalussa: poimii karttapisteen, jonka ympäriltä referenssejä haetaan. |
| **Kerrosala (m²)** | Hypoteettisen uuden rakennuksen kerrosala neliömetreinä. |
| **Rakennustyyppi** | Monivalintalista. Valitse yksi tai useampi VRK-rakennustyyppikoodi. Oletuksena kaikki tyypit ovat valittuna. Jos haluat verrata esim. vain omakotitaloja (koodi 039), poista muut valinnat. |
| **Veroprosentti** | Sovellettava rakennusveroprosentti (vakituinen asunto, yleinen rakennusvero tms.). |
| **Hakusäde (m)** | Säde metreissä. Oletus 500 m. |

Paina **"Laske arvio"** käynnistääksesi haun.

---

### Tulospaneeli (oikea puoli)

#### Tuloskenttä

Näyttää arvioidun kiinteistöveron keskiarvon (`Ka: X €`). Alapuolella:
- Laskentakaava: vero/m²-ka × kerrosala = arvio
- Vaihteluväli min–max
- Referenssien lukumäärä

#### Referenssitaulukko

| Sarake | Kuvaus |
|---|---|
| **Kiinteistötunnus** | Referenssirakennuksen kiinteistötunnus |
| **Tyyppi** | VRK-rakennustyyppikoodi |
| **Kerrosala (m²)** | Referenssirakennuksen veron rakennuspinta-ala |
| **Verotusarvo (€)** | Rakennuksen verotusarvo verottajan rekisterissä |
| **Vero (€)** | Toteutunut rakennuksen kiinteistövero |
| **Vero/m² (€)** | Laskettu suhdeluku: vero ÷ kerrosala |
| **KV tällä aluehinnalla (€)** | **Arvio:** paljonko uusi rakennuksesi maksaisi tämän referenssin vero/m²-suhteella |

Rivit, joilta puuttuu vero tai kerrosala, näkyvät `–`-arvoilla kaikissa laskennallisissa sarakkeissa. Ne voidaan jättää taulukkoon informatiivisessa tarkoituksessa tai poistaa "Poista valittu rivi" -painikkeella.

Rivit järjestetään vero/m²-arvon mukaan nousevaan järjestykseen (edullisimmat ensin). Rivit ilman verotietoa sijoitetaan taulukon loppuun.

#### Poista valittu rivi

Toimii samoin kuin maapohjatyökalussa. Poistaa valitun rivin taulukosta, päivittää tilastot ja synkronoi karttakorostuksen.

---

### Käyttöesimerkki — Rakennus

**Tilanne:** Uusi 180 m² omakotitalo on valmistumassa asuinalueelle. Arvioidaan sen tuleva kiinteistövero.

1. Avaa `Rakennus – Veroarvio (vertaileva)`.
2. Valitse **Rakennukset-taso**: `Rakennukset_Yhdistetty_vero_ja_tietokanta`.
3. Klikkaa **"Valitse sijainti kartalta"** ja osoita tulevan rakennuksen tontti.
4. Syötä **Kerrosala**: `180`.
5. Valitse **Rakennustyyppi**: rastita ainoastaan `039 – Omakotitalo` ja `199 – Muu asuinrakennus`.
6. Valitse **Veroprosentti**: `Vakituinen asunto`.
7. Paina **"Laske arvio"**.
8. Tarkastele referenssitaulukkoa. Poista mahdolliset selvästi poikkeavat tai epärelevanteiksi katsomasi kohteet.
9. Lopullinen `Ka:`-arvo on arvioitu kiinteistövero.

---

## Karttakorostus

Kun **"Näytä referenssit kartalla"** -painiketta painetaan:

- **Maapohjatyökalulla** löydetyt referenssipalstat korostetaan **vihreällä** täyttövärillä.
- **Rakennustyökalulla** löydetyt referenssirakennukset korostetaan **sinisellä** täyttövärillä.

Korostus näyttää ainoastaan ne referenssirivit, jotka ovat **tällä hetkellä taulukossa** — poistetut rivit eivät näy korostuksessa. Tämä mahdollistaa poikkeama-analyysin: näet kartalla tarkalleen, mitkä kiinteistöt vaikuttavat arvioon.

Korostus pysyy näkyvissä kunnes:
- Uusi haku käynnistetään (korostus päivittyy uusiin tuloksiin), tai
- QGIS-korostusnäkymä nollataan muulla tavoin.

---

## Usein kysytyt kysymykset

**Miksi hakusäteen sisällä olevat rakennukset eivät näy taulukossa?**
Tarkista, että oikea taso on valittuna. Jos rakennustyyppisuodatin on aktiivisena, varmista että haettu rakennustyyppikoodi löytyy valitussa tasossa kentästä `VRK-rakennustyyppi__vero`. Kokeile myös kasvattaa hakusädettä.

**Miksi jotkut rivit näyttävät "–" vero- ja kerrosalasarakkeissa?**
Rakennus on löydetty kartalta (se sijaitsee hakusäteen sisällä ja tyyppisuodatin hyväksyy sen), mutta kyseisellä kiinteistöllä ei ole kiinteistövero- tai pinta-alatietoa prosessoidussa aineistossa. Tämä voi johtua esim. verovapaudesta tai puuttuvasta tiedosta verottajan tiedostossa. Nämä rivit eivät vaikuta arvioon — ne on esitetty näkyvissä informatiivisessa tarkoituksessa.

**Miksi taulukossa on vain muutama rivi vaikka alueella on paljon kiinteistöjä?**
Käyttötarkoitus- tai rakennustyyppisuodatin rajaa tuloksia. Avaa monivalintalistoja ja tarkista, että oikeat kategoriat ovat valittuna. Voit myös kasvattaa hakusädettä.

**Miksi "Laske arvio" -painike näyttää virheen "Valitse taso ensin"?**
Mitään QGIS-tasoa ei ole ladattuna tai oikeaa tasoa ei ole valittuna Maapohja-taso / Rakennukset-taso -pudotusvalikossa.

**Voiko arvion perusteella tehdä virallisia päätöksiä?**
Ei. Tämä työkalu on suunnattu sisäiseen analyysiin ja arviointiin. Viralliset kiinteistöveron laskentapäätökset tekee Verohallinto arvostamislain mukaisesti.

---

## Yhteenveto käyttöönottovaiheista

```
1. Avaa Kiinteistöveroanalyysi-ikkuna
2. Valitse työkalu pudotusvalikosta
3. Valitse oikea QGIS-taso
4. Klikkaa "Valitse sijainti kartalta" → osoita kartalla
5. Täytä muut parametrit (pinta-ala/kerrosala, suodattimet, veroprosentti, hakusäde)
6. Paina "Laske arvio"
7. Tarkastele tulostaulukkoa — poista tarvittaessa poikkeavia rivejä
8. Lue lopullinen arvio tuloskehtässä (Ka: X €)
9. Halutessasi klikkaa "Näytä referenssit kartalla"
```
