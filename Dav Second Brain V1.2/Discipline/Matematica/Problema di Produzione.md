#uni 
Una ditta produce laminato di Tipo A e laminato di Tipo B (il prodotto).
Ogni laminato passa per i reparti MateriePrime, Taglio, Finiture Tipo A, Finiture Tipo B (in base a se è tipo A o B).
Il guadagno è 8,4 per il Tipo A e 11,2 per il tipo B.
I vincoli sono:
Tipo A deve stare 30h in MateriePrime, 10h in Tagli, 20h in Finiture A.
Tipo B deve stare 20h in MateriePrime, 20h in Tagli, 30h in Finiture B.
Materie prime può fare massimo 120h, Tagli 80h, Finiture A 62h, Finiture B 105h.
Creiamo la funzione obiettivo:

|              | A   | B    | tot  |
| ------------ | --- | ---- | ---- |
| Guadagno     | 8,4 | 11,2 |      |
| MateriePrime | 30h | 20h  | 120h |
| Tagli        | 10h | 20h  | 80h  |
| Finiture A   | 20h | -    | 62h  |
| Finiture B   | -   | 30h  | 105h |
Applichiamo il modello matematico di Programmazione Lineare:
Questo è il nostro $Ax \leq b$: 
$$\begin{pmatrix} 30 \ 20\\ 10 \ 20\\ 10 \ 0\\ 0 \ 30\\ -1 \ 0 \\ 0 \ -1 \end{pmatrix} \cdot \begin{pmatrix}x_A \\ x_B \end{pmatrix} \leq \begin{pmatrix} 120 \\ 80\\ 62\\ 105\\ 0\\ 0\end{pmatrix}$$
troviamo questi l'intersezione di questi semipiani ed abbiamo trovato la [[Regione Ammissibile]].
Adesso non resta che trovare il massimo della funzione $max \ c^T \cdot x$, che in questo caso è: $max \ 8,4\cdot x_A + 11,2 \cdot x_B$ 