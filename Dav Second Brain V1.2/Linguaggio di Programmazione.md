#uni 
Non usiamo direttamente il linguaggio naturale poiché i linguaggi naturali non evitano le _ambiguità_ e non si prestano a descrivere processi computazionali automatizzabili. 
Un linguaggio di programmazione è una notazione formale che può essere usata per descrivere algoritmi.
Un linguaggio è caratterizzato da:
1. ___Sintassi___: insieme di regole formali per la scrittura di programmi, usate per costruire correttamente frasi nel linguaggio.
2. ___Semantica___: insieme dei significati da attribuire alle frasi costruite nel linguaggio
	1. a parole (poco precisa e ambigua)
	2. mediante azioni (semantica operazionale)
	3. mediante funzioni matematiche (semantica denotazionale)
	4. mediante formule logiche (semantica assiomatica)
# Definizione
Detti:
1. $V$ alfabeto: l'insieme dei simboli con cui si costruiscono le frasi.
2. $V^*$ universo linguistico: l'insieme di tutte le frasi (ovvero sequenze finite) di elementi di $V$.
3. $L$ linguaggio su alfabeto $V$: un sottoinsieme di $V^*$ .
4. $S$ simbolo non terminale detto simbolo iniziale.
_Data una grammatica $G$, si dice linguaggio $LG$ generato da $G$ l'insieme delle frasi di  $V$ derivabili dal simbolo iniziale $S$ applicando le regole di produzione $P$_.
# Approcci
### Approccio Compilato
1. editing: scrivere il testo e memorizzarlo su supporti di memoria permanenti.
2. compilazione e linking
	Analisi e traduzione del programma sorgente
3. esecuzione
# Approccio Interpretato
1. editing
2. interpretazione
	Analisi ed esecuzione del programma sorgente
# Linguaggi di Programmazione
[[C++]] 