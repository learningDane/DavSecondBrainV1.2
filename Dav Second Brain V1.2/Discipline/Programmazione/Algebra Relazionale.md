#uni 
Con l'algebra relazionale si definisce il modo in cui il [[DBMS]] esegue una interrogazione.
Una ___interrogazione___ è una operazione di lettura sulla base di dati. Le interrogazioni sono espresse ad alto livello e non vi è concetto di ___costo___.
Una Interrogazione può essere espressa in modo __dichiarativo__, specificando le proprietà del risultato, oppure in modo __procedurale__, specificando le modalità di generazione del risultato.
Si definisce il _comportamento_ delle interrogazioni in modo procedurale utilizzando le espressioni dell'algebra relazione.
Si definisce il _risultato_ di una interrogazione in modo dichiarativo utilizzando le espressioni del __calcolo relazionale__, che è l'effettiva semantica del linguaggio.
L'Algebra è data da dati e operatori, nell'algebra relazione i dati sono relazioni e gli operatori che sono su relazioni, producono relazioni e possono essere composti.
# Operatori dell'Algebra Relazionale
Operatori su insiemi:
	Le relazioni sono insiemi, i risultati devono essere relazioni e si possono applicare solo a relazioni definite sugli stessi attributi.
- __unione__
  tra due relazioni, restituisce una relazione che contiene tutte le tuple di entrambe le relazioni.
- __intersezione__
  tra due relazioni, restituisce una relazione che contiene le tuple presenti in entrambe le relazioni.
- __differenza__
  tra due relazioni, restituisce una relazione che contiene le tuple della prima relazione NON presenti nella seconda.
Operatori su relazioni:
- __ridenominazione__
  monadico, modifica lo schema dell'operando senza alterare l'istanza: cambia il nome di un attributo. $\rho_{B_1B_2...\leftarrow A_1A_2...}(R)$ che si legge _attributo A_1 viene sostituito da B_1_ ecc
- __selezione__
  monadico, restituisce una relazione che contiene solo le tuple della relazione operanda che soddisfano una condizione fissata. $\sigma _F (R)$ dove $F$ è una espressione Booleana ottenuta componendo con gli __operatori logici__ (AND, OR, NOT) delle __condizioni atomiche__ ($A \star B$, dove $A$ e $B$ sono attributi di $X$ con domini compatibili e $\star$ è un operatore di confronto. Oppure $A \star k$ dove $k$ è una costante con dominio compatibile con $A$). La presenza di un valore NULL rende immediatamente falsa la condizione atomica, per riferirsi appositamente a valori NULL bisogna usare `IS NULL` oppure `IS NOT NULL`.
- __proiezione__
  monadico, restituisce una relazione che ha un sottoinsieme degli attributi dell'operando e tutte le tuple cui contribuiscono tutti i valori esistenti dell'operando. $\pi _Y (R)$ con $Y \in X$ . Se $Y$ è una superchiave di $R$ allora la proiezione contiene esattamente tante tuple quante ne ha $R$, altrimenti di meno.
- __join__
	- __naturale, interno__
	  tra due relazioni, restituisce una relazione le cui tuple sono unioni delle tuple dei due operandi. $R_1\bowtie R_2$ . Il risultato contiene un numero di tuple compreso fra $0$ ed il prodotto di $R_1$ ed $R_2$. Se il join coinvolge una chiave di $R_2$ allora il numero di tuple è compreso fra $0$ e $R_1$, se coinvolge anche un vincolo di integrità referenziale allora il numero di tuple è uguale a $|R_1|$ .
	  Le tuple che non si legano ad altre tuple vengono tagliate fuori.
	  Il __join esterno__ estende, con valori NULL, le tuple che verrebbero tagliate fuori dal join interno. Ne esistono 3 versioni: sinistro, destro e completo.
	- __prodotto cartesiano__
	  date due relazioni $R_1(X_1)$ e $R_2(X_2)$ senza attributi comuni vale la definizione di join naturale: restituisce un numero di tuple pari al prodotto della cardinalità degli operandi poiché per ogni tupla di $1$ ne restituisce i join con ogni tupla di $2$. $R_1 \times R_2$ .
	- __theta__
	  è un operatore derivato, composto da prodotto cartesiano e selezione. $R_1 \bowtie _F R_2$ , se l'operatore di confronto è l'uguaglianza allora si parla di __equi-join__.
