#uni 
Il __Sistema di Gestione di Basi di Dati__ (o [[Database]] management system, __DBMS__) gestisce collezioni di dati:
- _grandi_ $\to$ gestione sofisticata
- _persistenti_ $\to$ in memoria secondaria (lenta) $\to$ limitare accesso a memoria lenta
  tempo di vita indipendente dalle singole esecuzioni dei programmi che le utilizzano
- _condivise_ $\to$ meccanismi di autorizzazione e [[Gestione della Concorrenza]]  
e garantisce:
- _privacy_
- _affidabilità_
  i [[Database]] sono una risorsa pregiata e vanno protetti, la tecnica fondamentale inerente è la [[Gestione delle Transazioni]]. 
- _efficienza_
  utilizzare al meglio le risorse di spazio e di tempo
- _efficacia_
  migliorare la produttività dell'utilizzatore
Nei DBMS esiste una porzione della base di dati che contiene una descrizione centralizzata dei dati. Viene introdotto il concetto di [[Modello dei dati]].
Un DBMS può essere ___monoutente___ o ___multiutente___ a seconda del numero di utenti che possono usufruirne simultaneamente.
### Architettura a tre livelli di un DBMS
1. Utente
2. Schema Esterno
   descrizione di parte della base di dati in un modello logico
3. Schema logico
   descrizione della base di dati nel modello logico (eg. la struttura della tabella)
3. Schema interno (o Fisico)
   rappresentazione dello schema logico per mezzo di strutture memorizzazione (file)
4. Base di Dati
#### Indipendenza dei Dati
L'accesso ai dati avviene solo tramite livello esterno (che può coincidere con i livello logico).
__Indipendenza Fisica__: il livello logico ed esterno sono indipendenti da quello fisico
__Indipendenza logica__: il livello esterno è indipendente da quello logico
# Media
![[Pasted image 20240821131745.png]]
