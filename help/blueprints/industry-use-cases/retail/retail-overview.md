---
title: Kwesties voor winkelgebruik
description: Ontdek hoe de detailhandelsorganisaties Adobe Experience Platform gebruiken om winkelervaringen te personaliseren, verlaten winkelwagentjes terug te krijgen, en klantenloyaliteit te drijven.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2590'
ht-degree: 0%

---


# Kwesties voor winkelgebruik

De detailhandelorganisaties gebruiken Adobe Experience Platform om klantengegevens van online winkels, fysieke plaatsen, en loyaliteitsprogramma&#39;s in één enkele mening van elke verkoopster te verenigen. Deze stichting laat gepersonaliseerde het winkelen ervaringen, geschikte outreach toe die verloren opbrengst terugwint, en loyaliteitsstrategieën die klanten houden terugkomend.

## Aanbevelingen voor gepersonaliseerde producten

Persoonlijke productaanbevelingen weergeven op homepage-, categoriepagina&#39;s en pagina&#39;s met productdetails op basis van de browsergeschiedenis, de aankoopgeschiedenis en vergelijkbaar gedrag van de klant. Wanneer kopers producten zien die op hun belangen zijn afgestemd, besteden ze meer tijd aan het verkennen en hebben ze veel meer kans om producten te kopen.

### Zakelijke impact

Detailhandelaars zien meestal een stijging van 20-30% in doorkliksnelheden en een verbetering van 15-25% in omrekeningskoersen wanneer ze gepersonaliseerde aanbevelingen doen in plaats van lijsten met statische producten.

### Uitvoeren

