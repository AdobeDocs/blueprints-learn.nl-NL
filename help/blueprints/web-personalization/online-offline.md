---
title: Online/offline webpersonalisatie-scenario
description: Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
translation-type: tm+mt
source-git-commit: 9b6c220a515c5abae22b58fe33558d7d2fed375d
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---



# Online/offline webpersonalisatie-scenario

Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.

## Gevallen gebruiken

* Optimalisatie landingspagina
* Gedrag en offlineprofiel activeren
* Personalisatie op basis van eerdere product/inhoud-weergaven, product/inhoud-affiniteit, milieukenmerken, publieksgegevens van derden en demografie, naast offlineinzichten zoals transacties, loyaliteit- en CRM-gegevens, en gemodelleerde inzichten

## Toepassingen

* Real-time Platform voor klantgegevens
* Adobe Target
* Adobe Audience Manager (optioneel): Hiermee voegt u publieksgegevens van derden, apparaatgrafieken die op meerdere pagina&#39;s zijn gebaseerd, de mogelijkheid om segmenten van Platforms in Adobe Analytics te laten doorlopen en de mogelijkheid om Adobe Analytics-segmenten in het Platform te laten doorlopen toe
* Adobe Analytics (optioneel): Hiermee kunt u segmenten samenstellen op basis van historische gedragsgegevens en fijnkorrelige segmentatie van Adobe Analytics-gegevens

## Architectuur

<img src="assets/onoff.svg" alt="De architectuur van de verwijzing voor het Online/Offline scenario van de Personalisatie van het Web" style="border:1px solid #4a4a4a" />

## Guardrails

* De segmenten die van Experience Platform aan Audience Manager worden gedeeld worden gedeeld binnen notulen van segmentverwezenlijking - of via het stromen of partijevaluatie methode. Er is een eerste synchronisatie van de segmentconfiguratie tussen AEP en AAM van ~4 uur voordat het lidmaatschap van het AEP-segment in AAM profielen wordt gerealiseerd. Eenmaal in de AAM zijn de AEP-segmentabonnementen beschikbaar voor dezelfde paginagrootte via Adobe Target.
* Merk op dat voor segmentrealisaties die binnen de synchronisatie van de 4 uurssegmentconfiguratie tussen AEP en AAM voorkomen, deze segmentrealisaties in AAM op de verdere baan van het partijsegment als &quot;bestaande&quot;segmenten zullen worden gerealiseerd.
* Delen van batchsegmenten vanuit AEP - eenmaal per dag of handmatig gestart via API. Zodra deze segmentlidmaatschappen worden gerealiseerd worden zij gedeeld aan AAM binnen notulen en beschikbaar voor zelfde/volgende paginagrootte in Doel.
* Streaming segmentatie wordt uitgevoerd binnen ~ p95 5min. Zodra deze segmentrealisaties voorkomen, worden zij gedeeld aan AAM binnen notulen en beschikbaar voor zelfde/volgende paginagrootte in Doel.
* Door gebrek laat de segment delende dienst een maximum van 75 publiek toe om voor elke het rapportreeks van Adobe Analytics worden gedeeld. Als de klant een licentie voor Audience Managers heeft, geldt er geen limiet voor het aantal soorten publiek dat kan worden gedeeld tussen Adobe Analytics en Adobe Target of Audience Manager en Adobe Target.

## Implementatievereisten

