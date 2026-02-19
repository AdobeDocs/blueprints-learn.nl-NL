---
title: AJO B2B Betaalde Media Controller
description: Prioriteit van campagnes en activering van accounts naar betaalmedia-bestemmingen
solution: Journey Optimizer B2B Edition
source-git-commit: dff5608af92fa1140419d6834d8374df75de98d3
workflow-type: tm+mt
source-wordcount: '1392'
ht-degree: 0%

---

# Overzicht

De teams van de marketing die B2B betaalde media bij schaal in werking stellen staan voor een terugkerend probleem: **de rekeningen eindigen omhoog in veelvoudige campagnes tegelijkertijd** (persona, categorierusbewustzijn, oplossing-geleid, nastreven), die overseinen, oorzaken publieksvermoeidheid, en forceert handwerk-uploads, uitsluitingen, en onderdrukking-over LinkedIn Overeenkomst (de Bestemming van de Rekening). Zonder **watervalprioriteit** en **geautomatiseerde campagnetaak**, is er geen enige plaats om te beslissen welke rekening krijgt welk bericht, en de verrichtingen niet schrapen.

Het **Betaalde Controlemechanisme van Media** is een perfecte oplossing in het richten van dit probleem. Het gebruikt **Adobe Journey Optimizer B2B edition (AJO B2B)** en **Adobe Experience Platform (AEP)** samen: één **rekeningsreis** leest een gekwalificeerd-rekeningspubliek van Real-Time CDP, past **spleet-weg (waterval) logica** toe om elke rekening aan precies één campagnerij toe te wijzen, en **activeert direct elke weg** aan betaalde media bestemmingen (&lbrace;10.g. kedIn Gelijke Soorten publiek **) - zonder handlijsthandboeien.** Het resultaat is precisiecontrole, minder overlapping, en een herhaalbaar patroon voor multichannel B2B betaalde media orchestratie.

## Gebruiksscenario: Het verhaal van een markeerteken: Waarom een controller belangrijk is

*Maya leidt betaalde media voor een globaal B2B merk. Haar team voert tientallen campagnes uit: bewustwording bij de basis, categorieintentie (Reis, Gegevens, Inhoud), programma&#39;s met oplossingsleiding, persoonlijke campagnes en must-win-activiteiten. Ze heeft een probleem.*

**het probleem:** de zelfde rekeningen verschijnen in veelvoudige campagnes. Een reisaccount met veel bedoelingen staat ook op een brede bewustmakingslijst. Een achtervolgingsaccount krijgt nog steeds persoonlijke advertenties. Uploads en uitsluitingen van lijsten worden handmatig uitgevoerd. Telkens als de verkoop een &quot;moet-win&quot;lijst of een nieuwe persoonscampagne bijwerkt, voert haar team publiek opnieuw uit, maakt overlappingen in spreadsheets, en heruploadt aan LinkedIn en andere platforms. Het is traag, foutgevoelig en schaalt niet.

**wat zij wil:** Één plaats waar elke gekwalificeerde rekening eens wordt geëvalueerd, aan de *meest relevante* campagne toegewezen gebruikend duidelijke prioritaire regels (waterval), en verzonden naar juiste betaalde media bestemming-automatisch bestemming-wordt. Geen handmatige lijsthandgrepen. Wanneer de gegevens of de strategie veranderen, herevalueert het systeem en beweegt rekeningen tussen campagnes zonder haar team het aanraken lijsten.

**Adobe antwoord:** met **AJO B2B en AEP die samen werken**, kan Maya één enkele **Betaalde reis van het Controlemechanisme van Media in werking stellen**: AEP en Real-Time CDP houden de gegevens en één meester &quot;gekwalificeerd rekeningspubliek&quot;; AJO B2B stelt een rekeningsreis in werking die **spleet-weg logica** (waterval) gebruikt om elke rekening in juiste-bv., gericht te leiden Nastreven → Oplossing-Geleide → Persona → Categorie Bewustwording → Begrenzing-en **activeert aan Bestemming** verzendt elke weg naar het recht (of andere) campagne LinkedIn. Eén reis, één bron van waarheid, geen handmatige export. Dat is het patroon van de Betaalde Controlemechanisme van Media-en het is hoe Adobe precisie en schaal voor B2B betaalde media toelaat.

## Waarom het belangrijk is voor B2B-ondernemingen:

