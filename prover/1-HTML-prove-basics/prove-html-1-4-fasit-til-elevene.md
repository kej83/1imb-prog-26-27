# Prøve i HTML — fasit med forklaringer

*Hefte 1–4 i serien «Nettsider fra bunnen av»*

---

Her er hele prøven på nytt, med riktig svar og en kort forklaring under hvert spørsmål. Gå gjennom de spørsmålene du svarte feil på — og les forklaringen selv om du svarte riktig, hvis du var i tvil. Det er de spørsmålene du gjettet på, som er verdt mest å lese nå.

---

**1.** Du har åpnet en mappe i VS Code og laget fila `index.html`. Hvordan får du fram den minimale HTML-malen?

**A** Skriver `html` og trykker `TAB`\
**B** Skriver `!` og trykker `ENTER`\
**C** Velger **File → New HTML Template**\
**D** Skriver `<html>` og trykker `ENTER`

> **Riktig: B.** Utropstegn og `ENTER` er snarveien som gir hele malen. Den er innebygd i VS Code — det finnes ingen meny som heter **New HTML Template**.

**2.** Hvilket element inneholder det som faktisk vises på selve nettsiden?

**A** `<head>`\
**B** `<title>`\
**C** `<body>`\
**D** `<style>`

> **Riktig: C.** `<head>` inneholder informasjon *om* siden, som ikke vises. Alt innholdet ditt skal ligge mellom `<body>` og `</body>`.

**3.** Hva brukes teksten i `<title>` til?

**A** Den blir sidens hovedoverskrift\
**B** Den vises øverst i `<body>`\
**C** Den bestemmer filnavnet\
**D** Den vises i fanen øverst i nettleseren

> **Riktig: D.** Dette er en klassisk blanding: `<title>` er teksten i fanen, mens `<h1>` er overskriften på selve siden. De kan godt ha ulik tekst.

**4.** Hvor mange `<h1>`-elementer bør det være på én nettside?

**A** Ett\
**B** Ingen\
**C** Ett per avsnitt\
**D** Så mange du vil

> **Riktig: A.** `<h1>` er sidens hovedoverskrift, og en side har bare én hovedoverskrift. Delkapitler bruker `<h2>`, og underkapitler `<h3>`.

**5.** Hvilken av disse er en tom tagg — altså en tagg uten lukketagg?

**A** `<p>`\
**B** `<li>`\
**C** `<hr>`\
**D** `<h1>`

> **Riktig: C.** De tomme taggene du har lært, er `<br>`, `<hr>` og `<img>`. Felles for dem: de pakker ikke inn noe innhold, de *setter inn* noe. Derfor trenger de ikke et sted å slutte.

**6.** Hvordan skriver du en kommentar i HTML?

**A** `// kommentar`\
**B** `/* kommentar */`\
**C** `# kommentar`\
**D** `<!-- kommentar -->`

> **Riktig: D.** Pass på: `/* */` er kommentar i **CSS**, ikke i HTML. Hvert språk har sin egen måte.

**7.** Du skriver ett avsnitt over tre linjer i koden, uten noen tagger imellom. Hva skjer på nettsiden?

**A** Teksten blir vist på tre linjer\
**B** Teksten flyter sammen til én sammenhengende tekst\
**C** Nettleseren gir en feilmelding\
**D** Bare den første linja vises

> **Riktig: B.** Nettleseren ignorerer linjeskift og ekstra mellomrom i koden. Skal du ha et nytt avsnitt, lager du en ny `<p>`. Trenger du et linjeskift inne i teksten — for eksempel i et dikt — bruker du `<br>`.

**8.** Du skal lage en handleliste der rekkefølgen ikke betyr noe. Hvilket element bruker du?

**A** `<ul>`\
**B** `<ol>`\
**C** `<li>`\
**D** `<list>`

> **Riktig: A.** `<ul>` når rekkefølgen er likegyldig, `<ol>` når den betyr noe (som trinn i en oppskrift). `<li>` er de enkelte punktene *inni* lista, og `<list>` finnes ikke i HTML.

**9.** Hva betyr `<strong>`?

**A** At teksten skal være fet\
**B** At teksten skal være større\
**C** At teksten er viktig\
**D** At teksten er et sitat

> **Riktig: C.** At teksten *vises* fet, er bare nettleserens standardvalg — og det kan du endre med CSS. `<strong>` sier noe om innholdet: dette er viktig.

**10.** Hvilket element brukes til en overskriftscelle i en tabell?

**A** `<td>`\
**B** `<tr>`\
**C** `<th>`\
**D** `<caption>`

> **Riktig: C.** `<th>` er overskriftscelle (*table header*), `<td>` er vanlig datacelle. En `<th>` kan stå øverst i en kolonne, men også først i en rad.

**11.** Hva lager elementet `<tr>`?

**A** En celle\
**B** En rad\
**C** En kolonne\
**D** En tabelloverskrift

> **Riktig: B.** *Table row*. Tabeller bygges rad for rad — kolonnene oppstår av at hver rad har like mange celler.

