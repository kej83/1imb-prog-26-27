# Rømningsrommet 🔐

## Hva du skal lage

Du skal lage et lite nettsted der man er «låst inne» og må løse **tre gåter** for å komme seg ut.
Hver gåte har **tre svaralternativer**. Alternativene er lenker:

- Riktig svar → du kommer videre til neste gåte
- Feil svar → du havner på en «feil»-side og må prøve igjen

Klarer du alle tre, kommer du til **seiersskjermen**.

Alt du trenger kan du allerede: overskrifter, avsnitt, lister, bilder, tabeller, `<style>` og lenker.

---

## Filstruktur – les dette først!

**Alle filene skal ligge i samme mappe.** Også bildene.

```
romningsrommet/
├── index.html
├── gate1.html
├── gate2.html
├── gate3.html
├── feil1.html
├── feil2.html
├── feil3.html
├── seier.html
├── dor.jpg
└── pokal.jpg
```

Regler for filnavn:

1. **Ingen mellomrom** i filnavn. Bruk bindestrek: `min-side.html`, ikke `min side.html`.
2. **Ingen æ, ø, å** i filnavn. Skriv `romningsrommet`, ikke `rømningsrommet`.
3. **Bare små bokstaver.** Nettservere skiller på store og små bokstaver.
4. Startsiden skal alltid hete **`index.html`**.

Når alt ligger i samme mappe, blir lenkene enkle:

```html
<a href="gate1.html">Neste</a>
<img src="dor.jpg" alt="En låst dør">
```

Lagrer du et bilde i en undermappe, må du skrive `bilder/dor.jpg` i stedet. Det er lett å rote til – hold alt samlet i én mappe nå.

---

## Sidene du skal lage

| Fil | Hva den inneholder |
|---|---|
| `index.html` | Introduksjon + bilde av en dør + lenke til gåte 1 |
| `gate1.html` | Gåte 1 med tre svaralternativer |
| `gate2.html` | Gåte 2 med tre svaralternativer |
| `gate3.html` | Gåte 3 med tre svaralternativer |
| `feil1.html` | «Feil!»-side som lenker tilbake til `gate1.html` |
| `feil2.html` | «Feil!»-side som lenker tilbake til `gate2.html` |
| `feil3.html` | «Feil!»-side som lenker tilbake til `gate3.html` |
| `seier.html` | Seiersskjerm med bilde og en tabell |

**To bilder skal være med:**

- `dor.jpg` på startsiden
- `pokal.jpg` på seiersskjermen

Finn bildene på nett (f.eks. søk på «locked door» og «trophy» på pexels.com eller pixabay.com), høyreklikk → *Lagre bilde som…* → lagre i **samme mappe** som HTML-filene. Har du dårlig tid, kan du bruke `https://picsum.photos/400/300` som `src` i stedet.

---

## Innhold til hver side

Teksten under kan du kopiere. Jobben din er å velge **riktige HTML-elementer** og få lenkene til å peke rett sted.

### index.html

> **Overskrift (h1):** Rømningsrommet
>
> **Avsnitt:** Døra smalt igjen bak deg. Det er ingen håndtak på innsiden. På veggen henger tre lapper med gåter, og under den siste lappen ligger nøkkelen.
>
> **Bilde:** `dor.jpg` – alt-tekst: «En tung, låst dør»
>
> **Overskrift (h2):** Regler
>
> **Punktliste:**
> - Du må løse tre gåter
> - Svarer du feil, må du prøve gåten på nytt
> - Ingen juks med å åpne filene direkte!
>
> **Lenke:** Start rømningen → `gate1.html`

---

### gate1.html

> **Overskrift (h1):** Gåte 1 av 3
>
> **Avsnitt:** Jeg har byer, men ingen hus. Jeg har fjell, men ingen trær. Jeg har vann, men ingen fisk. Hva er jeg?
>
> **Overskrift (h2):** Velg svar
>
> **Punktliste med lenker:**
> - En skog → `feil1.html`
> - **Et kart** → `gate2.html` ← riktig
> - Et akvarium → `feil1.html`

---

### gate2.html

> **Overskrift (h1):** Gåte 2 av 3
>
> **Avsnitt:** Jo mer du tar av meg, jo større blir jeg. Hva er jeg?
>
> **Overskrift (h2):** Velg svar
>
> **Punktliste med lenker:**
> - En ballong → `feil2.html`
> - En bursdagskake → `feil2.html`
> - **Et hull** → `gate3.html` ← riktig

---

### gate3.html

> **Overskrift (h1):** Gåte 3 av 3
>
> **Avsnitt:** Jeg blir våtere og våtere jo mer jeg tørker. Hva er jeg?
>
> **Overskrift (h2):** Velg svar
>
> **Punktliste med lenker:**
> - **Et håndkle** → `seier.html` ← riktig
> - En solsikke → `feil3.html`
> - En paraply → `feil3.html`

---

### feil1.html, feil2.html og feil3.html

Disse tre er helt korte. Bare bytt tallet og lenka.

> **Overskrift (h1):** Feil svar!
>
> **Avsnitt:** Låsen rikker seg ikke. Et sted i rommet hører du en klokke tikke litt fortere.
>
> **Lenke:** Prøv gåten på nytt → `gate1.html` (i `feil2.html` skal den peke på `gate2.html`, i `feil3.html` på `gate3.html`)

---

### seier.html

> **Overskrift (h1):** Du kom deg ut! 🎉
>
> **Avsnitt:** Nøkkelen lå under den siste lappen. Døra glir opp, og du går ut i sola som en fri person.
>
> **Bilde:** `pokal.jpg` – alt-tekst: «Gullpokal»
>
> **Overskrift (h2):** Rekordlista
>
> **Tabell (3 kolonner, 4 rader):**
>
> | Plass | Navn | Tid |
> |---|---|---|
> | 1 | Nora | 1 min 12 sek |
> | 2 | Jonas | 2 min 05 sek |
> | 3 | Deg? | ? |
>
> **Lenke:** Spill på nytt → `index.html`

Sett farge på tabellen med en `<style>` i `<head>`, slik du gjorde i tabell-oppgaven:

```html
<style>
    table {
        width: 400px;
        background-color: gold;
        border: 1mm solid black;
    }
</style>
```

---

## Sjekkliste før du er ferdig

- [ ] Alle 8 HTML-filene og begge bildene ligger i **samme mappe**
- [ ] Ingen mellomrom, æ, ø eller å i filnavnene
- [ ] Hver side har `<!DOCTYPE html>`, `<html>`, `<head>` med `<title>`, og `<body>`
- [ ] Hver `<title>` beskriver siden (f.eks. «Gåte 1»)
- [ ] Begge bildene har fornuftig `alt`-tekst
- [ ] Alle lenkene virker – klikk deg gjennom **alle** stiene, også de feile
- [ ] Du kommer deg fra `index.html` helt fram til `seier.html`

---

## Ferdig? Prøv disse utvidelsene

1. **Skjul fasiten.** En smarting kan gjette at riktig svar peker på `gate2.html`. Døp filene om til noe nøytralt, som `rom-a.html`, `rom-b.html`, `rom-c.html`.
2. **Bilde som lenke.** Gjør svaralternativene til bilder man klikker på i stedet for tekst.
3. **Flere gåter.** Legg til gåte 4 og 5 – da må du lage `gate4.html` og `feil4.html` også.
4. **Kart over rommet.** Lag en side `kart.html` med en tabell som forestiller rutenettet i rommet, og lenk til den fra alle gåtesidene.
5. **Lag dine egne gåter** og bytt rømningsrom med en annen elev.