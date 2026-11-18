# Løsning og retteveiledning – Prøve: OG og ELLER i JavaScript (A)

Her er hele prøven slik den var. Riktig svar står ved hver oppgave, sammen med en kort forklaring.

## Slik retter du prøven din

1. Rett med en annen farge enn den du skrev prøven med. Ikke endre svarene dine.
2. **Del 1 (oppgave 1–35):** Sammenlign krysset ditt med riktig svar. Sett ✓ ved riktig og ✗ ved feil. Riktig svar gir 1 poeng. Ingen kryss, eller flere kryss på samme oppgave, gir 0 poeng.
3. **Del 2 (oppgave 36–45):** Sammenlign linjen din med løsningen, og gi deg selv poeng:
   - **2 poeng:** Linjen er riktig og ville virket i programmet. Den trenger ikke se helt lik ut som løsningen. Et glemt semikolon gir ikke trekk.
   - **1 poeng:** Riktig idé, men én feil. Ved hver oppgave står det hvilke feil som gir 1 poeng.
   - **0 poeng:** Linjen gjør noe annet enn den skal, eller du har ikke skrevet noe.
   - Er du usikker, setter du et spørsmålstegn og spør læreren.
4. Les forklaringen på alle oppgavene du hadde feil på.
5. Legg sammen poengene, og skriv dem på svararket: Del 1 ___ / 35, Del 2 ___ / 20, Totalt ___ / 55.

**Fasit del 1:** 1B · 2D · 3A · 4A · 5E · 6C · 7A · 8D · 9C · 10A · 11D · 12C · 13E · 14C · 15A · 16D · 17B · 18E · 19A · 20C · 21B · 22C · 23E · 24D · 25B · 26D · 27E · 28A · 29C · 30B · 31D · 32E · 33B · 34E · 35B

---

## Del 1 – Flervalg (1 poeng per oppgave)

### A – Forståelse

**1.** Når er uttrykket `a && b` sant?

- A) Når minst én av a og b er sann
- **B) Når både a og b er sanne** ✅ **Riktig**
- C) Når verken a eller b er sanne
- D) Bare når a er sann
- E) Bare når b er sann

> **Riktig svar: B.** `&&` betyr OG. Hele uttrykket er bare sant når **begge** delene er sanne.

**2.** Når er uttrykket `a || b` **usant**?

- A) Når både a og b er sanne
- B) Når a er sann
- C) Når b er sann
- **D) Når både a og b er usanne** ✅ **Riktig**
- E) Det kan aldri bli usant

> **Riktig svar: D.** `||` betyr ELLER. Det holder at én del er sann. Uttrykket blir derfor bare usant når **begge** delene er usanne.

**3.** Hva blir `alder >= 13 && alder < 16`?

```javascript
let alder = 16;
```

- **A) usant (false)** ✅ **Riktig**
- B) sant (true)
- C) 16
- D) 13
- E) Det gir en feilmelding

> **Riktig svar: A.** 16 >= 13 er sant, men 16 < 16 er usant. Med `&&` må begge være sanne.

**4.** Hva blir `time < 7 || time > 22`?

```javascript
let time = 6;
```

- **A) sant (true)** ✅ **Riktig**
- B) usant (false)
- C) 6
- D) 7
- E) Det gir en feilmelding

> **Riktig svar: A.** 6 < 7 er sant. Med `||` holder det at én del er sann.

**5.** Hva blir `poeng >= 60 && fravaer <= 10`?

```javascript
let poeng = 79;
let fravaer = 12;
```

- A) sant (true)
- B) 79
- C) 12
- D) Det gir en feilmelding
- **E) usant (false)** ✅ **Riktig**

> **Riktig svar: E.** 79 >= 60 er sant, men 12 <= 10 er usant. Med `&&` blir hele uttrykket usant.

**6.** Hva blir `svar == "nei" || svar == "NEI"`?

```javascript
let svar = "Nei";
```

