#uni 
notazione scientifica: $r = \pm m \cdot \beta^e$
	l'intervallo di rappresentabilità è fissato dal numero di cifre dell'esponente e l'accuratezza è fissata dal numero di cifre della mantissa. 
Rappresentazione di un binario:
	- La mantissa con parte intera è costituita da un solo bit di valore 1
	- La rappresentazione è una tripla costituita da tre numeri naturali
$$r \iff R = ( s,\ E,\ F)$$La rappresentazione R è costituita da 3 naturali, $s,E,F$ dove:
	$s$ = codifica del segno (1 bit)
	$F$ = codifica della parte frazionaria della mantissa su $G$ bit
	$E$ = codifica dell'esponente su $K$ bit $$R = ( s,\ E,\ F)$$$$r = (s==0)?[+(1+f)\cdot due^e]:[-(1+f)\cdot due^e]$$$f = F/2^g$ è la parte frazionaria della mantissa ($m=1+f=1+F/2^G$) 
	$e = +E-(2^{K-1} - 1)$ è l'esponente rappresentato dal numero naturale $E$ ([[Rappresentazione con Bias dei Numeri Naturali]]) 
	Conseguenza dell'uno _implicito_: lo _zero_ non è rappresentabile!
___Half Precision___: 16 bit, K = 5 e G = 10; $max = 0.11111.1111111111 = 2^{17}$; $min = 1.11111.1111111111$;
L'intervallo di rappresentabilità è quindi: $[-2^{bias+2},2^{bias + 2}]$, i numeri con modulo minimo sono: $\pm 2^{-15}$;
___Single Precision___: 32 bit, K = 8, G = 23, massimo modulo: $2^{+129}$, minimo modulo: $2^{-127}$ 
___Double Precision___: 64 bit, K = 11, G = 52, massimo modulo: $2^{+1025}$, minimo modulo: $2^{-1023}$ 
___Quadruple Precision___: 128 bit, K = 15, G = 112, massimo modulo: $2^{+16385}$, minimo modulo: $2^{-16383}$ 
La IEEE sta lavorando alla standardizzazione dei numeri reali in virgola mobile su 8 bit, ma è possibile che float8 abbia diverse versioni, con K = 3,4 o 5, quest'ultima sarebbe nell'interesse della comunità del _machine learning_.