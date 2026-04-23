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


a) Aja tunnilla esitetty ARP hyökkäys ja tutki, miten se toimii.
