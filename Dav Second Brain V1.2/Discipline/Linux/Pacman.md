#self-taught 
Pacman è il Package Manager di [[Arch]].
`pacman -S` di solito serve per sincronizzare/installare (`pacman -Syu` aggiorna tutte le app)
	`y` sincronizza dai Mirror
	`yy` force-synchronises le app
	`u` aggiorna i programmi che sono stati sincronizzati
	`w` scarica gli aggiornamenti ma non aggiorna
	`s` cerca sulla repository
	`c` chiede se vuoi rimuovere tutti i pacchetti obsoleti
`pacman -Q` serve per cercare
	`e` mostra i programmi che ho esplicitamente scaricato
	`q` fa sì che non vengano mostrati versione eccetera delle app
	`n` mostra i programmi scaricati da main repositories
	`m` mostra tutti i programmi installati dalla ___Aur___.
	`dt` mostra le dependencies che non vengono più usate dai programmi, gli "orfani".
	`s` mostra gli elementi nella repository locale
	con `| wd -l` restituisci il numero di elementi
`pacman -R` serve per rimuovere (`pacman -Rsc` rimuove l'app indicata e tutto ciò che ha creato)
	`n` rimuove le dependencies create dalle app
	`s` rimuove i file creati dalle app
	`c` rimuove solo le dependencies che non servono più