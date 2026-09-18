# Prosjekt: Ditt eget nettsted

*Avsluttende prosjekt i serien «Nettsider fra bunnen av». Bygger på hefte 1–9.*

---

**Navn:** ............................................................  **Klasse:** ....................

---

## Oppgaven

Du skal planlegge og bygge et **helt nettsted på tre eller flere sider** om et tema du velger selv. Nettstedet skal være responsivt, og bruke det du har lært i hefte 1–9.

Dette er ikke et nytt hefte med nytt stoff. Alt du trenger, kan du allerede — oppgaven er å sette det sammen selv, uten at noen forteller deg hvilket element eller hvilken regel du skal bruke hvor. Du har heftene tilgjengelig hele veien, og du skal bruke dem som oppslagsverk.

---

## Velg tema

Velg noe du kan eller vil finne ut av. Det beste temaet er ett du har lyst til å skrive om — da blir innholdet bedre, og da orker du å gjøre det siste 20 prosentene som skiller et greit nettsted fra et godt et.

| Type | Forslag |
|---|---|
| Interesse | En hobby, en idrett, et spill, en musikksjanger |
| Noen andre | En artist, et lag, en forfatter, en oppfinner |
| Et sted | Hjemstedet ditt, en by du vil besøke, skolen |
| Noe du kan | En oppskriftssamling, en guide, en anmeldelsesside |
| Noe oppdiktet | En klubb, en festival, en bedrift, et band |

> **💡 Tips:** Unngå tema der du må lete lenge etter innhold. Du skal bruke tida på koden, ikke på research.

**Mitt tema:** ..............................................................................

---

## Slik kommer du i gang

### Steg 1: Skisse på papir

Før du skriver en eneste kodelinje, tegn sidene dine på papir. Én rute per side. Marker hvor toppen, menyen, hovedinnholdet, sidespalten og bunnteksten skal være.

Dette steget føles unødvendig, og det er det aldri. Alle som bygger nettsteder profesjonelt, tegner først.

### Steg 2: Bestem sidene

Skriv ned hvilke sider du skal ha, og hva som er på hver av dem. Et vanlig oppsett:

| Fil | Innhold |
|---|---|
| `index.html` | Forsiden — kort introduksjon, det viktigste |
| `side2.html` | En hoveddel av temaet |
| `side3.html` | En annen hoveddel |
| `om.html` | Om siden, kilder, kontakt |

Gi filene navn som passer til *ditt* tema — `konserter.html`, `oppskrifter.html`, `historie.html`. Husk reglene: små bokstaver, bindestrek i stedet for mellomrom, ingen æ, ø eller å.

### Steg 3: Lag mappa

```text
mitt-nettsted/
├── index.html
├── ...
├── stil.css
└── bilder/
```

### Steg 4: Bygg skjelettet først

Lag **alle** sidene med sideskjelettet fra hefte 4 og samme meny, før du fyller inn innhold. Da har du et nettsted som henger sammen fra dag én, og resten er påfyll.

### Steg 5: Innhold før stil

Skriv ferdig HTML-en med ekte innhold før du begynner på CSS-en. Det er fristende å style med en gang, men da ender du med å style om igjen hver gang innholdet endrer seg.

---

## Minstekrav

Alt i disse to tabellene skal være på plass. Kryss av underveis.

### HTML

| | Krav | Hefte |
|:--:|------------------------------------------------|:-----:|
| ☐ | Minst **tre sider** som er lenket sammen med en felles meny | 3 |
| ☐ | Riktig mal på alle sider: `lang="no"`, `<meta charset>`, og en beskrivende `<title>` per side | 1 |
| ☐ | Sideskjelett på alle sider: `<header>`, `<nav>`, `<main>`, `<footer>` | 4 |
| ☐ | Bare **én** `<h1>` per side, og overskriftsnivåer som følger strukturen | 1, 4 |
| ☐ | Minst to `<section>` med egen overskrift | 4 |
| ☐ | Minst én punktliste og én nummerert liste | 2 |
| ☐ | Minst **tre bilder** med god `alt`-tekst, minst ett i `<figure>` med `<figcaption>` | 3 |
| ☐ | Minst én tabell med `<caption>` og `<thead>` | 2, 4 |
| ☐ | Minst ett sitat med `<blockquote>` eller `<q>` | 2 |
| ☐ | Minst én lenke til et annet nettsted, som åpnes i ny fane | 3 |
| ☐ | `<address>` i bunnteksten | 2, 4 |
| ☐ | Kommentarer i koden som viser hvor hoveddelene begynner | 1 |

### CSS

| | Krav | Hefte |
|:--:|------------------------------------------------|:-----:|
| ☐ | Én felles `stil.css` som er koblet til **alle** sidene med `<link>` | 5 |
| ☐ | `* { box-sizing: border-box; }` øverst i stilfila | 7 |
| ☐ | Skrifttype, skriftstørrelse og linjeavstand satt på `body` | 5 |
| ☐ | Et fargevalg som henger sammen, med god kontrast mellom tekst og bakgrunn | 5 |
| ☐ | Minst tre egne klasser som faktisk brukes | 6 |
| ☐ | Padding og margin brukt bevisst — ingenting klistrer seg til kanten | 7 |
| ☐ | Meny laget med flexbox | 8 |
| ☐ | Minst én rad med flexbox — for eksempel kort eller spalter | 8 |
| ☐ | `img { max-width: 100%; }` og et innholdsområde med `max-width` | 9 |
| ☐ | Minst én media query som endrer layouten på smal skjerm | 9 |
| ☐ | Ingen vannrett rulling ved noen skjermbredde | 9 |
| ☐ | Kommentarer som deler stilfila inn i deler | 5 |

