#self-taught 
Navigazione tra cartelle:
	`ls` lista tutti i file e le cartelle presenti nella cartella presente
		`ls -la` mostra anche cartelle nascoste
		`l` mostra le cose in formato lungo: `-` indica un file `d` indica una directory, le lettere dopo indicano _read, write, execute_ per ogni classe di user. Il primo è il proprietario, il secondo è il gruppo di user che detiene il file, il terzo è tutti gli altri.
	`cat nomefile` restituisce il contenuto di un file
	`pwd` restituisce il nome e il path della cartella corrente
	`cd` permette di accedere ad una cartella visibile nella path attuale
	`cd ..` fa in modo di tornare alla cartella superiore a quella attuale
	se invece voglio digitare l'intero path devo partire da `/` e digitare il path: `ls /home/user/eccetera` 
	`locate nome` trova il nome (`updatedb` aggiorna il database)
Creare/spostare/copiare/cancellare file e cartelle
	`mkdir nomeCartella` crea una cartella dal nome indicato
	`touch nomeFile` crea un file dal nome indicato
	`cp file path` e `mv` copiano/muovono la cartella da un posto all'altro
	`rm nomefile`  cancella il file
	`rmdir` cancella cartella
	`rm -R nomecartella` cancella la cartella e tutto il contenuto (in modo ricorsivo)
Compilare un singolo file in [[C++]] 
	`g++ [opzioni] -o eseguibile sorgente.cpp` 
	[[Compilazione e Linking]] 
Eseguire programma
	`./eseguibile` 
Tastiera
	`setxkbmap nomeTastiera` cambia la tastiera (it=italiano, us=international) 
Root / Sudo
	`sudo` permette ad un utente qualsiasi di lanciare comandi da root.
	`sudo su -` permette di cambiare l'istanza attuale a root.
Password / aggiungere user
	`passwd` ti fa cambiare la password
	`adduser nome` 
	in `etc/passwd` trovi tutti gli utenti
	in `etc/shadow` trovi le password ma è un file nascosto e protetto
Aiuto
	`man nomecomando` e `nomecomando --help` mostrano un manuale
scrivere roba in un file
	`echo "testodainserire" > nome del file` 
cambiare i permessi di un file/cartella
	`chmod` e poi `+rwx` o `+x` o `777`(tutti i privilegi a tutti) e poi `il nome`