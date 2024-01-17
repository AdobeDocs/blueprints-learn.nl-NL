---
title: Campagne v8 blauwdruk, campagne en platform
description: Adobe Campaign v8 is het volgende-gen campagnehulpmiddel dat voor traditionele marketing kanalen zoals e-mail en direct mail wordt gebouwd. Het biedt robuuste ETL- en gegevensbeheermogelijkheden om de perfecte campagne te helpen kweken en beheren. De orkestmotor van het netwerk voorziet in rijke multi-touchmarketingprogramma's met een centrale focus op batchgeoriënteerde reizen.  Het komt ook met een scalable Real-Time overseinenserver worden verbonden die marketing teams toelaat om vooraf bepaalde berichten te verzenden die op een alle-inclusieve lading van om het even welk systeem van IT voor dingen zoals het terugstellen van het wachtwoord, orderbevestiging, e-ontvangstbewijzen en veel meer worden gebaseerd.
solution: Campaign,Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: ac6e27e88854f5a05a7ff7428cd4375b3532f632
workflow-type: tm+mt
source-wordcount: '1074'
ht-degree: 0%

---

# Campagne v8 blauwdruk

Adobe Campaign v8 is het volgende-gen campagnehulpmiddel dat voor traditionele marketing kanalen zoals e-mail en direct mail wordt gebouwd. Het biedt robuuste ETL- en gegevensbeheermogelijkheden om de perfecte campagne te helpen kweken en beheren. De orkestmotor van het netwerk voorziet in rijke multi-touchmarketingprogramma&#39;s met een centrale focus op batchgeoriënteerde reizen.  Het komt ook met een scalable Real-Time overseinenserver worden verbonden die marketing teams toelaat om vooraf bepaalde berichten te verzenden die op een alle-inclusieve lading van om het even welk systeem van IT voor dingen zoals het terugstellen van het wachtwoord, orderbevestiging, e-ontvangstbewijzen en veel meer worden gebaseerd.

<br>

## Gebruik hoofdletters

* Zeer complexe batchgebaseerde berichtprogramma&#39;s
* Onboarding- en hermarketingcampagnes
* Reclamecampagnes voor e-mail, brochures en tijdschriften
* Eenvoudig transactiebericht (bijv. opnieuw instellen van wachtwoord, e-mailontvangstbewijzen, bevestiging van bestelling, enz.)
* Integratie van Campagnegegevens in Adobe Experience Platform voor analyse en profielopbouw
* Het delen van het publiek van Real-time Customer Data Platform naar Campaign.

<br>

## Architectuurdiagrammen

