#uni 
Il ___Query Processor___ (o ottimizzatore) è un modulo del DBMS.
Le interrogazioni sono espresse ad alto livello, l'ottimizzatore sceglie la strategia realizzativa a partire dall'istruzione [[MySQL]]. 
Il termine ottimizzazione è improprio perché il processo utilizza ___euristiche___.
Si basa sul concetto di equivalenza: due espressioni sono equivalenti se producono lo stesso risultato.
I DBMS cercano di eseguire espressioni equivalenti a quelle date ma meno _costose_.
___Euristica Fondamentale___:
	- selezioni e proiezioni il più presto possibile per ridurre le dimensioni dei risultati intermedi
		- ___push selections down___: 
		- ___push projections down___: 
Le euristiche ci vengono fornite dagli ___alberi___.
# Grafi, Cammini, Cicli e Alberi
