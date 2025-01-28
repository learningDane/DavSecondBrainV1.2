#uni 
Un cammino dal nodo $n_1$ al nodo $n_{p+1}$ è un insieme di archi $a_1, . . . , a_p$ tale che per ogni $i= 1, . . . , p$ si ha che $a_i = (n_i, n_{i+1})$ oppure $a_i = (n_{i+1}, n_i)$ ed inoltre che
gli archi siano tutti diversi tra loro.
Se vale sempre la prima condizione, cioè gli archi coinvolti vanno dal nodo $n_i$ al nodo $n_{i+1}$, il cammino si dice orientato.
Questo è il problema di trovare (se esistono) i cammini orientati di costo minimo da un nodo $r$ verso tutti gli altri nodi.
Tale problema si può formulare come un problema di flusso di costo minimo ponendo le capacità superiori $u_{ij} = +∞$ ed i bilanci dei nodi tutti uguali ad $1$ tranne quello del nodo $r\quad$:   $b=\begin{cases} 1 \quad se \ i≠ r \\ -n+1 \quad se \ i=r\end{cases}$ 
# Modello
Identico a quello del [[Problema di Programmazione Matematica a Reti non Capacitate (PLRnC)]].
$$\begin{cases} 
\min \sum_{(i,j)\in A}c_{ij} \cdot x_{ij} \\
\sum_i x_{ij} - \sum_i x_{ji} = b_j \quad \forall j \quad  b=\begin{cases} 1 \quad se \ i≠ r \\ -n+1 \quad se \ i=r\end{cases}\\
x_{ij}\in N \quad \forall(i,j)\in A
\end{cases}$$
# Risoluzione
La soluzione di questa classe di problemi è molto facile in quando necessita solamente dell'applicazione dell'[[Algoritmo di Dijkstra]]. 