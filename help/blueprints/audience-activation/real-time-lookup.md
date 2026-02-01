---
title: Edge-profieltoegang in realtime voor internet en mobiele Personalization
description: '[!UICONTROL  toegang van het Profiel van de Klant in real time ] bij de rand om context voor Web en mobiele verpersoonlijking in real time te verstrekken.'
solution: Real-Time Customer Data Platform, Data Collection
kt: 719
exl-id: null
source-git-commit: 5530337ed9a9c67285db4abd0afba3809466e42c
workflow-type: tm+mt
source-wordcount: '1544'
ht-degree: 0%

---

# Edge-profieltoegang in realtime voor internet en mobiele Personalization

De blauwdruk van de Toegang van het Profiel van Edge in real time voor Web en Mobiele Personalization toont hoe het Web en de mobiele toepassingen tot het Profiel van de Klant van Adobe Experience Platform [!UICONTROL  in real time ] bij de rand voor high-through, laag-latentie verpersoonlijking kunnen toegang hebben.

Toepassingen hebben toegang tot profielkenmerken en publiek in realtime dankzij de latentie voor milliseconden. Kenmerken, publiekslidmaatschappen en modelgestuurde functies die in het profiel zijn opgeslagen als kenmerken, kunnen in real-time worden benaderd voor personalisatie op internet en mobiele kanalen op dezelfde pagina en op de volgende pagina.

Met deze mogelijkheid kunt u op basis van het realtime profiel van de klant zeer persoonlijke ervaringen op uw websites en mobiele toepassingen aanbieden, inclusief publiek dat is afgeleid van real-time gedragingen, kenmerken die zijn opgenomen in het Real-time profiel van de klant en berekende inzichten.

>[!NOTE]
>
>Edge-profieltoegang is speciaal ontworpen voor gebruiksgevallen met hoge doorvoer en lage latentie, zoals web/mobiele inbound-personalisatie en real-time beslissingen over aanbiedingen. Voor lagere productiescenario&#39;s zoals agent steunde steun of verkoopinteractie, is de het profielraadpleging API van de Hub geschikter. Zie de [ Toegang van het Profiel in real time voor de blauwdruk van de Scenario&#39;s van de Steun en van de Verkoop ](customer-activity.md) voor op hub-gebaseerde profieltoegang.

## Applicaties

* Gegevensplatform voor realtime klanten
* Adobe Experience Platform-gegevensverzameling (Web SDK / Mobile SDK)
* Edge Network Server-API

## Gebruiksscenario&#39;s

* In real time verpersoonlijking op Web en mobiele kanalen voor bekende klantenervaringen
* Zelfde pagina en volgende pagina personalisatie die op profielattributen en publiek in real time wordt gebaseerd
* Inhoud en aanbieding personalisatie op klantprofielen met inbegrip van gedragsgegevens in real time, attributen, en berekende inzichten wordt gebaseerd
* Integratie met verpersoonlijkingsmotoren, inhoudsbeheersystemen, en externe toepassingen voor besluitvorming in real time
* Testen en inhoud optimaliseren met realtime profielcontext

## Vereisten

Deze blauwdruk vereist het gebruik van één van de volgende methodes van de gegevensinzameling als u het profiel in real time met het stromen gegevens wilt worden bijgewerkt. Het is mogelijk om toegang in real time tot het Profiel van Edge te krijgen zonder het moeten gegevens rechtstreeks aan het Profiel van Edge verzamelen; de gegevens kunnen aan de Hub worden verzameld en aan het Profiel van Edge eveneens worden geprojecteerd. Merk op dat er toegevoegde latentie voor gegevens zal zijn die aan de Hub worden verzameld en dan aan Edge worden geprojecteerd.

