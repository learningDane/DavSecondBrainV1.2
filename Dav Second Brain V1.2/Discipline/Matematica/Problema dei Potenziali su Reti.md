#uni 
Il problema dei potenziali su rete è il Duale della forma matriciale duale standard del [[Problema del Flusso di Costo Minimo]]: $$(flusso \ minimo)\begin{cases} \min \quad
\begin{pmatrix} c \\ 0\end{pmatrix}^T\begin{pmatrix} x \\ w\end{pmatrix} \\
\begin{pmatrix} E^T &I \\0 &I\end{pmatrix}^T\begin{pmatrix} x \\ w\end{pmatrix}=\begin{pmatrix} b \\ u\end{pmatrix} \\ (x,w)≥0
\end{cases}$$
# Modello
$$\begin{cases} 
\max \quad (b  \quad u)^T\begin{pmatrix} \pi \\ \mu\end{pmatrix}  \\ 
\begin{pmatrix} E^T &I \\0 &I\end{pmatrix}\begin{pmatrix} \pi \\ \mu\end{pmatrix}≤\begin{pmatrix} c \\ 0\end{pmatrix} 
\end{cases}$$
che equivale a:
$$\begin{cases}
\max \quad \pi^Tb+\mu^Tu \\
\pi^TE+\mu^T≤c^T \\ 
\mu ≤0
\end{cases}$$
# Ammissibilità e Degenere
Il potenziale di base $\overline \pi$ è ammissibile se e solo se i costi ridotti ($c^\pi_{ij}=\pi_i +c_{ij}-\pi_j$)degli archi in $L$ sono non negativi ed i costi ridotti degli archi in $U$ sono non positivi.
