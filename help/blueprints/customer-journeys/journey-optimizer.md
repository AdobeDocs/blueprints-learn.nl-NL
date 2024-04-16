---
title: "[!DNL Journey Optimizer] - geactiveerd berichtenverkeer en Adobe Experience Platform-blauwdruk"
description: Voer geactiveerde berichten en ervaringen uit via het Adobe Experience Platform als centrale hub voor het streamen van gegevens, klantprofielen en segmentatie.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: a1f3aef5b508575019bd651b9706efc7d6db5306
workflow-type: tm+mt
source-wordcount: '522'
ht-degree: 3%

---

# [!DNL Journey Optimizer] blauwdrukken

Adobe [!DNL Journey Optimizer] is een doelgebouwd systeem voor marketing teams om in real time aan klantengedrag te reageren en hen te ontmoeten waar zij zijn. Mogelijkheden voor gegevensbeheer zijn verplaatst naar de Adobe [!DNL Experience Platform] marketingteams in staat stellen zich te richten op wat ze het beste doen: dat is het maken van persoonlijke gesprekken en gesprekken van klanten van wereldklasse.

Deze blauwdruk beschrijft de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten die omhoog maken [!DNL Journey Optimizer].

## Gebruik hoofdletters

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
| [Berichten van derden](3rd-party-messaging.md) | Demonstreert hoe Adobe [!DNL Journey Optimizer] kan met de systemen van het derdeoverseinen worden gebruikt om gepersonaliseerde mededelingen te organiseren en te verzenden | Lever 1:1 op het moment gepersonaliseerde mededelingen aan klanten aangezien zij met uw merk of bedrijf in wisselwerking staan<br><br>Overwegingen:<br><ul><li>Systeem van derden moet toonder-tokens voor verificatie ondersteunen</li><li>Geen steun voor statische IPs toe te schrijven aan multi-huurdersarchitectuur</li><li>Houd rekening met architecturale beperkingen op systemen van derden voor API-aanroepen per seconde.  Mogelijk moet de klant extra volume van de externe leverancier kopen om het volume van [!DNL Journey Optimizer]</li><li>Biedt geen ondersteuning voor Beslissingsbeheer in berichten of ladingen</li></ul> |

<br>

## Integratiepatronen

| Integratie | Beschrijving | Mogelijkheden |
| :-- | :--- | :--- |
| [[!DNL Journey Optimizer] met Adobe Campaign](ajo-and-campaign.md) | Toont hoe u Adobe kunt gebruiken [!DNL Journey Optimizer] om 1:1 ervaringen te ordenen die het Real-Time Profiel van de Klant gebruiken en hefboomwerking het inheemse systeem van het Transactieoverseinen van Adobe Campaign om het bericht te verzenden | Gebruik het profiel en de kracht van de Real-Time Klant van [!DNL Journey Optimizer] om in de huidige ervaringen te ordenen terwijl het gebruiken van de inheemse mogelijkheden van het overseinen in real time van Adobe Campaign om de laatste mijl mededeling te doen<br><br>Overwegingen:<br><ul><li>Campagne-toepassing moet zijn ingeschakeld in versie 7 build >21.1 of v8</li><li>De productie van berichten</li><ul><li>Campagne v7 - tot 50 k per uur</li><li>Campagne v8 - maximaal 1 miljoen per uur</li><li>Campaign Standard - tot 50 k per uur</li></ul><li>Er wordt geen vertraging uitgevoerd, dus in geval van gebruik is een technische controle door een Enterprise Architect vereist</li><li>Geen steun voor het gebruiken van Beslissingsbeheer in bericht dat door Campagne wordt verzonden</li></ul> |

<br>

## Vereisten

Adobe [!DNL Experience Platform]:

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u kunt vormen [!DNL Journey Optimizer] gegevensbronnen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Proefdetails profiel&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met [!DNL Journey Optimizer]

E-mail:

* Moet subdomain klaar hebben om voor bericht het verzenden te worden gebruikt
* Subdomain kan volledig aan Adobe (geadviseerd) worden gedelegeerd of CNAMEs kan worden gebruikt om aan Adobe-specifieke DNS servers (douane) te richten
* Google TXT-record is nodig voor elk subdomein om goede prestaties te garanderen

Mobiel duwtje:

* De klant moet over een mobiele ontwikkelaar beschikken om de app te maken
* Adobe Experience Platform Mobile SDK

## Guardrails

[[!DNL Journey Optimizer] Product Link Guardrails](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html)

[Hulplijnen en advies voor end-to-end latentie](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html)

## Gerelateerde documentatie

* [[!DNL Experience Platform] documentatie](https://experienceleague.adobe.com/docs/experience-platform.html?lang=en)
* [[!DNL Experience Platform] Documentatie over tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en)
* [[!DNL Experience Platform Mobile SDK] documentatie](https://experienceleague.adobe.com/docs/mobile.html?lang=en)
* [[!DNL Journey Optimizer] documentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=en)
* [[!DNL Journey Optimizer] productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
