NFC ja RFID
===

###### 13.4.2026.
###### 17:00


Järjestelmä:

Järjestelmän malli: Aspire E5-573G

Käyttöjärjestelmä: Microsoft Windows 11 Home

Suoritin: Inter(R) Pentium(R) 3558U @ 1.70GHz. Mhz, 2 ydin(tä)

Muisti: 6.00 Gt asennettua fyysistä muistia

Oracle Virtualbox

Debian 13 (trixie)

###### 14.4.2026
###### 20:12 

Kotitehtävät
===

1. Tarkastele käytössäsi olevia RFID tuotteita, mieti miten hyvin olet suojautunut RFID urkinnalta?

Lomapakossa olevat kortit ovat pääosin huonosti suojattuja, koska nahkalompakko ei varsinaisesti suojaa. Näin ollen kortin lukeminen onnistuisi helposti, mikäli laite olisi      riittävän lähellä. Tässä on kyse heikosta suojauksesta. Laadultaan hiekompi suojaus tapahtuu, kun kortit ovat lähekkäin tai päällekkäin lompakossa, jolloin se häiritsisi urkintaa yksittäisen kortin kohdalla. Tästä voidaan tulla siihen päätelmään, että tavalliset kortit lompakossa ovat huonosti suojattuja, ja näin ollen vaarassa.

(Korjattu: 7.5.2026)

Älypuhelin on vahvasti suojattu, sillä kirjautumiseen vaaditaan tunnistautumisen lisäksi salasana. Lisäksi puhelin on suojattu tietoturvapaketilla, mikä lisää turvallisuutta, mutta ei poista sitä mahdollisuutta, että siihen voidaan kohdistaa urkintaa.

(Korjattu: 7.5.2026.)

2. Tutustu APDU komentojen rakenteeseen (voit käyttää tekoälyä tutustumiseen)

APDU kometojen tutustumiseen käytin Googlen tekoälyä. Tämän jälkeen etsin YouTubesta aiheeseen liittyviä videoita. Hakutulos osoittaa hyvin suppean määrän videoita ja eri kielillä, mutta löysin yhden, joka sisältää seitsemän slidia. Tämä video sisältää hyvin lyhyen esitelmän liittyen kyseiseen teemaan. Lähde: https://www.youtube.com/watch?v=1YBkkdM1tKU.

(Korjattu: 7.5.2026.)
   
   Lyhyt tiivistelmä

   APDU (Application Protocol Data Unit) on viestimuoto, jota käytetään älykortin ja lukijalaitteen välillä.

   Command APDU = laite lähettää käskyn kortille
   Response APDU = kortti vastaa ja kertoo onnistuiko toiminto

   👉 Käytetään esim. maksukorteissa, SIM-korteissa ja NFC-teknologiassa. (Lähde: ChatGBT)

   APDU komento koostuu yleensä näistä kentistä:

    CLA | INS | P1 | P2 | Lc | Data | Le

   <img width="1536" height="1024" alt="Image" src="https://github.com/user-attachments/assets/9e78771b-7917-42b9-9ae3-827515748aeb" />

   Kuva 1. APDU-komennot. Lähde: ChatGPT

   <img width="1024" height="1536" alt="Image" src="https://github.com/user-attachments/assets/64c48482-c8c0-4d84-b0b7-22655e80f555" />

   Kuva 2. APDU-komennot ja statuskoodit. Lähde: ChatGPT

###### 14.4.2026
###### 21:35 

###### 15.4.2026.
###### 17:05 
   
4. Tutki ja kerro minkä mielenkiintoisen RFID hakkerointi uutiset löysit. (Vinkki, useimmat liittyvät henkilökortteihin)

   Iltasanomien digijulkaisu otsikolla: 15 euroa riitti murtamaan asuntojen hienot sähkölukot

   Wieniläinen Adrian Dabrowski osoitti Chaos Communication Congressissa, kuinka haavoittuvia sähköiset avainkorttijärjestelmät ovat, murtaen alle 15 euron korttisimulaattorilla    jopa 93 % Begeh Schließsysteme -lukoista. Tutkimus paljastaa, että skannaamalla postinkantajan RFID-signaali, järjestelmästä saadaan avattua merkittävä osa ovista, eikä          sähköistä lukkoa ole mahdollista päivittää turvallisemmaksi murtamisen jälkeen. Lisäksi artikkelissa mainitaan, että vuonna 2011 tutkijat olivat onnistuneet avaamaan
   vankilasellin ovet etänä. (Lähde: Ilta-Sanomat)

Tämän uutisen alkuperäistä lähdettä ei löytynyt googlettamalla. Uutinen on vuodelta 2013.

(Päivitetty: 7.5.2026.)

   

###### 15.4.2026.
###### 17:57




   


Lähde
===

Google Gemini 2026. Tekoälyä käytetty APDU tehtävässä. Lähde: https://gemini.google.com/app. Käytetty: 14.4.2026.

Ilta-Sanomat 31.12 2013. Artikkeli. 15 euroa riitti murtamaan asuntojen hienot sähkölukot. Luettavissa: https://www.is.fi/digitoday/art-2000001821216.html. Luettu: 14.4.2026.

YouTube. Understanding the APDU Command Variance in Personal ID Card Readers. Katsottu: 14.4.2026. Katsottavissa: https://www.youtube.com/watch?v=1YBkkdM1tKU. 


   
