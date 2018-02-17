# Latex voor beginners

Latex is een hoge kwaliteit zet (typeset) systeem voor het opmaken van o.a. documentatie in PDF formaat.  
In Latex voor beginners wordt stapsgewijs uitgelegd hoe je Latex kunt gebruiken om een boek te schrijven.    

* Basis
* Opsommingen
* Referenties, Voetnoten, Hyperlinks
* Afbeeldingen
* Tabellen
* Appendix
* Index

## Basis

Voor het omzetten van `.tex` latex bestanden naar PDF wordt [Tex Live](https://www.tug.org/texlive/) gebruikt.  
Eclipse TeXlipse plugin 2.0.1. wordt gebruikt om in Eclipse te kunnen werken met .tex files.    

command-line kan gebruik worden gemaakt van 

	$ pdflatex <boek.tex>
	
om het `.tex` bestand om te zetten naar PDF.  

### Minimale opzet

Een "Hello World!" Latex document met een [minimale opzet](tex-bestanden/minimale-opzet.tex) ziet er als volgt uit  

	\documentclass[a4paper]{book}
	
	\begin{document}
	Hello World!
	\end{document}

Het document bestaat uit opdrachten (macros of commandos) en inhoud tekst.  
Opdrachten worden vooraf gegaan door `\`. Opdracht 

	\documentclass[a4paper]{book}

b.v., is een minimale configuratie voor Latex.  
Elk document begint met `\begin{document}` en eindigt met `\end{document}`.
Tussen begin en end kan de **inhoud** van het boek geschreven worden.

### Opdrachten

#### Packages

Latex heeft een basis set aan opdrachten. Andere opdrachten moeten worden geïmporteerd door gebruik te maken van

	\usepackage{package-naam}

De basis set opdrachten wordt bepaald door `documentclass` b.v. `book`.

#### Nieuwe opdrachten

Bij herhaald gebruik van samengestelde opdrachten kan gebruik gemaakt worden van 

	\newcommand{\opdracht-naam}{\samengetelde-opdracht}

om nieuwe opdrachten te maken.  
In de opdrachten kunnen ook parameters worden geïntroduceerd zoals

	\newcommand[aantal-input-parameters]{\opdracht-naam}{\samengetelde-opdracht{#1}}
	
bijvoorbeeld

	\newcommand[1]{\imp}{\textbf{\textit{#1}}}
	
Dit voorbeeld levert een nieuwe opdracht `\imp` op die tekst zowel vet als schuingedrukt weergeeft.  
De nieuwe opdracht is dan als volgt te gebruiken

	\imp{tekst}

De parameters worden aangeduid met `[1]` ingevuld op de plek van `{#1}`, `[2]` ... etc.

### Een `.tex` opbouwen uit meerdere `.tex` bestanden

Het `.tex` bestand kan de gehele inhoud van het boek bevatten.  
Als het boek groter wordt is gangbaar dat de hoofdstukken worden verdeeld over meerdere `.tex` bestanden.  
Invoegen van een tex bestand kan door gebruik te maken van

	\input{tex-bestand}

Het voorbeeld `boek.tex` bestand maakt gebruik van deze constructie

	\input{boek-bestanden/basis.tex}

In de generatie van het boek wordt `basis.tex` meegegenereerd naar het PDF document.  
Op deze wijze kan je hoofdstukken ook hergebruiken.  

N.B. de rest van de hoofstuk en de andere hoofdstukken uit voorbeeld `boek.tex` zijn op deze wijze geïmporteerd.  

### Tekst opmaak

Dik gedrukte tekst wordt verkregen met

	\textbf{tekst}
	
en schuingedrukte tekst met

	\textit{tekst}
	
onderstrepen kan met

	\underline{tekst}

Het `%` symbool wordt gebruikt voor commentaar. De rest van de regel wordt dan genegeerd bij het genereren van het PDF document.

	% Commentaar  

### Pagina marges

De marges van een pagina kunnen geconfigureerd worden met package `geometry` zoals

	\usepackage[top=2.5cm, left=2.5cm, bottom=2.5cm, right=2.5cm]{geometry}

waarbij in dit geval aan alle zijden een marge van 2,5 centimeter wordt ingesteld.

### Titelpagina

Gebruik `\title`, `\author`, `\date` en tenslotte `\maketitle` om een [titelpagina](tex-bestanden/titel-pagina.tex) aan te maken.  

	\title{Latex voor beginners}
	\author{Bas de Reus}
	\date{\today}
	\maketitle
	
### Inhoudsopgave

De inhoudsopgave wordt neergezet met

	\tableofcontents

### Hoofdstukken, Secties

Hoofdstukken en (sub)secties worden automatisch genummerd met b.v. `Chapter 1`.

Hoofdstuk worden aangegeven met

	\chapter{titel}

secties met

	\section{titel}

subsecties met

	\subsection{titel}

en sub-subsecties met

	\subsusection{title}

Normaal gesproken wordt een hoofdstuk neergezet volgens default taal Engels als `Chapter`.  
Automatische vertaling naar `Hoofdstuk` is mogelijk door gebruik te maken van package `babel` en optie `dutch`.  

	\usepackage[dutch]{babel}

### Dummy tekst

Met behulp van `blindtext` kun je een idee krijgen van hoe de opmaak uitpakt zonder eigen tekst in te voeren.

	\usepackage{blindtext}

en vervolgens waar nodig

	\blindtext

of 1 of meerdere paginas (aantal x) met

	\blindtext[x]

## Opsommingen

Opsommingen kunnen zowel `genummerd` als `ongenummerd` zijn  

### Genummererde opsommingen

Opsommingen zoals  

 1. Eerste item  
 2. Tweede item  

worden in Latex met package `\usepackage{enumerate}` geïntroduceerd als   

	\begin{enumerate}
	  \item Eerste item
	  \item Tweede item
	\end{enumerate}

Met

	\begin{enumerate}[a)]
	
loopt de 'nummering' als volgt  

 a) Eerste item  
 b) Tweede item  

