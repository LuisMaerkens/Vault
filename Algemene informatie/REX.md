
### REX: Het kloppend hart van de processen

**REX** is het centrale zaaksysteem van de gemeente Leeuwarden. Het is de digitale hub waar alle "zaken" (zoals klachten van burgers, aanvragen of meldingen) binnenkomen en worden beheerd. Het systeem regelt de volledige workflow, van het begin tot het einde van een zaak.

---

### De samenwerking met andere teams

- **[[Algemene informatie/RPA]] (Robotic Process Automation):** De **RPA-robots** werken direct met REX. Ze halen taken op uit REX en voeren repetitieve handelingen uit in andere systemen (zoals het bijwerken van een SharePoint-site). Nadat de robot een taak heeft voltooid, stuurt hij de status van de zaak terug naar REX. Dit laat zien dat REX niet alleen een passieve database is, maar actief de werkvoorraad van de robots aanstuurt.
    
- **DWO (Data & Workflows):** Dit team gebruikt technieken zoals **Process Mining** om te analyseren hoe processen verlopen. Ze kunnen de logbestanden van REX onderzoeken om te zien hoe snel zaken worden afgehandeld, waar knelpunten zitten of waar afwijkingen van het standaardproces plaatsvinden. De data uit REX is dus essentieel voor het DWO-team om te kunnen bepalen hoe de workflows geoptimaliseerd kunnen worden.
    
- **[[Algemene informatie/IM]] (Informatiemanagement):** Het **IM-team** is strategisch verantwoordelijk voor de gehele informatievoorziening van de gemeente. REX valt onder hun verantwoordelijkheid. Het IM-team zorgt voor de kwaliteit van de data in REX en overziet de integratie met andere systemen. De nauwe samenwerking tussen de teams van IM, DWO en RPA is cruciaal voor het optimaal functioneren van REX en de bijbehorende processen.
    
---


1. **De Klant** vult een e-formulier in voor een klacht.
    
2. De klacht wordt als een bericht (geïllustreerd door de envelop) verstuurd naar de afdeling **Gemeente**.
    
3. Dit bericht komt binnen bij **REX**. REX is hier een data-opslag, een soort database of digitale inbox, die fungeert als een 'werkvoorraad'.
    
4. De **"KHV_0_Werkvoorraad robot"** haalt de taak (de "zaak") op uit deze REX werkvoorraad.
    
5. Nadat de robot de zaak heeft opgehaald en verwerkt, slaat hij deze op een **SharePoint site** op.
    
![[simple rex.png]]
### Wat betekent dit in de praktijk?

In de context van procesautomatisering, en met name **Robotic Process Automation ([[Algemene informatie/RPA]])**, is een werkvoorraad een essentiële component.

- **REX functioneert als de centrale wachtrij:** Het is de plek waar alle nieuwe taken (klachten in dit geval) binnenkomen en wachten om te worden opgepakt. Dit zorgt voor een georganiseerde, gecontroleerde stroom van werk.
    
- **De robot is de 'worker':** De robot is geprogrammeerd om continu de REX werkvoorraad te monitoren. Zodra er een nieuwe taak verschijnt, pakt de robot deze op en begint met de verwerking.
    
- **Decoupling:** Het gebruik van een werkvoorraad ontkoppelt het proces van het aanmaken van taken (de klant vult het formulier in) van het proces van het uitvoeren van de taken (de robot verwerkt de klacht). Dit maakt het proces robuuster en schaalbaarder. Stel je voor dat er plotseling honderden klachten tegelijk binnenkomen: de robot kan ze niet allemaal tegelijk verwerken, maar ze worden wel netjes in de REX-wachtrij gezet. De robot verwerkt ze dan één voor één, op volgorde van binnenkomst of op basis van prioriteit.
    



### Deel 1: Klacht indienen en opstarten van het robotproces 

1. **De klant** dient een klacht in via een e-formulier.
    
2. De ingediende klacht wordt als een bericht (envelop) verstuurd naar de afdeling "Gemeente".
    
3. Dit bericht komt binnen in een database of werkvoorraad met de naam **"REX"**. Zoals in het vorige antwoord uitgelegd, fungeert REX hier als de centrale wachtrij voor taken.
    
4. Een specifieke robot, genaamd **"KHV_0_Werkvoorraad robot"**, haalt de klacht (de 'zaak') op uit de REX-werkvoorraad.
    
5. De robot verwerkt de taak en slaat de zaak op in een **SharePoint site**. Dit markeert het begin van het dossier.
    

### Deel 2: 

1. **"KHV_1_robot"** pakt de zaak op en stuurt een bericht naar het **"Huurteam"**. Dit laat zien dat de robot een taak uitvoert die normaal door een mens zou worden gedaan: het informeren van de juiste afdeling.
    
2. Het huurteam ontvangt dit bericht en kan de klacht behandelen. Het proces heeft hier een beslispunt ("gateway"):
    
    - **Ja (voor huurteam?):** Als de klacht bedoeld is voor het huurteam, wordt deze op de SharePoint-site gezet. Er volgt een handmatige stap ("Zaak op SharePoint bijwerken"). Na de handmatige afhandeling wordt de status op de SharePoint-site bijgewerkt naar "Afgehandeld".
        
    - **Nee (voor huurteam?):** Als de klacht niet voor hen is, wordt de status op SharePoint gezet op "Doorgestuurd".
        
3. Tegelijkertijd werkt er een andere robot: **"KHV_2_robot"**. Deze robot scant de SharePoint-site om te controleren of de zaak is afgehandeld. Dit is een voorbeeld van een geautomatiseerde monitoringstap.
    
4. De robot komt bij een beslispunt:
    
    - **Ja (afgehandeld?):** Als de zaak op SharePoint is afgehandeld door het huurteam, is de robot-taak voltooid.
        
    - **Nee (afgehandeld?):** Als de zaak niet is afgehandeld, zet de robot de zaak door naar een nieuwe afdeling: "Medewerker Gebiedszaken".
        
5. De **medewerker gebiedszaken** behandelt de zaak en werkt vervolgens de REX-werkvoorraad bij. Dit laat zien dat er een terugkoppeling is naar het REX-systeem, vermoedelijk om de status van de klacht te updaten in de centrale werkvoorraad.
    


![[not simple rex.png]]