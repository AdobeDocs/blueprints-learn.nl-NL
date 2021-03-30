---
title: Het scenario van de Aanpassing van het Web van het gedrag
description: Persoonlijk maken op basis van online gedrag en publieksgegevens.
solution: Experience Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7085thumb-web-personalization-scenario1.jpg
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---


# Het scenario van de Aanpassing van het Web van het gedrag

Persoonlijk maken op basis van online gedrag en publieksgegevens.

## Gevallen gebruiken

* Optimalisatie landingspagina
* Gedragsgerichte acties
* Personalisatie op basis van eerdere productweergaven/content-weergaven, de affiniteit tussen product en inhoud, milieukenmerken, publieksgegevens van derden en demografie

## Toepassingen

* Adobe Target
* Adobe Analytics (optioneel)
* Adobe Audience Manager (optioneel)

## Architectuur

<img src="assets/personalization.svg" alt="Referentiearchitectuur voor het scenario van de Personalisatie van het Web van het Gedrag" style="border:1px solid #4a4a4a" />


## Guardrails

Door gebrek, laat de segment delende dienst een maximum van 75 publiek toe om voor elke het rapportreeks van Adobe Analytics worden gedeeld. Als de Audience Manager voor publiek het delen wordt gebruikt, is er geen grens op het aantal publiek dat kan worden gedeeld. 

## Implementatievereisten

| Toepassing/service | Vereiste bibliotheek | Notities |
|---|---|---|
| Adobe Target | Platform Web SDK*, at.js 0.9.1+, of mbox.js 61+ | at.js heeft de voorkeur omdat mbox.js niet meer wordt ontwikkeld. |
| Adobe Audience Manager (optioneel) | Platform Web SDK* of dil.js 5.0+ |  |
| Adobe Analytics (optioneel) | Platform Web SDK* of AppMeasurement.js 1.6.4+ |  |
| Experience Cloud Identity Service | Platform Web SDK* of VisitorAPI.js 2.0+ |  |
| Experience Platform Mobile SDK (optioneel) | 4.11 of hoger voor iOS en Android™ |  |
| Experience Platform Web SDK | 1.0, heeft de huidige versie van Experience Platform SDK [verschillende gebruiksgevallen nog niet ondersteund voor de Experience Cloud toepassingen](https://github.com/adobe/alloy/projects/5) |  |

## Implementatiestappen

1. [Implementeer de Adobe-](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) doelstelling voor uw web- of mobiele toepassingen.

   Bij gebruik van Audience Manager of Analytics:

1. [Adobe Audience Manager implementeren](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html)
1. [Adobe Analytics implementeren](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)
1. [Experience Cloud Identity Service implementeren](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html)

   >[!NOTE]
   >
   >Elke toepassing moet de Experience Cloud-id gebruiken en deel uitmaken van dezelfde Experience Cloud-organisatie om het delen van het publiek tussen toepassingen mogelijk te maken.

1. [De levering van het verzoek voor de Mensen en de Diensten van het Delen van het Publiek (Gedeelde Publiek)](https://www.adobe.com/go/audiences)
1. Segmenten maken in [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html) of [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/segments/segment-builder.html) en [deze soorten publiek configureren voor delen naar de Experience Cloud](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html) (als u Audience Manager of Adobe Analytics gebruikt)
1. Zodra het publiek in Adobe Target beschikbaar is, kunnen zij voor [het richten ervaringen met Adobe Target](https://experienceleague.adobe.com/docs/target/using/audiences/target.html) worden gebruikt


## Gegevensstroomdiagrammen implementeren

Het Web/Mobiele Vervaging van de Personalisatie kan worden uitgevoerd door of het Web SDK van het Platform of Mobiele SDK en het netwerk van de Rand te gebruiken, of het gebruiken van of traditionele toepassing-specifieke SDKs (bijvoorbeeld, AppMeasurement.js).

### Web/Mobile SDK van Platform en de Benadering van het Netwerk van de Rand

<img src="assets/websdkflow.svg" alt="Referentiearchitectuur voor de Web SDK/Mobile SDK van het Platform en de Benadering van het Netwerk van de Rand" style="border:1px solid #4a4a4a" />


### Toepassingsspecifieke SDK-benadering

<img src="assets/appsdkflow.png" alt="Referentiearchitectuur voor de toepassingsspecifieke SDK-benadering" style="border:1px solid #4a4a4a" />


## Verwante documentatie

* [Experience Cloud publiek](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html)
* [Audience Manager integreren met Adobe Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html)
* [Adobe Analytics Segment Sharing via AAM](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)


## Verwante blogberichten

* [Blauwdruk voor web personalisatie met Adobe Experience Platform Real-Time klantprofiel](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [Adobe Experience Platform-beslissingsengine integreren met AEM websites](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [Hoe Adobe Experience Platform Predictive Audiences persoonlijke ervaringen verbetert](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [Adobe Experience Platform Web SDK voor Audience Management](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [Adobe Experience Platform Real-Time klantprofiel implementeren via ons &quot;Customer Zero&quot;-programma](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [Hoe Adobe Experience Platform Klanten kan helpen hun mobiel Overseinen in real time aan te passen met de Dienst van Journey Orchestration en een Mobiele Leverancier van het Overseinen](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [Segmentatie in seconden: Hoe Adobe Experience Platform real-time klantprofielen werkelijkheid heeft gemaakt](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)