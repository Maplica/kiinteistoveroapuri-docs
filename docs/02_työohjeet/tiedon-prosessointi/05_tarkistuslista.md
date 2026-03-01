---
sidebar_position: 5
---

# Tarkistuslista

Käytä tätä listaa pikaoppaana ennen prosessoinnin aloittamista. Varmista että jokainen kohta on kunnossa.

---

## ✅ Lähtötiedot

- [ ] Kaikki 4 shapefile-tiedostoa (kiinteistöt, määräalat, rakennukset, alueet) löytyvät
- [ ] Jokainen shapefile sisältää .shp, .dbf, .prj, .shx -tiedostot
- [ ] Shapefile-tiedostot avautuvat QGIS:ssä ilman virheitä
- [ ] Geometriat näkyvät oikein kartalla
- [ ] Attribuuttitaulut avautuvat ja sisältävät dataa
- [ ] Verottajan tiedot löytyvät ja avautuvat

---

## ✅ Sarakkeet ja sisältö

- [ ] Tiedän tarkat sarakkeiden nimet (dokumentoin ne)
- [ ] Pakolliset sarakkeet sisältävät dataa (eivät tyhjiä)
- [ ] Käyttötarkoituskoodit ovat valideja

:::info Muistilista: Pakolliset sarakkeet
**Kiinteistöt:** `Kiinteistötunnus`, `Palstan pinta-ala`, `Kaavan käyttötarkoitus`, `Vesialueen pinta-ala`  
**Rakennukset:** `PRT`, `Kiinteistötunnus`, `Rakennuksen numero`, `Kokonaisala`, `Kerrosala`, `Tilavuus`  
**Määräalat:** `Määräalatunnus`  
**Aluejaot:** `Alueen tunniste`  

Katso tarkemmat kuvaukset: [Esivalmistelut → Vaaditut sarakkeet](./esivalmistelut.md#vaaditut-sarakkeet-tasoittain)
:::

---

## ✅ Koordinaattijärjestelmät

- [ ] Tiedän kaikkien shapefile-tiedostojen koordinaattijärjestelmät ja ne ovat samat kaikilla
- [ ] Valitsin oikean CRS:n tulosteille

---

## ✅ Työympäristö

- [ ] Riittävästi levytilaa tulosteille (arvioi ~2x lähtödatan koko)
- [ ] Tietokone ei sammu kesken prosessoinnin (virransäästöasetukset)
- [ ] QGIS on käynnissä ja projekti tallennettu

---

## ✅ Tulostiedostot

- [ ] Määrittelin tulostiedostojen sijainnit
- [ ] Minulla on kirjoitusoikeudet kyseisiin hakemistoihin
- [ ] Tiedän mitä teen HETU-tiedoilla (mukaan vai pois)
- [ ] Tuloshakemistossa on tilaa

---

## ✅ Prosessoinnin jälkeen

- [ ] Kaikki tulostiedostot luotiin (GeoPackage, Excel, Tilastot)
- [ ] Puuttuvien rakennusten määrä on odotettu
- [ ] Geometriat näkyvät oikein kartalla
- [ ] Ei epätavallisen paljon NULL-arvoja
- [ ] Projekti tallennettu prosessoinnin jälkeen

---

:::tip Kaikki kunnossa?
Jos kaikki kohdat on tarkistettu, olet valmis aloittamaan prosessoinnin! Siirry [Prosessoinnin käynnistys](./01_kaynnistys.md) -sivulle.
:::