# Ottimizzazione delle Interrogazioni
Il ___query processor___ (o ottimizzatore) è un modulo del [[DBMS]] che si occupa di ottimizzare le query che invece sono espresse ad alto livello.
Questa è l'__esecuzione delle Interrogazioni__:
	[[SQL]]: Analisi lessicale, sintattica e semantica -> Algebra: ottimizzazione algebrica -> algebra: ottimizzazione basata sui costi
### Profili delle Relazioni
Contengono informazioni quantitative:
- cardinalità delle relazioni
- dimensioni delle tuple
- dimensione dei valori
- numero di valori distinti degli attributi
- valore minimo e massimo degli attributi
Queste informazioni sono memorizzate nel ___catalogo___ e aggiornate e vengono utilizzate nella fase finale dell'ottimizzazione per stimare le dimensioni dei risultati intermedi.
### Ottimizzazione Algebrica
Il termine ottimizzazione è improprio perché il processo utilizza euristiche. Questo processo si basa sulla nozione di equivalenza.
L'euristica fondamentale: selezioni e proiezioni il più presto possibile.
### Equivalenza di Espressioni
Due espressioni sono equivalenti se producono lo stesso risultato (qualunque sia l'istanza attuale). I DBMS cercano di eseguire espressioni equivalenti ma meno costose.
___Push Selections Down___:
	Riduce la dimensione del risultato intermedio e quindi il costo dell'operazione $$\sigma(R_1 \bowtie R_2)\equiv R_1 \bowtie \sigma(R_2)$$
___Push Projections down___:
	Riduce risultato intermedio $$\pi(R_1\bowtie R_2)\equiv R_1 \bowtie \pi(R_2)$$
# Grafo
Un Grafo $G=(V,E)$ consiste in:
- un insieme $V$ di __vertici__ (o __nodi__).
- un insieme $E$ di coppie di vertici, detti __archi__.
  Ogni arco connette due vertici
Un __grafo Orientato__ (o __diretto__) è un grafo di archi orientati e rappresenta relazioni orientate tra coppie di oggetti.
Un __grafo non orientato__ (o __non diretto__) è un grafo di archi non orientati e rappresenta relazioni simmetriche tra coppie di oggetti.
# Cammino e Ciclo
Un cammino di un grafo $G=(V,E)$ da un vertice $x$ ad $y$ è dato da una sequenza di vertici $v_i$ di $V$ con $v_0=x$ e $v_k=y$, tale che per ogni $1 \leq i \leq k$, l'arco $(v_{i-1},v_i) \in E$ 
Un cammino $(v_0,...,v_k)$ tale che $v_0=v_k$ è detto __ciclo__.
Un grafo diretto è detto aciclico se non contiene cicli.
# Albero
Un grafo non orientato si dice __connesso__ se esiste un cammino tra ogni coppia di vertici.
Un albero è un grafo non orientato nel quale due vertici qualsiasi sono connessi da un solo cammino.
# Simboli Katex Utili
leftarrow: \leftarrow: $\leftarrow$ 
select: sigma: $\sigma$ 
project: pi: $\pi$ 
inner/natural join: bowtie: $\bowtie$ 
cross product: times: $\times$ 
rename: rho: $\rho$ 
leg: $\leq$ 
geq: $\geq$ 
neq: $\neq$ 
and: wedge: $\wedge$ 
or: vee: $\vee$ 
not: neg: $\neg$ 