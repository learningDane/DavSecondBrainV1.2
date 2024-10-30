#uni 
Serve per generare una Valutazione Inferiore nel [[Problema di Copertura]].
1. Ordino le postazioni per il loro costo unitario, ovvero il costo di apertura diviso per la somma degli utenti coperti.
2. Apro la postazione con costo unitario minimo, ne cancello la colonna e ne cancello le righe che serve e depenno la postazione.
   Inoltre cancello le righe di tutti $1$ se si presenta.
3. Se ho ancora righe:
   Ricalcolo i costi unitari, ovvero il costo di apertura diviso per la somma degli utenti, non depennati, coperti.
   Torno al punto `2`.