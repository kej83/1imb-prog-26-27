# Gruppeoppgaver: HTML

*15 samarbeidsoppgaver bygget på hefte 1–3 i serien «Nettsider fra bunnen av».*

---

## Slik jobber dere

Dere er en gruppe på **2 eller 3**. Poenget med disse oppgavene er ikke å bli først ferdig — det er å **snakke sammen** om koden. Dere lærer mer av å forklare enn av å gjette.

**Tre regler:**

1. **Les høyt.** Én i gruppa leser oppgaven høyt for de andre. Bytt på hvem som leser.
2. **Alle skal være enige.** Ingen skriver ned et svar før hele gruppa er enig. Er dere uenige — bra! Da må dere argumentere. Uenighet er der læringen skjer.
3. **Begrunn svaret.** Til hvert svar skal dere kunne si *hvorfor*. «Det bare er sånn» teller ikke.

**Roller (bytt for hver oppgave):**

| Rolle | Oppgave |
|---|---|
| Leseren | Leser oppgaven høyt, holder styr på hva som skal svares |
| Skriveren | Skriver ned gruppas svar |
| Testeren | Sitter ved tastaturet når oppgaven skal prøves på PC |

Er dere to, deler dere på rollene.

**Merking av oppgavene:**

- **[UTEN PC]** — løses med penn og papir. Ikke jukse ved å teste!
- **[MED PC]** — her skal dere skrive kode i VS Code og se resultatet.

---

## Oppgave 1 — Finn feilene [UTEN PC]

*Type: kode med feil*

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Klassens side<title>
</head>
<body>
  <h1>Velkommen til 1IMA</h1>
  <p>Vi er 28 elever som liker å lage nettsider.
  <p>Vi lærer HTML nå.</p>
</body>
```

Koden inneholder **fire** feil. Finn dem alle sammen uten å bruke PC.

> **Snakk sammen:** Hvilken av de fire feilene tror dere er mest alvorlig — altså hvilken ødelegger mest på siden? Bli enige om en rangering fra verst til minst ille, og begrunn førsteplassen.

---

## Oppgave 2 — Hvilken kode er riktig? [UTEN PC]

*Type: flervalg*

Dere skal lage et bilde med bildetekst under. Bare **ett** av alternativene er riktig.

**A**

```html
<img src="katt.jpg" alt="En katt">
<figcaption>Nabokatten Mons.</figcaption>
```

**B**

```html
<figure>
  <img src="katt.jpg" alt="En katt">
  <figcaption>Nabokatten Mons.</figcaption>
</figure>
```

**C**

```html
<figure src="katt.jpg" alt="En katt">
  <figcaption>Nabokatten Mons.</figcaption>
</figure>
```

**D**

```html
<figcaption>
  <img src="katt.jpg" alt="En katt">
  <p>Nabokatten Mons.</p>
