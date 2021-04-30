---
title: Activering publiek en profiel
description: Zorg voor activering van het publiek en profilering van centrale klantervaringen met Real-time ​ van klantgegevens.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: 9e0954334e8b8a8c5bf52651611e7afa165f6d21
workflow-type: tm+mt
source-wordcount: '1249'
ht-degree: 0%

---


# Activering publiek en profiel

Activering van publiek en profiel is de sleutel tot succes in een wereld van gegevensgestuurde marketing. Veel merken richten zich echter nog steeds op activering via het kanaal, wat vaak leidt tot inconsistente bereikbaarheid en personalisatie.

Met een kanaal-eerste benadering, handelt elk kanaal als silo waarin de verpersoonlijkingsinspanningen slechts de klanten richten die met het merk op dat kanaal interactie aangaan. Deze benadering weerspiegelt niet de realiteit dat klanten op verschillende aanraakpunten met merken communiceren. Activering van publiek en profiel maakt het voor merken mogelijk om klanteninteracties via meerdere kanalen te verbinden, zodat zij een gecentraliseerd profiel en publiek leveren dat op alle kanalen kan worden geactiveerd.

| Blauwdruk | Beschrijving | Experience Cloud-toepassingen |
|---|---|---|
| **[Anoniem Audience Activation](anonymous.md)** | <ul><li>Doelpubliek via internet en reclamekanalen voor anonieme en gedragsgegevens van klanten.</li><li>Integreren met publieksgegevens van derden voor een betere personalisatie.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Online/offline Audience Activation](online-offline.md)** | <ul><li>Activeer naar bekende, op profielen gebaseerde bestemmingen, zoals e-mailproviders, sociale netwerken en reclamebestemmingen. </li><li>Gebruik offlinekenmerken en -gebeurtenissen, zoals offlinebestellingen, transacties, CRM of loyaliteitsgegevens, samen met onlinegedrag voor het online aanwijzen en personaliseren.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-time Platform voor klantgegevens]</li><li>Adobe Audience Manager (optioneel)</li></ul> |
| **[Activering van publiek en profiel naar Enterprise-doelen](enterprise-destinations.md)** | <ul><li>Replicatie en update van profiel- en publiekswijzigingen naar bedrijfsgegevensopslagsystemen voor activering en rapportage van gebruiksgevallen. </li></ul><ul><li>Een verkoop- of ondersteuningsactie aan de klant initiëren via een kennisgeving van een actie van de klant van het [!UICONTROL Real-time Platform van klantgegevens] aan bedrijfssystemen en toepassingen.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Real-time Platform voor klantgegevens]</li><li>Experience Platform activeren</li><li>Adobe Audience Manager (optioneel)</li></ul> |
| **[Hub voor klantactiviteiten](customer-activity.md)** | <ul><li>Verbeter de context van de consument aan agent-gesteunde interactie, zoals steun en verkoopervaringen. Gebruikend het profielraadpleging in Experience Platform, kunnen de agenten meer context over de consument, zoals recente aankopen, campagneinteractie, eigenschappen, publiekslidmaatschappen, en andere attributen en inzichten ontvangen die in het klantenprofiel in real time worden opgeslagen.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## Instructies voor doelgroep en activering van profiel

* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

### Guardrails voor segmentbeoordeling en -activering

| Segmentatietype | Frequentie | Doorvoer | Latentie (evaluatie van segmenten) | Latentie (segmentactivering) | Payload activeren |
|-|-|-|-|-|-|-|-
| Randsegmentatie | De segmentatie van de rand is momenteel in bèta en staat voor geldige real-time segmentatie toe om op het Netwerk van de Rand van het Experience Platform voor real-time, zelfde paginabesluit via Adobe Target en Adobe Journey Optimizer worden geëvalueerd. |  | ~100 milliseconden | Direct beschikbaar voor personalisatie in Adobe Target, voor profielopzoekingen in het Edge-profiel en voor activering via op cookies gebaseerde doelen. | Publiek Membership beschikbaar op de Rand voor profielraadplegingen en koekjesgebaseerde bestemmingen.<br>Adobe Target en Journey Optimizer hebben toegang tot publiek- en profielkenmerken.  |
| Streaming segmentering | Telkens wanneer een nieuwe het stromen gebeurtenis of een verslag in het Profiel van de Klant in real time wordt opgenomen en de segmentdefinitie een geldig het stromen segment is. <br>Zie de  [segmentatiedocumentatie ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html) voor richtlijnen over streamingsegmentcriteria | Tot 1500 gebeurtenissen per seconde.  | ~ p95 &lt; 5 minuten | Streaming doelen: Het lidmaatschap van het streaming publiek wordt binnen ongeveer 10 minuten geactiveerd of wordt op basis van de vereisten van de bestemming op micro-batches geactiveerd.<br>Geplande doelen: Het stromen publiekslidmaatschap wordt geactiveerd in partij die op de geplande tijd van de bestemmingslevering wordt gebaseerd. | Streaming doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |
| Incrementele segmentatie | Eenmaal per uur voor nieuwe gegevens die in het Real-time profiel van de Klant sinds de laatste incrementele of batchsegmentevaluatie zijn opgenomen. |  |  | Streaming doelen: Het incrementele publiekslidmaatschap wordt binnen ongeveer 10 minuten geactiveerd of op micro-basis op basis van de vereisten van de bestemming.<br>Geplande doelen: De incrementele publiekslidmaatschappen worden geactiveerd in partij, die op de geplande tijd van de bestemmingslevering wordt gebaseerd. | Streaming doelen: Alleen wijzigingen in het lidmaatschap van het publiek en identiteitswaarden.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |
| Batchsegmentering | Eenmaal per dag op basis van een vooraf vastgesteld schema voor het systeem of handmatig gestart via de API. |  | Ongeveer één uur per baan voor maximaal 10 terabytes-profielopslaggrootte, 2 uur per baan voor 10 terabytes tot 100 terabytes-profielopslaggrootte. De prestaties van batchsegmenttaken zijn afhankelijk van numerieke profielen, de grootte van profielen en het aantal segmenten dat wordt geëvalueerd. | Streaming doelen: Het lidmaatschap van het batchpubliek wordt geactiveerd binnen ongeveer 10 jaar na voltooiing van de segmentatiebeoordeling of op micro-batches gebaseerd op de vereisten van de bestemming.<br>Geplande doelen: De het publiekslidmaatschappen van de partij worden geactiveerd gebaseerd op de geplande tijd van de bestemmingslevering. | Streaming doelen: Alleen wijzigingen in het lidmaatschap van het publiek en identiteitswaarden.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |

### Guardrails voor delen publiek tussen toepassingen

| Integratie van toepassingen voor het publiek | Frequentie | Productie/volume | Latentie (evaluatie van segmenten) | Latentie (segmentactivering) |
|-|-|-|-|-|-|-
| Platform voor realtime klantgegevens aan Audience Manager | Afhankelijk van het segmentatietype - zie bovenstaande tabel met segmentatiegeleidingen. | Afhankelijk van het segmentatietype - zie bovenstaande tabel met segmentatiegeleidingen. | Afhankelijk van het segmentatietype - zie bovenstaande tabel met segmentatiegeleidingen. | Binnen enkele minuten na voltooiing van de segmentbeoordeling.<br>De aanvankelijke synchronisatie van de publieksconfiguratie tussen het Platform en de Audience Manager van de Gegevens van de Klant in real time neemt ongeveer 4 uur.<br>Om het even welke publiekslidmaatschappen die tijdens de periode van 4 uur worden gerealiseerd zullen aan Audience Manager op de verdere partijsegmentatietaak als &quot;bestaand&quot;publieksenlidmaatschap worden geschreven. |
| Platform voor realtime klantgegevens aan Ad Cloud | Merk op dat het delen van publiek van het Platform van de Gegevens van de Klant in real time aan Adobe Advertising Cloud Audience Manager vereist. Dezelfde garanties die van toepassing zijn voor het delen van klantgegevens in realtime aan Audience Manager, zullen gelden voor de integratie van het publiek in het Platform voor realtime klantgegevens in Advertising Cloud. | - |-  | - |
| Adobe Analytics naar Real-time Customer Data Platform | Momenteel niet beschikbaar | Momenteel niet beschikbaar | Momenteel niet beschikbaar | Momenteel niet beschikbaar |
| Adobe Analytics naar Audience Manager |-  | Standaard kunnen maximaal 75 soorten publiek worden gedeeld voor elke Adobe Analytics-rapportsuite. Als een Audience Manager-licentie wordt gebruikt, is er geen limiet voor het aantal soorten publiek dat kan worden gedeeld tussen Adobe Analytics en Adobe Target of Adobe Audience Manager en Adobe Target. | - |-  |


### Grafische instructies voor het activeren van kenmerken en identiteiten

* [!UICONTROL Het ] platform van de Gegevens van de Klant in real time kan publiekslidmaatschappen evenals attributen en identiteitsveranderingen activeren die voor profielen voorkomen die leden van segmenten zijn die voor activering worden geselecteerd. Als u attributen of identiteiten wilt activeren, moet u een globaal segment definiëren dat alle profielen bevat waarnaar kenmerken en identiteitsupdates worden verzonden. Op dat punt, kunt u het segment en gewenste attributen selecteren om als deel van de bestemmingsconfiguratie te activeren.
* Merk op dat de partijbestemmingen activering van attribuut-slechts veranderingsgebeurtenissen niet steunen. Het volledige of stijgende publiekslidmaatschap kan samen met de geselecteerde attributen voor activering worden verzonden, maar u kunt geen attribuut-enige veranderingsgebeurtenissen via partijbestemmingen activeren.

Batchsegmenten activeren voor streamingdoelen

* Activering van batchsegmenten naar streaming doelen wordt ondersteund. De banen van het segment van de partij plaatsen berichten op de pijpleiding zodra de segmentbaan voor het stromen activering volledig is

Streaming segmenten activeren naar batchbestemmingen

* Activering van streaming segmenten naar batchbestemmingen wordt ondersteund. Het de segmentlidmaatschap van de de uitvoer van het de partijbestemmingsprogramma van de uitvoer op het programma van de partijbestemming wordt gebaseerd. Dit omvat zowel segmentlidmaatschap dat via het stromen en partijmethodes wordt bepaald.

Activering van ervaringsgebeurtenissen

* Het activeren van gebeurtenissen voor onbewerkte ervaring wordt niet ondersteund. Om tegen ervaringsgebeurtenissen te activeren, moet een segment met de noodzakelijke regels worden gecreeerd die de logica van de ervaringsgebeurtenis omvatten of uitsluiten. Dit leidt tot een segment dat tegen ervaringsgebeurtenissen wordt bepaald, en het segmentlidmaatschap kan als volmacht voor het activeren van ruwe ervaringsgebeurtenissen worden geactiveerd. Overweeg ook het gebruik van [!UICONTROL Server Side starten] om onbewerkte ervaringsgebeurtenissen te activeren die via SDK zijn verzameld.


## Verwante blogberichten

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
