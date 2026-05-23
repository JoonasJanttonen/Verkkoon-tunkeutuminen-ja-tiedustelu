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

Lataan vain tavallisimmat ohjelmat, jotta voin suorittaa helpoimmat tehtävät haasteesta. Tässä haasteessa en keskity haastavampimiin, koska ohjeena oli suorittaa aloittelijan tehtävät.

```
sudo apt update && sudo apt install -y exiftool binwalk seclists gobuster curl p7zip-full
```

Näillä ohjelmilla voin oletettavasti suorittaa web -tehtävät ja kuva-tehtävät / Forensics. Selaimena käytän Firefoxia. Tähän haasteeseen loin debian trixie - ympäristöön erillisen prohektikansion (~/SecLeaf) ja sinne sanalistat-alihakemiston. Latasin sinne Daniel Miesslerin SecLists-kokoelmasta common.txt-sanalistan, jota hyödynnetään Web-haasteiden piilotettujen hakemistojen ja tiedostojen automatisoidussa etsinnässä, esim Gobuster - ohjelmalla. 


Lopuksi tutustuin artikkeliin, jossa kerrotaan CTF haasteesta. (https://medium.com/@bhagwani6260/how-to-develop-ctf-challenges-d49697d28572).


Kone pitäisi olla nyt 100 % valmis siihen, että voin suorittaa perustehtävät haasteesta. Mikäli ongelmia esiintyy, kirjaan ne tänne raporttiin. Haasteessa on hyvin aikaa, koska se on avoinna kaikille kaksikymmentäneljätuntia. Tämän jälkeen haaste sulkeutuu.

###### 16:12 
###### 22.5.2026.

###### 11:40 
###### 23.5.2026.

Edellisenä iltana priiffasin itseäni katsomalla aiheesta YouTube - videoita, kuten: https://www.youtube.com/watch?v=P07NH5F-t3s&pp=ygUZYmVnaW5uZXIgY2FwdHVyZSB0aGUgZmxhZw%3D%3D & https://www.youtube.com/watch?v=KQiTDIkZTo0&pp=ygUeY2FwdHVyZSB0aGUgZmxhZyBuYWhhbWNvbiAyMDI0.

Käynnistän haasteen kirjautumalla SecLeafin - sivuille. Navigoin sivuilta kohtaan: haasteet. Aihealueet: Misc, Cryptography, Forensics, REV ja PWN. Keskityn työstämään helpoimpia tehtäviä, kuten sähköpostissa neuvoit. 

Ensimmäinen tehtävä on SanityCheck, jossa pitää löytää lippu Youtubelinkin takaa: https://www.youtube.com/@SecLeaf. Edellisenä iltana priiffasin itseäni katsomalla aiheesta YouTube - videoita, kuten: https://www.youtube.com/watch?v=P07NH5F-t3s&pp=ygUZYmVnaW5uZXIgY2FwdHVyZSB0aGUgZmxhZw%3D%3D & https://www.youtube.com/watch?v=KQiTDIkZTo0&pp=ygUeY2FwdHVyZSB0aGUgZmxhZyBuYWhhbWNvbiAyMDI0.

Tehtävä näyttäisi olevan johdanto, jossa osoitetaan, kuinka lippu palautetaan. Lippu näkyy etusivula, kun linkin avaa. Palautan tämän ja saan ensimmäisen pisteen haasteesta.

<img width="256" height="280" alt="Image" src="https://github.com/user-attachments/assets/4e76a5c9-103e-4b46-abfd-43defa420e1e" />

Kuva 2. Ensimmäinen tehtävä, Misc.

Vastaus näkyy kuvan yläosassa.

<img width="394" height="257" alt="Image" src="https://github.com/user-attachments/assets/a05bd88e-0896-4c4f-9fd9-e227068352d3" />

Kuva 3. Tehtävä ratkaistu.

###### 12:15
###### 12:24

Tehtävä kaksi, Vaultcore. Aloitan tehtävän lataamalla tiedoston. Tämän jälkeen avaan terminaalin ja syötän komennon:

```
ls ~/Lataukset
```

Siirrä tiedoston SecLeaf-kansioon.

```
mv ~/Lataukset/vaultcore .
```


Kuva 3. Ratkaisu tehtävään, Vaultcore.









Lähde:
===

Joonas Janttonen GitHub 2026. Luettu: 22.5.2026. Luettavissa: https://github.com/JoonasJanttonen/Verkkoon-tunkeutuminen-ja-tiedustelu/edit/main/h7%20Aaltoja%20harjaamassa.md.

Medium. Anshuman Bhagwani 27.4.2023. How to develop CTF Challenges. Luettu: 22.5.2026. Luettavissa: https://medium.com/@bhagwani6260/how-to-develop-ctf-challenges-d49697d28572.

SecLeaf CTF 2026. Rekisteröinti sivulta. Luettu: 22.5.2026. Luettavissa: https://ctf.secleaf.tech/

SecLeaf 2026. SanityCheck, ensimmäinen tehtävä (Misc). Katsottavissa: https://www.youtube.com/@SecLeaf. Luettu: 23.5.2026.
