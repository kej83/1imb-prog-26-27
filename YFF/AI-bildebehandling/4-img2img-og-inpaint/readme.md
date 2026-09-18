# AI-bildebehandling del 4: Image2Image og Inpaint i ComfyUI 

## Mål

Etter denne økta skal du kunne:

* bruke **img2img** (image-to-image) i ComfyUI ved å konvertere et bilde til **latent**
* teste **denoise** (f.eks. 0.2 → 0.8) og forklare hva som skjer
* lage og forbedre en **prompt** som endrer noe i bildet (bakgrunn, farger, detaljer på person)
* bruke **MaskEditor** og kjøre en **minimal inpaint-workflow**
* dokumentere resultater med kommentarer i et **Word-dokument**

---

## Før du starter

Du trenger:

* ComfyUI åpent og workflowen dere har jobbet med tidligere. Se del 2: `2-more-txt2img`.
* Et bilde fra **Pinterest / Google** (last ned eller kopier til PC-en)
* Word-dokument klart til notater (se mal under)

**Viktig:** Lag en mappe der du lagrer:

* originalbilde
* resultatbilder (navn med denoise-verdi)
* Word-dokumentet

Eksempel på filnavn:

* `original.jpg`
* `img2img_denoise_0.2.png`
* `img2img_denoise_0.5.png`
* `inpaint_hair_denoise_0.3.png`

---

# Del 1: Image2Image (img2img)

## A) Finn et bilde og last det inn

1. Finn et bilde på Pinterest/Google (helst med tydelig motiv).
2. Last ned bildet.
3. I ComfyUI: legg til node **Load Image**

   * Dobbeltklikk i tomt område → søk `Load Image`
4. Velg bildet ditt i **Load Image**.

---

## B) Bytt ut “Empty Latent” med “Image → Latent”

Du skal nå bruke bildet som startpunkt, ikke et tomt latent.

1. Finn noden dere brukte som starter generering (ofte **Empty Latent Image**).
2. Fjern/ignorer den, og legg til en node som konverterer bildet til latent.

Vanlige noder (kan variere litt etter workflow):

* **VAE Encode**
* **VAE Encode (Tiled)** (noen bruker tiled for store bilder)

**Kobling (typisk):**

* `Load Image` → (IMAGE) → `VAE Encode`
* `VAE Encode` → (LATENT) → `KSampler` (latent_image input)

> Tips: Hvis du mangler node, dobbeltklikk og søk etter navnet.
> Hvis du fortsatt ikke finner, søk på nett: **"simple img2img workflow comfyui"** og se hvilke noder de bruker.

---

## C) Prompt til bildet (og endre noe!)

### 1) Få en start-prompt

* Last opp bildet til **ChatGPT eller Gemini**
* Be om en prompt som passer til modellen dere bruker, f.eks.:
  **“Lag en detaljert bildeprompt optimalisert for Z Image Turbo / turbo-modell.”**

### 2) Du MÅ endre noe i prompten

Velg minst én endring:

* **Bakgrunn:** “from indoor room to outdoor street at sunset”
* **Farger:** “cool tones” → “warm tones”, “pastel palette”
* **Person:** hår, klær, ansiktsuttrykk, tilbehør (hatt, jakke, smykker)
* **Stil/lys:** “soft studio lighting” → “dramatic cinematic lighting”

Skriv både:

* **Original prompt**
* **Din endrede prompt**

---

## D) Test denoise (viktig!)

Finn **denoise** i `KSampler`.

Test minst disse verdiene:

* 0.2
* 0.4
* 0.6
* 0.8

**Hva betyr denoise? (enkelt forklart)**

* **Lav denoise (0.2–0.3):** Bildet beholder mye av originalen. Små endringer.
* **Medium (0.4–0.6):** Tydelige endringer, men originalen er fortsatt synlig.
* **Høy (0.7–0.9):** Bildet kan endre seg mye og “bli et nytt bilde”.

**Viktig regel:** Jo høyere denoise, jo mindre “låst” er du til originalbildet.

---

# Del 2: Dokumentasjon i Word (obligatorisk)

## Lag en enkel rapport (1–2 sider)

**Innhold:**

