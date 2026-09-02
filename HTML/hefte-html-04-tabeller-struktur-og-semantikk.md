# Kapittel 4: Tabeller, struktur og semantikk

*HTML og CSS — hefte 4 i serien «Nettsider fra bunnen av». Bygger på hefte 1–3.*

---

## Slik jobber du med dette heftet

Heftet følger arbeidsmåten **PRIMM**, med stegene **[Predict]** (les koden og forutsi hvordan siden ser ut), **[Run]** (skriv av og se resultatet), **[Investigate]** (gjør små endringer og undersøk), **[Modify]** (utvid siden) og **[Make]** (lag din helt egen side — i oppgavene bakerst). Noen oppgaver i del B og C starter med en boks merket **Nytt stoff**.

### Husk fra hefte 1–3

Ny HTML-fil: `!` + `ENTER` gir malen, sett `lang="no"`. Lagre med `CTRL` + `S`, og se resultatet med **Show Preview** eller **Go Live**. Du kan overskrifter, avsnitt, lister, tabeller, lenker, bilder og medier — og du har hørt setningen «HTML beskriver hva innholdet **er**, ikke hvordan det ser ut» noen ganger nå. I dette heftet blir den setningen for alvor nyttig.

### Dette heftet handler om to ting

**Første halvdel** tar tabellene videre: du lærer å gi tabellen en overskrift, dele den i logiske deler, og slå sammen celler over flere rader og kolonner.

**Andre halvdel** handler om selve sideskjelettet. Til nå har alt innholdet ditt ligget løst i `<body>`. Nå skal du lære å dele siden inn i topp, meny, hoveddel og bunn — med elementer som forteller hva hver del **er**. Det skjelettet kommer du til å gjenbruke på hver eneste side du lager resten av året.

> **💡 Tips:** Lag en ny mappe `nettside4` for dette heftet, og åpne den i VS Code med **File → Open Folder**.

---

## 4.1 Tabellen får en overskrift

```html
<body>
  <table>
    <caption>Resultater fra klubbmesterskapet 2026</caption>
    <tr>
      <th>Plass</th>
      <th>Navn</th>
      <th>Tid</th>
    </tr>
    <tr>
      <td>1</td>
      <td>Amina</td>
      <td>12,4 s</td>
    </tr>
    <tr>
      <td>2</td>
      <td>Jonas</td>
      <td>12,9 s</td>
    </tr>
  </table>
</body>
```

I hefte 2 bygde du tabeller med `<table>`, `<tr>`, `<th>` og `<td>`. Nå skal tabellene bli ordentlige.

Det første en tabell trenger, er en **overskrift som hører til tabellen selv**. Elementet heter `<caption>`, og det skal stå som aller første linje inni `<table>`:

1. Les koden. Hvor havner teksten «Resultater fra klubbmesterskapet 2026»? **[Predict]**
2. Lag fila `resultater.html`, skriv av koden, og se på resultatet. **[Run]**
3. Flytt `<caption>`-linja ned, slik at den står *etter* den første `<tr>`-raden. Lagre, og se hva som skjer. Flytt den tilbake. **[Investigate]**
4. Bytt ut `<caption>` med en vanlig `<h2>` rett over tabellen. Ser siden annerledes ut? **[Investigate]**

Punkt 4 er verdt å tenke over. En `<h2>` over tabellen ser nesten likt ut — men den er en overskrift for *alt* som kommer etter, mens `<caption>` hører til nøyaktig denne tabellen. Bytt tilbake til `<caption>`.

5. Legg til to nye deltakere i tabellen. **[Modify]**

> **⚠️ Merk:** `<caption>` må stå som første element inni `<table>`. Står den et annet sted, flytter nettleseren den vanligvis opp likevel — men koden din er da feil, og det kan slå ut på andre måter senere.

---

## 4.2 Tabellen deles i tre

```html
<table>
  <caption>Salg i skolekiosken</caption>
  <thead>
    <tr>
      <th>Vare</th>
      <th>Antall</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Boller</td>
      <td>45</td>
    </tr>
    <tr>
      <td>Juice</td>
      <td>30</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>Totalt</th>
      <td>75</td>
    </tr>
  </tfoot>
</table>
```

