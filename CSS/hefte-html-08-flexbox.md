# Kapittel 8: Flexbox

*HTML og CSS — hefte 8 i serien «Nettsider fra bunnen av». Bygger på hefte 1–7.*

---

Alt du har laget til nå, ligger under hverandre. Overskrift, avsnitt, seksjon, kort — nedover, nedover, nedover. Ekte nettsider gjør ikke det: menyer ligger bortover, kort ligger side om side, og en sidespalte ligger ved siden av hovedinnholdet.

I dette heftet lærer du **flexbox** — verktøyet som plasserer elementer bortover i stedet for nedover. Det er samme verktøy som brukes på så godt som alle nettsteder i dag, og det er overraskende enkelt: du setter én regel på boksen utenpå, og barna inni legger seg på rad.

> **💡 Tips:** Lag en ny mappe `nettside8` med `index.html` og `stil.css`. Husk `* { box-sizing: border-box; }` øverst i stilfila — den skal ligge der i alt du lager fra nå av.

---

## 8.1 Block og inline

```html
<body>
  <div class="boks">Første boks</div>
  <div class="boks">Andre boks</div>
  <p>Et avsnitt med et <span class="merket">merket ord</span> inni.</p>
</body>
```

```css
.boks {
  background-color: #d6eaf8;
}

.merket {
  background-color: gold;
}
```

Før vi kan flytte på elementer, må vi vite hvordan de oppfører seg av seg selv.

1. Skriv av koden, og se på resultatet.
2. Se på de to `<div>`-ene. Hvor brede er de — akkurat så brede som teksten, eller hele siden?
3. Se på det merkede ordet. Hvor bredt er det?

Elementer deles i to typer:

| Type | Oppfører seg slik | Eksempler |
|---|---|---|
| **block** | Tar hele bredden, og legger seg på ny linje | `<div>`, `<p>`, `<h1>`, `<section>`, `<ul>`, `<li>`, `<header>`, `<main>`, `<footer>` |
| **inline** | Tar bare plassen innholdet trenger, og blir stående på linja | `<span>`, `<a>`, `<strong>`, `<em>`, `<img>` |

Dette er grunnen til at en `<div>` skyver alt nedover mens en `<span>` ikke gjør det — og det er svaret på spørsmålet fra hefte 6.

4. Legg til `display: inline;` i `.boks`-regelen. Hva skjer med de to boksene?
5. Endre til `display: block;` i `.merket`-regelen. Hva skjer med ordet inni avsnittet?
6. Angre begge endringene.

Du kan altså **bytte om** hvordan et element oppfører seg. Det er nettopp det du gjorde i hefte 7, da knappen trengte `display: inline-block` for å ta imot padding oppover og nedover:

| Verdi | Bredde | Ny linje? | Tar imot padding oppover/nedover? |
|---|---|---|---|
| `block` | Hele bredden | Ja | Ja |
| `inline` | Bare innholdet | Nei | Nei |
| `inline-block` | Bare innholdet | Nei | Ja |

7. Lag en lenke med klassen `knapp`, gi den padding og bakgrunnsfarge, og prøv den både med og uten `display: inline-block`.

---

## 8.2 Skjule elementer

```css
.under-arbeid {
  display: none;
}
```

Verdien `none` er den fjerde — og den gjør noe helt annet: elementet forsvinner **helt**.

1. Lag en `<section class="under-arbeid">` med en overskrift og et avsnitt, og legg på regelen.
2. Se på siden. Er det et tomt hull der seksjonen var?

Nei. Elementet tar ikke plass i det hele tatt — det er som om det ikke finnes. Innholdet ligger fortsatt i HTML-en, men vises ikke.

3. Kommenter ut regelen med `/* */`, og se seksjonen dukke opp igjen.

`display: none` brukes hele tiden på ekte nettsteder: til å skjule innhold som ikke er ferdig, til menyer som bare skal vises på mobil, og til alt som skal kunne skrus av og på. I hefte 9 bruker du den til nettopp det.

> **⚠️ Merk:** Innhold som er skjult med `display: none`, er *fortsatt i koden*. Skjuler du noe fordi det er hemmelig, er det ikke hemmelig — hvem som helst kan lese HTML-en. Bruk `display: none` til å styre hva som vises, aldri til å gjemme noe.

