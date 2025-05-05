---
title: Experience Platform (AEP) en architectuurdiagrammen voor toepassingen
description: Bekijk de architectuurdiagrammen die laten zien hoe Adobe Experience Platform (AEP) zich verhoudt tot andere Experience Cloud-toepassingen en -toepassingsservices.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Real-Time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: 495a2480828e2c6b4caa41226f4fe67437b081c1
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 0%

---

# Adobe Experience Platform- en toepassingsarchitectuurdiagrammen

Deze architectuurdiagrammen tonen hoe Experience Platform (AEP) zich verhoudt tot andere Experience Cloud-toepassingen en -toepassingsservices.

>[!MORELIKETHIS]
>
>[ de Configuraties van de Integratie voor de Integraties van de Toepassingen van Experience Cloud ](https://experienceleague.adobe.com/docs/integrations-learn/experience-cloud/overview.html?lang=nl-NL).


## Architectuurdiagram

Dit architectuurdiagram toont hoe Adobe Experience Platform op de toepassingen en de toepassingsdiensten van Adobe Experience Cloud betrekking heeft.

<img src="assets/aep+apps.svg" alt="Experience Platform en toepassingen" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Overzichtsdiagram

<img src="assets/aep+apps_overview.svg" alt="Experience Platform en toepassingen" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

## Gedetailleerd architectuurdiagram

<img src="assets/aep+apps_detailed.svg" alt="Experience Platform en toepassingen" style="border:1px solid #4a4a4a; width:90%; margin-bottom: 15px;" class="modal-image" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Integratie van AEP- en Experience Cloud-toepassingen

| Toepassing | Experience Platform naar toepassing | Toepassing op Experience Platform |
|------------------------------|-----------------------------------|-----------------------------------|
| **Ad Cloud** | - Publiek dat in het Real-time Customer Data Platform is gedefinieerd, kan worden gedeeld met Ad Cloud om zich te richten via Audience Manager. | - Geen huidige integratie |
| **Analytics** | - Gegevens die via het web/Mobile SDK zijn verzameld, kunnen naar Adobe Analytics worden doorgestuurd. | - De gegevens die door Analytics worden verzameld, kunnen naar de gegevens-/meeropslagplaats van Experience Platform worden verzonden. [ Verbinding van Gegevens van Analytics ](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=nl-NL) |
| **Audience Manager** | - Soorten publiek die zijn gedefinieerd in het Real-Time Customer Data Platform kunnen worden gedeeld met Audience Manager voor activering naar andere cookie-doelen. | - Gegevens die samen met het lidmaatschap van het publiek van Audience Manager zijn verzameld en geëvalueerd, kunnen worden gedeeld met Experience Platform Data Lake and Profile Store. [ de Schakelaar van Audience Manager Source ](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=nl-NL) |
| **Adobe Campaign** | - Publiek dat is gedefinieerd in het Real-Time Customer Data Platform kan worden gedeeld met Campaign Classic om campagnes te starten. | - Interactie- en campagnegegevens die door Campagne worden verzameld, kunnen in Experience Platform worden opgenomen voor verder gebruik in publieksopbouw, Customer Journey Analytics en Query Service. |
| **Campaign Standard** | - Publiek dat is gedefinieerd in het Real-Time Customer Data Platform kan worden gedeeld met Campaign Standard om campagnes te starten. | - Interactie- en campagnegegevens die door Campaign worden verzameld, kunnen voor verder gebruik in Experience Platform worden opgenomen. |
| **Customer Journey Analytics** | - Gegevens die verzameld en gegeconsumeerd zijn in het Experience Platform data Lake zijn beschikbaar voor verwerking in Customer Journey Analytics. <br> - Profiel- en publieksgegevens van het Real-Time Customer Data Platform kunnen in CJA worden ingevoerd. [ RTCDP aan de integratie van CJA ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/ingest-aep-segments.html?lang=nl-NL) | - Stimuleer het publiek in CJA en deel de resultaten van het publiek naar het realtime klantgegevensplatform. [ het Publiceren van het Publiek van CJA ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=nl-NL) |
| **Experience Manager** | - Het Experience Platform-profiel kan op de server worden geopend om persoonlijke ervaringen in Experience Manager te verbeteren. | - Geen huidige integratie, interacties die worden uitgevoerd op Experience Manager-sites worden verzameld via het Experience Platform Web en Mobile SDK. |
| **Journey Optimizer** | - Gegevensgebeurtenissen en -profielen die in Experience Platform worden ingevoerd, worden ter beschikking gesteld van Journey Optimizer. | - De door Journey Optimizer geproduceerde gegevens over interacties en campagnes worden in Experience Platform verzameld voor verder gebruik. |
| **Adobe Commerce** | - Profielen en publiek die zijn ingebouwd in Real-time Customer Data Platform kunnen worden gebruikt voor personalisatie in Adobe Commerce. | - Native gegevens van Adobe Commerce kunnen via een Adobe Commerce-bronconnector naar Experience Platform worden verzonden. |
| **Marketo** | - Soorten publiek die zijn gedefinieerd in het Real-Time Customer Data Platform kunnen worden gedeeld met Marketo om campagnes te starten en objecten bij te werken. | - Marketo-accounts, contactpersonen en campagnegegevens worden in Experience Platform opgenomen voor verdere analyse. [ Verbinding van Marketo Engage ](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=nl-NL) |
| **Real-Time CDP** | - Gegevens die in Experience Platform worden ingevoerd, vormen de bron voor realtime klantprofielen die het Real-time gegevensplatform van de Klant van stroom voorzien. | - Metrische gegevens over publiek en profiel worden voor inzichten naar het datumpigment van Experience Platform gestuurd. |
| **Doel** | - Soorten publiek en profielkenmerken van het Real-time Customer Data Platform kunnen worden gedeeld met Target voor personalisatie. | - Gegevens die voor doelervaringen zijn verzameld, kunnen naar Experience Platform worden verzonden voor publieksopbouw en -analyse. |
