---
title: Brand Concierge Conversation Experience
description: Leer hoe u digitale eigenschappen omzet in een merkveilige conversatie met AI-mogelijkheden die de klant helpen bij het ontdekken van digitale eigenschappen.
solution: Experience Platform, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7239'
ht-degree: 0%

---


# Brand Concierge-conversatie-ervaring

Deze handleiding bevat een uitgebreide implementatiereferentie voor door AI aangedreven conversationele ervaringen met [!DNL Adobe Brand Concierge] , geïntegreerd met [!DNL Adobe Experience Platform] (AEP) en [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]). Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die merkveilige gespreksagenten moeten implementeren over digitale eigenschappen.

Het omvat alle levensvatbare benaderingen voor het opstellen van conversationele ervaringen, van productadvieschatbots aan volledige medewerkers van de plaatsnavigatie, met begeleiding op wanneer om elke optie te kiezen. Het plan richt agentenconfiguratie, merkbeheer, inhoudsintegratie, plaatsingsstrategieën, profielverrijking van gesprekssignalen, en analytische optimalisering.

[!DNL Brand Concierge] laat merken toe om intelligente gespreksagenten op te stellen die merkstem begrijpen, tot goedgekeurde productcatalogi en inhoud toegang hebben, gepersonaliseerde aanbevelingen leveren die op profielgegevens in real time worden gebaseerd, en intent en sentiment signalen terug in het verenigde klantenprofiel vangen. Het resultaat is een conversationele ervaring die natuurlijk en on-brand voelt terwijl het verbeteren van het inzicht van de organisatie in elke klant.

## Hoofdlettergebruik

Organisaties proberen steeds vaker statische digitale ervaringen om te zetten in dynamische, door AI aangedreven gesprekken die klanten door detectie, productselectie en aankoopbeslissingen begeleiden. [!DNL Adobe Brand Concierge] Hiermee wordt dit opgelost door een georkestreerde conversatie-AI-laag op te geven die bestaande digitale eigenschappen aanwijst, aangedreven door AEP Agent Orchestrator.

Dit patroon verschilt van traditionele chatbot-implementaties omdat het native is geïntegreerd met het verenigde AEP-profiel, het gebruik van merkgovernancegaranties om ervoor te zorgen dat elke reactie op de merkstandaarden wordt afgestemd en conversiesignalen terugvoert naar het dataplatform van de klant voor downstreampersonalisatie en activering.

Het doelpubliek omvat digitale ervaringsteams, e-commercemanagers, content strategists, en marketing technologen die intelligente conversationele ervaringen moeten opstellen die betrokkenheid, omzetting, en profielverrijking drijven.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

### Lever persoonlijke klantenervaringen

Inhoud, aanbiedingen en berichten voor individuele voorkeuren, gedrag en levenscyclusfase aanpassen.

**KPIs:** Betrokkenheid, de Tarieven van de Omzetting, Tevredenheid van de Klant (CSAT)