---

## 8.3 `display: flex`

```html
<div class="rad">
  <div class="boks">Én</div>
  <div class="boks">To</div>
  <div class="boks">Tre</div>
</div>
```

```css
.rad {
  display: flex;
  gap: 20px;
}

.boks {
  background-color: #d6eaf8;
  padding: 20px;
  border: 1px solid #1a5276;
}
```

Nå kommer det.

1. Skriv av koden, men **uten** `display: flex`-linja først. De tre boksene ligger under hverandre, som forventet.
2. Legg til `display: flex;`, og lagre.

De tre boksene la seg på rad. Med én kodelinje.

Her er det viktigste å forstå: **`display: flex` settes på boksen utenpå**, ikke på boksene som skal flyttes. Den ytre boksen kalles en *flex-container*, og barna inni blir *flex-elementer* som legger seg på rad.

```text
.rad  ← her settes display: flex
 ├── .boks   ┐
 ├── .boks   ├── disse legger seg på rad
 └── .boks   ┘
```

3. Prøv å flytte `display: flex` til `.boks`-regelen i stedet. Hva skjer? Flytt den tilbake.
4. Fjern `gap: 20px`, og se på boksene. Legg den tilbake.

`gap` er avstanden mellom flex-elementene. Før `gap` fantes måtte man fikle med margin på hver enkelt boks — nå er det én linje på containeren.

5. Legg til en fjerde boks i HTML-en. Trengte du å endre CSS-en?
6. Prøv `gap: 0`, `gap: 5px` og `gap: 60px`.

> **🐞 Når noe går galt:** Skjer det ingenting når du setter `display: flex`? Ni av ti ganger står regelen på feil element. Flex settes alltid på **forelderen** — boksen som inneholder det du vil ha på rad.

---

## 8.4 `justify-content`

```css
.rad {
  display: flex;
  gap: 20px;
  justify-content: center;
}
```

Boksene ligger nå til venstre i raden. Med `justify-content` bestemmer du hvor i raden de skal ligge.

1. Prøv verdien `center`, og se på resultatet.
2. Prøv de andre verdiene, én om gangen:

| Verdi | Gjør |
|---|---|
| `flex-start` | Alt til venstre (standard) |
| `center` | Alt midtstilt |
| `flex-end` | Alt til høyre |
| `space-between` | Første helt til venstre, siste helt til høyre, lik avstand mellom |
| `space-around` | Lik luft rundt hver boks |

3. `space-between` er den mest brukte i praksis. Tenk over hvorfor: hva ligger typisk helt til venstre og helt til høyre i toppen av et nettsted?

For at du skal se forskjellen, må raden være bredere enn boksene til sammen.

4. Gjør nettleservinduet smalere til boksene fyller hele raden. Ser du fortsatt forskjell på verdiene? Gjør vinduet bredt igjen.

`justify-content` fordeler nemlig **plassen som er til overs**. Er det ingen plass til overs, er det ingenting å fordele.

---

## 8.5 `align-items`

```html
<div class="rad">
  <div class="boks">Kort tekst</div>
  <div class="boks">En litt lengre tekst som tar to eller tre linjer i boksen sin.</div>
  <div class="boks">Middels lang tekst her.</div>
</div>
```

1. Bytt ut innholdet i de tre boksene med tekster av ulik lengde, som i koden over.
2. Se på resultatet. Hvor høye er boksene?

Alle tre er **like høye** — like høye som den høyeste. Det skjer helt av seg selv i flexbox, og det er en av grunnene til at kortrader ser så ryddige ut.

Vil du ha det annerledes, bruker du `align-items`:

3. Legg til `align-items: flex-start;` i `.rad`-regelen. Nå får hver boks sin egen høyde.
4. Prøv de andre verdiene:

| Verdi | Gjør |
|---|---|
| `stretch` | Alle like høye (standard) |
| `flex-start` | Alle på linje øverst, egen høyde |
| `center` | Midtstilt på tvers |
| `flex-end` | På linje nederst |

5. Fjern `align-items` igjen, slik at boksene blir like høye.

Legg merke til navnene: `justify-content` styrer **bortover**, `align-items` styrer **på tvers**. Det er den eneste forskjellen å huske.

---

## 8.6 `flex-wrap`

