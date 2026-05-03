###### 27.4.2026.
###### 10:16

WiFi
===

Järjestelmä:

Järjestelmän malli: Aspire E5-573G

Käyttöjärjestelmä: Microsoft Windows 11 Home

Suoritin: Inter(R) Pentium(R) 3558U @ 1.70GHz. Mhz, 2 ydin(tä)

Muisti: 6.00 Gt asennettua fyysistä muistia

Oracle Virtualbox

Wi-FiChallenge Lab v2.4.2 Oracle VirtualBox

###### 10:20

Kotitehtävät
===
###### 28.4.2026.
###### 20:34 

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

h6 kotitehtävät

a) Tutustu wifi challenge lab 2.1 harjoitus ympäristöön ja käytä tarvittaessa hyväksesi jo olemassa olevia ohjeita. 

WifiChallenge Lab v2.4.2.VIrtualbox latasin tikulta luennon aikana. Haasteet löytyinvät sivulta: https://lab.wifichallenge.com/challenges.
Internetissä surffailessani löysin loistavan sivuston ohjeisiin ja harjoitteluun: https://www.aircrack-ng.org/doku.php?id=airmon-ng. Toinen sivu, josta löysin vinkkejä: https://github.com/koutto/pi-pwnbox-rogueap/wiki/03.-WiFi-Monitoring-(Passive-Scanning). Ohjeita seuraamalla tein harjoituksia ja tutustuin WifiChallenge 2.1 labin harjoituksiin: https://r4ulcl.com/posts/walkthrough-wifichallenge-lab-2.0/.  

Käytin seuraavanlaisia komentoja harjoiteltaessa:

Listaa langattomat interfacet
```
sudo airmon-ng
```
Näyttää prosessit

```
sudo airmon-ng check
```

Mode päälle
```
sudo airmon-ng start wlan0
```
Sulje pois päältä

```
sudo airmon-ng stop wlan1 
```

Lopettaa prosessit, jotka häiritsevät

```
sudo airmon-ng check kill
```

Näytä status (interface)
```
sudo iwconfig
```
Tarvittaessa voit löytää ohjeet, käyttämällä komentoa: 
```
sudo airodump-ng --help
```



###### 28.4.2026.
###### 21:46 

###### 29.4.2026.
###### 18:47

<img width="833" height="445" alt="Image" src="https://github.com/user-attachments/assets/db8508cd-25e9-452f-9715-f3c78c7c11c2" />

Kuva 1. WiFiChallenges

Walkthroughsta löytyy ohjeita tehtävien tekemiseen, mikäli jää jumiin: https://r4ulcl.com/posts/walkthrough-wifichallenge-lab-2.0/. 


###### 3.5.2026
###### 03:05

Päivitän kotiläksyt, koska olin lisännyt väärät kuvat tänne Githubiin.



```
sudo su
cat /root/flag.txt
```
<img width="548" height="130" alt="Image" src="https://github.com/user-attachments/assets/18a8e9d9-2eb6-49e4-b23d-9812edfdd71b" />

Kuva 2. Flag

Seuraavaaksi katsoin mitä laitteita löydän komennolla: 

```
ip a
```
Kokeilin airdodump-ng wlan0 mutta en löytänyt globalia. Tämän jälkeen kokeilin wlan1 ja sieltä löytyi:

```
airodump-ng wlan1 --band abg
```
<img width="383" height="13" alt="Image" src="https://github.com/user-attachments/assets/c8cc95b6-03b3-416a-b828-4ab05746a56c" />

Kuva 3. Global

Seuraavaksi löydin Wi-FI-IT, joka löytyi kanavalta 11

```
airodump-ng wlan1 --channel 11
```
<img width="371" height="11" alt="Image" src="https://github.com/user-attachments/assets/494e16c2-a6be-4056-932e-a853a99644f8" />

Kuva 4. Wi-Fi-IT

Jos olen tehnyt tämän oikein tämä pitäisi olla ESSID verkon piilotettu nimi:

<img width="274" height="11" alt="Image" src="https://github.com/user-attachments/assets/d81b0ece-1e53-497f-a6c0-2b2c12b6473c" />

Kuva 5. ESSID

b) Kirjoita raportti siitä mitä opit ja mitkä asia yllättivät sinut kun tutustuit harjoitukseen.

Harjoittelun myötä opin tietotekniikka, jossa WiFiChallenge Lab on virtuaalinen harjoitusympäristö, jonka avulla voin oppia langattomien verkkojen tietoturvasta ja testaamista ilman fyysisiä Wi-Fi-adaptereita. Lisäksi eri suojausmenetelmien murtamisesta ja analysoinnista. Aircrackin kautta opin uusia työkaluja Wi-Fi turvallisuuden tutkimiseen. Lopuksi opin, että Wireshark on hyvin moniulotteinen työkalu verkon tutkimiseen. Yhteenvetona: opin uutta tietoturvasta.

c) Miten suhtautumisesi WLanin turvallisuuteen muuttui sen jälkeen kun teit harjoitukset?

Suhtautuminen Wlanin turvallisuuteen muuttui jo luennon aikana, kun opettaja (Lari) kertoi tilanteita ja esimerkkejä liittyen verkkojen turvallisuudesta. Harjoitusten myötä koin ymmärryksen, että verkot jakavat tietoa kaikkiin suuntiin. Lisäksi opin sen, että avoimia verkkoja tulisi välttää, kuten lentonkentän WiFiä, jota verrkorikkolliset voivat hyödyntää. Päivittämisen tärkeydestä sekä siihen, että salasana itsessään ei tee verkosta murtumatonta. 


###### 29.4.2026.
###### 22:10 












Lähde
===

Aircrack-ng 2026. Luettavissa: https://www.aircrack-ng.org/doku.php?id=airmon-ng. Luettu: 28.4.2026

GitHub 1.11.2020. Koutto. Luettavissa: https://github.com/koutto/pi-pwnbox-rogueap/wiki/03.-WiFi-Monitoring-(Passive-Scanning). Luettu: 29.4.2026.

GitHub 2026. WifiChallenge. Luettavissa: https://github.com/koutto/pi-pwnbox-rogueap/wiki/03.-WiFi-Monitoring-(Passive-Scanning) Luettu: 27.4.2026.

Haaga-Helia Moodle (pohjana). Larin luennot 2026. 6. WiFi. Luettu: 27.4.2026.

Joonas Janttonen GitHub 2026. h5 Mininet. Luettavissa: https://github.com/JoonasJanttonen/Verkkoon-tunkeutuminen-ja-tiedustelu/blob/main/h5%20Mininet.md. Luettu: 27.4.2026.

WiFiChallenge lab 2023 2.0. README. Luettavissa: https://r4ulcl.com/posts/walkthrough-wifichallenge-lab-2.0/. Luettu: 29.4.2026.
