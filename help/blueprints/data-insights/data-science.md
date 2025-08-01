---
title: Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking
description: Leer hoe de op wetenschap-gebaseerde inzichten van gegevens in  [!DNL Experience Platform]  kunnen worden opgenomen om het Profiel van de Klant in real time te verrijken.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 1%

---

# Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking

De aangepaste gegevenswetenschap voor profielverrijkingsblauwdruk laat zien hoe gegevens kunnen worden gebruikt voor het trainen, implementeren en scoren van modellen voor machinaal leren van inzicht in [!DNL Experience Platform] en de [!DNL Real-Time Customer Data Platform] van gereedschappen voor gegevenswetenschap en machinaal leren.

Modelleerde inzichten kunnen in [!DNL Experience Platform] worden opgenomen om het realtime profiel van de klant te verrijken. Voorbeelden van leerinzicht in machines zijn levenslange waardeschaling, product- en categoriaffiniteit, conversiesnelheid of churn.

## Gebruiksscenario&#39;s

* Pak insight uit en ontdek patronen uit klantgegevens, trein- en scoremodellen van deze gegevens.
* Verrijk het [!UICONTROL &#x200B; Real-time Profiel van de Klant &#x200B;] met model gedreven inzichten en attributen voor meer korrelige verpersoonlijking en geoptimaliseerde reizen.
* Train- en Score-modellen om de inzichten van klanten te bepalen, zoals de levenslange waarde van de klant, de neiging om te converteren of te klonen, de affiniteit van producten en inhoud, en servicescore.

## Architectuur

<img src="assets/data_science.svg" alt="Referentiearchitectuur voor de Custom Data Science for Profile Enrichment Blueprint" style="width:90%; border:1px solid #4a4a4a" />

## Beveiligingsmechanismen

* Voor gedetailleerde gidsen en eind om latentie te beëindigen bij het opnemen van de resultaten van de gegevenswetenschap in [!DNL Experience Platform] en het Profiel van de Klant In real time verwijst het Profiel van de Klant naar de gidsen van de gegevensopname en het latentieschema dat in het [ document van de plaatsingsgidsen ](../experience-platform/guardrails.md) van verwijzingen wordt voorzien.

## Implementatieoverwegingen

* In de meeste gevallen moet het modelresultaat worden opgenomen als profielkenmerken en hoeven er geen gebeurtenissen te worden ervaren. De modelresultaten kunnen eenvoudige kenmerktekenreeksen zijn. Als er meerdere modelresultaten zijn die moeten worden opgenomen, is het raadzaam een array- of kaarttekstveld te gebruiken.
* De gegevensset met momentopnamen voor dagelijkse profielen, die een dagelijkse export is van de gegevens van de verenigde profielkenmerken, kan worden gebruikt om modellen voor profielkenmerkgegevens op te leiden. De document van de momentopnamesdataset van het profiel kan [ hier ](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html#profile-attribute-datasets) worden betreden.

## Gerelateerde documentatie

* [ Adobe  [!DNL Experience Platform]  het productbeschrijving van de Intelligentie ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [ de Dienst van de Vraag van Adobe  [!DNL Experience Platform]  ](https://experienceleague.adobe.com/docs/experience-platform/query/home.html)

## Gerelateerde blogberichten

* [ Inhoud en Commerce AI: Het personaliseren van Uw Interacties met Klanten door Inhoudsintelligentie ](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [ Een Inleiding bekijkt de Verkennende Analyse van Gegevens op Adobe  [!DNL Experience Platform] ](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [ Het snijden over de Ervaring van Adobe Producten met het Leren van de Machine aan Verhoogde Ervaring van de Gebruiker ](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [ Segmentation.AI: Geautomatiseerd publiek-Groeperend-a-Dienst in Adobe  [!DNL Experience Platform] ](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)