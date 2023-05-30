---
title: Journey Optimizer - blauwdruk voor communicatie van derden
description: Toont aan hoe Adobe Journey Optimizer met de systemen van het derdeoverseinen kan worden gebruikt om gepersonaliseerde mededelingen te ordenen en te verzenden.
solution: Journey Optimizer
exl-id: 3a14fc06-6d9c-4cd8-bc5c-f38e253d53ce
source-git-commit: 342b039e62ff3a8fc8a42cf292f4fc28781c21de
workflow-type: tm+mt
source-wordcount: '823'
ht-degree: 0%

---

# Blauwdruk voor berichten van derden

Toont aan hoe Adobe Journey Optimizer met de systemen van het derdeoverseinen kan worden gebruikt om gepersonaliseerde mededelingen te ordenen en te verzenden.

<br>

## Architectuur

<img src="assets/3rd-party-messaging-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Vereisten

Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u de gegevensbronnen van Journey Optimizer kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer

Andere toepassing voor berichten

* Moet REST API-aanroepen ondersteunen voor het verzenden van transactiebetalingen

<br>

## Guardrails

[Journey Optimizer Guardrails Product Link](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)

Extra Journey Optimizer-instructies:

* Het maximum is vandaag via API beschikbaar om ervoor te zorgen dat het bestemmingssysteem niet aan het punt van mislukking wordt verzadigd. Dit betekent dat berichten die het maximum overschrijden volledig worden verwijderd en nooit worden verzonden. Het roteren wordt niet ondersteund.
   * Max. verbindingen - maximumaantal http/s-verbindingen dat een doel kan afhandelen
   * Max. aantal oproepen - maximumaantal oproepen dat in periodInMp paramater kan worden gedaan
   * periodInMS - tijd in milliseconden
* Op gang gebrachte reizen met het lidmaatschap van een segment kunnen in twee modi worden uitgevoerd:
   * Batchsegmenten (elke 24 uur vernieuwd)
   * Streaming segmenten (&lt;5mins kwalificatie)
* Batchsegmenten - zorg dat u het dagelijkse volume van gekwalificeerde gebruikers begrijpt en ervoor zorgt dat het doelsysteem de burst-doorvoer per reis en over alle reizen kan verwerken
* Streamingsegmenten - moeten ervoor zorgen dat de eerste uitbarsting van profielkwalificaties kan worden afgehandeld samen met het dagelijks streaming kwalificatievolume per reis en over alle reizen
* Beslissingsbeheer wordt niet ondersteund
* Uitgaande integratie in systemen van derden
   * Geen steun voor één enkele Statische IPs aangezien onze infrastructuur multi-huurder is (moet alle datacenter IPs lijsten van gewenste personen)
   * Alleen methoden voor POSTEN en PUTTEN worden ondersteund voor aangepaste handelingen
   * Verificatieondersteuning: token | wachtwoord | OAuth2
* Kan afzonderlijke componenten van Adobe Experience Platform of Journey Optimizer niet verpakken en verplaatsen tussen verschillende sandboxen. Moet opnieuw worden geïmplementeerd in nieuwe omgevingen

<br>

Communicatiesysteem van derden

* Moet begrijpen welke belasting het systeem kan ondersteunen voor transactie-API-aanroepen
   * Aantal toegestane vraag per seconde
   * Aantal verbindingen
* Noodzaak om te begrijpen welke authentificatie wordt vereist om API vraag te maken
   * Type auteur: token | wachtwoord | OAuth2 wordt ondersteund via Journey Optimizer
   * De duur van de Auth geheime voorgeheugen: hoe lang is het teken geldig? 
* Als batch-opname alleen wordt ondersteund, moet deze worden gestreamd naar een cloudopslagengine zoals Amazon Kinesis of Azure Event Grid 1st
   * De gegevens kunnen van deze wolkenopslagmotoren worden gestroomd en in de derde partij worden geleend
   * Alle vereiste middleware is de verantwoordelijkheid van de klant of derde partij om

<br>

## Uitvoeringsstappen

### Adobe Experience Platform

#### Schema/datasets

1. [Afzonderlijke profiel-, ervarings- en multientiteitsschema&#39;s configureren](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, op basis van door de klant verstrekte gegevens.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) in Experience Platform voor gegevens die moeten worden ingevoerd.
1. [Labels voor gegevensgebruik toevoegen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/classify-data-using-governance-labels.html) in Experience Platform met de dataset voor bestuur.
1. [Beleid maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-governance/create-data-usage-policies.html) de handhaving van het bestuur op bestemmingen.

#### Profiel/identiteit

1. [Maak klantspecifieke naamruimten](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [Identiteiten toevoegen aan schema&#39;s](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html).
1. [De schema&#39;s en datasets voor Profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Samenvoegbeleid instellen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) voor verschillende weergaven van [!UICONTROL Klantprofiel in realtime] (optioneel).
1. Maak segmenten voor gebruik in Reis.

#### Bronnen/bestemmingen

1. [Gegevens in Experience Platform opnemen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) via streaming API&#39;s en bronconnectors.

### Journey Optimizer

1. Vorm uw gegevensbron van de Experience Platform en bepaal welke gebieden als deel van de profileStreaming gegevens zouden moeten worden in het voorgeheugen ondergebracht die worden gebruikt om een klantenreis in werking te stellen moet binnen Journey Optimizer eerst worden gevormd om een orchestration identiteitskaart te krijgen. Deze orchestratie-id wordt vervolgens aan de ontwikkelaar geleverd om met inname te gebruiken
1. Externe gegevensbronnen configureren
1. Aangepaste acties configureren voor toepassing van derden

### Mobiele pushconfiguratie (optioneel omdat tokens van derden kunnen worden verzameld)

1. Implementeer Experience Platform Mobile SDK om pushtokens en aanmeldingsgegevens te verzamelen en terug te koppelen naar bekende klantprofielen
1. Gebruik Adobe-tags en maak een mobiele eigenschap met de volgende extensie:
   * Adobe Journey Optimizer
   * Adobe Experience Platform Edge Network
   * Identiteit voor Edge Network
   * Mobiele kern
1. Zorg ervoor dat u beschikt over een specifieke gegevensstroom voor implementatie van mobiele apps versus webimplementaties
1. Voor meer informatie volgt u de [Adobe Journey Optimizer Mobile-gids](https://developer.adobe.com/client-sdks/documentation/mobile-foundation-extensions/)

<!--
This step with a broken link was replaced by above step.
1. For more information follow the [Adobe Journey Optimizer Mobile Guide](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)
-->

<br>

## Gerelateerde documentatie

* [Documentatie Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Documentatie over Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
* [Journey Optimizer-documentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [Journey Optimizer-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
