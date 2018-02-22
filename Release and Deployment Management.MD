# <a id="begin"></a>Release and Deployment Management
Datum: 08-02-2018  
Auteurs: Ferry Jongmans (343410), Martijn Broekman (345814)

## Inleiding
Deze documentatie is geschreven om een inzicht te geven in het Release en Deployment Management van Kwetter.

### Casus
Twitter is een internetdienst ontstaan in 2006 waarbij gebruikers korte berichtjes publiceren. Via twitter.com geeft de hele wereld online antwoord op de vraag “What are you doing?”
>“Twitter is a free social networking and microblogging service that enables its users to send and read messages known as tweets. Tweets are text-based posts of up to 140 characters displayed on the author's profile page and delivered to the author's subscribers who are known as followers. Senders can restrict delivery to those in their circle of friends or, by default, allow open access.” -Uit Wikipedia, de vrije encyclopedie

Dit project is gebaseerd op Twitter en heet "Kwetter".

Voor verdere details over deze casus is [hier](./Docs/Casus.docx) meer informatie te vinden.

### Doel van deze documentatie
Het doel van dit document is om te omschrijven hoe er omgegaan wordt met Releases en Deployment. Eerst wordt er een algemene workflow omschreven die een globaal beeld schetst over de verschillende stappen in het ontwikkelproces.  

Vervolgens wordt op de onderdelen uit de workflow in de subkoppen Git, Scrum, Testing en Deployment ingezoomd waarin de specifieke details worden toegelicht. 

Ten slotte bevind zich op het einde van deze documentatie een samenvatting die in het kort alle stappen van development to deployment samenvat.

