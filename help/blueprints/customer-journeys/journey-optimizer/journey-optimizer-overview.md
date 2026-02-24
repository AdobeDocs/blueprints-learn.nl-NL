---
title: '[!DNL Journey Optimizer] - Transparantie vervagen'
description: Voer geactiveerde berichten en ervaringen uit via het Adobe Experience Platform als centrale hub voor het streamen van gegevens, klantprofielen en segmentatie.
solution: Journey Optimizer
exl-id: 97831309-f235-4418-bd52-28af815e1878
source-git-commit: 49251caac58cd8f62dff977f94ea6a716aa94250
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 4%

---

# [!DNL Journey Optimizer] blauwdrukken

Adobe [!DNL Journey Optimizer] is een &#39;cloud-native&#39; toepassing die is gebaseerd op Adobe Experience Platform en die realtime en geplande organisatie van klantritten langs meerdere kanalen mogelijk maakt. Deze functie ondersteunt gebeurtenisgestuurde triggers, publiekssegmentatie en beslissingsservices om persoonlijke ervaringen te bieden via e-mail, SMS, push, web en berichten in de app. Het integreert met binnenkomende en uitgaande systemen, die voor verenigd beheer van de publieksstaat en contextafhankelijke overeenkomst over de klantenlevenscyclus toestaan.

Deze blauwdruk beschrijft de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten die omhoog maken [!DNL Journey Optimizer].

<br>

## Gebruiksscenario&#39;s

>[!BEGINTABS]
>[!TAB  Reis (gebeurtenis-gedreven, Echt - tijd) ]

- **Terugwinning van de ontbinding:** Trigger gepersonaliseerde berichten wanneer een gebruiker een kar, een vorm, of zitting-via e-mail, duw, of in-app verlaat.
- **Nieuwe Teken-up van de Gebruiker:** verbind nieuwe gebruikers onmiddellijk nadat zij met nieuwe rekeningsvoorkeur, relevante bevorderingen of voordelen registreren
- **Transactioneel Overseinen:** verzend bevestiging in real time, alarm, of updates (b.v., verscheepte orde, wachtwoordterugstellen) gebruikend gebeurtenistrekkers.
- **Contextale het richten:** communiceer met gebruikers in het ogenblik dat op hun signalen en plaats wordt gebaseerd om hun ervaring te helpen begeleiden en te leiden
- **Contextafhankelijke Upsell/Cross-Sell:** lever gepersonaliseerde aanbiedingen die op profielattributen in real time en recente interactie worden gebaseerd.

>[!TAB  Bezwaren van de Campagne (Gepland, merk-in werking gesteld) ]

- **Bevorderende Campagnes**: Start multi-step, multi-channel campagnes voor productlanceringen, seizoensaanbiedingen, of verkoopgebeurtenissen.
- **Levenscyclusmarketing**: Automatiseer terugkomende campagnes zoals verjaardagsberichten, vernieuwingsherinneringen, of loyaliteitsmijlpalen.
- **publiek-Gebaseerde Pushes van Funnel**: Segment en duw publiek in gestructureerde campagnes die op bedrijfslogica of attributen van CRM worden gebaseerd.
- **Nieuwsbrief &amp; de Distributie van de Inhoud**: Plan en lever gepersonaliseerde inhoud aan gericht publiek over e-mail en mobiel.
- **herverbindingsCampagnes**: Identificeer slapende gebruikers en herintroduceer hen in betrokkenheidsstromen die op inactiviteitsdrempels worden gebaseerd.

>[!ENDTABS]

<br>

## Architectuur

<img src="images/ajo-architecture.svg" alt="Referentiearchitectuur Adobe Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

<br>

## Blauwdrukscenario&#39;s

