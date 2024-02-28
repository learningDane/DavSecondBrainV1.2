#uni 
Structured Query Language.
Questo è un linguaggio ___dichiarativo___ per interagire con database relazionali, a differenza del [[C++]], che è un linguaggio procedurale.
Dichiarativo vuol dire che dichiari le proprietà del risultato invece di scrivere come lo si ottiene.
Gli _statement_ dell'SQL sono fatte da tre componenti, uno statement anche se va a capo non termina fino a che non si inserisca un punto e virgola.
In un database vi sono più tabelle e possono essere combinate per formare una lista di tabelle. 
SQL non è Case Sensitive.
### Chiave
La chiave è l'identificatore di un ___Record___, è unica e quindi non può ripetersi e non può essere NULL.
### Query
```MySQL
SELECT Cognome, Nome  //proiezione  //oppure SELECT * se vuoi tutti gli attributi
FROM Persona          //fonte
WHERE Età < 40;       //condizione
```
Condizioni più espressive si ottengono con gli operatori logici:
```SQL
SELECT  CodiceFiscale
FROM Persona
WHERE Età < 40
	AND Cognome = 'Lepre';
```
### Direttive
BETWEEN = `WHERE Età BETWEEN 45 AND 60;` oppure `WHERE Età <= 60 AND Età >= 45;` include sempre gli estremi.
### Valori NULL
Gli attributi non chiave possono essere NULL, ovvero l'informazione manca. Quando nelle condizioni viene esaminato un attributo NULL, a priori assume False, anche NULL=NULL è falso. Se voglio cercare attributi NULL devo usare IS, se voglio attributi non NULL devo usare IS NOT NULL.
NULL ha valore mancante ma può avere un significato logicamente definito (per esempio dataLaurea è NULL = non laureato). 
### Duplicati
In una tabella non ci sono mai due ___record___(righe) uguali. Due record sono uguali se il valore degli attributi corrispondenti è uguale per tutti gli attributi, i valori degli attributi non chiave invece possono ripetersi.
Se la query restituisce alcuni stessi valori più volte, posso scegliere di eliminarli con DISTINCT. `SELECT DISTINCT Cognome ecc`, questa parola chiave agisce su tutti gli attributi proiettati.
### Date
Una data è il tempo trascorso da un reference, che come in tutti i sistemi UNIX è 01/01/1970. Se la data è negativa è precedente alla Reference.