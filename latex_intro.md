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

Dette er oppsettet som ble brukt i barnehelseatlas-rapporten

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


