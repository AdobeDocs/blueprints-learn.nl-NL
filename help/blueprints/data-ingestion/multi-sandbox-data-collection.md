---
title: Vervaging van gegevensverzameling door:sturen via meerdere sandboxgebeurtenissen
description: Verzamelde gegevens door Experience Platform-SDK's streamen naar meerdere sandboxen met behulp van Event Forwarding
solution: Data Collection
kt: 7202
source-git-commit: 8ea7041103f86f034740f00a607ae36ca0b358cf
workflow-type: tm+mt
source-wordcount: '608'
ht-degree: 0%

---

# Vervaging van gegevensverzameling door:sturen via meerdere sandboxgebeurtenissen

Multi Sandbox Event Forwarding Data Collection Blueprint laat zien hoe gegevens verzameld met Adobe Experience Platform Web en Mobile SDK&#39;s kunnen worden geconfigureerd om één gebeurtenis te verzamelen en door te sturen naar meerdere AEP-sandboxen. Deze blauwdruk is een specifiek gebruiksgeval dat de eigenschap Door:sturen van de Gebeurtenis van de Markeringen van Adobe gebruikt.

Naast het repliceren van de gebeurtenis, gebruikend de Gebeurtenis het Door:sturen eigenschappen, kunt u de originele verzamelde gegevens toevoegen aan, filtreren of manipuleren die aan vereisten voor andere zandbakken voldoen. Sandbox A moet bijvoorbeeld alle gebeurtenisgegevenselementen ontvangen en Sandbox B mag alleen niet-PII-gegevens ontvangen.

Gebeurtenis doorsturen gebruikt een afzonderlijke eigenschap Tag die de gegevenselementen, -regels en -extensies bevat die nodig zijn voor uw gegevensvereisten. Met een inkomende Gebeurtenis, kan uw Gebeurtenis Door:sturen Bezit de gegevens verzamelen en beheren zoals nodig alvorens door:sturen.

Uw bestemmingsdropbox zou een gevormde het stromen van HTTP Eindpunt nodig hebben dat door de Gebeurtenis door:sturen uitbreiding HTTPS zou worden gebruikt.



## Gevallen gebruiken

* Globale gegevensrapportage - Bij het gebruik van meerdere sandboxen om besturingsomgevingen te isoleren en de noodzaak om gegevensverzameling te consolideren naar één sandbox voor rapportage tussen sandboxen. Gebeurtenis doorsturen naar een rapportsandbox stelt elke sandbox-besturingssysteem in staat gegevens te verzenden zoals deze in real-time worden verzameld naar een rapportsandbox
* De gegevensverzameling in verschillende sandboxen beheren op basis van verschillende gegevensregels voor elke sandbox-besturingsomgeving. Dergelijke werkende milieu&#39;s die het filtreren van gevoelige gegevens zoals Gezondheidszorg en Financiële Diensten vereisen

## Toepassingen

* Adobe Experience Platform Collection

## Architectuur

<img src="assets/multi-Sandbox-Data-Collection.svg" alt="Referentiearchitectuur voor doorsturen van gebeurtenissen met meerdere sandboxen" style="width:90%; border:1px solid #4a4a4a" />

1. Auteurs van tags definiëren zowel een eigenschap Tag als een eigenschap voor het doorsturen van gebeurtenissen. Hier, zullen de auteurs de Elementen, de Regels en de Acties bepalen van Gegevens die gegevensinzameling beheren. Houd in mening, loopt de code van het Bezit van de Markering op de cliënt en door een CDN gastheer verdeeld. De door:sturen van de Gebeurtenis de code van het Bezit loopt op de Server van Adobe Edge.

1. Gegevens die op de client zijn verzameld, worden naar de Edge-server verzonden. De klanten hebben ook de optie om gegevens naar hun eigen server eerst als methode van de inzameling van de serverzijde te verzenden.
WebSDK kan een Server aan het inzamelingsvermogen van de Server verstrekken. Hiervoor is echter wel een ander programmeringsmodel nodig. Raadpleeg de documentatie **Overzicht van Edge Network Server API** onder

1. De Server van de Rand van het Platform ontvangt gegevens inzamelingslading en organiseert de stroom van gegevens aan de vereiste systemen zoals Doel en Analytics.

1. De gebeurtenis die bezitsgegevens door:sturen wordt gebruikt om tot gebeurtenisgegevens toegang te hebben die in de lading aankomen. De regels kunnen ook worden gebruikt om de gegevens van de Gebeurtenis te manipuleren zoals nodig voorafgaand aan het door:sturen. Bijvoorbeeld het formatteren van de gegevens in vereiste XDM voor het stromen gegevensopname

1. Gebeurtenis doorsturen biedt de HTTPS-extensie die de mogelijkheid biedt om de gebeurtenisgegevens door te sturen naar een HTTPS-eindpunt.

1. Sandbox 2 wordt gevormd met een Streaming Eindpunt dat de door:sturen gebeurtenis ontvangt.

## Verwante documentatie

* [Documentatie voor doorsturen van gebeurtenissen](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html)
* [Video&#39;s over het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/docs/launch-learn/tutorials/server-side/overview.html)
* [Gebeurtenis doorsturen, les](https://experienceleague.adobe.com/docs/platform-learn/implement-web-sdk/event-forwarding/setup-event-forwarding.html) van de webSDK-zelfstudie
* [Experience Platform WebSDK - Overzicht](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [Overzicht van Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html)

## Verwante blogberichten

* [[!DNL Boosting Website Performance with Adobe Experience Platform Web SDK and Edge Network]](https://medium.com/adobetech/boosting-website-performance-with-adobe-experience-platform-web-sdk-and-edge-network-329fcf70fdf9)
* [[!DNL Solving Implementation Pain Points with Adobe Experience Platform Web SDK and Edge Network]](https://medium.com/adobetech/solving-implementation-pain-points-with-adobe-experience-platform-web-sdk-and-edge-network-880b635e6819)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
* [[!DNL Adobe Experience Platform Web SDK — Adobe Target]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-adobe-target-9b9f621d271)
* [[!DNL Adobe Experience Platform Web SDK Migration Scenarios for Adobe Analytics]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-migration-scenarios-for-adobe-analytics-91c255ec82b0)
* [[!DNL Unify Your Adobe Experience Platform Services with Adobe Experience Platform Web SDK]](https://medium.com/adobetech/unify-your-adobe-experience-platform-services-with-adobe-experience-platform-web-sdk-75cf6851a9fc)
* [[!DNL Accelerate Your Mobile Application Development with Adobe Experience Platform Mobile SDK and Launch]](https://medium.com/adobetech/accelerate-your-mobile-application-development-with-adobe-experience-platform-mobile-sdk-and-launch-ed023536d611)
* [[!DNL Simplifying Customer Workflows with Adobe Experience Platform Web SDK]](https://medium.com/adobetech/simplifying-customer-workflows-with-adobe-experience-platform-web-sdk-4e54fe134f4a)
