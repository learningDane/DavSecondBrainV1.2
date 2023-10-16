#uni 
Di norma per convertire la base di rappresentazione di un numero da base $\alpha$ a base $\beta$ basta convertire prima in base dieci e applicare ora l'algoritmo _DIV&MOD_.
# Casi Particolari
Ci sono poi i casi particolari, per esempio il cambio di base tra potenze di 2: per passare da una base potenza di 2 alla base 2 basta convertire i singoli bit nel numero a potenza $\beta$ nei necessari bit in base 2. Esempio
$(A03)_{sedici} = (1010\ 0000\ 0011)_{due}$ 
Per facilità è possibile usare queste tabelle:
$\beta = 8$:                       $\beta = 16$:
```table
| bas |  8  |   | base |  16  |
|  0  | 000 |   |    0 | 0000 |
|  1  | 001 |   |    1 | 0001 |
|  2  | 010 |   |    2 | 0010 |
|  3  | 011 |   |    3 | 0011 |
|  4  | 100 |   |    4 | 0100 |
|  5  | 101 |   |    5 | 0101 |
|  6  | 110 |   |    6 | 0110 |
|  7  | 111 |   |    7 | 0111 |
-------------   |    8 | 1000 |
				|    9 | 1001 |
				|    A | 1010 |
				|    B | 1011 |
				|    C | 1100 |
				|    D | 1101 |
				|    E | 1110 |
				|    F | 1111 |
```