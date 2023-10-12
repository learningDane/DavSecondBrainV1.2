#uni 10/10/2023
Una funzione che non ha limite superiore non per forza tende a infinito.
# Teorema di unicità del limite
_Il limite, se esiste, è unico_.
	Per esempio: $lim_{n \to \inf} (-1)^n= \ non \ esiste$ perché a seconda che $n$ sia pari o dispari, il limite tende a $+1$ o $-1$.
# Proprietà
I limiti hanno le seguenti proprietà:
1. Ipotesi: $lim_{n \to \infty} a_n=L$   e   $lim_{n \to \infty} b_n=M$ 
   Tesi: $lim_{n \to \infty} (a_n + b_n) = lim_{n \to \infty} a_n +lim_{n \to \infty} b_n$ 
2. Ipotesi:  $lim_{n \to \infty} a_n=L$   e   $lim_{n \to \infty} b_n=M$ 
   Tesi: $lim_{n \to \infty} (a_n \cdot b_n) = lim_{n \to \infty} a_n \cdot lim_{n \to \infty} b_n$
3. Ipotesi:  $lim_{n \to \infty} a_n=L$   e   $lim_{n \to \infty} b_n=M$ 
   Tesi: $lim_{n \to \infty} (\frac{a_n}{b_n}) = \frac{lim_{n \to \infty} a_n}{lim_{n \to \infty} b_n}$ 
# Limiti Notevoli
1. $$lim_{x \to \infty} \frac{1}{x} = 0$$Dimostrazione non fatta
2. $$lim_{x \to \infty} sin(\frac{1}{x}) = 0$$Dimostrazione:
	   Adoperiamo il [[Teorema del Confronto]], se troviamo $a_n \leq b_n \leq c_n$ tali che $a_n$ ed $c_n$ si stringono attorno ad un valore troviamo anche il limite di $b_n$.
	   Quindi: $0 \leq sin(x) \leq x$,[^1] $\forall x \in [0, \ \frac{\pi}{2}[$ e $x = \frac{1}{n} < \frac{\pi}{2}$ quindi $0 \leq sin(\frac{1}{n}) \leq \frac{1}{n}$ 
	   Ma $lim_{n \to \infty} 0$ va ovviamente a $0$, e $lim_{n \to \infty} \frac{1}{n}$ va anche a $0$, quindi anche $lim_{x \to \infty} sin(\frac{1}{x})$ va a $0$, C.V.D.
3. s
# Altro
1. Dimostrazione che $lim_{x \to \infty} a^n = \infty; \ \ se \ a\geq 1$ : 11/10/2023 ultima pagina
2. [^1]:  Dimostrazione che $sin(x) \leq x$ //