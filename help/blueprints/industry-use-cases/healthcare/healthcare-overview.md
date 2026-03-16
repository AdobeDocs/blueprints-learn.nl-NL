---
title: Gevallen voor gebruik in de gezondheidszorg
description: Ontdek hoe zorgorganisaties Adobe Experience Platform gebruiken om de betrokkenheid van patiënten te verbeteren, de coördinatie van de zorg te stroomlijnen en betere gezondheidsresultaten te bevorderen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2356'
ht-degree: 1%

---


# Gevallen voor gebruik in de gezondheidszorg

Gezondheidszorgorganisaties gebruiken Adobe Experience Platform om uniforme patiëntenprofielen te maken en persoonlijke, actuele communicatie op elk aanraakpunt mogelijk te maken. Door klinische, gedrags- en voorkeursgegevens op één locatie aan te sluiten, kunnen zorgteams patiënten effectiever betrekken bij het handhaven van de hoogste normen op het gebied van privacy en naleving.

## Automatisering van benoemingsherinnering

Stuur persoonlijke herinneringen voor afspraak via e-mail, tekstbericht en pushberichten op basis van de communicatievoorkeuren en het type afspraak van elke patiënt. Geautomatiseerde herinneringen verminderen gemiste afspraken en houden de schema&#39;s vlot, zodat het personeel zich kan concentreren op de patiëntenzorg.

### Zakelijke impact

Organisaties die automatische herinneringen voor benoemingen implementeren zien doorgaans een verbetering van 30 tot 40 procent in hun aanstelling in percentages en een aanzienlijke vermindering van kostbare no-shows.

### Uitvoeren

