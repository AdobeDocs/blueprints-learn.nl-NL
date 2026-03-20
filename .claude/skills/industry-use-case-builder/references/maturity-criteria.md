---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---
# Criteria voor beoordeling van de aflooptijden gebruiken

## Zuiverheidsniveaus

### Foundary

**Badge:** `[!BADGE Foundational]{type=Neutral}`

Een gebruiksgeval is **Begonnen** wanneer het:

- Kaarten aan een enig-stap of gebeurtenis-teweeggebracht patroon (gebeurtenis-teweeggebrachte Overseinen, de Actief van het Bericht van de Partij Uitgaande
- Bevat eenvoudige gegevensvereisten (type enkele gebeurtenis, kenmerken van standaardprofielen)
- Vereist minimale of geen AI/ML mogelijkheden
- Gebruikt standaard kanaallevering (e-mail, SMS, push) zonder complexe orchestratie
- Heeft gevestigde implementatiepatronen met duidelijke best practices
- Vereist minder systeemintegratie (typisch 1-2 gegevensbronnen)

**Typische patronen:** gebeurtenis-teweeggebrachte Overseinen, de Actie van het Bericht van de Partij Uitgaande

**Voorbeelden:** Verlaten kartterugwinning, benoemingsherinneringen, de dienstberichten, prijsdalingsalarm, rekeningsherinneringen

### Opkomend

**Badge:** `[!BADGE Emerging]{type=Informative}`

Een gebruiksgeval is **Ontkomende** wanneer het:

- Kaarten aan een multi-step of personalisatiepatroon (Multi-Step Orchestrated Journey, Known-Visitor Personalization, Gedragsaanbeveling, Anoniem Visitor Personalization)
- Vereist verzameling en analyse van gedragsgegevens
- Gebruikt aanbevelingen of bekende resolutie van bezoekersprofiel
- Hierbij gaat het om multitouch-opvoedingssequenties met vertakkende logica
- Heeft matige integratiecomplexiteit (2-4 gegevensbronnen)
- Mogelijk moet het publiek worden geactiveerd of moet het doelsegment op segment worden gebaseerd

**Typische patronen:** multi-Step Orchestrated Reis, het bekende-Bezoeker Web/App Personalization, de Aanbeveling van het Gedrag, Anoniem het Web Personalization van de Bezoeker, B2B Audience Activation

**Voorbeelden:** Welkome reeksen, medicatie therapietacampagnes, gepersonaliseerde rekeningsdashboards, lood scoring, inhoudaanbevelingen

### Geavanceerd

**Badge:** `[!BADGE Advanced]{type=Caution}`

Een gebruiksgeval is **Geavanceerd** wanneer het:

- Kaarten aan een beslissings- of kanaalorkestpatroon (Cross-Channel Journey with Decisioning, Offer Decisioning)
- Vereist voorspellingen op basis van AI of scoring van de buigzaamheid
- Gebruikt gelijktijdig gecentraliseerde beslissingslogica over veelvoudige kanalen
- Omvat complexe orchestratie met real-time besluitvorming op meerdere reispunten
- Heeft hoge integratieingewikkeldheid (4+ gegevensbronnen, gegevensvoer in real time)
- Vereist geavanceerde bedrijfsregels, prioritair beheer en frequentiebeheer

**Typische patronen:** Reis van het Kanaal met Beslissing, Offer Decisioning

**Voorbeelden:** Preventie van de Kern met AI het scoren, levensstadium productaanbevelingen, dwars-verkoop optimalisering, loyaliteitsprogramma, exclusieve aanbiedingen van VIP

## Beoordelingsworkflow

1. Identificeer welk gebruikspatroon de gebruikscase toewijst aan
2. Controleer bovenstaande lijst &quot;Typische patronen&quot; voor een snelle overeenkomst
3. Als het patroon niet duidelijk op rijpheid wijst, evalueer de gegevensingewikkeldheid, AI/ML vereisten, en integratiewerkingsgebied
4. Presenteer de beoordeling aan de gebruiker met het redeneren: &quot;Gebaseerd op de patroonafbeelding ({pattern}) en {key factors}, zou ik dit als {level} wegens {reasoning} classificeren.&quot;
5. Laat de gebruiker bevestigen of met voeten treden alvorens te werk te gaan
