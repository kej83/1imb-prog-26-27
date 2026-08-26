# Kapittel 2: Tekst, lister og tabeller

*HTML og CSS — hefte 2 i serien «Nettsider fra bunnen av». Bygger på hefte 1: Din første nettside.*

---

## Slik jobber du med dette heftet

Heftet følger arbeidsmåten **PRIMM**, med stegene **[Predict]** (les koden og forutsi hvordan siden ser ut), **[Run]** (skriv av og se resultatet), **[Investigate]** (gjør små endringer og undersøk), **[Modify]** (utvid siden) og **[Make]** (lag din helt egen side — i oppgavene bakerst).

### Husk fra hefte 1

Du jobber i en mappe i VS Code. Ny HTML-fil: skriv `!` og trykk `ENTER` for å få malen, sett `lang="no"`, og skriv innholdet mellom `<body>` og `</body>`. Lagre med `CTRL` + `S`, og se resultatet med **Show Preview** (høyreklikk i koden) eller **Go Live** (knappen nede til høyre).

> **💡 Tips:** Lag en ny mappe `nettside2` for dette heftet, og åpne den i VS Code med **File → Open Folder**.

> **🐞 Når noe går galt:** Ser siden rar ut, er det som oftest en glemt lukketagg eller en skrivefeil i et taggnavn. VS Code fargelegger koden — hvis fargene «velter» nedover fila, har du mest sannsynlig en tagg som ikke er lukket.

---

## 2.1 Utheving: strong og em

```html
<body>
  <h1>Beskjed til klassen</h1>
  <p>Prøven i engelsk er flyttet til <strong>fredag</strong>.
  Husk å ta med <em>egen</em> PC.</p>
</body>
```

Noen ord er viktigere enn andre. I HTML kan vi utheve tekst *inne i* et avsnitt:

| Element | Betydning | Vises som oftest |
|---|---|---|
| `<strong>` | Viktig tekst | **Fet skrift** |
| `<em>` | Trykk på ordet (*emphasis*) | *Kursiv* |

1. Les koden. Hvilke ord blir uthevet, og hvordan? **[Predict]**
2. Lag fila `beskjed.html`, skriv av koden, og se på resultatet. **[Run]**
3. Bytt om: sett `<em>` rundt `fredag` og `<strong>` rundt `egen`. Hva endret seg? Bytt tilbake etterpå. **[Investigate]**
4. Kan et ord være både viktig **og** ha trykk? Prøv `<strong><em>fredag</em></strong>`. **[Investigate]**
5. Legg til en ny setning i avsnittet der minst ett ord er merket som viktig. **[Modify]**

Legg merke til at `<strong>` og `<em>` ligger **inni** `<p>`-elementet. Tagger som pakkes inn i hverandre, må lukkes i motsatt rekkefølge av at de ble åpnet — den som ble åpnet sist, lukkes først.

> **⚠️ Merk:** HTML handler om **betydning**, ikke utseende. `<strong>` betyr «dette er viktig» — at nettleseren viser det med fet skrift, er bare standardvalget. Hvordan ting skal se ut, styrer vi med CSS senere i serien. Da vil du også se at det finnes en tagg `<b>` for fet skrift — men utviklere bruker `<strong>` og `<em>`, som sier noe om innholdet.

---

## 2.2 Punktlister og nummererte lister

```html
<body>
  <h1>Handleliste</h1>
  <ul>
    <li>Melk</li>
    <li>Brød</li>
    <li>Ost</li>
  </ul>
</body>
```

Lister bruker du oftere enn du tror: menyer, ingredienser, spillelister, resultatlister. HTML har to typer:

| Element | Navn | Gir |
|---|---|---|
| `<ul>` | *unordered list* | Punktliste med kulepunkter |
| `<ol>` | *ordered list* | Nummerert liste: 1, 2, 3, ... |
| `<li>` | *list item* | Ett punkt i lista — brukes i begge |

1. Les koden. Hvordan vil handlelista se ut? **[Predict]**
2. Lag fila `lister.html`, skriv av koden, og se på resultatet. **[Run]**
3. Endre `<ul>` og `</ul>` til `<ol>` og `</ol>`. Hva skjedde med kulepunktene? **[Investigate]**
4. Legg til to nye varer i lista. Måtte du endre noe annet for at nummereringen skulle stemme? **[Investigate]**
5. Bytt om på to `<li>`-linjer i koden. Hva skjer med numrene på siden? **[Investigate]**

