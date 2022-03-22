---
title: Activering van publiek en profiel met blauwdruk voor Experience Cloud-toepassingen
description: Profielen en publiek in Experience Platform beheren en deze delen met Experience Cloud-toepassingen.
solution: Experience Platform, Real-time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 2b4e1f7134b240b68a432bfd70fe698ff634857a
workflow-type: tm+mt
source-wordcount: '741'
ht-degree: 0%

---

# Activering van publiek en profiel met blauwdruk voor Experience Cloud-toepassingen

Profielen en publiek in Experience Platform beheren en deze delen met Experience Cloud-toepassingen. Bouw en deel rijke klantensegmenten en inzichten in Experience Platform en deel hen met de toepassingen van de Experience Cloud.

Activering met Experience Cloud-toepassingen wordt nauw afgestemd op de [Bekende blauwdruk voor activering door klant](known.md).

## Gevallen gebruiken

* Personaliseer en richt zich over de kanalen van de klanteninteractie die door Experience Cloud worden aangedreven.
* Deel publiek- en profielgegevens tussen Experience Platform- en Experience Cloud-toepassingen.

## Toepassingen

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]
* Experience Platform activeren
* Experience Cloud-toepassingen
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer

## Architectuur

Zie de [Sectie Experience Platform- en toepassingsarchitectuur](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html) voor extra architectuurdiagrammen met betrekking tot de integratie van het Experience Platform met de Toepassingen van Experience Cloud.

### Activering van publiek en profiel met Experience Cloud-toepassingen

<img src="../experience-platform/assets/aep+apps_horizontal.svg" alt="Referentiearchitectuur voor de activering van publiek en profiel met Experience Cloud-toepassingen" style="width:80%; border:1px solid #4a4a4a" />
<br>

## Guardrails

Zie de [handleidingen op de pagina Overzicht van activering van publiek en profiel](overview.md)

## Overwegingen bij de implementatie

* Wanneer u profielgegevens deelt met bestemmingen, moet u de specifieke identiteitswaarde opnemen die door de bestemming wordt gebruikt in de doellading. Om het even welke identiteit die voor een doelbestemming noodzakelijk is moet in Platform worden opgenomen en als identiteit voor worden gevormd [!UICONTROL Klantprofiel in realtime].

### Publiek delen van Real-time Customer Data Platform naar Audience Manager

* Raadpleeg de volgende documentatie voor meer informatie. [Experience Platform segmentdelen met Audience Manager en andere Experience Cloud-oplossingen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html).

* Het lidmaatschap van het publiek van RT-CDP wordt gedeeld aan Audience Manager op streamingwijze zodra de segmentbeoordeling volledig is en aan het profiel van de Klant in real time wordt geschreven, of de segmentevaluatie in partij of het stromen voorkwam. Als het gekwalificeerde profiel de regionale verpletterende informatie voor verwante profielapparaten bevat, dan wordt het publiekslidmaatschap van RTCDP gekwalificeerd op het stromen wijze op de bijbehorende Rand van de Audience Manager. Als de regionale verpletterende informatie in de afgelopen 14 dagen op een profiel met een timestamp werd toegepast zal het op de Rand van de Audience Manager in het stromen worden geëvalueerd. Als de profielen van RTCDP geen regionale verpletterende informatie bevatten of de regionale verpletterende informatie is groter dan 14 dagen oud, dan worden de profiellidmaatschappen verzonden naar de hubplaats van de Audience Manager voor partijgebaseerde evaluatie en activering. Profielen die in aanmerking komen voor Edge-activering worden binnen minuten na segmentkwalificatie geactiveerd vanuit RTCDP. Profielen die niet in aanmerking komen voor Edge-activering, komen in aanmerking voor de hub van de Audience Manager en hebben mogelijk een tijdsbestek van 12-24 uur voor verwerking.

* De regionale verpletterende informatie waarvoor Rand het profiel van de Audience Manager wordt opgeslagen kan aan Experience Platform van Audience Manager, de Dienst van identiteitskaart van de Bezoeker, Analytics, Lancering, of direct van het Web SDK als afzonderlijke de klassendataset van het profielverslag worden verzameld gebruikend de &quot;gegevens vangen gebiedinformatie&quot;XDM gebiedsgroep.

* Voor activeringsscenario&#39;s waarbij het publiek van Experience Platform tot Audience Manager wordt gedeeld, worden de volgende identiteiten automatisch gedeeld: ECID, IDFA, GAID, gehashte e-mailadressen (EMAIL_LC_SHA256), AdCloud-id. Aangepaste naamruimten worden momenteel niet gedeeld.

* Het publiek van Experience Platform kan door de bestemmingen van de Audience Manager worden gedeeld wanneer de vereiste bestemmingsidentiteiten in inbegrepen zijn [!UICONTROL Klantprofiel in realtime]of waar de identiteit in de [!UICONTROL Klantprofiel in realtime] kan worden gerelateerd aan de vereiste doelidentiteiten die in Audience Manager zijn gekoppeld.

### Publiek delen van Real-time Customer Data Platform naar Target

* Zie de [Web/Mobile Personalization met on line &amp; offline gegevensblauwdruk](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/online-offline.html) voor meer informatie over het delen van profielen en publiek van Real-time Customer Data Platform naar Target.

### Publiek delen van Real-time Customer Data Platform naar Campagne en Journey Optimizer

* Zie de [Blauwdrukken voor reizen van klanten](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/overview.html) voor meer informatie over het delen van profielen en publiek van Real-time Customer Data Platform naar Campaign en Journey Optimizer.

## Verwante documentatie

* [[!UICONTROL Real-time Customer Data Platform] Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Verwante video&#39;s en Tutorials

* [[!UICONTROL Real-time Customer Data Platform] overzicht](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