Gebruik het [ gebeurtenis-teweeggebrachte patroon van het Overseinen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Het creëren en bijwerken van benoemingen van gebeurtenissen van het planningssysteem dienen als natuurlijke trekkers voor geschikte, relevante herinneringsberichten.

### Technische overwegingen

- Ervoor zorgen dat alle contactgegevens van de patiënt en de aanstellingsgegevens worden verzonden en opgeslagen in overeenstemming met de HIPAA-vereisten, met passende labels voor gegevensgebruik om ongeoorloofde toegang te beperken.
- Integreer met het elektronische systeem voor het plannen van de gezondheidsverslagen om benoeming te vangen creatie, annulering, en herplanningsgebeurtenissen in echt - tijd.
- Beleid voor het beheer van toestemmingen toepassen, zodat herinneringen alleen worden verzonden via kanalen waartoe de patiënt expliciet heeft besloten.
- Vorm suppressieregels om dubbele of bovenmatige herinneringen te verhinderen wanneer de benoemingen in snelle opeenvolging worden opnieuw gepland.


## Campagnes voor therapietrouw

Verstuur persoonlijke herinneringen en trainingsmateriaal om patiënten te helpen bij het volgen van hun medicatieschema en behandelingsplannen. Op maat gesneden berichten op basis van medicatietype, doseringsschema en patiëntengeschiedenis zorgen voor betere therapietrouw en betere gezondheidsresultaten.

### Zakelijke impact

Persoonlijke therapietrouw-campagnes leiden doorgaans tot een verbetering van de therapietrouw met 20 tot 30 procent, wat meetbaar tot betere gezondheidsresultaten en minder ziekenhuisopnames leidt.

### Uitvoeren

Gebruik het [ multi-Step Orchestrated patroon van de Reis ](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). De therapietrouw van geneesmiddelen vereist een duurzame, multi-touchaanpak met escalerende herinneringen, educatieve aanraakpunten en follow-up check-ins gedurende de loop van een behandelingsplan.

### Technische overwegingen

- Pas strikte etiketten voor gegevensgebruik toe op alle beschermde gezondheidsinformatie met betrekking tot medicatie- en diagnosegegevens om te voorkomen dat onbevoegde downstreamactivering plaatsvindt.
- Integreer met systemen voor de registratie van geneesmiddelen en elektronische medische dossiers om gegevens te ontvangen die op recept worden ingevuld en nagevuld en die de trajecten van de reis in gang zetten.
- Voer een krachtig beheer van de toestemming uit om ervoor te zorgen dat patiënten ermee hebben ingestemd geneesmiddelen te ontvangen en de toestemming op elk moment kunnen intrekken.
- Ontwerpen van reislogica om niet-betrokkenheidspatronen op te sporen en escaleren naar meldingen voor zorgteams wanneer een patiënt het risico loopt niet te worden onderschreven.


## Herinneringen voor preventieve zorg

Patiënten proactief herinneren aan aanbevolen preventieve zorg zoals vaccinaties, screenings en jaarlijkse controles op basis van hun leeftijd, medische geschiedenis en risicofactoren. Tijdige herinneringen aan de preventieve zorg helpen de lacunes in de zorg te dichten en de algehele volksgezondheid te verbeteren.

### Zakelijke impact

Proactieve preventieve zorg leidt doorgaans tot een stijging van 25 tot 35 procent van het aantal voltooide preventieve zorg, wat bijdraagt tot een betere volksgezondheid en lagere kosten voor langdurige behandeling.

### Uitvoeren

Gebruik het [ Uitgaande patroon van de Activering van het Bericht van de Partij ](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Herinneringen voor preventieve zorg kunnen het best worden geleverd door middel van geplande batchcampagnes die de geschiktheid van de patiënt toetsen aan klinische richtlijnen op een reguliere kadentie.

### Technische overwegingen

- Creëer publiekssegmenten aan de hand van criteria van klinische richtsnoeren (leeftijd, geslacht, familiegeschiedenis, voorafgaande screeningdata) en pas gegevensgebruikslabels toe op alle beschermde gezondheidsinformatie die in segmentatie wordt gebruikt.
- Coördineren met klinische teams om te zorgen voor de inhoud van de herinnering, in overeenstemming met de huidige empirisch onderbouwde richtsnoeren voor preventieve zorg en organisatorische protocollen.
- Implementeer frequentiecategorieën om overweldigende patiënten te voorkomen die tegelijkertijd in aanmerking komen voor meerdere aanbevelingen voor preventieve zorg.
- Handhaaf een audittrail van alle preventieve zorgmededelingen die voor regelgevende rapportage en documentatie over kwaliteitsmaatstaven worden verzonden.


## Follow-upcampagnes na bezoek

Automatisch enquêtes, zorginstructies en herinneringen voor de follow-up verzenden na het bezoek en op basis van de specifieke behoeften van elke patiënt. Een tijdige follow-up verbetert de tevredenheid van de patiënt en zorgt voor continuïteit van de zorg na elke ontmoeting.

### Zakelijke impact

Geautomatiseerde follow-upcampagnes na het bezoek leveren doorgaans een verbetering van 40 tot 50 procent op in de responspercentages van de enquête en meetbaar hogere score voor de tevredenheid van de patiënt.

### Uitvoeren

Gebruik het [ gebeurtenis-teweeggebrachte patroon van het Overseinen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Bezoek voltooiingsevenementen van het systeem voor elektronische medische dossiers biedt een natuurlijke, tijdige trigger voor follow-upcommunicatie die is afgestemd op het type ontmoeting.

### Technische overwegingen

- Integreer met het systeem voor elektronische medische dossiers om ontslaggebeurtenissen van het bezoek te ontvangen die bezoekentype, leverancier, en relevante zorginstructies omvatten zonder volledige klinische nota&#39;s bloot te stellen.
- Pas labels voor gegevensgebruik toe op de inhoud van zorginstructies om ervoor te zorgen dat de beschermde gezondheidsinformatie alleen wordt gedeeld via beveiligde, door de patiënt geautoriseerde kanalen.
- Configureer timingsregels die rekening houden met het type bezoek — voor post-chirurgische follow-ups kan bijvoorbeeld een andere timing nodig zijn dan routinecontroles.
- Beveiligde koppelingen naar het patiëntenportaal opnemen voor voltooiing van de enquête en planning van de afspraak in plaats van gezondheidsinformatie te verzamelen via onbeveiligde kanalen.


## Programma&#39;s voor Chronic Disease Management

De communicatie over chronisch ziektebeheer, educatieve inhoud en herinneringen voor de bewaking aanpassen op basis van de specifieke toestand en het behandelingsplan van elke patiënt. Door een aanhoudende, relevante betrokkenheid kunnen patiënten een actieve rol spelen bij het beheer van hun gezondheid in de loop van de tijd.

### Zakelijke impact

In programma&#39;s voor gepersonaliseerd chronisch ziektebeheer wordt doorgaans een stijging van 30 tot 40 procent van de betrokkenheidsgraad van het programma waargenomen, wat leidt tot betere resultaten van het ziektebeheer en een lager gebruik van de noodzorg.

### Uitvoeren

Gebruik het [ multi-Step Orchestrated patroon van de Reis ](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Het beheer van chronische ziekten is inherent een langdurige multi-touchpoint ervaring die adaptieve communicatie vereist op basis van de betrokkenheid van patiënten en de mijlpalen voor de gezondheid.

### Technische overwegingen

- Ontwerpen van vertakkende logica die zich aanpast op basis van conditiespecifieke metriek (bijvoorbeeld bloedglucosetrends voor diabetesbeheer of bloeddrukwaarden voor hypertensieprogramma&#39;s).
- Implementeer strikte gegevensbeheer met gegevensgebruikslabels van [!DNL Adobe Experience Platform] om gezondheidsgegevens die specifiek zijn voor een bepaalde voorwaarde, tijdens de hele reis in te delen en te beschermen.
- Integreer met afstandsbedieningen voor patiëntbewaking en door de patiënt gerapporteerde resultaatsystemen om realtime gezondheidsgegevens in te voeren in de beslissingspunten voor reizen.
- Doorverwijspaden van zorgteams maken binnen de reis, zodat niet-betrokkenheid of zorgtendensen tot waarschuwingen voor het juiste klinische personeel leiden.


## Nieuwe patiënt op instapreis

Automatiseer een meerstapsentraject voor nieuwe patiënten, met welkomstinformatie, toegangsinstructies voor het patiëntenportaal en richtlijnen voor de planning van de afspraak. Een vlotte instapervaring zet de toon voor een betrokken, langdurige patiëntenrelatie.

### Zakelijke impact

Geautomatiseerde nieuwe patiënten die aan boord gaan rijden zorgen doorgaans voor een verbetering van 50 tot 60 procent in de activeringspercentages van de portal en een aanzienlijk hogere betrokkenheid van de vroege patiënt.

### Uitvoeren

Gebruik het [ multi-Step Orchestrated patroon van de Reis ](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Het instappen van patiënten is een natuurlijk opeenvolgend, meertrapsgewijs proces waarbij elke communicatie voortbouwt op de vorige en zich aanpast op basis van of de patiënt de belangrijkste handelingen heeft uitgevoerd.

### Technische overwegingen

- Integreer met het systeem voor patiëntenregistratie om de instapreis onmiddellijk te starten wanneer er nieuwe patiëntendossiers worden aangemaakt, zodat de eerste indruk tijdig ontstaat.
- Gebruik identiteitsresolutie om eventuele bestaande records (bijvoorbeeld van een bezoek van een website of een verzoek om benoeming) samen te voegen met het nieuwe patiëntprofiel om dubbele communicatie te voorkomen.
- Ervoor zorgen dat de koppelingen en referenties voor poortactivering via beveiligde, HIPAA-compatibele kanalen worden geleverd en na een bepaalde periode verlopen.
- Ontwerp de reis om portaalactivering en formuliervoltooiingsgebeurtenissen te detecteren zodat volgende stappen de informatie waarop de patiënt al heeft gereageerd, aanpassen in plaats van deze te herhalen.


## Speciale levering van gezondheidsinhoud

Lever persoonlijke gezondheidseducatieve inhoud, tips voor welzijn en hulpmiddelen die zijn afgestemd op de omstandigheden, belangen en gezondheidsdoelen van elke patiënt. Relevante inhoud zorgt voor vertrouwen, verbetert de kennis van de gezondheid en stelt patiënten in staat geïnformeerde beslissingen te nemen over hun zorg.

### Zakelijke impact

De levering van persoonlijke gezondheidsinhoud bereikt doorgaans een stijging van 35 tot 45 procent in de betrokkenheid bij content, wat leidt tot een meetbaar verbeterde patiënteneducatie en gezondheidsvaardigheden.

### Uitvoeren

Gebruik de [ Reis van het Kanaal met het Beslissen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon. De levering van content in de gezondheidszorg is gebaat bij beslissingen in real-time waarbij de meest relevante inhoud voor elke patiënt wordt geselecteerd op basis van zijn omstandigheden, voorkeuren en eerdere betrokkenheid, die via het voorkeurskanaal wordt geleverd.

### Technische overwegingen

- Pas inhoudclassificatie- en gegevensgebruikslabels toe op alle materialen voor gezondheidseducatie om ervoor te zorgen dat er alleen voorwaardenspecifieke inhoud wordt geleverd aan patiënten die ermee hebben ingestemd gezondheidsinformatie over dat onderwerp te ontvangen.
- Integreer de beslissingsengine met een opslagplaats voor inhoud die regelmatig wordt beoordeeld en goedgekeurd door klinische teams om medische nauwkeurigheid te garanderen.
- Implementeer regels voor inhoudvermoeidheid om overmatige levering van inhoud over één onderwerp te voorkomen en om educatief materiaal in evenwicht te brengen in de verschillende gezondheidsbehoeften van een patiënt.
- Houd de signalen van de inhoudsbetrokkenheid bij (opent, klikt, bestede tijd) om de relevantie van inhoud voortdurend te verfijnen zonder aanvullende beschermde gezondheidsinformatie te verzamelen of op te slaan.


## Melding van Lab-resultaten

Waarschuwen patiënten wanneer laboratoriumresultaten beschikbaar zijn via hun voorkeurscommunicatiekanaal met gepersonaliseerde, veilige berichten. Een snelle melding moedigt patiënten aan om de resultaten snel te beoordelen en zo nodig hun zorgteam te volgen.

### Zakelijke impact

De geautomatiseerde berichten van de laboratoriumresultaten drijven typisch een verhoging van 60 tot 70 percenten van resultaat het bekijken van tarieven, verbeterend patiëntenmededeling en toelatend snellere klinische follow-up wanneer de resultaten actie vereisen.

### Uitvoeren

Gebruik het [ gebeurtenis-teweeggebrachte patroon van het Overseinen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). De beschikbaarheid van LAB-resultaten is een aparte gebeurtenis die een directe, eenmalige melding via het voorkeurskanaal van de patiënt vereist.

### Technische overwegingen

- Neem nooit de daadwerkelijke waarden van het laboratoriumresultaat op in de berichtberichten — meld de patiënt alleen dat de resultaten beschikbaar zijn en stuur deze naar de beveiligde patiëntportal voor meer informatie.
- Integreer met het laboratoriuminformatiesysteem om resultaatklare gebeurtenissen te ontvangen en strikte labels voor gegevensgebruik toe te passen om te voorkomen dat klinische gegevens naar de marketingkanalen stromen.
- Implementeer logica voor het bewaren van providers, zodat meldingen alleen worden verzonden nadat de opdrachtgevende arts de resultaten heeft bekeken en vrijgegeven voor weergave door de patiënt.
- Zorg ervoor dat alle koppelingen naar meldingen verwijzen naar geverifieerde, gecodeerde patiëntportal-sessies die voldoen aan de HIPAA-beveiligingsvereisten.


## Verificatie van dekking verzekering

Verifieer en deel de verzekeringsdekkingsinformatie vóór hun benoeming proactief aan de patiënten door om de factureringsproblemen te verminderen en de algehele patiëntervaring te verbeteren. Duidelijke, openstaande berichtcommunicatie bouwt vertrouwen en vermindert geschillen over facturering na een bezoek.

### Zakelijke impact

Verificatie van de proactieve verzekeringsdekking resulteert doorgaans in een verbetering van de dekkingspercentages vóór het bezoek met 25 tot 35 procent en een zinvolle vermindering van factureringsgeschillen en klachten van patiënten.

### Uitvoeren

Gebruik het [ gebeurtenis-teweeggebrachte patroon van het Overseinen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gebeurtenissen voor benoemingsplanningen dienen als trigger voor het starten van een controle van de dekking en het doorgeven van resultaten aan de patiënt vóór het bezoek.

### Technische overwegingen

- Integreer met systemen voor de verificatie van de verzekeringsgeschiktheid om de status van real-time dekking op te halen zonder de volledige gegevens van de verzekeringsaanvraag op te slaan in het gegevensplatform van de klant.
- Pas labels voor gegevensgebruik toe op alle financiële en verzekeringsinformatie om het gebruik ervan te beperken tot factureringsgerelateerde communicatie.
- Configureer berichttiming om voldoende doorlooptijd voor de afspraak mogelijk te maken voor patiënten om problemen met de dekking op te lossen of contact op te nemen met hun verzekeringsprovider.
- Neem duidelijke instructies en contactgegevens op voor de factuuradatie zodat patiënten vragen kunnen stellen of bijgewerkte verzekeringsgegevens kunnen verstrekken voor hun bezoek.


## Herinneringen telehealth-benoeming

Verzend gepersonaliseerde herinneringen voor telehealth benoemingen die verbindingsinstructies, voorbereidingstips, en technische steuninformatie omvatten. Effectieve herinneringen aan de telegezondheid verminderen gemiste virtuele bezoeken en helpen patiënten vertrouwen te voelen door gebruik te maken van digitale zorginstrumenten.

### Zakelijke impact

Gepersonaliseerde herinneringen voor telehealth-afspraak zorgen meestal voor een verbetering van 40 tot 50 procent in het virtuele bezoek en tonen de snelheid en versnellen de algehele invoering van telehealth in de gehele patiëntenpopulatie.

### Uitvoeren

Gebruik het [ gebeurtenis-teweeggebrachte patroon van het Overseinen ](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Gebeurtenissen in verband met de toegezegdsplanning voor telelehealth bieden een natuurlijke trigger voor tijdige herinneringen die verbindingsdetails en voorbereidingsrichtlijnen bevatten.

### Technische overwegingen

- Neem platformspecifieke verbindingsinstructies op (desktop versus mobiel) op basis van de bekende apparaatvoorkeuren van de patiënt of gegevens van eerdere telehealth sessies.
- Verzeker alle verbindingen van de telehealth verbinding en zittingsherkenningstekens door gecodeerde, HIPAA-Volgzame kanalen worden geleverd en verlopen na het geplande benoemingsvenster.
- Integreer met het telehealth platform om te bepalen wanneer een patiënt een verbinding heeft, zodat secundaire herinneringsberichten kunnen worden onderdrukt.
- Een fallback-pad naar contactgegevens voor technische ondersteuning bieden aan patiënten die niet binnen een bepaald venster verbinding hebben gehad vóór het begin van de afspraak.


## Betrokkenheid van het Wellness-programma

Pas de communicatie, uitdagingen en beloningen van het programma van de Ziekenheid aan op basis van de gezondheidsdoelstellingen, het activiteitsniveau, en de voorkeur van elke patiënt. Het opzetten van programma&#39;s voor een goede gezondheid motiveert patiënten om gezonder te zijn en het welzijn op lange termijn te handhaven.

### Zakelijke impact

De gepersonaliseerde campagnes van het programma van de Ziekenschap bereiken typisch een 30 tot 40 percenten verhoging van de percentages van de programmaparticipatie, die tot betere gezondheidsresultaten en sterkere patiëntenloyaliteit bijdragen.

### Uitvoeren

Gebruik het [ multi-Step Orchestrated patroon van de Reis ](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Wellness-programma&#39;s zijn aanhoudende ervaringen met betrokkenheid met meerdere mijlpalen, uitdagingen en beloningsaanraakpunten die adaptieve orchestratie vereisen op basis van de deelname en voortgang van de patiënt.

### Technische overwegingen

- Integreer met de doorvoer van gegevens over het apparaat en de geschiktheidstoepassing en gebruik duidelijke labels voor gegevensgebruik om gegevens over de gezondheid te onderscheiden van klinische gezondheidsgegevens, mits aan strengere wettelijke voorschriften wordt voldaan.
- Implementeer toestemmingsbeheer waarmee patiënten toestemming kunnen verlenen en intrekken voor het verzamelen van gegevens over welheid, onafhankelijk van hun voorkeuren voor klinische communicatie.
- Ontwerp reislogica die de moeilijkheidsgraad en communicatiefrequentie van de uitdaging aanpast op basis van de betrokkenheidspatronen van elke patiënt om ontmoediging of vermoeidheid te voorkomen.
- Ervoor zorgen dat de belonings- en stimuleringstracering voldoet aan de toepasselijke gezondheidsvoorschriften inzake patiënteninducements en antikickback-vereisten.


## Coördinatie zorgteam

Gepersonaliseerde communicatie en coördinatie tussen patiënten en hun leden van het zorgteam mogelijk maken op basis van het zorgplan en individuele voorkeuren. Betere coördinatie leidt tot naadloze overgangen in de zorg en betere resultaten voor patiënten met complexe zorgbehoeften.

### Zakelijke impact

Effectieve communicatie tussen zorgteams leidt doorgaans tot een verbetering van de betrokkenheid van het zorgteam met 35 tot 45 procent en een meetbaar betere coördinatie van de zorg tussen zorgplannen met meerdere aanbieders.

### Uitvoeren

Gebruik het [ multi-Step Orchestrated patroon van de Reis ](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Bij de coördinatie van het zorgteam zijn meerdere belanghebbenden betrokken en zijn doorlopende communicatiestromen nodig die zich moeten aanpassen op basis van de mijlpalen in het zorgplan, wijzigingen in de status van de patiënt en acties van de leverancier.

### Technische overwegingen

- Implementeer op rollen gebaseerde toegangscontroles en labels voor gegevensgebruik om ervoor te zorgen dat elk lid van het zorgteam alleen patiëntinformatie ontvangt die relevant is voor zijn rol in het zorgplan.
- Integreer met zorgbeheer en elektronische gezondheidszorgregistratiesystemen om de updates van het zorgplan, de voltooiing van verwijzingen, en overgang-van-zorg gebeurtenissen te ontvangen die coördinatieberichten teweegbrengen.
- Ontwerp afzonderlijke communicatiepaden voor patiëntgerichte en providergerichte berichten, waarbij ervoor wordt gezorgd dat de klinische terminologie op de juiste wijze wordt gebruikt voor aanbieders, terwijl de patiëntenberichten duidelijk en toegankelijk blijven.
- Een volledig auditspoor bijhouden van alle communicatie over zorgcoördinatie voor naleving van de zorgcontinuïteitsvoorschriften en accreditatievereisten.
