#uni 10/10/2023
Una funzione che non ha limite superiore non per forza tende a infinito.
# Teoremi
##### Teorema di unicità del limite
_Il limite, se esiste, è unico_.
	Per esempio: $lim_{n \to \inf} (-1)^n= \ non \ esiste$ perché a seconda che $n$ sia pari o dispari, il limite tende a $+1$ o $-1$.
##### Teorema della Permanenza del Segno
_Se un limite è strettamente positivo allora l'oggetto che vi converge è sempre positivo "da un certo punto in poi" o in un "certo intorno"_. $$lim_{n \to \infty} b_n = M > 0 \implies b_n > 0 \  definitivamente \ dato \ un \ n \ abbastanza \ grande$$
##### Teorema della Limitatezza di Successioni Convergenti
_Ogni successione convergente è limitata_. [[funzioni#Successioni]]
###### Dimostrazione
Ipotesi: la successione è convergente $lim_{n \ to \infty} a_n = L$ 
Tesi: la successione è limitata, ovvero $\exists M > 0 \ t.c. \ |a_n| < M, \ \forall n \ in N$ 
Partiamo dal riscrivere la definizione di limite di successione: 
$\forall \epsilon > 0 \exists k \ in N \ : \ La - \overline \epsilon < a_n < L + \overline \epsilon \space \forall n > k$ 
Quindi la successione risulta limitata superiormente ed inferiormente lungo tutto l'insieme dei numeri naturali, che sono il dominio della successione per definizione.
# Proprietà
I limiti hanno le seguenti proprietà:
1. Ipotesi: $lim_{n \to \infty} a_n=L$   e   $lim_{n \to \infty} b_n=M$ 
   Tesi: $lim_{n \to \infty} (a_n + b_n) = lim_{n \to \infty} a_n +lim_{n \to \infty} b_n$ 
2. Ipotesi:  $lim_{n \to \infty} a_n=L$   e   $lim_{n \to \infty} b_n=M$ 
   Tesi: $lim_{n \to \infty} (a_n \cdot b_n) = lim_{n \to \infty} a_n \cdot lim_{n \to \infty} b_n$
3. Ipotesi:  $lim_{n \to \infty} a_n=L$   e   $lim_{n \to \infty} b_n=M$ 
   Tesi: $lim_{n \to \infty} (\frac{a_n}{b_n}) = \frac{lim_{n \to \infty} a_n}{lim_{n \to \infty} b_n}$ 
# Forme Indeterminate
Le forme indeterminate si presentano quando semplicemente sostituire il valore del limite all'incognita non basta perché porta a uno di 4 casi particolari:
1. $0 \cdot \infty$ 
2. $\frac{\infty}{0}$ 
3. $\infty ^ 0$ 
4. $\infty - \infty$ 
# Limiti Notevoli
$$\begin{array} {|c|c|} \hline limite & generalizzazione\\ \hline \lim_{x\rightarrow 0}\frac{sinx}{x}=1 & \lim_{f(x)\rightarrow 0}\frac{sinf(x)}{f(x)}=1 \\ \hline \lim_{x\rightarrow 0}\frac{1-cosx}{x^2}=\frac{1}{2} & \lim_{f(x)\rightarrow 0}\frac{1-cosf(x)}{f(x)^2}=\frac{1}{2}\\ \hline \lim_{x\rightarrow 0}\frac{e^x-1}{x}=1 & \lim_{f(x)\rightarrow 0}\frac{e^f(x)-1}{f(x)}=1 \\ \hline \lim_{x \rightarrow 0} \frac {a^x - 1}{x} = 1 & \lim_{f(x) \rightarrow 0} \frac {a^f(x) - 1}{f(x)} = 1 \\  \hline \lim_{x\rightarrow 0} \frac{x+sin(x)}{x} = 2 & \lim_{f(x)\rightarrow 0}\frac{f(x)+sin(f(x)}{f(x)}=2 \\ \hline \lim_{x\rightarrow 0}\frac{\log_a{(1+x)}}{x}=\frac{1}{\ln(a)} & \lim_{f(x)\rightarrow 0}\frac{\log_a{(1+f(x))}}{f(x)}=\frac{1}{\ln(a)}\\ \hline \lim_{x\rightarrow 0}\frac{(1+x)^b -1}{x}=b & \lim_{f(x)\rightarrow 0}\frac{(1+f(x))^b -1}{f(x)}=b\\ \hline \lim_{x\rightarrow \infty}(1+ \frac{a}{x})^x=e^a & \lim_{f(x)\rightarrow 0}\frac{(1+f(x))^b -1}{f(x)}=b\\ \hline \lim_{x\rightarrow \infty}\frac{logx}{x^c}=0 & \lim_{f(x)\rightarrow \infty}\frac{log(f(x))}{f(x)^c}=0 \\ \hline \lim_{x\rightarrow \infty}\frac{x^k}{e^x}=0 & \lim_{f(x)\rightarrow \infty}\frac{f(x)^k}{e^{f(x)}}=0\\ \hline \lim_{x \rightarrow \pm \infty}\left(1+\frac{1}{x}\right)^x=e & \lim_{f(x) \rightarrow \pm \infty}\left(1+\frac{1}{f(x)}\right)^{f(x)}=e\\ \hline \lim_{x \to \infty} \frac{x!}{x^x} = 0 \\ \hline \end{array}$$
# Gerarchia degli infiniti
$$\log _a x << x^b << c^x << x^x$$Per $x \to \infty$, con $a > 0 \land a \neq 1$, $b> 0$, $c>1$ 
# Dimostrazioni Limiti Notevoli
1. $$lim_{x \to \infty} sin(\frac{1}{x}) = 0$$Dimostrazione:
	   Adoperiamo il [[Teorema del Confronto]], se troviamo $a_n \leq b_n \leq c_n$ tali che $a_n$ ed $c_n$ si stringono attorno ad un valore troviamo anche il limite di $b_n$.
	   Quindi: $0 \leq sin(x) \leq x$,[^1] $\forall x \in [0, \ \frac{\pi}{2}[$ e $x = \frac{1}{n} < \frac{\pi}{2}$ quindi $0 \leq sin(\frac{1}{n}) \leq \frac{1}{n}$ 
	   Ma $lim_{n \to \infty} 0$ va ovviamente a $0$, e $lim_{n \to \infty} \frac{1}{n}$ va anche a $0$, quindi anche $lim_{x \to \infty} sin(\frac{1}{x})$ va a $0$, C.V.D.
2. xx
# Altro
1. Dimostrazione che $lim_{x \to \infty} a^n = \infty; \ \ se \ a\geq 1$ : 11/10/2023 ultima pagina
2. xx
[^1]:  Dimostrazione che $sin(x) \leq x$ //