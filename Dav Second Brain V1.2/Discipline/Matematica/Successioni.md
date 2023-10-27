#uni 
Una successione numerica è una funzione che associa ad ogni numero naturale n un numero reale r.
Sono indicate con $f_n$ dove $n\in N$.
Una successione si dice limitata se: $\exists M > 0 \ t.c. \ |a_n| < M, \ \forall n \ in N$
Il [[Limiti]] della successione è dato da: $$\forall \epsilon > 0 \exists n_0 \ in N \ con \ n_0 > 0 \ t.c. \ \forall n>n_0 \ risulta \ |a_n - a | < \epsilon$$$$lim_{n \to \infty} a_n = a$$
### Successioni monotone
Una Successione è detta _monotona crescente_ se $\forall n \in N \ : \ a_n < a_{n+1}$
Una Successione è invece detta _monotona non decrescente (o crescente in senso lato)_ se $\forall n \in N \ : \ a_n \leq a_{n+1}$ 
### Sottosuccessioni
$b_n$ è detta sottosuccessione di $a_n$ se $\exists k: N \to N \ strettamente \ crescente \ t.c. \ b_n = a_{k_n}$ 
##### Teorema di Regolarità per Sottosuccesioni
Se il [[Limiti]] $\lim_{n \to \infty} a_n = L (+ \infty) \ allora \ \forall a_{n_k} \ sottosuccessione \ di \ a_n \ : \ \lim_{k \to \infty} a-{n_k} = L (+ \infty)$ 
In parole povere la sottosuccessione di una successione ha lo stesso limite della successione.
###### Corollario del Teorema di Regolarità per Sottosuccessioni
Se esistono due sottosuccessioni di $a_n$, $a_{n_k}$ e $a_{m_k}$ tali che $\lim_{ n \to \infty} a_{n_k} \neq \lim_{m \to \infty} a_{m_k}$ allora la successione $a_n$ non ammette limite.
### Limiti di successioni
___OGNI successione monotona ammette limite___.
Ogni Successione Monotona limitata ammette come limite l'estremo, superiore o inferiore che sia.
1. Limite di una successione crescente limitata superiormente: #teorema
	Ipotesi: $a_n \leq a_n + 1$ , $\forall n \in N$ ; $\exists M \ t.c. \ a_n \leq M$ , $\forall n \in N$
	Tesi: $\lim_{n \to \infty} a_n = \sup a_n$ 
2. Il limite di una successione crescente non limitata superiormente: #teorema 
   ipotesi:
	   1. $a_n \leq a_{n+1}$ 
	   2. $\forall k \in R \ : \ \exists \overline n \ t.c. \ a_{\overline n} > k$ 
   tesi: 
	   $\lim_{n \to \infty} a_n = + \infty$