---
title: Online/offline Audience Activation vervagen
description: Online/offline Audience Activation.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 24b6ffe3021389d33e84688a8f1a90711ca4b772
workflow-type: tm+mt
source-wordcount: '990'
ht-degree: 0%

---

# Online/offline Audience Activation vervagen

Gebruik offlinekenmerken en -gebeurtenissen zoals offline bestellingen, transacties, CRM of loyaliteitsgegevens, samen met onlinegedrag voor het online aanwijzen en personaliseren.

Activeer het publiek naar bekende, op profielen gebaseerde bestemmingen, zoals e-mailproviders, sociale netwerken en advertentiebestemmingen.

## Gevallen gebruiken

* Publiek dat zich richt op bekende doelgroepen op sociale en reclamebestemmingen.
* Online personalisatie met online en offline kenmerken.
* Activeer het publiek naar bekende kanalen, zoals e-mail en SMS.

## Toepassingen

* Adobe Experience Platform
* [!UICONTROL Real-time Platform voor klantgegevens]

## Architectuur

<img src="assets/onoff.svg" alt="Referentiearchitectuur voor de blauwdruk voor online/offline Audience Activation" style="border:1px solid #4a4a4a" />

## Guardrails

* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

### Guardrails voor segmentbeoordeling en -activering

| Segmentatietype | Frequentie | Doorvoer | Latentie (segmentevaluatie) | Latentie (segmentactivering) | Payload activeren |
|---|---|---|---|---|---|
| Randsegmentatie | De segmentatie van de rand is momenteel in bèta en staat voor geldige segmentatie in real time toe die op het Netwerk van de Rand van het Experience Platform voor real time, zelfde paginabesluit via Adobe Target en Adobe Journey Optimizer wordt geëvalueerd. |  | ~100 ms | Direct beschikbaar voor personalisatie in Adobe Target, voor profielraadplegingen in het Profiel van de Rand, en voor activering via op koekjes gebaseerde bestemmingen. | De Lidmaatschappen van het publiek beschikbaar op de Rand voor profielraadplegingen en koekjesgebaseerde bestemmingen.<br>Adobe Target en Journey Optimizer hebben toegang tot publiek- en profielkenmerken. |
| Streaming segmentering | Telkens wanneer een nieuwe het stromen gebeurtenis of een verslag in het klantenprofiel in real time wordt opgenomen en de segmentdefinitie is een geldig het stromen segment. <br>Zie de  [segmentatiedocumentatie ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html) voor richtlijnen over streamingsegmentcriteria | Tot 1500 gebeurtenissen per seconde. | ~ p95 &lt;5min | Streaming doelen: Het lidmaatschap van het streaming publiek wordt binnen ongeveer 10 minuten geactiveerd of wordt op basis van de vereisten van de bestemming op micro-batches geactiveerd.<br>Geplande doelen: Het stromen publiekslidmaatschap wordt geactiveerd in partij die op de geplande tijd van de bestemmingslevering wordt gebaseerd. | Streaming doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |
| Incrementele segmentatie | Eenmaal per uur voor nieuwe gegevens die in het klantprofiel in real time sinds de laatste incrementele of batchsegmentevaluatie zijn opgenomen. |  |  | Streaming doelen: Het incrementele publiekslidmaatschap wordt binnen ongeveer 10 minuten geactiveerd of op micro-basis op basis van de vereisten van de bestemming.<br>Geplande doelen: De incrementele publiekslidmaatschappen worden geactiveerd in partij die op de geplande tijd van de bestemmingslevering wordt gebaseerd. | Streaming doelen: Alleen wijzigingen in het lidmaatschap van het publiek en identiteitswaarden.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |
| Batchsegmentatie | Eenmaal per dag op basis van een vooraf vastgesteld schema voor de systeeminstellingen of handmatig via de API gestart. |  | Ongeveer één uur per taak voor een opslagcapaciteit van maximaal 10 TB profiel, 2 uur per taak voor een opslaggrootte van 10 TB tot 100 TB profiel. De prestaties van batchsegmenttaken zijn afhankelijk van numerieke profielen, de grootte van profielen en het aantal segmenten dat wordt geëvalueerd. | Streaming doelen: Het lidmaatschap van het batchpubliek wordt geactiveerd binnen ongeveer 10 jaar na voltooiing van de segmentatiebeoordeling of op micro-batches gebaseerd op de vereisten van de bestemming.<br>Geplande doelen: De het publiekslidmaatschappen van de partij worden geactiveerd gebaseerd op de geplande tijd van de bestemmingslevering. | Streaming doelen: Alleen wijzigingen in het lidmaatschap van het publiek en identiteitswaarden.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |

### Guardrails voor delen publiek tussen toepassingen

| Integratie van doeltoepassingen | Frequentie | Doorvoer/volume | Latentie (segmentevaluatie) | Latentie (segmentactivering) |
|---|---|---|---|---|
| Real-time Platform van klantgegevens aan Audience Manager | Afhankelijk van het segmentatietype. Zie de bovenstaande tabel met segmentatiehulplijnen. | Afhankelijk van het segmentatietype. Zie de bovenstaande tabel met segmentatiehulplijnen. | Afhankelijk van het segmentatietype. Zie de bovenstaande tabel met segmentatiehulplijnen. | Binnen minuten na voltooiing van de segmentbeoordeling.<br>De aanvankelijke synchronisatie van de publieksconfiguratie tussen het Platform en de Audience Manager van de Gegevens van de Klant in real time neemt ongeveer 4 uur.<br>Om het even welke publiekslidmaatschappen die tijdens de periode van 4 uur worden gerealiseerd zullen aan Audience Manager op de verdere partijsegmentatietaak als &quot;bestaand&quot;publieksenlidmaatschap worden geschreven. |
| Adobe Analytics naar Audience Manager |  | Standaard kunnen maximaal 75 soorten publiek worden gedeeld voor elke Adobe Analytics-rapportsuite. Als een Audience Manager-licentie wordt gebruikt, is er geen limiet voor het aantal soorten publiek dat kan worden gedeeld tussen Adobe Analytics en Adobe Target of Adobe Audience Manager en Adobe Target. |  |  |
| Adobe Analytics naar Real-time Customer Data Platform | Momenteel niet beschikbaar | Momenteel niet beschikbaar | Momenteel niet beschikbaar | Momenteel niet beschikbaar |





## Implementatiestappen

1. Vorm schema&#39;s en datasets in Experience Platform.
1. Vorm de correcte identiteiten en identiteitsnamespaces op het schema om ervoor te zorgen dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. Laat het schema en de datasets voor Profiel toe.
1. Gegevens opnemen in Platform.
1. Bepaling [!UICONTROL Real-time Customer Data Platform] segment sharing tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt bepaald om aan Audience Manager te worden gedeeld.
1. Auteurssegmenten in Experience Platform, te evalueren in batch of streaming. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. Vorm bestemmingen voor het delen van profielattributen en publiekslidmaatschappen aan gewenste bestemmingen.

## Overwegingen bij de implementatie

* Wanneer u profielgegevens deelt met bestemmingen, moet u de specifieke identiteitswaarde opnemen die door de bestemming wordt gebruikt in de doellading. Om het even welke identiteit die voor een doelbestemming noodzakelijk is moet in Platform worden opgenomen en als identiteit voor [!UICONTROL Real-time Profiel van de Klant worden gevormd ].

* Voor activeringsscenario&#39;s waarin het publiek van Experience Platform tot Audience Manager wordt gedeeld, worden alle identiteiten inbegrepen in [!UICONTROL Real-time Klantprofiel] gedeeld aan Audience Manager. Het publiek van Experience Platform kan via de bestemmingen van de Audience Manager worden gedeeld wanneer de vereiste bestemmingsidentiteiten in [!UICONTROL Real-time het Profiel van de Klant ] worden omvat, of waar de identiteiten in [!UICONTROL Real-time Klantprofiel] met de vereiste bestemmingsidentiteiten kunnen worden verwant die in Audience Manager worden verbonden.

## Verwante documentatie

* [[!UICONTROL Real-time Customer Data ] PlatformProductbeschrijving](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Verwante video&#39;s en Tutorials

* [[!UICONTROL Real-time ] overzicht van klantgegevens](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van het Platform van de Gegevens van de Klant in  [!UICONTROL real time]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
