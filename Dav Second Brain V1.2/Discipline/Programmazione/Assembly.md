#uni 
link utili: [[ascii]], [[Schema del Calcolatore]], [[Note sull'Architettura Intel-AMD a 64bit]] 
Si può dire anche Assembler.
Questo è il linguaggio in cui si scrivono direttamente le istruzioni eseguite dal processore.
Il processore ciclicamente:
1. preleva un'istruzione macchina dalla memoria (___fetch___)
2. la esegue
La memoria contiene zeri ed uno, assembly è una sintassi simbolica per il linguaggio macchina, che è zeri ed uno.
Il passaggio dall'assembly al LM (linguaggio macchina) si chiama ___assemblaggio___, fatto da un ___Assemblatore___, che è diversa dalla compilazione ([[Compilazione e Linking]]).
In Assembly mancano costrutti di controllo di flusso strutturato tipici dei linguaggi di alto livello, come [[C++]], (for, while, do...).
Gli unici controlli (primitivi) di flusso in assembly sono i ___Salti___. Mancano i tipi di variabile, gli operandi sono stringhe di bit.
L'assembly è processor-specific, noi vedremo quello per Intel x86 a 32bit (facilmente passabile a 64bit). Sono sempre validi i principi generali. Il manuale di Assembly Intel x86 è di circa 2000 pagine.
# Codifica Macchina e Codifica Mnemonica
La codifica macchina è una serie di 0 e 1 che codificano le istruzioni per il processore
La codifica Mnemonica è un modo simbolico di scrivere quella serie di 0 e 1
L'[[Assembly]] usa codifica Mnemonica delle istruzioni, e dispone di una serie di sovrastrutture sintattiche.
Questo è il formato macchina:

| I prefix |     | Opcode | Mode | SIB | Displacement | Immediate |
| -------- | --- | ------ | ---- | --- | ------------ | --------- |
| 0/1 byte | 0/1 | 1/2    | 0/1  | 0/1 | 0/4          | 0/4       |
è irrilevante, noi scriveremo `MOV %EAX, 0x01F4E39A` e l'assemblatore traduce in macchina secondo regole che non abbiamo bisogno di conoscere.
Ancora meglio invece di un indirizzo possiamo usare un simbolo a nostro piacimento, per esempio `pippo`-> `MOV %EAX, pippo` e l'assemblatore traduce nell'indirizzo.
# Istruzioni in codifica Mnemonica
Una istruzione conta 3 campi:
1. ___codice operativo___: operazione eseguita
2. ___suffisso di lunghezza___: quanto sono lunghi gli operandi, può essere omesso in casi in cui
3. ___operandi___ dell'istruzione
```Assembly
OPCODEsuffix source, dest
	ADD %BX, pluto
``` 
gli operandi possono essere contenuti in registri, celle di memoria, porte di I/O, direttamente nell'istruzione come costanti.
Le istruzioni ammettono zero, uno o due operandi.
1. 2: il primo è sorgente il secondo è destinatario, devono essere della stessa lunghezza salvo casi rari
   - il sorgente non è modificato
   - il destinatario viene sostituito con risultato
2. 1: può essere sorgente o destinatario, è chiaro dal contesto
Le istruzioni possono essere:
1. operative: svolge compito
2. di controllo: altera il flusso: __JMP___, ___J___ + controllo dei flag (si salta o meno in base al contenuto di un flag)
# Programma Assembly
Un programma Assembly è diviso in:
- Sezione dati
  - dichiarazione di variabili
    le variabili sono nomi simbolici per indirizzi di memoria
- sezione codice
  - istruzioni
Un programma contiene:
- direttive (per assemblaggio e dichiarazione variabili)
- istruzioni
Alcune note sintattiche:
- ogni direttiva occupa una riga, terminata da CR (ritorno carrello)
- ANCHE l'ultima riga deve essere terminata da CR
- assembly è case insensitivi per le keyword
- assembly è case sensitivi per i simboli definiti dall'utente
- una riga di codice è come segue: 
```assembly
nome: KEYWORD operandi #commento [\CR]

```
	può mancare tutto tranne il ritorno carrello
ESEMPIO:
```assembly
.GLOBAL _main
.DATA
dato: .LONG 0x0F..
conteggio: .BYTE 0x00

.TEXT
_main: NOP
	MOV
	ecc
comp: CMP $0x00, %EAX
	ecc
fine: MOV %CL, conteggio
	RET
```
# Direttive
`.KEYWORD operandi`
### Dichiarazione variabili:
- `.BYTE` riserve 1 byte
- `.WORD`
- `.LONG`
caldo consiglio: quando dichiari mettici anche il valore, l'assemblatore in mancanza di valore DOVREBBE INIZIALIZZARE a zero, ma non fidarti, usa .FILL
Variabili dichiarate di seguito nella sezione dati sono consecutive in memoria.
Per caratteri speciali (ritorno carrello, tabulazione ecc) si usano le stessa sequenze di escape di [[C++]].
Esempi:
```assembly
var1: .BYTE 0x30 #scalare, valore 0x30
var2: .BYTE 0x30, 0x31 #vettore, 2 componenti da un byte
var3: .WORD 0x1020, 0x32AB #vettore, 2 componenti da 2 byte
var4: .LONG var3+2 #scalare, 4 byte
```
##### FILL
`.FILL numero, dim, espressione`
Dichiara numero variabili di lunghezza dim e le inizializza ad espressione (default 0)
- dim può essere 1,2,4 (byte)
Viene anche usato per NON inizializzare una variabile
##### Codifiche ASCII
`var5: .BYTE 'carattere'`
`var6: .ASCII "messaggio"` vettore, 9componenti da 1 byte
`var7: .ASCIZ "messaggio"` vettore, 10 componenti da 1 byte, termina con \0 (NUL)
### Altre Direttive
`.INCLUDE "path"`
- include un file sorgente nel presente file
- l'assemblatore assembla un file unico contentente il codice di entrambi, si mette in genere in cima o in fondo.
`.SET nome, espressione`
- crea costanti simboliche, tali costanti hanno nome ed il valore espressione:
- per misurare peso di un programma posso fare:
  `.SET occupazione, (foo-dato1)`
  `...`
  `MOV $occupazione, %ECX`
# Costanti Numeriche
- naturali: non hanno segno e vengono convertire nella loro rappresentazione in base 2 [[Rappresentazione in Complemento a 2]].
- intere: hanno un segno davanti e vengono convertire in 2C
- i numeri possono essere scritti in base 2,8,10,16
	- 2: preceduti da 0b
	- 8: cominciare con 0
	- 10: non devono cominciare con 0
	- 16: preceduti da 0x
Quando non sono delle dimensioni giuste vengono:
- troncate se troppo lunghe e l'assemblatore ve lo dice
- estese, assemblatore non ve lo dice
# Controllo di Flusso
I csotrutti di controllo di flusso devono essere implementati in termini di istruzione di salto:
- if then else
  slide
- for
```assembly
	MOV $0, %CX
ciclo: CMP var, %CX
	JE fuori
	istruzioni
	INC %CX
	JMP ciclo
fuori: ...
```
- do while
  come for ma controllo in cima
### LOOP
```assembly
	MOV $5, %ECX
ciclo: istuzioni
	LOOP ciclo
```
decrementa ECX e salta se ECX ≠ 0
ECX va inizializzato al numero di iterazioni desiderate, se non viene modificato il valore di ECX durante il LOOP.
Se si vuole utilizzare la "i" durante il ciclo conviene azzerare EBX ed incrementarlo ad ogni interazione del ciclo.
##### LOOP condizionali
Hanno senso solamente dopo una compare:
LOOPE
LOOPNE
Il salto avviene se:
1. la condizione è vera
2. dopo il decremento di ECX a 0
# Sottoprogrammi e passaggio dei parametri
CALL e RET non prevedono passaggio di parametri o valori.
È necessario stabilire delle convenzioni e rispettarle:
1. usare locazioni di memoria condivise
2. usare registri
3. usare la pila:
   così fanno i compilatori ma è difficile a farsi a mano
La memoria principale è indirizzabile da qualunque sottoprogramma.
Quando si scrive un sottoprogramma si DEVE specificare i parametri di ingresso e di uscita tramite commenti.
```assembly
# sottoprogramma "nome", [descrizione]
# ingresso: %AX, [desc]
# uscita: %CX, [dscr]
```
I registri che non contengono valori di ritorno NON DEVONO essere sporcati da un sottoprogramma.
I registri che un sottoprogramma utilizza DEVONO essere salvati in pila e ripristinati alla fine.
### Salvare Registri in Pila
Ci sono registri che vengono sporcati da operazioni avendo operandi impliciti, esempio (E)DX.
La pila va lasciata in ordine, per ogni PUSH ci deve essere un POP, nell'ordine inverso, altrimenti quando la RET preleva dalla pila l'indirizzo di ritorno ci trova valori senza senso e il programma si ferma.
### Sottoprogramma principale
Il `_main ` va in esecuzione come sottoprogramma e quindi deve terminare con una RET, chi lo chiama si aspetta un valore di ritorno in %EAX (0=tutto ok).
# Dichiarazione dello Stack
Lo stack esiste e funziona correttamente se qualcuno lo dichiara e si inizializza %ESP.
Bisogna riservare abbastanza memoria ed %ESP va inizializzato alla cella successiva al fondo dello Stack.
```assembly
.Data
...
mystack: .FILL 1024, 4 #dichiarazione stack

.TEXT
_main: NOP
	MOV $initial_esp, %ESP #inizializzazione dello stack
```
Nel nostro ambiente non serve dichiararlo
# Ingresso/Uscita
Per fare questo nell'ambiente c'è un sottoprogramma apposta, va incluso il file utility con la direttiva: `.INCLUDE "./files/utility.s"` 
Alcuni sottoprogrammi di I/O
1. inchar: mette in AL la codifica ASCII del tasto premuto, non fa eco a video
2. outchar: mette sul video la codifica ASCII contenuta in AL
3. newline: va a capo, stampa i caratteri 0x0D (ritorno carrello) e 0x0A (line feed), servono entrambi
4. pauseN: mette in pausa il programma e stampa sul video:
   `Checkpoint number N. Press any key to continue`, dove $N$ deve essere una cifra decimale.
In [[Assembly]] non esistono istruzioni di ingresso/uscita, esistono solo IN e OUT su interfacce, ma sono privilegiate.
I/O tastiera/video si usano servizi del Sistema ([[DOS]]), che sono sottoprogrammi scritti da altri che girano in modalità sistema. Sono primitivi, ingresso/uscita di UN solo carattere.
Per fare ingresso da tastiera di un numero naturale a 2 cifre in base 10:
1. leggo e memorizzo due codifiche ASCII: $C_1, C_0$
2. calcolo le singole cifre decimali $a_1, a_0$ a partire dalle codifiche
3. ricostruisco il numero digitato come $10a_1+a_0$ 
### Ingresso/Uscita di caratteri e stringhe
Nel nostro ambiente devi includere il file utility con la direttiva:
`.INCLUDE "./files/utility.s"`
1. inline: consente di portare una stringa di max 80 caratteri in un buffer di memoria digitando da tastiera con eco su video
   - parametri di ingresso: EBX: indirizzo di memoria del buffer, CX: numero di caratteri da leggere (max 80)
    la lettura da tastiera termina dopo 78 caratteri o se premete invio, vengono aggiunti in doa al buffer i caratteri LF 0x0A e CR 0x0D
    il sottoprogramma interpreta backspace come ordine di cancellare dal buffer e dal video l'ultimo carattere digitato
2. outline: stampa a video max 80 caratteri, si ferma prima se trova un carattere di ritorno carrello, stampando anche i caratteri necessari ad andare a capo.
   parametri di ingresso: EBX indirizzo di memoria del buffer.
3. outmess: parametri di ingresso EBX indirizzo memoria buffer, CX numero di caratteri da stampare a video.
### Ingresso/Uscita di numeri esadecimali
- inbyte, inword, inword:
  prelevano da tastiera con eco a video 2,4 o 8 caratteri da tastiera e mettono in AL, AX, EAX il numero esadecimale digitato, ignorano qualunque altro carattere che viene premuto.
### Ingresso/Uscita di numeri decimali
- indecimal_byte, indecimal_word, indecimal_long:
  prelevano ta tastiera con eco a video fino a 3,5,10 cifre decimali e lo mettono in Al, AX, EAX. Ignorano qualunque altro carattere premuto, se il numero è troppo grande viene troncato, si può premere invio per dare in ingresso meno di 3,5,10 cifre.
- outdecimal_byte/word/long
  stampano su video il contenuto di AL, AX, EAX interpretato come naturale sul numero di cifre strettamente necessario.
# Indirizzamento delle istruzioni operative
`OPCODEsize source, destination`
1. OPCODE = codice operativo (MOV, CMP)
2. Size: B(byte), W(word), L(long o doublelong), può essere omesso se chiaro dal contesto
3. source e destination, indicati tramite indirizzo o nome di registro.
### Indirizzamento di Registro
Uno tra: 
- 8 registri generali a 32 bit: (EAX, EBX, ECX, OX, EBP, ESI, EDI, ESP)
- 8 reg gen a 16 bit: (AX, BX, CX, DX, Sl, Dl, SP, BP)
- 8 reg gen a 8 bit: (AH, BH, CH, DH, AL, BL, CL, DL)
Si applica sia a sorgente che al destinatario, vanno indicati tramite `%`, esempio: `OPCODE %EAX` 
[[Schema del Calcolatore#Registri]] 
### Indirizzamento Immediato
Solo per operando sorgente
`OPCODE %0x20, %AL` 8bit
`OPCODE %0x564B43E3, %ECX` 32bit
### Indirizzamento di Memoria 
Sorgente oppure Destinatario (non entrambi), è necessario specificare un indirizzo di memoria a 32bit e quindi per muovere memoria deve passare dal processore.
Caso generale: $indirizzo = |base+indice\cdot scala \pm displacement | modulo2^{32}$ ovvero si prende solo i 32bit più bassi e il resto si butta.
base = registro generale a 32bit
displacement = costante intera
scala = 1 di default, 2, 4, 8
Sintassi: `OPCODEsuf +- disp(base, indice, scala)` 
###### Indirizzamento di memoria di tipo diretto
Utilizzo unicamente il displacement, che coincide con l'indirizzo
`OPCODEW 0x000020001` 
L'operando è a 16bit (Word), che si trova nella doppia locazione cui indirizzo più basso è 0x000020001.
###### Indirizzamento di memoria di tipo indiretto/registro puntatore
`OPCODEL (%EBX)` 
LE PARENTESI SONO COME OPERATORE DI DEREFERENZIAZIONE.
Operando a 32 bit, cui primo indirizzo è indicato in EBX. Utilizza la base, che è il primo indirizzo.
`OPCODE (,%ESI,4)`
con 4 scala, moltiplichi indirizzo e moltiplichi per scala.
Attenzione moltiplica l'Indice!!, che è il secondo indirizzo, non la base.
###### Indirizzamento con displacement e registro di modifica
`OPCODEW 0x002A3A2B (%EDI)`
operando a 16bit, indirizzo si ottiene sommando il displacement 0x002A3A2B e il contenuto di EDI, e facendo il modulo $2^{32}$ .
###### Indirizzamento bimodificato senza displacement
`OPCODEW (%EBX, %EDI)`
`OPCODEW (%EBX, %EDI, 8)`
###### Indirizzamento bimodificato con displacement
`OPCODEB 0x002F9000 (%EBX, %EDI, 2)` 
L'operando è a 8bit e si trova nella locazione il cui indirizzo vale:
$base \ in \ EBX + indice \ in \ EDI + 0x002F9000|modulo2^{32}$ 
Il displacement può anche essere negativo, in quel caso ovviamente viene sottratto.
##### Indirizzamento delle porte I/O
Uno dei due operandi può trovarsi nello spazio di I/O
Per indirizzi <256 possiamo usare indirizzamento diretto (cuz nel formato macchina ci sono 8bit).
Si può usare indirizzamento indiretto con registro puntatore, ma questo deve essere per forza DX!
```
IN 0x001A, %AL
IN (%DX), $AX
OUT %AL, 0x003A
OUT %AL, (%DX)
```
### Note sulla sintassi
- Gli operandi immediati/le costanti vanno preceduti dal dollaro `$` 
- i registri vanno preceduti dal simbolo percentuale %
- in una istruzione un numero non preceduto dal dollaro è un indirizzo di memoria (indirizzamento diretto)
# Principali Istruzioni
Istruzioni Operative:
1. di trasferimento
2. aritmetiche
3. di traslazione/rotazione
4. logiche
Istruzioni di controllo:
1. di salto
2. per la gestione di sottoprogrammi
Per ogni istruzione descriviamo:
- il formato/sintassi
- cosa fa
- se aggiorna i flag, quali e come
- quali sono le modalità di indirizzamento ammesse per gli operandi.
### MOVE
- memoria <-> registro
- registro -> registro
- I/O <-> registro
NON ESISTE memoria <-> memoria
- FORMATO: `MOV source, destination`
- AZIONE: sostituisce operando destinatario con una copia dell'operando sorgente
- FLAG modificati: nessuno

| Operandi                             | Esempi               |
| ------------------------------------ | -------------------- |
| Memoria, registro generale           | MOV 0X00002000, $EDX |
| registro generale, memoria           | MOV %CL, 0X12AB1024  |
| registro generale, registro generale | MOV %AX, %DX         |
| immediato, memoria                   | MOVB $0X5B, (%EDI)   |
| Immediato, registro generale         | MOV $0X54A3, %AX     |

### LOAD EFFECTIVE ADDRESS
- FORMATO: `LEA source, destination`
- AZIONE: sostituisce contenuto di operando destinatario con espressione indirizzo contenuta nell'operando sorgente
- FLAG modificati: nessuno

| Operandi                            | Esempi                               |
| ----------------------------------- | ------------------------------------ |
| memoria, registro generale a 32 bit | LEA 0x00002000, %EDX                 |
|                                     | LEA 0x00213AB1 (%EAX, %EBX, 4), %ECX |
### Exchange
- FORMATO: `XCHG source, destination`
- AZIONE:  scambia contenuto degli operandi
- FLAG nessuno

| Op               |     |
| ---------------- | --- |
| memoria, reg gen |     |
| reg gen, mem     |     |
| reg gen, reg gen |     |
### INPUT
- FORMATO
  1. `IN indirizzo, %AL` 8bit
  2. `IN indirizzo, %AX` 16bit
  3. `IN (%DX), %AL/AX` 
- AZIONE: sostituisce contenuto del registro destinatario con il contenuto di un adeguato numero di porte consecutive. Come al solito indirizzamento diretto solo utilizzabile con porte con indirizzo inferiore a 256
- FLAG nessuno
### OUTPUT
- FORMATO
  1. `OUT %AL, indirizzo` 8bit
  2. `OUT %AX, indirizzo` 16bit
  3. `OUT %AL/AX, (%DX)` 
- AZIONE: copia il contenuto del registro sorgente in un adeguato numero di porte consecutivi
- FLAG nessuno
### INPUT, OUTPUT, non ortogonalità
Queste sono le uniche due istruzioni che riguardo l' I/O.
Non Ortogonalità: se posso fare qualcosa con un registro generale non vuol dire che possa farlo anche con altri registri.
Utilizzano solamente AL e AX come sorgente/destinatario e DX come registro puntatore
# La Pila (Stack)
Questa è una zona di memoria gestita LIFO.
Serve a poter annidare sottoprogrammi, l'assembly è organizzato per sottoprogrammi.
Prima di saltare ad un sottoprogramma mi "salvo" l'indirizzo di ritorno, (quello della prossima istruzione), nella pila (___PUSH___).
Al termine del sottoprogramma, per tornare dove ero, faccio una ___POP___ dalla pila.
```
Programma principale

codice
chiamata sottoprogramma
	sottoprogramma
	
	codice
	ritorno al chiamante
prima istruzione di ritorno
codice
```
ESP serve come puntatore al top della pila, quindi NON va usato per altri scopi.
- PUSH valore
	- decrementa ESP
	- copia valore in (%ESP)
- POP destinatario
	- copia (%ESP) in destinatario
	- incrementa ESP
ESP va inizializzato prima che parta il programma.
### PUSH
- FORMATO `PUSH source`
- AZIONE salva nella pila corrente una copia dell'operando sorgente (deve essere 16 o 32 bit).
  1. decrementa l'indirizzo contenuto nel registro ESP di 2 o di 4
  2. memorizza una copia dell'operando sorgente nella doppia o quadruple locaizone il cui indirizzo è contenuto in ESP
- FLAG nessuno

| Op                | Es                |
| ----------------- | ----------------- |
| memoria           | PUSHW 0X3214200A  |
| immediato         | PUSHL $0X4871A000 |
| registro generale | PUSH %BX          |

### POP
- FORMATO `POP destination`
- AZIONE rimuove dalla pila corrente una word o un long e la inserisce nell'operando destinatario
  1. inserisce nel destinatario una copia del contenuto della doppia o quadrupla locazione il cui indirizzo è contenuto in ESP
  2. incrementa di 2 o 4 l'indirizzo contenuto in ESP, rimuovendo in tal modo dalla pila la word/long copiato
- FLAG nessuno

| op                | es              |
| ----------------- | --------------- |
| memoria           | POPW 0x02AB2000 |
| registro generale | POP %BX         |

## La pila come memoria temporanea
Siccome abbiamo pochi registri generali, possiamo "parcheggiare" i dati in pila
Esempio:
Sto usando EAX ma mi serve un dato da una porta
```Assembly
PUSH %EAX
IN 0x001A, %AL
...
POP $EAX                 #riprendo i conti che stavo facendo
```
#### PUSHAD/POPAD
- FORMATO `PUSHAD` 
- AZIONE salva nella prila corrente una copia del contenuto degli 8 registri generali a 32bit in questo ordine:
  EAX, ECX, EDX, EBX, ESP, EBP, ESI, EDI
- FLAG nessuno

- FORMATO `POPAD` 
- AZIONE: rimuove dalla pila 8 long e con essi rinnova il contenuto degli 8 registri generali a 32bit, nell'ordine inverso della PUSHAD
- FLAG nessuno
# Istruzioni Aritmetiche
Alcune considerano gli operandi indifferentemente come naturali e come interi (per esempio la somma).
Modificano i flag, CF per naturali, SF/OF per interi ([[Schema del Calcolatore#Registri]]).
Il programmatore è l'unico che sa cosa sta scrivendo.
### ADD
- FORMATO `ADD source, destination`
- AZIONE modifica operando destinatario sommandovi l'operando sorgente.
- FLAG: CF = 1 se interpretando come naturali si ha un riporto -> da negativo siamo arrivati a positivo. OF = 1 se interpretando come interi si ha un riporto -> overflow.
  La ADD mette OF = 1 se 1. gli operandi sono concordi; 2. il risultato è discorde dagli operandi
  ZF = 1 se tutto 0
  SF <- MSB, in C2 rappresenta il segno.

| Operandi                   | Esempi               |
| -------------------------- | -------------------- |
| memoria, reg gen           | ADD 0x0002000, %EDX  |
| reg gen, mem               | ADD %CL, 0x12AB1024A |
| reg gen, reg gen           | ADD %AX, %DX         |
| valore immediato, memoria  | ADDB $0X5B, (%EDI)   |
| valore immediato, registro | ADD %0x54A3, %AX     |

### INCREMENT
- FORMAT `INC destination` 
- AZIONE equivale ad `ADD $1, destination` solo che non modifica flag CF
- FLAG: OF, SF, ZF

| op           |             |
| ------------ | ----------- |
| memoria      | INCB (%ESI) |
| reg generale | INC %CX     |
### SUBTRACT
- FORMAT `SUB source, destination`
- AZIONE come ADD
- FLAG se con naturali CF = 1 sottrazione sbagliata, se con interi OF = 1 sbagliata
	- se su naturali: CF = 0: la differenza è naturale; CF = 1: la differenza non è un naturale
	- se su interi: la differenza di numeri concordi è sempre rappresentabile, differenza di numeri discordi è rappresentabile solo se il risultato ha il segno del minuendo.
	  OF = 0: fattibile
### DECREMENT
- FORMAT `DEC destination`
- AZIONE equivale a `SUB $1, destination` solo che non modifica carry flag
- FLAG: OF, SF, ZF
### ADD WITH CARRY
- FORMAT `ADC source, destination`
- AZIONE come ADD ma aggiunge anche contenuto di CF
- FLAG tutti
serve a fare somme di operandi a molti bit.
Esempio voglio sommare due operandi a 64 bit, ma il sistema accetta solo operandi a 32bit.

| ADC      | ADD      |     |
| -------- | -------- | --- |
| 56A9C2D4 | 67A43B5F | +   |
| 44B9A5A4 | A6B4C55A | =   |
| 9B636870 | 0E5900B9 |     |
Uso la ADD per i 32bit meno significativi, questa potrebbe generare un riporto; Uso ADC per i 32bit più significativi, sommando anche il riporto.
### SUBTRACT WITH BORROW
- FORMATO `SBB source, destinatio`
- AZIONE come ADC
- FLAG tutti
### NEGATE
- FORMATO `NEG destination`
- AZIONE intepretando operando come intero, lo sostituisce con il suo opposto, se non è possibile setta OF = 1 (se operando iniziale è estremo negativo). Mette CF = 1 eccetto quando operando è zero, in tal caso CF = 0
  insomma complementa bit a bit il destinatario e aggiunge uno
- FLAG tutti

| operandi          | esempio |
| ----------------- | ------- |
| memoria           |         |
| registro generale |         |
### Compare
- FORMATO: `CMP source, destination`
- AZIONE verifica se operando destinatario è maggiore, uguale o minore della sorgente
  1. `null = dest - source`
  2. `aggiorna flag come farebbe la SUB`
- FLAG
### Moltiplicazioni e divisioni
Sono diverse per naturali e interi:
- `MUL` o `IMUL`
- `DIV` o `IDIV`
Il prodotto di due numeri a N cifre sta su 2N cifre. Quindi non ha senso usare un operando sia come fattore che come contenitore del risultato, servono 3 operandi.
#### Moltiplicazione
Ha sia un operando che il destinatario impliciti.
- 8bit: AX = AL * source
- 16bit: DX_AX = AX * source
- 32bit: EDX_EAX = EAX * source
parte alta su DX, bassa su AX
alta su EDX, bassa su EAX
È il programmatore a scegliere, in base alla dimensione della source.
- FORMATO `MUL source` / `IMUL source`
- AZIONE considera sorgente come un moltiplicando e il destinatario (implicito) come un moltiplicatore, interpretando come naturali/interi
- FLAG: CF e OF messi a 1 se il risultato non sta sul numero di bit del source
#### Divisione
Oltre ai problemi della moltiplicazione, ci serve un posto per il resto e l'operazione può non essere fattibile (divido per 0).
$X div Y \to Q,R$ 
$0 \leq R \leq Y-1$
$0 \leq Q \leq X$ 
Ci sono 3 divisioni:
- 8bit: AL = quoziente(AX/source) ; AH = resto
- 16bit: AX = quoziente(DX_AX/source) ; DX =resto
- 32bit: EAX = quoziente(EDX_EAX/source) ; EDX = resto
stiamo cercando di mettere il quoziente su un numero di bit che è metà del necessario, se effettivamente sfora, abbiamo una ___Eccezione___, e il programma si inchioda. DA EVITARE.
Voglio dividere 15000 per 3, quale scelgo?
15000 sta su 16bit
3 sta su 8bit
se scegliamo 8bit si inchioda, dobbiamo usare la divisione su 16bit:
```assembly
MOV $3, %CX
MOV $15000, %AX
MOV %0, %DX       #NONSCORDARE DI PULIRE DX
DIV $%X
```
Codice: 
- FORMATO `DIV source` 
- AZIONE considera sorgente come divisore e operando destinatario(implicito) come un dividendo, interpretando come naturali.
  1. 8bit : divide Ax per il sorgente, mette il quoziente in AL ed il resto in AH
  2. 16bit : divide DX_AX per sorgente, quoziente in AX e resto in DX
  3. 32bit : divide EDX_EAX per sorgente, mettendo quoziente in EAX e resto in EDX
- FLAG
#### INTEGER DIVIDE
- FORMATO `IDIV source(che è il divisore)`
- AZIONE interpreta come numeri interi
- FLAG tutti ma non in modo attendibile
nella divisione intera:
- il resto ha sempre il segno del dividendo e è in modulo minore del divisore.
Il quoziente viene sempre approsimato all'intero più vicino allo zero (approssimazione per troncamento).
#### Note conclusive su moltiplicazione e divisione
Bisogna scegliere con cura la versione.
Ricordarsi di azzerare ___DX/EDX___ prima della divisione, se è a più di 8bit, altrimenti i risultati non tornano.
Il contenuto di DX/EDX viene modificato da moltiplicazione/divisione a più di 8bit.
### ESTENSIONE DI CAMPO
Per i naturali è banale: basta aggiungere zeri in testa
Per gli interi si deve ripetere il bit più significativo:
- 100110 -> 1100110
- 011011 -> 0011011
### CONVERT WORD TO DOUBLEWORD IN EAX
- FORMATO `CWDE`
- AZIONE interpreta AX come un numero intero a 16bit e lo rappresenta su 32bit e lo memorizza in EAX
- FLAG nessuno
### TRASLAZIONE/ROTAZIONE
Servono a variare l'ordine dei bit in un operando destinatario.
Hanno due formati:
- `OPCODE src, dest`
- `OPCODE dest`
dove src è il numero di ripetizioni e può essere: 
- immediato oppure registro CL
- massimo 31
- se omesso vale 1

|             | sx  | dx  |
| ----------- | --- | --- |
| traslazione | SHL | SHR |
|             | SAL | SAR |
| rotazione   | ROL | ROR |
|             | RCL | RCR |
#### SHIFT LOGICAL LEFT
- FORMATO `SHL source, destination` oppure senza source 
- AZIONE interpreta sorgente come un naturale $n$ e per $n$ volte sostituisce il bit contenuto in CF e ciascun bit dell'operando destinatario con il bit immediatamente a destra del contenuto in CF.
  moltiplica per $2^{src}$ la destination.
- FLAG 
#### SHIFT ARITHMETIC LEFT
uguale a shift logical left
#### SHIFT LOGICAL RIGHT
- FORMATO `SHR source, destination` oppure senza source
- AZIONE 
  divide destination per $2^{src}$, approssimando il quoziente per DIFETTO, sempre verso sinistra (non verso zero come IDIV) (destination intepretato come naturale!!!)
- FLAG
#### SHIFT ARITHMETIC RIGHT
- FORMATO `SAR source, destination` o senza source
- AZIONE
  fa quasi la stessa cosa della SHR ma opera sugli interi, invece di aggiungere zeri allo MSB, ripete il MSB.
- FLAG
#### SAR e DIV
IDIV approssima per troncamento, verso lo zero
DIV approssimano sempre a sinistra
Quindi danno lo stesso quoziente solo se:
- dividendo è positivo
- divisione dà resto nullo
#### ROTAZIONE
Uguale alla traslazione il bit che aggiunge dipende: 
- in ROL e ROR non include CF, riprende il bit che esce
- in RCL e RCR include il CF

| ope                |     |
| ------------------ | --- |
| immediato, reg gen |     |
| immediato, mem     |     |
| CL, reg gen        |     |
| CL, mem            |     |
| mem                |     |
| reg gen            |     |
### Istruzioni Logiche
Applicano operatori dell'algebra di bool, in genere modificano i flag
AND, OR, XOR si possono usare per lavorare su singoli bit di operandi, usando un operando sorgente immediato detto ___maschera___, ovvero una fila di 0 tranne il bit che voglio guardare.
#### NOT
- FORMATO `NOT destination`
- AZIONE inverte i bit di destination
- FLAG nessuno
#### AND
- FORMATO `AND source, destination`
- AZIONE sostituisce ciascun bit dell'operando destinatario con il risultato dell'operazione AND tra il bit stesso e il corrispondente bit della sorgente, mette a 0 il contenuto dei flag CF e OF
- FLAG tutti
1. si usa per testare un certo bit di destination con una mschera (tutti 0 tranne bit)
2. si usa per resettare singoli bit di un operando (tutti 1 tranne bit)
3. si usa per settare singoli bit (tutti 0 tranne bit)
4. si usa per estensione di operandi naturali:
   voglio sommare due naturali, uno in AL e altro in BX
   ```
   MOV $5, %AL
   MOV $100000, %EBX
   AND $0X000000FF, %EAX
   ADD %EAX, %EBX
	```
#### OR
- FORMATO `OR source, destination`
- AZIONE come AND ma con OR
  CF,OF = 0
- FLAG tutti
#### XOR
- FORMATO
- AZIONE come OR ma con 1-1 fa 0
- FLAG
1. si usa per invertire singoli bit usando maschera (tutti 0 tranne bit)
   esempio bit n.5: `XOR $0x20, %AH      #0x20=0010|0000`
2. resettare un registro `XOR %EAX, %EAX` istruzione di un solo byte, mov $0 %eax invece 5 byte.
# Istruzioni di Controllo
Le istruzioni sono in memoria consecutivamente, il processore preleva istruzione, incrementa EIP, la esegue, ripete.
Scorre normale a meno che una istruzione non modifichi EIP ([[Schema del Calcolatore#Registri]])
### JUMP
- FORMATO `JMP %EIP +- displacement`
  `JMP *extended_register`
  `JMP *memory`
- AZIONE calcola indirizzo di salto e lo immette nel registro EIP
- FLAG nessuno
In assembly si usa un nome simbolico per indicare un indirizzo
```assembly
routine: 
JMP routine
```
### JUMP if condition is met
- FORMATO `Jcon %EIP +- displacement`
- AZIONE controlla contenuto dei flag
- FLAG
#### Condizioni
###### Condizioni flag

| JZ/JNZ | zero, ZF = 1 (risultato di istruzione precedente = 0) |
| ------ | ----------------------------------------------------- |
| JC/JNC | carry, CF = 1                                         |
| JO/JNO | overflow, OF = 1                                      |
| JS/JNS | sign, SF = 1                                          |
###### Condizioni numeri naturali

| JE  | =   | equal, ZF = 1, dopo CMP dest = sorg                    |
| --- | --- | ------------------------------------------------------ |
| JNE | !=  | not equal, ZF = 0, dopo CMP dest != sorg               |
| JA  | >   | above, CF = 0 e ZF = 0, dopo CMP dest > sorg           |
| JAE | >=  | above or equal, CF = 0, dopo CMP dest >= sorg          |
| JB  | <   | below, CF = 1, dopo CMP dest < cmp                     |
| JBE | <=  | below or equal, CF = 1 e ZF = 1, dopo CMP dest <= sorg |
###### Condizioni numeri interi

| JE  | =   | equal, ZF = 1                         |
| --- | --- | ------------------------------------- |
| JNE | !=  | not equal, ZF = 0                     |
| JG  | >   | greater, ZF = 0 e SF = OF             |
| JGE | >=  | greater or equal, SF = OF             |
| JL  | <   | less, SF != OF                        |
| JLE | <=  | less or equal, ZF = 1 oppure SF != OF |
# Sottoprogrammi
Coinvolge due comandi: CALL e RET, chiamano un sottoprogramma e ritornano al programma chiamante, entrambe fanno riferimento alla pila.
### CALL
- FORMATO `CALL %EIP +- $displacement`
  `CALL *extendedregister`
  `CALL *memory`
- AZIONE salva nella pila corrente il contenuto del registro EIP e poi modifica il suo contenuto in modo del tutto simile alla JMP
- FLAG nessuno
### RETURN
- FORMATO `RET`
- AZIONE rimuove un long dalla pila e con esso rinnova il contenuto di EIP
- FLAG nessuno
# Miscellanous
### NO OPERATION
- FORMATO `NOP`
- AZIONE niente
- FLAG nessuno
### Halt
- FORMATO `HLT` 
- AZIONE cessa ogni attività del processore
# Istruzioni Privilegiate
Il processore funziona in due modalità: utente e sistema, in sistema può usare tutte le istruzioni.
Tra le istruzioni privilegiate troviamo: 
- HLT
- IN
- OUT
se ne cerchiamo di utilizzare uno in modalità utente va in esecuzione una eccezione di protezione, diversa da sistema a sistema.
# Istruzioni sulle stringhe
## Manipolazione
In [[Assembly]] non esistono tipi dato ne strutture dati, esistono solo byte, word, long.
Supporta però il concetto di vettore:
dichiarazione di vettore di variabile di una certa dimensione:
- indirizzamento con displacement + registri base/indice
Le istruzioni stringa servono a copiare interi buffer di memoria e usano i registri %ESI, %EDI come puntatori (S: source, D: destination).
### MOVE DATA FROM STRING TO STRING (with repeat)
- FORMATO `MOVSsuf`
- AZIONE copia il numero di byte specificato dal suffisso dall'indirizzo di memoria puntato da ESI all'indirizzo di memoria puntato da EDI. Se DF=0 somma ad ESI e ad EDI il numero di byte specificato dal suffisso, se DF=1 sottrae da ESI e da EDI.
  Se viene premesso il prefisso REP, allora le azioni indicate sopra vengono ripetute per il numero di volte specificato in ECX, che viene decrementato fino a zero.
- FLAG nessuno
### Altre istruzioni
`LODSsuf` copia in AL, AX o EAX a seconda del suffisso il contenuto della memoria all'indirizzo puntato da ESI. A seconda di DF incrementa o decrementa ESI di 1,2,4.
`STOSsuf` copia il registro AL, AX, EAX in memoria all'indirizzo puntato da EDI. A seconda di DF incrementa o decrementa EDI di 1,2,4.
OI registri usati come puntatore implicito sono differenti: ESI come sorgente ed EDI come destinatario. 
## Istruzioni Stringa per l'I/O
`INSsuf` fa ingresso di 1,2,4 byte dalla porta di I/O il cui offset è contenuto in DX. L'operando viene inserito in memoria a partire dall'indirizzo di memoria contenuto in EDI. A seconda di DF incrementa/decrementa EDI di 1,2,4.
`OUTsuf` copia 1,2,4 byte contenuti in memoria a partire dall'indirizzo di memoria contenuto in ESI, alla porta di I/O il cui offset è contenuto in DX. A seconda di DF incrementa/decrementa ESI di 1,2,4.
## COMPARE STRING
`CMPSsuf` confronta il contenuto delle (1,2,4) locazioni indirizzate da ESI (sorgente) ed EDI (destinatario). A seconda di DF incrementa/decrementa ESI e EDI di 1,2,4.
## SCAN STRING
`SCASsuf` confronta il contenuto del registro AL,AX, EAX (suffisso) con la locazione (sing, doppia, quad) di memoria indirizzata da EDI, con lo stesso algoritmo della CMP. A seconda di DF incrementa/decrementa EDI di 1,2,4.
# Prefissi di Ripetizione
`REP` può essere usato con MOVS, STOS, INS, OUTS e LODS(non ha senso).
`REPE`/`REPNE` può essere usato con CMPS e SCAS, si fanno al massimo EcX ripetizioni finché la condizione specificata è vera.