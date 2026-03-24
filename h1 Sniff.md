Sniff
---

###### 24.3.2026.

###### 18:00

Järjestelmä:

Järjestelmän malli: Aspire E5-573G

Käyttöjärjestelmä: Microsoft Windows 10 Home

Suoritin: Inter(R) Pentium(R) 3558U @ 1.70GHz. Mhz, 2 ydin(tä)

Muisti: 6.00 Gt asennettua fyysistä muistia

Oracle Virtualbox

Debian 13 (trixie)




---

Debianin asentamisen syötän tutut komennot, kuten:

```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get -y dist-upgrade
sudo apt-get -y install ufw \
sudo ufw enable 
```
Lopuksi aikavyöhykkeen asennus, jotta ohjelmat toimivat oikein. Tätä toimintoa ei tarvitse, mutta jos joku haluaa kopioida tästä itselleen, niin:

```
sudo timedatectl set-timezone Europe/Helsinki
sudo timedatectl
set-ntp true
```

x) Lue ja tiivistä. (Tässä x-alakohdassa ei tarvitse tehdä testejä tietokoneella, vain lukeminen tai kuunteleminen ja tiivistelmä riittää. Tiivistämiseen riittää muutama ranskalainen viiva.)

Karvinen 2025: Wireshark - Getting Started. 

- Wireshark soveltuu verkon analysointiin, jossa käyttäkä voi tutkia verkon liikennettä.

- Wireshark on monipuolinen ohjelma ja laajasti käytössä, kun analysoidaan verkkoja.

- Halutessasi voit seurata TCP - virtaa, kun tarkastelet suojaamattomia yhteyksiä.

###### 19:26 Läksyjen työstäminen jatkuu seuraavana päivänä

Karvinen 2025: Network Interface Names on Linux

- 

-

-

a) Linux. Asenna Debian tai Kali Linux virtuaalikoneeseen. (Tätä alakohtaa ei poikkeuksellisesti tarvitse raportoida, jos sinulla ei ole mitään ongelmia. 
Jos on mitään haasteita, tee täsmällinen raportti)

Asennus onnistui ongelmitta.

b) Ei voi kalastaa. Osoita, että pystyt katkaisemaan ja palauttamaan virtuaalikoneen Internet-yhteyden


c) Wireshark. Asenna Wireshark. Sieppaa liikennettä Wiresharkilla. (Vain omaa liikennettäsi. Voit käyttää tähän esimerkiksi virtuaalikonetta). 


d) Oikeesti TCP/IP. Osoita TCP/IP-mallin neljä kerrosta yhdestä siepatusta paketista. Voit selityksen tueksi laatikoida ne ruutukaappauksesta. (Voit käyttää vastauksesi osana ruutukaappaustasi h0-tehtävästä, mutta tässä tehtävässä tarvitaan myös sanallinen selitys.)

e) Mitäs tuli surffattua? Avaa surfing-secure.pcap. Tutustu siihen pintapuolisesti ja kuvaile, millainen kaappaus on kyseessä. Tässä siis vain lyhyesti ja yleisellä tasolla. Voit esimerkiksi vilkaista, montako konetta näkyy, mitä protokollia pistää silmään. Määrästä voit arvioida esimerkiksi pakettien lukumäärää, kaappauksen kokoa ja kestoa.

f) Vapaaehtoinen, vaikea: Mitä selainta käyttäjä käyttää? surfing-secure.pcap (Päivitys 2025-03-31 w14 ma - muutin tehtävän vapaaehtoiseksi Giang:n suosituksesta)

g) Minkä merkkinen verkkokortti käyttäjällä on? surfing-secure.pcap

h) Millä weppipalvelimella käyttäjä on surffaillut? surfing-secure.pcap

    Huonoja uutisia: yhteys on suojattu TLS-salauksella.

i) Analyysi. Sieppaa pieni määrä omaa liikennettäsi. Analysoi se, eli selitä mahdollisimman perusteellisesti, mitä tapahtuu. (Tässä pääpaino on siis analyysillä ja selityksellä, joten liikennettä kannattaa ottaa tarkasteluun todella vähän - vaikka vain pari pakettia. Gurut huomio: Selitä myös mielestäsi yksinkertaiset asiat.)




Lähteet
===

Joonas Janttonen 2025. Github. h5 Toimiva versio. Luettavissa: https://github.com/JoonasJanttonen/Palvelinten-hallinta/edit/main/h5%20Toimiva%20versio.md. Luettu: 24.3.2026.

Tero Karvinen 2025. Network Interface Names on Linux. Luettavissa: https://terokarvinen.com/network-interface-linux/. Luettu: 24.3.2026.

Tero Karvinen 2026. Verkkoon tunkeutuminen ja tiedustelu. Luettavissa: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#kertauspaketti. Luettu: 24.3.2026.

Tero Karvinen 2026. Wireshark - Getting Started. Luettavissa: https://terokarvinen.com/wireshark-getting-started/. Luettu: 24.3.2026.
