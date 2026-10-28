# Quiz: JavaScript 1 – Hent, regn, vis

Navn: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ Klasse: \_\_\_\_\_\_\_ Dato: \_\_\_\_\_\_\_\_\_\_

> **Slik gjør du:** Det er 25 spørsmål. Hvert spørsmål har fem svaralternativer, men bare **ett** er riktig. Kryss av for svaret du tror er riktig.

### 1. Hva er `id="inpAlder"` på input-feltet til?

- [ ] **A)** Det bestemmer hvor bredt input-feltet blir.
- [ ] **B)** Det gjør at feltet bare tar imot tall.
- [ ] **C)** Det er navnet JavaScript bruker for å finne input-feltet.
- [ ] **D)** Det er teksten som står i feltet før brukeren skriver noe.
- [ ] **E)** Det kobler knappen til funksjonen `regnUt`.

### 2. Du har skrevet HTML-en fra steg 2, men ingen `<script>` ennå. Hva skjer når du trykker på knappen?

- [ ] **A)** Ingenting skjer på siden, fordi funksjonen `regnUt` ikke finnes ennå.
- [ ] **B)** Det står «Knappen virker!» på siden.
- [ ] **C)** Siden lastes på nytt og input-feltet blir tømt.
- [ ] **D)** Alderen blir regnet ut automatisk.
- [ ] **E)** Nettleseren lukker fanen.

### 3. Hvorfor lar vi funksjonen først bare skrive «Knappen virker!»?

- [ ] **A)** Fordi en funksjon må inneholde en melding for å kunne kjøre.
- [ ] **B)** Fordi nettleseren krever at den første versjonen av en funksjon er en test.
- [ ] **C)** For at brukeren skal vite at siden er ferdig lastet.
- [ ] **D)** Fordi `textContent` bare virker med tekst, ikke med tall.
- [ ] **E)** For å sjekke at knappen, funksjonen og `txtUt` henger sammen før vi gjør mer.

### 4. Knappen har `onclick="regnUt()"`, men funksjonen er skrevet `function regnut()`. Hva skjer?

- [ ] **A)** Det virker, fordi navnene er nesten like.
- [ ] **B)** Det virker ikke, fordi datamaskinen skiller mellom store og små bokstaver.
- [ ] **C)** Det virker, men bare første gang du trykker.
- [ ] **D)** Nettleseren retter navnet til `regnUt` automatisk.
- [ ] **E)** Det virker hvis du fjerner `()` i `onclick`.

### 5. Hva er `inpAlder.value`?

- [ ] **A)** Det brukeren har skrevet i input-feltet – alltid som et tall.
- [ ] **B)** Id-en til input-feltet.
- [ ] **C)** Hvor mange tegn brukeren har skrevet.
- [ ] **D)** Det brukeren har skrevet i input-feltet – alltid som tekst.
- [ ] **E)** Et tall som nettleseren velger tilfeldig.

### 6. Hva gjør `Number(inpAlder.value)`?

- [ ] **A)** Teller hvor mange tall som står i feltet.
- [ ] **B)** Gjør teksten fra input-feltet om til et tall, så vi kan regne med det.
- [ ] **C)** Gir input-feltet et nummer, for eksempel 1, 2 eller 3.
- [ ] **D)** Sjekker om brukeren har skrevet noe i feltet.
- [ ] **E)** Runder av tallet til nærmeste hele tall.

### 7. Se på koden. Brukeren skriver `14` og trykker på knappen. Hva står på siden?

```javascript
let alder = inpAlder.value;
txtUt.textContent = `Neste år blir du ${alder + 1}`;
```

- [ ] **A)** Neste år blir du 15
- [ ] **B)** Neste år blir du 14
- [ ] **C)** Neste år blir du ${alder + 1}
- [ ] **D)** Ingenting – programmet stopper med en feil.
- [ ] **E)** Neste år blir du 141

### 8. Hva blir `"3" + "5"` i JavaScript?

- [ ] **A)** `"35"`
- [ ] **B)** `8`
- [ ] **C)** `"8"`
- [ ] **D)** `"3 + 5"`
- [ ] **E)** `15`

### 9. Hvilket tegn bruker vi for å gange i JavaScript?

- [ ] **A)** `x`
- [ ] **B)** `·`
- [ ] **C)** `*`
- [ ] **D)** `%`
- [ ] **E)** `^`

### 10. Brukeren skriver `2`. Hva blir verdien av `timer`?

```javascript
let alder = Number(inpAlder.value);
let dager = alder * 365;
let timer = dager * 24;
```

- [ ] **A)** 730
- [ ] **B)** 8760
- [ ] **C)** 754
- [ ] **D)** 17520
- [ ] **E)** 48

### 11. Hvilken linje viser alderen riktig på siden?

- [ ] **A)** `` txtUt.textContent = `Du er ${alder} år`; ``
- [ ] **B)** `txtUt.textContent = 'Du er ${alder} år';`
- [ ] **C)** `txtUt.textContent = "Du er ${alder} år";`
- [ ] **D)** `` txtUt.textContent = `Du er {alder} år`; ``
- [ ] **E)** `` txtUt.textContent = `Du er $alder år`; ``

### 12. Linjene inni funksjonen er nummerert 1–4. Hvilken del av Hent – Regn – Vis er linje 2 og 3?

```javascript
1  let alder = Number(inpAlder.value);
2  let dager = alder * 365;
3  let timer = dager * 24;
4  txtUt.textContent = `Du er ca. ${dager} dager gammel.`;
```

- [ ] **A)** Hent
- [ ] **B)** Vis
- [ ] **C)** Hent og vis
- [ ] **D)** Regn
- [ ] **E)** Ingen av dem – de gjør ingenting

