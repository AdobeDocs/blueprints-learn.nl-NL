---
user-guide-title: Digitale beleving blauwdrukken
breadcrumb-title: Blauwdrukken
user-guide-description: De blauwdrukken zijn herhaalbare implementaties om gevestigde bedrijfsproblemen aan te pakken en architectuurdiagrammen, technische overwegingen, en relevante documentatiekoppelingen te bevatten.
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: af390011dc068c4289f98d7fc0108ce48a5375c7
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 4%

---


# Digitale beleving blauwdrukken {#architecture}

+ [Overzicht](/help/blueprints/overview.md)
+ Verticale industrie blauwdrukken{#vertical-blueprints}
   + [Overzicht](/help/blueprints/vertical-blueprints/overview.md)
   + [Deksel](/help/blueprints/vertical-blueprints/apparel.md)
   + [Detailhandel](/help/blueprints/vertical-blueprints/retail.md)
   + [Telecommunicatie](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [Reizen en verblijf](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ Overzicht van architectuur{#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform en toepassingen](/help/blueprints/experience-platform/platform-applications.md)
   + [Gegevensstroom Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
   + Implementatie{#deployment}
      + [Experience Platform Web SDK &amp; Edge Network](/help/blueprints/experience-platform/deployment/websdk.md)
      + [SDK&#39;s voor toepassingen](/help/blueprints/experience-platform/deployment/appsdk.md)
      + [Guardrails](/help/blueprints/experience-platform/deployment/guardrails.md)
+ Activering publiek en profiel{#audience-activation}
   + [Overzicht](/help/blueprints/audience-activation/overview.md)
   + [Anonieme Audience Activation (AAM)](/help/blueprints/audience-activation/anonymous.md)
   + Bekende activering van de Klant (RTCDP) {#known-customer-audience-activation}
      + [Overzicht](/help/blueprints/audience-activation/known.md)
      + Activering op sociale en advertentiekanalen{#audience-activation}
         + [Activering voor aangepast publiek van Facebook](/help/blueprints/audience-activation/destinations/facebook.md)
         + [Activering voor Google Customer Match](/help/blueprints/audience-activation/destinations/gcm.md)
      + [Activering voor streaming van bestanden en bedrijven](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Hub voor klantactiviteiten](/help/blueprints/audience-activation/customer-activity.md)
      + [Segmentovereenkomst](/help/blueprints/audience-activation/segment-match.md)
   + [Activering met Experience Cloud-toepassingen](/help/blueprints/audience-activation/platform-and-applications.md)
+ B2B-activering en marketing{#b2b-activation}
   + [Overzicht](/help/blueprints/b2b/overview.md)
   + [B2B-activering](/help/blueprints/b2b/b2bactivation.md)
   + Aanvoerketen voor campagnes met Marketo en Workfront{#optimize-campaign-supply-chain-with-marketo-and-workfront}
      + [Overzicht](/help/blueprints/b2b/campaign-supply-chain/overview.md)
      + [Innemen en maken](/help/blueprints/b2b/campaign-supply-chain/intake-and-create.md)
      + [Artikelen met succes voor klanten](/help/blueprints/b2b/campaign-supply-chain/customer-success-stories.md)
+ Customer Journey Analytics{#customer-journey-analytics}
   + [Overzicht](/help/blueprints/customer-journey-analytics/overview.md)
   + [CJA-publiek delen naar RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA en Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ Klantenreizen{#customer-journeys}
   + [Overzicht](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer{#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + Beslissingsbeheer{#decision-management}
         + [Overzicht](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [Beslissingsbeheer aan de rand](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [Beslissingsbeheer op de hub](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer met Adobe Campaign](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [Berichten van derden](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard{#campaign-standard}
      + [Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html)
      + [Real-Time CDP met Adobe Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html)
   + Campagne v8{#campaign-v8}
      + [Campagne v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP met Adobe Campaign v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer met Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campagne v7{#campaign-v7}
      + [Campagne v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP met Adobe Campaign v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer met Adobe Campaign v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ Gegevensverzameling, Toegang en Exporteren{#data-ingestion}
   + [Overzicht](/help/blueprints/data-ingestion/overview.md)
   + [Voorbereiding en inname van gegevens](/help/blueprints/data-ingestion/ingestion.md)
   + [Toegang tot gegevens en exporteren](/help/blueprints/data-ingestion/egress.md)
   + [Gebeurtenis doorsturen](/help/blueprints/data-ingestion/server-side-collection.md)
+ Gegevensanalyse, intelligentie en AI/ML{#data-exploration}
   + [Overzicht](/help/blueprints/data-insights/overview.md)
   + [Gegevensanalyse en -informatie](/help/blueprints/data-insights/analysis.md)
   + [Aangepaste gegevenswetenschap voor profielverrijking](/help/blueprints/data-insights/data-science.md)
+ Web en mobiele personalisatie{#web-personalization}
   + [Overzicht](/help/blueprints/web-personalization/overview.md)
   + [Gedrag aanpassen - Doel](/help/blueprints/web-personalization/behavioral.md)
   + [Bekende klantpersonalisatie - Doel en RTCDP](/help/blueprints/web-personalization/known-personalization.md)
   + [Beslissingsbeheer](/help/blueprints/web-personalization/decision-management-edge.md)