# VisiDraw

Lavagna per disegnare **a mano libera** (penna, dito o mouse) schemi di rete, workflow e diagrammi di flusso.
Con **✨ Elabora** lo schizzo diventa un diagramma pulito, come fatto con Visio: forme regolari e allineate,
connettori agganciati alle forme, frecce e testi.

Un solo file, `visidraw.html`: si apre con un doppio clic, funziona **offline** (nessuna libreria, nessuna connessione).

## Come si usa
1. **Penna** (`P`): disegna rettangoli, ovali/cerchi, rombi, triangoli, parallelogrammi, nuvole; poi linee e frecce fra le forme.
   Nella barra scegli lo **spessore** (sottile, medio, grosso) e il **colore** (nero, blu, rosso, verde, viola).
   Il nero medio dà i colori del tema; con altri colori o spessori forme (bordo), connettori e testi
   mantengono colore e spessore del tratto. Valgono anche per la scrittura a mano.
2. **Scritte**: con la stessa penna scrivi in **stampatello** dentro le forme o accanto alle frecce.
   Le lettere vicine, di altezza simile e allineate vengono riconosciute come scritta (anche grandi o chiuse come O e D);
   anche i tratti tracciati dentro una forma diventano la sua etichetta. Sul tablet, tenendo premuto il tasto laterale
   della penna, il tratto è sempre scritta; il retro della penna cancella. In alternativa usa **Testo** `T` da tastiera.
3. **✨ Elabora** (`Invio`): riconosce forme, connettori e frecce e **legge le scritte a mano**: la finestra di
   trascrizione arriva già compilata, tu confermi con `Invio` o correggi (svuotando un campo la scritta resta a mano libera).

### Lettura della scrittura a mano
Funziona offline, senza librerie, con lo **stampatello** (il corsivo legato non si può dividere in lettere).
Con *Vista › Scrivo in stampatello MAIUSCOLO* (attivo di default, anche nella finestra di trascrizione) considera solo
maiuscole e cifre ed è più preciso.
- **Divisione in lettere guidata dal riconoscimento**: i tratti, nell'ordine in cui li hai fatti, vengono raggruppati
  nel modo che dà le lettere più riconoscibili, quindi funziona anche con lettere **molto vicine o che si toccano**.
- Ogni lettera viene confrontata con i modelli (algoritmo $P, con varianti strette, larghe e oblique); numero di tratti,
  proporzioni e vuoti interni evitano di scambiare due lettere attaccate per una sola.
- Un vocabolario di parole frequenti negli schemi (router, switch, firewall, datacenter, internet, VLAN…) corregge le
  parole, anche ridividendole se una lettera era stata spezzata o unita alla vicina.
- **Impara dalle tue correzioni**: ogni trascrizione confermata aggiunge le tue lettere e le tue parole (salvate nel browser);
  *Vista › Dimentica la mia scrittura* le azzera.

### Punti di aggancio e connettori
Ogni forma ha **8 punti di aggancio** (croci blu, visibili passando sulla forma o selezionandola): i 4 spigoli e
le 4 metà dei lati. I connettori agganciati alle forme sono **ortogonali** (solo tratti orizzontali e verticali,
mai diagonali): da uno spigolo escono in orizzontale o in verticale.
- **Aggancio automatico**: il connettore sceglie da solo i lati migliori e li ricalcola quando sposti le forme.
- **Nuovo connettore**: trascina da una croce verso un'altra forma.
- **Spostare un connettore**: con **Seleziona** afferra direttamente il suo estremo (anche se è sopra una croce)
  e trascinalo su un'altra croce o su un'altra forma; *Maiusc* + trascina da una croce crea invece un nuovo connettore.
- **Punto fisso**: trascina un estremo del connettore su una croce (cerchio verde) oppure in un **punto
  intermedio** lungo il contorno; il punto resta in proporzione anche ridimensionando la forma.
  Rilasciandolo dentro la forma torna all'aggancio automatico (anche con *Aggancio › Automatico* nel pannello).

Altro: tavolozza di forme e icone di rete (router, switch, Catalyst/switch L3, firewall, server, datacenter, PC, portatile, AP, modem, stampante, telefono).
Sezioni espandibili: *Dispositivi e videosorveglianza* (iPhone, Android, iPad, tablet Android, server Linux, NAS a 2 e 4 dischi, telecamera, DVR/NVR) e
*Casa e intrattenimento* (Fire TV, console, luce Hue, colonnina di ricarica EV, Echo, soundbar).
Anche le icone hanno bordo (colore, spessore, tratteggio); con un riempimento chiaro i dettagli diventano scuri e compare
un contorno grigio, così restano visibili sul foglio bianco.
Scrivendo *router, switch, catalyst, firewall, server, datacenter, modem, pc, AP, internet, database*… la forma diventa l'icona corrispondente.
Vale anche per *iPhone / smartphone, Android, iPad / tablet, tablet Android / Galaxy Tab, Linux / Ubuntu / server Linux, NAS (4 dischi) / NAS 2 (2 dischi), telecamera / TVCC / CCTV, DVR / NVR,
TV / Fire TV, console / PS5 / Xbox, luce / Hue, EV / colonnina / wallbox, Echo / Alexa, soundbar*.
Modalità **Auto**: forme e linee vengono elaborate da sole dopo una pausa. Menu **Esempi** per provare subito.

## Cosa riconosce
| Disegno | Risultato |
|---|---|
| Tratto chiuso (anche in più tratti consecutivi) | rettangolo, ellisse/cerchio, rombo, triangolo, parallelogramma, nuvola |
| Linea dritta fra forme | connettore ortogonale (dritto se le forme sono allineate) |
| Linea che parte da uno spigolo | connettore agganciato a quello spigolo |
| Linea a gomito | connettore ortogonale (rispetta lati di uscita/entrata disegnati) |
| Punta a "V" (nello stesso tratto o separata) | freccia (anche doppia) |
| Estremo vicino a una forma | connettore agganciato: segue la forma quando la sposti |
| Lettere vicine e allineate, o tratti dentro una forma | scritte (lette e proposte nella trascrizione) |
| Tratti piccoli | scritte da trascrivere (dentro la forma → etichetta; vicino a un connettore → etichetta del connettore) |

## Testo
Carattere (Calibri, Arial, Consolas, Comic Sans, Ebrima) e dimensione si scelgono:
- per tutto il diagramma in *Vista › Carattere*;
- per gli oggetti selezionati nel pannello proprietà (strumento **Seleziona**);
- per le scritte appena trascritte nella finestra di trascrizione.

## Salvataggio ed esportazione
- **Salva/Apri** in JSON (`.visidraw.json`); salvataggio automatico nel browser.
- **PNG** (alta risoluzione), **SVG** vettoriale, **draw.io** (`.drawio`): si apre in diagrams.net e da lì
  *File › Esporta come › VSDX* per Visio.

## Test
`visidraw.html#selftest` (o *Vista › Autotest del riconoscimento*): genera schizzi sintetici "a mano"
con 5 varianti casuali per caso e verifica il riconoscimento.
