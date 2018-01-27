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

Een "Hello World!" Latex document `tex-bestanden\minimale-opzet.tex` ziet er als volgt uit.  

	\documentclass[a4paper]{book}
	
	\begin{document}
	Hello World!
	\end{document}

Opdrachten worden vooraf gegaan door `\`. Opdracht `\documentclass[a4paper]{book}` is een minimale configuratie voor Latex.  
Elk document begint met `\begin{document}` en eindigt met `\end{document}`.
Tussen begin en end kan de **inhoud** van het boek geschreven worden.  


	

