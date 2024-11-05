#uni 
Questo algoritmo di Riduzione del Gap può essere usato per risolvere qualsiasi [[Problema di Programmazione Lineare Intera (PLI)]].
Consiste nel Calcolare un piano di taglio, ovvero un vincolo, e aggiungerlo al problema di partenza, iterativamente, fino a quando non si ottiene un errore nel target.
# Algoritmo
1. Calcolo $X_{RC}$ 
2. Porto il problema in [[Problema di Programmazione Lineare (PL)#Formato Duale Standard]] 
3. Ricalcolo $X_{RC}$ nel duale, ovvero calcolo gli scarti
4. Trovo $B=(indici \ di \ componenti \ \neq 0)$ e $r=(primo \ indice \ di \ componente \ frazionaria)$ 
5. $\tilde A=A_B^{-1}\cdot A_N$ , nomino le righe di $\tilde A$ con gli stessi indici di $A_B$ 
6. Scrivo il piano di Taglio: $$r:\quad( .. \ \{\tilde A_r\}\ ..)\cdot \begin{pmatrix}..\\ X_N \\ .. \end{pmatrix}\geq \{ X_r\}$$dove $\{ \}$ indica ___parte frazionaria___ e si calcola : $\{ C\}= C- \lfloor C \rfloor$ 
   ovvero = _numero_ - _arrotondamento per difetto_. 
7. se necessario possiamo scrivere il piano di taglio con le variabili del primale, ovvero sostituire lo scarto con lo scarto in funzione delle variabili del primale.