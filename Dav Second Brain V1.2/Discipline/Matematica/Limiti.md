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
Ma in generale il limite é indifferente da come é definito l' $x_0$ al quale tende.
# Regole Generali
1. Date $a_n \to \infty$ e $b_n$ limitata inferiormente: $a_n + b_n \to \infty$ 
2. dati $k_1 > k_2$: $\lim_{n \to \infty} \frac{n^{k_1}} {n^{k_2}} = \infty$ 
3. Dati $a_n \ e \ b_n \to \infty$ : $a_n b_n \to \infty$ 
4. 
# Forme Indeterminate
Le forme indeterminate si presentano quando semplicemente sostituire il valore del limite all'incognita non basta perché porta a uno di 4 casi particolari:
1. $0 \cdot \infty$ 
2. $\frac{0}{0}$ 
3. $\infty ^ 0$ 
4. $\infty - \infty$ 
5. $\frac{\infty}{\infty}$ 
6. $0^0$ 
7. $1^\infty$ 
# Limiti Notevoli
$$\begin{array} {|c|c|} \hline limite & generalizzazione\\ \hline \lim_{x\rightarrow 0}\frac{sinx}{x}=1 & \lim_{f(x)\rightarrow 0}\frac{sinf(x)}{f(x)}=1 \\ \hline \lim_{x\rightarrow 0}\frac{1-cosx}{x^2}=\frac{1}{2} & \lim_{f(x)\rightarrow 0}\frac{1-cosf(x)}{f(x)^2}=\frac{1}{2}\\ \hline \lim_{x\rightarrow 0}\frac{e^x-1}{x}=1 & \lim_{f(x)\rightarrow 0}\frac{e^f(x)-1}{f(x)}=1 \\ \hline \lim_{x \rightarrow 0} \frac {a^x - 1}{x} = 1 & \lim_{f(x) \rightarrow 0} \frac {a^f(x) - 1}{f(x)} = 1 \\  \hline \lim_{x\rightarrow 0} \frac{x+sin(x)}{x} = 2 & \lim_{f(x)\rightarrow 0}\frac{f(x)+sin(f(x)}{f(x)}=2 \\ \hline \lim_{x\rightarrow \infty}\frac{\log_a{(1+\frac{1}{x})}}{\frac{1}{x}}=\log_a e & \lim_{f(x)\rightarrow 0}\frac{\log_a{(1+f(x))}}{f(x)}=\frac{1}{\ln(a)}\\ \hline \lim_{x\rightarrow 0}\frac{(1+x)^b -1}{x}=b & \lim_{f(x)\rightarrow 0}\frac{(1+f(x))^b -1}{f(x)}=b\\ \hline \lim_{x\rightarrow \infty}(1+ \frac{a}{x})^x=e^a & \lim_{f(x)\rightarrow 0}\frac{(1+f(x))^b -1}{f(x)}=b\\ \hline \lim_{x\rightarrow \infty}\frac{logx}{x^c}=0 & \lim_{f(x)\rightarrow \infty}\frac{log(f(x))}{f(x)^c}=0 \\ \hline \lim_{x\rightarrow \infty}\frac{x^k}{e^x}=0 & \lim_{f(x)\rightarrow \infty}\frac{f(x)^k}{e^{f(x)}}=0\\ \hline \lim_{x \rightarrow \pm \infty}\left(1+\frac{1}{x}\right)^x=e & \lim_{f(x) \rightarrow \pm \infty}\left(1+\frac{1}{f(x)}\right)^{f(x)}=e\\ \hline \lim_{x \to \infty} \frac{x!}{x^x} = 0 \\ \hline \end{array}$$
# Gerarchia degli infiniti
$$(\log _a x)^d << x^b << c^x << x! << x^x$$Per $x \to \infty$, con $a > 0 \land a \neq 1$, $b> 0$, $c>1$, $d \in R$  
La notazione $x_n << y_n$ significa che $\lim_{n\to \infty} \frac{x_n}{y_n} = 0$
Se il limite $\lim_{x\to a}\frac{f(x)}{g(x)} =$
1. $non \ esiste$ : gli infiniti ___non sono confrontabili___.
2. $0$ : $g(x)$ è un ___infinito di ordine superiore___.
3. $\pm \infty$ : $g(x)$ è un infinito di ordine inferiore.
##### Ordine
Dati due infiniti $f(x)$ e $g(x)$, per $x \to a$, si dice che $f(x)$ è un infinito di ordine $\gamma$ ($\gamma >0$) rispetto a $g(x)$, se: $$\lim_{x \to a} \frac{f(x)}{[g(x)]^\gamma } = L \neq 0$$
Dove $g(x)$ è detto __Infinito Campione__.
# Vari Limiti Generali
1. $$\lim_{n \to \infty} \frac{n^a}{n^b}=\begin{cases} +\infty \ , \ a>b \\ 0 \ ,\ a<b \\ 1 \ , \ a=b \end{cases}$$
2. $$\lim_{n \to \infty} \sum^n_{k=0} a_k n^k = \begin{cases} +\infty \ , \ a_k\geq 0 \\ -\infty \ , \ a_k < 0 \end{cases}$$
3. $$\lim_{n \to \infty} n^m[a_n + \frac{a_{n-1}}{n} + ...+ \frac{a_0}{n^m}]=\begin{cases}\infty \ , \ a_m>0 \\ -\infty \ , \ a_m <0 \end{cases}$$
4. $$\lim_{n \to \infty} a_n^{b_n} = e^{b_n \ln a_n}$$
# Dimostrazioni Limiti Notevoli
1. $lim_{x \to \infty} sin(\frac{1}{x}) = 0$
   Adoperiamo il [[Teorema del Confronto]], se troviamo $a_n \leq b_n \leq c_n$ tali che $a_n$ ed $c_n$ si stringono attorno ad un valore troviamo anche il limite di $b_n$.
   Quindi: $0 \leq sin(x) \leq x$,[^1] $\forall x \in [0, \ \frac{\pi}{2}[$ e $x = \frac{1}{n} < \frac{\pi}{2}$ quindi $0 \leq sin(\frac{1}{n}) \leq \frac{1}{n}$ 
   Ma $lim_{n \to \infty} 0$ va ovviamente a $0$, e $lim_{n \to \infty} \frac{1}{n}$ va anche a $0$, quindi anche $lim_{x \to \infty} sin(\frac{1}{x})$ va a $0$, C.V.D.
2. $\lim_{x \to \infty} \sqrt[n]{n} = 1$
   Poniamo $1 < a_n = \sqrt[n]{n}$, quindi $n = (a_n)^n$ e $a_n = 1 + b_n$ 
   Quindi $n= (a_n)^n=(1+b_n)^n \geq 1 + nb_n$ Per la [[Disuguaglianza Bernoulli]] 
   $(1+ b_n)^n = 1 + nb_n + ...$ ma la somma è maggiore degli addendi quindi sicuramente $(1+b_n)^n > \begin{pmatrix} n \\ k \end{pmatrix} (b_n)^2 = \frac{n(n-1)}{2} b_n ^2$  
   Siccome $b_n > 0$ Allora: $0 \leq b_n ^2 \leq \frac{2}{n - 1}$ 
   Ma $\frac{2}{n-1} \to 0$ Allora $b_n \to 0$ per il [[Teorema del Confronto]].
   Ma $n = (1 + b_n ) ^n$ Quindi $\sqrt[n]{n} \to 1$ C.V.D. 
   Oppure: 
   $\lim_{x \to \infty} \sqrt[n]{n} = lim_{ n \to \infty} n^{\frac{1}{n}}$  
   Siccome in generale $a^b = e^{b\ln a}$ Allora $n^{\frac{1}{n}} = e^{\frac{1}{n} \ln n}$ Ma $\frac{1}{n} \ln n \to 0$ Quindi $lim_{ n \to \infty} n^{\frac{1}{n}} = 1$ C.V.D.
3. $\lim_{n \to \infty} \frac{n!}{n^n} = 0$
   Vediamo se possiamo applicare il [[Principio di Sostituzione degli Infiniti (esimi)]] e sostituire $n! = \sqrt{2 \pi n} (\frac{n}{e})^n$:
   $$\frac{n!}{n^n} = \frac{n!}{\sqrt{2 \pi n} (\frac{n}{e})^n} \frac{\sqrt{2 \pi n} (\frac{n}{e})^n}{n^n}$$La prima frazione tende a $1$ secondo la [[Formula di Stirling]], la seconda frazione tende ad un numero quindi posso applicare il principio, allora: $$\lim_{n \to \infty} \frac{n!}{n^n} = \lim_{n \to \infty} \frac{\sqrt{2 \pi n} (\frac{n}{e})^n}{n^n} = \lim_{ n \to \infty} \frac{\sqrt{2 \pi n}}{e^n} = 0$$
4. $\lim_{n \to \infty} \frac{a^n}{n!} = 0, \ \forall a \geq 1$ 
   Sostituisco con la [[Formula di Stirling]]: $$\lim_{n\to \infty} \frac{a_n}{\sqrt{2 \pi n}(\frac{n}{e})^n} = \frac{(a_n e)^n}{\sqrt{2 \pi n} \ n^n} \leq  (\frac{ae}{n})^n \to 0$$
   Quindi possiamo generalizzare la [[Limiti#Gerarchia degli infiniti]] e dire che $a^n < n!, \ \forall a \geq 1$
5. $\lim_{n\to \infty} \sum^n _{k = 0} q^k= a_n =\frac{1-q^{n+1}}{1-q}$ 
   Se $-1 \leq q < +1$ allora $q^{n+1} = 0$ quindi $\lim_{n \to \infty} a_n = \frac{1}{1-q}$ 
   Se $q \geq 1$ allora $\lim_{n \to \infty} a_n = +\infty$ 
6. $\lim_{n \to \infty} \frac{a^n}{n} = \infty$ 
7. $\lim_{n \to \infty} \sin(n) = N/E$ 
# Altro
1. Dimostrazione che $lim_{x \to \infty} a^n = \infty; \ \ se \ a\geq 1$ : 11/10/2023 ultima pagina
2. xx
[^1]:  Dimostrazione che $sin(x) \leq x$ //
