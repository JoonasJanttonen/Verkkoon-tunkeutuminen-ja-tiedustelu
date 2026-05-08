###### 4.5.2026.
###### 16:17


Aaltoja harjaamassa
===

Järjestelmä:

Järjestelmän malli: Aspire E5-573G

Käyttöjärjestelmä: Microsoft Windows 11 Home

Suoritin: Inter(R) Pentium(R) 3558U @ 1.70GHz. Mhz, 2 ydin(tä)

Muisti: 6.00 Gt asennettua fyysistä muistia

Oracle Virtualbox

Debian 13 (trixie)

Koneen päivittämistä ennen tehtävien työstämistä.
```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get -y dist-upgrade
sudo apt-get -y install ufw \
sudo ufw enable 
```

```
sudo timedatectl set-timezone Europe/Helsinki
sudo timedatectl
set-ntp true
```




Kotitehtävät
===

x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)


Hubacek 2019: Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs (Video, alkaen 3:19 ja päättyen 7:40. Yhteensä noin 4 min.)

- Universal Radio Hackerillä voidaan tallentaa signaalia tiedostoksi hyödyntämällä spektrianalysaattoria.
- Signaali voidaan purkaa bittimuotoon säätämällä modulaatiota.
- Data muunnetaan Hex-koodiksi myöhempää toistoa varten.

Cornelius 2022: Decode 433.92 MHz weather station data

- SDR-laitteisto ja URH-ohjelmisto mahdollistavat ASK-moduloitujen 433 MHz:n signaalien analysoinnin ja toisintamisen helposti Arduino-pohjaisilla ratkaisuilla.
- Tallennetut signaalit voidaan purkaa vastaanottimella tai vaihtoehtoisesti analysoida Audacity-ohjelmistolla SSB-demodulaation jälkeen.  
- 36-bittistä tiedonsiirtoa ei ole mahdotonta purkaa. 

(Tekstissä on paljon uutta sanastoa, joten apuna käytin Google Kääntäjää ja Google Geminiä lukiessani käännöstä. Tässä tehtävässä sovellettiin tekoälyä.

Vapaaehtoinen, vaikeahko: Lohner 2019: Decoding ASK/OOK_PPM Signals with URH and rtl_433

- Universal Radio Hacker (URH) ja rtl_433 sovelluksien avulla voidaan purkaa esim. sääasmien signaaleja ja langattomia ovikelloja. 
- Teksti osoittaa, että digitaalinen radioliikenne perustuu tarkkaan ajoitukseen.
- Informaatio ei ole itse pulsseissa, vaan niiden välimatkassa.

(Tässä osiossa hyödynsin (kääntäjänä) Google Geminiä).

###### 4.5.2026.
###### 18:57

###### 7.5.2026.
###### 17:08 

a) Lähteet ja läppä. Tarkista, että jokaisessa kotitehtäväraportissasi on viitattu lähteisiin (kurssiin, tehtäviin, kirjoihin, ohjeisiin...). Tarkista myös, että tekoälyn käyttö on kerrottu läpikyvästi ja merkitty lähteisiin. Laita läppäri valmiiksi lipunryöstöön. Opettaja voi tarkistaa läppärin. Jos käytät lipunryöstössä pelkästään virtuaalikonetta (myös weppiselailun), tarkastan vain virtuaalikoneen. Tätä alakohtaa a ei tarvitse raportoida, pelkkä kuittaus tekemisestä riittää.

OK.

###### 18:10 
###### 18:28
b) rtl_433. Asenna rtl_433 automaattista analyysia varten. Kokeile, että voit ajaa sitä. './rtl_433' vastaa "rtl_433 version 25.02 branch..."

Ennen asentamista varmistan sudo apt-get update, että kone ohjelmat ovat ajantasalla. Tämän jälkeen asennan rtl_433 komennolla:

```
sudo apt update
sudo apt install rtl-433

```

Tarkistan, että päivitys on onnistunut komennolla:

```
rtl_433 -V
```

<img width="358" height="11" alt="Image" src="https://github.com/user-attachments/assets/0082ce4d-252d-4694-aac9-cb05b13cb64e" />

Kuva 1. Näkymä terminaalissa.

###### 7.5.2026.
###### 18:35

###### 18:45

c) Automaattinen analyysi. Mitä tässä näytteessä tapahtuu? Mitä tunnisteita (id yms) löydät? Converted_433.92M_2000k.cs8. Analysoi näyte 'rtl_433' ohjelmalla.

Tiedosto oli tuntematon. Alkuun en saanut avattua tiedostoa. Tämän jälkeen selvitin asiaa googlettamalla. En saanut avattua tiedostoa terminaalista, joten pyysin tekoälyltä opastusta tehtävän suorittamiseen. Lähde: Google Gemini

