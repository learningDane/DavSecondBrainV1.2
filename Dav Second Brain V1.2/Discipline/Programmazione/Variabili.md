#uni 27/09/2023
# Tipo di variabile
Il tipo di variabile definisce le dimensioni della variabile, ovvero il numero di celle, quali valori può assumere e quali sono le operazioni che ci si può eseguire.
![[Memoria RAM#Tipi]]
# Numeri interi
##### In memoria
4 celle (32 bit - 4 byte)
##### Operazioni:
$+\ -\ *\ /\ \%$ 
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
# Numeri Reali
##### Operazioni:
$+\ -\ *\ /$
##### Virgola Fissa
Si usa un numero di bit fisso per la parte intera ed un numero di bit fisso per la parte frazionaria. Sia $r$ un numero reale da rappresentare, indiciamo con $I(r)$ la parte intera e con $F(r)$ la parte razionale. Siano $p$ i bit per rappresentare $r$, $f$ quelli per la parte frazionaria e $(p-f)$ i bit per la parte intera: $$R=\sum^{p-f-1}_{i=-f} a_i\beta^{1}=a_{p-f-1}\beta^{p-f-1}+...+a_0\beta⁰+a_{-1}\beta^{-1}+...+a_{-f}\beta^{-f}$$
Dove $a_{-1}\beta^{-1}+...+a_{-f}\beta^{-f}$ è la parte frazionaria. Per ricavarla si usa il seguente procedimento, chiamato __Procedura _parte frazionaria-parte intera___:
$f_0=F(r)$
Se $f_0 \neq 0$ :
$f_{-1} = F(f_0 \cdot 2)$    $a_{-1} = I(f_0 \cdot 2)$
$f_{-2} = F(f_{-1})$  ecc...
fino a che $f_{-j} = 0$ oppure si è raggiunta la precisione desiderata.
È possibile incontrare parti frazionarie che hanno bisogno di un numero infinito di cifre per essere rappresentate, in questo caso c'è una parte periodica che si ripete all'infinito e va operato un troncamento alla cifra necessaria per la precisione desiderata.
##### Virgola Mobile
È data da una mantissa, la lunghezza della quale determina la precisione, e da una base con esponente, che determina l'intervallo di rappresentabilità: $r=\pm m \cdot \beta^e$, con $m$ mantissa, $beta$ e $e$ esponente.
Numeri reali _normalizzati_:
1. una mantissa con parte intera costituita da un solo bit di valore $1$
2. rappresentazione tripla costituita da tre numeri naturali
$r \iff R = \langle s, E, F \rangle$ dove $s$ codifica il segno, $F$ codifica la parte frazionaria della mantissa su $G$ bit e $E$ codifica l'esponente su $K$ bit. $$r = (s == 0) ? [+1+f) \cdot due^e)] : [-(1+f) \cdot due^e)]$$
$f= \frac{F}{2^G}$ è la parte frazionaria della mantissa $(m=1 + f = 1+ \frac{F}{2^G})$ 
$e = +E-(2^{k-1} -1 )$ è l'esponente rappresentato dal numero naturale $E$ (rappresentazione con Bias).
Una conseguenza dell'_uno implicito_ è l'impossibilità di rappresentare lo zero!
1. __Half Precision__: massimo modulo: $11111,1111111111_{due} = 2^{17}$ 
   minimo modulo: $00000,0000000000 = 2^{-15}$ 
2. __Single Precision__: massimo modulo: $2^{+129}$
   minimo modulo: $2^{-127}$ 
# Booleano
### In memoria
1 bit $0$ oppure $1$, rispettivamente per falso e vero.
### Operazioni
1. $||$ OR logico o disgiunzione
2. $\& \&$ AND logico o congiunzione
3. $!$ NOT logico o negazione
# Carattere
### In memoria
Generalmente un byte. Il valore può essere espresso in decimale, ottale (`\cifraottale`) ed esadecimale (`\xcifraesadecimale`).
### Operazioni
Sono possibili tutte le operazioni degli interi, che agiscono sulla codifica dei caratteri.
### Valori
1. letterale carattere: un carattere racchiuso fra apici $'a'$
2. caratteri di controllo: combinazioni speciali che iniziano con un backslash:
	1. `\n` : nuova riga
	2. `\t` tabulazione orizzontale
	3. `\r` ritorno carrello
	4. `\\` backslash
	5. `\'` apice
	7. `\"` virgolette
### Nota
le sequenze di escape e le rappresentazioni ottale e esadecimale di un carattere vanno racchiuse fra apici '' quando rappresentano un _letterale carattere_.