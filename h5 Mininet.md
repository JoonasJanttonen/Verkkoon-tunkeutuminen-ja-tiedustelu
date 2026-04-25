###### 23.4.2026.
###### 18:20


Mininet
===




Järjestelmä:

Järjestelmän malli: Aspire E5-573G

Käyttöjärjestelmä: Microsoft Windows 11 Home

Suoritin: Inter(R) Pentium(R) 3558U @ 1.70GHz. Mhz, 2 ydin(tä)

Muisti: 6.00 Gt asennettua fyysistä muistia

Oracle Virtualbox

Debian 13 (trixie)


Kotitehtävät
===

Ennen tehtävien työstämistä, syötän peruskomennot terminaaliin:

```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get -y dist-upgrade
sudo apt-get -y install ufw \
sudo ufw enable 
```

Lopuksi aikavyöhykkeen asennus, jotta ohjelmat toimivat oikein:

```
sudo timedatectl set-timezone Europe/Helsinki
sudo timedatectl
set-ntp true
```

Tutustuin aiheeseen Moodlessa.

###### 23.4.2026.
###### 20:10 

###### 24.4.2026.
###### 15:09

Päivittämisen jälkeen tutustuin oppitunnin aiheeseen Moodlessa. Tämän jälkeen latasin tiedostot virtuaalikoneeseen, ja purkasin tiedostot.

<img width="434" height="188" alt="Image" src="https://github.com/user-attachments/assets/388dd6a9-2fc0-47f6-a3fd-7256c13709b7" />

Kuva 1. Purkaaminen

Annetaan suoritusoikeus:

```
chmod +x VMware-Workstation-Full-25H2u1-25219725.x86_64.bundle
```

Kuvassa vielä kertaalleen annetut komennot.

<img width="800" height="285" alt="Image" src="https://github.com/user-attachments/assets/0d6eba66-9d46-454e-aedc-f177985d0755" />

Kuva 2. Asennus suoritettu!

Kun lähdin purkamaan tiedostoa, sain ilmoitukseksi, että tila on loppunut. Tämän jälkeen lisäsin muistitilaa Oraclessa, mutta sekään ei auttanut. Tämän jälkeen kokeilin gpartedia:

<img width="780" height="301" alt="Image" src="https://github.com/user-attachments/assets/ed2cb331-1cb9-4955-a715-8442a8d8f8fe" />

Kuva 3. gparted.


Seuraavaksi käynnistin asennusohjelman komennolla: 

```
sudo ./VMware-Workstation-Full-25H2u1-25219725.x86_64.bundle
```


###### 17:33 
###### 18:37

Tässä vaiheessa en ollut tietoinen siitä, että pitääkö tiedostot purkaa koneelle? Tässä kohtaa siirryin työstämään kotitehtäviä.

Mininetin asennus, komennolla:

```
sudo apt update
sudo apt install mininet -y
```

######

a) Aja tunnilla esitetty ARP hyökkäys ja tutki, miten se toimii.

Asennetaan Scrapy ohjeiden mukaisesti:
```
sudo apt install python3-scapy -y
```

Käynnistetään verkkotopologia:
```
cd ~/Lataukset/labs/01-Network-Security-Lab/scripts
```
ja lopuksi mininetin käynnistys:
```
sudo python3 hub_topo.py
```
<img width="793" height="286" alt="Image" src="https://github.com/user-attachments/assets/45c76356-bf9a-4620-9be7-d6818ea5fc0b" />

Kuva 4. Mininetin käynnistys

Syötän mininettiin komennot:
```
mininet> h1 python3 udp_server.py &
mininet> h2 python3 udp_client.py &
mininet> h3 python3 arp_poison.py
Poisoning ARP cache of 10.0.0.1 and 10.0.0.2
```
<img width="463" height="76" alt="Image" src="https://github.com/user-attachments/assets/b7ac4750-2af1-4b32-8a8b-b8ba1f380e17" />

Kuva 5. Terminaalin näkymä

Itse tehtävästä: Suoritin ARP-myrkytyshyökkäyksen, jossa hyökkääjä (H3) lähetti väärennettyjä ARP-viestejä uhreille (H1 ja H2). Hyökkäys hyödyntää ARP-protokollan luottamusta: uhrit saatiin uskomaan, että vastapuolen IP-osoite kuuluu hyökkääjän MAC-osoitteelle. Tämän seurauksena uhrien välinen liikenne ohjautui hyökkääjän kautta, mikä mahdollisti datan salakuuntelun. Hyökkäyksen onnistuminen varmistettiin tarkistamalla uhrien ARP-taulukot, joissa näyttäytyi hyökkääjän fyysinen osoite kohteen kohdalla.

