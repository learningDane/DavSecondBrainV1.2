#uni 
La progettazione concettuale è la prima fase del terzo stadio del [[Metodologie e Modelli Progettuali#Waterfall Model]], in particolare quella che porta alla realizzazione dello schema concettuale ([[Modello Entity-Relationship]]). -> [[Progettazione Logica]] 
# La metodologia per la progettazione
1. analisi dei requisiti
   - analizzare i requisiti ed eliminare ambiguità
   - glossario dei termini
   - raggruppare requisiti
2. passo base
   - definire schema scheletro
3. passo iterativo
   - raffinare i concetti
   - aggiungere concetti per descrivere specifiche non descritte
4. analisi di qualità dello schema
   - correttezza
   - completezza
   - leggibilità
   - minimalità
# Design Pattern
Si utilizzano i ___design pattern___, che sono soluzioni progettuali a problemi comuni.
### Reificazione di attributo di entity
Questo pattern è quando si prende un attributo di una entity e lo si trasforma in un'altra entity, legata alla prima attraverso una relazione.
### Parte-Di o _pattern_ ISA
Quando una entity è parte di un'altra entity alla quale è collegata da una relationship "parte di" o simili.
### Istanza-Di
Quando una entity è un'istanza particolare di un'altra entity, alla quale è collegata tramite una relationship "occorrenza", "istanza-di" o simili.
#### Reificazione di relationship binaria/ternaria
Quando si prende una relationship binaria e la si trasforma in entity, collegandola alle due entity originariamente connesse attraverso 2 nuove relationship.
#### Reificazione di attributo di relationship
Quando si reifica una relationship binaria e la si collega tramite nuova relationship ad una nuova entity, che era originariamente un suo attributo.
#### Caso particolare di entity
Quando si prende un caso particolare di una entity e lo si reifica, rendendolo sottoinsieme (quindi unico figlio) con una [[Modello Entity-Relationship#Generalizzazione]] __parziale__.
#### Storicizzazione di concetto
Questa viene rappresentata come una generalizzazione totale cui le 2 figlie sono 2 entity, una che afferisce al presente ed una che afferisce al passato.
#### Evoluzione di concetto
# Strategie di Progetto
Esistono 3 strategie di progetto, anche se nella pratica si procede con una strategia mista:
1. si individuano i concetti principali e si realizza uno ___schema scheletro___:
   si organizza i concetti più importanti e li si organizza in un semplice schema concettuale
2. basandosi su questo si può decomporre
3. poi si raffina, espande ed integra
### Le 3 strategie di progetto canoniche
#### Top-Down
Si parte da uno schema iniziale che viene via via raffinato e integrato per mezzo di ___primitive___, che lo trasformano in una serie di schemi intermedi, fino ad arrivare allo schema E-R finale ([[Modello Entity-Relationship]]).
Le primitive di raffinamento sono le seguenti:
- da entity ad relationship tra entity
- da entity a generalizzazioni
- da relationship a insiemi di associazioni
- da relationship ad entity con relationship
- introduzione di attributi su entity e relationship
#### Bottom-Up
Si parte dalle specifiche iniziali e si suddividono fino a dare specifica ad una componente minima di cui si da lo schema E-R. Gli schemi prodotti vengono fusi e integrati fino ad ottenere lo schema E-R finale.
Le primitive di trasformazione:
- generazione di entity
- generazione di relationship
- generazione di generalizzazione
#### Inside-Out