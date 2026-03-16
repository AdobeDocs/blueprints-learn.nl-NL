---
title: Publiek Collaboration met segmentovereenkomst
description: Leer hoe u publiekssegmenten in sandboxen of organisaties kunt delen en afstemmen met Segmentovereenkomst.
solution: Real-Time Customer Data Platform, Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6238'
ht-degree: 0%

---


# Samenwerking van het publiek met de Gelijke van het Segment

Deze handleiding bevat een uitgebreide implementatiereferentie voor publiekssamenwerking met [!DNL Segment Match] in [!DNL Real-Time CDP] en [!DNL Adobe Experience Platform] . Het wordt ontworpen voor oplossingsarchitecten, marketing technologen, en implementatiemengineers die publiekssegmenten over zandbakken of organisaties op een privacy-veilige manier moeten delen en aanpassen.

Gebruik dit plan om de beschikbare benaderingen te begrijpen, compromissen te evalueren, en [!DNL Adobe Experience League] voor gedetailleerde configuratieinstructies te navigeren.

Met [!DNL Segment Match] kunnen twee of meer [!DNL Experience Platform] -organisaties (of sandboxen binnen een organisatie) samenwerken aan publieksgegevens door informatie over segmentlidmaatschap te delen zonder onderliggende PII toegankelijk te maken. Deelnemers kunnen overlappingen schatten, publiek delen en aangepaste profielen activeren voor downstreamdoelen.

## Hoofdlettergebruik

Organisaties moeten steeds meer samenwerken aan publieksgegevens met partners, dochterondernemingen of bedrijfseenheden, terwijl ze strikte privacycontroles behouden. Samenwerking met het publiek lost dit probleem op door beveiligde segmentdeling via [!DNL Segment Match] mogelijk te maken. Dit is een functie binnen [!DNL Real-Time CDP] waarmee twee of meer [!DNL Experience Platform] -organisaties (of sandboxen) gegevens over publieksleden kunnen uitwisselen met gehashte, privacyveilige id&#39;s.

Het bedrijfsscenario impliceert typisch één organisatie (de afzender) die een waardevol publiekssegment heeft gebouwd en het met een partnerorganisatie (de ontvanger) voor gezamenlijke het richten, onderdrukking, of verrijking wil delen. Voordat u gaat delen, kunnen beide partijen de overlappingen van het publiek inschatten om de waarde te bepalen. Zodra gedeeld, kan de ontvangende organisatie het aangepaste publiek door hun eigen bestemmingen activeren.

Dit patroon verschilt van standaardactivering van het publiek, omdat het werkt tussen organisaties of sandboxen in plaats van naar externe reclame- of marketingbestemmingen. Het verschilt ook van &#39;data clean rooms&#39; of samenwerkingsplatforms van derden, omdat het native werkt binnen het Adobe-ecosysteem met behulp van [!DNL Experience Platform] identiteitsinfrastructuur.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

### Nieuwe klanten aanschaffen

Breid de klantenbasis door gerichte aanschafcampagnes, lookend publiek, en betaalde media optimalisering uit. De samenwerking van het publiek laat organisaties toe om nieuwe perspectiefpools te ontdekken door hun segmenten tegen partnerpubliek aan te passen, high-value overlapping te identificeren, en netto-nieuwe klanten door gezamenlijke activering te bereiken.

