#uni #formulario
- $u \cdot v = ||u|| \cdot ||v|| \cos \theta$ .
- $u \times v = ||u|| \cdot ||v|| \sin \theta$ .
- $u \cdot v = 0$ : ortogonali.
- $u \times v = 0$ : linearmente dipendenti.
- $\begin{pmatrix} a & b \\ c & d \end{pmatrix}^T = \begin{pmatrix} a & c \\ b & d \end{pmatrix}$ è la ___trasposta___ e $(AB)^T=B^T \cdot A^T$ 
- $A$ è simmetrica se $A^T=A$ .
- matrice antisimmetrica: $\begin{pmatrix} 0 & b & c \\ -b & 0 & d \\ -c & -d & 0 \end{pmatrix}$ .
- dimensione di una matrice simmetrica $n\times n$: $dim A= \frac{n(n+1)}{2}$ .
- se $V$ è uno S.V. e β è una sua base, allora $dim(V)=|β|$ = numero degli elementi di una sua qualsiasi base.
- uno S.V. $V$ è dato dato da $V=Span(u_1,u_2,u_3)$ : $u_1,u_2,u_3$ sono ___generatori___ di $V$ e sono linearmente indipendenti, allora $(u_1,u_2,u_3)$ è una base di $V$.
- la base canonica di un S.V. è composta da $n$ matrici nulle meno che un elemento $=1$ .
- matrice identica $I=\begin{pmatrix} 1&0&0 \\ 0&1&0 \\ 0&0&1\end{pmatrix}$ è quindi tale che $AI=IA=A$ .
- prodotto tra matrici $(AB)_{i,j}=\sum_{k=1}^nA_{i,k}\cdot B_{k,j}$ con $A^{m \times n},B^{n \times l} \rightarrow AB^{m,l}$  
- ___Lemma di Eliminazione___ siano $v_1,...,v_{n+1}$ dei vettori in uno S.V. V, se $v_{n+1}$ è combinazione lineare degli altri allora $SPAN(v_1,...,v_{n+1}) = SPAN(v_1,...,v_n)$ 
- ___Formula di Grassmann___ $dim(V+W) + dim(V\cap W)=dim(V)+dim(W)$ 
- ___sistema lineare___ è un sistema composto da tante equazioni quante incognite e si può abbreviare con $Ax=b$ dove $A$ è la matrice dei coefficienti, $x,b$ sono vettori colonna, $x$ delle incognite e $b$ dei termini noti (___forma matriciale___) e il ___sistema lineare omogeneo___ ad esso associato è $Ax=0$ .
- Def ___Applicazione Lineare___: 
	siano $V$ e $W$ S.V. , una app. lin. è una $f : V \to W$ t.c. $f(v_1+v_2) \ f(v_1) + f(v_2)$ e $f(λV)=λf(v)$ 
- $ker(f)$ è l'insieme $ker(f)=\{v \in V : f(v)=0\}$ ed è sottospazio V. di $V$ .
- $Im(f)$ è l'insieme $Im(f)=\{ f(v) : v \in V \}$ ed è sottospazio V. di $V$ .
- se $ker(f) = \{ \emptyset \}$  allora $f$ è iniettiva
- se $v_1,...,v_n$ sono una base di $V$ allora $f(v_1),...,f(v_n)$ sono generatori di $Im(f)$, ma non è detto che siano linearmente indipendenti, lo sono solo se $f$ è iniettiva e quindi se $ker(f)$ è vuoto.
- ___Teo. Rank Nullity___: se $f :V\to W$ è applicazione lineare allora $dim(ker(f))+dim(Im(f))=dim(V)$ , corollario: se $dim(V) > dim(W)$ allora $f$ non è iniettiva, se $dim(V) < dim(W)$ allora $f$ non può essere suriettiva ($Im(f)\neq W$). Se invece $dim(V) = dim(W)$ allora $f$ è biettiva.
- ___Matrice Associata___ ad una applicazione lineare:
  $f:V \to W$ , ${v_1,...,v_n}$ base di $V$ , ${w_1,...,w_m}$ base di $W$ 
  1. calcolo $f(v_1)=c_{1,1}w_1+c_{2,1}w_2+...+c_{m,1}w_m$ e i coefficienti sono la prima colonna della matrice,
  2. calcolo $f(v_2)=c_{1,2}w_1+c_{2,2}w_2+...+c_{m,2}w_m$ ed ottengo seconda colonna
  3. continuo fino a $f(v_n)$ 
- ___Matrice Inversa___ data una $A$ quadrata $m\times m$, $A^{-1}$ è tale che $AA^{-1}=A^{-1}A=Id$ 
	  1. se $m=2$ allora $A^{-1}=\frac{1}{det(A)} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$ con $A=\begin{pmatrix} a&b \\ c&d \end{pmatrix}$ e se $det(A) = 0$ l'inversa non esiste.
	  2. Caso generale $A\begin{pmatrix} a&b&c\ |&1&0&0 \\ d&e&f\ | &0&1&0 \\ g&h&i\ | &0&0&1 \end{pmatrix}$ e lavoro alla jordan fino a che la metà di sinistra non torni identica: $\begin{pmatrix} 1&0&0\ |&j&k&l \\ 0&1&0\ | &m&n&o \\ 0&0&1\ | &p&q&r \end{pmatrix}$ e la parte di destra è $A^{-1}$ .
- ___Matrice Cambio di Base___: $V$ S.V. di dimensione finita, $v_1,...v_n$ prima base di $V$, $w_1,...,w_n$ seconda base di $V$ 
  1. scrivo $v_1$ usando la prima base: $v_1=c_{1,1}w_1+c_{1,2}w_2+...+c_{1,n}w_n$ e i coefficienti $c_{x,y}$ formano la prima colonna della matrice
  2. continuo fino ad $c_n$ 
  oppure
  1. $mat=$ (inversa di matrice base d'arrivo) $\cdot$ (matrice associata rispetto a basi canoniche) $\cdot$ (matrice base di partenza)