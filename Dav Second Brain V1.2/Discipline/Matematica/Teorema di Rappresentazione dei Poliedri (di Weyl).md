#uni 
Dato un [[Poliedro]] ($Ax \geq b$) $\exists V = \{v^1,...,v^n\} \in P$
ed $\exists E = \{e^1,...,e^n\} \subset R^n$ 
tale che $$P=convesso V+conoE$$
Le rappresentazioni di Weyl di uno stesso poliedro non sono uniche, per ogni poliedro ci sono infinite rappresentazioni di Weyl. (per es invece del vettore $(1,0)$ posso prendere $(2,0)$ ).
Essenzialmente prendi il convesso di alcuni punti e lo trasli lungo il cono individuato da alcuni vettori.
# Soluzione di un PdPL
Questo teorema può essere utilizzato per risolvere un [[Problema di Programmazione Lineare (PL)]].
Dato un PL $(P) \begin{cases}max c^T \cdot x \ \ \ \ \}f.o.  \\ Ax \leq b \ \ \ \}P \end{cases}$ 
Per il teorema di Weyl abbiamo $\forall x_i \in P \to x_i = v_i e_i$ 
$\overline x = \sum \lambda_i v_i + \sum \mu_j e_j$ con $\sum \lambda = 1, \ \lambda \in [0,1]$ e $\mu \geq 0$ 
Calcolo la funzione obiettivo sostituendo a $x$ quanto sopra, tenendo a mente che $\sum \lambda v$ è limitato, invece se $\exists j : c\cdot e_j > 0$ abbiamo che $(P)=+\infty$ 
se invece siamo nel caso in cui $\forall j, c\cdot e_j \leq 0$ allora $(P)$ è limitato ed inoltre:
scegliendo $s$ tale che $c\cdot v_s \geq c\cdot v_i, \forall i$  allora abbiamo che la soluzione ottimale della funzione obiettivo: $$max_{x\in P} \ c\cdot x = c\cdot v_s$$
