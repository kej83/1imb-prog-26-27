# Kapittel 5: CSS — farger og tekst

*HTML og CSS — hefte 5 i serien «Nettsider fra bunnen av». Bygger på hefte 1–4.*

---

Fire hefter har du nå bygget nettsider som alle ser helt like ut: svart tekst på hvit bakgrunn, i samme skrifttype. Det er ikke fordi HTML mangler noe — det er fordi HTML aldri var ment å bestemme utseende. HTML beskriver hva innholdet **er**. Utseendet styres av et helt eget språk: **CSS**.

CSS står for *Cascading Style Sheets*. I dette heftet lærer du å gi sidene dine farger, skrifttyper og størrelser — og du får endelig betalt for alt arbeidet du la ned i riktig struktur i hefte 4.

> **💡 Tips:** Lag en ny mappe `nettside5` for dette heftet, og åpne den i VS Code med **File → Open Folder**.

---

## 5.1 Den første CSS-regelen

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8">
  <title>Min første CSS</title>
  <style>
    p {
      color: red;
    }
  </style>
</head>
<body>
  <h1>Fargeprøve</h1>
  <p>Dette avsnittet skal bli rødt.</p>
  <p>Dette også.</p>
</body>
</html>
```

CSS skrives i et `<style>`-element inne i `<head>`. Alt som står der, er regler for hvordan innholdet i `<body>` skal se ut.

1. Les koden. Hvilke deler av siden blir røde — og hvilke blir det ikke?
2. Lag fila `index.html`, skriv av koden, og se på resultatet.
3. Legg til et tredje avsnitt nederst. Blir det også rødt, uten at du rører CSS-en?

Det siste er hele poenget: regelen gjelder **alle** `<p>`-elementer på siden, også de du lager senere.

En CSS-regel består av fire deler:

```text
p        {  color: red;  }
^           ^      ^
selektor    egenskap   verdi
```

| Del | I eksempelet | Betyr |
|---|---|---|
| Selektor | `p` | Hvilke elementer regelen gjelder for |
| Egenskap | `color` | Hva som skal endres |
| Verdi | `red` | Hva det skal endres til |
| Deklarasjon | `color: red;` | Egenskap + verdi, avsluttet med semikolon |

Krøllparentesene `{ }` samler alle deklarasjonene som hører til selektoren.

4. Legg til en regel for `h1` som gjør overskriften blå. Regelen skal stå rett under `p`-regelen, inni `<style>`.
5. Gi `p`-regelen en deklarasjon til, slik at den blir slik:

```css
p {
  color: red;
  background-color: yellow;
}
```

6. Fjern semikolonet etter `color: red`. Lagre, og se på siden. Hva skjedde med den neste deklarasjonen? Sett semikolonet tilbake.

> **⚠️ Merk:** Semikolonet avslutter hver deklarasjon. Glemmer du ett, slutter resten av regelen å virke — og nettleseren sier ingenting. Dette er den vanligste CSS-feilen som finnes, og den er vond å oppdage fordi det ser ut som om du ikke har endret noe.

> **💡 Tips:** Kommentarer i CSS skrives `/* slik */`. De virker ikke med `<!-- -->` som i HTML — det er to forskjellige språk.

---

## 5.2 Egen stilfil

```html
<head>
  <meta charset="UTF-8">
  <title>Min første CSS</title>
  <link rel="stylesheet" href="stil.css">
</head>
```

```css
/* stil.css */
p {
  color: red;
}

