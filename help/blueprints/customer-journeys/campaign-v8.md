---
title: Campagne v8 blauwdruk, campagne en platform
description: Meer informatie over de blauwdruk voor Campaign v8.
solution: Campaign,Campaign v8
version: Campaign v8
exl-id: 89b3a761-9cb3-4e01-8da0-043e634fa61f
source-git-commit: 1d10727899aaae6b8cd339ce10d2a520c73bdaa2
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 0%

---

# Campagne v8 blauwdruk

Adobe Campaign v8 is het volgende-gen campagnehulpmiddel dat voor traditionele marketing kanalen zoals e-mail en direct mail wordt gebouwd. Het biedt robuuste ETL- en gegevensbeheermogelijkheden om de perfecte campagne te helpen kweken en beheren. De orkestmotor van het netwerk voorziet in rijke multi-touchmarketingprogramma&#39;s met een centrale focus op batchgeoriënteerde reizen.

Het komt ook met een scalable Real-Time overseinenserver worden verbonden die marketing teams toelaat om vooraf bepaalde berichten te verzenden die op een alle-inclusieve lading van om het even welk systeem van IT voor dingen zoals het terugstellen van het wachtwoord, orderbevestiging, e-ontvangstbewijzen en veel meer worden gebaseerd.

## Gebruiksscenario&#39;s

* Zeer complexe batchgebaseerde berichtenprogramma&#39;s.
* Onboarding- en hermarketingcampagnes.
* Reclamecampagnes voor e-mail, brochures en tijdschriften
* Eenvoudig transactiebericht (zoals het opnieuw instellen van het wachtwoord, e-mailontvangstbewijzen, orderbevestigingen, enzovoort).
* Integratie van Campagnegegevens in Adobe Experience Platform voor analyse en profielopbouw.
* Het delen van het publiek van het Platform van Gegevens van de Klant in real time aan Campaign.

## Architectuurdiagrammen

