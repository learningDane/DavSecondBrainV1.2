#uni 
Un vettore è un segmento orientato, cioè un segmento $AB$ i cui estremi sono considerati in un certo ordine. Un vettore è caratterizzato dalle seguenti proprietà:
- ___direzione___ = la direzione della retta passante per i due punti.
- ___verso___ = il verso che sulla retta da $A$ porta a $B$ o da $B$ a $A$ .
- ___modulo___ = detto anche intensità o lunghezza, e definito come la misura del segmento $AB$ rispetto ad una fissata unità di misura.

# Operazioni tra vettori
- ___Somma___ (differenza)
	siano $x$ e $y$ in $R^n$, diciamo $\vec x = (x_1, ..., x_n)$ e $\vec y = (y_1,...,y_n)$ allora $$\vec x+\vec y = (x_1+y_1, x_2 + y_2, ..., x_n + y_n)$$
- ___Prodotto per uno scalare___
	$\vec x=(x_1,...,x_n)$  e  $a\in R$ $$a\vec x = (ax_1, ..., ax_n)$$
- ___Prodotto scalare___ Canonico
	$\vec x=(x_1,...,x_n)$  e  $\vec y = (y_1,....y_n)$ $$\vec x \bullet \vec y\ \  oppure<\vec x,\vec y> \ =||\vec x||\cdot ||\vec y|| \cdot cos \gamma = \ x_1 y_1 + x_2 y_2 +\ ...\ + x_n y_n$$
	Prorietà:
	- $<\vec x , \vec y + \vec z> \  =  \ < \vec x, \vec y> + < \vec x , \vec z >$
	- $< a \cdot \vec x , \vec y > = a\  \cdot < \vec x, \vec y>$   
- ___Norma___ 
	Dato un vettore $\vec x=(x_1,...,x_n)$  e  $a\in R$  la sua Norma è $$|| \vec x|| = \sqrt {x_1 ^2 + x_2^2 +\ ...\ + x_n ^2}$$ ossia $$||\vec x || = \sqrt{<\vec x,\ \vec x>}$$ Ed è la lunghezza (modulo) del vettore.
- ___Distanza tra due vettori___
	Dati $x$ e $y$ in $R^n$, diciamo $\vec x = (x_1, ..., x_n)$ e $\vec y = (y_1,...,y_n)$ $$dist(\vec x, \ \vec y) = || \vec x - \vec y  || = \sqrt{(x_1 - y_1)^2 +\ ...\ + (x_n + y_n)^2}$$
- ___Prodotto Vettoriale___ 
	Il modulo del prodotto vettoriale è l'area del parallelogramma definito da $\vec{v}$ e $\vec{w}$.
	Il modulo del vettore risultante:$$\vec{v} \times \vec{w} \ oppure \ \vec{v} \land \vec{w}= ||\vec{v}|| \cdot || \vec{w}|| \sin(θ)$$La direzione del vettore risultante è la direzione ___ortogonale___ al piano che contiene i vettori $\vec{v}$ e $\vec{w}$.
	Il verso si ricava con la regola della mano destra.
	Proprietà:
	- Proprietà distributiva
	- Proprietà di Bilinearità 
	- Proprietà Anticommutativa: $\vec{v} \times \vec{w} = -\vec{w} \times \vec{v}$ 
	Formula per vettori $\in R^3$: $\vec{v} \times \vec{w} = (v_2w_3-v_3w_2,v_3w_1-v_1w_3,v_1w_2 - v_2w_1)$ 
