# Kapittel 6: Klasser, id-er og bildestiler

*HTML og CSS — hefte 6 i serien «Nettsider fra bunnen av». Bygger på hefte 1–5.*

---

I hefte 5 lærte du elementselektorer. De er kraftige — men også litt for kraftige. Skriver du en regel for `p`, treffer den *alle* avsnitt på siden. Hva om ett av dem skal se annerledes ut enn de andre?

Det er problemet dette heftet løser. Du lærer å sette merkelapper på elementene i HTML-en, slik at CSS-en kan plukke ut akkurat dem du vil. Til slutt bruker du det nye til noe elevene alltid vil ha: å gjøre bilder pene.

> **💡 Tips:** Lag en ny mappe `nettside6` for dette heftet. Du trenger også et par bilder — bruk egne, nedlastede eller `picsum.photos` fra hefte 3.

---

## 6.1 Klasser

```html
<body>
  <h1>Turgruppa</h1>
  <p class="ingress">Vi går tur hver torsdag, og alle kan bli med.</p>
  <p>Turene tar mellom én og to timer.</p>
  <p>Vi er tilbake før det blir mørkt.</p>
</body>
```

```css
p {
  color: #333333;
}

.ingress {
  color: #1a5276;
  font-size: 22px;
}
```

Det første avsnittet er en **ingress** — den lille innledningen som skal skille seg ut. For å få tak i akkurat det avsnittet, gir vi det en merkelapp med attributtet `class`.

1. Lag fila `index.html` og `stil.css`, skriv av koden, og se på resultatet.
2. Se nøye på skrivemåten. I HTML står det `class="ingress"` — uten punktum. I CSS står det `.ingress` — **med** punktum. Punktumet er tegnet som betyr «klasse».
3. Fjern punktumet i CSS-fila, slik at det står `ingress { ... }`. Lagre, og se hva som skjer med siden.

Ingenting skjer — for nå leter nettleseren etter et element som heter `<ingress>`, og det finnes ikke. Sett punktumet tilbake.

4. Gi også det siste avsnittet `class="ingress"`. Hvor mange avsnitt er blå nå?

Der har du den store forskjellen fra elementselektoren: **du bestemmer selv** hvilke elementer regelen gjelder for.

5. Lag en ny klasse `.advarsel` som gir teksten rød farge, og bruk den på et nytt avsnitt du legger til nederst.

> **⚠️ Merk:** Klassenavn bør beskrive **hva innholdet er**, ikke hvordan det ser ut. `.ingress` er et godt navn; `.blaa-tekst` er et dårlig et — for hva gjør du den dagen ingressen skal bli grønn?

> **💡 Tips:** Klassenavn kan ikke inneholde mellomrom, og bør skrives med små bokstaver. Trenger du flere ord, bruk bindestrek: `class="viktig-melding"`.

---

## 6.2 Flere klasser på samme element

```html
<p class="ingress">Bare ingress.</p>
<p class="advarsel">Bare advarsel.</p>
<p class="ingress advarsel">Begge deler!</p>
```

```css
.ingress {
  font-size: 22px;
}

.advarsel {
  color: crimson;
  font-weight: bold;
}
```

Et element kan ha flere klasser samtidig. Da skriver du dem inni de samme anførselstegnene, med **mellomrom** mellom.

1. Skriv av koden, og se på de tre avsnittene. Hva har det siste fått av de to reglene?
2. Bytt om rekkefølgen, slik at det står `class="advarsel ingress"`. Endret noe seg?

Nei. Rekkefølgen i HTML betyr ingenting — det er rekkefølgen i **CSS-fila** som avgjør hvis to regler krasjer, akkurat som du lærte i hefte 5.

3. Lag en klasse `.stor` som setter `font-size: 30px`, og gi ett av avsnittene både `advarsel` og `stor`.

Slik jobber profesjonelle: de lager små klasser som gjør én ting hver, og kombinerer dem etter behov.

> **🐞 Når noe går galt:** Skriver du `class="ingress, advarsel"` med komma, virker ingen av dem. Nettleseren tror da at klassen heter `ingress,`. Bare mellomrom mellom klassenavnene.

---

## 6.3 Id

```html
<p id="hovedbudskap">Husk å melde deg på innen fredag!</p>
```

```css
#hovedbudskap {
  background-color: #fdf2cc;
  color: #7d6608;
}
```

En **id** er også en merkelapp, men med en viktig forskjell: en id skal brukes på **bare ett** element per side. I CSS skriver du den med firkanttegn: `#hovedbudskap`.

