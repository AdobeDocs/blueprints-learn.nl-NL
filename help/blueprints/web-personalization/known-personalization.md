---
title: Overzicht van web-/mobiele personalisatie
description: Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.
landing-page-description: Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.
solution: Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection, Experience Platform
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: b1da29f76b274334ca36d0c144adcb6aa797fc0e
workflow-type: tm+mt
source-wordcount: '1268'
ht-degree: 0%

---


# Web/Mobile Personalization met bekende klantgegevens

## Gevallen gebruiken

* Online personalisatie met bekende klantgegevens
* Optimalisatie landingspagina
* Personalization is gebaseerd op eerdere product/inhoud-weergaven, product/inhoud-affiniteit, milieukenmerken en demografie, naast offlinegegevens zoals transacties, loyaliteits- en CRM-gegevens, en gemodelleerde inzichten
* Deel en doelpubliek dat in Real-time Customer Data Platform is gedefinieerd op websites en mobiele apps met Adobe Target.

## Toepassingen

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optioneel): Hiermee voegt u publieksgegevens van derden, op een computer gebaseerde apparaatgrafiek toe
* Adobe Analytics (optioneel): Hiermee kunt u segmenten samenstellen op basis van historische gedragsgegevens en fijnkorrelige segmentatie van Adobe Analytics-gegevens

## Integratiepatronen

| Integratiepatroon | Capaciteit | Voorwaarden |
|---|---|---|
| Realtime segmentevaluatie op de Rand die van Real-time Customer Data Platform aan Doel wordt gedeeld | <ul><li>Evalueer publiek in real time voor zelfde of volgende paginagrootte op de Rand.</li><li>Bovendien zullen om het even welke segmenten die op het stromen of partijwijze worden geëvalueerd ook aan het Netwerk van de Rand worden geprojecteerd om in de evaluatie en verpersoonlijking van het randsegment worden omvat.</li></ul> | <ul><li>Web/Mobile SDK moet zijn geïmplementeerd voor de Edge Network Server-API</li><li>DataStream moet in de Rand van de Ervaring met toegelaten de uitbreiding van het Doel en van het Experience Platform worden gevormd</li><li>Het doel moet in de Doelen van Real-time Customer Data Platform worden gevormd.</li><li>Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.</li></ul> |
| Streaming en batchverdeling van publiek van Real-time Customer Data Platform naar Target via Edge-aanpak | <ul><li>Deel streaming en batchpubliek van Real-time Customer Data Platform naar Target via het Edge Network. Het publiek dat in real time wordt geëvalueerd vereist WebSDK en de implementatie van het Netwerk van de Rand.</li></ul> | <ul><li>Web/Mobile SDK wordt niet vereist voor het delen van het stromen en partijpubliek aan Doel hoewel het wordt vereist om de evaluatie van het randsegment in real time toe te laten.</li><li>Als u AT.js gebruikt, wordt alleen profielintegratie met de naamruimte ECID ondersteund.</li><li>Voor de raadplegingen van de douanetechaamsnaamruimte op de Rand, wordt de plaatsing WebSDK vereist en elke identiteit moet als identiteit in de identiteitskaart worden geplaatst.</li><li>Het doel moet in de Doelen van Real-time Customer Data Platform worden gevormd.</li><li>Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.</li></ul> |
| Streaming en batchverdeling van publiek van Real-time Customer Data Platform naar Target en Audience Manager via de benadering voor het delen van services bij het publiek | <ul><li>Dit integratiepatroon kan worden benut wanneer extra verrijking van gegevens van derden en publiek in de Audience Manager gewenst is.</li></ul> | <ul><li>Web/Mobile SDK wordt niet vereist voor het delen van het stromen en partijpubliek aan Doel hoewel het wordt vereist om de evaluatie van het randsegment in real time toe te laten.</li><li>Als u AT.js gebruikt, wordt alleen profielintegratie met de naamruimte ECID ondersteund.</li><li>Voor de raadplegingen van de douanetechaamsnaamruimte op de Rand, wordt de plaatsing WebSDK vereist en elke identiteit moet als identiteit in de identiteitskaart worden geplaatst.</li><li>De projectie van het publiek via de dienst voor het delen van het publiek moet worden voorzien.</li><li>Het doel moet in de Doelen van Real-time Customer Data Platform worden gevormd.</li><li>Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.</li></ul> |

## Real-time, Streaming en Batch Publiek delen met Adobe Target

Architectuur

<img src="assets/RTCDP+Target.png" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:90%; border:1px solid #4a4a4a" />

Sequentiedetail

<img src="assets/RTCDP+Target_flow.png" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:90%; border:1px solid #4a4a4a" />

Overzichtsarchitectuur

<img src="assets/personalization_with_apps.png" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:90%; border:1px solid #4a4a4a"/>

## Implementatiepatronen

Bekende Customer Personalization wordt ondersteund via verschillende implementatiemethoden.

