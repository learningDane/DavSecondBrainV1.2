#uni 
Il preprocessore è una parte del compilatore che elabora il testo del programma prima dell'analisi lessicale e sintattica. 
Svolge alcune azioni:
1. include altri file nel testo
2. espande secondo le loro definizioni i simboli definiti dall'utente
3. include o esclude parti di codice che verrà compilato.
Queste operazioni sono controllate dalle _direttive_ per il preprocessore (quelle che iniziano con `#`) e possono essere inclusioni di file _header_.
1. percorso a partire da cartelle standard: `#include<file.h>`
2. percorso a partire dalla cartella in cui avviene la compilazione: `#include "file.h"`.
# Define
`#define identificatore token-string` 
Con define posso fare si che il preprocessore sostituisca ogni istanza del mio identificatore con il valore _token-string_.
Si può anche usare come macro:
`#define massimo(A,B) ((A)>(B) ? (A) : (B))`
Quindi ogni volta che il preprocessore trova _massimo(A,B)_ lo sostituisce con il numero più grande.
# Compilazione condizionale
`#if, #elif, #else, #endif`.
### Forme Concise
`#ifdef = #if defined`
`#ifndef = #if !defined`
### Define a riga di comando
Linux: `g++ -DLINUX main.cpp -o main.exe`
# Evitare la doppia implementazione di un file
```
//file complesso.h
#ifndef complesso.h
#define complesso.h
	//contenuto del file complesso.h
#endif

//file main.cpp
#include "complesso.h"
#include "complesso.h" //il file viene comunque incluso una sola volta.

int main() {
//blah blah
}
```