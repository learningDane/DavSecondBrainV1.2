#uni 
Questi sono i comandi per la compilazione ed il linking:
File singolo:
	compilazione:
		`g++ -c main.cpp -o main.obj`
	linking:
		`g++ main.obj -o main.exe`
File multipli:
	compilazione:
		`g++ -c main.cpp -o main.obj`
		`g++ -c file.cpp -o file.obj`
	linking:
		`g++ main.obj file.obj -o main.exe`
	compilazione e linking insieme:
		`g++ main.cpp file.cpp -o main.exe`
	esecuzione:
		`main` 
--
___In generale quindi___:
	`g++ main.cpp +altriFile.cpp -o main.exe` 
--
In Linux:
	`g++ main.cpp compito.cpp -o main`
	esecuzione:
		`./main` 