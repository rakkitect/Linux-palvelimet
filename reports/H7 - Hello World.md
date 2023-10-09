<h1>H7 - Hello World</h1>

<h2>x) Linkit aikaisempiin läksyihin</h2>

- [H1 - Oma Linux](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H1%20-%20Oma_linux.md)
- [H2 - Komentaja Pingviini](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H2%20-%20Komentaja%20Pingviini.md)
- [H3 - Hello Web Server](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H3%20-%20Hello%20Web%20Server.md)
- [H4 - Maailma Kuulee](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H4%20-%20Maailma%20kuulee.md)
- [H5 - Nimittäin](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H5%20-%20Nimitt%C3%A4in.md)
- [H6 - DJ ANGO](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H6%20-%20DJ%20Ango.md)

<h2>y) Lue ja tiivistä</h2>

Karvinen 2018: https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/

- `Hello World!` on yleinen tapa testata ohjelmointikielen toimivuus.
- Itselleni relevantit kielet lienee: Python 3, Java, C
  - Nämä sen takia, että mielenkiintoni raportin kirjoitushetkellä kohdentuu kyberturvallisuuteen
- Ohjelmointikielet löytyvät Linuxilla paketinhallinnasta komennolla `apt-get`


<h2>a) "Hello World" Pythonilla, Javalla ja C:llä</h2>

Tässä tehtävässä minun pitää asentaa kääntäjät (compiler) Pythonia, Javaa ja C:tä varten, joten ensimmäisenä päivitän paketinhallinan sekä asennetut paketit komennoilla `sudo apt-get update` ja `sudo apt-get upgrade`. Edeltävä komento päivittää paketinhallinan valikoiman uusimpiin versioihin, ja jälkimmäinen lataa päivitykset Linux-ympäristööni asennettuihin paketteihin.

Koneellani oli valmiiksi jo kääntäjät C:lle ja Pythonille, mutta asennukset olisin tehnyt komennoilla `sudo apt-get install python3` ja `sudo apt-get install gcc`. Javaa varten en ollut asentanut kääntäjää, joten sen asensin komennolla `sudo apt-get install default-jdk`. Löysin tarvittavan paketin komennolla `sudo apt-cache jdk`. "JDK" on lyhenne sanoista Java Development Kit, jonka mukana tulee kääntäjä ja yleisimmät luokka kirjastot (class libraries) (Tyson, M 2022).

<h3>Python3:</h3>

- Loin hello.py tiedoston "Micro"-tekstieditorilla käyttäen komentoa `micro hello.py`
- Koodi pyöritetään komennolla `python3 hello.py`

![Hello World Pythonilla](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/hello_python.png)
  
<h3>Java:</h3>

- Loin hello.java tiedoston "Micro"-tekstieditorilla käyttäen komentoa `micro hello.java`
- Javalla on tärkeää että tiedoston nimi on sama kuin koodissa oleva luokka, joten tiedoston ollessa "hello.java" nimesin luokan myös "hello"
  - Tämä on "case sensitive", eli kirjainkoolla on väliä
- Tiedoston luonnin jälkeen, koodi piti vielä kääntää komennolla `javac hello.java`
- Tämän jälkeen pystyin pyörittää koodin terminaalissa komennolla `java hello`

![Hello World Javalla](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/hello_java.png)

<h3>C:</h3>

- Loin hello.c tiedoston "Micro"-tekstieditorilla käyttäen komentoa `micro hello.c`
- Kun koodi on kirjoitettu, se pitää kääntää komennolla `gcc hello.c -o helloc`

![Hello World C:llä](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/hello_c.png)
 
<h2>b) "Hello World!" bash:illa.</h2>

Päätiin tehdä tämän tehtävän vielä bash-kielellä, koska ymmärtääkseni se on hyödyllinen ohjelmointikieli tietoverkkojen kanssa työskennellessä:
- Kooditiedoston kirjoitin komennolla `micro hello.sh`
- Bash-komentoa ei tarvinnut erikseen kääntää, vaan pystyin heti ajamaan sen komennolla `bash hello.sh`

![Hello World Bashilla](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/hello_bash.png)

Lopuksi vielä kuinka pyörittää koodi kaikilla mainituilla kielillä:

![Hello World Pythonilla, Javalla, C:llä ja Bashilla](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/hello_kaikki.png)


<h2>c) Python-taskulaskin</h2>

Pythonia voi käyttää myös laskimena terminaalin sisällä. Pythonin käynnistys onnistuu komennolla `Python3` jonka jälkeen voit syöttää suoritettavan koodin.

![Pythonin käyttö laskimena](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/python_laskin.png)

Pythonin laskennalliset toiminnot:

<img src="https://github.com/rakkitect/Linux-palvelimet/blob/main/images/python_laskin_hommat.png" width="600">


<h2>d) Tee shell script.</h2>

Tähän tehtävään tein Bashilla scriptin, joka kertoo onko syöttämäsi numero pariton vai parillinen. Loin shell-scriptin komennolla `micro pariton.sh`.

![Scripti joka kertoo onko syötetty numero pariton vai parillinen](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/shell_script.png)

- Ensimmäinen rivi on shebang-merkintä, joka määrittää että scripti on tarkoitus suorittaa Bash:ia käyttäen (Wikipedia)
  - Myöhemmässä vaiheessa muokkasin tätä riviä vielä niin että shebang on `#!/usr/bin/bash`

<h2>e) Tee uusi komento Linuxiin</h2>

Jotta voin muuttaa äsken tekemäni scriptin komennoksi, pitää minun ensin antaa kaikille käyttäjille oikeudet ajaa se. Tämä onnistuu komennolla `chmod ugo+rx pariton.sh`.

