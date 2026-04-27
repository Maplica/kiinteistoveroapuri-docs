---
sidebar_position: 2
---

# Prosessointiasetukset

Avautuu kun: Napsautat valikosta [Asetukset → Asetukset](./01_paaikkuna.md#asetukset-pudotusvalikko)  
Asetukset on jaettu kategorioihin. Kunkin kategorian asetuksiin pääset käsiksi napauttamalla kategoriaa vasemmalla listassa.

OK-painike:
- Tallentaa asetukset
- Sulkee valintaikkunan
- *Sama toiminta kuin Käytä + Sulku*

Peruuta-painike:
- Sulkee valintaikkunan tallentamatta muutoksia
- Palauttaa kaikki asetukset edellisiin arvoihin

Käytä-painike:
- Tallentaa asetukset
- Pitää ikkunan auki
- Näyttää "Tallennettu"-viestin merkkinä onnistumisesta
- Muutokset otetaan käyttöön välittömästi

## Yleiset-sivu

![kuva käyttöliittymästä](/img/asetusikkuna/asetukset_yleiset.png)

Valintaruutu: *Muista pääikkunan koko*

Kun valittu, ohjelma tallentaa ikkunan koon ja palauttaa sen seuraavalla käynnistyskerralla. Kun ei valittu, käytetään aina oletuskokoa.

## Tietokanta-sivu

![kuva käyttöliittymästä](/img/asetusikkuna/asetukset_tietokanta.png)

Kolme ryhmää: Kiinteistöt, Määrä-ala, Rakennukset. Jokaisessa ryhmässä pudotusvalikot avainkenttien määrittämiseen:
- **Kiinteistöt:** Kiinteistötunnus (Palstat)
- **Määrä-ala:** Määräalatunnus
- **Rakennukset:** Kiinteistötunnus, PRT, Rakennuksen numero

Pudotusvalikot täytetään projektin tasojen kentillä. Täällä määrität, mitkä tietokantakentät vastaavat avaintietoja — tärkeää erityisesti kun käytetään tasoja joilla ei ole `__vero`/`__kunta`-päätteitä.

## Taulukko-sivu

![kuva käyttöliittymästä](/img/asetusikkuna/asetukset_taulukko.png)

Valintaruutu: *Sovita sarakkeiden leveys automaattisesti aineiston latauksen jälkeen*
- Kun valittu (oletus): sarakkeet sovitetaan sisällön mukaan
- Kun ei valittu: käytetään oletusleveyttä

Ryhmälaatikko: *Lisättyjen kohteiden taulukon sarakkeet*
- "Verotietojen kentät (oletus)" — näytetään vain `__vero`/`__added`-kentät
- "Tietokannan valitut kentät" — näytetään vain `__kunta`-kentät
- "Molemmat (vero ensin, sitten tietokanta)" — näytetään molemmat

## Raportit-sivu

![kuva käyttöliittymästä](/img/asetusikkuna/asetukset_raportit.png)

Tekstikenttä: *Oletuskansio raporteille*
Määrittelee oletussijainnin raporttitiedostojen tallennukseen.

## Lisäasetukset-sivu

Tällä hetkellä lisäasetuksia ei ole. Kategoria on varattu tulevaisuuden asetuksille.
