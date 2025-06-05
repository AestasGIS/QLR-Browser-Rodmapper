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

Løsningen baserer ser på¨brugen af operativsystemets "symlinks" facilitet. Symlink er en metode til at få filer og mapper placeret et sted på harddisken eller på et netværks share til at se ud, som de er placeret et andet sted i filsystemet

Et eksempel: 

Vi ønsker at filen "vigtig_dokument.txt" som er placeret i mappe H:\fælles_data" til at se ud, som om den er placeret i mappe C:\mine_dokumenter under navnet "ikke_mit_eget_dokument.txt"
  



  


Jeg fosøgte   

