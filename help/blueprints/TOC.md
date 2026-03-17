---
user-guide-title: Zakelijke doelstellingen van Customer Experience Orchestration, Gebruiksscenario's, Architectuurdiagrammen en -blauwdrukken
breadcrumb-title: Gevallen en blauwdrukken gebruiken
user-guide-description: Belangrijke bedrijfsdoelstellingen, gebruikspatronen, en industrie gebruiken gevallen voor Adobe Experience Platform en toepassingen onderzoeken. De visuele architectuurdiagrammen en de blauwdrukken verstrekken technische verwijzingen voor systeemintegratie, gegevensstromen, en oplossingsontwerp — verbindend bedrijfswaarde met implementatie.
product: adobe experience platform
mini-toc-levels: 3
role: Developer, User
source-git-commit: 8ad59ff130dae13553f10049eb685cf557a73ead
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 7%

---


# Klantenervaring met orkesttekeningen {#architecture}

+ [Klantenervaring met orkesttekeningen](/help/blueprints/overview.md)
+ Belangrijkste bedrijfsdoelstellingen voor AEP en toepassingen{#business-objectives}
   + [Overzicht](/help/blueprints/business-objectives/overview.md)
   + Verwerving en groei{#acquisition-growth}
      + [Nieuwe klanten ophalen](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)
      + [Loodgeneratie verhogen](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)
      + [Betrokkenheid van website verhogen](/help/blueprints/business-objectives/acquisition-growth/increase-website-engagement.md)
   + Opbrengsten en inkomsten{#revenue-monetization}
      + [Conversietarieven verhogen](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)
      + [Opbrengst en verkoop verhogen](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)
      + [Opbrengsten voor cross-selling en upsell](/help/blueprints/business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)
      + [Klantengarantie en levensduurwaarde verhogen](/help/blueprints/business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)
   + Kosten en efficiëntie{#cost-efficiency}
      + [Kostprijs voor overname door klant verlagen](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)
      + [Marketing-uitgaven en investeringsrendement optimaliseren](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)
      + [Kwaliteit en beheer van gegevens verbeteren](/help/blueprints/business-objectives/cost-efficiency/improve-data-quality-governance.md)
      + [Consolidatie en modernisering van marketingtechnologie](/help/blueprints/business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md)
   + Klantervaring{#customer-experience-objectives}
      + [Lever persoonlijke klantervaring](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)
      + [Behoud van klant verbeteren](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)
      + [Klant beter instappen](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)
      + [Verlaten karretjes en reizen herstellen](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)
   + Analyse en inzichten{#analytics-insights}
      + [Analyse en rapportage verbeteren](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)
      + [Gegevensgestuurde besluitvorming inschakelen](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)
      + [Marketingkenmerken verbeteren](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md)
   + Kwalificatie en verkoop (B2B){#qualification-sales-b2b}
      + [Kwalificatie en conversie van lead verbeteren](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)
      + [Betrokkenheid van klanten verbeteren](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)
+ Hoofdletterpatronen gebruiken{#use-case-patterns}
   + [Overzicht](/help/blueprints/use-case-patterns/overview.md)
   + Audience Building &amp; Activation{#audience-building-activation}
      + [Audience Activation naar bestemmingen](/help/blueprints/use-case-patterns/audience-building-activation/audience-activation-to-destinations.md)
      + [Publiek Collaboration met segmentovereenkomst](/help/blueprints/use-case-patterns/audience-building-activation/audience-collaboration-segment-match.md)
      + [Gebeurtenis doorsturen](/help/blueprints/use-case-patterns/audience-building-activation/event-forwarding.md)
      + [B2B Audience Activation](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md)
   + Personalisatie{#personalization-patterns}
      + [Anonieme bezoeker van Web Personalization](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md)
      + [Bekende bezoeker Web/App Personalization](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md)
      + [Besluitvorming over aanbiedingen](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md)
      + [Gedragsaanbeveling](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md)
   + Campagne management &amp; Orchestration{#campaign-orchestration-patterns}
      + [Batch Outbound Message Activation](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md)
      + [Gebeurtenisgestuurde berichten](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md)
      + [Meerdere stappen geordende reis](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md)
      + [Kanaalreis met beslissing](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md)
      + [Op groep gebaseerde marketing en reisbeheer kopen](/help/blueprints/use-case-patterns/campaign-management-orchestration/buying-group-based-marketing.md)
   + Analyse{#analysis-patterns}
      + [Klantenanalyse en Insight Generation](/help/blueprints/use-case-patterns/analysis/customer-analytics-insight-generation.md)
      + [B2B-analyse](/help/blueprints/use-case-patterns/analysis/b2b-analytics.md)
   + Gesprekkervaring{#conversational-experience-patterns}
      + [Brand Concierge Conversation Experience](/help/blueprints/use-case-patterns/conversational-experience/brand-concierge-conversational-experience.md)
+ Voorbeelden van gevallen van industriële toepassing{#industry-use-cases}
   + [Overzicht](/help/blueprints/industry-use-cases/overview.md)
   + [Hoofdlettercatalogus gebruiken](/help/blueprints/industry-use-cases/use-case-catalog.md)
   + [Automobielen](/help/blueprints/industry-use-cases/automotive/automotive-overview.md)
   + [B2B](/help/blueprints/industry-use-cases/b2b/b2b-overview.md)
   + [Financiële diensten](/help/blueprints/industry-use-cases/financial-services/financial-services-overview.md)
   + [Gezondheidszorg](/help/blueprints/industry-use-cases/healthcare/healthcare-overview.md)
   + [Verzekering](/help/blueprints/industry-use-cases/insurance/insurance-overview.md)
   + [Media en entertainment](/help/blueprints/industry-use-cases/media-entertainment/media-entertainment-overview.md)
   + [Retail](/help/blueprints/industry-use-cases/retail/retail-overview.md)
   + [Telecommunicatie](/help/blueprints/industry-use-cases/telecommunications/telecommunications-overview.md)
   + [Reizen en verblijf](/help/blueprints/industry-use-cases/travel-hospitality/travel-hospitality-overview.md)
+ Architectuurdiagrammen en blauwdrukken{#architecture-diagrams}
   + Architectuur-overzichten{#architecture-overview}
      + [Experience Cloud](/help/blueprints/experience-platform/experience-cloud.md)
      + [Experience Platform en toepassingen](/help/blueprints/experience-platform/platform-applications.md)
      + [Experience Platform-gegevensstroom](/help/blueprints/experience-platform/platform-data-flow.md)
      + [Experience Platform guardrails](/help/blueprints/experience-platform/guardrails.md)
      + Implementatie{#deployment}
         + [Experience Platform Web SDK &amp; [!DNL Edge Network]](/help/blueprints/experience-platform/deployment/websdk.md)
         + [SDK&#39;s voor toepassingen](/help/blueprints/experience-platform/deployment/appsdk.md)
   + Activering publiek en profiel{#audience-activation}
      + [Op apparaat gebaseerd - Anonieme doelgroep voor Audience Manager](/help/blueprints/audience-activation/audience-manager.md)
      + Real-Time Customer Data Platform (RTCDP) {#known-customer-audience-activation}
         + [Activering van het publiek naar sociale en reclamebestemmingen](/help/blueprints/audience-activation/advertising-activation.md)
         + [Activering van publiek en profiel voor ondernemingdoelen blauwdruk](/help/blueprints/audience-activation/enterprise-destinations.md)
         + [Realtime profieltoegang voor steun en verkoopscenario&#39;s](/help/blueprints/audience-activation/customer-activity.md)
         + [Toegang tot Edge-profielen in realtime voor web en mobiele personalisatie](/help/blueprints/audience-activation/real-time-lookup.md)
         + [Samenwerking van het publiek met de Gelijke van het Segment](/help/blueprints/audience-activation/segment-match.md)
         + [Bekende klantenverpersoonlijking met Doel](/help/blueprints/audience-activation/rtcdp-target.md)
         + [Aangepaste gegevenswetenschap voor profielverrijking](/help/blueprints/audience-activation/data-science.md)
   + B2B-activering en -marketing{#b2b-activation}
      + [Overzicht](/help/blueprints/b2b/overview.md)
      + [B2B-activering](/help/blueprints/b2b/b2bactivation.md)
      + [B2B-rekeningactivering](/help/blueprints/b2b/b2b-account-activation.md)
      + [Op groepsbasis kopen van marketing en reisbeheer](/help/blueprints/b2b/b2b-buying-group-journeys.md)
      + [B2B-reizen met Marketo-gegevens](/help/blueprints/b2b/b2b-journeys-with-marketo.md)
      + [B2B Betaalde mediacontrole](/help/blueprints/b2b/ajo-b2b-paid-media-controller.md)
      + Integratieblauwdruk voor Marketo Engage en Workfront{#marketo-engage-and-workfront-integration-blueprint}
         + [Overzicht](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/overview.md)
         + [Innemen en maken](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/intake-and-create.md)
         + [Reviseren en goedkeuren](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/review-and-approve-blueprint.md)
         + [Succesverhalen van klanten](/help/blueprints/b2b/marketo-engage-and-workfront-integration-blueprint/customer-success-stories.md)
   + Customer Journey Analytics{#customer-journey-analytics}
      + [Overzicht](/help/blueprints/customer-journey-analytics/overview.md)
      + [B2B Customer Journey Analytics](/help/blueprints/customer-journey-analytics/b2b-cja.md)
      + [CJA-publiek delen met RTCDP](/help/blueprints/customer-journey-analytics/cja-rtcdp.md)
      + [CJA en Journey Optimizer](/help/blueprints/customer-journey-analytics/cja-ajo.md)
      + [Gegevensanalyse en -intelligentie](/help/blueprints/customer-journey-analytics/analysis.md)
   + Reizen van klanten{#customer-journeys}
      + [Overzicht](/help/blueprints/customer-journeys/overview.md)
      + Journey Optimizer{#journey-optimizer}
         + [Journey Optimizer](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md)
         + [AJO-reizen](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-journeys.md)
         + [AJO-campagnes](/help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-campaigns.md)
         + [Berichten van derden](/help/blueprints/customer-journeys/journey-optimizer/3rd-party-messaging.md)
      + Beslissingsbeheer{#decision-management}
         + [Overzicht](/help/blueprints/customer-journeys/decision-management/decision-management-overview.md)
         + [Beslissingsbeheer in Edge](/help/blueprints/customer-journeys/decision-management/decision-management-edge.md)
         + [Beslissingsbeheer op de hub](/help/blueprints/customer-journeys/decision-management/decision-management-hub.md)
      + Campaign v8{#campaign-v8}
         + [Campaign v8](/help/blueprints/customer-journeys/campaign-v8/campaign-v8-overview.md)
         + [Real-Time CDP met Adobe  [!DNL Campaign]  v8](/help/blueprints/customer-journeys/campaign-v8/rtcdp-and-campaign-v8.md)
         + [Journey Optimizer met Adobe Campaign v8](/help/blueprints/customer-journeys/campaign-v8/ajo-and-campaign-v8.md)
      + Verouderde blauwdrukken{#deprecated-blueprints}
         + Campaign Standard{#campaign-standard}
            + [[!DNL Campaign Standard]](https://experienceleague.adobe.com/en/docs/campaign-standard){target="_blank"}
            + [Real-Time CDP met Adobe  [!DNL Campaign Standard]](https://experienceleague.adobe.com/en/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/get-started-sources-destinations)
         + Campagne v7{#campaign-v7}
            + [Campagne v7](/help/blueprints/customer-journeys/campaign-v7/campaign-v7-overview.md)
