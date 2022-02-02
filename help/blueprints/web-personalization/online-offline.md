---
title: Web/mobiel personaliseren met online en offline gegevens
description: Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.
landing-page-description: Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7194thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: 5613bd6211b6eb6a960522f7ab04fd4a04ee9653
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Web/mobiel personaliseren met online en offline gegevens

Synchroniseer webpersonalisatie met e-mail en andere bekende en anonieme kanaalpersonalisatie.

## Gevallen gebruiken

* Optimalisatie landingspagina
* Gedrag en offlineprofiel activeren
* Personalisatie op basis van eerdere product/inhoud-weergaven, product/inhoud-affiniteit, milieukenmerken, publieksgegevens van derden en demografie, naast offlineinzichten zoals transacties, loyaliteit- en CRM-gegevens, en gemodelleerde inzichten
* Deel en doelpubliek dat in Real-time Customer Data Platform is gedefinieerd op websites en mobiele apps met Adobe Target.

## Toepassingen

* [!UICONTROL Real-time Customer Data Platform]
* Adobe Target
* Adobe Audience Manager (optioneel): Hiermee voegt u publieksgegevens van derden, apparaatgrafieken die op meerdere pagina&#39;s zijn gebaseerd, de mogelijkheid om segmenten van Platforms in Adobe Analytics te laten doorlopen en de mogelijkheid om Adobe Analytics-segmenten in het Platform te laten doorlopen toe
* Adobe Analytics (optioneel): Hiermee kunt u segmenten samenstellen op basis van historische gedragsgegevens en fijnkorrelige segmentatie van Adobe Analytics-gegevens

## Geïntegreerde patronen

<table class="tg" style="undefined;table-layout: fixed; width: 790px">
<colgroup>
<col style="width: 20px">
<col style="width: 276px">
<col style="width: 229px">
<col style="width: 265px">
</colgroup>
<thead>
  <tr>
    <th class="tg-y6fn">Aantal</th>
    <th class="tg-f7v4">Integratiepatroon</th>
    <th class="tg-y6fn">Capaciteit</th>
    <th class="tg-f7v4">Voorwaarden</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td class="tg-0lax">1</td>
    <td class="tg-73oq"><span style="font-weight:400;font-style:normal">RTCDP-streaming en delen van publiek in batches naar doel en Audience Manager via de benadering voor het delen van services bij publiek</span></td>
    <td class="tg-0lax"><span style="font-weight:400;font-style:normal">- Deel streaming en batchpubliek van RTCDP naar Target en Audience Manager via de service Publiek delen. Het publiek dat in real time wordt geëvalueerd vereist WebSDK en de publieksevaluatie in real time die in integratiepatroon 3 wordt geschetst.</span></td>
    <td class="tg-73oq">- Projectie van het publiek via de service voor het delen van het publiek moet worden uitgevoerd.<br>- Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.<br>- Identiteit moet worden omgezet in ECID om aan de rand te delen voordat Doel actie kan ondernemen.<br>- WebSDK-implementatie is niet vereist voor deze integratie.</td>
  </tr>
  <tr>
    <td class="tg-0lax">2</td>
    <td class="tg-73oq">RTCDP-streaming en delen van publiek in batches naar doel via Edge-aanpak</td>
    <td class="tg-0lax">- Deel streaming en batchpubliek van RTCDP naar Target via het Edge Network. Het publiek dat in real time wordt geëvalueerd vereist WebSDK en de publieksevaluatie in real time die in integratiepatroon 3 wordt geschetst.</td>
    <td class="tg-73oq">- De doelbestemming moet in Doelen RTCDP worden gevormd.<br>- Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.<br>WebSDK is niet vereist. <br>- Als het gebruiken van AT.js slechts profielraadpleging tegen ECID wordt gesteund. <br>- Voor aangepaste id namespace lookups op de Rand, wordt de plaatsing WebSDK vereist en elke identiteit moet als identiteit in de identiteitskaart worden geplaatst.</td>
  </tr>
  <tr>
    <td class="tg-0lax">3</td>
    <td class="tg-73oq">RTCDP segment evaluatie in real time op de Rand die aan Doel via de Rand wordt gedeeld gebruikend WebSDK.</td>
    <td class="tg-0lax">- Evalueer publiek in real time voor zelfde of volgende paginagrootte op de Rand.</td>
    <td class="tg-73oq">- De doelbestemming moet in Doelen RTCDP worden gevormd.<br>- Voor integratie met Doel is dezelfde IMS-instelling vereist als voor Experience Platform-instantie.<br>- WebSDK moet worden geïmplementeerd.<br>- Mobiele SDK en API-gebaseerde implementatie is nog niet beschikbaar</td>
  </tr>
</tbody>
</table>


## Architectuur

Overzichtsarchitectuur

<img src="assets/RTCDP+Target.png" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:80%; border:1px solid #4a4a4a" />

Processtroomarchitectuur

<img src="assets/RTCDP+Target_flow.png" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:80%; border:1px solid #4a4a4a" />

<br>

<img src="assets/RTCDP+Target_sequence.png" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:80%; border:1px solid #4a4a4a" />


Gedetailleerde architectuur

<img src="assets/personalization_with_apps.png" alt="Referentiearchitectuur voor de blauwdruk voor online/offline webpersonalisatie" style="width:80%; border:1px solid #4a4a4a"/>

## Guardrails

[Raadpleeg de handleidingen op de pagina Overzicht van de blauwdrukken voor persoonlijk gebruik op internet en mobiele apparatuur.](overview.md)

## Implementatiepatronen

De Web/Mobiele verpersoonlijkingsblauwdruk kan door de volgende benaderingen worden uitgevoerd zoals hieronder geschetst.

