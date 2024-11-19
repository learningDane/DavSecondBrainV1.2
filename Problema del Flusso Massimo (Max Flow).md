C'è solo la Capacità
Si definisce un *sorgente* ($s$) a un *destinatario* ($t$):
- Il primo è il nodo 1 degli esempi : ha solo archi uscenti
- il secondo è il nodo n degli esempi : ha solo archi entranti
Se il poliedro è vuoto allora la S.O. = 0.
## Modello
Si introduce il concetto di portata massima $v$ che è sostanzialmente il valore ottimo della SO:$$\begin{cases} \max {0x+v} \\ Ex = b \\ 0 \leq x_{(i,j)} \leq u_{(i,j)} \end{cases}$$
dove $v$ è:$$\begin{cases} -v \quad i=s \\ 0 \quad i\neq s,t \\ v \quad i=t \end{cases}$$
se la funzione obbiettivo la vedo come $min{-0x-v}$ allora è chiaro che diventa un banale [[Problema di Programmazione Matematica a Reti ]] di *flusso di costo minimo*.
Questo, legato al fatto che v ha coefficiente 1 o -1, ci assicura che la matrice $E$, pur aggiungendoci una colonna (quella di $v$), rimane una *matrice d'incidenza* e quindi vale il [[Teorema di Interezza]]:
$v$ è un **arco** (in particolare l'arco che va da t a s diretto, avrà costo -1 e $u_{t,s} \geq$ del bilancio (t, s) (può valere anche $+\infty$ ))

Dopo aver aggiunto questo arco costruisco una **Tripartizione**:
vedi [[Problema di Programmazione Matematica a Reti Capacitate#Come si fa una tripartizione?]]
## Potenziali
Calcolo i potenziali come sempre ($-\pi_i+\pi_j=c_{(i,j)}$), tipicamente essendo che i costi sugli archi interni sono 0 si avrà:
- potenziale pari a 0 sui nodi raggiunti dal nodo 1 (preso come sempre da riferimento)
- potenziale pari a 1 sui nodi raggiunti dal nodo n a causa del costo = -1 sul nodo (n,1) che viene percorso al contrario (quindi $-\pi_n+0=-1$ di solito $c_{i,j}$ ha segno concorde a $\pi_i$ ma qui percorro l'arco al contrario ovvero da 1 a n)

## Soluzione Ottima
Due strade:
1. Applico pari pari l'[[Algoritmo del Simplesso su Reti#Reti Capacitate]]
2. Applico l'
 
