#uni 
Per compilare:
```zsh
~/cartellaProgetto> iverilog -o sim ./rc.v ./testbench
vvp ./sim
gtkwave.exe ./waveform sim &


//in mac: gtkwave waveform.vcd
```
# Struttura di un Sistema
```Verilog
module sistema;
	wire w; //variabile binaria di tipo wire di nome locale w
	trasmettitore T(w); //oggetto modulo trasmettitore di nome locale T, collegato con w
	ricevitore R(w); // "
	endmodule

module trasmettitore (z);
	output z;
	//descrizione della struttura interna
	endmodule

module ricevitore (x);
	input x;
	//etc
	endmodule
```
# Dimensionamento Variabili
```Verilog
module retetotale (x3_x0, z7_z0);
input[3:0] x3_x0;
output[7:0] z7_z0;
wire[3:0] a_R1,a_R2;
wire[11:0] sum11_sum0;
assign a_R1=x3_x0;
assign a_R2=z7_z0[3:0]; //assegno la parte bassa di z7_z0
assign sum11_sum0={a_R1,a_R2}; //assegno a sum la concatenazione ar1,ar2
endmodule
//z7_z0 è solo un nome, non indica a verilog che è a 8 bit

costante:
Nbit'configurazionebit:
8'10010100 //anche scritto come 8'1001_0100, underscore viene ignorato
8'1011 //mancano 4 bit, sostituiti da 0 in testa = 8'0000_1011
esadecimale:
N'Hconfigurazione
16'H9c7
base dieci:
N'Dconfigurazione
16'D40023
numero N di bit può essere omesso quando ricavabile dal contesto
se non ricavabile automaticamente N=32
se omessa base allora considerata base 10

Parametri
parameter[N-1:0] nomeparametro=costante, altroparamtetro=costante;
parameter parametro='B01011 equivale a scrivere [31:0] perché omesso N

UNA VARIABILE BINARIA HA 4 VALORI POSSIBILII: 1'B0, 1'B1, 'BZ , 'BX
altaimpedenza=associata a un filo flottante
valoreindefinita=valore ambiguo (per esempio tra 1V e 2V, con 0-1V=0 e 2-3V=1)
oppure valore privo di interesse

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
# Descrizione di una qualunque RC
```Verilog
module rete_combinatoria(z_{M-1},....,z_0, x_{N-1},...,x_0);
	input x_{N-1},...,x_0;
	output z_{M-1},...,z_0;
	assign #T {z_{M-1},...,z_0}={F_{M-1}(x_{N-1},...,x_0),
										F_{M-2}(x_{N-1},...,x_0),
										...
										F_0(x_{M-1},...,x_0) };
	endmodule

//esempio di RC p.34
assign #1 {z1,z0} = ({x2,x1,x0} == 3'B001) ? 2'B01 :
					({x2,x1} == 2'B01) ? 2'B10 :
					({x2,x1} == 2'B10) ? 2'B11 : 
													2'B00; //caso default
//che scritto sotto forma di funzione diventa:
function F[1:0] F;
	input x2,x1,x0;
	casex({x2,x1,x0})
		3'b001 : F='b01;
		3'b01? : F='b10;
		3'b10? : F='b11;
		default : F='b00
		endcase
	endfunction
```
# Definizione di Funzione
```Verilog
module rete_combinatoria(etc);
	input etc;
	output etc;
	assign #T {etc} = F(etc);
	function[M-1:0] F;
		input etc;
		etc;
		endfunction;
	endmodule;
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
# Modulo Top Level
Il modulo top level è il modulo non istanziato in nessun altro modulo e pertanto "contiene" gli altri. Dentro ogni modulo posso dichiararne altri, anche all'interno dello stesso file.
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
# Linguaggio di Trasferimento tra Registri
Un assegnamento allo STAR si chiama ___microsalto___ ($\mu$-salto).
In generale supponendo di avere $Q$ registri operativi, uno statement ha la seguente struttura:
```verilog
sj : begin
	assegnamenti ai registri operativi
	STAR <= espressione //microsalto (assegnamento a star)
end
```
È possibile omettere il comportamento di un registro OPERATIVO, in questo caso equivale a `registro <= registro` 
Non omettere mai l'assegnamento a STAR, farlo diminuisce la leggibilità. Se lo ometto è sottinteso che µ-salto è incondizionato e porta allo statement successivo nella descrizione.
Questo perché se invece fosse `STAR <= STAR` ci sarebbe un deadlock.
# Appendice
[[Comuni Reti in Verilog]] 