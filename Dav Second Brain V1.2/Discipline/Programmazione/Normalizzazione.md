#uni 
Una ___forma normale___ è una proprietà di un [[Database]] relazionale ([[Modello Logico Relazionale]]) che ne garantisce la qualità, ovvero l'assenza di determinati difetti, tra cui le anomalie.
Una relazione non normalizzata:
- presenta ridondanze
- durante gli aggiornamenti incontra errori
Le forme normali sono di solito definite sul [[Modello Logico Relazionale]] ma hanno senso anche in altri contesti, per esempio nel [[Modello Entity-Relationship]].
La _normalizzazione_ è una procedura che permette di trasformare schemi non normalizzati in schemi che soddisfano una determinata forma normale. Questa procedura viene utilizzata come tecnica di verifica dei risultati della progettazione di una base di dati, non è una metodologia di progettazione.
# Decomposizione di Schemi
_Teorema_:
	Dato uno schema $R(T)$, l'insieme di schemi $\rho = \{R_1(T_1),...,R_k(T_k)\}$ è una ___decomposizione___ di $R$ se e solo se $\cup_iT_i=T$
Nota bene: la precedente definizione non richiede che gli schemi $R_i$ siano disgiunti.
Affinché uno schema e la sua decomposizione siano equivalenti quest'ultima deve _preservare i dati_ e _preservare le dipendenze_.
##### Teorema della perdita dei dati
Se $\rho = \{R_1(T_1),...,R_k(T_k)\}$ è una decomposizione di $R(T,F)$, allora per ogni istanza di $r$ di $R(T)$ si ha $$r \in π_{T_1}(r) \bowtie ... \bowtie π_{T_k}$$
Questo teorema ci dice che perdiamo informazione quando, ricostruendo una relazione, otteniamo più tuple che nella relazione originaria.
### Decomposizione che preserva dati
Se $\rho = \{R_1(T_1),...,R_k(T_k)\}$ è una decomposizione di $R(T,F)$, $\rho$ è una decomposizione che __preserva i dati__ se e solo se, per ogni relazione $r$ che soddisfa $R(T,F)$, si ha: $$r = π_{T_1}(r) \bowtie ... \bowtie π_{T_k}$$
Questa definizione ci dice che in una decomposizione che preserva dati, ogni istanza valida $r$ della relazione di partenza deve essere uguale al join naturale delle sue proiezioni sui vari $T_i$.
##### Teorema di preservazione dei dati
Sia $\rho = \{R_1(T_1),R_2(T_2)\}$ una decomposizione di $R(T,F)$, essa preserva i dati se e solo se $T_1 \cap T_2 \to T_1 \in F^+$ oppure $T_1 \cap T_2 \to T_2 \in F^+$.
In altre parole gli attributi comuni alle due relazioni devono essere chiave in una delle due tabelle.
### Decomposizione che preserva le dipendenze
Dato uno schema $R(T,F)$ e una decomposizione $\rho = \{R_1(T_1),...,R_k(T_k)\}$, $\rho$ è una decomposizione di $R(T,F)$ che preserva le FD se e solo se: $\cup_iπ_{T_i}(F)\equiv F$, cioè se $(\cup_iπ_{T_i}(F))^+= F^+$ 
###### Verificare una decomposizione che preserva le FD
Per verificare se una decomposizione di $R(T,F)$ in due relazioni con attributi $X,Y$ preserva le dipendenze bisogna verificare che $(π_X(F) \cup π_Y(F))^+ = F^+$ 
Per fare ciò è necessario:
- saper calcolare la proiezione di un insieme di FD su un insieme di attributi: _algoritmo con complessità esponenziale_ 
- saper determinare l'equivalenza di due insiemi di FD: _algoritmo con complessità polinomiale_:
	- per ogni $X \to Y \in F$ calcoliamo $X_G^+$ e verifichiamo se $Y \in X_F^+$ 
	- di nuovo invertendo $F$ e $G$.
# Proiezione di un insieme di dipendenze
Dato $R(T,F)$ e $T_i \in T$, la proiezione dell'insieme di FD $F$ sull'insieme di attributi $T_i$ è $$π_{T_i}(F)=\{ X \to Y \in F^+ | X,Y \in T_i\}$$
### Algoritmo per il calcolo di $π_{T_i}(F)$ 
_Input_: $R(T,F)$ e $T_i \in T$ 
_Output_: $π_{T_I}(F)$ 
$Z \gets \{ \}$ 
__for each__ $Y \in T_i$ __do__ 
	$W \gets Y^+ - Y$ 
	$Z \gets Z \cup \{ Y \to (W \cap T_i)\}$ 
