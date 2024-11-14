#uni 
abbiamo adesso due registri: STAR e OUTR.
A STAR assegno quello che gli compete secondo la legge A, a OUTR assegno quello che gli compete secondo la legge B, che dipende da STAR.
Questi assegnamenti arrivano contemporaneamente all'arrivo del clock, quindi l'ordine con cui li scrivo è ininfluente.
`S0 : begin STAR <= S1; OUTR<=STAR; end`, che valore memorizza OUTR all'arrivo del clock? Il contenuto di STAR ___PRIMA___ del clock!!! Perché è NON TRASPARENTE.
È il motivo per cui l'istruzione `XCHG` ([[Assembly]]) funziona.
Non posso quindi nello stesso `begin-end` contemporaneamente assegnare un valore ad un registro ed usare il nuovo valore. 