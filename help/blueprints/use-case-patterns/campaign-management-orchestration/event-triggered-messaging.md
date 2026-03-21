---
title: Gebeurtenisgestuurde berichten
description: Leer hoe u contextuele, realtime berichten kunt leveren als reactie op gedrags- of systeemgebeurtenissen.
solution: Journey Optimizer, Real-Time Customer Data Platform
source-git-commit: 126dd712603494513b71a8a6e1c4b99bdb7ff212
workflow-type: tm+mt
source-wordcount: '9039'
ht-degree: 0%

---


# Gebeurtenisgestuurde berichten

Deze handleiding bevat een uitgebreide implementatieblauwdruk voor berichten die door gebeurtenissen worden geactiveerd met [!DNL Adobe Journey Optimizer] (AJO), [!DNL Real-Time Customer Data Platform] (RT-CDP) en [!DNL Adobe Experience Platform] (AEP). Het wordt ontworpen voor oplossingsarchitecten, marketing technologen, en implementatietechnici die contextuele, real-time berichten in antwoord op gedrag of systeemgebeurtenissen moeten leveren.

Gebruik deze gids om te begrijpen wat te vormen, waar de implementatiekeuzen bestaan, en welke compromis drijven elk besluit.

De gids behandelt de volledige levenscyclus van gebeurtenisopname en het verwezenlijking van de reis door berichtlevering en prestatiesrapportering, met gedetailleerde beslissingsbegeleiding voor drie verschillende implementatieopties.

## Hoofdlettergebruik

Gebeurtenis-teweeggebracht overseinen levert een contextafhankelijk bericht in antwoord op een gedrag in real time of systeemgebeurtenis. In tegenstelling tot batchactivering van uitgaande berichten, die naar een vooraf geëvalueerd publiek volgens een schema verzendt, luistert dit patroon naar een kwalificerende gebeurtenis — zoals een winkelwagentje, een bladersessie, een formulierverzending of een wijziging in de systeemstatus — en voert dit patroon onmiddellijk het activeringsprofiel in een reis die voorwaarden evalueert en een bericht aflevert.

Het patroon is gebaseerd op real-time streaming van gebeurtenissen naar AEP (via Web SDK, Mobile SDK of server-side API), een reis met een eenheidgebeurtenis in AJO en logica voor voorwaardevaluatie die bepaalt of en wat er moet worden verzonden. Het bericht wordt doorgaans binnen minuten na de activerende gebeurtenis verzonden, waardoor dit patroon ideaal is voor tijdgevoelige, contextafhankelijke communicatie.

Organisaties gebruiken dit patroon om in real-time te reageren op acties van klanten, waardoor de relevantie toeneemt en hogere betrokkenheid- en conversietarieven worden gehanteerd dan bij geplande batchcommunicatie. Veelvoorkomende scenario&#39;s zijn achtergelaten kaartherstel, follow-up na aankoop, welkomstberichten na registratie en tijdgevoelige meldingen zoals betalingsfouten of waarschuwingen voor prijsverlaging.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

**[Terugwinning verlaten wagentjes &amp; reizen](../../business-objectives/customer-experience/recover-abandoned-carts-journeys.md)**

Neem gebruikers opnieuw op die tijdens aankoop, toepassing, of inschrijvingsstromen met geschikte, gepersonaliseerde follow-ups zijn weggevallen.

| KPI&#39;s |
| --- |
| Omrekeningskoersen, incrementele inkomsten, betrokkenheid |

**[de omzettingspercentages van de Verhoging](../../business-objectives/revenue-monetization/increase-conversion-rates.md)**

Verbeter het percentage bezoekers en de vooruitzichten die de gewenste acties zoals aankopen, inschrijven, of vormverzendingen voltooien.

| KPI&#39;s |
| --- |
| Omzettingssnelheden, omzetting van lead, kosten per lead |

**[lever gepersonaliseerde klantenervaringen](../../business-objectives/customer-experience/deliver-personalized-customer-experiences.md)**

Inhoud, aanbiedingen en berichten voor individuele voorkeuren, gedrag en levenscyclusfase aanpassen.

| KPI&#39;s |
| --- |
| Betrokkenheid, omrekeningskoersen, klanttevredenheid (CSAT) |

**[verbeter klant onboarding](../../business-objectives/customer-experience/improve-customer-onboarding.md)**

Versnel tijd-aan-waarde voor nieuwe klanten met gestroomlijnde, gepersonaliseerde welkom ervaringen en activeringsreizen.

| KPI&#39;s |
| --- |
| Betrokkenheid, bewaring, conversietarieven |

## Voorbeelden van tactische gebruiksgevallen

De volgende scenario&#39;s illustreren hoe het gebeurtenis-teweeggebrachte overseinen over verschillende bedrijfscontexten kan worden toegepast.

- **Verlaat van de winkelwagentje e-mail of SMS** — verzend een herinneringsbericht wanneer een klant punten aan hun winkelwagentje toevoegt maar niet de aankoop binnen een bepaald tijdvenster voltooit
- **doorblader de follow-up van de verlaten** — Draai bezoekers opnieuw in dienst die producten of inhoud bekeken maar geen omzettingsactie nam
- **ná-aankoop dank-u of dwars-verkoop** — Lever een bevestiging en dwars-verkoopaanbeveling onmiddellijk na een aankoopgebeurtenis
- **Herinnering van de proefvervaldatum** — Deel gebruikers mee die het eind van een vrije proef met vernieuwing of omzettingsoverseinen naderen
- **Welkome bericht na registratie** — verzend een onmiddellijk instapend bericht wanneer een nieuwe gebruiker registreert of een rekening creeert
- **bevestiging van de de voorlegging van de Vorm** — Bevestig vormvoorlegging (contactverzoeken, toepassingen, inschrijvingen) met een contextuele bevestiging
- **bericht van de mislukking van de Betaling** — Alarm klanten wanneer een terugkomende betaling ontbreekt, die hen ertoe aanzetten om betalingsinformatie bij te werken
- **App uninstall win-back dupmelding** — Trigger een win-backbericht wanneer een gebruiker een mobiele toepassing verwijdert
- **het Boeken of benoemingsbevestiging** - verzend directe bevestiging na een boek, een reserve, of een benoeming is gepland
- **het dalingsalarm van de Prijs voor gezochte vermelde punten** — Meld klanten wanneer een product op hun verlanglijst in prijs daalt

## Kernprestatie-indicatoren

De volgende hulp KPIs meet de doeltreffendheid van gebeurtenis-teweeggebrachte overseinenimplementaties.

| KPI | Beschrijving | Meting |
| --- | --- | --- |
| Conversiesnelheid | Percentage getriggerde berichtontvangers die de gewenste actie uitvoeren (aankoop, aanmelding, verlenging) | Afgeleverde conversies/berichten * 100 |
| Incrementele inkomsten | Aanvullende inkomsten die zijn toe te schrijven aan gebeurtenisgestuurde berichten in vergelijking met besturingsgroepen die geen verzendbesturingselementen verzenden | Inkomsten uit teweeggebrachte verzendingen - basislijn van controlegroep |
| OpenRate | Percentage geleverde berichten die door ontvangers worden geopend | Openen/geleverde * 100 |
| Doorkliksnelheid (CTR) | Percentage geleverde berichten die minstens één klik produceren | Klikken/geleverde * 100 |
| Tijd voor conversie | Gemiddelde verstreken tijd tussen berichtlevering en conversiegebeurtenis | Avg (tijdstempel conversie - tijdstempel levering) |
| Voltooiingssnelheid reis | Percentage profielen dat de reis ingaat en de stap van de berichtlevering bereikt (niet gelaten vallen door voorwaarden of uitgang) | Profielen die op levering komen / Profielen die op reis gaan * 100 |
| Berichtonderdrukkingssnelheid | Percentage onderdrukte kwalificatieprofielen als gevolg van frequentiecamera&#39;s, toestemmingen of voorwaardelijke evaluatie | Onderdrukte profielen / Totaal aantal kwalificatieprofielen * 100 |
| Stuitsnelheid | Percentage berichten dat niet kon worden geleverd vanwege harde of zachte stuiteringen | Stortingen / Verzonden * 100 |

## Hoofdletterpatroon gebruiken

Deze sectie beschrijft het kernpatroon en de functieketen die gebeurtenis-teweeggebrachte overseinen drijven.

**gebeurtenis-teweeggebracht Overseinen**

Luister naar een realtime gedrags- of systeemgebeurtenis en lever vervolgens een contextueel bericht aan het activeringsprofiel.

**Keten van de Functie:** de Ingestie van de Gebeurtenis > Ingang van de Reis > de Evaluatie van de Voorwaarde > de Levering van het Bericht > het Melden

## Applicaties

In dit gebruikspatroon worden de volgende Adobe-toepassingen gebruikt.