- A) sant (true)
- B) "Nei"
- **C) usant (false)** ✅ **Riktig**
- D) "nei"
- E) Det gir en feilmelding

> **Riktig svar: C.** `"Nei"` med stor N er verken `"nei"` eller `"NEI"`. JavaScript skiller mellom store og små bokstaver.

**7.** Hva blir `dag <= 5 && time >= 8 && ferie == "nei"`?

```javascript
let dag = 3;
let time = 9;
let ferie = "nei";
```

- **A) sant (true)** ✅ **Riktig**
- B) usant (false)
- C) 3
- D) "nei"
- E) Det gir en feilmelding

> **Riktig svar: A.** Alle tre delene er sanne: 3 <= 5, 9 >= 8 og ferie er «nei». Et uttrykk kan ha flere enn to deler.

**8.** Hva blir `alder < 18 || alder >= 67 && medlem == "ja"`?

```javascript
let alder = 10;
let medlem = "nei";
```

- A) usant (false)
- B) 10
- C) "nei"
- **D) sant (true)** ✅ **Riktig**
- E) Det gir en feilmelding

> **Riktig svar: D.** `&&` regnes ut først: `alder >= 67 && medlem == "ja"` er usant. Så blir det `alder < 18 || usant`, og 10 < 18 er sant. Regner du fra venstre mot høyre, får du feil svar.

**9.** Hvor mange av de fem uttrykkene er sanne?

```javascript
let x = 15;

x > 10 && x < 20
x < 10 || x > 20
x >= 15 && x <= 15
x == 10 || x == 20
x > 10 || x > 100
```

- A) 1
- B) 2
- **C) 3** ✅ **Riktig**
- D) 4
- E) 5

> **Riktig svar: C.** Det første, det tredje og det femte er sanne. 15 er verken under 10 eller over 20, og 15 er verken 10 eller 20.

**10.** Hvilket utsagn om `&&` og `||` er riktig?

- **A) `&&` regnes ut før `||` hvis det ikke står parenteser** ✅ **Riktig**
- B) `||` regnes ut før `&&` hvis det ikke står parenteser
- C) De regnes alltid ut fra høyre mot venstre
- D) Parenteser har ingen betydning når vi bruker `&&` og `||`
- E) `&&` og `||` kan ikke stå i samme `if`

> **Riktig svar: A.** `&&` regnes ut før `||`, akkurat som ganging før pluss. Parenteser bestemmer hva som skal regnes ut først.

**11.** Hva kan du si om uttrykket `tall < 0 && tall > 100`?

- A) Det er alltid sant
- B) Det er sant for tall utenfor 0–100
- C) Det er sant for tall mellom 0 og 100
- **D) Det kan aldri bli sant** ✅ **Riktig**
- E) Det gir en feilmelding

> **Riktig svar: D.** Ingen tall er både mindre enn 0 og større enn 100. Skal du finne tall **utenfor** 0–100, bruker du `||`.

**12.** Brukeren skriver 5 i det første feltet og 3 i det andre. Hva står på siden?

```javascript
let a = inpA.value;
let b = inpB.value;
txtSvar.textContent = a + b;
```

- A) 8
- B) 5 + 3
- **C) 53** ✅ **Riktig**
- D) a + b
- E) Det gir en feilmelding

> **Riktig svar: C.** `.value` gir tekst. Tekst + tekst setter tekstene sammen: «5» og «3» blir «53». Med `Number()` hadde svaret blitt 8.

### B – Velg riktig betingelse

**13.** Du får studentrabatt hvis du er student **eller** under 26 år. Hvilken betingelse er riktig?

- A) `student == "ja" && alder < 26`
- B) `student == "ja" || alder <= 26`
- C) `student == "ja" || < 26`
- D) `student || alder < 26`
- **E) `student == "ja" || alder < 26`** ✅ **Riktig**

> **Riktig svar: E.** Det holder med én av grunnene, så vi bruker `||`. «Under 26» er `< 26`, og variabelen må stå i begge delene.

