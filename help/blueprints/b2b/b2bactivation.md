---
title: B2B blauwdruk voor audience and Profile Activation
description: Lever een publiek op basis van accounts en maak een profilering van de belangrijkste ervaringen van klanten met Real-time Customer Data Platform ​.
solution: Real-Time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: 3dfdb1a237995e7f17e280e24f8865e992d9eb5f
workflow-type: tm+mt
source-wordcount: '895'
ht-degree: 0%

---

# B2B blauwdruk voor audience and Profile Activation

Gebruik account-, opportuniteits- en hoofdinformatie die aan een individuele klant is gekoppeld om actioneerbare b2b-profielen te maken voor een betere personalisatie en doelgerichtheid op verschillende kanalen.

## Gebruiksscenario&#39;s

* Maak een publiek van mensen voor doelgerichtheid en personalisatie op verschillende kanalen tegen B2B-gegevens, waaronder accounts, mogelijkheden en leads.
* Activeer publiek aan om het even welke Experience Platform bestemmingen voor het richten en verpersoonlijken.
* Maak een publiek van accounts (bijvoorbeeld lijsten van bedrijven) en richt zich op die bedrijven via bestemmingen als LinkedIn die lijsten van bedrijven accepteren als input of export naar cloudopslagbestemmingen voor doelgericht gebruik en verkoop.

## Applicaties

* Real-time Customer Data Platform B2B Edition

## Integratiepatronen

* B2B-gegevensbronnen (Marketo, Salesforce, enz.) -> Real-time Customer Data Platform B2B Edition -> Doelen
* Verschillende B2B-gegevensbronnen kunnen worden gebruikt om account-, lead-, opportunity- en personengegevens toe te wijzen aan de B2B Edition van Real-time Customer Data Platform.

## Architectuur

![ architectuur van de Verwijzing voor de Vervaging van de Activering B2B ](assets/b2b-activation.png)

## Beveiligingsmechanismen

* Merk op dat aan Marketo Engage gerelateerde instructies en implementatiestappen alleen relevant zijn wanneer Marketo Engage als bron en/of bestemming wordt gebruikt.

* Voor extra details en begeleiding voor gegevensmodel, grootte, en segmentatie verwijzen naar het [ document van de plaatsingsgidsen ](../experience-platform/deployment/guardrails.md)


### Ondersteuning voor meerdere instanties en IMS-besturingssystemen:

In het volgende voorbeeld worden de ondersteunde patronen voor het toewijzen van instanties van Experience Platforms en Marketo&#39;s Engage beschreven.

#### Marketo als gegevensbron voor Experience Platform:

* Meerdere Marketo&#39;s Engage-instanties naar één Experience Platform-instantie worden ondersteund.
* Eén Marketo Engage-instantie voor veel Experience Platform-instanties wordt niet ondersteund.
* Eén Marketo Engage-instantie op één Experience Platform-instantie en meerdere sandboxen wordt ondersteund.

#### Marketo als bestemming voor Experience Platform:

* Experience Platform naar veel instanties van Marketo&#39;s Engage wordt ondersteund
* Veel instanties van Experience Platforms naar één instantie Marketo Engage worden ondersteund

#### Experience Platform profiel en segmentatiehulplijnen:

