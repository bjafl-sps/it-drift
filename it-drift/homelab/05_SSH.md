# SSH Oppsett og Testing

## 1. SSH-oversikt

SSH (Secure Shell) er en kryptert nettverksprotokoll for sikker tilkobling til servere. Vi skal:
1. Bekrefte SSH-status
2. Generere SSH-nøkler
3. Overføre nøkkel til server
4. Teste tilkobling
5. Sikre SSH-konfigurasjonen

## 2. Verifiser SSH-status

På serveren:
```bash
# Sjekk SSH-status
sudo systemctl status ssh

# Sjekk hvilken port som lyttes på
sudo ss -tulpn | grep ssh
```

## 3. Generer SSH-nøkler

På din lokale maskin (Windows):
```bash
# Generer ny SSH-nøkkel
ssh-keygen -t ed25519 -C "homelab"

# Nøklene lagres vanligvis i:
# C:\Users\<brukernavn>\.ssh\id_ed25519 (privat nøkkel)
# C:\Users\<brukernavn>\.ssh\id_ed25519.pub (offentlig nøkkel)
```

## 4. Overfør nøkkel til server

### Metode 1: ssh-copy-id (Linux/Mac)
```bash
ssh-copy-id brukernavn@server-ip
```

### Metode 2: Manuell (Windows)
```bash
# Vis offentlig nøkkel
type C:\Users\<brukernavn>\.ssh\id_ed25519.pub

# Kopier innholdet

# På serveren:
mkdir -p ~/.ssh
nano ~/.ssh/authorized_keys
# Lim inn den offentlige nøkkelen
```

## 5. Test tilkobling

```bash
# Test SSH-tilkobling
ssh brukernavn@server-ip

# Hvis alt er riktig, skal du nå logge inn uten passord
```

## 6. Vanlige problemer

### Problem: Tilkobling nektes
Sjekk:
- IP-adresse er korrekt
- SSH-tjenesten kjører
- Brannmur tillater SSH
- Rettigheter på .ssh-mappe

### Problem: Nøkkel aksepteres ikke
Sjekk:
- Rettigheter på .ssh-mappe og filer
```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

## 7. Dokumentasjon
Noter:
- Server IP
- SSH-port
- Plassering av nøkler
- Eventuelle spesielle konfigurasjoner

## Verifisering
- [ ] SSH-tjeneste kjører
- [ ] Nøkler generert
- [ ] Nøkkel overført til server
- [ ] Passordløs innlogging fungerer
- [ ] Rettigheter er korrekte

Dette gir deg et grunnleggende, sikkert SSH-oppsett. Neste steg vil være å forbedre sikkerheten ytterligere ved å deaktivere passordinnlogging og konfigurere andre sikkerhetstiltak.