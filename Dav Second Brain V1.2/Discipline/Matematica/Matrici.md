#uni 
# Matrici e Sistemi Lineari
Ogni sistema lineare si può scrivere nella forma: $$Ax=b$$$A_{n \times m}$ è la matrice dei coefficienti.
$x_{m \times 1}$ è il vettore colonna delle incognite.
$b_{n \times 1}$ è il vettore colonna dei termini noti.
Il sistema ha tante equazioni quante sono le righe di $A_{n \times m}$ e i termini noti $b_{n \times 1}$, ($n$).
# Notazione
Indichiamo con $M_{n\times m}$ l'insieme delle matrici con $n$ righe e $m$ colonne.
Se $A \in M_{n\times m}$ allora l'elemento che sta nella riga $i$ e colonna $j$ si indica con $A_{i \times j}$.
Se $n=1$ allora la matrice prende il nome di ___Vettore Riga___.
Se $m=1$ allora la matrice prende il nome di ___Vettore Colonna___.
Se $n=m=1$ allora la ma trice è un solo numero.
# Matrici Speciali
1. Matrice Nulla = matrice con tutti $0$.
2. Matrice Identità $I_{n \times n}$= matrice quadrata con tutti $1$ sulla diagonale principale e $0$ altrove: $\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}$ 
	   tutte le volte che moltiplico una matrice per una matrice identità, ottengo la matrice stessa.
# Operazioni
### Somma / Differenza
$$A+B=\begin{pmatrix} a & b \\ c & d \end{pmatrix}+\begin{pmatrix} e & f \\ g &h \end{pmatrix} = \begin{pmatrix} a+e & b+f \\ c+g & d+h\end{pmatrix}$$
### Moltiplicazione per uno Scalare
$$k \cdot A = k \cdot\begin{pmatrix} a & b \\ c & d \end{pmatrix}= \begin{pmatrix} ka & kb \\ kc & kd \end{pmatrix}$$
### Prodotto di Matrici
Moltiplico le righe della prima per le colonne della seconda
$$A_{n \times m} \cdot B_{m \times k}= M_{n \times k} =\begin{pmatrix} a & b & c \\ d & e & f \end{pmatrix} \cdot \begin{pmatrix} g & h\\ i &j \\ k & l \end{pmatrix} = \begin{pmatrix} ag+bi+ck & ah+bj+cl \\ dg+ei+fk & dh+ej+fl \end{pmatrix}$$ $$(AB)_{i,j}= \sum_{r=1}^{m}A_{i,r}\cdot B_{r,j}$$
###### Proprietà
1. Se le dimensioni sono compatibili il prodotto è distributivo: $(A+B)C=AC+BC$ 
2. Il prodotto si distribuisce rispetto al prodotto per una costante: $(λA)B=λ(AB)$ 
3. Il prodotto è associativo: $A(BC) = (AB)C$ 
4. Il prodotto ___NON___ è commutativo: $AB \neq BA$ e probabilmente $BA$ non si può nemmeno fare.
### Matrice Trasposta
La Matrice Trasposta $A^t$ di $A$ è la matrice che si ottiene scambiando le righe con le colonne. $$(A^t)_{n\times m} = A_{m \times n} = \begin{pmatrix} a & c \\ b & d \end{pmatrix}$$
# Determinante
Il Determinante ($\det A$ o $|A|$) è:
1. una funzione che prende in input $n$ vettori di $R^n$ e restituisce in output un numero. Se il risultato è $0$ i vettori sono ___linearmente dipendenti___.
2. funzione che prende in input una matrice $A_{n \times n}$, quindi quadrata, e restituisce un numero. 
###### Minore Complementare
$$M_{i,j}=\det(A-i-j)$$
###### Complemento Algebrico
$$A_{i,j}=(-1)^{i+j}M_{i,j}$$
##### Definizione Assiomatica (le proprietà)
Le Proprietà:
1. $\det I_{n \times n} = 1$
2. se tra gli $n$ vettori ce ne sono due uguali allora il $\det = 0$
3. $\det (v_1 , v_2 , λv_3 , ... , v_n) = λ\det(v_1 , ... , v_n)$ 
4. le somme escono fuori: $\det(v_1,..., v_i + v_j,...,v_n)= \det(v_1,v_i,...,v_n)+\det(v_1,v_j,...,v_n)$ 
Le proprietà 3 e 4 le posso riassumere dicendo che il determinante è una funzione lineare di ognuno degli $n$ vettori.
5. se scambio due vettori tra di loro il determinante cambia segno.
##### Determinante di una matrice 2x2
$$\det\begin{pmatrix} a&b\\c&d\end{pmatrix}=ad-cb$$
##### Formula Generale per il Determinante
Il Determinante di una generica matrice quadrata è la somma degli elementi di una riga (o di una colonna) moltiplicati per il loro complemento algebrico. Posta la riga $k$ con $1\leq k \leq n$ :$$\det(A_{n \times n})=\sum_{i=1}^na_{k,i}A_{k,i}$$