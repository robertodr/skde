# En kort introduksjon til LaTeX for SKDE

## En _enkel_ start

```latex
\documentclass[a4paper, norsk]{article}

\usepackage[utf8]{inputenc}
\usepackage[norsk]{babel}
\usepackage{parskip}

\begin{document}

\section{Dette er en overskrift}

En introduksjon til hvordan man skriver i \LaTeX.

\subsection{En underoverskrift}

Enkelt og greit.

\section*{Dette er en overskrift uten teller}

Litt mer tekst med æ, ø og å.

\end{document}
```  

- Et LaTeX-dokument starter alltid med `documentclass`. Her spesifiserer man hva slags dokument man skal skrive (article/report/book) og gir noen instillinger (at dokumentet er på norsk og at det er A4). 
- Man legger så inn noen `pakker` man vil bruke. Her har jeg brukt pakken `inputenc` med valget `utf8` for å kunne skrive æ, ø og å. Jeg bruker i tillegg pakken `babel` med valg `norsk`, for å bryte ord riktig ved tvunget linjeskift. Til slutt bruker jeg pakken `parskip` for å få rom mellom avsnitt.
- Mellom `\begin{document}` og `\end{document}` skriver man inn selve teksten.
- Overskrifter og underoverskrifter skrives i `\section{}` og `\subsection{}`.


