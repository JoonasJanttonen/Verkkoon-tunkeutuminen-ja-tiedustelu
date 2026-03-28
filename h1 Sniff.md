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

- Wireshark soveltuu verkon analysointiin. Käyttäjäj voi tutkia verkon liikennettä sharkin avulla.

- Wireshark on monipuolinen ohjelma, jossa on paljon toimintoja.

- Yksi suosituimmista ominaisuuksista on Follow TCP stream.

###### 19:26 Läksyjen työstäminen jatkuu seuraavana päivänä

Karvinen 2025: Network Interface Names on Linux

- "Verkkoliitäntä on melkein kuin "verkkokortti". Paitsi että se ei välttämättä ole fyysinen kortti". Lähde: (https://terokarvinen.com/network-interface-linux/)

- Nimeämisjärjestelmät:
- en = langallinen E ja n etwl
- WLAN, langaton lähiverkko, WiFi
- lo Lo opback adapteri. Lähde: (https://terokarvinen.com/network-interface-linux/)

- wlp4s0 WiFi-kortti.
- enp1s0 Langallinen Ethernet-kortti
- lo Loopback-sovitin.
- enx738899738899 Langallinen Ethernet-kortti. Numero "x": n jälkeen on kortin MAC-numero. Lähde: (https://terokarvinen.com/network-interface-linux/)

a) Linux. Asenna Debian tai Kali Linux virtuaalikoneeseen. (Tätä alakohtaa ei poikkeuksellisesti tarvitse raportoida, jos sinulla ei ole mitään ongelmia. 
Jos on mitään haasteita, tee täsmällinen raportti)

OK.

###### 24.3.2026.
###### 20:20


###### 28.3.2026.
###### 07:10

Läksyjen tekeminen jatkuu... Välipäivinä alustin koneen ja putsasin sisältä. Kone toimii kuin uusi! :)


b) Ei voi kalastaa. Osoita, että pystyt katkaisemaan ja palauttamaan virtuaalikoneen Internet-yhteyden

Löysin verkkoliitännän nimen komennalla:

```
ip a
```
<img width="830" height="49" alt="Image" src="https://github.com/user-attachments/assets/cb1f65e8-fdc6-4844-8231-299c1013215e" />

Kuva 1. Liitännän nimi näkyy kohdassa 2. 

Seuraavaksi katkaisin yhteyden kommennolla:

```
sudo ip link set enp0s3 down
```
<img width="280" height="115" alt="Image" src="https://github.com/user-attachments/assets/6805ee16-ad4d-4359-9195-e80726a00888" />

Kuva 2. Yhteys katkaistu.

Lopuksi palautan yhteyden kommennolla:

```
sudo ip link set enp0s3 up
```
<img width="362" height="125" alt="Image" src="https://github.com/user-attachments/assets/2fe0d5d3-5a4e-4e0c-ad30-c14594abb5ed" />

Kuva 3. Yhteys palautettu.

<img width="472" height="94" alt="Image" src="https://github.com/user-attachments/assets/b44ef33f-b215-458a-8a60-bb2b6a2e70d8" />

Kuva 4. Näkymä terminaalista kotitehtävää tehdessä.

###### 8:20

c) Wireshark. Asenna Wireshark. Sieppaa liikennettä Wiresharkilla. (Vain omaa liikennettäsi. Voit käyttää tähän esimerkiksi virtuaalikonetta). 

Asennan Wiresharkin syöttämällä terminaaliin seuraavat komennot:

```
sudo apt update
```
```
sudo apt install wireshark
```
<img width="851" height="537" alt="Image" src="https://github.com/user-attachments/assets/804f6655-e4e6-4076-9069-601083145b48" />

Kuva 5. Valitsin Kyllä Tero Karvisen ohjeiden mukaisesti: https://terokarvinen.com/wireshark-getting-started/.
Tämä mahdollistaa pakettien kaappaamisen ilman, että ohjelmaa tarvitsee ajaa aina root-oikeuksilla (mikä on tietoturvallisempaa).

Lisäsin käyttäjän Wireshark - ryhmään.
```
sudo usermod -aG wireshark joonas
```
Otan muutokset käyttöön:
```
newgrp wireshark
```

<img width="1276" height="589" alt="Image" src="https://github.com/user-attachments/assets/f874a8e7-91df-49f3-8d87-7f3ceeadc8fa" />

Kuva 6. Lopputulos! Wireshark käynnistys syöttämällä terminaaliin: "Wireshark".


###### 8:39

d) Oikeesti TCP/IP. Osoita TCP/IP-mallin neljä kerrosta yhdestä siepatusta paketista. Voit selityksen tueksi laatikoida ne ruutukaappauksesta. (Voit käyttää vastauksesi osana ruutukaappaustasi h0-tehtävästä, mutta tässä tehtävässä tarvitaan myös sanallinen selitys.)

