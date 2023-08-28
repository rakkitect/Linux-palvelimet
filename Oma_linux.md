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

Ladattuani Debianin .iso-tiedoston, käynnistin Virtualboxin, ja aloitin uuden virtuaalikoneen luomisen painamalla "New". Nimesin virtuaalikoneen "DebianOskuHeikkinen" ja valitsin ladatun .iso-tiedoston. Valitsin täpän "Skip Unattended Installation" ja jatkaakseni painoin "Expert Mode", sillä ilmeisesti muuten asennus ei onnistu (lähde: https://terokarvinen.com/2021/install-debian-on-virtualbox/)


