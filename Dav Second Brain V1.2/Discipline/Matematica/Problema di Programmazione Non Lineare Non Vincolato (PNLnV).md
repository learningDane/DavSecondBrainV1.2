#uni 
Un problema PNR non vincolato è la semplice massimizzazione/minimizzazione di una funzione non lineare.
I metodi di risoluzione sono algoritmi iterativi che iniziano da un punto di partenza e convergono a punti stazionari.
__Punto di accumulazione__: punto al cui l'algoritmo si avvicina per infiniti passi.
Gli algoritmi costruiscono il nuovo punto nel seguente modo:
$$x^{k+1}=x^k+t_kd^k$$
con $d^k$ direzione e $t_k$ step size.
Differiscono nel modo in cui si calcolano direzione e step size.
Si restringe il problema ad una semiretta funzione di una variabile:
$$\Phi(t)=f(x^k+t_kd^k)$$
Per definizione $d^k$ deve essere una direzione buona, quindi: (PROB DI MINIMO)
$$\Phi(t)=\nabla f(x^k+t_k d^k)\cdot d^k$$
scelgo $d^k=-\nabla f(x^k)$ 
# Numero di Passi
Purtroppo in un problema non lineare non vincolato i passi possono essere illimitati, ci servono quindi delle regole di Stop, qua abbiamo alcuni esempi:
1. dopo un certo numero di step/tempo
2. quando il miglioramento diventa trascurabile: $|f(x^{k+1})-f(x^k)|<10^{-4}$ per esempio
3. quando il gradiente diventa quasi zero: $||\nabla f(x^{k+1})||<10^{-4}$ 
# Metodo del Gradiente Libero
Riassumiamo la risoluzione di un problema di minimo non lineare non vincolato tramite il metodo del gradiente:
Ipotesi: $f:R^n\to R, \quad f \in C^1$ 
$x^{k+1}=x^k+t_kd^k$ , calcolo $d^k=-\nabla f(x^k)$ e calcolo $t_k=argmin_{t≥0} \Phi (t)$ 
con $\Phi(t)=f(x^k+t_kd^k)$ 
### Metodo del gradiente a Passo costante
per MAX
$$\begin{matrix}
d^k=\nabla f(x^k)
\\
0≤t_k≤\frac{2}{L} \quad con \ L≥|\frac{∂^2f}{∂x_1x_2}|
\end{matrix}$$
### Metodo di Newton
$$
\begin{matrix}
d^k=H\cdot f(x^k)^-1\cdot\nabla f(x^k)
\\
t_k=1
\end{matrix}
$$
### Teorema del metodo del Gradiente
La successione del gradiente con ricerca esatta, o termina in un numero finito di passo in un punto stazionario, oppure i suoi punti di accumulazione sono punti stazionari.