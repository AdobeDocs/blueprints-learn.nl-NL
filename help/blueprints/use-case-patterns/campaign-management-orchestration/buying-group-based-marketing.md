---
title: Op groep gebaseerde marketing en reisbeheer kopen
description: Leer hoe u reizen op accountniveau kunt ontwikkelen die geschikt zijn voor leads naar inkoopgroepen om de B2B-marketingeffectiviteit te verbeteren.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7932'
ht-degree: 0%

---


# Groepsmarketing en reisbeheer kopen

Deze handleiding bevat een uitgebreide referentie voor de implementatie van de aankoop van groepsgewijze marketing en reisbeheer. Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die op accountniveau reisorchestratie moeten implementeren met het aanschaffen van groepsbeheer met behulp van [!DNL Adobe Journey Optimizer B2B Edition] en [!DNL Real-Time CDP B2B Edition] .

Gebruik dit document om te begrijpen wat te vormen, waar de implementatiekeuzen bestaan, en welke compromis drijven elk besluit.

In tegenstelling tot individuele trajecten, werkt dit patroon op het rekeningsniveau, kwalificerende individuele leidt in het kopen van groepen verbonden aan oplossingsbelangen, het scoren van betrokkenheid op het het kopen groepsniveau, en het ordenen van multi-step rekeningsreizen die door pijpleidingsstadia in verkoopbereidheid begeleiden.

## Hoofdlettergebruik

B2B-organisaties staan voor een fundamentele uitdaging: aankoopbeslissingen worden zelden door één persoon genomen. Bij complexe B2B-aankopen zijn meerdere belanghebbenden betrokken — besluitvormers, invloedrijke personen, kampioenen, budgethouders en technische beoordelaars — die samen een &quot;koopgroep&quot; vormen. Traditionele, op lood-gebaseerde marketing behandelt elke persoon onafhankelijk, die het kritieke signaal mist van of de juiste combinatie rollen binnen een rekening wordt betrokken en bereid om te kopen.

Door groepsgewijze marketing en reisbeheer te kopen, wordt dit aangepakt door de eenheid van orchestratie van individuele leads te verschuiven naar rekeningen en inkoopgroepen. Met dit patroon kunnen B2B-marketers oplossingsbelangen definiëren (de producten of services die worden verkocht), inkoopgroepsjablonen maken die aangeven welke rollen nodig zijn voor een aankoopbesluit, binnenkomende leads kwalificeren ten opzichte van die rollen, de betrokkenheid van de inkoopgroep beoordelen en accountreitten organiseren die reageren op de volledigheid en gereedheidssignalen van de inkoopgroep.

Het gewenste resultaat is een betere kwaliteit en snelheid van de pijpleiding: marketing levert rekeningen aan verkoop slechts wanneer de juiste mensen binnen de rekening worden betrokken en de koopgroep voldoende volledig is, verminderend verspilde verkoopinspanning en versnelt overeenkomstenvooruitgang.

## Belangrijkste bedrijfsdoelstellingen

Dit gebruikspatroon ondersteunt de volgende bedrijfsdoelstellingen.

### Kwalificatie en conversie van leads verbeteren

Verhoog de loodkwaliteit en verhoog de voortgang van de pijplijnen via scoring, verpleging en gepersonaliseerde follow-up.

**KPIs:** de Omzetting van de lood, Vooruitzichten/Loodomzetting, Efficiëntie

