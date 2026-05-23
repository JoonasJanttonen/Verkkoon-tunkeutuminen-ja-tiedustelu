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





Reksiteröinnin jälkeen avaan virtuaalikoneen ja valmistelen virtuaalikoneen huomista haastetta varten. Varmistan vielä, että kaikki toimii, kuten pitää.


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
WifiChallenge Lab minulla on virtuaalikoneessa, mikäli sitä tarvitaan CTF - haasteessa. Päivitän koneen ja asennan joitakin ohjelmia debianille. WireShark minulta näyttääkin jo löytyvän, joten se on kunnossa. Itsenäisen opiskelun kautta rakennan itselleni ymmärrtystä siitä, mistä on kyse, kun puhutaan CTF - haasteesta. 

Koneessa näyttäisi olevan vielä hyvin tilaa: 15 Gt.

Lataan ohjelmat valmiiksi, mikäli niitä tarvitaan huomisessa haasteessa. Tavoitteena on oppia ja ymmärtää haasteesta työstämällä perustason tehtäviä.

```
sudo apt update && sudo apt install -y exiftool binwalk seclists gobuster curl p7zip-full
```

Linuxin huolellinen päivittäminen mahdollistaa sen, että voin (oletettavasti) suorittaa erilaisia tehtäviä, kuten web -tehtävät ja kuva-tehtävät / Forensics. Selaimena käytän Firefoxia. Tähän haasteeseen loin debian trixie - ympäristöön erillisen prohektikansion (~/SecLeaf) ja sinne sanalistat-alihakemiston. Tämän pitäisi auttaa tehtävien työstämisessä terminaalin kautta.


