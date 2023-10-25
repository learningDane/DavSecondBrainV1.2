#uni 
Nella conversione da _double_ a _int_ si può verificare una perdita di informazioni, dovuta al troncamento della parte decimale.
Nella conversione da _int_ a _double_ si può verificare una perdita di informazioni dovuta al fatto che i reali vengono rappresentati per approssimazione.
La conversione a booleano di un numero: se il numero è diverso da zero, _true_, invece se il valore del numero è zero allora _false_.
# Conversioni implicite
Se un operatore ha entrambi gli operandi interi o reali, ma di lunghezza diversa, quello di lunghezza minore viene convertito al tipo di quello di lunghezza maggiore.
Se un operatore ha un operando intero ed uno reale, il valore dell'operando intero viene convertito a reale ed il risultato è un reale.
##### Conversioni più significative per l'assegnamento
1. Ad una variabile di tipo reale può essere assegnato un valore intero
2. ad una variabile tipo intero può essere assegnato un valore di tipo reale, booleano, enumerazione e carattere.
3. ad una variabile tipo carattere può essere assegnato un valore di tipo intero, booleano o enumerazione.
4. ad una variabile di tipo booleano o enumerazione non può essere assegnato un valore non del suo tipo.
# Conversioni Esplicite
`static_cast<tipo>(variabile);
Effettua una conversione di tipo quando esiste la conversione implicita inversa e può essere usato per effettuare conversioni di tipo previste dalla conversione implicita.
`variabile1 = (tipo) variabile2;
Effettua una conversione.