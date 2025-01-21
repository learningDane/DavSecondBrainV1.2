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
# D Flip-Flop
Si dicono flip-flop gli elementi di memoria non trasparenti.
```verilog
module dff ( 	
	input 	d,
	input 	clk,
	input 	rstn,
	output reg	q);

	// Contents of the module
	always @ (posedge clk) begin
		if (!rstn)
			q <= 0;
		else
			q <= d;
	end
endmodule
```
