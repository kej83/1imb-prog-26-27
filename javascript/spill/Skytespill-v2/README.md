# JavaScript 6: Mini skytespill – elevhefte

## Slik bruker du heftet

Sammen med læreren har du laget et mini skytespill. Fienden (`enemy`) starter usynlig utenfor brettet, glir inn og over spillebrettet (`gameboard`). Treffer du den, får du poeng. Nå skal du gjøre spillet kulere og morsommere. Heftet har fire deler:

| Del | Hva du gjør |
| --- | --- |
| **Del 1** – Steg for steg | Kult design og nye regler. Du får all koden. |
| **Del 2** – Fyll inn | Koden er halvveis ferdig. Du fyller inn det som mangler på strekene. |
| **Del 3** – Lag selv | Du får krav og tips, men ingen kode. |
| **Del 4** – Utfordringer | Vanskeligere oppgaver for deg som vil mer. |

Gjør del 1 først. Alle de andre oppgavene bygger på den.

**Lagre en kopi før hver ny del**, for eksempel `spill-del2.html`. Da har du alltid en versjon som virker. Test etter hvert steg!

> **Husk fra fellesgjennomgangen**
>
> - `overflow: hidden` på `#gameboard` gjør at alt utenfor brettet er usynlig. Derfor kan fienden starte på `x = -30` og gli inn.
> - `x` og `y` sier hvor fienden **er**. `tegnFiende()` flytter den på skjermen. Endrer du `x` eller `y`, må du kalle `tegnFiende()`.
> - `nyFiende()` lager en ny fiende. Den brukes både ved treff og når fienden har glidd ut.
> - `setInterval(flytt, 20)` kjører `flytt()` 50 ganger i sekundet. `clearInterval(tidtaker)` stopper den.
> - Bruk variablene `brettBredde`, `brettHoyde` og `fiendeStorrelse` i stedet for tallene 500, 400 og 30.

**Koden vi lagde sammen** – `<script>` i `index.html`:

```javascript
        // Størrelser – de samme tallene som i style.css
        let brettBredde = 500;
        let brettHoyde = 400;
        let fiendeStorrelse = 30;

        // Hvor fienden er, og hvor fort den går
        let x = 0;
        let y = 0;
        let fart = 2;

        // Poeng
        let poeng = 0;

        // Flytter fienden på skjermen dit x og y sier
        function tegnFiende() {
            enemy.style.left = `${x}px`;
            enemy.style.top = `${y}px`;
        }

        // Ny fiende starter usynlig utenfor brettet, til venstre
        function nyFiende() {
            x = -fiendeStorrelse;
            y = Math.floor(Math.random() * (brettHoyde - fiendeStorrelse));
            tegnFiende();
        }

        // Kjører 50 ganger i sekundet
        function flytt() {
            x = x + fart;
            if (x > brettBredde) {
                nyFiende();
            }
            tegnFiende();
        }

        function treff() {
            poeng++;
            txtPoeng.textContent = `Poeng: ${poeng}`;
            nyFiende();
        }

        nyFiende();
        let tidtaker = setInterval(flytt, 20);
```

**Forstår du koden?**

1. Hvorfor ser du ikke fienden når `x` er −30? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
2. Hvor mange piksler går fienden på ett sekund? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
3. Hvorfor er grensen i `flytt()` `x > brettBredde` og ikke `x > brettBredde - fiendeStorrelse`? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

<!-- side -->

## Del 1 – Steg for steg

### Steg 1 – Kult design

Bytt ut **alt** i `style.css` med dette. Spillet får mørk bakgrunn, lysende kanter og en fiende som pulserer.

```css
body {
    background-color: #0b0f1a;
    color: #e6f1ff;
    font-family: "Courier New", monospace;
    text-align: center;
}

h1 {
    color: #7cf9ff;
    text-transform: uppercase;
    letter-spacing: 6px;
    text-shadow: 0 0 8px #7cf9ff, 0 0 24px #00b3ff;
}

#txtPoeng {
    font-size: 22px;
    color: #ffe66d;
}

#txtSlutt {
    font-size: 26px;
    color: #ff4d6d;
    text-shadow: 0 0 10px #ff4d6d;
}

#gameboard {
    position: relative;
    width: 500px;
    height: 400px;
    margin: 0 auto;
    overflow: hidden;
    border: 2px solid #7cf9ff;
    border-radius: 12px;
    background: radial-gradient(circle at 50% 40%, #1b2a4a, #05070d);
    box-shadow: 0 0 25px #00b3ff;
    cursor: crosshair;
}

#enemy {
    position: absolute;
    width: 30px;
    height: 30px;
    left: -30px;
    top: 0px;
    border-radius: 50%;
    background: radial-gradient(circle at 35% 35%, #b6ff9e, #2ecc40 60%, #0a5c1a);
    box-shadow: 0 0 12px #2ecc40;
    animation: puls 0.6s infinite alternate;
}

@keyframes puls {
    from { transform: scale(1); }
    to   { transform: scale(1.2); }
}
```

