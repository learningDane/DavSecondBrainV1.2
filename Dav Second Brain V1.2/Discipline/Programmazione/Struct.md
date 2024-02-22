#uni 
Gli struct sono strutture dati personalizzate.
Sono uno strumento originato dal C e a differenza delle [[Classe]] non possono contenere metodi.
Questi sono gruppi di membri, ciascuno dei quali ha un tipo, un nome ed una informazione.
Un'altra differenze rispetto alle classi è che tutti i suoi membri sono pubblici.
Si possono creare array di struct.
Non sono definite operazioni di confronto sulle strutture.
Le strutture possono essere argomenti e tipi di funzioni.
```
struct costrutto{
	int a;
	int b;
};
oppure
struct { int a; int b; } costrutto = { 4, 6 };

costrutto coso;
coso.a = 6;
coso.b = 12;

costrutto ciao[7];

ciao[2].a = 13;
```
# Liste
Con le _struct_ è possibile creare le ___liste___, che sono strutture dati dove ogni elemento contiene un puntatore al prossimo elemento. Gli elementi vengono chiamati ___nodi___.
Si tiene in memoria solamente l'indirizzo del primo nodo, e viene chiamato ___head___.
Il puntatore dell'ultimo nodo in lista è ___nullptr___.
L'_head_ viene conservato nello _stack_, i nodi invece vengono conservati nell'_heap_.
```
struct nodo{
int a;
nodo*link = nullptr;
}
nodo*head = new nodo;
nodo*nuovaCoda = new nodo;
head->link = nuovaCoda;

nodo*nuovaHead = new nodo;
nuovaHead->link = head;
head = nuovaHead;
```
Una scomodità delle liste è che per trovare un elemento vanno scorse dalla _head_ in poi analizzando singolarmente tutti i nodi.