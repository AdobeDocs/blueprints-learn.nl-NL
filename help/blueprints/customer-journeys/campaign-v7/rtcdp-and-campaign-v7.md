---
title: Real-Time CDP met  [!DNL Campaign]  v7 en het integratiepatroon van Campaign Standard
description: Toon hoe Adobe Experience Platform en zijn Real-Time Profiel van de Klant en gecentraliseerd segmenteringshulpmiddel met Adobe  [!DNL Campaign]  kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.
solution: Real-Time Customer Data Platform, Campaign
exl-id: a15e8304-2763-42fc-9978-11f2482ea8b8
source-git-commit: fa1f8799e774713a48fdd437a9325731aef1b6ab
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 1%

---

# [!DNL Real-Time Customer Data Platform] met [!DNL Campaign] integratiepatroon

Geeft aan hoe de Adobe [!DNL Experience Platform] en het realtime klantprofiel en het gecentraliseerde segmentatieprogramma kunnen worden gebruikt met Adobe [!DNL Campaign] voor persoonlijke gesprekken.

## Applicaties

* Adobe [!DNL Experience Platform Real-Time Customer Data Platform]
* Adobe [!DNL Campaign] v7 of [!DNL Campaign Standard]

## Architectuur

<img src="assets/rtcdp-campaign-architecture.svg" alt="Referentiearchitectuur voor het integratiepatroon Batch Messaging en Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Vereisten

* Experience Platform en [!DNL Campaign] kunnen het beste worden ingericht in dezelfde IMS-organisatie en Adobe Admin Console gebruiken voor gebruikerstoegang. Dit zorgt ook ervoor dat de klanten de oplossingsschakelaar van binnen marketing UI kunnen gebruiken

## Beveiligingsmechanismen

In de volgende secties worden de instructies voor deze integratie beschreven.

### Adobe [!DNL Campaign]

* Alleen ondersteuning voor Adobe [!DNL Campaign]-implementaties per organisatie
* Adobe [!DNL Campaign] is een bron van waarheid voor alle actieve profielen. Dit houdt in dat er profielen moeten bestaan in Adobe [!DNL Campaign] en dat nieuwe profielen niet moeten worden gemaakt op basis van Experience Platform-segmenten.
* [!DNL Campaign] workflows exporteren om maximaal elke 4 uur uit te voeren
* Het XDM-schema en de gegevenssets voor Adobe [!DNL Campaign] wideLog, trackingLogs en niet-te leveren adressen zijn niet uit het vak en moeten worden ontworpen en gebouwd

### Real-Time Customer Data Platform-segmentdeling

* Verwijs naar de schakelaar van de Bestemming van RTCDP [!DNL Campaign] - [ Verbinding van de Campagne van RTCDP ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)

