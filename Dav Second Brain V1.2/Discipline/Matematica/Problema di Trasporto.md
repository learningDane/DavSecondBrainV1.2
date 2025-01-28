#uni 
Un problema di Trasporto è un [[Problema di Programmazione Lineare (PL)]], è un sottoinsieme dei [[Problema di Programmazione Matematica a Reti non Capacitate (PLRnC)]], quindi gode del [[Teorema di Interezza]].
--- controlla su quaderno
Questo problema consiste nel trovare il minimo costo possibile di trasporto di oggetti, dati diversi stabilimenti di spedizione e diversi stabilimenti di arrivo. Ogni stabilimento di spedizione ha un costo diverso per spedire ad uno stabilimento di arrivo.
I vincoli consistono nella disponibilità degli stabilimenti di spedizione e nella domanda degli stabilimenti di arrivo.
Se l'offerta è maggiore della domanda una soluzione possibile è lo stoccaggio, se invece la domanda è maggiore dell'offerta il [[Poliedro]] è vuoto.
Per la risoluzione si utilizza l'[[Algoritmo del Simplesso]].
# Modello Matematico
con: 
- $c_{ij}$ costo da $i$ a $j$
- $o_i$ offerta di $i$
- $d_j$ domanda di $j$ 
$$\begin{cases} \min \sum_i\sum_j c_{ij}\cdot x_{ij} \\
\sum_jx_{ij}=o_i \quad \forall i \\
\sum_ix_{ij}=d_j \quad \forall j \\
x_{ij}≥0 
\end{cases}$$
quindi $$\begin{cases} min \ c^T x \\ \begin{pmatrix} 1..1|0..0|..|0..0 \\ 0..0|1..1|0..0|..|0..0\\.. \\ 0..0|0..0|..|0..0|1..1\\ 010.00|010.00|..|010..0 \\ 0010..0|0010..0|..|0010..0 \\..\\ 0..01|0..01|..|0..01\\-{1}0..0|0..0|..|0..0\\0{-1}0..0|0..0|..|0..0\\..\\0..0|0..0|..|0..0{-1} \end{pmatrix} \cdot \begin{pmatrix} x_{11}\\x_{12}\\..\\x_{1n}\\x_{21}\\x_{22}\\..\\x_{2n}\\..\\ \\ \\x_{nn} \end{pmatrix}\leq \begin{pmatrix} b_1 \\b_2\\..\\..\\..\\..\\..\\b_{n^2}\\-1\\-1\\..\\-1\end{pmatrix} \end{cases}$$