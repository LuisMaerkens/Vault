



![[Commonground 5 lagen.png]]

Laag 1 en 2 lijken samen de _Data tier_. Ze zorgen voor de centrale opslag van data, autorisatie en logging. Het idee van **Haal Centraal** sluit goed aan bij het concept van **Data Lakes** om silovorming te voorkomen. Procesmatige validatie hoort hier inderdaad niet thuis, maar “gemaksgegevens” die stabiel in de tijd zijn, zouden hier wel kunnen worden ondergebracht – dat blijft uiteindelijk een ontwerpkeuze.

Laag 3 (NLX) is eigenlijk technische infrastructuur. Door deze hier expliciet te tonen wordt duidelijk dat data bij de bron kan worden opgehaald. Daarmee vormt laag 3 een verfijning van de datalaag. Vanuit de applicatie gezien vraag je uiteindelijk gewoon een dataset op – of dat nu via een API of een rechtstreekse SQL-query gebeurt. De meerwaarde van de API-aanpak ligt in het ontkoppelen en breder toegankelijk maken van de datalaag.

Laag 4 heet in het 5-lagenmodel ‘procesinrichting’. Dat blijft verwarrend. Als we het langs de lijn van het klassieke 3-tier model leggen, zou dit de _Logic Tier_ zijn: hier hoort de applicatielogica, zoals berekeningen (bijvoorbeeld een risicoscore), functies (zoals het genereren van een PDF) of beslistabellen. In het Common Ground-document _Realisatieprincipes_ staat echter dat het 5-lagenmodel niet bedoeld is om processen te modelleren, maar de informatievoorziening. Het modelleert het gegevenslandschap (laag 1+2) en het applicatielandschap (laag 4+5). Processen horen in een apart procesmodel, niet per se in dit 5-lagenmodel.

Laag 5, de interactielaag, sluit wél goed aan bij de _Presentation Tier_: de user interfaces en de ontsluiting van informatie naar eindgebruikers. Hier vinden we de javascript-frameworks, de UI-specialisten en de apps.

Het 5-lagenmodel fungeert deels als praatplaat – het helpt om draagvlak en overzicht te creëren, bijvoorbeeld bij de inrichting van de appstore. Tegelijkertijd is het belangrijk dat het fundament duurzaam en helder is. De huidige naamgeving in de proceslaag zorgt soms voor onbalans; een voorbeeld is de component _“Blauwe Knop proces-API Schulden ophalen bij Bronorganisatie”_.

Kortom: het 5-lagenmodel helpt om informatievoorziening en applicaties te ordenen, maar blijft lastig te rijmen met het 3-tier model. Vooral de benaming van de proceslaag vraagt verduidelijking.


### De Toekomstvisie: Common Ground

De gemeente wil af van deze afhankelijkheid en overstappen op het **Common Ground**-principe. Dit is een landelijke beweging binnen Nederlandse gemeenten. De kernideeën van Common Ground zijn:

- **Van systeem naar data:** De data (bijvoorbeeld informatie over een burger of een klacht) staat centraal, niet het systeem waarin die data is opgeslagen. De data wordt opgeslagen in een centrale, veilige omgeving.
    
- **Modulaire, losse applicaties:** In plaats van één groot zaaksysteem, worden er meerdere, kleinere applicaties gebruikt. Deze applicaties hebben elk hun eigen specifieke taak.
    
- **Geen vendor lock-in:** Omdat de data losgekoppeld is van de applicaties, kan een gemeente makkelijk van applicatie wisselen zonder dat alle data opnieuw overgezet hoeft te worden.
    

Tezza is hierin een van de nieuwe applicaties die de gemeente waarschijnlijk wil gaan gebruiken. Tezza is zo'n **Common Ground-applicatie** die speciaal is ontwikkeld voor zaakgericht werken, en die naadloos samenwerkt met andere, losse applicaties.





[[Generele informatie]]