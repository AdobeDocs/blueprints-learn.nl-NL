---
title: Activering publiek en profiel
description: Zorg voor activering van het publiek en profilering van centrale klantervaringen met Real-time ​ van klantgegevens.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
translation-type: tm+mt
source-git-commit: b5d8160235fb510642701ba066434d8bd226b464
workflow-type: tm+mt
source-wordcount: '1201'
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

### Guardrail Diagram

<img src="assets/activation_guardrails.svg" alt="Guardrail-diagram voor de activering van blauwdrukken voor publiek en profiel" style="border:1px solid #4a4a4a" />



### Guardrails voor segmentbeoordeling en -activering

| Segmentatietype | Gevallen gebruiken | Frequentie | Doorvoer | Latentie (segmentevaluatie) | Latentie (segmentactivering) | Payload activeren |
|--------------------------|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Randsegmentatie | Web/mobiele personalisatie (zelfde pagina/Volgende pagina) | De segmentatie van de rand is momenteel in bèta en nog niet algemeen beschikbaar. | - | Ongeveer 100 milliseconden | Doel en Journey Optimizer:<ul><li>Beschikbaar onmiddellijk in het zelfde verpersoonlijkingsverzoek.</li></ul>Op cookie gebaseerde doelen:<ul><li>Beschikbaar voor beslissingen op de volgende pagina.</li></ul> | Edge Profile Lookups (Target en Journey Optimizer):<ul><li>Publiek lidmaatschap</li><li>Profielkenmerken</li></ul>Op cookie gebaseerde doelen:<ul><li>Publiek lidmaatschap</li></ul> |
| Streaming segmentering | Trigger-gebaseerde marketing (streaming) | Telkens wanneer een nieuwe het stromen gebeurtenis of een verslag in het klantenprofiel in real time wordt opgenomen en de segmentdefinitie is een geldig het stromen segment. <br>Zie de segmentatiedocumentatie voor begeleiding op het  [segmenteringsdocumentatie van de streaming segmenteringscriteria](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html) | Tot 1500 gebeurtenissen per seconde. | Ongeveer 5 minuten, p95 | Streaming doelen:<ul><li>Ongeveer 1 minuut aan Audience Manager en Doel</li><li>Ongeveer 10 minuten naar externe bestemmingen of microbatches afhankelijk van de bestemming.</li></ul>Geplande doelen:<ul><li>Geactiveerd aan externe bestemmingen in partij die op de geplande tijd van de bestemmingslevering wordt gebaseerd.</li></ul> | Streaming doelen: <ul><li>Wijzigingen in het lidmaatschap van de doelgroep</li><li>Identiteitswaarden</li><li>Profielkenmerken</li></ul>Geplande doelen:<ul><li>Wijzigingen in het lidmaatschap van de doelgroep</li><li>Identiteitswaarden</li><li>Profielkenmerken</li></ul> |
| Incrementele segmentatie | <li>Batchberichten<li>Doelgerichte campagnes en ervaringen | Eenmaal per uur voor nieuwe gegevens die in het klantprofiel in real time sinds de laatste incrementele of batchsegmentevaluatie zijn opgenomen. | Niet van toepassing | Afhankelijk van het aantal profielen, de grootte van profielen en het aantal segmenten dat wordt geëvalueerd. | Streaming doelen:<ul><li>Ongeveer 1 minuut aan Audience Manager en Doel</li><li>Ongeveer 10 minuten naar externe bestemmingen of microbatches afhankelijk van de bestemming.</li></ul>Geplande doelen:<ul><li>Geactiveerd aan externe bestemmingen in partij die op de geplande tijd van de bestemmingslevering wordt gebaseerd.</li></ul> | Streaming doelen: <ul><li>Wijzigingen in het lidmaatschap van de doelgroep</li><li>Identiteitswaarden</li></ul>Geplande doelen:<ul><li>Wijzigingen in het lidmaatschap van de doelgroep</li><li>Identiteitswaarden</li><li>Profielkenmerken</li></ul> |
| Batchsegmentatie | <ul><li>Batchberichten</li><li>Doelgerichte campagnes en ervaringen</li></ul> | Eenmaal per dag op basis van een vooraf vastgesteld schema voor de systeeminstellingen of handmatig via de API gestart. | Niet van toepassing | Afhankelijk van het aantal profielen, de grootte van profielen en het aantal segmenten dat wordt geëvalueerd.<ul><li>Ongeveer één uur per taak voor maximaal 10 TB profielopslaggrootte</li><li>2 uur per taak voor opslaggrootte van 10 TB tot 100 TB profiel.</li></ul> | Streaming doelen:<ul><li>Ongeveer 1 minuut aan Audience Manager en Doel</li><li>Ongeveer 10 minuten naar externe bestemmingen of microbatches afhankelijk van de bestemming.</li></ul>Geplande doelen:<ul><li>Geactiveerd aan externe bestemmingen in partij die op de geplande tijd van de bestemmingslevering wordt gebaseerd.</li></ul> | Streaming doelen: <ul><li>Wijzigingen in het lidmaatschap van de doelgroep</li><li>Identiteitswaarden</li></ul>Geplande doelen:<ul><li>Wijzigingen in het lidmaatschap van de doelgroep</li><li>Identiteitswaarden</li><li>Profielkenmerken</li></ul> |

