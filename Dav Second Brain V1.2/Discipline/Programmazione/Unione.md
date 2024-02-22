#uni 
Le unioni sono dichiarate ed usate con la stessa sintassi delle [[Struct]], salvo sostituite la parola chiave struct con union.
Una unione rappresenta un'area di memoria che può in tempi diversi contenere dati di tipi differenti: i membri di una unione corrispondono a interpretazioni diverse di una unica are di memoria.
In caso di due membri di dimensioni differenti viene allocato lo spazio per il tipo più grande.
Valgono le stesse operazioni definite sulle strutture.
Si può assegnare solo un valore iniziale e viene assegnato del tipo del primo membro.
```
union Unione{
	char c;
	int i;
}
oppure
union{char c; int i;} Unione = {'A'};
```