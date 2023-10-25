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
1. structured statement
2. jump statement
3. labeled statement