#uni 
Il sistema LKKT (Lagrange-Kurush-Kuhn-Tucker) è un sistema composto dalla funzione Lagrangiana e da altri vincoli basati sulla regione ammissibile ([[Problema di Programmazione Non Lineare (PNL)#Dominio/Regione Ammissibile della PNL]]), le cui soluzioni sono i punti stazionari e quindi contengono massimi e minimi del problema.
$$LKKT:\begin{cases} 
\nabla f(x) +\sum_{i=1}^m \lambda_i\cdot\nabla g_i(x) +\sum_{j=1}^p
\mu_j\cdot\nabla h_j(x)=0\\ 
\lambda_k\cdot g_k(x)=0 \quad \forall k \in m \\
	h_l(x)=0 \quad \forall l \in p
\end{cases}$$
Tutte le soluzioni $\overline x = (x, \lambda, \mu)$ che risolvono il sistema sono __punti stazionari___.
# Classificazione dei Punti Stazionari
Una $\overline x \in \{punti \ stazionaroi \}$ può essere $\min / \max$ $locale/globale$ o $Sella$.
- se $\lambda$ discordi $\to$ $Sella$
- se $\lambda ≥ 0 \quad \to \quad mG/mL/Sella$  
- se $\lambda ≤ 0 \quad \to \quad MG/ML/Sella$ 
Se non esiste una soluzione $\overline x = \{x,\lambda, \mu \}$ che soddisfa il sistema allora massimo e minimo non esistono ($\pm \infty$).
Se il poliedro è limitato, una soluzione $\overline x$ esiste per il [[Funzioni#Teorema di Weierstrass]].
In un punto interno al dominio, le $\lambda$ sono $zero$ e le $h$ non esistono, il sistema si riduce quindi a $\nabla f(x)=0$.