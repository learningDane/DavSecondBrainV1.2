#uni 26/09/2023
# Bit
L'informazione è astratta e per manipolarla va rappresentata. Nei calcolatori si usano le sequenze di 'bit' (Binary digIT).
1 bit può essere either 0 or 1.
Il bit è l'unità di misura fondamentale dell'informazione.
1 byte = 8 bit
Una stessa sequenza di bit può però rappresentare informazioni differenti (la stessa sequenza potrebbe rappresentare una lettera, un numero o un colore)
L'informazione rappresentabile in _n_ bit è uguale a $2^n$, ovvero tutte le possibili combinazione.

---
I dispositivi di conversione, convergono gli input in bit, e i bit in output.
# Testo
Può essere rappresentato con la codifica ASCII standard (a 7 bit), la codifica ASCII estesa (8 bit) oppure nei browser per esempio con l'UNICODE (16 bit).
# Numeri
I numeri vengono rappresentati in basi diverse, 2,5,8,10,16 ecc.
Ogni numero naturale minore della base in quale viene rappresentato, è associato ad un simbolo e viene detto cifra. Un numero maggiore della base invece viene rappresentato con una sequenza di cifre secondo la rappresentazione posizionale.
___Teorema fondamentale della rappresentazione dei numeri naturali___:
	dato un numero naturale N, esiste una ed una sola sequenza (una per ogni base) che può rappresentarlo ed è definito dalla ___formula della sommatoria___: $$N=\sum^{p-1}_{i=0}a_i \beta^i$$
	dove $a_0$ è detta cifra meno significativa e $a_{p-1}$ è detta invece cifra più significativa.
	Esempi:
		$A03_{16}=10*16²+0*16¹+3*16⁰=2563$
	Sia _mod_ il resto e _div_ il quoziente della divisione intera, l'algoritmo si chiama __Div & Mod__:
		se N=0 porre $a_0 = 0$, $\implies$ __fine__,
		altrimenti: porre $q_0=N$ e poi eseguire la seguente procedura iterativa:
			$q_1 = q_0$ div $\beta$ --- $a_0 = q_0$ mod $\beta$
			$q_2 = q_1$ div $\beta$ --- $a_1 = q_1$ mod $\beta$
			...
			$q_p = q_{p-1}$ div $\beta$ --- $a_{p-1} = q_{p-1}$ mod $\beta$
		fino a quando $q_0 = 0$ 
#### Numeri Naturali rappresentabili con $p$ bit in base $\beta$:
$$intervalli\ di\ rappresentabilità \ con \ p \ bit \ e \ base \ \beta =[0;\beta^p-1]$$
#### Overflow:
In generale ci vogliono $p+1$ bit (chiamato bit di riporto) per rappresentare la somma tra due numeri di $p$ bit. Col prodotto invece si rischia di ottenere un numero non rappresentabile su $p$ bit, si dice che il prodotto ha dato luogo ad un ___overflow___. In c++ i numeri naturali sono organizzati ad anello, se superi il valore massimo riparti dal minimo e viceversa (precisamente, se provi a rappresentare il numero massimo + 1, c++ restituisce 0).
#### Cambio di Base
In generale per effettuare un cambio di base si passa per la rappresentazione in base 10, ma ci sono alcuni casi particolare:
	1. da 8 a 2, ogni cifra in base 8 diventa tre cifre in base 2
	2. da 16 a 2, ogni cifra in base 16 diventa 4 cifre in base 2
#### Somma:
per sommare due numeri binari il metodo più facile e più intuitivo è l'addizione in colonna, quando si ottiene un 2, semplicemente si mette 0 e si riporta 1 alla cifra successiva in ordine di significato. $$ \begin{cases} \ 1010100+ \\ \ 0101111= \\ 10000011 \end{cases} $$
### Numeri interi
##### Prima rappresentazione: in modulo e segno
Per rappresentare i numeri interi CON SEGNO, un bit viene allocato per la rappresentazione del segno, il primo bit, se $0$ allora $n$ è positivo, se $1$ allora $n$ è negativo. Per esempio su $p=4$ bit, il numero $1011 = -3$. In questa rappresentazione lo zero viene rappresentato due volte, una volta negativo ed una positivo, perdendo così un possibile elemento.
Codifica: $$A = (segno_a, \ |a|)$$
Decodifica: $$a = (a_{p-1} == 0 ) \ ? \ |a| \ : \ -|a|$$
###### Intervallo di rappresentabilità
$$[-(2^{(p-1)}-1), \ (2^{(p-1)}-1)]$$
##### Seconda rappresentazione: in complemento a 2 (in complemento di base)
In questa rappresentazione lo zero viene rappresentato una volta sola. Questa è la rappresentazione usata dai calcolatori, perché basta sommare i valori binari per fare la somma tra due numeri, si può quindi utilizzare la stessa circuiteria dei numeri naturali.
Codifica: $$A = (a \geq 0) \ ? \ |a| \ : \ due^p - |a|$$
Decodifica: $$a = (a_{p-1} == 0 ) \ ? \ A \ : \ -(due^p - A)$$Quindi fino a metà dei numeri rappresentabili il numero è positivo e cresce al crescere del valore del binario, dopo il numero col valore assoluto più alto è negativo, e da questo si continua a salire. Esempio: $1111 = -1$, $0110$ = 6, $0001 = 1$, $1000 = -8$.
###### Intervallo di rappresentabilità
$$[-(2^{(p-1)}-1), \ (2^{(p-1)}-1)]$$
##### Terza rappresentazione: con bias
Codifica: $$A = a + (2^{p-1} - 1 )$$
Decodifica: $$a = A - (2^{p - 1} - 1) $$
dove $(2^{p-1} - 1)$ è detto ___Bias___.
Lo zero anche qua viene rappresentato uno volta sola.
###### Intervallo di rappresentabilità 
$$[-(2^{p-1}+1, \ 2^{p-1}], \ ossia \ [-bias, \ bias + 1]$$ 