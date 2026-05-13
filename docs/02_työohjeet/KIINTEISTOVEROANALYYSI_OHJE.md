---
sidebar_position: 4
---

# Kiinteistöveroanalyysi — Käyttöohje

> **Huomio — arviolaskelmat:** Kaikki tämän ikkunan työkalut tuottavat **arvioita**. Ne perustuvat Verohallinnon julkaisemiin laskentasääntöihin (arvostamislaki 1142/2005, VvMA 1073/2025 ja Verohallinnon päätös VH/5812/00.01.00/2025). **Viralliset verotusarvot ja kiinteistöveropäätökset vahvistaa ainoastaan Verohallinto.** Tätä työkalua ei voi käyttää virallisena verotusasiakirjana eikä valitusperusteena.

---

## 1. Yleistä

**Kiinteistöveroanalyysi** on KiinteistöveroApuri-liitännäisen analyysidialogi, joka kokoaa yhteen 12 laskentaa — maapohjan ja rakennusten veroarviolaskennan, tilastot, kohtuullistamissimuloinit ja yhteenvedon.

**Avaaminen:** Klikkaa KiinteistöveroApuri-paneelista **"Analyysi"**-painiketta. Ikkuna on **ei-modaalinen**: se pysyy auki kartan ja muiden dialogien ollessa aktiivisena.

**Koko:** Ikkuna aukeaa koossa 980 × 680 px. Se on suurennettavissa ja pienennettävissä normaalisti.

**Vastuuvapauslauseke:** Ikkunan oikeassa yläkulmassa on pieni **!**-merkki. Vie hiiri sen päälle lukeaksesi koko vastuuvapauslausekkeen.

---

## 2. Laskentatyökalun valinta

![Laskentatyökalun valintapudotusvalikko](/img/system_images/dialog_analyysi_toolselector.svg)

Ikkunan yläreunassa on pudotusvalikko **"Laskentatyökalu:"**. Kaikki 12 työkalua on lueteltu aihealueittain ryhmiteltyinä:

| Ryhmä | Työkalu |
|---|---|
| **── Maapohja ──** | Maapohja – Veroarvio |
| | Alennuskaava-laskuri |
| | Rakentamattoman tontin vertailu |
| | Rakennusoikeuden vajaakäyttö |
| | Rantakiinteistön arvio |
| | Aluehintojen jakaumaanalyysi |
| **── Rakennukset ──** | Rakennus – Veroarvio (vertaileva) |
| | Rakennus – Laskenta alusta |
| | Ikäalennus & Perusparannuslaskin |
| | Vero per m² rakennustyypeittäin |
| **── Yhteenveto ──** | Veropohja-yhteenveto |
| **── Ohje ──** | Ohje ja tietoa laskureista |

Ryhmäotsikot (harmaat, lihavoitu) eivät ole valittavissa — ne ovat vain jakajia. Valitse haluamasi työkalu klikkaamalla sen nimeä.

---

## 3. Veroprosenttien asettaminen

![Asetukset – veroprosentit](/img/system_images/settings_tax_rates.svg)

Monet laskurit käyttävät kunnan soveltamia veroprosentteja. Prosentit asetetaan **päädialogin Asetukset-välilehdellä** kohdassa **"Kiinteistövero prosentit"**.

Seitsemän tallennettavaa veroprosenttia ja niiden oletusarvot:

| Asetus | Seliteotsikko | Oletus |
|---|---|---|
| `tax_maapohja_yleinen` | Maapohja – yleinen | 1,00 % |
| `tax_rakennus_yleinen` | Rakennukset – yleinen | 1,00 % |
| `tax_vakituinen_asunto` | Vakituinen asunto | 0,45 % |
| `tax_muu_asuinrakennus` | Muu asuinrakennus | 1,00 % |
| `tax_yleishyodyllinen` | Yleishyödyllinen yhteisö | 0,00 % |
| `tax_rakentamaton_tontti` | Rakentamaton tontti | 3,00 % |
| `tax_voimalaitos` | Voimalaitos | 1,00 % |

