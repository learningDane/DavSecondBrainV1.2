#uni 
In questa rappresentazione lo zero viene rappresentato una volta sola. Questa è la rappresentazione usata dai calcolatori, perché basta sommare i valori binari per fare la somma tra due numeri, si può quindi utilizzare la stessa circuiteria dei numeri naturali.
# Come
Se $X$ comincia con $0$ (quindi $MSB = 0$) allora $x$ è positivo e sale al crescere di $X$.
Se $X$ comincia con $1$ (quindi $MSB = 1$) allora $x$ è negativo e sale al crescere di $X$.
$X=00...00 \implies x = 0$ 
$X=01...11 \implies x = 2^{(p-1)}-1$ 
$X=10...00 \implies x = -2^{(p-1)}$ 
$X = 11...11 \implies x = -1$ 
Codifica:
$$X = \begin{cases} x \ \ \ x \geq 0 \\ 2^N+1 \ \ \ x < 0 \end{cases}$$
Decodifica:
$$x = \begin{cases} X \ se \ MSB = 0 \\ - (\overline X + 1) \ se \ MSB = 1 \end{cases}$$
Intervallo di Rappresentabilità:
$$[-2^{(N-1)}, \ (2^{(N-1)}-1)]$$