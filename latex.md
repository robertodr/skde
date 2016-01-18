# Hvordan installere LaTeX på SKDE-maskiner

Hvis det oppstår problemer med denne fremgangsmåten, gi gjerne beskjed til arnfinn.steindal@[skde.no|gmail.com|uit.no]

## Installere MikTeX

Dette er selve LaTeX.

- Last ned fra [denne siden](http://miktex.org/download)
- Installer programmet på ditt hjemmeområdet på c:
- Gå inn på START/Alle programmer/MikTeX 2.9/Maintenance/Settings
  - Sjekk at General-fanen ser omtrent slik ut:

![Alt text](figurer/miktex_general.png)
  - Gå inn på Roots-fanen og legg inn følgende mappe:

![Alt text](figurer/miktex_roots.png)
- Gå inn på `START/Alle programmer/MikTeX 2.9/Maintenance/Package Manager`
  - Gå så inn på `Repository/Change Package Repository` og trykk på `Connection Settings...`
 
![Alt text](figurer/miktex_repository1.png)
  - Her legger man inn en proxy med adresse `www-proxy.helsenord.no` og port nummer `8080`:

![Alt text](figurer/miktex_repository_proxy.png)


## Installere Texmaker 

Dette er programmet vi skal skrive LaTeX i.

- Last ned fra [denne siden](http://www.xm1math.net/texmaker/download.html)
- Installer programmet på ditt hjemmeområdet på c:

Man kan velge et annet skriveprogram hvis man vil, f.eks [TeXnicCenter](http://www.texniccenter.org).


