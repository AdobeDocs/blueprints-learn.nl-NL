---
title: Vervaging van de Hub voor klantactiviteiten
description: '"[!UICONTROL Klantprofiel in realtime] raadplegingen om context voor agent-bijgewoonde steun en verkoop te verstrekken."'
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
source-git-commit: 1d286f4dabe71f359c14a88c91f306ea443646a6
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---

# Vervaging van de Hub voor klantactiviteiten

Het Vervagen van de Hub van de Activiteit van de Klant toont hoe de externe toepassingen tot Adobe Experience Platform kunnen toegang hebben [!UICONTROL Klantprofiel in realtime].

Externe toepassingen hebben toegang tot profielen met een API-GET-aanvraag. Kenmerken, gebeurtenissen, segmentlidmaatschap en modelgestuurde functies die in het profiel zijn opgeslagen, kunnen vervolgens worden gebruikt in deze externe toepassingen die geen Adobe zijn.

Met dit vermogen, kon u rijke context oppervlakte wanneer een klant uw vraagcentrum roept. De agenten van de steun zouden zicht in de levenwaarde van de klant, neiging tot kurn of blootstelling aan marketing campagnes kunnen hebben, bijvoorbeeld. De agenten van de verkoop kunnen ook van meer context of inzicht in hun klant profiteren.

>[!NOTE]
>
>De huidige latentie die door profiel raadpleging API wordt gesteund is ongeveer 500 milliseconden, die deze benadering ongeschikt maken voor integratie van het profiel met besluitvormingsmotoren in real time zoals het Web van de zelfde pagina of mobiele verpersoonlijking.

## Gevallen gebruiken

* Verbeter de context van de consument aan agent-gesteunde interactie, zoals steun en verkoopervaringen. Gebruikend het profielraadpleging in Experience Platform, kunnen de agenten meer context op de consument, zoals recente aankopen, campagneinteractie, eigenschappen, publiekslidmaatschappen, en andere attributen en inzichten ontvangen die in het klantenprofiel in real time worden opgeslagen.

## Architectuur

<img src="assets/customer_activity_hub.svg" alt="De Architectuur van de verwijzing voor de Vervaging van de Hub van de Activiteit van de Klant" style="width:80%; border:1px solid #4a4a4a" />

## Guardrails

* [Guardrails voor [!UICONTROL Klantprofiel in realtime] data](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementatiestappen

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden ingevoerd.
1. [De juiste identiteiten en naamruimten configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) op het schema om ervoor te zorgen dat ingesloten gegevens in een verenigd profiel kunnen vastmaken.
1. [De schema&#39;s en datasets voor profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html).
1. [Gegevens samenvoegen](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. [Samenvoegbeleid instellen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html).
1. Gebruik de [Entiteiten die API&#39;s gebruiken om een profielkenmerk op te zoeken](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html), hetzij van de recordentiteit of de ervaringsgebeurtenisentiteit.

## Verwante documentatie

* [Productbeschrijving van Adobe Experience Platform Activation](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL Klantprofiel in realtime] documentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=en)
* [Profielhulplijnen](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [API voor zoeken van profielen](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
