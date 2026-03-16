---
title: Gebruiksscenario's voor financiële services
description: Ontdek hoe financiële dienstenorganisaties Adobe Experience Platform gebruiken om productaanbiedingen te personaliseren, karretjes te verhinderen, en klantenverhoudingen te verdiepen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2209'
ht-degree: 1%

---


# Gebruiksscenario&#39;s voor financiële services

Financiële-dienstenorganisaties vertrouwen erop dat Adobe Experience Platform klantgegevens in alle bancaire, kredietverlenings- en investeringskanalen verenigt, waardoor gepersonaliseerde ervaringen mogelijk worden die relaties versterken en de groei stimuleren. Door de activiteiten van de rekening, de transactiegeschiedenis, en gedragssignalen samen te brengen, kunnen deze organisaties het juiste aanbod op het juiste ogenblik leveren terwijl het handhaven van het vertrouwen en de naleving hun klanten verwachten.

## Hoogwaardige lead-curturing

Identificeer hoogwaardige vooruitzichten die op profielgegevens en gedrag worden gebaseerd, dan verberg hen met gepersonaliseerde inhoud en aanbiedingen door geautomatiseerde reizen. Door demografische details, het doorbladeren van activiteit, en betrokkenheidssignalen te combineren, kunnen financiële instellingen prioriteit geven aan de leads die het meest waarschijnlijk zijn om ze om te zetten en te begeleiden via een op maat gemaakt pad naar het worden van klanten.

### Zakelijke impact

Organisaties die hoogwaardige loodzorg implementeren zien doorgaans een stijging van 25-35% in de conversiekoersen van lood naar klant terwijl ze een gezondere, voorspelbaardere verkooppijplijn bouwen.

### Uitvoeren

Gebruik het [ Multi-Step Orchestrated patroon van de Reis ](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) om geautomatiseerde opeenvolgingen te bouwen van de Zorg die zich baseert op de signalen van de perspectiefbetrokkenheid en van de bereidheid aanpast.

### Technische overwegingen

- Gegevens en gedragsgebeurtenissen voor CRM-lead-scoring integreren in uniforme perspectiefprofielen om toegang tot en vertakkende logica voor reizen mogelijk te maken.
- Ervoor zorgen dat op elk aanspreekpunt toestemming en opt-in-voorkeuren worden toegepast, met name voor telefonische en e-mailcontacten die onder de financiële marketingregels vallen.
- Vorm reis throttling om overweldigende vooruitzichten met veelvoudige mededelingen tijdens korte evaluatievensters te vermijden.
- Zorg voor gegevenslatentie tussen de interactie van de afdeling of de adviseur en digitale betrokkenheid om het koepelbericht relevant te houden.


## Productaanbeveling voor bestaande klanten

Aanbevolen relevante financiële producten zoals creditcards, leningen en beleggingsproducten aan bestaande klanten op basis van hun profiel, transactiegeschiedenis en levensfase. Met dit gebruiksscenario worden gegevens van dagelijkse accounts omgezet in actioneerbare inzichten die het op een na beste product voor elke klant bieden.

### Zakelijke impact

De gepersonaliseerde productaanbevelingen drijven een verhoging van 20-30% van productadoptie en meetbaar verhogen de waarde van het klantenleven door het portefeuilleaandeel te verdiepen.

### Uitvoeren

Gebruik het [ patroon van Offer Decisioning ](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md) om elke klant tegen in aanmerking komende productaanbiedingen in real time te evalueren, die aanbevelingen door relevantie en bedrijfsprioriteit rangschikken.

### Technische overwegingen

- Transactiegegevens, rekeningssaldi, en productbezit verenigen in één enkel klantenprofiel zodat de beslissingsmodellen een volledig overzicht van bestaande verhoudingen hebben.
- Pas regels inzake financiële geschiktheid en wettelijke toelatingsbeperkingen toe als harde garanties binnen de beslissingsmotor alvorens aanbiedingen te rangschikken.
- Coördineer de aanbieding van levering over online bankieren, mobiele app, e-mail, en adviseurskanalen om tegenstrijdige of dubbele aanbevelingen te verhinderen.
- Uitvoering van frequentieclausule per productcategorie om moeheid bij aanbevelingen te voorkomen, met name voor producten met een hoge afweging, zoals hypotheken en beleggingsrekeningen.


## Churn Prevention Campaigns