Nummererte lister passer når rekkefølgen betyr noe — trinn i en oppskrift, en topp 10-liste. Punktlister passer når rekkefølgen er likegyldig. Og som du så: nettleseren nummererer selv. Du skal aldri skrive «1.» inn i teksten i et `<li>`.

6. Under handlelista: lag en `<h2>` med teksten `Slik pakker du sekken` og en nummerert liste med tre trinn du bestemmer selv. **[Modify]**

> **⚠️ Merk:** Inne i `<ul>` og `<ol>` skal det **bare** ligge `<li>`-elementer. Tekst rett inni `<ul>`, utenfor et `<li>`, er feil HTML — selv om nettleseren sjelden klager.

---

## 2.3 Lister inni lister

```html
<body>
  <h1>Pakkeliste for turen</h1>
  <ul>
    <li>Klær
      <ul>
        <li>Ullsokker</li>
        <li>Regnjakke</li>
      </ul>
    </li>
    <li>Mat</li>
    <li>Førstehjelpsutstyr</li>
  </ul>
</body>
```

Et listepunkt kan inneholde en helt ny liste. Da får du en liste med undernivåer.

1. Les koden. Hvor mange punkter er det på øverste nivå? Hvilke punkter blir rykket inn? **[Predict]**
2. Skriv av koden i en ny fil `pakkeliste.html`, og se på resultatet. **[Run]**

Se nøye på koden: hele underlista `<ul>...</ul>` ligger **inni** `<li>Klær ... </li>`, før lukketaggen. Innrykket i koden gjør strukturen lettere å lese — nettleseren trenger det ikke, men mennesker gjør det.

3. Se på kulepunktene på siden. Bruker underlista samme tegn som hovedlista? **[Investigate]**
4. Gi punktet `Mat` en underliste med minst tre matvarer. **[Modify]**
5. Klarer du tre nivåer? Gi en av matvarene en egen underliste. **[Modify]**

> **💡 Tips:** VS Code hjelper deg med innrykk automatisk. Blir koden rotete, kan du høyreklikke i koden og velge **Format Document** — da rykkes alt pent inn. Prøv!

---

## 2.4 Tabeller

```html
<body>
  <h1>Timeplan for mandag</h1>
  <table>
    <tr>
      <th>Time</th>
      <th>Fag</th>
    </tr>
    <tr>
      <td>1</td>
      <td>Norsk</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Programmering</td>
    </tr>
  </table>
</body>
```

Tabeller viser data i rader og kolonner — som en timeplan, en resultatliste eller en prisliste.

| Element | Navn | Gir |
|---|---|---|
| `<table>` | *table* | Selve tabellen |
| `<tr>` | *table row* | Én rad i tabellen |
| `<th>` | *table header* | Overskriftscelle — vises med fet skrift |
| `<td>` | *table data* | Vanlig celle med data |

1. Les koden. Hvor mange rader og kolonner får tabellen? **[Predict]**
2. Lag fila `timeplan.html`, skriv av koden, og se på resultatet. **[Run]**

En tabell bygges rad for rad: hver `<tr>` er en rad, og inni raden legger du én celle per kolonne. Første rad bruker `<th>` fordi det er overskriftene.

3. Tell taggene: hvor mange celler har hver rad? Hva skjer hvis du sletter en `<td>`-celle i en av radene? Se på resultatet, og legg cellen tilbake. **[Investigate]**
4. Utvid timeplanen med resten av timene dine på mandag. **[Modify]**
5. Legg til en tredje kolonne `Rom`: en ny `<th>` i første rad, og en ny `<td>` i hver av de andre radene. **[Modify]**

> **⚠️ Merk:** Tabellen har ingen streker eller rammer ennå — den ser kanskje litt «naken» ut. Rammer, farger og luft i cellene lager vi med CSS i hefte 5 og 6. Nå bygger vi bare strukturen — og den må være riktig for at CSS-en skal bli enkel senere.

> **⚠️ Merk:** Tabeller er til **data** i rader og kolonner. De skal ikke brukes til å plassere ting utover siden — layout lager vi med CSS i hefte 7.

---

## 2.5 Sitater: blockquote, q og cite

```html
<body>
  <h1>Min favorittbok</h1>
  <p>Jeg leser <cite>Ringenes herre</cite> for andre gang.</p>
  <blockquote>
    <p>Selv den minste person kan forandre verdens gang.</p>
  </blockquote>
  <p>Galadriel sier dette til Frodo, og som hun sier:
  <q>Selv den minste person kan forandre verdens gang.</q></p>
</body>
```

