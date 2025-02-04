x#uni 
Questo è il modello base del [[Problema di Programmazione Matematica a Reti Capacitate (PLRC)]], ma per chiarezza e più facile consultazione, ripeterò qua considerazioni sul modello e altro.
## Modello
Uguale a quello del [[Problema di Programmazione Matematica a Reti non Capacitate (PLRnC)]] solo che aggiungo la variabile $u$ che rappresenta le *capacità di trasporto degli archi* ovvero quanto flusso al massimo può passare sull'arco in questione.
$$\begin{cases} min \quad c^T\cdot x\\ E\cdot x=b \\ 0\leq x_{ij} \leq u_{ij} \\ \end{cases}$$
dove $b$ sono i bilanci ai nodi
oppure $$\begin{cases} 
\min \sum_{(i,j)\in A}c_{ij} \cdot x_{ij} \\
\sum_i x_{ij} - \sum_i x_{ji} = b_j \quad \forall j \quad (1) \\
l_{ij} ≤ x_{ij} ≤ u_{ij} \quad \forall (i,j) \in A \quad (2)
\end{cases}$$
dove $A$ è l'insieme degli archi, $l$ è la capacità minima, $u$ è la capacità massima, $(1)$ sono i vincoli di bilancio ai nodi e $(2)$ sono i vincoli di capacità.
## Flusso di Base
Per definire un base nelle reti capacitate dobbiamo prima modificare leggermente il modello introducendo una variabile $w_{ij}$ che indica la *portata residua* di un arco:
$$\begin{cases} min \quad C^T\cdot x\\ E \ x=b \\ x_{ij}+w_{ij}=u_{ij} \\ x \geq 0 \\ w \geq0 \end{cases}$$ovvero in forma matriciale, duale standard ([[Problema di Programmazione Lineare (PL)#Formato Duale Standard]]): $$\begin{cases} \min \quad
\begin{pmatrix} c \\ 0\end{pmatrix}^T\begin{pmatrix} x \\ w\end{pmatrix} \\
\begin{pmatrix} E^T &I \\0 &I\end{pmatrix}^T\begin{pmatrix} x \\ w\end{pmatrix}=\begin{pmatrix} b \\ u\end{pmatrix} \\ (x,w)≥0
\end{cases}$$
Con $M=\begin{pmatrix} E^T &I \\I &I\end{pmatrix}$ di dimensione $2m\times(n-1+m)$ e rango $n-1+m$.