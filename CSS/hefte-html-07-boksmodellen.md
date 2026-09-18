# Kapittel 7: Boksmodellen

*HTML og CSS — hefte 7 i serien «Nettsider fra bunnen av». Bygger på hefte 1–6.*

---

Sidene dine har farger og rammer nå, men de ser fortsatt litt trange ut: teksten klistrer seg til kanten, boksene klistrer seg til hverandre, og alt ligger tett i tett. Det som mangler, er **luft**.

Luft i CSS handler om én ting: å forstå at hvert eneste element på siden er en boks, og at boksen har fire lag. Dette kalles **boksmodellen**, og det er sannsynligvis det viktigste enkelttemaet i hele CSS. Når du har den inne, kan du plassere ting der du vil.

> **💡 Tips:** Lag en ny mappe `nettside7` for dette heftet, med `index.html` og `stil.css`.

---

## 7.1 Alt er bokser

```html
<body>
  <h1>Boksjakt</h1>
  <p>Dette avsnittet er en boks.</p>
  <p>Dette er en annen boks.</p>
  <ul>
    <li>Også en boks</li>
    <li>Og enda en</li>
  </ul>
</body>
```

```css
* {
  border: 1px solid red;
}
```

Før du kan styre boksene, må du se dem. Stjernen `*` er en selektor som treffer **alle** elementer på siden — den er ikke noe du bruker i vanlig arbeid, men den er et glimrende feilsøkingstriks.

1. Skriv av koden, og se på resultatet. Hvor mange bokser er det på siden?
2. Se nøye etter: `<body>` er også en boks. Det samme er `<ul>`, og hver enkelt `<li>` inni den.
3. Legg til en `<section>` med en overskrift og et avsnitt. Hvor mange nye rammer dukker opp?

Der ser du hele prinsippet: **hvert element er en rektangulær boks**, og bokser ligger inni andre bokser. Overskrifter, avsnitt, listepunkter, bilder, seksjoner — alt sammen.

4. Fjern `*`-regelen igjen. Vi skal jobbe med én boks om gangen fra nå av.

> **💡 Tips:** Husk `* { border: 1px solid red; }` — det er det raskeste trikset som finnes når du lurer på hvorfor noe havner et rart sted på siden. Legg den inn, se hvor boksene faktisk ligger, og slett den etterpå.

---

## 7.2 Padding: luft inni boksen

```html
<p class="faktaboks">Turgruppa ble startet i 2024.</p>
```

```css
.faktaboks {
  background-color: #eaf2f8;
  border: 2px solid #1a5276;
  padding: 20px;
}
```

1. Skriv av koden, men **uten** `padding`-linja først. Se hvor tett teksten ligger inntil rammen.
2. Legg til `padding: 20px;`, og se på forskjellen.

`padding` er luften **mellom innholdet og rammen** — inni boksen. Legg merke til at bakgrunnsfargen følger med ut i paddingen: den hører til boksen, ikke bare til teksten.

3. Prøv `5px`, `40px` og `0`. Finn en verdi du synes ser bra ut.
4. Du kan også gi padding til bare én side:

```css
.faktaboks {
  padding-left: 40px;
}
```

Prøv `padding-left`, `padding-top`, `padding-right` og `padding-bottom` hver for seg, og se hvilken side som endrer seg.

5. Gi alle `<th>`- og `<td>`-cellene i en tabell `padding: 8px`. Sammenlign med hvordan tabellen så ut før — dette er det enkleste grepet som finnes for å gjøre en tabell lesbar.

---

## 7.3 Margin: luft utenfor boksen

```css
.faktaboks {
  background-color: #eaf2f8;
  border: 2px solid #1a5276;
  padding: 20px;
  margin: 30px;
}
```

1. Legg til `margin: 30px;` på faktaboksen, og se hva som skjer.
2. Lag en faktaboks til, rett under den første. Se på avstanden mellom dem.

`margin` er luften **utenfor** boksen — avstanden til naboene og til kantene rundt. Sammenlign de to:

| | Hvor | Bakgrunnsfargen? |
|---|---|---|
| `padding` | Inni boksen, mellom innhold og ramme | Følger med |
| `margin` | Utenfor boksen, mellom ramme og naboer | Følger **ikke** med |

