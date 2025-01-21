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
   $y_B=((A_B)^T)^{-1}$ e $y_N=(0, 0, ..., 0)$ 
2. Determino $W=-A_B^{-1}$ e $W^l$ è una colonna di $W$ determinata dalla $l$-esima riga di $A$, in particolare considero $W^h$, ovvero la colonna di $W$ determinata dalla $h$-esima (con $h$ indice uscente) riga di $A$. 
3. Calcolo per ogni indice $i$ non di base il prodotto scalare $A_iW^h$ e scarto gli indici per cui tale rapporto è negativo
4. Rimpiazzo $h$ con l'indice $i$ non di base che produce il minimo del seguente prodotto: $$r_i=\frac{b_i-A_i\overline x}{A_iW^h}$$
   - se due indici hanno lo stesso $r$ scelgo l'indice minore.
   - se tutti gli indici $i$ portano ad $A_iW^h \leq 0$ allora la soluzione è illimitata.
# Passo del Simplesso Duale

In questo caso partiamo da un [[Problema di Programmazione Lineare (PL)#Formato Duale Standard]], prendiamo un vertice, scopriamo che non è ammissibile nel primale e quindi dobbiamo applicare il Simplesso Duale.
$$(D)=\begin{cases} min\ b^T \cdot y \\ y^TA=c^T \\ y\geq 0 \end{cases}$$ 
1. data una base $B$, trovo la soluzione di base $\overline y_B^T=c^TA^{-1}_B$ e scopriamo che è ammissibile (tutte componenti di $\overline y \geq 0$ )
2. Trovo quindi la complementare $\overline x = A^{-1}_B\cdot b_B$, se trovo che questa $\overline x$ non è ammissibile nel primale (non rispetta tutti i vincoli, quindi $A_N\cdot \overline x\geq b_N$ ) allora sappiamo che la nostra $\overline y$ non è Ottimo (fallisce il Test di Ottimalità del [[Teoria della Dualità#Teorema della Dualità Forte / degli Scarti Complementari]]).
3. Allora $\exists j \in N : A_j\cdot \overline x > b_j$ (esiste almeno una riga violata), sia $k$ la prima riga violata (indice minore - [[Regole Anticiclo di Blend]]), l'indice _entrante_.
4. Calcoliamo $W=-A^{-1}_B$ 
5. Calcoliamo $A_kW^i$ con $i \in B$ e elimino gli indici per i quali viene positivo (se tutti gli indici portano a prodotto positivo il minimo è $=-\infty$ )
6. Costruisco i rapporti $r_i=\frac{-y_i}{A_kW^i}$ con $i\in B$ e prendo l'indice che porta al rapporto minore, e lo chiamo $h$, _indice uscente_ e questo viene rimpiazzato da $k$ (se due $r$ sono uguali prendo l'indice minore).
# Algoritmo verifica Poliedro Vuoto
Questo algoritmo serve per sapere se il poliedro è vuoto o meno:
1. Costruisco il suo [[Duale Ausiliario]] (DA)
	partendo da un problema in duale std 
	   $$(D)=\begin{cases}min\ y^Tb \\A^Ty=c \\ y\geq 0 \end{cases}$$
	costruisco il suo Duale Associato + tante epsilon quante sono le righe del duale moltiplicandole per l'identità $( i )$ 
	
	$$(D_{aux})=\begin{cases}min \sum^n_{i = 0} \epsilon_i \\y^TA+\epsilon^T=c^T \\ y\geq 0 \\ \epsilon \geq0 \\ \end{cases}$$che equivale a prendere il poliedro nella sua forma $A^Ty=c$ ed aggiungere ad ogni riga di $A^Ty$ una $\epsilon$, quindi le $\epsilon$ sono tante quante lo sono le righe di $A^T$ (ovvero numero di colonne di $A$). 
   
2. Cerco il Valore Ottimo del $(D_{aux})$  (VO) tramite il [[#Passo del Simplesso Duale]] (mi aspetto che le due epsilon escano)
3. Controllo il segno di VO:
   - se $VO > 0$ allora poliedro del duale (D) è vuoto
   - se $VO = 0$ allora $(D)$ non è vuoto, e una base ammissibile per $(D)$ si costruisce a partire da una base ottima per $(D_{aux})$.
