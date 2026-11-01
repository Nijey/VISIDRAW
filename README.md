# VisiDraw

Lavagna per disegnare **a mano libera** (penna, dito o mouse) schemi di rete, workflow e diagrammi di flusso.
Con **✨ Elabora** lo schizzo diventa un diagramma pulito, come fatto con Visio: forme regolari e allineate,
connettori agganciati alle forme, frecce e testi.

Un solo file, `visidraw.html`: si apre con un doppio clic, funziona **offline** (nessuna libreria, nessuna connessione).

## Come si usa
1. **Penna** (`P`): disegna rettangoli, ovali/cerchi, rombi, triangoli, parallelogrammi, nuvole; poi linee e frecce fra le forme.
2. **Scrittura a mano** (`W`, oppure un altro clic sulla penna già attiva): scrivi le etichette dentro le forme o vicino
   alle frecce. In questa modalità i tratti (viola) diventano **sempre testo**, mai forme: anche una "O" grande resta una lettera.
   Sul tablet si scrive anche tenendo premuto il tasto laterale della penna; il retro della penna cancella.
   In alternativa usa **Testo** `T` da tastiera.
3. **✨ Elabora** (`Invio`): riconosce forme, connettori e frecce e chiede di trascrivere le scritte a mano
   (lasciando vuoto restano a mano libera). Se il browser ha il riconoscimento della scrittura, le precompila.
4. **Seleziona** (`V`): sposta, ridimensiona, doppio clic per il testo, pannello per forma, colori, frecce e percorso.

Altro: tavolozza di forme e icone di rete (router, switch, firewall, server, PC, portatile, AP, stampante, telefono).
Scrivendo *router, switch, firewall, server, pc, AP, internet, database*… la forma diventa l'icona corrispondente.
Modalità **Auto**: forme e linee vengono elaborate da sole dopo una pausa. Menu **Esempi** per provare subito.

## Cosa riconosce
| Disegno | Risultato |
|---|---|
| Tratto chiuso (anche in più tratti consecutivi) | rettangolo, ellisse/cerchio, rombo, triangolo, parallelogramma, nuvola |
| Linea dritta | connettore diretto |
| Linea a gomito | connettore ortogonale (rispetta lati di uscita/entrata disegnati) |
| Punta a "V" (nello stesso tratto o separata) | freccia (anche doppia) |
| Estremo vicino a una forma | connettore agganciato: segue la forma quando la sposti |
| Tratti fatti in modalità Scrittura | sempre scritte da trascrivere, a qualunque dimensione |
| Tratti piccoli (in modalità Forme) | scritte da trascrivere (dentro la forma → etichetta; vicino a un connettore → etichetta del connettore) |

## Salvataggio ed esportazione
- **Salva/Apri** in JSON (`.visidraw.json`); salvataggio automatico nel browser.
- **PNG** (alta risoluzione), **SVG** vettoriale, **draw.io** (`.drawio`): si apre in diagrams.net e da lì
  *File › Esporta come › VSDX* per Visio.

## Test
`visidraw.html#selftest` (o *Vista › Autotest del riconoscimento*): genera schizzi sintetici "a mano"
con 5 varianti casuali per caso e verifica il riconoscimento.
