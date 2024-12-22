#uni 
- il gradiente è il vettore composto dalle derivate parziali della funzione.
- Teorema di Fermat: con $f \in C^1$, se $\nabla f(\overline x)=0$ allora $\overline x$ è punto di min/max locale.
- L'Hessiana è la matrice composta dalle derivate parziali (derivate due volte) della funzione:
  $$Hf(x)=\begin{bmatrix} \frac{\delta^2f(x)}{\delta x^2_1} \quad ... \quad \frac{\delta^2f(x)}{\delta x_1 \delta x_n} \\
  ... \quad \quad \quad\quad ... \\
					\frac{\delta^2 f(x)}{\delta x_2 \delta x_1 } \quad ... \quad \frac{\delta^2f(x)}{\delta x_n^2} \end{bmatrix}$$
	Per il Teorema di Schwartz l'Hessiana è simmetrica.
- Sia $\overline x$ stazionario, se $Hf(\overline x) > 0$ allora $\overline x$ è minimo locale. $\implies$ se $\overline x$ è minimo locale, allora $Hf(\overline x) >0$ 
- Una matrice è definita positiva ($> 0$) se $<Ax, x > > 0 \forall x$, è invece semidefinita positiva ($\geq 0$) se $<Ax,x> \geq 0 \forall x$ 
- Teorema: una matrice simmetrica è definita positiva se e solo se i suoi autovalori sono strettamente positivi, è semidefinita positiva se i suoi autovalori sono $\geq 0$.
- Teorema: le matrici simmetriche hanno autovalori Reali.
  quindi sulla Hessiana posso controllare $\det (H-\lambda I)=0, \quad \lambda > 0 ?$ 
- Quindi in questo ordine ho questi insiemi (Diagramma di Venn): Punti stazionari ($\nabla f =0$) $\rightarrow$ $H≥0$ $\rightarrow$ minimi locali $\rightarrow$ $H > 0$, quindi come criterio di stop dobbiamo usare la condizione necessaria $H ≥ 0$ 
- Teorema del calcolo della derivata direzionale: $$f'(\overline x, \overline d)=<\nabla f(\overline x),\overline d >$$
- __Forma quadratica___:
  $f(x)=x^T Qx+c^T x$ con $2Q=Hf$ 
  quindi se $f(x)=6x_1^2 +3x_1x_2 + 5x_2^2$ allora $Q=\begin{bmatrix} 6 \quad \frac{3}{2} \\ \frac{3}{2} \quad 5\end{bmatrix}$ e $H=\begin{bmatrix} 12 \quad 3 \\ 3 \quad 10 \end{bmatrix}$ 
- __Funzioni convesse__: 
  $f:R^n \to R$ , una $f$ si dice convessa se $f(\lambda x+(1-\lambda) y)\leq \lambda f(x) + (1- \lambda)f(y) \forall \lambda \in [0,1], \forall x \in R^n$ 
  Anche: una $f$ si dice convessa se il gradiente è monotono crescente ($\nabla f(x+h) > \nabla f(x) \forall h >0$ ), quindi:
  $f\in C^2$ è convessa se e solo se $H f(x)≥ 0 \forall x$, ma il gradiente in una quadratica è costante, quindi basta calcolarsi gli autovalori.
- __Teorema__: se $f$ è convessa e $\nabla f(\overline x)=0$  allora $\overline x$ è minimo globale, poiché una $f$ convessa non ha minimi locali ne selle.
- __Funzioni coercive continue__:
  una funzione è coerciva se $\lim_{||x|| \to \infty} f(x)=+\infty$ ovvero se va a più infinito in tutte le direzioni.
  Se una funzione è coerciva allora esiste un Minimo Globale (anticoerciva $\to -\infty$ , esiste MG).