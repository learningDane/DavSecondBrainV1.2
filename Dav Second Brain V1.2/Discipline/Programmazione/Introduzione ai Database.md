#uni 
Cosa è un Database? Questo è semplicemente un deposito per le informazioni. Queste però vengono depositate secondo alcuni criteri ovviamente. I database sono studiati per facilitare l'interazione con i dati. 
Un database è un insieme di dati gestito da un DBMS (database management system).
Il ___modello logico relazionale___:
	cerca su internet
Il linguaggio usato per i database è [[SQL]]. 
Concetti chiave: 
	guarda le slide
Un Database ha dimensioni molto maggiore della memoria centrale del sistema di calcolo utilizzato e ha un tempo di vita indipendente dalle singole esecuzioni dei programmi che le utilizzano (___persistenza___ dei dati).
Un ___DBMS___ gestisce collezioni di dati:
- grandi
- persistenti
- condivise
garantendo:
- privacy
- affidabilità
- efficienza
- efficacia
### Problemi
I possibili problemi possono essere:
- ripetizione di informazioni
- rischio di incoerenza
- cattiva gestione dello spazio di archiviazione
### Privacy di un Database
Un database è una risorsa integrata, condivisa fra applicazioni. Servono meccanismi di autorizzazione e controllo della concorrenza.
### Affidabilità di un database
Un Database deve essere resistente a malfunzionamenti hardware e software. Un Database è una risorsa pregiata e quindi deve essere conservata a lungo termine.
Serve una gestione delle transazioni: una transazione è un insieme di operazioni da considerare indivisibile (___atomico___), corretto anche in presenza di concorrenza e con effetti definitivi. 
Le transazioni sono atomiche e devono funzionare correttamente anche in presenza di concorrenza.
I risultati di una transazione conclusa positivamente devono essere permanenti e corrisponde ad un impegno (___commit___) a mantenere traccia del risultato in modo definitivo, anche in presenza di guasti e di esecuzione concorrente.
### Efficienza di un Database
I database devono cercare di utilizzare al meglio le risorse di spazio di memoria, principale e secondaria, e tempo, di esecuzione e di risposta. Minore efficienza di un Database  porta ad affrontare spese più grandi per maggiore spazio di archiviazione o a esperienze di utilizzo peggiori.
### Modello dei Dati
Il modello dei dati è l'insieme di costrutti utilizzati per organizzare i dati di interesse e descriverne la dinamica. Questo modello dei dati fornisce ai programmi applicativi una vista astratta dei dati.
### Schema ed Istanza
In ogni base di dati esistono:
- ___schema___: sostanzialmente invariante nel tempo, descrive la struttura della tabella 
- ___istanza___: i valori attuali, che possono cambiare anche molto rapidamente, inoltre ci possono essere più istanze diverse.