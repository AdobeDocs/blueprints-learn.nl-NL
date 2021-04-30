---
title: Online/offline Audience Activation vervagen
description: Online/offline Audience Activation.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services, Data Collection
kt: 7086
exl-id: 011f4909-b208-46db-ac1c-55b3671ee48c
translation-type: tm+mt
source-git-commit: 76fe52d8e83e075f9e7ce6e8596880181b01a7fd
workflow-type: tm+mt
source-wordcount: '421'
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

<img src="assets/online_offline_activation.svg" alt="Referentiearchitectuur voor de blauwdruk voor online/offline Audience Activation" style="border:1px solid #4a4a4a" />

## Guardrails

Verwijs naar de gidsen zoals die op de pagina van het Overzicht van de Activering van het Publiek en van het Profiel - [LINK](overview.md) worden geschetst

## Implementatiestappen

1. Vorm schema&#39;s en datasets in Experience Platform.
1. Vorm de correcte identiteiten en identiteitsnamespaces op het schema om ervoor te zorgen dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. Laat het schema en de datasets voor Profiel toe.
1. Gegevens opnemen in Platform.
1. Bepaling [!UICONTROL Real-time Customer Data Platform] segment sharing tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt bepaald om aan Audience Manager te worden gedeeld.
1. Auteurssegmenten in Experience Platform, te evalueren in batch of streaming. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. Vorm bestemmingen voor het delen van profielattributen en publiekslidmaatschappen aan gewenste bestemmingen.

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
