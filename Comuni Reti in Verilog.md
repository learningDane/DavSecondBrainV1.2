#uni 
# D Flip-Flop
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
