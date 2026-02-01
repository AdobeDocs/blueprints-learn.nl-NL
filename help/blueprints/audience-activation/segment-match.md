---
title: Publiek Collaboration met segmentovereenkomst
description: Leer over [!UICONTROL &#x200B; Overeenkomst van het Segment &#x200B;] voor Adobe Experience Platform (AEP). [!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] is de dienst van de gegevenssamenwerking die u toelaat om segmentgegevens uit te wisselen die op gemeenschappelijke industriedetails op een beveiligde, beheerde, en privacy-vriendelijke manier worden gebaseerd.
solution: Experience Platform
exl-id: d7e6d555-56aa-4818-8218-b87f6286a75e
source-git-commit: 88a15765c0a998d49c19d9853ad0c44d6e3bfaa1
workflow-type: tm+mt
source-wordcount: '2123'
ht-degree: 0%

---

# Auditie Collaboration met segmentafstemming blauwdruk

Segment Match stelt partnermerken in staat om soorten publiek te delen in hun respectieve Experience Platform-omgevingen. De sleutel voor merken is om met klanten te verbinden die op gegevens worden gebaseerd die uit hun directe relaties met consumenten worden verzameld. Met betere governance, toestemmingen, en voorkeurbeheersystemen, kunnen de marketers hun eerste-partij voor authentiek verklaarde publiek met zeer belangrijke partners verder verbeteren.

[!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] is de dienst van de gegevenssamenwerking om de klanten van Experience Platform (AEP) (die als _worden bedoeld partners_) toe te staan om segmentgegevens uit te wisselen die op gemeenschappelijke industriedetails op een beveiligde, beheerde, en privacy-vriendelijke manier worden gebaseerd.

De dienst laat klanten toe om passende IDs veilig te identificeren op een veilige, neutrale manier zonder het moeten hun volledig gegevensbestand openbaarmaken. De partners ontvangen slechts aangewezen attributen (segmentnaam) voor overlappende IDs, toelatend sneller en gemakkelijkere het delen op een controleerbare, toestemming-gestuurde manier.

[!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] gebruikt het gegevensbestuur van AEP en toestemmingskader als zijn backbone. Het is beschikbaar voor alle klanten van het platform van de Gegevens van de Klant van B2C en B2P in real time. De zeer belangrijke eigenschappen van [!UICONTROL [!UICONTROL &#x200B; Overeenkomst van het Segment &#x200B;]] omvatten:

* Segmentdeling voor overlappende klanten met toestemming
* Rapportage vóór het delen voor inzichten in het geschatte overeenkomstenvolume
* Volledig geïntegreerd DULE beleid en toestemmings handhaving
* Gegevensdeling, toestemmingskaderbackbone
* Gegevensfeeds voor het organiseren van segmenten en partners

## Applicaties

Merk naar uitgever:

De &#39;uitgeverij-zaak&#39; is het meest beïnvloed door de afleiding van cookies van derden en gegevens van mobiele advertentie-id. Dit gebruiksgeval heeft een grote invloed op de media- en amusementsindustrie, die zich richt op het verkopen van reclame als bedrijfsmodel. [!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] is een weg voor uitgevers met grote eerste partijpubliek die direct met hun adverteerders willen samenwerken. Adverteerders kunnen rechtstreeks met uitgevers samenwerken om advertenties te maken tegen overeenkomende doelgroepen op uitgeverseigenschappen voor gerichte of prospectieve campagnes.

### Merk naar merk

Consumentenreizen zijn nooit lineair. Een klant kan bijvoorbeeld trouw zijn aan een luchtvaartmaatschappij en aan hun creditcardmaatschappij. Door [!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] te gebruiken, kunnen de luchtvaartmaatschappij en het creditcardbedrijf een gegevenspartnerschap tot stand brengen om overlappende publiek te begrijpen en dan aanbiedingen te maken om ervaringen aan loyale consumenten van elk van de bedrijven te personaliseren.

### BU naar BU

Internationale multinationals hebben problemen met de samenwerking van gegevens tussen onafhankelijke bedrijfseenheden. Het combineren van gegevens in één sandbox is mogelijk niet mogelijk vanwege verschillende privacybeleid, overnames of het beheer van machtigingen voor BU&#39;s.

[!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] hulp verdeelt marketing teams over massieve organisaties efficiënter samenwerken, terwijl het blijven onafhankelijk werken

## Architectuur

![&#x200B; Architectuur van de Gelijke van het Segment &#x200B;](assets/architecture-segment-match.png){zoomable="yes"}

[!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] is geen gegevensmarkt waar de gegevens kunnen worden gekocht. In plaats daarvan is het een AEP-functie die werkt met gegevens van de eerste partij met bepaalde partners, die privacycontroles en toestemmingscontroles gebruiken om samen te werken. [!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] hulp concentreert zich inspanningen op het verbeteren van klantenverhoudingen en het kweken van het merk. Het is nuttig wanneer bestaande merken of partnerrelaties bestaan. [!UICONTROL &#x200B; ervaring van de Gelijke van het 1&rbrace; Segment is gemakkelijk te leiden, scalable, en staat voor beheerders toe om segmenten op een opt-in, controleerbare manier te delen.]

[!UICONTROL &#x200B; de Overeenkomst van het Segment &#x200B;] laat toe:

* Segmentlidmaatschapsgegevens die veilig door organisaties moeten worden geëxporteerd met standaard id&#39;s op mensniveau, zoals gehashte e-mail of telefoonnummer
* Een gebruikersinterface en workflows delen met meldingen
* Vooraf gedeelde overlap schattingen
* Zelfserverende partneropstelling
* Overlappingen op bepaalde gestandaardiseerde naamruimten (hashed email, hashed phone, ECID, IDFA, GAID)
* Goedkeuring van gegevensuitwisseling
* Levenscyclusbeheer voor gedeeld publiek
* DULE-handhaving in workflow voor delen
* Dagelijkse batchupdates

[!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] staat toe om onderling verbonden klantenervaring tot stand te brengen. De ondersteunde duurzame id&#39;s zijn gehashte e-mails, gehashte telefoonnummers en id&#39;s zoals ECID, IDFA en GAID. Klanten kunnen feeds maken die overeenkomen en publieksgegevens verplaatsen tussen merksandboxen, met een sterke governance, transparantie en intrekkingsmogelijkheden voor gebruik in reclame- en marketingactiviteiten

## Voorwaarden

De pre-vereisten voor [!UICONTROL &#x200B; Overeenkomst van het Segment &#x200B;] zijn:

* RT-CDP actief met licentie
* Ondersteunde standaard hashed-id&#39;s zijn SHA256-hashed-e-mail, hashed phone, ECID, Apple IDFA en GAID
* Privacykader en toestemmingsstrategie
* Overeenkomsten inzake gegevensuitwisseling tussen klanten

## Beveiliging

### RBAC

De [!UICONTROL &#x200B; stroom van de Gelijke van het Segment &#x200B;] om partners te beheren wordt beveiligd door RBAC. Alleen personen met de juiste machtiging kunnen partners initiëren, accepteren of beheren. Dit kan worden gedaan in het gedeelte Gegevensinname van het productprofiel. De volgende machtigingen zijn vereist:

![&#x200B; Verbinding van het Aandeel van het publiek &#x200B;](assets/data-ingestion.png){zoomable="yes"}

| Machtiging | Beschrijving |
|---|---|
| **beheer de Verbindingen van het Aandeel van het publiek** | Deze toestemming staat u toe om het proces van de partnerhanddruk te voltooien, dat twee organisaties IMS verbindt om [!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] stromen toe te laten. |
| **beheer de Aandelen van het publiek** | Deze toestemming staat u toe om, voer (het pakket van gegevens tot stand te brengen uit te geven die voor [!UICONTROL &#x200B; worden gebruikt de Overeenkomst van het Segment &#x200B;]) met actieve partners (partners die door de admin gebruiker met **toegang van het Aandeel van de Auditie** zijn verbonden). |

Verwijs naar de [&#x200B; officiële documentatie &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=nl-NL#understanding-segment-match-permissions) om meer over de toestemmingen te leren.

### Connect-id

De partner verbindt proces wordt beheerd door **[!UICONTROL verbind identiteitskaart &#x200B;],** die een willekeurig geproduceerd herkenningsteken is dat kaarten aan een specifieke zandbak van AEP. Deze Connect-id is vereist voor het initiëren en beheren van partnersandboxen. U kunt ook de Connect-id opnieuw genereren en zo nodig een partnerverbinding opnieuw configureren.

### Beheer

Om het even welke dataset of gegevensattributen met *C11* contractetiket worden beperkt voor de [!UICONTROL &#x200B; dienst van de Gelijke van het Segment &#x200B;]. De segmenten die die attributen gebruiken kunnen niet voor [!UICONTROL &#x200B; de Gelijke van het Segment &#x200B;] worden gebruikt. Dit verstrekt de controle waarop de segmenten voor [!UICONTROL &#x200B; gelijke van het Segment &#x200B;] kunnen of niet kunnen worden gebruikt. Daarnaast worden het aangepaste beleid en de gemaakte marketingacties ook afgedwongen. Het beleid is standaard uitgeschakeld en moet zijn ingeschakeld voor handhaving. Beperkingen zoals e-mailmarketing en onsite reclame die tijdens het delen van segmenten worden gekozen, worden ook verspreid en gedeeld met de partners.

### Toestemming

De toestemmingsmontages voor [!UICONTROL &#x200B; Overeenkomst van het Segment &#x200B;] kunnen op de volgende manieren worden beheerd:

* Op organisatieniveau, tijdens het instappen, gebruik makend van de opt-out of opt-in-instelling voor toestemmingscontroles.

  Deze instelling bepaalt of gebruikersgegevens kunnen worden gedeeld. De standaardinstelling is ingesteld op Weigeren om aan te geven dat gebruikersgegevens kunnen worden gedeeld met de aanname dat de AEP-klant al de vereiste toestemming heeft voor het gebruik van gegevensuitwisseling. U kunt deze instelling wijzigen en aanmelden door contact op te nemen met de Adobe-accountmanager en een extra controle in te stellen om AEP-klanten te dwingen hun toestemming expliciet bij te houden.

* Het plaatsen van het aandeelattribuut specifiek voor identiteiten (idSpecific) gebruikend de [&#x200B; Groep van de Inhoud en van het Gebied van de Voorkeur &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/xdm/field-groups/profile/consents.html?lang=nl-NL).

  Deze veldgroep biedt één objecttype veld, toestemmingen, voor het vastleggen van toestemmings- en voorkeursgegevens. [!UICONTROL &#x200B; de Overeenkomst van het Segment &#x200B;], door gebrek, zal alle identiteiten omvatten die niet uitdrukkelijk uit, voorbeeld zijn gekozen:

  ```
  "share": {
  `                `"val": "n"
  `     `}
  ```

  U kunt deze instelling wijzigen door contact op te nemen met Adobe Account Manager, zodat alleen     identiteiten met expliciete opt-in, bijvoorbeeld:

  ```
  "share": {
  `                `"val": "y"
  `     `}
  ```

### Meldingen

Het alarm wordt geproduceerd wanneer een partnerverbinding in werking wordt gesteld of wanneer de segmentvoer met partners wordt gedeeld.

## Workflow instellen

De workflow voor het instellen van een partnerverbinding wordt beheerd met de RBAC, zoals hierboven vermeld. Als de juiste machtigingen zijn ingesteld, moet de verbinding met een partnersandbox de Connect-id van die sandbox/instantie binnen de org van de partner delen.

Zodra een verbinding van de verzendende partner wordt gevraagd, moet het bij de ontvangende kant worden goedgekeurd om een veilige en veilige partneropstelling te verzekeren. De handdruk van de partnerverbinding zorgt ervoor dat de overeenkomst tussen de twee organisaties bestaat en staat Adobe toe om het [!UICONTROL &#x200B; proces van de Gelijke van het Segment &#x200B;] namens de organisatie te vergemakkelijken. Met de goedgekeurde verbinding en in actieve staat, kan het segment delend proces van beide kanten in werking worden gesteld.

### Segment delen

Het delen van segmenten met partner gebeurt slechts wanneer een gelijke op het geselecteerde herkenningsteken bestaat. Er kan een één-aan-vele partnerverhouding zijn, die betekent de segmenten met veelvoudige partners kunnen worden gedeeld.

Om segment in werking te stellen delend nadat de partnerverbinding opstelling is, zou de verzendende partner een voer moeten creëren. Selecteer vervolgens de gevallen of acties waarin de segmentgegevens moeten worden uitgesloten en de duurzame id&#39;s. De relevante segmenten kunnen dan aan het voer voor het delen worden toegevoegd.

Als deel van dit segment-delend werkschema, kan de verzendende partner potentiële high-value segmenten via geschatte overlappingen ontdekken alvorens om het even welke gegevens worden bewogen.

De algemene processtroom is:

![&#x200B; Segment delend &#x200B;](assets/segment-sharing.png){zoomable="yes"}

Deze overlappende ramingen bieden belangrijke inzichten, partnerontdekking, en gegevens aan de samenwerkingsovereenkomsten van brandstofgegevens. Er worden geen klant- of segmentgegevens over sandboxen verplaatst om deze schattingsgegevens voor overlappingen te verkrijgen. De door de klant geselecteerde, vooraf gehaaste toepasselijke identiteiten in een bepaalde sandbox worden toegevoegd aan een probabilistische gegevensstructuur die Adobe in staat stelt samenvoegings- en intersectiebewerkingen tussen hen uit te voeren. Deze verrichtingen helpen [!UICONTROL &#x200B; Overeenkomst van het Segment &#x200B;] krijgen de geschatte doorsnede van twee gegevensstructuren die uit identiteiten van twee verschillende zandbakken worden samengesteld zonder het moeten de daadwerkelijke waarden vergelijken

Het proces van de identiteitsoverlap hangt van de **dagelijkse volledige profieluitvoer** dataset van zowel afzender als ontvanger zandbakken af om gemeenschappelijke profielen te identificeren die tot de gedeelde segmenten behoren. De gedetailleerde processtroom voor het overlappingsproces wordt hieronder getoond:

![&#x200B; Identiteit overlappend proces &#x200B;](assets/overlap-process.png){zoomable="yes"}

Nadat het delen van segmenten volledig van de verzendende partner is, krijgt de ontvanger een bericht over het gedeelde segmentvoer. Deze segmentvoer moet voor profiel bij de ontvanger worden toegelaten om de gegevens van het segmentlidmaatschap in werking te stellen. Alleen segmentlidmaatschap wordt opgenomen in de overlappende profielfragmenten van de IMS-organisatie van de ontvanger en er wordt geen aanvullende identiteit overgedragen van de afzender naar de ontvanger.

Het gedeelde segment is beschikbaar onder de `AEPSegmentMatch` sectie van het **[!UICONTROL publiek]** lusje in de **[!UICONTROL Bouwer van het Segment]** en kan voor opneming of onderdrukking van publiek worden gebruikt terwijl het bouwen van segmenten in de ontvangerzandbak.

Het dagelijkse overlappingsproces houdt het segmentlidmaatschap synchroon tussen de afzender en de ontvanger. De ontvanger kan profiel voor het ontvangen segmentvoer onbruikbaar maken om het segment te pauzeren delend proces.

#### Afstap/ingang van segment

Als deel van de volledige profieluitvoer, heeft de status voor gedeelde segment-IDs onder het segmentlidmaatschap voor profielen één van de overeenkomstige waarden - _gerealiseerde_, _verlaten_, of _bestaand_ om op de huidige staat te wijzen.

Tijdens het dagelijkse proces van de identiteitsoverlapping, als de overeenkomstige identiteit in de ontvangerzandbak bestaat, worden deze status van het segmentlidmaatschap voor gedeelde segmenten verzonden over naar de ontvanger voor opname.

#### Intrekking van segment

De intrekking/schrapping van het segment van de afzender is een proces op bestelling waar de lijst van alle profielen met ingetrokken segment-IDs van de ontvanger wordt verkregen. De segment-IDs wordt verwijderd uit het segmentlidmaatschap van die identiteiten en bij de ontvanger hervat. Deze actie beschrijft het bestaande fragment van het segmentlidmaatschap, dat het lidmaatschap voor dat segment schrapt.

## De Overeenkomst van het Segment van het gebruik in Programmatische Overeenkomst

Met de toenemende beperkingen rond cookies en apparaat-id&#39;s van derden, zoekt programmatische reclame naar nieuwe manieren om doelgroepen op te bouwen en te richten. Er is een toenemend aantal oplossingen voor &#39;universele id&#39; voorgesteld, maar de industrie is nog steeds in volle beweging zonder een overeengekomen, schaalbare manier om hetzelfde streefniveau te bereiken en tegelijkertijd de toepasselijke privacyproblemen in evenwicht te brengen.

U kunt de Gelijke van de Segment van Adobe Experience Platform in privacy-centric publiekssamenwerking gebruiken en programmatic privé overeenkomsten tussen adverteerders en uitgevers verbeteren. Met Segment afstemmen kunt u:

* Splits **en de handel van de Advertentie** en **3&rbrace; werkschema&#39;s van het Publiek.**
* Sta partnermerken toe om publieksmeta-gegevens voor wederzijds gedeelde, en toestemmende identiteiten te delen gebruikend duurzame herkenningstekens zoals gehakt e-mail en gehakt telefoonaantal binnen een toestemming-gedwongen proces.

### Gebruiksscenario&#39;s

* Het richten van het eerste-partijpubliek door programmatic privé overeenkomsten.
* Onderdrukking van het publiek van de eerste partij via programmatic privé overeenkomsten.
* Gericht publiek dat lijkt op het publiek van de eerste partij dat via programmatische privé-deals wordt voorgezeten.

>[!BEGINSHADEBOX]

**overweeg het volgende voorbeeldwerkschema tussen een merk (Luma) en een media netwerk (ACME):**

1. Een merk (Luma) leidt een publieksgelijke met een media netwerk (ACME) via de Gelijke van het Segment.
2. ACME stuurt de doelgroep(en) via Adobe Real-Time CDP-doelen naar een server- of programmatische SSP.
3. ACME stelt een Private Inventory Deal (ID) met de toepasselijke die criteria op, met inbegrip van het publiek in de vorige stap wordt gevestigd. De persoonlijke-inventarisatie-id wordt vervolgens doorgegeven aan de DSP van Luma.
4. Luma vestigt een Private Inventory Deal en verkeerscampagne/creatief.
5. De campagne levert dan via programmatic Private Inventory Deal.
6. Vervolgens levert de advertentieserver of SSP advertenties die voldoen aan de vastgestelde doelcriteria. (Aanvullende criteria voor het toewijzen van doelen, zoals frequentietoewijzing, zijn beschikbaar via een advertentieserver en/of DSP, afhankelijk van het feit of een gegarandeerde deal of een voorkeurendeal in de overeenkomst is vastgelegd.)
7. Het verkeer wordt gedreven aan de merkeigenschappen van Luma.
8. ACME deelt vervolgens de inzichten of het publiek na de campagne via Segment Match voor heroriëntering.

>[!ENDSHADEBOX]

![&#x200B; een diagram van het werkschema tussen merk en uitgever.](./assets/segment-match-blueprints.png)

>[!IMPORTANT]
>
> Hoewel de hierboven geschetste oplossing een gemakkelijke manier verstrekt om eerstepartijgegevens via programmatic privé overeenkomsten te richten, kunnen er sommige overwegingen zijn alvorens uit te voeren, met inbegrip van, maar niet beperkt tot de volgende voorbeelden:
>
>* Toestemming: toepasselijke toestemmingsinzameling door het merk, de uitgever, of het netwerk van kleinhandelsmedia, aan hefboomwerking gegevens op deze manier.
>
>* Beleid en licentieovereenkomsten: naleving van alle toepasselijke beleidsregels (waaronder privacybeleid, overeenkomsten met leveranciers van derden) door het merk, de uitgever of het retail-medianetwerk om gegevens op deze manier te benutten en te activeren.



## Meer informatie

* [&#x200B; Overeenkomst van het Segment &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/overview.html?lang=nl-NL#)
* [&#x200B; Toestemmingen &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/access-control/home.html?lang=nl-NL)
* [&#x200B; het Oplossen van problemen &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/segmentation/ui/segment-match/troubleshooting.html?lang=nl-NL)
* [&#x200B; XID &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/identity/api/list-native-id.html?lang=nl-NL)
