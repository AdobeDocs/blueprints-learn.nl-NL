---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---
# Rijsjabloon hoofdletter gebruiken

## Rijopmaak

Voor elke rij in de catalogus met use-case-catalogi wordt de exacte notatie gebruikt:

```
| <img src="assets/use-case-icons/{industry}/icon-{kebab-name}.png" alt="{Alt Text}" width="40"> | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

### Rij zonder pictogram (gebruiken wanneer pictogram nog niet beschikbaar is)

```
| | [{Use Case Title}]({industry}/{industry}-overview.md#{heading-anchor}) | {One-sentence description} | [!BADGE {Maturity}]{type={Type}} | [{Pattern Name}](/help/blueprints/use-case-patterns/{category}/{pattern-file}.md) |
```

## Veldverwijzing

| Veld | Indeling | Voorbeeld |
| --- | --- | --- |
| industrie | mapnaam kebab-hoofdletters | detailhandel, financiële diensten, reisgastvrijheid |
| kebab-naam | hoofdlettergebruik voor pictogram | in de steek gelaten karretjes, het voeden van lood |
| Alt-tekst | Alles Beginhoofdletter, kort | Verlaten auto&#39;s, hoofdverpleegkundigen |
| kopanker | hoofdlettergebruik van de ##-kop in overzicht | verlaten-kar-e-mail-terugwinning |
| Looptijd + type | Badge-syntaxis | `[!BADGE Foundational]{type=Neutral}`, `[!BADGE Emerging]{type=Informative}`, `[!BADGE Advanced]{type=Caution}` |

## Markeringen op het tabblad Industrie in de catalogus

Het catalogusbestand gebruikt deze tabstructuur:

- `>[!TAB Retail]`
- `>[!TAB Automotive]`
- `>[!TAB Financial Services]`
- `>[!TAB Healthcare]`
- `>[!TAB Insurance]`
- `>[!TAB Media & Entertainment]`
- `>[!TAB Telecommunications]`
- `>[!TAB Travel & Hospitality]`
- `>[!TAB B2B]`

## Orderen binnen tabbladen

Rijen worden geordend op het looptijdniveau:

1. **Begonnen** rijen eerst (type=Neutraal)
2. **Opkomende** rijen tweede (type=Informatief)
3. **Geavanceerde** rijen laatste (type=Caution)

Voeg binnen hetzelfde looptijdniveau nieuwe rijen toe aan het einde van die groep.
