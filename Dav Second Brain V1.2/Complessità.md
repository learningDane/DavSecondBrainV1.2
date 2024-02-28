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
___Regole___:
	se $f(n)$ è $O(g(n))$ e $g(n)$ è $O(h(n))$ allora -> $f(n)$ è $O(h(n))$
	per ogni costante $k$, $k$ è $O(1)$ 
	per $m<=p$, $n^m$ è $O(n^p)$ 
	un polinomio di grado $m$ è $O(n^m)$ 
Quando valuto due algoritmi li valuto in maniera asintotica, quindi $T_{p2} = 2n = 4n = T_{p1}$ per esempio.
# Notazioni
In generale una funzione $f(n) = expr$ si indica con solo $expr$ 
Quindi $f(n)=100n \ è \ O(g(n)=5n)$ diventa $100n \ è \ O(5n)$.
sinonimi: 
	1. $f(n)$ è di ordine $O(g(n))$ 
	2. $f(n)$ è $O(g(n))$ 
	3. $f(n) \in O(g(n))$ 
	4. $f(n)$ = $O(g(n))$ 
$O(n)$ è l'insieme delle funzioni di ordine $O(f(n))$ 
### Notazione O Grande: Limite Asintotico Superiore
$f(n)$ è di ordine $O(g(n))$ se esistono un intero $n_0$ ed una costante $c>0$ tali che $\forall n \geq n_0 : f(n) \leq c g(n)$. Quindi oltre una certa $n_0$ $f(n)$ è minore di $g(n)$ 
Classi di Complessità:
	$O(1)$ = costante; $O(log(n))$ = logaritmica; $O(n)$ = lineare; $O(nlog(n))$ ; $O(n^2)$ = quadratica ; $O(n^3)$ = cubica; $O(n^p)$ = polinomiale ; $O(2^p)$ e $O(n^n)$ = esponenziale.
### Notazione theta grande: Limite Asintotico Stretto
$f(n)$ è $\Theta(g(n))$ se $f(n)$ è $O(g(n))$ e $f(n)$  è $\Omega(g(n))$ 
Quindi $f(n)$ è $\Theta g(n)$ quando $f$ e $g$ hanno lo stesso ordine di complessità.
### Notazione Omega Grande: Limite Asintotico Inferiore
$f(n)$ è $\Omega(g(n))$ se esistono un intero $n_0$ ed una costante $c>0$ tali che $\forall n \geq n_0 : f(n) \geq c g(n)$ 

### Regole
1. Regola dei fattori costanti:
	   per ogni costante positiva $k$, $O(f(n)) = O(kf(n))$ 
2. Regola della somme:
	   se $f(n)$ è $O(g(n))$ allora $f(n) + g(n)$ è $O(g(n))$ 
3. Regola del prodotto
	   se $f(n)$ è $O(f_1(n))$ e $g(n)$ è $O(g_1(n))$, allora $f(n)g(n)$ è $O(f_1(n)g_1(n))$ 
4. se $f(n)$ è $O(g(n))$ e $g(n)$ è $O(h(n))$, allora $f(n)$ è $O(h(n))$ 
5. per ogni costante $k$, $k$ è $O(1)$ 
6. per $m \leq p$, $n^m$ è $O(n^p)$ 
7. un polinomio di grado $m$ è $O(n^m)$ 