Met

	\begin{enumerate}[~~~1)]

wordt de nummering voorafgegaan met 3 spaties en eindigt deze op een sluitend haakje.  

### Ongenummererde opsommingen

Met behulp van `itemize` kunnen ongenummerde (stippen) lijsten gemaakt worden

 * Eerste item
 * Tweede item

worden in Latex als volgt genoteerd  
 
	\begin{itemize}
	  \item Eerste item
	  \item Tweede item
	\end{itemize}

## Hyperlinks

Om hyperlinks te ondersteunen kan package `hyperref` gebruikt worden

	\usepackage[colorlinks=true, breaklinks]{hyperref}

Optie `colorlinks=true` toont links zonder 'box' om de links heen.  
`breaklines` kapt links met een lange naam netje af.  

### Hoofdstuk hyperlink

Hyperlinks naar een Hoofdstuk kunnen gemaakt worden door

	\chapter{Hyperlinks}
	\label{label-naam}
	
gebruik te maken van opdracht `\label` als locatie waar naar toe verwezen kan worden.  

	\ref{label-name}
	
verwijst dan naar het nummer van het hoofdstuk b.v. `2`.  
Door gebruik te maken van  
 
	\autoref{label-naam}

wordt de verwijzing naar `Chapter 2`. N.B. Nederlands wordt niet standaard ondersteund.  
Met behulp van

	\addto\extrasdutch{  
		\def\chapterautorefname{Hoofdstuk}  
	}

