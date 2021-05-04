---
title: Vervaging van de Analyse van de Vervorming van de vraag Vervaging
description: Analyseer klantengedrag alvorens zij het vraagcentrum contacteren.
solution: Experience Platform, Customer Journey Analytics
kt: 7209
exl-id: 13593c1c-4c58-4b8a-aa6c-7530fd679a14
translation-type: tm+mt
source-git-commit: 58368eb06b9bbd6c332424bdcfa2789dde7d4c2f
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# De Vervaging van de Vraag de Vervaging Blauwdruk van de Analyse

Analyseer het gedrag van een klant op desktop en mobiel voordat deze contact opneemt met het callcenter. Identificeer kansen om de klantenreis te verbeteren door te begrijpen welke acties uw klanten proberen om te voltooien, welke inhoud zij, en welke termijnen bekijken zij alvorens zij klantensteun contacteren zoeken. Bepaal de inhoud en de zelfbedieningshulpmiddelen die kunnen worden verbeterd om uw klanten te helpen kwesties oplossen zonder het moeten binnen roepen.

## Gevallen gebruiken

* Het gedrag van klanten analyseren voordat klanten contact opnemen met de ondersteuningsafdeling
* Ontdek mogelijkheden om zelfbediening mogelijkheden te verbeteren

## Toepassingen

* Adobe Experience Platform
* Customer Journey Analytics

## Integratiepatronen

* Adobe Experience Platform → Customer Journey Analytics

## Architectuur

<img src="assets/CJA.svg" alt="Referentiearchitectuur voor de Customer Journey Analytics Blueprint" style="border:1px solid #4a4a4a" />

## Implementatiestappen

1. Vorm datasets en schema&#39;s.
1. Gegevens opnemen in Platform.
Gegevens moeten in het Platform worden ingenomen voordat ze in Customer Journey Analytics worden opgenomen.
1. Analyseer de gegevenssets voor kanaalgebeurtenissen.
Datasets die in union worden geanalyseerd, moeten een gemeenschappelijke naamruimte-id hebben of opnieuw worden weergegeven via de op velden gebaseerde stitching-mogelijkheid van Customer Journey Analytics. 

   >[!NOTE]
   >
   >Customer Journey Analytics gebruikt momenteel niet het profiel van het Experience Platform of de diensten van de Identiteit voor het stitching.

1. Voer om het even welk douane gegevensvoorbereiding of gebruik van de op gebied-gebaseerde identiteit uit stitching op de gegevens, om een gemeenschappelijke sleutel over tijdreeksdatasets te verzekeren die in Customer Journey Analytics moeten worden opgenomen.
1. Geef een primaire id op voor opzoekgegevens, die kunnen worden gekoppeld aan een veld in de gebeurtenisgegevens. Telt als rijen in licentie.
1. Stel dezelfde primaire id voor profielgegevens in als de primaire id van de gebeurtenisgegevens.
1. Configureer een gegevensverbinding om gegevens van Experience Platform tot Customer Journey Analytics in te voeren. Nadat gegevens in het datumpeer zijn geland, verwerkt het binnen 90 minuten tot Customer Journey Analytics.
1. Configureer een gegevensweergave op de verbinding om de specifieke afmetingen en metriek te selecteren die in de weergave moeten worden opgenomen. Attributie- en toewijzingsinstellingen worden ook geconfigureerd in de gegevensweergave. Deze instellingen worden tijdens het rapport berekend.
1. Creeer een project om dashboards en rapporten binnen Analysis Workspace te vormen.

## Overwegingen bij de implementatie

### Overwegingen bij het plaatsen van identiteiten

* Gegevens uit tijdreeksen die moeten worden verenigd, moeten dezelfde id-naamruimte hebben op elke record. Om de gegevens van het vraagcentrum met anonieme apparatengegevens te verbinden, moet digitale identiteitskaart aan roepende identiteitskaart worden gebonden. Deze koppeling kan op verschillende manieren plaatsvinden:
   * Het wijzerplaataantal is een uniek wijzerplaataantal voor die bezoeker voor die tijd, samen met een raadplegingslijst om de verhouding te volgen.
   * Verplicht de gebruiker voor authentiek te verklaren alvorens steun te verzoeken en deze authentificatie aan een herkenningsteken te binden die door de vraagagent wordt bepaald (bijvoorbeeld, telefoonaantal of e-mail).
   * Gebruik een partner aan boord om online apparatenherkenningstekens met bekende herkenningstekens te helpen verbonden aan het steunverzoek.
* Het verenigingsproces van het verenigen van verschillende datasets vereist een gemeenschappelijke primaire persoon/entiteitsleutel over de datasets.
* Secundaire op sleutels gebaseerde unies worden momenteel niet ondersteund.
* Het op gebied-gebaseerde identiteitsstitching proces staat voor het opnieuw teweegbrengen van identiteiten in rijen toe die op verdere voorbijgaande verslagen van identiteitskaart, zoals een authentificatieidentiteitskaart worden gebaseerd. Met dit proces kunt u verschillende records omzetten in één id voor analyse op persoonlijke niveau in plaats van op apparaat- of cookieniveau.
* Er wordt één keer per week getikt, waarbij het na de stik opnieuw wordt afgespeeld.

## Veelgestelde vragen

* Wat zijn de downstreameffecten van gegevensmodellen in Customer Journey Analytics?

   Objecten en kenmerken van hetzelfde XDM-veld worden samengevoegd in één dimensie in Customer Journey Analytics. Om veelvoudige attributen van diverse datasets in de zelfde dimensie te verenigen CJA, zouden de datasets het zelfde XDM gebied of schema moeten van verwijzingen voorzien.

## Verwante documentatie

* [Customer Journey Analytics Productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics-documentatie](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Customer Journey Analytics-zelfstudies](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
