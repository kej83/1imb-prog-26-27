# Kapittel 3: Lenker, bilder og medier

*HTML og CSS — hefte 3 i serien «Nettsider fra bunnen av». Bygger på hefte 1 og 2.*

---

## Slik jobber du med dette heftet

Heftet følger arbeidsmåten **PRIMM**, med stegene **[Predict]** (les koden og forutsi hvordan siden ser ut), **[Run]** (skriv av og se resultatet), **[Investigate]** (gjør små endringer og undersøk), **[Modify]** (utvid siden) og **[Make]** (lag din helt egen side — i oppgavene bakerst). Noen oppgaver i del B og C starter med en boks merket **Nytt stoff** — der lærer du noe nytt som du tar i bruk i den oppgaven.

### Husk fra hefte 1 og 2

Ny HTML-fil: `!` + `ENTER` gir malen, sett `lang="no"`, og skriv innholdet mellom `<body>` og `</body>`. Lagre med `CTRL` + `S`, og se resultatet med **Show Preview** eller **Go Live**. Et **attributt** er ekstra informasjon i en åpnetagg, som `lang="no"` — i dette heftet kommer du til å bruke mange attributter.

> **💡 Tips:** Lag en ny mappe `nettside3` for dette heftet, og åpne den i VS Code med **File → Open Folder**. I dette heftet betyr mappa ekstra mye — filene dine skal snakke sammen!

> **⚠️ Merk:** Flere av eksemplene i heftet henter bilder fra nettet. Da må maskinen din være på internett for at bildene skal vises.

---

## 3.1 Lenker til andre nettsteder

```html
<body>
  <h1>Mine favorittnettsteder</h1>
  <p>Jeg sjekker nyheter på <a href="https://www.nrk.no">NRK</a>
  nesten hver dag.</p>
</body>
```

Lenker er selve limet på nettet — det er de som gjør at du kan klikke deg fra side til side. En lenke lages med elementet `<a>` (*anchor*):

| Del | Eksempel | Forklaring |
|---|---|---|
| Taggen | `<a>` ... `</a>` | Selve lenken |
| Attributtet `href` | `href="https://www.nrk.no"` | Adressen lenken går til |
| Innholdet | `NRK` | Lenketeksten — det du klikker på |

1. Les koden. Hvilket ord på siden blir klikkbart? **[Predict]**
2. Lag fila `index.html`, skriv av koden, og se på resultatet. Åpne siden med **Go Live**, og prøv lenken. **[Run]**
3. Endre lenketeksten til `nyhetene` uten å endre `href`. Hva er forskjellen på det som vises, og dit du kommer? **[Investigate]**
4. Hva skjer hvis du fjerner hele `href`-attributtet? Se på ordet på siden. Legg attributtet tilbake. **[Investigate]**
5. Legg til en punktliste med lenker til tre nettsteder du bruker ofte — hvert listepunkt inneholder én lenke. **[Modify]**

> **⚠️ Merk:** Adresser til andre nettsteder må starte med `https://`. Skriver du bare `href="www.nrk.no"`, tror nettleseren at du mener en fil i din egen mappe — og lenken slutter å virke.

> **💡 Tips:** Test lenker med **Go Live** i nettleseren. Forhåndsvisningen inne i VS Code er fin til å se på siden, men til å klikke seg rundt er nettleseren best.

---

## 3.2 Flere sider — ditt første nettsted

```html
<body>
  <h1>Om meg</h1>
  <p>Jeg går på vg1 og lærer HTML.</p>
  <p><a href="index.html">Tilbake til forsiden</a></p>
</body>
```

Et nettsted er flere sider som er lenket sammen. Nå lager vi side nummer to:

1. Lag en ny fil `om-meg.html` i samme mappe som `index.html`, og skriv av koden ovenfor (husk malen først!). **[Run]**
2. Se på `href` i koden: her står det bare et filnavn, ingen `https://`. Hvorfor tror du det holder? **[Predict]**
3. Åpne `index.html`, og legg til lenken `<a href="om-meg.html">Om meg</a>` i et avsnitt. Åpne siden med **Go Live**, og klikk deg frem og tilbake mellom de to sidene. **[Run]**
4. Endre `href` til `om-meg.htm` (uten l), og prøv lenken på nytt. Hva skjer? Rett feilen etterpå. **[Investigate]**

En lenke til en fil i samme mappe skriver du bare med filnavnet. Da spiller det ingen rolle hvor nettstedet ligger — på din maskin i dag, på en server i morgen. Lenkene virker uansett.

5. Lag en tredje side, `hobby.html`, om noe du liker å drive med. Legg til en meny øverst på **alle tre** sidene: en punktliste der hvert punkt er en lenke til én av sidene. **[Modify]**

> **💡 Tips:** Filnavnet i `href` må stemme *nøyaktig* — store og små bokstaver kan gjøre forskjell den dagen nettstedet legges ut på nett. Enda en grunn til regelen fra hefte 1: små bokstaver, ingen mellomrom, ingen æøå i filnavn.

---

## 3.3 Bilder

```html
<body>
  <h1>Dagens bilde</h1>
  <img src="https://picsum.photos/400/250" alt="Et tilfeldig fotografi">
</body>
```

Endelig — bilder! Et bilde settes inn med den tomme taggen `<img>` og to viktige attributter:

| Attributt | Gjør |
|---|---|
| `src` | *source* — hvor bildet hentes fra: en adresse på nettet, eller en fil i mappa di |
| `alt` | *alternativ tekst* — beskriver bildet med ord |

Adressen `picsum.photos` er en tjeneste som gir deg et **tilfeldig fotografi** i akkurat den størrelsen du ber om. Du skriver ønsket bredde og høyde rett inn i adressen: `https://picsum.photos/400/250` gir et bilde som er 400 piksler bredt og 250 høyt. Vil du ha et kvadratisk bilde, holder det med ett tall: `https://picsum.photos/300`.

1. Les koden. Hva slags bilde får du? (Lurespørsmål!) **[Predict]**
2. Lag fila `bilder.html`, skriv av koden, og se på resultatet. **[Run]**
3. Last siden på nytt (trykk på oppdater-knappen i nettleseren). Fikk du det samme bildet? **[Investigate]**
4. Endre tallene i adressen til `800/200`, og se på resultatet. Prøv også `https://picsum.photos/250` — hva slags form får bildet? **[Investigate]**
5. Legg til to bilder til i ulike størrelser, hvert med sin egen `alt`-tekst. **[Modify]**

### Egne og nedlastede bilder

Bilder fra nettet er kjekt, men oftest vil du bruke *egne* bilder. Da skal bildefila ligge i mappa til nettstedet ditt — ryddigst i en egen undermappe:

1. Lag en ny mappe `bilder` inne i `nettside3` (bruk **New Folder**-ikonet i utforskeren i VS Code).
2. Finn et bilde du har lov til å bruke, og få det inn i mappa. To måter:
   - **Eget bilde:** Kopier en bildefil du har på maskinen (eller overfør et mobilbilde), og lim den inn i `bilder`-mappa. Du kan også dra fila rett inn i utforskeren i VS Code.
   - **Nedlastet bilde:** Finn et gratisbilde på nettet, høyreklikk på det, velg **Lagre bilde som ...**, og lagre det i `bilder`-mappa. Gi fila et ryddig navn, som `fjelltur.jpg`.
3. Sett inn bildet med en relativ filsti — mappenavn, skråstrek, filnavn: **[Run]**

```html
<img src="bilder/fjelltur.jpg" alt="Utsikt fra fjelltopp i solnedgang">
```

4. Skriv `src` med feil filnavn med vilje, og se på siden. Hva vises i stedet for bildet? Der ser du hvorfor `alt`-teksten aldri skal droppes! Rett feilen. **[Investigate]**

`alt`-teksten vises når bildet ikke kan lastes — og den leses høyt for blinde og svaksynte som bruker skjermleser. En god `alt`-tekst beskriver det bildet viser: `alt="To elever spiller sjakk i kantina"`, ikke `alt="bilde1"`.

> **⚠️ Merk:** Du kan ikke bruke et hvilket som helst bilde fra nettet — bilder har **opphavsrett**. Bruk egne bilder, eller last ned fra nettsteder med gratis bilder (søk etter «royalty free images»). Til skolearbeid er det også lurt å notere hvor bildet kom fra.

---

## 3.4 Bilder med bildetekst: figure og figcaption

```html
<figure>
  <img src="https://picsum.photos/500/300" alt="Et tilfeldig fotografi">
  <figcaption>Figur 1: Dagens tilfeldige bilde.</figcaption>
</figure>
```

I aviser og fagbøker har bilder nesten alltid en bildetekst. HTML har et eget par for akkurat det: `<figure>` pakker inn bildet, og `<figcaption>` er bildeteksten.

1. Les koden. Hvor vil bildeteksten havne? **[Predict]**
2. Legg koden inn nederst i `bilder.html`, og se på resultatet. **[Run]**
3. Flytt `<figcaption>`-elementet slik at det står *før* `<img>`, og se hva som skjer med plasseringen. Flytt det tilbake. **[Investigate]**
4. Gjør om ett av dine egne bilder fra 3.3 til en `<figure>` med en beskrivende bildetekst. **[Modify]**

> **💡 Tips:** Bruk `<figure>` når bildet har en tekst knyttet til seg — og en enkel `<img>` når det ikke har det. Igjen handler HTML om hva innholdet **er**.

---

## 3.5 Lyd

```html
<body>
  <h1>Lydsiden min</h1>
  <p>Hør på dette:</p>
  <audio controls src="lyd/opptak.mp3"></audio>
</body>
```

Nettsider kan også spille av lyd. Elementet `<audio>` lager en liten avspiller med play-knapp og volum.

Først trenger du en lydfil i formatet `.mp3`:

1. Lag mappa `lyd` inne i `nettside3`.
2. Skaff en mp3-fil, og legg den i mappa. Forslag: spill inn en kort lyd med mobilen og overfør den, last ned et gratis lydklipp fra nettet, eller spør læreren om en fil klassen kan bruke. Kall fila `opptak.mp3` (eller tilpass koden til ditt filnavn).
3. Lag fila `lydside.html` med koden ovenfor, og trykk på play. **[Run]**
4. Fjern attributtet `controls`, lagre, og se på siden. Hvor ble avspilleren av? Legg attributtet tilbake. **[Investigate]**

La du merke til noe nytt? `controls` er et attributt **uten verdi** — det står ikke noe `="..."` etter. Slike attributter virker som en av/på-bryter: står ordet der, er funksjonen på.

5. Legg til en lydfil til, med en liten overskrift over hver avspiller. **[Modify]**

---

## 3.6 Video

```html
<video controls width="400" src="video/klipp.mp4"></video>
```

Video fungerer nesten akkurat som lyd — elementet heter `<video>`, og fila bør være i formatet `.mp4`. Attributtet `width` bestemmer hvor bred avspilleren skal være, målt i piksler.

1. Lag mappa `video`, og legg en mp4-fil der. Forslag: film tre sekunder med mobilen og overfør fila, eller bruk et gratis videoklipp fra nettet.
2. Lag fila `videoside.html`, sett inn koden (tilpass filnavnet), og spill av videoen. **[Run]**
3. Endre `width="400"` til `width="200"`, og se på resultatet. Hva skjer hvis du fjerner hele attributtet? Sett det tilbake. **[Investigate]**

### Filformater — en oversikt

| Type | Vanlige formater | Kommentar |
|---|---|---|
| Bilder | `.jpg`, `.png`, `.svg`, `.gif` | `.jpg` for foto, `.png` for grafikk, `.svg` for ikoner |
| Lyd | `.mp3` | Trygt valg som virker overalt |
| Video | `.mp4` | Trygt valg som virker overalt |

> **🐞 Når noe går galt:** Vises ikke bildet, lyden eller videoen? Sjekk i denne rekkefølgen: 1) Er filstien i `src` riktig — mappenavn, skråstrek, filnavn? 2) Er filnavnet stavet nøyaktig likt, med riktig endelse? 3) Ligger fila faktisk i mappa? Se i utforskeren i VS Code.

---

## Sammendrag

I dette heftet ble nettsiden din til et nettsted — med lenker, bilder, lyd og video.

### Lenker

```html
<a href="https://www.nrk.no">Til et annet nettsted</a>
<a href="om-meg.html">Til en annen side i samme mappe</a>
```

Eksterne lenker trenger hele adressen med `https://`. Lenker til egne sider bruker bare filnavnet.

### Bilder

```html
<img src="https://picsum.photos/400/250" alt="Et tilfeldig fotografi">
<img src="bilder/fjelltur.jpg" alt="Utsikt fra fjelltopp">
<figure>
  <img src="bilder/fjelltur.jpg" alt="Utsikt fra fjelltopp">
  <figcaption>Fra toppturen i høstferien.</figcaption>
</figure>
```

`src` kan peke til en adresse på nettet eller en fil i mappa di. `alt` beskriver bildet, og vises når bildet ikke lastes. `picsum.photos` gir tilfeldige bilder: bredde og høyde rett i adressen (`/400/250`), ett tall gir kvadrat (`/300`). Egne og nedlastede bilder legges i en `bilder`-mappe og hentes med relativ filsti. Husk opphavsretten!

### Lyd og video

```html
<audio controls src="lyd/opptak.mp3"></audio>
<video controls width="400" src="video/klipp.mp4"></video>
```

`controls` er et attributt uten verdi — en av/på-bryter som gir avspilleren knapper. `width` setter bredden i piksler.

### Mappestruktur

```text
nettside3/
├── index.html
├── om-meg.html
├── hobby.html
├── bilder/
│   └── fjelltur.jpg
├── lyd/
│   └── opptak.mp3
└── video/
    └── klipp.mp4
```

---

## Oppgaver

> **💡 Tips:** Jobb videre i mappa `nettside3`, så kan oppgavene gjenbruke bildene og menyene dine. Husk: nytt stoff i del B og C står i egne bokser.

### Del A — Enkle oppgaver

**Oppgave A1**

```html
<p>Sjekk ut <a href="www.nrk.no">NRK</a> for nyheter.</p>
<img scr="https://picsum.photos/300/200">
```

Koden inneholder tre feil: én i lenken og to i bildet (en skrivefeil, og noe viktig som mangler helt). Finn og rett feilene, og sjekk at både lenken og bildet virker.

**Oppgave A2**

```text
┌───────────────────────────────────────────────────────┐
│   <figcaption>Min favorittplass i byen.</figcaption>  │
├───────────────────────────────────────────────────────┤
│ <h1>Fotoalbum</h1>                                    │
├───────────────────────────────────────────────────────┤
│ </figure>                                             │
├───────────────────────────────────────────────────────┤
│   <img src="https://picsum.photos/400" alt="Foto">    │
├───────────────────────────────────────────────────────┤
│ <figure>                                              │
└───────────────────────────────────────────────────────┘
```

Sett sammen kodebitene i riktig rekkefølge, slik at siden viser en overskrift og et bilde med bildetekst under. Skriv koden inn i en ny fil, og sjekk resultatet.

**Oppgave A3**

```html
<h1>Gjett!</h1>
<img src="https://picsum.photos/200" alt="Bilde A">
<img src="https://picsum.photos/200/100" alt="Bilde B">
<p><a href="index.html">Hjem</a></p>
```

Les koden, og tegn på papir hvordan siden vil se ut: hvilken form får hvert av bildene, og hvor havner lenken? Skriv deretter av koden, og sjekk svaret ditt.

**Oppgave A4**

```html
<h1>Lenkesamlingen min</h1>
<ul>
  <li><a href="...">...</a></li>
  <li><a href="...">...</a></li>
  <li><a href="...">...</a></li>
</ul>
```

Fyll inn skjelettet med lenker til tre nettsteder du kan anbefale. Lenketeksten skal være navnet på nettstedet — ikke adressen.

**Oppgave A5**

Lag fila `tilfeldig.html` med overskriften `Tilfeldig kunstgalleri` og tre bilder fra picsum.photos i tre forskjellige størrelser: ett kvadratisk, ett bredt og ett høyt. Alle skal ha `alt`-tekst. Last siden på nytt et par ganger og nyt utstillingen!

**Oppgave A6**

Lag fila `minplass.html` om et sted du liker deg: en `<h1>`, et avsnitt, og et eget eller nedlastet bilde i en `<figure>` med bildetekst i `<figcaption>`. Legg bildefila i `bilder`-mappa, og skriv i bildeteksten hvor bildet kommer fra.

### Del B — Middels

**Oppgave B1**

> **🆕 Nytt stoff:** Vanligvis åpnes en lenke i samme fane. Med attributtet `target="_blank"` åpnes den i en **ny** fane: `<a href="https://www.nrk.no" target="_blank">NRK</a>`. Det brukes gjerne på eksterne lenker, så besøkeren ikke mister siden din.

Åpne `index.html` fra innlæringsdelen. Sørg for at alle lenkene til *andre nettsteder* åpnes i ny fane, mens lenkene til dine *egne* sider fortsatt åpnes i samme fane. Test alle lenkene med **Go Live**, og forklar med én setning hvorfor denne forskjellen er fornuftig.

**Oppgave B2**

> **🆕 Nytt stoff:** picsum.photos kan også gi deg det **samme** bildet hver gang. Legg `seed/` og et valgfritt ord inn i adressen: `https://picsum.photos/seed/katt/300/200`. Samme ord gir samme bilde — bytt ord, og du får et annet. Dessuten kan et bilde gjøres om til en lenke ved å pakke `<img>` inn i `<a>`.

