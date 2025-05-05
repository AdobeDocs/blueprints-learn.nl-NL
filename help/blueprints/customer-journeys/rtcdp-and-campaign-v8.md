---
title: Real-Time CDP met Adobe Campaign v8-integratiepatroon
description: Toont hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe Campaign v8 kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: a1f3aef5b508575019bd651b9706efc7d6db5306
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# [!DNL Real-Time CDP] met Adobe [!DNL Campaign] v8-integratiepatroon

De Adobe tonen [!DNL Experience Platform] en zijn Real-Time Klantprofiel en gecentraliseerd segmentatiehulpmiddel kunnen met Adobe Campaign worden gebruikt om gepersonaliseerde gesprekken te leveren.

## Toepassingen

* Adobe [!DNL Experience Platform Real-Time CDP]
* Adobe [!DNL Campaign] v8

## Architectuur

<img src="assets/rtcdp-campaignv8-architecture.svg" alt="Referentiearchitectuur voor het integratiepatroon Batch Messaging en Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Vereisten

* De klant moet voor Experience Cloud een geldige IMS-organisatie hebben
* Adobe Experience Platform en [!DNL Campaign] wordt aangeraden om voor één aanmeldings-URL in dezelfde IMS-organisatie te worden ingericht
* De klant moet een V8-exemplaar van [!DNL Campaign]
* De klant moet in aanmerking komen en toegang hebben voor RTCDP, Bronnen, Doelen.
* Adobe [!DNL Campaign] productcontext moet bestaan
<br>

## Implementatiestappen

Raadpleeg de volgende documentatie over het configureren van de v8-bronaansluiting voor Campagne naar Adobe Experience Platform en de Real-time Customer Data Platform-doelconnector naar Campaign v8.
[Campagne en AEP-connectors](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=nl-NL)

## Guardrails

### Adobe Campaign

* Raadpleeg de documentatie bij de bronaansluiting van de campagne - [Campagne Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=nl-NL)
* Alleen ondersteuning voor implementatie van één organisatie in Adobe Campaign


### Delen van Real-time Customer Data Platform-Experience Platform

* Verwijs naar de schakelaar van de Bestemming van de Campagne RTCDP - [RTCDP-cameraverbinding](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=nl-NL)

* Zie instructies voor het opnemen van profielen en gegevens voor AEP - [Koppeling](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=nl-NL)
