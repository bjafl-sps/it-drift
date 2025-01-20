# Virtualiseringsstøtte: Hva, hvorfor og hvordan

## Hva er virtualiseringsstøtte?
Virtualiseringsstøtte er maskinvarefunksjoner i moderne prosessorer som gjør det mulig å kjøre virtuelle maskiner effektivt. Dette er bygget inn i prosessoren og må ofte aktiveres spesifikt i BIOS/UEFI.

## Hvorfor er det viktig?
- Muliggjør effektiv kjøring av virtuelle maskiner
- Gir bedre ytelse for virtuelle systemer
- Nødvendig for å kjøre 64-bit gjestesystemer
- Kreves for moderne virtualiseringsverktøy

## Hvordan sjekke status

I Windows kan du sjekke status for virtualiseringsstøtte på flere ulike måter:

1. **Bruk Oppgavebehandling**
   - Trykk Ctrl + Shift + Esc
   - Velg fanen "Ytelse"
   - Se etter "Virtualisering: Aktivert/Deaktivert"

2. **Bruk Systeminformasjon**
   - Åpne Kjør-dialogen \[Win + R\]
   - Skriv `msinfo32` og trykk \[Enter\]
   - Se etter linjen "Virtualization Enabled In Firmware: Yes/No"

3. **Bruk PowerShell**
   - Åpne _Terminal_ eller _PowerShell_

      > _Slik åpner du et nytt terminalvindu:_
      >- Fra startmenyen
      >- Bruk Kjør-dialogen \[Win + R\], skriv `powershell` og trykk \[Enter\]
      >- Bruk _Power User Menu:_ Trykk [Win + X] og velg _Terminal_ fra menyen

   - Skriv inn følgende kommando, og trykk \[Enter\]

   ```powershell
   Get-ComputerInfo -Property "HyperVRequirements*"
   ```
   - Kommandoen under kan også brukes.
      - Se etter `True` under `VirtualizationFirmwareEnabled`
   ```powershell
   Get-CimInstance CIM_Processor | Select-Object Name,VirtualizationFirmwareEnabled
   ```
   

## Aktivere virtualiseringsstøtte

Hvis virtualiseringsstøtte ikke er aktivert, kan det være at dette må aktiveres
i datamaskinens BIOS-instillinger

### BIOS/UEFI-innstillinger
1. Slå av maskinen. Skru den på og gå inn i BIOS/UEFI. Dette gjøres ved å trykke
   en av tastene på tastaturet i det maskinen skrur seg på. 
   - Vanlige taster: F2, F10, F12, eller Del

2. Finn riktig innstilling:
   - Se etter "Virtualization Technology" eller lignende
   - Navnet på instillingen er avhengig av prosessortype:
      - Intel: "Intel VT-x", "Intel Virtualization Technology"
      - AMD: "AMD-V", "SVM Mode"

   > _Vanlige plasseringer i BIOS/UEFI:_
   >- Under "CPU Configuration"
   >- Under "Security Settings"
   >- Under "System Configuration"
   >- Under "Advanced Settings"

3. Aktiver innstillingen. Lagre og lukk BIOS-menyen.
   - Dette heter gjerne 'Exit Saving Changes'
   - Maskinen vil da starte på nytt.

### Aktiver Windows Hypervisor Platform

1. Åpne Windows-funksjoner:
   - Åpne Kjør-dialogen [Win + R]
   - Skriv `optionalfeatures.exe`
   - Trykk Enter

2. Finn og kryss av for disse funksjonene:
   - Windows Hypervisor Platform
   - Virtual Machine Platform
   - Hyper-V (valgfritt, aktiver hvis tilgjengelig)

3. Klikk OK og restart PC-en

Du kan også aktivere via _PowerShell_. Kjør som administrator og skriv inn 
kommandoen under:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
```

Du kan også prøve å aktivere _Hyper-V_ med kommandoen under. Dette er valgfritt, 
og det kan være du får feilmelding hvis funksjonen ikke er tilgjengelig på
din PC.

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName HypervisorPlatform
```

> **Obs:**
> Etter aktivering må du restarte PC-en for at endringene skal tre i kraft.

## Feilsøking

### Vanlige problemer:
1. Finner ikke virtualiseringsinnstillinger / kommer ikke inn i BIOS-meny
   - Se etter "Enter Setup" melding som kan komme opp rett etter du skrur 
   på PC.
      - Om du ser meldingen, står det hvilken tast du skal trykke for å 
      gå inn i BIOS-menyen
   - Sjekk PC/motherboard manual 
   - Søk etter modellspesifikk guide

   > _Finne dokumentasjon_:
   >- Bruk _Systeminfo_ ved å kjøre `msinfo32` i Kjør-dialogen \[Win + R\] 
   >- På laptop: Finn laptopens produktnavn under 'Systemmodell'
   >- På stasjonær: Finn hovedkortets produsent og modell 'Hovedkort...'
   >- Søk på internett etter navn på laptop eller hovedkort, for å finne
      informasjon om å åpne BIOS-meny og/eller aktivere virtualisering.

2. Virtualiseringsstøtte fortsatt deaktivert i Windows etter aktivering 
   og omstart av PC.
   - Dobbeltsjekk at endringer ble lagret i BIOS
   - Sjekk om Windows Hypervisor Platform er aktivert

> ### _Fortsatt problemer?_
>- Noen antivirusprogrammer kan blokkere virtualisering
>- Eldre prosessorer støtter kanskje ikke virtualisering
>- Spør gjerne om hjelp!

## Verifisering etter aktivering
1. Start maskinen på nytt
2. Sjekk status i Windows
3. Test med VirtualBox
4. Dokumenter eventuelle feilmeldinger