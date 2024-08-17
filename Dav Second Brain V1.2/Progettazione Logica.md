#uni 
La progettazione logica è la seconda fase del terzo stadio del [[Metodologie e Modelli Progettuali#Waterfall Model]], in particolare quella che porta alla realizzazione dello schema logico.
L'obiettivo di questa fase è quello di tradurre lo schema concettuale prodotto durante la [[Progettazione Concettuale]] in uno schema logico che rappresenti gli stessi dati in maniera corretta ed efficiente.
I dati in ingresso sono: 
- schema concettuale
- informazioni sul carico applicativo
- modello logico
Mentre i dati in uscita sono:
- schema logico
- documentazione associata
Il primo passo è la ristrutturazione dello schema E-R ([[Modello Entity-Relationship]]), al fine di semplificare la traduzione in schema logico e ottimizzare le prestazioni. Nota bene, uno schema E-R ristrutturato non è più uno schema concettuale nel senso stretto del termine.
# Valutazione delle prestazioni
Per valutare le prestazioni consideriamo i seguenti indicatori:
- __spazio__: numero di occorrenze previste
- __tempo__: numero di occorrenze visitate per portare a termine un'operazione.
Per cominciare si prende l'operazione da eseguire e si costruisce una ___tavola degli accessi___, basata su uno ___schema di navigazione___.
# Attività di ristrutturazione
#### Analisi delle ridondanze
Una ridondanza è un'informazione significativa ma derivabile, durante questa fase si decide se eliminarle, mantenerle o introdurne di nuovi.
Una ridondanza semplifica le interrogazioni ma appesantisce gli aggiornamenti e occupa maggiore spazio.
Le  ridondanze possono essere _attributi derivabili_ oppure _relationship derivabili_.
#### Eliminazione delle generalizzazioni
Il [[Modello Logico Relazionale]] non può rappresentare direttamente le generalizzazioni, si eliminano quindi le gerarchie, sostituendole con entity e relationship.
Le possibilità sono:
- accorpamento delle figlie nel genitore
- accorpamento del genitore nelle figlie
- sostituzione della generalizzazione con relationship
#### Partizionamento/accorpamento di entity e relationship
#### Scelta degli identificatori primari