Alunperin tein scriptin oman käyttäni kotihakemistoon, mutta kopioin sen komennolla `sudo cp pariton.sh /usr/local/bin/` hakemistoon jotta muut käyttäjät pääsevät siihen myös käsiksi.

Tein scriptistä komennon käyttämällä `alias` komentoa. Se luo oikotien määräämääsi komentoon. Minun tilanteessani käytin komentoa `alias nro=bash /usr/local/bin/pariton.sh`. Tällöin kirjoittamalla "nro" ja painamalla enteriä, tekemäni scripti pyörii.

Tässä vaiheessa komento `nro` ei kuitenkaan toiminut luomallani testikäyttäjällä, ja ideoita sen korjaamiseksi ei ole.

Tässä scriptin koodi ja /etc/profile -tiedostoon luomani alias komento.

![Koodi](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/pariton.png)
![Profile alias](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/profile.png)
![Ei toimi](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/ei_toimi.png)


<h2>f) Intelligent intelligence. Ratkaise vanha arvioitava laboratorioharjoitus.</h2>

- 

<h2>g) Asenna arvioitavaa laboratorioharjoitusta varten itsellesi uusi tyhjä virtuaalikone. Suosittelen Debian 12-Bookworm, amd64. Koneella saa halutessasi olla paketit päivitettynä ja palomuuri asennettuna. Koneella ei saa olla näiden lisäksi muita asetuksia ja ohjelmia kuin ne, jotka tulivat tavalliesn asennuksen yhteydessä. Katso, että koneella on toimiva nettiyhteys, riittävästi kovalevytilaa ja RAM-muistia. Virtuaalikoneella ei saa olla luottamuksellisia tietoja.</h2>

Asennan labraharjoitusta varten Debian 12.2-Bookworm-imagella varustetun virtuaalikoneen. Imagen latasin täältä: https://www.debian.org/releases/bookworm/debian-installer/. Valitsin netinst amd64 CD imagen.

Muistin määräksi asetin 4096 MB, ja prosessorien määrän asetin 4:ään. Loin uuden virtuaalikovalevyn ja määritin sille 20GB muistia.

![Asennus1](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/asennus1.png)
![Asennus2](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/asennus2.png)
![Asennus3](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/asennus3.png)

Käynnistettyäni virtuaalikoneen, alkoi asennusprosessi.

Asennuksen käyttöliittymä oli hieman erilainen kuin aiemmin asentamani Debian 12.1.0.

Valitsin kieleksi englannin, lokaatioksi United States, ja näppäimistöksi suomalaisen näppäimistön.

Näiden valintojen jälkeen loin root-käyttäjän sekä peruskäyttäjän ilman admin-oikeuksia.

Lisäksi minun piti määritellä haluamani levyn osiointi (partition). Valitsin tähän käytettäväksi koko kovalevyn, sekä että kaikki tiedostot olisivat yhdellä osiolla. Mikäli kone olisi tulossa itselleni päivittäiseen käyttöön, olisin mahdollisesti erottanut ainakin /home-hakemiston omaan osioonsa.

![Osiot](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/osiot.png)

Tämän jälkeen käyttöjärjestelmä jatkoi asennusta, ja n. 5sek jälkeen minulta kysyttiin mistä haluan peilata(?) paketinhallinnan. Valitsin Suomen, ja paketinhallinnaksi deb.debian.org:in. Luulen että tässäkin olisi suositeltavaa valita joku muu maa mikäli kone tulisi pitkäaikaiseen käyttöön.

![Paketinhallinta valikko](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/package_manager.png)

Lopuksi minulta kysyttiin vielä valinnaisten softien asennusta, mutta koneen ollessa laboratorioharjoituskäytössä jätin asentamatta mitään ylimääräistä.

![Softa valinnat](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/softa_valinnat.png)

Tämän jälkeen sovelluspakettien latauksessa ja asennuksessa meni n.2min, jonka jälkeen minulta kysyttiin haluanko asentaa GRUB boot loaderin. Tämä oli oletuksena valittuna, joten valitsin kyllä.

Kaiken tämän jälkeen pääsin vihdoinkin kirjautumaan tunnuksillani sisään. Avaamalla Firefox-selaimen totesin että verkkoyhteys toimii. Yritin myös päivittää paketinhallinnan vain todetakseni että käyttäjältäni puuttuu sudo-oikeudet. Tämän korjasin vaihtamalla itseni root-käyttäjäksi, ja lisäämällä käyttäjäni sudo-ryhmään komennolla `usermod -aG sudo osku`.

Kun ryhmään lisäys tuli voimaan, päivitin paketinhallinnan ja asennetut paketit komennoilla `sudo apt-get update` ja `sudo apt-get upgrade`.

Palomuurin asensin komennolla `sudo apt-get install ufw -y` ja otin sen käyttöön komennolla `sudo ufw enable`.

Nyt virtuaalikoneen pitäisi olla valmis laboratorioharjoitusta varten.

<h2>Lähteet</h2>

- - Debian s.a. Installing Debian 12.2. https://www.debian.org/releases/bookworm/debian-installer/
- Karvinen, T 2018. Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04. Luettavissa: https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/. Luettu 07.10.2023
- Tyson, M 2022. What is the JDK? Introduction to the Java Development Kit. Luettavissa: https://www.infoworld.com/article/3296360/what-is-the-jdk-introduction-to-the-java-development-kit.html. Luettu 07.10.2023
- Wikipedia s.a. Shebang (Unix). Luettavissa: https://fi.wikipedia.org/wiki/Shebang_(Unix). Luettu: 08.10.2023
