Lempiväri: violetti
===

###### 4.4.2026
###### 19:46

Järjestelmä:

Järjestelmän malli: Aspire E5-573G

Käyttöjärjestelmä: Microsoft Windows 11 Home

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

x) Lue ja vastaa lyhyesti kysymyksiin. Tässä alakohdassa x ei tällä kertaa tarvitse lukea artikkeleita kokonaan, ei tarvitse tiivistää niitä, eikä tehdä testejä koneella.

Selitä tuskan pyramidin idea 1-2 virkkeellä. Bianco 2013: Pyramid of Pain. (Katso eritoten pyramidin kuvaa.) 

- Pyramid of Pain on malli, joka kuvaa kyberhyökkääjän havaitsemiseen käytettyjen indikaattoreiden suhdetta siihen, kuinka paljon niiden estäminen vaikeuttaa vastustajan toimintaa. Alhaalta ylöspäin siirryttäessä indikaattorit muuttuvat helpoista teknisistä tiedoista, kuten tiivisteistä, monimutkaisiin toimintatapoihin (TTPs), joiden muuttaminen aiheuttaa hyökkääjälle suurinta mahdollista haittaa.

- Pyramidin huipulla sijaitsevien taktiikoiden ja menetelmien (TTPs) estäminen on tehokkainta, sillä niiden muuttaminen aiheuttaa hyökkääjälle suurimmat menetykset, kuten kustannukset ja vaikeudet.

Selitä timanttimallin (Diamond Model) idea 1-2 virkkeellä. Tekijä esittelee sen aika juhlallisesti, voit myös etsiä yksinkertaisempia artikkeleita hakukoneella tai kelata suoraan timantin kuvaan. Caltagirone et al 2013: Diamond Model.

- Diamond Model on analyysikehys, joka yhdistää hyökkäyksen neljä ydintekijää: hyökkääjän, kyvykkyyden, infrastruktuurin ja uhrin.
- Mallin avulla analyytikot voivat hahmottaa hyökkäysten välisiä yhteyksiä ja muodostaa kokonaiskuvan uhkista niiden tehokkaampaa torjumista varten.

###### 20:13 
###### 20:20
a) Apache log. Asenna Apache-weppipalvelin paikalliselle virtuaalikoneellesi. Surffaa palvelimellesi salaamattomalla HTTP-yhteydellä, http://localhost . Etsi omaa sivulataustasi vastaava lokirivi. Analysoi yksi tällainen lokirivi, eli selitä sen kaikki kohdat. (Jos Apache ei ole kovin tuttu, voit tätä tehtävää varten vain asentaa sen ja testata oletusweppisivulla. Eli ei tarvitse tehdä omia kotisvuja tms.)

Asennus Tero karvisen ohjeiden mukaisesti:

 ```  
    sudo apt-get update
    sudo apt-get install apache2
    sudo systemctl start apache2
```

<img width="463" height="16" alt="Image" src="https://github.com/user-attachments/assets/d5eea7a5-5153-4491-b535-539c0081a26f" />

Kuva 1. Näkymä terminaalissa.

<img width="793" height="322" alt="Image" src="https://github.com/user-attachments/assets/13d4dab6-8b30-40c1-9a77-a71349c20019" />

Kuva 2. Apache2 localhost

``` 
    /var/log/apache2/
    sudo tail -F /var/log/apache2/access.log
    (Useimmat muut lokit ovat nykyisin 'sudo journalctl --follow')
```
<img width="847" height="55" alt="Image" src="https://github.com/user-attachments/assets/87291422-958e-4334-944e-ba0d9848e0ca" />

Kuva 3. Lokirivi

Lokirivin analyysiä:

