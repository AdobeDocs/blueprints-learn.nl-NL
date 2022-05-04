---
title: offer decisioning op de hub
description: Aangepersonaliseerde aanbiedingen aan consumenten aanbieden op verschillende kanalen, waaronder kiosken, ervaringen met assistentie van agenten en in e-mail en andere uitgaande leveringen.
solution: Experience Platform, Journey Optimizer
exl-id: 5a386e18-bbac-4216-a35f-0a5016785e4a
source-git-commit: 494d70fca12a42befb7b726562d98cec17a21d22
workflow-type: tm+mt
source-wordcount: '820'
ht-degree: 0%

---

# Journey Optimizer - Offer decisioning op de hub

Adobe Beslissingsbeheer is een dienst die wordt verleend als onderdeel van Adobe Journey Optimizer. Deze blauwdruk schetst de gebruiksgevallen en de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten en overwegingen die omhoog Offer decisioning maken.

Beslissingsbeheer kan op twee manieren worden ingezet. De eerste is via de Adobe Experience Platform hub, een centrale datacenterarchitectuur. In de &quot;hub&quot;-benadering worden aanbiedingen uitgevoerd, gepersonaliseerd en geleverd met een latentie van > 500 ms. Aldus is de hubarchitectuur het best geschikt voor klantenervaringen die geen sub-tweede latentie vereisen, omvatten de voorbeelden aanbiedingsbesluiten die voor kiosken of agent bijgewoonde ervaringen zoals in callcenters of in persoonlijke interactie worden verstrekt. Aanbiedingen die in e-mail en uitgaande campagnes worden opgenomen worden ook aangedreven door de hubbenadering.

De tweede benadering is via het Edge Network van de Ervaring, dat een wereldwijd gedistribueerde, geografisch gesitueerde infrastructuur is om snelle sub-seconde en milliseconde ervaringen te dienen. De eindgebruikerservaring die wordt uitgevoerd door de randinfrastructuur die het dichtst bij de geo-locatie van de consument ligt om de latentie te minimaliseren. Beslissingsbeheer op de rand is ontworpen om in real-time ervaringen met de consument te bieden, zoals online of mobiele binnenkomende verzoeken om personalisatie.

Deze blauwdruk zal betrekking hebben op de specifieke kenmerken van het beheer van besluiten op de hub.

Raadpleeg voor meer informatie over Beslissingsbeheer op Edge [Beslissingsbeheer aan de rand](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html?lang=en) blauwdruk.

Raadpleeg de productdocumentatie voor meer informatie over Beslissingsbeheer [HIER](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

## Gevallen gebruiken

* Speciale aanbiedingen voor kiosken en winkelervaringen.
* Persoonlijke aanbiedingen via de hulp van een agent, zoals callcenters of verkoopinteracties.
* Aanbiedingen inbegrepen in e-mail, SMS, of andere uitgaande interactie.
* Transactieuitvoering via verschillende kanalen - biedt consistentie via internet, mobiele apparaten, e-mail en andere interactiekanalen via Adobe Journey Optimizer.

<br>

## Architectuur

<img src="../assets/offers_hub.svg" alt="Referentie architectuur Offer decisioning op de randblauwdruk" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Integratiepatronen

| Integratie | Beschrijving |
| :-- | :--- |
| [offer decisioning met Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html) | offer decisioning kan worden geïntegreerd met Adobe Target zodat de aanbiedingen kunnen worden getest en geleverd als ervaringen met het doel. |

## Vereisten

Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u de gegevensbronnen van Journey Optimizer kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer

<br>

## Guardrails

* Raadpleeg het volgende voor Journey Optimizer-instructies [Journey Optimizer Guardrails](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).
* Raadpleeg de volgende bronnen voor Offer decisioning [Productbeschrijving offer decisioning](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).


### Gegevensinname Guardraals

<img src="../assets/aep-data-ingestion-details-latency.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:80%; border:1px solid #4a4a4a" />

<br>

### Activeringsinstructies

<img src="../assets/ajo-activation-details-latency.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Implementatiepatronen

* Geïmplementeerd in e-mail, SMS, en uitgaande kanalen via directe integratie met [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/offers-e2e.html).
* Voor server-API-implementatie gebruikt u de functie [API voor besluitvorming](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/decisioning-vs-edge-apis.html).
* Voor implementatie van batchgewijs besluit om aanbiedingen in bulk aan een toepassing van de berichtlevering te leveren gebruik [Batchbeslissing-API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/batch-decisioning-api.html).
* Voor op rand gebaseerde real-time ervaringen gebruikt u de Web/Mobile SDK of de Edge Decisioning API zoals beschreven in de [offer decisioning op de Edge-blauwdruk](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/offer-decisioning/offers-edge.html).
<br>

## Implementatiestappen

### Adobe Experience Platform

#### Schema/gegevensset

1. [Afzonderlijke profiel-, ervarings- en multientiteitsschema&#39;s configureren](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, op basis van door de klant verstrekte gegevens.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) in Experience Platform voor gegevens die moeten worden ingevoerd.
1. [Labels voor gegevensgebruik toevoegen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform met de dataset voor bestuur.
1. [Beleid maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html) de handhaving van het bestuur op bestemmingen.

#### Profiel/identiteit

1. [Maak klantspecifieke naamruimten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Identiteiten toevoegen aan schema&#39;s](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [De schema&#39;s en datasets voor Profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Samenvoegbeleid instellen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) voor verschillende weergaven van [!UICONTROL Klantprofiel in realtime] (optioneel).
1. Maak segmenten voor gebruik in Reis.

#### Bronnen/bestemmingen

1. [Gegevens in Experience Platform opnemen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) via streaming API&#39;s en bronconnectors.

## Verwante documentatie

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer-beslissingsbeheer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Productbeschrijving Adobe Offer decisioning](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
