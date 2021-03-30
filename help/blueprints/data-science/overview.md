---
title: Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking
description: Deze blauwdruk laat zien hoe de Werkruimte van de Wetenschap van Gegevens van Adobe Experience Platform gegevens binnen Experience Platform kan gebruiken om, modellen op te leiden, op te stellen en te scoren om machine het leren inzichten van de gegevens te verstrekken.
solution: Experience Platform, Data Collection
kt: 7203
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---


# Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking

Deze blauwdruk laat zien hoe de gegevens in Adobe Experience Platform door de Werkruimte van de Wetenschap van Gegevens worden gebruikt om, modellen op te leiden, op te stellen en te scoren om machine het leren inzichten te verstrekken. Deze modellen kunnen rechtstreeks uitvoeren aan een dataset die voor het Profiel van de Klant in real time wordt toegelaten. Voorbeelden van computerleerinzichten zijn levenslange waarde, product- en categorievestigheid, conversiedrietheid of churn-gevoeligheid.

## Gevallen gebruiken

* Haal inzicht uit en ontdek patronen van klantengegevens in Experience Platform. Train- en scoremodellen van deze gegevens.
* Verrijk het profiel van de Klant in real time met model gedreven inzichten en attributen voor meer korrelige personalisering en geoptimaliseerde reis optimalisering.
* Train- en Score-modellen om de inzichten van klanten te bepalen, zoals de levenslange waarde van de klant, de neiging om te converteren of te klonen, de affiniteit van producten en inhoud, en servicescore.

## Scenarios

| Scenario | Beschrijving van scenario | Experience Cloud-toepassingen |
|---|---|---|
| Exploratiegegevens | <ul><li>Detecteren van signalen, volledigheid, juistheid van gegevens</li><li>Ontdek nieuwe inzichten met gebruik van het hulpmiddel van de wetenschap van gegevens</li></ul> | <ul><li>Experience Platform Intelligence</li></ul> |
| Profielverrijking met AI/ML<br> - batch | <ul><li>Ontdek, auteur, treer, stel, score, en operationeel modellen op.</li><li>Push model prediction to profile or to data Lake for batch-based activation.</li></ul> | <ul><li>Experience Platform Intelligence</li></ul> |

## Architectuur

<img src="assets/datascience.svg" alt="Referentiearchitectuur voor de Custom Data Science for Profile Enrichment Blueprint" style="border:1px solid #4a4a4a" />

## Implementatiestappen

1. Creeer schema&#39;s en datasets.
1. Gegevens opnemen in Experience Platform.
1. Maak een DSW-laptop.
1. Kies een taal. Python en PySpark worden ondersteund.
1. Auteurmodel in laptop.
1. Teken het model.
1. Score het model om voorspellingen met de doelgegevens te produceren.
1. Schakel de gegevensset met modelresultaten voor het profiel in als u de resultaten van het model wilt doorsturen naar het realtime profiel van de klant.

## Verwante documentatie

* [Productbeschrijving Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Documentatie over wetenschapswerkruimte](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [Zelfstudies over de werkruimte voor gegevenswetenschap](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## Verwante blogberichten

* [Het vereenvoudigen van de Levenscyclus van de Wetenschap van Gegevens met de Ervaring van het Platform van Adobe](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [AI voor inhoud en handel: Pas uw interactie met klanten aan via Content Intelligence](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Het verkrijgen van een diepere Begrip van Kurn Gebruikend de Werkruimte van de Wetenschap van Gegevens](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [Data Science in Adobe Experience Platform begrijpen](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [Een kennismaking met de Verkennende Analyse van Gegevens over Adobe Experience Platform](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [Door Adobe Experience Products heen te gaan met de computer die leert tot een verbeterde gebruikerservaring](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [XDM-gegevens modelleren voor gegevenswetenschap op schaal op Adobe Experience Platform](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [Segmentation.AI: Geautomatiseerd publiek-zich-als-a-Dienst in Adobe Experience Platform](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [Jupyter-laptops verfraaien voor bedrijven](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [Intelligente inzichten versnellen met de Adobe Experience Platform Data Science Workspace](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [Een voorvertoning van tijdreeksprognoses met Adobe Experience Platform](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [Door Adobe Experience Products heen te gaan met de computer die leert tot een verbeterde gebruikerservaring](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)


