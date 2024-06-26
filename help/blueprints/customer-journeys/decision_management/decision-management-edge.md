---
title: Beslissingsbeheer voor de Edge-blauwdruk
description: Aangepaste aanbiedingen aan consumenten via verschillende kanalen aanbieden, ook in real-time internet en mobiele ervaringen.
solution: Experience Platform, Journey Optimizer
exl-id: 31e5f624-5578-49e1-ab92-5cabd596a632
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 0%

---

# JOURNEY OPTIMIZER - [!DNL Decision Management] op de rand

[!DNL Decision Management] een dienst is die wordt verleend als onderdeel van [!DNL Journey Optimizer]. Deze blauwdruk schetst de gebruiksgevallen en de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten en overwegingen die omhoog het Beheer van de Beslissing maken.

>[!MORELIKETHIS]
>
>Meer informatie over [!DNL Decision Management], zie de [blauwdruk](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=en) of ga naar [productdocumentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html).

[!DNL Decision Management] kan op twee manieren worden ingezet. De eerste is via de [!DNL Experience Platform] Hub, die één enkele architectuur van het gegevenscentrum is. In de &quot;hub&quot;benadering worden de aanbiedingen uitgevoerd, gepersonaliseerd, en geleverd in tweede latentie. Aldus is de hubarchitectuur het best geschikt voor klantenervaring die geen sub-tweede latentie vereist, omvatten de voorbeelden aanbiedingsbesluiten die voor kiosken of agent bijgewoonde ervaringen zoals in callcenters of in persoonlijke interactie worden verstrekt.

De tweede aanpak is via het Experience Platform [!DNL Edge Network], een wereldwijd gedistribueerde geografisch gesitueerde infrastructuur om snelle sub-seconde en millisecondenervaringen te dienen. De eindgebruikerservaring die wordt uitgevoerd door de Edge-infrastructuur die het dichtst bij de geo-locatie van de consument ligt om de latentie te minimaliseren. [!DNL Decision Management] op de Edge-server is ontworpen om in real-time de ervaringen van de consument te dienen. Deze omvatten ervaringen zoals Web of mobiele binnenkomende verpersoonlijkingsverzoeken.

Deze blauwdruk zal de specifieke details van Beslissingsbeheer op de Rand omvatten.

Meer informatie over het Beheer van het Besluit op de hub verwijst naar [Beslissingsbeheer op de hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=en) blauwdruk.

## Gebruik gevallen voor Beslissingsbeheer aan de rand

* Bij streaming gebruik is de latentie van de profielcontext strikt lager dan 15 minuten latentie en de uitvoering van het beslissingsbeheer subseconden.
* Online personalisatie via internet of mobiele binnenkomende ervaringen.
* Transactieuitvoering via verschillende kanalen - biedt consistentie via internet, mobiele apparaten, e-mail en andere interactiekanalen via Adobe Journey Optimizer.

<br>

## Architectuur

<img src="../assets/offers_edge.svg" alt="Referentie architectuur Beslissingsbeheer op de randblauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Integratiepatronen

| Integratie | Beschrijving |
| :-- | :--- |
| [Beslissingsbeheer met Adobe Target](https://experienceleague.adobe.com/docs/target/using/integrate/ajo/offer-decision.html) | Beslissingsbeheer kan in Adobe Target worden geïntegreerd, zodat aanbiedingen kunnen worden getest en geleverd als ervaringen met het doel. |

## Vereisten

Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u Journey Optimizer gegevensbronnen kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer

<br>

## Guardrails

* Raadpleeg het volgende voor Journey Optimizer-instructies [Journey Optimizer Guardrails](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/limitations.html).

* Raadpleeg de volgende bronnen voor instructies voor het beheer van beslissingen: [Productbeschrijving van Beslissingsbeheer](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html).

[Hulplijnen en advies voor end-to-end latentie](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)


## Implementatiepatronen

* Gebruik het Web of Mobiele SDK voor plaatsing op websites en mobiele toepassingen om Beslissingsbeheer uit te voeren waar SDK opstelde.
   * [Web/Mobile SDK-blauwdruk](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/websdk.html?lang=en)
   * [Web SDK](https://experienceleague.adobe.com/docs/experience-platform/edge/personalization/offer-decisioning/offer-decisioning-overview.html)
   * [MobileSDK](https://aep-sdks.gitbook.io/docs/)

of

* Voor een API-server naar een servergebaseerde implementatie gebruikt u de Edge Network Service API voor directe server-naar-server implementatie van Besluit Management.
   * [Edge Network Server-API](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery/deliver-offers.html)

<br>

## Implementatiestappen

### Adobe Experience Platform

#### Schema/datasets

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

## Gerelateerde documentatie

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer-beslissingsbeheer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Beslissingsbeheer Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
