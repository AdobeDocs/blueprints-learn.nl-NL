---
title: Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking
description: Deze blauwdruk laat zien hoe de Werkruimte van de Wetenschap van Gegevens van Adobe Experience Platform gegevens binnen Experience Platform kan gebruiken om, modellen op te leiden, op te stellen en te scoren om machine het leren inzichten van de gegevens te verstrekken.
solution: Experience Platform,Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: f323d2deee5547abd0ccc8247a23ac7a144b2f07
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking

De Wetenschap van de Gegevens van de douane voor de Blauwdruk van de Verrijking van het Profiel illustreert hoe de gegevens in Adobe Experience Platform kunnen worden gebruikt in [!UICONTROL Werkruimte voor gegevenswetenschap] om modellen op te leiden, te implementeren en te scoren om computerleerinzicht te bieden. Deze modellen kunnen direct output aan een dataset voor [!UICONTROL Klantprofiel in realtime] om klantprofielen verder te verrijken. Deze inzichten kunnen dan worden gebruikt voor personalisatie. Voorbeelden van leerinzicht in machines zijn levenslange waardeschaling, product- en categoriaffiniteit, conversiesnelheid of churn.

## Gevallen gebruiken

* Haal inzicht uit en ontdek patronen van klantengegevens in Experience Platform. Train- en scoremodellen van deze gegevens.
* Verrijken de [!UICONTROL Klantprofiel in realtime] met modelgestuurde inzichten en kenmerken voor meer korrelige personalisatie en geoptimaliseerde reizen.
* Train- en Score-modellen om de inzichten van klanten te bepalen, zoals de levenslange waarde van de klant, de neiging om te converteren of te klonen, de affiniteit van producten en inhoud, en servicescore.

## Architectuur

<img src="assets/data_science.svg" alt="Referentiearchitectuur voor de Custom Data Science for Profile Enrichment Blueprint" style="width:80%; border:1px solid #4a4a4a" />

## Implementatiestappen

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden ingevoerd.
1. [Gegevens samenvoegen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. [Een DSW-laptop maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/load-data-in-jupyterlab-notebooks.html?lang=en).
1. Kies een taal. Python en PySpark worden ondersteund.
1. [Auteursmodel](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/recipe-builder-template.html?lang=en) in laptop.
1. [Het model trainen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/schedule-training-scoring.html?lang=en).
1. [Score van het model](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/schedule-training-scoring.html?lang=en) om voorspellingen met de doelgegevens te produceren.
1. [Schakel de gegevensset met modelresultaten voor het profiel in als u de resultaten van het model naar het [!UICONTROL Klantprofiel in realtime]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/dsw-profile-segmentation.html?lang=en).

## Verwante documentatie

* [Productbeschrijving Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [[!UICONTROL Werkruimte voor gegevenswetenschap] documentatie](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en)
* [[!UICONTROL Werkruimte voor gegevenswetenschap] zelfstudies](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-science-workspace/understanding-data-science-workspace.html)

## Verwante blogberichten

* [[!DNL Simplifying the Data Science Lifecycle with Adobe Platform Experience]](https://medium.com/adobetech/simplifying-the-data-science-lifecycle-with-adobe-platform-experience-8ea4f056d82f)
* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL Gaining a Deeper Understanding of Churn Using Data Science Workspace]](https://medium.com/adobetech/gaining-a-deeper-understanding-of-churn-using-data-science-workspace-18a2190e0cf3)
* [[!DNL Understanding Data Science In Adobe Experience Platform]](https://medium.com/adobetech/understanding-data-science-in-adobe-experience-platform-5bce5a17b42)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Modeling XDM Data for Data Science at Scale on Adobe Experience Platform]](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)
* [[!DNL Reimagining Jupyter Notebooks for Enterprise Scale]](https://medium.com/adobetech/reimagining-jupyter-notebooks-for-enterprise-scale-8bc6340d504a)
* [[!DNL Accelerate Intelligent Insights with Adobe Experience Platform Data Science Workspace]](https://medium.com/adobetech/accelerate-intelligent-insights-with-adobe-experience-platform-data-science-workspace-89538bacbbea)
* [[!DNL A Preview of Time Series Forecasting with Adobe Experience Platform]](https://medium.com/adobetech/preview-of-time-series-forecasting-with-adobe-experience-platform-38a2fc778e89)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
