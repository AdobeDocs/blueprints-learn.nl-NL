---
title: B2B Audience Activation
description: Leer hoe u op account gebaseerde B2B-doelgroepen activeert via internet, e-mail en reclamekanalen.
solution: Real-Time Customer Data Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '7567'
ht-degree: 0%

---


# B2B-publieksactivering

Deze handleiding bevat een uitgebreide implementatiereferentie voor het activeren van B2B-publiek op basis van account met [!DNL Adobe Real-Time Customer Data Platform] ([!DNL RT-CDP]) B2B edition. Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die een publiek op accountniveau moeten maken, evalueren en activeren via internet, e-mail, reclame en CRM-kanalen.

Deze omvat de volledige levenscyclus van de eenmaking van het accountprofiel via publieksevaluatie en activering naar B2B-specifieke doelen zoals [!DNL Marketo Engage], [!DNL LinkedIn] en CRM-systemen. Alle uitvoerbare benaderingen worden voorgesteld met compromissen en beslissingsbegeleiding om u te helpen de juiste weg voor uw organisatie selecteren.

## Hoofdlettergebruik

B2B-marketingteams moeten doelgroepen maken en het publiek activeren op het niveau van de account in plaats van op het niveau van de individuele persoon. In tegenstelling tot B2C-publieksactivering waarbij de eenheid voor doelgerichtheid één consumentenprofiel is, vereist B2B-publieksactivering inzicht in de relatie tussen mensen en de accounts waartoe zij behoren, evaluatie van het aantal doelgroepen op basis van kenmerken op accountniveau in combinatie met persoonlijke betrokkenheidssignalen, en levering van dit soort doelgroepen aan doelen die op account gebaseerde doelgerichtheid ondersteunen.

[!DNL RT-CDP] B2B edition breidt de standaard [!DNL Real-Time Customer Data Platform] uit met gespecialiseerde XDM-klassen voor accounts, mogelijkheden en campagnes, samen met B2B-identiteitsresolutie die relaties van persoon tot account in kaart brengt. Op deze manier kunnen marketeers accountsoorten samenstellen die firmografische gegevens (industrie, inkomsten, personeelsbestand), technische gegevens (technologiestapel, productgebruik) en gedragsgegevens (webbezoeken, betrokkenheid bij e-mail, aanwezigheid bij gebeurtenissen) van de personen die bij deze accounts zijn betrokken, combineren.

Het publiek van de geactiveerde account maakt gebruik van energieverbruiksgevallen op de funnel voor het genereren van vraag: top-of-funnel bewustmakingscampagnes over [!DNL LinkedIn] en het weergeven van advertenties, programma&#39;s voor middelmatige funnel-vermeerdering in [!DNL Marketo Engage] en bottom-funnel-mogelijkheden voor verkoop via CRM-integratie. Accountsuppressie voorkomt verspilde uitgaven door bestaande klanten, gesloten accounts of accounts die zich al in actieve verkoopcycli bevinden, uit te sluiten.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

### De productie van lood verhogen

Genereer meer gekwalificeerde leads voor de verkooppijplijn via formulieren, gebeurtenissen, inhoud en betrokkenheid via meerdere kanalen.

**KPIs:** Vooruitzichten, Kosten per Lood, Loodomzetting

[Meer informatie over het verhogen van de productie van lood](/help/blueprints/business-objectives/acquisition-growth/increase-lead-generation.md)

### Kwalificatie en conversie van leads verbeteren

Verhoog de loodkwaliteit en verhoog de voortgang van de pijplijnen via scoring, verpleging en gepersonaliseerde follow-up.

**KPIs:** de Omzetting van de lood, Vooruitzichten/Loodomzetting, Efficiëntie

[Meer informatie over het verbeteren van kwalificatie en conversie van leads](/help/blueprints/business-objectives/qualification-sales-b2b/improve-lead-qualification-conversion.md)

### Nieuwe klanten aanschaffen

Breid de klantenbasis door gerichte aanschafcampagnes, lookend publiek, en betaalde media optimalisering uit.

**KPIs:** Nieuwe Klanten, de Kosten van de Aankoop van de Klant, Vooruitziendheid/Loodomzetting

[Meer informatie over het aanschaffen van nieuwe klanten](/help/blueprints/business-objectives/acquisition-growth/acquire-new-customers.md)

### marketinguitgaven en investeringsrendement optimaliseren

Verbeter het rendement van marketing investering door betere richten, attributie, publieksonderdrukking, en begrotingstoewijzing.

**KPIs:** Kostenbesparingen, de Kosten van de Aankoop van de Klant, Incrementele Inkomsten

## Voorbeelden van tactische gebruiksgevallen

De volgende scenario&#39;s tonen aan hoe dit patroon in de praktijk kan worden toegepast.

- **Op account gebaseerde reclame op[!DNL LinkedIn]** — Doelaccounts die overeenkomen met uw ideale klantprofiel (ICP) met gesponsorde inhoud en InMail-campagnes op [!DNL LinkedIn] , die accountlijsten gebruiken die zijn geactiveerd vanuit [!DNL RT-CDP] B2B edition
- **[!DNL Marketo Engage]Programma dat zich richt** — activeer rekeningspubliek aan [!DNL Marketo Engage] om bijbehorende lood en contacten in gerichte boompingsstromen in te schrijven die op rekeningsniveau kwalificatiecriteria worden gebaseerd
- **de synchronisatie van de de rekeningslijst van CRM** - duw gekwalificeerde rekeningslijsten aan [!DNL Salesforce] of [!DNL Microsoft Dynamics] voor het zicht van het verkoopteam, gebiedstoewijzing, en uitgaande prospectieve werkschema&#39;s
- **de onderdrukking van de Rekening voor betaalde media** — onderdruk bestaande klanten, gesloten-won rekeningen, of rekeningen in actieve verkoopcycli van betaalde aanschafcampagnes om verspilde uitgaven te verminderen
- **Intent-based rekening richtend** — combineer derde intent signalen met de gegevens van de eerste-partijovereenkomst op het rekeningsniveau om publiek van rekeningen binnen-marktwerking te identificeren en te activeren
- **product dwars-verkoopt aan bestaande rekeningen** — Bouw publiek van rekeningen gebruikend één productlijn maar niet een andere, dan activeer aan e-mail en reclamekanalen voor dwars-verkoopcampagnes
- **Gebeurtenis en webinar richtend** — activeer rekeningspubliek aan reclame en e-mailkanalen om gebeurtenisregistratie van doelrekeningen te drijven
- **Concurrerende verplaatsingscampagnes** — De rekeningen van het doel die concurrerende producten met specifiek overseinen gebruiken die door reclame en e-mailkanalen worden geactiveerd
- **Gelaagde rekeningsovereenkomst** — de rekeningen van het segment in betrokkenheidsrijen (hoog, middelgroot, laag) die op samengevoegde persoon-vlakke activiteit wordt gebaseerd en gedifferentieerde campagnes voor elke rij activeert
- **Partner co-marketing publiek** — De segmenten van het rekeningspubliek van het aandeel met kanaalpartners of co-marketing programma&#39;s door de bestemmingen van de wolkenopslag

## Kernprestatie-indicatoren

De volgende KPIs helpt het succes van dit gebruiks gevalpatroon meten.

| KPI | Beschrijving | Meetmethode |
| --- | --- | --- |
| Accountoverzicht | Aantal doelaccounts dat via activeringskanalen is bereikt | Unieke accounts bijhouden die per doel zijn geactiveerd |
| Betrokkenheid account | Percentage geactiveerde accounts met betrokkenheidssignalen | De betrokkenheid op persoonlijk niveau meten geaggregeerd voor rekening |
| Invloed pijpleiding | Opbrengstpijplijn die wordt toegeschreven aan op rekeningen gebaseerde activeringscampagnes | Mogelijkheden bijhouden die door gebruikers van geactiveerde accounts zijn gemaakt |
| Kosten per account | Marketinguitgaven gedeeld door het aantal accounts met betrokkenheid | Kosten voor alle advertenties en e-mailkanalen berekenen |
| Omzetsnelheid lead | Percentage leads van geactiveerde accounts die worden omgezet in kansen | Aanloop-naar-opportuniteitsconversie volgen voor actief publiek |
| Besparingen op onderdrukking van het publiek | Kosten vermeden door niet-subsidiabele accounts uit betaalde campagnes te verwijderen | De uitgaven van de maatregel verminderen van onderdrukkingspubliek |
| Accountdekking | Percentage van de totale adresseerbare markt (TAM) dat door het actieve publiek wordt gedekt | Vergelijk geactiveerde rekeningen met totaal ICP universum |

## Hoofdletterpatroon gebruiken

**B2B publieksactivering**

Activeer op account gebaseerde B2B-doelgroepen via internet, e-mail en reclamekanalen.

