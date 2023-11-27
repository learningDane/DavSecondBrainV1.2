#uni 
# Formula di Taylor con resto di Peano
La formula di Taylor serve ad approssimare, almeno localmente, tutte le funzioni sufficientemente regolari con polinomi.
###### Ipotesi: 
1. Sia $f(x)$ una funzione definita in un certo intervallo $(-δ , δ)$ per qualche $δ>0$
2. $f(x)$ derivabile $n-1$ volte nell'intervallo
3. Esiste la derivata n-esima almeno in $x=0$  
###### Tesi
$$f(x) = T_n(x) + o(x^n) : x \to 0$$Con $T_n$ : $$T_n(x)= f(x) + \frac{f'(x_0)}{1!}x + \frac{f''(x_0)}{2!}x^2 + ...+\frac{f^{(n)}(x_0)}{n!} x^n= \sum_{k=0}^n \frac{f^{(k)}(x_0)}{k!} (x-x_0)^k$$$T_n$ prende il nome di _polinomio di Taylor_$^4$ di grado $n$ generato da $f$,con centro in $x_0$ 
Se $x_0 = 0$ $T_n$ è anche detto _polinomio di Mac Laurin di grado $n$_. $T_n[f]$ è il polinomio di Taylor di grado $n$ generato da $f$.
# Proprietà
Siano $f$ e $g$ funzioni derivabili $n$ volte in $x_0$, $c_1,c_2 \in R$ allora: 
1. $T_n[c_1f +c_2g] = c_1T_n[f] + c_2T_n[g]$ 
2. $T'_n[f]=T_{n-1}[f']$ 
# Esempi Notevoli
$$se \ f(x)=e^x :T_n(x)=\sum_{k=0}^n \frac{x^k}{k!} $$$$se \ f(x)=\sin x : T_{2n+1}(x)=\sum_{k=0}^n(-1)^k\frac{x^{2k+1}}{(2k+1)!}$$$$se \ f(x)=\cos x : T_{2k}(x)=\sum_{k=0}^n(-1)^k\frac{x^{2k}}{(2k)!}$$$$se \ f(x)=\log(1+x) : T_n(x)=\sum_{k=0}^n(-1)^{k+1}\frac{x^k}{k}$$