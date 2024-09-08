#uni 
# Come svolgere esercizi
su [[Linux]] al posto di SQL/mySQL si usa [[MariaDB]]. Per fare gli esercizi bisogna prima far partire mariadb con `systemctl start mariadb.service`, poi entrare in Data Grip oppure MySQL Workbench. Per connettersi a mariadb: root & root.

Sia dato il seguente schema di tabella:
STUDENTE (Matricola, Cognome, Nome, DataNascita, DataIscrizione, DataLaurea,
NumeroEsamiSostenuti, Facolta),
esprimere le seguenti richieste in linguaggio MySQL:
	- Indicare matricola degli studenti che non si erano ancora laureati il 15 Luglio 2005.
	- Indicare matricola e cognome degli studenti il cui percorso di studi è durato (o dura da) oltre sei anni.
	- Indicare nome, cognome ed età degli studenti laureati quest’anno in Lettere (durata standard 5 anni a ciclo
	unico), non fuori corso e come minimo con un anticipo di sei mesi rispetto alla durata standard.
	- indicare matricola e cognome degli studenti laureati fuori corso, cioè oltre il mese di Aprile del 6° anno,
	nell’anno accademico 2009-2010.
```MySQL
Sia dato il seguente schema di tabella:
STUDENTE (MATRICOLA, Cognome, Nome, DataNascita, DataIscrizione, DataLaurea, NumeroEsamiSostenuti, Facolta)

1. Indicare matricola degli studenti che non si erano ancora laureati il 15 Luglio 2005.
SELECT Matricola
FROM Studente
WHERE DataLaurea > '2005-07-15'
	OR DataLaurea IS NULL;

2. Indicare matricola e cognome degli studenti il cui percorso di studi è durato (o dura da) oltre sei anni.
SELECT Matricola, Cognome
FROM Studente
WHERE (DataLaure IS NOT NULL AND DataIscrizione + INTERVAL 6 YEAR < DataLaurea)
	OR (DataIscrizione + INTERVAL 6 YEAR < CURRENT_DATE AND DataLaurea IS NULL);

3. Indicare nome, cognome ed età degli studenti laureati quest’anno in Lettere (durata standard 5 anni a ciclo unico), non fuori corso e come minimo con un anticipo di sei mesi rispetto alla durata standard.
SELECT Nome, Cognome, DATEDIFF(CURRENT_DATE, DataNascita)/365
FROM Studente
WHERE YEAR(DataLaurea) = YEAR(CURRENT_DATE)
	AND Facolta = 'lettere'
	AND DataIscrizione + INTERVAL 5 YEAR > DataLaurea + INTERVAL 6 MONTH;

4. Indicare matricola e cognome degli studenti laureati fuori corso, cioè oltre il mese di Aprile del 6° anno, nell’anno accademico 2009-2010.
SELECT Matricola, Cognome
FROM Studente
WHERE (DataLaurea > '2010-04-30' AND DataLaurea < '2011-01-01')
	AND (DataIscrizione > '2003-04-30' AND DataIscrizione < '2004-04-01');
```
es:
```MySQL
Indicare cognome e nome delle persone di età inferiore a 40 anni
SELECT Cognome, Nome
FROM Persona
WHERE Età < 40;

indicare tutte le informazioni di blah blah
SELECT *
ecc

indicare il codice fiscale delle persone di età inferiore a 40 anni il cui cognome è Lepre
WHERE Età < 40
	AND Cognome = 'Lepre';

Indicare codice fiscale ed età delle persone il cui cognome è Nutrie o il cui nome è Maddalena
WHERE Cognome = 'Nutrie'
	OR Cognome = 'Maddalena';

Indicare cognome e nome delle persone di età compresa fra 45 e 60 anni
WHERE Età BETWEEN 45 AND 60;
oppure
WHERE Età >= 45
	AND Età <= 60;

Indicare i cognomi delle persone di età almeno pari a 38 anni (togli duplicati)
SELECT DISTINCT Cognome
etc
WHERE Età >= 38;

Indicare la matricola degli studenti non ancora laureati
WHERE DataLaurea IS NOT NULL;

Indicare matricola e data di laurea (nel formato ‘dd|mm|yyyy, nome_giorno’) degli studenti iscritti prima del 2005
SELECT Matricola, DATE_FORMAT(DataLaurea, '%d|%m|%y,%W')
FROM Studente
WHERE DataIscrizione < '2005-01-01';

Indicare la matricola degli studenti che si sono laureati di mercoledì
SELECT Matricola
FROM Studente
WHERE DATE_FORMAT(DataLaurean, '&w')=3;

Indicare matricola e mese di laurea degli studenti immatricolati dopo il 2000
SELECT Matricola, MONTH(DataLaurea)
FROM Studente
WHERE YEAR(DataLaurea) > 2000;

Indicare il cognome degli studenti che si sono laureati cinque anni fa
WHERE DataLaurea IS NOT NULL
	AND YEAR(DataLaurea) = YEAR(CURRENT_DATE)-5;

Indicare matricola e da quanti giorni risultavano iscritti gli studenti, ad oggi laureati, che non si erano ancora laureati il 15 Luglio 2005
SELECT Matricola, DATEDIFF('2005-07-15',DataIscrizione)
FROM Studente
WHERE DataLaurea IS NOT NULL
	AND DataLaurea > '2005-07-15';

Indicare la matricola e il mese di iscrizione degli studenti che si sono laureati dopo cinque anni esatti dal giorno dell’iscrizione
SELECT
FROM Studente
WHERE DataLaurea = DATE_ADD(DataIscrizione, INTERVAL 5 Year);
oppure
WHERE DataLaurea = DataIscrizione + INTERVAL Year;

Indicare il numero di visite effettuate in data 1° Marzo 2013
SELECT COUNT(*) AS VisitePrimoMarzo
FROM Visita
WHERE Data = '2013-03-01'; 

STUDENTE (Matricola, Cognome, Nome, DataNascita, ColoreCapelli, Fila)
1. Contare gli studenti della prima fila
SELECT COUNT(*)
FROM STUDENTE
WHERE Fila = 'Prima';
2. Contare i colori di capelli degli studenti della prima fila
SELECT COUNT(DISTINCT ColoreCapelli)
FROM STUDENTE
WHERE ColoreCapelli
	AND Fila = 'Prima';
1. Contare i colori di capelli degli studenti della prima fila ignorando gli studenti il cui colore di capelli non è noto
SELECT COUNT(DISTINCT ColoreCapelli)
FROM STUDENTE
WHERE ColoreCapelli IS NOT NULL
	AND Fila = 'prima';

semplice somma
SELECT SUM(Reddito) AS RedditoTotale
ecc

semplice media
SELECT AVG(Reddito) AS RedditoMedio
ecc

indicare il reddito massimo e nome e cognome di chi lo detiene
SELECT MAX(Reddito), Nome, Cognome
FROM Paziente;
```
---
```MySQL
SELECT Matricola
FROM STUDENTE
WHERE DataLaure IS NULL
---
SELECT Matricola, Cognome
FROM STUDENTI
WHERE YEAR(DATEDIFF(DataLaurea, DataIscrizione)) > 6
	OR DATEDIFF(CURRENT_DATE, DataIscrizione) > 6;
---
SELECT Nome, Cognome, YEAR(CURRENT_DATE, DataNascita)
FROM STUDENTI
WHERE YEAR(DataLaurea) = YEAR(CURRENT_DATE)
	AND Facoltà = Lettere;
---
SELECT Matricola, Cognome
FROM STUDENTI
WHERE YEAR(DataIscrizione) < 5
	AND DataLaure > '2010-05-30'
	AND DataLaurea < '2011-1-1'
```
• Indicare l’incasso totale degli ultimi due anni, realizzato grazie alle visite dei
medici cardiologi della clinica.

