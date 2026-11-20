# Le Monete di Valentina

App web (PWA) per iPad per imparare l'uso delle monete euro. Un solo file principale (`index.html`), nessuna installazione, nessun server, nessun dato inviato online.

## Sezioni
1. **Ordina**: 3 livelli con le monete (8, 6, 4) e 3 livelli con le banconote (6, 5, 4, livelli 4-6); 6 sistemazioni ciascuno, crescente poi decrescente, lampadina di aiuto, soglia 80%.
2. **Scomponi**: somme semplici fino a 10 per ognuna delle 8 monete e, in una sezione separata, per ognuna delle 6 banconote (5, 10, 20, 50, 100, 200 euro).
3. **Moltiplica e dividi**: equivalenze tra monete e tra banconote (una categoria per ogni banconota). Le 6 domande di ogni categoria sono di 6 tipi diversi: moltiplica, dividi, scegli il gruppo giusto, cambia la moneta (si tocca per comporre), quanto valgono in tutto, vero o falso.
4. **Negozio**: 24 prodotti. I primi 12 («Piccole spese», fino a 2 euro) si pagano con le monete; gli altri 12 («Grandi spese», da 6,50 a 180 euro) si pagano anche con le banconote. Il pagamento è libero: Valentina mette nel piatto le monete e le banconote che vuole (anche combinazioni diverse), può toglierle toccandole e preme «Ho pagato»; l'acquisto riesce se la somma è esatta. Ogni moneta messa o tolta e ogni tentativo vengono registrati nel CSV.
5. **Dati**: la sessione dura finché non si preme «Concludi sessione». Il pulsante apre il foglio di condivisione dell'iPad con il CSV già allegato (millisecondi, correttezza, quesito): si sceglie Mail e l'indirizzo. Poi l'app chiede conferma e cancella le risposte dal dispositivo; resta solo una riga per sessione con la percentuale di risposte giuste. Se la condivisione viene annullata i dati restano. Se il dispositivo non supporta la condivisione di file, il CSV viene scaricato e, se `EMAIL` è compilato, si apre una mail già indirizzata.

## File
- `index.html`: tutta l'app (HTML + CSS + JavaScript + immagini di monete e banconote + colonna sonora, tutto incorporato; pesa circa 4 MB).
- `manifest.json`, `sw.js`, icone: servono per "Aggiungi a Home" e per il funzionamento offline.

## Musica
La colonna sonora («green light journey», ricodificata a 128 kbps) parte al primo tocco, si ripete in tutte le sezioni e si ferma quando l'app va in secondo piano. Il pulsante con la nota musicale in basso a destra la spegne e la riaccende (la scelta resta salvata). Non c'è più la voce che legge le frasi. Per cambiare brano si sostituisce la costante `MUSICA_B64` (mp3 in base64) in `index.html`.

## Impostazioni da modificare
In cima al JavaScript di `index.html`, sezione `IMPOSTAZIONI`:
- `NOME`: nome usato dalla mascotte
- `EMAIL`: tuo indirizzo, usato solo come alternativa se non c'è il foglio di condivisione
- `PROVE`: numero di prove per livello
- `SOGLIA`: soglia di superamento (0.8 = 80%)

Prodotti e prezzi del negozio (in centesimi): costante `PRODOTTI`. Le banconote sono nella costante `NOTES`, le immagini in `NOTE_IMG`; `NF` regola quanto sono grandi sullo schermo rispetto alle monete.

## Pubblicazione
Qualsiasi hosting statico (Cloudflare Workers/Pages, Netlify, GitHub Pages). Per GitHub Pages: Settings > Pages > Deploy from branch > `main` / root, con i file nella radice del repository.
Se cambi `index.html`, cambia anche `C='monete-valentina-v1'` in `sw.js` (ad esempio `v2`) per forzare l'aggiornamento sull'iPad.

## Note
Le immagini delle monete e delle banconote sono ritagliate da immagini di riferimento (le banconote sono esemplari «specimen» della serie Europa; la BCE ha regole sulla riproduzione delle banconote): verifica i diritti d'uso prima di una pubblicazione fuori dal tuo lavoro. I dati di gioco restano nel browser dell'iPad (`localStorage`).


## Versione 7 — Tabelline e grafico

- **Nuova sezione «Tabelline»** (sesta voce della barra in basso): un livello per ogni numero da 1 a 10. Il primo fattore è il cesto, il secondo un frutto sempre uguale per tutto il livello (1 pera, 2 arancia, 3 fragola, 4 susina, 5 pesca, 6 cocomero, 7 ananas, 8 banana, 9 limone, 10 kiwi).
- Ogni livello ha 10 moltiplicazioni (N×1 … N×10). Al centro c'è la moltiplicazione con uno spazio vuoto dopo l'uguale: toccandolo si apre la tastiera con le cifre 0–9. Sotto, «Costruiamolo insieme»: a sinistra si scelgono i cesti, a destra i frutti in ogni cesto; i cesti si riempiono di frutta e la linea dei numeri (da 0 a 10×N) si colora a salti uguali. La bandierina sulla linea segna il risultato.
- Quando i due fattori sono diversi, in fondo allo schermo compare «RICORDA: 3 × 5 = 5 × 3».
- Conta solo il primo tentativo (come nelle altre sezioni); i tentativi successivi sono registrati come `risposta_ripetuta` e non entrano nella percentuale. Le scelte di cesti e frutti sono registrate come `tocco_cesti` e `tocco_frutti`. Soglia 80%, nessuna voce.
- **Grafico in «Dati»**: percentuale di risposte giuste per ogni sessione conclusa più la sessione in corso (cerchio vuoto), con la linea dell'obiettivo 80% e, sotto, la percentuale per sezione dell'ultima sessione. Le sessioni concluse conservano la percentuale per sezione.
- Le immagini di cesto e frutti sono incorporate nel file (ritagliate dalle immagini fornite): non servono file aggiuntivi.
- Service worker: cache `monete-valentina-v7`.
