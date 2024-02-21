#uni 27/09/2023
## Basi:
È un linguaggio _Case Sensitive_, ovvero distingue fra maiuscole e minuscole.
Ogni statement seguito da `;`diventa una istruzione espressiva.
## Codice:
`#include`include le librerie, seguita poi `<xx>`per le librerie interne e `"xx.h"`per le librerie esterne ma contenute nel progetto.
Con `using namespace std;` indichi al compilatore che tutti i nomi usati nel programma si riferiscono allo standard ANSI-C++.
`int main() {}`dichiarazione della funzione main, il periodo base.

`cout<< xxx;`stampa xxx nella console (output)
`<<endl;` finisce la riga corrente e si usa con `cout<< xx << endl;`
`cin>>;` invece prende input

## Variabili
1.  `bool`= booleano, 1 bit, assume come valori solo vero o falso
2. `short int`= short integer, 16 bit, numero intero
3. `int`= integer, 32 bit, numero intero
4. `long int`= long integer, 64 bit (non sempre), numero intero
5. `double`= floating point number, 64 bit, numero decimale
6. `char`= single character, 8 bit, carattere singolo, circondato da virgolette singole
7. `string`= frase, ? bit, frase, circondato da doppie virgolette
8. `struct`= è un contenitore di variabili diversi, definito dal programmatore di volta in volta. Questa può essere definita al di fuori di funzioni ma non alloca memoria.

# Operatori
1. `++a;` incremento prefisso
	restituisce la variabile già aumentata.
2. `a++;`incremento postfisso
	restituisce la variabile e POI la aumenta.
3. `(a) ? b : c;`Operatore ternario
	se `a` allora `b` altrimenti `c`.
# Calcolo delle espressioni
Ordine del calcolo delle espressioni:
Per primi vengono valutati i fattori (prima postfissi e poi prefissi), il NOT (`!`) logico, il meno unario (`-`) ed il più unario (`+`). Le parentesi fanno diventare il contenuto un fattore.
- Operatori parentesi ()
- Operatori di accesso ai membri . e ->
- Operatori di post-incremento ++ e post-decremento --
- Operatori di pre-incremento ++ e pre-decremento --
- Operatori di moltiplicazione * e divisione /
- Operatori di addizione + e sottrazione -
- Operatori di spostamento a sinistra << e spostamento a destra >>
- Operatori di confronto <, <=, >, >=
- Operatori di uguaglianza == e di non uguaglianza !=
- Operatori logici & (AND) e | (OR)
- Operatore di assegnazione =
# Associatività
Gli operatori aritmetici sono associativi a sinistra. Gli operatori unari e di assegnamento sono assiociativi a destra. 
Gli operatori && e || sono associativi a sinistra ed il calcolo di un'espressione contenente questi operatori termina appena si può decidere se sia vera o falsa, questa si chiama ___Regola del Corto Circuito___.
# Istruzioni Ripetitive
1. while
	`while (condizione) {statement;}`
	Se la condizione è vera, esegue lo statement e torna a verificare la condizione, esegue lo statement finché la condizione è vera, se è falsa esco dal ciclo. Dentro lo statement quindi ci deve essere qualcosa che influisce sulla condizione, per evitare di comicniare un ciclo infinito.
1. do
2. for
# Struttura di un programma
_basic main program_
	`int main ()`_compound statement_
_compound statement_ 
	`{`statement sequence `}`
