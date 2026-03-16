---
title: Bekende bezoeker Web/App Personalization
description: Leer hoe u persoonlijke inhoud, aanbiedingen of promoties aan bepaalde bezoekers kunt leveren op basis van realtime profiel en segmentlidmaatschap.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7957'
ht-degree: 0%

---


# Bekende gebruikerspubliek voor web/apps

Dit referentieplan bevat een volledige implementatiegids voor het leveren van gepersonaliseerde inhoud aan geïdentificeerde bezoekers op digitale oppervlakken met [!DNL Adobe Journey Optimizer] (AJO) en [!DNL Adobe Real-Time Customer Data Platform] (RT-CDP). Het wordt ontworpen voor oplossingsarchitecten, marketing technologen, en implementatietechnici die alle levensvatbare implementatiemethodes, de besluiten moeten begrijpen die in elke fase, en de documentatie van Experience League moeten worden genomen die configuratie steunt.

Verpersoonlijking voor bekende bezoekers op het web en in apps is het primaire verpersoonlijkingspatroon voor geverifieerde digitale ervaringen. In tegenstelling tot anonieme personalisatie van de bezoeker, die uitsluitend op het gedragssignalen van de in-zittingstijd steunt, gebruikt dit patroon het volledige verenigde profiel: historische gedragsgegevens, segmentlidmaatschap, loyaliteitsrij, koopgeschiedenis, levenscyclusstadium, gegevens verwerkte attributen, en aandrijvingsscores. Deze functie ondersteunt personalisatie op verschillende webpagina&#39;s (via het AJO-webkanaal), mobiele in-app-berichten en inhoudskaarten.

In deze handleiding worden alle uitvoerbare implementatieopties (segmentgebaseerd, op beslissingen gebaseerd en meerdere oppervlakken) gepresenteerd, met afwegingen, beslissingsrichtlijnen en verwijzingen naar [!DNL Adobe Experience League] -documentatie.

## Hoofdlettergebruik

Organisaties met geverifieerde digitale eigenschappen — e-commercesites, bancaire portals, abonnementendiensten, loyaliteitsprogramma&#39;s, mobiele apps — moeten persoonlijke ervaringen bieden die de relatie van elke klant met het merk weerspiegelen. Wanneer een bezoeker zich aanmeldt of wordt herkend via identiteitsresolutie, heeft het platform toegang tot zijn volledige, uniforme profiel en levert het inhoud die is afgestemd op zijn specifieke kenmerken, gedrag en voorkeuren.

Dit patroon is bedoeld voor het scenario waarin een geïdentificeerde bezoeker op een webeigenschap aankomt of een mobiele app opent. Het systeem moet de optimale inhoud, aanbieding of promotie bepalen op basis van realtime profielgegevens en het lidmaatschap van het publiek. Het verpersoonlijkingsbesluit gebeurt bij de rand in milliseconden, toelatend sub-second inhoudslevering zonder merkbare latentie.

Het patroon ondersteunt zowel deterministische personalisatie (waarbij specifieke inhoud wordt toegewezen aan specifieke publiekssegmenten) als dynamische besluitvorming (waarbij AJO-besluit geschiktheidsregels evalueert en rangschikkingsstrategieën om de optimale inhoud per profiel te selecteren). Het beslaat meerdere digitale oppervlakken — webpagina&#39;s, mobiele in-app berichten en inhoudskaarten — en maakt een consistente personalisatie mogelijk op de digitale reis van de klant.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gericht door dit gebruikspatroon.

### Lever persoonlijke klantenervaringen

Inhoud, aanbiedingen en berichten voor individuele voorkeuren, gedrag en levenscyclusfase aanpassen. Voor meer informatie, zie [ gepersonaliseerde klantenervaringen leveren ](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md).

| KPI | Beschrijving |
| --- | --- |
| Betrokkenheid | Interactiefrequentie en -diepte met gepersonaliseerde inhoud op digitale oppervlakken |
| Omrekeningskoers | Percentage bezoekers dat de gewenste acties uitvoert na ontvangst van gepersonaliseerde inhoud |
| Klanttevredenheid (CSAT) | Verbetering van de algemene tevredenheid dankzij relevante, gepersonaliseerde digitale ervaringen |

### De betrokkenheid van websites vergroten

Verbeter de tijd op de site, de pagina&#39;s per sessie en de interactie met webinhoud via relevante ervaringen. Voor meer informatie, zie [ de websiteovereenkomst van de Verhoging ](../../business-objectives/acquisition-growth/increase-website-engagement.md).

| KPI | Beschrijving |
| --- | --- |
| Tijd op (webpagina) | Verhoogde wachttijd in gepersonaliseerde inhoudsgebieden |
| Betrokkenheid | Interactietarieven met gepersonaliseerde elementen (kliks, rollen, interactie) |
| Omrekeningskoers | Verbeterde omzetting van persoonlijke inhoud in standaardinhoud |

### De betrokkenheid van mobiele apps vergroten

Het dagelijkse actieve gebruik, de eigenschapgoedkeuring, en in-app omzettingen door persoonlijke in-app ervaringen drijven.

| KPI | Beschrijving |
| --- | --- |
| Betrokkenheid | Interactiesnelheden in apps met persoonlijke berichten en inhoudskaarten |
| Bewaren | Verbeterde toepassingsretentie dankzij persoonlijke ervaringen |
| Omrekeningskoers | Verbeteringen in de conversie in de app van persoonlijke aanbiedingen en aanbevelingen |

## Voorbeelden van tactische gebruiksgevallen

Hieronder vindt u algemene tactische implementaties van dit patroon:

- De hoofdpersonalisering van de homepage door loyaliteitsrij of levenscyclusstadium — toon verschillende heldenbanners die op worden gebaseerd of de klant nieuw, actief, bij risico, of VIP is
- Productaanbeveling carrousel op basis van de aankoopgeschiedenis — oppervlakterelevante productsuggesties op basis van eerdere aankoopgegevens en productaffiniteitsscores
- Persoonlijke promotionele banner per klantensegment — toon verschillende promoties aan hoog-waarde, bij-risico, en nieuwe klantensegmenten
- Bericht in de app voor mobiele gebruikers op basis van functietoepassing — gebruikers helpen met onvoldoende gebruikte functies op basis van hun gebruikspatronen
- Inhoudskaart met persoonlijke aanbieding op het dashboard van de account — permanente, niet-toegestane aanbiedingen die zijn afgestemd op het profiel van de klant
- Gepersonaliseerde prijsstelling of disconteringsvertoning die op klantenrij wordt gebaseerd — toon laag-specifieke tarifering of exclusieve kortingen aan loyaliteitsprogrammaleden
- Widget voor aanbevelingen voor grensoverschrijdende verkoop op basis van eigen producten — suggereren aanvullende producten of services op basis van de huidige portfolio
- Persoonlijke navigatie of inhoudsvolgorde op basis van interesses — inhoudmodules of navigatie-elementen opnieuw ordenen op basis van aangetoonde voorkeuren

## Kernprestatie-indicatoren

De volgende KPIs helpen de doeltreffendheid van dit gebruiks gevalpatroon meten.

| KPI | Meetmethode | Benchmarkleidraad |
| --- | --- | --- |
| Personalization Engagement Rate | Klikt en interactie met gepersonaliseerde inhoudselementen die door beelden worden verdeeld | Persoonlijke inhoud moet de standaardinhoud overtreffen met 20-50% |
| Optillen conversiesnelheid | Conversiesnelheid voor persoonlijke ervaringen versus controle-/standaardervaringen | Doel: 10-30% lichter maken boven niet-persoonlijke ervaringen |
| Doorkliksnelheid (CTR) | Klikt op gepersonaliseerde CTA&#39;s, aanbiedingen, en aanbevelingen die door beelden worden verdeeld | Monitor per oppervlak (web, in-app, inhoudskaart) en per segment |
| Ontvangsten per bezoek | Ontvangsten die worden toegerekend aan sessies met persoonlijke ervaringen | Vergelijk persoonlijke en niet-persoonlijke bezoekerscohorten |
| Interactiesnelheid inhoudskaart | Klikken en verwijderen van inhouds-kaart in verhouding tot indrukken | Bijhouden per kaarttype en publiekssegment |
| Betrokkenheid voor berichten in de app | Interacties tussen berichten in de app (CTA klikt, ontslagen) met betrekking tot afbeeldingen | Vergelijk over publiekssegmenten en berichttypes |
| Tijd op pagina | Gemiddelde tijd besteed aan pagina&#39;s met gepersonaliseerde inhoud versus gebrek | De gepersonaliseerde pagina&#39;s zouden verhoogde storttijd moeten tonen |
| Aanbiedingsacceptatie | Percentage van geselecteerde aanbiedingen met beslissingsbevoegdheid die resulteren in een conversiegebeurtenis | Track per aanbieding, per plaatsing en per waarderingsstrategie |

