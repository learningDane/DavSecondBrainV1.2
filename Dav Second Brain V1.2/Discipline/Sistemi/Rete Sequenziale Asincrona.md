#uni 
Una [[Rete Combinatoria]] è priva di memoria, lo stato di uscita dipende solo dai valori attuali.
Un ___Buffer___ memorizza uno stato. 
Per ottenere una rete sequenziale, dove lo stato di uscita dipenda dalla sequenza, è necessario avere memoria degli stati.
# Latch SR
Questa rete è composta da due NOR in sequenza collegati uno all'entrata `s` set e l'altro collegato all'entrata `r` reset. In uscita ha `q` e `qN`.
Le variabili in entrata si dicono ___attive alte___, che indica che la funzione che è indicata dal loro nome viene eseguita quando il valore dell'ingresso è pari a $1$.

| s   | r   | q               |
| --- | --- | --------------- |
| 1   | 0   | 1               |
| 0   | 1   | 0               |
| 0   | 0   | _conservazione_ |
| 1   | 1   | NON SI FA       |
Lo stato $(0,0)$ è quello che rende la rete ___sequenziale___, poiché memorizza lo stato.
Questa rete inoltre è asincrona poiché è sempre aggiornata e si adegua immediatamente agli stati di entrata.
Questa è la sua ___tabella di applicazione___ ($\neq$ tabella di verità), che mostra gli stati di ingresso necessari affinché lo stato di uscita passi da `q` a `q'`.

| q   | q'  | s   | r   |
| --- | --- | --- | --- |
| 0   | 0   | 0   | -   |
| 0   | 1   | 1   | 0   |
| 1   | 0   | 0   | 1   |
| 1   | 1   | -   | 0   |
### Regole di Pilotaggio
Delle [[Rete Combinatoria#Regole di Pilotaggio]] per il Latch SR basta rispettare la prima regola.
È importare non dare lo stato di ingresso `(1,1)` poiché il primo bit che si stabilizza determina lo stato finale della rete, generando effettivamente un bit casuale.
Il tempo che ci mette un Latch SR a stabilizzarsi è di pochi nanosecondi.
### Fase di Reset
All'accensione del sistema i Latch SR hanno contenuto casuale, ma per esempio i registri del processore EF ed EIP ([[Schema del Calcolatore#Registri]]) devono avere un determinato valore (le prime istruzioni).
Questo porta ad avere bisogno di una ___fase di reset___ nella quale si inizializzano determinati valori.