---
title: Journey Optimizer met Adobe Campaign v8-blauwdruk
description: Toont aan hoe Adobe Journey Optimizer met Adobe Campaign kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in Campagne te gebruiken
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
source-git-commit: 6901596cbb661ffa8cf57c6ae958db1978bf1520
workflow-type: tm+mt
source-wordcount: '1128'
ht-degree: 0%

---

# Journey Optimizer met Adobe Campaign v8

Toont aan hoe Adobe Journey Optimizer met Adobe Campaign kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in Campaign te gebruiken.

<br>

## Architectuur

<img src="assets/ajo-campaign-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>Het gebruik van zowel Journey Optimizer als Campagne om berichten onafhankelijk van elkaar te verzenden is mogelijk, maar bevat enkele technische overwegingen die moeten worden doorgelicht. Als u deze route wilt nastreven, gelieve met uw Architect van de Onderneming van de pre-Verkoop samen te werken om ervoor te zorgen dat u een inzicht in hebt wat zal worden vereist om de implementatie te steunen.

<br>

## Vereisten

### Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u de gegevensbronnen van Journey Optimizer kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer
* Journey Optimizer en Campagne worden geleverd in dezelfde IMS Org

### Campagne v8

* De instantie van de uitvoering van de dienst van het overseinen in real time (d.w.z. het Centrum van het Bericht) moet door Adobe Beheerde Cloud Services worden ontvangen
* Alle bericht authoring wordt uitgevoerd binnen de Campagne-instantie zelf

<br>

## Guardrails

[Journey Optimizer Guardrails Product Link](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)

### Extra Journey Optimizer Guardrails

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
* Zakelijke gebeurtenissen worden niet ondersteund
* Uitgaande integratie in systemen van derden
   * Geen steun voor één enkele Statische IPs aangezien onze infrastructuur multi-huurder is (moet alle datacenter IPs lijsten van gewenste personen)
   * Alleen methoden voor POSTEN en PUTTEN worden ondersteund voor aangepaste handelingen
   * Verificatieondersteuning: token | wachtwoord | OAuth2
* Kan afzonderlijke componenten van Adobe Experience Platform of Journey Optimizer niet verpakken en verplaatsen tussen verschillende sandboxen. Moet opnieuw worden geïmplementeerd in nieuwe omgevingen

<br>

### Campagne (v8)

* De instantie van de uitvoering van het Centrum van het Bericht moet door Adobe Beheerde Cloud Services worden ontvangen
* Moet aanwezig zijn op v7-build >21.1 of v8
* De productie van berichten
   * AC (v7) 50 k per uur
   * AC (v8) tot 1 MB per uur gebaseerd op pakket
* AC (v7) steunt slechts gebeurtenis geïnitieerde reis
   * Geen segment- of segmentlidmaatschap gestart voor Journey
   * Reis op basis van gebeurtenissen van het type Audience Read en Business wordt niet ondersteund vanwege het volume dat het kan verzenden naar de uitvoeringsinstanties
* AC (v7) noch AC (v8) steunt Beslissingsbeheer in berichten
* Geen vertraging van uitgaande API vraag die aan Campagne wordt gemaakt
* Met Campagne v8.4 is het mogelijk om Adobe Campaign Managed Services Source Connector in Experience Platform te gebruiken voor het synchroniseren van bezorgings- en traceringsgebeurtenissen van Campagne naar Experience Platform. Raadpleeg de documentatie bij de Source Connector voor meer informatie. [Koppeling](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

<br>

## Implementatiestappen

### Adobe Experience Platform

#### Schema/gegevensset

1. [Afzonderlijke profiel-, ervarings- en multientiteitsschema&#39;s configureren](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) in Experience Platform, op basis van door de klant verstrekte gegevens.
1. Creeer de op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voor Adobe Campaign bredeLog, trackingLog en niet-te leveren adreslijsten (facultatief).
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
1. Aangepaste acties voor de instantie Campagne configureren

### Campagne v8

* De malplaatjes van het bericht moeten met aangewezen verpersoonlijkingscontext worden gevormd
* Voor de norm van de Campagne - de werkschema&#39;s van de Uitvoer moeten worden gevormd om de transactionele overseinenlogboeken terug naar het Experience Platform uit te voeren. De aanbeveling moet ten hoogste om de vier uur lopen.
* Voor Campagne v8.4 is het mogelijk om Adobe Campaign Managed Services Source Connector in Experience Platform te gebruiken om bezorgings- en traceringsgebeurtenissen van Campagne in Experience Platform te synchroniseren. Raadpleeg de documentatie bij de Source Connector voor meer informatie. [Koppeling](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html)

### Mobiele pushconfiguratie (optioneel)

1. Implementeer Experience Platform Mobile SDK om pushtokens en aanmeldingsgegevens te verzamelen en terug te koppelen naar bekende klantprofielen
1. Gebruik Adobe-tags en maak een mobiele eigenschap met de volgende extensie:
   * Adobe Journey Optimizer | Adobe Campaign Classic | Adobe Campaign Standard
   * Adobe Experience Platform Edge Network
   * Identiteit voor Edge Network
   * Mobiele kern
1. Zorg ervoor dat u beschikt over een specifieke gegevensstroom voor implementatie van mobiele apps versus webimplementaties
1. Voor meer informatie volgt u de [Adobe Journey Optimizer Mobile-gids](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-journey-optimizer)

   >[!IMPORTANT]
   >Mobiele tokens moeten mogelijk zowel in Journey Optimizer als in Campagne worden verzameld als er behoefte is aan realtime communicatie via Journey Optimizer en batchpushberichten via Campagne. Voor campagne v8 is het exclusieve gebruik van de Campagne SDK vereist voor het vastleggen van push-tokens.

<br>

## Verwante documentatie

* [Documentatie Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Documentatie over Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
* [Journey Optimizer-documentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [Journey Optimizer-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Campagne v8-documentatie](https://experienceleague.adobe.com/docs/campaign-v8.html?lang=en)
* [Campagne v7-documentatie](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=en)
* [Campaign Standard-documentatie](https://experienceleague.adobe.com/docs/campaign-standard.html?lang=en)
