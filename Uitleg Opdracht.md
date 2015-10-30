### Oefenopdracht Research Data Management op GitHub

##### Beginnen

Om aan de slag te kunnen met deze opdracht doe je eerst het volgende:

Maak een github account aan op [GitHub](https://www.github.com).
[Installeer](https://help.github.com/articles/set-up-git/) vervolgens github en gitshell op je eigen computer 

Open github en gitshell

Op je eigen computer kun je nu een eigen repository maken met je eigen onderzoeksdata.
Lees op de github pagina de informatie [Creating a Repo](https://help.github.com/articles/create-a-repo/)

Op github.com log je in en op je eigen pagina creeer je een repository. 

```
1. linksboven op het plusje klikken
2. als naam geef je je projectnr en groepsnummer
3. geef een korte opschrijving.
4. maak een public repository aan.
5. kies "maak een readme".
6. klik create repository
```

In het overzicht van je nieuwe repositry staat nu een leeg bestandje *read me*.
klik hierop, kies edit en zet hierin je studentnummers en namen en wat je met deze data gaat doen.

In het programma github op je pc staat nu nog niks, omdat je je online versie van github nog niet hebt gesynchroniseerd met jouw computer. Vanuit github.com kopieer je uit het rechter menu naast je repository de URL van je repository.

In de gitshell navigeer je naar de github folder op jouw computer (waarschijnlijk C:\Users\Naam\Documents\GitHub )door in de gitshell command window te typen:

```
cd C:\Users\[JouwNaam]\Documents\GitHub
```

Daarna "kloon" je de repository naar je computer met de command clone:

```
git clone [URL van je repository]
```

Later kun je je lokale versie van je repository laten aanpassen aan de remote versie (op github.com) met het commando *git pull* (hierover later meer).

De nieuwe folder onder Documents/GitHub kun je nu gebruiken om je onderzoeksgegevens in te plaatsen en beheren.
Als je klaar bent met het verplaatsen en aanpassen van je data in deze folder kun je ze laten synchroniseren met je remote repository, dat doe je als volgt:

```
cd "[padnaarjouwrepository]" 
git add -A 
git commit -m "[typ hier een bericht dat kort aangeeft wat je hebt verandered]"
git push
```

Deze sequentie van commando's zorgt ervoor dat alle bestanden uit jouw lokale repository worden opgestuurd naar de remote repository, gematched op basis van bestandsnaam en alles wordt bijgevoegd en geupdate. Nu staan alle gegevens correct op je github.com pagina. 

Alle commando's die je hier geleerd hebt kun je ook zonder de gitshell command window laten uitvoeren door in het programma github op je computer repositories te creeren, klonen en aanpassen. Je lokale repository de gegevens uit je remote repository laten ophalen en bijwerkern doe je met het commando git pull, of door in het github programma rechtsbovenaan op sync te klikken.


##### Samenwerken met GitHub

Met github is het mogelijk gezamenlijk te werken aan een enkele versie van een bestand. Dit wordt bijvoorbeeld gedaan met scripts door programmeurs maar dit kan ook prima met onderzoeksdata. Bovenddien stelt GitHub je in staat om veranderingen bij te houden en te herstellen, om een "master" repository te maken waarvoor toestemming moet worden gegeven om aanpassingen door te voeren en misschien belangrijker: het dwingt je workflows en protocollen af te spreken met je collegas om de data uberhaupt te kunnen samenvoegen.
Enkele belangrijke afwegingen zijn bijvoorbeeld:
- wie heeft de leiding over de master dataset?
- wordt de dataset publiek of prive beheerd?
- welke aanpassingen mogen wel en niet gemaakt worden?
- en door wie?

Lees bijvoorbeeld deze online artikelen over "version control" met github:

Het is bijvoorbeeld vrij logisch dat als iedereen toegang heeft tot de master dataset, dingen snel onduidelijk en onoverzichtelijk kunnen worden. Bovendien zou een deelnemer per ongeluk gegevens van een ander weg kunnen gooien zoner daar erg in te hebben. Hier gebruiken we een techniek genaamd "forking", waarmee iedereen een kopie maakt van de master dataset, zowel een remote kopie als een lokale kopie. Deze lokale kopie passen we aan, hier voegen we bijvoorbeeld dingen aan toe, en daar schrijf je dan een message bij die aangeeft wat je gedaan hebt. De lokale, aangepaste kopie pushen we terug naar de remote kopie (of fork). Om deze veranderingen te laten doorvoeren in de master repository moeten we een "pull request" doen, wat aangeeft dat de beheerder van de master repository akkoord moet gaan met onze veranderingen.

###### Forking:

Om te oefenen browse je naar de volgende repository op GitHub:
[UvA Research data Management](https://github.com/UvARDM/FirstSteps)

Hierin staat een .txt bestandje "test". Lees wat erin staat.

Fork deze repository door rechtsboven op "fork" te klikken. Op jouw eigen GitHub.com pagina zie je nu deze repo verschijnen. kloon deze naar je lokale repo (kopieer de URL en geef in gitshell het commando git clone [URL] )

Open het nieuwe bestandje nu vanuit je file explorer op je eigen computer en voeg iets aan het textbestandje toe. Sla het weer op in de GitHub map (Documents/GitHub/TestData)

Stuur de aanpassingen als volgt terug naar je remote repo:

```
cd ..[padnaarjouwmapje]/GitHub/FirstSteps
git add -A 
git commit -m "[typ hier een bericht dat kort aangeeft wat je hebt veranderd]"
git push
```

Nu zijn de veranderingen alleen in jouw eigen fork aangepast. Om het in de master branch te laten opnemen stuur je ene pull request naar de beheerder van de master branch. de pull request houdt in dat je haar/hem vraagt jouw veranderingen te pullen

###### Pull requests:

Navigeer naar jouw fork op github.com. Klik op de groene knop links boven (compare, revire, pull request) Dit menu geeft je een overview van alles wat er precies is aangepast tussen jouw versie en de master branch. Ook geeft het aan of het gemerged kan worden of niet. Als er gemerged kan worden kun je een pull request sturen. Zet in de comments precies wat je hebt gedaan. Nu kan de beheerder bepalen of jouw pull request wordt doorgevoerd, of jouw vragen je pull request aan te passen omdat er iets nog niet in orde is.

Als de beheerder jouw pull request honoreert wordt jouw verhaaltje toegevoegd in de master branch. Als je wilt weten wat andere studenten gisteren hebben gedaan kun je jouw fork als volgt laten syncen met de master branch:

Ga naar de originele master branch en kopieer de URL

```
cd "[padnaarjouwmapje]\GitHub\FirstSteps"
git remote -v
git remote add upstream [jouw gekopieerde URL]
```

Om te controleren of dit heeft gewerkt:

```
git remote -v
```

Bij "origin" staat nu de URL van jouw fork
Bij "upstream" staat nu de URL van de originele master branch

Nu kun je syncen met de volgende commandos:

```
git fetch upstream
git checkout master
git merge upstream/master
```

Ook kun je syncen met de sync knop in het GitHub programma op je computer.

Wees erop voorbereid dat dit tot merging errors kan leiden als de indeling van jouw fork niet meer compatibel is met die van de master branch. Zodra alle uploads van alle groepjes zijn voltooid bekijken de docenten en assistenten de einddataset nog een keer. Daarna kan deze met git pull worden opgeslagen op je eigen computer.
