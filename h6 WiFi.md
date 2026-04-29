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


<img width="302" height="254" alt="Image" src="https://github.com/user-attachments/assets/e12176eb-1a79-432e-b935-97cdcd7dc743" />

Kuva 2. Näkymä terminaalissa harjoittelun päätyttyä.


b) Kirjoita raportti siitä mitä opit ja mitkä asia yllättivät sinut kun tutustuit harjoitukseen.



c) Miten suhtautumisesi WLanin turvallisuuteen muuttui sen jälkeen kun teit harjoitukset?











Lähde
===

Aircrack-ng 2026. Luettavissa: https://www.aircrack-ng.org/doku.php?id=airmon-ng. Luettu: 28.4.2026

GitHub 1.11.2020. Koutto. Luettavissa: https://github.com/koutto/pi-pwnbox-rogueap/wiki/03.-WiFi-Monitoring-(Passive-Scanning). Luettu: 29.4.2026.

GitHub 2026. WifiChallenge. Luettavissa: https://github.com/koutto/pi-pwnbox-rogueap/wiki/03.-WiFi-Monitoring-(Passive-Scanning) Luettu: 27.4.2026.

Haaga-Helia Moodle (pohjana). Larin luennot 2026. 6. WiFi. Luettu: 27.4.2026.

Joonas Janttonen GitHub 2026. h5 Mininet. Luettavissa: https://github.com/JoonasJanttonen/Verkkoon-tunkeutuminen-ja-tiedustelu/blob/main/h5%20Mininet.md. Luettu: 27.4.2026.

WiFiChallenge lab 2023 2.0. README. Luettavissa: https://r4ulcl.com/posts/walkthrough-wifichallenge-lab-2.0/. Luettu: 29.4.2026.
