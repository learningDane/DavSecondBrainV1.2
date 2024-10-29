#seminar
# Le Basi del Prompting
Un prompt è un set di istruzioni che forniamo ad un modello per ottenere una risata.
Modificando iterativamente il prompt riusciamo a raffinare il risultato.
Il ___prompt engineering___ è l'insieme di tutte le tecniche che utilizziamo per raffinare il prompt e il risultato.
I principi fondamentali:
- chiarezza e specificità
- contesto adeguato
- adattabilità al task
Linee guida per ottenere un prompt efficace:
- utilizzare comandi imperativi per riassumere ciò che si intende ottenere (scrivi, classifica ecc)
- sperimentare e raffinare iterativamente
- collocare le istruzioni all'inizio del prompt
- ___evitare di dire cosa NON fare, ovvero costruire il prompt con positività, questo incoraggia una maggiore specificità___
# Parametri degli LLM
- Temperatura: determinismo
- penalità di frequenza
- lunghezza della parola
- Top p: determinismo
##### Determinismo
Per controllare la casualità di una risposta ci riferiamo al determinismo del modello:
- Freddo: risultati pertinenti e meno creativi, sceglie sempre il token successivo più probabile.
- Caldo: il contrario, da utilizzare per task creative
##### Top_p/nucleos sampling
Simile alla temperatura.
Il modello seleziona un insieme di parole candidato finché la somma delle loro probabilità raggiunge una soglia. Dopo avere raccolto queste parole ne sceglie una a caso.
Top_p basso: freddo
Top_p alto: caldo
##### Penalità di frequenza
Applica una penalità al token successivo, più alta è la penalità di frequenza, minnore è la probabilità che una stessa parola compaia più volte.
##### Max_Length 
Gestisce il numero di token generato dal modello.
Dopo aver esaurito i token il modello si fermerà, anche se il risultato è incompleto.
La concisione del risultato diminuisce le allucinazioni AI.
##### Sequenze di Stop
Stringa che serve per controllare la lunghezza e la struttura della risposta del modello.
# Tecniche di Prompt
1. prompt zero-shot
2. prompt few-shot
3. prompt chain-of-thought
##### Prompt zero shot
Consente di restituire risultati senza un addestramento specifico o esempi precedenti.
##### Prompt Few Shot
Con questa tecnica formiamo un apprendimento in contesto, fornendo al modello dimostrazioni nel prompt per guidarlo.
##### Prompt Chain-of-Thought
Vengono utilizzate fasi di ragionamento intermedio per diminuire le allucinazioni. Combina il few-shot e lo accoppia con un esempio intermedio
### Perché?
Prompt errati possono portare ad usi impropri, rischi, contenuto errati o con bias. Possiamo adottare alcune pratiche di sicurezza per mitigare queste criticità.
# Prompt Injection
Queste sono tecniche che mirano a dirottare l'output del modello utilizzando prompt progettati ad hoc.
- ___Prompt Leaking___:
  Mira a far trapelare dettagli riguardo all'addestramento del modello.
- ___Jailbreaking___:
  mira ad aggirare le restrizioni etiche e di sicurezza imposte al modello, utilizza prompt ingannevoli che forzano il modello. 
- ___DAN___:
  Do Anything Now, forza un modello linguistico a ignorare le sue limitazioni.
# Tattiche di Difesa
Servono per evitare che il nostro modello venga ingannato e produca contenuti errati ecc.
- aggiungere una difesa all'istruzione
- citazioni e formattazione aggiuntiva
# Rischi dei LLM
- Bias e Pregiudizi
  Derivano dai dati di addestramento.
- fake news
- deep fake

