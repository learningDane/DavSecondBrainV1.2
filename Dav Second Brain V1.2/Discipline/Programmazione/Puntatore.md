#uni
Un puntatore è un oggetto il cui valore rappresenta l'indirizzo di un altro oggetto o di una funzione. Se un puntatore è const non si può usarlo per modificare l'oggetto a cui punta, anche se non const. Se provato a stampare restituisce il valore esadecimale dell'indirizzo contenuto. Molto utili come parametri di funzioni, come i riferimenti. Usati nelle liste e nelle array dinamiche.

```
int intero = 54;
int*puntatore = &intero;
```
`&` è l'operatore indirizzo, semplicemente restituisce l'indirizzo della variabile.
Sul puntatore si possono effettuare varie operazioni, se dopo aver dichiarato il puntatore, ci si mette `*` davanti, restituisce la variabile alla quale punta:
```
int intero = 7;
cout << intero << endl; //7
int*puntatore = &intero;
*puntatore += 8;
cout << *puntatore; //15 (7+8)
```
I puntatori vengono usati per cambiare il valore di una variabile attraverso una funzione che non dichiara la variabile: 
```
void cambio(int*pun) {  
    *pun += 8;  
}  
int main() {  
    int intero = 78;  
    cambio(&intero);
    cout << intero; //86 (78+8)
}
```
Vengono anche usati nelle liste, dove uno dei membri di un nodo è l'indirizzo al nodo successivo.
# Puntatore a Funzione
I puntatori possono anche contenere indirizzi di funzioni.
Definizione: `tipo (*nome) {corpo};`
Chiamata attraverso il puntatore: `(*nome) (parametri);`