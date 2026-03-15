---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 1%

---
# Adobe Experience League — Goedgekeurde metagegevensvelden - Referentie

*die van de Gids van de Authoring van Adobe ExL (gekropen Feb 2026) + repo analyse van blauwdrukken-learn.nl* wordt ontvangen

&#x200B;---

## Metagegevenshiërarchie

Metagegevenscascades in deze volgorde (artikel overschrijft inhoudsopgave, inhoudsopgave overschrijft repo):
1. Voornaam artikel (hoogste prioriteit)
2. TOC.md in de gebruikershandleiding
3. metadata.md op basis van repo-hoofdmap (laagste prioriteit)

&#x200B;---

## Velden op artikelniveau

### VEREIST

| Veld | Beschrijving | Indeling/beperkingen |
|-------|-------------|----------------------|
| `title` | SEO-paginatitel. Wordt weergegeven in zoekresultaten. | Max ~60 tekens; titeldraagtas; gebruik `[!DNL Product]` voor productnamen; dupliceer H1 NIET exact tenzij dit de bedoeling is |
| `description` | Meta-beschrijving voor zoekmachines en ExL-aanbevelingen. | 150-160 tekens; idealiter begint &quot;Leren hoe..&quot; of &quot;Meer informatie over...&quot;; validatie mislukt indien ontbreekt/null |
| `exl-id` | Door het systeem toegewezen unieke id. Wordt gebruikt voor het bijhouden van inhoud. | UUID formaat (b.v. `70573eb9-cd69-4fe6-b2ae-dae81665a308`); **schrapping wanneer het kopiëren van een dossier** — het zal auto-toegewezen zijn; nooit gedupliceerd over dossiers |

### STERK AANBEVOLEN

| Veld | Beschrijving | Geldige waarden |
|-------|-------------|--------------|
| `solution` | Adobe-product(en) waarop het artikel betrekking heeft. Wordt gebruikt voor zoeken/filteren in ExL en aanbevelingen voor inhoud. | Komma-gescheiden; case-sensitive; moet goedgekeurde enum aanpassen (zie de Geldige Waarden van de Oplossing hieronder) |

### OPTIONEEL — GEMEENSCHAPPELIJK

| Veld | Beschrijving | Geldige waarden / notities |
|-------|-------------|----------------------|
| `kt` | Verouderde kennis-artikel JIRA-nummer. Wordt gebruikt voor het bijhouden van analyses. | Geheel getal (bijvoorbeeld `7207`); leeg acceptabel; `null` acceptabel |
| `thumbnail` | Referentie miniatuurafbeelding voor aanbevelingen/analyses. | Bestandsnaamreeks of `null` of leeg |
| `version` | Productversiefilter. Voornamelijk gebruikt voor blauwdrukken van AEM en Campagne. | E.g. `Campaign v8`, `Campaign v8 Client Console`; moet version.yml aanpassen |
| `doc-type` | Indeling van het gehalte in repo/analyse. | `blueprint`, `overview-page`, `Video`, `Tutorial`, `Troubleshooting` (voorkeur in kleine letters) |
| `feature` | Onderwerplabels die op ExL-pagina&#39;s als &quot;Onderwerpen&quot; worden weergegeven. | 1-2 per artikel; titelhoofdletters/kleine letters; moet feature.yml aanpassen; komma&#39;s gescheiden |
| `feature-set` | Bovenliggende toepassing voor validatie van functies. | Moet overeenkomen met eigenschap.yml-waarden |
| `role` | Rol doelpubliek. Weergegeven als &quot;Gemaakt voor&quot; op ExL. | `Admin`, `Architect`, `Data Architect`, `Data Engineer`, `Developer`, `Leader`, `User` |
| `level` | Gebruikerservatieniveau. Weergegeven als &quot;Gemaakt voor&quot; op ExL. | `Beginner` , `Intermediate` , `Experienced` (titelcase) |
| `topic` | Interconnectiviteit tussen producten voor zoeken/filteren. | Het geval van de titel; moet topic.yml aanpassen; komma-gescheiden |
| `type` | Hulplijnindeling. | `Documentation` (standaardwaarde), `Tutorial`, `Troubleshooting` |
| `last-substantial-update` | Inhoud oppervlakken in &quot;Nieuwe functies&quot;-widgets. | Indeling: `YYYY-MM-DD` |
| `hide` | Hiermee sluit u de pagina uit van alle zoekopdrachten en aanbevelingen en stelt u de index in op Geen. | `yes` of `no` |
| `hidefromtoc` | Verwijdert uit de navigatie van TOC maar de pagina is nog toegankelijk via directe verbinding. | `yes` of `no` |
| `index` | Bepaalt of de pagina wordt weergegeven in externe zoekopdracht/sitemap. | `yes`/`no` of `y`/`n`; default: `no` (geïndexeerd) |
| `recommendations` | Bepaalt het gedrag van de widget &quot;Meer hulp bij deze functie&quot;. | `noDisplay` (voorkomt weergave van widgets), `noCatalog` (sluit uit van groep met aanbevelingen) |
| `internal` | Hiermee markeert u de pagina als alleen intern Adobe. Voorkomt markering van interne koppeling. | `yes` |
| `short-description` | Omschrijving met een condensiteit voor ExL-bestemmingspagina&#39;s. Gebruikt `description` als deze wordt weggelaten. | Eén zin; max ~20 woorden |
| `activity` | Classificatie van paginagebruik. | `understand` , `implement` , `troubleshoot` (kleine letters) |
| `sub-product` | Productsubcomponent. Werk met oplossingsteams voor geldige opsommingen. | Kleine letters; bijvoorbeeld `search`, `assets`, `sites` |
| `team` | Teamtoewijzing voor analyses. | E.g. `TM` |
| `landing-page-name` | Koppelingen naar bestemmingspagina voor broodkruimel. | E.g. `experience-manager` |
| `landing-page-breadcrumb-title` | Breadcrumb-tekst voor koppeling naar bestemmingspagina. | E.g. `AEM` |
| `auto-video-transcripts` | Hiermee schakelt u standaardinstellingen voor videotranscripties in. | `true` |
| `badgeType` | Badge for content status. | Varieert; bijvoorbeeld `informative`, `positive` |
| `badgePremium` | Premium-badge-indicator. | Specificaties per Adobe-badge |
| `badgeLabel` | labeltekst voor badge. | Korte tekenreeks |
| `source-git-url` | URL Source-opslagplaats. | Volledige GitHub-URL |
| `cloud` | Overschrijven van de categorie Wolk op artikelniveau. | Hoofd-kleine letter; moet overeenkomen met cloud.yml |

