---
title: Hoofdlettercatalogus gebruiken
description: Doorblader de gevallen van het industrietak door verticaal, rijpingsniveau, of implementatiepatroon om het juiste uitgangspunt voor uw reis van Adobe Experience Platform te vinden.
doc-type: overview-page
exl-id: 7a3c2f1e-9b4d-4e6a-8f5c-2d1b3a4e7c9f
source-git-commit: 8ad59ff130dae13553f10049eb685cf557a73ead
workflow-type: tm+mt
source-wordcount: '1022'
ht-degree: 6%

---

# Hoofdlettercatalogus gebruiken

Ontdek de gebruiksmogelijkheden van de industrie voor [!DNL Adobe Experience Platform] en toepassingen. Blader door de branche om de gebruiksgevallen voor uw verticaal weer te geven, door het ontwikkelingsniveau om het juiste beginpunt voor uw organisatie te vinden of door het implementatiepatroon om te begrijpen welke technische aanpak bij uw behoeften past.

Elke gebruikscase verbindt met gedetailleerde implementatierichtsnoeren door een gebruikscatroon, dat de functieketen, beslissingspunten, en configuratiestappen beschrijft nodig om het gebruiksgeval tot leven te brengen.

## Bladeren door industrie

>[!BEGINTABS]

>[!TAB  Detailhandel ]

Commerciële organisaties gebruiken [!DNL Adobe Experience Platform] om klantgegevens van online winkels, fysieke plaatsen, en loyaliteitsprogramma&#39;s in één enkele mening van elke verkoopster te verenigen.

