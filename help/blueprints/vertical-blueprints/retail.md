---
title: Detailhandel - Activering met Experience Cloud-toepassingen
description: Lever real-time, klantenervaringen over digitale media, e-mail, duw, en Webkanalen.
solution: Real-Time Customer Data Platform, Customer Journey Analytics, Journey Orchestration, Campaign, Analytics, Target
kt: 9474
exl-id: a675bc81-e76c-491a-8718-359867d63351
source-git-commit: 2dab717d638bdbc0a903861ec743a81f2aed986d
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Zakelijke uitdaging voor de detailhandel

Deze geïntegreerde ervaringszaken probeerden de volledige klantenreis aan te passen om loyaliteit te verhogen, aan bestaande klanten upsell, en marketing uitgaven over hun campagnes te verbeteren. De strategie om het doel te bereiken is door hun digitale capaciteit uit te breiden om off-line klantengegevens &amp; transactiegegevens te omvatten om de groei te drijven.

## Adobe

* Genereer een verenigd klantprofiel dat alle relevante online/offline gegevens bevat die in real time kunnen worden geactiveerd
* Ordeer klantinteracties via internet, media en pushkanalen om het aankoopgedrag voor het eerst of voor de tweede keer te stimuleren.

## Bedrijfswaarde geleverd

| Doelen | Tactiek | Waarde ontgrendeld |
|---|---|---|
| **Realtime klantreizen ordenen **<br></br>**Aankopen van nieuwe klanten herhalen **<br></br>**Verbeter marketing efficiency en verminder media kosten**</ul> | <ul><li>Robuuste gegevens- en identiteitsstrategie om een alomvattend real-time profiel te voeden.</li><li>Klant en transactionele gegevensstreaming in real-time inclusief een historische belasting van 90 dagen</li><li>Segmentering streamen naar Advertising Networks en Adobe Target om media-uitgaven en personaliseringsinspanningen te stimuleren.</li><li>Realtime klantritten door Adobe Campaign die een strategie omvatten om prestaties te meten</li></ul> | <ul><li><strong>Real-time Customer Data Platform:</strong> In real-time, ervaringen van klanten op verschillende media, e-mail, push en het web</li><li><strong>Gegevensbronnen:</strong> Streaming gegevens over de profielopslag, het bestelsysteem, de productcatalogus en de detailhandel van deze detailhandelaar.</li><li><strong>Real-time media activeren:</strong>Streaming segmenten naar advertentienetwerken voor toewijzing en onderdrukking van advertenties</li><li><strong>Personalisatie in realtime van het web:</strong>Streaming segmenten geactiveerd naar Adobe Target om de webbeleving van de detailhandelaar te activeren.</li><li><strong>Journey Orchestration op schaal:</strong>Berichten in real-time geactiveerd, verrijkt met beschikbare klantgegevens en geactiveerd in real-time voor e-mail en pushkanalen</li></ul> |


## Gebruiksmogelijkheden

| Categorie | Goal | Hoofdletters gebruiken | Beschrijving |
|:----|:----|:----|:----|
| Klantenreizen | Verwerving | Welkomstserie | Welkom nieuwe abonnees met introductie in het bedrijf, het product en de services |
| | | Eerste aankoopprogramma | |
| | Verkoop verbeteren | Verlaten winkelwagentje/bladeren | Herstel van potentiële kopers en opdrijvende verkopen |
| | | Productbeoordeling/Crossselderij | Meer objecten doorverkopen met productherzieningen. |
| | | Productpromoties |  |
| | | Tijd voor opnieuw ordenen | Herhaling van herinnering voor cyclische producten/services |
| | Brand Loyalty | Win terug | Klanten herstellen die inactief zijn geweest. |
| | | Verjaardagherinneringen | Bevorder een persoonlijkere relatie met uw klanten door deel van hun verjaardagsfeest te zijn! |
| Merchandising | Inventaris beheren | Terug in voorraad | Verbeter inventaris door klanten te tonen de producten die zij gewild hebben terug in voorraad zijn |
| | | Volgende beste rubriek | Beste categorieën/verkopen voor gebruikers identificeren |
| | | Beste verkopers | |
| | | Herinneringen voor neerzetten van prijs | Gebruikers laten zien dat objecten die ze leuk vinden een lagere prijs hebben |
| | | Vergelijkbare producten |  |
| Persoonlijk maken | Conversie verhogen | Coupons/voorstellen | Beste voorstellen/coupons voor klanten weergeven |
| | | Persoonlijke productzoekopdracht | Zoekervaring verbeteren |
| | | Product Recommendations | Ervaring met bladeren door producten verbeteren |
| | | Universeel-kanaalervaring | Klanten op alle kanalen bereiken |
| Meetlat | Klantreizen begrijpen | Campagne voor meerdere kanalen | Kanaalcampagnes meten |
| | | Segmentprestaties | De prestaties en bijdrage van segmenten begrijpen |
| | | Falloutrapporten | Conversies in elke fase visualiseren |
| | | Cohortanalyse | De betrokkenheid van de maatregel tussen segmentgroepen |
| | | Click-to-Brick-rapporten | Ontdek hoe klantconversies leiden tot ervaringen in de winkel |
| | | Attributie | Weergeven welk aanraakpunt/ervaring de grootste invloed heeft op de conversie van aankopen |
| | | Voorspelende inzichten | Meer informatie over klanteneigenschappen |

## Architectuur

<img src="../vertical-blueprints/assets/retail-architecture.png" alt="Detailreferentiearchitectuur" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />


## Verwante blauwdrukken


| Hoofdlettergebruik/integratie gebruiken  | Koppeling |
|:----|:----|
| CJA + AEP | [Overzicht van Customer Journey Analytics blauwdrukken](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=en) |
| | [Customer Journey Analytics - Gebruik hoofdletters](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-usecases/cja-usecases.html?lang=en) |
| AJO + AEP | [Adobe Journey Optimizer - Kwesties gebruiken](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/journey-optimizer.html?lang=en) |
| | [Beslissingsbeheer](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-overview.html?lang=en) |
| RTCDP + AEP | [Online/offline Audience Activation](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/known-customer-audience-activation/known.html?lang=en) |
| | [Experience Platform + activering van toepassing](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en) |
| Marketo + AEP | [B2B-activering en marketing](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/b2b-activation/overview.html?lang=en) | |
| Doel + AEP | [Adobe Target Use case - Behavioral Web/Mobile Personalization](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/web-personalization/behavioral.html?lang=en) | [Web/Mobiele Personalisatie met bekende klantengegevens](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/web-personalization/known-personalization.html?lang=en) | |
