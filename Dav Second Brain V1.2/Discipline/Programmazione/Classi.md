#uni 
Le classi vengono usate per definire strutture dati personalizzate ma rispetto agli [[Struct]], i cui membri sono pubblici, i suoi membri sono privati di default.
```
class nomeClasse {
private:
//dati membro

public:
//dati membro
//funzioni membro
};
```
se un elemento viene solo usato da un metodo all'interno della classe, conviene tenerlo private.