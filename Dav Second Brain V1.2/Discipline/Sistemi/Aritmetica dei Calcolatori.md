#uni 
# Estensore di Campo per Interi
```Verilog
// β=2
// duplico la cifrà più significativa di A
wire [M-1:0] V={M{A[N-1]}};
assign Aest={V,A};
```
# Riduttore di Campo per Interi
```Verilog
// β=2
// produco ow flag in base allo xor delle due cifre più significative
// elimino cifra più significativa
// caso riduzione unitaria
assign ow=A[L-1]^A[L-2];
assign Arid=A[L-2:0];

//caso generale, con riduzione di M
assign ow=(&A[L-1:N-1])^(|A[L-1:N-1]); //scoprire se le M+1 cifre più significative di A sono uguali tra loro: & e | devono dare lo stesso risultato
assign Arid=A[N-1:0];
```
# Negatore
```Verilog
//se a coincide con l'estremo negativo ovvero A=β^(n) / 2, l'opposto non esiste
wire [N-2:0] zero={(N-1){'B0}};
wire [N-1:0] estremonegativo={1'B1,zero};
assign ow=(A==estremonegativo)?1:0;
assign Aopp= ~A+1;
```
# Sommatore per Interi
```Verilog
//si estendono gli addendi di una cifra
//fare somma su N+1 cifre
//ridurre somma di una cifra, se ow=1, la somma non era fattibile su N cifre
assign Sest={A[N-1],A}+{B[N-1],B};
assign ow={Sest[N]==Sest[N-1])?0:1;
assign S=Sest[N-1:0];
//su β=2 possiamo evitare l'estensione e semplicemente ricavare ow dallo xor dei due riporti più significativi
```
# Sottrattore per Interi
```Verilog
assign Dest={A[N-1],A}-{B[N-1],B};
assign ow={Dest[N]==Dest[N-1])?0:1;
assign D=Dest[N-1:0];
//su β=2 possiamo evitare l'estensione e semplicemente ricavare ow dallo xor dei due riporti più significativi
```
# Comparatore per Interi
```Verilog
assign Dest={A[N-1],A}-{B[N-1],B};
assign flag_min=Dest[N];
assign flag_eq= ~(|Dest)
```
# Estrattore del Valore Assoluto
```Verilog
assign ABS_a==(A[N-1]==0) ? A : (~A+1);
```
# Moltiplicatore Interi
```Verilog
//convertiamo moltiplicandi da CR a MS
//segno=XOR segni
//modulo=prodotto naturale tra moduli
//riconvertiamo MS->CR
assign segno_a=A[N-1];
assign segno_b=B[N-1];
assign segno_p=segno_a ^ segno_b,
	ABS_p=ABS_a*ABS_b;
assign P=(segno_p==0) ? ABS_p : (~ABS_p+1);
```
# Divisore Interi
```Verilog
assign segno_a=A[L-1],
	ABS_a=(segno_a==0) ? A : (~A+1);
assign segno_b=B[L-1],
	ABS_b=(segno_b==0) ? B : (~B+1);
assign no_div=(ABS_a[L-1:N-1]<{ABS_b,1'B0}) ? 0 : 1,
	segno_q=segno_a ^ segno_b,
	ABS_q=ABS_a/(~ABS_b);
assign segno_r=segno_a,
	ABS_r=ABS_a%(~ABS_b);
wire[N-2:0] zero={(N-1){'B0}};
wire[N-1:0] estremonegativo={1'B1,zero};
assign ow_conv_q=(ABS_q>(estremonegativo)) | ((ABS_q==(estremonegativo))&(segno_q==0));
assign no_idiv=no_div | ow_conv_q;
assign Q=(segno_q==0) ? ABS_q : (~ABS_q+1);
assign R=(segno_r==0) ? ABS_r : (~ABS_r+1);
```