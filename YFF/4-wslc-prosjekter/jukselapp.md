# Jukselapp – wslc og Tailscale

[← Tilbake til hovedsiden](README.md)

## Containere

| Kommando | Hva den gjør |
| --- | --- |
| `wslc run -d --name NAVN IMAGE` | Starter en ny container i bakgrunnen |
| `wslc list` | Viser containere som kjører |
| `wslc list --all` | Viser alle containere, også stoppede |
| `wslc logs NAVN` | Viser loggen. **Første sted å se når noe ikke virker!** |
| `wslc logs -f NAVN` | Følger loggen live. Avslutt med `Ctrl` + `C` |
| `wslc stop NAVN` | Stopper en container |
| `wslc start NAVN` | Starter en stoppet container |
| `wslc restart NAVN` | Starter en container på nytt |
| `wslc rm -f NAVN` | Stopper og sletter containeren. Data i volumer blir liggende |
| `wslc exec -it NAVN bash` | Åpner et skall *inne i* containeren. Skriv `exit` for å gå ut |
| `wslc exec NAVN KOMMANDO` | Kjører én kommando inne i containeren |
| `wslc stats` | Viser CPU- og minnebruk akkurat nå |
| `wslc container inspect NAVN` | Viser alle detaljer om containeren (JSON) |
| `wslc container cp NAVN:/sti .\mappe` | Kopierer filer ut av containeren |

## Valg til `wslc run`

| Valg | Eksempel | Betyr |
| --- | --- | --- |
| `-d` | | Kjør i bakgrunnen |
| `--name` | `--name web` | Navn på containeren |
| `-p` | `-p 8080:80` | Port på PC-en : port i containeren |
| `-p` med IP | `-p 100.101.102.103:30000:30000/udp` | Bare tilgjengelig på denne IP-adressen. `/udp` for UDP |
| `-e` | `-e TZ=Europe/Oslo` | Miljøvariabel (innstilling eller passord) |
| `-v` volum | `-v mine-data:/data` | Lagrer `/data` i volumet `mine-data` |
| `-v` mappe | `-v "$env:USERPROFILE\Videos:/media:ro"` | Kobler en Windows-mappe inn. `:ro` = skrivebeskyttet |
| `--network` | `--network mitt-nett` | Kobler til et nettverk der containere finner hverandre på navn |
| `--shm-size` | `--shm-size 128M` | Delt minne (trengs av noen databaser) |

## Images, volumer og nettverk

| Kommando | Hva den gjør |
| --- | --- |
| `wslc images` | Viser nedlastede images |
| `wslc image pull IMAGE` | Laster ned et image uten å starte det |
| `wslc volume create NAVN` / `wslc volume list` | Lager og viser volumer |
| `wslc volume rm NAVN` | Sletter et volum. **Dataene forsvinner for godt!** |
| `wslc network create NAVN` / `wslc network list` | Lager og viser nettverk |
| `wslc container prune` | Sletter alle stoppede containere |
| `wslc image prune` | Sletter images som ikke brukes |

## Tailscale

| Kommando | Hva den gjør |
| --- | --- |
| `tailscale status` | Viser enhetene i tailnettet ditt |
| `tailscale ip -4` | Viser PC-ens Tailscale-adresse (100.x.x.x) |
| `tailscale serve --bg 2283` | Gjør `localhost:2283` tilgjengelig som HTTPS i tailnettet |
| `tailscale serve --bg --https=8443 localhost:8096` | Samme, men på port 8443 |
| `tailscale serve --bg --tcp=25565 tcp://localhost:25565` | Videresender ren TCP (for eksempel Minecraft Java) |
| `tailscale serve status` | Viser hva som deles nå |
| `tailscale serve reset` | Fjerner alt `serve` har satt opp |
| `tailscale funnel ...` | Gjør en tjeneste **offentlig på internett**. Bare med lærerens godkjenning! |

## Fra `docker-compose.yml` til wslc

wslc kan ikke kjøre compose-filer ennå. Slik oversetter du dem:

| I compose-filen | Blir i wslc |
| --- | --- |
| hver tjeneste under `services:` | én `wslc run` |
| `container_name:` | `--name` |
| `image:` | siste ord i `wslc run` |
| `ports: - "8080:80"` | `-p 8080:80` |
| `environment:` | én `-e NØKKEL=verdi` per linje |
| `env_file: .env` | `--env-file .env`, eller `-e` for hver linje |
| `volumes: - navn:/sti` | `wslc volume create navn` + `-v navn:/sti` |
| `networks:`, eller bare at tjenestene skal snakke sammen | `wslc network create` + `--network` |
| `depends_on:` | Start containerne i riktig rekkefølge selv |
| `restart: always` | Finnes ikke. Start med `wslc start` etter omstart |
| `shm_size: 128mb` | `--shm-size 128M` (stor M) |

## PowerShell-triks

- Lange kommandoer kan deles over flere linjer med en **backtick** `` ` `` helt til slutt på linjen. Det må ikke være mellomrom etter den.
- `$Navn = "verdi"` lagrer en verdi i en variabel. Variabelen forsvinner når du lukker Terminal.
- Pil opp (`↑`) henter forrige kommando.
