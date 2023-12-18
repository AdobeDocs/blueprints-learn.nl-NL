---
title: Experience Platform- en toepassingsinstructies
description: In de handleidingen worden de prestatieverwachtingen en de gevolgen voor de componenten en services in Adobe Experience Platform en Applications gedefinieerd
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 5a4827244b7d8414b1f1a0bf9b3cd8308bde8c60
workflow-type: tm+mt
source-wordcount: '630'
ht-degree: 0%

---

# Guardrails

Hulplijnen zijn aanbevolen drempelwaarden voor het gebruik van gegevens, waargenomen vertragingen en systemen in Adobe Experience Platform en toepassingen. De gidsen weerspiegelen systeembeperkingen en prestatiesverwachtingen om klantenarchitectuur te optimaliseren en caseprestaties te gebruiken, en helpen fouten of onverwachte resultaten te vermijden. Guardrails zijn niet bedoeld als serviceniveau-overeenkomsten, serviceniveau-overeenkomsten worden gedocumenteerd in de productbeschrijvingen die hieronder en in de licentieovereenkomsten voor klanten zijn gekoppeld. De gidsen zijn bedoeld om begeleiding in het ontwerpen van oplossingen voor specifieke klantengebruiksgevallen te verstrekken om stabiliteit en uitvoering te verzekeren.

Voor informatie over specifieke overeenkomsten van het de dienstniveau voor toepassingen en eigenschappen, verwijs naar [Beschrijvingen van toepassingen en functies](#application-feature-descriptions) onder aan deze pagina.

Merk op dat voor om het even welk geval van het klantengebruik dat strikte latentie of volumevereisten heeft, de Adobe adviseert uw gebruiksgeval in detail met uw Team van de Rekening van de Adobe en partner van de Implementatie te herzien. In bepaalde gevallen is het aan te raden een bepaalde gebruikscase-implementatie te testen en in acht te nemen voordat de gebruikszaak wordt gestart, om het verwachte gedrag te observeren en te begrijpen - aangezien elke implementatie van de klant verschillende factoren te zien heeft, waaronder de aard en de cadentie van gegevensopname, de specifieke kenmerken van de gesegmenteerde regels die worden gebouwd en de verschillende activeringsuitdagingen en nuttige lasten - elke implementatie van het gebruiksgeval zal verschillende waargenomen prestaties hebben. Als zodanig is het het beste om de verwachte prestaties vooraf te bepalen en te testen om correcte architectuur en implementatie overeenkomstig de latentie en prestatiesvereisten van het gebruiksgeval te verzekeren.


## Referentiedocumentatie voor instructies voor Adobe Experience Platform en toepassingen

De volgende pagina&#39;s bevatten informatie over hulplijnen voor Adobe Experience Platform-functies, -services en -toepassingen:

**Experience Platforms**

* [Overzicht van Real-Time CDP-instructies](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [Customer Journey Analytics, begeleiding voor publiek delen](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [Customer Journey Analytics data-opname guardrails](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [Journey Optimizer guardrails](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**Experience Platform**

* [Gegevens-innamegardrails](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [Edge Network API-handleidingen](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [Klantprofiel en segmentatiehandleidingen in realtime](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [Identiteitsinstructies](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=en)
* [Query Service-handleidingen](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en)
* [Guardrails voor doelactivering](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html)

## Diagrammen met latentie van begin tot eind {#end-to-end-latency}

### Gegevensinvoer {#data-ingestion}

In het onderstaande diagram worden de verwachte waarden voor de inlaatlatentie van gegevens weergegeven via [streaming opname](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) en [batch-inname](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=en) bij het invoeren van gegevens in Real-Time CDP. Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![Het visuele overzicht op hoog niveau van de gegevensinvoer.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg "Gegevens op hoog niveau - visueel overzicht en latentiewaarden"){width="1000" zoomable="yes"}

### Segmentering {#segmentation}

In het onderstaande diagram worden de verwachte latentiewaarden weergegeven wanneer u met het publiek werkt in het dialoogvenster [Real-Time CDP-segmenteringsservice](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![Een visueel overzicht op hoog niveau van segmentatie.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg "Zichtbare overzicht en latentiewaarden op hoog niveau segmenteren"){width="1000" zoomable="yes"}

### Real-time Customer Data Platform en Adobe Target {#adobe-target-latency}

In het onderstaande diagram worden de verwachte latentiewaarden weergegeven bij het exporteren van soorten publiek van Real-Time CDP naar [Adobe Target](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![Exporteren naar Adobe Target - visueel overzicht op hoog niveau.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Target_guardrails.svg "Soorten publiek exporteren naar Adobe Target, visueel overzicht op hoog niveau en latentiewaarden"){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

In het onderstaande diagram worden de verwachte latentiewaarden weergegeven wanneer u werkt met [Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![Werken met Customer Journey Analytics op hoog niveau, visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg "Werken met visuele overzichtswaarden en latentiewaarden op hoog niveau voor Customers Journey Analytics"){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

In het onderstaande diagram worden de verwachte latentiewaarden weergegeven wanneer u werkt met [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![Werken met Adobe Journey Optimizer-visueel overzicht op hoog niveau.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg "Werken met Adobe Journey Optimizer-waarden voor visueel overzicht en wachttijd op hoog niveau"){width="1000" zoomable="yes"}

## Beschrijvingen van toepassingen en functies {#application-feature-descriptions}

Voor informatie over eigenschap-specifieke overeenkomsten van het de dienstniveau, verwijs naar de productbeschrijvingen hieronder:

* [Experience Platform Collection Enterprise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-collection-enterprise.html)
* [Real-time Customer Data Platform](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [B2B-klantgegevensplatform](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-b2b.html)
* [Experience Platform activeren](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [Experience Platform Intelligence](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Intelligente services](https://helpx.adobe.com/legal/product-descriptions/intelligent-services.html)
* [Data Distiller](https://helpx.adobe.com/legal/product-descriptions/data-distiller.html)
* [Customer Journey Analytics](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Journey Optimizer](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Journey Orchestration](https://helpx.adobe.com/legal/product-descriptions/journey-orchestration.html)
* [Offer decisioning](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
