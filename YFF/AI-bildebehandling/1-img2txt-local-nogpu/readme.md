# Elevinstruks: Lag en lokal “Image Captioner” (ComfyUI + Ollama)

## Mål

Du skal lage et ComfyUI-workflow som:

1. tar inn et bilde
2. sender bildet til en lokal LLM (Ollama)
3. viser en tekst-beskrivelse (caption) i ComfyUI

---

## Før du begynner

Du trenger:

* Windows PC (uten GPU går fint)
* Internett (for nedlasting første gang)
* Ca. 5 GB ledig plass (avhenger av modell)

---

# Del 1 – Installer og start ComfyUI

## 1. Last ned ComfyUI (Windows)

1. Last ned ComfyUI for Windows [Last ned comfy](https://github.com/comfyanonymous/ComfyUI/releases/latest/download/ComfyUI_windows_portable_nvidia.7z)
2. Pakk ut til f.eks:

* `C:\ComfyUI\`

✅ **Sjekkpunkt:** Du har en mappe `C:\ComfyUI\` med `.bat`-filer inni.

## 2. Start ComfyUI (CPU)

1. Åpne `C:\ComfyUI\`
2. Dobbeltklikk:

* `run_cpu.bat` (hvis den finnes)
  eller
* `run.bat` / `start.bat` (navn kan variere)

3. Når terminalen viser at serveren kjører, åpne nettleser:

* `http://127.0.0.1:8188`

✅ **Sjekkpunkt:** Du ser ComfyUI-griden (node-canvas).

> Ikke lukk terminalvinduet mens du jobber. Det er “serveren”.

---

# Del 2 – Installer ComfyUI Manager (viktig)

ComfyUI Manager lar dere installere noder fra UI med noen klikk.

## 1. Installer Git (hvis nødvendig)

1. Åpne PowerShell
2. Skriv:

```powershell
git --version
```

* Hvis du får en versjon → Git er ok.
* Hvis du får feil → installer **Git for Windows** (standardvalg er fint), og test kommandoen igjen.

## 2. Klon ComfyUI Manager

1. Åpne PowerShell
2. Gå til `custom_nodes`:

```powershell
cd C:\ComfyUI\custom_nodes
```

3. Klon Manager:

```powershell
git clone https://github.com/ltdrdata/ComfyUI-Manager.git
```

✅ **Sjekkpunkt:** Mappa `C:\ComfyUI\custom_nodes\ComfyUI-Manager` finnes.

## 3. Restart ComfyUI og sjekk at Manager dukker opp

1. Lukk ComfyUI (Ctrl + C i terminalen)
2. Start ComfyUI igjen (`run_cpu.bat`)
3. Oppdater nettleseren

✅ **Sjekkpunkt:** Du ser “Manager”/“ComfyUI Manager” i menyen (ofte oppe i UI).

---

# Del 3 – Installer Ollama (lokal LLM-server)

## 1. Installer Ollama

1. Last ned og installer **Ollama for Windows** her [https://ollama.com/](https://ollama.com/)
2. Etter installasjon kjører den vanligvis som en lokal tjeneste.

## 2. Last ned en modell ved å kjøre første chat (viktig!)

1. Åpne PowerShell
2. Kjør (samme som dere brukte):

```powershell
ollama run gemma3:4b
```

3. Når den starter, skriv en kort setning (f.eks. “hei”) → da lastes modellen ned.
4. Skriv `exit` for å avslutte chatten.

## 3. Sjekk at modellen er installert

```powershell
ollama list
```

✅ **Sjekkpunkt:** Du ser `gemma3:4b` i lista.

> Hvis modellen blir for treg på noen PC-er: bytt til en mindre modell senere. Men start med samme for å følge oppskriften.

---

# Del 4 – Installer comfyui-ollama via Manager

1. Åpne ComfyUI i nettleser: `http://127.0.0.1:8188`
2. Åpne **Manager**
3. Gå til **Install / Custom Nodes** (navn kan variere)
4. Søk etter:

* `comfyui-ollama`

5. Klikk **Install**
6. Når den er ferdig: **Restart ComfyUI** (Manager har ofte en “Restart”-knapp, ellers stopp/start fra terminal).

✅ **Sjekkpunkt:** Du kan legge til noder som heter:

* **Ollama Connectivity**
* **Ollama Chat**

---

# Del 5 – Bygg workflowet (MWE)

Du skal lage 4 noder og koble dem.

## 1. Legg til noder

Høyreklikk på canvas → Add Node / Search:

* **Load Image**
* **Ollama Connectivity**
* **Ollama Chat**
* **Preview as Text** (eller “Preview Text”)

## 2. Koble nodene (akkurat slik)

Koble disse:

### A) Bilde inn til chat

* `Load Image : IMAGE` → `Ollama Chat : images`

### B) Tilkobling inn til chat

* `Ollama Connectivity : connection` → `Ollama Chat : connectivity`

### C) Resultat til visning

* `Ollama Chat : result` → `Preview as Text : source`

✅ **Sjekkpunkt:** Du har 3 kabler, og “Preview as Text” står klar til å vise tekst.

---

# Del 6 – Fyll inn riktige innstillinger

## 1) Ollama Connectivity

* **url:** `http://127.0.0.1:11434`
* **model:** `gemma3:4b`
* **keep_alive:** `5`
* **keep_alive_unit:** `minutes`
* Trykk **Reconnect** hvis den finnes.

✅ **Sjekkpunkt:** Ingen feilmelding, og modellen kan velges.

## 2) Ollama Chat (prompt)

Skriv inn:

**System (øverst):**

> `You are an AI artist.`

**User (nederst):**

> `describe this image using natural language`

(Valgfritt)

* **think:** false
* **format:** text

---

# Del 7 – Kjør og test

1. I **Load Image**: velg et bilde
2. Trykk **Queue Prompt**

✅ **Resultat:** “Preview as Text” viser en tekst-beskrivelse av bildet.

---

# Feilsøking (når noe går galt)

## 1) Ingen respons / “connection refused”

* Sjekk at Ollama kjører:

```powershell
ollama list
```

* Sjekk URL i Connectivity: `http://127.0.0.1:11434`
* Prøv **Reconnect** og restart ComfyUI.

## 2) Modellen finnes ikke i ComfyUI

* Kjør minst én gang:

```powershell
ollama run gemma3:4b
```

* Deretter: restart ComfyUI.

## 3) Det går veldig tregt

* Bruk mindre bilde (lavere oppløsning)
* Bytt modell til en mindre (spør lærer / meg, så får dere forslag som passer CPU)

## 4) Manager viser ikke “comfyui-ollama”

* Oppdater node-lista i Manager
* Sjekk at dere restartet ComfyUI etter installasjon

---

# Levering (hva dere skal vise)

* Screenshot av workflowet (4 noder koblet)
* Et eksempelbilde dere testet med
* Teksten som kom ut i “Preview as Text”
