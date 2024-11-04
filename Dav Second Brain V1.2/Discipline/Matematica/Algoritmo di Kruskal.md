#uni 
Questo algoritmo è utilizzato per costruire un [[k-Albero]].
# Algoritmo
Su $n$ nodi
1. Isolo il nodo $k$
2. tra i nodi $n-k$  disegno il collegamento di costo minimo
3. tra i nodi $n-k$ disegno il prossimo collegamento di costo minimo
4. continuo fino ad ottenere $n-1$ collegamenti
5. Unisco $k$ al resto con il suo collegamento di costo minimo
6. Unisco $k$ al resto con il suo prossimo collegamento di costo minimo