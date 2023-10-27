#uni 
# Matrici a Scala
Tutte le righe sono del tipo: $$\begin{pmatrix} 0 \ ... \ 0 \ \ * \ \ * \ ... \ *\end{pmatrix}$$Dove il primo $*$ è un numero diverso da zero, e quelli dopo sono altra roba, che può anche essere $0$.
Nella prima riga possono non esserci zeri iniziali.
In ogni riga c'è almeno uno zero iniziale in più della precedente.
Il primo numero non nullo prima degli zeri iniziali, si chiama ___pivot della riga___.
Il fatto fondamentale è che lavorando alla Gauss posso portare qualunque matrice in una forma a scala.
### Soluzioni
La soluzione è unica quando le righe differiscono tutte per numero $1$ zeri.
Le soluzioni sono infinite quando le righe differiscono per un numero di zeri diverso da $1$.
Le soluzioni sono impossibili quando ottengo una riga con tutti zeri nella parte dei coefficienti ed un numero diverso da zero della parte dei termini noti.
In un sistema a scala, solo le variabili che hanno un pivot hanno una soluzione unica.