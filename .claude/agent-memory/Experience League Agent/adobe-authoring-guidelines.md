---
name: Adobe Experience League Authoring Guidelines
description: Volledige verwijzing naar de ontwerpregels voor opmaakcodes van de Adobe Experience League, die in maart 2026 zijn uitgekomen in de officiële handleiding voor het schrijven van scripts.
type: reference
source-git-commit: 61c2666b4546222423e85e52270b436c59d846a3
workflow-type: tm+mt
source-wordcount: '1664'
ht-degree: 0%

---


# Ontwerprichtlijnen voor Adobe Experience League

Source: https://experienceleague.adobe.com/en/docs/authoring-guide/using/home
Gekwurd: 2026-03-15

---

## &#x200B;1. METAGEGEVENS/VOORWERP

### Vereiste velden
| Veld | Vereiste | Regels |
|---|---|---|
| `title` | Vereist | Max. 60 tekens (Engels). Alles in titel. Geen productnamen tenzij dit voor de duidelijkheid nodig is. Systeem voegt &quot; | ProductName&quot; automatisch. Plaats aanhalingstekens tussen aanhalingstekens als deze dubbele punten of vierkante haken bevat. |
| `description` | Vereist | max. 150-160 tekens Kan niet leeg/null zijn. Concepten beginnen met &quot;Meer informatie over..&quot; Taken beginnen met &#39;Leren hoe..&#39; of dwingende werkwoorden. |

### Optionele maar veelgebruikte velden
| Veld | Geldige waarden | Notities |
|---|---|---|
| `feature` | Moet overeenkomen met de YAML-waarden van de functie; hoofdlettergebruik voor titels met spaties (bijvoorbeeld &quot;Inhoudsfragment&quot;) | 1-2 per artikel; vertoningen in Onderwerpen |
| `feature-set` | Moet valideren tegen functie YAML | Bovenliggende toepassing van functie |
| `role` | Gebruiker, Ontwikkelaar, Leader, Admin, Architect, Data Architect, Data Engineer | Hoofdlettergevoelig; wordt weergegeven als &quot;Gemaakt voor&quot; |
| `level` | Beginnend, middelmatig, ervaren | Wordt standaard ingesteld op Beginner als deze niet is opgegeven |
| `solution` | Moet overeenkomen met oplossing YAML (bijvoorbeeld &quot;Campagne, Campaign Standard v7&quot;) | Meerdere waarden toegestaan; wordt gebruikt voor zoekfiltering |
| `topic` | Moet onderwerp YAML aanpassen; titelgeval met ruimten | Voor cross-product filtering (bijvoorbeeld &quot;Integrations&quot;) |
| `type` | Documentatie, zelfstudie, probleemoplossing | Repo-niveau; standaardinstellingen voor documentatie |
| `short-description` | Eén zin, maximaal 20 woorden | Voor ExL-bestemmingspagina&#39;s wanneer de beschrijving te lang is |
| `badgePremium` | `label="Premium" type="Positive" url="..."` | Badge op paginaniveau |
| `mini-toc-levels` | 1-6 (standaard 2) | Hiermee regelt u de weergavediepte van kop rechts-nav |
| `hidefromtoc` | true/false | Uitsluiten van linkernav, maar URL blijft toegankelijk |

### Plaatsing metagegevens
- Artikelniveau: bovenkant van markeringsbestand als YAML-voorgrond
- Inhoudsopgave-niveau: in bestand TOC.md
- Repo-niveau: in bestand metadata.md

### Regels voor sleutelopmaak
- Rondom aanhalingstekens geplaatste waarden tussen komma&#39;s of vierkante haken plaatsen
- Meerdere waarden, gescheiden door komma&#39;s
- Hoofdlettergevoelige overeenkomsten met YAML-definities
- Waarden van lege of lege tags veroorzaken validatiefout

### Verouderde velden
seo-title, seo-description, publiek, moeilijkheid, uuid (uit migratietijdperk)

---

## &#x200B;2. VERKEERDE SYNTAXIS (ADOBE-FLAVORED)

### Tekstopmaak
- Vet: `**text**`
- Cursief: `*text*`
- Vet + cursief: `***text***`
- Speciale tekens voor Escape: gebruik backslash `\` vóór `# { } [ ] * + - . !`
- HTML-entiteiten: `&lt;` `&gt;` `&amp;` `&mdash;` `&ndash;`

