#uni 28/09/2023
Le operazioni sono caratterizzate da:
1. simbolo
2. arietà (n° di operandi)
3. posizione (prefisso-infisso-postfisso)
4. associatività (sx $\to$ dx oppure dx $\to$ sx)
5. priorità
La maggior parte degli operatori non cambia gli operandi, restituisce solo un valore destro risultato delle operazioni.
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
2. $\&$ AND bit a bit
3. __^__ OR esclusivo bit a bit
4. $\sim$ complemento bit a bit
5. $<<$ traslazione a sinistra
6. $>>$ traslazione a destra
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