#uni 
La complessità in algoritmi si divide in ___complessità spaziale___ e ___complessità temporale___. Siccome la complessità spaziale ha poche soluzioni in ambito software  e più in ambito hardware, noi parleremo solo di complessità temporale. 
Dato un algoritmo A la ___complessità___ viene determinata contando il numero di operazioni aritmetiche e logiche, accesso ai file, letture e scritture in memoria, etc. 
Quindi è il tempo impiegato proporzionale al numero di operazioni eseguite (ciascuna a costo unitario).
___Definizione del Corso:___
	La complessità di un algoritmo è una funzione (sempre positiva) che associa alla __dimensione__ del problema il __costo__ della sua risoluzione.
La complessità è diversa dal ___profiling___ (tecnica di analisi di un programma basato sulla misurazione di indici di prestazione a _runtime_) poiché questo dipende dall'ambiente di esecuzione. 
Si indica normalmente come $O(f(n))$ con $n$ numero di dati. 
Definiamo $O(f(n))$ l'insieme delle funzioni di ordine $O(f(n))$.
$O(f(n))$ è quindi l'insieme delle funzioni della forma $g(n) = an$ 
$O(f(n^2))$ è quindi l'insieme delle funzioni della forma $g(n) = an^2$ 
___Notazione__:
	$f(n)$ è di ordine $O(g(n))$ 
	1. $f(n)$ è $O(g(n))$ 
	2. $f(n) \in $O(g(n))$ 
	3. 
___Regole___:
	se $f(n)$ è $O(g(n))$ e $g(n)$ è $O(h(n))$ allora -> $f(n)$ è $O(h(n))$
	per ogni costante $k$, $k$ è $O(1)$ 
	per $m<=p$, $n^m$ è $O(n^p)$ 
	un polinomio di grado $m$ è $O(n^m)$ 
Quando valuto due algoritmi li valuto in maniera asintotica, quindi $T_{p2} = 2n = 4n = T_{p1}$ per esempio.