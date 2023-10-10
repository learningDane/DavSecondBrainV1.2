#uni 26/09/2023
Gli insiemi vengono rappresentati con lettere maiuscole, gli oggetti con lettere minuscole. Vengono rappresentati attraverso i [[Diagrammi di Eluero-Venn]].
### Definizione di un insieme
Dato un insieme A
$[a,\ b] = {x \in A \space : \space a\leq x \leq b}$ : insieme chiuso
$]a,\ b[= {x\in A \space : \space a<x<b}$ : insieme aperto (anche scritto $(a, \ b)$)
$[a, \ b) = {x\in A \space : \space a\leq x < b}$ : insieme semiaperto (o semichiuso)
### Massimo, Maggiorante e Estremo Superiore
Definizione: il Massimo $\overline{M}$ di un insieme $A$ per essere tale deve:
1. essere ___Maggiorante___ di $A$: $(\overline{M} \geq a \space , \space \forall \ a \in A)$.
2. appartenere ad $A$.
In un insieme semiaperto o non limitato superiormente il massimo non esiste. Stessa cosa per il  minimo in un insieme semiaperto o non limitato inferiormente.
##### Maggiorante $M$
È Maggiorante di $A$ ogni numero tale che $M\geq a, \ \forall \ a \in A$ .
##### Estremo superiore $sup$ 
È $sup \ A$ il più piccolo tra i Maggioranti di $A$.
Se esiste un massimo $M$ di un insieme $A$, questo è anche limite superiore $sup$.
###### Definizione:
$S\in  R$ 
1. $a\leq S\ \forall \ a\ \in A$  
2. $\forall \ \epsilon > 0 \ ;\ \exists \ x\ \in A \ \ t.c.\ x > S-\epsilon$ 
###### Teorema di esistenza dell'estremo superiore
Se un insieme $A$ è limitato superiormente allora il limite superiore $sup$ esiste ed è finito.
##### Dimostrazione di "Se il massimo esiste è unico":
$M_1<M_2$
$M_1 \geq a \ \forall \ a \in A$ e $M_1 \in A$ 
$M_2 \geq a \ \forall \ a \in A$ e $M_2 \in A$ 
Ma se $M_1$ deve essere più grande di tutti gli elementi di $A$ deve essere anche più grande di $M_2$ , ma la stessa cosa vale se avessimo posto $M_1 > M_2$ , e dobbiamo avere una di queste due condizioni affinché $M_1 \neq M_2$ , allora è impossibile, $M_1$ ed $M_2$ coincidono per forza.

### Le operazioni
Le operazioni con gli insiemi sono le seguenti:
##### Unione
indicato con il simbolo: $$\land$$
$$A\land B=tutti\ gli\ oggetti\ di\ A\ e\ di\ B$$

##### Intersezione
indicata con il simbolo: $$\lor$$
$$A\lor B = tutti\ gli\ oggetti\ sia\ in\ A\ che\ in\ B$$
##### Prodotto Cartesiano
Indicato con il simbolo: $$\times$$$$A \times B = \{(a,b) \ t.c.\ a \in A, b \in B\}$$
Il prodotto cartesiano tra due insiemi è un insieme composto tra coppie ordinate di argomenti contenuti uno in A ed uno in B.

##### Sottoinsieme
Indicato con il simbolo: $$\subseteq$$$$A\subseteq B\implies \forall x \in A, x \in B $$
	Dire che A è un sottoinsieme di B vuol dire che ogni elemento di A è anche un elemento di B.

### Diversi tipi di insiemi:
##### N: i numeri naturali
	numeri interi positivi
##### Z: i numeri interi
	numeri interi positivi o negativi
##### Q: i numeri razionali
	numeri decimali finiti
##### R: i numeri reali
	I numeri decimali non finiti
È un insieme non numerabile perché tra due numeri ve ne sono infiniti e non esiste una  funzione bigettiva tale che $f: N \to R$.

$[x]=\{ max\ k,\ con\ k \in Z;\ k\leq x \}$ ovvero la parte intera di $x$, approssimazione di $x$ per difetto.
$\{x \} = x - [x]$ ovvero la parte decimale di $x$.
###### Troncatura
Per comodità si può rappresentare un numero $r\in R$ con $n$ cifre decimali:
$[r]_n$: troncatura del numero $r$ con $n$ cifre decimali
### Cardinalità 
Indicata con il simbolo # :
$$\#(A)=n \in N \implies \exists \ f\ bigettiva\ t.c.\ f: A \to \{ 1,\ 2,\ 3,\ ...\ ,\ n\}$$ A è finito se: $\exists \ n \in N\ t.c.\ \#A=n$ 