---
title: Blauwdruk profiel en Audience Activation naar zakelijke doelen
description: Profiel en Audience Activation naar Enterprise-doelen
solution: Experience Platform,Real-time Customer Data Platform,Target,Audience Manager,Analytics,Experience Cloud Services,Data Collection
kt: 7086
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
translation-type: tm+mt
source-git-commit: 2fa5fc1def554713b057e1478bdd65a15913e0e4
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 0%

---


# Blauwdruk profiel en Audience Activation naar zakelijke doelen

Replicatie en update van profielwijzigingen naar bedrijfsgegevensopslagsystemen voor activering en rapportage van gebruiksgevallen.

Een verkoop- of ondersteuningsactie aan de klant initiëren via een melding van een actie van de klant van het Real-time Platform van klantgegevens aan bedrijfssystemen en -toepassingen.

## Gevallen gebruiken

* Activering van profiel en publiek naar cloudopslagbestemmingen of streamingbestemmingen voor het bijhouden, opslaan, analyseren en activeren van klantgegevens en -inzichten op bedrijfsniveau.

## Toepassingen

* Adobe Experience Platform-activering

## Architectuur

<img src="assets/enterprise_destination.svg" alt="Referentiearchitectuur voor het activeringsscenario voor ondernemingen" style="border:1px solid #4a4a4a" />

## Guardrails

[Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

Drempelwaarden voor latentie en doorvoer:

Streaming segmentatie:

* Tot 5 minuten voor streamingsegmentatie, tot 1500 gebeurtenissen per seconde
* Tot 11 minuten voor activering van streaming

Batchsegmentatie:
Eenmaal per dag of handmatig gestart via de API

* Ongeveer 1 uur per taak voor maximaal 10 TB profielopslaggrootte
* Ongeveer 2 uur per taak voor opslaggrootte van 10 TB tot 100 TB profiel

## Implementatiestappen

1. Schema&#39;s maken voor gegevens die moeten worden ingevoerd
1. Gegevenssets maken voor gegevens die moeten worden ingevoerd
1. Vorm de correcte identiteiten en identiteitsnamespaces op het schema om ervoor te zorgen dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. Laat de schema&#39;s en datasets voor profielverwerking toe.
1. Vorm om het even welke Bronnen voor gegevensopname
1. Auteurssegmenten in Experience Platform, te evalueren in batch of streaming. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. Vorm bestemmingen voor het delen van profielattributen en publiekslidmaatschappen aan gewenste bestemmingen.

## Overwegingen bij de implementatie

Activering van kenmerken en identiteiten

* Het Platform van Gegevens van de Klant in real time kan zowel publiekslidmaatschappen als attributen en identiteitsveranderingen activeren die voor profielen voorkomen die leden van segmenten zijn die voor activering zijn geselecteerd. Als het gebruiksscenario het activeren van kenmerken en/of identiteiten is, moet een algemeen segment worden gedefinieerd dat alle profielen omvat waarvoor kenmerk-/identiteitsupdates worden verzonden. Zodra dit op zijn plaats is kunnen het segment en de gewenste te activeren attributen als deel van de bestemmingsconfiguratie worden geselecteerd.
* Merk op dat de partijbestemmingen activering van attribuut slechts veranderingsgebeurtenissen niet steunen. Volledige of incrementele deelname van het publiek kan samen met de geselecteerde kenmerken voor activering worden verzonden, maar alleen wijzigingsgebeurtenissen van kenmerken kunnen niet via batchbestemmingen worden geactiveerd.

Batchsegmentactivering naar streaming doelen

* Activering van batchsegmenten naar streaming doelen wordt ondersteund. De banen van het segment van de partij plaatsen berichten op de pijpleiding zodra de segmentbaan voor het stromen activering volledig is

Activering streaming segment naar batchbestemmingen

* Activering van streaming segment naar batchbestemming wordt ondersteund. Het programma van de partijbestemming zal segmentlidmaatschap van de profielen uitvoeren die op het programma van de partijbestemming worden gebaseerd. Dit omvat zowel segmentlidmaatschap dat via het stromen en partijmethodes wordt bepaald.

Activering van Experience Events

* Activering van onbewerkte ervaringsgebeurtenissen wordt momenteel niet ondersteund. Om tegen ervaringsgebeurtenissen te activeren moet een segment met de noodzakelijke regels worden gecreeerd die de logica van de ervaringsgebeurtenis omvatten/uitsluiten waartegen moet worden geactiveerd. Dit leidt tot een segment dat tegen ervaringsgebeurtenissen wordt bepaald - en het segmentlidmaatschap kan als volmacht voor het activeren van ruwe ervaringsgebeurtenissen worden geactiveerd. Overweeg ook de opstartserver te gebruiken voor het activeren van onbewerkte ervaringsgebeurtenissen die via SDK zijn verzameld.

## Verwante documentatie

* [Productbeschrijving in realtime-Platform voor klantgegevens](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Verwante video&#39;s en Tutorials

* [Overzicht van het Platform voor realtime klantgegevens](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van Platform van realtime klantgegevens](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
