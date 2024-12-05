---
title: Journey Optimizer met Adobe Campaign v7-blauwdruk
description: Toont aan hoe Adobe Journey Optimizer met Adobe Campaign kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in Campagne te gebruiken
solution: Journey Optimizer, Campaign, Campaign Classic v7, Campaign Standard
exl-id: 6d9bc65c-cca0-453f-8106-d2895d005ada
source-git-commit: f8b9cc115739b53bba71d06b228dcce57df9dd7b
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

* De instantie van de uitvoering van de dienst van het overseinen in real time (d.w.z. het Centrum van het Bericht) moet door Adobe Geleide Cloud Servicen worden ontvangen
* Alle bericht authoring wordt uitgevoerd binnen de Campagne-instantie zelf

<br>

## Beveiligingsmechanismen

[ Journey Optimizer Guardrails Product Link ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

[ Guardrails en de Begeleiding van de Latentie van Eind tot Eind ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Implementatiestappen

### Adobe Experience Platform

#### Schema/datasets

1. [ vorm individueel profiel, ervaringsgebeurtenis, en multi-entiteitsschema&#39;s ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, dat op klant-geleverde gegevens wordt gebaseerd.
1. Creeer de op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voor Adobe Campaign bredeLog, trackingLog en niet-te leveren adreslijsten (facultatief).
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

1. Vorm uw gegevensbron van de Experience Platform en bepaal welke gebieden als deel van de profileStreaming gegevens zouden moeten worden in het voorgeheugen ondergebracht die worden gebruikt om een klantenreis in werking te stellen moet binnen Journey Optimizer eerst worden gevormd om een orchestration identiteitskaart te krijgen. Deze orchestratie-id wordt vervolgens aan de ontwikkelaar geleverd om met inname te gebruiken
1. Externe gegevensbronnen configureren
1. Aangepaste acties voor de instantie Campagne configureren

### Campagne v7

* De malplaatjes van het bericht moeten met aangewezen verpersoonlijkingscontext worden gevormd
* Voor Campagne v7 - de werkschema&#39;s van de Uitvoer moeten worden gevormd om de transactionele overseinenlogboeken terug naar het Experience Platform uit te voeren. De aanbeveling moet ten hoogste om de vier uur lopen.

### Mobiele pushconfiguratie (optioneel)

1. Implementeer Experience Platform Mobile SDK om pushtokens en aanmeldingsgegevens te verzamelen en terug te koppelen naar bekende klantprofielen
1. Gebruik Adobe-tags en maak een mobiele eigenschap met de volgende extensie:
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform [!DNL Edge Network]
   * Identiteit voor [!DNL Edge Network]
   * Mobiele kern
1. Zorg ervoor dat u beschikt over een specifieke gegevensstroom voor implementatie van mobiele apps versus webimplementaties
1. Voor meer informatie volg de [ Mobiele Gids van Adobe Journey Optimizer ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >Mobiele tokens moeten mogelijk zowel in Journey Optimizer als in Campagne worden verzameld als er behoefte is aan realtime communicatie via Journey Optimizer en batchpushberichten via Campagne. Voor campagne v8 is het exclusieve gebruik van de Campagne SDK vereist voor het vastleggen van push-tokens.

<br>

## Gerelateerde documentatie

* [ documentatie van Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [ de Beschrijving van het Product van Journey Optimizer ](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [ de documentatie van de Campagne v7 ](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
