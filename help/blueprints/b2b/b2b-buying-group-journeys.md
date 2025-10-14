---
title: Op groep-gebaseerde Bladeren van de Marketing en van het Beheer van de Reis
description: Leer hoe u een reis kunt herkennen, ontwerpen en maken die in aanmerking komt voor een inkoopgroep in Adobe Journey Optimizer B2B edition.
solution: Journey Optimizer B2B Edition
exl-id: 0a9da49c-f13a-4f2a-8407-277def2db591
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '2118'
ht-degree: 0%

---

# Blauwdruk voor op groep gebaseerde marketing en reisbeheer kopen

Marketing teams hebben momenteel te maken met vele uitdagingen bij het bieden van gekwalificeerde leads aan Sales. Een van deze uitdagingen is het werken met de juiste mensen in de organisatie en is meestal duidelijk in inspanning en nauwkeurigheid. Met _lood het scoren_, is de groep te smal en de teams zouden de juiste mensen kunnen missen. Met _rekening het scoren_, is er grotere inspanning wordt vereist om de juiste persoon met zulk een brede mening van een rekening te identificeren.

Deze uitdaging is waar het concept **_het kopen groep_** wordt geïntroduceerd. Een inkoopgroep stelt marketers in staat de juiste groep personen in de account te vinden en met deze personen samen te werken door de lens te gebruiken om de leads te kwalificeren en hun rol in de groep te identificeren.

## Hoe koopgroepen worden gebruikt om leads en accounts te kwalificeren

Door een inkoopgroep op te richten en te trachten deze te voltooien, wordt de marketingactiviteit doeltreffender bij het in aanmerking nemen van producten, wat verkoopmogelijkheden tot gevolg heeft. Het kopen van groepen wordt verbonden aan passende lood aan rolmalplaatjes die met de intentie van de Oplossing verbonden zijn.

Een voorbeeld van een het kopen groep zou _Acme Corp Seeds Kopen Groep_ kunnen zijn, die een oplossingsrente van _AI Gedreven Zaden_ heeft.

De het kopen groepen vertegenwoordigen een groep mensen bij het bedrijf die in een oplossing door een oplossingsintent geinteresseerd zijn. En een koopgroep zou voor meer dan één oplossingsbelang kunnen worden geïdentificeerd en de individuen verschijnen in meer dan één die groep koopt.

Dankzij de verbeterde B2B-mogelijkheden die Journey Optimizer B2B edition biedt, kunt u nu de volgende uitdagingen aangaan:

* Een gebrek van _klant-eerste_ marketing campagnes.
* Inconsistente MQL (Marketing Qualified Lead)-conversie naar SQL (Sales Qualified Lead), waardoor het nodig is initiatieven af te stemmen op de verkoop om MQL te voeden
* Gebrek van een verkoopbaar mechanisme om _te identificeren en te richten beconcurreren_ rekeningen.
* Concentratierisico in inkomsten en pijplijnen.

De volgende KPIs richt zich goed op het meten van het succes van gebruiksgevallen:

* **Bewustheid**: Zijn doelklanten die uw advertenties zien en drijft het hen aan uw website aan een hoger tarief dan voordien?
* **Betrokkenheid**: komen de doelklanten aan uw website en het in dienst nemen met inhoud?
* **Tijd**: Hoeveel tijd neemt het het team van de Verkoop om contacten van diverse hulpmiddelen aan de kans te vinden en toe te voegen?
* **Kosten**: Hoeveel geld leidt elk kosten op elk platform?

## Op account gebaseerde marketing

Een veel voorkomend geval van gebruik, en de nadruk in deze blauwdruk, is een op rekening-gebaseerd marketing initiatief. Deze gebruikszaak verkent het punt waar de door u gemaakte inkoopgroep is gevuld met een lead wanneer deze is gekoppeld aan een rol- en oplossingsbelang.

Terwijl u een individu door de reis leidt, verzamelt u meer informatie over de lead (de Werkstroom van de Groep van het Kopen), door vormen, de Synchronisatie van CRM, en LinkedIn activering.

Wanneer een lood duidelijk de oplossingsrente toont, wijst het op een bedrijfsgebeurtenis die door een bedrijfslens wordt bepaald. Op dit moment is het bedrijf ervan overtuigd dat deze voorsprong echt geïnteresseerd is in een product. In Journey Optimizer B2B edition is de lead gekoppeld aan een inkoopgroep voor die oplossing in een rolsjabloon (zoals invloeden, besluitvormers, kampioenen en sponsors).

Zoals in het volgende diagram wordt geïllustreerd, kunt u details verzamelen in formulieren of via LinkedIn-activering en een oplossingsintentie kwalificeren wanneer interactie met een chats-bot optrad.

