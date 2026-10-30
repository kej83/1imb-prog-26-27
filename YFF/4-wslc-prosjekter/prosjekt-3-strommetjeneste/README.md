# Prosjekt 3 – Egen strømmetjeneste med Jellyfin

[← Tilbake til hovedsiden](../README.md) · [Jukselapp](../jukselapp.md) · [Feilsøking](../feilsoking.md)

Du lager ditt eget «Netflix» som kjører på PC-en din, og fyller det med egne filmer og medieproduksjoner. Du lager plakater, beskrivelser og undertekster, og setter opp brukere som får se forskjellig innhold. Til slutt strømmer du til mobilen og ser hva som skjer når videoen må gjøres om underveis.

**GitHub-prosjekt:** [jellyfin/jellyfin](https://github.com/jellyfin/jellyfin)

| | |
| --- | --- |
| **Vanskelighetsgrad** | ★☆☆ Lett – én container. Et fint første prosjekt |
| **Du lærer** | Porter, volumer, å koble inn Windows-mapper, filstruktur og metadata, brukere og tilganger, transkoding |
| **Resultat** | En strømmetjeneste med egne produksjoner, tre brukere med ulik tilgang, og avspilling på mobil |
| **Før du starter** | Du må ha gjort alt i [Kom i gang](../00-kom-i-gang.md) |

### Sjekkliste

- [ ] Del A – Samle og organiser mediene
- [ ] Del B – Start Jellyfin
- [ ] Del C – Sett opp biblioteker
- [ ] Del D – Gjør innholdet ditt proft: plakater, beskrivelser og undertekster
- [ ] Del E – Brukere og tilgang
- [ ] Del F – Strøm til mobilen, og undersøk transkoding
- [ ] Del G – Drift: startskript og omstart
- [ ] Refleksjon og levering

---

## Del A – Samle og organiser mediene

Jellyfin forstår innholdet ditt ut fra **mappe- og filnavn**. God struktur fra starten sparer deg for mye arbeid.

### A1 – Lag mappestrukturen

```powershell
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\Videos\Jellyfin\Filmer"
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\Videos\Jellyfin\Musikk"
New-Item -ItemType Directory -Force -Path "$env:USERPROFILE\Videos\Jellyfin\Vare produksjoner"
```

### A2 – Finn innhold du har lov til å bruke

- **Egne produksjoner:** videoer, kortfilmer, animasjoner og musikk fra mediefagene
- **Fritt lisensierte filmer:** Blender Foundation har laget kortfilmer med lisensen CC BY, som du kan bruke fritt bare du krediterer dem. For eksempel [Big Buck Bunny](https://peach.blender.org/download/), [Sintel](https://durian.blender.org/download/) og [Tears of Steel](https://mango.blender.org/download/).

> **Skolens wifi:** Velg 720p- eller 1080p-versjonen, ikke 4K. Last ned én film om gangen.

### A3 – Navngi riktig

Jellyfin vil ha hver film i sin egen mappe, med tittel og årstall:

```
Videos\Jellyfin\
├── Filmer\
│   ├── Big Buck Bunny (2008)\
│   │   └── Big Buck Bunny (2008).mp4
│   └── Sintel (2010)\
│       ├── Sintel (2010).mkv
│       └── Sintel (2010).no.srt        ← norsk undertekst
├── Musikk\
│   └── Artistnavn\
│       └── Albumnavn\
│           ├── 01 - Første låt.mp3
│           └── cover.jpg
└── Vare produksjoner\
    └── Min kortfilm (2026)\
        └── Min kortfilm (2026).mp4
```

**Spørsmål til driftsloggen:** Hvorfor tror du strømmetjenester er så nøye med filnavn og mappestruktur?

---

## Del B – Start Jellyfin

### B1 – Lag volumer for innstillinger og mellomlager

```powershell
wslc volume create jellyfin-config
wslc volume create jellyfin-cache
```

### B2 – Start containeren

```powershell
wslc run -d --name jellyfin `
  -p 8096:8096 `
  -e TZ=Europe/Oslo `
  -v jellyfin-config:/config `
  -v jellyfin-cache:/cache `
  -v "$env:USERPROFILE\Videos\Jellyfin:/media:ro" `
  jellyfin/jellyfin
```

Hva betyr linjen med `/media:ro`?

- Mappen `Videos\Jellyfin` på PC-en dukker opp som `/media` inne i containeren.
- `:ro` betyr *read-only*, altså skrivebeskyttet. Jellyfin kan lese filmene dine, men ikke endre eller slette dem.

**Spørsmål til driftsloggen:** Hvorfor er det lurt at Jellyfin ikke får skrive i mediemappen din?

### B3 – Sjekk at den kjører

```powershell
wslc list
wslc logs jellyfin
```

---

## Del C – Sett opp biblioteker

1. Åpne **http://localhost:8096**.
2. Følg oppsettveiviseren:
   - Språk: **Norsk bokmål**
   - Lag administratorbrukeren din med et sterkt passord
3. Legg til tre **mediebiblioteker**:

   | Bibliotek | Innholdstype | Mappe |
   | --- | --- | --- |
   | Filmer | Filmer | `/media/Filmer` |
   | Musikk | Musikk | `/media/Musikk` |
   | Våre produksjoner | Filmer, eller *Hjemmevideoer og bilder* | `/media/Vare produksjoner` |

   > Mappene heter `/media/…`, ikke `C:\Users\…`. Jellyfin kjører inne i containeren og ser bare det du koblet inn med `-v`.

4. Fullfør veiviseren og logg inn. Vent til bibliotekene er skannet.

> Menyene i Jellyfin kan hete litt annerledes på norsk, eller i nyere versjoner. I instruksjonene står det engelske navnet i parentes, for eksempel **Dashbord** (*Dashboard*). Bytter du språk til engelsk, blir det lettere å følge.

Jellyfin henter automatisk plakater og beskrivelser for kjente filmer, som Blender-filmene. Dine egne produksjoner finnes ikke i noen database, så dem må du gjøre selv i del D.

📸 *Skjermbilde til driftsloggen: forsiden med bibliotekene dine.*

---

## Del D – Gjør innholdet ditt proft

Velg minst én av dine egne produksjoner, og gjør den like fin som en «ekte» film.

### D1 – Plakat og bakgrunn

1. Lag en **plakat** i stående format (for eksempel 1000 × 1500 piksler) og et **bakgrunnsbilde** i liggende format (1920 × 1080).
2. I Jellyfin: åpne filmen → `⋮` → **Rediger bilder** (*Edit images*) → last opp plakat (Primær) og bakgrunn (Backdrop).

### D2 – Beskrivelse og aldersgrense

`⋮` → **Rediger metadata** (*Edit metadata*). Fyll ut:

- Tittel, år og en kort beskrivelse (2–3 setninger)
- Sjanger og medvirkende (deg selv og de du laget filmen med)
- Aldersgrense (offisiell vurdering)

### D3 – Undertekster

1. Lag en undertekstfil for filmen din, for eksempel med det gratis programmet [Subtitle Edit](https://github.com/SubtitleEdit/subtitleedit), eller skriv den i Notisblokk:

   ```
   1
   00:00:01,000 --> 00:00:04,000
   Dette er min første undertekst.

   2
   00:00:05,000 --> 00:00:08,500
   Den vises i fire sekunder.
   ```

2. Lagre den ved siden av videofilen, med samme navn og språkkode: `Min kortfilm (2026).no.srt`
3. I Jellyfin: `⋮` → **Oppdater metadata** (*Refresh metadata*). Spill av filmen og slå på underteksten.

📸 *Skjermbilde til driftsloggen: filmsiden din med plakat, beskrivelse og undertekst.*

---

## Del E – Brukere og tilgang

Lag to nye brukere under **Dashbord** (*Dashboard*) → **Brukere** (*Users*) → **+**:

| Bruker | Tilgang | Slik setter du det opp |
| --- | --- | --- |
| **Gjest** | Bare «Våre produksjoner» | Under **Tilgang** (*Access*): fjern haken for «Aktiver tilgang til alle biblioteker», og velg bare «Våre produksjoner» |
| **Barn** | Bare innhold med lav aldersgrense | Under **Foreldrekontroll** (*Parental control*): sett høyeste tillatte aldersgrense. Sett aldersgrenser på filmene (D2) |
| *(deg)* | Alt + administrator | – |

Test hver bruker i et inkognito-vindu, og fyll ut:

| Test | Hva tror du skjer? | Hva skjedde? |
| --- | --- | --- |
| Gjest logger inn – hvilke biblioteker vises? | | |
| Barn prøver å finne en film med høy aldersgrense | | |
| En film *uten* aldersgrense – ser Barn den? | | |
| Gjest prøver å åpne Dashbord | | |

**Spørsmål:** Hva skjer med filmer som ikke har noen aldersgrense? Er det trygt?

---

## Del F – Strøm til mobilen, og undersøk transkoding

### F1 – Gjør Jellyfin tilgjengelig i tailnettet

Vi bruker port **8443** i tailnettet, så Jellyfin ikke kolliderer med Immich hvis du også gjør prosjekt 1:

```powershell
tailscale serve --bg --https=8443 localhost:8096
tailscale serve status
```

Adressen blir for eksempel `https://im-pc-kari.tail1234.ts.net:8443`.

### F2 – Installer appen

1. Slå på Tailscale på mobilen.
2. Installer **Jellyfin** fra App Store eller Google Play.
3. Server-adresse: adressen fra F1. Logg inn.

📸 *Skjermbilde til driftsloggen: en av dine produksjoner spilles av på mobilen.*

### F3 – Undersøk transkoding

Når en enhet ikke kan spille av filformatet, eller nettet er for tregt, må Jellyfin gjøre om (**transkode**) videoen underveis. Det koster mye CPU.

1. Spill av en film på mobilen.
2. Kjør dette i Terminal på PC-en mens filmen spilles:

   ```powershell
   wslc stats
   ```

3. Se i Jellyfin på PC-en: **Dashbord** → **Aktive enheter** (*Active devices*). Står det **direkteavspilling** eller **transkoding**?
4. Endre kvaliteten i avspilleren på mobilen til noe lavt, for eksempel 720p, 1 Mbit/s. Kjør `wslc stats` igjen.

| Avspilling | Direkte eller transkoding? | CPU (%) | Minne |
| --- | --- | --- | --- |
| Maks kvalitet | | | |
| 720p, 1 Mbit/s | | | |
| Med undertekst innbrent (valgfritt) | | | |

### F4 – Del med en medelev

Del PC-en med en medelev i Tailscale ([Kom i gang, steg 7](../00-kom-i-gang.md#steg-7--lær-deg-å-dele-maskinen-med-en-medelev)), og lag en Jellyfin-bruker til medeleven, for eksempel med Gjest-tilgang. Kan medeleven se produksjonene dine?

---

## Del G – Drift: startskript og omstart

1. Lag filen `start-jellyfin.ps1` i Dokumenter:

   ```powershell
   Write-Host "Starter Jellyfin..."
   wslc start jellyfin
   wslc list
   Write-Host "Ferdig! Åpne http://localhost:8096"
   ```

2. Første gang må du tillate skript (én gang, i vanlig Terminal):

   ```powershell
   Set-ExecutionPolicy -Scope CurrentUser RemoteSigned
   ```

3. Start PC-en på nytt, og kjør skriptet:

   ```powershell
   & "$env:USERPROFILE\Documents\start-jellyfin.ps1"
   ```

   Er brukerne, plakatene og innstillingene dine der fortsatt? Hvorfor?

4. **Legg til en ny film** i mappen mens Jellyfin kjører. Dukker den opp av seg selv? Hvis ikke: **Dashbord** → **Biblioteker** (*Libraries*) → **Skann alle biblioteker** (*Scan all libraries*).

---

## Refleksjon

Svar i driftsloggen:

1. Tegn oppsettet: containeren, porten, de to volumene, mediemappen og Tailscale.
2. Hva er forskjellen på det som ligger i *volumene* (`jellyfin-config` og `jellyfin-cache`) og det som ligger i *mediemappen*?
3. Forklar transkoding med egne ord. Bruk målingene dine. Hvorfor bruker Netflix og YouTube mye penger på å lage mange versjoner av hver video på forhånd?
4. Hva betyr lisensen CC BY, og hvorfor er det viktig å sjekke lisensen før du legger ut innhold andre har laget?
5. Hvilke fordeler og ulemper har en egen strømmetjeneste sammenlignet med YouTube eller Netflix?

## Rydde opp (når prosjektet er levert)

Filmene dine i `Videos\Jellyfin` blir **ikke** slettet. Det gjør bare Jellyfins innstillinger.

```powershell
tailscale serve --https=8443 localhost:8096 off
wslc rm -f jellyfin
wslc volume rm jellyfin-config jellyfin-cache
```

---

[← Tilbake til hovedsiden](../README.md)
