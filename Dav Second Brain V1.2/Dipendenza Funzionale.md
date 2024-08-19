#uni 
Una dipendenza funzionale (___FD___) esprime un legame semantico tra due gruppi di attributi di uno schema di relazione $R$. Una FD è una proprietà di $R$ non di una $r$ di $R$ è perciò non può essere dedotta da una $R$ ma deve essere dedotta da qualcuno che conosce la semantica degli attributi di $R$. Vengono anche usate per verificare la presenza di anomalie e per la [[Normalizzazione]]. Con $R(X,F)$ intendiamo uno schema di relazione $R(X)$ che verifica un insieme di dipendenza funzionali $F$.
Definizione formale:
	esiste in $r$ su $R(X)$ una FD da due sottoinsiemi non vuoti di $X$, da $Y$ a $Z$ se per ogni coppia di tuple $t_1$ e $t_2$ di $r$ con gli stessi valori su $Y$, risulta che $t_1$ e $t_2$ hanno gli stessi valori anche su $Z$, e si scrive $Y \to Z$ (che NON implica $Z \to Y$).
	In breve: Dati due insiemi di attributi $X$ e $Y$, si dice che $X$ determina $Y$ ($X \to Y$) se e solo se date due tuple distinte $t_1$ e $t_2$, se $t_1[X]=t_2[X]$ allora $t_1[Y]=t_2[Y]$.
