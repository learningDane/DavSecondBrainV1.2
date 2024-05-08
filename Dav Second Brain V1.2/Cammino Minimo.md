#uni 
Un cammino è il numero di nodi che crea un arco tra due nodi di partenza ed arrivo.
Il cammino minimo è quel cammino che permette di attraversare il minimo numero di nodi.
# Algoritmi di ricerca del Cammino Minimo
###### Algoritmo di Dijkstra
Si applica ai grafi orientati che hanno peso positivo sugli archi.
Trova i cammini minimi da un nodo di partenza a tutti gli altri nodi.
Questo è un algoritmo greedy, prende decisioni locali sperando che siano le scelte migliori globalmente.
I cammini minimi vengono inizialmente posti ad infinito e vengono via via aggiornati con stime sempre piè precise ad ogni iterazione di un ciclo, quando un nuovo nodo viene "sistemato" quindi stabilizza il cammino.
Utilizza due tabelle _dist_ e _pred_ con $n$ elementi ($n$ = numero di nodi).