# QLR-Browser-Rodmapper

Oprettelse af flere rodmapper til QLR Browser.

Tilbage i 2015 gik en række kommuner sammen om at få Septima til at udvikle "QLR Browser", et plugin til styring af QLR filer. 

QLR Browser indeholder en række ekstra faciliteter i forhold til den normale QGIS Datahåndtering, men har altid manglet en enkelt facilitet.
Allerede i starten af 2016 var der et ønske om at kunne tilknytte flere "rodmapper" til QLR Browser, så man f.eks. kunne have én "privat" 
mappe til sine egne qlr-filer - og én fælles mappe til organisationens fælles data. Den private mappe kan eks. placeres på brugerens lokale harddisk og fællesmappen 
kunne placeres på et fælles drev.
 
Jeg har nu siddet og nørdet lidt til QGIS contributor meeting 2025 med brugen af QLR Browser.. og fundet en mulighed for at implementere ønsket om flere rodmapper med den nuværende udgave af QLR Browser.

Jeg bruger ikke selv QLR Browser længere og jeg ved faktisk ikke hvor mange som stadigvæk benytter plugin'et. Men løsningen er rimelig ligetil, 
så derfor har jeg skrevet denne vejledning. (Jeg ved faktisk ikke, om nedenstående er "almindelig viden"; hvis det er, har I alle min tilladelse til at
fnyse hånligt over min uvidenhed) 

Løsningen baserer ser på brugen af operativsystemets "symlink" facilitet. Symlink er en metode til at få filer og mapper placeret et sted på harddisken 
eller netværks-share'en til at se ud, som de er placeret et andet sted i filsystemet.

Et eksempel: 

Vi ønsker at filen "vigtig_dokument.txt" som er placeret i mappe H:\fælles_data" til at se ud, som om den er placeret i mappe 
"C:\mine_dokumenter" under navnet "ikke_mit_eget_dokument.txt"

Man starter en DOS kommandolinje op med administrator-rettigheder.... 

(Og det er så her, at mange skal have fat i deres IT-administrator til at give dem denne rettighed. 
Det kun til selve oprettelsen af symlink'et hvor det er nødvendigt med denne rettighed. Den efterfølgende brug kræver ingen specielle rettigheder) 

- I start menuen skriver man CMD. Der vises et udvalg af mulige programmer.
- Man højreklikker på "Command Prompt". Der vises en undermenu ud for teksten.
- Man klikker på "Run as administrator" (eller hvad det nu hedder på dansk)

- ![alt text](https://github.com/AestasGIS/QLR-Browser-Rodmapper/blob/main/cmd.png "CMD startup")
- Der vises et et skærmbillede, hvori man kan skrive dos- kommando.
- Man skriver følgende kommando:
```
mklink ""C:\mine_dokumenter\ikke_mit_eget_dokument.txt" "H:\fælles_data\vigtig_dokument.txt" 
```



  



  


Jeg fosøgte   

