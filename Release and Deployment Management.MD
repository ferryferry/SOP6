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

Er gaat gebruik 
![gitWithEnvironments][gitWithEnvironments]


## <a id="scrum"></a>Scrum
[Hieronder tekst]

## <a id="testing"></a>Testing
[Hieronder tekst]

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
| - | --------- | ----------- |
| ✅ | Inleiding   | Ferry |
| 🚧 | Workflow   | Martijn |
| 🔴 | Git | Martijn |
| 🔴 | Scrum    | Ferry |
| 🔴 | Testing    | Martijn |
| 🔴 | Deployment    | n.v.t. |
| 🔴 | Samenvatting | n.v.t. |

Legenda:  
✅ = Done  
🚧 = Under Construction  
🔴 = Not Started
