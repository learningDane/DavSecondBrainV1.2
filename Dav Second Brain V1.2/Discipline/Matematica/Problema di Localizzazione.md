#uni 
Questo problema riguarda la localizzazione di servizi in maniera da riuscire a soddisfare vincoli quali distanza massima tra servizio e ogni cliente.
È un caso particolare del [[Problema di Copertura]].
# Modello
$a_{ij}=\begin{cases} 1 \quad distanza \ i,j \ ≤ target \\ 0 \quad altrimenti \end{cases}$ 
$j$: insieme delle richieste
$I$: insieme delle possibili postazioni
$x_i=\begin{cases} 1 \quad servizio \ posizionato \ in \ i \\ 0 \quad altrimenti \end{cases}$ 
- minimizzare il numero di ambulanze
- vincoli: tutti gli utenti devono essere  raggiunti in al più {target}.
$$\begin{cases}
\min \sum_i x_i \\
\sum_i a_{ij} \cdot x_i ≥ 1 \quad \forall j \\ 
x_i \in \{0,1\}
\end{cases}$$
