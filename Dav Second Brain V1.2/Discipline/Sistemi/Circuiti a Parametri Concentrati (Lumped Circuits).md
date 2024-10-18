Questi sono circuiti le cui distanze fra le componenti sono tali da generare variazioni del segnale elettrico trascurabili (utilizzano approssimazione di **non estendersi nello spazio**).
Affinché le distanze siano tali da non influire sul segnale elettrico devono essere molto minori di $\lambda$ ($d<<\lambda$), la lunghezza d'onda del segnale elettrico, definita come $\lambda=\frac{v}{f}$.
I due casi tipici in cui invece l'estensione di un circuito non può essere trascurata sono i seguenti:
- $d\simeq \lambda$ 
- $f>>50Hz$, $50Hz$ è la frequenza tipica della rete di casa, un esempio di frequenza molto maggiore è la radio, che lavora tra i $75$ e i $108MHz$.

# Semplificazione di un Circuito
1. Semplifico le [[#Resistenze in Serie]]
2. Semplifico le [[#Resistenze in Parallelo]]
3. Trasformo le [[#Resistenze a Triangolo]] ($Y->\Delta$)
4. Trasformo le [[#Resistenze a Stella]] ($\Delta->Y$)
## Generatori di Corrente

```
generatore di corrente
```
- E' dotato di *contrassegno* che indica dove sta il + (ovvero il verso di scorrimento della corrente)
- Non ne conosco immediatamente la caduta di potenziale, va calcolata
- $i(t) \ = \ costante$ corrente *continua*
- $i(t) \ = \ alternata$ varia nel tempo in maniera sinusoidale
- $i(t) \ = \ 0$ allora A e B collegati con un [[#Circuito Aperto]]
### Generatori di Corrente in Serie

Non puoi mettere [[#Generatori di Corrente]] in serie a meno che non siano dei [[#Generatori di Corrente Reali]] (R in *parallelo*)
### Generatori di Corrente in Parallelo

```
generatore di corrente
```

La corrente totale ($i_{tot}(t)$) è rappresentata dalla somma algebrica di tutte le correnti presenti nel parallelo secondo la [[Prima Legge di Kirchkoff]] :
$$i_{tot}(t)=i_1(t)+i_2(t)+...+i_n(t)$$
# Tensione/Potenziale
## Definizione

La Differenza di Potenziale è il lavoro che serve per spostare $q^{(+)}$ da A a B
$$V_{ab}(t)=\frac{L_{ab}(t)}{q^{(+)}}=[\frac{w}{C}]=[V]$$
Forti parallelismi tra ***rete elettrica*** e ***rete idraulica***: le cariche vanno da Potenziale Maggiore a Potenziale Minore. 

Se il circuito non ha "salti" di Potenziale allora serve una "pompa": il [[#Generatore di Tensione]]
## Generatori di Tensione 
```
generatore di tensione
```
- E' dotato di un *contrassegno* che indica dove sta il + ( in sostanza ci dice se è $V_{AB}$ o $V_{BA}$)
- Per calcolare V si scelgono sistemi [[Non Associati]] (contrariamente ai resistori)
- $V(t) \ = \ costante$ si dice che genera corrente in *continua*
- $V(t) \ \neq \ costante$ allora varia secondo *sinusoide* -> corrente *alternata*
- $V(t) \ = \ 0$ allora A e B collegati in [[#Corto Circuito]]
### Generatori di Tensione in Serie
Dei [[#Generatori di Tensione]] sono in *serie* se sono attraversati dalla stessa corrente
```
generatori in serie
```
La $V_{eq}$ sarà data dalla somma algebrica di tutti i generatori nella serie:
$$V_{eq}=V_{AB}=V_1+V_2+...+V_n$$
il segno di ogni singola V dipende dal verso della corrente e dal contrassegno su ognuno di essi:
- se corrente concorde al contrassegno allora ***meno*** (riferimento [[#Associato]])
- se corrente opposta al contrassegno allora ***più*** (riferimento [[#Non Associato]])
### Generatori di Tensione in Parallelo

Non puoi mettere dei [[#Generatori di Tensione]] in *parallelo* a meno che non consideri [[#Generatori di Tensione Reali]] (R in serie).

Secondo la [[Seconda Legge di Kirchkoff]] la somma dei voltaggi calcolati su una maglia è uguale a 0:
$$\sum^{n}_{I=1}V_i(t)=0$$
# Generatori Pilotati
```
generatore di tensione
```
Possono essere di *tensione* o di *corrente* e vengono influenzati da altre correnti o tensioni moltiplicate per un certo valore:
es.
$$V_{BA}(t)= \alpha V(t)$$
$$i_{BA}=\beta V(t)$$
# Bipoli Elettrici

|                  | Memoria | Energia                           | t Invariante                   |
| ---------------- | ------- | --------------------------------- | ------------------------------ |
| [[#Resistori]]   | NO      | PASSIVO                           | SI (approssimazione del corso) |
| [[#Condesatori]] | SI      | PASSIVO (se inizialmente scarico) | SI                             |
| [[#Induttori]]   | SI      | PASSIVO (se inizialmente scarico) | SI                             |
## Resistori

"Rallenta" le cariche che passano al suo interno, quindi modifica la Differenza di Potenziale tra i due capi:
$$V_R(t)=\ R\ *\ i_R(t)=\ [\frac {V} {A}]=[\ohm]$$
La resistenza però dipende anche da fattori intrinsechi al resistore se non trascurati come la *lunghezza*, la *sezione*, la ***resistività*** $\rho$ = $[\ohm*m]$
$$R = \rho \frac{l}{S}$$
### Resistenze in Serie

Due o più [[#Resistori]] si dicono in *serie* se sono attraversati dalla stessa corrente:

```tikz
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz} \draw
    % Nodo iniziale A
    (0,0) node[left] {$A$}
    to[R=$R_1$, v_<= $V_1$] (2,0) % Prima resistenza con differenza di potenziale sotto
    to[R=$R_2$, v_<= $V_2$] (4,0) % Seconda resistenza con differenza di potenziale sotto
    -- (5,0) node[anchor=north] {\dots} % Puntini di sospensione
    -- (6,0)
    to[R=$R_n$, v_<= $V_n$] (8,0) % Ultima resistenza con differenza di potenziale sotto
    % Nodo finale B
    node[right] {$B$};
\end{circuitikz}
\end{document}
``` 


```tikz
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz} \draw
    % Nodo iniziale A
    (0,0) node[left] {$A$}
    to[R=$R_{eq}$, v_<= $V_{eq}$] (6,0) % Resistenza equivalente con differenza di potenziale sotto
    % Nodo finale B
    node[right] {$B$};
\end{circuitikz}
\end{document}
```
La resistenza equivalente $R_{eq}$ si trova facendo la somma algebrica di tutte le resistenze della serie
$$R_{eq}=R_1+R_2+. . .+R_n$$
Quindi automaticamente la differenza di potenziale tra i nodi A e B diventa:
$$V_{ab}(t)=R_{eq}\ * \ i_{ab}(t)$$

### Resistenze in Parallelo

Due o più [[#Resistori]] si dicono in *parallelo* se si trovano allo stesso [[#Tensione/Potenziale]]:
```tikz
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz} \draw
    % Nodo madre A e collegamenti con i nodi A^n
    (0,0) node[above] {$A$}
    to[short] (2,0) node[above] {$A^1$} % Collegamento A con A^1
    to[short] (4,0) node[above] {$A^2$} % Collegamento A con A^2
    -- (6,0) node[above] {\dots} -- (8,0) node[above] {$A^n$} % Puntini di sospensione e A^n
    
    % Nodo madre B e collegamenti con i nodi B^n
    (0,-3) node[below] {$B$}
    to[short] (2,-3) node[below] {$B^1$} % Collegamento B con B^1
    to[short] (4,-3) node[below] {$B^2$} % Collegamento B con B^2
    -- (6,-3) node[below] {\dots} -- (8,-3) node[below] {$B^n$} % Puntini di sospensione e B^n
    
    % Resistenze in parallelo con le correnti
    (2,0) to[R=$R_1$, i_=$i_1$] (2,-3) % Prima resistenza con corrente i_1
    (4,0) to[R=$R_2$, i_=$i_2$] (4,-3) % Seconda resistenza con corrente i_2
    (8,0) to[R=$R_n$, i_=$i_n$] (8,-3); % Ultima resistenza con corrente i_n
\end{circuitikz}
\end{document}
```


```tikz
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz} \draw
    % Nodo madre A e collegamenti senza lettere intermedie
    (0,0) node[above] {$A$}
    to[short] (2,0) % Collegamento A
    to[open] (2,-3) % Aperto al posto della prima resistenza
    (2,-3) to[short] (0,-3) node[below] {$B$} % Collegamento B
    
    (2,0) -- (4,0) to[open] (4,-3) % Secondo ramo aperto
    (4,-3) -- (2,-3)
    
    (4,0) -- (6,0) node[anchor=north] {\dots} -- (8,0) % Puntini di sospensione e ultimo ramo
    
    % Resistenza equivalente Req con corrente ieq
    (8,0) to[R=$R_{eq}$, i_=$i_{eq}$] (8,-3) % Req con ieq
    (8,-3) -- (6,-3) -- (0,-3); % Chiusura circuito a B
\end{circuitikz}
\end{document}
```

La resistenza equivalente $R_{eq}$ si trova facendo la somma algebrica delle ***conduttanze*** ($G=\frac{1}{R}$) di tutte le resistenze del parallelo
$$\frac{1}{R_{eq}}=\frac{1}{R_{1}}+\frac{1}{R_{2}}+...+\frac{1}{R_{n}}$$
viene da se che la corrente ($i_{eq}$) che scorre da A a B sarà:
$$i_{eq}(t)=V_{AB}(t)*R_{eq}$$
### Resistenze a Triangolo

Tre resistenze sono a *Triangolo* se a 2 a 2 condividono dei "braccetti"

```tikz
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz} \draw
    % Nodo 1
    (0,0) node[left] {$1$}
    to[R=$R_{12}$] (3,0) node[right] {$2$} % Resistenza tra i nodi 1 e 2
    
    % Resistenza tra i nodi 2 e 3
    to[R=$R_{23}$] (1.5,-2.5) node[below] {$3$}
    
    % Resistenza tra i nodi 3 e 1
    to[R=$R_{31}$] (0,0); 
\end{circuitikz}
\end{document}
```
come si vede dalla figura la resistenza $R_{12}$ ad esempio ha un braccetto in comune sia con $R_{31}$ (braccio 1) sia con $R_{23}$ (braccio 2), che a loro volta condividono il braccio 3.

Questa configurazione la posso trasformare, inserendo un nodo comune alle 3 al centro di questo triangolo in sistema di [[#Resistenze a Stella]]:

```tikz
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz} \draw
    % Nodo centrale comune
    (0,0) node[circle, draw, inner sep=2pt] (C) {}
    
    % Nodo 1 e resistenza tra 1 e il nodo centrale
    (C) to[R=$R_1$] (-2,2) node[left] {$1$}
    
    % Nodo 2 e resistenza tra 2 e il nodo centrale
    (C) to[R=$R_2$] (2,2) node[right] {$2$}
    
    % Nodo 3 e resistenza tra 3 e il nodo centrale
    (C) to[R=$R_3$] (0,-2.5) node[below] {$3$};
\end{circuitikz}
\end{document}
```
a questo punto se voglio sapere $R_x$ mi basterà fare
$$R_X=\frac{R_{XY}*R_{XZ}} {R_{XY}+R_{XZ}+R_{YZ}}$$
Quando faccio queste equivalenze devo stare attento a non usare nodi importanti come potevano essere prima A e B che ti collegano al resto del circuito.
### Resistenze a Stella

Tre resistenze sono a *Stella* se condividono un nodo

```tikz
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz} \draw
    % Nodo centrale comune
    (0,0) node[circle, draw, inner sep=2pt] (C) {}
    
    % Nodo 1 e resistenza tra 1 e il nodo centrale
    (C) to[R=$R_1$] (-2,2) node[left] {$1$}
    
    % Nodo 2 e resistenza tra 2 e il nodo centrale
    (C) to[R=$R_2$] (2,2) node[right] {$2$}
    
    % Nodo 3 e resistenza tra 3 e il nodo centrale
    (C) to[R=$R_3$] (0,-2.5) node[below] {$3$};
\end{circuitikz}
\end{document}
```

la trasformazione definita prima è reversibile quindi da [[#Resistenze a Stella]] posso passare a una [[#Resistenze a Triangolo]]

```tikz
\usepackage{circuitikz}
\begin{document}
\begin{circuitikz} \draw
    % Nodo 1
    (0,0) node[left] {$1$}
    to[R=$R_{12}$] (3,0) node[right] {$2$} % Resistenza tra i nodi 1 e 2
    
    % Resistenza tra i nodi 2 e 3
    to[R=$R_{23}$] (1.5,-2.5) node[below] {$3$}
    
    % Resistenza tra i nodi 3 e 1
    to[R=$R_{31}$] (0,0); 
\end{circuitikz}
\end{document}
```
a questo punto se voglio conoscere $R_{xy}$ mi basterà fare

$$R_{XY}=\frac{R_XR_Y+R_XR_Z+R_YR_Z}{R_Z}$$
## Condensatori
## Induttori