Klanten identificeren die het risico lopen te klappen met behulp van door AI aangedreven kinnevoorspelling en hen met bewaaraanbiedingen en gepersonaliseerde communicatie in dienst nemen. Vroege detectie van terugtrekkingssignalen stelt financiële instellingen in staat om te interveniëren voordat een klant rekeningen sluit of activa elders verplaatst.

### Zakelijke impact

De pro-actieve inspanningen van de kartonpreventie verminderen typisch klantenvermindering met 15-25%, beschermend terugkomende opbrengststromen en verminderend de kosten van klantenvervanging.

### Uitvoeren

Gebruik de [ Reis van het Kanaal met Beslissing ](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon om bewaarritten teweeg te brengen wanneer de duim-risico scores bepaalde drempels overschrijden, met ingebedde beslissing om de meest dwingende bewaaraanbieding te selecteren.

### Technische overwegingen

- Tendensen van de de rekeningsactiviteit van het voer, de de interactiegeschiedenis van de dienst, en betrokkenheidsfrequentie in [!DNL Customer AI] churn aandrijvingsmodellen om risicoscores te produceren.
- Vaststellen van drempelwaarden voor het churn-risico specifiek voor productlijnen, aangezien de terugtrekkingssignalen voor het controleren van rekeningen verschillen van die voor beleggingsportefeuilles.
- Zorgen voor de handhaving van de aanbiedingen, zodat zij voldoen aan de voorschriften inzake eerlijke kredietverlening en gelijke behandeling, zodat hoogrisicosegmenten een billijke behandeling krijgen.
- Bouw suppressielogica om klanten uit te sluiten die door fraude of nalevingsacties worden gejaagd, waar de behoudoutreach ongepast zou zijn.


## Persoonlijk accountdashboard

Pas het dashboard voor online bankieren en de mobiele app-ervaring aan op basis van de activiteiten, voorkeuren en financiële doelstellingen van elke klant. Een op maat gemaakt dashboard helpt klanten te vinden wat het belangrijkst is en oppervlakken relevante inzichten zonder hen te vereisen om te zoeken.

### Zakelijke impact

Gepersonaliseerde dashboards verhogen de betrokkenheidspercentages met 30-40% en verbeteren op betekenisvolle wijze de score voor klanttevredenheid door digitaal bankieren intuïtief en relevant te maken.

### Uitvoeren

Gebruik het ](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) patroon van het Web/App Personalization van 0} Known-Bezoeker {om gepersonaliseerde inhoudsblokken, productspots, en financiële inzichten binnen voor authentiek verklaarde digitale ervaringen in real time te leveren.[

### Technische overwegingen

- Hefboomwerking [!DNL Edge Network] voor subseconden personaliseringsbesluiten binnen voor authentiek verklaarde bankzittingen waar de latentie gebruikerservaring direct beïnvloedt.
- Samengevoegde transactiegegevens in vooraf berekende profielkenmerken zoals uitgavencategorieën en spaartrends om real-time berekening van grote gegevenssets te voorkomen.
- Voldoe aan toegankelijkheidsnormen en zorg ervoor dat gepersonaliseerde inhoud voldoet aan dezelfde openbaarmakingsvereisten als statische inhoud.
- Coördineer personalisatielogica tussen web en mobiele kanalen zodat de klanten een verenigbare ervaring ongeacht apparaat zien.


## Levensfase-gebaseerde productaanbiedingen

Identificeer klanten die nieuwe levensstadia ingaan zoals huwelijk, huisaankoop, of pensioen en proactief relevante financiële producten en diensten aanbieden. Door te anticiperen op deze mijlpalen kunnen instellingen zichzelf als vertrouwde partners positioneren tijdens cruciale financiële momenten.

### Zakelijke impact

De levensfase-teweeggebrachte aanbiedingen bereiken een 35-45% productadoptiepercentage, beduidend overtreft generische campagnes, terwijl het versterken van klantenverhoudingen op lange termijn.

### Uitvoeren

Gebruik de [ Reis van het Kanaal met Beslissing ](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon om de indicatoren van het levensstadium te ontdekken en multi-aanrakingsreizen met ingebedde aanbiedingsselectie te ordenen die aan elke mijlpaal wordt aangepast.

### Technische overwegingen

- Combineer eerderesignalen zoals adresveranderingen, gezamenlijke rekeningsopeningen, en grote deposito&#39;s met toegelaten derdegegevens om de overgangen van het levensstadium af te leiden.
- Verwerk gevoelige levensgebeurtenissen met zorg in berichttoon en frequentie, aangezien onjuist afgeleide mijlpalen het vertrouwen kunnen uithollen.
- De controles van de regelgevende geschiktheid van de laag in aanbiedingsbesluit zodat de geadviseerde producten zich op de geverifieerde financiële situatie van de klant richten.
- Afkoelingsperiodes maken tussen levensfase-campagnes om overlappende outreach te voorkomen wanneer meerdere indicatoren in een kort venster branden.


## Transactiegerichte waarschuwingen en aanbevelingen

Verzend waarschuwingen in real time voor transacties en verstrek gepersonaliseerde aanbevelingen die op uitgavenpatronen en rekeningsactiviteit worden gebaseerd. Tijdige, relevante berichten houden klanten op de hoogte en creëren natuurlijke momenten om nuttige financiële begeleiding te bieden.

### Zakelijke impact

Transactiegerichte waarschuwingen behalen een betrokkenheidspercentage van 50-60%, waardoor het beveiligingsbewustzijn aanzienlijk wordt verbeterd en waardevolle aanraakpunten voor gepersonaliseerde aanbevelingen worden gecreëerd.

### Uitvoeren

Gebruik het [ gebeurtenis-teweeggebrachte patroon van het Overseinen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) om aan transactiegebeurtenissen in echt te antwoorden - tijd met alarm en contextafhankelijke aanbevelingen.

### Technische overwegingen

- Zet transactiegebeurtenissen door een het stromen pijpleiding met laag-latentie leveringsvereisten, aangezien de veiligheidsalarm waarde verliest als meer dan een paar minuten wordt vertraagd.
- Pas klant-bepaalde waakzame voorkeur en drempels toe zodat wijzen de berichten op individuele montages eerder dan enig-grootte-pasvorm-alle regels.
- Scheid verplichte veiligheidsalarm van facultatieve aanbevelingen in de overseinenarchitectuur om ervoor te zorgen de nalevingsberichten nooit worden onderdrukt.
- Zorg voor hoge transactievolumes tijdens piekperiodes, zoals dagen en feestdagen, door een doorvoercapaciteit te ontwerpen die schaalt met de vraag.


## Terugwinning van creditcardtoepassing

Identificeer klanten die begonnen maar geen creditcardtoepassingen voltooiden en hen met gepersonaliseerde overseinen en aanbiedingen opnieuw in dienst nemen. De beëindiging van de toepassing vertegenwoordigt een hoog-intent publiek dat vaak slechts een kleine verschuiving nodig heeft om het proces te voltooien.

### Zakelijke impact

De campagnes van het terugwinnen van de landingen verbeteren het percentage van de toepassingsvoltooiing met 20-30%, direct verhogend nieuwe rekeningsverwerving van een publiek dat reeds belangstelling heeft getoond.

### Uitvoeren

Gebruik het [ gebeurtenis-teweeggebrachte patroon van het Overseinen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) om de gebeurtenissen van de toepassingsontkenning te ontdekken en geschikte follow-up berichten teweeg te brengen die gemeenschappelijke drop-off redenen richten.

### Technische overwegingen

- Leg de specifieke stap vast waar de toepassing is verlaten om berichten op maat te maken, aangezien iemand die bij identiteitsverificatie is afgebroken andere betrouwbaarheid nodig heeft dan iemand die de status heeft gecontroleerd.
- Voldoen aan de voorschriften inzake kredietmarketing, met inbegrip van de vereiste informatieverschaffing en de regels inzake billijke kredietverschaffing in alle terugvorderingsmededelingen.
- Implementeer logica voor tijdverval, zodat de hersteloutreach stopt na een gedefinieerd venster, aangezien de gegevens van een verouderde toepassing mogelijk niet langer geldig zijn voor voorkwalificatie.
- Coördineren met het toepassingssysteem om herstelberichten te onderdrukken voor aanvragers die via een ander kanaal, zoals een bezoek van een filiaal of een telefoongesprek, hebben voltooid.


## Portfolio-aanbevelingen voor investeringen

Verstrek gepersonaliseerde beleggingsaanbevelingen die op het risicoprofiel van elke klant, investeringsgeschiedenis, en financiële doelstellingen worden gebaseerd. Met behulp van gegevensgestuurde portfoliobegeleiding kunnen klanten geïnformeerde beslissingen nemen en tegelijkertijd hun betrokkenheid bij services voor vermogensbeheer versterken.

### Zakelijke impact

Aanbevolen aanbevelingen voor gepersonaliseerde investeringen stimuleren een toename van 25-35% in de acceptatie van beleggingsproducten en verbeteren de diversificatie van de portefeuille in de gehele klantenbasis.

### Uitvoeren

Gebruik het ](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md) patroon van de Aanbeveling van het Gedrag [ {om investeringsgedrag en voorkeur te analyseren, dan oppervlakte relevante portefeuillereaanbevelingen door digitale kanalen en adviseurshulpmiddelen.

### Technische overwegingen

- Integreer brokerage- en bewaargegevens om een nauwkeurige, actuele weergave van de actuele belangen en allocatie van elke klant te behouden.
- Naleving van de in de effectenvoorschriften voorgeschreven geschiktheidsvereisten, zodat de aanbevelingen in overeenstemming zijn met de door de klant gedocumenteerde risicotolerantie en beleggingsdoelstellingen.
- Persoonlijke beleggingsinhoud duidelijk als educatief of informatief aanduiden waar dat nodig is, en onderscheiden van formele beleggingsadviezen die fiduciaire verplichtingen inhouden.
- Vernieuw aanbevelingsmodellen op een regelmatige snelheid om rekening te houden met marktverschuivingen, het wegvallen van portfolio&#39;s en wijzigingen in klantdoelstellingen.


## Fraud Alert Personalization

Pas fraudealarm en veiligheidsmededelingen aan die op de communicatie voorkeur van elke klant en het verleden interactiegeschiedenis worden gebaseerd. Door op maat gemaakte waarschuwingen neemt de kans toe dat klanten kritieke beveiligingsmeldingen opmerken, begrijpen en verwerken.

### Zakelijke impact

Gepersonaliseerde fraudewaarschuwingen verbeteren de responspercentages voor waarschuwingen met 40-50%, waardoor de naleving van de beveiligingsvoorschriften aanzienlijk wordt verbeterd en de blootstellingsperiode tijdens verdachte activiteiten aanzienlijk wordt verkort.

### Uitvoeren

Gebruik het [ gebeurtenis-teweeggebrachte patroon van het Overseinen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md) om fraudealarm door het aangewezen kanaal van elke klant met contextafhankelijke details te leveren die het gemakkelijk maken om activiteit te bevestigen of te bevechten.

### Technische overwegingen

- Prioriteit geven aan de snelheid en betrouwbaarheid van de levering boven alle andere overwegingen in verband met het ontwerp, aangezien de waarschuwing voor fraude direct verband houdt met de blootstelling aan financieel verlies.
- Het alarm van de route door het geverifieerde aangewezen kanaal van de klant terwijl het handhaven van reservekanalen om levering te verzekeren zelfs als het primaire kanaal ontbreekt.
- De geschiedenis van de waarschuwingsinteractie van de opslag om toekomstige waakzaamheid te verbeteren en vals-positieve moeheid voor klanten te verminderen die vaak reizen of atypische aankopen maken.
- Zorgen dat alle inhoud en workflows voor fraudewaarschuwingen voldoen aan de beveiligingsvoorschriften van het bankwezen en geen gevoelige rekeninggegevens in voorvertoningen van berichten of onderwerpregel toegankelijk maken.


## Loyalty Program Engagement

Personaliseer de mededelingen van het loyaliteitsprogramma, beloningen, en aanbiedingen die op de rij van elke klant, puntbalans, en terugkoopgeschiedenis worden gebaseerd. Relevante, geschikte loyaliteitsmededelingen houden leden betrokken en drijven hogere programmaparticipatie.

### Zakelijke impact

De persoonlijke loyaliteitsbetrokkenheid verhoogt de programmaparticipatie met 30-40% en drijft meetbaar hogere puntaflossing, die de waardeperceptie van het programma versterkt.

### Uitvoeren

Gebruik de [ Reis van het Kanaal met Beslissing ](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon om loyaliteitsmededelingen over kanalen, met ingebedde beslissing te ordenen om de meest relevante beloning of de aanbieding voor elk lid te selecteren.

### Technische overwegingen

- Synchroniseer gegevens van het loyaliteitsplatform met inbegrip van rij status, puntsaldi, en terugkoopgeschiedenis in klantenprofielen op een bijna-real-time basis om het bevorderen van verlopen of onnauwkeurige saldi te vermijden.
- De reislogica van het segment door tier om onderscheiden ervaringen te leveren, aangezien de high-tier leden exclusieve behandeling en vroege toegang tot bevorderingen verwachten.
- Coördineer loyaliteitsoverseinen met bredere marketing campagnes om berichtvermoeidheid en conflicterende aanbiedingen over programma&#39;s te verhinderen.
- Terugbetalingsattributie van het spoor over kanalen om te meten welke gepersonaliseerde mededelingen het hoogste programmarendement op investering drijven.


## Voorkeurscampagnes voor hypotheken

Doelklanten die waarschijnlijk op de markt zullen zijn voor een hypotheek op basis van profielgegevens, gedragssignalen en indicatoren voor de levensfase. De pro-actieve outreach van de pregoedkeuring plaatst de instelling als geschikte eerste keus tijdens één van de grootste financiële besluiten een klant zal nemen.

### Zakelijke impact

Gerichte hypotheekpretoetredingscampagnes verhogen de toepassingspercentages met 20-30% en verbeteren het volume van de leningverstrekking door op het juiste moment gekwalificeerde vooruitzichten te bereiken.

### Uitvoeren

Gebruik het ](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md) patroon van de Reis van meerdere stappen [ Orchestrated om hypotheekvooruitzichten door een multi-aanraking opeenvolging van de Aansporing van bewustzijn door pre-goedkeuring te begeleiden, die op overeenkomst en kwalificatiesignalen wordt gebaseerd.

### Technische overwegingen

- Combineer het gedrag van het bezitsonderzoek, de tendensen van de spaargroei, en de signalen van de huurvervaldatum om een nevenmodel te bouwen dat waarschijnlijke hypotheekzoekers identificeert.
- Ervoor zorgen dat alle berichten vóór goedkeuring voldoen aan de voorschriften voor hypothecaire reclame, inclusief vereiste informatie, tariefnauwkeurigheid en gelijke huisvestingstaal.
- Coördineer de campagnemonttiming met veranderingen in de tariefomgeving zodat de outreach zich op gunstige leningsvoorwaarden richt en verouderde renteferenties vermijdt.
- De workflows voor overdracht aan uitleningsfunctionarissen opbouwen zodat digitaal gekoesterde mensen vloeiend overstappen op het formele toepassings- en verzekeringsproces.


## Inhoud voor gepersonaliseerde financiële educatie

Lever persoonlijke inhoud, tips en bronnen voor financiële educatie op basis van het financiële profiel, de doelstellingen en de belangen van elke klant. Relevante educatieve inhoud creëert vertrouwen, verbetert de financiële kennis en schept biologische mogelijkheden om relevante producten in te voeren.

### Zakelijke impact

Inhoud voor gepersonaliseerd onderwijs verhoogt de betrokkenheid bij inhoud met 25-35% en verbetert de financiële kennis van klanten, wat op zijn beurt weer leidt tot meer betrouwbare productacceptatie.

### Uitvoeren

Gebruik de [ Reis van het Kanaal met Beslissing ](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon om een gekrulde opeenvolging van educatieve inhoud over kanalen te leveren, gebruikend besluit om onderwerpen aan de financiële situatie en belangen van elke klant aan te passen.

### Technische overwegingen

- Wijs educatieve inhoud toe aan kenmerken van financiële profielen zoals de verhouding tussen de schuld en het inkomen, het spaarpercentage en de ervaring met investeringen om de relevantie van onderwerpen te verzekeren.
- Inhoud met moeilijkheidsniveaus en in de eerste plaats vereiste onderwerpen coderen om progressieve leerpaden te bouwen in plaats van losgekoppelde eenmalige artikelen te leveren.
- De overeenkomst van de inhoud van het spoor op het onderwerpniveau om personalisatiemodellen te verfijnen en opkomende belangengebieden over de klantenbasis te identificeren.
- Ervoor zorgen dat educatieve inhoud duidelijk wordt onderscheiden van productmarketing om naleving van de regelgeving te handhaven en het vertrouwen van de klant in de objectiviteit van het programma te behouden.
