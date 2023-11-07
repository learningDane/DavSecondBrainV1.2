#uni 26/09/2023
# Basi
Una funzione lega due [[Insiemi]] attraverso una relazione.
Per avere una funzione servono: due insiemi e una relazione:
A: ___dominio___
B: ___codominio___
___Relazione___: $f$: relazione che a ogni elemento di $A$ associa __uno ed uno__ solo elemento di $B$.
###### Funzioni Uguali
Due funzioni $f(x)$ e $g(x)$ sono ___uguali___ se hanno lo stesso Dominio e se $\forall x \in D \ : \ f(x) = g(x)$ 
###### Zeri di una Funzione
Un numero $a$ è detto ___zero della funzione___ $f(x)$ se $f(a)=0$ 
###### Studiare il Segno di una Funzione
___Studiare il segno___ di una funzione significa cercare per quali valori del Dominio la funzione è positiva e per quali altri la funzione è negativa.
###### Simmetrie
Una funzione è detta ___pari___ (simmetrica rispetto all'asse $y$) se $f(x) = f(-x)$, ed è detta ___dispari___ (simmetrica rispetto all'origine) se $f(x)=-f(-x)$ .
###### Funzioni crescenti, in senso lato, monotone
Una funzione è detta ___crescente___ in un intervallo $I$ se $\forall x_1, x_2 \in I, x_1 < x_2 \ : \ f(x_1) < f(x_2)$ , è detta invece ___non decrescente___ o ___crescente in senso lato___, se $f(x_1) \leq f(x_2)$. Vale un discorso speculare per la decrescenza.
Una funzione è detta ___monotona___ se è sempre crescente o decrescente.
###### Funzione Inversa
Data la funzione biunivoca $y=f(x)$ da $A$ a $B$, la funzione inversa di $f$ è la funzione biunivoca $x=f^{-1}(y)$ da $B$ a $A$, che associa ad ogni $y$ di $B$ il valore $x$ di $A$ tale che $y=f(x)$.
Se una funzione ammette inversa, si dice ___invertibile___.
Il grafico di una funzione e quello della sua inversa sono simmetrici rispetto alla bisettrice del primo e del terzo quadrante.
###### Funzione Composta
Date le funzioni $g$ ed $f$, la funzione composta $g \circ f$ associa ad ogni $x$  del dominio di $f$ che ha immagine $f(x)$ nel dominio d $g$ il valore $y=g[f(x)]$ .
In generale $g \circ f \neq f \circ g$ .
# Tipi di Funzioni
###### __iniettiva__
$$\forall a_1,a_2 \in A\ \ t.c.\ \ a_1\neq a_2 \implies f(a_1) \neq f(a_2)$$
A ogni elemento di $B$, $f$ lega al più un elemento di $A$.
##### __suriettiva__ o invertibile
$$\forall \ b \in B,\ \exists \ a \in A,\ t.c.\ f(a)=b$$
a ogni elemento di $B$ è associato almeno un elemento di $A$.
##### __biunivoca__ o bicettiva 
Una funzione sia iniettiva che suriettiva, lega ad ogni elemento di $A$ uno ed uno solo elemento di $B$ e ad ogni elemento di $B$ uno ed uno solo elemento di $A$.
Una funzione è invertibile se e solo se è biunivoca.

##### Condizioni
Se il codominio contiene meno elementi del dominio la funzione non può essere iniettiva.
# Invertibilitá di una Funzione
In generale, sotto alcune ipotesi, l'inversa di una funzione é invertibile.
Definizione di invertibile:
$f:[a,b] \to Im(f) \ esiste \ g : Im(f) \to [a,b]$ con $g(f(x)) = x$ e $f(g(y)) = y$ 
##### Teorema
Ipotesi: $f \in C([a,b]) \ invertibile : f:[a,b] \to [c,d]$ 
Tesi: $\exists g \in C([c,d]) ; g=f^{-1} ; \ g : [c,d] \to [a,b]$ 
### Esempi
$\sin h(x) = \frac{e^x - e^{-x}}{2} \implies \sin h^{-1} x = settore \sin h(x)$ 
$\frac{1}{\sin(x)} \neq \sin^{-1} (x) \neq \arcsin (x)$ 
# Funzioni Periodiche
Una funzione è detta ___periodica___ di periodo $T$, con $T> 0$, se $\forall k \in Z \ : \ f(x) = f(x + kT)$ .
Una funzione periodica non può essere iniettiva.
Se una funzione è periodica di periodo $T_1$, allora $f(kx)$ è periodica di periodo $T= \frac{T_1}{k}$ .

# Funzioni a tratti
Una funzione è detta definita a tratti se per tratti diversi di dominio ha relazioni diverse. $$f(x) = \begin{cases} \frac{x}{2} \ se\ n\ è\ pari \\ 1\ se\ è\ dispari\end{cases} $$

