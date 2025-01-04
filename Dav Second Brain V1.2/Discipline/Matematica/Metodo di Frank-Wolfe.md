#uni 
$$\begin{cases} \min f(x) \\ Ax \leq b \quad poliedro \ limitato\end{cases}$$
$$x^{k+1}=x^k+t_k \cdot d^k$$
Costruiamo il _Problema Linearizzato_, ovvero la restrizione ad equazione parametrica del segmento:
$$PL(x^k) \quad \begin{cases} \min \nabla f(x^k)x \\ Ax ≤ b \end{cases}$$
Lo risolviamo e chiamiamo la soluzione $y^k$
La direzione diventa: $$d^k=y^k - x^k$$
Il passo diventa: $$t_k \in argmin_{t\in [0,1]}\phi$$
con $\phi=f(x^k+t\cdot d^k)$.
# Note
[[Note Introduttive alla PNL di Analisi II]] 