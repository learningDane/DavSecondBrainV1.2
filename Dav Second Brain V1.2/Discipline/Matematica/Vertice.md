#uni 
Un vertice è un punto nel [[Poliedro]] che non si può esprimere come [[combinazione convessa]] propria di altri due punti (diversi dallo stesso) nel Poliedro.
# Soluzione di Base
Trovare i vertici in un [[Problema di Programmazione Lineare (PL)]]:
sia $B \subset \{1,...,n\} ; |B| = n$, prendiamo $n$ vincoli su $m$
sia $A_B$ la sottomatrice di $A$ che ha le righe individuate da $B$
sia $b_B$ il sottovettore di $b$ con gli indici di $B$
Se e solo se $det A_B \neq 0$ la ___Soluzione di Base___ del sistema $A_B \cdot x =b_B$ 
Le soluzioni di base di un sistema lineare sono le intersezioni dei vincoli (semipiani).
Per il ___Teorema di Rouché-Capelli___ ([[Formulario Algebra Lineare]]), determinante diverso da zero significa che la soluzione esiste ed è unica.
Soluzione: $x=A_B^{-1}\cdot b_B$ 
# Ammissibile
Una soluzione di base è ___ammissibile___ se e solo se fa parte del [[Poliedro]], ovvero rispetta tutti i vincoli.
Per finire:
Un punto $\overline x$ del poliedro $P$ è ___vertice___ se e solo se è _soluzione di base ammissibile_.
# Degenere
Una soluzione di base si dice ___degenere___ quando è generata da più basi.
SOLO in $R^2$ una soluzione degenere implica l'esistenza di un vincolo superfluo e quindi eliminabile.
# Numero di Basi di un sistema
Il numero di basi di un sistema di $m$ vincoli su $n$ variabili è dato da: $$num=\begin{pmatrix} m \\ n\end{pmatrix}=\frac{m!}{n!(m-n)!}$$