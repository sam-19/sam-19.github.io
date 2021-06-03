<h1>Käyttäjän opas - radiologia</h1>

* TOC
{:toc}

## 1. Yleistä

Radiologian moduulilla on mahdollista tarkastella DICOM-muotoisia radiologisia kuvantamistutkimuksia. Tällä hetkellä yksittäisten natiivikuvien ja CT-kuvapakkojen tarkastelu toimii kohtalaisen hyvin. Myös magneettikuvien ja ultraäänitallenteiden katselu on  mahdollista, mutta niistä puuttuu modaliteettikohtaisia ominaisuuksia.

## 2. Työkalurivi

![toolbar](toolbar.png)

Työkalurivin painikkeet eivät ole käytettävissä, ennen kuin jokin kuvantamistutkimus on avattu tarkasteltavaksi. Riippuen kontekstista, kaikkia painikkeita ei välttämättä ole käytettävissä. Työkalupainikkeet on jaettu toiminnallisesti ryhmiin, ja vain yksi työkalu per ryhmä voi olla samalla kertaa aktiivisena; työkalun aktivointi kytkee automaattisesti muut saman ryhmän työkalut pois päältä. Aktiivinen työkalu toimii aina hiiren vasenta nappia painamalla ja hiirtä liikuttamalla nappi pohjassa. Työkalurivillä on myös kolme painikeryhmää, jotka klikattaessa avaavat nkyville ryhmään kuuluvat työkalupainikkeet.

Työkalupainikkeet vasemmalta oikealle lueteltuna:
- ![medigi-tool-pan](uploads/dfe08ba40eac2357dc8ba6a0c6078986/medigi-tool-pan.png) _Liikuttelutyökalu:_ Liikuttaa kuvaa pysty- ja vaakasuunnassa.
- ![medigi-tool-zoom](uploads/177fa38b49ba7e91767ada364534ec05/medigi-tool-zoom.png) _Suurennuslasi:_ Liikuttaa kuvaa syvyyssuunnassa, ts. lähentää ja loitontaa sitä.
- ![medigi-tool-scroll](uploads/f14ff214bbbd541c98d0d4d150fd6de8/medigi-tool-scroll.png) _Pakan selaus:_ Selaa kuvapakkaa, ts. näyttää järjestyksessä pakan seuraavan tai edellisen kuvan (toimii ainoastaan kuvapakoilla).
- ![medigi-tool-crosshairs](uploads/4c3853be3440e445757221de4ec5bf8c/medigi-tool-crosshairs.png) _Pakan kohdennus:_ Kohdentaa samasta kuvauksesta saatujen kuvapakkojen leikkeet samaan anatomiseen kohtaan (toimii ainoastaan kuvapakoilla).
- ![medigi-tool-orientation](uploads/b961c8381b32706bc10277218d1e90a6/medigi-tool-orientation.png) _Kuvan suuntaus (työkaluryhmä):_
  - Kierrä vastapäivään.
  - Kierrä myötäpäivään.
  - Käännä vaakasuunnassa.
  - Käännä pystysuunnassa.
- ![medigi-tool-measurement](uploads/02a0a1b6e4f00bd5a72dd39a70dac4fc/medigi-tool-measurement.png) _Mittaustyökalut (työkaluryhmä):_
  - Välimatkan mittaus.
  - Pinta-alan mittaus (sisältää myös HU-arvon)
- ![medigi-tool-invert](uploads/975f9c4a2f0a4cbf6321032d19e54032/medigi-tool-invert.png) _Käänteinen ikkunointi:_ Kääntää kuvan ikkunoinnin päinvastaiseksi (ns. invertoi kuvan).
- _Ikkunoinnin säätäminen:_ Säätää kuvan ikkunointia hiiren liikkeiden mukaisesti.
- ![medigi-tool-arrangement](uploads/9e5a1887643c174a3487d157cf654301/medigi-tool-arrangement.png) _Asettelutyökalut (työkaluryhmä):_
  - Automaattinen asettelu.
  - 2x2 ripustelu (manuaalinen asettelu).
- ![medigi-tool-link](uploads/4c1a702951863c8aacbae694ed856a1c/medigi-tool-link.png) _Kytke kaikki kuvapakat:_ Kytkee yhteen tai poistaa kytkennän kaikista auki olevista kuvapakoista.
- ![medigi-tool-reset](uploads/c738794fc335cf4178e6247e5b4757a0/medigi-tool-reset.png) _Palauta alkuperäinen näkymä:_ Palauttaa kaikkien aktiivisten kuvien kuvanäkymät alkuperäiseen tilaansa, ts. kumoaa liikuttelu-, suurennuslasi- ja ikkunointityökaluilla tehdyt muutokset.

Sekä oikeassa ylänurkassa:
- _Asetukset:_ Koko näytön tila sekä radiologianäkymän asetukset ja yleiset asetukset.

## 3. Sivupalkki

![medigi-radiology-sidebar](uploads/1a2c715e865424061842463554e51aad/medigi-radiology-sidebar.png)

Valitun käynnin tutkimukset aukeavat vasemmalle sivupalkkiin. Jos mahdollista, sivupalkkiin aukeaa myös esikatselukuva itse tutkimuksesta. Tutkimuksen klikkaaminen avaa sen katselunäkymään; toisen tutkimuksen klikkaaminen sulkee edellisen ja avaa klikatun tutkimuksen.

![medigi-radiology-single-image](uploads/bafa2753d955194f8715f19a177e3a26/medigi-radiology-single-image.png)

Jos uutta tutkimusta klikataan Control-nappi pohjassa, aukeaa klikattu tutkimus edellisen rinnalle. Jos tutkimusta klikataa Shift-nappi pohjassa, aukeavat myös kaikki aktiivisen ja klikatun tutkimuksen väliin jäävät tutkimuset.

![medigi-radiology-multiple-images](uploads/281431f09df62193a5a2ae7fbc6ff67a/medigi-radiology-multiple-images.png)

Tutkimusten avautumisjärjestystä on mahdollista vaihtaa muuttamalla niiden järjestystä sivupalkissa (raahaamalla kuvakkeita ylös tai alas). Vaihtoehtoisesti kuvat on mahdollista sijoitella ripustelunäkymässä manuaalisesti valmiiseen ruudukkoon raahaamalla ne haluttuun ruutuun.

![medigi-radiology-drag-image](uploads/9ce07ac6cb28d4248b42fb3d0c16fb42/medigi-radiology-drag-image.png)
![medigi-radiology-drop-image](uploads/e85ff280dfd663470d06037899ea7c89/medigi-radiology-drop-image.png)

Harvoin ripustellun kuvan lataaminen epäonnistuu, jolloin ruutuun tulee seuraava ilmoitus:

![medigi-radiology-loading-failed-fi](uploads/8106d6c335bb0cd8df7e6699212941c6/medigi-radiology-loading-failed-fi.png)

Tällöin kyseisessä kuvassa näkyy sivupalkissa häiriökuvake. Kuvauksen saa näkyviin klikkaamalla kuvausta sivupalkissa (muista painaa Control pohjaan, jos ole jo avannut muita kuvia!).

![medigi-radiology-loading-failed-sidebar](uploads/0fea6087f89e75bb98272af2b54398c4/medigi-radiology-loading-failed-sidebar.png)