3. Sett `background-color: yellow` midlertidig på boksen, og prøv å øke først `padding` og så `margin`. Nå ser du forskjellen helt tydelig: paddingen blir gul, marginen forblir hvit.
4. Akkurat som padding kan margin settes på én side: prøv `margin-bottom: 50px` på den første boksen.
5. Fjern `margin` fra `<h1>` med `margin: 0;`. Ser du at overskriften hadde luft rundt seg hele tiden, uten at du hadde skrevet noe?

Det siste er verdt å merke seg: nettleseren gir mange elementer margin og padding av seg selv. Overskrifter, avsnitt og lister har luft rundt seg fra starten. Når du setter dine egne verdier, overstyrer du nettleserens.

> **⚠️ Merk:** Det er lett å blande `padding` og `margin`. Huskeregel: **padding er polstringen inni jakka, margin er avstanden til personen ved siden av deg.**

---

## 7.4 Boksmodellen samlet

Nå kan vi sette det hele sammen. Hver boks har fire lag, fra innerst til ytterst:

```text
    ┌─────────────────────────────────────────┐
    │  MARGIN  (luft utenfor, gjennomsiktig)  │
    │   ┌─────────────────────────────────┐   │
    │   │  BORDER  (rammen)               │   │
    │   │   ┌─────────────────────────┐   │   │
    │   │   │  PADDING  (luft inni)   │   │   │
    │   │   │   ┌─────────────────┐   │   │   │
    │   │   │   │   INNHOLD       │   │   │   │
    │   │   │   │   tekst, bilde  │   │   │   │
    │   │   │   └─────────────────┘   │   │   │
    │   │   └─────────────────────────┘   │   │
    │   └─────────────────────────────────┘   │
    └─────────────────────────────────────────┘
```

| Lag | Egenskap | Hva det er |
|---|---|---|
| Innhold | `width`, `height` | Teksten eller bildet selv |
| Padding | `padding` | Luft mellom innhold og ramme |
| Ramme | `border` | Streken rundt boksen |
| Margin | `margin` | Luft mellom boksen og naboene |

1. Lag en boks med alle fire: en bakgrunnsfarge, `padding: 20px`, `border: 5px solid navy` og `margin: 40px`.
2. Endre én verdi om gangen, og se nøyaktig hva som skjer med boksen og med naboene rundt.
3. Sett `margin: 0` og se hvordan boksene legger seg helt inntil hverandre.

> **💡 Tips:** Du kan se boksmodellen for et hvilket som helst element på en ekte nettside: høyreklikk på siden i nettleseren og velg **Inspiser** (*Inspect*). Der ligger en fargelagt figur som viser nøyaktig samme fire lag. Prøv det på forsiden til NRK.

---

## 7.5 Bredde — og en overraskelse

```css
.kort {
  width: 300px;
  padding: 20px;
  border: 5px solid navy;
  background-color: #eaf2f8;
}
```

1. Skriv av koden, og legg den på en `<div class="kort">` med litt tekst i.
2. Hvor bred tror du boksen blir på skjermen? Skriv ned gjetningen.
3. Bruk **Inspiser** i nettleseren, eller legg to slike bokser ved siden av hverandre og mål med øyet.

Boksen blir **350 piksler** bred, ikke 300:

```text
  20px   5px            300px             5px   20px
padding border        innhold           border padding
  └──────────────── 350 piksler totalt ──────────────┘
```

Grunnen er at `width` bare gjelder **innholdet**. Padding og ramme legges utenpå. Dette overrasker alle som lærer CSS, og det er kilden til utrolig mange rare layouter.

4. Legg til `padding: 50px` i stedet for 20. Hvor bred er boksen nå? Regn ut før du sjekker.
5. Sett `width: 100%` på boksen, behold paddingen, og se hva som skjer. Nå stikker boksen ut over kanten av siden — fordi 100 % pluss padding pluss ramme er *mer* enn det er plass til.

---

## 7.6 `box-sizing: border-box`

```css
.kort {
  box-sizing: border-box;
  width: 300px;
  padding: 20px;
  border: 5px solid navy;
}
```

Heldigvis finnes det en bryter som gjør at `width` betyr det du trodde det betydde.

1. Legg til `box-sizing: border-box;` i regelen, og mål boksen på nytt.

Nå er boksen nøyaktig **300 piksler** bred totalt — padding og ramme regnes inn i tallet, og innholdet får den plassen som blir til overs. Det er slik de fleste mennesker tenker om bredde.

