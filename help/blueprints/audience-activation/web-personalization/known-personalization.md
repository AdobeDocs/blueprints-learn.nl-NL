---
title: Overzicht van web/mobiele personalisatie - Adobe Target en RTCDP
description: Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.
landing-page-description: Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.
short-description: Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 845655a275cdb6d4a9cd397ec7c3515cbf02d321
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 4%

---


# Web/Mobiele Aanpassing met bekende blauwdruk van klantgegevens

## Gebruiksscenario&#39;s

* Online personalisatie met bekende klantgegevens
* Optimalisatie landingspagina
* Personalisatie op basis van eerdere product/inhoud-weergaven, product/inhoud-affiniteit, milieukenmerken en demografie, naast offlinegegevens zoals transacties, loyaliteits- en CRM-gegevens, en gemodelleerde inzichten
* Deel en doelpubliek dat in Real-time Customer Data Platform is gedefinieerd op websites en mobiele apps met Adobe Target.

## Applicaties

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optioneel): gegevens voor publiek van derden toevoegen
* Adobe Analytics of Customer Journey Analytics (optioneel): hiermee kunt u segmenten samenstellen op basis van historische gegevens van klanten en gedragingen met een fijnkorrelige segmentatie

### Referentiedocumentatie

* [Adobe Target Connection voor Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [Edge DataStream-configuratie](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
* [Het segmentdelen van Experience Platforms met Audience Manager en andere oplossingen van Experiencen Cloud](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)


## Integratiepatronen

| Integratiepatroon | Capaciteit | Voorwaarden |
|---|---|---|
| Realtime segmentevaluatie op de Rand die van Real-time Customer Data Platform aan Doel wordt gedeeld | <ul><li>Evalueer publiek in real time voor zelfde of volgende paginagrootte op de Rand.</li><li>Daarnaast worden alle segmenten die op streaming- of batchwijze worden beoordeeld, geprojecteerd op de [!DNL Edge Network] op te nemen in de evaluatie en personalisatie van het Edge-segment.</li></ul> | <ul><li>Web/Mobile SDK moet worden geïmplementeerd of [!DNL Edge Network] Server-API</li><li>DataStream moet in de Rand van de Ervaring met toegelaten de uitbreiding van het Doel en van het Experience Platform worden gevormd</li><li>Het doel moet in de Doelen van Real-time Customer Data Platform worden gevormd.</li><li>Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.</li></ul> |
| Streaming en batchverdeling van publiek van Real-time Customer Data Platform naar Target via Edge-aanpak | <ul><li>Deel streaming en batchpubliek van Real-time Customer Data Platform naar Target via de [!DNL Edge Network]. Het publiek dat in real time wordt geëvalueerd vereist Web SDK en [!DNL Edge Network] uitvoering.</li></ul> | <ul><li>Web/Mobile SDK of de implementatie van de Rand API van Doel wordt niet vereist voor het delen van het stromen en partij RTCDP publiek aan Doel hoewel het wordt vereist om in real time de hierboven geschetste evaluatie van het randsegment toe te laten.</li><li>Als u AT.js gebruikt, wordt alleen profielintegratie met de naamruimte ECID ondersteund.</li><li>Voor de raadplegingen van de douaneidentiteit namespace op de Rand, wordt de plaatsing van SDK/Edge API van het Web vereist en elke identiteit moet als identiteit in de identiteitskaart worden geplaatst.</li><li>De doelbestemming moet in de Doelen van Real-time Customer Data Platform worden gevormd, slechts wordt de standaardproductiestandaard in RTCDP gesteund.</li><li>Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.</li></ul> |
| Streaming en batchverdeling van publiek van Real-time Customer Data Platform naar Target en Audience Manager via de benadering voor het delen van services bij het publiek | <ul><li>Dit integratiepatroon kan worden benut wanneer extra verrijking van gegevens van derden en publiek in de Audience Manager gewenst is.</li></ul> | <ul><li>Web/Mobile SDK wordt niet vereist voor het delen van het stromen en partijpubliek aan Doel hoewel het wordt vereist om de evaluatie van het randsegment in real time toe te laten.</li><li>Als u AT.js gebruikt, wordt alleen profielintegratie met de naamruimte ECID ondersteund.</li><li>Voor de raadplegingen van de douaneidentiteit namespace op de Rand, wordt de plaatsing van SDK/Edge API van het Web vereist en elke identiteit moet als identiteit in de identiteitskaart worden geplaatst.</li><li>De projectie van het publiek via de dienst voor het delen van het publiek moet worden voorzien.</li><li>Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.</li><li>Alleen het publiek van de standaardproductiesandbox ondersteunt de hoofdservice voor het delen van het publiek.</li></ul> |

## In real time, het stromen, en partijpubliek die aan Adobe Target delen

Architectuur

<img src="assets/RTCDP+Target.svg" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Sequentiedetail

<img src="assets/RTCDP+Target_flow.svg" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Overzicht architectuur

<img src="assets/personalization_with_apps.svg" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Implementatiepatronen

Bekende klantpersonalisatie wordt ondersteund via verschillende implementatiemethoden.

### Implementatiepatroon 1 - [!DNL Edge Network] met Web/Mobile SDK of [!DNL Edge Network] API (aanbevolen aanpak)

* Met de [!DNL Edge Network] met de Web/Mobile SDK. Voor Edge-segmentatie in realtime is de Web/Mobile SDK- of Edge API-implementatiebenadering vereist.
* [Verwijs naar het Web van het Experience Platform en Mobiele SDK Blauwdruk](../../experience-platform/deployment/websdk.md) voor de op SDK gebaseerde implementatie.
* Voor gebruik in de mobiele SDK wordt de [Adobe Journey Optimizer - Extensie voor besluitvorming](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer-decisioning) moet worden geïnstalleerd in de mobiele SDK.
* [Zie de [!DNL Edge Network] Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) voor een API-gebaseerde implementatie van Adobe Target met Edge Profile.

### Implementatiepatroon 2 - Toepassingsspecifieke SDK&#39;s

traditionele toepassingsspecifieke SDK&#39;s gebruiken (bijvoorbeeld AT.js en AppMeasurement.js). De evaluatie van het segment in real time van de Rand wordt niet gesteund gebruikend deze implementatiebenadering. Het streamen en het delen van batchgebruikers vanuit de hub van het Experience Platform worden echter ondersteund met deze implementatieaanpak.

[Raadpleeg de documentatie bij de Adobe Target Connector](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[Raadpleeg de specifieke SDK-blauwdruk voor de toepassing](../../experience-platform/deployment/appsdk.md)

## Implementatieoverwegingen

Identiteitsvoorwaarden

* Elke primaire identiteit kan worden gebruikt bij het gebruik van het hierboven beschreven implementatiepatroon 1 met de [!DNL Edge Network] en Web SDK. Voor de eerste persoonlijke aanmelding is de primaire identiteit van de set met verpersoonlijkingsverzoeken gelijk aan de primaire identiteit van het profiel van Real-time Customer Data Platform.

## Gerelateerde documentatie

### SDK-documentatie

* [Experience Platform Web SDK-documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentatie over Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)
* [Documentatie Experience Cloud ID Service](https://experienceleague.adobe.com/docs/id-service/using/home.html)

### Segmenteringsdocumentatie

* [Overzicht van segmentatie Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Segmentatie in realtime](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html)
* [Streaming segmentering](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Adobe Analytics Segment Sharing via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Configuratie van beleid samenvoegen](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)

### Tutorials

* [Volgend-klare personalisatie met Real-Time CDP en Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=en)

### Gerelateerde blogberichten

* [Adobe kondigt &#39;Same Page Enhanced Personalization&#39; aan met Adobe Target en Real-time Customer Data Platform](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform's Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our "Customer Zero" Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
