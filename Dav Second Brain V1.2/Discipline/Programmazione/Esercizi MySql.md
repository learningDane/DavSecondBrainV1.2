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
es:
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