h1 {
  color: blue;
}
```

Å ha CSS-en inni HTML-fila fungerer, men blir fort rotete — og verre: skal du ha lik stil på ti sider, må du lime inn den samme CSS-en ti ganger. I stedet legger vi CSS-en i sin **egen fil**, og kobler den til.

1. Lag en ny fil i mappa di med navnet `stil.css`. Legg merke til endelsen: `.css`, ikke `.html`.
2. Klipp ut alt som står inni `<style>`-elementet i `index.html`, og lim det inn i `stil.css`. Slett deretter hele `<style>`-elementet.
3. Sett inn `<link>`-linja i `<head>` slik koden over viser, og lagre begge filene.
4. Se på siden. Den skal se helt lik ut som før — men nå ligger stilen i sin egen fil.

`<link>` er en tom tagg med to attributter:

| Attributt | Betyr |
|---|---|
| `rel="stylesheet"` | Fila som kobles til, er et stilark |
| `href="stil.css"` | Hvor fila ligger — samme slags filsti som til bilder og sider |

5. Lag en ny side `om.html` med sideskjelettet fra hefte 4. Sett inn den **samme** `<link>`-linja i `<head>`.
6. Åpne `stil.css`, og endre `color: red` til `color: green`. Lagre, og se på **begge** sidene.

Der ser du gevinsten: én endring i én fil, og hele nettstedet endret seg. Slik jobber alle profesjonelle utviklere.

> **🐞 Når noe går galt:** Skjer det ingenting når du endrer CSS-en? Sjekk i denne rekkefølgen: 1) Er begge filene lagret? 2) Står `<link>`-linja inni `<head>`? 3) Er filnavnet i `href` stavet helt likt som fila? 4) Ligger `.css`-fila i samme mappe som HTML-fila?

---

## 5.3 Elementselektorer — også de semantiske

```css
body {
  background-color: white;
}

header {
  background-color: navy;
  color: white;
}

main {
  background-color: white;
}

footer {
  background-color: gainsboro;
}
```

Alt du lærte i hefte 4 betaler seg nå. Fordi sidene dine har `<header>`, `<main>` og `<footer>`, kan du style hver del med én selektor hver — uten å røre HTML-en i det hele tatt.

1. Bygg om `index.html` slik at den følger sideskjelettet fra hefte 4: `<header>` med `<h1>` og en `<nav>`, `<main>` med minst én `<section>`, og `<footer>` med en `<address>`.
2. Legg reglene over inn i `stil.css`, og se på resultatet.
3. Legg til en regel for `nav` som gir menyen en annen bakgrunnsfarge.
4. Legg til en regel for `section`. Hva skjer hvis du har flere seksjoner?

Alle selektorene du har brukt så langt, er **elementselektorer**: de treffer alle elementer av den typen. Det gjelder alle elementer du kan — `h1`, `p`, `ul`, `li`, `table`, `th`, `td`, `figure`, `figcaption`, `address`.

5. Gi tabellstilen et løft. Lag en side med en tabell fra hefte 4, og legg til:

```css
th {
  background-color: lightgray;
}
```

6. Husker du `<thead>` og `<tfoot>` fra hefte 4? Legg til en regel for `thead` og en for `tfoot`, og gi dem hver sin bakgrunnsfarge. Nå fikk du betalt for at du delte tabellen i tre.

> **💡 Tips:** Én selektor kan gjelde for flere elementer samtidig. Skriv dem med komma mellom: `h1, h2, h3 { color: navy; }`. Da slipper du å gjenta den samme regelen tre ganger.

---

## 5.4 Farger

```css
body {
  background-color: cornsilk;
}

h1 {
  color: #1a5276;
}

footer {
  background-color: rgb(230, 230, 230);
}
```

Til nå har du brukt fargenavn som `red` og `blue`. Det finnes rundt 140 slike navn — men de holder ikke lenge. Profesjonelle bruker nesten alltid en av de to andre måtene.

### Fargenavn

Enklest, men mest begrenset. Noen brukbare navn å kjenne til: `white`, `black`, `gainsboro`, `lightgray`, `dimgray`, `navy`, `teal`, `crimson`, `cornsilk`, `tomato`.

### Hex-koder

En hex-kode er et firkanttegn og seks tegn: `#1a5276`. De seks tegnene er tre par, ett for hver av grunnfargene:

```text
#  1a   52   76
   ^^   ^^   ^^
   rød  grønn blå
```

Hvert par går fra `00` (ingenting) til `ff` (maks). `#000000` er svart, `#ffffff` er hvit, `#ff0000` er knallrød.

### rgb()

Samme idé, men med vanlige tall fra 0 til 255: `rgb(26, 82, 118)` er nøyaktig samme farge som `#1a5276`.

