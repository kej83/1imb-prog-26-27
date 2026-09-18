# Kapittel 9: Responsivt design

*HTML og CSS — hefte 9 i serien «Nettsider fra bunnen av». Bygger på hefte 1–8.*

---

Mer enn halvparten av all surfing på nett skjer på mobil. Sidene du har laget, er testet på en PC-skjerm — og der ser de bra ut. Spørsmålet er hva som skjer når noen åpner dem på en telefon.

En nettside som ser bra ut på alle skjermstørrelser, kalles **responsiv**. I dette heftet lærer du de fire grepene som skal til, og du bruker flexbox fra hefte 8 til å gjøre jobben.

> **💡 Tips:** Lag en ny mappe `nettside9`. Du kommer til å dra mye i vindusbredden i dette heftet — sett nettleseren i eget vindu, ikke maksimert.

---

## 9.1 Finn feilene selv

Vi begynner med å ødelegge noe.

1. Åpne en av sidene dine fra hefte 7 eller 8 med **Go Live**.
2. Ta tak i kanten av nettleservinduet, og dra det så smalt du klarer — omtrent så smalt som en telefon.
3. Skriv ned alt som går galt. Sannsynligvis noe av dette:
   - Bilder stikker ut over kanten
   - Bokser med fast bredde blir bredere enn skjermen
   - Menyen havner oppå seg selv, eller forsvinner ut til høyre
   - Du må dra sidelengs for å se alt
   - Teksten blir så bred at den er vond å lese når vinduet er stort

4. Dra vinduet bredt igjen, og se hvordan alt blir bra. Det er nettopp problemet: siden er laget for **din** skjerm.

### Slik tester du som proffene

Du trenger ikke en telefon for å teste. I nettleseren:

1. Høyreklikk på siden og velg **Inspiser**.
2. Trykk på ikonet som ser ut som en mobil og et nettbrett, oppe til venstre i panelet som åpnes (i Chrome heter det **Toggle device toolbar**).
3. Velg en telefonmodell i nedtrekkslista øverst.

Nå ser du siden i nøyaktig den bredden en telefon har. Bruk dette gjennom hele heftet.

---

## 9.2 Et innholdsområde som tilpasser seg

```css
.innhold {
  max-width: 900px;
  margin: 0 auto;
  padding: 0 20px;
}
```

```html
<div class="innhold">
  <main> ... </main>
</div>
```

Det første grepet løser to problemer på én gang.

1. Lag en side med mye tekst, pakk innholdet i `<div class="innhold">`, og legg på regelen.
2. Gjør vinduet bredt. Teksten sprer seg ikke lenger over hele skjermen — den stopper på 900 piksler og blir stående midt på.
3. Gjør vinduet smalt, smalere enn 900 piksler. Hva skjer nå?

Her er forskjellen på `width` og `max-width`:

| Egenskap | Betyr |
|---|---|
| `width: 900px` | «Vær alltid 900 piksler» — også når skjermen er 400 |
| `max-width: 900px` | «Vær høyst 900 piksler, men krymp om nødvendig» |

`max-width` er altså regelen som *gir etter*. Det er hele hemmeligheten bak responsivt design: verdier som tilpasser seg, i stedet for verdier som står fast.

4. Bytt `max-width` til `width`, dra vinduet smalt, og se forskjellen. Bytt tilbake.
5. Hvorfor `padding: 0 20px`? Fjern den, dra vinduet helt smalt, og se hvordan teksten klistrer seg til kanten.

`margin: 0 auto` kjenner du fra hefte 7: verdien `auto` fordeler plassen som er til overs likt på hver side, og sentrerer boksen.

> **💡 Tips:** 60–80 tegn per linje er det letteste å lese. Derfor setter nesten alle nettsteder en `max-width` på tekstinnholdet sitt — ikke fordi skjermen er for liten, men fordi den er for stor.

---

## 9.3 Prosent i stedet for piksler

