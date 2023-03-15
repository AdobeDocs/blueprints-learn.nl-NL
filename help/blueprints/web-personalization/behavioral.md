---
title: Gedragingen webpersonalisatie blauwdruk
description: Ontdek hoe u content kunt aanpassen op basis van online gedrag en publieksdata.
landing-page-description: Leer personaliseren op basis van online gedrag en doelgroepgegevens.
short-description: Learn to personalize based on online behavior and audience data.
solution: Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7085
thumbnail: thumb-web-personalization-scenario1.jpg
exl-id: b9882c2c-cb45-4efa-a85c-8fe48f641a12
source-git-commit: 3a6a98eded28baee2cbb44de2262bbd580fa0c94
workflow-type: tm+mt
source-wordcount: '609'
ht-degree: 3%

---

# Gedragingen Web/Mobiele Verpersoonlijkingsblauwdruk

Persoonlijk maken op basis van online gedrag en publieksgegevens.

## Gebruik hoofdletters

* Optimalisatie landingspagina
* Gedragsgerichte acties
* Personalisatie op basis van eerdere productweergaven/content-weergaven, de affiniteit tussen product en inhoud, milieukenmerken, publieksgegevens van derden en demografie

## Toepassingen

* Adobe Target
* Adobe Analytics (optioneel)
* Adobe Audience Manager (optioneel)
* Adobe Real-time Customer Data Platform (optioneel)

## Architectuur

<img src="assets/behavioral_personalization.svg" alt="Referentiearchitectuur voor de blauwdruk van de Aanpassing van het Web Behavioral" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" class="modal-image" />


## Implementatiepatronen

De Web/Mobiele verpersoonlijkingsblauwdruk kan door de volgende benaderingen worden uitgevoerd zoals hieronder geschetst.

1. Met de [!UICONTROL Platform Web SDK] of [!UICONTROL Platform Mobile SDK] en [!UICONTROL Edge Network]. [Verwijs naar het Web van het Experience Platform en Mobiele SDK Blauwdruk](../experience-platform/deployment/websdk.md)
1. Traditionele toepassingsspecifieke SDK&#39;s gebruiken (bijvoorbeeld AppMeasurement.js). [Raadpleeg de specifieke SDK-blauwdruk voor de toepassing](../experience-platform/deployment/appsdk.md)

## Uitvoeringsstappen

1. [Adobe Target implementeren](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) voor uw web- of mobiele toepassingen.

### Implementatiestappen - Audience Manager of Adobe Analytics

1. [Adobe Audience Manager implementeren](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html)
1. [Adobe Analytics implementeren](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)
1. [Experience Cloud Identity Service implementeren](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html)

   >[!NOTE]
   >
   >Elke toepassing moet de Experience Cloud-id gebruiken en deel uitmaken van dezelfde Experience Cloud-organisatie om het delen van het publiek tussen toepassingen mogelijk te maken.

1. [De levering van het verzoek voor de Mensen en de Diensten van het Delen van het Publiek (Gedeelde Publiek)](https://www.adobe.com/go/audiences)
1. Segmenten samenstellen in [Adobe Analytics](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-build.html) of [Adobe Audience Manager](https://experienceleague.adobe.com/docs/audience-manager/user-guide/features/segments/segment-builder.html) en [deze soorten publiek configureren voor het delen naar de Experience Cloud](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)  (bij gebruik van Audience Manager of Adobe Analytics)
1. Zodra het publiek in Adobe Target beschikbaar is, kan het worden gebruikt voor [het richten van ervaringen met Adobe Target](https://experienceleague.adobe.com/docs/target/using/audiences/target.html)

### Implementatiestappen - Real-time Customer Data Platform

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden ingevoerd.
1. [De juiste identiteiten en naamruimten configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) op het schema om ervoor te zorgen dat ingesloten gegevens in een verenigd profiel kunnen vastmaken.
1. [De schema&#39;s en datasets voor profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Gegevens samenvoegen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. [Voorziening [!UICONTROL Real-time Customer Data Platform] delen van segmenten](https://www.adobe.com/go/audiences) tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt gedefinieerd en aan Audience Manager wordt gedeeld.
1. [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html) in Experience Platform. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. [Doelen configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html) voor het delen van profielkenmerken en publieksleden aan gewenste bestemmingen.


## Gerelateerde documentatie

* [Experience Cloud publiek](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html)
* [Audience Manager integreren met Adobe Target](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html)
* [Adobe Analytics Segment Sharing via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [[!UICONTROL Real-time Customer Data Platform] overzicht](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [[!UICONTROL Real-time Customer Data Platform] Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Gerelateerde blogberichten

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our "Customer Zero" Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
