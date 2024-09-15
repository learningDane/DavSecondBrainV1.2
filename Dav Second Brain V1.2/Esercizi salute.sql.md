#uni 
```MySQL
Indicare il numero di pazienti aventi nome uguale ad almeno un medico della clinica
SELECT COUNT(DISTINCT P.CodFiscale) 
FROM Paziente P 
	CROSS JOIN 
	Medico M 
WHERE P.Nome = M.Nome;

Indicare le visite effettuate da medici che non lavorano più presso la clinica
SELECT V.* 
FROM Visita V 
	LEFT OUTER JOIN 
	Medico M 
		ON V.Medico = M.Matricola 
WHERE M.Matricola IS NULL

Indicare nome e cognome dei pazienti visitati dal dott. Rino Neri
select distinct paziente.nome, paziente.cognome
from visita 
	inner join 
    medico on visita.medico = medico.matricola
	inner join 	
    paziente on visita.paziente = paziente.codfiscale
where medico.nome = 'alvaro';

Indicare nome e cognome dei pazienti visitati nel mese Dicembre 2013, e il nome e cognome dei medici che li hanno visitati
select distinct paziente.nome as nomepaziente, paziente.cognome as cognomepaziente, medico.nome as nomemedico
from visita 
	inner join 
    medico on visita.medico = medico.matricola
	inner join 	
    paziente on visita.paziente = paziente.codfiscale
where year(visita.data)=2013 and month(visita.data)=12;

Indicare il codice fiscale dei pazienti che sono stati visitati più di una volta da uno stesso medico della clinica, nel mese corrente
SELECT DISTINCT V1.Paziente 
FROM Visita V1 
	INNER JOIN 
	Visita V2 ON ( 
		V2.Medico = V1.Medico 
		AND V2.Paziente = V1.Paziente 
		AND V2.Data <> V1.Data
		) 
WHERE DATE_FORMAT(V1.Data, ‘%Y%m’) = DATE_FORMAT(CURRENT_DATE, ‘%Y%m’) 
	AND DATE_FORMAT(V2.Data, ‘%Y%m’) = DATE_FORMAT(CURRENT_DATE, ‘%Y%m’)

Indicare la matricola dei medici che, nel mese di Ottobre 2013, hanno visitato per la prima volta almeno un paziente

Indicare la matricola dei medici che non hanno mai visitato di giovedì
SELECT DISTINCT V1.Medico 
FROM Visita V1 LEFT OUTER JOIN 
	( 
		SELECT V2.Medico                  |
		FROM Visita V2                    |-> derived table
		WHERE DAYOFWEEK(V2.Data) = 4      |
	) 
	AS D                              |-> alias (obbligatorio) della Derived Table
	ON V1.Medico = D.Medico |oppure| USING(Medico)
WHERE D.Medico IS NULL;
``
Indicare l’incasso totale degli ultimi due anni, realizzato grazie alle visite dei medici cardiologi della clinica
select sum(medico.parcella) as incassototale
from visita
	inner join medico
    on visita.medico = medico.matricola
where medico.specializzazione = 'cardiologia'
	and year(visita.data) >= year(current_date)-1;

Indicare il numero di pazienti di sesso femminile che, nel quarantesimo anno d’età, sono stati visitati, una o più volte, sempre dallo stesso gastroenterologo
select count(distinct d1.paziente) as numeropazientesse
from 
	(
		select *
		from paziente
			inner join visita
			on paziente.codfiscale = visita.paziente
		where year(paziente.datanascita + interval 40 year) = year(visita.data)
			and paziente.sesso = 'F'
	)	as d1
    left outer join
    (
		select *
		from paziente
			inner join visita
			on paziente.codfiscale = visita.paziente
		where year(paziente.datanascita + interval 40 year) = year(visita.data)
			and paziente.sesso = 'F'
	)	as d2
    on d1.paziente = d2.paziente 
    and d1.medico <> d2.medico 
where d2.medico is null;

Indicare l’età media dei pazienti mai visitati da ortopedici
select avg(year(current_date) - year(paziente.datanascita)) as etamedia
from (
	visita
    inner join medico
    on visita.medico = medico.matricola
    )
    right outer join
    paziente
    on medico.specializzazione = 'ortopedia'
where visita.medico is null;

Indicare nome e cognome dei pazienti che sono stati visitati non meno di due volte dalla dottoressa Gialli Rita
select distinct paziente.nome, paziente.cognome
from paziente
	inner join visita v1
    on paziente.codfiscale = v1.paziente
    inner join visita v2
    using (medico, paziente)
    inner join medico 
    on v1.medico = medico.matricola
where medico.nome = 'rita'
	and medico.cognome = 'gialli'
    and v1.data <> v2.data;

Indicare il reddito medio dei pazienti che sono stati visitati solo da medici con parcella superiore a 100 euro, negli ultimi sei mesi

Restituire valore medio e deviazione standard delle parcelle medie dei medici delle varie specializzazioni
select avg(parcellamedia) as parcellamedia, stddev(parcellamedia) as deviazionestandard
from (
	select avg(parcella) as parcellamedia
	from medico
	group by specializzazione
	) as d;

Per ogni specializzazione medica, indicarne il nome, la parcella minima e il cognome del medico a cui appartiene
select medico.specializzazione, medico.parcella as parcellaminima, medico.cognome
from medico
	natural join (
		select specializzazione, min(parcella) as parcellaminima
		from medico
		group by specializzazione
		) as d
where d.parcellaminima = medico.parcella;

indicare le specializzazioni della clinica con più di due medici
SELECT Specializzazione 
FROM Medico 
GROUP BY Specializzazione 
HAVING COUNT(*) > 2;

indicare le specializzazioni con la più alta parcella media
SELECT M.Specializzazione 
FROM Medico M 
GROUP BY M.Specializzazione 
HAVING AVG(M.Parcella) = ( 
	SELECT MAX(D.MediaParcelle) 
	FROM ( 
		SELECT M2.Specializzazione, AVG(M2.Parcella) AS MediaParcelle 
		FROM Medico M2 
		GROUP BY M2.Specializzazione 
	) AS D 
);

indicare le specializzazioni con più di due medici a Pisa
select specializzazione
from medico
where citta = 'pisa'
group by specializzazione
having count(*) > 2;

indicare il numero di pazienti di siena, mai visitati da ortopedici
WITH pazientivisitati AS
	(
	select
	from paziente
		inner join
		visita
		on paziente.codfiscale = visita.paziente
	where paziente.citta = 'siena'
	)
select count(*)
from pazientivisitati
	left outer join
	medico
	on pazinetivisitati.medico = medico.matricola
	and medico.specializzazione = 'ortopedia'
where medico.citta is null;

considerata ogni specializzazione, indicarne il nome e l´incasso degli ultimi due anni
select medico.specializzazione, sum(medico.parcella) as incasso
from visita
	inner join
	medico
	on visita.medico = medico.matricola
where visita.data + interval 2 year > current_date
	and visita.mutuata is false
group by medico.specializzazione;

indicare le specializzazioni aventi medici tutti della stessa città
select specializzazione
from medico
group by specializzazione
having count(distinct citta) = 1;

indicare le specializzazioni aventi almeno due medici della stessa città
select specializzazione
from medico
group by specializzazione, città
having count(*) > 1;

indicare codfiscale, nome, cognome ed età del paziente più anziano della clinica, e il numero di volte in cui è stato visitato da ogni medico
with datapiuvecchia as
(
	select min(data)
	from paziente
)
select paziente.codfiscale, paziente.nome, paziente.cognome, year(current_date)-year(paziente.datanascita), sum(visita.data)
from paziente
	inner join
	visita
	on visita.paziente = paziente.codfiscale
	inner join
	medico
	on visita.medico = medico.matricola
		and paziente.datanascita = datapiuvecchia
group by

Indicare la matricola dei medici che hanno effettuato più del 20% delle visite annue della loro specializzazione in almeno due anni fra il 2010 e il 2020.
with vispec as (
select medico.specializzazione, year(visita.data) as anno, count(data) as visite
from medico
	inner join visita
    on medico.matricola = visita.medico
    and year(visita.data) >= 2010
	and year(visita.data) <= 2020
group by medico.specializzazione, year(visita.data)
),
vimed as (
select medico.matricola, medico.specializzazione, year(visita.data) as anno, count(data) as visite
from medico
	inner join visita
    on medico.matricola = visita.medico
    and year(visita.data) >= 2010
	and year(visita.data) <= 2020
group by medico.matricola, year(visita.data)
)
select vimed.matricola
from vispec
	cross join vimed
    on vispec.specializzazione = vimed.specializzazione
		and vispec.anno = vimed.anno
        and vimed.visite*5 > vispec.visite
group by vimed.matricola
	having count(*) > 1;

Fra tutte le città da cui provengono più di tre pazienti con reddito superiore a 1000 Euro, indicare quelle da cui provengono almeno due pazienti che sono stati visitati più di una volta al mese, nel corso degli ultimi 10 anni.
with citta as (
select citta
from paziente
where reddito > 1000
group by citta
having count(codfiscale) > 3
),
pazienti as (
select paziente.codfiscale, paziente.citta
from visita
	inner join paziente
    on visita.paziente = paziente.codfiscale
where year(visita.data + interval 10 year) > year(current_date)
group by paziente.codfiscale, month(visita.data), year(visita.data)
having count(visita.data) > 1
)
select pazienti.citta
from citta
	cross join pazienti
    on citta.citta = pazienti.citta
group by pazienti.citta
having count(pazienti.codfiscale) > 1;

Indicare nome, cognome e specializzazione dei medici che hanno effettuato visite eccetto che il giorno 1° Marzo 2013
SELECT M.Nome, M.Cognome, M.Specializzazione 
FROM Medico M 
WHERE M.Matricola IN ( 
	SELECT V.Medico 
	FROM Visita V 
	) 
AND M.Matricola NOT IN ( 
	SELECT V.Medico 
	FROM Visita V 
	WHERE V.Data = ’2013-03-01’ 
	);

Indicare il numero degli otorini aventi parcella più alta della media delle parcelle dei medici della loro specializzazione.
SELECT COUNT(*) 
FROM Medico M1 
WHERE M1.Specializzazione = ‘Otorinolaringoiatria’ 
	AND M1.Parcella > ( 
		SELECT AVG(M2.Parcella) 
		FROM Medico M2 
		WHERE M2.Specializzazione = ‘Otorinolaringoiatria’ 
		);

Indicare nome e cognome dei pazienti che non sono mai stati visitati dal medico avente la parcella più alta fra tutti i medici della clinica
select paziente.nome, paziente.cognome
from paziente
where paziente.codfiscale not in (
	select visita.paziente
	from visita
	where visita.medico in (
		select matricola
		from medico	
		where parcella = (
			select max(parcella) as parcellamax
			from medico
		)
	)
) 

Indicare matricola e parcella dei medici che hanno visitato per la prima volta almeno un paziente nel mese di Ottobre 2013
SELECT DISTINCT V1.Medico 
FROM Visita V1 
WHERE YEAR(V1.Data) = 2013 
	AND MONTH(V1.Data) = 10 
	AND V1.Paziente NOT IN ( 
		SELECT V2.Paziente 
		FROM Visita V2 
		WHERE V2.Medico = V1.Medico 
			AND V2.Data < V1.Data 
		)

Considerato ciascun paziente di sesso maschile, indicarne il nome e il numero di visite effettuate
SELECT P.CodiceFiscale,( 
		SELECT COUNT(*) 
		FROM Visita V 
		WHERE V.Paziente = P.CodFiscale
		) AS TotaleVisite
FROM Paziente P 
WHERE P.Sesso = ‘M’

Una visita di controllo è una visita in cui un medico visita un paziente già visitato precedentemente almeno una volta. Indicare medico, paziente e data delle visite di controllo del mese di Gennaio 2016
select v1.medico, v1.paziente, v1.data
from visita v1
where month(v1.data) = 1
	and year(v1.data) = 2016
    and exists (
		select *
        from visita v2
        where v2.data < v1.data
			and v2.paziente = v1.paziente
            and v2.medico = v1.medico
            )

Indicare cognome e nome dei pazienti visitati almeno una volta da tutti i cardiologi di Pisa nel primo semestre del 2015.

Selezionare cognome e specializzazione dei medici la cui parcella è superiore alla media delle parcelle della loro specializzazione e che, nell´anno 2011, hanno visitato almeno un paziente che non avevano mai visitato prima

scrivere una query che restitusicsa nome e cognome del medico che , al 31/12/2014, aveva visitato un numero di pazienti superiore a quelli visitati da ciascun medico delal sua stessa specializzazione

scrivere una query che restituisca il codice fiscale dei pazienti che sono stati visitati sempre dal medico avente la parcella piú alta, in tutte le specializzazioni. Se anche per una sola specializzazione, non vi è un medico avente la parcella più alta, la query non deve restituire alcun risultato.

Scrivere una stored procedure che stampi la parcella media di una specializzazione specificata come parametro
DROP PROCEDURE IF EXISTS parcella_media_spec; 
DELIMITER $$ 
CREATE PROCEDURE parcella_media_spec(IN _specializzazione VARCHAR(100)) 
	BEGIN 
		SELECT AVG(M.Parcella) 
		FROM Medico M 
		WHERE M.Specializzazione = _specializzazione; 
	END $$ 
DELIMITER ; 

CALL parcella_media_spec(‘Ortopedia’);

Scrivere una stored procedure che restituisca il numero di pazienti visitati da medici di una data specializzazione, ricevuta come parametro 
DROP PROCEDURE IF EXISTS tot_pazienti_visitati_spec; 
DELIMITER $$ 
CREATE PROCEDURE tot_pazienti_visitati_spec( IN _specializzazione VARCHAR(100), OUT totale_pazienti_ INT) 
	BEGIN 
		SELECT COUNT(DISTINCT V.Paziente) INTO totale_pazienti_ 
		FROM Visita V 
			INNER JOIN Medico M 
			ON V.Medico = M.Matricola 
		WHERE M.Specializzazione = _specializzazione; 
	END $$ 
DELIMITER ; 

CALL tot_pazienti_visitati_spec(‘Neurologia’, @quantiPazienti); 

SELECT @quantiPazienti;

Scrivere una stored procedure che riceva come parametro un intero t e una specializzazione s e restituisca in uscita true se il numero di visite della specializzazione s nel mese in corso è superiore a t, false se è inferiore, e NULL se è uguale.
DROP PROCEDURE IF EXISTS numero_visite;
DELIMITER $$
CREATE PROCEDURE numero_visite(IN _minimovisite INT, IN _specializzazione VARCHAR, OUT maggiore BOOL)
	BEGIN
		DECLARE visite_mese_attuali INT DEFAULT 0;
		SET visite_mese_attuali = (
		SELECT COUNT(*)
		FROM visita
			inner join medico
			on visita.medico = medico.matricola
		WHERE medico.specializzazione = _specializzazione
		)
		IF visite_mese_attuali > _minimovisite
			SET maggiore = TRUE;
		ELSE
			SET maggiore = FALSE;
		END IF;
	END $$
DELIMITER;

CALL numero_visite(10, 'Otorinolaringoiatria',@controllo);

Scrivere una stored procedure che restituisca la data in cui un paziente, il cui codice fiscale è passato come parametro, è stato visitato per la prima volta, e il nome e cognome del medico che lo ha visitato in tale circostanza. In caso di più medici, per semplicità, selezionarne uno.
DROP PROCEDURE IF EXISTS prima_data_paziente;
DELIMITER $$
CREATE PROCEDURE prima_data_paziente(IN _codicefiscale VARCHAR, OUT _nomemedico VARCHAR, OUT _cognomemedico VARCHAR, OUT _datavisita DATE)
	BEGIN
		SELECT MIN(visita.data) INTO dataPrimaVisita
		FROM visita
		WHERE visita.paziente = _codicefiscale;
		
		SELECT medico.nome, medico.cognome INTO _nomemedico, _cognomemedico
		FROM Visita
			INNER JOIN Medico
			ON ..
		WHERE visita.data = dataPrimaVisita
			and visita.paziente = _codicefiscale
		LIMIT 1;
	END $$
DELIMITER;
```
![[Pasted image 20240909094826.png]]
![[Pasted image 20240909094840.png]]
![[Pasted image 20240909094857.png]]
