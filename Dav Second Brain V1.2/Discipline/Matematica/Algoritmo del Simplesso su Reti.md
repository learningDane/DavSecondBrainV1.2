#uni 
Si basa sull'[[Algoritmo del Simplesso]], ma semplificato e alleggerito appositamente per un [[Problema di Programmazione Matematica a Reti]].
# Algoritmo
1. Troviamo un vertice di partenza $T\to x_T\geq 0$ ammissibile con potenziale non ammissibile ([[Teorema di Bellman]]), ovvero con almeno un costo ridotto relativo ad un arco non di base minore stretto di zero.
   Scelgo il primo ([[Regole Anticiclo di Blend]]) vincolo che viola Bellman: $(i,j)\in L : c_{ij}^π < 0$, e questo è l' ___arco entrante____. 
2. Disegno l'albero di copertura (solo archi di base) e aggiungo tratteggiato l'arco entrante.
   Questo creerà un ciclo all'interno della Rete.
Adesso devo trovare l'arco uscente, in particolare l'arco uscente deve far parte del ciclo, in modo da "spezzare" il ciclo.
	   1. orientiamo il ciclo in maniera concordata con $(i,j)$ 
	   2. $C=C^+\cup C^-$ dove $C^+$ sono gli archi concordi con il verso, e $C^-$ quelli discordi.
	   3. ___Regola di Update___:
	      con $\theta \geq 0,\in N$ 
	      $$x(\theta)=\begin{cases} \overline x_{ij} + \theta \quad(i,j)\in C^+ \\ \overline x_{ij}-\theta \quad (i,j) \in C^- 
	      \\ \overline x_{ij} \quad \quad \ \ \ (i,j) \notin C
	      \end{cases}$$
	    ___Teorema___: La funzione obiettivo, calcolata sul nuovo flusso, è uguale al costo precedente, più theta volte il costo dell'arco entrante: $$c^Tx(\theta)=c^T\overline x + \theta \cdot c_{ij}^π$$
3. Prendo $\theta = min\{\overline x_{ij} \} \quad (i,j)\in C^-$ 
   e il primo arco di cui prendo il valore è l'arco uscente ([[Regole Anticiclo di Blend]])
# Ammissibilità
Per controllare che la nuova $x(\theta)$ sia ammissibile dobbiamo controllare che rispetti i bilanci, ovvero $\begin{cases} Ex=b \\ x\geq 0\end{cases}$ 
per controllare che un flusso di base sia ammissibile basta controllare che le componenti siano maggiori di $zero$.
Controlliamo allora. che soddisfi i bilanci:
1. prendiamo un nodo esterno al ciclo, gli archi del nodo possono essere:
   -  entrambi concordi al ciclo: 
   - entrambi discordi
   - uno concorde ma uscenti
   - uno concorde ma entranti.
in tutti i casi il flusso se prima era ammissibile allora con il nuovo flusso rispetta i bilanci,
ora controlliamo che siano tutti positivi:
- $\overline x_{ij} +\theta \geq 0$ 
- $\overline x_{ij} \geq 0$ 
- $\overline x_{ij} - \theta \geq 0 \quad ?$ solo se $\theta \leq min\{\overline x_{ij} \} \quad (i,j)\in C^-$ e lo scegliamo proprio uguale quindi si, allora è ammissibile ed inoltre sappiamo che pone un flusso a zero.  
# Considerazioni e Ottimizzazione
L'unico caso in cui l'algoritmo entri in loop è nel caso in cui il minimo dei flussi degli archi discordi al ciclo, sia $zero$, che vuol dire che un flusso di base è $zero$, ovvero è un caso degenere.
Le [[Regole Anticiclo di Blend]], in questo algoritmo serve solo per evitare il loop del caso degenere. Se sappiamo che il problema non ha casi degeneri possiamo non implementare la regola e invece di prendere il primo flusso negativo potremmo prendere il più negativo e velocizzare molto l'algoritmo.
Spesso la regola non viene proprio applicata, si controlla solo che l'algoritmo non sia in loop, se individua un loop riapplica la regola, superando il degenere, e poi torna a non applicarla.
# Cicli
Se viene fuori un ciclo il cui costo è negativo, il problema fa $meno \ infinito$.