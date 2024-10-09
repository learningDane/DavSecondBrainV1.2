#uni 
Per risolvere un [[Problema di Programmazione Lineare (PL)]], [[MatLab]] offre ___linprog___.
Risolve i problemi nel seguente forma: $$\begin{cases} min \ c^T x \\ Ax \leq b \\ A_{eq} = b_{eq} \\ LB \leq x \leq UB \end{cases}$$
dove $LB$ e $UB$ sono i vettori dei lower e upper bound.
Questa forma è una forma standard, quindi ogni problema PL può essere portato in questa forma
# Esempio
$$\begin{cases} max \ x_1+x_2 \\ 3x_1+5x_2\geq 7 \\ 2x_1+6x_2-9x_3 = 9 \\ x_1, x_2, x_3 \geq 0 \\ x_2 \leq 8\end{cases}$$
Digitare: (ordine e nomi alle matrici non contano, conta solo ordine nel comando linprog(...))
```matlab
>> c=[-1 0 -1]
>> UB=[ ; 8 ; ]
>> LB=[0;0;0]
>> beq=[9]
>> b=[-7 ; 3]
>> A=[-3 -5 0 ; 1 0 1]
>> Aeq=[2 6 -8]
>> [x,v]=linprog(c,A,b,Aeq,beq,LB,UB)
>> appare soluzione: x=(val ottimo)
```
