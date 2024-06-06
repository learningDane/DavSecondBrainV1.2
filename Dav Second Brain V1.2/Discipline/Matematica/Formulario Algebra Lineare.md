#uni #formulario
- $u \cdot v = ||u|| \cdot ||v|| \cos \theta$ .
- $u \times v = ||u|| \cdot ||v|| \sin \theta$ .
- $u \cdot v = 0$ : ortogonali.
- $u \times v = 0$ : linearmente dipendenti.
- $\begin{pmatrix} a & b \\ c & d \end{pmatrix}^T = \begin{pmatrix} a & c \\ b & d \end{pmatrix}$ è la ___trasposta___ e $(AB)^T=B^T \cdot A^T$ 
- $A$ è simmetrica se $A^T=A$ .
- matrice antisimmetrica: $\begin{pmatrix} 0 & b & c \\ -b & 0 & d \\ -c & -d & 0 \end{pmatrix}$ .
- dimensione di una matrice simmetrica $n\times n$: $dim A= \frac{n(n+1)}{2}$ .
- ___Traccia___: (matrici quadrate) somma degli elementi sulla diagonale principale.
- se $V$ è uno S.V. e β è una sua base, allora $dim(V)=|β|$ = numero degli elementi di una sua qualsiasi base.
- uno S.V. $V$ è dato dato da $V=Span(u_1,u_2,u_3)$ : $u_1,u_2,u_3$ sono ___generatori___ di $V$ e sono linearmente indipendenti, allora $(u_1,u_2,u_3)$ è una base di $V$.
- la base canonica di un S.V. è composta da $n$ matrici nulle meno che un elemento $=1$ .
- matrice identica $I=\begin{pmatrix} 1&0&0 \\ 0&1&0 \\ 0&0&1\end{pmatrix}$ è quindi tale che $AI=IA=A$ .
- prodotto tra matrici $(AB)_{i,j}=\sum_{k=1}^nA_{i,k}\cdot B_{k,j}$ con $A^{m \times n},B^{n \times l} \rightarrow AB^{m,l}$  
- ___Lemma di Eliminazione___ siano $v_1,...,v_{n+1}$ dei vettori in uno S.V. V, se $v_{n+1}$ è combinazione lineare degli altri allora $SPAN(v_1,...,v_{n+1}) = SPAN(v_1,...,v_n)$ 
- ___Formula di Grassmann___ $dim(V+W) + dim(V\cap W)=dim(V)+dim(W)$ 
- ___sistema lineare___ è un sistema composto da tante equazioni quante incognite e si può abbreviare con $Ax=b$ dove $A$ è la matrice dei coefficienti, $x,b$ sono vettori colonna, $x$ delle incognite e $b$ dei termini noti (___forma matriciale___) e il ___sistema lineare omogeneo___ ad esso associato è $Ax=0$ .
- Def ___Applicazione Lineare___: 
	siano $V$ e $W$ S.V. , una app. lin. è una $f : V \to W$ t.c. $f(v_1+v_2) = f(v_1) + f(v_2)$ e $f(λV)=λf(v)$ 
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
- ___Matrice Inversa___ data una $A$ quadrata $m\times m$, $A^{-1}$ è tale che $AA^{-1}=A^{-1}A=Id$ ma $det(A)$ DEVE essere DIVERSO da $0$.
	  1. se $m=2$ allora $A^{-1}=\frac{1}{det(A)} \begin{pmatrix} d & -b \\ -c & a \end{pmatrix}$ con $A=\begin{pmatrix} a&b \\ c&d \end{pmatrix}$ e se $det(A) = 0$ l'inversa non esiste.
	  2. Caso generale $A\begin{pmatrix} a&b&c\ |&1&0&0 \\ d&e&f\ | &0&1&0 \\ g&h&i\ | &0&0&1 \end{pmatrix}$ e lavoro alla jordan fino a che la metà di sinistra non torni identica: $\begin{pmatrix} 1&0&0\ |&j&k&l \\ 0&1&0\ | &m&n&o \\ 0&0&1\ | &p&q&r \end{pmatrix}$ e la parte di destra è $A^{-1}$ .
	una matrice si dice ___ortogonale___ se la sua inversa coincide con la sua trasposta.