Käynnistän Wireshark-sieppauksen ja siirryn selaimella osoitteeseen http://www.lonnrot.net. Koska kyseessä on verkkosivun avaaminen, tietokoneeni tekee ensin DNS-kyselyn (Domain Name System) selvittääkseen palvelimen IP-osoitteen:

<img width="1279" height="171" alt="Image" src="https://github.com/user-attachments/assets/dcd2e6bc-e508-471e-ba3f-d44b5c416662" />

Kuva 7. Verkkoliitäntäkerros (Ethernet II). Internet-kerros (IPv4). Kuljetuskerros (UDP). Sovelluskerros (DNS).

###### 9:17

Tauko + h0 päivittämistä

###### 10:15

e) Mitäs tuli surffattua? Avaa surfing-secure.pcap. Tutustu siihen pintapuolisesti ja kuvaile, millainen kaappaus on kyseessä. Tässä siis vain lyhyesti ja yleisellä tasolla. Voit esimerkiksi vilkaista, montako konetta näkyy, mitä protokollia pistää silmään. Määrästä voit arvioida esimerkiksi pakettien lukumäärää, kaappauksen kokoa ja kestoa.

Pakettien määrä näyttäisi olevan: 283. Tiedoston koko näyttäisi olevan pieni, kuten kuva.pgp. Kesto: 7 sekunttia. Osa tiedostosta on salattua, koska protocolissa lukee TLS / SSL, eli kyseessä on salattu liikenne. Kyseessä voi olla yksittäinen pyyntö. 


f) Vapaaehtoinen, vaikea: Mitä selainta käyttäjä käyttää? surfing-secure.pcap (Päivitys 2025-03-31 w14 ma - muutin tehtävän vapaaehtoiseksi Giang:n suosituksesta)

Syötin kenttään: tls.handshake.type == 1. Valitsin Quic, ja löysin paljon UDP - liikennettä. Löysin Internetistä tietoa, että  Google kehitti QUIC-protokollan, joka toimii UDP. Tästä voidaan päätellä, että kyseessä on todennököisesti: Google Chrome?

g) Minkä merkkinen verkkokortti käyttäjällä on? surfing-secure.pcap

LGb it. Käyttäjällä on käytössä: Giga-byte Technology.

<img width="892" height="41" alt="Image" src="https://github.com/user-attachments/assets/4c6e18ad-e464-41da-a354-12e46489bcbc" />

Kuva 8. Source

h) Millä weppipalvelimella käyttäjä on surffaillut? surfing-secure.pcap
Huonoja uutisia: yhteys on suojattu TLS-salauksella.

Lataan tiedoston, joka käynnistyy sharkissa. Syötän komentoriville: "tls.handshake.type == 1"
Selaan paketteja ja valitsen Client Hello - viestin. Käyn läpi pakettilistoja, ja syötän DNS komentoriville. Huomaan, että listalla on Stand query AAA. Huomaan, että viimeisin sivu, jossa käyttäjä on vieraillut löytyy tältä riviltä:

<img width="1227" height="58" alt="Image" src="https://github.com/user-attachments/assets/0b79f671-d13a-434d-8795-0125444ac2be" />



Kuva 9. Näkymä Wireshark 

i) Analyysi. Sieppaa pieni määrä omaa liikennettäsi. Analysoi se, eli selitä mahdollisimman perusteellisesti, mitä tapahtuu. (Tässä pääpaino on siis analyysillä ja selityksellä, joten liikennettä kannattaa ottaa tarkasteluun todella vähän - vaikka vain pari pakettia. Gurut huomio: Selitä myös mielestäsi yksinkertaiset asiat.)




Lähteet
===

Joonas Janttonen 2025. Github. h5 Toimiva versio. Luettavissa: https://github.com/JoonasJanttonen/Palvelinten-hallinta/edit/main/h5%20Toimiva%20versio.md. Luettu: 24.3.2026.

Projekti Lönnrot 2005. Internet-sivut. Luettavissa: https://www.lonnrot.net/valmiit.html. Luettu: 28.3.2026.

Tero Karvinen 2025. Network Interface Names on Linux. Luettavissa: https://terokarvinen.com/network-interface-linux/. Luettu: 24.3.2026.

Tero karvinen. Verkkorajapinnan nimet Linuxissa. Luettavissa: https://terokarvinen.com/network-interface-linux/. Luettu: 28.3.2026.

Tero Karvinen 2026. Verkkoon tunkeutuminen ja tiedustelu. Luettavissa: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#kertauspaketti. Luettu: 24.3.2026.

Tero Karvinen 2026. Wireshark - Getting Started. Luettavissa: https://terokarvinen.com/wireshark-getting-started/. Luettu: 24.3.2026.
