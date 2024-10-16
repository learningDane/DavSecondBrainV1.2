#uni 
Questi problemi hanno il seguente modello:
$$\begin{cases} max \ c^Tx \\ Ax \leq b \\ x \in Z^n_+\end{cases}$$
La tecnica di risoluzione di questi problemi si fonda sulla diminuzione del gap tra $V_i$ e $V_s$.
Per Ottenere la _valutazione superiore_ normalmente risolviamo il rilassato continuo, ma non sempre ciò è possibile e quindi ci limitiamo ad eliminare determinati vincoli.
Questa tecnica di risoluzione è ___greedy___, ovvero facile, rapido e buono.