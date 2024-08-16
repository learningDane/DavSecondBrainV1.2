#uni 
Anche detto modello __E-R__, è il [[Modello dei dati]] concettuale più diffuso.
Prevede i seguenti costrutti:
- Costrutti di Base:
  1. ___Entità___
  2. ___Relationship___
  3. ___Attributo___
- Altri costrutti:
  1. Identificatore
  2. generalizzazione
  3. ...
# Entity
Una entità è una classe di oggetti (fatte, persone, cose) con proprietà comuni ed esistenza _autonoma_.
Non cambia da una istanza all'altra: un "impiegato" rimane sempre un "impiegato" senza altre proprietà note oltre a quelle che lo definiscono "impiegato".
Ogni entità ha un nome che la identifica univocamente nello schema, il nome deve essere espressivo e si deve fare riferimento a opportune convenzioni, eg. usare sempre il singolare.
# Relationship
Questa è un legame logico fra due o più entity, può venire chiamata relazione, correlazione oppure associazione.
Ogni relationship ha un nome, espressivo, singolare e possibilmente deve essere un sostantivo, non un verbo.
Alcuni esempi: Residenza (fra persona e città), esame (fra studente e corso).
Una occorrenza di relationship _binaria_ è una coppia di occorrenze di entità, un per ognuna delle due entità coinvolte. Una occorrenza di relationship _n-aria_ è una tupla di occorrenze di entità, una per ogni $n$ entità coinvolte.
Nell'ambito di una relationship non ci possono essere occorrenze ripetute.
# Attributo
Un attributo è una proprietà elementare di entity o relationship. Associa ad ogni occorrenza di entity o relationship un valore, appartenente al dominio dell'attributo.
Un attributo __composto__ raggruppa attributi che presentano affinità di una medesima entity o  relationship, ad esempio _via, numero, civico_ e _cap_ formano _indirizzo_.
# Altri Costrutti
### Cardinalità
Può essere di _relationship_ o di attributo.
Questa è una coppia di coppie di valori associata ad ogni entità coinvolta in una _relationship_.
Specifica il numero minimo e massimo di occorrenze della _relationship_ cui ciascuna occorrenza di entità può partecipare.
Per semplicità utilizziamo solo 3 simboli:
- $0$ e $1$ per la cardinalità minima:
  1. $0=$ partecipazione opzionale
  2. $1=$ partecipazione obbligatoria
- $1$ e $N$ per la cardinalità massima ($N$ non pone alcun limite)
Possiamo con la cardinalità distinguere 3 tipi di _relationship_:
- ___uno a uno___: $(k,N) - (k,N$ )
- ___uno a molti___: $(k,k) - (N,N)$ 
- ___molti a molti___: $(k,k) - (k,k)$ 
_eg:_ $Impiegato \ (1,1) \ Residenza \ (0,N) \ Città$ 
### Identificatore di _entity_ 
Questo è uno strumento per identificare univocamente delle occorrenze di una _entity_. Ogni entity deve possedere almeno un identificatore ma può averne di più.
Un identificatore può essere costituito da:
- attributi dell'entity
  1. cui fa parte se presente l'___identificatore interno___ (la __chiave__)
- attributi + chiave di entità esterne, raggiunta attraverso _relationship_
  1. cui fa parte se presente l'___identificatore esterno___ (possibile solo attraverso una relationship $(1,1)$. 
### Generalizzazione
Mette in relazione una o più entity $E_1,E_2,...$ con una entity $E$ che le comprende come casi particolari, si dice che $E$ è una ___generalizzazione___ (o genitore) di $E_1,E_2,...$, che invece si dicono ___specializzazioni___ (o sottotipi o figlie) di $E$.
Ogni proprietà di $E$ è significativa per le figlie ma non rappresentata esplicitamente e ogni occorrenza delle figlie è occorrenza anche di $E$.
Si dice Generalizzazione __Totale__ se ogni occorrenza del Genitore è occorrenza di almeno una delle figlie, altrimenti di dice __Parziale__.
Si dice __Esclusiva__ se ogni occorrenza del genitore è occorrenza di al più una figlia, altrimenti di dice __Sovrapposta__.
Se una generalizzazione ha solo un'entità figlia si parla di __Sottoinsieme__.
Il genitore di una generalizzazione totale può non avere identificatore, purché …
# Media
![[Pasted image 20240816121719.png]]
![[Pasted image 20240816094228.png]]
![[Pasted image 20240816123548.png]]
![[Pasted image 20240816095713.png]]
Relationship ricorsiva con ruoli: 
![[Pasted image 20240816095415.png]]
![[Pasted image 20240816095905.png]]
