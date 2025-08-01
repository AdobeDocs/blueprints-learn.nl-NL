---
title: Journey Optimizer met Adobe Campaign v7-blauwdruk
description: Toont aan hoe Adobe Journey Optimizer met Adobe Campaign kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in Campagne te gebruiken
solution: Journey Optimizer, Campaign, Campaign Classic v7, Campaign Standard
exl-id: 6d9bc65c-cca0-453f-8106-d2895d005ada
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 1%

---

# Journey Optimizer met Adobe Campaign v7-blauwdruk

Toont aan hoe Adobe Journey Optimizer met Adobe Campaign kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in Campaign te gebruiken.

<br>

## Architectuur

<img src="assets/ajo-campaign-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>Het gebruik van zowel Journey Optimizer als Campagne om berichten onafhankelijk van elkaar te verzenden is mogelijk, maar bevat enkele technische overwegingen die moeten worden doorgelicht. Als u deze route wilt nastreven, gelieve met uw Architect van de Onderneming van de pre-Verkoop samen te werken om ervoor te zorgen dat u een inzicht in hebt wat zal worden vereist om de implementatie te steunen.

<br>

## Vereisten

### Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u Journey Optimizer gegevensbronnen kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer
* Journey Optimizer en Campagne worden geleverd in dezelfde IMS Org

### Campagne v7

* De instantie van de uitvoering van de Real-Time Messaging-service (dus Message Center) moet worden gehost door Adobe Managed Cloud Services
* Alle bericht authoring wordt uitgevoerd binnen de Campagne-instantie zelf

<br>

## Beveiligingsmechanismen

[ Journey Optimizer Guardrails Product Link ](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/get-started/guardrails)

[ Guardrails en de Begeleiding van de Latentie van Eind tot Eind ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## Implementatiestappen

### Adobe Experience Platform

#### Schema/datasets

1. [ vorm individueel profiel, ervaringsgebeurtenis, en multi-entiteitsschema&#39;s ](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, die op klant-geleverde gegevens wordt gebaseerd.
1. Creeer de op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voor Adobe Campaign bredeLog, trackingLog en niet-te leveren adreslijsten (facultatief).
1. [ creeer datasets ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=nl-NL) in Experience Platform voor gegevens die moeten worden opgenomen.
1. [ voegt de etiketten van het gegevensgebruik ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=nl-NL) in Experience Platform aan de dataset voor bestuur toe.
1. [ creeer beleid ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=nl-NL) dat bestuur op bestemmingen afdwingt.

#### Profiel/identiteit

1. [ creeer om het even welke klant-specifieke namespaces ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=nl-NL).
1. [ voegt identiteiten aan schema&#39;s ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=nl-NL) toe.
1. [ laat de schema&#39;s en datasets voor Profiel ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=nl-NL) toe.
1. [ opstelling voegt beleid ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=nl-NL) voor verschillende meningen van [!UICONTROL &#x200B; in real time het Profiel van de Klant &#x200B;] (facultatief) samen.
1. Maak segmenten voor gebruik in Reis.

#### Bronnen/bestemmingen

1. [ Samenvatting gegevens in Experience Platform ](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2020.1.dataingestion) gebruikend het stromen APIs &amp; bronschakelaars.

### Journey Optimizer

1. Configureer uw Experience Platform-gegevensbron en bepaal welke velden in de cache moeten worden geplaatst als onderdeel van de profileStreaming-gegevens die worden gebruikt om een klantentraject te starten, moeten eerst binnen Journey Optimizer worden geconfigureerd om een orchestratie-id te verkrijgen. Deze orchestratie-id wordt vervolgens aan de ontwikkelaar geleverd om met inname te gebruiken
1. Externe gegevensbronnen configureren
1. Aangepaste acties voor de instantie Campagne configureren

### Campagne v7

* De malplaatjes van het bericht moeten met aangewezen verpersoonlijkingscontext worden gevormd
* Voor Campagne v7 - de werkschema&#39;s van de Uitvoer moeten worden gevormd om de transactionele overseinenlogboeken terug naar Experience Platform uit te voeren. De aanbeveling moet ten hoogste om de vier uur lopen.

### Mobiele pushconfiguratie (optioneel)

1. Experience Platform Mobile SDK implementeren om pushtokens en aanmeldingsgegevens te verzamelen om terug te keren naar bekende klantprofielen
1. Gebruik Adobe-tags en maak een mobiele eigenschap met de volgende extensie:
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform [!DNL Edge Network]
   * Identiteit voor [!DNL Edge Network]
   * Mobiele kern
1. Zorg ervoor dat u beschikt over een specifieke gegevensstroom voor implementatie van mobiele apps versus webimplementaties
1. Voor meer informatie volg de [ Mobiele Gids van Adobe Journey Optimizer ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer/push-notification/)

   >[!IMPORTANT]
   >Mobiele tokens moeten mogelijk zowel in Journey Optimizer als in Campagne worden verzameld als er behoefte is aan realtime communicatie via Journey Optimizer en batchpushberichten via Campagne. Voor Campaign v8 is het exclusieve gebruik van de Campagne SDK vereist voor het vastleggen van push-tokens.

<br>

## Gerelateerde documentatie

* [ documentatie van Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=nl-NL)
* [ de Beschrijving van het Product van Journey Optimizer ](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-journey-optimizer.html)
* [ de documentatie van de Campagne v7 ](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=nl-NL)
