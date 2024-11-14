#uni 
Per compilare:
```zsh
~/cartellaProgetto> iverilog -o sim ./rc.v ./testbench
vvp ./sim

gtkwave.exe ./waveform sim &
//in mac: gtkwave waveform.vcd
```
# Struttura Modulo
```verilog
module nomeModulo ( listadelleporte ); //porte dichiarate qua non si possono dichiare nel body del modulo

	//lista input/output
	.x , .y ,
	.c_in, .c_out

	[declaration_of_other_signals]

	[other_module_instantiations_if_required]

	comportamentoModulo
endmodule
```
# Struttura TestBench
```verilog
module nomeTestbench();

	//dichiarazione variabili input/output
	reg nome1;
	reg nome2;
	wire nome3;
	wire nome4;

	//instanziazione del design
	nomeModulo fa (
	//collegamento variabili
		.x (nome1) , .y (nome2)
		.c_in(nome3) , .c_out(nome4)
	)

	//comportamento
	initial begin

		//codice

	end
endmodule
```
# Modulo Top Leve
Il modul otop level è il modulo non istanziato in nessun altro modulo e pertanto "contiene" gli altri. Dentro ogni modulo posso dichiararne altri, anche all'interno dello stesso file.
# Operatori
### Unari
Appaiono a sinistra dell'operando
### Binari
Appaiono in mezzo agli operandi
### Terzari/Condizionali
`x = (y>5) ? y : 5;` 
# Numeri
### Formattazione
`bb..bb` : decimale
`0xbb..bb` : esadecimale
`10111000..01001` : binario
### Dimensionamento
Si indica il numero di bit con un numero decimale:
`[Nbit]'[prefissoFormattazione][numero]`
dove `prefissoFormattazione` può essere `b`=binario, `d`=decimale, `h`=esadecimale, `o`=ottale, le lettere possono anche essere maiuscole.
Se non specificato i numeri sono decimali e il numero di bit allocati dipende dal simulatore.
Si possono indicare numeri negativi tramite il segno `-` PRIMA di `Nbit`: `-4'b1001`
# Identificatori
Vengono usati per indicare variabili, sono composti da: `0-9 , a-z , A-Z , $ , _`
NON possono cominciare con una cifra o con `$`
# Tipi di Dato
Quasi tutti i tipi di dato in Verilog (a parte i Reali ed Evento) possono assumere solo i seguenti valori:
- 1
- 0
- x = (variabile 0/1)
- z = alta impedenza
# Keywords
Sono identificatori speciali riservati ai costrutti del linguaggio, una lista delle più importanti:
##### Structural Keywords
• module / endmodule: Define modules.
• input, output: Specify ports.
• wire, reg: Declare connections and variables.
##### Procedural and Behavioral Keywords
• always: Defines sequential logic.
• initial: Used for simulation setup.
• if / else, case: Conditional logic.
• posedge, negedge: Edge-triggered sensitivity.
##### Control and Timing
• #: Delay control.
• @: Event control for triggers.
##### Data Types
• integer, reg, wire: Common variable types.
##### Task and Function Keywords
• task, function: Define procedural blocks.
##### Simulation Keywords
• $display, $monitor, $stop, $finish: Simulation control and output.
# Appendice
[[Comuni Reti in Verilog]] 