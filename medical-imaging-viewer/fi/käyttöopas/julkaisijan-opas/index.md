<h1>Julkaisijan opas</h1>

* TOC
{:toc}

## Edellytykset kuvantamisten katseluun ohjelmalla

Tutkimuksia näyttääkseen katselinohjelma tarvitsee tietoonsa osoitteet, joista kuvantamistiedostot löytyvät. Nämä osoitteet ovat yleensä www-osoitteita, mutta ohjelma pystyy avaamaan tiestoja tiedostojärjestelmäosoitteista käyttäjän kovalevyltä, jos tiedostot on joko erikseen avattu tai suoraan raahattu ojelmaan. Yksittäiset tiedostot aukeavat pelkän osoitteen avulla, mutta monimutkaisemmat tutkimukset (kuten kuvapakat) ja tutkimuskokonaisuudet vaativat tietyllä tavalla organisoidun tiedostojärjestelmärakenteen.

### Tiedostojärjestelmärakenne

Jos ohjelmalla avataan enemmän kuin yksittäinen tiedosto, täytyy tiedostot järjestellä oikein, jotta ohjelma pystyy tulkitsemaan tutkimuksen rakenteen. Nyrkkisääntönä on, että **jokaista yksittäistä tutkimusta, sekvenssiä ja projektiota varten vaaditaan oma kansio**.
```
📁 Käynti #1
   📁 Tutkimus #1
      - kuvantamistiedostot
   📁 Tutkimus #2
      - kuvantamistiedostot
📁 Käynti #2 (kansio)
   📁 Tutkimus #3
      - tutkimustiedostot
```
Teidostojärjestelmän huolellinen suunnittelu on tärkeää! Jos yllä kuvattuun tutkimuskokonaisuuteen lisätään siihen kuulumattomia elementtejä, eivät tiedostot lataudu oikein:
- Jos jompaan kumpaan käyntikansioon lisätään ylimääräisä tiedostoja, jätetään ne huomioimatta.
- Jos jomman kumman tutkimuskansion sisälle lisätään ylimääräinen kansio, jätetään koko se tutkimuskansio huomioimatta.

Yksittäisillä sisäkkäisillä kansioilla ei ole väliä, ohjelma "romahduttaa" yksittäiset sisäkkäiset kansiot yhteen ja huomioi vain viimeisen kansion. Jos esimerkiksi edellä mainittu tutkimuskokonaisuus olisi useamman _yksittäisen sisäkkäisen_ kansion sisällä, ladattaisiin se samalla tavalla kuin edellä:
```
📁 Jokukansio 1
   📁 Jokukansio 2
      📁 Jokukansio 3
         📁 Käynti #1
            📁 Tutkimus #1 (kansio)
                - ...
         📁 Käynti #2 (kansio)
             - ...
```
Sama pätee sisäkansioihin, eli tutkimuskokonaisuuden lataamiseen ei vaikuta jos yksittäisiä tutkimuksia on sisäkkäisten kansioiden alla:
```
📁 Käynti #1
   📁 Jokukansio 1
      📁 Jokukansio 2
         📁 Jokukansio 3
            📁 Tutkimus #1
               - kuvantamistiedostot
```

#### Havainnollistavia esimerkkejä

Keuhkokuva, jossa AP- ja sivuprojektiot
```
📁 Thorax-rtg
   📁 Thorax ap-projektio
      - dicomkuvatiedosto
   📁 Thorax sivuprojektio
      - dicomkuvatiedosto
```
Vartalon CT-kuvaus, jossa kolme projektiota
```
📁 Vartalon CT
   📁 Vartalon CT aksiaali
      - dicomtiedosto001
      - dicomtiedosto002
      - ...
   📁 Vartalon CT sagittaali
      - dicomtiedosto001
      - dicomtiedosto002
      - ...
   📁 Vartalon CT koronaali
      - dicomtiedosto001
      - dicomtiedosto002
      - ...
```
Nämä tutkimukset ohjelma tulkitsisi siten, että pudotusvalikon käynnin nimeksi tulisi ylimmän hakemiston nimi (joko `Thorax-rtg` tai `Vartalon CT`), ja sivupalkissa näkyvien tutkimusten nimiksi tulisi projektiot sisältävien kansioiden nimet (esim. `Thorax ap-projektio`, `Vartalon CT aksiaali` jne.). Itse kuvatiedostojen nimet eivät tulisi ohjelmassa lainkaan näkyviin. Ohjelma lähtökohtaisesti pyrkii käyttämään kansioiden nimiä käyntien ja tutkimusten niminä, mutta jos ladataan vain yksittäinen tiedosto, niin silloin tiedoston nimestä tulee tutkimuksen nimi ja pudotusvalikkoon käynnin nimeksi tulee geneerinen Käynti `Käynti #1`.

Jos käynnillä on useampia eri modaliteetin tutkimuksia, ei näitä tarvitse jaotella omiin hakemistoihinsa; ohjelma tunnistaa modaliteetit automaattisesti:
```
📁 Päivystyskäynti
   📁 Lepo-EKG (kansio)
      - dicomekgtiedosto
   📁 Natiivi-thorax ap (kansio)
      - dicomkuvatiedosto
   📁 Natiivi-thorax sivu (kansio)
      - dicomkuvatiedosto
   📁 Pään natiivi-CT (kansio)
      - dicomkuvatiedosto001
      - dicomkuvatiedosto002
      - ...
```
Jos samaan tutkimuskokonaisuuteen haluttaisiin liittää vielä pudotusvalikosta valittava seurantakäynti, lisättäisiin se vain omaksi ylimmän tason kansiokseen:
```
📁 Päivystyskäynti
   - ...
📁 Seurantakäynti 1kk
   📁 Kontrolli-EKG
      - dicomekgtiedosto
   📁 Kontrolli-thorax ap
      - dicomkuvatiedosto
   📁 Kontrolli-thorax sivu
      - dicomkuvatiedosto
```

## Tutkimusten lataaminen

Yksikertaisin tapa tutkimusten lataamiseen ohjelmaan, on raahata ne kovalevyltä (joko yksittäin tai edellä kuvattuna tiedostojärjestelmänä) ohjelma vasempaan sivupakkiin. Verkosta ladattaessa ohjelmalle on ilmoitettava tutkimuskokonaisuuden tiesotojärjestelmärakenne, sekä mistä osoitteesta jokainen yksittäinen kuvatiedosto löytyy. Tällainen _konfiguraatiotiedosto_ on mahdollista kirjoittaa myös käsin, mutta se voi olla varsin työlästä erityisesti kuvapakkoja sisältävien tutkimusten tapauksessa. Siksi ohjelmalle on laadittu ja edelleen kehitetään muissa verkkoympäristöissä käytettäviä lisäosia, jotka helpottavat tätä prosessia. Näille lisäosille on olemassa omat ohjeensa:
- Moodlen ATTO-tekstinkäsittijän lisäsosa