127.0.0.1 IP-osoite, eli oma localhost
- - Identiteetti ja käyttäjätunnus tyhjä, koska sivusto on julkinen.
04/April/2026/20:28:51 on aikaleima, jolloin pyyntö on vastaanotettu.
"Get / HTTP /1.1" 200 3883 " ozilla Firefox haettu tiedostopolku, eli juurihakemisto ja protokolla.
200 HTTP tilakoodi 200 tarkoittaa, että pyyntö onnistui, eli on OK.
Palvelimelta lähetettyjen tavujen määrä: 3383 tämä ei sisällä otsikkotietoja.
"-" Tämä tarkoittaa, että viittaaja ei ole.
Selain - ja käyttöjärjestelmä, jolla sivu ladattiin, eli Mozilla Firefox 5.0 (X11 Linux x86_64)

###### 20:52 
###### 5.4.2026.
###### 7:35 

b) Nmapped. Porttiskannaa oma weppipalvelimesi käyttäen localhost-osoitetta ja 'nmap -A' päällä. Selitä tulokset. (Pelkkä http-portti 80/tcp riittää)

Suoritan peruskomennot, ja asennan Nmappedin kommennolla:

```
sudo apt update && sudo apt install nmap -y
```

Varmistan, että apache2 on käynnissä.

<img width="794" height="100" alt="Image" src="https://github.com/user-attachments/assets/a06aaa96-31fc-4332-99b4-ae07d29ed832" />

Kuva 4. Apache on käynnissä.

Tämän jälkeen suljen Internetin, jotta tehtävä tulee suoritetuksi suljetussa ympäristössä.

Seuraava kuva kertoo, että portti 80 on auki. -A versiontunnistus, kun Nmap kysyi palvelimelta sen numeä ja versiota. Tämä on ilmeisesti hyvä, jos halutaan etsiä kyseiseen versioon sopivia haavoittuvuuksia.

<img width="539" height="37" alt="Image" src="https://github.com/user-attachments/assets/cce13256-9d51-4664-913e-86880d11e5ff" />

Kuva 5. Portti 80

-A ajaa automaattisesti skriptejä. Tämän löysin http-title kohdasta. Namp päättelee verkkopakettien perusteella, että kyseessä on Linux (Debian). Tämä on tarkka, koska käytän localhostia.

<img width="523" height="19" alt="Image" src="https://github.com/user-attachments/assets/b0febe2c-fe8c-4412-80ac-0d081cfba2d2" />

Kuva 6. Namp onnistui lukemaan webbisivun otsikon.

Seuraava kuva osoittaa, että kyseessä on tavallinen tietokone, eikä esim reititin.

<img width="305" height="19" alt="Image" src="https://github.com/user-attachments/assets/e95fecda-c619-4e86-add3-c4d2aee98f06" />

Kuva 7. Device type.

Ilman -A - parametria Nmap kertoisi vain, onko portti 80 auki vai kiinni. Näin sain selville palvelimen nimen, version, käyttöjärjestelmän ja webbisivun otsikon yhdellä komennolla.

###### 8:44

c) Skriptit. Mitkä skriptit olivat automaattisesti päällä, kun käytit "-A" parametria? (Näkyy avoimien porttinumeroiden alta, http-blah, http-blöh...).

<img width="528" height="40" alt="Image" src="https://github.com/user-attachments/assets/2e030d8c-0616-49f9-a8d6-f96acbdf3804" />

Kuva 8. Skriptit

d) Jäljet lokissa. Etsi weppipalvelimen lokeista jäljet porttiskannauksesta (NSE eli Nmap Scripting Engine -skripteistä skannauksessa). Löydätkö sanan "nmap" isolla tai pienellä? Selitä osumat. Millaisilla hauilla tai säännöillä voisit tunnistaa porttiskannauksen jostain muusta lokista, jos se on niin laaja, että et pysty lukemaan itse kaikkia rivejä?

Löysin "namp", mutta en ollut varma vastaako tämä tehtävänantoa / vastausta, joten otin kaksi kuvaa:

<img width="1263" height="41" alt="Image" src="https://github.com/user-attachments/assets/4e9a83bd-a332-4a0e-8901-adfc858b7ba1" />