**14.** Skiheisen har barnepris fra og med 7 til og med 15 år. Hvilken betingelse er riktig?

- A) `alder > 7 && alder < 15`
- B) `alder >= 7 || alder <= 15`
- **C) `alder >= 7 && alder <= 15`** ✅ **Riktig**
- D) `alder <= 7 && alder >= 15`
- E) `7 <= alder <= 15`

> **Riktig svar: C.** «Fra og med» og «til og med» gir `>=` og `<=`. Begge grensene må gjelde, så vi bruker `&&`. `7 <= alder <= 15` ser riktig ut, men fungerer ikke i JavaScript.

**15.** Om vinteren er det mørkt før kl. 8 og fra kl. 16. Hvilken betingelse sjekker om det er mørkt?

- **A) `time < 8 || time >= 16`** ✅ **Riktig**
- B) `time < 8 && time >= 16`
- C) `time >= 8 && time < 16`
- D) `time <= 8 || time > 16`
- E) `time > 8 || time <= 16`

> **Riktig svar: A.** Det mørke ligger utenfor intervallet 8–16. Klokka kan ikke være begge deler samtidig, så vi bruker `||`. Kl. 8 er det lyst, og kl. 16 er det mørkt.

**16.** Du får leie bowlingbane hvis du er minst 18 år, **eller** hvis du er minst 13 år **og** har med en voksen. Hvilken betingelse er riktig?

- A) `alder >= 18 && (alder >= 13 || voksen == "ja")`
- B) `(alder >= 18 || alder >= 13) && voksen == "ja"`
- C) `alder >= 13 && voksen == "ja" && alder >= 18`
- **D) `alder >= 18 || (alder >= 13 && voksen == "ja")`** ✅ **Riktig**
- E) `alder >= 18 || alder >= 13 || voksen == "ja"`

> **Riktig svar: D.** Parentesen samler regelen «minst 13 OG voksen». Er du 18 år eller eldre, holder det alene.

**17.** Du får låne PC hvis du er elev, **og** du enten har levert skjema **eller** har med en lærer. Hvilken betingelse er riktig?

- A) `elev == "ja" && skjema == "ja" || laerer == "ja"`
- **B) `elev == "ja" && (skjema == "ja" || laerer == "ja")`** ✅ **Riktig**
- C) `elev == "ja" || skjema == "ja" && laerer == "ja"`
- D) `(elev == "ja" && skjema == "ja") || laerer == "ja"`
- E) `elev == "ja" && skjema == "ja" && laerer == "ja"`

> **Riktig svar: B.** Du må alltid være elev. Parentesen samler de to mulighetene. Uten parentes kan alle som har med en lærer, låne PC – også de som ikke er elever.

**18.** En karakter må være fra 1 til 6. Hvilken betingelse finner en **ugyldig** karakter?

- A) `kar < 1 && kar > 6`
- B) `kar >= 1 && kar <= 6`
- C) `kar <= 1 || kar >= 6`
- D) `kar < 1 || > 6`
- **E) `kar < 1 || kar > 6`** ✅ **Riktig**

> **Riktig svar: E.** Ugyldig betyr under 1 **eller** over 6. Karakterene 1 og 6 er gyldige, så det skal stå `<` og `>`. I D mangler variabelen etter `||`.

**19.** Du må være minst 10 år, og svaret skal godtas om det er skrevet `ja`, `Ja` eller `JA`. Hvilken betingelse er riktig?

- **A) `alder >= 10 && (svar == "ja" || svar == "Ja" || svar == "JA")`** ✅ **Riktig**
- B) `alder >= 10 && svar == "ja" || svar == "Ja" || svar == "JA"`
- C) `alder >= 10 && svar == "ja" || "Ja" || "JA"`
- D) `alder >= 10 && (svar == "ja" && svar == "Ja" && svar == "JA")`
- E) `alder >= 10 || svar == "ja" || svar == "Ja" || svar == "JA"`

