Per rappresentare i numeri interi CON SEGNO, un bit viene allocato per la rappresentazione del segno, il primo bit, se $0$ allora $n$ è positivo, se $1$ allora $n$ è negativo. Per esempio su $p=4$ bit, il numero $1011 = -3$. In questa rappresentazione lo zero viene rappresentato due volte, una volta negativo ed una positivo, perdendo così un possibile elemento.
Codifica: $$A = (segno_a, \ |a|)$$
Decodifica: $$a = (a_{p-1} == 0 ) \ ? \ |a| \ : \ -|a|$$dove $p_{-1}$ è il segno.
###### Intervallo di rappresentabilità
$$[-(2^{(p-1)}-1), \ (2^{(p-1)}-1)]$$