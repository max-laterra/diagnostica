# La Terra – Diagnostica

**Versione 1.0** — 10 novembre 2026

Il numero di versione è scritto in fondo alla pagina: «La Terra · Diagnostica · versione 1.0».

Serve a controllare, da telefono o da computer, che funzioni tutto:
app degli autisti, cartella Dropbox «Autisti La Terra», servizio notifiche su
Cloudflare e archivio dell'app Presenze (Supabase). Può anche fare qualche
riparazione, sempre chiedendo conferma. L'Agenda non viene controllata.

---

## Regola per le impostazioni

Come nell'app degli autisti, **tutte le impostazioni stanno nella pagina
nascosta**: si apre toccando **6 volte di fila la scritta «Diagnostica»** in
alto (entro 4 secondi). Anche ogni impostazione nuova va messa lì.

---

## I file di questo pacchetto

Vanno caricati tutti nella radice del repository **diagnostica** su GitHub.

| File | A cosa serve |
|---|---|
| `index.html` | **È l'app.** |
| `manifest.webmanifest` | Nome e icona sulla schermata Home. |
| `icons/` | Le icone. |
| `README.md` | Questo file. |

Indirizzo dell'app: `https://max-laterra.github.io/diagnostica/`

---

## Cosa controlla

In alto un **semaforo** (verde, giallo, rosso) e l'elenco dei problemi trovati,
ognuno con **«Cosa fare»**. Sotto, le sezioni (si aprono toccandole):

1. **Servizio notifiche**: ultimo giro, versione, errori, lucchetto, notifiche
   in attesa, campanelli di Dropbox e Presenze, ultime operazioni.
2. **Collegamento Presenze**: ultimo passaggio, problemi (per esempio 520),
   autisti dell'Agenda che non trovano il loro nome nelle Presenze, conferme dei
   riposi copiate.
3. **Autisti e telefoni**: per ogni autista telefono, ultima apertura, versione
   dell'app, notifiche (attive, avviso del giorno prima, esito dell'ultima
   notifica).
4. **Fogli di oggi e dei prossimi 7 giorni**: PDF presente, chi li ha aperti e
   quando, ritirati, più autisti sullo stesso pullman.
5. **Buste spese** dell'ultimo mese: da consegnare, consegnate, foto degli
   scontrini non arrivate.
6. **Riposi e rimesse di domani**: arrivati ai telefoni e chi ha premuto OK;
   con l'archivio collegato, anche i riposi segnati in Presenze ma non arrivati.
7. **Crocette dei pasti di oggi**: chi le ha messe e se sono arrivate nelle
   Presenze.
8. **Archivio Presenze (Supabase)**: raggiungibile, tabelle, conferme.
9. **Versioni**: app autisti e Presenze pubblicate su GitHub, servizio
   notifiche, versioni dell'app sui telefoni degli autisti.

Il controllo si rifà da solo ogni 2 minuti con l'app aperta, e con il tasto
**«Controlla»**.

## Riparazioni (sempre con conferma)

- **Togli il lucchetto** (se il servizio è rimasto bloccato da più di 2 minuti).
- **Fai rileggere tutta la cartella** al servizio (fogli, telefoni, crocette,
  conferme): non manda notifiche doppie.
- **Svuota le notifiche in attesa**.
- **Rimanda i riposi a tutti i telefoni**.
- **Ricopia le conferme nelle Presenze**.
- **Notifica di prova** a un autista («Prova riuscita» sul suo telefono).

Le riparazioni che toccano lo stato del servizio prendono il suo lucchetto,
come fa il servizio a ogni giro: se il servizio sta lavorando, aspettano e, se
serve, rinunciano («riprova tra un minuto»). Ogni riparazione resta scritta
nelle «Ultime operazioni» del servizio come «Diagnostica: …».

---

## Come si installa

### 1. Il repository su GitHub
1. Apri github.com e accedi.
2. In alto a destra tocca **+** › **New repository**.
3. In **Repository name** scrivi `diagnostica`.
4. Lascia **Public** e tocca **Create repository**.
5. Tocca **uploading an existing file**.
6. Trascina tutto il contenuto della cartella scompattata (index.html,
   manifest.webmanifest, README.md e la cartella icons).
7. Tocca **Commit changes**.
8. Tocca **Settings** › **Pages**.
9. In **Branch** scegli **main** e **/(root)**, poi **Save**.
10. Dopo qualche minuto l'app è a `https://max-laterra.github.io/diagnostica/`.

### 2. Il «telefono» Diagnostica nell'Agenda
1. Nell'Agenda: Pannello Super Master › Autisti › **Collega un telefono**.
2. Come nome scrivi **Diagnostica**.
3. Tocca **Copia il link**.

### 3. Primo avvio
1. Apri `https://max-laterra.github.io/diagnostica/`.
2. Incolla il link e tocca **Collega**.
3. Scegli una password (almeno 8 caratteri).
4. Per l'archivio Presenze: tocca 6 volte la scritta **Diagnostica** ›
   **Archivio Presenze**: indirizzo, chiave pubblica, email e password sono gli
   stessi dell'app Presenze (scheda Dipendenti › «Telefono e computer
   insieme»). La password dell'archivio non viene salvata.
5. Tocca **‹ Diagnostica**.

Su ogni dispositivo (telefono e computer) il primo avvio si fa una volta.

## Sicurezza
- La password si chiede a ogni apertura; dopo **15 minuti in sottofondo** si
  richiede. «Resta collegato su questo dispositivo» la toglie: usalo solo su un
  dispositivo personale con il blocco schermo.
- Il link dell'Agenda apre la cartella Dropbox degli autisti: se un dispositivo
  con la diagnostica si perde, **blocca il telefono «Diagnostica» nell'Agenda**
  e creane uno nuovo.
- In cima a `index.html` c'è l'elenco dei siti con cui l'app può parlare
  (Content-Security-Policy). Se cambia l'indirizzo delle app su GitHub o si
  aggiunge un servizio, va aggiunto lì.

## Collegata a
- App autisti 1.13 o successiva (le versioni precedenti si vedono come
  «1.12 o precedente»).
- Servizio notifiche **1.10** (con la 1.9 mancano versione del servizio ed
  esito dell'ultima notifica per telefono).
- App Presenze 1.11.

## Prove fatte prima della consegna (1.0)
Con Dropbox, archivio Supabase, GitHub e servizio notifiche 1.10 simulati,
44 controlli tutti superati: collegamento e password; problemi trovati (foglio
di domani non aperto, foglio senza PDF, autista con servizi ma senza telefono,
app non aperta da 5 giorni, app vecchia, notifiche scadute, busta da
consegnare, foto non arrivata, servizio bloccato dal lucchetto, autista non
abbinato, riposo non arrivato al telefono, crocette non copiate); versioni ed
esiti delle notifiche; impostazioni nascoste e archivio; riparazioni (lucchetto,
rileggi, rimanda i riposi, notifica di prova) e verifica che dopo il giro del
servizio i problemi spariscono; riparazione che rinuncia se il servizio sta
lavorando; blocco automatico dopo 15 minuti; telefono e computer.
