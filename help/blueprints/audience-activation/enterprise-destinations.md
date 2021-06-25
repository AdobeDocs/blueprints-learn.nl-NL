---
title: Activering van publiek en profiel naar Enterprise-doelen - blauwdruk
description: Activering van publiek en profiel naar Enterprise-doelen
solution: Experience Platform,Real-time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5,None
source-git-commit: 2fc1adc04a9ca2184c88970d5ba0785957327f68
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# Activering van publiek en profiel naar Enterprise-doelen - blauwdruk

Deel profiel- en publiekswijzigingen en -gebeurtenissen in streaming of batch van [!UICONTROL Real-time Customer Data Platform] naar bedrijfsgegevenswinkels en -toepassingen. Deze profiel- en publieksgebeurtenissen kunnen worden gebruikt om een verkoop- of ondersteuningsactie aan de klant te initiëren, zoals het volgen van een afgebroken toepassingsproces of webinar-registratie, of om bedrijfstoepassingen bij te werken met de nieuwste klantkenmerken en intelligentie van [!UICONTROL Real-time Customer Data Platform].

## Gevallen gebruiken

* Profiel- en publieksactivering voor cloudopslagdoelen of streamingdoelen voor het bijhouden, opslaan, analyseren en activeren van klantgegevens en -inzichten op bedrijfsniveau.

## Toepassingen

* Adobe Experience Platform-activering

## Architectuur

<img src="assets/enterprise_destination_activation.svg" alt="Referentiearchitectuur voor het activeringsscenario voor ondernemingen" style="border:1px solid #4a4a4a" />


## Guardrails

[Raadpleeg de hulplijnen die worden beschreven op de pagina Overzicht van publiek- en profielactivering.](overview.md)

## Implementatiestappen

1. [Maak ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) schema&#39;s voor gegevens die moeten worden ingevoerd.
1. [Maak ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) gegevenssets voor gegevens die moeten worden ingevoerd.
1. [Vorm de correcte identiteiten en de identiteit ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) namespacesop het schema om ervoor te zorgen dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. [Laat de schema&#39;s en datasets voor profiel](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html) toe.
1. [Gegevens ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform opnemen.
1. [Levering van  [!UICONTROL realtime ]  ](https://www.adobe.com/go/audiences) platformoverschrijding van klantgegevens tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt gedefinieerd en aan Audience Manager wordt gedeeld.
1. [Maak ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html) segmentaties in het Experience Platform. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. [Vorm bestemmingen ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html) voor het delen van profielattributen en publiekslidmaatschappen aan gewenste bestemmingen.

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