### Koppen
- ATX-stijl gebruiken (`#` alleen syntaxis, nooit onderstreping/setext-stijl)
- Eén H1 per document (meestal de paginatitel die overeenkomt met metagegevens `title`)
- Alle volgende koppen H2 (`##`) of lager
- Lege regels vereist voor en na de koppen (met uitzondering van de allereerste kop)
- Max. 69 tekens (Engels) / 120 tekens (gelokaliseerd)
- Max ~5 woorden bij voorkeur
- Als in een zin voor alle koppen (alleen het eerste woord en de juiste cijfers in hoofdletters)
- ALLEEN titelhoofdletters/kleine letters voor het metagegevensveld `title`
- Geen eindleestekens (vraagtekens toegestaan voor koppen van veelgestelde vragen)
- Aangepaste anker-id&#39;s: `## Title {#custom-id}` — gebruik afbreekstreepjes en geen punten
- Geen dubbele koptekstanker-id&#39;s in een document
- Gebruik geen gereserveerde ankernamen: zoeken, resultaten, facetten, paginering, sorteren, query, zoekvak, inhoud, kop-, voettekst, hoofd, navigatie, zijbalk, pagina, container, wrapper
- Volg elke kop met ten minste één alinea met tekst (plaats lijsten/tabellen niet direct na een kop)
- Concept-koppen: zelfstandigen/zelfstandigen
- Taakkoppen: dwingende werkwoorden (NOT gerondes — &quot;Een segment maken&quot; niet &quot;Een segment maken&quot;)
- Parallelle structuur tussen kopniveaus

### Lijsten
- Opsommingsteken (ongeordend): `*`, `-` of `+` — consistent gebruiken in een document
- Geordend: `1.` voor elk item (automatische nummers)
- Lege regels voor en na lijsten
- Geneste genummerde items laten inspringen 3 spaties; geneste opsommingstekens 2 spaties
- Stippelleestekens: puntkomma&#39;s/komma&#39;s/conjuncties aan het einde weglaten; alleen punten toevoegen voor volledige zinnen
- Voeg geen punten toe als alle punten ≤ 3 woorden zijn of etiketten UI/rubrieken zijn

### Koppelingen
- Extern: `[text](https://url.com)`
- Relatief (zelfde niveau): `[text](file.md)`
- Basis relatief: `[text](/help/path/file.md)` — moet beginnen met `/`
- Diepe koppelingen (dezelfde pagina): `[text](#heading-anchor)`
- Diepe koppelingen tussen documenten: `[text](file.md#heading-id)`
- Nieuwe tab forceren: `[text](url){target="_blank"}`
- Zon-URL&#39;s: omloop tussen punthaken `<https://example.com>` om klikbaar te maken
- Referentiekoppelingen: alleen absolute koppelingen werken voor koppelingen in verwijzingsstijl
- Hetzelfde bestand niet opnemen op meerdere locaties in de inhoudsopgave via relatieve koppelingen
- Windows-gebruikers: backslashes omzetten in slashes in paden

### Afbeeldingen
- Eenvoudig: `![alt text](image.png "hover tooltip")`
- Formaat wijzigen: `{width="300"}`
- Uitlijnen: `{align="center"}` of `{align="right"}`
- Zoombaar: `{zoomable="yes"}` of `{modal="regular"}`
- Max. bestandsgrootte: 100 MB (aanbevolen minder dan 5 MB)
- Voor alle afbeeldingen is alternatieve tekst vereist (voor SEO en toegankelijkheid)
- Namen van afbeeldingsbestanden: kleine letters met afbreekstreepjes
- Afbeeldingen opslaan in een toegewezen map met middelen

### Codeblokken
- Inline: backticks `` `code` ``
- Gebruiken voor: bestandsnamen, URL&#39;s, door de gebruiker gedefinieerde termen, opdrachten
- Afgezonderde codeblokken: drie achtergronden met taalid

  ```
  ```javascript
  code here
  ```

  ```
  
  
- Opties: `{line-numbers="true"}`, `{start-line="7"}`, `{highlight="11-13, 16"}`
- Neem altijd een taal-id op in codeblokken met een omheining

