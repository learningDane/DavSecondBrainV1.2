#uni 
Una rete combinatoria è caratterizzata da:
1. un insieme di $N$ variabili logiche di ingresso 
2. un insieme  di $M$ variabili logiche di uscita.
3. una descrizione funzionale $F : X \to Z$ che mappa stati di ingresso in stati di uscita
4. una legge di evoluzione nel tempo, che dice continuamente se $X$ è lo stato di ingresso presente, adegua lo stato di uscita di $F(X)$.
# Teorema
Data una qualunque tabella di verità a $N$ ingressi, può essere realizzata tramite un ___Multiplexer___ a $N-1$ variabili di controllo. Ne consegue che qualsiasi rete combinatoria può essere realizzata utilizzando solo AnD, OR e NOT e massimo due livelli di logica, come un [[#Multiplexer]].
Questo ci consente di stimare un tempo di attraversamento teorico massimo.
# Tempo di attraversamento
Questo è il tempo di accesso o di risposta, il tempo che ci mette la rete ad adeguare lo stato di uscita al nuovo stato di ingresso, e purtroppo non è nullo.
Si rende necessario attendere che l'uscita sia andata a regime prima di variare ancora lo stato di ingresso.
Questo vincolo si chiama ___pilotaggio in modo fondamentale___.
# Descrizione di una Rete Combinatoria
- Quanti sono gli ingressi
- Quante sono le uscite
- Quale è la funzione $f$, la descrizione funzionale (tabella di verità)
### Tabella di verità
A sinistra dati di ingresso e a destra i dati di uscita a seconda dell'input.

| x2  | x1  | x0  | z1  | z0  |
| --- | --- | --- | --- | --- |
| 0   | 0   | 0   | 0   | 0   |
| 0   | 0   | 1   | 0   | 1   |
| 0   | 1   | 0   | 1   | 0   |
| 1   | 1   | 1   | -   | -   |
La variabile z1 riconosce i seguenti stati di ingresso: ( 0 1 0 )
La variabile z0 riconosce invece: ( 0 0 1 )
Le lineette significano NON DETERMINATO (don't care in inglese).
### Descrizione
Modo formale per dire cosa fa una rete, ovvero il suo comportamento: tabella di verità
### Sintesi
Momento successivo alla descrizione, è il progetto della realizzazione di una rete.
Sfrutta il ___modello strutturale universale per reti combinatorie___.
- Esistono diverse sintesi per la stessa legge combinatoria
- hanno costo diverso in termini di numero di porte
- la riduzione del costo è basata su proprietà algebriche ([[Algebra di Boole]])
- abbiamo bisogno di un metodo formale (quindi algoritmico) per minimizzare il costo della sintesi.
# Teorema 2
Una rete combinatoria ad $N$ ingressi ed $M$ uscite può essere realizzata interconnettendo $M$ reti combinatorie ad $N$ ingressi ed una uscita. Possiamo quindi dividere una rete combinatoria in sottogruppi, tanto dall'esterno è uguale.
# Regole di Pilotaggio
1. ___Pilotaggio in modo fondamentale___: cambiare gli ingressi soltanto quando la rete è a Regime
2. Stati di ingresso consecutivi devono essere adiacenti.
# Reti combinatorie Elementari
Quante sono le reti combinatorie a $N$ ingressi? $2^{2^N}$ .
### Zero ingressi
Generatori di costante (caso degenere).
Si disegnano con sopra il valore della costante.
Vengono realizzate connettendo il filo al polo positivo oppure alla massa per ottenere 0 o 1.
### Un ingresso
- Invertitore: triangolo con pallino: 0->1 ; 1-> 0
- elemento neutro/buffer: triangolo: 0->0 ; 1->1
  può essere usata come rete che perde tempo (tempo di attraversamento) oppure come rete che rigenera un segnale elettrico degradato.
## Decoder
Un decoder $N$ a $2^N$ rende segnale su una determinata variabile di uscite in base alle variabili in entrata.
Esempio tabella di verità 2 a 4:

| x1  | x0  | z0  | z1  | z2  | z3  |
| --- | --- | --- | --- | --- | --- |
| 0   | 0   | 1   | 0   | 0   | 0   |
| 0   | 1   | 0   | 1   | 0   | 0   |
| 1   | 0   | 0   | 0   | 1   | 0   |
| 1   | 1   | 0   | 0   | 0   | 1   |
#### Decoder con Enabler
Questi decoder hanno una variabile di ingresso in più che gli permette di collegarsi ad altri decoder. 
Quando $e = 0$ l'output è $0$, se invece $e=1$ la rete si comporta come un normale Decoder.
Viene realizzato aggiungendo un AND con $e$ a ogni uscita.
## Demultiplexer
Un demultiplexer ha $N+1$ ingressi e $2^N$ uscite, dove un ingresso $x$ si dice variabile da commutare e le altre sono variabili di comando.
Essenzialmente in base alle variabili di comando, il valore di $x$ viene portato su una delle uscite, mentre le altre rimangono a $0$.
generica uscita: $z_0=\begin{cases} x \ \ \ \  (b_{N-1}...b_1b_0) \\ 0 \ \ \ \ altrimenti \end{cases}$ quindi $z_0=x\cdot \overline{b_{N-1}}...\overline {b_1} \overline{b_0}$ 
Un demultiplexer è essenzialmente un [[#Decoder con Enabler]], sono la stessa cosa.
## Multiplexer
Questo ha $N+2^N$ ingressi e $1$ uscita.
Fa il contrario del demultipllexer.
Ha al massimo 2 livelli di logica e utilizza solo AND, OR, NOT.