1. Legg koden inn på siden din, og se på resultatet.
2. Gi et annet avsnitt den samme id-en `hovedbudskap`. Ser du noen forskjell på siden?

Begge avsnittene blir gule — nettleseren klager ikke. Men koden er nå feil, akkurat som to `<h1>` eller to `<main>` er feil. En id er ment å peke ut ett bestemt sted på siden.

3. Fjern den ekstra id-en igjen.

### Klasse eller id?

| | `class` | `id` |
|---|---|---|
| Hvor mange ganger per side? | Så mange du vil | Bare én gang |
| Skrives i CSS som | `.navn` | `#navn` |
| Brukes til | Stil som skal gjenbrukes | Ett helt bestemt element |

Regelen er enkel: **bruk klasse.** Nesten all styling handler om ting som skal gjenbrukes, og klasser kan gjenbrukes. Id-er er til når du trenger å peke ut nøyaktig ett element — og den virkelig store nytten kommer når du lærer JavaScript senere, der du stadig må få tak i ett bestemt element.

---

## 6.4 `<div>`: en boks uten betydning

```html
<div class="faktaboks">
  <h3>Visste du at ...</h3>
  <p>Turgruppa ble startet i 2024.</p>
</div>
```

```css
.faktaboks {
  background-color: #eaf2f8;
}
```

Noen ganger vil du style flere elementer **sammen** — gi dem felles bakgrunn, felles ramme, felles plassering. Da trenger du noe å pakke dem inn i. Elementet `<div>` er en slik boks.

1. Legg koden inn på siden din, og se hvordan overskriften og avsnittet får felles bakgrunn.
2. Legg til et avsnitt til inni `<div>`-en. Får det også bakgrunnen?
3. Flytt ett av avsnittene ut av `<div>`-en, og se på resultatet.

En `<div>` betyr **ingenting**. Den sier verken at innholdet er en seksjon, en artikkel eller en meny — den er bare en boks. Og det er både styrken og svakheten.

> **⚠️ Merk:** Før du skriver en `<div>`, still deg spørsmålet fra hefte 4: **hva ER dette?** Er det et tema med egen overskrift, skal det være en `<section>`. Er det sidens topp, en `<header>`. Er det menyen, en `<nav>`. Bruk `<div>` bare når innholdet ikke har noen egen betydning — når du trenger en boks, og ingenting mer.

4. Har du en `<section>` på siden fra før? Gi den en klasse, og style den på samme måte. Du trengte altså aldri en `<div>` der.

Nettsider laget av nybegynnere er ofte fulle av `<div>`-er der det skulle stått semantiske elementer. Det har til og med et kallenavn blant utviklere: *divitis*.

---

## 6.5 `<span>`: en bit inne i teksten

```html
<p>Turen koster <span class="pris">150 kroner</span> per person.</p>
```

```css
.pris {
  color: crimson;
  font-weight: bold;
}
```

`<span>` er `<div>`-ens lillebror: en merkelapp du kan sette rundt noen få ord **inne i** en tekst, uten at det lages et nytt avsnitt.

1. Skriv av koden, og se på resultatet.
2. Bytt ut `<span>` med `<div>`, og se hva som skjer med linjeskiftene. Bytt tilbake.

Der ser du forskjellen: en `<div>` tar hele bredden og skyver resten nedover, mens en `<span>` holder seg på linja. (Hvorfor det er slik, lærer du i hefte 8.)

3. Merk et par andre ord i teksten din med `<span>` og en klasse du lager selv.

> **⚠️ Merk:** Skal ordet utheves fordi det er **viktig**, bruk `<strong>` fra hefte 2 — ikke en `<span>`. `<span>` er for når du bare trenger et sted å henge en klasse.

---

## 6.6 Rammer

```css
.faktaboks {
  background-color: #eaf2f8;
  border: 3px solid #1a5276;
}
```

En ramme rundt en boks lages med `border`, og skrives med tre verdier i denne rekkefølgen:

```text
border: 3px    solid   #1a5276;
        ^^^    ^^^^^   ^^^^^^^
        bredde stil    farge
```

1. Legg rammen på faktaboksen din, og se på resultatet.
2. Prøv de ulike stilene ved å bytte ut `solid`:

| Verdi | Gir |
|---|---|
| `solid` | Heltrukken strek |
| `dashed` | Stiplet strek |
| `dotted` | Prikket strek |
| `double` | Dobbel strek |
| `none` | Ingen ramme |

3. Øk bredden til `10px`, og prøv `double` igjen. Nå ser du forskjellen tydelig.
4. Gi også `.advarsel`-avsnittet en ramme i en farge som passer.

