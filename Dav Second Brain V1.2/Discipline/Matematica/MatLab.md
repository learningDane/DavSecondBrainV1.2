#uni 
# Linprog
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
>> [x,v]=linprog(c,a,b,aeq,beq,lb,ub)
>> appare soluzione: x=(val ottimo)
```
# Intlinprog
$$\begin{cases} min \ c^T x \\ Ax \leq b \\ A_{eq} = b_{eq} \\ LB \leq x \leq UB \\ x \end{cases}$$
`[x,v]=intlinprog(c,int,a,b,aeq,beq,lb,ub)`
dove `intcom` è la lista degli indici di variabili che devono essere intere.
se per esempio ho 4 variabili e le voglio tutte intere: `int=[1 2 3 4]` oppure `int=[1;2;3;4]` 
# Quadprog
$$\begin{cases} 
\min \frac{1}{2}x^THx+f^Tx \\
A\cdot x≤b \\
Aeq\cdot x=beq \\
lb ≤ x ≤ub
\end{cases}$$
```Matlab
[x,fval,exitflag,output,lambda]=quadprog(h,f,a,b,aeq,beq,lb,ub,x0,options)
``` 
esempio: $f(x)=\frac{1}{2}x^2+y^2 -xy-2x-6y$ 
`h = [1 -1 ;-1 2]` 
`f = [-2 ; -6]` 
`a = [1 1; -1 2; 2 1];`
`b = [2; 2; 3];` 
### exitflag
![[Pasted image 20250107122104.png]]
# Assignment
Restituisce l'assegnamento di costo minimo del TSP, per fare poi l'algoritmo delle toppe. 
```Matlab
assignment([matricespecchiatadeicostiTSP])
```
# fgh_display(f,g,h,x,range,c)
Disegna il dominio e il valore della funzione su questo dominio.
```Matlab
f=x1*2+3*x1*x2 ...
g1= x2+3 ..
..
g4= ..
fgh_display(f, [g1;g2;g3;g4], [], [],[],[])
```
# minsearch
```Matlab
[x,fval]= fminsearch('6*x(1)^2+3*x(2)-9*x(1)*x(2) ecc',x0)
```
![[Pasted image 20250125184419.png]]
# Gradiente proiettato
esegue un passo del gradiente proiettato, inserire bene le matrici vettore, b e x, non possono essere inserite matrici righe.
MINIMIZZA
```Matlab
RicOp.gradienteProiettato(f,a,b,xk,100)
```
# Gomory
esegue un taglio di gomory a partire da una certa X di base.
Vanno inseriti i dettagli della forma duale std, quindi con gli scarti!!!
MI RACCOMANDO I PUNTI E VIRGOLI PER I VETTORI COLONNA.
```Matlab
gomory(c,x,a,b)

%es:
%per trovare gli scarti (vanno messi nella x), vettore s=b-a*x dove b e a NON %hanno i vincoli di positività (sono già nel duale)
c=[43 45 0 0]
x=[32 ; 12 ; s1 ; s2]
a=[123 132 1 0 ; 3 98 0 1]
b=[12 ; 1]
```
# Simplex
esegue un passo del simplesso, MASSIMIZZA ATTENZIONE!!!!!
```Matlab
RicOp.pSimplex(f,A,b,base,iter)

⎰ max f'*x
⎱ A*x<=b
            % EXAMPLE
            % f = [-7 1]
            % A = [
            % 	-3 2;
            % 	-1 -3;
            % 	0 1;
            % 	3 2;
            % 	1 0;
            % 	2 -1; ]
            % b = [4; -6; 5; 22; 6; 16]
            % base = [4 5]
```