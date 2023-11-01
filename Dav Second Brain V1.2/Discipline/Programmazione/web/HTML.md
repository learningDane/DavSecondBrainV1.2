#self-taught 
HTML (___HyperText Markup Language___) è un linguaggio di _markup_ nato per la formattazione e impaginazione di documenti ipertestuali.
L'HTML è un linguaggio di pubblico dominio, la cui sintassi è stabilita dal [[World Wide Web Consortium]] (W3C).
# Codice
## Basi
`<!DOCTYPE html>` stabilisce il tipo di documento da formattare e la versione di HTML.
`<html> xxx </html>` indica l'inizio e la fine dell'HTML.
`<head> xxx </head>` contiene la metadata del documento, titolo della pagina, il tipo di encoding e link a risorse esterne.
1. `<title> </title>` il titolo della pagina.
2. `<link rel="icon" href="link dell'immagine">` icona del sito.
`<body> xxx </body>` questo elemento è una delle componenti fondamentali dell'HTML, il contenuto di questo elemento è tutto ciò che viene mostrato sulla pagina web.
`<hn> xxx </hn>` dove $n$ è l'indice di priorità è un heading.
`<p> xxx </p>` è un paragrafo non formattato.
`<pre> xxx </pre>` è invece un paragrafo preformattato.
## Formattazione
`<b> </b>` __bold__.
`<strong> </strong>` __bold__.
`<em> </em>` $\sim$ _italic_.
`<i> </i>` _italic_.
`<mark> </mark>` highlights text.
`<del> </del>` delete
`<ins> </ins>` underline
`<small> </small>` small
`<sub> </sub>` $aaa_{this is sub}$ 
`<sup> </sup>` $a^{lol}$ 
## Elementi a chiusura autonoma
`<br>` serve per andare a capo
`<hr>` una linea separatrice
## Attributi
`<p style="attributo; altro attributo"> </p>` 
`Color: colore` 
`background-color` 
## Link
Se non metti il `https://` (che rende il link assoluto), il browser lo prende come link relativo.
`<a href="il link"> blah blah </a>` apre il link nella stessa pagina.
`<a href="il link" target="_blank"> blah blah </a>` con questo attributo _target="_blank"_ apre il link in una nuova pagina.
`<a href="mailto:indirizzoemail"> send me an email </a>`
## Tabelle
```
<table>
	<tr> //tr sono le righe
		<th> </th>
		<th> ecc //th  sono le colonne (table-heading)
	</tr>
	
	<tr>
		<td> dsrfgerg </td> //table data
		<td> ecc
	</tr>
	
	<tr> ecc
</table>
```
# Liste
`<ul>` se lista deve essere non-ordinata
`<ol>`se lista deve essere ordinata
`<dl>`se la lista deve avere descrizioni aggiuntive
```
<ul>
	<li> sfwf </li>
	<li> ecc
</ul>
```
## Commenti
`<!-- commentooo -->`