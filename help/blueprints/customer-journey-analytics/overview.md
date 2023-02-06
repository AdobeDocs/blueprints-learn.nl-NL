---
title: Customer Journey Analytics blauwdrukken
description: Gegevens en klantgedragingen tijdens de customer journey verenigen en analyseren
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 3bb2dada-f4cd-43f7-a0d0-f276510ad224
source-git-commit: 5110ee2a7a079945475055cbcfdabf7cdcaa0ab5
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 5%

---

# Customer Journey Analytics blauwdrukken

Customer Journey Analytics toont hoe de merken klantengegevens en gedrag van diverse interactiekanalen en bronnen kunnen verenigen om een op reis-gebaseerde mening van alle klanteninteractie tot stand te brengen. De rapportering en de analyse kunnen in de de toepassingsdienst van Customer Journey Analytics worden uitgevoerd om inzicht in klanteninteractie en gedragspatronen te evalueren en te verkrijgen.

Een volledig overzicht van de gevallen van gebruik van Customer Journey Analytics vindt u in de Customer Journey Analytics-documentatie die u hier vindt.

## Customer Journey Analytics-gebruik

[Vaak Gebruik](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=en) omvatten:

* Soorten publiek maken en publiceren naar Real-time Customer Data Platform
* Paden boven/onder omzetten
* Kanaalbetrokkenheid en conversie
* Meest bekeken inhoud
* Topcategorieën en producten
* Welke campagnes resulteerden in conversie en grotere betrokkenheid
* Analyse van het gebruik van hulpmiddelen om zelfbedieningservaringen te optimaliseren

## Architectuur voor Customer Journey Analytics

![Architectuurdiagram](assets/CJA.svg){zoomable=&quot;yes&quot;}

Voorbeelden van gevallen van primair gebruik waren:
| Blauwdruk | Beschrijving | Experience Cloud-aanvragen | |—|—|—| | **[Reisanalyse Kanaal](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cross-channel.html)**  | <ul><li>Eén geconsolideerde weergave van het gedrag van klanten op verschillende kanalen hebben door gegevens van verschillende web-, mobiele en offline eigenschappen te verenigen.</li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li><li>Adobe Analytics (optioneel)</li></ul>| | **[Soorten publiek publiceren naar Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html)** | <ul><li>Maak en publiceer publiek dat in Customer Journey Analytics (CJA) aan het Profiel van de Klant in real time in Adobe Experience Platform wordt geïdentificeerd voor klant richt en verpersoonlijking. Ideaal voor het maken van soorten publiek met behulp van historische gegevens of meer verfijnde doelgroepen van korrelfilteren en berekende velden in Customer Journey Analytics.</li></ul> | <ul><li>Real-time Customer Data Platform</li><li>Customer Journey Analytics</li> | | **[De Analyse van de Vervorming van de vraag](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/call-center.html)** | <ul><li>Bepaal welk gedrag het meest indicatief in het resulteren in agent begeleide vraag door de gegevens van het Centrum van de Vraag samen met Web, mobiele, en andere interactiegegevens te brengen is.</li><li>Deze inzichten kunnen dan worden gebruikt om de klantenervaring te optimaliseren en de weg aan agent bijgewoonde interactie door geoptimaliseerde zelf-dienst inhoud en hulpmiddelen te verminderen.  </li></ul> | <ul><li>Adobe Experience Platform</li><li>Customer Journey Analytics</li> |

## Guardraildiagram voor Customer Journey Analytics-blauwdrukken

* Voor gedetailleerde instructies en eindlatenties raadpleegt u de [document met implementatiehandleidingen](../experience-platform/deployment/guardrails.md)

![Guardraildiagram](../experience-platform/assets/CJA_guardrails.svg){zoomable=&quot;yes&quot;}

## Gerelateerde blogberichten

* [[!DNL Blueprint for Multi-Channel Orchestration in Adobe Experience Platform]](https://medium.com/adobetech/blueprint-for-multi-channel-orchestration-in-adobe-experience-platform-c68317e94184){target="_blank"}
* [[!DNL Leveraging External Data Platforms in Adobe Experience Platform Journey Orchestration]](https://medium.com/adobetech/leveraging-external-data-platforms-in-adobe-experience-platform-journey-orchestration-54fc6134fe17){target="_blank"}
* [[!DNL Event-Based Triggering on Adobe Experience Platform Orchestration Service using Apache Airflow]](https://medium.com/adobetech/event-based-triggering-on-adobe-experience-platform-orchestration-service-using-apache-airflow-8607b28251f1){target="_blank"}
* [[!DNL Adobe Campaign Classic Integration with Journey Orchestration]](https://medium.com/adobetech/adobe-campaign-classic-integration-with-journey-orchestration-ae577653281){target="_blank"}
* [[!DNL Demonstrating the Power of Adobe's New Journey Orchestration Service to Build Personalized Omnichannel Experiences in Real-Time]](https://medium.com/adobetech/demonstrating-the-power-of-adobes-new-journey-orchestration-service-to-build-personalized-aa60d88cd34){target="_blank"}
* [[!DNL Journey Orchestration in an Omnichannel World]](https://medium.com/adobetech/journey-orchestration-in-an-omnichannel-world-3a2d32d556d9){target="_blank"}
