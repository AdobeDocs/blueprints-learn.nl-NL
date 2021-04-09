---
title: Gegevensanalyse en inlichtingenblauwdruk
description: Deze blauwdruk toont de capaciteit binnen Adobe Experience Platform om verkennende vraag en analyse van de gegevens uit te voeren die in het gegevensmeer bestaan.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: 009a55715b832c3167e9a3413ccf89e0493227df
workflow-type: tm+mt
source-wordcount: '283'
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

<img src="assets/dataexplore.svg" alt="Referentiearchitectuur voor de Enterprise Data Exploration and Reporting Blueprint" style="border:1px solid #4a4a4a" />

## Guardrails

* Tijdslimiet van 10 minuten voor interactieve query&#39;s
* Limiet voor 100 records die wordt geretourneerd in de gebruikersinterface
* Maximaal 50.000 records die via de SQL-connector worden geretourneerd

## Implementatiestappen

1. Vorm datasets en schema&#39;s voor gegevensopname in het gegevensmeer.
1. Samenvattingsgegevens.
1. Bevestig dat de gegevens aan [!UICONTROL Query Service] en [!UICONTROL Data Science Workspace] voor ruwe toegang en vraag beschikbaar zijn.
1. Verbind de hulpmiddelen van de Business Intelligence en SQL cliënten met [!UICONTROL de Dienst van de Vraag] voor visualisatie, gegevensvraag, en exploratie.

## Verwante documentatie

* [Productbeschrijving Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Query ] Services-documentatie](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
