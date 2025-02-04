#self-taught 
simpletex.cn è un sito che con AI trasforma una foto di formule matematice nell'equivalente katex
matcha.io per disegnare funzioni
# Uso di Vim
usando vim il modo più veloce per compilare il documento è:
```vim
:!pdflatex nomedelfile
```
e poi cliccare enter, se adesso tocchi la finestra del pdf viewer si aggiornerà.
# Distribuzioni
- La distribuzione macTeX include TUTTI i pacchetti disponibili ma pesa tanto (non si trova bene in rete quanto ma penso attorno ai 5gb)
- basicTeX sono 180mb tipo, dovrai installare i pacchetti che ti servono dopo semmai:
```bash
brew install --cask basictex


#poi per controllare se è installato
which pdflatex

#se non trova niente aprire una nuova finestra di terminale e riprovare

#oppure
bash --login #equivale a una nuova finestra
which pdflatex


#ora aggiungere al path
export PATH="/Library/TeX/texbin/:$PATH"


#per installare pacchetti mancanti:
tlmgr install nomepachetto
```
# Sintassi
```Latex
\documentclass{article}
\author{Davide Squeri}
\title{Titolo}
\date{date}

\begin{document}
\maketitle

\section{Introduzione}

linea1
sempre linea1

this is normal text, \textbf{this is bold} , \textit{this is italic}
\emph{this is emphatic}
%quasi identico a italic, ma comunque usare aadeguatamente

linea2
\section{Altrasezione}
\subsection{sottosezione}

\end{document}
```