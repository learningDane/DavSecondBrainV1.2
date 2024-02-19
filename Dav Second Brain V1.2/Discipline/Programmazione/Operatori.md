#uni 28/09/2023
Le operazioni sono caratterizzate da:
1. simbolo
2. arietà (n° di operandi)
3. posizione (prefisso-infisso-postfisso)
4. associatività (sx $\to$ dx oppure dx $\to$ sx)
5. priorità
La maggior parte degli operatori non cambia gli operandi, restituisce solo un valore destro risultato delle operazioni.
# Calcolo di espressioni
Nel calcolo di insiemi di operazioni vengono rispettate le precedenze e le associatività degli operatori presenti.
##### Precedenza
Per primi vengono valutati i fattori (prima postfissi e poi prefissi), il NOT (`!`) logico, il meno unario (`-`) ed il più unario (`+`).
Dopo vengono valutati i termini, applicando gli operatori binari nel seguente ordine:
1. moltiplicativi (`*, /, %`)
2. additivi (`*,-`)
3. di relazione (`<, ...`)
4. di uguaglianza (` ==, != `)
5. logici nell'ordine: `&&, ||`
6. di assegnamento (` =, ...`)
Le parentesi tonde fanno diventare qualunque espressione un fattore, che viene calcolato per primo.
# Operatori logici
1. Negazione logica
	1. !
	2. unario
	3. prefisso
	4. dx $\to$ sx
	5. !, &&, ||
2.  Or Logico
	1. ||
	2. binario
	3. infisso
	4. sx $\to$ dx
	5. !, &&, ||
3. And Logico
	1. &&
	2. binario
	3. infisso
	4. sx $\to$ dx
	5. !, &&, || 
4. Implicazione Logica
	1. $\implies$
	2. binario
	3. infisso
	4. sx $\to$ dx
	5. bho
	Vera a meno che $b$ sia falso. [[Basi della Logica#Implicazione]]
# Operatori bit a bit
1. $|$ OR bit a bit
	0,0-0; 0,1-1; 1,1-1
2. $\&$ AND bit a bit
	0,0-0; 0,1-0; 1,1-1
3. __^__ XOR esclusivo bit a bit
	0,0-0; 0,1-1; 1,1-0
4. $\sim$ complemento bit a bit
	0-1; 1-0
5. $<<$ traslazione a sinistra e >> traslazione a destra: `a>>b` 
	operatore binario che trasla di `b` bit i singoli bit di `a`. Esempio: `19 (10011)>>2 = 4(100)` 
# Altri operatori
1. Assegnamento
	1. =
	2. binario
		a sinistra ci deve essere un left-value, a destra ci può essere anche un right-value, quindi `3=5;`non compila, 3 è una variabile letterale, non ha una left-value.
	3. infisso
	4. dx $\to$ sx
	5. penultima, svolta prima della virgola
	Come risultato produce la variabile aggiornata.
2. Operatore Ternario
	1. (a) ? b : c;
	2. ternario
	3. infisso?
	4. sx $\to$ dx
	5. bho
3. Operatore `sizeof(variabile)` c++
4. Virgola
	1. `,`
	2. binario
	3. infisso
	4. sx $\to$ dx
	5. ha la priorità più bassa di tutti