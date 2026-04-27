---
sidebar_position: 3
---

# Vuosivertailu

Avautuu kun: Napsautat valikosta [Vertailu → Vuosivertailu](./01_paaikkuna.md#vertailu-pudotusvalikko)

Vuosivertailu on tarkoitettu tilanteisiin, joissa haluat verrata aiemmin tehtyä selvitystyötä päivitettyyn aineistoon. Työkalu lataa tallennetun istuntotiedoston ja tarkistaa, löytyvätkö siihen kuuluvat rakennukset tai kiinteistöt edelleen nykyisestä projektista — ja jos löytyvät, mitä tiedoissa on muuttunut.

## Työkulku lyhyesti

1. Avaa vuosivertailu valikosta **Vertailu → Vuosivertailu**
2. Lataa aikaisempi istuntotiedosto **“Lataa sessio…”** -painikkeella
3. Tarkista kohteiden tila **“Tarkista tiedot”** -painikkeella
4. Katso tilastot **Tilastot & kaaviot** -välilehdeltä
5. Kaksoisnapsauta yksittäistä kohde-riviä nähdäksesi että tiedot ovat muuttuneet

Ikkuna toimii itsenäisesti eikä muuta pääikkunan tietoja.

![Vuosivertailu-ikkuna](/img/system_images/dialog_vuosivertailu.svg)

## Korjaus tarkistus -välilehti

- Lataa istuntotiedoston **“Lataa sessio…”** -painikkeella
- Näyttää ladatut kohteet taulukossa nykyisen kategorian mukaan
- **“Vaihda kategoria”** -painike vaihtaa Rakennus/Maapohja välillä
- **"Tarkista tiedot"** -painike ![Tarkista tiedot](/img/system_images/btn_validoi.svg) suorittaa validoinnin
- Validointi käyttää ryhmärajoitteita: Rakennus → Rakennukset/Rakennuksen Osat, Maapohja → Määrä-alat
- Näyttää kunkin kohteen tilan (OK/Check), nykyisen tason ja huomiot
- Rivit värjätään: vihreä (OK), punainen (Check), valkoinen (ei validoitu)
- Kaksoisnapsautus avaa vain luku -näkymän kaikista tiedoista + Candidate Data -välilehden

## Tilastot & kaaviot -välilehti

- Näyttää OK/Check-määrät kategoriaa kohden (Rakennus, Maapohja)
- Näyttää kiinteistövero-summia:
  - **Kiinteistövero lisä:** summa siirroista (puuttuvat → yhdistetty)
  - **Kiinteistövero erot:** summa päivitetyistä arvoista, joissa on muutos
- Sisältää selityksen laskentalogiikasta

## Info-välilehti

- Näyttää ladatun istunnon metatiedot (otsikko, polku, muokkausaika)
- Näyttää nykyisen projektin metatiedot
- Näyttää yhteenvedon (kohteet yhteensä, löydetty, ei löydetty)
- Sisältää selitykset kaikista Huomio-viesteistä