Lag fila `galleri.html` med tre små bilder (200 × 150) som bruker hver sin seed. Hvert bilde skal være en lenke til en **stor** utgave av *det samme* bildet (800 × 600 — samme seed!). Test at klikk på hvert lite bilde åpner riktig storversjon.

**Oppgave B3**

Utvid nettstedet ditt fra 3.2 med en fjerde side, `album.html`, med minst tre bilder i `<figure>` med bildetekster — egne, nedlastede eller fra picsum. Oppdater menyen på **alle** sidene slik at `album.html` er med. Sjekk at du kan klikke deg til alle sidene fra alle sidene.

**Oppgave B4**

Lag fila `lydquiz.html` — en gjettelek med lyd: minst to `<audio>`-avspillere med hver sin nummererte overskrift (`Lyd 1`, `Lyd 2`), der besøkeren skal gjette hva som lager lyden. Fasiten skal stå nederst på siden — skjult i en kommentar. Bruk lydfiler du spiller inn selv eller laster ned gratis.

**Oppgave B5**

```text
Overskrift: Slik lastet jeg ned et bilde
En nummerert liste som beskriver alle stegene, fra du
   fant bildet til det virket på siden din.
Bildet selv, vist i en figure med bildetekst som
   forteller hvor bildet kommer fra.
En avsluttende setning der ordet opphavsrett er uthevet
   som viktig.
```

Lag fila `nedlasting.html` ved å følge beskrivelsen ovenfor. Velg selv riktige HTML-elementer for hver del.

### Del C — Mer krevende

**Oppgave C1**

> **🆕 Nytt stoff:** picsum.photos har flere triks. Legg `?grayscale` til på slutten av adressen for svart-hvitt, eller `?blur=5` for uskarphet (tall fra 1 til 10): `https://picsum.photos/seed/fjell/400/250?grayscale`

Lag fila `effekter.html` som viser **samme** bilde (samme seed, 400 × 250) tre ganger side om side: originalen, i svart-hvitt, og uskarpt. Hver utgave skal stå i sin egen `<figure>` med en bildetekst som forteller hvilken effekt som er brukt. Eksperimenter med ulike blur-tall, og skriv i en kommentar hvilket tall du landet på.

**Oppgave C2**

> **🆕 Nytt stoff:** `<video>` har flere av/på-attributter: `autoplay` starter videoen automatisk, `muted` skrur av lyden, og `loop` starter videoen på nytt når den er ferdig. Nettlesere nekter som regel å autostarte video **med** lyd — derfor brukes `autoplay` og `muted` nesten alltid sammen: `<video autoplay muted loop width="400" src="video/klipp.mp4"></video>`

Lag fila `stemning.html`: en side med en kort video som starter av seg selv, uten lyd, og går i evig løkke — som en levende bakgrunn. Under videoen: en overskrift og et avsnitt som passer til stemningen i klippet. Skriv til slutt en kommentar i koden: Hvorfor tror du nettlesere nekter å autostarte video med lyd?

**Oppgave C3**

Bygg et komplett mininettsted i en **ny mappe** `fotoalbum` om et valgfritt tema (et sted, en hobby, et dyr). Tegn opp strukturen på papir før du koder. Krav:

- Minst tre sider: `index.html`, en albumside og en «om»-side
- Meny med lenker på alle sidene, og minst én ekstern lenke som åpnes i ny fane
- Undermappa `bilder` med minst tre bilder (egne eller nedlastede) — alle vist i `<figure>` med bildetekst og god `alt`-tekst
- Minst én lyd **eller** video
- En `<address>` nederst på forsiden
- Alle filnavn etter reglene: små bokstaver, ingen mellomrom, ingen æøå

**Oppgave C4**

Undersøk selv, og skriv svarene som kommentarer i fila `eksperiment3.html`:

1. Sett inn et bilde fra picsum med størrelse `2000/300`. Hva skjer med siden? (Dette problemet løser vi med CSS i hefte 8!)
2. Lag en lenke til en fil som ikke finnes, åpne siden med **Go Live**, og klikk på lenken. Hva slags side kommer du til? Hva betyr tallet du ser?
3. Kan en `<figure>` inneholde to `<img>` og én felles `<figcaption>`? Prøv!
4. Pakk et helt avsnitt — både tekst og et bilde — inn i én `<a>`-lenke. Hva blir klikkbart?

---

*Hefte 3 av serien «Nettsider fra bunnen av». Neste hefte: Struktur og semantikk.*