Meer informatie over de implementatiemodellen voor Campagne v8 in [deze pagina](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"}.

### Implementatie van Campagne Enterprise (FFDA)

<img src="assets/P4-architecture.png" alt="Referentiearchitectuur voor blauwdruk van campagne v8 (P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


### Implementatie van FDA voor campagne v8

<img src="assets/P1-P3-architecture.png" alt="Referentiearchitectuur voor campagne v8 Blueprint (P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Integratiepatronen

| Scenario | Beschrijving | Mogelijkheden |
| :-- | :--- | :--- |
| [Gegevensplatform voor realtime klanten met Adobe Campaign](rtcdp-and-campaign-v8.md) | Toon hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe Campaign kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren | <ul><li>Delen van profielen en soorten publiek van de Real-Time CDP naar Adobe Campaign via de workflows voor het uitwisselen van bestanden voor cloudopslag en Adobe Campaign-opname </li><li>Eenvoudig leverings- en interactiegegevens delen uit gesprekken van klanten terug naar de Real-Time CDP vanuit Adobe Campaign om zowel het Real-Time Klantprofiel te verbeteren als rapportage over communicatiecampagnes via meerdere kanalen te verzorgen</li></ul> |
| [Journey Optimizer met Adobe Campaign](ajo-and-campaign.md) | Toont hoe u Adobe Journey Optimizer kunt gebruiken om 1:1 ervaringen te ordenen gebruikend het Real-Time Profiel van de Klant en hefboomwerking het inheemse systeem van het de transactionele overseinen van Adobe Campaign om het bericht te verzenden | Gebruik het Real-Time Klantprofiel en de macht van Journey Optimizer om in de huidige ervaringen te ordenen terwijl het gebruiken van de inheemse mogelijkheden van het Overseinen in real time van Adobe Campaign om de laatste mijl mededeling te doen<br><br>Overwegingen:<br><ul><li>Kan tot 1M berichten per uur via de Echte - tijd server van het Bericht verzenden<li>Er wordt geen vertraging uitgevoerd vanuit Journey Optimizer, zodat technische controles door een pre-Sales Enterprise Architect worden uitgevoerd</li><li>Beslissingsbeheer wordt niet ondersteund in pakketten naar campagne v8</li></ul> |

<br>

## Vereisten


### Toepassingsserver en Real-Time Messaging-server

* De Adobe Campaign Client Console is vereist voor interactie en gebruik van de Campaign v8-software. Het is een op vensters gebaseerde client en gebruikt standaard internetprotocollen (SOAP, HTTP, enz.). Zorg ervoor dat u de benodigde rechten hebt die op uw org zijn ingeschakeld voor het distribueren, installeren en uitvoeren van software

* Aanbieding toestaan voor IP-adres
   * Identificeer de IP waaiers die alle gebruikers tijdens toegang tot de cliëntconsole zullen hefboomwerking
   * Identiteit die de ondernemingssystemen zullen worden toegestaan om met de Real-Time overseinenserver te spreken en ervoor te zorgen zij statisch toegewezen IP of waaier hebben die u kunt lijsten van gewenste personen
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

### Grootte toepassingsserver

* Opslag kan worden geschaald tot maximaal 200 MB profielen met mogelijkheid om te schalen tot 1B-profielen
* Gebruikerstoegang instellen en beheren via Adobe Admin Console
* Het laden van gegevens naar campagne wordt verwacht via batchbestanden
   * Ondersteuning voor het laden van API-gegevens is voornamelijk bedoeld voor het beheer van profielen of eenvoudige objecten in de database (d.w.z. maken en bijwerken). Het is niet bedoeld voor het laden van grote hoeveelheden gegevens of batchbewerkingen.
   * Het gebruik van API&#39;s voor het lezen van gegevens voor aangepaste toepassingsdoeleinden wordt niet ondersteund
   * Gegevens die via de API zijn geladen, worden in de toepassingsdatabase gefaseerd en vervolgens elk uur naar de Cloud-database gerepliceerd
* Beperkingen op API-aanroepen zijn van toepassing. Meer informatie in het dialoogvenster [Adobe Campaign-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"}.

### Grootte van batchcommunicatieserver

* Kan worden geschaald voor verwerking tot berichten van 20 MB per uur

### Real-time communicatieservergrootte

* Kan tot 1 M berichten per uur verzenden
* Standaard worden twee realtime communicatieservers ingericht. Mogelijkheid om maximaal acht Real-Time Messaging-servers te schalen.

### SMS-configuratie

* De campagne verstrekt de capaciteit om met een leverancier van SMS te integreren. De leverancier wordt aangekocht door de klant en geïntegreerd met campagne voor het verzenden van SMS-berichten
* De steun is via het protocol SMPP
* Er zijn drie (3) verschillende soorten SMS die Adobe kan ondersteunen:
   * SMS MT (Mobile Terminated): een SMS dat door Adobe Campaign via de SMPP-provider naar mobiele telefoons wordt gezonden.
   * SMS MO (Mobile Originated): een SMS dat door een mobiel naar Adobe Campaign wordt verzonden via de SMPP-provider.
   * SMS SR (Status Report) of DR of DLR (Delivery Receipt): een door de mobiele telefoon via de SMPP-provider naar Adobe Campaign verzonden ontvangstbewijs dat het SMS met succes is ontvangen. Adobe Campaign kan ook SR ontvangen om aan te geven dat het bericht niet kan worden verzonden, vaak met een beschrijving van de fout.

## Implementatiestappen

Zie de gids Aan de slag voor [Adobe Campaign v8 implementeren](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=en)


## Gerelateerde documentatie

* [Campagne v8-documentatie](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [Campagne v8 Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [Documentatie over Experience Platform-tags](https://experienceleague.adobe.com/docs/launch.html)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html)
