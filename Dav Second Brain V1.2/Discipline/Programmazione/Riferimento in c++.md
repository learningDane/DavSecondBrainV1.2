#uni 
Un riferimento è un identificatore che individua un oggetto, non si possono creare riferimenti a riferimenti. Deve sempre essere dichiarato ed inizializzato.  I riferimenti sono utilissimi usati come argomenti di funzioni. Un riferimento const può avere come argomento una variabile, ma non il contrario. `int &nome = variabile;` , `const_cast` converte un riferimento const in un riferimento non const.
Uno strumento analogo è il ___Typedef___, che si usa per aggiungere un alias ad un tipo:
```
typedef int intero;

intero a = 5;
```