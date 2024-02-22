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
struct { int a; int b; } costrutto = { 4, 6 }

costrutto coso;
coso.a = 6;
coso.b = 12;

costrutto ciao[7];

ciao[2].a = 13;
```