> **Riktig svar: A.** Svaret kan være én av tre skrivemåter, så de samles med `||` i en parentes. Uten parentes kommer en 5-åring som skriver «Ja», inn.

### C – Riktig rekkefølge

**20.** Linjene A–F skal stå mellom start og slutt, slik at programmet viser om butikken (kl. 10–20) er åpen. Hvilken rekkefølge er riktig?

```javascript
A   } else {
B   function sjekk() {
C     txtSvar.textContent = "Stengt.";
D     if (time >= 10 && time < 20) {
E     let time = Number(inpTime.value);
F     txtSvar.textContent = "Åpent!";

    // Til slutt står:   }   }
```

- A) B D E F A C
- B) E B D F A C
- **C) B E D F A C** ✅ **Riktig**
- D) B E D C A F
- E) B E D F C A

> **Riktig svar: C.** Funksjonen starter (B). Så hentes tallet (E) før det brukes i `if`-en (D). Teksten for «åpent» (F) står før `else` (A), og «stengt» (C) står etter.

**21.** En `if`-kjede skal gi riktig vurdering **uten** å bruke `&&`: 80 eller mer gir «Meget godt», 60–79 gir «Godt», 40–59 gir «Bestått» og under 40 gir «Ikke bestått». I hvilken rekkefølge må sjekkene stå?

- A) `poeng >= 40`, så `poeng >= 60`, så `poeng >= 80`
- **B) `poeng >= 80`, så `poeng >= 60`, så `poeng >= 40`** ✅ **Riktig**
- C) `poeng >= 60`, så `poeng >= 80`, så `poeng >= 40`
- D) `poeng >= 40`, så `poeng >= 80`, så `poeng >= 60`
- E) `poeng >= 60`, så `poeng >= 40`, så `poeng >= 80`

> **Riktig svar: B.** Bare den første sanne delen kjører. Står `poeng >= 40` først, får alle med 40 eller mer «Bestått». Uten `&&` må vi sjekke den høyeste grensen først.

**22.** I et terningspill gir to seksere 5 poeng, et par 3 poeng og summen 7 gir 1 poeng. Hvilken rekkefølge i `if`-kjeden gir alltid riktig antall poeng?

- A) Par, to seksere, summen 7
- B) Summen 7, par, to seksere
- **C) To seksere, par, summen 7** ✅ **Riktig**
- D) Par, summen 7, to seksere
- E) Rekkefølgen spiller ingen rolle

> **Riktig svar: C.** To seksere er også et par. Står par-sjekken før sjekken for to seksere, gir to seksere bare 3 poeng.

**23.** Hvor må linjen `let antall = 0;` stå, slik at telleren øker for hvert trykk på knappen?

```javascript
function trykk() {
  antall++;
  txtAntall.textContent = `Antall: ${antall}`;
}
```

- A) Øverst inni funksjonen
- B) Rett etter `antall++;`
- C) Nederst inni funksjonen
- D) I HTML-en, inni knappen
- **E) Utenfor funksjonen, over den** ✅ **Riktig**

> **Riktig svar: E.** Står den inni funksjonen, settes `antall` til 0 hver gang du trykker. Utenfor funksjonen husker variabelen verdien mellom hvert trykk.

**24.** Linjene A–F skal stå mellom start og slutt i en innloggingsfunksjon. Hvilken rekkefølge gir et program som virker?

```javascript
    // Start:   function loggInn() {

A     if (bruker == "ola" && passord == "1234") {
B     let passord = inpPassord.value;
C       txtUt.textContent = "Velkommen!";
D     let bruker = inpBruker.value;
E       txtUt.textContent = "Feil brukernavn eller passord.";
F     } else {

    // Slutt:   }   }
```

- A) A D B C F E
- B) D A B C F E
- C) D B A E F C
- **D) D B A C F E** ✅ **Riktig**
- E) D B A C E F

> **Riktig svar: D.** Begge variablene må hentes (D og B) før de brukes i `if`-en (A). «Velkommen» står før `else` (F), og feilmeldingen står etter.

### D – Finn syntaksfeilen

