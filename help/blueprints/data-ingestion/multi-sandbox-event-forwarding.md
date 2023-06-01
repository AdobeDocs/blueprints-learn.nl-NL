---
title: Blauwdruk van gegevensverzameling doorsturen door meerdere sandboxgebeurtenissen
description: Leer hoe de gegevens die met het Web van het Experience Platform en Mobiele SDKs worden verzameld kunnen worden gevormd om één enkele gebeurtenis te verzamelen en aan veelvoudige Sandboxen door:sturen AEP.
solution: Data Collection
kt: 7202
source-git-commit: 3410adfd978de2458d257de96a7e484997f268db
workflow-type: tm+mt
source-wordcount: '835'
ht-degree: 0%

---


# Blauwdruk van gegevensverzameling doorsturen door meerdere sandboxgebeurtenissen

Deze blauwdruk toont hoe de gegevens die met het Web van het Experience Platform en Mobiele SDKs worden verzameld kunnen worden gevormd om één enkele gebeurtenis te verzamelen en aan veelvoudige Sandboxen door:sturen AEP. Deze blauwdruk is een specifiek gebruiksgeval voor de Verzameling van Gegevens Multi Sandbox die Gebeurtenis door:sturen gebruikt om dit doel te verwezenlijken.

Naast het repliceren van de gebeurtenis met de door:sturen van de Gebeurtenis eigenschappen, kunt u toevoegen aan, filtreren, of de originele verzamelde gegevens manipuleren die aan vereisten voor andere zandbakken voldoen.

Gebeurtenis doorsturen gebruikt een afzonderlijke eigenschap die de gegevenselementen, -regels en -extensies bevat die nodig zijn voor uw gegevensvereisten. Met een inkomende gebeurtenis, kan uw Gebeurtenis Door:sturen bezit de gegevens verzamelen en beheren zoals nodig alvorens door:sturen.

Voor uw doelsandbox is een HTTP Streaming End Point vereist dat is geconfigureerd en wordt gebruikt door de extensie Adobe Cloud Connector.

## Gebruik hoofdletters

* Globale gegevensrapportage - Bij het gebruik van meerdere sandboxen om besturingsomgevingen te isoleren en de noodzaak om gegevensverzameling te consolideren naar één sandbox voor rapportage tussen sandboxen. Het verpletteren van een Gebeurtenis van de Rand van de Ervaring door:sturen aan een rapporteringszandbak staat elke zandbak werkende milieu toe om gegevens te verzenden aangezien het in echt - tijd aan een rapportzandbak wordt verzameld
* De gegevensverzameling in verschillende sandboxen beheren op basis van verschillende gegevensregels voor elke sandbox-besturingsomgeving.

## Toepassingen

* Adobe Experience Platform-gegevensverzameling
* Gebeurtenis doorsturen
* AEP-extensie
* Extensie Cloud Connector

## Overwegingen

Met Gebeurtenis door:sturen als benadering van het verzenden van gegevens naar veelvoudige zandbakken, zijn er overwegingen die met uw oplossingsarchitectuur moeten worden in overweging genomen.

### Geen HIPAA-gegevens

Gebeurtenis doorsturen wordt niet als HIPAA Ready beschouwd en mag niet worden gebruikt in HIPAA-gebruiksgevallen waarin HIPAA-gegevens worden verzameld. De infrastructuur die wordt gebruikt voor het doorgeven van gebeurtenissen wordt echter als HIPAA-klaar beschouwd en is uitsluitend naar goeddunken van de klant. Terwijl uw eigenschap van de Tag voor het doorsturen van gebeurtenissen zich in het systeem voor het doorsturen van gebeurtenissen bevindt, wordt de volledige verzamelde gegevenslading voor verwerking verzonden naar het systeem voor het doorsturen van gebeurtenissen. Dit proces maakt het doorsturen van gebeurtenissen met betrekking tot HIPAA-gebruiksgevallen. Met de volledige lading die aan het Door:sturen van de Gebeurtenis systeem wordt verscheept, zou dit om het even welke waarden van HIPAA omvatten. Alhoewel de Gebeurtenis door:sturen regels die gegevens zullen filtreren alvorens naar zijn bestemming te verzenden, dat het gegeven HIPAA nog wordt verscheept aan een niet HIPAA klaar infrastructuur. Nochtans, worden de ladingsgegevens nooit opgeslagen en is eenvoudig een pas door.

