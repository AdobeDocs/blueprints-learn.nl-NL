---
title: Campagne v7 blauwdruk
description: Leer over de blauwdruk van de Campagne v7 voor op partij-gebaseerde overseinenprogramma's, het aan boord nemen en re-marketing campagnes, directe postreclame, en eenvoudig transactieoverseinen.
solution: Campaign,Campaign Classic v7
exl-id: 71c808f5-59e6-4f49-a6ba-581ed508bc04
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '1103'
ht-degree: 0%

---

# Campagne v7 blauwdruk

Adobe Campaign v7 is een campagneprogramma dat is ontwikkeld voor traditionele marketingkanalen zoals e-mail en direct mail. Het biedt robuuste ETL- en gegevensbeheermogelijkheden om de perfecte campagne te helpen kweken en beheren. De orkestmotor van het netwerk voorziet in rijke multi-touchmarketingprogramma&#39;s met een centrale focus op batchgeoriënteerde reizen.

Het komt ook met een Etime overseinenserver worden verbonden die marketing teams toelaat om vooraf bepaalde berichten te verzenden die op een alle-inclusieve lading van om het even welk systeem van IT voor dingen zoals het terugstellen van het wachtwoord, orderbevestiging, e-ontvangstbewijzen en veel meer worden gebaseerd.

## Gebruik hoofdletters

* Berichtenprogramma&#39;s op basis van batch
* Onboarding- en hermarketingcampagnes
* Reclamecampagnes voor e-mail, brochures en tijdschriften
* Eenvoudig transactiebericht met laag volume (bijv. opnieuw instellen van wachtwoord, e-mailontvangstbewijzen, bevestiging van bestellingen enz.)

## Architectuur

<img src="assets/campaign-v7-architecture.svg" alt="Referentiearchitectuur voor Campagne v7 Blueprint" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Integratiepatronen

| Scenario | Beschrijving | Mogelijkheden |
| :-- | :--- | :--- |
| [Real-Time CDP met Adobe Campaign](rtcdp-and-campaign.md) | Toont hoe de Adobe Experience Platform Real-Time CDP en zijn gecentraliseerde segmenteringshulpmiddel met Adobe Campaign kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren | <ul><li>Delen van profiel en publiek van de Real-Time CDP naar Adobe Campaign via de workflows voor het uitwisselen van bestanden voor cloudopslag en Adobe Campaign-opname </li><li>Eenvoudig leverings- en interactiegegevens delen uit gesprekken van klanten terug naar de Real-Time CDP vanuit Adobe Campaign om zowel het Real-Time Klantprofiel te verbeteren als rapportage over communicatiecampagnes via meerdere kanalen te verzorgen</li></ul> |
| [Journey Optimizer met Adobe Campaign](ajo-and-campaign.md) | Toont hoe u Adobe Journey Optimizer kunt gebruiken om 1:1 ervaringen te ordenen gebruikend het Real-Time Profiel van de Klant en hefboomwerking het inheemse systeem van het de transactionele overseinen van Adobe Campaign om het bericht te verzenden | Gebruik het Real-Time Klantprofiel en de macht van Journey Optimizer om in de huidige ervaringen te ordenen terwijl het gebruiken van de inheemse mogelijkheden van het Overseinen in real time van Adobe Campaign om de laatste mijl mededeling te doen<br><br>Overwegingen:<br><ul><li>Kan tot 50 k berichten per uur via de server van het tijdBericht verzenden<li>Er wordt geen vertraging uitgevoerd vanuit Journey Optimizer, zodat technische controles door een pre-Sales Enterprise Architect worden uitgevoerd</li><li>Het Beheer van het besluit wordt niet gesteund in lading aan de het overseinenserver van de Campagne v7 in real time</li></ul> |

## Vereisten

Controleer de volgende voorwaarden hieronder.

### Toepassingsserver en Real-Time Messaging-server

* De Adobe Campaign Client Console is vereist voor interactie en gebruik van de Campaign v8-software. Het is een op vensters gebaseerde client en gebruikt standaard internetprotocollen (SOAP, HTTP, enz.). Zorg ervoor dat u de benodigde rechten hebt die op uw org zijn ingeschakeld voor het distribueren, installeren en uitvoeren van software

* Aanbieding toestaan voor IP-adres
   * Identificeer de IP waaiers die alle gebruikers tijdens toegang tot de cliëntconsole zullen hefboomwerking
   * Identiteit die de ondernemingssystemen zullen worden toegestaan om met de overseinenserver in real time te spreken en ervoor te zorgen zij statisch toegewezen IP of waaier hebben die u kunt lijsten van gewenste personen
   * U kunt dit instellen en beheren via het Configuratiescherm van de campagne
* sFTP-sleutelbeheer
   * SSH openbare sleutels beschikbaar hebben om met de Campagne te gebruiken verstrekt sFTP. Dit kan worden ingesteld en gecontroleerd via het Configuratiescherm van de Campagne.

### E-mail

* Heb klaar subdomain om voor bericht het verzenden te gebruiken
* Subdomain kan volledig aan Adobe (geadviseerd) worden gedelegeerd of CNAMEs kan worden gebruikt om aan Adobe-specifieke DNS servers (douane) te richten
* Google TXT-record is nodig voor elk subdomein om goede prestaties te garanderen