Når du siterer noen — en bok, en artikkel, et intervju — har HTML egne elementer for det:

| Element | Brukes til | Vises som oftest |
|---|---|---|
| `<blockquote>` | Lengre sitat som står for seg selv | Innrykket blokk |
| `<q>` | Kort sitat inne i en setning | Får anførselstegn automatisk |
| `<cite>` | Tittelen på et verk (bok, film, sang) | *Kursiv* |

1. Les koden. Hva blir innrykket? Hvor dukker det opp anførselstegn? **[Predict]**
2. Lag fila `sitat.html`, skriv av koden, og se på resultatet. **[Run]**
3. Skrev du anførselstegn selv noe sted? Se på teksten i `<q>`-elementet på siden — hvor kom tegnene fra? **[Investigate]**
4. Bytt ut `<q>`-elementet med vanlige anførselstegn du skriver selv. Ser du forskjell på siden? Hvorfor er `<q>` likevel bedre? (Hint: hva vet nettleseren — og en søkemotor — om teksten nå?) Bytt tilbake. **[Investigate]**
5. Legg til et avsnitt om en annen bok eller film du liker: tittelen i `<cite>`, og et kort sitat fra den i `<q>`. **[Modify]**
6. Finn et sitat du liker (fra en bok, en sang eller en kjent person), og legg det til som en `<blockquote>` med et avsnitt under som forteller hvor sitatet er hentet fra. **[Modify]**

> **💡 Tips:** Legg merke til mønsteret fra `<strong>` og `<em>`: HTML beskriver hva teksten **er** (et sitat, en verkstittel), ikke hvordan den skal se ut. Det er nettopp derfor elementene finnes.

---

## 2.6 Kode, forkortelser og kontaktinfo

```html
<body>
  <h1>HTML-tips</h1>
  <p>I <abbr title="HyperText Markup Language">HTML</abbr> lager du
  et avsnitt med taggen <code>&lt;p&gt;</code>, og en overskrift
  med <code>&lt;h1&gt;</code>.</p>
  <hr>
  <address>
    Skrevet av Mufasa<br>
    mufasa@skolen.no
  </address>
</body>
```

Til slutt tre elementer du får bruk for når du skriver *om* fag — for eksempel når du skal dokumentere dine egne prosjekter:

| Element | Brukes til | Vises som oftest |
|---|---|---|
| `<code>` | Kode inne i tekst | `Skrivemaskinskrift` |
| `<abbr>` | Forkortelse — med forklaring i `title`-attributtet | Prikket understrek |
| `<address>` | Kontaktinfo for den som eier siden | *Kursiv* |

1. Les koden. Hvilke deler av teksten vil skille seg ut, og hvordan? **[Predict]**
2. Lag fila `tips.html`, skriv av koden, og se på resultatet med **Go Live**. **[Run]**
3. Hold musepekeren over ordet HTML på siden, og vent et øyeblikk. Hva skjer? Hvor i koden kommer teksten fra? **[Investigate]**

Så var det den mystiske skrivemåten `&lt;p&gt;`. Prøv selv:

4. Endre `<code>&lt;p&gt;</code>` til `<code><p></code>`, lagre, og se på siden. Hvor ble taggen av? **[Investigate]**

Skriver du `<p>` rett i teksten, tror nettleseren at du starter et nytt avsnitt! Skal tegnene `<` og `>` *vises* på siden, må du skrive dem med koder: `&lt;` (*less than*) gir `<`, og `&gt;` (*greater than*) gir `>`. Angre endringen fra punkt 4.

5. Utvid avsnittet med en setning om `<br>`-taggen, der taggen vises med `<code>` og de spesielle tegnkodene. **[Modify]**
6. Legg til forkortelsen `<abbr title="Cascading Style Sheets">CSS</abbr>` i en ny setning, og bytt ut navnet og e-postadressen i `<address>` med dine egne. **[Modify]**

> **💡 Tips:** `<address>` hører typisk hjemme nederst på siden, i sidens bunntekst. I hefte 4 lærer du elementet `<footer>` — da får kontaktinfoen et enda tydeligere hjem.

---

## Sammendrag

I dette heftet har du fylt verktøykassa med elementer for tekst, lister og tabeller — og lært et viktig prinsipp: HTML beskriver hva innholdet **er**, ikke hvordan det ser ut.

### Utheving og sitater

