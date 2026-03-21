---
title: Gebeurtenis doorsturen
description: Leer hoe u real-time gebeurtenisgegevens die via Edge Network zijn verzameld, kunt doorsturen naar niet-Adobe-bestemmingen voor analyses, opslag of reclame.
solution: Experience Platform
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '6342'
ht-degree: 0%

---


# Gebeurtenis doorsturen

Deze handleiding behandelt de implementatie van het doorsturen van gebeurtenissen aan de serverzijde met behulp van [!DNL Adobe Experience Platform] Edge Network. Het is ontworpen voor oplossingsarchitecten, marketingtechnici en implementatietechnici die realtime gebeurtenisgegevens die via de Edge Network zijn verzameld, moeten verspreiden naar niet-Adobe-bestemmingen, zoals analyseplatforms van derden, eindpunten voor cloudopslag, advertentienetwerken of aangepaste websites.

Het biedt een overzicht van alle haalbare benaderingen voor het configureren van het doorsturen van gebeurtenissen, legt de afwegingen tussen de twee oplossingen uit en legt koppelingen naar [!DNL Adobe Experience League] -documentatie voor gedetailleerde procedurele richtlijnen.

## Hoofdlettergebruik

Organisaties die gedragsgegevens verzamelen via de [!DNL Adobe Experience Platform] Web SDK, Mobile SDK of Server API moeten vaak dezelfde gebeurtenisstroom delen met niet-Adobe-systemen, zoals analyseplatforms zoals [!DNL Google Analytics] of [!DNL Snowflake] , advertentienetwerken voor het bijhouden van conversies, gegevensopslagruimten voor langetermijnopslag of aangepaste interne services. Dit vereiste proliferatie van tags aan de clientzijde, waardoor het paginagewicht toeneemt, latentie ontstaat en privacy- en governancerisico&#39;s ontstaan.

Gebeurtenis die door:sturen lost dit door server-kant op Edge Network in werking te stellen op. Wanneer een bezoekersinteractie een gebeurtenis door het Web SDK of Server API teweegbrengt, wordt die gebeurtenis verpletterd door een gegevensstroom aan Edge Network. Gebeurtenis door:sturen regels — gevormd in een specifieke gebeurtenis die bezit door:sturen — evalueer de inkomende gebeurtenisgegevens en door:sturen selectief het aan één of meerdere gevormde bestemmingen. Deze server-kant benadering vermindert cliënt-zijmerkblokkering, verbetert paginaprestaties, centraliseert gegevensbeheer, en geeft de organisatie controle over precies wat gegevens het ecosysteem van Adobe verlaten.

Het doelpubliek voor dit patroon bevat organisaties die de [!DNL Adobe Experience Platform] Web SDK of Server API voor gegevensverzameling al hebben geïmplementeerd (of van plan zijn te implementeren) en die investering willen uitbreiden door gebeurtenisgegevens te verspreiden naar niet-Adobe-eindpunten zonder JavaScript-tags aan de client-side toe te voegen.

## Belangrijkste bedrijfsdoelstellingen

De volgende bedrijfsdoelstellingen worden gesteund door dit gebruiks gevalpatroon.

### Kwaliteit en bestuur van gegevens verbeteren

Zorg voor schone, volledige en compatibele gegevens voor nauwkeurige doelgerichtheid, verminderd afval en betrouwbare analyses. Bij het doorsturen van gebeurtenissen wordt de gegevensdistributie aan de serverzijde gecentraliseerd, waardoor de organisatie één enkel controlepunt krijgt voor welke gegevens met externe systemen worden gedeeld, waardoor het risico op gegevenslekkage wordt verminderd en het beleid voor het beheer wordt toegepast voordat gegevens de Edge Network van [!DNL Adobe] verlaten.

**KPIs:** Efficiëntie, Kostenbesparingen

