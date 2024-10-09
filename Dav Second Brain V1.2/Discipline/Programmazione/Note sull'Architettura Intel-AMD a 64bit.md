#uni 
# Registri
Un processore a 64 bit ha registri di 64 bit, indicati da 'r' .
Ci sono poi altri 8 registri generali aggiunti, da r8 a r15, di cui sono indirizzabili anche le loro parti basse a 32,16,8bit, con i rispettivi suffissi 'd', 'w', 'b'.
### Registri di Stato
RIP: instruction pointer a 64 bit
RFLAGS:
# Spazio di memoria
In teoria sono indirizzabili $2^{64}$ byte, in pratica invece le architetture rendono utilizzabili $2^{48}$ o $57$ byte (256 terabyte, 128 petabyte).
I bit in eccesso devono avere lo stesso valore all'ultimo bit.
Se si viola questa regola il processore da errore.
# Modifiche all'assembly
[[Assembly]]
I suffissi sono: 
- B per 8bit
- W per 16bit
- L per 32bit
- Q per 64bit
dichiarazione di variabile a 64bit:
`pippo: .QUAD x0123456789ABCDEF`
### Indirizzamento di memoria
Il displacement deve essere a 32bit e la scala può essere 1,2,4 e adesso 8.
Non si possono riferire operandi immediati a 64bit nelle istruzioni.
Non si possono riferire displacement a 64bit nelle. istruzioni.
##### MOVABS
È una versione della MOV che consente di utilizzare displacement a 64 bit, ottenendo quindi indirizzamento immediato del sorgente e displacement a 64bit.
Per esempio la LEA non accetta 64bit come siplacement quindi:
```assembly
.data
num1: .quad 0xecc

.text
.global _main
_main: NOP
	MOVABS $num1, %rax
	# $num1 è L'INDIRIZZO DI NUM1 non il valore.
```
### Altre modifiche
- LOOPx, REPx usano RCX invece di ECX
- (I)MUL a 64bit : RDX_RAX <- RAX * source
- (I)DIV a 64bit : dividendo in RDX_RAX, Q in RAX, R in RDX.
- traslazione e rotazione, operando sorgente deve essere ≤ 63(vengono mascherati i bit 6 e 7).