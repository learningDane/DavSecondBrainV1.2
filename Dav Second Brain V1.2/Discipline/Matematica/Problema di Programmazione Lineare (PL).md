#uni 
Un problema di programmazione lineare segue il seguente [[Modello Matematico]]:
$$\begin{cases} min/max \ c^T \cdot x \\ Ax \leq b \\ Bx \geq d \\ Cx = e \\ se \ non \ cooperativo \ aggiungere \ x\in Z^n\end{cases}$$
Ogni problema PL può essere portato nella seguente forma standard
### Forma Standard
Una forma standard è un formato in cui possono essere portati TUTTI i problemi attraverso le trasformazioni equivalenti. Ciò si fa per semplicizzare oppure perché programmi come [[MatLab]] accettano solo alcuni formati standard.
###### Formato Primale Standard
$$\begin{cases} max \ c^T \cdot x \\ Ax \leq b\end{cases}$$
###### Formato Duale Standard
$$\begin{cases} min \ c^Tx \\ Ax=b \\ x\geq 0 \end{cases}$$
###### Formato Linprog Standard
$$\begin{cases} min \ c^T x \\ Ax \leq b \\ A_{eq} = b_{eq} \\ LB \leq x \leq UB \end{cases}$$
##### Trasformazioni Equivalenti
1. i $\geq$ diventano $\leq$
2. i $=$ diventano un sistema $\begin{cases} \leq \\ \leq \end{cases}$ RADDOPPIO DEI VINCOLI
3. i $min$ diventano $max$, poiché $\overline x \in argmax \ f \leftrightarrow \overline x \in argmax \ -f$ 
4.  $Ax \leq b$ diventano un sistema $\begin{cases} Ax + S=b \\ S \geq 0 \end{cases}$ con $S$ dicesi $slack$ AGGIUNGO VARIABILE
5. $x \geq 0$ diventa $x_i = x_i^{++} - x_i^+$ RADDOPPIO DELLE VARIABILI
# Soluzione Ottima
La [[Regione Ammissibile]] di un problema $(P)$ di programmazione lineare è un [[Poliedro]] $P$. 
1. Il $max$ se esiste, appartiene al bordo ([[Teorema di Fermat]])
2. Il $max$ può essere $+\infty$ (con $P$ illimitati)
3. La Soluzione Ottima non è per forza unica
4. $P$ può essere vuoto ($\to$ ranking dei vincoli)
5. Almeno un vertice è soluzione ottima
6. se la regione ammissibile si restringe i minimi salgono (___Rilassamento___)

___Cono di Competenza___ = insieme di vettori $c$ che hanno tra le soluzioni ottimali lo stesso vertice. Si dice cono di competenza relativo ad un vertice.
Proposizione:
$(P) \in PL$:
1. se $max \ cx = -\infty$ $\implies$ ha $P$ vuoto
2.  può avere $P$ illimitato
3. se ha $2$ soluzioni ottime $\implies$ ha illimitate soluzioni ottime
# Risoluzione di un Problema di Programmazione Lineare
Il [[Teorema Fondamentale dei Problemi PL]] ci dice che dato un problema con [[Poliedro]] non vuoto e soluzione limitata, la soluzione ottima esiste, inoltre, se il poliedro non è privo di vertici, per il [[Teorema di Fermat]] sappiamo che deve essere sul bordo e quindi almeno un vertice è soluzione.
# Problemi
[[Problema di Produzione]] 
[[Problema di Assegnamento]] 
[[Problema di Trasporto]] 