---
title: Besluitvorming over aanbiedingen
description: Leer hoe u de gecentraliseerde besluitvormingslogica gebruikt om de op een na beste aanbieding of inhoud voor een profiel te selecteren voor verschillende kanalen.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '7889'
ht-degree: 0%

---


# Beslissing voorstel

Deze handleiding bevat een uitgebreide implementatiereferentie voor het bepalen van aanbiedingen met behulp van [!DNL Adobe Journey Optimizer] (AJO) Decisioning and [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Het wordt ontworpen voor oplossingsarchitecten, marketing technologen, en implementatietechnici die de gecentraliseerde logica van de aanbiedingsselectie moeten uitvoeren die de volgende-beste aanbieding voor elk klantenprofiel over kanalen bepaalt.

Gebruik deze gids om te begrijpen wat moet worden gevormd, waar keuzen bestaan, en welke compromissen op elk besluit van toepassing zijn.

Het patroon ontkoppelt de &quot;wat te tonen&quot;beslissing van de &quot;waar te om het&quot;kanaallogica te tonen, toelatend verenigbare, geoptimaliseerde aanbiedingsselectie over e-mail, Web, mobiele app, en om het even welk ander aanraakpunt. AJO-besluit beheert de volledige levenscyclus van de aanbieding: aanmaak van aanbiedingen en catalogusbeheer, subsidiabiliteitsregels (die elk aanbod kunnen zien), rangschikkingsstrategieën (hoe u kunt kiezen tussen de in aanmerking komende aanbiedingen), stages (waar aanbiedingen verschijnen) en besluitvormingsbeleid (die alles bij elkaar binden).

## Hoofdlettergebruik

Organisaties moeten op het moment van de interactie vaak het meest relevante aanbod, de meest relevante promotie of de meest relevante prikkel aan elke klant presenteren. Of de interactie plaatsvindt in een e-mailcampagne, op een website homepage, in een mobiele app of op een beslissingspunt binnen een meerstapsreis, de uitdaging is dezelfde: selecteer de optimale aanbieding in een catalogus met beschikbare opties op basis van wie de klant is, waarvoor zij in aanmerking komen en welke aanbieding het meest geschikt is om het gewenste resultaat te bereiken.

De besluitvorming van de aanbieding richt dit door alle aanbiedingsselectielogica in AJO te centraliseren Beslissingsbeheersmotor. In plaats van hardcodering biedt toewijzingen aan in afzonderlijke campagnes of kanalen, evalueert de besluitvormingsmotor de attributen van elk profiel, het publiekslidmaatschap, en contextafhankelijke signalen om de beste aanbieding in echt te bepalen - tijd. Deze centralisatie zorgt ervoor dat de zelfde klant verenigbare, geoptimaliseerde aanbiedingen ontvangt ongeacht welk kanaal zij door.

Dit patroon verschilt qua bereik van bekende gebruikers van websites/apps. Beslissing is kanaalagnostisch en gecentraliseerd, terwijl bekende bezoekers zich richten op de personalisatie van digitale oppervlakken. Het verschilt van gedragsaanbevelingen in benadering — bied besluitvorming expliciete geschiktheidsregels en rangordestrategieën aan, terwijl gedragsaanbevelingen de nadruk leggen op gedragssignaal-gedreven aanbevelingen gebruikend selectiestrategieën en modellen van ML.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

**[lever gepersonaliseerde klantenervaringen](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**
Inhoud, aanbiedingen en berichten voor individuele voorkeuren, gedrag en levenscyclusfase aanpassen.
**KPIs:** Betrokkenheid, Conversietarieven, Tevredenheid van de Klant (CSAT)

**[de dwars-verkoop van de aandrijving &amp; upsell opbrengst](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)**
Aanvullende en hoogwaardige producten of services aan bestaande klanten promoten op basis van gedrag en aankoopgeschiedenis.
**KPIs:** Upsell/Cross-Sell %, Incrementele Inkomsten, de Waarde van het Leven van de Klant

**[de klantenloyaliteit en levenwaarde van de verhoging](../../business-objectives/revenue-monetization/increase-customer-loyalty-lifetime-value.md)**
Verbeter klantenverhoudingen en maximaliseer waarde op lange termijn door loyaliteitsprogramma&#39;s, beloningen, en gepersonaliseerde betrokkenheid.
**KPI&#39;s:** Levensduur klant, Retentie, Upsell/Cross-sell%

## Voorbeelden van tactische gebruiksgevallen

De volgende scenario&#39;s illustreren hoe de aanbodbeslissing in de praktijk kan worden toegepast.

- Volgende beste aanbieding in e-mailcampagnes — selecteer de meest relevante aanbieding per ontvanger op verzendtijd
- Promotiebanner in realtime op de website: door te beslissen wordt de aanbieding tijdens het laden van de pagina geselecteerd op basis van het profiel van de bezoeker
- Aangepaste interne kaart met de beste prikkel voor de levenscyclusfase van de gebruiker
- Interchannel bieden consistentie — dezelfde beslissingslogica dient voor e-mail, web en push, zodat de klant een uniforme aanbiedingservaring ziet
- Dynamische coupon- of kortingsselectie op basis van het waardeniveau van de klant (klanten met een hoge waarde ontvangen bijvoorbeeld een premium-aanbieding)
- Selectie voor productupgrade of upselvoorstel op basis van huidig abonnementsniveau
- Loyalty biedt verpersoonlijking op basis van tier en activiteitengeschiedenis

## Kernprestatie-indicatoren

De volgende PKIs helpen de doeltreffendheid van een implementatie van het aanbiedingsbesluit meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Aanbiedingsacceptatie | Percentage geleverde aanbiedingen dat resulteert in een klik, terugbetaling of conversie | Aanbieding klikt of aflossingen/Totaal aantal aangeboden aanbiedingen |
| Selectiedistributie aanbieden | Percentage van elk aanbod dat is geselecteerd voor alle beslissingen | Aantal per aanbieding/Totaal aantal genomen beslissingen |
| Fallbacksnelheid | Percentage besluiten waarbij geen gepersonaliseerd aanbod in aanmerking kwam en de fallback werd gedaan | Terugvalindrukkingen/Totaal aantal beslissingen |
| Conversiesnelheid | Percentage van de ontvangers van de aanbieding die de gewenste actie hebben uitgevoerd (aankoop, aanmelding, terugbetaling) | Conversies/aanbiedingen |
| Incrementele inkomsten | Opbrengsten die zijn toe te schrijven aan door besluiten gekozen aanbiedingen versus een controlegroep of terugvalsteun | Ontvangsten uit gepersonaliseerde aanbiedingen - Ontvangsten uit fallback/controle |
| Consistentiescore tussen kanalen | Percentage profielen dat dezelfde aanbieding via meerdere kanalen binnen een bepaald venster ontvangt | Consistente aanbiedingen / Totaal aantal meerkanaalsindrukwekkende beelden |
| Doorkliksnelheid aanbieden | Percentage van aanbiedingsindrukken dat resulteert in een klik | Aanbiedingen klikken/impressies aanbieden |

## Hoofdletterpatroon gebruiken

In deze sectie worden de functieketen en patroondefinitie voor het bepalen van aanbiedingen beschreven.

**het besluit van de Aanbieding**

Gebruik de gecentraliseerde besluitvormingslogica om de op één na beste aanbieding of inhoud voor een profiel over kanalen te selecteren.

**Keten van de Functie:** de Evaluatie van het publiek > de Ontvankelijkheid van de Aanbieding > Rangschikkende Strategie > de Uitvoering van het Besluit > Levering > het Melden

Zie de [ sectie van de Opties van de Implementatie ](#implementation-options) voor hoe elke samenstelling zich manifesteert.

## Applicaties

In dit gebruikspatroon worden de volgende Adobe-toepassingen gebruikt.

- **[!DNL Adobe Journey Optimizer](AJO)** — De motor van het Beheer van het Besluit voor het aanbieden creatie, geschiktheidsregels, rangschikkingsstrategieën, plaatsingen, en besluitvormingsbeleid; kanaalconfiguratie en berichtauteurs voor aanbieding; campagne en reis uitvoering
- **[!DNL Adobe Real-Time Customer Data Platform](rt-CDP)** — Poortevaluatie voor aanbiedingssegmenten; profielgegevens en berekende attributen die in geschiktheid en rangschikking worden gebruikt
- **[!DNL Adobe Experience Platform](AEP)** — Verenigde profielopslag, identiteitsresolutie, en gegevensstichting die zowel AJO als rt-CDP steunen

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | AJO-sandbox met beslissingsbevoegdheden ingeschakeld. Bied beheerrollen aan (Beslissingsmanager, Aanbiedingsfiatteur) die zijn toegewezen aan het implementatieteam. | [ het overzicht van Sandboxen ](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [ overzicht van de Toegangscontrole ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | Profielschema moet kenmerken bevatten die worden gebruikt voor de geschiktheidsregels voor aanbiedingen (bijv. een loyaliteitslaag, koopgeschiedenis, soort abonnement). Een aanbiedingsreactie-/interactieschema voor het bijhouden van aanbiedingsindrukkingen, klikken en conversies moet zijn ingesteld. | [ XDM het overzicht van het Systeem ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [ de samenstellingsgrondbeginselen van het Schema ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Gegevensbronnen en -verzameling | Verondersteld op plaats | Profielkenmerken die worden gebruikt in subsidiabiliteitsregels moeten actueel zijn. Voor Weblevering (Optie B), moet het Web SDK met de dienst van AJO worden uitgevoerd die op de datastream wordt toegelaten. Voor het verzenden van e-mail, moeten de profielattributen bij verzendtijd oplosbaar zijn. | {het overzicht van SDK van 0} Web ](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [ vormt gegevensstromen ](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)[ |
| Identiteit en profielconfiguratie | Verondersteld op plaats | Profielen moeten op alle kanalen kunnen worden opgelost waar aanbiedingen worden geleverd. Voor consistentie tussen kanalen is een uniforme identiteit essentieel. Hetzelfde profiel moet worden herkend in e-mail-, web- en mobiele contexten. Een randactief samenvoegbeleid is vereist voor realtime web-/app-levering. | [ overzicht van de Dienst van de Identiteit ](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [ overzicht van het beleid van de Fusie ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Auditiedefinitie en segmentatie | Vereist | Als criteria voor het in aanmerking nemen van aanbiedingen gebruikte publiek moet worden gedefinieerd en beoordeeld (bv. &quot;klanten met een hoge waarde&quot;, &quot;proefgebruikers&quot;, &quot;goudlaag voor loyaliteit&quot;). De evaluatiemethode moet overeenkomen met de vertraging bij de levering — Edge-evaluatie voor realtime web/app, batch of streaming voor e-mailcampagnes. | [ overzicht van de Dienst van de Segmentatie ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [ de gids UI van de Bouwer van het Segment ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Klant-AI-waardenscores, levenswaardeberekeningen en maatstaven voor betrokkenheid verbeteren de effectiviteit van de classificatiestrategie aanzienlijk. Met berekende kenmerken, zoals &quot;dagen sinds laatste aankoop&quot; of &quot;totaal besteden in 90 dagen&quot;, kunnen nauwkeurigere toelatingsregels en op formule gebaseerde rangorde worden ingevoerd. | ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [ overzicht van de Klant AI van 0} Berekende attributen ](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)[ |
| Levenscyclusbeheer van gegevens | Aanbevolen | De geschiedenis van de aanbieding en de gegevens van de beslissingsgebeurtenis accumuleren zich in tijd. Het beleid van het behoud (afloop) zou voor de datasets van de de interactiegebeurtenis moeten worden gevormd om opslag te beheren en aan de vereisten van het gegevensbehoud te voldoen. | [ het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens ](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [ Verlopen Dataset ](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | Regelgevingslabels zorgen ervoor dat aanbiedingen met gevoelige doelcriteria (bijvoorbeeld financiële status, gezondheidsomstandigheden) voldoen aan het beleid voor gegevensgebruik. Etiketten op velden die in de subsidiabiliteitsregels worden gebruikt, voorkomen dat niet-conforme aanbiedingen worden gericht. | [ het beheer van Gegevens overzicht ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [ overzicht van de gebruiksetiketten van Gegevens ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Bewaking en waarneming | Aanbevolen | De prestaties van de beslissingsmotor, de terugvalsnelheden en de gezondheid van de levering moeten worden gecontroleerd. De alarm voor hoge reservetarieven kan op geschiktheidsregelmisconfiguration of de kwesties van de gegevensversheid wijzen. | [ het overzicht van Alarm ](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [ Overzicht van de Inzichten van de Waarneming ](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | De prestatiesrapportering van aanbiedingen maakt deel uit van de functieketen (Fase 7). De analyse van CJA maakt het mogelijk om de doeltreffendheid van de dwars-kanaalaanbieding, opbrengsteffect attributie, en optimaliseringsopportuniteit identificatie te meten. | [ overzicht van CJA ](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [ overzicht van Analysis Workspace ](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer] (AJO)

De volgende lijst maakt een lijst van de functies van AJO en de implementatiefasen waar zij worden gevormd.

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Besluitvorming | Fase 3: Instellingen voor besluitvorming | Aanbiedingspunten maken, toelatingsregels definiëren, classificatiestrategieën configureren, terugvalaanbiedingen maken, plaatsingen definiëren en besluitvormingsbeleid maken |
| Kanaalconfiguratie | Fase 4: Configuratie van kanaal en oppervlak | E-mail-, web-, in-app- of op code gebaseerde kanaaloppervlakken configureren voor levering |
| Berichtontwerp | Fase 5: Configuratie van inhoud en levering | Ontwerpberichtsjablonen met plaatsingszones voor aanbiedingen; op code gebaseerde ervaringen configureren voor levering via web/app |
| Campagne uitvoeren | Fase 5: Configuratie van inhoud en levering | Uitvoeren geplande of API-teweeggebrachte campagnes die besluitvormingsbeleid (Optie A) aanhalen |
| Inhoud experimenteren | Fase 5: Configuratie van inhoud en levering | Optioneel test A/B verschillende classificatiestrategieën of biedt creatieve varianten |
| Rapportage en prestatieanalyse | Fase 7: Rapportage en prestatiebewaking | Monitor biedt selectiedistributie, acceptatiesnelheden, fallback-snelheden en prestaties op kanaalniveau |

### [!DNL Real-Time CDP] (RT-CDP)

De volgende lijst maakt een lijst van functies RT-CDP en de implementatiefasen waar zij worden gevormd.

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Fase 2: Evaluatie van het publiek | Bepaal en evalueer publiek dat voor de regels van de aanbiedingsontvankelijkheid wordt gebruikt; selecteer aangewezen evaluatiemethode (partij, het stromen, of rand) |
| Profielverrijking | Fase 1 (Ondersteuning): berekende kenmerken | Verrijk profielen met berekende kenmerken en eigenschapscores die de effectiviteit van de classificatiestrategie verbeteren |

## Vereisten

Voltooi de volgende voorwaarden voordat u begint met de implementatie.

- [ ] AJO-sandbox met mogelijkheden voor Beslissingsbeheer ingeschakeld
- [ ] Gebruikersrollen met beslissingsbeheermachtigingen (aanbiedingen, plaatsingen, beslissingen maken/bewerken)
- [ ] Profielschema bevat kenmerken die vereist zijn om in aanmerking te komen voor een aanbieding (bijvoorbeeld een loyaliteitsniveau, klantensegment, abonnementsniveau)
- [ ] Profielgegevens zijn actueel en worden actief ingevoerd voor kenmerk-versheid voor geschiktheid
- [ ] Voor optie A (E-mail): E-mailkanaaloppervlak geconfigureerd met geverifieerd subdomein en geïntegreerde pool
- [ ] Voor Optie B (Web/App): Web SDK geïmplementeerd met AJO-service ingeschakeld op de gegevensstroom; edge-active samenvoegbeleid geconfigureerd
- [ ] Voor optie C (Reis): de toestemmingen van het canvas van de reis en minstens één gebeurtenis of publiek gevormd van de reisingang
- [ ] Creatieve elementen aanbieden (afbeeldingen, kopiëren, CTA&#39;s) voorbereid voor elke aanbieding en plaatsingscombinatie
- [ ] Inhoud van de terugvalaanbieding die voor elke plaatsing wordt voorbereid
- [ ] Soorten publiek voor aanbiedingstoelatingsregels gedefinieerd en geëvalueerd in RT-CDP

## Implementatieopties

In deze sectie worden de beschikbare implementatieopties voor het bepalen van aanbiedingen beschreven. Elke optie dient een ander leveringskanaal en een ander gebruiksscenario.

### Optie A: Beslissing van e-mailaanbiedingen

Deze optie is het meest geschikt voor het selecteren van de beste aanbieding om in uitgaande e-mailcampagnes op te nemen — promotionele e-mails, personalisatie voor nieuwsbrieven, levenscycluse-mails met dynamische aanbiedingsinhoud. Het besluit wordt genomen bij de tijd van de berichtteruggave voor elke ontvanger.

#### Hoe werkt het

Beslissingsbeleid wordt aangeroepen tijdens het genereren van e-mailberichten om de beste aanbieding voor elke ontvanger te selecteren. De e-mailsjabloon bevat een zone voor plaatsing van aanbiedingen waar de beslissingsengine de inhoudsweergave van de geselecteerde aanbieding (afbeelding, HTML of tekst) invoegt. Tijdens het verzenden evalueert de engine het profiel van elke ontvanger aan de hand van de regels voor het in aanmerking nemen van aanbiedingen, past de classificatiestrategie toe en sluit de inhoud van de winnende aanbieding in de e-mail in.

Deze benadering werkt met zowel geplande campagnes (die in de tijd van de campagneuitvoering worden geëvalueerd) als reis-ingebedde e-mail (die wordt geëvalueerd wanneer het profiel de knoop van de berichtactie bereikt). De inhoud van het aanbod — image, kop, kopie van het lichaam en CTA — wordt gepersonaliseerd per ontvanger op basis van de uitkomst van het besluit.

#### Belangrijkste overwegingen

- Aanbiedingsgeschiktheid wordt tijdens het verzenden geëvalueerd op basis van de huidige status van het profiel
- De evaluatie van het publiek in de batch is voldoende omdat beslissingen tijdens het weergeven van berichten plaatsvinden
- Voor elk aanbod is een HTML of afbeelding-inhoud nodig voor plaatsing van de e-mail
- Voor elke gebruikte e-mailplaatsing moet het terugvalvoorstel inhoud bevatten

#### Voordelen

- Eenvoudigste implementatiepad: maakt gebruik van standaard e-maillevering voor campagne of reizen
- Geen SDK-vereisten voor clients
- Werkt met bestaande e-mailinfrastructuur en kanaaloppervlakken
- Steunt grote publieksvolumes door de uitvoering van de partijcampagne

#### Beperkingen

- De beslissing wordt genomen op het tijdstip van verzending; kan zich niet aanpassen aan het gedrag na verzending
- De inhoud van de aanbieding is statisch zodra e-mail wordt geleverd (geen updates in real time)
- Beperkt tot profielkenmerken die beschikbaar zijn in de opslagruimte van het hubprofiel (niet voor Edge)

#### Experience League-bronnen

- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

### Optie B: Beslissing van aanbiedingen via Web/app in real-time

Deze optie is het meest geschikt voor selectie in real-time op webpagina&#39;s of mobiele apps — promotionele homepagebanners, widgets voor accountdashboardaanbiedingen, kaarten voor in-app-aanbiedingen of een digitaal oppervlak waarop de aanbieding moet worden geselecteerd op het moment dat de pagina wordt geladen of het scherm wordt weergegeven.

#### Hoe werkt het

Beslissingsbeleid wordt aangeroepen bij het laden van een pagina of het weergeven van een toepassingsscherm via het Edge-beslissingsnetwerk of op code gebaseerde ervaringen. Wanneer een bezoeker een pagina laadt, stuurt de Web SDK een aanvraag naar de Edge Network, die het randprofiel van de bezoeker evalueert aan de hand van de toelatingsregels voor aanbiedingen en rangschikkingsstrategieën. De geselecteerde aanbieding is teruggekeerd in de reactie en in de gevormde plaatsing op het digitale oppervlak teruggegeven.

Voor code-gebaseerde ervaringen, wint de toepassing de besluitreactie terug en geeft de aanbiedingsinhoud gebruikend douane front-end logica terug. Voor webkanaalervaringen kan het AJO-webkanaal de inhoud van de aanbieding rechtstreeks in de pagina injecteren door middel van visuele of op code gebaseerde authoring.

#### Belangrijkste overwegingen

- Vereist SDK- of Mobile SDK-implementatie van het web met AJO-service ingeschakeld op de gegevensstroom
- Edge-actief samenvoegbeleid is vereist voor realtime profielopzoekingen
- Voor subsidiabiliteit gebruikte doelgroepen moeten randevaluatie (eenvoudige kenmerkcontroles en segmentlidmaatschap) ondersteunen.
- De inhoud van de aanbieding vertegenwoordigingen zouden JSON of beeldURL formaten voor cliënt-zijrendering moeten gebruiken
- Het volgen van de druk moet worden uitgevoerd om aanbiedingsmeningen en klikken te vangen

#### Voordelen

- Selectie in realtime, tijdens de sessie, gebaseerd op de huidige profielstatus van de bezoeker
- Latentie in tweede beslissingsfase via Edge Network
- Aanbiedingen worden aangepast aan de meest recente profielgegevens die beschikbaar zijn aan de rand
- Ondersteunt A/B-tests van aanbiedingsstrategieën via contentexperimenten

#### Beperkingen

- SDK-implementatie op de client vereist (Web SDK of Mobile SDK)
- Edge-profiel heeft een subset van volledige hubprofielkenmerken — complexe toelatingsregels worden mogelijk niet correct geëvalueerd
- Edge-segmenten hebben beperkingen voor de complexiteit van segmentregels (geen query&#39;s voor tijdreeksen)
- Vereist front-end ontwikkeling voor aangepaste rendering in op code gebaseerde ervaringen

#### Experience League-bronnen

- [Aanbiedingen leveren met de Edge-API voor besluitvorming](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Code-gebaseerd ervaringskanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based-experience/get-started-code-based)

### Optie C: Beslissingsknooppunt voor reis

Deze optie is het beste voor de selectie van aanbiedingen binnen een multi-step reis — het selecteren van de beste aanbieding op een besluitvormingspunt in een klantenreis, dan het leveren van het door de volgende actieknooppunt. Gebruik dit wanneer het biedingsbesluit deel van een bredere orchestratiestroom met wacht, voorwaarden, en veelvoudige berichtacties uitmaakt.

#### Hoe werkt het

Het beleid van het besluit wordt aangehaald van een besluitvormingsknoop binnen een de reiscanvas van AJO. Wanneer een profiel het beslissingsknooppunt bereikt, evalueert de engine de geschiktheid en rangschikking van de aanbieding om de optimale aanbieding te selecteren. De geselecteerde aanbieding informeert de volgende berichtactie — die inhoud aanbieden om te omvatten, welk kanaal te gebruiken, of welke reistak te nemen op basis van het aanbiedingsresultaat.

Deze aanpak maakt adaptieve reizen mogelijk wanneer het besluit tot het aanbieden van het aanbod van invloed is op latere stappen van de reis. Een reis kan bijvoorbeeld de beste aanbieding selecteren, deze via e-mail verzenden, wachten op betrokkenheid en vervolgens een pushmelding uitvoeren als het aanbod niet is geopend.

#### Belangrijkste overwegingen

- De reis moet met een beslissingsknoop worden ontworpen die door één of meerdere knopen van de berichtactie wordt gevolgd
- Aanbiedingsgeschiktheid wordt beoordeeld aan de hand van de status van het profiel op het moment dat het profiel het beslissingsknooppunt bereikt
- De reis wacht stappen tussen de beslissing en levering kan de staat van het profiel veroorzaken om te veranderen
- Kan combineren met vertakking van de reis om verschillende wegen te nemen gebaseerd op welke aanbieding werd geselecteerd

#### Voordelen

- Hiermee wordt selectie in meerdere stappen geïntegreerd
- Maakt adaptieve reizen mogelijk wanneer de keuzemogelijkheid van invloed is op de volgende stappen
- Biedt ondersteuning voor levering via meerdere kanalen binnen dezelfde reis (e-mail, push, SMS)
- Kan combineren met reisvoorwaarden voor service na aanbieding

#### Beperkingen

- Complexere organisatie dan standalone campagnebeslissingen
- Er gelden beperkingen voor de doorvoer van reizen (5.000 profielen per seconde)
- Beslissing is gekoppeld aan de context van de reis — veranderingen vereisen een ombuiging van de reis
- Reis moet opnieuw worden gepubliceerd om de catalogus met aanbiedingen of de actualiseringen van het besluitvormingsbeleid van kracht te laten worden

#### Experience League-bronnen

- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Optievergelijking

In de volgende tabel worden de drie implementatieopties vergeleken met de belangrijkste criteria.

| Criteria | Optie A: E-mailbesluitvorming | Optie B: Web/app in real-time | Optie C: Beslissingsknooppunt voor reis |
| --- | --- | --- | --- |
| Best voor | Batch-e-mailcampagnes met selectie per ontvanger | Banners in realtime aanbieden op internet/op toepassingsoppervlakken | Selectie aanbieden binnen meerstaps georkestreerde reizen |
| Vertraging bij besluit | Tijdens het verzenden (seconden per ontvanger tijdens batchrendering) | Subseconde (Edge Network) | Bij uitvoering van knooppunt (seconden) |
| Kanaal | E-mail | Web, mobiele app, op code gebaseerde oppervlakken | Elk kanaal (e-mail, push, SMS) binnen de reis |
| SDK vereist | Nee | Ja (Web SDK of Mobile SDK) | Nee (voor e-mail/push); Ja (als het webkanaal een reisactie is) |
| Poortevaluatie | Batch of streaming | Edge | Batch, streaming of edge (afhankelijk van het reisadres) |
| Bereik profielgegevens | Volledig hubprofiel | Edge-profiel (subset) | Volledig hubprofiel |
| Complexiteit | Laag | Medium-High | Gemiddeld |
| Doorvoer | Hoog (batchcampagnevolumes) | Hoog (Edge Network-schaal) | Medium (beperkingen van de reisdoorvoer gelden) |

### Kies de juiste optie

Gebruik de volgende richtlijnen om de beste implementatieoptie voor uw gebruiksgeval te selecteren.

- **kies Optie A** als het primaire gebruiksgeval de beste aanbieding per ontvanger in uitgaande e-mailcampagnes selecteert en geen cliënt-kant SDK beschikbaar is. Dit is het eenvoudigste implementatiepad en werkt goed voor promotiemateriaal, nieuwsbrieven en levenscycluscampagnes.
- **kies Optie B** als de aanbiedingen in echt - tijd moeten worden geselecteerd op het ogenblik een bezoeker een Web-pagina laadt of een mobiele app opent. Hiervoor is Web SDK of Mobile SDK vereist en een &#39;edge-active&#39; samenvoegbeleid, maar dit biedt de snelste, meest contextuele aanbiedingsselectie.
- **kies Optie C** als het aanbiedingsbesluit deel van een bredere klantenreis met veelvoudige stappen, wacht, en voorwaardelijk het vertakken uitmaakt. Dit is de juiste keuze wanneer het geselecteerde aanbod invloed moet hebben op de afhandelingsacties of wanneer meerkanaalsfollow-up op basis van de betrokkenheid van het aanbod nodig is.
- **combineer opties** wanneer de aanbiedingen over kanalen constant moeten worden geleverd. Gebruik hetzelfde beslissingsbeleid voor alle drie de opties om ervoor te zorgen dat een klant hetzelfde aanbod ziet in e-mail (Option A), op de website (Option B) en in een follow-up van de reis (Option C).

## Uitvoeringsfasen

De volgende fasen schetsen de implementatiereeks van begin tot eind voor aanbiedingsbesluit.

### Fase 1: Voorwaarden voor het valideren van grondslagen

**de functie van de Toepassing:** AEP: De Modellering en de Voorbereiding van Gegevens, AEP: Identiteit &amp; de Configuratie van het Profiel

Deze fase bevestigt dat de fundamentele gegevenslaag besluiten aanbiedt. Profielschema&#39;s moeten de kenmerken bevatten die worden gebruikt in de toelatingsregels voor aanbiedingen en identiteitsconfiguratie moet het oplossen van profielen voor meerdere kanalen mogelijk maken.

#### Besluit: Profielkenmerken voor subsidiabiliteit

Bepaal welke profielkenmerken worden gebruikt in de toelatingsregels voor aanbiedingen.

>[!NOTE]
>De keuze van profielkenmerken is van invloed op zowel het ontwerp van de toelatingsregel als de doeltreffendheid van de rangorde. Beschouw berekende kenmerken en scores voor eigenheid als hulpmiddel om de beslissingskwaliteit te verbeteren.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Standaardprofielkenmerken (loyaliteitsniveau, aankoopgeschiedenis) | Kenmerken bestaan al in het profielschema | Geen schemaveranderingen nodig; verifieer gegevensversheid |
| Berekende kenmerken (levenslange waarde, betrokkenheidsscore) | De geschiktheid of rangschikking hangt af van geaggregeerde gedragsgegevens | Vereist S1 configuratie; voegt een gebiedsdeel op gegevens verwerkte attributen toe verfrist kadentie |
| Klant AI-waardenscores | De rangschikking zou hefboomwerking op op ML gebaseerde voorspellingen moeten | Vereist voldoende trainingsgegevens (profielen van 10.000+ met doelgebeurtenis); trainingstijd model |

#### Belangrijkste configuratiedetails

- Controleer of het profielschema velden bevat waarnaar wordt verwezen in geschiktheidsregels (bijvoorbeeld `_tenantId.loyaltyTier`, `_tenantId.subscriptionType` )
- Er bestaat al een schema voor het bijhouden van de aanbiedingsinteractie voor indruk-, klik- en conversiegebeurtenissen
- Voor Optie B: Verifieer edge-active samenvoegbeleid wordt gevormd en Web SDK datastream heeft de dienst van AJO toegelaten

#### Experience League-documentatie

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Een schema voor profiel inschakelen](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Fase 2: publieksevaluatie configureren

**functie van de Toepassing:** rt-CDP: de Evaluatie van het publiek

Deze fase definieert en evalueert de soorten publiek die worden gebruikt als criteria om in aanmerking te komen voor de aanbieding. Deze doelgroepen bepalen welke klantsegmenten in aanmerking komen voor specifieke aanbiedingen (bv. &quot;klanten met een hoge waarde&quot; komen in aanmerking voor premiumaanbiedingen, &quot;proefgebruikers&quot; komen in aanmerking voor conversieaanbiedingen).

#### Besluit: Methode voor de evaluatie van het publiek

Bepaal hoe snel het lidmaatschap van de doelgroep moet worden bijgewerkt om in aanmerking te komen voor een aanbieding.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Batchevaluatie | Optie A (e-mailcampagnes) waarbij de geschiktheid tijdens het verzenden wordt beoordeeld | Eenvoudig; alle gesteunde uitdrukkingen van de segmentregel; dagelijks of op bestelling verfrissen zich |
| Streaming evaluatie | Optie A of C wanneer de bijna-real-time publieksupdates tussen partijen worden vereist | Automatisch voor in aanmerking komende segmenten; beperkte segmentregelondersteuning (enkele gebeurtenissen, kenmerkvergelijkingen) |
| Edge-evaluatie | Optie B (web/app in real-time) waar geschiktheid moet worden geëvalueerd bij het laden van de pagina | Subseconde; vereist voor real-time web/app aanbiedingen; beperkt tot eenvoudige controles van kenmerken en segmentlidmaatschap |

**navigatie UI:** Klant > Soorten publiek > leidt tot publiek > bouwt regel

#### Belangrijkste configuratiedetails

- Doelgroepen definiëren voor geschiktheid voor aanbiedingen (bijvoorbeeld &quot;Loyalty Gold Tier&quot;, &quot;High Value Customers&quot;, &quot;Trial Users&quot;)
- Definieer zo nodig het publiek voor onderdrukking (bijv. &quot;Onlangs ontvangen aanbod X&quot;)
- Voor optie B: Controleer of het publiek dat in aanmerking komt in aanmerking komt voor randevaluatie — vermijd vragen uit tijdreeksen en complexe aggregaties in segmentregelexpressies

#### Waar opties afwijken

**voor Optie A (E-mailbesluit):**
Evaluatie via batch of streaming is voldoende. Het publiek wordt geëvalueerd vóór of tijdens de uitvoering van de campagne. Complexe segmentregelexpressies inclusief op tijd gebaseerde voorwaarden en gebeurtenisaggregaties worden volledig ondersteund.

**voor Optie B (Echte Web/App):**
Edge-evaluatie is vereist. Het publiek moet eenvoudige attributencontroles of de voorwaarden van het segmentlidmaatschap gebruiken. De subsidiabiliteit van de rand van de test door de uitdrukking van de segmentregel te verifiëren kwalificeert voor randsegmentatie.

**voor Optie C (de Knoop van het Besluit van de Reis):**
Elke evaluatiemethode werkt afhankelijk van de toegangscriteria voor de reis. Als de reis op publiek-gebaseerd ingang gebruikt, past de methode van de publieksevaluatie de behoeften van de reis aan.

#### Experience League-documentatie

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Fase 3: Bepaling instellen

**functie van de Toepassing:** AJO: Beslissing

Dit is de kernfase waarin de catalogus van aanbiedingen, de toelatingsregels, de rangschikkingsstrategieën en het besluitvormingsbeleid worden opgebouwd. Deze fase leidt tot de configuratie van de besluitvormingsmotor die alle leveringsopties (A, B, C) deelt.

#### Besluit: Placement channel and content format

Bepaal waar aanbiedingen worden weergegeven en in welke indeling.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| E-mail (HTML) | Optie A — Inhoud aanbieden die als HTML is gerenderd in de e-mailhoofdtekst | Ondersteunt rijke opmaak; moet compatibel zijn met e-mailclients |
| E-mail (URL afbeelding) | Optie A — Aanbieding weergegeven als een gehoste afbeelding per e-mail | Eenvoudiger; afbeelding moet worden gehost en toegankelijk zijn; geen dynamische tekst |
| Web (HTML) | Optie B — Aanbieding die als HTML op een webpagina wordt weergegeven | Besturingselement voor volledige layout; ondersteunt interactieve elementen |
| Web/mobiel (JSON) | Optie B: gegevens aanbieden die als JSON worden geretourneerd voor aangepaste rendering | Maximale flexibiliteit; vereist front-end ontwikkeling om terug te geven |
| Op code gebaseerd (JSON) | Optie B — gegevens voor op code gebaseerde ervaringsoppervlakken aanbieden | Toepassingsbesturingselementen voor rendering; meest flexibel |

#### Besluit: beoordelingsstrategie

Bepaal hoe de beste aanbieding uit in aanmerking komende aanbiedingen moet worden geselecteerd.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Op prioriteit gebaseerd (handleiding) | Catalogi met kleine aanbiedingen; expliciete bedrijfsregels voor het bestellen van aanbiedingen | Eenvoudig te configureren; handmatig prioriteitswaarde per aanbieding toewijzen; deterministisch |
| Op basis van formule (aangepaste expressie) | De rangorde zou profielattributen (b.v., loyaliteitslaag, recentie) moeten overwegen | Flexibel; gebruikt profielgegevens om een rangschikkingsscore te berekenen; vereist het ontwerp van de de uitdrukkingsuitdrukking van de segmentregel |
| Op AI-schaal (automatische optimalisatie) | Catalogi met grote aanbiedingen; wil dat ML de selectie in de loop der tijd optimaliseert | Vereist minimaal 1.000 conversiegebeurtenissen voor modeltraining; leert van de prestatiegegevens van de aanbieding |

#### Beslissing: aanbod afstemmen

Bepaal of er limieten moeten zijn voor het aantal keren dat een aanbieding wordt getoond.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Per profiel | Voorkomen dat hetzelfde aanbod te vaak aan één klant wordt getoond | Vermijdt moeheid; tegenvertraging van een paar seconden in scenario&#39;s van de hoge productie |
| Globale lampvoet | Totale indrukken voor een aanbieding beperken tot alle profielen (bijv. beperkte voorraad) | De controles bieden levering aan; zodra maximum wordt bereikt, wordt het aanbod uitgesloten van besluiten |
| Geen uiteinde | Aanbiedingen zijn onbeperkt beschikbaar | Eenvoudigst; geschikt voor acties die altijd worden aangeboden |

**navigatie UI:** Componenten > Beslissingsbeheer > Plaatsingen/Regels/Aanbiedingen/Besluiten

#### Belangrijkste configuratiedetails

1. **creeer plaatsingen** - bepaal waar de aanbiedingen verschijnen door het kanaaltype en inhoudsformaat voor elke plaatsing te specificeren.
   - UI: Components > Decision Management > Placements
   - Eén plaatsing per kanaal/indeling maken (bijvoorbeeld &quot;Email Hero Banner - HTML&quot;, &quot;Web Homepage - JSON&quot;, &quot;Mobile App Card - JSON&quot;)

2. **bepaalt toelatingsregels** - creeer regels gebruikend de uitdrukkingen van de segmentregel die profielattributen of publiekslidmaatschap van verwijzingen voorzien.
   - UI: Components > Decision Management > Rules
   - Regels kunnen verwijzen naar het lidmaatschap van het publiek, profielkenmerken (loyaliteitslaag, abonnementstype), datumbeperkingen of contextafhankelijke gegevens

3. **creeer gepersonaliseerde aanbiedingen** — Bouw elke aanbieding met inhoudsvertegenwoordiging voor elke plaatsing, wijs geschiktheidsregels toe, plaats prioriteit, en vorm facultatieve aftappen.
   - UI: Componenten > Beslissingsbeheer > Aanbiedingen > Aanbod maken
   - Elke aanbieding heeft een inhoudsweergave per plaatsing nodig (bijvoorbeeld HTML voor e-mail, JSON voor web)
   - Wijs toelatingsregels toe om te controleren welke profielen elke aanbieding kunnen zien
   - Geldigheidsdatums voor aanbieding instellen (begin/einde) en optionele frequentietoewijzing instellen
   - Elke aanbieding goedkeuren om ervoor te zorgen dat deze in aanmerking komt voor een beslissing

4. **creeer fallback aanbiedingen** — Bouw een standaardaanbieding voor elke plaatsing die wordt getoond wanneer geen gepersonaliseerde aanbieding kwalificeert.
   - UI: Componenten > Beslissingsbeheer > Aanbiedingen > Terugvalaanbieding maken
   - Voor elke plaatsing die in de beslissing wordt gebruikt, moet een reservekopie zijn aangebracht

5. **creeer inzamelingsbepalende eigenschappen en inzamelingen** - organiseer aanbiedingen in inzamelingen gebruikend bepalingsmarkeringen.
   - UI: Components > Decision Management > Collection kwalificfiers
   - Groepsgerelateerde aanbiedingen (bv. &quot;Summer Promotions&quot;, &quot;Loyalty Rewards&quot;) voor gebruik in besluitvormingsgebieden

6. **creeer besluitvormingsbeleid** — Bind plaatsingen, inzamelingen, het rangschikken strategieën, en reserveaanbiedingen in uitvoerbare besluiten.
   - UI: Componenten > Beslissingsbeheer > Besluiten > Beslissingen maken
   - Elk beslissingsbereik koppelt een plaatsing aan een verzameling en geeft de waarderingsmethode op

#### Experience League-documentatie

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Plaatsingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Beslissingsregels maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Alternatieve aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Verzamelingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Verzamelingsaanduidingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-tags)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 4: Kanaal en oppervlak configureren

**functie van de Toepassing:** AJO: De Configuratie van het Kanaal

Deze fase vormt de kanaaloppervlakten waardoor de aanbiedingen zullen worden geleverd. De configuratie is afhankelijk van de implementatieoptie(s).

#### Besluit: kanaaltype

Bepaal welk overseinenkanaal het gebruiksgeval vereist.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| E-mail | Optie A of Optie C met e-maillevering | Vereist subdomain delegatie, IP pool, afzendermontages |
| Web | Optie B voor aflevering van het web | Vereist Web SDK- en datastreamconfiguratie |
| In-app | Optie B voor levering van mobiele apps | Vereist mobiele SDK en pushreferenties |
| Ervaring op basis van code | Optie B voor aangepaste renderoppervlakken | Het meest flexibel; de rendering van toepassingen wordt verwerkt |

#### Waar opties afwijken

**voor Optie A (E-mailbesluit):**
- UI: Beheer > Kanalen > Kanaaloppervlakken > Oppervlak maken (e-mail)
- Subdomein, IP-pool, naam/e-mail van afzender, antwoordinstellingen, abonnementsinstellingen configureren
- Verifieer SPF, DKIM, en DMARC verslagen voor het verzendende subdomain

**voor Optie B (Echte Web/App):**
- UI: Beheer > Kanalen > Kanaaloppervlakken > Oppervlak maken (Web of In-app)
- Voor web: het URL-patroon van het weboppervlak configureren
- Voor op code gebaseerde ervaringen: definieer het oppervlak-URI voor de toepassing
- Controleren of de gegevensstroom AJO-service heeft ingeschakeld

**voor Optie C (de Knoop van het Besluit van de Reis):**
- Kanaaloppervlakken configureren voor elk kanaal dat wordt gebruikt tijdens de rit (e-mail, push, SMS of web)
- Elke actie van het reisbericht vereist een overeenkomstige actieve kanaaloppervlakte

#### Experience League-documentatie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Instellingen van e-mailoppervlak](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Fase 5: Inhoud en levering configureren

**functie van de Toepassing:** AJO: De Authoring van het Bericht, AJO: De Uitvoering van de campagne

Deze fase ontwerpt de berichtmalplaatjes of ervaringsoppervlakken die de geselecteerde aanbieding tonen, dan vormt het leveringsmechanisme (campagne, reis, of code-gebaseerde ervaring).

#### Besluit: Inhoudsaanpak voor het aanbieden van voorstellen

Bepaal hoe de aanbiedingsinhoud in het bericht of de ervaring moet worden geïntegreerd.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Beslissingscomponent aanbieden in e-mail-Designer | Optie A — Aanbieding insluiten in e-mailsjabloon | Slepen en neerzetten; inhoud automatisch aanbieden op basis van beslissingsresultaat |
| Code-gebaseerde ervaring met besluitvormingsbeleid | Optie B — de toepassing wint en geeft aanbiedingsgegevens terug | Maximale controle over rendering; is front-end ontwikkeling vereist |
| Reisbericht met ingesloten beslissing | Optie C — Beslissingsknooppunten bieden inhoud aan reisbericht aan | De selectie en levering van de aanbieding worden georkestreerd binnen de transportstroom |

#### Beslissing: type campagne (alleen optie A)

Bepaal of dit een geplande marketing campagne of een API-getriggerde campagne is.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Geplande campagne | Eenmalige of terugkerende batch verzendt naar een bepaald publiek | Publiek dat tijdens uitvoeringstijd wordt geëvalueerd; vastgestelde datum/tijd of herhaling |
| API-gestuurde campagne | Gebeurtenisgestuurde of door het systeem geactiveerd verzenden naar opgegeven profielen | Profielen die zijn opgegeven in een triggerlading; ondersteunt maximaal 20 ontvangers per aanvraag |

#### Waar opties afwijken

**voor Optie A (E-mailbesluit):**

1. Het e-mailbericht schrijven met de e-mailtoepassing Designer
   - UI: Campagnes > Campagne maken > E-mail selecteren > Inhoud bewerken
   - Voeg een component voor de aanbiedingsbeslissing in de e-maillay-out in om de plaatsingszone te definiëren
   - Voeg personalisatietokens voor profiel-vlakke inhoud (naam, loyaliteitsrij) toe
   - De onderwerpregel en de voorheader configureren met optionele personalisatie
2. De campagne maken en configureren
   - UI: Campagnes > Campagne maken > Gepland of API-geactiveerd
   - Het doelpubliek binden en het kanaaloppervlak selecteren
   - Het uitvoeringsschema of de configuratie van de API-trigger instellen
   - De campagne evalueren en activeren

**voor Optie B (Echte Web/App):**

1. De op code gebaseerde ervaring of het webkanaal configureren
   - UI: Campagnes > Campagne maken > Code-gebaseerde ervaring (of Web)
   - Het beslissingsbeleid koppelen aan het ervaringsoppervlak
   - De renderindeling definiëren (JSON-reactie voor op code gebaseerd; visuele editor voor webkanaal)
2. Rendering op de client implementeren
   - Gebruik de Web SDK `sendEvent` -reactie om de geselecteerde aanbieding op te halen
   - De aanbiedingsinhoud renderen in de opgegeven plaatsing op de pagina
   - Afbeelding importeren en klikken op bijhouden

**voor Optie C (de Knoop van het Besluit van de Reis):**

1. De reis ontwerpen met een beslissingsknooppunt
   - UI: Reizen > Reis maken > Beslissingsknooppunt toevoegen
   - Vorm de besluitknoop om het besluitvormingsbeleid van Fase 3 aan te halen
2. Knoppen voor berichtactie toevoegen na de beslissing
   - E-mail-, push- of SMS-acties configureren die verwijzen naar de geselecteerde aanbieding
   - Wachtstappen, voorwaarden of vertakking toevoegen op basis van de service van de aanbieding
3. De reis publiceren

#### Experience League-documentatie

- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Fase 6: Testen en valideren

**functie van de Toepassing:** AJO: Beslissing, AJO: De Authoring van het Bericht

In deze fase wordt gecontroleerd of de beslissingsengine de juiste aanbiedingen voor testprofielen retourneert en of de inhoud van de aanbieding op de juiste wijze wordt weergegeven in elk leveringskanaal.

#### Bepalingslogica testen

Gebruik testprofielen met bekende kenmerken om te controleren of de juiste aanbiedingen zijn geselecteerd op basis van geschiktheid en rangschikking.

- Testprofielen maken die voldoen aan verschillende geschiktheidscriteria (bijvoorbeeld Gold-laag, Silver-laag, proefgebruiker)
- Controleer of elk testprofiel het verwachte aanbod ontvangt
- Controleren of profielen die voldoen aan geen subsidiabiliteitsregels, een fallback-aanbieding ontvangen

#### Rendering van inhoud testen

Bekijk de inhoud van de aanbieding in elk leveringskanaal.

- Voor optie A: gebruik de e-mailvoorvertoning met testprofielen om te controleren of de inhoud van de aanbieding correct wordt weergegeven
- Voor optie B: test de Edge-beslissingsrespons in een testomgeving
- Voor Optie C: De wijze van de de reistest van het gebruik om de beslissingsknoop correct te verifiëren selecteert

#### Tekstspatiëring valideren

Bevestig dat er afbeeldingen worden bijgehouden die afbeeldingen kunnen weergeven, klikken en conversies.

- Controleren of er interactiegebeurtenissen voor aanbiedingen worden weergegeven in de volgende gegevenssets
- Toewijzing bevestigen tussen aanbiedingsindrukken en downstreamomzettingen

#### Experience League-documentatie

- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [E-mailproefdrukken verzenden](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/proofs)

### Fase 7: rapportage en prestatiebewaking configureren

**functie van de Toepassing:** AJO: Rapportering &amp; de Analyse van Prestaties

In deze fase worden de rapportage zodanig ingesteld dat de distributie van aanbiedingen, acceptatiecijfers, conversie-effecten en terugvalpercentages worden bijgehouden. In deze fase worden zowel de eigen AJO-rapporten als de op CJA gebaseerde analyse van meerdere kanalen behandeld.

#### Besluit: Rapportagemethode

Bepaal welke rapporteringshulpmiddelen nodig zijn voor de analyse van de aanbiedingsprestaties.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen systeemeigen AJO-rapporten | Operationeel toezicht op individuele campagnes of reizen | Snelle toegang; ingebouwde maatstaven voor levering en betrokkenheid; beperkte analyse van meerdere entiteiten |
| CJA-werkruimteanalyse | Interkanaalse aanbiedingen zijn effectief, inkomstentoewijzing, funnel-analyse | Vereist CJA-verbinding en gegevensweergave; meer analytische mogelijkheden |
| Zowel AJO als CJA | Volledige operationele en analytische dekking | Aanbevolen voor productieimplementaties; AJO voor realtime bewaking, CJA voor strategische analyse |

#### Belangrijkste configuratiedetails

1. **inheemse rapportering van AJO** — de campagne of de reisprestaties van de monitor gebruikend ingebouwde rapporten.
   - UI: Campagnes > Select campagne > All time report (of Live-rapport)
   - Aanbiedingsspecifieke maatstaven bekijken: indrukken per aanbieding, doorkliktarief per aanbieding, terugvalpercentage
   - Bezorging voor monitor funnel: Gericht > Verzonden > Geleverd > Openen > Klikken

2. **de analyse van CJA (geadviseerd)** — Bouw dwars-kanaal prestaties dashboards aan.
   - Een CJA-verbinding configureren, inclusief AJO-gegevens voor interactie
   - Een gegevensweergave maken met de aanbiedingsspecifieke afmetingen (naam van aanbieding, plaatsing, beslissing) en metriek (afbeeldingen, klikken, conversies)
   - De werkruimteanalyse van de bouw voor: de distributie van de aanbieding, het tarief van de acceptatie per segment, opbrengsteffect, dwars-kanaalaanbiedingen consistentie

#### Experience League-documentatie

- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

## Implementatieoverwegingen

In deze sectie worden onder meer de begeleiding, gemeenschappelijke valkuilen, beste praktijken en afwegingsbesluiten voor het uitvoeren van beslissingen over aanbiedingen besproken.

### Guardrails en limieten

Houd rekening met de volgende platformhulplijnen en -beperkingen wanneer u de implementatie plant.

- Maximum van 10.000 goedgekeurde gepersonaliseerde aanbiedingen per zandbak - [ de gidsen van het Beheer van het Besluit ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximaal 30 stages per besluit
- Maximaal 30 verzamelingsbereiken per beslissingsverzoek
- Voor AI-classificatiemodellen is een minimum van 1.000 conversieevenementen vereist voor training
- Aanbiedings het begrenzen tellers kunnen een vertraging van tot een paar seconden in hoge productiescenario&#39;s hebben
- Edge-beslissingen zijn beperkt tot profielkenmerken die beschikbaar zijn in de winkel met randprofielen
- Maximum van 4.000 segmentdefinities per zandbak - [ de gidsen van het Platform ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Er kan slechts één samenvoegbeleid actief zijn op Edge per sandbox
- Maximaal 500 actieve live campagnes per sandbox
- Grenswaarde voor het aantal reizen: 5.000 profielen per seconde
- Maximaal 10 kanaaloppervlakken per kanaaltype per sandbox

### Veelvoorkomende valkuilen

Vermijd deze vaak voorkomende problemen tijdens de implementatie.

- **het Besluit keert altijd terugvalaanbieding terug:** dit typisch betekent gepersonaliseerde aanbiedingen niet worden goedgekeurd, buiten hun waaier van de geldigheidsdatum zijn, of de toelatingsregels passen niet de attributen van het testprofiel aan. Verifieer elke voorwaarde: goedkeuringsstatus, datumwaaier, en de uitdrukkingsnauwkeurigheid van de segmentregel. Controleer ook of de plafondlimiet niet is bereikt.
- **Aanbieding die niet in inzameling verschijnt:** verzeker de aanbieding met het correcte inzamelingsbepaler is geëtiketteerd en dat de gelijken van de inzamelingsfilter. Aanbiedingen moeten gelabeld en goedgekeurd zijn om in een op verzameling gebaseerd beslissingsbereik te worden weergegeven.
- **het Rangschikken formule niet toegepast:** verifieer dat de formule syntactisch geldig is en verwijzingen toegankelijke profielattributen. Formulatiefouten worden zonder meer teruggezet naar op prioriteit gebaseerde rangschikking zonder zichtbare fout.
- **de levering van Edge keert lege verpersoonlijking terug:** zorg de datastream wordt gevormd met de [!DNL Adobe Journey Optimizer] toegelaten dienst en dat het besluitvormingswerkingsgebied correct geformatteerd is. Controleer of het arceringsactieve samenvoegbeleid bestaat.
- **Inconsistente aanbiedingen over kanalen:** als het afzonderlijke besluitvormingsbeleid per kanaal wordt gebruikt, kan het zelfde profiel verschillende aanbiedingen ontvangen. Gebruik één enkel besluitvormingsbeleid over kanalen voor consistentie, of keur opzettelijke divergentie op kanaal-specifieke plaatsingen toe.
- **inhoud van de aanbieding die niet in e-mail teruggeeft:** verifieer de aanbieding een inhoudsvertegenwoordiging heeft die het formaat van de e-mailplaatsing (HTML of beeld URL) aanpast. Ontbrekende weergaven resulteren in lege plaatsingszones.

### Aanbevolen procedures

Volg deze aanbevelingen voor een succesvolle implementatie van het Aanbiedingsbesluit.

- **Begin met een kleine aanbiedingscatalogus en herhaling** - begin met 5-10 aanbiedingen en breid uit aangezien het beslissingskader wordt bevestigd. Dit vereenvoudigt het oplossen van problemen en verzekert geschiktheidsregels correct werken alvorens te schrapen.
- **de inzamelingsbepalers van het Gebruik strategisch** - de aanbiedingen van de markering door categorie (b.v., &quot;Aankoop,&quot;Behoud,&quot;Upsell&quot;) om flexibele op inzameling-gebaseerde besluitvormingswerkingsgebieden toe te laten die over campagnes en reizen kunnen worden opnieuw gebruikt.
- **creeer altijd betekenisvolle reserveaanbiedingen** — De aanbiedingen van de reserve zijn niet enkel een veiligheidsnet; zij zijn de standaardervaring voor profielen die geen toelatingsregel aanpassen. Investeer in fallback-inhoud die zelfs zonder personalisatie waarde biedt.
- **de toelatingsregels van het Ontwerp om waar mogelijk elkaar uit te sluiten** - wanneer de veelvoudige aanbiedingen overlappende geschiktheid hebben, wordt de rangschikkende strategie kritiek. Indien de zakelijke vereisten een specifieke aanbieding voor een bepaald segment voorschrijven, sluit de toelatingsregels dan wederzijds uit in plaats van alleen op rangschikking te vertrouwen.
- **Test met rand-representatieve profielen voor Optie B** - de profielen van Edge bevatten een ondergroep van de attributen van het hubprofiel. Testen met profielen met randkenmerken om te controleren of geschiktheid correct wordt beoordeeld in de productie.
- **de fallbacktarieven van de Monitor als gezondheid metrisch** - een hoog fallback tarief (boven 20-30%) wijst erop dat de aanbiedingscatalogus genoeg klantensegmenten niet behandelt. Breid de aanbiedingencatalogus uit of verruim de subsidiabiliteitsregels.
- **het besluitvormingsbeleid van de Versie eerder dan het uitgeven levende degenen** - creeer een nieuwe versie van het besluitvormingsbeleid eerder dan het wijzigen van actieve. Dit voorkomt verstoring van live campagnes en maakt een A/B-vergelijking van besluitvormingsstrategieën mogelijk.

### Handelsbesluiten

Houd rekening met de volgende compromissen wanneer u beslissingen neemt op het gebied van architectuur en configuratie.

#### Geschiktheidsbepaling versus dekking van aanbieding

De strenge toelatingsregels zorgen ervoor dat elke aanbieding alleen de meest relevante profielen bereikt, maar kunnen resulteren in hoge terugvalpercentages wanneer de profielen niet overeenkomen met een aanbod. De brede toelatingsregels maximaliseren aanbiedingsdekking maar verminderen personaliseringsprecisie.

- **de dichte toelatingsgunsten:** Hogere goedkeuringspercentages, betere verpersoonlijking, lagere aanbiedingsvermoeidheid
- **brede geschiktheidsgunsten:** Lagere fallback tarieven, ontvangen meer profielen gepersonaliseerde aanbiedingen, eenvoudiger regelbeheer
- **Aanbeveling:** begin met bredere geschiktheidsregels en draai hen die op prestatiesgegevens worden gebaseerd aan. Houd de terugvalpercentages en acceptatiecijfers in de gaten om de juiste balans te vinden. Gebruik waarderingsstrategieën om onderscheid te maken tussen breed in aanmerking komende aanbiedingen.

#### Op basis van prioriteit versus op AI gerangschikte rangschikking

Rangschikking op basis van prioriteit geeft de onderneming volledige controle over welke aanbiedingen worden getoond, terwijl de op AI-rangschikking optimaliseert voor omzetting maar menselijke controle over aanbiedingsselectie vermindert.

- **op prioriteit-gebaseerde voorkeur:** Bedrijfs controle, voorspelbaarheid, geen vereiste van opleidingsgegevens, directe plaatsing
- **AI-gerangschikte voorkeur:** de optimalisering van de Omzetting, ontdekking van onverwachte patronen, automatische aanpassing aan veranderend klantengedrag
- **Aanbeveling:** Op prioriteit-gebaseerde rangschikking van het gebruik voor aanvankelijke lanceringen en regelgevende-gevoelige aanbiedingen waar de bedrijfscontrole van het grootste belang is. De overgang naar AI-gerangschikt voor gebruik met hoge volumes en optimale prestaties zodra er voldoende conversiegegevens (1.000+ gebeurtenissen) beschikbaar zijn.

#### Beleid met één keuze tegenover beleid met één kanaal

Eén enkel beslissingsbeleid zorgt voor consistentie op alle kanalen, maar beperkt optimalisatie per kanaal. Het beleid per kanaal staat kanaal-specifieke rangschikking en geschiktheid toe maar risico inconsistente klantenervaringen.

- **Enig beleid begunstigt:** de consistentie van het Kanaal, eenvoudiger beheer, verenigde rapportering
- **per-kanaalbeleid gunt:** kanaal-geoptimaliseerde rangschikking, kanaal-specifieke geschiktheid (b.v., Web-slechts aanbiedingen), onafhankelijke herhaling
- **Aanbeveling:** begin met één enkel besluitvormingsbeleid voor dwars-kanaalconsistentie. Creeer per-kanaalbeleid slechts wanneer de bedrijfsvereisten kanaalspecifieke aanbiedingsstrategieën (b.v., Web-exclusieve flitsverkoop) vragen.

#### De beslissing van de hub (Optie A/C) vs. randbesluit (Optie B)

Het besluit van de hub heeft toegang tot het volledige profiel maar werkt bij verzendtijd. Edge-beslissingen worden in real-time uitgevoerd met een latentie van subseconden, maar zijn beperkt tot kenmerken van randbeschikbare profielen.

- **de beslissingsvoorkeur van de Hub:** Toegang tot volledige profielgegevens, complexe toelatingsregels, de volumes van de partijcampagne
- **de besluiten van Edge begunstigen:** context In real time, in-session verpersoonlijking, sub-tweede reactie
- **Aanbeveling:** hubbesluit van het gebruik voor uitgaande kanalen (e-mail, duw) waar de volledige profielgegevens relevantie verbeteren. Gebruik randbeslissingen voor binnenkomende kanalen (web, app) waar real-time respons van essentieel belang is. Ervoor zorgen dat randgebruiksregels alleen randkenmerken bevatten.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie over de componenten die in dit gebruikspatroon worden gebruikt.

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

### Levering aanbieden

- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Aanbiedingen leveren met de Edge-API voor besluitvorming](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Aanbiedingen leveren met de API voor besluitvorming](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/decisioning-api)

### Kanaalconfiguratie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Instellingen van e-mailoppervlak](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Authoring en personalisatie van berichten

- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Campagnes en reizen

- [Aan de slag met campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)

### Inhoud testen

- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Splitsen en segmenteren

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Profiel en identiteit

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [AI-overzicht van klant](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Gegevensmodellering en gegevensverzameling

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)

### Rapportage en analyse

- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Beheer van gegevens en levenscyclus

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Overzicht van labels voor gegevensgebruik](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Overzicht van geavanceerd gegevenslevenscyclusbeheer](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Toestemming in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Beveiligingsmechanismen

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)

### Tutorials

- [De API voor het beheer van beslissingen wordt gestart](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/getting-started)
