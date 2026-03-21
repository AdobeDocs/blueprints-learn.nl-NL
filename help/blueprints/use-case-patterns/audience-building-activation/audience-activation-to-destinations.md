---
title: Activering van het publiek naar bestemmingen
description: Leer hoe te om publiekssegmenten aan externe bestemmingen voor het richten of onderdrukking te evalueren en te publiceren het gebruiken van Adobe Real-Time CDP.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: b2e496eb521fc3dd3290fccdd9a8203384934b88
workflow-type: tm+mt
source-wordcount: '7005'
ht-degree: 0%

---


# Activering van het publiek naar bestemmingen

Deze handleiding bevat een volledige implementatiereferentie voor het activeren van het publiek van Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP) naar externe doelen. Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die publiekssegmenten moeten evalueren en deze moeten publiceren naar platformen, cloudopslag, CRM-systemen of gegevenspartners voor het instellen van doelen, onderdrukking, lookalike-modellering of analytische verrijking.

Het presenteert alle levensvatbare implementatieopties met afwegingsanalyse, beslissingsbegeleiding, UI navigatiepaden, en de documentatieverwijzingen van Experience League.

De gids behandelt de volledige levenscyclus van publieksactivering — van het bepalen van en het evalueren van publiekssegmenten door bestemmingsverbindingen te vormen en publiek te publiceren, aan het controleren van activeringsgezondheid en het handhaven van governance naleving.

## Hoofdlettergebruik

Organisaties moeten publieksgegevens aan externe systemen leveren om betaalde mediacampagnes aan te zwengelen, CRM-records verrijken, gegevens delen met partners of downstreamanalyses voeden. Audience Activation naar bestemmingen is het basisactiveringspatroon in RT-CDP: het evalueert welke profielen voor een doelpubliek in aanmerking komen, verbindt met één of meerdere externe bestemmingen, kaarten profielattributen aan bestemmings-specifieke gebieden, en publiceert het publiek voor stroomafwaartse consumptie.

Dit patroon is van toepassing wanneer het doel is om publieksgegevens naar een extern systeem in het juiste formaat op het juiste ogenblik te krijgen. Het omvat geen berichtlevering, onsite verpersoonlijking, of analyse. Het is het gemeenschappelijkste uitgangspunt voor RT-CDP implementaties en dient als bouwsteen dat andere patronen bovenop van maken.

Tot de meest gangbare belanghebbenden behoren onder meer digitale marketingteams die betaalde media beheren, gegevensteams die opslagplaatsen verrijken, CRM-teams die contactlijsten opstellen voor campagnes, en privacyteams die de naleving van het bestuur bij uitgaande gegevensstromen garanderen.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gericht door dit gebruikspatroon.

### Nieuwe klanten aanschaffen

Breid de klantenbasis door gerichte aanschafcampagnes, lookend publiek, en betaalde media optimalisering uit.

**KPIs:** Nieuwe Klanten, de Kosten van de Aankoop van de Klant, Vooruitziendheid/Loodomzetting

