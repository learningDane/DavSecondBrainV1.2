#uni 
TSP = traveling salesman problem = problema del commesso viaggiatore
Dati dei nodi collegati da archi, con ogni arco con relativo costo:
Trovare il cammino di costo minimo che includa tutti i nodi una ed una sola volta, detto ___Ciclo Hamiltoniano___.
Questo problema su $n$ nodi ha $n!$ soluzioni ammissibili.
# Modello
$N$ nodi
Variabili: $x_{ij}= (arco \ (i,j) \in ciclo) \quad ? \quad 1:0$ 
$$\begin{cases} \end{cases}$$
# Ciclo Hamiltoniano Simmetrico
Quando la direzione dei legami non importa.
Potremmo usare le tecniche risolutive del TSP [[#Asimmetrico]] ma come segue possiamo dimezzare le variabili.
### Modello
$$\begin{cases} min \  c^T\cdot x \\ \sum_{i<j}x_{ij}+\sum_{j<i}x_{ji} =2 \space \forall j \\ \\ \sum_{ \begin{matrix} i \in S \\j \notin S \\ i<j\end{matrix} } x_{ij} + \sum_{ \begin{matrix} i \notin S \\j \in S \\ j<i\end{matrix} } x_{ji} \geq1 \space \forall j \space , \space S \subset N\\ x_{ij}\in \{0,1\}\end{cases}$$
I Primi si chiamano ___vincoli di grado___, ovvero ogni nodo ha tot legami, grado 2, e sono $n$ vincoli (con $n=|nodi|$). In ogni vincoli ci sono $n-1$ legami.
I secondi si chiamano ___vincoli di connessione___.
Le variabili sono $|x|=\frac{n!}{|S|!(n-|S|)!}$ 
La matrice $Aeq$ avrà dimensioni $n\times |x|$ 
La matrice $A$ avrà dimensioni $(2^n-2n-2) \times |x|$ ma in realtà si dimezzano.
### Risoluzione
Trovare una $V_I$, trovare una $V_S$, applicare Riduzione del Gap (valido per tutte le PLI).
- $V_I$: Trovare [[k-Albero]] tramite [[Algoritmo di Kruskal]].
- $V_S$: Algoritmo del Nodo più vicino.
- Riduzione del gap: [[Algoritmo di Riduzione del Gap Branch and Bound]]. 