#uni 
Un'equazione lineare è un'equazione in cui compaiono solo somme di multipli di incognite. $$ax + by +\ ...\ + cz = k$$ Un sistema lineare è un sistema di equazioni lineari. $$\begin{cases} \ ax + by = c \\ \ dx + ey = f \\ \ ... \end{cases}$$
# Sistemi Lineari Omogenei
Un sistema si dice omogeneo se il termine noto è uguale a $0$ in tutte le equazioni. Un sistema lineare può:
- avere una soluzione unica
- non avere soluzione
- avere infinite soluzioni
# Mosse di Gauss
- aggiungere un multiplo di un'equzione a un'altra
- Moltiplicare un'equazione per uno scalare nullo
- Riordinare le equazioni
# Eliminazione Gaussiana, Algoritmo di Gauss
Applicare le 3 mosse di Gauss per semplificare un sistema di equazioni lineari.
### Variante di Jordan
Lavorando dal basso, dopo aver ridotto a scala possiamo mettere degli zeri sopra tutti i pivot
$$\begin{pmatrix} 1 & 0 & 2 & 3 \\ 2 &-1 & 1 & 1 \\ 1 &-1& 3 & 0\end{pmatrix} \to \begin{pmatrix} 1 & 0 & 2 & 3 \\ 0 & -1 & -3 & -5 \\ 0 & -1 & 1 & -3 \end{pmatrix} \to \begin{pmatrix} 1 & 0 & 2 & 3 \\ 0 & -1 & -3 &-5\\0 &0&4&2 \end{pmatrix} \to \begin{pmatrix} 1&0&2&3\\0&1&3&5\\0&0&2&1\end{pmatrix}$$ Adesso Jordan $$\begin{pmatrix} 1&0&0&2\\ 0&2&0&7\\ 0&0&2&1 \end{pmatrix}$$E ho risolto.