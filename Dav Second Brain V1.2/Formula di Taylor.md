#uni 
# Formula di Taylor con resto di Peano
La formula di Taylor serve ad approssimare, almeno localmente, tutte le funzioni sufficientemente regolari con polinomi.
###### Ipotesi: 
1. Sia $f(x)$ una funzione definita in un certo intervallo $(-δ , δ)$ per qualche $δ>0$
2. $f(x)$ derivabile $n-1$ volte nell'intervallo
3. Esiste la derivata n-esima almeno in $x=0$  
###### Tesi
$$f(x) = T_n(x) + o(x^n) : x \to 0$$Con $T_n$ detto polinomio di Mac Laurin di grado $n$: $$T_n(x)= f(x) + \frac{f'(0)}{1!}x + \frac{f''(0)}{2!}x^2 + ...+\frac{f^{(n)}(o)}{n!} x^n= \sum_{k=0}^n \frac{f^{(k)}(0)}{k!} x^k$$
