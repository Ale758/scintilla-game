# Scintilla

Un endless runner arcade in stile "corsa al tramonto" — salta gli ostacoli, abbassati per schivare quelli che volano, raccogli i power-up e resta accesa più a lungo possibile.

Un unico file HTML autosufficiente: HTML5 Canvas, JavaScript puro, zero dipendenze esterne.

## Come si gioca

- **Salto**: SPAZIO, freccia SU, oppure tocco nella metà alta dello schermo
- **Abbassarsi** (per schivare gli ostacoli volanti): freccia GIÙ, oppure tocco nella metà bassa dello schermo
- **Power-up**: raccogli i bagliori turchesi — uno scudo (assorbe un colpo) e un doppio salto (un salto extra a mezz'aria)

## Come pubblicarlo gratis

### GitHub Pages
1. Crea un nuovo repository su GitHub e carica `index.html` (e questo `README.md`)
2. Vai su **Settings → Pages**
3. In "Branch" scegli `main` e la cartella `/ (root)`, poi salva
4. Dopo un minuto il gioco è online su `https://<tuo-utente>.github.io/<nome-repo>/`

### Alternative
Funziona altrettanto bene su **Vercel** (importa il repository, zero configurazione) o su **itch.io** (carica lo zip come progetto HTML5, spuntando "This file will be played in the browser").

## Personalizzarlo

Il codice dentro `index.html` è diviso in sezioni commentate:

1. Riferimenti DOM e costanti
2. Stato di gioco
3. Logica (salto, abbassarsi, power-up, spawn, collisioni)
4. Disegno (sfondo, ostacoli, power-up, giocatore, particelle)
5. Game loop e input

Le costanti principali per cambiare sensazione e difficoltà sono in cima allo script: `GRAVITY`, `JUMP_V`, `SHIELD_DURATION`, `SCORE_UNLOCK_FLYING`, `SCORE_UNLOCK_PATTERNS`.

Il record è salvato solo per la sessione corrente (dentro Claude il local storage non è supportato). Una volta ospitato fuori da Claude puoi aggiungere `localStorage` per renderlo persistente tra le visite.
