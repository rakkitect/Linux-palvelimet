Raportin kirjoittaminen:
- Raportissa kerrotaan mitä tehtiin, ja mitä sen seurauksena tapahtui
- Mikäli joku muu toistaa raportissasi tehtävät toimenpiteet, heidän pitäisi päästä samaan lopputulokseen kuin sinä
- Täsmällisyys ja selkeä teksti ovat tärkeitä

What is Free software?
- Käyttäjillä on oikeus käyttää, kopioida, jakaa, tutkia, muuttaa ja parantaa ohjelmistoa niin kuin he haluavat
- Mikäli ohjelmisto ei anna käyttäjille kaikkia näitä vapauksia, sitä ei voi kutsua vapaaksi ohjelmistoksi
- Vapaa, ei välttämättä ilmainen
- Vapaan ohjelmiston pitää olla käytettävissä myös kaupallisesti

Linuxin asennus
Tässä raportissa käyn läpi Linuxin asentamisen Oracle Virtualbox virtuaalikoneelle. Käyttämäni Virtualbox versio on 7.0.10.
Ympäristönä toimii W10 versio 10.0.19045, ja oleelliset tiedot raudasta ovat:
- Prosessori: AMD Ryzen 7
- RAM: 16GB

Latasin raporttiin käytettävän Linux version täältä: https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/debian-live-12.1.0-amd64-xfce.iso

Ladattuani Debianin .iso-tiedoston, käynnistin Virtualboxin, ja aloitin uuden virtuaalikoneen luomisen painamalla "New". Nimesin virtuaalikoneen "DebianOskuHeikkinen" ja valitsin ladatun .iso-tiedoston.

Valitsin täpän "Skip Unattended Installation" ja jatkaakseni painoin "Expert Mode", jotta pääsen valitsemaan 64-bittisen version (lähde: https://terokarvinen.com/2021/install-debian-on-virtualbox/)

![Virtual Machine Creation](https://github.com/rakkitect/Linux-palvelimet/blob/main/Debian0.png)

Hardware-valintoja tehdessä muutin muistin määrän 4GB, ja prosessorien määrän pidin yhdessä.

![Virtual Machine Creation](https://github.com/rakkitect/Linux-palvelimet/blob/main/debian2.png)

Virtuaalista kovalevyä luodessa asetin kovalevyn koon 20GB, ja muuten pidin asetukset oletuksena. Tässä vaiheessa ei annettu vaihtoehtoa asettaa kovalevyä allokoimaan dynaamisesti, joten toivon että se on oletuksena.

![Virtual Machine Creation](https://github.com/rakkitect/Linux-palvelimet/blob/main/debian3.png)

Näiden valintojen jälkeen painoin "Finish", ja virtuaalikone tuli näkyviin Virtualboxiin vasempaan reunaan.

Tämän jälkeen olin menossa asettamaan ISO-kuvaketta virtuaaliseksi levyksi, mutta omalla kohdallani se oli valmiiksi valittuna.

(https://github.com/rakkitect/Linux-palvelimet/blob/main/debian4.png)

Käynnistin juuri luodun virtuaalisen koneen valitsemalla sen Virtualboxin vasemmasta reunasta, ja painamalla "Start" yläreunasta.

Käynnistettyäni virtuaalikoneen, tuli näkyviin bootloader josta valitsin "Live system (amd64). Valitsemalla live-systeemin voin tarkistaa kaiken toimivan.

![Virtual Machine Creation](https://github.com/rakkitect/Linux-palvelimet/blob/main/debian5.png)

Koneen käynnistyttyä kokeilin selainta, ja se toimi niinkuin pitikin joten etenin asentamaan käyttöjärjestelmää laukaisemalla työpöydältä "Install Debian". Jouduin suorittamaan lopullisen asennuksen ilman virtalähdettä, ja ilmeni varoitus että kaikki toiminnot eivät ole käytössä.

Seuraavaksi luettelen tekemäni valinnat/muutokset asennuksen aikana. Mikäli jotain ei ole mainittu niin olen valinnut oletuksena olevan valinnan.

- Kieli: American English
- Lokaatio: Suomi (valittu painamalla karttaa)
- Näppäimistö: Generic 105-key PC)
- Erase disk: Kyllä
- Käyttäjän nimi: Osku Heikkinen
- Käyttäjä: oskuh

Yhteenvedon jälkeen maksimoin virtuaalikoneen sisäisen ruudun, ja painoin "Install"

![Virtual Machine Creation](https://github.com/rakkitect/Linux-palvelimet/blob/main/debian6.png)

Vaikka tietokoneeni ei ollut virtalähteessä, asennus meni läpi ilman mitään ongelmia.