Du kan også gi ramme til bare én side av boksen — det brukes ofte til sitater:

```css
blockquote {
  border-left: 5px solid #1a5276;
}
```

5. Prøv `border-left` på et `<blockquote>` du legger til på siden. Prøv også `border-bottom` under en `<h2>`.

> **💡 Tips:** Rammen legger seg helt inntil innholdet, og det ser ofte trangt ut. Luften mellom ramme og innhold heter `padding`, og den er hovedtemaet i hefte 7.

---

## 6.7 Bildestiler

```html
<img src="bilder/tur1.jpg" alt="Utsikt fra fjelltopp" class="galleribilde">
<img src="bilder/portrett.jpg" alt="Portrett av turlederen" class="portrett">
```

```css
.galleribilde {
  width: 300px;
  border: 4px solid #ffffff;
}

.portrett {
  width: 150px;
  border-radius: 50%;
}
```

Bilder er der klasser virkelig viser seg nyttige: nesten alltid skal ulike bilder på samme side se ulike ut. Et galleribilde, et portrett og en logo har ingenting med hverandre å gjøre — men alle er `<img>`.

1. Skaff to bilder, legg dem i mappa `bilder`, og skriv av koden. Tilpass filnavnene.
2. Se på portrettet. `border-radius: 50%` gjør bildet helt rundt — det er slik profilbilder lages overalt på nett.
3. Prøv andre verdier på `border-radius`: `0`, `8px`, `25px`, `50%`. Hvor går grensen mellom «litt avrundede hjørner» og «rundt»?

### De vanligste bildestilene

| Egenskap | Gjør | Typisk verdi |
|---|---|---|
| `width` | Bestemmer bredden. Høyden følger med av seg selv | `300px` |
| `border` | Ramme rundt bildet | `4px solid #ffffff` |
| `border-radius` | Avrundede hjørner — `50%` gir sirkel | `8px` eller `50%` |

4. Sett `width: 300px` på galleribildet, og legg deretter til `height: 300px`. Se nøye på bildet. Hva skjedde med proporsjonene?

Når du setter **både** bredde og høyde, blir bildet strukket eller klemt sammen. Derfor setter man som regel bare `width` — da regner nettleseren ut riktig høyde selv.

5. Fjern `height` igjen.
6. Lag en tredje klasse `.miniatyr` med `width: 100px` og en tynn grå ramme, og bruk den på et par små bilder.

> **💡 Tips:** Bildeklasser er også en gyllen anledning til å rydde: har du tre bilder som skal se helt like ut, skal de ha **samme** klasse — ikke tre nesten like regler. Ser du deg selv kopiere en CSS-regel, er det nesten alltid en klasse som mangler.

---

## 6.8 Når flere regler treffer samme element

```html
<p class="ingress" id="hovedbudskap">Hvilken farge blir jeg?</p>
```

```css
p {
  color: black;
}

.ingress {
  color: crimson;
}

#hovedbudskap {
  color: navy;
}
```

Nå kan det samme elementet treffes av tre regler samtidig. Hvem vinner?

1. Les koden, og gjett fargen. Skriv gjetningen ned.
2. Skriv av koden, og sjekk.

Avsnittet blir **mørkeblått**. Reglene har nemlig ulik styrke, og den sterkeste vinner — uansett hvilken rekkefølge de står i:

```text
element   <   klasse   <   id
  p           .ingress     #hovedbudskap
svakest                    sterkest
```

3. Flytt `p`-regelen nederst i fila, og sjekk fargen på nytt. Endret noe seg?

Nei. Rekkefølgen avgjør bare når reglene er **like sterke** — som de to `p`-reglene du prøvde i hefte 5. Er de ulikt sterke, vinner alltid den sterkeste.

4. Fjern `id`-en fra HTML-en. Hvilken farge får avsnittet nå?
5. Fjern også klassen. Nå er bare `p`-regelen igjen.

Dette er grunnen til at rådet «bruk klasse, ikke id» også handler om praktisk arbeid: id-regler er så sterke at de blir vanskelige å overstyre senere. Med klasser holder du CSS-en fleksibel.

---

## Sammendrag

### Klasser

```html
<p class="ingress">Et avsnitt med klasse.</p>
<p class="ingress stor">Et avsnitt med to klasser.</p>
```

```css
.ingress {
  color: #1a5276;
}
```

Klassen settes i HTML **uten** punktum, og skrives i CSS **med** punktum. Ett element kan ha flere klasser, skilt med mellomrom. Navngi etter hva innholdet er, ikke hvordan det ser ut.