```css
.rad {
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.kort {
  width: 300px;
  background-color: #ffffff;
  border: 1px solid #c8c8c8;
  border-radius: 10px;
  padding: 20px;
}
```

1. Lag seks kort inni `.rad`, hvert med en `<h3>` og et avsnitt.
2. Se på siden **uten** `flex-wrap`. Hva skjedde med bredden på 300 piksler?

Boksene ble klemt sammen for å få plass på én linje. Flexbox prøver nemlig alltid å få alt på rad, og krymper elementene om nødvendig.

3. Legg til `flex-wrap: wrap;`, og se på resultatet.

Nå brekker kortene om til ny linje når det ikke er plass — og de beholder bredden sin. Dette er selve oppskriften på et kortgalleri.

4. Gjør nettleservinduet smalere og bredere, og se hvordan kortene flytter seg av seg selv. Hvor mange kort får plass på én linje når vinduet er bredt? Når det er smalt?

Legg merke til at du nettopp laget noe som tilpasser seg skjermen — helt uten media queries. Det kommer i hefte 9.

5. Prøv `justify-content: center` på raden, slik at kortene midtstilles når den siste linja ikke er full.

---

## 8.7 Menyen

```html
<nav>
  <ul>
    <li><a href="index.html">Hjem</a></li>
    <li><a href="om.html">Om oss</a></li>
    <li><a href="kontakt.html">Kontakt</a></li>
  </ul>
</nav>
```

```css
nav ul {
  display: flex;
  gap: 24px;
  list-style: none;
  padding: 0;
  margin: 0;
}

nav a {
  color: #1a5276;
  text-decoration: none;
}
```

Siden hefte 3 har menyen din vært en punktliste som ligger nedover, med kuler foran. Nå fikser vi den.

1. Legg inn koden, og se på menyen.
2. Regelen gjør tre ting samtidig. Fjern én linje om gangen, og se hva hver av dem hadde ansvaret for:
   - `display: flex` — hva skjer uten den?
   - `list-style: none` — hva kommer tilbake?
   - `padding: 0` — hvorfor er menyen rykket inn uten den?

`list-style: none` fjerner kulepunktene, og `padding: 0` fjerner innrykket nettleseren gir alle lister av seg selv — akkurat som du så i hefte 7.

3. Legg til `justify-content: center` på menyen for å midtstille den.
4. Gi lenkene `padding: 10px 16px` og en `:hover`-regel fra hefte 5 som endrer bakgrunnsfargen. Husk `display: inline-block` fra 8.1 hvis paddingen oppfører seg rart.

### Logo til venstre, meny til høyre

```html
<header class="topp">
  <h1>Sykkelklubben</h1>
  <nav>
    <ul> ... </ul>
  </nav>
</header>
```

```css
.topp {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px 30px;
}
```

5. Bygg toppen slik, og se på resultatet. Her har du svaret på spørsmålet fra 8.4: `space-between` presser navnet helt til venstre og menyen helt til høyre, mens `align-items: center` sørger for at de står på linje midt på.

Legg merke til at det nå er **to** flex-containere: `.topp` legger overskriften og menyen på rad, og `nav ul` legger menypunktene på rad inni der.

---

## 8.8 To spalter med `<aside>`

```html
<div class="spalter">
  <main>
    <h2>Onsdagsturene</h2>
    <p>Vi sykler 30 km i rolig tempo.</p>
  </main>

  <aside>
    <h3>Visste du at ...</h3>
    <p>Klubben ble startet i 2019 av tre elever.</p>
  </aside>
</div>
```

```css
.spalter {
  display: flex;
  gap: 30px;
}

main {
  flex: 1;
}

aside {
  width: 250px;
  background-color: #eaf2f8;
  padding: 20px;
  border-radius: 8px;
}
```

Her er elementet som har ventet siden hefte 4: `<aside>`. Det er innhold som hører til siden, men som står **ved siden av** hovedsaken — en faktaboks, en lenkesamling, en «relaterte saker»-liste. Først nå, med flexbox, kan du faktisk plassere det ved siden av noe.

1. Bygg oppsettet, og se på resultatet.
2. Sidespalten er 250 piksler. Hva gjør `flex: 1` på `<main>`?

