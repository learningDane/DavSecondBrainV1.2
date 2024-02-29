#uni 
Structured Query Language.
Questo è un linguaggio ___dichiarativo___ per interagire con database relazionali, a differenza del [[C++]], che è un linguaggio procedurale.
Dichiarativo vuol dire che dichiari le proprietà del risultato invece di scrivere come lo si ottiene.
Gli _statement_ dell'SQL sono fatte da tre componenti, uno statement anche se va a capo non termina fino a che non si inserisca un punto e virgola.
In un database vi sono più tabelle e possono essere combinate per formare una lista di tabelle. Dividere il database in più tabelle può s volgere diversi motivi, evitare anomalie, evitare ridondanza o distribuire dati.
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
Una data è il tempo trascorso da un reference, che come in tutti i sistemi UNIX è 01/01/1970 (___EPOCK___). Se la data è negativa è precedente alla Reference.
Formati:
	- DATE: YYYY-MM-DD
	- TIMESTAMP: YYYY-MM-DD HH:MM:SS
DATE_FORMAT:
	guarda tabella su slide- --------
Stampare nel seguente formato: ('dd||mm||yyyy, nome_giorno'): `SELECT Matricola, DATE_FORMAT(DataKaurea,'%d blah blah guarda slide')` -------------
Indicare la matricola degli studenti che si sono laureati di mercoledì: `WHERE DATE_FORMAT(DataLaurea, '%w') = 3;` 

Le funzioni DAY,MONTH,YEAR SLIDE --------------. `YEAR(DataIscrizione) > 2000;`
Indicare il cognome degli studenti che si sono laureati _5 anni fa_, si usa la parola chiave CURRENT_DATE: `WHERE YEAR(DataLaurea) = YEAR(CURRENTE_DATE) - 5;`

Le date in MySQL non possono essere sottratte tramite l'operatore '-', ma occorre usare `DATEDIFF()` : numero di giorni che separano due date: `SELECT Matricola, DATEDIFF('2005-07-15'-DataIscrizione)` prima viene la date più recente e poi quella più remota.
Non sottrarre o sommare date perché è bestemmia!!!
DATE_ADD e DATE_SUB permettono di sommare o sottrarre intervalli di tempo ad una data e vengono espressi con la keyword INTERVAL.
`INTERVAL NumeroInterno [YEAR|MONTH|DAY]`
`WHERE DataLaurea = DATE_ADD(DataIscrizione, INTERVAL 5 YEAR);`  oppure
`WHERE DataLaurea = DataIscrizione + INTERVAL 5 YEAR;`

Altre funzioni:
	- DAYNAME()
	- MONTHNAME()
	- DAYOFWEEK() //1,...,7
	- WEEKDAY() //0,...,6
	- LAST_DAY() //ultimo giorno del mese della data
	- DAYOFYEAR() //mese in 2 cifre
	- WEEKOFYEAR() //numero della settimana dell'anno
	- YEARWEEK() //anno e settimana
# Operatori
### Operatori di aggregazione
Permettono di eseguire calcoli i cui operandi sono i valori assunti da un attributo, in un insieme di record -> collassa in un solo record formato da un solo attributo numerico.
Accanto ad una aggregazione posso solo mettere un'altro aggregazione e non altro perchè la tabella scompare. 
1. conteggio: conta le righe slide che rientrano nella ricerca, conta i risultati.
	   `SELECT  count(*) AS VisitePrimoMarzo` restituisce il risultato con il nome VisitePrimoMarzo, quindi AS si chiama ___ridenominazione___, `COUNT(*)` non fa distinzione tra risultati e conta anche i duplicati. Se non voglio contare i duplicati devo usare `COUNT(DISTINCT Attributo)`
1. somma
	   `SELECT SUM(Reddito) AS RedditoTotale` 
1. minimo/massimo
	```SQL
	SELECT MAX(Reddito)
	FROM paziente;
	```
1. media
	   `SELECT AVG(Reddito) AS RedditoTotale`
# Query su più Tabelle
Per riunire le tabelle si utilizza `JOIN`. 
1. `natural join`
2. `inner join`
3. `left outer join`
4. `self join`
5. `cross join`
6. `right outer join`
affianca i record e li unifica in singole righe/
EG voglio indicare nome e cognome dei medici che hanno effettuato almeno una visita: 
```
SELECT DISTINCT M.Nome, M.Cognome
FROM Visita V
	INNER JOIN
	Medico M ON V.Medico = M.Matricola;
//dove V ed M sono Alias per le tabelle.
```
[[Esercizi MySql]] 