# Latex voor beginners

Latex is een hoge kwaliteit zet (typeset) systeem voor het opmaken van o.a. documentatie in PDF formaat.  
In Latex voor beginners wordt stapsgewijs uitgelegd hoe je Latex kunt gebruiken om een boek te schrijven.    

* Basis
* Hyperlinks
* Referenties
* Figuren
* Tabellen
* Opsommingen
* Wiskunde
* Appendix
* Footnotes
* Todos
* Index

## Basis

Voor het omzetten van .tex latex bestanden naar PDF wordt [Tex Live](https://www.tug.org/texlive/) gebruikt.  
Eclipse TeXlipse plugin 2.0.1. wordt gebruikt om in Eclipse te kunnen werken met .tex files.    

command-line kan gebruik worden gemaakt van 

	$ pdflatex <boek.tex>
	
om het .tex bestand om te zetten naar PDF.  

### Minimale opzet

Een "Hello World!" Latex document [minimale opzet](tex-bestanden/minimale-opzet.tex) ziet er als volgt uit.  

	\documentclass[a4paper]{book}
	
	\begin{document}
	Hello World!
	\end{document}

Opdrachten (macros of commandos) worden vooraf gegaan door `\`. Opdracht `\documentclass[a4paper]{book}` is een minimale configuratie voor Latex.  
Elk document begint met `\begin{document}` en eindigt met `\end{document}`.
Tussen begin en end kan de **inhoud** van het boek geschreven worden.


### Opdrachten

#### Packages

Latex heeft een basis verzameling aan opdrachten. Andere opdrachten moeten worden geïmporteerd door gebruik te maken van

	\usepackage{package-naam}

De basis verzameling opdrachten wordt bepaald door `documentclass` b.v. `book`.

#### Nieuwe opdrachten

Bij herhaald gebruik van samengestelde opdrachten kan gebruik gemaakt worden van 

	\newcommand{\opdracht-naam}{\samengetelde-opdracht}

ook kunnen parameters worden geïntroduceerd zoals

	\newcommand[aantal-input-parameters]{\opdracht-naam}{\samengetelde-opdracht{#1}}
	
bijvoorbeeld

	\newcommand[1]{\imp}{\textbf{\textit{#1}}}
	
levert een nieuwe opdracht `\imp` op die tekst zowel vet als schuingedrukt weergeeft te gebruiken als

	\imp{tekst}

De nummering van parameters loopt op als `#1, #2, ...`

### Tekst opmaak

Dik gedrukte tekst wordt verkregen met

	\textbf{tekst}
	
en schuingedrukte tekst met

	\textit{tekst}
	
onderstrepen kan met

	\underline{tekst}

Het `%` symbool wordt gebruikt voor commentaar. De rest van de regel wordt dan genegeerd bij het genereren van een PDF document.

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
	
