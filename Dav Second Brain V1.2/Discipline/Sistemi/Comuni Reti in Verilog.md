#uni 
# Latch SR
Si dicono Latch gli elementi di memoria trasparenti.
```Verilog
module Latch_SR(q,qN,s,r);
	input s,r;
	output q,qN;
	assign #1 q= ~(r|qN);
	assign #2 qN= ~(s|q);
	endmodule
```
# D Latch (reg)
```Verilog
reg D_LATCH;
	assign q=D_LATCH;
	alway @(reset_==0) #1 D_LATCH<=bit_iniziale 
	alway @(c or d) if (reset_==1) #2 D_LATCH <= (c==1) ? d : D_LATCH;
	//"quando c o d cambiano valore"
	// <= assegnamento procedurale non bloccate
	//se si vuole bitiniziale=1 : /preset collegata a /reset, /preclear collegata a Vcc
	//se si vuole bitiniziale=0 : il contrario
	//se non interessa al reset, togliere reset dalla descrizione e collegare nella sintesi /preset e /preclear a vcc
```
# D flip flop (positive edge triggered D flip flop)
Si dicono flip-flop gli elementi di memoria non trasparenti.
```Verilog
reg D_EDGE;
	assign q = D_EDGE;
	always @(reset_ == 0) #1 D_EDGE <= bit_iniziale;
	always @(posedge p) if (reset_ == 1) #3 D_EDGE <= d;
	//#3 è Tpropagation
```
# RAM statica 8Mx8bit
```Verilog
module RAM(d3_d0,a22_a0,s_,mr_,mw_);
	input[22:0] a22_a0;
	input s_, mw_, mr_;
	inout[3:0] d3_d0;
	reg[3:0] LOCATION[0:8388607];
	wire b; assign b=({s_,mr_,mw_}== 'B001) ? 1:0;
	wire c; assign c=({s_,mr_,mw_}== 'B010) ? 1:0;
	//ciclo di lettura
	assign #Tread d3_d0=(b==1) ? LOCATION[a22_a0]:'HZ;
	//ciclo di scrittura
	always @(c or d3_d0) #Twrite LOCATION[a22_a0] <= (c==1) ? d3_d0 : LOCATION[a22_a0];
	endmodule
```
# Registro
```Verilog
reg[W-1:0] registro;
wire clock, reset_;
wire[W-1:0] dW-1_d0;
wire[W-1:0] qW-1_q0;
assign qW-1_q0 = registro;
always @(reset_ == 0) registro <= contenutoiniziale;
always @(posedge clock) if (reset_ == 1) #Tpropagation registro <= dW-1_d0;
```
# Contatore Up su Naturali
```Verilog
module ContatoreUpNcifreBaseB(numero, clock, reset_)
input clock, reset_;
output[N-1:0] numero;
reg[N-1:0] OUTR;
assign numero = OUTR;
always @(reset_ == 0) #1 OUTR <= contenutoniziale;
always @(posedge clock) if (reset_ == 1) #3 OUTR <= numero + 1;
endomdule
```
# Rete di Moore
```Verilog
module Rete_di_Moore( z, x, clock, reset_); //o (Xn-1,...,x=X0, Zm-1,...,Z0,etc)
	input clock, reset_;
	input[N-1:0] x;
	output[M-1:0] z;
	reg[W-1:0] STAR;
	parameter S0 = codifica0, S1 = codifica1, Sk-1 = codificak-1;
	assign {zM-1,...,z0} = (STAR == S0) ? ZS0 :
		(STAR == S1) ? ZS1 :
		...
		/*(STAR == Sk-1) */ ZSk-1;
	always @(reset_ == 0) #1 STAR<=statointernoiniziale;
	always @(posedge clock) if (reset_ == 1) #3
		casex(STAR)
			S0 : STAR <= AS0(xN-1,...,x0);
			S1 : ...
			..
			Sk-1 : STAR <= ASk-1(xN-1,...,x0);
		endcase
	endmodule
```
# Flip Flop JK
Specifiche: quando arriva il segnale di sincronizzazione se lo stato di ingresso JK è:
10-setta, 01-resetta, 00-conservazione, 11-commutazione.
```Verilog
module Flipflopjk( j, k, q, reset_, clock);
	input reset_, clock;
	input j,k;
	output q;
	reg STAR;
	parameter S0 = 'b0, S1 = 'b1;
	assign q = (STAR == 0) ? 0 : 1;
	always @(reset_ == 0) #1 STAR <= S0;
	always @(posedge clock) if (reset_ == 1) #3 
		casex(STAR)
			S0 : STAR<=(j==0) ? S0 : S1;
			S1 : STAR<=(k==0) ? S1 : S0;
		endcase
	endmodule
```
# Riconoscitore di Sequenze
11 01 10
```Verilog
module riconoscitore(x, z, reset_, clock);
	input reset_, clock;
	input[1:0] x;
	output z;
	reg[1:0] STAR;
	parameter s0 : 00, s1:01 , s2:10 , s3:11;
	assign z = (STAR == S3) ? 1 : 0;
	always @(reset_ == 0) #1 STAR <= s0;
	always @(posedge clock) if (reset_ == 1) #3 
		casex(STAR)
			s0 : STAR<= (x == 'b11) ? s1 : s0;


   00 01 11 10
s0 s0 s0 s1 s0
s1 s0 s2 s1 s0
s2 s0 s0 s1 s3 
s3 s0 s0 s1 s0
```
# Rete di Mealy
```Verilog
module Rete_di_Mealy(x, z, clock, reset_);
	input clock, reset_;
	input[N-1:0] x;
	output[M-1:0] z;
	reg[W-1:0] STAR;
	parameter S0:codifica0 , S1:codifica1, ... Sk-1:codificak-1;
	assign z = (STAR == S0) ? Zs0(x) : //legge Z
		...
		/* (STAR == Sk-1) ? */ Zsk-1(x);
	always @(reset_ == 0) #1 STAR <= statointernoiniziale;
	always @(posedge clock) if (reset_ == 1) #3 casex(STAR)
		S0: STAR <= As0(x); //legge A
		...
		Sk-1: STAR <= Ask-1(x);
		endcase
	endmodule
```
# Rete di Mealy Ritardato
```Verilog
module Rete_di_Mealy(x, z, clock, reset_);
	input clock, reset_;
	input[N-1:0] x;
	output[M-1:0] z;
	reg[W-1:0] STAR;
	parameter S0:codifica0 , S1:codifica1, ... Sk-1:codificak-1;
	reg[M-1] OUTR;
	assign z = OUTR;
	
	always @(reset_ == 0) #1 begin 
		STAR <= statointernoiniziale;
		OUTR <= ZSiniziale;
	
	always @(posedge clock) if (reset_ == 1) #3 casex(STAR)
		S0: begin
			STAR <= As0(x);
			OUTR <= Zs0(x); end
		...
		Sk-1: begin 
			STAR <= Ask-1(x);
			OUTR <= Zsk-1(x); end
		endcase
	endmodule
```
# RSS complesse
```Verilog
module RSScomplessa(x, z, clock, reset_);
	input clock, reset_;
	input[N-1:0] x;
	output[M-1:0] z;
	reg[...] Rq-1;
	...
	reg[...] R0;
	reg[W-1:0] STAR;
	parameter S0:codifica0 , S1:codifica1, ... Sk-1:codificak-1;
	reg[M-1] OUTR;
	assign z = {Rq-1,...,R0}; //tutti i registri o solo una parte
	
	always @(reset_ == 0) #1 begin 
		STAR <= statointernoiniziale;
		Rq-1 <= statoiniziale
		...
		R0 <= statoiniziale
	
	always @(posedge clock) if (reset_ == 1) #3 casex(STAR)
		S0: begin
			STAR <= As0(x,Rq-1,...,R0);
			Rq-1 <= Rs0,q-1(x,Rq-1,..,R0); 
			...
			R0 <= Rs0,0(x,Rq-1,...,R0); end
		...
		Sk-1: begin 
			STAR <= Ask-1(x,Rq-1,...,R0);
			Rq-1 sk-1,q-1(x,Rq-1,...,R0);
			...
			R0 sk-1,0(x,Rq-1,...,R0); end
		endcase
	endmodule
```
# Rete parte operativa-parte controllo
```Verilog

```