[Meer informatie over het aanbieden van persoonlijke klantervaringen](/help/blueprints/business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

### Betere betrokkenheid van klanten

Verhoog de interactiefrequentie en -diepte voor alle digitale en fysieke aanraakpunten.

**KPIs:** Betrokkenheid, tijd op (Web) Pagina, Open Tarieven

[Meer informatie over het verbeteren van de betrokkenheid van klanten](/help/blueprints/business-objectives/qualification-sales-b2b/improve-customer-engagement.md)

### Conversietarieven verhogen

Verbeter het percentage bezoekers en de vooruitzichten die de gewenste acties zoals aankopen, inschrijven, of vormverzendingen voltooien.

**KPIs:** de Tarieven van de Omzetting, Loodomzetting, Kosten per lood

[Meer informatie over hogere conversietarieven](/help/blueprints/business-objectives/revenue-monetization/increase-conversion-rates.md)

### Nieuwe klanten aanschaffen

Breid de klantenbasis door gerichte aanschafcampagnes, lookend publiek, en betaalde media optimalisering uit.

**KPIs:** Upsell/Cross-Sell %, Incrementele Inkomsten, de Waarde van het Leven van de Klant

[Meer informatie over het aanschaffen van nieuwe klanten](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

## Voorbeelden van tactische gebruiksgevallen

De volgende scenario&#39;s tonen aan hoe dit patroon in de praktijk kan worden toegepast.

- **de ontdekkingsassistent van het Product** — stel een gespreksagent op de pagina&#39;s op van de productlijst die kwalificerende vragen stelt en productaanbevelingen beperkt die op klantenbehoeften, voorkeur, en begroting worden gebaseerd
- **Geleide vergelijkingsadviseur** — De klanten van de hulp vergelijken producten zij aan zij door natuurlijke dialoog, die verschillen benadrukken relevant voor hun verklaarde prioriteiten
- **Grootte en pas concierge** - het kleding van de gids of schoeisel shoppers door grootteselectie gebruikend conversatie Q&amp;A, verminderend winst en verhogend aankoopvertrouwen
- **de selecteur van het Abonnement of van het Plan** — Loop klanten door de opties van het de dienstrij of abonnement met gepersonaliseerde aanbevelingen die op gebruikspatronen en verklaarde behoeften worden gebaseerd
- **de navigatiemedewerker van de Plaats** — de bezoekers van de Hulp vinden relevante inhoud, steunmiddelen, of productcategorieën die op hun verklaarde bedoeling worden gebaseerd, die stuittarieven op complexe plaatsen verminderen
- **pre-koopoverleg** — Verstrek de begeleiding van de hoge-bezinningsaankoop (bijvoorbeeld, elektronica, financiële producten, verzekering) door multi-boommengesprekken die naar een aanbeveling bouwen
- **het programmasamenspel van de Loyalty** — De loyaliteitsleden van de hulp ontdekken beloningen, begrijpen rijvoordelen, en vinden terugbetalingskansen door gespreksinteractie
- **herverbind gesprek** — Initieer pro-actieve gespreksoutreach aan het terugkeren bezoekers die op vorige doorbladergeschiedenis of verlaten wortelpunten worden gebaseerd
- **Levende agentenescalatie met context** — Verstuur naadloos complexe vragen aan levende verkoop of steunagenten terwijl het behoud van volledige gesprekscontext en gegevens van het klantenprofiel
- **post-aankoop steun en upsell** — Moed klanten na aankoop met opstellingshulp, complementaire productsuggesties, en tevreden controle-ins door omzettingskanalen aan

## Kernprestatie-indicatoren

De volgende KPIs helpt het succes van dit gebruiks gevalpatroon meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Betrokkenheid gesprek | Percentage bezoekers die een gesprek beginnen en onderhouden | Gestarte gesprekken/subsidiabele paginaweergaven |
| Voltooiingssnelheid van gesprek | Percentage gesprekken dat een zinvolle resolutie bereikt | Voltooide gesprekken/gesprekken begonnen |
| Omzettingssnelheid | Percentage gesprekken dat tot een gewenste actie leidt (aankoop, aanmelding, lead form) | Conversies van conversatie/totale conversatie |
| Gemiddelde diepte gesproken tekst | Aantal beurten per gesprek, dat op betrokkenheidskwaliteit wijst | Gemiddeld aantal berichten per sessie |
| Klanttevredenheid (CSAT) | De score van de post-gesprekstevredenheid van in-ervaring terugkoppelt | Antwoorden van enquêtes of duim omhoog/omlaag ratings |
| Aanvaardingspercentage aanbeveling | Percentage aanvaarde of aangeklikte productaanbevelingen | Aanbevolen aanbevelingen |
| Afgiftesnelheid van Live Agent | Percentage gesprekken geëscaleerd aan levende agenten | Afwisselingen/totale conversaties |
| Profielverrijkingsgraad | Percentage gesprekken dat nieuwe intent- of voorkeurssignalen oplevert | Verbeterde profielen / totale conversaties |
| Door discussies beïnvloede inkomsten | Inkomsten uit aankopen waarbij een [!DNL Brand Concierge] gesprek voorafging aan de conversie | Attributieanalyse op conversatie-tot-aankoop reizen |
| Tijd tot oplossing | Gemiddelde duur van gespreksbegin tot resolutie of overdracht | Analyse van tijdstempels over gespreksgebeurtenissen |

## Hoofdletterpatroon gebruiken

**de gesprekservaring van Brand Concierge**

Transformeer digitale eigenschappen in door AI aangedreven, merkveilige gesprekservaringen die klanten door natuurlijke dialoog helpen ontdekken, verrijken profielen met intent- en sentimentsignalen, en leveren gepersonaliseerde productaanbevelingen.

**de ketting van de Functie:** de Configuratie van de agent > de Opstelling van de Regering van het Merk > de Integratie van de Inhoud > de Plaatsing van de Ervaring van de Conversatie > de Verrijking van het Profiel > Analyse &amp; Optimalisering

## Applicaties

De volgende toepassingen worden gebruikt om dit gebruiks gevalpatroon uit te voeren.

- **[!DNL Brand Concierge]** — Een door AI aangedreven toepassing voor conversatie-ervaring die de agent, de Product Advisor Agent, de Site Advisory Agent, het beheer van merken en de analyse van gesprekken levert
- **[!DNL Adobe Experience Platform] (AEP)** — Verenigde gegevensstichting die XDM schema&#39;s, identiteitsresolutie, klantenprofielen in real time, en infrastructuur van de gegevensinzameling voor omzettingssignalen verstrekt
- **[!DNL Real-Time CDP] ([!DNL RT-CDP])** — Het gegevensplatform van de Klant die profielraadpleging in real time voor gepersonaliseerde gesprekken verstrekken, publiekssegmentatie van gesprekssignalen, en profielverrijking met intent en sentiment gegevens

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Vereist | Sandbox provisioned with [!DNL Brand Concierge] toegelaten recht; rollen die voor conversationele ervaringsbeheerders, inhoudsmanagers, en analysegebruikers worden gevormd; ABAC beleid op zijn plaats voor gespreksgegevens die PII of gevoelige klantensignalen bevatten | [&#x200B; overzicht van het Toegangsbeheer &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | XDM-schema&#39;s voor conversationele gebeurtenissen (klasse ExperienceEvent met conversatiespecifieke veldgroepen die intentie, sentiment, productinteracties en afhandelingsgebeurtenissen vastleggen); profielschema uitgebreid met conversationele voorkeur en intentkenmerken; opzoekschema voor productcatalogus voor oplopende aanbevelingen | [&#x200B; XDM overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/home) |
| Gegevensbronnen en -verzameling | Vereist | [!DNL Web SDK] of [!DNL Mobile SDK] geconfigureerd met gegevensstreams die conversiegebeurtenisgegevens naar AEP-gegevenssets routeren; [!DNL Edge Network] integratie voor realtime-gebeurtenisvastlegging tijdens gesprekken; productcatalogusgegevens die via bronconnectors of batch-opname zijn ingevoerd | [&#x200B; overzicht van SDK van het Web &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/web-sdk/home) |
| Identiteit en profielconfiguratie | Vereist | Identiteitsnaamruimten die voor bezoekersidentificatie (ECID voor anonieme, identiteitskaart van CRM of e-mail voor voor authentiek verklaard) worden gevormd; samenvoegbeleid dat met randactivering voor profielraadpleging in real time tijdens gesprekken wordt gevormd; identiteit die regels voor de continuïteit van het interdevice gesprek verbindt | [&#x200B; Overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/home) |
| Auditiedefinitie en segmentatie | Verondersteld op plaats | De soorten publiek niet die voor kern gespreksplaatsing maar nodig voor gepersonaliseerde gespreksstrategieën worden vereist (bijvoorbeeld, ontvangen de high-value klantensegmenten verschillende gespreksstromen); het stromen of randevaluatie die voor gespreksverpersoonlijking in real time wordt geadviseerd | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Samengevoegde conversatie-signalen in profiel-vlakke attributen (bijvoorbeeld, totale gesprekken, dominante productbelangen, gemiddelde sentimentscore) voor gebruik in downstreamsegmentatie en personalisatie | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Vorm behoudbeleid voor gespreksgebeurtenisgegevens, beheer toestemming voor gesprekopname en het profileren van gesprekken, en steun privacy schrappingsverzoeken voor gesprekstranscripties | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | Teken gespreksgegevensgebieden die PII, sentiment, of intent signalen bevatten; afdwingen governance beleid verhinderend gevoelige gespreksgegevens om onbevoegde bestemmingen te bereiken | [&#x200B; Overzicht van het beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home) |
| Bewaking en waarneming | Aanbevolen | De pijpleidingen van het opnemen van gespreksgebeurtenissen van de controle, de succespercentages van de spoorprofielverrijking, en alarm over de mislukkingen van de gegevensstroom die de kwaliteit van de gespreksverpersoonlijking konden beïnvloeden | [&#x200B; overzicht van de Inzichten van de Waarnemelijkheid &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | Analyseer gespreksprestaties, klantenfeedback, conversieattributie en de doeltreffendheid van de agent met behulp van [!DNL Brand Concierge] ingebouwde analyse en [!DNL CJA] voor de analyse van het effect van gesprekken tussen kanalen | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Brand Concierge]

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Configuratie van agent | Fase 1: Configuratie van de agent | Configureer de [!DNL Brand Concierge] agent orchestrator met specialisatie van de agent (productadviseur, Siteadvies) en basisgedragsinstellingen |
| Brand Governance Setup | Fase 2: Instelling merkenbeheer | De stem van het merk, toon, overseinengidsen, goedgekeurde inhoudsgrenzen, en verboden onderwerpen bepalen die alle gespreksinteractie vormen |
| Inhoudsintegratie | Fase 3: Integratie van inhoud | Connect-bronnen met door een merk goedgekeurde inhoud, zoals AEM-inhoud, productcatalogi, kennisbanken en andere vertrouwde gegevens voor basisreacties |
| Configuratie van productadvies | Fase 3: Integratie van inhoud | Configureer de Product Advisor Agent voor gepersonaliseerde productaanbevelingen, vergelijkingen met instructies en levering van merkgebonden reacties |
| Configuratie van siteadvies | Fase 3: Integratie van inhoud | Vorm de Agent van het Adviserende Bevel van de Plaats om navigatie te verbeteren door interactie aan te passen die op bezoekersgedrag en intentiesignalen wordt gebaseerd |
| Implementatie van conversatie-ervaring | Fase 4: Implementatie van conversatie-ervaring | Schakel conversatie-ervaringen in via ondersteunde kanalen (web, mobiele app, aangepaste SDK) met ondersteuning voor tekst- en spraakinteractie |
| Flow Management met lage code | Fase 4: Implementatie van conversatie-ervaring | Laat marketing teams toe om conversationele toon, stromen, en inhoud bij te werken gebruikend laag-code configuratiehulpmiddelen |
| Verrijking van conversieprofiel | Fase 5: Profielverrijking | Verrijk AEP-klantprofielen met intentie, sentiment, productaffiniteit en gedragssignalen die tijdens gesprekken zijn vastgelegd |
| Conversationele analyse | Fase 6: Analyse en optimalisatie | De metriek van de overeenkomst van de monitor, klantenterugkoppelen, omzettingsgegevens, en gesprekskwaliteit via ingebouwde analytische dashboards |
| Live Agent Handoff | Fase 4: Implementatie van conversatie-ervaring | Vorm naadloze overdracht aan levende verkoop of steunagenten terwijl het bewaren van volledige gesprekscontext |

### [!DNL Real-Time CDP]

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Real-time profiel opzoeken | Fase 4: Implementatie van conversatie-ervaring | Toegang de attributen van het klantenprofiel in real time en segmentlidmaatschap om omzettingsreacties te personaliseren die op bekende klantengegevens worden gebaseerd |
| Profielverrijking | Fase 5: Profielverrijking | Verrijken profielen met berekende kenmerken die zijn afgeleid van conversationele gedragsgebeurtenissen (intentscores, sentimenttrends, productaffiniteit) |
| Evaluatie publiek | Fase 5: Profielverrijking | Evalueer publiekslidmaatschap dat op gesprekssignalen wordt gebaseerd stroomafwaarts gericht op betrokken gesprekssegmenten toe te laten |

## Vereisten

De volgende items moeten aanwezig zijn voordat de implementatie begint.

- [!DNL Adobe Brand Concierge] machtiging is actief voor de organisatie
- AEP- en [!DNL RT-CDP] -licenties beschikken over voldoende profielen en rechten voor gebeurtenisvolumes
- Beschikbaar document van de de richtlijnen van het merk bepalend stem, toon, goedgekeurd overseinen, en verboden onderwerpen
- Productcatalogus of opslagplaats voor inhoud voorbereid voor integratie (AEM-middelen, PIM-gegevens of gestructureerde productfeed)
- De eigenschappen van het Web die voor gesprekservaring plaatsing met technische toegang voor de integratie van SDK worden geïdentificeerd
- Live agent-infrastructuur beschikbaar als overdracht vereist is (platform van contactcentrum, integratie van CRM)
- Er is een kader voor het beheer van de instemming voor het vastleggen en profileren van conversiegegevens
- [!DNL Web SDK] of [!DNL Mobile SDK] al geïmplementeerd op doeleigenschappen (of gepland voor gelijktijdige implementatie)
- Betrokkenheid-groepering op gesprekswerkingsgebied (productadvies slechts, plaatsnavigatie, of allebei)
- Privacy en juridische revisie voltooid voor het vastleggen en gebruiken van conversatiegegevens op basis van AI

## Implementatieopties

De volgende secties beschrijven verschillende benaderingen voor het uitvoeren van dit gebruiks gevalpatroon.

### Optie A: implementatie van productadvies

**Best voor:** e-commerce en detailhandelsorganisaties concentreerden zich op geleide productontdekking, vergelijking, en aanbevelingen ervaringen die omzetting en gemiddelde ordewaarde drijven.

**hoe het werkt:**

Product Advisor Agent wordt gevormd als primaire gespreksspecialisatie. Het verbindt met de productcatalogus, begrijpt productkenmerken en relaties, en leidt klanten door natuurlijke dialoog om tot gepersonaliseerde aanbevelingen te komen. De agent gebruikt de garantie van het merkbeheer om ervoor te zorgen dat de aanbevelingen in overeenstemming zijn met de bedrijfsprioriteiten (bijvoorbeeld het promoten van items in voorraad, het benadrukken van producten in winstmarge).

De Adviseur van het product integreert met het profiel van de klant in real time om tot aankoopgeschiedenis toegang te hebben, gedrag, en voorkeursgegevens te doorbladeren, toelatend aanbevelingen die rekening houden voor wat de klant reeds bezit, heeft eerder overwogen, of waarschijnlijk zal vereisen gebaseerd op hun profiel. Conversies worden vastgelegd als ervaringsgebeurtenissen en de intentsignalen stromen terug naar het profiel voor downstreamgebruik.

**Zeer belangrijke overwegingen:**

- Vereist een goed gestructureerde productcatalogus met rijke kenmerkgegevens voor efficiënte aanbevelingen
- Productgegevens moeten actueel worden gehouden om te voorkomen dat producten uit de voorraad worden aanbevolen of worden gestaakt
- Brand governance moet bepalen hoe de agent omgaat met concurrerende productbeweringen en prijsvergelijkingen

**Voordelen:**

- Directe drijft meetbare opbrengstgevolgen door geleide aankoopomzetting
- Vermindert de rendementspercentages van producten door beter geïnformeerde aankoopbeslissingen
- Vangt high-value productaffiniteit en intentsignalen voor stroomafwaartse verpersoonlijking
- Natuurlijke uitbreiding van bestaande ervaringen op het gebied van e-handel

**Beperkingen:**

- Vereist doorlopend onderhoud en synchronisatie van productcatalogi
- Beperkt tot productgerichte gesprekken; vragen over sitenavigatie worden mogelijk niet beantwoord
- Effectiviteit hangt af van de kwaliteit en volledigheid van catalogusgegevens

**Experience League:**

- [Brand Concierge-overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge productadviseur](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)

### Optie B: Implementatie van advies voor sites

**Best voor:** Organisaties met complexe digitale eigenschappen (media, financiële diensten, gezondheidszorg, technologie) waar de bezoekers navigatiehulp nodig hebben om relevante inhoud, middelen, of zelfbedieningshulpmiddelen te vinden.

**hoe het werkt:**

De agent van het Adviserende van de Plaats wordt gevormd als primaire gespreksspecialisatie. Het indexeert de structuur van de site-inhoud, begrijpt de paginagerelataties en inhoudscategorieën en past de richtlijnen aan op basis van de gedragssignalen van de bezoeker en de opgegeven intentie. Wanneer een bezoeker zich aansluit, interpreteert de agent hun behoeften en leidt hen aan de meest relevante inhoud, de hulpmiddelen, of de middelen.

Siteadvies maakt gebruik van gedragssignalen in real time (huidige pagina, verwijzingsbron, navigatiepad) in combinatie met profielgegevens (vorige bezoeken, voorkeuren voor inhoud, klantniveau) om contextafhankelijke navigatieondersteuning te bieden. Dit is bijzonder waardevol op plaatsen met diepe inhoudshiërarchieën, veelvoudige productlijnen, of complexe zelfbediening werkschema&#39;s.

**Zeer belangrijke overwegingen:**

- Vereist uitgebreide inhoud indexeren en regelmatig opnieuw kruipen wanneer de inhoud van de site verandert
- Het meest effectief op sites met een aanzienlijke inhoudsbreedte waar bezoekers vaak moeite hebben om te vinden wat ze nodig hebben
- Merk governance zou werkingsgebiedgrenzen moeten bepalen (welke plaatsgebieden de agent aan kan navigeren)

**Voordelen:**

- Hiermee verlaagt u de stuiteringsfrequentie en verbetert u de ontdekkingsmogelijkheden van inhoud op complexe sites
- Hiermee legt u navigatieintentiesignalen vast die gaten in de inhoud en problemen met de gebruikerservaring weergeven
- Minder complexiteit bij implementatie dan productadvies (geen integratie van productcatalogus vereist)
- Biedt analytische inzichten van waarnaar bezoekers op zoek zijn, maar die niet kunnen worden gevonden

**Beperkingen:**

- Minder rechtstreeks gekoppeld aan omzettingen dan productieve conversaties
- Vereist dat de inhoud goed gestructureerd en regelmatig bijgewerkt is voor nauwkeurige begeleiding
- Mogelijk moet de site regelmatig opnieuw worden opgeleid naarmate de sitestructuur zich ontwikkelt

**Experience League:**

- [Brand Concierge-overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Adviseur voor Brand Concierge-sites](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)

### Optie C: Gecombineerde productadvies + implementatie van siteadvies

**Best voor:** Organisaties die een uitvoerige gesprekservaring willen die zowel productontdekking als plaatsnavigatie, typisch grote detailhandel of merken B2C met uitgebreide digitale eigenschappen en diverse bezoekersintenties behandelen.

**hoe het werkt:**

Zowel de Product Advisor Agent als de Site Advisory Agent zijn geconfigureerd in het [!DNL Brand Concierge] -orkest. De agent orchestrator gebruikt intentopsporing om gesprekken aan de aangewezen specialisatie te leiden — productgerelateerde vragen gaan naar de Adviseur van het Product terwijl de navigatie en de inhoud-vinden vragen naar het Adviserend van de Plaats gaan. Het orchestrator beheert naadloze overgangen tussen specialisaties binnen één enkel gesprek.

Deze aanpak biedt de meest complete beleving van gesprekken, waarbij alle behoeften van bezoekers worden verwerkt, van &quot;Help mij een product te vinden&quot; tot &quot;Waar kan ik de status van mijn bestelling controleren?&quot; Handelsbeheerinstructies gelden uniform voor beide specialisaties, zodat een consistente stem van het merk wordt gegarandeerd, ongeacht het gespreksonderwerp.

**Zeer belangrijke overwegingen:**

- Hogere complexiteit bij de implementatie waarbij zowel de productcatalogus als de inhoudintegratie vereist zijn
- Het verpletteren van de intentie tussen specialisaties moet goed-afgestemd zijn om misgeleide gesprekken te vermijden
- Brand governance setup is uitgebreider voor zowel product- als navigatiecontext

**Voordelen:**

- Biedt de meest uitgebreide conversatie-ervaring voor bezoekers
- Eén ingangspunt verwerkt diverse bezoekersintensies zonder afzonderlijke interfaces te vereisen
- Cross-specialization gesprekken (bijvoorbeeld productvraag die tot steun navigatie leidt) die natuurlijk worden behandeld
- rijkste profielverrijking van diverse gesprekssignalen

**Beperkingen:**

- Hoogste implementatieinspanningen en doorlopend onderhoud
- Vereist coördinatie tussen productcatalogus en inhoudsteams
- Complexere eisen inzake tests en kwaliteitsborging
- Betrokkenheid van de configuratie van het merk

**Experience League:**

- [Brand Concierge-overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Optievergelijking

| Criteria | Optie A: Productadvies | Optie B: Siteadvies | Optie C: Gecombineerd |
| --- | --- | --- | --- |
| Best voor | E-commerce, productgestuurde conversie | Inhoudsintensieve sites, zelfbediening voor navigatie | Volledige digitale ervaring |
| Complexiteit | Gemiddeld | Low-Medium | Hoog |
| Tijd tot waarde | 4-6 weken | 3-5 weken | 6-10 weken |
| Inkomsteneffect | Hoog (directe invloed op conversie) | Medium (indirect via betrokkenheid) | Hoogste (zowel conversie als betrokkenheid) |
| Inhoud-eisen | Productcatalogus met rijke kenmerken | Index van site-inhoud | Zowel productcatalogus als inhoudsindex |
| Profielverrijking | Productaffiniteit, aankoopintentie | Navigatieintentie, voorkeuren voor inhoud | Volledig signaalspectrum |
| Onderhoudsinspanning | Synchronisatie van productcatalogus | Inhoud opnieuw indexeren | Beide lopende |

### Kies de juiste optie

Begin door uw primaire bedrijfsdoelstelling en digitale bezitskenmerken te beoordelen:

1. **als uw primair doel productomzetting** drijft en uw digitaal bezit is handel-geconcentreerd, kies **Optie A (de Adviseur van het Product)**. Dit is het meest gangbare uitgangspunt voor handelsmerken en e-commerce.

2. **als uw primair doel inhoudsontdekkingsbaarheid** verbetert en uw plaats diepe inhoudshiërarchieën of complexe zelfbedieningwerkschema&#39;s heeft, kies **Optie B (het Adviserende Bevel van de Plaats)**. Dit is ideaal voor media, financiële diensten, gezondheidszorg, en technologiebedrijven.

3. **als u uitvoerige dekking** nodig hebt en zowel product handel als inhoudsnavigatie heeft behoeften, kies **Gecombineerde Optie C**. Overweeg te beginnen met één specialisatie en de tweede toe te voegen nadat het eerste stabiel en geoptimaliseerd is.

Een gefaseerde benadering wordt geadviseerd voor de meeste organisaties: stel eerst één specialisatie op, bevestig prestaties en verzamel lessen, dan breid aan de gecombineerde plaatsing uit.

## Uitvoeringsfasen

In de volgende fasen wordt de aanbevolen implementatiereeks beschreven.

### Fase 1: Configuratie van agent

**functie van de Toepassing:** [!DNL Brand Concierge]: De Configuratie van de agent

Configureer de kern-agent van [!DNL Brand Concierge], inclusief het selecteren van agentspecialisaties (Productadvies, Siteadvies of beide), het configureren van het gedrag van de basisagent en het tot stand brengen van de verbinding tussen [!DNL Brand Concierge] en AEP voor profieltoegang en het vastleggen van gebeurtenissen.

#### Besluit: selectie van de agent specialisatie

Bepaal welke agentenspecialisaties voor deze plaatsing zouden moeten worden geactiveerd.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen productadvies | Commerce-gerichte implementatie gericht op productdetectie en -conversie | Vereist integratie met productcatalogus; snelste weg naar inkomsteneffect |
| Alleen voor advies over site | Implementatie op basis van inhoud en navigatie | Lagere integratiecomplexiteit; het beste voor niet-commerciële plaatsen |
| Beide specialisaties | Uitgebreide conversatie-dekking voor producten en inhoud | Hogere complexiteit; overwogen gefaseerde implementatie te beginnen met één |

#### Besluit: Inleidend model van gesprek

Bepaal hoe gesprekken op het digitale bezit moeten beginnen.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Door bezoekers geïnitieerde (passieve) | Standaardbenadering waarbij de chatwidget beschikbaar is maar niet proactief wordt geactiveerd | Minder onderbreekrisico; vertrouwt op bezoekersbewustzijn van de praatjeoptie |
| Proactieve betrokkenheid (geactiveerd) | De agent stelt gesprek in werking dat op gedragssignalen wordt gebaseerd (bijvoorbeeld, verlengde storttijd, herhaalde paginabezoeken, kartaaraaraaraarbestand) | Hogere betrokkenheidspercentages, maar riskeert irritatie van de bezoeker als de triggers te agressief zijn; vereist afstelling van de gedragtrigger |
| Hybride (passief met contextafhankelijke herinneringen) | De chatwidget is passief, maar geeft contextuele aanwijzingen weer op basis van pagina-inhoud of het gedrag van de bezoeker | Evenwichtige benadering; aanwijzingen zonder betrokkenheid te dwingen |

#### Vorm de agent

**navigatie UI:** [!DNL Experience Platform] > AI Medewerker > [!DNL Brand Concierge] > de Configuratie van de Agent

Belangrijke configuratiedetails:

- Bepaal de agentennaam en beschrijving die in de omzettingsinterface zullen verschijnen
- Selecteer welke AEP-sandbox het klantprofiel en de gebeurtenisgegevens bevat waartoe de agent toegang moet krijgen
- Vorm de agent orchestrator aan routevragen tussen specialisaties die op intentopsporing worden gebaseerd
- De parameters van de gesprekszitting (onderbrekingsduur, maximumgesprekslengte, gezamenlijke zittingsgrenzen) plaatsen
- De integratie van de profielraadpleging in real time inschakelen zodat de agent tot de gegevens van het bezoekersprofiel tijdens gesprekken kan toegang hebben

**waar de opties uiteenlopen:**

**voor Optie A (de Adviseur van het Product):**
Schakel de productadviseur-specialisatie in en configureer de verbinding met de gegevensbron van de productcatalogus. Stel parameters voor productaanbevelingen in, inclusief maximale aanbevelingen per reactie, weergavevoorkeuren voor productkenmerken en vergelijkingsregels.

**voor Optie B (het Adviseren van de Plaats):**
Schakel de specialisatie Siteadvies in en configureer de verbinding met de index van de site-inhoud. Stel navigatieparameters in, waaronder grenzen van inhoudsbereik, verwerking van paginacategorieën en voorkeuren voor het genereren van diepkoppelingen.

**voor Optie C (Gecombineerd):**
Laat zowel specialisaties toe en vorm de intent verpletterende logica van het orkest. Bepaal het verpletteren van regels die bepalen wanneer een gesprek door de Adviseur van het Product versus het Adviseren van de Plaats zou moeten worden behandeld, en hoe de overgangen tussen specialisaties binnen één enkel gesprek zouden moeten worden geleid.

**documentatie van Experience League:**

- [Brand Concierge-overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Overzicht van AI-assistent](https://experienceleague.adobe.com/nl/docs/experience-platform/ai-assistant/home)
- [AEP Agent Orchestrator](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)

### Fase 2: Instelling van Brand-governance

**functie van de Toepassing:** [!DNL Brand Concierge]: De Opstelling van de Governance van het merk

Configureer de merkbeheerinstructies die alle conversatieinteracties vormgeven. Dit omvat merkstem en toondefinities, goedgekeurde inhoudsgrenzen, verboden onderwerpen, richtlijnen van de reactiestijl, en escalatieregels. Brand governance zorgt ervoor dat elke door AI gegenereerde reactie op de merkstandaarden wordt afgestemd.

#### Besluit: striktheidsniveau bestuur

Bepaal hoe strak de merkbeheerinstructies gespreksreacties zouden moeten beperken.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Strikte governance | Zeer gereguleerde industrieën (financiële diensten, gezondheidszorg, verzekeringen) of premiummerken die nauwkeurige tooncontrole vereisen | Beperkt conversatieflexibiliteit; kan leiden tot frequentere reacties &quot;Ik kan daar niet mee helpen&quot;; hoogste merkveiligheid |
| Moderne governance | De meeste consumentenmerken waar de consistentie van de merkstem belangrijk maar sommige gespreksflexibiliteit aanvaardbaar is | Een goede balans tussen merkveiligheid en conversatie-naturaliteit; aanbevolen uitgangspunt voor de meeste implementaties |
| Flexibel bestuur | Handelsmerken met een handmatige of levensstijl waarbij de prioriteit wordt gelegd op gesprekspartners en betrokkenheid | De meeste natuurlijke conversatie voelt; vereist meer doorlopende controle op reacties buiten het merk |

#### Besluit: strategie voor externe behandeling

Bepaal hoe de agent vragen buiten zijn gevormde werkingsgebied zou moeten behandelen.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Omleiden naar bereik | De agent erkent de vraag en richt zich aan onderwerpen het met kan helpen | Handhaaft betrokkenheid maar kan bezoekers met wettige off-topic behoeften frustreren |
| Aflevering aan levende agent | De agent biedt aan om de bezoeker met een menselijke agent voor off-topic vragen te verbinden | Beste klantervaring, maar vereist live agentinfrastructuur en -personeel |
| Gracedelijke afname met middelen | De agent verklaart het niet met dat onderwerp kan helpen en verleent verbindingen aan relevante middelen of steunkanalen | Lage frictie fallback; vereist geen live agentenbeschikbaarheid |

#### Brandbeheer configureren

**navigatie UI:** [!DNL Experience Platform] > AI Medewerker > [!DNL Brand Concierge] > Merk Governance

Belangrijke configuratiedetails:

- Kenmerken van een merk definiëren: merknaam, taglijn, missie, waarden en persoonlijkheidskenmerken die conversatie-tint mogelijk maken
- De parameters van de vastgestelde toon: formaliteitsniveau, humoristische tolerantie, empathieniveau, en assertiviteit voor productaanbevelingen
- Vorm goedgekeurde inhoudsgrenzen: onderwerpen de agent wordt gemachtigd om te bespreken en onderwerpen die uitdrukkelijk worden verboden
- Richtlijnen voor de indeling van reacties definiëren: maximale responslengte, gebruik van lijsten versus prose, emoji-beleid en koppelingsopmaak
- De vastgestelde escalatietrekkers: voorwaarden die een gesprek aan een levende agent (bijvoorbeeld, klachtenopsporing, herhaalde ontevredenheidssignalen, high-value klantenidentificatie) automatisch zouden moeten leiden
- Configureer competitieve berichtafhandeling: hoe de agent moet reageren wanneer bezoekers vragen naar producten van concurrenten
- Vereisten inzake openbaarmaking van informatie en juridische kennisgeving definiëren: verplichte informatieverschaffing voor gereglementeerde industrieën

**documentatie van Experience League:**

- [Brand Concierge-merkbeheer](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Operationele inzichten van AI Assistant](https://experienceleague.adobe.com/nl/docs/experience-platform/ai-assistant/home)

### Fase 3: Integratie van inhoud

**functie van de Toepassing:** [!DNL Brand Concierge]: De Integratie van de inhoud, de Configuratie van de Adviseur van het Product, de Configuratie van het Adviseur van de Plaats

Vorm de inhoudsbronnen die omzettingsreacties in nauwkeurige, merk-goedgekeurde informatie baseren. Dit omvat de integratie van productcatalogi, AEM-inhoudverbindingen, de import van kennisbestanden en de planning voor het vernieuwen van inhoud.

#### Besluit: Integratiemethode productcatalogus

Bepaal hoe productgegevens aan de Product Advisor Agent moeten worden verstrekt. (Alleen optie A en C)

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Integratie van AEP-gegevensset | De productcatalogus is al opgenomen in AEP als opzoekgegevensset via bronconnectors | Gebruikt bestaande gegevensinfrastructuur; houdt productgegevens gesynchroniseerd met profielgegevens; vereist modellering en inzameling van basisgegevens om productcatalogus te omvatten |
| Directe integratie van diervoeders | De catalogus van het product bestaat in PIM of een handelsplatform die een gestructureerd voer kan verstrekken | Kan meer inventarisatie- en prijsgegevens in real time bieden; hiervoor is configuratie en planning van de feed vereist |
| Integratie van AEM-inhoud | De inhoud van het product wordt beheerd in AEM en zou als gebiedende bron van productgegevens moeten dienen | Het beste voor merken waarbij AEM de inhoudhub is; zorgt voor consistentie tussen webinhoud en gespreksreacties |

#### Besluit: frequentie voor vernieuwen van inhoud

Bepaal hoe vaak de de inhoudskennisbasis van de agent zou moeten worden bijgewerkt.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Real-time / bijna real-time | De beschikbaarheid, de prijs, of de inhoudveranderingen van het product vaak (bijvoorbeeld flitsverkoop, inventaris-gevoelige kleinhandel) | Hoogste nauwkeurigheid maar hogere infrastructuurbelasting; kritiek voor inventarisgevoelige aanbevelingen |
| Dagelijks vernieuwen | Wijzigingen in de inhoud worden gepland en gepland (bijvoorbeeld redactiecalenders, wekelijkse promoties) | Goede balans tussen nauwkeurigheid en prestaties; geschikt voor de meeste implementaties |
| Op aanvraag vernieuwen | Wijzigingen in inhoud komen niet vaak voor en kunnen handmatig worden geactiveerd wanneer updates plaatsvinden | Laagste overhead; geschikt voor statische productcatalogi of stabiele inhoudslocaties |

#### Inhoudsbronnen configureren

**navigatie UI:** [!DNL Experience Platform] > AI Medewerker > [!DNL Brand Concierge] > Inhoudsbronnen

Belangrijke configuratiedetails:

- Gegevensbronnen van productcatalogi verbinden met veldtoewijzing voor productnaam, beschrijving, kenmerken, prijs, beschikbaarheid, afbeeldingen en categoriehiërarchie
- Inhoud indexeren voor sitepagina&#39;s, kennisbankartikelen, inhoud van Veelgestelde vragen en ondersteuningsdocumentatie configureren
- Vastgestelde grenzen van het inhoudswerkingsgebied die bepalen welke inhoud de agent kan van verwijzingen voorzien en die wordt uitgesloten
- Vorm inhoud het terugvalgedrag wanneer de agent relevante inhoud niet kan vinden om een vraag te beantwoorden
- Inhoudskwaliteitsregels instellen: minimale vertrouwensdrempel voor inhoud voor opnemen in reacties, citeringsvereisten en brontoewijzing

**waar de opties uiteenlopen:**

**voor Optie A (de Adviseur van het Product):**
Focus op de integratie van productcatalogi met toewijzing van rijke productkenmerken. Configureer de logica van de Product Advisor Agent-aanbevelingen, inclusief het aantal producten dat u wilt voorstellen, de manier waarop u items uit de voorraad moet verwerken, de manier waarop u productvergelijkingen kunt presenteren en de manier waarop u gegevens over het klantprofiel (aankoopgeschiedenis, browsergedrag) kunt opnemen in de rangschikking van aanbevelingen.

**voor Optie B (het Adviseren van de Plaats):**
Focus op indexering van site-inhoud met toewijzing van paginahiërarchie. Vorm de navigatielogica van de Agent van het Adviseur van de Plaats met inbegrip van hoe te om bezoekersintentie te interpreteren, welke inhoudscategorieën om voorrang te geven, hoe te om dubbelzinnige navigatieverzoeken te behandelen, en hoe te om suggesties aan te passen die op de huidige paginacontext en zittingsgedrag van de bezoeker worden gebaseerd.

**voor Optie C (Gecombineerd):**
Configureer zowel de productcatalogus als de inhoudsbronnen van de site. Verzeker de inhoud die logica verplettert correct inhoud aan de aangewezen specialisatie toewijst en dat de verwijzingen tussen productinhoud en de inhoud van de plaatsnavigatie behoorlijk in kaart worden gebracht.

**documentatie van Experience League:**

- [Brand Concierge-inhoudsconfiguratie](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge productadviseur](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Adviseur voor Brand Concierge-sites](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Overzicht van bronnen](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/home)

### Fase 4: Implementatie van ervaringen tijdens het gesprek

**de functie van de Toepassing:** [!DNL Brand Concierge]: De Omroepplaatsing van de Ervaring, het Laag-Code Stroombeheer, Levende Agent Handoff; [!DNL RT-CDP]: De Opzoeken van het profiel in real time

Implementeer de conversatie-ervaring op digitale doeleigenschappen, waaronder kanaalconfiguratie, widgetaanpassing, profielopzoekintegratie voor personalisatie, regels voor actieve agent-overdracht en low-code-tools voor doorlopend inhoudsbeheer.

#### Besluit: distributiekanaal

Bepaal aan welke kanalen de gesprekservaring moet worden ingezet.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Web (ingesloten widget) | Primaire webeigenschap is het belangrijkste aanraakpunt voor klanten | Meest voorkomende startpunt; vereist [!DNL Web SDK] integratie; ondersteunt zowel anonieme als geverifieerde bezoekers |
| Mobiele app (SDK-integratie) | Mobiele app is een belangrijk servicekanaal voor klanten | Vereist [!DNL Mobile SDK] integratie; overweeg de beperkingen van het schermbezit voor gespreksinterface |
| Aangepaste SDK-implementatie | Conversationele ervaring moet worden ingesloten in een aangepaste toepassing, kiosk of niet-standaard digitale eigenschap | Maximale flexibiliteit; vereist meer ontwikkelingsinspanningen; geschikt voor kiosken in de winkel of voor bedrijfseigen platforms |
| Meerkanaalsimplementatie | Gesprekkervaring vereist voor het web, mobiele apparaten en andere kanalen | Hoogste bereik; vereist consistent merkbeheer over kanalen; de gesprekscontext moet zo mogelijk door kanalen blijven |

#### Besluit: Personalization-diepte voor gesprekken

Bepaal hoeveel gegevens van het klantenprofiel de agent zou moeten gebruiken om gesprekken te personaliseren.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen-anonieme (sessiecontext) | Privacyeerste aanpak of wanneer de meeste bezoekers niet geïdentificeerd zijn | Gebruikt alleen gedragssignalen tijdens de sessie; er is geen profielzoekopdracht vereist; geschikt voor anonieme productdetectie |
| Profielbewust (geverifieerde bezoekers) | Bezoekers worden doorgaans aangemeld en gepersonaliseerde aanbevelingen gebaseerd op toegevoegde waarde in de geschiedenis | Vereist opzoeken in realtime profiel via [!DNL RT-CDP]; aanzienlijk betere kwaliteit van aanbevelingen voor bekende klanten |
| Progressieve personalisatie | Het mengen van anoniem en voor authentiek verklaard met progressieve profielbouw tijdens gesprek | Begint met zittingscontext; verrijkt als bezoeker informatie verstrekt of voor authentiek verklaart; brengt privacy en verpersoonlijking in evenwicht |

#### Beslissing: configuratie van de liveagent

Bepaal of conversaties escaleerbaar moeten zijn voor levende menselijke agenten.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Geen overdracht (alleen zelfbediening) | De AI agent kan alle verwachte gesprekstypes behandelen, of de levende agenten zijn niet beschikbaar | Eenvoudigste implementatie; kan bezoekers frustreren met complexe behoeften; geschikt voor low-risk, productbrowserscenario&#39;s |
| Op regels gebaseerde handoff | De specifieke trekkers zouden aan levende agenten moeten escaleren (bijvoorbeeld, klachtenopsporing, high-value klant, complex onderzoek) | Voorspelbaar escalatiegedrag; vereist het bepalen van escalatieregels en trekkers; vereist de integratie van het actieve agentenplatform |
| Door bezoekers gevraagde overdracht | De bezoekers kunnen om een levende agent op om het even welk punt in gesprek verzoeken | De beste klantenervaring; vereist altijd-beschikbaar agentenpersoneel of rijbeheer; gesprekscontext moet overbrengen |

#### Implementeer de conversatie-ervaring

**navigatie UI:** [!DNL Experience Platform] > AI Medewerker > [!DNL Brand Concierge] > Plaatsing

Belangrijke configuratiedetails:

- De weergave van de widget voor gesprekken configureren: positie, kleurschema, avatar, welkomstbericht en interactiestijl (tekst, stem of beide)
- Integreren met [!DNL Web SDK] of [!DNL Mobile SDK] voor het vastleggen van gebeurtenissen en het oplossen van profielen
- Vorm profielraadpleging in real time om tot klantenattributen, segmentlidmaatschap, en recente activiteit tijdens gesprekken toegang te hebben
- De actieve integratie van de agentenoverdracht van de opstelling met het platform van het contactcentrum, met inbegrip van het protocol van de contextoverdracht, rij die en agentenbericht verplettert
- Laat low-code hulpmiddelen van het stroombeheer voor marketing teams toe om gesprekstarters, promotioneel overseinen, seizoensgebonden inhoud, en stroomvariaties zonder ontwikkelaarsbetrokkenheid bij te werken
- Vorm de persistentieregels van de gesprekszitting: hoe lang de gespreksgeschiedenis wordt behouden, of de gesprekken over zittingen, en de continuïteit van het dwars-apparatengesprek kunnen hervatten

**documentatie van Experience League:**

- [Brand Concierge-implementatie](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Overzicht van Web SDK](https://experienceleague.adobe.com/nl/docs/experience-platform/web-sdk/home)
- [Overzicht Edge Network Server API](https://experienceleague.adobe.com/nl/docs/experience-platform/edge-network-server-api/overview)
- [Het eindpunt van API-entiteiten voor profielen](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/api/entities)
- [Overzicht van het realtime klantprofiel](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/home)

### Fase 5: Profielverrijking

**de functie van de Toepassing:** [!DNL Brand Concierge]: De Verrijking van het Profiel van de discussie; [!DNL RT-CDP]: De Verrijking van het profiel, de Evaluatie van het Publiek

Vorm de vangst en de verrijkingspijpleiding die gesprekssignalen terug in het AEP verenigde klantenprofiel voedt. Dit omvat het in kaart brengen van gespreksgebeurtenissen aan XDM, het halen van intent en sentiment signalen, het creëren van gegevens gegevens verwerkt van gespreksgegevens, en het bouwen van publiek dat op conversationeel gedrag wordt gebaseerd.

#### Beslissing: Omvang van het conversiesignaal

Bepaal welke conversatiesignalen moeten worden vastgelegd en geschreven naar het profiel van de klant.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen kernbetrokkenheidssignalen | Minimale profielverrijking; begin, einde, duur van gesprek vastleggen en voltooiingsstatus | Laagste gegevensvolume; voldoende voor basisanalyse; beperkte personalisatiewaarde |
| Intentie- en voorkeurssignalen | Vastleggen van afgeleide productbelangen, vermelde voorkeuren en besproken onderwerpcategorieën | Hoge verpersoonlijkingswaarde; matig gegevensvolume; het meest meestal geadviseerd |
| Volledige signaalopname | Vastlegintentie, sentiment, productinteracties, aanbevelingen, afhandelingsgebeurtenissen en feedbackscores | rijkere profielverrijking; hoogste gegevensvolume; maakt geavanceerde analysemogelijkheden en ML-gedreven personalisatie mogelijk |

#### Besluit: publiek creëren op basis van gespreksgegevens

Bepaal of het publiek moet worden gecreëerd op basis van conversationeel gedrag voor downstreamactivering.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Geen publiek in gesprek | Conversiegegevens die alleen voor analyses worden gebruikt, niet voor activering van het publiek | Eenvoudigste aanpak; geschikt als conversaties een aanvulling zijn op bestaande betrokkenheidskanalen |
| Op intentie gebaseerd publiek | Een publiek maken op basis van bepaalde productbelangen of navigatie-intenties van gesprekken | Maakt het mogelijk om bezoekers die blijk gaven van interesse maar niet bekeerde; hoge waarde voor handel opnieuw te richten |
| Gedragssoorten | Creeer publiek dat op gespreksbetrokkenheidspatronen wordt gebaseerd (bijvoorbeeld, hoge betrokkenheid, verlaten gesprek, herhaalde bezoeken) | Laat dialoog-geïnformeerde reis orkest en dwars-kanaalfollow-up toe |

#### Profielverrijking configureren

**navigatie UI:** [!DNL Experience Platform] > Klant > Profielen > Berekende attributen (voor afgeleide signalen); Klant > Soorten publiek > Gesprek creëren (voor gesprekspartners)

Belangrijke configuratiedetails:

- Wijs gespreksgebeurtenissen aan XDM het schemagebieden van ExperienceEvent die gespreksidentiteitskaart, berichttelling, besproken onderwerpen, producten van verwijzingen voorzien, sentimentscores, en resolutiestatus vangen
- [!DNL Brand Concierge] profielverrijking configureren om intentie- en voorkeurssignalen naar het verenigde profiel te schrijven
- Maak berekende kenmerken op basis van conversationele gebeurtenisgegevens: totale conversaties (leven), dominante belangen in de productcategorie (30 dagen), gemiddelde sentimentscore (90 dagen), conversiekoers van gesprek naar aankoop
- Definieer streaming- of batchpubliekssegmenten op basis van conversatiesignalen voor downstreamactivering (bijvoorbeeld &quot;Bezoekers die productcategorie X de afgelopen 7 dagen hebben besproken maar niet hebben aangeschaft&quot;)
- Valideer profielverrijking door steekproefprofielen op te zoeken om omzettingsattributen te bevestigen bevolkt zijn

**documentatie van Experience League:**

- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/overview)
- [Gebruikershandleiding voor berekende kenmerken](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/ui)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Overzicht van het realtime klantprofiel](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/home)

### Fase 6: Analyse en optimalisatie

**functie van de Toepassing:** [!DNL Brand Concierge]: De Conversationele Analytics

Stel analytische dashboards en rapportage in voor het meten van de prestaties van een beleving van gesprekken, het identificeren van optimalisatiemogelijkheden en het volgen van KPI&#39;s. Dit omvat [!DNL Brand Concierge] ingebouwde analyses, optionele [!DNL CJA] integratie voor de analyse van het effect van gesprekken tussen kanalen en doorlopende optimalisatieworkflows.

#### Besluit: analytische diepte

Bepaal welk niveau van gespreksanalyse nodig is.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Ingebouwde [!DNL Brand Concierge] analysemogelijkheden | De standaard rapportering over gespreksvolume, overeenkomst, tevredenheid en omzetting is voldoende | Snelst te activeren; omvat kern-KPI&#39;s; beperkte correlatie tussen kanalen |
| [!DNL Brand Concierge] + [!DNL CJA] integratie | Interkanaalanalyse nodig om te begrijpen hoe gesprekken bredere klantenreizen beïnvloeden | Vereist [!DNL CJA] verbinding en gegevensweergave instellen; maakt attributieanalyse mogelijk via conversatie en andere kanalen |
| Stapel met volledige analyse ([!DNL Brand Concierge] + [!DNL CJA] + aangepaste dashboards) | Rapportage op directieniveau, geavanceerde attributiemodellen en het creëren van een aangepast publiek op basis van analytische inzichten | Hoogste analytische capaciteit; vereist [!DNL CJA] deskundigheid; laat gegeven-gedreven gespreksoptimalisering toe |

#### Analyse en optimalisatie configureren

**navigatie UI:** [!DNL Experience Platform] > AI Medewerker > [!DNL Brand Concierge] > Analytics; [!DNL Analytics Platform] > Workspace (voor [!DNL CJA])

Belangrijke configuratiedetails:

- Bekijk [!DNL Brand Concierge] ingebouwde analytische dashboards: trends voor het gespreksvolume, betrokkenheidssnelheid, voltooiingssnelheid, CSAT-scores, acceptatiesnelheid van aanbevelingen en wachtfrequentie
- Configureer [!DNL CJA] -verbinding om conversationele gebeurtenisgegevenssets op te nemen voor kanaalanalyse (als u [!DNL CJA] -integratie kiest)
- Bouw [!DNL CJA] werkruimteanalyse voor gesprek-aan-omzetattributie, die welke gespreksonderwerpen met aankoopgedrag correleert
- De kwaliteit van het gesprek van de opstelling controle: spooronderwerpen waar de agent, gemeenschappelijke onbeantwoorde vragen, en sentimenttendensen in tijd worstelt
- Workflows voor optimalisatie definiëren: regelmatig overzicht van functies voor het beheren van merken, triggers voor het vernieuwen van inhoud en verbeteringen in de gespreksstroom op basis van analyses

**documentatie van Experience League:**

- [Brand Concierge Analytics](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [CJA Analysis Workspace - overzicht](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-workspace/home)
- [Een CJA-verbinding maken of bewerken](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-connections/create-connection)
- [Een CJA-gegevensweergave maken of bewerken](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-dataviews/create-dataview)

## Implementatieoverwegingen

In de volgende secties worden onder andere de volgende secties beschreven: guardrails, valkuilen, best practices en beslissingen om zaken af te handelen, waarmee u tijdens de implementatie rekening kunt houden.

### Guardrails en limieten

- [!DNL Brand Concierge] conversatie-ervaringen zijn onderhevig aan de generatielimieten voor AI-respons; gelijktijdige conversatiecapaciteit is afhankelijk van machtigingsniveau
- Realtime profielraadpleging tijdens gesprekken is onderworpen aan de het tariefgrenzen van het Profiel API per zandbak — [&#x200B; Realtime de guardrails van het Profiel van de Klant &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)
- Het opnemen van de gebeurtenisgegevens van het gesprek volgt standaard AEP die binnendringingsgrenzen stromen - [&#x200B; de guardrails van de Ingestie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/ingestion/guardrails)
- Grootte van productcatalogus en volume van inhoudsindex zijn onderworpen aan [!DNL Brand Concierge] beperkingen voor de integratie van inhoud
- Maximum van 25 gegevens verwerkte attributen per zandbak is op conversatie signaalsamenvoegingen van toepassing - [&#x200B; de gegevens verwerkte attributengidsen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/overview)
- Maximum van 4.000 segmentdefinities per zandbak is op conversatie publiek van toepassing - [&#x200B; de gidsen van de Segmentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)

### Veelvoorkomende valkuilen

- **Onvoldoende definitie van het merkbeheer:** Opstellend zonder de grondige configuratie van het merkbeheer resulteert in off-brand reacties die klantenvertrouwen beschadigen. Investeer significante tijd in Fase 2 bepalend toon, grenzen, en escalatieregels vóór plaatsing.
- **de gegevens van de de productcatalogus van de Stale:** de aanbevelingen van de Adviseur van het Product die op verouderde inventaris, tarifering, of beschikbaarheidsgegevens worden gebaseerd frustreren klanten en eroderen vertrouwen. Installeren van automatische vernieuwingsleidingen voor inhoud met validatiecontroles.
- **Overagressieve pro-actieve betrokkenheidstrekkers:** Plaatsende gedragstrekkers te agressief (bijvoorbeeld, die gesprek na 3 seconden op pagina) teweegbrengen brengt bezoekers en verhoogt stuitende tarieven. Begin met conservatieve triggers en kies op basis van betrokkenheidsgegevens.
- **Neglecterend anonieme bezoekerservaring:** Het concentreren zich verpersoonlijking slechts op voor authentiek verklaarde bezoekers negeert de meerderheid van verkeer. De gespreksstromen van het ontwerp die waarde aan anonieme bezoekers verstrekken gebruikend in-zittingsgedragssignalen.
- **het Overslaan configuratie van de profielverrijking:** het Opstellen van gesprekken zonder signalen terug naar het profiel te vangen verspilt waardevolle intent en voorkeursgegevens. Vorm profielverrijking parallel met plaatsing, niet als nagedachte.
- **het negeren van de ervaring van de het agentenoverdracht:** Arme handoff ervaringen (verloren context, herhaalde vragen, lange wachttijden) beschadigen de algemene conversationele ervaring meer dan het aanbieden van afhangend bij allen. Test de volledige handmatige doorloop van begin tot einde voor het starten.

### Aanbevolen procedures

- Begin met één enkele agentenspecialisatie (de Adviseur van het Product of Adviseur van de Plaats) en breid na het vestigen van basislijnprestaties uit.
- Voer workshops voor het beheer van merken uit met belanghebbenden op het gebied van marketing, wetgeving en klantervaringen voordat u de instructies configureert.
- Gebruik progressieve verpersoonlijking: begin gesprekken met op zitting-context-gebaseerde reacties en verdiep verpersoonlijking aangezien de bezoeker informatie verstrekt of voor authentiek verklaart.
- Voer A/B het testen van gesprekstarters, herinneringen, en de formaten van de aanbeveling presentatie uit gebruikend de low-code hulpmiddelen van het stroombeheer.
- Plan regelmatig (wekelijks of tweewekelijks) overzicht van gespreksanalyses om inhoudskloven, gemeenschappelijke mislukkingspunten, en optimaliseringskansen te identificeren.
- Creeer een terugkoppel lijn tussen conversationele analyses en merkgovernance updates — gebruik gespreksgegevens om toon te verfijnen, nieuwe goedgekeurde onderwerpen toe te voegen, en escalatieregels aan te passen.
- De trends van het gespreksgevoel van de monitor als vroege waarschuwingssysteem voor productkwesties, plaatsproblemen, of merkperceptieverschuivingen.
- De gespreksstromen van het ontwerp die profiel-verrijkende signalen natuurlijk vangen zonder de interactie te maken als een ondervraging voelen.

### Handelsbesluiten

>[!NOTE]
>De volgende afwegingsbeslissingen moeten worden beoordeeld op basis van de specifieke vereisten en beperkingen van uw organisatie.

**de verpersoonlijkingsdiepte van de Gesprek vs. privacy eenvoud**

Een diepere profielintegratie maakt gepersonaliseerde en effectievere gesprekken mogelijk, maar verhoogt de complexiteit van gegevensverzameling, toestemmingsvereisten en de nalevingsbelasting van de privacy.

- **Diepe verpersoonlijking bevordert:** Hogere omzettingspercentages, betere aanbeveling kwaliteit, rijkere profielverrijking, en meer het in dienst nemen van gesprekken voor terugkerende klanten
- **eenvoud van de Privacy gunst:** snellere plaatsing, eenvoudiger toestemmingsbeheer, lager regelgevend risico, en een privacy-eerste merkpositionering
- **Aanbeveling:** Begin met progressieve verpersoonlijking die goed voor anonieme bezoekers werkt en op profiel-gebaseerde verpersoonlijking voor voor authentiek verklaarde zittingen toevoegt. Dit levert waarde op alle identificatieniveaus terwijl de naleving van de privacyregels beheersbaar blijft. Vastleggen van toestemming uitvoeren voor conversieprofilering die is afgestemd op bestaande goedkeuringskaders.

**striktheid van het Merk tegenover conversationele naturalness**

Strikte garanties op het gebied van merkbeheer zorgen ervoor dat elke reactie op één lijn komt met merkstandaarden, maar al te rigide beperkingen maken conversaties het gevoel van robotisch en verminderen de betrokkenheid.

- **Strikt beheer gunt:** de veiligheid van het merk, regelgevende naleving, verenigbaar overseinen, en voorspelbaar agentengedrag
- **Flexibel beheer gunt:** Natuurlijke gespreksstroom, hogere overeenkomst, betere klantentevredenheid, en de capaciteit om een bredere waaier van vragen te behandelen
- **Aanbeveling:** begin met gematigd bestuur en draai of losser gebaseerd op gespreksanalyses. Bewaak het tarief van &quot;ik kan niet met dat&quot;reacties als indicator van overbeperking helpen. Gebruik de low-code hulpmiddelen van het stroombeheer om op governance montages snel zonder ontwikkelaarsbetrokkenheid te herhalen.

**Real-time inhoud verfrist zich vs. systeemprestaties**

De inhoudssynchronisatie in real time verzekert de agent altijd huidige product en inhoudsgegevens heeft, maar ononderbroken verfrist verbruikt meer infrastructuurmiddelen en kan latentie introduceren.

- **Reëel-tijd verfrist voorkeur:** Nauwkeurigheid voor inventaris-gevoelige aanbevelingen, tijdgevoelige bevorderingen, en snel veranderende inhoud
- **Geplande verfrist zich gunsten:** de stabiliteit van het systeem, voorspelbaar middelverbruik, en lagere infrastructuurkosten
- **Aanbeveling:** De dagelijkse inhoud van het gebruik verfrist zich als gebrek, met bijna-real time verfrist zich slechts voor inventarisbeschikbaarheid en het tarief gegevens die wezenlijk de klantenervaring beïnvloeden. De nauwkeurigheidsmetriek van de inhoud van de monitor om te bepalen als verfrist frequentie adequaat is.

**Uitgebreide signaalvangst vs. gegevensbeheer overheadkosten**

Door elk conversatiesignaal vast te leggen, beschikt u over het rijkste profiel voor verrijking en analyse, maar vergroot u het gegevensvolume, de opslagkosten en de complexiteit van het beheer.

- **Volledige signaalvangst begunstigt:** Geavanceerde analyses, het modelopleiding van ML, uitvoerige profielverrijking, en maximum stroomafwaartse verpersoonlijkingswaarde
- **Selectieve vangt gunsten:** Lagere opslagkosten, eenvoudiger gegevensbeheer, snellere prestaties van de profielraadpleging, en gemakkelijkere naleving van de beginselen van de gegevensminimalisering
- **Aanbeveling:** Begin met intent en voorkeur signaalvangst (de middengrond) en breid aan volledige signaalvangst uit slechts na het bevestigen dat de extra gegevens meetbare stroomafwaartse waarde creëren. Pas het beleid van de gegevenssetvervalsing op gespreksgebeurtenisgegevens toe om opslaggroei te beheren.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie voor het implementeren van dit gebruikspatroon.

**[!DNL Brand Concierge]**

- [Brand Concierge-overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/overview)
- [Brand Concierge productadviseur](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/product-advisor)
- [Adviseur voor Brand Concierge-sites](https://experienceleague.adobe.com/en/docs/experience-platform/ai-assistant/brand-concierge/site-advisor)
- [Overzicht van AI-assistent](https://experienceleague.adobe.com/nl/docs/experience-platform/ai-assistant/home)

**[!DNL Adobe Experience Platform]**

- [AEP-overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/landing/home)
- [XDM System, overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/home)
- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/schema/composition)
- [Overzicht van het realtime klantprofiel](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/home)

**de inzameling en integratie van Gegevens**

- [Overzicht van Web SDK](https://experienceleague.adobe.com/nl/docs/experience-platform/web-sdk/home)
- [Overzicht van Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/configure)
- [Overzicht Edge Network Server API](https://experienceleague.adobe.com/nl/docs/experience-platform/edge-network-server-api/overview)
- [Overzicht van bronnen](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/home)

**Identiteit en profiel**

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/home)
- [Overzicht van naamruimten](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/features/namespaces)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/merge-policies/overview)
- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/overview)

**Soorten publiek en segmentatie**

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/methods/streaming-segmentation)

**het bestuur van Gegevens en privacy**

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home)
- [Toestemming en voorkeuren, veldgroep](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/field-groups/profile/consents)
- [Privacy Service-overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/privacy/home)
- [Overzicht van geavanceerd gegevenslevenscyclusbeheer](https://experienceleague.adobe.com/nl/docs/experience-platform/data-lifecycle/home)

**Controle en waarneming**

- [Overzicht van observatiegegevens](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/home)
- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/alerts/overview)

**Analytics en het melden**

- [CJA-overzicht](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-overview/cja-overview)
- [Overzicht van CJA-verbindingen](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-connections/overview)
- [Overzicht van CJA-gegevensweergaven](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-dataviews/data-views)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-workspace/home)

**Guardrails**

- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)
- [Ingestiegrepen](https://experienceleague.adobe.com/nl/docs/experience-platform/ingestion/guardrails)
- [Segmenteringsgeleiding](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)
