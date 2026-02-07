---
source-git-commit: dfa21942ecf2a1db06df6f6cc945f5572811ca93
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 1%

---
# Referentie blauwdruk document — Gedetailleerde gids

## Documenttypen

| Type | Doel | Locatie/voorbeeld |
|------|---------|--------------------|
| **Overzicht / hub** | Introduceert een product of een gebied; verbindingen aan scenario blauwdrukken | bijv. `overview.md`, `journey-optimizer-overview.md` |
| **blauwdruk van het Scenario** | Hoofdlettergebruik voor eenmalig gebruik: architectuur, stappen, instructies | bijv. `real-time-lookup.md`, `journey-optimizer-journeys.md` |
| **TOC** | Navigatie; niet gebruiken als inhoudssjabloon | `help/blueprints/TOC.md` |

&#x200B;---

## Volledige sectieverwijzing

### Benaming en beschrijving (voormaterie)

- **titel**: Kort, specifiek. Gebruik `[!DNL Product Name]` voor productnamen (bijvoorbeeld `[!DNL Journey Optimizer]` ).
- **beschrijving**: Één zin. Beschrijf wat de blauwdruk toont en het resultaat (bijv. &quot;Toegang van het Profiel van de Klant in real time bij de rand voor web en mobiele verpersoonlijking.&quot;).

### Hoofdsecties

| Sectie | Wanneer moet u opnemen | Richtlijnen voor inhoud |
|---------|-----------------|-------------------|
| **Toepassingen** | Altijd voor concepten | Lijst met opsommingstekens van betrokken Adobe-producten/oplossingen (bijvoorbeeld Real-time Customer Data Platform, Data Collection). |
| **Gevallen van het Gebruik** | Altijd | Bullet list van zaken/technische gebruiksgevallen deze blauwdruk steunt. |
| **Eerste vereisten** | Wanneer instellen vereist is | Producten, subdomeinen, SDKs, config die op zijn plaats moeten zijn. Koppeling naar Experience League voor instellingenstappen. |
| **Diagram van de Architectuur** | Altijd | Eén primair diagram (bij voorkeur SVG). Gebruik consistente opmaak: `style="width:90%; border:1px solid #4a4a4a" class="modal-image"` . Geef betekenisvolle `alt` tekst op. |
| **Guardrails** | Altijd wanneer het product draden heeft | Koppeling naar officiële Experience League guardrail-pagina&#39;s. Voeg blauwdrukspecifieke grenzen (bijvoorbeeld TTL, tariefgrenzen) als kogels toe. |
| **de patronen van de Implementatie** | Wanneer er meerdere benaderingen bestaan | Geef elk patroon een naam (bijv. &quot;Patroon 1: Publiek lidmaatschap-gebaseerd met Web SDK&quot;); gebruik opsommingstekens voor het gebruik en de afweging. |
| **de stappen van de Implementatie** | Voor scenario-blauwdrukken met een gedefinieerd pad | Genummerde lijst. Elke stap: actie + link naar Experience League waar de procedure loopt. Kopieer de volledige procedures niet. |
| **overwegingen van de Implementatie** | Als er belangrijke waarschuwingen zijn | Subsecties (bijvoorbeeld identiteitsoverwegingen, op kenmerken gebaseerde personalisatie). Opsommingstekens of korte alinea&#39;s; link naar diepte. |
| **Verwante documentatie** | Altijd | Gegroepeerde koppelingen naar Experience League (en optioneel developer.adobe.com). Zie &quot;Experience League link groups&quot; hieronder. |

### Overzicht-/hubpagina&#39;s

- Begin met 1-2 alinea&#39;s op het product/gebied en wat de blauwdrukken bedekken.
- **gevallen van het Gebruik**: Kan `>[!BEGINTABS]` / `>[!TAB ...]` / `>[!ENDTABS]` voor veelvoudige categorieën gebruiken.
- **Architectuur**: Één hoofddiagram.
- **Scenario&#39;s van de Vervaging** of **de Patronen van de Integratie**: Lijst met scenario naam, korte beschrijving, en verbinding aan de scenario blauwdruk.
- **Eerste vereisten**, **Grafieken**, **Verwante documentatie**: Gelijk zoals hierboven; houd beknopt.

&#x200B;---

## Adobe Experience League — Agent Directions

### Wanneer verwijst u naar Experience League

- **documentatie van het Product**: Hoe een product werkt, stromen UI, concepten.
- **APIs**: Eindpunten, parameters, voorbeelden (Experience Platform, Edge, enz.).
- **Guardrails**: Officiële guardrailpagina&#39;s voor het product of de dienst.
- **Leerprogramma&#39;s**: Step-by-step gidsen (b.v. creeer schema&#39;s, activeer bestemmingen).
- **Configuratie**: De stromen van gegevens, bestemmingen, fusiebeleid, identiteiten, enz.

