# Scintilla

Un endless runner arcade in stile "corsa al tramonto" — salta gli ostacoli, abbassati per schivare quelli che volano, raccogli i power-up e resta accesa più a lungo possibile.

Un unico file HTML autosufficiente: HTML5 Canvas, JavaScript puro, zero dipendenze esterne.

## Come si gioca

- **Salto**: SPAZIO, freccia SU, oppure tocco nella metà alta dello schermo
- **Abbassarsi** (per schivare gli ostacoli volanti): freccia GIÙ, oppure tocco nella metà bassa dello schermo
- **Pausa**: tasto P o ESC, oppure il pulsante in alto durante la partita
- **Muto**: il pulsante a forma di altoparlante in alto — disattiva sia la musica che gli effetti sonori
- **Power-up**: raccogli i bagliori turchesi — uno scudo (assorbe un colpo), un doppio salto (un salto extra a mezz'aria) e un moltiplicatore di punti (×2 per qualche secondo)

C'è anche una musica di sottofondo generata al volo (nessun file audio, quindi zero problemi di copyright), che si intensifica in tre livelli man mano che la partita accelera.

### Due modalità

- **Normale**: quando vieni colpito è game over, si ricomincia da capo.
- **Zen**: quando vieni colpito, invece di finire, torni indietro di circa 2 secondi — come se l'ostacolo non fosse mai arrivato — e continui. Niente game over, pensata per giocare senza pressione. La cornice diventa verde acqua per riconoscerla a colpo d'occhio.

Si sceglie con due pulsanti nella schermata iniziale (e in quella di game over, per cambiare modalità alla partita successiva). Ogni modalità tiene il proprio record separato, visibile in alto a destra.

### Record

Il punteggio migliore si salva automaticamente nel browser (localStorage) e resta ricordato tra una visita e l'altra — **ma solo una volta che il gioco è ospitato fuori da Claude** (GitHub Pages, Vercel, ecc.). Nell'anteprima dentro Claude il record vale solo per la sessione corrente, perché Claude non permette il salvataggio nel browser.

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