En tabell har som regel tre logiske deler: overskriftsradene øverst, selve dataene i midten, og av og til en oppsummeringsrad nederst. HTML har egne elementer for hver del:

| Element | Navn | Inneholder |
|---|---|---|
| `<thead>` | *table head* | Overskriftsraden(e) |
| `<tbody>` | *table body* | Radene med data |
| `<tfoot>` | *table foot* | Sum- eller oppsummeringsrad |

De pakkes **rundt** radene — `<tr>`-ene ligger altså inni dem.

1. Les koden. Hvordan tror du siden ser ut sammenlignet med tabellen i 4.1? **[Predict]**
2. Lag fila `kiosk.html`, skriv av koden, og se på resultatet. **[Run]**
3. Ble det noen synlig forskjell? Prøv å fjerne `<thead>`, `<tbody>` og `<tfoot>` (behold radene), og sammenlign. **[Investigate]**

Nei — det ser helt likt ut. Så hvorfor bry seg?

Fordi delene gir tabellen **mening**. I hefte 5 og 6 lærer du CSS, og da kan du med én kodelinje gi hele `<thead>` grå bakgrunn, eller gjøre hele `<tfoot>` fet — uten å røre en eneste rad. Uten `<thead>` og `<tfoot>` måtte du merket hver rad for seg. Du bygger altså strukturen nå, og høster gevinsten om to hefter.

4. Angre endringen fra punkt 3, slik at de tre delene er tilbake. **[Modify]**
5. Legg til to nye varer i `<tbody>`, og rett opp totalen i `<tfoot>`. **[Modify]**

> **💡 Tips:** Legg merke til at sumraden bruker `<th>` på ordet «Totalt». En overskriftscelle trenger ikke å stå øverst — den kan også stå først i en rad, som en radoverskrift.

---

## 4.3 Celler som strekker seg: colspan

```html
<table>
  <caption>Åpningstider</caption>
  <tr>
    <th>Dag</th>
    <th>Formiddag</th>
    <th>Ettermiddag</th>
  </tr>
  <tr>
    <td>Mandag</td>
    <td>08-12</td>
    <td>13-17</td>
  </tr>
  <tr>
    <td>Lørdag</td>
    <td colspan="2">Stengt hele dagen</td>
  </tr>
</table>
```

Noen ganger passer ikke innholdet inn i én rute. På lørdag er det stengt hele dagen — da er det meningsløst å dele opp i formiddag og ettermiddag. Med attributtet `colspan` lar vi én celle strekke seg over flere kolonner.

1. Les koden. Hvor mange celler har lørdagsraden? Hvor bred blir den siste cellen? **[Predict]**
2. Lag fila `apningstider.html`, skriv av koden, og se på resultatet. **[Run]**
3. Tell cellene i hver rad, og skriv tallene ned. Hvorfor har lørdagsraden færre celler enn de andre — og likevel like mange kolonner? **[Investigate]**

Her er hele hemmeligheten: en celle med `colspan="2"` **teller som to kolonner**. Lørdagsraden har derfor 1 + 2 = 3 kolonner, akkurat som de andre radene — selv om den bare har to celler i koden.

4. Endre `colspan="2"` til `colspan="3"`, og se hva som skjer med tabellen. Forklar det du ser. Endre tilbake. **[Investigate]**
5. Legg til en rad for søndag, der det også er stengt hele dagen. **[Modify]**

> **⚠️ Merk:** Regelen du alltid må sjekke: **hver rad skal dekke like mange kolonner**. En celle med `colspan="2"` erstatter to celler — du skal altså *ikke* skrive den ekstra cellen i tillegg. Dette er den vanligste tabellfeilen som finnes.

---

## 4.4 Celler som strekker seg nedover: rowspan

