#uni 
$$\begin{cases} max \ c^T \cdot x \\ Ax \leq b \end{cases}$$
dove $max \ c^T \cdot x$ è la funzione obiettivo e
$Ax \leq b$ sono i vincoli (in cui devo anche includere i vincoli sulle soluzioni, _ex_ $x_A > 0$ )
ATTENZIONE il $\leq$ non è un minore uguale vero e proprio, sta a indicare che il primo valore di $Ax$ è uguale al primo valore di $b$, il secondo eccetera. Serve per evitare di scrivere una disequazione per ogni riga.