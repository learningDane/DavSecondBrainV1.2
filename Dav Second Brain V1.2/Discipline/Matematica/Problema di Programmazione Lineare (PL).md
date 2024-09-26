#uni 
Un problema di programmazione lineare segue il seguente [[Modello Matematico]]:
$$\begin{cases} min/max \ c^T \cdot x \\ Ax \leq b \\ Bx \geq d \\ Cx = e \\ se \ non \ cooperativo \ aggiungere \ x\in Z^n\end{cases}$$
Ogni problema PL può essere portato nella seguente forma standard
### Trasformazione in forma Standard
La forma standard permette di costruire facilmente la [[Regione Ammissibile]], inoltre, in molti programmi, come [[MatLab]] questa forma è l'unica utilizzabile.
___Problema di Programmazione Lineare in forma Primale Standard___:
$$\begin{cases} max \ c^T \cdot x \\ Ax \leq b\end{cases}$$
##### Trasformazioni Equivalenti
1. i $\geq$ diventano $\leq$
2. i $=$ diventano un sistema $\begin{cases} \leq \\ \leq \end{cases}$ (sdoppio)
3. i $min$ diventano $max$, poiché $\overline x \in argmax \ f \leftrightarrow \overline x \in argmax \ -f$ 
4.  $Ax \leq b$ diventano un sistema $\begin{cases} Ax + S=b \\ S \geq 0 \end{cases}$ con $S$ dicesi $slack$ 
5. coming
# Soluzione Ottima
La [[Regione Ammissibile]] di un problema $(P)$ di programmazione lineare è un [[Poliedro]] $P$. 
Il $max$ non può essere all'interno della regione, deve essere sul Bordo (vedi [[Teorema di Fermat]]). 
1. Il $max$ se esiste, appartiene al bordo
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
# Problemi
[[Problema di Produzione]] 
[[Problema di Assegnamento]] 