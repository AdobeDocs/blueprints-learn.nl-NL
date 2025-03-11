---
title: Gegevensplatform voor realtime klanten en Adobe Target
description: RTCDP-profielen en -soorten publiek integreren met Adobe Target.
landing-page-description: RTCDP-profielen en -soorten publiek integreren met Adobe Target.
short-description: RTCDP-profielen en -soorten publiek integreren met Adobe Target.
solution: Real-Time Customer Data Platform, Target, Experience Platform
kt: 7194
thumbnail: thumb-web-personalization-scenario2.jpg
exl-id: 29667c0e-bb79-432e-af3a-45bd0b3b43bb
source-git-commit: de447727048098ecc0bf8598fe3bca386779f543
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---


# Integratie in realtime van klantgegevensplatform met Adobe Target

## Gebruiksscenario&#39;s

* Online personalisatie met bekende klantgegevens
* Optimalisatie landingspagina
* Personalization is gebaseerd op eerdere product/inhoud-weergaven, product/inhoud-affiniteit, milieukenmerken en demografie, naast offlinegegevens zoals transacties, loyaliteits- en CRM-gegevens, en gemodelleerde inzichten
* Deel en doelpubliek dat is gedefinieerd in het Real-Time Customer Data Platform op websites en mobiele apps met Adobe Target

## Applicaties

* [!UICONTROL  Real-time Platform van Gegevens van de Klant ]
* Adobe Target

### Referentiedocumentatie

