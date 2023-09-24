<h1>H5 - Nimittäin</h1>

<h2>x) Lue ja tiivistä</h2>

- Karvinen 2016: New Default Website with Apache2 – Show your homepage at top of example.com, no tilde
- Karvinen 2018: Name Based Virtual Hosts on Apache – Multiple Websites to Single IP Address
- Apache Software Foundation 2023: Name-based Virtual Host Support

a) Vuokraa domain-nimi ja aseta se osoittamaan virtuaalipalvelimeesi.*

Vuokrasin tätä tehtävää varten domain-nimen domain.com palvelusta. Lopulliseksi vuosihinnaksi osoitteelleni tuli 1.23$, elikkä noin 1.15€. Alkuperäinen hinta oli 0.99$, mutta Ameriikan tapaan verojen määrä ilmoitettiin vasta loppuvaiheessa.

![Ostoskori]

Domain.comin käyttöliittymä oli melko vaikeasti suunnistettavissa, mutta pienen odottelun ja Googlettamisen jälkeen pääsin kuin pääsinkin muuttamaan DNS-asetuksia. Tätä kautta saan ostamani domain-nimen osoittamaan Apache2-palvelimeni IP-osoitteeseen.

![DNS asetukset]

Tässä vaiheessa minulle ilmoitettiin, että muutoksien voimaan tulossa saattaa mennä jopa 24-48 tuntia, joten tässä raportissa en sitä varmaan pääse todistamaan (sunnuntaina 24.09 klo 22.04)

b) Tutki oman nimesi tietoja 'host' ja 'dig' -komennoilla. Analysoi tulokset.

[Host ja Dig komennot]

`host rakkitehti.space` tulosti IP-osoitteet joihin kyseinen domain-nimi osoittaa, sekä mikä sähköpostipalvelin vastaanottaa tälle domain-nimelle lähetetyt sähköpostit.
`dig rakkitehti.space` tulostaa paljon laajemman raportin. 

c) Etusivu uusiksi. Name based virtual hosting. Laita kotisivusi näkymään oman palvelimen etusivulla. Sivujen tulee olla tallennettu jonnekin kotihakemistojen alle ja olla muokattavissa ilman sudoa.
