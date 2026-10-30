# Veiledning for læreren

[← Tilbake til hovedsiden](README.md)

## Før første økt

- [ ] **Test hele «Kom i gang» og minst ett prosjekt på en elev-PC.** Kommandoene er sjekket mot kildekoden til wslc 3.0.1 og mot dokumentasjonen til hvert prosjekt, men de er ikke kjørt på en ekte Windows-PC. wslc er nytt (allment tilgjengelig fra 29. september 2026), og små endringer kan komme.
- [ ] **Avklar Tailscale med IT og personvernombud.** Opplegget forutsetter at hver elev har sin egen gratis Tailscale-konto (Personal-planen), og logger inn med Google, Microsoft eller GitHub. Sjekk Tailscales vilkår når det gjelder alder, og om skolen har egne regler for elevers bruk av skytjenester.
- [ ] **Planlegg nedlastingene.** Immich er flere GB fordelt på fire images, og maskinlæringsmodellene kommer i tillegg. Minecraft og Jellyfin er mindre, men 30 elever samtidig på skolens wifi blir tregt. Vurder å la elevene gjøre `wslc image pull` hjemme, eller spre nedlastingene utover dagen.
- [ ] **Sjekk at skolens nett ikke blokkerer Tailscale.** Tailscale virker på de fleste nett, også med klientisolasjon, fordi trafikken går ut mot internett. Test gjerne mellom to PC-er på elevnettet.

## Det som er mest usikkert

| Område | Hvorfor | Hva du kan gjøre |
| --- | --- | --- |
| **Minecraft Bedrock** | Bedrock bruker NetherNet (WebRTC) med mange UDP-porter. Det er den mest krevende kombinasjonen med wslc sitt nettverk | Test før du lar elever velge den. Fungerer den ikke, kan elevene velge Java eller Luanti |
| **Luanti med Windows-mappe** | Containeren prøver å endre eier på filene i mappen. Det kan gi advarsler på en Windows-mappe | Se i `wslc logs luanti`. Advarsler er vanligvis ufarlige |
| **Immich-oppstart** | wslc har ingen `depends_on` eller automatisk omstart. Starter serveren før databasen er klar, stopper den | Instruksjonen ber elevene vente på databasen. `wslc start immich-server` løser det |
| **Menynavn** | Immich og Jellyfin endrer brukergrensesnittet ofte | Instruksjonene har engelske menynavn i tillegg til norske |

## Progresjon og tid

Tidsanslagene på hovedsiden er grove. Regn med at første økt med «Kom i gang» tar lengre tid enn planlagt.

| Elev | Anbefalt rekkefølge |
| --- | --- |
| Nybegynner | Kom i gang → Prosjekt 3 → Prosjekt 2 (Java eller Luanti) |
| Erfaren | Kom i gang → Prosjekt 2 eller 3 → Prosjekt 1 |
| Ekstra utfordring | Prosjekt 1 del F4 (Funnel) med læreren til stede, eller Bedrock-varianten i prosjekt 2 |

## Forslag til vurdering

| Kriterium | Grunnleggende | God | Fremragende |
| --- | --- | --- | --- |
| **Fungerende tjeneste** | Tjenesten kjører på egen PC | Tjenesten er tilgjengelig på mobil eller for medelev via Tailscale | Tjenesten er satt opp med tilgangsstyring, backup og startskript |
| **Driftslogg** | Kommandoer er listet | Feil og løsninger er beskrevet | Loggen er så god at en annen kan gjenskape oppsettet |
| **Forståelse** | Kan forklare hva en container er | Kan forklare porter, volumer og nettverk i eget oppsett | Kan begrunne valg og drøfte sikkerhet og personvern |
| **Tilgang og sikkerhet** | Har sterke passord | Har testet hvem som har tilgang | Kan forklare lagene i tilgangsstyring med egne testresultater |

## Når wslc får `compose`

Microsoft har sagt at `wsl compose up` kommer. Da kan prosjekt 1 forenkles til den offisielle compose-filen. Oversettelsen fra compose til wslc-kommandoer er likevel en god læringsøvelse, så det kan være verdt å beholde del A.

## Kilder

- [Microsoft Learn – Get started with WSL containers](https://learn.microsoft.com/en-us/windows/wsl/tutorials/wsl-containers)
- [Microsoft Learn – WSL container settings](https://learn.microsoft.com/en-us/windows/wsl/wsl-container-settings)
- [microsoft/WSL på GitHub](https://github.com/microsoft/WSL) (kildekoden til wslc)
- [Tailscale – Serve](https://tailscale.com/kb/1242/tailscale-serve) og [Sharing](https://tailscale.com/kb/1084/sharing)
- [Immich – Docker Compose-installasjon](https://docs.immich.app/install/docker-compose)
- [itzg/docker-minecraft-server](https://github.com/itzg/docker-minecraft-server), [itzg/docker-minecraft-bedrock-server](https://github.com/itzg/docker-minecraft-bedrock-server), [linuxserver/docker-luanti](https://github.com/linuxserver/docker-luanti)
- [Jellyfin – dokumentasjon](https://jellyfin.org/docs/)
