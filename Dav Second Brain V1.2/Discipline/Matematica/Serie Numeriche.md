#uni 
$$\sum_k^{+\infty}a_n$$
# Studiare la Convergenza
___Converge___=la serie converge ad un numero reale
___Diverge___=la serie diverge a infinito
-  __Teorema__: Se $\lim_{x \to \infty} a_n \neq 0$ allora la serie diverge, se invece tende a $0$ non posso trarre conclusioni
-  __Teorema__: Se $|\sum_k^{+\infty} |a_n|$ converge, allora converge anche $\sum_k^{+\infty}a_n$ 
# Serie Note
1. ___Serie Geometrica___: $$\sum_k^{\infty}ax^n=a+ax+ax^2+...+ax^n$$ con $k>0$, è una serie geometrica se il rapporto tra due termini successivi è sempre uguale, e questo rapporto prende il nome di ___ragione $\rho$ della serie___$\frac{ax^n}{ax^{n-1}} = ax$. 
   - Se $|x|<1$ la serie converge assolutamente a $\frac{a}{1-x}$ se la serie parte da $0$!
   - Se $x \geq 1$ la serie diverge
   - Se $x \leq -1$ la serie è indeterminata 
2. ___Serie Armonica:___ 
	1. serie armonica semplice: $\sum_{n=1}^\infty \frac{1}{n}$ è divergente
	2. serie armonica generalizzata di tipo 1: $\sum_{n=1}^\infty \frac{1}{n^k}$ se $0\leq k \leq 1$ diverge, se $k>1$ converge
	3. serie armonica generalizzata di tipo 2: $\sum_{n=1}^\infty \frac{1}{n^k |\ln n|^β}$ insieme alle condizioni precedenti, diverge se $β \leq 1$ e converge se $β > 1$ 
3. ___Serie Telescopica___: $$\sum_{n=1}^\infty (a_{n+1}-a_n)=(a_2-a_1)+(a_3-a_2)+...+(a_{n+1}-a_n)$$oppure
$$\sum_{n}^\infty (a_n-a_{n+1})\rightarrow \lim_{n \to +infty} \sum = \lim_{n\to +\infty}(a_1-a_{n+1})$$rg