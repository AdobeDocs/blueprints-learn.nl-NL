---
title: Real-Time CDP met [!DNL Campaign] v7 en integratiepatroon voor Campaigns Standard
description: Toon hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe kunnen worden gebruikt [!DNL Campaign] om persoonlijke gesprekken te leveren.
solution: Real-Time Customer Data Platform, [!DNL Campaign]
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: 258aea64f6ff2f620b1adaa0c9ba4b02b47acce9
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# [!DNL Real-Time Customer Data Platform] with [!DNL Campaign] integratiepatroon

De Adobe tonen [!DNL Experience Platform] en zijn Real-Time Profiel van de Klant en gecentraliseerd segmenteringshulpmiddel kunnen met Adobe worden gebruikt [!DNL Campaign] om persoonlijke gesprekken te leveren.

## Toepassingen

* Adobe [!DNL Experience Platform Real-Time Customer Data Platform]
* Adobe [!DNL Campaign] v7 of [!DNL Campaign Standard]

## Architectuur

<img src="assets/rtcdp-campaign-architecture.svg" alt="Referentiearchitectuur voor het integratiepatroon Batch Messaging en Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Vereisten

* Experience Platform en [!DNL Campaign] wordt aangeraden provisioned te zijn in dezelfde IMS Org en Adobe Admin Console te gebruiken voor gebruikerstoegang. Dit zorgt ook ervoor dat de klanten de oplossingsschakelaar van binnen marketing UI kunnen gebruiken

## Guardrails

In de volgende secties worden de instructies voor deze integratie beschreven.

### Adobe [!DNL Campaign]

* Alleen ondersteuning voor Adobe [!DNL Campaign] implementatie van één organisatie-eenheid
* Adobe [!DNL Campaign] is een bron van waarheid voor alle actieve profielen, wat betekent dat er profielen moeten bestaan in Adobe [!DNL Campaign] en nieuwe profielen moeten niet worden gemaakt op basis van Experience Platforms segmenten.
* [!DNL Campaign] workflows exporteren om maximaal elke 4 uur te worden uitgevoerd
* XDM-schema en -gegevenssets voor Adobe [!DNL Campaign] wideLog, trackingLogs en niet-te leveren adressen zijn niet uit de doos en moeten worden ontworpen en gebouwd

### Real-time Customer Data Platform-segmentdeling

* Verwijs naar RTCDP [!DNL Campaign] Aansluiting bestemming - [RTCDP-cameraverbinding](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=nl-NL)

* Zie [Standaardhulplijnen voor [!DNL Real-Time Customer Profile Data] en segmentering](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=nl-NL)

## Implementatiestappen

In de volgende secties worden de implementatiestappen voor elke toepassing beschreven.

### Adobe Experience Platform

#### Schema/datasets

1. [Afzonderlijke profiel-, ervarings- en multientiteitsschema&#39;s configureren](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, op basis van door de klant verstrekte gegevens.
1. Adobe maken [!DNL Campaign] schema&#39;s voor wideLog, trackingLog, niet-te leveren adressen, en profielvoorkeur (facultatief).
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=nl-NL) in Experience Platform voor gegevens die moeten worden ingevoerd.
1. [Labels voor gegevensgebruik toevoegen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html?lang=nl-NL) in Experience Platform met de dataset voor bestuur.
1. [Beleid maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html?lang=nl-NL) de handhaving van het bestuur op bestemmingen.

#### Profiel/identiteit

1. [Maak klantspecifieke naamruimten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=nl-NL).
1. [Identiteiten toevoegen aan schema&#39;s](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=nl-NL).
1. [De schema&#39;s en datasets voor Profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=nl-NL).
1. [Samenvoegbeleid instellen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html?lang=nl-NL) voor verschillende weergaven van [!UICONTROL Klantprofiel in realtime] (optioneel).
1. Segmenten maken voor Adobe [!DNL Campaign] gebruik.

#### Bronnen/bestemmingen

1. [Experience Platform en [!DNL Campaign] Standaardbronnen en -doelen](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html?lang=nl-NL)
1. [Experience Platform en [!DNL Campaign] v7 Bronnen en doelen](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html?lang=nl-NL)
1. [Gegevens in Experience Platform opnemen](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2020.1.dataingestion) via streaming API&#39;s en bronconnectors.
1. Configureren [!DNL Azure] opslagbestemming voor blob voor gebruik met Adobe [!DNL Campaign].

#### Adobe [!DNL Campaign]

1. Configureer schema&#39;s voor profiel, opzoekgegevens en relevante verpersoonlijkingsgegevens van de levering.

>[!IMPORTANT]
>
>Het is van essentieel belang om op dit moment te begrijpen wat het gegevensmodel in Experience Platform is voor profiel- en gebeurtenisgegevens, zodat u weet welke gegevens vereist zijn in de Adobe [!DNL Campaign].

#### Workflows importeren

1. Vereenvoudigde profielgegevens laden en opnemen op Adobe [!DNL Campaign] sFTP.
1. De lading en neemt orchestratie en overseinen verpersoonlijkingsgegevens op Adobe op [!DNL Campaign] sFTP.
1. Experience Platform-segmenten samenvoegen uit [!DNL Azure] blokkeren via workflows.

#### Workflows exporteren

1. Adobe verzenden [!DNL Campaign] logt terug naar Experience Platform via werkschema&#39;s om de vier uur (wideLog, trackingLog, niet-te leveren adressen).
1. Verzend de profielvoorkeuren terug naar het Experience Platform via vooraf gebouwde workflows (optioneel).

### Mobiele pushconfiguratie

* Twee ondersteunde benaderingen voor integratie met mobiele apparaten voor pushmeldingen:
   * Experience Platform Mobile SDK
   * [!DNL Campaign] Mobile SDK
* Experience Platform Mobile SDK route:
   * Gebruik Adobe-tags en de [!DNL Campaign Classic] extensie voor het instellen van de integratie met de Experience Platform Mobile SDK
   * Wenst een werkende kennis van de Markeringen van de Adobe en gegevensinzameling
   * Hebt u mobiele ontwikkelervaring nodig met pushmeldingen in zowel Android als iOS om de SDK te implementeren, te integreren met FCM (Android) en APNS (iOS) om pushtoken te verkrijgen, uw app te configureren voor pushmeldingen en pushinteracties te verwerken
* [!DNL Campaign] Mobile SDK
   * Zie de [Campaign Classic SDK-documentatie](https://developer.adobe.com/client-sdks/solution/adobe-campaign-classic/)

>[!IMPORTANT]
>
>Als u [!DNL Campaign] SDK en werken met andere toepassingen van het Experience Cloud zij het gebruik van het Experience Platform Mobiele SDK voor gegevensinzameling zullen vereisen. Hierdoor worden dubbele aanroepen aan de clientzijde op het apparaat gemaakt.

## Gerelateerde documentatie

* [Adobe [!DNL Experience Platform] documentatie](https://experienceleague.adobe.com/docs/experience-platform.html?lang=nl-NL)
* [[!DNL Campaign Classic] documentatie](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=nl-NL)
* [[!DNL Campaign Standard] documentatie](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=nl-NL)
* [[!DNL Experience Platform] Documentatie starten](https://experienceleague.adobe.com/docs/launch.html?lang=nl-NL)
* [[!DNL Experience Platform] Mobiele SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=nl-NL)
