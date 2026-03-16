---
title: Meerdere stappen geordende reis
description: Leer hoe u een profiel begeleidt door een vertakkende multitouch-reis met wachttijden, voorwaarden en meerdere berichtacties in de loop van de tijd.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '8173'
ht-degree: 0%

---


# Reis met meerdere stappen georkestreerd

Deze handleiding bevat een uitgebreide implementatieblauwdruk voor het bouwen van meerstapse georkestreerde reizen met [!DNL Adobe Journey Optimizer] (AJO) en [!DNL Real-Time Customer Data Platform] (RT-CDP). Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die vertakkende, multi-touch klantritten moeten organiseren die in de loop der tijd meerdere berichten leveren.

Alle uitvoerbare implementatieopties, beslissingsoverwegingen op elk configuratiepunt en koppelingen naar [!DNL Adobe Experience League] -documentatie worden weergegeven. Gebruik deze gids om uw multi-step reisimplementatie te plannen, te vormen en te bevestigen.

## Hoofdlettergebruik

De in meerdere stappen georkestreerde reizen richten bedrijfsscenario&#39;s waar één enkel bericht ontoereikend is om het gewenste klantenresultaat te bereiken. In plaats van een eenmalige verzending begeleidt de reis elk profiel door een reeks aanraakpunten (e-mails, SMS-berichten, pushmeldingen of in-app berichten) die zich over dagen of weken uitstrekken, met vertakkende logica die het pad aanpast op basis van profielkenmerken, gedragssignalen of gebeurtenisgegevens.

Deze reizen zijn het meest complexe campagnepatroon in AJO. Zij combineren op publiek-gebaseerde of op gebeurtenis-gebaseerde ingang met een canvas van actieknooppunten (berichten), voorwaardenknopen (vertakkende logica), wachtknopen (tijdvertragingen), en uitgangscriteria (omzettingsgebeurtenissen of onderbrekingen). Elk profiel doorloopt de reis onafhankelijk, in hun eigen tempo, en ontvangt bij elke stap contextueel relevante inhoud.

Dit patroon subsumes de eenvoudigere patronen — partij uitgaande berichtactivering voor single-send campagnes en gebeurtenis-teweeggebracht overseinen voor single-event reacties. Gebruik dit patroon wanneer de gebruikscase vereist dat een profiel door meerdere interacties in de loop van de tijd wordt verzorgd.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

### Bewaren van klanten verbeteren

Bestaande klanten betrokken houden en vernieuwen door waardegestuurde ervaringen en doorlopende relatieverpleging.

**KPIs:** Behoud, de Waarde van het Leven van de Klant, Betrokkenheid

[Meer informatie over het verbeteren van klantenbehoud](/help/blueprints/business-objectives/customer-experience/improve-customer-retention.md)

### Klant beter instappen

Versnel tijd-aan-waarde voor nieuwe klanten met gestroomlijnde, gepersonaliseerde welkom ervaringen en activeringsreizen.

**KPIs:** Betrokkenheid, Behoud, Tarieven van de Omzetting

[Meer informatie over het verbeteren van de instapbaarheid van klanten](/help/blueprints/business-objectives/customer-experience/improve-customer-onboarding.md)

### Neem slapende klanten opnieuw aan

Win terug inactieve of verlopende klanten met gerichte reactiveringscampagnes die op gedragssignalen worden gebaseerd.

**KPIs:** Betrokkenheid, Behoud, Tarieven van de Omzetting

### Afgelopen wagens en reizen terughalen

Neem gebruikers opnieuw op die tijdens aankoop, toepassing, of inschrijvingsstromen met geschikte, gepersonaliseerde follow-ups zijn weggevallen.

**KPIs:** de Tarieven van de Omzetting, Incrementele Inkomsten, Betrokkenheid

[Meer informatie over het herstellen van verlaten wagens en reizen](/help/blueprints/business-objectives/customer-experience/recover-abandoned-carts-journeys.md)

## Voorbeelden van tactische gebruiksgevallen

De volgende scenario&#39;s illustreren gemeenschappelijke toepassingen van het multi-step georkestreerde reispatroon.

- **Klant op het instappen reeksen** — Welkome e-mail, gevolgd door eigenschaponderwijs, dan een activeringsherinnering over de eerste 14 dagen na registratie
- **de druppelcampagne van de re-overeenkomst** — Een herinnering e-mail, toen een aansporingsaanbieding, toen een definitieve bericht voor vervallen klanten over 3 weken
- **Loyalty milestone reis** — De verbeteringsbericht van de rij, die door een exclusieve aanbieding wordt gevolgd, toen een herroepingsherinnering aangezien de lidmaatschapsherdenking nadert
- **Win-back opeenvolging** — &quot;wij missen u&quot;e-mail, toen een kortingsaanbieding via e-mail, toen een definitieve herinnering van SMS voor vervallen kopers
- **de adoptietraject van het Product** — De proef verwelkomde, gebruiksuiteinden, dan een verbeteringsherinnering aangezien de proefperiode vordert
- **de vernieuwingsopeenvolging van het Abonnement** - bericht van 30 dagen, herinnering van 7 dagen, toen een verval-dag bericht voor de aanstaande abonnementsvernieuwingen
- **Postpurchase nurture** — Dank-u e-mail, hoe-aan-gebruiks gids, dwars-verkoop aanbeveling, toen een overzichtsverzoek meer dan 30 dagen na aankoop

## Kernprestatie-indicatoren

Gebruik de volgende KPIs om de doeltreffendheid van uw multi-stap georkestreerde reis implementatie te meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Voltooiingssnelheid reis | Percentage profielen dat de volledige reis zonder vroege uitgang voltooit | Reisrapport: Verlaat (voltooid) / Ingegaan |
| Omzetsnelheid stap | Percentage profielen dat van de ene stap naar de volgende gaat | Metriek per knoop in het reisrapport |
| Betrokkenheid kanaal | Open snelheden, doorkliksnelheden en responspercentages op elk aanraakpunt | Metrische gegevens voor levering en betrokkenheid per bericht |
| Omzetsnelheid criteria afsluiten | Percentage profielen dat de gebeurtenis exit (bijvoorbeeld aankoop, aanmelden) activeert vóór time-out van de reis | Aantal treffers voor afsluitcriteria / Totaal ingevoerd |
| Tijd voor conversie | Gemiddelde duur vanaf het moment van binnenkomst op het traject tot aan het einde van de rit volgens criteria | Reisanalyse: tijdstempel van item naar conversietijdstempel |
| Afgiftekoers reis | Percentage profielen dat bij elke stap stopt met activeren (valanalyse) | CJA-fallout visualiseren over stappen |
| Behoud/percentage voor opnieuw aangaan | Percentage doelprofielen dat terugkeert naar de actieve status | Analyse van gedragingen na de reis in CJA |

## Hoofdletterpatroon gebruiken

**Multi-Step Orchestrated Reis**

Een profiel door een vertakkende multitouch-reis begeleiden met wachttijden, voorwaarden en meerdere berichtacties in de loop van de tijd.

**de ketting van de Functie:** de Evaluatie van het publiek > Uitvoering van de Reis (multi-knoop) > Vertakking van de Voorwaarde > de Aflevering van het Bericht (xN) > Criteria van de Uitgang > het Melden

## Applicaties

De volgende toepassingen worden gebruikt om dit gebruiks gevalpatroon uit te voeren.