1. Lag en side med en `<header>`, en `<main>` og en `<footer>`, og gi hver del sin egen bakgrunnsfarge — bruk et fargenavn på den ene, en hex-kode på den andre og `rgb()` på den tredje.
2. Bytt ut hex-koden med `#000000`. Hva skjer? Prøv deretter `#ffffff`, `#ff0000` og `#00ff00`.
3. Endre `rgb(230, 230, 230)` til `rgb(255, 0, 0)`, og deretter til `rgb(0, 0, 255)`. Klarer du å lage lilla?

### Slik finner du farger

Du skal ikke gjette hex-koder. To gode måter:

- **I VS Code:** skriv `color: #ffffff;`, og klikk på den lille fargeruten som dukker opp foran koden. Da får du en fargevelger.
- **På nettet:** søk etter «color picker» eller «fargepalett», og kopier hex-koden.

4. Bruk fargevelgeren i VS Code til å finne en farge du liker til `<header>`.

> **⚠️ Merk:** Tenk på **kontrast**. Lysegrå tekst på hvit bakgrunn er nesten umulig å lese for mange — og umulig for noen. Mørk tekst på lys bakgrunn, eller lys tekst på mørk bakgrunn. Hvis du må myse, er kontrasten for dårlig.

5. Gi `<header>` mørk bakgrunn og lys tekst. Gjør deretter det motsatte på `<main>`.

---

## 5.5 Skrift og tekst

```css
body {
  font-family: Verdana, Arial, sans-serif;
  font-size: 18px;
}

h1 {
  font-size: 42px;
  text-align: center;
}

footer {
  font-size: 14px;
  text-align: center;
}
```

Nå til det som virkelig endrer hvordan en side føles: skriften.

| Egenskap | Bestemmer | Eksempelverdier |
|---|---|---|
| `font-family` | Skrifttypen | `Verdana`, `Georgia`, `"Courier New"` |
| `font-size` | Skriftstørrelsen | `18px`, `42px` |
| `text-align` | Hvordan teksten stilles opp | `left`, `center`, `right` |
| `font-weight` | Tykkelsen | `normal`, `bold` |
| `line-height` | Avstanden mellom linjene | `1.5` |

1. Legg reglene over inn i `stil.css`, og se på resultatet.
2. Endre `font-size` på `body` til `12px`, og deretter til `24px`. Hva skjedde med *alle* de andre tekstene på siden?
3. Bytt `Verdana` mot `Georgia`, og deretter mot `"Courier New"` (med anførselstegn, fordi navnet inneholder mellomrom).
4. Legg til `line-height: 1.6;` i `body`-regelen. Se nøye på avstanden mellom linjene i et langt avsnitt.

### Hvorfor tre skrifttyper i `font-family`?

```css
font-family: Verdana, Arial, sans-serif;
```

Fordi skrifttypen må finnes på maskinen til den som besøker siden. Listen leses fra venstre: finnes ikke `Verdana`, prøves `Arial`. Finnes ikke den heller, brukes `sans-serif` — «en hvilken som helst skrift uten føtter», som alle maskiner har.

De tre gruppene du bør kjenne:

| Gruppe | Utseende | Vanlige valg |
|---|---|---|
| `sans-serif` | Uten føtter, moderne | Verdana, Arial, Helvetica |
| `serif` | Med føtter, klassisk | Georgia, Times New Roman |
| `monospace` | Alle tegn like brede, som kode | Courier New, Consolas |

5. Gi `<code>`-elementer skrifttypen `"Courier New", monospace`, og prøv den på en side med kode i teksten.
6. Sentrer `<h1>` og `<footer>`, men la avsnittene være venstrestilt.

> **⚠️ Merk:** Ikke sentrer lange avsnitt. Sentrert tekst har ujevn venstrekant, og øyet mister linjen når det skal finne starten på neste linje. Sentrer overskrifter og korte biter — ikke brødtekst.

---

## 5.6 Arv: regler som smitter nedover

```css
body {
  font-family: Verdana, Arial, sans-serif;
  color: #333333;
}
```

La du merke til noe rart i forrige delkapittel? Du satte `font-size` på `body` — og *alt* på siden endret seg, også overskrifter og listepunkter du aldri hadde skrevet en regel for.

