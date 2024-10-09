#uni 
Questo è un formalismo per descrivere le reti logiche.
Data Una rete combinatoria posso sempre trovare una espressione booleana che mette in relazione ogni sua uscita con gli ingressi.
Data un'espressione booleana è sempre possibile sintetizzare una rete combinatoria in cui la relaizone tra ignresso ed uscita è data dall'espressione.
Espressioni logiche equivalenti portano a reti logiche che svolgono lo stesso compito.
### Operatori Logici
- Complemento: si indica con $\overline x$ oppure $!x$ oppure $/x$ , inverte il bit.
- Prodotto logico (AND): operatore binario: solo $1\cdot 1 = 1$, il resto 1
- somma logica (OR): op binario: solo $0 + 0= 0$, il resto 1
### Proprietà degli operatori Booleani
- involutiva del complemento: $\overline {\overline x} = x$ 
- commutativa della somma e del prodotto
- associativa della somma e del prodotto
- distributiva della somma rispetto al prodotto e viceversa
  1. $x\cdot (y+z)=(x\cdot y)+(x\cdot z)$ anche nell'algebra standard.
  2. $x+(y \cdot z)= (x+y)\cdot (x+z)$ invece falsa nell'algebra standard.
- complementazione: $\overline x \cdot x = 0 \ ; \ x+\overline x =1$ 
- unione e intersezione:
  $x+0=x \ ; \ x+1=1$
  $x \cdot 0 = 0 \ ; \ x \cdot 1 = x$ 
- idempotenza: $x+x = x \ ; \ x \cdot x = x$ 
- Teroemi di De Morgan
  $\overline {x \cdot y} = \overline x + \overline y$ 
  $\overline {x+y} = \overline x \cdot \overline y$ 
  valgono per $N$ variabili. Si dimostra per Induzione.