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

Moodlen kautta tutustun oppitunnin aiheisiin. Samalla lataan WMWAREN virtuaaalikoneeseen sekä purkaan tiedostot.

<img width="434" height="188" alt="Image" src="https://github.com/user-attachments/assets/388dd6a9-2fc0-47f6-a3fd-7256c13709b7" />

Kuva 1.

Annan tiedostolle suoritusoikeuden:

```
chmod +x VMware-Workstation-Full-25H2u1-25219725.x86_64.bundle
```

Kuvassa vielä kertaalleen annetut komennot.

<img width="800" height="285" alt="Image" src="https://github.com/user-attachments/assets/0d6eba66-9d46-454e-aedc-f177985d0755" />

Kuva 2. Asennus suoritettu!

Yritin purkaa tiedoston, mutta tilan puutteen vuoksi en päässyt sitä tekemään. Oraclen kautta lisäsin muistitilaa, mutta sekään ei auttanut. Kokeilin vielä gpartedia:

<img width="780" height="301" alt="Image" src="https://github.com/user-attachments/assets/ed2cb331-1cb9-4955-a715-8442a8d8f8fe" />

Kuva 3. gparted.


###### 17:33 





Tämän jälkeen käynnistän asennusohjelman komennolla: 

```
sudo ./VMware-Workstation-Full-25H2u1-25219725.x86_64.bundle
```

a) Aja tunnilla esitetty ARP hyökkäys ja tutki, miten se toimii.

