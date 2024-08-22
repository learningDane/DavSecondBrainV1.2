#uni 
Un Grafo $G=(V,E)$ consiste in:
- un insieme $V$ di __vertici__ (o __nodi__).
- un insieme $E$ di coppie di vertici, detti __archi__.
  Ogni arco connette due vertici
Un __grafo Orientato__ (o __diretto__) è un grafo di archi orientati e rappresenta relazioni orientate tra coppie di oggetti.
Un __grafo non orientato__ (o __non diretto__) è un grafo di archi non orientati e rappresenta relazioni simmetriche tra coppie di oggetti.
# Cammino e Ciclo
Un cammino di un grafo $G=(V,E)$ da un vertice $x$ ad $y$ è dato da una sequenza di vertici $v_i$ di $V$ con $v_0=x$ e $v_k=y$, tale che per ogni $1 \leq i \leq k$, l'arco $(v_{i-1},v_i) \in E$ 
Un cammino $(v_0,...,v_k)$ tale che $v_0=v_k$ è detto __ciclo__.
Un grafo diretto è detto aciclico se non contiene cicli.
Un cammino è quindi il numero di nodi che crea un arco tra due nodi di partenza ed arrivo.
### Cammino Minimo
Il cammino minimo è quel cammino che permette di attraversare il minimo numero di nodi.
##### Algoritmi di ricerca del Cammino Minimo
###### Algoritmo di Dijkstra
Si applica ai grafi orientati che hanno peso positivo sugli archi.
Trova i cammini minimi da un nodo di partenza a tutti gli altri nodi.
Questo è un algoritmo greedy, prende decisioni locali sperando che siano le scelte migliori globalmente.
I cammini minimi vengono inizialmente posti ad infinito e vengono via via aggiornati con stime sempre piè precise ad ogni iterazione di un ciclo, quando un nuovo nodo viene "sistemato" quindi stabilizza il cammino.
Utilizza due tabelle _dist_ e _pred_ con $n$ elementi ($n$ = numero di nodi).
# Albero
Un grafo non orientato si dice __connesso__ se esiste un cammino tra ogni coppia di vertici.
Un albero è un grafo non orientato nel quale due vertici qualsiasi sono connessi da un solo cammino.
Gli alberi vengono usati come rappresentazione interna delle interrogazioni: le foglie sono dati, quindi relazioni o file e i nodi intermedi sono operatori, quindi prima operatori algebrici e poi effettivi operatori di accesso ai dati.
![[Pasted image 20240814002057.png]]