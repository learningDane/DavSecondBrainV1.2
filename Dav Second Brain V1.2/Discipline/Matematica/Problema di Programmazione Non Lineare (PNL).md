#uni 
Abbiamo già parlato della classe [[Problema di Programmazione Non Lineare Non Vincolato (PNLnV)]], ma questi problemi nella realtà non esistono (pressoché), parliamo quindi di questo stesso problema ma stavolta vincolato.
# Dominio/Regione Ammissibile della PNL
$f:D\subset R^n \to R$ 
$$D=\{x\in R^n : g_1(x)≤0, \ ... \ , g_m(x) ≤ 0, \quad h_1(x)=0, \ ... \ ,h_p(x)=0\}$$con $g:R^n\to R^m, \quad g=(g_1, ...,g_m)$    e     $h:R^n\to R^p, \quad (h_1,...,h_p)$
### Possibili Proprietà dei Domini della PNL
1. ___Chiuso___: la frontiera appartiene all'insieme
2. ___Limitato___: rientra dentro una palla
3. ___Convesso___: 
   un insieme $D$ si dice convesso se $\forall x,y \in D:\lambda x+(1-\lambda)y \in D, \forall \lambda \in [0;1]$ 
   oppure una condizione sufficiente affinché $D$ sia convesso è che le $g_i$ siano convesse e le $h_j$ siano lineari. Quindi che l'Hessiana delle $g_i$ sia semidefinita positiva ([[Note Introduttive alla PNL di Analisi II]])
4. ___Regolare___: Ne esistono diverse classi:
   1. $g_i,h_j$ lineari
   2. $g_i$ convesse, $h_j$ lineari e sia soddisfatta la ___condizione di Slater___ (esiste un punto interno): $\exists \overline x:g(\overline x)<0$ 
   3. Soddisfatta la ___condizione di Mangasarian___: $\nabla g_i(\overline x), \nabla h_j(\overline x) \ siano \ linearmente \ indipendenti \quad \forall \overline x \ \ ammissibile \quad \forall i,j \ attivi \ in \ \overline x$ 
      in generale vuol dire che siano linearmente indipendenti i gradienti dei vincoli attivi nei punti di intersezione. Ovvero controllare che la matrice creata con questi gradienti abbia rango massimo.