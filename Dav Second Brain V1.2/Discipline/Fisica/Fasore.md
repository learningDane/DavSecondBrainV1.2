#uni 
In elettrotecnica un fasore è un numero complesso che indica una funzione sinusoidale di un determinato periodo.
Essendo un [[Numeri Immaginari (o Complessi)]] è rappresentabile nel piano di Gauss come un vettore __sfasato___ rispetto all'asse reale di un certo angolo, o ___fase___.
Un fasore viene indicato con il pallino sopra: $\dot x$. 
Se $$x(t)=X_msin(wt+\varphi_x)=X_m\cdot e^{j(wt+\varphi_x)}\implies\dot x = X_m\cdot e^{j\varphi_x}$$
dove $\dot x$ si dice il fasore associato alla funzione $x(t)$.
# Proprietà dei Fasori
- Addizione e Sottrazione: $$\dot I_1\pm \dot I_2=\dot I_1+(\pm \dot I_2)$$
- Proprietà di Derivata: $$\dot Y= j w \dot x$$
- Proprietà di Integrale: $$\dot Y=\frac{\dot x}{jw}$$
# Fasori Associati ai Bipoli 
### Resistore
$$v_R(t)=R\cdot i_R(t)$$
$$\dot V_R=R \cdot \dot I_R$$
### Induttore
$$v_L(t)=L\frac{di_L(t)}{dt}$$
$$\dot V_L=j\omega L\cdot \dot I_L$$
Il Fasore della [[tensione]] di un induttore è in anticipo di $90\degree$ rispetto al Fasore della corrente (ovvero angolo della corrente $+\pi/2$).
### Condensatore
$$v_C(t)=\frac{1}{C}\int i_C(t)dt$$
$$\dot V_C=\frac{1}{j\omega C}\cdot \dot I_C$$
Il Fasore della [[tensione]] di un induttore è in ritardo di $90\degree$ rispetto al Fasore della corrente (ovvero angolo della corrente $- \pi/2$).
##### Condensatori e Mutua Induzione
$$v_1(t)=L_1\frac{di_1(t)}{dt}\pm M\frac{di_2(t)}{dt}$$
$$\dot V_1=j\omega L_1 \dot I_1 \pm j \omega M \dot I_2$$