# Kapittel 1: Din første nettside

*HTML og CSS — hefte 1 i serien «Nettsider fra bunnen av».*

---

## Slik jobber du med dette heftet

Heftet følger arbeidsmåten **PRIMM**. Hvert delkapittel starter med litt kode, og du jobber deg gjennom disse stegene:

- **Predict (forutsi):** Les koden, og forsøk å forutsi hvordan nettsiden vil se ut. Dette steget egner seg godt for diskusjon i par eller små grupper.
- **Run (kjør):** Skriv av koden, og se resultatet. Forklar eventuelle avvik mellom det du forventet og det du faktisk ser.
- **Investigate (undersøk):** Gjør små endringer i koden, forutsi hva som vil skje, og se på nytt.
- **Modify (endre):** Gjør større endringer. Utvid siden, eller lag en liknende side som bygger på denne.
- **Make (lag):** Lag din helt egen side. Dette nivået møter du i oppgavesettet bakerst i heftet.

Stegene er merket slik i teksten: **[Predict]**, **[Run]**, **[Investigate]**, **[Modify]** og **[Make]**.

### Hva er HTML?

Alle nettsider du besøker — VG, NRK, YouTube, TikTok — er bygget med **HTML**. HTML står for *HyperText Markup Language* og er språket som beskriver **innholdet** på en nettside: overskrifter, avsnitt, lister, bilder og lenker. Senere i serien lærer du **CSS**, som bestemmer hvordan innholdet skal **se ut**: farger, skrifttyper og plassering.

I dette heftet lager du dine første nettsider i **Visual Studio Code** (VS Code), det samme verktøyet som profesjonelle utviklere bruker.

> **💡 Tips:** Du trenger utvidelsene **Live Preview** og **Live Server** i VS Code. De er trolig allerede installert på din maskin — spør læreren din hvis du ikke finner dem.

---

## 1.1 Bli kjent med VS Code

Før vi skriver kode, må vi gjøre klart et arbeidsområde. VS Code jobber alltid med en **mappe** — mappa blir «hjemmet» til nettstedet ditt, hvor alle filene dine samles.

1. Lag en ny mappe med navnet `nettside1` i dokumentmappa di (eller der læreren sier at du skal lagre skolearbeid).
2. Åpne VS Code.
3. Velg **File → Open Folder** (Fil → Åpne mappe), og velg mappa `nettside1`. Trykk på **Yes, I trust the authors** dersom du får spørsmål om du stoler på mappa.
4. Til venstre ser du nå **utforskeren** (Explorer) med navnet på mappa di. Den er tom — foreløpig.
5. Hold musepekeren over mappenavnet i utforskeren, og trykk på ikonet **New File** (et ark med et plusstegn). Skriv filnavnet `index.html`, og trykk `ENTER`.

Du har nå en tom HTML-fil. Legg merke til at fila fikk et eget HTML-ikon — VS Code skjønner hva slags fil det er ut fra endelsen `.html`.

> **💡 Tips:** Fila som er forsiden på et nettsted, heter så godt som alltid `index.html`. Det er navnet nettlesere og servere leter etter først. Venn deg til navnet med en gang.

> **⚠️ Merk:** Bruk små bokstaver og ingen mellomrom i filnavn på nett. Skriv `index.html`, ikke `Index (ny).HTML`. Norske bokstaver som æ, ø og å bør du også unngå i filnavn — de kan skape trøbbel når nettstedet en dag skal ut på nett.

---

## 1.2 Malen: `!` + `ENTER`

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Document</title>
</head>
<body>

