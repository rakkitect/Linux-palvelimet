<h1>H4 - Maailma kuulee</h1>

<h2>x) Tiivistelmä artikkelista First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS </h2>

- Vahvojen salasanojen käyttö on tärkeää. Siitä hetkestä lähtien kun palvelimesi on käynnistetty, siihen on yritetty jo murtautua.
- Tärkeitä ensimmäisiä vaiheita:
  - Palomuurin pystytys
  - Juurikäyttäjän lukitseminen
  - Softan päivitys
 - Verkkotunnus on käyttäjäystävällisempi kuin pelkkä IP-osoite.

<h2>a) Virtuaalipalvelimen vuokraus</h2>

Valitsin virtuaalipalvelimeni palveluntarjoajakseni DigitalOceanin. Luodessani sinne tunnuksia käytin GitHub:in käyttäjätunnustani kirjautumiseen. 
Tunnuksen luomisen yhteydessä vaadittiin pankkikortin lisäämistä maksuvälineeksi, ja sinne tehtiin 1.00 $ varaus kortin vahvistamiseksi.

DigitalOceanin etusivulla esiteltiin yleisimpä käyttötarkoituksia, ja valitsin "Host a website or static site", ja siitä seuraavalla sivulla valitsin "Debloy an Ubuntu server"

Ota screenshot luomisesta!!

<h2>b) Virtuaalipalvelimen alkutoimet</h2>

Kirjauduin aluksi DigitalOceanin omaan selainkonsoliin root-tunnuksella.

Tämän jälkeen tein nämä toimenpiteet:
- Otin palomuurin käyttöön
- Loin itselleni tunnuksen jolle annoin seuraavat oikeudet
  - sudo
  - adm
  - admin

Luotuani tunnukset ja annettuani sille täydet oikeudet, kokeilin ssh kirjautumista virtuaalikoneeni konsolissa. Todettuani että kirjautuminen toimii, menin takaisin DigitalOceanin selainkonsoliin sulkeakseni root-tunnuksen.
Käytin näitä komentoja:
`sudo usermod --lock root`
`sudoedit /etc/ssh/sshd_config`

Päivityksien lomassa tapahtui jokin virhe, jonka jälkeen SSH kirjautuminen ei toiminut, käynnistin DigitalOceanin Recovery Consolen ja sen avulla sain korjattua ongelman, käyttäen tätä komentoa: laita kuva
