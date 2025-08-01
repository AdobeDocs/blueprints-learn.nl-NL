---
title: Journey Optimizer - blauwdruk voor communicatie van derden
description: Toont aan hoe Adobe Journey Optimizer met de systemen van het derdeoverseinen kan worden gebruikt om gepersonaliseerde mededelingen te ordenen en te verzenden.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 2%

---

# Blauwdruk voor berichten van derden

Toont aan hoe Adobe Journey Optimizer met de systemen van het derdeoverseinen kan worden gebruikt om gepersonaliseerde mededelingen te ordenen en te verzenden.

<br>

## Architectuur

<img src="assets/3rd-party-messaging-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Vereisten

Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u Journey Optimizer gegevensbronnen kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer

Andere toepassing voor berichten

* Moet REST API-aanroepen ondersteunen voor het verzenden van transactiebetalingen

<br>

## Beveiligingsmechanismen

[ Journey Optimizer Guardrails Product Link ](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)

[ Guardrails en de Begeleiding van de Latentie van Eind tot Eind ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)


## Implementatiestappen

### Adobe Experience Platform

#### Schema/datasets

1. [ vorm individueel profiel, ervaringsgebeurtenis, en multi-entiteitsschema&#39;s ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, die op klant-geleverde gegevens wordt gebaseerd.
1. [ creeer datasets ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) in Experience Platform voor gegevens die moeten worden opgenomen.
1. [ voegt de etiketten van het gegevensgebruik ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform aan de dataset voor bestuur toe.
1. [ creeer beleid ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html) dat bestuur op bestemmingen afdwingt.

#### Profiel/identiteit

1. [ creeer om het even welke klant-specifieke namespaces ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [ voegt identiteiten aan schema&#39;s ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) toe.
1. [ laat de schema&#39;s en datasets voor Profiel ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html) toe.
1. [ opstelling voegt beleid ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) voor verschillende meningen van [!UICONTROL  in real time het Profiel van de Klant ] (facultatief) samen.
1. Maak segmenten voor gebruik in Reis.

#### Bronnen/bestemmingen

1. [ Samenvatting gegevens in Experience Platform ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) gebruikend het stromen APIs &amp; bronschakelaars.

### Journey Optimizer

1. Configureer uw Experience Platform-gegevensbron en bepaal welke velden in de cache moeten worden geplaatst als onderdeel van de profileStreaming-gegevens die worden gebruikt om een klantentraject te starten, moeten eerst binnen Journey Optimizer worden geconfigureerd om een orchestratie-id te verkrijgen. Deze orchestratie-id wordt vervolgens aan de ontwikkelaar geleverd om met inname te gebruiken
1. Externe gegevensbronnen configureren
1. Aangepaste acties configureren voor toepassing van derden

### Mobiele pushconfiguratie (optioneel omdat tokens van derden kunnen worden verzameld)

1. Experience Platform Mobile SDK implementeren om pushtokens en aanmeldingsgegevens te verzamelen om terug te keren naar bekende klantprofielen
1. Gebruik Adobe-tags en maak een mobiele eigenschap met de volgende extensie:
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge Network
   * Identiteit voor [!DNL Edge Network]
   * Mobiele kern
1. Zorg ervoor dat u beschikt over een specifieke gegevensstroom voor implementatie van mobiele apps versus webimplementaties
1. Voor meer informatie volg de [ Mobiele Gids van Adobe Journey Optimizer ](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer/)

<br>

## Gerelateerde documentatie

* [ documentatie van Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [ de documentatie van de Markeringen van Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [ Experience Platform Mobile SDK documentatie ](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
* [ documentatie van Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [ de Beschrijving van het Product van Journey Optimizer ](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
