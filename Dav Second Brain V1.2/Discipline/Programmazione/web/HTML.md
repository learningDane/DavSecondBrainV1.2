#uni 
HTML (___HyperText Markup Language___) is a _markup_ language. Markup is a way of specifing information about the content.
In the last decade a strong consensus has grown around the belief that HTML documents should only focus on structure and content of the document, and not how this document is visualized, which is left to [[CSS]]. 
This way of operating ensures: maintainability, speed, accessibility, better instructions for search engines -> SEO.
An HTML docuement is split into Head and Body, the head contains descriptive elements about the document, the body instead contains what should be displayed.
# Simplest HTML document
```HTML
<!DOCTYPE html>
<title>titolo</title>
<p>paragraph</p>
```
# Complete HTML document
```HTML
<meta charset = "utf-8">
<script src="js/html5shiv.js"></script> specifies the Javascript documents needed
<link rel="stylesheet" href="css/main.css"> specifies the style (CSS) document
```
# Elements
`<h></h>` heading
`<p><p/>` paragraph
`<div>` not displayed by the browser, does nothing
`<a>` anchor, has attribute `href="link/image"></a>`
links can be to external sites, resources within the current site, resources within the same page, particular locations on other page, instructions for user's email program, instructions to execute javascript function.




---
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
`style="Color: colore"` 
`style="border: il bordo che vuoi (oppure none)"` 
`background-color` 
`height="pixel di altezza"` 
`width="pixel di larghezza"` 
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
## Liste
`<ul>` se lista deve essere non-ordinata
`<ol>`se lista deve essere ordinata
`<dl>`se la lista deve avere descrizioni aggiuntive
```
<ul>
	<li> sfwf </li>
	<li> ecc
</ul>

<dl>
	<dt> blah blah </dt>
	<dd> descrizione </dd>
	<dt> ecc
</dl>
```
## Elementi in Blocco
Un elemento in blocco aggiunge spazi prima e dopo di se
`<div>` 
`<hr>` 
`<pre>` 
`<tutte le liste>` 
## Altri Elementi
`<div>` 
`<iframe src="il link"> //serve per includere una pagina` 
## Sintassi per i Simboli
`&il segno;` oppure con Unicode : `&#numero;` [tabella unicode](https://www.brescianet.com/appunti/vari/unicode.htm)
## I Form
```
<form>
	<label for="per cosa è l'imput"> La label </label>
	<br>
	<input type="tipo ti input (eg: text, number, checkbox)" name="il nome" id="l'id">
</form>
```
## Commenti
`<!-- commentooo -->` 