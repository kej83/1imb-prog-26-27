# NB!
# Bruk Google-Colab dersom din huggingface konto er mindre enn 30 dager gammel!!
---
title: Ultimate TTS – norsk og engelsk
emoji: 🎙️
colorFrom: blue
colorTo: green
sdk: gradio
sdk_version: 6.29.1
python_version: 3.12.12
app_file: app.py
pinned: false
short_description: Skoleutgave med stemmekloning gjennom OmniVoice
models:
  - k2-fsa/OmniVoice
---

# Publiser stemmekloning på Hugging Face uten betaling

Veiledning for elever og lærer. Vilkår og dokumentasjon kontrollert **9. oktober 2026**.

Dette er en tilpasset skoleutgave av **Ultimate Text To Speech Generator With Voice Cloning** fra SECourses. Den henter og bruker appens opprinnelige `OmniVoiceEngine`, med et enklere grensesnitt for norsk og engelsk. Den erstatter ikke motoren med en annen TTS-modell.

## Før dere begynner

**Gratis publisering krever en personlig Hugging Face-konto med bekreftet e-post, alder over 30 dager og tilgang til ZeroGPU.** Hugging Face oppgir inntil to ZeroGPU Spaces for slike gratis kontoer. Hvis ZeroGPU ikke er tilgjengelig for elevens konto, kan denne appen ikke publiseres og kjøres gratis på den kontoen nå. Opprett kontoene i god tid. [Offisielle ZeroGPU-vilkår](https://huggingface.co/docs/hub/spaces-zerogpu).

**Velg Gradio og ZeroGPU.** Nye Docker Spaces og ordinære Gradio Spaces krever et betalt abonnement, selv om CPU Basic er oppført med null timepris. Docker er derfor ikke løsningen for dette prosjektet. [Offisiell oversikt over Spaces](https://huggingface.co/docs/hub/spaces-overview).

Skoleutgaven inneholder stemmekloning fra opplastet lyd, språkvalg, lydavspilling og WAV-nedlasting. Stemmetrening, batchjobber, IndexTTS, AuK og de øvrige skrivebordsfanene inngår ikke. Disse arbeidsflytene er ikke tilpasset den gratis tjenesten her.

Læreren bør gjøre prøvepubliseringen og språktesten nedenfor før undervisningen. Installasjonsfilene er tilpasset, men første publisering på ekte ZeroGPU må fortsatt bekrefte GPU-driften og lydkvaliteten.

## 1. Klargjør en gratis konto

1. Gå til [Hugging Face](https://huggingface.co/) og logg inn på din personlige konto.
2. Bekreft e-postadressen hvis du ikke allerede har gjort det.
3. Kontroller at kontoen er over 30 dager gammel.
4. Bruk kontoens gratisnivå. Denne oppgaven trenger ikke PRO, betalingskort, API-kreditter eller en betalt GPU.

Hvis kontoen er for ny, kan du forberede filene nå og publisere senere. Du kan også prøve [OmniVoices offisielle demo](https://huggingface.co/spaces/k2-fsa/OmniVoice) mens du venter. Det er en annen demonstrasjonsapp, og teller ikke som publisering av din egen skoleutgave.

## 2. Opprett din Space

1. Åpne [Create a new Space](https://huggingface.co/new-space).
2. Under **Owner** velger du din personlige konto.
3. Skriv et navn, for eksempel `stemmekloning-norsk-engelsk`.
4. Velg **Gradio** som SDK. Velg en tom app hvis du får spørsmål om mal.
5. Velg **ZeroGPU** som maskinvare. Hvis opprettelsessiden ikke viser maskinvarevalget, må du finne ZeroGPU i **Settings → Hardware** før appen skal kjøre.
6. Velg **Public** dersom prosjektet skal deles med klassen. Da blir publiseringsfilene synlige for andre.
7. Opprett Space-en.

**Hvis siden krever abonnement eller betaling: stopp dette forsøket.** Kontroller at du bruker en personlig konto og Gradio med ZeroGPU. Hvis gratisvalget fortsatt mangler, må du vente på kontotilgang eller ta spørsmålet opp med læreren. Ikke velg en betalt GPU som erstatning.

## 3. Last opp de ferdige filene

Pakk ut `HuggingFace_Skolepakke.zip`, eller bruk filene i mappen `huggingface_space` som læreren deler ut.

1. Åpne **Files** eller **Files and versions** i Space-en.
2. Velg **Add file → Upload files**.
3. Last opp følgende filer direkte i roten av Space-en:

   - `app.py`
   - `school_engine.py`
   - `source_loader.py`
   - `validation.py`
   - `requirements.txt`
   - `packages.txt`
   - `README.md`
   - `.gitignore` dersom du ser denne skjulte filen; den er ikke nødvendig ved nettleseropplasting.

4. Erstatt den eksisterende `README.md` med den medfølgende filen. Behold YAML-blokken mellom de to linjene med `---` øverst. Den angir startfil og versjoner.
5. Skriv en kort melding, for eksempel «Legger til stemmekloningsappen», og velg **Commit changes**.

Filene skal ligge ved siden av hverandre, ikke inne i en undermappe kalt `huggingface_space`. Last opp de utpakkede filene, ikke ZIP-filen. Du trenger ikke å kjøre installasjonsfilene på din egen PC først.

**Ikke last opp** `index_TTS_requirements.txt`, Windows-/Linux-installerne, `pip_freeze.txt`, den store appmappen, modeller eller personlige lydopptak som kildefiler. `requirements.txt` i skolepakken er laget spesielt for denne publiseringen.

## 4. Kontroller oppstarten

1. Åpne **Settings** og kontroller at **Hardware** er **ZeroGPU**.
2. Gå til **App** og vent mens status er **Building** eller **Starting**.
3. Appen installerer bibliotekene og henter nødvendig appkode og OmniVoice-modell automatisk. Første oppstart kan ta flere minutter.
4. Når siden med «Stemmekloning på norsk og engelsk» vises, er grensesnittet startet. Lag en testlyd for å bekrefte at GPU-delen også fungerer.

Ingen Hugging Face-token eller hemmelig API-nøkkel trengs for de offentlige filene appen bruker. Omstart eller nybygging kan medføre ny nedlasting, siden gratis lagring ikke er varig. [Avhengigheter i Gradio Spaces](https://huggingface.co/docs/hub/spaces-dependencies).

## 5. Spill inn referansestemmen

1. Bruk din egen stemme, eller en stemme personen har gitt deg tillatelse til å bruke.
2. Spill inn **10–15 sekunder** uten musikk og bakgrunnsprat.
3. Last opp opptaket i appen. Et kort WAV-opptak er et godt utgangspunkt.
4. Skriv **nøyaktig alle ordene som sies i opptaket** i felt 2. Dette er referanseteksten; den nye teksten skal stå i felt 4.

Bruk et opptak med noen hele setninger og tydelig tale. Et norsk referanseopptak passer best når du vil lage norsk tale. Lag gjerne et eget engelsk opptak for engelsk.

Opptaket sendes til Hugging Face for behandling. Appen bygger ingen felles stemmeliste og lagrer ingen permanente stemmepromptfiler. Gradio bruker midlertidige lydfiler, og appen er satt til periodisk opprydding etter omtrent én time; dette er ikke et løfte om øyeblikkelig sletting eller om Hugging Faces øvrige logging. Lydopptak skal ikke legges inn under **Files**.

## 6. Lag og last ned norsk tale

1. Velg **Norsk (anbefalt)** i språklisten.
2. Skriv en ny, kort tekst: maks. **40 ord og 280 tegn**.
3. Prøv for eksempel: «Hei! Nå tester vi stemmekloning på norsk. Jeg ønsker å høre tydelig forskjell på æ, ø og å.»
4. Kryss av for at du bruker egen stemme eller har tillatelse.
5. Velg **Lag tale / Generate speech** og vent til lyden vises.
6. Lytt til hele resultatet. Bruk nedlastingsknappen i lydspilleren for å lagre WAV-filen.

Språkvalget «Norsk (anbefalt)» sender `no` til modellen. Egne valg for bokmål (`nb`) og nynorsk (`nn`) finnes også. OmniVoices språkoversikt oppgir langt mer treningsdata for `no` enn for `nb` og `nn`; derfor starter appen med `no`. Norskstøtte innebærer ikke at alle dialekter eller ord uttales riktig. [OmniVoices språkoversikt](https://github.com/k2-fsa/OmniVoice/blob/master/docs/languages.md).

Skriv tall og forkortelser slik de skal uttales, for eksempel «tjuefem» i stedet for «25». Denne utgaven bruker vanlig tekst uten spesielle kontrolltagger. Korte klipp får en beregnet lengde på inntil omtrent 18 sekunder for å begrense GPU-bruken.

## 7. Test engelsk og kontroller kvaliteten

1. Velg **English**. Referanseteksten skal fortsatt stemme med språket i opptaket.
2. Prøv: «Hello! This is a short test of my cloned voice. The speech should be clear and easy to understand.»
3. Lag lyden og lytt etter manglende ord og riktig uttale.
4. Hvis resultatet får norsk aksent, prøv et engelsk referanseopptak fra samme person.

Kloning mellom språk kan overføre aksenten fra referanseopptaket. Utvikleren anbefaler en kort referanse på samme språk som den nye talen for standarduttale. [OmniVoices bruksveiledning](https://github.com/k2-fsa/OmniVoice).

**Lærerens godkjenningstest:** Lag ett klipp på norsk og ett på engelsk med en kjent referansestemme. Kontroller at alle ordene er med, at æ/ø/å er forståelige, at stemmen ligner, og at de nedlastede WAV-filene kan spilles av. En grønn «Running»-status alene bekrefter ikke dette.

## 8. Del prosjektet og bruk gratiskvoten

Del lenken til din Space med læreren. Opplys at lyden er KI-generert.

Hugging Face oppgir for tiden **5 minutter GPU-tid per døgn for en innlogget gratiskonto**, med tilbakestilling 24 timer etter første GPU-bruk. Ventetid i kø og tid du bruker på å skrive er ikke det samme som GPU-tid. Kvoten gjelder brukerens bruk av ZeroGPU, ikke fem minutter per opprettet app. Logg inn når du tester. Når kvoten er brukt opp, vent på tilbakestilling. [Kvoter og kø](https://huggingface.co/docs/hub/spaces-zerogpu).

## Hvis noe ikke virker

| Problem | Hva du gjør |
| --- | --- |
| ZeroGPU mangler eller siden ber om PRO | Kontroller e-post, kontoalder, personlig konto og Gradio-valget. Ikke bestill betaling. |
| `No matching distribution` eller `ResolutionImpossible` | Kontroller at riktig `requirements.txt` er lastet opp, og at README angir Python 3.12.12. Send build-loggen til læreren. |
| `Cannot access CUDA` eller ingen NVIDIA-driver | Kontroller maskinvaren i Settings. Denne publiseringsutgaven krever ZeroGPU. |
| `Application source checksum mismatch` | Vis runtime-loggen til læreren. Ikke fjern kontrollen; kildepakken må undersøkes. |
| Build fullføres, men oppstart feiler | Åpne **Logs** og velg runtime-loggen. Del første konkrete feilmelding med læreren. |
| GPU-kvote brukt opp | Vent til kvoten tilbakestilles. Ikke kjøp kreditter. |
| GPU-tidsgrense på 60 sekunder | Prøv én kort setning og et tydelig 10–15 sekunders opptak. Ved gjentakelse må læreren kontrollere runtime-loggen. |
| Feil ord, mumling eller dårlig stemmelikhet | Rett referanseteksten, forkort målteksten og prøv et renere opptak. Endre seed for et nytt forsøk. |
| Lydfilen godtas ikke | Bruk et WAV-opptak på 10–15 sekunder med én eller to lydkanaler. |

## Til læreren: hva som er tilpasset

Publiseringsfilene bruker originalmotoren fra appversjon `832d8546bd759c5e9e4ba71e1c42fb9a08aaa329`. Appkilden lastes ned med SHA256-kontroll. OmniVoice-biblioteket og modellvektene bruker faste revisjoner. Dette gjør at elevene starter fra samme kode.

`spaces` importeres før PyTorch. Modellen lastes ved oppstart, og GPU-beregningen skjer i én funksjon merket `@spaces.GPU`. Appens vanlige tråd-/subprosessbaserte jobbkjøring brukes ikke. PyTorch og torchaudio er satt til samme versjon, 2.8.0 med CUDA 12.8, som ZeroGPU-dokumentasjonen støtter. Originalinstallerens spesialbygde CUDA 13-utvidelser er ikke med. Norsk sendes eksplisitt til modellen, og ekstra Whisper-modell, stemmetrening og automatisk valg blant mange lydforsøk er utelatt.

**Publiseringsrettigheter:** Det offentlige SECourses-repoet som installereren peker til hadde ingen tydelig rotlisens ved kontrollen. Denne pakken inneholder tilpasningsfilene og henter originalkoden ved oppstart; det avklarer ikke rettigheten til å drifte en offentlig kopi av premiumappen. Læreren bør avklare denne bruken med SECourses før offentlig publisering. OmniVoice har sin egen Apache-2.0-lisens, som ikke automatisk gjelder for hele Ultimate TTS. Ikke sett hele prosjektets lisens til Apache-2.0 uten grunnlag.

Kilder: [Ultimate TTS-kildekode](https://github.com/FurkanGozukara/Premium_IndexTTS2_SECourses), [OmniVoice](https://github.com/k2-fsa/OmniVoice), [ZeroGPU](https://huggingface.co/docs/hub/spaces-zerogpu).
