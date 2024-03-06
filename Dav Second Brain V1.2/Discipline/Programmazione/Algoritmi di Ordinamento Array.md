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
# Quicksort
Si prende un'elemento dell'array come ___perno___ a caso (circa) e si divide l'array in due array, a sinistra tutti gli elementi più piccoli del Perno e a destra quelli più grandi. Poi se le array nuove sono maggiori di uno si chiama recursivamente la quicksort su di esse, che verranno a loro volta scomposte in altre array ecc.
```c++
void quicksort(int A[], int inf = 0, int sup = n-1) {
	int perno = A[(inf+sup)/2], s = inf, d = sup;
	while (s <= d) {
		while (A[s] < perno) s++;
		while (a[d] > perno) d--;
		if (s>d) break;
		exchange(A[s],A[d]);
		s++;
		d--;
	}
	if (inf < d) quicksort(a, inf, d);
	if (sup > s) quicksort(a, s, sup);
}
```
Complessità:
	- caso peggiore: $o(n^2)$ 
	- caso medio: $o(nlog(n))$ 
	- caso migliore: $o(nlog(n))$ ma con una costante nascosta minore rispetto al caso medio.

[[Torre di Hanoi]] 