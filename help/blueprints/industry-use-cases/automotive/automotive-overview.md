---
title: Gevallen voor autogebruik
description: Ontdek hoe automobielorganisaties Adobe Experience Platform gebruiken om de aankoop van voertuigen te personaliseren, het onderhoud van services te verbeteren en de loyaliteit van de eigenaar te vergroten.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '1843'
ht-degree: 0%

---


# Gebruikszaken voor auto&#39;s

Automobielorganisaties gebruiken Adobe Experience Platform om klantgegevens van dealerinteracties, online voertuigonderzoek, serviceregisters en verbonden automodellen te verenigen in één enkel gezichtspunt van elke eigenaar. Deze stichting maakt gepersonaliseerde ervaringen gedurende de gehele eigendomslevenscyclus mogelijk, van eerste voertuigonderzoek tot aankoop, service en loyaliteit.

## Hoofdlettergebruik

| Gebruiksscenario | Beschrijving | Zakelijke impact | Implementatiepatroon |
| --- | --- | --- | --- |
| [&#x200B; Reis van de Aankoop van het voertuig Personalization &#x200B;](#vehicle-purchase-journey-personalization) | Pas het traject van onderzoek tot aankoop van voertuigen aan met aanbevelingen voor voertuigen, financieringsopties en informatie van dealers. Wanneer potentiële kopers in elke fase op maat advies krijgen, gaan ze sneller en met meer vertrouwen door de funnel. | 20-30% stijging van de conversiekoers, verbeterde verkooppijplijn | [&#x200B; Reis van het Kanaal met Beslissing &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [&#x200B; Herinneringen van de Aanwijzing van de Dienst &#x200B;](#service-appointment-reminders) | Verzend persoonlijke serviceherinneringen op basis van de kilometerstand van het voertuig, de servicegeschiedenis en de voorkeuren van de klant. Proactieve outreach zorgt ervoor dat voertuigen onderhouden blijven en dat klanten terugkeren naar de dealers in plaats van naar derden te zoeken. | De verhoging van 40-50% van de dienstbenoeming toont tarieven, verhoogde de dienstopbrengst | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [&#x200B; handel-binnen de campagnes van de Waarde &#x200B;](#trade-in-value-campaigns) | Proactief bieden handel-binnen waardebeoordelingen aan klanten aan die bereid kunnen zijn om te bevorderen. Het bereiken van eigenaars op het juiste punt in hun eigendomscyclus versnelt de weg naar een nieuwe autoaankoop. | 25-35% toename van de handel in nieuwe voertuigen, toename van de verkoop van nieuwe voertuigen | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [&#x200B; de Aanbevelingen van de Delen en van de Toebehoren &#x200B;](#parts-and-accessories-recommendations) | Aanbevolen relevante onderdelen, accessoires en upgrades op basis van voertuigmodel, eigendomsduur en voorkeuren van de klant. Aanbevolen aanbevelingen op de aftermarket drijven stijgende inkomsten terwijl het helpen van eigenaars meer van hun voertuig krijgen. | 30-40% toename van aankopen van onderdelen/accessoires, verhoogde aftermarket-inkomsten | [&#x200B; Aanbeveling van het Gedrag &#x200B;](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) |
| [&#x200B; Notificaties van het Voertuig het Herhalen &#x200B;](#vehicle-recall-notifications) | Verzend gepersonaliseerde herinneringsberichten met de dienst plannende opties en veiligheidsinformatie. Tijdige, duidelijke terugroepmededelingen beschermen klantenveiligheid en tonen het engagement van het merk aan verantwoordelijke eigendomssteun. | 60-70% toename van de respons bij terugroepacties, verbeterde naleving van de veiligheidsvoorschriften | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [&#x200B; Nieuwe Campagnes van de Modellancering &#x200B;](#new-model-launch-campaigns) | De klanten van het doel die in nieuwe modellanceringen kunnen geinteresseerd zijn die op hun huidige voertuig, voorkeur, en aankoopgeschiedenis worden gebaseerd. Gericht publiek maximaliseert lanceringseffect en bouwt vroege ordedynamiek. | 35-45% toename van de betrokkenheid bij de introductiecampagne, verhoogde interesse voor nieuwe modellen | [&#x200B; Uitgaande Activering van het Bericht van de Partij &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md) |
| [&#x200B; Aanbiedingen van de Financiering en van de Verzekering &#x200B;](#financing-and-insurance-offers) | Aangepaste financierings- en verzekeringsaanbiedingen presenteren op basis van kredietprofiel, voertuigselectie en aankooptijdlijn. Op maat gesneden financiële producten verwijderen de belemmeringen voor de aankoop en helpen klanten zich vertrouwd te maken met hun voorwaarden. | 25-35% verhoging van de acceptatiecijfers van de financiering, hogere inkomsten per verkoop | [&#x200B; Offer Decisioning &#x200B;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) |
| [&#x200B; de Rand die van de Test plant &#x200B;](#test-drive-scheduling) | Zorg voor gepersonaliseerde planning van de testschijf met aanbevelingen van de dealer en beschikbaarheid van het voertuig. Door het voor geïnteresseerde kopers moeilijk te maken om achter het wiel te geraken, wordt het aankooppad versneld. | 50-60% toename in voltooiingssnelheden van de testschijf, verbeterde verkoopconversie | [&#x200B; gebeurtenis-teweeggebracht Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) |
| [&#x200B; Programma&#39;s van de Loyalty van de Eigenaar &#x200B;](#owner-loyalty-programs) | Personaliseer de mededelingen van het loyaliteitsprogramma, beloningen, en exclusieve aanbiedingen die op eigendomsgeschiedenis en loyaliteitsrij worden gebaseerd. Het herkennen van langetermijneigenaars versterkt de emotionele verbinding met het merk. | 40-50% verhoging van loyaliteitsprogramma&#39;s, verhoogde herhaalde aankopen | [&#x200B; Reis van het Kanaal met Beslissing &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) |
| [&#x200B; Garantie en Uitgebreide Plan van de Dienst &#x200B;](#warranty-and-extended-service-plans) | Aanbevelen garantie- en uitgebreide serviceplannen op optimale tijden op basis van de leeftijd, het aantal kilometers en het aankooppatroon van het voertuig. Goed getimede outreach legt inkomsten vast voordat de fabrieksgaranties verlopen. | 20-30% verhoging van uitgebreide garantiegoedkeuring, verhoogde de dienstopbrengst | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [&#x200B; Verbonden Activering van de Eigenschap van de Auto &#x200B;](#connected-car-feature-activation) | Aanbevelingen voor de functie Aangesloten auto aanpassen op basis van de mogelijkheden van het voertuig en de voorkeuren voor de technologie. Wanneer u eigenaars helpt ongebruikte functies te ontdekken, verhoogt u de tevredenheid en versterkt u de digitale relatie. | 35-45% verhoging van functionaliteit activatie, betere klantenervaring | [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) |
| [&#x200B; Coördinatie van het Netwerk van de Dealer &#x200B;](#dealer-network-coordination) | Laat gepersonaliseerde leveranciersaanbevelingen toe die op klantenplaats, voorkeur, en dealerinventaris worden gebaseerd. Het verbinden van klanten met het juiste dealership verbetert de aankoop en de dienstervaring. | 30-40% verhoging van het aantal dealers, verbeterde verkoopcoördinatie | [&#x200B; gekend-Bezoeker Web/App Personalization &#x200B;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) |

## Technische overwegingen bij gebruik

### Aanpassing van het voertuig voor de aanschaf van een reis

- De inventarisgegevens van voertuigen van de systemen voor het beheer van dealers moeten worden geïntegreerd en regelmatig worden vernieuwd, zodat de aanbevelingen de werkelijke beschikbaarheid in de nabijgelegen dealers weerspiegelen.
- Het onderzoeksgedrag van de klant op de hele website, inclusief de activiteiten van de voertuigconfiguratie, het gebruik van vergelijkingsprogramma&#39;s en het downloaden van brochures, moet worden vastgelegd om de inkoopintentsignalen nauwkeurig te kunnen identificeren.
- Loodscoringmodellen moeten rekening houden met zowel online betrokkenheid als offlinesignalen, zoals dealerbezoeken en telefoononderzoeken, om prioriteit te geven aan de vooruitzichten met de hoogste bedoelingen.
- [!DNL Real-Time Customer Data Platform] -profielen moeten anonieme webonderzoekssessies samenvoegen met bekende klantidentiteiten als een mogelijke gebruiker zich registreert of een dealership bezoekt.

### Herinneringen voor servicetoewijzing

- De gegevens over de afgelegde kilometers en telematica van de voertuigen van aangesloten autosystemen of de registers van de dealers moeten in de klantenprofielen stromen om herinneringen op de juiste de dienstintervallen teweeg te brengen.
- Herinneringsberichten moeten een-klik-planningskoppelingen bevatten die de voertuiginformatie van de klant vooraf invullen en aanbevolen servicepunten om de wrijving bij het boeken tot een minimum te beperken.
- De de geschiedenisverslagen van de dienst moeten worden geïntegreerd om het aanbevelen van de diensten te vermijden die onlangs werden voltooid en de herinnering met de specifieke verschuldigde onderhoudspunten te personaliseren.
- [!DNL Journey Optimizer] berichttiming moet rekening houden met de servicecapaciteit van de dealer en de openingstijden om ervoor te zorgen dat klanten afspraken kunnen boeken wanneer ze de herinnering ontvangen.

### Waardecampagnes voor handel

- De taxatiegegevens van derden voor voertuigen moeten worden geïntegreerd en regelmatig worden vernieuwd om ervoor te zorgen dat de met de klanten gedeelde inruilramingen accuraat en concurrerend zijn.
- In de levenscyclusmodellen van de eigenaar moet rekening worden gehouden met factoren zoals de vervaldata van de leaseovereenkomst, de uitbetalingstermijn van de lening en de gemiddelde eigendomsduur per voertuigsegment om het optimale bereikvenster te bepalen.
- Het campagnebericht moet dynamisch verwijzen naar het huidige voertuig van de klant en specifieke upgradeopties voorstellen die aansluiten bij hun voorkeuren en budget.
- [!DNL Experience Platform] -segmenten moeten klanten uitsluiten die onlangs een voertuig hebben gekocht of momenteel in een actief serviceconflict verkeren om te voorkomen dat de service op een slecht tijdstip wordt afgehandeld.

### Aanbevelingen voor onderdelen en toebehoren

- De productcatalogusgegevens moeten informatie over de voertuigcompatibiliteit bevatten, zodat in de aanbevelingen alleen de onderdelen en accessoires worden vermeld die passen bij het specifieke voertuigjaar, het merk en het model van de klant.
- Seizoensgebonden en regionale factoren moeten de aanbevelingen beïnvloeden; winteraccessoires moeten worden bevorderd in koudere klimaten, terwijl verbeteringen van de prestaties meer effect kunnen hebben in regio&#39;s met actieve enthousiaste gemeenschappen.
- Browsergedrag op pagina&#39;s met onderdelen en accessoires moet worden vastgelegd en gekoppeld aan klantprofielen om de aanbevelingen te verfijnen op basis van de getoonde interesse.
- [!DNL Experience Platform] Web SDK-implementatie moet gegevens van het voertuigidentificatienummer van geverifieerde sessies vastleggen om ervoor te zorgen dat de compatibiliteitsfilters correct zijn.

### Melding terugroepen van voertuigen

- De gegevens van het voertuigidentificatienummer moeten nauwkeurig worden bijgehouden in de klantprofielen, zodat de kennisgevingen van terugroeping aan elke betrokken eigenaar worden doorgegeven en niet naar onaangetaste klanten gaan.
- Recall messaging moet voldoen aan de wettelijke vereisten voor de inhoud, het tijdstip en de bevestiging van de levering van veiligheidsberichten op elke toepasselijke markt.
- De levering van meerdere kanalen (e-mail, tekstbericht, dupbericht, en fysieke post) zou moeten worden gebruikt om bereik te maximaliseren, aangezien de veiligheid-kritieke mededelingen hogere leveringszekerheid dan marketing berichten vereisen.
- [!DNL Journey Optimizer] moet de status van de terugroepreactie op het individuele niveau bijhouden en de vervolgcommunicatie escaleren voor eigenaars die de service niet binnen een bepaald tijdsbestek hebben gepland.

### Nieuwe modellanceringscampagnes

- De segmenten van het publiek voor lanceringscampagnes zouden huidig voertuigmodel, eigendomsduur, voorbij modelrentessignalen, en demografische geschiktheid moeten overwegen om de hoogste-volheidsvooruitzichten te identificeren.
- De inhoud van de lancering zou moeten worden gepersonaliseerd om het huidige voertuig van de klant van verwijzingen te voorzien en specifieke verbeteringen of eigenschappen te benadrukken die hun waarschijnlijke prioriteiten richten.
- De timing van de campagne moet gecoördineerd worden met de data waarop het embargo van kracht wordt en met de regionale lanceringsprogramma&#39;s, zodat de klanten op het juiste tijdstip informatie ontvangen voor hun markt.
- [!DNL Real-Time Customer Data Platform] activering van het publiek moet lanceersegmenten aan reclameplatforms voor gecoördineerde betaalde media steun naast het bezit-kanaal outreach synchroniseren.

### Financiering en verzekeringsaanbod

- De regels inzake de beleenbaarheid van financiële aanbiedingen moeten zorgvuldig worden geconfigureerd om te voldoen aan de leningsvoorschriften, zodat de aanbiedingen die aan klanten worden aangeboden, daadwerkelijk in aanmerking komen.
- Integratie van kredietprofielgegevens vereist veilige afhandeling en strenge toegangscontroles, aangezien financiële informatie onderworpen is aan verhoogde privacy- en regelgevingsvereisten.
- In de aanbiedingsvorm moeten duidelijk de voorwaarden, tarieven en voorwaarden worden vermeld die in overeenstemming zijn met de voorschriften inzake consumentenkrediet op elke toepasselijke markt.
- [!DNL Journey Optimizer] besluitvormingsregels zouden in de prijs van het voertuig, beneden betaling, en de voorkeur van de leningstermijnen ertoe moeten brengen om aanbiedingen door relevantie eerder dan eenvoudig door tarief te rangschikken.

### Teststationplanning

- De voorraadsystemen van de handelaar moeten worden geïntegreerd om te bevestigen dat het specifieke voertuigmodel en het bijsnijden waarin de klant geïnteresseerd is, beschikbaar zijn voor testaandrijving bij de aanbevolen handelaar.
- De op plaats-gebaseerde leveranciersaanbevelingen zouden in klantenadres, de verkopersbeoordelingen, en huidige benoemingsbeschikbaarheid moeten een factor zijn om de meest geschikte optie voor te stellen.
- Bevestigings- en herinneringsberichten voor teststations moeten aanwijzingen, contactgegevens van de dealer en de verwachte resultaten bevatten, waardoor de no-show-snelheden afnemen.
- In [!DNL Experience Platform] moeten gedragsgegevens het optimale moment bepalen om een teststation voor te stellen, zodat vroegtijdig contact met beginnende onderzoekers die nog niet klaar zijn, wordt vermeden.

### Programma’s voor loyaliteit aan eigenaars

- Berekeningen van de serviceniveaus moeten meerdere aspecten van de service omvatten, zoals servicebezoeken, aankopen van onderdelen, verwijzingen en aanwezigheid van gebeurtenissen, en niet alleen de aankoopgeschiedenis van voertuigen.
- De systemen van de beloningsvervulling bij dealership en de dienstcentra moeten worden geïntegreerd zodat de loyaliteitsvoordelen op het punt van dienst naadloos kunnen worden terugbetaald.
- Communicatie moet worden aangepast op basis van de levenscyclusfase van de eigendom, waarbij nieuwe eigenaars in hun eerste jaar verschillende waardevoorstellen krijgen dan eigenaars op lange termijn die een mogelijke upgrade naderen.
- [!DNL Journey Optimizer] de reislogica zou rijveranderingen in echt - tijd moeten ontdekken en gefeliciteerde of re-engagement berichten teweegbrengen wanneer de klanten zich tussen loyaliteitsniveaus bewegen.

### Garantie en uitgebreide serviceplannen

- Vervaldatums van de garantie en dekkingsdetails moeten nauwkeurig worden bijgehouden in de profielen van de klant om outreach op het juiste moment te activeren, doorgaans 60-90 dagen voor het verlopen.
- De kilometerstanden en gebruikspatronen van voertuigen op basis van gegevens of dienstgegevens van verbonden auto&#39;s moeten de aanbevelingen van het plan aangeven, aangezien bestuurders met een hoog kilometerbereik een andere dekking genieten dan eigenaars met een laag kilometerbereik.
- De inhoud van de overzichtsvergelijking zou duidelijk en jargon-vrij moeten zijn, die klanten helpen precies begrijpen wat wordt behandeld en de waarde met betrekking tot potentiële buiten-van-zakreparatiekosten.
- [!DNL Real-Time Customer Data Platform] -segmenten moeten onderscheid maken tussen klanten met vervallende fabrieksgaranties, klanten met bestaande uitgebreide plannen die de verlenging naderen en klanten zonder huidige dekking.

### Activering van de functie Aangesloten auto

- De gegevens van het platform van de aangesloten auto moeten worden geïntegreerd om te bepalen welke kenmerken op elk voertuig beschikbaar zijn en welke eigenschappen de eigenaar reeds heeft geactiveerd of gebruikt.
- Bij het bijhouden van de functie moeten activeringsgebeurtenissen, gebruiksfrequentie en betrokkenheidsdiepte worden vastgelegd om de volgorde en plaatsing van functieaanbevelingen aan te passen.
- De meldingskanalen aan boord van het voertuig moeten worden gecoördineerd met e-mail- en app-meldingen om functieaanwijzingen te leveren op het meest contextueel relevante moment, zoals het voorstellen van navigatiefuncties wanneer een wegreis wordt gedetecteerd.
- In [!DNL Experience Platform] -profielen moeten configuratiegegevens van voertuigtechnologie, inclusief geïnstalleerde pakketten en softwareversies, worden opgeslagen om ervoor te zorgen dat de aanbevelingen voor functies compatibel zijn met het specifieke voertuig van de eigenaar.

### Coördinatie van netwerken van dealers

- De voorraadfeeds van de handelaar moeten worden geïntegreerd en regelmatig worden vernieuwd om ervoor te zorgen dat de beschikbaarheid van voertuigen aan klanten nauwkeurig weerspiegelt wat op de partij van elke handelaar is.
- De klant-aan-wederverkoper toewijzingslogica zou nabijheid, dealer specialisatie, taalvoorkeur, en om het even welke bestaande leveranciersverhouding in overweging moeten nemen om de beste gelijke te verstrekken.
- Regels voor routering van leads moeten ervoor zorgen dat wanneer een klant online kooprente uitdrukt, het onderzoek snel de juiste dealer bereikt met de volledige context van de onderzoeksactiviteit van de klant.
- [!DNL Experience Platform] identiteitsresolutie moet scenario&#39;s behandelen waar een klant met veelvoudige dealership in wisselwerking staat, die een verenigd profiel handhaven terwijl het respecteren van de mening van elke dealer van hun eigen klantenverhoudingen.
