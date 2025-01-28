#uni 
Associo ad ogni utente/quartiere il numero di clienti/abitanti stimati, con un dato numero di postazioni da poter aprire, devo massimizzare il numero di clienti serviti dalle postazioni.
# Modello
- $I$ = insieme siti candidati ad ospitare il servizio
- $J$ = insieme nodi domanda
- $h_j$ = domanda associata al nodo $j$
- $p$ = numero prefissato di postazioni da aprire
- $d_{ij}$ = distanza tra $i$ e $j$ 
- $D$ = distanza di copertura
- $z_j$ = $1$ se il nodo $j$ è coperto dalla soluzione scelta
- $a_{ij}$ = $1$ se il nodo $j$ è coperto da $i$ 
$$\begin{cases} 
\max \sum_j h_j \cdot z_j \\
\sum_i a_{ij} \cdot x_i ≥ z_i \quad \forall j \quad (1)\\
\sum_i x_i =p \\ 
x_{ij} \in \{0,1\} \\ 
z_j \in \{0,1\}
\end{cases}$$
$(1)$: per coprire il nodo $j$, dobbiamo aprire il servizio in almeno una postazione che lo copra.