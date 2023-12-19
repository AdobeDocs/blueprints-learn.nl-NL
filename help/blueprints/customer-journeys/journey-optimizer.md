---
title: Journey Optimizer - geactiveerd berichtenverkeer en Adobe Experience Platform-blauwdruk
description: Voer getriggerde berichten en ervaringen uit via Adobe Experience Platform als centrale hub van het streamen van gegevens, klantprofielen en segmentatie.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 5f9384abe7f29ec764428af33c6dd1f0a43f5a89
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 3%

---

# Journey Optimizer-blauwdrukken

Adobe Journey Optimizer is een speciaal gebouwd systeem voor marketingteams om in real-time te reageren op gedragingen van klanten en hen te ontmoeten waar ze zich bevinden. De mogelijkheden voor gegevensbeheer zijn verplaatst naar de Adobe Experience Platform, zodat marketingteams zich kunnen richten op wat ze het beste doen: dat is het maken van klantentransacties en persoonlijke gesprekken van wereldklasse.  Deze blauwdruk beschrijft de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten die omhoog Adobe Journey Optimizer maken.

<br>

## Gebruik hoofdletters

* Gekoppelde berichten
* Bevestigingen van welkom en registratie
* Verlaten winkelwagentjes en aanvraagformulieren
* Locatie getriggerde berichten
* In-stadionervaringen
* Reis- en gastvrijheid vóór aankomst en verblijf

<br>

## Architectuur

<img src="assets/ajo-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Vervagingsscenario&#39;s

| Scenario | Beschrijving | Mogelijkheden |
| :-- | :--- | :--- |
| [Berichten van derden](3rd-party-messaging.md) | Toont aan hoe Adobe Journey Optimizer met de systemen van het derdeoverseinen kan worden gebruikt om gepersonaliseerde mededelingen te organiseren en te verzenden | Lever 1:1 op het moment gepersonaliseerde mededelingen aan klanten aangezien zij met uw merk of bedrijf in wisselwerking staan<br><br>Overwegingen:<br><ul><li>Systeem van derden moet toonder-tokens voor verificatie ondersteunen</li><li>Geen steun voor statische IPs toe te schrijven aan multi-huurdersarchitectuur</li><li>Houd rekening met architecturale beperkingen op systemen van derden voor API-aanroepen per seconde.  Mogelijk moet de klant extra volume van de externe leverancier kopen om het volume van Journey Optimizer te ondersteunen</li><li>Biedt geen ondersteuning voor Beslissingsbeheer in berichten of ladingen</li></ul> |

<br>

## Integratiepatronen

| Integratie | Beschrijving | Mogelijkheden |
| :-- | :--- | :--- |
| [Journey Optimizer met Adobe Campaign](ajo-and-campaign.md) | Toont hoe u Adobe Journey Optimizer kunt gebruiken om 1:1 ervaringen te ordenen gebruikend het Real-Time Profiel van de Klant en hefboomwerking het inheemse systeem van het de transactionele overseinen van Adobe Campaign om het bericht te verzenden | Gebruik het Real-Time Klantprofiel en de macht van Journey Optimizer om in de huidige ervaringen te ordenen terwijl het gebruiken van de inheemse mogelijkheden van het Overseinen in real time van Adobe Campaign om de laatste mijl mededeling te doen<br><br>Overwegingen:<br><ul><li>Campagne-toepassing moet zijn ingeschakeld in versie 7 build >21.1 of v8</li><li>De productie van berichten</li><ul><li>Campagne v7 - tot 50 k per uur</li><li>Campagne v8 - maximaal 1 miljoen per uur</li><li>Campaign Standard - tot 50 k per uur</li></ul><li>Er wordt geen vertraging uitgevoerd, dus in geval van gebruik is een technische controle door een Enterprise Architect vereist</li><li>Geen steun voor het gebruiken van Beslissingsbeheer in bericht dat door Campagne wordt verzonden</li></ul> |

<br>

## Vereisten

Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u Journey Optimizer gegevensbronnen kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer

E-mail

* Moet subdomain klaar hebben om voor bericht het verzenden te worden gebruikt
* Subdomain kan volledig aan Adobe (geadviseerd) worden gedelegeerd of CNAMEs kan worden gebruikt om aan Adobe-specifieke DNS servers (douane) te richten
* Google TXT-record is nodig voor elk subdomein om goede prestaties te garanderen

Mobiele push

* De klant moet over een mobiele ontwikkelaar beschikken om de app te maken
* Adobe Experience Platform Mobile SDK

<br>

## Guardrails

[Journey Optimizer Guardrails Product Link](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html)

[Hulplijnen en advies voor end-to-end latentie](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Gerelateerde documentatie

* [Documentatie Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [Documentatie over Experience Platform-tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [Experience Platform Mobile SDK-documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
* [Journey Optimizer-documentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [Journey Optimizer-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