* Zie [ Standaardgidsen voor  [!DNL Real-Time Customer Profile Data]  en segmentatie ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementatiestappen

In de volgende secties worden de implementatiestappen voor elke toepassing beschreven.

### Adobe Experience Platform

#### Schema/datasets

1. [ vorm individueel profiel, ervaringsgebeurtenis, en multi-entiteitsschema&#39;s ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, die op klant-geleverde gegevens wordt gebaseerd.
1. Maak Adobe [!DNL Campaign] -schema&#39;s voor wideLog, trackingLog, niet-te leveren adressen en profielvoorkeuren (optioneel).
1. [ creeer datasets ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) in Experience Platform voor gegevens die moeten worden opgenomen.
1. [ voegt de etiketten van het gegevensgebruik ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform aan de dataset voor bestuur toe.
1. [ creeer beleid ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html) dat bestuur op bestemmingen afdwingt.

#### Profiel/identiteit

1. [ creeer om het even welke klant-specifieke namespaces ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [ voegt identiteiten aan schema&#39;s ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) toe.
1. [ laat de schema&#39;s en datasets voor Profiel ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html) toe.
1. [ opstelling voegt beleid ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) voor verschillende meningen van [!UICONTROL  in real time het Profiel van de Klant ] (facultatief) samen.
1. Maak segmenten voor gebruik in Adobe [!DNL Campaign] .

#### Bronnen/bestemmingen

1. [ Experience Platform en  [!DNL Campaign]  StandaardBronnen en Ontvangingen ](https://experienceleague.adobe.com/docs/campaign-standard/using/integrating-with-adobe-cloud/adobe-experience-platform/aep-sources-destinations/get-started-sources-destinations.html)
1. [ Experience Platform en  [!DNL Campaign]  v7 Bronnen en Ontvangingen ](https://experienceleague.adobe.com/docs/campaign-classic/using/integrating-with-adobe-experience-cloud/aep-sources-destinations/get-started-sources-destinations.html)
1. [ Samenvatting gegevens in Experience Platform ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) gebruikend het stromen APIs &amp; bronschakelaars.
1. Configureer [!DNL Azure] blob storage destination for use with Adobe [!DNL Campaign] .

#### Adobe [!DNL Campaign]

1. Configureer schema&#39;s voor profiel, opzoekgegevens en relevante verpersoonlijkingsgegevens van de levering.

>[!IMPORTANT]
>
>Het is van essentieel belang dat u op dit moment begrijpt wat het gegevensmodel in Experience Platform is voor profiel- en gebeurtenisgegevens, zodat u weet welke gegevens vereist zijn in Adobe [!DNL Campaign] .

#### Workflows importeren

1. Vereenvoudigde profielgegevens laden en invoeren op Adobe [!DNL Campaign] sFTP.
1. Laad en voeg orchestration- en messaging personalization-gegevens toe aan Adobe [!DNL Campaign] sFTP.
1. Voeg Experience Platform-segmenten vanuit [!DNL Azure] blob toe via workflows.

#### Workflows exporteren

1. Verzend Adobe [!DNL Campaign] -logbestanden om de vier uur via workflows terug naar Experience Platform (wideLog, trackingLog, adressen die niet van levering zijn).
1. Stuur de profielvoorkeuren om de vier uur terug naar Experience Platform via vooraf gebouwde workflows (optioneel).

### Mobiele pushconfiguratie

* Twee ondersteunde benaderingen voor integratie met mobiele apparaten voor pushmeldingen:
   * Experience Platform Mobile SDK
   * [!DNL Campaign] Mobile SDK
* Experience Platform Mobile SDK route:
   * Gebruik Adobe Tags en de extensie [!DNL Campaign Classic] om uw integratie met de Experience Platform Mobile SDK in te stellen
   * Hebt u een praktische kennis nodig van Adobe-tags en gegevensverzameling
   * Hebt u mobiele ontwikkelervaring nodig met pushmeldingen in zowel Android als iOS om de SDK te implementeren, te integreren met FCM (Android) en APNS (iOS) om pushtoken te krijgen, uw app te configureren voor pushmeldingen en pushinteracties te verwerken
* [!DNL Campaign] Mobile SDK
   * Zie de [ documentatie van SDK van Campaign Classic ](https://developer.adobe.com/client-sdks/solution/adobe-campaign-classic/)

>[!IMPORTANT]
>
>Als u de [!DNL Campaign] SDK implementeert en met andere Experience Cloud-toepassingen werkt, moet u de Experience Platform Mobile SDK gebruiken voor gegevensverzameling. Hierdoor worden dubbele aanroepen aan de clientzijde op het apparaat gemaakt.

## Gerelateerde documentatie

* [ Adobe  [!DNL Experience Platform]  documentatie ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [[!DNL Campaign Classic]  documentatie ](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [[!DNL Campaign Standard]  documentatie ](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [[!DNL Experience Platform]  documentatie van de Lancering ](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [[!DNL Experience Platform]  Mobiele documentatie van SDK ](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