## Hoofdletterpatroon gebruiken

In deze sectie worden het kernpatroon en de functieketen beschreven.

**Bekende-bezoeker Web/app verpersoonlijking**

Lever gepersonaliseerde inhoud, aanbiedingen of promoties aan een geïdentificeerde bezoeker op basis van realtime profiel en segmentlidmaatschap op het web, mobiele in-app en op de oppervlakken van de inhoudskaart.

**Keten van de Functie:** de Evaluatie van het publiek > Personalization Beslissing > Oppervlak/de Configuratie van het Kanaal > Inhoudslevering > het Volgen van de Indrukking > het Melden

## Applicaties

In dit gebruikspatroon worden de volgende toepassingen gebruikt.

- **[!DNL Adobe Journey Optimizer](AJO)** — de kanaalconfiguratie van het Web, in-app kanaalconfiguratie, de configuratie van het inhoudskaartkanaal, besluit (de selectie van de aanbieding en rangschikking), bericht creatie (gepersonaliseerde inhoudsverwezenlijking), campagneuitvoering, inhoud experimenteren, en het melden
- **[!DNL Adobe Real-Time Customer Data Platform](rt-CDP)** — de evaluatie van het publiek (rand, het stromen, en partij), de raadpleging van het profiel in real time via Edge Network, profielverrijking met gegevens verwerkte attributen en aandrijvingsscores
- **[!DNL Adobe Experience Platform](AEP)** — De opslag van het profiel, de identiteitsdienst, Web SDK, Mobiele SDK, gegevensstroomconfiguratie, de levering van het randnetwerk

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary Function | Status | Wat moet er gebeuren? | Experience League Reference |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | AJO-sandbox met webkanaal-, in-app-kanaal- en beslissingsbevoegdheden geconfigureerd. Gebruikers die waren voorzien van rollen voor markeertekens en auteur van inhoud. | [ het overzicht van Sandboxen ](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [ overzicht van de Toegangscontrole ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | Profielschema moet kenmerken bevatten die worden gebruikt voor personalisatie en segmentatie (bijvoorbeeld een loyaliteitsniveau, aankoopgeschiedenis, productbelangen, levenscyclusfase). Ervaar gebeurtenisschema voor web-/app-interactie bijhouden en conversiegebeurtenissen. Datasets ingeschakeld voor [!DNL Real-Time Customer Profile] . | [ XDM het overzicht van het Systeem ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [ de samenstellingsgrondbeginselen van het Schema ](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Gegevensbronnen en -verzameling | Vereist | Web SDK is geïmplementeerd op het web voor het bijhouden van ervaringen en het weergeven van de indruk. Mobile SDK is geïmplementeerd op mobiele apps voor levering in de app en op de inhoudskaart. DataStream die met de dienst van AJO wordt gevormd die voor randverpersoonlijking wordt toegelaten. Profielgegevens in realtime beschikbaar aan de rand voor subtweede personalisatie. | {het overzicht van SDK van het 0} Web ](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [ Mobiel overzicht van SDK ](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview), [ vorm gegevensstromen ](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)[ |
| Identiteit en profielconfiguratie | Vereist | Bekende naamruimten (CRM-id, e-mail, geverifieerde gebruikersnaam) geconfigureerd. Identiteitsvervlechting tussen anonieme en voor authentiek verklaarde zittingen operationeel voor naadloze overgang van anonieme aan bekende-bezoekersverpersoonlijking. Edge-samenvoegbeleid geconfigureerd met `isActiveOnEdge: true` om het geverifieerde profiel aan de rand op te lossen. | [ overzicht van de Dienst van de Identiteit ](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [ overzicht van het beleid van de Fusie ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Auditiedefinitie en segmentatie | Vereist | Soorten publiek gedefinieerd met profielkenmerken, gedragsgegevens en berekende kenmerken. Edge- of streamingevaluatie ingeschakeld voor realtime personalisatievalificatie. Het publiek dat voor op segment-gebaseerde verpersoonlijking wordt gebruikt moet voor randevaluatie in aanmerking komen. | [ overzicht van de Dienst van de Segmentatie ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [ segmentatie van Edge ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League Reference |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Berekende kenmerken (bijvoorbeeld [!DNL Customer AI] eigenschapscores, levenslange waarde, betrokkenheidsscore, productaffiniteit, dagen sinds de laatste aankoop) verbeteren de kwaliteit van de personalisatie aanzienlijk door rijkere signalen te bieden voor de definitie van het publiek en de selectie van inhoud. | ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview), [ overzicht van de Klant AI van 0} Berekende attributen ](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)[ |
| Levenscyclusbeheer van gegevens | Aanbevolen | Het beleid voor het bewaren van profiel- en gebeurtenisgegevens zorgt voor nieuwe, relevante personalisatiebeslissingen met betrekking tot gegevensbevoegdheden. Met deze controle wordt ervoor gezorgd dat de personalisatie de gebruikersvoorkeuren respecteert. | [ het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens ](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [ Toestemming in Journey Optimizer ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | De etiketten van het bestuur op profielattributen die voor verpersoonlijking worden gebruikt (vooral PII-aangrenzende attributen zoals aankoopgeschiedenis, plaats, financiële gegevens) verzekeren naleving van het beleid van het gegevensgebruik. | [ het beheer van Gegevens overzicht ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [ overzicht van de gebruiksetiketten van Gegevens ](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Bewaking en waarneming | Aanbevolen | Dankzij de bewaking van de leverings- en personalisatieprestaties van Edge kunnen latentieproblemen, leveringsfouten of problemen met gegevensversheid worden opgespoord die de persoonlijke ervaring verslechteren. | [ overzicht van de Inzichten van de Waarneming ](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home), [ het overzicht van Alarm ](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview) |
| Rapportage en analyse | Opgenomen | Personalization-prestatierapportering maakt deel uit van de functie Chain Step 6. [!DNL Customer Journey Analytics] de analyse maakt een diepgaand onderzoek mogelijk naar de invloed van personalisatie op de conversie, betrokkenheid en omzet in verschillende bezoekerssegmenten. | [ overzicht van CJA ](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [ AJO + de integratiegids van CJA ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer] (AJO)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Kanaalconfiguratie | Oppervlak- en kanaalconfiguratie | Webpagina&#39;s, in-app en inhoudskaartkanaaloppervlakken configureren voor levering van een persoonlijke weergave |
| Berichtontwerp | Inhoud ontwerpen | Maak gepersonaliseerde inhoudvarianten met dynamische inhoud, verpersoonlijkingsuitdrukkingen, en voorwaardelijke blokken voor elk oppervlak |
| Campagne uitvoeren | Campagne instellen en activeren | Webcampagnes maken en activeren (gepland of API-geactiveerd) die een publiek, oppervlak en inhoud binden |
| Besluitvorming | Instellingen voor beslissing (Option B/C) | Configureer beleidsregels voor beslissingen met geschiktheidsregels, classificatiestrategieën en bied/inhoud-items aan voor dynamische personalisatie |
| Inhoud experimenteren | Optimalisatie (optioneel) | A/B-tests uitvoeren op varianten van gepersonaliseerde inhoud om de prestaties te optimaliseren |
| Frequentie en bedrijfsregels | Campagne instellen en activeren | Afschermfrequentiecappen afdwingen om oververpersoonlijkingsvermoeidheid te voorkomen |
| Rapportage en prestatieanalyse | Rapportage en optimalisatie | De levering van de verpersoonlijking van de monitor, overeenkomst en omzettingsmetriek per oppervlakte en segment |

### [!DNL Real-Time CDP] (RT-CDP)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Definitie en evaluatie door het publiek | Bepaal en evalueer publiek gebruikend profielattributen, gedragsgegevens, en gegevens verwerkte attributen met rand of het stromen evaluatie |
| Real-time profiel opzoeken | Inhoud leveren (runtime) | Toegang tot profielkenmerken in real time en segmentlidmaatschap via Edge Network voor beslissingen voor subtweede personalisatie |
| Profielverrijking | Preimplementatie (ondersteuning) | Verrijk profielen met berekende kenmerken, [!DNL Customer AI] scores en samengevoegde gedragssignalen die de verpersoonlijkingskwaliteit verbeteren |

## Vereisten

Zorg ervoor dat het volgende is geïnstalleerd voordat u dit gebruikspatroon implementeert:

- [ ] Web SDK geïmplementeerd op doelwegeigenschappen met `alloy("sendEvent")` geconfigureerd voor paginaweergaven en interactietracering
- [ ] Mobile SDK geïmplementeerd op mobiele apps voor doelapparaten (als oppervlakken van in-app- of inhoudskaarten worden gebruikt)
- [ ] DataStream geconfigureerd met [!DNL Adobe Journey Optimizer] -service ingeschakeld
- [ ] Profielschema bevat kenmerken die worden gebruikt voor personalisatie (loyaliteitslaag, aankoopgeschiedenis, productbelangen, levenscyclusfase)
- [ ] Experience Event-schema geconfigureerd voor het bijhouden van de indruk en conversie
- [ ] Bekende naamruimten gemaakt en identiteitsstitching operationeel tussen anonieme (ECID) en geverifieerde identiteiten
- [ ] Edge-samenvoegbeleid geconfigureerd met `isActiveOnEdge: true`
- [ ] Soorten publiek gedefinieerd met evaluatie die geschikt is voor randapparaten voor realtime personalisatie
- [ ] Inhoud-elementen (afbeeldingen, kopieën, CTA&#39;s) voorbereid voor elke personaliseringsvariant
- [ ] Personalization-strategie gedocumenteerd: welke kenmerken hebben betrekking op het station van de inhoud, waarvoor oppervlakken

## Implementatieopties

In deze sectie worden de beschikbare implementatiemethoden voor dit gebruikspatroon beschreven.

### Optie A: Webpersonalisatie op basis van segmenten

**Best voor:** Deterministische verpersoonlijking waar de specifieke inhoudsvarianten rechtstreeks aan publiekssegmenten in kaart brengen — loyalty tier-specifieke heldenbanners, het overseinen van het levenscyclusstadium, de promotionele inhoud van het klantensegment. Ideaal als de toewijzing van inhoud naar segment goed is gedefinieerd en geen dynamische classificatie of optimalisatie vereist.

**hoe het werkt:**

Op segmenten gebaseerde personalisatie wijst inhoudsvarianten rechtstreeks toe aan publiekssegmenten. Wanneer het profiel van een bekende bezoeker wordt geëvalueerd op basis van publiek dat geschikt is voor randapparaten bij het laden van een pagina, bepaalt het systeem tot welke segmenten de bezoeker behoort en geeft het de overeenkomstige inhoudvariant weer. De selectie is gebaseerd op de prioriteit van het segmentlidmaatschap — als een bezoeker voor veelvoudige segmenten kwalificeert, wordt de inhoud van het hoogst-prioritaire segment getoond.

Deze benadering gebruikt AJO-webkanaalcampagnes (of in-app/content card campagnes) met voorwaardelijke inhoudsregels of meerdere configuraties die zich richten op de behandeling. Elk publiekssegment is gekoppeld aan een specifieke ervaring met inhoud. Er is geen beslissingsengine betrokken — de logica voor de inhoudselectie is volledig gesegmenteerd.

Inhoud wordt gemaakt met de AJO-interface voor het schrijven van berichten met dynamische inhoudblokken die verschillende inhoud weergeven op basis van het lidmaatschap van het publiek of profielkenmerken. De SDK of Mobile SDK van het Web levert de gepersonaliseerde ervaring in echt - tijd via Edge Network.

**Zeer belangrijke overwegingen:**

- De inhoudvarianten moeten voor elk segment vooraf worden ontworpen
- Segmentdefinities moeten in aanmerking komen voor realtime-kwalificatie
- Voor het toevoegen van nieuwe segmenten of inhoudsvarianten moet de campagneconfiguratie worden bijgewerkt
- De selectie van de inhoud is deterministisch — hetzelfde segment ziet altijd dezelfde inhoud

**Voordelen:**

- Eenvoudig te implementeren en te onderhouden met duidelijke toewijzing van inhoud naar segment
- Eenvoudig te begrijpen en de logica voor personalisatie uit te leggen aan belanghebbenden
- Geen beslissingsoverhead — snellere resolutie van inhoud
- Volledige controle over de inhoud die elk segment ontvangt

**Beperkingen:**

- Beperkte flexibiliteit wanneer het aantal segmenten en inhoudvarianten toeneemt
- Kan de selectie van inhoud niet dynamisch optimaliseren op basis van signalen op profielniveau buiten het segmentlidmaatschap
- Voor het toevoegen van nieuwe inhoudvarianten zijn handmatige campagneupdates vereist
- Biedt geen ondersteuning voor scenario&#39;s met de volgende beste aanbieding waarbij meerdere aanbiedingen met dezelfde plaatsing concurreren

**Experience League:**

- [Aan de slag met webkanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Webervaringen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)

### Optie B: personalisatie op basis van beslissingen

**Best voor:** Dynamische verpersoonlijking waar de optimale inhoud of de aanbieding per profiel moeten worden geselecteerd gebruikend toelatingsregels en rangschikkingsstrategieën - volgende-best-aanbieding op homepage, gepersonaliseerde productaanbevelingen, dynamische bevorderende bannerselectie. Ideaal wanneer meerdere aanbiedingen of content-items met elkaar concurreren voor dezelfde plaatsing en het systeem de beste moet kiezen.

**hoe het werkt:**

Bij een op beslissingen gebaseerde personalisatie wordt AJO-beslissing gebruikt om het profiel van elke bezoeker te evalueren aan de hand van een catalogus met inhoudsitems of -aanbiedingen. Hierbij worden de geschiktheidsregels toegepast om te bepalen welke items in aanmerking komen en wordt vervolgens een rangschikkingsstrategie (op basis van prioriteit, op basis van formule of op basis van AI) toegepast om het optimale item voor elke plaatsing te selecteren.

De implementatie omvat het maken van plaatsingen (waar inhoud wordt weergegeven), het definiëren van aanbiedingen met geschiktheidsregels en representaties van inhoud, het organiseren van aanbiedingen in verzamelingen en het maken van besluitvormingsbeleid dat plaatsingen aan verzamelingen bindt met classificatiestrategieën. Wanneer een bezoeker tijdens runtime een pagina laadt, evalueert de Edge Network het beslissingsbeleid op basis van het profiel van de bezoeker en retourneert de geselecteerde aanbiedingsinhoud.

Deze benadering steunt geavanceerde verpersoonlijkingsscenario&#39;s met inbegrip van volgende-best-aanbieding, gepersonaliseerde bevorderingen met het maximum, en AI-geoptimaliseerde inhoudselectie. Aanbiedingen kunnen per profiel en globale begrenzingen, geldigheidsterdatumbereiken, en complexe geschiktheidscriteria hebben die profielattributen en publiekslidmaatschap combineren.

**Zeer belangrijke overwegingen:**

- Vereist meer configuratie vooraf (plaatsing, aanbiedingen, toelatingsregels, inzamelingen, besluiten)
- De rangschikkende strategieën kunnen op prioriteit-gebaseerd (hand) zijn, op formule-gebaseerd (douaneuitdrukking), of AI-gerangschikt (auto-optimalisering)
- Voor een modeltraining is minstens 1000 conversiegebeurtenissen vereist voor AI-classificatie
- Aanbiedings het begrenzen tellers kunnen een lichte vertraging onder hoge productiescenario&#39;s hebben
- Een reserveaanbod moet worden gevormd voor gevallen waar geen gepersonaliseerd aanbod kwalificeert

**Voordelen:**

- Dynamische selectie van inhoud per profiel zonder hardwarematige segmenttoewijzing aan inhoudstoewijzing
- Ondersteunt complexe toelatingscriteria en rangschikkingslogica
- Met de optie AI-gerangschikt schakelt u automatische optimalisatie in zonder handmatig ingrijpen
- Door aanbiedingen te beperken voorkomt u dat bepaalde inhoud overbelicht wordt
- Gecentraliseerd aanbiedingsbeheer — aanbiedingen kunnen via campagnes en kanalen worden hergebruikt

**Beperkingen:**

- Hogere implementatiecomplexiteit dan op segment gebaseerde personalisatie
- AI-classificatie vereist voldoende conversievolume voor training
- De besnoeiingsevaluatie voegt marginale latentie in vergelijking met directe op segment-gebaseerde inhoudslevering toe
- Op basis van formule bepalen vereist zorgvuldig ontwerp om onbedoelde prioritering te voorkomen

**Experience League:**

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Optie C: Verpersoonlijking op meerdere oppervlakken (web + in-app + inhoudskaart)

**Best voor:** Consistente verpersoonlijking over veelvoudige digitale oppervlakten — leverend gecoördineerde gepersonaliseerde ervaringen op Web-pagina&#39;s, mobiele in-app berichten, en inhoudskaarten. Ideaal wanneer de organisatie zowel web- als mobiele toepassingseigenschappen heeft en uniforme logica voor personalisatie voor alle digitale aanraakpunten wil.

**hoe het werkt:**

De verpersoonlijking van meerdere oppervlakken breidt of Optie A (op segment-gebaseerd) of Optie B (op besluit-gebaseerd) uit om gepersonaliseerde inhoud over veelvoudige oppervlaktypes van AJO te leveren. Elk type oppervlak (web, in-app, inhoudskaart) kan verschillende indelingen en leveringsmechanismen hebben, maar de onderliggende logica voor personalisatie (lidmaatschap van het publiek of besluitvorming) wordt gedeeld.

De implementatie omvat het configureren van kanaaloppervlakken voor elk type oppervlak, het ontwerpen van oppervlaktespecifieke inhoud (web HTML/CSS voor weboten, gestructureerde berichten voor in-app, kaartlay-outs voor inhoudskaarten) en het maken van campagnes die gericht zijn op het juiste oppervlak. Het Web SDK verzorgt de aflevering van het web, terwijl de Mobile SDK de aflevering van in-app- en inhoudskaarten afhandelt.

Inhoudskaarten zijn vooral handig voor permanente, niet-toegestane persoonlijke berichten op dashboards of startschermen van apps. In-app berichten zijn ideaal voor contextuele, zittingsspecifieke mededelingen. De verpersoonlijking van het Web behandelt heldenbanners, aanbeveling widgets, en promotionele inhoud.

**Zeer belangrijke overwegingen:**

- Elk oppervlaktetype vereist zijn eigen configuratie van het kanaaloppervlak en inhoudsontwerp
- Web SDK en Mobile SDK moeten beide worden geïmplementeerd en geconfigureerd
- De inhoud moet voor elk oppervlakteformaat (verschillende afmetingen, lay-outs, interactiepatronen) worden ontworpen
- Gedeeld publiek en logica voor besluitvorming zorgen voor consistentie tussen oppervlakken
- De tests moeten alle typen oppervlakken van de verschillende apparaten bestrijken

**Voordelen:**

- Consistente personaliseringservaring voor alle digitale aanraakpunten
- Gedeeld publiek en logica voor besluitvorming reduceren duplicatie
- Inhoudskaarten bieden een permanent, niet-indringend personalisatieoppervlak
- In-app-berichten maken contextuele, sessiespecifieke personalisatie op mobiele apparaten mogelijk

**Beperkingen:**

- Hoogste complexiteit bij implementatie — vereist configuratie voor elk type oppervlak
- Vereist SDK- en Mobile SDK-implementatie voor Web
- De inhoud moet voor elk oppervlakteformaat worden ontworpen en onderhouden
- Het bereik van de tests neemt toe met elk extra oppervlaktetype

**Experience League:**

- [Overzicht in-app kanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Kanaal van inhoudskaart](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Aan de slag met webkanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)

### Optievergelijking

In de volgende tabel worden de drie implementatieopties vergeleken.

| Criteria | Optie A: op segment gebaseerd | Optie B: op basis van beslissing | Optie C: Multi-Surface |
| --- | --- | --- | --- |
| Best voor | Bekende segment-aan-inhoud afbeelding | Dynamische selectie van inhoud per profiel | Consistente personalisatie voor internet en mobiele apparaten |
| Complexiteit | Laag | Medium-High | Hoog (bouwt voort op A of B) |
| Latentie | Snelst (directe segmentresolutie) | Iets hoger (beslissingsevaluatie) | Afhankelijk van onderliggende optie (A of B) |
| Flexibiliteit | Beperkt tot vooraf gedefinieerde segment-inhoudparen | Hoge — dynamische rangorde en geschiktheid | Hoogste — meerdere oppervlakken met gedeelde logica |
| Contentbeheer | Handmatige segmenttoewijzing aan inhoud | Gecentraliseerde aanbiedingenbibliotheek met toelatingsregels | Inhoud per oppervlak met gedeelde logica voor personalisatie |
| Optimalisatie | Handmatige A/B-tests | Automatisch optimaliseren volgens AI-classificatie beschikbaar | Optimalisatie per oppervlak |
| Vereisten | Voor Edge in aanmerking komend publiek, Web SDK | Plaatsingen, aanbiedingen, subsidiabiliteitsregels, besluiten | Web SDK + Mobile SDK, configuraties met meerdere oppervlakken |
| Ondersteunde oppervlakken | Web (primair) | Web (primair) | Web + In-app + inhoudskaart |

### Kies de juiste optie

Begin met deze vragen om de juiste implementatieaanpak te kiezen:

1. **hoeveel oppervlakten?** Kies Optie C (die voor de onderliggende logica op A of B voortbouwt) als u zowel op het web als op de mobiele app een personalisatie wilt uitvoeren. Kies in het geval van alleen het web een optie tussen A en B.

2. **hoe dynamisch is uw inhoudselectie?** Als u een duidelijk gedefinieerde toewijzing van segmenten aan inhoudsvarianten (bijvoorbeeld 3-5 loyaliteitslagen, elk met een specifieke hoofdbanner) hebt, kiest u Optie A. Kies Optie B als u een keuze wilt maken uit een catalogus met aanbiedingen met complexe geschiktheid en rangschikking.

3. **hebt u AI-geoptimaliseerde selectie nodig?** Als u wilt dat het systeem automatisch leert welke inhoud het beste voor elk profiel presteert, kiest u Optie B met een door AI gerangschikte beslissing.

4. **hoeveel inhoudsvarianten?** Als u minder dan 10 inhoudvarianten met duidelijke segmentafbeeldingen hebt, is Optie A eenvoudiger. Als u tientallen voorstellen hebt die geschiktheidsfilters en rangschikking vereisen, schalen Optie B beter.

5. **bent u van plan om tot andere kanalen uit te breiden?** Als uw besluitvormingslogica aanbiedingen over e-mail, Web, en andere kanalen uiteindelijk zou moeten dienen, verstrekt Optie B de gecentraliseerde beslissingsstichting die de beslissing van de dwars-kanaalaanbieding uitbreidt.

## Uitvoeringsfasen

Deze sectie doorloopt elke fase van de implementatie in detail.

### Fase 1: Doelgroepen definiëren en evaluatie configureren

**functie van de Toepassing:** rt-CDP: de Evaluatie van het publiek

**wat u zult vormen:** bepaal het publiek dat de selectie van de verpersoonlijkingsinhoud drijft. Deze doelgroepen vertegenwoordigen de bezoekerssegmenten die persoonlijke ervaringen krijgen: loyaliteitslagen, levenscyclusfasen, gedragscohorten of groepen met productaffiniteit.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: De evaluatiemethode van de Audience**
>
>Hoe snel moet het lidmaatschap van het publiek worden opgelost voor personalisatie? Dit is rechtstreeks van invloed op de vraag of personalisatie kan plaatsvinden bij het laden van de pagina of vertraging vereist.
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Edge-evaluatie | Real-time web-/app-personalisatie die subsecondenkwalificatie vereist | Beperkt tot eenvoudige profielcontroles en segmentlidmaatschap. Geen tijdreeksvragen of complexe aggregaties. Vereist voor bekende-bezoekersverpersoonlijking. |
>| Streaming evaluatie | Bijna real-time kwalificatie wanneer profielen een publiek bereiken of afsluiten op basis van gedragsgebeurtenissen | Ondersteunt query&#39;s voor één gebeurtenis en beperkte tijd voor venster. Wijzigingen in de doelgroep worden binnen enkele minuten weerspiegeld. Geschikt voor oppervlakken van in-app- en inhoudskaarten waar een kleine vertraging acceptabel is. |
>| Batchevaluatie | Dagelijkse publieksvernieuwingen voor segmenten op basis van complexe aggregaties of historische patronen | Ondersteuning voor de functie van een volledige segmentregel. Niet geschikt voor realtime personalisatie, maar kan randpubliek aanvullen met complexe vooraf berekende segmenten. |

>[!NOTE]
>**Besluit: De attributen van Personalization**
>
>Welke profielkenmerken moeten de definitie van het publiek en de selectie van inhoud bepalen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Profielkenmerken (loyaliteitsniveau, levenscyclusfase) | Deterministische verpersoonlijking die op bekende klanteneigenschappen wordt gebaseerd | Stabiele, duidelijk gedefinieerde kenmerken. Eenvoudig toe te wijzen aan inhoudsvarianten. Beschikbaar aan de rand als het profiel correct is geconfigureerd. |
>| Gedragssignalen (koopgeschiedenis, browserpatronen) | Personalization gebaseerd op recente gedragingen en betrokkenheidspatronen | Vereist berekende kenmerken of streaming segmenten. Dynamischer maar complexer om te onderhouden. |
>| Propensiteitsscores ([!DNL Customer AI]) | Voorspelende personalisatie op basis van waarschijnlijkheid om te zetten, te draaien of aan te schaffen | Vereist berekende kenmerken. Laat verfijnde verpersoonlijking toe maar vereist de modeltrainingsgegevens van ML. |
>| Gecombineerde aanpak | Meeste productieimplementaties | Gebruikt profielkenmerken voor primaire segmentatie met gedragssignalen en sterktenecores voor verfijning. |

**navigatie UI:** Klant > Soorten publiek > leidt tot publiek > bouwt regel

**Zeer belangrijke configuratiedetails:**

- Bepaal publiek gebruikend de Bouwer van het Segment met de uitdrukkingen van de segmentregel die profielattributen van verwijzingen voorzien
- Verzeker de uitdrukkingen van de segmentregel kwalificeren voor randevaluatie (eenvoudige attributencontroles, segmentlidmaatschap)
- Vorm rand-in aanmerking komend publiek voor de gebruiksgevallen van het verpersoonlijkingsgebruik in real time
- Overweeg het publiek onderdrukken om onlangs omgezette of uitgekozen bezoekers uit te sluiten

**documentatie van Experience League:**

- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Fase 2: Bepaling instellen (alleen optie B en C)

**functie van de Toepassing:** AJO: Beslissing

**wat u zult vormen:** Opstelling de besluitvormingsinfrastructuur die dynamisch de optimale inhoud of de aanbieding voor elke bezoeker selecteert. Dit omvat plaatsingen (waar aanbiedingen verschijnen), aanbiedingen (welke inhoud beschikbaar is), toelatingsregels (wie kwalificeert), rangschikkingsstrategieën (hoe te om het beste te kiezen), en besluitvormingsbeleid (hoe alles verbindt).

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: Het rangschikken strategie**
>
>Hoe moeten in aanmerking komende aanbiedingen gerangschikt worden om de beste voor elke bezoeker te selecteren?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Op prioriteit gebaseerd (handleiding) | Eenvoudig gebruik met duidelijke aanbiedingshiërarchie | Elke aanbieding heeft een handmatige prioritaire waarde. De hoogste prioriteit in aanmerking komende aanbieding wint. Gemakkelijk te begrijpen en te controleren. |
>| Op basis van formule (aangepaste expressie) | Houd bij de waardering rekening met profielkenmerken | Aangepaste rangschikkingsformules als referentieprofielgegevens (bijv. score op loyaliteitsniveau + recentie). Flexibel, maar vereist het ontwerpen en testen van formules. |
>| Op AI-schaal (automatische optimalisatie) | Als u wilt dat het systeem de selectie van aanbiedingen automatisch optimaliseert | Het model van ML leert welke aanbiedingen het beste presteren waarvoor profielen. Vereist minimaal 1.000 conversiegebeurtenissen voor training. Het beste voor hoge-verkeersstages. |

>[!NOTE]
>**Besluit: Het Aftappen van het aanbod**
>
>Moeten er beperkingen gelden voor het aantal keren dat een bezoeker of alle bezoekers een aanbieding ontvangen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Per profiel | Voorkomen dat vermoeidheid hetzelfde aanbod herhaaldelijk ziet | Hiermee beperkt u de indrukken per bezoeker gedurende een bepaalde periode. Zorgt voor variatie in de persoonlijke ervaring. |
>| Globale lampvoet | Totaal aantal indrukkingen beperken voor een aanbieding voor speciale acties of een aanbieding voor beperkte beschikbaarheid | Hiermee beperkt u de totale indrukken van alle bezoekers. Nuttig voor promoties van beperkte hoeveelheden. |
>| Geen uiteinde | Evergreen-inhoud of altijd relevante aanbiedingen | Geen impressiegrenzen. Geschikt voor permanente inhoud, zoals banners met een loyaliteitsniveau. |

**navigatie UI:** [!DNL Journey Optimizer] > Componenten > Beslissingsbeheer

**Zeer belangrijke configuratiedetails:**

- Plaatsen maken voor elk oppervlak waar aanbiedingen worden weergegeven (webbanner, berichtgebied in de app, sleuf voor inhoudskaart)
- Bepaal toelatingsregels gebruikend de uitdrukkingen van de segmentregel die profielattributen en publiekslidmaatschap van verwijzingen voorzien
- Aangepaste aanbiedingen maken met inhoudsrepresentaties voor elke plaatsing
- Een fallback-aanbieding maken die alle plaatsingen dekt (weergegeven wanneer geen gepersonaliseerde aanbieding in aanmerking komt)
- Aanbiedingen organiseren met verzamelingsaanduidingen (tags) en groeperen in verzamelingen
- Een beslissingsbeleid maken dat verzamelingen bindt met de geselecteerde rangschikkingsstrategie

**documentatie van Experience League:**

- [Plaatsingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Beslissingsregels maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Alternatieve aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Verzamelingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)

### Fase 3: oppervlakken en kanalen configureren

**functie van de Toepassing:** AJO: De Configuratie van het Kanaal

**wat u zult vormen:** vorm de kanaaloppervlakten die bepalen waar de gepersonaliseerde inhoud zal worden geleverd. Elk oppervlaktype (Web, in-app, inhoudskaart) vereist zijn eigen configuratie die de oppervlakte URI, inhoudsformaat, en leveringsparameters specificeert.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: De oppervlakken van het doel**
>
>Welke digitale oppervlakken krijgen gepersonaliseerde inhoud?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alleen webkanaal | Personalization concentreert zich op webeigenschappen | Vereist Web SDK. Eenvoudigste implementatie. Omvat hoofdbanners, promotiegebieden, aanbevelingen widgets. |
>| Alleen kanaal in app | Personalization richt zich op mobiele apps | Mobiele SDK vereist. Omvat contextuele, sessiespecifieke berichten in de app. |
>| Alleen inhoudskaartkanaal | Blijvende, niet-toelaatbare gepersonaliseerde berichten | Vereist Mobile SDK of Web SDK. Kaarten blijven bestaan tot ze worden ontslagen. Ideaal voor dashboards en thuisschermen. |
>| Meerdere oppervlakken (Option C) | Consistente personalisatie voor het web en mobiele apparaten | Vereist zowel Web SDK als Mobiele SDK. Voor elk oppervlak zijn afzonderlijke configuratie en inhoud nodig. |

>[!NOTE]
>**Besluit: De benadering van de oppervlakconfiguratie van het Web**
>
>Hoe zou de Weboppervlakte voor inhoudslevering moeten worden gevormd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Single-page application (SPA) | Moderne webtoepassingen met routering op de client | Gebruik `renderDecisions: true` in Web SDK `sendEvent` -aanroepen. Inhoud die automatisch wordt gerenderd door de SDK. |
>| Multi-page application (MPA) | Traditionele webpagina&#39;s die door de server worden gerenderd | Inhoud die wordt geleverd bij het laden van de pagina via Edge Network-reactie. Mogelijk hebt u de URI-configuratie op paginaniveau nodig. |

**navigatie UI:** [!DNL Journey Optimizer] > Beleid > Kanalen > de oppervlakten van het Kanaal

**Zeer belangrijke configuratiedetails:**

- Voor weboppervlakken: configureer de URI van het weboppervlak die overeenkomt met de doelpagina(&#39;s)
- Voor in-app-oppervlakken: configureer het oppervlak van de mobiele app met toepassings-id en type oppervlak
- Voor oppervlakken van inhoudskaarten: het oppervlak van de inhoudskaart configureren met toepassings-id of webcontext
- Zorg ervoor dat de datastream de AJO-service heeft ingeschakeld voor levering van randvervorming

**documentatie van Experience League:**

- [Aan de slag met webkanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Webkanaalconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)
- [Voorwaarden voor kanalen in de app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [Configuratie van inhoudskaart](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)

### Fase 4: Authorinhoud

**functie van de Toepassing:** AJO: De Authoring van het Bericht

**wat u zult vormen:** Auteur de gepersonaliseerde inhoudsvarianten voor elk oppervlakte en segment of aanbieding. Dit omvat het ontwerpen van de visuele lay-out, het toevoegen van verpersoonlijkingsuitdrukkingen die profielattributen van verwijzingen voorzien, het vormen van voorwaardelijke inhoudsblokken, en het creëren van herbruikbare inhoudsfragmenten.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: De benadering van de inhoud**
>
>Hoe zou de gepersonaliseerde inhoud voor dit gebruiksgeval moeten worden gestructureerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Voorwaardelijke inhoudsblokken | Verschillende inhoudssecties binnen dezelfde lay-out verschillen per publiek | Enkel inhoudselement met voorwaardelijke regels. Efficiënt voor kleine variaties (kop, CTA-tekst, afbeeldingswisseling). |
>| Verschillende inhoudvarianten per behandeling | Fundamenteel verschillende lay-outs of ontwerpen per publiek | Meerdere complete inhoudselementen. Flexibeler, maar meer om te onderhouden. Vereist voor het experimenteren met inhoud. |
>| Door decisioning aangedreven inhoud | Inhoud dynamisch geselecteerd uit een aanbiedingscatalogus | De inhoud wordt gedefinieerd in de aanbiedingsweergaven. Inhoudsbeheer is gecentraliseerd in de aanbiedingsbibliotheek. |

>[!NOTE]
>**Besluit: De diepte van Personalization**
>
>Hoeveel van de inhoud zou moeten worden gepersonaliseerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Aanpassing op oppervlakteniveau | Alleen bepaalde elementen zijn gepersonaliseerd (hoofdafbeelding, CTA, banner aanbieden) | Lagere complexiteit. Gerichte personalisatie op gebieden met veel impact. Meest voorkomende startpunt. |
>| Volledige personalisatie | De volledige pagina-indeling of de volgorde van de inhoud wordt aangepast | Hogere complexiteit. Vereist uitgebreide creatie van inhoud. Biedt de meest toegesneden ervaring. |
>| Token-vlakke verpersoonlijking | Inline personalisatie tokens (naam, laag, puntbalans) | Eenvoudigste vorm. Voegt profielkenmerkwaarden in anders statische inhoud in. |

**navigatie UI:** [!DNL Journey Optimizer] > Campagnes > tot Campagne leiden > geef inhoud uit

**waar de opties uiteenlopen:**

**voor Optie A (op segment-gebaseerd):**

- De inhoudvarianten van de auteur voor elk publiekssegment gebruikend de Webontwerper of de coderedacteur
- Dynamische inhoudsblokken gebruiken met voorwaarden die zijn gebaseerd op het lidmaatschap van het publiek
- Aanpassingsexpressies configureren die verwijzen naar profielkenmerken (bijvoorbeeld `{{profile.person.name.firstName}}`, `{{profile.loyalty.tier}}` )
- Voorwaardelijke regels instellen om verschillende inhoud weer te geven die is gebaseerd op segmentlidmaatschap

**voor Optie B (op besluit-gebaseerd):**

- De auteur biedt inhoudrepresentaties aan voor elke plaatsing die in Fase 2 is gedefinieerd
- Elke aanbieding heeft een of meer representaties (HTML, image, JSON) die overeenkomen met plaatsingen
- De beslissingsuitvoer integreren in de webpagina of de app door beslissingstips in te sluiten
- De inhoud wordt tijdens runtime dynamisch geselecteerd. Het ontwerpen richt zich op afzonderlijke aanbiedingsitems

**voor Optie C (multi-oppervlak):**

- oppervlaktespecifieke inhoud van de auteur voor elk doeloppervlak (web HTML/CSS, bericht met structuur in de app, lay-out inhoudskaart)
- Consistente personalisatielogica op verschillende oppervlakken behouden en tegelijk aanpassen aan de indelingsbeperkingen van elk oppervlak
- Rendering van inhoud testen op elk type oppervlak

**documentatie van Experience League:**

- [Webervaringen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Helpfuncties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)
- [In-app berichten maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Inhoudskaarten maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Fase 5: Campagnes instellen en activeren

**functie van de Toepassing:** AJO: De Uitvoering van de campagne

**wat u zult vormen:** creeer en activeer de campagne van AJO die het publiek, de oppervlakte, en de inhoud samen voor levering bindt. Voor Webverpersoonlijking, worden de campagnes typisch gevormd voor directe of aan de gang zijnde activering eerder dan eenmalige geplande verzendt.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: Het type van Campagne**
>
>Hoe moet de personalisatiecampagne in gang worden gezet?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Geplande campagne (altijd aan) | Doorlopende personalisatie die continu wordt uitgevoerd voor alle gekwalificeerde bezoekers | Stel de begindatum in op directe einddatum. Campagne blijft actief totdat u de toepassing handmatig beëindigt. Meestal voor webpersonalisatie. |
>| Geplande campagne (tijdgebonden) | Personalization gekoppeld aan een specifieke promotieperiode | Begin- en einddatum instellen. De campagne wordt automatisch gestopt na de einddatum. Geschikt voor seizoensgebonden promoties of aanbiedingen in beperkte tijd. |
>| API-gestuurde campagne | Personalization geactiveerd door een specifieke toepassingsgebeurtenis | Programmaatisch geactiveerd. Nuttig wanneer personalisatie alleen moet worden weergegeven als reactie op specifieke systeemgebeurtenissen. |

>[!NOTE]
>**Besluit: Het in kaart brengen van de frequentie**
>
>Moet de frequentie van de indruk voor deze personalisatie worden beperkt?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Frequentieregels toepassen | Promotie of op aanbieding gebaseerde personalisatie die bezoekers zou kunnen bemoeien | Voorkomt dat dezelfde personalisatie te vaak wordt weergegeven. Gevormd via de bedrijfsregels van AJO. |
>| Geen frequentiedop | Evergreen-inhoud aanpassen (banner voor loyaliteitsniveau, dashboardinhoud) | Altijd relevante inhoud die geen vermoeidheid veroorzaakt. Geen impressiegrenzen nodig. |

**navigatie UI:** [!DNL Journey Optimizer] > Campagnes > tot Campagne leiden

**Zeer belangrijke configuratiedetails:**

- Selecteer het web-, in-app- of inhoudskaartkanaal en het oppervlak dat is geconfigureerd in Fase 3
- Het doelpubliek binden dat is gedefinieerd in fase 1
- De inhoud koppelen die in Fase 4 is geschreven
- Het campagneschema configureren (direct, datumbereik of API-geactiveerd)
- De campagne evalueren en activeren
- Voor het experimenteren met inhoud: schakel het experimenteren in, definieer behandelingen, stel waarden voor verkeerstoewijzing en succes in voordat u het project activeert

**documentatie van Experience League:**

- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Aan de slag met campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)

### Fase 6: Afbeeldingen bijhouden en gegevens verzamelen

**functie van de Toepassing:** AEP: De Bronnen van Gegevens &amp; de Inzameling

**wat u zult vormen:** zorg ervoor dat de beelden, de interactie, en de omzettingen van gepersonaliseerde ervaringen terug naar het platform voor het melden, publiek herevaluatie, en beslissingsoptimalisering worden gevolgd.

**Zeer belangrijke configuratiedetails:**

- Controleren of Web SDK `decisioning.propositionDisplay` -gebeurtenissen verzendt wanneer persoonlijke inhoud wordt gerenderd
- Controleren of Web SDK `decisioning.propositionInteract` -gebeurtenissen verzendt wanneer bezoekers werken met gepersonaliseerde inhoud (klikken, ontslag)
- Voor Mobile SDK: controleer in-app berichten en interactiegebeurtenissen met de inhoudskaart worden vastgelegd
- Conversie-gebeurtenistracering configureren voor gegevens over downstreamsuccessen (aankopen, aanmelden, goedkeuring van functies)
- Zorg ervoor dat gebeurtenissen de voorstel-id bevatten voor toewijzing aan specifieke beslissingen voor personalisatie

**documentatie van Experience League:**

- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Gebeurtenissen bijhouden met Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/commands/sendevent/overview)
- [Overzicht van Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)

### Fase 7: rapporteren en optimaliseren

**functie van de Toepassing:** AJO: Rapportering &amp; de Analyse van Prestaties, Rapportering &amp; Analyse

**wat u zult vormen:** de prestaties van de opstelling controle en analyse om verpersoonlijkingsdoeltreffendheid over oppervlakken, segmenten, en inhoudsvarianten te meten. Gebruik native AJO-rapporten voor operationele metriek en [!DNL Customer Journey Analytics] voor de analyse van zakelijke gevolgen voor meerdere kanalen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: Meldend werkingsgebied**
>
>Welk niveau van analyse is nodig voor deze kwestie van het verpersoonlijkingsgebruik?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alleen systeemeigen AJO-rapporten | Operationeel toezicht op de gegevens over levering en betrokkenheid | Ingebouwde campagnerapporten met indruk, klik en omzettingsgegevens. Snelst in te stellen. |
>| CJA-kanaalanalyse | Diepe analyse van de gevolgen van personalisatie voor bedrijfsresultaten | Vereist CJA-verbinding en gegevensweergave. Hiermee schakelt u funnel-analyse, cohortvergelijkingen en kenmerkmodellering tussen kanalen in. |
>| Zowel AJO als CJA | Volledige operationele en analytische zichtbaarheid | Gebruik AJO voor dagelijkse controle en CJA voor strategische analyse. Aanbevolen voor productieimplementaties. |

**navigatie UI:**

- AJO-rapporten: Campagnes > Campagne selecteren > Rapport weergeven
- CJA: Projecten > Nieuw project maken

**Zeer belangrijke configuratiedetails:**

- Live-rapporten van de campagne openen tijdens levering van actieve personalisatie
- Historische rapporten voor voltooide campagnes of periodieke analyse bekijken
- Voor CJA: configureer een verbinding, inclusief AJO Experience-gebeurtenisdatasets, en maak een gegevensweergave met maatgegevens voor personalisatie
- Bouw dashboards die het tarief van de verpersoonlijking volgen, omzettingslift, aanbiedingstarief, en opbrengst per bezoek volgen
- Voor op besluiten-gebaseerde verpersoonlijking (Optie B): de prestaties van de monitor door plaatsing en rangschikkingsstrategie doeltreffendheid

**documentatie van Experience League:**

- [Campagne live-rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [Rapport voor inhoudexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementatieoverwegingen

In deze sectie worden onder andere de volgende zaken behandeld: instructies, gemeenschappelijke valkuilen, beste praktijken en handelsbeslissingen die relevant zijn voor dit gebruikspatroon.

### Guardrails en limieten

- De raadplegingen van Edge Network hebben een reactietijd SLA van minder dan 200ms voor rand-geëvalueerde segmenten — [ Echte - de guardrails van het Profiel van de Klant van de Tijd ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- Maximum van 4.000 segmentdefinities per zandbak - [ de gidsen van de Segmentatie ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- De segmenten van Edge zijn beperkt tot eenvoudige attributencontroles en vragen van het segmentlidmaatschap — geen tijd-reeksen vragen — [ de segmentatie van Edge ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- Slechts één samenvoegingsbeleid kan op Edge per zandbak actief zijn - [ beleid van de Fusie ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)
- Maximum van 10.000 goedgekeurde gepersonaliseerde aanbiedingen per zandbak - [ de gidsen van het Beheer van het Besluit ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum van 30 plaatsen per besluit - [ de guardrails van Journey Optimizer ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Voor AI-classificatiemodellen is een minimum van 1.000 conversieevenementen vereist voor training
- De leveringstijd van de aanbieding SLA is minder dan 500 ms bij P95 voor single-scope verzoeken
- Maximum van 500 actieve levende campagnes per zandbak — [ de guardrails van Journey Optimizer ](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- Maximum van 25 actieve gegevens verwerkte attributen per zandbak — [ verwerkte attributengidsen ](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)

### Veelvoorkomende valkuilen

- **de fusiebeleid van Edge niet gevormd:** Zonder een rand-actief fusiebeleid, kan Edge Network niet het voor authentiek verklaarde profiel oplossen, veroorzakend verpersoonlijking om te ontbreken of terug naar anoniem gedrag te vallen. Zorg ervoor dat precies één samenvoegbeleid `isActiveOnEdge: true` in de sandbox heeft.
- **publiek niet rand-in aanmerking komend:** als de uitdrukkingen van de de publieksegmentregel tijd-reeksen, complexe samenvoegingen, of `inSegment()` verwijzingen naar partij-slechts segmenten gebruiken, zullen zij niet voor randevaluatie kwalificeren en kunnen geen verpersoonlijking in real time aandrijven. Valideer randgeschiktheid tijdens publieksdefinitie.
- **Identiteit die hiaat stitching tijdens authentificatie:** wanneer een bezoekersovergangen van anoniem aan voor authentiek verklaard, kan er een kort moment zijn waar het profiel nog niet heeft opgelost. Zorg ervoor dat identiteitsstitching correct wordt gevormd en dat het Web SDK de voor authentiek verklaarde identiteit via `identityMap` onmiddellijk na login verzendt.
- **Ontbrekende reserveaanbieding in besluit:** als geen reserveaanbieding wordt gevormd en geen gepersonaliseerde aanbieding voor een bezoeker kwalificeert, keert het besluit lege inhoud terug, die tot een gebroken ervaring leiden. Configureer altijd een fallback-aanbieding voor alle plaatsingen.
- **SDK van het Web verzendt geen gebeurtenissen van de projectievertoning:** als `renderDecisions` aan `true` wordt geplaatst maar de vertoningsgebeurtenissen niet worden verzonden, zal het melden geen daadwerkelijke indrukkingen weerspiegelen. Verifieer gebeurtenis het volgen door netwerkverzoeken in browser ontwikkelaarshulpmiddelen te inspecteren.
- **het flikkeren van de Inhoud op paginading:** als de gepersonaliseerde inhoud niet pre-verborgen tijdens de beslissingsvraag is, kunnen de bezoekers standaardinhoud kort zien alvorens het wordt vervangen. Gebruik het voorverborgen fragment of het op CSS gebaseerde voorverbergen om flikkering te voorkomen.

### Aanbevolen procedures

- Begin met op segment-gebaseerde verpersoonlijking (Optie A) voor aanvankelijke implementatie, dan evolueer aan op besluit-gebaseerd (Optie B) aangezien de aanbiedingencatalogus groeit en optimalisatiebehoeften stijgen
- Gebruik waar mogelijk randbeoordeelde soorten publiek voor realtime personalisatie; streaming en batchgebruik voor complementaire gebruiksgevallen reserveren
- Inhoud experimenteren met persoonlijke ervaringen implementeren om te valideren dat personalisatie een meetbare lift boven de standaardinhoud drijft
- De personalisatie van het ontwerp met een graceful degradatiestrategie — als het profiel niet bij de rand kan worden opgelost, toont goed-ontworpen standaardinhoud eerder dan een gebroken ervaring
- Gebruik berekende kenmerken om hoogwaardige personalisatiesignalen te maken, zoals betrokkenheidsscore, productaffiniteit en dagen sinds de laatste aankoop, die zowel op segmenten gebaseerde als op beslissingen gebaseerde personalisatiekwaliteit verbeteren
- Behoud een proces voor contentbeheer om ervoor te zorgen dat gepersonaliseerde inhoud actueel blijft, in het merk wordt weergegeven en op alle oppervlakken compatibel blijft
- Verpersoonlijkingsprestaties per segment controleren om te bepalen welk publiek het meest van verpersoonlijking profiteert en waar de lift het sterkst is

### Handelsbesluiten

>[!NOTE]
>**handel-off: granularity van Personalization tegenover de ingewikkeldheid van het inhoudsbeheer**
>
>Meer korrelige personalisatie (meer segmenten, meer inhoudvarianten, meer oppervlakken) biedt steeds meer op maat gesneden ervaringen maar vereist proportioneel meer inspanningen voor het maken, onderhouden en beheren van inhoud.
>
>- **hogere granulariteit gunt:** betere klantenervaring, hogere overeenkomst, sterkere omzettingslift
>- **Lagere granularity gunst:** Snellere implementatie, lagere lasten van het inhoudonderhoud, eenvoudiger bestuur
>- **Aanbeveling:** Begin met 3-5 high-impact segmenten (b.v., loyaliteitsrijen of levenscyclusstadia) met duidelijke inhouddifferentiatie. Breid granulariteit uit op basis van gemeten prestatielift. Met Beslissing (Option B) kunt u de granulariteit schalen zonder de groei van het inhoudsbeheer proportioneel te vergroten.

>[!NOTE]
>**handel-off: Beslissing in real time vs. deterministische inhoudscontrole**
>
>Op beslissing-gebaseerde verpersoonlijking (Optie B) verstrekt dynamische optimalisering maar vermindert directe controle over welke inhoud elke bezoeker ziet. De op segment-gebaseerde verpersoonlijking (Optie A) verstrekt volledige deterministische controle maar beperkt dynamische optimalisering.
>
>- **Beslissende gunsten:** Schaalbaarheid, automatische optimalisering, complexe toelatingsscenario&#39;s
>- **op segment-gebaseerde voorkeur:** Voorspelbaarheid, nalevingscontrole, de transparantie van de aandeelhouder
>- **Aanbeveling:** Op segment-gebaseerde verpersoonlijking van het gebruik voor naleving-gevoelige inhoud (regelgevend overseinen, rij-specifieke tarifering) waar de nauwkeurige controle wordt vereist. Gebruik beslissingen voor promotionele inhoud, aanbiedingen en aanbevelingen waarbij dynamische optimalisatie toegevoegde waarde heeft.

>[!NOTE]
>**handel-off: De gegevensbeschikbaarheid van Edge versus verpersoonlijkingsrijkdom**
>
>Door Edge beoordeelde personalisatie is beperkt tot kenmerken die beschikbaar zijn in de winkel met randprofielen. Rijkere personaliseringssignalen (volledige gedragsgeschiedenis, complexe gegevens verwerkte attributen) kunnen server-zijraadpleging of pre-berekening vereisen.
>
>- **Edge-slechts gunt:** Subtweede latentie, eenvoudigste architectuur
>- **pre-gegevens verwerkte verrijking bevordert:** rijkere verpersoonlijkingssignalen, verfijndere publieksdefinities
>- **Aanbeveling:** Gebruik gegevens verwerkte attributen om rijke gedragssignalen in rand-beschikbare profielattributen vooraf samen te voegen. Dit geeft de rijkdom aan gedragsgegevens met de snelheid van randevaluatie.

## Gerelateerde documentatie

De volgende middelen verstrekken extra detail op de technologieën en de configuraties die in deze gids van verwijzingen worden voorzien.

### Webkanaalpersonalisatie

- [Aan de slag met webkanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/get-started-web)
- [Webervaringen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/create-web)
- [Webkanaalconfiguratie](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/web/web-configuration)

### In-app en inhoudskaartkanalen

- [Overzicht in-app kanaal](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/get-started-in-app)
- [Voorwaarden voor kanalen in de app](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/inapp-configuration)
- [In-app berichten maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/in-app/create-in-app)
- [Kanaal van inhoudskaart](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/get-started-content-card)
- [Configuratie van inhoudskaart](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/content-card-configuration)
- [Inhoudskaarten maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/content-card/create-content-card)

### Beslissingsbeheer

- [Overzicht van Beslissingsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/get-started-decision/starting-offer-decisioning)
- [Plaatsingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-placements)
- [Beslissingsregels maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-decision-rules)
- [Gepersonaliseerde aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-personalized-offers)
- [Alternatieve aanbiedingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-fallback-offers)
- [Verzamelingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-collections)
- [Beslissingen maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/create-components/creating-activities)
- [Rangorde van strategieën](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/ranking/ranking-strategies)
- [Aanbiedingen in berichten leveren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/decisioning/offer-decisioning/deliver-offers/deliver-offers-in-messages)

### Personalization en inhoud

- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helpfuncties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)

### Splitsen en segmenteren

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Edge-segmentatie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/edge-segmentation)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Profile Query Language-referentie](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/pql/overview)

### Identiteit en profiel

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van naamruimten](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Koppelingsregels voor identiteitsgrafiek](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Profieloverzicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Gegevensverzameling en SDK

- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Web SDK installeren](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
- [Overzicht van Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Overzicht Edge Network Server API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)

### Campagnes en experimenten

- [Aan de slag met campagnes](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/get-started-with-campaigns)
- [Een campagne maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/campaigns/create-campaign)
- [Aan de slag met het experimenteren met inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/content-experiment)
- [Een inhoudexperiment maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/create-content-experiment)
- [Rapport voor inhoudexperiment](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-experiment/experiment-report)

### Berekende kenmerken en verrijking

- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Gebruikershandleiding voor berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)
- [AI-overzicht van klant](https://experienceleague.adobe.com/en/docs/experience-platform/intelligent-services/customer-ai/overview)

### Rapportage en analyse

- [Campagne live-rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-live-report)
- [Globaal verslag campagne voeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/campaign-global-report-cja)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)
- [CJA-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview)
- [Analysis Workspace-overzicht](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-workspace/home)

### Bestuur en privacy

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Toestemming in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)
- [Overzicht van geavanceerd gegevenslevenscyclusbeheer](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home)

### Beveiligingsmechanismen

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Identiteitsservicehandleidingen](https://experienceleague.adobe.com/en/docs/experience-platform/identity/guardrails)
