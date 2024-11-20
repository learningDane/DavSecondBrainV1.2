#uni 
>
>_Dato un albero di copertura $T$, che genera un flusso di base ($x_T$) ammissibile, se sono rispettate le __Condizioni di Bellman__ allora siamo all'ottimo_.
>
#### Condizioni di Bellman per Reti non Capacitate
[[Problema di Programmazione Matematica a Reti non Capacitate]]
- $C^π_{ij} = 0 : (i,j)\in T$ 
  ovvero costi ridotti di archi di base $=0$
- $C^π_{ij} \geq 0 : (i,j)\in L$
  ovvero costi ridotti di archi $\in L$ (non di base) $\geq 0$ 
#### Condizioni di Bellman per Reti Capacitate
[[Problema di Programmazione Matematica a Reti Capacitate]]
- $C^π_{ij} = 0 : (i,j)\in T$ 
  ovvero costi ridotti di archi di base $=0$
- $C^π_{ij} \geq 0 : (i,j)\in L$
  ovvero costi ridotti di archi $\in L$ (non di base) $\geq 0$ 
- $C^π_{ij} \leq 0 : (i,j)\in U$
  ovvero costi ridotti di archi $\in U$ (non di base) $\leq 0$ 
# Costo Ridotto
Definito il ___costo ridotto relativo ad un arco___: $$C^π_{ij}=c_{ij}+π_i - π_j$$ 