De organisaties die dit patroon goedkeuren kunnen handonderdrukking en uitsluitingslogica volledig elimineren (b.v., 100% van overlappende resolutie die in de reis wordt behandeld), schaal aan **tienduizenden rekeningen** door één enkel controlemechanisme, en handhaven a **enige bron van waarheid** waarvoor de rekening naar welke campagne gaat. Het systeem **past automatisch** als campagnecorrectie, doelpubliek, en verandering van verkoopdoelstellingen aan, zonder lijsten opnieuw uit te voeren of aan elk platform opnieuw te uploaden. Voor elke B2B-onderneming die meerdere betaalde mediacampagnes uitvoert, biedt het Paid Media Controller-patroon de helderheid, controle en automatisering die niet mogelijk is bij handmatige lijstworkflows.

De volgende KPIs richt zich goed op het meten van succes:

- **Bewustheid:** zijn doelrekeningen die de juiste advertenties zien en zich aan de juiste campagnes aan een hoger tarief bewegen?
- **Betrokkenheid:** zijn de betrokkenheid en de omzetting beter wanneer de overlapping wordt verwijderd?
- **Efficiëntie:** Hoeveel heeft handlijstwerk (uploads, uitsluitingen, onderdrukking) verminderd?
- **Kosten:** Hoe veranderen de kosten per verworven rekening of de opportuniteitsverandering met geautomatiseerd orchestration?

## Betaalde media Reisorkest

Een gemeenschappelijk gebruiksgeval, en de nadruk van deze blauwdruk, is **B2B betaalde organisatie van de Reis van de Media van de Reis**: het verzekeren van elke gekwalificeerde rekening wordt toegewezen aan precies één campagnerij en geactiveerd aan de correcte betaalde media bestemming, zonder overlapping of handhandoff.

Het controlemechanismereis **leest** een gekwalificeerd-rekeningspubliek (die in Real-Time CDP van AEP gegevens wordt gebouwd), **evalueert** elke rekening door spleet-weg (waterval) voorwaarden-b.v., nastreven → oplossing-geleide → persona → categorieintent → fundamentational-en **activeert** elke weg aan de overeenkomstige bestemming (b.v., LinkedIn Gelijkheden voor elke campagne).

**rekening-geconcentreerde oplossing:** de nadruk van het Betaalde Controlemechanisme van Media is **rekeningen** en hun **campagnecostaak**. De technische opstelling steunt de gegevens en het publiek die gekwalificeerde rekeningen en hun attributen (b.v., intent, segment, persona) vertegenwoordigen, die voor succesvolle op rekeningsniveau segmentatie en op reis-gebaseerde orchestratie wordt vereist.

## Vereisten

De rekening-geconcentreerde oplossing vereist de volgende toepassingen en de diensten:

- **Adobe Journey Optimizer B2B edition** - de reizen van de Rekening, spleet-weg (waterval) logica, activeert aan Bestemming.
- **Adobe Real-time het Platform van Gegevens van de Klant (RTCDP) B2B edition** — De profielen van de Rekening, rekeningspubliek (b.v., gekwalificeerde rekeningen voor betaalde media).

## Architectuur

Stroomniveau:

1. **Gegevens &amp; publiek** — AEP houdt profielen en gebeurtenissen; Real-Time CDP B2B bouwt rekeningspubliek (b.v., &quot;Betaalde Media In aanmerking komende Rekeningen&quot;) dat als het publiek van de reisingang wordt gebruikt.
2. **Orchestration** — AJO B2B- rekeningsreis: **gelezen publiek** (gekwalificeerde rekeningen) → **Gesplitste weg** (waterval: bv., voert na: Oplossing-Geleide → Perona → Categorie → Begonnen) → **activeert aan Bestemming** (per weg aan LinkedIn of andere betaalde media).
3. **Doelen** — Betaalde media kanalen (b.v., LinkedIn Gelijke Soorten publiek) ontvangen rekening-vlakke activering van elke wegweg; geen handlijstuploads.

## Architectuurdiagram

<img src="assets/ajo-b2b-paid-media-activation-architecture.svg" alt="AJO B2B Betaalde Media Controller Architectuur" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Gegevensmodellering in B2B AEP

Met om het even welke gegeven-gedreven organisatie, is het schemaontwerp belangrijk. De rekening en de persoonprofielen in AEP/RTCDP moeten de attributen omvatten die in **worden gebruikt spleet-weg voorwaarden** (b.v., achtervolgingsvlag, oplossingsrente, persona, intentcategorie, betrokkenheidsscore). B2B-schema&#39;s (XDM Business Account, XDM Individual Profile, relationeel) moeten uw hiërarchie en gegevensbronnen vertegenwoordigen. Voor details, zie [&#x200B; de schema&#39;s van RTCDP B2B &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) en [&#x200B; documentatie van AJO B2B &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/home).

**Nota:** Splitst-weg logica in de reis gebruikt profiel en, waar gesteund, relationele gegevens; zorg ervoor de gebieden u voor watervallogica nodig hebt beschikbaar in de reis zijn.

### Beveiligingsmechanismen