### Tabellen
- Voor scheidingsrij zijn ten minste 3 afbreekstreepjes per kolom vereist: `|---|---|---|`
- Uitlijning: links `|---|`, midden `|:---:|`, rechts `|---:|`
- Letterlijke Escape-pijpen: `\|` of gebruik `&vert;`
- HTML-tabellen toegestaan; gebruik `<table style="table-layout:auto">` of `table-layout:fixed`
- HTML-tabeluitlijning: `<td align="left|center|right">`
- Vermijd de syntaxis van markeringen in HTML-tabellen (`[!NOTE]` werkt bijvoorbeeld niet in HTML-tabellen)
- Randen verwijderen: `<tr style="border: 0;">`
- Optie voor lay-out tabel met opmaak weghalen: `{style="table-layout:auto"}` toevoegen na tabel met lege regels
- Vermijd zeer brede/hoge tabellen vanwege problemen met de zichtbaarheid van de horizontale schuifbalk

---

## &#x200B;3. SPECIALE ADOBE SYNTAXISEXTENSIES

### Bijschriften/waarschuwingen

```
>[!NOTE]
>
>Text here.

>[!TIP]
>
>Text here.

>[!IMPORTANT]
>
>Text here.

>[!WARNING]
>
>Text here.

>[!CAUTION]
>
>Text here.

>[!ADMIN]
>[!AVAILABILITY]
>[!PREREQUISITES]
>[!INFO]
>[!ERROR]
>[!SUCCESS]
```
- KRITIEK: geen ruimte tussen `>` en `[!` — gebruik `>[!NOTE]` NOT `> [!NOTE]`
- Lege regel toevoegen tussen `>[!NOTE]` en de tekstregel van de hoofdtekst

### Tabs

```
>[!BEGINTABS]

>[!TAB iOS]
Content here

>[!TAB Android]
Content here

>[!ENDTABS]
```

### Inklapbare secties (accordeons)

```
+++Click to expand
Content inside
+++
```
Opmerking: geneste inklapbare secties worden NIET ondersteund.

### Schaduwvakken

```
>[!BEGINSHADEBOX "Optional Title"]
Content here
>[!ENDSHADEBOX]
```

### Video&#39;s

```
>[!VIDEO](https://video.tv.adobe.com/v/ID/?quality=12&learn=on)
```
Voeg `{transcript=true}` toe voor transcripties.

### Meer als dit

```
>[!MORELIKETHIS]
>* [Article 1](url)
>* [Article 2](url)
```

### Contextafhankelijke Help

```
>[!CONTEXTUALHELP]
>id="..."
>title="..."
>abstract="..."
>additional-url="..."
```

### Badges (inline)

```
[!BADGE Label]{type=Informative url="https://example.com" tooltip="text"}
```
Typen: `Informative` (blauw), `Positive` (groen), `Negative` (rood), `Neutral` (grijs), `Caution` (geel)

### Tekstmarkering (voorvertoning)

```html
<span class="preview">highlighted text</span>
```

### Inclusief en Fragmenten
- Inclusief volledig bestand: `{{$include /help/_includes/legal-blurb.md}}`
- Fragment (geen koppen): `{{snippet-id}}`
- Herbruikbare bestanden opslaan in de map `help > _includes/`
- Fragmenten opgeslagen in `help > _includes/snippets.md`
- Inclusief kan koppen bevatten; fragmenten KUNNEN NIET
- Werkt alleen binnen dezelfde repository (niet cross-repo)
- Escape `{{` - of `}}` -tekens in bestanden zonder verwijzing

### DNL-tag (Niet lokaliseren)
- `[!DNL ProductName]` — Hiermee worden product-/merknamen van een onmiddellijke verpakking die niet mogen worden vertaald
- Gebruiken voor eerste of opvallende vermelding binnen een pagina

