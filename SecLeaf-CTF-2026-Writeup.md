SecLeaf Q2 CTF 2026
===

Järjestelmä:

Järjestelmän malli: Aspire E5-573G

Käyttöjärjestelmä: Microsoft Windows 11 Home

Suoritin: Inter(R) Pentium(R) 3558U @ 1.70GHz. Mhz, 2 ydin(tä)

Muisti: 6.00 Gt asennettua fyysistä muistia

Oracle Virtualbox

Debian 13 (trixie)

###### 14:47
###### 22.5.2026.

Rekisteröin SecLeafin - sivuille, jotta voin osallistua haasteeseen: https://ctf.secleaf.tech/. Rekisteröin itseni samalla käyttäjäniemellä kuin Laksussa: Oppilas_777
Rekisteröinti onnistui helposti omalla sähköpostilla. 


<img width="401" height="167" alt="Image" src="https://github.com/user-attachments/assets/540a6f24-f55f-4e74-93b4-d4d444a844cc" />

Kuva 1. Rekisteröinti SecLeaf.

Seuraavaksi sivustolla pyydetään perustamaan tiimi. Luon yhden henkilön tiimin, jonka nimeksi tulee: Taikuri. 

<img width="794" height="365" alt="Image" src="https://github.com/user-attachments/assets/54bfb595-d1d4-4341-9d9e-7bd48fdc43c7" />

Kuva 2. Tiimi rekisteröity.





Reksiteröinnin jälkeen avaan virtuaalikoneen ja valmistelen tämän huomista haastetta ajatellen. Varmistan vielä, että kaikki toimii, kuten pitää.
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
WifiChallenge Lab minulla on virtuaalikoneessa, mikäli sitä tarvitaan CTF - haasteessa. Päivitän koneen ja asennan joitakin ohjelmia debianille. WireShark minulta näyttääkin jo löytyvän, joten sitä ei tarvitse asentaa uudelleen. 

Koneessa näyttäisi olevan vielä hyvin tilaa: 15 Gt.


















Lähde:

Joonas Janttonen GitHub 2026. Luettu: 22.5.2026. Luettavissa: https://github.com/JoonasJanttonen/Verkkoon-tunkeutuminen-ja-tiedustelu/edit/main/h7%20Aaltoja%20harjaamassa.md.

SecLeaf CTF 2026. Rekisteröinti sivulta. Luettu: 22.5.2026. Luettavissa: https://ctf.secleaf.tech/
