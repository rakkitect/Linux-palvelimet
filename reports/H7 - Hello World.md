<h1>H7 - Hello World</h1>

<h2>x) Linkit aikaisempiin läksyihin</h2>

- [H1 - Oma Linux](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H1%20-%20Oma_linux.md)
- [H2 - Komentaja Pingviini](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H2%20-%20Komentaja%20Pingviini.md)
- [H3 - Hello Web Server](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H3%20-%20Hello%20Web%20Server.md)
- [H4 - Maailma Kuulee](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H4%20-%20Maailma%20kuulee.md)
- [H5 - Nimittäin](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H5%20-%20Nimitt%C3%A4in.md)
- [H6 - DJ ANGO](https://github.com/rakkitect/Linux-palvelimet/blob/main/reports/H6%20-%20DJ%20Ango.md)

<h2>y) Lue ja tiivistä</h2>

- `Hello World!` on yleinen tapa testata ohjelmointikielen toimivuus.
- Itselleni relevantit kielet lienee: Python 3, Java, C
  - Nämä sen takia, että mielenkiintoni raportin kirjoitushetkellä kohdentuu kyberturvallisuuteen
- Ohjelmointikielet löytyvät Linuxilla paketinhallinnasta komennolla `apt-get`


<h2>a) Käännä "Hei maailma" Pythonilla, Javalla ja C-kielellä. (Kirjoita lähdekoodi erilliseen tiedostoon, vaikka Pythonissa onkin interaktiivinen tulkki [REPL]).</h2>

Tässä tehtävässä minun pitää asentaa kääntäjät (compiler) Pythonia, Javaa ja C:tä varten, joten ensimmäisenä päivitän paketinhallinan sekä asennetut paketit komennoilla `sudo apt-get update` ja `sudo apt-get upgrade`. Edeltävä komento päivittää paketinhallinan valikoiman uusimpiin versioihin, ja jälkimmäinen lataa päivitykset Linux-ympäristööni asennettuihin paketteihin.

Koneellani oli valmiiksi jo kääntäjät C:lle ja Pythonille, mutta asennukset olisin tehnyt komennoilla `sudo apt-get install python3` ja `sudo apt-get install gcc`. Javaa varten en ollut asentanut kääntäjää, joten sen asensin komennolla `sudo apt-get install default-jdk`. Löysin tarvittavan paketin komennolla `sudo apt-cache jdk`. "JDK" on lyhenne sanoista Java Development Kit, jonka mukana tulee kääntäjä ja yleisimmät luokka kirjastot (class libraries).

Python3:
- Loin hello.py tiedoston "Micro"-tekstieditorilla käyttäen komentoa `micro hello.py`
- Koodi pyöritetään komennolla `python3 hello.py`
![Hello World Pythonilla](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/hello_python.png)
  
Java:
- Loin hello.java tiedoston "Micro"-tekstieditorilla käyttäen komentoa `micro hello.java`
- Javalla on tärkeää että tiedoston nimi on sama kuin koodissa oleva luokka, joten tiedoston ollessa "hello.java" nimesin luokan myös "hello"
  - Tämä on "case sensitive", eli kirjainkoolla on väliä.
- Tiedoston luonnin jälkeen, koodi piti vielä kääntää komennolla `javac hello.java`
- Tämän jälkeen pystyin pyörittää koodin terminaalissa komennolla `java hello`
![Hello World Javalla](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/hello_java.png)

C:
- Loin hello.c tiedoston "Micro"-tekstieditorilla käyttäen komentoa `micro hello.c`
- Kun koodi on kirjoitettu, se pitää kääntää komennolla `gcc hello.c -o helloc`
  - `-o helloc`
 
<h2>b) Käännä "Hei maailma" jollain muulla kielellä (kuin Python, Java, C).</h2>



<h2>c) Esittele Pythonin käyttöä interaktiivisena taskulaskimena. Voit käyttää myös Jupyteria, eli ipython3-liittymää.</h2>

<h2>d) Tee shell script.</h2>

<h2>e) Tee uusi komento Linuxiin. Osoita, että se toimii kaikilla käyttäjillä ja ilman, että tarvitsee kirjoittaa polkua tuohon komentoon. (Voit käyttää esimerkkiohjelmana äsken tekemääsi shell scriptiä)</h2>

<h2>f) Intelligent intelligence. Ratkaise vanha arvioitava laboratorioharjoitus tältä kurssilta. Saa soveltaaa. Jos harjoituksessa on kohtia, jotka ovat liian vaikeita tai kovin erilaisia kuin tällä toteutuksella opetetut, voit vaihtaa ne sopivampaan tai jopa hypätä niiden yli.</h2>

<h2>g) Asenna arvioitavaa laboratorioharjoitusta varten itsellesi uusi tyhjä virtuaalikone. Suosittelen Debian 12-Bookworm, amd64. Koneella saa halutessasi olla paketit päivitettynä ja palomuuri asennettuna. Koneella ei saa olla näiden lisäksi muita asetuksia ja ohjelmia kuin ne, jotka tulivat tavalliesn asennuksen yhteydessä. Katso, että koneella on toimiva nettiyhteys, riittävästi kovalevytilaa ja RAM-muistia. Virtuaalikoneella ei saa olla luottamuksellisia tietoja.</h2>

<h2>h) Vapaaehtoinen: Tee Linxuiin uusi komento Pythonilla.</h2>

<h2>i) Vapaaehtoinen: Tee Linxuiin uusi komento Javalla. Voit käyttää shell scriptiä käynnistämään java-ohjelmasi, 'cd /opt/iloveobjects/; java ILoveObjects'.</h2>

<h2>j) Vapaaehtoinen: Tee Linuxiin uusi komento jollain muulla kielellä kuin Javalla tai Pythonilla.</h2>

<h2>Lähteet</h2>

- Karvinen, T 2018. Hello World Python3, Bash, C, C++, Go, Lua, Ruby, Java – Programming Languages on Ubuntu 18.04. Luettavissa: https://terokarvinen.com/2018/hello-python3-bash-c-c-go-lua-ruby-java-programming-languages-on-ubuntu-18-04/
- Tyson, M 2022. What is the JDK? Introduction to the Java Development Kit. Luettavissa: https://www.infoworld.com/article/3296360/what-is-the-jdk-introduction-to-the-java-development-kit.html. Luettu 07.10.2023
