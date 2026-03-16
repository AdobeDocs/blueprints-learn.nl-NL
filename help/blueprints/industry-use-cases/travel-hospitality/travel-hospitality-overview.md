---
title: Reis- en ziekenhuiszaken
description: Ontdek hoe reis- en gastorganisaties Adobe Experience Platform gebruiken om boekingservaringen te personaliseren, verlaten reserveringen terug te krijgen en gastloyaliteit te bouwen.
solution: Experience Platform, Real-Time Customer Data Platform, Journey Optimizer
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '2835'
ht-degree: 0%

---


# Reis- en ziekenhuiszaken

Reizen- en gastorganisaties gebruiken Adobe Experience Platform om gastgegevens van boekingsprogramma&#39;s, loyaliteitsprogramma&#39;s, vastgoedbeheersystemen en digitale aanraakpunten samen te brengen in één enkel gezichtspunt van elke reiziger. Deze verenigde stichting machtigt gepersonaliseerde ervaringen die boekingen inspireren, verlaten reserveringen terugkrijgen, en het soort gastloyaliteit bouwen die herhaalde bezoeken drijft.

## Persoonlijke homepage voor nieuwe bezoekers

Toon persoonlijke cruise, hotel, en bestemmingsaanbevelingen op de homepage die op de geografische plaats van de bezoeker en het het doorbladeren gedrag wordt gebaseerd. Eerste bezoekers die onmiddellijk relevante reisopties zien, zullen waarschijnlijk veel vaker verder verkennen en beginnen met het boekingsproces.

### Zakelijke impact

Door de homepage voor nieuwe bezoekers aan te passen, wordt de conversiesnelheid gewoonlijk met 15-20% verhoogd door reisopties weer te geven die overeenkomen met de locatie en belangen van de bezoeker in plaats van algemene inhoud.

### Uitvoeren