## Inhoudsopgave
+ [Workflow](#workflow)
+ [Git](#git)
+ [Scrum](#scrum)
+ [Testing](#testing)
+ [Deployment](#deployment)
+ [Samenvatting](#samenvatting)

## <a id="workflow"></a>Workflow
De workflow van Kwetter maakt gebruik van verschillende technieken. In [Figuur 1](#FiguurWorkflow) is te zien hoe een feature geimplementeerd wordt in Kwetter met deze technieken. In de volgende hoofdstukken is beschreven hoe deze technieken werken en waarom deze zo zijn geimplementeerd.

<a id="FiguurWorkflow"></a>![workflow][workflow]
Figuur 1: Workflow

## <a id="git"></a>Git
Het versiebeheer systeem Git wordt gebruikt voor het samenwerken tussen de verschillende ontwikkelaars, doormiddel van verschillende branches is het mogelijk voor verschillende programmeurs samen te werken aan één project zonder dat zij elkaar in de weg zitten.

![gitWithEnvironments][gitWithEnvironments]

Er gaat gebruik worden gemaakt van een 5 tal verschillende branches. Elke branch zal ook een bijbehoorde omgeving hebben. Deze omgevingen gaan in de volgende subhoofdstukken worden toegelicht.

### User story
Alle ontwikkelaars werken op een losse branch per user story. Als deze userstory is afgerond moet een andere ontwikkelaar deze code na kijken. Dit doet de ontwikkelaar doormiddel van een pullrequest. Ook moet de ontwikkelaar die het na kijkt de applicatie zelf testen, omdat niet alle fouten in één opzicht te zien zijn in de code.  
Daarom komt er specieke omgeving online voor de pullrequest, zodat de functionaliteiten getest kunnen worden. Nadat de pullrequest is goedgekeurt in is gemerged met de develop branch sluit deze omgeving automatisch af. 

### Develop
Dit is de hoofdbranch binnen het ontwikkelproces. Van deze branch worden de verschillende User story branches gemaakt. Het is de bedoeling dat op deze branch alleen code staat die is goedgekeurd code minimaal één andere ontwikkelaar.  
Drie dagen voor het einde van een sprint zal de code van de develop branch naar de test branch worden gepushed.

### Test
Deze branch is er, zodat er verder kan worden gewerkt op de develop branch zonder dat er nieuwe code komt die de validiteit van de testen kan beïnvloeden. Ook zal de code op deze branch automatisch naar de test omgeving worden gedeployed, zodat de testers de code zelf hoeven in te zien.  
Alle bugs die worden gevonden zullen op de code van deze branch worden opgelost en daarna naar de develop branch gepushed.

### Acceptance
Op deze branch komt de getesten code voor de oplevering van de sprint. Deze code wordt dan ook naar de verschillende acceptatie omgevingen van de klanten gepublished, zodat zijn de versie kunnen bekijken voor de oplevering van de daadwerlijke sprint.

### Master
Op deze branch komt de code als het is goedgekeurt door de product owner. De code op de branch komt ook automatisch in de release omgeving.

## <a id="scrum"></a>Scrum
Binnen Kwetter wordt gebruik gemaakt van Scrum. In de flowchart uit de workflow sectie is te zien aan de terminologie dat er gebruik gemaakt wordt van Scrum.

Binnen Scrum zijn een aantal persoonsrollen die verdeeld zijn. Iedere rol heeft zijn verantwoordelijkheden.

| Rol                  | Omschrijving           | Uitgevoerd door  |
| -------------        |:-------------| -----:|
| Product Owner 👨‍💼     | Toezicht op de ontwikkeling en hoofdrolspeler wat betreft stories die opgepakt gaan worden binnen ontwikkeling van de applicatie.  | Michael Franssen |
| Stakeholders 👨‍🔧👩‍🏭👩‍💼 | Personen uit de business waarvoor Kwetter een behoefte is. Zij dragen userstories aan naar de Product Owner.      |   Frank Coenen, Frenk  Reemer, Eric Slaats |
| Developers 👨‍💻👩‍💻     | De personen die de applicatie gaan ontwikkelen.      |    Ferry Jongmans, Martijn Broekman |

### Werkwijze
De productowner zorgt ervoor dat de userstories die hij en zijn stakeholders belangrijk vinden uitgewerkt worden door de developers. De developers werken in een sprint die 3 weken duurt. Deze keuze is gemaakt omdat het development team klein is. Indien de sprints korter duren zal er minder opgeleverd kunnen worden door de developers. Dit resulteert dan vervolgens in teveel overhead.

### Productownership
De productowner levert userstories op aan de developers. In overleg met hen wordt er een prioriteit gekoppeld aan de userstories wat vervolgens de volgorde van development bepaalt.

### Developers
Iedere dag vind er een stand-up plaats met de andere ontwikkelaars waarin de laatste ontwikkelingen worden besproken in een format wat er als volgt uitziet:
- Wat ben ik aan het doen?
- Wat ga ik doen?
- Loop ik tegen problemen aan, of ga ik tegen problemen aanlopen?

Op deze manier houd je de andere ontwikkelaars bewust van het ontwikkelproces en blijft het voor iedereen overzichtelijk.

### Backlog
De backlog is een aparte plaats waar alle userstories opgeslagen worden. Vanuit de backlog worden de userstories gekozen voor de huidige sprint. 

Deze userstories bevinden zich in verschillende stadia voordat zij geimplementeerd kunnen worden. Hieronder staan de statussen omschreven:  
1. New (Nieuw aangeleverde userstory aangeleverd door de productowner)
1. Identified (De userstory is uitgewerkt en begrijpbaar voor de developers)
1. Committed (De userstory is opgenomen in een sprint)
1. Closed (Userstory is niet gemaakt, productowner heeft de ontwikkeling van deze userstory stopgezet)
1. Done (Userstory is compleet uitgewerkt volgens de definition of done en de acceptatie criteria)

### Scrumboard
Het scrumboard is een kanban bord met hierop alle userstories die opgenomen zijn in de sprint. De userstories zijn gesorteerd op prioriteit waardoor de belangrijkste userstories zich bovenin het bord bevinden.

Het scrumboard kent diverse swimlanes:
1. Todo (Ontwikkeling nog niet gestart)
1. In progress (Ontwikkeling gestart)
1. Review (Nieuwe features staan in een pullrequest)
1. Done (Ontwikkeling voltooid en samengevoegd met de develop branch)

Op het scrumboard bevinden zich userstories. Elke userstory kan heeft een of meerdere taken die de developer zelf toevoegt.

Voorbeeld: Op het scrumboard staat een userstory: "Als gebruiker van de Kwetter applicatie wil ik een Kwet kunnen liken zodat degene die de Kwet geplaatst heeft diet dat ik het leuk vind". Onder deze userstory vallen diverse taken. Hieronder is een voorbeeld van een userstory met losse taken te zien.

| Userstory         | Todo      | In progress       | Review | Done |
| -------------     | --------- | -----             | ---    | --- |
| Als gebruiker van de Kwetter applicatie wil ik een Kwet kunnen liken zodat degene die de Kwet geplaatst heeft diet dat ik het leuk vind". Onder deze userstory   | Task: Service methode maken voor het aanroepen opslaan van een like |   |
| |  | Task: LikeComponent maken in Angular Frontend | |
| | Task: LikeComponent CSS maken | |

### Sprint oplevering
Als de sprint is afgelopen wordt de applicatie uitgebracht. Deze versie wordt gepresenteerd aan de productowner en bij voorkeur ook aan de stakeholders. Binnen deze oplevering betrek je de opdrachtgever bij het opgeleverde werk. Indien zij nog graag aanpassingen zien aan de opgeleverde versie kan dit eenvoudig aangepast worden. Zo'n aanpassing heet een Request For Change (RFC).

Na de sprintoplevering kiest de productowner weer opnieuw userstories uit die gebruikt gaan worden voor de nieuwe sprint.

### Uitzonderingen
Uiteraard zijn er ook uitzonderingen mogelijk. Indien er een userstory blocked is tijdens de sprint kan er dus niet aan gewerkt worden. De productowner dient te allen tijde op de hoogte te zijn van dit soort problemen.

Als een userstory nog niet helemaal is geimplementeerd is het verantwoord deze uit de sprint oplevering te laten. Voor de eindgebruiker is het beter om een feature niet te hebben dan een feature die voor de helft werkt.

## <a id="testing"></a>Testing
In dit hoofdstuk wordt toegelicht hoe de applicaties getest gaan worden. De testen zijn onder te verdelen in

## <a id="deployment"></a>Deployment
[Hieronder tekst]

## <a id="samenvatting"></a>Samenvatting
[Hieronder tekst]

---
[Terug naar boven](#begin)
<!-- Logos referenced in this markdown -->
[logo]: ./Images/icon.png "Logo Title Text 2"
[workflow]: ./Images/Workflow.png "Workflow"
[gitWithEnvironments]: ./Images/Git_Graph.png "Git Graph with environments"
<!-- 
Reference-style: 
![logo][logo] -->

## Werkverdeling:
| State | Onderdeel | Door |
| :-: | --------- | -----------: |
| ✅ | Inleiding   | Ferry |
| ✅ | Workflow   | Martijn |
| 🚧 | Git | Martijn |
| ✅ | Scrum    | Ferry |
| 🔴 | Testing    | Martijn |
| 🔴 | Deployment    | n.v.t. |
| 🔴 | Samenvatting | n.v.t. |

Legenda:  
✅ = Done  
🚧 = Under Construction  
🔴 = Not Started