</figcaption>
```

Velg riktig alternativ. Forklar deretter for hverandre **hva som er galt** i hvert av de tre andre.

---

## Oppgave 3 — Sett sammen koden [UTEN PC]

*Type: kode-rekkefølge*

```text
┌──────────────────────────────────────────────────┐
│   <li><a href="om-oss.html">Om oss</a></li>      │
├──────────────────────────────────────────────────┤
│ </ul>                                            │
├──────────────────────────────────────────────────┤
│ <h1>Sykkelklubben</h1>                           │
├──────────────────────────────────────────────────┤
│   <li><a href="index.html">Hjem</a></li>         │
├──────────────────────────────────────────────────┤
│ <ul>                                             │
├──────────────────────────────────────────────────┤
│   <li><a href="turer.html">Turer</a></li>        │
└──────────────────────────────────────────────────┘
```

Kodebitene er stokket om. Skriv dem i riktig rekkefølge, slik at siden viser en overskrift og en meny med tre lenker.

> **Snakk sammen:** Menyen skal ligge på alle sidene i nettstedet. Hva må endres i koden når den limes inn på siden `turer.html`? Er det noe som ikke bør være en lenke der?

---

## Oppgave 4 — Hva mangler? [UTEN PC]

*Type: finn det som mangler*

Hver av de fire kodelinjene mangler **én ting** som gjør at den ikke fungerer som den skal:

```html
1.  <a>Trykk her for å komme til NRK</a>
2.  <img src="bilder/hund.jpg">
3.  <audio src="lyd/klipp.mp3"></audio>
4.  <a href="www.vg.no">VG</a>
```

Skriv hver linje ferdig og riktig.

> **Snakk sammen:** Linje 2 og 3 «virker» kanskje på skjermen selv med feilen — men noe er likevel galt. Hvem merker problemet i linje 2? Tenk på hefte 3.

---

## Oppgave 5 — Velg riktig element [UTEN PC]

*Type: koble sammen*

Koble hver innholdsbit til elementet den bør ligge i. Ett element brukes **ikke**.

| Innhold | | Element |
|---|---|---|
| 1. Ingrediensene i en oppskrift, der rekkefølgen ikke betyr noe | | A. `<ol>` |
| 2. Trinnene i en oppskrift | | B. `<blockquote>` |
| 3. Tittelen på en film, nevnt i en setning | | C. `<abbr>` |
| 4. Et langt sitat fra et intervju | | D. `<ul>` |
| 5. E-postadressen til den som eier siden | | E. `<cite>` |
| 6. Forkortelsen NRK, med forklaring | | F. `<address>` |
| | | G. `<code>` |

> **Snakk sammen:** Punkt 1 og 2 handler om samme oppskrift, men skal ha hvert sitt element. Hvorfor?

---

## Oppgave 6 — Hvem har rett? [UTEN PC]

*Type: diskusjon*

Tre elever krangler om koden nedenfor:

```html
<h1>Nyheter</h1>
<h3>Første sak</h3>
<p>Skolen får nytt bibliotek.</p>
```

- **Ida** sier: «`<h3>` er helt greit her. Det ser fint ut, og det er jo mindre enn `<h1>`.»
- **Omar** sier: «Nei, det skal være `<h2>`. Overskriftene handler om struktur, ikke om størrelse.»
- **Nora** sier: «Begge tar feil. Man kan bare bruke `<p>` med fet skrift, så slipper man hele diskusjonen.»

Hvem har rett? Bli enige i gruppa, og skriv ned **to argumenter** som støtter svaret deres.

> **Snakk sammen:** Nora sitt forslag ville sett helt likt ut på skjermen. Finn minst én situasjon der det likevel ville skapt problemer. (Tenk på en person som ikke ser skjermen.)

---

## Oppgave 7 — Forutsi resultatet [UTEN PC]

*Type: predict*

```html
<h1>Turutstyr</h1>
<ol>
  <li>Sekk</li>
  <li>Mat
    <ul>
      <li>Matpakke</li>
      <li>Termos</li>
    </ul>
  </li>
  <li>Kart</li>
</ol>
```

Tegn på papir hvordan siden kommer til å se ut. Vær nøyaktige: Hvilke punkter får tall, og hvilke får kuler? Hvilket tall står foran `Kart`?

> **Snakk sammen:** Bytt `<ol>` mot `<ul>` i hodet. Hva ville endret seg — og hva ville ikke endret seg?

---

## Oppgave 8 — Tabelldetektiven [UTEN PC]

*Type: finn feilen — viderekomment*

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
    <td colspan="2">Stengt hele dagen</td>
    <td>18-20</td>
  </tr>
  <tr>
    <td>Tirsdag</td>
    <td rowspan="2">08-12</td>
    <td>13-17</td>
  </tr>
  <tr>
    <td>Onsdag</td>
    <td>08-12</td>
    <td>13-17</td>
  </tr>
</table>
```

Tabellen skal ha **tre kolonner**. To av radene går ikke opp.

1. Tell hvor mange kolonner hver rad faktisk dekker. Skriv tallene ned.
2. Finn de to radene som er feil, og forklar hva som er galt i hver av dem.
3. Rett koden.

> **Snakk sammen:** En celle med `rowspan="2"` «spiser» en celle i raden under. Hva må dere da huske å gjøre — eller *ikke* gjøre — i den neste raden?

---

## Oppgave 9 — Filsti-utfordringen [UTEN PC]

*Type: velg riktig svar*

Nettstedet har denne mappestrukturen:

```text
klubben/
├── index.html
├── medlemmer.html
└── bilder/
    ├── logo.png
    └── lag.jpg
```

I fila `index.html` skal logoen settes inn. Hvilken kode er riktig?

**A** `<img src="logo.png" alt="Klubbens logo">`

**B** `<img src="bilder/logo.png" alt="Klubbens logo">`

**C** `<img src="klubben/bilder/logo.png" alt="Klubbens logo">`

**D** `<img src="https://bilder/logo.png" alt="Klubbens logo">`

Velg riktig alternativ, og forklar hvorfor de tre andre feiler.

> **Snakk sammen:** Hvordan blir lenken fra `index.html` til `medlemmer.html`? Og hvordan blir lenken tilbake igjen?

---

## Oppgave 10 — Hva gir disse adressene? [MED PC]

*Type: undersøk sammen*

Gjett først, og test etterpå. Skriv ned gjetningen deres **før** dere åpner PC-en.

| Adresse | Vår gjetning | Faktisk resultat |
|---|---|---|
| `https://picsum.photos/300` | | |
| `https://picsum.photos/600/200` | | |
| `https://picsum.photos/seed/hav/300/300` | | |
| `https://picsum.photos/seed/hav/300/300` (lastet på nytt) | | |

Lag en HTML-fil med alle fire bildene, og fyll ut tabellen.