| CSS | Hva det gjør |
| --- | --- |
| `text-shadow` / `box-shadow` | Lager en glød rundt tekst og bokser. Flere skygger skilles med komma. |
| `radial-gradient(...)` | En farge som går over i en annen, fra et punkt og utover. Fienden ser ut som en kule. |
| `animation` og `@keyframes` | Fienden vokser og krymper hele tiden. `alternate` betyr fram og tilbake. |
| `cursor: crosshair` | Musepekeren blir et sikte over brettet. |
| `margin: 0 auto` | Midtstiller brettet. |

**Prøv selv:** Endre fargene. `#2ecc40` er grønn. Prøv `#ff4d6d` (rosa) eller `#bf7cff` (lilla). Endre `0.6s` i animasjonen til `0.2s`. Hva skjer?

<!-- side -->

### Steg 2 – Lyd, og fiender som rømmer

Når fienden glir ut på høyre side, har den **rømt**. Det skal telles. Ved treff skal det spilles en lyd. Legg lydfilen `treff.mp3` i samme mappe.

Endre poengteksten i HTML-en:

```html
    <p id="txtPoeng">Poeng: 0 Rømt: 0</p>
```

Legg til en variabel under `let poeng = 0;`:

```javascript
        let romt = 0;
```

Lag en funksjon som viser poengene:

```javascript
        function visPoeng() {
            txtPoeng.textContent = `Poeng: ${poeng} Rømt: ${romt}`;
        }
```

Bytt ut **hele** `flytt()` og `treff()` med dette:

```javascript
        function flytt() {
            x = x + fart;
            if (x > brettBredde) {
                romt++;
                visPoeng();
                nyFiende();
            }
            tegnFiende();
        }

        function treff() {
            let lyd = new Audio("treff.mp3");
            lyd.play();
            poeng++;
            visPoeng();
            nyFiende();
        }
```

**Test:** Treff to fiender, og la én slippe unna. Står det «Poeng: 2 Rømt: 1»?

### Steg 3 – Raskere og raskere

For hvert treff skal fienden gå litt fortere. Legg til denne linjen i `treff()`, rett under `poeng++;`:

```javascript
            fart = fart + 0.5;
```

**Forutsi:** Fienden går `fart` × 50 piksler i sekundet.

| Antall treff | `fart` | Piksler per sekund |
| --- | --- | --- |
| 0 | 2 | 100 |
| 4 |  |  |
| 10 |  |  |

<!-- side -->

### Steg 4 – Game over

Når tre fiender har rømt, er spillet over. Da skal fienden stoppe, og nye treff skal ikke telle.

Legg til et avsnitt under `txtPoeng`:

```html
    <p id="txtSlutt"></p>
```

Lag en ny funksjon:

```javascript
        function sjekkSlutt() {
            if (romt >= 3) {
                clearInterval(tidtaker);
                txtSlutt.textContent = `GAME OVER – ${poeng} poeng`;
            }
        }
```

I `flytt()` legger du til `sjekkSlutt();` rett under `visPoeng();`.

Til slutt skal `treff()` bare gjøre noe så lenge spillet ikke er over. Legg alt inni `treff()` inn i en `if`. `romt < 3` betyr «spillet er ikke over ennå».

```javascript
        function treff() {
            if (romt < 3) {
                let lyd = new Audio("treff.mp3");
                lyd.play();
                poeng++;
                fart = fart + 0.5;
                visPoeng();
                nyFiende();
            }
        }
```

**Test:** La tre fiender rømme. Står det «GAME OVER»? Stopper fienden? Teller et klikk på fienden nå?

### Sjekkpunkt – slik skal `<script>` se ut nå

Sammenlign med koden din. Rekkefølgen på funksjonene spiller ingen rolle, men `nyFiende();` og `setInterval` skal stå nederst.

