# Homelab: Forberedelser og installasjon

## Sjekk av systemkrav

### Minimum maskinvarekrav
1. Prosessor (CPU):
   - 64-bit prosessor med virtualiseringsstøtte
   - Minst 2 kjerner tilgjengelig for virtualisering

2. Minne (RAM):
   - Minimum 8GB RAM totalt på maskinen
   - 2GB skal dedikeres til den virtuelle maskinen

3. Lagring:
   - Minimum 50GB ledig diskplass
   - SSD anbefales for bedre ytelse

### Sjekk virtualiseringsstøtte

Du kan lese mer om virtualiseringsstøtte [her](homelab1.2.1-hyperv.md), som 
også inkluderer instruksjoner for å aktivere virtualiseringsstøtten.

1. Windows:
   - Åpne Oppgavebehandling (Ctrl+Shift+Esc)
   - Gå til fanen "Ytelse"
   - Under "Prosessor", se etter "Virtualisering: Aktivert"

2. BIOS/UEFI:
   - Virtualisering må være aktivert
   - Kalles ofte VT-x (Intel) eller AMD-V (AMD)

> #### Får du ikke aktivert virtualiseringsstøtte?
>
> Selv om hardware-virtualisering ikke er aktivert, kan det være du kan sette
> opp en fungerende VM. Du kan prøve å gå videre uten at virtualiseringsstøtten
> er aktivert korrekt. Hvis du da får problemer med å kjøre VM, kan det være
> på grunn av at virtualiseringsstøtten ikke er aktiv.

## Programvare-installasjon

### VirtualBox
1. Last ned VirtualBox:
   - Gå til https://www.virtualbox.org/wiki/Downloads
   - Velg versjon for ditt operativsystem
   - Last ned også "Extension Pack"

2. Installer VirtualBox:
   - Kjør installasjonsfilen
   - Følg standard installasjonsvalg
   - Start maskinen på nytt etter installasjon

3. Installer Extension Pack:
   - Dobbeltklikk på nedlastet Extension Pack
   - Følg installasjonsveiviseren

### Ubuntu Server ISO
1. Last ned Ubuntu Server:
   - Gå til https://ubuntu.com/download/server
   - Velg LTS (Long Term Support) versjonen
   - Last ned ISO-filen (ca 1GB)

2. Verifiser nedlastingen:
   - Noter hvor ISO-filen ble lagret
   
   > _Ekstra-oppgave: verifiser nedlastingen_
   >- Sjekk at ISO-filen du har lastet ned ikke er korrupt ved å bruke SHA-hash
   >- [Se her](./homelab1.2.2-hash.md) for informasjon om hvordan du går frem.


## Verktøy for dokumentasjon
- Bruk en valgfri teksteditor
   - VS Code eller Notepad++ er gode teksteditorer, som også egner seg til 
   å skrive / redigire script-filer.
   - Notisblokk, WordPad eller MS Word e.l. fungerer også fint for å 
   dokumentere arbeidet ditt.
- Opprett en mappe for prosjektdokumentasjon
- Start en loggfil (tekstfil) for prosjektet, som du bruker til å notere 
underveis.

## Sjekkliste før du fortsetter
- [ ] Virtualiseringsstøtte er aktivert
- [ ] VirtualBox er installert og fungerer
- [ ] Extension Pack er installert
- [ ] Ubuntu Server ISO er lastet ned
- [ ] Tekstfil for logging og dokumentering opprettet

## Neste steg
Når alle punkt på sjekklisten er oppfylt, er du klar til å begynne med oppsett av den virtuelle maskinen. Ta deg tid til å sjekke at alt er klart - det gjør resten av prosjektet enklere.

## Problemløsning
- Hvis virtualiseringsstøtte mangler:
  - Sjekk BIOS/UEFI-innstillinger
  - Søk etter veiledning for din PC-modell
- Ved installasjonsproblemer med VirtualBox:
  - Se etter feilmeldinger
  - Sjekk VirtualBox sin dokumentasjon
  - Noter eventuelle feilmeldinger