Plak lange procedures van Experience League niet in de blauwdruk. Overzicht en koppeling.

### URL-patronen

| Contenttype | Basis-URL | Voorbeeldpad |
|--------------|----------|--------------|
| Experience Platform-documenten | `https://experienceleague.adobe.com/docs/experience-platform/` | `.../profile/home.html`, `.../destinations/catalog/...` |
| Experience League (en) | `https://experienceleague.adobe.com/nl/docs/` | Dezelfde structuur als hierboven met `/en/` . |
| Journey Optimizer | `https://experienceleague.adobe.com/docs/journey-optimizer/` | `.../using/get-started/guardrails.html` |
| Web SDK | `https://experienceleague.adobe.com/docs/experience-platform/web-sdk/` | `.../home.html`, `.../commands/command-responses.html` |
| Edge Network Server-API | `https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/` | `.../overview.html`, `.../guardrails.html` |
| Mobiele SDK | `https://developer.adobe.com/client-sdks/` | `.../home/`, `.../edge/adobe-journey-optimizer-decisioning/` |
| Tags | `https://experienceleague.adobe.com/docs/experience-platform/tags/` | `.../home.html` |
| Platformzelfstudies | `https://experienceleague.adobe.com/docs/platform-learn/tutorials/` | `.../profiles/create-merge-policies.html` |

Gebruik het canonieke pad dat overeenkomt met de huidige Experience League-site (geef de voorkeur `/en/docs/` als het Engelse pad bekend is).

### Opmaak van koppeling in markering

- **Beschrijvende verbindingstekst**: `[Create schemas](https://experienceleague.adobe.com/nl...)` &quot;klik hier niet&quot;.
- **de namen van het Product in tekst**: Gebruik `[!DNL Product Name]` per stijl van Adobe (b.v. `[!DNL Real-time Customer Profile]`).
- **Externe verbindingen**: voeg `{target="_blank"}` slechts toe wanneer het malplaatje of de pijpleiding het vereist (controleer bestaande blauwdrukken in repo).

### Verwante documentatie — voorgestelde groepen

Gebruik deze groepen wanneer ze van toepassing zijn:

1. **configuraties van de Bestemming** (voor activering/de blauwdrukken van de randverpersoonlijking)
2. **de documentatie van SDK** (Web SDK, Mobiele SDK, de Server API van Edge Network, Markeringen)
3. **Profiel en segmentatie** (Real-time het Profiel van de Klant, verenigt beleid, segmentatie)
4. **Zelfstudies** (platform-leren of product-specifieke geleidelijke gidsen)
5. **documentatie van het Product** (het huis van het belangrijkste productdocument of zeer belangrijke subsecties)
6. **Guardrails** (als niet reeds in sectie Guardrails)

Voorbeeld:

```markdown
## Related documentation

### Destination configurations
* [Custom Personalization Connection](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/personalization/custom-personalization)
* [Activate audiences to edge personalization destinations](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations)

### SDK documentation
* [Experience Platform Web SDK](https://experienceleague.adobe.com/docs/experience-platform/web-sdk/home.html?lang=nl-NL)
* [Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=nl-NL)

### Profile and segmentation
* [Real-time Customer Profile](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=nl-NL)
* [Profile Guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=nl-NL)
```

&#x200B;---

## Repo en inhoudsopgave

- **de inhoudspad van de Vervaging**: `help/blueprints/` (met subfolders door gebied, bijvoorbeeld `audience-activation/`, `customer-journeys/journey-optimizer/`).
- **Assets**: Cobepaal de plaats met de blauwdruk (b.v. `assets/`, `images/`) of in een gedeelde omslag (b.v. `experience-platform/assets/`).
- **TOC**: geef `help/blueprints/TOC.md` uit wanneer het toevoegen van, het anders noemen van, of het bewegen van blauwdrukpagina&#39;s. De voorgrond (`user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`) en de hiërarchie `+` behouden.

&#x200B;---

## Voorbeelden van verwijzingen in dit antwoord

- **de blauwdruk van het Scenario (lange vorm)**: `help/blueprints/audience-activation/real-time-lookup.md`
- **Overzicht/hub met lusjes en lijsten**: `help/blueprints/customer-journeys/journey-optimizer/journey-optimizer-overview.md`
- **Guardrails-geconcentreerd**: `help/blueprints/experience-platform/guardrails.md`
- **Navigatie**: `help/blueprints/TOC.md`, `help/blueprints/overview.md`

Gebruik deze patronen als patronen voor de sectieorde, de voorzijde, diagramplaatsing, en het verbindingsgebruik van Experience League.