Leer meer over [ de plaatsingsmodellen van de Campagne v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/config/architecture/architecture.html#ac-deployment){target="_blank"} .

### Implementatie van Campagne Enterprise (FFDA)

<img src="assets/P4-architecture.png" alt="Referentiearchitectuur voor blauwdruk van campagne v8 (P4)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

### Implementatie van FDA voor campagne v8

<img src="assets/P1-P3-architecture.png" alt="Referentiearchitectuur voor campagne v8 Blueprint (P1-P3)" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Integratiepatronen

| Scenario | Beschrijving | Mogelijkheden |
| :-- | :--- | :--- |
| [[!DNL Real-time Customer Data Platform]  met Adobe  [!DNL Campaign]](rtcdp-and-campaign-v8.md) | Toont hoe de Adobe Experience Platform en zijn Real-Time Klantprofiel en gecentraliseerd segmenteringshulpmiddel met Adobe [!DNL Campaign] kunnen worden gebruikt om gepersonaliseerde gesprekken te leveren | <ul><li>Delen van profielen en soorten publiek van [!DNL Real-Time CDP] naar Adobe [!DNL Campaign] via de workflows voor het uitwisselen van bestanden voor cloudopslag en Adobe [!DNL Campaign] . </li><li>U kunt eenvoudig levering- en interactiegegevens delen van gesprekken van klanten die teruggaan naar de [!DNL Real-Time CDP] vanuit Adobe [!DNL Campaign] om zowel het Real-Time Klantprofiel te verbeteren als om via het kanaal rapporten te verstrekken over berichtcampagnes</li></ul> |
| [[!DNL Journey Optimizer]  met Adobe  [!DNL Campaign]](ajo-and-campaign.md) | Toont hoe u Adobe Journey Optimizer kunt gebruiken om 1:1 ervaringen te ordenen die het Real-Time Profiel van de Klant gebruiken en hefboomwerking het inheemse systeem van het de transactionele overseinen van Adobe [!DNL Campaign] om het bericht te verzenden | Hefboomwerking het Profiel en de macht van de Klant in real time van [!DNL Journey Optimizer] aan orchestratie in de huidige ervaringen terwijl het gebruiken van de inheemse overseinenmogelijkheden in real time van Adobe [!DNL Campaign] om de laatste mijlcommunicatie <br><br> Overwegingen te doen:<br><ul><li>Kan tot 1M berichten per uur via de Echte - tijd server van het Bericht verzenden<li>Er wordt geen vertraging uitgevoerd vanuit [!DNL Journey Optimizer], zodat technische controles door een pre-Sales Enterprise Architect worden uitgevoerd</li><li>Beslissingsbeheer wordt niet ondersteund in pakketten naar campagne v8</li></ul> |

## Vereisten

De volgende voorwaarden bestaan voor deze blauwdruk.

### Toepassingsserver en Real-Time Messaging-server

* De Adobe [!DNL Campaign] Client Console is vereist voor interactie en gebruik van de [!DNL Campaign] v8-software. Het is een op vensters gebaseerde client en gebruikt standaard internetprotocollen (SOAP, HTTP, enz.). Zorg ervoor dat u de benodigde rechten hebt die op uw org zijn ingeschakeld voor het distribueren, installeren en uitvoeren van software

* Aanbieding met IP-adres toestaan:
   * Identificeer de IP waaiers die alle gebruikers hefboomwerking tijdens toegang tot de cliëntconsole.
   * Identiteit die de ondernemingssystemen worden toegestaan om met de Real-Time overseinenserver te spreken en ervoor te zorgen zij statisch toegewezen IP of waaier hebben die u kunt toestaan-lijst.
   * Dit kan worden ingesteld en gecontroleerd via het Configuratiescherm van de Campagne.
* sFTP-sleutelbeheer:
   * SSH openbare sleutels beschikbaar hebben om met de Campagne te gebruiken verstrekt sFTP. Dit kan worden ingesteld en gecontroleerd via het Configuratiescherm van de Campagne.

### E-mail

* Heb klaar subdomain om voor bericht het verzenden te worden gebruikt.
* Subdomein kan volledig aan Adobe (geadviseerd) worden gedelegeerd of CNAMEs kan worden gebruikt om aan Adobe-specifieke DNS servers (douane) te richten.
* Google TXT-record is nodig voor elk subdomein om goede prestaties te garanderen.

### Mobiele push

* Een mobiele ontwikkelaar beschikbaar hebben om de mobiele app te implementeren, te configureren en samen te stellen.
* Adobe verstrekt slechts een SDK om de noodzakelijke informatie van FCM (Android) en APNS (iOS) te verzamelen om berichtlading naar hun servers te verzenden. Hoe de mobiele app moet worden gecodeerd, geïmplementeerd, beheerd en opgespoord, valt onder de verantwoordelijkheid van de klant.

### Webapps (optioneel)

* Kan een extra subdomein voor Campagne delegeren ontvangen unsubscribe en landende pagina&#39;s.
* SSL-certificaat wordt sterk aangemoedigd.

## Beveiligingsmechanismen

De instructies worden hieronder beschreven.

### Grootte toepassingsserver

* Opslag kan worden geschaald tot maximaal 200 M profielen met mogelijkheid om tot 1B profielen te schrapen.
* Toegang tot gebruikers instellen en beheren via Adobe [!DNL Admin Console] .
* Gegevens die naar [!DNL Campaign] worden geladen, worden naar verwachting via batchbestanden geladen:
   * Ondersteuning voor het laden van API-gegevens is voornamelijk bedoeld voor het beheer van profielen of eenvoudige objecten in de database (d.w.z. maken en bijwerken). Het is niet bedoeld voor het laden van grote hoeveelheden gegevens of batchbewerkingen.
   * Het gebruik van API&#39;s voor het lezen van gegevens voor aangepaste toepassingsdoeleinden wordt niet ondersteund
   * Gegevens die via de API zijn geladen, worden in de toepassingsdatabase gefaseerd en vervolgens elk uur naar de Cloud-database gerepliceerd
* Beperkingen op API-aanroepen zijn van toepassing. Leer meer in de [ Beschrijving van het Product van Adobe Campaign ](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html){target="_blank"} .

### Grootte van batchcommunicatieserver

* Kan worden geschaald voor verwerking tot berichten van 20 MB per uur

### Real-time communicatieservergrootte

* Kan tot 1 M berichten per uur verzenden
* Standaard worden twee realtime communicatieservers ingericht. Mogelijkheid om maximaal acht Real-Time Messaging-servers te schalen.

### SMS-configuratie

* De campagne verstrekt de capaciteit om met een leverancier van SMS te integreren. De leverancier wordt aangekocht door de klant en geïntegreerd met campagne voor het verzenden van SMS-berichten.
* De steun is via het protocol SMPP.
* Er zijn drie (3) verschillende soorten SMS die Adobe kan ondersteunen:
   * SMS MT (Mobile Terminated): een SMS dat door Adobe [!DNL Campaign] naar mobiele telefoons wordt gezonden via de SMPP-provider.
   * SMS MO (Mobile Originated): een SMS-bericht dat door een mobiel naar Adobe wordt verzonden [!DNL Campaign] via de SMPP-provider.
   * SMS SR (Status Report) of DR of DLR (Delivery Receipt): een door de mobiele telefoon via de SMPP-provider naar Adobe verzonden ontvangstbewijs dat het SMS met succes is ontvangen. [!DNL Campaign] Adobe [!DNL Campaign] kan ook SR ontvangen die aangeeft dat het bericht niet kan worden verzonden, vaak met een beschrijving van de fout.

## Implementatiestappen

Zie de begonnen gids voor [ Uitvoeren Adobe Campaign v8 ](https://experienceleague.adobe.com/docs/campaign/campaign-v8/implement/implement.html?lang=en)

## Gerelateerde documentatie

* [ Campagne v8 documentatie ](https://experienceleague.adobe.com/docs/campaign-v8.html)
* [ Campagne v8 Beschrijving van het Product ](https://helpx.adobe.com/legal/product-descriptions/adobe-campaign-managed-cloud-services.html)
* [ de documentatie van de Markeringen van Experience Platform ](https://experienceleague.adobe.com/docs/launch.html)
* [ Experience Platform Mobile SDK documentatie ](https://experienceleague.adobe.com/docs/mobile.html)
