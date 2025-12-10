---
title: B2B-reizen met Marketo-gegevensblauwdruk
description: Blauwdruk voor snelle implementatie van Journey Optimizer B2B edition met Marketo Engage-gegevens.
solution: Journey Optimizer B2B Edition
exl-id: d7bd0bd3-0f61-4e59-855f-27afc147c9aa
source-git-commit: c8ea7b87270a25420ad43dae4384d70603f00dcd
workflow-type: tm+mt
source-wordcount: '1706'
ht-degree: 0%

---

# B2B-reizen met Marketo-gegevensblauwdruk

Deze uitgebreide gids schetst het integratieproces van Marketo Engage met Adobe Journey Optimizer B2B edition. Het behandelt de configuratie van douaneschema, opname van profielen en rekeningen, en de organisatie van gepersonaliseerde reizen voor het kopen van groepen. Door gebruik te maken van Marketo Engage-gegevens zorgt deze blauwdruk voor een precieze doelgerichtheid en betrokkenheid op meerdere kanalen, waardoor meer gekwalificeerde vraag wordt gestimuleerd en de ervaringen van klanten worden verbeterd.

## Gebruiksscenario&#39;s

* **creeer en beheer het Kopen Groepen**: Gebruik generatieve AI om het kopen groepen binnen doelrekeningen samen te stellen en te beheren, die uitvoerige dekking van zeer belangrijke belanghebbenden verzekeren
* **Automatiseer de Taak van het Lid**: Wijs automatisch leden aan het kopen groepsrollen toe die op bepaalde criteria, zoals inhoudsconsumptie en de gegevens van CRM worden gebaseerd
* **Gepersonaliseerde Reizen**: Ontwerp en visualiseer multi-step reizen die aan elke het kopen groep en lid op hun rol, rekening, productrente, en levenscyclusstadium worden gebaseerd
* **Real-Time Automatisering**: Automatiseer de vooruitgang van rekeningen en het kopen van groepen door reizen met in real time betrokkenheidstrekkers en kwalificatie het scoren
* **Cross-Channel Engagement**: Neem het kopen groepen over veelvoudige kanalen, met inbegrip van e-mail, SMS, advertenties, praatje, gebeurtenissen, en webinars in dienst, om vraaggeneratie en kwalificatie te stroomlijnen
* **AI-Gedreven Inzichten**: Gebruik AI-gedreven inzichten om inhoudslevering en betrokkenheidsstrategieën voor individuele kopers en volledige het kopen groepen te optimaliseren
* **Verenigde Activering van Gegevens**: Activeer verenigde rekeningslijsten van Adobe Real-Time Customer Data Platform om de meest recente en volledige gegevens voor het kopen van groepsverwezenlijking en beheer te verstrekken
* **Verbeterde Collaboration**: Coördineer marketing en verkoopinspanningen om preciezere verkoopkansen tot stand te brengen en pijpleidingsverwezenlijking te versnellen

## Applicaties

* Journey Optimizer B2B Edition
* Real-time Customer Data Platform B2B edition
* Marketo Engage

## Integratiepatronen

