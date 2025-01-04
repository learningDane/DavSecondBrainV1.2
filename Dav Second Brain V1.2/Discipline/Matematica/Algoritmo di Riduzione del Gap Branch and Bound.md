#uni 
Questo è un algoritmo di [[Complessità]] esponenziale usato per i [[Problema di Programmazione Lineare Intera (PLI)]] booleani (anche se si può usare per quelli interi).
Si fonda sul concetto di [[Albero di Enumerazione Totale]].
È possibile applicarlo a qualsiasi [[Problema di Programmazione Lineare Intera (PLI)]], basta che abbia una $V_I$ ed una $V_S$ facilmente calcolabili.
# Algoritmo
Parto con $V_i$ come _valore corrente_.
Tramite la regola di taglio:
Taglio un ramo e scopro se tra le soluzioni sotto quel ramo ce ne è una migliore del _valore corrente_, in caso contrario taglio via quel ramo e quindi nego la variabile di quel ramo.
Se invece trovo un valore migliore, lo tengo come _valore corrente_, taglio il ramo e fisso la variabile di quel ramo.
___Tagliare___: visita implicita del sottoalbero.
Questo algoritmo finisce quando ho fatto una ___visita implicita___ per ogni ramo.
### Regole di Taglio (Branch)
##### minimo (TSP)
con $P_{ij}$ stadio $i$, ramo $j$.
1. $P_{ij}=\emptyset \quad ? \quad taglio$ 
   devo controllare poiché più scendo e più restringo la [[Regione Ammissibile]] (aggiungo vincoli).
2. $V_I(P_{ij})\geq V_S(P) \quad ? \quad taglio$  
   Calcolo $V_I(P_{ij})$, ovvero l'ottimo del Rilassato continuo di $P_{ij}$, se è maggiore del _valore corrente_ posso tagliare.
3. se $V_I(P_{ij}) < V_S(P)\quad$ e $\quad V_I(P_{ij}) \ ammissibile\quad$  allora aggiorno $V_S$ con $V_I(P_{ij})$ 
##### massimo (TSP)
Tenendo come riferimento il [[Problema dello Zaino]] (quindi di $max$)
con $P_{ij}$ stadio $i$, ramo $j$.
1. $P_{ij}=\emptyset \quad ?\quad taglio$ 
2. $V_S(P_{ij}) \leq V_I(P) \quad ? \quad taglio$ 
   Calcolo $V_S(P_{ij})$, ovvero l'ottimo del Rilassato continuo di $P_{ij}$, se è minore o uguale del _valore corrente_ posso tagliare.
3. se $V_S(P_{ij}) > V_I(P)\quad$ e $\quad V_S(P_{ij})\ ammissibile$($\in Z^n$ ovvero componenti intere)$\quad$ allora aggiorno $V_I$ con $V_S(P_{ij})$ allora scatta la regola 2 e taglio.
