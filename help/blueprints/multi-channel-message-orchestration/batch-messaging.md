---
title: Batchberichten en Adobe Experience Platform-blauwdruk
description: Uitvoer geplande en partijoverseinen campagnes gebruikend Adobe Experience Platform als centrale hub voor klantenprofielen en segmentatie.
solution: Experience Platform, Campaign
kt: 7196
exl-id: 4e55218c-c158-4f78-9f0b-c03528d992fa
translation-type: tm+mt
source-git-commit: 37416aafc997838888edec2658d2621d20839f94
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Batchberichten en Adobe Experience Platform-blauwdruk

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

<img src="assets/aepbatch.svg" alt="Referentiearchitectuur voor Batch Messaging en Adobe Experience Platform Blueprint" style="border:1px solid #4a4a4a" />

## Guardrails

* Ondersteunt alleen implementaties van één organisatie in Adobe Campaign
* Adobe Campaign is een bron van waarheid voor alle actieve profielen. Dit houdt in dat er profielen moeten bestaan in Adobe Campaign en dat er geen nieuwe profielen moeten worden gemaakt op basis van Experience Platform-segmenten.
* De segmentlidmaatschapsrealisatie van Experience Platform is latent voor zowel batch (1 per dag) als streaming (~5 minuten)

**[!UICONTROL Real-time delen van klantgegevens ] Platformsegment naar Adobe Campaign:**

* Aanbeveling voor een limiet van 20 segmenten
* Activering is beperkt tot elke 24 uur
* Alleen Unieschema-kenmerken beschikbaar voor activering (geen ondersteuning voor array-/maps-/ervaringsgebeurtenissen).
* Aanbeveling van niet meer dan 20 kenmerken per segment
* Eén bestand per segment van alle profielen met &quot;gerealiseerde&quot; segmentlidmaatschap OF als segmentlidmaatschap is toegevoegd als kenmerk in het bestand, zowel de profielen &quot;gerealiseerde&quot; als &quot;verlaten&quot;
* De stijgende of volledige segmentuitvoer wordt gesteund
* Bestandscodering wordt niet ondersteund
* Adobe Campaign-exportworkflows die maximaal om de 4 uur kunnen worden uitgevoerd
* Zie [profiel- en gegevensinvoerinstructies voor Experience Platform](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementatiestappen

### Adobe Experience Platform

#### Schema/gegevensset

1. Vorm individuele profiel, ervaringsgebeurtenis, en multi-entiteitsschema&#39;s in Experience Platform, die op klant-geleverde gegevens wordt gebaseerd.
1. Maak Adobe Campaign-schema&#39;s voor wideLog, trackingLog, niet-te leveren adressen en profielvoorkeuren (optioneel).
1. Voeg labels voor gegevensgebruik toe aan de dataset voor beheer.
1. Creeer beleid dat bestuur op bestemmingen afdwingt.

#### Profiel/identiteit

1. Maak klantspecifieke naamruimten.
1. Identiteiten toevoegen aan schema&#39;s.
1. Laat schema&#39;s en datasets voor profiel toe.
1. Stel samenvoegregels in voor verschillende weergaven van [!UICONTROL Real-time klantprofiel] (optioneel).
1. Maak segmenten voor Adobe Campaign-gebruik.

#### Bronnen/bestemmingen

1. Gegevens in Experience Platform opnemen met streaming API&#39;s en bronconnectors.
1. Vorm [!DNL Azure] blob opslagbestemming voor gebruik met Adobe Campaign.

#### Implementatie van mobiele apps

1. Adobe Campaign SDK voor Adobe Campaign Classic of Experience Platform SDK voor Adobe Campaign Standard implementeren. Als er Experience Platform Launch aanwezig is, wordt aanbevolen Adobe Campaign Classic of Adobe Campaign Standard uit te breiden met Experience Platform SDK.

#### Adobe Campaign

1. Configureer schema&#39;s voor profiel, opzoekgegevens en relevante verpersoonlijkingsgegevens van de levering.

>[!IMPORTANT]
>
>Het is van essentieel belang dat u op dit moment begrijpt wat het gegevensmodel in het Experience Platform is voor profiel- en gebeurtenisgegevens, zodat u weet welke gegevens in Adobe Campaign vereist zijn.

#### Workflows importeren

1. Vereenvoudigde profielgegevens laden en invoeren op Adobe Campaign sFTP.
1. Laad en voeg orchestratie- en messaging personalization-gegevens toe aan Adobe Campaign sFTP.
1. Samenvoegen van Experience Platforms segmenten van [!DNL Azure] blob via workflows.

#### Workflows exporteren

1. Stuur Adobe Campaign-logbestanden om de vier uur via workflows terug naar het Experience Platform (wideLog, trackingLog, niet-te leveren adressen).
1. Verzend de profielvoorkeuren terug naar het Experience Platform via vooraf gebouwde workflows (optioneel).


## Verwante documentatie

* [Adobe Experience Platform-documentatie](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Campaign Classic-documentatie](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Campaign Standard-documentatie](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
* [Documentatie Experience Platform Launch](https://experienceleague.adobe.com/docs/launch.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
