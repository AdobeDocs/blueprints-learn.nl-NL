---
title: Gegevensanalyse en inlichtingenblauwdruk
description: Deze blauwdruk toont de capaciteit binnen Adobe Experience Platform om verkennende vraag en analyse van de gegevens uit te voeren die in het gegevensmeer bestaan.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Gegevensanalyse en inlichtingenblauwdruk

De Analyse en de Intelligentie van gegevens omvat de capaciteit binnen Adobe Experience Platform om verkennende vraag en analyse van de gegevens uit te voeren die in het gegevensmeer bestaan.

Experience Platform [!UICONTROL Query-service] staat SQL vragen toe om op de gegevens worden uitgevoerd.

Het Experience Platform staat verbindingen met derdeSQL cliënten, interfaces, en hulpmiddelen van de Business Intelligence (BI) toe om met, tot de gegevens binnen Experience Platform direct te verbinden toegang te hebben en te vragen, gebruikend [!DNL PostgreSQL] protocol.

## Gebruik hoofdletters

* Interactieve query en aggregatie van gegevens
* De rij en kolomtoegang tot ingebedde gegevens voor exploratie en bevestiging
* Dashboarding en visualisatie van gegevens via Business Intelligence tooling

Hier worden extra veelvoorkomende gebruiksgevallen voor de queryservice beschreven [Gebruik van query-service-aanvragen](https://experienceleague.adobe.com/docs/experience-platform/query/use-cases/abandoned-browse.html)

## Toepassingen

* Adobe Experience Platform

## Architectuur

<img src="assets/data_exploration.svg" alt="Referentiearchitectuur voor de Enterprise Data Exploration and Reporting Blueprint" style="width:90%; border:1px solid #4a4a4a" />

## Guardrails

Raadpleeg de documentatie bij het product Query Service voor meer informatie over beste praktijken en instructies.
[Begeleiding voor zoekservice](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html)

## Uitvoeringsstappen

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden ingevoerd.
1. [Gegevens samenvoegen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. Bevestig dat gegevens beschikbaar zijn voor [[!UICONTROL Query-service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=en).
1. [Business Intelligence-gereedschappen en SQL-clients verbinden met [!UICONTROL Query-service]](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html) voor visualisatie, gegevensvraag, en exploratie.

## Gerelateerde documentatie

* [Productbeschrijving Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Query-service] documentatie](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
