---
title: Online/offline Audience Activation vervagen
description: Online/offline Audience Activation.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 844fff1cefe367575beb5c03aa0f0d026eb9f39b
workflow-type: tm+mt
source-wordcount: '724'
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
* Real-time Platform voor klantgegevens

## Architectuur

<img src="assets/onoff.svg" alt="Referentiearchitectuur voor het scenario Online/Offline Audience Activation" style="border:1px solid #4a4a4a" />

## Guardrails

* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* Batchsegmenttaken worden eenmaal per dag uitgevoerd op basis van het vooraf bepaalde schema. De de uitvoerbanen van het segment worden dan in werking gesteld voorafgaand aan de geplande bestemmingslevering. Merk op dat de banen van het partijsegment en de banen van de bestemmingslevering afzonderlijk lopen. Taken voor batchsegmenten en de prestaties van exporttaken zijn afhankelijk van het aantal profielen, de grootte van profielen en het aantal segmenten dat wordt geëvalueerd.
* Streaming segmenttaken worden geëvalueerd in minuten van streaminggegevens die worden ontvangen om een profiel te maken en het segmentlidmaatschap onmiddellijk naar het profiel te schrijven en een gebeurtenis te verzenden waarop toepassingen zich kunnen abonneren.
* Het streaming segmentlidmaatschap wordt onmiddellijk gehandeld voor het stromen bestemmingen en wordt geleverd in of enige segment lidmaatschapsgebeurtenissen of een micro-partij van veelvoudige profielgebeurtenissen afhankelijk van de innamepatronen van de bestemming. De geplande bestemmingen zullen een segmentuitvoerbaan van profiel voorafgaand aan levering in werking stellen, voor om het even welke segmenten die in het stromen worden geëvalueerd die via geplande levering van het partijsegment worden geleverd.
* Voor het delen van RTCDP segmentlidmaatschap aan Audience Manager, gebeurt dit binnen notulen voor het stromen segmenten en binnen notulen na voltooiing van de partijsegmentbeoordeling voor partijsegmentatie.
* De segmenten die van Experience Platform aan Audience Manager worden gedeeld worden gedeeld binnen notulen van segmentverwezenlijking - of via het stromen of partijevaluatie methode. Er is een aanvankelijke synchronisatie van de segmentconfiguratie tussen AEP en AAM zodra het segment eerst wordt gecreeerd, na ~4 uur kunnen de AEP segmentlidmaatschappen beginnen te worden gerealiseerd in AAM profielen. Het Lidmaatschap van het publiek dat vóór configuratie van het Experience Platform en het publiek van de Audience Manager wordt gerealiseerd deelt of alvorens het publiek meta-gegevens van Experience Platform aan Audience Manager wordt gesynchroniseerd zal niet in Audience Manager worden gerealiseerd tot de volgende segmentbaan waar het &quot;bestaande&quot;segmentlidmaatschap wordt gedeeld.
* De partij of het stromen bestemmingstaken van partijsegmentbanen kunnen de updates van de profielattributen evenals segmentlidmaatschap delen.
* Streaming segmentatietaken naar streamingdoelen delen alleen updates voor segmentlidmaatschap.

## Implementatiestappen

1. Vorm schema&#39;s en datasets in Experience Platform.
1. Vorm de correcte identiteiten en identiteitsnamespaces op het schema om ervoor te zorgen dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. Laat het schema en de datasets voor Profiel toe.
1. Gegevens opnemen in Platform.
1. De bepaling in real time het segment van het Platform van Gegevens van de Klant tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt bepaald aan Audience Manager moet worden gedeeld.
1. Auteurssegmenten in Experience Platform, te evalueren in batch of streaming. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. Vorm bestemmingen voor het delen van profielattributen en publiekslidmaatschappen aan gewenste bestemmingen.

## Overwegingen bij de implementatie

* Wanneer u profielgegevens deelt met bestemmingen, moet u de specifieke identiteitswaarde opnemen die door de bestemming wordt gebruikt in de doellading. Om het even welke identiteit die voor een doelbestemming noodzakelijk is moet in Platform worden opgenomen en als identiteit voor het Profiel van de Klant in real time gevormd.

* Voor activeringsscenario&#39;s waarin het publiek van Experience Platform tot Audience Manager wordt gedeeld, worden alle identiteiten inbegrepen in [!UICONTROL Real-time Klantprofiel] gedeeld aan Audience Manager. Het publiek van Experience Platform kan via de bestemmingen van de Audience Manager worden gedeeld wanneer de vereiste bestemmingsidentiteiten in [!UICONTROL Real-time het Profiel van de Klant ] worden omvat, of waar de identiteiten in [!UICONTROL Real-time Klantprofiel] met de vereiste bestemmingsidentiteiten kunnen worden verwant die in Audience Manager worden verbonden.

## Verwante documentatie

* [Productbeschrijving in realtime-Platform voor klantgegevens](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Verwante video&#39;s en Tutorials

* [Overzicht van het Platform voor realtime klantgegevens](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van Platform van realtime klantgegevens](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