* [ Verbinding van Adobe Target voor het Platform van Gegevens van de Klant in real time ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html)
* [ Configuratie van Edge DataStream ](https://experienceleague.adobe.com/docs/experience-platform/edge/fundamentals/datastreams.html)

## Integratiepatronen

| Integratiepatroon | Capaciteit | Voorwaarden |
|--------------------|------------|---------------|
| **Real-time segmentevaluatie op Edge die van het Platform van Gegevens van de Klant in real time aan Doel wordt gedeeld** | - Evalueer publiek in real time voor zelfde of volgende paginagroonitalisering op de Edge. <br> - Alle segmenten die op streaming- of batchwijze worden geëvalueerd, worden ook geprojecteerd op de Edge Network en worden opgenomen in de evaluatie en personalisatie van de randsegmenten. | - Web/Mobile SDK moet worden geïmplementeerd voor de Edge Network Server-API. <br> - DataStream moet in Experience Edge worden geconfigureerd met de extensie Target en Experience Platform ingeschakeld. <br> - Het doel van het doel moet in de Doelen van het Platform van Gegevens van de Klant in real time worden gevormd. <br> - Voor integratie met Doel is dezelfde IMS-volgorde vereist als voor de Experience Platform-instantie. |
| **het stromen en partijpubliek die van het Platform van Gegevens van de Klant in real time aan Doel via de benadering van Edge delen** | - Deel streaming en batchpubliek van Real-time Customer Data Platform naar Target via de Edge Network. <br> - Voor publiek dat in real time wordt geëvalueerd, is de Web SDK- en Edge Network-implementatie vereist. | - Web/Mobile SDK of Edge API-implementatie van Target is niet vereist voor het delen van streaming en het batchgebruik van RTCDP naar Target, maar is vereist om realtime segment-evaluatie mogelijk te maken. <br> - Als u AT.js gebruikt, wordt alleen profielintegratie met de naamruimte van de ECID-identiteit ondersteund. <br> - Voor opzoekingen naar aangepaste naamruimten op de Edge is de Web SDK/Edge API-implementatie vereist en moet elke identiteit als een identiteit worden ingesteld in het identiteitsoverzicht. <br> - Het doel van het doel moet in de Doelen van het Platform van de Gegevens van de Klant in real time worden gevormd, slechts wordt de standaardproductiestandaard in RTCDP gesteund. <br> - Voor integratie met Doel is dezelfde IMS-volgorde vereist als voor de Experience Platform-instantie. |
| **het stromen en partijpubliek die van het Platform van de Gegevens van de Klant in real time aan Doel en Audience Manager via de Begrip van de Dienst het Delen van het Publiek delen** delen | - Dit integratiepatroon kan worden benut wanneer extra verrijking van gegevens en publiek van derden in Audience Manager gewenst is. | - Web/Mobile SDK is niet vereist voor het delen van streaming en batchpubliek naar Doel, maar is vereist voor het inschakelen van realtime segment-evaluatie. <br> - Als u AT.js gebruikt, wordt alleen profielintegratie met de naamruimte van de ECID-identiteit ondersteund. <br> - Voor opzoekingen naar aangepaste naamruimten op de Edge is de Web SDK/Edge API-implementatie vereist en moet elke identiteit als een identiteit worden ingesteld in het identiteitsoverzicht. <br> - De projectie van het publiek via de service voor het delen van het publiek moet zijn ingericht. <br> - Voor integratie met Doel is dezelfde IMS-volgorde vereist als voor de Experience Platform-instantie. <br> - Alleen het publiek van de standaardproductiesandbox ondersteunt de hoofdservice voor het delen van het publiek. |

## In real time, het stromen, en partijpubliek die aan Adobe Target delen

Architectuur

<img src="assets/RTCDP+Target.svg" alt="Referentiearchitectuur voor de online/offline Personalization-blauwdruk voor het web" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Sequentiedetail

<img src="assets/RTCDP+Target_flow.svg" alt="Referentiearchitectuur voor de online/offline Personalization-blauwdruk voor het web" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

Overzicht architectuur

<img src="assets/personalization_with_apps.svg" alt="Referentiearchitectuur voor de online/offline Personalization-blauwdruk voor het web" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Implementatiepatronen

Bekende Customer Personalization wordt ondersteund via verschillende implementatiemethoden.

### Implementatiepatroon 1 - [!DNL Edge Network] met Web/Mobile SDK of [!DNL Edge Network] API (aanbevolen aanpak)

* De [!DNL Edge Network] gebruiken met de SDK Web/Mobile. Voor Edge-segmentatie in realtime is de implementatiebenadering van Web/Mobile SDK of Edge API vereist.
* [ verwijs naar het Web van Experience Platform en de Mobiele Vervaging van SDK ](../experience-platform/deployment/websdk.md) voor de op SDK gebaseerde implementatie.
* Voor gebruik in Mobiele SDK moet de [ Adobe Journey Optimizer - beslissingsuitbreiding ](https://developer.adobe.com/client-sdks/edge/adobe-journey-optimizer-decisioning/) worden geïnstalleerd.
* [ verwijs naar  [!DNL Edge Network]  Server API ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html) voor een API gebaseerde implementatie van Adobe Target met het Profiel van Edge.

### Implementatiepatroon 2 - Toepassingsspecifieke SDK&#39;s

traditionele toepassingsspecifieke SDK&#39;s gebruiken (bijvoorbeeld AT.js en AppMeasurement.js). Edge-segmentevaluatie in realtime wordt niet ondersteund met deze implementatiebenadering. Streaming en het delen van batchgebruikers vanuit de Experience Platform-hub worden echter ondersteund met deze implementatieaanpak.

[ verwijs naar de Documentatie van de Verbinding van Adobe Target ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection)
[ Verwijs naar de toepassing specifieke Vervaging van SDK ](../experience-platform/deployment/appsdk.md)

## Implementatieoverwegingen

* Elke primaire identiteit kan worden gebruikt bij het gebruik van implementatiepatroon 1 zoals hierboven beschreven met de [!DNL Edge Network] en Web SDK.
* De eerste login verpersoonlijking met bekende klantengegevens die in RTCDP werden opgenomen vereist dat het verpersoonlijkingsverzoek een primaire identiteit heeft die de bekende grafiek van de klantenidentiteit in het Platform van de Gegevens van de Klant in real time aanpast. Als de primaire id is ingesteld op ECID of een identiteit die nog niet is gekoppeld aan het bekende klantprofiel, duurt het enkele minuten voordat de identiteitssteek aan de rand wordt gerealiseerd en voordat de bekende klantgegevens van de Edge-versie zijn opgenomen.
* Edge-profielen hebben momenteel een TTL van 14 dagen. Als een gebruiker zich niet heeft aangemeld of 14 dagen niet actief is geweest aan de rand, kan het profiel aan de rand verlopen zijn. De rand moet daarom het profiel ophalen van de hub om de historische profielweergave te kunnen gebruiken voor personalisatie met oudere ingesloten profielkenmerken en segmenten. Dit zal resulteren in personalisatie met de historische weergave van profielen die plaatsvindt op volgende paginaweergaven versus de eerste aanmelding.

## Gerelateerde documentatie

### SDK-documentatie

* [ de documentatie van SDK van het Web van Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/edge/home.html)
* [ de documentatie van de Markeringen van Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)
* [ de documentatie van de Dienst van identiteitskaart van Experience Cloud ](https://experienceleague.adobe.com/docs/id-service/using/home.html)

### Segmenteringsdocumentatie

* [ het Overzicht van de Segmentatie van Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/home.html)
* [ Realtime Segmentatie ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/edge-segmentation.html)
* [ het stromen Segmentatie ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)
* [ het Segment dat van Adobe Analytics door Adobe Audience Manager ](https://experienceleague.adobe.com/docs/analytics/components/segmentation/segmentation-workflow/seg-publish.html) deelt
* [ Configuratie van het Beleid van de Fusie ](https://experienceleague.adobe.com/docs/experience-platform/profile/merge-policies/ui-guide.html?lang=en#create-a-merge-policy)

### Tutorials

* [ Volgorde verpersoonlijking met Real-Time CDP en Adobe Target ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/experience-cloud/next-hit-personalization.html?lang=en)
