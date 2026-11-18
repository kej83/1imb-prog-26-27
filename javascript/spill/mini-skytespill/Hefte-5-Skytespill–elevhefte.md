# JavaScript 5: Skytespill – elevhefte

## Slik bruker du heftet

Sammen med læreren har du laget et spill der en fiende (`enemy`) dukker opp et tilfeldig sted på spillebrettet. Treffer du, hører du én lyd. Bommer du, hører du en annen. Nå skal du gjøre spillet bedre. Heftet har fire deler:

| Del | Hva du gjør |
| --- | --- |
| **Del 1** – Steg for steg | Du får all koden. Skriv den av, og test etter hvert steg. |
| **Del 2** – Fyll inn | Koden er halvveis ferdig. Du fyller inn det som mangler på strekene. |
| **Del 3** – Lag selv | Du får krav og tips, men ingen kode. |
| **Del 4** – Utfordringer | Vanskeligere oppgaver for deg som vil mer. |

Gjør del 1 først. Der retter vi en feil i spillet vi lagde sammen, og alle de andre oppgavene bygger på den.

**Lagre en kopi før hver ny del**, for eksempel `spill-del2.html`. Da har du alltid en versjon som virker.

**Koden vi lagde sammen** står i `index.html` og `style.css`. Heftet bruker de samme navnene: `spillBrett`, `enemy`, `treff()`, `bom()` og `respawnEnemy()`.

> **Husk fra fellesdelen**
>
> - `position: relative` på `#spillBrett` gjør at `top` og `left` på fienden måles fra hjørnet av brettet.
> - `position: absolute` på `#enemy` lar oss plassere fienden med `top` og `left`.
> - `` enemy.style.left = `${nyLeft}px`; `` flytter fienden. Uten `px` skjer ingenting.
> - Vi bruker `550` og `350` fordi brettet er 600 × 400 px og fienden er 50 px. Da havner den aldri utenfor.

<!-- side -->

## Del 1 – Steg for steg

### Steg 1 – Tell treff og bom

Spillet skal vise hvor mange treff og bom du har. Legg til et avsnitt rett over spillebrettet i `<body>`:

```html
    <p id="txtPoeng">Treff: 0 Bom: 0</p>
```

Legg til to variabler **øverst** i `<script>`, over `function treff()`:

```javascript
        let antallTreff = 0;
        let antallBom = 0;
```

Lag en ny funksjon nederst i `<script>`:

```javascript
        function visPoeng() {
            txtPoeng.textContent = `Treff: ${antallTreff} Bom: ${antallBom}`;
        }
```

Legg til disse to linjene i `treff()`, rett over `respawnEnemy();`:

```javascript
            antallTreff++;
            visPoeng();
```

Legg til disse to linjene i `bom()`, rett over `respawnEnemy();`:

```javascript
            antallBom++;
            visPoeng();
```

**Test:** Klikk ved siden av fienden tre ganger. Klikk så på fienden én gang. Hva står det på siden? Hører du én eller to lyder når du treffer?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### Steg 2 – Et treff skal ikke telle som bom

Du så sikkert at et treff også ble telt som bom. Fienden ligger **inni** spillebrettet, så et klikk på fienden er også et klikk på brettet. Nettleseren kjører først `treff()` og så `bom()`.

Vi løser det slik: `treff()` legger igjen en beskjed i en variabel, og `bom()` leser den. Legg til en variabel øverst i `<script>`:

```javascript
        let bleTruffet = false;
```

Legg til denne linjen **først** i `treff()`:

```javascript
            bleTruffet = true;
```

Bytt ut **hele** `bom()` med denne:

```javascript
        function bom() {
            if (bleTruffet == true) {
                bleTruffet = false;
            } else {
                var lyd = new Audio("bom.mp3");
                lyd.play();
                antallBom++;
                visPoeng();
                respawnEnemy();
            }
        }
```

**Forutsi:** Fyll ut tabellen før du tester.