```css
.spalte {
  width: 50%;
}
```

En bredde i piksler er et fast tall. En bredde i prosent regnes ut fra **boksen utenpå** — og endrer seg dermed med skjermen.

1. Lag to bokser ved siden av hverandre i en flex-rad, og gi begge `width: 50%`.
2. Dra vinduet smalere og bredere. Boksene beholder forholdet, men endrer størrelse.
3. Endre til `width: 300px` på begge, og dra vinduet smalt igjen. Nå ryker det.

| Verdi | Oppfører seg |
|---|---|
| `300px` | Fast — endrer seg aldri |
| `50%` | Halvparten av boksen utenpå — endrer seg med den |

4. Prøv `width: 70%` og `width: 30%` på de to boksene.

Husker du `flex: 1` fra hefte 8? Det gjør samme nytten, og er ofte enklere: i stedet for å regne ut prosenter, sier du «ta plassen som er igjen».

5. Bytt ut prosentene med `flex: 1` på begge boksene. Sammenlign.

---

## 9.4 Bilder som skalerer

```css
img {
  max-width: 100%;
}
```

Dette er én kodelinje, og den løser det vanligste responsivitetsproblemet som finnes.

1. Legg et stort bilde på en side — for eksempel `https://picsum.photos/1200/600`.
2. Dra vinduet smalt. Bildet stikker ut, og du må dra sidelengs.
3. Legg inn regelen over, og prøv igjen.

Nå krymper bildet når det må, men blir aldri større enn sin egen størrelse. `max-width: 100%` betyr «høyst like bredt som boksen utenpå».

4. Prøv `width: 100%` i stedet. Hva skjer med et *lite* bilde? Bytt tilbake til `max-width`.

`width: 100%` tvinger små bilder til å bli store og uskarpe. `max-width: 100%` lar dem være.

> **💡 Tips:** Skriv `img { max-width: 100%; }` inn i stilfila på hvert eneste nettsted du lager, med en gang. Den koster ingenting og redder deg hver gang.

---

## 9.5 Media queries

```css
.kort {
  width: 300px;
}

@media (max-width: 600px) {
  .kort {
    width: 100%;
  }
}
```

De tre forrige grepene lar siden *strekke* seg. Men noen ganger holder det ikke å strekke — layouten må gjøres **annerledes** på en liten skjerm. Da bruker vi en **media query**.

En media query er en boks rundt CSS-regler, med et vilkår: «hvis skjermen er smalere enn dette, gjelder reglene inni».

```text
@media (max-width: 600px) {     ← hvis skjermen er 600 px eller smalere
  .kort {                        ← gjelder denne regelen
    width: 100%;
  }
}                                ← slutt
```

1. Lag en side med tre kort på 300 piksler i en flex-rad med `flex-wrap`.
2. Legg til media queryen over.
3. Dra vinduet sakte smalere, og følg med. Ved 600 piksler skifter kortene til full bredde.

Bredden der stilen endrer seg, kalles et **brytepunkt**.

4. Endre `600px` til `900px`, og se at skiftet skjer tidligere.
5. Legg til en regel til inni media queryen — for eksempel `body { background-color: #fdf2cc; }`. Nå ser du tydelig når brytepunktet passeres. Fjern den igjen etterpå.

> **⚠️ Merk:** Media queryen skal stå **nederst** i stilfila, etter de vanlige reglene. Husker du fra hefte 5 at den siste regelen vinner når to er like sterke? Står media queryen øverst, blir den overstyrt av reglene under, og ingenting skjer.

6. Flytt media queryen øverst i fila, og bekreft at den slutter å virke. Flytt den tilbake.

---

## 9.6 Menyen på mobil

```css
nav ul {
  display: flex;
  gap: 24px;
  list-style: none;
  padding: 0;
  margin: 0;
}

@media (max-width: 600px) {
  nav ul {
    flex-direction: column;
    gap: 8px;
  }
}
```