is het mogelijk de verwijzing de juiste vertaling naar `Hoofdstuk 2`. 
Op de [hyperref documentatie](https://ctan.org/pkg/hyperref) pagina staat meer uitleg over andere referentie opties.

Navigatie door de PDF heen aan de hand van geklikte links kan met ALT-LEFT en ALT-RIGHT.

### Sectie hyperlink

Dezelfde regels gelden voor sectie, waarbij de `\label` dan onder de sectie komt te staan.  

	\section{Hyperlinks}
	\label{sectie-label-naam}
	
Door `\def\sectionautorefname{Sectie}` toe te voegen aan `\addto\extrasdutch` worden secties ook vertaald naar b.v. `Sectie 2`.  

### Aangepaste hyperlink

Een aangepaste hyperlin wordt verkregen door b.v.  

	\hyperref[label-naam]{aangepaste-versie-naam \ref*{label-naam}}

met b.v. tot gevolg  

	aangepaste-versie-naam 2
	
waarbij `2` bijvoorbeeld een hoofdstuk nummer is.

### Voetnoten

Met `\footnote{voetnoot-tekst}` wordt een voetnoot geplaatst onderaan de pagina.  

### Internet links

Hyperlinks naar internet lokaties worden verkregen met

	\url{https://ctan.org}

of

	\href{https://ctan.org}{CTAN website}  
	
## Referenties

Een verwijzing naar een `\label{label-naam}` zonder hyperlink wordt verkregen met  

	\ref*{label-naam}
  
### Literatuur referenties

Literatuur verwijzingen kunnen worden opgezet met Bibtex.  
Inhoudelijk worden deze referenties in een extern bestand bewaard b.v. `library.bib`  
De koppeling vindt plaats door  

	\bibliographystyle{abbrvnat}
	\bibliography{tex-bestanden/library}

Om `abbrvnat` te kunnen gebruiken is package `natbib` nodig  

	\usepackage[round,authoryear]{natbib}

Daarmee is ook de `\citep` beschikbaar.  

Verwijzingen worden gedaan op `sleutel` zoals

	\cite{Martin2018}
	
zichtbaar als `Martin (2018)` of

	\citep{Martin2018}

zichtbaar als `(Martin, 2018)`
	
waarbij b.v.  

	@book{Martin2018,
		abstract = {Abstract text},
		author = {Martin, Robert C.},
		isbn = {97801344944166},
		pages = {404},
		publisher = {Pearson Education},
		title = {{Clean Architecture}},
		url = {https://url},
		year = {2018}
	}

Om de verwijzingen op de juiste manier in het PDF document te krijgen moet de volgens reeks command-line opdrachten gebruikt worden  

	pdflatex boek
	bibtex boek
	pdflatex boek
	pdflatex boek

### Kleurinstellingen referenties

De referenties hebben per default nogal felle kleuren groen, rood en blauw.  
Met package `xcolor` kunnen de kleuren gewijzigd worden  

	\usepackage{xcolor}
	\definecolor{c1}{rgb}{0,0,1} % blauw
	\definecolor{c2}{rgb}{0,0.3,0.9} % licht blauw
	\definecolor{c3}{rgb}{0.3,0,0.9} % paars
	\hypersetup{
	    linkcolor={c1}, % interne referenties
	    citecolor={c2}, % literatuur referenties
	    urlcolor={c3} % externe referenties
	}

## Afbeeldingen

Voor afbeeldingen wordt package `graphicx` gebruikt

	\usepackage{graphicx}  
	
Met opdracht `\includegraphics` kunnen afbeeldingen van het type PNG of JPEG in het PDF document worden geïmporteerd.  
Afbeelding `aarde.png` wordt b.v. neergezet met  

	\includegraphics[width=0.3\textwidth]{boek-bestanden/aarde}

Ook kan er een lijst met figuren worden toegevoegd met opdracht

	\listoffigures

Daarvoor is wel nodig dat de afbeelding is opgenomen tussen `\begin{figure}` en `\end{figure}`

	\begin{figure}[h!]
		\centering
		\includegraphics[width=0.3\textwidth]{boek-bestanden/aarde}
		\caption{aarde}		
	\end{figure}

en een bijschrift zoals  

	\caption{Aarde}

Opdracht `\centering` zorgt ervoor dat de afbeelding gecentreerd op de pagina komt te staan.  
Optie `[h!]` zorgt ervoor dat de afbeelding ter plekke wordt ingevoegd.  
Optie [width=0.3\textwidth] maakt de breedte van de afbeelding 0.3 maal de breedte van de text.  

Afbeelding referenties worden niet per default vertaald.  Vertaling kan worden toegevoegd door  

	\def\figureautorefname{Figuur}  

aan

	\addto\extrasdutch{    
	
toe te voegen.  

## Tabellen

Tabellen worden vergelijkbaar met afbeeldingen ingevoegd. 
De volgende representatie van een tabel defineert twee kolommen en twee rijen;  

	\begin{table}[h!]
	\begin{tabular}{lr}
	cel (1,1)
	& cel (1,2)
	\\
	cel (2,1)
	& cel (2,2)
	\end{tabular}
	\end{table}

Optie `[h!]` zorgt ervoor dat de tabel ter plekke wordt ingevoegd.  
Standaard wordt de tabel links uitgelijnd.  
`\begin{tabular}{lr}` definieert een tabel met twee kolommen waaran de tekst in de eerste kolom links uitgelijnd wordt en de tekst in de tweede kolom rechts.  
Kolommen worden gescheiden met `&`.  Rijen worden gescheiden met `\\`.  

Toevoegen van horizontale omlijning in de tabel kan met `\hline\`.  
Vertikale omlijning wordt in na `{tabular}` gedefinieerd in de vorm van een pipe `|`.  

	\begin{table}[h!]
	\label{tabel}
	\centering
	\begin{tabular}{|l|c|l|}
	\hline
	
	& kop 1
	& kop 2
	\\ \hline
	rij 1
	& cel (1,1)
	& cel (1,2)
	\\
	rij 2
	& cel (2,1)
	& cel (2,2)
	\\ \hline
	\end{tabular}
	\caption{Tabel Verwijzing}
	\end{table}
	
Met `\label{tabel}` kan naar de tabel verwezen worden met `\autoref{tabel}`.  
De vertaling is niet standaard geregeld en kan worden toegevoegd door  

	\def\tableautorefname{Tabel}  

aan 

	\addto\extrasdutch

toe te voegen.  

`\centering` plaatst de tabel in het midden op de pagina.  
`\caption{Tabel Verwijzing}` is het onderschrift van de tabel.  

Met opdracht `\listoftables` wordt een lijst met verwijzingen naar tabellen aan de PDF toegevoegd.  

## Bijlagen

In [appendix](boek-bestanden/appendix.tex) staat het gebruik van bijlagen uitgwerkt.  
Tussen `\begin{appendix}` en `\end{appendix}` kunnen bijlagen worden ingevoegd.  
Elk `\chapter{appendix-titel}` zorgt voor een nieuwe bijlage met oplopende letters `A, B, ...`  
Paragrafen `\section{sectie-titel}` worden genummerd voorafgegaan door de letter van de desbetreffende bijlage.  

Als voorbeeld zorgt

	\begin{appendix}
	\chapter{Eerste uitleg}
	\label{bijlage1}
	\section{Eerste onderdeel}
	\end{appendix}
	
voor een bijlage volgens
 
	Bijlage A
	Eerste uitleg
	
	A.1 Eerste onderdeel
	
Met `\label{bijlage1}` kan naar de bijlage verwezen worden met `\autoref{bijlage1}`.  
De vertaling is niet standaard geregeld en kan worden toegevoegd door  

	\def\appendixautorefname{Bijlage}  

aan 

	\addto\extrasdutch

toe te voegen.  


	