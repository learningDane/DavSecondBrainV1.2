#uni 
# Significato Geometrico
Per capire la derivata prendiamo in esempio una funzione di equazione di secondo grado ($y=x^2$), diciamo che vogliamo trovare il coefficiente angolare medio in un determinato intervallo $[x_0;x_1]$: 
Ci basta fare il rapporto tra la differenza dell'ordinata dei due punti e la differenza dell'ascissa degli stessi: $m=\frac{f(x_1) - f(x_0)}{x_1 - x_0}$. Ora riscriviamo $x_1 = x_0 + h$ e sostituiamo: $m=\frac{f(x_0 + h) - f(x_0)}{h}$. Ora più rimpiccioliamo $h$, la differenza tra le due ascisse, e più ci avviciniamo al coefficiente angolare effettivo nel punto $x_0$. 
# Rapporto Incrementale
Ora per ottenere definitivamente il coefficiente angolare adoperiamo l'operazione di limite, ed ecco che arriviamo a quello che si chiama rapporto incrementale: $$\lim_{h \to 0} \frac{f(x_0 + h) - f(x_0)}{h}$$Se questo limite esiste ed è finito, la funzione $f(x)$ si dice ___derivabile___ nel punto $x_0$ e il valore che assume il limite si dice ___derivata di $f$ in $x_0$___.
# Notazioni
$f'(x_0)$ (___Notazione di Lagrange___) oppure $\dot{f}(x_0)$ (___Notazione di Newton___) oppure $\frac{d^n}{dx^n} f(x_0)$ (___Notazione di Leibniz___) oppure $D^n f(x_0)$ (___Notazione di Eulero___). 
# Derivabilità
Una funzione si dice derivabile in un punto se il rapporto incrementale in quel punto esiste ed è finito, oppure se la derivata destra e la derivata sinistra in quel punto sono uguali.
Se la funzione è derivabile in ogni punto di un insieme $A$ allora la funzione si dice derivabile in $A$.
A questo punto possiamo scrivere una funzione che ad ogni $x_0 \in A$ associ una $f'(x_0)$, questa funzione prende il nome di ___Funzione Derivata Prima___: $y=f'(x)$
###### Derivata di un [[Valori Assoluti]]
Una funzione valore assoluto $|f(x)|$ è derivabile solo se nel punto $x_0$ in cui $f(x_0)=0 : f'(x_0) = 0$ 
# Derivata delle Funzioni Elementari
###### Costanti
se $f(x) = k$ allora $f'(x) = 0$.
###### Potenze
se $f(x)=x^n$ allora $f'(x)=nx^{n-1}$ 
###### Funzioni Trigonometriche
1. ___Seno___: se $f(x) = \sin x$ allora $f'(x) = \cos x$ 
2. ___Coseno___: se $f(x) = \cos x$ allora $f'(x)=- \sin x$ ]
3. ___Tangente___: se $f(x) = \tan x$ allora $f'(x) = \frac{1}{\cos^2x}=1+ \tan^2x$ 
4. ___Cotangente___: se $f(x) = \cot x$ allora $f'(x) = \frac{1}{\sin^2x}=-1- \cot^2x$ 
5. ___Arcoseno___: se $f(x) = \arcsin x$ allora $f'(x) = \frac{1}{\sqrt{1-x^2}}$ 
6. ___Arcocoseno___: se $f(x) = \arccos x$ allora $f'(x) =- \frac{1}{\sqrt{1-x^2}}$ 
7. ___Arcotangente___: se $f(x) = \arctan x$ allora $f'(x) = \frac{1}{1-x^2}$ 
8. ___Arcocotangente___: se $f(x) = arccot \ x$ allora $f'(x) = -\frac{1}{1-x^2}$ 
###### Esponenziale
se $f(x) = e^x$ allora $f'(x) = e^x$ 
###### Logaritmo
se $f(x) = \log_ax$ allora $f'(x) = \frac{1}{x}\log_ae=\frac{1}{x}\frac{1}{\ln a}$ 
# Regole di Derivazione
### Somma
$$D \ f(x) + g(x) = f'(x) + g'(x)$$
### Prodotto
$$D\ f(x)g(x) = f'(x)g(x)+f(x)g'(x)$$
### Rapporto
$$D\frac{f(x)}{g(x)}=\frac{f'(x)g(x)-f(x)g'(x)}{g^2(x)}$$
# Tabella delle Derivate
$$\begin{array} {|c|c|} \hline Derivate
\\ \hline
D\ k = 0 & 
D\ \sin x = \cos x \\ \hline
\end{array}$$