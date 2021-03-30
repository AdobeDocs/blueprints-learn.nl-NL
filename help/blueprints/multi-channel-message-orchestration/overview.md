---
title: Blauwdruk voor berichtenorchestratie meerdere kanalen
description: Lever individuele, just-in-time klantenervaringen over schermen.
solution: Experience Platform
kt: null
thumbnail: null
translation-type: tm+mt
source-git-commit: e1a9881996a181310bdc32cb083e4c5654139bf0
workflow-type: tm+mt
source-wordcount: '234'
ht-degree: 0%

---


# Blauwdruk voor berichtenorchestratie meerdere kanalen

De blauwdruk van de Orchestratie van het Bericht van meerdere kanalen toont hoe de merken proactief met hun klanten via kanalen zoals e-mail, SMS, en mobiele alarm kunnen in dienst nemen en communiceren.

Orchestration tools kunnen met andere interactiekanalen (zoals met binnenkomende kanalen) voor web en mobiele personalisatie integreren door de publieksstatus te delen met de besluitvormingsengines van de andere kanalen. Diverse factoren helpen bepalen welke toepassingen en plaatsingsopties te gebruiken, zoals of de klanteninteractie op trekker-gebaseerd of gepland is, welke gegevens voor het richten en verpersoonlijking, etc. noodzakelijk zijn. Deze factoren resulteren in diverse mogelijke scenario&#39;s en plaatsingsopties wanneer het opbouwen van het vermogen van de berichtorganisatie.

## Scenarios


| Scenario | Beschrijving | Experience Cloud-toepassingen |
|---|---|---|
| **Batch en transactioneel overseinen** | <ul><li>De auteur en voert geplande en partij uitgaande campagnes uit</li><li>Transactieberichten leveren</li></ul> | <ul><li>Adobe Campaign Classic en Managed Services</li><li>Adobe Campaign Standard</li></ul> |
| **[Batchberichten en Adobe Experience Platform](batch-messaging.md)** | <ul><li>Uitvoer geplande en batch-overseinencampagnes gebruikend Adobe Experience Platform als centrale hub voor klantenprofielen en segmentatie</li></ul> | <ul><li>Real-time Platform voor klantgegevens</li><li>Adobe Campaign Classic, Managed Services of Campaign Standard</li><li>Ondersteunde externe berichtenprovider</li></ul> |
| **[Gekoppelde berichten en Adobe Experience Platform](triggered-messaging.md)** | <ul><li>Voer getriggerd en het stromen overseinen uit gebruikend Adobe Experience Platform als centrale hub voor het stromen gegevens, klantenprofielen en segmentatie, met Journey Orchestration voor het stromen van reisorchestratie en berichtlevering</li></ul> | <ul><li>Adobe Experience Platform</li><li>Journey Orchestration</li><li>Adobe Campaign of een andere toepassing van derden voor het verzenden van berichten</li></ul> |