</body>
</html>
```

Alle HTML-filer starter med det samme grunnoppsettet. Det slipper du å skrive selv:

1. Klikk inn i den tomme fila `index.html`, skriv bare et utropstegn `!`, og trykk `ENTER`. **[Run]**

Hele malen ovenfor dukker opp av seg selv. Dette er en snarvei som ligger innebygd i VS Code. La oss se hva delene betyr:

| Kodelinje | Forklaring |
|---|---|
| `<!DOCTYPE html>` | Forteller nettleseren at dette er en HTML-side |
| `<html lang="en">` | Rota som all koden ligger inni. `lang` angir språket |
| `<head>` | Informasjon **om** siden — vises ikke på selve siden |
| `<meta charset="UTF-8">` | Gjør at æ, ø og å vises riktig |
| `<meta name="viewport" ...>` | Viktig for mobiltilpasning — mer om denne i hefte 8 |
| `<title>Document</title>` | Teksten som vises i fanen i nettleseren |
| `<body>` | Selve innholdet på siden — alt du skal vise, ligger her |

Du trenger ikke å pugge alt dette nå. Det viktigste er å vite at **innholdet ditt skal ligge mellom `<body>` og `</body>`**.

2. Siden vår er norsk, ikke engelsk. Endre `lang="en"` til `lang="no"`. **[Modify]**
3. Endre `<title>Document</title>` til `<title>Min første nettside</title>`. **[Modify]**
4. Skriv inn en overskrift mellom `<body>` og `</body>`, slik at det står: **[Modify]**

```html
<body>
  <h1>Hei, verden!</h1>
</body>
```

5. Lagre fila med `CTRL` + `S`.

> **⚠️ Merk:** Nettleseren ser bare det som er **lagret**. En hvit prikk i fanen øverst i VS Code betyr at fila har ulagrede endringer. Gjør det til en vane å trykke `CTRL` + `S` hver gang du har endret noe.

---

## 1.3 Se resultatet: Show Preview og Go Live

Nå skal vi endelig se nettsiden. Det kan du gjøre på to måter:

**Måte 1 — Live Preview:** Høyreklikk i selve koden, og velg **Show Preview**. Da åpnes en ny fane *inne i VS Code* med en forhåndsvisning av nettsiden. Du ser koden og siden ved siden av hverandre — perfekt når du jobber.

**Måte 2 — Live Server:** Trykk på knappen **Go Live** nederst til høyre i VS Code. Da åpnes siden i *nettleseren*, akkurat slik besøkende ville sett den.

1. Åpne forhåndsvisningen med **Show Preview**. Ser du overskriften `Hei, verden!`? **[Run]**
2. Trykk deretter på **Go Live**, og se den samme siden i nettleseren. Se på fanen øverst i nettleseren: der står teksten fra `<title>`. **[Run]**
3. Gå tilbake til koden i VS Code, endre teksten i `<h1>` til noe annet, og lagre. Følg med på hva som skjer i forhåndsvisningen. **[Investigate]**

Både Show Preview og Live Server oppdaterer siden automatisk hver gang du lagrer. Du skriver kode, lagrer, ser resultatet — og gjentar. Slik jobber du resten av året.

> **💡 Tips:** Bruk **Show Preview** mens du jobber, og **Go Live** når du vil se siden i full størrelse i nettleseren. Resultatet er det samme.

> **🐞 Når noe går galt:** Ser du ingen endring? Sjekk først om fila er lagret (den hvite prikken!). Sjekk deretter at du skrev koden på riktig sted — innholdet skal ligge mellom `<body>` og `</body>`.

---

## 1.4 Overskrifter og avsnitt

```html
<body>
  <h1>Fotball</h1>
  <p>Fotball er en av verdens mest populære idretter.</p>
  <h2>Regler</h2>
  <p>To lag med elleve spillere prøver å score flest mål.</p>
