#uni 
Questo è un [[Problema di Programmazione Matematica a Reti]] con la differenza che gli archi sono capacitati, ovvero hanno una capacità massima.
## Modello
Uguale a quello del [[Problema di Programmazione Matematica a Reti]] solo che aggiungo la variabile u che rappresenta le *capacità di trasporto degli archi* ovvero quanto flusso al massimo può passare sull'arco in questione
$$\begin{cases} min \quad C^T*x\\ E*x=b \\ 0\leq x_{ij} \leq u_{ij} \\ \end{cases}$$ 
## Flusso di Base
Per definire un base nelle reti capacitate dobbiamo prima modificare leggermente il modello introducendo una variabile $w_{ij}$ che ci indicherà sostanzialmente la *portata residua* di un arco :
$$\begin{cases} min \quad C^T*x\\ E*x=b \\ x_{ij}+w_{ij}=u_{ij} \\ x \geq 0 \\ w \geq0 \end{cases}$$
Questo modello mi genera un matrice di $rango = m+n-1$, per generare una base dobbiamo *esapartizionare* la matrice in $T,L,U \quad e\quad T^I, L^I, U^I$ :
- in T archi di "base" (stessa denominazione del [[Problema di Programmazione Matematica a Reti]])
- in L gli archi *vuoti* ( nella soluzione tutti gli archi di  $x_L$ avranno flusso 0 quindi $w_{L^I}$ pari alla portata massima ($u_{ij}$) )
- in U gli archi *saturi* ( nella soluzione tutti gli archi di $x_U$ avranno flusso pari a $u_{ij}$ quindi $w_{U^I}$ pari a 0)

La prima *tripartizione* farà riferimento alle x quindi avremo $x_T,x_L,x_U$; la seconda invece farà riferimento alle w quindi avremo $w_{T^I},w_{L^I},w_{U^I}$.
Secondo il [[Teorema della Caratterizzazione delle Basi]] scegliendo l'insiemi di archi $T,U,T^I,L^I$ ottengo una base (**vale anche il contrario**).
La soluzione di base quindi avrà questa forma ( in ordine: a sinistra $x_T,x_L,x_U$; a destra$w_{T^I},w_{L^I},w_{U^I}$ ) :$$(x,w) = (x_T, 0, u_U \quad| \quad u_T-x_T, u_L,0)$$
### Come si fa una tripartizione?
1. metto in $T$ :
	- per primi gli archi *non vuoti* e *non saturi*
	- poi gli archi *saturi* o *vuoti* (in ordine lessico-grafico) fino ad avere $[T]=n-1$ 
2. metto in $U$ tutti gli archi *saturi* rimanenti
3. metto in $L$ tutti gli archi *vuoti* rimanenti
## Ammissibilità
Devo controllare che $\begin{cases} x_T \geq 0 \\ u_T-x_T \geq 0 \end{cases}$  quindi in sostanza $0 \leq x_T \leq u_T$ 
## Potenziali (Primale Associato)