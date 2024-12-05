---
title: Journey Optimizer met Adobe Campaign v8-blauwdruk
description: Toont aan hoe Adobe Journey Optimizer met Adobe Campaign kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in Campagne te gebruiken
solution: Journey Optimizer, Campaign, Campaign v8 Client Console
exl-id: 447a1b60-f217-4295-a0df-32292c4742b0
source-git-commit: f8b9cc115739b53bba71d06b228dcce57df9dd7b
workflow-type: tm+mt
source-wordcount: '632'
ht-degree: 2%

---

# Journey Optimizer met Adobe Campaign v8-blauwdruk

Toont aan hoe de Adobe [!DNL Journey Optimizer] met Adobe [!DNL Campaign] kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in [!DNL Campaign] te gebruiken.

## Architectuur

<img src="assets/ajo-campaign-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

>[!IMPORTANT]
>Het gebruik van zowel Journey Optimizer als Campagne om berichten onafhankelijk van elkaar te verzenden is mogelijk, maar bevat enkele technische overwegingen die moeten worden doorgelicht. Als u deze route wilt nastreven, gelieve met uw Architect van de Onderneming van de pre-Verkoop samen te werken om ervoor te zorgen dat u een inzicht in hebt wat zal worden vereist om de implementatie te steunen.

## Vereisten

Controleer de volgende voorwaarden voor elke toepassing.

### Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u Journey Optimizer gegevensbronnen kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer
* Journey Optimizer en Campagne worden geleverd in dezelfde IMS Org

### Campaign v8

* De instantie van de uitvoering van de dienst van het overseinen in real time (d.w.z. het Centrum van het Bericht) moet door Adobe Geleide Cloud Servicen worden ontvangen
* Alle bericht authoring wordt uitgevoerd binnen de Campagne-instantie zelf

## Beveiligingsmechanismen

* [ Journey Optimizer Guardrails productbeperkingen ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

* [ Guardrails en de begeleiding van begin tot eind van de latentie ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Implementatiestappen

Volg de implementaties voor elke hieronder beschreven toepassing.

### Adobe Experience Platform

#### Schema/datasets

1. [ vorm individueel profiel, ervaringsgebeurtenis, en multi-entiteitsschema&#39;s ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, dat op klant-geleverde gegevens wordt gebaseerd.
1. (Optioneel) Maak op de klasse gebaseerde schema&#39;s voor Experience Event voor Adobe Campaign wideLog, trackingLog en niet-leverbare adrestabellen.
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

1. [ Samenvatting gegevens in  [!DNL Experience Platform] ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) gebruikend het stromen APIs &amp; bronschakelaars.

### Journey Optimizer

1. Configureer uw [!DNL Experience Platform] -gegevensbron en bepaal welke velden in de cache moeten worden geplaatst als onderdeel van de profileStreaming-gegevens die worden gebruikt om een klantentereis te starten, moeten eerst binnen Journey Optimizer worden geconfigureerd om een organisatie-id te verkrijgen. Deze orkest-id wordt vervolgens aan de ontwikkelaar geleverd om met inname te gebruiken.
1. Externe gegevensbronnen configureren.
1. Vorm douaneacties voor de instantie van de Campagne.

### Campaign v8

* De malplaatjes van het overseinen moeten met aangewezen verpersoonlijkingscontext worden gevormd.
* Voor [!DNL Campaign] standard: de werkschema&#39;s van de uitvoer moeten worden gevormd om de transactionele overseinenlogboeken terug naar het Experience Platform uit te voeren. De aanbeveling is om ten hoogste om de vier uur te lopen.
* Voor [!DNL Campaign] v8.4 is het mogelijk om de Adobe [!DNL Campaign] Managed Services Source Connector in Experience Platform te gebruiken voor het synchroniseren van bezorgings- en volggebeurtenissen van Campagne naar Experience Platform. Verwijs naar de [ 1} documentatie van de Schakelaar van Source {voor details.](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

### Mobiele pushconfiguratie (optioneel)

1. Implementeer [!DNL Experience Platform] Mobile SDK om pushtokens en aanmeldingsgegevens te verzamelen en terug te koppelen naar bekende klantprofielen.
1. Gebruik Adobe-tags en maak een mobiele eigenschap met de volgende extensie:
   * Adobe [!DNL Journey Optimizer] | Adobe [!DNL Campaign Classic] | Adobe [!DNL Campaign Standard]
   * Adobe [!DNL Experience Platform] [!DNL Edge Network]
   * Identiteit voor [!DNL Edge Network]
   * Mobiele kern
1. Zorg ervoor dat u beschikt over een specifieke gegevensstroom voor implementatie van mobiele apps versus webimplementaties.
1. Voor meer informatie volg de [ Mobiele Gids van Adobe Journey Optimizer ](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer).

   >[!IMPORTANT]
   >Mobiele tokens moeten mogelijk zowel in Journey Optimizer als in Campagne worden verzameld als er behoefte is aan realtime communicatie via Journey Optimizer en batchpushberichten via Campagne. Voor campagne v8 is het exclusieve gebruik van de Campagne SDK vereist voor het vastleggen van push-tokens.

## Gerelateerde documentatie

* [ documentatie van Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [ de Beschrijving van het Product van Journey Optimizer ](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [ Campagne v8 documentatie ](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
