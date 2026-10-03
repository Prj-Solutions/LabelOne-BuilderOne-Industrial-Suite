# LabelOne & BuilderOne Suite

LabelOne e BuilderOne costituiscono una suite integrata per la progettazione grafica di etichette, la creazione di interfacce utente gestionali (GUI) e l'automazione dei processi di stampa industriale.

## Indice

- [Panoramica della Suite](#panoramica-della-suite)
- [Componenti ed Elementi di Input](#componenti-ed-elementi-di-input)
  - [Input da CheckBox](#input-da-checkbox)
  - [Input da ComboBox](#input-da-combobox)
- [Macro Funzionali](#macro-funzionali)
  - [Keyboard Enabler](#keyboard-enabler)
  - [Gestore Backup](#gestore-backup)
  - [Gestore LogIn](#gestore-login)
- [Gestione Progetti e Documentazione](#gestione-progetti-e-documentazione)
  - [Documentazione di Progetto](#documentazione-di-progetto)
  - [Ridenominazione ed Eliminazione Frame](#ridenominazione-ed-eliminazione-frame)
  - [Controllo Versione e Storico File](#controllo-versione-e-storico-file)
- [Deploy e Creazione Installer](#deploy-e-creazione-installer)

---

## Panoramica della Suite

La suite si suddivide in due componenti principali:
* **BuilderOne**: Ambiente di sviluppo visuale per comporre frame, gestire flussi utente, configurare opzioni di stampa e definire macro.
* **LabelOne**: Engine di runtime e motore di stampa che esegue i progetti generati (`.prj`), gestendo l'interazione con stampanti industriali e dispositivi di campo.

---

## Componenti ed Elementi di Input

### Input da CheckBox
Il componente **CheckBox** consente la gestione di opzioni binarie o a selezione singola/multipla[cite: 31]:
* **Persistenza su File**: Lo stato (*selezionato/non selezionato*) viene salvato su un file di testo specificato dall'utente[cite: 31]. I valori standard predefiniti sono `TRUE` e `FALSE`, personalizzabili con stringhe o valori numerici a scelta[cite: 31].
* **Selezioni Indipendenti**: Associando file distinti a ciascun CheckBox (es. `Taschino.txt`, `polsino.txt`), le opzioni operano autonomamente[cite: 31].
* **Comportamento RadioButton (Selezioni Dipendenti)**: Associando più CheckBox al medesimo file di destinazione, la selezione di un'opzione deseleziona automaticamente le altre, scrivendo il valore specifico del CheckBox attivo nel file comune[cite: 31].

### Input da ComboBox
Il componente **ComboBox** (menu a tendina) consente la selezione di opzioni da una lista predefinita[cite: 32]:
* **Sorgente Dati**: La lista degli elementi visualizzabili nel menu viene prelevata da un file di testo esterno (es. `comboboxList.txt`), in cui le singole opzioni sono separate da `;`[cite: 32].
* **Registro Selezione**: L'opzione selezionata dall'operatore viene scritta nel file di memoria impostato per essere elaborata successivamente dal sistema[cite: 32].

---

## Macro Funzionali

### Keyboard Enabler
Attiva una tastiera virtuale numerica o alfanumerica sullo schermo all'immissione dati. La tastiera si apre automaticamente cliccando sui campi di testo ed è configurabile per dimensione, font e lingua.

### Gestore Backup
Effettua il salvataggio automatico dei dati contenuti nella cartella `Data` ad ogni chiusura del programma:
* I file vengono salvati in cartelle denominate `Data_Backup_N` dove *N* è il giorno della settimana (da 1 a 7).
* I backup ruotano con frequenza settimanale sovrascrivendo la cartella del rispettivo giorno.
* Consente il backup su percorsi locali, chiavette USB o server di rete, oltre al salvataggio manuale istantaneo tramite pulsante dedicato.

### Gestore LogIn
Permette la gestione degli account operatore e la protezione di frame o pulsanti riservati. Salva l'identificativo dell'utente attivo nel file `UserName.txt` ad ogni azione protetta per tracciabilità e analisi statistiche.

---

## Gestione Progetti e Documentazione

### Documentazione di Progetto
BuilderOne include strumenti dedicati alla documentazione tecnica dei progetti:
* **Commenti per Componente**: Consente di documentare lo scopo di ogni singolo elemento inserito.
* **Mappatura Flussi**: Genera un grafico delle connessioni tra i diversi frame navigabile con un click.
* **Esportazione**: Genera report riepilogativi stampabili con le specifiche complete del progetto.

### Ridenominazione ed Eliminazione Frame
* **Ridenominazione globale**: Rinomina un frame (es. `Frame2.spj`) e aggiorna automaticamente tutti i riferimenti e i collegamenti presenti all'interno dell'intero progetto[cite: 31].
* **Rimozione sicura**: Verifica le dipendenze prima dell'eliminazione definita dal pulsante *Elimina*[cite: 31].

### Controllo Versione e Storico File
* **Backup circolare**: I salvataggi di sviluppo vengono memorizzati nella cartella `Backup` con formato `NomeDocumento.ext~C~` (con contatore *C* da 0 a 99)[cite: 32]. Superata la quota 99, il contatore riparte sovrascrivendo i backup meno recenti[cite: 32].
* **Pannello History**: Interfaccia di ripristino per recuperare versioni precedenti di un frame (salvate con il prefisso `Re_`)[cite: 32].

---

## Deploy e Creazione Installer

LabelOne e BuilderOne sono progettati per essere applicativi portabili. Non richiedono installazioni invasive a livello di sistema operativo: l'intera applicazione risiede in una singola cartella contenente librerie, risorse e DLL.

### Comando di Esecuzione Standard
```bash
# Esecuzione Runtime LabelOne
javaw.exe -jar percorso\L1.jar

# Esecuzione Ambiente BuilderOne
javaw.exe -jar percorso\L1.jar -PED

# Esecuzione Progetto Specifico
javaw.exe -jar percorso\L1.jar NomeProgetto.prj Frame_Main.spj
