---
title: Reisanalyse Kanaal
description: Analyseer en extraheer inzichten van klanteninteractie over de klantenreis.
solution: Experience Platform, Customer Journey Analytics, Data Collection
kt: 7208
exl-id: b042909c-d323-40d5-8b35-f3e5e3e26694
translation-type: tm+mt
source-git-commit: b0664edc3d29d693d33eefc3b3c6da8bf7308224
workflow-type: tm+mt
source-wordcount: '568'
ht-degree: 0%

---

# Blauwdruk analyse reis kanaal

Eén geconsolideerde weergave van het gedrag van klanten op verschillende kanalen hebben door gegevens van verschillende web-, mobiele en offline eigenschappen te verenigen.

## Gevallen gebruiken

* Analyseer de interacties van klanten op verschillende desktops en mobiele apparaten om het gedrag van klanten te begrijpen en inzicht te krijgen in hun ervaringen met digitale klanten.
* Analyseer de interactie van de klant over kanalen, met inbegrip van digitale en off-line kanalen zoals steuninteractie en in-store aankopen om de klantenreis beter te begrijpen en te optimaliseren. 

## Toepassingen

* Adobe Experience Platform
* Customer Journey Analytics
* Adobe Analytics (optioneel)

## Integratiepatronen

* Adobe Experience Platform → Customer Journey Analytics
* Adobe Analytics → Adobe Experience Platform → Customer Journey Analytics

## Architectuur

<img src="assets/CJA.svg" alt="Referentiearchitectuur voor de Customer Journey Analytics Blueprint" style="border:1px solid #4a4a4a" />

## Guardrails

Gegevensinname in Customer Journey Analytics:

* Gegevensopname naar meer: API ~ 7 GB/uur, bronaansluiting ~ 200 GB/uur, streaming naar meer ~ 15 minuten, Adobe Analytics-bronaansluiting naar meer ~ 45 minuten.
* Nadat er gegevens zijn gepubliceerd naar het datumpeer, kan het tot 90 minuten duren om in Customer Journey Analytics te verwerken.

## Implementatiestappen

1. Vorm datasets en schema&#39;s.
1. Gegevens opnemen in Platform.
De gegevens moeten in Platform worden opgenomen alvorens tot Customer Journey Analytics te verwerken.
1. Analyseer de gegevenssets voor kanaaloverschrijdende gebeurtenissen die worden geanalyseerd om er zeker van te zijn dat deze een gemeenschappelijke naamruimte-id hebben of opnieuw worden weergegeven via de op velden gebaseerde stitching-mogelijkheid van Customer Journey Analytics. 

   >[!NOTE]
   >
   >Customer Journey Analytics gebruikt momenteel niet het profiel van het Experience Platform of de diensten van de Identiteit voor het stitching.

1. Voer om het even welk douane gegevensvoorbereiding of gebruik van de op gebied-gebaseerde identiteit uit stitching op de gegevens om een gemeenschappelijke sleutel over tijdreeksdatasets te verzekeren die in Customer Journey Analytics moeten worden opgenomen.
1. Opzoekgegevens een primaire id geven die kan worden gekoppeld aan een veld in de gebeurtenisgegevens. Telt als rijen in licentie.
1. Stel dezelfde primaire id voor profielgegevens in als de primaire id van de gebeurtenisgegevens.
1. Configureer een gegevensverbinding om gegevens van Experience Platform tot Customer Journey Analytics in te voeren. Nadat gegevens in het datumpeer zijn geland, verwerkt het binnen 90 minuten tot Customer Journey Analytics.
1. Configureer een gegevensweergave op de verbinding om de specifieke afmetingen en metriek te selecteren die in de weergave moeten worden opgenomen. Attributie- en toewijzingsinstellingen worden ook geconfigureerd in de gegevensweergave. Deze instellingen worden tijdens het rapport berekend.
1. Creeer een project om dashboards en rapporten binnen Analysis Workspace te vormen.

## Overwegingen bij de implementatie

### Overwegingen bij het plaatsen van identiteiten

* Gegevens uit tijdreeksen die moeten worden verenigd, moeten dezelfde id-naamruimte hebben op elke record.
* Het verenigingsproces van het verenigen van verschillende datasets vereist een gemeenschappelijke primaire persoon/entiteitsleutel over de datasets.
* Secundaire op sleutels gebaseerde unies worden momenteel niet ondersteund.
* Het op gebied-gebaseerde identiteitsstitching proces staat voor het opnieuw teweegbrengen van identiteiten in rijen toe die op verdere voorbijgaande verslagen van identiteitskaart, zoals een authentificatieidentiteitskaart worden gebaseerd. Hierdoor kunnen afwijkende records op één id worden omgezet voor analyse op het niveau van de persoon in plaats van op het apparaat of cookie.
* Er wordt één keer per week getikt, waarbij het na de stik opnieuw wordt afgespeeld.

## Veelgestelde vragen

* Wat zijn de downstreameffecten van gegevensmodellen in Customer Journey Analytics?

   Objecten en kenmerken van hetzelfde XDM-veld worden samengevoegd in één dimensie in Customer Journey Analytics. Naar  Voeg veelvoudige attributen van diverse datasets in de zelfde dimensie van Customer Journey Analytics samen, zouden de datasets het zelfde XDM gebied of schema moeten van verwijzingen voorzien.

## Verwante documentatie

* [Customer Journey Analytics productbeschrijving](https://helpx.adobe.com/legal/product-descriptions/customer-journey-analytics.html)
* [Customer Journey Analytics-documentatie](https://experienceleague.adobe.com/docs/customer-journey-analytics.html)
* [Customer Journey Analytics-zelfstudies](https://experienceleague.adobe.com/docs/customer-journey-analytics-learn/tutorials/overview.html)
