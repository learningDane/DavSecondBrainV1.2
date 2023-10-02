#uni 28/09/2023
Indicato dai segni $|$ attorno all'argomento, rende positivo un eventuale valore negativo e lascia positivo un eventuale valore positivo:
$|-3|=+3$
Se l'argomento è una variabile conviene trasformarlo in un sistema: $$|x|= \begin{cases} x\ \ \ \ \ se\ x \geq 0 \\ -x\ \  se\ x \leq 0 \end{cases}$$
# Proprietà del valore assoluto:
#### Proprietà della disuguaglianza triangolare:
$$|x+y| \leq |x| + |y|$$
Dimostrazione:
	$- |x|\leq x \leq |x|$
	// per $y$ 
	Allora $-|x|-|y|\leq x+y \leq |x|+|y|$ 
	ciò vuol dire che $|x+y| \leq |x| + |y|$ C.V.D.

#### Lipschitzianità: $$||x|+|y|| \leq |x-y|$$
Dimostrazione:
	$|x| = |(x-y) + y| \leq |x-y| +|y|$
	$|y| = |(y - x) +x| \leq | y - x| + |x|$
	$|y| \leq (x-y) + |x|$
	$|x| - |y| \leq  |x-y|$ 
	$|y| - |x| \leq |x-y|$ 