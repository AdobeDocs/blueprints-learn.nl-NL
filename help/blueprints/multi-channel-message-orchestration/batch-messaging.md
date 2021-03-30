---
title: Batchberichten en Adobe Experience Platform-scenario
description: Uitvoer geplande en partijoverseinen campagnes gebruikend Adobe Experience Platform als centrale hub voor klantenprofielen en segmentatie.
solution: Experience Platform, Campaign
kt: 7196
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '544'
ht-degree: 0%

---


# Batchberichten en Adobe Experience Platform-scenario

Uitvoer geplande en partijoverseinen campagnes gebruikend Adobe Experience Platform als centrale hub voor klantenprofielen en segmentatie.

## Gevallen gebruiken

* Geplande e-mailcampagnes
* Onboarding- en hermarketingcampagnes

## Toepassingen

* Adobe Experience Platform
* Adobe Campaign Classic of Standard

## Integratiepatronen

* Adobe Experience Platform → Adobe Campaign Classic
* Adobe Experience Platform → Adobe Campaign Standard

## Architectuur

<img src="assets/aepbatch.svg" alt="Referentiearchitectuur voor het scenario Batch Messaging en Adobe Experience Platform" style="border:1px solid #4a4a4a" />

## Guardrails

* Ondersteunt alleen implementaties van één organisatie-eenheid voor campagnes
* Campagne is een bron van waarheid voor alle actieve profielen. Dit houdt in dat er profielen moeten bestaan in Campagne en dat er geen nieuwe profielen moeten worden gemaakt op basis van de segmenten van het Experience Platform.
* De segmentlidmaatschapsrealisatie van Experience Platform is latent voor zowel batch (1 per dag) als streaming (~5 minuten)

**Het segment van het Platform van Gegevens van de Klant in real time delen aan campagne:**

* Aanbeveling voor een limiet van 20 segmenten
* Activering is beperkt tot elke 24 uur
* Alleen Unieschema-kenmerken beschikbaar voor activering (geen ondersteuning voor array-/maps-/ervaringsgebeurtenissen).
* Aanbeveling van niet meer dan 20 kenmerken per segment
* Eén bestand per segment van alle profielen met &quot;gerealiseerde&quot; segmentlidmaatschap OF als segmentlidmaatschap is toegevoegd als kenmerk in het bestand, zowel de profielen &quot;gerealiseerde&quot; als &quot;verlaten&quot;
* De stijgende of volledige segmentuitvoer wordt gesteund
* Bestandscodering wordt niet ondersteund
* Workflows voor exporteren van campagnes die maximaal om de 4 uur worden uitgevoerd
* Zie [profiel- en gegevensinvoerinstructies voor Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementatiestappen

### Adobe Experience Platform

#### Schema/gegevensset

1. Vorm individuele profiel, ervaringsgebeurtenis, en multi-entiteitsschema&#39;s in Experience Platform, die op klant-geleverde gegevens wordt gebaseerd.
1. Maak campagnereschema&#39;s voor wideLog, trackingLog, niet-te leveren adressen en profielvoorkeuren (optioneel).
1. Voeg labels voor gegevensgebruik toe aan de dataset voor beheer.
1. Creeer beleid dat bestuur op bestemmingen afdwingt.

#### Profiel/identiteit

1. Maak klantspecifieke naamruimten.
1. Identiteiten toevoegen aan schema&#39;s.
1. Laat schema&#39;s en datasets voor profiel toe.
1. Stel fusieregels in voor verschillende weergaven van het Real-time profiel van de klant (optioneel).
1. Maak segmenten voor campagnegebruik.

#### Bronnen/bestemmingen

1. Gegevens in Experience Platform opnemen met streaming API&#39;s en bronconnectors.
1. Vorm [!DNL Azure] blob opslagbestemming voor gebruik met Campagne.

#### Implementatie van mobiele apps

1. Voer de SDK van de Campagne voor Campaign Classic of Experience Platform SDK voor Campaign Standard uit. Als er Experience Platform Launch aanwezig is, wordt aanbevolen Campaign Classic/Standard-extensie te gebruiken met Experience Platform SDK.

#### Campagne

1. Configureer schema&#39;s voor profiel, opzoekgegevens en relevante verpersoonlijkingsgegevens van de levering.

>[!IMPORTANT]
>
>Het is belangrijk om op dit punt te begrijpen wat het gegevensmodel binnen Experience Platform voor profiel en gebeurtenisgegevens is zodat u weet welke gegevens in Campagne zullen worden vereist.

#### Workflows importeren

1. Vereenvoudigde profielgegevens laden en invoeren op Campagne sFTP.
1. Laad en neem orchestratie en overseinen verpersoonlijkingsgegevens op Campagne sFTP op.
1. Samenvoegen van Experience Platforms segmenten van [!DNL Azure] blob via workflows.

#### Workflows exporteren

1. Verzend de logboeken van de Campagne terug naar Experience Platform via werkschema&#39;s om de vier uur (bredeLog, trackingLog, niet-te leveren adressen).
1. Verzend de profielvoorkeuren terug naar het Experience Platform via vooraf gebouwde workflows (optioneel).


## Verwante documentatie

* [Adobe Experience Platform-documentatie](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Campaign Classic-documentatie](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Campaign Standard-documentatie](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentatie Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
