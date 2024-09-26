#uni 
Una __transazione__ deve essere un insieme di operazioni ___atomico___ (indivisibile) e ___definitivo___, corretto anche in presenza di concorrenza e con effetti definitivi. La conclusione positiva di una transazione corrisponde ad un impegno a mantenere traccia del risultato in modo definitivo.
In altre parole una transazione identifica una unit' elementare di lavoro svolta da un'applicazione, che deve rispettare particolari caratteristiche di correttezza, robustezza e isolamento: è quindi una successione di comandi e/o operazioni in esecuzione che forma un'unit' logica di elaborazione sulla base di dati.
Una transazione comprende una o più operazioni di accesso al [[Database]]:
- ___read___, lettura: interrogazioni
- ___write___, scrittura: inserimenti, cancellazioni, modifiche
In termini più informatici una __transazione__ è una parte di programma caratterizzata da __inizio__, una __fine__ e al cui interno deve essere eseguita __una sola volta__ uno dei seguenti comandi:
- `commit` per terminare correttamente
- `rollback`/`abort` per abortire la transazione
In [[MySQL]]:
- `begin-transaction`
- `end transaction` 
Esempio di transazione:
```NON_IN_SQL
	start transaction;
	update ContoCorrente
		set Saldo = Saldo + 10
			where NumConto = 12202;
	if (NumConto > 0) commit work
		else rollback work;
```
# Stato di una transazione
Una transazione entra nello stato __attivo__ subito dopo essere iniziata, e ci rimane per tutta la sua esecuzione.
Quando termina entra nello stato di __commit parziale__, se è stata eseguita con successo e tutti i suoi aggiornamenti sul [[Database]] sono permanenti si sposta nello stato __commit__, in caso contrario entra nello stato __fallito__ dal quale passa ad __abortito__ quando tutti i suoi aggiornamenti al Database sono stati annullati.
# Proprietà delle transazioni
### Atomicità
Una transazione è un'unità atomica di elaborazione. Non può lasciare il database in uno stato intermedio, se fallisce deve __annullare__ i cambiamenti svolti.
### Consistenza
La transazione deve rispettare i vincoli di integrità, se lo stato iniziale è corretto allora lo è anche lo stato finale.
Il sistema deve sempre essere in un ostato consistente, solo durante l'esecuzione della transazione può non esserlo.
### Isolamento
La transazione non è influenzata dagli effetti delle altre transazioni concorrenti, l'esecuzione concorrente di una collezione di transazioni deve produrre un risultato uguale a quello che si otterrebbe con un'esecuzione sequenziale. Quindi una transazione non espone i suoi stati intermedi: si evita un _effetto domino_.
### Durabilità (o persistenza)
Gli effetti di una transazione andata in _commit_ sono persistenti e non vanno perduti quindi anche dopo un guasto possiamo sempre ripristinare il database ad uno stato consistente.
# Sistema Transazionale
Un sistema che offre un meccanismo per la definizione e l'esecuzione di transazioni è detto ___sistema transazionale___ (___OLTP___), questo esegue transazioni per conto di applicazioni concorrenti.