| | Gebruiksscenario | Beschrijving | Looptijd | Patroon |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Aanbevelingen voor gepersonaliseerde producten" width="40"> | [&#x200B; Persoonlijke Aanbevelingen van het Product &#x200B;](retail/retail-overview.md#personalized-product-recommendations) | Persoonlijke producten weergeven op basis van bladeren en aankoopgeschiedenis | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | [&#x200B; Aanbeveling van het Gedrag &#x200B;](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Verlaten wagen" width="40"> | [&#x200B; Verlaten E-mailterugwinning van de Kar &#x200B;](retail/retail-overview.md#abandoned-cart-email-recovery) | Aangepaste herinneringen verzenden voor verlaten winkelwagentjes | [!BADGE &#x200B; Foundational &#x200B;]{type=Neutral} | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Voorraadurgentie" width="40"> | [&#x200B; op inventaris-Gebaseerde Urgentiecampagnes &#x200B;](retail/retail-overview.md#inventory-based-urgency-campaigns) | Waarschuwing in real time activeren wanneer de productvoorraad laag is | [!BADGE &#x200B; Foundational &#x200B;]{type=Neutral} | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Crossverkoop Upsell" width="40"> | [&#x200B; Verkoop en upload Aanbevelingen &#x200B;](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Toon relevante cross-sell en upsell producten bij kassa en in e-mail | [!BADGE &#x200B; Geavanceerd &#x200B;]{type=Caution} | [&#x200B; Offer Decisioning &#x200B;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Welkomstserie" width="40"> | [&#x200B; Nieuwe het Welkome Reeks van de Klant &#x200B;](retail/retail-overview.md#new-customer-welcome-series) | Automatiseer een welkomstserie voor meerdere e-mails met gepersonaliseerde aanbevelingen | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Prijsdaling" width="40"> | [&#x200B; de Daling van de Prijs Alarm &#x200B;](retail/retail-overview.md#price-drop-alerts) | Klanten op de hoogte stellen wanneer verlanglijst of bekeken objecten in prijs dalen | [!BADGE &#x200B; Foundational &#x200B;]{type=Neutral} | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Aanvulling" width="40"> | [&#x200B; HervormingsHerinneringen &#x200B;](retail/retail-overview.md#replenishment-reminders) | Verzend geautomatiseerde herinneringen voor regelmatig gekochte verbruiksproducten | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Categoriepagina&#39;s" width="40"> | [&#x200B; Gepersonaliseerde Pagina&#39;s van de Categorie &#x200B;](retail/retail-overview.md#personalized-category-pages) | Categoriepagina&#39;s dynamisch opnieuw ordenen op basis van de voorkeuren van elke klant | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | [&#x200B; Aanbeveling van het Gedrag &#x200B;](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Na aankoop" width="40"> | [&#x200B; follow-up campagnes post-Purchase &#x200B;](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Zorgtips, revisieverzoeken en verwante productsuggesties verzenden | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [&#x200B; Exclusieve Aanbiedingen van de Klant van VIP &#x200B;](retail/retail-overview.md#vip-customer-exclusive-offers) | Exclusieve aanbiedingen en vroege toegang tot klanten met een hoge waarde | [!BADGE &#x200B; Geavanceerd &#x200B;]{type=Caution} | [&#x200B; Reis van het Kanaal met Beslissing &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| | [&#x200B; uit-van-voorraad Meldingen &#x200B;](retail/retail-overview.md#out-of-stock-notifications) | Klanten op de hoogte stellen wanneer producten uit de voorraad beschikbaar komen | [!BADGE &#x200B; Foundational &#x200B;]{type=Neutral} | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [&#x200B; Sociale Bewijs Personalization &#x200B;](retail/retail-overview.md#social-proof-personalization) | Persoonlijke revisies en beoordelingen weergeven op basis van het klantprofiel | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | [&#x200B; gekend-Bezoeker Web/App Personalization &#x200B;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB  Financiële Diensten ]

Er komen binnenkort gevallen van gebruik van financiële diensten. [De huidige het gebruiksgevallen van Financiële Diensten van de Mening &#x200B;](financial-services/financial-services-overview.md).

>[!TAB  Gezondheidszorg ]

Er komen binnenkort gevallen van gebruik in de gezondheidszorg. [Huidige de gebruiksgevallen van de Gezondheidszorg van de Mening &#x200B;](healthcare/healthcare-overview.md).

>[!TAB  Automobielindustrie ]

Er komen binnenkort gevallen van autogebruik. [Huidige Gebruiksgevallen voor motorvoertuigen weergeven &#x200B;](automotive/automotive-overview.md).

>[!TAB  Reizen &amp; Ziekenplaats ]

Reis- en ziekenhuisgevallen komen binnenkort. [Huidige gevallen van reizen en gebruik van ziekenhuisopnamen weergeven &#x200B;](travel-hospitality/travel-hospitality-overview.md).

>[!TAB  Telecommunicatie ]

Er komen binnenkort gevallen van telecommunicatiegebruik. [De huidige het gebruiksgevallen van Telecommunicatie van de mening &#x200B;](telecommunications/telecommunications-overview.md).

>[!TAB  Media &amp; Entertainment ]

Er komen binnenkort gevallen van media- en entertainmentgebruik. [Huidige Media en het gebruiksgevallen van het Entertainment &#x200B;](media-entertainment/media-entertainment-overview.md) bekijken.

>[!TAB  Verzekering ]

Verzekeringskwesties komen binnenkort aan de orde. [Huidige gevallen van verzekeringsgebruik weergeven &#x200B;](insurance/insurance-overview.md).

>[!TAB  B2B ]

Er komen binnenkort gevallen van B2B-gebruik. [Huidige B2B gebruiksgevallen &#x200B;](b2b/b2b-overview.md) bekijken.

>[!ENDTABS]

## Bladeren op ontwikkelingsniveau

>[!BEGINTABS]

>[!TAB  Foundational ]

Basis, bewezen patronen die levering met één kanaal gebruiken. Ideale uitgangspunten voor organisaties die hun [!DNL Experience Platform] reis beginnen.

| | Gebruiksscenario | Industrie | Zakelijke impact | Patroon |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Verlaten wagen" width="40"> | [&#x200B; Verlaten E-mailterugwinning van de Kar &#x200B;](retail/retail-overview.md#abandoned-cart-email-recovery) | Retail | 25-35% herstelpercentage voor kar | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Voorraadurgentie" width="40"> | [&#x200B; op inventaris-Gebaseerde Urgentiecampagnes &#x200B;](retail/retail-overview.md#inventory-based-urgency-campaigns) | Retail | Conversie met 30-40% verhoogd | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Prijsdaling" width="40"> | [&#x200B; de Daling van de Prijs Alarm &#x200B;](retail/retail-overview.md#price-drop-alerts) | Retail | 20-30% conversiesnelheid | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| | [&#x200B; uit-van-voorraad Meldingen &#x200B;](retail/retail-overview.md#out-of-stock-notifications) | Retail | Conversie van 40-50% | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |

>[!TAB  Opkomende ]

Multikanaal en multi-step patronen die voortbouwen op grondmogelijkheden met AI-gedreven personalisering en georkestreerde reizen.

| | Gebruiksscenario | Industrie | Zakelijke impact | Patroon |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Aanbevelingen voor producten" width="40"> | [&#x200B; Persoonlijke Aanbevelingen van het Product &#x200B;](retail/retail-overview.md#personalized-product-recommendations) | Retail | 20-30% toename van CTR, 15-25% conversielift | [&#x200B; Aanbeveling van het Gedrag &#x200B;](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Categoriepagina&#39;s" width="40"> | [&#x200B; Gepersonaliseerde Pagina&#39;s van de Categorie &#x200B;](retail/retail-overview.md#personalized-category-pages) | Retail | 25-35% toename in betrokkenheid | [&#x200B; Aanbeveling van het Gedrag &#x200B;](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Welkomstserie" width="40"> | [&#x200B; Nieuwe het Welkome Reeks van de Klant &#x200B;](retail/retail-overview.md#new-customer-welcome-series) | Retail | 40-50% betrokkenheidsgraad | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Aanvulling" width="40"> | [&#x200B; HervormingsHerinneringen &#x200B;](retail/retail-overview.md#replenishment-reminders) | Retail | Aankoopsnelheid 30-40% herhalen | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Na aankoop" width="40"> | [&#x200B; follow-up campagnes post-Purchase &#x200B;](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Retail | Herzieningspercentage van 15-20%, 10-15% herhaal aankoop | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| | [&#x200B; Sociale Bewijs Personalization &#x200B;](retail/retail-overview.md#social-proof-personalization) | Retail | 10-15% stijging van de conversiesnelheid | [&#x200B; gekend-Bezoeker Web/App Personalization &#x200B;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

>[!TAB  Geavanceerd ]

Kanaaloverschrijdende organisatie met real-time besluitvorming en door AI gedreven aanbiedingsselectie voor de verfijnde klantenervaringen.

| | Gebruiksscenario | Industrie | Zakelijke impact | Patroon |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Crossverkoop Upsell" width="40"> | [&#x200B; Verkoop en upload Aanbevelingen &#x200B;](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Retail | $25-$75 verhoging van AOV, 10-15% opbrengstverhoging | [&#x200B; Offer Decisioning &#x200B;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| | [&#x200B; Exclusieve Aanbiedingen van de Klant van VIP &#x200B;](retail/retail-overview.md#vip-customer-exclusive-offers) | Retail | 50-70% betrokkenheidsgraad van VIP&#39;s | [&#x200B; Reis van het Kanaal met Beslissing &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |

>[!ENDTABS]

## Bladeren op implementatiepatroon

>[!BEGINTABS]

>[!TAB  Beheer &amp; Orchestratie van de Campagne ]

### Gebeurtenisgestuurde berichten

Reageer op gedragsgebeurtenissen in real time met geschikte, single-channel berichten.

| | Gebruiksscenario | Industrie | Looptijd | Zakelijke impact |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-abandoned-cart.png" alt="Verlaten wagen" width="40"> | [&#x200B; Verlaten E-mailterugwinning van de Kar &#x200B;](retail/retail-overview.md#abandoned-cart-email-recovery) | Retail | [!BADGE &#x200B; Foundational &#x200B;]{type=Neutral} | 25-35% herstelpercentage voor kar |
| <img src="assets/use-case-icons/icon-inventory-urgency.png" alt="Voorraadurgentie" width="40"> | [&#x200B; op inventaris-Gebaseerde Urgentiecampagnes &#x200B;](retail/retail-overview.md#inventory-based-urgency-campaigns) | Retail | [!BADGE &#x200B; Foundational &#x200B;]{type=Neutral} | Conversie met 30-40% verhoogd |
| <img src="assets/use-case-icons/icon-price-drop.png" alt="Prijsdaling" width="40"> | [&#x200B; de Daling van de Prijs Alarm &#x200B;](retail/retail-overview.md#price-drop-alerts) | Retail | [!BADGE &#x200B; Foundational &#x200B;]{type=Neutral} | 20-30% conversiesnelheid |
| | [&#x200B; uit-van-voorraad Meldingen &#x200B;](retail/retail-overview.md#out-of-stock-notifications) | Retail | [!BADGE &#x200B; Foundational &#x200B;]{type=Neutral} | Conversie van 40-50% |

### Meerdere stappen geordende reis

De klanten door multi-aanrakingsopeenvolgingen begeleiden die zich op overeenkomst en gedrag aanpassen.

| | Gebruiksscenario | Industrie | Looptijd | Zakelijke impact |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-welcome-series.png" alt="Welkomstserie" width="40"> | [&#x200B; Nieuwe het Welkome Reeks van de Klant &#x200B;](retail/retail-overview.md#new-customer-welcome-series) | Retail | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | 40-50% betrokkenheidsgraad |
| <img src="assets/use-case-icons/icon-replenishment.png" alt="Aanvulling" width="40"> | [&#x200B; HervormingsHerinneringen &#x200B;](retail/retail-overview.md#replenishment-reminders) | Retail | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | Aankoopsnelheid 30-40% herhalen |
| <img src="assets/use-case-icons/icon-post-purchase.png" alt="Na aankoop" width="40"> | [&#x200B; follow-up campagnes post-Purchase &#x200B;](retail/retail-overview.md#post-purchase-follow-up-campaigns) | Retail | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | Herzieningspercentage van 15-20%, 10-15% herhaal aankoop |

### Kanaalreis met beslissing

Orchestrate cross-channel ervaringen met real-time aanbiedingen voor beslissingen op elk aanraakpunt.

| | Gebruiksscenario | Industrie | Looptijd | Zakelijke impact |
| --- | --- | --- | --- | --- |
| | [&#x200B; Exclusieve Aanbiedingen van de Klant van VIP &#x200B;](retail/retail-overview.md#vip-customer-exclusive-offers) | Retail | [!BADGE &#x200B; Geavanceerd &#x200B;]{type=Caution} | 50-70% betrokkenheidsgraad van VIP&#39;s |

>[!TAB  Personalization ]

### Gedragsaanbeveling

Gebruik door AI aangedreven modellen om gepersonaliseerde inhoud en producten aan de oppervlakte te brengen die op gedragssignalen worden gebaseerd.

| | Gebruiksscenario | Industrie | Looptijd | Zakelijke impact |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-product-recommendations.png" alt="Aanbevelingen voor producten" width="40"> | [&#x200B; Persoonlijke Aanbevelingen van het Product &#x200B;](retail/retail-overview.md#personalized-product-recommendations) | Retail | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | 20-30% toename van CTR, 15-25% conversielift |
| <img src="assets/use-case-icons/icon-category-pages.png" alt="Categoriepagina&#39;s" width="40"> | [&#x200B; Gepersonaliseerde Pagina&#39;s van de Categorie &#x200B;](retail/retail-overview.md#personalized-category-pages) | Retail | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | 25-35% toename in betrokkenheid |

### Besluitvorming over aanbiedingen

Gebruik gecentraliseerde besluitvormingslogica om de beste aanbieding voor elke klant en context te evalueren en te selecteren.

| | Gebruiksscenario | Industrie | Looptijd | Zakelijke impact |
| --- | --- | --- | --- | --- |
| <img src="assets/use-case-icons/icon-cross-sell-upsell.png" alt="Crossverkoop Upsell" width="40"> | [&#x200B; Verkoop en upload Aanbevelingen &#x200B;](retail/retail-overview.md#cross-sell-and-upsell-recommendations) | Retail | [!BADGE &#x200B; Geavanceerd &#x200B;]{type=Caution} | $25-$75 verhoging van AOV, 10-15% opbrengstverhoging |

### Bekende bezoeker Web/App Personalization

Het web en de inhoud van de app aanpassen voor bepaalde bezoekers op basis van profiel, voorkeuren en bladercontext.

| | Gebruiksscenario | Industrie | Looptijd | Zakelijke impact |
| --- | --- | --- | --- | --- |
| | [&#x200B; Sociale Bewijs Personalization &#x200B;](retail/retail-overview.md#social-proof-personalization) | Retail | [!BADGE &#x200B; Opkomende &#x200B;]{type=Informative} | 10-15% stijging van de conversiesnelheid |

>[!ENDTABS]