Arvot tallennetaan QSettingsiin ja ovat voimassa välittömästi kaikissa laskureissa. **Aseta ne ennen ensimmäistä laskentaa** vastaamaan oman kuntasi voimassa olevia veroprosentteja.

---

## 4. Maapohja – Veroarvio

![Maapohja Veroarvio -käyttöliittymä](/img/system_images/panel_maapohja_veroarvio.svg)

### Mitä työkalu tekee

Hakee QGIS-karttatasolta kaikki maapohjapalstat, joiden geometrian keskipiste on valitun karttapisteen ympyrän sisällä (hakusäde metreissä), ja laskee referenssiksi kelpuutettujen palstajoukosta:

- **Aluehintastatistiikan** (minimi, keskiarvo, maksimi)
- **Arvioidun kiinteistöveron** hypoteettiselle uudelle palstalle:

```
KV = Aluehinta_ka × Pinta-ala × 0,75 × (Veroprosentti / 100)
```

Kerroin **0,75** on arvostamislain § 29 mukainen tavoitearvokerroin asemakaavoitetuille kiinteistöille.

### Syöttökentät

| Kenttä | Kuvaus | Oletus |
|---|---|---|
| **Maapohja-taso** | QGIS-taso, josta referenssit haetaan | – |
| **Valitse sijainti kartalta** | Aktivoi karttapistepoimintatyökalun | – |
| **Pinta-ala (m²)** | Hypoteettisen palstan pinta-ala | – |
| **Käyttötarkoitus** | Monivalintalista; suodattaa hakua käyttötarkoituksen mukaan | kaikki |
| **Veroprosentti** | Sovellettava maapohjaveroprosentti (asetuksista) | Maapohja – yleinen |
| **Hakusäde (m)** | Etäisyys karttapisteestä metreissä | 1 000 m |

### Tulospaneeli

- **Suuri sininen kenttä:** `Ka: X €` — arvioidun kiinteistöveron keskiarvo
- **Tekstikenttä:** laskentakaava, vaihteluväli min–max, referenssien lukumäärä
- **"Näytä referenssit kartalla":** korostaa nykyiset (ei poistetut) referenssit kartalla vihreänä
- **Referenssitaulukko** (sarakkeet):
  - Kiinteistötunnus
  - Pinta-ala (m²)
  - Aluehinta (€/m²)
  - Verotusarvo (€)
  - Kiint.vero (€)
  - KV tällä aluehinnalla (€) — arvio uudelle palstalle tällä referenssin aluehinnalla
- **"Poista valittu rivi":** poistaa valitun rivin taulukosta, päivittää tilastot ja karttakorostuksen

> **Vinkki:** Poista selvästi poikkeavat referenssit ennen lopullisen arvion lukemista. Jos poistat liikaa, paina uudelleen **"Laske arvio"** — se hakee koko referenssilistan uudelleen.

### Käyttöesimerkki

**Tilanne:** Kunta harkitsee uuden 3 000 m² teollisuuspalstan myyntiä.

1. Valitse **Maapohja-taso** → `Kiinteistot_Yhdistetty_vero_ja_tietokanta`
2. Klikkaa **"Valitse sijainti kartalta"** → osoita tontin suunniteltu sijainti
3. Syötä **Pinta-ala** → `3000`
4. Valitse **Käyttötarkoitus** → rastita vain `T – Teollisuus`
5. **Veroprosentti** → `Maapohja – yleinen`
6. **Hakusäde** → `1500`
7. Paina **"Laske arvio"**
8. Poista mahdolliset selvästi poikkeavat rivit → lue `Ka:`-arvo

---

## 5. Alennuskaava-laskuri

![Alennuskaava-laskuri](/img/system_images/panel_alennuskaava.svg)

### Mitä työkalu tekee

Laskee arvostamislain alennuskaavan mukaisen vaiheittaisen yksikköhinnan alenemisen ja kokonaisarvon vyöhykkeittäin. Työkalu kattaa:

- **Haja-asutusalueen alennuskaava (raja 3 000 m²)** — § 2.5.5: ensimmäiset 3 000 m² täysihinnalla, ylimenevä osa alennettuun hintaan vyöhykkeittäin
- **Haja-asutusalueen alennuskaava (raja 2 000 m², vanha tontti)** — vastaava logiikka 2 000 m² rajalla
- **Asemakaava – teollisuus/varasto** — § 2.5.7: teollisuus- ja varastokiinteistöjen vaiheistus

Tuloksena saadaan **efektiivinen yksikköhinta (€/m²)** vyöhykejaon jälkeen sekä **vyöhykekohtainen taulukko**.

> **Huomio:** Tavoitearvokerroin (× 0,75) **ei sisälly** tähän laskuriin. Käytä Maapohja – Veroarvio -työkalua täydelliseen laskentaan, jossa 0,75 on mukana.

### Syöttökentät

| Kenttä | Kuvaus | Oletus |
|---|---|---|
| **Pinta-ala** | Kiinteistön pinta-ala neliömetreinä | 2 000 m² |
| **Aluehinta** | Verottajan vahvistama yksikköhinta | 30,00 €/m² |
| **Kaavatyyppi** | Alennuskaavan tyyppi (3 vaihtoehtoa) | Haja-asutus (raja 3 000 m²) |

### Tulospaneeli

- **Kokonaisarvo (€):** vyöhykejaon mukainen summa ennen 0,75-kerrointa
- **Efektiivinen yksikköhinta:** kokonaisarvo ÷ pinta-ala
- **Vyöhyketaulukko** (sarakkeet): Vyöhyke — Pinta-ala (m²) — Osuus (%) — Yksikköhinta (€/m²) — Arvo (€)

### Kaava (haja-asutus, raja 3 000 m²)

```
V = Σ (ala_i × h_i)
```

missä `h_i` on vyöhykkeen `i` alennettu yksikköhinta arvostamislain taulukon mukaisesti.

### Käyttöesimerkki

1. Pinta-ala → `5500`; Aluehinta → `22,00`; Kaavatyyppi → **Haja-asutus (raja 3 000 m²)**
2. Paina **"Laske alennuskaava"**
3. Taulukko näyttää 2–3 vyöhykettä; efektiivinen €/m² on matalampi kuin 22,00

---

## 6. Rakentamattoman tontin vertailu

![Rakentamaton tontti -vertailu](/img/system_images/panel_rakentamaton_tontti.svg)

### Mitä työkalu tekee

Vertailee rakennetun ja rakentamattoman tontin vuotuista kiinteistöverorasitusta saman pinta-alan ja aluehinnan perusteella. Rakentamaton tontti on verotettava korotetulla veroprosentilla (`tax_rakentamaton_tontti`, oletuksena 3,00 %), joka asetetaan Asetuksissa.

### Syöttökentät

| Kenttä | Kuvaus | Oletus |
|---|---|---|
| **Pinta-ala** | Tontin pinta-ala | 1 000 m² |
| **Aluehinta** | Yksikköhinta | 25,00 €/m² |
| **Kaavatyyppi** | Asemakaava (ei alennuskaavaa) tai haja-asutus | Asemakaava |

### Tulospaneeli

2-rivinen taulukko (sarakkeet: Tilanne — Veroprosentti (%) — Verotusarvo (€) — Kiinteistövero (€/v)):

- Rivi 1 (vihreä): **Rakennettu tontti** — yleinen maapohjaveroprosentti
- Rivi 2 (punainen): **Rakentamaton tontti** — korotettu veroprosentti

Lisäksi näytetään lisäveron määrä (€/vuosi) rakentamattomuudesta.

### Kaava

```
KV_rakentamaton = A × h × 0,75 × (p_rakentamaton / 100)
```

### Käyttöesimerkki

Kunta haluaa havainnollistaa, miten paljon rakentamattomuuden korotusprosentti lisää verorasitusta 2 000 m² tontilla (aluehinta 30 €/m²). Syötä arvot ja lue ero.

---

## 7. Rakennusoikeuden vajaakäyttö

![Vajaakäyttö-laskuri](/img/system_images/panel_vajaakayto.svg)

### Mitä työkalu tekee