1. Skjermbilde av workflow (valgfritt, men fint)
2. Originalbilde
3. Resultater med denoise 0.2 / 0.4 / 0.6 / 0.8
4. Kommentarer: hva endret seg, hva ble best, hvorfor?

### Mal du kan kopiere inn i Word

**Tittel:** Img2Img test – (navn) – (dato)

**Bilde:** (sett inn original)

**Prompt (fra AI):**
…

**Min endring i prompt:**
…

**Resultater:**

* **Denoise 0.2:** (sett inn bilde)
  Kommentar: Hva ble annerledes? Hva ble likt?
* **Denoise 0.4:** (sett inn bilde)
  Kommentar: …
* **Denoise 0.6:** (sett inn bilde)
  Kommentar: …
* **Denoise 0.8:** (sett inn bilde)
  Kommentar: …

**Konklusjon (3–5 setninger):**

* Hvilken denoise likte du best og hvorfor?
* Når ville du brukt lav vs høy denoise?

---

# Del 3: Inpaint i ComfyUI (MaskEditor)

## A) Åpne MaskEditor

1. Høyreklikk på bildet i **Load Image**-noden
2. Velg **Open in MaskEditor**
3. Maskér et område, f.eks.:

   * bare håret
   * bare jakka
   * bare bakgrunn (himmel/vegg)

**Tips for maske:**

* Zoom inn
* Maskér litt større enn området du vil endre (for naturlige overganger)
* Bruk “feather/blur” hvis tilgjengelig (mykere kant)

---

## B) Finn en minimal inpaint-workflow (nett-søk)

Søk på:

* **“minimal inpaint workflow comfyui”**
* **“comfyui inpaint basic nodes”**

Målet er å finne hvilke noder som mangler hos deg, og så:

* dobbeltklikke i ComfyUI
* søke opp noden
* koble den inn

---

## C) Minimal inpaint: typiske noder og idé

Det finnes flere varianter, men en “klassisk minimal” inpaint består ofte av:

**Nødvendig:**

* `Load Image`
* `Mask` (fra MaskEditor / eller mask-output)
* `Checkpoint Loader`
* `CLIP Text Encode` (prompt + ev. negativ prompt)
* `VAE Encode (for Inpainting)` **eller** `VAE Encode` + en node som bruker mask på latent
* `KSampler`
* `VAE Decode`
* `Save Image`

**Vanlig mask-løsning i latent:**

* en node som heter noe som:

  * **Set Latent Noise Mask**
  * eller “latent mask” / “apply mask to latent”
  * (navn varierer etter versjon/nodes)

**Hva skjer i inpaint?**

* Masken forteller modellen: “Endre bare dette området”
* Resten av bildet skal helst forbli likt originalen

---

## D) Inpaint-oppgave: Bytt hårfarge

1. Maskér bare håret i MaskEditor
2. Prompt eksempel:

   * “change hair to deep copper red, natural hair texture, realistic lighting”
3. Test denoise:

   * lav: 0.25–0.35
   * medium: 0.45–0.60
   * høy: 0.70–0.85

**Hva du skal se etter:**

* Lav denoise: små, forsiktige endringer (kan bli for svakt)
* Høy denoise: større endring, men kan “ødelegge” detaljer eller påvirke resten

---

# Del 4: Dokumentasjon for Inpaint (i samme Word)

Legg til en ny seksjon:

**Inpaint – hår**

* Maskescreenshot (valgfritt)
* Resultatbilder:

  * denoise lav
  * denoise medium
  * denoise høy
* Kommentarer:

  * Ble bare håret endret?
  * Ble kantene fine?
  * Når ble det “for mye”?

---

## Levering

Du leverer:

* Word-dokument (med bilder + kommentarer)
* (valgfritt) en mappe med resultatbildene

---

## Hjelp og feilsøking (kort)

* Finner du ikke node? → dobbeltklikk → søk → prøv synonymer (“VAE Encode”, “inpaint”, “mask latent”)
* Blir hele bildet endret under inpaint? → sjekk at mask faktisk er koblet riktig inn i latent/mask-noden
* Ingenting endrer seg? → denoise for lav, eller prompt for svak/uklar
