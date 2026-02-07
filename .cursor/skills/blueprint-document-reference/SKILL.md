---
name: blueprint-document-reference
description: Verwijzing voor het maken en bewerken van documenten met de functie Adobe Digital Experience Bluepprint. Gebruik deze optie wanneer u nieuwe blauwdrukken maakt, pagina's met blauwdruk toevoegt of wanneer de gebruiker vragen stelt over de structuur van de blauwdruk, secties, sjablonen of wanneer wordt verwezen naar de Adobe Experience League.
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 1%

---


# Referentie blauwdruk document

Gebruik deze vaardigheid wanneer het creëren van of het uitgeven van blauwdrukdocumenten in deze bewaarplaats. De blauwdrukken zijn herhaalbare implementaties die gevestigde bedrijfsproblemen behandelen en architectuurdiagrammen, technische overwegingen, en verbindingen aan de documentatie van de Liga van de Ervaring van Adobe omvatten.

## Wanneer moet u toepassen

- Een nieuw document of een nieuwe overzichtspagina voor een blauwdruk maken
- Secties toevoegen of herstructureren in een bestaande blauwdruk
- Documentatie van de Adobe Experience League koppelen of doorgeven
- Nieuwe inhoud uitlijnen met conventies voor blauwdrukken (voorzijde, koppen, diagrammen)

## Snelle naslag

1. **doel van het Document**: De blauwdrukken verstrekken systeem en gegevensstroomarchitectuur om te tonen hoe Adobe Experience Platform en de toepassingen worden geïntegreerd. Ze zijn visueel en technisch, niet op de markt.
2. **Secties**: Gebruik de standaardsecties van het malplaatje; weglaat slechts wanneer niet van toepassing (zie [ reference.md ](reference.md)).
3. **Experience League**: verkies het verbinden met Experience League voor productdocumenten, APIs, gidsen, en leerprogramma&#39;s. Gebruik volledige URLs; zie [ reference.md ](reference.md) voor patronen URL en het formatteren.
4. **Repo structuur**: De levende blauwdrukken onder `help/blueprints/`. `help/blueprints/TOC.md` bijwerken bij het toevoegen of verplaatsen van blauwdrukpagina&#39;s.

## Documentsjabloon

Elke blauwdrukpagina moet deze structuur volgen. Alleen de desbetreffende secties opnemen.

```markdown
---
title: [Short descriptive title]
description: "[One sentence: what this blueprint shows and why it matters.]"
solution: [Product name, e.g. Real-Time Customer Data Platform, Journey Optimizer]
exl-id: [UUID - leave blank if new, this will be auto-generated as part of the Experience League publishing flow]
---
# [H1 - same as title or expanded]

[1–3 paragraphs: what the blueprint covers, key capabilities, and who it’s for.]

## Applications

* [Product 1]
* [Product 2]

## Use cases

* [Use case 1]
* [Use case 2]

## Prerequisites

[Bullets or short paragraphs: required products, config, or setup.]

## Architecture Diagram

<img src="[path to SVG/image]" alt="[Descriptive alt]" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />

## Guardrails

[Link to Experience League guardrails and any blueprint-specific limits.]

## Implementation patterns

[Optional: named patterns with bullets.]

## Implementation steps

1. [Step with link to Experience League where relevant]
2. ...

## Implementation considerations

[Optional: identity, performance, security, etc.]

## Related documentation

[Grouped links to Experience League: product docs, APIs, tutorials.]
```

Voor overzicht of hubpagina&#39;s, gebruik een kortere structuur: intro, gebruikscenario&#39;s (of lusjes), architectuurbeeld, scenario/patroonlijst, eerste vereisten, gidsen, verwante documentatie. Zie bestaande overzichten in `help/blueprints/` voor voorbeelden.

## Frontkey

| Veld | Vereist | Notities |
|-------|----------|--------|
| `title` | Ja | Kort; gebruik `[!DNL Product Name]` voor productnamen per Adobe-stijl |
| `description` | Ja | Eén zin; wordt gebruikt in zoekopdrachten en kaarten |
| `solution` | Ja | Primair product (bijvoorbeeld Real-Time Customer Data Platform, Journey Optimizer) |
| `exl-id` | Ja | UUID; leeg laten voor nieuwe pagina&#39;s |
| `doc-type` | Voor overzichten | `overview-page` gebruiken voor hoofdpagina&#39;s met een blauwdrukoverzicht |
| `kt` | Optioneel | Artikel-id van kennisbank indien gekoppeld |

## Verwijzen naar Adobe Experience League

- **wanneer om** te verbinden: Verbinding met Experience League voor productdocumentatie, API verwijzingen, gidsen, leerprogramma&#39;s, en configuratiestappen. Dupliceer lange procedures niet; vat samen en verbind.
- **formaat URL**: Gebruik volledige URLs. Voorkeur `https://experienceleague.adobe.com/docs/...` of `https://experienceleague.adobe.com/en/docs/...` . Voor ontwikkelaarsdocumenten is `https://developer.adobe.com/...` ook geldig.
- **Tekst van de Verbinding**: De beschrijvende tekst van het gebruik (b.v. [ leidt schema&#39;s ](url)&quot;niet &quot;klik hier&quot;). Gebruik, indien van toepassing, `[!DNL Product Name]` voor productnamen in koppelingstekst.
- **Verwante documentatiesectie**: Eind blauwdrukken met een &quot;Verwante documentatie&quot;sectie die verbindingen groeperen door categorie (b.v. de configuraties van de Bestemming, de documentatie van SDK, Profiel en segmentatie, Leerprogramma&#39;s).

Voor gedetailleerde patronen URL, verbinding groeperen, en voorbeelden, zie [ reference.md ](reference.md).

## Controlelijst voor verzending

- [ ] De voorgrond heeft `title` , `description` , `solution` , `exl-id`
- [ ] H1 komt overeen met de titel of breidt de titel op de juiste wijze uit
- [ ] Architectuurdiagram aanwezig en alt-tekstbeschrijvend
- [ ] Implementatiestappen zijn gekoppeld aan Experience League waar de procedures actief zijn
- [ ] Sectie met instructies verwijst naar officiële documenten van Experience League guardrail
- [ ] Sectie Verwante documentatie bevat relevante Experience League-koppelingen
- [ ] Nieuwe of verplaatste pagina&#39;s worden weergegeven in `help/blueprints/TOC.md`

## Aanvullende resources

- Volledige malplaatje en sectienota&#39;s: [ reference.md ](reference.md)
- Bestaande blauwdrukken: `help/blueprints/` (bijvoorbeeld `audience-activation/real-time-lookup.md` , `customer-journeys/journey-optimizer/journey-optimizer-overview.md` )
- Inhoudsopgave en navigatie: `help/blueprints/TOC.md`