```html
<table>
  <caption>Timeplan</caption>
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
    <td>2</td>
    <td>D204</td>
  </tr>
  <tr>
    <td>3</td>
    <td>Norsk</td>
    <td>B103</td>
  </tr>
</table>
```

Programmering er en dobbelttime. I stedet for å skrive «Programmering» to ganger, lar vi cellen strekke seg **nedover** med `rowspan`.

1. Les koden. Hvor mange celler har raden med time 2, og hvorfor akkurat så mange? **[Predict]**
2. Lag fila `timeplan.html`, skriv av koden, og se på resultatet. **[Run]**
3. Legg til `<td>Programmering</td>` i raden for time 2 også, slik at raden får tre celler. Lagre, og se på tabellen. Hva gikk galt? Fjern cellen igjen. **[Investigate]**

Der ser du det: cellen med `rowspan="2"` **spiser** en celle i raden under. Den raden skal derfor ha én celle mindre enn de andre. Skriver du cellen likevel, blir raden for lang, og tabellen skjærer seg.

4. Endre `rowspan="2"` til `rowspan="3"`. Nå spiser cellen to rader nedover. Hva må du gjøre med raden for time 3 for at tabellen skal gå opp? Prøv, og rett opp. **[Investigate]**
5. Angre tilbake til `rowspan="2"`, og utvid timeplanen med time 4 og 5. Minst én av dem skal være en ny dobbelttime. **[Modify]**

> **💡 Tips:** Blir du forvirret, tegn tabellen som et rutenett på papir og kryss av rutene hver celle dekker. Det er slik profesjonelle også løser floker i tabeller.

---

## 4.5 Sideskjelettet: header, main og footer

```html
<body>
  <header>
    <h1>Sykkelklubben Fart</h1>
    <p>Klubben for deg som liker to hjul</p>
  </header>

  <main>
    <h2>Velkommen</h2>
    <p>Vi sykler hver onsdag klokka 18.</p>
  </main>

  <footer>
    <p>Sykkelklubben Fart, Storgata 1</p>
  </footer>
</body>
```

Nå forlater vi tabellene og går løs på selve siden.

Til nå har alt innholdet ditt ligget løst inni `<body>`, som klær kastet på gulvet. En ekte nettside er delt inn i **deler**: en topp med tittel, et hovedinnhold, og en bunn med kontaktinfo. HTML har egne elementer for akkurat disse delene:

| Element | Navn | Inneholder |
|---|---|---|
| `<header>` | topptekst | Sidens tittel og det som hører til toppen |
| `<main>` | hovedinnhold | Det siden faktisk handler om |
| `<footer>` | bunntekst | Kontaktinfo, opphavsrett, det som hører til bunnen |

1. Les koden. Hvordan tror du siden ser ut? **[Predict]**
2. Lag fila `index.html`, skriv av koden, og se på resultatet. **[Run]**
3. Overrasket? Siden ser ut nøyaktig som om elementene ikke var der. Fjern `<header>`, `<main>` og `<footer>` (behold innholdet), og sammenlign. **[Investigate]**

Akkurat som med `<thead>` og `<tfoot>`: ingen synlig forskjell — foreløpig. Elementene lager **struktur**, ikke utseende. Og strukturen er det som gjør at:

- Du i hefte 6 kan skrive én CSS-regel for `footer` og gi hele bunnen en annen farge.
- En skjermleser kan si «hovedinnhold» og hoppe rett dit, forbi menyen.
- En annen utvikler — eller du selv om tre måneder — skjønner koden med én gang.

4. Angre endringen fra punkt 3. **[Modify]**
5. Utvid `<main>` med et nytt avsnitt, og `<footer>` med en `<address>` som inneholder en e-postadresse. **[Modify]**

> **⚠️ Merk:** Det skal være **én** `<main>` per side, og `<h1>` hører hjemme i `<header>`. `<footer>` er stedet for `<address>` — nå fikk kontaktinfoen fra hefte 2 endelig sitt riktige hjem.

---

## 4.6 Menyen flytter inn: nav

