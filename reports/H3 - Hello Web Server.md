<h1>Hello Web Server</h1>

<h2>x) "Install Apache Web Server on Ubuntu" tiivistelmä</h2>

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

Muutos aloitussivuun tehtiin komennolla `echo hello|sudo tee /var/www/html/index.html` jonka jälkeen käynnistin palvelimen uudestaan komennolla `sudo systemctl restart apache2`.

Tämän jälkeen Apache2-palvelimen aloitussivu näyttää vastaavalta:

![default page](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/lyhyt_home.png)

<h2> d) Laita käyttäjien kotisivut toimimaan.</h2>

Tämän vaiheen tein puolivahingossa jo aikaisemmassa vaiheessa, niin tästäkään ei ole kuvia todistamaan prosessia.

Käyttäjälle annetaan oikeus tehdä kotisivuja komennolla `sudo a2enmod userdir`, jonka jälkeen palvelin pitää taas käynnistää uudestaan komennolla `sudo systemctl restart apache2` jotta se tulee voimaan.

Tämän jälkeen sain luotua kotihakemistooni uuden kansion "public_html" komennolla `mkdir public_html`, joka mahdollistaa surffaamisen osoitteeseen "127.0.0.1/~oskuh/

![Kotisivuhakemisto](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/kotisivu.html.png)

<h2> e) Tee validi HTML5 sivu.</h2>

Testasin aikaisemmin luomani kotisivun validiteetin tällä verkkosivulla: https://validator.w3.org/ käyttämällä "File Upload"-vaihtoehtoa.

Aluksi sain varoituksen `lang` attribuutin puuttumisesta, ja että "The character encoding was not declared", mutta nämä sain korjattua lisäämällä html-tagiin `lang="fi"`, ja lisäämällä meta-tagin `<meta charset="utf-8" />`

![Validiteetti todistus](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/validiteetti.png)

<h2> Anna esimerkit 'curl -I' ja 'curl' -komennoista. Analysoi 'curl -I' tuloste.</h2>

`curl` komennolla tulostetaan tiedosto tekstinä komentoriville.

![Curl-komento](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/curl_komento.png)

`curl -i` komento tulostaa lisäksi informaatiota:
- Date: Koska tiedosto on luotu
- Server: Tämä liittyy jotenkin tietokoneeseen millä tiedosto on luotu, enempää en tiedä
- Last modified: Milloin viimeksi tiedostoa on muokattu
- eTag: Selaimen antama tunniste tiedoston lähteelle
- Lopuista en tiedä

![curl -i](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/curl_i_komento.png)


<h2>Lähteet</h2>
- Karvinen, T 2008 Install Apache Web Server on Ubuntu. Luettavissa: https://terokarvinen.com/2008/05/02/install-apache-web-server-on-ubuntu-4/. Luettu 11.09.2023
