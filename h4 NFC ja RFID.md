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

   Lomapakossa oleva(t) kortit ovat pääosin huonosti suojattuja, koska lompakko ei varsinaisesti suojaa. Näin ollen kortin lukeminen onnistuisi helposti, mikäli laite olisi          riittävän lähellä. Tässä on kyse heikosta suojauksesta.Vähemmän heikko, tai kohtalainen korttisuojaus on mahdollinen, mikäli kortit ovat lompakossa päällekkäin. Tämä häritsisi    signaalia yksittäisen kortin kohdalla. Tästä voidaan päätellä, että kortit ovat huonosti suojattuja.

   Älypuhelin on vahvasti suojattu, sikäli siihen kirjautuminen vaatii esimerkiksi tunnistautumisen. Lisäksi puhelin on suojattu tietoturvapaketilla.

2. Tutustu APDU komentojen rakenteeseen (voit käyttää tekoälyä tutustumiseen)

   Tutustuin aiheeseen syöttämällä APDU:n Googlen tekoälyyn. Tämän jälkeen etsin YouTubesta aiheeseen liittyviä videoita. Hakutuloksena löytyi yksi video, joka sisältää seitsemän
   slidia, eli lyhen esitelmän liittyen teemaan. Lähde: https://www.youtube.com/watch?v=1YBkkdM1tKU.

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
   
3. Tutki ja kerro minkä mielenkiintoisen RFID hakkerointi uutiset löysit. (Vinkki, useimmat liittyvät henkilökortteihin)

   Iltasanomien digijulkaisu otsikolla: 15 euroa riitti murtamaan asuntojen hienot sähkölukot

   Digijulkaisu on julkaistu 31.12.2013. Julkaisussa kerrotaan Itävaltalaisesta henkilöstä, joka onnistui murtamaan sähköisen avainkorttijärjestelmän. Lisäksi Artikkeli             älykorttien (myös henkilökorttien) sirujen tietoturvaa ja APDU-komentoihin liittyvää tutkimusta. Ilta-Sanomien Digitoday julkaisu käsittelee älykorttien tietoturvaa.             Tutkimuksessa analysoitiin, miten APDU-komennoilla voidaan kommunikoida kortin sirun kanssa ja tutkia sen toimintaa. Tutkimus todisti sen, että haavoittuvuuksien löytäminen      ei aiheuttanut välitöntä vaaraa käyttäjille, mutta se ei ole turvallinen verrattuna perinteisiin avaimeen, kuten Iloq.

   Artikkelin julkaisusta on 13 vuotta, mutta se on mielenkiintoinen. En löytänyt julkaisun alkuperäistä lähdettä.

   






   


Lähde
===


YouTube. Understanding the APDU Command Variance in Personal ID Card Readers. Katsottu: 14.4.2026. Katsottavissa: https://www.youtube.com/watch?v=1YBkkdM1tKU. 


   
