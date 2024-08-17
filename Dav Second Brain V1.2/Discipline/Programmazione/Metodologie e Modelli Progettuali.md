#uni 
Se per modellare un'applicazione cerchiamo di definire subito lo schema logico ci perdiamo nei dettagli e risulta molto difficile poiché il modello relazionale è rigido. 
Partiamo quindi con la progettazione del [[Database]], che è una delle attività del processo di sviluppo dei sistemi informativi, inquadriamola quindi in un contesto più generale:
Il ___ciclo di vita___ di un [[Sistema Informativo]]:
1. insieme e organizzazione temporale delle attività svolte dalle diverse figure durante sviluppo ed uso dei sistemi informativi.
2. attività iterativa.
# Waterfall Model
Questo è il primo modello da scegliere, e ne esistono di vari, il più vecchio è il __waterfall model__: in questo modello le fasi sono ordinate e _non ripetibili_:
1. ___Studio di fattibilità___
2. ___raccolta ed analisi dei requisiti___
   1. ___acquisizione dei requisiti___
      da interviste di utenti, normative, procedure aziendali e realizzazioni preesistenti, importante il ___ranking dei requisiti___.
      Regole generali per la documentazione che segue l'interazione con gli utenti:
      - standardizzare la struttura delle frasi
      - separare frasi su dati da frasi su funzioni
      - organizzare termini e concetti
        - costruire un glossario dei termini
          - individuare sinonimi
          - rendere esplicito il riferimento fra termini
	  - riorganizzare le frasi per concetti
   1. analisi dei requisiti
      coadiuvata da linguaggi specifici per definire i requisiti, ad esempio [[UML]] 
3. ___progettazione___
	   divisa in progettazione dei dati (e quindi scelta del [[Modello dei dati]] e delle applicazioni. Si Progetta per diversi livelli di astrazione: [[Progettazione Concettuale]], [[Progettazione Logica]] e fisica che lavorano rispettivamente su schema concettuale, logico e fisico.
1. ___realizzazione___
2. ___validazione e collaudo___
3. ___funzionamento o shipping___ 
# Altro
![[Pasted image 20240815235035.png]]
# Esempi documentazione
Si vuole realizzare una base di dati per una società che
eroga corsi: di ogni corso vogliamo rappresentare i dati
dei partecipanti e dei docenti. Per gli studenti (circa
5000), identificati da un codice, si vuole memorizzare il
codice scale, il cognome, l'età, il sesso, il luogo di
nascita, il nome dei loro attuali datori di lavoro, i posti
dove hanno lavorato in precedenza insieme al periodo,
l'indirizzo e il numero di telefono, i corsi che hanno già
frequentato (le materie sono in tutto circa 200) e il
giudizio finale.
Rappresentiamo anche i corsi attualmente attivi e, per
ogni giorno, i luoghi e le ore dove sono tenute le
lezioni. I corsi hanno un codice, un titolo e possono
avere varie edizioni con date di inizio e ne e numero
di partecipanti. Se gli studenti sono liberi professionisti,
vogliamo conoscere l'area di interesse e, se lo
possiedono, il titolo. Per quelli che lavorano alle
dipendenze di altri, vogliamo conoscere invece il loro
livello e la posizione ricoperta.
Per gli insegnanti (circa 300), rappresentiamo il
cognome, l'età, il posto dove sono nati, il nome del
corso che insegnano, quelli che hanno insegnato nel
passato e quelli che possono insegnare. Rappresentiamo
anche tutti i loro recapiti telefonici. I docenti possono
essere dipendenti interni della società o collaboratori
esterni.

| termine          | descrizione                                              | sinonimi   | collegamenti   |
| ---------------- | -------------------------------------------------------- | ---------- | -------------- |
| partecipante     | persona che partecipa ai corsi                           | studente   | corso, società |
| docente          | docente dei corsi, può essere esterno                    | insegnante | corso          |
| corso            | corso organizzato dalla società. Può avere più edizioni  | materia    | docente        |
| datore di lavoro | ente presso cui i partecipanti lavorano o hanno lavorato | posto      | partecipante   |
### Strutturazione dei requisiti in gruppi di fasi omogenee
_Frasi di carattere generale_:
Si vuole realizzare una base di dati per una società che eroga corsi: di ogni corso vogliamo rappresentare i dati dei partecipanti e dei docenti
_Frasi relative ai datori di lavoro_:
Relativamente ai datori di lavoro presenti e passati dei
partecipanti, rappresentiamo il nome, l'indirizzo e il
numero di telefono.
_ecc_...