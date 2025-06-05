# QLR-Browser-Rodmapper

Oprettelse af flere rodmapper til QLR Browser.

Tilbage i 2015 gik en række kommuner sammen om at få firmaetSeptima til at udvikle "QLR Browser", et plugin til administration af QLR filer. 

QLR Browser indeholder en række ekstra faciliteter i forhold til den normale QGIS Datahåndtering, men har altid manglet en enkelt facilitet:
Allerede i starten af 2016 var der et ønske om at kunne tilknytte flere "rodmapper" til QLR Browser, så man f.eks. kunne have én "privat" 
mappe til sine egne qlr-filer - og én fælles mappe til organisationens fælles data. Den private mappe kan eks. placeres på brugerens lokale harddisk og fællesmappen 
kunne placeres på et fælles drev.
 
Jeg har nu siddet og nørdet lidt til "QGIS contributor meeting 2025" med brugen af QLR Browser - og fundet en mulighed for at implementere ønsket om flere rodmapper med den nuværende udgave af QLR Browser.

(Jeg bruger ikke selv QLR Browser længere og jeg ved faktisk ikke hvor mange som stadigvæk benytter plugin'et. Men løsningen er rimelig ligetil, 
så derfor har jeg skrevet denne vejledning. Jeg ved heller ikke, om nedenstående er "almindelig viden"; hvis det er, har I alle min tilladelse til at
fnyse hånligt over min uvidenhed) 

Løsningen baserer sig på brugen af Windows / Linux / IOS operativsystemets "symlink" facilitet. Symlink er en metode til at få filer og mapper placeret et sted på harddisken 
eller netværket til at se ud, som de er placeret et andet sted i filsystemet.

Et Windows eksempel: 

Vi ønsker at få mappen H:\common_gisdata" til at se ud, som om den er placeret i mappe "C:\gisdata" under navnet "Fælles filer". 
 - "H:\common_gisdata" er den mappe, som allerede indeholder organisationens fælles QLR filer - dvs. pt. opsat som QLR Browser "Base directory" 
 - "C:\gisdata" er den mappe, som man ønsker brugeren skal placere sine egne qlr filer i.
   

Man starter en DOS kommandolinje op med administrator-rettigheder.... 

(Og det er så her, at mange skal have fat i deres IT-administrator til at give dem denne rettighed. 
Det kun til selve oprettelsen af symlink'et hvor det er nødvendigt med denne rettighed. Den efterfølgende brug kræver ingen specielle rettigheder) 

- I start menuen skriver man CMD. Der vises et udvalg af mulige programmer.
- Man højreklikker på "Command Prompt". Der vises en undermenu ud for teksten.
- Man klikker på "Run as administrator" (eller hvad det nu hedder på dansk)

- ![alt text](https://github.com/AestasGIS/QLR-Browser-Rodmapper/blob/main/cmd.png "CMD startup")
- Der vises et et skærmbillede, hvori man kan skrive cmd kommandoer.
- I skærmbilledet skrives følgende kommando:
```
mklink /D "C:\gisdata\Fælles filer" "H:\common_gisdata" 
```

... Og så er vi stort set færdige. Hvis man åbner en stifinder og navigerer til mappe "C:\gisdata\" kan man se, at der nu er en ny undermappe "Fælles filer" i denne mappe.

I QGIS opsættes QLR Browser'ens base directory til "C:\gisdata". Herefter vil der i QLR browseren vises en række lokale qlr filer samt en ny mappe "Fælles filer". Hvis man navigerer ned i "Fælles filer" kan man se alle de fælles
 qlr-filer som i realiteten er placeret på "H:\common_gisdata". 

Tip !!

Man benytte share definitioner uden noget drev-bogstav, såsom  

```
mklink /D "C:\gisdata\Fælles filer" "\\my_server\my_share\common_gisdata" 
```

Man kan placere sin lokale qlr mappe sammen med resten af QGIS opsætningen: 

```
mkdir %APPDATA%\QGIS\QGIS3\gisdata
REM kopier brugerens egne qlr filer ned i denne mappe
mklink /D "%APPDATA%\QGIS\QGIS3\gisdata\Fælles filer" "\\my_server\my_share\common_gisdata" 
```