| Scenario | Beschrijving |
| :-- | :-- |
| [&#x200B; Reizen &#x200B;](journey-optimizer-journeys.md) | De Reizen van AJO in Adobe Journey Optimizer worden geautomatiseerd, gepersonaliseerde klantenervaringen teweeggebracht door gebeurtenissen in real time of publiekssegmenten, toestaand marketers om relevante berichten over kanalen zoals e-mail, SMS, en dupberichten te leveren. |
| [&#x200B; Campagne Orchestration &#x200B;](journey-optimizer-campaigns.md) | Met AJO Campaign Orchestration kunnen marketers persoonlijke, cross-channel campagnes ontwerpen en uitvoeren met behulp van realtime gegevens en kijkcijfers. Het steunt dynamische het richten, berichtlevering, en reislogica om klantenbetrokkenheid over e-mail, SMS, duw, en douanekanalen te optimaliseren. |

<br>

## Integratiepatronen

| Integratie | Beschrijving | Technische overwegingen |
| :-- | :-- | :-- |
| [&#x200B; het Overseinen van de derde partij &#x200B;](3rd-party-messaging.md) | Toont aan hoe Adobe [!DNL Journey Optimizer] met derdeoverseinenplatforms kan integreren om gepersonaliseerde klantenmededelingen te ordenen en te leveren. | <ul><li>Het derdesysteem moet **dragertokenauthentificatie** steunen</li><li>**Statische IPs wordt niet gesteund** toe te schrijven aan de multi-huurdersarchitectuur.</li><li>Ben zich bewust van **API tariefgrenzen** op derdesystemen; de klanten kunnen extra capaciteit moeten kopen om verkeer uit **Adobe Journey Optimizer** te behandelen.</li><li>**het Beheer van het Besluit** wordt niet gesteund binnen berichtlading of leveringslogica.</li></ul> |
| [[!DNL Journey Optimizer]  met Adobe Campaign v8 &#x200B;](../campaign-v8/ajo-and-campaign-v8.md) | Toont aan hoe Adobe [!DNL Journey Optimizer] met de mogelijkheden van Adobe Campaign v8 voor transactiemeldingen kan integreren om de uiteindelijke berichtlevering uit te voeren. | <ul><li>Er is geen vertraging van berichten. Uiteinde van 4.000 berichten per 5 minuten.</li><li>Alleen ondersteuning voor een reis op initiatief van een gebeurtenis</li><li>Beslissingsbeheer wordt niet ondersteund in berichten die door de campagne worden verzonden</li></ul> |

<br>

## Vereisten

Adobe [!DNL Experience Platform] :

- De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u [!DNL Journey Optimizer] gegevensbronnen kunt vormen
- Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring XDM, voeg &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
- Voor schema&#39;s die zijn gebaseerd op de klasse XDM Individual Profile voegt u de veldgroep &#39;Proefdetails profiel&#39; toe om testprofielen te kunnen laden voor gebruik met [!DNL Journey Optimizer]

<br>

E-mail:

- Moet subdomain klaar hebben om voor bericht het verzenden te worden gebruikt
- Subdomein kan volledig worden gedelegeerd aan Adobe (aanbevolen) of CNAMEs kan worden gebruikt om aan Adobe-specifieke DNS servers (douane) te richten
- Google TXT-record is nodig voor elk subdomein om goede prestaties te garanderen

<br>

Mobiel duwtje:

- De klant moet over een mobiele ontwikkelaar beschikken om de app te maken
- Adobe Experience Platform Mobile SDK

<br>

## Beveiligingsmechanismen

[[!DNL Journey Optimizer]  Guardrails Product Link &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails.html)

[&#x200B; Guardrails en de Begeleiding van de Latentie van Eind tot Eind &#x200B;](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/deployment/guardrails.html?lang=nl-NL)

## Gerelateerde documentatie

- [[!DNL Experience Platform]  documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-platform.html?lang=nl-NL)
- [[!DNL Experience Platform]  documentatie van Markeringen &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=nl)
- [[!DNL Experience Platform Mobile SDK]  documentatie &#x200B;](https://experienceleague.adobe.com/docs/mobile.html?lang=nl-NL)
- [[!DNL Journey Optimizer]  documentatie &#x200B;](https://experienceleague.adobe.com/docs/journey-optimizer/using/ajo-home.html?lang=nl-NL)
- [[!DNL Journey Optimizer]  productbeschrijving &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-journey-optimizer.html)