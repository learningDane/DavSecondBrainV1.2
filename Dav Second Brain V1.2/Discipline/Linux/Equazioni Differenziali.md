#uni 
Una equazioni in cui l'incognita è una funzione e vi sono presenti una o più derivate.
L'__ordine__ (o grado) di una equazione differenziale è il massimo grado di derivazione presente in essa.
Non esista un metodo di risoluzione generale, esso varia in base al tipo di equazione differenziale.
# Equazioni differenziali del $I^o$ ordine
Una equazione differenziale del primo grado si presenta così: $$y'(x)+a(x)y(x)=f(x)$$
### Equazioni differenziali elementari
$$y'(x)=f(x)$$
Se $a(x) = 0$ essa è una equazione differenziale __elementare__ e per risolverla basta portarla nella forma $y'(x) = f(x)$ ed integrare membro a membro.
### Equazioni differenziali omogenee (o a variabili separabili)
$$y'(x) + a(x)y(x)=0$$
Se $f(x) = 0$ essa è una equazione differenziale __omogenea__ e per risolvere si applica il seguente procedimento:
1. separo le variabili ( $y'(x) = \frac{dy}{dx}$ ): $$\frac{1}{y(x)}dy=a(x)dx$$
2. Integro membro a membro: $$\int\frac{1}{y(x)}dy=\int a(x)dx$$
3. Ricavo $y(x)$ 
__IMPORTANTE__: Se $\exists \overline{x} \in R : y(\overline{x})=0$ Allora $y(x) = \overline{x}$ è soluzione costante
Che in breve equivale alla formula: $$y(x)=c\cdot e^{-A(x)}$$
### Equazioni differenziali Lineari non omogenee
$$y'(x)+a(x)y(x)=f(x)$$
Se $a(x)\neq 0 \neq f(x)$ allora questa si dice equazione differenziale lineare non omogenea e per risolverla si applica il seguente metodo:
1. trovo la primitiva $A(x)$ di $a(x)$: $A(x)=\int a(x) dx$ 
2. moltiplico entrambi i membri per $e^{A(x)}$ 
3. mi accorgo che $y'(x)e^{A(x)}+ a(x)e^{A(x)}y(x) = D\big[ y(x)e^{A(x)}\big]$ 
4. integro quindi entrambi i membri e mi rimane: $y(x)e^{A(x)}=\int f(x)e^{A(x)}dx$ 
5. Ricavo $y(x)$ moltiplicando per $e^{-A(x)}$ 
Che in breve equivale alla formula: $$y(x)=e^{-A(x)}\int e^{A(x)}f(x)dx$$
# Equazioni differenziali del $II^o$ Ordine
### Equazioni differenziali del $II^o$ ordine Omogenee
Si presentano sotto la forma: $$ay''(x)+b'(x)+cy(x)=0$$con $a,b,c \in R$ 
L'insieme delle soluzioni è uno spazio vettoriale di dimensione $2$.
La soluzione generale di queste equazioni è del tipo: $$y(x)=c_1y_1(x)+c_2y_2(x)$$dove $y_1(x)$ e $y_2(x)$ sono una base dello spazio delle soluzioni.
##### Risoluzione:
Risolvo in $C$ l'equazione caratteristica $az^2+bz+c=0$ e se:
- trovo due soluzioni reali distinte: $λ_1 \neq λ_2$ la base è $e^{λ_1x},e^{λ_2x}$ e la soluzione è: $$y(x)=c_1e^{λ_1x}+c_2e^{λ_2x}$$
- trovo due soluzioni reali coincidenti: la base è $e^{λx},xe^{λx}$ e la soluzione è: $$y(x)=c_1e^{λx}+c_2xe^{λx}$$
- se trovo due soluzioni complesse: $λ_{1,2}=α \pm iβ$ con $α=\frac{-b}{2}$ e $β=\frac{\sqrt{-Δ}}{2}$  e la soluzione è: $$y(x)=c_1e^{αx}\cos(βx)+c_2e^{αx}\sin(βx)$$
### Equazioni differenziali del $II^o$ ordine Non Omogenee
Si presentano sotto la forma: $$y''(x) +by'(x)+cy(x)=f(x)$$
###### Metodo della variazione delle costanti:
1. Determinare la soluzione generale dell'equazione omogenea associata: $$y_0(x)=c_1y_1(x)+c_2y_2(x)$$
2. Trovare una soluzione particolare con questa forma: $$y_p(x)=c_1(x)y_1(x)+c_2(x)y_2(x)$$
   Risolvendo il seguente sistema: $$\begin{cases} c'_1(x)y_1(x)+c_2'y_2(x)=0 \\ c_1'(x)y_1'(x)+c_2y_2'(x)=f(x) \end{cases}$$Integrando gli appena ottenuti $c_1'(x)$ e $c_2'(x)$ ed inserendoli in $y_p(x)$
3. Trovare la soluzione generale: $$y(x)=y_0(x) + y_p(x)$$
###### Metodo della somiglianza
$$y''(x) +by'(x)+cy(x)=f(x)$$
1. Trovo le radici $λ_1,λ_2$ dell'equazione caratteristica e trovo quindi la soluzione dell'omogenea associata $y_0(x)$ 
2. Trovo la forma di $y_p(x)$, essa deve essere ___simile___ ad $f(x)$ 
	   Esempi:
		- $f(x)=(a_1x^2+b_1x+c)$ , $y_p(x)=(ax^2+bx+c)$ 
		  se un coefficiente in $f(x)$ è $=0$ allora lo stesso coefficiente è $=0$ anche in $y_p(x)$ 
		- $f(x)=a_1e^{bx}$ , $y_p(x)=(ae^{bx})$ ovvero l'autovalore rimane lo stesso
3. per ricavare i coefficienti $a,b,c,ecc$ di $y_p(x)$ questa deve essere soluzione dell'equazione differenziale originaria, quindi trovo le sue derivate e la sostituisco al posto di $y''(x),y'(x),y(x)$ e risolvo. A questo punto ottengo la completa $y_p(x)$ 
4. Trovo la soluzione $y(x)=y_0(x) + y_p(x)$ 
### Risonanza
Nel metodo della somiglianza, la struttura di $y_p(x)$ cambia in base alla ___molteplicità algebrica dell'autovalore___ $π$, ovvero in base a quante volte, l'autovalore, il coefficiente $α$ dell'esponenziale, è soluzione dell'equazione caratteristica. Infatti se il termine noto è: $$f(x)=e^{αx}(p_n(x)\cos βx+q_m(x)\sinβ x)$$con $α,β \in R$ e $p_n,q_m$ polinomi di gradi $n$ e $m$ 
allora esso individua il numero complesso $z=α \pm iβ$ 
Vi è risonanza con molteplicità $π$ solo se $z$ è radice $π$-volte dell'equazione caratteristica e quindi la soluzione particolare va cercata della forma: $$y_p(x)=x^πe^{αx}(P_k(x)\cos βx+Q_k(x)\sin βx)$$in cui $k=\max \{n,m\}$ e $P_k,Q_k$ sono polinomi a coefficienti incogniti di grado $k$. 