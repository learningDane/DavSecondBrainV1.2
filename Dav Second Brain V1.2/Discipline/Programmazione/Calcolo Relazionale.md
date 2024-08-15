#uni 
Questo è una famiglia di linguaggi dichiarativi basati sul calcolo dei predicati del primo ordine. Un altro modo per esprimere query oltre all'[[Algebra Relazionale]].
Si divide in:
- __TRC__: calcolo relaizonale sulle tuple:
- __DRC__: calcolo relazionale sui domini con dichiarazioni di _range_ 
### Calcolo relazionale sui Domini
Le espressioni hanno la seguente forma: $$\{A_1:x_1,...,A_k:x_k|f\}$$
dove:
- $f$ è una formula a partire da formule atomiche, connettivi booleani e quantificatori. Le formule atomiche possono essere di due tipi:
  1.  $R(A_1:x_1,...,A_P:x_p)$ dove $R(A_1,....,A_p)$ è uno _schema di relazione_ e $x_i$ sono variabili
  2. $x\theta y$ oppure $x\theta c$ con $x,y$ variabili, $c$ costante e $\theta$ operatore di confronto
- $A_i$ è un attributo
- $x_i$ è una variabile
- $A_1:x_1,...,A_n:x_n$ è chiamata ___target list___ e descrive il risultato
Il risultato è una relazione su $A_1,...,A_k$ che contiene tuple di valori per $x_1,...,x_k$ che rendono vera la formula $f$ rispetto ad una istanza di base di dati a cui l'espressione è applicata.
	Esempio: Trovare matricola nome degli impiegati che guadagnano più di 40: $$\{ Matr: m, Nome: n| Impiegati(Matr:m,Nome:n,Età:e,Stipendio:s) \land s>40\}$$
	Esempio: Trovare matricola e nome dei capi i cui impiegati guadagnano più di 40: $$\{c,n|Impiegati(c,n,e,s)\land \forall m'\forall n' \forall e' \forall s':Impiegati(m',n',e',s')\land Supervisione(c,m')\land s'>40\}$$
### Calcolo relazionale sulle Tuple
Le espressioni hanno la forma: $$\{T|L|f\}$$
dove:
- $T$ è la _target list_, con elementi del tipo:
  1. $Y:x.Z$
  2. $x.Z\equiv Z:x.Z$ 
  3. $x.*\equiv X:x.X$ 
  4. $x$ è una variabile
  5. $Y,Z$ sono liste di attributi
  6. Gli attributi di $Z$ devono comparire nello schema di relazione che costituisce il campo di variabilità, o ___range___, di $x$ 
- $L$ è la _range list_, che elenca le variabili libere della formula $f$ con i relativi campi di variabilità, o _range_ 
- $f$ è una formula
Con il calcolo sulle tuple non si possono esprimere alcune interrogazioni, per esempio le unioni. Per questo motivo [[SQL]] (che è basato su questo calcolo) prevede un operatore esplicito di unione, ma non tutte le versioni prevedono intersezione e differenza.
	Esempio: Trovare mat, nome, età e stip degli impiegati che guadagnano più di 40: $$\{i,*|i(Impiegati) |i.Stipendio > 40\}$$
	Esempio: trovare mat e nome dei capi i cui impiegati guadagnano più di 40: $$\{Matr,Nome:i'.(Matr,Nome)|i'(Impiegati),s(Supervisione),i(Impiegati)|i'.Matr=s.Capo \land s.Impiegato=i.Matr \landi.Stipendio>40\}$$