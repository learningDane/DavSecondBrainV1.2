#uni 27/09/2023
# Tipo di variabile
Il tipo di variabile definisce le dimensioni della variabile, ovvero il __numero di celle__, quali __valori può assumere__ e quali sono le __operazioni che ci si può eseguire__.
Le variabili posso essere dichiarate (assegnare un identificatore ed un tipo) e definite (allocare la memoria ed assegnare un valore). Di solito queste due operazioni vengono svolte insieme.
# Tipi
I tipi si dividono in:
1. fondamentali (o aritmetici):
	1. tipi predefiniti
		1. tipo intero (tipo __numerico__ e __discreto__) e naturale
		2. reale (tipo __numerico__)
		3. booleano (__discreto__)
		4. carattere (__discreto__)
	2. tipi enumerazione
2. derivati
	si ottengono a partire dai tipi predefiniti e permettono di costruire strutture dati più complesse.
# Luogo di Definizione
Se una variabile viene definita al di fuori di una funzione, viene immagazzinata nella memoria statica e viene chiamata variabile ___globale___, che viene caricata all'avviarsi del programma e distrutta quando il programma si chiude.
Un altro modo per condividere una variabile tra funzioni è _static_:  `static int;`.
Esiste poi la memoria dinamica ___"Heap"___. `new*variabile = new int;` per esempio alloca una int nello heap e crea un puntatore di nome variabile a quell'allocazione.
# Condividere Variabili tra file
Per condividere una variabile va definita globalmente e con il tag _external_: `external int variabile;`.
# Intero

# Reale

# Booleano
### In memoria
1 bit $0$ oppure $1$, rispettivamente per falso e vero.
### Operazioni
1. $||$ OR logico o disgiunzione
2. $\& \&$ AND logico o congiunzione
3. $!$ NOT logico o negazione
# Carattere
[[Char]] 
# Enumerati 
Sono costituiti da insiemi di costanti intere, definite dal programmatore, ciascuna individuata da un identificatore e detta ___enumeratore___. Servono per rappresentare informazioni non numeriche definite dal programmatore e sono utilizzate per variabili che assumono solo un numero limitato di valori.
### Operazioni
Sono possibili tutte le operazioni di confronto e quelle degli interi, che agiscono sulla codifica degli enumeratori.
### Esempi
```
enum Giorni {lun, mar, mer, gio = 7, ven, sab = 9, dom};
Giorni oggi = lun; //0
oggi += 8; //ven
cout << oggi << endl; //8, conversione implicita

enum {rosso, giallo, verde} semaforo;
semaforo = rosso;
```
# Tipi Derivati
1. [[Riferimento in c++]] 
2. [[Puntatore]] 
3. [[Array]] 
4. [[Struct]] 
	[[Pila in c++]] 
	[[Coda in c++]] 
1. [[Unione]]  
2. [[Classe]] 
# Costanti
### In memoria
### Operazioni
Una costante può solo fare da valore sinistro, non può subire operazioni di assegnazione dopo che ha ricevuto un valore.
### Esempi
`const int hakunamatata = 4;`