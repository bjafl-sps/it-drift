# Bli kjent med terminalen

Terminalen er et tekstbasert grensesnitt for å kommunisere med datamaskinen din. I stedet for å klikke med musen, skriver du kommandoer som forteller datamaskinen nøyaktig hva du vil den skal gjøre. Selv om det kan virke skummelt i begynnelsen, gir terminalen deg kraftige verktøy for å jobbe mer effektivt. Mange utviklere foretrekker terminalen fordi den gir mer presis kontroll og mulighet for automatisering av oppgaver.

## Kommandolinjeprosessor (skall)

Et skall er programmet som tolker kommandoene du skriver i terminalen. Tenk på det som en tolk mellom deg og datamaskinens operativsystem. Når du skriver en kommando, er det skallet som:
1. Leser det du har skrevet
2. Tolker hva du mener
3. Utfører handlingen
4. Viser resultatet tilbake til deg

### Ulike skall (engelsk: shell)

Akkurat som det finnes mange forskjellige programmeringsspråk, finnes det flere typer skall. Hvert skall har sine egne fordeler og spesialiteter, men de grunnleggende prinsippene er like. De mest vanlige er:
- Bash (Bourne Again Shell)
- Zsh (Z Shell)
- PowerShell (Windows)
- Fish (Friendly Interactive Shell)

#### UNIX / Linux

På Unix-baserte systemer (som Linux og macOS) er Bash det mest utbredte skallet. Det kommer som standard på de fleste Linux-distribusjoner og er kjent for å være:
- Kraftig og fleksibelt
- Godt dokumentert
- Kompatibelt med eldre Unix-skall
- Støttet av et stort brukerfellesskap

macOS brukte tidligere Bash som standard, men har nå byttet til Zsh, som er en modernisert versjon med flere funksjoner.

#### Windows

Windows har to hovedtyper skall:
1. __Command Prompt (cmd.exe)__
   - Det tradisjonelle Windows-skallet
   - Begrenset funksjonalitet
   - Bruker forskjellig syntaks fra Unix-skall

2. __PowerShell__
   - Moderne og kraftig
   - Objektorientert tilnærming
   - Bedre integrasjon med Windows-systemer
   - Kan også installeres på Linux og macOS

Windows 10 og nyere støtter også Windows Subsystem for Linux (WSL), som lar deg kjøre et fullverdig Linux-system direkte i Windows. Dette gir deg tilgang til Bash og andre Unix-verktøy.
## Filbaner og navigering

På datamaskinen din er filer organisert i et hierarki av mapper (også kalt kataloger). Det er noen fundamentale forskjeller i hvordan Windows og Unix-baserte systemer (Linux, macOS) organiserer dette hierarkiet:

Windows filsystem:
- Starter med en diskbokstav (f.eks. C:, D:)
- Hovedstasjonen er vanligvis C:
- Bruker backslash (\) som skilletegn
- Standard mappestruktur:
  - C:\Windows - systemfiler
  - C:\Program Files - installerte programmer
  - C:\Users - brukermapper
  - C:\Users\dittnavn - din personlige mappe
- Eksempel filbane: `C:\Users\dittnavn\Documents\fil.txt`
- Skiller ikke mellom store og små bokstaver (ikke case-sensitive)

Unix/Linux filsystem:
- Starter fra en enkelt rotmappe (/)
- Ingen diskbokstaver - andre disker "mountes" inn i filsystemet
- Bruker vanlig skråstrek (/) som skilletegn
- Standard mappestruktur:
  - /bin - grunnleggende systemkommandoer
  - /home - brukermapper
  - /home/dittnavn - din personlige mappe
  - /usr - programmer og data
  - /etc - konfigurasjonsfiler
- Eksempel filbane: `/home/dittnavn/dokumenter/fil.txt`
- Skiller mellom store og små bokstaver (case-sensitive)

