#uni 
Supponiamo di dover procurare un servizio. Costruiamo la matrice di Copertura che indica se un utente è servito o meno dalle varie postazioni.
Dobbiamo minimizzare i costi, la somma dei costi di apertura delle postazioni.
È un [[Problema di Programmazione Lineare Intera (PLI)]] NP-HARD.
### Problema di Massima Copertura
Associo ad ogni utente/quartiere il numero di clienti/abitanti stimati, con un dato numero di postazioni da poter aprire, devo massimizzare il numero di clienti serviti dalle postazioni.
- $h_i$ sono gli abitanti del quartiere $i$ 
- $z_i$ sono i quartieri scelti dalla scelta $x_i$ 
- $k$ numero di postazioni da aprire
$$\begin{cases} 
max \quad h^T\cdot z \\
Ax\geq z\\
\sum_i^n x_i=k \\
x_i,z_i\in \{0,1\}
\end{cases}$$
Matlab: 
colonne di A, Aeq: `numero di x + numero di utenti/quartieri(Nvincoli)` 
righe di A: `numero di utenti/quartieri(Nvincoli)`
righe di Aeq: `1`
c: `(-h1 -h2 ... -h8)` 
# Regole di Riduzione di una Matrice a Priori
1. una riga di tutti $0$ vuol dire [[Regione Ammissibile]] vuota, quindi non si può presentare
2. una colonna di tutti $0$ possiamo toglierla
3. una riga di tutti $1$ possiamo toglierla
4. una riga con un solo $1$ vuol dire che devo porre a $1$ la variabile della postazione che lo serve, posso poi quindi cancellare tutti i quartieri serviti dalla postazione
5. ___regola di dominanza___: si applica alle colonne (postazioni), se una postazione copre tutti i quartieri (o più) che copre un'altra postazione, posso eliminare la colonna di quest'ultima.
   $A^k \geq A^r$ , regola applicabile solo in mancanza di costi.
# Modello
una variabile per ogni postazione di cui non conosco l'apertura
un vincolo per ogni quartiere
se non specificato il vettore dei costi, $c=\vec e =(1 1 1 1 .. 1)$ 
il vettore $\vec e$ è il vettore di tutti $1$, $\vec e=(1 1 1 1 ... 1)$ 
$$(P)=\begin{cases} 
min\quad c^T\cdot x\\
Ax \geq \vec e\\
x\in \{0,1\}
\end{cases}$$
# Risoluzione
- $V_I$: Risolvo il rilassato continuo $\begin{cases} min \quad c^T\cdot x \\ AX\geq \vec e \\ 0 \leq x \leq 1 \end{cases}$ e arrotondo per eccesso essendo un problema di minimo
- $V_S$: la S.A.
  1. senza costi: (caso particolare dell'algoritmo con costi) saturiamo progressivamente, apriamo postazioni con più quartieri forniti, cancello la colonna della postazione e cancello le righe servite, vediamo cosa rimane e ripetiamo
  2. con i costi: [[Algortimo Chvatal]] 
- Algoritmo di riduzione del gap:
# Esempio
Per esempio dobbiamo fornire le ambulanze, il tempo di arrivo di una ambulanza deve essere minore di 20 minuti.
Ci vengono forniti i tempi di arrivo nei diversi quartieri per ogni postazione, non ci interessa, trasformiamo in una matrice booleana con valore uno se il tempo di arrivo è minore del ___target___.
Se ci fosse anche un costo legato all'apertura di una postazione la regola di dominanza va applicata con cautela

| quartieri/postazioni | 1   | 2   | 3   | 4   | 5   |
| -------------------- | --- | --- | --- | --- | --- |
| 1                    | 19  | 35  | 10  | 27  | 6   |
| ...                  |     |     |     |     |     |
$\downarrow$ 

| quartieri/postazioni | 1   | 2   | 3   | 4   | 5   |
| -------------------- | --- | --- | --- | --- | --- |
| 1                    | 1   | 0   | 1   | 0   | 1   |
| 2                    | 0   | 1   | 0   | 1   | 0   |
| 3                    | 1   | 1   | 0   | 0   | 0   |
| 4                    | 0   | 1   | 1   | 0   | 1   |
| 5                    | 0   | 0   | 0   | 0   | 1   |
| 6                    | 1   | 1   | 1   | 1   | 1   |
| 7                    | 1   | 1   | 0   | 0   | 1   |
| 8                    | 0   | 1   | 1   | 1   | 0   |
| 9                    | 0   | 0   | 1   | 0   | 1   |
| 10                   | 0   | 0   | 0   | 0   | 0   |