</body>
```

Vi skal bygge en liten side om fotball, og møter nettsidens to viktigste byggeklosser: overskrifter og avsnitt.

1. Les koden. Hvordan vil siden se ut? Hvilken tekst blir størst? **[Predict]**
2. Bytt ut innholdet i `<body>` i `index.html` med koden ovenfor, lagre, og se resultatet med Show Preview. **[Run]**

En **tagg** består av et navn mellom `<` og `>`. Taggene opptrer nesten alltid i par: `<h1>` er en **åpnetagg**, og `</h1>` er en **lukketagg** — legg merke til skråstreken. Taggparet med innholdet imellom kaller vi et **element**.

HTML har seks nivåer av overskrifter: `<h1>` er hovedoverskriften, `<h2>` er overskrift for et delkapittel, og så videre helt ned til `<h6>`. Avsnitt med vanlig tekst ligger i `<p>`-elementer (p for *paragraph*).

3. Endre `<h2>` til `<h3>`, lagre, og se på resultatet. Prøv også `<h6>`. Hva skjer med størrelsen? Endre tilbake til `<h2>` etterpå. **[Investigate]**
4. Hva skjer hvis du glemmer lukketaggen `</h1>` på første overskrift? Prøv! Se godt på resultatet, og forklar det du ser. Sett lukketaggen på plass igjen etterpå. **[Investigate]**
5. Utvid siden med et nytt delkapittel: en `<h2>`-overskrift med teksten `Utstyr`, og under den et avsnitt om hva man trenger for å spille fotball. **[Modify]**
6. Legg til enda et avsnitt under `Regler`. **[Modify]**

> **⚠️ Merk:** En side skal bare ha **én** `<h1>` — den er sidens hovedoverskrift. Velg heller ikke overskriftsnivå ut fra størrelsen: nivåene beskriver strukturen i innholdet, som kapitler og delkapitler i en bok. Størrelsen ordner vi senere med CSS.

La oss undersøke en ting til. Hva skjer med linjeskift *i koden*?

7. Skriv et avsnitt på denne måten, med linjeskift midt i teksten: **[Investigate]**

```html
<p>Dette avsnittet
er skrevet over
tre linjer i koden.</p>
```

8. Se på resultatet. Ble det tre linjer på nettsiden?

Nettleseren bryr seg ikke om linjeskift og ekstra mellomrom i koden — den flyter all tekst i et avsnitt sammen, og bryter linjene der det passer med vindusbredden. Vil du ha nytt avsnitt, bruker du en ny `<p>`.

---

## 1.5 Tagger uten innhold, og kommentarer

```html
<body>
  <h1>Dikt om høsten</h1>
  <p>Bladene faller ned,<br>
  en etter en,<br>
  gult og rødt og brunt.</p>
  <hr>
  <p>Skrevet av meg selv.</p>
