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
- Man legger så inn noen pakker man vil bruke. Her har jeg brukt pakken `inputenc` med valget `utf8` for å kunne skrive æ, ø og å. Jeg bruker i tillegg pakken `babel` med valg `norsk`, for å bryte ord riktig ved tvunget linjeskift. Til slutt bruker jeg pakken `parskip` for å få rom mellom avsnitt.
- Mellom `\begin{document}` og `\end{document}` skriver man inn selve teksten.
- Overskrifter og underoverskrifter skrives i `\section{}` og `\subsection{}`.

## En SKDE-rapport

Denne her: [rapport barnehelseatlas](http://www.helseatlas.no/getfile.php/SKDE%20INTER/Helseatlas/rapport_digitalt.pdf)

### Oppsett


```latex
\documentclass[norsk, 11pt, a4paper]{book}

\def \figurbredde {0.8\textwidth}
\def \captionbredde {1.0\textwidth}

\usepackage[norsk]{babel}
\usepackage[utf8x]{inputenc}
\usepackage[T1]{fontenc}

\usepackage{natbib}
\usepackage{bibtopic} % to referanselister

\usepackage{multicol}
\usepackage{graphicx}
\usepackage[labelfont=bf, font=scriptsize, width=\captionbredde, justification=justified,singlelinecheck=false]{caption} %instillinger for figurtekster

\usepackage{appendix}
\usepackage{xcolor}
\usepackage{verbatim}
\usepackage[bottom = 2.50cm]{geometry}
\usepackage{parskip}

% for tabeller
\usepackage{booktabs}
\usepackage{longtable}
\usepackage{rotating}
\usepackage{tabularx}

\usepackage{lipsum} % latin
\usepackage{textcomp} %copyright symbol
\usepackage{footmisc} %flere fotnoter

\usepackage{emptypage}
\usepackage{afterpage} % bedre clearpage?
\usepackage{pdfpages} % for å legge inn forside/bakside

\usepackage{fancyhdr}
\pagestyle{fancy}
\fancyhf{}
\fancyhead[lo]{\nouppercase{\rightmark}}
\fancyhead[re]{\nouppercase{\leftmark}}
\fancyhead[ro,le]{\thepage}
\setlength{\headheight}{14pt}

\definecolor{skde}{RGB}{0,80,158}
\definecolor{lysblaa}{rgb}{0.27,0.51,0.71}

\usepackage[colorlinks, citecolor=skde, linkcolor=skde, urlcolor=lysblaa]{hyperref} % brukes for nettutgaven

%\usepackage[colorlinks, citecolor=black, linkcolor=black, urlcolor=black]{hyperref} % brukes for printutgaven

% farge på overskrifter
\usepackage{sectsty}
\chapterfont{\color{skde}}  % sets colour of chapters
\sectionfont{\color{skde}}  % sets colour of sections
\subsectionfont{\color{skde}}  % sets colour of sections
\subsubsectionfont{\color{skde}}  % sets colour of sections

% for å få siste side til å være partall
\makeatletter
\def\cleartoleftpage{\clearpage\if@twoside \ifodd\c@page
\hbox{}\newpage\if@twocolumn\hbox{}\newpage\fi\fi\fi}
\makeatother

% Flere figurer per side etc
\renewcommand{\topfraction}{0.95}	% max fraction of floats at top
\renewcommand{\bottomfraction}{0.95}	% max fraction of floats at bottom
\renewcommand{\textfraction}{0.05}	% allow minimal text w. figs
\renewcommand{\floatpagefraction}{.8} %only pages with more than 80% of floats, will become pure float-only pages. The default is 0.6

% legge figurer på topp av float-only sider
\makeatletter
\setlength{\@fptop}{0pt}
\setlength{\@fpbot}{0pt plus 1fil}
\makeatother

```

### Side to

Lagt i egen fil kalt `side2.tex`

```
\newgeometry{bottom=2cm, right=2cm}

\null
\vfill


\begin{small}
{\color{skde}
\begin{tabularx}{0.46\paperwidth}{lX}
SKDE rapport    & Nr. 2/2015\\
Hovedforfatter & Atle Moen \\
Fungerende redaktør & Barthold Vonen \\
Ansvarlig redaktør & Olav Helge Førde\\
Medforfattere   & Bård Uleberg, Frank Olsen, Arnfinn Hykkerud Steindal, Petter Otterdal, Trygve Deraas, Trine Magnus og Lise Balteskard\\
Oppdragsgiver   & Helse- og omsorgsdepartementet og Helse Nord RHF\\
Gradering       & Åpen  \\
Dato            & September 2015\\
Versjon         & \today \\
\\
\multicolumn{2}{l}{Dokumentet skrevet i \LaTeX} \\
\multicolumn{2}{l}{Figurer produsert med SAS\textsuperscript{\textregistered}}\\
\multicolumn{2}{l}{Forsidefoto: Shutterstock} \\
\\
\multicolumn{2}{l}{\bf{ISBN:} \bf{978-82-93141-17-4}}\\
\\
\multicolumn{2}{l}{Alle rettigheter SKDE.}
\end{tabularx}
}
\end{small}

\restoregeometry

```

### Selve dokumentet

Bruker `\input{filnavn}` for å legge inn andre LaTeX-filer. "side2" er gitt [over](#side-to).

```latex
\begin{document}

\pagenumbering{arabic}
\pagestyle{empty}

\includepdf[pages={1}]{omslag.pdf}

\input{side2}

\input{forord}

\input{forord_blf}

\newgeometry{top=2.3cm}

\makeatletter
\@openrightfalse
\tableofcontents
\@openrighttrue
\makeatother
\restoregeometry


\pagestyle{fancy}

\input{sammendrag}

\input{introduksjon}

\input{helsetjenester}

\input{data_utvalg_metode}

\input{resultater}

\input{diskusjon}

\bibliographystyle{apalike2}

\begin{btSect}{referanser}

\chapter*{Referanser}
\addcontentsline{toc}{chapter}{Referanser}%\clearpage
\markboth{Referanser}{}
\btPrintCited

\chapter*{Øvrig litteratur}
\addcontentsline{toc}{chapter}{Øvrig litteratur}
\markboth{Øvrig litteratur}{}
\btPrintNotCited
\end{btSect}

\input{appendiks}

\cleartoleftpage

\includepdf[pages={2}]{omslag.pdf}

\end{document}
```

