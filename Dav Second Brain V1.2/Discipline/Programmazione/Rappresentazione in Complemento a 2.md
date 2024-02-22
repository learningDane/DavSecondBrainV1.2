#uni 
In questa rappresentazione lo zero viene rappresentato una volta sola. Questa è la rappresentazione usata dai calcolatori, perché basta sommare i valori binari per fare la somma tra due numeri, si può quindi utilizzare la stessa circuiteria dei numeri naturali.
Codifica: $$A = (a \geq 0) \ ? \ |a| \ : \ due^p - |a|$$
Decodifica: $$a = (a_{p-1} == 0 ) \ ? \ A \ : \ -(due^p - A)$$Quindi fino a metà dei numeri rappresentabili il numero è positivo e cresce al crescere del valore del binario, dopo il numero col valore assoluto più alto è negativo, e da questo si continua a salire. Esempio: $1111 = -1$, $0110$ = 6, $0001 = 1$, $1000 = -8$.
###### Intervallo di rappresentabilità
$$[-2^{(p-1)}, \ (2^{(p-1)}-1)]$$