Når du jobber med stier i terminalen, er det viktig å være klar over disse forskjellene. For eksempel vil en Windows-sti som `C:\Users\John\Documents` måtte skrives som `/home/john/dokumenter` på et Unix-system. I moderne Windows kan du ofte bruke fremoverskråstrek `/` i stedet for bakoverskråstrek `\`, men dette er ikke garantert å fungere i alle programmer.

### Arbeidsmappe (engelsk: Working Directory)

Når du jobber i terminalen, er du alltid i en bestemt mappe. Dette er arbeidsmappen din, og alle relative filbaner tar utgangspunkt i denne. Tenk på det som "hvor du står" i filsystemet. Kommandoen `pwd` (print working directory) viser hvor du er.


### Relative og absolutte filbaner

Det finnes to måter å spesifisere en filbane:

1. Absolutt filbane:
   - Starter fra roten av filsystemet
   - Begynner med `/` (Linux/Unix) eller en stasjonsbokstav `C:\` (Windows)
   - Beskriver hele veien til filen
   - Eksempel: 
        - `/home/bruker/dokumenter/rapport.txt` (Linux)
        - `C:\Users\bruker\Documents\rapport.txt` (Windows)
   - Fungerer uansett hvor du er i filsystemet

2. Relativ filbane:
   - Beskriver veien fra der du er nå (arbeidsmappen)
   - Bruker spesielle symboler:
     - `.` betyr "nåværende mappe"
     - `..` betyr "opp én mappe"
   - Eksempel: 
     - `../dokumenter/rapport.txt` (Linux)
     - `..\dokumenter\rapport.txt` (Windows)
   - Kortere å skrive, men avhenger av hvor du er

### Navigering

For å bevege deg mellom mapper bruker du kommandoen `cd` (change directory). Her er noen vanlige måter å bruke den på:

```bash
cd dokumenter       # Går inn i mappen "dokumenter"
cd ..               # Går opp én mappe
cd ~                # Går til din hjemmappe (Linux)
cd ~/dokumenter     # Går til dokumenter i hjemmemappen (Linux)
cd /                # Går til rotmappen
cd -                # Går tilbake til forrige mappe du var i
```

Tips: 
- Bruk Tab-tasten for automatisk fullføring av mappenavn
- Hvis et mappenavn inneholder mellomrom, må du bruke anførselstegn: `cd "Mine Dokumenter"`

### Skriv ut mappeinnhold og fildetaljer

For å se innholdet i en mappe bruker du `ls` (list). Dette fungerer både i Linux og om du bruker terminal / PowerShell på Windows. Om du bruker det eldre skallet `cmd` på Windows, må man i stedet bruke kommandoen `dir`. Ved å kjøre `ls` (eller `dir`) skrives det ut en liste over filer og mapper som finnes i arbeidsmappen (eller i en annen mappe om man bruker argumenter, mer om dette senere).

## Bash

Bash er ikke bare et skall, det er også et skriptspråk. Dette betyr at du kan:
- Kombinere kommandoer
- Lage variabler
- Bruke kontrollstrukturer (if, for, while)
- Lagre sekvenser av kommandoer i filer (skript)

### Viktige kommandoer

Her er de mest grunnleggende kommandoene du bør kjenne til:

Filsystem:
```bash
pwd                    # Vis nåværende mappe
ls                     # List filer og mapper
cd mappenavn           # Bytt mappe
mkdir mappenavn        # Lag ny mappe
rmdir mappenavn        # Slett tom mappe
touch filnavn          # Lag ny tom fil
rm filnavn             # Slett fil
cp kilde mål           # Kopier fil
mv gammel ny           # Flytt/omdøp fil
```

Visning og redigering:
```bash
cat fil.txt            # Skriv ut hele filen til terminal
less fil.txt           # Vis filen side for side
head fil.txt           # Skriv ut første 10 linjer til terminal
tail fil.txt           # Skriv ut siste 10 linjer til terminal
nano fil.txt           # Åpne fil i Nano editor
```

Systeminfo:
```bash
date                   # Vis dato og tid
whoami                 # Vis brukernavn
df -h                  # Vis diskplass
free -h                # Vis minnebruk
top                    # Vis kjørende prosesser
```

### STORE og små bOKstAvER

I Unix-systemer er store og små bokstaver forskjellige. Dette betyr at:
- `Dokument.txt`, `dokument.txt` og `DOKUMENT.TXT` er tre forskjellige filer
- Kommandoer som `LS` eller `Ls` vil ikke fungere, det må være `ls`
- Dette gjelder også mappenavn og nesten alt annet i terminalen

Dette er en vanlig kilde til feil for nybegynnere, så vær ekstra oppmerksom på dette.

### Argumenter og parametre

Kommandoer kan ta ulike typer input som endrer hvordan de oppfører seg:

1. Argumenter:
   - Filer eller mapper kommandoen skal jobbe med
   - Kommer etter kommandoen
   - Eksempel: `cat fil.txt` (fil.txt er argumentet)

2. Opsjoner/flagg:
   - Starter med `-` (kort form) eller `--` (lang form)
   - Endrer hvordan kommandoen oppfører seg
   - Eksempel: `ls -l` (-l er en opsjon)

3. Kombinasjoner:
   ```bash
   ls -l dokumenter     # -l er opsjon, dokumenter er argument
   cp -r mappe1 mappe2  # -r er opsjon, mappe1 og mappe2 er argumenter
   ```

#### Mer om ls

`ls`-kommandoen er en av de mest brukte, og har mange nyttige opsjoner:

```bash
ls -l      # Detaljert liste
ls -a      # Vis skjulte filer
ls -h      # Menneskelesbare størrelser
ls -R      # Rekursiv listing (undermapper)
ls -S      # Sorter etter størrelse
ls -t      # Sorter etter tid
```

Du kan kombinere opsjoner:
```bash
ls -lha    # Detaljert liste, med skjulte filer og lesbare størrelser
```

Kommandoen godtar også argument, slik at du kan få en liste over innhold i andre mapper enn den du står i:
```bash
ls ~/dokumenter -la   # Detaljert liste, med skjulte filer, over innholdet i mappen 'dokumenter' i din hjemmappe.
```

### Manualen (man)

Manualen er den innebygde dokumentasjonen i Unix-systemer. Den er ditt viktigste verktøy for å lære nye kommandoer.

#### Slå opp en side

```bash
man ls     # Vis manualen for ls
man cp     # Vis manualen for cp
man man    # Ja, manualen har til og med en manual!
```

#### Søk etter en side

Hvis du ikke vet nøyaktig hvilken kommando du trenger:

```bash
man -k [søkeord]  # Søk i alle manualsider

