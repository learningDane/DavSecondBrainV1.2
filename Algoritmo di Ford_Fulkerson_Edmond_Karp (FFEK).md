## Definizioni necessarie

### Taglio della Rete
Per *taglio* s'intende una suddivisione della rete in $N_s$ e $N_t$ che separano $s$ da $t$. Gli altri archi possono stare arbitrariamente in un gruppo rispetto che nell'altro
### Archi Diretti del Taglio
Definiti da $A^+$ sono tutti gli archi $(i,j)\quad t.c.\quad i\in N_s \quad e \quad j\in N_t$ quindi sostanzialmente gli archi uscenti da $N_s$ e entranti in $N_t$ **non il contrario**
### Portata del Taglio
È definita dalla somma delle capacità degli [[#Archi Diretti del Taglio]] $$u(N_s,N_t)= \sum_{(i,j)\in A^+}u_{ij}$$
### Grafo Residuo
È il Grafo della rete (ovvero semplicemente lo schema topologico) con il *raddoppio* degli archi in verso opposto
### Capacità Residua
Su ogni arco a questo punto introduco una *Capacità Residua* ($r_{ij}$)$$r_{ij}=u_{ij}-\overline x_{ij}+\overline x_{ji}$$
- sull'arco "*vero*" rappresenta in effetti la capacità residua .
- sull'arco "*fittizio*" rappresenta la quantità di flusso inviata sull'arco vero.
### Cammino Aumentante
È un *Cammino Orientato* da $s$ a $t$ formato da archi $(i,j)$ con $r_{ij} > 0$.
Al percorso in questione è sempre associata una *Portata di* $C_{aum}$:$$\delta=min_{(i,j)\in C_{aum}}{(r_{ij})}$$
Per trovare il *Cammino Aumentante* applico l'[[#Algoritmo della Croce]]
### Teo (Max Flow_Min Cut)
Il flusso massimo è uguale al taglio di portata minima$$\overline x_{max} = u(N_s,N_t)$$
Da questo teorema capiamo che il *Problema del Taglio di Portata Minima* non è altro che il *Duale* del [[Problema del Flusso Massimo (Max Flow)]]
### Algoritmo della Croce
Lo applico per trovare i $C_{aum}$ e si basa sul cercare le *Stelle Uscenti* ($FS$) dal nodo $i$ quindi in sostanza tutti gli archi uscenti da quel nodo:$$FS(i)=\{j\} \quad t.c. \quad (i,j) \in A$$
Appena appare t nella colonna di destra mi fermo e ho trovato il mio $C_{aum}$. 
**RICORDA**: gli archi con capacità = 0 non li scrivo.
# Algoritmo
Data una soluzione ammissibile $\overline x$ (composta anche da tutti 0)
1. Seleziono un [[#Cammino Aumentante]] e calcolo il relativo $\delta$. Se non ci sono $C_{aum}$ sei all'ottimo
2. Aggiorno $\overline x$ con la seguente regola:$$\overline x_{new}=\begin{cases} \overline x_{ij} + \delta \quad \forall(i,j)\in C_{aum} \\ \overline x_{ij} \quad \forall(i,j)\notin C_{aum} \end{cases}$$ 
3. Ricalcolo $r_{ij}$ e torno al passo 1

