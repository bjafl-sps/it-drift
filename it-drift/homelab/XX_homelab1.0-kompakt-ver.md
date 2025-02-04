# Prosjektinstruks: Første Homelab - Virtuell Webserver

## Forberedelser

### Last ned nødvendig programvare
1. VirtualBox: https://www.virtualbox.org/wiki/Downloads
2. Ubuntu Server: https://ubuntu.com/download/server
3. VS Code eller Notepad++

### Systemkrav
- Minimum 8GB RAM tilgjengelig
- 50GB ledig diskplass
- Prosessor som støtter virtualisering

## Oppgaver og gjennomføring

### Del 1: Grunnoppsett
1. Installer VirtualBox på din maskin
2. Opprett en ny virtuell maskin:
   - Navn: "webserver01"
   - Type: Linux
   - Version: Ubuntu 64-bit
   - RAM: 2048 MB
   - Harddisk: 20 GB (dynamisk allokert)
   - Nettverk: Bridged Adapter

### Del 2: Installasjon av operativsystem
1. Start den virtuelle maskinen
2. Velg Ubuntu Server ISO som boot-medium
3. Følg installasjonsveiviseren:
   - Velg språk: English
   - Velg minimal serverinstallasjon
   - Sett opp brukernavn og passord
   - Noter ned alle valg du gjør

### Del 3: Grunnleggende systemkonfigurasjon
1. Logg inn på serveren
2. Oppdater systemet:
   ```bash
   sudo apt update
   sudo apt upgrade
   ```
3. Konfigurer statisk IP:
   - Dokumenter nåværende nettverksoppsett
   - Endre til statisk IP via Netplan
   - Test at nettverket fungerer

### Del 4: Webserver
1. Installer Apache:
   ```bash
   sudo apt install apache2
   ```
2. Sjekk status:
   ```bash
   sudo systemctl status apache2
   ```
3. Konfigurer brannmur:
   ```bash
   sudo ufw allow 'Apache'
   sudo ufw enable
   ```

### Del 5: Sikkerhet
1. Sett opp SSH:
   - Generer SSH-nøkkelpar
   - Konfigurer SSH-tilgang
   - Deaktiver passordinnlogging
2. Oppdater brannmurregler for SSH

## Dokumentasjon

Før logg over:
1. Alle kommandoer du bruker
2. Konfigurasjonsendringer
3. Problemer du støter på og hvordan du løser dem
4. Nettverksoppsett
5. Sikkerhetsinnstillinger

## Tips
- Ta backup av konfigurasjoner før endringer
- Test endringer før du dokumenterer
- Noter ned feilmeldinger
- Bruk offisiell Ubuntu-dokumentasjon ved behov

## Egenvurdering
Når du er ferdig, sjekk at du kan:
- Logge inn via SSH
- Se websiden fra en annen maskin
- Forklare grunnleggende om nettverksoppsettet
- Gjenopprette systemet ved behov

## Neste steg
Når grunnoppsettet fungerer, vurder å:
- Sette opp en egen webside
- Konfigurere HTTPS
- Sette opp automatisk sikkerhetskopiering
- Legge til overvåking