#uni 
Una pila è un insieme ordinato di dati dello stesso tipo in cui è possibile effettuare operazioni di inserimento e di estrazione secondo la regola ___LIFO___: last in first out.
Il primo elemento  è all'indice 0, la attuale cima viene chiamata ___top___ e il numero massimo di elementi è ___dim___.
Se $top == -1$ la pila è vuota. Se $top == dim -1$ allora la pila è piena.
```
struct Pila {
int top = -1;
int stack[dim];
}
```