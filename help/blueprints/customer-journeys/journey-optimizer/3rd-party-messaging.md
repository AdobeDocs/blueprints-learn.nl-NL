---
title: Journey Optimizer - blauwdruk voor communicatie van derden
description: Toont aan hoe Adobe Journey Optimizer met de systemen van het derdeoverseinen kan worden gebruikt om gepersonaliseerde mededelingen te verzenden.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 8fcc71abcc29f5dc7d2e2b3a5afcc60d9e844fcc
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 2%

---

# Blauwdruk voor berichten van derden

Toont aan hoe Adobe Journey Optimizer met de systemen van het derdeoverseinen kan worden gebruikt om gepersonaliseerde mededelingen te verzenden.

<br>

## Architectuur

<img src="images/3rd-party-messaging-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Vereisten

**Adobe Experience Platform**

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u Journey Optimizer gegevensbronnen kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring, voeg &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis wilt teweegbrengen die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Proefdetails profiel&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer

**de Toepassing van het Overseinen van de derde partij**

* Moet REST API-aanroepen ondersteunen voor het verzenden van transactiebetalingen

<br>

## Beveiligingsmechanismen

[&#x200B; Journey Optimizer Guardrails Product Link &#x200B;](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=nl-NL)

[&#x200B; Guardrails en de Begeleiding van de Latentie van Eind tot Eind &#x200B;](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html?lang=nl-NL)

<br>

## Implementatiestappen

### Adobe Experience Platform

#### Schema/datasets

1. [&#x200B; vormt schema&#39;s &#x200B;](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, die op klant-geleverde gegevens wordt gebaseerd.
1. [&#x200B; creeer datasets &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=nl-NL) in Experience Platform voor gegevens die moeten worden opgenomen.
1. [&#x200B; voegt de etiketten van het gegevensgebruik &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=nl-NL) in Experience Platform aan de dataset voor bestuur toe.
1. [&#x200B; creeer beleid &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=nl-NL) dat bestuur op bestemmingen afdwingt.

#### Profiel/identiteit

1. [&#x200B; creeer om het even welke klant-specifieke namespaces &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=nl-NL).
1. [&#x200B; voegt identiteiten aan schema&#39;s &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=nl-NL) toe.
1. [&#x200B; laat de schema&#39;s en datasets voor Profiel &#x200B;](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile) toe.
1. [&#x200B; opstelling voegt beleid &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=nl-NL) voor verschillende meningen van [!UICONTROL &#x200B; in real time het Profiel van de Klant &#x200B;] (facultatief) samen.
1. Maak segmenten voor gebruik in Reis.

#### Bronnen/bestemmingen

1. [&#x200B; Samenvatting gegevens in Experience Platform &#x200B;](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2020.1.dataingestion) gebruikend het stromen APIs &amp; bronschakelaars.

### Journey Optimizer

1. Vorm uw gegevensbron van Experience Platform en bepaal welke gebieden als deel van de reis in het voorgeheugen zouden moeten worden opgeslagen
1. Streaming gegevens, die worden gebruikt om een reis van de klant te initiëren, moeten eerst worden geconfigureerd om een organisatie-id te krijgen. Deze orchestratie-id wordt vervolgens aan de ontwikkelaar geleverd voor gebruik tijdens inname.
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
1. Voor meer informatie volg de [&#x200B; Mobiele Gids van Adobe Journey Optimizer &#x200B;](https://developer.adobe.com/client-sdks/documentation/adobe-journey-optimizer/)

<br>

## Gerelateerde documentatie

* [&#x200B; documentatie van Experience Platform &#x200B;](https://experienceleague.adobe.com/docs/experience-platform.html?lang=nl-NL)
* [&#x200B; de documentatie van de Markeringen van Experience Platform &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)
* [&#x200B; Experience Platform Mobile SDK documentatie &#x200B;](https://experienceleague.adobe.com/docs/mobile.html?lang=nl-NL)
* [&#x200B; documentatie van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=nl-NL)
* [&#x200B; de Beschrijving van het Product van Journey Optimizer &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-journey-optimizer.html)
