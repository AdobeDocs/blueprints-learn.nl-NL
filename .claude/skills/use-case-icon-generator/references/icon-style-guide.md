---
source-git-commit: ef1c207922c1079117d8bd255dbfa32a1527b014
workflow-type: tm+mt
source-wordcount: '832'
ht-degree: 2%

---
# Hulplijn hoofdletters/kleine letters gebruiken

## Overzicht

Pictogrammen voor hoofdletters en kleine letters gebruiken dienen als visuele id&#39;s in de catalogus met hoofdletters en kleine letters. Ze moeten onmiddellijk herkenbaar zijn bij een weergavebreedte van 40 px en de kwaliteit behouden bij de standaardresolutie van 1024 x 1024.

## Technische specificaties

| Eigenschap | Waarde |
| --- | --- |
| Dimensies | 1024 x 1024 pixels |
| Indeling | PNG (8-bits RGB of RGBA) |
| Bestandsgrootte | 900 kB - 1,4 MB standaard |
| Weergavegrootte | 40 px breedte in catalogustabellen |
| Naamgeving | `icon-{kebab-case-name}.png` |
| Opslagpad | `/help/blueprints/industry-use-cases/assets/use-case-icons/{industry}/` |

## Richtlijnen voor visuele stijl

### Samenstelling
- **Enig centraal onderwerp** — Elk pictogram zou één duidelijke visuele metafoor moeten kenmerken die het concept van het gebruiksgeval vertegenwoordigt
- **Gecentreerde samenstelling** — Het belangrijkste onderwerp zou met evenwichtige whitespace moeten worden gecentreerd
- **Geen tekst** — De Tekst is onleesbaar bij 40px; baseer zich volledig op visuele metafoor
- **Geen complexe scènes** — Vermijd multi-element samenstellingen, achtergronden met vele voorwerpen, of narratieve scènes
- **Vette silhouetten** — De vorm van het pictogram zou zelfs als zeer klein silhouet herkenbaar moeten zijn

### Kleur en toon
- **Schone, moderne palet** - Gebruik beroeps, collectief-aangewezen kleuren
- **de cohesie van de Industrie** — De pictogrammen binnen de zelfde industrie zouden moeten voelen alsof zij samen behoren
- **Hoog contrast** - verzeker het belangrijkste onderwerp duidelijk van de achtergrond uitkomt
- **vermijd neon of oververzadigde kleuren** — houd het palet verfijnd en professioneel

### Stijl
- **Modern en beroeps** — Schone lijnen, gepolijst eind
- **Consistent teruggevend** — Alle pictogrammen zouden uit het zelfde ontwerpsysteem moeten schijnen te komen
- **3D of vlak is aanvaardbaar** - maar ben verenigbaar binnen een industrie verticaal
- **vermijd fotomealisme** — Afbeelding of teruggegeven stijl verkieslijk voor consistentie
- **Geen merklogo&#39;s of gedeponeerde beelden** — Gebruik generische visuele metafors

### Kleinschalige leesbaarheidstest
Voordat u gaat voltooien, schaalt u de afbeelding mentaal naar 40 px:
- Kunt u het hoofdonderwerp identificeren?
- Is er voldoende contrast tussen voorgrond en achtergrond?
- Zijn er fijne details die zouden veranderen in visuele ruis?
- Leest de vorm duidelijk zonder kleur (in het geval van toegankelijkheid)?

## Visual Metaphor Examples by Industry

### Retail
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| Verlaten wagen | Winkelwagentje met objecten |
| Aanbevelingen voor producten | Cadeaudoos of gekrulde producten |
| Crossverkoop Upsell | Verbonden winkelartikelen |
| Welkomstserie | Welkomstkaart of cadeau |
| Prijsdaling | Prijscode met pijl-omlaag |

### Automobielen
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| Herinneringen voor services | Kalender voor gebruik door moersleutel |
| Aanschaf van voertuig | Auto met toetsen |
| Handel in | Pijlen voor het uitwisselen van auto&#39;s |
| Verbonden auto | Auto met digitale verbinding |

### Gezondheidszorg
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| Herinnering benoeming | Kalender met stethoscoop |
| Adherentie van geneesmiddelen | Fles of voorschrift |
| Preventieve zorg | Schild met gezondheidssymbool |

### Financiële diensten
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| Lead Nurturturturturturing | Groeidiagram of zaadveredeling |
| Churenpreventie | Schild- of retentiesymbool |
| Levensfase | Tijdlijn levensmijlpalen |

### B2B
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| ABM | Doel met samenstellen |
| Scores voor lead | Scoreprofiel of thermometer |
| Verlenging contract | Document met vernieuwingssymbool |

### Reizen en verblijf
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| Kart-opheffing | Kassen of boeken |
| Loyalty-programma | Loyalty- of sterkenteken |
| Herinneringen voor boeken | Kalender met vliegtuig/hotel |

