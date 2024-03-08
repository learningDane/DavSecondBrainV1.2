#uni 
Tutti i dati sono rappresentati  come ___relazioni___ e manipolati con gli operatori dell'[[Algebra Relazionale]] o del calcolo relazionale.
Il modello relazionale consente al _progettista_ di database di creare una rappresentazione consistente e logica dell'[[Informazione]]. La consistenza è ottenuta inserendo nel progetto del database appropriati vincoli, che formano lo ___schema logico___. 
La struttura base del modello relazionale è costituita da:
1. uno o più ___attributi___ o campi dato. Ogni campo dato ha un tipo e quindi un dominio. I nomi attributo vengono indicati con lettere dell'alfabeto a partire dalla $A$. Gli insiemi di attributi invece si indicano con le lettere a partire dalla $Z$. 
2. una o più ___tuple___ (i record). Una  tupla su un insieme di attributi $X$ è una funzione che associa a ciascun attributo $A \in X$ un elemento, o valore, nel dominio $D_A$ di $A$.
$t[A]$ indica il valore della tupla $t$ sull'attributo $A$. 
$t[Y]$ indica il valore della tupla $t$ sull'insieme di attributi $Y$. 
Una ___istanza___ di Database è l'insieme dei valori delle tuple sugli attributi.
Se l'attributo $A$ ha come dominio $D_A$, allora ogni tupla $t[A]$ può assumere come valore solo elementi appartenenti a $D_A$ oppure NULL. 
--------- slides --------------
# Chiave
Un attributo per essere chiave per una relazione $r$ deve essere: 
	- superchiave = un'insieme $k$ di attributi è una superchiave per una relaizone $r$ se $r$ non contiene due _tuple_ distinte $t_1$ e $t_2$ con $t_1[k] = t_2[k]$.
	- minimale = contenere un solo attributo
Non sta scritto da nessuna parte che le chiavi sono uniche.
L'insieme di tutti gli attributi è una ___superchiave___, altrimenti sarebbero due tuple uguali. Ogni relazione ha quindi almeno una chiave.
Le chiavi possono avere come valore NULL.
Attributi che non si ripetono ma non sono chiavi si chiamano chiavi candidate.
### Chiave esterna
bho ----------------------------------------
### Dipendenze funzionali 
Dati due insieme di attributi x e y sulla relazione $r$ esiste una dipendenza funziona le da x a y, ovvero si dice che x determina y, ovvero $x \to y$, se e solo se date due tuple distinte $t_1$ e $t_2$, se queste due tuple assumono gli stessi valori sulle x allora assumo gli stessi valori sulle y. 
I ___vincoli di chiave___ sono particolari tipi di vincoli, che fanno parte delle ___dipendenze funzionali___.
# Vincolo di Integrità referenziale
Informazioni in relazioni diverse posso essere correlate
attraverso valori comuni, si usano normalmente i valori delle chiavi.
Un ___vincolo di integrità referenziale___ fra gli attributi $X$
(anche più di uno) di una relazione $R_1$ e un’altra
relazione $R_2$ impone ai valori su $X$ in $R_1$ di comparire
come valori della chiave primaria di $R_2$. In questo caso l’ordine degli attributi tra
cui è stabilito il vincolo è significativo.