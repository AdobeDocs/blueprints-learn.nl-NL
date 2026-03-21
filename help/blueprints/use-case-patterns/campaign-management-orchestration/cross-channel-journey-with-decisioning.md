---
title: Kanaalreis met beslissing
description: Leer hoe u een meerstapsreis kunt ordenen met real-time beslissingen om een optimaal kanaal, optimale inhoud of aanbod te selecteren.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8992'
ht-degree: 0%

---


# De reis over het kanaal met beslissing

Deze handleiding bevat een volledige referentie voor de implementatie van de reis over het kanaal met beslissingen. Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die meertraps, meerkanaalse reizen moeten ordenen die realtime beslissingen bij een of meer reisknooppunten bevatten.

Gebruik deze handleiding om inzicht te krijgen in het volledige landschap van implementatiekeuzen, compromissen te evalueren en naar de relevante Experience League-documentatie te navigeren voor gedetailleerde configuratieinstructies.

De reis over het kanaal met besluitvorming is het verfijnde patroon van campagneorchestratie in het [!DNL Adobe Experience Platform] ecosysteem. Het breidt georkestreerde reizen in meerdere stappen uit door real-time besluitvorming op te nemen — door [!DNL AJO] Beslissing te gebruiken om de huidige context van een profiel te evalueren en dynamisch het optimale kanaal, de optimale inhoud of het aanbod op een of meer beslissingspunten binnen het reiscanvas te selecteren.

## Hoofdlettergebruik

Organisaties moeten steeds vaker adaptieve, gepersonaliseerde klantritten aanbieden die dynamisch reageren op de context van elk individu in real time in plaats van een vaste, vooraf bepaalde volgorde te volgen. Het voorkeurskanaal van een klant, zijn betrokkenheidsgeschiedenis, zijn loyaliteitslaag, hun voorspelde levensduurwaarde, en hun huidige productbelangen allen factor in wat de volgende-beste actie op elk aanraakpunt zou moeten zijn.

De reis over het kanaal met beslissing richt deze behoefte door twee krachtige [!DNL AJO] mogelijkheden te combineren: reis orchestratie (die de multi-step stroom, timing, voorwaarden, en kanaallevering beheert) en besluit (die toelatingsregels evalueert, rangschikkingsstrategieën toepast, en de optimale aanbieding of inhoudvariant op elk beslissingspunt selecteert).

Dit patroon is geschikt wanneer:

- De reis moet dynamisch aan de staat in real time van elk profiel aanpassen eerder dan het volgen van een vast kanaal of inhoudsopeenvolging
- Meerdere aanbiedingen, inhoudvarianten of kanalen zijn kandidaten voor een of meer reisknooppunten en de beste optie moet worden geselecteerd op basis van de profielcontext
- Voor een optimale keuze voor de keuze van het aanbod over de hele reis is een door AI of formule ondersteunde rangschikking nodig.
- De organisatie wil de logica van de kanaalselectie consolideren en beheer in een gecentraliseerd besluitvormingskader aanbieden eerder dan het handhaven van complexe vertakkende logica

Het doelpubliek omvat marketers die levenscyclusprogramma&#39;s, loyaliteitstrajecten, win-back opeenvolgingen, en instapkaartstromen beheren waar verpersoonlijking op schaal geautomatiseerde besluitvorming op elk aanraakpunt vereist.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gericht door dit gebruikspatroon.