```html
<p>Husk <strong>fredag</strong> - det er <em>viktig</em>.</p>
<p>Jeg leser <cite>Ringenes herre</cite>, og som Galadriel
sier: <q>Selv den minste person kan forandre verdens gang.</q></p>
<blockquote>
  <p>Et lengre sitat står i sin egen blokk.</p>
</blockquote>
```

`<strong>` er viktig tekst (fet), `<em>` er trykk (kursiv), `<q>` gir anførselstegn automatisk, `<cite>` er verkstitler, og `<blockquote>` er lengre sitater. Tagger inni hverandre lukkes i motsatt rekkefølge.

### Lister

```html
<ul>
  <li>Punktliste - rekkefølgen er likegyldig</li>
  <li>Klær
    <ul>
      <li>En liste kan ligge inni et listepunkt</li>
    </ul>
  </li>
</ul>
<ol>
  <li>Nummerert liste - rekkefølgen betyr noe</li>
  <li>Nettleseren teller selv</li>
</ol>
```

Inne i `<ul>` og `<ol>` ligger det bare `<li>`-elementer. En underliste ligger *inni* et `<li>`, før lukketaggen.

### Tabeller

```html
<table>
  <tr>
    <th>Time</th>
    <th>Fag</th>
  </tr>
  <tr>
    <td>1</td>
    <td>Norsk</td>
  </tr>
</table>
```

Rad for rad med `<tr>`, overskriftsceller med `<th>`, dataceller med `<td>`. Alle rader skal ha like mange celler. Rammer og farger kommer med CSS.

### Kode, forkortelser og kontaktinfo

```html
<p>Taggen <code>&lt;p&gt;</code> lager et avsnitt i
<abbr title="HyperText Markup Language">HTML</abbr>.</p>
<address>
  Mufasa<br>
  mufasa@skolen.no
</address>
```

`<code>` viser kode i teksten, `<abbr>` forklarer forkortelser når musepekeren hviler over ordet, og `<address>` er kontaktinfo. Tegnene `<` og `>` skrives `&lt;` og `&gt;` når de skal vises på siden.

---

## Oppgaver

> **💡 Tips:** Lag en ny fil for hver oppgave. Start med `!` + `ENTER`, sett `lang="no"`, og velg en beskrivende `<title>`.

### Del A — Enkle oppgaver

**Oppgave A1**

```html
<ul>
  <li>Epler
  <li>Bananer</li>
  <il>Druer</il>
</ul>
```

Koden inneholder to feil. Finn dem ved å lese koden, rett dem, og sjekk at lista viser tre punkter.

**Oppgave A2**

```text
┌────────────────────────────────┐
│ </ol>                          │
├────────────────────────────────┤
│   <li>Stek vaflene</li>        │
├────────────────────────────────┤
│ <h1>Vafler på 1-2-3</h1>       │
├────────────────────────────────┤
│   <li>Visp sammen røren</li>   │
├────────────────────────────────┤
│ <ol>                           │
├────────────────────────────────┤
│   <li>La røren svelle</li>     │
└────────────────────────────────┘
```

Sett sammen kodebitene i riktig rekkefølge, slik at siden viser en overskrift og en nummerert liste med de tre trinnene i fornuftig rekkefølge. Skriv koden inn i en ny fil, og sjekk resultatet.

**Oppgave A3**

```html
<h1>Kveldens kamp</h1>
<p>I kveld spiller <strong>Norge</strong> mot Brasil.</p>
<ol>
  <li>Norge</li>
  <li>Brasil</li>
  <li>Sverige</li>
</ol>
```

Les koden, og tegn på papir hvordan siden vil se ut. Hvilket ord er uthevet? Hvilke tall står foran lagene? Skriv deretter av koden, og sjekk svaret ditt.

**Oppgave A4**

```html
<h1>Min spilleliste</h1>
<ol>
  <li>...</li>
  <li>...</li>
  <li>...</li>
</ol>
```

Fyll inn skjelettet med dine tre favorittlåter, med den beste øverst. Merk artistnavnet i hvert punkt med `<em>`, slik: `<li>Låtnavn av <em>Artist</em></li>`.

**Oppgave A5**

Lag fila `ukemeny.html` med en tabell over middager for tre valgfrie dager: én kolonne for dag og én for middag. Bruk `<th>`-celler i første rad, og husk en `<h1>` over tabellen.

**Oppgave A6**

