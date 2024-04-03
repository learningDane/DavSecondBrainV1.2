#self-taught 
bash script: `nome.sh` 
`cat file.txt | grep "robaDaCercare"` restituisce solo la riga con la ricerca
`ping indirizzo -c 3` fa il ping 3 volte, `-c` conta il numero di ripetizioni da fare
`cat file.txt | grep "robaDaCercare" | cut -d " " -f 4` prende solo la quarta parola, -d è il delimitatore.
`cat file.txt | grep "robaDaCercare" | cut -d " " -f 4 | tr -d ":"` toglie `:`, tr sta per translate