### UICONTROL-tag
- `[!UICONTROL Button Label]` — hiermee plaatst u tekst in een interface-element (knoppen, menu&#39;s, veldnamen)
- Zorgt ervoor dat UI-tekenreeksen van productdatabases worden gehaald in plaats van automatische vertaling
- Geen apostroffen, aanhalingstekens of leestekens binnen UICONTROL-tags
- Vette opmaak gebruiken voor UI-elementen waarnaar in stappen wordt verwezen

### Niet-ondersteunde functies
- Taaklijsten (selectievakjes)
- Emoji
- Horizontale lijnen
- Geneste inklapbare secties

---

## &#x200B;4. BESTANDSNAAM EN MAPSTRUCTUUR

### Naamgevingsregels voor bestanden
- Namen van kleine bestanden met alleen afbreekstreepjes
- Geen hoofdletters, onderstrepingstekens, punten of spaties
- Beschrijvende, SEO-vriendelijke namen (bijvoorbeeld `calculated-metric-overview.md` niet `cmo.md` )
- Nummers in bestandsnamen vermijden; beschrijvende woorden gebruiken
- Gebruik geen gereserveerde/conflicterende namen: `metadata.md`, `search.md`
- Voor het wijzigen van de naam van live bestanden is omleidingsbeheer vereist (URL-wijzigingen)

### Mapstructuur
- Directory-/mapnamen hebben GEEN invloed op URL&#39;s (alleen repo-namen en bestandsnamen zijn van invloed op URL&#39;s)
- TOC.md bestuurt de navigatiehiërarchie, niet de plaats van de omslag van de Git
- Afbeeldingen/middelen opslaan in een toegewezen map met middelen
- Herbruikbare include-bestanden die zijn opgeslagen in `help/_includes/`
- Fragmenten opgeslagen in `help/_includes/snippets.md`

### TOC.md-regels
- Elk artikel moet in TOC.md worden vermeld om op Experience League terug te geven
- H1-indeling: `# Guide Title {#anchor-id}` — anker genereert basis-URL-pad
- Sectiekoppen moeten anker-id&#39;s hebben: `+ Section Name {#section-id}`
- Sectiekoppen (bovenliggende items) kunnen zelf geen koppelingen zijn
- Artikelkoppelingen: `+ [Title](path/file.md)`
- Als u sectieanker-id&#39;s wijzigt, worden alle geneste artikel-URL&#39;s gewijzigd (omleidingen zijn vereist)
- Gebruik overal dezelfde stijl voor opsommingstekens ( `+` , `*` of `-` )
- Metagegevens van inhoudsopgave: `user-guide-description` (optioneel) `breadcrumb-title`
- `mini-toc-levels`: besturingselementen voor de weergave van kop rechts-nav (1-6, standaard 2)

---

## &#x200B;5. INHOUDSKWALITEIT EN BEWERKINGSNORMEN

### Stem en toon
- De actieve stem verkiest boven passief
- Toekomstige spanningen presenteren
- Tweede persoon (&quot;u&quot;) voor instructies
- Zinnen onder 35 woorden
- Sterke, nauwkeurige werkwoorden — vermijd zwakke werkwoorden (&quot;erg&quot;, &quot;extreem&quot;)

### Stappen/procedures
- Elke stap bestaat uit één enkele, beknopte opdracht (één zin)
- Extra informatie vindt u op de volgende regel (inspringt u onder de stap)
- Begin elke stap met een noodzakelijk werkwoord
- Beperk de procedures tot ongeveer 7 stappen (max ~10 voordat u de subtaken start)
- conceptuele informatie plaatsen VOOR stappen
- Screenshots plaatsen NA de relevante stap
- Pagina-/tabnamen herhalen voor de leesrichting
- Vette UICONTROL-opmaak voor UI-elementen in stappen

### Interfaceterminologie
- **Open/Sluiten**: toepassingen en programma&#39;s
- **ga naar**: menu&#39;s, lusjes, of plaatsen UI
- **Uitgezocht**: tekst, cellen, of opties van lijsten
- **klik**: muisacties (vermijd specificerend controletype tenzij essentieel)
- **Dropdown menu** (niet &quot;dropdown lijst&quot;)

### Productnamen
- Geen productnaam aan titels/koppen toevoegen, tenzij dit voor de duidelijkheid vereist is
- &quot;The&quot; weglaten vóór productnamen
- Inclusief &quot;Adobe&quot; bij eerste vermelding op hulplijnniveau (vereiste handelsmerk)
- &quot;Adobe&quot; in secundaire vermeldingen zetten, tenzij dit wettelijk verplicht is
- DNL-tags gebruiken voor productnamen om vervorming te voorkomen

### Nadruk en opmaak
- Vet: UI-elementen en toetsenbordacties
- Cursief: foutberichten, vreemde woorden, nadruk
- Code (backticks): bestandsnamen, URL&#39;s, door de gebruiker gedefinieerde termen
- Geen aanhalingstekens rond UI-elementen (gebruik in plaats daarvan de tag UICONTROL)

### Kapitalisatie
- Als in een zin uitgedrukte tekst, navigatie, subkoppen
- ALLEEN titelhoofdletters/kleine letters voor het metagegevensveld `title`
- Gepaste getallen worden altijd met hoofdletters weergegeven

---

## &#x200B;6. BESTE PRAKTIJKEN VOOR SEO

- Eén H1 per pagina — moet beknopt en beschrijvend zijn en gebruikers vertellen waar de pagina om gaat
- Hiërarchie van opeenvolgende koppen (h1 → h2 → h3, niveaus nooit overslaan)
- Trefwoorden opnemen in H1, platte tekst en metagegevens (niet de metatag `keywords` - Google negeert deze)
- Trefwoordopvulling vermijden (intentie > frequentie)
- Titel: max. 50-60 tekens; systeem voegt toe &quot;| Adobe ProductName&quot; automatisch
- Omschrijving: 150-160 tekens; moet een call to action zijn en geen herhaling van inhoud
- Beschrijvende alt-tekst toevoegen aan alle afbeeldingen
- Inclusief videoritscripties (zoekmachines kunnen alleen tekst lezen)
- Strategisch koppelen aan gerelateerde pagina&#39;s (zwevende pagina&#39;s vermijden)
- Inclusief gestructureerde elementen: genummerde lijsten, subkoppen, codeblokken
- Hulpmiddelen van het gebruik zoals AnswerThePublic, Google probeert aan onderzoekstrefwoorden
- Inhoud moet E-E-A-T aantonen (ervaring, deskundigheid, gezaghebbendheid, betrouwbaarheid)

---

## &#x200B;7. LOKALISATIE

### Eerst machinevertaling
- Engelse broninhoud genereert automatisch gelokaliseerde versies
- Ondersteunde talen: Duits, Frans, Japans, Italiaans, Spaans, Braziliaans Portugees, Vereenvoudigd Chinees, Traditioneel Chinees, Koreaans, Nederlands, Zweeds

### Schrijven voor lokalisatie
- Consistente terminologie
- Korte zinnen en actieve stem
- StandaardEngelse woordvolgorde (subject → verb → object)
- Relatieve uitspraak gebruiken (&quot;dat,&quot; &quot;dat&quot;)
- Vermijd: humor, idiomen, jargon, regionale woordgroepen, metafoor, overbodige woorden

### Lokalisatietags
- `[!UICONTROL Label]` — zorgt ervoor dat UI-tekenreeksen van product-DB worden opgehaald, niet automatisch worden vertaald
- `[!DNL ProductName]` — Voorkomt dat productnamen/merknamen worden vertaald
- Afbeeldingen in een map &#39;do-not-localize&#39; zijn uitgesloten van lokalisatie

---

## &#x200B;8. INHOUDSTYPEN

- **Gids**: Online inzameling van pagina&#39;s die in TOC van verwijzingen worden voorzien; behandelt officiële beste praktijken
- **Leerprogramma**: De inhoud van de Instructie (video of tekst) voor specifieke gebruiksgevallen; gepubliceerd in leert repos
- **Gids van de Verwijzing**: Ontwikkelaar APIs/SDKs; typisch lijstformaat; gepubliceerd aan developer.adobe.com
- **Cursus**: Deskundige-gekromde inzameling van lessen gericht op specifieke gebruikersrollen
- **de Artikelen van de Kennisbank**: Kort, tijdelijk relevante het oplossen van problemeninhoud
- **Landing Pagina/Homepage**: Beheerd afzonderlijk (SCCM)

---

## &#x200B;9. ALGEMENE VALIDATIEFOUTEN OM TE VOORKOMEN

- Ontbrekende of lege `title` of `description` metagegevens
- `description` begint niet met &quot;Meer informatie over..&quot; of &quot;Leer hoe...&quot;
- Ruimte tussen `>` en `[!` in callout syntaxis (`> [!NOTE]` in plaats van `>[!NOTE]`)
- Spaties in vette markeringen: `**text **` (spaties worden vet afgebroken)
- Markeringssyntaxis in HTML-tabellen (callouts werken daar bijvoorbeeld niet)
- Kopanker-id&#39;s in een document dupliceren
- Anker-id&#39;s met punten (gebruik in plaats daarvan afbreekstreepjes)
- Het gebruiken van gereserveerde ankernamen (onderzoek, resultaten, kopbal, footer, enz.)
- `role` , `level` , `feature` , `topic` waarden die niet overeenkomen met YAML-definities
- Gestapelde koppen zonder platte tekst
- H1 meer dan één keer per document gebruikt
- Niveaus van overgeslagen posten (bv. H1 → H3)
- Bestandsnaamgeving met hoofdletters, onderstrepingstekens of spaties
- Ontbrekende alternatieve tekst in afbeeldingen
- Gerund task heading (&quot;Creating...&quot;) in plaats van &quot;Maken...&quot;)
