# Stemmekloning på norsk og engelsk – Ultimate TTS i Google Colab

Et undervisningsopplegg der elevene lager KI-generert tale fra et **10–15 sekunders lydopptak**. Utgaven bruker den opprinnelige OmniVoice-motoren fra Ultimate TTS. Den kloner stemmen fra opptaket uten å trene en ny stemmemodell.

**[Åpne eller last ned elevnotatboken](Ultimate_TTS_Colab_Elev.ipynb)** · **[Åpne Google Colab](https://colab.research.google.com/)**

Notatboken inneholder all nødvendig kode og alle elevinstruksjonene: installasjon, opplasting, referansetekst, språkvalg, lydtagger, avspilling, WAV-nedlasting, elevoppgaver og feilsøking. Ingen ekstra appfiler må lastes opp i Colab. Biblioteker, original appkode og modellvekter hentes automatisk fra offentlige kilder.

## Dette trenger eleven

- En Google-konto med tilgang til Google Colab. Skolekontoen må ha tjenesten aktivert.
- Tilgang til en gratis GPU i Colab når oppgaven skal utføres. Tilgang og kvoter varierer.
- Ett tydelig lydopptak på **10–15 sekunder**, maksimalt **10 MB**, og en nøyaktig utskrift av det som sies.
- Sin egen stemme, eller tillatelse fra personen i opptaket.

Det kreves ingen Hugging Face-konto, ingen kontoalder på 30 dager, ingen API-nøkkel, PRO, betalingskort eller kjøp av kreditter. Ikke velg en betalt GPU som erstatning dersom gratis GPU mangler; prøv senere eller avtal et annet tidspunkt med læreren.

## Slik kommer eleven i gang

1. Åpne [notatboken i dette GitHub-repoet](Ultimate_TTS_Colab_Elev.ipynb), og last ned filen med nedlastingsknappen eller **Download raw file**.
2. Gå til [Google Colab](https://colab.research.google.com/) og logg inn.
3. Velg **File → Open notebook → Upload**, og last opp `Ultimate_TTS_Colab_Elev.ipynb`.
4. Lagre en egen kopi med **File → Save a copy in Drive** hvis du skal beholde notatboken.
5. Velg **Runtime → Change runtime type**: **Python 3**, **GPU** og **Runtime Version 2026.07**. Velg T4 hvis det finnes et eget valg. Trykk **Save** og **Connect**.
6. Følg instruksjonene i notatboken og kjør kodecellene **én om gangen fra 1 til 9**. Vent til hver celle er ferdig. Ikke bruk **Run all**; du må velge lydfil og fylle ut tekst underveis.
7. Last ned WAV-filene du vil beholde før du avslutter økten.

Alternativt kan du i Colabs **Open notebook → GitHub** lime inn nettadressen til denne notatboken på GitHub og åpne den derfra.

Det valgte kjøremiljøet bruker Python 3.12.13. Google tilbyr eldre kjøremiljøer i en begrenset periode, så læreren må oppdatere klassekopien når denne versjonen fjernes. [Offisiell oversikt over kjøremiljøer](https://research.google.com/colaboratory/runtime-version-faq.html).

## Hva cellene gjør

| Celle | Handling |
|---|---|
| 1 | Kontrollerer Python og GPU. |
| 2 | Installerer nødvendige biblioteker i et eget miljø. |
| 3 | Klargjør skoleutgaven fra koden som ligger i notatboken. |
| 4 | Laster OmniVoice og holder modellen klar mellom forsøk. |
| 5 | Laster opp og kontrollerer referanseopptaket. |
| 6 | Tar imot referansetekst, ny tekst, språk og seed. |
| 7 | Lager tale og viser en lydspiller. |
| 8 | Laster ned det siste vellykkede resultatet som WAV. |
| 9 | Avslutter modellen og frigjør GPU-minnet. |

**Ny tekst med samme opptak:** Kjør celle 6, 7 og 8 igjen. **Nytt opptak:** Kjør celle 5, 6, 7 og 8. Installasjon og modellinnlasting trenger vanligvis bare å kjøres én gang per økt. Ingen omstart av Python er nødvendig etter installasjonen.

## Norsk, engelsk og lydtagger

Velg **Norsk (anbefalt)** for norsk tale eller **English** for engelsk. Bokmål og nynorsk finnes som egne valg. En referanse på samme språk som den nye talen er et godt utgangspunkt. Bruk maks. **40 talte ord og 280 tegn** per forsøk. Skriv referanseteksten nøyaktig slik du faktisk snakket i opptaket.

OmniVoice støtter blant annet `[laughter]` for latter og `[sigh]` for sukk. Skriv engelske taggnavn med små bokstaver i **den nye teksten**, også når setningen er norsk:

```text
[laughter] Det var morsomt! [sigh] Nå må vi jobbe videre.
```

```text
[laughter] That was funny! [sigh] Now we need to get back to work.
```

Begynn med én tagg og en kort setning. Taggene sendes til modellen uendret. De teller med i tegngrensen, og modellen får ekstra tid til lydene. Uttale, stemmelikhet og lyduttrykk varierer; prøv en annen **seed** hvis resultatet er svakt. Hele den støttede tagglisten og konkrete språkøvelser finnes i notatboken. [OmniVoices taggdokumentasjon](https://github.com/k2-fsa/OmniVoice/blob/08be0b4ccbac3e13e374e86fbfead4b4cac343e2/README.md#non-verbal--pronunciation-control).

## Gratis Colab og tjenestevilkår

Gratis GPU er ikke garantert. Notatboken bruker opplasting og avspilling direkte i Colab, siden Google kan avbryte gratisøkter som hovedsakelig brukes gjennom et separat webgrensesnitt.

Google forbyr **«creating deepfakes»** i administrerte Colab-økter. FAQ-en avklarer ikke uttrykkelig grensen for dette skoleopplegget med egen stemme. Samtykke er derfor ikke en garanti for at Google godtar bruken. Læreren må vurdere opplegget mot vilkårene; ingen omgåelse av blokkeringer eller kvoter er del av denne veiledningen. [Googles Colab-FAQ](https://research.google.com/colaboratory/faq.html).

## Personvern og levering

Opptaket behandles på Googles maskin. Bruk et opptak som er egnet for skoleoppgaven, og merk resultatene **KI-generert tale**. Ikke utgi resultatet for å være et ekte opptak av personen.

Lydspillere og celleutdata kan lagres i selve notatboken. Før du deler den: fjern utdata med **Edit → Clear all outputs**, og kontroller referanseteksten. Legg ikke personlige referanseopptak eller private resultater i GitHub-repoet.

Når du er ferdig, last ned resultatene, kjør celle 9 og velg **Runtime → Disconnect and delete runtime**. En ny økt må installere og laste ned på nytt. Følg skolens opplegg for kontoer, samtykke og innlevering.

## Til læreren: publisering og kontroll

Du kan legge disse **to filene ved siden av hverandre i roten av GitHub-repoet**:

```text
README.md
Ultimate_TTS_Colab_Elev.ipynb
```

README-lenken til notatboken virker da uten at du må endre brukernavn eller repo-navn i teksten. Del GitHub-lenken med elevene. Publiser uten lagrede elevutdata og uten lydopptak.

**Prøvekjør på en ekte Colab-GPU før undervisningen:** Test en kjent 10–15 sekunders referanse, norsk og engelsk, latter og sukk, og WAV-nedlasting. Den tekniske flyten er testet lokalt med en testmotor, inkludert ekte lydkonvertering og prosesskommunikasjon. Notatbokens format og Python-kode er kontrollert. Ekte talesyntese og lydkvalitet på Colab-GPU er ikke verifisert i denne leveransen.

Dette er en skoleutgave for kort stemmekloning gjennom OmniVoice. Full stemmetrening og de andre motorene/fanene i skrivebordsappen inngår ikke.

## Kildekode og rettigheter

Utgaven bruker faste revisjoner av [Ultimate TTS-kilden](https://github.com/FurkanGozukara/Premium_IndexTTS2_SECourses) og [OmniVoice](https://github.com/k2-fsa/OmniVoice), med kontroll av apparkivets SHA256. Versjonene er dokumentert i notatboken. T4 bruker FP16; grafikkort med native BF16-støtte kan bruke BF16.

OmniVoice har Apache-2.0-lisens. Dette avklarer ikke rettighetene til hele SECourses-premiumappen, som ikke hadde noen tydelig rotlisens ved kontrollen. Avklar deling/publisering av premiumappen med opphavspersonen. Ikke gi hele prosjektet Apache-2.0-lisens uten grunnlag.

Dokumentasjon og tilpasning kontrollert **9. oktober 2026**. Tjenestevilkår, kvoter og kjøremiljøer kan endres.
