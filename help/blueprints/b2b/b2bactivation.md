---
title: B2B blauwdruk voor audience and Profile Activation
description: Lever een publiek op basis van accounts en maak een profilering van de belangrijkste ervaringen van klanten met Real-time Customer Data Platform ​.
solution: Real-Time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: 8355a36a235d847a6faf2398f3fadbed28ccac37
workflow-type: tm+mt
source-wordcount: '842'
ht-degree: 0%

---

# B2B blauwdruk voor audience and Profile Activation

Gebruik account-, opportuniteits- en hoofdinformatie die aan een individuele klant is gekoppeld om actioneerbare b2b-profielen te maken voor een betere personalisatie en doelgerichtheid op verschillende kanalen.

## Gebruik hoofdletters

* Maak een publiek van mensen voor doelgerichtheid en personalisatie op verschillende kanalen tegen B2B-gegevens, waaronder accounts, mogelijkheden en leads.
* Activeer publiek aan om het even welke Experience Platform bestemmingen voor het richten en verpersoonlijken.

## Toepassingen

* Real-time Customer Data Platform B2B Edition

## Integratiepatronen

* B2B-gegevensbronnen (Marketo, Salesforce, enz.) -> Real-time Customer Data Platform B2B Edition -> Doelen Verschillende B2B-gegevensbronnen kunnen worden gebruikt om account-, lead-, opportunity- en personengegevens toe te wijzen aan de B2B Edition van Real-time Customer Data Platform.

## Architectuur

<img src="assets/b2b-activation.svg" alt="Referentiearchitectuur voor de blauwdruk voor B2B-activering" style="width:90%; border:1px solid #4a4a4a" />
<br>

## Guardrails

* Merk op dat aan Marketo Engage gerelateerde instructies en implementatiestappen alleen relevant zijn wanneer Marketo Engage als bron en/of bestemming wordt gebruikt.

* Zie voor meer informatie en instructies voor de laatste en laatste latentie de [document met implementatiehandleidingen](../experience-platform/deployment/guardrails.md)


### Ondersteuning voor meerdere instanties en IMS-besturingssystemen:

In het volgende voorbeeld worden de ondersteunde patronen voor het toewijzen van Experience Platform- en Marketo Engage-instanties beschreven.

#### Marketo als gegevensbron voor Experience Platform:

* Meerdere Marketo Engage-instanties naar één Experience Platform-instantie worden ondersteund.
* Meerdere Marketo Engage-instanties naar veel Experience Platforms worden niet ondersteund.
* Eén Marketo Engage-instantie voor veel Experience Platforms wordt niet ondersteund.
* Eén Marketo Engage-instantie op één Experience Platform-instantie en meerdere sandboxen wordt ondersteund.

#### Marketo als bestemming voor Experience Platform:

* Experience Platform naar veel Marketo Engage-instanties wordt ondersteund
* Veel instanties van Experience Platforms naar één instantie Marketo Engage worden ondersteund

#### Experience Platform profiel en segmentatiehulplijnen:

* Zie het profiel en de segmentatiehulplijnen voor Experience Platform - [Profiel en segmentatiehulplijnen](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* B2B-segmenten die accounts, leads en opportuniteiten bevatten, maken gebruik van relaties met meerdere entiteiten die ertoe leiden dat de segmentbeoordeling in batch wordt verwerkt. Streaming segmentatie wordt ondersteund voor segmenten die zijn beperkt tot personen en gebeurtenissen.

#### Experience Platform - Marketo Engage Source Connector:

* Het voltooien van een historische back-up kan maximaal 7 dagen duren, afhankelijk van het gegevensvolume.
* Voortdurende gegevensupdates en wijzigingen van Marketo worden via streaming API naar het Experience Platform verzonden, die maximaal ongeveer 5 minuten aan het profiel kunnen worden doorgegeven, en ongeveer 15 minuten aan het datumpomeer, afhankelijk van het volume.

#### Experience Platform - Marketo-bestemmingsconnector:

* Het delen van streaming segmenten van Real-time Customer Data Platform naar Marketo Engage kan maximaal 5 minuten in beslag nemen.
* De segmentatie van de partij wordt eens per dag gedeeld die op het Experience Platform segmenteringsprogramma wordt gebaseerd. B2B-segmenten die accounts, leads en opportuniteiten bevatten, maken gebruik van relaties met meerdere entiteiten die ertoe leiden dat het segment in batch wordt weergegeven.

#### Marketo Engage Guardrails:

* Contactpersonen en leads moeten worden opgenomen en rechtstreeks in Marketo Engage worden gedefinieerd, zodat het Real-time Customer Data Platform-publiek zich aan een Marketo Engage-contactpersoon en -lead kan aanpassen.

#### Guardrails bestemming

* Raadpleeg de doeldocumentatie voor specifieke aanwijzingen over de bestemmingen. [Guardrails bestemming](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=en)


## Uitvoeringsstappen

Voor hulp bij het implementeren en configureren van de B2B Edition van de Real-time Customer Data Platform raadpleegt u de B2B Edition van de Real-time Customer Data Platform-documentatie. [B2B Edition van Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

Er zijn twee mogelijke implementatiepatronen. Zowel de mogelijkheid om B2B-gegevens en -profielen van Marketo Engage in te nemen als de mogelijkheid om B2B-gegevens van andere CRM-gegevensbronnen in te nemen.

## Implementatieoverwegingen

Richtlijnen voor belangrijke overwegingen en configuraties van de blauwdruk.

* CRM-integratie met en zonder Marketo: Als de implementatie Marketo Engage als bron zal gebruiken en Marketo Engage met CRM wordt verbonden, dan gebruik de Marketo bronschakelaar in Experience Platform om de gegevens van CRM in Experience Platform in te voeren. Gebruik de bronschakelaar van het Experience Platform als de extra lijsten moeten worden opgenomen. Als de implementatie geen Marketo Engage als bron zal gebruiken verbind direct CRM bron met AEP gebruikend de bron van CRM Experience Platform schakelaar.
* Het starten en verzorgen van lood uit de B2B Edition van Real-time Customer Data Platform alleen wordt niet aanbevolen. Voor dit gebruik wordt het gebruik van een gereedschap voor het koesteren van lood (zoals Marketo Engage) aanbevolen.
* De de bestemmingsschakelaar van de Marketo Engage voor AEP die publiek aan Marketo Engage voor activering duwt, duwt slechts e-mailadressen en ECIDs. Er wordt geen nieuwe lead gemaakt als de contactpersoon nog niet bestaat. Daarom moet u het profiel invoeren en gegevens naar Marketo Engage leiden.

## Gerelateerde documentatie

* [B2B Edition van Real-time Customer Data Platform](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Marketo Engage](https://experienceleague.adobe.com/docs/marketo/using/home.html?lang=en)
* [Adobe Experience Platform - Marketo Source Connector](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en)
* [Adobe Experience Platform - Marketo-bestemmingsconnector](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html?lang=en)
