#uni 
Un problema di Assegnamento è un [[Problema di Programmazione Lineare (PL)]], è infatti un caso particolare del [[Problema di Trasporto]], pertanto, essendo a sua volta caso particolare del [[Problema di Programmazione Matematica a Reti]], gode del [[Teorema di Interezza]].

|       | progetti | IS  | CS  | TI  | AB  |
| ----- | -------- | --- | --- | --- | --- |
|       |          | 1   | 2   | 3   | 4   |
| ditte |          |     |     |     |     |
| 1     |          | 20  | 18  | 16  | 14  |
| 2     |          | 22  | 16  | 19  | 15  |
| 3     |          | 21  | 17  | 15  | 23  |
| 4     |          | 19  | 18  | 14  | 24  |
Un gruppo bancario deve far fare 4 progetti ed indice un bando al quale partecipano 4 aziende, ogni azienda quota un prezzo per ogni progetto. Per ogni progetto ci vuole un mese, e ogni azienda può fare un solo progetto alla volta.
### Modello Matematico
$$\begin{cases} min \ C^Tx \\ X_{1,1}+X_{1,2}+X_{1,3}+X_{1,4} = 1 \\ ... \\ X_{1,1}+X_{2,1}+X_{3,1}+X_{4,1} = 1 \\ ... \\  X_{i,j} \geq 0 \end{cases}$$quindi $$\begin{cases} min \ c^T x \\ \begin{pmatrix} 1..1|0..0|..|0..0 \\ 0..0|1..1|0..0|..|0..0\\.. \\ 0..0|0..0|..|0..0|1..1\\ 010.00|010.00|..|010..0 \\ 0010..0|0010..0|..|0010..0 \\..\\ 0..01|0..01|..|0..01\\-{1}0..0|0..0|..|0..0\\0{-1}0..0|0..0|..|0..0\\..\\0..0|0..0|..|0..0{-1} \end{pmatrix} \cdot \begin{pmatrix} x_{11}\\x_{12}\\..\\x_{1n}\\x_{21}\\x_{22}\\..\\x_{2n}\\..\\ \\ \\x_{nn} \end{pmatrix}\leq \begin{pmatrix} 1 \\1\\1\\1\\..\\1\\1\\..\\-1\\-1\\..\\-1\end{pmatrix} \end{cases}$$
##### Variabili
Considerato un generico assegnamento $a,b,c,d$ , dove ditta 1 fa progetto $a$, 2 fa $b$ eccetera.
Il numero totale di permutazioni possibili è $n! = 4! = 24$.
Consideriamo la variabile $X_{i,j} = \begin{cases} 0 \ se \ i \ non \ fa \ j \\ 1 \ se \ i \ fa \ j \end{cases}$ 
Le $X_{i,j}$ possibili sono $4 \cdot 4 = 16$ 
Una soluzione si può dunque scrivere come ogni $X_{i,j}$ nell'ordine ${X_{1,1} , X_{1,2} , ... , X_{2,1}}$ 
quindi una soluzione possibile è  $X=(1 \ 0\ 1\ ... \ 0)$ 
##### Funzione obiettivo
$$min \ C^Tx = min \ 20X_{1,1} + 18X_{1,2} + 16X_{1,3} + 14X_{1,4} + 22X_{2,1}+...+24X_{4,4}$$dove $C$ è il vettore dei costi.
##### Vincoli
Ogni azienda può fare un solo progetto, quindi per ogni ditta:
$X_{1,1}+X_{1,2}+X_{1,3}+X_{1,4} = 1$ 
Ogni progetto deve essere fatto da una ditta, quindi per ogni progetto:
$X_{1,1}+X_{2,1}+X_{3,1}+X_{4,1} = 1$ 
Se il problema è cooperativo dobbiamo specificare che $X_{i,j} \geq 0$, e questo problema lo è.
# Dimensioni
Considerato un problema con $n$ entità ed $n$ "progetti": $$\begin{cases} min \ C^Tx \\ Ax \leq b \\ x \geq 0 \end{cases}$$
$x \in R^{16}$ 
$b \in R^8$ 
$A \in M^{16,16}$ 
# Cooperativo vs Non Cooperativo
Nei problemi di assegnamento, e solo in quelli di assegnamento, per ogni soluzione cooperativa ce ne è una non cooperativa, quindi sono lo stesso problema, ed è indipendente quale dei due risolvo.
# Numero di Variabili e Vincoli nella Forma Primale Standard
dati $i$ operatori e $j$ progetti
Numero di Variabili: $i\cdot j$
Numero di Vincoli: $i\cdot j +2i+2j$ 