Det kalles **arv**. Alle elementene på siden ligger inni `<body>`, og noen egenskaper arves nedover til alt som ligger inni. Skrift og tekstfarge arves. Bakgrunnsfarge gjør det også i praksis, fordi elementer uten egen bakgrunn er gjennomsiktige.

1. Sett `color: #333333;` på `body`. Sjekk at både overskrifter, avsnitt og listepunkter blir mørkegrå.
2. Legg til en regel `h1 { color: crimson; }`. Hvilken vinner for `<h1>` — den arvede fargen, eller den egne?

Den egne vinner alltid. En regel som gjelder elementet direkte, slår en regel elementet bare har arvet.

Derfor jobber utviklere slik: sett det som skal gjelde overalt på `body`, og lag deretter egne regler bare for det som skal være annerledes.

3. Rydd i `stil.css`: flytt `font-family` opp i `body`-regelen, og slett den fra alle andre regler der den nå er overflødig.

### Når to regler krasjer

```css
p {
  color: blue;
}

p {
  color: green;
}
```

4. Legg begge reglene inn i `stil.css`, i den rekkefølgen. Hvilken farge får avsnittene?

Den siste vinner. Når to like sterke regler sier forskjellige ting om samme element, gjelder den som står **nederst** i fila. Det er en av tingene «Cascading» i *Cascading Style Sheets* viser til.

5. Bytt om på rekkefølgen, og bekreft at fargen skifter.
6. Slett den ene regelen. To regler for samme selektor er nesten alltid en feil — de skal slås sammen til én.

---

## 5.7 Alt satt sammen

```css
/* stil.css - grunnstil for nettstedet */

body {
  font-family: Verdana, Arial, sans-serif;
  font-size: 18px;
  line-height: 1.6;
  color: #333333;
  background-color: #fdfdfd;
}

header {
  background-color: #1a5276;
  color: #ffffff;
  text-align: center;
}

nav {
  background-color: #d6eaf8;
}

h1 {
  font-size: 42px;
}

h2 {
  color: #1a5276;
}

th {
  background-color: #d6eaf8;
}

footer {
  background-color: #eaeaea;
  font-size: 14px;
  text-align: center;
}
```

Dette er en komplett grunnstil for et nettsted. Legg merke til hvordan den er bygget opp: først `body` med det som skal gjelde overalt, deretter reglene for hver del av sideskjelettet, ovenfra og ned.

1. Lag denne stilfila, og koble den til alle sidene i et av nettstedene dine fra hefte 3 eller 4.
2. Bytt ut fargene med dine egne, funnet med fargevelgeren i VS Code.
3. Se på siden i nettleseren. Sammenlign med hvordan den så ut for ti minutter siden.

> **💡 Tips:** Skriv en kommentar øverst i stilfila, og gjerne én foran hver del. Om tre uker husker du ikke hvorfor du valgte akkurat de fargene.

---

## Sammendrag

### Slik kobles CSS til

```html
<head>
  <link rel="stylesheet" href="stil.css">
</head>
```

CSS kan skrives i et `<style>`-element i `<head>`, men hører hjemme i sin egen `.css`-fil som kobles til med `<link>`. Da gjelder den samme stilen for alle sidene på nettstedet.

### En CSS-regel

```css
p {
  color: #333333;
  background-color: white;
}
```

Selektoren (`p`) velger elementene. Inni krøllparentesene står deklarasjonene: egenskap, kolon, verdi, semikolon. **Husk semikolonet** — uten det slutter resten av regelen å virke.

Kommentarer skrives `/* slik */`.

### Farger

```css
h1 { color: navy; }
h2 { color: #1a5276; }
h3 { color: rgb(26, 82, 118); }
```

Tre måter å skrive samme farge på: navn, hex-kode og `rgb()`. Hex-koden er tre par fra `00` til `ff`, i rekkefølgen rød, grønn, blå. Bruk fargevelgeren i VS Code. Pass alltid på kontrasten mellom tekst og bakgrunn.

### Skrift og tekst

```css
body {
  font-family: Verdana, Arial, sans-serif;
  font-size: 18px;
  line-height: 1.6;
}

h1 {
  text-align: center;
}
```

