---
title: Batch Outbound Message Activation
description: Leer hoe te om een publiek te evalueren en een gepland uitgaand bericht in één enkele partijuitvoering te leveren.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8246'
ht-degree: 0%

---


# Batchactivering van uitgaande berichten

Deze gids verstrekt een volledige implementatieverwijzing voor het leveren van geplande uitgaande berichten aan bepaalde publiekssegmenten gebruikend [!DNL Adobe Journey Optimizer] (AJO) en [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die alle haalbare implementatiemethoden, de beslissingsoverwegingen die elke keuze bepalen en waar u gedetailleerde documentatie vindt op [!DNL Adobe Experience League] .

De uitgaande berichtactivering van de partij is het fundamentele campagnerepatroon voor één-aan-vele uitgaand overseinen. Het behandelt de volledige levenscyclus van publieksdefinitie door berichtlevering en prestatiesanalyse. Deze handleiding bevat drie implementatieopties — Geplande campagne, Publiek-activering en API-activering van campagne — en biedt gestructureerde beslissingsbegeleiding voor het selecteren van de juiste aanpak voor elk gebruiksgeval.

Het biedt implementatieopties, afwegingsanalyse, UI-navigatiepaden en [!DNL Experience League] documentatieverwijzingen.

## Hoofdlettergebruik

De organisaties moeten vaak één enkel bericht aan een bekend publiekssegment op een bepaald ogenblik of in antwoord op een systeemgebeurtenis leveren. Met dit patroon wordt deze vereiste verholpen door publieksevaluatie in [!DNL RT-CDP] te combineren met het schrijven van berichten en het uitvoeren van campagnes in [!DNL Journey Optimizer] .

Het bedrijfsscenario is duidelijk: bepaal wie het bericht zou moeten ontvangen, creeer de berichtinhoud met verpersoonlijking, bindt het publiek en het bericht in een campagne of een reis, en voer verzenden op een programma, via publiekskwalificatie, of door een systeemtrekker uit. Het resultaat is een bezorgd bericht met volledige rapportering over levering, betrokkenheid, en omzettingsmetriek.

Dit patroon is van toepassing wanneer een bedrijfsdoelstelling kan worden geavanceerd door één enkel bericht aan een gekend publiek in één uitvoering te leveren. Het verschilt van gebeurtenis-teweeggebrachte overseinen, die aan gedragsgebeurtenissen in real time antwoordt, en van multi-step georkestreerde reizen, die profielen door veelvoudige touchpoints in tijd begeleiden. De activering van de partij is het eenvoudigste campagnepatroon en het gemeenschappelijkste uitgangspunt voor uitgaande overseinengebruiksgevallen.

## Belangrijkste bedrijfsdoelstellingen

Deze sectie identificeert de primaire bedrijfsdoelstellingen die de batch uitgaande berichtactivering steunt.

### Verhoog de betrokkenheid bij e-mail en campagnes

**Beschrijving:** verbeter open tarieven, klik-door tarieven, en algemene campagnereactie door geoptimaliseerde inhoud en het richten.

**KPIs:** Open Tarieven, Betrokkenheid, de Tarieven van de Omzetting

### Verhoog de omzet

**Beschrijving:** de top-line omzetgroei van de aandrijving door geoptimaliseerde digitale kanalen, campagnes, en klantenreizen.

**KPIs:** de Tarieven van de Omzetting, Incrementele Inkomsten, Gemiddelde Waarde van de Orde

**Verwante bedrijfsdoelstelling:** [&#x200B; de Inkomsten &amp; Verkoop van de Verhoging &#x200B;](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

### Uitvoering van campagne stroomlijnen

**Beschrijving:** verkort campagne bouwt tijd en vereenvoudigt multi-kanaalcampagnelevering door malplaatjes, automatisering, en gestandaardiseerde processen.

**KPIs:** Snelheid aan Markt, Efficiëntie, op tijd voltooide %

## Voorbeelden van tactische gebruiksgevallen

De volgende scenario&#39;s illustreren gemeenschappelijke toepassingen van partij uitgaande berichtactivering.

- **de aankondiging van de Verkoop of bevorderende e-mailontploffing** — Uitzending een promotieaanbieding aan een segment van in aanmerking komende klanten op een geplande datum
- **de lancerings dupmelding van het Product** — Deel geïnteresseerde klanten over een nieuwe productbeschikbaarheid door duw op de hoogte
- **Nieuwsbrief of samenvatting e-mail** — Lever periodieke inhoudafrondingen aan abonneepubliek
- **de registratieuitnodiging van de Gebeurtenis** - nodigt gekwalificeerde vooruitzichten aan webinars, conferenties, of gebeurtenissen uit
- **Herinnering e-mail van de vernieuwing van het Abonnement** — Herinneer klanten die vernieuwingsdata naderen om actie te ondernemen
- **het mijlpaal van het programma van de Loyalty bericht** — Gefeliciteerd leden die loyaliteitsrijen of puntdrempels bereiken
- **Specifieke e-mail van call-to-action** — aandrijving een gerichte actie zoals het voltooien van een aankoop, het bijwerken voorkeur, of het registreren voor een programma
- **campagne van SMS voor flitsverkoop of tijd-beperkte aanbieding** - verzend dringende, aan tijd gebonden bevorderingen via SMS naar opted-in publiek

## Kernprestatie-indicatoren

De volgende lijst bepaalt KPIs wordt gebruikt om campagnedoeltreffendheid te meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Leveringssnelheid | Percentage van berichten dat met succes aan ontvangers is geleverd | Geleverd/Verzonden x 100 |
| OpenRate | Percentage geleverde berichten die door ontvangers worden geopend | Unieke open/geleverde x 100 |
| Doorkliksnelheid (CTR) | Percentage geleverde berichten waar op een koppeling werd geklikt | Unieke klikken/Geleverd x 100 |
| Klikken-tot-Open Tarief (CTOR) | Percentage geopende berichten waar op een koppeling werd geklikt | Unieke klikken / Unieke open x 100 |
| Conversiesnelheid | Percentage ontvangers dat de gewenste actie heeft uitgevoerd | Omzettingen / Geleverd x 100 |
| Abonnement opzeggen | Percentage ontvangers die zich afmelden na ontvangst van het bericht | Abonnement opzeggen / Geleverd x 100 |
| Stuitsnelheid | Percentage van berichten dat niet kon worden geleverd | Stommen / Verzonden x 100 |
| Ontvangsten per verzonden e-mail | Ontvangsten die aan de campagne zijn toegerekend, gedeeld door verzonden berichten | Totale inkomsten/verzonden |

## Hoofdletterpatroon gebruiken

**uitgaande berichtactivering van de Partij**

Evalueer een publiek en lever vervolgens een gepland uitgaand bericht (e-mail, SMS, push) aan alle kwalificerende profielen in één batch-uitvoering.

**de ketting van de Functie:** de Evaluatie van het publiek > Authoring van het Bericht > de Uitvoering van de Campagne > het Melden

## Applicaties

Voor de implementatie van dit patroon worden de volgende toepassingen gebruikt.

- **[!DNL Adobe Journey Optimizer] (AJO)** — Het schrijven van berichten, kanaalconfiguratie, campagneuitvoering, reis orchestratie, inhoud experimenteren, frequentieregels, en rapportering
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Poortevaluatie, toestemming en handhaving van het bestuur
- **[!DNL Adobe Experience Platform] (AEP)** — De opslag van het profiel, de identiteitsdienst, schema&#39;s, datasets, gegevensinzameling

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary Function | Status | Wat moet er gebeuren? | Experience League Reference |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | AJO-sandbox met een actieve kanaalconfiguratie. Het verzenden van subdomein gemachtigde, toegewezen IP pool, en IP warmte-up volledig. Gebruikersrollen met toegewezen machtigingen voor het maken van campagne/reizen. | [&#x200B; het overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [&#x200B; overzicht van de Toegangscontrole &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | Schema voor individueel XDM-profiel met kenmerken die worden gebruikt voor segmentatie en personalisatie (bijvoorbeeld naam, e-mail, voorkeuren, laag). XDM ExperienceEvent-schema waarin de doelconversieactie (bijv. `commerce.purchases`, `web.webInteraction` ) wordt vastgelegd voor het bijhouden van de conversie na de campagne. Profiel-toegelaten datasets voor beide schema&#39;s. | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [&#x200B; de samenstellingsgrondbeginselen van het Schema &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Gegevensbronnen en -verzameling | Verondersteld op plaats | Web SDK of Analytics tagging op de CTA-bestemming moet actief zijn om conversiegebeurtenissen vast te leggen. Streaming- of batch-innamepijpleidingen voor profielkenmerken moeten operationeel zijn. | {het overzicht van SDK van 0} Web [&#128279;](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [&#x200B; Bronoverzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identiteit en profielconfiguratie | Verondersteld op plaats | Naamruimten voor e-mailadressen (en eventuele id&#39;s voor andere apparaten) geconfigureerd. Profielkenmerken die vereist zijn voor personalisatie die tijdens het verzenden is toegewezen, opgenomen en oplosbaar. Beleid voor samenvoegen geconfigureerd. | [&#x200B; overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [&#x200B; overzicht van het beleid van de Fusie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Auditiedefinitie en segmentatie | Vereist | Het publiek van het doel dat in rt-CDP wordt bepaald gebruikend de Bouwer van het Segment of de Samenstelling van het Publiek. Publiek gepubliceerd en geëvalueerd met een populatie die niet gelijk is aan nul. Omvat in uitvoeringsfase 1 via RT-CDP Audience Evaluation. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [&#x200B; de gids UI van de Bouwer van het Segment &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League Reference |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Berekende kenmerken, zoals dagen sinds laatste aankoop, aantal levenslange bestellingen of betrokkenheidsscore, verbeteren de nauwkeurigheid van het publiek en maken een rijkere personalisatie van berichten mogelijk. | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Het beleid van het behoud van gegevens (afloop) zou op zijn plaats voor gebeurtenisdatasets moeten zijn die conversie het volgen drijven. De gebieden van het toestemmingsschema moeten voor kanaal-vlakke opt-in/opt-out handhaving worden gevormd. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [&#x200B; Toestemming en de groep van het voorkeurengebied &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | Regelgevingslabels op PII-velden die worden gebruikt voor personalisatie zorgen ervoor dat tijdens de activering aan de vereisten wordt voldaan. Voorkomt ongeoorloofd gebruik van gevoelige profielgegevens in berichtinhoud of publieksuitvoer. | [&#x200B; het beheer van Gegevens overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [&#x200B; overzicht van de gebruiksetiketten van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Bewaking en waarneming | Opgenomen | In real time verzendt controle deel van de Rapporterende fase. Waarschuwing op platformniveau over fouten met inname of gebruik van licenties biedt operationele zichtbaarheid die verder gaat dan metingen op campagnereniveau. | [&#x200B; overzicht van de Inzichten van de Waarneming &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [&#x200B; het overzicht van Alarm &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Rapportage en analyse | Opgenomen | Campagne- en reisverslagen worden behandeld in de rapportagefase. Voor een diepere kanaalanalyse, verstrekt de integratie van CJA funnel analyse, attributiemodellering, en cohortanalyse voorbij AJO ingebouwde rapporten. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [&#x200B; AJO + de integratiegids van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de catalogus van de toepassingsfunctie uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer] (AJO)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Kanaalconfiguratie | Fase 2: Kanaalconfiguratie | Vorm of bevestig de kanaaloppervlakte (e-mail, SMS, of duw) met inbegrip van subdomain, IP pool, afzendermontages en onderdrukkingslijst |
| Berichtontwerp | Fase 3: Berichtgeving | Berichtinhoud maken met behulp van sjablonen, de e-mail-Designer, personalisatie-expressies, voorwaardelijke inhoudsblokken en inhoudsfragmenten |
| Campagne uitvoeren | Fase 4: Campagne of Reiscreatie | Creeer, vorm, en activeer een geplande of API-teweeggebrachte campagne die publiek, bericht, en uitvoeringsprogramma bindt |
| Inhoud experimenteren | Fase 4: Campagne of Reiscreatie | Configureer desgewenst A/B of experimenten met meerdere inhoud om de berichtprestaties te optimaliseren |
| Frequentie en bedrijfsregels | Fase 4: Campagne of Reiscreatie | Pas optioneel regels voor frequentiecontrole toe om overseinen over gezamenlijke campagnes te verhinderen |
| Conflict- en prioriteitsbeheer | Fase 4: Campagne of Reiscreatie | Prioriteitsscores toewijzen en conflictoplossing configureren wanneer meerdere campagnes gericht zijn op overlappend publiek |
| Rapportage en prestatieanalyse | Fase 5: Rapportage en prestatieanalyse | De leveringsmetriek van de monitor via levende rapporten tijdens uitvoering en analyseert campagneprestaties via historische rapporten na voltooiing |

### [!DNL Real-Time CDP] (RT-CDP)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Fase 1: Evaluatie van het publiek | Bepaal publieksregels gebruikend de Bouwer van het Segment of de Samenstelling van het Publiek, selecteer de evaluatiemethode (partij, het stromen, of rand), en bevestig publiekspopulatie |
| Goedkeuring en handhaving van bestuur | Fase 1: Evaluatie van het publiek | Voorkeuren voor toestemming en beleid voor gegevensgebruik afdwingen om ervoor te zorgen dat alleen profielen met toestemming het campagnebericht ontvangen |

## Vereisten

Voltooi het volgende voordat u begint met de implementatie.

- AJO-sandbox is ingericht en actief
- Het verzenden van subdomein wordt gedelegeerd en geverifieerd (SPF, DKIM, DMARC geconfigureerd)
- IP de pool wordt toegewezen en opgewarmd voor productie verzendend volume
- Er is minstens één actief kanaaloppervlak (e-mail, SMS of push) aanwezig
- Gebruikersaccounts beschikken over machtigingen voor het maken van campagnes/reizen en voor het schrijven van inhoud
- Het XDM-profielschema bevat kenmerken die nodig zijn voor publiekssegmentatie en berichtpersonalisatie
- Met het XDM-gebeurtenisschema worden conversiegebeurtenissen vastgelegd voor bijhouden na de campagne
- Profielgegevens worden ingevoerd en samengevoegd via Identity Service
- Web SDK of Analytics tagging is actief op de CTA-doelpagina om conversiegebeurtenissen vast te leggen
- De gebieden van de toestemming worden bevolkt op profielen voor het doel overseinenkanaal
- Inhoud (afbeeldingen, logo&#39;s, richtlijnen voor het merk) is beschikbaar voor het ontwerpen van berichten

## Implementatieopties

In deze sectie worden drie implementatieopties voor batchactivering van uitgaande berichten beschreven, samen met een vergelijkings- en beslissingsbegeleiding.

### Optie A: Geplande campagne (eenmalige verzending)

**Best voor:** Datum-verankerd verzendt — verkoopaankondigingen, productlanceringen, de termijnen van de gebeurtenisregistratie, hernieuwingsherinneringen, nieuwsbrief blasten, en om het even welke send waar de uitvoeringsdatum vooraf gekend is.

**hoe het werkt:**

Een geplande campagne is de eenvoudigste variant van partij uitgaand overseinen. De markeerteken definieert het doelpubliek, ontwerpt de inhoud van het bericht, stelt een verzenddatum en -tijd in en activeert de campagne. Op de geplande uitvoeringstijd evalueert AJO het publiek om de huidige in aanmerking komende populatie te bepalen en stuurt het bericht vervolgens naar alle in aanmerking komende profielen in één batch.

De volledige configuratie gebeurt binnen de interface van de Campagnes van AJO — er is geen wegcanvas, geen vertakkende logica, en geen wachtende stappen. Dit maakt geplande campagnes het snelst om te vormen en het gemakkelijkst te leiden. De campagne kan worden ingesteld voor onmiddellijke uitvoering, een specifieke datum/tijd in de toekomst of een terugkerend schema (dagelijks, wekelijks, maandelijks).

**Zeer belangrijke overwegingen:**

- Het publiek wordt geëvalueerd op het moment van uitvoering, zodat profielen die tussen planning en uitvoering in aanmerking komen, worden opgenomen
- Er is geen vertakking, wachttijd of voorwaardelogica beschikbaar — het bericht wordt aan alle kwalificerende profielen geleverd
- Ondersteunt het rechtstreeks experimenteren met inhoud (A/B-tests) binnen de campagneconfiguratie
- Campagneeigenschappen bevatten een prioriteitsscore voor het oplossen van conflicten met andere campagnes

**Voordelen:**

- Eenvoudige configuratie met de minste overhead
- Snellste tijd-aan-lancering voor ongecompliceerde partij verzendt
- Ingebouwde ondersteuning voor terugkerende planningen
- Inhoud experimenteren wordt op native ondersteuning ondersteund
- Publiek opnieuw geëvalueerd tijdens uitvoeringstijd voor versheid

**Beperkingen:**

- Geen wachtstappen, voorwaarden of vertakking voor levering
- Kan niet reageren op profielgedrag tussen planning en uitvoering
- Alleen actie voor één bericht — geen multi-touchsequenties
- Kan niet bewerken nadat geactiveerd (moet worden gedupliceerd en gewijzigd)

**Experience League:**

- [Aan de slag met campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Optie B: Reis door het publiek geactiveerd

**Best voor:** Gedrag-gedreven verzendt — verlaten kartberichten, de herinneringen van de proefvervaldatum, mijlpaalfakanalen, op kwalificatie-gebaseerde outreach, en om het even welke send waar de trekker publiekskwalificatie of een bedrijfsgebeurtenis eerder dan een kalenderdatum is.

**hoe het werkt:**

Een door het publiek geïnitieerde reis gebruikt het reiscanvas om een bericht te leveren wanneer een profiel voor een bepaald publiek kwalificeert of een kwalificerende gebeurtenis in brand steekt. De ingang van de reis wordt teweeggebracht door de veranderingen van het publiekslidmaatschap (profielen die het publiek ingaan) eerder dan een vast programma. Het reiscanvas staat facultatieve wachtstappen, voorwaardentakken, en onderdrukkingslogica vóór de berichtactie toe, die meer flexibiliteit dan een geplande campagne verstrekken.

De reis wordt gevormd in de interface van de Reizen van AJO gebruikend de Gelezen de ingangsgebeurtenis van het Publiek. Als profielen in aanmerking komen voor het publiek, gaan ze de reis in en gaan ze door de canvasknooppunten. Een eenvoudige implementatie kan slechts één e-mailactieknooppunt bevatten, waardoor het functioneel vergelijkbaar is met een geplande campagne maar met een toegangstijdstip gebaseerd op publiekskwalificatie. Complexere implementaties kunnen wachtknooppunten toevoegen (bijvoorbeeld wachten 24 uur na kwalificatie), voorwaardenknooppunten (bijvoorbeeld controleren of het profiel een vorige e-mail heeft geopend) of suppressielogica vóór de berichtlevering.

**Zeer belangrijke overwegingen:**

- De ingang van de reis wordt teweeggebracht door publiekskwalificatie, niet een kalenderdatum
- Het reiscanvas ondersteunt wachttijden, voorwaarden en gesplitste knooppunten voor logica vóór levering
- Regels voor het opnieuw betreden van een reis bepalen of profielen de reis meerdere keren kunnen invoeren
- De montages van de arbitrage van de reis bepalen gedrag wanneer een profiel reeds in een concurrerende reis is

**Voordelen:**

- Flexibele ingstijdstip op basis van kwalificatie van het publiek in plaats van vaste planning
- Wachten en voorwaardenknooppunten toestaan logica vóór levering (bijvoorbeeld vertraging, controle, onderdrukken)
- Met besturingselementen voor opnieuw invoeren voorkomt u dat dubbel wordt verzonden naar hetzelfde profiel
- Kan worden uitgebreid tot een meerstapsreis als de gebruikscase zich ontwikkelt
- Steunt reis-vlakke rapportering met ingang, uitgang, en knoop-vlakke metriek

**Beperkingen:**

- Meer configuratieoverhead dan een geplande campagne
- Het canvas van de reis voegt ingewikkeldheid zelfs voor de kwesties van het enig-berichtgebruik toe
- Reis moet worden gepubliceerd en kan niet worden bewerkt tijdens live (moet een nieuwe versie maken)
- Het aantal profielen dat binnen een tijdvenster wordt ingevoerd, kan worden beperkt door de functie voor het toewijzen van toegang

**Experience League:**

- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Reis van het publiek lezen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Optie C: API-gestuurde campagne

**het Best voor:** systeem-in werking gestelde verzendt — de bevestiging van de orde met upsell inhoud, de follow-ups van de steunkaartenresolutie, transactionele berichten met marketing inhoud, en om het even welk verzendt waar de het teweegbrengen gebeurtenis van een extern systeem op een specifiek ogenblik voortkomt.

**hoe het werkt:**

Een API-getriggerde campagne wordt geactiveerd via een REST API-aanroep op het moment dat een activerende systeemgebeurtenis plaatsvindt. De campagne is vooraf geconfigureerd in AJO met berichtinhoud en kanaalinstellingen, maar in plaats van een vooraf gedefinieerd publiek te binden, geeft de API-aanroep de ontvangende profielen op en kan contextuele gegevens doorgeven die dynamische berichtparameters vullen.

Deze variant is ideaal wanneer de verzendtiming wordt bepaald door een extern systeem (bijvoorbeeld een orderbeheersysteem, een CRM-workflow of een ondersteuningsplatform) in plaats van door een publieksevaluatie of een agenda. Contextuele gegevens die in de API triggerlading worden doorgegeven (zoals orderdetails, kaartnummers of productnamen) kunnen de inhoud van het bericht personaliseren met gebruik van contextafhankelijke kenmerken die niet in het profiel zijn opgeslagen.

**Zeer belangrijke overwegingen:**

- Geen vooraf gebonden publiek vereist — ontvangers worden opgegeven in de API-triggeraanvraag
- Contextuele gegevens in de triggerlading maken dynamische personalisatie mogelijk die verder gaat dan profielkenmerken
- De campagne moet van het type &quot;API-teweeggebracht&quot;zijn en moet worden geactiveerd alvorens het triggerverzoeken kan ontvangen
- Elke API-triggeraanvraag ondersteunt maximaal 20 profielontvangers
- De Evaluatie van het publiek (Fase 1) kan worden overgeslagen aangezien de ontvangers uit de API vraag komen

**Voordelen:**

- Real-time activeren van externe systemen op het moment van de gebeurtenis
- Contextuele personalisatie met gegevens die niet in het profiel worden opgeslagen (orderdetails, kaartinformatie)
- Geen overhead voor publieksevaluatie — ontvangers worden direct opgegeven
- Steunt transactie + marketing hybride overseinen

**Beperkingen:**

- Vereist externe systeemintegratie om de API-trigger te verzenden
- Maximaal 20 ontvangers per API-triggeraanvraag
- Geen ingebouwde publieksevaluatie — het roepende systeem moet ontvangers bepalen
- Meer technische complexiteit door vereisten voor API-integratie
- Inhoud-experimenteren wordt niet ondersteund voor API-gestuurde campagnes

**Experience League:**

- [API-gestuurde campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Campagnes activeren met API&#39;s](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Optievergelijking

In de volgende tabel worden de drie implementatieopties vergeleken met de belangrijkste criteria.

| Criteria | Optie A: geplande campagne | Optie B: Publiek teweeggebrachte reis | Optie C: API-activering |
| --- | --- | --- | --- |
| Best voor | Datum-verankerd verzendt (bevorderingen, lanceringen, nieuwsbrieven) | Gedragsgestuurd verzenden (kwalificatiegebeurtenissen, mijlpalen) | Door het systeem geïnitieerde verzending (orderbevestigingen, transactioneel) |
| Complexiteit | Laag | Gemiddeld | Medium-High |
| Type trigger | Kalenderdatum/-tijd of terugkerend schema | Poortkwalificatie of bedrijfsgebeurtenis | API-aanroep van extern systeem |
| Logica vóór levering | Geen | Wacht, voorwaarde, gesplitste knooppunten beschikbaar | Geen (logica in aanroepend systeem) |
| Poortbinding | Vooraf gedefinieerd RT-CDP-publiek | Vooraf gedefinieerd RT-CDP-publiek | Ontvangers opgegeven in API-payload |
| Contextuele gegevens | Alleen profielkenmerken | Alleen profielkenmerken | Profielkenmerken + API-laadgegevens |
| Inhoud testen | Ondersteund | Ondersteund (actie bij bericht) | Niet ondersteund |
| Frequentiecorrectie | Ondersteund | Ondersteund | Ondersteund |
| Terugnamecontrole | N.v.t. (eenmalige uitvoering) | Configureerbare terugkeerregels | N.v.t. (per aanvraag) |
| Configuratie-interface | AJO Campaigns | AJO-reizen | AJO-campagnes + extern systeem |
| Vereisten | Publiek, kanaaloppervlak, bericht | Publiek, kanaaloppervlak, bericht, reiscanvas | Kanaaloppervlak, bericht, API-integratie |

### Kies de juiste optie

Gebruik de volgende beslissingsstroom om de juiste implementatieoptie te selecteren:

1. **wordt verzonden teweeggebracht door een externe systeemgebeurtenis (b.v., geplaatste orde, opgelost kaartje)?** Als ja, kies **Optie C: API-Teweeggebrachte Campagne**. Dit is de enige optie die door het systeem geïnitieerde triggers met contextafhankelijke ladingsgegevens ondersteunt.

2. **is verzend verankerd aan een specifieke kalenderdatum of terugkerend programma?** Als ja, kies **Optie A: Geplande Campagne**. Dit is het eenvoudigst en snelst om voor datum-gedreven te vormen verzendt.

3. **verzendt behoefte om aan publiekskwalificatie te reageren of pre-leveringslogica (wacht, voorwaarde, onderdrukking) te vereisen?** Als ja, kies **Optie B: Publiek-teweeggebrachte Reizen**. Het reiscanvas biedt de flexibiliteit voor door gedrag gestuurde instap- en leveringsbeslissingslogica.

4. **is verzendt een eenvoudige uitzending naar een bekend publiek zonder speciale timing of logische vereisten?** Kies **Optie A: Geplande Campagne** voor de laagste configuratieoverheadkosten.

## Uitvoeringsfasen

In deze sectie wordt elke uitvoeringsfase in detail doorlopen, met inbegrip van beslissingspunten en optiespecifieke richtsnoeren.

### Fase 1: Evalueer het publiek

**functie van de Toepassing:** rt-CDP: de Evaluatie van het publiek

Deze fase bepaalt en evalueert het doelpubliekssegment dat de campagneboodschap zal ontvangen. Het bepaalt welke profielen voor verzenden op profielattributen, gedragssignalen, en suppressieregels in aanmerking komen.

>[!NOTE]
>Voor optie C (API-activering) kan deze fase worden overgeslagen als de ontvangers volledig zijn opgegeven in de payload van de API-trigger. Zelfs API-getriggerde campagnes hebben echter baat bij een onderdrukkend publiek om profielen uit te filteren die geen berichten mogen ontvangen.

#### Besluit: criteria voor het publiek

Welke voorwaarden bepalen het doelpubliek? Welke suppressieregels moeten profielen uitsluiten?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Profiel, op kenmerk gebaseerd publiek | Het doelpubliek wordt gedefinieerd door demografische kenmerken, voorkeuren of statuskenmerken | Eenvoudig te bouwen; steunt alle evaluatiemethodes |
| Op gedrag gebaseerde publiek | Het doelpubliek wordt gedefinieerd door acties die binnen een tijdvenster worden uitgevoerd (of niet worden uitgevoerd) | Vereist gegevensinvoer in een gebeurtenis; volgens tijdsperiodes is het mogelijk dat streaminggeschiktheid wordt beperkt |
| Audience Composition (afgeleid publiek) | Het doelpubliek vereist rang, spleet, sluit, of verrijkt verrichtingen over veelvoudige bronpubliek uit | Krachtigere maar partij-slechts evaluatie; beperkt tot 10 samenstellingen per zandbak |

#### Besluit: Evaluatiemethode

Hoe snel moet het publiek bijwerken om nieuwe kwalificerende of diskwalificerende profielen te weerspiegelen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Batchevaluatie | Geplande campagnes waarbij de versheid van het publiek binnen een dag acceptabel is; groot, complex publiek | Standaard voor de meeste segmenttypes; processen op een dagelijks programma of op bestelling; steunt alle functies van de segmentregel |
| Streaming evaluatie | Publiek-getriggerde reizen waarbij profielen bijna realtime moeten ingaan als ze in aanmerking komen | Automatisch voor kwalificerende uitdrukkingen van de segmentregel; niet alle segmenttypes komen voor het stromen in aanmerking; dichtbij-real-time latentie (seconden aan notulen) |
| Edge-evaluatie | Niet standaard voor dit patroon (wordt gebruikt voor personalisatie op dezelfde pagina) | Beperkte segmentregelondersteuning; milliseconde latentie; alleen relevant in combinatie met webpersonalisatiepatronen |

#### Besluit: Samenvoegingsbeleid

Welk samenvoegbeleid zou het publiek moeten gebruiken om profielfragmenten op te lossen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Standaardsamenvoegbeleid (tijdstempel geordend) | Meest voorkomende gebruiksgevallen van batchcampagnes | Recentste kenmerkwaarde wint; norm voor uitgaande overseinen |
| Aangepast samenvoegingsbeleid (prioriteit gegevensset) | Wanneer een specifieke gegevensbron prioriteit moet krijgen voor sleutelkenmerken | Nuttig wanneer CRM-gegevens voor bepaalde velden de via het web verzamelde gegevens moeten overschrijven |

#### UI-navigatie

Klant > Soorten publiek > Deelvenster maken > Regel maken

#### Belangrijkste configuratiedetails

- Bepaal het publiek gebruikend de Bouwer van het Segment met segmentregels voor profielattributen, gedragsgebeurtenissen, en segmentlidmaatschap
- Pas onderdrukkingsregels toe om profielen uit te sluiten die al zijn omgezet, onlangs een gelijkaardig bericht hebben ontvangen of uit hebben gekozen
- Controleren of het publiek een populatie heeft die niet gelijk is aan nul voordat u verdergaat
- Voor partijcampagnes, verzeker een programma van de segmentevaluatie actief is of op bestelling evaluatie teweegbrengt
- Bevestig toestemmingsgebieden (`consents.marketing.email.val`, `consents.marketing.sms.val`, enz.) zijn gevuld en afgedwongen

#### Waar opties afwijken

**voor Optie A (Geplande Campagne):**

Batchevaluatie is typisch. Het publiek wordt opnieuw geëvalueerd op het moment dat de campagne wordt uitgevoerd, zodat de meest recente gekwalificeerde populatie doelgericht is. Definieer het publiek en controleer de bevolking en ga vervolgens door met het maken van campagnes.

**voor Optie B (publiek-teweeggebrachte reis):**

De evaluatie van het stromen wordt geprefereerd zodat gaan de profielen de reis in aangezien zij kwalificeren. Zorg ervoor dat de expressie van de segmentregel streaming-in aanmerking komt (eenvoudige gebeurtenistriggers, kenmerkvergelijkingen, beperkte tijdvensters). Configureer het publiek en controleer of de streamingkwalificatie actief is.

**voor Optie C (API-teweeggebrachte Campagne):**

De evaluatie van het publiek kan volledig worden overgeslagen. Indien gebruikt, creeer een onderdrukkend publiek aan filterprofielen die niet het bericht zouden moeten ontvangen (b.v. onlangs unsubscribed, reeds omgezet). Het roepende systeem bepaalt de primaire ontvangers.

#### Experience League-documentatie

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Samenstelling publiek](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/pql/overview)

### Fase 2: Het kanaal configureren

**functie van de Toepassing:** AJO: De Configuratie van het Kanaal

Deze fase bevestigt of leidt tot de kanaaloppervlakte (vooraf ingesteld) die de verzendende infrastructuur voor het bericht - subdomain, IP pool, afzenderidentiteit, antwoord-aan adres, en unsubscribe montages bepaalt. Een geldig kanaaloppervlak moet bestaan voordat de berichtinhoud kan worden geschreven of campagnes kunnen worden geactiveerd.

#### Besluit: Doelkanaal

Welk overseinenkanaal zal het campagnebericht leveren?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| E-mail | Meest gebruikte soorten campagnes — nieuwsbrieven, promoties, meldingen, verlengingen | Vereist gemachtigde subdomain, verwarmde IP pool, afzenderidentiteit, en unsubscribe configuratie |
| Sms | Tijdgevoelige of korte berichten — flash-verkoop, aanstellingsherinneringen, OTP-codes | Vereist de geloofsbrieven van de leverancier van SMS (Sinch, Twilio, of Infobip); hogere per berichtkosten; strengere toestemmingsvereisten |
| Pushmelding | Mobiel betrokken publiek — app-updates, locatiegebaseerde aanbiedingen, in-app functieaankondigingen | Vereist APNs (iOS) en/of FCM (Android) geloofsbrieven; de gebruikers moeten app hebben geïnstalleerd met verleende duptoestemmingen |

#### Besluit: selectie van kanaaloppervlak

Bestaat er al een geschikt kanaaloppervlak in de sandbox of moet er een nieuw oppervlak worden gemaakt?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Bestaande oppervlak opnieuw gebruiken | Een geverifieerd, actief oppervlak komt overeen met het vereiste subdomein, de identiteit van de afzender en het kanaaltype | Snelste weg; geen DNS of warmteconfiguratie nodig |
| Nieuw oppervlak maken | Geen bestaande oppervlakte past vereisten aan, of een nieuwe subdomein/afzenderidentiteit wordt vereist | Vereist subdomain delegatie, DNS controle, IP pool taak, en potentieel IP warmte-up (2-4 weken voor nieuwe IPs) |

#### Besluit: Afhandeling van abonnement opzeggen

Hoe moet opt-out worden beheerd op het kanaaloppervlak?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Een-klik lijst-unsubscribe kopbal | Norm voor alle marketing e-mails; die door belangrijke ISPs (Gmail, Yahoo) voor leverability worden vereist | Voegt een mailto toe: of op URL gebaseerde unsubscribe kopbal die ISPs oppervlakte als &quot;Unsubscribe&quot;knoop |
| Koppeling in e-mailhoofdtekst opzeggen | Vereist als fallback voor e-mailclients die geen ondersteuning bieden voor headers voor het opzeggen van abonnementen in lijsten | Koppelingen voor opzeggen opnemen in de e-mailvoettekst naast de header voor het opzeggen van een abonnement |
| Beide (aanbevolen) | Beste praktijken voor alle marketing e-mails | Maximale nalevingsdekking en best-leverbaarheidsprofiel |

#### UI-navigatie

Beheer > Kanalen > Kanaaloppervlakken > Oppervlak maken (of selecteer bestaand)

#### Belangrijkste configuratiedetails

- Voor e-mail: bind het verzendende subdomain, IP pool, de naam van de afzender, de afzender e-mail, antwoord-aan adres, en adres BCC (als de controle exemplaar wordt vereist)
- Voor SMS: configureer de referenties van de SMS-provider en de instellingen voor korte of lange code
- Voor push: configureer APN&#39;s en/of FCM-referenties met het certificaat of de serversleutel van de app
- Controleer of het kanaaloppervlak de status Actief heeft voordat u verdergaat
- Bevestig DNS verslagen (SPF, DKIM, DMARC) correct voor het verzendende subdomain worden gevormd
- De suppressielijst bekijken voor items met een schaal; opschonen voor activering

#### Experience League-documentatie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [IP-pools maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-opwarmingsplannen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Instellingen van e-mailoppervlak](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Onderdrukkingslijst beheren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Fase 3: Bericht auteur

**functie van de Toepassing:** AJO: De Authoring van het Bericht

Deze fase leidt tot de berichtinhoud die aan het publiek zal worden geleverd. Het omvat het selecteren of het creëren van een inhoudsmalplaatje, het ontwerpen van de berichtlay-out, het toevoegen van verpersoonlijking gebruikend profielattributen, het vormen van voorwaardelijke inhoudsblokken voor publiek-specifieke variaties, het creëren van herbruikbare inhoudsfragmenten, en het voorvertonen van/het testen van het bericht met steekproefprofielen.

#### Besluit: Inhoudsaanpak

Hoe moet de inhoud van het bericht worden gemaakt?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Starten met bestaande sjabloon | Merk-goedgekeurde malplaatjes bestaan en aanpassen het berichttype (promotioneel, transactie, nieuwsbrief) | Snelste ontwerppad; zorgt voor consistentie tussen merken; sjablonen zijn sandbox-specifiek |
| Ontwerpen vanaf nul | Er bestaat geen geschikte sjabloon of het bericht vereist een unieke indeling | Meer flexibiliteit maar meer moeite; denk sparen als malplaatje voor hergebruik |
| HTML importeren | Berichtontwerp is extern gemaakt (bijvoorbeeld in een ontwerpgereedschap) en HTML is gereed voor import | Behoudt extern ontwerp; heeft mogelijk aanpassingen nodig voor AJO-compatibiliteit en personalisatietokens |

#### Besluit: diepte Personalization

Welke profielattributen zouden het bericht moeten personaliseren, en zijn voorwaardelijke nodig inhoudsblokken?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Basisverpersoonlijking (naam, begroeting) | Eenvoudige campagnes waarbij algemene inhoud met een gepersonaliseerde aanhef volstaat | Lage inspanning; minimaal risico van teruggevende kwesties; gebruikt standaardprofielattributen |
| Op kenmerken gebaseerde personalisatie | Berichtinhoud varieert op basis van profielkenmerken (laag, voorkeur, locatie) | Vereist geverifieerde XDM-paden; test met meerdere profielen om ervoor te zorgen dat alle variaties correct worden gerenderd |
| Voorwaardelijke inhoudsblokken | De verschillende inhoudssecties moeten aan verschillende publiekssegmenten binnen het zelfde bericht worden getoond | Complexere creatie; voor elke voorwaarde is een standaardfallback vereist; test alle permutaties |
| Contextuele personalisatie (alleen Optie C) | API-getriggerde campagnes moeten gegevens renderen die worden doorgegeven in de triggerlading (orderdetails, kaartinformatie) | Contextuele kenmerken worden niet opgeslagen in het profiel. Definieer plaatsaanduidingen in het bericht en wijs deze toe aan payload-velden |

#### Besluit: Fragmentstrategie

Moeten gedeelde inhoudsblokken worden gemaakt als herbruikbare fragmenten?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Herbruikbare fragmenten | Kopteksten, voetteksten, juridische disclaimers of afmelden blokken worden via meerdere campagnes gedeeld | Wijzigingen in een fragment worden doorgegeven aan alle berichten die ernaar verwijzen (live en concept); maximaal 30 fragmenten per bericht |
| Inline-inhoud | Eenmalig bericht zonder gedeelde elementen in andere campagnes | Eenvoudiger inhoud voor eenmalig gebruik; geen vermeerderingsrisico |

#### UI-navigatie

Campagnes > Selectiecampagne > Inhoud bewerken > Designer e-mailen (of SMS/Push-editor)

#### Belangrijkste configuratiedetails

- Ontwerp de berichtlay-out gebruikend belemmering-en-dalingsinhoudcomponenten (tekst, beeld, knoop, verdeler, kolommen)
- De eigenschappen van de e-mailkoptekst instellen: onderwerpregel, voorkoptekst en oppervlak van de afzender
- Verpersoonlijkingsexpressies invoegen met behulp van de syntaxis Handlebars (bijvoorbeeld `{{profile.person.name.firstName}}`)
- Helperfuncties voor opmaak configureren (datum, nummer, tekenreeksmanipulatie)
- Voorwaardelijke inhoudsregels toevoegen om verschillende inhoud weer te geven op basis van profielkenmerken of segmentlidmaatschap
- Standaardfallback-inhoud configureren als aan geen voorwaarden wordt voldaan
- Voor SMS stelt u de hoofdtekst van het bericht samen binnen de overwegingen voor de tekenlimiet
- Configureer voor push titel, tekst, afbeelding en handeling (diepe koppeling of URL)
- Een voorvertoning weergeven van het bericht met voorbeeldprofielen om de weergave op maat te controleren
- Proef-e-mails ter controle verzenden aan interne belanghebbenden
- Rendering testen tussen e-mailclients met de functie voor het renderen van e-mail

#### Experience League-documentatie

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
- [E-mailproefdrukken verzenden](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [E-mailrendering](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)
- [Een SMS-bericht maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Een pushmelding ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Fase 4: Maak een campagne of reis

**functie van de Toepassing:** AJO: De Uitvoering van de campagne (Opties A en C) of AJO: Journey Orchestration (Optie B)

Deze fase leidt tot de campagne of de reis die het publiek, het bericht, en het uitvoeringsmechanisme in een te leveren eenheid bindt. Op dit punt lopen de drie implementatieopties het meest uiteen.

#### Besluit: experimenten met inhoud

Moet de campagne een A/B test of multivariate experiment omvatten om berichtprestaties te optimaliseren?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Geen experiment | Enige berichtvariant met hoge betrouwbaarheid in inhoudsdoeltreffendheid | Eenvoudige configuratie; snelste activering |
| A/B-test (2 varianten) | Het testen van onderwerpregel, CTAs, of inhoudslay-outs met een duidelijke hypothese | Gesplitst verkeer 50/50 of met een gewogen toewijzing; vereist voldoende publieksgrootte voor statistische significantie |
| Multivariatietest (3+ varianten) | Meerdere inhoudselementen tegelijk testen | Vereist een groter publiek; langere duur om betrouwbaarheidsdrempel te bereiken; maximaal 10 behandelingen per experiment |

#### Besluit: frequentiebeperking

Moet deze campagne de wereldwijde regels voor frequentiecontrole respecteren om overberichten te voorkomen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Frequentieregels toepassen | De campagne maakt deel uit van een breder overseinenprogramma met veelvoudige gezamenlijke verzendt | Voorkomt vermoeidheid bij klanten; profielen die de limiet overschrijden, worden onderdrukt uit levering |
| Vrijstellen van aftopping | De campagne is tijd-kritiek of transactie en moet alle kwalificerende profielen ongeacht recente berichtgeschiedenis bereiken | Maak spaarzaam gebruik; het vrijstellen van campagnes van frequentieregels brengt het risico over overseinen |

#### Besluit: Prioriteitsscore

Welk prioriteitsniveau moet deze campagne hebben ten opzichte van andere actieve campagnes?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Hoge prioriteit (75-100) | Kritieke campagnes — grote productlanceringen, aanbiedingen in beperkte tijd, kennisgevingen van regelgeving | Heeft voorrang op campagnes met lagere prioriteit wanneer er conflicten ontstaan |
| Prioriteit Medium (25-74) | Standaardmarketingcampagnes — nieuwsbrieven, betrokkenheidscampagnes, algemene promoties | Evenwicht tegen andere campagnes; kan worden onderdrukt als een campagne met hogere prioriteit conflicten veroorzaakt |
| Lage prioriteit (0-24) | Aangenaam verzendt — informatieve updates, secundaire promoties | Zal worden onderdrukt ten gunste van campagnes met hogere prioriteit |

#### Waar opties afwijken

**voor Optie A (Geplande Campagne):**

**navigatie UI:** Campagnes > Create Campagne > Gepland > Marketing

1. Nieuwe geplande marketingcampagne maken
2. Selecteer het doelpubliek in de publiekskiezer
3. Selecteer het kanaaloppervlak en koppel de geschreven berichtinhoud
4. Configureer het uitvoeringsschema: onmiddellijk, specifieke datum/tijd of terugkerend
5. Schakel desgewenst inhoudexperimenten in en definieer behandelingsvarianten
6. Vorm facultatief frequentietoewijzing en prioritaire score
7. Controleer de volledige campagneconfiguratie
8. De campagne activeren

**voor Optie B (publiek-teweeggebrachte reis):**

**navigatie UI:** de Reizen > creëren Reis

1. Een nieuwe reis maken met een entry-event &quot;Read Audience&quot;
2. Doelgroep selecteren als ingangsbron
3. Regels voor opnieuw invoeren configureren (opnieuw invoeren, eenmalige invoer of opnieuw invoeren na wachtperiode toestaan)
4. Voeg eventueel wachtknooppunten toe (wacht 24 uur na kwalificatie)
5. Voeg desgewenst voorwaardenknooppunten toe (bijvoorbeeld controleren of het profiel aan extra criteria voldoet)
6. Voeg de knoop van de berichtactie toe en selecteer de kanaaloppervlakte en geschreven inhoud
7. Afsluitcriteria configureren (bijv. profielconverts, profielen afmelden)
8. Schakel desgewenst het experimenteren met inhoud op de berichtactie in
9. De reis evalueren en publiceren

**voor Optie C (API-teweeggebrachte Campagne):**

**navigatie UI:** Campagnes > Create Campagne > API-teweeggebracht

1. Een nieuwe API-gestuurde campagne maken
2. Selecteer het kanaaloppervlak en koppel de geschreven berichtinhoud
3. Contextafhankelijke personalisatietokens configureren voor gegevens die worden doorgegeven in de payload van de API-trigger
4. De campagne evalueren en activeren
5. Noteer de campagne-id voor gebruik in de API-triggerintegratie van het externe systeem
6. Het roepende systeem verzendt trekkerverzoeken naar het campagneeindpunt met ontvankelijke profielen en contextuele gegevens

#### Experience League-documentatie

- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Aan de slag met campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [API-gestuurde campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)
- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Reis van het publiek lezen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)
- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Mogelijke conflicten identificeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Fase 5: Analyseren van rapportage en prestaties

**functie van de Toepassing:** AJO: Rapportering &amp; de Analyse van Prestaties

Deze fase controleert leveringsmetriek tijdens uitvoering via levende rapporten en analyseert campagneprestaties na voltooiing via historische rapporten. Configureer desgewenst CJA-integratie voor een diepgaande analyse van de verschillende kanalen.

#### Besluit: Rapportagemethode

Welk niveau van verslaglegging is nodig voor deze campagne?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen systeemeigen AJO-rapporten | De standaardmaatstaven voor levering en betrokkenheid zijn toereikend (verzonden, geleverd, geopend, geklikt, beloften) | Geen extra configuratie; de rapporten worden gebouwd in campagne/reis UI |
| Native AJO-rapporten + CJA-analyse | De analyse van het dwars-kanaaleffect, attributiemodel, of de analyse van funnel is nodig voorbij leveringsmetriek | Vereist een CJA-verbinding en een gegevensweergave die gekoppeld zijn aan AJO-gegevenssets; biedt meer analytische mogelijkheden |
| Programmatische rapportage voor CJA | Geautomatiseerde dashboards of geplande rapportlevering zijn nodig voor belanghebbenden | Vereist CJA Reporting API-integratie; handig voor dashboards met uitvoerende functies en herhaalde prestatieoverzichten |

#### Besluit: conversie bijhouden

Hoe wordt het succes van de campagne gemeten boven de cijfers voor levering en betrokkenheid?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Geen conversie bijhouden | Campagnedoel is bewustzijn of betrokkenheid (openen, klikken) zonder specifieke downstreamactie | Eenvoudig; geen extra bijhouden van gebeurtenissen vereist |
| Webconversie bijhouden | Campagne CTA maakt een koppeling naar een webpagina waarop conversiegebeurtenissen (aankoop, registratie, verzenden van formulier) worden bijgehouden | Vereist Web SDK of Analytics tagging op de bestemmingspagina; de gebeurtenissen moeten in de datasets van AEP worden gevangen |
| Aangepaste conversiegebeurtenis | Het succes van de campagne wordt gemeten door een bedrijfsspecifieke gebeurtenis die niet op het Web wordt gevangen (bijvoorbeeld, in-store aankoop, vraagcentrum interactie) | Vereist dat de aangepaste gebeurtenis in AEP wordt ingevoerd en in de rapportage van gegevenssets wordt opgenomen |

#### UI-navigatie

- Live rapporten: Campagnes > Selectiecampagne > Live-rapport (of Reizen > Reis selecteren > Live-rapport)
- Historische rapporten: Campagnes > Selectiecampagne > Alle tijdrapport (of Reizen > Een reis selecteren > Alle tijdrapport)

#### Belangrijkste configuratiedetails

- Live-rapporten openen tijdens de uitvoering van de campagne om de levering en betrokkenheid in real time te controleren
- Metriek bekijken: Verzonden, Geleverd, Stommen, Openen, Klikken, Afmelden (e-mail); Verzonden, Geleverd, Klikken, Fouten (SMS); Verzonden, Geleverd, Openen, Openen, Handelingen (push)
- Na afloop van de campagne kunt u historische rapporten (altijd) openen voor uitgebreide analyse
- De levering funnel analyseren: Gericht > Verzonden > Geleverd > Openen > Klikken
- Fout- en uitsluitingsredenen controleren om leveringsproblemen vast te stellen
- Als het experimenteren met inhoud is ingeschakeld, controleert u de resultaten van het experiment en wacht u op statistisch vertrouwen voordat u een winnaar opgeeft
- Voor CJA-integratie moet u controleren of de AJO-gegevensweergave de relevante AJO-gegevenssets bevat (Gegevensset voor feedbackgebeurtenis, Gegevensset voor e-mailtrackingervaring)

#### Experience League-documentatie

- [Campagne live-rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journaal live](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Rapport voor inhoudexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementatieoverwegingen

In deze sectie worden onder meer de begeleiding, gemeenschappelijke valkuilen, beste praktijken en afwegingsbesluiten besproken.

### Guardrails en limieten

- Maximum van 500 actieve levende campagnes per zandbak — [&#x200B; de guardrails van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum van 4.000 segmentdefinities per zandbak - [&#x200B; Echte - de guardrails van het Profiel van de Klant - tijd &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximaal 10 kanaaloppervlakken per kanaaltype per sandbox
- API-getriggerde campagnes ondersteunen maximaal 20 profielontvangers per triggeraanvraag
- Campagnes kunnen niet worden bewerkt nadat ze zijn geactiveerd — dupliceren en in plaats daarvan wijzigen
- Live rapporten worden elke 60 seconden vernieuwd en tonen de laatste 24 uur aan gegevens
- Historische rapporten kunnen tot 2 uur duren om volledig te worden ingevuld na voltooiing van de campagne
- Maximaal 10 behandelingen (varianten) per experiment
- Maximaal 10 plafondconfiguraties per sandbox
- Maximaal 30 inhoudsfragmenten per bericht
- Maximale e-mailgrootte van 100 kB wordt aanbevolen voor optimale prestaties
- IP-opwarmingsplannen moeten het volume geleidelijk opvoeren over 2-4 weken voor nieuwe IP&#39;s
- Items in de lijst met onderdrukking blijven behouden gedurende een configureerbare periode (standaard 14 dagen voor zachte grenzen)

### Veelvoorkomende valkuilen

- **het verzenden vóór IP warmup is volledig:** Nieuwe IP adressen die hoge volumes onmiddellijk verzenden zullen door ISPs worden gemarkeerd, resulterend in slechte leverbaarheid en potentiële zwarte lijst. Voltooi altijd een IP warmup plan alvorens de productie op nieuwe IPs verzendt.

- **niet het testen van verpersoonlijking over veelvoudige profielen:** de tokens van Personalization die voor één testprofiel werken kunnen voor anderen ontbreken als de referenced XDM weg niet bestaat of ongeldig op sommige profielen is. Altijd voorvertonen met meerdere testprofielen die verschillende volledigheidsniveaus van de gegevens vertegenwoordigen.

- **het Overslaan overzicht van de suppressielijst:** de ingangen van de de suppressielijst van de Stale kunnen levering aan geldige adressen blokkeren, terwijl de ontbrekende ingangen in levering aan ongeldige adressen kunnen resulteren die grenzen produceren. Controleer en schoonmaak de lijst van de onderdrukking vóór grote campagnes.

- **het negeren van frequentiecapping voor promotiecampagnes:** het verzenden van een promotiecampagne zonder frequentiecapping terwijl andere campagnes ook actief zijn kan in profielen resulteren die veelvoudige berichten in een korte periode ontvangen, die unsubscribes en spamklachten drijven.

- **plannend campagnes zonder de publiekspopulatie te verifiëren:** Het activeren van een campagne alvorens het doelpubliek te bevestigen heeft een niet-nul geëvalueerde populatieresultaten in geleverde nul berichten. Controleer altijd de publieksgrootte voordat u activeert.

- **Gebruikend partijevaluatie voor publiek-teweeggebrachte reizen:** als de reis een Gelezen ingang van de Publiek met partijevaluatie gebruikt, zullen de profielen niet in dichtbij-real time ingaan. Gebruik streamingevaluatie voor het publiek wanneer invoer in real-time bijna vereist is.

- **het vormen toestemmingshandhaving:** het verzenden van berichten naar profielen zonder geldige marketing toestemming schendt verordeningen en beschadigt de reputatie van de leverbaarheid. Zorg ervoor dat de machtigingsvelden zijn ingevuld en worden afgedwongen op het niveau van het kanaaloppervlak.

### Aanbevolen procedures

- Begin met Optie A (Geplande Campagne) voor eenvoudige uitzendingsgebruiksgevallen en graaf aan Optie B (Publiek-teweeggebrachte Reis) slechts wanneer pre-leveringslogica of gedrag-gedreven timing nodig is
- Neem altijd voor maximale compatibiliteit zowel een één klik voor het opzeggen van een lijst als een koppeling voor het opzeggen van een abonnement op in de hoofdtekst van de e-mail
- Maak herbruikbare inhoudsfragmenten voor kop- en voetteksten en juridische disclaimes om ervoor te zorgen dat de campagnes consistent blijven
- Stel regels voor frequentiecapping in voordat u campagnes activeert om te veel berichten te voorkomen bij gelijktijdige verzendingen
- Gebruik experimenteren met inhoud om de onderwerpregel en CTA&#39;s te optimaliseren, te beginnen met A/B-tests voordat u overschakelt naar multivariate experimenten
- Prioriteitsscores toewijzen aan alle actieve campagnes om consistente conflictoplossing te garanderen
- Plan de evaluatie van het batchpubliek vóór de uitvoeringstijd van de campagne om nieuwe publieksgegevens te garanderen
- E-mails met proefdrukken verzenden en de functie voor het renderen van e-mail gebruiken om te controleren of het bericht correct wordt weergegeven bij e-mailclients voordat het wordt geactiveerd
- Bewaak direct na activering van de campagne het live rapport om leveringsproblemen vroegtijdig af te vangen
- Campagnerconfiguraties archiveren en resultaten experimenteren voor toekomstig referentie en continue optimalisatie

### Handelsbesluiten

De volgende compromissen moeten worden geëvalueerd wanneer het maken van implementatiekeuzen.

#### Eenvoud versus flexibiliteit

Geplande campagnes (Optie A) bieden de eenvoudigste configuratie maar geen pre-leveringslogica. Publiek-teweeggebrachte reizen (Optie B) verstrekken pre-leveringslogica maar voegen configuratieingewikkeldheid toe.

- **Optie A komt voor:** Snelheid aan lancering, operationele eenvoud, markeerteken zelfbediening
- **Optie B begunstigt:** Gedrag gericht, voorwaardelijke onderdrukking, rekbaarheid aan multi-step reizen
- **Aanbeveling:** Begin met Optie A voor ongecompliceerde verzendt. Ga naar Optie B slechts wanneer het gebruiksgeval echt wachttijd, voorwaarde, of vertakkende logica vóór levering vereist. Vermijd het gebruik van het reiscanvas voor eenvoudige batchverzendingen die niet profiteren van orkestmogelijkheden.

#### Poortversheid ten opzichte van de evaluatiekosten

De evaluatie van het stromen verstrekt bijna-real-time publieksupdates maar heeft segmentregelbeperkingen. De evaluatie van de partij steunt alle functies van de segmentregel maar evalueert op een dagelijks programma.

- **het stromen voorkeur:** Tijdigheid, gedrag-gedreven nauwkeurigheid, publiek-teweeggebrachte reisingang
- **de Partij gunt voor:** Complexe publiekslogica, grote populaties, lagere evaluatie overheadkosten
- **Aanbeveling:** partijevaluatie van het gebruik voor geplande campagnes (Optie A) waar de dagelijkse versheid voldoende is. Gebruik streamingevaluatie voor door het publiek geïnitieerde reizen (optie B), waarbij profielen moeten invoeren als ze daarvoor in aanmerking komen. Als de de regeluitdrukking van het publiekssegment niet streaming-in aanmerking komt, herstructureer de regels of keurt partij-vlakke latentie goed.

#### Personalization-diepte versus ontwerpcomplexiteit

Een diepere personalisatie (voorwaardelijke inhoudblokken, dynamische secties) verbetert de betrokkenheid, maar verhoogt de ontwerpings- en testinspanningen.

- **Diepe verpersoonlijking gunt:** Hogere betrokkenheidstarieven, relevantere klantenervaring, betere omzetting
- **Eenvoudige verpersoonlijkingsvoorkeur:** Sneller te lanceren tijd, lagere testende last, verminderd risico van het teruggeven van fouten
- **Aanbeveling:** Begin met basisverpersoonlijking (voornaam, relevante productcategorie) en laag in voorwaardelijke inhoudsblokken die op gemeten prestatieswinsten worden gebaseerd. Test altijd alle variaties in de inhoud van meerdere testprofielen voordat u de toepassing activeert.

#### Frequentiebeheer versus berichtbereik

Strikte aftopping van frequenties voorkomt overberichten, maar onderdrukt mogelijk de levering van campagnes aan profielen die onlangs andere berichten hebben ontvangen.

- **Strikte het begrenzen gunsten:** de ervaringskwaliteit van de Klant, lagere unsubscript tarieven, merkreputatie
- **Relaxed het in kaart brengen gunst:** Maximum berichtbereik, hogere totale indrukken, campagnedekking
- **Aanbeveling:** laat altijd frequentiecapping voor marketing campagnes toe. Kanaalspecifieke uiteinden instellen (bijvoorbeeld 3-5 e-mails per week, 1-2 sms per week). Alleen echt tijd-kritieke of transactionele berichten van de plafondregels vrijstellen.

## Gerelateerde documentatie

Deze sectie bevat uitgebreide koppelingen naar [!DNL Experience League] -documentatie die per onderwerp zijn ingedeeld.

### Campagnes

- [Aan de slag met campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [API-gestuurde campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/api-triggered-campaigns/api-triggered-campaigns)

### Journeys

- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Reis van het publiek lezen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/read-audience)

### Kanaalconfiguratie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [IP-pools maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-opwarmingsplannen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Instellingen van e-mailoppervlak](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Onderdrukkingslijst beheren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Authoring en personalisatie van berichten

- [Een e-mail maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [E-mail Designer-inhoudsonderdelen gebruiken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/content-components)
- [E-mailinhoud importeren of coderen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/code-content)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helpfuncties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Inhoudsbeheer

- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [E-mailproefdrukken verzenden](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)
- [E-mailrendering](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/email-rendering)

### Inhoud testen

- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport voor inhoudexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistische berekeningen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

### Frequentie- en conflictbeheer

- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Overzicht van bedrijfsregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Aan de slag met conflict- en prioriteitsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Mogelijke conflicten identificeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Afbakening van reizen en arbitrage](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Splitsen en segmenteren

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Samenstelling publiek](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/pql/overview)

### Rapportage

- [Campagne live-rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journaal live](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Beheer van gegevens en toestemming

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Overzicht van labels voor gegevensgebruik](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Toestemming en voorkeuren, veldgroep](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Toestemming in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Gegevensmodellering en identiteit

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Beveiligingsmechanismen

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Ingestiegrepen](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Zelfstudies en aan de slag

- [Aan de slag met Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/get-started)
- [Uw eerste campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Uw eerste journey maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
