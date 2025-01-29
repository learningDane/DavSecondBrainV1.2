#uni 
Questa famiglia di problemi appartiene a quella dei [[Problema di Programmazione Lineare (PL)]].
Consiste nell'avere vari oggetti da trasportare, ognuno con un "peso" $p$ (o ingombro) diverso e un valore $v$, ed uno "zaino", con una certa capienza $C$.
Il problema consiste nel trovare la combinazione di oggetti che permette di portare più peso possibile e quindi "saturare" lo zaino.
# Modello bin/intero
$$\begin{cases} \max v^T\cdot x \\ 
\sum_i x_i ≤ C \\ 
x_i \in \{0,1\} \quad oppure \quad x_i \in N\end{cases}$$
- binario: ogni oggetto può essere portato oppure no, una sola volta: $x$ può essere $0,1$ 
- intero: ogni oggetto può essere preso quante volte si vuole: $x$ può essere preso $n$ volte ($n \in N$) 