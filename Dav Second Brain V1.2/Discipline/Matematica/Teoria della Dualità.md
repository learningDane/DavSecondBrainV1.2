#uni 
Dato un [[Problema di Programmazione Lineare (PL)]] in [[Problema di Programmazione Lineare (PL)#Formato Primale Standard]] ne individuiamo il suo ___complementare duale___: $$(P)\begin{cases} max \ c^T \cdot x \\ Ax \leq b \end{cases} \to (D)\begin{cases} min \ b^T \cdot y \\ A^Ty = c \\ y \geq 0\end{cases}$$
Questa è una operazione di dualità, trovare il duale di un primale; Inoltre il duale di un duale è il suo primale!! 
# Teorema della Dualità Forte / degli Scarti Complementari
Sia $(P)$ un problema PL con Duale (D), se $x,y$ sono soluzioni ammissibili di $(P),(D)$ e inoltre:
1. ogni volta che $x_j \neq 0$, $y$ soddisfa il $j$-esimo vincolo con uguaglianza
2. ogni volta che $y_i \neq 0$, $x$ soddisfa il $i$-esimo vincolo con uguaglianza
Allora $x$ e $y$ sono entrambe Ottime.
Sappiamo che una base del primale è anche una base del duale.
QUINDI:
1. ___Dato un vertice del problema primale, se nella sua duale la soluzione generata dalla stessa base è ammissibile, Allora la soluzione di base di quella stessa base è Ottimo in entrambi i problemi___.
2. ___Se uno degli elementi di $x_B$ è $0$, la soluzione di base è Degenere___.
3. ___Se tutti gli elementi di $y_B$ sono $\geq 0$ allora la soluzione di base è ammissibile (vertice)___.
# In Pratica
Per sapere se un dato vertice di un $(P)$ in forma primale è ottimo:
1. trovo la base che lo genera
2. trovo la duale di $(P)$ 
3. dal sistema $A^Ty=c$ pongo a $0$ le componenti Non Di Base e risolvo
4. se risolvendo le componenti Di Base tornano tutte positive, scopriamo che (la soluzione di base è ammissibile poiché rispetta tutti i vincoli $y \geq 0$ e di conseguenza) la nostra base genera un ottimo in entrambi i problemi.