### Mobiele push

* Een mobiele ontwikkelaar beschikbaar hebben om de mobiele app te implementeren, configureren en bouwen
* Adobe biedt alleen een SDK om de benodigde informatie van FCM (Android) en APNS (iOS) te verzamelen voor het verzenden van berichten naar hun servers. Hoe de mobiele app moet worden gecodeerd, geïmplementeerd, beheerd en opgespoord, valt onder de verantwoordelijkheid van de klant

### Webapps (optioneel)

* Kan een extra subdomein delegeren voor op campagne gehoste afmeldings- en landingspagina&#39;s
* SSL-certificaat wordt sterk aangemoedigd

<br>

## Guardrails

Bekijk de volgende instructies.

### Grootte toepassingsserver

* Opslag kan worden geschaald naar maximaal 100 MB profielen
* Gebruikerstoegang instellen en beheren via Adobe Admin Console (aanbevolen) of lokaal in de toepassing zelf
* Het laden van gegevens naar campagne wordt verwacht via batchbestanden
   * Ondersteuning voor het laden van API-gegevens is voornamelijk bedoeld voor het beheer van profielen of eenvoudige objecten in de database (d.w.z. maken en bijwerken). Het is niet bedoeld voor het laden van grote hoeveelheden gegevens of batchbewerkingen.
   * Het gebruik van API&#39;s voor het lezen van gegevens voor aangepaste toepassingsdoeleinden wordt niet ondersteund
* API-aanroepen zijn beperkt tot 15 per seconde of 150 k per dag op schaal

### Grootte van batchcommunicatieserver

* Kan worden geschaald voor verwerking tot berichten van 2,5 MB per uur

### Real-Time communicatieservergrootte

* Kan maximaal 50 k berichten per uur verzenden
* Standaard worden twee realtime communicatieservers ingericht. Mogelijkheid om maximaal acht Real-Time Messaging-servers te schalen.

### SMS-configuratie

* De campagne verstrekt de capaciteit om met een leverancier van SMS te integreren. De leverancier wordt aangekocht door de klant en geïntegreerd met campagne voor het verzenden van SMS-berichten
* De steun is via het protocol SMPP
* Er zijn drie (3) verschillende soorten SMS die Adobe kan ondersteunen:
   * SMS MT (Mobile Terminated): een SMS dat door Adobe Campaign via de SMPP-provider naar mobiele telefoons wordt gezonden.
   * SMS MO (Mobile Originated): een SMS dat door een mobiel naar Adobe Campaign wordt verzonden via de SMPP-provider.
   * SMS SR (Status Report) of DR of DLR (Delivery Receipt): een door de mobiele telefoon via de SMPP-provider naar Adobe Campaign verzonden ontvangstbewijs dat het SMS met succes is ontvangen. Adobe Campaign kan ook SR ontvangen om aan te geven dat het bericht niet kan worden verzonden, vaak met een beschrijving van de fout.

### Mobiele pushconfiguratie

* Twee ondersteunde benaderingen voor integratie met mobiele apparaten voor pushmeldingen:
   * Experience Platform Mobile SDK (aanbevolen)
   * Campagne Mobile SDK
* Experience Platform Mobile SDK route:
   * De Markeringen van de Adobe van de hefboomwerking en de uitbreiding van het Campaign Classic voor vestiging uw integratie met het Experience Platform Mobile SDK
   * Wenst een werkende kennis van de Markeringen van de Adobe en gegevensinzameling
   * Hebt u mobiele ontwikkelervaring nodig met pushmeldingen in zowel Android als iOS om de SDK te implementeren, te integreren met FCM (Android) en APNS (iOS) om pushtoken te verkrijgen, uw app te configureren voor pushmeldingen en pushinteracties te verwerken
* Campagne Mobile SDK
   * Neem contact op met de klantenservice van de Adobe om toegang te krijgen
   * Volg de [Campagne-SDK-documentatie](https://experienceleague.adobe.com/docs/campaign-classic/using/sending-messages/sending-push-notifications/integrating-campaign-sdk-into-the-mobile-application.html?lang=nl-NL) leren hoe u de SDK kunt installeren en configureren

  >[!IMPORTANT]
  >Als u de Campagne SDK opstelt en met andere toepassingen van het Experience Cloud werkt zullen zij het gebruik van het Experience Platform Mobiele SDK voor gegevensinzameling vereisen. Dit is een andere SDK en moet worden geïnstalleerd naast de campagne-SDK

## Implementatiestappen

Zie de [Aan de slag](https://experienceleague.adobe.com/docs/campaign-classic/using/getting-started/starting-with-adobe-campaign/about-adobe-campaign-classic.html?lang=nl-NL) voor de implementatie van Adobe Campaign v7.


## Gerelateerde documentatie

* [Campagne v7-documentatie](https://experienceleague.adobe.com/docs/campaign-classic.html?lang=nl-NL)
* [Campagne v7 productbeschrijving](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentatie over Experience Platform-tags](https://experienceleague.adobe.com/docs/launch.html?lang=nl-NL)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=nl-NL)
