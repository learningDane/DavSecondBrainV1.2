#uni 

# RSS complesse
- ___microoperazioni___: i $K\cdot Q$ assegnamenti `Rq<=Rsk,q(x,Rq-1,...,R0)` relativi ai registri operativi.
- ___microsalti___: i $K$ assegnamenti `STAR<=(x,R1-1,...,R0)` relativi al registro di stato.
- ___statement di etichetta $S_i$___ : gli statement completi all'interno al costrutto `casex .. endcase`.
### Precisazioni sulle microooperazioni
1. $C=\{A,B\}$ descrive l'assegnamento del registro $C$ con i contenuti di $A,B$.
2. $\{A,B\}<=C$ equivale a DUE microoperazioni:
	1. $A<=C[l-1:m]$ 
	2. $B<=C[m-1:0]$ 
3. $C[m-1:0]<=B$ è sostanzialmente scorretta, in quanto A OGNI clock TUTTO il registro viene riassegnato, quindi equivarrebbe a: $C<=\{C[l-1:m],B\}$ 
# Handshake /dav, rfd
- /dav : _data valid_: se \dav=1 allora il dato fornito non è attendibile, se \dav=0 il dato è corretto e disponibile
- rfd : _ready for data_: se rfd=1, il consumatore è pronto a ricevere, se rfd=0 allora il consumatore non è pronto a leggere il dato
Funzionamento:
0. S0: $\text{/dav,rfd}=1,1$ : il dato del produttore non è pronto, il consumatore è pronto a ricevere
1. S1: $\text{/dav,rfd}=0,1$ : il dato è pronto
2. S2: $\text{/dav,rfd}=0,0$ : il consumatore ha prelevato il dato e non è pronto a riceverne altri
3. S3: $\text{/dav,rfd}=1,0$ : il produttore è pronto a produrre un nuovo byte
4. S0: $\text{/dav,rfd}=1,1$ : ritorno allo stato iniziale
Partendo da una condizione iniziale in cui rfd=1 e \dav=1:
Il produttore compie la prima mossa: aggiorna il dato e pone \dav=0, ad indicare che il dato è adesso valido.
Il consumatore, legge \dav=0, pone quindi rfd=0, preleva il dato, e lo elabora.
Il produttore riporta allora \dav=1 e attende che il consumatore riport rfd=1, per ritornare alal condizione iniziale.
Tutte queste variabili di handshake necessitano di un registro di supporto, ognuno dello stesso nome della variabile.
# Handshake soc, eoc
- soc: _start of computation_: soc=0 consumatore non ha bisogno di nuovo byte, soc=1 indica al produttore di fornire un nuovo byte.
- eoc: _end of computation_: eoc=0 produttore ha iniziato la preparazione di un nuovo byte, eoc=1 il produttore è pronto a preparare un nuovo byte.
Funzionamento:
0. S0: $soc,eoc = 0,1$ : consumatore non è pronto a nuovo byte e produttore è disponibile ad iniziarne una nuova
1. S1: $soc,eoc=1,1$ : consumatore è pronto
2. S2: $soc,eoc=1,0$ : produttore inizia produzione
3. S3: $soc,eoc=0,0$ : consumatore notifica di aver capito e non chiede più altri dati
4. S0: $soc,eoc=0,1$ : il produttore ha finito e il consumatore preleva il dato