Menyen fra hefte 8 ligger bortover. På en smal skjerm er det det verste stedet å ligge.

1. Bygg menyen, og dra vinduet smalt. Se hvordan punktene presses sammen.
2. Legg til media queryen, og prøv igjen.

`flex-direction: column` snur flex-containeren: i stedet for å legge barna bortover, legger den dem nedover. Det er én linje, og menyen blir brukbar på mobil.

3. Prøv også `flex-direction: row-reverse` og `column-reverse` i media queryen, bare for å se hva de gjør. Sett tilbake til `column`.
4. Gjør det samme med toppen din fra hefte 8: inni media queryen, sett `.topp { flex-direction: column; gap: 10px; }` slik at navnet legger seg over menyen i stedet for ved siden av.

### Skjule noe på mobil

```css
@media (max-width: 600px) {
  .ekstra-lenker {
    display: none;
  }
}
```

5. Har menyen din mange punkter, kan noen av dem skjules på mobil. Gi et par mindre viktige punkter en klasse, og skjul dem med `display: none` fra hefte 8 — men bare inni media queryen.

> **⚠️ Merk:** Vær forsiktig med å skjule innhold på mobil. Den som sitter på telefonen, skal ikke få en dårligere side enn den som sitter på PC — de skal få den samme siden, tilpasset. Skjul dekorasjon, aldri innhold noen trenger.

---

## 9.7 Spaltene stables

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

@media (max-width: 800px) {
  .spalter {
    flex-direction: column;
  }

  aside {
    width: 100%;
  }
}
```

To spalter ved siden av hverandre fungerer ikke på en telefon — da blir begge altfor smale.

1. Bygg to-spalteoppsettet fra hefte 8, og legg til media queryen.
2. Dra vinduet smalt. Sidespalten legger seg under hovedinnholdet og tar full bredde.
3. Hvorfor må `aside` få `width: 100%` inni media queryen? Fjern den linja, og se selv.

Legg merke til hvor lite som skal til: hele omleggingen er to regler. Det er fordi layouten allerede er laget med flexbox — og flexbox er bygget for å kunne snus.

4. Prøv `flex-direction: column-reverse` i stedet, slik at sidespalten havner **over** hovedinnholdet. Hvilken rekkefølge gir best mening på en telefon? Bestem deg, og begrunn valget i en kommentar.

---

## 9.8 Viewport-linja

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Denne linja har ligget i malen din siden hefte 1, uten forklaring. Nå er tiden inne.

Uten den later mobilnettlesere som om skjermen er omtrent 980 piksler bred, og krymper hele siden ned så den får plass. Det ble gjort fordi de fleste nettsider på den tiden var laget for PC — men resultatet er en side med mikroskopisk tekst.

Linja sier to ting:

| Del | Betyr |
|---|---|
| `width=device-width` | Bruk skjermens faktiske bredde |
| `initial-scale=1.0` | Ikke zoom inn eller ut i utgangspunktet |

1. Åpne en av de responsive sidene dine, og se på den i mobilvisning i nettleseren.
2. Slett `<meta name="viewport" ...>`-linja fra `<head>`, lagre, og last siden på nytt.

Alt arbeidet ditt forsvant. Media queryen slår ikke inn, fordi telefonen påstår at den er 980 piksler bred.

3. Sett linja tilbake, og last på nytt.

Uten viewport-linja virker ingen media queries på mobil. Den er derfor det aller første kravet til en responsiv side — og heldigvis har du fått den gratis i malen hele tiden.

---

## Sammendrag

### De fire grepene

| Grep | Kode | Løser |
|---|---|---|
| Fleksibelt innholdsområde | `max-width: 900px; margin: 0 auto;` | Teksten blir for bred på store skjermer |
| Fleksible størrelser | `width: 50%` eller `flex: 1` | Faste bredder sprenger smale skjermer |
| Bilder som krymper | `img { max-width: 100%; }` | Bilder stikker ut over kanten |
| Media queries | `@media (max-width: 600px) { ... }` | Layouten må gjøres annerledes, ikke bare mindre |

### `width` eller `max-width`?

```css
.boks { width: 900px; }      /* alltid 900 - sprenger smale skjermer */
.boks { max-width: 900px; }  /* høyst 900 - krymper om nødvendig */
```

### Media query

```css
.kort {
  width: 300px;
}