```html
<header>
  <h1>Sykkelklubben Fart</h1>
  <nav>
    <ul>
      <li><a href="index.html">Hjem</a></li>
      <li><a href="turer.html">Turer</a></li>
      <li><a href="om-oss.html">Om oss</a></li>
    </ul>
  </nav>
</header>
```

I hefte 3 lagde du en meny som en punktliste med lenker. Den menyen skal nå få sitt eget element: `<nav>` (av *navigation*).

1. Les koden. Endrer `<nav>` noe på hvordan menyen ser ut? **[Predict]**
2. Utvid `index.html` fra 4.5 med menyen inni `<header>`, slik koden viser. Lag også de to andre sidene, `turer.html` og `om-oss.html`, med samme skjelett. **[Run]**
3. Klikk deg rundt mellom sidene med **Go Live**. **[Run]**
4. Flytt hele `<nav>`-elementet ned i `<footer>`. Fungerer menyen fortsatt? **[Investigate]**

Menyen virker begge steder — men den hører logisk hjemme i toppen, så flytt den tilbake. (En bunnmeny finnes også på ekte nettsteder, og da er `<nav>` i `<footer>` helt riktig. Poenget er at *du* velger med vilje.)

5. Legg til en fjerde side i menyen på alle sidene. **[Modify]**

> **💡 Tips:** `<nav>` er ment for de **viktige** lenkesamlingene — hovedmenyen, ikke enhver lenke på siden. En vanlig lenke midt i et avsnitt skal ikke ha `<nav>` rundt seg.

---

## 4.7 Innholdet deles opp: section

```html
<main>
  <section>
    <h2>Onsdagsturene</h2>
    <p>Vi sykler 30 km i rolig tempo.</p>
  </section>

  <section>
    <h2>Bli medlem</h2>
    <p>Medlemskap koster 300 kr i året.</p>
  </section>
</main>
```

Hovedinnholdet på en side består ofte av flere adskilte temaer. Hvert tema kan pakkes inn i en `<section>` — en seksjon.

1. Les koden. Hvor mange seksjoner er det, og hva kjennetegner hver av dem? **[Predict]**
2. Bytt ut innholdet i `<main>` på `index.html` med koden, og se på resultatet. **[Run]**
3. Legg til en tredje seksjon om noe du finner på selv. **[Modify]**

Legg merke til mønsteret: **hver `<section>` starter med sin egen overskrift.** Det er selve kjennetegnet. Har du en bit innhold som ikke fortjener en overskrift, er den sannsynligvis ikke en seksjon — da holder det med et avsnitt.

4. Prøv å lage en `<section>` som bare inneholder ett avsnitt, uten overskrift. Ser du noen forskjell på siden? **[Investigate]**

Nei — og det er nettopp derfor du må tenke selv. Nettleseren protesterer aldri. `<section>` uten overskrift er som en perm uten rygglapp: den finnes, men ingen vet hva som er i den.

---

## 4.8 Alt satt sammen: malen du skal gjenbruke

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Sykkelklubben Fart</title>
</head>
<body>

  <header>
    <h1>Sykkelklubben Fart</h1>
    <nav>
      <ul>
        <li><a href="index.html">Hjem</a></li>
        <li><a href="turer.html">Turer</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section>
      <h2>Onsdagsturene</h2>
      <p>Vi sykler 30 km i rolig tempo.</p>
    </section>
  </main>

  <footer>
    <address>post@sykkelklubbenfart.no</address>
  </footer>

