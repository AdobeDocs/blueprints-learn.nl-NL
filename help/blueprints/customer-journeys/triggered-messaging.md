---
title: Gekoppelde berichten en Adobe Experience Platform-blauwdruk
description: Voer teweeggebrachte berichten en ervaringen uit gebruikend Adobe Experience Platform als centrale hub van het stromen gegevens, klantenprofielen, en segmentatie.
solution: Experience Platform, Campaign, Journey Orchestration
kt: 7197
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 584007cc71e00729732c67a97546e2c21aed3f87
workflow-type: tm+mt
source-wordcount: '694'
ht-degree: 0%

---

# Gekoppelde berichten en Adobe Experience Platform-blauwdruk

Voer teweeggebrachte berichten en ervaringen uit gebruikend Adobe Experience Platform als centrale hub van het stromen gegevens, klantenprofielen, en segmentatie.

## Gevallen gebruiken

* Gekoppelde berichten
* Registratie-bevestigingen
* Verlaten winkelwagentjes en aanvraagformulieren
* Locatie getriggerde berichten

## Architectuur

<img src="assets/triggered.svg" alt="Referentiearchitectuur voor de blauwdruk voor geactiveerd berichtenverkeer en Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Integratiepatronen

* Adobe Experience Platform -> Journey Orchestration

## Vereisten

* Adobe Experience Platform
* Journey Orchestration

## Guardrails

### Journey Orchestration

* Zie de koppeling voor [meer informatie over beperkingen](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en#starting-with-journeys)
* De Capping is beschikbaar door API opstelling om ervoor te zorgen dat het bestemmingssysteem niet aan het punt van mislukking wordt verzadigd. Het maximum betekent dat de berichten die het maximum overschrijden volledig worden gelaten vallen en nooit worden verzonden. Throttling wordt nog steeds niet ondersteund.
   * max. verbindingen: Maximumaantal http/s-verbindingen dat een doel kan afhandelen
   * max. aantal aanroepen: Maximumaantal oproepen dat in de parameter periodInMS moet worden gedaan
   * periodInMS: Tijd in milliseconden
* Op gang gebrachte reizen met het lidmaatschap van een segment kunnen in twee modi worden uitgevoerd:
   * batchsegmenten (elke 24 uur vernieuwd)
   * Streaming segmenten (&lt;5 minuten kwalificatie)
* Batchsegmenten: Zorg ervoor dat u het dagelijkse volume van gekwalificeerde gebruikers begrijpt en dat het bestemmingssysteem de burst-doorvoer per reis en over alle reizen kan verwerken
* Streaming segmenten: Ervoor zorgen dat de eerste uitbarsting van profielkwalificaties kan worden afgehandeld samen met het dagelijks streaming kwalificatievolume per reis en over alle reizen
* De eindbestemming moet REST API en JSON payload ondersteunen
* Biedt momenteel geen ondersteuning voor Offer decisioning
* Zie [profiel- en gegevensinvoerinstructies voor Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)

### Adobe Campaign Standard

* Alleen ondersteuning voor doorvoer van 14 tps (50 k per uur)
* Reizen met lidmaatschap van een segment worden niet ondersteund
* Reactiegebeurtenissen voor open/kliks van transactieberichten worden ondersteund binnen Journey Orchestration.
* De transactionele overseinenlogboeken worden niet nationaal gesynchroniseerd aan Experience Platform momenteel, die een handconfiguratie vereisen. U wordt aangeraden de logbestanden maximaal om de vier uur te exporteren.


## Implementatiestappen

### Adobe Experience Platform

#### Schema/gegevensset

1. [Vorm individueel profiel, ervaringsgebeurtenis, en multi-entiteitsschema&#39;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) s in Experience Platform, die op klant-geleverde gegevens wordt gebaseerd.
1. Maak Adobe Campaign-schema&#39;s voor wideLog, trackingLog, niet-te leveren adressen en profielvoorkeuren (optioneel).
1. [Creeer ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) datasetsin Experience Platform voor gegevens die moeten worden opgenomen.
1. [Voeg ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) labels voor gegevensgebruik in Experience Platform toe aan de dataset voor bestuur.
1. [Creeer ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html) beleid dat bestuur op bestemmingen afdwingt.

#### Profiel/identiteit

1. [Maak klantspecifieke naamruimten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Identiteiten toevoegen aan schema&#39;s](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Laat de schema&#39;s en datasets voor Profiel](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html) toe.
1. [Stel samenvoegbeleid ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) in voor verschillende weergaven van  [!UICONTROL realtime klantprofiel]  (optioneel).
1. Maak segmenten voor Adobe Campaign-gebruik.

#### Bronnen/bestemmingen

1. [Gegevens opnemen in Experience ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) Platform met streaming API&#39;s en bronconnectors.1. Vorm  [!DNL Azure] blob opslagbestemming voor gebruik met Adobe Campaign.

#### Implementatie van mobiele apps

1. Adobe Campaign SDK voor Adobe Campaign Classic of Experience Platform SDK voor Adobe Campaign Standard implementeren. Als er Experience Platform Launch aanwezig is, wordt aanbevolen Adobe Campaign Classic of Adobe Campaign Standard uit te breiden met Experience Platform SDK.


### Journey Orchestration

1. Streaming gegevens die worden gebruikt om een reis van de klant te initiëren, moeten eerst binnen Journey Orchestration worden geconfigureerd om een orchestratie-id te krijgen. Deze orkest-id wordt vervolgens aan de ontwikkelaar geleverd om met inname te gebruiken.
1. Externe gegevensbronnen configureren.
1. Aangepaste handelingen configureren.

### Adobe Campaign Standard

1. Vorm overseinensjablonen met aangewezen verpersoonlijkingsmontages.
1. Vorm de werkschema&#39;s van de de uitvoeruitvoer transactionele overseinenlogboeken. De aanbeveling moet ten hoogste om de vier uur worden uitgevoerd.


## Verwante documentatie

* [Adobe Experience Platform-documentatie](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Journey Orchestration-documentatie](https://experienceleague.adobe.com/docs/journey-orchestration.html?lang=en)
* [Adobe Campaign Classic-documentatie](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Adobe Campaign Standard-documentatie](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentatie Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
