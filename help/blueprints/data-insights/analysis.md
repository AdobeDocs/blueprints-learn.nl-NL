---
title: Gegevensanalyse en inlichtingenblauwdruk
description: Adobe gebruiken [!DNL Experience Platform] (AEM) verkennende vraag en analyse van de gegevens uitvoeren die in het gegevensmeer bestaan.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 0%

---

# Gegevensanalyse en inlichtingenblauwdruk

Gegevensanalyse en -intelligentie omvat het vermogen binnen [!DNL Experience Platform] om verkennende vraag en analyse van de gegevens uit te voeren die in het gegevensmeer bestaan.

[!DNL Experience Platform]s [!UICONTROL Query-service] staat SQL vragen toe om op de gegevens worden uitgevoerd.

[!DNL Experience Platform] staat verbindingen met derdeSQL cliënten, interfaces, en Business Intelligence (BI) hulpmiddelen toe om met, tot de gegevens binnen direct toegang te hebben en te vragen [!DNL Experience Platform], met de [!DNL PostgreSQL] protocol.

## Gebruik hoofdletters

* Interactieve query en aggregatie van gegevens
* De rij en kolomtoegang tot ingebedde gegevens voor exploratie en bevestiging
* Dashboarding en visualisatie van gegevens via Business Intelligence tooling

Hier worden extra veelvoorkomende gebruiksgevallen voor de queryservice beschreven [Gebruik van query-service-aanvragen](https://experienceleague.adobe.com/docs/experience-platform/query/use-cases/abandoned-browse.html?lang=nl-NL)

## Toepassingen

* Adobe [!DNL Experience Platform]

## Architectuur

<img src="assets/data_exploration.svg" alt="Referentiearchitectuur voor de Enterprise Data Exploration and Reporting Blueprint" style="width:90%; border:1px solid #4a4a4a" />

## Guardrails

Raadpleeg de documentatie bij het product Query Service voor meer informatie over beste praktijken en instructies.
[Begeleiding voor zoekservice](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=nl-NL)

## Implementatiestappen

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=nl-NL) voor gegevens die moeten worden ingevoerd.
1. [Samenvattingsgegevens](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in [!DNL Experience Platform].
1. Bevestig dat gegevens beschikbaar zijn voor [[!UICONTROL Query-service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=nl-NL).
1. [Business Intelligence-gereedschappen en SQL-clients verbinden met [!UICONTROL Query-service]](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=nl-NL) voor visualisatie, gegevensvraag, en exploratie.

## Gerelateerde documentatie

* [Adobe [!DNL Experience Platform] Omschrijving van het inlichtingenproduct](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Query-service] documentatie](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=nl-NL)
