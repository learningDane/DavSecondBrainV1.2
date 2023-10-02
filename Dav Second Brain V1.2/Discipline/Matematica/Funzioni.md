#uni 26/09/2023
# Basi
Una funzione lega due [[Insiemi]] attraverso una relazione.
Per avere una funzione servono: due insiemi e una relazione:
A: dominio
B: codominio
Relazione: $f$: relazione che a ogni elemento di $A$ associa __uno ed uno__ solo elemento di $B$.

# Tipi di Funzioni
###### __iniettiva__
$$\forall a_1,a_2 \in A\ \ t.c.\ \ a_1\neq a_2 \implies f(a_1) \neq f(a_2)$$
A ogni elemento di $B$, $f$ lega al più un elemento di $A$.
##### __suriettiva__ o invertibile
$$\forall \ b \in B,\ \exists \ a \in A,\ t.c.\ f(a)=b$$
a ogni elemento di $B$ è associato almeno un elemento di $A$.
##### __biunivoca__ o bicettiva o 
Una funzione sia iniettiva che suriettiva, lega ad ogni elemento di $A$ uno ed uno solo elemento di $B$ e ad ogni elemento di $B$ uno ed uno solo elemento di $A$.

##### Condizioni
Se il codominio contiene meno elementi del dominio la funzione non può essere iniettiva.

# Funzioni a tratti
Una funzione è detta definita a tratti se per tratti diversi di dominio ha relazioni diverse. $$f(x) = \begin{cases} \frac{x}{2} \ se\ n\ è\ pari \\ 1\ se\ è\ dispari\end{cases} $$

# Successione
Una successione numerica è una funzione che associa ad ogni numero naturale n un numero reale r.
Sono indicate con $f_n$ dove $n\in N$

# Funzione crescente
Una funzione è crescente se: $$\forall x_1\ e\ x_2\  \in D\ t.c.\ x_1<x_2\ \implies f(x_1) \leq f(x_2)$$
È invece ___strettamente crescente___ se risulta che $f(x_1)\ <\  f(x_2)$.

##### Dimostrazione esempio
Dimostriamo che $f(x)=x^2$ è crescente:
- Ipotesi: $x_1\leq x_2$
- Tesi: $x_1^2 < x_2^2$ 
$\forall \ x_1\ e\ x_2 \in D\ e\ \geq 0$ 
	Dimostrazione:
	$x_1\leq x_2$ equivale a dire che $0 \leq x_2^2 - x_1^2$ 
	quindi $0\leq (x_2 + x_1)(x_2 - x_1)$ 
	ma $x_2 + x_1$ è maggiore di zero perché $x_2$ e $x_1$ sono positivi
	e $x_2 - x_1$ è anche maggiore di zero poiché $x_2 > x_1$ per tesi
	Allora $f(x)=x^2$ è crescente, inoltre essendo entrambi diversi da $0$, il loro prodotto non può essere $0$, quindi la funzione è ___strettamente crescente___.