#uni 
Ho un numero di oggetti di cui conosco il peso e ho un indeterminato numero di contenitori (Bin) di cui conosco la capienza.
# Algoritmi
Per trovare la soluzione ottimale abbiamo 3 algoritmi, in ordine di accuratezza:
1. ___next-fit-decreasing___:
	
2. ___first-fit-decreasing___:
3. ___best-fit-decreasing___:
# Comando Matlab
Bisogna usare [[MatLab#Intlinprog]], la difficoltà è scrivere $b$ poiché è in funzione di un'altra variabile, le $y$.
Semplicemente porto le b, che sono $Py_i$, a sinistra dell'uguale, come fossero una ulteriore $x_{ij}$ 
```matlab
# Nvariabili = Noggetti x Ncontenitori + Ncontenitori = Ncontenitori(Noggetti + 1)
# Aeq è Noggetti x Nvariabili, esempio 6x28
Aeq=[1000001000001000001000000000 ; 0100000100000100000100000000 ; 0010000010000010000010000000 ; ecc]
beq=[1 ; 1 ; 1 ; 1 ; 1 ; 1]
b=[0 ; 0 ; 0 ; 0]
A=[1riga ; 2riga ; 000000 000000 p1p2p3p4p5p6 000000 00 -P 0]
```