#uni 
A partire da un problema in [[Problema di Programmazione Lineare (PL)#Formato Duale Standard]]: 
$$(D)=\begin{cases}min\ y^Tb \\A^Ty=c \\ y\geq 0 \end{cases}$$
costruisco il suo Duale Associato + tante epsilon quante sono le righe del duale moltiplicandole per l'identità $( i )$ $$(D_{aux})=\begin{cases}min \sum^n_{i = 0} \epsilon_i \\y^TA+\epsilon^T=c^T \\ y\geq 0 \\ \epsilon \geq0 \\ \end{cases}$$
# Utilizzo del Duale Ausiliario
$$\begin{matrix}
(D)
\begin{cases} 
\min \quad b^Ty \\
A^Ty=c \\ 
y≥0
\end{cases} 

\quad \to \quad 
(D_{aux})
\begin{cases}
\min \sum_i \epsilon_i \\ 
A^T y + \epsilon = c \\ 
y ≥ 0 \\ 
\epsilon ≥ 0 \\
 \end{cases}
\\ 
soluzione \ di \ base \ con \ B=\{ 0 \ 1 \ ... \ 2n \}: \\
 \quad \begin{pmatrix} y \\ \epsilon \end{pmatrix} =
\begin{matrix}
\begin{cases}     y_1 \\ y_2 \\ ... \\ y_n    \end{cases} \\
\begin{cases}   \epsilon_1 \\ \epsilon_2 \\ ... \\ \epsilon_n  \end{cases}
\end{matrix}
\begin{pmatrix} 0\\0\\...\\0\\c_1\\c_2\\...\\c_n \end{pmatrix}
\end{matrix}$$
Il duale ausiliario (D_aux) viene utilizzato per trovare una base ammissibile in un problema in forma duale std (D).
Una volta costruito il duale ausiliario, la base costituita dai primi 2n vincoli (con n dimensione del vettore y) è una base la cui soluzione di base è ammissibile (soluzione: tutte le y a 0 e tutte le epsilon uguali alle relative c). Da questa soluzione di base possiamo applicare il simplesso Duale fino all'ottimo.

- Se il valore ottimo di (D_aux) è maggiore di zero allora (D) non ha soluzioni ammissibili.
- Se il valore ottimo di (D_aux) è uguale a zero, allora (D) ha almeno una soluzione di base ammissibile, che si può costruire a partire da una base ottima per (D_aux).

ATTENZIONE: prima di costruire (D_aux) è necessario fare in modo che tutte le c in (D) siano ≥ 0, semplicemente cambiando semmai di segno alle equazioni.
Altrimenti la soluzione di base di (D_aux) indicata dai primi 2n indici non sarebbe ammissibile.