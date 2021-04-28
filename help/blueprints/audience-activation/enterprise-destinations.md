---
title: Activering van publiek en profiel naar Enterprise-doelen - blauwdruk
description: Activering van publiek en profiel naar Enterprise-doelen
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: 2f35195b875d85033993f31c8cef0f85a7f6cccc
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# Activering van publiek en profiel naar Enterprise-doelen - blauwdruk

Deel profiel- en publiekswijzigingen en -gebeurtenissen in streaming of batch van [!UICONTROL Real-time Customer Data Platform] naar bedrijfsgegevenswinkels en -toepassingen. Deze profiel- en publieksgebeurtenissen kunnen worden gebruikt om een verkoop- of ondersteuningsactie aan de klant te initiëren, zoals het volgen van een afgebroken toepassingsproces of webinar-registratie, of om bedrijfstoepassingen bij te werken met de nieuwste klantkenmerken en intelligentie van [!UICONTROL Real-time Customer Data Platform].

## Gevallen gebruiken

* Profiel- en publieksactivering voor cloudopslagdoelen of streamingdoelen voor het bijhouden, opslaan, analyseren en activeren van klantgegevens en -inzichten op bedrijfsniveau.

## Toepassingen

* Adobe Experience Platform-activering

## Architectuur

<img src="assets/enterprise_destination.svg" alt="Referentiearchitectuur voor het activeringsscenario voor ondernemingen" style="border:1px solid #4a4a4a" />

## Guardrails

[Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

### Guardrails voor segmentbeoordeling en -activering

| Segmentatietype | Frequentie | Doorvoer | Latentie (evaluatie van segmenten) | Latentie (segmentactivering) | Payload activeren |
|-|-|-|-|-|-|
| Randsegmentatie | De segmentatie van de rand is momenteel in bèta en staat voor geldige real-time segmentatie toe om op het Netwerk van de Rand van het Experience Platform voor real-time, zelfde paginabesluit via Adobe Target en Adobe Journey Optimizer worden geëvalueerd. |  | ~100 ms | Direct beschikbaar voor personalisatie in Adobe Target, voor profielopzoekingen in het Edge-profiel en voor activering via op cookies gebaseerde doelen. | Publiek Membership beschikbaar op de Rand voor profielraadplegingen en koekjesgebaseerde bestemmingen.<br>Adobe Target en Journey Optimizer hebben toegang tot publiek- en profielkenmerken.  |
| Streaming segmentering | Telkens wanneer een nieuwe het stromen gebeurtenis of een verslag in het klantenprofiel in real time wordt opgenomen en de segmentdefinitie een geldig het stromen segment is. <br>Zie de  [segmentatiedocumentatie ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html) voor richtlijnen over streamingsegmentcriteria | Tot 1500 gebeurtenissen per seconde.  | ~ p95 &lt;5min | Streaming doelen: Het lidmaatschap van het streaming publiek wordt binnen ongeveer 10 minuten geactiveerd of wordt op basis van de vereisten van de bestemming op micro-batches geactiveerd.<br>Geplande doelen: Het stromen publiekslidmaatschap wordt geactiveerd in partij die op de geplande tijd van de bestemmingslevering wordt gebaseerd. | Streaming doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |
| Incrementele segmentatie | Eenmaal per uur voor nieuwe gegevens die zijn opgenomen in het realtime klantprofiel sinds de laatste incrementele of batchsegmentevaluatie. |  |  | Streaming doelen: Het incrementele publiekslidmaatschap wordt binnen ongeveer 10 minuten geactiveerd of op micro-basis op basis van de vereisten van de bestemming.<br>Geplande doelen: De incrementele publiekslidmaatschappen worden geactiveerd in partij die op de geplande tijd van de bestemmingslevering wordt gebaseerd. | Streaming doelen: Alleen wijzigingen in het lidmaatschap van het publiek en identiteitswaarden.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |
| Batchsegmentering | Eenmaal per dag op basis van een vooraf vastgesteld schema voor het systeem of handmatig gestart via de API. |  | Ongeveer één uur per taak voor een opslagcapaciteit van maximaal 10 TB, 2 uur per taak voor een opslagcapaciteit van 10 TB tot 100 TB. De prestaties van batchsegmenttaken zijn afhankelijk van numerieke profielen, de grootte van profielen en het aantal segmenten dat wordt geëvalueerd. | Streaming doelen: Het lidmaatschap van het batchpubliek wordt geactiveerd binnen ongeveer 10 jaar na voltooiing van de segmentatiebeoordeling of op micro-batches gebaseerd op de vereisten van de bestemming.<br>Geplande doelen: De het publiekslidmaatschappen van de partij worden geactiveerd gebaseerd op de geplande tijd van de bestemmingslevering. | Streaming doelen: Alleen wijzigingen in het lidmaatschap van het publiek en identiteitswaarden.<br>Geplande doelen: Wijzigingen in het publiekslidmaatschap, identiteitswaarden en profielkenmerken. |



## Implementatiestappen

1. Maak schema&#39;s voor gegevens die moeten worden ingevoerd.
1. Maak gegevenssets voor gegevens die moeten worden opgenomen.
1. Vorm de correcte identiteiten en identiteitsnamespaces op het schema om ervoor te zorgen dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. Laat de schema&#39;s en datasets voor profielverwerking toe.
1. Vorm om het even welke bronnen voor gegevensopname.
1. Auteurssegmenten in Experience Platform, te evalueren in batch of streaming. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. Vorm bestemmingen voor het delen van profielattributen en publiekslidmaatschappen aan gewenste bestemmingen.

## Overwegingen bij de implementatie

Kenmerken en identiteiten activeren

* [!UICONTROL Het ] platform van de Gegevens van de Klant in real time kan publiekslidmaatschappen evenals attributen en identiteitsveranderingen activeren die voor profielen voorkomen die leden van segmenten zijn die voor activering worden geselecteerd. Als u attributen of identiteiten wilt activeren, moet u een globaal segment definiëren dat alle profielen bevat waarnaar kenmerken en identiteitsupdates worden verzonden. Op dat punt, kunt u het segment en gewenste attributen selecteren om als deel van de bestemmingsconfiguratie te activeren.
* Merk op dat de partijbestemmingen activering van attribuut-slechts veranderingsgebeurtenissen niet steunen. Het volledige of stijgende publiekslidmaatschap kan samen met de geselecteerde attributen voor activering worden verzonden, maar u kunt geen attribuut-enige veranderingsgebeurtenissen via partijbestemmingen activeren.

Batchsegmenten activeren voor streamingdoelen

* Activering van batchsegmenten naar streaming doelen wordt ondersteund. De banen van het segment van de partij plaatsen berichten op de pijpleiding zodra de segmentbaan voor het stromen activering volledig is

Streaming segmenten activeren naar batchbestemmingen

* Activering van streaming segment naar batchbestemming wordt ondersteund. Het de segmentlidmaatschap van de de uitvoer van het de partijbestemmingsprogramma van de uitvoer op het programma van de partijbestemming wordt gebaseerd. Dit omvat zowel segmentlidmaatschap dat via het stromen en partijmethodes wordt bepaald.

Activering van ervaringsgebeurtenissen

* Het activeren van gebeurtenissen voor onbewerkte ervaring wordt niet ondersteund. Om tegen ervaringsgebeurtenissen te activeren, moet een segment met de noodzakelijke regels worden gecreeerd die de logica van de ervaringsgebeurtenis omvatten of uitsluiten. Dit leidt tot een segment dat tegen ervaringsgebeurtenissen wordt bepaald, en het segmentlidmaatschap kan als volmacht voor het activeren van ruwe ervaringsgebeurtenissen worden geactiveerd. Overweeg ook het gebruik van [!UICONTROL Server Side starten] om onbewerkte ervaringsgebeurtenissen te activeren die via SDK zijn verzameld.

## Verwante documentatie

* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [Overzicht van opslagdoelen voor cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP-bestemming](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [[!UICONTROL Real-time Customer Data ] PlatformProductbeschrijving](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Verwante video&#39;s en Tutorials

* [[!UICONTROL Real-time ] overzicht van klantgegevens](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van het Platform van de Gegevens van de Klant in  [!UICONTROL real time]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