| Egenskap | Bestemmer |
|---|---|
| `font-family` | Skrifttype, med reserveløsninger etter komma |
| `font-size` | Størrelse, oppgitt i `px` |
| `text-align` | `left`, `center` eller `right` |
| `font-weight` | `normal` eller `bold` |
| `line-height` | Linjeavstand, for eksempel `1.6` |

### Arv og rekkefølge

Skrift og tekstfarge arves nedover fra `body` til alt som ligger inni. En regel som gjelder elementet direkte, slår en arvet regel. Sier to like sterke regler forskjellige ting, vinner den som står nederst i fila.

Arbeidsmåten er derfor: sett fellestrekkene på `body`, og lag egne regler bare for det som skal skille seg ut.

---

## Oppgaver

> **💡 Tips:** Lag en ny mappe eller en ny fil for hver oppgave, og husk `<link>`-linja i `<head>`. Noen oppgaver i del B og C starter med en boks merket **Nytt stoff**.

### Del A — Enkle oppgaver

**Oppgave A1**

```css
p {
  color: red
  font-size: 20px;
}

h1 (
  color: blue;
)
```

Koden inneholder tre feil. Finn og rett dem alle, og sjekk at både avsnitt og overskrift får riktig stil.

**Oppgave A2**

```text
┌──────────────────────────────────┐
│   color: white;                  │
├──────────────────────────────────┤
│ }                                │
├──────────────────────────────────┤
│ header {                         │
├──────────────────────────────────┤
│   background-color: darkgreen;   │
└──────────────────────────────────┘
```

Sett sammen kodebitene til en gyldig CSS-regel. Prøv den på en side med en `<header>`.

**Oppgave A3**

```css
body {
  color: navy;
  font-size: 20px;
}

h1 {
  color: crimson;
}
```

Les koden uten å bruke PC. Hvilken farge og størrelse får en `<h1>`? Hva med et `<p>`? Og et `<li>` inni en liste? Skriv svarene ned, og sjekk dem deretter på PC.

**Oppgave A4**

```css
body {
  font-family: ...;
  font-size: ...;
}

h1 {
  text-align: ...;
  color: ...;
}
```

Skriv ferdig stilfila, og koble den til en side du lager selv. Skriften skal være uten føtter, brødteksten lett å lese, og overskriften sentrert i en farge du velger med fargevelgeren i VS Code.

**Oppgave A5**

Lag fila `farger.html` med seks avsnitt. Gi hvert avsnitt sin egen bakgrunnsfarge ved hjelp av en tabell over fargenavn du finner på nettet — to med fargenavn, to med hex-koder og to med `rgb()`. Alle skal ha lesbar kontrast mot teksten.

**Oppgave A6**

Ta en av sidene dine fra hefte 4, lag en `stil.css` til den, og gi `header`, `main` og `footer` hver sin bakgrunnsfarge. Sett også skrifttype og skriftstørrelse på `body`.

### Del B — Middels

**Oppgave B1**

> **🆕 Nytt stoff:** Flere selektorer kan dele samme regel. Skriv dem med komma mellom:
>
> `h1, h2, h3 {`
> `  color: #1a5276;`
> `  font-family: Georgia, serif;`
> `}`
>
> Regelen gjelder da for alle tre.

Lag en stilfil der alle overskriftsnivåene deler samme farge og skrifttype, satt i **én** regel. Gi deretter `h1` en egen regel som bare endrer størrelsen. Test på en side med `h1`, `h2` og `h3`.

**Oppgave B2**

> **🆕 Nytt stoff:** Egenskapen `text-decoration` styrer strek i teksten. `text-decoration: none;` fjerner understreken lenker har som standard, og `text-decoration: underline;` setter den på.

Lag en side med en meny i `<nav>`. Fjern understreken på lenkene, og gi dem en tydelig farge i stedet. Skriv en kommentar i CSS-fila: Hvorfor kan det være et problem å fjerne understreken hvis lenkene ikke skiller seg ut på annen måte?

**Oppgave B3**

Bygg en komplett grunnstil til nettstedet ditt fra hefte 4. Krav:

