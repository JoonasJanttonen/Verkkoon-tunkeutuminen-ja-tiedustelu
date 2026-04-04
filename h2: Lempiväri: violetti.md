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
