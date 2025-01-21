#uni 
A partire da un problema in [[Problema di Programmazione Lineare (PL)#Formato Duale Standard]]: 
$$(D)=\begin{cases}min\ y^Tb \\A^Ty=c \\ y\geq 0 \end{cases}$$
costruisco il suo Duale Associato + tante epsilon quante sono le righe del duale moltiplicandole per l'identità $( i )$ $$(D_{aux})=\begin{cases}min \sum^n_{i = 0} \epsilon_i \\y^TA+\epsilon^T=c^T \\ y\geq 0 \\ \epsilon \geq0 \\ \end{cases}$$ 