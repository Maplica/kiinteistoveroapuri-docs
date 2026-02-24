---
sidebar_position: 3
---

# Vuosivertailu

Avautuu kun: Napsautat valikosta [Vertailu → Vuosivertailu](./01_paaikkuna.md#vertailu-pudotusvalikko)  
Vuosivertailuikkuna helpottaa muutosten tarkistuksessa ja seurannassa koostamalla tietoa tehokkaaseen muotoon.

## Korjaus tarkistus -välilehti
- Lataa istuntotiedoston "Lataa sessio…" -painikkeella
- Näyttää ladatut kohteet taulukossa nykyisen kategorian mukaan
- "Vaihda kategoria" -painike vaihtaa Rakennus/Maapohja välillä
- "Tarkista tiedot" -painike suorittaa geometriapohjaisen validoinnin (1 m säde)
- Validointi käyttää ryhmärajoitteita: Rakennus → Rakennukset/Rakennuksen Osat, Maapohja → Määrä-alat
- Näyttää kunkin kohteen tilan (OK/Check), nykyisen tason ja huomiot
- Rivit värjätään: vihreä (OK), punainen (Check), valkoinen (ei validoitu)
- Kaksoisnapsautus avaa vain luku -näkymän kaikista tiedoista + Candidate Data -välilehden

## Tilastot & kaaviot -välilehti
- Näyttää OK/Check-määrät kategoriaa kohden (Rakennus, Maapohja)
- Näyttää Kiinteistövero-summia:
  - Kiinteistövero lisä: summa siirroista puuttuvat→yhdistetty
  - Kiinteistövero erot: summa päivitetyistä arvoista joissa ero
- Sisältää selityksen laskentalogiikasta

## Info-välilehti
- Näyttää ladatun istunnon metatiedot (otsikko, polku, muokkausaika)
- Näyttää nykyisen projektin metatiedot
- Näyttää yhteenvedon (yhteensä kohteet, löydetty, ei löydetty)
- Sisältää selitykset kaikista Huomio-viesteistä

Tämä valintaikkuna toimii itsenäisesti eikä vaikuta pääikkunan oikeaan taulukkoon. Sitä käytetään aiemmin tallennettujen istuntojen tarkasteluun ja validointiin päivitettyä projektiaineistoa vastaan.