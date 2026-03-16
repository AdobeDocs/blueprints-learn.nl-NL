---
title: B2B-gebruiksgevallen
description: Ontdek hoe B2B-organisaties Adobe Experience Platform gebruiken om de pijpleiding te versnellen, de loodkwaliteit te verbeteren en de uitbreiding van klanten te stimuleren.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2269'
ht-degree: 1%

---


# B2B-gebruiksgevallen

Bedrijfs-aan-zaken organisaties gebruiken Adobe Experience Platform om rekening en persoon-vlakke gegevens te verenigen, toelatend marketing en verkoopteams om gecoördineerde, relevante ervaringen over elke fase van de koopreis te leveren. Van pijpleidingsversnelling aan klantenuitbreiding, tonen deze gebruiksgevallen aan hoe de teams B2B complexe gegevens in meetbare bedrijfsresultaten veranderen.

>[!NOTE]
>
>Voor B2B-Specifieke architectuurblauwdrukken met inbegrip van op rekening-gebaseerde activering en het kopen groepsbeheer, zie [&#x200B; B2B activering &amp; marketing blauwdrukken &#x200B;](/help/blueprints/b2b/overview.md).

## Account-Based Marketing Personalization

Pas marketingcommunicatie en inhoud voor doelaccounts aan op basis van accountprofiel, betrokkenheidsgeschiedenis en koopsignalen. Door het overseinen aan de unieke context van elke rekening te richten, kunnen de marketing teams door het lawaai breken en de juiste belanghebbenden met de juiste inhoud in dienst nemen.

### Zakelijke impact

Organisaties die op rekening-gebaseerde marketing verpersoonlijking uitvoeren zien typisch een verhoging van 30-40% in het tarief van de rekeningsovereenkomst, die sterkere pijpleiding en snellere overeenkomstenvooruitgang drijven.

### Uitvoeren

Gebruik het [&#x200B; B2B Audience Activation &#x200B;](/help/blueprints/use-case-patterns/audience-building-activation/b2b-audience-activation.md) patroon om account-vlakke publiek te bouwen en gepersonaliseerde inhoud over kanalen te activeren. Dit patroon is speciaal ontwikkeld voor strategieën op basis van account en ondersteunt zowel het richten op account- als op persoonniveau.

### Technische overwegingen

- CRM-gegevens (bijvoorbeeld [!DNL Salesforce] of [!DNL Microsoft Dynamics] ) integreren om bijgewerkte accounthiërarchieën, opportuniteitsfasen en eigendomstoewijzingen te onderhouden.
- Configureer profielschema&#39;s op accountniveau voor het vastleggen van grafische kenmerken, zoals de industrie, het aantal werknemers, het inkomstenbereik en de technologiestapel.
- Wijs relaties van persoon tot account toe om ervoor te zorgen dat individuele betrokkenheidssignalen worden opgedeeld in score en segmentatie op accountniveau.
- Coördineer met [!DNL Marketo Engage] om marketingautomatiseringscampagnes af te stemmen op platformgestuurd accountpubliek.


## Loodscores en verpleegkunde

Volgen automatisch scoren op basis van profielgegevens en gedrag, leidt het routeren van hoge scoring tot verkoop met persoonlijke opvoedcampagnes voor anderen. Deze benadering zorgt ervoor dat verkoopteams zich op de meest veelbelovende kansen concentreren terwijl de marketing vooruitzichten in een vroeger stadium blijft ontwikkelen.

### Zakelijke impact

Bedrijven die gedragslead scoring en geautomatiseerde verplegend werken, realiseren doorgaans een toename van 25-35% in de &#39;lead-to-opportunity&#39; conversie, versnelde snelheid van de pijpleiding en een verbetering van de verkoopproductiviteit.

### Uitvoeren

Gebruik het [&#x200B; Multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) aan ontwerp vertakkende borrelritten die aan de veranderingen van de loodscore en gedragtrekkers antwoorden. Dit patroon steunt de voorwaardelijke logica nodig om verbindingen tussen de sporen van de boomkwekerij en de werkschema&#39;s van de verkoopoverdracht te leiden.

### Technische overwegingen

- Bidirectionele CRM-synchronisatie instellen (bijvoorbeeld [!DNL Salesforce] of [!DNL Microsoft Dynamics] ), zodat de leadscores en kwalificatiestatus consistent blijven tussen marketing- en verkoopsystemen.
- Definieer zowel demografische (rol, bedrijfsgrootte, industrie) als gedragsafmetingen (downloads van inhoud, webinaire aanwezigheid, bezoeken aan productpagina&#39;s).
- Coördineer leadscoremodellen met [!DNL Marketo Engage] om tegenstrijdige scores op verschillende platforms te voorkomen.
- Stel de regels voor het verlagen van de score in om ervoor te zorgen dat leads die stil gaan, in de loop der tijd worden onthouden.


## Inhoud Personalization for Prospects

Pas de inhoud, bronnen en aanbiedingen van websites aan op basis van de bedrijfswereld, de rol, de bedrijfsgrootte en de geschiedenis van uw betrokkenheid. Wanneer de vooruitzichten de inhoud relevant voor hun specifieke situatie zien, verbinden zij zich dieper en bewegen zich sneller door de funnel.

### Zakelijke impact

B2B-organisaties die webervaringen personaliseren voor bekende vooruitzichten zien doorgaans een toename van 20-30% in de betrokkenheid bij inhoud, wat leidt tot meer gekwalificeerde pijpleidingen en kortere verkoopcycli.

### Uitvoeren

Gebruik het [&#128279;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) patroon van het Web/App Personalization van 0&rbrace; Known-Bezoeker &lbrace;om op maat gemaakte inhoudservaringen te leveren die op verenigde perspectiefprofielen worden gebaseerd. Dit patroon gebruikt profielgegevens in real time om de meest relevante middelen, casestudy&#39;s, en vraag aan actie voor elke bezoeker te dienen.

### Technische overwegingen

- Voer identiteitsresolutie uit om anoniem het doorbladeren gedrag aan bekende perspectiefverslagen aan te passen zodra zij voor authentiek verklaren of een vorm voorleggen.
- Definieer personalisatieregels die zijn gebaseerd op kenmerken op accountniveau (industrie, segment, handelsstadium) en op kenmerken op individueel niveau (rol, gebruik van inhoud in het verleden).
- Integreer met uw contentbeheersysteem om hoofdbanners, aanbevelingen voor bronnen en oproepen tot actie dynamisch om te wisselen.
- Zorg ervoor dat [!DNL Marketo Engage] webtraceringsgegevens in het uniforme profiel worden ingevoerd voor een compleet gedragsbeeld.


## Registratie en follow-up van gebeurtenissen

Automatiseer gepersonaliseerde bevestigingen van de gebeurtenisregistratie, herinneringen, en follow-up na de gebeurtenis gebaseerd op gebeurtenistype en deelnemersprofiel. Hierdoor blijven de vooruitzichten actief voor, tijdens en na gebeurtenissen en wordt het marketingteam bevrijd van handmatige coördinatie.

### Zakelijke impact

De geautomatiseerde, gepersonaliseerde werkschema&#39;s van de gebeurtenismededeling drijven typisch een verhoging van 40 tot 50% van gebeurtenisaanwezigheid, die rendement op gebeurtenisinvestering maximaliseren en perspectiefverhoudingen versterken.

### Uitvoeren

Gebruik het [&#x200B; Multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) om de volledige levenscyclus van de gebeurtenis van registratie door postevent te ordenen cultuur. Dit patroon ondersteunt op tijd gebaseerde triggers, voorwaardelijke vertakking op gebeurtenistype en meerkanaalse opvolgreeksen.

### Technische overwegingen

- Integreer registratiegegevens van webinaire platforms (bijvoorbeeld [!DNL ON24] , [!DNL Zoom Webinar] ) en persoonlijke gebeurtenissystemen in het uniforme profiel.
- Leg aanwezigheids- en betrokkenheidssignalen (sessieduur, gestelde vragen, opiniepeilingantwoorden) vast om het follow-upbericht aan uw persoonlijke wensen aan te passen.
- U kunt gebeurtenisritten coördineren met de status van het [!DNL Marketo Engage] -programma om consistente rapportering tussen systemen te behouden.
- Ontwerp afzonderlijke trajectvertakkingen voor registranten die aanwezig waren, in plaats van voor diegenen die dat niet deden, met op maat gesneden inhoud voor elk.


## Proefconversiecampagnes voor producten

Neem proefgebruikers met gepersonaliseerde productaanbevelingen, trainingsmiddelen en aanbiedingen in dienst om de conversie naar betaalde plannen aan te moedigen. Door testgebruikers te ontmoeten waar zij in hun productexploratie zijn, kunnen de teams wrijving verwijderen en de weg aan aankoop versnellen.

### Zakelijke impact

Organisaties die persoonlijke conversiecampagnes implementeren zien doorgaans een stijging van 25-35% in de conversie van kosten naar kosten, wat rechtstreeks van invloed is op de omzet van nieuwe bedrijven en de kosten voor het aanschaffen van klanten verlaagt.

### Uitvoeren

Gebruik het [&#x200B; Multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) om op tijd-gebaseerde en op gedrag-gebaseerde omzettingsritten voor proefgebruikers te bouwen. Dit patroon ondersteunt voorwaardelijke paden die zijn gebaseerd op de mijlpalen van het productgebruik, waardoor doelgerichte verschuivingen op de juiste momenten mogelijk zijn.

### Technische overwegingen

- De telemetrie van het productgebruik (eigenschapadoptie, login frequentie, tijd-in-product) van de aanwinst om profielen van de proefovereenkomst in real time te bouwen.
- Definieer op gebruik gebaseerde mijlpalen (bijv. eerst gemaakt project, sleutelfunctie gebruikt, samenwerking uitgenodigd) als reistriggers voor tijdige outreach.
- Synchroniseer de status van de proefversie en conversiegebeurtenissen naar [!DNL Salesforce] of [!DNL Microsoft Dynamics] , zodat vertegenwoordigers van de verkoopafdeling volledig zichtbaar zijn in de proefversie.
- Coördineer met [!DNL Marketo Engage] programma&#39;s om overlappende communicatie tijdens de proefperiode te voorkomen.


## Klantsucces en onboarding

Pas de klant aan boord van reizen aan met relevante training, bronnen en ondersteuning op basis van het aangeschafte product en het profiel van de klant. Effectief aan boord nemen vermindert tijd aan waarde en plaatst de stichting voor langdurige klantenbehoud en groei.

### Zakelijke impact

Organisaties met gepersonaliseerde instapprogramma&#39;s realiseren zich doorgaans in de eerste 90 dagen een toename van 50-60% van de acceptatie van functies, wat rechtstreeks bijdraagt aan hogere retentie- en uitbreidingsinkomsten.

### Uitvoeren

Gebruik het [&#x200B; Multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) aan orchestrate onboarding opeenvolgingen die aan product, planrij, en klantensegment worden aangepast. Dit patroon ondersteunt op mijlpaal gebaseerde progressie, zodat klanten in elke fase van hun instapsysteem de juiste richtlijnen krijgen.

### Technische overwegingen

- De telemetrie van het productgebruik van de samenvatting om aan boord tredende mijlpalen (eerste login, aanvankelijke configuratie, eerste voltooide werkschema) te volgen en de volgende reisstap dienovereenkomstig teweegte.
- Wijs de profielen van de klant aan het correcte onboarding spoor toe dat op product, planrij, en aantal vergunning gegeven gebruikers wordt gekocht.
- De gegevens van het platform van het de succesplatform van de klant aan de scores van de oppervlaktegezondheid en vlaggen op risico voor pro-actieve interventie integreren.
- Sync on boarding status and adoptie metrics back to [!DNL Salesforce] or [!DNL Microsoft Dynamics] so customer success managers can priority outreach.


## Campagnes voor verlenging van contracten

Neem proactief klanten aan die contractvernieuwing naderen met gepersonaliseerde aanbiedingen, gebruiksinzichten en vernieuwingsstimulansen. Tijdige, gegevensgestuurde verlengingsoutreach vermindert de klanken en beschermt terugkerende inkomsten.

### Zakelijke impact

De bedrijven die pro-actieve, gepersonaliseerde vernieuwingscampagnes uitvoeren zien typisch een verhoging van 30-40% in vernieuwingstarief, beschermend terugkomende opbrengst en verminderend de kosten van klantenheraanschaf.

### Uitvoeren

Gebruik de [&#x200B; Reis van het Kanaal met het Beslissen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon om de juiste vernieuwingsaanbieding door het juiste kanaal in de juiste tijd te leveren. Dit patroon combineert reisorchestratie met het geven van beslissingen, waardoor dynamische vernieuwingsstimulansen mogelijk worden op basis van de waarde en het gebruik van de rekening.

### Technische overwegingen

- Stel de einddatums van het contract, de voorwaarden voor verlenging en de waarde van de account in op [!DNL Salesforce] of [!DNL Microsoft Dynamics] om verlengingen te starten tijdens de juiste aanlooptijd (bijvoorbeeld 90, 60, 30 dagen uit).
- Gegevens over het productgebruik en de gezondheidscores van de klant opnemen om het risico op verlenging te bepalen en de aanbiedingsstrategie dienovereenkomstig aan te passen.
- Gebruik een beslissing om de optimale stimulans voor verlenging (korting, uitgebreide voorwaarden, upgrade van de premie) te selecteren op basis van de levensduurwaarde van de account en de waarschijnlijkheid van de omslag.
- Coördineer vernieuwingsoutreach met klantensucces en verkoopteams om tegenstrijdige berichten door [!DNL Marketo Engage] en de taaktoewijzing van CRM te vermijden.


## Upsell- en uitbreidingsmogelijkheden

Identificeer klanten klaar voor productverbeteringen of extra vergunningen die op gebruikspatronen, de groeiindicatoren, en gegevens van het klantensucces worden gebaseerd. De pro-actieve uitbreidingsoutreach maakt klantendynamiek in opbrengstgroei.

### Zakelijke impact

Organisaties die systematisch uitbreidingssignalen identificeren en op zich nemen produceren typisch een verhoging van 20-30% van uitbreidingsopbrengst, verbeterend netto opbrengstbehoud en waarde van het klantenleven.

### Uitvoeren

Gebruik de [&#x200B; Reis van het Kanaal met Beslissing &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon om gepersonaliseerde upsell en uitbreidingsaanbiedingen te leveren die op gebruik in real time en rekeningssignalen worden gebaseerd. Dit patroon gebruikt besluiten om elke rekening met het meest relevante uitbreidingsaanbod over kanalen aan te passen.

### Technische overwegingen

- Vermeld de telemetrie van het productgebruik om uitbreidingssignalen zoals de drempels van het vergunningsgebruik, eigenschapplafondhits, en het groeiende aantal gebruikers te ontdekken.
- Bouw op accountniveau aandrijvingsmodellen die historische uitbreidingsgegevens, gebruikstrends, en firmografische attributen gebruiken.
- De uitbreidingsmogelijkheden van de synchronisatie en geadviseerde aanbiedingen terug aan [!DNL Salesforce] of [!DNL Microsoft Dynamics] zodat kunnen de verkoopteams op marketing-geproduceerde pijpleiding volgen.
- Coördineer met [!DNL Marketo Engage] om ervoor te zorgen dat het uitbreidingsoverseinen niet met aan de gang zijnde steun of vernieuwingsmededelingen conflicteert.


## Vervangingscampagnes voor concurrenten

De vooruitzichten van het doel die concurrerende producten met gepersonaliseerde overseinen, migratieaanbiedingen, en concurrerende vergelijkingen gebruiken. Door de specifieke knelpunten aan te pakken verbonden aan elke concurrent, kunnen de marketing teams effectiever onderscheiden en schakelen besluiten versnellen.

### Zakelijke impact

B2B-organisaties die gerichte concurrentiële vervangingscampagnes voeren, behalen doorgaans een stijging van 15-25% van de concurrerende win-winrente, waardoor het marktaandeel wordt overgenomen en gevestigde leveranciers worden verdrongen.

### Uitvoeren

Gebruik het [&#x200B; Multi-Step Orchestrated Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) patroon om multi-aanraak concurrerende campagnes te ordenen die aan de specifieke concurrent en het vooruitgangsprofiel worden aangepast. Dit patroon steunt voorwaardelijke vertakking die op geïdentificeerde concurrent wordt gebaseerd, toelatend overseinen die de unieke pijnpunten van elk concurrerend scenario richten.

### Technische overwegingen

- Integreer concurrerende inlichtingengegevens (bijvoorbeeld technologieleveranciers, gebieden van de concurrent CRM) in het verenigde profiel om te bepalen welke concurrent momenteel een vooruitzicht gebruikt.
- Concurrentiespecifieke content-elementen maken (migratiehulplijnen, vergelijkingsbladen, ROI-rekenmachines) en deze toewijzen aan blokken met reisinhoud.
- Coördineer met [!DNL Marketo Engage] om concurrentiecampagnes voor vooruitzichten te onderdrukken reeds in actieve verkoopcycli of bestaande klanten.
- Houd een concurrerende verschuivingspijplijn bij in [!DNL Salesforce] of [!DNL Microsoft Dynamics] met toegewezen campagnetoewijzing om de doeltreffendheid van het programma te meten.


## Webinar- en demo-planning

Personaliseer webinar uitnodigingen en demo planning op basis van de belangen van het vooruitzicht, de industrie, en betrokkenheidsgeschiedenis. Relevante, geschikte uitnodigingen verhogen de aanwezigheid en produceren een pijpleiding van hogere kwaliteit van levende interactie.

### Zakelijke impact

Gepersonaliseerde webinar- en demo-uitnodigingsprogramma&#39;s zorgen doorgaans voor een toename van het aantal webinar-deelnemers met 35-45%, waardoor meer gekwalificeerde pijpleidingen van de mogelijkheden voor live service worden verwijderd.

### Uitvoeren

Gebruik het [&#x200B; gebeurtenis-teweeggebrachte patroon van het Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) om gepersonaliseerde uitnodigingen te verzenden wanneer de vooruitzichten rentesignalen tonen die met volgende webinar of demo onderwerpen worden gericht. Dit patroon reageert in real time op gedragtriggers en zorgt ervoor dat uitnodigingen aankomen wanneer de interesse het hoogst is.

### Technische overwegingen

- Definieer op rente gebaseerde triggergebeurtenissen (bijv. bezoeken van een productpagina, downloaden van een verwante bron, verbinden met een vergelijking van concurrenten) die zich uitlijnen op geplande webinar- of demo-onderwerpen.
- Gegevens van webinar-platformen (bijvoorbeeld [!DNL ON24], [!DNL Zoom Webinar] ) integreren om de registratie-, aanwezigheids- en betrokkenheidswaarden in het uniforme profiel te volgen.
- Synchroniseer demoverzoeken en planningsgegevens met [!DNL Salesforce] of [!DNL Microsoft Dynamics] om ervoor te zorgen dat verkoopteams tijdig meldingen en context ontvangen.
- Coördineer uitnodigingsinterface met communicatielimieten van [!DNL Marketo Engage] om te voorkomen dat er overberichtperspectieven zijn die in aanmerking komen voor meerdere gebeurtenissen.


## Casestudy en ROI Personalization

Lever gepersonaliseerde gevallenstudies, ROI calculators, en succesverhalen die op de industrie van het vooruitzicht, bedrijfsomvang, en gebruiksgeval worden gebaseerd. Wanneer de vooruitzichten proefpunten van organisaties gelijkend op hun zien, bouwt het vertrouwen sneller en koopt besluiten versnelt.

### Zakelijke impact

Organisaties die inhoud op basis van proefpunten personaliseren, zien doorgaans een toename van 25-35% in de betrokkenheid van de studie bij gevallen, wat bijdraagt aan een groter vertrouwen in de deal en snellere close rates.

### Uitvoeren

Gebruik het [&#128279;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) patroon van het Web/App Personalization van 0&rbrace; Known-Bezoeker &lbrace;om de meest relevante casestudies en het bewijs van ROI dynamisch te oversteken dat op het profiel van elk vooruitzicht wordt gebaseerd. Dit patroon past bezoekerskenmerken aan een inhoudsbibliotheek aan, zodat elk vooruitzicht proefpunten van hun industrie en peer groep ziet.

### Technische overwegingen

- U kunt het hoofdlettergebruik en de ROI-inhoud voorzien van tags met metagegevens (industrie, bedrijfsgrootte, gebruiksscenario, product), zodat dynamische overeenkomsten mogelijk zijn met perspectiefprofielen.
- Voer verpersoonlijkingsregels uit die de industrie voorrang geven aanpassen eerst, toen bedrijfsomvang en gebruikscase, met reserveinhoud voor vooruitzichten met beperkte profielgegevens.
- Integreer de signalen van de inhoudsbetrokkenheid (downloads, tijd op pagina, aandelen) terug in het verenigde profiel om loodscoring en verkoopbereik te informeren.
- Coördineren met [!DNL Marketo Engage] om persoonlijke inhoud met een proefpunt op te nemen in e-mailsequenties die u maakt, en niet alleen op locatie.


## Programma&#39;s voor klantenondersteuning

Identificeer en verbind tevreden klanten voor beplechtigingskansen zoals verwijzingen, gevallenstudies, en getuigenissen die op gebruik en tevredenheidsgegevens worden gebaseerd. Tevreden klanten zijn een krachtige groeimotor wanneer zij worden erkend en uitgenodigd om hun succes te delen.

### Zakelijke impact

Gestructureerde programma&#39;s voor klantbehartiging leiden doorgaans tot een toename van 20-30% van de deelname aan belangenbehartiging, wat leidt tot een gestage stroom van referenties, casestudies en getuigenissen die nieuwe bedrijfsverwerving ondersteunen.

### Uitvoeren

Gebruik het [&#x200B; Multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) om vooraanstaande identificatie en betrokkenheidswerkschema&#39;s te bouwen die aan tevredenheid en gebruikssignalen antwoorden. Dit patroon ondersteunt progressieve pleitbezorging, te beginnen met een lichte deelname (bijvoorbeeld een herziening) en het doorvoeren naar diepere toezeggingen (bijvoorbeeld een referentie- of casestudy).

### Technische overwegingen

- Resultaten van het Ingest tevredenheidsonderzoek (bijvoorbeeld, de Netto Score van de Bevorder, de scores van de klantentevredenheid) en de gegevens van het productgebruik om een beplechtigingsbereidheid voor elke rekening te bouwen.
- Bepaal ontvankelijkheidscriteria voor pleitbezorgers die tevredenheidsdrempels, gebruiksmijlpalen, en rekeningstijd combineren om voortijdige outreach te vermijden.
- Synchroniseer de status van uw voorstanders en de deelnemingshistorie terug naar [!DNL Salesforce] of [!DNL Microsoft Dynamics] , zodat verkoopteams tijdens het zoeken kunnen verwijzen naar voorstanders van de klant.
- Coördineer met [!DNL Marketo Engage] om het bereiken van voorkeuren tijdens actieve supportescalaties of verlengingsonderhandelingen te onderdrukken.