Tämän jälkeen tutustuin rauhassa artikkeliin, jossa kerrotaan CTF - haasteesta. (https://medium.com/@bhagwani6260/how-to-develop-ctf-challenges-d49697d28572).


Tässä vaiheessa kone on olettavasti pitäisi 100 % valmis. Mikäli ongelmia esiintyy, kirjaan ne tänne raporttiin. Haasteessa on hyvin aikaa, koska se kestää kaksikymmentäneljätuntia.

###### 16:12 
###### 22.5.2026.

###### 11:40 
###### 23.5.2026.

Edellisenä iltana briiffasin itseäni katsomalla aiheesta YouTube - videoita, kuten: https://www.youtube.com/watch?v=P07NH5F-t3s&pp=ygUZYmVnaW5uZXIgY2FwdHVyZSB0aGUgZmxhZw%3D%3D & https://www.youtube.com/watch?v=KQiTDIkZTo0&pp=ygUeY2FwdHVyZSB0aGUgZmxhZyBuYWhhbWNvbiAyMDI0.

Ja sitten itse haasteeseen...

Käynnistän haasteen kirjautumalla SecLeafin - sivuille. Navigoin sivuilta kohtaan: haasteet. Aihealueet: Misc, Cryptography, Forensics, REV ja PWN. Tavoitteena on suorittaa ainakin neljä tai viisi tehtävää eri osa-alueista. 

Ensimmäinen tehtävä on SanityCheck, jossa pitää löytää lippu Youtubelinkin takaa: https://www.youtube.com/@SecLeaf. Tehtävä oli ilmeisen helppo eikä sen suorittaminen vaatinut temppuja.

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

Tehtävän etusivulla annettiin ymmärtää, että kyseessä on anti-debugging, mutta todellisuudessa lippua ei piilotettu tiedoston sisälle, vaan sen pystyi ratkaisemaan Linuxin komentoriviltä. Ratkaisuksi löytyi pelkästään strings - komentoa käyttämällä. Ensimmäiset tehtävät eivät näytä vaativan erikoista osaamista, eikä vaadi suurta määrää koodaamista.


<img width="334" height="21" alt="Image" src="https://github.com/user-attachments/assets/41489b1d-de07-4133-8598-ceaad868cb00" />

Kuva 4. Näkymä terminaalissa.

<img width="238" height="55" alt="Image" src="https://github.com/user-attachments/assets/c8df2a4f-f1ef-49f7-beb9-9eb93e457cd6" />

Kuva 5. Ratkaisu tehtävään, Vaultcore.


###### 13:01

Kolmas tehtävä näyttäisi sekin olevan tasoa: helppo. Tehtävän on suorittaunut jo miltein 500 ratkaisua. Kyseessä on kryptografiasta. Aloitan lataamalla tiedoston: encrypted.txt. Klikkaan tiedostoa sen ladattua ja näkymyä aukeaa LibreOfficella. Tässä vaiheessa hyödynnän CyberChef - sivustoa. Maalaan kuvassa näkyvän koodin ja syötän sen CyberChef - sivulle. Tämän jälkeen raahaan magicin keskelle, ja vastaus ilmestyy input - osioon. Vastaus: "base64 ei ole salausta" (suom.)

<img width="391" height="25" alt="Image" src="https://github.com/user-attachments/assets/86cb3416-8b88-4c77-a9b9-022e8dc7c695" />

Kuva 6. LibreOffice.
 
Sivu on käteävä tapa löytämään ratkaisu. Katsoin myös terminaalista, johon oli ladannut kyseisen tehtävän SecLeaf - kansioon, mutta ratkaisu muodostettiin CyberChef - sivujen kautta. (https://gchq.github.io/CyberChef/) 

<img width="300" height="59" alt="Image" src="https://github.com/user-attachments/assets/d4ec1fd9-959e-4133-a185-8d6bc3485714" />

Kuva 7. Tehtävän ratkaisu.

CyberChef - työkalua hyödyntämällä lipusta voitiin tunnistaa, että kyseessä ei ollut varsinainen kryptografinen salaus, vaan pelkkä Base64-koodaus. 


###### 13:29

Tämän jälkeen selaan tehtäviä läpi ja yritän etsiä helpompia tehtäviä. Huomaan, että osassa tehtäviässä on pisteytyksenä 250. En yritä ratkaista näitä, koska ne vaikuttavat erittäin haasteellisilta. 

###### 13:40 

Neljännessä tehtävässä (Forensics), eli kuvatehtävässä näyttäisi olevan nopein ratkaisu hyödyntää samaa työkalua kuin aiemmassa tehtävässä. Lataan tiedoston koneelle, ja rahaan tämän kuvan input - laatikkoon. 

<img width="95" height="91" alt="Image" src="https://github.com/user-attachments/assets/d0eb6f23-afb1-4be1-82aa-0ac416240db2" />

Kuva 8. CyberChef

###### 13:55 

Seuraavassa tehtävässä pyydetään lataamaan kuva. Yritän samaa kikkaa, mutta se osoittautuu vesiperäksi. En saa lippua ilmestymään CyberChefillä. Raahamalla magicin recipe kohtaan, saan ratkaistua tehtävän. 

Yritin ratkaista tämän myös terminaalin kautta, jotta tämä osio tulee tehtyä oiken. Lataan tiedoston. Syötän seuraavat komennot:

Siirretään tiedosto oikealla nimelle.

```
mv ~/Lataukset/Important.jpg .
```

Selvitetään oikea muoto

```
file Important.jpg
```
Puretaan Zip-tiedosto

```
unzip Important.jpg
```
Tsekataan lista(t)

```
ls
```
<img width="236" height="20" alt="Image" src="https://github.com/user-attachments/assets/827c34d0-70fa-4c8c-b1b7-44980578270b" />

Kuva 9. ls


lopuksi luetaan lipun sisältö

```
cat flag.txt
```
<img width="211" height="19" alt="Image" src="https://github.com/user-attachments/assets/69ddea1a-a4cd-4c0b-9f54-de691dc0f0d8" />

Kuva 10. Terminaali

###### 14:23 
Tauko. Selaan myös haasteen nettisivuja ja huomaan, että SecLeaf - sivuille on ilmestynyt uusia haasteita. Tällä hetkellä olen suorittanut neljä haastetta. Tehtävien suorittaminen on keskittynyt seuraaviin aihealueisiin, kuten MISC, Cryptography, Forensics. 
###### 22:24

Community tehtävissä näyttäisi olevan kolme lisättyä tehtävää, joten päätän työstää tästä aiheesta tehtävän. Kaksi ensimmäisestä tehtävästä olivat helppoja tehtäviä, jossa oli jaettu vastaus suoraan tehtänannossa. Kolmannessa tehtävässä piti etsiä instagram postauksista. Tarkoituksena oli seuraa: @knight_secured - tiliä ja @secleafofficial profiilia. Tämän jälkeen tarinoista muodostuivat flag: SecLeaf{1_FOLLOW_YOU}

###### 23:29

Tässä vaiheessa olen käyttänyt tämän tehtävän työstämiseen noin kuusi tuntia, kun lasketaan esivalmistelut, itsenäistä opiskelua sekä raportin (writeupin) - kirjoittamista. kahdeksan tehtävää on suoritettu ja aikaa on jäljellä noin 7,5 tuntia haasteen sulkeutumiseen. 



Steganography aiheen tehtävä: vector_ghost. En saanut suoritettua kyseistä tehtävää, koska en löytänyt tekstitiedostosta lippua. Kokeilin terminaalin kautta sekä CyberChefin kautta. 


<img width="401" height="218" alt="Image" src="https://github.com/user-attachments/assets/858bf582-cc0e-4d0c-8d58-240c8e6f1b3f" />

Kuva 11. Tekstitiedosto avattuna terminaalissa

Voi olla, että väsymyksestä johtuen en hoksaa enkä löydä vastausta.

<img width="403" height="31" alt="Image" src="https://github.com/user-attachments/assets/04a658e8-551c-4cce-b7dd-661bf9083034" />

Kuva 12. Terminaalissa ja CyberChehissä sama näkymä.

###### 0:21 

Tässä vaiheessa totean, että aika alkaa olla täynnä sekä muut tehtävät vaativat huomiota ja aikaa. TÄmä haaste oli erittäin mielenkiintoinen ja aion osallistua uudestaan, kun aika on suotuisa. Tehtävät olivat erilaisia, mutta kuvatehtävä(t) toistuivat muutamaan kertaan. Instagram postauksista lipun etsiminen oli ehkä se mielenkiintoisin. Tämä oli erittäin opettavainen haaste, ja minusta tuntuu, että olen käyttänyt tähän hyvin aikaa. Tämä on mahdollistanut sen, että olen oppinut uutta ja sisäistänyt tämän aihealueen ainakin pintapuolisesti ja hieman syvällisemmin, kun mietitään että kyseessä oli kaikentasoisille toteutettu haaste. Toki tätä olisi voinut jatkaa pitkälle aamuun saakka, mutta aika ei riitä. Web, Osint ja PWN - aihealueen tehtäviä en ehtinyt suorittamaan. Näkisin, että raportti osoittaa jo monipuolisuutta tehtävien työstämisessä. Tämä on ollut hyvää harjoittelua.

Lopuksi listaan tähän saavutetut tulokset liittyen haasteeseen.

<img width="785" height="220" alt="Image" src="https://github.com/user-attachments/assets/dd38913f-2f86-4ea1-b077-6a34d5280e66" />

Kuva 13. Kilpailussa sijoittuminen lopetettaessa

<img width="753" height="377" alt="Image" src="https://github.com/user-attachments/assets/525dcd29-e9e1-44f2-b6b3-beb36681f060" />

Kuva 14. Aikaleima(t)

<img width="753" height="378" alt="Image" src="https://github.com/user-attachments/assets/5150e5a1-528d-40b5-a9fb-c307621c67e8" />

Kuva 15. Aktiivisuus tehtäviä tehdessä

###### 24.5.2026.
###### 0:43 



Lähde:
===

GitHub.io/CryptoChef 2026. Kolmannessa tehtävässä syötetty ratkaisu. Luettavissa: https://gchq.github.io/CyberChef/. Katsottu: 23.5.2026.

Joonas Janttonen GitHub 2026. Luettu: 22.5.2026. Luettavissa: https://github.com/JoonasJanttonen/Verkkoon-tunkeutuminen-ja-tiedustelu/edit/main/h7%20Aaltoja%20harjaamassa.md.

Medium. Anshuman Bhagwani 27.4.2023. How to develop CTF Challenges. Luettu: 22.5.2026. Luettavissa: https://medium.com/@bhagwani6260/how-to-develop-ctf-challenges-d49697d28572.

SecLeaf CTF 2026. Rekisteröinti sivulta. Luettu: 22.5.2026. Luettavissa: https://ctf.secleaf.tech/

SecLeaf 2026. SanityCheck, ensimmäinen tehtävä (Misc). Katsottavissa: https://www.youtube.com/@SecLeaf. Luettu: 23.5.2026.

Youtube 20.4.2021. BEGINNER Capture The Flag - PicoCTF 2021 001 "Obedient Cat". (Itsenäistä opiskelua). Katsottavissa: https://www.youtube.com/watch?v=P07NH5F-t3s. Katsottu: 22.5.2026.

Youtune 27.5.2024. Capture The Flag! NahamCon 2024 CTF Warmups. (Itsenäistä opiskelua). Katsottavissa: https://www.youtube.com/watch?v=KQiTDIkZTo0. Katsottu: 22.5.2026.