* Zie het profiel en de segmentbegeleiding voor Experience Platform - [ de Grafieken van het Profiel en van de Segmentatie ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* B2B-segmenten die accounts, leads en opportuniteiten bevatten, maken gebruik van relaties met meerdere entiteiten die ertoe leiden dat de segmentbeoordeling in batch wordt verwerkt. Streaming segmentatie wordt ondersteund voor segmenten die zijn beperkt tot personen en gebeurtenissen.
* Neem een batch b2b-segment op als invoer voor een streaming- of Edge-segment ter ondersteuning van Gebruiksgevallen van streaming b2b-segment. Het lidmaatschap van het segment van de partij is gebaseerd op het recentste dagelijkse resultaat van de partijsegmentatie.

#### Experience Platform - Marketo Engage Source Connector:

* Het voltooien van een historische back-up kan maximaal 7 dagen duren, afhankelijk van het gegevensvolume.
* Doorlopende gegevensupdates en wijzigingen van Marketo worden via streaming API naar het Experience Platform verzonden. Deze kunnen tot ongeveer 10 minuten aan het profiel worden aangepast en kunnen tot 60 minuten duren aan het datumpeer, afhankelijk van het volume.

#### Experience Platform - Marketo-bestemmingsconnector:

* Het delen van streaming segmenten van Real-time Customer Data Platform naar Marketo Engage kan maximaal 15 minuten in beslag nemen. Het maken van back-upprofielen die al bestonden in het segment voordat het voor het eerst werd geactiveerd, kan maximaal 24 uur in beslag nemen.
* De segmentatie van de partij wordt eens per dag gedeeld die op het Experience Platform segmenteringsprogramma wordt gebaseerd. B2B-segmenten die relaties met meerdere entiteiten gebruiken, bijvoorbeeld segmenten die gegevens in de account- en opportuntobjecten gebruiken, worden altijd in batchmodus uitgevoerd.

#### Marketo&#39;s Engage hulplijnen:

* Contactpersonen en leads moeten in het Marketo Engage worden opgenomen en rechtstreeks worden gedefinieerd, zodat het Real-time Customer Data Platform-publiek dezelfde naam als het Marketo Engage kan kiezen.
* De bestemming RTCDP Marketo kan naar keuze tot nieuwe lood in Marketo voor klanten leiden die in een segment zijn maar niet in Marketo bestaan.

#### Guardrails bestemming

* Raadpleeg de doeldocumentatie voor specifieke aanwijzingen over de bestemmingen. [ Guardrails van de Bestemming ](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=en)


## Implementatiestappen

Voor hulp bij het implementeren en configureren van de B2B Edition van de Real-time Customer Data Platform raadpleegt u de B2B Edition van de Real-time Customer Data Platform-documentatie. [ B2B Uitgave van Real-time Customer Data Platform ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

Er zijn twee mogelijke implementatiepatronen. Zowel de mogelijkheid om B2B-gegevens en -profielen uit Marketo Engage in te nemen als de mogelijkheid om B2B-gegevens uit andere CRM-gegevensbronnen in te nemen.

## Implementatieoverwegingen

Richtlijnen voor belangrijke overwegingen en configuraties van de blauwdruk.

* CRM-integratie met en zonder Marketo:
Als de implementatie Marketo Engage als bron gebruikt en het Marketo Engage met CRM wordt verbonden, dan zullen de gegevens van CRM automatisch door de zelfde verbinding stromen, verwijderend de behoefte om CRM direct aan Platform te verbinden tenzij er extra de gegevensvoorwerpen van CRM zijn die niet door Marketo worden overgegaan. Gebruik de bronschakelaar van het Experience Platform als de extra lijsten moeten worden opgenomen. Als de implementatie geen Marketo Engage als bron zal gebruiken verbind direct CRM bron met Platform gebruikend de bron van CRM Experience Platform schakelaar.
* De bestemmingsschakelaar van het Marketo Engage voor Platform, die publiek aan Marketo Engage voor activering duwt, deelt publieksleden die op overeenkomstige e-mailadressen en ECIDs worden gebaseerd. Er kan een nieuwe lead worden gemaakt als de contactpersoon nog niet bestaat. Bij het maken van een nieuwe lead kunnen maximaal 50 profielkenmerken (niet-array- of toewijzingskenmerken) in de Real-time Customer Data Platform worden toegewezen aan Person-velden in Marketo.

## Gerelateerde documentatie

* [ B2B Uitgave van Real-time Customer Data Platform ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [ Begonnen het Worden met de Uitgave van Real-time Customer Data Platform B2B ](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [ Grafieken voor de Uitgave van Real-time Customer Data Platform B2B ](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [ Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [ Marketo Engage ](https://experienceleague.adobe.com/docs/marketo/using/home.html)
* [ Adobe Experience Platform - de Schakelaar van Marketo Source ](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en)
* [ Adobe Experience Platform - de Schakelaar van de Bestemming van Marketo ](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html)