• Indicare il numero di pazienti di sesso femminile che, nel quarantesimo anno
d’età, sono stati visitati, una o più volte, sempre dallo stesso gastroenterologo.

• Indicare l’età media dei pazienti mai visitati da ortopedici.

• Indicare nome e cognome dei pazienti che sono stati visitati non meno di due
volte dalla dottoressa Gialli Rita.

• Indicare il reddito medio dei pazienti che sono stati visitati solo da medici con
parcella superiore a 100 euro, negli ultimi sei mesi.
- indicare medico, paziente e data delle __visite di controllo__ del mese di Gennaio 2016
```MySQL
SELECT V1.Medico, V1.Paziente, V1.Data
FROM Visita V1
WHERE MONTH (V1.Data) = 1
	AND YEAR(V1.Data) = 2016
	AND EXISTS
		(
		SELECT *
		FROM Visita V2
		WHERE V2.Medico = V1.Medico
			AND V2.Paziente = V1.Paziente
				AND V2.Data < V1.Data
			);
```
###### Indicare mat dei med che hanno visitato per la prima volta almeno un paziente nel mese di Ottobre 2013
```MySql
SELECT DISTINCT V1.Medico
FROM Visita V1
WHERE YEAR(V1.Data) = 2013
	AND MONTH(V1.Data) = 10
	AND NOT EXISTS (
		SELECT *
		FROM Visita V2
		WHERE V2.Medico = V1.Medico
			AND V2.Paziente = V1.Paziente
			AND V2.Data < V1.Data)
```
###### Indicare nome e cogn dei paz che sono stati visitati non meno di due volte dalla dottoressa Gialli Rita
  tabelle:
	  paziente> nome, cognome
	  visita>
	  Medico> nome, cognome
condizioni sui record:
	1. medico = Rita Gialli (nome e cognome)
```MySQL
SELECT
FROM
GROUP BY
HAVING
```