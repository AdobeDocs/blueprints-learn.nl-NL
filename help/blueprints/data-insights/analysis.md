---
title: Gegevensanalyse en inlichtingenblauwdruk
description: Deze blauwdruk toont de capaciteit binnen Adobe Experience Platform om verkennende vraag en analyse van de gegevens uit te voeren die in het gegevensmeer bestaan.
solution: Experience Platform
kt: 7207
thumbnail: null
exl-id: 3b22dfdd-3fbe-40b3-b798-1ee983723039,a972ea56-d1c8-45da-9044-ed31222a2441
translation-type: tm+mt
source-git-commit: cd98c46d948af9026449c947496df82fd1be6718
workflow-type: tm+mt
source-wordcount: '285'
ht-degree: 0%

---

# Gegevensanalyse en inlichtingenblauwdruk

De Analyse en de Intelligentie van gegevens omvat de capaciteit binnen Adobe Experience Platform om verkennende vraag en analyse van de gegevens uit te voeren die in het gegevensmeer bestaan.

De Dienst van de Vraag van het Experience Platform staat SQL vragen toe om op de gegevens worden uitgevoerd. De werkruimte van de Wetenschap van Gegevens laat gegevensexploratie, gegevenswetenschap, en machine het leren werklasten toe om op de gegevens worden uitgevoerd.

Bovendien staat het Experience Platform verbindingen met derdeSQL cliënten, interfaces, en de hulpmiddelen van de Business Intelligence (BI) toe om met, tot de gegevens binnen Experience Platform direct te verbinden toegang te hebben en te vragen, gebruikend het protocol PostgreSQL.

Bepaalde garanties zijn van toepassing op de vraagonderbreking en voor de hoeveelheid gegevens die in het vraagresultaat inbegrepen is, zoals vermeld binnen de scenario details.

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
1. Bevestig dat de gegevens aan de Dienst van de Vraag en de Werkruimte van de Wetenschap van Gegevens voor ruwe toegang en vraag beschikbaar zijn.
1. Verbind de hulpmiddelen van de Business Intelligence en SQL cliënten met de Dienst van de Vraag voor visualisatie, gegevensvraag, en exploratie.

## Verwante documentatie

* [Productbeschrijving Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Documentatie bij Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en)
