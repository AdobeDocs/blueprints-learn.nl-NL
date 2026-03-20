---
name: use-case-icon-generator
description: Produceer pictogramspecificaties en de herinneringen van de beeldgeneratie voor gebruiksgevalpictogrammen in de plaats van de Vergroting van Adobe Experience Platform. Gebruik deze vaardigheid wanneer het creëren van pictogrammen voor nieuwe industrie gebruiksgevallen, wanneer de industrie-gebruik-case-builder vaardigheid een pictogram nodig heeft, of wanneer de gebruiker over het creëren van of het bijwerken van gebruikscapictogrammen vraagt. Hiermee wordt een gedetailleerde vraag over het genereren van afbeeldingen weergegeven die de gebruiker kan gebruiken met Midtrip-, DALL-E-, Adobe Firefly- of vergelijkbare gereedschappen, samen met de juiste bestandsnaam en -plaatsing.
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '875'
ht-degree: 0%

---


# Pictogramgenerator voor hoofdletters/kleine letters gebruiken

Produceer gedetailleerde pictogramspecificaties en AI de herinneringen van de beeldgeneratie voor gebruiksgevalpictogrammen in de bewaarplaats van blauwdrukken.

## Wanneer om deze Vaardigheid te gebruiken

- Een nieuw gebruiksgeval maken waarvoor een pictogram nodig is
- Geroepen door industrie-gebruik-geval-bouwer vaardigheid om een pictogramspecificatie te produceren
- Gebruiker vraagt of het pictogram van een gebruiksgeval moet worden gemaakt, bijgewerkt of vervangen
- De gebruiker wil een partij pictogrammen voor een nieuwe industrie verticaal produceren

## Stap 1: Invoer verzamelen

Verzamel de volgende informatie van de gebruiker of van de roepende vaardigheid:

**Vereist:**
- **het gevalnaam van het Gebruik** - de mens-leesbare naam van het gebruiksgeval (b.v., &quot;Verlaten Kar&quot;, &quot;het Scoreren van het Lood&quot;)
- **Verticale Industrie** — Één van: automobielindustrie, b2b, financiële diensten, gezondheidszorg, verzekering, media-vermaak, kleinhandel, telecommunicatie, reis-gastvrijheid
- **Korte beschrijving** — 1-2 zinnen die beschrijven wat het gebruiksgeval doet

**Facultatief:**
- **Gewenste visuele metafoor of onderwerp** - als de gebruiker een specifiek idee voor heeft wat het pictogram zou moeten tonen

Als vereiste invoer ontbreekt, vraag de gebruiker alvorens te werk te gaan.

## Stap 2: De stijlhandleiding lezen

Lees het bestand `references/icon-style-guide.md` (relatief ten opzichte van de map van deze vaardigheid) om de complete stijlhulplijn te laden, waaronder:

- Technische specificaties
- Richtlijnen voor visuele stijl
- Visuele metafovoorbeelden door de industrie
- Het snelle malplaatje
- De bestaande pictograminventaris

Gebruik de stijlhulplijn voor consistentie met bestaande pictogrammen.

## Stap 3: Genereer de pictogramspecificatie

Alle drie de onderdelen van de pictogramspecificatie produceren:

### A. Bestandsspecificatie

De bestandsnaam en het pad worden afgeleid van de naam en de industrie van het gebruiksgeval:

- **filename:** `icon-{kebab-case-name}.png`
   - Zet de naam van het gebruiksgeval in kebab-case om (kleine letters, afbreekstreepjes voor spaties)
   - Voorbeelden: &#39;Afgewezen winkelwagentje&#39; wordt `icon-abandoned-cart.png` , &#39;Cros-Sell Upsell&#39; wordt `icon-cross-sell-upsell.png`
- **Weg:** `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/`
- **Afmetingen:** 1024 x 1024 pixel
- **Formaat:** PNG, 8 beetje RGB of RGBA
- **de dossiergrootte van het Doel:** 900KB - 1.4MB

### B. Vragen om het genereren van afbeeldingen

Maak een gedetailleerde, gebruiksklare aanwijzing voor gereedschappen voor het genereren van AI-afbeeldingen. De vraag moet:

1. **beschrijf een duidelijke visuele metafoor** - kies één enkele, sterke visuele metafoor die onmiddellijk het concept van het gebruiksgeval meedeelt. Als de gebruiker een voorkeursmetafoor heeft opgegeven, gebruikt u deze. Anders selecteert u er een op basis van de voorbeelden van de stijlhulplijn en de beschrijving van het gebruiksscenario.

2. **specificeer de artistieke stijl** - omvat deze stijlrichtlijnen:
   - Heldere, moderne stijl voor pictogramafbeelding
   - Professioneel ontwerp voor bedrijven
   - Vette vormen en schone lijnen
   - Gefilterde, gerenderde afwerking (niet fotorealistisch)
   - Consistent met een uniform ontwerpsysteem

