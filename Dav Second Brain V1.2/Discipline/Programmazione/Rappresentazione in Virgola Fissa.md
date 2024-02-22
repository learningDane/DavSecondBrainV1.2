#uni 
Viene usato un numero fisso di bit per la parte intera ed un numero fisso di bit per la parte frazionaria. Siano $p$ i bit totali, $f$ quelli per la parte frazionaria e $(p-f)$ quelli per la parte intera: $$R = \sum_{i = -f}^{p-f-1}a_iB^i = a_{p-f-1}B^{p-f-1}+...+a_0B^0+a_{-1}B^{-1}+...+a_{-f}B^{-f}$$dove $a_0B^0+a_{-1}B^{-1}+...+a_{-f}B^{-f}$ è la parte frazionaria.
Per la parte intera si usano le tecniche note, per la parte frazionaria si usa il seguente procedimento: 
	$f_0 = F(r)$ 
	se $f_0 \neq 0$ eseguire la seguente procedura iterativa:
		$f_{-1} = F(f_0*2) \ \ a_{-1} = I(f_0*2)$ 
		$f_{-2} = F(f_{-1}*2) \ \ a_{-2} = I(f_{-1}*2)$ 
		fino a che $f_{-j} = 0$ oppure si è raggiunta la precisione desiderata.
	alcuni parti frazionali hanno bisogno di u numero infinito di cifre, in questi casi operiamo un __troncamento__ al numero di cifre che abbiamo a disposizione, aggiungendo un errore di troncatura.