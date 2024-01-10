#self-taught 
# Teoria
Siano $f : I \to R$ una funzione __continua__ e $g : J \to I$ una funzione __derivabile__ con derivata __continua__. Si ha che: $$\int f(g(x))g'(x)dx=\bigg[ \int f(t)dt \bigg]_{t=g(x)}$$Nel caso in cui la funzione $g(t)$ sia __invertibile__ [[Funzioni#__suriettiva__ o invertibile]], allora vale la seguente formula di integrazione, allora vale la seguente formula di integrazione: $$\int f(x)dx=\bigg[ \int f(g(t))g'(t)dt \bigg]_{t=g^{-1}(x)}$$Le due forme sono del tutto equivalenti e in base a come si presenta la funzione integranda sta a noi scegliere quale conviene adoperare.
# Applicazione
Abbiamo un integrale che si presenta nella forma: $$\int f(g(x))g'(x)dx$$
1. Poniamo $t=g(x)$ e deriviamo membro a membro in modo da ottenere il nuovo differenziale $$dt = g'(x)dx$$
2. Sostituiamo nell'integrale e otteniamo: $$\int f\overbrace{(g(x))}^t \overbrace{g'(x)dx}^{dt} = \int f(t)dt$$
3. Calcoliamo l'integrale $F(t) + c$ 
4. Sostituiamo a $t$ l'espressione analitica della funzione $g(x)$ nella primitiva $F(t)$ e otteniamo $$F(g(x)) + c$$
