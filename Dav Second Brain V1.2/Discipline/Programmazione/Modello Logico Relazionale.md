#uni 
Proposto da Edward Frank Codd nel 1970 per favorire l'indipendenza dei dati. Si basa sul concetto matematico di relazione, con una variante. Le relazioni hanno naturale rappresentazione per mezzo di Tabelle.
Tutti i dati sono rappresentati  come ___relazioni___ e manipolati con gli operatori dell'[[Algebra Relazionale]] o del calcolo relazionale.
Una relazione matematica è un sottoinsieme qualsiasi di un insieme prodotto da una qualche operazione tra uno o più insiemi detti ___Domini___. 
- Non c'è ordinamento tra le __tuple__ 
- non esistono tuple uguali
- ogni tupla è ordinata al suo interno
La struttura della tabella può essere posizionale, quindi l'ordine dei domini nella tabella dipende dall'ordine degli stessi nella relazione, oppure non posizionale, in cui a ciascun dominio di associa un nome unico nella tabella, che ne descrive il ruolo.
I riferimenti fra dati in relazioni diverse sono rappresentati per mezzo di ___valori___ dei domini che compaiono nelle tuple. 
# Definizioni
- ___Schema di Relazione___: $R(X)$ con $R$ nome della relazione e $X$ insieme di attributi
- ___Schema di Base di Dati___: $R={R_1(X_1),...,R_m(X_m)}$ quindi un insieme di schemi di relazione
- Una tupla su un insieme di attributi $X$ è una funzione che associa a ciascun attributo $A \in X$ un valore nel dominio di $A$, il simbolo $t[A]$ denota il valore della tupla $t$ sull'attributo $A$ 
- ___Istanza di Relazione___ su uno schema $R(X)$: insieme $r$ di tuple su $X$ 
- ___Istanza di base di dati___ su uno schema $R$: insieme di relazioni $r={r_1,...,r_m}$ dove ogni $r_i$ è una relazione sullo schema $R_i(X_i)$ 
# Valore Nullo
Il modello relazionale impone ai dati una struttura rigida, se una informazione manca non conviene usare valori particolari, viene utilizzato il valore ___NULL___. Si devono però imporre restrizioni sulla presenza di valori nulli in una relazione.
NULL può volere dire per esempio:
- valore sconosciuto
- valore inesistente
- valore senza informazione
I DBMS non distinguono i tipi di valore nullo!
# Chiave e Superchiave
Un insieme $K$ di attributi è una __superchiave__ per una relazione $r$ se $r$ non contiene due tuple distinte $t_1$ e $t_2$ con $t_1[K]=t_2[K]$ 
K è una __chiave__ per $r$ se è una superchiave minimale di $r$  (ovvero non contiene un'altra superchiave).
Una relazione è un insieme e per definizione quindi non può avere due elementi (le tuple) uguali, quindi ogni relazione ha almeno una chiave, la superchiave rappresentata dall'insieme degli attributi su cui è definita.
I valori NULL nelle chiavi non permettono di identificare le tuple e quindi devono essere limitati.
# Vincoli di Integrità
Un vincolo di integrità è una __proprietà__ associata ad una base di dati, che se soddisfatta esprime la correttezza del DB rispetto all'applicazione.
Questi permettono una descrizione più accurata della realtà, sono utili nella progettazione e sono usati nei [[DBMS]] nella esecuzione delle interrogazioni.
I vincoli corrispondono a proprietà reali e interessano tutte le istanze e se sono tutti soddisfatti garantiscono la correttezza dello schema.
In particolare un vincolo di integrità è una funzione booleana chiamata su ogni istanza della base di dati.
Esistono due tipi di vincoli di integrità:
- intra-relazionali
- inter-relazionali
###### Vincoli intrarelazionali
Il suo soddisfacimento è definito rispetto ad una singola relazione della base di dati.
- ___Vincolo di Tupla___: può essere valutata su ciascuna tupla indipendentemente dalle altre.
- ___Vincolo di dominio___: vincolo di tupla che coinvolge un solo attributo.
###### Vincoli interrelazionali
Il suo soddisfacimento è definito rispetto a più relazioni della base di dati
###### Vincoli di chiave
I vincoli di chiave sono particolari vincoli che fanno parte delle ___dipendenza funzionali___
###### Dipendenze funzionali
Formalmente:
Dati due insiemi di attributi $X$ e $Y$, si dice che $X$ determina $Y$ ($X \to Y$) se e solo se date due tuple distinte $t_1$ e $t_2$, se $t_1[X]=t_2[X]$ allora $t_1[Y]=t_2[Y]$ 
###### Vincolo di Integrità Referenziale
Un vincolo di integrità referenziale fra gli attributi $X$ di una relazione $R_1$ e una relazione $R_2$ impone ai valori su $X$ in $R_1$ DIVERSI da NULL di comparire come valori della chiave primaria di $R_2$. Nota che in questo caso l'ordine degli attributi tra cui è stabilito il vincolo è significativo.
###### Reazione alla violazione di vincoli
Quando si tenta di compiere un'operazione che viola un vincolo entrano in gioco diversi meccanismi, che prendono il nome di ___azioni compensative___.