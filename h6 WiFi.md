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







b) Kirjoita raportti siitä mitä opit ja mitkä asia yllättivät sinut kun tutustuit harjoitukseen.

Internetissä surffailessani löysin loistavan sivuston ohjeisiin ja harjoitteluun: https://www.aircrack-ng.org/doku.php?id=airmon-ng. Ohjeita seuraamalla tein harjoituksia ja tutustuin WifiChallenge 2.1 labin harjoituksiin. Käytin seuraavanlaisia komentoja tehdessäni harjoituksia:

Check status and/or listing wireless interfaces
```
sudo airmon-ng
```
Checking for interfering processes
```
sudo airmon-ng check
```
Enable monitor mode
```
sudo airmon-ng start wlan0
```
Killing interfering processes
```
sudo airmon-ng check kill
```
###### 28.4.2026.
###### 21:46 

c) Miten suhtautumisesi WLanin turvallisuuteen muuttui sen jälkeen kun teit harjoitukset?











Lähde
===

Aircrack-ng 2026. Luettavissa: https://www.aircrack-ng.org/doku.php?id=airmon-ng. Luettu: 28.4.2026

GitHub 2026. WifiChallenge. Luettavissa: https://github.com/koutto/pi-pwnbox-rogueap/wiki/03.-WiFi-Monitoring-(Passive-Scanning) Luettu: 27.4.2026.

Haaga-Helia Moodle. Larin luennot 2026. 6. WiFi. Luettu: 27.4.2026.

Joonas Janttonen GitHub 2026. h5 Mininet. Luettavissa: https://github.com/JoonasJanttonen/Verkkoon-tunkeutuminen-ja-tiedustelu/blob/main/h5%20Mininet.md. Luettu: 27.4.2026.