### 13. Du bytter ut `txtUt.textContent = ...` med `document.write(...)` inni funksjonen og trykker på knappen. Hva skjer?

- [ ] **A)** Teksten havner i `txtUt` akkurat som før.
- [ ] **B)** Teksten legges til nederst, og resten av siden blir stående.
- [ ] **C)** Hele siden blir slettet – bare teksten står igjen.
- [ ] **D)** Ingenting skjer, fordi `document.write` ikke finnes.
- [ ] **E)** Teksten vises i et eget popup-vindu.

### 14. Brukeren trykker på knappen mens input-feltet er tomt. Hva blir `Number(inpAlder.value)`?

- [ ] **A)** `1`
- [ ] **B)** Tom tekst `""`
- [ ] **C)** `-1`
- [ ] **D)** En feilmelding som stopper programmet
- [ ] **E)** `0`

### 15. Hva er forskjellen på `=` og `==`?

- [ ] **A)** `=` sjekker om to ting er like. `==` gir en variabel en verdi.
- [ ] **B)** `=` gir en variabel en verdi. `==` sjekker om to ting er like.
- [ ] **C)** Det er ingen forskjell, begge kan brukes om hverandre.
- [ ] **D)** `==` brukes bare for tekst, `=` bare for tall.
- [ ] **E)** `==` betyr «ikke lik».

### 16. Når kjører koden inni `else { }`?

- [ ] **A)** Alltid, rett etter `if`-delen.
- [ ] **B)** Når sjekken i `if` stemmer.
- [ ] **C)** Bare første gang funksjonen kjører.
- [ ] **D)** Når det er en skrivefeil i koden.
- [ ] **E)** Når sjekken i `if` ikke stemmer.

### 17. Hva betyr `alder <= 0`?

- [ ] **A)** alder er større enn eller lik 0
- [ ] **B)** alder er mindre enn eller lik 0
- [ ] **C)** alder er mindre enn 0, men ikke 0
- [ ] **D)** alder er ikke lik 0
- [ ] **E)** alder får verdien 0

### 18. Sjekken er `if (alder == 0)`. Brukeren skriver `-5`. Hva skjer?

- [ ] **A)** Det står «Du må skrive inn alderen din først!».
- [ ] **B)** −5 blir gjort om til 5, og programmet regner ut 1825 dager.
- [ ] **C)** `Number` gjør −5 om til 0.
- [ ] **D)** Programmet regner ut −1825 dager, fordi −5 ikke er lik 0.
- [ ] **E)** Programmet stopper med en rød feilmelding.

### 19. Du legger til `<input type="text" id="inpNavn">`. Trenger du `Number( ... )` rundt `inpNavn.value`?

- [ ] **A)** Nei – navnet er tekst, og vi skal ikke regne med det.
- [ ] **B)** Ja – alt fra input-felt må alltid ha `Number`.
- [ ] **C)** Ja – ellers vises ikke navnet på siden.
- [ ] **D)** Nei – felt med `type="text"` gir tall automatisk.
- [ ] **E)** Ja – fordi navnet skal stå inni `${ }`.

### 20. Koden virker ikke. Hvor finner du en rød feilmelding som forteller hvilken linje feilen er på?

- [ ] **A)** Høyreklikk på siden og velg «Lagre som».
- [ ] **B)** I tittelen på fanen øverst i nettleseren.
- [ ] **C)** Trykk F12 og velg fanen Console.
- [ ] **D)** Nederst på selve nettsiden.
- [ ] **E)** Trykk Ctrl + S i editoren.

### 21. Kinokveld: En billett koster 130 kr og et popcorn 70 kr. Hva koster 2 billetter og 2 popcorn til sammen?

- [ ] **A)** 200 kr
- [ ] **B)** 260 kr
- [ ] **C)** 530 kr
- [ ] **D)** 400 kr
- [ ] **E)** 140 kr

### 22. Hvorfor er det lurt å lagre prisene i variabler, for eksempel `let billettpris = 130;`?

- [ ] **A)** JavaScript kan ikke regne med tall som står direkte i koden.
- [ ] **B)** Ellers fungerer ikke `Number( ... )`.
- [ ] **C)** Da er det lett å endre prisen senere.
- [ ] **D)** Ellers vises prisen i input-feltet.
- [ ] **E)** Variabler gjør at programmet går raskere.

### 23. Sparegrisen: Hvor skal `let saldo = 0;` stå?

- [ ] **A)** Utenfor funksjonene, så verdien blir husket mellom hvert trykk.
- [ ] **B)** Inni `leggI()`, så den starter på 0 hver gang.
- [ ] **C)** Inni både `leggI()` og `taUt()`.
- [ ] **D)** I HTML-en, som en id.
- [ ] **E)** Inni `if`-sjekken.

### 24. Når stemmer sjekken `if (belop > saldo)`?

- [ ] **A)** Når det er mer i sparegrisen enn brukeren vil ta ut.
- [ ] **B)** Når brukeren prøver å ta ut mer enn det som er i sparegrisen.
- [ ] **C)** Når sparegrisen er tom.
- [ ] **D)** Når brukeren har skrevet 0.
- [ ] **E)** Hver gang brukeren legger penger i grisen.

### 25. Saldoen starter på 0. Brukeren gjør dette i rekkefølge: Legg i 100 → Legg i 250 → Ta ut 50 → Ta ut 500 → Ta ut 300. Hva står på siden til slutt?

- [ ] **A)** Du har ikke nok penger!
- [ ] **B)** Du har −200 kr i sparegrisen.
- [ ] **C)** Du har 300 kr i sparegrisen.
- [ ] **D)** Du har −500 kr i sparegrisen.
- [ ] **E)** Du har 0 kr i sparegrisen.

**Poeng:** \_\_\_\_\_ av 25