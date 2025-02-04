#uni 
Questo è un metodo di risoluzione del [[Problema di Programmazione Non Lineare (PNL)]].
# Teorema della Proiezione
La matrice $H$ è la matrice di Proiezione, e $Hy$ è la proiezione di $y$ su $M$.
# Algoritmo per MAX
1. trovo la matrice $M$, ovvero la matrice formata dalle righe dei vincoli attivi di $A$ (dominio di forma $Ax≤b$) in $x^k$.
2. Calcolo la matrice $H$ $$H=\begin{cases} I \quad se \ x^k \ non \ ha \ vincoli \ attivi \\ 
   I-M^T(MM^T)^{-1}M\end{cases}$$
3. calcolo la direzione $$d^k=H\cdot\nabla f(x^k)$$se $d^k=0$ vai al punto 3ª
4. calcolo il passo massimo $$\hat t_k=\begin{cases} \max t\\
   A(x^k+t\cdot d^k)≤b\end{cases}$$
5. calcolo il passo effettivo $$t_k \in argmax_{t\in[0;\hat t_k]}\phi(t)$$con $\phi(t)=f(x^k+t\cdot d^k)$
6. calcolo il nuovo punto $$x^{k+1}=x^k+t_k \cdot d^k$$
3ª. se $d^k=0$:
	1. calcolo $$\lambda=-(MM^T)^{-1}M\cdot \nabla f(x^k)$$
	2. se $\lambda≤0$ allora $x^k$ risolve $LKKT$ 
	3. altrimenti sia $j:\lambda_j=\max_{i\in[0;k]} \lambda_i$ , sappiamo che è $>0$ 
	4. elimino la riga $j$ da $M$ e ritorno al passo ___2___.
# Algoritmo per MIN
oppure applico l'algoritmo per il massimo a $-f$.
1. trovo la matrice $M$, ovvero la matrice formata dalle righe dei vincoli attivi di $A$ (dominio di forma $Ax≤b$) in $x^k$.
2. Calcolo la matrice $H$ $$H=\begin{cases} I \quad se \ x^k \ non \ ha \ vincoli \ attivi \\ 
   I-M^T(MM^T)^{-1}M\end{cases}$$
3. calcolo la direzione $$d^k=H\cdot(-\nabla f(x^k))$$se $d^k=0$ vai al punto 3ª
4. calcolo il passo massimo $$\hat t_k=\begin{cases} \max t\\
   A(x^k+t\cdot d^k)≤b\end{cases}$$
5. calcolo il passo effettivo $$t_k \in argmin_{t\in[0;\hat t_k]}\phi(t)$$con $\phi(t)=f(x^k+t\cdot d^k)$
6. calcolo il nuovo punto $$x^{k+1}=x^k+t_k \cdot d^k$$
3ª. se $d^k=0$:
	1. calcolo $$\lambda=-(MM^T)^{-1}M\cdot \nabla f(x^k)$$
	2. se $\lambda≥0$ allora $x^k$ risolve $LKKT$ 
	3. altrimenti sia $j:\lambda_j=\min_{i\in[0;k]} \lambda_i$ 
	4. elimino la riga $j$ da $M$ e ritorno al passo ___2___.
 