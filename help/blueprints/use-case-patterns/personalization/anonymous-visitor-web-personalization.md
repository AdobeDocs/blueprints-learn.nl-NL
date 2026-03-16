---
title: Anonieme bezoeker van Web Personalization
description: Leer hoe u persoonlijke webinhoud kunt leveren aan niet-geïdentificeerde bezoekers op basis van gedragssignalen tijdens de sessie.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '8076'
ht-degree: 0%

---


# Anonieme webpersonalisatie voor bezoekers

Dit referentieplan biedt implementatierichtlijnen voor het leveren van gepersonaliseerde webinhoud aan anonieme (niet-geïdentificeerde) bezoekers op basis van gedragssignalen tijdens de sessie. Het bestrijkt de volledige levenscyclus van de implementatie — van [!DNL Web SDK] configuratie en randpublieksdefinitie tot levering van inhoud en prestatierapportering — en is ontworpen voor oplossingsarchitecten, marketingtechnologen en implementatietechnici die werken met [!DNL Adobe Journey Optimizer] (AJO), [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP) en [!DNL Adobe Experience Platform] (AEP).

Gebruik dit plan om de architectuur te begrijpen, implementatieopties te evalueren, geïnformeerde configuratiebesluiten te nemen, en van de relevante documentatie van Experience League voor elke fase van implementatie de plaats te bepalen.

Het patroon werkt met beperkte gegevens — alleen wat kan worden waargenomen in de huidige sessie en elk anoniem randprofiel dat is verzameld bij eerdere bezoeken met hetzelfde apparaat of cookie. Dit maakt het geschikt voor top-of-funnel personalisatie waar de bezoeker geen rekening heeft of niet voor authentiek verklaard.

## Hoofdlettergebruik

Anonieme bezoeker Web Personalization richt zich op de zakelijke behoefte om relevante, gepersonaliseerde inhoud te leveren aan websitebezoekers die nog niet zijn geïdentificeerd — ze hebben zich niet aangemeld, hebben geen bekende identiteit en kunnen niet worden opgelost in een gezamenlijk klantprofiel. Ondanks deze beperking is een zinvolle personalisatie mogelijk met gedragssignalen tijdens de sessie: weergegeven pagina&#39;s, weergegeven tijd op locatie, schuifdiepte, verwijzingsbron, geografische locatie, apparaattype en UTM-campagneparameters.

Dit patroon gebruikt AJO-oppervlakken van webkanalen en code-gebaseerde ervaringen om pagina-inhoud in real-time te wijzigen. De segmentatie van Edge is de primaire evaluatiemethode aangezien de besluiten met sub-second latency moeten worden genomen aangezien de bezoeker de plaats navigeert. [!DNL Web SDK] verzamelt gedragssignalen en verzendt hen naar [!DNL AEP Edge Network], waar de rand-beoordeelde publieksregels bepalen welke inhoudvariant om te leveren.

In tegenstelling tot bekende-bezoeker Web/app verpersoonlijking, die het volledige verenigde profiel en segmentlidmaatschap gebruikt, wordt dit patroon beperkt tot gegevens waarneembaar in de huidige zitting en om het even welk anoniem randprofiel verbonden aan ECID van de bezoeker ([!DNL Experience Cloud ID]). Dit onderscheid is essentieel voor implementatieplanning: de gedragssignalen die beschikbaar zijn voor personalisatie zijn beperkt tot wat de [!DNL Web SDK] vastlegt en wat er in de opslag van het randprofiel blijft bestaan over sessies via de op cookie gebaseerde ECID.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

**[de websiteovereenkomst van de verhoging](../../business-objectives/acquisition-growth/increase-website-engagement.md)**

Verbeter de tijd op de site, de pagina&#39;s per sessie en de interactie met webinhoud door relevante ervaringen op maat van anonieme bezoekerssignalen.

| KPI&#39;s |
| --- |
| Tijd op (webpagina) |
| Betrokkenheid |
| Omrekeningskoers |

