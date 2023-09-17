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
Tunnuksen luomisen yhteydessä vaadittiin pankkikortin lisäämistä maksuvälineeksi, ja sille tehtiin 1.00 $ varaus kortin vahvistamiseksi.

DigitalOceanin etusivulla valitsin "Spin up a Droplet", joka on heidän käyttämä nimi virtuaalikoneelle.
Käyttämäni valinnat:
- Region: Frankfurt
- Datacenter: Frankfurt - Datacenter 1 - FRA1
- Image: Ubuntu 22.04 (LTS) x64
- Size: Shared CPU - Basic
- CPU: Regular - Disk type: SSD
- Authentication method: Salasana

![Droplet_luonti.png]

Ota screenshot luomisesta!!

<h2>b) Virtuaalipalvelimen alkutoimet</h2>

Palvelimen luonnin jälkeen, kirjauduin root-käyttäjänä terminaalin kautta.

Tämän jälkeen tein nämä toimenpiteet:
- Otin palomuurin käyttöön
- Loin itselleni tunnuksen jolle annoin seuraavat oikeudet
  - sudo
  - adm
  - admin

Luotuani tunnukset ja annettuani sille täydet oikeudet, kokeilin ssh kirjautumista toisessa terminaalissa. Todettuani että kirjautuminen toimii, suljin root-käyttäjän mahdollisuuden kirjautua sisään.

Käytin näitä komentoja:
- `sudo usermod --lock root`
- `sudoedit /etc/ssh/sshd_config`
- `PermitRootLogin no`
- `sudo service ssh restart`

Seuraava vaihe palvelimen käyttöönotossa on tietenkin paketinhallinnan päivitykset, eli kunnon vanhat `sudo apt-get update` ja `sudo apt-get upgrade`.

Päivityksen lomassa tuli vastaava virhe:
[openssh-server]

Valitsin kohdan "Keep the local version currently installed", sillä se oli valmiiksi valittu, ja ymmärtääkseni se säilyttää vain muokatun sshd_config tiedoston.
