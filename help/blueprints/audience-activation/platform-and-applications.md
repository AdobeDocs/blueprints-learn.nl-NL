---
title: Activering van publiek en profiel met blauwdruk voor Experience Cloud-toepassingen
description: Profielen en publiek in Experience Platform beheren en deze delen met Experience Cloud-toepassingen.
solution: Real-Time Customer Data Platform, Target, Audience Manager, Analytics, Experience Cloud Services
kt: 7722
exl-id: f36014e8-170d-47e1-b4ec-10c0ea70612d
source-git-commit: 8355a36a235d847a6faf2398f3fadbed28ccac37
workflow-type: tm+mt
source-wordcount: '896'
ht-degree: 0%

---

# Activering van publiek en profiel met blauwdruk voor Experience Cloud-toepassingen

Profielen en publiek in Experience Platform beheren en deze delen met Experience Cloud-toepassingen. Bouw en deel rijke klantensegmenten en inzichten in Experience Platform en deel hen met de toepassingen van de Experience Cloud.

Activering met Experience Cloud-toepassingen wordt uitgelijnd op de knop [Bekende blauwdruk voor activering door klant](known.md).

## Gebruik hoofdletters

* Personaliseer en richt zich over de kanalen van de klanteninteractie die door Experience Cloud worden aangedreven.
* Deel publiek- en profielgegevens tussen Experience Platform- en Experience Cloud-toepassingen.
* Bouw rijke insignes van multi-kanaalgegevens met inbegrip van online gedragsgegevens en gegevenswetenschapsmodellen om klantenprofiel in real time in Experience Platform te verrijken dat dan met Experience Cloud toepassingen kan worden gedeeld.

## Toepassingen

* Adobe Experience Platform
* [!UICONTROL Real-time Customer Data Platform]
* Experience Platform activeren
* Experience Cloud-toepassingen
   * Adobe Audience Manager
   * Adobe Target
   * Adobe Campaign
   * Journey Optimizer
   * Marketo Engage
   * Adobe Commerce
   * Customer Journey Analytics

## Architectuur

Zie de [Sectie Experience Platform- en toepassingsarchitectuur](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-applications.html) voor extra architectuurdiagrammen met betrekking tot de integratie van het Experience Platform met de Toepassingen van Experience Cloud.

### Activering van publiek en profiel met Experience Cloud-toepassingen

<img src="../experience-platform/assets/aep+apps_horizontal.svg" alt="Referentiearchitectuur voor de activering van publiek en profiel met Experience Cloud-toepassingen" style="width:90%; border:1px solid #4a4a4a" />
<br>

## Guardrails

Zie de [handleidingen op de pagina Overzicht van activering van publiek en profiel](overview.md) en de [implementatiehandleidingen](../experience-platform/deployment/guardrails.md) pagina.

## Implementatieoverwegingen

* Wanneer u profielgegevens deelt met bestemmingen, moet u de specifieke identiteitswaarde opnemen die door de bestemming wordt gebruikt in de doellading. Om het even welke identiteit die voor een doelbestemming noodzakelijk is moet in Platform worden opgenomen en als identiteit voor worden gevormd [!UICONTROL Klantprofiel in realtime].

### Publiek delen van Real-time Customer Data Platform naar Audience Manager

