---
sidebar_position: 3
---

# Parhaat käytännöt

Tässä osiossa käydään läpi prosessoinnin parhaat käytännöt tietojen valmisteluun, prosessoinnin aikaiseen työskentelyyn ja tulosten tarkistamiseen.

---

## 1. Tietojen valmistelu

### Ennen ensimmäistä prosessointia:

**🔍 Validoi lähtödata:**
- Tarkista että geometriat ovat valideja (QGIS → Vector → Geometry Tools → Check Validity)
- Poista tyhjät rivit Verottajan CSV-tiedostosta
- Tarkista että pakolliset sarakkeet eivät sisällä tyhjiä arvoja

<!-- PLACEHOLDER: Kuvakaappaus QGIS:n Check Validity -työkalusta -->

---

## 2. Prosessoinnin aikana

**⏱️ Varaa riittävästi aikaa:**
- Älä aloita prosessointia kiireessä
- Pidä tietokone päällä koko prosessoinnin ajan

**💾 Tallenna välivaiheet:**
- Tallenna projekti ennen prosessointia
- Tallenna projekti prosessoinnin jälkeen
- Älä poista vanhoja tulostiedostoja heti (nimeä uudet eri nimellä)

---

## 3. Tulosten tarkistus

**Heti prosessoinnin jälkeen:**

1. **Tarkista että kaikki tulostiedostot luotiin:**
   - GeoPackage-tiedostot (10 tasoa)
   - Excel-raportit kohteista jotka eivät yhdisty (2 tiedostoa)
   - Tilastot (2 tasoa)
   - Alkuperäiset aineistot (4 tasoa)

2. **Tarkista puuttuvat rakennukset -raportti:**
   - Kuinka monta rakennusta ei löytynyt?
   - Onko tämä odotettu määrä?
   - Tutki miksi rakennukset puuttuvat

<!-- PLACEHOLDER: Kuvakaappaus esimerkkitulostiedostoista kansiossa tai QGIS:ssä avattuna -->

**🚩 Punaiset liput (merkkejä ongelmista):**
- Tyhjät tulostiedostot
- Huomattavan vähän rivejä tulosteissa
- Kaikki rakennukset "puuttuvat"
- Geometriat väärässä paikassa kartalla
- NULL-arvoja paljon sarakkeissa jotka pitäisi olla täytetty

---

## 4. Datan hallinta

**📁 Järjestä tiedostot loogisesti:**

```
Esim.

C:\Kiinteistovero\
├── 2025\
│   ├── 01_Helmikuu\
│   │   ├── Lahtotiedot\
│   │   │   ├── Kunnan_data\
│   │   │   └── Verottaja_data\
│   │   └── Tulokset\
│   └── 02_Maaliskuu\
│       └── ...
└── Arkisto\
    └── 2024\
```

**🔒 Tietoturva ja varmuuskopiointi:**
- Henkilötietoja sisältävät tiedostot: säilytä suojatussa verkkolevyssä
- Käytä turvallista tiedostonsiirtoa (ei sähköposti) kun lähetät aineistoja
- Varmuuskopioi tulostiedostot säännöllisesti
