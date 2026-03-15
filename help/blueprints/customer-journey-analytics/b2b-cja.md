---
title: B2B Customer Journey Analytics-blauwdruk
description: Neem B2B-account, opportuniteits- en inkoopgroepgegevens op in Customer Journey Analytics voor rapportage op basis van account en reisanalyse.
solution: Customer Journey Analytics
source-git-commit: 10e54d97082143b61e43bae56250a524d1759d45
workflow-type: tm+mt
source-wordcount: '729'
ht-degree: 0%

---


# B2B Customer Journey Analytics-blauwdruk

Customer Journey Analytics B2B edition maakt rapportage en analyse op basis van account mogelijk voor B2B-organisaties. In tegenstelling tot persoon-centric B2C analyseert, plaatst dit blauwdruk de **rekening** bij het centrum van het gegevensmodel zodat kunt u complexe B2B aankoopreizen over veelvoudige belanghebbenden, het kopen groepen, en verkoopcycli analyseren. Gebruik [!DNL Customer Journey Analytics] om gedragsgegevens te verenigen met B2B-dimensies (accounts, mogelijkheden, campagnes en marketinglijsten) voor op reizen gebaseerde inzichten en het creëren van een publiek.

## Applicaties

* Adobe [!DNL Customer Journey Analytics] (B2B edition)
* Adobe Experience Platform (voor B2B- en gebeurtenisgegevens)

## Gebruiksscenario&#39;s

* **optimaliseer rekening marketing** — Analyseer marketing effect over campagnes, kanalen, en inhoud op het kopen van groepen binnen rekeningen, pijpleidingsvooruitgang, en upsell/cross-sell kansen.
* **Groei zeer belangrijke rekeningen** - identificeer high-value touchpoints over het kopen groepen binnen zeer belangrijke rekeningen om marketing en verkoopacties te informeren, en de waarde van het klantenleven op het rekeningsniveau te berekenen.
* **bouwt productwaarde** — Meet het effect van productversies en gebruik op klantentevredenheid op rekening en gebruikersniveaus om eigenschappen te optimaliseren en ontwikkeling te informeren.
* **op persoon-gebaseerde B2B analyse** - combineer rekening en opportuniteitscontext met individueel gebruikersgedrag voor lood het scoren, overeenkomst, en reisanalyse.

## Vereisten

* [!DNL Customer Journey Analytics] B2B edition machtiging.
* B2B en gedragsgegevens in Adobe Experience Platform: B2B datasets (rekeningen, kansen, personen, campagnes, marketing lijsten, B2B activiteiten) en gebeurtenisgegevens (Web, mobiel, of andere kanalen) beschikbaar in de verbinding van a [&#x200B; CJA &#x200B;](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html?lang=nl-NL).
* [&#x200B; B2B noemend voor CJA &#x200B;](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html): B2B-Specifieke montages van de gegevensmening (rekeningsidentiteitskaart, opportuniteidentiteitskaart, en verwante dimensies) die voor de verbinding wordt gevormd.

## Architectuur

![&#x200B; architectuur van Customer Journey Analytics met B2B- rekening en opportuniteitsgegevens verenigd voor reisanalyse &#x200B;](assets/CJA.svg){zoomable="yes"}

Gegevens lopen van Experience Platform (B2B en gebeurtenissendatasets) naar [!DNL Customer Journey Analytics] via een CJA-verbinding. B2B-afmetingen worden weergegeven in gegevensweergaven, zodat analyse en publiek kunnen worden opgebouwd op account-, opportuniteits- en persoonniveaus.

## Beveiligingsmechanismen

* Voor het productgrenzen en de aanspraken van B2B edition, zie [&#x200B; Customer Journey Analytics B2B productbeschrijving &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/customer-journey-analytics-b2b.html).
* Voor het Platform van Analytics en de technische grenzen van CJA, zie [&#x200B; de gidsen van het Platform van Analytics &#x200B;](https://experienceleague.adobe.com/nl/docs/analytics-platform/using/technotes/guardrails).
* Voor CJA gegevensopname en verbindingsgrenzen, zie [&#x200B; de guardrails van de gegevensopname van Customer Journey Analytics &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=nl-NL#what-is-the-expected-latency-for-analytics-data-on-platform%3F).
* Als het publiceren van het publiek van CJA aan het Platform van de Gegevens van de Klant in real time, zie [&#x200B; het publiek dat van Customer Journey Analytics guardrails deelt &#x200B;](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=nl-NL#latency).
* Voor de latentie van begin tot eind en platformbegeleiding, verwijs naar het [&#x200B; document van de plaatsingsgidsen &#x200B;](../experience-platform/guardrails.md).

## Implementatiestappen

1. **Samenvatting B2B en gebeurtenisgegevens in Experience Platform** - breng in rekening, kans, persoon, campagne, en activiteitengegevens, plus gedragsgebeurtenissen, gebruikend [&#x200B; bronnen &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/sources/home.html?lang=nl-NL) (b.v. [!DNL Marketo Engage], CRM, of andere B2B schakelaars).
2. **creeer een verbinding van CJA** — [&#x200B; voeg de relevante datasets van Experience Platform &#x200B;](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html?lang=nl-NL) (B2B en gebeurtenis) aan een verbinding van Customer Journey Analytics toe.
3. **vorm B2B in de gegevensmening** - laat [&#x200B; B2B het noemen en zeer belangrijke dimensies &#x200B;](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html) toe (rekening identiteitskaart, opportuniteidentiteitskaart, enz.) in de gegevensweergave(en) van de verbinding.
4. **bouwt op rekening-gebaseerde analyse en publiek** - Gebruik [&#x200B; B2B van CJA gebruiksgevallen en het melden &#x200B;](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b.html?lang=nl-NL) om rapporten, onderbrekingen, en publiek op rekening en opportuniteitsniveau tot stand te brengen; naar keuze [&#x200B; publiceer publiek aan Real-time CDP &#x200B;](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=nl-NL) voor activering.

## Gerelateerde documentatie

### Customer Journey Analytics B2B edition

* [Customer Journey Analytics B2B edition](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-overview/cja-b2b/cja-b2b-edition.html?lang=nl-NL)
* [B2B-gebruiksgevallen](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b.html?lang=nl-NL)
* [Overzicht van B2B edition-gebruikskwesties](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b/b2b-edition/use-cases-overview.html?lang=nl-NL)
* [Een voorbeeld van een op persoon gebaseerd B2B-project](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/b2b/example.html?lang=nl-NL)

### Verbindingen en gegevensweergaven

* [Verbinding maken](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-connections/create-connection.html?lang=nl-NL)
* [B2B-instellingen voor gegevensweergave](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-dataviews/b2b.html)

### Soorten publiek en guardrails

* [CJA-publiek publiceren naar CDP in real-time](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=nl-NL)
* [Experience Platform en toepassingsinstructies](../experience-platform/guardrails.md)