- ___Matrice Cambio di Base___: $V$ S.V. di dimensione finita, $v_1,...v_n$ prima base di $V$, $w_1,...,w_n$ seconda base di $V$ 
  1. scrivo $v_1$ usando la prima base: $v_1=c_{1,1}w_1+c_{1,2}w_2+...+c_{1,n}w_n$ e i coefficienti $c_{x,y}$ formano la prima colonna della matrice
  2. continuo fino ad $c_n$ 
  oppure
  1. $mat=$ (inversa di matrice base d'arrivo) $\cdot$ (matrice associata rispetto a basi canoniche) $\cdot$ (matrice base di partenza)
- ___Determinante___ 
  1. _Algoritmo di Gauss_: porto in forma a scala usando solo scambi di riga e operazioni ultraortodosse ($R_i = 1 \times R_1 + bR_j$), il $det(A) = (moltiplico \ diagonale)\cdot (-1)^{numero \ di \ scambi \ di \ riga}$
  2. _Sviluppi di Laplace_: scelgo la riga o colonna con più $0$, formata da diciamo $(a,b,c,d)$, $det(A)= a\cdot (det\ resto)-b\cdot (det\ resto)+c\cdot (det\ resto) -d\cdot (det\ resto)$ 
	  Le Proprietà del determinante:
	  1. $det(Id)=1$ 
	  2. $det(AB)=det(A)\cdot det(B)$ 
	  3. $det(A^{-1}) = \frac{1}{det(A)}$
	  4. $det(A^t)=det(A)$ 
	  5. $det(λA)=λ^ndet(A)$ 
	  6. se $A$ mat diagonale: $det(A)=prodotto\ elementi\ diagonale$ (vale anche per mat triangolari)
	  7. Se scambio due righe o colonne tra di loro il $det$ cambia di segno
	  8. Se moltiplico una sola riga o colonna per λ: $det(A)=λdet(A)$ 
- ___Sottomatrice___: le ottengo togliendo ad una matrice righe e/o colonne.
- ___Minore___: determinante delle sottomatrici quadrate
- ___Rango___: massima dimensione di un minore con determinante $\neq 0$ .
  1. oppure massimo numero di righe/colonne linearmente indipendenti = $dim(Span(righe/colonne))$ 
- ___Teorema di Rouché-Capelli___: 
  1. considero un sistema $Ax=b$ 
  2. costruisco la matrice $\hat A=(A |b)$ , aggiungiamo quindi la colonna $b$ 
  Allora
  1. il sistema ammette soluzione solo se $rango(A)=rango(\hat A)$ 
  2. se ha soluzione, allora la soluzione generale dipende da $k$ parametri con $k=n-r$ , $n$ numero di incognite e $r$ rango delle due matrici ed inoltre $k=dim(ker(A))$ .
  I casi quindi sono 2:
	  1. i due ranghi sono uguali $\to$ $b$ è comb lin di $c_1,...,c_n$ 
	  2. $rango(\hat A) = rango(A) + 1$ $\to$ $b$ NON è comb lin di $c_1,...,c_n$ 
- ___Regola di Cramer___: dato un sistema lineare $Ax=b$ con $A=n\times n$, allora ogni incognita è data da: $x_i=\frac{det(A_i)}{det(A)}$ dove $x_i$ è la matrice ottenuta sostituendo la i-esima colonna con la colonna $b$ dei termini noti. 
- ___Traccia___: (di mat quadrata) somma degli elementi sulla diagonale principale.
- ___Autovalori, Autovettori, Autospazi, Diagonalizzabilità___:
  1. un numero λ si dice _Autovalore_ (relativo ad autovettore ecc) di $A$ se esiste un _Autovettore_ $v\neq 0$ t.c. $Av=λv$ .
     per trovare gli autovalori di $A$: $det(A-λ\cdot Id)=0$
     otteniamo un polinomio in λ di grado $n$ se $A$ è una matrice $n\times n$, che chiamiamo ___polinomio caratteristico di $A$___. Le radici (gli autovalori) appartengono a $C$, possono essere quindi complessi o reali, e possono avere molteplicità.
     Il **prodotto** degli autovalori è uguale al termine noto del polinomio caratteristico ed è uguale al determinante della matrice. La **somma** degli autovalori è uguale alla traccia della matrice. Si dice ___molteplicità algebrica di una λ___ ($m_a(λ)$) quante volte λ è radice del pol, caratteristico. Si dice ___molteplicità geometrica di una λ___ ($m_g(λ)$) la dimensione dell'autospazio di λ e quindi $m_g(λ)=dim(ker(A-λ \cdot Id))=n-rango(A_λ\cdot Id_n)$ .
  1. dato un _Autovalore_ λ, si dice _Autospazio_ di λ l'insieme di tutti gli autovettori, compreso lo zero, relativi a λ.
  Quando si diagonalizza una matrice, gli autovalori diventano gli elementi sulla diagonale e gli autovettori diventano le colonne della matrice $M$.
  ___TH di Diagonalizzazione___: una matrice $A$ $n\times n$ è diagonalizzabile se e solo se $m_g(λ)=m_a(λ) \ , \ \forall λ$ quindi se $1\leq m_g(λ) \leq m_a(λ)$ e quindi se tutti gli autovalori hanno $m_g(λ)=1$ .
  Posso dare queste stesse esatte definizioni per applicazioni lineari $f:V\to V$ 
- matrici ___simili___: siano $A$ e $B$ 2 matrici simili, hanno:
  1. stesso polinomio caratteristico
  2. stessi autovalori
  3. stesso determinante
  4. stessa traccia
- ___Teoria delle forme canoniche___:  data $A$, trovare $B$ simile che sia il più semplice possibile, quindi:
  1. diagonalizzazione di lusso: $M$ è anche ortogonale ($A^{-1}=A^t$)
  2. diagonalizzazione su reali o complessi
  3. nessuna diagonalizzazione, forma alla Jordan su reali o complessi.
- ___TH DERIVATO DA Th Fond dell'Algebra___: sia $p(x)$ un polinomio monico di grado $n$ a coefficienti $\in C$. Allora $p(x)=(x-λ_1)(x-λ_2)\cdot ... \cdot (x-λ_n)$ dove quindi $λ_1,...,λ_n$ sono le radici di $p(x)$ .
- se una matrice è triangolare inf o sup, gli autovalori sono gli elementi sulla diagonale.
Geometria:
- angolo tra retta e piano: $\cos β=\frac{|<(a,b,c piano),(direzione retta)>|}{||(a,b,c piano)|| \cdot ||(direz retta)||}$ 
- distanza punto-retta nel piano: $dist(P,retta)=\frac{|ax_0+by_0+c|}{\sqrt{a^2+b^2}}$ 
- distanza punto-piano: $dist(P,piano)=\frac{|ax_0+by_0+cz_0+d|}{\sqrt{a^2+b^2+c^2}}$ 
- proiezione di $u$ su $v$: $proiez(u,v)=\frac{u\cdot v}{||v||^2}V$ 
- piano $H$: $a_1x+a_2y+a_3z=b$ con $(a_1,a_2,a_3)$ perpendicolare ad $H$ 
- $u\cdot v \times w=$ area del parallelogramma
- $u\times v$ perpendicolare a $u,v$ 
- piano param$\to$ cartesiana: $(punto)+t(vec)+s(vet)$ quindi $(a,b,c)=det\begin{pmatrix}i&j&k \\ v&e&c \\ v&e&t \end{pmatrix}$ e per trovare termine noto sostituisco $punto$ 
- se piano passa per origine, termine noto $=0$ 
- per intersecare due piani metto a sistema le cartesiane.
- per intersecare retta (par) e piano (cart) sostituisco le direzioni della retta nel piano e trovo $t$.
Numeri complessi:
- $\overline z = a-bi$ 
- $z^{-1}=\frac{\overline z}{z\overline z}=\frac{a}{a^2+b^2}-\frac{b}{a^2+b^2}i$ 
- $|z|=\sqrt{z}\overline z=\sqrt{a^2+b^2}$ 