- **[!DNL Adobe Journey Optimizer] (AJO)** — Reisorganisatie met eenheidgebeurtenis ingang, voorwaardevaluatie, wachtstappen, berichtauthoring, kanaalconfiguratie, frequentiebeheer en leveringsrapportage
- **[!DNL Adobe Real-Time Customer Data Platform] (RT-CDP)** — Poortevaluatie voor voorwaardelijk filtreren binnen reizen, toestemming en governance handhaving, profielverrijking
- **[!DNL Adobe Experience Platform] (AEP)** — Real-time gebeurtenisopname via Web SDK, Mobile SDK of server-side API; gegevensmodellering; identiteitsresolutie; Edge Network

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary Function | Status | Wat moet er gebeuren? | Experience League Reference |
| --- | --- | --- | --- |
| Beheer en bestuur | Verondersteld op plaats | AJO-sandbox met actieve kanaalconfiguratie. Reis maken en publicatiemachtigingen publiceren die zijn toegewezen aan het implementatieteam. Gebruikersrollen geconfigureerd voor reisbeheer, het schrijven van inhoud en kanaalbeheer. | [&#x200B; het overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sandbox/home), [&#x200B; overzicht van de Toegangscontrole &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | In een XDM ExperienceEvent-schema moet de activerende gebeurtenis worden vastgelegd met alle contextuele velden die nodig zijn voor voorwaardenevaluatie en berichtpersonalisatie (bijvoorbeeld `commerce.productListAdds` voor cartgebeurtenissen, productdetails, cartwaarde). Het schema moet voor het Profiel van de Klant in real time worden toegelaten. Een overeenkomstige dataset moet worden gecreeerd en profiel-toegelaten. | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home), [&#x200B; de samenstellingsgrondbeginselen van het Schema &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition) |
| Gegevensbronnen en -verzameling | Vereist | Gebeurtenisstreaming in realtime moet worden geconfigureerd — Web SDK for web-gebeurtenissen, Mobile SDK for app-gebeurtenissen of Edge Network Server API voor systeemgebeurtenissen. Een gegevensstroom moet met toegelaten de diensten van AEP en van AJO worden gevormd, die gebeurtenissen aan de correcte dataset verpletteren. Dit is een kritieke afhankelijkheid omdat het patroon van gebeurtenis in real time afhangt. | {het overzicht van SDK van 0} Web [&#128279;](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home), [&#x200B; vormt gegevensstromen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure) |
| Identiteit en profielconfiguratie | Vereist | De activeringsgebeurtenis moet gekoppeld zijn aan een bekende identiteit (e-mail, CRM-id of geverifieerde sessie), zodat de reis het profiel kan oplossen en het bericht kan verzenden. Naamruimten moeten bestaan voor de id&#39;s die door de activeringsgebeurtenis worden gebruikt. Anonieme gebeurtenissen vereisen identiteitsstitching via de identiteitsgrafiek alvorens een bericht kan worden geleverd. Een fusiebeleid moet worden gevormd. | [&#x200B; overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home), [&#x200B; overzicht van het beleid van de Fusie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview) |
| Auditiedefinitie en segmentatie | Aanbevolen | Hoewel strikt vereist voor gebeurtenis-teweeggebrachte reizen (de ingang is gebeurtenis-gebaseerd, niet op publiek-gebaseerd), kunnen de publiekssegmenten voor voorwaardenevaluatie binnen de reis worden gebruikt (b.v., slechts verzenden als het profiel in een &quot;high-value klant&quot;segment is, of onderdrukken als het profiel in een &quot;onlangs gecontacteerd&quot;segment is). De evaluatie van het stromen wordt geadviseerd voor de controles van het segmentlidmaatschap in real time binnen reizen. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home), [&#x200B; Streaming segmentatie &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League Reference |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Berekende kenmerken, zoals het aantal dagen dat het winkelwagentje wordt verlaten, het aantal dagen sinds de laatste aankoop, de gemiddelde orderwaarde en het totale bedrag van de levenslange aankoop, verbeteren de evaluatie van de conditie en de personalisatie binnen de getriggerde reizen. Deze gedragsaggregaten maken nauwkeuriger gerichte beslissingen mogelijk (bijvoorbeeld onderscheid maken tussen mensen die voor het eerst afstappen van recidive). | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | Vervaldatum van gebeurtenisgegevens moet worden geconfigureerd voor voorbijgaande gedragsgebeurtenissen (paginaweergaven, zoekopdrachten, klikken) om opslagkosten en compatibiliteit te beheren. De gebieden van het toestemmingsschema moeten aanwezig zijn voor kanaal-specifieke opt-in/opt-out handhaving tijdens berichtlevering. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/home), [&#x200B; Verlopen Dataset &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-lifecycle/ui/dataset-expiration) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | De etiketten van het bestuur op gebeurtenis en profielgebieden verzekeren volgzame verpersoonlijking. Als gepersonaliseerde inhoud in getriggerde berichten wordt opgenomen met behulp van PII- of gedragsgegevens, moeten de labels voor gegevensgebruik en het governancebeleid worden herzien om onbevoegd gegevensgebruik in berichtinhoud te voorkomen. | [&#x200B; het beheer van Gegevens overzicht &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home), [&#x200B; overzicht van de gebruiksetiketten van Gegevens &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview) |
| Bewaking en waarneming | Opgenomen | Controle van de uitvoering van de reis maakt deel uit van de rapportagefase. Bovendien, vorm alarm voor de mislukkingen van de gebeurtenisopname of de vertragingen van de reisverwerking om pijpleidingskwesties te ontdekken die teweeggebrachte berichten zouden verhinderen worden verzonden. | [&#x200B; het overzicht van Alarm &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview), [&#x200B; Overzicht van de Inzichten van de Waarneming &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home) |
| Rapportage en analyse | Opgenomen | Reisprestatierapporten worden behandeld in de rapportagefase. Voor een diepere analyse van teweeggebrachte overseinendoeltreffendheid over kanalen en in tijd, vorm de verbindingen en de werkruimten van CJA om omzetattributie, tijd-aan-omzetting, en kanaalprestaties te analyseren. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/analytics-platform/using/cja-overview/cja-overview), [&#x200B; AJO + de integratiegids van CJA &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Journey Optimizer] (AJO)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Journey Orchestration | Reisontwerp en -configuratie | Maak een reis met eenheidgebeurtenis, configureer de kwalificerende gebeurtenis, voeg voorwaardenknopen toe, wacht stappen, berichtacties, uitgangscriteria, en re-entry regels |
| Kanaalconfiguratie | Kanaaloppervlak instellen | Kanaaloppervlakken (e-mail, SMS, push) configureren of valideren, inclusief subdomeindelegatie, IP-pools, afzenderinstellingen en beheer van suppressielijst |
| Berichtontwerp | Berichtinhoud maken | Contextuele berichtinhoud van de auteur met gebeurtenis-gedreven verpersoonlijking, voorwaardelijke inhoudsblokken, en herbruikbare fragmenten |
| Frequentie en bedrijfsregels | Reis maken en configureren (Option C) | Vorm frequentiecappen en deduplicatieregels om over overseinen van high-frequency gebeurtenisbronnen te verhinderen |
| Conflict- en prioriteitsbeheer | Reisontwerp en -configuratie | Prioriteitsscores toewijzen en conflictdetectie configureren voor reizen die voor dezelfde profielen concurreren |
| Rapportage en prestatieanalyse | Rapportage en bewaking | De metriek van de reislevering van de monitor via levende en historische rapporten; toegang programmacode prestatiesgegevens via CJA |

### [!DNL Real-Time CDP] (RT-CDP)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Foundational Setup (F5) | Evalueer publiekssegmenten die voor op voorwaarde-gebaseerde het filtreren binnen de reis worden gebruikt (b.v., high-value klantensegmenten, onderdrukkingssegmenten) |
| Goedkeuring en handhaving van bestuur | Foundational Setup (S2/S3) | Handhaaf toestemmingsvoorkeur en het beleid van het gegevensgebruik tijdens berichtlevering om volgzame mededelingen te verzekeren |

## Vereisten

Voltooi het volgende voordat u begint met de implementatie.

- [ ] AJO-sandbox met bevoegdheden voor het maken en publiceren van reizen (F1)
- [ ] XDM ExperienceEvent-schema dat de activerende gebeurtenis vastlegt met contextuele velden, ingeschakeld voor Real-Time Klantprofiel (F2)
- [ ] Real-time streaming van gebeurtenissen geconfigureerd via Web SDK, Mobile SDK of Edge Network Server API met een gegevensstroom die gebeurtenissen naar de juiste AEP-dataset routeert (F3)
- [ ] Naamruimten geconfigureerd voor de id&#39;s van de activerende gebeurtenis; regels voor identiteitskoppeling ingesteld (F4)
- [ ] Kanaaloppervlak (e-mail, SMS of push) geconfigureerd en gevalideerd met een geslaagde test voor verzenden
- [ ] Berichtinhoud geschreven, gecontroleerd en getest met voorbeeldprofielen
- [ ] Toegangsvelden die zijn ingevuld in profielen voor het doelkanaal (bijvoorbeeld `consents.marketing.email.val` )
- [ ] Bij gebruik van op voorwaarde gebaseerde publiekfiltering (Option B/C), worden streaming-geëvalueerde publiekssegmenten gedefinieerd en actief geëvalueerd

## Implementatieopties

Deze sectie beschrijft drie implementatieopties voor gebeurtenis-teweeggebrachte overseinen. Elke optie bouwt op vorige voort, die extra mogelijkheden toevoegt.

### Optie A: Eenvoudig, door de gebeurtenis geactiveerd bericht

**Best voor:** Onmiddellijke, enig-berichtreacties waar geen vertraging of voorwaardelijke logica nodig is — de bevestiging van de orde, welkome e-mail, de erkenning van de vormvoorlegging, reserveringsbevestiging.

**hoe het werkt:**

De reis luistert naar een kwalificerende gebeurtenis via een eenheidgebeurtenisingknooppunt. Wanneer de gebeurtenis wordt ontvangen, gaat het profiel de reis in, gaat door minimale voorwaardenevaluatie (toestemmingscontrole, profielcontrole), en ontvangt onmiddellijk één enkel bericht via de gevormde knoop van de kanaalactie.

Dit is de eenvoudigste implementatievariant. Het reiscanvas bevat een knooppunt voor gebeurtenisinvoer, een optioneel knooppunt voor elementaire geschiktheidscontroles, een knooppunt voor één actiepunt voor berichten en een knooppunt voor eindbewerkingen. Er zijn geen wachtstappen, geen complexe vertakking en geen conversiecontroles. Het bericht wordt doorgaans binnen seconden tot minuten na de activeringsgebeurtenis bezorgd.

Gebeurtenisgegevens van de activeringsgebeurtenis (productnaam, totaal van de volgorde, formulierdetails) kunnen worden gebruikt voor het personaliseren van berichten via contextafhankelijke kenmerken in de personalisatie-editor. Deze benadering maximaliseert snelheid-aan-levering en minimaliseert reis ingewikkeldheid.

**Zeer belangrijke overwegingen:**

- Het bericht wordt verzonden ongeacht of de klant na de gebeurtenis zelf-omzet (geen omzettingscontrole)
- Het meest geschikt voor gebeurtenissen die inherent een directe reactie rechtvaardigen (bevestigingen, erkenningen)
- Regels voor herinvoer moeten zorgvuldig worden geconfigureerd — voor berichten in bevestigingsstijl, herinvoer toestaan zodat elke gebeurtenis een bericht genereert; voor berichten in welkomststijl, herinvoer voorkomen

**Voordelen:**

- Snelste levertijd (seconden tot minuten na de gebeurtenis)
- Eenvoudigste reisconfiguratie met minimale bewegende onderdelen
- Laagste risico van mislukte of geplakte profielen
- Eenvoudig te testen en te onderhouden

**Beperkingen:**

- Geen mogelijkheid om te controleren of de klant zichzelf heeft geconverteerd voordat hij of zij het verzendt
- Kan voorwaardelijk logica met vertraging niet opnemen
- Kan onnodige berichten genereren als de gebeurtenis vaak plaatsvindt zonder frequentieregelgeving

**Experience League:**

- [Een reis maken](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Algemene gebeurtenissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)

### Optie B: Voorwaardelijk gebeurtenisgeactiveerd bericht met wachttijd

**Best voor:** Vertraagde, voorwaardelijke reacties waar de klant tijd zou moeten hebben om zich vóór het ontvangen van het bericht om te zetten - de kar verlaten (wacht 1-4 uren, dan controleer als het karretje nog) wordt verlaten, doorbladert verlaten (wacht 24 uur, controleer of de aankoop werd gemaakt), proefafloop (wacht tot de vervaldatum nadert).

**hoe het werkt:**

De reis luistert naar een kwalificerende gebeurtenis, gaat het profiel in, en introduceert een wachttijdperiode alvorens voorwaarden te evalueren. Na het wachten, controleert een voorwaardenknoop of de klant zelf-omgezet (b.v., voltooide de aankoop, vernieuwde het abonnement) of de originele context nog geldig is. Alleen als aan de voorwaarde is voldaan (bv. de nog verlaten wagentje) gaat de reis door naar de levering van berichten.

Het reiscanvas bevat een knooppunt voor gebeurtenisinvoer, een wachttijdknooppunt (configureerbare duur of specifieke datum/tijd), een knooppunt voor voorwaarden dat controleert op een wijziging in een conversiegebeurtenis of profielstatus, vertakkende paden (bericht verzenden versus afsluiten zonder verzenden), een knooppunt voor berichtactie op het kwalificerende pad en een eindknooppunt op elke vertakking. De criteria van de uitgang kunnen worden gevormd om profielen van de reis automatisch te verwijderen als de conversiegebeurtenis tijdens de wachttijd voorkomt, die de behoefte aan de expliciete voorwaardencontrole elimineren.

Deze benadering vermindert onnodig overseinen door klanten tijd te geven om zich om te zetten, verbeterend de klantenervaring en verhogend de waargenomen relevantie van berichten die worden verzonden.

**Zeer belangrijke overwegingen:**

- De duur van de wachttijd heeft een aanzienlijke invloed op de conversiekoersen: kortere wachttijden (1-2 uur) veroorzaken een hogere urgentie, maar meer overbodig verzenden; langere wachttijden (24-48 uur) verminderen het volume maar kunnen het relevante venster missen
- De Condition-evaluatie vereist dat de conversiegebeurtenis wordt vastgelegd in AEP en gekoppeld aan dezelfde profielidentiteit
- De criteria van de uitgang verstrekken een schoner alternatief aan expliciete voorwaardenknopen voor omzetcontrole
- Regels voor herintreding moeten rekening houden met de wachttijd — een profiel mag de reis niet opnieuw betreden terwijl al gewacht wordt

**Voordelen:**

- Vermindert onnodig overseinen door voor zelfomzetting te controleren
- Produceert betere kwaliteit, relevantere mededelingen
- Steunt tijd-gevoelige gebruiksgevallen met configureerbare vertragingsvensters
- Afsluitingscriteria maken het automatisch verwijderen van de reis bij conversie mogelijk

**Beperkingen:**

- Grotere complexiteit van de reis met wachttijd- en voorwaardenknooppunten
- Profielen nemen tijdens wachttijden slots in beslag (afhankelijk van een reistime-out van 91 dagen)
- Vereist dat de conversiegebeurtenis in AEP wordt opgenomen binnen het wachttijdvenster voor een nauwkeurige statusevaluatie
- Langere tijd-aan-levering in vergelijking met Optie A

**Experience League:**

- [Wachtactiviteit](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Voorwaardeactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Afsluitingscriteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)

### Optie C: Gebeurtenis geactiveerd met frequentiebeheer

**Best voor:** Hoog-frequente gebeurtenisbronnen waar de berichtvermoeidheid een zorg is — paginameningen, productmeningen, onderzoeksvragen, herhalen de toevoegingen van het karretje. Kan worden toegepast als een bedekking boven op optie A of optie B.

**hoe het werkt:**

Deze optie voegt frequentiebeheer aan of Optie A of Optie B toe om over-overseinen te verhinderen. Hoge frequente gedragsgebeurtenissen (zoals productweergaven of herhaalde toevoegingen van winkelwagentjes) kunnen de reis meerdere keren binnen een korte periode teweegbrengen. Zonder frequentiebeheer kan een profiel dubbele of excessieve berichten ontvangen.

Het beheer van de frequentie wordt geïmplementeerd via twee complementaire mechanismen: AJO-bedrijfsregels (frequentieclaims) die het aantal berichten dat een profiel per kanaal per tijdsperiode ontvangt, beperken, en regels voor het opnieuw betreden van de reis die een afkoelingsperiode definiëren voordat een profiel dezelfde reis opnieuw kan betreden. De bedrijfsvoorschriften werken op organisatieniveau en dwingen plafonds toe voor alle campagnes en reizen (bijv. maximaal 3 e-mails per week), terwijl de afkoelingsservice op individueel niveau wordt uitgevoerd (een profiel kan deze specifieke reis bijvoorbeeld niet binnen 72 uur na de laatste binnenkomst opnieuw betreden).

Bovendien, kunnen het conflict en prioritaire beheer worden gevormd om prioritaire scores aan de teweeggebrachte reis toe te wijzen, die ervoor zorgen dat wanneer veelvoudige reizen of campagnes voor het zelfde profiel concurreren, de hoogst-prioritaire mededeling wint.

**Zeer belangrijke overwegingen:**

- De frequentiecamera&#39;s moeten een evenwicht vinden tussen het voorkomen van vermoeidheid en het waarborgen van belangrijke getriggerde berichten.
- Kanaalspecifieke uiteinden worden aanbevolen: e-mail, SMS en push hebben verschillende vermoeiingsdrempels
- De terugkeer van de reis koeldown en organisatie-vlakke frequentiecappen werken samen; allebei zouden moeten worden gevormd
- Prioritaire scores bepalen welke communicatie wint wanneer de uiteinden worden bereikt — hogere prioriteit moet worden toegekend aan reizen met hogere scores

**Voordelen:**

- Voorkomt vermoeidheid van berichten uit bronnen van veelvoorkomende gebeurtenissen
- Houdt merkreputatie en abonneetevredenheid in stand
- Organisatievlakken bieden een vangnet voor alle campagnes en reizen
- Met prioriteitsscoring worden de belangrijkste berichten geleverd wanneer de hoofdletters worden bereikt

**Beperkingen:**

- Sommige kwalificatieprofielen worden onderdrukt, mogelijk ontbrekende relevante berichten
- De configuratie van frequentieclips verhoogt de administratieve complexiteit
- De plafonds kunnen onverwacht communiceren met andere actieve campagnes en reizen die hetzelfde kanaal delen
- Vereist voortdurende controle en aanpassing aangezien de overseinenportefeuille verandert

**Experience League:**

- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Overzicht van bedrijfsregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Reisbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)

### Optievergelijking

In de volgende tabel worden de drie implementatieopties vergeleken met de belangrijkste criteria.

| Criteria | Optie A: Eenvoudige gebeurtenis geactiveerd | Optie B: Voorwaardelijk met wachten | Optie C: Frequentiebeheer |
| --- | --- | --- | --- |
| Best voor | Onmiddellijke bevestigingen, erkenningen | Herstel van locaties wordt uitgesteld, voorwaardelijke reacties worden uitgesteld | Frequente gebeurtenisbronnen, omgevingen met meerdere reizen |
| Complexiteit | Laag | Gemiddeld | Medium-High (toegevoegd aan A of B) |
| Berichtvertraging | Seconden naar minuten | Minuten tot uren/dagen (configureerbare wachttijd) | Gelijk aan onderliggende optie (A of B) |
| Zelfomzettingscontrole | Nee | Ja (via voorwaarde- of uitstapcriteria) | Afhankelijk van onderliggende optie |
| Frequentiebeveiliging | Geen (tenzij gecombineerd met C) | Geen (tenzij gecombineerd met C) | Ja — kanaaluiteinden en terugslagsysteem |
| Journey Canvas Nodes | 3-4 (gebeurtenis, optionele voorwaarde, handeling, einde) | 5-7 (gebeurtenis, wacht, voorwaarde, vertakkingen, handeling, einde) | Gelijk aan A of B, plus de configuratie van de bedrijfsregel |
| Vereisten | Gebeurtenisschema, kanaaloppervlak, berichtinhoud | Alles bij optie A + opnemen van conversiegebeurtenis | Alle opties A of B + configuratie van de frequentieregel |

### Kies de juiste optie

Gebruik de volgende beslissingsrichtlijnen om de juiste implementatieoptie te selecteren.

1. **moet het bericht onmiddellijk zonder vertraging worden verzonden?** Als ja, begin met **Optie A**. Bevestigingsberichten, welkomste-mails en bevestigingen vereisen doorgaans geen wachttijd.

2. **zou de klant tijd moeten hebben om alvorens het bericht te ontvangen zelf-om te zetten?** Als ja, kies **Optie B**. Het verlaten van de winkelwagentje, doorbladeren verlaten, en de gebruiksgevallen van de proefvervaldatum profiteren van een wachttijdperiode die klanten toestaat om de actie op hun te voltooien.

3. **is de teweegbrengende gebeurtenis hoog-frequentie (komt veelvoudige tijden per zitting of per dag voor het zelfde profiel voor)?** Als ja, **Optie C** als bekleding bovenop Optie A of B. De meningen van het product, paginameningen, en onderzoeksgebeurtenissen kunnen hoge volumes van trekkers produceren die frequentiebescherming vereisen.

4. **zijn veelvoudige teweeggebrachte reizen en campagnes actief in de zandbak?** Als ja, voeg **Optie C** ongeacht gebeurtenisfrequentie toe om dwars-reis communicatie lading te beheren en kanaalvermoeidheid te verhinderen.

In de praktijk, gebruiken de meeste productieimplementaties Optie B + C voor het verlaten-stijl gebruiksgevallen (voorwaardelijk wachten met frequentiebeheer) en Optie A + C voor bevestiging-stijl gebruiksgevallen (onmiddellijk verzenden met frequentiebeheer als veiligheidsnet).

## Uitvoeringsfasen

De volgende fasen lopen door de implementatie van begin tot eind van gebeurtenis-teweeggebracht overseinen.

### Fase 1: Gebeurtenisschema en gegevensverzameling configureren

**de Functie van de Toepassing:** AEP: De Modellering van gegevens (F2), AEP: Gegevensbronnen &amp; Inzameling (F3)

**wat u zult vormen:** Het schema XDM ExperienceEvent dat de het teweegbrengen gebeurtenis, de dataset vangt die deze gebeurtenissen, en de pijpleiding van de gegevensinzameling in real time (SDK van het Web, Mobiele SDK, of Server API) opslaat die gebeurtenissen in AEP stroomt. Deze fase legt de gegevensbasis vast waarop de reis zal luisteren.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: het teweegbrengen gebeurtenistype**
>
>Welke gebeurtenis activeert het bericht? Het gebeurtenistype bepaalt de vereiste schemagebieden en de inzamelingsmethode.
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Commerce-gebeurtenis (toevoegen, kopen, uitchecken van winkelwagentjes) | Kwesties in verband met e-handel — afstoting van winkelwagentjes, postaankoop | Vereist Commerce-veldgroep met `productListItems` -, `cart` - `order` velden |
>| Web interaction event (paginaweergave, productweergave) | Bladeren door opgeven, activering van inhoud | Veldgroep Webdetails vereist met `webPageDetails`, `webInteraction` -velden |
>| Toepassingsgebeurtenis (toepassing installeren, verwijderen, in-app actie) | Mobiele betrokkenheidstriggers | Vereist mobiele SDK-implementatie en toepassingsveldgroep |
>| Systeemgebeurtenis (betalingsfout, wijziging van abonnement, statusupdate) | Operationele kennisgevingen | Vereist server-kant API of bronschakelaar om systeemgebeurtenissen in te voeren |
>| Gebeurtenis voor verzenden van formulier | Loodgeneratie, inschrijvingsbevestiging | Vereist een aangepaste veldgroep voor het vastleggen van formuliergegevensvelden |

>[!NOTE]
>
>**Besluit: De methode van de inzameling**
>
>Hoe wordt de activeringsgebeurtenis vastgelegd en gestreamd naar AEP?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Web SDK | Op het web gebaseerde gedragsgebeurtenissen (cart add, page views, form submission) | Vereist Web SDK-installatie op de website; gebeurtenissen worden in real-time gestreamd via Edge Network |
>| Mobile SDK | Mobiele toepassingsgebeurtenissen (app wordt geopend, in-app-handelingen, push-token-registratie) | Vereist Mobile SDK-integratie in de native app of React Native wrapper |
>| Edge Network Server-API | Server-side systeemgebeurtenissen (betalingsverwerking, abonnementsbeheer, backendtriggers) | Geen afhankelijkheid aan de clientzijde; gebeurtenissen verzonden vanuit de back-endsystemen van de organisatie |
>| Source-connector | Gebeurtenissen van externe systemen (CRM, marketingautomatisering, verouderde platforms) | Doorgaans op batchbasis; ondersteunt geen realtime triggermodus tenzij streaming mogelijk is |

**navigatie UI:** de Inzameling van Gegevens > Gegevensstromen > Nieuwe Datasstream (voor gegevensstroomopstelling); Schema&#39;s > creeer schema (voor gebeurtenisschema); Datasets > creeer dataset van schema (voor datasetverwezenlijking)

**Zeer belangrijke configuratiedetails:**

- Het gebeurtenisschema moet alle gebieden omvatten nodig voor de evaluatie van de reisvoorwaarde en berichtverpersoonlijking
- Voor de gegevensstroom moeten zowel [!DNL Adobe Experience Platform] - als [!DNL Adobe Journey Optimizer] -services zijn ingeschakeld
- De dataset moet voor het Profiel van de Klant in real time worden toegelaten zodat de gebeurtenissen met verenigde profielen worden geassocieerd
- Gebeurtenisgegevens moeten een identiteitsveld bevatten (e-mail, CRM-id, ECID) dat kan worden omgezet in een bekend profiel

**documentatie van Experience League:**

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Overzicht Edge Network Server API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Overzicht van het opnemen van streaming](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Fase 2: Identiteit en profiel configureren

**de Functie van de Toepassing:** AEP: Identiteit &amp; de Configuratie van het Profiel (F4)

**wat u zult vormen:** Identiteitsnaamruimten voor de herkenningstekens op de het teweegbrengen gebeurtenis, primaire identiteitsaanwijzing op het gebeurtenisschema, identiteit die regels voor dwars-apparatenresolutie, en een fusiebeleid voor profieleenmaking verbindt. Dit verzekert de het teweegbrengen gebeurtenis met een verenigd klantenprofiel wordt geassocieerd zodat kan de reis contactinformatie oplossen en het bericht leveren.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Primaire identiteit voor gebeurtenisschema**
>
>Welk identiteitsveld op de activeringsgebeurtenis moet fungeren als de primaire identiteit voor het oplossen van profielen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| E-mailadres | Gebeurtenissen van geverifieerde websessies of formulieren waarin e-mail wordt vastgelegd | Directe oplossing voor een aanspreekbare identiteit; eenvoudigste manier om de e-mail te verzenden |
>| CRM-id | Gebeurtenissen van geverifieerde systemen waarbij de CRM-id de primaire id is | Vereist het creëren van CRM ID namespace; het profiel moet een verbonden e-mail of een telefoon voor berichtlevering hebben |
>| ECID (Experience Cloud-ID) | Anonieme web- of app-gebeurtenissen waarbij geen geverifieerde identiteit beschikbaar is | Vereist identiteitsstitching om ECID aan een bekende identiteit te verbinden; de berichten kunnen niet alleen naar ECID worden verzonden |
>| Telefoonnummer | Gebeurtenissen van mobiele interacties of interacties via callcenter | Ondersteunt SMS-levering; vereist telefoonnaamruimte |

**navigatie UI:** Identiteiten > creëren identiteitskaart namespace; Schema&#39;s > Uitgezocht schema > Uitgezocht gebied > Identiteit > Reeks als primaire identiteit; Profielen > het beleid van de Fusie

**Zeer belangrijke configuratiedetails:**

- Anonieme gebeurtenissen (alleen ECID) kunnen geen berichtlevering activeren totdat de ECID is gekoppeld aan een bekende contactbare identiteit (e-mail, telefoon) via de identiteitsgrafiek
- Het samenvoegbeleid dat door AJO wordt gebruikt, moet consistent zijn met het beleid dat wordt gebruikt voor publieksevaluatie
- Voor web-based teweeggebracht overseinen, zorg ervoor de identiteitsgrafiek ECID aan voor authentiek verklaarde identiteiten door login gebeurtenissen verbindt

**documentatie van Experience League:**

- [Overzicht van naamruimten](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Koppelingsregels voor identiteitsgrafiek](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Fase 3: Kanaaloppervlakken instellen

**Functie van de Toepassing:** AJO: De Configuratie van het Kanaal

**wat u zult vormen:** de kanaaloppervlakte (vooraf ingesteld) die de verzendende infrastructuur voor het teweeggebrachte bericht bepaalt — subdomain delegatie, IP pool, afzender identiteit, antwoord-aan adres, unsubscribe behandeling, en kanaal-specifieke geloofsbrieven (leverancier van SMS, duw certificaten). Er moet een geldig kanaaloppervlak zijn voordat de berichtinhoud kan worden gemaakt of voordat reizen kunnen worden gepubliceerd.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Het kanaal van het Bericht**
>
>Welk kanaal zal het teweeggebrachte berichtgebruik?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| E-mail | Meest getriggerde gevallen voor berichtgebruik — herstel van wachttijden, bevestigingen, onboarding | Vereist subdomain delegatie, IP pool, afzenderconfiguratie; steunt rijke inhoud en verpersoonlijking van HTML |
>| Sms | Tijdgevoelige meldingen, beknopte waarschuwingen, publiek met hoge SMS-service | Vereist integratie van SMS-provider (Sinch, Twilio, Infobip); onderworpen aan tekenbeperkingen en strengere toestemmingsvereisten |
>| Pushmelding | Betrokkenheid bij mobiele apps, opnieuw inschakelen van gebruikers van apps | Vereist een push-credentieconfiguratie (APNs voor iOS, FCM voor Android); de gebruiker moet de app hebben geïnstalleerd met pushtechnologie ingeschakeld |
>| Meerdere kanalen | Uitgebreide servicestrategie met kanaalvoorkeur of fallback-logica | Vereist meerdere kanaaloppervlakken; kanaalselectie kan worden beheerd via knooppunten voor reisvoorwaarden |

>[!NOTE]
>
>**Besluit: De methode van de subdomeindelegatie (e-mail)**
>
>Hoe moet het e-mailverzendende subdomein worden gedelegeerd aan Adobe?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Volledige delegatie | De organisatie wil Adobe alle DNS verslagen voor het verzendende subdomain beheren | Eenvoudigste installatie: Adobe beheert automatisch SPF-, DKIM- en DMARC-records |
>| CNAME-delegatie | De organisatie wil DNS controle terwijl het richten aan de infrastructuur van Adobe handhaven | Vereist handmatig DNS-recordbeheer; biedt meer organisatorische controle over DNS |

**navigatie UI:** Beleid > Kanalen > Subdomeinen (voor subdomeinopstelling); Beleid > Kanalen > IP pools (voor IP poolconfiguratie); Beleid > Kanalen > de oppervlakten van het Kanaal > Create oppervlakte (voor oppervlakverwezenlijking)

**Zeer belangrijke configuratiedetails:**

- De controle van subdomain en DNS de propagatie kunnen tot 48 uren vergen
- Nieuwe IP-pools vereisen een opwarmingsplan (2-4 weken geleidelijke volumetoename)
- Een klik-op-lijst-ophef kopteksten voor e-mailnaleving configureren
- Voor SMS, vorm de leveranciersgeloofsbrieven alvorens de het kanaaloppervlakte van SMS te creëren
- Configureer voor push APN&#39;s en FCM-referenties voordat u het oppervlak van het drukkanaal maakt

**documentatie van Experience League:**

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [IP-pools maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [Kanaaloppervlakken instellen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)

### Fase 4: Berichtinhoud maken

**Functie van de Toepassing:** AJO: De Authoring van het bericht

**wat u zult vormen:** de berichtinhoud die door de reis, met inbegrip van lay-outontwerp, verpersoonlijkingstkens zal worden geleverd gebruikend profiel en gebeurtenisattributen, voorwaardelijke inhoudsblokken, herbruikbare fragmenten (kopballen, footers, wettelijke disclaimers), en inhoudsvoorproef en het testen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: De benadering van de inhoud**
>
>Hoe moet de inhoud van het bericht worden gemaakt?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Starten met een bestaande sjabloon | Er bestaan organisatiesjablonen en er is consistentie van merken vereist | Snelste weg aan inhoudsverwezenlijking; verzekert brandnaleving; malplaatjeveranderingen verspreiden zich aan nieuwe berichten |
>| Ontwerpen vanaf nul in e-mail-Designer | Aangepaste indeling vereist voor dit specifieke getriggerde bericht | Volledige creatieve controle; visuele editor voor slepen en neerzetten; langzamer maar flexibeler |
>| HTML importeren | Inhoud is ontworpen door een extern team of agentschap en wordt geleverd als HTML | Vereist HTML-codeerexpertise; biedt mogelijk geen volledige ondersteuning voor alle Designer-functies voor e-mail |

>[!NOTE]
>
>**Besluit: De verpersoonlijking van de gebeurtenis**
>
>Welke gebeurtenisgegevens zouden in de berichtinhoud moeten worden gebruikt?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Contextafhankelijke kenmerken van gebeurtenissen | Het bericht moet gegevens bevatten van de activeringsgebeurtenis (productnaam, tekenwaarde, formuliervelden) | Contextgebonden gebeurteniskenmerken gebruiken in de personalisatie-editor; gegevens zijn afkomstig van de activerende gebeurtenislading |
>| Profielkenmerken | Het bericht moet gegevens op profielniveau bevatten (voornaam, loyaliteitslaag, locatie) | Profielkenmerken gebruiken via XDM-paden (bijv. `profile.person.name.firstName`); gegevens komen uit het verenigde profiel |
>| Zowel gebeurtenis- als profielkenmerken | Het bericht moet de gebeurteniscontext combineren met profielpersonalisatie | Meest gangbare aanpak voor getriggerde berichten; zorgt voor zowel relevantie (gebeurtenis) als personalisatie (profiel) |

**navigatie UI:** het Beheer van de Inhoud > de Malplaatjes van de Inhoud > doorbladert (voor malplaatjeselectie); Campagne of de actie van de Reis > geeft inhoud uit > E-mail Designer (voor inhoudsontwerp); Selecteer tekstcomponent > het pictogram van Personalization (voor het toevoegen van verpersoonlijking)

**Zeer belangrijke configuratiedetails:**

- Contextgebonden kenmerken gebruiken om zich aan te passen aan de gegevens van de activerende gebeurtenis (bijvoorbeeld productnaam, tekenwaarde)
- Profielkenmerken gebruiken voor naam, voorkeuren en loyaliteitsgegevens
- Configureer voorwaardelijke inhoudsblokken om de inhoud per profielsegment of kenmerk te variëren (bijvoorbeeld verschillende CTA voor loyaliteitsleden)
- Herbruikbare fragmenten maken voor kopteksten, voetteksten en juridische disclaimes die via getriggerde berichten worden gedeeld
- Voorvertonen met meerdere testprofielen om te controleren of de weergave op de juiste wijze is aangepast
- Proefdrukken verzenden naar interne belanghebbenden voordat de reis wordt gepubliceerd

**documentatie van Experience League:**

- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)

### Fase 5: De reis maken en configureren

**Functie van de Toepassing:** AJO: Journey Orchestration, AJO: Frequentie &amp; Bedrijfs Regels (Optie C), AJO: Conflict &amp; Prioritair Beheer

**wat u zult vormen:** de reis die op de het teweegbrengen gebeurtenis luistert en berichtlevering organiseert. Dit is de kernimplementatiefase waarin het reiscanvas is ontworpen met het knooppunt voor gebeurtenisinvoer, voorwaardenknooppunten, wachtstappen (voor Option B), knooppunten voor berichtactie en afsluitcriteria. Deze fase heeft ook betrekking op frequentiebeheer (optie C) en conflict/prioriteitsconfiguratie.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Regels van de terugkeer**
>
>Kan een profiel deze reis opnieuw ingaan als de het teweegbrengen gebeurtenis opnieuw voorkomt?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Opnieuw invoeren toestaan (met afkoelingsmethode) | De gebeurtenis kan rechtmatig opnieuw plaatsvinden en elk voorval rechtvaardigt een bericht (elke buitengebruikstelling van een winkelwagen moet bijvoorbeeld een herstelbericht activeren) | Stel een afkoelingsperiode in (minimaal 5 minuten) om te voorkomen dat dubbele gebeurtenissen snel opnieuw worden binnengebracht. Doorgaans loopt de afkoelingsperiode van 1 uur tot 72 uur |
>| Geen terugkeer | Het bericht mag slechts eenmaal per profiel worden verzonden, ongeacht de terugkerende gebeurtenis (bijv. welkomstbericht na eerste registratie) | Profiel is definitief uitgesloten na eerste voltooiing van de reis; geschikt voor eenmalige levenscyclusberichten |

>[!NOTE]
>
>**Besluit: Wacht duur (Optie B slechts)**
>
>Hoe lang moet de reis wachten alvorens voorwaarden te evalueren en het bericht te verzenden?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Korte wachttijd (1-4 uur) | Gebruiksgevallen met een hoge urgentie, zoals het verlaten van het winkelwagentje, waar onmiddellijke follow-up effectief is | Hoger berichtvolume; kan sommige zelf-omzetters vangen; best voor hoogwaardige kartterugwinning |
>| Medium-wachttijd (12-24 uur) | Gebruiksgevallen met een matige urgentie, zoals het verlaten van een browser of het aangaan van content | Evenwichtige benadering; vermindert onnodige verzendingen terwijl het handhaven van relevantie |
>| Lange wachttijd (2-7 dagen) | Gebruiksgevallen met een lage urgentie, zoals herinneringen voor het verlopen van de proefversie of periodieke controles | Lager berichtvolume; groter risico om contextafhankelijke relevantie te verliezen |
>| Aangepaste datum/tijd | Gebruik zaken die aan een bepaalde datum zijn gebonden (verzend bijvoorbeeld 3 dagen vóór vervaldatum van de proefversie) | Wacht tot een berekende datum/tijd; gebruikt de redacteur van de douaneuitdrukking |

>[!NOTE]
>
>**Besluit: De criteria van de uitgang**
>
>Onder welke voorwaarden moet een profiel uit de reis worden verwijderd voordat de berichtactie wordt uitgevoerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Conversiegebeurtenis (bijv. aankoop voltooid) | Winkelen of bladeren in stopzetting waar conversie het doel is | Profiel wordt automatisch afgesloten wanneer de conversiegebeurtenis wordt gedetecteerd; schoonste aanpak voor optie B |
>| Wijziging van het lidmaatschap voor het publiek | Profiel moet worden afgesloten als ze een in aanmerking komend segment verlaten | Vereist een door streaming geëvalueerd publiek dat in bijna real time bijwerkt |
>| Time-out reis (maximaal 91 dagen) | Standaardgedrag — profiel wordt afgesloten na de maximale reisduur | Veiligheidsnet; mag niet het primaire uitreismechanisme zijn voor kortstondige getriggerde reizen |
>| Geen expliciete afsluitcriteria | Eenvoudige bevestigingen (optie A) waarbij elk in aanmerking komend profiel het bericht moet ontvangen | Profiel wordt op natuurlijke wijze afgesloten na berichtactie en eindknooppunt |

>[!NOTE]
>
>**Besluit: Het bestuur van de Frequentie (Optie C)**
>
>Hoeveel getriggerde berichten zou een profiel per tijdspanne moeten ontvangen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Kanaalspecifieke uiteinden (bijvoorbeeld 3 e-mails/week, 1 sms/dag) | Verschillende kanalen hebben verschillende vermoeiingsdrempels | Aanbevolen benadering; eerbiedigt het indringingsniveau van elk kanaal |
>| Globale limiet (bv. 5 berichten per week op alle kanalen) | Vereenvoudigd bestuur voor alle communicatietypen | Gemakkelijker te beheren maar minder genanceerd; kan minder indringende kanalen te veel beperken |
>| Alleen inkopen op reis-niveau | Regelgeving inzake frequentie vereist voor deze specifieke reis, maar niet voor de hele organisatie | Eenvoudigste implementatie; biedt geen bescherming tegen vermoeidheid tijdens de reis |

**navigatie UI:** De Schavens > creëren de Reizen (voor reisverwezenlijking); Het canvas van de Reis > de gebeurtenisactiviteit van de Belemmering (voor gebeurtenisingang); Het canvas van de Reis > &quot;Wacht&quot;activiteit (voor voorwaardenconfiguratie); De eigenschappen van de Reis > van de Belemmering (voor uitgangsconfiguratie); Het beleid > Bedrijfs regels > leidt regel (voor frequentiecappen)

**Zeer belangrijke configuratiedetails:**

- Vorm de reisgebeurtenis door het gebeurtenisschema te selecteren en de kwalificerende voorwaarden te bepalen
- Voor Optie B, voeg de wachttijdknoop onmiddellijk na de gebeurtenisingang en vóór om het even welke voorwaardevaluatie toe
- Configureer voorwaardenknooppunten met behulp van profielkenmerken, gebeurtenisgegevens of publiekslidmaatschapscontroles
- Verbind de knoop van de berichtactie met de kanaaloppervlakte en authentieke inhoud van Fases 3 en 4
- De tijd voor de reis instellen op een geschikte duur (korter dan 91 dagen voor getriggerde reizen)
- Voor Optie C, creeer frequentieregels via Beleid > Bedrijfs regels alvorens de reis te publiceren
- Een prioriteitsscore toewijzen aan de reis als andere campagnes of reizen gericht zijn op overlappende doelgroepen

**waar de opties uiteenlopen:**

**voor Optie A (eenvoudige gebeurtenis-teweeggebracht):**
Het canvas van de reis is minimaal: gebeurtenisingang > facultatieve toestemming/geschiktheidsvoorwaarde > berichtactie > eind. Geen wachtstappen of conversiecontroles. Stel regels voor opnieuw invoeren in op basis van het feit of de gebeurtenis telkens een bericht moet genereren wanneer dit plaatsvindt.

**voor Optie B (Voorwaardelijk met Wacht):**
Voeg een wachttijdknooppunt toe na gebeurtenisinvoer. Voeg na de wachttijd een voorwaardenknooppunt toe om te controleren op conversie (controleer bijvoorbeeld of de gebeurtenis `commerce.purchases` heeft plaatsgevonden na het invoeren van de reis) of gebruik afsluitcriteria om omgezette profielen automatisch te verwijderen. Vertakking aan de berichtactie op de &quot;niet geconverteerde&quot;weg en aan een eindknoop op de &quot;omgezette&quot;weg.

**voor Optie C (Frequency Governance):**
Vorm organisatie-vlakke frequentiecaps via Beleid > Bedrijfs regels alvorens te publiceren. Reisniveaure-ineenstorting in de reis eigenschappen plaatsen. U kunt desgewenst een prioriteitsscore toewijzen via de eigenschappen van de reis om te bepalen welke communicatie wint wanneer hoofdletters worden bereikt. Deze optie kan boven op optie A of optie B worden toegepast.

**documentatie van Experience League:**

- [Een reis maken](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journeyeigenschappen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Algemene gebeurtenissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [Voorwaardeactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wachtactiviteit](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Een bericht toevoegen tijdens een rit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Afsluitingscriteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Reisbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Mogelijke conflicten identificeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)

### Fase 6: De reis testen en implementeren

**Functie van de Toepassing:** AJO: Journey Orchestration

**wat u zult vormen:** de wijzebevestiging van de Test om het reis te verifiëren gedraagt zoals verwacht met testprofielen, die door reispublicatie worden gevolgd om het levend te maken.

**navigatie UI:** het canvas van de Reis > de wijze van de Test knevel (voor het testen); Het canvas van de Reis > publiceert (voor plaatsing)

**Zeer belangrijke configuratiedetails:**

- De testmodus op het canvas inschakelen om gebeurtenistriggers met testprofielen te simuleren
- Testprofielen selecteren met geldige kanaalcontactgegevens (e-mailadres, telefoonnummer)
- De testgebeurtenis activeren en controleren of het testprofiel het verwachte pad doorloopt
- Voor Optie B, verifieer dat de wachtstap correct gedraagt en die voorwaardevaluatie de verwachte vertakking veroorzaakt
- Verifieer dat de verpersoonlijkingstokens correct in het testbericht teruggeven
- Na succesvolle tests publiceert u de reis om deze live te zetten
- De reisstatus en de initiële cijfers voor profielinvoer na publicatie controleren

**documentatie van Experience League:**

- [Uw reis testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [De reis publiceren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Fase 7: Prestaties bewaken en rapporteren

**de Functie van de Toepassing:** AJO: Rapportering &amp; Analyse van Prestaties, S4: Controle &amp; Observability, S5: Rapportering &amp; Analyse

**wat u zult vormen:** Levende en historische reisrapporten voor levering en betrokkenheidscontrole, platformalarm voor gebeurtenisopname en de mislukkingen van de reisverwerking, en naar keuze CJA werkruimten voor diepere dwars-kanaalanalyse van teweeggebrachte overseinendoeltreffendheid.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Meldend diepte**
>
>Hoeveel rapportage-analyse is nodig voor dit geval?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alleen systeemeigen AJO-rapporten | De operationele controle van de leveringscijfers is voldoende | Beschikbaar onmiddellijk; verzonden, geleverde, teruggestuurde, geopende en aangeklikte omslagen; geen extra configuratie vereist |
>| Integratie van AJO native + CJA | Er is behoefte aan kanaalanalyse, conversie-toewijzing en trendanalyse | Vereist CJA-verbinding en gegevensweergave voor AJO-gegevenssets; biedt uitgebreidere analytische mogelijkheden |

**navigatie UI:** de Reizen > Uitgezochte reis > Levend rapport (voor levende controle); De Reizen > Uitgezochte reis > Alle tijdrapport (voor historische analyse); Alarm > de Regels van de Waarschuwing > Abonneren (voor waakzame configuratie)

**Zeer belangrijke configuratiedetails:**

- Heb toegang tot het reis levende rapport tijdens actieve uitvoering om profielingangen, uitgang en leveringsmetriek te controleren
- Herzie het historische rapport nadat de reis voor voldoende tijd actief is geweest om zinvolle gegevens te verzamelen
- Waarschuwingen configureren voor fouten bij uitvoering van de bronstroom (opnemen van gebeurtenissen) en vertragingen bij de verwerking van de reis
- Voor CJA-integratie moet u ervoor zorgen dat de CJA-verbinding gegevens over gebeurtenissen uit de AJO-ervaring bevat (Gegevensset over feedbackgebeurtenis, Gegevensset over ervaringen met e-mailtracking)

**documentatie van Experience League:**

- [Journaal live](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [Werken met Customer Journey Analytics](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/report-cja-manage)
- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

## Implementatieoverwegingen

Deze sectie behandelt gidsen, gemeenschappelijke valkuilen, beste praktijken, en handelsbesluiten voor gebeurtenis-teweeggebrachte overseinenimplementaties.

### Guardrails en limieten

De volgende platformgidsen en grenzen zijn van toepassing op gebeurtenis-teweeggebrachte overseinenimplementaties.

- **de unitaire gebeurtenisproductie:** Maximum 5.000 gebeurtenissen per seconde per zandbak voor unitaire gebeurtenisreizen - [&#x200B; de guardrails van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **Levende reisgrens:** Maximum 500 levende reizen per zandbak - [&#x200B; de guardrails van Journey Optimizer &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- **de canvasgrens van de Reis:** Maximum 50 activiteiten per wegcanvas
- **timeout van de Reis:** Maximale reisduur is 91 dagen (globale onderbreking)
- **re-entry koeldown:** minimum re-entry koeldown is 5 minuten
- **configuraties van het GLB van de Frequentie:** Maximum 10 die configuraties begrenzen per zandbak
- **de oppervlakten van het Kanaal:** Maximum 10 kanaaloppervlakten per kanaaltype per zandbak
- **Streaming opname:** Maximum 20.000 verslagen per seconde per de verbinding van HTTP — [&#x200B; Ingestiegaranties &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)
- **Berekende attributen:** Maximum 25 gegevens verwerkte attributen per zandbak — [&#x200B; de gegevens verwerkte attributengidsen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview#guardrails)
- **de fragmenten van de Inhoud:** Maximum 30 inhoudsfragmenten per bericht
- **Levend rapport verfrist zich:** Levende rapporten verfrissen zich om de 60 seconden en tonen de laatste 24 uren van gegevens
- **Historische rapportlatentie:** Historische (alle tijd) de rapporten kunnen tot 2 uren nemen om volledig te bevolken na uitvoeringseinden

### Veelvoorkomende valkuilen

Houd rekening met de volgende algemene problemen bij het implementeren van berichten die door gebeurtenissen worden geactiveerd.

- **Anonieme gebeurtenissen zonder identiteitsresolutie:** het teweegbrengen gebeurtenissen die slechts een ECID (anonieme koekjesidentiteitskaart) dragen kan niet aan een aanspreekbaar profiel voor berichtlevering oplossen. Zorg ervoor dat de activeringsgebeurtenis een geverifieerde identiteit bevat of dat de identiteitsgrafiek de ECID koppelt aan een bekend contact. Zonder identiteitsresolutie, gaan de profielen de reis in maar ontbreken bij de stap van de berichtlevering.

- **Ontbrekende omzettingsgebeurtenis voor de voorwaardecontroles van Optie B:** als de omzettingsgebeurtenis (b.v., aankoop) niet in AEP wordt opgenomen of niet met de zelfde profielidentiteit zoals de het teweegbrengen gebeurtenis wordt geassocieerd, zal de voorwaardencontrole verkeerd evalueren als &quot;niet omgezet&quot;en verzendt onnodige berichten. Controleer of conversiegebeurtenissen realtime naar AEP stromen en deel een identiteit met de activeringsgebeurtenis.

- **over het algemeen permissieve re-entry regels:** Toestaan re-ingang zonder een inzamelingsperiode op high-frequency gebeurtenisbronnen kan het zelfde profiel veroorzaken om veelvoudige berichten binnen notulen te ontvangen. Stel altijd een terugboeking in die overeenkomt met de zakelijke context (bijvoorbeeld 4-uurs afkoelingsregeling voor het weglaten van winkelwagentjes, 24-uursafbeelding voor het weglaten van bladeren).

- **wacht de wangroepering van de tredetijdzone:** wacht stappen in UTC door gebrek. Als de reis profielen over veelvoudige tijdzones richt en wacht zich op de lokale tijd van de ontvanger zou moeten richten, vorm dienovereenkomstig de timezone montages op de reis.

- **frequentiekappen die met andere campagnes in conflict brengen:** organisatie-vlakke frequentiekappen zijn op alle campagnes en reizen van toepassing. Een nieuwe getriggerde reis kan worden onderdrukt als profielen hun maximum reeds hebben bereikt van andere actieve campagnes. Controleer het suppressietarief en pas prioriteitsscores aan om ervoor te zorgen dat belangrijke getriggerde berichten prioriteit krijgen.

- **publiceer de Reis mislukking toe te schrijven aan ontbrekende gebiedsdelen:** Elke tak in het wegcanvas moet met een eindactiviteit eindigen. Alle actieknooppunten moeten verwijzen naar geldige kanaaloppervlakken met actieve berichtinhoud. Verifieer alle gebiedsdelen alvorens te publiceren.

### Aanbevolen procedures

Volg deze aanbevelingen voor succesvolle gebeurtenis-teweeggebrachte overseinenimplementaties.

- **Begin eenvoudig, dan herhaling:** Begin met Optie A voor nieuwe teweeggebrachte gevallen van het overseinengebruik. Voeg wachttijd en voorwaardelogica (Optie B) slechts na het bevestigen van de gebeurtenispijpleiding en berichtlevering toe. Voeg frequentiebeheer (Optie C) toe wanneer de veelvoudige teweeggebrachte reizen actief zijn.

- **de uitgangscriteria van het gebruik in plaats van voorwaardenknopen voor omzetcontroles:** de criteria van de Uitgang verwijderen automatisch profielen uit de reis wanneer een kwalificerende gebeurtenis (b.v., aankoop) voorkomt, eliminerend de behoefte aan een expliciete voorwaardenknoop na de wachttijdstap. Dit levert een schoner reiscanvas en responsievere omzettingsopsporing op.

- **Test met echte gebeurtenisgegevens in een ontwikkelingszandbak:** de testwijze van het gebruik met daadwerkelijke gebeurtenislading (niet alleen testprofielen) om die gebieden van het gebeurtenisschema, verpersoonlijkingstokens, en voorwaardenuitdrukkingen te bevestigen werken correct met productie-als gegevens.

- **vastgestelde gebeurtenis-specifieke re-ingangskoelingen:** pas de inzamelingsperiode aan de bedrijfscontext van de het teweegbrengen gebeurtenis aan. Voor ritten voor het achterlaten van auto&#39;s wordt doorgaans een 4-24 uur oude koeltijd gebruikt; bevestigingstrajecten kunnen onmiddellijk opnieuw worden binnengebracht; bij instapreizen moet het opnieuw betreden volledig worden voorkomen.

- **controleert het suppressietarief als gezondheid metrisch:** als het suppressietarief (profielen die maar geen berichten wegens frequentiekapitalen of voorwaarden ontvangen) 30-40% overschrijden, herzie of de kappen te restrictief zijn of of de het teweegbrengen gebeurtenis te breed wordt bepaald.

- **reizen van de versie in plaats van levende degenen uit te geven:** Een levende reis kan niet direct worden uitgegeven. Maak een nieuwe versie door de rit te dupliceren, wijzigingen aan te brengen, vervolgens de oude versie te stoppen en de nieuwe te publiceren. Dit voorkomt verstorende profielen die momenteel op reis zijn.

- **omvat een reserve/standaardweg in voorwaardenknopen:** vormt altijd een (anders) weg standaard in voorwaardenknopen om onverwachte profielstaten te behandelen. Profielen die niet overeenkomen met een voorwaardelijke vertakking moeten netjes worden afgesloten en niet vastlopen.

### Handelsbesluiten

Overweeg de volgende compromissen wanneer het ontwerpen van uw gebeurtenis-teweeggebrachte overseinenimplementatie.

>[!NOTE]
>
>**handel-off: De snelheid van het bericht vs. berichtrelevantie**
>
>De directe berichtlevering (Optie A) maximaliseert snelheid maar kan berichten naar klanten verzenden die zelf-omgezet zouden hebben. Vertraagde voorwaardelijke levering (Optie B) verbetert relevantie door uit zelfomzetters te filtreren maar introduceert latentie die urgentie kan verminderen.
>
>- **Optie A komt voor:** Snelheid, eenvoud, bevestiging-stijl gebruiksgevallen waar elke gebeurtenis een bericht rechtvaardigt
>- **Optie B begunstigt:** Relevantie, verminderde berichtmoeheid, verlaten-stijl gebruiksgevallen waar zelfomzetting gemeenschappelijk is
>- **Aanbeveling:** Optie A van het Gebruik voor transactie en bevestigingsberichten waar de snelheid de primaire waarde is. Gebruik Optie B voor herstel- en re-betrokkenheidsberichten wanneer de relevantie groter is dan de snelheid. Experimenteer met wachttijden om de optimale balans voor elk geval van gebruik te vinden.

>[!NOTE]
>
>**handel-off: De bescherming van de frequentie tegenover berichtdekking**
>
>Strikte frequentiecaps (Option C) voorkomen vermoeidheid, maar kunnen belangrijke getriggerde berichten onderdrukken wanneer de profielen dicht bij hun hoofdletter staan. De toegelaten of geen maximum maximaliseert dekking maar het risico overseinen en kanaalmoeheid.
>
>- **Strikte kappen gunnen:** De ervaring van de Klant, merkreputatie, leverbaarheid (minder spamklachten)
>- **Toestemmende kappen gunnen:** de dekking van het Bericht, omzettingskansen, vermijdend gemiste trekkers
>- **Aanbeveling:** begin met industrie-standaardkappen (3-5 e-mails/week, 1-2 SMS/week, 2-3 duw/dag) en aanpassen gebaseerd op betrokkenheidsmetriek en unsubscribe tarieven. Wijs hogere prioritaire scores aan teweeggebrachte berichten toe zodat winnen zij over partijcampagnes wanneer kappen worden bereikt.

>[!NOTE]
>
>**handel-off: De eenvoud van de reis tegenover de verfijning van de reis**
>
>Eenvoudige reizen (weinig knooppunten, geen vertakking) zijn eenvoudiger te maken, testen en onderhouden, maar bieden beperkte contextafhankelijke aanpassingen. De geavanceerde reizen (veelvoudige voorwaarden, vertakkende wegen, segmentcontroles) laten meer genuanceerde reacties toe maar verhogen ingewikkeldheid en risico van fouten.
>
>- **Eenvoudige reizen begunstigen:** Snellere implementatie, gemakkelijkere zuivering, lagere onderhoudslast
>- **Verfijnde reizen begunstigen:** preciezer gericht, betere verpersoonlijking, verminderd onnodig verzendt
>- **Aanbeveling:** Begin met de eenvoudigste reis die aan het bedrijfsvereiste voldoet. Voeg incrementele complexiteit toe op basis van prestatiegegevens. Een eenvoudige reis die betrouwbaar werkt is waardevoller dan een complexe reis met onopgespoorde fouten.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende informatie over de mogelijkheden die in deze implementatie worden gebruikt.

### Reisorkest

- [Aan de slag met reizen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/journey)
- [Een reis maken](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Journeyeigenschappen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-properties)
- [Algemene gebeurtenissen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/general-events)
- [kwalificatiegebeurtenissen voor het publiek](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/audience-qualification-events)
- [Voorwaardeactiviteit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/condition-activity)
- [Wachtactiviteit](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/wait-activity)
- [Een bericht toevoegen tijdens een rit](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/journeys-message)
- [Afsluitingscriteria](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/exit-criteria)
- [Reisbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/entry-management)
- [Uw reis testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/testing-the-journey)
- [De reis publiceren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/orchestrate-journeys/create-journey/publishing-the-journey)

### Kanaalconfiguratie

- [Aan de slag met e-mailconfiguratie](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/channels/email/configure-email/get-started-email-config)
- [Subdomeinen delegeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/delegate-subdomain)
- [IP-pools maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-pools)
- [IP-opwarmingsplannen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/ip-warmup/ip-warmup-gs)
- [Instellingen van e-mailoppervlak](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/configure-email/email-settings)
- [SMS-kanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/configure-sms/sms-configuration)
- [Pushmeldingskanaal configureren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/configure-push/push-configuration)
- [Onderdrukkingslijst beheren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/monitor-reputation/manage-suppression-list)

### Authoring en personalisatie van berichten

- [Een e-mail maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/create-email)
- [E-mailinhoud ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/email/design-email/design-emails)
- [Aanpassing toevoegen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalize)
- [Personalization-syntaxis](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/personalization-syntax)
- [Helpfuncties](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/functions/functions)
- [Dynamische inhoud](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/personalization/dynamic-content)
- [Werken met inhoudssjablonen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/content-templates/content-templates)
- [Werken met inhoudsfragmenten](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/fragments/content-fragments)
- [Inhoud voorvertonen en testen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/content-management/preview-test/preview-test)
- [Een SMS-bericht maken](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/sms/create-sms)
- [Een pushmelding ontwerpen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/channels/push/design-push)

### Frequentie en bedrijfsregels

- [Frequentieregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/frequency-rules)
- [Overzicht van bedrijfsregels](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/business-rules/business-rules)
- [API voor uitlijnen](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/configuration/channel-surfaces/capping)

### Conflict en prioritair beheer

- [Aan de slag met conflict- en prioriteitsbeheer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/gs-conflict-prioritization)
- [Mogelijke conflicten identificeren](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/conflicts)
- [Prioriteitsscores](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/priority-scores)
- [Afbakening van reizen en arbitrage](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/conflict-prioritization/journey-capping)

### Rapportage en prestaties

- [Journaal live](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-live-report)
- [Journaal algemeen rapport](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reports/journey-global-report-cja)
- [AJO + CJA-integratiehandleiding](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/reporting/channel-report/cja-ajo)

### Verzameling en inname van gegevens

- [Overzicht van Web SDK](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/home)
- [Overzicht van Mobile SDK](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/mobile-sdk/overview)
- [Overzicht Edge Network Server API](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network-server-api/overview)
- [Gegevensstromen configureren](https://experienceleague.adobe.com/en/docs/experience-platform/datastreams/configure)
- [Overzicht van het opnemen van streaming](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/streaming/overview)

### Gegevensmodellering en -schema&#39;s

- [XDM System, overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/home)
- [Grondbeginselen van de schemacompositie](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/schema/composition)

### Identiteit en profiel

- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
- [Overzicht van naamruimten](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/namespaces)
- [Koppelingsregels voor identiteitsgrafiek](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-linking-logic)
- [Profieloverzicht](https://experienceleague.adobe.com/en/docs/experience-platform/profile/home)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/en/docs/experience-platform/profile/merge-policies/overview)

### Segmentering en publiek

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/segment-builder)
- [Streaming segmentering](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/methods/streaming-segmentation)

### Beheer van gegevens en toestemming

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/home)
- [Overzicht van labels voor gegevensgebruik](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/labels/overview)
- [Toestemming en voorkeuren, veldgroep](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/field-groups/profile/consents)
- [Toestemming in Journey Optimizer](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/privacy/consent/consent-restricted)

### Berekende kenmerken

- [Overzicht van berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/overview)
- [Gebruikershandleiding voor berekende kenmerken](https://experienceleague.adobe.com/en/docs/experience-platform/profile/computed-attributes/ui)

### Controle en waarneming

- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/en/docs/experience-platform/observability/alerts/overview)
- [Overzicht van observatiegegevens](https://experienceleague.adobe.com/en/docs/experience-platform/observability/home)

### Beveiligingsmechanismen

- [Journey Optimizer guardrails](https://experienceleague.adobe.com/en/docs/journey-optimizer/using/get-started/guardrails)
- [Garanties voor realtime klantprofiel](https://experienceleague.adobe.com/en/docs/experience-platform/profile/guardrails)
- [Ingestiegrepen](https://experienceleague.adobe.com/en/docs/experience-platform/ingestion/guardrails)

### Zelfstudies en hulplijnen

- [Een zelfstudie over reizen maken](https://experienceleague.adobe.com/nl/docs/journey-optimizer/using/orchestrate-journeys/create-journey/journey-gs)
- [Web SDK installeren](https://experienceleague.adobe.com/en/docs/experience-platform/web-sdk/install/overview)
