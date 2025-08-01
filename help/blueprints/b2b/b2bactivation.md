---
title: B2B blauwdruk voor audience and Profile Activation
description: Lever een op rekeningen gebaseerd publiek en profilering centric klantenervaringen met de ​ van het Platform van Gegevens van de Klant in real time.
solution: Real-Time Customer Data Platform
kt: 9311
exl-id: 5215d077-b0a9-4417-ae9b-f4961d4a73fa
source-git-commit: 0509c5a8ce92c25040262130a5f583cdd7f08e59
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# B2B blauwdruk voor audience and Profile Activation

Gebruik account-, opportuniteits- en hoofdinformatie die aan een individuele klant is gekoppeld om actioneerbare b2b-profielen te maken voor een betere personalisatie en doelgerichtheid op verschillende kanalen.

## Gebruiksscenario&#39;s

* Maak een publiek van mensen voor doelgerichtheid en personalisatie op verschillende kanalen tegen B2B-gegevens, waaronder accounts, mogelijkheden en leads.
* Activeer publiek aan om het even welke bestemmingen van Experience Platform voor het richten en verpersoonlijken.
* Maak een publiek van accounts (bijvoorbeeld lijsten van bedrijven) en richt zich op die bedrijven via bestemmingen zoals LinkedIn die lijsten van bedrijven accepteren als input of export naar cloudopslagbestemmingen voor doelgericht gebruik en verkoop.

## Applicaties

* Real-time Customer Data Platform B2B edition

## Integratiepatronen

* B2B-gegevensbronnen (Marketo, Salesforce, enz.) -> Real-time Customer Data Platform B2B edition -> Doelen
* Verschillende B2B-gegevensbronnen kunnen worden gebruikt om account-, lood-, opportunitegegevens en personengegevens toe te wijzen aan de B2B edition of Real-time Customer Data Platform.

## Architectuur

![ architectuur van de Verwijzing voor de Vervaging van de Activering B2B ](assets/b2b-activation.png)

## Beveiligingsmechanismen

* Merk op dat aan Marketo Engage gerelateerde instructies en implementatiestappen alleen relevant zijn wanneer Marketo Engage als bron en/of bestemming wordt gebruikt.

* Voor extra details en begeleiding voor gegevensmodel, grootte, en segmentatie verwijzen naar het [ document van de plaatsingsgidsen ](../experience-platform/guardrails.md)


### Ondersteuning voor meerdere instanties en IMS-besturingssystemen:

In het volgende voorbeeld worden de ondersteunde patronen beschreven voor het toewijzen van Experience Platform- en Marketo Engage-instanties.

#### Marketo als gegevensbron voor Experience Platform:

* Meerdere Marketo Engage-instanties naar één Experience Platform-instantie worden ondersteund.
* Eén Marketo Engage-instantie voor veel Experience Platform-instanties wordt niet ondersteund.
* Eén Marketo Engage-instantie naar één Experience Platform-instantie en meerdere sandboxen worden ondersteund.

#### Marketo als bestemming voor Experience Platform:

* Experience Platform naar veel Marketo Engage-instanties wordt ondersteund
* Veel Experience Platform-instanties naar één Marketo Engage-instantie worden ondersteund

#### Experience Platform Profile and Segmentation Guardrails:

* Zie het profiel en de segmentbegeleiding voor Experience Platform - [ de Grafieken van het Profiel en van de Segmentatie ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* B2B-segmenten die accounts, leads en opportuniteiten bevatten, maken gebruik van relaties met meerdere entiteiten die ertoe leiden dat de segmentbeoordeling in batch wordt verwerkt. Streaming segmentatie wordt ondersteund voor segmenten die zijn beperkt tot personen en gebeurtenissen.
* Neem een batch b2b-segment op als invoer voor een streaming- of Edge-segment ter ondersteuning van Gebruiksgevallen van streaming b2b-segment. Het lidmaatschap van het segment van de partij is gebaseerd op het recentste dagelijkse resultaat van de partijsegmentatie.

#### Experience Platform - Marketo Engage Source Connector:

* Het voltooien van een historische back-up kan maximaal 7 dagen duren, afhankelijk van het gegevensvolume.
* Doorlopende gegevensupdates en wijzigingen van Marketo worden via streaming API naar Experience Platform verzonden. Deze kunnen tot ongeveer 10 minuten aan het profiel worden aangepast en kunnen tot 60 minuten duren aan het datumpeer, afhankelijk van het volume.

#### Experience Platform - Marketo-bestemmingsconnector:

* Het delen van streaming segmenten van het Real-Time Customer Data Platform naar Marketo Engage kan tot 15 minuten na segmentevaluatie in beslag nemen. Het maken van back-upprofielen die al bestonden in het segment voordat het voor het eerst werd geactiveerd, kan maximaal 24 uur in beslag nemen.
* Batchsegmentatie wordt eenmaal per dag gedeeld op basis van het Experience Platform-segmentatieschema. B2B-segmenten die relaties met meerdere entiteiten gebruiken, bijvoorbeeld segmenten die gegevens in de account- en opportuntobjecten gebruiken, worden altijd in batchmodus uitgevoerd.

#### Marketo Engage-instructies:

* Contactpersonen en leads moeten in Marketo Engage worden opgenomen en rechtstreeks worden gedefinieerd voor het realtime publiek van het Customer Data Platform om overeen te komen met een Marketo Engage-contactpersoon en -lead.
* De bestemming van RTCDP Marketo kan naar keuze nieuwe lood in Marketo voor klanten tot stand brengen die in een segment zijn maar niet in Marketo bestaan.

#### Guardrails bestemming

* Raadpleeg de doeldocumentatie voor specifieke aanwijzingen over de bestemmingen. [ Guardrails van de Bestemming ](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=en)


## Implementatiestappen

Raadpleeg de B2B edition van de documentatie van het Real-time Customer Data Platform voor hulp bij het implementeren en configureren van de B2B edition van het Real-Time Customer Data Platform. [ B2B edition van het Platform van Gegevens van de Klant in real time ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)

Er zijn twee mogelijke implementatiepatronen. Zowel de mogelijkheid om B2B-gegevens en -profielen van Marketo Engage in te nemen als de mogelijkheid om B2B-gegevens van andere CRM-gegevensbronnen in te nemen.

## Implementatieoverwegingen

Richtlijnen voor belangrijke overwegingen en configuraties van de blauwdruk.

* CRM-integratie met en zonder Marketo:
Als de implementatie Marketo Engage als bron gebruikt en Marketo Engage is verbonden met de CRM, zullen de CRM-gegevens automatisch door dezelfde verbinding stromen, waardoor de noodzaak om de CRM rechtstreeks te verbinden met Platform wordt verwijderd, tenzij er aanvullende CRM-gegevensobjecten zijn die niet door Marketo worden doorgegeven. Gebruik de Experience Platform-bronaansluiting als u meer tabellen moet opnemen. Als de implementatie Marketo Engage niet als bron gebruikt, sluit u de CRM-bron rechtstreeks aan op Platform met behulp van de CRM-bron Experience Platform-connector.
* De Marketo Engage-doelconnector voor Platform, die het publiek voor activering naar Marketo Engage stuurt, deelt publieksleden op basis van overeenkomstige e-mailadressen en ECID&#39;s. Er kan een nieuwe lead worden gemaakt als de contactpersoon nog niet bestaat. Bij het maken van een nieuwe lead kunnen maximaal 50 profielkenmerken (niet-array- of kaartkenmerken) in het Real-time Customer Data Platform worden toegewezen aan Person-velden in Marketo.

## Gerelateerde documentatie

* [ B2B edition van het Platform van Gegevens van de Klant in real time ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/b2b-overview.html?lang=en)
* [ Begonnen het worden met het Platform van Gegevens van de Klant in real time B2B edition ](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [ Grafieken voor het Platform van Gegevens van de Klant in real time B2B edition ](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [ Adobe Experience Platform ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [ Marketo Engage ](https://experienceleague.adobe.com/docs/marketo/using/home.html)
* [ Adobe Experience Platform - de Schakelaar van Marketo Source ](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en)
* [ Adobe Experience Platform - de Schakelaar van de Bestemming van Marketo ](https://experienceleague.adobe.com/docs/marketo/using/product-docs/core-marketo-concepts/smart-lists-and-static-lists/static-lists/push-an-adobe-experience-cloud-segment-to-a-marketo-static-list.html)