`flex: 1` betyr «ta all plassen som er til overs». Sidespalten får sine 250 piksler, og hovedinnholdet fyller resten — uansett hvor bredt vinduet er.

3. Fjern `flex: 1`, og se hva som skjer. Legg den tilbake.
4. Endre sidespalten til `width: 400px`. Måtte du endre noe på `<main>`?
5. Bytt om rekkefølgen i HTML-en, slik at `<aside>` kommer først. Nå ligger sidespalten til venstre.

### Om `<div class="spalter">`

I hefte 6 advarte vi mot *divitis* — å bruke `<div>` der et semantisk element hørte hjemme. Her er unntaket: denne `<div>`-en finnes **bare** for å legge to bokser på rad. Den betyr ingenting, og skal ikke bety noe. Det er nettopp det `<div>` er til for.

Regelen er fortsatt den samme: har innholdet en betydning, bruk elementet som beskriver den. Trenger du bare en boks for layout, bruk `<div>`.

6. Sett hele siden sammen: `<header class="topp">` med navn og meny, `<div class="spalter">` med `<main>` og `<aside>`, og en `<footer>` nederst.

---

## Sammendrag

### Block og inline

| Type | Bredde | Ny linje? | Eksempler |
|---|---|---|---|
| `block` | Hele bredden | Ja | `div`, `p`, `h1`, `section`, `li` |
| `inline` | Bare innholdet | Nei | `span`, `a`, `strong`, `img` |
| `inline-block` | Bare innholdet | Nei | Brukes på knapper og menylenker |
| `none` | Vises ikke i det hele tatt | — | Skjult innhold |

### Flexbox

```css
.rad {
  display: flex;
  gap: 20px;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
}
```

`display: flex` settes på **boksen utenpå**. Barna inni legger seg på rad.

| Egenskap | Styrer |
|---|---|
| `gap` | Avstanden mellom elementene |
| `justify-content` | Plassering **bortover**: `flex-start`, `center`, `flex-end`, `space-between`, `space-around` |
| `align-items` | Plassering **på tvers**: `stretch` (standard, like høye), `flex-start`, `center`, `flex-end` |
| `flex-wrap: wrap` | La elementene brekke om til ny linje når det er trangt |

### Menyen

```css
nav ul {
  display: flex;
  gap: 24px;
  list-style: none;
  padding: 0;
  margin: 0;
}
```

### To spalter

```css
.spalter {
  display: flex;
  gap: 30px;
}

main {
  flex: 1;
}

aside {
  width: 250px;
}
```

`flex: 1` betyr «ta all plassen som er til overs». `<aside>` er innhold som hører til siden, men som står ved siden av hovedsaken.

---

## Oppgaver

### Del A — Enkle oppgaver

**Oppgave A1**

```html
<div class="rad">
  <div class="boks">Én</div>
  <div class="boks">To</div>
</div>
```

```css
.boks {
  display: flex;
  gap: 20px;
}
```

Boksene legger seg ikke på rad. Finn feilen, rett den, og forklar med én setning hva som var galt.

**Oppgave A2**

```text
┌──────────────────────────────────┐
│   justify-content: center;       │
├──────────────────────────────────┤
│ }                                │
├──────────────────────────────────┤
│   display: flex;                 │
├──────────────────────────────────┤
│ .rad {                           │
├──────────────────────────────────┤
│   gap: 15px;                     │
└──────────────────────────────────┘
```

Sett sammen kodebitene til en gyldig regel, og prøv den på tre bokser.

**Oppgave A3**

```css
.rad {
  display: flex;
  justify-content: space-between;
}
```

Raden inneholder tre bokser og er mye bredere enn dem. Tegn på papir hvor de tre boksene havner. Hva skjer hvis du bytter til `center`? Og til `flex-end`? Skriv ned alle tre svarene før du tester.

**Oppgave A4**

```css
nav ul {
  display: ...;
  gap: ...;
  list-style: ...;
  padding: ...;
}
```

Skriv ferdig regelen slik at menyen blir vannrett, uten kulepunkter og uten innrykk, med passe luft mellom punktene.

**Oppgave A5**

Lag fila `galleri.html` med åtte kort i en rad som brekker om. Hvert kort skal ha fast bredde, ramme, avrundede hjørner og padding. Test ved å endre bredden på nettleservinduet.

**Oppgave A6**