**12.** Du skal ha med et kort sitat midt inne i en setning. Hvilket element passer best?

**A** `<blockquote>`\
**B** `<cite>`\
**C** `<em>`\
**D** `<q>`

> **Riktig: D.** `<q>` er korte sitater inne i en setning, og gir anførselstegn helt av seg selv. `<blockquote>` er for lengre sitater som står for seg selv i en egen blokk.

**13.** Du nevner tittelen på en bok i et avsnitt. Hvilket element bruker du på selve tittelen?

**A** `<cite>`\
**B** `<abbr>`\
**C** `<address>`\
**D** `<code>`

> **Riktig: A.** `<cite>` brukes på titler på verk — bøker, filmer, sanger, spill.

**14.** Du vil at tegnet `<` skal vises som tekst på nettsiden. Hvordan skriver du det?

**A** `&lt;`\
**B** `&gt;`\
**C** `\<`\
**D** `&less;`

> **Riktig: A.** `&lt;` er *less than* og gir `<`, mens `&gt;` er *greater than* og gir `>`. Skriver du `<` rett i teksten, tror nettleseren at en tagg begynner — og teksten din forsvinner.

**15.** Hva gjør `title`-attributtet i `<abbr title="HyperText Markup Language">HTML</abbr>`?

**A** Endrer teksten i nettleserfanen\
**B** Viser forklaringen når musepekeren holdes over ordet\
**C** Gjør forkortelsen til en lenke\
**D** Skriver forklaringen ut i parentes på siden

> **Riktig: B.** Merk at attributtet `title` og elementet `<title>` er to helt forskjellige ting, selv om de heter det samme.

**16.** Hvilken lenke til et annet nettsted er riktig skrevet?

**A** `<a href="www.nrk.no">NRK</a>`\
**B** `<a src="https://www.nrk.no">NRK</a>`\
**C** `<a href="https://www.nrk.no">NRK</a>`\
**D** `<a link="https://www.nrk.no">NRK</a>`

> **Riktig: C.** To ting må stemme: attributtet heter `href` (ikke `src` — det hører til bilder), og adressen til et annet nettsted må starte med `https://`. Uten det leter nettleseren etter en fil i din egen mappe.

**17.** Hva mangler i denne kodelinja: `<img src="katt.jpg">`

**A** En lukketagg\
**B** Et `alt`-attributt\
**C** Et `href`-attributt\
**D** Ingenting — linja er riktig

> **Riktig: B.** `<img>` er en tom tagg og skal *ikke* ha lukketagg — men `alt` skal alltid være der. Alt-teksten vises hvis bildet ikke lastes, og leses høyt for den som bruker skjermleser.

**18.** Bildet `katt.jpg` ligger i undermappa `bilder`. HTML-fila ligger rett utenfor mappa. Hva skal `src` være?

**A** `src="katt.jpg"`\
**B** `src="/katt.jpg"`\
**C** `src="https://bilder/katt.jpg"`\
**D** `src="bilder/katt.jpg"`

> **Riktig: D.** Mappenavn, skråstrek, filnavn. Filstien starter alltid der HTML-fila ligger, og `https://` betyr «ute på nettet» — ikke i din egen mappe.

**19.** Hva slags bilde gir adressen `https://picsum.photos/300`?

**A** Et tilfeldig kvadratisk bilde, 300 × 300\
**B** Et tilfeldig bilde, 300 bredt og 200 høyt\
**C** Bilde nummer 300 i en fast liste\
**D** Det samme bildet hver gang, 300 × 300

> **Riktig: A.** Ett tall gir et kvadratisk bilde, to tall gir bredde og høyde (`/600/200`). Vil du ha *samme* bilde hver gang, må du bruke en seed: `/seed/katt/300`.

**20.** Du vil ha en bildetekst under et bilde. Hvilken løsning er riktig?

**A** `<img>` og `<figcaption>` etter hverandre\
**B** `<figcaption>` med `<img>` inni\
**C** `<figure>` med `src` og `alt`\
**D** `<figure>` med `<img>` og `<figcaption>` inni

> **Riktig: D.** `<figure>` er innpakningen som binder bildet og bildeteksten sammen. `src` og `alt` hører til `<img>`, ikke til `<figure>`.

**21.** Du har skrevet `<audio src="lyd/klipp.mp3"></audio>`, men det vises ingen avspiller på siden. Hva mangler?

**A** Attributtet `controls`\
**B** Attributtet `alt`\
**C** En `<figure>` rundt\
**D** Attributtet `width`

> **Riktig: A.** `controls` er et attributt uten verdi — en av/på-bryter. Står ordet der, får avspilleren knapper. Det samme gjelder `<video>`.

**22.** Hva gjør `target="_blank"` i en lenke?

**A** Gjør lenken blank og usynlig\
**B** Fjerner understreken på lenken\
**C** Åpner lenken i samme fane\
**D** Åpner lenken i en ny fane

> **Riktig: D.** Brukes typisk på lenker til *andre* nettsteder, så besøkeren ikke mister siden din. Lenker til dine egne sider åpnes vanligvis i samme fane.

**23.** Hvor i koden skal `<caption>` stå?

