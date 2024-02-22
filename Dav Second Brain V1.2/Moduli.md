#uni 
Un modulo è una parte di programma che svolge una certa funzionalità e che risiede su uno o più file. Esistono moduli ___servitori___ e ___clienti___.
# Modulo Servitore
Un modulo servitore offre (esporta) risorse di varia natura, come funzioni, variabili e tipi. Questo è di norma costituito da due file, un `.h` ed un `.cpp`:
1. intestazione, ovvero dichiarazione dei servizi offerti.
2. realizzazione e corpo delle funzioni.
# Modulo Cliente
Utilizza e quindi importa risorse offerte dai moduli servitori, tramite l'inclusione del file di intestazione (`#include 'file.h'`).
Viene scritto senza conoscere i dettagli dei moduli servitori.
# Ricompilazione
La modifica di un file di intestazione richiede la ricompilazione di tutti i file che lo includono.
La modifica di un file di realizzazione richiede la sola ricompilazione dello stesso.
# .h
Questi file contengono l'intestazione di moduli.
# .cpp
Questi file contengono il codice da eseguire.
# .o
Questi file sono un prodotto intermedio della compilazione.