**de ketting van de Functie:** de Verrijking van het Profiel van de Rekening > de Evaluatie van het publiek van de Rekening > de Configuratie van de Bestemming > Audience Activation > Controle

## Applicaties

De volgende toepassingen worden gebruikt om dit gebruiks gevalpatroon uit te voeren.

- **[!DNL Real-Time CDP]B2B edition** — Het platform van de Kern voor de unificatie van het rekeningsprofiel, B2B identiteitsresolutie, de evaluatie van het rekeningspubliek, B2B-Specifieke bestemmingsconfiguratie, en activering van het rekeningspubliek
- **[!DNL Adobe Experience Platform] (AEP)** — Foundational Infrastructure for B2B XDM data modelling, gegevensopname van CRM en marketing automatiseringsbronnen, identiteitsdienst, en bestuur
- **[!DNL Marketo Engage]** — Primaire automatiseringsbestemming voor B2B-marketing voor programma&#39;s, scoring en uitvoering van de campagne die door het publiek van de geactiveerde account worden gebruikt

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary, functie | Status | Wat moet er gebeuren? | Experience League-referentie |
| --- | --- | --- | --- |
| Beheer en bestuur | Vereist | Sandbox met [!DNL RT-CDP] B2B edition ingeschakeld. Rollen die zijn geconfigureerd voor B2B-gegevensbeheer, publiekscreatie en doelactivering. ABAC-beleid is ingesteld als accountgegevens beperkte velden bevatten. | [&#x200B; het overzicht van Sandboxen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sandbox/home), [&#x200B; overzicht van de Toegangscontrole &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | B2B XDM-schema&#39;s geconfigureerd met XDM Business Account, XDM Business Opportunity, XDM Business Campaign en XDM Individual Profile-klassen. B2B-veldgroepen die zijn toegepast voor accountkenmerken, relaties tussen personen en accounts. Voor elke B2B-entiteit worden gegevenssets gemaakt en profiel ingeschakeld. Schemarelaties gedefinieerd tussen account, persoon, opportuniteit en campagneentiteiten. | [&#x200B; XDM het overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/home), [&#x200B; B2B- schema&#39;s in Real-Time CDP &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/rtcdp/schemas/b2b) |
| Gegevensbronnen en -verzameling | Vereist | Source-connectors geconfigureerd voor CRM ([!DNL Salesforce], [!DNL Microsoft Dynamics] ) en marketingautomatisering ([!DNL Marketo Engage] ) om account, persoon, opportuniteit en campagnegegevens in te voeren. Batch- of streamingpipetten zijn actief. De afbeeldingen van Prep van gegevens die worden gevormd om brongegevens in B2B XDM- schema&#39;s om te zetten. | [&#x200B; Bronoverzicht &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/home), [&#x200B; schakelaar van Marketo Engage &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) |
| Identiteit en profielconfiguratie | Vereist | B2B-naamruimten geconfigureerd voor account-id&#39;s (account-id, CRM-account-id) en personen-id&#39;s (e-mail, CRM-contact-id, Marketo Lead-id). Persoonlijke relaties opgelost via B2B-identiteitsafwikkeling. Beleid samenvoegen dat is geconfigureerd voor samenvoeging van accountprofielen. | [&#x200B; Overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/home), [&#x200B; B2B edition van Real-Time CDP &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b) |
| Auditiedefinitie en segmentatie | Vereist | Accountniveau publieksdefinities gemaakt met accountkenmerken, personekenmerken en activiteitsgegevens. De programma&#39;s van de evaluatie die voor rekeningspubliek worden gevormd. Onderdrukkingspubliek gedefinieerd voor het uitsluiten van niet-beleenbare rekeningen. | [&#x200B; overzicht van de Dienst van de Segmentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home), [&#x200B; het publiek van de Rekening &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/types/account-audiences) |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League-referentie |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Aanbevolen | Geaggregeerde betrokkenheidsscores, levenslange waarde en activiteitscijfers op accountniveau verbeteren de nauwkeurigheid van de doelgroep. Met berekende kenmerken kunnen gebeurtenissen op persoonlijk niveau (e-mail wordt geopend, webbezoeken, downloaden van inhoud) naar het accountniveau worden opgehaald voor gebruik in segmentatie. | [&#x200B; Berekende attributen overzicht &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/computed-attributes/overview) |
| Levenscyclusbeheer van gegevens | Aanbevolen | B2B-beleid voor gegevensopslag zorgt ervoor dat de gegevens van een account op een schaal worden opgeschoond en dat de opportuniteitsgegevens worden opgeschoond. Het beheer van de toestemming voor B2B contacten verzekert naleving van e-mailmarketing verordeningen. Dataset vervalbeleid verhindert accumulatie van verouderde gegevens van de synchronisatie van CRM. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Opgenomen | B2B-rekeninggegevens bevatten vaak contractuele beperkingen (inkomstencijfers, personeelstellingen van derden). Met labels voor gegevensgebruik kunnen beperkte accountkenmerken niet worden geactiveerd voor onbevoegde doelen. Het beleid van het bestuur zorgt ervoor dat PII- gebieden van contactverslagen correct tijdens activering worden behandeld. | [&#x200B; Overzicht van het beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home) |
| Bewaking en waarneming | Opgenomen | Door CRM en [!DNL Marketo Engage] bronconnectorgegevens te controleren, blijven de accountgegevens actueel. Controle van doelactivering bevestigt dat het publiek correct wordt benaderd voor [!DNL LinkedIn] -, [!DNL Marketo] - en CRM-doelen. Waarschuwingsregels mislukte inname van gegevens afvangen die storende accountgegevens zouden veroorzaken. | [&#x200B; het overzicht van Alarm &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/alerts/overview), [&#x200B; de bestemmingsdataflows van de Monitor &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/dataflows/ui/monitor-destinations) |
| Rapportage en analyse | Aanbevolen | [!DNL CJA] B2B edition biedt analyses op accountniveau, waaronder bereik, betrokkenheid en invloed van de pijpleiding. De op rekening-gebaseerde attributie helpt de invloed van activeringscampagnes op opportuniteitsvooruitgang en opbrengst meten. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Real-Time CDP] B2B edition ([!DNL RT-CDP] B2B)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Account Profile Unification | Fase 1: Verrijking van accountprofiel | Consolideer accountgegevens van CRM, marketingautomatisering en bronnen van derden tot geconsolideerde accountprofielen met behulp van B2B XDM-schemaklassen |
| B2B-identiteitsresolutie | Fase 1: Verrijking van accountprofiel | Los van persoon tot rekening verhoudingen gebruikend primaire herkenningstekens, in kaart brengend contacten en leidt tot hun bijbehorende rekeningen |
| Evaluatie accountpubliek | Fase 2: Evaluatie van accountpubliek | Evalueer het op rekeningsniveau segmentlidmaatschap door rekeningsattributen, persoonattributen, en de gegevens van de persoonactiviteit te combineren |
| Configuratie van accountbestemming | Fase 3: Doelconfiguratie | Verbindingen met B2B-specifieke bestemmingen ([!DNL Marketo Engage], [!DNL LinkedIn], CRM, cloudopslag) configureren met veldtoewijzing op accountniveau |
| Account Audience Activation | Fase 4: Audience Activation | Publiceer op rekening-gebaseerde publiek aan gevormde bestemmingen voor het richten, onderdrukking, of synchronisatie van CRM |
| [!DNL Marketo Engage] Integratie | Fase 3: Doelconfiguratie | Bidirectionele gegevensstroom configureren met [!DNL Marketo Engage] met behulp van native B2B-bron- en doelconnectors |
| B2B-gegevensbeheer | Fase 5: Bestuur en toezicht | Beleid voor gegevensgebruik afdwingen en toestemming geven voor activering van B2B-accountgegevens om blootstelling aan onbevoegde gegevens te voorkomen |

### [!DNL Real-Time CDP] ([!DNL RT-CDP]) — standaardfuncties

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Evaluatie publiek | Fase 2: Evaluatie van accountpubliek | Onderliggende evaluatiemotor voor het publiek voor rekening, ter ondersteuning van batchbeoordeling van definities van segmenten op rekeningniveau |
| Doelconfiguratie | Fase 3: Doelconfiguratie | De infrastructuur van de bestemmingsverbinding van de kern die door B2B-specifieke bestemmingsconfiguratie wordt gebruikt |
| Doelgroepactivering | Fase 4: Audience Activation | Dataflow-infrastructuur voor kernactivering die door activering van het accountpubliek wordt gebruikt |
| Goedkeuring en handhaving van bestuur | Fase 5: Bestuur en toezicht | Voorkeuren voor toestemming en beleid voor gegevensgebruik tijdens activering afdwingen |

## Vereisten

Voltooi het volgende voordat u de implementatie start.

- [ ] [!DNL RT-CDP] B2B edition-licentie ingericht en geactiveerd op de organisatie
- [ ] CRM-systeem ([!DNL Salesforce] of [!DNL Microsoft Dynamics]) dat toegankelijk is met API-referenties voor de configuratie van de bronconnector
- [ ] [!DNL Marketo Engage] -instantie voorzien van API-toegang (Munchkin-id, client-id, clientgeheim) als [!DNL Marketo] als doel wordt gebruikt
- [ ] [!DNL LinkedIn] Campagnebeheeraccount met overeenkomende mogelijkheden voor publiek als [!DNL LinkedIn] als doel wordt gebruikt
- [ ] B2B XDM-schema&#39;s die zijn gemaakt met account-, persoon-, opportuniteits- en campagneklassen (F2)
- [ ] Source-connectors geconfigureerd en gebruikt actief CRM- en marketingautomatiseringsgegevens (F3)
- [ ] Persoonlijke identiteitsrelaties opgelost en accountprofielen samengevoegd (F4)
- [ ] De conventies en taxonomie voor accountnamen die zijn overeengekomen voor publieksdefinities
- [ ] Beleid voor gegevensbeheer gedefinieerd voor gegevensgevoeligheidsclassificaties op accountniveau

## Implementatieopties

In de volgende opties worden verschillende methoden beschreven voor het implementeren van dit gebruikspatroon. Bekijk elke optie en selecteer de optie die het beste bij uw vereisten past.

### Optie A: activering van het stroompubliek naar [!DNL Marketo Engage]

**Best voor:** Organisaties die [!DNL Marketo Engage] gebruiken als hun primaire B2B het marketing automatiseringsplatform, die updates van het publiek in de buurt-real-time nodig hebben om de programma&#39;s van de boomkwekerij, update loodscores, of wijzig campagnecolleship als rekeningen kwalificeren of diskwalificeren.

**hoe het werkt:**

Deze optie gebruikt de native [!DNL Marketo Engage] doelconnector in [!DNL RT-CDP] om wijzigingen in het publiekslidmaatschap van een account rechtstreeks in [!DNL Marketo Engage] te streamen. Wanneer een account in aanmerking komt voor of een publiekssegment verlaat, worden de bijbehorende leads en contactpersonen in [!DNL Marketo] bijgewerkt met de kenmerken voor segmentlidmaatschap. [!DNL Marketo] slimme campagnes kunnen dan worden geactiveerd op basis van deze lidmaatschapswijzigingen.

De bestemming [!DNL Marketo Engage] is een het stromen bestemming, betekenend de veranderingen van het publiekslidmaatschap stapsgewijs worden verzonden aangezien zij eerder dan in geplande partijen voorkomen. Dit biedt snellere tijd-aan-actie voor campagnes die aan veranderingen van de rekeningskwalificatie moeten antwoorden. Veldtoewijzingen verbinden [!DNL RT-CDP] -profielkenmerken met [!DNL Marketo] lead/contact-velden, zodat [!DNL Marketo] -records kunnen worden verrijkt met gegevens op accountniveau uit [!DNL RT-CDP] .

**Zeer belangrijke overwegingen:**

- Vereist een actief [!DNL Marketo Engage] abonnement met API-toegang
- Door activering van streaming worden incrementele updates verzonden, niet volledige momentopnamen voor het publiek
- Records op persoonlijke niveau in [!DNL Marketo] worden bijgewerkt, niet rechtstreeks records op accountniveau
- [!DNL Marketo] Slimme campagnes moeten worden geconfigureerd om te werken op de updates van het segmentlidmaatschapsveld

**Voordelen:**

- Updates van het bijna-real-time publiekslidmaatschap in [!DNL Marketo]
- Geïntegreerde tweerichtingsaansluiting vereenvoudigt integratie
- Incrementele updates minimaliseren gegevensoverdrachtvolume
- [!DNL Marketo] kan programma&#39;s voor het opvoeden onmiddellijk activeren op basis van wijzigingen in het publiek

**Beperkingen:**

- Beperkt tot [!DNL Marketo Engage] als activeringsdoel
- De toelatingsbeperkingen voor stroomevaluatie zijn van toepassing op de onderliggende publieksdefinities
- Vereist toewijzing tussen [!DNL RT-CDP] accountpubliek en [!DNL Marketo] lead/contact records
- Complexe [!DNL Marketo] programmalogi zijn mogelijk nodig om updates op persoonniveau te vertalen in acties op accountniveau

**Experience League:**

- [Marketo Engage-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Soorten publiek naar Marketo Engage-doel activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/adobe/marketo-engage#activate)

### Optie B: activering van het publiek in batch op reclameplatforms

**Best voor:** op rekening-gebaseerde reclamecampagnes op [!DNL LinkedIn], vertoningsnetwerken, of andere reclameplatforms waar de dagelijkse publieksverfrissingen voldoende zijn en het primaire doel is bereik en bewustzijn op rekeningsniveau eerder dan reactie in real time.

**hoe het werkt:**

Met deze optie activeert u het accountpubliek naar advertentieplatformdoelen ([!DNL LinkedIn] Gelijkend publiek, [!DNL Google] Klantenovereenkomst, [!DNL Facebook] Aangepast publiek of [!DNL The Trade Desk] ) op een geplande batch-opname. De activeringsgegevensstroom exporteert accountgebruikers met toegewezen identiteitsvelden (meestal gehashte e-mailadressen van bijbehorende contactpersonen) die het advertentieplatform gebruikt om met zijn gebruikersbasis overeen te komen.

Voor [!DNL LinkedIn] in het bijzonder, keurt de [!DNL LinkedIn] Gelijke bestemming van het Publiek bedrijfsnaam en op domein-gebaseerde aanpassing naast op e-mail-Gebaseerde aanpassing goed, toelatend ware rekening-vlakke richten. Andere advertentieplatforms vereisen typisch persoon-vlakke herkenningstekens (e-mail, telefoon) van de contacten verbonden aan kwalificerende rekeningen.

Batchactivering wordt uitgevoerd volgens een configureerbaar schema (dagelijks, elke 6 uur, enz.) en exporteert volledige publieksmomentopnamen of incrementele wijzigingen, afhankelijk van het doeltype. Deze aanpak is zeer geschikt voor permanente bewustmakingscampagnes waarbij de behoefte aan het publiek aan versheid wordt gemeten in uren in plaats van minuten.

**Zeer belangrijke overwegingen:**

- De versheid van het publiek hangt af van het batchschema (gewoonlijk dagelijks)
- Advertising-platforms hebben hun eigen beperkingen met betrekking tot de match rate
- [!DNL LinkedIn] ondersteunt matching op accountniveau; andere platforms vereisen id&#39;s op persoonlijke niveau
- Bestandsindelingen en identiteitsvereisten voor export verschillen per bestemming

**Voordelen:**

- Ondersteunt meerdere reclameplatforms tegelijk
- Batchverwerking hanteert efficiënt grote doelvolumes
- Het publiek voor accountonderdrukking vermindert verspilde advertentie-uitgaven
- [!DNL LinkedIn] Gelijktijdig publiek maakt native doelgericht gebruik op accountniveau mogelijk

**Beperkingen:**

- De updates van het publiek zijn niet real time; de latentie hangt van partijprogramma af
- Gelijke snelheden variëren per platform en beschikbare identiteitsvelden
- Sommige platforms bieden geen ondersteuning voor werkelijke afstemming op accountniveau, alleen op persoonlijke niveau
- Vereist een aparte doelconfiguratie voor elk advertentieplatform

**Experience League:**

- [Doel van LinkedIn-overeenkomend publiek](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/social/linkedin)
- [Google Customer Match-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/advertising/google-customer-match)
- [Doelcatalogus](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/overview)

### Optie C: activering van bestanden naar cloudopslag

**Best voor:** Organisaties die maximumflexibiliteit in vereisen hoe de rekeningspubliek stroomafwaarts, met inbegrip van de invoer van CRM, de verrijking van het gegevenspakhuis, partner gegevens het delen, of douaneverbeteringen wordt verbruikt waar een op dossier-gebaseerde handoff voorkeur heeft.

**hoe het werkt:**

Met deze optie exporteert u accountsoorten als CSV-, JSON- of Parquet-bestanden naar cloudopslagdoelen ([!DNL Amazon S3], [!DNL Azure Blob Storage], [!DNL Google Cloud Storage], SFTP) op een geplande poort. Het exporteren omvat accountkenmerken, velden op persoonniveau van de bijbehorende contactpersonen en metagegevens van het publiekslidmaatschap. Downstreamsystemen gebruiken deze bestanden via hun eigen importprocessen.

Activering op basis van bestanden biedt de meeste controle over de exportindeling, de veldselectie en de planning. Deze functie ondersteunt zowel volledige export (volledige publieksopname elke keer) als incrementele export (alleen wijzigingen sinds de laatste keer dat de animatie wordt uitgevoerd). Deze benadering wordt doorgaans gebruikt wanneer het doelsysteem geen native [!DNL RT-CDP] doelconnector heeft of wanneer de organisatie de gegevens moet verwerken of transformeren voordat deze in het doelsysteem worden geladen.

**Zeer belangrijke overwegingen:**

- Vereist een infrastructuur voor cloudopslag ([!DNL S3], [!DNL Azure Blob], [!DNL GCS] of SFTP)
- Downstream-importprocessen moeten worden ontwikkeld en onderhouden
- De bestandsindeling (CSV, JSON, Parquet) moet overeenkomen met de vereisten van het downstreamsysteem
- Exportplanning moet worden uitgelijnd met downstreamverwerkingsvensters

**Voordelen:**

- Maximale flexibiliteit in het gebruik van publieksgegevens
- Ondersteunt elk downstreamsysteem dat bestanden kan lezen
- Volledige controle over exportindeling, velden en planning
- Kan meerdere downstreamconsumenten van één enkele export bedienen
- Ondersteunt volledige en incrementele exportmodi

**Beperkingen:**

- Hoogste latentie van alle opties (alleen batch)
- Vereist de bouw en het handhaven van stroomafwaartse de invoerwerkschema&#39;s
- Geen native integratie — extra ontwikkelingsinspanningen vereist
- Bestandsbeheer (opschonen, archiveren) moet afzonderlijk worden behandeld

**Experience League:**

- [Amazon S3-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Azure Blob-opslagbestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/cloud-storage/azure-blob)
- [Soorten publiek naar batchbestemmingen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/api/connect-activate-batch-destinations)

### Optie D: Streaming activering naar CRM-systemen

**Best voor:** verkoop-marketing groepering gebruikt gevallen waar de veranderingen van de rekeningskwalificatie in CRM ([!DNL Salesforce] of [!DNL Dynamics]) in bijna-real-time voor het zicht van het verkoopteam, de updates van de gebiedstoewijzing, of geautomatiseerde verkoopworkflows moeten worden weerspiegeld.

**hoe het werkt:**

Deze optie gebruikt het stromen bestemmingsschakelaars ([!DNL Salesforce] CRM, [!DNL Microsoft Dynamics]) om de veranderingen van het rekeningspubliek direct in de rekening van CRM of contactverslagen van CRM te duwen. Wanneer een rekening voor kwalificeert of een publiek weggaat, wordt het verslag van CRM bijgewerkt met een douanegebied dat op segmentlidmaatschap wijst. Verkoopteams kunnen vervolgens CRM-rapporten, -weergaven en -waarschuwingen samenstellen op basis van deze velden.

De streamingconnector verzendt incrementele updates wanneer wijzigingen in het publiekslidmaatschap optreden. Veldtoewijzingen verbinden [!DNL RT-CDP] -account en persoonkenmerken met CRM-velden, waardoor CRM-records kunnen worden verrijkt met gegevens van [!DNL RT-CDP] . Deze benadering sluit de lijn tussen marketing intelligentie (rekeningskwalificatie) en verkoopuitvoering (de werkschema&#39;s van CRM).

**Zeer belangrijke overwegingen:**

- Hiervoor is CRM API-toegang met de juiste schrijfmachtigingen vereist
- Aangepaste CRM-velden moeten worden gemaakt om lidmaatschapsgegevens voor het publiek te ontvangen
- Streaming volume moet binnen CRM API-snelheidslimieten liggen
- De automatisering van CRM-workflows moet worden geconfigureerd om op veldinstellingen te kunnen reageren

**Voordelen:**

- De updates van CRM in real time voor het zicht van het verkoopteam
- Maakt geautomatiseerde CRM-workflows mogelijk die worden geactiveerd door wijzigingen in het publiek
- Verrijkt CRM-records met gegevens van een geconsolideerde account van [!DNL RT-CDP]
- Ondersteunt zowel updates op accountniveau als op contactniveau

**Beperkingen:**

- CRM API-snelheidslimieten kunnen updates op grote volumes vertragen
- CRM-aanpassing vereist (aangepaste velden, workflows)
- Beperkt tot [!DNL Salesforce] en [!DNL Microsoft Dynamics] als native connectors
- De het stromen evaluatiebeperkingen zijn van toepassing op het onderliggende publiek

**Experience League:**

- [Salesforce CRM-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)

### Optievergelijking

In de volgende tabel worden de belangrijkste kenmerken van elke implementatieoptie vergeleken.

| Criteria | Optie A: [!DNL Marketo] Streaming | Optie B: Advertising-batch | Optie C: Cloudopslag | Optie D: CRM-streaming |
| --- | --- | --- | --- | --- |
| Best voor | Activering van het cursusprogramma | Reclame op basis van account | Flexibele downstreamintegratie | Afstemming op de verkoop |
| Complexiteit | Laag | Gemiddeld | Medium-High | Gemiddeld |
| Latentie | Bijna real-time (minuten) | Batch (uren) | Batch (uren) | Bijna real-time (minuten) |
| Flexibiliteit | Laag ([!DNL Marketo] only) | Medium (reclameplatforms) | Hoog (elk downstreamsysteem) | Laag (alleen CRM) |
| Vereisten | [!DNL Marketo Engage] licentie | Advertising-platformaccounts | Infrastructuur voor cloudopslag | Toegang tot CRM API |
| Doelstelling op accountniveau | Via persoonrecords | [!DNL LinkedIn] alleen (andere persoon) | Configureerbaar | Via account/contactgegevens |
| Onderhoudsinspanning | Laag | Low-Medium | Hoog | Gemiddeld |

### Kies de juiste optie

Gebruik de volgende beslissingsrichtlijnen om de juiste activeringsmethode te selecteren:

1. **als uw primaire doel B2B lood het voeden is en u[!DNL Marketo Engage]** gebruikt, kies Optie A. De native streamingconnector biedt de snelste tijd-tot-actie voor het op de markt brengen van automatiseringsworkflows.

2. **als uw primaire doel op rekening-gebaseerd bewustzijn en vraaggeneratie door reclame** is, verkies Optie B. [!DNL LinkedIn] Gelijktijdige doelgroepen bieden het sterkste doel op accountniveau. Gebruik andere advertentieplatforms voor een groter bereik.

3. **als u rekeningspubliek aan systemen zonder inheemse [!DNL RT-CDP] schakelaars** moet voeren, of als u maximumcontrole over gegevensformaat en stroomafwaartse verwerking nodig hebt, verkies Optie C. Dit is ook de beste keus voor het delen van partnergegevens of de verrijking van het gegevenspakhuis.

4. **als uw primair doel verkoopenablement en het zicht van CRM van marketing-gekwalificeerde rekeningen** is, verkies Optie D. Dit sluit marketing-aan-verkoop handoff lijn door de verslagen van CRM in bijna-real-time bij te werken.

De meeste B2B-organisaties implementeren tegelijkertijd meerdere opties, bijvoorbeeld optie A voor programma&#39;s voor het opvoeden van een kind, optie B voor [!DNL LinkedIn] reclame en optie D voor synchronisatie van CRM. Deze opties sluiten elkaar niet uit; hetzelfde accountpubliek kan tegelijkertijd worden geactiveerd voor meerdere doelen.

## Uitvoeringsfasen

In de volgende fasen wordt het stapsgewijze proces beschreven voor het implementeren van dit gebruikspatroon.

### Fase 1: Verrijking van accountprofielen

Deze fase vestigt verenigde rekeningsprofielen door gegevens van CRM, marketing automatisering, en derdebronnen te consolideren.

**de functie van de Toepassing:** [!DNL RT-CDP] B2B: De Unificatie van het Profiel van de rekening, [!DNL RT-CDP] B2B: B2B de Resolutie van de Identiteit

**wat u zult vormen:** Deze fase vestigt verenigde rekeningsprofielen door gegevens van CRM, marketing automatisering, en derdebronnen te consolideren. B2B-identiteitsresolutie wijst relaties van persoon tot account toe, zodat persoonlijke betrokkenheidsgegevens (e-mail wordt geopend, webbezoeken, downloaden van inhoud) kunnen worden samengevoegd en gebruikt in de evaluatie van het publiek op accountniveau. Deze fase bouwt voort op de grondfuncties F2, F3, en F4 die reeds moeten zijn op zijn plaats.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: De strategie van identiteitskaart van de Rekening**
>
>Welke identificator dient als primaire rekeningssleutel over systemen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| CRM-account-id (bijvoorbeeld [!DNL Salesforce] account-id) | CRM is het systeem van registratie voor rekeningen | Meest voorkomende aanpak. Hiermee zorgt u voor uitlijning tussen [!DNL RT-CDP] en CRM. Vereist dat alle bronsystemen verwijzen naar dezelfde CRM-account-id. |
>| Aangepaste account-id | Meerdere CRM-instanties of een eigen accountmaster | Vereist een toewijzingslaag tussen bron systeem IDs en canonical rekening ID. Flexibeler, maar vergroot de complexiteit. |
>| DUNS-nummer of -domein | Verrijking van gegevens van derden is de primaire rekeningbron | Nuttig wanneer leveranciers van grafische gegevens de belangrijkste bron zijn. Mogelijk is vage overeenkomst vereist voor op domein gebaseerde resolutie. |

>[!NOTE]
>**Besluit: Persoonlijk-aan-rekening relatiemodel**
>
>Hoe zijn personen (leads, contactpersonen) gekoppeld aan accounts?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Eén-op-één (elke persoon behoort tot één account) | Eenvoudig B2B-model met zuivere CRM-gegevens | Eenvoudige resolutie. Meest voorkomende voor B2B-middenmarkt. |
>| Vele-aan-vele (de mensen kunnen tot veelvoudige rekeningen behoren) | Complexe bedrijfsrelaties, consultants of partnernetwerken | [!DNL RT-CDP] B2B edition biedt hiervoor native ondersteuning. Verhoogt de complexiteit van het publiek, maar geeft de relaties in de praktijk accuraat weer. |

**navigatie UI:** Platform > Profielen > doorbladert (om verenigde rekeningsprofielen te verifiëren)

**Zeer belangrijke configuratiedetails:**

- Controleer of B2B XDM-schema&#39;s (XDM Business Account, XDM Business Person Account) zijn geïnstalleerd vanuit F2
- Bevestig CRM en de [!DNL Marketo] bronschakelaars nemen actief rekening en persoongegevens van F3 op
- Controleren of relaties van persoon tot account zijn opgelost in de identiteitsgrafiek van F4
- De volledigheid van het accountprofiel controleren door te bladeren in voorbeeldaccountprofielen

**documentatie van Experience League:**

- [Real-Time CDP B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [B2B-schema&#39;s in Real-Time CDP](https://experienceleague.adobe.com/nl/docs/experience-platform/rtcdp/schemas/b2b)
- [Marketo Engage-connector](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce-connector](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/crm/salesforce)

### Fase 2: Evaluatie van het accountpubliek

In deze fase worden publiek op accountniveau gedefinieerd en geëvalueerd met behulp van een combinatie van accountkenmerken, personekenmerken en persoonactiviteit-gegevens.

**de functie van de Toepassing:** [!DNL RT-CDP] B2B: De Evaluatie van het publiek van de rekening, [!DNL RT-CDP]: De Evaluatie van het publiek

**wat u zult vormen:** Deze fase bepaalt en evalueert rekening-vlakke publiek gebruikend een combinatie rekeningsattributen, persoonattributen, en gegevens van de persoonactiviteit. Met het accountpubliek in [!DNL RT-CDP] B2B edition kunt u accounts segmenteren op basis van zowel de firmografische kenmerken (industrie, inkomsten, personeelsbestand) als het betrokkenheidsgedrag van personen die bij deze accounts horen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: De evaluatiemethode van de Audience**
>
>Hoe snel moet de update van het gebruikerslidmaatschap worden uitgevoerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Batchbeoordeling (dagelijks) | Campagnepubliek verfrist zich op een dagelijkse cadence, bestandsgebaseerde activering, publiek reclameplatform | De meeste accountgebruikers maken gebruik van batchevaluatie. Verwerkt complexe query&#39;s met meerdere entiteiten waarin account- en persoonkenmerken worden gecombineerd. Volstaan voor de meeste B2B-gebruikgevallen waarbij dagelijkse vernieuwing acceptabel is. |
>| Streaming evaluatie | [!DNL Marketo] of CRM-activering wanneer kwalificatie in real-time vereist is | Accountpubliek heeft beperkte mogelijkheden voor streaming. Alleen eenvoudige accountkenmerkvoorwaarden komen in aanmerking voor streamingevaluatie. Voor gedragscondities op individueel niveau is doorgaans een batch vereist. |

>[!NOTE]
>**Besluit: De benadering van de de publieksdefinitie van de rekening**
>
>Hoe definieert u de criteria voor het accountpubliek?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alleen accountkenmerken | Eenvoudig, zelfgrafisch gericht (industrie, opbrengst, regio) | Snelst te implementeren. Beperkt tot gegevens op accountniveau. Gebruik voor brede doelframes. |
>| Account + persoonkenmerken | Doelaccounts waarbij geassocieerde personen voldoen aan specifieke criteria (functie, afdeling) | Nauwkeuriger doelframes. Combineert firmografische en demografische gegevens. |
>| Account + persoonkenmerken + persoonactiviteit | Bezig accounts af te stemmen op betrokken contactpersonen (e-mail wordt geopend, webbezoeken, downloaden van inhoud) | Het krachtigste maar meest complexe. Vereist gedragsgebeurtenisgegevens van F3. Gewoonlijk is batchevaluatie vereist. |
>| Samenstelling publiek | Complexe publiekslogica die bewerkingen met een rang, gesplitst, uitsluiten of verrijken vereist | Gebruik het visuele canvas van de Samenstelling van de Publiek voor afgeleid rekeningspubliek. Beperkt tot batchbeoordeling. |

>[!NOTE]
>**Besluit: De strategie van het publiek van de onderdrukking**
>
>Welke rekeningen zouden van activering moeten worden uitgesloten?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Bestaande klantenonderdrukking | Aankoopcampagnes gericht op nieuwe nettorekeningen | Accounts met actieve abonnementen of closed-won-kansen uitsluiten |
>| Actieve onderdrukking van de verkoopcyclus | Belemmert u niet met accounts in actieve verkoopovereenkomst | Exclusief accounts met open mogelijkheden boven een bepaalde fase |
>| Recente onderdrukking van betrokkenheid | Overberichten over onlangs gecontacteerde accounts voorkomen | Rekeningen uitsluiten die binnen een terugkijkvenster worden gebruikt (bijvoorbeeld 30 dagen) |
>| Geen onderdrukking | Merk-bewustmakingscampagnes gericht op alle in aanmerking komende accounts | Wees voorzichtig; kan leiden tot verspilling van uitgaven voor niet-subsidiabele accounts |

**navigatie UI:** Klant > Soorten publiek > leidt publiek tot > de regel van de Bouwstijl (uitgezochte Rekening als het publiekstype)

**Zeer belangrijke configuratiedetails:**

- Selecteer &quot;Account&quot; als type publiek bij het maken van een nieuw publiek in Segment Builder
- Accountkenmerken worden weergegeven onder de sectie Account in Segment Builder (sector, inkomsten, status van account)
- De attributen en de activiteiten van de persoon kunnen door de verhouding van &quot;Mensen&quot;in de bouwer van het rekeningspubliek worden toegevoegd
- Batchevaluatieschema configureren als er nog geen bestaat voor de sandbox
- Doelgroepen maken (accounts om op te nemen) en publiek onderdrukken (accounts om uit te sluiten)

**documentatie van Experience League:**

- [Accountpubliek](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/types/account-audiences)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/segment-builder)
- [Samenstelling publiek](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/audience-composition)
- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home)

### Fase 3: Doelconfiguratie

Deze fase vestigt voor authentiek verklaarde verbindingen aan de doelbestemmingen waar de rekeningspubliek zal worden geleverd.

**functie van de Toepassing:** [!DNL RT-CDP] B2B: De Configuratie van de Bestemming van de rekening, [!DNL RT-CDP] B2B: [!DNL Marketo Engage] Integratie, [!DNL RT-CDP]: de Configuratie van de Bestemming

**wat u zult vormen:** Deze fase vestigt voor authentiek verklaarde verbindingen aan de doelbestemmingen waar het rekeningspubliek zal worden geleverd. De configuratie omvat het selecteren van de bestemming van de catalogus, het verstrekken van authentificatiegeloofsbrieven, het vormen rekening-vlakke en persoon-vlakke gebiedstoewijzingen, en het plaatsen van het de uitvoerprogramma. Elk bestemmingstype heeft unieke vereisten en mogelijkheden.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: de selectie van de Bestemming**
>
>Welke bestemming(en) zal (zullen) het geactiveerde accountpubliek ontvangen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| [!DNL Marketo Engage] | B2B-begeleiding, scoring en uitvoering van campagnes | Geïntegreerde streamingaansluiting. Hiermee werkt u de hoofd-/contactgegevens bij. Vereist [!DNL Marketo] API-referenties (Munchkin-id, client-id, clientgeheim). |
>| [!DNL LinkedIn] Overeenkomende soorten publiek | Reclame op basis van account op [!DNL LinkedIn] | Ondersteunt de bedrijfsnaam en domeinovereenkomst voor het zoeken op accountniveau. Batchactivering. Vereist toegang tot [!DNL LinkedIn] Campagnebeheer. |
>| [!DNL Salesforce] CRM | Verkoopmogelijkheden en synchronisatie van CRM-accountlijsten | Streaming connector werkt account- of contactrecords bij. Vereist [!DNL Salesforce] API-toegang met schrijfmachtigingen. |
>| [!DNL Microsoft Dynamics 365] | Verkoopmogelijkheden voor op [!DNL Dynamics] gebaseerde organisaties | Streaming connector. Hiervoor is [!DNL Dynamics 365] API-toegang vereist. |
>| Cloudopslag ([!DNL S3], [!DNL Azure Blob], [!DNL GCS], SFTP) | Aangepaste integratie, gegevenspakje, partner delen | Op bestanden gebaseerde batchexport. Maximale flexibiliteit maar downstreamverwerking. |
>| [!DNL Google] Klantenovereenkomst | Doelgerichtheid van zoekopdrachten en displays | Overeenkomsten op persoonlijk niveau via gehashte e-mail. Batchactivering. |
>| [!DNL The Trade Desk] | Programmatische weergave en videoreclame | Person-level aanpassing. Batchactivering. |

>[!NOTE]
>**Besluit: De strategie van de kartering van het gebied**
>
>Welke account- en persoonvelden moeten worden toegewezen aan de bestemming?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alleen identiteitsvelden | Advertising-platforms die alleen overeenkomende id&#39;s nodig hebben | Minimale gegevensoverdracht. Doel komt overeen met e-mail- of bedrijfsdomein. |
>| Identiteit + kernaccountkenmerken | CRM of [!DNL Marketo] waar de context van de account de focus verbetert | Inclusief industrie, inkomsten, personeelsbestand, accountniveau. Verrijk downstreamrecords. |
>| Volledige kenmerkset | Exporteren van cloudopslag of gegevenspakhuis | Alle relevante account- en persoonkenmerken opnemen. Grootste exportlading. |

**navigatie UI:** Verbindingen > Doelen > Catalogus > Onderzoek naar bestemming > vormen

**Zeer belangrijke configuratiedetails:**

- Navigeer naar de catalogus Doelen en selecteer het doeldoel
- Geef verificatiereferenties op die specifiek zijn voor het doeltype
- Veldtoewijzingen configureren die [!DNL RT-CDP] XDM-velden verbinden met doelvelden
- Voor [!DNL Marketo Engage]: geef Munchkin-id, client-id en clientgeheim op
- Voor [!DNL LinkedIn]: autoriseren via OAuth en het [!DNL LinkedIn] ad-account selecteren
- Voor cloudopslag: geef de naam van de emmertje/container, het pad, de bestandsindeling en de referenties op
- Voor CRM: geef instantie-URL, API-referenties en doelobjecttype (Account of Contact) op

**waar de opties uiteenlopen:**

**voor Optie A ([!DNL Marketo Engage] het stromen):**

Ga naar Doelen > Catalogus > Adobe > [!DNL Marketo Engage] . Configureer de Munchkin-id en API-referenties. Wijs [!DNL RT-CDP] identiteitsvelden (e-mail) en profielkenmerken toe aan [!DNL Marketo] lead velden. De bestemming behandelt automatisch stijgende het stromen updates.

**voor Optie B (de Partij van het Platform van Advertising):**

Navigeer naar Doelen > Catalogus > Advertising/Social > platform selecteren. Autoriseren via OAuth. Configureer het exportschema (aanbevolen: dagelijks). Wijs gehashte e-mailid&#39;s en alle ondersteunde overeenkomende velden toe. Wijs voor [!DNL LinkedIn] bovendien bedrijfsnaam en domeinvelden toe voor overeenkomsten op accountniveau.

**voor Optie C (Op dossier-Gebaseerde Opslag van de Wolk):**

Ga naar Doelen > Catalogus > Cloudopslag > provider selecteren. Vorm emmertje/container, het malplaatje van de dossierweg, en dossierformaat (CSV, JSON, of Parquet). Stel het exportschema in en kies Volledig of incrementeel exporteren. Wijs alle gewenste velden voor account- en persoonkenmerken toe.

**voor Optie D (het Streamen van CRM):**

Navigeer naar Doelen > Catalogus > CRM > selecteren [!DNL Salesforce] of [!DNL Dynamics] . Geef API-referenties en instantie-URL op. Wijs [!DNL RT-CDP] velden toe aan CRM-account of contactvelden. Zorg ervoor dat de CRM aangepaste velden bevat om lidmaatschapsgegevens voor het publiek te ontvangen.

**documentatie van Experience League:**

- [Overzicht van doelen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/home)
- [Doelcatalogus](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Doel van LinkedIn-overeenkomend publiek](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Amazon S3-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)

### Fase 4: Activering van het publiek

Deze fase publiceert het geëvalueerde rekeningspubliek aan de gevormde bestemmingen.

**functie van de Toepassing:** [!DNL RT-CDP] B2B: De rekening Audience Activation, [!DNL RT-CDP]: Audience Activation

**wat u zult vormen:** Deze fase publiceert het geëvalueerde rekeningspubliek aan de gevormde bestemmingen. De activering leidt tot dataflow die het rekeningspubliek (bron) met de externe bestemming (doel) verbindt, past attributenafbeeldingen toe, en stelt de uitvoer volgens het gevormde programma of het stromen gedrag in werking. U zult ook suppressiepubliek vormen om niet in aanmerking komende rekeningen van activering uit te sluiten.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: Het type van de Uitvoer**
>
>Moet de activering volledige publieksmomentopnamen of slechts stijgende veranderingen uitvoeren?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Incrementeel exporteren | Streaming doelen ([!DNL Marketo], CRM) of batchbestemmingen waar downstreamsystemen deltas verwerken | Kleiner gegevensvolume per export. Snellere verwerking. Vereist downstreamsystemen om de status te beheren. Standaard voor streamingdoelen. |
>| Volledig exporteren | Batchbestemmingen waar het downstreamsysteem het volledige publiek vervangt, elke run | Groter gegevensvolume, maar eenvoudiger stroomafwaartse logica. Nuttig wanneer downstreamsystemen de status niet behouden. Beschikbaar voor op bestanden gebaseerde doelen. |

>[!NOTE]
>**Besluit: Het werkingsgebied van de Activering**
>
>Hoeveel publiek zou per bestemming moeten worden geactiveerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Eén publiek per gegevensstroom | Eenvoudige activering met duidelijke publiek-naar-bestemmingstoewijzing | Gemakkelijk om te controleren en problemen op te lossen. Eén publieksfout heeft geen invloed op andere gebruikers. |
>| Meerdere soorten publiek per gegevensstroom | Meerdere verwante doelgroepen die naar dezelfde bestemming gaan | Efficiënter gebruik van bestemmingsverbindingen. Alle doelgroepen delen dezelfde veldtoewijzing en hetzelfde schema. |

**navigatie UI:** Verbindingen > Doelen > doorbladeren > Uitgezochte bestemming > actief publiek

**Zeer belangrijke configuratiedetails:**

- Selecteer het doelpubliek of de doelgroepen in de lijst met doelgroepen
- De veldtoewijzingen in fase 3 controleren en bevestigen
- Voor batchbestemmingen: configureer het exportschema (tijd, frequentie)
- Voor streamingdoelen: activering begint direct na configuratie
- Voeg desgewenst suppressiepubliek toe met de functie voor uitsluiten
- Trigger een aanvankelijke test activering om de dataflow te bevestigen

**waar de opties uiteenlopen:**

**voor Optie A ([!DNL Marketo Engage] het stromen):**

Selecteer het accountpubliek dat u wilt activeren. Activering begint direct met streamen. Controleer in [!DNL Marketo] of de hoofd-/contactrecords worden bijgewerkt met de velden voor segmentlidmaatschap. Configureer [!DNL Marketo] slimme campagnes om te activeren op basis van deze veldwijzigingen.

**voor Optie B (de Partij van het Platform van Advertising):**

Selecteer accountpubliek en configureer het dagelijkse exportschema. Nadat de eerste export is voltooid, controleert u in het advertentieplatform of het publiek wordt weergegeven en of het lid een populatiegraad heeft. 24-48 uur toestaan voor het platform om het eerste publieksbestand te verwerken.

**voor Optie C (Op dossier-Gebaseerde Opslag van de Wolk):**

Selecteer een accountpubliek en configureer het exportschema en de bestandsindeling. Na de eerste exportbewerking worden de bestanden op de doelopslaglocatie weergegeven met de verwachte indeling en inhoud. Bevestig downstream-importprocessen waarbij de geëxporteerde bestanden zijn verwerkt.

**voor Optie D (het Streamen van CRM):**

Selecteer het accountpubliek dat u wilt activeren. Activering begint direct met streamen. Verifieer in CRM dat de rekening of contactverslagen met de in kaart gebrachte gebieden worden bijgewerkt. Vorm de rapporten van CRM, lijstmeningen, of werkschemaautomatisering om op de bijgewerkte gebieden te handelen.

**documentatie van Experience League:**

- [Stimulansen voor het publiek naar streamingdoelen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Soorten publiek naar batchbestemmingen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activeringsinstructies](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/guardrails)
- [Overzicht van doelen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/home)

### Fase 5: Bestuur en toezicht

Deze fase zorgt ervoor dat de activering van het accountpubliek in overeenstemming is met het gegevensbeheerbeleid en de voorkeuren voor toestemming en dat doorlopende activeringsgegevensstromen worden gecontroleerd op gezondheid.

**de functie van de Toepassing:** [!DNL RT-CDP] B2B: B2B de Governance van Gegevens, [!DNL RT-CDP]: Toestemming &amp; de Handhaving van het Bestuur

**wat u zult vormen:** Deze fase zorgt ervoor dat de activering van het rekeningspubliek aan het beleid van het gegevensbeheer en toestemmingsvoorkeur voldoet, en dat de aan de gang zijnde activeringsdataflows voor gezondheid worden gecontroleerd. B2B-gegevensbeheer handhaaft beperkingen op gevoelige rekeningkenmerken (inkomsten, personeelsbestand van derden), terwijl handhaving van de instemming garandeert dat communicatie op persoonniveau de voorkeuren voor opt-out respecteert. De controle bevestigt dat de activeringsgegevensstromen met succes voltooien.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>**Besluit: Het handhavingsniveau van de governance**
>
>Hoe strikt moet gegevensbeheer worden gehandhaafd voor B2B-activiteiten?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Volledige handhaving (blok bij overtreding) | Productieactiviteiten met gevoelige gegevens | Verhindert elke activering die het governancebeleid schendt. Mogelijk moet u de toewijzingen van herhalende velden aanpassen om overtredingen te verhelpen. |
>| Waarschuwen en doorgaan | Ontwikkelings- of testomgevingen | Hiermee kan de activering worden uitgevoerd, maar worden waarschuwingen geregistreerd. Nuttig tijdens de eerste installatie om potentiële problemen te identificeren. |

>[!NOTE]
>**Besluit: De benadering van de controle**
>
>Hoe moet de activeringsgezondheid worden gecontroleerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Waarschuwing gebaseerd op bewaking | Productieomgevingen waar fouten snel moeten worden opgevangen | Vorm alarm voor de mislukkingen van de bestemmingsactivering, de mislukkingen van de bronstroom, en dataflow vertragingen. Vereist installatie van een waarschuwingsabonnement. |
>| Handmatige controle | Ontwikkeling of activering van geringe volumes | Periodiek overzicht dataflow loopt in de Doelen UI. Minder overhead, maar het risico van vertraagde storingsdetectie. |
>| Beide | Productieomgevingen met complexe activering van meerdere doelen | Waarschuwingen voor kritieke fouten en periodieke dashboardcontrole voor trends. Aanbevolen voor de meeste B2B-implementaties. |

**navigatie UI:** Privacy > Beleid (voor bestuur), Verbindingen > Doelen > doorbladeren > Uitgezochte bestemming > looppas Dataflow (voor controle)

**Zeer belangrijke configuratiedetails:**

- Labels voor gegevensgebruik toepassen op B2B-gegevenssets die beperkte kenmerken bevatten
- Controleren of het beleid inzake governance wordt nageleefd door de activering te evalueren aan de hand van de marketingactie target
- Waarschuwingen configureren voor fouten bij doelactivering en fouten met bronaansluiting
- Metrische gegevens voor gegevensstroomuitvoering controleren (profielen geëxporteerd, records mislukt) na elke activeringscyclus
- Dashboardrevisie voor licentiegebruik instellen om het volume van het accountprofiel op te sporen met rechten

**documentatie van Experience League:**

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home)
- [Toestemming en voorkeuren](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)
- [Doelgegevens bewaken](https://experienceleague.adobe.com/nl/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/alerts/overview)
- [Activeringsinstructies](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/guardrails)

## Implementatieoverwegingen

De volgende secties bieden extra aanwijzingen voor een geslaagde implementatie.

### Afbeeldingen en limieten

Bekijk de volgende platforminstructies en -limieten die van toepassing zijn op dit gebruikspatroon.

- Maximum van 4.000 segmentdefinities per zandbak, met inbegrip van rekeningspubliek — [&#x200B; de gidsen van de Segmentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)
- Accountpubliek wordt primair geëvalueerd aan de hand van batchevaluatie; streamingmogelijkheden zijn beperkt tot eenvoudige voorwaarden voor accountkenmerken
- Maximum van 100 dataflows per bestemmingsverbinding - [&#x200B; de waarborgen van Doelen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/guardrails)
- Batchdoelen exporteren maximaal 5 miljoen profielen per bestandssegment
- Streaming doelen hebben een doorvoerlimiet per seconde die is ingesteld door de doelpartner (bijvoorbeeld [!DNL Marketo] API-snelheidlimieten)
- Samengesteld publiek (van Audience Composition) is beperkt tot batchevaluatie en kan geen streaming gebruiken
- Maximum van 10 samenstellingsblokken per het canvas van de Samenstelling van het Publiek
- [!DNL LinkedIn] Voor activering is een minimale doelgrootte (meestal 300 leden) vereist voor passend publiek
- CRM-streamingdoelen zijn onderworpen aan de API-snelheidslimieten van de CRM-provider (bijv. de dagelijkse limieten van [!DNL Salesforce] bulk API)
- [!DNL RT-CDP] B2B edition vergunning regelt het totale aantal profielen van de bedrijfsrekening — [&#x200B; RT-CDP productbeschrijving &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

### Veelvoorkomende valkuilen

Houd rekening met de volgende algemene problemen wanneer u dit gebruikspatroon implementeert.

- **Onvolledige persoon-aan-rekening afbeelding:** als de persoonverslagen (lood, contacten) niet behoorlijk met rekeningsverslagen door B2B identiteitsresolutie worden verbonden, zullen de rekeningspubliek dat van persoonattributen of activiteiten afhangt gekwalificeerde rekeningen onderschrijven. Valideer relaties van persoon tot account in F4 voordat u accountpubliek gaat opbouwen.

- **de gegevens van CRM van de Stale die publieksdrift veroorzaken:** als de bron van CRM schakelaars niet op een regelmatig programma lopen of stil ontbreken, worden de rekeningsattributen (industrie, opbrengst, status) stale. Dit leidt ertoe dat het publiek accounts opneemt die niet langer in aanmerking komen of die accounts uitsluiten die in aanmerking zouden moeten komen. Dataflow health van de bronconnector van de monitor.

- **het platform van Advertising past tariefverwachtingen aan:** wanneer het activeren van rekeningspubliek aan reclameplatforms buiten [!DNL LinkedIn], hangt het gelijke tarief van het hebben van geldige persoon-vlakke herkenningstekens (gehakt e-mail) voor contacten verbonden aan kwalificerende rekeningen af. Accounts zonder bijbehorende contactpersonen met e-mailadressen komen niet overeen. Monitor stemt overeen met snelheden en u kunt overwegen contactgegevens te verrijken.

- **[!DNL Marketo]onjuist uitlijnen van veldtoewijzing:** bij streaming naar [!DNL Marketo Engage] moet de [!DNL RT-CDP] veldtoewijzing gericht zijn op bestaande lood- of contactvelden [!DNL Marketo] . Als het toegewezen veld [!DNL Marketo] niet bestaat, mislukt de update zonder toezicht. Maak vooraf alle doelvelden in [!DNL Marketo] voordat u het doel configureert.

- **beleid dat van de Governance activering blokkeert:** de etiketten van het gegevensgebruik op de gebieden van de rekeningsattributen (vooral derde firmographic gegevens) kunnen governanceschendingen teweegbrengen wanneer het activeren aan reclamebestemmingen. Evalueer naleving van governance alvorens gebiedstoewijzingen te activeren en aan te passen om beperkte gebieden indien nodig uit te sluiten.

- **het publiek van de Rekening die rekening en persoongegevens met partij-enige evaluatie combineren:** het publiek van de Rekening dat persoon-vlakke gedragsgebeurtenissen van verwijzingen voorziet (b.v., &quot;rekeningen waar minstens één contact een e-mail in de laatste 30 dagen opende&quot;) vereisen partijevaluatie. Als het gebruiksgeval kwalificatie in real time verwacht, kan deze beperking onverwachte latentie veroorzaken.

### Aanbevolen procedures

Volg deze aanbevelingen voor optimale resultaten.

- Begin met een klein aantal duidelijk gedefinieerde accountsoorten (ICP-niveau, industrie-verticaal, betrokkenheidsniveau) voordat u de definitie van meerdere kenmerken uitbreidt
- Maak een speciaal suppressiepubliek voor bestaande klanten, actieve kansen en recent aangegane accounts om verspilde uitgaven en kanaalconflicten te voorkomen
- Gebruik Audience Composition om gelaagde accountsoorten te maken (hoge/gemiddelde/lage betrokkenheid) door accounts te rangschikken op geaggregeerde betrokkenheidsscores
- Hetzelfde accountpubliek tegelijkertijd naar meerdere doelen activeren voor gecoördineerde multikanaalscampagnes (bijvoorbeeld [!DNL LinkedIn] voor advertenties, [!DNL Marketo] voor e-mail, CRM voor zichtbaarheid bij verkoop)
- Voer een verenigbare noemende overeenkomst voor rekeningspubliek uit die de het richten criteria en voorgenomen kanaal omvat (b.v., &quot;B2B_ICP_Enterprise_Tech_LinkedIn&quot;of &quot;B2B_Suppression_ActiveOpps&quot;)
- Batchactivering plannen tijdens niet-piekuren om het effect op downstreamsystemen tot een minimum te beperken en zich aan te passen aan de verwerkingsvensters van advertentieplatforms
- Gelijke percentages per bestemming controleren na de eerste activering en de toewijzingen van identiteitsvelden herhalen om de overeenkomst te verbeteren
- Bidirectionele gegevensstroom behouden met [!DNL Marketo Engage]: gegevens over de betrokkenheid van [!DNL Marketo] in [!DNL RT-CDP] (bronaansluiting) opnemen en het publiek weer activeren naar [!DNL Marketo] (doelaansluiting) voor een gesloten-lussysteem

### Handelsbesluiten

Houd rekening met de volgende compromissen wanneer u uitvoeringsbesluiten neemt.

>[!NOTE]
>**handel-off: De versheid van het publiek tegenover de ingewikkeldheid van de evaluatie**
>
>Accountpubliek dat accountkenmerken combineert met gedragsgegevens op persoonniveau, biedt de meest nauwkeurige doelgroep, maar is beperkt tot batchevaluatie (dagelijks vernieuwen). Eenvoudiger publiek op basis van alleen accountkenmerken kan in aanmerking komen voor streamingevaluatie met updates in real-time.
>
>- **de Partij (complexe criteria) bevordert:** het richten precisie, het combineren van firmografische en gedragssignalen, uitvoerige rekening het scoren
>- **het stromen (eenvoudige criteria) bevordert:** Snelheid van publieksupdates, reactie in real time aan rekeningsveranderingen, snellere tijd-aan-actie in [!DNL Marketo] en CRM
>- **Aanbeveling:** de partijevaluatie van het gebruik voor primair gericht publiek waar dagelijks verfrist is aanvaardbaar (de meeste B2B gebruiksgevallen). Evaluatie van streaming reserveren voor tijdgevoelige triggers zoals wijzigingen in de status van de account of waarschuwingen voor accounts met een hoge waarde.

>[!NOTE]
>**handel-off: Gecentraliseerde activering vs. bestemmings-specifiek publiek**
>
>U kunt één uniform accountpubliek activeren voor meerdere doelen, of doelspecifieke doelgroepen maken die zijn afgestemd op de mogelijkheden en vereisten van elk kanaal.
>
>- **Gecentraliseerde publieksvoorkeur:** Consistentie over kanalen, eenvoudiger publieksbeheer, verenigde rapportering
>- **Bestemming-specifieke publiek begunstigt:** Geoptimaliseerd gericht aan per kanaal (b.v., [!DNL LinkedIn] voordelen van bedrijf-vlakke attributen terwijl [!DNL Marketo] lood-vlakke details), kanaal-specifieke suppressieregels vereist
>- **Aanbeveling:** Begin met gecentraliseerd publiek voor consistentie, creeer dan bestemmings-specifieke varianten slechts wanneer de kanaalvereisten beduidend afwijken (b.v., verschillende onderdrukkingsvensters voor reclame vs. e-mail).

>[!NOTE]
>**handel-off: synchronisatie in real time CRM vs. de updates van batch CRM**
>
>Streaming naar CRM biedt direct zicht op de verkoop, maar verbruikt de CRM API-quota. Het exporteren van batchbestanden is efficiënter, maar zorgt voor latentie.
>
>- **het stromen synchronisatie van CRM verkiest:** de reactiesnelheid van de verkoop, directe rekeningsalarm, pijpleidingszicht in real time
>- **de updates van CRM van de Partij verkiest:** API quotabehoud, bulkupdateefficiency, groepering met de gegevens die van CRM vensters laden
>- **Aanbeveling:** Gebruik het stromen synchronisatie van CRM voor de veranderingen van de hoge prioritaire rekeningskwalificatie (b.v., rekeningsbewegingen aan &quot;Klaar van de Verkoop&quot;rij). U kunt batchbestanden exporteren voor bulkupdates, zoals maandelijkse versies voor het noteren van accounts of lijsten voor het opnieuw toewijzen van gebieden.

## Gerelateerde documentatie

De volgende bronnen bieden aanvullende context en gedetailleerde instructies voor de mogelijkheden die in dit gebruikspatroon worden gebruikt.

**[!DNL RT-CDP]B2B edition**

- [Real-Time CDP B2B edition - overzicht](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/overview#rtcdp-b2b)
- [B2B-schema&#39;s in Real-Time CDP](https://experienceleague.adobe.com/nl/docs/experience-platform/rtcdp/schemas/b2b)
- [Accountpubliek](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/types/account-audiences)
- [RT-CDP B2B edition productbeschrijving](https://helpx.adobe.com/nl/legal/product-descriptions/real-time-customer-data-platform-b2b-edition-prime-and-ultimate-packages.html)

**de evaluatie en segmentatie van het publiek**

- [Overzicht van segmentatieservice](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/home)
- [Handleiding voor de gebruikersinterface van Segment Builder](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/segment-builder)
- [Samenstelling publiek](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/audience-composition)
- [Streaming segmentering](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/methods/streaming-segmentation)
- [Segmenteringsgeleiding](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/guardrails)

**Doelen &amp; activering**

- [Overzicht van doelen](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/home)
- [Doelcatalogus](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/overview)
- [Marketo Engage-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/adobe/marketo-engage)
- [Doel van LinkedIn-overeenkomend publiek](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/social/linkedin)
- [Salesforce CRM-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/crm/salesforce)
- [Microsoft Dynamics 365-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/crm/microsoft-dynamics-365)
- [Amazon S3-bestemming](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/cloud-storage/amazon-s3)
- [Stimulansen voor het publiek naar streamingdoelen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-segment-streaming-destinations)
- [Soorten publiek naar batchbestemmingen activeren](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-batch-profile-destinations)
- [Activeringsinstructies](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/guardrails)

**de bronnen &amp; de schakelaars van Gegevens**

- [Overzicht van bronnen](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/home)
- [Marketo Engage-connector](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
- [Salesforce-connector](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/crm/salesforce)

**modellering van Gegevens &amp; identiteit**

- [XDM System, overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/home)
- [Overzicht van identiteitsservice](https://experienceleague.adobe.com/nl/docs/experience-platform/identity/home)
- [Profieloverzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/home)
- [Overzicht van beleid samenvoegen](https://experienceleague.adobe.com/nl/docs/experience-platform/profile/merge-policies/overview)

**Beheer van Gegevens &amp; privacy**

- [Datagovernance - Overzicht](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home)
- [Overzicht van labels voor gegevensgebruik](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/labels/overview)
- [Toestemming en voorkeuren](https://experienceleague.adobe.com/en/docs/experience-platform/data-governance/consent/adobe/overview)

**Controle &amp; waarneming**

- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/alerts/overview)
- [Doelgegevens bewaken](https://experienceleague.adobe.com/nl/docs/experience-platform/dataflows/ui/monitor-destinations)
- [Brongegevens controleren](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/api-tutorials/monitor)
- [Het gebruiksdashboard voor licenties](https://experienceleague.adobe.com/en/docs/experience-platform/landing/license-usage-and-guardrails/license-usage-dashboard)

**Rapportering &amp; analyses**

- [CJA-overzicht](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-overview/cja-overview)
- [Overzicht van verbindingen](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-connections/overview)
- [Overzicht van gegevensweergaven](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-dataviews/data-views)

**Zelfstudies &amp; gidsen**

- [Aan de slag met Real-Time CDP B2B edition](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro)
- [Een schema maken voor B2B-bronnen](https://experienceleague.adobe.com/nl/docs/experience-platform/rtcdp/schemas/b2b)
- [Sandbox Tooling](https://experienceleague.adobe.com/nl/docs/experience-platform/sandbox/sandbox-tooling-api/overview)