Voor meer informatie, zie [&#x200B; de kwaliteit en het bestuur van gegevens verbeteren &#x200B;](../../business-objectives/cost-efficiency/improve-data-quality-governance.md).

### Consolideer en moderniseer marketingtechnologie

Verminder hulpmiddelfragmentatie en technische schuld door aan verenigde, scalable platforms te migreren. Het door:sturen van gebeurtenissen laat organisaties toe om veelvoudige cliënt-zijverkopermarkeringen met één enkel server-zijmechanisme van de gegevensdistributie te vervangen, die paginalading overheadkosten verminderen en de technologiestapel vereenvoudigen.

**KPIs:** Kostenbesparingen, Efficiëntie, Snelheid aan Markt

Voor meer informatie, zie [&#x200B; marketing technologie &#x200B;](../../business-objectives/cost-efficiency/consolidate-modernize-marketing-technology.md) consolideren en moderniseren.

## Voorbeelden van tactische gebruiksgevallen

Hieronder vindt u algemene tactische scenario&#39;s waarin dit gebruikspatroon wordt toegepast.

- **de verrijking van de de analysemogelijkheden van de derde** — Voorwaartse paginamening, klik, en omzettingsgebeurtenissen aan [!DNL Google Analytics], [!DNL Snowflake], of andere analyseplatforms in echt - tijd zonder cliënt-zijmarkeringen toe te voegen
- **het omzetvolgen van Advertising** — verzend aankoop en lood-generatie gebeurtenissen aan [!DNL Meta] Conversies API, [!DNL Google Ads], [!DNL TikTok], of [!DNL Snap] voor server-zijomzettingsmeting en optimalisering
- **het entrepot van Gegevens die** stromen - de ruwe gebeurtenisgegevens van de Route aan een entrepot van wolkengegevens ([!DNL Google BigQuery], [!DNL Amazon S3], [!DNL Azure Event Hubs]) voor opslag op lange termijn en off-line analyse
- **Web-haakintegratie van de Douane** — Door:sturen gefilterde of getransformeerde gebeurtenisgegevens aan interne microservices, de systemen van CRM, of partnerplatforms via HTTP eindpunten
- **de vermindering van de markering en de verbetering van de paginaprestaties** — Vervang de veelvoudige cliënt-zijleveranciersJavaScript markeringen met één enkele implementatie van SDK van het Web plus server-zij gebeurtenis door:sturen regels, die paginagewicht verminderen en Core Web Vitals verbeteren
- **Privacy-volgzame gegevens die** delen - pas gegevens het filtreren en gebied-vlakke redactieregels server-kant toe alvorens gebeurtenisgegevens met derden te delen, die PII verzekeren wordt gestript of gehakt alvorens het externe systemen bereikt
- **Multicloud gebeurtenisdistributie** - door:sturen gelijktijdig de zelfde gebeurtenisstroom aan veelvoudige bestemmingen (bijvoorbeeld, analyses, reclame, en gegevenspakhuis) van één enkele server-zij regelreeks
- **Real-time het fraudesignaal door:sturen** — Door:sturen high-value transactiegebeurtenissen aan de systemen van de fraudeopsporing voor risico het scoren in real time en alarmerend

## Kernprestatie-indicatoren

De volgende KPIs helpt het succes van dit gebruiks gevalpatroon meten.

- **de tijdvermindering van de ladingstijd van de Pagina** — Gemeten verbetering in de snelheid van de paginading en Core Web Vitals na het migreren van cliënt-zijmarkeringen aan server-zij gebeurtenis door:sturen
- **het succestarief van de levering van gegevens** — Percentage gebeurtenissen met succes door:sturen aan bestemmings eindpunten zonder fouten of onderbrekingen
- **de tellingsvermindering van de markering** — Aantal cliënt-zijverkopermarkeringen die na het uitvoeren van server-zijequivalenten worden verwijderd
- **de fris/latentie van Gegevens** — Tijd tussen gebeurtenisvoorkomen op de cliënt en gebeurtenisaankomst bij het bestemmingspunt (doel: sub-seconde aan seconden)
- **de nalevingstarief van de Governance** — Percentage van uitgaande gegevensaandelen die door server-zij het filtreren regels overgaan, die geen PII of beperkte gegevens verzekeren bereikt onbevoegde bestemmingen
- **Operationele efficiency** — Vermindering in ontwikkelaarsuren besteed het beheren van cliënt-kant markeringsplaatsingen en het oplossen van problemenmarkeringsconflicten

## Hoofdletterpatroon gebruiken

Deze sectie beschrijft het patroon en de functieketen die worden gebruikt om gebeurtenis uit te voeren door:sturen.

**Gebeurtenis door:sturen** — Door:sturen gebeurtenisgegevens in real time die via Edge Network aan niet-Adobe bestemmingen voor analyse, opslag, of reclame worden verzameld.

**Keten van de Functie:** Configuratie DataStream > de Definitie van de Regel van de Gebeurtenis > Toewijzing van de Bestemming > Door:sturen Uitvoering > Controle

## Applicaties

In dit gebruikspatroon worden de volgende toepassingen gebruikt.

- **[!DNL Adobe Experience Platform] (Edge Network)** — Ontvangt en leidt gebeurtenisgegevens in real time van Web SDK, Mobiele SDK, of Server API door gevormde gegevensstromen
- **[!DNL Adobe Experience Platform] (Gebeurtenis door:sturen)** — Verstrekt de server-zijregelmotor voor evaluatie, het filtreren, het transformeren, en het door:sturen van gebeurtenisgegevens aan externe bestemmingen
- **[!DNL Adobe Experience Platform] (Codes/de Inzameling van Gegevens)** — Beheert de gebeurtenis die bezitslevenscyclus, uitbreidingen, regels, en het publiceren werkschema door:sturen

## Foundbootfuncties

Voor dit gebruikspatroon moeten de volgende basisfuncties aanwezig zijn. Voor elke functie, wijst de status erop of het typisch wordt vereist, verondersteld om vooraf te worden gevormd, of niet van toepassing.

| Foundary Function | Status | Wat moet er gebeuren? | Experience League Reference |
| --- | --- | --- | --- |
| Beheer en bestuur | Vereist | Een zandbak moet actief zijn met aangewezen gevormde gebruikersrollen en toestemmingen. Gebruikers die gebeurtenissen doorsturen, hebben in [!DNL Adobe Admin Console] machtigingen voor gegevensverzameling nodig, waaronder rechten voor het beheren van eigenschappen, extensies en regels voor het doorsturen van gebeurtenissen. | [&#x200B; overzicht van het Toegangsbeheer &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/access-control/home) |
| Gegevensmodellering en -voorbereiding | Vereist | XDM-schema&#39;s moeten worden gedefinieerd voor de gebeurtenisgegevens die door de Edge Network stromen. De gegevensstroom moet een geldig schema van XDM ExperienceEvent van verwijzingen voorzien zodat de gebeurtenis die regels door:sturen tot gestructureerde gebieden voor het filtreren, transformatie, en afbeelding kan toegang hebben. | [&#x200B; XDM overzicht van het Systeem &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/home) |
| Gegevensbronnen en -verzameling | Vereist | Een mechanisme voor gegevensverzameling moet actief zijn — Web SDK, Mobile SDK of Edge Network Server API — gebeurtenissen verzenden via een geconfigureerde gegevensstroom. De gegevensstroom is de fundamentele verpletterende laag die cliënt-zijinzameling met server-zijgebeurtenis verbindt door:sturen. | [&#x200B; vorm gegevensstromen &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/configure) |
| Identiteit en profielconfiguratie | Niet van toepassing | Het door:sturen van gebeurtenissen werkt op ruwe gebeurtenisgegevens bij de laag van Edge Network, alvorens identiteitsresolutie of profieleenwording voorkomt. Identiteitsnaamruimten en samenvoegbeleid worden niet vereist tenzij de door:sturen gebeurtenissen ook aan het Profiel van de Klant in real time moeten bijdragen (dat een afzonderlijke configuratie van de datastream dienst, niet een gebeurtenis is die zorg door:sturen). | |
| Auditiedefinitie en segmentatie | Niet van toepassing | Het door:sturen van de gebeurtenis verwerkt individuele gebeurtenissen in echt - tijd en evalueert publiek geen lidmaatschap. Het op publiek-gebaseerde filtreren is geen deel van de gebeurtenis die functieketen door:sturen. Als activering op basis van het publiek nodig is, raadpleegt u het referentieplan Audience Activation naar bestemmingen. | |

## Ondersteunende functies

De volgende mogelijkheden vergroten dit gebruikspatroon, maar zijn niet vereist voor kernuitvoering.

| Ondersteunende functie | Status | Waarom het belangrijk is | Experience League Reference |
| --- | --- | --- | --- |
| Berekend / Afgeleid kenmerk maken | Niet van toepassing | Het door:sturen van gebeurtenissen werkt op ruwe gebeurtenisgegevens, niet profiel-niveau gegevens verwerkt attributen. De gegevens verwerkte attributen zijn niet beschikbaar in de gebeurtenis die context door:sturen. | |
| Levenscyclusbeheer van gegevens | Aanbevolen | Als gebeurtenisgegevens ook in de datasets van AEP (via zelfde gegevensstroom) worden opgenomen, zou het beleid van het gegevensbehoud (afloop) voor die datasets moeten worden gevormd om opslagkosten en regelgevende naleving te beheren. Het door:sturen van de gebeurtenis zelf slaat geen gegevens op, maar de parallelle weg van de AEP van de opname. | [&#x200B; het Geavanceerde overzicht van het Beheer van de Levenscyclus van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-lifecycle/home) |
| Etikettering en handhaving van gegevensgebruik | Aanbevolen | Terwijl de gebeurtenis die regels door:sturen gebied-vlakke het filtreren verstrekt (die u toestaan om gevoelige gegevens van door:sturen nuttige ladingen uit te sluiten), zorgt het toepassen van de etiketten van het gegevensgebruik op de onderliggende schema&#39;s en datasets ervoor het beleid wordt afgedwongen als het zelfde gegeven voor publieksactivering of verpersoonlijking wordt gebruikt. | [&#x200B; Overzicht van het beheer van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/data-governance/home) |
| Bewaking en waarneming | Opgenomen | Monitoring is essentieel voor het doorsturen van gebeurtenissen. Het Dashboard van de Controle van de Gebeurtenis Door:sturen verstrekt zicht in het door:sturen van succespercentages, foutenpercentages, en de codes van de bestemmingsreactie. Het alarm zou voor bestemmingsmislukkingen moeten worden gevormd. | [&#x200B; Gebeurtenis door:sturen controle &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/monitoring) |
| Rapportage en analyse | Aanbevolen | Als door:sturen gebeurtenissen een platform van de derdeanalyse van de derdeanalyse voorzien, denk na verbindend de zelfde de gebeurtenisdatasets van AEP met CJA voor een verenigde dwars-kanaalmening. Dit maakt een vergelijking mogelijk tussen Adobe-side en derdeanalyse. | [&#x200B; overzicht van CJA &#x200B;](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/cja-overview/cja-overview) |

## Toepassingsfuncties

Dit plan oefent de volgende functies van de Catalogus van de Functie van de Toepassing uit. Functies worden toegewezen aan implementatiefasen in plaats van aan genummerde stappen.

### [!DNL Adobe Experience Platform] (AEP)

| Functie | Implementatiefase | Beschrijving |
| --- | --- | --- |
| Configuratie DataStream | Fase 1: Configuratie DataStream | Configureer een gegevensstroom om Edge Network-gebeurtenissen te ontvangen en de service voor het doorsturen van gebeurtenissen in te schakelen |
| Instellingen van eigenschap voor doorsturen van gebeurtenissen | Fase 2: Event Forwarding Property &amp; Extensions | Creeer een gebeurtenis door:sturen bezit en installeer bestemmingsspecifieke uitbreidingen |
| Definitie van gebeurtenisregel | Fase 3: Definitie gebeurtenisregel | Definieer regels die binnenkomende gebeurtenisgegevens evalueren en bepalen wat er moet worden doorgestuurd en waar |
| Toewijzing bestemming | Fase 3: Definitie gebeurtenisregel | De elementen van gebeurtenisgegevens van de kaart aan bestemmings-specifieke lading formaten binnen het door:sturen regels |
| Uitvoering doorsturen | Fase 4: Publiceren en activeren | Publiceer de gebeurtenis door:sturen configuratie aan Edge Network voor levende uitvoering |
| Monitoring | Fase 5: Bewaking en validatie | Monitor die succespercentages, foutencodes, en bestemmingsgezondheid door:sturen |

## Vereisten

Zorg ervoor dat het volgende op zijn plaats is voordat u begint met de implementatie.

- [ ] [!DNL Adobe Experience Platform] licentie met Edge Network en de machtiging Event Forwarding
- [ ] Machtigingen voor gegevensverzameling geconfigureerd in [!DNL Adobe Admin Console] (eigenschappen, extensies, regels en publiceren beheren voor het doorsturen van gebeurtenissen)
- [ ] Ten minste één actief mechanisme voor gegevensverzameling (Web SDK, Mobile SDK of Server API) dat gebeurtenissen verzendt via een gegevensstroom
- [ ] XDM ExperienceEvent-schema gedefinieerd voor de gebeurtenisgegevens die worden verzameld
- [ ] DataStream gemaakt en gekoppeld aan het verzamelingsmechanisme
- [ ] Referenties en documentatie voor het eindpunt van de bestemming beschikbaar (bijvoorbeeld [!DNL Meta] Conversies API-toegangstoken, [!DNL Google Analytics] meting-id, URL van webhaak, gegevens voor cloudopslag)
- [ ] Begrijpen van het gebeurtenisgegevensmodel en welke velden/gebeurtenissen elk doel vereist

## Implementatieopties

Deze sectie beschrijft de beschikbare benaderingen voor het uitvoeren van gebeurtenis door:sturen en verstrekt raad bij het kiezen van de juiste optie.

### Option A: op extensies gebaseerde gebeurtenis doorsturen

**Best voor:** Teams die goed-gesteunde bestemmingsplatforms ([!DNL Meta] gebruiken, [!DNL Google], [!DNL AWS], [!DNL Azure], [!DNL Snowflake], enz.) die vooraf gebouwde gebeurtenis hebben door:sturen uitbreidingen beschikbaar in de catalogus van de Inzameling van Gegevens.

**hoe het werkt:**

Bij het doorsturen van op extensies gebaseerde gebeurtenissen wordt gebruikgemaakt van vooraf gebouwde integratie die door Adobe of andere partners wordt onderhouden. Elke uitbreiding is doel-gebouwd voor een specifieke bestemming en behandelt authentificatie, lading het formatteren, en eindpuntmededeling. Implementer installeert de uitbreiding in de gebeurtenis door:sturen bezit, vormt authentificatiereferenties, en bouwt regels die XDM gegevenselementen aan de actievelden van de uitbreiding in kaart brengen.

Deze benadering minimaliseert douaneontwikkeling omdat de uitbreiding de vereisten van API van de bestemming abstracteert. De extensie [!DNL Meta] Conversies-API zet bijvoorbeeld XDM-commercegebeurtenissen om in de indeling die [!DNL Meta] verwacht, waarbij hashing van PII-velden, deduplicatieparameters en toegangstokenbeheer wordt afgehandeld. Op dezelfde manier verwerken de extensies [!DNL Google Cloud Platform] en [!DNL AWS] verificatie- en payload-opmaak voor hun respectievelijke cloudservices.

De verhouding is dat de uitbreidingsbeschikbaarheid bepaalt welke bestemmingen worden gesteund. Als er geen extensie voor een doeldoel bestaat, moet in plaats daarvan Option B (Aangepaste webhaak) worden gebruikt.

**Zeer belangrijke overwegingen:**

- De beschikbaarheid van de uitbreiding varieert — controleer de [&#x200B; catalogus van de uitbreidingen van de Inzameling van Gegevens &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/overview) alvorens te plannen
- De uitbreidingen worden gehandhaafd door Adobe of partners; de updates kunnen breekveranderingen introduceren die regelaanpassingen vereisen
- Sommige extensies ondersteunen alleen bepaalde gebeurtenistypen of vereisen specifieke XDM-veldtoewijzingen
- Extensies verwerken verificatie en credentiebeheer binnen hun configuratie-interface

**Voordelen:**

- Snellste tijd tot implementatie voor ondersteunde doelen
- Vooraf samengestelde payload-opmaak reduceert toewijzingsfouten
- Verificatie- en credentiebeheer afgehandeld door de extensie
- Bijgehouden en bijgewerkt door Adobe of gecertificeerde partners
- Lagere aangepaste code en lagere onderhoudslast

**Beperkingen:**

- Beperkt tot doelen met beschikbare extensies
- Minder flexibiliteit in aanpassing van de payload in vergelijking met aangepaste webhaken
- Voor updates van extensies moet u de regel opnieuw configureren
- Sommige extensies ondersteunen mogelijk niet alle doel-API-functies

**Experience League:**

- [Catalogus voor het doorsturen van extensies](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/overview)
- [Meta Conversions API-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/snowflake/overview)

### Optie B: Aangepaste webhaakgebeurtenis (Fetch API) doorsturen

**Best voor:** Teams die gebeurtenissen aan bestemmingen zonder een pre-gebouwde uitbreiding moeten door:sturen, of die volledige controle over de het verzoeklading, kopballen van HTTP, en authentificatiemechanisme vereisen.

**hoe het werkt:**

Aangepaste, op webhaak gebaseerde gebeurtenis die door:sturen gebruikt de [!DNL Adobe Cloud Connector] -extensie (standaard inbegrepen) om willekeurige HTTP-aanvragen naar een willekeurig eindpunt te maken. De uitvoerder bepaalt gegevenselementen om waarden uit de inkomende gebeurtenis te halen en om te zetten XDM, dan vormt een regelactie gebruikend het de actietype van de Vraag van de Vraag van de Verbinding van de Wolk &quot;van de Vetch van het Merk&quot;maken. Deze actie staat volledige controle over de methode van HTTP, URL, kopballen, en verzoeklichaam toe.

De aanvraaginstantie wordt doorgaans samengesteld met behulp van gegevenselementen en aangepaste code om de lading op te maken volgens de API-specificatie van de bestemming. Deze benadering steunt om het even welk HTTP-toegankelijk eindpunt — REST APIs, webhooks, wolkenfuncties, of interne diensten — die het de meest flexibele optie maken.

De afweging bestaat uit een grotere inspanning bij de uitvoering en een voortdurend onderhoud. De implementator moet de doel-API begrijpen, de verificatie handmatig afhandelen (bijvoorbeeld door machtigingsheaders in te stellen, token te vernieuwen) en de indeling voor de nuttige lading handhaven als de doel-API zich ontwikkelt.

**Zeer belangrijke overwegingen:**

- Vereist inzicht in de bestemmingsAPI specificatie (de methode van HTTP, de structuur URL, het formaat van de lading, authentificatie)
- Verificatiegegevens moeten handmatig worden beheerd in gegevenselementen of geheimen
- Er kan een aangepaste code nodig zijn voor het transformeren van de lading (hashing, encoding, conversion)
- Geen automatische updates wanneer de doel-API verandert — handmatig onderhoud vereist
- De functie Secreten in Gegevensverzameling kan API-sleutels en tokens veilig opslaan

**Voordelen:**

- Steunt om het even welk HTTP-toegankelijk eindpunt — geen uitbreidingsgebiedsafhankelijkheid
- Volledige controle over verzoeklading, kopballen, en authentificatie
- Kan doorsturen naar interne services, aangepaste API&#39;s of nicheplatforms
- Hiermee worden complexe ladingtransformaties met aangepaste code ingeschakeld
- Kan logica voor opnieuw proberen en foutafhandeling implementeren binnen aangepaste code

**Beperkingen:**

- Hogere initiële implementatieinspanningen
- Doorlopende onderhoudsverantwoordelijkheid voor de indeling en verificatie van de lading
- Geen vooraf gebouwde foutafhandeling of referentie-rotatie — moet handmatig worden geïmplementeerd
- Vereist expertise van ontwikkelaars op het gebied van HTTP-protocollen en bestemmings-API

**Experience League:**

- [extensie Adobe Cloud Connector](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Gebeurtenis die geheimen doorstuurt](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/secrets)

### Optie C: Hybride (extensies + aangepaste webhaken)

**Best voor:** Organisaties die gebeurtenissen aan veelvoudige bestemmingen door:sturen waar sommige pre-gebouwde uitbreidingen en anderen douaneintegratie vereisen.

**hoe het werkt:**

De hybride benadering combineert op uitbreiding-gebaseerde het door:sturen voor goed-gesteunde bestemmingen met de acties van de douanehaak voor bestemmingen die uitbreidingen missen. Één enkele gebeurtenis die bezit door:sturen bevat veelvoudige regels — sommigen die uitbreidingsacties gebruiken (bijvoorbeeld, [!DNL Meta] uitbreiding van API van Conversies voor het registreren van reclame) en anderen die de acties van de de haalslag van de Schakelaar gebruiken van de Wolk (bijvoorbeeld, door:sturen aan een intern eindpunt van het gegevenspeer).

Deze benadering maximaliseert dekking terwijl het minimaliseren van onnodige douaneontwikkeling. Elke regel werkt onafhankelijk, zodat op uitbreiding gebaseerde regels van vooraf gebouwde lading het formatteren profiteren terwijl de douaneregels volledige flexibiliteit handhaven.

**Zeer belangrijke overwegingen:**

- De ingewikkeldheid van het bezit stijgt met het aantal regels en bestemmingen
- Het testen en het zuiveren kunnen verschillende benaderingen voor op uitbreiding-gebaseerde versus douaneregels vereisen
- Wijzigingen in publicatie zijn van invloed op alle regels in de eigenschap — gebruik bibliotheken en omgevingen om wijzigingen in het werkgebied veilig te maken
- U kunt regels ordenen met duidelijke naamconventies om op extensies gebaseerde acties te onderscheiden van aangepaste acties

**Voordelen:**

- Beste dekking over diverse bestemmingstypen
- Gebruikt vooraf gebouwde uitbreidingen waar beschikbaar, die inspanning verminderen
- Handhaaft flexibiliteit voor douanebestemmingen
- Enige gebeurtenis die bezit door:sturen beheert al het door:sturen logica

**Beperkingen:**

- Hogere eigenschapcomplexiteit met meerdere regeltypen
- Gemengd onderhoudsmodel — sommige regels worden automatisch bijgewerkt via extensies, andere vereisen handmatig onderhoud
- Foutopsporing vereist vertrouwdheid met zowel extensieconfiguraties als aangepaste aanroeppatronen

**Experience League:**

- [Overzicht van het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/overview)
- [Aan de slag met het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/getting-started)

### Optievergelijking

In de volgende tabel worden de drie implementatieopties vergeleken.

| Criteria | Optie A: op extensie gebaseerd | Optie B: Aangepaste webhaak | Optie C: Hybride |
| --- | --- | --- | --- |
| Best voor | Ondersteunde doelen ([!DNL Meta], [!DNL Google], [!DNL AWS], enz.) | Aangepaste eindpunten, nicheplatforms, interne services | Meerdere doelen met gemengde ondersteuning |
| Complexiteit | Laag | Medium-High | Gemiddeld |
| Uitvoeringstijd | Dagen | Dagen-weken | Varieert op bestemmingsmix |
| Flexibiliteit | Beperkt tot uitbreidingsmogelijkheden | Volledig besturingselement | Volledige controle indien nodig |
| Onderhoud | Laag (met extensie beheerd) | Hoog (handmatig onderhoud) | Gemengd |
| Vereisten | Extensie beschikbaar voor doel | API-doeldocumentatie | Beide, afhankelijk van bestemming |
| Aangepaste code vereist | Minimaal | Matig-significant | Varieert |

### Kies de juiste optie

Begin door uw doelbestemmingen te inventariseren en te controleren of de pre-gebouwde gebeurtenis die uitbreidingen door:sturen voor elk bestaat.

1. **als alle bestemmingen uitbreidingen** hebben — kies Optie A. Dit geeft u de snelste implementatie met de laagste onderhoudslast. Extensies verwerken verificatie, payload-opmaak en API-versiebeheer.

2. **als geen bestemmingen uitbreidingen hebben, of u volledige ladingscontrole** nodig hebt — kies Optie B. Gebruik de uitbreiding van de Verbinding van de Wolk om de verzoeken van douaneHTTP aan om het even welk eindpunt te maken. Dit is ook de juiste keuze wanneer u complexe transformaties, aangepaste hashing of verzending naar interne services moet toepassen.

3. **als u een mengeling van gesteunde en niet gesteunde bestemmingen** hebt — kies Optie C. Gebruik extensies voor platformen zoals [!DNL Meta] , [!DNL Google] en [!DNL AWS] en aangepaste websites voor alle andere platformen. Dit is het meest gangbare productiescenario voor organisaties met uiteenlopende analyses en reclamestapels.

## Uitvoeringsfasen

De volgende fasen beschrijven het implementatieproces van begin tot eind voor gebeurtenis het door:sturen.

### Fase 1: Configuratie DataStream

**de functie van de Toepassing:** AEP: Configuratie DataStream

**wat u zult vormen:** Een datastream die gebeurtenissen van uw SDK van het Web, Mobiele SDK, of de implementatie van Server API ontvangt en hen leidt aan Edge Network waar de gebeurtenis die regels door:sturen hen kan verwerken. Als gebeurtenis het door:sturen aan een bestaande plaatsing van de gegevensinzameling wordt toegevoegd, zult u gebeurtenis toelaten die op de bestaande gegevensstroom door:sturen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Nieuwe gegevensstroom vs. bestaande datastream**
>
>Moet u een nieuwe gegevensstroom voor gebeurtenis creëren door:sturen of gebeurtenis toelaten door:sturen op een bestaande gegevensstroom?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Bestaande gegevensstroom gebruiken | U hebt Web SDK of Server API al die gebeurtenissen door een datastream verzenden | Het gemeenschappelijkste scenario; gebeurtenis door:sturen wordt eenvoudig toegelaten als extra dienst op de datastream. Er zijn geen wijzigingen aan de clientzijde nodig. |
>| Nieuwe gegevensstroom maken | Dit is een greenfield-implementatie zonder bestaande gegevensverzameling, of u hebt een aparte gegevensstroom nodig voor specifieke gebeurtenistypen | Vereist de client-side SDK-configuratie om naar de nieuwe gegevensstroom-id te wijzen. Staat geïsoleerde configuratie toe. |

>[!NOTE]
>
>**Besluit: Welke diensten van AEP om naast gebeurtenis toe te laten door:sturen**
>
>De datastream kan gebeurtenissen gelijktijdig naar meerdere AEP-services verzenden. Het doorsturen van gebeurtenissen is één service; andere services (AEP data ingestion, [!DNL Target], [!DNL Analytics] ) kunnen parallel worden uitgevoerd.
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alleen gebeurtenis doorsturen | U hoeft alleen gebeurtenissen door te sturen naar niet-Adobe-doelen en hebt geen gegevens nodig in AEP-gegevenssets | Minimaliseert de kosten voor gegevensverwerking. De gebeurtenissen stromen door Edge Network aan het door:sturen van regels maar worden niet opgenomen in het de gegevensmeer van AEP. |
>| Gebeurtenis doorsturen + AEP-opname | U hebt dezelfde gebeurtenissen nodig, zowel in AEP (voor profielen, publiek, reizen) als op externe systemen | Dit komt vooral voor organisaties die [!DNL RT-CDP] of [!DNL AJO] naast analyses van derden gebruiken. De gegevensstroom verzendt gebeurtenissen naar zowel de datasets van AEP als gebeurtenis die regels door:sturen. |
>| Gebeurtenis doorsturen + meerdere Adobe-services | U hebt gebeurtenissen nodig die tegelijkertijd naar AEP, [!DNL Target], [!DNL Analytics] en externe doelen worden gerouteerd | Schakel alle vereiste services in de gegevensstroom in. Elke service ontvangt de gebeurtenis onafhankelijk. |

**navigatie UI:** [!DNL Experience Platform] > de Inzameling van Gegevens > De stromen van Gegevens > selecteren of creeer gegevensstroom

**Zeer belangrijke configuratiedetails:**

- De gegevensstroom moet gebeurtenis hebben door:sturen toegelaten onder zijn Geavanceerde Montages of de dienstconfiguratie
- Koppel de gebeurtenis door:sturen bezit (die in Fase 2 wordt gecreeerd) aan de datastream
- Bevestig het XDM-schema dat aan de datastream is toegewezen, overeenkomt met de gebeurtenisstructuur die uw verzamelingsmechanisme verzendt

**documentatie van Experience League:**

- [Gegevensstromen configureren](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/configure)
- [Overzicht gegevensstromen](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/overview)
- [Overzicht van het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/overview)

### Fase 2: Gebeurtenis die bezit en uitbreidingen door:sturen

**de functie van de Toepassing:** AEP: De gebeurtenis die de Opstelling van het Bezit door:sturen

**wat u zult vormen:** een gebeurtenis die bezit in de Inzameling UI van Gegevens door:sturen, samen met de uitbreidingen nodig voor uw doelbestemmingen. De gebeurtenis die bezit door:sturen is de container voor alle regels, gegevenselementen, en uitbreidingen die uw server-kant het door:sturen logica bepalen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: Enig bezit vs. veelvoudige eigenschappen**
>
>Moet u één gebeurtenis gebruiken die bezit voor alle bestemmingen of afzonderlijke eigenschappen door:sturen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Enkele eigenschap | De meeste implementaties; alle het door:sturen regels delen de zelfde gebeurtenisstroom | Eenvoudiger te beheren, één publicatieworkflow, evalueren alle regels voor elke gebeurtenis. De regelvoorwaarden van het gebruik om te filtreren welke gebeurtenissen gaan naar welke bestemmingen. |
>| Meerdere eigenschappen | U hebt verschillende teams nodig om verschillende doelintegratie onafhankelijk te beheren, of u hebt strikte vereisten voor de isolatie van omgevingen | Elke eigenschap heeft een eigen publicatieworkflow en kan worden gekoppeld aan verschillende gegevensstreams. Verhoogt beheersoverheadkosten maar verbetert toegangsbeheergrenzen. |

>[!NOTE]
>
>**Besluit: Welke uitbreidingen om** te installeren
>
>Selecteer extensies op basis van uw doeldoelen en de gekozen implementatieoptie (A, B of C van boven).
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Doelspecifieke extensies ([!DNL Meta] , [!DNL Google] , [!DNL AWS] , enzovoort) | De bestemming heeft een vooraf gebouwde uitbreiding en u wilt minimale douaneconfiguratie (Optie A of C) | Elke extensie vereist bestemmingsspecifieke gegevens (API-tokens, maats en account-id&#39;s). Raadpleeg de documentatie bij extensies voor ondersteunde gebeurtenistypen en vereiste velden. |
>| Alleen extensie Wolk Connector | Alle doelen gebruiken aangepaste HTTP-aanvragen (Option B) | De extensie Cloud Connector wordt standaard geïnstalleerd. Gebruik de functie Secrets om API-sleutels en verificatietokens veilig op te slaan. |
>| Zowel bestemmingsspecifieke als Cloud Connector | U hebt een mengeling van gesteunde en douanebestemmingen (Optie C) | Installeer specifieke extensies voor goed ondersteunde doelen en gebruik de Cloud Connector voor de rest. |

**navigatie UI:** [!DNL Experience Platform] > de Inzameling van Gegevens > Gebeurtenis door:sturen > creeer Bezit (of selecteer bestaand)

**Zeer belangrijke configuratiedetails:**

- Geef de eigenschap een duidelijke naam (bijvoorbeeld &quot;Event Forwarding - Production&quot; of &quot;EF - Analytics &amp; Advertising&quot;).
- Installeer de extensie [!DNL Adobe Cloud Connector] (die standaard wordt meegeleverd bij aangepaste webhaakhandelingen)
- Installeer bestemmingsspecifieke uitbreidingen en vorm hun geloofsbrieven
- Gebruik de functie Secrets (Gegevensverzameling > Gebeurtenis doorsturen > Geheimen) om API-sleutels, tokens en gegevens veilig op te slaan
- Configureren van omgevingen (ontwikkeling, staging, productie) voor workflows voor veilig publiceren

**documentatie van Experience League:**

- [Aan de slag met het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/getting-started)
- [Catalogus voor het doorsturen van extensies](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/overview)
- [Gebeurtenis die geheimen doorstuurt](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/secrets)
- [extensie Adobe Cloud Connector](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Fase 3: Definitie van gebeurtenisregel

**de Functie van de Toepassing:** AEP: De Definitie van de Regel van de gebeurtenis, AEP: De Toewijzing van de bestemming

**wat u zult vormen:** Regels die inkomende gebeurtenisgegevens evalueren, voorwaarden op filter toepassen welke gebeurtenissen door:sturen, en acties bepalen die de gegevens naar bestemmings eindpunten verzenden. Elke regel bestaat uit voorwaarden (wanneer moet worden afgegaan) en handelingen (wat moet worden gedaan). De elementen van gegevens halen en transformeren waarden van de XDM gebeurtenislading voor gebruik in regelvoorwaarden en actieconfiguraties.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: De het filtreren van de gebeurtenis strategie**
>
>Hoe zou u moeten bepalen welke gebeurtenissen aan elke bestemming door:sturen?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alle gebeurtenissen doorsturen | De bestemming heeft een volledige gebeurtenisstroom nodig (bijvoorbeeld, gegevenspakje voor ruwe gebeurtenisopslag) | Eenvoudigste configuratie — geen voorwaarden nodig. Hoog gegevensvolume bij de bestemming. Houd rekening met de kosten en tarieflimieten van de bestemming. |
>| Filteren op type gebeurtenis | Verschillende bestemmingen hebben verschillende gebeurtenistypen nodig (bijvoorbeeld aankopen naar advertenties, paginaweergaven naar analysemogelijkheden) | Gebruik voorwaarden die zijn gebaseerd op `arc.event.xdm.eventType` of vergelijkbare XDM-velden. Vermindert onnodige gegevens bij de bestemming. |
>| Filteren op gebeurteniskenmerken | Alleen specifieke gebeurtenissen die aan bepaalde criteria voldoen, moeten worden doorgestuurd (bijvoorbeeld aankopen boven een drempel of gebeurtenissen van specifieke paginaden) | Waarden voor gegevenselementen gebruiken in regelvoorwaarden. Complexer, maar vermindert ruis op de bestemming. |

>[!NOTE]
>
>**Besluit: De benadering van de transformatie van gegevens**
>
>Hoe moeten XDM gebeurtenisgegevens voor de bestemmingslading worden omgezet?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Directe XDM-veldtoewijzing via gegevenselementen | De bestemmingsgebieden in kaart brengen schoon aan gebieden XDM (gemeenschappelijk met op uitbreiding-gebaseerd door:sturen) | Maak gegevenselementen die verwijzen naar XDM-paden (bijvoorbeeld `arc.event.xdm.commerce.order.priceTotal` ). Extensies verschaffen vaak een toewijzingsinterface. |
>| Aangepaste codetransformatie | De bestemming vereist een nuttige ladingsformaat beduidend verschillend van XDM, of de gebieden vereisen het hakken, de aaneenschakeling, of de herstructurering | Gebruik aangepaste code-gegevenselementen of aangepaste code op actieniveau om de payload te transformeren. Flexibeler, maar moeilijker te onderhouden. |
>| Combinatie van gegevenselementen en aangepaste code | Sommige velden worden rechtstreeks toegewezen, terwijl andere moeten worden getransformeerd | Gebruik gegevenselementen voor eenvoudige toewijzingen en aangepaste codeblokken voor complexe transformaties. Evenwicht tussen onderhoudsgemak en flexibiliteit. |

>[!NOTE]
>
>**Besluit: PII behandeling in door:sturen gegevens**
>
>Hoe zou persoonlijk identificeerbare informatie alvorens door:sturen moeten worden behandeld?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| PII-velden volledig uitsluiten | De bestemming heeft geen PII nodig en het bestuursbeleid beperkt het delen | Vorm regels om PII- gebieden van de door:sturen lading weg te laten. Eenvoudigste aanpak voor privacynaleving. |
>| Hash PII-velden voordat deze worden doorgestuurd | Het doel vereist gehashte id&#39;s ([!DNL Meta] vereist bijvoorbeeld SHA-256 gehashte e-mail voor conversie-API) | Gebruik aangepaste code-gegevenselementen om SHA-256-hashing toe te passen. Bij sommige extensies wordt hashing automatisch verwerkt. |
>| Doorlopende PII met contractuele basis | De bestemming heeft een gegevensverwerkingsovereenkomst en de rechtsgrondslag bestaat voor het delen van PII | Zorg ervoor dat labels voor gegevensgebruik en beleidsregels voor beheer (S3) het delen toestaan. Documenteer de rechtsgrondslag. |

**navigatie UI:** [!DNL Experience Platform] > de Inzameling van Gegevens > Gebeurtenis door:sturen > Uitgezochte Bezit > Elementen van Gegevens/Regels

**Zeer belangrijke configuratiedetails:**

- **de elementen van Gegevens** verwijzen de inkomende gebeurtenis XDM gebruikend de wegprefix `arc.event.xdm.` (bijvoorbeeld, `arc.event.xdm.web.webPageDetails.URL` voor de pagina URL)
- **de voorwaarden van de Regel** evalueren de waarden van het gegevenselement om te bepalen als de regel zou moeten in brand steken
- **de acties van de Regel** gebruiks uitbreiding-specifieke acties (voor Optie A) of de Schakelaar van de Wolk &quot;maakt de Acties van de Vraag van de Vetch&quot;(voor Optie B) om gegevens naar bestemmingen te verzenden
- Elke regel kan veelvoudige acties hebben, toestaand één enkele gebeurtenis om aan veelvoudige bestemmingen door:sturen
- Regelvolgorde gebruiken om de volgorde van de evaluatie te bepalen wanneer meerdere regels voor dezelfde gebeurtenis kunnen worden geactiveerd
- De regels van de test grondig in het milieu van de Ontwikkeling alvorens aan Productie te publiceren

**waar de opties uiteenlopen:**

**voor Optie A (op uitbreiding-Gebaseerd):**

Vorm regelacties gebruikend de pre-gebouwde actietypen van de bestemmingsuitbreiding. De API-extensie [!DNL Meta] Conversies biedt bijvoorbeeld de handeling Gebeurtenis verzenden, waarbij u XDM-velden toewijst aan [!DNL Meta] -gebeurtenisparameters (event_name, event_time, user_data, custom_data). De extensie handelt de indeling, hashing en API-communicatie van de payload af.

**voor Optie B (Aangepaste Webhaak):**

Configureer regelhandelingen met de actie &quot;Vraag ophalen&quot; van de extensie Cloud Connector. Geef de doel-URL, de HTTP-methode (doorgaans POST), aanvraagheaders (inclusief autorisatie) op en stel de aanvraaginstantie samen met gegevenselementen en/of aangepaste code. U bent verantwoordelijk voor het exact afstemmen van de verwachte ladingsindeling van de doel-API.

**voor Optie C (Hybride):**

Maak afzonderlijke regels voor elk doel. De op uitbreiding-gebaseerde regels gebruiken de actietypen van de uitbreiding; de douaneregels gebruiken de haalvraag van de Verbinding van de Wolk. Alle regels bestaan samen in dezelfde eigenschap en evalueren onafhankelijk van elke binnenkomende gebeurtenis.

**documentatie van Experience League:**

- [Regels voor het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/overview)
- [Gegevenselementen bij het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/ui/data-elements)
- [Regels voor gegevensverzameling](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/ui/rules)
- [extensie Adobe Cloud Connector](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/cloud-connector/overview)

### Fase 4: Publiceren en activeren

**Functie van de Toepassing:** AEP: Door:sturen Uitvoering

**wat u zult vormen:** het publiceren werkschema dat uw gebeurtenis bevordert door:sturen regels van Ontwikkeling door het Opvoeren aan Productie. Het door:sturen van gebeurtenissen gebruikt het zelfde op bibliotheek-gebaseerde het publiceren model zoals Markeringen, met milieu&#39;s en bouwt artefacten die controleren welke configuratie bij Edge Network actief is.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: het publiceren werkschemarrigor**
>
>Hoe rigoureus moet het publicatieproces zijn?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Direct naar productie (Ontwikkeling > Productie) | Kleine teams, bestemmingen met een laag risico, of gebruiksklare implementaties | Snellere implementatie, maar hogere risico&#39;s op productieproblemen. Geschikt voor initiële tests met niet-kritieke bestemmingen. |
>| Voortgang van de volledige omgeving (Development > Staging > Production) | Productie-implementaties met kritieke bestemmingen (reclameplatforms, datapakhuizen) | Aanbevolen voor alle gevallen waarin het product wordt gebruikt. Het opvoeren staat bevestiging met echt verkeer vóór productieplaatsing toe. |

**navigatie UI:** [!DNL Experience Platform] > de Inzameling van Gegevens > Gebeurtenis door:sturen > Uitgezochte Bezit > het Publiceren Stroom

**Zeer belangrijke configuratiedetails:**

- Een bibliotheek maken met alle regels, gegevenselementen en extensieconfiguraties die u wilt publiceren
- Bouw en test in het milieu van de Ontwikkeling eerst gebruikend het Door:sturen van de Gebeurtenis hulpmiddel om gebeurtenissen te verifiëren correct door:sturen
- Bevorderen tot Staging voor preproductievalidering met live-verkeer
- Publiceren naar productie alleen na bevestiging van geslaagde gebeurtenislevering in Staging
- Bibliotheekversie gebruiken om wijzigingen bij te houden en terugdraaien in te schakelen, indien nodig

**documentatie van Experience League:**

- [Overzicht van publicatie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/publish/overview)
- [Bibliotheken](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/publish/libraries)
- [Omgevingen](https://experienceleague.adobe.com/en/docs/experience-platform/tags/publish/environments)
- [Builds](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/publish/builds)

### Fase 5: Controle en validatie

**Functie van de Toepassing:** AEP: Controle

**wat u zult vormen:** de Controle dashboards en bevestigingsprocessen om gebeurtenissen te bevestigen met succes door:sturen, diagnostiseren mislukkingen, en handhaven operationele gezondheid van de gebeurtenis die plaatsing door:sturen.

**de punten van het Besluit in deze fase:**

>[!NOTE]
>
>**Besluit: De controle diepte**
>
>Hoe diep zou gebeurtenis het door:sturen moeten worden gecontroleerd?
>
>| Optie | Wanneer kiest u | Overwegingen |
>| --- | --- | --- |
>| Alleen het dashboard voor bewaking van gebeurtenissen doorsturen | Basis controle voor niet kritieke bestemmingen of aanvankelijke plaatsingen | Verstrekt overzicht van het door:sturen van succes/mislukkingen tarieven en de codes van de bestemmingsreactie. Volstaan voor de meeste implementaties. |
>| Gebeurtenis die Controle door:sturen + bestemmings-zijbevestiging | Kritieke bestemmingen waar de volledigheid van de gegevens direct bedrijfsresultaten beïnvloedt (reclame het volgen van omzettingen, de integriteit van het gegevenspakhuis) | Kruisverwijzing Adobe-side het door:sturen metriek met bestemming-zijontvangstbevestiging. Vangt randgevallen waar de bestemming het verzoek goedkeurt maar er niet in slaagt om de gegevens te verwerken. |
>| Volledige waarneembaarheidsstapel (Event Forwarding Monitoring + bestemmingsbevestiging + AEP Alerts) | Implementaties op bedrijfsniveau met SLA-vereisten voor gegevenslevering | Combineer gebeurtenis die controle met het platformalarm van AEP voor een uitvoerige mening door:sturen. Vorm waakzame berichten voor het door:sturen van mislukkingsdrempels. |

**navigatie UI:** [!DNL Experience Platform] > de Inzameling van Gegevens > Gebeurtenis door:sturen > Uitgezochte Bezit > Controle

**Zeer belangrijke configuratiedetails:**

- Het hulpmiddel van de Controle van de Gebeurtenis door:sturen toont gebeurtenisvolume, succespercentages, en foutendetails per regel en per bestemming
- De responscodes van HTTP van de monitor van bestemmingen - 2xx wijst op succes, 4xx wijst op cliëntfouten (waarschijnlijk lading of authentificatiekwesties), 5xx wijst op bestemmings-zijmislukkingen aan
- Met de browserextensie [!DNL Adobe Experience Platform Debugger] kunt u gebeurtenissen inspecteren die vanuit de client via de Edge Network naar regels voor het doorsturen van gebeurtenissen gaan
- Valideer end-to-end door te controleren dat door:sturen gebeurtenissen in het bestemmingssysteem verschijnen (bijvoorbeeld, controleer [!DNL Google Analytics] rapporten in real time, [!DNL Meta] de Manager van Gebeurtenissen, of de lijsten van het gegevenspakhuis)
- Stel AEP Alerts in voor bron- en dataflow-fouten om stroomopwaartse problemen af te vangen die zouden verhinderen dat gebeurtenissen regels voor het doorsturen van gebeurtenissen bereiken

**documentatie van Experience League:**

- [Toezicht op doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/monitoring)
- [Adobe Experience Platform Debugger](https://experienceleague.adobe.com/nl/docs/experience-platform/debugger/home)
- [Overzicht van waarschuwingen](https://experienceleague.adobe.com/nl/docs/experience-platform/observability/alerts/overview)

## Implementatieoverwegingen

Deze sectie heeft betrekking op begeleiding, gemeenschappelijke valkuilen, beste praktijken, en handelsbesluiten om in mening te houden door de implementatie.

### Guardrails en limieten

- Gebeurtenis door:sturen verwerkt gebeurtenissen in echt - tijd bij Edge Network - er is geen partijwijze of herprobeer rij voor ontbroken leveringen door gebrek
- De tariefgrenzen van Edge Network zijn op het totale gebeurtenisvolume van toepassing dat per datastream wordt verwerkt — [&#x200B; de guardrails van Edge Network &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/edge-network/guardrails)
- Gebeurtenis die regels door:sturen voert server-kant uit en heeft geen toegang tot cliënt-zijmiddelen (DOM, koekjes, localStorage)
- Aangepaste code in regels voor het doorsturen van gebeurtenissen wordt uitgevoerd in een sandbox-omgeving. Niet alle JavaScript API&#39;s van de browser zijn beschikbaar
- De de ophaalvraag van de Verbinding van de Wolk heeft onderbrekingsgrenzen — de bestemmingen die langzaam antwoorden kunnen onderbrekingen veroorzaken
- Het doorsturen van gebeurtenissen is afhankelijk van Edge Network geografische routering — gebeurtenissen worden verwerkt op de dichtstbijzijnde Edge-locatie
- Maximale ladingsgrootte voor doorgestuurde aanvragen wordt bepaald door Edge Network-limieten

### Veelvoorkomende valkuilen

- **Door:sturen alle gebieden XDM zonder het filtreren:** Verzendend de volledige XDM gebeurtenislading aan een bestemming die slechts een paar gebieden nodig heeft verspilt bandbreedte, verhoogt bestemmingskosten, en kan onbedoeld PII delen. Wijs altijd slechts de vereiste gebieden in uw het door:sturen regels in kaart.

- **het beveiligen van geloofsbrieven niet met Geheimen:** De sleutels of tokens van de Hardcoding API in gegevenselementen of regelacties leiden tot een veiligheidsrisico. Gebruik altijd de eigenschap van de Secreten van de Gegevensverzameling om geloofsbrieven veilig op te slaan en hen in regels van verwijzingen te voorzien.

- **Negerend de grenzen van het bestemmingstarief:** De bestemmingen van de derde hebben vaak API tariefgrenzen. Als uw gebeurtenisvolume de capaciteit van een bestemming overschrijdt, kunnen de gebeurtenissen worden gelaten vallen of kan uw API toegang worden vertraagd. De bestemmingsdocumentatie van het overzicht voor tariefgrenzen en voert het filtreren uit om gebeurtenisvolume te verminderen indien nodig.

- **het Publiceren direct aan Productie zonder het opvoeren:** het Overslaan van het het Opvoeren milieu betekent de fouten slechts in Productie worden ontdekt, potentieel veroorzakend gegevensverlies bij kritieke bestemmingen. Bevestig altijd in Staging met levend verkeer eerst.

- **controleert niet de antwoordcodes van HTTP:** Een regel die zonder fouten brandt garandeert niet de bestemming met succes verwerkte de gegevens. De codes van de bestemmingsreactie van de monitor (beschikbaar in het hulpmiddel van de Controle van de Door:sturen van de Gebeurtenis) en onderzoeken om het even welke reacties niet-2xx.

- **Misconfigured XDM wegverwijzingen:** de elementen van Gegevens gebruiken de `arc.event.xdm.` prefix om inkomende gebeurtenisgebieden van verwijzingen te voorzien. Een onjuist pad (waarbij bijvoorbeeld een nestniveau ontbreekt) resulteert in stilte in null-waarden en niet in het genereren van fouten. Waarden voor gegevenselementen valideren met Foutopsporing.

### Aanbevolen procedures

- **Begin met één enkele bestemming en breid geleidelijk** uit - bevestig gebeurtenis die van begin tot eind met één bestemming door:sturen alvorens extra regels en bestemmingen toe te voegen. Dit vereenvoudigt het zuiveren en bouwt vertrouwen in de infrastructuur.

- **Gebruik verenigbare noemende overeenkomsten** - de gegevenselementen, de regels, en de bibliotheken van de naam met een duidelijke overeenkomst die de bestemming, het gebeurtenistype, en het milieu (bijvoorbeeld, &quot;Regel: Meta - Inkoopgebeurtenissen&quot;identificeert, &quot;DE: Het Totaal van de Orde&quot;).

- **voer gebied-vlakke het filtreren voor privacy** uit — zelfs als de bestemmingseisen PII geschikt te behandelen, server-zij het filtreren op strook of knoeiboel gevoelige gebieden toepassen alvorens zij Edge Network verlaten. Dit is het primaire governancevoordeel van gebeurtenis die over cliënt-zijmarkeringen door:sturen.

- **Versie uw configuraties** - gebruik het bibliotheek het publiceren werkschema om versioned momentopnamen van uw gebeurtenis te handhaven door:sturen configuratie. Documenteer wat elke bibliotheekversie bevat voor audit- en terugdraaidoeleinden.

- **Test met Debugger van het Platform** — De [!DNL Adobe Experience Platform Debugger] uitbreiding verstrekt zicht in de gebeurtenislevenscyclus van cliënt-kant SDK door de verwerking van Edge Network. Gebruik het tijdens ontwikkeling en het oplossen van problemen.

- **richt gebeurtenis door:sturen regels met uw XDM schemaontwerp** - als gebeurtenis het door:sturen een bekend vereiste is, ontwerp uw schema XDM en gebeurtenistaxonomie om de gebiedsbestemmingen te omvatten zal nodig hebben. Het opnieuw aanbrengen van schemawijzigingen na implementatie is storender.

### Handelsbesluiten

>[!NOTE]
>
>**handel-off: De eenvoud van de uitbreiding vs. Web-haakflexibiliteit**
>
>Vooraf gebouwde extensies minimaliseren de implementatie-inspanningen en het onderhoud, maar beperken u tot de ondersteunde functies en ladingsindelingen van de extensie. Aangepaste websites bieden volledige controle, maar vereisen meer ontwikkeling en doorlopend onderhoud.
>
>- **op uitbreiding-Gebaseerde (Optie A) begunstigt:** Snelheid aan markt, verminderde ontwikkelaarafhankelijkheid, automatisch credentiebeheer, lager onderhoud
>- **WebHaak-Gebaseerde (Optie B) bevordert:** Volledige controle van de nuttige lading, steun voor om het even welk eindpunt van HTTP, de logica van de douanetransformatie, onafhankelijkheid van de cycli van de uitbreidingsversie
>- **Aanbeveling:** Gebruik uitbreidingen wanneer beschikbaar en voldoende. Ga alleen terug naar aangepaste websites als de bestemming geen extensie heeft of als de extensie geen ondersteuning biedt voor de specifieke API-functies die u nodig hebt. De hybride benadering (optie C) is de pragmatische keuze voor de meeste organisaties.

>[!NOTE]
>
>**handel-off: Door:sturen alle gebeurtenissen vs. selectief filtreren**
>
>Door alle gebeurtenissen naar een bestemming door te sturen zorgt u voor volledigheid, maar verhoogt u het gegevensvolume, de bestemmingskosten en de privacyblootstelling. Met selectief filteren vermindert u ruis, maar het risico bestaat dat er gebeurtenissen ontbreken die waardevol kunnen zijn.
>
>- **door:sturen alle gebeurtenissen begunstigt:** de volledigheid van Gegevens, eenvoud, toekomstig-proef (het gegeven is daar indien nodig later)
>- **Selectieve het filtreren voorkeur:** Kostenefficiëntie, verminderd privacyrisico, schonere bestemmingsgegevens, naleving van de beginselen van de gegevensminimalisering
>- **Aanbeveling:** Gebrek aan selectief filtreren die op gebeurtenistype en bedrijfsrelevantie wordt gebaseerd. Door:sturen slechts de gebeurtenissen en de gebieden elke bestemming eigenlijk behoeften. Dit is in overeenstemming met de beginselen van gegevensminimalisering (artikel 5 van de GDPR) en verlaagt de operationele kosten.

>[!NOTE]
>
>**handel-off: Enig bezit vs. veelvoudige eigenschappen**
>
>Één enkele gebeurtenis die bezit door:sturen is eenvoudiger te beheren maar betekent alle regels één het publiceren werkschema delen. De veelvoudige eigenschappen verstrekken isolatie maar verhogen beheersoverheadkosten.
>
>- **Enig bezit bevordert:** Eenvoud, verenigd het publiceren, gedeelde gegevenselementen, gemakkelijkere het zuiveren
>- **Veelvoudige eigenschappen begunstigen:** Team-vlakke toegangscontrole, onafhankelijke het publiceren kadingen, isolatie van bestemmingsmislukkingen
>- **Aanbeveling:** Begin met één enkel bezit voor de meeste implementaties. Alleen gesplitst in meerdere eigenschappen als verschillende teams verschillende doelintegraties bezitten en onafhankelijke releasecycli nodig hebben, of als de regelgevingsvereisten strikte isolatie tussen gegevensstromen vereisen.

## Gerelateerde documentatie

De volgende middelen verstrekken extra detail over de onderwerpen die in deze gids worden behandeld.

**Gebeurtenis door:sturen**

- [Overzicht van het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/overview)
- [Aan de slag met het doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/getting-started)
- [Toezicht op doorsturen van gebeurtenissen](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/monitoring)
- [Gebeurtenis die geheimen doorstuurt](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/event-forwarding/secrets)

**Gebeurtenis door:sturen uitbreidingen**

- [Serverside extensiecatalogus](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/overview)
- [extensie Adobe Cloud Connector](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/cloud-connector/overview)
- [Meta Conversions API-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/meta/overview)
- [Google Cloud Platform-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/google-cloud-platform/overview)
- [AWS-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/aws/overview)
- [Snowflake-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/snowflake/overview)
- [Google Ads Enhanced Conversions-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/google-ads-enhanced-conversions/overview)
- [Mailchimp-extensie](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/extensions/server/mailchimp/overview)

**de inzameling van Gegevens en Edge Network**

- [Gegevensstromen configureren](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/configure)
- [Overzicht gegevensstromen](https://experienceleague.adobe.com/nl/docs/experience-platform/datastreams/overview)
- [Overzicht van Web SDK](https://experienceleague.adobe.com/nl/docs/experience-platform/web-sdk/home)
- [Overzicht Edge Network Server API](https://experienceleague.adobe.com/nl/docs/experience-platform/edge-network-server-api/overview)
- [Overzicht van codes](https://experienceleague.adobe.com/nl/docs/experience-platform/tags/home)
