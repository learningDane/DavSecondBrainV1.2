#uni 
# Selection Sort
Si cerca l'elemento più piccolo tra i rimanenti N-i e si scambia con l'elemento in posizione i, per i = 0, 1, ... , N-1.
```
void selectionSort(int vettore[], int n) {
int min
for (int i = 0; i < n-1; i++) {
	min = i;
	for (int j = i+1; j < n; j++) {
		if (vettore[j] < vettore[min]) { min = j; }
	  }
	  scambia(vettore, i, min);
}
}
```
La complessità di questo algoritmo è dell'ordine $n^2$.
# Bubble Sort
Si scorre l'array $n-1$ volte, dove $n$ è il numero di elementi nella array scambiando due elementi contigui se non sono nell'ordine giusto. 
```
void bubbleSort(int vettore[], int n) {
for (int i = 0; i < n-1; i++) {
	for (int j = n-1; j > i; j--) {
		if (vettore[j] < vettore[j-1]) {
			scambia(vettore, j, j-1);
		}
	}
}
}
```
La complessità di questo algoritmo è dell'ordine $n^2$.