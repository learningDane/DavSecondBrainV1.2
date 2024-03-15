#uni 
Se scomponiamo velocità e accelerazione in parte tangenziale e parte radiale, capiamo che $a_{tangenziale}$ dipende dalla variazione del modulo della velocità $\vec v$, mentre $a_{radiale}$ dipende dalla variazione del vettore della velocità.
	$\vec a = \sqrt{\vec a_r^2 + \vec a_t^2}$ 
	$|\vec a_t|= \frac{d|\vec v|}{dt}$ 
	$|\vec a_r|= \frac{v^2}{r}$ 
	$\vec v(t)=\vec v(t_0) + \int_{t_0}^t \vec a (t')dt$ 
$x(t)=x_0 + \int_{t_0}^t\vec v(t)dt$ 
In forma vettoriale:
	$\vec r_0=(x_0,y_0,z_0)$    ,    $\vec v_0=(v_{x0},v_{y0},v_{z0})$ 
	vettore posizione: $\vec r (t)=\vec r_0 + \int_{t_0}^t\vec v (t)dt$ 
	velocità: $\vec v(t)=\vec v_0 + \int_{t_0}^t\vec a (\Gamma)d\Gamma$ 
# In coordinate polari
- Vettore $\vec R = (x,y,z) = (R \cos \theta, r \sin \theta, 0)$ 
- versore $\hat R = (x/R, y/R,0)=(\cos \theta, \sin \theta, 0)$ 
- versore $\hat \theta = (-\sin \theta, \cos \theta,0)$ 
Il moto è ___circolare___ se $R$ è costante.
Il moto è circolare ___uniforme___ se $R$ è costante e $||\vec V||$ è costante.
La ___velocità angolare___ $ω$ è la derivata del vettore $\vec \theta$ rispetto al tempo $t$.
La velocità angolare in questo sistema è un vettore costante ma non negli altri sistemi.
La velocità è tangente alla traiettoria.
L'accelerazione ha solo componente radiale.
Periodo $T= \frac{2 \pi}{|ω|}$ 
Frequenza $V=\frac{1}{|T|}$ 
$$\begin{matrix} \vec ω=\frac{d\vec \theta}{dt} = (0,0,\theta) = \hat z \dot \theta \implies ω_z= ω =\frac{d\theta}{dt}=\dot \theta \implies [\vec ω ]= rad/s \\ \vec V = \frac{d \vec R}{dt} = \frac{d}{dt}(R\cos \theta, R \sin \theta, 0 ) = \vec ω \land \vec R= \hat \theta \dot \theta R= ωR\hat \theta \\ \vec a = -ω^2R\hat R=-\frac{V^2}{R}\hat R\end{matrix}$$
# Riepilogo
$$\begin{array} {|c|c|} \hline grandezza & circolare \ uniforme & circolare \ n/f & generale
\\ \hline
\theta & 
lienare \ con \ t &
variabile & 
variabile \\ \hline
ω &
costante &
variabile &
variabile
\\ \hline
α &
0 & 
variabile & 
variabile
\\ \hline
|\vec R| &
costante & 
costante & 
variabile
\\ \hline
|\vec V| &
costante & 
variabile &
variabile
\\ \hline
\vec V &
\vec ω \land \vec R & 
\vec ω \land \vec R &
\vec ω \land \vec R + \dot R \hat R
\\ \hline
V_R &
0 &
0&
\dot R
\\ \hline
V_\theta &
ωR &
ωR &
ωR
\\ \hline
\vec a &
-ω^2 \vec R &
-ω^2 \vec R + aR\hat \theta &
-ω^2 \vec R + aR\hat \theta+2ω \dot R \hat \theta+\ddot R \hat R
\\ \hline
a_R &
-ω^2 R &
-ω^2 R &
-ω^2 R + \ddot R
\\ \hline
a_\theta &
0 &
aR &
aR+2ω\dot R
\\ \hline
\end{array}$$
