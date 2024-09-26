#uni 
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
# Le istruzioni
scrivi le istruzioni
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
Sintassi: `OPCODEsfx +- disp(base, indice, scala)` 
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
- AZIONE: sostituisce operando destinatario con espressione indirizzo contenuta nell'operando sorgente
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