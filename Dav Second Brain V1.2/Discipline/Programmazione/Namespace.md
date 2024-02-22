#uni 
Un ___namespace___ è un insieme di dichiarazioni e definizioni racchiuse tra parentesi graffe. Una namespace può essere dichiarata solo a livello di unità di compilazione o all'interno di un'altra _namespace_.
Gli identificatori relativi ad un namespace sono visibili dal punto di dichiarazione fino alla fine del _namespace_, salvo ___operatore risoluzione di visibilità___ [[Operatori#Altri operatori]].
I _namespace_ sono aperti, ovvero con una successiva dichiarazione usando lo stesso identificatore è possibile includere altri membri.
Per utilizzare uno specifico namespace si può usare la direttiva ___using namespace nomeNamespace;___ .
# namespace globale
Questo è il namespace costituito dalle definizioni e dichiarazioni a livello di unità di compilazione.
```
namespace nome {

	int n;
	
	struct nome {
		ecc
	}
	
	tipo funzione(argomenti) { corpo }
	
	namespace nome2 {
		ecc
	}
	
}

int main() {
	nome::n = 5;
}
```
