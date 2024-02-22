#uni 
Un programma può essere formato da più unità di compilazione, che vengono sviluppate separatamente e collegate successivamente per formare un file eseguibile.
	- Un identificatore ha collegamento interno se si riferisce ad una entità accessibile solamente da quella unità di compilazione. In questo caso uno stesso identificatore in diverse unità di compilazione si riferisce ad entità diverse.
	- Un identificatore ha collegamento esterno se si riferisce ad una entità accessibile da diverse unità di compilazione.
	  In questo caso tale entità deve essere unica in tutto il programma.
La regola di default è che:
	- gli identificatori con visibilità locale hanno collegamento interno.
	- gli identificatori con visibilità a livello di unità di compilazione hanno collegamento esterno (a meno che non siano ___const___).
# Static
Oltre al luogo di dichiarazione, sulla visibilità influisce anche la parola chiave ___static___:
	1. quando applicata ad una variabile dichiarata in una funzione, la rende persistente tra diverse istanze della funzione, facendole ritenere il suo valore.
	2. quando applicata ad una variabile membro, la rende persistente tra le diverse istanze della classe, facendole ritenere il suo valore. Questa variabile viene allocata al partire del programma e persiste fino alla fine dello stesso.
	3. quando applicata ad una funzione membro, diventa possibile chiamarla senza specificare una istanza della classe. Così facendo però non ha accesso ai membri della classe (attraverso il pointer ___this___).
	4. quando applicata a variabili globali o di una namespace, la rende visibile solo alla attuale unità di compilazione.