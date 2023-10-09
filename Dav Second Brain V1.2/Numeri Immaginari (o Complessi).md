#uni 
$$i=\sqrt{-1}$$ $$C = \{ z=a+ib;\ a,b\ \in \ R \}$$
# Piano di Gauss (Argand-Gauss)
Il piano di Gauss rappresenta su un piano cartesiano un numero complesso, mettendo sull'asse dell'ascissa la parte reale di $z$ e sull'ordinata il coefficiente della parte immaginaria di $z$.
![[Immagine 2023-10-09 133838 1.png]]
# Forma Algebrica
$$z=a+ib$$Con $a$: parte reale di $z$, e $b$: coefficiente della parte immaginaria di $z$, con $a,\ b \in R$ 
### Somma
La somma si svolge semplicemente sommando parti reali e coefficienti tra di loro
### Moltiplicazione
$$z_1 \cdot z_2 = (a_1 a_2 - b_1 b_2) + i(a_1b_2 + b_1 a_2)$$
# Forma Trigonometrica (o Polare)
$$z=r[cos(\theta) + i \ sin(\theta)]$$Con:
$r \geq 0$ e $r \in R$
$-\pi < \theta \leq \pi$ oppure $0\leq \theta < 2\pi$ 
Dove $\theta$ è l'angolo compreso tra il segmento che porta a $z$ e l'asse reale, nel Piano di Gauss  e $r$ è la lunghezza del segmento. Ne risulta che:
$a=r\cdot cos(\theta)$
$b=r \cdot sin (\theta)$ 
$z = r [cos(\theta) + i \ sin(\theta)]$ 
$r$ è detto ___norma___ o _modulo_ di $z$ e $\theta$ è detto ___argomento___ o _anomalia_ di $z$.
La condizione $-\pi < \theta \leq \pi$ oppure $0\leq \theta < 2\pi$  viene posto perché $sin$ e $cos$ son funzioni periodiche e la corrispondenza tra forma algebrica e polare di $z$ non sarebbe biunivoca. Un altro accorgimento affinché la corrispondenza sia biunivoca è porre il numero complesso $z=0$ come $r=0 \space ; \space \nexists \ \theta$ 
# Coniugato Complesso
Il coniugato di un numero complesso $z$, indicato con $\overline z$, $z^*$ o $conj(z)$ è per definizione un numero complesso con parte reale uguale a $z$ e parte immaginaria uguale ma di segno opposto a $z$.
Quindi se $z=a+i \ b$ allora $\overline z = a - i \ b$.
Quindi se $z = r [cos(\theta) + i \ sin(\theta)]$ allora $\overline z = r [cos(\theta) - i \ sin(\theta)]$ oppure $\overline z = r [cos(-\theta)  i \ sin(-\theta)]$.
Quindi se $z=r \ e^{i \theta}$ allora $\overline z = r\ e^{-i\theta}$.
# Inverso di un numero complesso
$z\cdot z^{-1} = 1$
$z^{-1} = \frac{\overline z}{|z|^2}$ quindi se $z=a+i\ b$ allora $z^{-1} = \frac{a-i\ b}{a^2 + b^2}$ 