_statement_
1. declaration statement
2. definition statement
3. expression statement
	   `expr | opt ;
	   Esempi:
		   `5;`
		   `a+b;`
4. structured statement
	1. compound statement
		Attraverso la coppia di delimitatori `{ e }` si trasforma una sequenza di istruzioni in una unica istruzione.
	2. selection-statement
		1. if
		2. switch
	3. iteration statement
		1. while
		2. do
		3. for
1. jump statement
	1. break;
	2. continue;
	3. goto;
	4. return;
2. labeled statement
# Arrays/Vettori
Una array è un gruppo di variabili che possono essere chiamate attraverso l'aggiunta di un indice al nome del gruppo
```
tipo nomeArray[numero di elementi] = {elemento1, elemento2, ecc};
nomeArray[numero dell'elemento] = valore da assegnare;
```
### Array Multidimensionali / Matrici
```
tipo nomeArray[dimensione1][dimensione2][dimensione3] = { 
{ { {} , {} , ecc} , { {} , {} , ecc} , ecc } ,
{ {} , {} , ecc } ,
ecc 
}
nomeArray[indice1][indice2][indice3] = valore;
```
### Vettori Dinamici
Prima di c++ '13 non si poteva scrivere `int vettore[size]` , si doveva usare una allocazione manuale della memoria:
```
size = 7;
int *array = new int[size]{3,5,8,12, ecc};
delte[] array;
```
RICORDA di usare il `delete[]` per deallocare la memoria.
# Istruzione if
```
if (condizione) {statement}
else if (condizione) {statement}
esle {statement}
```
# Istruzione _switch_ e _break_
```
switch (indice: int, char, enum...) {
	case 1:
		statement
		break;
	case 2: case 5:
		statement
	default:
		statement
}
``` 
attenzione, se non è presente il break vengono anche eseguite le istruzioni successive, anche se il case non è giusto.
# Istruzioni ripetitive
### While
```
while (condizione) { statement }
```
### Do-While
```
do {statement} while (condizione)
```
Qui viene prima eseguito lo statement e poi, se la condizione è vera, viene ripetuto.
### For
```
for (inizializzazione; condizione; statement) { step }
```
# Istruzioni di Salto
### Break
Salta all'istruzione immediatamente successiva al corpo del ciclo o dello switch che contiene il break.
### Continue
Termina l'iterazione del ciclo che la contiene e passa a rivalutare la condizione.
# Gli Stream
Gli stream predefiniti sono ___cin, cout e cerr___. Si trovano  in `<iostream>`.
##### cin
`cin >> variabile;`, è definito per caratteri, numeri interi, numeri reali e sequenze di caratteri. 
Quando viene incontrato un `cin` il programma si arresta in attesa di dati.
Col comando di esecuzione del programma, lo _stream_ `cin` può essere ridiretto su un file _file.in_ residente su memoria di massa con il seguente comando Linux/DOS/Windows: `programma.exe < file.in`.
Il `cin` non preleva niente finché non incontra qualcosa che non sia uno spazio bianco e si ferma appena ne trova uno, se vuoi che prelevi solo un carattere e questo carattere deve poter essere anche uno spazio bianco, usa `cin.get(variabile);` 
La lettura di interi e reali invece continua fino a che non incontra qualcosa di non assegnabile al tipo di variabile voluto.
`cin` è associativo a sinistra e produce come risultato `cin` quindi è possibile fare `cin >> a >> b`. 
Se la `cin` è in stato di errore si può utilizzare `cin.clear();`. Inoltre può costituire una condizione, vera se non è in stato di errore, falsa altrimenti. `while (!(cin>>a>)) { cin.clear(); }`
Se il programma sta leggendo dati da un terminale, per emettere la marca di fine stream l'utente deve utilizzare `ctrl+d` in Unix-Linux e `ctrl+z` in Dos-Windows.
##### cout
`cout << espressione`
Viene calcolata l'espressione e convertita in una sequenza di caratteri.
Possono essere scritti interi, reali, caratteri e sequenze di caratteri. Gli enum e bool vengono implicitamente convertiti ad interi.
Analogamente alla `cin`, possono essere concatenate diverse `cout` poiché `cout << blah blah;` restituisce `cout`.
Può avere i seguenti parametri:
	1. ampiezza del campo, ovvero il numero totale di caratteri impiegati.
	2. lunghezza della parte frazionaria.
Col comando di esecuzione del programma, lo _stream_ `cout` può essere ridiretto su un file _file.out_ residente su memoria di massa con il seguente comando Linux/DOS/Windows: `programma.exe < file.out`.
# Concetto di Funzione
Una variabile dichiarata all'interno di una funzione si dice locale ed è visibile solo all'interno di essa. Lo stesso nome usato su variabili in funzione diverse si riferisce ad oggetti diversi. La memoria per queste variabili locali viene assegnata alla chiamata di una istanza di uan funzione e viene deallocata alla fine della medesima istanza, le variabili locali infatti non mantengono il valore tra le diverse istanze della stessa funzione.
Una funzione può chiamare altre funzioni, ma se una funzione chiama un'altra istanza di se stessa, si dice ___ricorsiva___. 
# Stringhe
Una stringa è una sequenza di caratteri. In c++ non esiste il tipo stringa, sono invece delle array di caratteri, che memorizzano stringhe (un carattere per elemento) e il carattere nullo `'\0'` finale. Gli operatori di ingresso ed uscita accettano stringhe come argomento: l'operatore di ingresso legge i caratteri dallo stream di ingresso, saltando eventuali spazi bianchi in testa e li memorizza in sequenza fino a che non incontra un carattere spazio, che viene registrato come carattere nullo ed indica la fine della stringa.
# Librerie
Una libreria è un insieme di funzioni precompilate. Ogni libreria è formata da coppie di file, in uno vi è la dichiarazione delle funzioni (.h) e nell'altro vi è il corpo delle funzioni (.cpp).
Per includere una libreria bisogna usare la direttiva `#include`.
Queste sono le componenti della ___libreria std___.
1. cstdlib
	abs(n)
	rand(), casuale tra zero e RAND_MAX
	srand(n) inizializza la funzione rand()
2. cctype
	isalnum(c)
	isalpha(c)
	isdigit(c)
	islower(c)
	isprint(c)
	isspace(c)
	isupper(c)
3. cmath (x è double)
	sin(x)
	cos(x)
	tan(x)
	asin(x)
	acos(x)
	atan(x)
	exp(x)
	log(x)
	log10(x)
	fabs(x)
	ceil(x)
	floor(x)
	pow(x,y) //x^y
	sqrt(x)
#### Libreria `<cstring>` 
1. `strlen(const char str)` restituisce un intero che è il numero di caratteri (length). Non conta il carattere nullo.
2. `strcpy(char dest, const char sorg)` copia una stringa dentro un'altra stringa destinazione.
3. `strcmp(const char str1. const char str2)` è una sorta di operatore confronto, restituisce un numero positivo, negativo, oppure 0.
4. `tolower(char str)` rende tutti i caratteri minuscoli.
5. `toupper(char str)` rende tutti i caratteri maiuscoli.
6. `strcat(char dest, const char sorg)` concatena due stringhe in una sola.
7. `strchr(const char str, char c)` restituisce un puntatore alla prima occorrenza di `c` in `str` oppure `0` se non ne trova.