* Gebruik [ SDK van het Web van Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html) als u gegevens van uw website wilt verzamelen.
* Gebruik [ Adobe Experience Platform Mobile SDK ](https://developer.adobe.com/client-sdks/home/) als u gegevens van uw mobiele toepassing wilt verzamelen.
* Gebruik [ de Server API van Edge Network ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) als u niet het Web SDK of Mobiele SDK gebruikt, of een directere server aan serververbinding uitvoert.

>[!IMPORTANT]
>
>Alvorens randverpersoonlijking uit te voeren, lees de gids op hoe te [ publieksgegevens aan de bestemmingen van de randverpersoonlijking ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations) activeren. Deze handleiding begeleidt u door de vereiste configuratiestappen voor het gebruik van dezelfde pagina en volgende pagina&#39;s voor personalisatie, voor meerdere Experience Platform-componenten.

## Architectuurdiagram

<img src="assets/real-time-edge-lookup.svg" alt="Referentiearchitectuur voor Edge Profile Access for Web en Mobile Personalization" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Beveiligingsmechanismen

* [ Guardrails voor [!UICONTROL  Real-time gegevens van het Profiel van de Klant ] ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [ Edge Network Guardrails ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html)
* Edge-profielen hebben een time-to-live (TTL) van 14 dagen. Als een gebruiker 14 dagen niet actief op de rand is geweest, kan het randprofiel verlopen en moet het van de hub worden gehaald, wat de verpersoonlijking van eerste pagina kan beïnvloeden.
* De personalisatie van Edge steunt de evaluatie van het publiekslidmaatschap in real time voor publiek dat aan de criteria van de randsegmentatie voldoet. De partij en het stromen publiek van de hub zijn ook beschikbaar bij de rand met aangewezen configuratie.

## Implementatiepatronen

De verpersoonlijking van Edge kan worden uitgevoerd gebruikend de [ bestemming van de Verbinding van 1} Douane van Personalization in het Platform van Gegevens van de Klant in real time. ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) Deze bestemming steunt veelvoudige methodes van de gegevensinzameling afhankelijk van uw gebruiksgeval.

### Patroon 1: Aangepaste, op lidmaatschap gebaseerde personalisatie voor publiek met Web SDK / Mobile SDK

* Gebruik de Adobe Experience Platform Web SDK of Mobile SDK met de Edge Network voor personalisatie op basis van het gebruikerslidmaatschap.
* Deze benadering biedt lage latentie en beste prestaties voor randverpersoonlijking die op publiekslidmaatschappen wordt gebaseerd.
* Voor Edge-segmentatie in realtime is de Web/Mobile SDK-implementatie vereist.
* SDK van het Web en Mobiele SDK **alleen steunen verpersoonlijking die op publiekslidmaatschap slechts** wordt gebaseerd.
* [ verwijs naar het Web van Experience Platform en de Mobiele Vervaging van SDK ](../experience-platform/deployment/websdk.md) voor op SDK-Gebaseerde implementatie.
* Voor de Mobiele implementatie van SDK, moet [ Adobe Journey Optimizer - beslissingsuitbreiding ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/) in Mobiele SDK worden geïnstalleerd.

### Patroon 2: Aanpassing op basis van kenmerken met Edge Network Server-API (vereist voor profielkenmerken)

>[!IMPORTANT]
>
>**op attributen-gebaseerde verpersoonlijkingsvereisten:** Als u gebaseerd op profielattributen (niet alleen publiekslidmaatschap) wilt personaliseren, moet u **** de [ Server API van Edge Network ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) met voor authentiek verklaarde server-zijintegratie gebruiken, ongeacht of u ook SDK van het Web of Mobiele SDK voor gegevensinzameling gebruikt.

* Laat integratie met derdeverpersoonlijkingsmotoren en op CDN-Gebaseerde verpersoonlijking toe.
* De server API van Edge Network wordt **vereist** om profielattributen voor verpersoonlijking veilig terug te winnen.
* U kunt profielkenmerken ophalen via de Edge Network Server-API door een integratie op de server toe te voegen die dezelfde gegevensstroom gebruikt als die u al gebruikt voor uw Web- of Mobile SDK-implementatie.
* Alle Edge Network Server API-aanroepen voor profielkenmerken moeten in een geverifieerde context worden uitgevoerd om vertrouwelijke gegevens te beschermen.
* Dit patroon laat zowel op publiekslidmaatschap-gebaseerde verpersoonlijking als op attribuut-gebaseerde verpersoonlijking toe.
* Geschikt voor verpersoonlijkingsgebruikstoepassingen aan de serverzijde, op API-Gebaseerde integratie, en scenario&#39;s die profielkenmerktoegang vereisen.

## Implementatiestappen

1. [ creeer schema&#39;s ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden opgenomen.
1. [ creeer datasets ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden opgenomen.
1. [ vorm de correcte identiteiten en de identiteit namespaces ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) op het schema om ervoor te zorgen dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. [ laat de schema&#39;s en datasets voor profiel ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html) toe.
1. [ Ingest gegevens ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. [ opstelling voegt beleid ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) samen om correcte identiteit het stitching en profiel het samenvoegen te verzekeren.
1. [ vorm een datastream ](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html) in de Inzameling van Gegevens van Experience Platform met de toegelaten bestemmingsconfiguratie. De gegevensstroom bepaalt waarin de gegevensstroom van de Inzameling van Gegevens het publiek in de reactie op de pagina zal worden omvat.
1. Voer [ of ](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html) Mobiele SDK van het Web van Adobe Experience Platform [ op Web en mobiele eigenschappen voor gegevensinzameling uit.](https://developer.adobe.com/client-sdks/home/)
1. Vorm randsegmentatie voor publiek dat evaluatie in real time vereist. [ de segmentatiedocumentatie van Edge ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html).
1. In de catalogus van Doelen, opstelling de [ bestemming van de Verbinding van Personalization van 0} Douane:](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization)
1. [ activeer publiek aan de bestemming van de randverpersoonlijking ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations). Selecteer welk publiek u aan de bestemming wilt activeren.
1. (Facultatief voor op attribuut-gebaseerde verpersoonlijking) als u zich gebaseerd op profielattributen naast kijklidmaatschap moet personaliseren, voer de [ Server API van Edge Network API ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) met voor authentiek verklaarde server-zijintegratie uit gebruikend de zelfde datastream. Dit wordt **vereist** voor de toegang tot van profielattributen.
1. Implementeer personalisatielogica in uw web/mobiele toepassing om de geëxporteerde gegevens en profielkenmerken van het publiek te gebruiken:
   * Als het gebruiken van Markeringen in Adobe Experience Platform, gebruik [ verzendt gebeurtenis volledige functionaliteit ](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html) om tot `event.destinations` variabele met de uitgevoerde gegevens toegang te hebben.
   * Als het gebruiken van geen Markeringen, gebruik [ bevelreacties ](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html) om de reactie JSON van Adobe Experience Platform te ontleden en publiek IDs en profielattributen terug te winnen.

## Implementatieoverwegingen

### Identiteitsoverwegingen

* Elke primaire identiteit kan worden gebruikt voor verpersoonlijking van randen wanneer u de SDK van het Web of de Mobile SDK met Edge Network gebruikt.
* Voor eerste login verpersoonlijking met bekende klantengegevens, moet het verpersoonlijkingsverzoek een primaire identiteit gebruiken die de bekende klantenidentiteit in het Platform van de Gegevens van de Klant in real time aanpast. Als de primaire id is ingesteld op ECID of een anonieme identiteit die nog niet is gekoppeld aan het bekende klantprofiel, duurt het enige tijd voordat de identiteitssteek wordt gerealiseerd, wat van invloed kan zijn op de beschikbaarheid van historische profielgegevens voor personalisatie.
* Edge-profielen moeten worden geïnitialiseerd voordat ze kunnen worden gebruikt voor personalisatie. Eerste bezoekers of terugkerende bezoekers van wie het randprofiel is verlopen (TTL van 14 dagen) kunnen initiële personalisatie ervaren die op beperkte profielgegevens wordt gebaseerd tot het randprofiel volledig is bevolkt.

### Op kenmerken gebaseerde personalisatie

>[!IMPORTANT]
>
>Profielkenmerken kunnen vertrouwelijke gegevens bevatten. Om dit gegeven te beschermen, moet u **gebruiken** de Server API van Edge Network [ wanneer het vormen van de bestemming van Personalization van de Douane voor op attribuut-gebaseerde verpersoonlijking. ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) Alle API-aanroepen van Edge Network Server moeten in een geverifieerde context worden uitgevoerd.

* Voor op attribuut-gebaseerde verpersoonlijking die profielattributen gebruikt, moet u een server-zijintegratie met de Server API toevoegen van Edge Network die de zelfde gegevensstroom gebruikt u voor uw implementatie van het Web of van Mobile SDK gebruikt.
* U moet via de bestemmingsconfiguratie van Aangepaste Personalization Connection bepalen welke profielkenmerken in de randprojectie moeten worden opgenomen.
* **SDK van het Web en Mobiele SDK alleen steunen verpersoonlijking die op publiekslidmaatschap** wordt gebaseerd. De server API van Edge Network wordt **vereist** om profielattributen voor verpersoonlijking veilig terug te winnen.
* Als u de Edge Network Server-API niet implementeert voor kenmerktoegang, is personalisatie alleen gebaseerd op het lidmaatschap van het publiek.
* De API-reactie voor Aangepaste Personalization met kenmerken bevat naast de publiekssegmenten ook een `attributes` -sectie.

### Overwegingen voor het publiek

* Het publiek dat door het stromen of partijsegmentatie op de hub wordt geëvalueerd wordt geprojecteerd aan de rand en kan voor verpersoonlijking worden gebruikt.
* Soorten publiek dat aan de criteria van de randsegmentatie voldoet wordt geëvalueerd in real time op de rand voor verpersoonlijking van zelfde pagina.
* Vorm aangewezen publiek voor randevaluatie die op hun gebruik in verpersoonlijkingsgebruiksgevallen in real time wordt gebaseerd.

## Gerelateerde documentatie

### Doelconfiguraties

* [ Verbinding van Personalization van de Douane ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) - Primaire implementatiegids
* [ de bestemmingen van Personalization overzicht ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/overview)
* [ activeer publiek aan de bestemmingen van de randverpersoonlijking ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)
* [ kijkt omhoog profielattributen op de rand in real time ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-edge-profile-lookup)

### SDK-documentatie

* [ de documentatie van SDK van het Web van Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html)
* [ Experience Platform Mobile SDK documentatie ](https://developer.adobe.com/client-sdks/home/)
* [ de documentatie van de Server API van Edge Network ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)
* [ de documentatie van de Markeringen van Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)
* [ Reacties van het Bevel in Web SDK ](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/commands/command-responses.html)

### Documentatie voor profiel en segmentatie

* [[!UICONTROL  documentatie ] van het Profiel van de Klant in real time](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html)
* [ Guardrails van het Profiel ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

### Tutorials

* [ Volgorde verpersoonlijking met Real-Time CDP en Adobe Target ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html)
* [ Configuratie DataStream ](https://experienceleague.adobe.com/docs/experience-platform/datastreams/configure.html)