</body>
</html>
```

Dette er sideskjelettet. Fra nå av starter hver nye side du lager, med denne strukturen — og du fyller den med ditt eget innhold.

1. Bygg om alle tre sidene dine fra 4.6 slik at de følger skjelettet nøyaktig. **[Modify]**
2. Sjekk koden din med **Format Document** (høyreklikk i koden). Ligger alle elementene pent innrykket inni hverandre? **[Run]**
3. Se på siden i nettleseren. Den ser nesten lik ut som før — men koden din er nå på et helt annet nivå. **[Run]**

> **🐞 Når noe går galt:** Blir strukturen rotete, er det nesten alltid fordi et element er lukket på feil sted. Bruk **Format Document**: hvis innrykket plutselig hopper langt ut til venstre eller høyre, har du funnet stedet. VS Code viser deg også hvilken åpnetagg som hører til en lukketagg når du klikker på den.

---

## Sammendrag

Dette heftet ga deg to ting: ordentlige tabeller, og et sideskjelett.

### Tabeller

```html
<table>
  <caption>Salg i skolekiosken</caption>
  <thead>
    <tr>
      <th>Vare</th>
      <th>Antall</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Boller</td>
      <td>45</td>
    </tr>
  </tbody>
  <tfoot>
    <tr>
      <th>Totalt</th>
      <td>45</td>
    </tr>
  </tfoot>
</table>
```

| Element / attributt | Betydning |
|---|---|
| `<caption>` | Tabellens egen overskrift. Skal stå først inni `<table>` |
| `<thead>` | Pakker inn overskriftsraden(e) |
| `<tbody>` | Pakker inn radene med data |
| `<tfoot>` | Pakker inn sum- eller oppsummeringsraden |
| `colspan="2"` | Cellen strekker seg over 2 kolonner |
| `rowspan="2"` | Cellen strekker seg over 2 rader |

**Den gyldne regelen:** hver rad skal dekke like mange kolonner. En celle med `colspan="2"` teller som to, og en celle med `rowspan="2"` spiser en celle i raden under — den cellen skal *ikke* skrives.

### Sideskjelettet

```html
<body>
  <header>
    <h1>Sidens tittel</h1>
    <nav>
      <ul>
        <li><a href="index.html">Hjem</a></li>
      </ul>
    </nav>
  </header>

  <main>
    <section>
      <h2>Overskrift for seksjonen</h2>
      <p>Innhold.</p>
    </section>
  </main>

  <footer>
    <address>post@eksempel.no</address>
  </footer>
</body>
```

| Element | Inneholder |
|---|---|
| `<header>` | Sidens topp: `<h1>` og som regel `<nav>` |
| `<nav>` | Hovedmenyen — lenkene til de andre sidene |
| `<main>` | Hovedinnholdet. Bare **én** per side |
| `<section>` | Ett tema i hovedinnholdet. Starter alltid med en overskrift |
| `<footer>` | Sidens bunn: kontaktinfo, `<address>`, opphavsrett |

### Det viktigste å ta med seg

Ingen av elementene i dette heftet endrer hvordan siden ser ut. De endrer hva koden **betyr** — og det er verdt like mye, av tre grunner: CSS blir mye enklere i hefte 5–7, skjermlesere kan navigere siden, og andre utviklere forstår koden din.

---

## Oppgaver

> **💡 Tips:** Lag en ny fil for hver oppgave. Fra og med nå starter du hver side med sideskjelettet fra 4.8 — også når oppgaven ikke sier det uttrykkelig.

### Del A — Enkle oppgaver

**Oppgave A1**

```html
<table>
  <tr>
    <th>Frukt</th>
    <th>Pris</th>
  </tr>
  <caption>Prisliste</caption>
  <tr>
    <td>Eple</td>
  </tr>
</table>
```

Koden inneholder to feil: ett element står på feil sted, og én rad mangler noe. Rett feilene, og gi eplet en pris.

**Oppgave A2**

```text
┌────────────────────────────────────┐
│   </header>                        │
├────────────────────────────────────┤
│ <main>                             │
├────────────────────────────────────┤
│   <h1>Min side</h1>                │
├────────────────────────────────────┤
│ </main>                            │
├────────────────────────────────────┤
│ <header>                           │
├────────────────────────────────────┤
│   <p>Velkommen hit.</p>            │
└────────────────────────────────────┘
```

Sett sammen kodebitene i riktig rekkefølge, slik at siden får en topp med overskrift og et hovedinnhold med et avsnitt. Skriv koden inn mellom `<body>` og `</body>`, og sjekk resultatet.

**Oppgave A3**

```html
<table>
  <tr>
    <th>Navn</th>
    <th>Mandag</th>
    <th>Tirsdag</th>
  </tr>
  <tr>
    <td>Ida</td>
    <td colspan="2">Ferie</td>
  </tr>
  <tr>
    <td rowspan="2">Omar</td>
    <td>Jobb</td>
    <td>Jobb</td>
  </tr>
  <tr>
    <td>Fri</td>
    <td>Fri</td>
  </tr>
