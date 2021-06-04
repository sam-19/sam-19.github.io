---
layout: default
title: Moodle-lisäosa
parent: Suomeksi
grand_parent: Medical Imaging Study Viewer
nav_order: 3
has_children: false
---

<h1>Katselimen Moodle-lisäosa</h1>

* TOC
{:toc}

## Yleistä

Katselimen käyttöön Moodlessa tarvitaan erillinen lisäosa, ns. filtteri. Lisäosa poimii tekstistä tunnisteen, jonka perusteella se käynnistää katselinsovelluksen ja lataa siihen halutut tutkimukset. Tunniste on mahdollista kirjoittaa myös käsin, mutta sen syöttäminen on helpompaa toisen, valinnaisen lisäosan avulla, joka laajentaa Moodlen Atto-tekstinkäsittelijän ominaisuuksia.

## Moodle filter

Filtteri tunnistaa tekstin joukosta sellaiset hyperlinkit, joissa on tietty tunniste perässä. Tämän jälkeen filtteri korvaa kyseisen linkin katselinsovelluksella, johon se avaa linkin kohteen.

### Linkin lisääminen manuaalisesti

Mikä tahansa linkki on mahdollista merkata sovullekselle `:medimg-resource`-tunnisteella linkin href-kentässä.

Esimerkki: Kirjoita mikä tahansa kuvaava teksti (tämä näkyy vain sisällön muokkaajille) ja linkkaa siihen haluamasi kuvantamistiedosto.

![atto-editor-link](atto-editor-link.png)

Avaa lisätyökalut vasemmassa ylänurkassa olevasta nuolesta ja aktivoi HTML-muokkaustila. Tämän jälkeen lisää tekemäsi linkin href-kentän loppuun `:medimg-resource`.

![atto-editor-html](atto-editor-html.png)

Muokkaajalle linkki näkyy edelleen linkkinä, mutta Moodlen käyttäjälle latautuu katselinsovellus linkin tilalle. Linkattu tiedosto avautuu katselimeen automaattisesti.

Moodlen linkkausominaisuus ei ikävä kyllä tue kansioiden linkkaamista, mikä tekee niiden manuaalisesta lisäämisestä aavistuksen haastavampaa. Jos edellisen esimerkin tiesoto olisi ollut kansiossa `/Esimerkkikuvaus/somedicom.dcm` ja tarkoituksena olisi linkata koko kansio, olisi linkki pitänyt tehdä ensin itse tiedostoon ja tunnistetta lisättäessä poistaa tiedoston nimi, jolloin lopullinen href-kenttä olisi ollut `https://.../Esimerkkikuvaus/:medimg-resource`.

![atto-editor-dir](atto-editor-dir.png)

### Linkin lisääminen Atto-pluginia käyttäen

Moodlen Atto-tekstinkäsittelijään on saatavilla lisäosa, joka helpottaa paitsi tiedostojen, erityisesti kansioiden linkkaamista.

Avaa lisäosan tiedostoselain sen painikkeesta (painikkeen ulkonäkö ja sijainti voi vaihdella Moodle-ympäristöstä riippuen). Paikallinen tiedostoalue aukeaa näkyviin. Kansion tai tiedoston nimen klikkaaminen valitsee sen ylärivin osoitekenttään. Tuplaklikkaaminen lisäksi avaa tai sulkee kansion.

![atto-plugin-browser](atto-plugin-browser.png)
![atto-plugin-select](atto-plugin-select.png)

Osoiterivin oikeassa reunassa on kaksi painiketta, kopioi ja liitä (_copy_ ja _insert_). Kopioi-painike kopioi aina valitun tiedoston/kansion osoitteen ja siihen valmiiksi liitetyn tunnisteen perään. Tämä on mahdollista sitten lisätä linkkinä tekstinkäsittelijän normaalilla linkkityökalulla.

Liitä-painikkeen toiminta riippuu siitä, mitä tekstinkäsittelyruudussa oli valittuna (maalattuna) kun hakemisto avattiin:
- Jos valittuna oli tekstiä, lisätään tiedosto linkkinä valittuun tekstiin.
- Jos valittuna oli aikaisempi linkki, päivitetään sen linkin osoite valittuun resurssiin.
- Jos valittuna ei ollut mitään, lisätään linkki kursorin sijaintikohtaan ja linkin tekstiksi tulee tiedoston osoite.

Kaikissa tapauksissa käyttäjälle kuitenkin aukeaa linkin sijaan sen kohteessa oleva tiedosto/tiedostojärjestelmä katselinsovelluksessa.

## Huomioita ja tunnettuja ongelmia

Joskus sisältöä muokkaustilassa selattaessa ei oikeassa ylänurkassa oleva valikko (_Actions menu_) aukea, jos samalla sivulla on selainsovellus. Sivu on ladattava uudestaan, jotta valikon saa avattua.

Tiedostoalueen tiedostoja Moodlen omalla selaimella tarkasteltaessa saattaa näkyä lukuisia ilmoituksia käyttämättömistä tiedostoista (erityisesti jos alueelle on tallennettu kuvapakkoja). Tämä ei haittaa; kuvankatselin osaa kyllä löytää nämä tiedostot, vaikka niitä ei olekaan suoraan linkitetty tekstiin.