# Eksempel:
man -k file       # Finn alle kommandoer relatert til filer
```

#### Finne frem i en man-side

Man-sider er organisert i seksjoner og følger en standard struktur:
1. NAME: Kort beskrivelse
2. SYNOPSIS: Hvordan kommandoen brukes
3. DESCRIPTION: Detaljert beskrivelse
4. OPTIONS: Tilgjengelige opsjoner
5. EXAMPLES: Eksempler på bruk
6. SEE ALSO: Relaterte kommandoer

Navigering i man:
- Mellomrom: Neste side
- b: Forrige side
- /søkeord: Søk fremover
- n: Neste treff
- N: Forrige treff
- q: Avslutt

> ___Merk:___
> navigering i `man` bruker (stort sett) samme snarveier som ved bruk av `less` som vi ser på under.

### Navigere i tekst

I terminalen bruker vi ofte programmer for å lese lengre tekstfiler. De vanligste er:

1. less:
   - Moderne og fleksibel
   - Kan bla frem og tilbake
   - Kan søke i teksten
   ```bash
   less fil.txt
   ```

2. more:
   - Eldre og enklere
   - Kan bare bla fremover
   ```bash
   more fil.txt
   ```

Det anbefales å gjøre seg kjent med `less`, da snarveiene her brukes mye for navigering i tekst i terminalen. 

_Her er noen nyttige snarveier i `less`:_

```bash
less fil.txt         # Åpne fil i less


# Når less er åpen, kan disse snarveiene brukes:

# Bevegelse
Mellomrom eller f    # Én side frem
b                    # Én side tilbake
Pil ned eller Enter  # Én linje ned
Pil opp             # Én linje opp
g                    # Gå til starten av filen
G                    # Gå til slutten av filen
50g                  # Gå til linje 50

# Søking
/tekst              # Søk fremover etter "tekst"
?tekst              # Søk bakover etter "tekst"
n                   # Gå til neste søketreff
N                   # Gå til forrige søketreff

