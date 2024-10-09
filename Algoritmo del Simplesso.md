#uni 
Questo è l'algoritmo pre trovare la soluzione ottima di un [[Problema di Programmazione Lineare (PL)]], facendo uso della [[Teoria della Dualità]].
Dato un problema PL in primale standard: $(P)\begin{cases} max \  c^T\cdot x \\ Ax \leq b\end{cases}$
Ne trovo il duale complementare $(P)\begin{cases} min \ b^T \cdot y \\ A^T y = c \\ \forall k, \ y_k \geq 0\end{cases}$ 
Parto da una soluzione di base ammissibile del primale, ovvero un [[Vertice]].
Data la sua base $B$, ne calcolo la soluzione nel duale, secondo le modalità descritte nella [[Teoria della Dualità]], se la soluzione duale è ammissibile (tutte $y_B \geq 0$) questo vertice è soluzione, altrimenti devo fare un [[#Passo del Simplesso]].
Se parto da una base con soluzione non ammissibile nel primale, che è invece soluzione ammissibile nel duale, devo fare un [[#Passo del Simplesso Duale]].
# Passo del Simplesso
1. Determino l'indice uscente $h$: il minore indice (di base) la cui $y_h \leq 0$.
   si prende sempre il minore per la Regola Anticiclo di Blend.
2. Determino $W=-A_B^{-1}$ e $W^l$ è una colonna di $W$ determinata dalla $l$-esima riga di $A$, in particolare considero $W^h$, ovvero la colonna di $W$ determinata dalla $h$-esima (con $h$ indice uscente) riga di $A$.
3. Calcolo per ogni indice $i$ non di base il prodotto scalare $A_iW^h$ e scarto gli indici per cui tale rapporto è negativo
4. Rimpiazzo $h$ con l'indice $i$ non di base che produce il minimo del seguente prodotto: $$r_i=\frac{b_i-A_i\overline x}{A_iW^h}$$
   - se due indici hanno lo stesso $r$ scelgo l'indice minore.
   - se tutti gli indici $i$ portano ad $A_iW^h \leq 0$ allora la soluzione è illimitata.
# Passo del Simplesso Duale
In questo caso partiamo da un [[Problema di Programmazione Lineare (PL)#Formato Duale Standard]], prendiamo un vertice, scopriamo che non è ammissibile nel primale e quindi dobbiamo applicare il Simplesso Duale.
$$(D)=\begin{cases} min yb \\ yA=c \\ y\geq 0 \end{cases}$$
1. data una base $B$, trovo la soluzione di base $\overline y=(cA^{-1}_B,0)$ e scopriamo che è ammissibile (tutte componenti di $\overline y \geq 0$ )
2. Trovo quindi la complementare $\overline x = A^{-1}_B\cdot b_B$, se trovo che questa $\overline x$ non è ammissibile nella primale (non rispetta tutti i vincoli, quindi $A_N(A^{-1}b_B)\geq b_N$ ) allora sappiamo che la nostra $\overline y$ non è Ottimo (fallisce il Test di Ottimalità del [[Teoria della Dualità#Teorema della Dualità Forte / degli Scarti Complementari]]).
3. Altrimenti $\exists j \in N : A_j(A^{-1}_Bb_B) > b_j$ (esiste almeno una riga violata), sia $k$ la prima riga violata (indice minore - regola anticiclo di blend), l'indice _entrante_.
4. Calcoliamo $W=-A^{-1}_B$ 
5. Calcoliamo $A_kW^i$ e elimino gli indici per i quali viene positivo (se tutti gli indici portano a prodotto positivo il minimo è $=-\infty$ )
6. Costruisco i rapporti $r_i=\frac{-\overline y}{A_kW^i}$ e prendo l'indice che porta al rapporto minore, e lo chiamo $h$ e questo rimpiazza $k$ (se due $r$ sono uguali prendo l'indice minore).