- **Journey Optimizer B2B edition** - zie de [&#x200B; productbeschrijving &#x200B;](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer-b2b.html) voor reisgrenzen, knoopgrenzen, en bestemmingssteun.
- **Real-Time CDP** — Zie [&#x200B; de guardrails van RTCDP &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview) voor segmentatie en activeringsgrenzen.

## Implementatie

In de volgende stappen worden aanwijzingen gegeven voor de implementatie van de Betaalde Mediacontrole met AJO B2B en AEP.

### Vooraf vereiste stappen

1. **bepaal rekeningspubliek en het Model van Gegevens in Real-Time CDP B2B.**

   Creeer het **gekwalificeerde-rekeningspubliek** (b.v., &quot;Betaalde Media In aanmerking komende Rekeningen&quot;) die de controlemechanismereis zullen ingaan. De Bouwer van het Segment van het gebruik en de rekening/persoonattributen die geschiktheid (b.v., geografie, segment, status MQA) bepalen. Dit publiek is het enige toegangspunt voor de reis.

2. **bepalen campagnehiërarchie en gespleten logica.**

   Documenteer de watervalvolgorde (bv. Naderen → Solution-Led → Persona → Categorie → Foundational) en de voorwaarden voor elk pad (welke kenmerken of soorten publiek een rekening kwalificeren). Verzeker voorwaarden **wederzijds uitsluitend in orde** (top-down) zijn: een rekening zou hoogstens één weg, eerste moeten aanpassen die waar evalueert.

3. **vorm bestemmingen.**

   Stel betaalmedia-bestemmingen in (bijv. LinkedIn Matched Audiences) in AEP/RTCDP en zorg ervoor dat deze beschikbaar zijn voor activering vanuit AJO B2B. Wijs accountid&#39;s en eventuele vereiste kenmerken toe voor elke bestemming.

### Configuratie van betaalde mediacontrole

1. **creeer de controlemechanismereis in AJO B2B.**

   - **gelezen publiek:** selecteer het gekwalificeerde-rekeningspubliek van Real-Time CDP.
   - **Gesplitste weg:** voeg knopen in watervalorde toe. Elk knooppunt evalueert de voorwaarden (bijvoorbeeld &quot;in publiek achterhalen&quot;, &quot;interesse voor oplossing = X&quot;, &quot;persona = Y&quot;, &quot;categorie intent = Z&quot;). Accounts die overeenkomen met exit to the corresponding activation; other continue to the next split.
   - **activeer aan Bestemming:** voor elke weg, voeg toe activeer aan de knoop van de Bestemming aan de correcte (of andere) campagne LinkedIn/bestemming.

2. **bevestigt wederzijdse exclusiviteit.**

   - Bevestig dat elke account slechts één pad invoert (de eerste voorwaarde voor afstemming).
   - Verifieer activering: accounts worden op de juiste bestemming weergegeven en worden volgens plan uitgesloten van campagnes met lagere prioriteit.

## Implementatiediagram

<img src="assets/ajo-b2b-paid-media-controller-canvas.svg" alt="AJO B2B Betaald Media Controller-canvas" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

### 4.2.3. Activering van het publiek

1. **activeer aan LinkedIn (en andere bestemmingen).**

   Gebruik &quot;Activate to Destination&quot; in de reis om elke weg naar het juiste betaalde mediapubliek te verzenden. Geen handmatige export of upload; de reis drijft activering als rekeningen door wegen stromen.

2. **Monitor en stemmen.**

   Gebruik reisrapportage om volumes per pad te controleren.

## Overzicht

Het **Betaalde 1&rbrace; blauwdruk van het Controlemechanisme van Media van Media &lbrace;toont hoe** AJO B2B en AEP **samenwerken om B2B-marketers één enkele, geautomatiseerde manier te geven om rekeningen aan campagnes toe te wijzen en aan betaalde media te activeren: één hoofdpubliek, één reis, watervalgespleten logica, en directe activering aan bestemmingen-geen handlijsthandschoenen.** Het vestigt een herhaalbaar patroon voor uit meerdere kanalen B2B betaalde media orchestratie en helpt overlapping verminderen, relevantie, en schaalverrichtingen verbeteren.

## Gerelateerde documentatie

- [&#x200B; het Kopen op groep-Gebaseerde Verkoop en de blauwdruk van het Beheer van de Reis &#x200B;](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/b2b-activation/b2b-buying-group-journeys) — De reis van de Rekening en het kopen groepsreizen in AJO B2B.
- [&#x200B; Adobe Journey Optimizer B2B edition &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b) — de documentatie van het Product.
- [&#x200B; Real-time het Platform van Gegevens van de Klant B2B edition &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/b2b-overview) - het publiek van de Rekening en activering.
