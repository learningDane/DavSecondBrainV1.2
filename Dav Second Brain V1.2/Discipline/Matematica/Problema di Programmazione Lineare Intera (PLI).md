#uni 
Questi problemi hanno il seguente modello:
$$\begin{cases} max \ c^Tx \\ Ax \leq b \\ x \in Z^n_+\end{cases}$$
La tecnica di risoluzione di questi problemi si fonda sulla diminuzione del gap tra $V_I$ e $V_S$.
Per Ottenere la _valutazione superiore_ normalmente risolviamo il rilassato continuo, ma non sempre ciò è possibile e quindi ci limitiamo ad eliminare determinati vincoli.
Questa tecnica di risoluzione è ___greedy___, ovvero facile, rapido e buono.
# Problemi di Minimo
- Valutazione Superiore:
  1. s
  2. per [[Problema di TSP]]: [[Algoritmo di Kruskal]] per creazione di [[k-Albero]] di costo minimo
  3. per [[Problema Bin-Packing]]: Algoritmi next,first,best-fit-decreasing
  4. per [[Problema di Copertura]]: [[Algortimo Chvatal]] 
- Valutazione Inferiore
  1. Rilassato continuo
  2. per [[Problema di TSP]]: Algoritmo del Nodo più vicino
# Problemi di Massimo
- Valutazione Superiore:
  1. Rilassato Continuo
- Valutazione Inferiore
  1. [[Problema dello Zaino]]: Algoritmo di Saturazione dello Zaino per Rendimenti (componenti Intere)
# Algoritmi per Riduzione del Gap
1. [[Algoritmo di Riduzione del Gap "Branch and Bound"]]
2. [[Algoritmo di Riduzione del Gap tramite Piani di Taglio]] 