2. Gå tilbake til boksen med `width: 100%` fra forrige delkapittel, og legg til `box-sizing: border-box`. Problemet forsvinner.

Fordi dette er så mye mer praktisk, setter profesjonelle utviklere det på **alt** — helt øverst i stilfila, én gang for hele nettstedet:

```css
* {
  box-sizing: border-box;
}
```

3. Legg denne regelen øverst i `stil.css`, og fjern `box-sizing` fra de enkelte reglene dine. Sjekk at alt fortsatt ser riktig ut.

Fra nå av begynner alle stilfilene dine med den regelen. Du kommer ikke til å tenke på den igjen — den bare gjør at ting oppfører seg fornuftig.

> **💡 Tips:** Husker du `*`-selektoren fra 7.1? Her er den nyttig på ordentlig. Dette er faktisk det eneste stedet de fleste utviklere bruker den.

---

## 7.7 Kortformer og runde hjørner

```css
.kort {
  margin: 20px 40px;
  padding: 10px 20px 30px 40px;
  border-radius: 12px;
}
```

Du har skrevet `padding: 20px` med én verdi, som gir like mye luft på alle fire sider. Men du kan gi flere verdier:

| Skrivemåte | Betyr |
|---|---|
| `margin: 20px;` | 20 px på alle fire sider |
| `margin: 20px 40px;` | 20 px opp og ned, 40 px til sidene |
| `margin: 10px 20px 30px 40px;` | Opp, høyre, ned, venstre — med klokka fra toppen |

1. Prøv alle tre skrivemåtene på en boks, og se nøye på hvilke sider som endrer seg.
2. Den vanligste i praksis er den med to verdier. Sett `padding: 15px 25px` på faktaboksen din — litt mindre luft opp og ned enn til sidene ser som regel best ut.

Fra hefte 6 kjenner du `border-radius` på bilder. Den virker på alle bokser:

3. Legg til `border-radius: 12px` på en boks med bakgrunnsfarge og ramme. Prøv også `0`, `4px` og `30px`.
4. Sett `border-radius: 50%` på en firkantet boks med lik `width` og `height`. Hva får du?

> **💡 Tips:** Fireverdiskrivemåten går med klokka fra toppen: **opp, høyre, ned, venstre**. Mange husker den som «TRBL» — *top, right, bottom, left*.

---

## 7.8 Sett det sammen: et kort

```html
<section class="kort">
  <h2>Onsdagsturene</h2>
  <p>Vi sykler 30 km i rolig tempo, og alle kan bli med.</p>
</section>
```

```css
* {
  box-sizing: border-box;
}

.kort {
  width: 400px;
  background-color: #ffffff;
  border: 1px solid #c8c8c8;
  border-radius: 10px;
  padding: 20px 25px;
  margin-bottom: 20px;
}

.kort h2 {
  margin-top: 0;
  color: #1a5276;
}
```

Dette er et **kort** — mønsteret du ser overalt på nett: på nettbutikker, nyhetssider, strømmetjenester.

1. Bygg kortet, og se på resultatet.
2. Legg merke til `.kort h2` — etterkommerselektoren fra hefte 6. Den treffer bare overskrifter som ligger **inni** et kort.
3. Hvorfor `margin-top: 0` på overskriften? Fjern linja, og se selv. Nettleserens egen margin på `<h2>` gir et stygt tomrom øverst i kortet.
4. Lag tre kort med ulikt innhold på samme side. Alle skal bruke den samme klassen.
5. Gi det ene kortet en ekstra klasse `uthevet`, som endrer rammen til `3px solid #1a5276`.

> **🐞 Når noe går galt:** Havner noe på et uventet sted, er det nesten alltid en margin eller padding du ikke visste om — enten din egen, eller en nettleseren har lagt inn selv. Legg inn `* { border: 1px solid red; }` en liten stund, så ser du hvor boksene egentlig er.

---

## Sammendrag

### De fire lagene

```text
margin  →  border  →  padding  →  innhold
(ytterst)                        (innerst)
```

| Egenskap | Hva | Bakgrunnsfargen? |
|---|---|---|
| `padding` | Luft mellom innhold og ramme | Følger med |
| `border` | Rammen | — |
| `margin` | Luft mellom boksen og naboene | Følger ikke med |

Huskeregel: padding er polstringen inni jakka, margin er avstanden til personen ved siden av deg.

