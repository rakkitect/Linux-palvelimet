<h1>Hello Web Server</h1>

<h2>x)"Install Apache Web Server on Ubuntu" tiivistelmä</h2>

- Apache asennetaan paketinhallinasta komennolla `sudo apt-get install apache2`
- Palvelinta voi selata verkossa osoitteesta "http://localhost"'
- Palvelimen tiedostot tallennetaan käyttäjän kotihakemistoon, kansion "public_html" alle.
   - Tämä kansio pitää luoda itse komennolla `mkdir public_html`

(Karvinen 2.5.2008)

<h2>a) Asenna Apache-palvelin</h2>

Olin asentanut Apachen jo aikaisemmin, joten tässä raportissa ei ole kuvankaappauksia itse prosessista.

Aloitin asennuksen päivittämällä paketinhallinnan komennolla `sudo apt-get update`. Tämän jälkeen aloitin itse asennuksen komennolla `sudo apt-get install apache2`.
Asennusprosessin jälkeen kokeilin palvelimen toimintaa komennolla `firefox http://localhost` joka avaa palvelimen selainnäkymässä. Näin vahvistin että palvelimeen saa yhteyden.

![Apache-palvelimen localhost-näkymä](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/localhost.png)

Komennolla `ip addr` sain selville virtuaalikoneeni IP-osoitteen, jota käyttämällä myös muut voisivat ottaa yhteyden palvelimelleni verkkoselaimen kautta syöttämällä IP-osoitteen selaimen osoitepalkkiin.

Käyttäjäni kotisivuja pääsin selaamaan komennolla `firefox "http://localhost/~oskuh"`. Aluksi tämä ei toiminut, mutta käynnistettyäni Apache2-palvelimen uudestaan komennolla `sudo systemctl restart apache2` sain kotihakemiston näkyviin.

![Kotisivu](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/homepage.png)

<h2>b) Etsi lokista rivit, jotka syntyvät, kun lataat omalta palvelimeltasi yhden sivun. Analysoi rivit.</h2>

Tätä tehtävää varten loin kotihakemistooni tiedoston "hello_world.html" Libre Officen avulla. Sain sen tallennettua suoraan hakemistoon ilman komentorivin käyttöä.

Latasin luomani sivun, ja sen jälkeen hain Apache2 lokitiedostot komennolla: `sudo tail /var/log/apache2/access.log`.

![Lokit](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/download_kotisivu.png)

Analyysi:
- Loki näyttää missä IP-osoitteessa on tapahtunut ja mihin kellonaikaan.
- Oletan että "GET" tarkoittaa sitä että palvelimelta on "haettu" eli ladattu perässä mainittu tiedosto, eli "/~oskuh/hello_world.html"
- HTTP/1.1 on tapahtumassa käytetty protokolla
- Oletan että Mozilla/5.0 tarkoittaa tapahtumassa käytettyä selainta

<h2>c) Vaihda Apachen esimerkkisivu johonkin lyheen sivuun niin, että vanha esimerkkisivu ei näy.</h2>

Tätä tehtävää en osannut tehdä.

<h2> d) Laita käyttäjien kotisivut toimimaan</h2>












<h2>Lähteet</h2>
- Karvinen, T 2008 Install Apache Web Server on Ubuntu. Luettavissa: https://terokarvinen.com/2008/05/02/install-apache-web-server-on-ubuntu-4/. Luettu 11.09.2023
