#uni 
## [[Problema di Programmazione Matematica a Reti]]
Definiamo il ___costo ridotto dell'arco___: $c_{ij}^π=c_{ij}+π_i-π_j$ che sugli archi di base ($T$) fa sempre $0$.
Invece sugli archi non di base ($L$), per essere ammissibile deve essere maggiore di zero.
_Dato un albero di copertura $T$, che genera un flusso di base ($x_T$) ammissibile, se i costi ridotti degli archi di $L$ sono tutti positivi, allora siamo all'ottimo_.
## [[Problema di Programmazione Matematica a Reti Capacitate]]
**IPO**: supponiamo di avere una *tripartizione* che generi un *flusso di base* ammissibile.
- Se i costi ridotti degli archi di L $C^\pi_{(ij)L} \geq 0$ 
- Se i costi ridotti degli archi di U $C^\pi_{(ij)U} \leq 0$ 
**TESI**: Siamo all'ottimo