Suljen tehtävien ajaksi Internetyhteyden, jotta tehtävien tekeminen tapahtuu turvallisesti. Tämä ei ollut kuitenkaan tarpeellista, koska Mininetissä harjoittelu on turvallista.

###### 19:05

b) Samassa hakemistossa on myös ICMP Spoofing ja TCP Session Hijacking. Aja molemmat labrat läpi ja kerro, miten molemmat tekniikat toimivat.

ICMP Spoofing (b1):

    H1 (Kuuntelija): h1 python3 sniff_icmp.py & (Tämä havaitsee paketit).
    H2 (Uhri): h2 ping 10.0.0.1 (Normaali ping-yhteys).
    H3 (Hyökkääjä): h3 python3 spoof_icmp.py (Väärentää vastaukset).

<img width="659" height="159" alt="Image" src="https://github.com/user-attachments/assets/c54f8846-e3fa-4e4b-acdb-21b975058ed0" />

Kuva 6. ICMP Spoofing

TCP Session Hijacking (b2):

    H1 (Palvelin): h1 python3 tcp_server.py &
    H2 (Asiakas): h2 python3 tcp_client.py &
    H3 (Hyökkääjä): h3 python3 sniff_tcp_session.py & (Haistelee sekvenssinumerot).
    H3 (Hyökkääjä): h3 python3 tcp_hijack.py (Syöttää väärennetyn paketin).

<img width="613" height="134" alt="Image" src="https://github.com/user-attachments/assets/db034c56-af99-4791-9524-e5e2d9c82cae" />

Kuva 7. TCP Session Hijacking

ICMP Spoofingissa hyökkääjä lähettää väärennettyjä ohjaus / vastauspaketteja uhrille, mikä mahdollistaa verkkoliikenteen harhaanjohtamisen. TCP Session Hijackingissa mennään askeleen edelle, eli siinä hyökkääjä kaappaa jo käynnissä olevan luotetun yhteyden ennustamalla TCP-sekvenssinumerot. Tällöin hyökkääjä voi syöttää omia komentojaan suoraan istuntoon uhrin nimissä.

###### 19:41
###### 19:50

c) Hakemistossa 02-SDN-DDos_Simulation tryout-kansiossa on työkalut, jotta voit ajaa TCP SYN-Flood-hyökkäyksen turvallisesti. Kirjoita, miten ajoit hyökkäyksen ja miten kyseinen hyökkäys toimii.

Siirtyminen kansioon: 
```
cd ~/Lataukset/labs/02-SDN_DDoS_Simulation-tryout/
```
Verkon puhdistaminen:
```
sudo mn -c
```
Verkon käynnistäminen:
```
sudo python3 simple_tree_top.py
```


Ajoin TCP SYN-Flood -hyökkäyksen käyttämällä tree_topology.py -skriptiä. Skripti loi automaattisen simulaation, jossa eri isäntäkoneet (kuten host5 ja host4) vuorotellen suorittivat hyökkäyksiä ja normaaleja tietoliikennepyyntöjä. Simulaatio hyödynsi SDN-verkkotopologiaa hyökkäyksen vaikutusten analysointiin.

<img width="591" height="190" alt="Image" src="https://github.com/user-attachments/assets/a5c6a9e4-ea23-41ab-af45-510329ffd0b4" />


Kuva 7. Näkymä terminaalissa TCP SYN-Floodia tehdessä.

TCP SYN-Flood on palvelunestohyökkäys (DoS), joka perustuu TCP-protokollan kolmivaiheisen kättelyn väärinkäyttöön. Hyökkääjä tarkoituksena on lähettää kohteeseen suuren määrän SYN-paketteja (pyyntöjä), mutta ei koskaan vastaa palvelimen lähettämiin SYN-ACK-viesteihin. Tällä hyökkääjä tavoittelee sitä, että kulutetaan palvelimen resursseja ja estetään laillisten käyttäjien pääsyn palveluun.




###### 20:55 

d) Vapaaehtoinen tutustu myös seuraaviin työkaluihin

https://evilginx.com/
https://github.com/utoni/ptunnel-ng

Kerro kyseisistä työkaluista, mitä ne tekevät, saitko asennettua ne, lisää ohjeraporttiin ja olivatko kyseiset työkalut mielenkiintoisia, jos olivat, niin miksi? Pohdi raportissasi, mihin ja missä tilanteissä kyseisiä työkaluja voidaan käyttää? Arvioi, onko käyttö kohde moraalisesti oikein tai väärin.

