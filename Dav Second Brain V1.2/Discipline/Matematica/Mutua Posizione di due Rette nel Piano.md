#uni 
Abbiamo 3 possibilità:
1. $r_1$ ed $r_2$ coincidono (insieme non limitato)
2. $r_1$ ed $r_2$ sono parallele (insieme vuoto)
	In questo caso vogliamo trovare la distanza tra le due rette.
3. $r_1$ ed $r_2$ sono incidenti (singoletto)
	In questo caso vogliamo:
	1. trovare il punto di intersezione.
	2. trovare gli angoli formati dalle rette.
4. Non incidenti e non parallele, Sghembe
# Punto di Intersezione
Per trovare il punto di intersezione tra due rette bisogna risolvere un sistema lineare.
1. se conosco la forma cartesiana di $r_1$ ed $r_2$ allora metto a sistema e risolvo.
2. Forma parametrica:
	Trovo l'angolo tra i due vettori direzione. $(a,b) + t(c,d)$ e $(e,f) + t(g,h)$ 
	Metodo 1: porto in cartesiana implicita
	metodo 2: Scrivo le due rette scrivendo parametri diversi. $\to (a +tc,b+td$ ) e $(e+sg, f+sh)$ 
	Costruisco questo sistema: $$\begin{cases} a+tc =e+sg \\ b+td = f+sh \end{cases} \to \begin{cases} tc-sg=e+a \\ td - sh = f+d\end{cases}$$ Risolvo per $t$ ed $s$ e sostituisco nelle rette e trovo il punto di intersezione.
# Angolo di Incidenza
Forma parametrica: calcolo l'angolo tra le direzioni. $$\tan(angolo\ compreso) = |\frac{m_1 -m_2}{1+m_1 m_2}|$$ 
Se ho la forma cartesiana:
l'angolo tra le due rette è uguale all'angolo tra i vettori perpendicolari alle direzioni. I vettori perpendicolari sono quelli dalla direzione $a,b$ della rappresentazione cartesiana implicita. $$\cos (angolo \ compreso) = \frac{<v_1,v_2>}{||v_1||\cdot||v_2||}$$
# Distanza
?