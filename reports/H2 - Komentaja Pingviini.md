<H1>H2 - Komentaja Pingviini</H1>

<h2>x) Command line basics revisited</h2>

- `sudo` komento antaa korkeimmat mahdolliset oikeudet. Sitä tarvitaan kaikkiin komentoihin jotka vaikuttavat järjestelmään kokonaisvaltaisesti. Asetetaan komennon eteen, esim. `sudo apt-get update`
- joitain komentoja hakemistossa liikkumiseen: `pwd` = tulostaa työskentelyhakemiston, `ls` = listaa tiedostot ja alahakemistot työskentelyhakemistossa
- Tärkeitä hakemistoja, joita kaikkien pitäisi muistaa ovat juurihakemisto `/`, kaikkien käyttäjien kotihakemisto `/home/` ja `/var/log/` johon tallentuu kirjaukset kaikesta mitä järjestelmässä on tapahtunut

<h2>a) Micro-editorin asennus</h2>

Aloitin asennusprosessin päivittämällä Linuxin pakettihakemiston komennolla `sudo apt-get update`, jonka jälkeen syötin komennon `sudo apt-get -y install micro`. 

![Micro-editorin asennus](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/micro_asennus1.png)

Lisäämällä komentoon tuon `-y`-kohdan, käsken komentoriviä vastaamaan kaikkiin "tyhmiin" kysymyksiin kyllä, jolloin asennus käynnistyy heti.

![Micro-editori käytössä](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/micro_editori.png)

<h2>b) Rauta </h2>

Asensin komentoriviltä "LSHW"-työkalun, jolla pystyy poimia yksityiskohtaista tietoa koneen "raudasta", eli laitteistosta. Tein tämän komennolla `sudo apt-get -y install lshw`

![lshw asennus](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/lshw_asennus.png)

Asennuksen jälkeen ajoin komennon `sudo lshw -short -sanitize`. Komennon viimeinen osa poistaa lopputuloksesta kaiken aran tiedon, kuten IP-osoitteet ja sarjanumerot. Työkalua pystyy käyttämään myös ilman superkäyttäjän tunnuksia, mutta silloin se näyttää vain rajattua tietoa.

![lshw listaus](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/lshw_listaus.png)

Listauksesta näkee kaiken mitä fyysisessäkin emolevyssä olisi kytkettynä, kuten RAM-muistin, prosessorin, kovalevyn ja USB-portit. 

Listauksen mukaan virtuaalikoneeni prosessori on AMD Ryzen 7 5800U ja  RAM-muistia on 4GiB. Ensimmäisen rivin kuvaus paljastaa koneemme olevan VirtualBox virtuaalikone

<h2>c) apt</h2>

Asensin itselleni kolme uutta komentoriviohjelmaa: Googler, Figlet ja Cmatrix. Sain kaikki kolme asennettua yhdellä komennolla: `sudo apt-get install googler figlet cmatrix -y`

![Apt asennus](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/asennus.png)

Googlerin avulla pystyy tekemään hakuja Googleen komentorivin kautta, ja painamalla hakutuloksien indeksinumeroa, se avaa kyseisen verkkosivun selaimessa.

![Googler](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/googler.png)

Figletin avulla pystyt luoda ASCII tekstibannereita haluamastasi tekstistä.

![Figlet](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/figlet.png)

Cmatrix mahdollistaa komentorivin käyttämistä näytönsäästäjänä, ja teemana on tietenkin ikoninen sci-fi leffa. Näytönsäästäjän saa suljettua painamalla `q` tai `Ctrl + C`

![Cmatrix](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/cmatrix.png)

<h2>d) FHS - Filesystem Hierarchy Standard</h2>

/ = Linuxin juurihakemisto jonka alla kaikki tiedostot ja hakemistot ovat

![Juuri](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/juuri.png)

/home/ = Sisältää kaikkien käyttäjien kotihakemistot

![home](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/home.png)

/home/oskuh/ = Käyttäjän oskuh kotihakemisto, sisältää kaiken mitä olen tallentanut

![home_oskuh](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/home_oskuh.png)

/etc/ = Sisältää kaikki järjestelmän asetustiedostot, on ikäänkuin Linuxin hermosto.

![etc](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/etc.png)

/media/ = Mikäli koneeseen on kytketty jokin ulkoinen tallennusväline, kuten USB-tikku tai CD-levy, se näkyisi tämän hakemiston alla

![media](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/media.png)

/logs/ = Sisältää kaikki järjestelmän luomat kirjaukset eri tapahtumista

![logs](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/logs.png)

<h2>e) The Friendly M </h2>

Tässä osiossa näytän muutaman esimerkin `grep`-komennon käytöstä. Tämän komennon avulla etsitään tekstiä ja merkkijonoja määritellystä tiedostosta

Komennolla `grep oskuh /etc/passwd` etsin käyttäjää "oskuh" passwd tiedostosta, joka sijaitsee /etc/ hakemistossa

![Grep1](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/grep1.png)

Komento `grep -ril 'lorem' ~/paivat/` etsii kaikki tiedostot jotka sisältävät sanan "lorem"  hakemistosta "paivat".

- `r` etsii rekursiivisesti
- `i` tekee hausta kirjainkoosta riippumattoman
- `l` listaa tiedostojen nimet

![Grep2](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/grep2.png)

<h2>f) Pipe </h2>

Putki, eli `|` mahdollistaa kahden komennon yhdistämisen, ja käyttää ensimmäisen tulosta toisen syötteenä.

Esimerkki: Komento `ls -l | more` listaa kaikki tiedostot ja hakemistot nykyisestä hakemistosta, ja käyttää niitä `more`-komennon syötteenä. Tämä on hyödyllistä mikäli hakemistossa olisi erittäin paljon tiedostoja, eivätkä ne mahtuisi yhteen ruutuun.

![Pipes](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/pipes.png)

<h2>g) Tukki </h2>

Minulla oli vaikeuksia ymmärtää tätä tehtävää, joten jätin sen tekemättä.

<h2>Lähteet:</h2>
- Karvinen, T. Command Line Basics Revisited 2020, Luettavissa: https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited
