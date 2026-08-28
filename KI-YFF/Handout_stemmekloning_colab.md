# Stemmekloning i Google Colab — prosjekthefte

**Varighet:** 2–3 timer · **Arbeidsform:** grupper på 2 eller 3 · **Alt foregår i nettleseren**

---

## 1. Hva dere skal gjøre

Hver av dere tar opp sin egen stemme i 20 sekunder. Deretter får dere en KI-modell til å snakke
med den stemmen — og presser den så langt dere klarer: kan den gråte? Skrike? Hviske? Flørte?

Til slutt kommer det viktigste: **du skal ikke vurdere din egen klone.** Det klarer du ikke.
Du kjenner ikke din egen stemme utenfra — den høres helt annerledes ut på opptak enn inni hodet
ditt. Derfor er det gruppa di som dømmer klonen din, og du som dømmer deres.

**Dere lærer:**

- hvor lite lyd som skal til for å kopiere en stemme
- hvordan en modell kan skille *hvem som snakker* fra *hvilken følelse de har*
- hvorfor slike modeller trenger et skjermkort, og hva «en GPU i skyen» betyr
- hvor vanskelig det er å høre forskjell på ekte og syntetisk — og hvem som lettest lures

---

## 2. Grupper, roller og rotasjon

Gruppa deler **én** Colab-økt. Dere må altså vente på tur og bli enige. Det er meningen.

| Rolle | Ansvar |
|---|---|
| **Pilot** | Sitter ved tastaturet. Kjører cellene, laster opp lyd, trykker Generate. |
| **Regissør** | Bestemmer hva som skal prøves. Beskriver med ord hva som mangler. **Får ikke ta på tastaturet.** |
| **Lytter** | Vurderer resultatet med lukkede øyne. Fører loggen. |

**Rotér når det er en ny persons stemme som skal klones.** Den som eier stemmen som testes,
kan gjerne være pilot — men det er de andre som avgjør om resultatet er bra.

I en gruppe på to slår dere sammen regissør og lytter.

---

## 3. Spilleregler

Dere kloner **bare deres egen stemme**. Ingen andres — ikke lærere, ikke venner utenfor gruppa,
ikke familie, ikke kjendiser eller politikere.

Ett unntak, og det er en viktig del av oppgaven: dere kan låne hverandre **følelsesklipp**
(se punkt 7). Da låner dere bare måten noen roper eller gråter på, ikke stemmen deres. Spør
alltid først.

**Ellers gjelder:**

- ingenting publiseres eller deles utenfor klasserommet — ikke i gruppechat, ikke på TikTok
- ingen lager lyd der noen sier noe de ville tatt avstand fra: ingen sjikane, ingen trusler,
  ikke noe seksuelt
- alle filer slettes fra Colab og egne maskiner når oppgaven er vurdert
- sier noen «slett den», så slettes den. Uten diskusjon

---

## 4. Tidsplan

| Tid | Hva |
|---|---|
| 0–15 min | **Start Colab-installasjonen først** (punkt 5, steg 0–2). Den går i bakgrunnen |
| 15–35 min | Opptak av alles stemmer (punkt 6) |
| 35–45 min | Lenken opp, første klon (punkt 7) |
| 45–60 min | Fonetikk-verksted: få den til å si noe på norsk (punkt 8) |
| 60–105 min | Uttrykkslaboratoriet (punkt 9) |
| 105–130 min | Blindtest (punkt 10) |
| 130–150 min | Last ned, lever, slett, refleksjon |

---

## 5. Sett i gang Colab

1. Gå til [colab.research.google.com](https://colab.research.google.com) og logg inn.
2. **Fil → Last opp notatblokk** → velg `Stemmekloning_Colab.ipynb`.
3. **Kjøretid → Endre type kjøretid → T4 GPU → Lagre.** Uten dette virker ingenting.
4. Kjør cellene ovenfra og ned. Steg 1 og 2 tar til sammen 15–25 minutter.
5. **Gjør punkt 6 mens dere venter.** Ikke sitt og se på framdriftslinja.

### Hva skjer egentlig?

Modellen er altfor tung for en vanlig bærbar PC. I Colab kjører den på et skjermkort i et av
Googles datasentre, mens dere bare ser resultatet i nettleseren.

Appen kjører på en maskin som ikke har noen egen adresse på internett. Derfor starter vi den
med valget `--share`, som ber programmet lage en midlertidig, offentlig adresse. Den slutter på
`gradio.live` og virker i noen timer. Alle i gruppa kan åpne den samme lenken samtidig, fra hver
sin maskin. (Tjenester som ngrok gjør det samme, men krever konto og innlogging. Her er det
innebygd og gratis.)

### Tre advarsler

- **Alt slettes når økta lukkes.** Last ned lydfilene før dere går — siste celle i notatblokka.
- Colab kobler fra hvis fana står urørt lenge. La den stå åpen og aktiv.
- Gratis GPU er ikke garantert. Får dere ikke T4: prøv en annen Google-konto i gruppa.

---

## 6. Opptaket — og hvorfor du trenger en partner

Kvaliteten på klonen bestemmes nesten helt av dette opptaket. Og du er dårlig egnet til å
vurdere ditt eget.

**Jobb to og to:** én leser inn, den andre er lydtekniker. Lydteknikeren hører gjennom med
hodetelefoner og har vetorett. «Ta det på nytt» er et helt legitimt svar.

1. Finn det roligste stedet dere kan. Gangen, grupperom, trapp.
2. Ta opp med mobilen (Taleopptak / Voice Memos).
3. Hold mikrofonen 20–30 cm unna, litt på skrå — ikke rett foran munnen.
4. Les i **15–25 sekunder**, normalt tempo, normalt toneleie. Ikke skuespill.
5. Lydteknikeren sjekker: romklang? bakgrunnsprat? pesing på p-er? latter? → ta det på nytt.

**Tekst å lese inn** (nøytral med vilje — følelsene kommer senere):

> «I dag er det vanlig skoledag. Jeg heter … og jeg går i klasse … Utenfor er det grått, og jeg
> tenker på at helgen kommer altfor sakte. Til middag blir det antakelig noe kjedelig. Hvis jeg
> fikk velge helt fritt, ville jeg heller vært et helt annet sted akkurat nå.»

**Krav:** `.wav` eller `.m4a`, 15–25 sekunder, én stemme, ingen musikk.

Døp fila `fornavn_original.wav`. **Dette er den ene innleveringen din.**

---

## 7. Første klon

Når notatblokka har skrevet ut lenken, åpne den i en ny fane. Alle i gruppa kan åpne den samme
lenken samtidig.

1. **Referanselyd** — last opp opptaket ditt, eller ta det opp på nytt rett i appen med
   mikrofonknappen. Appen godtar også videofiler og henter ut lyden selv.
2. **Text** — skriv noe kort på engelsk til å begynne med, f.eks. `Hello, this is my voice.`
3. Trykk **Generate Speech** (den store røde knappen).

Lytt. Så gjør dere dette, i denne rekkefølgen:

- **Stemmeeieren gjetter først:** «på en skala fra 1 til 5, hvor likt er dette meg?»
- **Så sier de andre sitt.**
- Skriv ned begge tallene i loggen.

Dette gjentar dere for hver person i gruppa. Til slutt: **spriker tallene?** I hvilken retning?
Er folk strengere eller snillere mot sin egen klone enn andre er? Noter hva dere fant.

---

## 8. Fonetikk-verksted: få den til å snakke norsk

IndexTTS-2 er trent på **kinesisk, engelsk og japansk**. Norsk står ikke på lista. Modellen leser
norsk tekst med engelske uttaleregler, og `æ`, `ø` og `å` forstår den ikke i det hele tatt.

**Trikset:** skriv norsk med engelsk stavemåte. Dette er en gruppeoppgave — dere må prøve dere
fram, høre, og krangle litt om hvordan det skal skrives.

| Norsk | Skriv i stedet |
|---|---|
| Morna, Jens | `Moorna, Yenns` |
| Hei, hvordan går det? | `Hi, voordan gore day?` |
| Jeg heter Kari | `Yai hehter Kaari` |
| Tusen takk for i dag | `Toosen tuck for ee dahg` |
| Sju sjøsyke sjømenn | `Shoo shur-sooke shur-men` |

Grovregler: `j` → `y`, `æ` → `ae` eller `e`, `ø` → `ur` eller `u`, `å` → `aw` eller `oh`,
`kj`/`skj` → `sh`.

### Oppgave: Ordkonkurransen

Hver i gruppa velger **ett norsk ord** som dere tror blir umulig. Forslag: *kjøttkake, sjøhest,
øyeblikkelig, rødgrøt, tjueåtte, fjærkre*.

Alle prøver å skrive sitt ord fonetisk. Så bytter dere: **du skal skrive fonetisk for ordet en
annen valgte.** Generer begge versjoner. Hvem sin staving ble best?

Skriv ned de tre beste omskrivingene deres. Dere trenger dem i punkt 11.

### Bonus

Helt nederst i notatblokka ligger **Chatterbox**, en annen modell som faktisk støtter norsk. Den
har svakere følelseskontroll, men riktig uttale. Rekker dere begge deler: bruk IndexTTS-2 til
uttrykkene og Chatterbox til den norske innleveringsfila.

---

## 9. Uttrykkslaboratoriet

Nå skal dere finne ut hvor langt stemmen kan strekkes.

### Fire måter å styre følelsen på

I feltet **Emotion control**:

1. **Same as speaker voice** — følelsen hentes fra referanseopptaket ditt
2. **Use emotion reference audio** — dere laster opp et *eget* klipp som bare styrer følelsen
3. **Use emotion vector control** — åtte skyveknapper:
   `glad · sint · trist · redd · avsky · tungsindig · overrasket · rolig`
4. **Use emotion text description** — beskriv følelsen med ord, på engelsk:
   `whispering, secretive` eller `crying, voice breaking`

**Emotion alpha** styrer styrken. Rundt **0,6** gir som regel det mest naturlige. Skru den til
1,0 og hør hvor det ryker.

**Bruk Save preset.** Appen kan lagre hele oppsettet under et navn og hente det tilbake senere.
Når dere finner noe som funker, lagre det med én gang — da slipper dere å skrive alt om igjen
når dere skal sammenligne to varianter. Låser en generering seg, trykk **Cancel**.

### Hovedoppgaven: lån hverandres følelser

Metode 2 er den mest interessante, og den krever at dere samarbeider.

**Slik:** én i gruppa tar opp seg selv i 5–10 sekunder mens hun **roper sint**. Det klippet
brukes som *emotion reference* — men med **din** stemme som *speaker reference*.

Resultatet: din stemme, hennes sinne.

Gjør dette med minst tre følelsesklipp som dere lager sammen. Én tar opp gråt, én tar opp
hvisking, én tar opp latter eller panikk. **Alle bruker alles klipp.**

Så diskuterer dere:

- Blir det fortsatt tydelig *din* stemme, eller siver personligheten hennes inn?
- Hvem sitt raserianfall funker best som mal? Hvorfor akkurat det?
- Hva sier dette om hva modellen egentlig har lært å skille fra hverandre?

### Arbeidsdeling: metodedysten

Bli enige om **én tekst** og **én følelse** — for eksempel `I can't believe you did that.` med
følelsen *trist*.

Så tar dere hver deres metode:

| Person | Metode |
|---|---|
| A | Emotion vector — skru på skyveknappene |
| B | Emotion reference audio — ta opp noen som faktisk er lei seg |
| C (eller A igjen) | Emotion description text — `sad, on the verge of tears` |

Samme tekst, samme mål, tre veier. Spill av alle tre for gruppa. **Hvilken vant, og hvorfor?**
Skriv to setninger.

### Uttrykk å prøve

Velg minst **seks**, og minst to fra hver kolonne.

**Grunnfølelser**

- lei seg, med gråt i stemmen
- rasende, roper
- redd, i panikk
- overrasket / sjokkert
- skuffet
- lettet
- skadefro

**Roller og stiler**

- hvisker en hemmelighet
- flørtende
- sarkastisk / ironisk
- monoton nyhetsoppleser
- sportskommentator i mål-øyeblikket
- reklamestemme som selger noe
- streng lærer
- trøstende og omsorgsfull
- søvnig, gjesper
- stresset, snakker altfor fort
- høytidelig 17.-mai-tale
- nervøs, nøler, mange pauser
- eventyrforteller ved sengekanten
- skrytende og kjepphøy
- konspiratorisk, snakker lavt og fort
- robot uten følelser

### Tre regler

1. **Endre én ting av gangen.** Ellers vet dere ikke hva som gjorde forskjellen.
2. **Før logg.** Uten logg er dette bare tilfeldig klikking.
3. **Regissøren snakker, piloten trykker.** Regissøren sier «det høres ut som han later som han
   er sint» — piloten finner ut hvilken knapp det er.

### Lek: Følelsesgjettleken

Én lager et klipp med et hemmelig uttrykk fra lista. De andre gjetter. Riktig gjett = modellen
gjorde jobben. Feil gjett = finn ut hva som manglet, og prøv igjen.

---

## 10. Blindtest

### Test A — Kjenner du din egen stemme?

Piloten lager fem klipp med **din** stemme: to er utdrag av det ekte opptaket, tre er klonet.
Bland rekkefølgen slik at du ikke vet hva som er hva.

**Du gjetter først, med lukkede øyne.** Så gjetter de andre i gruppa.

| | Antall riktige av 5 |
|---|---|
| Stemmeeieren selv | |
| Gruppemedlem 2 | |
| Gruppemedlem 3 | |

Gjenta for hver person i gruppa.

### Test B — Betyr det noe hvor godt du kjenner personen?

Slå dere sammen med en annen gruppe og kjør samme test på hverandres klipp. Nå hører folk som
knapt kjenner stemmeeieren.

**Hvem tar mest feil: den som eier stemmen, en venn, eller en fremmed?** Diskuter hva svaret
betyr for hvem som er lettest å lure i virkeligheten.

### Vurderingsskjema

Fyll ut for de tre beste klippene deres:

| | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| Likhet til den ekte stemmen | | | | | |
| Naturlig taleflyt | | | | | |
| Følelsen er tydelig | | | | | |
| Uttalen er forståelig | | | | | |

Skriv én setning: **hva var det som avslørte at det ikke var ekte?**

---

## 11. Logg

Fyll ut underveis, ikke til slutt.

| # | Hvem sin stemme | Metode | Innstillinger | Tekst | Eierens karakter | De andres karakter | Hva var galt? |
|---|---|---|---|---|---|---|---|
| 1 | | | | | | | |
| 2 | | | | | | | |
| 3 | | | | | | | |
| 4 | | | | | | | |
| 5 | | | | | | | |
| 6 | | | | | | | |

---

## 12. Innlevering

**Hver elev leverer to lydfiler:**

1. `fornavn_original.wav` — ditt eget referanseopptak
2. `fornavn_klonet.wav` — **30 sekunder** der din klonede stemme snakker

**Krav til 30-sekundersfila:**

- minst **to forskjellige uttrykk** fra lista i punkt 9
- minst ett av dem laget med et **følelsesklipp fra en annen i gruppa**
- klipp gjerne sammen flere korte genereringer

**Gruppa leverer i tillegg:** loggen, vurderingsskjemaet, de tre beste fonetiske omskrivingene,
og svaret på metodedysten.

---

## 13. Refleksjon

Svar kort skriftlig, som gruppe:

1. Hvor mange sekunder lyd trengte dere egentlig? Hva sier det om hvor lett det er å klone
   stemmen til hvem som helst som legger ut en story?
2. Var stemmeeieren en bedre eller dårligere dommer over sin egen klone enn de andre? Hva tror
   dere det kommer av?
3. Modellen kan gi *din* stemme *en annens* følelser. Hva betyr det at disse to tingene kan
   skilles fra hverandre?
4. Chatterbox legger et usynlig vannmerke i alt den lager. IndexTTS-2 gjør det ikke. Burde
   merking være påbudt? Hvem skulle håndhevet det?
5. Beskriv en situasjon der noen kunne blitt lurt av dette. Hva ville avslørt det?
6. Nevn to gode bruksområder.
7. Hvem eier stemmen din, juridisk sett? Hva mener dere at svaret *burde* vært?

---

## 14. Feilsøking

| Problem | Sannsynlig årsak | Løsning |
|---|---|---|
| Klonen høres ut som en helt annen person | Dårlig referanseopptak | Nesten alltid dette. Ta opp på nytt |
| Uttalen er helt gal | Norsk tekst med æøå | Skriv om fonetisk, se punkt 8 |
| Stopper midt i setningen | For lang tekst i ett jafs | Del opp i korte setninger |
| Følelsen høres påtatt ut | Emotion alpha for høy | Prøv 0,5–0,7 i stedet for 1,0 |
| `Model directory ... does not exist` | Modellnedlastingen ble ikke ferdig | Kjør Steg 2 i notatblokka om igjen |
| `CUDA out of memory` | For mye tekst om gangen | Kortere tekst, sjekk at FP16 er på |
| Lenken sier «Bad Gateway» | Appen er ikke ferdig startet | Vent ett minutt, oppdater sida |
| Ingen GPU tilgjengelig | Gratiskvoten er brukt opp | Bytt til en annen Google-konto i gruppa |
| Alt forsvant | Colab-økta ble lukket | Filene må lastes ned før dere går |

---

## Vedlegg A — Gruppeavtale

*Fylles ut for hånd og leveres sammen med lydfilene.*

---

Vi i gruppa ______________________________________________________ avtaler at:

- vi kloner bare våre egne stemmer
- vi kan låne hverandre følelsesklipp, men bare etter å ha spurt hver gang
- ingenting av det vi lager, deles utenfor klasserommet
- ingen av oss lager lyd der en annen sier noe hun eller han ikke vil si
- hvem som helst kan når som helst si «slett den», og da slettes den umiddelbart
- alle filer slettes fra Colab og fra mobiler og PC-er når oppgaven er vurdert

Sted og dato: ______________________

Signaturer: ______________________  ______________________  ______________________

---

## Vedlegg B — Hva gjør koden i notatblokka?

Les alltid et skript før du kjører det. Det er en god vane. Her er hva cellene gjør:

| Kommando | Hva den gjør |
|---|---|
| `nvidia-smi` | Viser hvilket skjermkort Google har gitt dere |
| `git clone <adresse>` | Laster ned kildekoden fra GitHub |
| `pip install uv` | Installerer `uv`, en mye raskere erstatter for `pip` |
| `uv venv --python 3.10` | Lager et isolert Python-miljø med akkurat den versjonen appen krever |
| `uv pip install -r requirements...` | Installerer alle Python-pakkene programmet trenger |
| `snapshot_download(...)` | Laster ned selve modellfilene, flere gigabyte |
| `subprocess.Popen([... webui.py ...])` | Starter appen i bakgrunnen |
| `--share` | Ber appen lage den midlertidige, offentlige `gradio.live`-adressen |
| `files.download(...)` | Sender zip-fila med lyden ned til maskinen din |

**Stemmekloning er ikke én modell, men fem som samarbeider:** hovedmodellen som lager talen,
`w2v-bert-2.0` som hører hva som blir sagt, `MaskGCT` som koder lyd om til tall, `campplus` som
kjenner igjen hvem som snakker, og `BigVGAN` som gjør tallene om til hørbar lyd igjen.