3. **omvat technische specificaties:**
   - Vierkante indeling, 1024x1024 pixels
   - Enkel gecentreerd onderwerp
   - Achtergrond van effen of subtiele verlopen
   - Hoog contrast tussen onderwerp en achtergrond

4. **afdwingen klein-grootteleesbaarheid:**
   - Geen tekst of lettertype
   - Geen fijne details of ingewikkelde patronen
   - Geen complexe achtergronden of scènes met meerdere elementen
   - Vet silhouet dat duidelijk leesbaar is bij 40 px
   - Sterke vormherkenning, zelfs zonder kleur

5. **Gids het kleurenpalet:**
   - Professionele, bedrijfsgeschikte kleuren
   - Levendig maar geraffineerd (niet neon of oververzadigd)
   - Hoog contrast voor toegankelijkheid
   - Samenhang met andere pictogrammen in de zelfde industrie verticaal

Structuur de vraag als één enkele paragraaf, klaar om in om het even welk hulpmiddel van de beeldgeneratie te kleven.

### C. Referentiesegment catalogus

Genereer het HTML-fragment voor gebruik in de catalogustabel:

```
<img src="assets/use-case-icons/{industry}/icon-{name}.png" alt="{Alt Text}" width="40">
```

Waarbij `{Alt Text}` de door de mens leesbare naam van het gebruiksgeval is.

## Stap 4: Bestaande pictogrammen weergeven in dezelfde branche

Controleer het bestaande gedeelte voor pictograminventarisatie van de stijlhulplijn en geef alle huidige pictogrammen voor dezelfde branche weer. Hierdoor kan de gebruiker:
- Zorg voor visuele consistentie bij het genereren van het nieuwe pictogram
- Dupliceer een pictogram dat al bestaat
- Verwijzen naar bestaande pictogrammen als stijlvoorbeelden

## Stap 5: De uitvoer presenteren

Maak de uitvoer duidelijk op met deze secties:

---

### Pictogramspecificaties: {Use Case Name}

**Industrie:** {Industry}

**Details van het Dossier:**
- Bestandsnaam: `icon-{kebab-case-name}.png`
- Pad: `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/`
- Afmetingen: 1024 x 1024 pixels
- Indeling: PNG (8-bits RGB/RGBA)

**de Herinnering van de Generatie van het Beeld:**

> {De volledige, gedetailleerde vraag — geformatteerd als blockquote zodat is het gemakkelijk te kopiëren)

**Catalogus HTML:**

```html
<img src="assets/use-case-icons/{industry}/icon-{name}.png" alt="{Use Case Name}" width="40">
```

**Bestaande Pictogrammen in {Industry}:**
- {list of existing icon names}

**Volgende Stappen:**
1. Kopieer de bovenstaande prompt voor het genereren van afbeeldingen.
2. Plak het bestand in het voorkeursprogramma voor het genereren van afbeeldingen (Adobe Firefly, Midtrip, DALL-E of vergelijkbare).
3. Genereer de afbeelding en selecteer het beste resultaat.
4. Vergroot of verklein indien nodig het formaat/exporteer het document naar exact 1024 x 1024 pixels.
5. Opslaan als `{filename}` in het hierboven weergegeven pad.
6. Controleer of het pictogram er helder en herkenbaar uitziet bij een weergave van 40 px.
7. Gebruik het HTML-fragment van de catalogus wanneer u dit gebruiksscenario aan de catalogustabel toevoegt.

---

## Richtlijnen

- **produceert nooit het daadwerkelijke beeld** — Deze vaardigheid veroorzaakt de specificatie en slechts herinnering. De gebruiker moet een extern gereedschap voor het genereren van afbeeldingen gebruiken.
- **Één pictogram per gebruiksgeval** - Elk gebruiksgeval krijgt precies één pictogram.
- **Controle voor duplicaten** - als een pictogram met de zelfde of zeer gelijkaardige naam reeds in de inventaris bestaat, waarschuwt de gebruiker.
- **Prioritize leesbaarheid** - wanneer in twijfel tussen gedetailleerde metafoor en eenvoudige, kies altijd de eenvoudigere optie die goed bij 40px leest.
- **ben specifiek in herinneringen** - de Vage herinneringen veroorzaken inconsistente resultaten. Omvat concrete visuele details (bijvoorbeeld &quot;een winkelwagentje met twee kleurrijke dozen erin&quot; in plaats van &quot;een winkelconcept&quot;).
- **vermijd klemmen waar mogelijk** — probeer om verse maar nog onmiddellijk herkenbare visuele metafors te vinden. Een gloeilamp voor elk &#39;slim&#39; gebruik wordt steeds herhaald.
