---
title: Gedragsaanbeveling
description: Leer hoe u aanbevelingen voor items en inhoud kunt genereren met behulp van selectiestrategieën en waarderingsmodellen.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '7626'
ht-degree: 0%

---


# Gedragsaanbeveling

In deze handleiding wordt beschreven hoe u gedragsproduct- en inhoudsaanbevelingen kunt implementeren met [!DNL Adobe Journey Optimizer] (AJO) Decisioning, [!DNL Real-Time Customer Data Platform] (RT-CDP) en [!DNL Adobe Experience Platform] (AEP). Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die persoonlijke aanbevelingen moeten doen via het web, mobiele apps en e-mailkanalen.

Het bevat alle uitvoerbare implementatieopties, beslissingsoverwegingen in elke fase en koppelingen naar [!DNL Adobe Experience League] -documentatie. De aanbeveling van het gedrag produceert punt-niveau of inhoud-vlakke aanbevelingen gebruikend gedragssignalen — productmeningen, aankopen, inhoudinteractie, onderzoeksvragen — gecombineerd met AJO beslissende selectiestrategieën en rangschikkingsmodellen. In tegenstelling tot de beslissing over aanbiedingen, die wordt gekozen uit een gekromde reeks marketingaanbiedingen met behulp van expliciete toelatingsregels, werkt dit patroon op grote itemcatalogi (producten, artikelen, video&#39;s) en gebruikt het gedrags affiniteitssignalen en op ML gebaseerde rangschikking om de meest relevante items voor elke bezoeker te laten overstijgen.

## Hoofdlettergebruik

Organisaties met productcatalogi, inhoudsbibliotheken of mediabibliotheken moeten de meest relevante items aan elke bezoeker laten zien op basis van hun gedragsgeschiedenis en activiteiten tijdens de sessie. Of het nu gaat om een carrousel &quot;aanbevolen voor u&quot; op een homepage, een widget voor meerdere verkopen op een pagina met productdetails of productaanbevelingen die in een e-mailcampagne zijn ingesloten, de onderliggende uitdaging is hetzelfde: het gedragsprofiel van elke bezoeker aanpassen aan de meest relevante items in een catalogus en deze aanbevelingen vervolgens op het juiste kanaal op het juiste moment uitvoeren.

Dit patroon verhelpt die uitdaging door gedragssignalen in real time via [!DNL Web SDK] of [!DNL Mobile SDK] in te voeren, ze te verwerken via AJO Decisioning-selectiestrategieën die itemkenmerken combineren met gedragscontext, en de aanbevolen items te leveren via internet, in-app of e-mailkanalen. Rangschikkingsmodellen kunnen op formule-gebaseerd zijn (bijvoorbeeld, soort door de score van de categorieaffiniteit) of op AI-niveau gerangschikt (bijvoorbeeld, gepersonaliseerd aanbevelingsmodel). Het patroon behandelt ook koudstartscenario&#39;s voor nieuwe bezoekers zonder gedragsgeschiedenis door terugvalaanbevelingen te vormen.

Het doelpubliek voor dit patroon omvat teams voor de handel in elektronische handel, teams voor de verpersoonlijking van inhoud, en teams voor digitale ervaring die de betrokkenheid, conversie en gemiddelde orderwaarde willen verbeteren door gepersonaliseerde aanbevelingen die door echt gebruikersgedrag worden gedreven.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

### [&#x200B; de dwars-verkoop van de aandrijving en upsell opbrengst &#x200B;](../../business-objectives/revenue-monetization/drive-cross-sell-upsell-revenue.md)

Aanvullende en hoogwaardige producten of services aan bestaande klanten promoten op basis van gedrag en aankoopgeschiedenis.

| KPI | Beschrijving |
| --- | --- |
| Upsell/CrosSell % | Percentage klanten dat aanbevolen aanvullende of premieartikelen koopt |
| Incrementele inkomsten | Aanvullende inkomsten die zijn toe te schrijven aan op aanbevelingen gebaseerde aankopen |
| Levensduur van klant | Waardeverhoging op lange termijn door een diepere betrokkenheid bij het product |

### [&#x200B; de omzettingspercentages van de Verhoging &#x200B;](../../business-objectives/revenue-monetization/increase-conversion-rates.md)

Verbeter het percentage bezoekers en de vooruitzichten die de gewenste acties zoals aankopen, inschrijven, of vormverzendingen voltooien.

| KPI | Beschrijving |
| --- | --- |
| Omrekeningskoers | Percentage bezoekers die zich na het aangaan van aanbevelingen converteren |
| Loodconversie | Tarief waartegen geadviseerde bezoekers klanten worden |
| Kosten per lead | Vermindering van aanschafkosten door aanmaning voor organische aanbevelingen |

### [&#x200B; lever gepersonaliseerde klantenervaringen &#x200B;](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)

Inhoud, aanbiedingen en berichten voor individuele voorkeuren, gedrag en levenscyclusfase aanpassen.

| KPI | Beschrijving |
| --- | --- |
| Betrokkenheid | Interactiefrequentie met aanbevolen oppervlakken (klik, weergave, invoegtoepassing) |
| Omrekeningskoers | Optillen van omrekeningskoersen voor met aanbevelingen belaste bezoekers versus controle |
| Klanttevredenheid (CSAT) | Verbetering van klanttevredenheid dankzij relevante, persoonlijke ervaringen |

## Voorbeelden van tactische gebruiksgevallen

Hieronder vindt u algemene tactische implementaties van dit patroon:

- Widget voor cross-sell van producten op de pagina met productdetails (klanten hebben ook gekocht)
- Carrousel &quot;Aanbevolen voor u&quot; op homepage op basis van browsergeschiedenis
- Aanbevelingen voor inhoud op mediasite op basis van leesgedrag
- &#39;Recent bekeken&#39; in combinatie met vergelijkbare objecten-widget
- Aanbevelingen voor aanvullende producten na aankoop
- Aanbevelingen voor e-mailproducten op basis van gedragsaffiniteit
- Categoriespecifieke aanbevelingen op basis van browsergedrag tijdens sessie
- Herwaardering van zoekresultaten op basis van gedragssignalen

## Kernprestatie-indicatoren

De volgende KPIs helpen de doeltreffendheid van gedrags adviserende implementaties meten.

| KPI | Meetmethode |
| --- | --- |
| Aanbevolen doorkliksnelheid (CTR) | Klikken op aanbevolen items gedeeld door aanbevelingen |
| Conversiesnelheid aanbeveling | Aankopen of gewenste acties van aanbevelingen klikken gedeeld door totale aanbevelingen klikken |
| Ontvangsten beïnvloed door aanbevelingen | Totale inkomsten uit orders die ten minste één aanbevolen product bevatten |
| Gemiddelde bestelwaarde (AOV) optillen | Verhoging van AOV voor sessies met aanbevelingen versus sessies zonder |
| Items per bestelling | Aantal items per bestelling voor sessies met een aanbeveling |
| Dekking aanbeveling | Percentage subsidiabele paginaweergaven of sessies waarvoor persoonlijke (niet-reservekopie)aanbevelingen zijn ontvangen |
| Fallbacksnelheid koude start | Percentage van aanbevelingen die worden gedaan door fallback-logica als gevolg van onvoldoende gedragsgeschiedenis |

## Hoofdletterpatroon gebruiken

**Aanbeveling van het Gedrag**

Genereer aanbevelingen op itemniveau of inhoudsniveau op basis van gedragssignalen, met gebruik van AJO-selectiestrategieën en rangordemodellen voor het weergeven van contextafhankelijke inhoud.

**Keten van de Functie:** De Ingestie van het Gedrag van het Signaal > de Evaluatie van de Strategie van de Beslissing > de Levering van de Aanbeveling > het Melden

Zie de sectie Patrooncompositie onder Implementatieoverwegingen voor hulp bij het combineren van patronen.

## Applicaties

In dit gebruikspatroon worden de volgende toepassingen gebruikt.

- **[!DNL Adobe Journey Optimizer] (AJO) Beslissing** — De strategieën van de selectie, rangschikkende modellen, puntcatalogi, en besluitvormingsbeleid die gedragssignalen evalueren en de meest relevante punten voor elke bezoeker terugkeren
- **[!DNL Adobe Real-Time Customer Data Platform] (rt-CDP)** — De accumulatie van de profielgegevens van het Gedrag, publieksevaluatie voor aanbeveling het scoping, en gegevens verwerkte attributen voor het gedrag affiniteitscoring
- **[!DNL Adobe Experience Platform] (AEP)** — Gedragingen van gebeurtenissen via [!DNL Web SDK] en [!DNL Mobile SDK] , [!DNL Edge Network] verwerking, XDM-schemabeheer voor gebeurtenis- en catalogusgegevens

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary Function | Status | Wat moet er gebeuren? | Experience League Reference |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | AJO-sandbox met beslissingsbevoegdheden ingeschakeld. De rollen van de gebruiker provisioned met toegang tot het beheer van de puntcatalogus, de configuratie van de selectiestrategie, en het beleid van de kanaaloppervlakte. | [&#x200B; het overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [&#x200B; overzicht van de Toegangscontrole &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | Ervaar het gebeurtenisschema dat gedragssignalen (productmeningen, toe:voegen-aan-kart, aankopen, inhoudinteractie) met punt/productherkenningstekens vastlegt. Het catalogusschema van het punt (productattributen, categorieën, beelden, prijzen) voor de reeks van het aanbeveling punt. Profielschema met identiteitsvelden. Alle schema&#39;s ingeschakeld voor [!DNL Real-Time Customer Profile] . | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [&#x200B; de samenstellingsgrondbeginselen van het Schema &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition), [&#x200B; creeer een dataset &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create) |
| Gegevensbronnen en -verzameling | Vereist | Beleidsgebeurtenisstreaming in realtime via [!DNL Web SDK] of [!DNL Mobile SDK] is van essentieel belang — de aanbevolen kwaliteit hangt af van nieuwe gedragssignalen. Gegevens uit de itemcatalogus moeten worden ingevoerd (batch- of streaming). Gegevensstromen die met de dienst van AJO worden gevormd die voor de beslissing van Edge wordt toegelaten. | {het overzicht van SDK van het 0} Web [&#128279;](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [&#x200B; Mobiel overzicht van SDK &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [&#x200B; vorm gegevensstromen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identiteit en profielconfiguratie | Vereist | Gedragssignalen moeten worden gekoppeld aan een identiteit (bekend of anoniem via ECID) om gedragsprofielen te maken. Voor bekende-bezoekersaanbevelingen, voor authentiek verklaarde identiteit (identiteitskaart van CRM, e-mail) moet worden gevormd. Het beleid van de fusie actief op Edge voor aanbeveling in real time levering. | [&#x200B; overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [&#x200B; overzicht van het beleid van de Fusie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Auditiedefinitie en segmentatie | Aanbevolen | De doelgroepen kunnen worden gebruikt om aanbevelingen voor het toepassingsgebied op te stellen (bijvoorbeeld alleen om premiumproducten aan te bevelen) of om te filteren. Niet strikt vereist als aanbevelingen louter gedragsgericht zijn. Vereist voor op e-mail-gebaseerde aanbevelingen (Optie C) om het doelpubliek te bepalen. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [&#x200B; de gids UI van de Bouwer van het Segment &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League Reference |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Berekende kenmerken, zoals de affiniteitsscores voor categorieën, de interactiefrequentie voor producten, de kooprecentie en de totale uitgaven, verbeteren de kwaliteit van de aanbevolen rangschikking. [!DNL Customer AI] Propensiteitsscores kunnen de relevantie verder verbeteren door de aankoopwaarschijnlijkheid te voorspellen. | [&#128279;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [&#x200B; overzicht van de Klant AI van 0&rbrace; Berekende attributen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Gedragsgebeurtenisgegevens moeten een geschikt vervalbeleid hebben — relevantie van aanbevelingen neemt af met gegevens over nietsdoen. Het plaatsen van het beleid van de gegevenssetvervalsing op gedragsgebeurtenisdatasets verzekert versheid en beheert opslag. Met de handhaving van de toestemming wordt ervoor gezorgd dat gedragsgegevens op de juiste wijze worden gebruikt. | [&#x200B; Verlopen van de Dataset &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration), [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | De etiketten van de governance op gedragsgegevens verzekeren volgzaam gebruik van interactiegeschiedenis voor aanbevelingen. Vooral belangrijk wanneer gedragsgegevens browserpatronen, koopgeschiedenis of gezondheids-/financiële signalen van belang zijn. | [&#x200B; het beheer van Gegevens overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [&#x200B; overzicht van de gebruiksetiketten van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Bewaking en waarneming | Aanbevolen | De leveringslatentie van de aanbeveling, de terugvaltarieven, en de gezondheid van de inname van de puntcatalogus zouden moeten worden gecontroleerd. Waarschuwingen over fouten bij het innemen van gedragsgebeurtenissen en beslissingsfouten helpen de kwaliteit van aanbevelingen te handhaven. | [&#x200B; overzicht van de Inzichten van de Waarneming &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [&#x200B; het overzicht van Alarm &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Rapportage en analyse | Opgenomen | Rapportage van aanbevolen prestaties maakt deel uit van stap 4 van de functieketen. [!DNL Customer Journey Analytics] een analyse van de doeltreffendheid van aanbevelingen, het effect op de inkomsten en de prestaties op itemniveau op oppervlakken en segmenten geeft inzicht in de optimalisatie. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [&#x200B; overzicht van Analysis Workspace &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer] (AJO)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Besluitvorming | Instellingen van itemcatalogus en -selectiestrategie | Vorm puntcatalogi (besluitvormingspunten), selectiestrategieën met gedrag rangschikkende modellen, het filtreren regels, en fallback aanbevelingen |
| Kanaalconfiguratie | Kanaal- en oppervlakteconfiguratie | Leveringsoppervlakken configureren voor web (op code gebaseerde ervaringen), in-app, inhoudskaart of e-mailkanalen waar aanbevelingen worden weergegeven |
| Berichtontwerp | Configuratie van inhoud en levering | Ontwerpaanbeveling rendersjablonen, lay-outs voor itemweergave en personalisatie-expressies voor aanbevolen items |
| Rapportage en prestatieanalyse | Rapportage en optimalisatie | Houd de aanbeveling van de monitor doorklikken, omzetten, en opbrengstmetriek door inheemse rapporten van AJO en [!DNL Customer Journey Analytics] integratie |

### [!DNL Real-Time CDP] (RT-CDP)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Audience Scoping (Option C) | Evalueer publiekssegmenten die aan werkingsgebiedaanbevelingen worden gebruikt of bepaal de doelpopulatie voor e-mailaanbevelingscampagnes |
| Profielverrijking | Gedragingen Signaalverrijking | Verrijkt profielen met berekende kenmerken (categoriescore, interactiefrequentie) die de rangorde van aanbevelingen verbeteren |

## Vereisten

Voltooi het volgende voordat u begint met de implementatie:

- AJO-besluitvorming wordt ingericht en ingeschakeld in de doelsandbox
- [!DNL Web SDK] of [!DNL Mobile SDK] wordt geïmplementeerd en gedragsgebeurtenissen worden verzameld met product-/inhoudsidentificatoren
- Gegevens uit de product- of inhoudscatalogus kunnen worden ingevoerd (productnaam, categorie, prijs, afbeeldings-URL, beschikbaarheid)
- De schema&#39;s van de gedragsgebeurtenis omvatten punt/productherkenningstekens die met cataloguspunten verbinden
- DataStream wordt geconfigureerd met [!DNL Adobe Journey Optimizer] -service ingeschakeld (vereist voor Edge-besluitvorming)
- Het beleid Samenvoegen met `isActiveOnEdge: true` is geconfigureerd (vereist voor realtime aanbevelingen voor web en toepassingen)
- Voor e-mailaanbevelingen (Option C): oppervlak van e-mailkanaal is geconfigureerd en gevalideerd
- Voor e-mailaanbevelingen (Optie C): doelgroep wordt gedefinieerd en geëvalueerd

## Implementatieopties

De volgende opties beschrijven verschillende benaderingen voor het uitvoeren van gedragsaanbevelingen. Kies de optie die het beste aansluit bij uw kanaalvereisten en technische beperkingen.

### Optie A: Aanbevelingen in real time voor het web

**Best voor:** aanbevelingen van het product of van de inhoud op Web-pagina&#39;s — de pagina van het productdetail dwars-verkoopwidgets, homepage aanbeveling carrousels, gepersonaliseerde lijsten van de categoriepagina, en de verpersoonlijking van het onderzoeksresultaat.

**hoe het werkt:**

Gedragssignalen worden in real time via [!DNL Web SDK] verzameld wanneer bezoekers door de site bladeren. Elke paginaweergave, productinteractie of zoekquery wordt gestreamd naar AEP en is gekoppeld aan het profiel van de bezoeker (via ECID voor anonieme bezoekers of een geverifieerde identiteit voor bekende bezoekers). Wanneer een pagina met een aanbevolen oppervlak wordt geladen, vraagt [!DNL Web SDK] AJO om een beslissingsevaluatie via de [!DNL Edge Network] . De beslissingsengine evalueert het gedragsprofiel van de bezoeker op basis van de selectiestrategie, past waarderingslogica toe, filtert niet-subsidiabele items uit (al aangeschaft, niet beschikbaar) en retourneert de aanbevolen items.

Aanbevelingen worden op de pagina weergegeven via op code gebaseerde ervaringen of webkanaaloppervlakken. De rendering kan een carrousel, raster, widget voor één item of een aangepaste indeling zijn die in de aanbevolen sjabloon is gedefinieerd. Impressie- en klikgebeurtenissen worden automatisch teruggezet naar AEP voor prestatierapportage.

**Zeer belangrijke overwegingen:**

- Edge-beslissingen vereisen dat het fusiebeleid actief is op Edge
- De latentie van de aanbeveling hangt van [!DNL Edge Network] reactietijd (sub-500ms SLA voor enig-werkingsgebied verzoeken) af
- Anonieme bezoekers ontvangen aanbevelingen op basis van gedrag tijdens de sessie; bekende bezoekers profiteren van gedragsgeschiedenis tijdens verschillende sessies
- Koudstartbezoekers zonder gedragsgeschiedenis ontvangen fallback-aanbevelingen

**Voordelen:**

- Realtime verpersoonlijking die op gedrag in sessie wordt gebaseerd
- Tweede aanbeveling voor levering via [!DNL Edge Network]
- Werkt voor zowel anonieme als bekende bezoekers
- Automatische weergave en klik op bijhouden
- Geen paginaherladen vereist voor nieuwe aanbevelingen

**Beperkingen:**

- Edge-profielarchief bevat een subset van volledige profielkenmerken
- De complexe rangschikkingsmodellen met vele profielattributen kunnen hubzijevaluatie vereisen
- Vereist [!DNL Web SDK] implementatie met gedragsgebeurtenistracering

**Experience League:**

- [Aanbiedingen leveren met de Edge-API voor besluitvorming](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)
- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)

### Optie B: Aanbevelingen voor mobiele apps

**Best voor:** In-app productaanbevelingen, gepersonaliseerde inhoudsvoer, bericht-gedreven aanbevelingen, en mobiele handelservaringen.

**hoe het werkt:**

Gedragssignalen worden via [!DNL Mobile SDK] verzameld terwijl gebruikers met de app communiceren. Productweergaven, interacties met inhoud, zoekopdrachten en aankopen worden gestreamd naar AEP. Wanneer een scherm met een aanbevolen oppervlak wordt geladen, vraagt [!DNL Mobile SDK] om een beslissingsevaluatie. Aanbevelingen worden geleverd via berichten in de app, inhoudskaarten of ervaringen op basis van code in de mobiele app.

Inhoudskaarten zijn bijzonder geschikt voor het gebruik van aanbevolen toepassingen in mobiele apps, omdat ze een feed-achtige ervaring hebben die gebruikers naar eigen goeddunken kunnen doorbladeren. Berichten in de app kunnen worden gebruikt voor contextuele aanbevelingen die worden geactiveerd door specifieke gedragingen (bijvoorbeeld het weergeven van complementaire producten na het toevoegen van een artikel aan de winkelwagen).

**Zeer belangrijke overwegingen:**

- [!DNL Mobile SDK] moet worden geconfigureerd met gedragsgebeurtenistracering voor relevante interacties
- Inhoudskaarten bieden een aanhoudend aanbevolen oppervlak; in-app-berichten zijn letterlijk
- Offline gedragspatiëring vereist SDK-voorraadbeheer voor uitgestelde gebeurtenisverzending
- Update-cycli van App Store beïnvloeden hoe snel aanbevelingen voor het teruggeven van wijzigingen kunnen worden geïmplementeerd

**Voordelen:**

- Native mobiele ervaring met vloeiende, toepassingsgeïntegreerde aanbevolen rendering
- Inhoudskaarten bieden een permanente, bladerbare aanbevolen feed
- In-app-berichten maken contextuele, door gedrag geïnitieerde aanbevelingen mogelijk
- Gebruikt apparaatsignalen (locatie, gebruikspatronen van de app) voor verbeterde relevantie

**Beperkingen:**

- Vereist [!DNL Mobile SDK] bronnen voor integratie en ontwikkeling van apps
- Voor het renderen van wijzigingen zijn app-updates vereist (tenzij u code-gebaseerde ervaringen met servergestuurde lay-outs gebruikt)
- Offlineperioden zorgen voor tussenruimten in gedragssignaalverzameling

**Experience League:**

- [Overzicht van Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Optie C: Aanbevelingen betreffende e-mailgedrag

**het Best voor:** aanbevelingen van het Product in e-mailcampagnes — verlaten doorbladert e-mail met bekeken productaanbevelingen, post-aankoop dwars-verkoop e-mails, periodieke &quot;plukken voor u&quot;onderverdelingen, en re-engagement e-mails met gepersonaliseerde productsuggesties.

**hoe het werkt:**

De gegevens van het gedragsprofiel die van vorige zittingen worden verzameld informeren aanbeveling selectie bij e-mail verzendt tijd of geeft tijd terug. Er is een publiek gedefinieerd dat zich richt op de juiste ontvangers (bijvoorbeeld bezoekers die hebben gebladerd maar niet hebben aangeschaft, klanten die onlangs een aankoop hebben gedaan). Een campagne of reis wordt gevormd om een e-mail te verzenden die aanbevelingen plaatsing omvat. Bij het verzenden evalueert AJO Decisioning het gedragsprofiel van elke ontvanger op basis van de selectiestrategie en injecteert de aanbevolen items in de e-mailinhoud.

Deze optie is gebaseerd op de geaccumuleerde gedragsgeschiedenis in plaats van signalen tijdens de sessie. Berekende kenmerken (categoriescores, recente productweergaven, aankoopfrequentie) verbeteren de kwaliteit van aanbevelingen voor e-mail aanzienlijk omdat gedragsgeschiedenis wordt omgezet in signalen op profielniveau die de selectiestrategie efficiënt kan evalueren.

**Zeer belangrijke overwegingen:**

- E-mailaanbevelingen worden geëvalueerd tijdens het verzenden, niet tijdens het openen. De status van het gedragsprofiel op het moment van verzending bepaalt de aanbevelingen
- Gedetailleerde kenmerken worden ten zeerste aanbevolen om de kwaliteit van de classificatie te verbeteren
- Beperkingen voor weergave via e-mail (geen JavaScript, beperkte CSS) beperken aanbevolen weergaveindelingen
- Vereist een geconfigureerd en gevalideerd oppervlak voor e-mailkanalen

**Voordelen:**

- Gebruikt volledige gedragsgeschiedenis over zittingen voor diepere verpersoonlijking
- Integreert met bestaande campagne- en reisworkflows
- Geschikt voor terugzetprocedures en terugwinningsscenario&#39;s waarbij web-/app-aanraakpunten niet beschikbaar zijn
- Kan meerdere aanbevelingen opnemen in één e-mail

**Beperkingen:**

- Aanbevelingen zijn statisch tijdens het verzenden. Ze worden niet bijgewerkt wanneer het e-mailbericht wordt geopend
- Beperkingen voor rendering van e-mail beperken aanbevelingen voor weergave-indelingen
- Vereist publieksevaluatie en campagne-/reis-orkestinfrastructuur
- Hogere implementatiecomplexiteit als gevolg van extra afhankelijkheden (kanaalconfiguratie, definitie van het publiek, uitvoering van de campagne)

**Experience League:**

- [Een e-mail maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Optievergelijking

De volgende tabel geeft een overzicht van de belangrijkste verschillen tussen implementatieopties.

| Criteria | Option A: Web Real-Time | Optie B: Mobiele app | Optie C: Gedrag e-mail |
| --- | --- | --- | --- |
| Best voor | Aanbevelingen voor webpagina&#39;s (PDP, homepage, categorie) | Aanbevelingen en inhoudsfeeds in de app | E-mailcampagnes met productaanbevelingen |
| Gedragssignaalbron | In-session + cross-session ([!DNL Web SDK]) | Interacties in de app ([!DNL Mobile SDK]) | Gecumuleerde gedragsgeschiedenis (profiel) |
| Aanbevelingslatentie | Subseconde ([!DNL Edge Network]) | Subseconde ([!DNL Edge Network]) | Op verzendtijd (hubzijevaluatie) |
| Type bezoeker | Anoniem en bekend | Bekend (gebruikers van de app) | Bekend (e-mailontvangers) |
| Complexiteit | Gemiddeld | Medium-High | Hoog |
| Kanaalafhankelijkheid | [!DNL Web SDK], op code gebaseerd ervaringsoppervlak | [!DNL Mobile SDK], in-app/inhoudskaartoppervlak | E-mailkanaaloppervlak, publiek, campagne/reis |
| Vereisten | [!DNL Web SDK] -implementatie, samenvoegbeleid van Edge | [!DNL Mobile SDK] -implementatie, samenvoegbeleid van Edge | E-mailoppervlak, definitie van publiek, instellen van campagne |

### Kies de juiste optie

Gebruik de volgende richtlijnen om de beste optie voor uw situatie te selecteren:

- **Begin met Optie A** als uw primair doel productaanbevelingen in real time op uw website is. Dit is het meest gangbare uitgangspunt en biedt onmiddellijke waarde met de laagste complexiteit bij de implementatie.
- **kies Optie B** als uw mobiele app een primair betrokkenheidskanaal is en de aanbevelingen in-app zouden leiden tot een zinvolle conversie lichter. Optie B kan parallel lopen met optie A gebruikend de zelfde selectiestrategieën en puntcatalogi.
- **voeg Optie C** toe wanneer u gedragsaanbevelingen in e-mailcampagnes wilt uitbreiden. Deze laag wordt gewoonlijk boven op Option A of B geplaatst, gebruikend de zelfde puntcatalogi en selectiestrategieën maar met e-mailspecifieke het teruggeven malplaatjes en op publiek-gebaseerd richten.
- **combineer Opties A + C** voor een gemeenschappelijk patroon: Webaanbevelingen in real time voor actieve bezoekers, plus verlaten doorblader of post-aankoop e-mailaanbevelingen voor bezoekers die zonder het omzetten vertrekken.

## Uitvoeringsfasen

De volgende fasen begeleiden u door de implementatie van begin tot eind van gedragsaanbevelingen.

### Fase 1: gedragsgebeurtenisschema en gegevensverzameling configureren

**de Functie van de Toepassing:** AEP: De Modellering en Voorbereiding van gegevens (F2), AEP: Gegevensbronnen &amp; Inzameling (F3)

Deze fase vestigt de schema&#39;s XDM, datasets, en mechanismen van de gegevensinzameling die gedragssignalen en de gegevens van de puntcatalogus vangen. Dit gegevensfundament is waar alle aanbevelingen op gericht zijn.

#### Besluit: ontwerp van gedragsgebeurtenisschema

Welke gedragssignalen zouden aanbevelingen moeten drijven?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen productweergaven | Eenvoudige aanbevelingen voor cross-sell/upsell | Laagste implementatie-inspanning; beperkte signaaldiepte |
| Weergaven van producten en aankopen | Aanbevelingen met uitsluiting van aankopen en cross-sell-logica | Matige inspanning; laat &quot;reeds gekochte&quot;filtreren toe uitsluiten |
| Volledige gedragssuite (weergaven, aankopen, add-to-cart, zoekopdrachten, interactie met inhoud) | Geavanceerde aanbevelingen met multi-signaalclassificatie | Hoogste signaalkwaliteit; vereist uitvoerige [!DNL Web SDK]/[!DNL Mobile SDK] instrumentatie |

#### Besluit: methode voor het opnemen van objectcatalogi

Hoe wordt de product- of inhoudscatalogus in AEP opgenomen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Batchopname via bronaansluiting | Catalogusupdates zijn periodiek (dagelijks/wekelijks) | Eenvoudiger instellen; cataloguswijzigingen worden niet in real-time doorgevoerd |
| Streaming opname | Catalogus vereist updates in real time (prijsveranderingen, beschikbaarheid) | Complexer; zorgt ervoor dat de aanbevelingen de huidige inventaris weerspiegelen |
| Handmatig/API-upload | Kleine catalogus met niet vaak voorkomende wijzigingen | Eenvoudige installatie; niet schaalbaar voor grote of dynamische catalogi |

**navigatie UI:** het Beheer van Gegevens > Schema&#39;s > creeer schema; de Inzameling van Gegevens > Gegevensstromen > Nieuwe DataStream

**Zeer belangrijke configuratiedetails:**

- In het gebeurtenisschema van de ervaring moeten product-/item-id&#39;s (SKU, product-id, inhoud-id) zijn opgenomen voor de gebeurtenislading
- Het catalogusschema van items moet kenmerken bevatten die worden gebruikt voor filteren en rangschikken: categorie, prijs, afbeeldings-URL, beschikbaarheidsstatus, tags
- DataStream moet de [!DNL Adobe Journey Optimizer] -service hebben ingeschakeld voor Edge-besluitvorming
- [!DNL Web SDK] `sendEvent` aanroepen moeten productinteractiegegevens bevatten die zijn toegewezen aan XDM-handelsvelden

**documentatie van Experience League:**

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Een relatie tussen twee schema&#39;s definiëren](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Fase 2: Identiteit en profiel configureren

**de Functie van de Toepassing:** AEP: Identiteit &amp; de Configuratie van het Profiel (F4)

Deze fase plaatst omhoog identiteitsnamespaces, primaire identiteitsaanduidingen, en fusiebeleid dat ervoor zorgt dat de gedragssignalen correct met bezoekersprofielen en beschikbaar voor de levering van de aanbeveling in real time worden geassocieerd.

#### Besluit: Samenvoegingsbeleid voor Edge-besluitvorming

Moet in het geval van de aanbeveling Edge-evaluatie in real-time worden uitgevoerd?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Actief op samenvoegbeleid van Edge | Opties A en B (web en mobiele aanbevelingen in real time) | Vereist voor levering van subsecondenaanbevelingen; slechts één Edge-samenvoegbeleid per sandbox |
| Standaardsamenvoegbeleid (niet in Edge) | Alleen optie C (e-mailaanbevelingen geëvalueerd tijdens het verzenden) | Voldoende voor hubzijevaluatie; verbruikt niet de groef van het de fusiebeleid van Edge |

#### Beslissing: Anonieme versus bekende identiteit bezoeker

Hoe moeten gedragssignalen van anonieme bezoekers worden afgehandeld?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen ECID (anoniem) | Aanbevelingen voornamelijk voor anonieme bezoekers op basis van gedrag tijdens de sessie | Eenvoudiger instellen; geen continuïteit tussen verschillende sessies, tenzij bezoekers de instellingen verifiëren |
| ECID + geverifieerde identiteit (CRM-id, e-mail) | Aanbevelingen voor meerdere sessies voor bekende bezoekers met identiteitsstitching | Rijkere gedragsprofielen; vereist authentificatiestroom |
| Beide met identiteitsgrafiek die verbinding vormt | Volledige anonieme reis met identiteit stitching | Uitgebreid; vereist configuratie van regels voor identiteitskoppeling |

**navigatie UI:** Identiteiten > Identiteitsnamespaces; Profielen > het beleid van de Fusie

**Zeer belangrijke configuratiedetails:**

- ECID-naamruimte wordt vooraf geconfigureerd en automatisch gebruikt door [!DNL Web SDK] en [!DNL Mobile SDK]
- Aangepaste identiteitsnaamruimten (CRM-id, loyalty-id) moeten worden gemaakt voor geverifieerde identiteit
- Primaire identiteit in het gebeurtenisschema Experience moet worden ingesteld op ECID voor gedraggebeurtenissen voor web/mobiele apparaten
- Het beleid van de fusie moet Privé Grafiek van het Apparaat voor identiteit gebruiken stitching over apparaten

**documentatie van Experience League:**

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van naamruimten](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Koppelingsregels voor identiteitsgrafiek](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)

### Fase 3: Een itemcatalogus en selectiestrategie instellen

**Functie van de Toepassing:** AJO: Beslissing

Deze fase vormt de puntcatalogus (besluitvormingspunten), selectiestrategieën die gedragssignalen met puntattributen voor het rangschikken, het filtreren regels om niet in aanmerking komende punten uit te sluiten, en terugvalaanbevelingen voor koudstartprofielen combineren.

#### Besluit: bereik van itemcatalogus

Welke punten zijn beschikbaar voor aanbeveling?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Productcatalogus (e-commerce) | Aanbevolen fysieke of digitale producten voor aankoop | Objectkenmerken omvatten prijs, categorie, beschikbaarheid, afbeeldingen |
| Inhoudscatalogus (media/publiceren) | Artikelen, video&#39;s of trainingsmateriaal aanbevelen | Itemkenmerken zijn onderwerp, auteur, publicatiedatum, inhoudstype |
| Hybride catalogus | Aanbevelen voor zowel producten als inhoud | Vereist verenigd puntschema dat beide types omvat |

#### Besluit: Willekeurige aanpak

Hoe moeten in aanmerking komende items worden gerangschikt om de beste aanbevelingen te bepalen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Op basis van formule | Duidelijke bedrijfslogica voor rangschikking (bijvoorbeeld, sorteer door categorie affiniteitscore vermenigvuldigd met puntpopulariteit) | Transparante, controleerbare classificatie; vereist gedefinieerde waarderingsformule |
| Op AI-schaal (automatische optimalisatie) | Het leren van de machine zou optimale rangschikking op omzettingsgegevens moeten bepalen | Vereist minimaal 1.000 conversiegebeurtenissen voor modeltraining; minder transparant |
| Op prioriteit gebaseerd (handleiding) | Eenvoudige, handmatig beheerde aanbevolen volgorde | Gemakkelijk te vormen; past zich niet aan individueel gedrag aan |

#### Besluit: Filtervoorschriften

Welke punten zouden van aanbevelingen moeten worden uitgesloten?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Reeds gekochte objecten uitsluiten | Aanbevelingen voor cross-sell en detectie | Vereist een aankoopgeschiedenis in gedragsprofiel |
| Exclusief posten buiten de voorraad | Handel met dynamische inventaris | Vereist real-time of bijna-real-time catalogusupdates |
| Eerder verwijderde items uitsluiten | Aanbevelingen voor inhoud waarin gebruikers suggesties kunnen negeren | Vereist dat gedragsgebeurtenissen worden gevolgd bij ontslag |
| Categoriebereik filteren | Aanbevelingen beperkt tot specifieke categorieën | Gebruikt itemkenmerken voor filteren |

#### Besluit: Koudstartstrategie

Wat moet worden getoond voor nieuwe bezoekers zonder gedragsgeschiedenis?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Populaire objecten (wereldwijde bestsellers) | Algemene fallback | Eenvoudig te onderhouden; niet gepersonaliseerd |
| Rubriekspecifieke populaire objecten | Bezoeker is aangekomen op een rubriekpagina | Contextueel relevante fallback; vereist paginacontext |
| Gekrulde redactionele selectie | Brand wil redactionele controle over koudstartervaring | Vereist handmatige kromming en updates |
| Trending items (tijdgewogen populariteit) | Dynamische fallback die de huidige trends weerspiegelt | Vereist trending signaalberekening |

**navigatie UI:** [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Besluiten; [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Aanbiedingen; [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Plaatsingen

**Zeer belangrijke configuratiedetails:**

- Beslissingsitems maken die elk product of inhoudsitem in de catalogus vertegenwoordigen, met kenmerken (categorie, prijs, afbeeldings-URL, tags)
- Definieer selectiestrategieën die het filteren van de itemcatalogus combineren met logica voor gedragsrangschikking
- Classificatiemodellen configureren — op formule gebaseerde expressies kunnen verwijzen naar profielkenmerken (bijvoorbeeld categoriaffiniteitscores van berekende kenmerken)
- Maak fallback-aanbiedingen/items die als standaardaanbevelingen voor koudstartprofielen dienen
- Items in verzamelingen indelen met behulp van verzamelingsaanduidingen (tags) voor logische groepering
- Opstelling het filtreren regels binnen selectiestrategieën om bedrijfsregels (exclusief gekochte, in voorraad slechts) af te dwingen

**documentatie van Experience League:**

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Plaatsingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Beslissingsregels maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Alternatieve aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Verzamelingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 4: Kanaal en oppervlak configureren

**Functie van de Toepassing:** AJO: De Configuratie van het Kanaal

Deze fase vormt de leveringsoppervlakten waar de aanbevelingen zullen worden teruggegeven. De configuratie varieert aanzienlijk per implementatieoptie.

#### Besluit: Type leveringsoppervlak

Waar worden aanbevelingen weergegeven?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Code-gebaseerde ervaring (web) | Widget aanbevelingen op webpagina&#39;s met aangepaste rendering | Maximale flexibiliteit voor renderen; vereist front-end ontwikkeling |
| Webkanaaloppervlak | Standaardoppervlak voor webpersonalisatie | Gebruikt AJO-webontwerper; minder flexibel dan op code gebaseerd |
| Bericht in de app | Contextuele aanbevelingen die worden geactiveerd door het gedrag van de app | Ephemeral; verdwijnt na interactie of ontslag |
| Inhoudskaart (mobiel) | Aanhoudende aanbevolen feed in mobiele app | Blijft tot de gebruiker werkt; browserervaring |
| E-mail | Productaanbevelingen ingesloten in e-mailcampagnes | Statisch bij verzendtijd; afhankelijk van weergavebeperkingen voor e-mail |

**waar de opties uiteenlopen:**

**voor Optie A (Echte het Web - tijd Aanbevelingen):**
Configureer een op code gebaseerd ervaringsoppervlak of een webkanaaloppervlak. Codegebaseerde ervaringen bieden de meeste flexibiliteit voor het renderen van aangepaste aanbevelingen (carrousels, rasters, itemkaarten). De oppervlakte-URI identificeert waar op de paginaaanbevelingen verschijnen.

**voor Optie B (Mobiele Aanbevelingen van de Toepassing):**
Vorm in-app bericht of inhoudskaartoppervlakken. Inhoudskaarten worden aanbevolen voor doorlopende aanbevelingen. Berichten in de app werken goed voor contextuele, door gedrag gestuurde aanbevelingen.

**voor Optie C (de Aanbevelingen van het Gedrag E-mail):**
Vorm een oppervlakte van het e-mailkanaal met subdomain delegatie, IP pooltoewijzing, en afzendermontages. Zorg ervoor dat het oppervlak gevalideerd is voor de te leveren items.

**navigatie UI:** Beleid > Kanalen > de oppervlakten van het Kanaal > Create oppervlakte

**documentatie van Experience League:**

- [Kanaaloppervlakken instellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Fase 5: Inhoud en levering configureren

**Functie van de Toepassing:** AJO: De Authoring van het bericht

Deze fase bepaalt de aanbeveling die malplaatjes teruggeeft die controleren hoe de geadviseerde punten aan de bezoeker worden getoond. Dit omvat ontwerp van de puntlay-out, verpersoonlijkingsuitdrukkingen die puntattributen (naam, beeld, prijs, verbinding) trekken, en het algemene ontwerp van de aanbeveling ervaren.

#### Besluit: Weergaveformaat aanbeveling

Hoe moeten aanbevolen items worden gerenderd?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Carousel (horizontaal schuiven) | Homepage of categoriepagina met beperkte verticale ruimte | Vertrouwd UX-patroon; geeft meerdere items weer in een compacte ruimte |
| Raster (meerdere rijen) | Sectie met specifieke aanbevelingen met ruim beschikbare ruimte | Hiermee geeft u meer items tegelijk weer. Dit werkt goed voor secties die u &quot;aanbevolen&quot; hebt. |
| Widget van één item | Contextuele aanbeveling op een specifieke paginalocatie (bijvoorbeeld zijbalk) | Minimale voetafdruk; plaatsing met hoge impact |
| Inline-e-mailblok | Aanbevelingen ingesloten in hoofdtekst van e-mail | Beperkt tot HTML/CSS-e-mail; doorgaans 2-4 items |

#### Besluit: Aantal weer te geven aanbevelingen

Hoeveel punten zou de beslissing per plaatsing moeten terugkeren?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| 3-4 items | Standaardwidget voor aanbevelingen | Balancering relevantie met visuele dichtheid |
| 6-8 items | Carrousel met schuiven of rasterlay-out | Meer opties voor de bezoeker; vereist voldoende catalogusdiepte |
| 1 item | Contextuele aanbeveling voor één product | Hoogste invloed op relevantie; eenvoudigste rendering |
| 10+ items | Aanbevolen voedingsstijl | Gebruiksscenario&#39;s met veel inhoud (media, publiceren) |

**waar de opties uiteenlopen:**

**voor Optie A (Echte het Web - tijd Aanbevelingen):**
Ontwerp de aanbeveling die gebruikend code-gebaseerde ervaringsmalplaatjes teruggeeft. Gebruik HTML/CSS/JavaScript om de carrousel-, raster- of widgelay-out te maken. Personalization-expressies verwijzen naar de kenmerken van de besluitreactie (naam, afbeeldings-URL, prijs, product-URL). Indrukken en klikken bijhouden worden automatisch afgehandeld door de [!DNL Web SDK] .

**voor Optie B (Mobiele Aanbevelingen van de Toepassing):**
Configureer inhoudskaart of berichtsjablonen in de app met de logica voor de itemweergave. Gebruik op JSON gebaseerde inhoudsstructuren die de mobiele app native rendert. Voeg diepe koppelingen toe voor elk aanbevolen item.

**voor Optie C (de Aanbevelingen van het Gedrag E-mail):**
Ontwerp e-mailinhoud met de e-mailtoepassing Designer. Voeg aanbevelingen toe met behulp van besluitvormende inhoudsblokken. Vorm verpersoonlijkingsuitdrukkingen voor puntattributen binnen het e-mailmalplaatje. De onderwerpregel kan verwijzing naar hoogste geadviseerde punten.

**navigatie UI:** Inhoudsbeheer > de Malplaatjes van de Inhoud; Campagne/Reis > geeft inhoud uit > E-mail Designer

**Zeer belangrijke configuratiedetails:**

- Elke plaatsing van de aanbeveling moet verwijzen naar het besluit dat in Fase 3 is genomen
- Personalization-expressies gebruiken Handlebars-syntaxis om itemkenmerken te renderen
- Voor Web: vorm de op code-gebaseerde ervaring om het besluit te roepen en de reactie terug te geven
- Voor e-mail: sluit het besluit in de e-mailactie binnen de campagne of reis in
- Aanbevelingen voorvertonen met testprofielen met bekende gedragsgeschiedenis

**documentatie van Experience League:**

- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Fase 6: publieksbereik en campagne/reis instellen (alleen optie C)

**Functie van de Toepassing:** rt-CDP: De Evaluatie van het publiek, AJO: De Uitvoering van de campagne of Journey Orchestration

Voor op e-mail-gebaseerde aanbevelingen (Optie C), bepaalt deze fase het doelpubliek en vormt de campagne of de reis die de aanbeveling e-mail levert. De opties A en B slaan deze fase over omdat de aanbevelingen in echt - tijd bij pagina/het schermlading worden geleverd.

#### Besluit: Methode voor de evaluatie van het publiek

Hoe moet het doelpubliek voor e-mails met aanbevelingen worden geëvalueerd?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Batchevaluatie | Geplande e-mailcampagnes voor aanbevelingen (dagelijkse, wekelijkse samenvatting) | voorspelbare verzendtiming; publiek geëvalueerd vóór verzending |
| Streaming evaluatie | E-mails met aanbevelingen die door gebeurtenissen worden geactiveerd (opgegeven browse, post-purchase) | Near-real-time publiekskwalificatie; paren met reis orchestratie |

#### Besluit: Leveringsmechanisme

Moet de e-mail worden bezorgd via een campagne of een reis?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Geplande campagne | Eenmalige of terugkerende aanbevelingen worden via e-mail verzonden naar een bepaald publiek | Eenvoudiger instellen; batchpublieksevaluatie en verzenden |
| Reis met kijkvermelding | E-mails met aanbevelingen die worden geactiveerd door de kwalificatie van het publiek | Hiermee schakelt u meerstapsstromen in (bijv. via een e-mail met aanbevelingen gevolgd door een herinnering) |
| Door gebeurtenissen geïnitieerde reis | Aanbevelingen die via e-mail worden geactiveerd door een specifieke gebeurtenis (gebladerde, aanschaf) | Real-time triggermodus; vereist gebeurtenisgebaseerde toegang tot de reis |

**navigatie UI:** Klant > Soorten publiek > leidt tot publiek > de regel van de Bouwstijl; Campagnes > creeer campagne; De Schavens > creëren reis

**Zeer belangrijke configuratiedetails:**

- Bepaal het doelpubliek gebruikend de uitdrukkingen van de segmentregel die op gedragsgeschiedenis verwijzen (b.v. &quot;bekeken producten in de afgelopen 7 dagen maar niet gekocht&quot;)
- Vorm de campagne of de reis met de e-mailactie die de kanaaloppervlakte van Fase 4 van verwijzingen voorzien
- Het besluit uit fase 3 insluiten in de e-mailinhoud
- Plaats het plannen en de frequentieregels om over overseinen te vermijden

**documentatie van Experience League:**

- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Campagne live-rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)

### Fase 7: Rapportage en optimalisatie configureren

**Functie van de Toepassing:** AJO: Rapportering &amp; Analyse van Prestaties, S5: Rapportering &amp; Analyse

Deze fase vestigt prestatiescontrole voor aanbeveling klikthrough, omzetting, en opbrengstmetriek. Het creëert de rapportinfrastructuur om de doeltreffendheid van aanbevelingen te meten en optimaliseringsmogelijkheden te identificeren.

#### Besluit: rapportagediepte

Welk niveau van rapporteringsanalyse is nodig?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen systeemeigen AJO-rapporten | Standaardprestatiebewaking voor aanbevelingen | Snel instellen; beperkt tot door AJO bijgehouden gegevens |
| AJO + [!DNL Customer Journey Analytics] integratie | Effectanalyse en inkomstentoewijzing voor kanaaloverschrijdende aanbevelingen | Vereist [!DNL Customer Journey Analytics] verbinding en gegevensweergave; biedt meer inzicht |
| Volledige [!DNL Customer Journey Analytics] werkruimte met aangepaste dashboards | Doorlopende optimalisatieprogramma met item-level, segment-level, en oppervlakte-vlakke analyse | Uitgebreid; vereist [!DNL Customer Journey Analytics] expertise en installatie |

**navigatie UI:** Campagnes > de Uitgezochte campagne > Alle tijdrapport; De reizen > Uitgezochte reis > Alle tijdrapport; [!DNL Customer Journey Analytics] > Projecten > Nieuw project creëren

**Zeer belangrijke configuratiedetails:**

- AJO campagne- en reisrapporten voor levering en betrokkenheid bekijken
- Voor [!DNL Customer Journey Analytics] integratie maakt u een verbinding met gegevenssets voor ervaringen met AJO-ervaringen (Berichtfeedback, E-mailtracking, besluitvorming)
- Maak een [!DNL Customer Journey Analytics] gegevensweergave met aanbevelingen (itemnaam, itemcategorie, aanbevolen oppervlak) en metriek (afbeeldingen, klikken, conversies, inkomsten)
- Berekende maatstaven maken voor aanbeveling CTR, conversiekoers en inkomsten per indruk
- Deelvensters in de werkruimte [!DNL Customer Journey Analytics] maken waarin de prestaties van aanbevelingen voor oppervlakken, segmenten en tijdsperioden worden vergeleken

**documentatie van Experience League:**

- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Verbinding maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Een gegevensweergave maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Overzicht van berekende metriek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

## Implementatieoverwegingen

Bekijk de volgende instructies, valkuilen, beste praktijken en compromissen voor en tijdens de implementatie.

### Guardrails en limieten

- Maximum van 10.000 goedgekeurde gepersonaliseerde aanbiedingen (besluitvormingspunten) per zandbak - [&#x200B; de guardrails van het Beheer van het Besluit &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximaal 30 stages per besluit
- Maximaal 30 verzamelingsbereiken per beslissingsverzoek
- Aanbieding leveringstijd SLA: minder dan 500 ms bij P95 voor Edge-aanvragen met één bereik
- Voor AI-classificatiemodellen is een minimum van 1.000 conversieevenementen vereist voor training
- Aanbiedings het begrenzen tellers kunnen een vertraging van tot een paar seconden in hoge productiescenario&#39;s hebben
- Edge-beslissingen zijn beperkt tot profielkenmerken die beschikbaar zijn in de winkel met randprofielen
- Slechts één samenvoegingsbeleid kan op Edge per zandbak actief zijn - [&#x200B; de gidsen van het Profiel &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum van 25 actieve gegevens verwerkte attributen per zandbak — [&#x200B; verwerkte attributengidsen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- Maximum van 4.000 segmentdefinities per zandbak - [&#x200B; de gidsen van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Streaming opname: maximum 20.000 verslagen per seconde per verbinding van HTTP - [&#x200B; Ingestiegeldrails &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Veelvoorkomende valkuilen

- **het Besluit keert slechts reservepunten terug:** verifieer dat de gepersonaliseerde besluitvormingspunten, binnen hun waaier van de geldigheidsdatum worden goedgekeurd, en dat de geschiktheidsregels de het profielattributen van de bezoeker aanpassen. Controleer of de plafondlimiet niet is bereikt.
- **de levering van Edge keert lege verpersoonlijking terug:** zorg ervoor de gegevensstroom met de [!DNL Adobe Journey Optimizer] toegelaten dienst wordt gevormd en dat het beslissingswerkingsgebied correct in het [!DNL Web SDK] verzoek wordt geformatteerd.
- **het Rangschikken formule niet toegepast:** verifieer dat de formule syntactisch geldig is en verwijzingen toegankelijke profielattributen. Formulatiefouten vallen zonder meer terug op prioriteitsclassificatie.
- **de aanbevelingen van de Schaal:** als gedragsgebeurtenisgegevens niet in echt stromen - tijd, zullen de aanbevelingen op verouderde gedragsprofielen worden gebaseerd. Controleer of [!DNL Web SDK] of [!DNL Mobile SDK] actief streaming gebeurtenissen is.
- **Cold-start fallback tarief is te hoog:** als een groot percentage bezoekers fallback aanbevelingen ontvangt, denk na verrijkend de koudstartstrategie met contextuele signalen (huidige paginacategorie, verwijzingsbron) eerder dan het baseren uitsluitend op gedragsgeschiedenis.
- **Aanbevelingen die niet op pagina teruggeven:** verifieer dat de op code-gebaseerde de ervaringsoppervlakte URI het patroon van pagina URL aanpast en dat [!DNL Web SDK] correct om de besluitreactie verzoekt en teruggeeft.
- **de punten van de Catalogus missen van aanbevelingen:** zorg ervoor alle cataloguspunten als besluitvormingspunten zijn opgenomen, geëtiketteerd met de correcte inzamelingsbepalers, en inbegrepen in de aangewezen inzamelingen die door de selectiestrategie van verwijzingen worden voorzien.

### Aanbevolen procedures

- Begin met een op formule gebaseerd rangordemodel met behulp van berekende kenmerken (categorievijnheid, interactierente) voordat u in op AI gerangschikte modellen investeert. Op formule-gebaseerde modellen zijn transparant, controleerbaar, en verstrekken een stevige basislijn voor vergelijking.
- Importeer de indruk en klik vanaf de eerste dag op Tekstspatiëring. Zonder interactiegegevens kunnen AI-classificatiemodellen niet trainen en u kunt de doeltreffendheid van aanbevelingen niet meten.
- Maak afzonderlijke selectiestrategieën voor verschillende aanbevolen oppervlakken (homepage, PDP, e-mail) in plaats van één strategie overal opnieuw te gebruiken. Verschillende oppervlakken hebben verschillende gebruikersinzichten.
- Gebruik berekende kenmerken om de gedragsgeschiedenis om te zetten in classificatiesignalen. Onbewerkte gebeurtenisgegevens zijn te korrelig voor een effectieve op formule gebaseerde rangschikking; geaggregeerde signalen zoals &quot;categoriaffiniteitsscore&quot; en &quot;dagen sinds laatste aankoop&quot; zijn effectiever.
- De aanbevelingen van de testreserve los van gepersonaliseerde aanbevelingen. Zorg ervoor dat de terugvalitems van hoge kwaliteit zijn en de standaardwaarden die geschikt zijn voor het merk, zorgen voor een goede ervaring voor nieuwe bezoekers.
- Controleer de fallbacksnelheid bij koude start als een belangrijke maatstaf voor de gezondheid. Een afnemende fallbacksnelheid in de loop der tijd geeft een toenemende gedragsdekking aan.
- Voor e-mailaanbevelingen verzendt het programma op momenten dat het gedragsprofiel het volledigst is (bijvoorbeeld na piekbladeruren, niet tijdens hen).

### Handelsbesluiten

De volgende compromissen moeten op basis van uw specifieke vereisten worden beoordeeld.

#### Realtime signalen vs. geaccumuleerde geschiedenis

Gedragssignalen tijdens sessies bieden onmiddellijke relevantie maar hebben een beperkte diepte. De geaccumuleerde gedragsgeschiedenis verstrekt diepte maar kan stuitend zijn. Het evenwicht tussen deze bronnen beïnvloedt de kwaliteit van de aanbevelingen.

- **Optie A gunt:** signalen in real time voor directe relevantie, die door geaccumuleerde geschiedenis voor bekende bezoekers wordt aangevuld
- **Optie C gunt:** Gecumuleerde geschiedenis uitsluitend, aangezien de e-mails asynchroon worden verzonden
- **Aanbeveling:** voor Web en mobiel (Opties A, B), combineer in-zittingssignalen met gegevens verwerkte attributen die uit historisch gedrag worden afgeleid. Voor e-mail (Optie C), investeer zwaar in gegevens verwerkte attributen die gedragsgeschiedenis in actionable profiel-vlakke signalen samenvatten.

#### Op basis van formule versus modellen met een AI-classificatie

Op formule gebaseerde rangschikking is transparant en onmiddellijk. Op AI gerangschikte modellen passen zich automatisch aan, maar vereisen trainingsgegevens en bieden minder zichtbaarheid bij rangschikkingsbesluiten.

- **op formule-Gebaseerde gunsten:** Transparantie, controleerbaarheid, directe plaatsing, en gealigneerde bedrijfscontrole over rangschikkende logica
- **AI-gerangschikte voorkeur:** Geautomatiseerde optimalisering, ontdekking van niet voor de hand liggende patronen, en verminderde handmatige het stemmen inspanning
- **Aanbeveling:** Begin met op formule-gebaseerde rangschikking om een prestatiesbasislijn te vestigen en omzettingsgegevens te accumuleren. De overgang naar modellen met de AI-classificatie zodra u voldoende trainingsgegevens hebt (1.000+ conversiegebeurtenissen) en u wilt verder optimaliseren dan wat handmatige regelafstelling kan bereiken.

#### Rapportage van aanbevelingen versus relevantie

Door de itemcatalogus uit te breiden en de filterregels te versoepelen wordt het percentage aanvragen dat gepersonaliseerde aanbevelingen ontvangt, verhoogd, maar kan de relevantie voor een aanbeveling afnemen.

- **Hoge dekking gunst:** Maximaliserend het aantal bezoekers die gepersonaliseerde aanbevelingen zien; nuttig wanneer het primaire doel overeenkomst is
- **Hoge relevantie gunst:** die slechts hoogst relevante punten tonen, zelfs als het betekent meer bezoekers terugvalaanbevelingen zien; nuttig wanneer het primaire doel omzetting is
- **Aanbeveling:** Begin met gematigd filtreren (sluit aangekochte punten, uit-van-voorraad punten) uit en controleer zowel fallback tarief als omzettingspercentage. Verbeter filterregels slechts als de omzettingsgegevens het steunen.

#### Personalization-diepte versus complexiteit van implementatie

Betere gedragssignalen en meer geavanceerde rangordemodellen verbeteren de kwaliteit van aanbevelingen, maar verhogen de complexiteit van de implementatie en de onderhoudsbelasting.

- **Eenvoudige implementatie gunt:** Snellere tijd aan waarde, lager onderhoud, gemakkelijker om te zuiveren en te herhalen
- **diepere verpersoonlijking gunt:** Hogere omzettingslift, betere klantenervaring, concurrerende differentiatie
- **Aanbeveling:** voer in fasen uit. Begin met de signalen van de productmening en op formule-gebaseerde rangschikking (Fase 1). Berekende kenmerken toevoegen voor verrijking van gedrag (fase 2). Evalueer modellen met een AI-classificatie zodra de basis rijp is en er voldoende trainingsgegevens beschikbaar zijn (fase 3).

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie over de technologieën en mogelijkheden die in dit patroon worden gebruikt.

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
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [Aanbiedingen leveren met de Edge-API voor besluitvorming](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/api/offer-delivery-api/edge-decisioning-api)

### Gegevensverzameling en Web/Mobile SDK

- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Web SDK installeren](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Overzicht van Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Overzicht Edge Network Server API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### XDM en gegevensmodellering

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Een gegevensset maken](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/create)
- [Een relatie tussen twee schema&#39;s definiëren](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/relationship-api)

### Identiteit en profiel

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van naamruimten](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Overzicht van het realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Splitsen en segmenteren

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Berekende kenmerken en profielverrijking

- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Gebruikershandleiding voor berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [AI-overzicht van klant](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Kanaalconfiguratie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Kanaaloppervlakken instellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)

### Authoring en personalisatie van berichten

- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)

### Rapportage en analyse

- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [CJA-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Overzicht van berekende metriek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)

### Beheer van gegevens en levenscyclus

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Overzicht van labels voor gegevensgebruik](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Overzicht van geavanceerd gegevenslevenscyclusbeheer](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Verlopen gegevensset](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration)

### Controle en waarneming

- [Overzicht van observatiegegevens](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)

### Beveiligingsmechanismen

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Ingestiegrepen](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Identiteitsservicehandleidingen](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)

### Zelfstudies en hulplijnen

- [Overzicht van bronnen](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Overzicht van codes](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)
- [Toestemming en voorkeuren, veldgroep](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
