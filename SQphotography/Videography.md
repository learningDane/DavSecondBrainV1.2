#self-taught 
# Video Codecs
H264/MPEG4/XAVC-S:
	più vecchio ma compatibile con tutto
	meno compressione
	adatto ad 8-bit
H265/HEVC/XAVC-HS:
	più compresso quindi file più piccoli oppure di qualità maggiore rispetto a H264
	adatto a 10-bit
PRORES/DNXHR/RAW:
	compatibile con tutto
	enormi file
	solo disponibile in alcune camera
	necessita di CFE cards o SSD
# Bit Depth
8-bit:
	256 colori per pixel
10-bit
	1024 colori per pixel
# Bit Rate
50mbps/6,25MB/s
200mbps/25MB/s
1MB/s=8mbps
10sec video @100mbps=125MB file size
___Per 4k @8-bit @24/25/30p si raccomanda 100mbps @h264___ oppure 50mbps @265
Per 4k @10-bit @24/25/30p si raccomanda 200mbps @h264 oppure 100mbps @h265
se raddoppi framerate devi raddoppiare bitrate.
se raddoppi risoluzione devi raddoppiare bitrate: $6k=2\cdot 4k$ 
# Video Encoding Techniques
ALL-INTRA salva tutti i frame per intero
LONG-GOP salva solo i cambiamenti, può andare bene per shot statici
# Picture Profiles
LOG, ogni manufatturiere ha il suo LOG, che è un profilo desaturato e a basso contrasto per mantenere più dati possibili e favorire il colo grading.
Fujifilm ha anche le film simulation.
Ci sono poi i profili CINE, simili al LOG. In Fujifilm è la film simulation ETERNA.
Se usi LOG conviene molto usare 10-bit, altrimenti puoi avere problemi durante il grading.