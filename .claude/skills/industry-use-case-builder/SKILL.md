---
name: industry-use-case-builder
description: 'Het creëren van nieuwe industrie gebruiksgevallen voor de het blauwdrukken bewaarplaats van Adobe Experience Platform. Gebruik deze vaardigheid wanneer het toevoegen van een nieuw gebruiksgeval aan een industrie verticaal (detailhandel, automobielindustrie, gezondheidszorg, financiële diensten, verzekering, media & vermaak, telecommunicatie, reis & gastvrijheid, B2B), wanneer de gebruiker bedrijfsscenario''s aan de industriepagina''s, of wanneer het bijwerken van de gebruikscatalogus wil toevoegen. Behandelt de volledige werkstroom: het verzamelen van gebruikscase details, het beoordelen van rijpheidsniveau, het produceren van inhoud, het bijwerken van de de overzichtspagina van de industrie en gebruikscatalogus, en het aanhalen van de gebruik-geval-pictogram-generatorvaardigheid voor pictogramverwezenlijking.'
source-git-commit: ed8928687806b619e95d8d320478d27c13722a80
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 1%

---


# Bedrijfs-gebruik Case Builder

Deze vaardigheid leidt tot de creatie van nieuwe industrie gebruiksgevallen voor de het blauwdrukken bewaarplaats van Adobe Experience Platform. Volg elke fase opeenvolgend. Lees de referentiebestanden voordat u begint:

- `references/use-case-template.md` — exacte sjabloon voor gebruik van hoofdlettersecties
- `references/catalog-row-template.md` — exacte notatie voor tabelrijen met catalogus
- `references/maturity-criteria.md` — Gedetailleerde rubriek voor beoordeling van de looptijd

## Fase 1: Informatie verzamelen

Bekijk de gebruiker om alle vereiste details te verzamelen voordat u inhoud genereert.

### Vereiste velden

1. **Verticale Industrie** — moet één van zijn:
   - automobielindustrie
   - b2b
   - financiële diensten
   - gezondheidszorg
   - verzekering
   - media-entertainment
   - kleinhandel
   - telecommunicatie
   - reisgastvrijheid

2. **het gevalnaam van het Gebruik** - een duidelijke, beschrijvende titel (b.v., &quot;Verlaten E-mail van de Kar Terugwinning&quot;, &quot;de Campagnes van de Overerving van de Geneesmiddelen&quot;).

3. **Beschrijving** — 1-2 zinnen beschrijvend het bedrijfsscenario en waarom het van belang is.

4. **Bedrijfs effect** — De gekwantificeerde resultaten met specifieke metriek (b.v., &quot;20-30% verhoging van klikthrough tarieven&quot;, &quot;15-25% verbetering in hervultarieven&quot;).

5. **het gevalpatroon van het Gebruik** - moet aan precies één van deze bestaande patronen in kaart brengen:
   - Audience Activation naar bestemmingen
   - Publiek Collaboration met segmentovereenkomst
   - Gebeurtenis doorsturen
   - B2B Audience Activation
   - Anonieme bezoeker van Web Personalization
   - Bekende bezoeker Web/App Personalization
   - Besluitvorming over aanbiedingen
   - Gedragsaanbeveling
   - Batch Outbound Message Activation
   - Gebeurtenisgestuurde berichten
   - Meerdere stappen geordende reis
   - Kanaalreis met beslissing
   - Op groep gebaseerde marketing en reisbeheer kopen
   - Klantenanalyse en Insight Generation
   - B2B-analyse
   - Brand Concierge Conversation Experience

6. **Technische overwegingen** — 4-8 bulletpoints die gegevensvereisten, integratie, regelgevende/nalevingsbehoeften, prestatiesoverwegingen, en architecturale nota&#39;s behandelen.

Vragen naar ontbrekende velden voordat u verdergaat. Neem geen details over of fabriceer deze niet.

## Fase 2: Looptijdbeoordeling

Lees `references/maturity-criteria.md` voor de volledige rubriek. Eén van de drie looptijdniveaus toewijzen:

- **Foundational** `[!BADGE Foundational]{type=Neutral}` - enig-stap of gebeurtenis-teweeggebrachte patronen (gebeurtenis-teweeggebracht Overseinen, Uitgaande Partij van de Partij), ongecompliceerde gegevensvereisten, minimale AI/ML, standaardintegraties.
- **Opkomende** `[!BADGE Emerging]{type=Informative}` — multi-step reizen, gedragsgegevens, aanbevelingen modellen, bekende-bezoekerspitalisatie, gematigde integratieingewikkeldheid.
- **Geavanceerd** `[!BADGE Advanced]{type=Caution}` — Beslissing over meerdere kanalen, AI-Gerichte voorspelling, bied besluit, complexe orkest, veelvoudige systeemintegratie aan.

### Beoordelingsworkflow

1. Identificeer welk gebruikspatroon de gebruikscase aan kaart brengt.
2. Controleer de lijst &quot;Typische patronen&quot; in de looptijdcriteria voor een snelle overeenkomst.
3. Als het patroon niet duidelijk op rijpheid wijst, evalueer gegevensingewikkeldheid, AI/ML vereisten, en integratiewerkingsgebied.
4. Presenteer de beoordeling aan de gebruiker met het redeneren: &quot;Gebaseerd op de patroonafbeelding ({pattern}) en {key factors}, zou ik dit als {level} wegens {reasoning} classificeren.&quot;
5. Wacht tot de gebruiker bevestigt of met voeten treedt alvorens aan inhoudsgeneratie te werk te gaan.