### Implementatiepatroon 1 - Edge Network with Web/Mobile SDK of Edge Network API (aanbevolen aanpak)

* Het gebruiken van het Netwerk van de Rand met Web/Mobile SDK. Voor Edge-segmentatie in realtime is de Web/Mobile SDK- of Edge API-implementatiebenadering vereist.
* [Verwijs naar het Web van het Experience Platform en Mobiele SDK Blauwdruk](../data-ingestion/websdk.md) voor de op SDK gebaseerde implementatie.
* [Raadpleeg de Edge Network Server-API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) voor een API-gebaseerde implementatie van Adobe Target met Edge Profile.

### Implementatiepatroon 2 - Toepassingsspecifieke SDK&#39;s

traditionele toepassingsspecifieke SDK&#39;s gebruiken (bijvoorbeeld AT.js en AppMeturement.js). De evaluatie van het segment in real time van de Rand wordt niet gesteund gebruikend deze implementatiebenadering. Het streamen en het delen van batchgebruikers vanuit de hub van het Experience Platform worden echter ondersteund met deze implementatieaanpak.

[Raadpleeg de specifieke SDK-blauwdruk voor de toepassing](../data-ingestion/appsdk.md)

### Implementatiestappen

1. [Adobe Target implementeren](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) voor uw web- of mobiele toepassingen
1. [Experience Platform uitvoeren en [!UICONTROL Klantprofiel in realtime]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html) zorgen ervoor dat het gemaakte publiek wordt geactiveerd voor de Edge door de toepasselijke [samenvoegingsbeleid](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy) als actief op de rand.
1. Implementeren [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html). SDK van het Web van het Experience Platform wordt vereist voor segmentatie in real time van de Rand, maar niet vereist voor het delen van het stromen en partijpubliek van Real-time Customer Data Platform aan Doel. Ondersteuning voor realtime segmentatie via de mobiele SDK en API is momenteel niet beschikbaar.
1. [Het Edge-netwerk configureren met een Edge DataStream](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
1. [Adobe Target inschakelen als bestemming in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
1. (Optioneel) [Adobe Audience Manager implementeren](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html).
1. (Optioneel) [Verzoek om provisioning voor het delen van publiek tussen Experience Platform en Adobe Target (gedeeld publiek)](https://www.adobe.com/go/audiences) om publiek van Experience Platform aan Doel te delen.

## Guardrails

[Raadpleeg de handleidingen op de pagina Overzicht van de blauwdrukken voor persoonlijk gebruik op internet en mobiele apparatuur.](overview.md)

## Overwegingen bij de implementatie

Identiteitsvoorwaarden

* Elke primaire identiteit kan worden benut wanneer implementatiepatroon 1 wordt gebruikt die hierboven is beschreven met het Edge-netwerk en WebSDK. Voor de eerste persoonlijke aanmelding is de primaire identiteit van de set met verpersoonlijkingsverzoeken gelijk aan de primaire identiteit van het profiel van Real-time Customer Data Platform. Identiteitsvervlechting tussen anonieme apparaten en bekende klanten wordt verwerkt op de hub en later geprojecteerd aan de rand.
* Voor het delen van het publiek van Adobe Experience Platform naar Adobe Target moet ECID als identiteit worden gebruikt bij het gebruik van de service voor het delen van het publiek, zoals beschreven in scenario 3 hierboven.
* Alternatieve identiteiten kunnen ook worden gebruikt om het publiek van het Experience Platform via Audience Manager naar Adobe Target te delen. Experience Platform activeert publiek naar Audience Manager via de volgende ondersteunde naamruimten: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Merk op dat Audience Manager en Doel publiekslidmaatschappen via de identiteit van ECID oplossen, zodat ECID nog voor het definitieve publiek die aan Adobe Target deelt wordt vereist.

## Verwante documentatie

### SDK-documentatie

* [Experience Platform Web SDK-documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentatie over Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)
* [Documentatie Experience Cloud ID-service](https://experienceleague.adobe.com/docs/id-service/using/home.html)

### Verbindingsdocumentatie

* [Adobe Target Connection voor Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Edge DataStream-configuratie](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)
* [Experience Platform segmentdelen met Audience Manager en andere Experience Cloud-oplossingen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)

### Segmentatiedocumentatie

* [Overzicht van segmentatie Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Segmentatie in realtime](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html)
* [Streaming segmentering](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Adobe Analytics Segment Sharing via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Configuratie van beleid samenvoegen](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)

### Tutorials

* [Volgend-klare verpersoonlijking met Real-Time CDP en Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=en)

### Verwante blogberichten

* [Adobe kondigt Personalization met dezelfde pagina en Real-time Customer Data Platform aan](https://blog.adobe.com/en/publish/2021/10/05/adobe-announces-same-page-enhanced-personalization-with-adobe-target-real-time-customer-data-platform)
* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
