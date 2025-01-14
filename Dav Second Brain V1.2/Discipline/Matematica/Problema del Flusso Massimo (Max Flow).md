#uni 
Questo è un [[Problema di Programmazione Matematica a Reti Capacitate (PLRC)]] con ogni arco di costo nullo, in cui si chiede di trovare il flusso massimo tra due nodi.
Per convenzione chiamiamo il nodo $1$, $s$ (source) ed il nodo $n$, $t$ (tail).
È possibile vedere il problema in maniera leggermente diversa in modo da semplificare l'apprendimento, in particolare aggiungiamo un arco, l'arco $(n,s)$ di costo $-1$, che quindi porta ad un guadagno per ogni unità di flusso che lo attraversa;
Il problema diventa la massimizzazione del flusso su questo ultimo arco, in particolare chiamiamo questo flusso $x_{n,1}$, $v$, che sarà la soluzione ottima del nostro problema.
Viene risolto tramite l'[[Algoritmo di Ford Fulkerson Edmond Karp (FFEK)]].
# Teorema del MaxFlow-minCut
$$\max \{ \overline x\}=\min \{ \ u(N_s;N_t) \quad \forall \quad (N_s; N_t) \ \}$$
: _Il Flusso Massimo è pari alla portata del taglio di portata minima_.
Il Problema del Taglio di Portata minima è il problema duale del problema di Flusso Massimo.
# Modello
$$\begin{cases} \max \quad v \\ Ex = b \quad---->\quad b=\begin{cases}-v \quad i =s \\0 \quad i\neq s,t\\v \quad i =t \end{cases} \\ 0 \leq x_{(i,j)} \leq u_{(i,j)} \end{cases}$$
ovviamente è possibile scrivere la funzione obiettivo come $-\min \quad -v$ .
# Considerazioni
Osserviamo che continua a valere il [[Teorema di Interezza]], poiché $E$ rimane sempre una Matrice di Incidenza su Rete ([[Problema di Programmazione Matematica a Reti non Capacitate (PLRnC)#Matrice di Incidenza della Rete]]), infatti avendo aggiunto questo arco risultano ancora tante colonne quanti archi, quindi rimane ad essere un [[Problema di Programmazione Matematica a Reti Capacitate (PLRC)]] di costo minimo, quindi è sempre possibile con l'[[Algoritmo del Simplesso su Reti]].