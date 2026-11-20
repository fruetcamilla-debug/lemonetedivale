# Come mettere «Le Monete di Valentina» su GitHub (senza programmare)

Alla fine l'app avrà un indirizzo internet tutto suo e si potrà installare sull'iPad. Servono circa 10 minuti.

## Cosa c'è nella cartella
Questi 6 file devono stare **tutti insieme, nella stessa cartella principale**, senza sottocartelle:

- `index.html` (l'app, con immagini e musica dentro)
- `manifest.json`
- `sw.js`
- `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`

`README.md` e questa guida sono facoltativi.

## Passo 1 – Crea un account GitHub
1. Vai su **github.com** e premi **Sign up**.
2. Inserisci mail, password e un nome utente (per esempio `mario-rossi`). Il nome utente farà parte dell'indirizzo dell'app.
3. Conferma la mail che GitHub ti manda.

## Passo 2 – Crea il «deposito» (repository)
1. In alto a destra premi il **+** e poi **New repository**.
2. In *Repository name* scrivi: `monete-valentina`
3. Lascia selezionato **Public** (serve pubblico per l'indirizzo gratuito).
4. Spunta **Add a README file**.
5. Premi **Create repository**.

## Passo 3 – Carica i file
1. Nella pagina del deposito premi **Add file** e poi **Upload files**.
2. Dal computer, apri la cartella `monete-valentina` e **seleziona tutti i file** al suo interno (non la cartella!). Trascinali nella pagina.
3. Aspetta che finiscano di caricarsi. `index.html` è grande (circa 4 MB), quindi può volerci un po'.
4. In basso premi **Commit changes**.

Controlla che nella lista del deposito si vedano tutti e 6 i file.

## Passo 4 – Attiva l'indirizzo internet (GitHub Pages)
1. Nel deposito premi **Settings** (l'ingranaggio, in alto).
2. Nel menu a sinistra premi **Pages**.
3. Sotto *Build and deployment*, in **Source** scegli **Deploy from a branch**.
4. In **Branch** scegli **main**, accanto lascia **/ (root)** e premi **Save**.
5. Aspetta 1–2 minuti e ricarica la pagina: in alto compare «Your site is live at…».

L'indirizzo sarà: `https://IL-TUO-NOME-UTENTE.github.io/monete-valentina/`

## Passo 5 – Installa sull'iPad
1. Apri l'indirizzo con **Safari** (deve essere Safari).
2. Premi il tasto di condivisione (il quadrato con la freccia in su).
3. Scegli **Aggiungi alla schermata Home** e conferma.
4. Apri l'app dall'icona sulla Home. Dopo la prima apertura con internet **funziona anche senza connessione**.

## Come aggiornare l'app in futuro
1. Nel deposito apri il file da sostituire (per esempio `index.html`), premi la matita o i tre puntini e poi **Delete file**, oppure più semplice: **Add file → Upload files** e carica il nuovo file con lo **stesso nome**. GitHub lo sostituisce.
2. Se hai cambiato `index.html`, **carica anche il nuovo `sw.js`**: contiene il numero di versione che dice all'iPad di scaricare la novità.
3. Premi **Commit changes**, aspetta 1–2 minuti, poi chiudi del tutto l'app sull'iPad e riaprila.

## Se qualcosa non va
- **Pagina «404»**: aspetta ancora qualche minuto, oppure controlla che i file siano nella cartella principale e non dentro un'altra cartella.
- **L'app non si aggiorna**: carica il nuovo `sw.js`, chiudi l'app e riaprila. Se non basta, cancella l'icona dalla Home e aggiungila di nuovo da Safari.
- **Niente musica**: tocca una volta lo schermo; controlla che il pulsante della nota in basso a destra non sia barrato e che l'iPad non sia in modalità silenziosa.

## Attenzione: il deposito pubblico è visibile a tutti
Chiunque conosca l'indirizzo può aprire l'app. Nell'app non ci sono dati personali (le risposte restano solo sull'iPad). Il nome «Valentina» però è scritto nell'app. Se preferisci, usa un nome utente e un nome del deposito che non facciano pensare a lei.
Controlla anche i diritti delle immagini di cesto e frutti prima di pubblicare.
