#uni 
Supponiamo di dover procurare un servizio. Costruiamo la matrice di Copertura che indica se un utente è servito o meno dalle varie postazioni.
Dobbiamo minimizzare i costi, la somma dei costi di apertura delle postazioni.
È un [[Problema di Programmazione Lineare Intera (PLI)]] NP-HARD.
# Modello
- I=insieme siti candidati ad ospitare il servizio
- J=insieme di nodi domanda
- $d_{ij}$ = distanza $i,j$
- $c_i$ = costo di aprire servizio in $i$ 
- $D$ = distanza massima per considerare domanda coperta da servizio
- minimizzare i costi
$$\begin{cases}
\min \sum_i c_i \cdot x_i \\
\sum_i a_{ij} \cdot x_i ≥ 1 \quad \forall j \quad a_{ij}=(d_{ij} ≤D)\ ?\  1:0 \\ 
x_i \in \{0,1\}
\end{cases}$$
# Regole di Riduzione di una Matrice a Priori
1. una riga di tutti $0$ vuol dire [[Regione Ammissibile]] vuota, quindi non si può presentare
2. una colonna di tutti $0$ possiamo toglierla
3. una riga di tutti $1$ possiamo toglierla
4. una riga con un solo $1$ vuol dire che devo porre a $1$ la variabile della postazione che lo serve, posso poi quindi cancellare tutti i quartieri serviti dalla postazione
5. ___regola di dominanza___: si applica alle colonne (postazioni), se una postazione copre tutti i quartieri (o più) che copre un'altra postazione, posso eliminare la colonna di quest'ultima.
   $A^k \geq A^r$ , regola applicabile solo in mancanza di costi.
# Risoluzione
- $V_I$: Risolvo il rilassato continuo $\begin{cases} min \quad c^T\cdot x \\ Ax\geq \vec e \\ 0 \leq x \leq 1 \end{cases}$ e arrotondo per eccesso essendo un problema di minimo
- $V_S$: la S.A.
  1. senza costi: (caso particolare dell'algoritmo con costi) saturiamo progressivamente, apriamo postazioni con più quartieri forniti, cancello la colonna della postazione e cancello le righe servite, vediamo cosa rimane e ripetiamo
  2. con i costi: [[Algoritmo Chvatal]] 
- Algoritmo di riduzione del gap: [[Algoritmo di Riduzione del Gap tramite Piano di Taglio]]. 
# Esempio
Per esempio dobbiamo fornire le ambulanze, il tempo di arrivo di una ambulanza deve essere minore di 20 minuti.
Ci vengono forniti i tempi di arrivo nei diversi quartieri per ogni postazione, non ci interessa, trasformiamo in una matrice booleana con valore uno se il tempo di arrivo è minore del ___target___.
Se ci fosse anche un costo legato all'apertura di una postazione la regola di dominanza va applicata con cautela

| j quartieri/postazioni i | 1   | 2   | 3   | 4   | 5   |
| ------------------------ | --- | --- | --- | --- | --- |
| 1                        | 19  | 35  | 10  | 27  | 6   |
| ...                      |     |     |     |     |     |
$\downarrow$ 

| j quartieri/postazioni i | 1   | 2   | 3   | 4   | 5   |
| ------------------------ | --- | --- | --- | --- | --- |
| 1                        | 1   | 0   | 1   | 0   | 1   |
| 2                        | 0   | 1   | 0   | 1   | 0   |
| 3                        | 1   | 1   | 0   | 0   | 0   |
| 4                        | 0   | 1   | 1   | 0   | 1   |
| 5                        | 0   | 0   | 0   | 0   | 1   |
| 6                        | 1   | 1   | 1   | 1   | 1   |
| 7                        | 1   | 1   | 0   | 0   | 1   |
| 8                        | 0   | 1   | 1   | 1   | 0   |
| 9                        | 0   | 0   | 1   | 0   | 1   |
| 10                       | 0   | 0   | 0   | 0   | 0   |
