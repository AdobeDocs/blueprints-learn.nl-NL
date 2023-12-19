---
title: Real-Time CDP met Adobe Campaign v7 en Campaign Standard-integratiepatroon
description: Toont hoe Adobe Experience Platform met zijn realtimeklantprofiel en gecentraliseerde segmenteringstool met Adobe Campaign kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.
solution: Real-Time Customer Data Platform, Campaign
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 5f9384abe7f29ec764428af33c6dd1f0a43f5a89
workflow-type: tm+mt
source-wordcount: '663'
ht-degree: 7%

---

# Real-Time CDP met Adobe Campaign-integratiepatroon

Toont hoe Adobe Experience Platform met zijn realtimeklantprofiel en gecentraliseerde segmenteringstool met Adobe Campaign kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.

<br>

## Toepassingen

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v7 of Campaign Standard

<br>

## Architectuur

<img src="assets/rtcdp-campaign-architecture.svg" alt="Referentiearchitectuur voor het integratiepatroon Batch Messaging en Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Vereisten

* Experience Platform en Campagne worden geadviseerd om in zelfde IMS Org provisioned te zijn en Adobe Admin Console voor gebruikerstoegang te gebruiken. Dit zorgt ook ervoor dat de klanten de oplossingsschakelaar van binnen marketing UI kunnen gebruiken

<br>

## Guardrails

### Adobe Campaign

* Alleen ondersteuning voor implementatie van één organisatie in Adobe Campaign
* Adobe Campaign is een bron van waarheid voor alle actieve profielen. Dit houdt in dat er profielen moeten bestaan in Adobe Campaign en dat er geen nieuwe profielen moeten worden gemaakt op basis van Experience Platform-segmenten.
* Workflows voor exporteren van campagnes die maximaal om de 4 uur worden uitgevoerd
* Het schema en de datasets van XDM voor Adobe Campaign wideLog, trackingLogs en niet te leveren adressen zijn niet uit de doos en moeten worden ontworpen en worden gebouwd

### CDP-segmentdeling van Experience Platform

* Verwijs naar de schakelaar van de Bestemming van de Campagne RTCDP - [RTCDP-cameraverbinding](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)

* Zie instructies voor het opnemen van profielen en gegevens voor AEP - [Koppeling](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementatiestappen

### Adobe Experience Platform

#### Schema/datasets

1. [Afzonderlijke profiel-, ervarings- en multientiteitsschema&#39;s configureren](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, op basis van door de klant verstrekte gegevens.
1. Maak Adobe Campaign-schema&#39;s voor wideLog, trackingLog, niet-te leveren adressen en profielvoorkeuren (optioneel).
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) in Experience Platform voor gegevens die moeten worden ingevoerd.
1. [Labels voor gegevensgebruik toevoegen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform met de dataset voor bestuur.
1. [Beleid maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html) de handhaving van het bestuur op bestemmingen.

#### Profiel/identiteit

1. [Maak klantspecifieke naamruimten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Identiteiten toevoegen aan schema&#39;s](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [De schema&#39;s en datasets voor Profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Samenvoegbeleid instellen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) voor verschillende weergaven van [!UICONTROL Klantprofiel in realtime] (optioneel).
1. Maak segmenten voor Adobe Campaign-gebruik.

#### Bronnen/bestemmingen

1. [Bronnen en ontwerpen voor Experience Platform en Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html)
1. [Bronnen en ontwerpen voor Experience Platform en campagne v7](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html)
1. [Gegevens in Experience Platform opnemen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) via streaming API&#39;s en bronconnectors.
1. Configureren [!DNL Azure] blob-opslagbestemming voor gebruik met Adobe Campaign.

#### Adobe Campaign

1. Configureer schema&#39;s voor profiel, opzoekgegevens en relevante verpersoonlijkingsgegevens van de levering.

>[!IMPORTANT]
>
>Het is van essentieel belang dat u op dit moment begrijpt wat het gegevensmodel in het Experience Platform is voor profiel- en gebeurtenisgegevens, zodat u weet welke gegevens in Adobe Campaign vereist zijn.

#### Workflows importeren

1. Vereenvoudigde profielgegevens laden en invoeren op Adobe Campaign sFTP.
1. Laad en voeg orchestratie- en messaging personalization-gegevens toe aan Adobe Campaign sFTP.
1. Experience Platform-segmenten samenvoegen uit [!DNL Azure] blokkeren via workflows.

#### Workflows exporteren

1. Stuur Adobe Campaign-logbestanden om de vier uur via workflows terug naar het Experience Platform (wideLog, trackingLog, niet-te leveren adressen).
1. Verzend de profielvoorkeuren terug naar het Experience Platform via vooraf gebouwde workflows (optioneel).


### Mobiele pushconfiguratie

* Twee ondersteunde benaderingen voor integratie met mobiele apparaten voor pushmeldingen:
   * Experience Platform Mobile SDK
   * Campagne Mobile SDK
* Experience Platform Mobile SDK route:
   * De Markeringen van de Adobe van de hefboomwerking en de uitbreiding van het Campaign Classic voor vestiging uw integratie met het Experience Platform Mobile SDK
   * Wenst een werkende kennis van de Markeringen van de Adobe en gegevensinzameling
   * Hebt u mobiele ontwikkelervaring nodig met pushmeldingen in zowel Android als iOS om de SDK te implementeren, te integreren met FCM (Android) en APNS (iOS) om pushtoken te verkrijgen, uw app te configureren voor pushmeldingen en pushinteracties te verwerken
* Campagne Mobile SDK
   * Volg de [Campagne-SDK-documentatie](Campagne Mobile SDK Volg de hier beschreven implementatiedocumentatie.)

  >[!IMPORTANT]
  >Als u de Campagne SDK opstelt en met andere toepassingen van het Experience Cloud werkt zullen zij het gebruik van het Experience Platform Mobiele SDK voor gegevensinzameling vereisen. Hierdoor worden dubbele aanroepen aan de clientzijde op het apparaat gemaakt.

## Gerelateerde documentatie

* [Adobe Experience Platform-documentatie](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Documentatie Campaign Classic](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Documentatie Campaign Standard](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentatie Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
