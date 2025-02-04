#uni 
# Sintesi SP
//inserire metodo di sintesi
# Sintesi PS
Data $F$ da sintetizzare PS:
1. sintetizzo $\overline{F}$ in forma SP di costo minimo
2. ora $\overline{\text{sintesi ottenuta}}$ è una sintesi di $F$, poiché $\overline{\overline{F}}=F$ 
3. applico da destra verso sinistra i teoremi di de morgan ([[Algebra di Boole#Proprietà degli operatori Booleani]]).
4. Al posto della somma finale negata (porta OR con $k$ ingressi e invertitore) pongo il prodotto dei suoi ingressi negati: $$
z = \overline{ \overline{ z}} =\overline{ P_{1}+P_{2}+\dots+P_{k}}=\overline{P_{1}\cdot P_{2}\cdot\dots \cdot P_{k}}
$$
5. Al posto di ciascun prodotto negato pongo le somme dei suoi ingressi negati: $$
\overline{ P_{i}}=\overline{\prod x_{j}}=\sum x_{j}
$$
6. Quanto ottenuto è in forma PS. Se $F$ è in forma canonica SP allora $F'$ è in forma canonica PS.
___Se la sintesi SP di $\overline{F}$ è a costo minimo, lo è anche la sintesi PS di $F$.