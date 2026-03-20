---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---
# Pagina&#39;s die moeten worden bijgewerkt wanneer een gebruikspatroon wordt toegevoegd

Wanneer u een nieuw gebruikspatroon maakt, moeten de volgende pagina&#39;s worden bijgewerkt om te zorgen dat het patroon kan worden gedetecteerd en correct is gekoppeld.

## Vereiste updates

### 1. TOC.md
- **Dossier:** `/help/blueprints/TOC.md`
- **Actie:** voeg een nieuwe ingang onder de correcte categoriesectie toe
- **Formaat:** `    + [{{Pattern Title}}](/help/blueprints/use-case-patterns/{{category}}/{{filename}}.md)`
- **Plaats door categorie:**
   - Audience Building &amp; Activation: after line ~47 (after existing entries in that section)
   - Personalization: na lijn ~52
   - Campagne Management &amp; Orchestration: na lijn ~58
   - Analyse: na lijn ~61
   - Conversationele ervaring: na lijn ~63

#### Toewijzing van categorie naar inhoudsopgave

| Categorie-witruimte | Sectiekop van inhoudsopgave | Anker |
| --- | --- | --- |
| `audience-building-activation` | `+ Audience Building & Activation` | `{#audience-building-activation}` |
| `personalization` | `+ Personalization` | `{#personalization-patterns}` |
| `campaign-management-orchestration` | `+ Campaign Management & Orchestration` | `{#campaign-orchestration-patterns}` |
| `analysis` | `+ Analysis` | `{#analysis-patterns}` |
| `conversational-experience` | `+ Conversational Experience` | `{#conversational-experience-patterns}` |

#### Inspringingsregels

- Categoriekoppen gebruiken twee spaties + `+` (bijvoorbeeld `  + Personalization{#personalization-patterns}` )
- Patroonitems gebruiken vier spaties + `+` (bijvoorbeeld `    + [Pattern Title](path)` )

### &#x200B;2. Overzicht van casepatronen gebruiken
- **Dossier:** `/help/blueprints/use-case-patterns/overview.md`
- **Actie:** voeg een nieuwe rij aan de correcte categorietabel toe
- **Formaat:** `| [{{Pattern Title}}]({{category}}/{{filename}}.md) | {{Primary capability description}} | [!DNL {{Solution1}}], [!DNL {{Solution2}}] |`
- **Categorieën in overzicht:**
   - Publiek bouwen en activeren (lijn ~18)
   - Personalization (lijn ~29)
   - Campagnebeheer &amp; orchestratie (lijn ~40)
   - Analyse (lijn ~52)
   - Gesprekkervaring (lijn ~61)

#### Voorbeeld van rijindeling

```
| [Event-Triggered Messaging](campaign-management-orchestration/event-triggered-messaging.md) | Listen for a real-time behavioral or system event, then deliver a contextual message to the triggering profile | [!DNL Journey Optimizer], [!DNL Real-Time CDP] |
```

## Controlelijst voor validatie

- [ ] Patroonmarkeringsbestand gemaakt in juiste categoriemap
- [ ] De achtergrond bevat titel, beschrijving, oplossing en exl-id
- [ ] TOC.md-item toegevoegd onder juiste categorie
- [ ] Overzicht.md tabelrij toegevoegd onder de juiste categorie
- [ ] Alle zakelijke objectieve koppelingen verwijzen naar bestaande bestanden
- [ ] Bestand gebruikt conventie voor naamgeving van hoofdletters en kleine letters
- [ ] Alle Experience League-koppelingen zijn geldige URL&#39;s
- [ ] Adobe-productnamen maken gebruik van `[!DNL ...]` syntaxis
- [ ] Functieketen gebruikt ` > ` -scheidingsindeling
- [ ] Het patroonbestand bevat alle vereiste secties (zie pattern-template.md)
