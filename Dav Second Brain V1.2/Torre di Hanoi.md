#uni 
Questo problema consiste nello spostare dei cerchi da un paletto ad un altro, potendo utilizzare un terzo paletto come appoggio.
Regola:
- spostare i cerchi da A a C
- spostare solo un cerchio alla volta
- non mettere cerchi più grandi sopra cerchi più piccoli
### Codice
```c++
void hanoi(int n, pal A, pal B, pal C) {
	if (n==1) sposta(A,C);
	else {
		hanoi(n-1, A,C,B);
		sposta(A, C);
		hanoi(n-1, B, A, C);
	}
}
```
$T(1) = a$, $T(n) = b+2T(N-1)$ 2