---
title: '[!DNL Journey Optimizer] - Gekoppelde berichten en Adobe Experience Platform-blauwdruk'
description: Voer geactiveerde berichten en ervaringen uit via het Adobe Experience Platform als centrale hub voor het streamen van gegevens, klantprofielen en segmentatie.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '521'
ht-degree: 4%

---

# [!DNL Journey Optimizer] blauwdrukken

Adobe [!DNL Journey Optimizer] is een speciaal gebouwd systeem voor marketingteams dat in real-time kan reageren op gedragingen van klanten en hen ontmoet waar ze zich bevinden. De mogelijkheden voor gegevensbeheer zijn verplaatst naar de Adobe [!DNL Experience Platform] , zodat marketingteams zich kunnen richten op wat ze het beste doen: dat is het maken van klantentransacties en persoonlijke gesprekken van wereldklasse.

Deze blauwdruk beschrijft de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten die omhoog maken [!DNL Journey Optimizer].

## Gebruiksscenario&#39;s

* Gekoppelde berichten
* Bevestigingen van welkom en registratie
* Verlaten winkelwagentjes en aanvraagformulieren
* Locatie getriggerde berichten
* In-stadionervaringen
* Reis- en gastvrijheid vóór aankomst en verblijf

## Architectuur

<img src="assets/ajo-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Vervagingsscenario&#39;s

| Scenario | Beschrijving | Mogelijkheden |
| :-- | :--- | :--- |
| [ het Overseinen van de derde partij ](3rd-party-messaging.md) | Toont aan hoe Adobe [!DNL Journey Optimizer] met derdeoverseinensystemen kan worden gebruikt om gepersonaliseerde mededelingen te ordenen en te verzenden | Lever 1 :1 in het moment gepersonaliseerde mededelingen aan klanten aangezien zij met uw merk of bedrijf <br><br> Overwegingen in wisselwerking staan:<br><ul><li>Systeem van derden moet toonder-tokens voor verificatie ondersteunen</li><li>Geen steun voor statische IPs toe te schrijven aan multi-huurdersarchitectuur</li><li>Houd rekening met architecturale beperkingen op systemen van derden voor API-aanroepen per seconde.  Mogelijk moet de klant extra volume van de externe leverancier kopen om het volume van [!DNL Journey Optimizer] te ondersteunen.</li><li>Biedt geen ondersteuning voor Beslissingsbeheer in berichten of ladingen</li></ul> |

<br>

## Integratiepatronen

| Integratie | Beschrijving | Mogelijkheden |
| :-- | :--- | :--- |
| [[!DNL Journey Optimizer]  met Adobe Campaign ](ajo-and-campaign.md) | Toont hoe u Adobe [!DNL Journey Optimizer] kunt gebruiken om 1 :1 ervaringen te ordenen die het Real-Time Profiel van de Klant gebruiken en hefboomwerking het inheemse systeem van het de transactieoverseinen van Adobe Campaign om het bericht te verzenden | Hefboomwerking het Real-Time Profiel van de Klant en de macht van [!DNL Journey Optimizer] aan orchestratie in de huidige ervaringen terwijl het gebruiken van de inheemse overseinenmogelijkheden in real time van Adobe Campaign om de laatste mijlcommunicatie <br><br> Overwegingen te doen:<br><ul><li>Campagne-toepassing moet zijn ingeschakeld in versie 7 build >21.1 of v8</li><li>De productie van berichten</li><ul><li>Campagne v7 - tot 50 k per uur</li><li>Campagne v8 - maximaal 1 miljoen per uur</li><li>Campaign Standard - maximaal 50 k per uur</li></ul><li>Er wordt geen vertraging uitgevoerd, dus in geval van gebruik is een technische controle door een Enterprise Architect vereist</li><li>Geen steun voor het gebruiken van Beslissingsbeheer in bericht dat door Campagne wordt verzonden</li></ul> |

<br>

## Vereisten

Adobe [!DNL Experience Platform] :

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u [!DNL Journey Optimizer] gegevensbronnen kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profieltestdetails&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met [!DNL Journey Optimizer]

E-mail:

* Moet subdomain klaar hebben om voor bericht het verzenden te worden gebruikt
* Subdomein kan volledig worden gedelegeerd aan Adobe (aanbevolen) of CNAMEs kan worden gebruikt om aan Adobe-specifieke DNS servers (douane) te richten
* Google TXT-record is nodig voor elk subdomein om goede prestaties te garanderen

Mobiel duwtje:

* De klant moet over een mobiele ontwikkelaar beschikken om de app te maken
* Adobe Experience Platform Mobile SDK

## Beveiligingsmechanismen

[[!DNL Journey Optimizer]  Guardrails Product Link ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

[ Guardrails en de Begeleiding van de Latentie van Eind tot Eind ](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/guardrails.html)

## Gerelateerde documentatie

* [[!DNL Experience Platform]  documentatie ](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [[!DNL Experience Platform]  documentatie van Markeringen ](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [[!DNL Experience Platform Mobile SDK]  documentatie ](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
* [[!DNL Journey Optimizer]  documentatie ](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [[!DNL Journey Optimizer]  productbeschrijving ](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