| Integratie | Beschrijving |
| :-- | :--- |
| [&#x200B; de schakelaar van Marketo Engage &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) | Adobe Experience Platform vereenvoudigt het opnemen van gegevens van Marketo en biedt mogelijkheden om de gegevens te structureren, te labelen en te verbeteren met behulp van zijn services. |
| [&#x200B; Journey Optimizer B2B edition - de acties van Marketo Engage &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-nodes/action-nodes#marketo-engage-actions) | Synchroniseer Account-Based Marketing in Journey Optimizer B2B edition met op leads gebaseerde inspanningen in Marketo Engage door op mensen gebaseerde acties te gebruiken om het lidmaatschap van lijsten te beheren en om campagnes aan te vragen. |

## Architectuur

![&#x200B; architectuur van de Oplossing voor Journey Optimizer B2B edition met de gegevens van Marketo &#x200B;](./assets/ajo-b2b-architecture-simplified.png){zoomable="yes"}

## Implementatiestappen

1. Installeer B2B-schema&#39;s en naamruimten met een van de volgende opties:
   * De inzameling van Postman van het gebruik [&#128279;](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility){target="_blank"}
   * Gebruik [&#x200B; malplaatjes &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/ui-tutorials/templates) in Platform UI
1. Maak indien nodig relationele schema&#39;s om bedrijfsentiteiten, zoals aankopen, licenties of registraties van gebeurtenissen, te vertegenwoordigen voor beslissingen over reizen en personalisatie van e-mail.
1. Voltooi de [&#x200B; configuratie XDM &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/admin/xdm-field-management/xdm-field-management){target="_blank"}.
   * Herzie de reeks standaardXDM gebieden die door gebrek in Journey Optimizer B2B edition worden geselecteerd, die ook als _wordt bekend beheerde gebieden_. Herzie de reeks beheerde gebieden door naar Configuratie XDM in **[!UICONTROL Beleid]** te gaan > **[!UICONTROL Configuraties]**.
      * Selecteer het **[!UICONTROL Standaard]** lusje, dan klik **[!UICONTROL beheerde gebieden]** voor zowel het Individuele Profiel XDM als Van Bedrijfs XDM Rekening uitgeven.
      * Selecteer **[!UICONTROL tonen slechts geselecteerde gebieden]** optie om de huidige lijst van geselecteerde gebieden te zien.
      * Voeg zo nodig velden toe of verwijder velden.
         * `workEmail.address` is vereist voor de gegevensset Person.
         * `accountName` is vereist voor de gegevensset Account.
   * Vorm de reeks gebieden XDM die u voor het _profiel van de Update_ wilt gebruiken en _de acties van het de rekeningsprofiel van de Update_ in reizen. Deze gebieden zijn ook gekend als _updatable gebieden_.
      * op het _[!UICONTROL Standaard]_ lusje, klik **[!UICONTROL updatable gebieden]** voor zowel het Individuele Profiel XDM als Van Bedrijfs XDM Rekening uitgeven.
      * Selecteer het schema, de dataset, en de gebieden die u wilt bijwerken.
   * Vorm de relationele schema&#39;s en de gebieden die u in reizen wilt gebruiken.
      * Selecteer het **[!UICONTROL Relationele]** lusje, klik **[!UICONTROL Uitgezocht relationeel schema XDM]**.
      * Selecteer het schema, de naamruimte en de velden die u wilt gebruiken.
   * Configureer de ervaringsgebeurtenissen die u tijdens reizen wilt gebruiken.
      * Selecteer het **[!UICONTROL lusje van Gebeurtenissen]**, en klik dan **[!UICONTROL Uitgezochte ervaringsgebeurtenis]**.
      * Selecteer ervaringsgebeurtenis en velden die u wilt gebruiken.
1. Vorm de [&#x200B; bron van Marketo Engage schakelaar &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).
   * Gebruik het gegevenswoordenboek om de [&#x200B; afbeelding van de Invoer &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/data-prep/ui/mapping#import-mapping) voor de bronschakelaar te bepalen.
   * Het wordt geadviseerd om het profiel niet toe te laten alvorens de [&#x200B; overwegingen van de Implementatie &#x200B;](#implementation-considerations) rekening te nemen.
   * U wordt ook aangeraden ten minste personen, bedrijven, kansen en activiteiten in te voeren, omdat deze objecten het nuttigst zijn bij het maken van uw accountpubliek.
1. Voer [&#x200B; Regels van de Grafiek van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-graph-linking-rules/overview) voor Mensen uit:
   * Bepaal hoe de verslagen van de Persoon gebruikend identiteitsnamespaces verbonden zijn.
   * Configureer naamruimten en identiteitsstitching-regels in Experience Platform.
   * Koppelingen valideren met voorbeeld-Personen en voorvertoningsgereedschappen.
1. Laat de Persoon, Bedrijven, Kansen, en de gegevensreeksen van Activiteiten voor [&#x200B; profielen &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/user-guide#enable-profile) toe
1. Bepaal uw eerste [&#x200B; rekeningspubliek &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/audiences/account-audience-overview)
1. Gebruik het rekeningspubliek om a [&#x200B; het kopen groep &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/accounts/buying-groups/buying-groups-overview) of een [&#x200B; rekeningsreis &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/account-journeys/journey-overview) te bepalen.
   * Wanneer een account in aanmerking komt voor het accountpubliek, wordt de inkoopgroeptaak dagelijks uitgevoerd om inkoopgroepen te maken en rollen toe te wijzen aan gekoppelde personen zodra het publiek wordt bijgewerkt.
   * Daarnaast wordt het aanschaffen van groepsonderhoud elke vrijdag om middernacht CT uitgevoerd. Dit wekelijkse proces verwerkt updates, zoals het verwijderen van leden die niet meer in aanmerking komen of het toevoegen van nieuw gekwalificeerde leden die niet zijn vastgelegd tijdens de eerste publieksupdate.

## Aanbevolen instelling

Om de implementatie te stroomlijnen en de compatibiliteit met Adobe Journey Optimizer B2B edition te garanderen, wordt de volgende installatie aanbevolen:

* **Gebruik de standaardidentiteitsgebieden:**
   * _e-mail_ en _b2b_person_ zou als identiteitsgebieden in het schema van de Persoon moeten worden behouden om identiteit het stitching en publieksactivering te steunen.
* **gebruik de standaardafbeeldingen voor de Schakelaar van Marketo Source:**
   * Gebruik de uit-van-de-doos gebiedstoewijzingen die door Adobe worden verstrekt om gegevensopname te vereenvoudigen en configuratieoverheadkosten te verminderen.
* **standaardafbeeldingen van het Gebruik voor AJO B2B:**
   * Ga de [&#x200B; standaardgebiedsafbeeldingen &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/admin/xdm-field-management/field-mapping) voor Journey Optimizer B2B edition aan om verenigbaarheid met het kopen van groepslogica en reisorchestratie te verzekeren.
* **het gebiedsupdates van het Blok op alle gebieden behalve e-mail:**
   * In Marketo Engage, vorm gebiedsbeheer aan [&#x200B; blokupdates &#x200B;](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field) van Adobe Experience Platform voor alle gebieden behalve _e-mail_. Hierdoor blijft de gegevensintegriteit behouden en blijft het oplossen van identiteiten mogelijk.
* **voer identiteit het koppelen regels uit gebruikend e-mail als unieke identiteitsnamespace**
   * Vorm [&#x200B; identiteitsgrafiek die regels &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/features/identity-graph-linking-rules/overview) verbindt in Adobe Experience Platform om _e-mail_ uitdrukkelijk als unieke identiteit te gebruiken namespace. Deze regels zorgen ervoor dat de profielen nauwkeurig over gegevensbronnen worden vastgezet waar _e-mail_ aanwezig is, toelatend robuuste identiteitsresolutie. Volg de best practices van Adobe en definieer koppelingsregels die e-mail prioriteren als een stabiele en wereldwijd unieke id voor een consistente en privacycompatibele identiteitsgrafiek.
Deze instelling zorgt voor een evenwicht tussen het gemak van implementatie en gegevensbeheer, waardoor een betrouwbare basis wordt gelegd voor het organiseren van B2B-reizen.

## Implementatieoverwegingen

Bij de implementatie van Adobe Journey Optimizer B2B edition is het van cruciaal belang dat u de mogelijkheden voor identiteitsstitching begrijpt die worden geboden door het Real-Time Customer Data Platform. Dit platform voert identiteitsstitching op zowel de persoon als rekeningsniveaus uit, die een verenigde mening van klantengegevens verzekeren.

### Belangrijke punten

* **Identiteit die** plaatst: Het platform stitches identiteiten gebruikend standaardherkenningstekens zoals identiteitskaart van Marketo, identiteitskaart van CRM, en e-mail. Zo kunt u een uitgebreid profiel maken door gegevens uit verschillende bronnen samen te voegen.
* **Potentiële Risks**: Het gebruiken van e-mail als herkenningsteken voor het stitching kan tot onopzettelijke identiteitsondergang leiden. Dit betekent dat verschillende personen die hetzelfde e-mailadres delen, mogelijk onjuist worden samengevoegd in één profiel. Deze identiteitsondergang kan de nauwkeurigheid van de gegevens van CRM negatief beïnvloeden en zijn integriteit compromitteren.
* **het samenvoegen van Strategie**: B2B CDP gebruikt een op tijd-gebaseerde het samenvoegen strategie, waar meest recente lastUpdatedDate voor een bepaald profielattribuut wordt gebruikt. Deze strategie zorgt ervoor dat de meest recente gegevens in het profiel worden weerspiegeld.
* **Overwegingen voor E-mail**: Het is essentieel om grondig het gebruik van e-mail als herkenningsteken voor het samenvoegen van profielfragmenten te beoordelen. Hoewel het nuttig kan zijn, moet het risico van identiteitsondergang zorgvuldig worden afgewogen tegen de voordelen. Een nadeel is dat zonder e-mail als id extern publiekslidmaatschap dat door AJO B2B is gemaakt, niet in het bestaande profiel wordt geïntegreerd.
* **de Integratie van de Persoon van Marketo**: AJO B2B gebruikt de persoon van Marketo met laagste identiteitskaart van het Lood wanneer de veelvoudige verslagen van Marketo in één enkel profiel samenvoegen.

Door deze punten in mening te houden, kunt u weloverwogen besluiten over hoe te om identiteit te vormen stitching in Adobe Journey Optimizer B2B edition, die nauwkeurige en betrouwbare klantenprofielen verzekert.

### Resultaten van identiteitsvaststelling evalueren

De Dienst van de vraag kan worden gebruikt om het effect van identiteitsstitching in een niet-profieltoegelaten gegevensreeks te zien. De volgende vraag kan worden gebruikt om de evaluatie te doen

#### Aantal opgenomen records

Deze vraag keert het totale aantal verslagen terug die in de gegevensreeks van het persoonsprofiel worden opgenomen

```sql
select
    count(distinct b2b.personKey.sourceKey)
from
    marketo_person_ajo_b2b
```

#### E-mails dupliceren

Deze query retourneert het aantal persoonrecords dat moet worden samengevoegd als onderdeel van de identiteitsstitching van het platform.

>[!NOTE]
>
>De datasetlijst marketo_person_ajo_b2b wordt gebruikt om een volledig voorbeeld van te verstrekken hoe te met de dataset van de Persoon van Marketo te werken.
>U kunt de dataset van uw zandbak in de [&#x200B; Datasets &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/catalog/datasets/user-guide) werkruimte vinden.

```sql
select
    SUM(personCount)
from
    (
        select
            emailAddress,
            count(*) as personCount
        from
            (
                select
                    MAX(workemail.address) as emailAddress
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
```

#### E-mailadressen met dubbele records

Deze query retourneert de e-mails met de meest gedupliceerde records in de gegevensset.  Deze lijst kan worden gebruikt om sommige van deze verslagen te controleren om beter te begrijpen hoe het verbinden van de identiteiten Marketo en CRM kan beïnvloeden.  Zie het [&#x200B; overzicht van de Dienst van de Identiteit &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home) voor meer details over hoe de identiteit het verbinden werkt.

```sql
select
    *
from
    (
        select
            emailAddress,
            MAX(personId) as personId,
            count(*) as personCount
        from
            (
                select
                    b2b.personKey.sourceKey,
                    MAX(workemail.address) as emailAddress,
                    MAX(b2b.personKey.sourceId) as personId
                from
                    marketo_person_ajo_b2b
                where
                    workemail.address IS NOT NULL
                group by
                    b2b.personKey.sourceKey
            )
        group by
            emailAddress
        having
            count(*) > 1
    )
order by
    personCount desc
```

### Opties

#### E-mail als identiteit verwijderen

Na uw analyse, als u e-mail niet een geldig gebied om als identiteitsgebied bepaalt te gebruiken, dan kan het schema van de Persoon worden gewijzigd om [&#x200B; e-mail als identiteitsgebied &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/xdm/ui/fields/identity) te verwijderen

#### Updates blokkeren vanuit Adobe Experience Platform

Als het houden van e-mail als identiteitsgebied voor uw gebruiksgevallen het best is, is er de optie om [&#x200B; gebiedsupdates &#x200B;](https://experienceleague.adobe.com/en/docs/marketo/using/product-docs/administration/field-management/block-updates-to-a-field) te blokkeren die uit AJO B2B komen en AJO B2B om hoofdzakelijk op de gegevens van Marketo toe te lopen.

## Beveiligingsmechanismen

Raadpleeg de volgende officiële documentatie voor een volledig begrip van de instructies die van toepassing zijn op B2B-reizen met Marketo Engage:

* [&#x200B; Adobe Journey Optimizer B2B edition - de Beschrijving van het Product &#x200B;](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer-b2b.html)
Bevat specifieke instructies en gebruiksparameters voor Journey Optimizer B2B edition.
* [&#x200B; de Grafieken van de Plaatsing van Adobe Experience Platform &#x200B;](https://experienceleague.adobe.com/en/docs/blueprints-learn/architecture/architecture-overview/guardrails?lang=en)
Omvat algemene architecturale en plaatsingsbegeleiding over de oplossingen van Adobe Experience Platform.
* [&#x200B; Adobe Marketo Engage - de Beschrijving van het Product &#x200B;](https://helpx.adobe.com/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails)
Details van de prestatie- en gebruiksgaranties voor Marketo Engage, inclusief activerings- en CRM-synchronisatiegegevens.
* [&#x200B; Real-Time CDP Guardrails &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/guardrails/overview?lang=en)
Biedt richtlijnen voor gegevensinvoer, segmentatie en activeringslimieten binnen de Real-Time Customer Data Platform.

## Gerelateerde documentatie

* [&#x200B; B2B edition van het Platform van Gegevens van de Klant in real time &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [&#x200B; Begonnen het worden met het Platform van Gegevens van de Klant in real time B2B edition &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial)
* [&#x200B; Grafieken voor het Platform van Gegevens van de Klant in real time B2B edition &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails)
* [&#x200B; Adobe Experience Platform &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform)
* [&#x200B; de Dienst van de Identiteit van Adobe Experience Platform &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/identity/home)
* [&#x200B; Marketo Engage &#x200B;](https://experienceleague.adobe.com/en/docs/marketo/using/home)
* [&#x200B; Adobe Experience Platform - de Schakelaar van Marketo Source &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo)
* [&#x200B; de Documentatie van Adobe Journey Optimizer B2B edition &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/guide-overview)
* [&#x200B; XDM gebiedsbeheer (Journey Optimizer B2B edition) &#x200B;](https://experienceleague.adobe.com/en/docs/journey-optimizer-b2b/user/admin/xdm-field-management/xdm-field-management)
