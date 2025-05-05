---
title: Experience Platform- en toepassingsinstructies
description: In de handleidingen worden de prestatieverwachtingen en de gevolgen voor de componenten en services in Adobe Experience Platform en Applications gedefinieerd
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: a5d127c2a9e18ebbf25012475b9f474c07575362
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 1%

---


# Beveiligingsmechanismen

De gidsen weerspiegelen systeembeperkingen, verwachte latentie, en prestatiesverwachtingen om klantenarchitectuur te optimaliseren en case prestaties te gebruiken en de stabiliteit te verzekeren, fouten of onverwachte resultaten te vermijden.

## Typen ardrails

| Het type Guardrail | Beschrijving |
|---|---|
| Prestatiegarantie (Zachte limiet) | Prestatiegaranties zijn gebruikslimieten die betrekking hebben op het bereik van uw gebruiksgevallen en een overzicht van de verwachte prestaties onder normale omstandigheden. Als deze waarde wordt overschreden, kunnen de prestaties achteruitgaan en de latentie toenemen. De Grafieken van prestaties worden gedocumenteerd in de documenten van het Experience League onder de guardrailsecties voor elke Oplossing zoals hieronder geschetst. |
| Statische limiet (harde limiet) | Dit zijn door het systeem opgelegde beperkingen die niet mogen worden overschreden. De statische grenzen zijn typisch contractueel gebonden en geschetst in het klantencontract en de [ Beschrijvingen van het Product ](https://helpx.adobe.com/nl/legal/product-descriptions.html). |

>[!NOTE]
>
> De begeleiding is niet bedoeld om de Overeenkomsten van het Niveau van de Dienst te zijn, maar eerder begeleiding voor optimale configuraties en verwacht systeemgedrag. Alle garanties die systeem- of contractuele limieten of serviceniveau-overeenkomsten zijn, worden specifiek in de klantencontracten en productbeschrijvingen vermeld. Als u meer wilt weten over aangepaste limieten, neemt u contact op met uw medewerker van de klantenservice.

>[!NOTE]
>
> Voor gebruiksgevallen met strikte latentie of prestatiesbehoeften, stelt de Adobe voor de details met uw Team van de Rekening van de Adobe en Partner van de Implementatie te bespreken. Elke klantenopstelling kan over de patronen van de gegevensopname, profieltellingen en rijkdom, segmentregels, en activeringskanalen variëren. Daarom is het belangrijk om uw gebruiksscenario te ontwerpen en te testen om de prestaties te optimaliseren en de verwachte prestatiekenmerken volledig te begrijpen.

## Referentiedocumentatie voor instructies voor Adobe Experience Platform en toepassingen

De volgende pagina&#39;s bevatten informatie over hulplijnen voor Adobe Experience Platform-functies, -services en -toepassingen:

**toepassingen van het Experience Platform**

* [ Real-Time CDP guardrails overzicht ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html?lang=nl-NL)
* [ het publiek dat van de Customer Journey Analytics guardrails deelt ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=nl-NL#latency)
* [ de guardrails van de gegevensopname van de Customer Journey Analytics ](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=nl-NL#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [ de guardrails van Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=nl-NL)

**de diensten van het Experience Platform**

* [ de guardrails van de Inname van Gegevens ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html?lang=nl-NL)
* [[!DNL Edge Network]  API Guardrails ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html?lang=nl-NL)
* [ Realtime Gidsen van het Profiel en van de Segmentatie van de Klant ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=nl-NL)
* [ De Grafieken van de Identiteit ](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=nl-NL)
* [ Guardrails van de Dienst van de Vraag ](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=nl-NL)
* [ Guardrails van de Activering van de Bestemming ](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=nl-NL)

## Diagrammen met latentie van begin tot eind {#end-to-end-latency}

### Experience Platform Edge Network en Hub Primaire Waargenomen Latenties {#edge-hub-latencies}

Het volgende diagram toont de primaire rand en de hub waargenomen latentie om zich van bewust te zijn wanneer het architect gebruiksgeval op het Experience Platform en de Toepassingen.

![ Experience Platform [!DNL Edge Network] en hub primaire waargenomen latentie.](/help/blueprints/experience-platform/deployment/assets/aep_edge_hub_latency_v1.svg " Edge Network van het Experience Platform en hub primaire waargenomen latentie "){width="1000" zoomable="yes"}

### Gegevensinvoer {#data-ingestion}

Het diagram hieronder toont verwachte waarden van de de latentie van de gegevensopname door [ het stromen ingeslikken ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/streaming/overview.html?lang=nl-NL) en [ partij ingeslikt ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/batch/getting-started.html?lang=nl-NL) wanneer het brengen van gegevens in Real-Time CDP. Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ de Inname van Gegevens high-level visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/aep_data_flow_guardrails.svg " het Inslikken van Gegevens high-level visuele overzicht en latentiewaarden "){width="1000" zoomable="yes"}

### Segmentatie {#segmentation}

Het diagram hieronder toont verwachte latentiewaarden wanneer het werken met publiek in de [ de segmentatiedienst van Real-Time CDP ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html?lang=nl-NL). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ Van de segmentatie hoog-vlakke visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/segmentation_guardrails.svg " de visuele overzicht en latentiewaarden van de Segmentatie op hoog niveau "){width="1000" zoomable="yes"}

### Real-time Customer Data Platform &amp; [!DNL Edge Network] {#adobe-edge-latency}

Het diagram hieronder toont verwachte latentiewaarden wanneer het leveraging van [!DNL Edge Network] - bijvoorbeeld aan hefboomwerkingRTCDP publiek in [ Adobe Target ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=nl-NL). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ het Netwerk en Experience Platform van Adobe Edge high-level visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/RTCDP_Edge_guardrails.svg " Exporterend publiek naar Adobe Target high-level visueel overzicht en latentie "){width="1000" zoomable="yes"}

### Customer Journey Analytics {#customer-journey-analytics}

Het diagram toont hieronder verwachte latentiewaarden wanneer het werken met [ Customer Journey Analytics ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-overview.html?lang=nl-NL). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ Werkend met Customer Journey Analytics hoog-vlakke visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/CJA_guardrails.svg " Werkend met Customer Journey Analytics hoog-vlakke visuele overzicht en latentiewaarden "){width="1000" zoomable="yes"}

### Journey Optimizer {#journey-optimizer}

Het diagram toont hieronder verwachte latentiewaarden wanneer het werken met [ Adobe Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/get-started.html?lang=nl-NL). Klik op de afbeelding om een versie met hoge resolutie weer te geven.

![ het Werken met Adobe Journey Optimizer high-level visueel overzicht.](/help/blueprints/experience-platform/deployment/assets/AJO_guardrails.svg " Werkend met Adobe Journey Optimizer hoog-vlakke visuele overzicht en latentiewaarden "){width="1000" zoomable="yes"}