**A** Rett over `<table>`\
**B** Som første element inni `<table>`\
**C** Inni `<thead>`\
**D** Nederst i tabellen

> **Riktig: B.** `<caption>` er tabellens *egen* overskrift, og hører derfor hjemme inni tabellen. En `<h2>` over tabellen ser nesten likt ut, men er en overskrift for alt som følger etter.

**24.** Hvilket element pakker inn overskriftsraden i en tabell?

**A** `<thead>`\
**B** `<tbody>`\
**C** `<tfoot>`\
**D** `<caption>`

> **Riktig: A.** De tre delene er `<thead>` (overskriftsrader), `<tbody>` (dataene) og `<tfoot>` (sumrad). Delene endrer ikke utseendet — men de gjør at du senere kan style hele overskriftsraden med én CSS-regel.

**25.** Hva betyr `colspan="2"`?

**A** Cellen strekker seg over to rader\
**B** Tabellen får to kolonner\
**C** Cellen strekker seg over to kolonner\
**D** Cellen deles i to

> **Riktig: C.** Huskeregel: **col**span går bortover (kolonner), **row**span går nedover (rader). Og husk at cellen da *teller* som to kolonner når du sjekker at raden går opp.

**26.** Se på denne tabellen:

```html
<table>
  <tr>
    <th>Time</th>
    <th>Fag</th>
    <th>Rom</th>
  </tr>
  <tr>
    <td>1</td>
    <td rowspan="2">Programmering</td>
    <td>D204</td>
  </tr>
  <tr>
    ...
  </tr>
</table>
```

Hvor mange celler skal den siste raden ha for at tabellen skal gå opp?

**A** 1\
**B** 2\
**C** 3\
**D** 4

> **Riktig: B.** Cellen med `rowspan="2"` «spiser» fag-cellen i raden under. Den raden trenger derfor bare to celler — én for timenummeret og én for rommet. Skriver du tre, blir raden for lang, og tabellen skjærer seg. Dette var prøvens vanskeligste spørsmål.

**27.** Hvor mange `<main>`-elementer skal en nettside ha?

**A** Ingen\
**B** Ett per seksjon\
**C** Så mange du vil\
**D** Ett

> **Riktig: D.** Én side har ett hovedinnhold. Skal du dele hovedinnholdet opp, bruker du flere `<section>` *inni* `<main>`.

**28.** Hovedmenyen med lenker til de andre sidene hører hjemme i:

**A** `<header>` alene, uten noe eget element rundt lenkene\
**B** `<section>`\
**C** `<main>`\
**D** `<nav>`

> **Riktig: D.** Menyen skal ha `<nav>` rundt seg. Selve `<nav>`-elementet ligger som regel inni `<header>` — men det er `<nav>` som forteller at dette er navigasjon.

**29.** Hva kjennetegner en `<section>`?

**A** Den inneholder alltid en tabell\
**B** Den kan bare brukes én gang per side\
**C** Den har sin egen overskrift\
**D** Den gir innholdet en ramme rundt seg

> **Riktig: C.** En seksjon er ett tema i hovedinnholdet, og starter med sin egen overskrift. Har innholdet ikke fortjent en overskrift, er det sannsynligvis ikke en seksjon. Rammer og bakgrunner er CSS — det kommer i hefte 5.

**30.** Du legger `<header>`, `<main>` og `<footer>` rundt innholdet på en side som var ferdig fra før. Hva skjer i nettleseren?

**A** Siden ser helt lik ut som før\
**B** Innholdet blir plassert i tre kolonner\
**C** Toppen og bunnen får grå bakgrunn\
**D** Siden slutter å virke uten CSS

> **Riktig: A.** Semantiske elementer endrer ingenting visuelt. De endrer hva koden **betyr** — og det er verdt like mye: CSS blir mye enklere, skjermlesere kan navigere siden, og andre utviklere forstår koden din.

---

## Tre ting som går igjen

Ser du tilbake på forklaringene, dukker de samme tre poengene opp om og om igjen:

1. **HTML beskriver hva innholdet er, ikke hvordan det ser ut.** Det gjelder `<strong>`, `<q>`, `<cite>`, `<section>` — og hele hefte 4.
2. **At noe ser riktig ut, betyr ikke at det er riktig.** Nettleseren klager nesten aldri. Du må vite hva du gjør.
3. **Tell alltid kolonnene i en tabell.** `colspan` og `rowspan` erstatter celler — de kommer ikke i tillegg.

---

## Forslag til poenggrenser

Grensene er et utgangspunkt, ikke en fasit. Juster etter hvor klassen ligger.

| Poeng | Karakter |
|---|---|
| 27–30 | 6 |
| 23–26 | 5 |
| 18–22 | 4 |
| 13–17 | 3 |
| 9–12 | 2 |
| 0–8 | 1 |

Merk at ren gjetting gir rundt 7–8 poeng på en firevalgsprøve. Grensen for karakteren 2 er derfor satt over gjettenivået.
---

*Prøve i HTML — hefte 1–4, serien «Nettsider fra bunnen av».*