### Id

```html
<p id="hovedbudskap">Ett bestemt avsnitt.</p>
```

```css
#hovedbudskap {
  background-color: #fdf2cc;
}
```

En id brukes bare én gang per side, og skrives med `#` i CSS. Til styling velger du nesten alltid klasse.

### `<div>` og `<span>`

```html
<div class="faktaboks">
  <h3>Overskrift</h3>
  <p>Innhold.</p>
</div>

<p>Turen koster <span class="pris">150 kroner</span>.</p>
```

`<div>` er en boks rundt flere elementer, `<span>` er en merkelapp rundt noen ord inne i en tekst. Begge betyr ingenting i seg selv — bruk dem bare når ingen semantisk element passer.

### Rammer

```css
.faktaboks {
  border: 3px solid #1a5276;
}

blockquote {
  border-left: 5px solid #1a5276;
}
```

`border` skrives som bredde, stil og farge. Stilene er `solid`, `dashed`, `dotted`, `double` og `none`. Du kan også bruke `border-left`, `border-right`, `border-top` og `border-bottom`.

### Bildestiler

```css
.galleribilde {
  width: 300px;
  border: 4px solid #ffffff;
}

.portrett {
  width: 150px;
  border-radius: 50%;
}
```

Sett bare `width` — da beholder bildet proporsjonene. `border-radius: 50%` gir et rundt bilde. Skal flere bilder se like ut, skal de ha samme klasse.

### Hvem vinner?

```text
element  <  klasse  <  id
```

Den sterkeste regelen vinner, uansett rekkefølge i fila. Rekkefølgen avgjør bare mellom regler som er like sterke.

---

## Oppgaver

### Del A — Enkle oppgaver

**Oppgave A1**

```html
<p class=".viktig">Husk prøven på fredag.</p>
```

```css
viktig {
  color: crimson;
}
```

Koden inneholder to feil — ett punktum for mye, og ett for lite. Rett dem, og sjekk at avsnittet blir rødt.

**Oppgave A2**

```text
┌────────────────────────────────┐
│   border: 2px dashed navy;     │
├────────────────────────────────┤
│ }                              │
├────────────────────────────────┤
│ .faktaboks {                   │
├────────────────────────────────┤
│   background-color: #eaf2f8;   │
└────────────────────────────────┘
```

Sett sammen kodebitene til en gyldig CSS-regel, og prøv den på en `<div class="faktaboks">` med en overskrift og et avsnitt inni.

**Oppgave A3**

```html
<h2 class="tema" id="start">Velkommen</h2>
```

```css
h2 { color: black; }
.tema { color: green; }
#start { color: purple; }
```

Les koden uten å bruke PC. Hvilken farge får overskriften? Hva blir fargen hvis du fjerner `id="start"` fra HTML-en? Og hvis du fjerner klassen også? Skriv ned alle tre svarene, og sjekk dem etterpå.

**Oppgave A4**

```css
.portrett {
  width: ...;
  border-radius: ...;
  border: ...;
}
```

Skriv ferdig regelen slik at den lager et rundt profilbilde på 120 piksler med en tynn hvit ramme. Prøv den på et bilde du velger selv.

**Oppgave A5**

Lag fila `galleri.html` med fire bilder. To av dem skal ha klassen `stor` (bredde 400 px), og to skal ha klassen `liten` (bredde 150 px). Alle fire skal ha samme ramme. Bruk bare **tre** CSS-regler til sammen.

**Oppgave A6**

Lag en side om et tema du velger selv, med minst tre avsnitt. Ett avsnitt skal være ingress med egen klasse, ett skal ha en advarselsklasse med ramme og bakgrunnsfarge, og ett skal være helt vanlig. Marker minst ett ord inne i et avsnitt med `<span>` og en klasse.

### Del B — Middels

**Oppgave B1**

> **🆕 Nytt stoff:** To selektorer etter hverandre med mellomrom mellom betyr «inni». Regelen
>
> `nav a {`
> `  color: white;`
> `}`
>
> gjelder alle lenker som ligger **inni** en `<nav>` — og ingen andre lenker på siden. Dette kalles en **etterkommerselektor**.

Lag en side med en meny i `<nav>` og minst én lenke i et vanlig avsnitt i `<main>`. Gi menylenkene en annen farge enn lenken i teksten, uten å bruke klasser i det hele tatt. Prøv deretter `main p` og `footer p` på samme måte.

**Oppgave B2**