### Verzekering
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| Beleidsherstel | Document met pijlen voor verlenging |
| Claimverwerking | Klembord met vinkje |
| Cross-Sell | Verbonden beleidsdocumenten |

### Media en entertainment
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| Nieuwe inhoud | Knop Afspelen of spotlicht |
| Aanbevelingen voor inhoud | Gekrulde afspeellijst of gestart-inhoud |
| Subscription Churn | Gebroken abonnementkaart |

### Telecommunicatie
| Gebruiksscenario | Visuele metafoor |
| --- | --- |
| Optimalisatie van plannen | Signaalbalken met vistuig |
| Apparaatupgrade | Telefoon met pijl-omhoog |
| Churenpreventie | Schild met signaal |

## Sjabloon voor prompt genereren van afbeelding

Gebruik deze sjabloon als beginpunt en pas het onderwerp en de details voor elk geval van gebruik aan:

```
A clean, modern icon illustration of {visual metaphor} representing {use case concept}. Professional corporate design style with bold shapes and clean lines. Single centered subject on a {solid/gradient} background. High contrast, vibrant but refined color palette. No text, no fine details, no complex backgrounds. The icon must be clearly recognizable when scaled down to 40 pixels. Square format, 1024x1024 pixels.
```

### Tips voor snelle aanpassing

- **ben specifiek over het onderwerp** — &quot;Een helderrood winkelwagentje met twee kleurrijke cadeaudozen binnen&quot;is beter dan &quot;een winkelwagentje&quot;
- **specificeer achtergrondbehandeling** — &quot;op een zachte blauwe gradiëntachtergrond&quot;of &quot;op een schone witte achtergrond met subtiele schaduw&quot;
- **Verlichting van de Mentie** - de &quot;zachte studioverlichting&quot;of &quot;zachte omgevingsgloed&quot;helpt consistentie bereiken
- **voegt stijlbepalingen** toe - &quot;minimalist&quot;, &quot;geometrisch&quot;, &quot;isometric&quot;, of &quot;vlak ontwerp&quot;om esthetisch te sturen
- **omvat negatieve herinneringen indien gesteund** — &quot;geen tekst, geen watermerken, geen grenzen, geen fotorealistische elementen&quot;

## Bestaande pictograminventaris

### Naar bedrijfstak

**Kleinhandel (9 pictogrammen):**
pictogram-verlaten-kar, pictogram-inventaris-urgentie, pictogram-prijs-daling, pictogram-product-aanbevelingen, pictogram-categorie-pagina&#39;s, pictogram-welkome-reeks, pictogram-aanvulling, pictogram-post-aankoop, pictogram-dwars-verkoop-upsell

**Automobiel (12 pictogrammen):**
icon-service-herinneringen, pictogram-terugroepen-berichten, pictogram-test-aandrijving, pictogram-model-lancering, pictogram-handel-binnen, pictogram-delen-toebehoren, pictogram-garantie, pictogram-verbonden-auto, pictogram-dealer-netwerk, pictogram-voertuig-aankoop, pictogramfinanciering, pictogram-eigenaar-loyaliteit

**Financiële Diensten (6 pictogrammen):**
pictogram-lood-verpleegster, pictogram-rekening-dashboard, pictogram-product-aanbeveling, icon-churn-preventie, pictogram-levensstadium

**Gezondheidszorg (4 pictogrammen):**
pictogram-afspraak-herinnering, pictogram-post-bezoek, pictogram-preventieve zorg, pictogram-medicatie-handigheid

**Verzekering (3 pictogrammen):**
icon-policy-refresh, icon-claims-process, icon-cross-sell

**Media &amp; Entertainment (3 pictogrammen):**
icon-new-content, icon-content-recommendations, icon-subscription-churn

**Telecommunicatie (3 pictogrammen):**
icon-plan-optimalisering, pictogram-apparaat-verbetering, pictogram-kurn-preventie

**reis &amp; Ziekenbaarheid (12 pictogrammen):**
pictogram-kart-verlaten, pictogram-boekende-herinneringen, pictogram-seizoensgebonden-campagnes, pictogram-gepersonaliseerd-homepage, pictogram-high-intent, pictogram-post-boeken-upsell, pictogram-win-rug, pictogram-dynamisch-route, pictogram-onlangs-doorbladerend, pictogram-groep-boek, pictogram-uitgang-bedoeling, pictogram-loyaliteit-programma

**B2B (11 pictogrammen):**
icon-webinar-demo, icon-abm, icon-lead-scoring, icon-content-personalization, icon-event-registration, icon-trial-conversion, icon-customer-onboarding, icon-competitive-replacement, icon-case-study, icon-contract-generation, icon-upsell-extension
