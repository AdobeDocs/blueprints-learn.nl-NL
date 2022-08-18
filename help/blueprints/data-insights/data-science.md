---
title: Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking
description: Deze blauwdruk toont hoe de op gegevenswetenschap gebaseerde inzichten in Experience Platform kunnen worden opgenomen om het Profiel van de Klant in real time te verrijken.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 6d44401fba8cc75402d4303825e32e7948753449
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 0%

---

# Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking

De Wetenschap van de Gegevens van de douane voor de Blauwdruk van de Verrijking van het Profiel illustreert hoe de gegevens kunnen worden gebruikt om, modellen op te leiden en te scoren om machine het leren inzicht in Experience Platform en de Real-time Customer Data Platform van gegevenswetenschappen en machine het leren hulpmiddelen te verstrekken. De gemodelleerde inzichten kunnen in Experience Platform worden opgenomen om het klantenprofiel in real time te verrijken. Voorbeelden van leerinzicht in machines zijn levenslange waardeschaling, product- en categoriaffiniteit, conversiesnelheid of churn.

## Gevallen gebruiken

* Haal inzicht uit en ontdek patronen van klantengegevens, trein en score modellen van deze gegevens.
* Verrijken de [!UICONTROL Klantprofiel in realtime] met modelgestuurde inzichten en kenmerken voor meer korrelige personalisatie en geoptimaliseerde reizen.
* Train- en Score-modellen om de inzichten van klanten te bepalen, zoals de levenslange waarde van de klant, de neiging om te converteren of te klonen, de affiniteit van producten en inhoud, en servicescore.

## Architectuur

<img src="assets/data_science.svg" alt="Referentiearchitectuur voor de Custom Data Science for Profile Enrichment Blueprint" style="width:90%; border:1px solid #4a4a4a" />

## Implementatiestappen

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden ingevoerd.
1. [Gegevens samenvoegen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.

Voor modelresultaten die in het Profiel van de Klant in real time moeten worden opgenomen ben zeker om het volgende te doen alvorens gegevens in te voeren:

1. [De juiste identiteiten en naamruimten configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) op het schema om ervoor te zorgen dat ingesloten gegevens in een verenigd profiel kunnen vastmaken.
1. [De schema&#39;s en datasets voor profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).

## Overwegingen bij de implementatie

* In de meeste gevallen moet het modelresultaat worden opgenomen als profielkenmerken en hoeven er geen gebeurtenissen te worden ervaren. De modelresultaten kunnen eenvoudige kenmerktekenreeksen zijn. Als er meerdere modelresultaten zijn die moeten worden opgenomen, wordt aanbevolen een array- of kaarttekstveld te gebruiken.
* De gegevensset met momentopnamen voor dagelijkse profielen, die een dagelijkse export is van de gegevens van de verenigde profielkenmerken, kan worden gebruikt om modellen voor profielkenmerkgegevens op te leiden. De document van de de momentopnamesdataset van het profiel kan worden betreden [hier](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html#profile-attribute-datasets).
* Voor het extraheren van gegevens uit Experience Platform kunnen de volgende methoden worden gebruikt
   * SDK voor gegevenstoegang
      * Gegevens worden opgeslagen in Raw-bestandsformulier
      * De gebeurtenisgegevens van de profielervaring blijven in onverenigde onbewerkte toestand staan.
   * RTCDP-doelen
      * Profielkenmerken en segmentlidmaatschap kunnen worden ingedrukt.

## Verwante documentatie

* [Productbeschrijving Adobe Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe Experience Platform Query Service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html)

## Verwante blogberichten

* [[!DNL Content and Commerce AI: Personalizing Your Interactions with Customers Through Content Intelligence]](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [[!DNL An Introductory Look at Exploratory Data Analysis on Adobe Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [[!DNL Cutting Across Adobe Experience Products with Machine Learning to Elevated User Experience]](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [[!DNL Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)