Lag en topp til et nettsted du finner på: nettstedets navn til venstre og en meny med tre lenker til høyre, på samme linje, med bakgrunnsfarge og padding.

### Del B — Middels

**Oppgave B1**

> **🆕 Nytt stoff:** Det finnes to måter å skjule noe på, og de gjør forskjellige ting:
>
> `display: none;` — elementet forsvinner helt, og tar ingen plass
> `visibility: hidden;` — elementet blir usynlig, men **plassen står igjen**

Lag en rad med tre bokser. Skjul den midterste med `display: none`, se på resultatet, og bytt deretter til `visibility: hidden`. Beskriv forskjellen i en kommentar, og foreslå én situasjon der hver av dem er riktig valg.

**Oppgave B2**

> **🆕 Nytt stoff:** `align-items` gjelder alle elementene i raden. Vil du at **ett** av dem skal plasseres annerledes, setter du `align-self` på nettopp det elementet:
>
> `.spesiell { align-self: flex-end; }`

Lag en rad med fire bokser av ulik høyde. Alle skal ligge på linje øverst, bortsett fra én som skal ligge nederst. Bruk `align-items` på raden og `align-self` på den ene boksen.

**Oppgave B3**

Bygg en bunntekst i tre spalter: «Om oss» med et kort avsnitt, «Snarveier» med en punktliste med lenker, og «Kontakt» med en `<address>`. Spaltene skal ligge på rad med lik avstand, og hele bunnteksten skal ha bakgrunnsfarge og padding.

**Oppgave B4**

Lag fila `lagsiden.html` om et lag eller en gruppe: en topp med navn og meny, et hovedinnhold med minst to seksjoner, en sidespalte med en faktaboks og en lenkeliste, og en bunntekst. Bruk `<aside>` til sidespalten, og `flex: 1` på hovedinnholdet.

**Oppgave B5**

Åpne kortsiden din fra hefte 7. Legg kortene i en flex-rad med `flex-wrap`, og sørg for at de er like høye selv om tekstene er ulikt lange. Sammenlign med hvordan siden så ut før.

### Del C — Mer krevende

**Oppgave C1**

> **🆕 Nytt stoff:** Med `order` kan du endre **rekkefølgen** elementene vises i, uten å røre HTML-en:
>
> `.boks-b { order: -1; }` flytter boksen først i raden
>
> Alle flex-elementer har `order: 0` som standard. Lavere tall kommer først.

Lag en rad med tre bokser merket A, B og C i HTML-en. Bruk `order` til å vise dem i rekkefølgen C, A, B — uten å flytte en eneste linje i HTML-fila. Skriv deretter en kommentar: Hvorfor kan dette være problematisk for en som bruker skjermleser, som leser HTML-rekkefølgen og ikke den visuelle?

**Oppgave C2**

Bygg en komplett forside for et nettsted du finner på. Krav:

- `<header>` med navn til venstre og meny til høyre (`space-between`)
- Under toppen: en rad med tre «tjenestekort» som er like høye
- Deretter `<div class="spalter">` med `<main>` (`flex: 1`) og `<aside>` (fast bredde)
- `<footer>` med tre spalter
- Alle radene laget med flexbox, og `gap` i stedet for margin mellom elementene
- `* { box-sizing: border-box; }` øverst i stilfila

Tegn layouten på papir først, og marker hvilke bokser som er flex-containere.

**Oppgave C3**

Undersøk selv, og skriv svarene som kommentarer i CSS-fila:

1. Sett `display: flex` på et element som bare har **ett** barn. Skjer det noe?
2. Sett `display: flex` på en `<ul>` uten å fjerne `list-style`. Hvor havner kulepunktene?
3. Legg vanlig tekst rett inni en flex-container, uten noen tagg rundt. Blir teksten et flex-element?
4. Sett både `justify-content: center` og `align-items: center` på en container som er 400 piksler høy, med ett element inni. Hvor havner elementet? (Dette er det enkleste trikset som finnes for å sentrere noe i begge retninger.)
5. Gi to bokser i samme rad `flex: 1` hver. Hvor brede blir de? Gi deretter den ene `flex: 2`. Hva skjedde?

---

*Hefte 8 av serien «Nettsider fra bunnen av». Neste hefte: Responsivt design.*