Questa definizione non è direttamente utilizzabile nella pratica perché prevede una quantificazione universale sulle istanze del [[Database]]. Non abbiamo un algoritmo capace di calcolare tutte le FD implicate da un insieme $F$.
# Dipendenze Funzionali Particolari
- Una FD è ___completa___ quando $Y \to Z$ e, per ogni $W \in Y$, non vale $W \to Z$ 
- se $Y$ è una superchiave ([[Modello Logico Relazionale#Chiave e Superchiave]]) di $R(X)$, allora $Y$ determina ogni altro attributo della relazione, quindi $Y\to X$ 
- se $Y$ è una chiave, allora $Y \to X$ è una dipendenza funzionale completa
- una FD è ___banale___ se è sempre soddisfatta, eg:
  1. $Y \to Y$ è banale
  2. $Y \to A$ è non banale se $A \notin Y$ 
  3. $Y \to Z$ è non banale se nessun attributo di $Z$ appartiene a $Y$ 
Esempio: relazione (_Impiegato_, stipendio, _progetto_, bilancio, funzione)
ogni impiegato ha un solo stipendio: $Impiegato \to Stipendio$, impiegato non è chiave quindi ci sono ripetizioni
ogni impiegato ha una sola funzione per progetto: $impiegato, progetto \to funzione$, imp e prog sono chiave quindi niente ripetizioni.
# Regole di inferenza d Armstrong
Armstrong ha fornito delle regole di inferenza che permettono di derivare costruttivamente tutte le FD implicate da un dato insieme iniziale.
1. ___Riflessività___: 
   Se $Y \in X$ allora $X \to Y$ 
2. ___Additività___ o ___Arricchimento___:
   Se $X \to Y$ allora $XZ \to YZ$ per qualunque $Z$
3. ___Transitività___:
   Se $X \to Y$ e $Y \to Z$ allora $X \to Z$ 
# Derivazione
Una derivazione di $f$ (FD) da $F$ (insieme di FD) secondo $RI$ (regole di inferenza) è una sequenza finita $f_1,...,f_m$ dove:
- $f_m = f$ 
- ogni $f_i$ è un elemento di $F$ oppure è ottenuta dalle precedenti FD $f_1,...,f_{i-1}$ della derivazione usando una delle $RI$ 
E indichiamo con $F \vdash X \to Y$ il fatto che la FD $X \to Y$ sia derivabile da $F$ usando $RI$.
#### Regole di derivazione comuni
- ___Unione___:
  $\{X \to Y, X \to Z \} \vdash X \to YZ$ 
- ___Decomposizione___:
  $\{X \to YZ\} \vdash X \to Y$ 
- ___Indebolimento___:
  $\{ X \to Y \} \vdash XZ \to Y$ 
- ___Identità___:
  $\{ \} \vdash X \to X$ 
# Chiusura di un insieme di attributi
Dato uno schema $R(T,F)$ con $X \in T$, la chiusura di $X$ rispetto a $F$ è definita come: $$X_F^+=\{ A \in T |F \vdash X \to A \}$$
Se non vi sono ambiguità per semplicità scriviamo $X^+$.
### Teorema della chiusura degli attributi
$$F \vdash X \to Y \iff Y \in X^+$$
# Correttezza e Completezza
$RI$ è corretto se $F \vdash X \to Y \implies F \vDash X \to Y$ : applicando $RI$ ad un insieme di $F$ di FD si ottengono solo dipendenze logicamente implicate da $F$.
$RI$ è completo se $F \vDash X \to Y \implies X \to Y$ : applicando $RI$ ad un insieme $F$ di FD si ottengono tutte le dipendenze logicamente implicate da $F$.
#### Teorema
_Le regole di inferenza di Armstrong sono corrette e complete_.
Questo teorema ci permette di scambiare $\vDash$ (soddisfa) con $\vdash$ (implica) ovunque, in particolare nella definizione di chiusura degli attributi.
Si può dimostrare che le regole di inferenza di Armstrong sono __minimali__, cioè ignorandone anche solo una di esse, l'insieme di regole che rimane non è più completo.
# Chiusura di un insieme di dipendenza funzionali
Sia $F$ definito su $R(Z)$, la chiusura di $F$ è l'insieme $F^+$ di tutte le FD implicate da $F$: $$F^+= \{ X \to Y | F \implies X \to Y \}$$
Dato un insieme $F$ definite su $R(Z)$, un'istanza $r$ di $R$ che soddisfa $F$ soddisfa anche le FD di $F^+$.
# Calcolo di $F^+$ 
per calcolare $F^+$ possiamo usare le regole di inferenza di Armstrong:
_Input_: $R(T,F)$ 
_Output_: $F^+$ 
$F^+ \gets F$ 
__while__ ($F^+$ non cambia) __do__
	__for each__ $f \in F^+$ __do__
		applicare riflessività ed additività a $f$ e aggiungere a $F^+$ le dipendenze ottenute
	__for each__ £f_1,f_2 \in F^+$ __do__ 
		se possibile, applicare transitività a $f_1$ e $f_2$ e aggiungere a $F^+$ la dipendenza ottenuta.
__return__ $F^+$ 
### Calcolo di $X^+$ 
Il calcolo di $F^+$ è molto costoso poiché ha una complessità esponenziale. Spesso però invece ci interessa verificare se $F^+$ contiene una certa FD, non generare l'intera chiusura, per fare ciò basta calcolare $X^+$ per il teorema di chiusura degli attributi:
_Input_: $R(T,F), X \in T$ 
_Output_: $X^+$ 
$X^+ \gets X$ 
__while__ ($X^+$ non cambia) __do__ 
	__for each__ $W \to V \in F$ __do__ 
		__if__ $W \in X^+$ __and__ $V \notin X^+$ __then__
			$X^+ \gets X^+ \cup V$ 
__return__ $X^+$ 
# Equivalenza
Due insiemi $F$ e $G$ di FD sugli attributi $T$ di una relazione $R(T)$ sono ___equivalenti___, in simboli $F \equiv G$, se e solo se $F^+ = G^+$. A quel punto si dice che $F$ è una ___copertura___ di $G$ e viceversa.
L'equivalenza ci permette di stabilire se due schemi di relazione rappresentano gli stessi fatti: basta che abbiano gli stessi attributi e FD equivalenti.
Per verificare l'equivalenza è sufficiente che:
- tutte le FD di $F$ appartengano a $G^+$ 
- tutte le FD di $G$ appartengano a $F^+$ 
# Ridondanza
Sia $F$ un insieme di FD, data $X \to Y \in F$, $X$ contiene un ___attributo estraneo___ se e solo se $X- \{ A \} \to Y \in F^+$.
$X \to Y$ è una FD ___ridondante___ se e solo se $X \to Y \in (F- \{ X \to Y \})^+$ 
Le FD che NON contengono attributi __estranei__ e la cui parte destra è un unico attributo, sono dette FD ___elementari___.
# Copertura Minimale
Sia $F$ un insieme di FD, $F$ è una ___copertura minimale___ se e solo se:
- ogni parte destra di una FD ha un unico attributo
- le FD non contengono attributi estranei
- non esistono dipendenza ridondanti
quindi se e solo sono tutte FD elementari non ridondanti.
Ogni tanto una copertura minimale viene chiamata _insieme minimale_ oppure _copertura canonica_.
### Teorema
Per ogni insieme di FD esiste una copertura minimale. (il teorema non dice nulla sull'unicità della cop. min.)
### Calcolo della copertura minimale
_input_: insieme $F$ di FD
_output_: copertura minimale $G$ di $F$ 
$G \gets F$ 
__for each__ $X \to Y$ __do__
	$Z \gets X$ 
	__for each__ $A \in X$ __do__ 
		__if__ $Y \in (Z-(A))_F^+$ __then__ 
			$Z \gets Z- \{A\}$ 
	$G \gets (G-\{X\to Y\} ) \cup \{ Z \to Y \}$ 
__for each__ $f \in (G- \{f \} )^+$ __then__
	$G \gets G- \{f\}$ 
__return__ $G$ 