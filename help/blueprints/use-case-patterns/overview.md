---
title: Hoofdletterpatronen gebruiken
description: Leer meer over de gebruikspatronen voor het implementeren van Adobe Experience Platform en toepassingen om belangrijke bedrijfsdoelstellingen te bereiken.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
doc-type: overview-page
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '492'
ht-degree: 0%

---


# Hoofdletters gebruiken

Met gebruikspatronen worden herhaalbare implementatiebenaderingen voor Adobe Experience Platform en toepassingen gedefinieerd. Elk patroon beschrijft een specifiek vermogen, de functieketen die het, de betrokken toepassingen, en de [ zeer belangrijke bedrijfsdoelstellingen ](/help/blueprints/business-objectives/overview.md) levert het steunt.

Gebruik de onderstaande tabellen om het patroon te vinden dat aansluit bij uw implementatiebehoeften en volg vervolgens de koppeling naar de volledige implementatieverwijzing, inclusief opties, fasen, beslissingsbegeleiding en Experience League-documentatie.

## Auditieopbouw en activering

De volgende patronen helpen u, publiekssegmenten over kanalen en bestemmingen bouwen evalueren en activeren.

| Patroon | Primaire capaciteit | Kernoplossingen |
| --- | --- | --- |
| [ Audience Activation aan Doelen ](audience-building-activation/audience-activation-to-destinations.md) | Evalueer en publiceer publiekssegmenten aan externe bestemmingen voor het richten of onderdrukken | [!DNL Real-Time CDP] |
| [ Collaboration van het publiek met de Overeenkomst van het Segment ](audience-building-activation/audience-collaboration-segment-match.md) | publiekssegmenten delen en afstemmen in sandboxen of organisaties met gebruik van Segment afstemmen | [!DNL Real-Time CDP], [!DNL Experience Platform] |
| [ Gebeurtenis door:sturen ](audience-building-activation/event-forwarding.md) | Gegevens in real time die via Edge Network zijn verzameld, doorsturen naar bestemmingen buiten Adobe | [!DNL Experience Platform] (Edge Network, gebeurtenis die wordt doorgestuurd) |
| [ B2B Audience Activation ](audience-building-activation/b2b-audience-activation.md) | B2B-publiek op basis van account activeren via web-, e-mail- en advertentiekanalen | [!DNL Real-Time CDP] B2B edition |

## Personalisatie

De volgende patronen bieden bekende en onbekende bezoekers op het web en in apps een op maat gemaakte ervaring.

| Patroon | Primaire capaciteit | Kernoplossingen |
| --- | --- | --- |
| [ Anonieme Personalization van het Web van de Bezoeker ](personalization/anonymous-visitor-web-personalization.md) | Aangepaste inhoud leveren op basis van gedragssignalen tijdens de sessie voor niet-geïdentificeerde bezoekers | [!DNL Journey Optimizer] (webkanaal), [!DNL Real-Time CDP] |
| [ gekend-Bezoeker Web/App Personalization ](personalization/known-visitor-web-app-personalization.md) | Aangepaste inhoud, aanbiedingen of promoties aan bepaalde bezoekers leveren op basis van realtime profiel en segmentlidmaatschap | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [ Offer Decisioning ](personalization/offer-decisioning.md) | Gebruik gecentraliseerde besluitvormingslogica om de volgende beste aanbieding of inhoud voor een profiel over kanalen te selecteren | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |
| [ Aanbeveling van het Gedrag ](personalization/behavioral-recommendation.md) | Aanbevelingen voor item en inhoud genereren met behulp van selectiestrategieën en waarderingsmodellen | [!DNL Journey Optimizer] (Decisioning), [!DNL Real-Time CDP] |

## Campagne beheren en organiseren

De volgende patronen behandelen geplande, teweeggebrachte, en multi-step berichtlevering over kanalen.

| Patroon | Primaire capaciteit | Kernoplossingen |
| --- | --- | --- |
| [ Uitgaande Activering van het Bericht van de Partij ](campaign-management-orchestration/batch-outbound-message-activation.md) | Evalueer een publiek, dan leveren een gepland uitgaand bericht in één enkele partijuitvoering | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [ gebeurtenis-teweeggebracht Overseinen ](campaign-management-orchestration/event-triggered-messaging.md) | Luisteren naar een realtime gedrags- of systeemgebeurtenis en vervolgens een contextueel bericht verzenden naar het activeringsprofiel | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [ Multi-Step Orchestrated Reis ](campaign-management-orchestration/multi-step-orchestrated-journey.md) | Een profiel begeleiden door een vertakkende multitouch-reis met wachten, voorwaarden en meerdere berichthandelingen | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [ Reis van het Kanaal met Beslissing ](campaign-management-orchestration/cross-channel-journey-with-decisioning.md) | Orchestreer een multi-step reis die Beslissing in real time omvat om optimaal kanaal, inhoud, of aanbieding te selecteren | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
| [ het Kopen op groep-Gebaseerde Marketing &amp; het Beheer van de Reis ](campaign-management-orchestration/buying-group-based-marketing.md) | Reizen op rekeningniveau ontwikkelen die geschikt zijn voor leads naar inkoopgroepen om B2B-marketing effectiever te maken | [!DNL Journey Optimizer] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Analyse

De volgende patronen ondersteunen kanaalanalyse van gedrag en prestaties.

| Patroon | Primaire capaciteit | Kernoplossingen |
| --- | --- | --- |
| [ Analytics van de Klant &amp; Generation van Insight ](analysis/customer-analytics-insight-generation.md) | De werkruimten voor kanaalanalyse, berekende metriek en dashboards maken voor gedrags- en prestatieanalyse | [!DNL Customer Journey Analytics], [!DNL Experience Platform] |
| [ B2B Analytics ](analysis/b2b-analytics.md) | B2B-informatie op accountniveau opnemen in de analyse van klantentransacties over meerdere kanalen | [!DNL Customer Journey Analytics] B2B edition, [!DNL Real-Time CDP] B2B edition |

## Gesprekkervaring

De volgende patronen maken door AI aangedreven, brandveilige conversatie-interacties op digitale eigenschappen mogelijk.

| Patroon | Primaire capaciteit | Kernoplossingen |
| --- | --- | --- |
| [ de Conversationele Ervaring van Brand Concierge ](conversational-experience/brand-concierge-conversational-experience.md) | Digitale eigenschappen omzetten in door AI aangedreven, merkveilige gesprekservaringen die klanten helpen om te ontdekken | [!DNL Brand Concierge], [!DNL Experience Platform], [!DNL Real-Time CDP] |