**25.** Hvilken linje har en **syntaksfeil**?

- A) `if (alder >= 13 && alder <= 19) {`
- **B) `if (time < 6 || > 22) {`** ✅ **Riktig**
- C) `if ((a > 1 && b > 1) || c > 1) {`
- D) `let svar = inpSvar.value;`
- E) `txtSvar.textContent = "Hei!";`

> **Riktig svar: B.** Etter `||` mangler variabelen: Det skal stå `time < 6 || time > 22`.

**26.** Hva er feil i koden?

```javascript
function sjekk() {
  let tall = Number(inpTall.value);
  if (tall >= 1 && tall <= 6) {
    txtSvar.textContent = "Gyldig";
  } else (tall > 6) {
    txtSvar.textContent = "Ugyldig";
  }
}
```

- A) `&&` skal være `||`
- B) `Number()` skal fjernes
- C) Det mangler semikolon etter `if`-linjen
- **D) `else` kan ikke ha en betingelse** ✅ **Riktig**
- E) `<=` skal skrives `=<`

> **Riktig svar: D.** `else` tar alt som er igjen og kan ikke ha en betingelse. Skriv `} else {`, eller `} else if (...) {` hvis du trenger en betingelse.

**27.** Hva er feil i linjen `if (hoyde >= 120 && (alder >= 10 || voksen == "ja") {`?

- A) `&&` skal være `||`
- B) `"ja"` skal stå uten anførselstegn
- C) Det skal stå `=` i stedet for `==`
- D) Ingenting er feil
- **E) Det mangler en avsluttende parentes** ✅ **Riktig**

> **Riktig svar: E.** Det er tre parenteser som åpnes, men bare to som lukkes. Det skal stå `...== "ja")) {`.

**28.** Siden har knappen `<button onclick="sjekk">Sjekk</button>`, og funksjonen `sjekk()` finnes. Ingenting skjer når du trykker. Hva er feil?

- **A) Det mangler `()` etter `sjekk`** ✅ **Riktig**
- B) Knappen må ha en `id`
- C) Teksten på knappen må være `sjekk()`
- D) Det skal være `<input>` i stedet for `<button>`
- E) Funksjonen må hete `Sjekk` med stor S

> **Riktig svar: A.** `onclick="sjekk()"` kjører funksjonen. Uten `()` blir funksjonen bare nevnt, men ikke kjørt.

### E – Finn den logiske feilen

**29.** En elev skriver `if (svar = "ja") {`. Det kommer ingen feilmelding. Hva skjer?

- A) `if`-en slår aldri til
- B) `if`-en slår bare til når brukeren skrev ja
- **C) `if`-en slår alltid til** ✅ **Riktig**
- D) Siden lastes på nytt
- E) Variabelen `svar` blir tom

> **Riktig svar: C.** Ett likhetstegn gir `svar` verdien `"ja"` i stedet for å sammenligne. Teksten `"ja"` regnes som sann, så `if`-en slår alltid til. Det skal stå `==`.

**30.** Barnepris skal gjelde under 12 år og fra 67 år. Koden er `if (alder < 12 && alder >= 67)`. Hva skjer?

- A) Alle får barnepris
- **B) Ingen får barnepris** ✅ **Riktig**
- C) Bare 67-åringer får barnepris
- D) Det gir en feilmelding
- E) Det virker som det skal

> **Riktig svar: B.** Ingen er både under 12 og 67 år eller eldre. Det skal stå `||`.

**31.** Butikken åpner kl. 10 og stenger kl. 20. Koden er `if (time > 10 && time <= 20)`. Hvilken test avslører feilen?

- A) Kl. 15 sier «stengt»
- B) Alle klokkeslett sier «åpent»
- C) Kl. 9 sier «åpent»
- **D) Kl. 10 sier «stengt», og kl. 20 sier «åpent»** ✅ **Riktig**
- E) Ingen test – koden er riktig