Simuloi KHO 2025:60 -ennakkopäätöksen mukaista verotusarvon kohtuullistamista tilanteessa, jossa kiinteistön tosiasiallinen käyttö poikkeaa merkittävästi kaavan mukaisesta käyttötarkoituksesta. Työkalu vertaa:

- **Kaavan mukaista hinnoittelua** (aluehinta × pinta-ala × 0,75)
- **Tosiasiallisen käytön mukaista hinnoittelua** (tosiasiallinen aluehinta × pinta-ala × 0,75)

Lasketaan kohtuullistettu verotusarvo ja sitä vastaava kiinteistövero (maapohjan yleinen veroprosentti asetuksista) sekä **säästö euroina per vuosi**.

### Syöttökentät

| Kenttä | Kuvaus | Oletus |
|---|---|---|
| **Aluehinta (kaava)** | Kaavan mukainen yksikköhinta | 50,00 €/m² |
| **Pinta-ala (kaava)** | Tontin pinta-ala | 2 000 m² |
| **Aluehinta (todellinen)** | Tosiasiallisen käytön mukainen yksikköhinta | 15,00 €/m² |
| **Pinta-ala (todellinen)** | Tosiasiallisesti käytettävä pinta-ala | 2 000 m² |

### Tulospaneeli

- **Suuri kenttä:** `Säästö: X €/vuosi` kohtuullistamisella
- **Teksti:** kohtuullistamisella saavutettu prosentuaalinen vähennys verotusarvosta
- **Taulukko** (2 riviä): Kaavan mukainen vs. kohtuullistettu tilanne — Verotusarvo (€) — KV (€/v)

### Kaava

```
Säästö = (V_kaava - V_todellinen) × (p_yleinen / 100)
```

missä `V = A × h × 0,75`.

### Käyttöesimerkki

Kiinteistöllä on kaavamerkintä K (kauppa, aluehinta 45 €/m²), mutta se on tosiasiallisesti varastoitu (lähialueen varaston aluehinta 12 €/m²). Syötä molemmat hinnat ja lue kohtuullistamisen tuottama säästö.

---

## 8. Rantakiinteistön arvio

![Rantakiinteistön arvio](/img/system_images/panel_rantakiinteisto.svg)

### Mitä työkalu tekee

Laskee omarantaisen tai yhteisrantaisen rantakiinteistön verotusarvon ja kiinteistöveron. Rantakiinteistöillä sovelletaan arvostamislain mukaista ranta-alennusta:

- **Omarantainen:** efektiivinen aluehinta = 100 % perusaluehinnasta
- **Yhteisrantainen:** efektiivinen aluehinta = 75 % perusaluehinnasta

Lisäksi **haja-asutusalueen** valintaruudusta voidaan soveltaa haja-asutusalueen alennuskaavaa (raja 3 000 m²) efektiivisen hinnan päälle.

### Syöttökentät

| Kenttä | Kuvaus | Oletus |
|---|---|---|
| **Pinta-ala** | Rantapalstan pinta-ala | 3 000 m² |
| **Perusaluehinta** | Verottajan vahvistama aluehinta | 40,00 €/m² |
| **Rantatyyppi** | Omarantainen / Yhteisrantainen | Omarantainen |
| **Haja-asutusalue** | Raksita, jos alennuskaava soveltuu | ei valittu |
| **Veroprosentti** | Sovellettava maapohjaveroprosentti | Maapohja – yleinen |

### Tulospaneeli

- **Suuri kenttä:** `X €` — vuotuinen kiinteistövero
- **Teksti:** efektiivinen aluehinta (€/m²), verotusarvo (€) ja käytetty veroprosentti

### Kaava

```
KV = A × h_efektiivinen × 0,75 × (p / 100)
```

missä `h_efektiivinen = h_perusaluehinta × k_ranta` (ja tarvittaessa alennuskaavakorjattu).

---

## 9. Aluehintojen jakaumaanalyysi

![Jakaumaanalyysi](/img/system_images/panel_jakaumaanalyysi.svg)

### Mitä työkalu tekee