[Meer informatie over het verbeteren van kwalificatie en conversie van leads](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### De productie van lood verhogen

Genereer meer gekwalificeerde leads voor de verkooppijplijn via formulieren, gebeurtenissen, inhoud en betrokkenheid via meerdere kanalen.

**KPIs:** Vooruitzichten, Kosten per Lood, Loodomzetting

[Meer informatie over het verhogen van de productie van lood](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Verhoog de omzet en verkoop

De groei van de omzet van de bovenste regel stimuleren via geoptimaliseerde digitale kanalen, campagnes en reizen van klanten.

**KPIs:** de groei van de Inkomsten, pijpleidingssnelheid, deal dicht tarief

[Meer informatie over het verhogen van omzet en verkoop](/help/blueprints/business-objectives/revenue-monetization/increase-revenue-sales.md)

## Voorbeelden van tactische gebruiksgevallen

Hieronder vindt u specifieke scenario&#39;s waarin dit patroon kan worden toegepast.

- **Oplossing-specifieke het kopen groepskwalificatie** - bepaal het kopen groepen voor elke productlijn (bijvoorbeeld, &quot;Onderneming CRM,&quot;het Platform van Gegevens,&quot;de Reeks van de Veiligheid&quot;) met rolmalplaatjes die vereiste individuen specificeren (Economische Koper, Technische Evaluator, Champion, Eind - gebruiker) en kwalificeer lood van het systeem van CRM en marketing automatisering tegen die rollen.
- **de reis van de Rekening voor pijpleidingsversnelling** — ordent een multi-step rekeningsreis die gerichte verpleging e-mails naar ondermaatse rollen binnen een het kopen groep verzendt, brengt verkoopalarm teweeg wanneer de betrokkenheidsdrempels worden bereikt, en overgaat de rekening naar een verkoop-klaar stadium.
- **het Kopen groepvolledigheidscampagnes** — identificeer rekeningen waar het kopen groepen ontbrekende rollen (bijvoorbeeld, geen geïdentificeerde Economische Koper) hebben en lanceer gerichte aanschafcampagnes om de juiste personen binnen die rekeningen in dienst te nemen.
- **dwars-verkoop rekeningsreizen** - na een aanvankelijke overeenkomst sluit, creeer nieuwe het kopen groepen voor complementaire oplossingsbelangen en orkestaccountreizen die de uitgebreide het kopen commissie voeden.
- **re-engagement voor geïnstalleerde overeenkomsten** — ontdek rekeningen waar het kopen van de scores van de groepsovereenkomst is gedaald en teweegbrengt re-engagement reizen met verse inhoud, uitvoerende outreach, of gebeurtenisuitnodigingen.
- **verkoop en marketing groepering via de inzichten van CRM** - het kopen van oppervlakte groepstatus, betrokkenheidsgegevens, en de vooruitgang van de rekeningsreis direct binnen [!DNL Salesforce] of [!DNL Dynamics 365] zodat hebben de verkoopvertegenwoordigers in real time zicht in marketing-gekwalificeerde rekeningen.
- **gebeurtenis-gedreven het kopen groepsupdates** — werk automatisch het kopen van groepslidmaatschap en betrokkenheidsscores bij wanneer de leiders webinars bijwonen, whitepapers downloaden, pagina&#39;s van de bezoekprijs, of vraagdemo&#39;s bezoeken.
- **Multiregion rekeningscoördinatie** — beheer het kopen groepen over globale rekeningen waar de verschillende regionale contacten verschillende rollen houden, verenigend betrokkenheidsonderzoek over geografische gebieden.

## Kernprestatie-indicatoren

De volgende KPIs helpen de doeltreffendheid van dit gebruiks gevalpatroon meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Volgorde van kopersgroep | Percentage van koopgroepen met alle vereiste rollen ingevuld | [!DNL AJO B2B] Analysedashboards: traceer roldekking per inkoopgroep |
| Betrokkenheidsscore voor kopersgroep | Geaggregeerde betrokkenheidsscore voor alle leden van een inkoopgroep | [!DNL AJO B2B] Betrokkenheid scoren: persoonlijke scores opgerold tot inkoopgroep |
| MQA (Marketing Qualified Account) | Percentage rekeningen die de voor de handel gekwalificeerde drempel bereiken | Criteria voor het afsluiten van accounts: accounts die overschakelen naar verkoopklaar stadium |
| Snelheid pijplijn | Gemiddelde tijd van het kopen groepscreatie aan verkoop-gekwalificeerde kans | CRM-integratie: stage-overgangen volgen van [!DNL AJO B2B] naar CRM-pijplijn |
| Kwalificatiepercentage van &#39;Lead to Buying&#39;-groep | Percentage leads is gekwalificeerd voor het kopen van groeprollen | [!DNL AJO B2B] Beheer van kopersgroepen: gekwalificeerde versus niet-gekwalificeerde lead ratio |
| Respons op verkoopwaarschuwing | Percentage verkoopwaarschuwingen die leiden tot vervolgactiviteiten | CRM Sales Insights: tracering naar activiteit conversie |
| Voltooiingssnelheid van rekeningreis | Percentage rekeningen die het voorgenomen reispad voltooien | [!DNL AJO B2B] Analytische dashboards: maatstaven voor voltooiing van de reis |
| E-mailbetrokkenheidsgraad (B2B) | Open- en doorkliksnelheden voor e-mails met B2B-verpleging | [!DNL AJO B2B] rapporten: gegevens over levering en betrokkenheid per e-mail |

## Hoofdletterpatroon gebruiken

**het Kopen op groep-gebaseerde marketing &amp; reisbeheer**

Reizen op rekeningniveau ontwikkelen die in aanmerking komen, leidt naar inkoopgroepen om de B2B-marketingeffectiviteit te verbeteren.

**de ketting van de Functie:** de Identificatie van de Rekening > het Kopen van de Definitie van de Groep > de Kwalificatie van de Lood > de Uitvoering van de Reis van de Rekening > het Score van de Betrokkenheid > het Melden

## Applicaties

In dit gebruikspatroon worden de volgende Adobe-toepassingen gebruikt.

- **[!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])** - ordent rekening-vlakke reizen, beheert het kopen groepen met rolmalplaatjes en oplossingsbelangen, scores overeenkomst op het persoon en het kopen groepsniveau, auteurs B2B e-mailinhoud, verzendt SMS berichten, vormt verkoopalarm, en verstrekt B2B analytische dashboards.
- **[!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])** - verenigt rekeningsprofielen van uit bron B2B gegevens, verhelpt persoon-aan-rekening verhoudingen, evalueert rekening-vlakke publiek, vormt B2B-Specifieke bestemmingen ([!DNL Marketo Engage], [!DNL LinkedIn], CRM), en dwingt gegevensbeheer over B2B gegevens af.

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Vereist | Sandbox met [!DNL AJO B2B Edition] - en [!DNL RT-CDP B2B Edition] -bevoegdheden ingeschakeld. Rollen die zijn geconfigureerd voor B2B-marketers, verkoopbewerkingen en beheerders met de juiste machtigingen voor het aanschaffen van groepsbeheer, accountrajecten en CRM-integratie-instellingen. | [&#x200B; het overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [&#x200B; overzicht van de Toegangscontrole &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | B2B XDM-schema&#39;s geconfigureerd met B2B-specifieke klassen: XDM Business Account, XDM Business Opportunity, XDM Business Person (lead/contact), XDM Business Campaign en XDM Business Marketing List. Veldgroepen voor accountkenmerken, persoonkenmerken en activiteit-/betrokkenheidsgegevens moeten aanwezig zijn. De gecreeerde Datasets en profiel-Toegelaten voor elk schema. | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [&#x200B; B2B schemaklassen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Gegevensbronnen en -verzameling | Vereist | B2B-gegevensinnamepijpleidingen die worden aangelegd, doorgaans via de [!DNL Marketo Engage] bronconnector of [!DNL Salesforce]/[!DNL Dynamics] CRM-bronconnectors. De gegevens van de account, de persoon, de opportuniteit, de campagne en het campagnerelid moeten in AEP-gegevenssets worden ingevoerd. Gedragingsbetrokkenheidsgegevens (webbezoeken, e-mailinteracties, downloads van inhoud) moeten ook worden opgenomen voor betrokkenheidsscoring. | [&#x200B; Bronoverzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home), [&#x200B; schakelaar van Marketo Engage &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identiteit en profielconfiguratie | Vereist | B2B-identiteitsresolutie geconfigureerd om relaties van persoon tot account op te lossen. Identiteitsnaamruimten voor B2B-id&#39;s ([!DNL Marketo] Persoon-id, [!DNL Salesforce] Lead/Contactpersoon-id, Account-id) moeten bestaan. Beleid samenvoegen dat is geconfigureerd voor B2B-profieleenwording. Accountprofielen moeten worden verenigd op basis van gegevens uit verschillende bronnen. | [&#x200B; Overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [&#x200B; B2B Resolutie van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) |
| Auditiedefinitie en segmentatie | Vereist | Accountniveau publieksdefinities gemaakt met accountkenmerken, personekenmerken en activiteitsgegevens. Accountpubliek geeft aan welke accounts groepsreizen kopen. De evaluatie van de partij is typisch voldoende voor B2B- rekeningsreizen, hoewel de het stromen evaluatie voor rekeningskwalificatietrekkers in real time kan worden gebruikt. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [&#x200B; het publiek van de Rekening &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Berekende kenmerken kunnen betrokkenheidsgebeurtenissen op persoonlijke niveau (e-mail wordt geopend, inhoud wordt gedownload, er wordt een webinar aanwezig) samenvoegen tot maatstaven voor de betrokkenheid op accountniveau die de aankooplogica voor groepsscore en accountkwalificatie ondersteunen. | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Toegangsbeheer is van essentieel belang voor B2B-e-mail- en SMS-communicatie. Het beleid voor het verlopen van gegevenssets helpt de levenscyclus van tijdelijke betrokkenheidsgegevens te beheren en ervoor te zorgen dat aan de vereisten voor gegevensbewaring wordt voldaan. | [&#x200B; het Geavanceerde Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | B2B-gegevens bevatten vaak gevoelige bedrijfsinformatie en persoonlijke gegevens van zakelijke contacten. Het beleid inzake gegevensbeheer zorgt voor een consistent gebruik van B2B-gegevens in verschillende bestemmingen, met name bij het activeren op reclameplatforms of systemen van derden. | [&#x200B; Overzicht van het beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Bewaking en waarneming | Aanbevolen | De controle zorgt ervoor dat B2B- gegevenspijpleidingen (CRM/[!DNL Marketo] syncs) gezond zijn, de rekeningsprofielen bijwerken, en de uitvoering van de rekeningsreis zonder mislukkingen te werk gaat. Waarschuwingen over fouten met brongegevens zijn van essentieel belang voor het onderhoud van de gegevensvaluta. | [&#x200B; overzicht van de Inzichten van de Waarnemelijkheid &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | B2B-analytische dashboards binnen [!DNL AJO B2B Edition] bieden de betrokkenheid van inkoopgroepen, de prestaties van de accountreis en pijpleidingsmetriek. [!DNL CJA B2B Edition] breidt analyse met op rekeningsniveau werkruimteanalyse, het kopen groepsanalyse, en opportuniteitcorrelatie uit. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de catalogus van de toepassingsfunctie uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer B2B Edition] ([!DNL AJO B2B])

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Belichtingsconfiguratie van oplossing | Fase 1: Opstelling van de Rente &amp; van de Groep van de Oplossing | Bepaal oplossingsbelangen die producten of de diensten aan het kopen van groepkwalificatiecriteria in kaart brengen |
| Groepsbeheer voor kopers | Fase 1: Opstelling van de Rente &amp; van de Groep van de Oplossing | Creeer en beheer het kopen groepen met rolmalplaatjes, persona afbeelding, en de definities van de oplossingsrente |
| Account Journey Orchestration | Fase 3: Ontwerp en uitvoering van accountreizen | Ontwerp en beheer meertrapsgewijze accountreizen met voorwaarden, acties en op betrokkenheid gebaseerde vertakking |
| Betrokkenheid scoren | Fase 2: Kwalificatie van leads en scores voor betrokkenheid | Score persoonlijke betrokkenheid binnen inkoopgroepen om volledigheid en gereedheid van inkoopgroep te meten |
| Accountkwalificatie | Fase 2: Kwalificatie van leads en scores voor betrokkenheid | Door AI aangedreven accountkwalificatieagenten gebruiken om de gereedheid en de kwaliteit van de pijpleiding te beoordelen |
| B2B-e-mailauthoring | Fase 3: Ontwerp en uitvoering van accountreizen | B2B-e-mailinhoud maken met sjablonen, visuele fragmenten, merkthema&#39;s en het genereren van AI-inhoud |
| SMS-kanaalbeheer | Fase 3: Ontwerp en uitvoering van accountreizen | SMS-communicatie binnen B2B-rekeningreizen configureren en beheren |
| Configuratie met verkoopwaarschuwing | Fase 4: Integratie van uitlijning en CRM van verkoop | E-mails met verkoopwaarschuwingen configureren om verkoopteams op de hoogte te stellen van mijlpalen in de accountservice en om signalen te kopen |
| CRM-verkoopgegevens | Fase 4: Integratie van uitlijning en CRM van verkoop | Bieden zichtbaarheid binnen CRM ([!DNL Salesforce], [!DNL Dynamics] ) voor het aanschaffen van groepsstatus, servicegegevens en voortgang van de accountreis |
| B2B-analysedashboards | Fase 5: Rapportage en optimalisatie | De prestaties van de rekenentransparantie, het kopen groepstoezicht, en pijpleidingsmetriek door intelligente en betrokkenheidsdashboards te controleren |

### [!DNL Real-Time CDP B2B Edition] ([!DNL RT-CDP B2B])

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Account Profile Unification | Fase 0: B2B Data Foundation | U consolideert B2B-gegevens van verschillende bronnen tot verenigde accountprofielen met behulp van gespecialiseerde XDM B2B-schemaklassen en veldgroepen |
| B2B-identiteitsresolutie | Fase 0: B2B Data Foundation | Los van persoon tot rekening verhoudingen gebruikend primaire herkenningstekens op, ondersteunend multi-level rekeningshiërarchieën en veel-aan-vele persoon-aan-rekening afbeeldingen |
| Evaluatie accountpubliek | Fase 0: B2B Data Foundation | Evalueer op rekeningsniveau segmentlidmaatschap die rekeningsattributen, persoonattributen, en activiteitengegevens combineren |
| Configuratie van accountbestemming | Fase 4: Integratie van uitlijning en CRM van verkoop | Verbindingen met B2B-specifieke bestemmingen ([!DNL Marketo Engage], [!DNL LinkedIn], CRM-systemen) configureren met veldtoewijzing op accountniveau |
| Account Audience Activation | Fase 4: Integratie van uitlijning en CRM van verkoop | Publiceer op rekening-gebaseerde publiek aan bestemmingen voor op rekening-gebaseerd richten en onderdrukking |
| [!DNL Marketo Engage] Integratie | Fase 0: B2B Data Foundation | Gegevens bidirectioneel inpakken en activeren met [!DNL Marketo Engage] via native B2B-bron- en doelconnectors |
| B2B-gegevensbeheer | Fase 0: B2B Data Foundation | Beleid voor gegevensgebruik afdwingen en toestemming geven voor het centralisatie- en activeringsproces van B2B-accountgegevens |

## Vereisten

Voltooi het volgende voordat u begint met de implementatie.

- [!DNL AJO B2B Edition] licentie ingesteld en ingeschakeld in de doelsandbox
- [!DNL RT-CDP B2B Edition] licentie ingesteld en ingeschakeld in de doelsandbox
- CRM-systeem ([!DNL Salesforce] of [!DNL Microsoft Dynamics 365] ) dat met de juiste API-referenties kan worden gebruikt voor bidirectionele gegevenssynchronisatie
- [!DNL Marketo Engage] -instantie verbonden (als [!DNL Marketo] wordt gebruikt als het marketingautomatiseringsplatform) met de bronconnector geconfigureerd
- B2B XDM-schema&#39;s geïmplementeerd: Account, Person, Opportunity, Campagne en Campagne Member-klassen met vereiste veldgroepen
- Account- en persoongegevens die in AEP worden ingevoerd met persoonlijke relaties opgelost
- geconfigureerd e-mailkanaal: subdomein gedelegeerd, IP-pool geactiveerd en kanaaloppervlak gemaakt voor verzending van B2B-e-mail
- SMS-provider geconfigureerd (als SMS-kanaal wordt gebruikt voor reizen naar de account): [!DNL Sinch] , [!DNL Twilio] , of [!DNL Infobip] gegevens geleverd
- Verkoopteam dat aan de component CRM Sales Insights is gekoppeld ( [!DNL Salesforce] AppExchange-pakket of [!DNL Dynamics] -oplossing geïnstalleerd)
- Inhoud voorbereid: B2B-e-mailsjablonen, merkthema&#39;s en visuele fragmenten voor e-mails met waarschuwings- en verkoopinformatie
- De vastgestelde taxonomie van het belang van de oplossing: lijst van producten/de diensten die bijbehorende het kopen groepen zullen hebben
- Rolrolsjablonen voor inkoopgroepen ontworpen: persona&#39;s en rollen vereist voor elke oplossingsrente (bijvoorbeeld Economische koper, Technische evaluator, Champion)

## Implementatieopties

In dit deel worden de beschikbare implementatiebenaderingen beschreven, die elk op verschillende organisatorische behoeften en ontwikkelingsniveaus zijn toegesneden.

### Optie A: Interessant voor één oplossing met lineaire accountreis

**Best voor:** Organisaties nieuw aan het kopen groepsbeheer die met één enkele productlijn of oplossing willen beginnen die, de benadering bevestigen, en herhalen alvorens aan veelvoudige oplossingsbelangen te schrapen.

**hoe het werkt:**

Deze benadering richt zich op één enkele oplossingsrente (één product of dienst) met één het kopen groepsmalplaatje. Een lineaire accountreis wordt ontworpen met opeenvolgende fasen: accountidentificatie, het aanschaffen van groepsformatie, de betrokkenheid van de verpleegkundigen, de drempel voor het bijhouden van afspraken en de verkoopoverdracht. De reis volgt een eenvoudig pad zonder complexe vertakkingen of parallelle sporen.

Leads zijn gekwalificeerd voor het kopen van groepsrollen wanneer ze worden ingepakt bij de CRM of [!DNL Marketo Engage] . De accountreis verzendt verplegend e-mails naar rollen onder contract, controleert betrokkenheidsscores en brengt een verkoopalarm teweeg wanneer de het kopen groep een bepaalde volledigheids en betrokkenheidsdrempel bereikt. Deze aanpak levert een duidelijk, meetbaar bewijs van concept voordat complexiteit wordt geïntroduceerd.

**Zeer belangrijke overwegingen:**

- Eenvoudiger te implementeren en te valideren, zodat deze geschikt is voor een eerste implementatie
- Beperkt tot één aankoop van producten/services per keer
- De lineaire reisstructuur is mogelijk niet geschikt voor complexe meerfasenaankoopcycli

**Voordelen:**

- Snellste tijd om te waarderen met minimale configuratiecomplexiteit
- Duidelijke succesmetriek verbonden aan één enkele oplossingsrente
- Eenvoudiger uit te leggen en organisatieaankopen te doen
- Rechtstreekse rapportage en KPI-meting

**Beperkingen:**

- Wordt niet gebruikt voor scenario&#39;s met meerdere of meerdere producten
- Voor rekeningen die in meerdere oplossingen geïnteresseerd zijn, zijn aparte, ongecoördineerde reizen nodig
- Mogelijk worden de beheermogelijkheden van de inkoopgroep niet volledig benut

**Experience League:**

- [AJO B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Koopgroepen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)

### Optie B: Meerdere oplossingen voor vertakkingen van rekeningreizen

**Best voor:** Organisaties met veelvoudige productlijnen of de dienstdienstenaanbod die afzonderlijke het kopen groepen per oplossingsrente moeten beheren, met rekeningsreizen die zich baseren op welke oplossingsbelangen actief zijn en hoe ver langs elke het kopen groep in het kwalificatieproces is.

**hoe het werkt:**

De veelvoudige oplossingsbelangen worden bepaald, elk met zijn eigen het kopen rolmalplaatje van de groep. Een rekeningreis begint met rekeningidentificatie en evalueert welke oplossingsbelangen op elke rekening van toepassing zijn die op gedragssignalen, firmografische gegevens, of expliciete bedoeling wordt gebaseerd. De reistakken om elke actieve oplossingsrente te richten, die parallelle koepelsporen voor verschillende het kopen groepen binnen de zelfde rekening in werking stellen.

Het scoren van betrokkenheid werkt onafhankelijk per het kopen groep, die één het kopen groep toestaat om verkoopbereidheid te bereiken terwijl een andere nog wordt gekoesterd. Het alarm van de verkoop wordt gevormd per oplossingsbelang, zodat wordt het aangewezen verkoopteam of de specialist op de hoogte gebracht wanneer een specifieke het kopen groep kwalificeert. CRM-inzichten bieden alle actieve inkoopgroepen voor een account, waardoor de verkoop een holistische weergave krijgt.

**Zeer belangrijke overwegingen:**

- Vereist een duidelijk omschreven taxonomie van de oplossingsrente en afzonderlijke het kopen groepsmalplaatjes
- De complexiteit van reizen neemt toe met elke extra interesse voor oplossingen
- Coördinatie tussen verschillende inkoopgroepen (bijvoorbeeld gedeelde contacten die een rol spelen in meerdere inkoopgroepen) moet worden gepland

**Voordelen:**

- Steunt dwars-verkoop en multi-product rekeningsstrategieën
- Onafhankelijke scores per inkoopgroep biedt zichtbaarheid via granulaire pijplijnen
- Verkoopteams ontvangen gerichte waarschuwingen per oplossingsbelang
- Maximaliseert de mogelijkheden voor [!DNL AJO B2B Edition] groepsbeheer kopen

**Beperkingen:**

- Hogere complexiteit van de implementatie en langere implementatietijd
- Meer inhoudselementen vereist (afzonderlijke e-mailtracks per oplossingsbelang)
- De rapportage is complexer met meerdere inkoopgroepen per account
- Risico van over-overseinencontacten die in veelvoudige het kopen groepen zijn (vereist frequentiebeheer)

**Experience League:**

- [Oplossingsbelangen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Accountreizen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)

### Optie C: kwalificatie van een AI-account met automatische reisprogressie

**het Best voor:** de organisaties van de Mature B2B met significante historische gegevens die de agenten van de de rekeningskwalificatie van AI willen hefboomwerking de beoordeling van rekeningsbereidheid automatiseren, handkwalificatieinspanning verminderen, en dynamisch reiswegen aanpassen die op AI-geproduceerde lezingsscores worden gebaseerd.

**hoe het werkt:**

Deze benadering bouwt voort op de multi-oplossing-rente stichting van Optie B maar voegt aan AI-Verantwoording van de rekening toe om de overgang tussen reisstadia te automatiseren. In plaats van alleen te vertrouwen op op regels gebaseerde betrokkenheidsscore-drempels, evalueert de AI-kwalificatieagent de gereedheid van de account met behulp van een bredere reeks signalen — de volledige groepsintegriteit, de snelheid van de service, de nauwkeurigheid van de zelfstudie, de historische conversiepatronen en de intentgegevens aanschaffen.

Accountreizen gebruiken de AI-kwalificatieresultaten om de volgende stappen te bepalen: accounts die hoog op gereedheid scoren, worden snel bijgehouden in verkoopwaarschuwingen, accounts in het middelste niveau krijgen een verhoogde verpleegkundigheid en rekeningen met lage gereedheid worden geplaatst in bewustmakingstracks op lange termijn. De AI-agent herevalueert voortdurend naarmate er nieuwe betrokkenheidsgegevens aankomen, waardoor dynamische voortgang van de reis mogelijk is zonder handmatige tussenkomst.

**Zeer belangrijke overwegingen:**

- Vereist voldoende historische gegevens om effectieve kwalificatiemodellen op te leiden
- AI-outputs moeten worden gevalideerd tegen feitelijke pijpleidingresultaten voordat ze volledig worden geïmplementeerd
- Combineert goed met [!DNL CJA B2B Edition] voor het analyseren van kwalificatienauwkeurigheid en pijpleidingscorrelatie

**Voordelen:**

- Vermindert handmatige kwalificatieinspanning en elimineert willekeurige op drempel-gebaseerde handoff
- Hiermee past u zich dynamisch aan veranderende accountgedrag en betrokkenheidspatronen aan
- Hogere pijpleidingskwaliteit door veelvoudige signalen voorbij eenvoudige betrokkenheidsscores op te nemen
- Door voortdurend opnieuw te evalueren wordt voorkomen dat rekeningen vastzitten in onjuiste reisfasen

**Beperkingen:**

- Vereist historische conversiegegevens voor betekenisvolle AI-training
- De kwalificatiebesluiten van de &quot;zwarte doos&quot;kunnen voor verkoopteams moeilijker begrijpen en vertrouwen aanvankelijk
- Complexer om problemen op te lossen wanneer de rekeningen onverwacht of helemaal niet worden gekwalificeerd
- Afhankelijk van de gegevenskwaliteit en volledigheid van alle invoersignalen

**Experience League:**

- [Accountkwalificatie](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [AI-assistent in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)

### Optievergelijking

| Criteria | Optie A: interesse voor één oplossing | Optie B: meerdere belangen van oplossingen | Optie C: AI-kwalificatie |
| --- | --- | --- | --- |
| Best voor | Eerste implementatie, één productlijn | Meerproductorganisaties | Natuurlijke organen met historische gegevens |
| Complexiteit | Laag | Medium-High | Hoog |
| Tijd tot waarde | 2-4 weken | 4-8 weken | 6-12 weken |
| Oplossingsbelangen | 1 | Meerdere | Meerdere |
| Reisstructuur | Lineair | Vertakking, parallelle tracks | Dynamische, door AI aangedreven progressie |
| Scoreaanpak | Regelgebaseerde drempels | Op regels gebaseerd per inkoopgroep | Door AI aangedreven kwalificatie + regels |
| Inhoud-eisen | Minimaal (één baan voor de kwekerij) | Hoog (per oplossingsbelang) | Hoge + dynamische selectie van inhoud |
| Verkoopuitlijning | Workflow voor één melding | Waarschuwing per oplossing | Geprioriseerde waarschuwingen met een AI-score |
| Vereisten | Basis B2B-gegevensstichting | Goed gedefinieerde oplossingstaxonomie | Historische conversiegegevens + taxonomie |

### Kies de juiste optie

Begin met deze vragen om de beste implementatieaanpak te bepalen:

1. **hoeveel afzonderlijke producten of de diensten hebben onafhankelijke het kopen commissies?** Als het antwoord één is (of de organisatie wil eerst het concept bewijzen), begin met Optie A. Indien meerdere, ga naar vraag 2.

2. **is er voldoende historische gegevens over gewonnen/verloren overeenkomsten, het kopen van compositie, en betrokkenheidspatronen?** Als ja en de organisatie handkwalificatie willen minimaliseren, verstrekt Optie C de meest geautomatiseerde benadering. Als niet, biedt Optie B multi-oplossing-interessessteun van regel-gebaseerd het scoren.

3. **wat is de capaciteit van het de veranderingsbeheer van de organisatie?** Opties B en C vereisen een meer organisatorische afstemming (productie van inhoud, verkoopmogelijkheden, interfunctionele coördinatie). Als de capaciteit beperkt is, begin met Optie A en breid uit.

Een gemeenschappelijk progressiepad is: begin met Optie A om het concept met één oplossingsrente te bewijzen, breid aan Optie B uit door oplossingsbelangen toe te voegen aangezien het vertrouwen groeit, dan laag in de AI van Optie C kwalificatie zodra genoeg historische gegevens beschikbaar zijn om de modellen effectief te trainen.

## Uitvoeringsfasen

In de volgende fasen wordt het stapsgewijze implementatieproces voor dit gebruikspatroon beschreven.

### Fase 0: B2B-gegevensstichting

**de functies van de Toepassing:** [!DNL RT-CDP B2B]: De Unificatie van het Profiel van de rekening, B2B de Resolutie van de Identiteit, [!DNL Marketo Engage] Integratie, B2B het Beheer van Gegevens, de Evaluatie van het Publiek van de Rekening

In deze fase wordt de B2B-gegevensinfrastructuur in [!DNL RT-CDP B2B Edition] ingesteld. U verenigt accountgegevens van CRM, marketingautomatisering en andere bronnen in één accountprofiel, lost relaties van persoon tot account op, configureert B2B-gegevensbeheer en maakt publiek op accountniveau dat wordt gebruikt in [!DNL AJO B2B Edition] groepsbeheer voor aankopen.

#### Besluit: B2B-gegevensbronstrategie

Welke systemen dienen als primaire bronnen voor rekening, persoon, en betrokkenheidsgegevens?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| [!DNL Marketo Engage] als primaire bron | [!DNL Marketo] is het marketingautomatiseringsplatform van de organisatie met een rijke servicegeschiedenis | Geïntegreerde bidirectionele connector vereenvoudigt de installatie; gegevensstromen van betrokkenheid automatisch; relaties van persoon tot account die worden overgeërfd van [!DNL Marketo] |
| CRM ([!DNL Salesforce]/[!DNL Dynamics]) als primaire bron | CRM is het recordsysteem voor accounts en contactpersonen; [!DNL Marketo] wordt niet gebruikt | Vereist de configuratie van de CRM-bronconnector; voor betrokkenheidsgegevens zijn mogelijk aanvullende bronnen nodig; persoonlijke relaties van CRM-accountverenigingen |
| Hybride: CRM voor accounts + [!DNL Marketo] voor betrokkenheid | CRM is eigenaar van de hoofdgegevens van account/contactpersoon terwijl [!DNL Marketo] gedragsbetrokkenheid vastlegt | Meest voorkomende patroon voor organisaties die beide gebruiken; vereist zorgvuldige identiteitsresolutie om [!DNL Marketo] personen te koppelen aan CRM-contactpersonen |

#### Besluit: strategie voor het accountpubliek

Hoe moet rekening worden gehouden met het publiek bij het betreden van de reis?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Voorkeursaccount op basis van firmware | Doelaccounts op basis van grootte, inkomstenniveau of geografie van de bedrijfstak, het bedrijf | Goed voor ABM-doellijsten; vereist geen betrokkenheidsgegevens; kan breed zijn |
| Accountpubliek op basis van betrokkenheid | Doelaccounts waarin mensen gedragsintentiesignalen hebben getoond | Vereist het stromen van betrokkenheidsgegevens; nauwkeuriger het richten; kan rekeningen met latente rente missen |
| Gecombineerde firmografisch + betrokkenheid | Doelaccounts die overeenkomen met het ideale klantprofiel EN de betrokkenheid tonen | Het nauwkeurigst; vereist beide gegevenstypes; geadviseerd voor gekwalificeerde pijpleidingsgeneratie |

**navigatie UI:** Platform > Bronnen > Catalogus > Uitgezochte bron ([!DNL Marketo Engage], [!DNL Salesforce], enz.) > Gegevensstroom instellen

**Zeer belangrijke configuratiedetails:**

- Vorm B2B XDM schema&#39;s voor elke B2B entiteit (Rekening, Persoon, Kans, Campagne, Lid van de Campagne) met vereiste gebiedsgroepen
- Bronconnectors instellen voor CRM en/of [!DNL Marketo Engage] met de juiste planning (doorgaans intervallen van 1-4 uur voor B2B-gegevens)
- Identiteitsnaamruimten configureren voor B2B-id&#39;s ([!DNL Marketo] Persoon-id, SFDC-lead-id, SFDC-contact-id, account-id)
- B2B-identiteitsresolutie inschakelen om personen aan accounts te koppelen
- Een publiek op accountniveau maken met behulp van de accountpubliek-functie in [!DNL RT-CDP]

**documentatie van Experience League:**

- [RT-CDP B2B edition-overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [B2B-schema&#39;s in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage-bronaansluiting](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Accountpubliek](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [B2B-identiteitsresolutie](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)

### Fase 1: Groepsinstellingen voor interesse en koop van oplossingen

**de functies van de Toepassing:** [!DNL AJO B2B]: De Configuratie van de Rente van de oplossing, het Kopen van het Beheer van de Groep

Deze fase bepaalt de oplossingsbelangen (producten/de diensten) en het kopen groepsmalplaatjes die de kern van het het kopen beheersmodel van de groep vormen. U zult oplossingsbelangen tot stand brengen, rolmalplaatjes met persoonlijke vereisten bepalen, en vormen hoe de lood in het kopen van groepsrollen worden gekwalificeerd.

#### Beslissing: granulariteit van het belang van de oplossing

Op welk niveau moeten de belangen van de oplossing worden bepaald?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Oplossingsbelangen op productniveau | Elk afzonderlijk product heeft zijn eigen inkoopgroep | Meest korrelig; maakt productspecifieke inkoopgroepssjablonen mogelijk; kan resulteren in veel inkoopgroepen per account |
| Belangen op oplossingsniveau | Groepeer verwante producten in oplossingscategorieën (bijvoorbeeld &quot;Marketing Cloud&quot; in plaats van afzonderlijke producten) | Eenvoudiger te beheren; minder inkoopgroepen; rollen kunnen generischer zijn; geadviseerd voor aanvankelijke plaatsingen |
| Belangen op gebruiksniveau | Belangen bepalen rond bedrijfsresultaten eerder dan producten (bijvoorbeeld &quot;Digitale Transformatie&quot;) | Richt zich op het adviserende verkopen; het kopen van groepsrollen kan veelvoudige producten overspannen; moeilijker om aan de pijpleidingsstadia van CRM in kaart te brengen |

#### Beslissing: ontwerp van rolsjabloon voor groep kopen

Hoe moeten rollen worden gedefinieerd binnen elke inkoopgroep?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Standaardrolsjabloon | Gebruik een gemeenschappelijke reeks rollen over alle oplossingsbelangen (bijvoorbeeld Economische Koper, Technische Evaluator, Champion, Eindgebruiker) | Consistente scoring en kwalificatie; eenvoudiger te beheren; houdt mogelijk geen oplossingsspecifieke rollen vast |
| Oplossingsspecifieke rolmalplaatjes | Bepaal unieke rollen per oplossingsrente die op de daadwerkelijke het kopen commissie voor dat product wordt gebaseerd | Betere kwalificatie; vereist meer kennis van elk aankoopproces; hoger onderhoud |
| Sjablonen voor gelaagde rollen | Vereiste rollen definiëren (must-have voor kwalificatie) en optionele rollen (de volledigheid vergroten maar niet vereist) | Precisie van balansen met flexibiliteit; verhindert te strenge kwalificatiecriteria pijpleiding te blokkeren |

**navigatie UI:** [!DNL AJO B2B Edition] > het Kopen Groepen > de Belangen van de Oplossing > creëren de Rente van de Oplossing

**navigatie UI:** [!DNL AJO B2B Edition] > het Kopen Groepen > de Malplaatjes van de Rol > creëren het Malplaatje van de Rol

**Zeer belangrijke configuratiedetails:**

- Bepaal elke oplossingsrente met een naam, een beschrijving, en het bedrijfsresultaat het richt
- Creeer rolmalplaatjes die de karakters specificeren die voor elke het kopen groep worden vereist (bijvoorbeeld &quot;Beslissingsmaker,&quot;Influencer,&quot;Praktijk,&quot;Uitvoerende Sponsor&quot;)
- Configureer kwalificatiecriteria voor lead-to-role: hoe het systeem bepaalt aan welke persoon een lead wordt toegewezen (op basis van functie, afdeling, anciënniteit of aangepaste kenmerken)
- Drempelwaarden voor volledigheid instellen: bepalen welk percentage van de rollen moet worden ingevuld als een inkoopgroep als &quot;volledig&quot; moet worden beschouwd
- Belangen van oplossingen koppelen aan accountpubliek of accountkenmerken die potentiële interesse aangeven

**waar de opties uiteenlopen:**

**voor Optie A (Enige Belang van de Oplossing):**
Creeer één oplossingsbelang en één rolmalplaatje. Nadruk op een duidelijke, goed begrepen koopmotie voor het primaire product of de dienst van de organisatie.

**voor Optie B (de Veelvoudige Belangen van de Oplossing):**
Creeer veelvoudige oplossingsbelangen, elk met zijn eigen rolmalplaatje. Wijs elke oplossingsbelang aan het aangewezen product van CRM/opportuniteitstype voor stroomafwaartse pijpentracering toe.

**voor Optie C (AI-Gesteunde Kwalificatie):**
Vorm oplossingsbelangen en rolmalplaatjes zoals in Optie B, maar vorm daarnaast de AI kwalificatieagent met historische gegevens over het succesvol kopen van groepssamenstellingen en overeenkomstenuitkomsten om het kwalificatiemodel te trainen.

**documentatie van Experience League:**

- [Overzicht van kopersgroepen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Oplossingsbelangen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Rolsjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Koopgroepen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)

### Fase 2: kwalificatie van leads en servicescorting

**de functies van de Toepassing:** [!DNL AJO B2B]: Het Scoren van de betrokkenheid, de Kwalificatie van de Rekening

In deze fase wordt het model voor betrokkenheidsscore opgezet dat de betrokkenheid op persoonlijke niveau bij het kopen van groepen meet en het opwaardeert tot het aanschaffen van groepen en gereedheidsscores op accountniveau. U configureert scoreregels, definieert betrokkenheidsdrempels voor kwalificatie en schakelt desgewenst kwalificatie van een door AI aangedreven account in.

#### Besluit: Engagement scoring model

Hoe moet de betrokkenheid op het niveau van de persoon en de koopgroep worden beoordeeld?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Op activiteiten gebaseerde scoring | Wijs puntwaarden toe aan specifieke acties (e-mail open = 5 punten, inhouddownload = 15 punten, demoverzoek = 50 punten) | Transparant en eenvoudig af te stemmen; vereist voortdurend onderhoud naarmate inhoud en kanalen veranderen; is het meest bekend bij [!DNL Marketo] -gebruikers |
| Recentieggewogen scoring | Gewicht recente activiteiten hoger dan oudere (decaying score model) | Kies Beter voor de huidige intentie; voorkomt dat scores met hoge scores op schaal kwalificatie opblazen; complexer om te configureren |
| AI-scoring | Met de AI-kwalificatieagent van [!DNL AJO B2B] kunt u gereedheidsscores genereren op basis van patroonherkenning | Meest geavanceerd; past zich automatisch aan; vereist historische gegevens; kan aan verkoopteams aanvankelijk ondoorzichtig zijn |

#### Besluit: Kwalificatiedrempel

Wanneer moet een koopgroep als klaar voor verkoop worden beschouwd?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen score | Kopergroep komt in aanmerking als de totale betrokkenheidsscore een gedefinieerde waarde overschrijdt | Eenvoudig uit te voeren; de scoredrempel kan in tijd moeten worden gestemd; overweegt niet rolsamenstelling |
| Voltooiing + score drempel | Kopergroep komt in aanmerking als aan de minimale dekkingsgraad EN score is voldaan | Meer robuuste kwalificatie; voorkomt dat u groepen met hoge scores koopt, maar een sleutelrol mist |
| Door AI bepaalde gereedheid | AI de kwalificatieagent bepaalt bereidheid gebruikend veelvoudige signalen voorbij score en volledigheid | Meest geavanceerd; verwerkt voor het kopen van snelheid, concurrerende signalen, en historische patronen; Optie C slechts |

**navigatie UI:** [!DNL AJO B2B Edition] > het Kopen Groepen > het Score van de Betrokkenheid > vormen het Schwaarderen Regels

**Zeer belangrijke configuratiedetails:**

- Regels voor het noteren van betrokkenheid definiëren: puntwaarden toewijzen aan gedragsgebeurtenissen (e-mail wordt geopend, er wordt geklikt, er worden webpagina&#39;s bezocht, inhoud wordt gedownload, er worden formulieren verzonden, er wordt een webinar bijgewoond, er worden demo-verzoeken verzonden)
- Score-verlies of recentieweging configureren bij gebruik van tijdgevoelige scoring
- Score op groepsniveau voor kopen instellen: hoe persoonlijke scores worden gecombineerd in een score voor een inkoopgroep (som, gewogen gemiddelde of minimum-drempel-per-rol)
- Kwalificatiedrempels definiëren: de score- en volledigheidsniveaus die de overgang naar de volgende aankoopfase activeren
- Vorm de AI kwalificatieagent (Optie C): trein met historische overeenkomstengegevens, bepaal de signalen de agent zou moeten overwegen, en vastgestelde betrouwbaarheidsdrempels

**documentatie van Experience League:**

- [Engagement scoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Groepsfasen voor kopen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Accountkwalificatie](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)

### Fase 3: Ontwerp en uitvoering van de reis van de rekening

**de functies van de Toepassing:** [!DNL AJO B2B]: De rekening Journey Orchestration, B2B E-mail Authoring, het Beheer van het Kanaal van SMS

Deze fase ontwerpt en implementeert de accountrit die de betrokkenheid bij het kopen van groepsleden organiseert. U maakt accountreizen met toegangsvoorwaarden, actieknooppunten (e-mail, SMS), voorwaardelijke vertakkingen (op basis van groepsstadium kopen, betrokkenheidsscore, roldekking), wachtstappen en afsluitcriteria.

#### Besluit: trigger voor het betreden van een reis

Welke gebeurtenis of toestand zorgt ervoor dat een account de reis betreedt?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Kwalificatie voor accountpubliek | Account wordt ingeschakeld wanneer een doelaccountpubliek wordt geopend | Batchgeoriënteerd; goed voor op ABM-lijsten gebaseerde invoer; publiek moet vooraf gedefinieerd zijn |
| Aanmaakgebeurtenis voor groep kopen | Account wordt ingevoerd wanneer voor het eerst een inkoopgroep voor de account wordt gemaakt | Gebeurtenis aangestuurd; geactiveerd door kwalificatie &#39;lead&#39; in een rol van de inkoopgroep; real-time meer |
| Wijziging van accountkenmerk | Account wordt ingeschakeld wanneer een specifiek kenmerk wordt gewijzigd (bijvoorbeeld een score bij de intentie, een accountlaag) | Vereist dat het activeringskenmerk in real-time of bijna-real-time wordt bijgewerkt |

#### Besluit: Kanaalmix voor B2B-kweek

Welke kanalen moeten de rekeningreis gebruiken om het kopen groepsleden aan te gaan?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen e-mail | De meeste B2B-interacties vinden plaats via e-mail; er is geen SMS-plug-in-infrastructuur | Eenvoudigst te vormen; gemeenschappelijkste B2B patroon; kan mobiel-eerste contacten missen |
| E-mail + SMS | Organisatie heeft SMS-opt-in van zakelijke contacten; dringende meldingen zijn gerechtvaardigd | SMS is effectief voor tijdgevoelige waarschuwingen (herinneringen aan gebeurtenissen, bevestigingen van vergaderingen); vereist configuratie van SMS-provider |
| E-mail + SMS + verkoopberichten | Volledig spectrum: marketing verpleegkunde via e-mail/SMS plus meldingen voor verkoopteams | Uitgebreid; vereist dat het verkoopteam een waarschuwingsworkflow aanneemt; coördineert marketing- en verkoopaanraakpunten |

#### Besluit: Reisvertakkingsstrategie

Hoe zou de reistak op rekening en het kopen groepsstatus moeten worden gebaseerd?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Op werkgebied gebaseerde vertakking | Branch die is gebaseerd op de fase van de inkoopgroep (bijvoorbeeld Bewustmaking, Overwegingen, Besluit) | Hiermee wordt uitgelijnd op traditionele funnel-fasen; inhoud toegewezen aan fasen; pad naar voortgang wordt gewist |
| Op rollen gebaseerde vertakking | Branch om verschillende inhoud naar verschillende rollen van inkoopgroepen te verzenden (technische inhoud naar beoordelaars, ROI-inhoud naar economische kopers) | Meer gepersonaliseerd; vereist rol-specifieke inhoudsactiva; hogere inspanning van de inhoudsproductie |
| Op betrokkenheid gebaseerde vertakking | Branch op basis van drempelwaarden voor betrokkenheidsscore (lage betrokkenheid = opnieuw inschakelen, hoog = versnellen) | Dynamisch en responsief; past zich aan het werkelijke gedrag aan; kan complexe vertakkende bomen creëren |

**navigatie UI:** [!DNL AJO B2B Edition] > de Reizen van de Rekening > Create Reis

**Zeer belangrijke configuratiedetails:**

- Maak het canvas van de accountritgang met de geselecteerde ingangsvoorwaarde
- Trajectknooppunten van account toevoegen: handelingen voor e-mail, SMS-handelingen, wachtstappen, splitsingen van voorwaarden en vertakking van paden
- E-mailinhoud van auteur B2B met de B2B-e-mail-Designer met merkthema&#39;s, visuele fragmenten en het genereren van AI-inhoud
- Vorm personalisatietokens verwijzend rekeningsattributen, persoonattributen, en het kopen groepsgegevens
- De wachttijd tussen aanraakpunten instellen (B2B-reizen gebruiken meestal langere wachttijden: 3-7 dagen tussen e-mails)
- Afsluitingscriteria definiëren: voorwaarden waaronder rekeningen de reis verlaten (kopende groep bereikt kwalificatiedrempel, in CRM gecreëerde mogelijkheid, account kiest uit)
- Vorm de acties van SMS als het gebruiken van het kanaal van SMS (vereist de leveranciersconfiguratie van SMS en contactoptie.
- De reis met testrekeningen testen alvorens te publiceren

**waar de opties uiteenlopen:**

**voor Optie A (Enige Belang van de Oplossing):**
Ontwerp een lineaire reis met opeenvolgende stadia. De vermelding is gebaseerd op één publiek van een account of op een gebeurtenis waarbij een groep wordt gemaakt. Één spoor van de e-mailcultuur met stijgende urgentie en diepte van inhoud.

**voor Optie B (de Veelvoudige Belangen van de Oplossing):**
Ontwerp een reis met parallelle takken per oplossingsbelang. Gebruik voorwaardenknooppunten om accounts te routeren naar het juiste verzorgingsvak op basis waarvan inkoopgroepen bestaan. Elke vertakking heeft zijn eigen inhoud en scoredrempels.

**voor Optie C (AI-Gesteunde Kwalificatie):**
Ontwerp een reis waar de voorwaardenknopen de AI kwalificatiescore eerder dan (of naast) op regel-gebaseerde drempels evalueren. Inclusief dynamische padselectie waarbij de AI bepaalt of een account moet worden versneld, onderhouden of de prioriteit ervan moet worden opgeheven.

**documentatie van Experience League:**

- [Overzicht van rekeningreizen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Transparante knooppunten van account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [B2B-e-mailauthoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [SMS-kanaal in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [AI Assistant voor het schrijven van e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### Fase 4: Integratie van uitlijning en CRM

**de functies van de Toepassing:** [!DNL AJO B2B]: De Configuratie van de Waarschuwing van de Verkoop, de Gegevens van de Verkoop CRM; [!DNL RT-CDP B2B]: de Configuratie van de Bestemming van de Rekening, Rekening Audience Activation

Deze fase vestigt de brug tussen marketing en verkoop door verkoop waakzame e-mails te vormen, de Inzichten van de Verkoop van CRM voor in-CRM zicht op te stellen, en naar keuze rekeningspubliek aan B2B bestemmingen ([!DNL LinkedIn], [!DNL Marketo], systemen van CRM) te activeren.

#### Besluit: triggerstrategie voor verkoopwaarschuwingen

Wanneer moet de verkoop op de hoogte worden gesteld van de status van een groep die een account koopt?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Mijlpaal-waarschuwingen | Verkoop waarschuwen wanneer de koopgroep specifieke mijlpalen bereikt (gekwalificeerd, volledig, hoog engagement) | Duidelijke, discrete meldingen; voorkomt vermoeidheid bij waarschuwingen; kan de geleidelijke ontwikkeling van betrokkenheid missen |
| Waarschuwingen op basis van drempelwaarden | Verkoop waarschuwen wanneer de betrokkenheidsscore een gedefinieerde drempel overschrijdt | Doorlopende bewaking; kan meerdere waarschuwingen veroorzaken wanneer de scores bij de drempelwaarde schommelen |
| Waarschuwingen over werkgebiedovergang | Verkoop op de hoogte stellen bij het kopen van groepsovergangen naar een nieuwe fase (bijvoorbeeld van Overwegingen naar Besluit) | Lijnt uit op de fasen van de pijpleiding; het duidelijkste signaal voor verkoopactie; vereist duidelijk gedefinieerde werkgebieddefinities |

#### Besluit: CRM-integratiediepte

Hoe diep moet het kopen van groepsgegevens in CRM worden opgedoken?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| Alleen verkoopwaarschuwingen (geen interne CRM-component) | Organisatie gebruikt [!DNL Salesforce] of [!DNL Dynamics] niet, of integratie van CRM is niet mogelijk | Laagste integratieinspanning; de verkoop ontvangt e-mailberichten maar geen dashboard van CRM; beperkte zichtbaarheid |
| CRM Sales Insights-dashboard | Organisatie gebruikt [!DNL Salesforce] of [!DNL Dynamics] en wil dat de status van de inkoopgroep zichtbaar is binnen de CRM | Vereist installatie van het CRM Sales Insights-pakket; biedt uitgebreide informatie op accountniveau; aanbevolen voor de meeste implementaties |
| Volledige bidirectionele CRM-synchronisatie | Het kopen groepsstadia en de scores schrijven terug naar de voorwerpen van CRM, beïnvloeden het werkschema en het melden van CRM | Hoogste integratieingewikkeldheid; laat CRM-inheemse pijpleidingsrapportering toe; vereist de configuratie van douaneCRM |

**navigatie UI:** [!DNL AJO B2B Edition] > Beleid > de Waarschuwingsconfiguratie van de Verkoop

**navigatie UI:** [!DNL AJO B2B Edition] > Beleid > de Inzichten van de Verkoop van CRM > vormen

**Zeer belangrijke configuratiedetails:**

- E-mailsjablonen voor verkoopwaarschuwingen configureren: de status van de inkoopgroep, betrokken personen, betrokkenheidsscore en aanbevolen volgende acties
- Bepaal waakzame verpletterende regels: welke verkopers of teams alarm ontvangen dat op rekeningseigendom, gebied, of oplossingsbelang wordt gebaseerd
- CRM Sales Insights installeren en configureren voor [!DNL Salesforce] of [!DNL Dynamics 365]
- Wijs de het kopen groepsgegevens aan de voorwerpen van CRM toe zodat de verkoop het kopen groepssamenstelling, overeenkomst, en reisvooruitgang binnen hun workflow van CRM kan bekijken
- Configureer desgewenst bestemmingsverbindingen voor account om accountpubliek te activeren naar [!DNL LinkedIn] (voor ABM-reclame), [!DNL Marketo Engage] (voor follow-up op hoofdniveau) of andere B2B-doelen

**documentatie van Experience League:**

- [E-mails met verkoopberichten](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM-verkoopgegevens](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)
- [Overzicht van doelen](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Doel van LinkedIn-overeenkomend publiek](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Fase 5: Rapportage en optimalisatie

**de functies van de Toepassing:** [!DNL AJO B2B]: B2B de Dashboards van de Analyse

In deze fase wordt het rapportage- en analytische kader vastgesteld voor het meten van de prestaties van de inkoopgroep, de doeltreffendheid van de accountrisport en de invloed van de pijpleiding. [!DNL AJO B2B Edition] bevat ingebouwde analytische dashboards; [!DNL CJA B2B Edition] (indien gelicentieerd) breidt de analyse uit met diepgaande inzichten op accountniveau over meerdere kanalen.

#### Besluit: Rapportageaanpak

Welke analytische hulpmiddelen voor aan de gang zijnde prestaties controle zouden moeten worden gevormd?

| Optie | Wanneer kiest u | Overwegingen |
| --- | --- | --- |
| [!DNL AJO B2B] alleen dashboards | De ingebouwde dashboards van [!DNL AJO B2B Edition] zijn voldoende voor het kopen van groep- en reismetriek | Het snelst te vormen; behandelt kernB2B metriek; beperkte capaciteit van de douaneanalyse |
| [!DNL AJO B2B] dashboards + [!DNL CJA B2B Edition] | De organisatie heeft een diepere dwars-kanaalanalyse, de analyse van de koopgroep, opportuniteitcorrelatie, en douaneattributie nodig | Vereist [!DNL CJA B2B Edition] licentie; meest uitgebreid; ondersteunt freeform-analyse op accountniveau |
| [!DNL AJO B2B] dashboards + CRM-rapportage | De organisatie verkiest pijpleidingrapportage in de CRM samen met de gegevens van de inkoopgroep te centraliseren | Vereist ontwikkeling van CRM-dashboard; combineert marketing- en verkoopcijfers op één locatie; beperkt tot CRM-rapportagemogelijkheden |

**navigatie UI:** [!DNL AJO B2B Edition] > Dashboards > het Overzicht van de Betrokkenheid/Intelligent Dashboard

**Zeer belangrijke configuratiedetails:**

- Open het [!DNL AJO B2B] Betrokkenheidsdashboard om de betrokkenheidsscores van de inkoopgroep, de volledigheidspercentages en de distributie van het werkgebied te controleren
- Toegang tot het intelligente dashboard voor door AI aangestuurde inzichten over rekeningbereidheid en pijpleidingkwaliteit
- Als u [!DNL CJA B2B Edition] gebruikt: configureer een CJA-verbinding op basis van account, inclusief [!DNL AJO B2B] datasets, stel een B2B-gegevensweergave in met de containers voor Groep en account kopen en maak een werkruimteanalyse voor het aanschaffen van groepsprogressie, opportuniteitcorrelatie en attributie
- Definieer de rapporteringskring: de prestatiesanalyses van de wekelijkse koopgroep, maandelijkse pijpleidingseffect analyse, driemaandelijkse programmaoptimalisering
- Annotaties maken voor belangrijke gebeurtenissen (lanceringen van campagne, vernieuwingen van inhoud, wijzigingen in het scoremodel) die correleren met prestatietrends

**documentatie van Experience League:**

- [B2B-analysedashboards](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Betrokkenheidsdashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Intelligent dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

## Implementatieoverwegingen

In de volgende secties worden onder andere de volgende secties beschreven: guardrails, valkuilen, best practices en beslissingen om zaken af te handelen, waarmee u tijdens de implementatie rekening kunt houden.

### Afbeeldingen en limieten

- [!DNL AJO B2B Edition] de grenzen van de rekeningsreis, met inbegrip van maximum gezamenlijke reizen en maximumrekeningen per reis, volgen de [!DNL AJO B2B Edition] productgidsen - [&#x200B; de Garanties van AJO B2B &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [!DNL RT-CDP B2B Edition] steunt tot 50 B2B schemaklassen en volgt standaardprofiel en segmenteringsgidsen - [&#x200B; Realtime de guardrails van het Profiel van de Klant &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- De evaluatie van het het publiek van de rekening werkt op partijprogramma&#39;s; de updates van het rekeningenpubliek in real time worden niet gesteund voor alle segmenttypes — [&#x200B; de gidsen van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- B2B bronschakelaaropname heeft minimum het plannen intervallen (typisch 15 minuten voor [!DNL Marketo], variërend voor de bronnen van CRM) — [&#x200B; Ingestiegaranties &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- De oppervlakken van het e-mailkanaal zijn beperkt tot 10 per kanaaltype per zandbak — [&#x200B; Journey Optimizer guardrails &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Veelvoorkomende valkuilen

- **het bepalen van teveel rollen per het kopen groep:** over-het specificeren rollen (bijvoorbeeld, die 8-10 verschillende karakters vereisen) maakt het bijna onmogelijk voor het kopen van groepen om volledigheidsdrempels te bereiken. Begin met 3-5 essentiële rollen en breid uit aangezien het model rijpt.
- **plaatsende de drempels van de betrokkenheidsscore te hoog of te laag:** als de drempels te hoog zijn, kwalificeren geen het kopen groepen, die de pijpleiding verhongeren. Als het te laag is, is de omzet van ongekwalificeerde accounts hoog. Begin met historische gegevensanalyse (indien beschikbaar) en herhaling gebaseerd op verkoop terugkoppel.
- **het negeren van persoon-aan-rekening resolutiekwaliteit:** als de personen niet correct met rekeningen worden verbonden, zullen het kopen groepen vermiste leden hebben zelfs wanneer de juiste mensen in dienst worden genomen. Investeer in kwaliteit voor identiteitsoplossing voordat u groepsreizen gaat kopen.
- **over-overseinencontacten in veelvoudige het kopen groepen:** Één enkel contact kan rollen in veelvoudige het kopen groepen (bijvoorbeeld, een CTO houden die een Technische Evaluator voor zowel CRM als de aankopen van het Platform van Gegevens is). Zonder frequentiebeheer ontvangt deze persoon e-mails van elke actieve reis. Implementeren van regels voor de frequentie van de verschillende reizen.
- **het Neglecteren verkoopenablement:** de teams van de Verkoop moeten begrijpen hoe te om het kopen groepsgegevens, betrokkenheidsscores, en verkoopalarm te interpreteren. Zonder training en adoptie faalt de &#39;marketing-naar-verkoop&#39;-overdracht, ongeacht de gegevenskwaliteit.
- **Behandelend rekeningsreizen zoals personenreizen:** De reizen van de rekening werken op rekeningsniveau, die e-mails verzenden naar personen binnen de de koopgroepen van de rekening. Reisontwerp moet er rekening mee houden dat meerdere personen berichten ontvangen per uitvoering van een accountknooppunt, wat fundamenteel anders is dan reizen op persoonlijk niveau [!DNL AJO] .

### Aanbevolen procedures

- **Begin met één oplossingsrente en breid** uit — Bewijs de modelwerken voor één het kopen motie alvorens aan veelvoudige oplossingsbelangen te schrapen. Hierdoor kan het team de rolsjablonen, scoring modellen en inhoud verfijnen voordat het de complexiteit toevoegt.
- **richt het kopen van groepsrollen met het verkoopproces van CRM** - Kaart het kopen groepsrollen aan de personen het verkoopteam reeds erkent. Dezelfde taal gebruiken (economische koper, kampioen, enz.) de overdracht is dus intuïtief .
- **voert een terugkoppel lijn met verkoop** uit — verzamel regelmatig verkoop terugkoppelt op de kwaliteit van marketing-gekwalificeerde rekeningen. Gebruik deze feedback om de drempelwaarden voor betrokkenheidsscores en de kwalificatiecriteria voor rollen af te stemmen.
- **inhoud van het Ontwerp voor rollen, niet alleen stadia** - de Verschillende het kopen groepsrollen hebben verschillende inhoud nodig: de managers willen ROI en strategische invloed, de technische beoordelaars architectuur en integratiedetails willen, willen de eind - gebruikers gebruiksklare demonstraties. Wijs inhoudsactiva aan rollen voor effectievere verpleegkunde toe.
- **de Inzichten van de Verkoop van CRM van de opstelling vroeg** - wacht niet tot de volledige reis levend is om het zicht van CRM op te stellen. Verkoopteams moeten de gegevens van de inkoopgroep in een vroeg stadium zien te vormen om feedback te geven over de nauwkeurigheid van de rol en het richten van accounts.
- **het gebruik wacht strategisch stappen** — B2B die cycli kopen is lang. De stappen in de wachttijd van de account moeten deze realiteit weerspiegelen (intervallen van 5-14 dagen tussen aanrakingen) in plaats van de urgentie in de stijl van de consument (1-3 dagen).
- **de dienstsnelheid van de Monitor, niet alleen betrokkenheidsscore** — Een het kopen groep die van score 20 tot 80 in twee weken gaat signalen sterker dan één die 80 over zes maanden bereikt. Configureer scoring en kwalificatie om rekening te houden met snelheid.

### Handelsbesluiten

De volgende compromissen moeten worden geëvalueerd op basis van de specifieke behoeften van uw organisatie.

#### Volledige inkoopgroep versus volume van pijpleiding

Door alle rollen in te vullen voordat een inkoopgroep in aanmerking komt, wordt de pijpleidingkwaliteit gemaximaliseerd, maar kan het volume van gekwalificeerde accounts aanzienlijk worden beperkt, met name voor nieuwe producten of markten waar de database van de organisatie een beperkte dekking heeft.

- **de hogere volledigheidsdrempel gunt:** kwaliteit van de Pijpleiding; de verkoop ontvangt volledig gevormde het kopen groepen; hogere win tarieven per rekening
- **Lagere volledigheidsdrempel gunst:** Het volume van de Pijpleiding; meer rekeningen bereiken verkoop; bredere dekking; hoger volume maar potentieel lagere kwaliteit
- **Aanbeveling:** begin met een gematigde drempel (60-70% roldekking) en aanpassen gebaseerd op daadwerkelijke win tariefgegevens. Voor gevestigde markten met een goede gegevensdekking neemt u toe naar 80%+. Accepteer in eerste instantie 50-60% voor nieuwe markten en gebruik volledigheidscampagnes voor inkoopgroepen om lacunes op te vullen.

#### Korreligheid van de score versus operationele eenvoud

De hoogst korrelige het scoren modellen (met tientallen activiteitentypes, recentieweging, en rol-specifieke het scoren) verstrekken nauwkeurigere kwalificatiesignalen maar zijn moeilijker te handhaven, uit te leggen en, problemen op te lossen.

- **Hogere granulariteit gunt:** Precisie van kwalificatie; genuanceerde differentiatie tussen rekeningen; betere groepering met complexe het kopen processen
- **Lagere granulariteit gunt:** Operationele eenvoud; gemakkelijker om aan verkoop te handhaven en uit te leggen; snellere implementatie; minder randgevallen
- **Aanbeveling:** Begin met een eenvoudig het scoren model (10-15 activiteitentypes, uniforme puntwaarden) en voeg ingewikkeldheid toe slechts waar het eenvoudige model er niet in slaagt om rekeningskwaliteit te onderscheiden. Documenteer het het scoren model grondig voor verkoopgroepering.

#### Eén reis versus meerdere gespecialiseerde reizen

Een enkele, uitgebreide accountreis die alle stadia en oplossingsbelangen in één canvas behandelt biedt uniforme controle maar kan lastig worden. Meerdere gespecialiseerde reizen (één per fase of per oplossing) zijn eenvoudiger, maar moeilijker te coördineren.

- **Enige reis gunst:** Holistische mening; gemakkelijker om verenigbare timing en overseinen te verzekeren; eenvoudiger om te controleren; één plaats voor alle logica
- **veelvoudige reizen gunnen:** Modulariteit; gemakkelijker om één stadium bij te werken zonder anderen te beïnvloeden; de verschillende teams kunnen verschillende reizen bezitten; schoner canvasontwerp
- **Aanbeveling:** voor Optie A, is één enkele reis aangewezen. Voor Opties B en C gebruikt u een primaire &quot;orchestration&quot;-reis die een rekening houdt met gespecialiseerde subreizen per oplossingsbelang of aankoopfase.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie over de toepassingen en mogelijkheden waarnaar in deze handleiding wordt verwezen.

### [!DNL AJO B2B Edition]

- [AJO B2B edition documentatie home](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Overzicht van kopersgroepen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-overview)
- [Oplossingsbelangen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/solution-interests)
- [Rolsjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates)
- [Koopgroepen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create)
- [Groepsfasen voor kopen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/buying-group-stages)
- [Overzicht van rekeningreizen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview)
- [Transparante knooppunten van account](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes)
- [E-mails met verkoopberichten](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sales-alert-email)
- [CRM-verkoopgegevens](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/buying-groups/crm-sales-insights)

### B2B-e-mail en -inhoud

- [B2B-e-mailauthoring](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/email-authoring)
- [SMS-authoring in AJO B2B](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/sms-authoring)
- [AI Assistant voor het schrijven van e-mail](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/content/ai-assistant-emails)

### B2B-analyses en dashboards

- [Het dashboard voor groepen kopen](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/buying-groups-dashboard)
- [Betrokkenheidsdashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/engagement-dashboard)
- [Intelligent dashboard](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/dashboards/intelligent-dashboard)
- [CJA B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-b2b)

### [!DNL RT-CDP B2B Edition]

- [RT-CDP B2B edition-overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview)
- [B2B-schema&#39;s in Real-Time CDP](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/schemas/b2b)
- [Accountpubliek](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/types/account-audiences)
- [Marketo Engage-bronaansluiting](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)

### Gegevensbasis

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van bronnen](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home)
- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)

### Kanaalconfiguratie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)

### Beheer en privacy van gegevens

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Geavanceerd levenscyclusbeheer van gegevens](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Doelen

- [Overzicht van doelen](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Doelcatalogus](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Doel van LinkedIn-overeenkomend publiek](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)

### Beveiligingsmechanismen

- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Segmenteringsgeleiding](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Ingestiegrepen](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)

### Zelfstudies en aan de slag

- [AJO B2B edition aan de slag](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
- [Zelfstudie RT-CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-tutorial)