Gebruik het [&#x200B; patroon van de Aanbeveling van het Gedrag &#x200B;](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Deze benadering gebruikt op AI-Gebaseerde adviseringsmodellen die voortdurend van klanteninteractie leren om de meest relevante producten voor elk individu te oppervlakten.

### Technische overwegingen

- De catalogusgegevens van het product moeten worden opgenomen en bijgewerkt, met inbegrip van productkenmerken, beelden, tarifering, en beschikbaarheid, om te verzekeren de aanbevelingen weerspiegelen wat klanten werkelijk kunnen kopen.
- Gedragssignalen zoals productweergaven, add-to-cart gebeurtenissen en aankopen moeten in real-time stromen om aanbevelingen vers te houden binnen één enkele het doorbladeren zitting.
- Voor modellen met aanbevelingen is een strategie nodig voor nieuwe bezoekers die geen browsergeschiedenis hebben, die doorgaans terugvallen op trending- of best-verkopende producten.
- De prestaties van het laden van de pagina moeten zorgvuldig worden gecontroleerd, aangezien de verpersoonlijkingsvraag geen merkbare latentie aan het winkelen zou moeten toevoegen.


## Verlaten e-mailherstel voor winkelwagentjes

Verzend automatisch persoonlijke e-mailherinneringen naar klanten die hun winkelwagentje hebben verlaten, inclusief de exacte achtergebleven objecten en relevante aanbiedingen om voltooiing aan te moedigen. De stopzetting van winkelwagentjes is een van de grootste bronnen van inkomstenderving in de detailhandel, en de tijdige follow-up kan een aanzienlijk deel van die verkopen herstellen.

### Zakelijke impact

Effectieve programma&#39;s voor het herstellen van winkelwagentjes leveren een herstelpercentage van 25-35% voor winkelwagentjes en kunnen een extra omzet van 100.000 tot 500.000 dollar per maand genereren, afhankelijk van het opslagvolume.

### Uitvoeren

Gebruik het [&#x200B; gebeurtenis-teweeggebrachte patroon van het Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Deze benadering reageert op een real-time gebeurtenis voor het verlaten van het winkelwagentje, waarbij een tijdige herinnering wordt verzonden terwijl de aankoopintentie nog steeds hoog is.

### Technische overwegingen

- Voor het detecteren van winkelwagentjes moet een drempel voor inactiviteit (meestal 30 tot 60 minuten) worden gedefinieerd voordat de eerste herinnering wordt geactiveerd, zodat berichten voor klanten die nog actief winkelen, worden vermeden.
- E-mailinhoud moet de huidige productafbeeldingen, prijzen en beschikbaarheid dynamisch tijdens het verzenden uit de catalogus halen, aangezien de items kunnen worden verkocht of de prijs tussen het verlaten en het leveren kan veranderen.
- Regels voor frequentiecontrole moeten voorkomen dat klanten in een korte periode meerdere e-mails met achterstallige winkelwagentjes ontvangen, met name als ze de winkelwagentjes vaak verlaten.
- De lijsten van de toestemming en van de onderdrukking moeten worden gecontroleerd alvorens te verzenden, en de klanten die hun aankoop door een ander kanaal voltooiden zouden in real time moeten worden uitgesloten.


## Op inventarisatie gebaseerde urgentiecampagnes

U kunt waarschuwingen en campagnes in real-time activeren wanneer de productvoorraad laag is, zodat u snel kunt kopen. Winkelaars die zien dat er slechts een paar objecten overblijven, zijn gemotiveerd om snel te handelen in plaats van hun beslissing uit te stellen.

### Zakelijke impact

Trage-voorraad urgentiecampagnes leiden doorgaans tot een stijging van 30-40% in de conversie van aanbevolen producten en helpen de overvoorraad te verminderen door de doorverkoop van langzaam bewegende producten te versnellen.

### Uitvoeren

Gebruik het [&#x200B; gebeurtenis-teweeggebrachte patroon van het Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Deze benadering reageert op gebeurtenissen met betrekking tot inventarisdrempels, waarbij automatisch het dringende bericht wordt geactiveerd wanneer de voorraadniveaus onder gedefinieerde limieten dalen.

### Technische overwegingen

- Het voer van de inventaris moet met het platform van klantengegevens in bijna echt - tijd integreren zodat het urgentieoverseinen daadwerkelijke voorraadniveaus eerder dan stapelgegevens weerspiegelt.
- Drempelwaarden moeten per productcategorie worden geconfigureerd, aangezien een &quot;lage voorraaddrempel&quot; voor een product met een hoog volume aanzienlijk verschilt van een drempel voor een luxegoed.
- Berichten moeten waarheidsgetrouw zijn en moeten in overeenstemming zijn met de voorschriften inzake consumentenbescherming. Onjuiste schaarste kan het vertrouwen van de merken schaden en op bepaalde markten de reclamenormen overtreden.
- Onsite berichten en e-mailkanalen moeten worden gecoördineerd, zodat een klant die al heeft aangeschaft geen urgente meldingen voor hetzelfde product blijft ontvangen.


## Aanbevelingen voor crossverkopen en uploaden

Toon relevante cross-sell en upsell producten bij kassa, in e-mail, en op productpagina&#39;s die op aankooppatronen en productverhoudingen worden gebaseerd. Door op het juiste moment aanvullende of premiumalternatieven voor te stellen wordt de mand groter zonder dat klanten zelf naar verwante items moeten zoeken.

### Zakelijke impact

Goed uitgevoerde cross-sell en upsell strategieën verhogen gemiddelde orderwaarde met $25-$75 en heffen opbrengst per transactie met 10-15%.

### Uitvoeren

Gebruik het [&#x200B; patroon van Offer Decisioning &#x200B;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Deze benadering gebruikt gecentraliseerde beslissingslogica om alle beschikbare aanbiedingen te evalueren en de beste optie voor cross-sell of upsell te selecteren voor elke klant en context.

### Technische overwegingen

- Productrelatiegegevens, waaronder vaak aangekochte koppelingen en upgradepaden, moeten worden bijgehouden en regelmatig worden vernieuwd om de huidige aankooppatronen te weerspiegelen.
- De rangschikkingslogica van de aanbieding zou voor marge, relevantie, en inventarisniveaus moeten rekenschap geven zodat de meest rendabele en beschikbare opties eerst opstijgen.
- Aanbevelingen voor cross-sell tijdens het afrekenen moeten snel worden geladen en mogen de aankoopstroom niet verstoren. Trage of indringende suggesties kunnen de conversie daadwerkelijk verminderen.
- De [!DNL Journey Optimizer] besluitvormingsregels zouden reserveaanbiedingen moeten omvatten zodat elke in aanmerking komende klant een aanbeveling ontvangt, zelfs wanneer de top-ranked optie niet beschikbaar is.


## Nieuwe welkomstreeks voor klanten

Automatiseer een welkomstserie voor meerdere e-mails voor nieuwe klanten met gepersonaliseerde productaanbevelingen, merkartikelen en speciale aanbiedingen. De eerste paar interacties nadat een klant zich aansluit vormen hun langetermijnrelatie met het merk, waardoor deze reeks een van de programma&#39;s met de hoogste impact is die een retailer kan uitvoeren.

### Zakelijke impact

Een goed ontworpen welkomstserie zorgt voor een betrokkenheid van 40 tot 50% bij nieuwe klanten en verbetert de levenslange waarde aanzienlijk door de brandaffiniteit vroegtijdig op te bouwen.

### Uitvoeren

Gebruik het [&#x200B; multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Deze multitouch-trainingstraject begeleidt nieuwe klanten door een reeks merkintroductie, productdetectie en stimulerende berichten, die worden aangepast op basis van hun betrokkenheid.

### Technische overwegingen

- De trigger voor het betreden van een reis moet op betrouwbare wijze nieuwe gebeurtenissen voor het maken van klanten vastleggen uit alle registratiebronnen, waaronder web, mobiele app, verkooppunten in de winkel en markten van derden.
- Wacht stappen tussen e-mails op basis van betrokkenheidsgegevens. Klanten die openen en klikken, ontvangen het volgende bericht mogelijk eerder, terwijl minder betrokken klanten profiteren van meer ruimte.
- De aanbevelingen van het product binnen welkome e-mails zouden moeten weerspiegelen wat de klant tijdens hun eerste bezoek doorzocht of kocht, niet generische beste verkopers.
- Klanten die een aankoop maken tijdens de welkomstreeks moeten zich vertakken in een postaankoopstroom in plaats van overnameberichten te blijven ontvangen.


## Waarschuwing: prijzen verlagen

Klanten via e-mail of push-berichten op de hoogte stellen wanneer producten in hun verlanglijst of eerder bekeken objecten de prijs verlagen. Winkelaars die wel belangstelling hebben getoond maar niet hebben gekocht, reageren sterk op prijsverlagingen, waardoor dit een van de meest efficiënte manieren is om de vergoeding in de verkoop om te zetten.

### Zakelijke impact

Prijsdalingswaarschuwingen genereren een conversiesnelheid van 20-30% bij ontvangers en verhogen de klanttevredenheid aanzienlijk door klanten te laten voelen dat ze de beste prijs-kwaliteitverhouding krijgen.

### Uitvoeren

Gebruik het [&#x200B; gebeurtenis-teweeggebrachte patroon van het Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Deze aanpak reageert op gebeurtenissen die zich hebben voorgedaan in verband met de verandering van de productprijs en stemt deze af tegen de signalen van de klant om tijdig meldingen te verzenden.

### Technische overwegingen

- Bij de detectie van prijswijzigingen moeten de huidige prijzen worden vergeleken met eerdere waarden in de productcatalogusfeed en moeten alleen waarschuwingen worden gegeven voor zinvolle reducties in plaats van kleine fluctuaties.
- Belangensignalen van klanten (wenslijsttoevoegingen, producteprofilering, tijd die op productpagina&#39;s wordt doorgebracht) moeten worden opgeslagen en efficiënt worden vergeleken met potentieel duizenden dagelijkse prijswijzigingen.
- In de meldingen moeten de oorspronkelijke prijs, de nieuwe prijs en het spaarbedrag worden vermeld om de waarde duidelijk aan te geven; vage berichten met &quot;prijsverlaging&quot; onderdrukken specifieke spaarrekeningen.
- [!DNL Real-Time Customer Data Platform] de segmenten voor prijsgevoelige kopers kunnen worden gebruikt om waakzame levering voorrang te geven en het overseinentoon aan te passen.


## Herinneringen voor vervanging

Verzend geautomatiseerde herinneringen aan klanten voor producten die zij regelmatig kopen, zoals abonnementsvoorwerpen en verbruiksartikelen, om herhaalde aankopen aan te moedigen alvorens zij opraken. Proactieve herinneringen verminderen de kans dat klanten op een concurrent overschakelen eenvoudig omdat zij vergaten om te herschikken.

### Zakelijke impact

Herstelprogramma&#39;s bieden een herhalingsfrequentie van 30-40% en verbeteren het vasthouden van de klant aanzienlijk door het voor kopers gemakkelijker te maken om de producten waarop ze vertrouwen, in voorraad te nemen.

### Uitvoeren

Gebruik het [&#x200B; multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Deze terugkerende geplande reis gebruikt de voorspellingen van de koopfrequentie om herinneringen op het optimale tijdstip te verzenden alvorens een klant waarschijnlijk een hervulling nodig heeft.

### Technische overwegingen

- Bij de berekening van de aankoopfrequentie moet rekening worden gehouden met de verschillende verbruikscategorieën; een herinnering voor koffie moet op een andere plaats komen dan voor schoonmaakbenodigdheden.
- De reis zou zijn timing dynamisch moeten aanpassen wanneer een klant vroeger of later dan voorspeld opnieuw bestelt, die de volgende herinnering op bijgewerkte aankoopgegevens herijkt.
- Herinneringen moeten een koppeling voor het direct opnieuw ordenen of een terugkoopoptie met één klik bevatten om wrijving te minimaliseren en de conversie vanuit de melding te maximaliseren.
- Klanten die al via een ander kanaal (in-store, abonnementsservice) opnieuw hebben geordend, moeten worden onderdrukt om het verzenden van irrelevante herinneringen te voorkomen.


## Speciale rubriekpagina&#39;s

Pas de categoriepagina&#39;s dynamisch aan, zodat de meest relevante producten eerst worden weergegeven op basis van de voorkeuren, eerdere aankopen en het bladergedrag van elke klant. Wanneer kopers producten zien die zijn afgestemd op hun smaak boven aan de pagina, ontdekken ze wat ze sneller willen en zetten ze ze om met hogere snelheden.

### Zakelijke impact

Gepersonaliseerde categoriepagina&#39;s zorgen voor een toename van de categoriepagina&#39;s met 25-35% en verbeteren de productdetectie aanzienlijk, met name voor detailhandelaren met grote catalogi.

### Uitvoeren

Gebruik het [&#x200B; patroon van de Aanbeveling van het Gedrag &#x200B;](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Deze benadering gebruikt selectiestrategieën en rangschikkingsmodellen om producten op categoriepagina&#39;s opnieuw te ordenen die op het profiel van elke bezoeker en gedrag in real time worden gebaseerd.

### Technische overwegingen

- De rangschikking van producten moet snel genoeg worden uitgevoerd om waargenomen vertragingen bij het laden van pagina&#39;s te voorkomen; personalisatie aan serverzijde of op rand-gebaseerde besluitvorming is vaak vereist voor categoriepagina&#39;s met honderden producten.
- De logica van de verpersoonlijking zou individuele voorkeur met handelsregels moeten mengen, die ervoor zorgen dat de bevorderde producten, de nieuwe aankomsten, en de seizoensgebonden voorwerpen nog behoorlijk zichtbaar worden.
- Er moet een A/B-testinfrastructuur zijn om het inkomsteneffect van gepersonaliseerde sortering versus standaard handelsregels doorlopend te meten.
- [!DNL Experience Platform] Web SDK-implementatie moet interactie tussen categoriepagina&#39;s vastleggen (schuifdiepte, productklikken, filtergebruik) om de rangordemodellen voortdurend te verfijnen.


## Follow-upcampagnes na aankoop

Verzend e-mails na aankoop met tips voor de productzorg, verwante productsuggesties, revisieverzoeken en informatie over het loyaliteitsprogramma. De periode onmiddellijk na een aankoop is dat klanten het meest betrokken zijn bij het merk, waardoor het een ideaal venster is om de relatie te verdiepen en toekomstige activiteiten aan te moedigen.

### Zakelijke impact

Effectieve campagnes na de aankoop verhogen de verzendingspercentages van de revisie met 15-20% en zorgen voor een herhalingsaankoopsnelheid van 10-15%, waardoor eenmalige kopers loyale klanten worden.

### Uitvoeren

Gebruik het [&#x200B; multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Deze multi-step post-purchase flow gebruikt vertakkende logica om follow-upberichten op te stellen op basis van producttype, klantensegment en betrokkenheid bij eerdere e-mails in de reeks.

### Technische overwegingen

- De reis moet rekening houden met de status van bestelling; zorgtips en verzoeken om herziening mogen alleen worden verzonden nadat het product is afgeleverd, niet onmiddellijk na de aankoop.
- Voor productspecifieke inhoud (zorginstructies, gebruikshandleidingen, aanvullende suggesties) is een systeem voor het toewijzen van inhoud vereist dat elke productcategorie koppelt aan relevante follow-upmaterialen.
- Het tijdstip van de aanvraag voor een nieuw onderzoek moet worden geoptimaliseerd op basis van de productcategorie; elektronica heeft mogelijk een langere gebruiksperiode nodig voordat een zinvolle revisie plaatsvindt, terwijl kleding kort na de levering kan worden herzien.
- Klanten die een terugkeer of ruil in werking stellen zouden automatisch uit de standaard post-aankoop stroom moeten worden verwijderd en aan een weg van de de dienstterugwinning opnieuw gericht.


## Exclusieve VIP-aanbiedingen voor klanten

Identificeer klanten van hoge waarde en verstrek exclusieve aanbiedingen, vroege toegang tot verkoop, en gepersonaliseerde het winkelen ervaringen die hun loyaliteit belonen. Het behouden van klanten van het hoogste niveau is veel rendabeler dan het verwerven van nieuwe, en de exclusieve behandeling versterkt de emotionele verbinding die hen houdt te besteden.

### Zakelijke impact

VIP-programma&#39;s genereren doorgaans een servicepercentage van 50-70% van klanten op het hoogste niveau en verbeteren de levenswaarde van klanten meetbaar door de kosten te reduceren tot het meest winstgevende segment.

### Uitvoeren

Gebruik de [&#x200B; Reis van het Kanaal met het Beslissen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon. Deze benadering combineert reisorchestratie met real-time besluitvorming voor aanbiedingsselectie, die ervoor zorgt dat elke VIP-klant het meest relevante exclusieve aanbod over elk kanaal ontvangt.

### Technische overwegingen

- De segmenteringscriteria van VIP moeten duidelijk worden bepaald gebruikend recentie, frequentie, en monetaire waardecijfers, en de segmenten zouden vaak genoeg moeten verfrissen om klanten te vangen die onlangs gekwalificeerd of gediskwalificeerd waren.
- Exclusieve aanbiedingen moeten worden afgedwongen op het moment van aflossing (web, app, store) om te voorkomen dat niet-VIP-klanten toegang krijgen tot deze aanbiedingen, wat integratie met promotie- en prijssystemen vereist.
- Kanaalvoorkeuren verschillen aanzienlijk tussen klanten met een hoge waarde. Sommige klanten geven de voorkeur aan e-mail, andere reageren op app-berichten of direct mail. Daarom moet de reis de leveringskanalen aanpassen op basis van eerdere betrokkenheid.
- [!DNL Journey Optimizer] De beslissingen moeten via verschillende kanalen worden gecoördineerd om te voorkomen dat een VIP-klant hetzelfde aanbod tegelijkertijd via e-mail, push en SMS ontvangt.


## Meldingen van buitenaf

Klanten toestaan zich aan te melden voor meldingen wanneer producten uit de voorraad beschikbaar komen en ze vervolgens automatisch via e-mail of tekst op de hoogte stellen. Door de vraag naar niet-beschikbare producten vast te leggen, voorkomt u dat er verkopen verloren gaan en krijgen klanten een reden om terug te keren naar de winkel in plaats van bij een concurrent te kopen.

### Zakelijke impact

Met meldingen van &quot;back-in-stock&quot; wordt een conversietarief van 40 tot 50% bereikt voor abonnees en wordt de verloren omzet voor producten met een hoge vraag die tijdelijk in voorraad zijn, aanzienlijk verminderd.

### Uitvoeren

Gebruik het [&#x200B; gebeurtenis-teweeggebrachte patroon van het Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Deze benadering leidt tot berichten op reserve-in-voorraad gebeurtenissen, die inventarisupdates met klanten bericht ondertekenen-ups aanpassen om tijdige alarm te leveren.

### Technische overwegingen

- Het controleren van de inventaris moet snel gebeurtenissen van het herbevolken ontdekken; vertragingen zelfs een paar uren kunnen tot het product leiden dat opnieuw uitverkoopt alvorens de aangemelde klanten een kans hebben om te kopen.
- Wanneer een populair product in beperkte hoeveelheden wordt hervoorraad, moeten meldingen worden gespreid of geprioriteerd op de inschrijvingsdatum om te voorkomen dat waarschuwingen naar meer klanten worden gestuurd dan de beschikbare voorraad kan dienen.
- In het aanmeldingsmechanisme moet de voorkeur voor het kanaal (e-mail of tekstbericht) worden vastgelegd en moet worden voldaan aan de vereisten voor aanmelding voor elk kanaal, met name voor SMS.
- [!DNL Real-Time Customer Data Platform] -profielkenmerken moeten bijhouden welke producten elke klant volgt, zodat dubbele meldingen worden voorkomen als hetzelfde product meerdere keren opnieuw wordt aangeboden.


## Sociale proef Personalization

Geef persoonlijke sociale proefdrukken weer, inclusief beoordelingen, beoordelingen en suggesties voor &#39;klanten die dit hebben gekocht&#39;, op basis van het profiel en de voorkeuren van elke klant. Het aanpassen van de sociale zekerheid om de ervaringen van vergelijkbare klanten weer te geven, leidt tot meer vertrouwen dan alleen algemene ratings.

### Zakelijke impact

Het persoonlijke sociale bewijs verhoogt de omrekeningskoersen met 10-15% en verbetert het vertrouwen van de consument, met name voor de eerste kopers en de duurdere producten waar de koopaarsaardigheid het grootst is.

### Uitvoeren

Gebruik het [&#128279;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) patroon van 0&rbrace; gekende-Bezoeker Web/App Personalization. Deze benadering past de webinhoud aan voor bepaalde bezoekers, waarbij de meest relevante revisies en elementen voor sociale profielen worden geselecteerd op basis van het profiel, de voorkeuren en de browsercontext van de klant.

### Technische overwegingen

- Het overzicht en de classificatiegegevens moeten door klantenattributen (zoals aankoopcontext, klantensegment, en het geval van het productgebruik) worden gestructureerd en worden geëtiketteerd om zinvolle filtratie en verpersoonlijking toe te laten.
- Elementen met sociale profielen moeten asynchroon worden geladen om te voorkomen dat de hoofdpagina-weergave wordt geblokkeerd, aangezien revisiegegevens afkomstig kunnen zijn van een revisieplatform van een derde met variabele responstijden.
- De privacyverordeningen vereisen dat om het even welke klantengegevens die worden gebruikt om overzichten aan bezoekers aan te passen volgens toestemmingsvoorkeur worden behandeld; het tonen van &quot;klanten als u&quot;inhoud impliceert het profileren die openbaarmaking kan vereisen.
- Met het lidmaatschap van een publiek van [!DNL Experience Platform] kunt u selecteren welke revisies u wilt markeren. Zo ziet u in plaats van algemene topbeoordelingen de revisies van buitenshuis door enthousiaste collega&#39;s.