- **[!DNL Adobe Journey Optimizer] (AJO)** — De motor van de Orchestratie van de reis, bericht creatie, kanaalconfiguratie, inhoud experimenteren, frequentie en conflictbeheer, en rapportering
- **[!DNL Adobe Real-Time Customer Data Platform] (rt-CDP)** — de evaluatie en de definitie van het publiek van het publiek van het publiek van de reisingang, profielgegevens voor verpersoonlijking en voorwaarde het vertakken
- **[!DNL Adobe Experience Platform] (AEP)** — De opslag van het profiel, de identiteitsdienst, de invoer van gebeurtenisgegevens, en de infrastructuur van stichtingsgegevens

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | AJO-sandbox met bevoegdheden voor het maken en publiceren van reizen. Kanaaloppervlakken voor alle kanalen die tijdens de reis worden gebruikt, moeten worden geconfigureerd. De gebruikers moeten de aangewezen rollen (Marketer, de Manager van de Reis) met reis en campagnetoestemmingen hebben. | [&#x200B; het overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [&#x200B; overzicht van de Toegangscontrole &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | XDM-profielschema met kenmerken die worden gebruikt voor vertakking en personalisatie van voorwaarden in meerdere berichten (bijvoorbeeld een loyaliteitsniveau, de interesse van het product, de betrokkenheidsscore). Ervaar de schema&#39;s van de Gebeurtenis voor omzettingsgebeurtenissen die uitgangscriteria en voorwaardevaluatie drijven (bijvoorbeeld, aankoopgebeurtenissen, vormverklaringen). | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [&#x200B; de samenstellingsgrondbeginselen van het Schema &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Gegevensbronnen en -verzameling | Verondersteld op plaats | Gebeurtenisstreaming moet actief zijn als de afsluitcriteria of -voorwaarden afhankelijk zijn van realtime-gebeurtenissen (bijvoorbeeld koopgebeurtenis om de reis af te sluiten). Batchopname voor profielkenmerken die worden gebruikt in vertakking. Web SDK of server-side API voor gedragsgebeurtenisinzameling. | [&#x200B; het stromen ingegaan overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview), [&#x200B; Bronoverzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identiteit en profielconfiguratie | Verondersteld op plaats | Profielen moeten kunnen worden opgelost in alle kanalen die tijdens de reis worden gebruikt (e-mail, SMS, push). Identiteit tussen apparaten moet worden gevormd als de reis Web en mobiele aanraakpunten overspant. Het samenvoegingsbeleid moet zijn geconfigureerd voor de sandbox. | [&#x200B; overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [&#x200B; overzicht van het beleid van de Fusie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Auditiedefinitie en segmentatie | Vereist | Toegangspubliek moet worden gedefinieerd voor reizen die door het publiek worden gelezen. Segmenten kunnen ook worden gebruikt in voorwaardenknooppunten voor vertakking. De evaluatiemethode (batch of streaming) moet overeenkomen met de vereisten voor het invoeren van de reis. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [&#x200B; de gids UI van de Bouwer van het Segment &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Berekende kenmerken zoals betrokkenheidsscores, dagen sinds laatste activiteit of waarde van levenslange aanschaf verbeteren de vertakkende logica voor voorwaarden en maken intelligentere beslissingen over reispaden mogelijk. | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Het bewaren van de gebeurtenisgegevens van de reis zou met het beleid van de gegevensset vervaldatum moeten worden gevormd om opslag te beheren en aan de verordeningen van het gegevensbehoud te voldoen. De handhaving van de toestemming verzekert slechts opted-binnen profielen berichten bij elk kanaal touchpoint ontvangen. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [&#x200B; Verlopen Dataset &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | De etiketten van de governance verzekeren volgzame verpersoonlijking over veelvoudige berichten touchpoints, vooral belangrijk wanneer de reizen PII of gevoelige gegevens voor verpersoonlijking over kanalen gebruiken. | [&#x200B; het beheer van Gegevens overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [&#x200B; overzicht van de gebruiksetiketten van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Bewaking en waarneming | Opgenomen | De controle van de uitvoering van de reis alarm op verwerkingsmislukkingen, de knelpunten van de profielingang, en leveringskwesties. Essentieel voor productiereizen waarbij vertragingen of storingen van invloed zijn op de gebruikerservaring. | [&#x200B; het overzicht van Alarm &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [&#x200B; Overzicht van de Inzichten van de Waarneming &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | CJA funnel en de analyse van de gevolgen op de hele reis zorgen voor diepere rapporten van insight dan alleen die van AJO. Hiermee schakelt u stapsgewijze conversieanalyse, cohortvergelijking en optimalisatie van de reis in. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [&#x200B; overzicht van Analysis Workspace &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer] (AJO)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Kanaalconfiguratie | Fase 1: Kanaalinstelling | Kanaaloppervlakken configureren (e-mail, SMS, push) voor elk communicatietoetspunt in de reis |
| Berichtontwerp | Fase 2: Berichtinhoud maken | Inhoud van het berichtbericht van de auteur met verpersoonlijking, dynamische inhoud, en malplaatjes voor elke knoop van de reisactie |
| Journey Orchestration | Fase 3: Ontwerpen en activeren van reizen | Ontwerp het multi-step reiscanvas met entry, action, condition, wait, and exit nodes; test en publiceer |
| Frequentie en bedrijfsregels | Fase 4: Bestuur en optimalisering | Vorm frequentiecappen om over overseinen over reis touchpoints en andere gezamenlijke campagnes te verhinderen |
| Conflict- en prioriteitsbeheer | Fase 4: Bestuur en optimalisering | Prioriteitsscores toewijzen en conflictdetectie configureren voor reizen die concurreren met andere actieve communicatie |
| Inhoud experimenteren | Fase 4: Bestuur en optimalisering | A/B tests op berichtinhoud binnen de knopen van de reisactie uitvoeren om prestaties te optimaliseren |
| Rapportage en prestatieanalyse | Fase 5: Rapportage en bewaking | De uitvoering van de reis, de maatstaven van de levering per stap, en de prestaties van de overeenkomst controleren |

### [!DNL Real-Time CDP] (RT-CDP)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Fase 1: Kanaalinstellingen (voorwaarde) | Bepaal en evalueer het ingangspubliek voor publiek-gelezen reizen; bepaal voorwaardenpubliek voor vertakking |
| Goedkeuring en handhaving van bestuur | Fase 4: Bestuur en optimalisering | Beleid voor toestemmingsvoorkeuren en gegevensgebruik afdwingen voor acties voor reisberichten |

## Vereisten

Voltooi de volgende voorwaarden voordat u met de implementatie begint.

- [ ] AJO-sandbox is voorzien van machtigingen voor het maken en publiceren van reizen
- [ ] Ten minste één kanaaloppervlak (e-mail, SMS of push) is geconfigureerd en actief
- [ ] Profielschema bevat kenmerken die nodig zijn voor vertakking en personalisatie van voorwaarden
- [ ] Experience Event-schema is geconfigureerd voor conversiegebeurtenissen die worden gebruikt in afsluitcriteria
- [ ] Gebeurtenisstreaming is actief voor realtime-gebeurtenissen die worden gebruikt in exit-criteria of gebeurtenisgestuurd item
- [ ] Identiteitsnaamruimten en samenvoegbeleid zijn geconfigureerd voor het oplossen van profielen voor meerdere kanalen
- [ ] Inhoud-elementen (afbeeldingen, kopieën, CTA&#39;s) worden voorbereid voor elk aanraakpunt voor berichten
- [ ] Toegangspubliek wordt gedefinieerd en geëvalueerd (voor publiekslees-ritten)
- [ ] Het gebeurtenisschema voor activering is geconfigureerd (voor door gebeurtenissen geïnitieerde reizen)
- [ ] Testprofielen zijn beschikbaar voor validatie van de testmodus
- [ ] De lijst met onderdrukking wordt gecontroleerd en bijgewerkt voor alle gebruikte kanalen

## Implementatieopties

Bekijk de volgende opties om de beste aanpak voor uw meerstapse georkestreerde reis te bepalen.

### Optie A: Door het publiek gelezen georkestreerde reis

**het Best voor:** op tijd-gebaseerde opeenvolgingen van de kwekerij waar een bekend publiek de reis ingaat en door geplande touchpoints voortschrijdt — op instapkaartreeksen, vernieuwingsopeenvolgingen, re-betrokkenheidsdruppels, loyalimitatie reizen.

**hoe het werkt:**

Een publiek wordt gelezen bij reisingang, of als eenmalig gelezen of op een terugkerend programma. Alle in aanmerking komende profielen gaan de reis gelijktijdig in en gaan dan door het canvas in hun eigen tempo, die door wachttijdduur en voorwaardenevaluatie wordt geregeerd. Het pad van elk profiel door de reis is onafhankelijk. Sommigen nemen mogelijk de tak &quot;betrokken&quot; terwijl anderen de tak &quot;niet betrokken&quot; nemen op basis van hun gedrag of kenmerken.

Het publiek wordt geëvalueerd op het moment dat de activiteit Audience lezen wordt uitgevoerd. Voor terugkerende reizen wordt het publiek opnieuw beoordeeld op elke terugkerende actie en komen nieuwe kwalificatieprofielen de reis binnen terwijl profielen die al op de reis zijn, hun pad voortzetten. Deze benadering verstrekt voorspelbare ingangstijdstip en is geschikt voor geplande levenscyclusprogramma&#39;s.

**Zeer belangrijke overwegingen:**

- Het publiek moet worden gedefinieerd en geëvalueerd voordat de reis wordt geactiveerd
- Bij terugkeren van lezen kunnen nieuwe kwalificatoren op elke cyclus worden ingevoerd
- Profielen tijdens de reis worden niet opnieuw gelezen; alleen nieuwe kwalificatietekens worden bij volgende lezingen ingevoerd
- Wacht stappen een minimumduur van 1 uur voor publiek-gelezen reizen hebben

**Voordelen:**

- Voorspelbare ingangstiming uitgelijnd op bedrijfsschema&#39;s
- Ondersteunt grote publieksvolumes (tot 20.000 profielen per seconde standaardsnelheid)
- Eenvoudig te testen en te bewaken met bekende populaties voor het publiek
- Kan worden gepland voor terugkerende invoer (dagelijks, wekelijks, maandelijks)

**Beperkingen:**

- Invoer is op batch gebaseerd, niet in real-time — profielen worden ingevoerd bij de geplande leestijd, niet wanneer ze in aanmerking komen
- Niet geschikt voor door gedrag geïnitieerde reeksen die directe reactie vereisen
- Wijzigingen in leesvolgorde worden niet weerspiegeld voor profielen die al op reis zijn

**Experience League:**

- [Lees de publieksactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Een reis maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)

### Optie B: Door gebeurtenissen veroorzaakte georkestreerde reis

**het Best voor:** Gedrag-in werking gestelde opeenvolgingen waar een gebeurtenis in real time de reis begint — de escalatie van het kartverlaten, post-aankoopcultuur, mijlpaal-teweeggebrachte loyaliteitreis, de opeenvolgingen van de proefactivering.

**hoe het werkt:**

Een eenheidsgebeurtenis (bijvoorbeeld een aankoop, het verlaten van het winkelwagentje, het indienen van een formulier of het installeren van een app) leidt in real-time tot het invoeren van een reis voor afzonderlijke profielen. Wanneer de gebeurtenis wordt ontvangen, gaat het profiel de reis in en dan door de opeenvolging van aanraakpunten met voorwaarden, wacht, en vertakkend. Deze benadering combineert de directheid van gebeurtenis-teweeggebrachte overseinen met de multi-step organisatie van een volledige reis.

De activerende gebeurtenis moet worden geconfigureerd als een reisgebeurtenis met het bijbehorende schema en de voorwaarden. Tijdens de reis wordt voortdurend naar de gebeurtenis geluisterd en worden profielen één voor één ingevoerd wanneer de gebeurtenissen aankomen. De volgende vervoerknopen kunnen de reactie van het profiel evalueren om te bepalen welke tak te volgen.

**Zeer belangrijke overwegingen:**

- Streaming van gebeurtenissen in real time is actief
- Gebeurtenisschema&#39;s en -voorwaarden moeten nauwkeurig zijn geconfigureerd om onjuiste triggers te voorkomen
- Regels voor opnieuw invoeren zijn van essentieel belang. Bepaal of een profiel opnieuw kan worden ingevoerd als de gebeurtenis opnieuw wordt geactiveerd.
- Ondersteunt maximaal 5.000 gebeurtenissen per seconde per sandbox

**Voordelen:**

- Invoer in realtime op basis van klantgedrag — in hoge mate contextueel
- Elk profiel wordt onafhankelijk ingevoerd wanneer de gebeurtenis plaatsvindt, niet volgens een schema
- Natuurlijke geschiktheid voor gedragsresponssequenties (afschaffing van winkelwagentjes, na aankoop)
- Kan combineren met profielgegevens voor gepersonaliseerde vertakking na invoer

**Beperkingen:**

- Er moet een streaminggebeurtenisinfrastructuur aanwezig zijn
- Hogere complexiteit in configuratie en testen van gebeurtenisschema
- Elke gebeurtenis voert één profiel in. Dit is niet geschikt voor activering van grote doelgroepen
- Foutopsporing vereist het traceren van individuele profielreizen

**Experience League:**

- [Algemene gebeurtenissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [kwalificatiegebeurtenissen voor het publiek](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)

### Optie C: meerkanaals georkestreerde reis

**Best voor:** de opeenvolgingen van het dwars-kanaal die verschillende kanalen bij elk aanraakpunt gebruiken — e-mail toen SMS toen duw escalatie, of e-mail plus in-app aanvullend overseinen. Kan item gebruiken dat door het publiek wordt gelezen of door gebeurtenissen wordt geactiveerd.

**hoe het werkt:**

Deze optie breidt Optie A of Optie B uit door veelvoudige overseinenkanalen binnen de zelfde reis op te nemen. Elk actieknooppunt in de reis kan zich op een verschillend kanaal richten (e-mail, SMS, duw, in-app, of Web), die een afzonderlijke kanaaloppervlakte voor elk vereisen. De reisontwerper selecteert bij elke stap het aangewezen kanaal, toelatend escalatiepatronen (bijvoorbeeld, eerst e-mail, dan sms als geen overeenkomst) of complementaire patronen (bijvoorbeeld, e-mail met in-app versterking).

De reizen over kanalen vereisen kanaaloppervlakten voor elk gebruikt kanaal en moeten rekening houden met kanaalspecifieke verpersoonlijking, karaktergrenzen, en opt-in vereisten. Voorwaardelijke knooppunten kunnen de betrokkenheid met vorige berichten controleren (bijvoorbeeld &quot;geopende e-mail?&quot; als een vertakkingsvoorwaarde) om het volgende kanaal te bepalen.

**Zeer belangrijke overwegingen:**

- Vereist actieve kanaaloppervlakken voor elk kanaal dat in de reis wordt gebruikt
- Elk kanaal heeft verschillende verpersoonlijkingsmogelijkheden en inhoudsbeperkingen
- De toestemming moet per kanaal worden geverifieerd — een profiel kan worden gekozen voor e-mail maar niet voor SMS
- Kanaalspecifieke frequentiecaps moeten worden geconfigureerd om overseinen over kanalen te voorkomen

**Voordelen:**

- Maximaliseert bereik door profielen in te schakelen op de kanalen van hun voorkeur
- Laat escalatiestrategieën voor non-responsieve profielen toe
- Ondersteunt aanvullende berichten via kanalen voor versterking
- De meest geavanceerde klantenervaring mogelijk

**Beperkingen:**

- Hoogste complexiteit van implementatie — vereist configuratie voor elk kanaal
- Inhoud moet voor elk kanaal op elk aanraakpunt worden geschreven
- Toestemming en frequentiebeheer worden complexer over kanalen
- Testen vereist validatie op alle kanaaloppervlakken

**Experience League:**

- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Optievergelijking

In de volgende tabel worden de drie implementatieopties vergeleken met de belangrijkste criteria.

| Criteria | Optie A: Publiek gelezen | Optie B: Gebeurtenis geactiveerd | Optie C: Multikanaal |
| --- | --- | --- | --- |
| Best voor | Geplande levenscyclusprogramma&#39;s, kwekerijprogramma&#39;s | Responssequenties van gedrag, verlaten van winkelwagentje | Doorverwijzing van meerdere kanalen, aanvullende berichtgeving |
| Invoer timing | Gepland (batch) | Real-time (gebeurtenisgestuurd) | Of gepland of real time |
| Complexiteit | Gemiddeld | Medium-High | Hoog |
| Invoervolume | Tot 20.000 profielen/sec | Tot 5.000 gebeurtenissen/sec | Gelijk aan onderliggende invoermethode |
| Kanaalbereik | Eén of meerdere kanalen | Eén of meerdere kanalen | Meerdere kanalen vereist |
| Vereisten | Gedefinieerd publiek, evaluatieschema | Streaming-gebeurtenisinfrastructuur | Kanaaloppervlakken voor elk kanaal |
| Realtime reactie | Neen — batchvermelding | Ja — onmiddellijk na de gebeurtenis | Afhankelijk van een invoermethode |

### Kies de juiste optie

Gebruik de volgende beslissingsstroom om de juiste implementatiebenadering te selecteren:

1. **is de reis die door een klantengedrag of een gebeurtenis in werking wordt gesteld?** Als ja, kies **Optie B** (gebeurtenis-teweeggebracht). Als de reis door een gepland publiek in werking wordt gesteld leest, kies **Optie A** (publiek-Gelezen).

2. **gebruikt de reis veelvoudige overseinenkanalen (bijvoorbeeld, e-mail EN SMS)?** Als ja, pas **Optie C** (Multikanaal) bovenop uw keus van de ingangsmethode (A of B) toe. Als de reis één enkel kanaal door het hele traject gebruikt, volstaat Optie A of B alleen.

3. **moet u aan een verschillend kanaal escaleren dat op overeenkomst wordt gebaseerd?** Als ja, kies **Optie C** met voorwaardenknopen die overeenkomst met vorige berichten en tak aan afwisselende kanalen controleren.

4. **is het publiek gekend vooraf en verwerkt op een programma?** Als ja, kies **Optie A**. Als de profielen de reis zouden moeten ingaan het ogenblik zij een actie uitvoeren, kies **Optie B**.

## Uitvoeringsfasen

De volgende fasen lopen door de implementatie van begin tot eind van een multi-step georkestreerde reis.

### Fase 1: Kanalen instellen en publiek voorbereiden

**de functies van de Toepassing:** AJO: De Configuratie van het Kanaal, rt-CDP: de Evaluatie van het publiek

Voordat u de reis ontwerpt, moeten alle kanaaloppervlakken actief zijn en moet het publiek voor de binnenkomst (voor optie A) worden gedefinieerd en geëvalueerd. Deze fase verzekert de infrastructuur klaar voor berichtlevering is.

#### Bepaal kanaaltype voor elk aanraakpunt

Welke overseinenkanalen zullen de reis op elk aanraakpunt gebruiken?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen e-mail | Reis communiceert uitsluitend via e-mail (inboarding, nurture) | Eenvoudige installatie; vereist e-mailsubdomein en IP-pool; afhankelijk van plaatsing in postvak |
| Alleen SMS | Tijdgevoelige waarschuwingen, herinneringen voor afspraak | Vereist gebruikersgegevens voor SMS-provider (Sinch, Twilio, Infobip); hogere kosten per bericht; strengere regels voor opt-out |
| Alleen induwen | In-app betrokkenheidssequenties voor mobiele gebruikers | Vereist APNs/FCM-referenties; gebruikers moeten de app hebben geïnstalleerd |
| Multikanaal | Escalatie of complementair overseinen over kanalen | Vereist kanaaloppervlak per kanaal; meest complex maar hoogste bereik |

#### Beslissen over de beoordelingsmethode voor het publiek (optie A)

Hoe snel moeten de profielen voor het ingangspubliek in aanmerking komen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Batchevaluatie | Publiek wordt gelezen volgens een schema (dagelijks, wekelijks); geen real-time ingang nodig | Eenvoudige opstelling; publiek geëvalueerd vóór reis gelezen; steunt complexe segmentregels |
| Streaming evaluatie | Profielen moeten in bijna realtime in aanmerking komen als kenmerken worden gewijzigd | De segmentregelexpressie moet in aanmerking komen voor streaming; bijna real-time kwalificatie |

#### Beslissen over de methode voor subdomeindelegatie (e-mailkanaal)

Hoe moet het e-mailverzendende subdomein worden gedelegeerd aan Adobe?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Volledige delegatie | Adobe beheert DNS-records; eenvoudigste setup | Snelst te configureren; Adobe verwerkt SPF, DKIM, DMARC |
| CNAME-delegatie | Organisatie behoudt DNS-controle | Vereist DNS beheerderbetrokkenheid; De verslagen van CNAME moeten worden gevormd |

#### UI-navigatie

- Kanaaloppervlakken: Beheer > Kanalen > Kanaaloppervlakken > Oppervlak maken
- Subdomeinen: Beheer > Kanalen > Subdomeinen
- SMS-configuratie: Beheer > Kanalen > SMS-configuratie
- Pushconfiguratie: Beheer > Kanalen > Instellingen voor pushmeldingen
- Soorten publiek: Klant > Soorten publiek > publiek maken > Regel maken

#### Belangrijkste configuratiedetails

- Verifieer IP groepswarmup status voor e-mail — de nieuwe IP pools vereisen een geleidelijk warmtekrachtplan over 2 tot 4 weken
- Voor SMS, vorm leveranciergeloofsbrieven en verifieer de registratie van het afzenderaantal
- Upload voor push APNs-certificaten en FCM-serversleutels
- Bepaal het ingangspubliek gebruikend de Bouwer van het Segment met segmentregels die de doelbevolking behandelen
- Inclusief onderdrukkingsregels in de definitie van het publiek (exclusief onlangs geconverteerde, globaal niet-geabonneerde)

#### Waar opties afwijken

**voor Optie A (publiek-Gelezen):**
Bepaal en evalueer het ingangspubliek. Bevestig dat het publiek een populatie heeft die niet gelijk is aan nul. Bepaal of de reis een eenmalig publiek lees- of terugkerend leesschema zal gebruiken.

**voor Optie B (gebeurtenis-teweeggebracht):**
Verifieer dat het het teweegbrengen gebeurtenisschema wordt gevormd en dat de gebeurtenissen in het platform stromen. Geen vooraf gedefinieerd publiek vereist — profielen worden afzonderlijk ingevoerd na ontvangst van de gebeurtenis.

**voor Optie C (multi-Kanaal):**
Kanaaloppervlakken configureren voor ELK kanaal dat tijdens de rit wordt gebruikt (e-mail, SMS, push, in-app). Verifieer toestemmingsstatus per kanaal voor de doelbevolking.

#### Experience League-documentatie

- [Kanaaloppervlakken instellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [IP-opwarmingsplannen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)


### Fase 2: Berichtinhoud maken

**functie van de Toepassing:** AJO: De Authoring van het Bericht

Schrijf de berichtinhoud voor elk aanraakpunt in de reis. Elk bericht kan verschillende inhoud, verpersoonlijkingsdiepte, en kanaal hebben. Deze fase leidt tot alle te leveren inhoud die de knooppunten van de reisactie zullen verwijzen.

#### Inhoudsaanpak kiezen

Moet elk bericht van een malplaatje beginnen, van kras worden ontworpen, of HTML invoeren?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Bestaande inhoudssjabloon | Berichten die consistent zijn met bestaande indelingen | Snelst; garandeert naleving van merk; sjabloon moet bestaan en moet overeenkomen met kanaaltype |
| Ontwerpen vanaf nul | Unieke, aangepaste schermindelingen voor elk aanraakpunt | Zeer flexibel; langere buildtijd; gebruik Designer via e-mail slepen en neerzetten |
| HTML importeren | Vooraf gebouwde HTML van externe ontwerpgereedschappen | Vereist schone HTML; kan een aanpassing voor de reactiesnelheid nodig hebben |

#### Bepaal de diepte van de verpersoonlijking

Hoeveel verpersoonlijking zou elk bericht moeten omvatten?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Eenvoudige token-invoeging | Voornaam, plaats, eenvoudige profielkenmerken | Lage complexiteit; gebruikt de syntaxis van Handgrebars met XDM wegen |
| Voorwaardelijke inhoudsblokken | Verschillende inhoud weergegeven op basis van segment of kenmerk | Medium-complexiteit; vereist dynamische inhoudsregels |
| Reis-contextafhankelijke personalisatie | Inhoud varieert op basis van reispad, vorige interacties | Hogere complexiteit; maakt gebruik van reiscontextvariabelen en gebeurtenisgegevens |

#### Fragmentstrategie kiezen

Moeten gedeelde inhoudsblokken (kop- en voetteksten, juridische tekst) worden gemaakt als herbruikbare fragmenten?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Herbruikbare fragmenten | Meerdere berichten delen gemeenschappelijke elementen; merkconsistentie vereist | De veranderingen verspreiden zich aan alle berichten gebruikend het fragment; maximum 30 fragmenten per bericht |
| Inline-inhoud | Eenmalige berichten met unieke lay-outs | Sneller voor inhoud voor eenmalig gebruik; geen voordeel voor consistentie tussen berichten |

#### UI-navigatie

- Content Management > Content Templates > Browse
- Designer e-mailen (binnen campagne- of reisactie)
- Inhoudsbeheer > Fragmenten > Fragment maken

#### Belangrijkste configuratiedetails

- Inhoud van auteur voor ELKE-berichtenactie tijdens de reis — een reis in vier stappen kan vier aparte berichtenontwerpen vereisen
- Verpersoonlijkingsexpressies gebruiken die verwijzen naar XDM-profielpaden (bijvoorbeeld `{{profile.person.name.firstName}}`)
- Dynamische inhoudsblokken voor segmentspecifieke variaties configureren
- Geef een voorvertoning van elk bericht weer met testprofielen om de weergave op maat te controleren
- Proefdrukken verzenden naar interne belanghebbenden voor inhoudsrevisie
- Voor SMS: tekenlimiet respecteren (160 tekens voor standaard GSM-codering)
- Voor push, configureer titel, tekst, afbeelding en diepe link/URL-actie

#### Experience League-documentatie

- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Een e-mail maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Een SMS-bericht maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Een pushmelding ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)


### Fase 3: Ontwerpen en de reis activeren

**functie van de Toepassing:** AJO: Journey Orchestration

Ontwerp het multi-step wegcanvas met inbegrip van de ingangsknoop, actieknooppunten (berichten), voorwaardenknopen (het vertakken), wachtknopen (tijdvertragingen), en uitgangscriteria. Test vervolgens met testprofielen en publiceer deze.

#### Beslissen op ingangstype

Hoe moeten profielen de reis ingaan?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Publiek lezen | Geregistreerde peuterreeksen; bekende doelgroep verwerkt in batch | Het publiek wordt tijdens het lezen geëvalueerd; ondersteunt eenmalige of terugkerende leesbewerkingen; tot 20.000 profielen/sec |
| Eenmalige gebeurtenis | Beleidstriggers in realtime (aankoop, afstoting van winkelwagentjes) | Real-time invoer; vereist streaming van gebeurtenissen; maximaal 5.000 gebeurtenissen/sec |
| Poortkwalificatie | Invoer wanneer een profiel een publiek in bijna real-time binnengaat of verlaat | Evaluatie streaming; geactiveerd door wijziging van segmentlidmaatschap |
| Zakelijke gebeurtenis | De hele organisatie activeert de reis voor een publiek | Nuttig voor productlanceringen, weergebeurtenissen, systeemwaarschuwingen |

#### Beslissen over het terugkeerbeleid

Kan een profiel de reis na voltooiing of het verlaten opnieuw ingaan?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Opnieuw openen toestaan (met afkoelingsmethode) | Profielen moeten mogelijk de reis herhalen (terugkerende aankopen, seizoensgebonden herbetrokkenheid) | Minimale afkoelingswaarde van 5 minuten; voorkomt dubbele vermeldingen in afkoelvenster |
| Geen nieuwe toegang | Eenmalige ritten (onboarding, gebeurtenis met één levenscyclus) | Profiel voltooit of verlaat de reis en kan niet meer worden ingevoerd |

#### De wachttijd tussen aanraakpunten bepalen

Hoe lang moet de reis tussen elk bericht wachten?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Vaste duur (bijvoorbeeld 3 dagen) | Consistente plaatsing, ongeacht het gedrag van het profiel | Eenvoudig, voorspelbaar tijdstip; minimaal 1 uur voor publieksgerichte reizen |
| Specifieke datum/tijd | Bericht moet op een nauwkeurige tijd (bijvoorbeeld, vernieuwingsdatum) aankomen | Gebruikt profielkenmerk of expressie om de exacte datum/tijd te bepalen |
| Aangepaste expressie | Dynamische wachttijd op basis van profielgegevens of reiscontext | Zeer flexibel; vereist uitdrukking creatie |

#### Beslissen over vertakkingsvoorwaarden

Welke voorwaarden bepalen welk pad een profiel gebruikt?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Kenmerken profiel controleren | Tak gebaseerd op loyaliteitsrij, productbelang, geografie | Gebruikt profielgegevens beschikbaar bij evaluatietijd |
| Segmentlidmaatschapscontrole | Vertakking op basis van het feit of het profiel tot een specifiek publiek behoort | Vereist dat het publiek wordt gedefinieerd en geëvalueerd |
| Gebeurtenisgegevenscontrole | Vertakking gebaseerd op of het profiel een actie (geopende e-mail, klikte verbinding) uitvoerde | Evalueert gegevens over gebeurtenissen met een reisbereik; nuttig voor vertakking op basis van betrokkenheid |
| Percentage splitsing | Profielen willekeurig over paden verdelen (voor A/B-tests of gecontroleerde rollouts) | Maakt geen gebruik van profielgegevens; puur willekeurige toewijzing |

#### Beslissen over uitstapcriteria

Welke gebeurtenis of toestand zorgt ervoor dat een profiel de reis voortijdig verlaat?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Conversion-gebeurtenis | Profiel voltooit de gewenste actie (aankoop, aanmelding, verzending van formulier) | Vereist streaming van gebeurtenissen; meest gangbare afsluitcriteria |
| Afsluiten van lidmaatschap voor publiek | Profiel verlaat het ingangspubliek of sluit zich aan bij een uitsluitingspubliek | Evalueert in bijna real time voor het stromen publiek |
| Time-out | Maximale reisduur bereikt (maximaal 91 dagen) | Standaardveiligheidsnet; configureerbaar in reiseigenschappen |
| Geen uitstapcriteria | Profiel voltooit het volledige pad op natuurlijke wijze | Eenvoudig; alle profielen gaan de volledige reis door tenzij manueel verwijderd |

#### Beslissen over time-out voor transport

Wat is de maximale duur die een profiel in de reis kan blijven?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| 91 dagen (maximaal) | Langlopende reizen (driemaandelijkse verlenging, verlengd instapmodel) | Maximaal toegestaan; profielen die op time-out nog onderweg zijn, worden automatisch verlaten |
| Aangepaste kortere duur | De reis moet binnen een bepaald venster (7 dagen, 14 dagen, 30 dagen) worden voltooid | Instellen op basis van de natuurlijke levenscyclus van het gebruiksgeval |

#### UI-navigatie

- Reis maken: Reis > Reis maken
- Eigenschappen voor reizen: canvas reis > deelvenster Eigenschappen
- Itemknooppunt: Reis canvas > Slepen &quot;Read Audience&quot; of gebeurtenisactiviteit
- Actieknooppunten: Reiscanvas > Kanaalactie slepen (e-mail, SMS, push)
- Condition-knooppunten: Reis canvas > &quot;Condition&quot;-activiteit slepen
- Wacht knopen: Reis canvas > belemmering &quot;wacht&quot;activiteit
- Afsluitcriteria: Reis-eigenschappen > Afsluitcriteria > Configureren
- Testmodus: Reis canvas > Testen/uitschakelen van testmodus
- Publiceren: Reis canvas > Publiceren

#### Belangrijkste configuratiedetails

- Noem de reis met een duidelijke, beschrijvende overeenkomst (bijvoorbeeld, &quot;Onboarding_Series_Email_v1&quot;)
- De tijdzone voor een consistente wachttijdstap instellen
- Vorm elke actieknoopknoop met de aangewezen kanaaloppervlakte en verbinding aan geschreven berichtinhoud
- Elke tak moet met een activiteit van het Eind eindigen
- Regels voor terugkeer configureren die geschikt zijn voor het gebruiksgeval
- Gebruik de testmodus met testprofielen om het volledige reispad te simuleren voordat u publiceert
- Controleren of testprofielen de verwachte paden doorlopen en juiste berichten ontvangen

#### Waar opties afwijken

**voor Optie A (publiek-Gelezen):**

- Sleep de activiteit &quot;Gelezen Publiek&quot;als ingangsknoop
- Doelgroep selecteren die is gedefinieerd in Fase 1
- Configureer desgewenst een terugkerend leesprogramma (dagelijks, wekelijks)
- De snelheid voor de leessnelheid configureren als de belasting van het downstreamsysteem een probleem is

**voor Optie B (gebeurtenis-teweeggebracht):**

- Sleep de activeringsgebeurtenis als het invoerknooppunt
- Het gebeurtenisschema en de toegangsvoorwaarden configureren
- Regels voor opnieuw invoeren zorgvuldig instellen om dubbele vermeldingen van herhaalde gebeurtenissen te voorkomen

**voor Optie C (multi-Kanaal):**

- De invoermethode van optie A of B gebruiken
- Bij elke actieknooppunt selecteert u het juiste kanaaloppervlak voor dat aanraakpunt
- Voeg voorwaardenknopen tussen kanalen toe om overeenkomst (bijvoorbeeld &quot;te controleren open het profiel e-mail?&quot;) en route aan afwisselende kanalen

#### Experience League-documentatie

- [Een reis maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journeyeigenschappen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Lees de publieksactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Algemene gebeurtenissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [kwalificatiegebeurtenissen voor het publiek](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Een bericht toevoegen tijdens een rit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Voorwaardeactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wachtactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Afsluitingscriteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Eindactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Reisbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Uw reis testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [De reis publiceren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)


### Fase 4: governance en optimalisatie configureren

**de functies van de Toepassing:** AJO: Frequentie &amp; BedrijfsRegels, AJO: Conflict &amp; Prioritair Beheer, AJO: De Experimentatie van de inhoud, rt-CDP: Toestemming &amp; de Handhaving van het Bestuur

Pas frequentiecappen toe om over-overseinen te verhinderen, prioritaire scores voor conflictoplossing met andere actieve mededelingen toe te wijzen, naar keuze A/B tests binnen reisberichten te vormen, en toestemminghandhaving te verifiëren.

#### Bepaal de configuratie van de frequentiecalter

Moeten reisberichten mondiale frequentiecamera&#39;s respecteren?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Frequentieregels toepassen | Reis werkt samen met andere campagnes en reizen; profielen mogen niet overdreven worden | Berichten kunnen worden onderdrukt als het profiel het uiteinde van andere communicatie al heeft bereikt |
| Vrijstellen van aftopping | De berichten van de reis zijn kritiek en moeten altijd worden geleverd (transactie, regelgevende) | Gebruik spaarzaam; kan bijdragen aan vermoeidheid van berichten als deze wordt overgebruikt |

#### Beslissen over toewijzing van prioriteitsscore

Hoe moet deze reis in verhouding staan tot andere actieve campagnes en reizen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Hoge prioriteit (70-100) | De berichten van de reis zijn kritieke levenscyclusmededelingen (onboarding, vernieuwing) | Hogere prioriteit wint wanneer de conflicten met andere mededelingen zich voordoen |
| Prioriteit Medium (30-69) | Reisberichten zijn belangrijk, maar niet dringend (voeden, onderwijs) | Kan onderdrukt worden door communicatie met hogere prioriteit |
| Lage prioriteit (0-29) | Reisberichten zijn aanvullend of promotioneel | Wordt onderdrukt wanneer wordt geconcurreerd met berichten met hogere prioriteit |

#### Beslissen over het experimenteren met inhoud

Moet een reisbericht een A/B-test of een multivariatie-test bevatten?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Ja — A/B-test | Onderwerpreeksen, CTA&#39;s of inhoudopmaak optimaliseren op een bepaald aanraakpunt | Vereist voldoende volume per variant voor statistische significantie; 2-10 ondersteunde behandelingen |
| Geen experimenten | Inhoud is voltooid of het volume is te laag voor betekenisvolle tests | Eenvoudiger instellen; geen varianttracering vereist |

#### UI-navigatie

- Frequentieregels: Beheer > Zakelijke regels > Regel maken
- Prioriteitsscores: Reiseigenschappen > Prioriteitsscore
- Conflictdetectie: Beheer > Bedrijfsregels > Conflict en prioriteit
- Inhoudsexperiment: Reiscanvas > Berichtactie selecteren > Schakelen tussen inhouds-experiment
- Beleid voor goedkeuring: Privacy > Beleid > Beleid voor goedkeuring

#### Belangrijkste configuratiedetails

- Kanaalspecifieke frequentiecaps instellen (bijvoorbeeld max. 3 e-mails/week, max. 1 SMS/dag, max. 2 push/dag)
- Wijs een prioritaire score aan de reis (0-100) toe die zijn bedrijfsbelang met betrekking tot andere actieve mededelingen weerspiegelt
- Controleer het deelvenster voor conflictdetectie om eventuele overlappende campagnes of reizen te identificeren
- Als het runnen van een inhoudexperiment, behandelingsvarianten bepalen, verkeerstoewijzing plaatsen, kiezen het succes metrisch (opent, klikt, of omzettingen), en de betrouwbaarheidsdrempel (typisch 95%) plaatsen
- Controleren of de handhaving van de toestemming actief is voor elk kanaal dat tijdens de reis wordt gebruikt

#### Experience League-documentatie

- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Overzicht van bedrijfsregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Mogelijke conflicten identificeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Afbakening van reizen en arbitrage](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Toestemming in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)


### Fase 5: Rapportage en bewaking configureren

**de functies van de Toepassing:** AJO: Rapportering &amp; de Analyse van Prestaties, Controle &amp; Waarneming, Rapportering &amp; Analyse

Volg de uitvoering van de reis tijdens en na activering, bekijk de gegevens voor levering en service per stap, configureer waarschuwingen voor problemen met de verwerking van de reis en maak eventueel een CJA-werkruimteanalyse voor een diepe funnel- en fallout-visualisatie.

#### Beslissen over de rapportagemethode

Welke rapporteringsinstrumenten zijn nodig voor deze reis?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen systeemeigen AJO-rapporten | De standaardbewaking voor levering en betrokkenheid is voldoende | Live rapport (tijdens uitvoering) en All Time-rapport (na uitvoering); vernieuwt elke 60 seconden voor live |
| AJO + CJA-analyse | Diepe funnel-analyse, stapsgewijze conversiesnelheden, fallout-visualisatie of vergelijking tussen verschillende reizen zijn nodig | Vereist CJA-verbinding en gegevensweergave gekoppeld aan AJO-gegevenssets; meest uitgebreid |
| Alleen CJA | De organisatie gebruikt CJA als primair platform voor analyse | Vereist CJA-configuratie; eigen AJO-rapporten blijven beschikbaar als back-up |

#### Beslissen op waakzame configuratie

Welke trajectmislukkingen zouden alarm moeten veroorzaken?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Signaleringen van de reisverwerking | Altijd aanbevolen voor productiereizen | Waarschuwingen over fouten bij profielinvoer, fouten met actieknooppunten en reisstallen |
| Ontbrekende levering | Kritiek voor reizen met hoogwaardige communicatie | Waarschuwingen over stuitpercentages die de drempelwaarden overschrijden, mislukte aflevering |

#### UI-navigatie

- Reis live rapport: Reis > Selecteer reis > Live rapport
- Reis-alle-tijdrapport: Reis > Selecteer reis > Alle-tijdrapport
- Waarschuwingen: Waarschuwingen > Regels voor waarschuwingen > Abonneren
- CJA-werkruimte: Projecten > Nieuw project maken

#### Belangrijkste configuratiedetails

- Heb toegang tot het levende rapport tijdens reisuitvoering om profielingangen, uitgang, en per-stap leveringsmetriek in echt te controleren - tijd
- Na voltooiing van de reis (of nadat voldoende gegevens zijn verzameld), herzie het rapport All Time voor uitgebreide analyse
- Platformwaarschuwingen configureren voor problemen met de verwerking van reizen en leveringsproblemen
- Voor CJA-analyse moet u ervoor zorgen dat de CJA-verbinding gegevens over de AJO-ervaringsgebeurtenis bevat (Berichtfeedback, E-mailtracking, trapsgewijze gebeurtenissen)
- Een CJA Workspace maken met:
   - Funnel visualisatie met profieltellingen bij elke reisstap
   - Vallout visualisatie om drop-off punten te identificeren
   - Berekeningen van de omrekeningskoers
   - Analyse van tijd tot conversie
   - Uitsplitsing op kanaalniveau (voor meerkanaalse reizen)

#### Experience League-documentatie

- [Journaal live](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementatieoverwegingen

Lees de volgende instructies, valkuilen, aanbevolen procedures en afwegingen voor en tijdens de implementatie.

### Guardrails en limieten

- Maximum van **500 levende reizen** per zandbak - [&#x200B; de guardrails van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- De maximum **reisduur is 91 dagen** (globale onderbreking) — profielen nog in de reis in onderbreking worden automatisch verlaten
- Maximum van **50 activiteiten** per wegcanvas
- Lees de ritsproces van het Publiek tot **20.000 profielen per seconde** (standaardthrottle)
- De de gebeurtenisreizen van de eenheid steunen tot **5.000 gebeurtenissen per seconde** per zandbak
- Wacht de stappen a **minimumduur van 1 uur** voor publiek-gelezen reizen hebben
- De  van de reis **re-entry koeldown minimum is 5 minuten**
- Maximum van **10 kanaaloppervlakten per kanaaltype** per zandbak
- Maximale e-mailgrootte van **100 KB** geadviseerd voor optimale leverbaarheid
- Maximum van **30 inhoudsfragmenten** per bericht
- Maximum van **10 de behandelingen van het inhoudexperiment** (varianten) per experiment
- Maximum van **10 die configuraties** per zandbak begrenzen
- Maximum van **4.000 segmentdefinities** per zandbak

### Veelvoorkomende valkuilen

- **het Publiceren zonder het testen:** gebruik altijd testwijze met testprofielen om de volledige wegweg vóór het publiceren te bevestigen. Controleer of de profielen de verwachte vertakkingen doorlopen, de stappen correct vooruit wachten en de berichten correct worden weergegeven.
- **Ontbrekende eindactiviteiten op takken:** Elke reistak moet met een activiteit van het Eind eindigen. De reis zal niet publiceren als om het even welke tak zonder een beëindigingsknoop wordt verlaten.
- **Te brede toegangsvoorwaarden:** Een los bepaald ingangspubliek of gebeurtenisvoorwaarde kan de reis met onbedoelde profielen overstromen. Verfijn ingscriteria met specifieke kenmerkcontroles en suppressieregels.
- **het negeren van re-ingangsregels:** voor gebeurtenis-teweeggebrachte reizen, kunnen de profielen de teweegbrengende gebeurtenis veelvoudige tijden in brand steken. Zonder de juiste configuratie voor terugkeer (ontken herbinnenkomst of afkoelingsperiode), kunnen profielen zich in de reis ophopen, waardoor dubbele berichten ontstaan.
- **wacht de verwarring van de step tijdzone:** wacht de duur in UTC wordt verwerkt. Stel de tijdzone van de reis expliciet in de eigenschappen van de reis in om te zorgen dat de stappen op de verwachte lokale tijd worden uitgevoerd.
- **Bewerkend een levende reis:** Levende reizen kunnen niet direct worden uitgegeven. Als u wijzigingen wilt aanbrengen, dupliceert u de rit, wijzigt u de kopie, stopt u het origineel en publiceert u de nieuwe versie. Plan de reisversioning voordat u live gaat.
- **geen vastgestelde uitgangscriteria:** Zonder uitgangscriteria, zullen de profielen die middenreis omzetten verdere berichten blijven ontvangen — potentieel irrelevant of tegenstrijdig. Configureer altijd afsluitcriteria voor conversiegebeurtenissen.
- **de toestemmingsmisgroepering van het Kanaal:** Een profiel kan binnen voor e-mail maar niet SMS worden gekozen. Bij meerkanaalse reizen moet de toestemming per kanaal in acht worden genomen. Verifieer de toestemmingsgebieden op elke kanaaloppervlakte worden bevolkt en worden afgedwongen.

### Aanbevolen procedures

- **Begin eenvoudig, herhaling:** Begin met een lineaire 2-3 stap reis alvorens complexe vertakking toe te voegen. Valideer de kernstroom voordat u lagen toevoegt in omstandigheden en kanalen.
- **beschrijvende noemende overeenkomsten van het Gebruik:** de vervoerknopen van de naam, voorwaarden, en wachten stappen duidelijk (bijvoorbeeld, &quot;Wacht_3_Days_After_Welcome&quot;eerder dan &quot;Wacht 1&quot;). Dit maakt testwijze het zuiveren en rapportinterpretatie veel gemakkelijker.
- **vorm vroege uitgangscriteria:** bepaal de omzetgebeurtenis als uitgangscriteria alvorens de wegwegen te ontwerpen. Dit zorgt ervoor dat profielen die worden omgezet, van de reis worden verwijderd, ongeacht de stap waarop zij zijn.
- **Reeks betekenisvolle wachttijdduur:** De wachttijd van de basis op gegevens van het klantengedrag — tijd tussen typische interactie, verwachte antwoordvensters, en kanaal-aangewezen kadentie (bijvoorbeeld, 2-3 dagen tussen e-mail, 1 week tussen SMS).
- **de voorwaardenknopen van het Gebruik om overeenkomst te controleren:** na een berichtactie, voeg een voorwaarde toe om te controleren of het profiel betrokken (geopend, geklikt). Verbind profielen aan één weg en niet-bezeten profielen aan een escalatie of afwisselend kanaalweg.
- **Hefboomwerking verwerkte attributen voor het vertakken:** Gebruik gegevens verwerkte attributen zoals betrokkenheidsscores, koopfrequentie, of dagen sinds laatste activiteit om vertakkende besluiten te maken gegeven-gedreven eerder dan willekeurig.
- **Monitor en optimaliseer intern:** de reisrapporten van het overzicht wekelijks tijdens de aanvankelijke looppas. Identificeer drop-off punten, pas wachttijdduur aan, verfijnen voorwaarden, en optimaliseer berichtinhoud die op de gegevens van de per-step prestaties wordt gebaseerd.
- **Versie uw reizen:** wanneer het aanbrengen van veranderingen, dupliceer de reis om een nieuwe versie tot stand te brengen. Een logboek met versiewijzigingen bijhouden voor controle en optimalisatie.

### Handelsbesluiten

De volgende compromissen moeten in de context van uw specifieke bedrijfsvereisten worden geëvalueerd.

#### Publiek-gelezen ingang vs gebeurtenis-teweeggebrachte ingang

De publiek-gelezen ingang verstrekt voorspelbare, op partij-gebaseerde verwerking die gemakkelijker is te beheren en te testen. Gebeurtenisgetriggerde invoer biedt realtime reactiesnelheid die contextueel relevanter is, maar die streaminginfrastructuur en zorgvuldiger beheer van terugkeer vereist.

- **publiek-Gelezen voorkeur:** Voorspelbaarheid, grote volumeverwerking, geplande levenscyclusprogramma&#39;s, eenvoudiger het testen
- **gebeurtenis-teweeggebrachte gunsten:** Realtime relevantie, gedragscontext, individueel profiel het afvangen, directe reactie op klantenacties
- **Aanbeveling:** publiek-gelezen van het gebruik voor geplande levenscyclusprogramma&#39;s (onboarding, vernieuwing) waar de timing zaken-gedreven is. Gebruik gebeurtenisactivering voor gedrags-responssequenties (het verlaten van het winkelwagentje, na aankoop) waarbij timing door de klant wordt bepaald.

#### Enkelkanaals versus meerkanaalsreis

Single Channel-reizen zijn eenvoudiger te implementeren, te testen en te beheren. Multikanaalreizen bieden een breder bereik en escalatiemogelijkheden, maar verhogen de complexiteit van het maken van inhoud, het beheer van toestemming en het beheer van frequenties.

- **Enig kanaal bevordert:** snellere implementatie, eenvoudiger toestemmingsbeheer, lagere inspanning van de inhoudsproductie, gemakkelijkere zuivering
- **Multikanaal voorkeur:** Hoger betrokkenheidspotentieel, kanaalescalatie voor niet-ontvankelijke profielen, uitvoerigere klantenervaring
- **Aanbeveling:** Begin met een enig-kanaals reis en bevestig de stroom en het bedrijfseffect alvorens aan multi-kanaal uit te breiden. Voeg kanalen incrementeel toe waar de betrokkenheidsgegevens laten zien dat het primaire kanaal niet effectief bij de doelgroep terechtkomt.

#### Complexiteit van reizen versus beheerbaarheid

Een hoogst vertakte reis met vele voorwaarden en wegen kan meer scenario&#39;s richten maar wordt moeilijker te testen, te zuiveren, en te optimaliseren. Een eenvoudiger traject met minder vertakkingen is eenvoudiger te beheren, maar kan een minder persoonlijke ervaring opleveren.

- **Complexe reizen begunstigen:** Korrelige verpersoonlijking, segment-specifieke wegen, uitvoerige scenariodekking
- **Eenvoudigere reizen begunstigen:** Snellere plaatsing, gemakkelijker het testen, duidelijkere rapportering, lagere onderhoudslast
- **Aanbeveling:** Beperk reizen tot 3-5 belangrijke takken en 15-25 activiteiten. Als de logica meer complexiteit vereist, kunt u overwegen om te splitsen in meerdere reizen met coördinatie over de reis in plaats van één enkele monolithische reis.

#### Strikte frequentiegrens versus voltooiing van de reis

Strikte frequentiecaps beschermen tegen overberichten, maar kunnen reisberichten onderdrukken, waardoor profielen stappen overslaan en tarieven voor het voltooien van de reis verminderen. Lenient caps zorgt ervoor dat reisberichten worden afgeleverd, maar dat er sprake is van vermoeidheid bij het risicokanaal.

- **Strikte kappen gunnen:** de ervaringsbescherming van de Klant, verlaagde tarieven unsubscript, merkvertrouwen
- **milde caps gunst:** de voltooiingstarieven van de reis, volledige levering van de berichtopeenvolging, de doeltreffendheid van het marketing programma
- **Aanbeveling:** wijs hogere prioritaire scores aan kritieke reisberichten (op het instappen, vernieuwing) toe zodat nemen zij belangrijkheid over promotiecampagnes wanneer de kappen worden bereikt. Reserve &quot;van het aftappen&quot;voor echt essentiële mededelingen slechts.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie over de mogelijkheden die in deze implementatie worden gebruikt.

### Journeys

- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Een reis maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journeyeigenschappen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [De reis publiceren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)
- [Uw reis testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)

### Reisactiviteiten

- [Lees de publieksactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Algemene gebeurtenissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [kwalificatiegebeurtenissen voor het publiek](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Voorwaardeactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wachtactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Een bericht toevoegen tijdens een rit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Eindactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/end-activity)
- [Een aangepaste handeling configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions)

### Toegang- en uitreisbeheer

- [Reisbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Afsluitingscriteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Kanaalconfiguratie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Kanaaloppervlakken instellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [IP-pools maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-opwarmingsplannen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Authoring en personalisatie van berichten

- [Een e-mail maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [E-mail Designer-inhoudsonderdelen gebruiken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helpfuncties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Inhoud testen

- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport voor inhoudexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistische berekeningen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Frequentie, conflict en prioriteit

- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Overzicht van bedrijfsregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Aan de slag met conflict- en prioriteitsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Afbakening van reizen en arbitrage](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)
- [Mogelijke conflicten identificeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Splitsen en segmenteren

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/api/edge-segmentation)

### Rapportage en analyse

- [Journaal live](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

### Toestemming en bestuur

- [Toestemming in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Onderdrukkingslijst beheren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Gegevensbasis

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Profieloverzicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