- `body` med skrifttype, skriftstørrelse, linjeavstand, tekstfarge og bakgrunnsfarge
- Egne regler for `header`, `nav`, `main` og `footer`
- Egne regler for `h1` og `h2`
- Minst én hex-farge og minst én `rgb()`-farge
- Kommentarer som deler stilfila inn i deler

**Oppgave B4**

> **🆕 Nytt stoff:** `text-transform: uppercase;` gjør teksten til STORE BOKSTAVER uten at du endrer HTML-en, og `letter-spacing: 2px;` øker avstanden mellom bokstavene.

Lag en `<header>` der sidens navn står med store bokstaver og god bokstavavstand, på mørk bakgrunn. Endre **bare** CSS — teksten i HTML-en skal skrives helt normalt. Forklar i en kommentar hvorfor det er bedre enn å skrive store bokstaver rett i HTML-en. (Hint: tenk på en skjermleser.)

**Oppgave B5**

Lag fila `tabellstil.html` med en tabell som har `<caption>`, `<thead>`, `<tbody>` og `<tfoot>` fra hefte 4. Gi `thead` og `tfoot` hver sin bakgrunnsfarge, `caption` en større skrift, og `th` en annen farge enn `td`. Alt skal gjøres med elementselektorer — du skal ikke røre HTML-en.

### Del C — Mer krevende

**Oppgave C1**

> **🆕 Nytt stoff:** Med `:hover` kan du lage en regel som bare gjelder når musepekeren er over elementet:
>
> `a:hover {`
> `  color: crimson;`
> `}`
>
> Dette kalles en pseudoklasse. Regelen slår inn når brukeren peker på lenken, og slutter å gjelde når pekeren flyttes vekk.

Lag en meny i `<nav>` der lenkene skifter farge når musepekeren er over dem. Prøv også å endre bakgrunnsfargen på hover. Test i nettleseren med **Go Live** — dette virker ikke like godt i forhåndsvisningen.

Legg merke til at du nå har laget noe som *reagerer* på brukeren, helt uten JavaScript.

**Oppgave C2**

Design en «mørk versjon» av et av nettstedene dine: mørk bakgrunn, lys tekst. Krav:

- Alle delene av sideskjelettet skal ha farger som hører sammen
- Kontrasten skal være god nok til at alt er lett å lese
- Lenkene skal være synlige mot den mørke bakgrunnen
- Overskriftene skal skille seg ut fra brødteksten

Vis siden til en medelev og be dem lese den høyt. Fant de noe som var vanskelig å lese? Juster.

**Oppgave C3**

Lag et lite «stilbibliotek» — fila `stilguide.html` — som viser fram designvalgene dine, slik profesjonelle designere gjør. Siden skal inneholde:

- En seksjon med alle overskriftsnivåene `h1` til `h4`, slik at man ser forskjellen
- En seksjon med brødtekst, en punktliste og en nummerert liste
- En seksjon med en tabell
- En seksjon med fargene dine: ett avsnitt per farge, med bakgrunnsfargen satt og hex-koden skrevet ut som tekst i `<code>`
- Alt stylet fra én `stil.css` med kommentarer

Denne fila kan du gjenbruke som utgangspunkt for alle senere nettsteder.

**Oppgave C4**

Undersøk selv, og skriv svarene som kommentarer i CSS-fila:

1. Sett `color: red;` på `body` og `color: blue;` på `main`. Hvilken farge får et avsnitt inni `<main>`? Hvorfor?
2. Skriv `font-family: Trøndersk Skrift, Verdana, sans-serif;` — altså med en skrifttype som ikke finnes. Hva skjer? Hva forteller det deg om hvorfor listen har flere navn?
3. Sett `font-size: 100px` på `body`. Hva skjer med siden, og hvilke elementer endret seg mest?
4. Lag to regler for `h1` som begge setter `color`, med ti linjer imellom. Hvilken vinner? Flytt om på dem og sjekk igjen.
5. Fjern `<link>`-linja fra HTML-fila, men behold CSS-fila. Ser du noe som forsvant? Skriv én setning om hva `<link>` egentlig gjør.

---

*Hefte 5 av serien «Nettsider fra bunnen av». Neste hefte: Klasser, id-er og boksmodellen.*