* Raadpleeg de volgende documentatie voor meer informatie. [Experience Platform segmentdelen met Audience Manager en andere Experience Cloud-oplossingen](https://experienceleague.adobe.com/docs/audience-manager/user-guide/implementation-integration-guides/integration-experience-platform/aam-aep-audience-sharing.html).

* Het lidmaatschap van het publiek van RT-CDP wordt gedeeld aan Audience Manager op streamingwijze zodra de segmentbeoordeling volledig is en aan het profiel van de Klant in real time wordt geschreven, of de segmentevaluatie in partij of het stromen voorkwam.
* Als het gekwalificeerde profiel de regionale verpletterende informatie voor verwante profielapparaten bevat, dan wordt het publiekslidmaatschap van RTCDP gekwalificeerd op het stromen wijze op de bijbehorende Rand van de Audience Manager. Als de regionale verpletterende informatie op een profiel met timestamp in de afgelopen 14 dagen werd toegepast zal het op de Rand van de Audience Manager in het stromen worden geëvalueerd. Als de profielen van RTCDP geen regionale verpletterende informatie bevatten of de regionale verpletterende informatie is groter dan 14 dagen oud, dan worden het RTCDP publiekslidmaatschap verzonden naar de hubplaats van de Audience Manager voor partijgebaseerde evaluatie en activering.
* Met de regionale verpletterende informatie zijn deze profielen verkiesbaar voor de activering van Edge en zullen binnen notulen van segmentkwalificatie van RTCDP activeren, profielen die niet voor de activering van de Rand kwalificeren in de hub van de Audience Manager en kunnen een 12-24 uur tijd voor verwerking hebben.
* De regionale verpletterende informatie waarvoor Rand het profiel van de Audience Manager wordt opgeslagen kan aan Experience Platform van Audience Manager, de Dienst van identiteitskaart van de Bezoeker, Analytics, Lancering, of direct van het Web SDK als afzonderlijke de klassendataset van het profielverslag worden verzameld gebruikend de &quot;gegevens vangen gebiedinformatie&quot;XDM gebiedsgroep. Zie het get Regional Information Document voor meer informatie [Koppeling](https://experienceleague.adobe.com/docs/id-service/using/reference/regions.html?lang=en).
* Voor activeringsscenario&#39;s waarbij het publiek van Experience Platform tot Audience Manager wordt gedeeld, worden de volgende identiteiten automatisch gedeeld: ECID, IDFA, GAID, gehashte e-mailadressen (EMAIL_LC_SHA256), AdCloud-id. Aangepaste naamruimten worden momenteel niet gedeeld.
* Het publiek van Experience Platform kan door de bestemmingen van de Audience Manager worden gedeeld wanneer de vereiste bestemmingsidentiteiten in inbegrepen zijn [!UICONTROL Klantprofiel in realtime]of waar de identiteit in de [!UICONTROL Klantprofiel in realtime] kan worden gerelateerd aan de vereiste doelidentiteiten die in Audience Manager zijn gekoppeld.

### Publiek delen van Real-time Customer Data Platform naar Target

* Zie de [Bekende klantpersonalisatie - Doel en RTCDP-blauwdruk](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/web-personalization/known-personalization.html) voor meer informatie over het delen van profielen en publiek van Real-time Customer Data Platform naar Target.

### Publiek delen van Real-time Customer Data Platform naar Campagne en Journey Optimizer

* Zie de [Blauwdrukken voor reizen van klanten](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en) voor meer informatie over het delen van profielen en publiek van Real-time Customer Data Platform naar Campaign en Journey Optimizer.

### Publiek delen van Real-time Customer Data Platform naar Marketo Engage

* Zie de [B2B-blauwdrukken voor activering](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/b2bactivation.html?lang=en) voor meer informatie over het delen van profielen en publiek van Real-time Customer Data Platform naar Marketo Engage.

### Publiek delen van Real-time Customer Data Platform naar Customer Journey Analytics

* Zie de [RTCDP-publiek gedeeld met Customer Journey Analytics](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=en) voor meer informatie over het delen van het Real-time Customer Data Platform-publiek in Customer Journey Analytics.

## Gerelateerde documentatie

* [[!UICONTROL Real-time Customer Data Platform] Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html)
* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [Segmenteringsdocumentatie](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [Doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)

## Verwante video&#39;s en zelfstudies

* [[!UICONTROL Real-time Customer Data Platform] overzicht](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html)
* [Demo van [!UICONTROL Real-time Customer Data Platform]](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [Segmenten maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