</body>
```

Noen tagger har ikke noe innhold, og trenger derfor ingen lukketagg. De kalles **tomme tagger**. Her møter du to av dem:

| Tagg | Navn | Gjør |
|---|---|---|
| `<br>` | *break* | Tvinger et linjeskift inne i et avsnitt |
| `<hr>` | *horizontal rule* | Lager en vannrett strek over siden |

1. Les koden. Hvor mange linjer får diktet? Hvor havner streken? **[Predict]**
2. Bytt ut innholdet i `<body>` med koden, lagre, og sjekk. **[Run]**
3. Fjern alle `<br>`-taggene, og se hva som skjer med diktet. Legg dem tilbake etterpå. **[Investigate]**

I diktet trengte vi `<br>`, fordi linjeskiftene er en del av selve diktet. Men til vanlig tekst skal du bruke `<p>` for hvert avsnitt — ikke `<br>` for å lage luft.

Til slutt: **kommentarer**. En kommentar er en beskjed til den som leser koden — nettleseren hopper over den, og den vises aldri på siden:

```html
<!-- Her begynner diktet -->
```

4. Legg inn en kommentar i koden din, lagre, og bekreft at den ikke vises på siden. **[Run]**
5. Hva skjer med det som ligger *inni* en kommentar? Pakk inn `<hr>`-linja slik: `<!-- <hr> -->`, og se på resultatet. Fjern kommentartegnene etterpå. **[Investigate]**

> **💡 Tips:** Kommentarer er nyttige for å forklare koden din — både til deg selv og til andre. I store filer brukes de ofte som «skilt» som viser hvor de ulike delene av siden begynner.

---

## Sammendrag

I dette heftet har du laget dine første nettsider med HTML og lært arbeidsflyten du kommer til å bruke hver eneste time fremover.

### Arbeidsflyten

1. Åpne mappa di i VS Code (**File → Open Folder**).
2. Lag en ny fil med endelsen `.html`, for eksempel `index.html`.
3. Skriv `!` og trykk `ENTER` for å få malen.
4. Skriv innholdet ditt mellom `<body>` og `</body>`.
5. Lagre med `CTRL` + `S`, og se resultatet med **Show Preview** (i VS Code) eller **Go Live** (i nettleseren). Begge oppdaterer seg automatisk når du lagrer.

### Begreper

| Begrep | Eksempel | Forklaring |
|---|---|---|
| Åpnetagg | `<h1>` | Starter et element |
| Lukketagg | `</h1>` | Avslutter elementet — merk skråstreken |
| Element | `<h1>Hei</h1>` | Taggpar med innhold |
| Tom tagg | `<br>`, `<hr>` | Tagg uten innhold og uten lukketagg |
| Attributt | `lang="no"` | Ekstra informasjon inne i en åpnetagg |
| Kommentar | `<!-- tekst -->` | Vises aldri på siden |

### Taggene du har lært

```html
<h1>Sidens hovedoverskrift - bare én per side</h1>
<h2>Overskrift for et delkapittel</h2>
<p>Et avsnitt med tekst.</p>
<p>Tekst med et<br>linjeskift inni.</p>
<hr>
<!-- En kommentar -->
```

Overskriftene går fra `<h1>` (størst) til `<h6>` (minst) og beskriver strukturen i innholdet. Nettleseren ignorerer linjeskift og ekstra mellomrom i koden — bruk `<p>` for nye avsnitt og `<br>` bare når linjeskiftet er en del av innholdet, som i dikt.

### Malen

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Teksten i nettleserfanen</title>
</head>
<body>
  <!-- Alt innhold ligger her -->
</body>
</html>
```

---

## Oppgaver

> **💡 Tips:** Lag en ny fil i mappa `nettside1` for hver oppgave, for eksempel `oppgaveA1.html`. Start alltid med `!` + `ENTER`, og husk `lang="no"` og en fornuftig `<title>`.

### Del A — Enkle oppgaver

**Oppgave A1**

```html
<body>
  <h1>Været i dag<h1>
  <p>Det er sol og 18 grader.</p>
  <p>I morgen blir det regn.
</body>
```

Koden inneholder to feil. Finn feilene ved å lese koden, rett dem, og sjekk at siden ser riktig ut.

**Oppgave A2**

```text
┌──────────────────────────────────────────────┐
│ <p>Jeg går på vg1 og lærer HTML.</p>         │
├──────────────────────────────────────────────┤
│ <h1>Om meg</h1>                              │
├──────────────────────────────────────────────┤
│ <p>På fritiden spiller jeg håndball.</p>     │
├──────────────────────────────────────────────┤
│ <h2>Fritid</h2>                              │
└──────────────────────────────────────────────┘
```

Sett sammen kodebitene i den rekkefølgen som gir en fornuftig side: hovedoverskrift øverst, deretter et avsnitt, så et delkapittel med sitt avsnitt. Skriv koden inn mellom `<body>` og `</body>`, og se på resultatet.

**Oppgave A3**

```html
<body>
  <h1>Kino</h1>
  <p>Fredag skal
  vi på kino.</p>
  <hr>
  <p>Vi gleder oss!</p>
</body>
```

Les koden, og tegn på papir hvordan siden vil se ut. Hvor mange tekstlinjer blir det før streken? Skriv deretter av koden, og sjekk svaret ditt.

**Oppgave A4**

```html
<body>
  <h1>...</h1>
  <p>...</p>
  <h2>Utseende</h2>
  <p>...</p>
  <h2>...</h2>
  <p>...</p>
</body>
```

Lag en side om favorittdyret ditt. Bruk skjelettet ovenfor, og fyll inn der det mangler noe (`...`): hovedoverskrift med dyrets navn, et innledende avsnitt, og to delkapitler — ett om utseende og ett med en overskrift du velger selv.