### Guardrails voor delen publiek tussen toepassingen

| Integratie van toepassingen voor het publiek | Gebruiksscenario&#39;s | Frequentie | Productie/volume | Latentie (evaluatie van segmenten) | Latentie (segmentactivering) |
|-|-|-|-|-|-|-|-
| Platform voor realtime klantgegevens aan Audience Manager | Verrijken van reclame van derden met bekende doelgroepen | Afhankelijk van het segmentatietype - zie bovenstaande tabel met segmentatiegeleidingen. | Afhankelijk van het segmentatietype - zie bovenstaande tabel met segmentatiegeleidingen. | Afhankelijk van het segmentatietype - zie bovenstaande tabel met segmentatiegeleidingen. | <ul><li>Binnen minuten na voltooiing van de segmentbeoordeling.</li><li>De aanvankelijke synchronisatie van de publieksconfiguratie tussen RTCDP en AAM duurt ongeveer 4 uur.</li><li>Om het even welke publiekslidmaatschappen die tijdens de periode van 4 uur worden gerealiseerd zullen aan AAM op de verdere partijsegmentatietaak als &quot;bestaand&quot;publiekslidmaatschappen worden geschreven.</li></ul> |
| Adobe Analytics naar Audience Manager | Verrijken van reclame van derden met op gedrag gebaseerd publiek in korrelvorm |  | Standaard kunnen maximaal 75 soorten publiek worden gedeeld voor elke Adobe Analytics-rapportsuite. Als een Audience Manager-licentie wordt gebruikt, is er geen limiet. |  |  |
| Adobe Analytics naar Real-time Customer Data Platform | Momenteel niet beschikbaar. | Momenteel niet beschikbaar | Momenteel niet beschikbaar | Momenteel niet beschikbaar | Momenteel niet beschikbaar |


### Kenmerken en identiteiten activeren

* [!UICONTROL Het ] platform van de Gegevens van de Klant in real time kan publiekslidmaatschappen evenals attributen en identiteitsveranderingen activeren die voor profielen voorkomen die leden van segmenten zijn die voor activering worden geselecteerd. Als u attributen of identiteiten wilt activeren, moet u een globaal segment definiëren dat alle profielen bevat waarnaar kenmerken en identiteitsupdates worden verzonden. Op dat punt, kunt u het segment en gewenste attributen selecteren om als deel van de bestemmingsconfiguratie te activeren.
* Merk op dat de partijbestemmingen activering van attribuut-slechts veranderingsgebeurtenissen niet steunen. Het volledige of stijgende publiekslidmaatschap kan samen met de geselecteerde attributen voor activering worden verzonden, maar u kunt geen attribuut-enige veranderingsgebeurtenissen via partijbestemmingen activeren.

### Batchsegmenten activeren voor streamingdoelen

* Activering van batchsegmenten naar streaming doelen wordt ondersteund. De banen van het segment van de partij plaatsen berichten op de pijpleiding zodra de segmentbaan voor het stromen activering volledig is

### Streaming segmenten activeren naar batchbestemmingen

* Activering van streaming segmenten naar batchbestemmingen wordt ondersteund. Het de segmentlidmaatschap van de de uitvoer van het de partijbestemmingsprogramma van de uitvoer op het programma van de partijbestemming wordt gebaseerd. Dit omvat zowel segmentlidmaatschap dat via het stromen en partijmethodes wordt bepaald.

### Activering van ervaringsgebeurtenissen

* Het activeren van gebeurtenissen voor onbewerkte ervaring wordt niet ondersteund. Om tegen ervaringsgebeurtenissen te activeren, moet een segment met de noodzakelijke regels worden gecreeerd die de logica van de ervaringsgebeurtenis omvatten of uitsluiten. Dit leidt tot een segment dat tegen ervaringsgebeurtenissen wordt bepaald, en het segmentlidmaatschap kan als volmacht voor het activeren van ruwe ervaringsgebeurtenissen worden geactiveerd. Overweeg ook het gebruik van [!UICONTROL Server Side starten] om onbewerkte ervaringsgebeurtenissen te activeren die via SDK zijn verzameld.


## Verwante blogberichten

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