```
rtl_433 -r /home/jjoonas123/Lataukset/Converted_433.92M_2000k.cs8 -A
```
<img width="400" height="56" alt="Image" src="https://github.com/user-attachments/assets/6ab2e496-ea88-4256-aafb-fa691b4de925" />

Kuva 2. Input

Malli (model): KlikAanKlikUit-Switch / Proove-Security / Nexa-Security
ID / House Code: 8785315 
Kanava (Channel): 3
Yksikkö (Unit): 0 tai 3
Komento (Command/State): Off (pois päältä)
Raakadata (codes): {64}5956955a6995a555

Terminalista huomaan, että avattu tiedosto sisältää radiotaajuista dataa, joka on lähetetty 433.92 MHZ taajuudella käyttäen OOK-modulaatiota (on-off keying). Ohjelma tunnistaa signaalin olevan peräisin kauko-ohjattavasta pistorasiasta tai kytkemisestä.



Näyte sisältää viestejä, kuten toistuvaa lähetystä, jotta se menisi varmasti perille. Nämä merkit ovat (KlikAaanKlikUit, Proove ja Nexa), sillä ne käyttävät samaa protokollaa. Signaali on tyypiltään "Off" -komento eli laite on kytketty pois päältä.

<img width="359" height="154" alt="Image" src="https://github.com/user-attachments/assets/cb3009d1-656b-4c17-b919-e81c8a624755" />

Kuva 3. Näyte.

###### 7.5.2026.
###### 19:35

Tauko

###### 20:26

d) Too compex 16? Olet nauhoittanut näytteen 'urh' -ohjelmalla .complex16s-muodossa. Muunna näyte rtl_433-yhteensopivaan muotoon ja analysoi se. Näyte Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s

Lataan tiedoston: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/.

Seuraavaksi syötän terminaaliin seuraavat komennot:

```
python3 -c "import numpy as np; d = np.fromfile('/home/jjoonas123/Lataukset/Recorded-HackRF-20250411_183354-433_92MHz-2MSps-2MHz.complex16s', dtype='<i2'); (d.astype('float32') / 32768 * 127 + 128).astype('uint8').tofile('/home/jjoonas123/Lataukset/muunnettu_hackrf.cu8')"

```
Analysoidaan tiedosto syöttämällä terminaaliin:

```
rtl_433 -r ~/Lataukset/muunnettu_hackrf.cu8 -s 2000k -A

```

Signaalin tyyppi: Näyte sisältää sarjan voimakkaita (n. 19 dB SNR) OOK-moduloituja radiopurskeita.

Toistuvuus: Paketteja havaitaan useita peräkkäin hyvin lyhyen ajan sisällä (esim. kohdissa 0.127s, 0.134s ja 0.146s)

Modulaation tunnistus: Ohjelma tunnistaa osan paketeista PWM-moduloiduiksi (Pulse Width Modulation), mutta monien kohdalla se ei löydä tunnettua kaavaa ("No clue"). Tämä viittaa siihen, että kyseessä on joko sääasema, auton kauko-ohjain tai muu laite, jonka protokolla on monimutkaisempi kuin perusvirtakytkimillä.

Tästä näytteestä ei löytynyt selkeitä laitetunnisteita (ID, kanava tai malli), koska signaali ei vastannut mitään rtl_433:n valmista purkukoodia.Raakadata: Pulse Analyzer sai poimittua vain lyhyitä bittijonoja, kuten {4}1 ja {6}7c.Tekniset parametrit: Ohjelma tunnisti pulssien pituuksiksi tyypillisesti 12 µs (lyhyt) ja 29 µs (pitkä).

Johtopäätös:

Vaikka tiedosto saatiin muunnettua ja analysoitua, laite on todennäköisesti sellainen, jota ohjelma ei osaa automaattisesti tulkita. Tehtävä on suoritettu siltä osin, että näyte on muunnettu ja sen tekninen sisältö on tutkittu automaattisella analyysilla.

###### 21:13
###### 21:16

###### 8.5.2026.
###### 17:23 

e) Ultimate. Asenna URH, the Ultimate Radio Hacker.

Asennetaan URH, the Ultimate Radio Hacker, Tero Karvisen ohjeiden mukaisesti: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/. 

Sudo oikeudet, komennolla: 

```
Su -
usermod -aG sudo jjoonas123

```
Exit. Uudelleen kirjautuminen terminaaliin.

