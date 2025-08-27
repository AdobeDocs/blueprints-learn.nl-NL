---
title: Real-Time CDP met Adobe Campaign v8-integratiepatroon
description: Toont hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe Campaign v8 kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.
solution: Real-Time Customer Data Platform, Campaign
exl-id: d0291088-02ed-4e7e-b538-018ea40e38c6
source-git-commit: 10d49e3b712fc9d4ecdf41defe6e62dde2a86b72
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 3%

---

# [!DNL Real-Time CDP] met Adobe [!DNL Campaign] v8-integratiepatroon

Toont hoe de Adobe [!DNL Experience Platform] en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe Campaign kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren.

## Applicaties

* Adobe [!DNL Experience Platform Real-Time CDP]
* Adobe [!DNL Campaign] v8

## Architectuur

<img src="images/rtcdp-campaign-v8-architecture.svg" alt="Referentiearchitectuur voor het integratiepatroon Batch Messaging en Adobe Experience Platform" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Vereisten

* Voor Experience Cloud moet de klant een geldige IMS-organisatie hebben
* Adobe Experience Platform en [!DNL Campaign] worden aangeraden in dezelfde IMS-organisatie te worden ingericht voor één aanmeldings-URL
* De klant moet een V8-exemplaar van [!DNL Campaign] voorzien zijn
* De klant moet in aanmerking komen en toegang hebben voor RTCDP, Bronnen, Doelen.
* Adobe [!DNL Campaign] -productcontext moet bestaan

<br>

## Implementatiestappen

Raadpleeg de volgende documentatie over het configureren van de v8-bronaansluiting voor Campagne naar Adobe Experience Platform en de doelconnector voor het Real-time Customer Data Platform naar Campaign v8.
[ Campagne en de Connectors van AEP ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/connect/ac-aep.html?lang=nl-NL)

## Beveiligingsmechanismen

### Adobe Campaign

* Verwijs naar de de bronschakelaardocumentatie van de Campagne - [ Verbinding van Source van de Campagne ](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/adobe-applications/campaign.html?lang=nl-NL)
* Alleen ondersteuning voor implementatie van één organisatie in Adobe Campaign


### Experience Platform Real-time delen van klantgegevens Platform

* Verwijs naar de schakelaar van de Bestemming van de Campagne van RTCDP - [ Verbinding van de Campagne van RTCDP ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/email-marketing/adobe-campaign-managed-services.html?lang=nl-NL)

* Zie profiel en gegevensingestition guardrails voor AEP - [ Verbinding ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=nl-NL)