---

## Utvidelser

Når minstekravene er på plass, velg noen av disse. De er der for å strekke deg — ingen er obligatoriske, og det er bedre å gjøre to skikkelig enn fem halvveis.

| | Utvidelse | Hefte |
|:--:|------------------------------------------------|:-----:|
| ☐ | Sidespalte med `<aside>` ved siden av `<main>`, som stables på mobil | 8, 9 |
| ☐ | Kortgalleri med `flex-wrap` som går fra tre til to til én i bredden | 8, 9 |
| ☐ | Knapper eller menylenker med `:hover`-effekt | 5, 7 |
| ☐ | Lyd eller video med `controls` | 3 |
| ☐ | Tabell med `colspan` eller `rowspan` | 4 |
| ☐ | `box-shadow` på kort | 7 |
| ☐ | `object-fit: cover` slik at bilder i ulike størrelser ser like ut | 9 |
| ☐ | To brytepunkter i stedet for ett | 9 |
| ☐ | `<article>` med egen `<footer>` for hver sak | 4 |

---

## Fremdriftsplan

| Uke | Dette skal være ferdig |
|---|---|
| 1 | Tema valgt, skisse tegnet, mappe laget, alle sidene bygget med skjelett og felles meny |
| 2 | Alt innhold på plass i HTML — tekst, bilder, lister, tabell, sitat. Stilfila påbegynt |
| 3 | CSS ferdig, responsivitet testet, sjekklista gjennomgått, innlevering |

Blir du ferdig før tida, gå løs på utvidelsene — ikke på et fjerde tema.

---

## Sjekkliste før innlevering

Gå gjennom denne til slutt. Alle punktene skal være avkrysset.

| | Sjekk |
|:--:|--------------------------------------------------------|
| ☐ | Alle lenkene i menyen virker, fra **alle** sidene |
| ☐ | Alle bildene vises — ingen ødelagte bildeikoner |
| ☐ | Alle bildene har en `alt`-tekst som faktisk beskriver bildet |
| ☐ | Siden er testet i mobilvisning (Inspiser → mobilikonet) på minst to bredder |
| ☐ | Ingen steder må man dra sidelengs for å se innholdet |
| ☐ | Alle filene er kjørt gjennom **Format Document** i VS Code |
| ☐ | Filnavnene følger reglene: små bokstaver, ingen mellomrom, ingen æøå |
| ☐ | Du har lest gjennom din egen kode én gang til slutt |
| ☐ | En medelev har åpnet nettstedet ditt og klikket seg rundt |

> **💡 Tips:** Det siste punktet er det nyttigste. Du er blind for ditt eget nettsted etter tre uker — en medelev finner den døde lenken på ti sekunder.

---

## Slik blir prosjektet vurdert

| Område | Lav måloppnåelse | Middels måloppnåelse | Høy måloppnåelse |
|---|---|---|---|
| **Struktur** | Sidene henger sammen, men skjelettet er ufullstendig eller delvis feil | Alle sidene har riktig sideskjelett og fungerende meny | Strukturen er gjennomtenkt på alle sider, med riktig element til alt innhold |
| **Semantikk** | Bruker mest `<div>` og generelle elementer | Bruker semantiske elementer stort sett riktig | Velger alltid elementet som beskriver innholdet, og kan begrunne valgene |
| **CSS** | Noe stil er på plass, men koden gjentar seg | Felles stilfil med klasser, ryddig og uten mye gjentakelse | Gjennomtenkt bruk av klasser og selektorer, lett å lese og endre |
| **Layout** | Innholdet ligger stort sett nedover | Flexbox brukt til meny og minst én rad | Layouten er bevisst designet, og flexbox brukt der det gir mening |
| **Responsivitet** | Siden er brukbar på PC, men ikke på mobil | Siden fungerer på mobil, med minst én media query | Siden er gjennomarbeidet på alle bredder, uten problemer noe sted |
| **Innhold** | Lite eller usammenhengende innhold | Nok innhold, og det henger sammen | Rikt innhold med tydelig rød tråd, og god `alt`-tekst overalt |
| **Ryddighet** | Koden er vanskelig å lese | Innrykk og kommentarer stort sett på plass | Koden er så ryddig at andre kan jobbe videre i den |

> **💡 Tips:** Legg merke til at ingen av radene handler om hvor *pen* siden er. Et gjennomført enkelt design med to farger slår et rotete design med ti.

---

## Innlevering

Lever hele mappa `mitt-nettsted` — med alle HTML-filene, `stil.css` og `bilder`-mappa.

Legg ved dette arket med sjekklistene avkrysset, og svar kort på de tre spørsmålene:

**1. Hva er du mest fornøyd med i prosjektet ditt?**

....................................................................................................

....................................................................................................

**2. Hva satt du fast på, og hvordan løste du det?**

....................................................................................................

....................................................................................................

**3. Hva ville du gjort annerledes hvis du fikk mer tid?**

....................................................................................................

....................................................................................................

---

*Prosjektark til serien «Nettsider fra bunnen av», hefte 1–9.*
