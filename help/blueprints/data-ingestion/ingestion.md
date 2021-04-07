---
title: Voorbereiding van gegevens en vervagingsblauwdruk
description: Deze blauwdruk toont alle methodes waardoor de gegevens in Adobe Experience Platform kunnen worden opgenomen en worden voorbereid.
solution: Experience Platform,Data Collection
kt: 7204
thumbnail: null
exl-id: 21f8a73e-6be7-448e-8cd3-ebee9fc848e1,5c3c94b6-c928-4d93-8b38-f8bd2aad2e68
translation-type: tm+mt
source-git-commit: 77ddc003d4328074ad269de5837a02f5e6d6add5
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---

# Voorbereiding van gegevens en vervagingsblauwdruk

Gegevensvoorbereiding en congestieblauwdruk omvatten alle methoden waarmee gegevens in Adobe Experience Platform kunnen worden voorbereid en opgenomen.

De voorbereiding van gegevens omvat de kaartbrongegevens aan het schema van het Model van Gegevens van de Ervaring (XDM). Het omvat ook het uitvoeren van transformaties op gegevens, waaronder datumopmaak, veldsplitsen/samenvoegen/conversies en het samenvoegen/samenvoegen/opnieuw koppelen van records. De voorbereiding van gegevens helpt klantengegevens verenigen om bijeengevoegde/gefilterde analyse te verstrekken, met inbegrip van het melden van of het voorbereiden van gegevens voor de assemblage van het klantenprofiel/gegevenswetenschap/activering.

## Architectuur

<img src="assets/dataingest.svg" alt="Referentiearchitectuur voor de blauwdruk voor gegevensvoorbereiding en insluiting" style="border:1px solid #4a4a4a" />

## Methoden voor gegevensinname

| Methoden van inname | Beschrijving |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Web/Mobile SDK | Latentie:<ul><li>In real time - de zelfde paginainzameling aan het Netwerk van de Rand</li><li>Streaming opname naar profiel ~1 minuut</li><li>Streaming opname naar data Lake (microbatch ~15 minuten)</ul>Documentatie: <ul><li>[Web SDK](https://experienceleague.corp.adobe.com/docs/web-sdk.html)</li><li>[Mobile SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en)</li></ul> |
| Streaming bronnen | Latentie:<ul><li>In real time - de zelfde paginainzameling aan het Netwerk van de Rand</li><li>Streaming opname naar profiel ~1 minuut</li><li>Streaming opname naar data Lake (microbatch ~15 minuten)</li></ul>[Documentatie](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors) |
| Streaming-API | Latentie:<ul><li>In real time - de zelfde paginainzameling aan het Netwerk van de Rand</li><li>Streaming opname naar profiel ~1 minuut</li><li>Streaming opname naar data Lake (microbatch ~15 minuten)</li><li>7 GB/uur</li></ul>[Documentatie](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=en#what-can-you-do-with-streaming-ingestion%3F) |
| ETL Tooling | Gebruik de hulpmiddelen van ETL om ondernemingsgegevens te wijzigen en om te zetten alvorens in Experience Platform in te gaan.<br><br>Latentie:<ul><li>De timing is afhankelijk van de externe planning van ETL-gereedschappen, en de standaardinstructies voor inname zijn van toepassing op basis van de gebruikte methode voor inname.</li></ul> |
| Batchbronnen | Gepland ophalen van bronnen<br>Latentie: ~ 200 GB/uur<br><br>[Documentatie](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=en#connectors)<br>[Video-Tutorials](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/overview.html) |
| Batch-API | Latentie:<ul><li>Batchopname in profiel afhankelijk van grootte en verkeersbelasting ~45 minuten</li><li>Batchopname in het datumpigment afhankelijk van grootte en verkeersbelasting</li></ul>[Documentatie](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/overview.html?lang=en#batch) |
| Adobe Application Connectors | Automatisch gegevens opnemen die afkomstig zijn van Adobe Experience Cloud-toepassingen<ul><li>Adobe Analytics: [Documentatie](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en#connectors) en [Videozelfstudie](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-adobe-analytics.html)</li><li>Audience Manager: [Documentatie](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en#connectors) en [Videozelfstudie](https://experienceleague.adobe.com/docs/platform-learn/tutorials/sources/ingest-data-from-aam.html)</li></ul> |


## Methoden voor het voorbereiden van gegevens

| Methoden voor het voorbereiden van gegevens | Beschrijving |
|------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Werkruimte voor gegevenswetenschap - Data Prep | Transformatie met behulp van model, transformatie met scripts.<br>[Documentatie](https://experienceleague.adobe.com/docs/experience-platform/data-science-workspace/home.html?lang=en) |
>[!NOTE]
>
>| Extern ETL-gereedschap ([!DNL Snaplogic], [!DNL Mulesoft], [!DNL Informatica] enzovoort) | Complexe transformaties uitvoeren in ETL-gereedschappen en standaard-API&#39;s of -connectors voor het Experience Platform gebruiken om de resulterende gegevens in te voeren.                                                                                                                                                               |

| Query-service - Data Prep                                  | Sluit zich aan bij, Splits, de gegevens van de Fusie, van de Transformatie, van de Vraag, en van de Filter in een nieuwe dataset. Tabel maken als selectie gebruiken (CTAS) <br>[Documentatie](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en#sql)                                                                       |
| XDM Mapper- en Data Prep-functies (streaming en batch)     | Bronkenmerken in CSV- of JSON-indeling toewijzen aan XDM-kenmerken tijdens het opnemen van het Experience Platform.<br>rekenfuncties op gegevens terwijl deze worden ingevoerd; dat wil zeggen, gegevens opmaken, splitsen, samenvoegen, enzovoort.<br>[Documentatie](https://experienceleague.adobe.com/docs/experience-platform/data-prep/home.html?lang=en) |

## Verwante blogberichten

* [De hefboomwerking van de Platforms van Externe Gegevens in de Journey Orchestration van Adobe Experience Platform](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17?source=your_stories_page-------------------------------------)
* [Hoge doorvoerinname met Iceberg](https://medium.com/adobetech/high-throughput-ingestion-with-iceberg-ccf7877a413f?source=your_stories_page-------------------------------------)
* [De Tricks van de Dienst van de vraag in Adobe Experience Platform (het schrijven van Vragen en het Opslaan van Voortgekomen Datasets)](https://medium.com/adobetech/query-service-tricks-in-adobe-experience-platform-writing-queries-and-storing-derived-datasets-eaee0d6d683e?source=your_stories_page-------------------------------------)
* [Het graven in het Model van de Gegevens van de Ervaring van Adobe Experience Platform om de Macht van het Profiel van de Klant in real time volledig te begrijpen](https://medium.com/adobetech/digging-into-adobe-experience-platforms-experience-data-model-to-more-fully-understand-the-power-3e109271e04f?source=your_stories_page-------------------------------------)
* [Een kennismaking met de Verkennende Analyse van Gegevens over Adobe Experience Platform](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a?source=your_stories_page-------------------------------------)
* [XDM-gegevens modelleren voor gegevenswetenschap op schaal op Adobe Experience Platform](https://medium.com/adobetech/modeling-xdm-data-for-data-science-at-scale-on-adobe-experience-platform-222bb2a6dbf7?source=your_stories_page-------------------------------------)
