#self-produced
Raccolta Requisiti [[Progettazione Concettuale]] 
Devo poter memorizzare:
Cliente:
1. chiave (IDcliente - autoincrementale)
3. nome
4. cognome
5. data di nascita
6. indirizzo
7. contatto telefono
8. contatto email
9. note
Azienda cliente:
1. chiave (codfiscale/p.IVA)
2. ragione sociale
3. indirizzo sede legale
4. indirizzo sede operativa
5. settore di attività
6. sito web
7. contatto telefono
8. contatto email
9. note
Ingaggio:
1. chiave (IDingaggio - autoincrementale)
2. cliente
5. data
6. data consegna elaborato
7. luogo
8. tipo
10. servizio offerto
12. note
Lavoro:
1. lavorante
2. ingaggio
Pagamento:
1. chiave (IDpagamento - autoincrementale)
2. prezzo concordato
3. data emissione
4. data di pagamento
Lavorante:
1. chiave (codFiscale)
2. nome
3. cognome
4. dataNascita