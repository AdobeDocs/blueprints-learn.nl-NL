---
title: Experience Platform- en toepassingsinstructies
description: In de handleidingen worden de prestatieverwachtingen en de gevolgen voor de componenten en services in Adobe Experience Platform en Applications gedefinieerd
solution: Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 164793e15315d64cf38cb14928eac10cf6ae5c35
workflow-type: tm+mt
source-wordcount: '680'
ht-degree: 1%

---

# Beveiligingsmechanismen

Hulplijnen zijn aanbevolen drempelwaarden voor het gebruik van gegevens, waargenomen vertragingen en systemen in Adobe Experience Platform en toepassingen. De gidsen weerspiegelen systeembeperkingen en prestatiesverwachtingen om klantenarchitectuur te optimaliseren en caseprestaties te gebruiken, en helpen fouten of onverwachte resultaten te vermijden. Guardrails zijn niet bedoeld als serviceniveau-overeenkomsten, serviceniveau-overeenkomsten worden gedocumenteerd in de productbeschrijvingen die hieronder en in de licentieovereenkomsten voor klanten zijn gekoppeld. De gidsen zijn bedoeld om begeleiding in het ontwerpen van oplossingen voor specifieke klantengebruiksgevallen te verstrekken om stabiliteit en uitvoering te verzekeren.

Voor informatie over de specifieke overeenkomsten van het de dienstniveau voor toepassingen en eigenschappen, verwijs naar de [ toepassing en eigenschapbeschrijvingen ](#application-feature-descriptions) sectie bij de bodem van deze pagina.

Merk op dat voor om het even welk geval van het klantengebruik dat strikte latentie of volumevereisten heeft, de Adobe adviseert uw gebruiksgeval in detail met uw Team van de Rekening van de Adobe en partner van de Implementatie te herzien. In bepaalde gevallen is het raadzaam een bepaalde gebruikscase-implementatie te testen en in acht te nemen voordat de gebruikszaak wordt gestart om het verwachte gedrag te observeren en te begrijpen - aangezien elke implementatie van de klant verschillende factoren heeft, waaronder de aard en de snelheid van de gegevensopname, de specifieke kenmerken van de segmentregels die worden gebouwd en de verschillende activeringskanalen en nuttige lasten - elke implementatie van de gebruikscase zal verschillende waargenomen prestaties hebben. Als zodanig is het het beste om de verwachte prestaties vooraf te bepalen en te testen om correcte architectuur en implementatie overeenkomstig de latentie en prestatiesvereisten van het gebruiksgeval te verzekeren.


## Referentiedocumentatie voor instructies voor Adobe Experience Platform en toepassingen

De volgende pagina&#39;s bevatten informatie over hulplijnen voor Adobe Experience Platform-functies, -services en -toepassingen:

**toepassingen van het Experience Platform**

* [ Real-Time CDP guardrails overzicht ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html)
* [ het publiek dat van de Customer Journey Analytics guardrails deelt ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html#latency)
* [ de guardrails van de gegevensopname van de Customer Journey Analytics ](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [ de guardrails van Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html)

**de diensten van het Experience Platform**

* [ de guardrails van de Inname van Gegevens ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html)
* [[!DNL Edge Network]  API Guardrails ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* [ Realtime Gidsen van het Profiel en van de Segmentatie van de Klant ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [ De Grafieken van de Identiteit ](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=en)
* [ Guardrails van de Dienst van de Vraag ](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en)
* [ Guardrails van de Activering van de Bestemming ](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html)

## Diagrammen met latentie van begin tot eind {#end-to-end-latency}

### Experience Platform Edge Network en Hub Primaire Waargenomen Latenties {#edge-hub-latencies}

Het volgende diagram toont de primaire rand en de hub waargenomen latentie om zich van bewust te zijn wanneer het architect gebruiksgeval op het Experience Platform en de Toepassingen.

![ Experience Platform [!DNL Edge Network] en hub primaire waargenomen latentie.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg " Edge Network van het Experience Platform en hub primaire waargenomen latentie "){width="1000" zoomable="yes"}

### Gegevensinvoer {#data-ingestion}

Het diagram hieronder toont verwachte waarden van de de latentie van de gegevensopname door [ het stromen ingeslikken ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html) en [ partij ingeslikt ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=en) wanneer het brengen van gegevens in Real-Time CDP. Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ de Inname van Gegevens high-level visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg " het Inslikken van Gegevens high-level visuele overzicht en latentiewaarden "){width="1000" zoomable="yes"}

### Segmentatie {#segmentation}

Het diagram hieronder toont verwachte latentiewaarden wanneer het werken met publiek in de [ de segmentatiedienst van Real-Time CDP ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ Van de segmentatie hoog-vlakke visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg " de visuele overzicht en latentiewaarden van de Segmentatie op hoog niveau "){width="1000" zoomable="yes"}

### Real-time Customer Data Platform &amp; [!DNL Edge Network] {#adobe-edge-latency}

Het diagram hieronder toont verwachte latentiewaarden wanneer het leveraging van [!DNL Edge Network] - bijvoorbeeld aan hefboomwerkingRTCDP publiek in [ Adobe Target ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ het Netwerk en Experience Platform van Adobe Edge high-level visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg " Exporterend publiek naar Adobe Target high-level visueel overzicht en latentie "){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

Het diagram toont hieronder verwachte latentiewaarden wanneer het werken met [ Customer Journey Analytics ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=en). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ Werkend met Customer Journey Analytics hoog-vlakke visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg " Werkend met Customer Journey Analytics hoog-vlakke visuele overzicht en latentiewaarden "){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

Het diagram toont hieronder verwachte latentiewaarden wanneer het werken met [ Adobe Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=en). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ het Werken met Adobe Journey Optimizer high-level visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg " Werkend met Adobe Journey Optimizer hoog-vlakke visuele overzicht en latentiewaarden "){width="1000" zoomable="yes"}

## Beschrijvingen van toepassingen en functies {#application-feature-descriptions}

Voor informatie over eigenschap-specifieke overeenkomsten van het de dienstniveau, verwijs naar de productbeschrijvingen hieronder:

* [ de Onderneming van de Inzameling van het Experience Platform ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-collection-enterprise.html)
* [ Real-time Customer Data Platform ](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [ B2B het Platform van Gegevens van de Klant ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-b2b.html)
* [ Activering van het Experience Platform ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [ Intelligentie van het Experience Platform ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [ Intelligente Diensten ](https://helpx.adobe.com/legal/product-descriptions/intelligent-services.html)
* [ Gegevens Distiller ](https://helpx.adobe.com/legal/product-descriptions/data-distiller.html)
* [ Customer Journey Analytics ](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [ Journey Optimizer ](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [ Journey Orchestration ](https://helpx.adobe.com/legal/product-descriptions/journey-orchestration.html)
* [ Offer decisioning ](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