### Én side om gangen

```css
.boks {
  padding-top: 10px;
  margin-bottom: 30px;
  border-left: 5px solid navy;
}
```

Alle tre finnes som `-top`, `-right`, `-bottom` og `-left`.

### Kortformer

```css
margin: 20px;                  /* alle fire sider */
margin: 20px 40px;             /* opp/ned, sidene */
margin: 10px 20px 30px 40px;   /* opp, høyre, ned, venstre */
```

### Bredde og `box-sizing`

```css
* {
  box-sizing: border-box;
}
```

Uten `border-box` gjelder `width` bare innholdet, slik at padding og ramme kommer **i tillegg** — en boks med `width: 300px` og `padding: 20px` blir 340 piksler bred, pluss rammen. Med `border-box` betyr `width` hele boksen. Sett regelen øverst i stilfila én gang, og slipp å tenke på det igjen.

### Et kort

```css
.kort {
  width: 400px;
  border: 1px solid #c8c8c8;
  border-radius: 10px;
  padding: 20px 25px;
  margin-bottom: 20px;
}

.kort h2 {
  margin-top: 0;
}
```

### Feilsøkingstrikset

```css
* {
  border: 1px solid red;
}
```

Legg den inn når noe havner feil, se hvor boksene faktisk ligger, og slett den etterpå. **Inspiser** i nettleseren viser det samme, med farger.

---

## Oppgaver

### Del A — Enkle oppgaver

**Oppgave A1**

```css
.boks {
  padding 20px;
  margin: 10px
  border: 2px solid navy;
}
```

Koden inneholder to feil. Finn og rett dem, og prøv regelen på en `<div class="boks">`.

**Oppgave A2**

```text
┌──────────────────────────────────┐
│   padding: 15px 25px;            │
├──────────────────────────────────┤
│ }                                │
├──────────────────────────────────┤
│   border: 2px solid #1a5276;     │
├──────────────────────────────────┤
│ .faktaboks {                     │
├──────────────────────────────────┤
│   margin-bottom: 20px;           │
└──────────────────────────────────┘
```

Sett sammen kodebitene til en gyldig regel. Hvor mye luft får boksen over og under innholdet, og hvor mye til sidene?

**Oppgave A3**

```css
.rute {
  width: 200px;
  padding: 25px;
  border: 5px solid black;
}
```

Regn ut på papir, uten PC: hvor bred blir boksen totalt? Skriv deretter av koden og mål med **Inspiser** i nettleseren. Legg så til `box-sizing: border-box`, og regn ut på nytt.

**Oppgave A4**

```css
.sitatboks {
  background-color: ...;
  border-left: ...;
  padding: ...;
  margin: ...;
}
```

Skriv ferdig regelen slik at et `<blockquote>` får lys grå bakgrunn, en tykk farget strek på venstre side, god luft inni, og tydelig avstand til teksten over og under.

**Oppgave A5**

Lag fila `tabell.html` med en tabell fra hefte 4. Gi alle cellene `padding: 8px`, tabellen `border-collapse: collapse`, og hver celle en tynn grå ramme. Sammenlign med hvordan tabellen så ut før.

> **💡 Tips:** `border-collapse: collapse;` på `<table>` slår sammen de doble strekene mellom cellene til én. Uten den får du dobbel ramme overalt.

**Oppgave A6**

Lag tre bokser under hverandre med hver sin bakgrunnsfarge. Den første skal ha padding men ingen margin, den andre margin men ingen padding, og den tredje begge deler. Skriv en kommentar i CSS-fila der du forklarer forskjellen du ser.

### Del B — Middels

**Oppgave B1**

> **🆕 Nytt stoff:** `box-shadow` legger en skygge under boksen og får den til å «løfte seg» fra siden:
>
> `box-shadow: 0 2px 8px rgba(0, 0, 0, 0.2);`
>
> De fire verdiene er: forskyvning til høyre, forskyvning nedover, hvor uskarp skyggen er, og fargen. `rgba()` er som `rgb()`, men med et fjerde tall for gjennomsiktighet, fra 0 til 1.

Lag tre kort på en side, og gi dem alle en myk skygge. Prøv å endre det tredje tallet fra `8px` til `0` og til `30px`, og se forskjellen. Finn en verdi du synes ser bra ut, og skriv i en kommentar hvorfor du valgte den.

**Oppgave B2**

