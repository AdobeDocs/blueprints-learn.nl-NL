---
title: Activering met blauwdruk van online en offline gegevens
description: Online/offline Audience Activation.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
source-git-commit: a347672abe145f5cb1eedee79bc4d8d4c08d991e
workflow-type: tm+mt
source-wordcount: '730'
ht-degree: 0%

---

# Activering met blauwdruk van online en offline gegevens

Gebruik offlinekenmerken en -gebeurtenissen zoals offline bestellingen, transacties, CRM of loyaliteitsgegevens, samen met onlinegedrag voor het online aanwijzen en personaliseren.

Activeer het publiek naar bekende, op profielen gebaseerde bestemmingen, zoals e-mailproviders, sociale netwerken en advertentiebestemmingen.

De blauwdruk voor activering met online en offline gegevens wordt nauw afgestemd op de [Activering van publiek en profiel met blauwdruk voor Experience Cloud-toepassingen](platform-and-applications.md). De aanvullende details zijn te vinden in het [Activering van publiek en profiel met blauwdruk voor Experience Cloud-toepassingen](platform-and-applications.md)   specifiek voor de integratie tussen Experience Platform- en Experience Cloud-toepassingen.

## Gevallen gebruiken

* Publiek dat zich richt op bekende doelgroepen op sociale en reclamebestemmingen.
* Online personalisatie met online en offline kenmerken.
* Activeer het publiek naar bekende kanalen, zoals e-mail en SMS.

## Toepassingen

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]

## Architectuur

### Activering met online en offline gegevens met doelen

<img src="assets/online_offline_activation.svg" alt="Referentiearchitectuur voor de blauwdruk voor online/offline Audience Activation" style="width:80%; border:1px solid #4a4a4a" />
<br>

## Guardrails

[Raadpleeg de hulplijnen die worden beschreven op de pagina Overzicht van publiek- en profielactivering.](overview.md)

## Implementatiestappen

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden ingevoerd.
1. [De juiste identiteiten en naamruimten configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) op het schema om ervoor te zorgen dat ingesloten gegevens in een verenigd profiel kunnen vastmaken.
1. [De schema&#39;s en datasets voor profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Gegevens samenvoegen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. [Voorziening [!UICONTROL Real-time Customer Data Platform] delen van segmenten](https://www.adobe.com/go/audiences) tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt gedefinieerd en aan Audience Manager wordt gedeeld.
1. [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html) in Experience Platform. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. [Doelen configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html) voor het delen van profielkenmerken en publieksleden aan gewenste bestemmingen.

## Overwegingen bij de implementatie

* Wanneer u profielgegevens deelt met bestemmingen, moet u de specifieke identiteitswaarde opnemen die door de bestemming wordt gebruikt in de doellading. Om het even welke identiteit die voor een doelbestemming noodzakelijk is moet in Platform worden opgenomen en als identiteit voor worden gevormd [!UICONTROL Klantprofiel in realtime].

### Publiek delen van Real-time Customer Data Platform naar Audience Manager

* Het lidmaatschap van het publiek van RT-CDP wordt gedeeld aan Audience Manager op streamingwijze zodra de segmentbeoordeling volledig is en aan het profiel van de Klant in real time wordt geschreven, of de segmentevaluatie in partij of het stromen voorkwam. Als het gekwalificeerde profiel de regionale verpletterende informatie voor verwante profielapparaten bevat, dan wordt het publiekslidmaatschap van RTCDP gekwalificeerd op het stromen wijze op de bijbehorende Rand van de Audience Manager. Als de profielen van RTCDP geen regionale verpletterende informatie bevatten dan worden de profiellidmaatschappen verzonden naar de hubplaats van de Audience Manager voor partijgebaseerde evaluatie en activering. Profielen die voor Edge-activering in aanmerking komen, worden binnen minuten na segmentkwalificatie geactiveerd vanuit RTCDP. Profielen die niet voor Edge-activering in aanmerking komen, komen in aanmerking voor de hub van de Audience Manager en hebben mogelijk een tijdsbestek van 12-24 uur voor verwerking.

* De regionale verpletterende informatie waarvoor de Rand van de Audience Manager de verwante apparateninformatie van het profiel wordt opgeslagen kan van de Verbinding van Gegevens van de Analyse worden verzameld wanneer de gegevens van de Analyse voor inzameling aan profiel worden toegelaten, of direct van SDK van het Web als afzonderlijke dataset van de klasse van het profielverslag die dan voor profiel moet worden toegelaten.

* Voor activeringsscenario&#39;s waarbij het publiek van Experience Platform tot Audience Manager wordt gedeeld, worden de volgende identiteiten automatisch gedeeld: IDFA, GAID, AdCloud, Google, ECID, EMAIL_LC_SHA256. Aangepaste naamruimten worden momenteel niet gedeeld.

Het publiek van Experience Platform kan door de bestemmingen van de Audience Manager worden gedeeld wanneer de vereiste bestemmingsidentiteiten in inbegrepen zijn [!UICONTROL Klantprofiel in realtime]of waar de identiteit in de [!UICONTROL Klantprofiel in realtime] kan worden gerelateerd aan de vereiste doelidentiteiten die in Audience Manager zijn gekoppeld.

## Verwante documentatie

* [[!UICONTROL Real-time Customer Data Platform] Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Verwante video&#39;s en Tutorials

* [[!UICONTROL Real-time Customer Data Platform] overzicht](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