Lag fila `favorittfilm.html` om en film eller serie du liker: en `<h1>`, et avsnitt der tittelen står i `<cite>`, og et kort sitat fra filmen i `<q>` inne i en setning. Avslutt med en `<blockquote>` som inneholder et lengre sitat (eller en anmeldelse du dikter opp).

**Oppgave A7**

Lag fila `omtale.html` der du forklarer to HTML-tagger du har lært, for en medelev. Taggnavnene skal vises på siden med `<code>` og tegnkodene `&lt;` og `&gt;`. Avslutt siden med `<address>` som inneholder navnet ditt og en (gjerne oppdiktet) e-postadresse.

### Del B — Middels

> **💡 Tips:** Noen av oppgavene i del B og C starter med en boks merket **Nytt stoff**. Der lærer du noe som ikke står i innlæringsdelen — les boksen nøye, og ta det nye i bruk i oppgaven.

**Oppgave B1**

```html
<h1>Turnering i friminuttet</h1>
<table>
  <tr>
    <th>Plass</th>
    <th>Lag</th>
    <th>Poeng</th>
  </tr>
  <tr>
    <td>1</td>
    <td>9A</td>
  </tr>
  <tr>
    <td>2</td>
    <th>9C</th>
    <td>4</td>
  </tr>
</table>
```

Tabellen har to feil: én rad mangler en celle, og én celle bruker feil taggtype. Rett feilene, og utvid deretter tabellen med to nye rader, slik at fire lag er med.

**Oppgave B2**

> **🆕 Nytt stoff:** En tabell kan få sin egen overskrift med elementet `<caption>`. Den skrives rett etter åpnetaggen `<table>`, og vises sentrert over tabellen:
>
> `<table>`
> `  <caption>Resultater fra klubbmesterskapet</caption>`
> `  <tr> ... </tr>`
> `</table>`

Lag fila `resultater.html` med en resultatliste fra en valgfri idrett eller e-sport: en tabell med kolonnene `Plass`, `Navn` og `Resultat`, med minst fem rader i tillegg til overskriftsraden — og en beskrivende `<caption>`. Over tabellen: en `<h1>` og et innledende avsnitt der minst ett ord er uthevet med `<strong>`. Under tabellen: en `<hr>` og en `<address>` med navnet ditt som ansvarlig for siden.

**Oppgave B3**

```html
<h1>Skolens kantinemeny</h1>
<h2>Mandag</h2>
...
<h2>Tirsdag</h2>
...
```

Lag fila `kantine.html`. Under hver dag skal det ligge en punktliste med minst tre retter. Minst én rett per dag skal ha en underliste med to valg av tilbehør. Merk dagens anbefaling med `<strong>` inne i listepunktet.

**Oppgave B4**

> **🆕 Nytt stoff:** En nummerert liste trenger ikke å starte på 1. Med attributtet `start` velger du selv første nummer: `<ol start="5">` gir en liste som teller 5, 6, 7, ...

Lag fila `pannekaker.html` med en oppskrift på pannekaker i to deler: en `<h2>` med teksten `Røren` fulgt av en nummerert liste med trinn 1–4, og en `<h2>` med teksten `Stekingen` fulgt av en ny nummerert liste som fortsetter tellingen på 5. Sjekk på siden at numrene fortsetter riktig.

**Oppgave B5**

```text
Overskrift: Ordbok for gamere
Et innledende avsnitt som forklarer hva siden er.
En punktliste med minst fire gamer-uttrykk.
   Hvert uttrykk står i fet skrift, fulgt av forklaringen.
Til slutt: en setning der forkortelsen GG forklares
   med abbr, slik at forklaringen vises med musepekeren.
```

Lag fila `ordbok.html` ved å følge beskrivelsen ovenfor. Velg selv riktige HTML-elementer for hver del.

**Oppgave B6**

Åpne `favorittfilm.html` fra A6. Legg til en tabell med fakta om filmen: kolonnene `Felt` og `Verdi`, en `<caption>` med filmens tittel, og rader for regissør, år og sjanger. Legg deretter til en nummerert topp 3-liste over scenene du husker best. Sjekk til slutt koden med **Format Document** — ligger alt pent innrykket?

### Del C — Mer krevende

**Oppgave C1**

> **🆕 Nytt stoff:** En celle kan strekke seg over flere kolonner eller rader. Attributtet `colspan` slår sammen kolonner, og `rowspan` slår sammen rader:
>
> `<td colspan="3">Denne cellen dekker tre kolonner</td>`
> `<td rowspan="2">Denne cellen dekker to rader</td>`
>
> Når en celle dekker flere plasser, skal de plassene **ikke** ha egne celler i tillegg — cellene den «spiser», skriver du rett og slett ikke. Tell alltid at hver rad til sammen dekker like mange kolonner.

