x) Oma tiivistelmäni Tero Karvisen artikkelista [Command line basics revisited](https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited).

- `sudo` komento antaa korkeimmat mahdolliset oikeudet. Sitä tarvitaan kaikkiin komentoihin jotka vaikuttavat järjestelmään kokonaisvaltaisesti. Asetetaan komennon eteen, esim. `sudo apt-get update`
- joitain komentoja hakemistossa liikkumiseen: `pwd` = tulostaa työskentelyhakemiston, `ls` = listaa tiedostot työskentelyhakemistossa
- Tärkeitä hakemistoja, joita kaikkien pitäisi muistaa ovat juurihakemisto `/`, kaikkien käyttäjien kotihakemisto `/home/` ja `/var/log/` johon tallentuu kirjaukset kaikesta mitä järjestelmässä on tapahtunut

a) Micro-editorin asennus

Aloitan asennusprosessin päivittämällä Linuxin pakettihakemiston komennolla `sudo apt-get update`, jonka jälkeen syötän komennon `sudo apt-get -y install micro`. 

[Micro-editorin asennus](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/micro_asennus1.png)

Lisäämällä komentoon tuon `-y`-kohdan, käsken komentoriviä vastaamaan kaikkiin "tyhmiin" kysymyksiin kyllä, jolloin asennus käynnistyy heti.

[Micro-editori käytössä](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/micro_editori.png)
