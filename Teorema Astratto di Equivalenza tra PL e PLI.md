#uni 
# Prefazione
Prendiamo il [[Poliedro]] del rilassato continuo di un [[Problema di Programmazione Lineare Intera (PLI)]], quindi $Ax \leq b \ ; \ x \geq 0$.
Disegniamo i punti a componenti intere dentro il poliedro, questo insieme è la [[Regione Ammissibile]] del problema PLI.
Adesso unisco i vertici dell'insieme di punti disegnato, otteniamo una regione ammissibile, che è la più piccola regione ammissibile che contiene le soluzioni ammissibili del PLI, ovvero $convS$ ([[Teorema di Rappresentazione dei Poliedri (di Weyl)]]).
Quindi abbiamo i punti $S=\{  x \in Z^n_+ : Ax \leq b \}$ e $p= \{ Ax\leq b \ , \ x \geq 0 \}$
Dato il Th di Weyl abbiamo che ogni poliedro è $convS + conoE$ e ogni $convS +conoE$ è poliedro.
Quindi abbiamo il più piccolo poliedro che contiene $S$.
Quindi $convS \leq P$ quindi $$ \begin{cases} max \ c^Tx \\ x \in S \end{cases} \leq \begin{cases} max \ c^Tx \\ x\in convS \end{cases} \leq \begin{cases} max \ c^Tx \\ x \in P \end{cases}$$
dove:
- $S$ è l'insieme dei punti a componenti intere dentro il poliedro del rilassato continuo.
- $convS$ è il convesso generato dai punti di $S$
- $P$ è il poliedro del rilassato continuo
# Teorema
dati $A,b \in Z$
$$max_{x \in S} \ c^Tx = max_{x\in convS} \ c^Tx$$
questo perché i vertici di questi due insiemi sono gli stessi! E sappiamo che l'ottimo sta sui vertici.