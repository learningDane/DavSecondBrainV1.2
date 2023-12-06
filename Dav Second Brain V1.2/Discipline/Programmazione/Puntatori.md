#uni
Un puntatore è un intero la cui informazione è semplicemente l'indirizzo di un'altra variabile. È possibile specificare il tipo di variabile alla quale punta per definirne le operazioni su. 
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