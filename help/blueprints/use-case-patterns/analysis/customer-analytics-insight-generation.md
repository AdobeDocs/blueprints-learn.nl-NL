---
title: Klantenanalyse en Insight Generation
description: Leer hoe u werkruimten voor kanaalanalyse, berekende metriek en dashboards kunt maken voor gedrags- en prestatieanalyse.
solution: Customer Journey Analytics, Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '8947'
ht-degree: 0%

---


# Klantenanalyse en insight-generatie

Deze handleiding bevat een volledige implementatiereferentie voor klantanalyse en insight-generatie. Hierin wordt beschreven hoe u [!DNL Adobe Experience Platform] -gegevenssets met [!DNL Customer Journey Analytics] kunt verbinden, gegevensweergaven kunt configureren, werkruimten voor vrije-vormanalyse kunt maken, berekende metriek kunt maken, dashboards en mobiele scorecards kunt publiceren en eventueel door CJA gedefinieerde soorten publiek kunt publiceren naar [!DNL Adobe Experience Platform] voor activering.

Het wordt ontworpen voor oplossingsarchitecten, marketing technologen, en implementatietechnici die alle levensvatbare implementatiepaden, de compromissen tussen hen, en de configuratiebesluiten moeten begrijpen die bij elke fase worden vereist.

In tegenstelling tot de andere patronen in de taxonomie die zich richten op activering en betrokkenheid (het verzenden van berichten, het personaliseren van inhoud, het activeren van het publiek), concentreert dit patroon zich op begrip — het analyseren van klantengedrag, het meten van campagneprestaties, het identificeren van tendensen, en het produceren van inzichten die strategie en optimaliseringsbesluiten informeren. Het is het meest meestal samengestelde patroon en paren met bijna elk activerings- of personalisatiepatroon.

## Hoofdlettergebruik

De organisaties moeten begrijpen hoe de klanten zich over kanalen gedragen, hoe de campagnes presteren, waar de klanten in hun reizen wegvallen, welke inhoud resoneert, en hoe de verschillende segmenten in tijd behouden. Analyses van klanten en insight-generatie voorzien in deze behoefte door de uitgebreide gegevens over meerdere kanalen in [!DNL Adobe Experience Platform] aan [!DNL Customer Journey Analytics] te koppelen, waar analisten vrije werkruimten kunnen bouwen, aangepaste metriek kunnen maken, attributiemodellen kunnen configureren en dashboards kunnen publiceren voor gebruik door belanghebbenden.

Het patroon dient voor meerdere doelgroepen: marketinganalisten die diepgaande verkennende analyse nodig hebben, campagnemanagers die prestatiedashboards nodig hebben, productmanagers die inzicht in betrokkenheid en behoud nodig hebben, en managers die KPI-scorecards in één oogopslag nodig hebben. De implementatieaanpak is afhankelijk van de primaire analytische focus: meting van de campagneresultaten, analyse van de reis over het kanaal, activering van het publiek door analyse of inzichten in producten met instructies.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

**verbetert analyses &amp; het melden**

Verbeter rapporteringsmogelijkheden voor snellere, actievere marketing inzicht door verenigde dashboards en zelfbedieningshulpmiddelen.

- **KPIs:** Efficiëntie, Productiviteit

Zie [ Verbeteren Analytics &amp; het Melden ](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md) voor meer informatie over dit bedrijfsdoel.

**laat gegeven-gedreven besluitvorming** toe

De teams van de macht met zelfbedienings analyses, klanteninzicht in real time, en op AI-Gebaseerde voorspellingen om strategie te begeleiden.

- **KPIs:** Efficiëntie, Productiviteit

Zie [ Gegevens-Gedreven Beslissing het Maken ](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md) voor meer informatie over dit bedrijfsdoel toelaten.

**verbeter marketing attributie**

Nauwkeurige meting van het effect van marketing touchpoints, kanalen, en campagnes op omzettings en opbrengstresultaten.

- **KPIs:** Efficiëntie, Incrementele Inkomsten

Zie [ Verbeteren de Attributie van de Marketing ](/help/blueprints/business-objectives/analytics-insights/improve-marketing-attribution.md) voor meer informatie over dit bedrijfsdoel.

**optimaliseer marketing uitgaven &amp; ROI**

Optimaliseer de toewijzing van marketingbudgetten door te begrijpen welke kanalen en campagnes het hoogste rendement opleveren.

- **KPIs:** Efficiëntie, Incrementele Inkomsten

Zie [ op de markt gebrachte uitgaven &amp; ROI ](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md) voor meer informatie over dit bedrijfsdoel optimaliseren.

## Voorbeelden van tactische gebruiksgevallen

Hieronder volgen voorbeelden van gevallen van tactisch gebruik die met dit patroon kunnen worden geïmplementeerd.

- Het dashboard voor de prestaties van de campagne — leveringsmetriek, betrokkenheidstarieven, conversie, en opbrengstattributie over e-mail, SMS, duw, en betaalde media campagnes
- Analyse van de neerslag van de reis van de klant — identificeer waar de klanten in aankoop, registratie of onboarding trechters wegvallen
- Cohortretentieanalyse — meet hoe sterk verschillende acquisitiecohorten in weken, maanden en kwarten behouden blijven
- Kanaalattribuutmodellering — vergelijk first-touch, last-touch, lineaire en time-remising attributie om te begrijpen welke kanalen conversies aansturen
- Analyse van de prestaties van de inhoud — bepaal welke inhoud het meest op segment, kanaal, en levenscyclusstadium resoneert
- Analyse van het gebruik en de goedkeuring van het product — spoor eigenschapadoptie, betrokkenheidsfrequentie, en gebruikerstoename
- Analyse van de levenscyclusfase van de klant — klanten segmenteren en analyseren per levenscyclusfase (nieuw, actief, risicovol, vervallen)
- Dashboard voor optimalisatie van marketingmix — vergelijk kanaalinvesteringen met inkomstenbijdrage
- Scoring en rapportage van betrokkenheid tussen kanalen — samengestelde betrokkenheidsscores maken van web-, app-, e-mail- en campagneinteracties

## Kernprestatie-indicatoren

De volgende KPIs helpt het succes van dit gebruiks gevalpatroon meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Efficiëntie | Minder tijd-aan-insight en manuele rapporteringsinspanning | De tijd van de analyst van het spoor besteedde het bouwen rapporten vóór en na de implementatie van CJA |
| Productiviteit | Aantal zelfbedieningsanalyses die door zakelijke gebruikers zijn gemaakt | Workspace-projectontwerp en dashboardgebruik bewaken |
| Incrementele inkomsten | Inkomsten die worden toegeschreven aan door inzichten gestuurde optimalisatiebesluiten | De opbrengst van de maatregel van campagnes die op CJA analyse worden geoptimaliseerd |
| Omrekeningskoers | Funnel-voltooiingstarieven voor belangrijke klantreizen | De fallouttarieven van het spoor bij elke wegstap gebruikend CJA fallout visualisatie |
| Betrokkenheid | Diepte en frequentie van klantinteractie tussen kanalen | Berekende maatstaven maken voor servicescortering in CJA |
| Bewaren | Rendementspercentages van klanten over bepaalde tijdsperiodes | CJA-cohortanalyse gebruiken om retentiecurven te meten |

## Hoofdletterpatroon gebruiken

**Analytics van de Klant &amp; generatie insight**

Bouw de werkruimten van de dwars-kanaalanalyse, gegevens verwerkte metriek, en dashboards om klantengedrag en campagneprestaties te begrijpen.

**de ketting van de Functie:** Verbinding van Gegevens > de Configuratie van de Mening van Gegevens > de Analyse van Workspace > Berekende Metrische Creatie > het Publiceren van het Dashboard

