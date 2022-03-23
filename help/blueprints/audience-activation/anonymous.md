---
title: Anonieme Audience Activation blauwdruk
description: Leer om publiek over Web en reclamekanalen te richten die op anonieme en gedragsklantengegevens worden gebaseerd. Deze capaciteit laat gepersonaliseerde en verenigbare klantenervaringen in real time over apparaten toe.
landing-page-description: Leer om publiek over Web en reclamekanalen te richten die op anonieme en gedragsklantengegevens worden gebaseerd.
solution: Experience Platform, Audience Manager
kt: 7211
thumbnail: null
exl-id: f17599f1-2e75-4cbe-841a-9fd1dae71ada
source-git-commit: 64e7b61c1b4b1d600641fd3299a2b84154873cfb
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# Anonieme Audience Activation blauwdruk

De activering van het Anonymou-publiek is de mogelijkheid om doelgericht te zijn op en zich te personaliseren voor het publiek via internet, mobiele media en reclamekanalen op basis van anonieme apparaat- en gedragsgegevens.

## Gevallen gebruiken

* Anonieme digitale publieksgerichtheid en verpersoonlijking op de website, mobiele app, of op gesteunde reclamekanalen uitvoeren.
* Optimaliseer openingspagina en pre-authentificatie ervaringen die op bekende apparaat en gedragskenmerken worden gebaseerd.
* Gebruik het gegevensnetwerk van de derde partij van de Audience Manager om uw publiek voor het richten verder te verfijnen en uit te breiden.


## Toepassingen

* Audience Manager
* Real-time Customer Data Platform

Zowel Audience Manager als Real-time Customer Data Platform kunnen worden benut om anonieme Audience Activation voor onsite en reclamebestemmingen aan te drijven. Merk op dat Real-time Customer Data Platform slechts een ondergroep van advertentiebestemmingen met anonieme apparatenherkenningstekens steunt zoals die in [documentatie voor doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en).

Microsoft Bing, Google DV360, en TradeDesk zijn de belangrijkste gesteunde reclamebestemmingen van Real-time Customer Data Platform voor anonieme op apparaat gebaseerde het richten. Daarnaast ondersteunt Real-time Customer Data Platform een groot aantal bekende klantgebaseerde doelen die zijn gecatalogiseerd in de [documentatie voor doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/advertising/overview.html?lang=en) en zoals beschreven in [bekende blauwdruk voor klantactivering](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## Architectuur

<img src="assets/anonymous_activation.svg" alt="Referentiearchitectuur voor de anonieme blauwdruk Audience Activation" style="width:80%; border:1px solid #4a4a4a" />

<br>

## Implementatiestappen

1. [Audience Manager implementeren](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/implement-audience-manager.html?lang=en#implementation-integration-guides).
1. Gegevens verzamelen naar Audience Manager.
1. Vorm signalen en eigenschappen voor gebruik in segmentdefinities.
1. Maak segmenten in Audience Manager.
1. Vorm bestemmingen in Audience Manager om publiek te delen.

Voor implementatiestappen van Real-time Customer Data Platform raadpleegt u de [bekende blauwdruk voor klantactivering](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).

## Verwante documentatie

* [Audience Manager](https://experienceleague.adobe.com/docs/audience-manager.html?lang=en)
* [Experience Cloud [!UICONTROL Soorten publiek]](https://experienceleague.adobe.com/docs/core-services/interface/audiences/audience-library.html)
* [Audience Manager integreren met doel](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-other-solutions/aam-target-integration.html)
* [Adobe Analytics Segment Sharing through Audience Manager](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html)
* [Bekende blauwdruk voor activering door klant](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html).
* [Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/overview.html)