> **🆕 Nytt stoff:** Skriver du selektorene **uten** mellomrom, betyr det «og». Regelen
>
> `p.viktig {`
> `  color: crimson;`
> `}`
>
> gjelder bare `<p>`-elementer som **også** har klassen `viktig` — ikke en `<h2 class="viktig">`. Med mellomrom («inni») og uten mellomrom («og») betyr altså helt forskjellige ting.

Lag en side der både et avsnitt og en overskrift har klassen `viktig`. Skriv én regel som treffer begge, og én som bare treffer avsnittet. Forklar forskjellen i en kommentar i CSS-fila.

**Oppgave B3**

```html
<div class="topp">
  <div class="tittel"><h1>Sykkelklubben</h1></div>
  <div class="meny">
    <ul><li><a href="index.html">Hjem</a></li></ul>
  </div>
</div>
<div class="innhold">
  <div class="del"><h2>Om oss</h2><p>Vi sykler.</p></div>
</div>
<div class="bunn"><p>post@sykkelklubben.no</p></div>
```

Denne siden har *divitis*. Skriv HTML-en om slik at hver `<div>` erstattes av det semantiske elementet som faktisk passer — se tilbake på hefte 4. Behold klassene der de fortsatt trengs, og fjern dem der elementnavnet nå holder som selektor.

**Oppgave B4**

Lag fila `filmkort.html` med tre «filmkort». Hvert kort er en `<section>` med klassen `kort`, og inneholder et plakatbilde, en `<h2>` med tittelen, og et avsnitt med en kort omtale. Alle kortene skal ha samme ramme og bakgrunnsfarge, og alle plakatbildene samme bredde og avrundede hjørner. Den filmen du liker best, skal i tillegg ha klassen `favoritt`, som gir kortet en tydeligere ramme.

**Oppgave B5**

Åpne et av nettstedene dine fra hefte 4 eller 5. Finn minst tre steder der en klasse ville gjort CSS-en bedre — for eksempel steder der du har kopiert nesten like regler, eller der du skulle ønske ett element så annerledes ut enn de andre. Legg inn klassene, og skriv en kommentar i CSS-fila om hva du ryddet opp i.

### Del C — Mer krevende

**Oppgave C1**

> **🆕 Nytt stoff:** Egenskapen `filter` legger en effekt oppå et bilde:
>
> `filter: grayscale(100%);` gjør bildet svart-hvitt
> `filter: blur(3px);` gjør det uskarpt
> `filter: brightness(50%);` gjør det mørkere
>
> Du kjenner igjen effektene fra `?grayscale` og `?blur` på picsum.photos i hefte 3 — forskjellen er at nå er det *din* CSS som gjør jobben, ikke nettstedet bildet kom fra.

Lag fila `effekter.html` som viser det **samme** bildet fire ganger: original, svart-hvitt, uskarpt og mørkere. Bruk fire klasser og samme `src` alle fire ganger. Kombiner til slutt to effekter i én regel (skriv dem etter hverandre med mellomrom mellom), og skriv i en kommentar hvilken kombinasjon du valgte.

**Oppgave C2**

Lag et «medlemskort» — fila `medlemskort.html` — som ser ut som noe en ekte nettside kunne vist:

- En `<section class="kort">` med ramme, bakgrunnsfarge og avrundede hjørner
- Et rundt portrettbilde (`border-radius: 50%`)
- Navn i en `<h2>`, rolle i et avsnitt med egen klasse
- Et sitat fra personen i en `<blockquote>` med `border-left`
- Kontaktinfo i en `<address>` med en klasse som gir mindre skrift

Lag deretter **tre** slike kort på samme side, med ulike personer. Alle tre skal bruke de samme klassene — du skal ikke skrive CSS-en tre ganger.

**Oppgave C3**

Undersøk selv, og skriv svarene som kommentarer i CSS-fila:

1. Gi et element klassen `stor` og klassen `liten`, der begge setter `font-size`. Hvilken vinner? Hva må du endre i CSS-fila for at den andre skal vinne i stedet?
2. Lag en regel `.kort p` og en regel `p.kort`. Lag HTML som viser at de treffer helt forskjellige ting.
3. Sett `border-radius: 50%` på et avsnitt med bakgrunnsfarge — altså ikke på et bilde. Hva skjer?
4. Sett `width: 300px` og `height: 300px` på et bilde som ikke er kvadratisk. Beskriv med egne ord hva som gikk galt.
5. Gi et bilde `border: 20px dotted crimson`. Hvor stor plass tar bildet nå på siden, sammenlignet med før? (Dette er en smakebit på hefte 7.)

---

*Hefte 6 av serien «Nettsider fra bunnen av». Neste hefte: Boksmodellen.*
