#uni 
Una curva parametrizzata è continua se sono continue tutte le funzioni che la definiscono. Una curva parametrizzata è differenziabile se lo sono tutte le funzioni che la definiscono. Una curva può essere ___derivabile___ in qualche direzione ma non ___differenziabile___ se non è derivabile in tutte le direzioni.
Def: $$I \in R, r:I\to R^n \ , \, \ t \in I, r(t) \in R^n$$
$r(I)$ si dice sostegno della curva, ed è l'insieme dei punti che compongono la curva.
[[Teoremi sulle Funzioni Continue in Spazi multidimensionali]] 
# Derivata
Una curva parametrizzata è differenziabile se lo sono tutte le funzioni che la definiscono. Una curva può essere ___derivabile___ in qualche direzione ma non ___differenziabile___ se non è derivabile in tutte le direzioni.
Per fare la derivata di una funzione se ne fa la derivata nelle singole direzioni, quindi si fa la derivata di ogni variabile una per volta, considerando le altre come costanti.
___Gradiente___: $$\triangledown f(x_0)= \begin{pmatrix} \frac{d_if}{dx_i}(x_0) \\ ... \\ \frac{df}{dx_m}(x_0)\end{pmatrix} = \bigg( \frac{df}{dx_i}(x_0), ... ,\frac{df}{dx_m}(x_0) \bigg)$$Ma siccome ovviamente si può derivare più volte, ecco che entra in gioco la ___matrice jacobiana___: $$Df=\begin{pmatrix} \frac{df_1}{dx_1},...,\frac{df_1}{dx_n} \\ ...,...,... \\ \frac{df_k}{dx_1} , ..., \frac{df_1}{dx_n} \end{pmatrix}$$
Definizione di derivabile: $$ \begin{matrix} f:A(aperto)\in R^n \to R \ è \ differenziabile \ in \ x_0\in A, \\ se \ \exists l \in R^n: f(x)=f(x_0) + l_0(x-x_0) + o(|x-x_0|) \end{matrix}$$
___Teorema___: $$f:A(aperto) \in R \to R , \ \ \ \frac{df}{dx_j}:A \to R \ continue, \ allora \ f \ è \ differenziabile \ in \ ogni \ punto \ di \ A$$