![&#x200B; het Kopen groepsreis &#x200B;](./assets/buying-group-journey-diagram.svg){zoomable="yes"}

Wanneer het volledige percentage van de inkoopgroep hoog genoeg is, deelt u de groep met het verkoopteam via SQL of een SOL om de leads in de account om te zetten in een voltooide verkoop.

## Accountgerichte oplossing

B2B-hoofdmanagement is gericht op accounts en hun leiding. De technische laag is opgezet om de gegevens te steunen die deze kenmerken vertegenwoordigen, wat een vereiste voor succesvolle rekeningssegmentatie en reisbeheer is.

### Vereisten

De rekening-geconcentreerde oplossing vereist de volgende toepassingen en de diensten:

* Adobe Journey Optimizer B2B edition
* Adobe Real-time Customer Data Platform (RTCDP) B2B edition
* Adobe Marketo Engage

>[!NOTE]
>
>De licentie voor Journey Optimizer B2B edition moet de volgende items bevatten:
><ul><li>Journey Optimizer B2B edition-instantie die is verbonden met Experience Platform B2B</li><li>Marketo Engage-instantie die wordt gesynchroniseerd met RTCDP</li></ul>
>&gt;<br/>
>&gt;Voor bestaande Marketo Engage-klanten is een verbinding met het bestaande exemplaar de aanbevolen aanpak.
>&gt;<br/><br/>
>&gt;Er zijn aanvullende extensies beschikbaar voor de oplossing om de rijkheid van profielen te verbeteren:
>&gt;<ul><li>Extra bronnen naar RTCDP om het profiel te verrijken</li><li>RTCDP-bestemming naar Marketo Engage</li></ul>

De implementatie van deze oplossing vereist ook een duidelijk inzicht in het concept _Rekening_ en _het Kopen groep_, en hoe zij uw kwalificatie van het verkooplood versterken en versnellen. Op deze manier moet u ook de gewenste volledigheidsscore voor de koopgroep identificeren.

### Architectuur

![&#x200B; architectuur van de Oplossing voor het kopen van op groep-gebaseerde marketing en reisbeheer &#x200B;](./assets/ajo-b2b-architecture.png){zoomable="yes"}

### Gegevensschema

Bij elke implementatie van gegevensgestuurde automatisering van de marketing is het ontwerpen van schema&#39;s van cruciaal belang voor het welslagen van de implementatie. Alvorens u uw schema ontwerpt, herzie [&#x200B; B2B namespaces en schema&#39;s &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo-namespaces) en zorg ervoor dat u het auto-generatienut begrijpt dat beschikbaar is om een nieuw schema in een nieuw implementatiescenario te produceren.

De schema&#39;s zijn specifiek verrijkt met B2B-gegevenselementen ter ondersteuning van de rijke relatie in profielen en omvatten het perspectief van de account via `sourceKey` om gebeurtenissen en profielen aan het accountschema te koppelen. De schema&#39;s zijn een vertegenwoordiging van uw organisatorische vereisten en de verzamelde en geprofileerde gegevens. Om aan deze behoeften te voldoen, zijn B2B-schema&#39;s flexibel en vormen zij een uitbreiding van de vereiste B2B-elementen.

Wanneer het ontwerpen van het gegevensschema voor uw organisatie, is het een beste praktijk om de belangrijkste entiteiten in uw ERD met de entiteiten op hoog niveau te vertegenwoordigen en te etiketteren. (Verwijs naar het eerste diagram in de [&#x200B; het schemadocumentatie van RTCDP B2B &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/tutorials/relationship-b2b)). Dit proces is zeer nuttig voor het begrip van de vereiste gegevenselementen die u in elk schema moet bepalen.

Op dit moment kunnen de ervaringsgebeurtenissen nog geen invloed hebben op de reizen. Naast de schema&#39;s van de Gebeurtenis van de Ervaring, adviseert men dat u eigenschappen aan de rekening toevoegt die belangrijke besluiten vertegenwoordigen die op gebruikersactiviteiten worden gebaseerd. Deze eigenschappen worden gebruikt voor gesplitste wegelementen in de reisontwerper.

>[!NOTE]
>
>Momenteel wordt de enige relatie die door Journey Optimizer B2B edition wordt ondersteund, gevormd door de directe relaties via het kenmerk `personComponents[0].sourceAccountKey.sourceKey` op de entiteit `Person` . De toekomstige uitbreiding wordt gepland om rekening-persoon relatievoorwerp in het B2b schema aan te passen.

### Marketo Engage-bronaansluiting

Als u de gegevenselementen van de account wilt verrijken, kunt u Marketo Engage en de bijbehorende B2B-gegevens gebruiken om de RTCDP- en Journey Optimizer B2B edition-accountweergave te verrijken. Door de Marketo Engage Source Connector in te stellen en Marketo Engage-gegevens toe te wijzen aan RTCDP-schemakenmerken, kunnen gegevens van Marketo Engage naar RTCDP en, indien aangewezen, naar het profiel stromen.

Voor gedetailleerde informatie over de schakelaarconfiguratie en de vereiste gebiedstoewijzing aan het schema, verwijs naar de [&#x200B; de schakelaardocumentatie van Marketo Engage &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo).

### Beveiligingsmechanismen

De Journey Optimizer B2B edition guardrails zijn gedetailleerd in de [&#x200B; pagina van de Beschrijving van het Product &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-journey-optimizer-b2b.html).

Implementatiegerelateerde geleidingssystemen

* Alle B2B de gidsen van de Publiek worden beschreven in [&#x200B; B2B de blauwdruk van de Activering van het Publiek en van het Profiel &#x200B;](https://experienceleague.adobe.com/nl/docs/blueprints-learn/architecture/b2b-activation/b2bactivation) worden direct omgezet aan het succes van Journey Optimizer B2B edition.
* Als de activering door de kanalen van Marketo Engage in de rekeningsreis wordt vereist of waar de Synchronisatie van CRM wordt gebruikt om de rekening te verrijken, zijn de [&#x200B; Verwante waarborgen Marketo Engage &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-marketo-engage---product-description.html#performance-guardrails) relevant.

Herzie de [&#x200B; documentatie van de Grafieken van Real-Time CDP &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/rtcdp/guardrails/overview) voor extra details voor de Grafieken van RTCDP.

### Provisioning

* Alle instanties moeten zich in dezelfde IMS-organisatie bevinden.
* Er kan slechts één Journey Optimizer B2B edition-instantie worden gekoppeld aan één Experience Platform-sandbox.
* Het wordt hoogst aangemoedigd om de [&#x200B; Schakelaar van Marketo Source aan het Platform van Gegevens van de Klant in real time &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo) uit te voeren.

## Implementatie

De volgende stappen bieden hulp bij het inschakelen van inkoopgroepen in uw Journey Optimizer B2B edition-exemplaar, waaronder activering van het publiek ter ondersteuning van de uitbreiding van uw accountbasis met de focus op ontbrekende rollensjablonen voor inkoopgroepen.

### Vooraf vereiste stappen

1. Bepaal het XDM schema dat uw bedrijfsmening van Rekeningen en Leads zal vertegenwoordigen.

   Als eerste stap, bepaalt en creeert u een ervaringsschema dat wordt ontworpen om de B2B gebruikscase behoeften te passen en de gegevensbronnen, zowel partij als echt te behandelen - tijd. Dit ontwerp moet de manier weergeven waarop het bedrijf aan de account- en persoonentiteiten denkt en de gebruiksgevallen die u wilt ondersteunen. Voor het schema om een B2B- schema te zijn, zou het schema de structuren moeten volgen beschikbaar in de [&#x200B; documentatie van het Schema van RTCDP B2B &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/xdm/tutorials/relationship-b2b).

   Een nuttige praktijk is de entiteitnamen van het diagram te nemen en die entiteiten in uw schema te identificeren door hen op de zelfde manier te etiketteren. Houd er rekening mee dat bepaalde schema&#39;s specifieke toetsen vereisen, zoals `sourceKey` , om te kunnen functioneren in RTCDP B2B. Voor de korte termijn, wordt het _vele-aan-vele_ verband tussen rekening en persoon door de Verhouding van de Persoon van de Rekening niet gesteund in Journey Optimizer B2B. Gebruik de versnellingsscripts voor het beste startpunt:

   * Gebruik het [&#x200B; het manuscript van de schemaverwezenlijking van RTCDP B2B &#x200B;](https://github.com/adobe/experience-platform-postman-samples/tree/master/Postman%20Collections/CDP%20Namespaces%20and%20Schemas%20Utility) om het aanvankelijke schema te produceren
   * Voeg gebruikscase-specifieke velden toe aan de schema&#39;s die worden gegenereerd om het schema te voltooien en aan te passen aan de behoeften van de organisatie.

   In dit stadium, hebt u de verbinding tussen Marketo Engage en RTCDP en de schemastructuur om de rekening en persoongegevens goed te keuren om de datasets voor de Segmenten van de Rekening te bevolken wordt bepaald. De volgende stap is RTCDP te verbinden met Marketo Engage en Journey Optimizer B2B edition.

1. Configureer de Marketo Engage-connector, inclusief de toewijzing van Marketo Engage aan de XDM-structuur.

   Met de XDM-structuur en -velden op zijn plaats gaat u verder om Marketo Engage met RTCDP te verbinden via de connector, die de gegevenssets doorvoert met gegevens van Marketo Engage en Journey Optimizer B2B. Begin door de toewijzing voor de gebieden van Marketo Engage aan de klassen van RTCDP te organiseren. Gebruik de informatie in de [&#x200B; schakelaardocumentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo#field-mapping-from-marketo-engage-to-xdm) om de gebieden te identificeren die u van uw implementatie van Marketo Engage wilt omvatten.

### Configuratie van kopersgroep

1. Maak een accountpubliek in Journey Optimizer B2B edition of RTCDP.

   Schakel de optie voor het plannen van alle soorten publiek in de klant → Soorten publiek → Bladeren op pagina in om accountpubliek in te schakelen. (Als dit niet werkt, moet u een segment Klantprofiel maken om accountpubliek te kunnen maken.)

   Om een segment tot stand te brengen, volg de stappen in de [&#x200B; documentatie van het rekeningspubliek &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer-b2b/user/account-audiences/account-audience-overview). Het gebruik van Segment Builder met de gegevensvelden die u als sleutel voor uw accountpubliek hebt geïdentificeerd, zou de belangrijkste activiteit zijn bij het definiëren van het publiek.

   Op dit moment weet u dat de account ertoe leidt dat de focus op RTCDP wordt gericht en dat deze wordt gebruikt voor de bouwstenen van de inkoopgroep.

1. Definieer de rolsjabloon.

   In elke het kopen groep, identificeer de rollen die de rol vertegenwoordigen de individuen in de groep nemen u wilt richten. Bijvoorbeeld, kon u _besluitvormer_ gebruiken, _invloedrijver_, en _kampioen_. Bepaal ook het gewicht en de voorwaarden voor deze rol in de koopgroep.

   De [&#x200B; documentatie van rolmalplaatjes &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-role-templates) beschrijft dit proces en hoe te om speciale voorwaarden te bepalen.

1. Bepaal de oplossingsrente.

   Een oplossingsbelang is een manier om aan te geven welke inkoopgroepen zich richten op uw marketingactiviteiten en -strategie.

   Om een oplossingsrente te bepalen, volg de stappen in de [&#x200B; documentatie van de oplossingsbelangen &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer-b2b/user/buying-groups/solution-interests). Houd er rekening mee dat u deze gebruikt om de inkoopgroep aan te passen aan een verkoopinitiatief in de organisatie.

1. Configureer de inkoopgroep.

   Met de bouwstenen van de het kopen groep klaar, vorm de het kopen groep voor de oplossingsrente en rekeningspubliek met een doel om het rolmalplaatje met de juiste leden van de rekening te voltooien. Met deze configuratie, wijs een oplossingsbelang aan het rolmalplaatje toe dat u identificeerde en u geeft elke rol een gewicht in het verkoopsucces voor dat specifiek product.

   Om de het kopen groep te bouwen, volg de stappen in de [&#x200B; het kopen groepsdocumentatie &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer-b2b/user/buying-groups/buying-groups-create).

   In dit stadium, bent u bereid om [&#x200B; een reis &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer-b2b/user/account-journeys/journey-overview#get-started-with-a-journey) te creëren en met het Publiek van de Rekening te gaan werken om de het kopen groep op te bouwen en hen voor de oplossingsrente te kwalificeren.

### Activering publiek

Verhoog de volledigheid van de inkoopgroep door activering van het publiek.

1. Definieer een publiek van een LinkedIn-advertentie-account.

   Naast e-mail- en formulierinvulactiviteiten biedt Journey Optimizer B2B edition een LinkedIn-advertentie-mogelijkheid om de openheid van uw account te vergroten en de inspanningen te ondersteunen om een inkoopgroep te voltooien door de uitbreiding van het aantal leads voor accounts en het bereik van uw marketingactiviteiten te vergroten.

   Om LinkedIn Betaalde media voor het communiceren met de rekeningen te gebruiken waar de het kopen groepen niet worden voltooid of genoeg geëngageerd, uitbreiden of met het Publiek van de Rekening in dienst nemen, gebruik het [&#x200B; LinkedIn Verpaste vermogen van het Publiek &#x200B;](https://experienceleague.adobe.com/nl/docs/journey-optimizer-b2b/user/account-audiences/linkedin-account-matched-audiences) om LinkedIn Ad publiek door de Verwante Publiek van de Rekening te produceren.

1. Activeer het publiek voor het kopen van groepen.

>[!TIP]
>
>Enkele tips voor succesvolle campagnes:
>
>* Een campagne zou rolfilters moeten hebben om koopgroepen met ontbrekende rollen aan te passen om ROI te verhogen.
>* Als u leads wilt vastleggen, leidt Direct naar invulformulieren (LinkedIn- of Marketo Engage-formulieren) en wordt de focus van het formulier gewijzigd.
