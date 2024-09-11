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

```
![[Pasted image 20240909094826.png]]
![[Pasted image 20240909094840.png]]
![[Pasted image 20240909094857.png]]