> **🆕 Nytt stoff:** `margin: 0 auto;` sentrerer en boks vannrett på siden. Verdien `auto` betyr «fordel plassen som er igjen likt på begge sider». Boksen må ha en `width` for at det skal virke.

Lag en side der hele innholdet ligger i en boks som er 800 piksler bred og sentrert på siden. Test ved å gjøre nettleservinduet bredere og smalere.

**Oppgave B3**

Bygg et «produktkort» for en nettbutikk: et bilde øverst, en `<h3>` med produktnavn, et avsnitt med beskrivelse, og prisen i et avsnitt med egen klasse. Kortet skal ha fast bredde, ramme, avrundede hjørner, padding og skygge. Lag deretter fire slike kort på samme side, med samme klasse.

**Oppgave B4**

```css
.knapp {
  background-color: #1a5276;
  color: white;
  padding: 12px 24px;
  border-radius: 6px;
  text-decoration: none;
}
```

Lag en lenke `<a href="..." class="knapp">Meld deg på</a>`, og legg på regelen. Paddingen ser rar ut — lenken får luft til sidene, men ikke ordentlig over og under.

> **🆕 Nytt stoff:** Årsaken er at `<a>` er et **inline**-element, og inline-elementer tar ikke imot padding oppover og nedover på vanlig måte. Løsningen er én linje: `display: inline-block;`

Legg til den linja, og se hva som skjer. Gi knappen til slutt en `:hover`-regel fra hefte 5 som endrer bakgrunnsfargen. Du får vite mye mer om `display` i hefte 8.

**Oppgave B5**

Åpne et av nettstedene dine fra hefte 5 eller 6. Gi hele nettstedet luft: `box-sizing: border-box` øverst, padding i `header`, `main` og `footer`, margin mellom seksjonene, og padding i alle tabellceller. Ta et skjermbilde eller skriv ut siden før og etter, og sammenlign.

### Del C — Mer krevende

**Oppgave C1**

Lag fila `boksmodell.html` — en side som **forklarer** boksmodellen for en medelev, og som samtidig demonstrerer den. Krav:

- Fire seksjoner: én for innhold, én for padding, én for ramme og én for margin
- Hver seksjon skal inneholde et levende eksempel: en boks der akkurat den egenskapen er satt tydelig, slik at man ser hva den gjør
- En tabell som oppsummerer de fire lagene
- Et eksempel som viser hva `box-sizing: border-box` gjør: to bokser med samme `width` og `padding`, der bare den ene har `border-box`
- Hele siden i et sentrert innholdsområde, maks 800 piksler bredt

**Oppgave C2**

Design en «prisliste» med tre pakker — for eksempel til en treningsstudio, en strømmetjeneste eller en nettbutikk du finner på. Krav:

- Tre kort med samme klasse, ulikt innhold
- Hvert kort: overskrift, pris i stor skrift med egen klasse, en punktliste over hva som inngår, og en knapp laget som i oppgave B4
- Midterste pakke skal skille seg ut med en ekstra klasse: tykkere ramme, tydeligere skygge, og litt mer padding
- `box-sizing: border-box` øverst i fila
- Ingen CSS-regel skal skrives to ganger

**Oppgave C3**

Undersøk selv, og skriv svarene som kommentarer i CSS-fila:

1. Sett `margin-bottom: 40px` på én boks og `margin-top: 40px` på boksen rett under. Hvor stor blir avstanden mellom dem — 40 eller 80 piksler? Mål med **Inspiser**. (Fenomenet heter *margin-kollaps*, og overrasker selv erfarne utviklere.)
2. Kan `padding` ha negativ verdi? Kan `margin`? Prøv `margin-top: -20px` på en boks, og beskriv hva som skjer.
3. Sett `padding: 20px` på et `<span>` og på et `<p>` med samme bakgrunnsfarge. Hvorfor oppfører de seg ulikt? (Du får svaret i hefte 8.)
4. Hva skjer med `width: 300px` hvis vinduet er smalere enn 300 piksler? Prøv å gjøre nettleservinduet veldig smalt. (Dette problemet løser vi i hefte 9.)
5. Fjern `box-sizing: border-box` fra en ferdig side der du har brukt både `width` og `padding` flere steder. Hvor mange steder ble ødelagt?

---

*Hefte 7 av serien «Nettsider fra bunnen av». Neste hefte: Display og layout.*
