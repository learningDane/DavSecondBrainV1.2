#uni 
Codifica: $$A = a + (2^{p-1} - 1 )$$
Decodifica: $$a = A - (2^{p - 1} - 1) $$
dove $(2^{p-1} - 1)$ è detto ___Bias___.
Lo zero anche qua viene rappresentato uno volta sola.
###### Intervallo di rappresentabilità 
$$[-(2^{p-1}+1, \ 2^{p-1}], \ ossia \ [-bias, \ bias + 1]$$
## Altro
i numeri maggiori di 0 iniziano con 1, i numeri minori di 0 iniziano con 0.
Prima di cominciare la codifica bisogna accertarsi che il numero a sia rappresentabile su $p$ bit.