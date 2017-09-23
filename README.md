# Git-kurs

## Installasjon
Nedlastningsfiler og instruksjoner for forskjellige OS finner du her:  https://git-scm.com/downloads Vi anbefaler og oppfordrer at alle som er på Windows bruker git bash som følger med i Windows-installasjonen. På Linux og Mac holder det med den innebygde terminalen.

## Legge til en SSH-nøkkel
Følg stegene her dersom du ikke allerede har gjort det før kurset:
https://help.github.com/articles/checking-for-existing-ssh-keys/


## Oppgaver
### Oppgave 1: Terminal 101
Åpne terminalen eller *git bash*. Gå til mappen du ønsker å ha prosjektet ditt i ved å bruke:

```
cd Path/Til/Din/Mappe
```

Her kan du lage en ny mappe:
```
mkdir git-kurs
```

Gå så inn i denne mappen:

```
cd git-kurs
```

Du kan liste innholdet i mappen ved å skrive inn `ls` i terminalen. Nå er mappen tom, så ingenting vil dukke opp.

### Oppgave 2: Initialisere et git-repo
Mens du er i mappen du nettopp lagde, skriv inn kommandoen under for å initialisere et tomt git-repo.
```
git init
```

Det som skjer, er at en `.git` mappe blir lagt til i mappen din. Denne kan du se dersom du kjører kommandoen `ls -A`. `-A`-flagget gjør at også skjulte filer (som starter med et punktum) blir vist.

### Oppgave 3: Legge til en ny fil
Åpne mappen du er i din favoritteditor. Dersom du ikke har en, kan du skrive `vim ditt-filnavn`.

#### Bruke Vim
Dette vil åpne en editor i terminalen din som heter Vim, hvor du kan redigere en fil `ditt-filnavn`. Skriv inn `i` (for insert mode), skriv inn noen greier og avslutt vim ved å trykke på `Esc`, og deretter skrive inn `:wq` etterfulgt av enter.


Dersom du nå kjører
```
git status
```
vil du forhåpentligvis få opp filen du nettopp lagde under "Untracked files".

For å legge til denne i "Staged" kjør:
```
git add ditt-filnavn
```

`git status` igjen bør vise at dette akkurat har skjedd.

Nå er denne filen i "Staged", det betyr at den vil bli med i din neste commit. Kjør:

`git commit`

Du vil nå mest sannsynlig komme inn i Vim, trykk på `i` (for insert mode) før du begynner å skrive øverst i filen. Dette vil bli commit-meldingen din. Dette er den aller første commiten i dette repoet, ofte skriver man da bare `Initial commit`, men du kan skrive hva du vil. Når du er ferdig, kom deg ut av Vim ved å trykke på `Esc`, og deretter skrive inn `:wq` og så Enter.

> **Tips!**
Dersom du bare har tenkt å skrive en kort commit-melding, og ingen kommentar under, kan du også skrive:
`
git commit -m "Din melding"
`
Da vil du ikke gå inn i Vim, men bare lage commiten direkte.

Grattis, da bør din første commit være på plass! Du kan dobbeltsjekke med `git status` at det ikke er noen endringer i repoet ditt nå.

### Oppgave 4: Vise loggen
For å vise hvilke commits du har på denne branchen (vi kommer til branching snart), kjør
```
git log
```
Her bør commiten du lagde i forrige oppgave listes opp. Nå har du bare èn, men når du får flere vil de vises i en liste. Den øverste vil være den nyeste. Da kan du scrolle eller bruke piltastene eller space for å bevege deg opp og ned i loggen.

Har du problemer med å komme deg ut av loggen, skriv `q`.

### Oppgave 5: Gjøre en forandring
Åpne filen du lagde tidligere, anten i din editor eller gjennom `vim ditt-filnavn`. Legg til og kanskje fjern noen linjer med innhold og lagre.

Dersom du nå kjører:
```
git diff
```
Bør forandringene du gjorde komme opp i terminalen.

Kjør
```
git status
```

Filen din burde nå ligge under "Modified".

`git add` og `git commit` filen slik som i Oppgave 3.

### Oppgave 6: Lag et repository på GitHub
Når du er logget inn på GitHub.com, gå til hovedsiden og trykk på "New" på høyre side. Du kan også gå til profilen din > Repositories > New Repository.

Du trenger ikke gjøre noen store forandringer. Gi repoet navnet "git-kurs" og gjør det **Private** hvis du ikke vil at alle skal kunne se det.

### Oppgave 7: Koble det lokale repoet ditt til repoet på GitHub
Du vil nå legge til repositoryet du lagde på GitHub som en *remote* lokalt på maskinen din. Når et GitHub-repository er lagt til som remote, betyr det at du kan pushe til det, og pulle fra det.

```
git remote add origin  https://github.com/ditt-brukernavn/git-kurs
```

Test om det fungerer ved å pushe det du har comittet så langt til GitHub:

```
git push origin master
```
Sjekk GitHub-repoet ditt, har commitene dine dukket opp?

### Oppgave 8: Lage en ny branch
La oss si at du vil lage en README-fil, men ikke er sikker på om du vil ha den inn i `master` med en gang. Lag en ny branch ut fra master, som du kaller `readme-fil`:

```
git branch readme-fil
```
Dersom du bare skriver `git branch` nå, bør det komme opp to brancher, `master` og `readme-fil`. Bytt til den nye branchen din:

```
git checkout readme-fil
```

> **Tips!**
Dersom du vil gjøre dette i én kommando, kan du kjøre:
`
git checkout -b readme-fil
`
Dette vil både lage og bytte til den nye branchen.