Lukee valitulta maapohja-tasolta kaikkien kiinteistöjen aluehintakenttä (`Aluehinta__vero`) ja ryhmittelee tiedot käyttötarkoituksen mukaan. Jokaiselle käyttötarkoitusluokalle lasketaan:

- Kappalemäärä
- Minimialuehinta (€/m²)
- Keskiarvo (€/m²)
- Maksimi (€/m²)
- Keskihajonta (€/m²)

Tämä antaa nopeasti kuvan kunnan aluehintojen jakaumasta eri maankäyttöluokittain — ilman erillistä piste- tai alavalintaa.

### Syöttökentät

| Kenttä | Kuvaus |
|---|---|
| **Taso** | Maapohja-QGIS-taso |

### Käyttöesimerkki

1. Valitse **Taso** → maapohja-taso
2. Paina **"Laske jakauma"**
3. Lue taulukosta: mikä käyttötarkoitusluokka on kallein, mikä on hajonnaltaan suurin

---

## 10. Rakennus – Veroarvio (vertaileva)

![Rakennus Veroarvio -käyttöliittymä](/img/system_images/panel_rakennus_veroarvio.svg)

### Mitä työkalu tekee

Hakee lähialueen olemassa olevat rakennukset ja laskee niiden toteutuneen **vero per kerrosneliömetri** -suhteen. Tätä vertailusuhdetta sovelletaan uuden rakennuksen arviointiin:

```
KV-arvio = (Vero_ref / Kerrosala_ref) × Kerrosala_uusi
```

Rakennukset, joilta puuttuu verotusarvo tai kiinteistövero, **näkyvät silti taulukossa** (`–`-arvoilla) mutta eivät vaikuta statistiikkaan.

### Syöttökentät

| Kenttä | Kuvaus | Oletus |
|---|---|---|
| **Rakennukset-taso** | QGIS-rakennustaso | – |
| **Valitse sijainti kartalta** | Karttapistepoiminta | – |
| **Kerrosala (m²)** | Uuden rakennuksen kerrosala | – |
| **Rakennustyyppi** | Monivalintalista VRK-koodeista | kaikki |
| **Veroprosentti** | Sovellettava rakennusveroprosentti | Rakennukset – yleinen |
| **Hakusäde (m)** | Etäisyys karttapisteestä | 500 m |

### Tulospaneeli

- **Suuri kenttä:** `Ka: X €`
- **Teksti:** vero/m²-ka × kerrosala = arvio, vaihteluväli, referenssien lukumäärä
- **"Näytä referenssit kartalla":** korostaa aktiiviset referenssirakennukset kartalla
- **Referenssitaulukko** (sarakkeet):
  - Kiinteistötunnus
  - Tyyppi (VRK-koodi)
  - Kerrosala (m²)
  - Verotusarvo (€)
  - Vero (€)
  - Vero/m² (€)
  - KV tällä aluehinnalla (€) — arvio uudelle rakennukselle tämän referenssin vero/m²-suhteella
- **"Poista valittu rivi":** poistaa rivin, päivittää tilastot ja karttakorostuksen

### Käyttöesimerkki

**Tilanne:** Uusi 180 m² omakotitalo valmistumassa asuinalueelle.

1. **Rakennukset-taso** → `Rakennukset_Yhdistetty_vero_ja_tietokanta`
2. Klikkaa **"Valitse sijainti kartalta"** → osoita tontti
3. **Kerrosala** → `180`
4. **Rakennustyyppi** → valitse vain `039 – Omakotitalo`
5. **Veroprosentti** → `Vakituinen asunto`
6. Paina **"Laske arvio"** → lue `Ka:`-arvo

---

## 11. Rakennus – Laskenta alusta

![Rakennus – Laskenta alusta](/img/system_images/panel_rakennus_alusta.svg)

### Mitä työkalu tekee

Laskee rakennuksen verotusarvon täydellä laskentakaavalla jälleenhankinta-arvosta (JHA) ja ikäalennuksesta. Työkalu soveltuu, kun rakennuksen JHA tiedetään tai arvataan ja halutaan selvittää vuotuinen kiinteistövero:

```
Verotusarvo = max(JHA × (1 - α),  0,20 × JHA)
```

missä `α` on netto-ikäalennus (%) ja lattia on 20 % JHA:sta.

```
KV = Verotusarvo × (p / 100)
```

### Syöttökentät

| Kenttä | Kuvaus | Oletus |
|---|---|---|
| **JHA** | Jälleenhankinta-arvo euroina | 200 000 € |
| **Rakennustyyppi** | VRK-tyyppinimike (käytetään ikäalennusryhmän määrittämiseen) | – |
| **Materiaali** | `puu` tai `kivi` | – |
| **Valmistumisvuosi** | Rakennuksen valmistumisvuosi | 1985 |
| **Veroprosentti** | Sovellettava veroprosentti | – |

### Tulospaneeli

- **Suuri kenttä:** `X €` — vuotuinen kiinteistövero
- **Teksti:** JHA, ikäalennus (%), verotusarvo, ikäalennusryhmä

### Käyttöesimerkki

1. JHA → `350000`; Rakennustyyppi → `Toimistotalo`; Materiaali → `kivi`; Vuosi → `1992`
2. Veroprosentti → `Rakennukset – yleinen`
3. Paina **"Laske verotusarvo"** → lue verotusarvo ja kiinteistövero

---

## 12. Ikäalennus & Perusparannuslaskin

![Ikäalennus & Perusparannus](/img/system_images/panel_ikaalennus.svg)

### Mitä työkalu tekee

Laskee rakennuksen netto-ikäalennuksen arvostamislain § 30 mukaisesti: brutto-ikäalennus rakennustyyppiryhmän ja materiaalin perusteella, johon sovelletaan perusparannusvähennykset.

**Ikäalennusryhmät:**

| Ryhmä | Rakennukset | Puu (%/v) | Kivi (%/v) | Katto (max) |
|---|---|---|---|---|
| 1 | Asunto, toimisto, koulu, kirkko, stadion, vankila, paloasema (toimistosiipi) | 1,25 | 1,00 | 70 % |
| 2 | Myymälä, varasto, tehdas, sairaala, terveyskeskus, paloasema (kalustosiipi), terminaalit, uimahalli, jäähalli | 5,00 | 4,00 | 80 % |
| 3 | Rakennelmat | 10 | 10 | 80 % |

### Syöttökentät

| Kenttä | Kuvaus | Oletus |
|---|---|---|
| **Rakennustyyppi** | Tyyppi (ryhmä määräytyy tästä) | – |
| **Materiaali** | `puu` tai `kivi` | – |
| **Valmistumisvuosi** | Rakennusvuosi | 1975 |

**Perusparannukset** (9 raksitettavaa kohtaa):

| Perusparannus | Vähennys |
|---|---|
| Ikkunat uusittu | −6 pp |
| Vesijohto/viemärilaitteet uusittu | −5 pp |
| Sähkölaitteet uusittu | −5 pp |
| Ilmastointi asennettu | −5 pp |
| Lämmitysjärjestelmä uusittu | −5 pp |
| Vesikate uusittu | −3 pp |
| Ovet uusittu | −1 pp |
| Ulkoseinien pinnoitteet uusittu | −2 pp |
| Ulkopuolinen lisäeristys | −8 pp |

### Laskentakaava

```
α_netto = max(0, min(α_katto, α_brutto - Σ Δ_i))
```

missä `α_brutto = ikä × r` (`r` = alennusprosentti per vuosi ryhmän mukaan) ja `Δ_i` on raksittujen perusparannusten vähennykset prosenttipisteinä.

### Tulospaneeli

- **Suuri kenttä:** `Netto-ikäalennus X %`
- **Teksti:** ikäalennusryhmä, ikä vuosina, kattovaikutus
- **Erittelytaulukko** (8 riviä): ikäalennusryhmä, materiaali, ikä, brutto-ikäalennus, perusparannus yhteensä, netto (ennen kattoa), katto, kattovaikutus

### Käyttöesimerkki

