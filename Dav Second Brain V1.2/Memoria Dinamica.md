#uni 
Quando si vuole gestire manualmente la memoria si utilizza l'___Heap___, che al contrario dello ___Stack___ che viene gestito automaticamente dall'OS, permette di allocare ed eliminare la memoria a piacimento.
Si utilizza per esempio nei casi in cui non si sa al momento della scrittura quale siano le dimensioni di una array, non è possibile infatti definire una array di dimensioni variabili poiché la memoria nello _stack_ viene allocata prima della partenza del programma.
È invece possibile allocare memoria nello _Heap_ a piacimento durante l'esecuzione del programma, gli oggetti così ottenuti sono detti _dinamici_ e sono allocati nella _memoria libera_. 
Per l'allocazione dinamica utilizziamo l'operatore prefisso ___new___: l'argomento è il tipo dell'oggetto da allocare e restituisce l'indirizzo della memoria allocata.<u>Se non è possibile allocare la memoria voluta, restituisce 0</u>. 
`int*p = new int;`
Si può preventivamente controllare l'esito di una allocazione con la funzione `set_new_handler();`  della libreria `<new>`. Questa funzione prende come argomento una funzione di tipo Void e senza argomenti, che viene eseguita se l'allocazione non è possibile.
Gli oggetti allocato con l'operatore _new_ non vengono automaticamente distrutti come gli oggetti nello _stack_. Per distruggerli serve l'operatore prefisso ___delete___. Esso ha come argomento un puntatore all'oggetto da distruggere, che __deve__ essere stato allocato con l'operatore _new_, altrimenti restituisce errore.
Se si vuole distruggere una _array_ allocata dinamicamente bisogna utilizzare `delete[]`.
Altrimenti gli oggetti allocati vengono comunque distrutti alla fine del programma. 