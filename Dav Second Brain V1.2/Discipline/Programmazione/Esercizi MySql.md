#uni 
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