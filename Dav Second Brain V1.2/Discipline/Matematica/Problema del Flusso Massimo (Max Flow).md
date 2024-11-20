#uni 
Questo è un [[Problema di Programmazione Matematica a Reti Capacitate]] con ogni arco di costo nullo, in cui si chiede di trovare il flusso massimo tra due nodi.
Per convenzione chiamiamo il nodo $1$, $s$ (source) ed il nodo $n$, $t$ (tail).
È possibile vedere il problema in maniera leggermente diversa in modo da semplificare l'apprendimento, in particolare aggiungiamo un arco, l'arco $(n,1)$ di costo $-1$, che quindi porta ad un guadagno per ogni unità di flusso che lo attraversa;
Il problema diventa la massimizzazione del flusso su questo ultimo arco, in particolare chiamiamo questo flusso $x_{n,1}$, $v$, che sarà la soluzione ottima del nostro problema.
# Modello
$$\begin{cases} \max \quad v \\ Ex = b \quad---->\quad b=\begin{cases}-v \quad i =s \\0 \quad i\neq s,t\\v \quad i =t \end{cases} \\ 0 \leq x_{(i,j)} \leq u_{(i,j)} \end{cases}$$
ovviamente è possibile scrivere la funzione obiettivo come $-\min \quad -v$ .
# Considerazioni
Osserviamo che continua a valere il [[Teorema di Interezza]], poiché $E$ rimane sempre una Matrice di Incidenza su Rete ([[Problema di Programmazione Matematica a Reti non Capacitate#Matrice di Incidenza della Rete]]), infatti avendo aggiunto questo arco risultano ancora tante colonne quanti archi, quindi rimane ad essere un [[Problema di Programmazione Matematica a Reti Capacitate]] di costo minimo, quindi è sempre possibile con l'[[Algoritmo del Simplesso su Reti]].