Omakotitalo, kivi, valmistunut 1965. Ikkunat ja lämmitysjärjestelmä on uusittu.
1. Rakennustyyppi → `Omakotitalo`; Materiaali → `kivi`; Vuosi → `1965`
2. Rastita: **Ikkunat uusittu** ja **Lämmitysjärjestelmä uusittu**
3. Paina **"Laske ikäalennus"** → lue netto-ikäalennus

---

## 13. Vero per m² rakennustyypeittäin

![Vero per m²](/img/system_images/panel_vero_per_m2.svg)

### Mitä työkalu tekee

Lukee kaikki rakennukset valitulta tasolta ja laskee **ryhmä kohtaisen vero per kerrosneliömetri** -tunnusluvun. Poikkeama kokonaisaineiston keskiarvosta värikoodataan:

| Väri | Poikkeama ka:sta |
|---|---|
| 🟢 Vihreä | ±30 % |
| 🟡 Keltainen | ±30–50 % |
| 🔴 Punainen | yli 50 % |

### Syöttökentät

| Kenttä | Kuvaus |
|---|---|
| **Taso** | Rakennukset-QGIS-taso |

### Tulostaulukko (sarakkeet)

| Sarake | Selite |
|---|---|
| Rakennustyyppi | VRK-koodi ja nimi |
| Kpl | Rakennusten lukumäärä ryhmässä |
| Ka pinta-ala (m²) | Kerrosalan keskiarvo ryhmässä |
| Ka vero (€) | Vuotuisen kiinteistöveron keskiarvo |
| Vero/m² (€) | Ka vero ÷ ka pinta-ala |
| Poikkeama ka:sta (%) | Poikkeama koko aineiston vero/m²-keskiarvosta |

### Käyttöesimerkki

Ajetaan koko rakennusaineistolla. Punainen rivi paljastaa rakennustyypin, jonka vero/m² on yli 50 % poikkeava — tämä voi viitata kirjausvirheeseen tai erityiseen laskentaperusteeseen, joka kannattaa tarkistaa.

---

## 14. Veropohja-yhteenveto

![Veropohja-yhteenveto](/img/system_images/panel_yhteenveto.svg)

### Mitä työkalu tekee

Laskee valitun kuntatietokannan **koko kiinteistöveropohjan** summaamalla maapohja- ja rakennusverot yhteen. Tulos jaetaan kolmeen kokonaislaatikkoon ja käyttötarkoituksittaiseen erittelytaulukkoon.

### Syöttökentät

| Kenttä | Kuvaus |
|---|---|
| **Maapohja-taso** | Maapohja-QGIS-taso (kaikki kiinteistöt) |
| **Rakennukset-taso** | Rakennukset-QGIS-taso (kaikki rakennukset) |

### Tulospaneeli

**Kolme kokonaislaatikkoa:**

- **Maapohja yhteensä (€)** — kaikki maapohjan kiinteistöverot yhteenlaskettuna
- **Rakennukset yhteensä (€)** — kaikki rakennusten kiinteistöverot yhteenlaskettuna
- **Yhteensä kaikki (€)** — koko kunnan kiinteistöveropohja

**Erittelytaulukko:** maapohja jaoteltuna käyttötarkoituksittain (Käyttötarkoitus — Kpl kiinteistöjä — Vero yhteensä (€)).

### Käyttöesimerkki

1. **Maapohja-taso** ja **Rakennukset-taso** → valitse oikeat tasot
2. Paina **"Laske yhteenveto"**
3. Lue kokonaistulos ja erittely — esim. kuinka suuri osuus kiinteistöveropohjasta koostuu asuinkäyttöön merkityistä kiinteistöistä

---

## 15. Ohje ja tietoa laskureista

Tämä pudotusvalikosta löytyvä sivu on ikkunan sisäinen pikaohje. Se sisältää:

- **Vastuuvapauslauseke** keltaisella taustalla
- **Maapohja-työkalutaulukko** (työkalu / mitä laskee / laskentaperuste)
- **Rakennukset-työkalutaulukko**
- **Ikäalennusryhmät** (ryhmä / rakennukset / puu / kivi / max)
- **Lähteet** (arvostamislaki, VvMA, KHO-päätökset)

