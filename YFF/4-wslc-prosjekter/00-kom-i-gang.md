# Kom i gang – gjør PC-en klar

[← Tilbake til hovedsiden](README.md)

Her gjør du PC-en klar til alle prosjektene. Når du er ferdig, har du:

- wslc installert og testet med en ekte nettserver
- Tailscale installert på PC og mobil, slik at de kan snakke sammen
- HTTPS slått på i ditt eget Tailscale-nett

Regn med én skoletime. Det meste av tiden går til nedlastinger.

---

## Steg 1 – Sjekk at PC-en er klar

Du trenger:

- Windows 11
- minst 16 GB RAM
- minst 30 GB ledig plass på disken
- administratorrettigheter på PC-en

Sjekk at **virtualisering** er slått på:

1. Trykk `Ctrl` + `Shift` + `Esc` for å åpne **Oppgavebehandling**.
2. Gå til **Ytelse** → **CPU**.
3. Nede til høyre skal det stå **Virtualisering: Aktivert**.

Står det «Deaktivert», må virtualisering slås på i BIOS. Spør læreren om hjelp.

---

## Steg 2 – Oppdater WSL

1. Høyreklikk på Start-knappen og velg **Terminal**. Velg *ikke* «Terminal (administrator)».
2. Skriv:

   ```powershell
   wsl --update
   ```

   Windows spør kanskje om du vil tillate endringer. Svar **Ja**.

3. Sjekk versjonen:

   ```powershell
   wsl --version
   ```

   Linjen **WSL-versjon** må være **3.0.1 eller nyere**.

4. **Lukk Terminal og åpne den på nytt.** Ellers finner ikke Windows den nye kommandoen.

---

## Steg 3 – Test wslc

```powershell
wslc version
wslc run --rm hello-world
```

Får du en melding som begynner med «Hello from …»? Da virker wslc.

Start så en ekte nettserver:

```powershell
wslc run -d --name test-web -p 8080:80 nginx
```

Åpne **http://localhost:8080** i nettleseren. Ser du «Welcome to nginx!», har du nettopp kjørt en Linux-nettserver på Windows-PC-en din.

Hva betyr kommandoen?

| Del | Betyr |
| --- | --- |
| `wslc run` | Start en ny container |
| `-d` | Kjør i bakgrunnen (detached), så du får terminalen tilbake |
| `--name test-web` | Gi containeren et navn du kan bruke senere |
| `-p 8080:80` | Koble port 8080 på PC-en din til port 80 inne i containeren |
| `nginx` | Imaget (programpakken) som skal kjøres. Hentes automatisk fra internett |

Prøv disse kommandoene, og se hva som skjer:

```powershell
wslc list              # viser containere som kjører
wslc logs test-web     # viser loggen til containeren
wslc stop test-web     # stopper containeren – last inn nettsiden på nytt
wslc start test-web    # starter den igjen
wslc rm -f test-web    # stopper og sletter containeren
```

> ### ⚠️ Viktig: bruk alltid vanlig Terminal
> Containere du lager i **Terminal (administrator)** er usynlige i vanlig Terminal, og omvendt. De lever i hver sin «økt».
> Bruk derfor **alltid vanlig Terminal** til `wslc`. Admin-vinduet bruker du bare når en instruksjon sier det, for eksempel for å lage en brannmurregel.

---

## Steg 4 – Installer Tailscale på PC-en

**Hvorfor Tailscale?** På skolens wifi kan elevmaskiner vanligvis ikke snakke direkte med hverandre. Det er en sikkerhetsinnstilling som heter klientisolasjon. Tailscale lager et privat, kryptert nettverk (et *tailnet*) mellom dine egne enheter. Det virker uansett hvilket nett du sitter på: skolen, hjemme eller mobilnett.