Ptunnel-ng asennus:

```
sudo apt update
sudo apt install ptunnel-ng
```
Esimerkki, kun tunneloidaan:

```
sudo ptunnel-ng
```

Ptunnel-ng (Ping Tunnel New Generation) on työkalu, joka kapseloi muun liikenteen sallitun ICMP-protokollan (ping) sisään, mahdollistaen tiedonsiirron tiukasti rajoitetuissa verkoissa. Menetelmä mahdollistaa palomuurien kierron, mikä on hyödyllistä sensuurin kiertämisessä, mutta voi väärinkäytettynä vaarantaa yritysten tietoturvan tai kiertää maksullisia palveluita.

Eettisesti työkalu riippuu tilanteesta. Mikäli käyttäjä / henkilö asuu maassa, jossa on tiukat säännöt, kuten sananvapaudessa, ptunnel-ng työkalu on tähän oiva tapa ohittaa esteet. Esimerkkinä, jossa henkilö on kafkamaisessa tilanteessa, jossa sananvapautta on rajoitettu - on tunnelointi skeä moraalisesti että eettisesti perusteltua ja oikein. Lisäksi, kun agendalla halutaan edistää hyvää.

Eettisesti väärin, mikäli henkilö altistaa yrityksen tietoturvan vaaraan, tai henkilö rikkoo lakia sekä toiminnallaan toimii yhteiskunnan asettaminen normien vastaisesti. Kuluttajana on epäeettistä ohittaa, esimerkiksi maksumuuri(t), kuten maksullinen Wi-fi. Työkalu mahdollistaa maksumuurien ohittamisen, mutta on epäeettistä, että tunneloidaan näin läpi.

Evilgnix Pro lataaminen ei onnistunut. Yritin myös Evilgnix2, mutta sekään ei onnistunut. 

Exilgnix Pro on kehittynyt tietoturvatyökalu, joka on suunniteltu simuloimaan nykyaikaisia tietojenkalasteluhyökkäyksiä (phishing). Sen eettisyys riippuu täysin sen käyttötarkoituksesta: se on ammattilaisten työkalu suojautumisen parantamiseen, mutta väärissä käsissä se on vaarallinen ase, sillä sen kriittisin ominaisuus on kyky ohittaa monivaiheinen tunnistautuminen (MFA) varastamalla hyväksyttyjä istuntoevästeitä, mikä antaa hyökkääjälle pääsyn tilille ilman salasanaa. Työkalun Pro-versio tehostaa tätä automaatiolla ja hienostuneella verkkotunnusten hallinnalla, tehden hyökkäyksistä vaikeammin havaittavia.

Eettisyys:

Valkohattu, kuten tietoturvakonsultti on eettinen käyttjä. Kun tietoturva-asiantuntija testaa yrityksen turvallisuutta / puolustusta - hän voi käyttää tähän kyseistä ohjelmaa. Työkalun avulla hän voi löytää heikkoudet ja opettaa esimerkiksi henkilöstöä välttämään / turvautumaan näiltä.

Valkohattu, kuten tietoturvakonsultti on eettinen käyttjä. Kun tietoturva-asiantuntija testaa yrityksen turvallisuutta / puolustusta - hän voi käyttää tähän kyseistä ohjelmaa. Työkalun avulla voidaan etsiä ja löytää heikkouksia yrityksen kyberturvallisuudessa sekä opettamaan henkilöstöä välttämään näitä hyökkäyksiä.

Epäeettinen toiminta pohjautuu rikollisuteen, kuten rahan varastamiseen tai yrityssalaisuuksien varastamiseen. 

Ohjelmiston kehittäjä Kuba Gretzky kehitti työkalun organisaatioiden hyväksi, ja jotta ihmiset ymmärtäisivät, että perinteiset MFA-menetelmät eivät ole murtumattomia.


###### 24.4.2026.
###### 21:50 

###### 25.5.2026
###### 5:38 

Ennen tehtävien palauttmista päätin yrittää vielä kerran, mikäli saisin Evilgnixin ladattua virtuaalikoneeseen.




Lähteet
===

Evilgnix Pro 2026. Luettavissa: https://evilginx.com/ Luettu: 24.4.2026.

Git-Hub. Utoni. 27.11.2024. p-tunnel-ng. Luettavissa: https://github.com/utoni/ptunnel-ng. Luettu: 24.4.2026.

Joonas Janttonen 2026. GitHub. Luettavissa: https://github.com/JoonasJanttonen/Verkkoon-tunkeutuminen-ja-tiedustelu/tree/main. Luettu: 23.4.2026.