Kuva 9. 

<img width="811" height="32" alt="Image" src="https://github.com/user-attachments/assets/6810c87e-90f0-49aa-b757-f7e9cd54e20f" />

Kuva 10.

Nmap työkalulla havaitsin terminaalissa, että kyseessä on skanneri.

Suodattamisessa voisin käyttää komentoa, kuten: 

```
sudo grep -i "nmap" /var/log/apache2/access.log
```

tai

```
sudo grep "HEAD" /var/log/apache2/access.log
```

e) Wire sharking. Sieppaa verkkoliikenne porttiskannatessa Wiresharkilla. Huomaa, että localhost käyttää "Loopback adapter" eli "lo". Tallenna pcap. Etsi kohdat, joilla on sana "nmap" ja kommentoi niitä. Jokaisen paketin jokaista kohtaa ei tarvitse analysoida, yleisempi tarkastelu riittää.

Käynnistän Wiresharkin ja valitsen liitännän: Loopback: Io. Tuplaklikkaamalla tätä Wireshark tallentaa koneen sisäistä liikennettä.

<img width="800" height="85" alt="Image" src="https://github.com/user-attachments/assets/51b7e214-893f-4b1a-8dd5-fe190dbae8f7" />

Kuva 11. Wireshark käynnistetty.

Avaan uuden terminaalin, ja suoritan Namp-skannauksen, komennolla:

```
nmap -sV localhost
```

Kirjoitan Wiresharkin yläreunan suodatinpalkkiin (Display Filter) "Nmap". Tämän jälkeen Wireshark näytti vain ne paketit, joiden sisällöstä löytyy "Nmap".

<img width="917" height="67" alt="Image" src="https://github.com/user-attachments/assets/737c6430-7f85-41d3-9cec-81078ad134e4" />

Kuva 12. Paketin suodatus

Lopuksi tarkistin User-Agent-tiedot

<img width="601" height="63" alt="Image" src="https://github.com/user-attachments/assets/ed5291c0-2469-4698-989e-4be139f2cf28" />

Kuva 13. User-Agent.

Löysin nmä tunnistetiedot HTTP-otsikoiden joukosta.

###### 9:17

Tässä vaiheessa siirytessäni tehtävään f) huomasin, että minulla ei ole Ngrep asennettuna koneeseen. Pysäytän testaamiseen, ja avaan Internet-yhteyden, ja päivitän raporttia tänne Githubiin.

###### 9:27

f) Net grep. Sieppaa verkkoliikenne 'ngrep' komennolla ja näytä kohdat, joissa on sana "nmap".

Asentaminen tapahtui komennolla:

```
sudo apt-get update
```

```
sudo apt install ngrep
```
Tämän jälkeen suljen Internet-yhteyden, jotta testaaminen tapahtuu "suljetussa ympäristössä".

###### 10:12 

Yhteys palateuttu!

Sieppasin verkkoliikennettä "ngrep" komennolla:

<img width="466" height="89" alt="Image" src="https://github.com/user-attachments/assets/c9d6fde4-4000-44ca-a5c2-c26d8da39c9b" />

Kuva 14. Näkymä terminaalissa.

g) Agentti. Vaihda nmap:n user-agent niin, että se näyttää tavalliselta weppiselaimelta.

Tero karvisen ohjeiden mukaisesti vaihdan kuvan mukaisesti, niin että se näyttää tavalliselta Web-selaimelta.

<img width="792" height="34" alt="Image" src="https://github.com/user-attachments/assets/bf875743-9ea6-41e4-a55b-f79fc6fcbf6c" />

Kuva 15. Uusi User-Agent.

h) Pienemmät jäljet. Porttiskannaa weppipalvelimesi uudelleen localhost-osoitteella. Tarkastele sekä Apachen lokia että siepattua verkkoliikennettä. Mikä on muuttunut, kun vaihdoit user-agent:n? Löytyykö lokista edelleen tekstijono "nmap"?