> **Riktig svar: D.** `time > 10` utelater kl. 10, og `time <= 20` tar med kl. 20. Det skal stå `time >= 10 && time < 20`. Test alltid rett på grensene.

**32.** Fri frakt gis når `sum >= 500 || medlem == "ja"`. Et medlem skriver «Ja» og må betale frakt. Hvilken linje retter feilen?

- A) `if (sum >= 500 || medlem == "ja" || "Ja")`
- B) `if (sum >= 500 && medlem == "ja" || medlem == "Ja")`
- C) `if (sum >= 500 || medlem == ("ja" || "Ja"))`
- D) `if (sum >= 500 || medlem = "Ja")`
- **E) `if (sum >= 500 || medlem == "ja" || medlem == "Ja")`** ✅ **Riktig**

> **Riktig svar: E.** `medlem ==` må stå foran hver skrivemåte. Når alle delene er bundet sammen med `||`, trengs det ingen parenteser.

**33.** Uansett hvor mange ganger du trykker, står det «Stemmer: 1». Hvorfor?

```javascript
function stem() {
  let stemmer = 0;
  stemmer++;
  txtSvar.textContent = `Stemmer: ${stemmer}`;
}
```

- A) `++` virker bare på tall over 0
- **B) `let stemmer = 0;` står inni funksjonen og nullstilles ved hvert trykk** ✅ **Riktig**
- C) `textContent` kan bare vise én ting
- D) `Number()` mangler
- E) Knappen mangler `onclick`

> **Riktig svar: B.** Variabelen lages på nytt med verdien 0 hver gang funksjonen kjører. Flytt `let stemmer = 0;` utenfor funksjonen.

### F – Fullfør programmet

**34.** Spillet er ferdig når du har minst 20 poeng, **eller** når du har kastet 10 ganger. Hva skal stå i den tomme parentesen?

```javascript
function kast() {
  if ( ? ) {
    txtSvar.textContent = "Spillet er ferdig!";
  } else {
    // ... kast terningen ...
  }
}
```

- A) `poeng >= 20 && kast >= 10`
- B) `poeng > 20 || kast > 10`
- C) `poeng >= 20 || >= 10`
- D) `poeng == 20 && kast == 10`
- **E) `poeng >= 20 || kast >= 10`** ✅ **Riktig**

> **Riktig svar: E.** Det holder at én av tingene har skjedd, så vi bruker `||`. «Minst» betyr `>=`.

**35.** Det skal stå «Dobbel!» når terningene er like **og** viser minst 4. Hva skal stå i den tomme parentesen?

```javascript
let t1 = Math.floor(Math.random() * 6) + 1;
let t2 = Math.floor(Math.random() * 6) + 1;

if ( ? ) {
  txtSvar.textContent = "Dobbel!";
}
```

- A) `t1 == t2 || t1 >= 4`
- **B) `t1 == t2 && t1 >= 4`** ✅ **Riktig**
- C) `t1 && t2 >= 4`
- D) `t1 == t2 && >= 4`
- E) `t1 >= 4 && t2 >= 4`

> **Riktig svar: B.** Begge kravene må gjelde, så vi bruker `&&`. Er terningene like, holder det å sjekke at én av dem er minst 4. I E er ikke kravet om like terninger med.

---

## Del 2 – Skriv linjen som mangler (2 poeng per oppgave)

Linjen som manglet, er satt inn i programmet og merket med «← svaret».

**36.** Programmet skal vise «Tenåring» for alder fra 13 til og med 19. Alderen skrives i `<input type="number" id="inpAlder">`. Skriv linjen som mangler.

```javascript
function sjekk() {
  let alder = Number(inpAlder.value);   // ← svaret

  if (alder >= 13 && alder <= 19) {
    txtSvar.textContent = "Tenåring";
  } else {
    txtSvar.textContent = "Ikke tenåring";
  }
}
```

**Forklaring:** Alderen må hentes fra input-feltet og gjøres om til et tall før `if`-en kan bruke den. Variabelen må hete `alder`, fordi det er det `if`-en bruker.

