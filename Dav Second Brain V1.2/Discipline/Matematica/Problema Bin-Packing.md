#uni 
Questo è un [[Problema di Programmazione Lineare Intera (PLI)]].
Ho un numero di oggetti di cui conosco il peso e ho un indeterminato numero di contenitori (Bin) di cui conosco la capienza.
Trovare l'assegnamento che porti all'utilizzo del minor numero possibile di contenitori
# Modello
$n$ oggetti, $m$ contenitori
Variabili:
- $x_{ij}=(j \ è \ dentro \ i) \quad ? \quad 1 : 0$  
- $y_i=(i \ è \ usato)\quad ? \quad 1:0$ 
$$\begin{cases} \min \sum_{i=1}^my_i
\\ \sum_{i=1}^mx_{ij}=1 \quad \quad \forall j\in[i;n]
\\ \sum_{j=1}^np_jx_{ij}\leq Cy_i \quad \forall i\in[i;m]
\\ x_{ij}\in \{ 0,1\}
\\ y_i\in \{ 0,1\}
\end{cases}$$
$A$ è di dimensioni: $(n+m)\times(n\cdot m+m)$ 
# Risoluzione
Essendo questo un problema di PLI, troviamo una $V_S$, una $V_I$, e applichiamo un algoritmo di riduzione del gap.
Il più adatto, per la natura binaria del problema, è l'[[Algoritmo di Riduzione del Gap Branch and Bound]].
Abbiamo bisogno di una approssimazione del numero di bin necessari, meno ne mettiamo nel modello e più velocizziamo. Alla peggio dovremo utilizzare $n$ contenitori (numero di oggetti).
### Algoritmi per la Vs
Per trovare la soluzione ottimale abbiamo 3 algoritmi, in ordine di accuratezza:
_decreasing = ordinare oggetti per peso decrescente_ 
1. ___next-fit-decreasing___:
   Il primo contenitore é il contenitore corrente.
   Se possibile, assegna un oggetto al contenitore corrente;
   altrimenti assegnalo ad un nuovo contenitore, che diventa quello corrente.
2. ___first-fit-decreasing___:
   Assegna ogni oggetto al primo contenitore usato che puó contenerlo.
   Se nessuno di essi puó contenerlo, assegna l’oggetto ad un nuovo contenitore.
3. ___best-fit-decreasing___:
   ordino i bin per capienza rimanente decrescente
   prendo un oggetto, lo metto nel bin con minore capienza rimanente, se non entra, in quello dopo
   ripeto: riordino i bin, metto un oggetto, riordino ecc
### Vi
La valutazione inferiore di questo problema è particolarmente semplice, è l'approssimazione per eccesso del valore associato alla soluzione del rilassato continuo del problema: $$V_I=\left \lceil \frac{\sum_{j=1}^np_j}{C}\right\rceil$$
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