# Andre nyttige kommandoer
q                   # Avslutt less
h                   # Vis hjelpeside med alle kommandoer
v                   # Åpne filen i standardeditoren
&tekst              # Vis bare linjer som inneholder "tekst"
=                   # Vis filinformasjon (linjenummer etc.)
```

#### Vise eller åpne en tekstfil

For å se innholdet i en fil har du flere valg:

1. `cat`: Viser hele filen på én gang
   - Lite egnet for lange filer!
   ```bash
   cat fil.txt  
   ```

2. `less`: Viser filen side for side
   -  God til større filer, kan søke og navigere effektivt
   ```bash
   less fil.txt 
   ```

3. `head`: Viser starten av filen
   ```bash
   head fil.txt      # Første 10 linjer

   # Flere linjer med opsjonen -n
   head -n 20 fil.txt # Første 20 linjer
   ```

4. `tail`: Viser slutten av filen
   ```bash
   tail fil.txt      # Siste 10 linjer

   # Kontinuerlig oppdatering ved filendring med
   # opsjonen -f (nyttig for loggfiler)
   tail -f fil.txt   # Følg med på nye linjer 
   ```

### Redigere tekst

For tekstredigering i terminalen har du flere valg:

1. Nano:
   - Enklest å lære
   - Viser kommandoer nederst
   - God for nybegynnere
   - Forhåndsinstallert på mange Linux-distribusjoner, som ubuntu.

2. Vim:
   - Kraftig men kompleks
   - Krever tid å lære
   - Meget effektiv når du kan den
   - Forgjengeren `Vi` er ofte forhåndsinstallert
     - En enkel versjon med færre funksjoner

3. Emacs:
   - Også kraftig og kompleks
   - Mer enn bare en editor
   - Populær blant programmerere

#### Nano

Nano er den anbefalte editoren for nybegynnere:

Grunnleggende bruk:
```bash
nano fil.txt    # Åpne/lag fil
```

Viktige kommandoer (^ betyr Ctrl):
- ^O: Lagre som (WriteOut)
- ^S: Lagre
- ^X: Avslutt
- ^K: Kutt linje
- ^U: Lim inn
- ^W: Søk i tekst
- ^G: Vis hjelp

### Kort introduksjon til noen litt mer avanserte tema

#### Rettigheter og tillatelser

Unix-systemer har et detaljert rettighetssystem:
- Hver fil har rettigheter for eier, gruppe (som 'eier' filen) og andre
- Rettigheter kan være lese (r), skrive (w), kjøre (x)
- Se rettigheter med `ls -l`
- Endre rettigheter med `chmod`

> ___Eksempel:___
>
> `rwxr-xr-x`:
> | Bruker | 'kode' | Tillatelser | Forklaring |
> |---|---|---|--- |
> | Eier | rwx |r, w og x | lese, skrive og kjøre |
> | Gruppen | r-x | r og x | lese og kjøre|
> | Andre | r-x | r og x |lese og kjøre|

#### Variabler og miljø

Miljøvariabler lagrer informasjon som programmer kan bruke:
- `PATH`: Hvor systemet leter etter programmer
- `HOME`: Din hjemmemappe
- `USER`: Ditt brukernavn
- Se alle med `env`
- Lag ny med `export NAVN=verdi`

Du kan skrive ut verdien til en miljøvariabel ved hjelp av `echo`-kommandoen:

```bash
echo $HOME  # Skriver ut filbanen til din hjemmappe
```

##### Andre variabler

En miljøvariabel er egentlig bare en variabel. Vi kan lage andre variabler hvis vi for
eksempel skal bruke den samme filbanen flere ganger, og slik slippe å skrive den inn 
på ny hver gang:

```bash
dokDir=~/Documents  # Lagrer filbanen til 'Documents' i hjemmappen til variabelen dokDir

cd $dokDir  # Navigerer til ~/Documents ved bruk av variabelen dokDir
```

Slike variabler vi definerer i terminalen, vil slettes og forsvinne når terminalen lukkes. 
Det spesielle med miljøvariabler er at de lastes inn på ny hver gang man åpner et nytt terminalvindu, 
og er slik alltid tilgjengelig. For å visuelt skille miljøvariabler fra andre variabler er det vanlig
å kun bruke store bokstaver som navn på miljøvariabler, som `HOME` som vi så på tidligere. 

#### Inndata, utdata og kjeding

Ofte er det nyttig å gjøre noe annet med utdata fra en kommando enn å skrive det ut til terminalen. 
Det betegnes gjerne som å 'omdirigere' utdata. Vi kan lagre utdata fra `kommando` til `fil.txt`
ved å bruke symbolet `>`:

- `kommando > fil.txt`
  - Overskriver `fil.txt` hvis den finnes fra før.
  - (Lager en ny fil hvis den ikke finnes.)
- `kommando >> fil.txt`
  - Legger til utdata i slutten av `fil.txt` om den allerede finnes
  - (Lager en ny fil hvis den ikke finnes.)

Andre ganger ønsker vi å sende utdata videre til en annen funksjon, i stedet for å lagre utdata i en fil.
Da kan vi bruke symbolet `|` som kalles for en `pipe`. Det engelske ordet pipe betyr rør på norsk, som passer godt, for vi lager et slags rør fra utdata generert av én kommando til inndata for en annen kommando:

  ```bash
  ls -l | grep ".txt"    # ls lister mappeinnhold, og grep filtrerer listen slik bare linjer som inneholder .txt vises
  ```

#### Pakkehåndtering (Package Management)

En pakkehåndterer (Package Manager) er et program som holder styr på installert software. Den
kan brukes til å installere, avinstallere og oppdatere programmer på en enkel måte. Pakkedata
om tilgjengelig software hentes (som standard) fra verifiserte kilder på internett. En kan se
på det litt som Play / App Store på mobiltelefonen.

Ubuntu/Debian:
```bash
sudo apt update          # Oppdater pakkelisten
sudo apt install program # Installer program
sudo apt upgrade         # Oppdater alle programmer
```

macOS (med Homebrew):
```bash
brew update             # Oppdater pakkelisten
brew install program    # Installer program
brew upgrade            # Oppdater alle programmer
```

Windows
```bash
winget install program  # Installer program
winget upgrade --all    # Oppdater alle programmer
```
