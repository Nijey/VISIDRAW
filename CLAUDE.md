# VISIDRAW: regole per Claude

## Obiettivo
Pagina **HTML unica, locale e offline** (`visidraw.html`): lavagna a mano libera che trasforma lo schizzo
(schemi di rete, workflow, diagrammi di flusso) in un diagramma pulito stile Visio. Dettagli d'uso in `README.md`.

## Stack tecnico
- Solo HTML + CSS + JavaScript "vanilla" in un unico file. Niente librerie, CDN, server.
- La CSP nel `<head>` blocca ogni connessione di rete: non allentarla.
- Testi dell'utente: sempre `textContent` / nodi di testo SVG, mai `innerHTML`. Nelle esportazioni XML usare `xmlEsc`.
- Deve funzionare offline con un doppio clic (Chrome/Edge/Firefox recenti), con mouse, penna e touch (Pointer Events).

## Architettura (dentro `visidraw.html`)
1. Stato `S` = {nodes, edges, texts, inks, seq, theme}; annulla/ripeti con snapshot JSON (`commit()` dopo ogni azione).
2. Geometria (resample, RDP, inviluppo convesso, poligoni inscritti, intersezioni raggio/poligono).
3. Riconoscimento: `recognize(inks, nodes, edges)` è puro (non tocca lo stato) → nodes, edges, clusters di scritte, ink da tenere.
   Soglie in pixel dello schermo (ogni tratto salva lo zoom `k` al momento del disegno).
4. Forme (`shapePath`, `outline`, `drawIcon`) e connettori (`edgeGeom`, `orthRoute`, `orthCandidates`, `routeScore`).
   Estremo agganciato = `{n}` (automatico, metà dei lati) o `{n, p:[u,v]}` (punto fisso relativo al riquadro,
   proiettato sul contorno da `anchorPoint`; 8 punti in `ANCHORS`). Connettori agganciati: niente diagonali.
3b. Lettura della scrittura (`hwReadLocal`): `hwSegment` (righe; lettere con programmazione dinamica sui tratti in ordine
   di tempo, costo = `hwClassify` + penalità; `force` = numero di lettere imposto), `hwClassify` ($P su `GLYPHS` + lettere
   imparate; penalità di posizione, tratti `HW_MAXS`, proporzioni), vocabolario `HW_WORDS` (con ridivisione ±1/±2);
   `opt.hwUpper` = solo maiuscole; `hwLearnFrom` impara dalle correzioni (localStorage `visidraw.hwlearn`).
   `detectText`/`insideText` in `recognize()` riconoscono le scritte fatte con la penna normale.
   Scrittura sintetica per i test: `SK.hand` (`gap`, `messy`). Prima di cambiare pesi o soglie misura con scritte
   sintetiche vicine e imprecise (oltre all'autotest).
5. Rendering SVG; 6. interazione; 7. file ed esportazioni (JSON validato da `validState`, SVG, PNG, draw.io); 8. autotest.
Versione in `APP_VERSION` (aumentala a ogni rilascio).

## Modo di lavorare
- Prima di implementare cambiamenti grandi: domande sui punti ambigui, poi piano breve.
- Passi piccoli; un commit per passo, messaggi in italiano.
- Test: `visidraw.html#selftest`; aggiungi un caso (schizzo sintetico `SK.*`) per ogni bug di riconoscimento corretto.
- Risposte concise, in italiano. Codice: nomi in inglese; commenti e documentazione in italiano.
