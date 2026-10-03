# LabelOne & BuilderOne

**LabelOne** è una suite software professionale per la progettazione grafica, la gestione di dati variabili, la generazione di codici a barre industriali e la stampa automatizzata di etichette su piattaforme Windows, Linux, macOS e sistemi embedded.

---

## 📋 Indice
- [Caratteristiche Principali](#-caratteristiche-principali)
- [Strumenti di Disegno e Gestione Testo](#-strumenti-di-disegno-e-gestione-testo)
- [Dati Variabili e Integrazione Database](#-dati-variabili-e-integrazione-database)
- [Codici a Barre e Assistente EAN/UCC 128](#-codici-a-barre-e-assistente-eanucc-128)
- [Parametri di Avvio e Opzioni di Esecuzione](#-parametri-di-avvio-e-opzioni-di-esecuzione)
- [Standard Application Identifiers (GS1 / AI)](#-standard-application-identifiers-gs1--ai)

---

## 🎨 Caratteristiche Principali

- **Editor Grafico Intuitivo**: Creazione immediata di etichette con elementi fissi, dinamici, forme e disegni a mano libera.
- **Motore di Stampa Avanzato**: Gestione flessibile di layout complessi, formati personalizzati (es. 90x90) e integrazione con stampanti industriali.
- **Architettura Client/Server**: Supporto nativo per la condivisione e l'esecuzione di progetti su rete.
- **Modalità Utente e Touch Screen**: Interfaccia adattabile per operatori di linea e schermi touch screen.

---

## ✒️ Strumenti di Disegno e Gestione Testo

### Disegno a Mano Libera (`DrawPencil`)
- **Tracciamento facile**: Attivazione tramite due clic consecutivi per definire punto iniziale e finale (senza necessità di trascinamento continuo).
- **Personalizzazione**: Applicazione di colori di riempimento e rifinitura delle forme.

### Modulo Testo (`DrawText`)
- **Modalità Editing**: Clic singolo per inserire il testo, doppio clic su elementi esistenti per la modifica, tasto `Esc` o clic esterno per uscire dall'editing.
- **Formattazione Paragrafo**:
  - *A capo manuale*: Mantiene le interruzioni inserite con `Invio`.
  - *A capo automatico*: Adatta il testo al rettangolo di selezione adattando la larghezza.
  - *Regolazioni*: Spaziatura tra caratteri, interlinea ed espansione orizzontale.
- **Effetti Grafici e Avanzati**:
  - Testo curvo (lungo linee curve con punti di controllo) e testo circolare (lungo l'arco o il perimetro di un'ellisse).
  - Stili 3D, ombreggiature e solo contorno (con spessore e tratteggio regolabili).
  - Supporto completo agli stili e formattazioni anche su **testi a dati variabili**.

---

## 🗄️ Dati Variabili e Integrazione Database

- **Campi Fissi**: Posizionamento preciso tramite mouse o inserimento diretto di coordinate ($X$, $Y$) nell'Ispettore Geometrie, con funzioni di allineamento automatico e distribuzione uniforme.
- **Collegamento Database**:
  - Connessione a file di dati (es. Microsoft Access `.mdb`) specificando percorso, tabella e campo.
  - Sincronizzazione intelligente: selezione guidata via finestra per il primo campo e impostazione **Ultimo record selezionato** per i campi successivi per mantenere la sincronia dei dati.
- **Prompt Operatore**: Richiesta di inserimento manuale dati a ogni stampa (es. inserimento numero di lotto tramite finestra pop-up).

---

## 🏷️️ Codici a Barre e Assistente EAN/UCC 128

- **Tipologie Supportate**: EAN13, Code 128 e molti altri formati industriali.
- **Variabili Locali**: Concatenazione di più sorgenti dati tramite la sintassi `var(id)` (es. `var(1)var(2)var(4)`).
- **Assistente 128 Wizard (Studio / StudioPro)**:
  - Procedura guidata per la creazione di codici **EAN/UCC 128** complessi.
  - Gestione automatica della formattazione degli **Application Identifier (AI)**.
  - Calcolo e inserimento automatico del **check-digit** (es. GTIN a 14 cifre) e riempimento con zeri.
  - Riapertura e modifica rapida tramite doppio clic sull'elemento barcode.

---

## ⚙️ Parametri di Avvio e Opzioni di Esecuzione

È possibile avviare **LabelOne** da riga di comando o all'interno di script utilizzando i seguenti parametri:

| Parametro | Descrizione / Funzione |
| :--- | :--- |
| `dir.prj sub.spj` | Esegue il sub-project `sub.spj` all'interno della cartella di progetto `dir.prj`. |
| `-USR` / `-usr` | Avvia la modalità *User* (interfaccia semplificata, salvataggio disabilitato). Con `-usr` è bloccata anche la modifica o lo spostamento degli elementi. |
| `-USR(int)` / `-usr(int)`| Attiva la modalità Touch regolando la dimensione degli elementi dell'interfaccia tramite il valore `int`. |
| `-MOD` | Esegue l'applicazione in finestra modale (non a schermo intero). |
| `-RSZ` / `-RSZ(x,y,w,h)`| Abilita il ridimensionamento della finestra modale o definisce posizione ($x,y$) e dimensioni ($w,h$). |
| `-INSP` | Sostituisce l'Ispettore delle Proprietà con un file browser. |
| `-HID` | Nasconde la finestra di benvenuto e i messaggi di sistema. |
| `-ERR` / `-ERW` | Salva i log ed eventuali errori nel file `error.log` (`-ERR`) o li mostra in una finestra (`-ERW`). |
| `-VRB` / `-DBG(L)` | Attiva la modalità Verbose/Debug specificando il livello con `L`. |
| `-SER` | Esegue l'applicazione come Server/Host Database. |
| `-CLI:IP` | Connette l'applicazione come Client all'indirizzo IP del Server. |
| `-PDE` | Esegue direttamente l'ambiente **BuilderOne**. |
| `-UNI` | Forza la lettura e scrittura dei file in modalità Unicode. |

---

## 📑 Standard Application Identifiers (GS1 / AI)

LabelOne supporta nativamente la codifica degli **Application Identifier** per la gestione della catena di fornitura. Di seguito i principali codici gestiti:

- **Identificazione**:
  - `00`: Serial Shipping Container Code (SSCC)
  - `01`: Global Trade Item Number (GTIN)
  - `10`: Numero di Lotto / Batch
  - `21`: Numero di Serie
- **Date e Tracciabilità**:
  - `11`: Data di Produzione (`AAMMGG`)
  - `13`: Data di Confezionamento (`AAMMGG`)
  - `15` / `17`: Data di Scadenza / Minima Validità
- **Misure e Pesi**:
  - Serie `310n` - `369n`: Pesi netti/lordi (kg, lb), dimensioni (metri, pollici), superfici ($m^2$) e volumi.
- **Logistica e Localizzazione**:
  - `400`: Numero d'Ordine d'Acquisto
  - `410` - `415`: Global Location Number (GLN) per spedizione, fatturazione e punto fisico
  - `420` / `421`: Codici Postali di destinazione

---

### 📝 Note di Licenza e Requisiti
*Le funzionalità avanzate come la concatenazione di stringhe superiori a 15 caratteri nei codici a barre e il Wizard EAN/UCC 128 richiedono le edizioni **Studio** o **StudioPro**.*