### Verschillende gegevensstreams en streamingeindpunten

Aangezien de gegevens door de stromen van Gegevens van het Netwerk van de Rand van het Platform stromen, wanneer het gebruiken van Gebeurtenis die aan een andere zandbak door:sturen AEP, moet een HARD vereiste NOOIT het zelfde Datstream of het Streamen Eindpunt gebruiken zoals DataStream die de originele inzameling produceert. Dit kan schadelijk zijn voor het AEP-exemplaar en kan een DoS-situatie veroorzaken.

### Geschatte verkeersvolumes

Verkeersvolumes zijn vereist voor herziening met elk geval van gebruik. Dit is belangrijk, omdat grote volumes tot een vertragingssituatie kunnen leiden en klanten op de hoogte zullen worden gesteld als dit gebeurt.

## Architectuur

![Gebeurtenis met meerdere sandboxen doorsturen](assets/multi-sandbox-data-collection.png)

1. U moet gebeurtenisgegevens verzamelen en naar het Edge Network-Platform verzenden om de gebeurtenis te kunnen doorsturen. Klanten kunnen Adobe-tags gebruiken voor client-side of de Edge Network Server-API van Platform voor server-naar-server gegevensverzameling. De Platform Edge Network API kan een server-naar-server verzamelingsmogelijkheid bieden. Hiervoor is echter wel een ander programmeringsmodel nodig. Zie [Overzicht van Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en)

1. De verzamelde nuttige lasten worden verzonden van de implementatie van Codes naar het Netwerk van de Rand van het Platform naar de dienst die van de Gebeurtenis door:sturen en door zijn eigen Elementen, Regels en Acties van Gegevens verwerkt. U kunt meer lezen over de verschillen tussen [Tags en doorsturen van gebeurtenissen](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. Een gebeurtenis die Bezit door:sturen wordt ook vereist om verzamelde gegevens van de Gebeurtenis van het Netwerk van de Rand van het Platform te ontvangen. Of die gegevens van de Gebeurtenis naar het Netwerk van de Rand van het Platform door een opgestelde implementatie van Markeringen of een server-aan-server inzameling werd verzonden. Auteurs definiëren de gegevenselementen, regels en handelingen die worden gebruikt om de gebeurtenisgegevens te verrijken voordat deze naar de tweede sandbox worden doorgestuurd. U kunt het JavaScript-gegevenselement Aangepaste code gebruiken om uw gegevens te structureren voor het opnemen van sandboxen. In combinatie met AEP Data Prep-mogelijkheden hebt u verschillende opties om uw gegevensstructuur te beheren.

1. Momenteel is het gebruik van de extensie Adobe Cloud Connector vereist in de eigenschap Event Forwarding. Zodra het proces van Regels of verrijkt de gebeurtenisgegevens, wordt de Verbinding van de Wolk gebruikt binnen een Vraag van de Vetch die voor een POST wordt gevormd die de nuttige lading naar de tweede zandbak verzendt

1. Voor de tweede sandbox is een Streaming eindpunt voor gegevensinvoer vereist. U kunt ook de mogelijkheden van de Prep van Gegevens in AEP met hulp bij het opnemen en in kaart brengen van Gebeurtenis die lading door:sturen aan XDM overwegen. Raadpleeg de AEP-documentatie Maak een [HTTP API streamingverbinding met de gebruikersinterface](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=en)
