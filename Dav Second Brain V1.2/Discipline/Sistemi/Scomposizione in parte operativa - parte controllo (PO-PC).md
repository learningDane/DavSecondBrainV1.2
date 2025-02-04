#uni 
![[Pasted image 20250202194305.png]]
>La parte operativa è quella responsabile dell'interfacciamento col mondo esterno e della produzione degli stati interni dei registri operativa.
>È una RSS di Mealy ([[Rete Sequenziale Sincronizzata (RSS)]], [[Modello di Mealy]]).

>La parte di controllo è quella contentente la logica per l'aggiornamento dello stato interno.
>È una RSS di Moore ([[Modello di Moore]]).

Queste reti presentano la variabile di condizionamento e quella di comando
# Procedimento
1. Guardiamo ad ogni registro operativo come [[Registro Multifunzionale]] e isoliamo le loro relative µ-operazioni diverse. Per ogni registro operativo andiamo a sintetizzare la relativa rete combinatoria operativa. Ogni rete combinatoria operativa prende in ingresso le variabili di comando della parte di controllo e lo stato di uscita dei registri operativi.
2. Adesso guardiamo i µ-salti e sintetizziamo per ogni condizione indipendente (le condizioni che determinano i µ-salti) una rete combinatoria di condizionamento, che deve generare una ==variabile di condizionamento==, che deve valere $1$ se la condizione è vera e deve valere $0$ se la condizione è falsa.
3. Adesso che abbiamo le variabili di condizionamento dobbiamo sintetizzare la parte controllo.
# Riassunto
- Immaginiamo ogni registro operativo come un registro multifunzionale (cioè un registro preceduto da multiplexer).
* Nel codice Verilog cerchiamo tutte le funzioni che possono determinare il valore del registro operativo nell’assegnamento procedurale.
* ==Quale funzione sarà considerata dipenderà dalle variabili di condizionamento==, generate dalla Parte Controllo. La cosa non è strana: è lo stato interno della rete a dirci cosa fare con un certo registro operativo.
```Verilog
casex(STAR)
	S0 : begin 
	//legge per registro operativo1
	//reg op 2 ecc
	end
	S1 : //ecc
	...
	endcase
```
# Immagine Riepilogativa
![[immagine riepilogativa sintesi pc-po.png]]