- **KPIs:** Nieuwe Klanten, de Kosten van de Aankoop van de Klant, Vooruitziendheid/Loodomzetting
- [Nieuwe klanten aanschaffen](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### Verlaag de aanschafkosten van de klant

Verbeter gerichte efficiency, onderdruk bestaande klanten van aanschafcampagnes, en optimaliseer media uitgaven. Door suppressiesegmenten over organisaties of bedrijfseenheden te delen, kunnen de teams verspilde uitgaven aan reeds omgezette klanten vermijden en begrotingen op werkelijk nieuwe vooruitzichten concentreren.

- **KPIs:** Kosten van de Aankoop van de Klant, Kosten per Lood, Efficiëntie
- [Verlaag de aanschafkosten van de klant](/help/blueprints/business-objectives/cost-efficiency/reduce-customer-acquisition-cost.md)

### marketinguitgaven en investeringsrendement optimaliseren

Verbeter het rendement van marketing investering door betere richten, attributie, publieksonderdrukking, en begrotingstoewijzing. [!DNL Segment Match] biedt ondersteuning voor onderdrukking van het publiek in verschillende organisaties en het gezamenlijk richten van doelgroepen die dubbel werk verminderen en de nauwkeurigheid verbeteren.

- **KPIs:** Kostenbesparingen, de Kosten van de Aankoop van de Klant, Incrementele Inkomsten
- [marketinguitgaven en investeringsrendement optimaliseren](/help/blueprints/business-objectives/cost-efficiency/optimize-marketing-spend-roi.md)

## Voorbeelden van tactische gebruiksgevallen

- **uitgever-adverteerder publiek die** aanpassen - het merk van A deelt zijn high-value klantensegment met een media uitgever om overlapping en doel aangepaste gebruikers met gepersonaliseerde advertenties te schatten, verbeterend campagnerelevantie zonder PII bloot te stellen.
- **Onderdrukking van het dwars-merk binnen een holdingbedrijf** — De veelvoudige merken onder een ouderorganisatie delen klantensegmenten om bestaande klanten van zustermerken van aanschafcampagnes te onderdrukken, die verspild verminderen en uitgaven uitgeven.
- **de Verrijking van het medianetsenpubliek van de kleinhandel** - retailer deelt op aankoop-gebaseerde segmenten met CPG merkpartners, toelatend de merken om bewezen kopers op het retailer media netwerk met hogere omzettingspercentages te richten.
- **Co-marketing de ontdekking van het partnerpubliek** — Twee niet-concurrerende merken evalueren publiek overlappend om partnerschapspotentieel te beoordelen alvorens een gezamenlijke campagne te lanceren, gebruikend overlappende raming om publieksengroepering te bevestigen.
- **gegevens coöperatief segment dat** deelt — Organisaties in een gegevens coöperatief aandeel haken publiekssegmenten uit om gericht bereik uit te breiden terwijl het handhaven van privacy naleving en gegevens beheerscontroles.
- **Multi-sandbox publieksenfederatie** — Een globale onderneming deelt publiekssegmenten over regionale zandbakken om verenigbare klant toe te laten die zich op markten richt terwijl het respecteren van de regionale vereisten van de gegevensingezetenschap.
- **het programma van de Loyalty dwars-partner activering** — De aandelen van de loyaliteitscoalitie de segmenten van de loyaliteitsrij met deelnemende handelaren zodat kan elke partner op rij-aangewezen bevorderingen aan de gedeelde klantenbasis aanbieden.
- **Samenwerking van de Meting en van de attributie** - een adverteerder deelt een omzettingssegment met een media partner zodat kan de partner campagnedoeltreffendheid meten door blootgestelde gebruikers tegen omzetters aan te passen.

## Kernprestatie-indicatoren

De volgende hulp KPIs meet het succes van de implementaties van de publiekssamenwerking.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Overlap snelheid publiek | Percentage profielen in het gedeelde segment dat overeenkomt tussen verzender en ontvanger | [!DNL Segment Match] overlap schattingsrapport |
| Identieke grootte publiek | Aantal profielen gevonden en beschikbaar voor activering | [!DNL Segment Match] deelstatus en aantal doelgroepen |
| Nieuwe overname door klant van passend publiek | Netto nieuwe klanten die door campagnes worden verworven die op overeenkomende segmenten richten | Conversie bijhouden bij campagnes met hetzelfde publiek |
| Kostenreductie voor overname door klant | Daling van kosten per verwerving bij gebruik van een passend publiek in vergelijking met een brede doelgerichtheid | Campagnekostenanalyse waarbij overeenkomende versus ongeëvenaarde prestaties van het publiek worden vergeleken |
| Besparingen onderdrukken | Media-uitgaven die zijn bespaard door bekende klanten te onderdrukken van aanschafcampagnes | Vergelijking van media-uitgaven vóór/na onderdrukking |
| Optillen van cameraprestaties | Verbetering van de conversiesnelheid, doorkliksnelheid of betrokkenheid voor campagnes met een vergelijkbaar publiek | A/B-test waarbij overeenkomende publiekscampagnes worden vergeleken met besturing |
| Tijd naar Collaboration | Verlopen tijd van initiatie van segmentaandelen tot activeringsgereedheid | [!DNL Segment Match] werkstroomtijdstempels |

## Hoofdletterpatroon gebruiken

Bij dit gebruik wordt het Collaboration-patroon van Audience gevolgd.

Gebruik [!DNL Segment Match] om doelsegmenten te delen en aan te passen aan verschillende sandboxen of organisaties.

**Keten van de Functie:** de Selectie van het Segment > de Configuratie van de Gelijke Controle > de Schatting van de Overlap > het Delen van het publiek > Activering

## Applicaties

In dit gebruikspatroon worden de volgende toepassingen gebruikt.

- **[!DNL Real-Time CDP]** — Biedt de [!DNL Segment Match] -mogelijkheid voor privacyveilig delen van het publiek, publieksevaluatie voor het maken van segmenten en doelactivering voor downstreamgebruik van overeenkomende doelgroepen.
- **[!DNL Adobe Experience Platform]** — Biedt de infrastructuur voor basisgegevens, zoals identiteitsresolutie, profieleenwording, gegevensbeheer en toestemmingshandhaving waarvan [!DNL Segment Match] afhankelijk is.

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Vereist | Zowel de afzender als de ontvangende organisaties moeten zandbakken hebben die met aangewezen rollen en toestemmingen worden voorzien. Gebruikers die [!DNL Segment Match] beheren, moeten machtigingen hebben om segmenten weer te geven en te delen, verbindingen te configureren en partnerfeeds te beheren. Het beleid ABAC zou moeten worden gevormd om te controleren welke gebruikers segmentaandelen in werking kunnen stellen en goedkeuren. | [&#x200B; overzicht van het Toegangsbeheer &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Verondersteld op plaats | De schema&#39;s XDM voor profielen en gebeurtenissen moeten met de vereiste gebiedsgroepen bestaan. Gegevenssets voor profiel en gebeurtenis moeten worden gemaakt en ingeschakeld voor [!DNL Real-Time Customer Profile] . Het gegevensmodel moet de identiteitsnamespaces steunen die voor segment aanpassing (typisch gehakt e-mail of gehakte telefoon) worden gebruikt. | [&#x200B; XDM overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home) |
| Gegevensbronnen en -verzameling | Verondersteld op plaats | De gegevens van de klant moeten actief naar [!DNL Experience Platform] stromen door gevormde gegevensbronnen (SDKs, bronschakelaars, partijopname). Profielen moeten worden gevuld met de identiteitstypen die worden gebruikt voor [!DNL Segment Match] (e-mail met hashing bijvoorbeeld). | [&#x200B; Bronoverzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/home) |
| Identiteit en profielconfiguratie | Vereist | Identiteitsnaamruimten moeten worden gevormd voor de herkenningstekens die in segment aanpassing worden gebruikt. Zowel de afzender als de ontvanger moeten compatibele naamruimten gebruiken. Het beleid van de fusie moet worden gevormd om profielen correct te verenigen. Er moeten regels voor identiteitskoppeling worden vastgesteld om een nauwkeurige profieloplossing te garanderen. | [&#x200B; Overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) |
| Auditiedefinitie en segmentatie | Vereist | Source-doelgroepen moeten worden gedefinieerd en geëvalueerd voordat ze via [!DNL Segment Match] kunnen worden gedeeld. Soorten publiek moet worden gemaakt met [!DNL Segment Builder] of [!DNL Audience Composition] als de batchevaluatie is voltooid. Alleen batchgeevalueerde doelgroepen komen in aanmerking voor [!DNL Segment Match] delen. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Met berekende kenmerken, zoals de aankoopwaarde tijdens de levensduur, de betrokkenheidsscore of de affiniteit van het product, kunt u nauwkeuriger segmenten voor delen maken. Invoersegmenten van hogere kwaliteit leiden tot een waardevollere samenwerking. | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Beleid voor inwilliging en gegevensbewaring zorgt ervoor dat gedeelde segmenten voldoen aan privacyregels. Het beleid voor het verlopen van de gegevensset helpt de levenscyclus van ontvangen publieksgegevens te beheren. Met de functie voor het afdwingen van toestemming wordt het delen van profielen die zijn uitgeschakeld, voorkomen. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Opgenomen | Het beleid inzake gegevensbeheer moet worden geëvalueerd voordat segmenten worden gedeeld om naleving te garanderen. Labels op identiteitsvelden en profielkenmerken bepalen wat kan worden gedeeld. De handhaving van de governance verhindert dat onbevoegde gegevens in segmentaandelen worden opgenomen. | [&#x200B; Overzicht van het beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home) |
| Bewaking en waarneming | Aanbevolen | Door het delen van het [!DNL Segment Match] -proces te controleren, schattingstaken te overlappen en activeringsgegevensstromen kunt u fouten vroeg detecteren. Het alarm kan voor aandeelmislukkingen of onverwacht lage gelijke tarieven worden gevormd. | [&#x200B; overzicht van de Inzichten van de Waarnemelijkheid &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Aanbevolen | Wanneer u de prestaties van campagnes met overeenkomende doelgroepen meet, wordt de waarde van het samenwerkingsproject gevalideerd. [!DNL Customer Journey Analytics] de analyse kan gelijke prestaties van de publiekscampagne met controlegroepen vergelijken. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de catalogus van de toepassingsfunctie uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Real-Time CDP]

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Fase 1: Segmentselectie en -voorbereiding | Evalueer segmentlidmaatschap met batchevaluatie om het publiek te produceren dat via [!DNL Segment Match] wordt gedeeld |
| Samenstelling publiek | Fase 1: Segmentselectie en -voorbereiding | Naar keuze stel afgeleid publiek (rang, spleet, sluit uit, verrijkt) samen om meer gerichte segmenten voor het delen tot stand te brengen |
| Goedkeuring en handhaving van bestuur | Fase 2: Identieke configuratie en bestuur | Beleid en voorkeuren voor gegevensgebruik afdwingen voordat u segmenten deelt om naleving te garanderen |
| Doelgroepactivering | Fase 5: Gelijktijdige Audience Activation | Publiceer passend publiek dat via [!DNL Segment Match] wordt ontvangen aan externe bestemmingen voor het richten of onderdrukken |
| Doelconfiguratie | Fase 5: Gelijktijdige Audience Activation | Verbindingen met externe bestemmingen configureren waar overeenkomend publiek wordt geactiveerd |

## Vereisten

- Zowel zender- als ontvangende organisaties hebben [!DNL Real-Time CDP] provisioned with [!DNL Segment Match] entitlement
- [!DNL Segment Match] is ingeschakeld voor organisaties of sandboxen die deelnemen aan de samenwerking
- De verbinding van de partner is gevestigd tussen de afzender en ontvangende organisaties in [!DNL Segment Match] UI
- Beide organisaties gebruiken compatibele naamruimten (beide hebben bijvoorbeeld een hashed-e-mail geconfigureerd)
- Source-publiek is gedefinieerd en geëvalueerd met populaties die niet gelijk zijn aan nul
- Beleid inzake gegevensbeheer wordt geconfigureerd en labels voor gegevensgebruik worden toegepast op relevante datasets en velden
- Gebruikers aan beide zijden hebben de benodigde machtigingen om [!DNL Segment Match] -verbindingen, -shares en -feeds te beheren
- De gebieden van de toestemming worden bevolkt op profielen om op toestemming gebaseerde het filtreren vóór het delen toe te laten

## Implementatieopties

De volgende opties beschrijven verschillende benaderingen voor het implementeren van publiekssamenwerking met [!DNL Segment Match]. Selecteer de optie die het beste aansluit bij uw organisatorische structuur en samenwerkingsvereisten.

### Optie A: Directe segmentaandelen (één op één)

Deze optie is het meest geschikt voor bilaterale partnerschappen tussen twee specifieke organisaties, zoals een adverteerder en een uitgever, of twee merken in een co-marketingovereenkomst.

**hoe het werkt:**

In een direct één-aan-één segmentaandeel, selecteert de afzenderorganisatie één of meerdere geëvalueerde publiek, stelt een aandeel met een specifieke partnerorganisatie in werking, en de ontvanger keurt het aandeel goed. De overlap schatting wordt automatisch uitgevoerd om het percentage en het volume van overeenkomende profielen aan beide partijen te laten zien voordat het aandeel is voltooid.

De afzender bepaalt welke identiteitsnaamruimten om te gebruiken voor aanpassing en selecteert de segmenten om te delen. De ontvanger controleert het inkomende aandeel, keurt het goed, en het overeenkomende publiek wordt beschikbaar in hun publiekslijst voor stroomafwaartse activering. Alleen gehakte identiteitsoverlapping wordt uitgewisseld — geen onderliggende PII- of profielkenmerkgegevens overschrijden de organisatiegrenzen.

Deze aanpak is eenvoudig en biedt beide partijen volledige controle. De afzender kiest precies wat te delen en met wie, en de ontvanger heeft de optie om elk aandeel goed te keuren of te verwerpen.

**Zeer belangrijke overwegingen:**

- Vereist expliciete opstelling van de partnerverbinding tussen de twee organisaties
- Beide organisaties moeten identiteitsnaamruimten overeenkomen voor overeenkomst
- Overlappingsschatting zorgt voor transparantie vóór toezegging
- Elk aandeel moet afzonderlijk worden beheerd en gecontroleerd

**Voordelen:**

- Eenvoudige, goed begrepen bilaterale workflow
- Volledige transparantie door overlap schatten alvorens te delen
- Korrelige controle — de afzender kiest precies welke segmenten om te delen
- Privacy-veilig — alleen hashid&#39;s worden gebruikt voor overeenkomsten
- Ontvanger kan aandelen selectief accepteren of afwijzen

**Beperkingen:**

- Schaalt niet efficiënt wanneer het samenwerken met vele partners gelijktijdig
- Voor elk partnerschap is afzonderlijke configuratie en beheer van de verbinding vereist
- De configuratie van het aandeel moet voor elk nieuw segment worden herhaald

**Experience League:**

- [Overzicht van afstemming van segment](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Problemen met segmentovereenkomst oplossen](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Optie B: De distributie van het multi-partnersegment (één-aan-vele)

Deze optie is het best voor organisaties die segmenten met veelvoudige partners gelijktijdig moeten delen, zoals een retailmedianetwerk dat op aankoop-gebaseerde segmenten met veelvoudige merkadverteerders deelt, of een holdingmaatschappij die segmenten aan dochtermerken distribueert.

**hoe het werkt:**

In een één-aan-vele distributiemodel, vestigt de afzenderorganisatie [!DNL Segment Match] verbindingen met veelvoudige partnerorganisaties en deelt de zelfde of verschillende segmenten met elk. De afzender beheert een portefeuille van partnerverbindingen en kan verschillende publiekssegmenten met verschillende partners selectief delen die op de verhouding en gebruiksgeval worden gebaseerd.

Elke partnerverbinding werkt onafhankelijk — de overlap raming, aandeelaanvaarding, en de activering worden beheerd per partner. De afzender kan controleren welke segmenten elke partner ontvangt, toelatend gedifferentieerde samenwerkingsstrategieën (b.v., ontvangen de premiepartners meer korrelige segmenten, ontvangen de standaardpartners bredere degenen).

Deze benadering gebruikt het zelfde onderliggende [!DNL Segment Match] mechanisme zoals Optie A maar past het op schaal met een operationeel kader toe voor het beheren van veelvoudige gezamenlijke partnerschappen.

**Zeer belangrijke overwegingen:**

- Vereist robuuste operationele processen voor het beheer van meerdere partnerschappen
- Het bestuursbeleid moet rekening houden met het delen van dezelfde segmenten met meerdere externe partijen
- Elke partner kan verschillende identiteitsnaamruimten gebruiken, die flexibele configuratie vereisen
- De overlappingen tarieven zullen door partner variëren, die per partnerevaluatie vereist

**Voordelen:**

- Schaalt publiekssamenwerking over een ecosysteem van partners
- Gedifferentieerde het delen strategieën per partner
- Gecentraliseerd beheer van alle uitgaande segmentaandelen van één organisatie
- Elk partnerschap handhaaft onafhankelijke controle op bestuur en instemming

**Beperkingen:**

- De operationele ingewikkeldheid verhoogt met elke extra partner
- De controle en het oplossen van problemen moeten per-partner worden gedaan
- Controle van de governance vereist voor elke nieuwe partnerverbinding
- Partners zien elkaars gegevens niet of delen status

**Experience League:**

- [Overzicht van afstemming van segment](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### Optie C: Diverse sandboxpublieksfederatie

Deze optie is het meest geschikt voor grote ondernemingen met meerdere [!DNL Experience Platform] -sandboxen (bijvoorbeeld regionale sandboxen, merkspecifieke sandboxen of specifieke milieusandboxen) die doelsegmenten over interne grenzen heen moeten delen zonder onbewerkte gegevens te verplaatsen.

**hoe het werkt:**

In plaats van te delen tussen verschillende organisaties, gebruikt de publieksfederatie van verschillende sandboxen [!DNL Segment Match] om publiekssegmenten tussen sandboxen binnen dezelfde organisatie te delen. Hierdoor kan een wereldwijd marketingteam een segment maken in een centrale sandbox en dit delen met regionale sandboxen, of kan merkspecifieke sandboxen suppressielijsten met elkaar delen.

De werkstroom weerspiegelt het directe segmentaandeel (Optie A) maar werkt binnen de organisatorische grens. Sandbox-naar-sandbox-verbindingen worden tot stand gebracht via [!DNL Segment Match] en segmenten worden gedeeld met behulp van hetzelfde privacy-safe matching proces. De ontvangende zandbak krijgt het aangepaste publiek als nieuw publiek dat door zijn eigen plaatselijk gevormde bestemmingen kan worden geactiveerd.

Deze benadering is bijzonder waardevol wanneer de vereisten van de gegevensresidentie het bewegen van ruwe klantengegevens tussen regio&#39;s verhinderen maar publiek-vlakke samenwerking wordt toegelaten.

**Zeer belangrijke overwegingen:**

- Vereist [!DNL Segment Match] -machtiging die het delen tussen sandboxen ondersteunt
- Identiteitsnaamruimten moeten consistent zijn in alle sandboxen
- Het beleid voor samenvoegen in elke sandbox kan profielen op een andere manier oplossen, wat mogelijk van invloed is op de percentages voor overeenkomsten
- Beleid voor governance wordt onafhankelijk toegepast per sandbox

**Voordelen:**

- Schakelt publiekssamenwerking in zonder onbewerkte gegevens over sandboxgrenzen te verplaatsen
- Biedt ondersteuning voor residente gegevens en vereisten voor regionale naleving
- Gebruikt bestaande infrastructuur voor organisatorische identiteit
- Eenvoudiger revisie van bestuur sinds delen plaatsvindt binnen dezelfde organisatie

**Beperkingen:**

- Vereist een consistente naamruimteconfiguratie voor alle sandboxen
- Afstemmen is afhankelijk van consistentie in samenvoegbeleid tussen sandboxen
- Hiermee wordt niet ingegaan op de samenwerkingsbehoeften tussen organisaties
- Sandbox Tooling kan nodig zijn om schema en configuratie te synchroniseren

**Experience League:**

- [Overzicht van afstemming van segment](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Overzicht van sandboxen](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

### Optievergelijking

In de volgende tabel worden de drie implementatieopties vergeleken met de belangrijkste criteria.

| Criteria | Optie A: Aandeel direct segment | Optie B: Distributie voor meerdere partners | Option C: Cross-Sandbox Federation |
| --- | --- | --- | --- |
| Best voor | Bilaterale partnerschappen | Samenwerking op ecosysteemschaal | Intern delen tussen sandboxen |
| Complexiteit | Laag | Hoog | Gemiddeld |
| Aantal partners | 1 | Veel | Interne sandboxen |
| Overheadkosten voor bestuur | Laag | Hoog (per-partneroverzicht) | Medium (binnen organisatie) |
| Operationeel beheer | eenvoudig | Vereist partnerbeheerframework | Gemiddeld |
| Ondersteuning voor gegevensresidentie | NVT | Afhankelijk van partnerlocatie | Sterk |
| Vereisten | Instellen van partnerverbinding | Meerdere partnerverbindingen | Cross-sandbox [!DNL Segment Match] |

### Kies de juiste optie

Gebruik de volgende beslissingsrichtlijnen om de juiste implementatieaanpak te kiezen:

1. **werkt u met een externe organisatie of binnen uw eigen organisatie samen?**
   - Externe organisatie: ga verder met vraag 2.
   - Binnen uw eigen organisatie (over zandbakken): kies **Optie C** (de Federatie van de Schaduwen).

2. **hoeveel externe partners u met zult samenwerken?**
   - Één partner: kies **Optie A** (het Directe Aandeel van het Segment).
   - Veelvoudige partners: kies **Optie B** (Multi-Partner Distribution).

3. **hebt u de beperkingen van de gegevensingezetenschap die het bewegen van ruwe gegevens over gebieden verhinderen?**
   - Ja: kies **Optie C** ongeacht of de partners intern of extern zijn — gebruik het delen van dwars-zandbak om gegevensplaats te handhaven.

## Uitvoeringsfasen

De volgende fasen beschrijven het implementatieproces van begin tot eind voor publiekssamenwerking met [!DNL Segment Match].

### Fase 1: Segmenten selecteren en voorbereiden

**functie van de Toepassing:** [!DNL Real-Time CDP]: De Evaluatie van het publiek, [!DNL Real-Time CDP]: De Samenstelling van het publiek

In deze fase worden de publiekssegmenten gedefinieerd en geëvalueerd die via [!DNL Segment Match] worden gedeeld. De bronsegmenten moeten volledig worden geëvalueerd met populaties die niet gelijk zijn aan nul voordat ze kunnen worden geselecteerd voor delen. Deze fase behandelt ook facultatieve publiekssamenstelling om segmenten te verfijnen alvorens te delen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: De definitiebenadering van het publiek**
>
>Hoe moeten de doelgroepen voor delen worden gecreëerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Segment Builder (segmentregels) | Standaardpublieksdefinities op basis van profielkenmerken, gebeurtenissen of segmentlidmaatschap | Ondersteunt batch-, streaming- en edge-evaluatie; meest flexibel voor het definiëren van criteria |
>| Samenstelling publiek | Afgeleide doelgroepen die bewerkingen met betrekking tot bestaande segmenten op een rang, splitsen, uitsluiten of vergroten | Alleen batchevaluatie wordt ondersteund; beperkt tot 10 compositiekanaals per sandbox |
>| Federale compositie publiek | Soorten publiek dat is samengesteld op basis van externe query&#39;s voor gegevenspakhuis zonder gegevens in te voeren [!DNL Experience Platform] | Vereist [!DNL Federated Audience Composition] machtiging; gegevens worden in het pakhuis opgeslagen |

>[!NOTE]
>
>**Besluit: De evaluatiemethode van de Audience**
>
>[!DNL Segment Match] vereist een publiek dat in een batch wordt geëvalueerd. Hoe moet de evaluatie worden gepland?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Geplande partij (dagelijks) | Standaardgebruiksituaties waarbij de dagelijkse publieksvernieuwing volstaat | Standaardevaluatieschema; eenvoudig te beheren |
>| On-demand batch | Ad-hoc het delen behoeften waar u het recentste publiek onmiddellijk wilt delen | Vereist handmatige trigger; handig voor tijdgevoelige samenwerking |
>| Aangepast schema | Specifieke timingvereisten die aan de vensters van de partneractivering worden gericht | Een aangepast uitsnijdschema configureren; complexer maar nauwkeuriger |

**navigatie UI:** Klant > Soorten publiek > leidt tot publiek > bouwt regel (voor [!DNL Segment Builder]) of stelt publiek samen (voor [!DNL Audience Composition])

**Zeer belangrijke configuratiedetails:**

- Bepaal publiekscriteria gebruikend profielattributen, gedragsgebeurtenissen, en/of segmentlidmaatschap
- Zorg ervoor dat het publiek een samenvoegbeleid gebruikt dat compatibel is met de naamruimten die worden gebruikt voor [!DNL Segment Match]
- Controleren of de doelpopulatie na evaluatie niet gelijk is aan nul
- Onderdrukkingsregels toepassen om profielen uit te sluiten die niet mogen worden gedeeld (bijvoorbeeld profielen die hebben opgegeven dat gegevens niet mogen worden gedeeld)

**waar de opties uiteenlopen:**

**voor Optie A (Direct Segment Share):**
Bereid de specifieke segmenten voor u met uw enige partner van plan bent te delen. Focus op kwaliteit boven kwantiteit: curate segmenten die een duidelijke waarde voor het partnerschap bieden.

**voor Optie B (multi-Partner Distributie):**
Bereid een portefeuille van segmenten voor die met verschillende partners kunnen worden gedeeld. Overweeg het creëren van partner-specifieke segmenten als de verschillende partners verschillende publieksdefinities nodig hebben. Gebruik consistente naamgevingsconventies om segmenten tussen partnerschappen te beheren.

**voor Optie C (dwars-Sandbox Federatie):**
Zorg ervoor dat het bronpubliek in de verzendende sandbox identiteitsnaamruimten gebruikt die in de ontvangende sandbox aanwezig zijn. Controleer of het samenvoegbeleid is uitgelijnd op de verschillende sandboxen.

**documentatie van Experience League:**

- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Overzicht van Audience Composition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Evaluatiemethoden](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home#evaluation-methods)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Fase 2: Combinatie en governance configureren

**de functie van de Toepassing:** [!DNL Real-Time CDP]: Toestemming &amp; de Handhaving van het Bestuur

In deze fase wordt de [!DNL Segment Match] -verbinding tussen organisaties of sandboxen tot stand gebracht, worden de naamruimten geconfigureerd die worden gebruikt voor overeenkomsten en wordt gegarandeerd dat het beleid voor gegevensbeheer het delen toestaat. De handhaving van de governance handelt als beleidspoort die moet worden ontruimd alvorens om het even welke segmentgegevens wordt gedeeld.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Identiteitsnaamruimte voor aanpassing**
>
>Welke identiteitsnaamruimte wordt gebruikt om profielen tussen afzender en ontvanger aan te passen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Onderbroken e-mail (SHA-256) | Beide organisaties verzamelen e-mailadressen en kunnen deze consistent hashen | Meest gebruikelijke combinatietoets; hoge match-rates voor gebruik door de consument; beide zijden moeten hetzelfde hash-algoritme gebruiken |
>| Onderbroken telefoonnummer | E-mail is niet consistent beschikbaar, maar telefoonnummers zijn | Lagere dekking dan e-mail in veel markten; nuttig voor mobiel-eerste publiek |
>| Aangepaste naamruimte (bijvoorbeeld &#39;hashed loyalty ID&#39;) | Organisaties delen een gemeenschappelijke id voor loyaliteit of lidmaatschapsprogramma | Hoogste gelijke tarieven voor bekende gedeelde klantenbases; vereist reeds bestaande gedeelde infrastructuur van identiteitskaart |
>| Meerdere naamruimten | Het maximaliseren van het gelijke tarief is kritiek en beide organisaties hebben veelvoudige verenigbare herkenningstekens | Verhoogt gelijke tarieven maar voegt ingewikkeldheid toe; elke namespace moet onafhankelijk worden gevormd |

>[!NOTE]
>
>**Besluit: De controle van het bestuur van gegevens**
>
>Welke governancecontroles moeten vóór het delen worden voltooid?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Evaluatie van standaardbestuur | Gebruiksscenario met standaardlabels en standaardbeleidsregels voor gegevensgebruik | Evalueer marketing actie &quot;Uitvoer naar Derde&quot;tegen datasetetiketten; los om het even welke schendingen alvorens het delen op te lossen |
>| Verbeterd bestuur met filters van toestemming | Delen met externe partners waar uitdrukkelijk moet worden gecontroleerd of er toestemming is | Toevoegen van op toestemming gebaseerde filters om profielen uit te sluiten zonder toestemming te delen (bijv. consents.share.val = &#39;n&#39;); strikter maar veiliger |
>| Herziening van de interne governance | Delen tussen sandboxen binnen dezelfde organisatie | Lichtere governancevereisten omdat gegevens binnen de grenzen van de organisatie blijven; nog steeds labels voor gegevensgebruik controleren |

**navigatie UI:** Klant > Soorten publiek > Afstemming van segment > de verbindingen van de Partner

**Zeer belangrijke configuratiedetails:**

- Vestig een partnerverbinding door verbindingsherkenningstekens tussen afzender en ontvangende organisaties uit te wisselen
- Vorm de identiteitsnamespaces die voor aanpassing aan beide kanten zullen worden gebruikt
- De evaluatie van het beleid van het gegevensbeheer van de looppas tegen het marketing actie verbonden aan segment het delen
- Controleren of machtigingsvelden worden ingevuld bij profielen en of profielen zonder gedeelde toestemming zijn uitgesloten
- De etiketten van het gegevensgebruik van het overzicht op de datasets en schemagebieden inbegrepen in het aandeel

**waar de opties uiteenlopen:**

**voor Optie A (Direct Segment Share):**
Creëer één enkele partnerverbinding. Vorm identiteitsnaamruimten met uw specifieke partner. De herziening van het bestuur richt zich op de bilaterale betrekkingen.

**voor Optie B (multi-Partner Distributie):**
Vestig en beheer veelvoudige partnerverbindingen. Elke partner kan een afzonderlijke controle van het bestuur vereisen. Documenteer de goedkeuring van het bestuur voor elk partnerschap. Overweeg een checklist voor governance te creëren om partner onboarding te stroomlijnen.

**voor Optie C (dwars-Sandbox Federatie):**
Sandbox-naar-sandbox-verbindingen tot stand brengen binnen de organisatie. Beheer is doorgaans eenvoudiger omdat delen intern plaatsvindt. Zorg ervoor dat naamruimten in alle sandboxen consistent zijn.

**documentatie van Experience League:**

- [Overzicht van afstemming van segment](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Beleidshandhaving](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Toestemming en voorkeuren](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

### Fase 3: Overlappende schatting

**functie van de Toepassing:** [!DNL Real-Time CDP]: De Evaluatie van het publiek (voor het schatten van overlapping)

Deze fase stelt de overlappende schatting tussen de segmenten van de afzender en de het profielbasis van de ontvanger in werking. De raming van de overlapping verstrekt beide partijen het verwachte gelijke volume en het percentage alvorens aan het volledige segmentaandeel te verbinden, toelatend geïnformeerde besluiten over de waarde van de samenwerking.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Overlappingsdrempel voor procedure**
>
>Welk minimum overlappende percentage rechtvaardigt de voortzetting van het volledige segmentaandeel?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Geen minimumdrempel | Experimentele partnerschappen of wanneer overlappingen waarde opleveren | Geschikt voor eerste samenwerkingsprojecten waarbij u de relatie test |
>| Lage drempelwaarde (1-5%) | Groot publiek samenwerkingsverband waarbij zelfs kleine overlapping een aanzienlijk volume vertegenwoordigt | Algemeen voor relaties tussen uitgevers en adverteerders met grote doelgroepen |
>| Medium-drempel (5-20%) | Standaardpartnerschappen waarbij een zinvolle overlapping wordt verwacht | Typisch voor co-marketing of zelfde-industrie samenwerking |
>| Hoge drempel (20%+) | Partnerschappen waarbij een sterke doelgerichtheid een voorwaarde is | Gezamenlijk voor loyaliteitscoalities of nauw geïntegreerde merkpartnerschappen |

**navigatie UI:** Klant > Soorten publiek > Afstemming van segmenten > Aandelen > Overlap schatten

**Zeer belangrijke configuratiedetails:**

- Selecteer de segmenten die u wilt opnemen in de overlap-schatting
- Controleer het overlappingsrapport met het aantal overeenkomende profielen en het percentage
- Deel de resultaten van overlappende schattingen ter goedkeuring met de belanghebbenden aan beide zijden
- Documenteer de overlappende metriek als basislijn voor het meten van samenwerkingsdoeltreffendheid
- Als de overlapping onder de aanvaardbare drempel is, denk na aanpassend segmentdefinities of overeenstemmende configuratie alvorens te werk te gaan

**documentatie van Experience League:**

- [Overzicht van afstemming van segment](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)

### Fase 4: Soorten publiek delen

**functie van de Toepassing:** [!DNL Real-Time CDP]: De Evaluatie van het publiek (voor aandeeluitvoering)

Deze fase voert het daadwerkelijke segmentaandeel van afzender aan ontvanger uit. De afzender stelt het aandeel voor de geselecteerde segmenten in werking, en de ontvanger keurt het inkomende aandeel goed. Zodra goedgekeurd, verschijnt het overeenkomende publiek in de publiekslijst van de ontvanger als nieuw publiek beschikbaar voor stroomafwaartse activering.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: De richting van het aandeel**
>
>Wat is het delende model voor deze samenwerking?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Eenwegs delen (zender naar ontvanger) | Asymmetrisch partnerschap waarbij slechts één partij publieksgegevens verstrekt | Eenvoudigste model; zender deelt, ontvanger activeert; gemeenschappelijk in adverteerder-uitgeversverhoudingen |
>| Bidirectioneel aandeel | Beide partijen profiteren van het met elkaar delen van het publiek | Beide organisaties handelen als afzender en ontvanger gelijktijdig; vereist twee aandeelconfiguraties; gemeenschappelijk in co-marketing partnerschappen |

>[!NOTE]
>
>**Besluit: Het aandeel verfrist cadence**
>
>Hoe vaak zou het gedeelde publiek met bijgewerkt segmentlidmaatschap moeten worden verfrist?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Eenmalig delen | Het testen van de samenwerking of voor een specifieke campagne met een vast publiek | Eenvoudigst; geen doorlopend onderhoud; publiek wordt in de loop der tijd stabiel |
>| Terugkerend aandeel (uitgelijnd met batchbeoordeling) | Lopende partnerschappen waarbij het aantal deelnemers verandert en actueel moet blijven | Vereist controle van vernieuwingsstatus; meest algemeen voor productiesamenwerking |

**navigatie UI:** Klant > Soorten publiek > de Gelijke van het Segment > Aandelen > Create aandeel (afzender) of Accepteer aandeel (ontvanger)

**Zeer belangrijke configuratiedetails:**

- De afzender selecteert de segmenten om te delen en stelt het aandeel met de gevormde partner in werking
- De ontvanger controleert de inkomende aandeeldetails (segmentnamen, geschatte grootte, gebruikte identiteitsnamespaces)
- De ontvanger accepteert het delen om het overeenkomende publiek in de sandbox te maken
- Controleren of het overeenkomende publiek wordt weergegeven in de publiekslijst van de ontvanger met de verwachte populatie
- Bevestig dat het overeenkomende publiek op de juiste wijze is gelabeld voor het bijhouden van governance

**waar de opties uiteenlopen:**

**voor Optie A (Direct Segment Share):**
Eén aandeel uitvoeren met uw partner. Controleer de deelstatus en verifieer het overeenkomende publiek aan de ontvangerszijde.

**voor Optie B (multi-Partner Distributie):**
Voer aandelen voor elke partner onafhankelijk uit. De status van het aandeel van het spoor over alle partnerschappen. Overweeg de onthutsende start van delen om de verwerkingsbelasting te beheren.

**voor Optie C (dwars-Sandbox Federatie):**
Het delen van de sandbox uitvoeren. Het overeenkomende publiek wordt weergegeven in de lijst met doelgroepen van de ontvangende sandbox. Controleer of de ontvangende sandbox de benodigde doelconfiguraties voor activering achteraf heeft.

**documentatie van Experience League:**

- [Overzicht van afstemming van segment](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Problemen met segmentovereenkomst oplossen](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Fase 5: overeenkomend publiek activeren

**functie van de Toepassing:** [!DNL Real-Time CDP]: De Configuratie van de Bestemming, [!DNL Real-Time CDP]: Audience Activation

Deze fase activeert het overeenkomende publiek (aan de ontvangerskant) aan externe bestemmingen voor het richten, onderdrukken, of downstreamgebruik. Het overeenkomende publiek wordt behandeld als elk ander publiek in de sandbox van de ontvanger en kan worden geactiveerd via de standaardworkflow voor doelactivering.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Het type van Bestemming voor aangepast publiek**
>
>Waar moet het overeenkomende publiek worden geactiveerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Advertising-bestemmingen (Google, Meta, Trade Desk) | Gelijkend publiek gebruiken voor adverteren of onderdrukken | Vereist bestemmingsverbinding en authentificatie; behoudens bestemmingsspecifieke tariefgrenzen en formaatvereisten |
>| Opslagbestemmingen voor cloud (S3, Azure, GCS) | Overeenkomende doelgroepen exporteren als bestanden voor gebruik in externe systemen | Ondersteunt aanpassing van bestandsindelingen; batchexportplanning vereist; flexibel voor downstreamverwerking |
>| CRM/marketingautomatiseringsbestemmingen | CRM-records verrijken of automatische marketingworkflows activeren met overeenkomende publieksgegevens | Vereist gebiedstoewijzing aan het schema van CRM; nuttig voor verkoop-marketing groepering |
>| Personalization-doelen (web, app) | Benoemd publiekslidmaatschap gebruiken voor on-site personalisatie | Vereist randevaluatie van het overeenkomende publiek of activering van streaming; latentie varieert per doel |

>[!NOTE]
>
>**Besluit: Het programma van de Activering**
>
>Hoe vaak moet het overeenkomende publiek naar de bestemming worden geëxporteerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Dagelijkse incrementele export | Standaardactivering met regelmatige publieksupdates | Alleen gewijzigde profielen; lager gegevensvolume; meest gangbaar voor lopende campagnes |
>| Dagelijks volledig exporteren | Doelen waarvoor telkens een volledig publieksbestand vereist is | Hoger gegevensvolume; verzekert bestemming volledige publieksstaat heeft; sommige bestemmingen vereisen volledige uitvoer |
>| Activering op aanvraag | Ad-hoc campagne start of tijdgevoelige activering | Handmatige trigger; bypass scheduled cadence; alleen beschikbaar voor batchbestemmingen |

**navigatie UI:** Verbindingen > Doelen > Catalogus (voor bestemmingsopstelling) of doorbladert > Uitgezochte bestemming > activeert publiek (voor activering)

**Zeer belangrijke configuratiedetails:**

- Vorm de bestemmingsverbinding met aangewezen authentificatiegeloofsbrieven
- Profielkenmerken van het overeenkomende publiek toewijzen aan doelvelden (identiteitsvelden, profielkenmerken, segmentlidmaatschap)
- Het exportschema configureren (incrementeel versus volledig, dagelijks versus aangepast)
- Controleer de activeringsgegevensstroom om te bevestigen dat de overeenkomende profielen voor publiek zijn geëxporteerd.
- Verifieer activeringsmetriek (geëxporteerde profielen, records zijn mislukt) in de controleweergave van het doel

**waar de opties uiteenlopen:**

**voor Optie A (Direct Segment Share):**
De ontvanger activeert het overeenkomende publiek door zijn standaarddoelworkflow. Er is geen speciale configuratie nodig buiten de normale doelactivering.

**voor Optie B (multi-Partner Distributie):**
Elke ontvangende organisatie activeert onafhankelijk passend publiek door hun eigen bestemmingen. De afzender heeft geen zicht in ontvangend-zijactivering.

**voor Optie C (dwars-Sandbox Federatie):**
De ontvangende sandbox moet een eigen doelconfiguratie hebben. Doelen kunnen niet worden gedeeld door sandboxen. Controleer of de benodigde doelverbindingen zijn ingesteld voor de ontvangende sandbox.

**documentatie van Experience League:**

- [Overzicht van doelen](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Doelcatalogus](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Dataflows voor doelen controleren](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Activeringsinstructies](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

## Implementatieoverwegingen

Bekijk de volgende overwegingen voor en tijdens de implementatie om algemene problemen te voorkomen en optimaliseer de samenwerking met het publiek.

### Guardrails en limieten

- [!DNL Segment Match] gebruikt gehakte herkenningstekens voor aanpassing — geen PII overschrijdt organisatorische grenzen. Zie [&#x200B; Overzicht van de Overeenkomst van het Segment &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview).
- Alleen batchgeevalueerde soorten publiek kunnen worden gedeeld via [!DNL Segment Match] . Streaming en Edge-geëvalueerde segmenten moeten worden geconverteerd naar batchevaluatie voordat ze kunnen worden gedeeld.
- Het maximum van 4.000 segmentdefinities per zandbak is op zowel bron als ontvangen segmenten van toepassing. Zie [&#x200B; de guardrails van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails).
- De nauwkeurigheid van overlap is afhankelijk van het volume van overeenkomende id&#39;s. Kleine doelgroepen kunnen minder nauwkeurige schattingen laten zien.
- Activeringsinstructies gelden voor overeenkomende doelgroepen op dezelfde manier als voor andere doelgroepen: maximaal 100 gegevensstromen per bestemming. Zie [&#x200B; guardrails van de Activering &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails).
- Samengestelde doelgroepen worden volgens een batchschema geëvalueerd en zijn beperkt tot 10 compositiekanaals per sandbox. Zie [&#x200B; de guardrails van de Samenstelling van de Publiek &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails).

### Veelvoorkomende valkuilen

- **het Inconsistente identiteitshashing tussen afzender en ontvanger:** als beide organisaties e-mailadressen maar verschillende het hakken algoritmen, normaliseringsregels, of salt waarden hashing, zullen gelijke tarieven dichtbij nul zijn. Beide partijen moeten overeenstemming bereiken over de exacte hashingspecificatie (bv. SHA-256 op gedownloade, bijgesneden e-mail) voordat de verbinding tot stand wordt gebracht.
- **het Delen van publiek zonder behoorlijk overzicht:** Het initiëren van een segmentaandeel zonder het beleid van het gegevensgebruik te evalueren kan tot nalevingsschendingen leiden. Voer altijd een beleidsevaluatie voor governance uit tegen de marketingactie &quot;Exporteren naar derde partij&quot; voordat u segmenten deelt met externe organisaties.
- **Lage gelijke tarieven toe te schrijven aan de hiaten van de identiteitsdekking:** als het publiek van de afzender hoofdzakelijk door ECID (anonieme koekje) wordt geïdentificeerd maar passende namespace hashed e-mail is, zal het gelijke tarief zeer laag zijn omdat de anonieme profielen geen e-mailadressen hebben. Verifieer dat het bronpubliek voldoende dekking van gevormde passende identiteit namespace heeft.
- **het vergeten om het aandeel op de ontvangerskant goed te keuren:** het gedeelde publiek verschijnt niet in de het publiekslijst van de ontvanger tot het aandeel uitdrukkelijk wordt goedgekeurd. Coördineer met de ontvanger om tijdige acceptatie te verzekeren, vooral voor tijdgevoelige campagnes.
- **de Vergroting paste publiek toe toe toe te schrijven aan misgroepering van het evaluatieschema:** als het bronpubliek van de afzender dagelijks evalueert maar [!DNL Segment Match] verfrist looppas wekelijks, kan het gematchte publiek aan de ontvangerskant op het recentste lidmaatschap niet wijzen. Lijn evaluatie uit en deel vernieuwt kadingen.

### Aanbevolen procedures

- Stel een formele overeenkomst voor het delen van gegevens in tussen organisaties voordat u [!DNL Segment Match] configureert. Dit moet betrekking hebben op toegestane gebruiksgevallen, vereisten inzake gegevensbeheer, toestemmingsverplichtingen en beëindigingsprocedures.
- Gebruik overlap schattingen als validatieprogramma vóór elke grote campagne — voer een schatting uit voordat u toezegt dat het overeenkomende publiek aan de minimale grootte- en kwaliteitsdrempels voldoet.
- Pas beschrijvende naamgevingsconventies toe op gedeelde segmenten die de partnernaam, het gebruiksgeval en de datum bevatten (bijvoorbeeld &quot;PartnerX_HighValue_Suppression_2026Q1&quot;) om duidelijkheid in alle organisaties te behouden.
- De gelijke tarieven van de monitor in tijd. Het dalende gelijke tarieven kunnen op de verslechtering van de identiteitsdekking, de kwesties van de gegevenskwaliteit, of veranderingen in het klantenbestand van de partner wijzen.
- Segmenteer het publiek van de bron om profielen uit te sluiten zonder overeenkomende naamruimte bevolkt. Dit verbetert de percentages van het gelijkenis en verstrekt nauwkeurigere overlappende ramingen.
- Voor bidirectionele het delen partnerschappen, wijs duidelijke eigendom van segmentonderhoud en verfrist programma&#39;s aan om verwarring te vermijden over welke organisatie voor updates verantwoordelijk is.

### Handelsbesluiten

>[!NOTE]
>
>**handel-off: Het tarief van de gelijke vs. privacycontrole**
>
>Het gebruiken van meer identiteitsnamespaces (gehakt e-mail, gehakte telefoon, apparaat IDs) voor de gelijke tarieven van verhogingen aanpassen maar breidt het oppervlakte voor potentiële re-identificatie uit. Het gebruik van minder naamruimten (alleen gehakte e-mail) biedt een betere bescherming van de privacy, maar kan de overeenkomende publieksgrootte verminderen.
>
>- **Veelvoudige namespaces gunnen:** Hogere gelijke tarieven, groter aangepast publiek, waardevoller voor campagne gericht
>- **Enige namespace gunt:** Betere privacy houding, eenvoudiger beheer overzicht, lager nalevingsrisico
>- **Aanbeveling:** Begin met één enkele namespace (gehakt e-mail is het gemeenschappelijkst) en voeg extra namespaces slechts toe als de gelijke tarieven voor het gebruiksgeval ontoereikend zijn. Documenteer de privacyeffectbeoordeling voor elke toegevoegde naamruimte.

>[!NOTE]
>
>**handel-off: granularity van het segment tegenover operationele eenvoud**
>
>Het delen van vele korrelige, hoogst gerichte segmenten met een partner verstrekt meer flexibiliteit voor campagne het richten maar verhoogt operationele ingewikkeldheid voor zowel afzender als ontvanger. Het delen van minder, bredere segmenten vereenvoudigt beheer maar vermindert het richten precisie.
>
>- **Korrelige segmenten verkiezen:** het nauwkeurige richten, onderscheiden campagnes, hogere relevantie
>- **Brede segmenten begunstigen:** Eenvoudiger beheer, minder te controleren aandelen, lagere operationele overheadkosten
>- **Aanbeveling:** Begin met een klein aantal high-value segmenten (2-5) voor een nieuw partnerschap. Meer granulariteit als het partnerschap rijpt en operationele processen worden ingesteld. Gebruik naamconventies en documentatie om complexiteit te beheren wanneer het aantal segmenten toeneemt.

>[!NOTE]
>
>**handel-off: Vernieuwt frequentie vs. verwerkingskosten**
>
>Als u het gedeelde publiek vaker vernieuwt, blijft het overeenkomende publiek op de juiste hoogte, maar neemt de verwerkingsbelasting toe en neemt de capaciteit van de licentie wellicht toe. Minder vaak vernieuwen leidt tot lagere kosten, maar zorgt ervoor dat het overeenkomende publiek stabiel wordt.
>
>- **verfrist zich vaak voor:** Huidig publiekslidmaatschap, hogere campagnerelevantie, betere suppressiecapaciteit
>- **verfrist zich vaak voor:** Lagere verwerkingskosten, eenvoudiger controle, verminderd vergunningsverbruik
>- **Aanbeveling:** verfrist zich dagelijks is aangewezen voor de meeste productiesamenwerking. Voor tijdsgevoelige gebruiksgevallen (bijvoorbeeld verkoop op flitsniveau, op gebeurtenissen gebaseerde campagnes) kunt u herevaluatie op aanvraag en delen overwegen vlak voordat de campagne wordt gestart.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie over de mogelijkheden die in dit gebruikspatroon worden gebruikt.

### [!DNL Segment Match]

- [Overzicht van afstemming van segment](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/overview)
- [Problemen met segmentovereenkomst oplossen](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-match/troubleshooting)

### Segmentering en publiek

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Overzicht van Audience Composition](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/audience-composition)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)

### Identiteit en profiel

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van naamruimten](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- [Overzicht van het realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)

### Beheer van gegevens en toestemming

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Overzicht van labels voor gegevensgebruik](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Beleidshandhaving](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/enforcement/overview)
- [Toestemming en voorkeuren](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Toestemming en voorkeuren, veldgroep](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)

### Doelen en activering

- [Overzicht van doelen](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/home)
- [Doelcatalogus](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/overview)
- [Dataflows voor doelen controleren](https://experienceleague.adobe.com/en/docs/experience-platform/dataflows/ui/monitor-destinations)

### Gegevensmodellen en -schema

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Beheer en toegangscontrole

- [Overzicht van toegangsbeheer](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home)
- [Overzicht van sandboxen](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home)

### Controle en waarneming

- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Overzicht van observatiegegevens](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Beveiligingsmechanismen

- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Segmenteringsgeleiding](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/guardrails)
- [Activeringsinstructies](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/guardrails)

### Tutorials

- [Een schema maken](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/tutorials/union-schema)
- [Een gegevensset voor profiel inschakelen](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/enable-for-profile)
