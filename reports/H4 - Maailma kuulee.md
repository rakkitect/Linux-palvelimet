<h1>H4 - Maailma kuulee</h1>

<h2>x) Tiivistelmä artikkelista First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS </h2>

- Vahvojen salasanojen käyttö on tärkeää. Siitä hetkestä lähtien kun palvelimesi on käynnistetty, siihen on yritetty jo murtautua.
- Tärkeitä ensimmäisiä vaiheita:
  - Palomuurin pystytys
  - Juurikäyttäjän lukitseminen
  - Softan päivitys
 - Verkkotunnus on käyttäjäystävällisempi kuin pelkkä IP-osoite.

(Karvinen 19.9.2017)

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

![Dropletin luominen](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/droplet_luonti.png)

<h2>b) Virtuaalipalvelimen alkutoimet</h2>

Palvelimen luonnin jälkeen kirjauduin root-käyttäjänä terminaalin kautta.

Tämän jälkeen tein nämä toimenpiteet:
- Otin palomuurin käyttöön
- Loin itselleni tunnuksen jolle annoin seuraavat oikeudet
  - sudo
  - adm
  - admin
 
  ![Add user](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/sudo_adduser.png)
  ![Sudo adm, admin](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/sudo_adduser_sudo.png)

Luotuani tunnukset ja annettuani sille täydet oikeudet, kokeilin ssh kirjautumista toisessa terminaalissa. Todettuani että kirjautuminen toimii, suljin root-käyttäjän mahdollisuuden kirjautua sisään.

Käytin näitä komentoja:
- `sudo usermod --lock root`
- `sudoedit /etc/ssh/sshd_config`
- `PermitRootLogin no`
- `sudo service ssh restart`

![Root Lockout](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/root_lockout.png)

Seuraava vaihe palvelimen käyttöönotossa on tietenkin paketinhallinnan päivitykset, eli kunnon vanhat `sudo apt-get update` ja `sudo apt-get upgrade`.

Päivityksien lomassa tuli seuraava ilmoitus:
![openssh-server](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/openssh-server.png)

Valitsin kohdan "Keep the local version currently installed", sillä se oli valmiiksi valittu, ja ymmärtääkseni se säilyttää vain muokatun sshd_config tiedoston.

<h2>c) Apache-palvelimen asennus</h2>

Tässä osiossa asennan vuokratulle pilvipalvelimelle Apache2 web-palvelimen.

Asennus aloitetaan tietenkin päivittämällä pakettienhallinan paketit uusimpiin komennolla `sudo apt-get update`. Tämän jälkeen suoritin itse Apachen asennuksen komennolla `sudo apt-get install apache2`.

Avasin Apachea varten reiän palomuuriin komennolla `sudo ufw allow 80/tcp`, jonka jälkeen sain palvelimeen yhteyden selaimessa.

![Apache_default](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/apache2_default.png)

Vaihdoin Apachen oletussivun menemällä hakemistoon `/var/www/html/` ja poistin olemassa olevan "index.html" tiedoston komennolla `sudo rm index.html`, jonka jälkeen loin uuden aloitussivun komennolla `sudo micro index.html`

Verkkosivun toimivuutta julkisesti kokeilin toisella tietokoneella Chrome-selaimen kautta avulla.

Linkki verkkosivulle on http://159.89.28.46/, jätän ne auki muutamaksi päiväksi tämän raportin julkaisun jälkeen.

![julkinen_apache](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/julkinen_apache.png)

<h2>d)Merkkejä murtautumisyrityksistä</h2>

Siitä hetkestä lähtien kun palvelimen kytkee verkkoon ja julkisesti saataville, on oletettavaa että sitä kohtaan kohdistuu useita murtautumisyrityksiä.

Komennolla `cat /var/log/auth.log | grep "authentication error"` sain printattua suunnattoman määrän lokiin merkattuja yrityksiä. Yrityksien välillä on noin 10-20 sekuntia.

![Authentication error](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/auth_log.png)

Komennolla `journalctl -n 2000 | grep "invalid user` sain selville murtautumisyrityksissä käytettyjä käyttäjänimiä. Osa nimistä näkyi useaan otteeseen.

![Journalctl](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/journalctl.png)

Käytin https://www.whatismyip.com/ip-address-lookup/ ottamaan selvää mistä päin maailmaa osa murtautumisyrityksistä tuli.
- Indonesia
- Kanada
- Englanti
- Venäjä

Tässä tietysti vain muutama, mutta oletettavaa on että yrityksiä on joka puolelta maata.

<h2>Lähteet</h2>
- Karvinen T, First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. Luettavissa:  https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/