> **Snakk sammen:** Dere skal lage en side der bildet **skal være det samme** hver gang noen besøker siden. Hvilken av adressene bruker dere da, og hvorfor?

---

## Oppgave 11 — Sorter elementene [UTEN PC]

*Type: kategorisering*

Her er tolv elementer:

```text
h2      img     ul      strong    table    br
figure  p       audio   hr        li       video
```

Sorter dem i to kolonner:

| Har både åpne- og lukketagg | Er en tom tagg (ingen lukketagg) |
|---|---|
| | |

> **Snakk sammen:** Er det noe felles ved elementene i høyre kolonne? Prøv å formulere en regel som forklarer hvorfor akkurat *disse* ikke trenger lukketagg. Test regelen deres på `<figcaption>` og `<td>` — holder den?

---

## Oppgave 12 — Rett opp lærerens side [MED PC]

*Type: forbedre kode*

Læreren har hastverk og har skrevet dette:

```html
<h1>Fagdag fredag</h1>
<p><strong>Program</strong></p>
<p>09.00 Oppmøte<br>
10.00 Foredrag<br>
12.00 Lunsj<br>
13.00 Gruppearbeid</p>
<p>Husk å ta med PC!</p>
<h4>Kontakt</h4>
<p>post@skolen-var.no</p>
```

Siden ser helt grei ut i nettleseren, men koden er full av dårlige valg. Skriv den om slik at hvert innhold ligger i det elementet som **passer til innholdet**. Test både før og etter i VS Code.

> **Snakk sammen:** Dere gjorde flere endringer som knapt synes på skjermen. Bli enige om én setning som forklarer hvorfor dere gjorde dem likevel — den setningen er hele poenget med HTML.

---

## Oppgave 13 — Alt-tekst-verkstedet [UTEN PC]

*Type: vurder og forbedre*

Bildet på siden viser tre elever som programmerer sammen foran en PC i klasserommet.

Her er fire forslag til `alt`-tekst:

- **A** `alt="bilde"`
- **B** `alt="IMG_20260826_113045.jpg"`
- **C** `alt="Tre elever samarbeider om koding foran en PC i klasserommet"`
- **D** `alt="Bilde av elever. Klikk her for å se mer om programmering på skolen vår, vi har mange spennende fag og flinke lærere som hjelper deg."`

1. Ranger de fire fra best til dårligst.
2. Skriv én setning om hva som er galt med hver av de tre dårligste.

> **Snakk sammen:** `alt`-teksten leses høyt av skjermlesere for blinde og svaksynte. Les alternativ D høyt for hverandre — i normalt taletempo. Hva er problemet?

---

## Oppgave 14 — Rydd i rotet [UTEN PC]

*Type: planlegging*

En elev har lagret alt i én mappe:

```text
minside/
├── Forside FERDIG (2).html
├── om meg.html
├── DSC00291.JPG
├── bilde av skolen.png
├── opptak fra intervju.mp3
└── Side om hobbyen min.html
```

1. Foreslå en ryddig mappestruktur med bedre filnavn. Tegn den slik som strukturen ovenfor.
2. Skriv ned tre navneregler dere mener elever bør følge.

> **Snakk sammen:** Filen `Forside FERDIG (2).html` skal være forsiden på nettstedet. Hva bør den hete, og hvorfor akkurat det navnet?

---

## Oppgave 15 — Bygg sammen [MED PC]

*Type: lag*

Til slutt skal gruppa bygge en liten side i fellesskap: en **anmeldelse** av en film, en serie, et spill eller et sted. Bruk stafett — bytt på hvem som sitter ved tastaturet etter hvert krav.

Siden skal inneholde:

1. Riktig mal med `lang="no"` og en beskrivende `<title>`
2. Én `<h1>` og minst to `<h2>`-delkapitler
3. Verkets tittel merket med `<cite>` i et avsnitt
4. En punktliste med minst tre ting dere likte
5. En nummerert liste: deres topp 3 øyeblikk
6. En tabell med `<caption>` og minst tre rader med fakta (år, sjanger, hvem som anbefales det til)
7. Et bilde i en `<figure>` med `<figcaption>` — og god `alt`-tekst
8. Et sitat i `<blockquote>` (fra verket, eller en anmeldelse dere finner på)
9. En lenke til mer informasjon, som åpnes i ny fane
10. En `<address>` nederst med gruppas navn

> **Snakk sammen underveis:** Hver gang dere er uenige om hvilket element som skal brukes — stopp, og la begge forklare. Noter ned én uenighet dere hadde, og hva dere landet på.

> **Til slutt:** Bytt side med en annen gruppe. Se på **koden** deres, ikke bare siden. Finn to ting den andre gruppa har gjort bra, og én ting dere ville løst annerledes.

---

*Gruppeoppgaver til serien «Nettsider fra bunnen av», hefte 1–3.*