## Fase 3: Inhoud genereren

Inhoud genereren of bijwerken in twee bestanden.

### A. Sectoroverkoepelend bestand

**weg van het Dossier:** `/help/blueprints/industry-use-cases/{industry}/{industry}-overview.md`

Lees eerst het bestaande bestand om de huidige structuur en inhoud te begrijpen. Voeg vervolgens een nieuwe sectie toe die volgt op de exacte sjabloon uit `references/use-case-template.md` :

```markdown
## {Use Case Title}

{1-2 sentence description of the business scenario and why it matters}

### Business impact

{Quantified business outcomes, e.g., "Retailers typically see a 20-30% increase in click-through rates..."}

### How to implement

Use the [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) pattern. {1-2 sentence explanation of why this pattern applies}

### Technical considerations

- {4-8 bullet points covering data integration, regulatory, performance, or architectural considerations}
```

Plaats de nieuwe sectie na de bestaande gebruikscase-secties, met behoud van een consistente opmaak.

### B. Hoofdlettercatalogus gebruiken

**weg van het Dossier:** `/help/blueprints/industry-use-cases/use-case-catalog.md`

Lees eerst het bestaande catalogusbestand. Voeg een nieuwe rij toe aan het correcte industrietusje. De catalogus gebruikt een structuur met tabs met `>[!TAB {Industry}]` markeertekens. Elk tabblad bevat een tabel met de volgende kolommen:

| Kolom | Inhoud |
| --- | --- |
| Pictogram | `<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">` (leeg laten als er nog geen pictogram is) |
| Gebruiksscenario | `[{Use Case Title}]({industry}/{industry}-overview.md#{anchor})` waarbij anker de kop in hoofdletters/kleine letters is |
| Beschrijving | Overzicht van één zin |
| Looptijd | Badgesyntaxis voor het toegewezen niveau |
| Patroon | `[{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md)` |

**de regel van de Plaatsing:** binnen elk industrie lusje, worden de rijen gegroepeerd door volwassenheid in deze orde: Begonnen eerst, dan het Opkomen, dan Geavanceerd. Plaats de nieuwe rij aan het einde van de correcte looptijdgroep.

De paden voor patroonbestanden zijn:
- `audience-building-activation/audience-activation-to-destinations.md`
- `audience-building-activation/audience-collaboration-segment-match.md`
- `audience-building-activation/event-forwarding.md`
- `audience-building-activation/b2b-audience-activation.md`
- `personalization/anonymous-visitor-web-personalization.md`
- `personalization/known-visitor-web-app-personalization.md`
- `personalization/offer-decisioning.md`
- `personalization/behavioral-recommendation.md`
- `campaign-management-orchestration/batch-outbound-message-activation.md`
- `campaign-management-orchestration/event-triggered-messaging.md`
- `campaign-management-orchestration/multi-step-orchestrated-journey.md`
- `campaign-management-orchestration/cross-channel-journey-with-decisioning.md`
- `campaign-management-orchestration/buying-group-based-marketing.md`
- `analysis/customer-analytics-insight-generation.md`
- `analysis/b2b-analytics.md`
- `conversational-experience/brand-concierge-conversational-experience.md`

## Fase 4: Pictogramgeneratie

Nadat de inhoud is gemaakt, roept u de `use-case-icon-generator` -vaardigheid aan om een pictogramspecificatie voor het nieuwe gebruiksgeval te genereren. Verstrek de vaardigheid van:
- De naam van het gebruiksgeval
- De industrie verticaal
- Een korte beschrijving van de gebruikszaak

Wanneer de gebruiker het gegenereerde pictogrambestand heeft, werkt u de catalogusrij bij en voegt u de pictogramverwijzing in:

```
<img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40">
```

## Fase 5: Validatie

Controleer vóór het voltooien het volgende:

1. **de naleving van het Malplaatje** — De industrie overzichtssectie volgt precies het malplaatje (## rubriek, beschrijving, ## Bedrijfs effect, ### hoe te om uit te voeren, ### Technische overwegingen).
2. **catalogusplaatsing** - de catalogusrij is in het correcte industrietuslusje en in de correcte rijpingsgroep (Begonnen, dan Ontkomende, dan Geavanceerde).
3. **geldigheid van de verbinding van het Patroon** — De patroonverbinding in zowel het overzicht als de catalogus gebruikt een geldig pad van het patroondossier van de bovenstaande lijst.
4. **consistentie van het Anker** — Het anker in de catalogusverbinding (b.v., `#abandoned-cart-email-recovery`) past de `##` rubriek in het overzichtsdossier aan dat in kebab-geval wordt omgezet.
5. **de wegovereenkomsten van het Pictogram** - de pictogramweg volgt `assets/use-case-icons/{industry}/icon-{kebab-name}.png`.

Meld eventuele problemen die tijdens de validatie zijn aangetroffen en los deze op voordat u deze voltooit.
