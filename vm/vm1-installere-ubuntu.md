# Installasjon av VirtualBox

1. Last ned VirtualBox
   - Gå til [virtualbox.org](https://www.virtualbox.org/)
   - Velg "Downloads"
   - Last ned versjonen som passer ditt operativsystem (Windows/MacOS/Linux)
   - Kjør installasjonsfilen og følg veiviseren

2. Sjekk systemkrav før du starter
   - Minimum 4GB RAM tilgjengelig
   - Minst 25GB ledig lagringsplass
   - Prosessor som støtter virtualisering (de fleste moderne prosessorer)

# Oppsett av virtuell maskin i VirtualBox

1. Last ned Ubuntu
   - Gå til [ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
   - Last ned nyeste LTS-versjon (Long Term Support)

2. Opprett ny virtuell maskin i VirtualBox
   - Klikk "New" eller "Ny"
   - Gi maskinen et navn (f.eks. "Ubuntu-VM")
   - Velg type: Linux
   - Velg versjon: Ubuntu (64-bit)
   - Klikk "Next"

3. Konfigurer ressurser
   - Tildel minne (RAM): Minimum 4GB (4096 MB) anbefales
   - Opprett en ny virtuell harddisk
   - Velg VDI (VirtualBox Disk Image)
   - Dynamisk allokert lagring
   - Sett størrelse: Minimum 25GB

4. Konfigurer systeminnstillinger
   - Velg din nye VM og klikk "Settings"
   - Under "System":
     - Aktiver EFI (hvis tilgjengelig)
     - Sett boot-rekkefølge (Optical/Hard Disk)
   - Under "Display":
     - Sett video-minne til minimum 128MB
     - Aktiver 3D-akselerasjon
   - Under "Storage":
     - Velg den tomme optical drive
     - Velg Ubuntu ISO-filen du lastet ned

# Installasjon av Ubuntu

1. Start den virtuelle maskinen
   - Velg din VM og klikk "Start"
   - Velg "Try or Install Ubuntu"

2. Installer Ubuntu
   - Velg språk
   - Velg "Install Ubuntu"
   - Velg tastaturoppsett
   - Velg "Normal installation"
   - Ved "Installation type", velg "Erase disk and install Ubuntu" 
     (dette er trygt siden det er en virtuell maskin)
   - Velg tidssone
   - Opprett brukerkonto:
     - Skriv inn navn
     - Velg datamaskinnavn
     - Velg brukernavn
     - Lag et sterkt passord

3. Vent på at installasjonen fullføres
   - Dette kan ta 15-30 minutter
   - Når installasjonen er ferdig, velg "Restart Now"

4. Etter omstart
   - Logg inn med brukernavn og passord
   - Installer Guest Additions:
     - I VirtualBox-menyen: Devices > Insert Guest Additions CD
     - Følg instruksjonene for installasjon
     - Restart VM når det er fullført

5. Første oppstart
   - Kjør programvareoppdateringer:
     ```bash
     sudo apt update
     sudo apt upgrade
     ```
   - Test at alt fungerer som det skal
   - Sjekk at nettverkstilkobling fungerer
   - Test at skjermoppløsning og kopier/lim inn fungerer

Nå har du en fungerende Ubuntu virtuell maskin klar til bruk!