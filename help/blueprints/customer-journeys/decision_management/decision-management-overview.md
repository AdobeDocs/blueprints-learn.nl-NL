---
title: Verwijzingen naar Besluit Management
description: Aangepaste aanbiedingen leveren voor alle reizen van de klant.
solution: Experience Platform, Journey Optimizer
exl-id: 1bc9335c-5321-4d0c-939e-4f402e2e8f51
source-git-commit: 60a7785ea0ec4ee83fd9a1e843f0b84fc4cb1150
workflow-type: tm+mt
source-wordcount: '701'
ht-degree: 0%

---

# Journey Optimizer - blauwdrukken voor besluitvormingsbeheer

Voor meer informatie over het beheer van beslissingen raadpleegt u de [productdocumentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)

Beslissingsbeheer van de Adobe is een dienst die wordt verleend als onderdeel van Adobe Journey Optimizer. Deze blauwdruk schetst de gebruiksgevallen en de technische mogelijkheden van de toepassing en verstrekt een diepe duik in de diverse architecturale componenten en overwegingen die omhoog het Beheer van de Beslissing maken.

Journey Optimizer wordt gebruikt om uw klanten de beste aanbieding en ervaring op alle aanraakpunten op het juiste moment te bieden. Beslissingsbeheer maakt personalisatie gemakkelijk met een centrale bibliotheek van marketing aanbiedingen en een besluitvormingsmotor die regels en beperkingen op rijke, real-time profielen toepast die door Adobe Experience Platform worden gecreeerd om u te helpen uw klanten het juiste aanbod op het juiste ogenblik verzenden.

De beslissingsmanagementcapaciteit bestaat uit twee hoofdcomponenten:

* De gecentraliseerde Bibliotheek van de Aanbieding die de interface is waar u creeert en de verschillende elementen beheert die uw aanbiedingen samenstellen, en hun regels en beperkingen bepalen.
* De Offertebeslissingsengine die gebruikmaakt van Adobe Experience Platform-gegevens en realtime klantprofielen, samen met de Offertebibliotheek, om de juiste tijd, klanten en kanalen te selecteren waaraan aanbiedingen worden geleverd.

<img src="../assets/offers_overview.png" alt="Beslissingsbeheer" style="width:100%; border:1px solid #4a4a4a" />

Beslissingsbeheer kan op twee manieren worden ingezet, op de rand of via de hub. Elk van deze methodes heeft een specifieke reeks interfaces en protocollen voor het werken van de dienst zoals geschetst in de respectieve hieronder vermelde blauwdrukken. Nadere gegevens zijn ook te vinden in het [Beslissingsbeheerdocumentatie](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/api-reference/offer-delivery-api/decisioning-vs-edge-apis.html).

## Beslissingsbeheer op de hub

De eerste is via de Adobe Experience Platform hub, een centrale datacenterarchitectuur. In de &quot;hub&quot;-benadering worden aanbiedingen uitgevoerd, gepersonaliseerd en geleverd met een latentie van > 500 ms. Aldus is de hubarchitectuur het best geschikt voor klantenervaringen die geen sub-tweede latentie vereisen, omvatten de voorbeelden aanbiedingsbesluiten die voor kiosken of agent bijgewoonde ervaringen zoals in callcenters of in persoonlijke interactie worden verstrekt. Aanbiedingen die in e-mail, de berichten van SMS, of dupberichten en andere uitgaande campagnes worden opgenomen worden ook aangedreven door de hubbenadering. Meer informatie over het Beheer van het Besluit op de hub verwijst naar [Beslissingsbeheer op de hub](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-hub.html?lang=en) blauwdruk.

* Aanbiedingsgeschiktheid kan werken volgens het volledige real-time klantprofiel, inclusief alle kenmerken en ervaringsgebeurtenissen

### Gebruik van gevallen voor beslissingsbeheer op de hub

* Speciale aanbiedingen voor kiosken en winkelervaringen.
* Persoonlijke aanbiedingen via de hulp van een agent, zoals callcenters of verkoopinteracties.
* Aanbiedingen inbegrepen in e-mail, SMS, of andere uitgaande interactie.
* Transactieuitvoering via verschillende kanalen - biedt consistentie via internet, mobiele apparaten, e-mail en andere interactiekanalen via Adobe Journey Optimizer.

### Beslissingsbeheer met betrekking tot de technische aspecten van de hub

* Verzoeken per seconde = 2000.
* Latentie van respons &lt; 500 ms.
* Toegang tot volledig real-time klantprofiel met inbegrip van publiekslidmaatschappen, attributen en ervaringsgebeurtenissen.

## Beslissingsbeheer aan de rand

De tweede aanpak is gebaseerd op de ervaring [!DNL Edge Network], een wereldwijd gedistribueerde geografisch gesitueerde infrastructuur om snelle sub-seconde en millisecondenervaringen te dienen. De eindgebruikerservaring die wordt uitgevoerd door de randinfrastructuur die het dichtst bij de geo-locatie van de consument ligt om de latentie te minimaliseren. Beslissingsbeheer op de rand is ontworpen om in real-time ervaringen met de consument te bieden, zoals web- of mobiele binnenkomende verzoeken om personalisatie. Raadpleeg voor meer informatie over Beslissingsbeheer op Edge [Beslissingsbeheer aan de rand](https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer/decision-management/decision-management-edge.html?lang=en) blauwdruk.

### Gebruik gevallen voor Beslissingsbeheer aan de rand

* Online personalisatie via internet of mobiele binnenkomende ervaringen.
* Transactieuitvoering via verschillende kanalen - biedt consistentie via internet, mobiele apparaten, e-mail en andere interactiekanalen via Adobe Journey Optimizer.

### Beslissingsbeheer op basis van geavanceerde technische overwegingen

* Verzoeken per seconde = 5000.
* Latentie van respons &lt; 250 ms.
* Toegang tot real-time randprofiel. In het profiel zijn alleen geprojecteerde soorten publiek en profielkenmerken beschikbaar.
* Als verpersoonlijking in eerste-tijdervaringen wordt vereist, zal de hub ideaal zijn aangezien het volledige profiel beschikbaar is. Het randprofiel moet voor het eerst worden gesynchroniseerd vanuit de hub. De allereerste ervaring met de rand bevat dus geen eerder geüploade profielgegevens naar de hub.

## Gerelateerde documentatie

* [Adobe Experience Platform](https://experienceleague.adobe.com/docs/experience-platform.html)
* [Adobe Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer.html)
* [Adobe Journey Optimizer-beslissingsbeheer](https://experienceleague.adobe.com/docs/journey-optimizer/using/offer-decisioniong/get-started-decision/starting-offer-decisioning.html)
* [Adobe Journey Optimizer-productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/adobe-journey-optimizer.html)
* [Adobe Beslissingsbeheer Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/offer-decisioning-app-service.html)
