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

```