[Meer informatie over het aanschaffen van nieuwe klanten](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Verlaag de aanschafkosten van de klant

Verbeter gerichte efficiency, onderdruk bestaande klanten van aanschafcampagnes, en optimaliseer media uitgaven.

**KPIs:** Kosten van de Aankoop van de Klant, Kosten per Lood, Efficiëntie

[Meer informatie over het verlagen van de aanschafkosten voor klanten](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### marketinguitgaven en investeringsrendement optimaliseren

Verbeter het rendement van marketing investering door betere richten, attributie, publieksonderdrukking, en begrotingstoewijzing.

**KPIs:** Kostenbesparingen, de Kosten van de Aankoop van de Klant, Incrementele Inkomsten

[Meer informatie over het optimaliseren van marketinguitgaven en investeringsrendement](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Voorbeelden van tactische gebruiksgevallen

- **het platformpubliek van de Advertentie richtend** - duw gekwalificeerde segmenten aan betaalde media platforms voor campagne gericht
- **Betaalde media onderdrukking van bestaande klanten** - sluit bekende klanten van aanschafcampagnes op advertentieplatforms uit om verspilde uitgaven te elimineren
- **Lookalike zaadpublieksgroepen** - duw high-value klantensegmenten aan Facebook, de Advertentie van Google, of de Desk van de Handel als zaadpubliek voor lookalike uitbreiding
- **synchronisatie van CRM voor verkoopenablement** - activeer high-intent of high-value publiek zodat kunnen de verkoopteams voorrang geven aan outreach
- **het publiek dat van de partner van Gegevens** deelt - Deel gekwalificeerde publiekssegmenten met gegevenspartners voor co-op het richten of meting
- **de opslaguitvoer van de Wolk voor de verrijking van het gegevenspakhuis** — het lidmaatschap van het publiek van de uitvoer en profielattributen aan Amazon S3, Azure Blob, de Opslag van de Wolk van Google, of SFTP voor stroomafwaartse analyse
- **opnieuw richtend publieksactivering** - activeer plaatsbezoekers die niet in het opnieuw richten van platforms omzetten
- **de lijstsynchronisatie van het Contact aan e-maildienstverleners** - duw publiekslidmaatschap aan derde e-mailplatforms voor gecoördineerde outreach

## Kernprestatie-indicatoren

| KPI | Beschrijving | Meetleidraad |
| --- | --- | --- |
| Kosten voor overname door klanten (CAC) | Kosten om een nieuwe klant via een actief publiek aan te schaffen | Totale media-uitgaven / nieuwe klanten toegeschreven aan actief publiek |
| Identieke doelfrequentie | Percentage geactiveerde profielen dat op het doel is afgestemd | Profielen komen overeen met doel/profielen geëxporteerd uit RT-CDP |
| Besparingen onderdrukken | Media-uitgaven vermeden door bestaande klanten te onderdrukken van aanschafcampagnes | Geschatte CPM x onderdrukte publieksgrootte |
| Leveringssnelheid activering | Percentage van profielen dat succesvol aan de bestemming is geleverd | Opgeleverde profielen/profielen in het bronpubliek |
| Tijd tot activering | Verstreken tijd van publieksdefinitie aan eerste levering bij de bestemming | Maatregel van segmentcreatie tot eerste bevestigde dataflow run |
| Toegankelijkheid doelgroep | Uitlijning tussen de verwachte en de werkelijke doelgrootte | Aantal doelgroepen / aantal RT-CDP-doelgroepen |

## Hoofdletterpatroon gebruiken

**Audience Activation aan Doelen** — Evalueer en publiceer een publiekssegment aan externe bestemmingen voor het richten of onderdrukking.

**Keten van de Functie:** de Evaluatie van het publiek > de Configuratie van de Bestemming > Audience Activation > Controle

## Applicaties

- **Adobe [!DNL Real-Time Customer Data Platform] (RT-CDP)** — de evaluatie van het publiek, bestemmingsbeheer, publieksactivering, toestemming en governance handhaving
- **Adobe [!DNL Experience Platform] (AEP)** — de opslag van het Profiel, de identiteitsdienst, segmenteringsmotor, gegevensbeheer

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | RT-CDP-sandbox ingericht en actief. Machtigingen voor doelbeheer en activering die zijn toegewezen aan implementatierollen. Referenties van bestemmingsaccount beschikbaar voor de doelplatforms. | [&#x200B; het overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sandbox/home), [&#x200B; overzicht van de Toegangscontrole &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | Profielschema moet kenmerken bevatten die worden toegewezen aan doelvelden (bijvoorbeeld e-mail, telefoon, hashed-id&#39;s, demografische kenmerken). Het schema moet profiel-toegelaten met datasets zijn die actief gegevens ontvangen. | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/home), [&#x200B; de samenstellingsgrondbeginselen van het Schema &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/schema/composition) |
| Gegevensbronnen en -verzameling | Verondersteld op plaats | De gegevens van het profiel die publieksevaluatie macht moeten worden ingebed en huidig. Batch- en/of streamingpijpleidingen werken. Web SDK, bronschakelaars, of batch ingestion die gegevens in profiel-toegelaten datasets leveren. | [&#x200B; Bronoverzicht &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/home), [&#x200B; het overzicht van SDK van het Web &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/web-sdk/home) |
| Identiteit en profielconfiguratie | Vereist | Identiteitsnaamruimten voor bestemmingsovereenkomst moeten worden gevormd (bv. gehakt e-mail voor de Aangepaste Soorten van Facebook, de Gelijke van de Klant van Google Ads). Bij samenvoegingsbeleid moeten uniforme profielen worden gemaakt met alle vereiste kenmerken voor activering. | [&#x200B; overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/home), [&#x200B; overzicht van het beleid van de Fusie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/merge-policies/overview) |
| Auditiedefinitie en segmentatie | Vereist | Doelpubliek gedefinieerd met gebruik van Segment Builder, Audience Composition of Federated Audience Composition. Evaluatiemethode (batch, streaming of edge) geselecteerd op basis van de vereiste activeringswachttijd. Deze functie wordt uitgeoefend in Fase 1 van dit plan. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home), [&#x200B; de gids UI van de Bouwer van het Segment &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/segment-builder) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | De gegevens verwerkte attributen zoals levenwaarde, betrokkenheidsscore, of volheidsscore verbeteren publieksprecisie en verstrekken verrijkingsattributen aan kaart aan bestemmingen. Bijzonder waardevol wanneer de bestemmingen van op waarde-gebaseerde of op score-gebaseerde publiekssegmentatie profiteren. | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Beleid voor gegevenssets en het verlopen van profielen zorgt voor gegevensversheid en compatibiliteit. Met de configuratie van het schema voor instemming worden alleen goedgekeurde profielen geactiveerd. Kritiek op naleving van regelgeving bij het exporteren van gegevens naar externe systemen. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | De etiketten en het beleid van de governance verhinderen activering van beperkte gegevens aan onbevoegde bestemmingen (b.v., PII aan en platforms, gevoelige segmenten aan gegevenspartners). Vooral belangrijk voor activering van het publiek naar externe systemen van derden. | [&#x200B; het beheer van Gegevens overzicht &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home), [&#x200B; overzicht van de gebruiksetiketten van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/labels/overview) |
| Bewaking en waarneming | Opgenomen | Activeringsbewaking maakt deel uit van de functieketen (fase 5). Omvat dataflow run monitoring, leveringsstatusalarm, publiekspopulatie het volgen, en de zichtbaarheid van het vergunningsgebruik. | [&#x200B; de bestemmingsdataflows van de Monitor &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/dataflows/ui/monitor-destinations), [&#x200B; Overzicht van het Alarm &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/alerts/overview) |
| Rapportage en analyse | Aanbevolen | De CJA-analyse van de doeltreffendheid van de activering van het publiek maakt het mogelijk de prestaties voor actief publiek te meten (bv. conversielift van onderdrukking, ROAS van lookalike-publiek). | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Real-Time CDP] (RT-CDP)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Fase 1: Evaluatie van het publiek | Bepaal publieksregels en evalueer segmentlidmaatschap gebruikend partij, het stromen, of de methodes van de randevaluatie |
| Samenstelling publiek | Fase 1: Evaluatie van het publiek | Eventueel samenstellen afgeleid publiek via verrijken, rangschikken, splitsen, uitsluiten en zich bij verrichtingen voor complexe publiekslogica aansluiten |
| Doelconfiguratie | Fase 2: Doelconfiguratie | Vorm voor authentiek verklaarde verbindingen aan externe bestemmingen met gebiedstoewijzing en het plannen parameters |
| Doelgroepactivering | Fase 3: Audience Activation | Publiceer beoordeelde publiek aan gevormde bestemmingen met attributenafbeelding en de uitvoer het plannen |
| Goedkeuring en handhaving van bestuur | Fase 4: Validatie van de governance | De toestemmingsvoorkeur en het beleid van het gegevensgebruik vóór en tijdens publieksactivering aan externe systemen afdwingen |

## Vereisten

- [ ] RT-CDP-licentie is actief met activeringsrechten voor het publiek
- [ ] De doelsandbox is ingericht en toegankelijk voor het implementatieteam
- [ ] Gebruikersrollen omvatten machtigingen voor bestemmingsbeheer en publieksactivering
- [ ] Verificatiereferenties voor elk doeldoel zijn beschikbaar (OAuth-tokens, API-sleutels, S3-toegangstoetsen of gebruikersgegevens van serviceaccounts)
- [ ] Profielschema bevat alle kenmerken die aan doelvelden moeten worden toegewezen
- [ ] Identiteitsnaamruimten die vereist zijn voor afstemming van bestemming zijn geconfigureerd (bijvoorbeeld gehashte e-mail, telefoon, apparaat-id&#39;s)
- [ ] Pipetten voor gegevensinvoer zijn operationeel en profielen vullen het profielarchief met gegevens aan
- [ ] Labels en beleidsregels voor gegevensbeheer worden gecontroleerd op de kenmerken die worden geactiveerd (met name voor externe doelen)
- [ ] Ingestane velden worden ingevuld in profielen als filteren op basis van toestemming is vereist

## Implementatieopties

De volgende implementatieopties zijn beschikbaar voor dit gebruikspatroon. Bekijk elke optie en de vergelijkingstabel om de beste benadering voor uw vereisten te bepalen.

### Optie A: activeren van stroombestemming

**Best voor:** de updates van het het publiekslidmaatschap in real time aan advertentieplatforms of partnersystemen — de Aangepaste Publiek van Facebook, de Gelijke Gelijke Gelijke Gelijke Gelijke Gelijke Publiek van Google Ads, LinkedIn, de Handelsbureau, en gelijkaardige het stromen op API-Gebaseerde bestemmingen.

**hoe het werkt:**

Streaming doelactivering zorgt ervoor dat het doellidmaatschap van de doelgroep in vrijwel realtime wordt gewijzigd, aangezien profielen in aanmerking komen voor of niet in aanmerking komen voor het segment. Wanneer een profielkenmerk verandert of een gedragsgebeurtenis plaatsvindt die ertoe leidt dat een profiel een publiek binnengaat of weggaat, wordt de lidmaatschapsupdate gestreamd aan de bestemming binnen notulen.

Deze benadering vereist een het stromen bestemmingsschakelaar (de meeste belangrijkste advertentieplatforms steunen dit) en een het stromen of de methode van de randpublieksevaluatie. De publieksevaluatie volgt voortdurend op wijzigingen in het kwalificatieprofiel en de activeringsgegevens duwt updates tijdens het uitvoeren. De bestemming ontvangt stijgende lidmaatschapsveranderingen eerder dan volledige publieksmomentopnamen.

De activering van het stromen is het gebrek voor de meeste ad platformbestemmingen in de RT-CDP catalogus. De bestemmingsschakelaar behandelt automatisch de authentificatie van de API, tarief het beperken, en logica opnieuw proberen.

**Zeer belangrijke overwegingen:**

- De evaluatie van het publiek moet het stromen of randevaluatie gebruiken (het partij-slechts publiek kan geen het stromen bestemmingen in real time voeren)
- Niet alle segmentexpressies komen in aanmerking voor streamingevaluatie — complexe aggregaties, query&#39;s voor meerdere entiteiten en bepaalde op tijd gebaseerde functies vereisen batch
- De het tarief van de partnerAPI van de bestemming grenzen kunnen productie tijdens grote publiekskwalificatiegebeurtenissen beïnvloeden
- De kenmerkupdates van het profiel worden samen met lidmaatschapsveranderingen verzonden, houdend de bestemmingsgegevens huidig

**Voordelen:**

- Bijna de versheid van het publiek in real time bij de bestemming (notulen, niet uren)
- De stijgende updates verminderen het volume van de gegevensoverdracht in vergelijking met volledige uitvoer
- Automatische afhandeling van zowel kwalificatiegebeurtenissen als ontkwalificatiegebeurtenissen
- De meeste en platformbestemmingen zelf ondersteunen streaming

**Beperkingen:**

- Vereist streaming-in aanmerking komende segmentdefinities (beperkte segmentfunctieset)
- Geen controle over bestandsindeling of exportstructuur — gegevensindeling bepaald door doelconnector
- Kan niet exporteren naar opslagdoelen op basis van bestanden (S3, Azure Blob, SFTP)
- De doel-API-snelheidslimieten kunnen wijzigingen op grote volumes vertragen

**Experience League:**

- [Stimulansen voor het publiek naar streamingdoelen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Streaming doelen in catalogus](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/overview)

### Optie B: Batchbestemming activeren (bestand exporteren)

**Best voor:** Gepland publiek voert naar wolkenopslag, gegevenspakhuizen, of systemen uit die op dossier-gebaseerde invoer — Amazon S3, de Opslag van Azure Blob, de Opslag van de Wolk van Google, SFTP, de Gebied van Gegevens gebruiken.

**hoe het werkt:**

De doelactivering van de partij evalueert publiek op een geplande ingang en voert de resultaten als dossiers (CSV, JSON, of Parquet) aan de gevormde opslagbestemming uit. Het exporteren kan volledige momentopnamen voor het publiek of incrementele wijzigingen (nieuwe kwalificaties en ontzettingen sinds de laatste export) bevatten.

De implementatie omvat het configureren van een op een bestand gebaseerde doelverbinding met opslagreferenties, voorkeuren voor bestandsindelingen (scheidingsteken, compressie, naamgevingsconventie) en een exportschema (dagelijks, elke 3 uur, elke 6 uur, enz.). Bij elke exportbewerking worden bestanden gegenereerd die het lidmaatschap van het publiek en eventuele toegewezen profielkenmerken bevatten.

Deze aanpak ondersteunt een zo groot mogelijk aantal downstreamconsumenten, omdat de uitwisseling van op bestanden gebaseerde gegevens door iedereen wordt ondersteund. Het is ook de enige optie voor het gebruik van cloudopslag en gegevensopslagruimte.

**Zeer belangrijke overwegingen:**

- De evaluatie van het publiek kan om het even welke methode (partij, het stromen, of rand) gebruiken — de uitvoer zelf loopt op een programma ongeacht
- Bestandsindeling, compressie en naamgevingsconventies kunnen per doel worden geconfigureerd
- Ondersteunt zowel incrementele exportbewerkingen (alleen wijzigingen) als volledige exportbewerkingen (volledige opname van het publiek)
- De planningsgranulariteit van de uitvoer varieert van om de 3 uur tot dagelijks

**Voordelen:**

- Volledige controle over de bestandsindeling voor export (CSV, JSON, Parquet), compressie en naamgeving
- Compatibel met elk downstreamsysteem dat bestanden kan gebruiken
- Ondersteunt zowel incrementele als volledige exportmodi
- Kan publiek met om het even welke evaluatiemethode (met inbegrip van partij-slechts segmenten met complexe segmentatielogica) uitvoeren
- Ondersteunt ad-hocexportbewerkingen (op aanvraag) die buiten het normale schema vallen

**Beperkingen:**

- Latentie is inherent hoger — de publieksgegevens komen bij de bestemming op een programma, niet in real time aan
- Voor op bestanden gebaseerde exportbewerkingen moet het doelsysteem de bestanden verwerken en invullen
- Opslagkosten op de bestemming voor geëxporteerde bestanden
- Grotere gegevensvolumes per export vergeleken met incrementele streaming updates

**Experience League:**

- [Soorten publiek activeren om exportdoelen voor batchprofielen te gebruiken](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Catalogus van op bestanden gebaseerde doelen](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/cloud-storage)

### Optie C: Activering van meerdere doelen

**Best voor:** het activeren van het zelfde publiek aan veelvoudige bestemmingen gelijktijdig — bijvoorbeeld, duwend een suppressielijst aan alle advertentieplatforms, die een hoogwaardig segment aan zowel CRM als advertentieplatorplatforms synchroniseren, of het coördineren van publieksbereik over veelvoudige media partners.

**hoe het werkt:**

De activering van de multi-bestemming is geen afzonderlijk technisch mechanisme maar een samenstelling van Opties A en B die op het zelfde publiek over veelvoudige bestemmingsverbindingen wordt toegepast. Het zelfde publiek wordt geactiveerd aan twee of meer bestemmingen, elk met zijn eigen verbindingsconfiguratie, gebiedstoewijzing, en het plannen.

Elke doelverbinding functioneert onafhankelijk — een streamingactivering op Facebook en een batchexport naar S3 kunnen gelijktijdig vanuit hetzelfde bronpubliek worden uitgevoerd. Veldtoewijzingen worden geconfigureerd per bestemming, zodat verschillende kenmerken naar verschillende systemen kunnen worden verzonden op basis van wat elke bestemming vereist en welk governancebeleid toestaat.

Dit is een gemeenschappelijk productiepatroon voor organisaties die op meerdere advertentieplatforms werken, CRM-synchronisatie naast mediaconactivering onderhouden, of die publieksgegevens moeten verspreiden naar zowel operationele als analytische systemen.

**Zeer belangrijke overwegingen:**

- Elke bestemming heeft onafhankelijke gebiedskaarten, planning, en governance evaluatie
- Het beleid van bestuur wordt afgedwongen per bestemming — verschillende attributen kunnen voor verschillende bestemmingstypes worden toegelaten
- Één enkel publiek kan aan een mengeling stromen en partijbestemmingen gelijktijdig worden geactiveerd
- Voor het toevoegen van een nieuw doel zijn geen wijzigingen in bestaande activeringen vereist

**Voordelen:**

- Gecoördineerde publieksdistributie over alle externe systemen van één enkele publieksdefinitie
- De onafhankelijke configuratie per bestemming staat geoptimaliseerde afbeeldingen en lijsten toe
- De handhaving van het bestuur per bestemming verzekert naleving over verschillende bestemmingstypes
- Centraliseert publieksbeheer terwijl het steunen van verdeelde activering

**Beperkingen:**

- Meer bestemmingsverbindingen om te vormen, voor authentiek te verklaren en te handhaven
- De complexere verhogingen van de controle met elke bestemming — de activeringsmislukkingen moeten per bestemming worden gevolgd
- Het gebruik van de vergunning (geactiveerde profielen) kan per bestemming afhankelijk van aanspraken tellen
- Het onderhoud van veldmapping tussen meerdere bestemmingen vereist coördinatie

**Experience League:**

- [Overzicht van doelen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/home)
- [Doelcatalogus](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/overview)

### Optievergelijking

| Criteria | Optie A: Streaming | Optie B: Batch (Bestand exporteren) | Optie C: Meerdere bestemmingen |
| --- | --- | --- | --- |
| Best voor | Doelstellingen en onderdrukking in realtime en op platformen | Verrijking van gegevenspakhuis, op dossier-gebaseerde systeemintegratie | Gecoördineerde distributie van publiek over verschillende platforms |
| Complexiteit | Laag | Gemiddeld | Hoog |
| Latentie | Minuten (bijna real-time) | Uren (gepland) | Mengsel van minuten en uren per bestemming |
| Bestandsindelingcontrole | Geen (doel bepaalt indeling) | Volledig (CSV, JSON, Parquet, compressie, naamgeving) | Per bestemming |
| Poortevaluatie | Streaming of rand vereist | Elke methode (batch, streaming, edge) | Vereisten per bestemming |
| Vereisten | Streaming doelconnector, voor streaming in aanmerking komend segment | Bestandsgebaseerde doelconnector, opslagreferenties | Meerdere doelconnectors en referenties |
| Beheer | Evaluatie van één bestemming | Evaluatie van één bestemming | Evaluatie per bestemming |

### Kies de juiste optie

Gebruik de volgende besluitvormingslogica om de juiste implementatiebenadering te selecteren:

1. **hoeveel bestemmingen hebt u nodig?** Als u het zelfde publiek aan twee of meer bestemmingen moet activeren, voert u Optie C uit (die Opties A en B per bestemming) samenstelt. Ga aan vraag 2 en 3 voor elke bestemming te werk.

2. **steunt de bestemming het stromen?** Als de bestemming een advertentieplatform (Facebook, Google Ads, LinkedIn, The Trade Desk) of partnerintegratie met een het stromen API is, gebruik Optie A voor die bestemming. Als de bestemming cloudopslag (S3, Azure Blob, GCS, SFTP) of een systeem is dat dossiers verbruikt, gebruik Optie B.

3. **hoe snel moet het publiek bij de bestemming aankomen?** Als het publiekslidmaatschap op de bestemming binnen notulen (b.v., onderdrukking in real time tijdens actieve campagnes) moet nadenken, gebruik Optie A. Als de dagelijkse of meeruurs levering voldoende is (bijv. wekelijkse data-entrepot vernieuwen, CRM batch sync), gebruik Optie B.

4. **gebruikt uw publiek complexe segmentatielogica?** Als de publieksdefinitie multi-gebeurtenissamenvoegingen, grote tijdvensters, of functies omvat die niet voor het stromen evaluatie kwalificeren, gebruik Optie B (partijbestemmingen) of verzeker optie A bestemmingen ook partij-geëvalueerd publiek op een programma ontvangen.

## Uitvoeringsfasen

De tenuitvoerlegging volgt deze fasen. Elke fase bevat configuratiegegevens, beslissingspunten en koppelingen naar Experience League-documentatie.

### Fase 1: Evaluatie door het publiek

**functie van de Toepassing:** rt-CDP: De Evaluatie van het publiek, rt-CDP: De Samenstelling van het publiek

**wat u zult vormen:** bepaal het doelpubliek dat aan bestemmingen zal worden geactiveerd. Dit omvat het specificeren van de publiekscriteria (welke profielen kwalificeren), het selecteren van de evaluatiemethode (hoe snel lidmaatschap bijwerkt), en het bevestigen van de publiekspopulatie. Dit is het uitgangspunt voor alle activering — zonder een bepaald en geëvalueerd publiek, is er niets te activeren.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: De aanmaakmethode van het publiek**
>
>Hoe moet het doelpubliek worden gedefinieerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Segmentbouwer (op regel gebaseerd) | Standaardpublieksdefinitie met profielkenmerken, gedraggebeurtenissen en voorwaarden voor segmentlidmaatschap | De meest flexibele regeldefinitie; steunt het stromen en randevaluatie voor in aanmerking komende uitdrukkingen; ideaal voor enig-voorwaarde of gematigd complex publiek |
>| Samenstelling publiek | Het publiek vereist combinatie, rangschikking, splitsing of uitsluiting van bestaand publiek | Visueel canvas voor opeenvolgende bewerkingen; de resultaten worden alleen in batch geëvalueerd; maximaal 10 compositieblokken per canvas |
>| Federale compositie publiek | De criteria van het publiek moeten worden beoordeeld aan de hand van gegevens in externe gegevensopslagplaatsen zonder deze in AEP op te nemen | Hiermee worden rechtstreeks externe databases opgevraagd; gegevensduplicatie wordt vermeden; Federated Audience Composition-licentie is vereist |

>[!NOTE]
>
>**Besluit: De methode van de Evaluatie**
>
>Hoe snel moeten de profielen ingaan en het publiek weggaan?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Batch | Geplande campagnes, dagelijkse publieksverfrissingen, of complexe segmentatielogica die niet voor het stromen kwalificeren | Verwerkt tot 24 miljoen profielen per baan; alle segmentatiefuncties die worden gesteund; looppas op een programma (dagelijks gebrek of douane bouwplan) |
>| Streaming | Wijzigingen in het realtime-publiekslidmaatschap vereist voor activering van bestemming of gebruiksgevallen die door een gebeurtenis worden geactiveerd | Bijna real-time (seconden aan notulen); beperkte geplaatste segmentatiefunctie — eenvoudige gebeurtenissen, attribuutvergelijkingen, en beperkte tijdvensters slechts; geen multi-entiteitvragen |
>| Edge | Gelijke paginagrootte of onmiddellijke publiekskwalificatie nodig aan de rand | Milliseconde latentie; meest beperkende regelreeks — profielattributen en eenvoudige controles van het segmentlidmaatschap slechts; hoofdzakelijk gebruikt voor onsite personalisatie (minder gemeenschappelijk voor bestemmingsactivering) |

>[!NOTE]
>
>**Besluit: Het beleid van de Fusie**
>
>Welk samenvoegingsbeleid zou de publieksevaluatie moeten gebruiken?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Tijdstempel geordend (standaard) | Meest gebruikte gevallen — recente gegevens moeten prioriteit krijgen bij conflict met profielfragmenten | Meest voorkomende; gebruikt de laatst bijgewerkte kenmerkwaarde |
>| Dataset-prioriteit | Specifieke gegevensbronnen moeten andere overschrijven, ongeacht het tijdstempel | Vereist het definiëren van een prioriteitsvolgorde voor een gegevensset; nuttig wanneer een CRM-systeem met record altijd de via het web verzamelde gegevens moet overschrijven |

**navigatie UI:** Klant > Soorten publiek > leidt tot publiek > bouwt regel (voor de Bouwer van het Segment) of stelt publiek samen (voor de Samenstelling van het Publiek)

**Zeer belangrijke configuratiedetails:**

- Bepaal publiekscriteria die op het gebruiksgeval worden gebaseerd — profielattributen, gedragsgebeurtenissen, segmentlidmaatschap, of op tijd-gebaseerde voorwaarden
- Onderdrukkingsregels toepassen om profielen uit te sluiten die niet moeten worden geactiveerd (bijv. onlangs geconverteerd, globaal afgemeld)
- De populatiegrootte van het publiek valideren voordat u verdergaat met activering
- Bevestig de evaluatiemethode richt zich op het bestemmingstype dat in Fase 2 wordt geselecteerd

**waar de opties uiteenlopen:**

**voor Optie A (het stromen de Activering van de Bestemming):**
Het publiek moet streaming of edge evaluation gebruiken om real-time lidmaatschapsupdates te leveren. Verifieer de uitdrukking van de segmentregel voor het stromen evaluatie kwalificeert — vermijd op tijd-gebaseerde samenvoegingsfuncties, multi-entiteitvragen, en `inSegment()` verwijzingen naar partij-slechts segmenten.

**voor Optie B (de Activering van de Bestemming van de Partij):**
Elke evaluatiemethode werkt. Batchevaluatie is de meest gebruikelijke keuze, aangezien de export zelf volgens een schema wordt uitgevoerd. Bevestig dat er een batchevaluatieschema bestaat in de sandbox of maak er een.

**voor Optie C (multi-Doelactivering):**
De evaluatiemethode zou de meest veeleisende bestemming moeten aanpassen. Als om het even welke bestemming het stromen vereist, zou het publiek het stromen evaluatie moeten gebruiken. Als alle bestemmingen partij zijn, is de partijevaluatie voldoende.

**documentatie van Experience League:**

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentering](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Overzicht van Audience Composition](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/audience-composition)
- [Evaluatiemethoden](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home#evaluation-methods)


### Fase 2: Doelconfiguratie

**functie van de Toepassing:** rt-CDP: De Configuratie van de Bestemming

**wat u zult vormen:** Vestig voor authentiek verklaarde verbindingen aan de externe bestemmingen waar het publiek zal worden gepubliceerd. Dit omvat het selecteren van de bestemming uit de catalogus, het verstrekken van authentificatiegeloofsbrieven, en het vormen bestemmings-specifieke parameters zoals dossierformaat, opslagplaats, en de uitvoer planning. Elke bestemming vereist zijn eigen verbindingsconfiguratie.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Het type van Bestemming**
>
>Waar moet het publiek worden gebracht?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Advertising-doel (streaming) | Doelstellingen of onderdrukking op advertentieplatforms (Facebook, Google Ads, LinkedIn, The Trade Desk, enz.) | Streaming connectors; lidmaatschapsupdates in bijna real-time; identiteitsvergelijking via gehashte e-mail, telefoon, of apparaat-id&#39;s |
>| Opslagbestemming voor cloud (batch) | Exporteren naar S3, Azure Blob, GCS, SFTP of Data Landing Zone voor verrijking van gegevensopslagplaatsen | Op bestand gebaseerde export; configureerbare indeling (CSV, JSON, Parquet); geplande corps |
>| CRM-bestemming | Synchroniseer publiek aan Salesforce, Microsoft Dynamics, of HubSpot voor verkoopenablement | Typisch stromen; vereist CRM-specifieke gebiedstoewijzing; kan de toestemmingen van CRM nodig hebben admin |
>| Doel gegevenspartner | Deel publieksgegevens met meetpartners of doelpartners | Varieert per partner; herzie governance implicaties van het delen van gegevens extern |
>| Aangepast doel (Destination SDK) | Doelsysteem niet beschikbaar in de catalogus | Vereist het bouwen van een douanebestemming gebruikend Destination SDK; hogere implementatieinspanning |

>[!NOTE]
>
>**Besluit: De methode van de Authentificatie**
>
>Welke geloofsbrieven vereist de bestemming?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| OAuth 2.0 | Advertentieplatforms en SaaS-bestemmingen (Facebook, Google, Salesforce) | Vereist initiële machtigingsstroom; tokens worden automatisch vernieuwd; meest gangbaar voor streamingdoelen |
>| Toegangstoets / Geheim sleutel | Cloudopslag (S3, Azure Blob) | Statische referenties; rotatie moet worden gepland; geschikt voor bestandsgebaseerde doelen |
>| Servicerekening/API-sleutel | Partner-API&#39;s en aangepaste integratie | Vereist credentielevering van de bestemmingspartner |
>| Verbindingstekenreeks | Op Azure gebaseerde bestemmingen | Eén tekenreeks met alle verbindingsparameters |

>[!NOTE]
>
>**Besluit: Het type van de uitvoer (partijbestemmingen slechts)**
>
>Hoe moeten publieksgegevens worden verpakt voor export?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Incrementeel exporteren | Alleen nieuwe kwalificaties en ontzettingen sinds laatste export | Kleinere bestandsgrootte; snellere verwerking bij bestemming; vereist doelsysteem om status te behouden |
>| Volledig exporteren | Volledige publieksopname bij elke uitvoering | Grotere bestanden; het doel krijgt elke keer een volledig beeld; eenvoudiger voor systemen die een volledige vervanging uitvoeren |

**navigatie UI:** Verbindingen > Doelen > Catalogus > [ Uitgezochte bestemming ] > vormt

**Zeer belangrijke configuratiedetails:**

- Blader door de doelcatalogus en selecteer het doeldoel
- Geef verificatiegegevens op en test de verbinding
- Voor batchbestemmingen: bestandsindeling (CSV, JSON, Parquet), compressie, naamgevingssjabloon voor bestanden en exportschema configureren
- Voor streamingdoelen: de verbinding wordt doorgaans tot stand gebracht via OAuth-autorisatiestroom
- Controleer of de status van de doelverbinding actief is voordat u verdergaat met activeren

**waar de opties uiteenlopen:**

**voor Optie A (het stromen de Activering van de Bestemming):**
Selecteer een streamingdoel in de catalogus (categorieën Advertising of Sociaal). Voltooi de OAuth autorisatiestroom. De verbinding is klaar voor activering zodra de vergunning wordt bevestigd.

**voor Optie B (de Activering van de Bestemming van de Partij):**
Selecteer een bestemming op basis van een bestand in de catalogus (categorie Cloud Storage). Configureer het opslagpad, de bestandsindeling, de compressie, de naamgevingsconventie en het exportschema. Test de verbinding door schrijftoegang tot de opslaglocatie te controleren.

**voor Optie C (multi-Doelactivering):**
Herhaal deze fase voor elke bestemming. Elke verbinding is onafhankelijk — u kunt een mengeling van het stromen en partijbestemmingen hebben. Documenteer de authentificatie en de configuratie van elke verbinding voor operationele verwijzing.

**documentatie van Experience League:**

- [Doelcatalogus](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/overview)
- [Overzicht van doelen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/home)
- [Soorten publiek activeren om exportdoelen voor batchprofielen te gebruiken](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Stimulansen voor het publiek naar streamingdoelen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Destination SDK-overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/destination-sdk/overview)
- [Destination SDK-configuratieopties](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/destination-sdk/functionality/configuration-options)


### Fase 3: Activering van het publiek

**functie van de Toepassing:** rt-CDP: Audience Activation

**wat u zult vormen:** publiceer het geëvalueerde publiek aan de gevormde bestemming door de activeringsdataflow te creëren. Dit betekent dat u moet selecteren welk publiek moet activeren, profielkenmerken moet toewijzen aan doelvelden en het exportschema moet configureren. De activeringsgegevensstroom verbindt het bronpubliek met de doelbestemming en beheert aan de gang zijnde gegevenslevering.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Toewijzing van Attributen**
>
>Welke profielkenmerken moeten worden opgenomen in de activering?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alleen identiteitsvelden | Doel hoeft alleen overeen te stemmen met profielen (bijvoorbeeld lidmaatschap voor doelgroepen op advertentieplatoren) | Minimale gegevensoverdracht; de meeste privacy-veiligheid; typisch voor het richten en onderdrukken van ad-platform |
>| Identiteit + profielkenmerken | De bestemming vereist verrijkingsattributen voor verpersoonlijking of segmentatie (b.v., synchronisatie CRM, partner het delen) | Meer overgedragen gegevens; vereist governance controle voor elk attribuut; controleer de etiketten van het gegevensgebruik tegen bestemmings marketing actie |
>| Identiteit + berekende kenmerken | De voordelen van de bestemming van afgeleide scores of samenvoegingen (b.v., levenswaarderij, aandrijvingsscore voor partner het richten) | Vereist berekende kenmerken die moeten worden geconfigureerd; hoogwaardige verrijking voor downstreamsystemen |

>[!NOTE]
>
>**Besluit: Uitvoer het plannen (partijbestemmingen slechts)**
>
>Hoe vaak moeten publieksgegevens worden geëxporteerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Dagelijks | Standaard vernieuwingscursus; de meeste gevallen van batchgebruik | Balancering versheid met verwerkingskosten; meest gangbare standaardinstelling |
>| Elke 3-6 uur | Hoger gebruik, bijvoorbeeld binnen de dag optimalisatie van de campagne | Veelvoorkomende bestandsgeneratie; hogere opslag- en verwerkingsbelasting op de bestemming |
>| Op aanvraag (ad hoc) | Eenmalige export of dringende activering buiten de cyclus | Handmatig omzeilen van trigger, schema; handig voor testen of dringende campagnebehoeften |

**navigatie UI:** Verbindingen > Doelen > doorbladeren > [ Uitgezochte bestemming ] > activeert publiek

**Zeer belangrijke configuratiedetails:**

- Selecteer een of meer soorten publiek om naar het doel te activeren
- Profielkenmerken en identiteitsvelden toewijzen aan bestemmingsspecifieke velden
- Voor streamingdoelen: identiteitsnaamruimtetoewijzing bevestigen (bijv. gehashte e-mail naar extern_id van Facebook)
- Voor batchbestemmingen: configureer het exportschema, selecteer de incrementele of volledige exportmodus en stel de eerste exportdatum in
- Controleer het activeringsoverzicht om alle toewijzingen en planningen te bevestigen voordat u publiceert

**waar de opties uiteenlopen:**

**voor Optie A (het stromen de Activering van de Bestemming):**
Selecteer het publiek en wijs naamruimten toe aan bestemmingsidentiteitsvelden. De activering begint onmiddellijk na het publiceren — het publiekslidmaatschap verandert stroom in de bestemming in dichtbij real time. Er is geen exportschema nodig; de activering gaat door.

**voor Optie B (de Activering van de Bestemming van de Partij):**
Selecteer het publiek, kaartprofielkenmerken en configureer het exportschema. U kunt kiezen tussen de incrementele en volledige exportmodi. U kunt desgewenst een ad-hocexport activeren voor directe levering buiten het normale schema.

**voor Optie C (multi-Doelactivering):**
Herhaal de activeringsworkflow voor elke bestemming. Het zelfde publiek kan aan veelvoudige bestemmingen met verschillende attributenafbeeldingen per bestemming worden geactiveerd. U kunt bijvoorbeeld alleen gehashte e-mailberichten verzenden naar advertentieplatforms, maar demografische kenmerken toevoegen aan de CRM.

**documentatie van Experience League:**

- [Stimulansen voor het publiek naar streamingdoelen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Soorten publiek activeren om exportdoelen voor batchprofielen te gebruiken](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Het publiek op aanvraag activeren naar batchbestemmingen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Dataflows voor doelen controleren](https://experienceleague.adobe.com/nl/docs/experience-platform/dataflows/ui/monitor-destinations)


### Fase 4: Validatie van bestuur

**functie van de Toepassing:** rt-CDP: Toestemming &amp; de Handhaving van het Bestuur

**wat u zult vormen:** bevestigt dat het beleid en de toestemmingsvoorkeur correct vóór en tijdens activering worden afgedwongen. Deze fase zorgt ervoor dat beperkte gegevens (PII, gevoelige kenmerken) niet naar onbevoegde bestemmingen worden verzonden en dat profielen zonder geldige toestemming van activering worden uitgesloten. De handhaving van de governance gebeurt automatisch op activeringstijd, maar de pro-actieve bevestiging verhindert geblokkeerde activering en nalevingsschendingen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: De handhavingsbenadering van het bestuur**
>
>Wanneer moet de naleving van het bestuur worden gevalideerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Proactief (pre-activering) | Aanbevolen voor alle implementaties, met name bij het activeren op externe systemen van derden | De etiketten en het beleid van het gegevensgebruik van het overzicht alvorens gebiedsafbeeldingen te vormen; verhindert activeringsmislukkingen en verzekert naleving van begin |
>| Reactief (op activeringstijd) | Wanneer het bestuursbeleid al goed is ingesteld en het team vertrouwt op naleving | Het platform dwingt automatisch beleid bij activering af; schendingen blokkeren de activering of sluiten beperkte attributen uit; kunnen onverwachte mislukkingen veroorzaken als het beleid niet goed wordt begrepen |

>[!NOTE]
>
>**Besluit: Het filtreren van de toestemming**
>
>Hoe beïnvloeden toestemmingsvoorkeuren activering?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Goedkeuring ingeschakeld | Vereist voor het activeren op reclame- of marketingbestemmingen waarvoor toestemming wettelijk vereist is | Profielen zonder geldige toestemming (consents.marketing.{channel}.val = &#39;y&#39;) worden automatisch van activering uitgesloten; gegevens over toestemming moeten worden ingevoerd |
>| Geen toestemming filteren | Intern gebruik of analytische uitvoer indien de toestemming niet van toepassing is op de gegevensoverdracht | Alleen geschikt wanneer het gegevensgebruik geen marketingactie is waarvoor toestemming vereist is; raadpleeg het juridische/privacy-team |

**navigatie UI:** Privacy > Beleid > Toestemmingsbeleid (voor toestemmingsoverzicht); Het bestuur van gegevens > Beleid (voor het beleidsoverzicht van het gegevensgebruik)

**Zeer belangrijke configuratiedetails:**

- De etiketten van het gegevensgebruik van het overzicht die op de datasets en schemagebieden worden toegepast die worden geactiveerd
- Controleren of het beleid inzake governance actief is voor de marketingactie die aan de bestemming is gekoppeld (bijvoorbeeld &quot;Exporteren naar derden&quot; voor advertentieplatforms)
- Bevestig bevestigingsgebieden op profielen worden bevolkt en dat de handhaving van de toestemming voor de relevante kanalen wordt toegelaten
- Als beleidsovertredingen worden gedetecteerd, kunt u dit oplossen door beperkte velden te verwijderen uit de doeltoewijzing of een andere bestemming te selecteren

**documentatie van Experience League:**

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home)
- [Beleidshandhaving](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/enforcement/overview)
- [Overzicht van labels voor gegevensgebruik](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/labels/overview)
- [Toestemming en voorkeuren](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Toestemming voor beleidshandhaving](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/policies/user-guide)


### Fase 5: Controle en validatie

**functie van de Toepassing:** Controle &amp; Observability

**wat u zult vormen:** opstelling aan de gang zijnde controle voor activeringsdataflows, vormt alarm voor mislukkingen, bevestigt publiekspopulatie bij bestemmingen, en het gebruik van de spoorvergunning. Monitoring is essentieel voor productieactiviteiten waarbij leveringsfouten rechtstreeks van invloed zijn op de prestaties van de campagne en de uitgaven van de media.

**Zeer belangrijke configuratiedetails:**

- De dataflow van het overzicht looppas status voor elke actieve bestemming om publiek te bevestigen met succes wordt geleverd
- Waarschuwingen configureren voor mislukte doelactivering, vertragingen bij gegevensstroom en anomalieën in de doelpopulatie
- Trackprofielen geëxporteerd versus profielen mislukt bij uitvoering van gegevensstroom
- Volgorde van de monitor past tarieven bij de bestemming (waar bestemmingrapport beschikbaar is) aan
- Het gebruik van een licentie controleren om het volume van het geactiveerde profiel op te sporen met rechten

**navigatie UI:** Verbindingen > Doelen > [ Uitgezochte bestemming ] > looppas Dataflow (voor activeringscontrole); Alarm > Waakzame regels > Abonneren (voor waakzame configuratie); Beleid > het gebruik van de Vergunning (voor vergunning het volgen)

**documentatie van Experience League:**

- [Dataflows voor doelen controleren](https://experienceleague.adobe.com/nl/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/alerts/overview)
- [Overzicht van observatiegegevens](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/home)
- [Het gebruiksdashboard voor licenties](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

## Implementatieoverwegingen

Lees de volgende overwegingen voor en tijdens de implementatie.

### Guardrails en limieten

- **de definitiegrens van het Segment:** Maximum van 4.000 segmentdefinities per zandbak - [&#x200B; de begeleiding van de segmentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)
- **Dataflows per bestemming:** Maximum van 100 dataflows per bestemmingsverbinding - [&#x200B; Bedoelingsgidsen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/guardrails)
- **de grootte van het de uitvoerdossier van de Partij:** Op dossier-gebaseerde bestemmingen hebben maximum de groottegrenzen van het de uitvoerdossier; de grote publiek wordt automatisch verdeeld over veelvoudige dossiers
- **het stromen bestemmingsproductie:** Per-seconde de productiegrenzen worden geplaatst door elke bestemmingspartner; de veranderingen van het hoog-volumepubliek kunnen worden vertraagd
- **de evaluatiecapaciteit van de Partij:** Tot 24 miljoen profielen per de baan van de segmentevaluatie door gebrek
- **Samenstelling van het publiek:** Maximum van 10 samenstellingsblokken per canvas; de samengestelde doelgroepen worden slechts batch-geëvalueerd
- **grafiek van de Identiteit:** Maximum van 50 identiteiten per grafiek - [&#x200B; Garanties van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/guardrails)
- **Berekende attributen:** Maximum van 25 gegevens verwerkte attributen per zandbak — [&#x200B; de gegevens verwerkte attributengidsen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **overzicht van de gidsen van de Activering:** [&#x200B; de guardrails van de Activering &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/guardrails)

### Veelvoorkomende valkuilen

- **het stromen segment met niet in aanmerking komende regellogica:** Bepalend een publiek met complexe samenvoegingsfuncties of multi-entiteitvragen en verwacht het stromen evaluatie. Deze segmenten vallen ongemerkt terug op batchevaluatie, wat onverwachte vertraging veroorzaakt. Preventie: bekijk de vereisten voor streaminggeschiktheid voordat u het publiek definieert.

- **Nul die profielen wegens toestemmings het filtreren worden uitgevoerd:** Alle profielen in het publiek hebben geldige toestemmingswaarden, die het volledige publiek veroorzaken om uit op activeringstijd worden gefiltreerd. Preventie: controleer of de inname van toestemmingsgegevens operationeel is en of de toestemmingsvelden zijn ingevuld voordat deze worden geactiveerd.

- **beleid dat van de Governance activering onverwacht blokkeert:** de gebruiksetiketten van gegevens op schemagebieden brengen beleidsschendingen teweeg die activering verhinderen. Preventie: evalueer pro-actief governance naleving (Fase 4) alvorens gebiedsafbeeldingen te vormen. Controleer welke labels van het schema zijn overgenomen.

- **de credentievervaldatum van de Bestemming:** De tokens van OAuth of API de sleutels verlopen, veroorzakend activeringsmislukkingen zonder onmiddellijk alarm. Preventie: vorm alarm voor de mislukkingen van de bestemmingsactivering en bepaal een credentieel omwentelingsprogramma.

- **Verkeerd gematchte identiteit namespaces:** De identiteit namespace die in de activeringsafbeelding wordt gevormd past niet aan wat de bestemming (b.v., verzendend duidelijk-tekst e-mail wanneer de bestemming SHA-256 gehakt e-mail vereist) verwacht. Preventie: controleer doeldocumentatie voor vereiste identiteitsindelingen alvorens de afbeelding te vormen.

- **de afbeeldingsfouten van het Gebied die uitvoermislukkingen veroorzaken:** Toewijzing een profielattribuut aan een bestemmingsgebied met een incompatibel gegevenstype of formaat. Preventie: test eerst de activering met een klein publiek en bekijk de gegevens voor de uitvoering van de gegevensstroom voor het in kaart brengen van fouten alvorens aan productiepubliek te schrapen.

- **de bevolkingsverschuiving van het publiek tussen rt-CDP en bestemming:** de publiekstelling in rt-CDP past niet de telling bij de bestemming toe toe toe toe toe toe te schrijven aan identiteit passende verschillen, bestemmingsdeduplicatielogica, of timing. Dit wordt verwacht gedrag — preventie: in een document worden benchmarks voor het benchmarkpercentage per bestemming verwacht en wordt gecontroleerd op significante afwijkingen.

### Aanbevolen procedures

- **Begin met een testpubliek:** activeer een klein, goed begrepen testpubliek aan elke nieuwe bestemming alvorens productiepubliek te activeren. Valideer veldtoewijzingen, identiteitsvergelijking en leveringscijfers met het testpubliek.

- **Laageigenschap vroeg:** pas de etiketten van het gegevensgebruik toe en vorm governancebeleid alvorens bestemmingsactiveringen te vormen. Hiermee voorkomt u geblokkeerde activering en zorgt u ervoor dat aan het begin wordt voldaan.

- **de stijgende uitvoer van het gebruik voor partijbestemmingen:** De stijgende uitvoer vermindert dossiergrootte, versnelt verwerking bij de bestemming, en minimaliseert opslagkosten. De volledige uitvoer van het gebruik slechts wanneer het bestemmingssysteem een volledige publieksvervanging vereist.

- **normaliseer het noemen overeenkomsten:** Vestig verenigbare het noemen voor publiek, bestemmingsverbindingen, en dataflows over de organisatie. Neem het gebruiksgeval, de bestemming en de evaluatiemethode op in namen (bijvoorbeeld &quot;Suppression_ExistingCustomers_Facebook_Streaming&quot;).

- **de gelijke tarieven van de Monitor:** spoor de verhouding van profielen die van rt-CDP naar profielen worden uitgevoerd die bij elke bestemming worden aangepast. Aanzienlijke dalingen in gelijke tarief kunnen op identiteitsresolutiekwesties, credentieproblemen, of bestemmingsAPI veranderingen wijzen.

- **coördinaat onderdrukking over bestemmingen:** wanneer het gebruiken van suppressiepubliek (b.v., exclusief bestaande klanten van aanschafcampagnes), activeer het suppressiepubliek aan alle relevante advertentieplatforms gelijktijdig om consistentie te handhaven.

- **Overzicht en duw inactieve activeringen af:** herzie periodiek bestemmingsdataflows en deactiveer publiek die niet meer nodig zijn. Inactieve activeringen verbruiken licentiecapaciteit en voegen controleoverhead toe.

### Handelsbesluiten

>[!NOTE]
>
>**handel-off: De versheid van het publiek tegenover segmenteringsflexibiliteit**
>
>De het stromen evaluatie levert dichtbij publieksupdates in real time maar beperkt de functies van de segmentregel u kunt gebruiken. De evaluatie van de partij steunt de volledige reeks van de segmentregel maar introduceert latentie (uren in plaats van notulen).
>
>- **het stromen begunstigt:** In real time gebruiksgevallen waar het publiekslidmaatschap bij de bestemming binnen notulen (actieve campagneonderdrukking, retargeting in real time) moet weerspiegelen
>- **de Partij verkiest:** Complexe publiekslogica die samenvoegingsfuncties, multi-entiteitvragen, of grote tijd-venster voorwaarden (de lagen van de levenwaarde, multi-aanraking gedragssegmenten vereist)
>- **Aanbeveling:** het stromen van het gebruik evaluatie voor publiek dat aan het stromen bestemmingen wordt geactiveerd waar de helderheid in real time bedrijfswaarde drijft. De partijevaluatie van het gebruik voor complexe publiek geactiveerd aan op dossier-gebaseerde bestemmingen of wanneer dagelijks verfrist volstaat. Voor publiek dat beide nodig heeft, kunt u twee versies maken: een vereenvoudigd streaming segment voor realtime activering en een uitgebreid batchsegment voor periodieke verrijking.

>[!NOTE]
>
>**handel-off: Minimale gegevensuitvoer vs. rijke attributenafbeelding**
>
>Door alleen identiteitsvelden te exporteren (hashed email, device ID) minimaliseert u de blootstelling aan gegevens en vereenvoudigt u het beheer. Door extra profielkenmerken te exporteren (demografie, waardeniveau, betrokkenheidsscore) verrijkt u de bestemming, maar vergroot u de complexiteit van het beheer en de aansprakelijkheid voor gegevens.
>
>- **Minimale uitvoervoorkeur:** privacy-eerste benadering; lager governancerisico; eenvoudiger gebiedstoewijzing; voldoende voor de meeste zaken van het gebruikstoepassing en van de onderdrukking van het platform richten
>- **de rijke uitvoer begunstigt:** Downstream verpersoonlijking bij de bestemming; de verrijking van CRM; partnergegevens die delen die attribuut-vlakke detail vereist
>- **Aanbeveling:** Gebrek aan minimale identiteit-slechts uitvoer voor reclamebestemmingen. Voeg profielattributen slechts toe wanneer de geval van het bestemmingsgebruik hen specifiek vereist en de controle van het bestuur bevestigt naleving. Gebruik berekende kenmerken om geaggregeerde, minder gevoelige verrijkingswaarden te verschaffen in plaats van onbewerkte PII.

>[!NOTE]
>
>**handel-off: Enig publiek per bestemming vs. geconsolideerde multi-publieksdataflows**
>
>Wanneer u elk publiek activeert als een aparte gegevensstroom, hebt u isolatie en korrelige controle nodig. Het activeren van veelvoudige publiek door één enkele dataflow aan een bestemming vereenvoudigt beheer maar vermindert isolatie.
>
>- **afzonderlijke dataflows:** Onafhankelijk toezicht, gemakkelijkere het oplossen van problemen, capaciteit om individuele publieksactiviteiten te pauzeren zonder anderen te beïnvloeden
>- **Geconsolideerde dataflows:** Minder te handhaven verbindingen, vereenvoudigd credentiebeheer, verminderde operationele overheadkosten
>- **Aanbeveling:** Gebruik geconsolideerde dataflows wanneer het activeren van veelvoudige verwante toehoorden aan de zelfde bestemming (b.v., alle onderdrukkingssegmenten aan Facebook). De afzonderlijke dataflows van het gebruik wanneer het publiek verschillende SLAs, verschillende attributenafbeeldingen heeft, of wanneer de mislukkingsisolatie kritiek is.

## Gerelateerde documentatie

**Doelen**

- [Overzicht van doelen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/home)
- [Doelcatalogus](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/overview)
- [Stimulansen voor het publiek naar streamingdoelen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Soorten publiek activeren om exportdoelen voor batchprofielen te gebruiken](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Het publiek op aanvraag activeren naar batchbestemmingen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/api/ad-hoc-activation-api)
- [Doelgeleidingen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/guardrails)
- [Destination SDK-overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/destination-sdk/overview)

**Soorten publiek en segmentatie**

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/segment-builder)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentering](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Overzicht van Audience Composition](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/audience-composition)
- [Segmenteringsgeleiding](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)

**Identiteit en profiel**

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/home)
- [Overzicht van naamruimten](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/features/namespaces)
- [Koppelingsregels voor identiteitsgrafiek](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/features/identity-linking-logic)
- [Profieloverzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/home)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/merge-policies/overview)

**modellering en schema&#39;s van Gegevens**

- [XDM System, overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/home)
- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/schema/composition)

**het bestuur van Gegevens**

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home)
- [Overzicht van labels voor gegevensgebruik](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/labels/overview)
- [Beleid inzake gegevensbeheer](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/policies/overview)
- [Beleidshandhaving](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/enforcement/overview)
- [Toestemming en voorkeuren](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Controle en waarneming**

- [Dataflows voor doelen controleren](https://experienceleague.adobe.com/nl/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/alerts/overview)
- [Overzicht van observatiegegevens](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/home)
- [Het gebruiksdashboard voor licenties](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Berekende attributen**

- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/overview)
- [Gebruikershandleiding voor berekende kenmerken](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/ui)

**de inzameling en de bronnen van Gegevens**

- [Overzicht van bronnen](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/home)
- [Overzicht van Web SDK](https://experienceleague.adobe.com/nl/docs/experience-platform/web-sdk/home)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/configure)

**Beleid**

- [Overzicht van sandboxen](https://experienceleague.adobe.com/nl/docs/experience-platform/sandbox/home)
- [Overzicht van toegangsbeheer](https://experienceleague.adobe.com/nl/docs/experience-platform/access-control/home)
- [Toegangsbeheer op basis van kenmerken](https://experienceleague.adobe.com/nl/docs/experience-platform/access-control/abac/overview)

**Guardrails**

- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)
- [Identiteitsservicehandleidingen](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/guardrails)
- [Activeringsinstructies](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/guardrails)
- [Ingestiegrepen](https://experienceleague.adobe.com/nl/docs/experience-platform/ingestion/guardrails)
