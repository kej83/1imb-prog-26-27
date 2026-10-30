# Feilsøking

[← Tilbake til hovedsiden](README.md)

**Første regel:** Les loggen! `wslc logs NAVN` forteller nesten alltid hva som er galt. Kopier feilmeldingen inn i driftsloggen din.

**Andre regel:** Endre én ting om gangen, og test etter hver endring.

---

## wslc

| Problem | Sannsynlig årsak | Løsning |
| --- | --- | --- |
| `wslc` blir ikke gjenkjent som kommando | WSL er for gammel, eller Terminal ble ikke startet på nytt | Kjør `wsl --update`, lukk Terminal og åpne den igjen |
| Containeren min er borte i `wslc list` | Den har stoppet, eller du er i feil type Terminal | Prøv `wslc list --all`. Sjekk at du bruker **vanlig** Terminal, ikke administrator |
| Containeren stopper rett etter start | Feil i innstillinger, eller en annen container den trenger er ikke klar | `wslc logs NAVN`. Rett feilen, så `wslc start NAVN` |
| «port is already allocated» eller lignende | En annen container eller et program bruker porten | Velg en annen port på PC-siden, for eksempel `-p 8081:80`. Sjekk `wslc list` |
| «name is already in use» | Det finnes allerede en container med det navnet | `wslc rm -f NAVN` og prøv igjen. Volumene blir ikke slettet |
| Nedlastingen henger eller feiler | Ustabil wifi | Kjør samme kommando på nytt |
| Jeg må endre en `-e`-innstilling | Innstillinger kan ikke endres på en eksisterende container | `wslc rm -f NAVN`, kjør `wslc run` på nytt med ny innstilling **og samme volum** |
| Disken er full | Gamle images og containere | `wslc container prune` og `wslc image prune` |
| PC-en blir treg | Containere bruker mye minne | `wslc stats` viser hvem som bruker mest. Stopp det du ikke bruker |

## Tailscale

| Problem | Sannsynlig årsak | Løsning |
| --- | --- | --- |
| Mobilen når ikke tjenesten | Tailscale er av på mobilen, eller `serve` er ikke satt opp | Slå på Tailscale i appen. Kjør `tailscale serve status` på PC-en |
| `tailscale serve` gir feil om HTTPS | HTTPS er ikke slått på i tailnettet | Følg lenken i feilmeldingen, eller se steg 5 i [Kom i gang](00-kom-i-gang.md) |
| `tailscale serve` gir «access denied» | Manglende rettigheter | Kjør kommandoen i **Terminal (administrator)** |
| Medeleven når ikke tjenesten | Feil adresse, eller delingen er ikke godtatt | Medeleven må bruke **fullt navn** (`maskin.tailXXXX.ts.net`) og ha godtatt invitasjonen |
| Tjenesten virket i går, men ikke i dag | PC-en har vært startet på nytt | `wslc list --all`, deretter `wslc start NAVN` |
| Sertifikatfeil første gang | Sertifikatet lages første gang noen besøker siden | Vent 30–60 sekunder og last inn på nytt |

## Spør om hjelp – på riktig måte

Når du spør læreren eller en medelev, ha dette klart:

1. Hva prøvde du å gjøre? (Steg nummer i instruksjonen.)
2. Hvilken kommando kjørte du? (Kopier den.)
3. Hva skjedde? (Kopier feilmeldingen eller loggen.)
4. Hva har du allerede prøvd?

Det er akkurat slik driftsfolk jobber. En god feilbeskrivelse er halve løsningen.
