---
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '205'
ht-degree: 0%

---
# Experience League Agent-geheugen

## Belangrijkste referentiebestanden in deze repo
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/metadata.md` — standaardinstellingen voor metagegevens op repo-niveau
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/help/blueprints/TOC.md` — metagegevens op hulplijnniveau
- `/Users/nick/Library/CloudStorage/OneDrive-Adobe/Documents/GitHub/blueprints-learn.en/.cursor/skills/blueprint-document-reference/reference.md` — ontwerppatronen

## Metagegevensregels (zie metadata-fields.md voor volledige verwijzing)
- Voorvertoning van artikel vereist: `title`, `description`, `exl-id`
- HELEMAAL AANBEVOLEN voorpagina van artikel: `solution`
- `exl-id` moet een geldige UUID zijn; verwijder/laat leeg bij het kopiëren van bestanden (automatisch toegewezen door systeem)
- `description` moet beginnen met &#39;Leren hoe..&#39; of &quot;Meer informatie over...&quot; volgens Adobe-richtlijnen
- `title` max ~60 tekens voor SEO; gebruik `[!DNL ProductName]` voor productnamen in titel
- `solution` -waarden zijn hoofdlettergevoelig en moeten overeenkomen met de goedgekeurde opsomming (zie metadata-fields.md)
- `thumbnail: null` of `thumbnail:` (blank) worden beide gebruikt; leeg is acceptabel
- `kt:` is een oud veld (JIRA-nummer kennisartikel); wordt nog steeds in dit antwoord weergegeven; leeg is acceptabel
- Bestanden met inhoudsopgave gebruiken: `user-guide-title`, `breadcrumb-title`, `user-guide-description`, `product`, `mini-toc-levels`, `role`
- Repo-niveau `metadata.md` gebruikt: `cloud`, `solution`, `product`, `type`, `doc-type`, `mini-toc-levels`, `git-repo`, `index`

## Algemene patronen in deze repo (blueprints-learn.nl)
- De meeste blauwdrukbestanden hebben: `title` , `description` , `solution` , `exl-id`
- Enkele oudere bestanden zijn ook: `kt`, `thumbnail`
- Voor sommige bestanden wordt `version` gebruikt (campagne v8-blauwdrukken)
- Gebruik van overzichtspagina&#39;s `doc-type: overview-page`
- `solution` bevat vaak meerdere door komma&#39;s gescheiden waarden: bijvoorbeeld `Real-Time Customer Data Platform, Campaign`
- Bestanden zonder `solution` gaan nog steeds over tot validatie als `exl-id` aanwezig is

## Adobe Markdown Extensions gebruikt in deze repo
- `>[!NOTE]`, `>[!TIP]`, `>[!IMPORTANT]`, `>[!WARNING]`, `>[!CAUTION]`
- `>[!BEGINTABS]` / `>[!TAB Name]` / `>[!ENDTABS]` voor inhoud met tabs
- `[!DNL ProductName]` — Geen lokalisatietags voor productnamen
- `[!UICONTROL Label]` — Verwijzingen naar UI-besturingselementen
- `{zoomable="yes"}` — kenmerk voor zoomen van afbeelding
- `{width="1000"}` — kenmerk voor afbeeldingsbreedte
- `{target="_blank"}` — doel externe koppeling

## Gedetailleerde verwijzingen
- Referentie van volledig metagegevensveld: `metadata-fields.md`
- Authoring guide crawled: https://experienceleague.adobe.com/en/docs/authoring-guide-exl/using/home (februari 2026)