```javascript
        let brettBredde = 500;
        let brettHoyde = 400;
        let fiendeStorrelse = 30;

        let x = 0;
        let y = 0;
        let fart = 2;

        let poeng = 0;
        let romt = 0;

        function tegnFiende() {
            enemy.style.left = `${x}px`;
            enemy.style.top = `${y}px`;
        }

        function nyFiende() {
            x = -fiendeStorrelse;
            y = Math.floor(Math.random() * (brettHoyde - fiendeStorrelse));
            tegnFiende();
        }

        function flytt() {
            x = x + fart;
            if (x > brettBredde) {
                romt++;
                visPoeng();
                sjekkSlutt();
                nyFiende();
            }
            tegnFiende();
        }

        function treff() {
            if (romt < 3) {
                let lyd = new Audio("treff.mp3");
                lyd.play();
                poeng++;
                fart = fart + 0.5;
                visPoeng();
                nyFiende();
            }
        }

        function visPoeng() {
            txtPoeng.textContent = `Poeng: ${poeng} Rømt: ${romt}`;
        }

        function sjekkSlutt() {
            if (romt >= 3) {
                clearInterval(tidtaker);
                txtSlutt.textContent = `GAME OVER – ${poeng} poeng`;
            }
        }

        nyFiende();
        let tidtaker = setInterval(flytt, 20);
```

<!-- side -->

## Del 2 – Fyll inn det som mangler

Hver oppgave har kode med nummererte streker, for eksempel `__1__`. Skriv hva som skal stå på hver strek, og sett det inn i koden din. Test etter hver oppgave.

### 5. Rekord

Spillet skal huske det beste resultatet. Lag `<p id="txtRekord">Rekord: 0</p>` og `let rekord = 0;`. Legg dette inn i `sjekkSlutt()`, rett under `clearInterval(tidtaker);`:

```javascript
                if (poeng __1__ rekord) {
                    rekord __2__ poeng;
                    txtRekord.textContent = `Rekord: ${__3__}`;
                }
```

1: \_\_\_\_\_\_\_\_ 2: \_\_\_\_\_\_\_\_ 3: \_\_\_\_\_\_\_\_

### 6. Fiender fra begge sider

Halvparten av fiendene skal starte usynlig til venstre og gå mot høyre. Den andre halvparten skal starte usynlig til høyre og gå mot venstre. Lag `let retning = 1;`. Bytt ut linjen `x = -fiendeStorrelse;` i `nyFiende()` med:

```javascript
            if (Math.random() __1__ 0.5) {
                retning = 1;
                x = -fiendeStorrelse;
            } else {
                retning = -1;
                x = __2__;
            }
```

Endre de to første linjene i `flytt()`:

```javascript
            x = x + fart __3__ retning;
            if (x > brettBredde __4__ x __5__ -fiendeStorrelse) {
```

1: \_\_\_\_ 2: \_\_\_\_\_\_\_\_\_\_\_\_ 3: \_\_\_\_ 4: \_\_\_\_ 5: \_\_\_\_
Hvorfor må det være `||` på strek 4, og ikke `&&`? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

| `retning` | `fart` | Endring i `x` hver gang | Fienden går mot |
| --- | --- | --- | --- |
| 1 | 2 | +2 | høyre |
| -1 | 2 |  |  |
| -1 | 3.5 |  |  |

<!-- side -->

### 7. Gullfiende

Omtrent hver femte fiende skal være gull og gi 3 poeng. Her bytter vi utseende ved å gi fienden en **CSS-klasse**. Legg dette nederst i `style.css`:

```css
#enemy.gull {
    background: radial-gradient(circle at 35% 35%, #fff6b0, #ffd700 60%, #8a6d00);
    box-shadow: 0 0 18px #ffd700;
}
```

Lag `let erGull = false;`. Legg dette til i `nyFiende()`, over `tegnFiende();`:

```javascript
            erGull = Math.random() __1__ 0.2;
            if (erGull) {
                enemy.className = __2__;
            } else {
                enemy.className = "";
            }
```

Bytt ut `poeng++;` i `treff()` med:

```javascript
                if (__3__) {
                    poeng = poeng + 3;
                } else {
                    poeng__4__;
                }
```

1: \_\_\_\_ 2: \_\_\_\_\_\_\_\_ 3: \_\_\_\_\_\_\_\_ 4: \_\_\_\_
Poengene må gis **før** `nyFiende()` kjører i `treff()`. Hvorfor? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

### 8. Fienden går på skrå

Fienden skal også bevege seg litt opp eller ned, og sprette tilbake fra toppen og bunnen. Lag `let fartY = 0;`. Legg til i `nyFiende()`, over `tegnFiende();`:

```javascript
            fartY = Math.random() * 2 - 1;   // et tall mellom -1 og 1
```

Legg dette til i `flytt()`, rett under linjen der `x` endres:

```javascript
            y = y + __1__;
            if (y < 0 __2__ y > brettHoyde __3__ fiendeStorrelse) {
                fartY = __4__fartY;
            }
```

