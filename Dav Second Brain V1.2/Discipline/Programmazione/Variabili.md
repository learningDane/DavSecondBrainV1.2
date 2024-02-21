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
Generalmente occupa un byte. Il valore può essere espresso in __decimale__, __ottale__ (`\cifraottale`) ed __esadecimale__ (`\xcifraesadecimale`).
Sono possibili tutte le operazioni degli interi, che agiscono sulla codifica dei caratteri.
La codifica usata dipende dall'implementazione ma la più comune è quella ASCII.
### Valori
1. letterale carattere: un carattere racchiuso fra apici $'a'$
2. caratteri di controllo: combinazioni speciali che iniziano con un backslash:
	1. `\n` : nuova riga
	2. `\t` tabulazione orizzontale
	3. `\r` ritorno carrello
	4. `\\` backslash
	5. `\'` apice
	7. `\"` virgolette
### Nota
le sequenze di escape e le rappresentazioni ottale e esadecimale di un carattere vanno racchiuse fra apici 'xxx' quando rappresentano un _letterale carattere_.
![[Pasted image 20240219161113.png]]
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
1. riferimenti
	è un identificatore che individua un oggetto, non si possono creare riferimenti a riferimenti. Deve sempre essere dichiarato ed inizializzato.  I riferimenti sono utilissimi usati come argomenti di funzioni. Un riferimento const può avere come argomento una variabile, ma non il contrario. `int &nome = variabile;` , `const_cast` converte un riferimento const in un riferimento non const.
2. puntatori
	Un puntatore è un oggetto il cui valore rappresenta l'indirizzo di un altro oggetto o di una funzione. Se un puntatore è const non si può usarlo per modificare l'oggetto a cui punta, anche se non const. Se provato a stampare restituisce il valore esadecimale dell'indirizzo contenuto. Molto utili come parametri di funzioni, come i riferimenti. Usati nelle liste e nelle array dinamiche. `int*puntatore = &variabile;` 
3. array
	l'identificatore di una array identifica l'indirizzo del primo elemento della array.
	___Aritmetica dei puntatori___:
		se l'espressione p rappresenta l'indirizzo di un oggetto di tipo T, allora l'espressione (p+1) rappresenta l'indirizzo di un oggetto sempre di tipo T, che si trova successivamente in memoria. 
		Se p=addr e il tipo T occupa n locazioni di memoria allora `(p+i) = addr+ni.` 
	`int nome[dimensione] = {a,b,c};`
	___Array multidimensionali___:
		ogni elemento della prima array è come se fosse un puntatore ad un'altra array. `int nome[larghezza][altezza][lunghezza];` 
1. strutture
2. unioni
3. classi
# Costanti
### In memoria
### Operazioni
Una costante può solo fare da valore sinistro, non può subire operazioni di assegnazione dopo che ha ricevuto un valore.
### Esempi
`const int hakunamatata = 4;`