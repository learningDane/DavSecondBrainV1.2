#uni 
Un punto ache si muove di moto circolare uniforme di velocità $v$ necessita di una accelerazione centripeta: $$a_c=\frac{v^2}{r}$$Questa accelerazione è sempre perpendicolare a $\vec v$. Questa accelerazione deve essere fornita da una forza, ___Forza Radiale___ $F_r$: $$\sum F_r=ma_c=m\frac{v^2}{r}$$
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
La ___velocità angolare___ $w$ è la derivata del vettore $\vec \theta$ rispetto al tempo $t$.
La velocità angolare in questo sistema è un vettore costante ma non negli altri sistemi.
La velocità è tangente alla traiettoria.
L'accelerazione ha solo componente radiale.
Periodo $T= \frac{2 \pi}{|w|}$ 
Frequenza $V=\frac{1}{|T|}$ 
$$\begin{matrix} \vec w=\frac{d\vec \theta}{dt} = (0,0,\theta) = \hat z \dot \theta \implies w_z= w =\frac{d\theta}{dt}=\dot \theta \implies [\vec w ]= rad/s \\ \vec V = \frac{d \vec R}{dt} = \frac{d}{dt}(R\cos \theta, R \sin \theta, 0 ) = \vec w \land \vec R= \hat \theta \dot \theta R= wR\hat \theta \\ \vec a = -w^2R\hat R=-\frac{V^2}{R}\hat R\end{matrix}$$