```
sudo apt-get update
sudo apt-get -y install pipx
pipx install urh --force
pipx ensurepath
sulje ja avaa terminaali
urh
```
<img width="337" height="58" alt="Image" src="https://github.com/user-attachments/assets/d3d4de0b-a344-4b8d-b562-fed84be34a8b" />

Kuva 4. urh


- Tarkastele näytettä 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s. Siinä Nexan pistorasian kaukosäätimen valon 1 ON -nappia on painettu kolmesti. Käytä Ultimate Radio Hacker 'urh' -ohjelmaa.

Lataan tämän ohjelmistojen / tiedostojen kääntämistä varten Tero Karvisen ohjeiden mukaisesti:

```
sudo apt-get -y install atool wget libssl-dev libtool libusb-1.0-0-dev librtlsdr-dev rtl-sdr libsoapysdr-dev
```

```
wget https://github.com/merbanan/rtl_433/releases/download/25.02/rtl_433-soapysdr-openssl3-Linux-amd64-25.02.zip
```

Tässä kohtaan jäin jumiin, kun en saanut pysäytettyä näytettä. Tutustuin ohjelmaan samalla.

<img width="629" height="227" alt="Image" src="https://github.com/user-attachments/assets/eb8c7f28-750b-473f-aaae-0154a74e3d46" />

Kuva 5. HackRF

###### 18:28

f) Yleiskuva. Kuvaile näytettä yleisesti: kuinka pitkä, millä taajuudella, milloin nauhoitettu? Miltä näyte silmämääräisesti näyttää?

Tiedosto: 1-on-on-on-HackRF-20250412_113805-433_912MHz-2MSps-2MHz.complex16s

Tiedoston nimestä päätellen nauhoitusaika on: 12.4.2025. Kello: 11:38:05. 

Taajuus on 433 MHz.

Silmämääräisesti näkyy kolme painallusta, jossa tauot. Kolme painallusta. Näen myös viisi kehystä / viivaa, kun katson signaalia.

g) Bittistä. Demoduloi signaali niin, että saat raakabittejä. Mikä on oikea modulaatio? Miten pitkä yksi raakabitti on ajassa? Kuvaile tätä aikaa vertaamalla sitä johonkin. (Monissa singaaleissa on line encoding, eli lopullisia bittejä varten näitä "raakabittejä" on vielä käsiteltävä)

Modulaatio on ASK/OOK. Analyysissa on 45 näytettä. Demoduloitu raakabittijono on pituudeltaan 68 näytettä. Tehtävän alussa asetin vaakaviivan kohinan yläpuolelle. Signal viewiin asetin: "demodulated". Analysis välilehdelllä asetin Manchester 1.

<img width="640" height="227" alt="Image" src="https://github.com/user-attachments/assets/89c555fe-9120-4892-8525-0351802e18b1" />

Kuva 6. Demoduloitu

###### 18:51 
Tauko
######
h) Vapaaehtoinen: Sdr++. Kokeile sdr++ -sovellusta ja esittele sillä jokin "hei maailma" -tyyppinen esimerkki.







Lähde
===

GitHub 2026. Joonas Janttonen. Läksyt. Luettavissa: https://github.com/JoonasJanttonen/Verkkoon-tunkeutuminen-ja-tiedustelu/blob/main/h6%20WiFi.md. Luettu: 7.5.2026.

GitHub. Karllohner. Decoding ASK/OOK_PPM Signals with URH and rtl_433. Luettavissa: https://github.karllohner.com/SDR/Decoding/Example_2019-01-24/. Luettu: 4.5.2026.

Google Gemini 2026. Käännöksessä käytetty: https://gemini.google.com/app. Luotu: 4.5.2026.

Google Gemini 2026. c) tehtävässä käytetty alustavasti tekoälyä. Tekoäly: https://gemini.google.com/app. Luotu: 7.5.2026.

Google Kääntäjä 2026. Käännöksessä käytetty: https://translate.google.fi/?sl=auto&tl=fi&op=translate. Luotu: 4.5.2026.

One Transistor.eu. Cornelius. 4.1.2022. (Updated, 2024). Decode 433.92 MHz weather station data. Luettavissa: https://www.onetransistor.eu/2022/01/decode-433mhz-ask-signal.html. Luettu: 4.5.2026.

Tero Karvinen 2026. Verkkoon tunkeutuminen ja tiedustelu (kotitehtävät). Luettavissa: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#tehtavanannot. Luettu: 4.5.2026.

YouTube 18.1.2019. Hubmartin. Universal Radio Hacker SDR Tutorial on 433 MHz radio plugs, 3:19 min – 7:40 min. Katsottavissa: https://www.youtube.com/watch?v=sbqMqb6FVMY&t=199s. Katsottu: 4.5.2026.

