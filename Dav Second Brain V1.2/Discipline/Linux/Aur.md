#self-taught 
La Aur "Arch User Repository" è una repo con tanti programmi.
# Scaricare applicazioni
Preferibilmente scaricare i pacchetti in una cartella apposta eg. `/Downloads/git` 
`git clone https://aur.archlinux.org/applicazione.git` 
entrare nella cartella
`cd applicazione` 
Costruire il pacchetto
	`makepkg` 
	Se da errore `public key is unknown` usare il comando: `gpg --recv-key KEY` sostituire `KEY` con la chiave che emette durante l'errore. Poi rilanciare il `makepkg`.
	Poi `ls` , copia il nome del file e:
	`sudo pacman -U nome-del-file`
Oppure
	`makepkg -sri` 
# Aur Helper
## YAY
Yay è uno Aur Helper.
###### Cercare
`yay nomeapp`
per cercare sia sulle repo officiali sia sulla AUR:
`yay -Ss nomeapp`
###### Installare un pacchetto
`yay -S nomeapp`
###### Rimuovere un pacchetto
`yay -R nomeapp`
Per rimuovere un pacchetto e le sue dependencies: 
`yay -Rns nomeapp`
Rimuovere dependencies inutilizzate a livello globale:
`yay -Yc` 