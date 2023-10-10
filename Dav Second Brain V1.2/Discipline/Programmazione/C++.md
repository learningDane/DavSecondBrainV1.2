#uni 27/09/2023
## Basi:
È un linguaggio _Case Sensitive_, ovvero non puoi usare la denominazione che vuoi per variabili ecc.
Ogni statement seguito da `;`diventa una istruzione espressiva.
## Codice:
`#include`include le librerie, seguita poi `<xx>`per le librerie interne e `"xx.h"`per le librerie esterne ma contenute nel progetto.
Con `using namespace std;`si evita di dover aggiungere `std`successivamente.
`int main() {}`è il periodo base.

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