**2 poeng – dette er også riktig:**

- `let alder = Number(inpAlder.value);`

**1 poeng:** 1 p hvis `Number()` mangler, eller hvis variabelen har et annet navn enn `alder`.

**37.** Det er gratis å parkere før kl. 8 og fra kl. 18. Skriv `if`-linjen som mangler.

```javascript
let time = Number(inpTime.value);

if (time < 8 || time >= 18) {   // ← svaret
  txtSvar.textContent = "Gratis parkering";
} else {
  txtSvar.textContent = "Parkering: 30 kr per time";
}
```

**Forklaring:** Gratis parkering ligger utenfor tidsrommet 8–18. Klokka kan ikke være begge deler samtidig, så vi bruker `||`.

**2 poeng – dette er også riktig:**

- `if (time < 8 || time >= 18) {`
- `if (time >= 18 || time < 8) {`

**1 poeng:** 1 p hvis grensene er litt feil (for eksempel `time <= 8` eller `time > 18`), men `||` er riktig brukt.

**38.** 80 poeng eller mer gir «Meget godt», 50–79 gir «Godt», og under 50 gir «Ikke bestått». Skriv linjen som mangler. Den starter med `} else if`.

```javascript
if (poeng < 0 || poeng > 100) {
  txtSvar.textContent = "Ugyldig poengsum";
} else if (poeng >= 80) {
  txtSvar.textContent = "Meget godt";
} else if (poeng >= 50 && poeng < 80) {   // ← svaret
  txtSvar.textContent = "Godt";
} else {
  txtSvar.textContent = "Ikke bestått";
}
```

**Forklaring:** «Godt» gjelder fra og med 50 til og med 79. Siden 80 og mer allerede er sjekket, holder det egentlig å skrive `poeng >= 50`.

**2 poeng – dette er også riktig:**

- `} else if (poeng >= 50 && poeng < 80) {`
- `} else if (poeng >= 50 && poeng <= 79) {`
- `} else if (poeng >= 50) {` (riktig, fordi 80 og mer allerede er sjekket)

**1 poeng:** 1 p hvis `} else if` eller krøllparentesen mangler, eller hvis grensen er 51 eller `> 50`.

**39.** Skriv HTML-linjen for en knapp med teksten «Sjekk» som kjører funksjonen `sjekkHoyde()`.

```html
<label for="inpHoyde">Høyde (cm):</label>
<input type="number" id="inpHoyde">
<button onclick="sjekkHoyde()">Sjekk</button>  <!-- ← svaret -->
<p id="txtSvar"></p>
```

**Forklaring:** `onclick` bestemmer hvilken funksjon som kjører. Parentesene `()` må være med.

**2 poeng – dette er også riktig:**

- `<button onclick="sjekkHoyde()">Sjekk</button>`

**1 poeng:** 1 p hvis `()` eller `</button>` mangler.

**40.** Spilleren har 10 kast. Variabelen som teller kastene, må huske verdien mellom hvert trykk. Skriv linjen som mangler.

```javascript
let antallKast = 0;   // ← svaret

function kast() {
  if (antallKast >= 10) {
    txtSvar.textContent = "Ingen kast igjen.";
  } else {
    antallKast++;
    txtSvar.textContent = `Kast nummer ${antallKast}`;
  }
}
```

**Forklaring:** Variabelen står utenfor funksjonen og starter på 0. Da husker den antall kast mellom hvert trykk.

**2 poeng – dette er også riktig:**

- `let antallKast = 0;`

**1 poeng:** 1 p hvis variabelen starter på et annet tall enn 0, eller hvis navnet er feil.

**41.** Gokart: Du må være minst 140 cm høy, **og** du må enten være minst 12 år **eller** ha med en voksen. Skriv `if`-linjen som mangler.

```javascript
let hoyde = Number(inpHoyde.value);
let alder = Number(inpAlder.value);
let voksen = inpVoksen.value;

if (hoyde >= 140 && (alder >= 12 || voksen == "ja")) {   // ← svaret
  txtSvar.textContent = "Kjør forsiktig!";
} else {
  txtSvar.textContent = "Du får ikke kjøre.";
}
```