**[lever gepersonaliseerde klantenervaringen](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Inhoud, aanbiedingen en berichten voor individuele voorkeuren, gedrag en levenscyclusfase aanpassen.
**KPIs:** Betrokkenheid, Conversietarieven, Tevredenheid van de Klant (CSAT)

**[de klantenloyaliteit en levenwaarde van de verhoging](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Verbeter klantenverhoudingen en maximaliseer waarde op lange termijn door loyaliteitsprogramma&#39;s, beloningen, en gepersonaliseerde betrokkenheid.
**KPI&#39;s:** Levensduur klant, Retentie, Upsell/Cross-sell%

**[verbetert klantenbehoud](../../business-objectives/customer-experience/improve-customer-retention.md)**
Bestaande klanten betrokken houden en vernieuwen door waardegestuurde ervaringen en doorlopende relatieverpleging.
**KPIs:** Behoud, de Waarde van het Leven van de Klant, Betrokkenheid

**[de dwars-verkoop van de aandrijving &amp; upsell opbrengst](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Aanvullende en hoogwaardige producten of services aan bestaande klanten promoten op basis van gedrag en aankoopgeschiedenis.
**KPIs:** Upsell/Cross-Sell %, Incrementele Inkomsten, de Waarde van het Leven van de Klant

## Voorbeelden van tactische gebruiksgevallen

De volgende scenario&#39;s tonen aan hoe de reis over het kanaal met besluitvorming in de praktijk kan worden toegepast.

- **Aangepaste win-backreis** — Een multi-step reis waar de beslissing het kanaal (e-mail, duw, of SMS) selecteert die op de de betrokkenheidsgeschiedenis van elk profiel wordt gebaseerd, en dynamisch de beste aansporingsaanbieding selecteert die op voorspelde levenwaarde wordt gebaseerd
- **volgende-best-actie levenscyclusreis** — Beslissing bepaalt wat in elk stadium van de klantenlevenscyclus te communiceren, selecterend van onboarding inhoud, dwars-verkoopaanbiedingen, loyaliteitbeloningen, of bewaarprikkels
- **Gepersonaliseerd onboarding met dynamische inhoudselectie** — Nieuwe klant op het instappen reis waar elk touchpoint besluit gebruikt om de meest relevante inhoud, de uiteinden, of de activeringsaanbiedingen van het productonderwijs te selecteren
- **de programmareis van de het interkanaalloyaliteit met gepersonaliseerde beloningen** — De vooruitgang van de leden van de Loyalty door een reis waar de beslissing gepersonaliseerde beloningsaanbiedingen selecteert die op rij, koopgeschiedenis, en categorievestiging worden gebaseerd
- **Dynamische re-engagement met kanaal en aansporingoptimalisering** — De sluimerende klant re-engagement waar zowel het outreach kanaal als de aansporing dynamisch worden geselecteerd om reactiewaarschijnlijkheid te maximaliseren
- **Klantenlevenscyclus van de Klant met AI-gerangschikte inhoudaanbevelingen** — Doorlopende boomgang waar de AI-gerangschikte beslissing de meest relevante inhoud of productaanbevelingen op elk aanraakpunt selecteert

## Kernprestatie-indicatoren

Gebruik de volgende KPIs om de doeltreffendheid van dit gebruiks gevalpatroon te meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Voltooiingssnelheid reis | Percentage profielen dat de volledige reis voltooit | Reisrapport: voltooid/ingevoerd |
| Aanbiedingsacceptatie | Percentage geselecteerde aanbiedingen met beslissingsbevoegdheid die betrekking hebben op (geklikt, afgelost) | Beslissingsrapport: klik aan/bied indruk |
| Betrokkenheid kanaal | Open en klik tarieven over elk kanaal dat in reis wordt gebruikt | Metriek van de levering per kanaal in reisrapport |
| Conversiesnelheid | Percentage deelnemers aan de reis die de doelconversieactie voltooien | Reisexit-gebeurtenis volgen of CJA funnel-analyse |
| Percentage voor alternatieven | Percentage van de verzoeken om terugzending van het fallback-aanbod in plaats van een gepersonaliseerd aanbod | Beslissingsrapport: fallback-selecties / totaal selecties |
| Gevolgen van de levensduur van de klant | Verandering in CLV voor reisdeelnemers versus controlegroep | CJA-cohortanalyse met holdout-vergelijking |
| Opbrengsten voor crossverkopen/upverkopen | Incrementele inkomsten die worden toegeschreven aan door besluiten geselecteerde aanbiedingen | CJA-toewijzingsanalyse bij door aanbiedingen gestuurde omzettingen |
| Effectiviteit beslissingsrelevantie | Prestatieverschil tussen beursgenoteerde aanbiedingen en willekeurige/prioritaire selectie | A/B-experiment waarbij classificatiestrategieën worden vergeleken |

## Hoofdletterpatroon gebruiken

**Reis van het Kanaal over de weg met besluit**

Orchestreer een multi-step, multi-channel reis die besluitvorming in real time bij één of meerdere knopen opneemt om het optimale kanaal, de inhoud, of de aanbieding te selecteren.

**Keten van de Functie:** de Evaluatie van het publiek > de Uitvoering van de Reis > de Selectie van het Besluit > de Selectie van het Kanaal > de Levering van het Bericht > het Melden

## Applicaties

De volgende toepassingen worden gebruikt om dit gebruiks gevalpatroon uit te voeren.

- **[!DNL Adobe Journey Optimizer] ([!DNL AJO])** — Reis orchestration (multi-step canvas ontwerp, ingangsvoorwaarden, wacht, voorwaarden, uitgangscriteria), bericht authoring over kanalen, de configuratie van de kanaaloppervlakte, conflict en prioriteitsbeheer
- **[!DNL Adobe Journey Optimizer]Beslissing** — Beheer van aanbod- en inhoudsonderdelen, toelatingsregels, classificatiestrategieën (prioriteit, formule, AI), beleidsregels, plaatsingen, fallback-aanbiedingen
- **[!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP])** — De evaluatie van het publiek voor de ingang van de reis en biedt toelatingssegmenten, profielverrijking met gegevens verwerkte attributen en aandrijvingsscores, toestemming en governance handhaving aan
- **[!DNL Adobe Experience Platform] ([!DNL AEP])** — Echte - de opslag van het Profiel van de Klant, de Dienst van de Identiteit voor dwars-kanaalresolutie, gegevensmodellering en opname infrastructuur

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | [!DNL AJO] zandbak met reis, campagne, en gevormde beslissingstoestemmingen. Kanaaloppervlakken voor alle mogelijke leveringskanalen. Gebruikersrollen voor reisontwerpers, besluitvormingsmanagers, en inhoudsauteurs. | [&#x200B; het overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [&#x200B; overzicht van de Toegangscontrole &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | Profielschema moet kenmerken bevatten die worden gebruikt voor beslissingen (bijvoorbeeld loyaliteitsniveau, koopgeschiedenis, kanaalvoorkeuren, betrokkenheidsscores). De catalogus van de aanbieding en de schema&#39;s van het besluitpunt moeten worden gevormd. De schema&#39;s van ExperienceEvent moeten gedragssignalen vangen die door toelatingsregels en rangschikkingsformules worden gebruikt. | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/home), [&#x200B; de samenstellingsgrondbeginselen van het Schema &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Gegevensbronnen en -verzameling | Verondersteld op plaats | Profielkenmerken en gedragssignalen die door beslissingen worden gebruikt, moeten actueel zijn. Gebeurtenisstreaming in realtime is vereist als de reis gebeurtenisgestuurde entry- of exit-criteria gebruikt. Web SDK, Mobile SDK, of de server-zijinzameling moet voor kanalen actief zijn die besluitvormingscontext voeden. | {het overzicht van SDK van 0} Web [&#128279;](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [&#x200B; Bronoverzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identiteit en profielconfiguratie | Vereist | De oplossing van de identiteit van meerdere kanalen is van essentieel belang. De reis moet profielen via e-mail, push, SMS en het web oplossen. Het beleid van de fusie moet een verenigd profiel voor besluit produceren. Identiteitsnaamruimten voor alle klant-id&#39;s (CRM-id, e-mail, ECID, telefoon) moeten zijn geconfigureerd. | [&#x200B; overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [&#x200B; overzicht van het beleid van de Fusie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Auditiedefinitie en segmentatie | Vereist | Omschrijving van het publiek bij binnenkomst voor de reis. Aanvullende segmenten die worden gebruikt voor de subsidiabiliteitsregels en vertakking van voorwaarden binnen de reis. De methode van de evaluatie moet latentievereisten (het stromen voor ingang in real time, partij voor gepland) aanpassen. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [&#x200B; de gids UI van de Bouwer van het Segment &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Berekende kenmerken, zoals AI-propyiteitsscores van de Klant, servicescore, kanaalvoorkeurscores en levenswaardeberekeningen, verbeteren de beslissingskwaliteit aanzienlijk. Deze verrijkte profielkenmerken maken geavanceerdere toelatingsregels en rangschikkingsformules mogelijk. | [&#128279;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [&#x200B; overzicht van de Klant AI van 0&rbrace; Berekende attributen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | De geschiedenis van de aanbieding en de gegevens van de besluitvormingsgebeurtenis accumuleren zich in tijd en zouden bewaarbeleid moeten hebben. Toegestane handhaving over meerdere kanalen is van essentieel belang — profielen zonder geldige toestemming voor een kanaal moeten worden uitgesloten van het leveringspad van dat kanaal. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [&#x200B; Toestemming in Journey Optimizer &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | De handhaving van het bestuur over veelvoudige kanalen en aanbiedingstypes is belangrijk wanneer de beslissing profielen aan verschillende kanalen met verschillende beperkingen van het gegevensgebruik kan leiden. Zorgt voor de levering van de compatibele aanbieding op alle kanalen. | [&#x200B; het beheer van Gegevens overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [&#x200B; de handhaving van het Beleid &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview) |
| Bewaking en waarneming | Opgenomen | Reis- en beslissingscontrole is van essentieel belang voor productieactiviteiten. De alarm voor de mislukkingen van de reistoegang, beslissingsfallback spikes, en leveringsfouten laten snelle probleemoplossing toe. | [&#x200B; het overzicht van Alarm &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [&#x200B; Overzicht van de Inzichten van de Waarneming &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | Reis- en beslissingsverslagen worden behandeld in de rapportagefase. CJA-analyse van de effectiviteit van beslissingen, kanaalmixoptimalisatie, prestaties en ROI voor reizen biedt de benodigde inzichten om de rangschikkingsstrategieën te verfijnen en de reis in de loop der tijd te optimaliseren. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [&#x200B; AJO + de integratiegids van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de catalogus van de toepassingsfunctie uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer] ([!DNL AJO])

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Kanaalconfiguratie | Fase 2: Kanaalconfiguratie | Kanaaloppervlakken configureren voor alle kanalen die door de beslissing kunnen worden geselecteerd of die door de reis worden gebruikt (e-mail, SMS, push, in-app) |
| Berichtontwerp | Fase 4: Berichtgeving | De inhoud van het het berichtbericht van de auteur voor elk kanaal en integreert beslissingsuitvoer — bied plaatsingen, dynamische inhoudblokken, verpersoonlijkingstkens van geselecteerde aanbiedingen aan |
| Besluitvorming | Fase 3: Instellingen voor besluitvorming | Vorm aanbiedingspunten, toelatingsregels, rangschikkingsstrategieën, besluitvormingsbeleid, en reserveaanbiedingen voor elk beslissingspunt in de reis |
| Journey Orchestration | Fase 5: Ontwerpen en activeren van reizen | Ontwerp het multi-step wegcanvas met ingangsvoorwaarden, beslissingsknopen, kanaal verpletterend, wacht stappen, berichtacties, en uitgangscriteria |
| Conflict- en prioriteitsbeheer | Fase 5: Ontwerpen en activeren van reizen | Prioriteitsscores en conflictopsporing configureren als meerdere reizen tegelijkertijd op dezelfde profielen kunnen worden gericht |
| Frequentie en bedrijfsregels | Fase 5: Ontwerpen en activeren van reizen | De frequentiecappen van het bericht over kanalen afdwingen om over overseinen binnen de reis met meerdere kanalen te verhinderen |
| Rapportage en prestatieanalyse | Fase 6: Rapportage en bewaking | De reis en de metriek van de per-knooplevering van de monitor, beslissingsprestaties, en kanaalbetrokkenheid |

### [!DNL Real-Time CDP] ([!DNL RT-CDP])

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Fase 1: Evaluatie van het publiek | Bepaal en evalueer het ingangspubliek of de kwalificerende ingangsgebeurtenis; creeer geschiktheidssegmenten die door besluit worden gebruikt |
| Profielverrijking | Vereiste / Ondersteuning | Verrijkt profielen met berekende kenmerken en eigenschapscores die de beslissingskwaliteit verbeteren |
| Goedkeuring en handhaving van bestuur | Fase 2: Kanaalconfiguratie | Overeenstemmingsvoorkeuren afdwingen op alle kanalen; zorg ervoor dat de levering van de aanbieding voldoet |

## Vereisten

Voltooi het volgende voordat u begint met de implementatie.

- [ ] [!DNL AJO] De sandbox is voorzien van mogelijkheden voor reisorkest en besluitvorming ingeschakeld
- [ ] Alle doelkanalen (e-mail, SMS, push) hebben actieve, geverifieerde kanaaloppervlakken
- [ ] Profielschema bevat kenmerken die vereist zijn voor de besluitvorming (loyaliteitsniveau, aankoopgeschiedenis, kanaalvoorkeuren, betrokkenheidsscores)
- [ ] Identiteitsresolutie voor meerdere kanalen is geconfigureerd — profielen kunnen worden opgelost via e-mail, pushtoken, telefoonnummer en web-id&#39;s
- [ ] Toegangspubliek wordt gedefinieerd en geëvalueerd met een populatie die niet gelijk is aan nul
- [ ] Catalogusinhoud aanbieden (creatieve elementen, kopiëren, juridische disclaimers) is goedgekeurd en gereed voor configuratie
- [ ] Er worden gegevens met toestemming ingevoerd en de handhaving van de toestemming is actief voor alle doelkanalen
- [ ] Inhoudssjablonen en -fragmenten voor elk kanaal zijn ontworpen en goedgekeurd
- [ ] Regels voor frequentiecontrole worden gedefinieerd en geïmplementeerd als de organisatie een beleid voor intercampagnefrequenties heeft
- [ ] Als u beslissingen op basis van een AI-classificatie gebruikt, bestaan minimaal 1000 conversiegebeurtenissen voor modeltraining

## Implementatieopties

Bekijk de volgende opties en selecteer de benadering die het beste bij uw vereisten past.

### Optie A: Reis met aanbod (vast kanaal, dynamische inhoud)

**Best voor:** reizen waar de kanaalopeenvolging vooraf wordt bepaald maar de inhoud of de aanbieding op elk aanraakpunt zou dynamisch moeten worden geselecteerd — loyaliteitsreizen met gepersonaliseerde beloningen, re-engagement met dynamische prikkels, levenscycluscultuur met AI-gerangschikte inhoudaanbevelingen.

#### Hoe werkt het

Het canvas van de reis bepaalt de vaste opeenvolging van kanalen en timing (bijvoorbeeld, Dag 0: E-mail, Dag 3: Duw, Dag 7: SMS). Bij elke knoop van de berichtactie, selecteert een besluitvormingsbeleid de beste aanbieding of inhoud om in het bericht van een gevormde catalogus van in aanmerking komende punten te omvatten. Aanbiedingen worden beheerd in de [!DNL AJO] Beslissingscatalogus met geschiktheidsregels die een profiel aanbieden dat in aanmerking komt voor, en rangschikkingsstrategieën die bepalen welke in aanmerking komende aanbieding het beste geschikt is.

Deze aanpak scheidt de &quot;wanneer en waar&quot; (reisorkest) van de &quot;wat&quot; (beslissing). De reisontwerper controleert de kanaalstroom, terwijl de besluitvormingsmanager de aanbiedingscatalogus, toelatingsregels, en rangschikkende logica onafhankelijk controleert. Deze scheiding van zorgen maakt de implementatie duurzamer en staat de aanbiedingscatalogus toe om zich te ontwikkelen zonder het reiscanvas te veranderen.

Aanbiedingsplaatsen worden direct ingesloten in berichtinhoud met de e-mail-Designer of andere kanaaleditors. Wanneer het bericht op leveringstijd wordt teruggegeven, evalueert de bepalende motor de geschiktheid van het profiel en het rangschikken om de optimale aanbieding voor elke plaatsing in het bericht te selecteren.

#### Belangrijkste overwegingen

- Kanaalvolgorde is statisch — alle profielen volgen hetzelfde kanaalpad, ongeacht hun voorkeuren
- De complexiteit van beslissingen is lager omdat alleen inhoud/aanbiedingen worden geselecteerd, niet kanalen
- Aanbiedingscatalogus kan onafhankelijk van de reis worden beheerd
- Voor elke plaatsing moeten back-upaanbiedingen worden geconfigureerd om profielen af te handelen zonder gepersonaliseerde aanbiedingen die hiervoor in aanmerking komen

#### Voordelen

- Eenvoudiger reiscanvas — geen vertakkende logica voor kanaalselectie
- Duidelijke scheiding van zorgen tussen reisontwerp en aanbiedingsbeheer
- Eenvoudiger te testen en te valideren — elk kanaalpad is deterministisch
- Minder complexiteit bij implementatie en snellere markttijden
- Wijzigingen in catalogus voorstellen worden onmiddellijk van kracht zonder wijzigingen in de reis

#### Beperkingen

- Kan het kanaal niet aanpassen op basis van het gedrag of de voorkeuren van het individuele profiel
- Profielen die de voorkeur geven aan een kanaal boven een ander kanaal ontvangen nog steeds berichten op vooraf ingestelde kanalen
- Optimaliseert niet voor betrokkenheidsniveaus op kanaalniveau

#### Experience League-verwijzingen

- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)

### Optie B: Reis met dynamische kanaalselectie (vaste inhoud, dynamisch kanaal)

**Best voor:** reizen waar de inhoud bij elk aanraakpunt gelijkaardig is maar het kanaal zou dynamisch moeten worden geselecteerd gebaseerd op profielcontext — adaptieve win-back (e-mail versus duw vs. SMS gebaseerd op overeenkomst), volgende-best-actiesprogramma&#39;s waar kanaaloptimalisering het primaire doel is.

#### Hoe werkt het

De reis gebruikt voorwaardenknopen die door profielattributen (zoals de scores van de kanaalvoorkeur, laatste betrokkenheidskanaal, of toestemmingsstatus) worden geïnformeerd of beslissingsoutput aan routeprofielen aan verschillende kanaalwegen. Elk pad levert kanaalspecifieke inhoud via een eigen knooppunt voor berichtactie. De beslissingslogica bepaalt welk kanaal het meest waarschijnlijk betrokkenheid zal wekken op basis van de gedragsgeschiedenis van het profiel.

De selectie van het kanaal kan worden uitgevoerd gebruikend de knopen van de reisvoorwaarde met de evaluaties van de profielattributen (bijvoorbeeld, als `channelPreference = "push"` route aan de drukknop), of door besluit met kanaal-specifieke punten te gebruiken waar elke &quot;aanbieding&quot;een kanaal vertegenwoordigt en de rangschikkingsstrategie het beste kanaal bepaalt.

Deze benadering optimaliseert het leveringskanaal terwijl het houden van inhoud vrij verenigbaar over kanalen. Het vereist berichtinhoud die voor elk mogelijk kanaal moet worden ontworpen, en kanaaloppervlakken moeten voor alle kandidaatkanalen worden gevormd.

#### Belangrijkste overwegingen

- Vereist varianten van de berichtinhoud voor elk kandidaatkanaal
- Kanaaloppervlakken moeten actief zijn voor alle mogelijke kanalen
- De logica van de voorwaarde of beslissingsconfiguratie moet rekening houden met toestemming — de profielen zonder de toestemming van SMS kunnen niet aan de weg van SMS worden verpletterd
- Het canvas van de reis is complexer met vertakkende wegen voor elk kanaal

#### Voordelen

- Hiermee optimaliseert u de kanaalselectie voor elk afzonderlijk profiel
- Verhoogt de algemene betrokkenheid door profielen op hun voorkeurskanaal te bereiken
- Voldoet automatisch kanaalspecifieke toestemming door toestemming-bewuste het verpletteren
- Kan betrokkenheidsgeschiedenis en kanaalvoorkeurscores opnemen in het routeren van beslissingen

#### Beperkingen

- Complexere reiscanvas met meerdere kanaalvertakkingen
- De inhoud moet voor elk kanaal afzonderlijk worden geschreven (hoewel de berichtenintentie hetzelfde is)
- Harder te testen — moet alle mogelijke kanaalpaden valideren
- De personalisatie van de inhoud binnen elk kanaal is statisch (geen aanbodbesluit)

#### Experience League-verwijzingen

- [Voorwaardeactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Een reis maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Optie C: volledig adaptieve reis (dynamisch kanaal + dynamische inhoud)

**Best voor:** Maximale verpersoonlijking — zowel het kanaal als de inhoud/de aanbieding worden dynamisch geselecteerd bij elke knoop. Geschikt voor hoogwaardige klantensegmenten, geavanceerde loyaliteitsprogramma&#39;s, en organisaties met rijpe besluitvormingspraktijken en rijke profielgegevens.

#### Hoe werkt het

Deze optie combineert Opties A en B. De reis gebruikt besluitvorming op twee niveaus: eerst om te bepalen welk kanaal voor elk aanraakpunt moet worden gebruikt, en tweede, om te bepalen welke inhoud of aanbieding om in het geselecteerde kanaal te leveren. Elk beslissingspunt in de reis evalueert de huidige context van het profiel om zowel het kanaal als de inhoud te selecteren.

De implementatie vereist uitgebreide besluitvormingsinstellingen met beslissingsbeleid voor zowel kanaalselectie als selectie van inhoud/aanbod. Kanaalselectie kan een besluitvormingsbeleid gebruiken wanneer elk item een kanaal vertegenwoordigt met op toestemming en betrokkenheid gebaseerde subsidiabiliteitsregels, terwijl bij de selectie van inhoud een apart besluitvormingsbeleid wordt gebruikt met op relevantie gerangschikte aangeboden items.

Dit is de meest complexe variant en vereist de diepste integratie tussen reisorganisatie en besluitvorming. Het levert de hoogste graad van verpersoonlijking maar vereist ook de meeste configuratie, het testen, en aan de gang zijnde beheer.

#### Belangrijkste overwegingen

- Vereist twee beslissingslagen: kanaalselectie en inhoudselectie
- De complexiteit van het canvas op reis is het hoogst met geneste vertakking en besluitvorming op elk knooppunt
- Uitgebreide tests vereist voor alle mogelijke kanaalinhoudcombinaties
- Vereist rijke profielgegevens (betrokkenheidsgeschiedenis, kanaalvoorkeuren, productaffiniteit, populatiescore) voor effectieve besluitvorming
- Beslissingen op basis van AI-waarden hebben aanzienlijk baat bij berekende kenmerken

#### Voordelen

- Maximale personalisatie — elk aanraakpunt is geoptimaliseerd voor kanaal en inhoud
- Beste betrokkenheid en conversiepotentieel voor goed geconfigureerde implementaties
- Centraliseert alle verpersoonlijkingslogica in besluitvorming eerder dan statische reistakken
- Kan voortdurend verbeteren door het leren van een AI-classificatiemodel

#### Beperkingen

- Hoogste complexiteit van implementatie en langste markttijd
- Vereist de meest uitgebreide aanbiedingencatalogus en de voorbereiding van kanaalinhoud
- moeilijker problemen op te lossen wanneer de leveringskwesties zich voordoen
- Vereist een geavanceerde gegevensinfrastructuur met rijke profielkenmerken
- AI-classificatie vereist voldoende conversiegebeurtenisvolume voor modeltraining

#### Experience League-verwijzingen

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Optievergelijking

Gebruik de volgende tabel om de drie implementatieopties in één oogopslag te vergelijken.

| Criteria | Optie A: Beslissing van aanbieding | Optie B: Dynamisch kanaal | Optie C: Volledig adaptief |
| --- | --- | --- | --- |
| Best voor | Volgorde van vaste kanalen, dynamische inhoud | Kanaaloptimalisatie, consistente inhoud | Maximale personalisatie voor beide dimensies |
| Complexiteit | Gemiddeld | Medium-High | Hoog |
| Reiscanvas | Eenvoudig (lineair met beslissingen bij actieknooppunten) | Gemiddeld (vertakking voor kanaalpaden) | Complex (geneste vertakking met besluitvorming op meerdere niveaus) |
| Beslissingsbereik | Alleen selectie van inhoud/aanbod | Alleen kanaalselectie | Zowel kanaal- als inhoudselectie |
| Inhoud-eisen | Eén set inhoud per kanaal (met aanbiedingspakketten) | Inhoud voor elk kandidaatkanaal | Inhoud met plaatsingen voor elk kandidaat-kanaal |
| Profielgegevensbehoeften | Matig (aanbiedingsbeleenbaarheidscriteria) | Modern (kanaalvoorkeur, betrokkenheid) | Hoog (zowel kanaal- als aanbiedingskenmerken) |
| Tijd tot de markt | Sneller | Gemiddeld | Langste |
| Doorlopend beheer | Catalogusbeheer aanbieden | Logische beheer voor kanaalroutering | Zowel bieden catalogus als kanaal het verpletteren aan |
| Personalization-diepte | Inhoud varieert, kanaal vast | Kanaal varieert, inhoud vergelijkbaar | Zowel kanaal als inhoud variëren |

### Kies de juiste optie

Gebruik de volgende richtlijnen om de beste optie voor uw situatie te bepalen.

- **Begin met Optie A** als uw kanaalstrategie reeds wordt bepaald (bijvoorbeeld, &quot;wij verzenden altijd eerst e-mail, dan duw, dan SMS&quot;) en de primaire verpersoonlijkingsbehoefte selecteert de juiste aanbieding of de inhoud bij elk aanraakpunt. Dit is het meest gangbare uitgangspunt voor organisaties die nog niet over beslissingen beschikken.

- **kies Optie B** als kanaaloptimalisering uw primair doel is — u elke klant op het kanaal wilt bereiken zij het waarschijnlijkst om met in dienst te nemen zijn, maar de berichtinhoud is vrij verenigbaar over kanalen. Hiervoor zijn kanaalvoorkeursgegevens voor profielen vereist.

- **kies Optie C** slechts wanneer u rijpe beslissingsinfrastructuur, rijke profielgegevens (met inbegrip van gegevens verwerkte attributen en aandrijvingsscores), een goed bevolkte aanbiedingscatalogus, en de organisatorische capaciteit hebt om de ingewikkeldheid te beheren. Vele organisaties beginnen met Optie A of B en evolueren aan Optie C aangezien hun beslissingsrijpheid stijgt.

- **als u onzeker** bent, begin met Optie A. Het levert zinvolle verpersoonlijking met de laagste ingewikkeldheid, en de aanbiedingencatalogus u voor Optie A bouwt is direct herbruikbaar als u later aan Optie C evolueert.

## Uitvoeringsfasen

De volgende fasen lopen door de implementatie van begin tot eind van dit gebruikspatroon.

### Fase 1: Evaluatie door het publiek

**functie van de Toepassing:** [!DNL RT-CDP]: De Evaluatie van het publiek

Deze fase vormt het ingangspubliek dat bepaalt welke profielen de reis ingaan, en om het even welke extra segmenten die voor aanbieding geschiktheidsregels of voorwaarde die binnen de reis vertakken worden gebruikt. De definitie van het publiek is de basis voor alle logica van downstreamreizen en besluitvorming.

#### Besluit: type van binnenkomst

Hoe moeten profielen de reis ingaan — via een gepland publiek gelezen of een real-time gebeurtenistrekker?

>[!NOTE]
>Selecteer één ingangstype op basis van de timing en activeringsvereisten van uw reis.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Publiek lezen (batchvermelding) | Levenscyclusprogramma&#39;s, loyaliteitsreizen, geplande herplaatsingscampagnes | Profielen worden in batches ingevoerd op geplande tijdstippen; het publiek wordt geëvalueerd tijdens het lezen; ondersteunt grote doelformaten |
| Audience Qualification (streaming) | Door gedrag geïnitieerde reizen waarbij de toegang moet plaatsvinden wanneer een profiel een segment binnengaat of verlaat | Bijna real-time invoer; vereist streaming-in aanmerking komende segmentdefinitie; goed voor trajecten op basis van mijlpaal |
| Eenvoudige gebeurtenis (activering van gebeurtenis) | Het specifieke evenement moet de reis in gang zetten (bijvoorbeeld aankoop, afstoting van winkelwagentjes, registratie) | Real-time invoer bij gebeurtenis; vereist configuratie van gebeurtenisschema; beperkt tot 5.000 gebeurtenissen/seconde |

#### Besluit: Methode voor de evaluatie van het publiek

Hoe snel moet het publiek profielen kwalificeren?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Batch | Dagelijkse of periodieke publieksupdates zijn voldoende; geplande campagneschijnritten | Verwerkt tot 24M profielen per baan; op programma-gebaseerd; de meeste gesteunde uitdrukkingen van de segmentregel |
| Streaming | Het lidmaatschap van het publiek in real time is nodig voor gebeurtenis-teweeggebrachte of op kwalificatie-gebaseerde ingang | Bijna real-time; beperkte functie van segmentregel; geen op tijd gebaseerde aggregaties |
| Edge | Benodigde kwalificatie voor dezelfde sessie | Milliseconde latentie; eenvoudige kenmerkcontroles slechts; beperkt tot de attributen van het randprofiel |

#### Belangrijkste configuratiedetails

**navigatie UI:** Klant > Soorten publiek > leidt tot publiek > bouwt regel

- Bepaal het ingangspubliek gebruikend de Bouwer van het Segment met de uitdrukkingen van de segmentregel richtend de relevante profielattributen en gedragsgebeurtenissen
- Extra beleenbaarheidscategorieën maken als de beleenbaarheidsregels van de aanbieding verwijzen naar het segmentlidmaatschap (bijvoorbeeld &quot;High Value Customers&quot;, &quot;Loyalty Gold Tier&quot;)
- Controleren of de doelpopulatie niet gelijk is aan nul voordat u verdergaat met de configuratie van de reis
- Selecteer het samenvoegbeleid dat de verenigde profielweergave produceert die nodig is voor de besluitvorming

#### Experience League-documentatie

- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Fase 2: Kanaalconfiguratie

**functie van de Toepassing:** [!DNL AJO]: De Configuratie van het kanaal

Deze fase vormt kanaaloppervlakten voor elk kanaal dat de reis voor berichtlevering kan gebruiken. Alle kandidaatkanalen moeten actieve, geverifieerde oppervlakken hebben voordat berichten kunnen worden geschreven of de reis kan worden gepubliceerd. Voor dit patroon configureert u doorgaans oppervlakken voor minimaal e-mail, SMS en push, en mogelijk ook in de app of op internet als bij de besluitvorming deze kanalen kunnen worden geselecteerd.

#### Besluit: welke kanalen moeten worden geconfigureerd

Welke kanalen zijn geschikt voor de reis — hetzij als vaste trajecten (opties A/B), hetzij als voor besluiten selecteerbare kanalen (opties B/C)?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen e-mail | Single Channel-reis met beslissing over de aanbieding (Option A, alleen e-mail) | Eenvoudige configuratie; vereist subdomein delegatie en IP warmte |
| E-mail + Push | Tweekanaals reis; gemeenschappelijk voor op betrokkenheid gerichte reizen | Voor push zijn APN&#39;s/FCM-referenties vereist; voor mobiele app moet SDK zijn geïntegreerd |
| E-mail + SMS + Push | Volledige reis over het kanaal; meest gebruikelijk voor Opties B en C | SMS vereist leveranciersgeloofsbrieven (Sinch, Twilio, Infobip); elk kanaal heeft zijn eigen oppervlakte nodig |
| E-mail + SMS + Push + In-app | Maximale kanaaldekking inclusief oppervlakken tijdens de sessie | Voor In-app is mobiele SDK en configuratie van oppervlak van app vereist |

#### Besluit: methode voor subdomeindelegatie (e-mail)

Hoe moet het verzendende subdomein worden gedelegeerd aan Adobe?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Volledige delegatie | De organisatie wil Adobe alle DNS verslagen voor het verzendende subdomain beheren | Eenvoudigste installatie; Adobe verwerkt SPF, DKIM, DMARC; minder controle over DNS |
| CNAME-delegatie | Organisatie moet controle over DNS-records houden | Complexere installatie; klant beheert DNS; biedt meer flexibiliteit |

#### Belangrijkste configuratiedetails

**navigatie UI:** Beleid > Kanalen > de oppervlakten van het Kanaal > Create oppervlakte

- Voor e-mail: vorm subdomain, IP pool, afzendernaam, antwoord-aan adres, en unsubscribe behandeling
- Voor SMS: configureer de referenties van de SMS-provider en het afzendernummer
- Voor push: configureer APN&#39;s en FCM-referenties voor iOS en Android
- Controleer of elk oppervlak actief is voordat u verdergaat
- Bevestig IP warmup volledig is voor e-mail die IPs verzendt

#### Experience League-documentatie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [IP-pools maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Fase 3: Instellingen voor besluitvorming

**functie van de Toepassing:** [!DNL AJO]: Beslissing

Deze fase vormt het volledige besluitvormingskader met inbegrip van plaatsingen, toelatingsregels, gepersonaliseerde aanbiedingen, reserveaanbiedingen, inzamelingskwaliteiten, inzamelings, rangschikkingsstrategieën, en besluitvormingsbeleid. Deze fase leidt tot de besluitvormingslogica die op de punten van het reisbesluit zal worden aangehaald.

#### Besluit: Toepassingsgebied van de beslissing

Wat moet een beslissing selecteren — aanbiedingen/inhoud (Option A), kanalen (Option B) of beide (Option C)?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen aanbod/inhoud selecteren | De kanaalvolgorde is vast. De inhoud wordt aangepast | Het beleid van het besluit richt punten met inhoudrepresentaties per plaatsing aan |
| Alleen kanaalselectie | Inhoud is consistent; optimalisatie vindt plaats op het leveringskanaal | Beslissingsitems vertegenwoordigen kanalen; geschiktheid omvat toestemmingscontroles; classificatie gebruikt betrokkenheidsgegevens |
| Zowel kanaal als inhoud | Volledige, adaptieve personalisatie over het gehele kanaal en de inhoud | Vereist twee lagen van besluitvormingsbeleid; het meest complexe maar hoogste personalisatie |

#### Besluit: beoordelingsstrategie

Hoe moeten in aanmerking komende aanbiedingen gerangschikt worden om de beste te selecteren?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Op prioriteit gebaseerd (handleiding) | Eenvoudige rangschikking waarbij bedrijfsregels het belang van een aanbieding bepalen | Elk aanbod krijgt een prioriteitsscore; de hoogste prioriteit wint; deterministisch en gemakkelijk te begrijpen |
| Op basis van formule (aangepaste expressie) | De classificatie zou in profielattributen (bijvoorbeeld, CLV, rij, affiniteitscore) moeten omvatten | De aangepaste rangschikkingsformule evalueert profielcontext; dynamischer dan prioriteit; geen vereiste ML |
| Op AI-schaal (automatische optimalisatie) | De rangschikking moet automatisch worden geoptimaliseerd op basis van historische conversiegegevens | Het AI-model leert van conversiegebeurtenissen; vereist minimaal 1.000 gebeurtenissen voor training; verbetert voortdurend |

#### Beslissing: aanbod afstemmen

Moeten er beperkingen gelden voor het aantal keren dat een aanbieding wordt getoond?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Per profiel | Voorkomen dat hetzelfde aanbod herhaaldelijk wordt weergegeven in hetzelfde profiel | Beschermt tegen moeheid bij het aanbieden; tegengaan mogelijk onder hoge productie |
| Globale lampvoet | Totaal aantal afbeeldingen beperken voor alle profielen (bijvoorbeeld beperkte voorraadpromoties) | Bepaalt de totale blootstelling; nuttig voor aanbiedingen met een beperkt aanbod |
| Geen uiteinde | Elke in aanmerking komende indruk moet het aanbod weergeven | Eenvoudigst; geschikt voor groene inhoud of onbeperkte aanbiedingen |

#### Belangrijkste configuratiedetails

**navigatie UI:** Componenten > Beslissingsbeheer > Plaatsingen/Aanbiedingen/Besluiten

- Plaatsen maken voor elke combinatie van kanaal en inhoudstype (bijvoorbeeld HTML-banner via e-mail, JSON via push, SMS)
- Bepaal geschiktheidsregels gebruikend de uitdrukkingen van de segmentregel die van profielattributen of publiek lidmaatschap van verwijzingen voorzien
- Maak persoonlijke aanbiedingen met weergaven voor elke plaatsing, wijs subsidiabiliteitsregels toe en stel prioriteit in
- Maak een fallback-aanbieding voor alle plaatsingen. Deze wordt geretourneerd wanneer geen gepersonaliseerd aanbod in aanmerking komt
- Aanbiedingen in verzamelingen indelen met behulp van verzamelingsaanduidingen (tags)
- Rangschikkingsstrategie configureren — op prioriteit gebaseerd, op formule gebaseerd of op AI-positie gerangschikt
- Beslissingsbeleid maken dat plaatsingen, verzamelingen, classificatiestrategie en fallback-aanbieding bindt
- Alle aanbiedingen goedkeuren voordat ze door middel van een beslissing kunnen worden geselecteerd

#### Waar opties afwijken

**voor Optie A (Offer Decisioning):**
Maak plaatsingen en aanbiedingen die zijn toegespitst op de personalisatie van inhoud binnen elk kanaal (bijvoorbeeld een banneraanbieding voor een e-mailhoofdtelefoon, een aanbieding voor een e-mailvoettekst, een aanbieding voor een pushmelding). Bij Beslissingsbeleid wordt de beste inhoud voor elke plaatsing in het bericht geselecteerd.

**voor Optie B (Dynamische Selectie van het Kanaal):**
Maak beslissingsitems die elk kanaal vertegenwoordigen. De kwalificatieregels omvatten toestemmingscontroles (bijvoorbeeld een profiel moet SMS-toestemming hebben om in aanmerking te komen voor het SMS-item). De rangschikking gebruikt kanaal betrokkenheidsscores of op formule-gebaseerde uitdrukkingen.

**voor Optie C (Volledige Aangepast):**
Configureer twee beslissingslagen: één set besluitvormingsbeleid voor kanaalselectie en een aparte set voor selectie van inhoud/aanbod binnen het geselecteerde kanaal. Beide lagen vereisen plaatsing, aanbiedingen, toelatingsregels, en rangschikkingsstrategieën.

#### Experience League-documentatie

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Plaatsingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Beslissingsregels maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Alternatieve aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Verzamelingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 4: Berichtontwerp

**functie van de Toepassing:** [!DNL AJO]: Het Authoring van het bericht

Deze fase vormt berichtinhoud voor elk kanaal en touchpoint in de reis, die beslissingsoutput (geselecteerde aanbiedingsinhoud) in de berichtmalplaatjes integreren. Elk knooppunt voor berichtactie in de reis vereist geschreven inhoud met het juiste kanaaloppervlak, personalisatietokens en biedt plaatsingsintegratie.

#### Besluit: Inhoudsaanpak

Hoe zou de berichtinhoud voor elk kanaal moeten worden gecreeerd?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Op een sjabloon gebaseerd | De organisatie heeft merkmalplaatjes gevestigd; consistentie is belangrijk | Sneller ontwerpen; zorgt voor consistentie tussen merken; kan ontwerpflexibiliteit beperken |
| Ontwerpen vanaf nul | Uniek creatief voor deze reis; geen bestaande malplaatjes | Volledig ontwerpbeheer; langere ontwerptijd; gebruik E-mail Designer slepen en neerzetten |
| HTML importeren | Creative-team produceert HTML extern; importeren naar [!DNL AJO] | Behoudt externe ontwerpworkflow; vereist HTML-compatibiliteit met e-mail Designer |

#### Besluit: toepassingsgebied Personalization

Welk niveau van verpersoonlijking zou berichten voorbij beslissingsoutput moeten omvatten?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Basisverpersoonlijking (naam, begroeting) | Minimale vereisten voor personalisatie die verder gaan dan selectie | Eenvoudige Handlebars-expressies; lage complexiteit |
| Voorwaardelijke inhoudsblokken | Verschillende inhoudssecties voor verschillende segmenten of kenmerken | Gebruikt dynamische inhoudsregels; inhoud varieert per profielkenmerk of segmentlidmaatschap |
| Volledige personalisering met beslissingsintegratie | Plaatsen van de aanbieding ingebed in bericht, gecombineerd met op profiel-gebaseerde verpersoonlijking | Combineert beslissingsuitvoer met Handlebars personalisatie tokens; rijkste ervaring |

#### Belangrijkste configuratiedetails

**navigatie UI:** Uitgezochte campagne of reisactie > geef inhoud uit > E-mail Designer / de redacteur van het Kanaal

- Inhoud van het auteurbericht voor elk kanaal dat in de reis (e-mail, SMS, duw, in-app) wordt gebruikt
- Plaats beslissingsstappen voor aanbiedingen in de berichtinhoud waarin de gekozen aanbiedingen moeten worden weergegeven
- Voeg personalisatie-expressies toe met de syntaxis Handlebars voor profielkenmerken (bijvoorbeeld `{{profile.person.name.firstName}}`)
- Vorm voorwaardelijke inhoudsblokken voor segment-specifiek overseinen
- Herbruikbare inhoudsfragmenten maken voor gedeelde elementen (kop- en voetteksten, juridische disclaimers)
- Voorvertonen en testen met voorbeeldprofielen om te controleren of de weergave op de juiste wijze is aangepast
- Proofingberichten verzenden voor revisie door belanghebbenden

#### Waar opties afwijken

**voor Optie A (Offer Decisioning):**
Elk bericht bevat aanbiedingsplaatsen waar door een beslissing geselecteerde inhoud wordt weergegeven. De berichtlay-out is verenigbaar, maar het aanbiedingsgebied toont dynamisch de beste aanbieding voor elk profiel.

**voor Optie B (Dynamische Selectie van het Kanaal):**
Elk kanaal heeft zijn eigen berichtinhoud die afzonderlijk wordt geschreven. Inhoud is vergelijkbaar tussen kanalen, maar is aangepast aan kanaalbeperkingen (HTML-mailadres versus SMS-tekst vs. notatie voor pushmeldingen).

**voor Optie C (Volledige Aangepast):**
Elk kanaal heeft zijn eigen berichtinhoud met ingebedde aanbiedingsplaatsen. Zowel worden het kanaal als de aanbiedingsinhoud binnen dat kanaal dynamisch geselecteerd.

#### Experience League-documentatie

- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Een SMS-bericht maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Een pushmelding ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Fase 5: Reisontwerp en activering

**functie van de Toepassing:** [!DNL AJO]: Journey Orchestration, [!DNL AJO]: Conflict &amp; Prioritair Beheer, [!DNL AJO]: Frequentie &amp; Bedrijfs Regels

Deze fase vormt het volledige wegcanvas met inbegrip van ingangsconfiguratie, besluitvormingsknopen verbonden aan gevormd besluitvormingsbeleid, voorwaardenspleten voor kanaal verpletterend (Opties B/C), de knopen van de berichtactie voor elk kanaalweg, wachtknopen tussen touchpoints, uitgangscriteria, conflict/prioritaire montages, en de regels van de frequentiecontrole. Deze fase assembleert alle eerder gevormde componenten in de georkestreerde reisstroom en activeert het.

#### Besluit: Hertoelatingsbeleid

Kunnen profielen de reis na voltooiing of het verlaten opnieuw ingaan?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Opnieuw openen toestaan (met afkoelingsmethode) | Terugkerende reizen waarbij profielen opnieuw in aanmerking komen (bijvoorbeeld verlenging van de driemaandelijkse loyaliteit) | Stel een afkoelingsperiode in (minimaal 5 minuten) om te voorkomen dat het document onmiddellijk opnieuw wordt binnengegaan; het profiel wordt opnieuw gestart vanaf het begin |
| Geen nieuwe toegang | Eenmalige ritten waarbij elk profiel slechts eenmaal mag reizen (bijvoorbeeld onboarding) | Profiel kan niet opnieuw worden ingevoerd na voltooiing of uitgang; eenvoudiger gedrag |

#### Besluit: Afsluitingscriteria

Onder welke voorwaarden moet een profiel van de reis worden verwijderd voordat het wordt voltooid?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Wijziging van het lidmaatschap voor het publiek | Profiel moet worden afgesloten wanneer het ingangspubliek wordt verlaten of een onderdrukkend publiek wordt geopend | Real-time exit op segmentwijziging; handig voor &#39;omgezette&#39; of &#39;opted out&#39; afsluiten |
| Gebeurtenis | Een specifieke gebeurtenis (bijvoorbeeld aankoop, afmelden) moet het afsluiten activeren | Real-time exit on event; vereist configuratie van gebeurtenisschema |
| Time-out | Maximumduur van de reis is verstreken | De standaard max. is 91 dagen. Hiermee voorkomt u dat profielen oneindig blijven |

#### Besluit: time-out reis

Wat is de maximale duur die een profiel in de reis kan blijven?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| 91 dagen (maximaal) | Langlopende levenscyclusritten met uitgebreide opvoedkundige reeksen | Maximaal toegestane duur; profielen worden na 91 dagen afgesloten, ongeacht |
| Aangepaste kortere duur | Tijdgebonden campagnes of seizoensreizen | Instellen op basis van logica voor het zakendoen van reizen; kortere time-out verlaagt profielen voor eindgebruikers |

#### Besluit: Conflict en prioritaire instellingen

Moet deze reis voorrang hebben bij het zoeken naar oplossingen voor conflicten met andere reizen/campagnes?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Hoge prioriteit (70-100) | Kritieke klantritten (behoud, loyaliteit) die voorrang zouden moeten hebben | Hogere prioriteit wint wanneer de veelvoudige mededelingen concurreren; gebruik spaarzaam |
| Prioriteit Medium (30-69) | Standaardlevenscyclusreizen | Evenwichtige prioriteit; kan onderdrukt worden door communicatie met hogere prioriteit |
| Lage prioriteit (0-29) | Aanvullende of informatieve reizen | Wordt onderdrukt wanneer wordt geconcurreerd met belangrijker communicaties |

#### Belangrijkste configuratiedetails

**navigatie UI:** de Reizen > creëren Reis

- Maak de reis en configureer eigenschappen (naam, beschrijving, tijdzone, timeout)
- Item configureren: publiek lezen (voor batch) of gebeurtenistrigger (voor realtime)
- Beslissingsknooppunten toevoegen die zijn gekoppeld aan geconfigureerd beslissingsbeleid uit fase 3
- Voorwaarde-splitsingen toevoegen voor kanaalroutering op basis van beslissingsuitvoer of profielkenmerken (Opties B/C)
- Voeg de knooppunten van de berichtactie voor elk kanaalweg toe, die met de geschreven inhoud van Fase 4 verbinden
- Wachten-nodes toevoegen tussen aanraakpunten (minimaal 1 uur voor reizen die door het publiek worden gelezen)
- Afsluitcriteria definiëren (wijziging van het publiek, gebeurtenis, time-out)
- Prioriteitsscore toewijzen voor conflictoplossing
- Vaststellen van frequentiegrenzen als de grenzen van de dwars-reisfrequentie van toepassing zijn
- Test de reis in testmodus met testprofielen voordat u publiceert
- De reis publiceren om deze live te maken

#### Waar opties afwijken

**voor Optie A (Offer Decisioning):**
Het reiscanvas is lineair met besluitvormingsbeleid ingebed in elk knooppunt van de berichtactie. Geen vertakking voor kanaalselectie. Het aanbodbesluit wordt gemaakt bij bericht geeft tijd binnen de actieknooppunt terug.

**voor Optie B (Dynamische Selectie van het Kanaal):**
Na elke wachttijdstap voegt u een voorwaardenknooppunt toe dat de criteria voor kanaalselectie evalueert (profielkenmerken, beslissingsuitvoer of toestemmingsstatus). Elke voorwaardestak leidt tot een kanaal-specifieke knoop van de berichtactie. Een standaardpad/ander pad opnemen voor profielen die niet overeenkomen met een voorwaarde.

**voor Optie C (Volledige Aangepast):**
Combineer knooppunten van de kanaalselectie met de actieknooppunten van het via beleidsregels ingesloten bericht. Op elk aanraakpunt: eerst bepaalt een voorwaarde of een beslissing het kanaal en vervolgens selecteert een beslissingsbeleid binnen de berichtactie van het geselecteerde kanaal de optimale aanbieding/inhoud.

#### Experience League-documentatie

- [Een reis maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journeyeigenschappen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Lees de publieksactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Voorwaardeactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wachtactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Een bericht toevoegen tijdens een rit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Afsluitingscriteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Reisbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Uw reis testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [De reis publiceren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Overzicht van conflicten en prioritair beheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Fase 6: Rapportage en toezicht

**functie van de Toepassing:** [!DNL AJO]: Rapportering &amp; de Analyse van Prestaties

Deze fase vormt reis en beslissingsprestatie controle door levende rapporten (tijdens uitvoering) en historische rapporten (na voltooiing). Beslissingsspecifieke metriek met inbegrip van de aanbiedingsselectiedistributie, terugvaltarieven, en rangschikkingsdoeltreffendheid. Optioneel, CJA-werkruimteanalyse voor een analyse van het investeringsrendement voor een grote afstand tussen kanalen en beslissingen.

#### Besluit: rapportagediepte

Welk niveau van rapporteringsanalyse is nodig?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| [!DNL AJO] alleen native rapporten | Operationeel toezicht op de gegevens over levering en betrokkenheid | Ingebouwde live en historische rapporten; geen aanvullende configuratie; beperkt tot [!DNL AJO] metriek |
| [!DNL AJO] + CJA-analyse | Diepe kanaalanalyse, effectiviteit van besluitvorming, ROI van de reis, cohortanalyse | Vereist CJA-verbinding en gegevensweergave; biedt mogelijkheden voor attributie, funnel en cohortanalyse |

#### Belangrijkste configuratiedetails

**navigatie UI:** de Reizen > Uitgezochte reis > Levend rapport/Al tijdrapport

- Live-rapport van de reis bijhouden tijdens de eerste uitvoering voor metingen van entry, exit en per node
- Beslissingsprestaties controleren: selectiedistributie aanbieden, reserveringspercentage, rangschikkingseffectiviteit
- Na voltooiing van de reis, herzie historische rapporten voor de analyse van begin tot eind funnel
- Voor CJA-analyse: controleer of CJA-verbinding [!DNL AJO] -gegevenssets bevat (Berichtfeedbackgebeurtenis, e-mailvolggebeurtenis)
- CJA-werkruimte maken met deelvensters voor kanaalmixanalyse, prestaties vergelijken en trajectconversietrechter
- Annotaties maken voor startdatums en belangrijke configuratiewijzigingen

#### Experience League-documentatie

- [Journaal live](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementatieoverwegingen

Bekijk de volgende richtlijnen, gemeenschappelijke valkuilen, beste praktijken, en handelsbesluiten vóór en tijdens implementatie.

### Guardrails en limieten

- Maximum van 500 levende reizen per zandbak — [&#x200B; de guardrails van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- De maximale reisduur is 91 dagen (globale time-out)
- Maximaal 50 activiteiten per reiscanvas
- Voor ritten voor leespubliek kunt u maximaal 20.000 profielen per seconde verwerken
- Dagelijkse ritten voor gebeurtenissen ondersteunen maximaal 5.000 gebeurtenissen per seconde per sandbox.
- Maximaal 10.000 goedgekeurde persoonlijke aanbiedingen per sandbox
- Maximaal 30 stages per besluit
- De reactietijd van de levering SLA van de aanbieding: minder dan 500 ms bij P95 voor single-scope verzoeken
- Voor AI-classificatiemodellen is een minimum van 1.000 conversieevenementen vereist voor training
- Maximaal 10 kanaaloppervlakken per kanaaltype per sandbox
- Wacht stappen een minimumduur van 1 uur voor publiek-gelezen reizen hebben
- Terugkoop van de reis is minimaal 5 minuten
- Maximum van 4.000 segmentdefinities per zandbak - [&#x200B; de gidsen van het Platform &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Veelvoorkomende valkuilen

**het Besluit keert altijd terugvalkenaanbod terug:** verifieer dat de gepersonaliseerde aanbiedingen (niet in ontwerpstaat), binnen hun waaier van de geldigheidsdatum worden goedgekeurd, en dat de geschiktheidsregels de attributen van de doelprofielen aanpassen. Controleer of er geen plafondlimiet is bereikt. Testen met een profiel dat duidelijk in aanmerking moet komen voor een gepersonaliseerd aanbod.

**de Reis publiceert maar de profielen gaan niet in:** voor publiek-gelezen reizen, bevestig het publiek een geëvalueerde bevolking groter dan nul heeft. Voor gebeurtenis-teweeggebrachte reizen, verifieer het gebeurtenisschema, die voorwaarden teweegbrengen, en dat de gebeurtenissen worden verzonden. Controleer dat het beleid van de de samenvoeging van het ingangspubliek het verwachte samenvoegingsbeleid van de reis aanpast.

**het Rangschikken formule wordt niet correct toegepast:** verifieer de formulesyntaxis geldig en verwijzingen toegankelijke profielattributen. Formulatiefouten vallen zonder waarschuwing weer terug op een rangschikking op basis van prioriteit. De rangschikking van de test met profielen die verschillende attributenwaarden hebben om de formule te bevestigen veroorzaakt de verwachte orde.

**het verpletteren van het Kanaal negeert toestemming:** de knopen van de Voorwaarde voor kanaalselectie moeten toestemmingscontroles omvatten. Een profiel zonder SMS-toestemming mag niet naar het SMS-pad worden geleid. Concept instemming in subsidiabiliteitsregels opbouwen bij het gebruik van besluiten voor kanaalselectie (optie B/C).

**Aanbieding die tellers aftappen onder hoge productie aanbiedt:** Aanbieding die tellers aftappen kan een vertraging van een paar seconden in high-productiescenario&#39;s hebben. Als de nauwkeurige aftappen kritiek is, gebruik globale maximumgrenzen met een buffer of combinatie met frequentieregels.

**het canvas van de Reis overschrijdt 50 activiteitengrens:** De complexe reizen van Optie C met vele kanaaltakken en beslissingsknopen kunnen de 50 activiteitengrens benaderen. Vereenvoudigen door voorwaardenlogica te consolideren, het aantal aanraakpunten te verminderen of in meerdere opeenvolgende reizen te splitsen.

**de besluiten van Edge keren lege verpersoonlijking terug:** als het gebruiken van randbesluit voor besluiten in real time, zorg ervoor de datastream de [!DNL Adobe Journey Optimizer] toegelaten dienst heeft en dat het besluitwerkingsgebied correct geformatteerd is. Edge-beslissingen zijn beperkt tot profielkenmerken die beschikbaar zijn in het archief met randprofielen.

### Aanbevolen procedures

**Begin eenvoudig en evolueer:** Begin met Optie A (vast kanaal, dynamische aanbiedingen) om het besluitvormingskader te bevestigen, dan evolueer aan Opties B of C aangezien uw gegevensrijpheid en organisatorische capaciteitsverhoging.

**investeer in profielverrijking:** De gegevens verwerkte attributen zoals betrokkenheidsscores, de indexen van de kanaalvoorkeur, en de de bezitsscores van AI van de Klant verbeteren dramatisch beslissingskwaliteit. Bouw deze verrijkingsattributen alvorens complexe rangschikkingsstrategieën te vormen.

**vormt altijd terugvalaanbiedingen:** Elk besluitvormingsbeleid moet een terugvalaanbieding hebben. De reserve van het ontwerp biedt als echt waardevolle inhoud (niet lege placeholders) aan aangezien zij profielen dienen die niet voor om het even welke gepersonaliseerde aanbieding kwalificeren.

**Test met diverse profielen:** de testwijze van het Gebruik met profielen die verschillende geschiktheidswegen, kanaalvoorkeur, en attributencombinaties vertegenwoordigen. Controleer of elk mogelijk reispad en beslissingsresultaat correct werkt voordat u het publiceert.

**de fallback van de Monitor tarieven als gezondheid metrisch:** een hoog tarief van de fallback van aanbiedt wijst erop dat de geschiktheidsregels te restrictief zijn of de aanbiedingscatalogus behandelt genoeg profielsegmenten niet. Richt een reserve tarief onder 20% voor goed-gevormde besluitvorming.

**de inhoudsfragmenten van het Gebruik voor dwars-kanaalconsistentie:** creeer gedeelde inhoudsfragmenten (kopballen, footers, wettelijke disclaimers, unsubscribe blokken) om merkconsistentie over e-mail, SMS, en duwberichten binnen de reis te handhaven.

**vorm pro-actief uitgangscriteria:** bepaal uitgangscriteria voor omzettingsgebeurtenissen (bijvoorbeeld, aankoop, registratie) zodat de profielen die de gewenste actie voltooien van de reis onmiddellijk worden verwijderd eerder dan het blijven berichten ontvangen.

**wijs zinvolle prioritaire scores toe:** wanneer het runnen van veelvoudige reizen en campagnes, wijs prioritaire scores toe die op bedrijfseffect worden gebaseerd. Reisreizen met hoge waarde voor het bewaren van gegevens moeten een hogere prioriteit hebben dan informatieve communicatie.

### Handelsbesluiten

Controleer de volgende compromissen om uw implementatiekeuzen te informeren.

#### Beslissende ingewikkeldheid tegenover tijd aan markt

De verfijndere besluitvorming (Optie C met AI rangschikking) levert hogere verpersoonlijking maar vereist beduidend meer configuratie, gegevensvoorbereiding, en testtijd.

- **Optie A/B komt voor:** Snellere plaatsing, eenvoudiger het testen, lagere aan de gang zijnde beheersoverheadkosten
- **Optie C gunt:** Maximale verpersoonlijking, ononderbroken AI-gedreven optimalisering, hoogste betrokkenheidspotentieel
- **Aanbeveling:** Begin met Optie A of B voor aanvankelijke lancering. Prestatiegegevens verzamelen en kenmerken voor profielverrijking parallel opbouwen. Ga naar optie C als u minstens 1.000 conversiegebeurtenissen voor AI rangschikking training en een goed gevulde aanbiedingencatalogus hebt.

#### Statische vertakking versus beslissing voor kanaalselectie

De kanaalselectie kan worden uitgevoerd via eenvoudige knooppunten voor de reisconditie (de beoordeling van profielkenmerken rechtstreeks) of via het beslissingskader (waarbij kanalen worden gemodelleerd als beslissingsitems met geschiktheid en rangorde).

- **de statische voorwaardenknopen gunnen:** Eenvoud, transparantie, gemakkelijke het oplossen van problemen. Best wanneer de logica voor kanaalselectie eenvoudig is (bijvoorbeeld: &quot;Als het pushtoken bestaat en de laatste push binnen 30 dagen is geopend, gebruikt u push; anders e-mail&quot;).
- **op besluit-Gebaseerde kanaalselectie gunst:** Gecentraliseerd beheer, AI optimalisatiepotentieel, capaciteit om rangschikkende logica te evolueren zonder het wegcanvas te wijzigen. Dit is het meest geschikt wanneer de kanaalselectie complex is en na verloop van tijd moet verbeteren.
- **Aanbeveling:** de statische voorwaardenknopen van het gebruik voor Optie B wanneer de criteria van de kanaalselectie eenvoudig en duidelijk zijn. Gebruik op beslissingen gebaseerde kanaalselectie als u wilt dat AI de kanaalselectie optimaliseert in de loop van de tijd of als de logica voor kanaalselectie complex genoeg is om te profiteren van gecentraliseerd geschiktheids- en classificatiebeheer.

#### Korreligheid ten opzichte van beheerbaarheid van catalogus

Een grote, granulaire aanbiedingencatalogus met veel gerichte aanbiedingen levert een preciezere personalisatie op, maar vereist meer beheerinspanningen. Een kleinere catalogus met een bredere geschiktheid is eenvoudiger te beheren, maar is minder gepersonaliseerd.

- **Grote catalogus (vele specifieke aanbiedingen) gunt:** Hogere verpersoonlijkingsprecisie, relevantere selecties voor diverse soorten publiek, lagere terugvaltarieven
- **Kleine catalogus (minder brede aanbiedingen) gunt:** Eenvoudiger beheer, snellere opstelling, eenvoudiger het testen, lager risico van verweesde aanbiedingen
- **Aanbeveling:** Begin met 5-15 gepersonaliseerde aanbiedingen plus een reserve per besluit. Voeg meer aanbiedingen toe terwijl u observeert welke segmenten het vaakst fallback-aanbiedingen ontvangen. Gebruik verzamelingsaanduidingen om aanbiedingen per categorie, laag of productlijn te ordenen voor beheerbare groei.

#### Op prioriteit gebaseerde versus op AI gerangschikte besluiten

Op prioriteit gebaseerde rangorde is deterministisch en transparant. Beslissing op basis van AI-waarden wordt automatisch geoptimaliseerd, maar vereist trainingsgegevens en is minder transparant.

- **op prioriteit-gebaseerde rangschikking gunst:** Voorspelbaarheid, transparantie, directe plaatsing, geen vereiste van opleidingsgegevens
- **AI-gerangschikte besluiten begunstigt:** Ononderbroken optimalisering, gegeven-gedreven selectie, capaciteit om niet voor de hand liggende aanbieding-profiel affiniteiten te ontdekken
- **Aanbeveling:** Op prioriteit-gebaseerde of op formule-gebaseerde rangschikking van het gebruik voor aanvankelijke plaatsing. De overgang aan op AI-Rangschikking zodra u minstens 1.000 omzettingsgebeurtenissen hebt geaccumuleerd en van op regel-gebaseerd aan model-gebaseerde optimalisering wilt bewegen.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie over de mogelijkheden die in dit gebruikspatroon worden gebruikt.

### Reisorkest

- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Een reis maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journeyeigenschappen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Lees de publieksactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Algemene gebeurtenissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [kwalificatiegebeurtenissen voor het publiek](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Voorwaardeactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wachtactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Een bericht toevoegen tijdens een rit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Afsluitingscriteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Reisbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Uw reis testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [De reis publiceren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Beslissingsbeheer

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Plaatsingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Beslissingsregels maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Alternatieve aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Verzamelingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Verzamelingsaanduidingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Kanaalconfiguratie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [IP-pools maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-opwarmingsplannen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Instellingen van e-mailoppervlak](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Authoring en personalisatie van berichten

- [Een e-mail maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Conflict-, prioriteit- en frequentiebeheer

- [Overzicht van conflicten en prioritair beheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Mogelijke conflicten identificeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Afbakening van reizen en arbitrage](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)

### Splitsen en segmenteren

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Samenstelling publiek](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Rapportage en analyse

- [Journaal live](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Profiel en identiteit

- [Overzicht van het realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [AI-overzicht van klant](https://experienceleague.adobe.com/nl/docs/experience-platform/intelligent-services/customer-ai/overview)

### Beheer van gegevens en toestemming

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Toestemming in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Onderdrukkingslijst beheren](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Beveiligingsmechanismen

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identiteitsservicehandleidingen](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
