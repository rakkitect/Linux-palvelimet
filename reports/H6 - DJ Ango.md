<h1>H6 - DJ Ango</h1>

<h2>x) Lue ja tiivistä artikkelit</h2>

<h3>Karvinen 2023 - Python Web - Idea to Production</h3>

- Artikkelissa rakennetaan weppipalvelu joka:
  - toimii yleisimmillä käyttöjärjestelmillä, sekä millä vain selaimella
  - ei vaadi käyttäjältä asennusta
  - ei vaadi käyttäjiltä manuaalisia päivityksiä, vaan käyttää uusinta versiota automaattisesti
  - palvelee samanaikaisesti useampaa käyttäjää

<h3>Karvinen 2022 - Django 4 Instant Customer Database Tutorial</h3>

- Artikkelissa luodaan tietokanta sekä käyttöliittymä jossa sitä voi hallita
- Terminaalissa tehdyt tietokannat pitää rekisteröidä käyttöliittymään Pythonia käyttäen

<h3>Karvinen 2022 - Deploy Django 4 - Production Install</h3>

- Tuotantoversio luodaan Apache2 verkkopalvelimelle. Se on maailman suosituin verkkopalvelin!
- `requirements.txt` kirjataan tarvittavat sovelluspaketit, joiden asennus virtualenv-ympäristössä onnistuu yhdellä komennolla `pip install -r requirements.txt`
- Tuotantoversiossa on fiksua poistaa "DEBUG"-tila pois käytöstä, jotta hyökkääjät eivät saisi tietoa sivujemme heikkouksista suoraan meiltä
- Ottaessa Python-ohjelmia käyttöön Apache-palvelimella, tulisi sinulla olla tiedossa seuraavat hakemistopolut:
  - Django-projektin päähakemisto, jossa sijaitsee `manage.py`
  - Polku tiedostoon `wsgi.py`
  - "Virtualenv site-packages" hakemisto

<h2>a) Asenna Django-kehitysympäristö niin, että näet './manage.py runserver' esimerkkisivun.</h2>

Ennen mitään asennuksia, aloitan päivittämällä paketin hallinnan: `sudo apt-get update`, sekä päivitän jo asennetut paketit: `sudo apt-get upgrade`.

Seuraavaksi asennan eristetyn "virtualenv"-ympäristön komennolla `sudo apt-get -y install virtualenv`.

Luon env/-hakemiston komennolla `virtualenv --system-site-packages -p python3 env/`, joka sisältää ajan tasalla olevat sovelluspaketit.

![Virtualenv](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/virtual_env.png)

Virtualenv-ympäristön aktivointi tapahtuu komennolla `source env/bin/activate`, jonka jälkeen komentokehote saa alkupäätteen (env)

![Alkupääte](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/alkup%C3%A4%C3%A4te.png)

Luon "micro"-tekstieditorilla tiedoston "requirements.txt" johon listaan tarvittavat asennuspaketit, eli tällä kertaa vain Djangon. Komentoa `pip install -r requirements.txt` käyttäen, Django asentuu virtualenv-hakemistoihin mikäli virtualenv on aktiivinen. Komennolla `django-admin --version` tarkistamme että saamamme versio on uusin, eli raportin julkaisuaikana 4.2.5

![requirements.txt](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/requirements.png)

Loin Django-projektini nimellä "Oskuco" komennolla `django-admin startproject oskuco`.

Palvelin käynnistetään näin:
```
$ cd oskuco
$ ./manage.py runserver
```
![Runserver](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/runserver.png)

Punaisella tekstillä näkyvä teksti johtuu luullakseni siitä että tietokantoja ei ole päivitetty. Se korjataan seuraavan vaiheen jälkeen.

Käynnistettyäni palvelimen, otin siihen yhteyden selaimella syöttämällä URL:in http://127.0.0.1:8000/

![Django interface](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/django_interface.png)

Tietokannat päivitetään komennolla `.manage.py migrate`
```
$ ./manage.py makemigrations
$ ./manage.py migrate
```

![Migration](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/migrations.png)

<h2>b) Yksinkertainen esimerkkitietokanta Django-kehitysympäristöön ja niiden muokkaus admin-käyttöliittymässä</h2>

Edellisen vaiheen jälkeen voin lisätä admin-käyttöliittymän. Sitä varten tarvitsen admin-käyttäjän. Aloitan tunnusten luonnin asentamalla salasana-generaattorin komennolla `sudo apt-get install pwgen`. Komennolla `pwgen -s 20 1` sovellus luo yhden 20 merkkiä pitkän satunnaisen salasanan.

Superuser-käyttäjä luodaan komennolla `./manage.py createsuperuser`. Tunnusten luonnissa kysytään tunnuksen nimeä, sähköpostia ja salasanaa. Sähköposti ei ollut pakollinen, ja itse jätin sen tyhjäksi (saa nähdä seuraako tästä ongelmia myöhemmin)

Tietokannan luominen alkaa komennolla `./manage.py startapp crm` joka luo kansion crm/ jonne asennetaan Customer Relationship Management sovellus. Asennus pitää lisätä Pythonin asetus-tiedostoon komennolla `micro oskuco/settings.py`. Lisätty rivi on korostettu:

![crm](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/crm.png)

Tämän jälkeen komennolla `micro crm/models.py ` voin tuoda "Customer"-taulun lisäämällä Python-tiedostoon halutut speksit:

![Database](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/database.png)

Siirtäessäni juuri luomaani tietokantaa palvelimelleni, tuli `./manage.py makemigrations`-komennon yhteydessä virheilmoitus puuttuvasta "("-merkistä "Customer"-taulussa. Korjauksen jälkeen migraatio sujui ongelmitta.

![database_migration](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/database_migration.png)

Luomisen jälkeen tietokanta pitää rekisteröidä, jotta sen näkee admin-käyttöliittymässä. Muutos tehdään Microlla `admin.py`-tiedostoon.

![register](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/register.png)

Rekisteröinnin jälkeen tietokanta tulee näkyviin:

![CRM_database](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/crm_database.png)

Saan lisättyä asiakkaita tietokantaan admin-käyttöliittymän kautta painamalla "Add customer +" painiketta CRM-näkymän yläreunasta. Kuvassa näkyy jo kaksi kappaletta luomiani rivejä.

![customers](https://github.com/rakkitect/Linux-palvelimet/blob/main/images/customer.png)

<h2>c) Tee Djangon tuotantotyyppinen asennus omalle, paikalliselle virtuaalikoneellesi. Siis sellainen, joka pyörii Apachella. Tämä tehtävä on hieman haastavampi.</h2>

Valitettavasti tämä tehtävä jäi omalta osaltani tekemättä ajanpuutteen takia, mutta aion sen toteuttaa paremmalla ajalla.


<h2>Lähteet</h2>

- Karvinen, T 2023. Python Web - Idea to Production. Luettavissa: https://terokarvinen.com/2023/python-web-idea-to-production/#osaamistavoitteet. Luettu: 01.10.2023
- Karvinen, T 2022. Django 4 Instat Customer Database Tutorial. Luettavissa: https://terokarvinen.com/2022/django-instant-crm-tutorial/. Luettu 01.10.2023
- Karvinen, T 2022. Deploy Django 4 - Production Install. Luettavissa: https://terokarvinen.com/2022/deploy-django/. Luettu 01.10.2023