**[lever gepersonaliseerde klantenervaringen](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Inhoud, aanbiedingen en berichten op maat maken voor individuele voorkeuren, gedrag en levenscyclusfase, zelfs voor bezoekers die zich nog niet hebben geïdentificeerd.

| KPI&#39;s |
| --- |
| Betrokkenheid |
| Omrekeningskoers |
| Klanttevredenheid (CSAT) |

**[de omzettingspercentages van de Verhoging](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Verbeter het percentage bezoekers en de vooruitzichten die de gewenste acties zoals aankopen, inschrijven of het indienen van formulieren voltooien door de meest relevante inhoud te presenteren op basis van gedragscontext.

| KPI&#39;s |
| --- |
| Omrekeningskoers |
| Loodconversie |
| Kosten per lead |

## Voorbeelden van tactische gebruiksgevallen

In de volgende voorbeelden worden specifieke scenario&#39;s geïllustreerd waarop dit patroon kan worden toegepast.

- **het Bestaan van paginakoppen A/B test die op verwijzingsbron** wordt gebaseerd — Test verschillende koppen voor bezoekers die van Google, sociale media, of direct verkeer aankomen om betrokkenheid door verwervingskanaal te optimaliseren
- **de affiniteitaanbevelingen van de Categorie die op bladergedrag** worden gebaseerd — het product of de inhoudaanbevelingen van de vertoning die op pagina&#39;s worden gebaseerd die in de huidige zitting worden bekeken om ontdekking en omzetting te verhogen
- **Uitgang-intent aanbieding voor bezoekers op het punt om** te verlaten — presenteer een promotieaanbieding of lood vangen vorm wanneer de gedragssignalen erop wijzen de bezoeker op het punt staat de plaats te verlaten
- **Geo-gerichte promotionele banner** — toon plaats-specifieke promoties, opslag locatorinhoud, of regionale aanbiedingen die op de geografische plaats van de bezoeker worden gebaseerd
- **apparaat-specifieke optimalisering van de inhoudslay-out** — Pas inhoudslay-out, beeldgrootte, en plaatsing aan CTA die op wordt gebaseerd of de bezoeker op Desktop, tablet, of mobiel is
- **Nieuw vs. het terugkeren van bezoeker welkome overseinen** — Verschil de ervaring voor eerste bezoekers tegenover het terugkeren van anonieme bezoekers die ECID persistentie over zittingen gebruiken
- **aanbevelingen van de Inhoud die op bekeken pagina&#39;s in huidige zitting** worden gebaseerd — dynamisch oppervlaktegerelateerde artikelen, producten, of middelen die op de pagina&#39;s worden gebaseerd de bezoeker reeds heeft bekeken
- **Dynamische heldenbanner die op UTM campagneparameters** wordt gebaseerd — Personaliseer de heldenbanner om het overseinen of creatief van de verwijzende campagne aan te passen

## Kernprestatie-indicatoren

Gebruik de volgende KPIs om de doeltreffendheid van dit gebruiks gevalpatroon te meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Personalization-immuniteitssnelheid | Percentage subsidiabele paginaweergaven waarvoor gepersonaliseerde inhoud is geleverd | AJO-campagnerapport: afbeeldingen/totaal aantal paginaweergaven |
| Doorkliksnelheid (CTR) | Percentage gepersonaliseerde inhoudstafbeeldingen dat in een klik resulteert | AJO-campagnerapport: klikken/indrukken |
| Betrokkenheid opheffen | Tijdsverhoging op pagina, pagina&#39;s per zitting, of roldiepte voor gepersonaliseerde versus standaardinhoud | CJA-werkruimte vergelijken: gepersonaliseerde cohort versus controle |
| Conversiesnelheid | Percentage bezoekers dat wordt blootgesteld aan persoonlijke inhoud die een gewenste actie uitvoert | CJA funnel-analyse: impressie > interactie > conversie |
| Korting op stuitsnelheid | Sessies van één pagina minder maken voor bezoekers die persoonlijke inhoud ontvangen | CJA-sessieanalyse: Bounce rate delta voor persoonlijke versus standaard |
| Win-snelheid experimenten | Percentage A/B-tests dat een statistisch significante winnaar produceert | Verslag over het AJO-experiment: experimenten die de betrouwbaarheidsdrempel bereiken |

## Hoofdletterpatroon gebruiken

Hieronder worden het kernpatroon en de functieketen voor dit gebruik beschreven.

**Anonieme Personalization van het Web van de Bezoeker**

Aangepaste inhoud leveren op basis van gedragssignalen tijdens de sessie voor niet-geïdentificeerde bezoekers via het AJO-webkanaal.

**de ketting van de Functie:** Configuratie van het Oppervlak van het Web > de Evaluatie van de Regel van het Gedrag > Inhoudslevering > het Volgen van de Indrukking > het Melden

## Applicaties

In dit gebruikspatroon worden de volgende toepassingen gebruikt.

- **[!DNL Adobe Journey Optimizer] (AJO)** — de configuratie van het het kanaaloppervlak van het Web, inhoud creatie (Web en code-gebaseerde ervaringen), campagneuitvoering, inhoud experimenteren (het testen A/B), besluit (dynamische inhoudselectie), en het melden
- **[!DNL Adobe Real-Time Customer Data Platform] (rt-CDP)** — de segmentatie van Edge voor publieksevaluatie in real time die op het gedragssignalen van het in-zittingsgedrag wordt gebaseerd; anoniem beheer van het randprofiel
- **[!DNL Adobe Experience Platform] (AEP)** — [!DNL Web SDK] voor de inzameling van het gedragssignaal, [!DNL Edge Network] voor gegevens in real time die en verpersoonlijkingslevering verpletteren, gegevensstroomconfiguratie

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | AJO-sandbox met webkanaalmachtigingen geconfigureerd. [!DNL Web SDK] implementatiemachtigingen en datastream toegang verleend aan het implementatieteam. Gebruikers met rollen die webkanaalconfiguratie, publieksbeheer en uitvoering van campagnes toestaan. | [&#x200B; overzicht van het Toegangsbeheer &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | Ervaar gebeurtenisschema&#39;s waarin webgedragssignalen worden vastgelegd (paginaweergaven, klikken, schuifdiepte, verwijzingsgegevens, UTM-parameters). Het schema moet standaardgroepen van het Web interactiegebied omvatten en voor randprofiel worden toegelaten om evaluatie in real time te steunen. Een overeenkomstige dataset moet worden gecreeerd en profiel-toegelaten. | [&#x200B; XDM overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Gegevensbronnen en -verzameling | Vereist | [!DNL Web SDK] moet worden geïmplementeerd op alle webeigenschappen van het doel met een gegevensstroom geconfigureerd om gegevens door te sturen naar [!DNL AEP Edge Network] . Voor de gegevensstroom moeten de services [!DNL Adobe Experience Platform] en [!DNL Adobe Journey Optimizer] zijn ingeschakeld. Dit is een kritieke afhankelijkheid — zonder [!DNL Web SDK] is geen gedragssignaalverzameling of ervaringslevering mogelijk. | [&#x200B; overzicht van SDK van het Web &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home) |
| Identiteit en profielconfiguratie | Vereist | ECID ([!DNL Experience Cloud ID]) gevormd als primaire identiteitskaart namespace voor anonieme bezoekers. Het samenvoegbeleid van Edge moet met `isActiveOnEdge: true` worden gevormd om anonieme profielgegevens bij de rand op te lossen. Er kan slechts één samenvoegbeleid actief zijn op de rand per sandbox. | [&#x200B; Overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Auditiedefinitie en segmentatie | Vereist | Door Edge beoordeelde publiekssegmenten gedefinieerd op basis van gedragssignalen tijdens de sessie. Edge-segmentatie is verplicht voor een latere evaluatie. De regels van het segment moeten slechts de rand-in aanmerking komende uitdrukkingen van de segmentregel gebruiken (eenvoudige attributencontroles en segmentlidmaatschap — geen tijd-reeksen vragen of complexe samenvoegingen). | [&#x200B; de segmentatie van Edge &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Niet van toepassing | Beperkte waarde voor anonieme bezoekers omdat er minimale historische profielgegevens zijn om samen te voegen. Dit kan van toepassing worden als het Edge-profiel zinvolle gedragsgegevens opneemt van eerdere anonieme bezoeken tijdens meerdere sessies. | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Voor anonieme Edge-profielen moet de vervaldatum van een pseudoniem profiel worden geconfigureerd om opslag te beheren en te voldoen aan privacyvereisten. U kunt instellen dat profielen die alleen voor ECID&#39;s zijn bestemd, tussen 14 en 365 dagen verlopen. Het beleid voor toestemming voor cookies moet worden afgedwongen voor het verzamelen van gedragsgegevens. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | De etiketten van de governance op gedragsgegevens verzekeren naleving, met name voor geo-gericht (S2 gevoelig geografisch etiket) en op apparaat-gebaseerde verpersoonlijking. Met labels wordt voorkomen dat beperkte gedragsgegevens worden gebruikt in onbevoegde personalisatiekanalen. | [&#x200B; Overzicht van het beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Bewaking en waarneming | Aanbevolen | [!DNL Edge Network] en [!DNL Web SDK] de controle van de gegevensstroom helpt verpersoonlijkingskwesties ontdekken. Vorm alarm voor gegevensstroommislukkingen, innamefouten, en randleveringsanomalieën. Kritiek voor productieplaatsingen waar de mislukkingen van de verpersoonlijking de ervaring van de bezoeker degraderen. | [&#x200B; overzicht van de Inzichten van de Waarnemelijkheid &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | Personalization-prestatierapportage maakt deel uit van de functieketen (fase 5). De CJA-analyse van de effectiviteit van anonieme personalisatie van bezoekers maakt een diepgaande funnel-analyse, -cohortvergelijking en -conversie-effectmeting mogelijk die verder gaat dan wat in AJO native rapporten wordt geboden. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer] (AJO)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Kanaalconfiguratie | Fase 1: Weboppervlakconfiguratie | Webkanaaloppervlakken configureren die bepalen waar gepersonaliseerde inhoud wordt geleverd op de doelwebeigenschappen |
| Berichtontwerp | Fase 3: Inhoud schrijven en Variant maken | Aangepaste inhoudsvarianten voor weboppervlakken ontwerpen met de webontwerper, de op code gebaseerde ervaringseditor of de inhoudssjablonen |
| Campagne uitvoeren | Fase 4: Configuratie van campagne en levering | Webcampagnes maken en activeren die het publiek, de inhoud en de leveringsconfiguratie binden |
| Besluitvorming | Fase 3: Inhoud schrijven en Variant maken (Optie C) | Bepalingsbeleid, geschiktheidsregels en classificatiestrategieën voor dynamische inhoudselectie configureren op basis van gedragssignalen |
| Inhoud experimenteren | Fase 3: Inhoud schrijven en Variant maken (optie B) | Vorm A/B en multivariatie inhoudexperimenten met verkeerstoewijzing, succesmetriek, en vertrouwensdrempels |
| Rapportage en prestatieanalyse | Fase 5: Rapportage en prestatieanalyse | De metriek van de verpersoonlijking van de monitor, variantdoeltreffendheid, proefresultaten en omzettingseffect |

### [!DNL Real-Time CDP] (RT-CDP)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Fase 2: Gedragsdefinitie van het publiek | Bepaal en evalueer rand-gebaseerde publiekssegmenten gebruikend in-zittingsgedragssignalen voor verpersoonlijking in real time die richten |

## Vereisten

Voltooi het volgende voordat u begint met de implementatie.

- [ ] [!DNL Web SDK] wordt geïmplementeerd op alle webeigenschappen van het doel met `sendEvent` -aanroepen die paginaweergaven, klikken en relevante gedragsinteracties vastleggen
- [ ] DataStream wordt geconfigureerd in de gebruikersinterface voor gegevensverzameling met [!DNL Adobe Experience Platform] - en [!DNL Adobe Journey Optimizer] -services ingeschakeld
- [ ] Experience Event-schema bestaat met webinteractieveldgroepen (paginaweergaven, verwijzingsgegevens, UTM-parameters, apparaatcontext) en is ingeschakeld voor Profiel
- [ ] ECID-naamruimte is geconfigureerd en toegewezen als primaire identiteit in het webgedragsgebeurtenisschema
- [ ] Edge-samenvoegbeleid is geconfigureerd met `isActiveOnEdge: true` in de doelsandbox
- [ ] AJO-webkanaal is ingericht en toegankelijk in de doelsandbox
- [ ] De varianten van de inhoud (exemplaar, beelden, CTAs) worden ontworpen en goedgekeurd voor elke het gebruiksgeval van de verpersoonlijking
- [ ] Succeswaarden worden gedefinieerd (wat een conversie- of betrokkenheidsgebeurtenis voor metingen is)
- [ ] Het mechanisme voor toestemming voor cookies wordt geïmplementeerd op de website om te voldoen aan privacyregels voordat gedragsgegevens worden verzameld

## Implementatieopties

In dit gedeelte worden drie implementatiebenaderingen beschreven. Selecteer de optie die het beste aansluit bij uw vereisten voor personalisatie.

### Optie A: Op regels gebaseerde webpersonalisatie

**Best voor:** Eenvoudige, deterministische verpersoonlijking — geo-gerichte banners, verwijzing-bron-specifieke koppen, apparaat-specifieke lay-outs, nieuw vs. het terugkeren van bezoekersoverseinen. Kies deze optie wanneer de inhoudvariant kan worden bepaald door eenvoudige voorwaardelijke logica (als voorwaarde X inhoud Y weergeeft).

**hoe het werkt:**

Op regel-gebaseerde verpersoonlijking gebruikt rand-geëvalueerde publiekssegmenten om te bepalen welke inhoudvariant een bezoeker ziet. Elk publiekssegment brengt aan een specifieke inhoudvariant door voorwaardelijke die regels in de campagne worden bepaald in kaart. Wanneer een bezoeker een pagina laadt, verzendt [!DNL Web SDK] gedragssignalen naar [!DNL Edge Network] , die het de randprofiel van de bezoeker tegen de bepaalde publieksregels in milliseconden evalueert. De overeenkomstige inhoudvariant wordt geretourneerd in het [!DNL Edge Network] -antwoord en op de pagina weergegeven.

Deze benadering vereist het bepalen van verschillende publiekssegmenten in RT-CDP (bijvoorbeeld &quot;bezoekers van het onderzoek van Google,&quot;bezoekers in Californië,&quot;mobiele apparatenbezoekers&quot;) en het creëren van overeenkomstige inhoudvarianten in AJO. De campagne bindt elk publiek aan zijn inhoudvariant gebruikend voorwaardelijke inhoudsregels of afzonderlijke campagnes per segment. Er is geen sprake van een AI-classificatie of verkeerssplitsing — de relatie tussen publiek en inhoud is deterministisch.

**Zeer belangrijke overwegingen:**

- Vereist duidelijk bepaalde publiekscriteria die als rand-in aanmerking komende uitdrukkingen van de segmentregel kunnen worden uitgedrukt
- De inhoudvarianten moeten voor elk publiekssegment worden pre-authored
- Voor het toevoegen van nieuwe aanpassingsregels moet u nieuwe publiekssegmenten en inhoudsvarianten maken
- Geeft geen statistische meting van de doeltreffendheid van de inhoudvariant

**Voordelen:**

- Eenvoudigst om uit te voeren en te begrijpen — duidelijke oorzaak-en-effect verhouding tussen publiek en inhoud
- Geen overhead- of verkeersopsplitsing voor experimenten vereist
- Met deterministisch gedrag maakt u het testen en het kwaliteitscontrole eenvoudig
- Lage latentie aangezien de randevaluatie puur op regel-gebaseerd is
- Het werkt goed wanneer de zaken reeds weten welke inhoud het best voor elk segment presteert

**Beperkingen:**

- Geen ingebouwd mechanisme om te meten of personalisatie de resultaten ten opzichte van de standaardinhoud verbetert
- Vereist handmatige besluitvorming over welke inhoud elk segment moet worden weergegeven
- Past niet aan of optimaliseert zich in tijd — statische regels tot manueel veranderd
- Schalen naar veel segmenten en varianten vergroot de complexiteit van de configuratie

**Experience League:**

- [Aan de slag met webkanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Optie B: Experimentatiegebaseerde webpersonalisatie

**het Best voor:** A/B en multivariate het testen — het testen van krantenvarianten, de knoopkleuren van CTA, lay-outalternatieven, promotionele aanbiedingen — met statistische significantiemeting. Kies deze optie wanneer u moet bevestigen welke inhoudvariant het best presteert alvorens aan een permanente verpersoonlijkingsregel te begaan.

**hoe het werkt:**

Bij personalisatie op basis van experimenten wordt gebruikgemaakt van AJO Content Experimentation om bezoekers willekeurig toe te wijzen aan inhoudsbehandelingsgroepen en te meten welke variant het beste presteert in vergelijking met een gedefinieerde succesmaatstaf. Het verkeer wordt opgesplitst over verschillende varianten (bv. 50/50 voor A/B, 33/33/34 voor A/B/C) en de prestaties worden bijgehouden totdat de statistische significantie is bereikt.

Het experiment is ingebed in een AJO-webcampagne. Wanneer een bezoeker een pagina laadt, wijst [!DNL Edge Network] hen aan een behandelingsgroep toe die op de gevormde verkeerstoewijzing wordt gebaseerd. De bezoeker ziet altijd dezelfde behandeling gedurende het experiment (sessieniveau of blijvend bezoekersniveau, afhankelijk van de configuratie). Succeswaarden (klikken, conversies, betrokkenheidsgebeurtenissen) worden bijgehouden via [!DNL Web SDK] en gerapporteerd in het AJO-testrapport.

Voor deze optie is geen vooraf gedefinieerde doelsegmenten vereist. Alle bezoekers (of een doelsubset) nemen deel aan het experiment. Het doel is te ontdekken welke inhoud het best presteert, niet om bekende segmenten met vooraf bepaalde inhoud te richten.

**Zeer belangrijke overwegingen:**

- Vereist voldoende verkeersvolume om binnen een redelijke termijn statistische significantie te bereiken
- Experimenten gebruiken een Bayesiaans statistisch model met telkens geldige betrouwbaarheidsintervallen
- Een holdout-groep (ontvangt geen gepersonaliseerde inhoud) wordt aanbevolen om de incrementele lift te meten
- Per campagne kan slechts één experiment tegelijk actief zijn
- De experimentele wijzigingen vereisen dat de campagne wordt gestopt en opnieuw wordt opgestart

**Voordelen:**

- Verstrekt statistisch rigoureuze meting van de doeltreffendheid van inhoudvariant
- Verwijdert giswerk uit personalisatiebeslissingen — gegevensgestuurde selectie van inhoud
- Ondersteunt holdoutgroepen voor werkelijke incrementele lichtmeting
- Ingebouwde experimentrapportage met betrouwbaarheidsintervallen en windenergie
- De resultaten kunnen toekomstige op regel-gebaseerde verpersoonlijking (Optie A) door het winnen varianten te identificeren informeren

**Beperkingen:**

- Vereist een betekenisvol verkeersvolume — pagina&#39;s met een laag verkeersvolume kunnen weken duren om betekenis te bereiken
- Verkeerssplitsing betekent dat sommige bezoekers tijdens de testperiode suboptimale inhoud zien
- Kan niet personaliseren per segment tijdens het experiment (alle bezoekers of een subset nemen evenzeer deel)
- Maximaal 10 behandelingsvarianten per experiment
- Geen continue optimalisatie — experimenten zijn discreet met een begin- en eindresultaat

**Experience League:**

- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport voor inhoudexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Optie C: Op beslissingen gebaseerde webpersonalisatie

**Best voor:** Dynamische inhoudselectie — de aanbevelingen van de categorierechtheid, uitgang-intent aanbiedingen, gedragsaanbevelingen — waar een besluitvormingsbeleid zittingssignalen evalueert en de optimale inhoud van een catalogus van in aanmerking komende punten selecteert. Kies deze optie als de logica voor het selecteren van inhoud te complex is voor eenvoudige regels, als u geoptimaliseerd wilt worden met een AI-positie of als de set in aanmerking komende inhoudsitems groot en dynamisch is.

**hoe het werkt:**

Op beslissing-gebaseerde verpersoonlijking gebruikt AJO Beslissing om gedragssignalen te evalueren en de beste inhoudvariant voor elke bezoeker van een beheerde catalogus van inhoudspunten (aanbiedingen) te selecteren. Elk inhoudspunt heeft geschiktheidsregels (die kwalificeert), representaties (hoe de inhoud eruit ziet in elke plaatsing) en optionele begrenzingsbeperkingen (hoe vaak deze kan worden weergegeven). Een beslissingsbeleid koppelt plaatsingen (waar inhoud op de pagina wordt weergegeven) aan verzamelingen van inhoudsitems en past een rangschikkingsstrategie toe om de beste optie te selecteren.

Wanneer een bezoeker een pagina laadt, verzendt [!DNL Web SDK] een [!DNL Edge Network] -aanvraag die het beslissingsbereik bevat. De beslissingsengine evalueert het Edge-profiel van de bezoeker op basis van de geschiktheidsregels voor inhoudsitems, past de classificatiestrategie (op basis van prioriteit, op basis van formule of op basis van AI) toe en retourneert het winnende inhoudsitem. Dit gebeurt aan de rand met subtweede latentie.

De rangschikkingsstrategie bepaalt hoe in aanmerking komende inhoudsitems worden geordend. Bij rangschikking op basis van prioriteit worden handmatig toegewezen prioriteitswaarden gebruikt. Bij op formule gebaseerde rangschikking wordt een aangepaste expressie gebruikt (bijvoorbeeld een wegingsfrequentie van paginaweergaven). In de classificatie AI-gerangschikt wordt een model voor machinaal leren gebruikt dat optimaliseert voor de geselecteerde succesmetrische methode in de loop der tijd, maar een minimum van 1.000 conversiegebeurtenissen voor opleiding vereist.

**Zeer belangrijke overwegingen:**

- Vereist het instellen van de beslissingscomponenten: plaatsingen, toelatingsregels, inhoudselementen, reserveonderdelen, inzamelingspunten, en besluitvormingsbeleid
- Voor strategieën op AI-niveau is een voldoende conversievolume (1000+ gebeurtenissen) vereist om het model te kunnen trainen
- Edge-beslissingen zijn beperkt tot profielkenmerken die beschikbaar zijn in de winkel met randprofielen
- Inhoudsitems moeten worden beheerd en onderhouden in de beslissingsbibliotheek
- Inhoud voor alternatieven moet worden gedefinieerd als geen gepersonaliseerd item in aanmerking komt

**Voordelen:**

- Schaalt naar grote inhoudcatalogi zonder dat afzonderlijke publiek-naar-content-toewijzing is vereist
- Op AI gerangschikte strategieën optimaliseren constant inhoudselectie op waargenomen prestaties wordt gebaseerd
- De toelatingsregels en de begrenzingsbeperkingen verstrekken fijnkorrelige controle over inhoudslevering
- Ondersteunt complexe bedrijfslogica die moeilijk als publiekssegmenten kan worden uitgedrukt
- Herbruikbaar via kanalen — hetzelfde beslissingsbeleid kan de personalisatie van internet, e-mail en mobiele apparaten stimuleren

**Beperkingen:**

- Hogere implementatiemogelijkheden: u moet de volledige stapel met beslissingscomponenten instellen
- Voor de classificatie van AI is een aanzienlijk omzettingsvolume en een aanzienlijke tijd nodig om effectief te kunnen trainen
- Beperkingen van Edge-profielgegevens beperken de complexiteit van de subsidiabiliteitsregel voor anonieme bezoekers
- Overheadkosten voor beheer van inhoudsitems — elk item heeft representaties, subsidiabiliteitsregels en onderhoud nodig
- Fouten opsporen in beslissingslogica is complexer dan op regels gebaseerde benaderingen

**Experience League:**

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Plaatsingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)

### Optievergelijking

In de volgende tabel worden de drie implementatieopties vergeleken met de belangrijkste criteria.

| Criteria | Optie A: Op regel gebaseerd | Optie B: Experimentatie | Optie C: Beslissing |
| --- | --- | --- | --- |
| Best voor | Bekende segment-aan-inhoud afbeeldingen | Controleren welke inhoud het beste werkt | Dynamische inhoud selecteren uit grote catalogi |
| Complexiteit | Laag | Gemiddeld | Hoog |
| Latentie | Subseconde (rand) | Subseconde (rand) | Subseconde (rand) |
| Personalization precision | Segmentniveau (publieksregels) | Bezoekersniveau (willekeurige toewijzing) | Bezoekersniveau (geschiktheid + rangschikking) |
| Inhoud optimaliseren | Handmatig (geen meting) | Statistische tests (A/B) | Doorlopend (van AI-klasse) of handmatig (prioriteit) |
| Vereist publiekssegmenten | Ja (gekanteld) | Nee (verkeerssplitsing) | Facultatief (voor subsidiabiliteitsregels) |
| Meetmogelijkheden | Geen ingebouwd (vereist CJA) | Ingebouwde experimentrapporten | Geïntegreerde beslissingsrapporten |
| Grootte van inhoudscatalogus | Klein (1 :1 segment-aan-inhoud) | Klein (2-10 varianten) | Grote (onbeperkte in aanmerking komende objecten) |
| Vereisten | Edge-publiek, inhoudvarianten | Campagne met experiment ingeschakeld | Beslissingscomponenten (plaatsingen, aanbiedingen, beleid) |

### Kies de juiste optie

Gebruik de volgende besluitvormingslogica om de aangewezen implementatieoptie te selecteren:

1. **weet u reeds welke inhoud aan elk bezoekerssegment zou moeten worden getoond?**
   - Ja: Begin met **Optie A (op regel gebaseerd)**. U hebt inhoudsstrategieën per segment vastgesteld en hebt deterministische levering nodig.
   - Nee: ga door met vraag 2.

2. **moet u een klein aantal inhoudvarianten testen om de beste uitvoerder te vinden?**
   - Ja: Kies **Optie B (Experimentatie)**. U wilt statistische validatie voordat u een inhoudsstrategie doorvoert.
   - Nee: ga door met vraag 3.

3. **hebt u een grote catalogus van inhoudspunten met complexe geschiktheid en het rangschikken vereisten?**
   - Ja: Kies **Optie C (Beslissing)**. U hebt een dynamische selectie van inhoud nodig waarbij de schaal verder gaat dan de eenvoudige regels.
   - Nr: Begin met **Optie A (regel-Gebaseerd)** voor eenvoud, dan evolueer aan Optie B of C aangezien de vereisten groeien.

**Combinerend opties:** Deze opties zijn niet wederzijds exclusief. Een algemene vooruitgang is om met Optie B (Experimentatie) te beginnen het winnen van inhoud te ontdekken, dan winnaars op te stellen gebruikend Optie A (regel-Gebaseerd) voor aan de gang zijnde levering. De optie C (Beslissing) kan op bovenkant voor gebruiksgevallen worden gelaagd die dynamische op catalogus-gebaseerde selectie vereisen, terwijl Optie A de eenvoudigere deterministische regels behandelt.

## Uitvoeringsfasen

De volgende fasen beschrijven de implementatieworkflow van begin tot eind.

### Fase 1: Weboppervlakken configureren

**functie van de Toepassing:** AJO: De Configuratie van het Kanaal

Definieer de oppervlakken van het webkanaal die aangeven waar op uw website gepersonaliseerde inhoud wordt geleverd. Een weboppervlak identificeert een specifiek pagina-URL- of URL-patroon en de locatie op de pagina (CSS-kiezer of op code gebaseerd ervaringsoppervlak) waar AJO inhoud kan injecteren of vervangen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: Type van oppervlakte** - hoe zou gepersonaliseerde inhoud aan de pagina moeten worden geleverd?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Webkanaal (visuele editor) | De verpersoonlijking impliceert het wijzigen van zichtbare paginaelementen (banners, koppen, beelden, CTAs) gebruikend een belemmering-en-dalings visuele redacteur | Vereist de browser van de webontwerper. Dit is het meest geschikt voor wijzigingen in inhoud die via marketing wordt gestuurd. Beperkt tot visuele wijzigingen van bestaande pagina-elementen. |
| Ervaring op basis van code | De personalisatie vereist het injecteren van gestructureerde gegevens (JSON) die de code van de websitetoepassing verbruikt en teruggeeft | Vereist een ontwikkelaarsimplementatie om de JSON-payload te gebruiken. Maximale flexibiliteit voor complexe personalisatie. Het beste voor SPAs, dynamische componenten, en programmatic het teruggeven. |
| Beide (hybride) | Verschillende personalisaties op dezelfde site hebben verschillende leveringsmechanismen nodig | Gebruik webkanaal voor eenvoudige visuele wijzigingen en op code gebaseerde ervaringen voor programmatische rendering. Verhoogt de complexiteit van de implementatie maar maximaliseert de dekking. |

>[!NOTE]
>**Besluit: Het werkingsgebied van de Oppervlakte** — Welk bereik URL zou de Weboppervlakte moeten behandelen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Exacte URL-overeenkomst | Personalization richt zich op een specifieke pagina (bijvoorbeeld homepage, landingspagina) | Het meest nauwkeurige richten. Vereist afzonderlijke oppervlakken voor elke pagina. |
| URL-patroon met jokertekens | Personalization wordt toegepast op een paginacategorie (bijvoorbeeld alle productpagina&#39;s, alle blogartikelen) | Hiermee verlaagt u de overhead voor oppervlaktebeheer. De varianten van de inhoud moeten worden ontworpen om over alle gelijke pagina&#39;s te werken. |
| Single-page application (SPA) oppervlak | De website is een SPA waarbij URL-wijzigingen niet leiden tot het opnieuw laden van de volledige pagina | Vereist SPA-bewuste [!DNL Web SDK] configuratie met `sendEvent` vraag op meningsveranderingen. Oppervlakdefinities gebruiken de naam van de SPA-weergave in plaats van URL. |

**navigatie UI:** [!DNL Journey Optimizer] > Beleid > Kanalen > de configuratie van het Web

**Zeer belangrijke configuratiedetails:**

- Het URL- of URL-patroon van de pagina voor het oppervlak definiëren
- CSS-kiezer of oppervlak-URI opgeven voor plaatsing van inhoud
- Voor code-gebaseerde ervaringen, bepaal de oppervlaknaam die de toepassingscode zal verwijzen
- Het oppervlak koppelen aan de AJO-sandbox waar campagnes worden gemaakt

**documentatie van Experience League:**

- [Aan de slag met webkanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Webervaringen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-gebaseerd ervaringskanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Op code gebaseerde ervaringsconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

### Fase 2: Gedragssoorten definiëren

**functie van de Toepassing:** rt-CDP: de Evaluatie van het publiek

Bepaal rand-beoordeelde publiekssegmenten die op in-zittingsgedragssignalen worden gebaseerd die verpersoonlijking richten. Deze doelgroepen bepalen welke bezoekers in aanmerking komen voor elke persoonlijke ervaring. Edge-evaluatie is verplicht voor dit patroon, aangezien beslissingen over personalisatie moeten worden genomen in subseconden als de bezoeker door de site navigeert.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: De selectie van het Gedrag signaalselectie** — Welke in-zittingssignalen zou verpersoonlijking het richten moeten drijven?

| Signaal | Wanneer gebruiken | Edge-geschiktheid |
| --- | --- | --- |
| Referentiebron/UTM-parameters | Aanpassing landingspagina&#39;s voor specifieke campagnes | In aanmerking komend — eenvoudige kenmerkcontrole op de huidige gebeurtenis |
| Geografische locatie (land, regio, stad) | Regionale promoties, taalspecifieke inhoud, opslaglocatie | In aanmerking komend — controle van profielkenmerken |
| Apparaattype (bureaublad, mobiel, tablet) | Inhoudslay-outs en CTA&#39;s die zijn geoptimaliseerd voor apparaten | In aanmerking komend — controle van profielkenmerken |
| Pagina&#39;s weergegeven in sessie | Categorieaffiniteit, aanbevelingen voor inhoud | Geschikt voor beperkingen — alleen eenvoudige controles op het aantal gebeurtenissen |
| Nieuwe bezoeker vs. terugkerende bezoeker | Welkomstberichten, progressieve betrokkenheid | Subsidiabel — ECID-persistentie geeft terugkerende bezoeker aan |
| Tijd op site/schuifdiepte | Uitgaande intentie, op betrokkenheid gebaseerde aanbiedingen | Mogelijk is aangepaste implementatie vereist — niet mogelijk voor randapparaten |

>[!NOTE]
>**Besluit: De evaluatiemethode van het publiek** — Alle publiek voor dit patroon moet randevaluatie gebruiken. Bevestig geschiktheid voordat u segmenten definieert.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Edge-evaluatie | Vereist voor dit patroon | De de regeluitdrukkingen van het segment moeten rand-in aanmerking komen: eenvoudige attributenvergelijkingen, de controles van het segmentlidmaatschap, geen tijd-reeksen vragen of samenvoegingsfuncties. Latentie evaluatie subseconden. |
| Streaming evaluatie (fallback) | Wanneer de uitdrukking van de segmentregel niet rand-in aanmerking komend maar bijna-real-time is aanvaardbaar | Latentie seconden tot minuten. Ondersteunt complexere segmentregelexpressies. Kan merkbare vertraging in de levering van personalisatie introduceren. |

**navigatie UI:** Klant > Soorten publiek > leidt tot publiek > bouwt regel

**Zeer belangrijke configuratiedetails:**

- De Bouwer van het Segment van het gebruik om publieksregels te bepalen gebruikend gedragsattributen
- Verifieer randgeschiktheid door de uitdrukking van de segmentregel te bevestigen gebruikt slechts gesteunde functies (eenvoudige attributenvergelijkingen, segmentlidmaatschap)
- Plaats het fusiebeleid aan rand-actief fusiebeleid dat in F4 wordt gevormd
- De kijkpopulatie van de voorproef om de segmentwinst verwachte resultaten te bevestigen
- Voor publiek dat op de meningen van de in-zittingspagina wordt gebaseerd, gebruik gebeurtenis-vlakke attributen van de huidige zitting eerder dan tijdreeksvragen

**waar de opties uiteenlopen:**

**voor Optie A (regel-Gebaseerd):**
Maak afzonderlijke publiekssegmenten voor elke inhoudvariant. Elk segment vertegenwoordigt een specifieke gedragsconditie (bijv. &quot;Referral = Google AND Geo = US&quot; wordt toegewezen aan inhoudvariant A). Het aantal doelgroepen is gelijk aan het aantal regels voor personalisatie.

**voor Optie B (Experimentation):**
De definitie van het publiek is optioneel. Als het experiment op alle bezoekers gericht is, wordt geen publiek vereist — het splitsen van het verkeer behandelt varianttoewijzing. Als het experiment gericht is op een specifieke subset (bv. alleen mobiele bezoekers), definieert u één doelgroep voor de subsidiabiliteit van het experiment.

**voor Optie C (Beslissing):**
Bepaal publiek voor gebruik als geschiktheidsregels voor inhoudsitems. Deze doelgroepen bepalen welke bezoekers in aanmerking komen voor welke inhoudsitems in het besluitvormingsbeleid. De beslissingsengine handelt de selectie van inhoud uit in aanmerking komende items af.

**documentatie van Experience League:**

- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Fase 3: Inhoud van auteur maken en varianten maken

**de functie van de Toepassing:** AJO: De Authoring van het Bericht, AJO: De Experimentatie van de inhoud (Optie B), AJO: Beslissing (Optie C)

Maak de varianten van gepersonaliseerde inhoud die aan bezoekers worden geleverd op basis van het lidmaatschap van het publiek (Option A), experimentele toewijzing (Option B) of beslissingslogica (Option C). Deze fase gaat over het maken van inhoud met behulp van de AJO-webontwerper of de op code gebaseerde ervaringseditor, maar ook over de test- of beslissingsconfiguratie die bepaalt hoe inhoud wordt geselecteerd.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: De auteursbenadering van de inhoud** - hoe de varianten van de Webinhoud zou moeten worden authored?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Webvisuele editor | Het marketingteam kan pagina-elementen visueel wijzigen zonder code | Vereist een browserextensie. Dit is het meest geschikt voor wijzigingen in tekst, afbeeldingen en CTA. Beperkt tot het wijzigen van bestaande pagina-elementen. |
| Code-gebaseerde ervaringseditor | De inhoud vereist gestructureerde gegevens (JSON) die door de toepassingscode worden gerenderd | Maximale flexibiliteit. Vereist ontwikkelaarsimplementatie om de lading te verbruiken. Het beste voor dynamische componenten en SPAs. |
| HTML/CSS-code-editor | Wijzigingen in inhoud vereisen aangepaste HTML of CSS | Directe codecontrole. Vereist HTML/CSS-expertise. Dit is het meest geschikt voor complexe layoutwijzigingen. |

>[!NOTE]
>**Besluit: de tokens van Personalization** — Moet de inhoud dynamische verpersoonlijking omvatten gebruikend profiel of contextafhankelijke attributen?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Variabelen voor statische inhoud | Elke variant is een vast stuk inhoud zonder dynamische tokens | Eenvoudigste aanpak. De inhoud is voorspelbaar en gemakkelijk aan QA. Geen risico op ontbrekende kenmerkwaarden. |
| Dynamische inhoud met personalisatie-expressies | De inhoud bevat tokens in de stijl Handlebars die worden omgezet in profiel- of gebeurteniskenmerken (bijvoorbeeld plaatsnaam, verwijzingsbron) | Betere inhoud. Vereist terugvalwaarden voor attributen die ongeldig op anonieme profielen kunnen zijn. Gebruik `{{profile.homeAddress.city}}` syntaxis met hulplijnen. |
| Voorwaardelijke inhoudsblokken | Verschillende inhoudsblokken worden gerenderd op basis van kenmerkvoorwaarden binnen één variant | Vermindert het aantal verschillende benodigde varianten. Hiermee vergroot u de complexiteit van inhoud. Goed voor kleine variaties binnen een gedeelde lay-out. |

**navigatie UI:** [!DNL Journey Optimizer] > Campagnes > Uitgezochte campagne > geef inhoud uit

**Zeer belangrijke configuratiedetails:**

- Inhoud van auteurs die de webontwerper (visuele wijzigingen) of de op code gebaseerde ervaringseditor (JSON-payload) gebruiken
- De personalisatie-expressie-editor gebruiken om dynamische tokens in te voegen van randprofielkenmerken
- Wijzig de fallback-inhoud voor personalisatietokens die leeg kunnen zijn in anonieme profielen
- Inhoud met testprofielen voorvertonen om de rendering in verschillende scenario&#39;s te controleren

**waar de opties uiteenlopen:**

**voor Optie A (regel-Gebaseerd):**
Auteur een verschillende inhoudsvariant voor elk publiekssegment dat in Fase 2 wordt bepaald. Bind elke variant aan zijn doelpubliek gebruikend voorwaardelijke inhoudsregels in de campagneconfiguratie. Zorg ervoor dat er een standaardinhoudsvariant bestaat voor bezoekers die geen publieksregel overeenkomen.

**voor Optie B (Experimentation):**
Varianten voor de behandeling van auteurs (A, B, C, enz.) voor het experiment. Laat inhoud experimenteren op de campagne toe, bepaal behandelingsvarianten met hun inhoud, plaats de percentages van de verkeerstoewijzing, en vorm succesmetrisch.

- 2-10 behandelingsvarianten met een duidelijk gehalte definiëren
- Verkeerstoewijzing instellen (bv. 50/50 voor A/B of gewogen splitsing voor tests met een lager risico)
- Neem optioneel een holdout-groep op (10% ontvangt bijvoorbeeld de standaardinhoud) om de incrementele lift te meten
- Selecteer succesmetrisch: uniek opent, unieke kliks, omzettingen, of douane metrisch
- Stel de betrouwbaarheidsdrempel in: 95% voor standaardtests, 99% voor beslissingen met een hoog risico en 90% voor gericht leren
- **navigatie UI:** De Campagne > het experiment van de Inhoud > voegt behandeling toe > de toewijzing van het Verkeer > metrische Opvolger

**voor Optie C (Beslissing):**
Opstelling de de componentenstapel van de Beslissing en integreert het in de campagne.

1. **creeer plaatsingen** - bepaal waar op de punten van de paginacontent zal verschijnen (Web HTML, Web JSON, Webbeeld)
   - **navigatie UI:** [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Plaatsingen
2. **bepaalt toelatingsregels** - creeer regels die op de attributen van het randprofiel worden gebaseerd die bepalen welke bezoekers voor elk inhoudspunt kwalificeren
   - **navigatie UI:** [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Regels
3. **creeer inhoudspunten (aanbiedingen)** — Auteur gepersonaliseerde inhoudspunten met vertegenwoordiging voor elke plaatsing, geschiktheidsregels, prioriteit, en facultatieve aftappen
   - **navigatie UI:** [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Aanbiedingen > Aanbieding maken
4. **creeer reserveinhoud** - bepaal een terugval punt teruggekeerd wanneer geen gepersonaliseerd punt kwalificeert
   - **navigatie UI:** [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Aanbiedingen > Create fallback aanbieding
5. **organiseert in inzamelingen** - de inhoudspunten van de Groep gebruikend inzamelingsbepalers (markeringen) en creeert inzamelingen
   - **navigatie UI:** [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Verzamelingsbepalers / Verzamelingen
6. **creeer besluitvormingsbeleid** — De plaatsingen van de Verbinding aan inzamelingen en selecteer de rangschikkende strategie (op prioriteit-gebaseerd, op formule-gebaseerd, of op AI gerangschikt)
   - **navigatie UI:** [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer > Besluiten > Beslissingen maken

**documentatie van Experience League:**

- [Webervaringen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-gebaseerd ervaringskanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 4: Campagne en levering configureren

**functie van de Toepassing:** AJO: De Uitvoering van de campagne

Maak en activeer de AJO-webcampagne die het weboppervlak (fase 1), de doelgroep of de testconfiguratie (fase 2-3) en de inhoudvarianten (fase 3) in een te leveren eenheid bindt. De campagne bepaalt wanneer en hoe persoonlijke inhoud aan bezoekers wordt aangeboden.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: Het type van Campagne** - hoe zou de campagne moeten worden teweeggebracht?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Geplande campagne (altijd aan) | Personalization moet continu worden uitgevoerd voor alle in aanmerking komende bezoekers | Stel de begindatum in zonder de einddatum voor het aanpassen van de versieringen. De evaluatie van het publiek gebeurt bij rand in echt - tijd. Meestal voor webpersonalisatie. |
| Geplande campagne (tijdgebonden) | Personalization is gebonden aan een specifieke promotieperiode of een seizoensgebeurtenis | Stel expliciete begin- en einddatums in. De campagne wordt automatisch gedeactiveerd op de einddatum. Goed voor promotiecampagnes. |
| API-gestuurde campagne | Personalization-levering moet worden geactiveerd door een externe systeemgebeurtenis | Vereist API-integratie. Minder algemeen voor anonieme Webverpersoonlijking. Gebruik wanneer een backend systeem moet controleren wanneer de verpersoonlijking actief is. |

**navigatie UI:** [!DNL Journey Optimizer] > Campagnes > tot Campagne leiden

**Zeer belangrijke configuratiedetails:**

- Selecteer het webkanaal en het weboppervlak dat is geconfigureerd in Fase 1
- Bind het doelpubliek (voor Optie A) of vorm experimentele montages (voor Optie B) of bedt het besluit (voor Optie C) in
- Het campagnereschema instellen (begindatum, einddatum of altijd-aan)
- Indien van toepassing, frequentietoewijzing op campagneniveau configureren
- Alle configuratie controleren en de campagne activeren

**waar de opties uiteenlopen:**

**voor Optie A (regel-Gebaseerd):**
Creeer één campagne per verpersoonlijkingsregel, elk gericht op een verschillend randpubliek met zijn overeenkomstige inhoudvariant. U kunt ook één campagne met voorwaardelijke inhoudsregels gebruiken die het lidmaatschap van het publiek aan inhoudvarianten binnen één campagne toewijzen.

**voor Optie B (Experimentation):**
Maak één campagne met toegelaten experimenteren met inhoud. De experimentele configuratie (varianten, verkeerstoewijzing, succesmetrisch) werd gedefinieerd in fase 3. Activeer de campagne om het experiment te starten.

**voor Optie C (Beslissing):**
Creeer een campagne die het besluitvormingsbeleid inbedt dat in Fase 3 wordt gevormd. De inhoudshandeling van de campagne verwijst naar het beslissingsbereik, dat de beslissingsengine aan de rand activeert. Activeer de campagne om te beginnen met het leveren van inhoud op basis van beslissingen.

**documentatie van Experience League:**

- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Aan de slag met campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Fase 5: Prestaties rapporteren en analyseren

**functie van de Toepassing:** AJO: Rapportering &amp; de Analyse van Prestaties

Bewaak de personalisatieprestaties met behulp van ingebouwde AJO-rapporten en breid desgewenst de analyse uit met CJA voor diepere interkanaalinzichten. Deze fase omvat de toegang tot levende en historische campagnerapporten, het herzien van experimentatieresultaten, en het bouwen van de werkruimten van de douaneanalyse.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: Meldend diepte** — Hoe diep zou de prestatieanalyse gaan?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen systeemeigen AJO-rapporten | De standaardwaarden voor levering en service zijn voldoende | Verstrekt impressies, klikken, CTR, en omzettingsmetriek uit de doos. Direct beschikbaar in de interface van de campagne. Beperkte aanpassing. |
| AJO-rapporten + CJA-analyse | Diepe funnel-analyse, cohortvergelijking of cross-channel-effectmeting is nodig | Vereist CJA-verbinding en gegevensweergave die zijn gekoppeld aan AJO-gegevenssets. Hiermee schakelt u vrije-vormanalyse, aangepaste berekende metriek, kenmerkmodellering en publiekspublicatie in. |

**navigatie UI:** [!DNL Journey Optimizer] > Campagnes > Uitgezochte campagne > het rapport van de Mening

**Zeer belangrijke configuratiedetails:**

- Heb toegang tot het levende rapport tijdens actieve campagnes om levering in real time te controleren (verfrist om de 60 seconden, toont afgelopen 24 uren)
- Open het historische (alle tijd) rapport na voltooiing van de campagne voor uitgebreide analyse (kan tot 2 uur duren om volledig te vullen)
- Voor optie B (Experimentation): bekijk het experimentatierapport voor vergelijking van de behandelingsprestaties, betrouwbaarheidsintervallen en windenergie
- Voor CJA-analyse: zorg ervoor dat een CJA-verbinding gegevens bevat over een AJO-ervaringsgebeurtenis en dat een gegevensweergave is geconfigureerd met maatstaven voor webpersonalisatie

**waar de opties uiteenlopen:**

**voor Optie A (regel-Gebaseerd):**
De campagnerapporten van het overzicht voor elk publiekssegment om levering en betrokkenheidsmetriek over gepersonaliseerde inhoudsvarianten te vergelijken. Gebruik CJA om een vergelijkingswerkruimte te maken die het conversieeffect meet van gepersonaliseerde versus standaardinhoud.

**voor Optie B (Experimentation):**
Bekijk het experimentatierapport voor statistisch vertrouwen, behandelingslift en identificatie van de winnaars. Wacht tot de betrouwbaarheidsdrempel is bereikt voordat u de winnaar declareert. U kunt winnende inhoud toepassen als de permanente variant (overschakeling naar Option A voor doorlopende levering).

- **navigatie UI:** Campagne > Inhoudsexperiment > het rapport van de Mening
- **Experience League:** [&#x200B; het experimenteerrapport van de Inhoud &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

**voor Optie C (Beslissing):**
Bekijk de maatstaven voor de beslissingsprestaties, zoals de beeldfrequentie, de selectiefrequentie en de conversietoewijzing per inhoudsitem. Analyseren hoe classificatiestrategieën presteren en of er te vaak fallback-inhoud wordt gebruikt (met vermelding van de subsidiabiliteitsregels zijn te restrictief).

**documentatie van Experience League:**

- [Campagne live-rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Statistische berekeningen in het inhoudexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

## Implementatieoverwegingen

In deze sectie worden hulplijnen, valkuilen, beste praktijken en afwegingsbeslissingen voor dit gebruikspatroon besproken.

### Guardrails en limieten

Controleer de volgende instructies voor en tijdens de implementatie.

- De segmenten van Edge zijn beperkt tot eenvoudige attributencontroles en segmentlidmaatschap — geen tijd-reeksen vragen of complexe samenvoegingen — [&#x200B; Edge segmentatiemogelijkheid &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- Slechts één samenvoegingsbeleid kan op rand per zandbak actief zijn - [&#x200B; de gidsen van het Profiel &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum van 4.000 segmentdefinities per zandbak - [&#x200B; de gidsen van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum van 500 actieve levende campagnes per zandbak — [&#x200B; de guardrails van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum van 10 behandelingsvarianten per inhoudexperiment — [&#x200B; de grenzen van het inhoudexperiment &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum van 10.000 goedgekeurde gepersonaliseerde aanbiedingen per zandbak (Optie C) - [&#x200B; de guardrails van het Beheer van het Besluit &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum van 30 plaatsen per besluit (Optie C) — [&#x200B; de guardrails van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Voor AI-classificatiemodellen is een minimum van 1.000 conversiegebeurtenissen vereist voor training (Option C)
- [!DNL Edge Network] reactietijd SLA: &lt; 200 ms voor Edge-geëvalueerde segmenten
- Vervaldatum van pseudoniem profiel: configureerbaar van 14 tot 365 dagen voor profielen met alleen ECID
- Live rapporten worden elke 60 seconden vernieuwd en tonen de laatste 24 uur aan gegevens
- Historische rapporten kunnen tot 2 uur duren om volledig te worden ingevuld na voltooiing van de campagne

### Veelvoorkomende valkuilen

Vermijd de volgende algemene implementatiefouten.

- **[!DNL Web SDK]geen gedragssignalen naar AEP verzenden:** controleer of de [!DNL Adobe Experience Platform] -service is ingeschakeld voor de gegevensstroom en of de gegevensset van de gebeurtenis correct is toegewezen. Zonder deze optie worden randprofielen niet gevuld en mislukt de publieksevaluatie ongemerkt — de bezoeker ontvangt de standaardinhoud zonder foutindicatie.
- **het publiek van Edge die nul kwalificaties terugkeren:** de segmentatie van Edge heeft strikte toelatingsvereisten. De vragen van de tijd-reeksen, samenvoegingsfuncties, en multi-entiteitvragen zijn niet rand-in aanmerking komend. Herschrijf de uitdrukking van de segmentregel gebruikend eenvoudige attributenvergelijkingen of de controles van het segmentlidmaatschap.
- **beleid van de Fusie niet actief op rand:** als het fusiebeleid dat door het publiekssegment wordt gebruikt niet `isActiveOnEdge: true` heeft, zullen de raadplegingen van het randprofiel ontbreken en de verpersoonlijking niet zal worden geleverd. Er kan slechts één samenvoegbeleid per sandbox actief zijn aan de rand. Controleer of er geen conflict bestaat.
- **Personalization flikkert op paginading:** de [!DNL Web SDK] `sendEvent` vraag die verpersoonlijkingsvoorstellingen terugwint moet uitvoeren alvorens de pagina het gebied van de doelinhoud teruggeeft. Implementeer vooraf verbergende fragmenten of asynchrone rendering om te voorkomen dat de standaardinhoud knippert voordat de gepersonaliseerde inhoud wordt geladen.
- **Inhoud die niet op de routeveranderingen van het KUUROORD teruggeeft:** single-page toepassingen vereisen expliciete `sendEvent` vraag met bijgewerkte meningsinformatie wanneer de route verandert. Zonder dit, [!DNL Edge Network] herevalueert geen verpersoonlijking voor de nieuwe mening.
- **Experiment die geen statistische betekenis bereikt:** Onvoldoende verkeersvolume of teveel behandelingsvarianten verdunnen de steekproefgrootte per variant. Verminder het aantal varianten of verhoog de duur van het experiment. Stop niet te vroeg met experimenten — de resultaten kunnen misleidend zijn.
- **Beslissend terugkerend slechts reserveinhoud:** Controle dat de gepersonaliseerde inhoudspunten, binnen hun waaier van de geldigheidsdatum worden goedgekeurd, en dat de geschiktheidsregels de attributen van het de randprofiel van de anonieme bezoeker aanpassen. Controleer ook of de plafondlimiet niet is bereikt.

### Aanbevolen procedures

Volg deze aanbevelingen voor een succesvolle implementatie.

- **Begin eenvoudig, dan herhaling:** Begin met Optie A (regel-Gebaseerd) voor aanvankelijke verpersoonlijking, dan gebruik Optie B (Experimentatie) om veronderstellingen en Optie C (Beslissing) voor geavanceerde gebruiksgevallen te bevestigen. Elke optie bouwt voort op de grondinfrastructuur.
- **gebruik preHide voor flikkerpreventie:** voer het AEP prehide fragment op pagina&#39;s uit waar de verpersoonlijking zal worden geleverd. Hierdoor wordt het inhoudsgebied van het doel verborgen totdat de gepersonaliseerde inhoud gereed is om te renderen, zodat visuele flikkering wordt voorkomen.
- **de fallbackinhoud van het Ontwerp bewust:** de standaard (niet-gepersonaliseerde) inhoud zou een ervaring van uitstekende kwaliteit op zich moeten zijn. Bezoekers die niet in aanmerking komen voor personalisatie — of wanneer de reactie van [!DNL Edge Network] wordt vertraagd — mogen geen gedegradeerde ervaring krijgen.
- **bevestigt randgeschiktheid vóór bouwpubliek:** alvorens in de ontwikkeling van de publieksregel te investeren, bevestig de uitdrukking van de segmentregel rand-in aanmerking komend door de geschiktheidscriteria in Experience League te herzien. Niet-in aanmerking komende expressies zullen stilletjes terugvallen op batch- of streaming evaluatie met onaanvaardbare vertraging voor dit patroon.
- **de prestaties van de randlevering van de Monitor:** opstelling controlealarm voor [!DNL Edge Network] reactietijden en mislukkingen van de verpersoonlijkingslevering. Leveringsproblemen met Edge zijn onzichtbaar voor de bezoeker (ze zien de standaardinhoud) en kunnen onopgemerkt blijven zonder proactieve controle.
- **vorm pseudoniem profielvervaldatum:** plaats aangewezen vervalperiodes voor anonieme randprofielen om dwars-zittingsverpersoonlijking (het erkennen van terugkerende bezoekers) met privacynaleving en opslagbeheer in evenwicht te brengen.
- **Test met representatieve profielen:** wanneer het previewing van gepersonaliseerde inhoud, gebruikstest profielen die de daadwerkelijke anonieme bezoekersscenario&#39;s (geen gegevens van CRM, beperkte gedragsgeschiedenis, diverse geografische plaatsen en apparaten) vertegenwoordigen.

### Handelsbesluiten

Houd rekening met de volgende compromissen wanneer u uw implementatie plant.

>[!NOTE]
>**handel-off: Breedte van Personalization vs. implementatiecomplexiteit**
>
>Meer korrelige personalisatie (veel soorten publiek, veel inhoudvarianten) geeft relevantere ervaringen, maar verhoogt de complexiteit van de configuratie en de overhead van de inhoudsproductie.
>
>- **brede verpersoonlijking bevordert:** Eenvoudigheid, snellere tijd aan markt, lagere kosten van de inhoudsproductie. Een klein aantal doelgroepen en varianten omvat het merendeel van de bezoekers met een betekenisvolle personalisatie.
>- **korrelige verpersoonlijkingsvoorkeur:** Maximale relevantie, hogere betrokkenheidsverhoging, betere omzettingspercentages. Veel soorten publiek en varianten richten zich op specifieke gedragssignalen met op maat gemaakte inhoud.
>- **Aanbeveling:** Begin met 3-5 high-impact verpersoonlijkingsregels die op de gemeenschappelijkste bezoekerssegmenten richten (b.v., verwijzingsbron, apparatentype, geografisch gebied). Meet de impact en breid vervolgens uit tot meer korrelige regels op basis van waargenomen prestaties en bedrijfswaarde.

>[!NOTE]
>**handel-off: Op regel-gebaseerde determinisme vs. AI-gedreven optimalisering**
>
>Op regel-gebaseerde benaderingen (Optie A) geven de zaken volledige controle over welke inhoud elke bezoeker ziet. Met een op AI gerangschikte aanpak (Option C) optimaliseert u de selectie van inhoud in de loop der tijd, maar vermindert u de zichtbaarheid van de selectie van specifieke inhoud.
>
>- **regel-based voorkeur:** Voorspelbaarheid, controleerbaarheid, bedrijfscontrole. Marketing teams weten precies welke inhoud elk segment ontvangt en kunnen de logica aan belanghebbenden uitleggen.
>- **AI-gedreven voorkeur:** de optimalisering van Prestaties, scalability, ononderbroken verbetering. Het AI-model ontdekt de affiniteit van inhoudsbezoekers die het schrijven van regels door mensen kan missen.
>- **Aanbeveling:** Op regel-gebaseerd gebruik voor high-stakes inhoudsbesluiten waar de merkconsistentie en de transparantie van de belanghebbenden van het grootste belang zijn. Gebruik de AI-indeling voor grote inhoudcatalogi waarbij handmatig regelbeheer lastig wordt en continue optimalisatie meetbare lift biedt.

>[!NOTE]
>**handel-off: De anonieme profielpersistentie vs. privacynaleving**
>
>Langere pseudoniem profielvervaldatum maakt een betere intersessiepersonalisatie mogelijk (herkenning van terugkerende bezoekers, opbouw van gedragscontext in de loop der tijd). Kortere vervaldatum verbetert de naleving van de privacy en verlaagt de opslagkosten.
>
>- **Langere vervaldatum begunstigt:** de rijkere anonieme profielen, beter terugkerende bezoekerserkenning, meer gegevens voor verpersoonlijkingsbesluiten. Stel de vervaldatum in op 90-365 dagen.
>- **Kortere vervaldatum begunstigt:** De naleving van de Privacy (GDPR, CCPA), lagere opslagkosten, minimaliseert het risico van de gegevens van het waliteitsprofiel. Stel de vervaldatum in op 14-30 dagen.
>- **Aanbeveling:** Richt verlopen met het beleid van de koekjesinstemming van uw organisatie en privacyvereisten. Voor de meeste implementaties biedt 30 tot 90 dagen een redelijk evenwicht tussen de waarde van de personalisatie en de naleving van de privacy.

## Gerelateerde documentatie

De volgende Experience League-bronnen bieden aanvullende informatie over de mogelijkheden die in dit gebruikspatroon worden gebruikt.

**het kanaal van het Web en op code-gebaseerde ervaringen**

- [Aan de slag met webkanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Webervaringen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Code-gebaseerd ervaringskanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/get-started-code-based)
- [Op code gebaseerde ervaringsconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/code-based/code-based-configuration)

**Soorten publiek en segmentatie**

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

**Personalization en inhoud**

- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

**experimenteren van de Inhoud**

- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport voor inhoudexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Statistische berekeningen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-calculations)

**Beheer van het Besluit**

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Plaatsingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Beslissingsregels maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Alternatieve aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Verzamelingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

**Campagnes**

- [Aan de slag met campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)

**[!DNL Web SDK]en gegevensverzameling**

- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Web SDK installeren](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Overzicht van codes](https://experienceleague.adobe.com/en/docs/experience-platform/tags/home)

**Identiteit en profiel**

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van naamruimten](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Overzicht van het realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

**modellering van Gegevens**

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

**het Melden en de analyses**

- [Campagne live-rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [CJA-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)

**het bestuur van Gegevens en privacy**

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Overzicht van geavanceerd gegevenslevenscyclusbeheer](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)
- [Toestemming en voorkeuren, veldgroep](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

**Guardrails**

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identiteitsservicehandleidingen](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
