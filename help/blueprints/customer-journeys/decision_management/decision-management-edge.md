---
title: Beslissingsbeheer betreffende de blauwdruk van Edge
description: Aangepaste aanbiedingen aan consumenten via verschillende kanalen aanbieden, ook in real-time internet en mobiele ervaringen.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: f6c4a0f39acdc177ac23c4314d2f50f793cbf270
workflow-type: tm+mt
source-wordcount: '395'
ht-degree: 0%

---

# Journey Optimizer - [!DNL Decision Management] op de Edge-blauwdruk

[!DNL Decision Management] is een service die wordt aangeboden als onderdeel van [!DNL Journey Optimizer] . Deze blauwdruk schetst de gebruiksgevallen en de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten en overwegingen die omhoog het Beheer van de Beslissing maken.

>[!MORELIKETHIS]
>
>Meer over [!DNL Decision Management] leren, zie het [ blauwdrukoverzicht ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=nl-NL) of bezoek de [ productdocumentatie ](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=nl-NL).

[!DNL Decision Management] kan op twee manieren worden geïmplementeerd. De eerste is via de [!DNL Experience Platform] Hub, die één enkele architectuur van het gegevenscentrum is. In de &quot;hub&quot;benadering worden de aanbiedingen uitgevoerd, gepersonaliseerd, en geleverd in tweede latentie. Aldus is de hubarchitectuur het best geschikt voor klantenervaring die geen sub-tweede latentie vereist, omvatten de voorbeelden aanbiedingsbesluiten die voor kiosken of agent bijgewoonde ervaringen zoals in callcenters of in persoonlijke interactie worden verstrekt.

De tweede aanpak is via het Experience Platform [!DNL Edge Network] , een wereldwijd gedistribueerde geografisch gesitueerde infrastructuur die snelle sub-seconde- en millisecondenervaringen biedt. De eindgebruikerservaring die wordt uitgevoerd door de Edge-infrastructuur die het dichtst bij de geo-locatie van de consument ligt om de latentie tot een minimum te beperken. [!DNL Decision Management] op de Edge is ontworpen om in real-time de ervaringen van de consument te dienen. Deze omvatten ervaringen zoals Web of mobiele binnenkomende verpersoonlijkingsverzoeken.

Deze blauwdruk zal de specifieke kenmerken van het besluitvormingsbeheer op de Edge bestrijken.

Meer over het Beheer van het Besluit op de hub leren verwijs naar het [ Beheer van het Besluit over de hub ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=nl-NL) blauwdruk.

## Gebruik gevallen voor Beslissingsbeheer aan de rand

* Bij streaming gebruik is de latentie van de profielcontext strikt lager dan 15 minuten latentie en de uitvoering van het beslissingsbeheer subseconden.
* Online personalisatie via internet of mobiele binnenkomende ervaringen.
* Transactieuitvoering via verschillende kanalen - biedt consistentie via internet, mobiele apparaten, e-mail en andere interactiekanalen via Adobe Journey Optimizer.

## Architectuur

<img src="../assets/offers_edge.svg" alt="Referentie architectuur Beslissingsbeheer op de randblauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Integratiepatronen

| Integratie | Beschrijving |
| :-- | :--- |
| [ Beheer van het Besluit met Adobe Target ](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html?lang=nl-NL) | Beslissingsbeheer kan in Adobe Target worden geïntegreerd, zodat aanbiedingen kunnen worden getest en geleverd als ervaringen met het doel. |

## Beveiligingsmechanismen

* Voor de guardrails van Journey Optimizer verwijzen naar de volgende [ Guardrails van Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html?lang=nl-NL).

* Voor de gidsen van het Beheer van het Besluit verwijzen naar de volgende [ Beschrijving van het Product van het Beheer van het Besluit ](https://helpx.adobe.com/nl/legal/product-descriptions/offer-decisioning-app-service.html).

[ Guardrails en de Begeleiding van de Latentie van Eind tot Eind ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=nl-NL)

## Gerelateerde documentatie

* [ Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=nl-NL)
* [ Adobe Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer.html?lang=nl-NL)
* [ Adobe Journey Optimizer Beslissingsbeheer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html?lang=nl-NL)
* [ de Beschrijving van het Product van Adobe Journey Optimizer ](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-journey-optimizer.html)
* [ Beschrijving van het Product van het Beheer van het Besluit van de Adobe ](https://helpx.adobe.com/nl/legal/product-descriptions/offer-decisioning-app-service.html)
