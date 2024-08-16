#uni 
Il __Sistema di Gestione di Basi di Dati__ (o [[Database]] management system, __DBMS__) gestisce collezioni di dati:
- grandi
- persistenti
  tempo di vita indipendente dalle singole esecuzioni dei programmi che le utilizzano
- condivise
e garantisce:
- privacy
- affidabilità
  i [[Database]] sono una risorsa pregiata e vanno protetti, la tecnica fondamentale inerente è la gestione delle __transazioni__. 
- efficienza
  utilizzare al meglio le risorse di spazio e di tempo
- efficacia
  migliorare la produttività dellìutilizzatore
Una __transazione__ è un insieme di operazioni da considerare indivisibile ("___Atomico___"), corretto anche in presenza di concorrenza e con effetti definitivi. La conclusione positiva di una transazione corrisponde ad un impegno a mantenere traccia del risultato in modo definitivo.
Nei DBMS esiste una porzione della base di dati che contiene una descrizione centralizzata dei dati. Viene introdotto il concetto di [[Modello dei dati]].
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