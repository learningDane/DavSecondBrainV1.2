#uni 
Una Base di Dati è il cuore di un sistema informativo automatizzato, cioè un insieme organizzato di dati utilizzati per rappresentare le informazioni di interesse.
Un Database è l'insieme di dati gestito da un [[DBMS]].
I Database hanno:
- dimensioni molto maggiori della memoria centrale del sistema di calcolo utilizzato
- tempo di vita indipendente dalle singole esecuzioni dei programmi che lo utilizzano (__persistenza__ dei dati)
Una base di dati è una risorsa integrata, condivisa fra applicazioni e quindi necessita di meccanismi di autorizzazione e controllo della concorrenza e dell'incoerenza.
In ogni base di dati esistono:
- ___schema___: invariante nel tempo, descrive la struttura del DB
- ___istanza___: insieme dei valori attuali
Il linguaggio usato per interagire con i database è l'[[MySQL]].



Cosa è un Database? Questo è semplicemente un deposito per le informazioni. Queste però vengono depositate secondo alcuni criteri ovviamente. I database sono studiati per facilitare l'interazione con i dati. 
Un database è un insieme di dati gestito da un DBMS (database management system).
Il ___modello logico relazionale___:
	cerca su internet
Il linguaggio usato per i database è [[MySQL]]. 
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
I database devono cercare di utilizzare al meglio le risorse di spazio di memoria, principale e secondaria, e tempo, di esecuzione e di risposta. Minore efficienza di un Database  porta ad affrontare spese più grandi per maggiore spazio di archiviazione o a esperienze di utilizzo peggiori. Qui è quindi di grande importanza l'[[Ottimizzazione delle Interrogazioni]]. 
### Modello dei Dati
Il modello dei dati è l'insieme di costrutti utilizzati per organizzare i dati di interesse e descriverne la dinamica. Questo modello dei dati fornisce ai programmi applicativi una vista astratta dei dati.
### Schema ed Istanza
In ogni base di dati esistono:
- ___schema___: sostanzialmente invariante nel tempo, descrive la struttura della tabella 
- ___istanza___: i valori attuali, che possono cambiare anche molto rapidamente, inoltre ci possono essere più istanze diverse.
# Modelli dei Dati
- Modelli logici:
	- adottati nei DBMS esistenti per l'organizzazione dei dati
		- utilizzati dai programmi
		- indipendenti dalle strutture fisiche
	- Esempi: relazionale, reticolare, gerarchico, a oggetti, basato su XML
- Modelli Concettuali
	- permettono di rappresentare i dati in modo indipendente da ogni sistema
		- cercano di descrivere i concetti del mondo reale
		- sono utilizzati nelle fasi preliminari di progettazione
	- il più diffuso è il modello ___Entity-Relationship (ER)___ 
# Architettura di un DBMS
___utente -> schema logico -> schema interno -> Database___ 
1. schema logico
	- descrizione della base di dati nel modello logico
		- ad esempio la struttura della tabella
2. schema interno (o fisico)
	-  rappresentazione dello schema logico per mezzo di strutture memorizzazione
		- ad esempio record con puntatori, ordinati in un certo modo
3. il livello logico è indipendente da quello fisico:
	- una tabella è utilizzata nello stesso modo qualunque sia la sua realizzazione fisica (che può cambiare nel tempo)
# Linguaggi per Basi di Dati
Linguaggi: 
	- linguaggi testuali interattivi ([[MySQL]]) 
	- comandi in linguaggi testuali immersi in un linguaggio ospite ([[C++]], Java, ecc)
	- con interfacce amichevoli
distinzione terminologica:
	- ___data definition language___ (DDL) per la definizione di schemi (logici o fisici)
	- ___data manipulation language___ (DML) per l'interrogazione e l'aggiornamento di (istanze di) basi di dati. 
# Indipendenza dei Dati
- l'accesso ai dati avviene solo tramite il livello esterno (che può coincidere con il livello logico)
- Indipendenza fisica:
	- il livello logico e quello esterno
# Personaggi
- progettisti e realizzatori di DBMS
- progettisti della base di dati e amministratori della base di dati
- progettisti e programmatori di applicazioni
- utenti:
	- utenti finali: eseguono applicazioni predefinite
	- utenti casuali: eseguono operazioni non previste a priori
# Vantaggi e Svantaggi dei DBMS
Vantaggi:
	1. dati come risorsa comune e database come modello della realtà
	2. gestione centralizzata con possibilità di standardizzazione ed ___economia di scala___
	3. disponibilità di servizi integrati
	4. riduzione di ridondanze e inconsistenze
	5. indipendenza dei dati
		1. favorisce lo sviluppo e la manutenzione delle applicazioni
Svantaggi:
	1. costo dei prodotti e della transizione verso di essi
	2. non scorporabilità delle funzionalità (con riduzione di efficienza)
# Modello Logico
Tre modelli logici ___tradizionali___:
- gerarchico e reticolare
	- utilizzano riferimenti espliciti (puntatori) fra record
- relazionale [[Modello Logico Relazionale]] 
	- è basato su valori
	- anche i riferimenti fra dati in strutture (relazioni) diverse sono rappresentati per mezzo dei valori stessi.
modelli logici più recenti:
- a oggetti
- basato su XML
- NoSQL
# Operazioni di aggiornamento
- Operazioni di Inserimento
	- violazione dei vincoli intra-relazionali
	- violazione dell'integrità referenziale
- operazione di cancellazione
	- violazione dell'integrità referenziale
- operazione di modifica
	- modifica = cancellazione + inserimento