# Successioni
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
# Permutazione
Sia $A$ un insieme, una permutazione di $A$ è una funzione $f$ biunivoca tale che $f: A \to A$.
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
# Teoremi
### Teorema di Weierstrass
Ipotesi: $f : [a,b] \to R : f \in C([a,b])$ 
Tesi: $\exists x_m \in [a,b] \ , \ x_M \in [a,b] \ t.c. \ f(x_m) = min \ , \ f(x_M) = Max$ 
### Teorema degli Zeri
Ipotesi: $f\in C([a,b]) : f(a) \cdot f(b) < 0$ 
Tesi: $\exists \overline c \in [a,b] \ t.c. \ f(\overline c ) = 0$ 
Attraverso questo teorema, con il metodo della bisezione é possibile trovare la posizione dello zero, di volta in volta dimezzando il campo di valori.
Dimostrazione attraverso il [[Limiti#Teorema della Permanenza del Segno]] : 
Abbiamo $f(a_n) < 0 \to \lim f(a_n) = f(c) \leq 0$ e $f(b_n) < 0 \to \lim f(b_n) = f(c) \geq 0$ 
Quindi $f(c) \leq 0$ e $f(c) \geq 0$ 
Allora $f(c)=0$ 
### Teorema dei Valori Intermedi
Ipotesi: $f \in C([a,b])$ quindi per il Teorema di Weierstrass esistono massimo e minimo $m=min \ f$ e $M = max \ f$ 
Tesi: $\exists \overline c \in [a,b] \ t.c\ f(\overline c) = λ \in ]m,M[$ 
Per dimostrarlo basta traslare la funzione sull'asse y di modo che λ sia in $y=0$ e poi si applica il teorema degli zeri., dato che ne sono rispettate le ipotesi
Esiste poi il _Secondo Teorema dei Valori Intermedi_ dove semplicemente nella formulazione invece di massimo e minimo si usano estremo inferiore ed estremo superiore.
### Teorema di Rolle
Ipotesi: $f \in C([a,b]) , f \ derivabile \ in \ ]a,b[ , f(a) = f(b)$ 
Tesi: $\exists c \in ]a,b[ : f'(c) = 0$ 
### Teorema di Lagrange
Ipotesi: $f \in C([a,b]) , f \ derivabile \ in \ ]a,b[$
Tesi: $\exists c \in ]a,b[ : f'(c) = \frac {f(b) - f{a}}{b-a}$ 
###### I corollario
###### II Corollario
se $f'(x) \geq 0 , \forall x \in ]a,b[ \implies f \ crescente$ 
###### III Corollario
se $f'(x) > 0 \forall x \in ]a,b[ \implies f'(x_0)=0$ o
###### IV Corollario

# Principali Funzioni
###### Funzione esponenziale $y=x^2$ 
```chart
type: line
labels: [-3,-2,-1,0,1,2,3]
series:
  - title: x axis
	data: [0,0,0,0,0,0,0,0,0]
	series:
  - title: f(x)
	data: [9,4,1,0,1,4,9]
  - title:
	data: [-3]
tension: 0.2
width: 80%
labelColors: false
fill: false
beginAtZero: false
bestFit: false
bestFitTitle: undefined
bestFitNumber: 0
```
###### Funzione Logaritmica $y=\ln x$ 
```chart
type: line
labels: [0,0.5,1,1.5,2,2.5,3,3.5,4,4.5,5,5.5,6]
series:
  - title: x axis
	data: [0,0,0,0,0,0,0,0,0,0,0,0,0]
	series:
  - title: f(x)
	data: [-15,-5,0,0.4,0.69331,0.91,1.1,1.25,1.39,1.5,1.61,1.70,1.9]
  - title:
	data: [10]
tension: 0.2
width: 80%
labelColors: false
fill: false
beginAtZero: false
bestFit: false
bestFitTitle: undefined
bestFitNumber: 0
```
###### Funzione Tangente $y=\tan x$ 
```chart
type: line
labels: [-4,-3.5,-3,-2.5,-2,-1.5,-1,-0.5,0,0.5,1,1.5,2,2.5,3,3.5,4]
series:
  - title: x axis
	data: [0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0,0]
	series:
  - title: f(x)
	data: [-1.2,-0.37,0.14,0.75,2.18,14]
  - title: f(x)
	data: [\,\,\,\,\,-14,-1.5,-0.54,0,0.54,1.5,14]
  - title: f(x)
	data: [\,\,\,\,\,\,\,\,\,\,\,-14,-1.5,-0.54,0,0.54,1.5]
tension: 0.2
width: 80%
labelColors: false
fill: false
beginAtZero: false
bestFit: false
bestFitTitle: undefined
bestFitNumber: 0
```