```html
<table>
  <tr>
    <th>Time</th>
    <th>Mandag</th>
    <th>Tirsdag</th>
  </tr>
  <tr>
    <th>1</th>
    <td>Norsk</td>
    <td rowspan="2">Programmering</td>
  </tr>
  <tr>
    <th>2</th>
    <td>Engelsk</td>
  </tr>
  <tr>
    <th>3</th>
    <td colspan="2">Lunsj i kantina</td>
  </tr>
</table>
```

Studer og kjør koden ovenfor: tirsdag har dobbelttime i programmering, og lunsjen dekker begge dagene. Lag deretter fila `timeplan2.html` med din egen timeplan for **tre valgfrie dager**. Krav:

- En `<caption>` og en overskriftsrad med `Time` pluss de tre dagene
- Minst fire timer (rader)
- Minst én dobbelttime laget med `rowspan`
- En lunsjrad der én celle dekker alle dagene med `colspan`
- Sjekk nøye at ingen rad har for mange celler

**Oppgave C2**

> **🆕 Nytt stoff:** Store tabeller deles gjerne i tre deler: `<thead>` (overskriftsradene), `<tbody>` (selve dataene) og `<tfoot>` (en avslutningsrad, for eksempel en sum). Delene pakkes rundt radene:
>
> `<table>`
> `  <thead> <tr> ... </tr> </thead>`
> `  <tbody> <tr> ... </tr> <tr> ... </tr> </tbody>`
> `  <tfoot> <tr> ... </tr> </tfoot>`
> `</table>`
>
> Siden ser lik ut som før — men strukturen gir mening til delene, og i hefte 5 kan du style dem hver for seg med CSS.

Lag fila `medaljer.html` med en medaljeoversikt fra et (gjerne oppdiktet) mesterskap: kolonnene `Land`, `Gull`, `Sølv` og `Bronse`, minst fire land i `<tbody>`, overskriftsraden i `<thead>`, og en sumrad nederst i `<tfoot>` der første celle inneholder teksten `Totalt` og de andre inneholder summene (regn ut selv). Bruk også `<caption>`.

**Oppgave C3**

Lag fila `quiz.html` med en quiz for klassen:

- Én `<h1>` og et innledende avsnitt som forklarer reglene, der viktige ord er merket med `<strong>`
- Minst fem spørsmål som en nummerert liste
- Hvert spørsmål har en punktliste inni seg med tre svaralternativer
- Under quizen: en `<hr>`, en `<h2>` med teksten `Fasit` — og fasiten som en tabell med kolonnene `Spørsmål` og `Svar`, der du bruker `<thead>` og `<tbody>`
- Nederst: `<address>` med quizmesterens navn

**Oppgave C4**

Lag fila `htmlguide.html` — en guide til HTML, skrevet i HTML! Siden skal handle om minst fire av elementene du har lært i hefte 1 og 2. Krav:

- Ett delkapittel (`<h2>`) per element
- I hvert delkapittel: et avsnitt som forklarer elementet, der taggnavnet vises med `<code>` og tegnkodene `&lt;` og `&gt;`
- Minst én forkortelse forklart med `<abbr>` (for eksempel HTML)
- En tabell nederst som oppsummerer: `<caption>`, kolonnene `Tagg` og `Brukes til`, og én rad per element
- Guiden avsluttes med et motiverende sitat i `<blockquote>`

**Oppgave C5**

Undersøk selv, og skriv svarene som kommentarer i fila `eksperiment2.html`:

1. Legg et helt `<p>`-element inni et `<li>`. Fungerer det? Se på luften rundt teksten.
2. Legg en liten tabell inni en `<td>`-celle i en annen tabell. Fungerer det? Når kunne det (kanskje) være nyttig?
3. Skriv `<q>` inni et `<blockquote>`-sitat. Hva skjer med anførselstegnene?
4. Gi en celle `colspan="10"` i en tabell som bare har tre kolonner. Hva skjer med tabellen?
5. Fjern `</li>` fra alle punktene i en liste. Ser siden fortsatt riktig ut? Skriv én setning om hvorfor du likevel alltid skal skrive lukketaggene.

---

*Hefte 2 av serien «Nettsider fra bunnen av». Neste hefte: Lenker, bilder og medier.*
