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