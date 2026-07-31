# CLAUDE.md — Sito Marco Mognon

> File di contesto per Claude Code. Leggilo all'avvio di ogni sessione.
> Il progetto è gestito da Sandro (sviluppo/design) per conto di Marco Mognon (cliente).
> Si lavora in **italiano**. Comunicazione concisa. Tolleranza zero per regressioni: verifica ogni modifica prima di consegnarla.

## Cos'è
Sito **one-pager vetrina** (niente form) per **Marco Mognon — Generative AI + Motion Designer**, Milano.
Design fornito su Figma dal cliente, in tre viste (desktop / tablet / mobile). Va replicato **fedele**, non reinterpretato.

- Figma: https://www.figma.com/design/28CGYnRROHt75S3leUqx5J/Ferrari?node-id=43-497&m=dev (node `43-497`)
- Per leggere il Figma in Dev Mode: MCP `figma-desktop` (Figma desktop aperto + Dev Mode MCP server attivo).

## Stack
- **Sito**: HTML/CSS statico, un solo file `index.html` con CSS inline. JS minimo (solo il player video). Niente framework, niente build step.
- **Font**: **Geist** via Google Fonts (fallback `Helvetica Neue, Helvetica, Arial`).
- **Hosting**: Netlify. Oggi è drag-and-drop di uno zip; il passo successivo è repo **GitHub → Netlify** (deploy automatico a ogni commit).
- **Video**: **Vimeo** (embed via ID, niente self-host del file).
- **Slideshow** (futuro): **Swiper.js**.
- **CMS editoriale** (prossimo step): **Decap CMS** + auth **DecapBridge** (così Marco edita da `/admin` senza account GitHub).

## Struttura della pagina (6 sezioni, in ordine)
1. **hero** — poster a tutta pagina (`assets/poster.jpg`) + velatura scura in basso + testo bianco in basso a sinistra ("Generative AI + Motion Designer" + sottotitolo).
2. **intro** — fondo cream, "Ciao!" + due paragrafi, colonna stretta a sinistra.
3. **reel** — banda video a tutta larghezza. Poster = `assets/volcano.jpg`, pulsante play. **Pronta per Vimeo**: inserire l'ID in `data-vimeo-id="…"` sul `.reel__frame` e al click carica l'embed.
4. **services** — fondo periwinkle. Etichetta "Cosa Faccio" + lista grande; ultima riga "+Altro? Chiedimi!" in viola. Su desktop layout a due colonne (etichetta | lista).
5. **gallery** — banda immagine a tutta larghezza (`assets/fashion.jpg`). Strutturata per diventare uno slideshow Swiper.
6. **footer** — fondo cream. "Marco Mognon" + ruolo + link (sito.com / email / Milano based / LinkedIn) + copyright.

## Token di design (sorgente di verità — verificati via Figma MCP)
```
--cream:    #F2F2F2                 /* fondo intro + footer (grigio chiaro) */
--peri:     #0015FF                 /* fondo "Cosa Faccio" (blu elettrico) */
--violet:   rgba(220,212,255,0.5)   /* accento "+Altro? Chiedimi!" (lilla tenue) */
--ink:      #0015FF                 /* testo principale (blu) */
--list:     #F7F4EB                 /* testo lista su blu */
--hero-fg:  #F2F2F2                 /* testo bianco hero */
font: "Geist"
gutter (margine contenuti): 6.5% mobile · 8% tablet · 12% desktop
breakpoint: 768px (tablet) · 1100px (desktop)
scale tipografica (da Figma):
  Display (76px): font-weight 400, line-height .95,  letter-spacing -0.06em
  Header  (32px): font-weight 500, line-height 1.09, letter-spacing -0.05em
  Para 1  (18px): font-weight 400, line-height 1.35, letter-spacing -0.02em
  Para 3  (14px): font-weight 400, line-height 1.4,  letter-spacing 0
hero overlay: rgba(0,0,0,0.4) solid (no gradiente)
```

## File
```
index.html          # pagina unica, CSS inline
assets/poster.jpg   # hero (poster vintage halftone) — PLACEHOLDER
assets/volcano.jpg  # poster del video — PLACEHOLDER
assets/fashion.jpg  # banda gallery — PLACEHOLDER
CLAUDE.md           # questo file
```

## Da fare (priorità)
1. **Video**: inserire l'ID Vimeo reale in `data-vimeo-id`.
2. **Link**: URL reali per `sito.com` e LinkedIn (ora segnaposto).
3. **Immagini**: sostituire poster/volcano/fashion con i lavori veri di Marco (e verificare i diritti d'uso — sembrano stock).
4. **CMS**: agganciare Decap CMS (campi editabili: copy hero, "Ciao!", ID video, lista servizi, immagini gallery, footer) + repo GitHub→Netlify + DecapBridge.
5. **Slideshow**: convertire la banda gallery in Swiper quando serve.

## Convenzioni
- Fedeltà al Figma prima di tutto: i valori dei token e il layout non si "migliorano" senza motivo.
- QA visivo prima di consegnare: screenshot a 1440 / 820 / 390 (headless). Una modifica a una sezione non deve romperne un'altra.
- Mantenere i contenuti sincronizzati se vengono duplicati.
- Ottimizzare le immagini per il web (il poster è un retino rumoroso: resta ~450KB).