| Du klikker på | Første funksjon som kjører | Andre funksjon som kjører | Treff øker? | Bom øker? |
| --- | --- | --- | --- | --- |
| Fienden | `treff()` |  |  |  |
| Brettet |  |  |  |  |

**Undersøk:** Fjern linjen `bleTruffet = false;` i `bom()`, og test. Hva skjer med neste bom? Sett linjen tilbake.

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

<!-- side -->

### Steg 3 – Ti skudd, så er spillet over

Spillet skal stoppe etter 10 skudd. Legg til et avsnitt under `txtPoeng`:

```html
    <p id="txtSlutt"></p>
```

Legg til en variabel øverst i `<script>`:

```javascript
        let maksSkudd = 10;
```

Lag en ny funksjon som viser en melding når spillet er over:

```javascript
        function sjekkSlutt() {
            if (antallTreff + antallBom >= maksSkudd) {
                txtSlutt.textContent = `Ferdig! Du traff ${antallTreff} av ${maksSkudd}.`;
            }
        }
```

Nå skal `treff()` og `bom()` bare gjøre noe så lenge spillet ikke er over. Bytt ut begge funksjonene med disse:

```javascript
        function treff() {
            bleTruffet = true;
            if (antallTreff + antallBom < maksSkudd) {
                var lyd = new Audio("treff2.mp3");
                lyd.play();
                antallTreff++;
                visPoeng();
                sjekkSlutt();
                respawnEnemy();
            }
        }

        function bom() {
            if (bleTruffet == true) {
                bleTruffet = false;
            } else if (antallTreff + antallBom < maksSkudd) {
                var lyd = new Audio("bom.mp3");
                lyd.play();
                antallBom++;
                visPoeng();
                sjekkSlutt();
                respawnEnemy();
            }
        }
```

- `bleTruffet = true;` står **før** `if`-en i `treff()`. Ellers blir et klikk på fienden etter at spillet er over, telt som bom.
- `antallTreff + antallBom < maksSkudd` betyr «spillet er ikke over ennå».

**Test:** Skyt 10 ganger. Står det «Ferdig!»? Teller nye klikk? Endre `maksSkudd` til 3, og test igjen.

<!-- side -->

### Sjekkpunkt – slik skal `<script>` se ut nå

Sammenlign med koden din. Rekkefølgen på funksjonene spiller ingen rolle.

<div class="small">

```javascript
let antallTreff = 0;
let antallBom = 0;
let bleTruffet = false;
let maksSkudd = 10;

function treff() {
    bleTruffet = true;
    if (antallTreff + antallBom < maksSkudd) {
        var lyd = new Audio("treff2.mp3");
        lyd.play();
        antallTreff++;
        visPoeng();
        sjekkSlutt();
        respawnEnemy();
    }
}

function bom() {
    if (bleTruffet == true) {
        bleTruffet = false;
    } else if (antallTreff + antallBom < maksSkudd) {
        var lyd = new Audio("bom.mp3");
        lyd.play();
        antallBom++;
        visPoeng();
        sjekkSlutt();
        respawnEnemy();
    }
}

function visPoeng() {
    txtPoeng.textContent =
        `Treff: ${antallTreff} Bom: ${antallBom}`;
}

function sjekkSlutt() {
    if (antallTreff + antallBom >= maksSkudd) {
        txtSlutt.textContent =
            `Ferdig! Du traff ${antallTreff} av ${maksSkudd}.`;
    }
}

function respawnEnemy() {
    let nyTop = Math.random()*350;
    let nyLeft = Math.random()*550;

    enemy.style.top = `${nyTop}px`;
    enemy.style.left = `${nyLeft}px`;
}
```

</div>

<!-- side -->

## Del 2 – Fyll inn det som mangler

Hver oppgave har kode med nummererte streker, for eksempel `__1__`. Skriv hva som skal stå på hver strek, og sett det inn i koden din. Test etter hver oppgave.

**4. Treffprosent.** Vis for eksempel «Treffprosent: 70 %». Lag avsnittet `<p id="txtProsent"></p>` under `txtPoeng`. Legg til dette nederst i `visPoeng()`:

```javascript
            let skudd = antallTreff + antallBom;
            if (skudd __1__ 0) {
                let prosent = Math.round(antallTreff / __2__ * 100);
                txtProsent.textContent = `Treffprosent: ${__3__} %`;
            }
```

1: \_\_\_\_\_\_\_\_ 2: \_\_\_\_\_\_\_\_ 3: \_\_\_\_\_\_\_\_ Hvorfor trenger vi `if`-en? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**5. Liv.** Du har 3 liv, og hvert bom koster ett liv. Spillet er over når du har mistet alle livene, **eller** når du har brukt alle skuddene. Endre `maksSkudd` til 20, og legg til `let liv = 3;` øverst. Vis livene med `<p id="txtLiv"></p>` og `` txtLiv.textContent = `Liv: ${liv}`; `` i `visPoeng()`.

I `bom()`, under `antallBom++;`:

```javascript
                liv__1__;
```

I **både** `treff()` og `bom()` skal betingelsen for «spillet er ikke over» endres til:

```javascript
liv __2__ 0 __3__ antallTreff + antallBom < maksSkudd
```

I `sjekkSlutt()` skal betingelsen for «spillet er over» endres til:

```javascript
            if (liv __4__ 0 __5__ antallTreff + antallBom >= maksSkudd) {
```

1: \_\_\_\_ 2: \_\_\_\_ 3: \_\_\_\_ 4: \_\_\_\_ 5: \_\_\_\_
Se på strek 3 og 5. Hvorfor blir det `&&` på den ene og `||` på den andre? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

<!-- side -->

**6. Rangering.** Når spillet er over, skal det stå en rangering: «Skarpskytter» for minst 8 treff **og** høyst 2 bom, «Godt skutt» for minst 5 treff, og ellers «Øv mer». Bytt ut innholdet i `if`-en i `sjekkSlutt()` med dette:

```javascript
                let rang = "";
                if (antallTreff __1__ 8 __2__ antallBom __3__ 2) {
                    rang = "Skarpskytter";
                } else if (antallTreff __4__ 5) {
                    rang = "Godt skutt";
                } __5__ {
                    rang = "Øv mer";
                }
                txtSlutt.textContent = `Ferdig! ${rang}.`;
```

1: \_\_\_\_ 2: \_\_\_\_ 3: \_\_\_\_ 4: \_\_\_\_ 5: \_\_\_\_\_\_\_\_

| Treff | Bom | Rangering |
| --- | --- | --- |
| 9 | 1 |  |
| 9 | 3 |  |
| 5 | 5 |  |
| 2 | 3 |  |

**7. Mindre og mindre.** Fienden skal krympe med 10 px ved 5 og 10 treff, men bare hvis den er større enn 20 px. Legg til `let storrelse = 50;` øverst. Legg dette inn i `treff()`, rett under `antallTreff++;`:

```javascript
                if ((antallTreff == 5 __1__ antallTreff == 10) __2__ storrelse > 20) {
                    storrelse = storrelse - 10;
                    enemy.style.width = storrelse __3__ "px";
                    enemy.style.height = storrelse + "px";
                }
```

Når fienden blir mindre, kan den komme nærmere kanten. Endre `respawnEnemy()`:

```javascript
            let nyTop = Math.random()*(400 - __4__);
            let nyLeft = Math.random()*(__5__ - storrelse);
```

1: \_\_\_\_ 2: \_\_\_\_ 3: \_\_\_\_ 4: \_\_\_\_\_\_\_\_ 5: \_\_\_\_\_\_\_\_
Hvorfor må parentesen rundt `||`-delen være med? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

<!-- side -->

## Del 3 – Lag selv

Nå får du krav og tips, men ingen kode. Se på koden du har skrevet, når du står fast.

**8. Nytt spill.** Lag en knapp «Nytt spill» som starter spillet på nytt.

