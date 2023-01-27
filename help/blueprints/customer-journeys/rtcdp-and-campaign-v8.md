---
title: Real-Time CDP met Adobe Campaign v8-integratiepatroon
description: Toont hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe Campaign v8 kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.
solution: Real-time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: b18d491fdefc57762932d1570401b5437bf97c76
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Real-Time CDP met Adobe Campaign v8-integratiepatroon

Toont hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe Campaign kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.

<br>

## Toepassingen

* Adobe Experience Platform Real-Time CDP
* Adobe Campaign v8

<br>

## Architectuur

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="Referentiearchitectuur voor het integratiepatroon Batch Messaging en Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" />

<br>

## Vereisten

* De klant moet voor Experience Cloud een geldige IMS-organisatie opgeven
* Adobe Experience Platform en Campagne worden aanbevolen om in dezelfde IMS-organisatie te worden ingericht voor één aanmeldings-URL
* De klant moet een V8-exemplaar van Campagne leveren
* De klant moet in aanmerking komen en toegang hebben voor RTCDP, Bronnen, Doelen.
* Adobe Campaign-productcontext moet bestaan

<br>

## Uitvoeringsstappen

Raadpleeg de volgende documentatie over het configureren van de v8-bronaansluiting voor Campagne naar Adobe Experience Platform en de Real-time Customer Data Platform-doelconnector naar Campaign v8.
[Campagne en AEP-connectors](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=en)

## Guardrails

### Adobe Campaign

* Raadpleeg de documentatie bij de bronaansluiting van de campagne - [Campagne Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=en)
* Alleen ondersteuning voor implementatie van één organisatie in Adobe Campaign
* Adobe Campaign is een bron van waarheid voor alle actieve profielen. Dit houdt in dat er profielen moeten bestaan in Adobe Campaign en dat er geen nieuwe profielen moeten worden gemaakt op basis van Experience Platform-segmenten.


### Delen van Real-time Customer Data Platform-Experience Platform

* Verwijs naar de schakelaar van de Bestemming van de Campagne RTCDP - [RTCDP-cameraverbinding](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html)
* Aanbeveling voor een limiet van 50 segmenten
* Merk op dat de verwezenlijking van het segmentlidmaatschap van AEP latent voor zowel partij (1 per dag) als het stromen (~5 min) en gebaseerd op het programma van de segmentbeoordeling is.
* De activeringsvertraging bedraagt minimaal 3 uur
* Alleen Unieschema-kenmerken beschikbaar voor activering (geen ondersteuning voor array-/maps-/ervaringsgebeurtenissen)
* Aanbeveling betreffende maximaal 20 kenmerken per segment
* Eén bestand per segment van alle profielen met &quot;gerealiseerde&quot; segmentlidmaatschap OF als segmentlidmaatschap is toegevoegd als kenmerk in het bestand, zowel de profielen &quot;gerealiseerde&quot; als &quot;verlaten&quot;
* De stijgende en volledige segmentuitvoer wordt gesteund
* Bestandscodering wordt niet ondersteund
* Zie instructies voor het opnemen van profielen en gegevens voor AEP - [Koppeling](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
