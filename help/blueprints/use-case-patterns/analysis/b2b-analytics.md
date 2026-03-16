---
title: B2B-analyse
description: Leer hoe u B2B-informatie op accountniveau opneemt in de analyse van de klantentransmissie over meerdere kanalen.
solution: Customer Journey Analytics, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7528'
ht-degree: 0%

---


# B2B-analyse

Deze handleiding bevat een uitgebreide implementatiereferentie voor B2B-analyses op accountniveau met [!DNL Customer Journey Analytics] ([!DNL CJA]) B2B edition en [!DNL Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition. Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die B2B-informatie op accountniveau moeten opnemen in de analyse van de klantreis over het kanaal.

Het omvat alle haalbare benaderingen voor rekenkundige analyses, van platte accountstructuren tot complexe algemene accounthiërarchieën, met richtlijnen voor de keuze van elke optie. Het plan richt B2B gegevensverbindingen, de meningsconfiguratie van de rekeningsgegevens, werkruimteanalyse, en dashboardpublicatie.

B2B Analytics breidt standaard [!DNL CJA] mogelijkheden met op rekening-gebaseerde verbindingen, B2B-specifieke containers (Rekening, Globale Rekening, Kans, de Groep van de Kopen), en rekening-vlakke rapportering uit. Met deze mogelijkheid kunnen organisaties marketing- en verkoopafspraken op accountniveau analyseren, de voortgang van de kansen volgen, de volledigheid van de inkoopgroep meten en de omzet toewijzen aan marketingaanraakpunten in uitgebreide B2B-verkoopcycli.

## Hoofdlettergebruik

B2B-organisaties staan voor een fundamentele uitdaging op het gebied van analyses: hun klanten zijn geen individuele personen, maar accounts die bestaan uit meerdere belanghebbenden, inkoopgroepen en mogelijkheden. De standaard op persoon-gebaseerde analyse kan geen vragen zoals &quot;Welke rekeningen zijn het meest betrokken?&quot;beantwoorden, &quot;Hoe volledig zijn onze koopgedrag groepen?&quot;, of &quot;Welke marketing touchpoints aandrijven opportuniteitsprogressie?&quot;

B2B-analysemogelijkheden bieden hiervoor een oplossing door [!DNL CJA] B2B edition te gebruiken om op account gerichte analytische weergaven te maken waarin gedragsgegevens op persoonlijk niveau worden gecombineerd met de dimensies account, opportunity en inkoopgroep. [!DNL RT-CDP] B2B edition biedt de onderliggende samenvoeging van het accountprofiel en de B2B-identiteitsresolutie die de analyselaag voedt. Samen, laten deze oplossingen organisaties toe om dwars-kanaal reisanalyse op rekeningsniveau te bouwen, marketing overeenkomst met pijpleidingsprogressie te correleren, en actionable inzichten aan zowel marketing als verkoopteams te leveren.

Het doelpubliek omvat B2B-marketingoperatieteams, toonaangevende producenten van vraaggeneratie, analisten van opbrengstverrichtingen en verkoopleider die zichtbaarheid op accountniveau en gezondheid van pijpleidingen nodig hebben.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

### Analyse en rapportage verbeteren

Verbeter rapporteringsmogelijkheden voor snellere, actievere marketing inzicht door verenigde dashboards en zelfbedieningshulpmiddelen. B2B-analyse stelt organisaties in staat om op accountniveau betrokkenheidsgegevens van meerdere bronnen te consolideren in één analytische omgeving, zodat ze over het kanaal kunnen zien hoe marketingprogramma&#39;s invloed hebben op pijpleidingen en inkomsten.

**KPIs:** Efficiëntie, Productiviteit

[Meer informatie over het verbeteren van analyses en rapporten](/help/blueprints/business-objectives/analytics-insights/improve-analytics-reporting.md)

### Gegevensgestuurde besluitvorming inschakelen

De teams van de macht met zelfbedienings analyses, klanteninzicht in real time, en op AI-Gebaseerde voorspellingen om strategie te begeleiden. Analyses op accountniveau zorgen ervoor dat marketing- en verkoopteams beschikken over de gegevens die nodig zijn om prioriteit toe te kennen aan accounts, betrokkenheidsstrategieën te optimaliseren en zich te richten op pijpleidingmogelijkheden.

**KPIs:** Efficiëntie, Productiviteit

[Meer informatie over het mogelijk maken van gegevensgestuurde besluitvorming](/help/blueprints/business-objectives/analytics-insights/enable-data-driven-decision-making.md)

### Kwalificatie en conversie van leads verbeteren

Verhoog de loodkwaliteit en verhoog de voortgang van de pijplijnen via scoring, verpleging en gepersonaliseerde follow-up. CJA B2B edition biedt uitgebreide terugkijkvensters voor 13 maanden die speciaal zijn ontworpen voor B2B-verkoopcycli, waardoor een nauwkeurige multi-touchattributie mogelijk is tijdens de volledige accountreis.

**KPIs:** Efficiëntie, Incrementele Inkomsten

[Meer informatie over het verbeteren van kwalificatie en conversie van leads](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

## Voorbeelden van tactische gebruiksgevallen

De volgende scenario&#39;s tonen aan hoe dit patroon in de praktijk kan worden toegepast.

- **het scoren van de overeenkomst van de Rekening analyse** — Meet en rangschikt rekeningen door hun gezamenlijke overeenkomst over Web, e-mail, gebeurtenissen, en inhoudsinteractie om high-intent rekeningen voor verkoopfollow-up te identificeren
- **het Kopen groep volledigheid die** volgt — Analyseer het kopen groepssamenstelling over rekeningen om hiaten in roldekking te identificeren en loodverwerving voorrang te geven voor onvolledige het kopen groepen
- **de pijpleidingscorrelatie van de Kans** - verwant de gegevens van de marketing overeenkomst met de progressie van het opportuniteitsstadium om te begrijpen welke campagnes en touchpoints pijpleidingsvooruitgang drijven
- **Multi-touch B2B attributie** — Pas attributiemodellen met terugkijkvensters van 13 maanden toe op credit marketing touchpoints over de volledige B2B die reis van eerste aanraking aan gesloten-won koopt
- **de vervoersafbeelding van de Rekening** — visualiseer de dwars-kanaalrekeningsreis van eerste bewustzijn door opportuniteitsverwezenlijking en sluiting, identificerend gemeenschappelijke wegen en wrijvingspunten
- **de invloed van de campagne op pijpleiding** — Meet hoe de specifieke campagnes de verwezenlijking van de rekeningspijpleiding, opportuniteitsvooruitgang, en opbrengstgeneratie beïnvloeden
- **het Kopen van de vooruitgang van de groepsovereenkomst** — Spoor hoe het kopen van de scores van de groepsovereenkomst zich in tijd evolueren en correleer betrokkenheidsdrempels met opportuniteitsresultaten
- **op rekening-gebaseerde inhoudsprestaties** — Analyseer welke inhoudsactiva en onderwerpen met specifieke rekeningssegmenten, industrieën resoneren, of het kopen van groepsrollen
- **Verkoop en marketing groeperingsdashboards** — Bouw gedeelde dashboards die zowel marketing als verkoopteams van een verenigde mening van rekeningsovereenkomst, pijpleidingsgezondheid, en opbrengstattributie voorzien
- **de segmentatie van de Rekening voor activering** — creeer B2B segmenten die op rekening-vlakke analyse (bijvoorbeeld, &quot;hoogst betrokken rekeningen zonder open kansen&quot;) worden gebaseerd en publiceer hen voor stroomafwaartse activering

## Kernprestatie-indicatoren

De volgende KPIs helpt het succes van dit gebruiks gevalpatroon meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Score voor accountbetrokkenheid | Samengevoegde betrokkenheidsmeting voor alle contactpersonen binnen een account | Berekende metrische gegevens door webbezoeken, e-mailinteracties, aanwezigheid van gebeurtenissen en het downloaden van inhoud op accountniveau te combineren |
| Voltooiing van kopersgroep | Percentage vereiste rollen ingevuld binnen een inkoopgroep | Verhouding van gevulde rollen tot de totale vereiste rollen per koopgroep, bijgehouden in de tijd |
| Pijpleiding beïnvloed door marketing | Door marketingactiviteiten aangeroerde inkomsten | De waarde van de kans waar de bijbehorende rekeningscontacten marketing aanraakpunten binnen het attributenvenster hebben |
| Omzetsnelheid account-naar-opportunity | Percentage afgesloten rekeningen die gekwalificeerde kansen genereren | Rekeningen met kansen gedeeld door totaal afgesloten rekeningen over een bepaalde periode |
| Gemiddelde Lengte van de cyclus van de Overeenkomst | Tijd van eerste marketingaanraking tot closed-won | Gemiddelde duur vanaf eerste toegewezen aanraakpunt tot aan einddatum van opportuniteit |
| Inkomsten marketingkenmerk | Ontvangsten die worden toegerekend aan marketingaanraakpunten | Inkomsten uit gesloten-won-kansen met marketingreizen, uitgedeeld per attribuutmodel |
| Accountbereik en -bescherming | Aantal contactpersonen per doelaccount | Unieke contacten met marketing interacties per rekening, in vergelijking met totale bekende contacten |
| Betrokkenheid bij inhoud door rol te kopen | Betrokkenheid wordt gesegmenteerd door de rol van de groep te kopen | Paginaweergaven, -downloads en -tijd uitgesplitst naar persoon/rol binnen inkoopgroepen |

## Hoofdletterpatroon gebruiken

**B2B analyseert**

Neem B2B-informatie op accountniveau op in de analyse van de klantentransmissie over de verschillende kanalen.

**de ketting van de Functie:** B2B- Gegevensverbinding > de Configuratie van de Mening van de Gegevens van de Rekening > de Analyse van Workspace > het Publiceren van het Dashboard

## Applicaties

De volgende toepassingen worden gebruikt om dit gebruiks gevalpatroon uit te voeren.

- **[!DNL Customer Journey Analytics]B2B edition** — Verstrekt op rekening-gebaseerde verbindingen, B2B-Specifieke containers van de gegevensmening, rekening-vlakke werkruimteanalyse, het kopen van groepsanalyse, opportuniteitsanalyse, B2B segmentatie, en B2B attributie met uitgebreide raadplegingsvensters
- **[!DNL Real-Time CDP]B2B edition** — Verstrekt de B2B gegevensstichting met inbegrip van de samenvoeging van het rekeningsprofiel, B2B identiteitsresolutie, B2B schemaklassen (Rekening, Opportunity, Kopen Groep), en [!DNL Marketo Engage] integratie voor het opnemen van B2B betrokkenheidsgegevens

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Vereist | Sandbox geconfigureerd met [!DNL CJA] B2B edition- en [!DNL RT-CDP] B2B edition-rechten. Rollen die beschikbaar zijn voor gebruikers van gegevensengineers, analisten en marketingbewerkingen met toegang tot [!DNL CJA] en het B2B-gegevensmodel. | [&#x200B; Overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home) |
| Gegevensmodellering en -voorbereiding | Vereist | B2B XDM-schema&#39;s geconfigureerd met B2B-klassen: XDM Business Account, XDM Business Opportunity, XDM Business Account Person Relation, XDM Business Opportunity Person Relation en XDM Business Marketing List-leden. Veldgroepen voor accountkenmerken, opportuniteitsfasen en het aanschaffen van groepsrollen moeten worden gedefinieerd. Datasets gemaakt en ingeschakeld voor Profiel. | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [&#x200B; schema&#39;s van B2B edition &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Gegevensbronnen en -verzameling | Vereist | B2B-gegevensbronnen aangesloten, doorgaans via de [!DNL Marketo Engage] bronconnector of [!DNL Salesforce] CRM-bronconnector. De verslagen van de rekening, opportunityverslagen, persoon-rekening verhoudingen, en de gebeurtenissen van de gedragsovereenkomst moeten in de datasets van AEP stromen. [!DNL Web SDK] of [!DNL Marketo] integratie moet gedragsgebeurtenissen vastleggen met accountassociatie. | [&#x200B; Bronoverzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [&#x200B; schakelaar van Marketo Engage &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identiteit en profielconfiguratie | Vereist | B2B-identiteitsresolutie geconfigureerd om relaties van persoon tot account op te lossen. De account-id, de persoon-id ([!DNL Marketo] hoofd-id of CRM-contactpersoon) en de identiteit van de andere apparaten (ECID, e-mail) moeten worden gekoppeld. De grafiek van de identiteit moet vele-aan-vele persoon-aan-rekening afbeelding steunen inherent aan B2B gegevensmodellen. | [&#x200B; Overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [&#x200B; B2B identiteitsresolutie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b) |
| Auditiedefinitie en segmentatie | Verondersteld op plaats | Accountniveau-publieksdefinities moeten beschikbaar zijn als B2B-segmenten van [!DNL CJA] naar AEP worden gepubliceerd voor activering. In gevallen waarin alleen analytische gegevens worden gebruikt, is dit geen strikte voorwaarde, maar wordt het aanbevolen voor segmentanalyse. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Berekende kenmerken op accountprofielen (bijvoorbeeld totale betrokkenheidsscore, aantal dagen sinds laatste activiteit, aantal kansen) verrijken de analytische dimensies die beschikbaar zijn in [!DNL CJA] voor accountanalyse. | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | B2B-gegevenssets, met name gedragsgebeurtenisgegevens van [!DNL Marketo Engage], kunnen snel groeien. Het beleid voor het verlopen van gegevenssets helpt opslag te beheren en ervoor te zorgen dat de vereisten voor gegevensbewaring worden nageleefd. | [&#x200B; het Geavanceerde Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | B2B-gegevens bevatten vaak gevoelige bedrijfsinformatie (contractwaarden, competitieve intelligentie). Met labels voor gegevensgebruik en het beleid voor beheer wordt ervoor gezorgd dat deze gegevens op de juiste wijze worden gebruikt voor alle workflows voor analyses en activering. | [&#x200B; Overzicht van het beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Bewaking en waarneming | Aanbevolen | B2B-bronconnectors ([!DNL Marketo], [!DNL Salesforce]) vereisen bewaking voor de gezondheid van inname. Bewaking van de verbindingsstatus in [!DNL CJA] zorgt voor gegevensversheid voor analyses. Waarschuwingsregels voor mislukte inname verhinderen vaststaande dashboards. | [&#x200B; overzicht van de Inzichten van de Waarnemelijkheid &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | Dit patroon is zelf een analysepatroon. Deze functie wordt van nature opgenomen omdat de kernfunctieketen rapportage- en analysemogelijkheden biedt. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Customer Journey Analytics] B2B edition

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Verbinding op basis van account | Fase 1: B2B-gegevensverbinding | Verbindingen configureren met Account of Global Account als primaire id voor analyse op organisatieniveau |
| Configuratie van B2B-gegevensweergave | Fase 2: Configuratie van weergave accountgegevens | Definieer gegevensweergaven met B2B-specifieke containers (Account, Global Account, Opportunity, Buying Group) naast standaardcontainers voor personen, sessies en gebeurtenissen |
| Workspace-analyse op accountniveau | Fase 3: Workspace-analyse | Bouw freeform analyse gebruikend rekeningsniveauafmetingen, metriek, en B2B containers voor organisatie-vlakke reisinzichten |
| Analyse van kopersgroep | Fase 3: Workspace-analyse | De samenstelling, betrokkenheid en voortgang van inkoopgroepen analyseren via het aankoopbeslissingsproces |
| Opportuniteitsanalyse | Fase 3: Workspace-analyse | Houd de opportuniteitsvoortgang bij door de verkoop in funnel-fasen en houd rekening met de gegevens van de marketingservice |
| B2B-segmentering | Fase 3: Workspace-analyse | Segmenten maken met behulp van B2B-containers voor gefilterde analyse op accountniveau |
| B2B-kenmerk | Fase 3: Workspace-analyse | Pas attributiemodellen met uitgebreide 13-maands accountopzoekvensters toe voor B2B-analyse van verkoopcycli |
| Berekend metrisch ontwerp | Fase 3: Workspace-analyse | Definieer de berekende maatstaven voor B2B-PKI&#39;s, zoals de betrokkenheidsgraad van de account, de volledigheid van de inkoopgroep en de invloed van de pijpleiding |
| Publiceren op dashboard en scorebord | Fase 4: Publiceren van dashboard | Dashboards en delen mobiele scorecards voor marketing en verkoopleiderschap |
| Publiek publiceren | Fase 4: Publiceren van dashboard | [!DNL CJA] gedefinieerde publiek op basis van account terugsturen naar AEP voor activering achteraf |

### [!DNL Customer Journey Analytics] — standaardfuncties

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Gegevensverbinding | Fase 1: B2B-gegevensverbinding | AEP B2B-gegevenssets binden aan [!DNL CJA] -verbindingen voor kanaalanalyse |
| Configuratie gegevensweergave | Fase 2: Configuratie van weergave accountgegevens | Standaardafmetingen, metriek, attributie, en persistentie montages binnen de B2B gegevensmening vormen |
| Workspace-analyse | Fase 3: Workspace-analyse | Maak vrije-vormanalyse met lijsten, fallout, stroom, cohort, en attributievisualisaties |
| Begeleide analyse | Fase 3: Workspace-analyse | Geleide workflows gebruiken voor funnel, trends en retentieanalyse op accountniveau |

### [!DNL Real-Time CDP] B2B edition

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Account Profile Unification | Vereiste (F2/F4) | Consolidatie van B2B-gegevens voor meerdere bronnen in geconsolideerde accountprofielen met behulp van gespecialiseerde XDM B2B-schemaklassen |
| B2B-identiteitsresolutie | Vereiste (F4) | Los van persoon tot rekening verhoudingen ondersteunend multi-level rekeningshiërarchieën en veel-aan-vele afbeeldingen op |
| [!DNL Marketo Engage] Integratie | Vereiste (F3) | Gegevens over gedragsbetrokkenheid en account/lead-records uit [!DNL Marketo Engage] via native B2B-bronconnectors verzamelen |

## Vereisten

De volgende items moeten aanwezig zijn voordat de implementatie begint.

- [!DNL CJA] B2B edition-licentie is actief en is ingericht voor de organisatie
- [!DNL RT-CDP] B2B edition-licentie is actief met geconfigureerde B2B-schema&#39;s en -accountprofielen
- B2B XDM-schema&#39;s zijn gedefinieerd (Account, Opportunity, Account Person Relatie, Opportunity Person Relatie, Marketing List members)
- [!DNL Marketo Engage] en/of CRM-bronconnectors zijn geconfigureerd en nemen actief gegevens op
- Gedragsgegevens op accountniveau (webbezoeken, e-mailinteracties, formulierverzendingen) stromen naar AEP met accountassociatie
- Relaties van persoon tot rekening worden vastgesteld in de identiteitsgrafiek
- Er zijn ten minste 30 dagen historische gegevens over de B2B-betrokkenheid beschikbaar voor een zinvolle analyse
- Belanghebbenden zijn het eens geworden over het aanschaffen van rolinedefinities van groepen en het toewijzen van rente voor oplossingen
- [!DNL CJA] -gebruikersaccounts beschikken over de juiste productprofielen voor B2B edition-functies
- DoelKPI&#39;s en rapportagevereisten zijn gedefinieerd door marketing- en verkoopleiderschap

## Implementatieopties

De volgende secties beschrijven verschillende benaderingen voor het uitvoeren van dit gebruiks gevalpatroon.

### Optie A: Accountgerichte analyse

**Best voor:** Organisaties die alle overeenkomst en pijpleidingsgegevens door de lens van de rekening willen analyseren. Deze benadering gebruikt de container van de Rekening als primaire analytische eenheid, die een top-down mening verstrekt van hoe de rekeningen door de het kopen reis vorderen.

**hoe het werkt:**

Configureer een [!DNL CJA] B2B-verbinding met Account als primaire id. Alle gedragsgebeurtenissen, kansen, en het kopen van groepsgegevens rollen tot het rekeningsniveau. In de gegevensweergave wordt Account gebruikt als container op het hoogste niveau, waarbij Person, Session en Event erin zijn genest. Dit laat analyse als &quot;toe hoeveel rekeningen bezocht de het tarief pagina en creeerde dan een kans binnen 30 dagen?&quot;

Accountgerichte analyse biedt de meest natuurlijke weergave voor B2B-organisaties waarbij de account de aankoopeenheid is. Dimensies zoals de industrie, bedrijfsgrootte, accountlaag en accounteigenaar kunnen worden gebruikt om betrokkenheidspatronen en pijpleidingmetriek af te splitsen. Attributie wordt toegepast op het rekeningsniveau met 13 maanden raadplegingsvensters die lange B2B verkoopcycli aanpassen.

**Zeer belangrijke overwegingen:**

- Vereist een schone account-aan-persoontoewijzing in de identiteitsgrafiek
- Alle gebeurtenissen op persoonniveau moeten aan een rekening kunnen worden toegerekend
- Anonieme webberichten die niet aan een account kunnen worden gekoppeld, worden niet weergegeven in een analyse op accountniveau

**Voordelen:**

- Verstrekt een ware rekening-vlakke mening van de volledige het kopen reis
- Hiermee wordt op een rekening gebaseerde attributie ingeschakeld die overeenkomt met de manier waarop B2B-inkomsten worden gegenereerd
- Steunt het kopen groep en opportuniteitsanalyse als genestelde containers binnen de rekening
- Hiermee worden analyses uitgelijnd op de ABM-strategie (account based marketing)

**Beperkingen:**

- Vereist robuuste oplossing voor identiteit van persoon tot account
- Anonieme of niet-overeenkomende betrokkenheidsgegevens worden niet meegenomen in de analyse
- Complexer te configureren dan persoonlijke analyses

**Experience League:**

- [CJA B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [B2B edition-schema&#39;s](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)

### Optie B: Globale analytische analyse op basis van account

**Best voor:** de organisaties van de onderneming met complexe rekeningshiërarchieën waar een ouderbedrijf veelvoudige dochterrekeningen heeft. Bij deze benadering wordt Global Account als primaire id gebruikt, waarbij alle activiteiten van de ondergeschikte account worden uitgebreid tot het niveau van de moederorganisatie.

**hoe het werkt:**

Configureer de [!DNL CJA] B2B-verbinding met Global Account als primaire id in plaats van als Account. Dit aggregeert de gegevens over de betrokkenheid van alle secundaire rekeningen onder hun moederorganisatie. Als &quot;Acme Corp&quot; bijvoorbeeld regionale dochterondernemingen &quot;Acme EMEA&quot; en &quot;Acme APAC&quot; heeft, consolideert een globale accountverbinding alle betrokkenheid van alle drie entiteiten in één analytische weergave.

De gegevensweergave bevat Global Account als container op hoofdniveau, met Account, Person, Session en Event als geneste containers. Dit maakt analyse op zowel het globale als subsidiaire rekeningsniveau binnen het zelfde werkruimteproject mogelijk. De terugkijkvensters van de attributie zijn op het globale rekeningsniveau van toepassing, die alle aanraakpunten over de volledige collectieve hiërarchie vangen.

**Zeer belangrijke overwegingen:**

- Vereist de gegevens van de rekeningshiërarchie met ouder-kind verhoudingen die in het B2B gegevensmodel worden bepaald
- De globale account-id moet in alle accountrecords worden ingevuld en correct zijn
- Subsidiaire rekeningen moeten correct aan hun moedermaatschappij worden toegewezen

**Voordelen:**

- Biedt geconsolideerde zichtbaarheid over complexe bedrijfsaccountstructuren
- Voorkomt gefragmenteerde analyse wanneer één enkele ondernemingsklant veelvoudige rekeningsverslagen heeft
- Maakt vergelijking tussen regionale dochterondernemingen binnen één enkele globale rekening mogelijk
- Ondersteunt pijplijn- en inkomstenrapportage op ondernemingsniveau

**Beperkingen:**

- Vereist nauwkeurige gegevens van de rekeninghiërarchie, die veel organisaties moeite hebben te handhaven
- Mogen patronen op secundair niveau onzichtbaar zijn wanneer ze alleen op mondiaal niveau worden bekeken
- Aanvullende inspanningen voor gegevensmodellering om hiërarchische relaties tot stand te brengen en te handhaven

**Experience League:**

- [CJA B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Optie C: Hybride persoon + accountanalyse

**Best voor:** Organisaties die van op persoon-gebaseerde analyses aan op rekening-gebaseerde analyses overgaan, of die die zowel persoon-vlakke als rekening-vlakke meningen nodig hebben. Deze benadering leidt tot twee gegevensmeningen van de zelfde verbinding - één persoon-centric en één rekening-centric.

**hoe het werkt:**

Configureer één [!DNL CJA] B2B-verbinding die alle B2B-gegevenssets bevat (gebeurtenis, account, opportuniteit, inkoopgroep, relaties tussen personen en accounts). Maak vervolgens twee gegevensweergaven: een met Person als primaire container (vergelijkbaar met standaard [!DNL CJA] ) en een met Account als primaire container. Analysten kunnen schakelen tussen gegevensweergaven afhankelijk van de vraag die wordt gesteld.

De persoon-centric gegevensmening verstrekt traditionele individuele reis analyse op niveau (bijvoorbeeld, &quot;wat is de omzettingsweg voor lood die kansen worden?&quot;), terwijl de rekening-centric gegevensmening organisatie-vlakke analyse verstrekt (bijvoorbeeld, &quot;Welke rekeningen hebben de hoogste overeenkomst-aan-pijpleiding omzettingspercentage?&quot;). In beide weergaven worden dezelfde onderliggende gegevens gebruikt, zodat consistentie wordt gegarandeerd.

**Zeer belangrijke overwegingen:**

- Vereist twee gegevensmeningen met potentieel verschillende afmeting en metrische configuraties
- Analyses hebben een training nodig voor het gebruik van elke weergave
- Het is mogelijk dat voor elke gegevensweergave afzonderlijk computergegevens moeten worden gemaakt

**Voordelen:**

- Biedt flexibiliteit voor het analyseren van gegevens op zowel persoon- als accountniveau
- Eenvoudiger acceptatiepad voor teams die vertrouwd zijn met persoonlijke analyses
- Maakt vergelijking mogelijk tussen cijfers op persoonlijke en op accountniveau
- Steunt zowel op lood-gebaseerde als op rekening-gebaseerde marketing strategieën

**Beperkingen:**

- Twee gegevensweergaven voor onderhoud en synchronisatie
- Mogelijke verwarring voor analisten over welk gezichtsveld wordt gebruikt
- Berekende metriek en filters hebben mogelijk duplicatie nodig voor verschillende weergaven

**Experience League:**

- [Een gegevensweergave maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Overzicht van gegevensweergaven](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)

### Optievergelijking

| Criteria | Option A: op account gericht | Optie B: Globaal op account gericht | Optie C: Hybride persoon + rekening |
| --- | --- | --- | --- |
| Best voor | Standaard B2B met platte rekeningstructuur | Onderneming met ouder-kind hiërarchieën | Overgangsorganisaties of dubbele behoeften |
| Complexiteit | Gemiddeld | Hoog | Medium-High |
| Gegevensvereisten | Toewijzing van accountants | Accounthiërarchie + toewijzing | Toewijzing van accountants |
| Attributiebereik | Accountniveau (13 maanden terugzoekactie) | Globaal accountniveau (13 maanden terugzoekactie) | Zowel persoon- als rekeningniveau |
| Anonieme gegevens | Uitgesloten van accountweergave | Uitgesloten van algemene weergave | Opgenomen in weergave Personen, uitgesloten van accountweergave |
| Vereisten | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition, hiërarchiegegevens | [!DNL RT-CDP] B2B edition, [!DNL CJA] B2B edition |
| Onderhoudsinspanning | Eén gegevensweergave | Eén gegevensweergave | Twee gegevensweergaven |

### Kies de juiste optie

- **kies Optie A** als uw organisatie een vlakke rekeningsstructuur (geen ouder-kind hiërarchieën) heeft, werkt uw strategie ABM op het individuele rekeningsniveau, en u wilt de eenvoudigste weg aan rekening-vlakke analyses.
- **kies Optie B** als uw doelrekeningen grote ondernemingen met dochterondernemingen rekeningen over gebieden of afdelingen zijn, en u geconsolideerde rapportering op het collectieve ouderniveau nodig hebt. Voor deze optie zijn hiërarchische gegevens van hoge kwaliteit vereist.
- **kies Optie C** als uw organisatie van lood-gebaseerde aan rekening-gebaseerde marketing overgaat, uw analisten zowel persoon-vlakke analyse van funnel en rekening-vlakke betrokkenheidsanalyse nodig hebben, of u hebt een mengeling van B2B en B2C bedrijfslijnen.

## Uitvoeringsfasen

In de volgende fasen wordt de aanbevolen implementatiereeks beschreven.

### Fase 1: B2B-gegevensverbinding

**functie van de Toepassing:** [!DNL CJA] B2B: Op rekening-Gebaseerde Verbinding, [!DNL CJA]: De Verbinding van gegevens

Configureer de [!DNL CJA] -verbinding die uw AEP B2B-gegevenssets bindt aan [!DNL CJA] voor analyse. Deze verbinding bepaalt welke datasets in [!DNL CJA] stromen, het primaire herkenningstype (Rekening of Globale Rekening), en hoe historische en het stromen gegevens worden opgenomen. De verbinding is de basis van alle volgende analyses.

#### Besluit: type primaire identificatiecode

Bepaal of voor de verbinding de account-id of de algemene account-id als primaire id moet worden gebruikt.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Account-id | Platte accountstructuur, geen bovenliggende/onderliggende hiërarchieën | Eenvoudiger instellen; elk account wordt onafhankelijk geanalyseerd. Meest gangbare keuze voor op het MKB gerichte B2B. |
| Globale account-id | Enterprise-accounts met secundaire hiërarchieën | Vereist hiërarchische gegevens; aggregeert alle dochterondernemingen onder moedermaatschappij. Best voor ABM-programma&#39;s voor bedrijven. |

#### Besluit: keuze van de gegevensset en typeaanduiding

Bepaal welke B2B-gegevenssets moeten worden opgenomen en hoe elk moet worden getypt.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Gegevenssets voor gebeurtenissen (gedrag) | Altijd opnemen | Webinteracties, e-mailgebeurtenissen, formulierverzendingen en het downloaden van inhoud. Moet een tijdstempelveld hebben. Dit zijn de betrokkenheidssignalen. |
| Gegevensbestanden voor accountrecords (profiel) | Altijd opnemen | Accountkenmerken zoals industrie, grootte, laag, eigenaar. Biedt de dimensionale context voor accountanalyse. |
| Opportuniteitsgegevenssets (opzoeken/profiel) | Opnemen voor analyse van pijpleidingen | Het werkgebied van de opportuniteit, waarde, einddatum. Vereist voor analyse van pijpleidingen en inkomstentoerekening. |
| Gegevenssets van groepen kopen (opzoeken/profiel) | Opnemen voor groepsanalyse voor kopen | Groeprollen, betrokkenheidsscores, volledigheid kopen. Vereist voor het kopen van de analyse van de groepssamenstelling. |
| Gegevensbestanden betreffende persoonlijke relaties (opzoekhandeling) | Altijd opnemen | Hiermee kunt u personen toewijzen aan accounts. Kritiek voor het associëren van persoon-vlakke gebeurtenissen met account-vlakke analyse. |
| Gegevensbestanden campagne/programma (opzoekopdracht) | Opnemen voor toewijzing | Campagne metagegevens, programmatypen, kanalen. Laat campagneinvloedanalyse toe. |

#### Besluit: bereik achtergrondvulling

Bepaal hoeveel historische gegevens in de verbinding moeten worden geïmporteerd.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alle bestaande gegevens | B2B verkoopcycli zijn lang (6-18 maanden) en u hebt volledige historie nodig | Aanbevolen voor B2B. De backfill kan dagen duren voor grote datasets, maar biedt volledige toewijzingsgegevens. |
| Aangepast datumbereik (afgelopen 2-3 jaar) | De gegevenskwaliteit neemt af na een bepaald punt | Hiermee wordt de volledigheid afgewogen tegen de gegevenskwaliteit. Vaak wanneer CRM-gegevens historische inconsistenties hebben. |
| Geen backfill | Uitsluitend testen of ontwikkelen | Alleen nieuwe gegevens worden doorgegeven. Niet geschikt voor B2B-productie. |

#### B2B-gegevensverbinding configureren

**navigatie UI:** [!DNL Customer Journey Analytics] > Verbindingen > creëren nieuwe verbinding

Belangrijke configuratiedetails:

- De AEP-sandbox met B2B-gegevenssets selecteren
- Het gemiddelde aantal dagelijkse gebeurtenissen voor capaciteitsplanning instellen
- Voeg elke dataset toe en wijs zijn type (gebeurtenis, raadpleging, of profiel) aan
- Het veld Personen-id configureren voor gebruik van account-id of Globale account-id voor B2B-verbindingen
- Laat het stromen voor datasets toe die bijna-real-time updates vereisen
- &quot;Alle bestaande gegevens importeren&quot; inschakelen voor historische backfill

**waar de opties uiteenlopen:**

**voor Optie A (rekening-centric):**
Stel de primaire id in op Account ID. Voeg accountrecord, opportuniteit, inkoopgroep en gegevens over persoonlijke relaties toe. Vorm persoon-vlakke gebeurtenisdatasets met het gebied van identiteitskaart van de Rekening voor dwars-dataset het toetreden.

**voor Optie B (Globale rekening-Centric):**
Stel de primaire id in op Globale account-id. Zorg ervoor dat de hiërarchiegegevens van de account het veld Globale account-id bevatten. Alle datasets moeten of aan Globale identiteitskaart van de Rekening voor juiste roll-up omvatten zijn.

**voor Optie C (Hybride):**
Creeer één enkele verbinding met alle B2B datasets. Account-id gebruiken als primaire id. De persoon-centric mening zal in Fase 2 door een verschillende configuratie van de gegevensmening op de zelfde verbinding te gebruiken worden gecreeerd.

**documentatie van Experience League:**

- [Overzicht van verbindingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Verbinding maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Verbindingen beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)
- [CJA B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### Fase 2: Configuratie van weergave accountgegevens

**functie van de Toepassing:** [!DNL CJA] B2B: B2B de Configuratie van de Mening van Gegevens, [!DNL CJA]: De Configuratie van de Mening van Gegevens

Vorm de gegevensmening die bepaalt hoe de verbindingsgegevens in analyse verschijnen. Voor B2B-analyses omvat dit het configureren van B2B-specifieke containers (Account, Opportunity, Buying Group), het toewijzen van B2B-schemavelden aan dimensies en metriek, het instellen van toewijzingsmodellen met B2B-geschikte terugzoekvensters en het maken van afgeleide velden voor B2B-bedrijfslogica.

#### Besluit: Containerconfiguratie

Bepaal welke B2B containers zouden moeten worden toegelaten en hoe zij zouden moeten worden genoemd.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Account + Persoon + Sessie + Gebeurtenis | Standaard B2B zonder inkoopgroep- of opportuniteitsanalyse | Eenvoudige B2B-containerhiërarchie. Account is de container op hoofdniveau. |
| Account + Opportunity + Persoon + Sessie + Gebeurtenis | Analyse van pijpleidingen en inkomsten vereist | Voegt kansen als containerniveau toe, toelatend kansen-scoped analyse. |
| Account + kopersgroep + Opportunity + Person + Sessie + Gebeurtenis | Volledige B2B-analyse met inbegrip van de samenstelling van de inkoopgroep | Uitgebreid. Laat analyse op elk niveau van het B2B gegevensmodel toe. |
| Globale account + account + persoon + sessie + gebeurtenis | Algemene analyse van de accounthiërarchie | Hiermee voegt u Global Account toe als container op het hoogste niveau boven Account. |

#### Besluit: Attributiemodel voor B2B-meetgegevens

Bepaal welk toewijzingsmodel standaard moet worden gebruikt voor conversiewaarden.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Lineaire toewijzing (13 maanden terugblik) | Gelijk krediet voor alle aanraakpunten op de B2B-reis | Dit is het meest geschikt voor een goed begrip van de volledige mix van marketingactiviteiten. Aanbevolen beginpunt voor B2B. |
| U-vormige attributie (13 maanden terugblik) | Nadruk op eerste en laatste aanraking met krediet aan middelste aanrakingen | Belangrijkste punten voor creatie en conversie van kansen. Algemeen in de analyse van de vraaggeneratie. |
| Tijdverlies (13 maanden terugblik) | Recentere aanraakpunten zouden meer krediet moeten krijgen | Het beste wanneer de recenentie van overeenkomst een belangrijk signaal voor verkoopbereidheid is. |
| Laatste aanraking | Eenvoudige rapportage van het laatste aanraakpunt vóór de conversie | Eenvoudig te begrijpen, maar onderwaardeert de marketing in een vroeg stadium. Alleen gebruiken voor snelle operationele rapportage. |

#### Besluit: Sessiedefinitie voor B2B

Bepaal hoe sessies moeten worden gedefinieerd voor B2B-betrokkenheid.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Tijdslimiet van 30 minuten (standaard) | Standaardgedrag voor sessie via webanalyse | Standaard voor webserviceanalyse. Kan lange sessies voor inhoudsverbruik fragmenteren. |
| Uitgebreide time-out (60-120 minuten) | B2B-gebruikers nemen langere onderzoekssessies aan | B2B-kopers besteden vaak uitgebreide tijd aan het controleren van technische inhoud, prijzen en documentatie. |
| Nieuwe sessie op basis van gebeurtenissen | Specifieke gebeurtenissen moeten altijd een nieuwe sessie starten | Gebruik deze optie wanneer u met het klikken op een campagne of het aanvragen van een demo altijd een nieuwe analytische sessie moet starten. |

#### De weergave met accountgegevens configureren

**navigatie UI:** [!DNL Customer Journey Analytics] > de meningen van Gegevens > creëren nieuwe gegevensmening

Belangrijke configuratiedetails:

- Selecteer de verbinding die in Fase 1 is gemaakt
- Vorm tijdzone en kalendertype aangewezen voor de organisatie
- Naam van containers wijzigen in B2B-relevante terminologie (bijvoorbeeld Account/Betrokkenheid/Touchpoint)
- B2B-schemavelden toewijzen aan dimensies: accountnaam, account-id, industrie, bedrijfsgrootte, accountlaag, rekeningeigenaar, opportuniteitsfase, opportuniteitswaarde, inkoopgroeprol, belang van oplossing
- Metrische gegevens over betrokkenheid toewijzen: gebeurtenissen (voorvallen), personen, sessies, paginaweergaven, formulierverzendingen, e-mailopenen, klikken op e-mail
- Configureer persistentie voor belangrijke dimensies (de accountsector blijft bijvoorbeeld op accountniveau bestaan)
- Toekenning op lineair instellen met een zoekfunctie van 13 maanden als standaard voor conversiemetriek
- Maak afgeleide velden voor de classificatie van marketingkanalen, betrokkenheidsscores en opportuniteitswerkgebiedgroepering

**waar de opties uiteenlopen:**

**voor Optie A (rekening-centric):**
Vorm één enkele gegevensmening met Rekening als top-level container. Omvat de containers van de Opportunity en van de Groep van de Kopen als de pijpleiding en het kopen groepsanalyse nodig is.

**voor Optie B (Globale rekening-Centric):**
Vorm Globale Rekening als top-level container. Account opnemen als subcontainer om zowel algemene als subsidiaire analyse mogelijk te maken.

**voor Optie C (Hybride):**
Maak twee gegevensweergaven via dezelfde verbinding. Gegevensweergave 1 gebruikt Person als primaire container (standaard [!DNL CJA] gedrag). De Mening 2 van gegevens gebruikt Rekening als primaire container met B2B containers. Wijs identieke metriek toe aan beide meningen waar toepasselijk.

**documentatie van Experience League:**

- [Overzicht van gegevensweergaven](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Een gegevensweergave maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Overzicht van componentinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributie-instellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Afgeleide velden](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Sessieinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

### Fase 3: Workspace-analyse

**de functie van de Toepassing:** [!DNL CJA] B2B: de Analyse van de Rekening-Vlakke Workspace, het Kopen van de Analyse van de Groep, de Analyse van de Kans, B2B Segmentation, B2B Attributie, [!DNL CJA]: De Analyse van Workspace, Berekende Metrische Creatie, Geleide Analyse

Bouwen werkruimteprojecten die de analytische inzichten leveren die in KPIs worden bepaald. Deze fase omvat het bouwen van vrije-vormlijsten met B2B dimensies en metriek, het creëren van gegevens gegevens voor B2B KPIs, het vormen B2B-specifieke visualisaties (rekening-vlakke stroom, kansenfunnel, het kopen groepsovereenkomst), het creëren van filters/segmenten gebruikend B2B containers, en het toepassen van B2B attributiemodellen.

#### Besluit: structuur van de analysewerkruimte

Bepaal hoe het werkruimteproject zou moeten worden georganiseerd.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Eén uitgebreid project met meerdere deelvensters | Het kleine team, alle belanghebbenden bekijken de zelfde rapporten | Eenvoudiger te onderhouden. Gebruik deelvensters om onderwerpen (betrokkenheid, pijpleiding, toewijzing) te scheiden. Tot 40 panelen per project. |
| Meerdere gerichte projecten per publiek | Verschillende belanghebbenden hebben verschillende weergaven nodig | Marketing krijgt betrokkenheid/attributie. De verkoop krijgt pijpleiding/rekeningsgezondheid. Bewerkingen krijgen gegevenskwaliteit. Meer onderhoud, maar beter gericht. |
| Op een sjabloon gebaseerde projecten met geleide analyse | Zelfbedieningsanalyses voor niet-deskundige gebruikers | Gebruik geleide analyse voor funnel en trendmeningen. Opslaan als sjablonen voor herhaalbare analyse. Meest geschikt voor brede adoptie. |

#### Besluit: B2B berekende cijfers

Bepaal welke berekende metriek nodig zijn voor B2B KPIs.

| Metrisch | Formule | Wanneer maakt u |
| --- | --- | --- |
| Betrokkenheid account | (Totaal aantal accountgebeurtenissen / Totaal aantal accounts) | Altijd — kern-B2B-metrisch |
| Volledige kopersgroep % | (Gevulde rollen / Vereiste rollen) * 100 | Wanneer u groepsanalyse koopt, valt deze binnen het bereik |
| Omzetting account-naar-opportunity | Accounts met opportunity/Engaged Accounts | Wanneer pijpleidingsanalyse nodig is |
| Invloed pijpleiding % | Influed waarde pijpleiding/Totale waarde pijpleiding | Wanneer marketingtoewijzing vereist is |
| Gemiddelde betrokkenheid per contactpersoon | Gebeurtenissen / unieke personen per account | Wanneer een analyse van de rekeningpenetratie nodig is |
| Inhoudsbetrokkenheid bij rol | Gebeurtenissen gefilterd op Rol van groep kopen | Als de inhoud voor B2B moet worden geoptimaliseerd |

#### Besluit: B2B-filter/segmentbereik

Bepaal bij welke containerniveaufilters moeten worden gemaakt.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Filters op accountniveau | Analyse binnen het bereik van de rekeningen die aan criteria voldoen (bijvoorbeeld ondernemingsrekeningen, specifieke industrieën) | Omvat alle gebeurtenissen van in aanmerking komende accounts. Meestal voor B2B. |
| Filters op opportuniteitsniveau | Analyse binnen bereik van specifieke opportuniteitstypen of -stadia | Omvat alle gebeurtenissen verbonden aan kwalificerende kansen. |
| Filters op groepsniveau kopen | Analyse binnen bereik van specifieke inkoopgroepstatussen | Omvat gebeurtenissen van mensen in in aanmerking komende koopgroepen. |
| Filters op persoonlijk niveau | Analyse binnen bereik van personen die aan criteria voldoen (bijvoorbeeld specifieke rollen, titels) | Standaardfiltergedrag. Wordt gebruikt bij het analyseren van individuele betrokkenheid binnen de B2B-context. |

#### De werkruimte-analyse maken

**navigatie UI:** [!DNL Customer Journey Analytics] > Workspace > Projecten > tot project leiden

Belangrijke configuratiedetails:

- Selecteer de B2B-gegevensweergave die in Fase 2 is gemaakt
- Vrije-vormtabellen maken met afmetingen op accountniveau (accountnaam, industrie, niveau), uitgesplitst naar betrokkenheidsmaatstaven
- Maak kansen voor funnel-visualisaties en laat de kans zien door de fasen heen te gaan
- Bouw het kopen van de lijsten van de groepssamenstelling die rolvullingen en overeenkomst per rol tonen
- Deelvensters voor B2B-attributie configureren waarin attributiemodellen (lineair, U-vormig, tijdverlies) worden vergeleken met 13 maanden terugzoekactie
- Maak een overzicht van uw accountstromen en geef deze algemene paden weer tijdens de koopreis
- Cohortabellen samenstellen voor het analyseren van het behoud en opnieuw inbrengen van accounts in de loop van de tijd
- B2B-filters toepassen op segmentanalyse op accountniveau, in de branche of op betrokkenheidsniveau
- Annotaties maken voor belangrijke gebeurtenissen (startprogramma&#39;s voor campagnes, productreleases, prijswijzigingen)

**documentatie van Experience League:**

- [Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Een project maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Vrije-vormtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Kenmerk, deelvenster](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Stroomvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Uitvalvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohortingtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Overzicht van filters](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Overzicht van berekende metriek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berekende waarden maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Overzicht van annotaties](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Overzicht van geleide analyse](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Afmetingen onderverdelingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

### Fase 4: Publiceren op dashboard

**de functie van de Toepassing:** [!DNL CJA]: Het Publiceren van het Dashboard &amp; van het Scorecard, [!DNL CJA]: het Publiceren van de Publiek

Maak deelbare dashboards en mobiele scorecards die de belanghebbenden inzicht geven in B2B-analysemogelijkheden. Deze fase omvat ook het publiceren van [!DNL CJA] gedefinieerde B2B-doelgroepen naar AEP voor activering in gevallen van downstreamgebruik, zoals activering van het B2B-publiek.

#### Besluit: leveringsmethode dashboard

Bepalen hoe de inzichten van B2B-analyses aan de belanghebbenden moeten worden verstrekt.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Workspace-project (bureaublad) | Analysten en marketingactiviteiten die interactieve verkenning nodig hebben | Volledige interactiviteit, boor-neer, filterknevel. Vereist [!DNL CJA] toegang. |
| Mobiele scorecard | Managers en verkoopleiders die KPI&#39;s in één oogopslag nodig hebben | Samenvattingsgetallen met trendlijnen. Toegankelijk via de [!DNL Adobe Analytics] -app dashboards. Beperkte interactiviteit. |
| Geplande PDF/CSV-export | Belanghebbenden zonder [!DNL CJA] toegang die regelmatig updates nodig hebben | Geautomatiseerde levering volgens een schema. Geen interactiviteit. Meest geschikt voor wekelijkse/maandelijkse samenvattingen. |
| Alle bovenstaande elementen | Grote organisaties met uiteenlopende behoeften van belanghebbenden | Maximaal bereik. Hoger onderhoud. Aanbevolen voor rijpe B2B-analyseprogramma&#39;s. |

#### Besluit: Publiek publiceren vanuit [!DNL CJA]

Bepaal of B2B-segmenten voor activering naar AEP moeten worden gepubliceerd.

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Advertenties op basis van account publiceren | Analytische inzichten moeten gericht op en onderdrukt | Schakelt activering van [!DNL CJA] gedefinieerde segmenten (bijvoorbeeld &#39;accounts met hoge betrokkenheid zonder open kansen&#39;) via [!DNL RT-CDP] in. Vernieuwingsfrequentie: 4 uur tot week. |
| Niet publiceren | Analyses zijn alleen bedoeld voor rapportage, niet voor activering | Eenvoudigere configuratie. Activering wordt afzonderlijk afgehandeld in [!DNL RT-CDP] . |

#### dashboards en publiek publiceren

**navigatie UI:** [!DNL Customer Journey Analytics] > Projecten > Aandeel (voor Workspace), Projecten > creëren > Mobiele scorecard (voor scorecards), Componenten > Soorten > Publiceren (voor publiekspublicatie)

Belangrijke configuratiedetails:

- Samenstellen van dashboards met samenvattingsnummers voor de belangrijkste B2B-KPI&#39;s (totaal opgenomen rekeningen, waarde van pijpleidingen, volledigheid van inkoopgroep)
- Vergelijkingsperiodes (maand-over-maand, kwartaal-over-kwartaal) voor trendindicatoren configureren
- Mobiele scorecards maken met tegels voor accountbetrokkenheid, de status van de pijpleiding en kenmerken
- Voeg filters voor managers toe om meningen door gebied, industrie, of rekeningsrij van een knevel te voorzien
- Geplande projectlevering voor wekelijkse uitvoerende rapporten configureren
- Voor publiek publiceren: selecteer het filter B2B, vorm de identiteit namespace (identiteitskaart van de Rekening ID), en plaats verfrist cadence

**documentatie van Experience League:**

- [Een mobiele scorecard maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [Projecten delen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Projecten plannen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [scorecards configureren en beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-dashboards — handleiding](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)
- [Overzicht publiek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Soorten publiek maken en publiceren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)

## Implementatieoverwegingen

In de volgende secties worden onder andere de volgende secties beschreven: guardrails, valkuilen, best practices en beslissingen om zaken af te handelen, waarmee u tijdens de implementatie rekening kunt houden.

### Guardrails en limieten

- [!DNL CJA] de verbindingen kunnen datasets van slechts één zandbak van AEP omvatten — [&#x200B; CJA guardrails &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)
- Maximaal 5.000 dimensies en 5.000 metriek per gegevensweergave
- Maximaal 100 afgeleide velden per gegevensweergave
- B2B-attributie ondersteunt terugzoekvensters tot 13 maanden voor analyse op accountniveau
- Maximaal 75 gepubliceerde doelgroepen per [!DNL CJA] klant voor alle sandboxen
- Publiek publiceren minimum vernieuwt kadaster is om de 4 uur
- De streamingvertraging van AEP naar [!DNL CJA] is doorgaans minder dan 90 minuten
- Vrije-vormtabellen bieden ondersteuning voor maximaal 10 dimensies diep
- Mobiele scorecards ondersteunen maximaal 16 tegels per scorecard
- Workspace-projecten ondersteunen maximaal 40 deelvensters per project
- De backfill voor grote B2B datasets (miljarden verslagen) kan dagen vergen om te voltooien

### Veelvoorkomende valkuilen

- **Onvolledige persoon-aan-rekening afbeelding:** als de persoon-vlakke gebeurtenissen niet met een rekening kunnen worden geassocieerd, zullen zij niet in rekening-vlakke analyse verschijnen. Verzeker alle gebeurtenisdatasets een gebied omvatten dat tot identiteitskaart van de Rekening kan worden aangesloten, of direct of door een persoon-rekening gegevensreeks van de verbindingsraadpleging. Het percentage gebeurtenissen met ontbrekende accountassociatie controleren voordat een analyse wordt gemaakt.
- **Onjuiste het type van dataset aanwijzing:** B2B raadplegingsdatasets (kans, het kopen groep, persoon-rekening relaties) moet correct als raadpleging of profieltype in de [!DNL CJA] verbinding worden aangewezen. Door een zoekgegevensset als een gebeurtenisgegevensset te naast elkaar te plaatsen, worden onjuiste resultaten verkregen omdat [!DNL CJA] probeert elke record als een gebeurtenis met tijdstempel te behandelen.
- **venster van de Attributie te kort voor B2B:** Gebruikend standaard 30 dagen attributie vensters zullen vroege-stadium touchpoints in B2B reizen missen die typisch 6-18 maanden overspannen. Configureer altijd terugzoekvensters voor 13 maanden voor B2B-attributiemetriek.
- **het mengen van rekening-niveau en persoon-vlakke metriek verkeerd:** het tellen van &quot;mensen&quot;in een rekening-vlakke analyse kan misleidend zijn. Zorg ervoor dat de berekende metriek op het juiste containerniveau worden gedefinieerd. Bij een &quot;uitroepingspercentage van een account&quot; moeten gebeurtenissen op accountniveau worden gebruikt gedeeld door accounts, niet door personen.
- **Stale het kopen groepsgegevens:** Het kopen van groepssamenstelling en roltaken veranderen in tijd. Als het kopen van groepsdatasets niet regelmatig wordt verfrist, zullen de volledigheids metriek onnauwkeurig zijn. Zorg ervoor dat het bronsysteem ( [!DNL Marketo Engage] of [!DNL AJO] B2B edition) de aanschafgegevens van groepen actief synchroniseert.
- **overladend één enkel werkruimteproject:** B2B analyseert overspant overeenkomst, pijpleiding, attributie, en het kopen groepen. Wanneer u alles in één project probeert te plaatsen, gaat het laden langzamer en leidt dit tot verwarring. Gebruik meerdere gerichte projecten of deelvensters met een duidelijk label.

### Aanbevolen procedures

- Begin met Optie A (account-centraal) zelfs als u Optie B (Globale Rekening) later wilt gebruiken. Accountgerichte analyse is eenvoudiger en valideert uw gegevensmodel voordat u hiërarchische complexiteit toevoegt.
- Creeer een specifiek &quot;B2B project van de Kwaliteit van Gegevens&quot;werkruimte dat het percentage gebeurtenissen met rekeningsvereniging, het aantal zwevende rekeningen, en het kopen van groeps volledigheidmetriek volgt. Voer deze week uit om gegevensproblemen vroegtijdig af te vangen.
- Gebruik afgeleide velden om niveaus voor betrokkenheidsscoring (Hoog/Medium/Laag) te maken op basis van het aantal gebeurtenissen op accountniveau. Dit vereenvoudigt de analyse en maakt dashboards actiever voor niet-technische belanghebbenden.
- Wanneer het vormen van B2B attributie, begin met lineaire attributie als basislijn, dan vergelijk met U-vormig en tijd-verval modellen. De verschillen tussen modellen laten vaak zien of uw marketingmix gericht is op bewustmakings- of conversieactiviteiten.
- Publiceer een mobiele scorecard van het type &quot;B2B Executive Summary&quot; met niet meer dan 8 tegels die de KPI&#39;s bedekken die het belangrijkst zijn voor de leiding. Gericht blijven — directie scorecards moeten antwoorden &quot;Hoe gaan we dat doen?&quot; niet &quot;Waarom?&quot;
- Annoteer belangrijke gebeurtenissen (productlanceringen, belangrijke campagnelanceringen, prijsveranderingen, veranderingen van het verkoopproces) om context voor gegevenstendensen te verstrekken. B2B-gegevens tonen vaak spikes en dips die zonder gebeurteniscontext niet kunnen worden verklaard.
- Wanneer het publiceren van B2B publiek van [!DNL CJA], gebruik dagelijks verfrist zich voor standaardactiveringssegmenten en 4 uur verfrist zich slechts voor tijd-gevoelige segmenten. Veelvoorkomende vernieuwingen verbruiken verwerkingsbronnen.

### Handelsbesluiten

>[!NOTE]
>De volgende afwegingsbeslissingen moeten worden beoordeeld op basis van de specifieke vereisten en beperkingen van uw organisatie.

**volledigheid van Gegevens vs. analytische nauwkeurigheid**

Het opnemen van alle gebeurtenissen op persoonlijk niveau in de accountanalyse (zelfs gebeurtenissen met een zwakke accountassociatie) verbetert de volledigheid van de gegevens, maar kan de analytische nauwkeurigheid verminderen als de accounttoewijzing onbetrouwbaar is.

- **Inclusief alle gebeurtenissen begunstigen:** Uitgebreide betrokkenheidsmeting, hogere score van de rekeningsovereenkomst, bredere zichtbaarheid
- **exclusief onovertroffen gebeurtenissen begunstigen:** nauwkeurige rekening-vlakke metriek, betrouwbare attributie, betrouwbare pijpleidingscorrelatie
- **Aanbeveling:** sluit ongeëvenaarde gebeurtenissen van rekening-vlakke analyse uit maar omvat hen in een afzonderlijke persoon-vlakke gegevensmening (Optie C) om het volledige beeld te begrijpen. Prioriteit geven aan het verbeteren van de gegevenskwaliteit van accountkoppelingen als parallelle workstream.

**B2B het vensterlengte van de attributieraadpleging**

Langere terugzoekvensters (13 maanden) leggen meer aanraakpunten vast, maar kunnen marketingactiviteiten omvatten die niet langer relevant zijn voor het huidige aankoopbesluit.

- **langere terugkijkhoek (13 maanden) gunt:** Vangst de volledige B2B reis, die bewustmakingsactiviteiten, die lange verkoopcycli aanpassen erkent
- **Kortere raadpleging (6 maanden) bevordert:** concentreert zich op recente overeenkomst, verminderend lawaai van oude aanraakpunten, betere weerspiegeling van huidige het kopen intentie
- **Aanbeveling:** Gebruik 13 maandraadpleging voor ondernemingsrekeningen met lange verkoopcycli (12+ maanden). Gebruik een zoekopdracht van 6 maanden voor mid-market accounts met kortere cycli. Maak afzonderlijke berekende maatstaven voor elk venster dat u wilt vergelijken.

**Enige uitvoerige gegevensmening vs. veelvoudige geconcentreerde gegevensmeningen**

Eén gegevensweergave met alle B2B-containers en dimensies is eenvoudiger te onderhouden, maar kan de analisten overweldigen met complexiteit. De veelvoudige geconcentreerde gegevensmeningen (overeenkomst, pijpleiding, attributie) zijn gemakkelijker te gebruiken maar moeilijker te handhaven.

- **Enige mening gunt:** Consistentie, gemakkelijker onderhoud, dwars-domeinanalyse binnen één enkel project
- **Veelvoudige meningen begunstigen:** Eenvoud voor analisten, snellere ladingstijden, op maat gemaakte componentenlijsten per gebruiksgeval
- **Aanbeveling:** Begin met één enkele uitvoerige gegevensmening. Als analisten melden dat het lastig is om de juiste afmetingen en maatstaven te vinden, maakt u groepen met gekrulde componenten in dezelfde weergave voordat u deze opsplitst in meerdere weergaven. Met werkruimtjablonen kunt u analisten naar de juiste componenten leiden.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie voor het implementeren van dit gebruikspatroon.

**[!DNL CJA]B2B edition**

- [CJA B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)
- [CJA-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [CJA guardrails](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-admin/guardrails)

**Verbindingen**

- [Overzicht van verbindingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/overview)
- [Verbinding maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/create-connection)
- [Verbindingen beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-connections/manage-connections)

**de meningen van Gegevens**

- [Overzicht van gegevensweergaven](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/data-views)
- [Een gegevensweergave maken of bewerken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/create-dataview)
- [Overzicht van componentinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/overview)
- [Persistinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/persistence)
- [Attributie-instellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/attribution)
- [Indelingsinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/component-settings/format)
- [Afgeleide velden](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/derived-fields)
- [Sessieinstellingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dataviews/session-settings)

**Workspace en analyse**

- [Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [Een project maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/build-workspace-project/create-projects)
- [Vrije-vormtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/freeform-table/freeform-table)
- [Stroomvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/flow/flow)
- [Uitvalvisualisatie](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/fallout/fallout-flow)
- [Cohortingtabel](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/visualizations/cohort-table/cohort-analysis)
- [Kenmerk, deelvenster](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/panels/attribution)
- [Projecten delen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/share-projects)
- [Projecten plannen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/curate-share/send-schedule-files)
- [Afmetingen onderverdelingen](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/components/dimensions/t-breakdown-fa)

**Componenten**

- [Overzicht van filters](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/filters-overview)
- [Filters maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-filters/create-filters)
- [Overzicht van berekende metriek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/calc-metr-overview)
- [Berekende waarden maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/cja-calcmetrics/cm-workflow/cm-build-metrics)
- [Overzicht van annotaties](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/annotations/overview)
- [Datumbereiken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/date-ranges/overview)

**Soorten publiek**

- [Overzicht publiek](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/audiences-overview)
- [Soorten publiek maken en publiceren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/publish)
- [Soorten publiek beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-components/audiences/manage)

**dashboards en scorecards**

- [Een mobiele scorecard maken](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/create-scorecard)
- [scorecards configureren en beheren](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/curate)
- [Adobe Analytics-dashboards — handleiding](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-dashboards/set-up-execs)

**Geleide analyse**

- [Overzicht van geleide analyse](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/overview)
- [Funnel-weergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/funnel/funnel)
- [Trends, weergave](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/trends/usage)
- [Weergave Behouden](https://experienceleague.adobe.com/en/docs/analytics-platform/using/guided-analysis/retention/retention-rates)

**[!DNL RT-CDP]B2B edition**

- [RT-CDP B2B edition-overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#702702)
- [B2B edition-schema&#39;s](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Overzicht van B2B-bronnen](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/sources/b2b)

**de gegevensstichting van AEP**

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Overzicht van bronnen](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Marketo Engage-connector](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van sandboxen](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

**het bestuur en de levenscyclus van Gegevens**

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Geavanceerd levenscyclusbeheer van gegevens](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

**Leerprogramma&#39;s en gidsen**

- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)
- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Overzicht van observatiegegevens](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)
