---
name: use-case-pattern-builder
description: 'Geleider maken van nieuwe inhoud voor gebruikspatronen voor de Adobe Experience Platform-opslagplaats voor blauwdrukken. Gebruik deze vaardigheid wanneer het toevoegen van een nieuw gebruiks gevalpatroon, het creëren van de inhoud van de implementatiebegeleiding, of wanneer de gebruiker het toevoegen van patronen aan de blauwdrukplaats bespreekt. Verwerkt de volledige workflow: patrooninformatie verzamelen, het markeringsbestand met de juiste sjabloonstructuur genereren en alle kruisverwijzingspagina''s bijwerken (TOC.md, overview.md).'
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 0%

---


# Case Pattern Builder gebruiken

Deze vaardigheid leidt tot de verwezenlijking van een nieuw gebruiks gevalpatroon voor de het blauwdrukken bewaarplaats van Adobe Experience Platform. Het behandelt het volledige werkschema: het verzamelen van patrooninformatie van de gebruiker, het produceren van het dossier van de prijsdalingsinhoud met de correcte malplaatjestructuur, en het bijwerken van alle verwijzingspagina&#39;s zodat is het nieuwe patroon ontdekkbaar.

Lees voordat u begint de volgende referentiebestanden voor de volledige sjabloonstructuur en de controlelijst met pagina&#39;s die u wilt bijwerken:

- `references/pattern-template.md` — de volledige markeringssjabloon met plaatsaanduidingswaarden
- `references/pages-to-update.md` — De controlelijst van pagina&#39;s die moeten worden bijgewerkt wanneer een patroon wordt toegevoegd

## Fase 1: Informatie verzamelen

Interview de gebruiker om alle vereiste informatie te verzamelen alvorens om het even welke dossiers te produceren. Vraag naar het volgende en ga niet verder met het genereren van inhoud totdat elk item wordt opgegeven of expliciet wordt uitgesteld.

### Vereiste informatie

1. **naam van het Patroon** - de mens-leesbare titel (b.v., &quot;Gebeurtenis-teweeggebracht Overseinen&quot;).

2. **Categorie** — Precies één van het volgende:
   - `audience-building-activation`
   - `personalization`
   - `campaign-management-orchestration`
   - `analysis`
   - `conversational-experience`

3. **Primaire vermogensbeschrijving** - één enkele zin beschrijvend wat dit patroon (gebruikt in de overzichtstabel en de beschrijving van de frontmaterie) doet.

4. **de oplossingen van de Kern Adobe** — De producten van Adobe centraal aan dit patroon. Kies uit: Journey Optimizer, Real-Time Customer Data Platform, Experience Platform, Customer Journey Analytics, Brand Concierge, Journey Optimizer B2B edition, Real-Time CDP of andere landen, naar gelang van het geval.

5. **de kettingstappen van de Functie** — 3-6 opeenvolgende fasen die de de uitvoeringsstroom van het patroon beschrijven, die door `>` wordt gescheiden. Voorbeeld: &quot;Event Ingestie > Journey Entry > Condition Evaluation > Message Delivery > Reporting&quot;.

6. **gesteunde Bedrijfs doelstellingen** — Één of meerdere bedrijfsdoelstellingen van de bestaande reeks onder `/help/blueprints/business-objectives/`. Elk onderdeel moet de naam van het object, de submap van de categorie en de bestandsnaam bevatten. Controleer of de bestanden waarnaar wordt verwezen bestaan voordat u inhoud genereert.

7. **tactische gebruikscase van het Voorbeeld** - 6-10 bulleted scenario&#39;s die beschrijven hoe dit patroon over verschillende bedrijfscontexten kan worden toegepast. Elk scenario moet een vette naam hebben, gevolgd door een beschrijving.

8. **KPIs** — Een lijst met drie kolommen: KPI (naam), Beschrijving (wat het meet), Meting (formule of benadering) meet.