**Forklaring:** Høydekravet gjelder alltid. Parentesen samler «alder ELLER voksen». Uten parentes slipper alle som har med en voksen inn, uansett høyde.

**2 poeng – dette er også riktig:**

- `if (hoyde >= 140 && (alder >= 12 || voksen == "ja")) {`
- `if ((alder >= 12 || voksen == "ja") && hoyde >= 140) {`

**1 poeng:** 1 p hvis parentesen mangler, eller hvis én grense er feil.

**42.** Prisen ligger i variabelen `pris`. Skriv linjen som viser for eksempel «Prisen er 60 kr.» i `txtPris`.

```javascript
let alder = Number(inpAlder.value);
let pris = 120;

if (alder < 16 || alder >= 67) {
  pris = 60;
}
txtPris.textContent = `Prisen er ${pris} kr.`;   // ← svaret
```

**Forklaring:** Med bakstreker og `${pris}` settes verdien til variabelen inn i teksten.

**2 poeng – dette er også riktig:**

- ``txtPris.textContent = `Prisen er ${pris} kr.`;``
- `txtPris.textContent = "Prisen er " + pris + " kr.";`

**1 poeng:** 1 p hvis du har skrevet `${pris}` mellom vanlige anførselstegn, eller hvis `.textContent` mangler.

**43.** Summen 7 **eller** 11 skal gi 1 poeng. Skriv linjen som mangler. Den starter med `} else if`.

```javascript
if (t1 == 6 && t2 == 6) {
  poeng = poeng + 5;
} else if (t1 == t2) {
  poeng = poeng + 3;
} else if (t1 + t2 == 7 || t1 + t2 == 11) {   // ← svaret
  poeng = poeng + 1;
}
```

**Forklaring:** Summen må regnes ut i begge delene. Det holder at én av dem er sann, så vi bruker `||`.

**2 poeng – dette er også riktig:**

- `} else if (t1 + t2 == 7 || t1 + t2 == 11) {`

**1 poeng:** 1 p hvis `t1 + t2 ==` mangler i én av delene, eller hvis det står `&&`.

**44.** Knappen «Nytt spill» skal trekke et nytt hemmelig tall fra 1 til 10. Skriv linjen som mangler.

```javascript
let hemmelig = 0;
let forsok = 0;

function nyttSpill() {
  hemmelig = Math.floor(Math.random() * 10) + 1;   // ← svaret
  forsok = 0;
  txtHint.textContent = "";
}
```

**Forklaring:** `hemmelig` finnes allerede utenfor funksjonen, så vi skriver **ikke** `let`. Oppskriften er `Math.floor(Math.random() * N) + 1`.

**2 poeng – dette er også riktig:**

- `hemmelig = Math.floor(Math.random() * 10) + 1;`

**1 poeng:** 1 p hvis du har skrevet `let` foran. Da lages en ny variabel inni funksjonen, og spillet bruker ikke det nye tallet. 1 p hvis tallet er fra 0 til 9 (`+ 1` mangler).

**45.** Spillet skal stoppe når du har minst 15 poeng **eller** har kastet 10 ganger. Skriv `if`-linjen som mangler.

```javascript
let poeng = 0;
let kast = 0;

function kastTerning() {
  if (poeng >= 15 || kast >= 10) {   // ← svaret
    txtSvar.textContent = "Spillet er over!";
  } else {
    kast++;
    // ... kast terningen og gi poeng ...
  }
}
```

**Forklaring:** Spillet er over når **én** av tingene har skjedd, så vi bruker `||`.

**2 poeng – dette er også riktig:**

- `if (poeng >= 15 || kast >= 10) {`
- `if (kast >= 10 || poeng >= 15) {`

**1 poeng:** 1 p hvis det står `&&`, eller hvis det står `>` i stedet for `>=`.