</table>
```

Les koden uten å bruke PC. Tegn tabellen på papir, rute for rute. Hvor mange kolonner dekker hver rad? Skriv deretter av koden, og sjekk om tegningen din stemte.

**Oppgave A4**

```html
<body>
  <header>
    ...
  </header>
  <main>
    <section>
      ...
    </section>
  </main>
  <footer>
    ...
  </footer>
</body>
```

Fyll inn skjelettet med innhold om favorittstedet ditt: en `<h1>` i toppen, en seksjon med `<h2>` og minst to avsnitt i hovedinnholdet, og en `<address>` i bunnen.

**Oppgave A5**

Lag fila `karakterer.html` med en tabell over fem valgfrie fag og hvor mange timer de har i uka. Tabellen skal ha `<caption>`, `<thead>` med to overskriftsceller, `<tbody>` med de fem fagene, og `<tfoot>` med totalt antall timer. Legg hele tabellen inni en `<section>` med en `<h2>` over.

**Oppgave A6**

Lag et lite nettsted med **to** sider om en hobby: `index.html` og `utstyr.html`. Begge sidene skal følge sideskjelettet fra 4.8, ha samme meny i `<nav>`, og minst én `<section>` i `<main>`.

### Del B — Middels

**Oppgave B1**

```html
<table>
  <caption>Kinoprogram</caption>
  <tr>
    <th>Tid</th>
    <th>Sal 1</th>
    <th>Sal 2</th>
  </tr>
  <tr>
    <td>18.00</td>
    <td rowspan="2">Actionfilmen</td>
    <td>Komedien</td>
  </tr>
  <tr>
    <td>20.00</td>
    <td>Actionfilmen</td>
    <td>Dramaet</td>
  </tr>
  <tr>
    <td>22.00</td>
    <td colspan="3">Stengt</td>
  </tr>
</table>
```

To av radene dekker feil antall kolonner. Finn dem, forklar hva som er galt i hver av dem, og rett koden. Tell nøye!

**Oppgave B2**

> **🆕 Nytt stoff:** En `<section>` kan inneholde en ny `<section>`. Da lager du underseksjoner — akkurat som et delkapittel kan ha sine egne underkapitler. Overskriftsnivåene skal følge med: `<h2>` i den ytre seksjonen, `<h3>` i den indre.

Lag fila `fagside.html` om programfaget ditt. `<main>` skal inneholde to seksjoner: `Hva vi lærer` og `Slik jobber vi`. Den første seksjonen skal ha to underseksjoner med hver sin `<h3>` — for eksempel `HTML` og `CSS` — og minst ett avsnitt i hver.

**Oppgave B3**

Bygg om et av dine egne nettsteder fra hefte 3 (for eksempel `fotoalbum`) slik at alle sidene følger sideskjelettet fra 4.8: `<header>` med `<h1>` og `<nav>`, `<main>` med minst to `<section>`, og `<footer>` med `<address>`. Skriv en kommentar øverst i fila der du forklarer hva du måtte endre.

**Oppgave B4**

> **🆕 Nytt stoff:** Attributtet `scope` forteller om en overskriftscelle gjelder for en **kolonne** eller en **rad**: `<th scope="col">` står øverst i en kolonne, mens `<th scope="row">` står først i en rad. Skjermlesere bruker dette til å lese opp riktig overskrift til hver celle — uten det kan en tabell bli helt uforståelig for en blind bruker.

Lag fila `naeringsinnhold.html` med en tabell over næringsinnholdet i fire matvarer: kolonnene `Matvare`, `Kalorier` og `Protein`. Bruk `<caption>`, `<thead>` og `<tbody>`, sett `scope="col"` på overskriftscellene øverst, og gjør den første cellen i hver datarad til en `<th scope="row">` med matvarens navn.

**Oppgave B5**

```text
En side om skolebiblioteket.
Toppen: bibliotekets navn og en meny med tre lenker.
Hovedinnholdet: to seksjoner, hver med sin overskrift.
   Den ene seksjonen inneholder en tabell over åpningstider,
   der to av dagene har samme tid og skal slås sammen
   med rowspan.
   Den andre seksjonen inneholder en punktliste over regler.
