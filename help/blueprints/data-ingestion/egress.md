---
title: Blauwdruk voor gegevenstoegang en exporteren
description: Deze blauwdruk biedt een overzicht van alle methoden waarmee gegevens kunnen worden benaderd en geëxporteerd vanuit Adobe Experience Platform en toepassingen.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-Time Customer Data Platform, Tags
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
source-git-commit: 8355a36a235d847a6faf2398f3fadbed28ccac37
workflow-type: tm+mt
source-wordcount: '1513'
ht-degree: 0%

---

# Blauwdruk voor gegevenstoegang en exporteren

In de blauwdruk voor gegevenstoegang en export worden alle mogelijke methoden beschreven waarmee gegevens kunnen worden benaderd of geëxporteerd vanuit Adobe Experience Platform en toepassingen.

De blauwdruk wordt opgedeeld in twee categorieën voor gegevenstoegang vanuit Experience Platform en toepassingen. Ten eerste, benaderingen voor het verzamelen van gegevens uit Experience Platform en toepassingen; dit zou worden beschouwd als een methode van het push - type van gegevensuitgang . Ten tweede, benaderingen voor toegangsgegevens van Experience Platform en toepassingen; dit zou worden beschouwd als een methode van het pull - type van gegevenstoegang .

Aanpak voor gegevenstoegang:

* [Toegang-API voor gebruikersprofiel in realtime](#rtcp-profile-access-api)
* [API voor gegevenstoegang](#data-access-api)
* [Query-service](#query-service)

Methoden voor het exporteren van gegevens:

* [Client Side Tags](#client-side-tags-extensions)
* [Gebeurtenis doorsturen](#event-forwarding)
* [Real-time Customer Data Platform-doelen](#RTCDP-destinations)
* [Aangepaste Journey Optimizer-handelingen](#jo-custom-actions)

## Overzichtsarchitectuur voor gegevenstoegang en export

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Referentiearchitectuur voor de blauwdruk voor gegevensvoorbereiding en insluiting" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" />

## Benadering voor gegevenstoegang

### Toegang-API voor gebruikersprofiel in realtime {#rtcp-profile-access-api}

Klanten kunnen toegang krijgen tot één enkel verenigd profiel vanuit de Real-time opslag van het Profiel van de Klant, met inbegrip van alle profielidentiteiten, publiekslidmaatschappen, attributen en ervaringsgebeurtenissen die de Toegang API van het Profiel van de Klant in real time gebruiken.

Zie de [Toegang-API voor gebruikersprofiel in realtime](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en) documentatie voor aanvullende informatie.

#### Gebruik hoofdletters

* Zoek één enkel profiel om context aan de interactie van de agentenklant zoals steuninteractie door praatje en vraagcentrum, of een verkoopinteractie op het verkooppunt toe te voegen.
* Toegevoegde context toestaan aan een verpersoonlijkingsbesluit dat door een extern systeem, bijvoorbeeld een systeem van de Webverpersoonlijking of een systeem van de aanbiedingsbeslissing wordt gemaakt.

#### Overwegingen

* Klantprofiel in realtime [guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) van toepassing.
* Ontworpen voor één profielzoekopdracht tegelijk. Niet gebruikt voor bulkprofieltoegang of download van de volledige profielpopulatie voor het gebruik van analyse of gegevenswetenschap.
* De responstijd van de opzoekopdracht van het profiel wordt gekoppeld aan de profielinstructies. Eisen voor realtime lage latentie: voor dezelfde vereisten voor paginagrootte moet u het Edge-profiel gebruiken van de naar [Adobe Target-verbinding](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) of de [Aangepaste aanpassingsverbinding](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en) voor realtime profieltoegang voor in browser en in app-personalisatie.

### API voor gegevenstoegang {#data-access-api}

De gebruikers van de API voor gegevenstoegang kunnen rechtstreeks toegang krijgen tot de onbewerkte gegevenssetbestanden die in het gegevenspeer van het Experience Platform zijn opgeslagen.

* Voor meer informatie over het gebruik van de API voor gegevenstoegang raadpleegt u de [documentatie](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=en).

#### Gebruik hoofdletters

* Trek ruwe en verwerkte gegevensdossiers van Experience Platform voor opslag en evaluatie in ondernemingsmilieu&#39;s.

#### Overwegingen

* Aangezien de gegevens op een batch asynchrone manier worden betreden, zal de toegang tot de gegevens inherent latent in vergelijking met het stromen van de benaderingen van de gegevensuitgang zoals het gebruiken van Markeringen, Gebeurtenis door:sturen, of RTCDP Doelen zijn.
* Gegevensbestanden die naar Experience Platform worden verwerkt, worden als verzamelingen van bestanden in batches opgeslagen en worden gecomprimeerd en opgeslagen in parketindeling. Als dusdanig wanneer het toegang tot van en het downloaden van de dossiers aan een verschillend milieu moeten zij systematisch door hun partij en dossier worden betreden zoals tegengesteld aan een volledige dataset en om het even welke verrichtingen op de gegevens moeten rekenschap geven voor de dossiers die in parquetformaat worden gecomprimeerd.

### Query-service {#query-service}

Gebruikend de klanten van de Dienst van de Vraag van het ervaringsplatform kunnen datasets binnen Experience Platform vragen en de resultaten van de vraag voortzetten. Een SQL Cliënt kan worden gebruikt om de vraagreactie in de gewenste opslagbestemming te vragen en voort te zetten die de SQL cliënt kan steunen. De dienst UI van de Vraag kan worden gebruikt om het SQL resultaat in een doeldataset in het Experience Platform op te slaan of de resultaten kunnen aan de lokale machine worden bewaard.

* Voor extra details over verbinding met SQL cliënten om SQL resultaten van de Dienst van de Vraag van het Experience Platform voort te zetten zie het volgende [documentatie](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=en).

#### Gebruik hoofdletters

* Vraag ruwe gegevens van de Experience Platform datasets en stelt de vraagresultaten voort.
* Vraag de dataset van de profielmomentopname om inzichten op het Profiel van de Klant in real time te halen. [Documentatie](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=en#profile-attribute-datasets).
* De vraagresultaten van de opslag in een afzonderlijke dataset voor toegang of in een profiel toegelaten dataset die later door RTCDP en andere toepassingen van Experience Cloud kunnen worden geïntegreerd die tot het Profiel van de Klant in real time toegang hebben.

#### Overwegingen

* Aangezien de gegevens op een batch asynchrone manier worden gevraagd, zal de toegang tot de gegevens inherent latent zijn in vergelijking met het stromen van de benaderingen van de gegevensuitgang zoals het gebruiken van Markeringen, Gebeurtenis door:sturen, of RTCDP Doelen.
* Slechts kunnen de gegevens die in het de gegevensmeer van de Experience Platform beschikbaar zijn worden gevraagd gebruikend de Dienst van de Vraag. De opslag van het Profiel van de Klant in real time, de identiteitsgrafiek, Customer Journey Analytics kan niet direct worden gevraagd gebruikend de Dienst van de Vraag. Slechts wanneer de datasets aan het gegevenshoek worden uitgevoerd kan deze datasets worden gevraagd, zoals in het voorbeeld van de dataset van de profielmomentopname.
* Merk op dat de gidsen voor het aantal vraagresultaten en vraagonderbreking zoals die in worden geschetst van toepassing zijn [Query Services-handleidingen](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en) documentatie.

## Methoden voor het exporteren van gegevens

### Tagextensies aan de clientzijde {#client-side-tags-extensions}

Extensies kunnen worden geïmplementeerd met de oplossing Adobe. Zodra een uitbreiding wordt opgesteld worden de gegevensverzoeken opgesteld direct op cliëntbrowser of toepassing en een verzoek kan worden aangehaald om gegevens en verzoeken naar de gewenste bestemming te verzenden.

Zie de [Overzicht van tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) documentatie voor aanvullende informatie.

#### Gebruik hoofdletters

* Verzamel onbewerkte streaminggegevens rechtstreeks vanuit clientomgevingen met behulp van tags.

#### Overwegingen

* Geen directe toegang tot informatie aan de serverzijde, zoals het Experience Platform in real time het Profiel van de Klant en publieksleden.
* Als u extra labels voor gegevensverzameling aan de pagina toevoegt, kunnen de laadtijden van de pagina toenemen.
* De mogelijkheid om regels in te stellen om alleen gegevens te vragen wanneer aan bepaalde criteria wordt voldaan.
* Gegevens worden rechtstreeks van de client verzameld, waardoor de typen transformaties en verrijking worden beperkt die kunnen worden uitgevoerd voordat de gegevens worden verzameld.

### Gebeurtenis doorsturen {#event-forwarding}

De verzoeken van de inzameling van gegevens worden verzameld direct aan het Netwerk van de Rand. Van de verzoeken van het Netwerk van de Rand aan externe RESTful eindpunten kunnen worden gevormd om deze verzoeken op de externe bestemming door:sturen.

Raadpleeg het volgende: [Gebeurtenis doorsturen](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en) documentatie voor aanvullende informatie.

#### Gebruik hoofdletters

* Verzamel ruw direct van cliënt zijmilieu&#39;s aan een ondernemingseindpunt gebruikend Adobe server zijgebeurtenis door:sturen.

#### Overwegingen

* Om Gebeurtenis door:sturen te gebruiken, moeten de gegevens naar het Netwerk van de Rand worden verzonden gebruikend het Web SDK of MobileSDK.
* De methode voor het doorsturen van gebeurtenissen verkort de laadtijd en het gewicht van de pagina omdat er extra codes op de pagina worden toegevoegd.
* Er wordt momenteel geen verrijking van het randprofiel of andere gegevensbronnen ondersteund.
* Beperkte gegevensfiltering en eenvoudige toewijzingstransformaties worden ondersteund.

### Real-time Customer Data Platform-bestemmingen {#RTCDP-destinations}

De gegevens van de profielattributen en van het publiekslidmaatschap kunnen aan onderneming en reclamebestemmingen worden geactiveerd. Dit betekent dat de gegevens moeten worden opgenomen in het Experience Platform Real-time Klantprofiel.

Zie de [Real-time Customer Data Platform-doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en) documentatie voor aanvullende informatie.

#### Gebruik hoofdletters

* Activeer profielkenmerkinformatie, waaronder het lidmaatschap van het publiek voor een interne bedrijfsgegevensopslagruimte, analyseprogramma&#39;s, e-mailsystemen of supportsystemen.
* Activeer het lidmaatschap van het profielpubliek voor een externe advertentiemap om inhoud aan het profiel te richten en te personaliseren.

#### Overwegingen

* Profielkenmerken en publiek lidmaatschap kunnen worden geactiveerd. Gebeurtenissen met een ruwe ervaring kunnen momenteel niet worden geactiveerd als onderdeel van RTCDP-doelen.
* Activaties worden uitgevoerd in streaming of batch, afhankelijk van de aard van de segmentevaluatie en de aard van het inslieprotocollen die de bestemming accepteert.

### Aangepaste Journey Optimizer-acties {#jo-custom-actions}

Het gebruiken van de klanten van Journey Optimizer kan een douaneactie van het reiscanvas aanhalen om een lading of een bericht naar een extern API eindpunt te verzenden dat wordt gevormd. Een actie kan aan om het even welke dienst van om het even welke leverancier worden gevormd die door REST API met een JSON-Geformatteerde lading kan worden geroepen. Deze nuttige lading kan gebeurtenisinformatie, profielattributen en vroegere gebeurtenisgegevens, transformaties en verrijkingen omvatten die in de reis worden gevormd.

Zie de [Aangepaste Journey Optimizer-acties](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en) documentatie voor aanvullende informatie.

#### Gebruik hoofdletters

* Activeringsgebeurtenissen van Experience Platform en Journey Optimizer die aanvullende informatie van het Real-time Klantprofiel bevatten.
* Externe systemen op de hoogte stellen wanneer een klant een specifiek punt van een reis heeft bereikt.

#### Overwegingen

* Guardrails op de doorvoer ondersteund door [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=en) en door de [Klantprofiel in realtime](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) van toepassing.
* Aangepaste acties kunnen voor elke gebeurtenis of elk profiel op een reis één voor één worden gestreamd. Bulkbewerkingen of bulkgegevensegress in de vorm van bestanden of geaggregeerde verzoeken over klantreizen kunnen niet worden uitgevoerd.
* Streaming toegang tot kenmerken van het realtime-klantprofiel en ervaringsgebeurtenissen die kunnen worden opgenomen in de activeringslading.
* Gebeurtenisgegevens kunnen worden gefilterd en eenvoudige toewijzingstransformaties kunnen worden toegepast voordat gebeurtenissen naar externe doelen worden verzonden.
