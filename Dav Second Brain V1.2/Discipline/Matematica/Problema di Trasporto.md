#uni 
Un problema di Trasporto è un [[Problema di Programmazione Lineare (PL)]], è un sottoinsieme dei [[Problema di Programmazione Matematica a Reti non Capacitate]], quindi gode del [[Teorema di Interezza]].
--- controlla su quaderno
Questo problema consiste nel trovare il minimo costo possibile di trasporto di oggetti, dati diversi stabilimenti di spedizione e diversi stabilimenti di arrivo. Ogni stabilimento di spedizione ha un costo diverso per spedire ad uno stabilimento di arrivo.
I vincoli consistono nella disponibilità degli stabilimenti di spedizione e nella domanda degli stabilimenti di arrivo.
Se l'offerta è maggiore della domanda una soluzione possibile è lo stoccaggio, se invece la domanda è maggiore dell'offerta il [[Poliedro]] è vuoto.
Per la risoluzione si utilizza l'[[Algoritmo del Simplesso]].
# Modello Matematico
$$\begin{cases} min \ C^Tx \\ X_{1,1}+X_{1,2}+X_{1,3}+X_{1,4} = b_1 \\ ... \\ X_{1,1}+X_{2,1}+X_{3,1}+X_{4,1} = b_{n+1} \\ ... \\  X_{i,j} \geq 0 \end{cases}$$quindi $$\begin{cases} min \ c^T x \\ \begin{pmatrix} 1..1|0..0|..|0..0 \\ 0..0|1..1|0..0|..|0..0\\.. \\ 0..0|0..0|..|0..0|1..1\\ 010.00|010.00|..|010..0 \\ 0010..0|0010..0|..|0010..0 \\..\\ 0..01|0..01|..|0..01\\-{1}0..0|0..0|..|0..0\\0{-1}0..0|0..0|..|0..0\\..\\0..0|0..0|..|0..0{-1} \end{pmatrix} \cdot \begin{pmatrix} x_{11}\\x_{12}\\..\\x_{1n}\\x_{21}\\x_{22}\\..\\x_{2n}\\..\\ \\ \\x_{nn} \end{pmatrix}\leq \begin{pmatrix} b_1 \\b_2\\..\\..\\..\\..\\..\\b_{n^2}\\-1\\-1\\..\\-1\end{pmatrix} \end{cases}$$