Tämä sivu on tarkoitettu nopeaksi muistilistaksi käytön aikana.

---

## 16. Karttakorostus

Maapohja – Veroarvio- ja Rakennus – Veroarvio -työkaluissa on **"Näytä referenssit kartalla"** -painike:

![Näytä korostukset -valintaruutu](/img/system_images/checkbox_nayta_korostukset.svg)

- Korostus aktivoituu klikkaamalla painiketta haun jälkeen
- Korostus näyttää **vain aktiivisessa referenssilistassa** olevat kohteet vihreänä
- **Poistetut rivit eivät näy** korostuksessa — myöskään edellisestä klikkauksen jälkeen poistetuille riveille korostus ei palaa ennen seuraavaa "Näytä"-klikkausta
- Korostus poistetaan, kun ikkuna suljetaan tai uusi haku ajetaan

Tämä mahdollistaa nopean visuaalisen tarkistuksen: ovatko referenssikohteet maantieteellisesti mielekkäät?

---

## 17. FAQ

**K: Mitä tapahtuu, jos hakusäde ei löydä yhtään referenssiä?**  
V: Tulos näyttää `–  €` ja teksti kertoo, ettei kohteita löytynyt. Suurenna hakusädettä tai poista käyttötarkoitus-/rakennustyyppisuodatus.

**K: Voinko verrata eri veroprosentteja rinnakkain?**  
V: Kyllä. Aja laskenta ensin yhdellä prosentilla, kirjaa tulos, vaihda prosentti ja aja uudelleen.

**K: Miten poistetut rivit saa takaisin?**  
V: Paina uudelleen **"Laske arvio"** — se hakee koko referenssilistan alusta.

**K: Alennuskaava-laskuri ei näytä 0,75-kerrointa — onko tulos oikein?**  
V: Kyllä. Alennuskaava-laskuri näyttää **verotusarvon ennen 0,75-kerrointa**. Maapohja – Veroarvio -työkalu sisällyttää kertoimen automaattisesti. Käytä Maapohja – Veroarvio täydelliseen laskentaan.

**K: Voiko ikäalennus ylittää 100 %?**  
V: Ei. Ikäalennus on rajoitettu ikäalennusryhmän kattoon (ryhmä 1: 70 %, ryhmä 2–3: 80 %).

**K: Mistä löydän viralliset aluehintakartat?**  
V: Verohallinnon [rakennusmaan arvoaluekartat](https://www.vero.fi/syventavat-vero-ohjeet/ohje-hakusivu/47871/rakennusmaan-arvoaluekartat/) ja aluehintakartat. Kuntakohtaiset tiedot löytyvät verottajan julkaisemasta aluehintadatasta.

**K: Miksi joillain rakennuksilla vero/m² näkyy `–`?**  
V: Rakennukselta puuttuu vero tai kerrosala verottajan rekisterissä. Tieto on mukana taulukossa informatiivisessa tarkoituksessa, mutta se ei vaikuta tilastoihin.

---

## 18. Viitteet

| Lähde | Kuvaus |
|---|---|
| **Laki varojen arvostamisesta verotuksessa 1142/2005** | Maapohjan ja rakennusten verotusarvon laskenta, §§ 28–31; alennuskaavat §§ 2.5.5, 2.5.7 |
| **VvMA 1073/2025** — Valtiovarainministeriön asetus rakennusten jälleenhankinta-arvon perusteista | JHA-taulukot ja ikäalennusryhmät |
| **VH/5812/00.01.00/2025** — Verohallinnon päätös rakennusmaan verotusarvon laskentaperusteista | Aluehintakertoimet ja laskentaohjeet |
| **KHO 2025:60** | Rakennusoikeuden vajaakäyttö — verotusarvon kohtuullistaminen |
| **KHO 2025:38** | Sairaala- ja terveyskeskusrakennusten ikäalennus (ryhmä 2) |
| **KHO 2023:94** | Paloasemien ikäalennusryhmittely (toimisto-/kalustosiiven jako) |

---

*Ohje päivitetty: 12.5.2026 | KiinteistöveroApuri-liitännäinen*