Bunnen: kontaktinfo.
```

Lag fila `bibliotek.html` etter beskrivelsen ovenfor. Velg selv riktige HTML-elementer for hver del.

### Del C — Mer krevende

**Oppgave C1**

Lag fila `turneringsplan.html` med en kampoppsett-tabell for en turnering. Krav:

- `<caption>`, `<thead>`, `<tbody>` og `<tfoot>`
- Kolonnene `Tid`, `Bane 1`, `Bane 2` og `Dommer`
- Minst fem tidspunkter i `<tbody>`
- Minst én kamp som går over to tidspunkter (`rowspan`)
- Minst én pause som dekker begge banene (`colspan`)
- Én dommer som dømmer tre kamper på rad (`rowspan="3"`)
- En `<tfoot>` med teksten «Alle kamper varer 20 minutter», som dekker hele tabellbredden

Tegn tabellen som et rutenett på papir **først**. Tell kolonner i hver rad før du skriver koden.

**Oppgave C2**

> **🆕 Nytt stoff:** Elementet `<article>` brukes til innhold som gir mening helt for seg selv — en nyhetsartikkel, et blogginnlegg, en anmeldelse. Testen er enkel: kan biten klippes ut og legges på en annen nettside uten å miste mening? Da er det en `<article>`. Handler den derimot bare om *denne* siden, er det en `<section>`.

Lag fila `nyheter.html` — en nyhetsside for skolen. `<main>` skal inneholde tre `<article>`-elementer, hver med egen `<h2>`, et bilde i en `<figure>` med `<figcaption>`, og minst to avsnitt. Under hver artikkel skal det stå en `<footer>` med journalistens navn og dato.

Ja — en `<article>` kan ha sin egen `<footer>`. Det er ikke bare siden som kan ha topp og bunn.

Skriv til slutt en kommentar øverst i fila: Hvorfor er hver nyhetssak en `<article>` og ikke en `<section>`?

**Oppgave C3**

Bygg et komplett nettsted i en ny mappe `klubben` for en klubb eller forening du finner på. Krav:

- Tre sider, alle med det samme sideskjelettet fra 4.8
- Felles meny i `<nav>` på alle sidene
- Forsiden: minst to `<section>`, og et bilde i en `<figure>` med bildetekst
- Side 2: en tabell med `<caption>`, `<thead>`, `<tbody>` og minst én sammenslått celle
- Side 3: minst to `<article>` med hver sin `<h2>` og egen `<footer>`
- Alle sidene: `<address>` i sidens `<footer>`
- Ingen `<h1>` mer enn én gang per side

Sjekk til slutt alle tre filene med **Format Document**.

**Oppgave C4**

Undersøk selv, og skriv svarene som kommentarer i fila `eksperiment4.html`:

1. Lag to `<main>`-elementer på samme side. Ser du noen forskjell? Hvorfor er det likevel feil?
2. Legg en `<table>` inni en `<section>`, og en `<section>` inni en `<td>`. Fungerer begge deler? Hvilken av dem gir mening?
3. Gi en celle både `colspan="2"` og `rowspan="2"` samtidig. Hva skjer med tabellen? Tegn resultatet på papir først.
4. Fjern `<main>` fra en ferdig side, slik at innholdet ligger løst i `<body>`. Siden ser lik ut. Skriv tre setninger om hvem eller hva som likevel merker forskjellen.

---

*Hefte 4 av serien «Nettsider fra bunnen av». Neste hefte: CSS — farger og tekststiler.*
