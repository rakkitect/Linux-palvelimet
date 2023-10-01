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



<h2>Lähteet</h2>

- Karvinen, T 2023. Python Web - Idea to Production. Luettavissa: https://terokarvinen.com/2023/python-web-idea-to-production/#osaamistavoitteet. Luettu: 01.10.2023
- Karvinen, T 2022. Django 4 Instat Customer Database Tutorial. Luettavissa: https://terokarvinen.com/2022/django-instant-crm-tutorial/. Luettu 01.10.2023
- Karvinen, T 2022. Deploy Django 4 - Production Install. Luettavissa: https://terokarvinen.com/2022/deploy-django/. Luettu 01.10.2023