__return__ $Z$ 
Complessità Esponenziale nel caso peggiore.
# Forma Normale di Boyce-Codd (BCNF)
_Teorema_:
	Uno schema $R(T,F)$ è in forma normale Boyce-Codd (___BCNF___) se e solo se per ogni dipendenza funzionale non banale $X \to Y \in F^+$, $X$ è una superchiave di $R$. 
_Corollario_:
	Uno schema $R(T,F)$ con $F$ copertura minimale è in BCNF se e solo se per ogni FD elementare $X \to A \in F$, $X$ è una superchiave.
Questa forma normale si basa sull'idea che una dipendenza funzionale $X \to A$, in cui $X$ non contiene attributi estranei ([[Dipendenza Funzionale#Ridondanza]]), indica che nella realtà che modella esiste una collezione di entità omogenee univocamente identificate da $X$.
Da questa definizione, il fatto che uno schema sia in BCNF dipende dalla chiusura $F^+$ e non dalla copertura $F$, purtroppo per calcolare $F^+$ abbiamo solo algoritmi esponenziali. Possiamo però facilmente stabilire se uno schema è in BCNF con un algoritmo di complessità polinomiale.
### Algoritmo di verifica BCNF
_Input_: schema $R(T,F)$ 
_Output_: __true__ se $R$ è in BCNF, __false__ altrimenti
__for each__ $X \to Y \in F$ __do__
	__if__ $Y \notin X$ __and__ $T \notin X^+$ __then__
		__return false__
__return true__ 
### Normalizzazione in BCNF in casi semplici
Per ogni dipendenza $X \to Y$ che viola la BCNF, definiamo una nuova relazione su $XY$ ed eliminiamo $Y$ dalla relazione originaria.
###  Algoritmo per decomposizione in BNCF che preserva i dati
_Input_: $R(T,F)$ (per semplicità gli elementi di $F$ sono nella forma $X \to A$)
_Output_: $\rho$ in BNCF che preserva i dati
$\rho \leftarrow \{R(T, F)\}$  
**while** esiste $R_i(T_i, F_i) \in \rho$ che non è in BCNF **do**  
	**for each** $X \rightarrow A \in F_i$ **do**  
		**if** $A \notin X$ **and** $T_i \not\subseteq X^+$ **then**  
			$R_1 \leftarrow R_i \left(T_i - A, \pi_{T_i - A}(F_i)\right)$  
			$R_2 \leftarrow R_i \left(X + A, \pi_{X + A}(F_i)\right)$  
			$\rho \leftarrow \rho - \{R_i\} \cup \{R_1, R_2\}$  
			**break**  
**return** $\rho$
Non è garantita la preservazione delle dipendenze.
# Terza Forma Normale (3NF)
_Teorema_:
	Una relazione è in 3NF se e solo se per ogni FD non banale $X \to A \in F^+$, è verificata almeno una delle seguenti condizioni:
	- $X$ è una superchiave di $R$ 
	- $A$ è contenuto in almeno una chiave di $R$ (in questo caso si dice che $A$ è un ___attributo primo___)
	Quindi se $R$ è in BCNF allora è anche in 3NF: $BCNF \implies 3NF$ 
La verifica di 3NF è un problema ___NP-completo___ e il miglior algoritmo deterministico noto ja complessità esponenziale nel caso peggiore. Occorre sapere le chiavi e l'algoritmo per farlo ha complessità esponenziale.
___Si può però sempre ottenere una decomposizione in 3NF che preserva dati e FD.___ 
### Algoritmo per decomposizione in 3NF
Dividiamo una copertura minimale $G$ in gruppi $G_i$ tale che tutte le le FD in un gruppo abbiano la stessa parte sinistra. Da ogni gruppo $G_i$ si definisce uno schema di relazione composto da tutti gli attributi che appaiono in $G_i$, la cui chiave, detta ___chiave sintetizzata___, è la parte sinistra comune:
_Input_: $R(T, F)$  
_Output:_ $\rho$ che preserva i dati e le dipendenze e con ogni elemento in 3NF
1. **Trovare una copertura minimale** $G$ di $F$ e porre $\rho \gets \{\}$
2. **Sostituire** in $G$ ogni insieme di dipendenze $\{X \rightarrow A_1, \dots, X \rightarrow A_h\}$ con la dipendenza $X \rightarrow A_1 \cdots A_h$
3. **Per ogni dipendenza** $X \rightarrow Y \in G$ creare uno schema con attributi $XY$ in $\rho$
4. **Eliminare** da $\rho$ ogni schema che sia contenuto in un altro schema di $\rho$
5. **Se** $\rho$ non contiene nessuno schema i cui attributi costituiscono una superchiave di $R$, aggiungere a $\rho$ uno schema con attributi $W$, dove $W$ è una **chiave** di $R$ 
Complessità polinomiale, sempre possibile e conserva dati e FD.