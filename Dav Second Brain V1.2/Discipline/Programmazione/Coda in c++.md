#uni 
Una coda è un insieme ordinato di dati di tipo uguale in cui è possibile effettuare operazioni di inserimento ed estrazione secondo la regola ___FIFO___: first in first out.
Viene realizzata con una array circolare e due puntatori: front, da dove avviene l'estrazione, e back, in cui avviene l'inserimento.
Se $front == back$ coda vuota
Se $front == (back + 1)mod \ dim$ coda piena.
Gli elementi massimi sono $dim - 1$.
```
strcut Coda {
int front, back;
int queue[dim];
}

void inizializzazione(coda &cc) {
cc.front = cc.back = 0;
}

bool empty(const coda&cc) {
	if (cc.front == (cc.back + 1)%dim) { return true; }
	return false;
}

bool full(const coda&cc) {
	if (cc.front == (cc.back+1)%dim) {return true;}
	return false;
}

bool insert(coda&cc, int s) {
	if (full(cc)) {return true;}
	cc.queue[cc.back] = s;
	cc.back = (cc.back+1)%dim;
	return truel
}

bool estract(coda &cc, int &s) {
	if (empty(cc)) {return false;}
	s = cc.queue[cc.front];
	cc.front = (cc.front +1) % dim;
	return true;
}

void stampa(const coda&cc) {
	for (int i = cc.front; i%dim != cc.back; i++) {
		cout << cc.queue[i%dim] << endl;
}
```