Tekstijonosta ei löytynyt "nmap" enää. Ennen lokissa luki tämä, mutta se on poistettu. Nyt siinä näkyy se merkkijono, jonka olen kirjoittanut ohjeisden mukaisesti.

<img width="799" height="58" alt="Image" src="https://github.com/user-attachments/assets/0ceb9c52-9879-41a4-a9f8-94d1d8ab669f" />

Kuva 16. Terminaalista katsottuna

i) Hieman vaikeampi: LoWeR ChEcK. Poista skritiskannauksesta viimeinenkin "nmap" -teksti. Etsi löytämääsi tekstiä /usr/share/nmap -hakemistosta ja korvaa se toisella. Tee porttiskannaus ja tarkista, että "nmap" ei näy isolla eikä pienellä kirjoitettuna Apachen lokissa eikä siepatussa verkkoliikenteessä. (Tässä tehtävässä voit muokata suoraan lua-skriptejä /usr/share/nmap alta, 'sudoedit'. Muokatun version paketoiminen siis rajataan ulos tehtävästä.)

Käyn poistamassa tekstistä kaikki "nmap" -sanat ja vaihdan ne Internet Explorer 11. Tämän jälkeen testasin vielä, että löytyykö sanaa mistään. Tämä vei hetken aikaa, koska vaihdoin kaikki, ehkä noin 15 minuuttia. Näppäimellä ctrl+W ja syötin hakukenttään "nmap". Tämän avulla löysin sanat tekstitiedostosta.

<img width="241" height="29" alt="Image" src="https://github.com/user-attachments/assets/e61aaadc-a79c-482d-9842-56440554fe8f" />

Kuva 17. Nmap ei löydy tiedostosta enää. 

Kokeilin porttiskannusta uudelleen (suljetussa ympäristössä).

<img width="801" height="462" alt="Image" src="https://github.com/user-attachments/assets/1ec04136-79ba-4e33-a36b-7e7977773913" />

Kuva 18. Skannaus.

###### 10:31 

j) FCC ID. Etsi valitsemasi langattoman laitteen tiedot FCC ID:llä. Mitä liikenteen purkamista tai manipuloimista hyödyttävää tietoa löydät?

Kirjaudun Federal Communications Commissions - sivuille. Nettisivut olivat tutut edelliseltä luennolta, jossa käsiteltiin aihetta.

<img width="249" height="34" alt="Image" src="https://github.com/user-attachments/assets/f618679a-e49c-4271-9293-b54d09f5f550" />

Kuva 19. FCC

Päätän tarkistaa langattoman hiireni tiedot. Hetken sain etisiä, kunnes löysin tiedot USB -vastaanottimesta. Irroitin tämän osan koneesta, ja teksti löytyi siitä. Syötin nämä tiedot nettisivulle.

Kuva 20. 

Liikenteen analysointiin seuraavanlaisia:

Operational Description (Theory of Operation): Tämä on tärkein tiedosto protokollan ymmärtämiseen. Se kertoo, mitä taajuuksia laite käyttää.

Test Report: Tästä näen tarkat radiotaajuudet ja kanavalistan.

Fyysiseen hakkerointiin:

Laiteetn kuvat ja kaaviot sekä yleistasolta, kuinka virta ja data kulkevat sensorilta radiolähettimelle.

Salauksessa esim, kuinka laite voidaan yhdistää koneeseen.



Lähteet
===

Tero Karvinen 2026. Verkkoon tunkeutuminen ja tiedustelu. Kotitehtävät. Luettavissa: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#h2-lempivari-violetti. Luettu: 4.4.2026.

WebAsha 7.17.2025. What Is the Diamond Model in Cybersecurity? A Beginner-Friendly Guide with Real-World Exambles and Analysis. Luettavissa: https://www.webasha.com/blog/what-is-the-diamond-model-in-cybersecurity-a-beginner-friendly-guide-with-real-world-examples-and-analysis. Luettu: 4.4.2026.
