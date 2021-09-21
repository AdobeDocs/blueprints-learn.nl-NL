---
title: Gegevensanalyse en inlichtingenblauwdruk
description: Deze blauwdruk toont de capaciteit binnen Adobe Experience Platform om verkennende vraag en analyse van de gegevens uit te voeren die in het gegevensmeer bestaan.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: a972ea56-d1c8-45da-9044-ed31222a2441
source-git-commit: 5e93d3a5a09a3a20418ec7e563b93d22aef3ddc7
workflow-type: tm+mt
source-wordcount: '337'
ht-degree: 0%

---

# Gegevensanalyse en inlichtingenblauwdruk

De Analyse en de Intelligentie van gegevens omvat de capaciteit binnen Adobe Experience Platform om verkennende vraag en analyse van de gegevens uit te voeren die in het gegevensmeer bestaan.

Met de [!UICONTROL Query Service] van het Experience Platform kunnen SQL-query&#39;s op de gegevens worden uitgevoerd. [!UICONTROL Met Data Science ] Workspacets kunnen gegevensexploratie, gegevenswetenschap en werklasten voor machinaal leren worden uitgevoerd op de gegevens.

Bovendien staat het Experience Platform verbindingen met derdeSQL cliënten, interfaces, en hulpmiddelen van de Business Intelligence (BI) toe om met, tot de gegevens binnen Experience Platform direct te verbinden toegang te hebben en te vragen, gebruikend het [!DNL PostgreSQL] protocol.

Bepaalde instructies gelden voor de time-out van de query en voor de hoeveelheid gegevens die in het queryresultaat is opgenomen, zoals vermeld in de details van de blauwdruk.

## Gevallen gebruiken

* Interactieve query en aggregatie van gegevens
* De rij en kolomtoegang tot ingebedde gegevens voor exploratie en bevestiging
* Dashboarding en visualisatie van gegevens via Business Intelligence tooling

## Toepassingen

* Adobe Experience Platform

## Architectuur

<img src="assets/data_exploration.svg" alt="Referentiearchitectuur voor de Enterprise Data Exploration and Reporting Blueprint" style="border:1px solid #4a4a4a" />

## Guardrails

Raadpleeg de documentatie bij het product Query Service voor meer informatie over beste praktijken en instructies.
[Begeleiding voor zoekservice](https://experienceleague.adobe.com/docs/experience-platform/query/best-practices/writing-queries.html?lang=en#best-practices)

## Implementatiestappen

1. [Maak ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) schema&#39;s voor gegevens die moeten worden ingevoerd.
1. [Maak ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) gegevenssets voor gegevens die moeten worden ingevoerd.
1. [Gegevens ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform opnemen.
1. Bevestig dat de gegevens aan [[!UICONTROL Query Service]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/queries/explore-data.html?lang=en) en [[!UICONTROL Data Science Workspace]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/load-data-in-jupyterlab-notebooks.html?lang=en) voor ruwe toegang en vraag beschikbaar zijn.
1. [Verbind de hulpmiddelen van de Business Intelligence en SQL cliënten met de  [!UICONTROL Dienst van de Vraag ]](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.qsvc.dash) voor visualisatie, gegevensvraag, en exploratie.

## Verwante documentatie

* [Productbeschrijving Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Query ] Services-documentatie](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
