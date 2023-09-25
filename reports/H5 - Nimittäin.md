<h1>H5 - Nimittäin</h1>

<h2>x) Lue ja tiivistä</h2>

<h3>Karvinen 2016: New Default Website with Apache2 – Show your homepage at top of example.com, no tilde</h3>
- Apachella VirtualHost on yhtäkuin verkkosivu
- Käytettävissä olevat sivut sijaitsevat hakemistossa `/etc/apache2/sites-available/`
- Uuden VirtualHostin luodaksesi, tarvitsee sinun luoda asetustiedosto ja samalla nimellä oleva hakemisto

<h3>Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address</h3>
- VirtualHost mahdollistaa usean eri domain-nimen liittämistä yhteen IP-osoitteeseen

<h3>Apache Software Foundation 2023: Name-based Virtual Host Support</h3>

- DNS-palvelin konfiguroidaan niin että jokainen hostname yhdistää oikeaan IP-osoitteeseen, jonka jälkeen Apache-palvelin konfiguroidaan tunnistamaan eri hostnamet.
- Tällä tavalla saadaan säästettyä IPv4-osoitteita
- Apache-palvelin käyttää "xxxx.conf" VirtualHost-asetustiedostoja tunnistamaan mikä on hakua parhaiten vastaava verkkosivu

a) Vuokraa domain-nimi ja aseta se osoittamaan virtuaalipalvelimeesi.*

Vuokrasin tätä tehtävää varten domain-nimen domain.com palvelusta. Lopulliseksi vuosihinnaksi osoitteelleni tuli 1.23$, elikkä noin 1.15€. Alkuperäinen hinta oli 0.99$, mutta Ameriikan tapaan verojen määrä ilmoitettiin vasta loppuvaiheessa.

![Ostoskori](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/kori.png)

Domain.comin käyttöliittymä oli melko vaikeasti suunnistettavissa, mutta pienen odottelun ja Googlettamisen jälkeen pääsin kuin pääsinkin muuttamaan DNS-asetuksia. Tätä kautta saan ostamani domain-nimen osoittamaan Apache2-palvelimeni IP-osoitteeseen.

![DNS asetukset](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/add_dns_record.png)

Seuraavana päivänä sain domain-nimeen yhteyden virtuaalikoneella, puhelimella ja tietokoneellani. Alunperin sain virhettä Forbidden 403, mutta korjasin sen komennolla `sudo chmod ugo+x / /home /home/osku /home/osku/public_html/`. Ymmärtääkseni `chmod ugo+x` muuttaa tarkennetun hakemiston suoritus/haku oikeudet niin että käyttäjät jotka eivät ole osa hakemiston käyttäjäryhmiä voivat suorittaa haun hakemistoon. (Die.net s.a.)

![chmod](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/chmod.png)

![Toimii](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/toimii.png)

<h2>b) Tutki oman nimesi tietoja 'host' ja 'dig' -komennoilla. Analysoi tulokset.</h2>

![Host ja Dig komennot](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/host_ja_dig.png)

`host rakkitehti.space` tulosti IP-osoitteet joihin kyseinen domain-nimi osoittaa, sekä mikä sähköpostipalvelin vastaanottaa tälle domain-nimelle lähetetyt sähköpostit.
`dig rakkitehti.space` tulostaa paljon laajemman raportin, kertoen paljon tietoverkkoihin liittyvää tietoa. 
- Ensimmäisellä rivillä kohta "DiG 9.18.12-0ubuntu0.22.04.3-Ubuntu" viittaa `dig`-komennon versioon
- "ANSWER SECTION" kertoo tärkeimmät tiedot
  - Ensimmäinen sarake haetun palvelimen nimen
  - Toinen sarake kertoo palvelimen TTL eli Time to Live
  - Kolmas sarake kertoo mihin luokkaan kysely kuuluu. IN = Internet
  - Neljäs sarake kertoo että kyselyn tyyppi on A-tietue, eli Address (Osoite)
- "OPT PSEUDOESECTION" kohdasta en tiedä muuta kuin UDP-paketin koon, eli tässä haussa se on 65494 tavua
- "QUESTION SECTION" antaa tietoa tehdystä kyselystä
- Viimenen kohta antaa kyselyn metadatan, kuten kuinka kauan kyselyssä kesti, mikä oli vastaanottavan DNS-palvelimen IP-osoite ja portti, milloin haku suoritettiin ja vastauksen koko. (PhoenixNAP 1.9.2020)

<h2>c) Etusivu uusiksi. Name based virtual hosting. Laita kotisivusi näkymään oman palvelimen etusivulla. Sivujen tulee olla tallennettu jonnekin kotihakemistojen alle ja olla muokattavissa ilman sudoa.</h2>

Loin uuden VirtualHostin komennolla `sudoedit /etc/apache2/sites-available/rakkitehti.space.conf`. Tämä luo asetustiedoston "rakkitehti.space.conf" hakemistoon "/etc/apache2/sites-available/" jossa Apachen saavutettavissa olevat sivut ovat.

Asetustiedoston luominen:
![VirtualHost](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/rakkitehti_virtualhost.png)

Ymmärtääkseni tämä asettaa VirtualHostin juurihakemistoksi /home/osku/public_html/, jolloin kaikki siihen hakemistoon luomani .html tiedostot ovat osa rakkitehti.space verkkosivuja.

Enabloin luomani VirtualHostin komennolla `sudo a2ensite osku.conf` ja disabloin vanhan oletussivun komennolla `sudo a2dissite 000-default.conf`. Tämän jälkeen käynnistin palvelimen uudelleen komennolla `sudo service apache2 restart` jotta muutokset tulevat voimaan.

Lopputuloksena, muutaman mutkan jälkeen jotka johtuivat typoista, joillain laitteilla http://rakkitehti.space/ toimii, ja joillain ei. Syytä en tiedä. Myönnetään että tein tämän tehtävän ja raportin hieman hätäisesti, joten mahdollisia virheitä on monia enkä kaikkea välttämättä muistanut raportoida.


<h2>Lähteet</h2>

- Die.net s.a. Linux man page. Luettavissa: https://linux.die.net/man/1/chmod
- PhoenixNAP. How to use Linux dig Command (DNS Lookup) 1.9.2020. Luettavissa: https://phoenixnap.com/kb/linux-dig-command-examples
- Karvinen, T 2016. New Default Website with Apache2 – Show your homepage at top of example.com, no tilde. Luettavissa: https://terokarvinen.com/2016/02/16/new-default-website-with-apache2-show-your-homepage-at-top-of-example-com-no-tilde/
- Karvinen, T 2018. Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address. Luettavissa: https://terokarvinen.com/2018/04/10/name-based-virtual-hosts-on-apache-multiple-websites-to-single-ip-address/
- Apache Software Foundation 2023: Name-based Virtual Host Support. Luettavissa: https://httpd.apache.org/docs/2.4/vhosts/name-based.html
