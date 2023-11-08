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
	2. selection-statement
	3. iteration statement
5. jump statement
6. labeled statement
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
switch (indice) {
	case 1:
		statement
		break;
	case 2:
		statement
	default:
		statement
}
```
Posso rimpiazzare gli _int_ con dei _char_:
```
switch (indice) {
	case 'a':
		statement
		break;
	case 'b': case 'B':
		statement
	default:
		statement
}
``` 
# Istruzioni ripetitive
### While
### Do-While
# Classi
### C-String
Una stringa è una array di _char_ avente lunghezza arbitraria e che ad un certo punto contiene il carattere di arresto `\0`.
Una qualunque array: `char stringa[] = {'p','a','r','o','l','a'};` 
Letterale stringa: `char stringa[] = "parola";` 
Come su tutte le array non si possono usare gli operatori di assegnamento sui letterali stringa, si possono solo usare durante l'inizializzazione, input ed output.
#### Libreria `<cstring>` 
1. `strlen()` restituisce un intero che è il numero di caratteri (length).
2. `strcpy()` copia una stringa dentro un'altra stringa destinazione.
3. `strcmp()` è una sorta di operatore confronto, restituisce un numero positivo, negativo, oppure 0.
4. `tolower()` rende tutti i caratteri minuscoli.
5. `toupper()` rende tutti i caratteri maiuscoli.
6. `strcat()` concatena due stringhe in una sola.