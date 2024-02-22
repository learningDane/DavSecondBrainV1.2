#uni 
# Controllo del Formato
Il controllo del formato avviene tramite i manipolatori:
`cout << manipolatore << datoDaManipolareSeNecessario;` 
`<iostream>`
	1. endl = inserisce '\n' e svuota il buffer
	2. dec,hex,oct = seleziona la base di numerazione
	3. boolalpha = inserisce o estrae oggetti di tipo booleano come nomi piuttosco che come 0/1
`<iomanip>`
	1. setw(int) = numero minimo di caratteri da utilizzare.
	2. setfill(char) = specifica quale carattere utilizzare per aumentare il numero di caratteri, il default è lo spazio
	3. setprecision(int) = nuemro di cifre significative per la stampa dei reali
I manipolatori hanno effetto fino alla nuova occorrenza del manipolatore eccetto setw() che ha effetto solamente sull'istruzione di scrittura immediatamente successiva.
# Controllo sugli Stream
Lo stato di uno stream dipende dalla configurazione dei ___bit di stato___, lo stato è _good_ se tutti i bit valgono 0.
	1. bit fail = errore irrecuperabile
	2. bit bad = se a 0 l'errore è recuperabile altrimenti no
	3. bit oef = posto a 1 se viene letta la marca di fine stream
I bit vengono esaminati tramite le seguenti funzioni:
	1. fail() = true se almeno uno dei due bit fail e bad sono ad 1
	2. bad() = true se bad = 1
	3. eof() = true se eof = 1
	4. good() = true se tutti i bit sono a 0