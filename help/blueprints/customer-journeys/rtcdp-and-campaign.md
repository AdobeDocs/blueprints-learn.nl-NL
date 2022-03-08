---
title: Real-Time CDP met Adobe Campaign-blauwdruk
description: Toont hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe Campaign kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.
solution: Experience Platform, Campaign v8, Campaign Classic v7, Campaign Standard
source-git-commit: 1c46cbdfc395de4fc9139966cf869ba1feeceaaa
workflow-type: tm+mt
source-wordcount: '764'
ht-degree: 0%

---

# Real-Time CDP met Adobe Campaign-blauwdruk

Toont hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe Campaign kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.

<br>

## Toepassingen

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v7 of Campaign Standard

<br>

## Architectuur

<img src="assets/rtcdp-campaign-architecture.svg" alt="Referentiearchitectuur voor Batch Messaging en Adobe Experience Platform Blueprint" style="width:100%; border:1px solid #4a4a4a" />

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

* Aanbeveling voor een limiet van 20 segmenten
* Activering is beperkt tot elke 24 uur
* Alleen Unieschema-kenmerken beschikbaar voor activering (geen ondersteuning voor array-/maps-/ervaringsgebeurtenissen)
* Aanbeveling betreffende maximaal 20 kenmerken per segment
* Eén bestand per segment van alle profielen met &quot;gerealiseerde&quot; segmentlidmaatschap OF als segmentlidmaatschap is toegevoegd als kenmerk in het bestand, zowel de profielen &quot;gerealiseerde&quot; als &quot;verlaten&quot;
* De stijgende en volledige segmentuitvoer wordt gesteund
* Bestandscodering wordt niet ondersteund

<br>

## Implementatiestappen

### Adobe Experience Platform

#### Schema/gegevensset

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
   * Gebruik Adobe-tags en de Campaign Classic-extensie om uw integratie met de Experience Platform Mobile SDK in te stellen
   * Wenst een werkende kennis van de Markeringen van Adobe en gegevensinzameling
   * Hebt u mobiele ontwikkelervaring nodig met pushmeldingen in zowel Android als iOS om de SDK te implementeren, te integreren met FCM (Android) en APNS (iOS) om pushtoken te verkrijgen, uw app te configureren voor pushmeldingen en pushinteracties te verwerken
* Campagne Mobile SDK
   * Volg de [Campagne-SDK-documentatie](Campagne Mobile SDK Volg de hier beschreven implementatiedocumentatie.)

   >[!IMPORTANT]
   >Als u de Campagne SDK opstelt en met andere toepassingen van Experience Cloud werkt zullen zij het gebruik van het Experience Platform Mobiele SDK voor gegevensinzameling vereisen. Hierdoor worden dubbele aanroepen aan de clientzijde op het apparaat gemaakt.

## Verwante documentatie

* [Adobe Experience Platform-documentatie](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Campaign Classic-documentatie](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Campaign Standard-documentatie](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentatie Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)