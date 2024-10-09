#uni 
Una rete logica è un modello astratto di un sistema fisico, costituito d dispositivi tra loro interconnessi che si scambiano informazioni codificate tramite fenomeni fisici.
Questi fenomeni fisici si presentano ad un osservatore in due aspetti distinti:
Ad esmpioç
- corrente forte/debole
- tensione. alta/bassa
- magnetizzazione positiva/negativa
- ecc
# Caratterizzare una rete logica
Una rete logica è formata da:
1. un insieme $N$ di variabili logiche di ingresso. Il loro valore all'istante $t$ si chiama ___stato di ingresso all'istante___ $t$. L'insieme di tutti i $2^M$ stati di uscita verrà indicata con $X$.
2. un insieme di variabili logiche di uscita. Il loro valore all'istante $t$ si chiama ___stato di uscita all'istante___ $t$. L'insieme di tutti i $2^M$ stati di uscita è indicato con $Z$. 
   $Z = \{(Z_{M-1}Z_{M-2}...Z_0)\}$
3. Una legge di evoluzione nel tempo, che dice come le uscite si evolvono in funzione degli ingressi.
# Classificazione delle Reti logiche
Vengono classificate in base a 2 criteri riguardanti il tipo di legge di evoluzione nel tempo.
1. presenza/assenza di memoria:
   - [[Rete Combinatoria]] 
   - [[Rete Sequenziale]]
2. temporizzazione della legge di evoluzione:
   - reti asincrone : continuo aggiornare
   - reti sincronizzate : blocchi di aggiornamenti
# Interfaccia ed interpretazione fisica
Le reti logiche comunicano con l'esterno tramite variabili logiche (0 e 1).
Nel caso dei circuiti elettronici le variabili logiche vengono codificate come tensioni: bassa 0 e alta 1.
# I limiti del nostro modello
### Transizione dei segnali
Durante la transizione da 0 a 1 o contrario abbiamo una fascia di indeterminazione.
### Non contemporaneità
Questo ragionamento non implica variazioni contemporanee di più variabili.
Dobbiamo quindi evitare di supporre che due variabili di ingresso varino contemporaneamente.
In una rete sincronizzata in genere la non contemporaneità non è un problema, nelle reti asincrone invece si.
Stati di ingresso consecutivi devono essere adiacenti.