---
title: Activering van publiek en profiel naar Enterprise-doelen - blauwdruk
description: Activering van publiek en profiel naar Enterprise-doelen
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
translation-type: tm+mt
source-git-commit: a63da7d5da3038cf66b5f2c99e117d4aa5b21cc1
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Activering van publiek en profiel naar Enterprise-doelen - blauwdruk

Replicatie en update van profiel- en publiekswijzigingen naar bedrijfsgegevensopslagsystemen voor activering en rapportage van gebruiksgevallen. <!-- This sentence is difficult to mentally process because there's no verb. Describe what the customer can do with this feature. The first paragraph on a page should not be an abstract description.-->

Een verkoop- of ondersteuningsactie aan de klant initiëren via een kennisgeving van een actie van de klant van het [!UICONTROL Real-time Platform van klantgegevens] aan bedrijfssystemen en toepassingen. <!-- What kinds of sales or support actions? You might add a "For example...." The content in these blueprints should be more simple and friendly.-->

## Gevallen gebruiken

* Profiel- en publieksactivering voor cloudopslagdoelen of streamingdoelen voor het bijhouden, opslaan, analyseren en activeren van klantgegevens en -inzichten op bedrijfsniveau.

## Toepassingen

* Adobe Experience Platform-activering

## Architectuur

<img src="assets/enterprise_destination.svg" alt="Referentiearchitectuur voor het activeringsscenario voor ondernemingen" style="border:1px solid #4a4a4a" />

## Guardrails

[Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

Latentie- en productiedrempels:

Streaming segmentatie:

* Tot 5 minuten voor streamingsegmentatie, tot 1500 gebeurtenissen per seconde
* Tot 11 minuten voor activering van streaming

Batchsegmentatie:
Eenmaal per dag of handmatig gestart via de API.

* Ongeveer 1 uur per taak voor maximaal 10 TB profielopslaggrootte
* Ongeveer 2 uur per taak voor opslaggrootte van 10 TB tot 100 TB profiel

## Implementatiestappen

1. Maak schema&#39;s voor gegevens die moeten worden ingevoerd. <!-- Cross-references to these topics would be helpful -->
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
