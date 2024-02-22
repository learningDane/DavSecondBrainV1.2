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
Oltre a private: e public: vi è uno stato intermedio: ___protected:___
	un membro protetto è come un membro _private_ solo che è anche accessibile alle classi derivate e alle funzioni amiche.

Le funzioni membro oltre che essere dichiarate all'interno della classe, possono essere dichiarate al di fuori di essa tramite l'operatore di risoluzione di visibilità [[Operatori#Altri operatori]].
Un oggetto appartenente ad una classe si chiama oggetto classe o istanza della classe.
Una classe individua un _campo di visibilità_.
Se all'interno di una classe viene utilizzato un identificatore dichiarato anche all'esterno della classe, la dichiarazione in classe nasconde quella esterna.
All'esterno della classe si può accedere ai membri interni ad una classe tramite l'_operatore di risoluzione di visibilità_ applicato al nome della classe se questi membri sono:
	1. funzione membro
	2. un tipo se dichiarato _public_
	3. statici
Quindi l'operatore non può essere applicato a campi dati non statici.
# Puntatore ___this___ 
Nel corpo di una funzione membro,ci si riferisce alla corrente istanza della classe a cui la funzione viene applicata tramite il puntatore predefinito ___this___.
```
Classe funzione(parametri) {
	corpo

	return *this;
}
//oppure anche
Classe& funzione(ecc) {
	return *this;
}
```
# Classi annidate
Nella dichiarazione di una classe si può dichiarare un'altra classe, in questo caso per accedere ai membri della classe annidata è necessario utilizzare due operatori di risoluzione di visibilità. Comunque nessuna delle due classi ha diritto di accedere ai membri privati dell'altra.
# Costruttore
Un costruttore è una funzione membro il cui nome è il nome della classe. Se definito viene chiamato tutte le volte che viene invocata una istanza di classe, subito dopo essere stata riservata la memoria per i campi dati.
È possibile definire più costruttori, uno che ammette argomenti ed uno di ___default___, che viene chiamato senza argomenti.
Un altro modo per fare ciò è semplicemente fornire degli argomenti di _default_: `Classe(tipo nome = valore, tipo altronome = altrovalore);`.
Questi due metodi non possono essere utilizzati contemporaneamente.
I costruttori vengono chiamati:
	1. per oggetti statici all'inizio del programma
	2. per oggetti automatici quando viene incontrata la definizione
	3. per oggetti dinamici quando viene incontrato l'operatore _new_. [[Memoria Dinamica]]
	4. per oggetti membro di altri oggetti, quando questi ultimi vengono costruiti.
	Un campo dati con l'attributo _const_ viene ___inizializzato___ nel momento in cui viene  definito il primo oggetto appartenente alla classe. 
L'___inizializzazione___ avviene tramite la ___lista di inizializzazione___ del costruttore. In una classe si possono dichiarati riferimenti non inizializzati purché siano inizializzati con la lista di inizializzazione.
Se qualche classe secondaria prevede argomenti formali allora deve essere definito un costruttore anche per la classe principale e questo deve possedere una ___lista di inizializzazione___.
### Costruttore di Copia
Il costruttore di copia predefinito è una funzione che agisce fra due oggetti della stessa classe effettuando una ricopiatura membro a membro dei campi dati.
Viene applicato:
	1. quando un oggetto classe viene inizializzato con un altro oggetto della stessa classe
	2. quando un oggetto classe viene passato come argomento ad una funzione
	3. quando una funzione restituisce (_return_) come valore un oggetto classe
Deve essere ridefinito per le classe che utilizzano memoria libera.
Se non si ridefinisce l'operatore di copia e non si vuole che venga nemmeno utilizzato quello standard, occorre inserire la sua dichiarazione nella parte _privata_. In questo caso però non si possono avere funzioni che abbiamo come argomenti un oggetto classe o come risultato valore del tipo della classe.
# Distruttore
Questo è una funzione membro invocata automaticamente quando un oggetto termina il suo tempo di vita. Un distruttore non ha argomenti. Un distruttore è obbligatorio quando il costruttore alloca memoria nello _heap_ [[Memoria Dinamica]].
I distruttori vengono chiamati:
	1. per oggetti statici al termine del programma
	2. per oggetti automatici all'uscita dal blocco in cui sono definiti
	3. per oggetti dinamici quando viene incontrato l'operatore _delete_ 
	4. per oggetti membro di altri oggetti quando questi ultimi vengono distrutti.
	Gli oggetti con stesso tempo di vita vengono distrutti nell'ordine inverso a quello in cui sono definiti.
# Funzioni _friend_
Una funzione è ___friend___ di una classe se una sua dichiarazione preceduta dalla parola chiave _friend_ viene inserita nella dichiarazione di tale classe. Questa può ora accedere ai campi pubblici e privati della classe tramite i selettori di membro.
# Overloading di Operatori
Può capitare che servano essere definite alcune operazioni su tipi di dato astratto. 
Si rende quindi necessaria la ridefinizione di questi operatori.
L'overloading di un operatore ha la forma di una definizione di una funzione, il cui identificatore è costituito dalla parola chiave ___operator___ seguita dall'operatore che si vuole ridefinire.
Tutti gli operatori di assegnamento restituiscono un riferimento all'oggetto.
ATTENZIONE: le versioni predefinite degli operatori assicurano alcune equivalenze, per esempio `++x` = `x += 1`. Quando si ridefinisce un operatore le equivalenze non valgono automaticamente.
ATTENZIONE: se si vuole che il primo operando possa essere qualsivoglia e non l'oggetto a cui si applica l'operatore (ovvero simmetria tra gli operatori) si devono utilizzare funzioni globali (quindi devono essere friend).
__Operatore di assegnamento__:
	L'operatore predefinito esegue una copia membro a membro ma va ridefinito se vi sono allocazioni dinamiche.
	L'operatore di assegnamento deve deallocare la memoria dinamica dell'operando di sinistra e riallocarla uguale all'operando di destra.
	___Problema dell'Aliasing___: evitare di sprecare operazioni se i due operandi sono già uguali.
	___Ottimizzare___ se le due memorie dinamiche hanno già la stessa dimensione.
Si possono ridefinire tutti gli operatori tranne:
	1. operatore di risoluzione di visibilità `::`
	2. operatore di selezione di membro `.` 
	3. operatore di selezione di membro tramite puntatore a membro `.*` 