**Oppgave A5**

Lag fila `sang.html` med teksten til et vers fra en sang du liker. Siden skal ha en `<h1>` med sangtittelen, verset i ett `<p>`-element med `<br>` mellom linjene, en `<hr>`, og til slutt et avsnitt som forteller hvem som har laget sangen.

**Oppgave A6**

Lag en side om deg selv med: én `<h1>`, minst to `<h2>`-delkapitler (for eksempel `Fritid` og `Favorittmat`), og minst ett avsnitt under hver overskrift. Husk riktig `<title>`.

### Del B — Middels

**Oppgave B1**

```html
<body>
  <h1>Skoledagen min</h1>
  <h3>Morgenen</h3>
  <p>Jeg står opp klokka sju.</p>
  <h6>Frokost</h6>
  <p>Jeg spiser havregrøt.</p>
  <h2>Skolen</h2>
  <p>Første time starter 08.15.</p>
</body>
```

Overskriftsnivåene i koden er valgt helt tilfeldig. Rett dem opp slik at strukturen blir logisk: `Morgenen` og `Skolen` er hoveddeler av siden, mens `Frokost` hører til under `Morgenen`. Forklar med én setning hvorfor `<h6>` var et dårlig valg for `Frokost`.

**Oppgave B2**

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <title>Kake</titel>
  <body>
  <h1>Sjokoladekake</h1>
  <p>Verdens beste kake!</p>
</head>
</body>
</html>
```

Denne koden har tre feil: en skrivefeil i en tagg, og to tagger som står på feil sted. Rett koden slik at malen får riktig struktur. Sammenlign gjerne med malen i sammendraget.

**Oppgave B3**

Lag fila `oppskrift.html` med en oppskrift du kan (eller finner på). Siden skal ha: sidetittel i `<title>`, én `<h1>` med rettens navn, et delkapittel `Ingredienser` der ingrediensene står i ett avsnitt med `<br>` mellom hver ingrediens, en `<hr>`, og et delkapittel `Slik gjør du` med fremgangsmåten i to eller flere avsnitt. Legg inn en kommentar i koden som markerer hvor fremgangsmåten begynner.

**Oppgave B4**

Åpne `oppskrift.html` fra B3 i nettleseren med **Go Live**. Gjør vinduet smalere og bredere, og se hva som skjer med teksten i avsnittene. Hvorfor bryter ikke linjene i ingredienslista på samme måte? Skriv svaret som en kommentar øverst i fila.

### Del C — Mer krevende

**Oppgave C1**

Lag fila `artikkel.html` med en nyhetsartikkel om noe som (kanskje) har skjedd på skolen din. Krav:

- Riktig mal med `lang="no"` og beskrivende `<title>`
- Én `<h1>` (overskriften på artikkelen), og et innledende avsnitt rett under
- Minst tre delkapitler med `<h2>` og tilhørende avsnitt
- Minst ett delkapittel som selv har et under-delkapittel med `<h3>`
- En `<hr>` nederst, fulgt av et avsnitt med dato og journalistens navn
- Kommentarer som markerer hver hoveddel av artikkelen

Tegn strukturen på papir før du koder: skriv opp overskriftene med innrykk som viser nivåene.

**Oppgave C2**

Undersøk selv, og skriv svarene som kommentarer i en egen fil `eksperiment.html`:

1. Hva skjer med tekst som du skriver i `<head>`, utenfor `<title>`? Vises den? Hvor?
2. Hva skjer hvis du lager to `<h1>`-elementer? Får du feilmelding?
3. Hva skjer hvis du skriver tekst rett i `<body>` uten noen tagg rundt? Sammenlign med tekst i et `<p>`-element, og forklar hvorfor `<p>` likevel er riktig å bruke.
4. Nettleseren klager nesten aldri, uansett hva du skriver. Skriv én setning om hvorfor det både er praktisk og litt farlig.

---

*Hefte 1 av serien «Nettsider fra bunnen av». Neste hefte: Tekst, lister og tabeller.*