Zie de [ opties van de Implementatie ](#implementation-options) sectie voor samenstellingsbegeleiding.

## Applicaties

In dit gebruikspatroon worden de volgende toepassingen gebruikt.

- **[!DNL Customer Journey Analytics](CJA)** — Verbindingen, gegevensmeningen, werkruimteanalyse, geleide analyse, gegevens gegevens gegevens gegevens gegevens verwerken, dashboards, publiek het publiceren, en inhoudanalyse
- **[!DNL Adobe Experience Platform](AEP)** — Het meer van gegevens, datasets, XDM schema&#39;s, profiel en gebeurtenisgegevens die de verbindingen van CJA van de input voorzien

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | CJA-productprofiel dat is ingericht voor het maken van werkruimten en toegangsrechten voor gegevensweergave. AEP-gegevenssets toegankelijk voor de CJA-verbinding. Gebruikers die zijn toegewezen aan de juiste CJA-rollen. | [ overzicht van het Toegangsbeheer ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | XDM-schema&#39;s en -gegevenssets die met CJA worden verbonden, moeten in AEP bestaan. Het ontwerp van het schema beïnvloedt direct welke afmetingen en metriek in de gegevensmeningen van CJA beschikbaar zijn. Gebeurtenisschema&#39;s hebben tijdstempelvelden nodig; opzoekschema&#39;s hebben sleutelvelden nodig. | [ XDM overzicht van het Systeem ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Gegevensbronnen en -verzameling | Vereist | Gegevens moeten in AEP datasets stromen — webgebeurtenissen via Web SDK, app-gebeurtenissen via Mobile SDK, AJO-campagnegebeurtenissen, CRM-gegevens via bronconnectors. De rijkdom van de analyse hangt af van de omvang van de verzamelde gegevens. | [ Bronoverzicht ](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identiteit en profielconfiguratie | Vereist | De configuratie van de identiteitskaart van de persoon in de verbinding van CJA bepaalt hoe de gebeurtenissen over datasets worden vastgemaakt. Identiteitsverstrengeling tussen apparaten in AEP verbetert de mogelijkheid van CJA om volledige klantentwitten te bouwen. Naamruimte moet worden geconfigureerd voor het veld Person-id. | [ Overzicht van de Dienst van de Identiteit ](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Auditiedefinitie en segmentatie | Niet van toepassing | CJA bouwt zijn eigen filters en publiek binnen de analytische context. RT-CDP-publiek is geen voorwaarde, maar CJA kan een publiek terugsturen naar AEP via publiekspublicaties (Option C). | [ overzicht van de Dienst van de Segmentatie ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | AEP berekende kenmerken kunnen de datasets verrijken die met CJA zijn verbonden, waardoor extra dimensies en meetgegevens voor analyse worden verschaft (bijvoorbeeld het aantal levenslange aankopen, het aantal dagen sinds de laatste activiteit). Deze aggregaties op profielniveau worden beschikbaar als afmetingen in CJA-gegevensweergaven. | [ Berekende attributen overzicht ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Het beleid voor het bewaren van gegevenssets is van invloed op de historische gegevens die beschikbaar zijn in CJA. Langdurige retentie is doorgaans gewenst voor analyses om vergelijkingen van jaar tot jaar en trendanalyse op lange termijn mogelijk te maken. Vorm dataset TTLs om adequate historische diepte te te verzekeren. | [ het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens ](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | Regelgevingslabels op gevoelige velden kunnen de weergave van CJA-gegevensweergaven beperken. Als PII of gevoelige gegevens zijn opgenomen in de CJA-verbinding, zorgen labels voor gegevensbeheer ervoor dat toegang aan de voorschriften voldoet en dat blootstelling door onbevoegden in gedeelde dashboards wordt voorkomen. | [ Overzicht van het beheer van Gegevens ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Bewaking en waarneming | Aanbevolen | De gezondheid van de verbinding van CJA en gegevensversheid zouden moeten worden gecontroleerd. Configureer waarschuwingen voor fouten met brongegevensstroom en inname-problemen om ervoor te zorgen dat de gegevensinvoer van CJA betrouwbaar en actueel is. | [ overzicht van de Inzichten van de Waarnemelijkheid ](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | Dit is de uitvoering van de rapportage en analyse. Als een referentieplan voor een ander patroon S5 bevat, gebruikt u dit klantanalyse- en insight-generatieplan voor de analytische implementatie. | [ overzicht van CJA ](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de catalogus van de toepassingsfunctie uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Customer Journey Analytics] (CJA)

In de volgende tabel worden de CJA-toepassingsfuncties weergegeven die in dit patroon worden gebruikt.

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Gegevensverbinding | Fase 1: Gegevensverbinding | Bind de datasets van AEP aan een verbinding van CJA voor kanaalanalyse, vormend datasettypes en identiteitskaart van de Persoon voor dwars-dataset het stitching |
| Configuratie gegevensweergave | Fase 2: Configuratie gegevensweergave | Definieer afmetingen, metriek, attributiemodellen, persistentie-instellingen, sessieparameters en afgeleide velden die het analytische perspectief vormen |
| Workspace-analyse | Fase 3: Analyse en metrische creatie | Maak vrije-vormanalyseprojecten met lijsten, visualisaties, filters, annotaties, en afmetingsonderverdelingen (Opties A, B, C) |
| Begeleide analyse | Fase 3: Analyse en metrische creatie | Gestructureerde workflows met instructies gebruiken voor funnel, trends, retentie, groei van gebruikers en analyse van de betrokkenheidsfrequentie (Option D) |
| Berekend metrisch ontwerp | Fase 3: Analyse en metrische creatie | Definieer berekende metriek met formules, filters, en functies voor herbruikbare PKIs zoals omzettingspercentage, betrokkenheidsscore, en opbrengst per bezoek |
| Publiceren op dashboard en scorebord | Fase 4: Publiceren van dashboard | Interactieve dashboards en mobiele scorecards maken en delen voor rapportage door belanghebbenden |
| Publiek publiceren | Fase 5: Publiek publiceren (alleen Optie C) | CJA-gedefinieerde soorten publiek terugsturen naar AEP Real-Time Klantprofiel voor downstreamactivering |
| Content-analytics | Fase 3: Analyse en metrische creatie | De trends, anomalieën en vermoeidheid van de inhoudsprestaties in digitale eigenschappen analyseren (wanneer de inhoudsanalyse de focus heeft) |

### [!DNL Adobe Experience Platform] (AEP)

In de volgende tabel worden de AEP-toepassingsfuncties weergegeven die in dit patroon worden gebruikt.

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Datameer en datasets | Vereiste (F2, F3) | De brongebeurtenis, het profiel en de opzoekgegevenssets opgeven die de CJA-verbinding voeden |
| Identiteitsservice | Vereiste (F4) | Identiteitsnaamruimteconfiguratie opgeven voor persoonsidentiteitsidentiteitskaart die zich in datasets in de verbinding van CJA vastmaakt |

## Vereisten

Aan de volgende voorwaarden moet worden voldaan voordat u dit gebruikspatroon implementeert.

- CJA-productrechten zijn voorbehouden voor de organisatie
- CJA-productprofielen zijn geconfigureerd met de juiste gebruikerstoegang (werkruimte maken, toegang tot gegevensweergave)
- De AEP-sandbox bevat de doeldatasets met gegevensstroom (webgebeurtenissen, toepassingsgebeurtenissen, campagnegegevens, CRM-records)
- XDM-schema&#39;s worden gedefinieerd voor alle brongegevenssets met de juiste veldgroepen
- Het veld Persoon-id wordt geïdentificeerd en is consistent beschikbaar in alle gegevenssets die worden verbonden
- Identiteitsnaamruimten worden in AEP geconfigureerd voor de persoon-id die wordt gebruikt in CJA-verbindingsstitching
- De vereisten van de belanghebbenden worden gedocumenteerd — welke KPI&#39;s, welke doelgroepen dashboards zullen gebruiken, welk detailniveau
- Voor mobiele scorecards: belanghebbenden hebben de mobiele app [!DNL Adobe Analytics] dashboards geïnstalleerd
- Voor optie C (Publiek publiceren): AEP Real-Time Klantprofiel is ingeschakeld in de doelsandbox
- Voor optie D (Analyse met instructies): CJA SKU bevat mogelijkheden voor analyse met instructies

## Implementatieopties

In deze sectie worden de beschikbare implementatieopties voor dit gebruikspatroon beschreven.

### Optie A: Analyse van de campagneprestaties

**Best voor:** het meten en optimaliseren campagne en reisdoeltreffendheid — e-mailcampagnedashboards, reisfunnel analyse, kanaalprestatiesvergelijking, en marketing ROI rapportering.

**hoe het werkt:**

Met deze optie verbindt u de campagne- en reisgegevenssets van AJO met CJA, configureert u gegevensweergaven met maatstaven voor levering en betrokkenheid (verzenden, leveringen, openen, klikken, stuiteringen, afmelden), maakt u prestatiedashboards van de campagne en publiceert u scorecards voor marketingbelanghebbenden. De nadruk ligt op het begrijpen van hoe marketingcampagnes op verschillende kanalen en in de loop van de tijd werken.

De gegevensmening wordt gevormd met campagne-specifieke afmetingen (campagnenaam, reisnaam, kanaaltype, berichtvariant) en leveringsmetriek. Berekende metriek worden gecreeerd voor afgeleide maatregelen zoals open tarief, klikthrough tarief, omzettingspercentage, en opbrengst per bericht. De dashboards presenteren deze KPIs met vergelijkingsperiodes voor trendanalyse.

**Zeer belangrijke overwegingen:**

- Vereist gegevenssets voor AJO-campagne en -reisgebeurtenissen in AEP
- Attributiemodellen dienen overeen te stemmen met de campagnemetingfilosofie van de organisatie
- Overweeg om zowel eigen AJO-rapporten (voor maatstaven voor operationele levering) als CJA (voor zakelijke gevolgen voor meerdere kanalen) op te nemen

**Voordelen:**

- Speciaal ontworpen voor het meten en optimaliseren van campagnes
- Maakt vergelijking tussen verschillende campagnes en analyse van kanaalmix mogelijk
- De gegevens op basis van berekeningen bieden gestandaardiseerde KPI-definities voor alle campagnes
- Mobiele scorecards bieden in één oogopslag prestaties voor marketingleiders

**Beperkingen:**

- Beperkt tot campagne- en reisgegevens; biedt geen volledige reiscontext voor klanten
- Omvat niet het wegschilderen, het vallen of de analyse van de cohort
- Het attribuut is scoped aan campagneaanraakpunten eerder dan de volledige klantenreis

**Experience League:**

- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Optie B: Analyse van de reis van de klant

**Best voor:** Begrijpend dwars-kanaal klantenreizen — fallout analyse, weganalyse, cohortbehoud, attributiemodellering, en de analyse van het levenscyclusstadium over Web, app, e-mail, CRM, en off-line touchpoints.

**hoe het werkt:**

Deze optie verbindt veelvoudige datasets van AEP (Webgebeurtenissen, app gebeurtenissen, de gegevens van CRM, campagneinteractie, transactieregisters) om een verenigde dwars-kanaalmening van de klantenreis te bouwen. De gegevensmening wordt gevormd met afmetingen en metriek die alle kanalen overspannen. De stroom, de fallout, de cohort, en attributie visualisaties van CJA worden gebruikt om te analyseren hoe de klanten zich door reizen bewegen, waar zij weggaan, hoe de verschillende segmenten behouden, en welke kanalen krediet voor omzettingen verdienen.

Dit is de meest uitgebreide analytische optie, die diepe insight in de ervaring van de klant van begin tot eind verstrekt. Het is ook het meest complex om uit te voeren, die de zorgvuldige configuratie van identiteitskaart van de Persoon voor dwars-dataset het stitching en het doordachte ontwerp van de gegevensmening vereisen om de juiste afmetingen en metriek bloot te stellen.

**Zeer belangrijke overwegingen:**

- Vereist consistente persoon-id voor alle verbonden datasets voor een nauwkeurige kanaalanalyse
- Het schemaontwerp in AEP is rechtstreeks van invloed op de kwaliteit en diepte van de CJA-analyse
- Meer datasets in verbinding betekent rijkere analyse maar langere backfill tijden
- Voor kenmerkmodellering zijn duidelijke definities van conversiegebeurtenissen vereist

**Voordelen:**

- Volledige zichtbaarheid van de reis van klanten over het hele kanaal
- Volledige suite met CJA-visualisaties: flow, fallout, cohort, attributie, vrije-vormtabellen
- Maakt detectie van inzichten mogelijk die onzichtbaar zijn in single-channel rapportage
- Ondersteunt complexe analytische vragen over het gedrag en de levenscyclus van klanten

**Beperkingen:**

- Hogere implementaticomplexiteit door verbindingen met meerdere gegevenssets en het stitching via meerdere kanalen
- Vereist meer voorplanning voor de configuratie van de gegevensmening en afgeleide gebieden
- De backfill voor grote multi-datasetverbindingen kan dagen vergen
- De kwaliteit van de analyse hangt af van de volledigheid en consistentie van de onderliggende gegevens

**Experience League:**

- [Overzicht van verbindingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Stroomvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Uitvalvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohortingtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Kenmerk, deelvenster](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)

### Optie C: Analyse met publiek publiceren

**Best voor:** Analyse-gedreven activering — ontdek interessante segmenten door de analyse van CJA, dan publiceer hen terug naar AEP voor activering via RT-CDP bestemmingen, de campagnes van AJO, of de reizen van AJO.

**hoe het werkt:**

Met deze optie wordt Option A of Option B uitgebreid met publiekspublicaties vanuit CJA. Analysten bouwen segmenten in CJA met behulp van kanaaloverschrijdende gedragsgegevens en de volledige analytische kracht van CJA-filters, en publiceren die soorten publiek naar AEP Real-Time Customer Profile voor downstreamactivering. Dit overbruggt de kloof tussen insight en action — segmenten die tijdens verkennende analyses zijn ontdekt, worden een actief publiek zonder handmatige recreatie in AEP Segment Builder te vereisen.

Gepubliceerde doelgroepen worden weergegeven in het AEP Poortenportaal met de oorsprong &quot;CJA&quot; en kunnen worden geactiveerd voor elke RT-CDP-bestemming, gebruikt als campagnedoelen in AJO, of gebruikt als toegangsvoorwaarden voor reizen.

**Zeer belangrijke overwegingen:**

- AEP Real-Time klantprofiel moet in de doelsandbox worden ingeschakeld
- CJA-verbinding moet een geldige persoon-id hebben die wordt omgezet in een naamruimte AEP-identiteit
- Gepubliceerde doelgroepen tellen mee voor de AEP-publieksrechten van de organisatie
- Vernieuwingskadentie moet worden geconfigureerd op basis van de activeringsvereisten (eenmalig, elke 4 uur, dagelijks, wekelijks)

**Voordelen:**

- Sluit de lus tussen analyse en activering
- Maakt het mogelijk high-value segmenten te detecteren met behulp van CJA cross-channel gedragsgegevens
- In CJA gedefinieerde soorten publiek kan gebruikmaken van dimensies en filters die niet beschikbaar zijn in AEP Segment Builder
- steunt de iteratieve verfijning van publiekscriteria op basis van analytische inzichten

**Beperkingen:**

- Maximaal 75 gepubliceerde doelgroepen per CJA-klant
- De eerste publieksevaluatie kan tot 24 uur duren voor grote datasets
- CJA-publicatiepubliek kan niet worden bewerkt in AEP — wijzigingen moeten worden aangebracht in CJA
- Vereist aanvullende naamruimte en profielconfiguratie naast basisanalyses

**Experience League:**

- [Overzicht publiek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Soorten publiek maken en publiceren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

### Optie D: Begeleide analyse voor productteams

**het Best voor:** de ervaringsinzichten van het Product — eigenschapadoptie, de tendensen van de gebruikersovereenkomst, behoud analyse, de omzetting van funnel, en de analyse van het versieeffect gebruikend CJA geleide analysewerkschema&#39;s zonder de complexe vrije het projectopstelling van Workspace te vereisen.

**hoe het werkt:**

Bij deze optie wordt CJA Guided Analysis gebruikt voor gestructureerde, gemodelleerde insight-generatie. Analyse met instructies biedt vooraf ontwikkelde analysetypen — funnel, trends, retentie, groei van gebruikers, betrokkenheidsfrequentie, impact op de release, eerste gebruik en tijdlijn — die analisten door een gestructureerde workflow laten lopen om specifieke product- en ervaringsvragen te beantwoorden. Het is ideaal voor productmanagers en analisten die snelle, gerichte inzichten nodig hebben zonder nieuwe vrije-vormprojecten te bouwen.

De implementatie verbindt AEP datasets met CJA, vormt een gegevensmening met gebeurtenis-vlakke dimensies en metriek, en gebruikt dan geleide analysewerkschema&#39;s om inzichten te produceren. De resultaten kunnen als panelen binnen de projecten van Workspace voor verdere aanpassing worden bewaard.

**Zeer belangrijke overwegingen:**

- Voor een analyse met instructies zijn CJA-productrechten vereist, waaronder mogelijkheden voor analyse met instructies.
- Meest geschikt voor product- en ervaringsanalyses in plaats van meting van de campagneprestaties
- Biedt gestructureerde workflows die toegankelijker zijn voor gebruikers die geen analist zijn
- Kan worden gecombineerd met vrije Workspace-analyse voor dieper onderzoek

**Voordelen:**

- Lagere toegangsbarrière — gestructureerde workflows begeleiden gebruikers door de analyse
- Speciaal ontworpen voor vragen over productervaring (funnel, retentie, groei, impact)
- Snellere tijd-aan-insight voor gemeenschappelijke analytische vragen
- Opgeslagen analyses kunnen in Workspace-projecten worden ingesloten, naast vrije-vormanalyse

**Beperkingen:**

- Minder flexibel dan vrije Workspace-analyse
- Beperkt tot de vooraf ontwikkelde analysetypen (funnel, trends, retentie, groei, frequentie, impact, tijdlijn)
- Segmentvergelijkingen ondersteunen tot 3 segmenten tegelijk
- Funnel-analyse ondersteunt maximaal 15 stappen

**Experience League:**

- [Overzicht van geleide analyse](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-weergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Weergave Behouden](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

### Optievergelijking

In de volgende tabel worden de beschikbare implementatieopties vergeleken.

| Criteria | Optie A: Campagneprestaties | Optie B: Reis van de klant | Optie C: Analyse + activering | Optie D: Analyse met instructies |
| --- | --- | --- | --- | --- |
| Best voor | Meting en optimalisatie van campagnes | Transparantie over verschillende kanalen | Activering van het insight-publiek | Inzichten in productervaring |
| Complexiteit | Low-Medium | Hoog | Hoog | Laag |
| Vereiste gegevensbestanden | AJO campagne-/reisevenementen | Meerdere gegevenssets met meerdere kanalen | Zelfde als A of B, plus profielidentiteit | Gebeurtenisgegevenssets met productinteracties |
| Belangrijke visualisaties | Vrije-vormtabellen, samenvattingsnummers, trendlijnen | Stroom, fallout, cohort, attributie | Zelfde als A of B, plus publiekspublicaties | Funnel, trends, behoud, groei |
| Activeringsmogelijkheid | Nee (alleen rapportage) | Nee (alleen rapportage) | Ja (publiceert publiek naar AEP) | Nee (alleen rapportage) |
| Publiek vereist | Marketinganalisten, campagnemanagers | Gegevensanalisten, reisarchitecten | Analyses + activeringsteams | Productmanagers, groeianalisten |
| CJA-functies gebruikt | Verbinding, Gegevens, Workspace, Berekende Metriek, Dashboard | Verbinding, Gegevens, Workspace, Berekende Metriek, Dashboard | Hetzelfde als A of B, plus Audience Publishing | Verbinding, gegevensweergave, analyse met instructies, dashboard |
| Tijd naar eerste insight | Dagen | Weken | Weken | Uren dagen |

### Kies de juiste optie

Gebruik de volgende richtlijnen om de implementatieoptie te selecteren die het beste bij uw behoeften past.

- **als uw primair doel campagnedoeltreffendheid** meet en u AJO campagnegegevens hebt die in AEP stromen, beginnen met **Optie A**. Het levert de snelste tijd-aan-waarde voor het melden van de marketing prestaties.

- **als u de volledige klantenreis** over Web, app, e-mail, en off-line aanraakpunten moet begrijpen, en u veelvoudige datasets met verenigbare identiteitskaart van de Persoon hebt, kies **Optie B**. Het verstrekt de diepste analytische mogelijkheden maar vereist meer voorinvestering in de configuratie van de gegevensmening.

- **Als u op inzichten** wilt handelen door CJA-Ontdekking segmenten terug naar AEP voor activering in rt-CDP of AJO te publiceren, kies **Optie C**. Dit breidt Optie A of B met publiek het publiceren uit en vereist AEP Real-Time configuratie van het Profiel van de Klant.

- **als uw team snelle, gestructureerde productinzichten** zonder de ingewikkeldheid van vrije projecten van Workspace nodig heeft, en uw SKU van CJA omvat geleide analyse, kies **Optie D**. Het is het snelste pad naar het beantwoorden van specifieke vragen over productervaring.

- **Vele organisaties voeren veelvoudige opties** uit: Optie A voor het op de markt brengen van de campagnedashboards van het team, Optie B voor de kanaalanalyse van het analytieteam, en Optie D voor de zelfbedieningstoetsen van het productteam. Deze opties delen dezelfde CJA-infrastructuur voor verbinding en gegevensweergave.

## Uitvoeringsfasen

In deze sectie worden de stapsgewijze implementatiefasen voor dit gebruikspatroon beschreven.

### Fase 1: Gegevensverbinding

**functie van de Toepassing:** CJA: De Verbinding van gegevens

Deze fase vormt een verbinding van CJA die één of meerdere datasets van AEP aan CJA voor analyse bindt. De verbinding bepaalt welke datasets in CJA stromen, hoe de gebeurtenissen over datasets via identiteitskaart van de Persoon worden vastgemaakt, en hoe de historische en het stromen gegevens worden opgenomen. Dit is de fundamentele verbinding tussen het AEP data Lake en CJA.

#### Beslissingspunten

In deze fase moeten de volgende besluiten worden genomen.

>[!NOTE]
>**Besluit: de zandbakselectie van AEP**
>
>Welke zandbak van AEP bevat de brondatasets?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Productiesandbox | Live-klantgegevens voor productierapportage | Gebruik voor productiedashboards en rapportage van belanghebbenden |
>| Ontwikkelingssandbox | Testen en herhalen vóór de productie | Gebruik voor aanvankelijke configuratie en bevestiging alvorens aan productie te bevorderen |

>[!NOTE]
>**Besluit: De selectie van de Dataset en typeaanwijzing**
>
>Welke datasets van AEP zouden in de verbinding moeten worden omvat, en welk type zou elk moeten worden toegewezen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Gebeurtenisgegevenssets | Gedetailleerde gedragsgegevens (webinteracties, toepassingsgebeurtenissen, campagneinteracties, transacties) | Een tijdstempelveld vereisen; de kern van de meeste analyses vormen |
>| Gegevensbestanden opzoeken | Referentiegegevens sleutelwaarde (productcatalogus, campagnemetagegevens, opslaglocaties) | Deelgenomen aan gebeurtenisgegevens via een gedeelde sleutel; alleen de laatste status wordt gebruikt |
>| Profielgegevenssets | Attributen op persoonlijk niveau (loyaliteitslaag, levensduurwaarde, CRM-attributen) | Verrijking op persoonniveau bieden; alleen de laatste staat wordt gebruikt |

>[!NOTE]
>**Besluit: De configuratie van identiteitskaart van de persoon**
>
>Welk gebied dient als Persoon identiteitskaart voor dwars-dataset stitching?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| CRM-id | Organisatie heeft consistente CRM-id over kanalen | Biedt de meest nauwkeurige cross-channel stitching voor bekende klanten |
>| ECID (Experience Cloud-ID) | Primair anonieme werking van websites/apps analyseren | Apparaatbereik; hecht niet aan andere apparaten zonder identiteitsresolutie |
>| E-mail (hashed) | E-mail is de algemene id in gegevenssets | Werkt goed wanneer e-mail consistent wordt vastgelegd tussen aanraakpunten |
>| Aangepaste naamruimte | Organisatie gebruikt een bedrijfseigen id | Moet overeenkomen met een naamruimte voor AEP-identiteit voor publiceren door publiek (Option C) |

>[!NOTE]
>**Besluit: De waaier van de achtergrond**
>
>Hoeveel historische gegevens zouden in de verbinding moeten worden ingevoerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alle bestaande gegevens | Maximale historische diepte vereist voor vergelijkingen van jaar tot jaar en langetermijntendensen | De steun voor grote datasets (miljarden verslagen) kan dagen vergen om te voltooien |
>| Aangepast datumbereik | Alleen de recente geschiedenis is relevant, of optimalisatie van opslag is een probleem | Beperkt de historische diepte die beschikbaar is voor analyse |
>| Geen backfill | Alleen toekomstgerichte analyse is nodig | Snelste verbindingsinstelling; geen historische gegevens beschikbaar tot nieuwe gegevens worden doorgegeven |

>[!NOTE]
>**Besluit: Het stromen enablement**
>
>Moeten nieuwe gegevens in real time in CJA stromen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Streaming inschakelen | Er is bijna realtime rapportage nodig (gegevens zijn beschikbaar binnen ~90 minuten na inname van AEP) | Meest gangbaar voor productieverbindingen; maakt tijdige analyse mogelijk |
>| Alleen batch | Periodieke vernieuwing is voldoende en streaming is niet nodig | Eenvoudigere configuratie; gegevens beschikbaar na batchverwerking |

#### Gegevensverbinding configureren

**navigatie UI:** CJA > Verbindingen > creëren nieuwe verbinding

Belangrijke configuratiedetails:

- De naam en beschrijving van de verbinding moeten de naamconventies van de organisatie volgen
- Het gemiddelde aantal dagelijkse gebeurtenissen wordt gebruikt voor de capaciteitsplanning van CJA
- Alle gegevenssets in één verbinding moeten afkomstig zijn uit dezelfde AEP-sandbox
- De gebieden van identiteitskaart van de persoon moeten over alle datasets voor nauwkeurige dwars-dataset het stitching consistent zijn
- Verifieer dat het gebied van identiteitskaart van de Persoon bestaat en in elke dataset alvorens het aan de verbinding toe te voegen wordt bevolkt

**documentatie van Experience League:**

- [Overzicht van verbindingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Verbinding maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Verbindingen beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Fase 2: Configuratie gegevensweergave

**functie van de Toepassing:** CJA: De Configuratie van de Mening van Gegevens

Deze fase vormt een gegevensmening die bepaalt hoe de verbindingsgegevens in analyse verschijnen. De gegevensmening bepaalt welke schemagebieden als afmetingen en metriek worden blootgesteld, hoe de waarden worden toegeschreven en voortgeduurd, hoe de zittingen worden bepaald, en welke afgeleide gebieden ruwe gegevens in analyse-klaar componenten omzetten. Er kunnen meerdere gegevensweergaven worden gemaakt via één verbinding voor verschillende analytische perspectieven.

#### Beslissingspunten

In deze fase moeten de volgende besluiten worden genomen.

>[!NOTE]
>**Besluit: Container noemend**
>
>Welke terminologie zouden de containers moeten gebruiken om het bedrijfsdomein aan te passen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Standaard (persoon/sessie/gebeurtenis) | De standaardterminologie voor analyses wordt door het team begrepen | Werkt voor de meeste implementaties |
>| Aangepaste namen (bijvoorbeeld Shopper / Visit / Interaction) | Bedrijfs domein-specifieke terminologie verbetert gebruikerstoepassing | Helpt niet-technische belanghebbenden het bereik van de analyse te begrijpen |
>| B2B-namen (bijvoorbeeld account/betrokkenheid/aanraakpunt) | B2B-analyse waarbij de analyse op rekeningniveau de focus heeft | Richt containerwerkingsgebied met B2B bedrijfsconcepten |

>[!NOTE]
>**Besluit: Sessietime-out**
>
>Hoe lang van inactiviteit een zittingsgrens bepaalt?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| 30 minuten (standaard) | Standaarddefinitie van webanalysetesessie | Industriestandaard; afgestemd op de meeste benchmarks voor analyses |
>| 15 minuten | Inhoud in korte vorm of transactiesites waar gebruikers taken snel voltooien | Creeert meer zittingen; kan verschillende gebruikersinzichten beter vangen |
>| 60 minuten of langer | Inhoud in lange vorm, complexe B2B-interacties of zware reizen voor onderzoek | Minder sessies; legt uitgebreid onderzoek vast als afzonderlijke sessies |
>| Aangepast met nieuwe sessiegebeurtenissen | Bepaalde gebeurtenissen (zoals het starten van de app, het doorklikken van de campagne) moeten altijd een nieuwe sessie starten | Verstrekt zaken-logica-gedreven zittingsgrenzen |

>[!NOTE]
>**Besluit: De gebreken van het model van de Attributie**
>
>Welk standaard toewijzingsmodel zou op omzettingsmetriek moeten worden toegepast?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Laatste aanraking (standaard) | Krediet moet vóór conversie naar het meest recente aanraakpunt gaan | Eenvoudig en intuïtief; kan bewustmakingskanalen onderschatten |
>| Eerste aanraking | Begrijpen welke kanalen de aanvankelijke bewustwording en verwerving drijven | Nuttig voor acquisitieanalyse; negeert aanraakpunten op het gebied van verpleegkunde |
>| Lineair | Alle aanraakpunten moeten gelijk krediet delen | Eerlijke distributie; kan de impact van belangrijke aanraakpunten verminderen |
>| Tijdverlies | Recente touchpoints zouden meer krediet moeten krijgen dan verre | Saldi van recuperatie met historische bijdrage |
>| U-gevormd | De eerste en laatste aanspreekpunten verdienen het meeste krediet | Goed voor inzicht in zowel de aanschaf- als de sluitingskanalen |
>| Algorithmic | Gegevensgestuurde attributie met behulp van CJA-AI-modellen | Het nauwkeurigst maar vereist voldoende conversiegegevensvolume |

>[!NOTE]
>**Besluit: Afgeleide gebiedslogica**
>
>Zijn de douanebedrijfsregels nodig om ruwe gegevens in analyse-klaar dimensies om te zetten?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Classificatie marketingkanaal (Case When) | Onbewerkte volgcodes moeten worden ingedeeld in kanaalgroepen | Meest voorkomende afgeleide praktijkgevallen; kritiek voor kanaalanalyse |
>| Waardebeperking | Doorlopende waarden moeten in bereiken worden gegroepeerd (bijvoorbeeld ordewaardenlagen) | Vereenvoudigt de analyse van continue metriek |
>| Veld samenvoegen | Meerdere bronvelden moeten worden gecombineerd in één dimensie | Nuttig wanneer het zelfde concept in verschillende schemawegen over datasets bestaat |
>| Regex-extractie | Gestructureerde waarden moeten worden geparseerd (bijv. het type campagne uit de campagnecode halen) | Krachtig, maar vereist zorgvuldig regex patroonontwerp |

#### Gegevensweergave configureren

**navigatie UI:** CJA > de meningen van Gegevens > creëren nieuwe gegevensmening

Belangrijke configuratiedetails:

- Selecteer de bovenliggende verbinding die in Fase 1 is gemaakt
- Vorm tijdzone en kalendertype om rapporteringsvereisten aan te passen
- XDM-schemavelden toewijzen aan dimensies met de juiste instellingen voor persistentie (toewijzing en verlopen)
- XDM-schemavelden toewijzen aan metriek met indelings- (decimaal, geheel getal, valuta, percentage, tijd) en attributie-instellingen
- Configureer include/exclude-regels voor afmetingen om irrelevante waarden uit te filteren
- Waar nodig metrische deduplicatie inschakelen om dubbeltelling te voorkomen
- Afgeleide velden maken voor classificatie van marketingkanalen, waardering omsluiten of samenvoegen van velden
- Maximaal 5.000 dimensies en 5.000 metriek per gegevensweergave
- Maximaal 100 afgeleide velden per gegevensweergave

#### Waar opties afwijken

**voor Optie A (de prestatiesanalyses van de Campagne):**

Specifieke afmetingen van de kaart: naam van de campagne, naam van de reis, kanaaltype, berichtvariant, onderwerpregel. Metrische gegevens van kaartlevering: verzenden, leveringen, openen, klikken, stuitingen, afmelden. Vorm attributie op omzettingsmetriek die op de filosofie van de campagnemeting wordt gebaseerd.

**voor Optie B (de analyse van de reis van de Klant):**

Meld kanaaloverschrijdende afmetingen toe: paginanaam, toepassingsscherm, kanaal, campagne, product, inhoudstype. Wijs betrokkenheid en omzettingsmetriek over alle kanalen toe. Meerdere toewijzingsmodellen configureren voor vergelijkingsanalyse. Maak afgeleide velden voor kanaalclassificatie en identificatie van het reisstadium.

**voor Optie D (Geleide analyse):**

Afmetingen op gebeurtenisniveau toewijzen en metingen die relevant zijn voor de analyse van de productervaring: functienaam, actie van de gebruiker, soort betrokkenheid. Focus op gebeurtenissen die funnel-stappen, retentiecriteria en groeisignalen definiëren.

**documentatie van Experience League:**

- [Overzicht van gegevensweergaven](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Een gegevensweergave maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Overzicht van componentinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributie-instellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Indelingsinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Metrische deduplicatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Waarden opnemen/uitsluiten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Sessieinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Afgeleide velden](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Fase 3: Analyse en metrische creatie

**de functie van de Toepassing:** CJA: De Analyse van Workspace, CJA: Begeleide Analyse, CJA: Berekende Metrische Creatie

Deze fase bouwt de analysewerkruimten (vrije vormprojecten of geleide analyse), gegevens gegevens voor afgeleide KPIs, filters voor gesegmenteerde analyse, en annotaties voor zeer belangrijke gebeurtenissen gegevens berekend. Dit is waar de analytische waarde wordt gerealiseerd — bouwend de lijsten, visualisaties, en metriek die bedrijfsvragen beantwoorden.

#### Beslissingspunten

In deze fase moeten de volgende besluiten worden genomen.

>[!NOTE]
>**Besluit: De benadering van de Analyse**
>
>Moet bij deze analyse gebruik worden gemaakt van vrije Workspace-projecten of geleide analyseworkflows?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Freeform Workspace (opties A, B, C) | Diepe verkennende analyse, aangepaste indelingen, complexe indelingen, geavanceerde visualisaties | Maximale flexibiliteit; vereist de vaardigheid van de analist; steunt alle visualisatietypen |
>| Analyse met instructies (optie D) | Gestructureerde productinzichten, snelle antwoorden op specifieke vragen, minder technische gebruikers | Snellere tijd-aan-insight; beperkt tot pre-gebouwde analysetypen; bespaart aan Workspace voor verdere aanpassing |
>| Beide | Organisatie heeft behoefte aan diepgaande analyse en snelle gestructureerde inzichten | Gebruik een geleide analyse voor veelvoorkomende vragen; Workspace voor diepgaand onderzoek |

>[!NOTE]
>**Besluit: De types van visualisatie**
>
>Welke visualisaties geven het beste de inzichten voor dit gebruiksgeval door?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Vrije-vormtabel | Gedetailleerde gegevensverkenning met uitsplitsingen naar dimensie | De stichting van de meeste analyses; steunt tot 10 verdelingsniveaus |
>| Stroomvisualisatie | Werken met plakken (paginastroom, kanaalovergangen) | Uitstekend voor detectie van reispaden; kan complex zijn met hoge kardinaliteit |
>| Uitvalvisualisatie | Omzetting meten via een gedefinieerde reeks aanraakpunten | Best voor funnel-analyse; laat duidelijk een uitval zien bij elke stap |
>| Cohortingtabel | Bewaaranalyse in de loop van de tijd door verwervingscohort | Toont hoe goed verschillende groepen behouden blijven; kritiek voor levenscyclusanalyse |
>| Kenmerk, deelvenster | Kenmerkingsmodellen vergelijken voor conversiemetriek | Naast elkaar modelvergelijking; vereist duidelijke definitie van conversiegebeurtenis |
>| Samenvattingsnummer/wijziging | Uitvoerende KPI-weergave met vergelijking over een periode heen | Schone, in één oogopslag metrische display; ideaal voor dashboardheaders |

>[!NOTE]
>**Besluit: Berekende metrische formules**
>
>Welke zaken KPIs berekende metriek voorbij de metriek van de basismening van gegevens vereist?
>
>| Metrisch patroon | Voorbeeld van formule | Wanneer gebruiken |
>| --- | --- | --- |
>| Verhouding/snelheid | Bestellingen/bezoeken | Conversiesnelheid, doorklikfrequentie, stuitsnelheid |
>| Gefilterde metrisch | Inkomsten (waarbij kanaal = &quot;e-mail&quot;) | Kanaalspecifieke of segmentspecifieke maatregelen |
>| Gemiddeld per item | Ontvangsten/bestellingen | Gemiddelde orderwaarde, inkomsten per bezoek |
>| Samengestelde formule | (Ontvangsten - kosten) / Ontvangsten | Margepercentage, ROI-berekeningen |
>| Betrokkenheidsscore | Gewogen som van interacties | Samengestelde betrokkenheidsscores over kanalen |

#### Analyse en metriek configureren

**navigatie UI:**

- Workspace: CJA > Workspace > Projecten > Project maken > Leeg project
- Analyse met instructies: CJA > Home > Analyse met instructies (of Workspace > Maken > Analyse met instructies)
- Berekende waarden: CJA > Componenten > Berekende meetwaarden > Maken
- Filters: CJA > Componenten > Filters > Filter maken

Belangrijke configuratiedetails:

- Selecteer de gegevensmening die in Fase 2 als mening van projectgegevens wordt gecreeerd
- Passende datumbereiken en vergelijkingsperiodes voor de analyse instellen
- Vrije-vormtabellen maken door afmetingen naar rijen en metriek naar kolommen te slepen
- Dimensie-indelingen toevoegen om gegevens op diepere niveaus te verkennen (bijv. kanaal voor campagne, pagina voor product)
- Creeer herbruikbare filters (segmenten) voor publiek-specifieke analyse (persoon-niveau, zitting-niveau, of gebeurtenis-niveau werkingsgebied)
- Annotaties toevoegen om belangrijke bedrijfsgebeurtenissen te markeren (productlanceringen, campagnes, incidenten)
- Berekende metrische notatie instellen (decimaal, percentage, valuta, tijd) en polariteit (omhoog is goed / omhoog is slecht)
- Werkruimteprojecten delen met CJA-gebruikers met weergave- of bewerkingsmachtigingen

#### Waar opties afwijken

**voor Optie A (de prestatiesanalyses van de Campagne):**

Vormtabellen maken met campagnedimensies, uitgesplitst naar bezorgings- en betrokkenheidswaarden. Creeer gegevens verwerkte metriek voor open tarief, klik-door tarief, omzettingspercentage, opbrengst per bericht, en campagne ROI. Voeg trendvisualisaties toe om campagneprestaties in tijd te volgen. Vergelijk campagnevarianten met segmentvergelijking.

**voor Optie B (de analyse van de reis van de Klant):**

Stel fallout-visualisaties samen om de aflooppunten van de rit te identificeren. Maak stroomvisualisaties om navigatiepatronen over kanalen te ontdekken. Cohortabellen maken om retentie te meten aan de hand van verwervingscohort. Configureer het deelvenster Toewijzing om toewijzingsmodellen voor conversiemetriek te vergelijken. Berekende maatstaven maken voor de voltooiingssnelheid van de reis, de interkanaalbetrokkenheidsscore en de conversie van het levenscyclusstadium.

**voor Optie C (Analytics met publiek het publiceren):**

Bouw de analysewerkruimten van Optie A of B, dan identificeer hoog-waarde of ondermaatse segmenten tijdens analyse. Maak CJA-filters die deze segmenten vastleggen voor publicatie in fase 5.

**voor Optie D (Geleide analyse):**

Selecteer het juiste geleide analysetype op basis van de bedrijfsvraag. Configureer toetsgebeurtenissen, datumbereiken, telmethoden en segmentvergelijkingen. Sla voltooide analyses op als deelvensters in Workspace-projecten voor verdere aanpassing.

**documentatie van Experience League:**

- [Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Een project maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Vrije-vormtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Stroomvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Uitvalvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohortingtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Kenmerk, deelvenster](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Afmetingen onderverdelingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Overzicht van filters](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Filters maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Overzicht van annotaties](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Overzicht van berekende metriek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berekende waarden maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Berekende metrische functies](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Overzicht van geleide analyse](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-weergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trends, weergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Weergave Behouden](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Actieve groeiweergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Weergave betrokkenheidsfrequentie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Weergave-effect](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Content-analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/content-analytics)

### Fase 4: Publiceren op dashboard

**functie van de Toepassing:** CJA: Het Publiceren van het Dashboard &amp; van het Scorecard

Deze fase leidt tot interactieve dashboards (de projecten van Workspace) en mobiele scorecards die KPI zicht aan belanghebbenden leveren. De dashboards verstrekken uitvoerend en operationeel zicht door summiere aantallen, trendlijnen, onderverdelingen, en annotaties. Mobiele scorecards bieden in één oogopslag prestatiegegevens via de mobiele app [!DNL Adobe Analytics] dashboards.

#### Beslissingspunten

In deze fase moeten de volgende besluiten worden genomen.

>[!NOTE]
>**Besluit: Het type van Dashboard**
>
>Is dit een Workspace-dashboard voor desktop, een mobiele scorecard of beide?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Workspace-project (bureaublad) | Gedetailleerde interactieve dashboards voor analisten en marketers | Volledige visualisatiemogelijkheden; ondersteunt deelvensters, tabellen en complexe lay-outs |
>| Mobiele scorecard | KPI&#39;s voor managers en belanghebbenden op mobiele apparaten in één oogopslag | Beperkt tot 16 tegels; samenvattingsnummers met trendsparklines; mobiele app vereist |
>| Beide | Organisatie heeft behoefte aan zowel gedetailleerde analyse als mobiele rapportering op uitvoeringsniveau | Afzonderlijke artefacten maar kunnen de zelfde gegevensmening en berekende metriek delen |

>[!NOTE]
>**Besluit: Het delen model**
>
>Wie moet het dashboard ontvangen en hoe?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Delen met specifieke gebruikers | Beperkt publiek met specifieke toegangsbehoeften | Meest korrelige controle; vereist individueel gebruikersbeheer |
>| Delen met productprofielgroep | Toegang op teamniveau uitgelijnd met organisatorische rollen | Efficiënt voor distributie in het hele team; beheerd via CJA-productprofielen |
>| E-maillevering plannen | Herhaalde PDF/CSV-rapporten voor belanghebbenden die zich niet bij CJA aanmelden | Automatische levering; maximale frequentie is per uur; PDF- en CSV-indelingen |

>[!NOTE]
>**Besluit: Het zicht van de Annotatie**
>
>Moeten de belangrijkste gebeurtenissen op de trendlijnen van het dashboard worden geannoteerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Ja — aantekeningen maken | Belangrijke campagnes, productlanceringen, plaatsincidenten, of seizoensgebonden gebeurtenissen kunnen gegevenstrends verklaren | Annotaties worden weergegeven als markeringen op lijngrafieken en scorecardtrends; bieden context voor gegevenspikes of dips |
>| Nee | Het publiek van het dashboard is vertrouwd met bedrijfscontext en de aantekeningen zouden vlotter toevoegen | Eenvoudigere visuele presentatie |

#### Dashboards configureren

**navigatie UI:**

- Workspace-dashboards: CJA > Workspace > Create project
- Mobiele scorecards: CJA > Projecten > Maken > Mobiele scorecard
- Delen: CJA > Workspace > Delen > Delen met Workspace-gebruikers
- Geplande levering: CJA > Workspace > Share > Plan project

Belangrijke configuratiedetails:

- Voor mobiele scorecards maakt u tegels die één metrische waarde met een overzichtsgetal en een sparkline trend weergeven
- Standaarddatumbereiken en vergelijkingsperiodes configureren (bijv. afgelopen 30 dagen vs. vorige periode of maand-over-maand)
- Voeg publiek-scoped filters toe die de managers op mobiele scorecards kunnen van een knevel voorzien
- Geplande e-maillevering configureren voor terugkerende PDF- of CSV-rapporten
- Maximaal 16 tegels per mobiele scorecard; maximaal 15 panelen per Workspace-project
- Annotaties zijn beperkt tot 100 per gegevensweergave

**documentatie van Experience League:**

- [Een mobiele scorecard maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [scorecards configureren en beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-dashboards — handleiding](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Projecten delen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Projecten plannen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Visualisatie van overzichtsnummers](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)
- [Datumbereiken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

### Fase 5: Publicatie door het publiek (alleen optie C)

**functie van de Toepassing:** CJA: Het Publiceren van het publiek

In deze fase wordt het publiceren van CJA-publiek zodanig geconfigureerd dat met analyse ontdekte segmenten worden teruggezet naar het Real-Time Klantprofiel van AEP voor downstreamactivering in RT-CDP-bestemmingen, AJO-campagnes of AJO-reizen.

#### Beslissingspunten

In deze fase moeten de volgende besluiten worden genomen.

>[!NOTE]
>**Besluit: Vernieuwen kadentie**
>
>Hoe vaak moet het lidmaatschap van het publiek worden vernieuwd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Eenmalig (momentopname) | Campagne-specifiek publiek dat niet aan de gang hoeft te blijven verfrissen | Geen verdere verwerking; moet opnieuw publiceren voor updates |
>| Elke 4 uur | Vereisten voor activering in realtime | Hogere verwerkingskosten; meest geschikt voor tijdgevoelige doelgroepen |
>| Dagelijks | Standaard activeringscursus voor marketing | Evenwichtige versheid en kosten; meest gebruikelijke keuze |
>| Wekelijks | Stabiel, langzaam veranderend publiek | Minimale verwerking; geschikt voor lange-termijnsegmenten |

>[!NOTE]
>**Besluit: Identiteitsnaamruimte**
>
>Welke naamruimte voor identiteit moet CJA gebruiken voor het oplossen van publieksleden?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| CRM-id | Hoofdklant-id van organisatie | Beste nauwkeurigheid voor bekende klantovereenkomst |
>| ECID | Primair publiek op het web/op apps | Apparaatbereik; wordt mogelijk niet omgezet in alle profielrecords |
>| E-mail (hashed) | E-mail is de algemene id voor activering | Moet overeenkomen met de naamruimte die wordt gebruikt in AEP-identiteitsconfiguratie |
>| Aangepaste naamruimte | Bedrijfs-id gebruikt in de hele organisatie | Moet zijn geconfigureerd in AEP Identity Service |

#### Publiceren van publiek configureren

**navigatie UI:** CJA > Componenten > Soorten > publiek publiceren

Belangrijke configuratiedetails:

- Bepaal publiekscriteria gebruikend de filters van CJA (persoon, zitting, of het werkingsgebied van de gebeurteniscontainer)
- Selecteer de gegevensweergave en het filter dat u wilt publiceren
- Naamruimte configureren voor AEP-profielresolutie
- De vernieuwingsfrequentie instellen op basis van de activeringsbehoeften
- Publicatiestatus controleren in de lijst CJA-soorten publiek (Componenten > Soorten publiek > Status)
- Controleren of het publiek wordt weergegeven in de AEP Audience Portal (Soorten publiek > Bladeren > Filteren op oorsprong &quot;CJA&quot;)
- Maximaal 75 gepubliceerde doelgroepen per CJA-klant (voor alle sandboxen)
- De eerste publieksevaluatie kan tot 24 uur duren voor grote datasets

**documentatie van Experience League:**

- [Overzicht publiek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Soorten publiek maken en publiceren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Soorten publiek beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)
- [Overzicht van het portal Publiek](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

## Implementatieoverwegingen

In deze sectie worden hulplijnen, valkuilen, beste praktijken en afwegingsbeslissingen voor dit gebruikspatroon besproken.

### Afbeeldingen en limieten

Voor deze implementatie gelden de volgende instructies en beperkingen.

- **de grenzen van de Verbinding:** Maximum aantal verbindingen per organisatie wordt beperkt door CJA SKU recht. Een enkele verbinding kan gegevenssets van slechts één AEP-sandbox bevatten. — [ de guardrails van CJA ](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- **de meningsgrenzen van Gegevens:** Maximum van 5.000 dimensies en 5.000 metriek per gegevensmening. Maximaal 100 afgeleide velden per gegevensweergave met maximaal 5 niveaus geneste functies.
- **de grenzen van Workspace:** Maximum van 40 panelen per project. Vrije-vormtabellen bieden ondersteuning voor maximaal 10 dimensiescheidingen diep. Maximum van 50.000 rijen per rapportverzoek.
- **Scorecard grenzen:** Maximum van 16 tegels per mobiele scorecard.
- **het stromen latentie:** het stromen gegevens is typisch beschikbaar in CJA binnen 90 minuten van AEP opname.
- **het publiceren van het publiek grenzen van het publiek:** Maximum van 75 gepubliceerd publiek per klant van CJA. De minimale vernieuwingsfrequentie is elke 4 uur.
- **Geleide analysegrenzen:** de analyse van Funnel steunt een maximum van 15 stappen. Segmentvergelijkingen ondersteunen tot 3 segmenten tegelijk.

### Veelvoorkomende valkuilen

Houd rekening met de volgende algemene problemen bij het implementeren van dit patroon.

- **identiteitskaart van de Persoon wanverhouding over datasets:** Alle datasets in een verbinding moeten een verenigbaar gebied van identiteitskaart van de Persoon voor dwars-datasetanalyse gebruiken. Verkeerd overeenkomende persoon-id&#39;s resulteren in gefragmenteerde klantenweergaven waarbij dezelfde persoon als meerdere personen wordt weergegeven. Controleer de consistentie van de persoon-id voordat u de verbinding maakt.

- **Achtergrond die onverwacht lang neemt:** De grote datasets met miljarden verslagen kunnen dagen aan backfill vergen. Plan dit tijdens implementatietijdlijnen en begin de backfill vroeg. De voortgang in de weergave met verbindingsdetails volgen.

- **mening die van Gegevens &quot;niet gespecificeerd&quot;voor de meeste afmetingswaarden tonen:** het in kaart gebrachte schemagebied kan dun bevolkt in de brongegevens zijn. Controleer de brondataset voor gegevenskwaliteit alvorens een configuratiefout te veronderstellen. U kunt overwegen een afgeleid veld te gebruiken voor de verwerking van null-waarden.

- **de tellingen van de Zitting lijken onjuist:** de onderbrekingsmontages van de Zitting beïnvloeden dramatisch zitting-scoped metriek. Een zeer korte onderbreking leidt tot meer zittingen; een zeer lange onderbreking leidt tot minder. Nieuwe gebeurtenissen voor het starten van de sessie kunnen sessies ook onverwacht fragmenteren. De montages van de overzicht en van de testzitting tegen bekende patronen van het gebruikersgedrag.

- **model van de Attributie dat niet zoals verwacht van toepassing is:** de modellen van de Attributie zijn slechts op metriek, niet dimensies van toepassing. Verifieer het terugkijkvenster geschikt voor de bedrijfscyclus wordt geplaatst. Bij korte terugkijkvensters kunnen vroege funnel-aanraakpunten ontbreken.

- **Berekende metriek die nul of onverwachte waarden terugkeren:** verifieer dat de basismetriek in de formule van verwijzingen wordt voorzien gegevens in de mening van doelgegevens voor de geselecteerde datumwaaier hebben. Controleer of de maateenheid voor de verhouding nul is. Haal de metrische definitie op en controleer de formule structuur.

- **het publiceren van het publiek ontbreekt (Optie C):** de verbinding van CJA moet een geldige identiteitskaart van de Persoon hebben die aan een identiteit van AEP namespace oplost. Verifieer de configuratie van identiteitsnamespace en dat AEP Real-Time het Profiel van de Klant in de doelzandbak wordt toegelaten.

### Aanbevolen procedures

Volg deze best practices voor een geslaagde implementatie.

- **Begin met één enkele uitvoerige verbinding:** creeer één verbinding die alle relevante datasets omvat, dan creeer veelvoudige gegevensmeningen voor verschillende analytische perspectieven. Dit voorkomt de proliferatie van verbindingen en vereenvoudigt beheer.

- **Gebruik afgeleide gebieden voor de classificatie van het marketing kanaal:** eerder dan het baseren op ruwe het volgen codes, creeer afgeleide gebieden met Geval wanneer logica om verkeer in marketing kanalen te classificeren. Dit zorgt voor consistente kanaalrapportage voor alle analyses.

- **creeer een metrisch woordenboek:** Document alle gegevens verwerkt metriek met hun formules, voorgenomen gebruik, en verwachte waardewaaiers. Deel dit woordenboek met het analyseteam om verenigbaar metrisch gebruik over projecten te verzekeren.

- **de gegevensmeningen van het Ontwerp voor uw publiek:** creeer afzonderlijke gegevensmeningen voor verschillende groepen van belanghebbenden - een marketing gegevensmening met campagne-gerichte dimensies en metriek, en een mening van productgegevens met eigenschap en betrokkenheidsdimensies. Dit vereenvoudigt de componentenlijsten voor elke gebruikersgroep.

- **annoteer alles:** creeer aantekeningen voor campagnelanceringen, plaatsveranderingen, technische incidenten, seizoensgebondenheid, en om het even welke gebeurtenis die gegevenstrends zou kunnen verklaren. Annotaties bieden een kritieke context wanneer u dashboards maanden later controleert.

- **test gegevens verwerkt gegevens tegen handberekeningen:** alvorens op gegevens verwerkte metrisch voor dashboards te vertrouwen, stel een rapport met gegevens verwerkte metrisch en zijn basiscomponenten naast elkaar in werking. Controleer of de berekende waarden overeenkomen met een handmatige berekening.

- **filters van het Gebruik strategisch:** creeer herbruikbare filters voor gemeenschappelijke segmentatiepatronen (nieuw vs. terugkerend, mobiel vs. Desktop, door geografie). Pas deze als filters op paneelniveau toe in plaats van ze in elke vrije-vormtabel in te sluiten.

- **de verbindingsgezondheid van de Monitor regelmatig:** controleer de mening van verbindingsdetails voor overgeslagen verslagen, ontbroken partijen, en het stromen vertragingen. De kwaliteitskwesties van gegevens op het verbindingsniveau beïnvloeden alle stroomafwaartse analyse.

### Handelsbesluiten

Houd rekening met de volgende compromissen wanneer u uw implementatie plant.

>[!NOTE]
>**handel-off: De diepte van de analyse versus tijd-aan-insight**
>
>Optie B (de analyse van de reis van de Klant) verstrekt de diepste dwars-kanaalinzichten maar vereist significante voorinvestering in verbindingsconfiguratie, het ontwerp van de gegevensmening, en afgeleide gebiedsverwezenlijking. Optie D (Bewerken met instructies-analyse) biedt snellere time-to-insight met gestructureerde workflows, maar biedt minder analytische flexibiliteit.
>
>- **Optie B begunstigt:** Uitgebreid begrip, complexe multikanaalanalyse, attributiemodellering, de ontwikkeling van douaneKPI
>- **Optie D begunstigt:** Snelheid, toegankelijkheid voor niet-analytische gebruikers, gestructureerde vragen van de productervaring
>- **Aanbeveling:** Begin met Optie D voor directe productinzichten terwijl het bouwen van de infrastructuur van Optie B parallel. Veel organisaties werken beide tegelijk voor verschillende teams.

>[!NOTE]
>**handel-off: De volledigheid van de steun versus verbindingsbereidheid**
>
>Het invoeren van alle historische gegevens biedt een maximale analytische diepte voor vergelijkingen van jaar tot jaar en een langetermijnanalyse van trends, maar het terugvullen van grote gegevenssets kan dagen in beslag nemen. Het beperken van backfill aan een recente periode krijgt de verbinding klaar sneller maar beperkt historische analyse.
>
>- **Alle gegevens begunstigen:** De analyse van de langetermijntrend, jaar-over-jaar vergelijkingen, cohortanalyse met uitgebreide geschiedenis
>- **Beperkte backfill voorkeur:** snellere verbindingsbereidheid, snellere tijd aan eerste dashboard, opslagoptimalisering
>- **Aanbeveling:** Steunen alle gegevens voor productieverbindingen die strategische analyse steunen. Gebruik beperkte backfill voor ontwikkelingsverbindingen en gebruiksklare implementaties.

>[!NOTE]
>**handel-off: Enige uitvoerige gegevensmening vs. veelvoudige geconcentreerde gegevensmeningen**
>
>Eén gegevensweergave met alle afmetingen en metriek biedt een uniforme analytische werkruimte, maar kan gebruikers overweldigen met lijsten met componenten. De veelvoudige geconcentreerde gegevensmeningen (één per team of gebruikscase) vereenvoudigen de componentenervaring maar vereisen het handhaven van veelvoudige configuraties.
>
>- **Enige gegevensmening gunt:** Verenigde analyse, dwars-domeinonderverdelingen, eenvoudiger beheer
>- **Veelvoudige gegevensmeningen begunstigen:** de componentenlijsten van de Cleaner, team-specifieke terminologie, verschillende zittingsdefinities per gebruiksgeval
>- **Aanbeveling:** Begin met één primaire gegevensmening, creeer dan extra geconcentreerde gegevensmeningen als de ingewikkeldheid van de componentenlijst een belemmering aan goedkeuring wordt. Alle gegevensweergaven kunnen verwijzen naar dezelfde verbinding.

>[!NOTE]
>**handel-off: Het stromen in real time vs. partij-enige opname**
>
>Het toelaten van het stromen op de verbinding van CJA verstrekt dichtbij-real-time gegevens (binnen ~90 minuten van de opname van AEP) maar verwerkt onophoudelijk meer gegevens. De inname in batch verwerkt regelmatig gegevens en kan vertragingen veroorzaken.
>
>- **het stromen begunstigt:** Tijdige rapportering, controlerend actieve campagnes, dichtbij-real-time dashboards
>- **partij-slechts gunt:** Eenvoudigere configuratie, voorspelbare verwerkingsvensters, voldoende voor wekelijkse of maandelijkse rapportering
>- **Aanbeveling:** laat het stromen voor productieverbindingen toe. De incrementele verwerkingskosten zijn minimaal in vergelijking met de waarde van tijdige gegevens voor actieve campagnecontrole en operationele dashboards.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie voor dit gebruikspatroon.

### [!DNL Customer Journey Analytics] — Aan de slag

- [CJA-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

### Connecties

- [Overzicht van verbindingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Verbinding maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Verbindingen beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

### Gegevensweergaven

- [Overzicht van gegevensweergaven](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Een gegevensweergave maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Overzicht van componentinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributie-instellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Indelingsinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Metrische deduplicatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/metric-deduplication)
- [Waarden opnemen/uitsluiten](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/include-exclude-values)
- [Sessieinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)
- [Afgeleide velden](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)

### Workspace en analyse

- [Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Een project maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Vrije-vormtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Stroomvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Uitvalvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohortingtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Kenmerk, deelvenster](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Afmetingen onderverdelingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)
- [Projecten delen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Projecten plannen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Overzicht van exporteren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/export/export-cloud)

### Analyse met instructies

- [Overzicht van geleide analyse](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-weergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trends, weergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Weergave betrokkenheidsfrequentie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/frequency)
- [Weergave Behouden](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)
- [Actieve groeiweergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/user-growth/active)
- [Weergave-effect](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/release)
- [Botsingweergave voor eerste gebruik](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/impact/first-use)
- [Tijdlijnweergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/streams/timeline)

### Onderdelen

- [Overzicht van filters](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Filters maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Overzicht van berekende metriek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berekende waarden maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Berekende metrische functies](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-functions)
- [Overzicht van annotaties](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Datumbereiken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)
- [Metrische component](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/apply-create-metrics)

### Publicatie door het publiek

- [Overzicht publiek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Soorten publiek maken en publiceren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Soorten publiek beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

### Inhoudsanalyse

- [Content-analytics](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/content-analytics)
- [Content Analytics-configuratie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/content-analytics/config/configuration)

### Dashboards &amp; scorecards

- [Een mobiele scorecard maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [scorecards configureren en beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-dashboards — handleiding](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Visualisatie van overzichtsnummers](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/summary-number-change)

### AEP-stichtingen

- [Overzicht van gegevenssets](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/overview)
- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Overzicht van bronnen](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van het portal Publiek](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-portal)

### Integratie van AJO-rapportage

- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [E-mailrapport campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/campaign-global-report-cja-email)
- [E-mailrapport reis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/reporting/journey-global-report-cja-email)

### Zelfstudies en hulplijnen

- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