| Toepassing/service | Vereiste bibliotheek | Notities |
|---|---|---|
| Adobe Target | Platform Web SDK*, at.js 0.9.1+, of mbox.js 61+ | at.js heeft de voorkeur omdat mbox.js niet meer wordt ontwikkeld. |
| Adobe Audience Manager (optioneel) | Platform Web SDK* of dil.js 5.0+ |  |
| Adobe Analytics (optioneel) | Platform Web SDK* of AppMeasurement.js 1.6.4+ | Bij het bijhouden van Adobe Analytics moet gebruik worden gemaakt van regionale gegevensverzameling (Regional Data Collection, RDC). |
| Experience Cloud ID-service | Platform Web SDK* of VisitorAPI.js 2.0+ | (Aanbevolen) Gebruik Experience Platform Launch om de dienst van identiteitskaart op te stellen om ervoor te zorgen dat identiteitskaart vóór om het even welke toepassingsvraag wordt geplaatst |
| Experience Platform Mobile SDK (optioneel) | 4.11 of hoger voor iOS en Android™ |  |
| Experience Platform Web SDK | 1.0, heeft de huidige versie van Experience Platform SDK [verschillende gebruiksgevallen nog niet ondersteund voor de Experience Cloud toepassingen](https://github.com/adobe/alloy/projects/5) |  |


## Implementatiestappen

1. [Adobe-](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) doel implementeren voor uw web- of mobiele toepassingen
1. [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html)  implementeren (optioneel)
1. [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)   implementeren (optioneel)
1. [Experience Platform en Real-time klantprofiel implementeren](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. [Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html) of [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) implementeren
   >[!NOTE]
   >
   >Elke toepassing moet de Experience Cloud-id gebruiken en deel uitmaken van dezelfde Experience Cloud-organisatie om het delen van het publiek tussen toepassingen mogelijk te maken.
1. [Verzoek om provisioning voor het delen van publiek tussen Experience Platform en Adobe Target (gedeeld publiek)](https://www.adobe.com/go/audiences)

## Gegevensstroomdiagrammen implementeren

Het Web/Mobiele verpersoonlijkingsblauwdruk kan worden uitgevoerd gebruikend of traditionele toepassing-specifieke SDKs (bijvoorbeeld, AppMeasurement.js), of door het Web SDK/Mobile SDK van het Platform en het Netwerk van de Rand te gebruiken.

### Platform Web/Mobile SDK en Edge Approach

<img src="assets/websdkflow.svg" alt="Referentiearchitectuur voor de Web SDK/Mobile SDK van het Platform en de Benadering van het Netwerk van de Rand" style="border:1px solid #4a4a4a" />

### Toepassingsspecifieke SDK-benadering

<img src="assets/appsdkflow.png" alt="Referentiearchitectuur voor de toepassingsspecifieke SDK-benadering" style="border:1px solid #4a4a4a" />

## Verwante documentatie

* [Experience Platform segmentdelen met Audience Manager en andere Experience Cloud-oplossingen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)
* [Overzicht van segmentatie Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Streaming segmentering](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Overzicht van Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Audience Manager Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html)
* [Adobe Analytics Segment Sharing via AAM](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Experience Platform Web SDK-documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentatie Experience Cloud ID-service](https://experienceleague.adobe.com/docs/id-service/using/home.html)
* [Documentatie Experience Platform Launch](https://experienceleague.adobe.com/docs/launch/using/home.html)

## Verwante blogberichten

* [Blauwdruk voor web personalisatie met Adobe Experience Platform Real-Time klantprofiel](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [Een optimale online ervaring opbouwen: Verrijken Verenigd Profiel met de Dienst van de Vraag](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [Adobe Experience Platform-beslissingsengine integreren met AEM websites](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [Adobe Experience Platform&#39;s Identity Service — How to Solate the Customer Identity Conundrum](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [Hoe Adobe Experience Platform Predictive Audiences persoonlijke ervaringen verbetert](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [Adobe Experience Platform Web SDK voor Audience Management](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe Experience Platform Real-Time klantprofiel implementeren via ons &quot;Customer Zero&quot;-programma](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [Hoe Adobe Experience Platform Klanten kan helpen hun mobiel Overseinen in real time aan te passen met de Dienst van Journey Orchestration en een Mobiele Leverancier van het Overseinen](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [Segmentatie in seconden: Hoe Adobe Experience Platform real-time klantprofielen werkelijkheid heeft gemaakt](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [Een optimale online ervaring opbouwen: Verrijken Verenigd Profiel met de Dienst van de Vraag](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)


