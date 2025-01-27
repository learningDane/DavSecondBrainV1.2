#uni 
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
Le reti di Moore sono reti ___NON trasparenti___.
Sono composte da due [[Rete Combinatoria]] e un Registro STAR.
- La rete RCa, funzione di SIP e X, definisce il SIS
- Il registro STAR contiene il SIP
- la rete RCz, funzione di STAR, definisce Z
# Leggi di Temporizzazione
- $T ≥ T_{hold} + T_{amonte} + T_A + T_{setup}$ 
- $T≥ T_{propagation} + T_A + T_{setup}$ $\to$ meno stringente della prima e può essere ignorata
- $T≥ T_{propagation} + T_Z + T_{avalle}$ 