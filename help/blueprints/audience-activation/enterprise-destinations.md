---
title: Activering van publiek en profiel naar streaming doelen voor bestanden en bedrijven (blauwdruk)
description: Activering van publiek en profiel naar Enterprise-doelen
solution: Real-Time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
source-git-commit: 8355a36a235d847a6faf2398f3fadbed28ccac37
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# Activering van publiek en profiel naar streaming doelen voor bestanden en bedrijven (blauwdruk)

Profiel- en publiekswijzigingen en gebeurtenissen in streaming of batch delen vanuit [!UICONTROL Real-time Customer Data Platform] aan de opslag van bedrijfsgegevens en toepassingen. Deze profiel- en publieksgebeurtenissen kunnen worden gebruikt om een verkoop- of ondersteuningsactie aan de klant te initiëren, zoals een follow-up van een verlaten toepassingsproces of een webinar-registratie, of om bedrijfstoepassingen bij te werken met de nieuwste klantkenmerken en intelligentie van [!UICONTROL Real-time Customer Data Platform].

## Gebruik hoofdletters

* Profiel- en publieksactivering voor cloudopslagdoelen of streamingdoelen voor het bijhouden, opslaan, analyseren en activeren van klantgegevens en -inzichten op bedrijfsniveau.

## Toepassingen

* Adobe Experience Platform-activering

## Architectuur

<img src="assets/enterprise_destination_activation.svg" alt="Referentiearchitectuur voor het activeringsscenario voor ondernemingen" style="width:90%; border:1px solid #4a4a4a" />


## Guardrails

[Raadpleeg de hulplijnen die worden beschreven op de pagina Overzicht van publiek- en profielactivering.](overview.md)

## Uitvoeringsstappen

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden ingevoerd.
1. [De juiste identiteiten en naamruimten configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) op het schema om ervoor te zorgen dat ingesloten gegevens in een verenigd profiel kunnen vastmaken.
1. [De schema&#39;s en datasets voor profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Gegevens samenvoegen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. [Voorziening [!UICONTROL Real-time Customer Data Platform] delen van segmenten](https://www.adobe.com/go/audiences) tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt gedefinieerd en aan Audience Manager wordt gedeeld.
1. [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html) in Experience Platform. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. [Doelen configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html) voor het delen van profielkenmerken en publieksleden aan gewenste bestemmingen.

## Gerelateerde documentatie

* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [Overzicht van opslagdoelen voor cloud](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [HTTP-bestemming](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* [[!UICONTROL Real-time Customer Data Platform] Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Verwante video&#39;s en zelfstudies

* [[!UICONTROL Real-time Customer Data Platform] overzicht](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
