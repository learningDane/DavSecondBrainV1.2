#uni 
Questo è un algoritmo di [[Complessità]] esponenziale usato per i [[Problema di Programmazione Lineare Intera (PLI)]] booleani (anche se si può usare per quelli interi).
Si fonda sul concetto di [[Albero di Enumerazione Totale]].
# Algoritmo
Parto con $V_i$ come _valore corrente_.
Tramite la regola di taglio:
Taglio un ramo e scopro se tra le soluzioni sotto quel ramo ce ne è una migliore del _valore corrente_, in caso contrario taglio via quel ramo e quindi nego la variabile di quel ramo.
Se invece trovo un valore migliore, lo tengo come _valore corrente_, taglio il ramo e fisso la variabile di quel ramo.
Questo algoritmo finisce quando esaurisco le foglie.
### Regole di Taglio (Branch)
Tenendo come riferimento il [[Problema dello Zaino]] (quindi di $max$)
con $P_{ij}$ stadio $i$, ramo $j$.
1. $P_{ij}=\emptyset \quad ?$ se si taglio
2. Calcolo $V_S(P_{ij})$, ovvero l'ottimo del Rilassato continuo di $P_{ij}$, se è minore del _valore corrente_ posso tagliare.