9. **de opties van de Uitvoering** — 2-4 implementatieopties. Verzamel voor elke optie:
   - Naam van optie
   - Best voor (wanneer deze optie wordt gebruikt)
   - Hoe het werkt (2-4 paragrafen)
   - Belangrijkste overwegingen (lijst met opsommingstekens)
   - Voordelen (lijst met opsommingstekens)
   - Beperkingen (lijst met opsommingstekens)
   - Experience League-koppelingen (URL&#39;s naar relevante documentatie)

### Optioneel maar aanbevolen

- Alinea&#39;s met gevaloverzicht gebruiken (3-5 alinea&#39;s; als deze niet zijn opgegeven, kunt u ze samenstellen op basis van de andere informatie.
- Toepassingenlijst met beschrijvingen van de rol van elke Adobe-app
- Foundational functions table (Function, Status, What Must be Place, Experience League Reference)
- Ondersteunende functietabel (functie, status, Waarom het belangrijk is, Experience League-referentie)
- Tabellen met toepassingsfuncties (één per toepassing, met functie, implementatiefase, beschrijving)
- Controlelijst voor vereisten

Als de gebruiker de optionele items niet levert, genereert u redelijke standaardinstellingen op basis van de patrooncategorie, de oplossingen en de functieketen.

## Fase 2: Inhoud genereren

Genereer het bestand met patroonmarkeringen op het volgende pad:

```
/help/blueprints/use-case-patterns/{category}/{kebab-case-pattern-name}.md
```

Voor de bestandsnaam moet gebruik worden gemaakt van een keybab-hoofdlettergebruik dat is afgeleid van de patroonnaam. &quot;Gebeurtenisgestuurde berichten&quot; wordt bijvoorbeeld `event-triggered-messaging.md` .

Gebruik de sjabloon uit `references/pattern-template.md` en vul alle waarden voor plaatsaanduidingen in met de verzamelde informatie. Het gegenereerde bestand moet elke sectie in de sjabloon bevatten:

1. **YAML frontt** — titel, beschrijving, oplossing (komma-gescheiden), exl-id (produceert placeholder UUID als `xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx` — het het publiceren team zal echte toewijzen).

2. **het Openen sectie** - `# {Pattern name}` rubriek gevolgd door een inleidende paragraaf en &quot;Gebruik deze gids om te begrijpen...&quot; zin.

3. **het gevaloverzicht van het Gebruik** — 3-5 paragrafen beschrijvend het patroonwerkingsgebied, wanneer het van toepassing is, wat het doet en niet doet, en wie de typische belanghebbenden zijn.

4. **Zeer belangrijke bedrijfsdoelstellingen** — Elke doelstelling als verbonden rubriek met een korte beschrijving en een KPIs summiere rij.

5. **tactische gebruikscase van het Voorbeeld** — Bulleted lijst van 6-10 scenario&#39;s.

6. **Zeer belangrijke prestatiesindicatoren** — Lijst met KPI, Beschrijving, de kolommen van de Meting.

7. **het gevalpatroon van het Gebruik** - de paragraaf van de beschrijving en de functieketen.

8. **Toepassingen** — Lijst van de toepassingen van Adobe met `[!DNL ...]` het formatteren en beschrijvingen.

9. **stichtende functies** — Lijst met kolommen: De functie van de Stichting, Status, wat op zijn plaats moet zijn, de Verwijzing van Experience League. Statuswaarden: vereist, verondersteld op plaats, niet van toepassing.

10. **Ondersteunende functies** — Lijst met kolommen: Het steunen van Functie, Status, waarom het, Verwijzing van Experience League van belang is. Statuswaarden: aanbevolen, inbegrepen, niet van toepassing.

11. **functies van de Toepassing** — Één lijst per toepassing met kolommen: Functie, de Fase van de Implementatie, Beschrijving.

12. **Eerste vereisten** — Controlelijst die `- [ ]` syntaxis gebruikt.

13. **de opties van de Implementatie** - 2-4 gedetailleerde opties, elk met Best voor, hoe het, Zeer belangrijke overwegingen, Voordelen, Beperkingen, en de verbindingen van Experience League werkt.

14. **de vergelijking van de Optie** — Summiere vergelijkingstabel aan het eind.

## Fase 3: Updates van kruisverwijzingen

Nadat u het patroonbestand hebt gegenereerd, werkt u de volgende bestanden bij. Lees `references/pages-to-update.md` voor de gedetailleerde controlelijst.

### TOC.md

**Dossier:** `/help/blueprints/TOC.md`

Voeg een nieuw item toe onder de juiste categoriesectie. De categorieën wijzen aan deze secties van TOC toe:

| Categorie-witruimte | Sectiekop van inhoudsopgave |
| --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation{#audience-building-activation}` |
| `personalization` | `+ Personalization{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience{#conversational-experience-patterns}` |

De invoernotatie is:

```
    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)
```

Voeg de nieuwe ingang na de laatste bestaande ingang in de passende sectie toe. De exacte inspringing behouden (vier spaties voor de `+` ).

### Overzicht pagina

**Dossier:** `/help/blueprints/use-case-patterns/overview.md`

Voeg een nieuwe rij toe aan de correcte categorietabel. De indeling is:

```
| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |
```

Voeg de nieuwe rij na de laatste bestaande rij in de overeenkomende categorietabel toe.

## Fase 4: Validatie

Controleer het volgende nadat alle bestanden zijn gemaakt en bijgewerkt:

1. **Bedrijfs objectieve verbindingen** — Elke bedrijfsobjectieve verbinding in het patroondossier richt aan een bestaand dossier onder `/help/blueprints/business-objectives/`. Gebruik een glob of een read om te bevestigen dat elk doelbestand bestaat.

2. **de ingangsplaatsing van TOC** - de nieuwe ingang van TOC is binnen de correcte categoriesectie en gebruikt het correcte inkeping en wegformaat.

3. **de lijstrij van het Overzicht** - de nieuwe overzichtsrij is in de correcte categorielijst en volgt het zelfde kolomformaat zoals bestaande rijen.

4. **Dossier noemend** — Patroonfilename gebruikt kebab-geval en past de weg aan die in zowel TOC.md als overview.md van verwijzingen wordt voorzien.

5. **de volledigheid van de Frontmaterie** — Het patroondossier omvat titel, beschrijving, oplossing, en exl-id in zijn voorzit YAML.

6. **de verbindingen van Experience League** — Spot-controle dat om het even welke Experience League URLs plausibel (begin met `https://experienceleague.adobe.com/nl`) is.

Meld eventuele validatiefouten aan de gebruiker en repareer deze voordat de taak is voltooid.

## Notities

- Gebruik altijd de syntaxis `[!DNL ...]` voor Adobe-productnamen in tabellen en platte tekst, volgens de conventie van bestaande patroonbestanden.
- De voorvoegsel `exl-id` moet een plaatsaanduiding voor de UUID zijn. De uitgeverspijplijn wijst de echte waarde toe.
- Als de gebruiker meerdere patronen tegelijk wil maken, herhaalt u fase 2-4 voor elk patroon, maar verzamelt u alle informatie in fase 1.
- Als een nieuwe categorie nodig is die niet in de bovenstaande lijst bestaat, waarschuwt u de gebruiker dat TOC.md en overview.md nieuwe secties nodig hebben, en behandelt u die als een afzonderlijke stap.