1: \_\_\_\_\_\_\_\_ 2: \_\_\_\_ 3: \_\_\_\_ 4: \_\_\_\_
Hva betyr det at `fartY` er negativ? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_
Se på koden: Hvorfor trenger vi ikke endre `tegnFiende()`? \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

<!-- side -->

## Del 3 – Lag selv

Nå får du krav og tips, men ingen kode. Se på koden du har skrevet, når du står fast.

### 9. Nytt spill

Lag en knapp «Nytt spill» som starter spillet på nytt.

- [ ] Poeng, rømt og fart settes tilbake til startverdiene. Rekorden blir **ikke** nullstilt.
- [ ] Meldingen om game over blir borte, og poengene vises på nytt.
- [ ] En ny fiende starter, og den beveger seg igjen.
- [ ] Knappen virker også midt i et spill, uten at fienden går dobbelt så fort.

Tips: Start en ny tidtaker med `tidtaker = setInterval(flytt, 20);`. Stopp alltid den gamle med `clearInterval(tidtaker);` først. Hvorfor?

### 10. Bombe – ikke skyt!

Av og til skal fienden være en rød bombe. Treffer du bomben, mister du 3 poeng. Lar du den gli ut, teller den **ikke** som rømt.

```css
#enemy.bombe {
    background: radial-gradient(circle at 35% 35%, #ffb3b3, #ff2a2a 60%, #5c0000);
    box-shadow: 0 0 18px #ff2a2a;
    border-radius: 4px;
}
```

- [ ] Omtrent hver sjette fiende er en bombe. En fiende kan ikke være både bombe og gull.
- [ ] Bomben har sin egen lyd.
- [ ] Poengene blir aldri mindre enn 0.

### 11. Eksplosjon

Et treff skal synes skikkelig.

- [ ] Brettet blinker ved treff. Lag en CSS-klasse `.blink` med en lysere bakgrunn, og gi brettet klassen med `gameboard.className = "blink";`.
- [ ] Klassen fjernes etter 100 millisekunder. Tips: `setTimeout(fjernBlink, 100);` kjører funksjonen `fjernBlink` én gang etter 100 ms.
- [ ] Det står «+1» eller «+3» ved siden av poengene en kort stund.

### 12. Mindre og mindre

Ved 5, 10 og 15 poeng skal fienden bli 5 px mindre, men aldri mindre enn 15 px.

- [ ] Endre `fiendeStorrelse`, og sett `enemy.style.width` og `enemy.style.height`.
- [ ] Fienden må fortsatt starte helt usynlig og gå helt ut før den kommer tilbake. Sjekk at det stemmer. Hvorfor gjør det det helt av seg selv?
- [ ] Bruk `>=` og en variabel for nivå, slik at et gulltreff som hopper fra 4 til 7 poeng også teller.

<!-- side -->

## Del 4 – Utfordringer

### 13. Sprett overalt

Fienden skal sprette rundt på hele brettet, som en ball, i stedet for å gli ut. Den kan ikke lenger rømme.

- Når fienden treffer venstre **eller** høyre kant, snur du `retning`. Når den treffer toppen **eller** bunnen, snur du `fartY`.
- Finn på en ny regel for game over, for eksempel tid eller antall bom.

| Når skal fienden snu? | Betingelse |
| --- | --- |
| Venstre eller høyre kant | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |
| Toppen eller bunnen | \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_ |

### 14. Nedtelling

Du har 30 sekunder på deg.

- Vis tiden som er igjen. Lag en tidtaker til, som kjører `nedtelling()` hvert sekund (`1000` ms).
- Spillet er over når tiden er ute, **eller** når tre fiender har rømt. Begge tidtakerne skal da stoppes.
- Gjør tiden rød og blinkende når det er under 10 sekunder igjen. Bruk en CSS-klasse.

### 15. To fiender

Lag en fiende til (`enemy2`) med en annen farge, størrelse og fart.

- Den trenger sine egne variabler: `x2`, `y2` og `fart2`. Den trenger også sine egne funksjoner: `tegnFiende2()`, `nyFiende2()` og `treff2()`.
- Begge kan flyttes i den samme `flytt()`.
- Den minste og raskeste fienden kan gi flest poeng.

### 16. Din egen idé

Noen forslag:

- **Romvesen:** Skriv `enemy.textContent = "👾";` og gi `#enemy` en stor `font-size` og ingen bakgrunn.
- **Stjernehimmel:** Legg flere `radial-gradient` med små hvite prikker i bakgrunnen på brettet.
- **Sjef-fiende:** På nivå 3 kommer en stor fiende som må treffes fem ganger.
- **Livsbar:** Vis tre hjerter som forsvinner når fiender rømmer.

Min idé: \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_

**Husk:** Lagre en kopi før hver ny del, og test etter hvert steg!