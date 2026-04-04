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




Lähteet
===

Tero Karvinen 2026. Verkkoon tunkeutuminen ja tiedustelu. Kotitehtävät. Luettavissa: https://terokarvinen.com/verkkoon-tunkeutuminen-ja-tiedustelu/#h2-lempivari-violetti. Luettu: 4.4.2026.

WebAsha 7.17.2025. What Is the Diamond Model in Cybersecurity? A Beginner-Friendly Guide with Real-World Exambles and Analysis. Luettavissa: https://www.webasha.com/blog/what-is-the-diamond-model-in-cybersecurity-a-beginner-friendly-guide-with-real-world-examples-and-analysis. Luettu: 4.4.2026.
