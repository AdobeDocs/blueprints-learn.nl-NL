---
user-guide-title: Blauwdrukken voor digitale ervaringen
breadcrumb-title: Blauwdrukken
user-guide-description: Blauwdrukken zijn herhaalbare implementaties om vastgestelde bedrijfsproblemen aan te pakken en bevatten architectuurdiagrammen, technische overwegingen en relevante documentatiekoppelingen.
product: adobe experience platform
mini-toc-levels: 3
role: Architect, Developer, User
source-git-commit: 5095a3aed75c727f0e28aaa07587994a23020448
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 18%

---


# Blauwdrukken voor digitale ervaringen {#architecture}

+ [Digitale ervaringen blauwdrukken](/help/blueprints/overview.md)
+ Verticale industriegrootte {#vertical-blueprints}
   + [Overzicht](/help/blueprints/vertical-blueprints/overview.md)
   + [Deksel](/help/blueprints/vertical-blueprints/apparel.md)
   + [Retail](/help/blueprints/vertical-blueprints/retail.md)
   + [Telecommunicatie](/help/blueprints/vertical-blueprints/telecommunications.md)
   + [Reizen en gastvrijheid](/help/blueprints/vertical-blueprints/travel-hospitality.md)
+ Overzichten van architectuur {#architecture-overview}
   + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
   + [Experience Platform en toepassingen](/help/blueprints/experience-platform/platform-applications.md)
   + [Gegevensstroom Experience Platform](/help/blueprints/experience-platform/platform-data-flow.md)
   + Implementatie {#deployment}
      + [Experience Platform Web SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
      + [SDK&#39;s voor toepassingen](/help/blueprints/experience-platform/deployment/appsdk.md)
      + [Beveiligingsmechanismen](/help/blueprints/experience-platform/deployment/guardrails.md)
+ Activering publiek en profiel {#audience-activation}
   + [Overzicht](/help/blueprints/audience-activation/overview.md)
   + [Anoniem Audience Activation](/help/blueprints/audience-activation/anonymous.md)
   + Bekende activering van de Klant (RTCDP) {#known-customer-audience-activation}
      + [Overzicht](/help/blueprints/audience-activation/known.md)
      + [Activering op sociale en reclamekanalen](/help/blueprints/audience-activation/advertising-activation.md)
      + [Activering voor streaming van bestanden en bedrijven](/help/blueprints/audience-activation/enterprise-destinations.md)
      + [Klantactiviteiten](/help/blueprints/audience-activation/customer-activity.md)
      + [Segmentovereenkomst](/help/blueprints/audience-activation/segment-match.md)
   + [Activering met Experience Cloud-toepassingen](/help/blueprints/audience-activation/platform-and-applications.md)
   + Web en mobiele Personalization {#web-personalization}
      + [Overzicht](/help/blueprints/audience-activation/web-personalization/overview.md)
      + [Gedrag aanpassen - Doel](/help/blueprints//audience-activation/web-personalization/behavioral.md)
      + [Bekende klantpersonalisatie - Doel en RTCDP](/help/blueprints/audience-activation/web-personalization/known-personalization.md)
      + [Beslissingsbeheer](/help/blueprints/audience-activation/web-personalization/decision-management-edge.md)
+ B2B-activering en -marketing {#b2b-activation}
   + [Overzicht](/help/blueprints/b2b/overview.md)
   + [B2B-activering](/help/blueprints/b2b/b2bactivation.md)
   + [B2B-rekeningactivering](/help/blueprints/b2b/b2b-account-activation.md)
   + Marketo Engage en de Blauwdruk van de Integratie van Workfront {#marketo-engage-and-workfront-integration-blueprint}
      + [Overzicht](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
      + [Innemen en maken](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
      + [Reviseren en goedkeuren](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
      + [Succesverhalen van klanten](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
+ Inhoud en Commerce {#content-commerce}
   + [Adobe Commerce &amp; RTCDP](/help/blueprints/content-commerce/commerce/commerce-rtcdp.md)
+ Customer Journey Analytics {#customer-journey-analytics}
   + [Overzicht](/help/blueprints/customer-journey-analytics/overview.md)
   + [CJA-publiek delen met RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
   + [CJA en Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
+ De Reizen van de klant {#customer-journeys}
   + [Overzicht](/help/blueprints/customer-journeys/overview.md)
   + Journey Optimizer{#journey-optimizer}
      + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer.md)
      + Beslissingsbeheer {#decision-management}
         + [Overzicht](/help/blueprints/customer-journeys/decision_management/decision-management-overview.md)
         + [Beslissingsbeheer aan de rand](/help/blueprints/customer-journeys/decision_management/decision-management-edge.md)
         + [ Beheer van het Besluit op de hub ](/help/blueprints/customer-journeys/decision_management/decision-management-hub.md)
      + [Journey Optimizer met Adobe Campaign](/help/blueprints/customer-journeys/ajo-and-campaign.md)
      + [Berichten van derden](/help/blueprints/customer-journeys/3rd-party-messaging.md)
   + Campaign Standard {#campaign-standard}
      + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/docs/campaign-standard.html){target="_blank"}
      + [ Real-Time CDP met Adobe  [!DNL Campaign Standard] ](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html) {target="_blank"}
   + Campagne v8 {#campaign-v8}
      + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8.md)
      + [Real-Time CDP met Adobe  [!DNL Campaign]  v8](/help/blueprints/customer-journeys/rtcdp-and-campaign-v8.md)
      + [Journey Optimizer met Adobe Campaign v8](/help/blueprints/customer-journeys/ajo-and-campaign-v8.md)
   + Campagne v7 {#campaign-v7}
      + [Campagne v7](/help/blueprints/customer-journeys/campaign-v7.md)
      + [Real-Time CDP met Adobe  [!DNL Campaign]  v7](/help/blueprints/customer-journeys/rtcdp-and-campaign.md)
      + [Journey Optimizer met Adobe  [!DNL Campaign]  v7](/help/blueprints/customer-journeys/ajo-and-campaign-v7.md)
+ Gegevensverzameling, Toegang en Exporteren {#data-ingestion}
   + [Overzicht](/help/blueprints/data-ingestion/overview.md)
   + [Het gebeurtenis-door:sturen van meerdere sandbox gegevensinzameling](/help/blueprints/data-ingestion/multi-sandbox-event-forwarding.md)
   + [Gegevensvoorbereiding en -inname](/help/blueprints/data-ingestion/ingestion.md)
   + [Toegang tot en exporteren van gegevens](/help/blueprints/data-ingestion/egress.md)
   + [Gebeurtenis doorsturen](/help/blueprints/data-ingestion/server-side-collection.md)
+ Gegevensanalyse, Intelligentie, en AI/ML {#data-exploration}
   + [Overzicht](/help/blueprints/data-insights/overview.md)
   + [Gegevensanalyse en -intelligentie](/help/blueprints/data-insights/analysis.md)
   + [Aangepaste gegevenswetenschap voor profielverrijking](/help/blueprints/data-insights/data-science.md)