1. Met de [!UICONTROL Platform Web SDK] of [!UICONTROL Platform Mobile SDK] en [!UICONTROL Edge Network].
1. Traditionele toepassingsspecifieke SDK&#39;s gebruiken (bijvoorbeeld AppMeasurement.js)

### 1. Platform Web/Mobile SDK en Edge Approach

[Verwijs naar het Web van het Experience Platform en Mobiele SDK Blauwdruk](../data-ingestion/websdk.md)

### 2. Toepassingsspecifieke SDK-benadering

<img src="assets/app_sdk_flow.png" alt="Referentiearchitectuur voor de toepassingsspecifieke SDK-benadering" style="width:80%; border:1px solid #4a4a4a" />

## Overwegingen bij de implementatie

Identiteitsvoorwaarden

* Voor het delen van het publiek van Adobe Experience Platform naar Adobe Target moet ECID als identiteit worden gebruikt.
* Alternatieve identiteiten kunnen ook worden gebruikt om het publiek van het Experience Platform via Audience Manager naar Adobe Target te delen. Experience Platform activeert publiek naar Audience Manager via de volgende ondersteunde naamruimten: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Merk op dat Audience Manager en Doel publiekslidmaatschappen via de identiteit van ECID oplossen, zodat ECID nog voor het definitieve publiek die aan Adobe Target deelt wordt vereist.

## Implementatiestappen


1. [Adobe Target implementeren](https://experienceleague.adobe.com/docs/target/using/implement-target/implementing-target.html) voor uw web- of mobiele toepassingen
1. [Adobe Audience Manager implementeren](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html) (optioneel)
1. [Adobe Analytics implementeren](https://experienceleague.adobe.com/docs/analytics/implementation/home.html)  (optioneel)
1. [Experience Platform uitvoeren en [!UICONTROL Klantprofiel in realtime]](https://experienceleague.adobe.com/docs/platform-learn/getting-started-for-data-architects-and-data-engineers/overview.html)
1. Implementeren [Experience Cloud Identity Service](https://experienceleague.adobe.com/docs/id-service/using/implementation/implementation-guides.html) of [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html) Experience Platform Web SDK is vereist voor realtime Edge-segmentatie, maar is niet vereist voor het delen van streaming- en batchpubliek van RTCDP naar Target. Merk op dat de steun voor segmentatie in real time via Mobiele SDK nog in ontwikkeling is.
1. [Adobe Target inschakelen als bestemming in Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) of voor de aanpak van het delen van het publiek [Verzoek om provisioning voor het delen van publiek tussen Experience Platform en Adobe Target (gedeeld publiek)](https://www.adobe.com/go/audiences) om publiek van Experience Platform aan Doel te delen.
   >[!NOTE]
   >
   >Wanneer het gebruiken van de dienst van het Delen van het Publiek tussen RTCDP en Adobe Target, moet het publiek worden gedeeld gebruikend identiteitskaart van de Experience Cloud en deel van het zelfde Experience Cloud Org uitmaken. Ondersteuning voor andere identiteiten dan ECID vereist het gebruik van de WebSDK en Experience Edge Network.


## Verwante documentatie

### Documentatie

* [Adobe Target Connection voor Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en)
* [Experience Platform segmentdelen met Audience Manager en andere Experience Cloud-oplossingen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html)
* [Experience Platform Web SDK-documentatie](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Documentatie Experience Cloud ID-service](https://experienceleague.adobe.com/docs/id-service/using/home.html)
* [Overzicht van segmentatie Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [Streaming segmentering](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Overzicht van Experience Platform Segment Builder](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/overview.html)
* [Audience Manager Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html)
* [Adobe Analytics Segment Sharing via Adobe Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Documentatie over Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html)

### Tutorials

* [Volgend-klare verpersoonlijking met Real-Time CDP en Adobe Target](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=en)

## Verwante blogberichten

* [[!DNL Blueprint for Web Personalization using Adobe Experience Platform Real-Time Customer Profile]](https://medium.com/adobetech/blueprint-for-web-personalization-using-adobe-experience-platform-real-time-customer-profile-fef2ce7a4b2f)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
* [[!DNL Integrating Adobe Experience Platform Decisioning Engine with AEM Websites]](https://jaeness.medium.com/integrating-adobe-experience-platform-decisioning-engine-with-aem-websites-9c222acd12e2)
* [[!DNL Adobe Experience Platform’s Identity Service — How to Solve the Customer Identity Conundrum]](https://medium.com/adobetech/adobe-experience-platforms-identity-service-how-to-solve-the-customer-identity-conundrum-f95e22d16ea9)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Implementing Adobe Experience Platform Real-Time Customer Profile through our “Customer Zero” Program]](https://medium.com/adobetech/implementing-adobe-experience-platform-real-time-customer-profile-through-our-customer-zero-32e7cd952896)
* [[!DNL How Adobe Experience Platform Can Help Customers Personalize Their Mobile Messaging in Real-Time with Journey Orchestration Service and a Mobile Messaging Vendor]](https://medium.com/adobetech/how-adobe-experience-platform-helped-a-client-personalize-their-mobile-messaging-in-real-time-with-7d634aefa098)
* [[!DNL Segmentation in Seconds: How Adobe Experience Platform Made Real-time Customer Profiles a Reality]](https://medium.com/adobetech/segmentation-in-seconds-how-adobe-experience-platform-made-real-time-customer-profiles-a-reality-a7a8552b0847)
* [[!DNL Build an Optimal Online Experience: Enrich Unified Profile with Query Service]](https://medium.com/adobetech/build-an-optimal-online-experience-enrich-unified-profile-with-query-service-8027c196ab33)
