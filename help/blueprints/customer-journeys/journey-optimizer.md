---
title: Journey Optimizer - geactiveerd berichtenverkeer en Adobe Experience Platform-blauwdruk
description: Voer teweeggebrachte berichten en ervaringen uit gebruikend Adobe Experience Platform als centrale hub van het stromen gegevens, klantenprofielen, en segmentatie.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 55584ea85570bbcd4c959b0bd94b9e0bdc2e962f
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 0%

---

# Journey Optimizer

Adobe Journey Optimizer is een speciaal gebouwd systeem voor marketingteams om in real-time te reageren op gedragingen van klanten en hen te ontmoeten waar ze zich bevinden. De mogelijkheden voor gegevensbeheer zijn verplaatst naar de Adobe Experience Platform, zodat marketingteams zich kunnen richten op wat ze het beste doen: die klanten van wereldklasse en gepersonaliseerde gesprekken creeert.  Deze blauwdruk beschrijft de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten die omhoog Adobe Journey Optimizer maken.

## Gevallen gebruiken

* Gekoppelde berichten
* Registratie-bevestigingen
* Verlaten winkelwagentjes en aanvraagformulieren
* Locatie getriggerde berichten

## Architectuur

<img src="assets/journey-optimizer.png" alt="Referentiearchitectuur voor de blauwdruk voor geactiveerd berichtenverkeer en Adobe Experience Platform" style="width:80%; border:1px solid #4a4a4a" />

## Integratiepatronen

* Adobe Experience Platform -> Journey Optimizer

## Vereisten

1. De klant moet voor Experience Cloud een geldige IMS-organisatie opgeven
1. Mobiele push

* De klant moet over een mobiele ontwikkelaar beschikken om de app te maken
* Adobe Experience Platform Mobile SDK
* Gegevensverzameling
   * Eigenschap voor mobiele tags
      * Extensies:
         * Adobe Journey Optimizer-extensie
         * Adobe Experience Platform Edge Network
         * Identiteit
         * Mobiele kern
         * Profiel
   * App Configurations
   * DataStreams
      * Ingeschakeld voor Experience Platform
      * Gegevensset gebeurtenis - wordt gebruikt voor het verzamelen van algemeen mobiel gedrag
      * Gegevensset profiel - Dataset AJO-pushprofiel (kan niet anders zijn)

## Guardrails

* Zie de koppeling voor meer informatie over hulplijnen voor Journey Optimizer [KOPPELING](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)
* Batchsegmenten - zorg dat u het dagelijkse volume van gekwalificeerde gebruikers begrijpt en ervoor zorgt dat het doelsysteem de burst-doorvoer per reis en over alle reizen kan verwerken
* Streamingsegmenten - moeten ervoor zorgen dat de eerste uitbarsting van profielkwalificaties kan worden afgehandeld samen met het dagelijks streaming kwalificatievolume per reis en over alle reizen
* De updateactiviteit van het profiel - het Real-Time Profiel van de Klant kan van binnen een reis worden bijgewerkt.  De verwerking van de update naar de profielopslag duurt maximaal 1 minuten
* Bedrijfs gebeurtenissen - een read segment gebaseerde reis kan worden teweeggebracht om te beginnen gebaseerd op een externe vraag in het JO systeem
* Native ondersteunt alleen Offer decisioning in berichten. Toekomstige ondersteuning via native actie
* Ondersteunde kanalen:
   * E-mail
   * Push (FCM/APNS)
   * API-eindpunten rust
* Verwerkt 5.000 gebeurtenissen per seconde met horizontale schaling (de achtergrond is beperkt)
* A/B-tests worden uitgevoerd met behulp van twee leveringen en de resultaten worden bepaald met behulp van QS of CJA
* Litmus-integratie: moet een account bij Litmus hebben om integratie te kunnen stimuleren

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
1. Maak segmenten voor campagnegebruik.

#### Bronnen/bestemmingen

1. [Gegevens in Experience Platform opnemen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) via streaming API&#39;s en bronconnectors.1. Configureren [!DNL Azure] blob-opslagbestemming voor gebruik met Adobe Campaign.

#### Implementatie van mobiele apps

1. Adobe Campaign SDK voor Adobe Campaign Classic of Experience Platform SDK voor Adobe Campaign Standard implementeren. Als er Experience Platform Launch aanwezig is, wordt aanbevolen Adobe Campaign Classic of Adobe Campaign Standard uit te breiden met Experience Platform SDK.


### Journey Orchestration

1. Streaming gegevens die worden gebruikt om een reis van een klant te initiëren, moeten eerst binnen Journey Optimizer worden geconfigureerd om een organisatie-id te verkrijgen. Deze orkest-id wordt vervolgens aan de ontwikkelaar geleverd om met inname te gebruiken.
1. Externe gegevensbronnen configureren.
1. Aangepaste handelingen configureren.

## Verwante documentatie

* [Adobe Experience Platform-documentatie](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Journey Optimizer-documentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [Documentatie Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