- [ ] Treff, bom og liv settes tilbake til startverdiene.
- [ ] Meldingen i `txtSlutt` blir borte, og poengene vises på nytt.
- [ ] Fienden flyttes og får tilbake størrelsen 50 px.
- [ ] Knappen står **utenfor** spillebrettet. Hva skjer hvis den står inni?

Tips: Variablene finnes allerede, så du skal ikke skrive `let` inni funksjonen.

**9. Rekord.** Spillet skal huske det beste antallet treff.

- [ ] Rekorden vises hele tiden, for eksempel «Rekord: 9».
- [ ] Når et spill er over og du slo rekorden, står det «Ny rekord!».
- [ ] «Nytt spill» nullstiller **ikke** rekorden.

**10. Vanskelighetsgrad.** Lag tre knapper utenfor brettet. Hver knapp starter et nytt spill med sine egne innstillinger.

| Knapp | Størrelse på fienden | Antall skudd | Liv |
| --- | --- | --- | --- |
| Lett | 70 px | 25 | 5 |
| Middels | 50 px | 20 | 3 |
| Vanskelig | 30 px | 15 | 1 |

Tips: Lag én funksjon per knapp. Hver av dem setter variablene og kaller funksjonen fra oppgave 8.

**11. Gullfiende.** Omtrent hver femte gang skal fienden bli gull og gi 3 poeng i stedet for 1.

- [ ] Spillet har en egen variabel for poeng. Treff og poeng er ikke lenger det samme.
- [ ] `Math.random() < 0.2` er sant omtrent hver femte gang. Bruk det i `respawnEnemy()`.
- [ ] En gullfiende har fargen `gold`. En vanlig fiende har sin vanlige farge.
- [ ] Et treff på en gullfiende har sin egen lyd.

Tenk over: Må du gi poengene **før** eller **etter** at `respawnEnemy()` kjører? Hvorfor?

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

<!-- side -->

## Del 4 – Utfordringer

**12. Fienden beveger seg.** Fienden skal gli over brettet i stedet for å stå stille.

- `setInterval(flyttEnemy, 40);` kjører funksjonen `flyttEnemy` 25 ganger i sekundet.
- Fiendens plassering må ligge i variabler utenfor funksjonene, for eksempel `x` og `y`. Husk å oppdatere dem i `respawnEnemy()` også.
- Inni `flyttEnemy()` øker du `x` og `y` med litt, for eksempel 2 px, og flytter fienden.
- **Ekstra:** Fienden skal sprette tilbake fra kantene. Lag variablene `fartX = 2` og `fartY = 2`. Når fienden treffer venstre **eller** høyre kant, snur du farten: `fartX = -fartX;`. Gjør det samme for toppen og bunnen.

| Når skal fienden snu? | Betingelse |
| --- | --- |
| Venstre eller høyre kant | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |
| Toppen eller bunnen | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |

**13. Nedtelling.** Du har 30 sekunder på deg.

- Vis tiden som er igjen, for eksempel «Tid: 17».
- `let tidtaker = setInterval(nedtelling, 1000);` kjører `nedtelling` hvert sekund. Der trekker du 1 fra tiden.
- Spillet er over når tiden er ute, **eller** livene er brukt opp, **eller** skuddene er brukt opp. Utvid betingelsene fra oppgave 5.
- `clearInterval(tidtaker);` stopper nedtellingen. Hva skjer med «Nytt spill» hvis du glemmer å stoppe den gamle tidtakeren?

**14. To fiender.** Lag en fiende til (`enemy2`) med en annen farge.

- Hver fiende har sin egen treff-funksjon. Den ene kan gi flere poeng enn den andre.
- Hver fiende har sin egen respawn-funksjon.
- Hva må du passe på med `bleTruffet` når det er to fiender?

**15. Din egen idé.** Hva mer kan gjøre spillet bedre? Noen forslag: et bilde i stedet for en sirkel, en fiende som blir raskere for hvert treff, eller et sikte som musepeker (`cursor: crosshair;`). Skriv idéen din her, og lag den.

Svar: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Husk:** Lagre en kopi før hver ny del, og test etter hvert steg!