Gebruik het [&#128279;](/help/blueprints/use-case-patterns/personalization/anonymous-visitor-web-personalization.md) patroon van Personalization van het Web van 0&rbrace; Anonieme Bezoeker &lbrace;. Deze benadering levert inhoud op maat aan bezoekers die zich nog niet hebben geïdentificeerd, gebruikend beschikbare signalen zoals geolocatie, apparatentype, en verwijzingsbron om de ervaring van de allereerste pagina te personaliseren.

### Technische overwegingen

- Geolocatiegegevens moeten aan de rand nauwkeurig worden opgelost om regionale bestemmingen, valuta&#39;s en vertrekhavens te kunnen bedienen zonder latentie toe te voegen aan de startpagina.
- De Personalization-regels moeten rekening houden met de seizoensgebonden reistrends per regio, waarbij bijvoorbeeld tijdens wintermaanden bezoekers in koude klimaten worden geconfronteerd met warm weer.
- Strategieën voor terugvalinhoud zijn van essentieel belang voor bezoekers wier locatie niet kan worden bepaald of die via anonimiserende services aankomen.
- Integratie met de beschikbaarheidsfeed van het reserveringssysteem zorgt ervoor dat de getoonde eigenschappen en routes daadwerkelijk boekbaar zijn, waardoor frustratie de verkoopopties niet kan bevorderen.


## Reispad voor herstel van winkelwagentjes

Automatisch detecteren wanneer een klant zijn boekenkar verlaat en een meerstapse e-mailreis met persoonlijke aanbiedingen activeren om voltooiing aan te moedigen. Abandonnementen vormen een van de grootste inkomstenlekken op het gebied van reizen en gastvrijheid en een tijdige follow-up terwijl de reisintentie nog vers is, herstelt een belangrijk deel van die boekingen.

### Zakelijke impact

Effectieve herstelprogramma&#39;s voor boekingen leveren een herstelpercentage van 25-35% voor winkelwagentjes op en kunnen extra $50.000 tot $200.000 aan maandelijkse inkomsten genereren, afhankelijk van boekingsvolume en gemiddelde reiswaarde.

### Uitvoeren

Gebruik het [&#x200B; gebeurtenis-teweeggebrachte patroon van het Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Deze benadering reageert op een real-time cart-voorval waarbij een tijdige herinnering wordt verzonden terwijl de reisintentie van de klant nog steeds hoog is.

### Technische overwegingen

- De detectiedrempels voor ritten moeten rekening houden met de langere beoordelingscycli die typisch zijn voor reisaankopen; een vertraging van 2-4 uur vóór de eerste herinnering is vaak geschikter dan de 30-60 minuten die in de detailhandel worden gebruikt.
- De e-mailinhoud moet de huidige prijzen, de beschikbaarheid van ruimte of cabine en de beelden van het reserveringssysteem op het moment van verzending dynamisch ophalen, aangezien de reisinventaris en de tarieven regelmatig veranderen.
- Persoonlijke prikkels zoals gratis upgrades of redactiecredieten moeten worden beheerd via bedrijfsregels die rekening houden met marge, seizoensgebondenheid en de klantenbindingslaag.
- De logica van de onderdrukking moet klanten uitsluiten die hun reservering door een ander kanaal, zoals een callcenter of een reisagent, voltooiden om irrelevante follow-upberichten te vermijden.


## Bezoeker met hoge intentie gericht

Ontdek bezoekers met een hoge aankoopintentie met behulp van AI-propensiteitsscoring en richt ze met persoonlijke aanbiedingen en inhoud. Door te weten welke bezoekers het meest waarschijnlijk boeken, kan de organisatie haar meest dwingende aanbiedingen en verkoopbereik richten op de reizigers die het dichtst bij een beslissing staan.

### Zakelijke impact

Het richten van high-intent bezoekers met gepersonaliseerde aanbiedingen drijft een verhoging van 30 tot 40% van omzetting voor deze segmenten, die marketing investering concentreren waar het het grootste rendement levert.

### Uitvoeren

Gebruik het [&#128279;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) patroon van 0&rbrace; gekende-Bezoeker Web/App Personalization. Deze benadering gebruikt profielgegevens en gedragssignalen in real time om de webervaring voor geïdentificeerde bezoekers te personaliseren, die op maat gemaakte inhoud leveren en aanbiedingen die hun niveau van koopbereidheid aanpassen.

### Technische overwegingen

- De modellen van de volheid moeten op reis-specifieke intentsignalen zoals datumonderzoeken, het tarief paginameningen, ruimtevergelijkingsactiviteit worden getraind, en herhaal bezoeken aan de zelfde bestemming binnen een kort venster.
- Ingrijpende interventies, zoals live chatherinneringen of aanbiedingen met beperkte tijd, moeten op natuurlijke beslissingspunten in de boekingsstroom verschijnen in plaats van de browserervaring te verstoren.
- In het scoremodel moet onderscheid worden gemaakt tussen onderzoeksintensie en boekingsintentie, aangezien reizigers vaak maanden onderzoeken voordat ze klaar zijn om te kopen.
- Met [!DNL Real-Time Customer Data Platform] berekende kenmerken kunt u gedragssignalen in verschillende sessies samenvoegen om voor elke bezoeker een actuele intentscore te behouden.


## Campagnes voor uploaden na reservering

Nadat een klant een reservering heeft voltooid, activeert hij automatisch upselcampagnes voor cabineupgrades, offshore excursies, restauratiepakketten en andere bijkantoren. De periode tussen boeken en reizen is wanneer gasten het meest opgewonden zijn over hun aanstaande reis en het meest ontvankelijk om hun ervaring te verbeteren.

### Zakelijke impact

Na het boeken van upsellingscampagnes verhoogt typisch gemiddelde ordewaarde met $200-$500 en hef nevenopbrengst met 15-25% op, die één enkel boeken in een beduidend waardevollere transactie verandert.

### Uitvoeren

Gebruik het [&#x200B; multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Deze reisgidsen met meerdere stappen boekten klanten door een getimed opeenvolging van upselmogelijkheden, die de aanbiedingen aanpassen die op wat de gast reeds heeft gekocht en hun betrokkenheid met vroegere berichten worden gebaseerd.

### Technische overwegingen

- De reis moet met het reserveringssysteem integreren om precies te weten wat de gast heeft geboekt, welke upgrades beschikbaar zijn voor hun specifieke route, en de huidige prijs voor elke bijkomende optie.
- De timing van de opkoop moet strategisch worden gespreid; de cabinedespiegels kunnen kort na de boeking worden aangeboden, terwijl de excursies en restauratiepakketten beter presteren naarmate de reisdatum nadert.
- De inventarisatie en de beschikbaarheid van hulpproducten moeten worden gecontroleerd op het moment van de presentatie van de aanbieding, aangezien de excursiecapaciteit en de beschikbaarheid van upgrades voortdurend veranderen.
- [!DNL Journey Optimizer] personalisatie moet rekening houden met het aantal reizigers in de boeking, en moet familiegerichte excursies voor familieboekingen en op paren gerichte ervaringen voor reserveringen door twee personen aanbevelen.


## Win-back-campagnes voor klanten met een laptop

Identificeer klanten die niet in twaalf of meer maanden hebben geboekt en verbind hen met gepersonaliseerde win-backaanbiedingen en inhoud die op hun vroegere reisvoorkeur worden gebaseerd. Het opnieuw engageren van verouderde gasten is aanzienlijk kosteneffectiever dan het aanschaffen van volledig nieuwe klanten, en in het verleden hebben reizigers al merkbekendheid die de belemmering voor het opnieuw boeken vermindert.

### Zakelijke impact

Goed gerichte win-backcampagnes bereiken een 10-15% reactiveringspercentage onder vervalste klanten, die inkomsten terugkrijgen van gasten die anders nooit zouden terugkeren.

### Uitvoeren

Gebruik het [&#x200B; multi-Step Orchestrated patroon van de Reis &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/multi-step-orchestrated-journey.md). Deze meerfasentransparantie heeft de klanten een reeks progressieve berichten doen verdwijnen die evolueren van inspiratie naar stimulans op basis van de reactie van de klant.

### Technische overwegingen

- Gesloten klantsegmentatie moet rekening houden met de typische boekingsfrequentie in de reiscategorie; een klant die jaarlijks boeken zou niet als vervallen moeten worden gemarkeerd na slechts zes maanden inactiviteit.
- Win-back-inhoud moet verwijzen naar de eerdere reisvoorkeuren van de klant, zoals voorkeursbestemmingen, cabinetypen of reisseizoenen, om aan te tonen dat het merk zich herinnert en deze waarden waarneemt.
- Aanbiedingen moeten over de hele reis escaleren, om te beginnen met inspirerende inhoud en om verder te gaan naar monetaire prikkels alleen als eerdere berichten geen betrokkenheid genereren.
- De dossiers van de klant moeten tegen het reserveringssysteem voor om het even welke die boekingen door off-line kanalen zoals reisagenten of callcenters worden gemaakt worden gecontroleerd om het verzenden van win-backberichten naar klanten te vermijden die eigenlijk actief zijn.


## Dynamische aanbevelingen voor reistijden

Toon persoonlijke cruise reisroutes en bestemmingen die op het verleden van de klant het boeken, het doorbladeren geschiedenis, en verklaarde voorkeur worden gebaseerd. Wanneer reizigers reisschema&#39;s zien die zijn aangepast aan hun belangen en reisstijl, nemen ze een dieper contact op met de planningervaring en gaan ze sneller naar boeken.

### Zakelijke impact

De gepersonaliseerde aanbevelingen van de reisroute drijven een verhoging van 20 tot 30% van overeenkomst met reispagina&#39;s, die klanten helpen de juiste reis sneller vinden en verminderen de drop-off die voorkomt wanneer de reizigers zich door teveel opties worden overweldigd.

### Uitvoeren

Gebruik het [&#128279;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) patroon van 0&rbrace; gekende-Bezoeker Web/App Personalization. Met deze methode wordt de inhoud van websites voor bepaalde bezoekers gepersonaliseerd, waarbij hun profielgegevens en gedragsgeschiedenis worden gebruikt om de meest relevante reisroutes en bestemmingen aan te geven.

### Technische overwegingen

- In de logica van de routineaanbevelingen moeten de datum van vertrek of verblijf, de vertrekhavens en de voorkeuren voor de duur naast de bestemmingsrente worden opgenomen om opties voor te stellen die aantrekkelijk en praktisch zijn voor de klant.
- Integratie met het centrale reserveringssysteem zorgt ervoor dat de aanbevolen routes een inventarisatie bevatten en de huidige prijzen weerspiegelen, waardoor frustratie wordt voorkomen bij het promoten van afverkochte reizen of volledig geboekte eigendommen.
- Seizoensfactoren zouden de aanbevelingen sterk moeten beïnvloeden; klanten die eerder voor de zomer van de Middellandse Zee cruises hebben geboekt, zouden vergelijkbare seizoensopties moeten zien in plaats van alternatieven buiten het seizoen.
- Het beleid voor het samenvoegen van profielen in [!DNL Experience Platform] moet het browsergedrag van meerdere apparaten op de juiste wijze verenigen, zodat het onderzoek dat op mobiele apparaten wordt uitgevoerd, wordt weerspiegeld in de aanbevelingen voor desktoptoepassingen.


## Onlangs bekeken producten op startpagina

Onlangs bekeken de vertoning cruises, hotels of bestemmingen op de homepage om bezoekers te herinneren aan hun interesse en terugkeerbezoeken aan te moedigen. Reizigers onderzoeken vaak meerdere sessies voordat ze boeken, en door hun eerdere belangen te overwinnen, wordt de wrijving weggenomen dat ze telkens opnieuw moeten zoeken.

### Zakelijke impact

Door recent gebrande reisproducten op de homepage te tonen, neemt de terugkeringsservice met 15 tot 20% toe, waardoor klanten kunnen oppakken waar ze zijn opgehouden en het pad naar boeken kunnen verkorten.

### Uitvoeren

Gebruik het [&#128279;](/help/blueprints/use-case-patterns/personalization/known-visitor-web-app-personalization.md) patroon van 0&rbrace; gekende-Bezoeker Web/App Personalization. Deze benadering gebruikt de opgeslagen profielgegevens van de bezoeker om eerder bekeken punten op de homepage terug te geven, die tot continuïteit over het doorbladeren zittingen leiden.

### Technische overwegingen

- Onlangs bekeken gegevens moeten op apparaten en sessies blijven bestaan met behulp van identiteitsresolutie, zodat een klant die op zijn telefoon bladert dezelfde items ziet wanneer hij of zij op een desktopcomputer terugkeert.
- Weergegeven items moeten de huidige prijs- en beschikbaarheidsstatus aangeven, met duidelijke indicatoren als een eerder bekeken optie niet meer beschikbaar is of als de prijs sinds het laatste bezoek is gewijzigd.
- Het recentievenster voor weergegeven items moet worden afgestemd op de boekingscycli voor reizen; het tonen van een cruise die drie maanden geleden is bekeken, kan nog steeds relevant zijn, in tegenstelling tot een handelsproduct dat zo lang geleden werd bekeken.
- De overwegingen van de privacy vereisen dat onlangs bekeken inhoud aan de toestemmingsstatus van de klant wordt gebonden, en een optie om het doorbladeren geschiedenis te ontruimen zou gemakkelijk toegankelijk moeten zijn.


## Model met intentie afsluiten met gerichte aanbiedingen

Wanneer een bezoeker de exitintentie weergeeft, geeft u een gepersonaliseerd modaal model weer met relevante aanbiedingen op basis van hun browsergedrag tijdens de sessie. Het vangen van een vertrekkende bezoeker met een dwingende, contextueel relevante aanbieding biedt een laatste kans om rente om te zetten in een boeking voordat ze vertrekken.

### Zakelijke impact

De intent-modaliteiten van de uitgang met gepersonaliseerde reisaanbiedingen herstellen een 5-10% omrekeningskoers onder bezoekers die anders zonder reservering zouden vertrekken, die opbrengst vangen die volledig zou worden verloren.

### Uitvoeren

Gebruik het [&#x200B; patroon van Offer Decisioning &#x200B;](/help/blueprints/use-case-patterns/personalization/offer-decisioning.md). Deze benadering gebruikt gecentraliseerde besluitvormingslogica om alle beschikbare aanbiedingen te evalueren en meest relevante voor de vertrekkende bezoeker te selecteren die op hun zittingsgedrag en profielgegevens wordt gebaseerd.

### Technische overwegingen

- Bij detectie van uitgangen op plaatsen voor reisboekingen moet rekening worden gehouden met browsergedrag met meerdere tabbladen, aangezien reizigers vaak meerdere reisschema&#39;s of eigenschappen openen op aparte tabbladen zonder dat zij echt van plan zijn te vertrekken.
- De selectie van de aanbieding zou moeten wijzen op wat de bezoeker tijdens hun zitting doorbladerde, die een korting op de specifieke bestemming of het bezit presenteerde zij eerder dan een generische bevordering verkondigden.
- De modulaire frequentie moet strikt worden beperkt om te voorkomen dat bezoekers bij elk bezoek hetzelfde aanbod zien, wat de urgentie en de waargenomen exclusiviteit van de promotie verhult.
- In de toelatingsregels van [!DNL Journey Optimizer] moet rekening worden gehouden met de loyaliteitslaag en de boekingsgeschiedenis van de bezoeker om naar behoren gewaardeerde prikkels te bieden, zodat gasten belangrijke risico&#39;s kunnen bieden in plaats van kleine kortingen.


## Loyalty Program Personalization

Pas de ervaring, aanbiedingen en communicatie van de website aan op basis van de loyaliteitslaag, puntbalans en betrokkenheidsgeschiedenis van de klant. Loyalty&#39;s die hun status in alle aanraakpunten zien, voelen zich erkend en gewaardeerd, wat hun betrokkenheid bij het merk versterkt en bevorderlijk is voor verdere ontwikkeling.

### Zakelijke impact

Op Tier-gebaseerde personalisatie zorgt voor een toename van de betrokkenheid van loyaliteitsleden met 25-35%, waardoor de relatie wordt verdiept en het loon- en terugbetalingsgedrag wordt versneld dat de inkomsten op lange termijn ondersteunt.

### Uitvoeren

Gebruik de [&#x200B; Reis van het Kanaal met het Beslissen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/cross-channel-journey-with-decisioning.md) patroon. Deze benadering combineert reisorchestratie met besluitvorming in real time om het juiste aanbod door het juiste kanaal voor elk loyaliteitslid te leveren, zich aan hun rij, voorkeur, en recente activiteit aan te passen.

### Technische overwegingen

- Gegevens over het kwaliteitsprogramma, zoals status op de laag, puntsaldi en de geschiedenis van het verdienen, moeten worden opgenomen en actueel worden gehouden om ervoor te zorgen dat de personalisatie van de website en de aanbiedingen de werkelijke status van de klant weerspiegelen.
- Ratiespecifieke voordelen zoals vroege toegang tot boekingen, gratis upgrades en exclusieve prijsstelling moeten worden afgedwongen op het moment van aflossing, wat een nauwe integratie met de boekings- en prijssystemen vereist.
- De veranderingen van het puntsaldo van boekingen, verblijven, en partnertransacties zouden herberekening van verpersoonlijkingsregels in dichtbij real time moeten teweegbrengen, zodat een klant die net genoeg punten voor een beloning verdiende die optie onmiddellijk ziet.
- Het publiek van [!DNL Real-Time Customer Data Platform] moet worden gestructureerd rond loyaliteitsniveaus en belangrijke betrokkenheidsmijlpalen, zoals het naderen van de volgende laag of het risico van laagdemotie.


## Herinneringen voor meerkanaals boeken

Stuur gepersonaliseerde herinneringen voor reserveringen via e-mail, tekstbericht en pushberichten naar klanten die hun reserveringen zijn begonnen maar niet zijn voltooid. Reizigers beginnen vaak met het reserveringsproces en worden onderbroken. Als ze op hun voorkeurskanalen bereiken, wordt er een herinnering weergegeven en met hun opgeslagen reisgegevens worden ze weer opgehaald om de reservering te voltooien.

### Zakelijke impact

Herinneringen voor meerkanaalse boekingen verbeteren de afsluitingspercentages met 20-30%, waardoor aanzienlijke inkomsten worden teruggevorderd van klanten die van plan waren te boeken, maar vóór de afwerking werden afgeschaft.

### Uitvoeren

Gebruik het [&#x200B; gebeurtenis-teweeggebrachte patroon van het Overseinen &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/event-triggered-messaging.md). Deze benadering brengt herinneringen automatisch teweeg wanneer een onvolledige boekingsgebeurtenis wordt ontdekt, leverend geschikte berichten over de aangewezen kanalen van de klant.

### Technische overwegingen

- Kanaalselectielogica moet de communicatievoorkeuren van de klant respecteren en de levering optimaliseren op basis van eerdere betrokkenheidspatronen, waarbij pushberichten worden verzonden naar klanten die goed reageren op mobiele apparaten en e-mailberichten worden gestuurd naar gebruikers die dat wensen.
- De inhoud van de herinnering moet een diepe verbinding omvatten die de klant aan hun bewaarde reservering met alle selecties intact terugkeert, eliminerend de wrijving van het opnieuw ingaan van reisdata, ruimtevoorkeur, en gastdetails elimineert.
- De regels voor timing en frequentie moeten op de verschillende kanalen worden gecoördineerd om overweldigende gevolgen voor de klant te voorkomen. Een e-mail en een pushmelding over dezelfde boeking moeten op de juiste wijze worden gespatieerd in plaats van tegelijkertijd te worden verzonden.
- Integratie met het eigenschapsbeheer of het centrale reserveringssysteem moet verifiëren of het oorspronkelijk geselecteerde kamertype, de snelheid en de datums nog beschikbaar zijn voordat de herinnering wordt verzonden. Het bericht wordt dan bijgewerkt als de beschikbaarheid is gewijzigd.


## Seizoenscampagne Personalization

Prijsgerichte campagnes en aanbiedingen op basis van seizoensvoorkeuren, boekingen uit het verleden en huidige seizoensgebonden trends. Reizigers worden sterk beïnvloed door seizoenen, en campagnes die aansluiten bij hun gedemonstreerde seizoensbelangen en de huidige reistrends zijn veel dwingender dan generieke promoties.

### Zakelijke impact

Seizoensgebonden gepersonaliseerde campagnes verhogen de seizoensgebonden boekingsconversie met 15-25%, waarbij ervoor wordt gezorgd dat de marketinginvesteringen zich concentreren op de bestemmingen en reisproducten die het meest geschikt zijn voor de klant.

### Uitvoeren

Gebruik het [&#x200B; Uitgaande patroon van de Activering van het Bericht van de Partij &#x200B;](/help/blueprints/use-case-patterns/campaign-management-orchestration/batch-outbound-message-activation.md). Deze benadering levert gepersonaliseerde seizoensgebonden campagneberichten aan grote doelgroepen op een geplande basis, die klanten door hun seizoensgebonden reispatronen en voorkeur segmenteren.

### Technische overwegingen

- De seizoensgebonden voorkeursprofielen van de klant moeten worden opgebouwd op basis van historische boekingsgegevens, waarbij patronen worden vastgesteld zoals consistente vakanties op het zomerstrand of winterskiltrips om campagnedoelen te informeren.
- De planning van de campagne moet rekening houden met de doorlooptijden in de reisindustrie; de vakantiecampagnes in de zomer moeten begin voorjaar van start gaan wanneer gezinnen plannen maken, en niet in juni wanneer de meeste boekingen al worden gedaan.
- De prijzen en de beschikbaarheid voor seizoensgebonden inventarisatie moeten zodanig worden geïntegreerd dat bevorderde aanbiedingen de real-time tarieven en de werkelijke beschikbaarheid van ruimte of cabine tijdens de aanbevolen reisperioden weerspiegelen.
- Het publiek van [!DNL Experience Platform] moet seizoensgebonden voorkeursgegevens combineren met recenindicatoren om prioriteit te geven aan klanten die zich in hun typische planningsvenster voor het komende seizoen bevinden.


## Aanbevelingen voor groepsregistratie

Identificeer klanten die regelmatig groepsreizen boeken en proactief groepspakketten, familievriendelijke opties, of multi-room het boeken aanbevelen. De boekingen van de groep vertegenwoordigen beduidend hogere opbrengst per transactie, en de klanten met een aangetoond patroon van groepsreis antwoorden goed aan gebogen opties die het planningsproces vereenvoudigen.

### Zakelijke impact

De pro-actieve groep die aanbevelingen opneemt verhoogt gemiddelde ordewaarde met $1.000 -$3.000 per boek, die de volledige waarde van de transacties van de groepsreis vangen die anders over veelvoudige individuele voorbehouden zouden kunnen worden verdeeld.

### Uitvoeren

Gebruik het [&#x200B; patroon van de Aanbeveling van het Gedrag &#x200B;](/help/blueprints/use-case-patterns/personalization/behavioral-recommendation.md). Deze benadering gebruikt AI-gedreven modellen die van klant het boeken patronen en gedrag leren om de meest relevante opties van de groepsreis voor elke klant aan te bevelen.

### Technische overwegingen

- Voor de identificatie van groepsreizen moet de boekingsgeschiedenis worden geanalyseerd op patronen zoals meerkamerreserveringen, boekingen met meerdere passagiers en gecoördineerde boekingen die dicht bij elkaar worden gehouden voor dezelfde data en bestemming.
- Prijsbepaling voor groepspakketten moet dynamisch uit het reserveringssysteem worden gehaald, aangezien de groepstarieven vaak verschillen van individuele tarieven en minimale partijformaten of vervroegde boekingstijden vereisen.
- De inhoud van de aanbeveling zou de unieke behoeften van groepsorganisatoren, met inbegrip van informatie over groep het dineren opties, vergaderingsruimten, blokboekingskortingen, en de beschikbaarheid van de groepsexcursie moeten richten.
- [!DNL Real-Time Customer Data Platform] -profielverrijking moet klanten markeren als groepsreisorganisatoren op basis van hun boekingspatronen, zodat doelgerichte campagnes mogelijk zijn tijdens piekplanningsperioden, zoals het seizoen van de gezinshereniging of bedrijfsaftremise.