&#x200B;---

## TOC.md-velden

| Veld | Beschrijving | Notities |
|-------|-------------|-------|
| `user-guide-title` | Naam van hulplijn weergegeven in ExL-broodkruimels en bestemmingspagina&#39;s. | Vereist voor inhoudsopgavebestanden |
| `breadcrumb-title` | Kortere hulplijnnaam voor broodkruimels wanneer de gebruikershandleiding te lang is. | Optioneel |
| `user-guide-description` | Overzicht van hulplijnen voor de bestemmingspagina van ExL. | Eén zin; maximaal ~20 woorden aanbevolen |
| `product` | Analyses bijhouden voor de handleiding. Alleen enkele waarde. | Moet overeenkomen met product.yml (zie Geldige productwaarden) |
| `mini-toc-levels` | Aantal kopniveaus die in rechts-nav mini-TOC worden getoond. | Geheel getal 1-6; standaard 2 |
| `role` | Standaardrol voor het publiek voor de hulplijn. | Dezelfde waarden als artikel `role`; gescheiden door komma&#39;s |
| `index` | Of de hulplijn is geïndexeerd. | `yes`/`no` |

&#x200B;---

## Metagegevens op reaniveau.md-velden

| Veld | Notities |
|-------|-------|
| `cloud` | Standaardwolkencategorie voor alle artikelen in reactie |
| `solution` | Standaardoplossing voor alle artikelen |
| `product` | Standaardproduct voor het bijhouden van analyses |
| `type` | Standaardhulplijntype |
| `doc-type` | Standaarddocumenttype |
| `mini-toc-levels` | Standaardniveaus voor miniinhoudsopgave |
| `git-repo` | GitHub repo-URL; schakelt de knoppen &quot;Deze pagina bewerken&quot; en &quot;Logprobleem&quot; in |
| `index` | Standaardinstelling |

&#x200B;---

## Geldige oplossingswaarden (hoofdlettergevoelig)

In dit antwoord gebruikte gemeenschappelijke waarden:
- `Experience Platform`
- `Real-Time Customer Data Platform`
- `Journey Optimizer`
- `Journey Optimizer B2B Edition`
- `Customer Journey Analytics`
- `Campaign`
- `Campaign v8`
- `Campaign Classic v7`
- `Campaign Standard`
- `Audience Manager`
- `Target`
- `Analytics`
- `Data Collection`
- `Commerce`
- `Marketo Engage`
- `Experience Cloud`
- `Journey Orchestration`

Meerdere waarden: door komma&#39;s gescheiden, bijvoorbeeld `Real-Time Customer Data Platform, Campaign`

&#x200B;---

## Geldige productwaarden (voor veld `product` — analysetracering)

Zie de vraag van het systeem voor volledige lijst. Hoofdwaarden:
- `adobe experience platform` / `experience platform` / `aem`
- `adobe analytics` / `analytics` / `aa`
- `adobe journey optimizer` / `journey optimizer` / `jo`
- `adobe customer journey analytics` / `customer journey analytics` / `cja`
- `adobe real time customer data platform` / `real time cdp` / `rtcdp`
- `adobe marketo` / `marketo` / `amk`
- `adobe campaign` / `campaign` / `ac`
- `adobe target` / `target` / `at`

&#x200B;---

## Geldige rolwaarden

- `Admin`
- `Architect`
- `Data Architect`
- `Data Engineer`
- `Developer`
- `Leader`
- `User`

&#x200B;---

## Regels voor sleutelvalidatie

1. Laat `exl-id` nooit met dezelfde UUID achter in een gekopieerd bestand — verwijder het bestand en laat het systeem een nieuw bestand toewijzen.
2. Lege/null `thumbnail` en `kt` zijn acceptabel; dit zijn verouderde velden.
3. `solution` -waarden moeten exact overeenkomen met de goedgekeurde opsomming, hoofdlettergevoelig.
4. `description` De validatie mislukt bij ontbrekende of null. Geef altijd een betekenisvolle waarde op.
5. Plaats `title` -waarden tussen aanhalingstekens als deze dubbele punten, vierkante haakjes of speciale voorlooptekens bevatten.
6. Meerdere `solution` -waarden worden gescheiden door komma&#39;s binnen een enkele tekenreekswaarde.
7. `product` is alleen één waarde (voor het bijhouden van analyses); gebruik geen door komma&#39;s gescheiden waarden.
8. Als u nieuwe opsommingswaarden wilt aanvragen, dient u een UGP JIRA-ticket in met de component &quot;Inhoud taggen&quot;.
