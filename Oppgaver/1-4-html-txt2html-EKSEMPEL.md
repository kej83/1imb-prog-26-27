# Fra tekst til nettside: eksempel med gjennomgang

*Til bruk i felles gjennomgang før elevene får tekstoppgavene. Bygger på hefte 1–4.*

---

## Om opplegget

Elevene får en helt uformatert tekst og skal bygge den som en nettside ved å velge riktig element til hver del. Det er ingen kodefeil å rette og ingen kode å skrive av — de skal **bestemme seg**, og kunne begrunne valgene.

Denne gjennomgangen er ment å tas i plenum, med koden på storskjerm, før elevene får sin egen tekst. Beregn 25–35 minutter. Poenget er ikke å rekke gjennom hele teksten, men å modellere spørsmålet elevene skal stille seg om hver eneste bit:

> **Hva ER denne biten?**

Ikke «hvordan skal den se ut», ikke «hva er lettest». Hva den *er*.

---

## Del 1: Teksten elevene ser

```text
Fotoklubben Blenderen

Skolens klubb for deg som liker å ta bilder

Meny: Hjem, Møter, Bli medlem

Om klubben

Fotoklubben Blenderen ble startet i 2019 av tre elever som var lei av
å fotografere alene. I dag er vi 24 medlemmer fordelt på alle tre
trinn. Vi holder til i mediarommet i andre etasje.

Vi bruker speilløse kameraer, men mobilkamera er like velkomment.
Det viktigste er at du har lyst til å lære.

[ BILDE: et kamera eller noen som fotograferer. Bildet skal ha en
  bildetekst som forteller hvor bildet er hentet fra. ]

Dette gjør vi på møtene

- Fotovandring i nærområdet
- Bildekritikk i plenum
- Enkel redigering
- Utstilling to ganger i året

Møteplan våren 2027

Dato        Tema              Sted
14. februar Portrett          Mediarommet
28. februar Portrett          Mediarommet
14. mars    Nattfotografering Ute
28. mars    Vinterferie - ingen møte

Leder Sara Nyland sier det slik: Vi bryr oss ikke om hvor dyrt
utstyret ditt er. Vi bryr oss om hva du ser.

Bli medlem

Medlemskap koster 150 kroner for hele skoleåret. Slik blir du medlem:

1. Møt opp på et hvilket som helst møte
2. Snakk med Sara eller en av de andre i styret
3. Betal kontingenten i kantina

Vil du se hva slags bilder vi lager? Vi legger ut bilder på
klubbens side hos Norsk Fotoforbund.

Fotoklubben Blenderen
blenderen@skolen-var.no
Mediarommet, 2. etasje
```

---

## Del 2: Gjennomgangen — spørsmål å stille klassen

Ta én bit om gangen. Still spørsmålet, la elevene svare, og skriv koden mens dere prater. Motstå fristelsen til å svare selv.

**1. «Vi har en tekst. Hva gjør vi aller først?»**

Svaret er ikke et element — det er `!` + `ENTER`, `lang="no"`, og en `<title>`. Spør: hva skal stå i `<title>`? (Fotoklubben Blenderen — den vises i fanen, ikke på siden.) Mange elever glemmer at tittelen i fanen og `<h1>` er to forskjellige ting.

**2. «De tre første linjene — klubbnavn, undertittel og meny. Hvor hører de hjemme?»**

Alt dette er sidens topp: `<header>`. Klubbnavnet er `<h1>`, undertittelen et `<p>`, og menyen en `<nav>` med `<ul>` og lenker.

Følg opp: *«Hvorfor ikke `<h2>` på undertittelen?»* Fordi den ikke starter et nytt tema — den beskriver klubben. Overskriftsnivåene er struktur, ikke størrelse.

**3. «Så kommer "Om klubben". Hva er det?»**

Starten på en ny del av innholdet, med egen overskrift → en `<section>` med `<h2>`. Og alt sammen ligger inni `<main>`.

Bruk gjerne 30 sekunder her på å tegne skjelettet på tavla: header — main — footer. Elevene som ikke har fått tak i hefte 4 ennå, henger seg ofte på nettopp her.

**4. «Bildet med bildeteksten?»**

`<figure>` med `<img>` og `<figcaption>`. Spør etter `alt`-teksten også — og la noen foreslå en. Diskuter forskjellen på `alt="kamera"` og `alt="Nærbilde av et speilløst kamera på et bord"`.

**5. «De fire tingene de gjør på møtene?»**

Punktliste, `<ul>`. Spør: *«Hvorfor ikke `<ol>`?»* Fordi rekkefølgen ikke betyr noe. Sammenlign med de tre trinnene for å bli medlem lenger ned — der betyr rekkefølgen alt, og da blir det `<ol>`. Dette paret er selve poenget med hele oppgavetypen.

**6. «Møteplanen. Hva er dette?»**

En tabell — rader og kolonner med data. Nå kommer de gode spørsmålene:

- Trenger den en overskrift som hører til tabellen? Ja → `<caption>Møteplan våren 2027</caption>`
- Hvor hører raden med `Dato Tema Sted` hjemme? I `<thead>`, med `<th>`-celler.
- **De to portrettmøtene har samme tema og sted.** Kan vi slå sammen? Ja → `rowspan="2"` på både `Portrett` og `Mediarommet`. Husk at raden under da skal ha *færre* celler.
- **Vinterferien har ingen tema og intet sted.** Hva gjør vi? `colspan="2"` over de to siste kolonnene.

La klassen telle kolonnene i hver rad høyt sammen. Dette er den beste 5-minutteren i hele gjennomgangen.

**7. «Sitatet fra Sara?»**

Her er det rom for uenighet, og det er bra. Sitatet står inne i en setning som forteller hvem som sier det → `<q>`. Men noen vil argumentere for `<blockquote>` fordi det er et helt utsagn. Begge kan forsvares — la elevene argumentere, og vær tydelig på at innledningen «Leder Sara Nyland sier det slik:» trekker i retning `<q>`.

**8. «Setningen om Norsk Fotoforbund?»**

En lenke. Spør: hva skal være lenketeksten? Ikke «klikk her» — men `Norsk Fotoforbund`. Og siden det er et annet nettsted: `https://` og `target="_blank"`.

**9. «De tre siste linjene?»**

Kontaktinfo nederst på siden → `<footer>` med `<address>`. Her lander alt fra hefte 2 og 4 på plass samtidig.

---

## Del 3: Ferdig løsning

```html
<!DOCTYPE html>
<html lang="no">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fotoklubben Blenderen</title>
</head>
<body>

  <header>
    <h1>Fotoklubben Blenderen</h1>
    <p>Skolens klubb for deg som liker å ta bilder</p>
    <nav>
      <ul>
        <li><a href="index.html">Hjem</a></li>
        <li><a href="moter.html">Møter</a></li>
        <li><a href="bli-medlem.html">Bli medlem</a></li>
      </ul>
    </nav>
  </header>

  <main>

    <section>
      <h2>Om klubben</h2>
      <p>Fotoklubben Blenderen ble startet i 2019 av tre elever som var
      lei av å fotografere alene. I dag er vi 24 medlemmer fordelt på
      alle tre trinn. Vi holder til i mediarommet i andre etasje.</p>
      <p>Vi bruker speilløse kameraer, men mobilkamera er like
      velkomment. Det viktigste er at du har lyst til å lære.</p>

      <figure>
        <img src="bilder/kamera.jpg"
             alt="Nærbilde av et speilløst kamera på et bord">
        <figcaption>Utstyret trenger ikke være dyrt.
        Foto: Unsplash.</figcaption>
      </figure>
    </section>

    <section>
      <h2>Dette gjør vi på møtene</h2>
      <ul>
        <li>Fotovandring i nærområdet</li>
        <li>Bildekritikk i plenum</li>
        <li>Enkel redigering</li>
        <li>Utstilling to ganger i året</li>
      </ul>
    </section>

    <section>
      <h2>Møteplan våren 2027</h2>
      <table>
        <caption>Møteplan våren 2027</caption>
        <thead>
          <tr>
            <th>Dato</th>
            <th>Tema</th>
            <th>Sted</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>14. februar</td>
            <td rowspan="2">Portrett</td>
            <td rowspan="2">Mediarommet</td>
          </tr>
          <tr>
            <td>28. februar</td>
          </tr>
          <tr>
            <td>14. mars</td>
            <td>Nattfotografering</td>
            <td>Ute</td>
          </tr>
          <tr>
            <td>28. mars</td>
            <td colspan="2">Vinterferie - ingen møte</td>
          </tr>
        </tbody>
      </table>
      <p>Leder Sara Nyland sier det slik: <q>Vi bryr oss ikke om hvor
      dyrt utstyret ditt er. Vi bryr oss om hva du ser.</q></p>
    </section>

    <section>
      <h2>Bli medlem</h2>
      <p>Medlemskap koster 150 kroner for hele skoleåret.
      Slik blir du medlem:</p>
      <ol>
        <li>Møt opp på et hvilket som helst møte</li>
        <li>Snakk med Sara eller en av de andre i styret</li>
        <li>Betal kontingenten i kantina</li>
      </ol>
      <p>Vil du se hva slags bilder vi lager? Vi legger ut bilder på
      klubbens side hos
      <a href="https://www.eksempel.no" target="_blank">Norsk
      Fotoforbund</a>.</p>
    </section>

  </main>

  <footer>
    <address>
      Fotoklubben Blenderen<br>
      blenderen@skolen-var.no<br>
      Mediarommet, 2. etasje
    </address>
  </footer>

</body>
</html>
```

**Merk deg tabellen:** raden for 28. februar har bare **én** celle, fordi de to `rowspan="2"`-cellene i raden over dekker resten. Dette er stedet elevene bommer.

---

## Del 4: Hva du kan forvente av feil

| Typisk feil | Hva du sier |
|---|---|
| Alt innhold rett i `<body>`, ingen `<main>` | «Hva ER denne biten en del av?» |
| `<h2>` brukt på undertittelen i toppen | Overskriftsnivå er struktur, ikke størrelse |
| Møteplanen laget med `<br>` i stedet for tabell | «Hva slags data er dette? Har den rader og kolonner?» |
| Raden for 28. februar får tre celler | La dem telle kolonner høyt, rad for rad |
| `alt="bilde"` eller ingen `alt` | «Les den høyt for meg. Hva ser jeg for meg?» |
| Lenketekst «klikk her» | «Hva står det på skiltet — og hvor peker det?» |
| `<section>` uten overskrift | En seksjon uten overskrift er en perm uten rygglapp |

---

## Del 5: Fasitoversikt for de tre tekstoppgavene

Elevene skal ikke ha disse.

### Tekst 1 (enkel) — Turgruppa

Forventede elementer: sideskjelett med `header` / `main` / `footer`, `h1` + undertittel i `<p>`, to `<section>` med `<h2>`, `<ul>` (utstyr), `<figure>` + `<figcaption>` + `<img alt>`, enkel tabell med `<caption>`, `<thead>` og `<tbody>`, `<address>` i footer. Ingen `<nav>` — teksten har ingen meny.

*Vurderingspunkt:* Er tabellen bygget som tabell, og ikke som en liste med mellomrom?

### Tekst 2 (middels) — Skolerevyen

Alt fra tekst 1, pluss: `<nav>` med tre lenker, `<ol>` (billettkjøp), tabell med `rowspan` (to forestillinger samme dag) og `colspan` (avlyst dag), `<blockquote>` (regissørens uttalelse), `<cite>` (revyens tittel), `<abbr>` (KKS), ekstern lenke med `target="_blank"`.

*Vurderingspunkt:* Får de `<ol>` og `<ul>` på riktig plass? Teksten inneholder begge, og valget er begrunnet i innholdet.

### Tekst 3 (vanskelig) — Skoleavisa

Alt over, pluss: to–tre `<article>` med hver sin `<h2>` og **egen** `<footer>` (byline), tabell med `<tfoot>`, `<th scope="row">`, både `colspan` og `rowspan`, `<audio>` eller `<video>`, `<q>` og `<blockquote>` brukt til hvert sitt formål, `<code>` med tegnkodene `&lt;` og `&gt;`.

*Vurderingspunkt 1:* Skjønner de forskjellen på `<section>` og `<article>`? Nyhetssakene er artikler — de kan klippes ut og gi mening alene.

*Vurderingspunkt 2:* Ser de at en `<article>` kan ha sin egen `<footer>` inni sidens `<footer>`-struktur? Dette er det eneste virkelig nye kravet i teksten, og det står ikke uttrykkelig — det må leses ut av at hver sak avsluttes med journalist og dato.

---

*Til serien «Nettsider fra bunnen av», hefte 1–4.*
