# 12 forslag til YFF-prosjekter – IT og medieproduksjon

[← Tilbake til README](README.md) · [Vg3-lærefag og kompetansemål →](vg3-laerefag.md)

## Innhold

- [Rammer for prosjektet](#rammer-for-prosjektet)
- [IT-drift: D1–D3](#it-drift)
- [IT-utvikling: U1–U3](#it-utvikling)
- [Medieproduksjon: M1–M6](#medieproduksjon)

## Rammer for prosjektet

Hvert prosjekt er skrevet som et oppdrag fra en tenkt kunde, slik det kunne kommet til en lærebedrift. Du velger ett oppdrag (eller lager et eget etter samme mønster), fyller ut prosjektmalen i HTML-loggen og får planen godkjent før du begynner å produsere.

- **Varighet:** 4 økter à 6 timer (24 timer), deretter presentasjon
- **Produkt:** hvert oppdrag har et konkret produkt som skal vises fram
- **Kompetansemål:** numrene viser til listene i [vg3-laerefag.md](vg3-laerefag.md)
- **Logg:** føres som HTML-side etter hver økt, med minst to bilder eller skjermbilder per økt
- **Presentasjon:** 5–8 minutter om oppdraget, produktet (vis det fram), prosessen, hva som gikk bra og hva du ville gjort annerledes

Felles øktplan som de fleste oppdragene følger:

| Økt | Hovedinnhold |
|---|---|
| 1 | Les oppdraget, fyll ut planleggingen, få den godkjent, gjør research og skisser eller oppsett |
| 2 | Produksjon del 1 |
| 3 | Produksjon del 2, testing og tilbakemelding fra en medelev («kunden») |
| 4 | Ferdigstill, dokumenter, skriv evaluering og lag presentasjon |

Oversikt over de 12 oppdragene:

| Nr. | Oppdrag | Oppdragsgiver | Lærefag |
|---|---|---|---|
| [D1](#d1--serverdrift-for-tannlegekontoret) | Serverdrift for tannlegekontoret | Smil Tannhelse AS | IT-driftsfaget |
| [D2](#d2--nettverk-for-nytt-kontor) | Nettverk for nytt kontor | Fjordtall Regnskap | IT-driftsfaget |
| [D3](#d3--dns-filter-og-overvåking-for-barnehagen) | DNS-filter og overvåking for barnehagen | Solsikken barnehage | IT-driftsfaget |
| [U1](#u1--responsiv-nettside-for-kafeen) | Responsiv nettside for kafeen | Kaffekroken | IT-utviklerfaget |
| [U2](#u2--utlånssystem-for-medieutstyr) | Utlånssystem for medieutstyr | Skolens medieavdeling | IT-utviklerfaget |
| [U3](#u3--inneklima-dashboard-for-klasserom) | Inneklima-dashboard for klasserom | Skolens driftsavdeling | IT-utviklerfaget |
| [M1](#m1--reklamefilm-for-sosiale-medier) | Reklamefilm for sosiale medier | Toppturen Sport | Innholdsproduksjonsfaget |
| [M2](#m2--produktfoto-til-nettbutikk) | Produktfoto til nettbutikk | Lokal såpeprodusent | Innholdsproduksjonsfaget |
| [M3](#m3--visuell-profil-for-ny-bedrift) | Visuell profil for ny bedrift | Ungdomsbedrift | Mediedesignfaget |
| [M4](#m4--app-prototype-for-treningssenter) | App-prototype for treningssenter | Puls Trening | Mediedesignfaget |
| [M5](#m5--livestream-av-skolearrangement) | Livestream av skolearrangement | Elevrådet | Medieteknikkfaget |
| [M6](#m6--teknisk-rigg-for-panelsamtale) | Teknisk rigg for panelsamtale | Næringsforeningen | Medieteknikkfaget |

Oppdragsgiverne er oppdiktet. Bytt dem gjerne ut med ekte lokale bedrifter eller skolens egne behov.

---

## IT-drift

### D1 – Serverdrift for tannlegekontoret

**Oppdragsgiver:** Smil Tannhelse AS har 8 ansatte: 3 tannleger, 3 assistenter og 2 i resepsjonen.

**Oppdraget:**
> «Vi har til nå lagret alt på hver enkelt PC og delt filer på minnepinne. Vi vil ha en sentral server der alle logger inn med egen bruker, der resepsjonen ikke ser tannlegenes mapper, og der vi kan bytte PC uten å miste noe. Vi trenger også en enkel veiledning til de ansatte.»

**Produkt som skal presenteres:** Et virtuelt servermiljø med domenekontroller (Active Directory), brukere og grupper, delte mapper med riktige tilganger, minst én gruppepolicy og én klient som er meldt inn i domenet. I tillegg driftsdokumentasjon og en brukerveiledning på én side.

**Relevante kompetansemål ([Vg3 IT-driftsfaget](vg3-laerefag.md#vg3-it-driftsfaget-it-driftstekniker)):** 1, 3, 9, 11, 13, 14

**Utstyr og programvare:** Hyper-V, VMware eller Proxmox, Windows Server (evalueringsversjon), Windows 10/11-klient, verktøy for skjermbilder

**Forslag til økter:**

1. Planlegging: lag brukerliste, gruppestruktur og mappetilganger på papir. Installer Windows Server som virtuell maskin.
2. Sett opp AD DS og DNS. Lag OU-er, brukere og grupper.
3. Lag delte mapper med NTFS-rettigheter og en gruppepolicy (f.eks. skrivebordsbakgrunn eller passordkrav). Meld inn klienten og test innlogging som ulike brukere.
4. Skriv driftsdokumentasjon, brukerveiledning og evaluering, og lag presentasjonen.

**Ekstra utfordring:** Lag et PowerShell-skript som oppretter alle brukerne fra en CSV-fil.

### D2 – Nettverk for nytt kontor

**Oppdragsgiver:** Fjordtall Regnskap flytter inn i nye lokaler med 10 arbeidsplasser og et møterom.

**Oppdraget:**
> «Vi trenger et nettverk der de ansatte og kundene våre på gjestenettet ikke kan se hverandre. Skriveren skal kunne brukes av alle ansatte. Vi vil ha en tegning av nettverket og en innkjøpsliste med pris før vi bestiller noe.»

**Produkt som skal presenteres:** Et fysisk nettverk på labben med switch og ruter, to VLAN (ansatte og gjest) med hvert sitt subnett og DHCP, og en test som viser at nettene er adskilt. I tillegg nettverkstegning, IP-plan og innkjøpsliste med priser og begrunnelse.

**Relevante kompetansemål ([Vg3 IT-driftsfaget](vg3-laerefag.md#vg3-it-driftsfaget-it-driftstekniker)):** 1, 6, 7, 11, 14

**Utstyr og programvare:** Managed switch og ruter (f.eks. Cisco), nettverkskabler, 2–3 klientmaskiner, Cisco Packet Tracer, draw.io eller Visio

**Forslag til økter:**

1. Planlegging: kartlegg behovene, lag IP-plan med subnett og tegn nettverket. Bygg nettverket i Packet Tracer først.
2. Konfigurer switchen (VLAN, trunk- og access-porter) og ruteren (subinterface, DHCP).
3. Koble opp klientene, test med ping og ipconfig, feilsøk og dokumenter. Sett opp en tilgangsliste slik at gjestenettet ikke når ansattnettet.
4. Lag innkjøpsliste med priser fra leverandører, gjør dokumentasjonen ferdig, skriv evaluering og lag presentasjonen.

**Ekstra utfordring:** Legg til et trådløst aksesspunkt med to SSID-er, knyttet til hvert sitt VLAN.

### D3 – DNS-filter og overvåking for barnehagen

**Oppdragsgiver:** Solsikken barnehage har nettbrett til barna og PC-er til de ansatte.

**Oppdraget:**
> «Vi vil at nettbrettene til barna ikke skal komme inn på uegnede nettsider eller vise reklame. Vi vil også få beskjed hvis internett eller skriveren slutter å virke, slik at vi slipper å oppdage det selv. Det må være billig og lite vedlikehold.»

**Produkt som skal presenteres:** En Raspberry Pi som kjører DNS-filter (Pi-hole) og overvåker internett, ruter og skriver (f.eks. med Uptime Kuma), med varsling. Et skript som automatisk tar sikkerhetskopi av oppsettet. I tillegg en kort driftsrutine og en rutine for avviksmelding.

**Relevante kompetansemål ([Vg3 IT-driftsfaget](vg3-laerefag.md#vg3-it-driftsfaget-it-driftstekniker)):** 1, 2, 5, 7, 10, 14

**Utstyr og programvare:** Raspberry Pi med strømforsyning og minnekort, Raspberry Pi OS Lite, SSH-klient, Pi-hole, Uptime Kuma (Docker), cron og et bash-skript

**Forslag til økter:**

1. Planlegging og risikovurdering. Installer Raspberry Pi OS og sett opp statisk IP, SSH-tilgang og sikker innlogging.
2. Installer og sett opp Pi-hole med blokkeringslister, og test på en klient.
3. Installer overvåkingen, legg inn tjenestene som skal overvåkes og sett opp varsling. Skriv backup-skriptet og kjør det automatisk med cron.
4. Skriv driftsrutine, avviksrutine og et kort opplæringsark til de ansatte. Skriv evaluering og lag presentasjonen.

**Ekstra utfordring:** Vis statistikk over blokkerte forespørsler og forklar hva den sier om personvern.

---

## IT-utvikling

### U1 – Responsiv nettside for kafeen

**Oppdragsgiver:** Kaffekroken er en liten kafé i sentrum.

**Oppdraget:**
> «Vi har bare en Facebook-side, og folk ringer hele tiden for å spørre om åpningstider og meny. Vi vil ha en enkel nettside som fungerer godt på mobil, som er lett å lese også for eldre kunder og svaksynte, og som vi selv kan oppdatere menyen på.»

**Produkt som skal presenteres:** En publisert nettside (f.eks. på GitHub Pages) med forside, meny, åpningstider og kontaktinformasjon med kart. Siden skal være responsiv, bestå en sjekk for universell utforming og ha en kort veiledning for hvordan kunden oppdaterer menyen.

**Relevante kompetansemål ([Vg3 IT-utviklerfaget](vg3-laerefag.md#vg3-it-utviklerfaget-it-utvikler)):** 3, 6, 9, 13, 15

**Utstyr og programvare:** VS Code, HTML, CSS og litt JavaScript, Git og GitHub, Figma eller papir for skisser, WAVE eller Lighthouse for test av universell utforming

**Forslag til økter:**

1. Planlegging: beskriv målgruppen, lag sidekart og skisser for mobil og PC. Sett opp Git-repo og mappestruktur.
2. Lag HTML-strukturen og CSS for mobil først, og tilpass deretter til større skjermer.
3. Legg menyen i en JavaScript-liste eller JSON-fil som er lett å endre. Test universell utforming (kontrast, alt-tekst, tastaturnavigasjon), rett feil og test siden med en medelev.
4. Publiser siden, skriv veiledning til kunden, skriv evaluering og lag presentasjonen.

**Ekstra utfordring:** Legg til et skjema for bordbestilling som sjekker det som skrives inn, direkte i nettleseren.

### U2 – Utlånssystem for medieutstyr

**Oppdragsgiver:** Skolens medieavdeling låner ut kameraer, mikrofoner og stativer.

**Oppdraget:**
> «I dag fører vi utlån i en notatbok, og vi vet aldri hvem som har kamera 3. Vi trenger et system der vi registrerer utstyr, hvem som låner, og når det skal leveres. Det skal være lett å se hva som er utlånt akkurat nå.»

**Produkt som skal presenteres:** En database med tabellene utstyr, elev og utlån, og en enkel app (nettside eller Python-program) der man kan registrere utlån og innlevering og se en liste over utlånt utstyr. I tillegg ER-diagram og brukerveiledning.

**Relevante kompetansemål ([Vg3 IT-utviklerfaget](vg3-laerefag.md#vg3-it-utviklerfaget-it-utvikler)):** 1, 4, 5, 6, 8, 15

**Utstyr og programvare:** VS Code, Python med SQLite (eller PHP og MySQL med XAMPP), draw.io for ER-diagram, eventuelt Flask for nettside

**Forslag til økter:**

1. Planlegging: intervju «kunden», lag datamodell og ER-diagram. Opprett databasen og legg inn testdata.
2. Lag funksjoner for å legge til utstyr og registrere utlån og innlevering.
3. Lag en oversikt over utlånt utstyr og hva som er forsinket. Test og feilsøk. Tenk gjennom personvernet: hvilke elevdata lagres, og hvorfor?
4. Skriv brukerveiledning, teknisk dokumentasjon og evaluering, og lag presentasjonen.

**Ekstra utfordring:** Legg inn innlogging for ansatte, der passordene lagres som hash.

### U3 – Inneklima-dashboard for klasserom

**Oppdragsgiver:** Skolens driftsavdeling, som får klager på dårlig luft og varme klasserom

**Oppdraget:**
> «Vi vil måle temperatur og luftfuktighet (gjerne CO₂) i et klasserom gjennom dagen og se målingene på en nettside, slik at vi vet når vi må lufte eller justere ventilasjonen.»

**Produkt som skal presenteres:** En Raspberry Pi med sensor som lagrer målingene i en fil eller database, og en nettside som viser siste måling og en graf over tid, med varsel når verdien er for høy. I tillegg koblingsskjema og dokumentasjon.

**Relevante kompetansemål ([Vg3 IT-utviklerfaget](vg3-laerefag.md#vg3-it-utviklerfaget-it-utvikler)):** 2, 4, 10, 12, 15, 16

**Utstyr og programvare:** Raspberry Pi, sensor (f.eks. DHT22, BME280 eller SCD30 for CO₂), koblingsbrett og ledninger, Python, Flask og et grafbibliotek (f.eks. Chart.js)

**Forslag til økter:**

1. Planlegging og koblingsskjema. Koble til sensoren og les av verdier med et Python-skript.
2. Lagre målingene automatisk med tidsstempel i CSV eller SQLite.
3. Lag nettsiden med siste måling, graf og varsel. Test over flere timer og feilsøk.
4. Skriv dokumentasjon, reflekter over energibruk og bærekraft, skriv evaluering og lag en presentasjon med live demo.

**Ekstra utfordring:** Sammenlign to rom, eller send varsel på e-post eller Teams når verdien er for høy.

---

## Medieproduksjon

### M1 – Reklamefilm for sosiale medier

**Oppdragsgiver:** Toppturen Sport, en sportsbutikk som skal lansere en ny kolleksjon av vinterutstyr

**Oppdraget:**
> «Vi vil nå ungdom mellom 15 og 25 på Instagram og TikTok. Vi trenger en kort, stilig video som viser fram kolleksjonen og får folk til å komme innom butikken. Vi vil se ideen før dere filmer.»

**Produkt som skal presenteres:** En vertikal reklamefilm på 15–30 sekunder (9:16), eksportert riktig for sosiale medier, med tekst og musikk som er lovlig å bruke. I tillegg pitch, manus eller storyboard, produksjonsplan og forslag til publiseringstidspunkt og tekst til innlegget.

**Relevante kompetansemål ([Vg3 innholdsproduksjonsfaget](vg3-laerefag.md#vg3-innholdsproduksjonsfaget-innholdsprodusent)):** 2, 6, 7, 8, 10, 11, 13, 14

**Utstyr og programvare:** Kamera fra utlån (eller mobil med stabilisator), stativ, mikrofon, lys, Premiere Pro, After Effects (valgfritt), lisensfri musikk (f.eks. Adobe Stock eller YouTube Audio Library)

**Forslag til økter:**

1. Analyser målgruppen, lag ideer og pitch dem for læreren («kunden»). Skriv manus og lag storyboard, opptaksplan og utstyrsliste.
2. Ta opp fra flere vinkler, med nok B-roll og god lyssetting.
3. Rediger: klipp i takt og legg på tekst, fargekorrigering og lyd.
4. Få tilbakemelding fra en medelev og gjør de siste justeringene. Eksporter, lag publiseringsplan, skriv evaluering og lag presentasjonen.

**Ekstra utfordring:** Lag tre versjoner (15 sekunder, 6 sekunder og kvadratisk 1:1) og forklar hvorfor algoritmene favoriserer ulike formater.

### M2 – Produktfoto til nettbutikk

**Oppdragsgiver:** En lokal såpeprodusent som skal åpne nettbutikk

**Oppdraget:**
> «Bildene vi har nå, er tatt med mobil på kjøkkenbenken. Vi trenger profesjonelle produktbilder på hvit bakgrunn til nettbutikken, og noen stemningsbilder vi kan bruke på Instagram.»

**Produkt som skal presenteres:** Minst 6 ferdigredigerte produktbilder på hvit bakgrunn med lik stil, og 3 stemningsbilder. Bildene leveres i riktig format og størrelse for nett, med gode filnavn og alt-tekst. I tillegg en lysskisse som viser oppsettet.

**Relevante kompetansemål ([Vg3 innholdsproduksjonsfaget](vg3-laerefag.md#vg3-innholdsproduksjonsfaget-innholdsprodusent)):** 2, 8, 9, 10, 11, 14, 18

**Utstyr og programvare:** Kamera fra utlån med makro- eller standardobjektiv, stativ, fotostudio eller lysboks, blitser eller lamper og reflekser, Lightroom og Photoshop

**Forslag til økter:**

1. Kartlegg kundens behov, finn referansebilder og planlegg bildeliste og lysoppsett. Test lyset.
2. Ta produktbildene. Dokumenter lysoppsettet med bilder av riggen.
3. Ta stemningsbildene. Rediger i Lightroom, og frilegg og rett opp i Photoshop.
4. Eksporter for nett med alt-tekst og gode filnavn, og sett opp en enkel produktside eller et kontaktark. Skriv evaluering og lag presentasjonen.

**Ekstra utfordring:** Lag et 360-graders produktbilde eller en kort stop motion-film av ett produkt.

### M3 – Visuell profil for ny bedrift

**Oppdragsgiver:** En ungdomsbedrift ved skolen, eller en medelev som tenker på å starte for seg selv

**Oppdraget:**
> «Vi har startet en bedrift, men har ingen logo eller farger. Vi trenger et helhetlig uttrykk vi kan bruke på alt: sosiale medier, visittkort og plakat. Vi vil gjerne se et par forslag før dere velger.»

**Produkt som skal presenteres:** Logo i flere varianter (farge, svart-hvitt, liten og stor), fargepalett, typografi og en enkel profilmanual på 2–4 sider. Profilen skal vises i bruk på visittkort, plakat og et innlegg til sosiale medier.

**Relevante kompetansemål ([Vg3 mediedesignfaget](vg3-laerefag.md#vg3-mediedesignfaget-mediedesigner)):** 1, 2, 3, 5, 7, 8, 9

**Utstyr og programvare:** Illustrator, InDesign, Photoshop, skisseblokk, eventuelt Adobe Fonts og Adobe Color

**Forslag til økter:**

1. Ha et møte med «kunden». Lag stemningsbrett og minst 10 ideer som skisser på papir.
2. Velg to retninger og lag dem som vektorgrafikk i Illustrator. Presenter for kunden og velg én.
3. Gjør ferdig logo, fargepalett og typografi. Lag visittkort, plakat og innlegg til sosiale medier.
4. Lag profilmanualen i InDesign og eksporter riktige filformater (SVG, PNG, PDF). Skriv evaluering og lag presentasjonen.

**Ekstra utfordring:** Lag en kort animert logo til bruk i video.

### M4 – App-prototype for treningssenter

**Oppdragsgiver:** Puls Trening, et lite treningssenter som vil la medlemmene booke timer selv

**Oppdraget:**
> «Medlemmene våre klager på at det er vanskelig å melde seg på gruppetimer. Vi vil ha et forslag til hvordan en app kan se ut og fungere før vi betaler et utviklerfirma for å lage den.»

**Produkt som skal presenteres:** En klikkbar prototype med minst 5 skjermer (forside, timeplan, booking, bekreftelse og min profil) i treningssenterets farger, testet på minst to brukere. I tillegg en brukerreise og en kort oppsummering av brukertesten.

**Relevante kompetansemål ([Vg3 mediedesignfaget](vg3-laerefag.md#vg3-mediedesignfaget-mediedesigner)):** 1, 3, 4, 5, 6, 10

**Utstyr og programvare:** Figma (gratis for utdanning) eller Adobe XD, Illustrator for ikoner, mobil for testing

**Forslag til økter:**

1. Skaff brukerinnsikt: intervju 2–3 medelever kort, lag en brukerreise og se på eksisterende apper. Lag skisser (wireframes) på papir.
2. Lag wireframes i Figma, og deretter visuelt design med farger, typografi og ikoner.
3. Koble skjermene sammen til en klikkbar prototype. Gjennomfør brukertest og noter funnene.
4. Forbedre prototypen ut fra testen, og sjekk kontrast og størrelse på knapper. Skriv evaluering og lag en presentasjon der du viser prototypen live.

**Ekstra utfordring:** Lag også mørk modus eller en versjon for nettbrett.

### M5 – Livestream av skolearrangement

**Oppdragsgiver:** Elevrådet, som vil strømme et arrangement (f.eks. allmøte, konsert eller turnering) til foreldre og elever som ikke kan være til stede

**Oppdraget:**
> «Vi vil at sendingen skal se proff ut, med flere kameravinkler, god lyd og navneskilt på de som snakker. Sendingen må ikke falle ut, og vi må vite hva vi gjør hvis noe går galt.»

**Produkt som skal presenteres:** En fungerende strømmerigg med minst to kameraer, lyd fra mikser, grafikk (logo, navneskilt og pauseskjerm) og en testsending eller et opptak av et kort arrangement. I tillegg riggetegning, kjøreplan og en plan B hvis noe går galt.

**Relevante kompetansemål ([Vg3 medieteknikkfaget](vg3-laerefag.md#vg3-medieteknikkfaget-medietekniker)):** 1, 2, 3, 4, 8, 11

**Utstyr og programvare:** 2–3 kameraer med HDMI-utgang, capture-kort eller videomikser (f.eks. ATEM Mini), lydmikser og mikrofoner, PC med OBS Studio, stativer og kabler, nettverkskabel

**Forslag til økter:**

1. Gjør befaring i lokalet. Lag riggetegning, utstyrsliste, risikovurdering og kjøreplan.
2. Rigg kamera og lyd, sett opp OBS med scener og kilder, og test opplastingshastigheten.
3. Lag grafikk, øv på å bytte mellom kameraer og gjennomfør en testsending (privat eller ulistet).
4. Gjennomfør sendingen eller opptaket, rigg ned og sjekk utstyret. Skriv evaluering og lag en presentasjon med klipp fra sendingen.

**Ekstra utfordring:** Legg til en reporter som intervjuer folk i pausen, med en egen kamerakilde.

### M6 – Teknisk rigg for panelsamtale

**Oppdragsgiver:** Næringsforeningen, som skal holde en panelsamtale med fire deltakere og et publikum på ca. 60

**Oppdraget:**
> «Alle i salen må høre godt, panelet må være godt belyst, og vi vil ha et opptak vi kan legge ut etterpå. Vi trenger også et prisoverslag på hva det ville kostet å leie utstyret.»

**Produkt som skal presenteres:** En rigget scene med lydanlegg, mikrofoner til fire deltakere og en moderator, lys på panelet og opptak med kamera og separat lyd. Et ferdig redigert opptak av en kort testsamtale. I tillegg riggetegning, utstyrsliste med leiepriser, risikovurdering og rutine for nedrigging og vedlikehold.

**Relevante kompetansemål ([Vg3 medieteknikkfaget](vg3-laerefag.md#vg3-medieteknikkfaget-medietekniker)):** 2, 5, 6, 7, 11, 12

**Utstyr og programvare:** Lydmikser, høyttalere, trådløse mikrofoner eller myggmikrofoner, lyskastere og stativer, kamera fra utlån, lydopptaker, Premiere Pro eller Audition

**Forslag til økter:**

1. Gjør en behovsanalyse og lag riggetegning, utstyrsliste, prisoverslag fra et utleiefirma og risikovurdering (kabler, strøm, løft).
2. Rigg lyd og lys, gjør lydsjekk og still inn mikseren slik at det ikke blir feedback.
3. Gjennomfør og ta opp en kort panelsamtale med medelever. Sjekk filene og ta sikkerhetskopi.
4. Synkroniser lyd og bilde og rediger opptaket. Rigg ned og sjekk utstyret, og vurder strømforbruk og miljø. Skriv evaluering og lag presentasjonen.

**Ekstra utfordring:** Lag en enkel løsning for teksting av opptaket, slik at det blir universelt utformet.

---

[← Tilbake til README](README.md) · [Vg3-lærefag og kompetansemål →](vg3-laerefag.md)