@media (max-width: 600px) {
  .kort {
    width: 100%;
  }
}
```

Media queryen skal stå **nederst** i stilfila. Bredden der stilen skifter, kalles et brytepunkt.

### Snu flexbox på mobil

```css
@media (max-width: 600px) {
  nav ul {
    flex-direction: column;
  }

  .spalter {
    flex-direction: column;
  }

  aside {
    width: 100%;
  }
}
```

`flex-direction: column` snur en flex-container fra bortover til nedover. Det er hovedgrepet for å gjøre en layout mobilvennlig.

### Viewport

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

Uten denne linja i `<head>` virker ingen media queries på mobil. Den har ligget i malen siden hefte 1.

### Slik tester du

Høyreklikk → **Inspiser** → mobilikonet øverst → velg en telefonmodell.

---

## Oppgaver

### Del A — Enkle oppgaver

**Oppgave A1**

```css
.kort {
  width: 300px;
}

@media (max-width 600px) {
  .kort {
    width: 100%
  }
}
```

Koden inneholder to feil. Finn og rett dem, og bekreft at brytepunktet virker.

**Oppgave A2**

```text
┌──────────────────────────────────┐
│   }                              │
├──────────────────────────────────┤
│ @media (max-width: 600px) {      │
├──────────────────────────────────┤
│ }                                │
├──────────────────────────────────┤
│     flex-direction: column;      │
├──────────────────────────────────┤
│   nav ul {                       │
└──────────────────────────────────┘
```

Sett sammen kodebitene til en gyldig media query. Pass på hvilken krøllparentes som hører til hva.

**Oppgave A3**

```css
.boks {
  max-width: 600px;
  margin: 0 auto;
}
```

Les koden, og svar uten PC: Hvor bred blir boksen når vinduet er 1200 piksler? Når det er 800? Når det er 400? Hvor på siden ligger den i hvert tilfelle?

**Oppgave A4**

```css
img {
  ...: 100%;
}

.innhold {
  ...: 900px;
  margin: ...;
}
```

Skriv ferdig de to reglene som skal ligge i enhver stilfil du lager: bilder som aldri stikker ut, og et sentrert innholdsområde.

**Oppgave A5**

Ta en av sidene dine fra hefte 7, og gjør den responsiv med de tre første grepene — innholdsområde, fleksible bredder og skalerende bilder. Ingen media queries ennå. Test i mobilvisning, og skriv ned hva som fortsatt er galt.

**Oppgave A6**

Legg til en media query på siden fra A5 som gjør menyen loddrett på skjermer smalere enn 600 piksler. Test både i mobilvisning og ved å dra i vindusbredden.

### Del B — Middels

**Oppgave B1**

> **🆕 Nytt stoff:** `max-width` spør «er skjermen smalere enn ...?». Motstykket er `min-width`, som spør «er skjermen **bredere** enn ...?»:
>
> `@media (min-width: 700px) { ... }`
>
> Mange utviklere bygger sidene sine mobil først: den vanlige CSS-en lages for liten skjerm, og `min-width`-spørringer legger til det som trengs på større skjermer.

Lag en kortside to ganger — ett oppsett med `max-width`-spørring, og ett med `min-width`-spørring — som ser helt like ut i nettleseren. Skriv i en kommentar hvilken av de to du synes var lettest å tenke i, og hvorfor.

**Oppgave B2**

> **🆕 Nytt stoff:** Du kan ha flere brytepunkter i samme stilfil:
>
> `@media (max-width: 900px) { ... }`
> `@media (max-width: 600px) { ... }`
>
> De skrives med det bredeste øverst, fordi den siste regelen vinner.

Lag et kortgalleri som viser tre kort i bredden på store skjermer, to på mellomstore og ett på mobil. Bruk to brytepunkter. Test alle tre bredder.

**Oppgave B3**

> **🆕 Nytt stoff:** Når bilder i et galleri har ulik form, blir kortene skjeve. `object-fit: cover` løser det: bildet fyller den plassen du gir det, og det som ikke får plass, beskjæres — uten at bildet strekkes.
>
> `.kortbilde { width: 100%; height: 200px; object-fit: cover; }`

Lag et kortgalleri med seks kort der bildene har helt ulike størrelser (bruk for eksempel `picsum.photos/400/300`, `/300/500` og `/600/200`). Få alle kortene til å se like ut med `object-fit: cover`. Prøv også `object-fit: contain` og `fill`, og beskriv forskjellen i en kommentar.

**Oppgave B4**

Gjør to-spalteoppsettet ditt fra hefte 8 responsivt: spaltene skal stables under hverandre på skjermer smalere enn 800 piksler, og sidespalten skal ta full bredde. Test i mobilvisning.

**Oppgave B5**

Lag fila `tabell-mobil.html` med en bred tabell fra hefte 4. Finn ut hva som skjer med den på en smal skjerm, og prøv minst to løsninger: mindre skriftstørrelse i en media query, og å skjule en mindre viktig kolonne med `display: none`. Skriv en kommentar om hvilken løsning du synes er best, og hvorfor.

### Del C — Mer krevende

**Oppgave C1**

Gjør et helt nettsted responsivt — bruk et av dine egne fra hefte 8, eller bygg et nytt. Krav:

- `img { max-width: 100%; }` og et sentrert innholdsområde med `max-width`
- Meny som blir loddrett under 600 piksler
- Kortgalleri som går fra tre til to til én i bredden
- To spalter som stables under 800 piksler
- Ingen vannrett rulling ved noen skjermbredde — test fra 320 piksler og oppover
- Alle media queries samlet nederst i stilfila, med kommentarer

Test til slutt i mobilvisning på minst tre ulike telefonmodeller i nedtrekkslista.

**Oppgave C2**

Lag fila `responsiv-guide.html` — en side som forklarer responsivt design for en medelev, og som *er* responsiv selv. Siden skal:

- Forklare de fire grepene, ett i hver seksjon
- Vise forskjellen på `width` og `max-width` med to bokser man kan se oppføre seg ulikt
- Ha en tabell over brytepunktene du har valgt, og hva som skjer ved hvert av dem
- Endre en tydelig ting — for eksempel en tekst eller en farge — ved hvert brytepunkt, slik at leseren ser at det skjer noe når de drar i vinduet

**Oppgave C3**

Undersøk selv, og skriv svarene som kommentarer i CSS-fila:

1. Hva er bredden på skjermen til telefonen din? Finn det ut i mobilvisning i nettleseren. Er 600 piksler et fornuftig brytepunkt for den?
2. Skriv `@media (min-width: 600px) and (max-width: 900px) { ... }`. Hva tror du dette betyr? Test med en tydelig bakgrunnsfarge.
3. Sett `width: 100%` på et bilde som bare er 200 piksler bredt, inni en boks på 900. Hvordan ser bildet ut? Hvorfor er `max-width` nesten alltid bedre?
4. Finn et nettsted du bruker ofte. Åpne det i mobilvisning, og dra bredden sakte fra smal til bred. Hvor mange brytepunkter klarer du å oppdage? Skriv ned hva som endrer seg ved hvert av dem.
5. Fjern viewport-linja fra en ferdig responsiv side, og se på den i mobilvisning. Beskriv med egne ord hva telefonen gjør i stedet.

---

*Hefte 9 av serien «Nettsider fra bunnen av». Neste hefte: Prosjekt — ditt eget nettsted.*