1. Installer Tailscale. Enten fra [tailscale.com/download/windows](https://tailscale.com/download/windows), eller i Terminal:

   ```powershell
   winget install --id Tailscale.Tailscale -e
   ```

2. Start Tailscale fra Start-menyen og velg **Log in**. Logg inn med din egen konto (Google, Microsoft eller GitHub).
3. Åpne [Tailscale admin console](https://login.tailscale.com/admin/machines). PC-en din skal stå i listen over maskiner.
4. **Gi PC-en et godt navn:** Trykk på `…` ved maskinen → **Edit machine name**. Bruk for eksempel `im-pc-kari`, *ikke* fullt navn.

   > Hvorfor? Når du slår på HTTPS, blir maskinnavnet ditt skrevet i en offentlig liste over sertifikater (Certificate Transparency). Navnet er altså ikke hemmelig.

5. Åpne Terminal på nytt og test:

   ```powershell
   tailscale status
   tailscale ip -4
   ```

   Den siste kommandoen viser PC-ens Tailscale-adresse. Den begynner alltid med `100.`. Skriv den i driftsloggen.

---

## Steg 5 – Slå på HTTPS og MagicDNS

Dette gjør at tjenestene dine får en adresse som `https://im-pc-kari.tail1234.ts.net` med gyldig sertifikat. Immich- og Jellyfin-appene på mobilen fungerer best med HTTPS.

1. Gå til **[DNS-siden](https://login.tailscale.com/admin/dns)** i admin console.
2. Sjekk at **MagicDNS** er slått på.
3. Under **HTTPS Certificates**, trykk **Enable HTTPS**.
4. Skriv ned **tailnet-navnet** ditt (det ser ut som `tail1234.ts.net`).

---

## Steg 6 – Installer Tailscale på mobilen

1. Last ned **Tailscale** fra App Store eller Google Play.
2. Logg inn med **samme konto** som på PC-en.
3. Slå på tilkoblingen. I admin console skal du nå se både PC og mobil.

**Test:** Start nginx igjen på PC-en, og gjør den tilgjengelig i tailnettet:

```powershell
wslc run -d --name test-web -p 8080:80 nginx
tailscale serve --bg 8080
```

Kommandoen skriver ut en adresse som `https://im-pc-kari.tail1234.ts.net/`. Åpne den på **mobilen**, med Tailscale slått på. Ser du nginx-siden? 🎉

Prøv så å slå av Tailscale på mobilen og laste inn siden på nytt. Hva skjer? Skriv svaret i driftsloggen.

Rydd opp etterpå:

```powershell
tailscale serve reset
wslc rm -f test-web
```

> Får du feilmelding fra `tailscale serve`, kan du prøve samme kommando i **Terminal (administrator)**. Tailscale er ikke en container, så her går det fint å bruke admin-vinduet.

---

## Steg 7 – Lær deg å dele maskinen med en medelev

I prosjekt 1, 2 og 3 skal noen andre bruke tjenesten din. Med Tailscale *deler* du én bestemt maskin med en medelev. Medeleven får da tilgang bare til den maskinen, ikke til resten av nettet ditt.

1. I [admin console](https://login.tailscale.com/admin/machines): trykk `…` ved PC-en din → **Share**.
2. Velg **Copy invite link** og send lenken til medeleven, for eksempel på Teams.
3. Medeleven åpner lenken, logger inn med sin egen Tailscale-konto og godtar.
4. Medeleven når nå PC-en din på det **fulle navnet**: `im-pc-kari.tail1234.ts.net`. Det korte navnet virker ikke for andre enn deg.

Du kan når som helst fjerne delingen under **Share** på maskinen.

---

## Portplan – hvis du gjør flere prosjekter

Bare én tjeneste kan bruke samme port om gangen. Bruk denne planen, så kolliderer ikke prosjektene:

| Prosjekt | Port på PC-en (`-p`) | Adresse i tailnettet |
| --- | --- | --- |
| 1 – Immich | 2283 | `https://<maskin>.<tailnet>.ts.net/` (port 443) |
| 2 – Minecraft Java | 25565 | `<maskin>.<tailnet>.ts.net` (port 25565) |
| 2 – Minecraft Bedrock | 19132 + 19140–19149 | Tailscale-IP-en din, port 19132 |
| 2 – Luanti | 30000 | Tailscale-IP-en din, port 30000 |
| 3 – Jellyfin | 8096 | `https://<maskin>.<tailnet>.ts.net:8443/` |

---

## Når du starter PC-en på nytt

Containere starter **ikke** av seg selv etter omstart. Du starter dem med:

```powershell
wslc list --all          # se hvilke containere du har
wslc start NAVN          # start en container
```

Dataene dine ligger trygt i volumene, så ingenting forsvinner. Det `tailscale serve` har satt opp, huskes også etter omstart.

---

## Om skolens wifi

- **Store nedlastinger:** Første gang du starter et prosjekt, laster wslc ned flere GB. Hvis nedlastingen stopper, kjør bare kommandoen på nytt; den fortsetter der den slapp.
- **Ikke alle laster ned samtidig:** Gjør gjerne nedlastingen hjemme, eller etter avtale med læreren.
- **Klientisolasjon:** Du kan ikke nå en medelevs PC direkte på skolenettet. Det er derfor vi bruker Tailscale.

---

✅ **Ferdig?** Gå tilbake til [hovedsiden](README.md) og velg prosjekt.
