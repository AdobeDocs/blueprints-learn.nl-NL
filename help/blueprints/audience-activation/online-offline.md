---
title: Online/offline Audience Activation vervagen
description: Online/offline Audience Activation.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 9fe9d67c5f97b633e45155bd54e2006f1b797332
workflow-type: tm+mt
source-wordcount: '500'
ht-degree: 0%

---

# Online/offline Audience Activation vervagen

Gebruik offlinekenmerken en -gebeurtenissen zoals offline bestellingen, transacties, CRM of loyaliteitsgegevens, samen met onlinegedrag voor het online aanwijzen en personaliseren.

Activeer het publiek naar bekende, op profielen gebaseerde bestemmingen, zoals e-mailproviders, sociale netwerken en advertentiebestemmingen.

## Gevallen gebruiken

* Publiek dat zich richt op bekende doelgroepen op sociale en reclamebestemmingen.
* Online personalisatie met online en offline kenmerken.
* Activeer het publiek naar bekende kanalen, zoals e-mail en SMS.

## Toepassingen

* Adobe Experience Platform
* [!UICONTROL Real-time Platform voor klantgegevens]

## Architectuur

### Online/offline Audience Activation met doelen

<img src="assets/online_offline_activation.svg" alt="Referentiearchitectuur voor de blauwdruk voor online/offline Audience Activation" style="border:1px solid #4a4a4a" />
<br>

### Online/offline Audience Activation met Experience Cloud-toepassingen

<img src="assets/activation+apps.svg" alt="Referentiearchitectuur voor de online/offline Audience Activation blauwdruk met Experience Cloud-toepassingen" style="border:1px solid #4a4a4a" />

## Guardrails

Verwijs naar de gidsen zoals die op de pagina van het Overzicht van de Activering van het Publiek en van het Profiel - [LINK](overview.md) worden geschetst

## Implementatiestappen

1. [Maak ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/schemas/create-a-schema.html) schema&#39;s voor gegevens die moeten worden ingevoerd.
1. [Maak ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) gegevenssets voor gegevens die moeten worden ingevoerd.
1. [Vorm de correcte identiteiten en de identiteit ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) namespacesop het schema om ervoor te zorgen dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. [Laat de schema&#39;s en datasets voor Profiel](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html) toe.
1. [Gegevens ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform opnemen.
1. [Levering van  [!UICONTROL realtime ]  ](https://www.adobe.com/go/audiences) platformoverschrijding van klantgegevens tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt gedefinieerd en aan Audience Manager wordt gedeeld.
1. [Maak ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html) segmentaties in het Experience Platform Het systeem bepaalt automatisch of het segment wordt geëvalueerd als batch- of streaming.
1. [Vorm bestemmingen ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html) voor het delen van profielattributen en publiekslidmaatschappen aan gewenste bestemmingen.

## Overwegingen bij de implementatie

* Wanneer u profielgegevens deelt met bestemmingen, moet u de specifieke identiteitswaarde opnemen die door de bestemming wordt gebruikt in de doellading. Om het even welke identiteit die voor een doelbestemming noodzakelijk is moet in Platform worden opgenomen en als identiteit voor [!UICONTROL Real-time Profiel van de Klant worden gevormd ].

* Voor activeringsscenario&#39;s waarin het publiek van Experience Platform tot Audience Manager wordt gedeeld, worden alle identiteiten inbegrepen in [!UICONTROL Real-time Klantprofiel] gedeeld aan Audience Manager. Het publiek van Experience Platform kan via de bestemmingen van de Audience Manager worden gedeeld wanneer de vereiste bestemmingsidentiteiten in [!UICONTROL Real-time het Profiel van de Klant ] worden omvat, of waar de identiteiten in [!UICONTROL Real-time Klantprofiel] met de vereiste bestemmingsidentiteiten kunnen worden verwant die in Audience Manager worden verbonden.

## Verwante documentatie

* [[!UICONTROL Real-time Customer Data ] PlatformProductbeschrijving](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Verwante video&#39;s en Tutorials

* [[!UICONTROL Real-time ] overzicht van klantgegevens](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van het Platform van de Gegevens van de Klant in  [!UICONTROL real time]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
