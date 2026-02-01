---
title: Toegang in realtime profiel voor support- en verkoopscenario's
description: '[!UICONTROL &#x200B; raadplegingen van het Profiel van de Klant in real time &#x200B;] om context voor agent-bijgewoonde steun en verkoop te verstrekken.'
solution: Data Collection
kt: 7195
exl-id: 3616cbf1-2e59-4e68-a1ff-1d2e3b344a1c
source-git-commit: 88a15765c0a998d49c19d9853ad0c44d6e3bfaa1
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 1%

---

# Toegang in realtime profiel voor support- en verkoopscenario&#39;s

De toegang van het Profiel in real time voor de blauwdruk van Steun en van de Scenario&#39;s van de Verkoop toont hoe de externe toepassingen tot Adobe Experience Platform [!UICONTROL &#x200B; in real time het Profiel van de Klant &#x200B;] kunnen toegang hebben.

Externe toepassingen hebben toegang tot profielen met een API GET-aanvraag. Kenmerken, gebeurtenissen, segmentlidmaatschap en modelgestuurde functies die in het profiel zijn opgeslagen, kunnen vervolgens in deze externe, niet-Adobe-toepassingen worden gebruikt.

Met dit vermogen, kon u rijke context oppervlakte wanneer een klant uw vraagcentrum roept. De agenten van de steun zouden zicht in de levenwaarde van de klant, neiging tot kurn of blootstelling aan marketing campagnes kunnen hebben, bijvoorbeeld. De agenten van de verkoop kunnen ook van meer context of insight in hun klant profiteren.

>[!NOTE]
>
>De raadpleging van het profiel op de hub is niet voorgenomen voor hoge productie, lage latentiegebruikgevallen zoals Web/mobiele binnenkomende verpersoonlijking. De raadpleging van het profiel op de hub is voorgenomen voor lagere latentiescenario&#39;s zoals agent begeleide steun of verkoopinteractie. Voor lage latentie, hoge productiescenario&#39;s zoals Web/mobiele verpersoonlijking, of het besluit van de aanbieding in real time, zou het profiel van Edge moeten worden gebruikt. Het profiel van Edge laat toegang in real time door de [&#x200B; Verbinding van Personalization van de Douane &#x200B;](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/personalization/custom-personalization) van het Platform van Gegevens van de Klant in real time toe.

## Gebruiksscenario&#39;s

* Verbeter de context van de consument aan agent-gesteunde interactie, zoals steun en verkoopervaringen. Met behulp van de profielzoekopdracht in Experience Platform kunnen agenten meer context op de consument ontvangen, zoals recente aankopen, campagneinteracties, eigenschappen, publiekslidmaatschappen en andere kenmerken en inzichten die in het profiel van de klant in real time worden opgeslagen.

## Architectuur

<img src="assets/customer_activity_hub.svg" alt="De Architectuur van de verwijzing voor de Vervaging van de Hub van de Activiteit van de Klant" style="width:90%; border:1px solid #4a4a4a"  class="modal-image" />

## Beveiligingsmechanismen

* [&#x200B; Guardrails voor [!UICONTROL &#x200B; Real-time gegevens van het Profiel van de Klant &#x200B;] &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)

## Implementatiestappen

1. [&#x200B; creeer schema&#39;s &#x200B;](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden opgenomen.
1. [&#x200B; creeer datasets &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden opgenomen.
1. [&#x200B; vorm de correcte identiteiten en de identiteit namespaces &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) op het schema om zeker te zijn dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. [&#x200B; laat de schema&#39;s en datasets voor profiel &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html) toe.
1. [&#x200B; Ingest gegevens &#x200B;](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. [&#x200B; opstelling voegt beleid &#x200B;](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/create-merge-policies.html) samen.
1. Gebruik [&#x200B; Entiteiten API om omhoog een profielattributen &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html) te kijken.

## Gerelateerde documentatie

* [&#x200B; het productbeschrijving van de Activering van Adobe Experience Platform &#x200B;](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-platform0.html)
* [[!UICONTROL &#x200B; documentatie &#x200B;] van het Profiel van de Klant in real time](https://experienceleague.adobe.com/docs/experience-platform/profile/home.html?lang=en)
* [&#x200B; Guardrails van het Profiel &#x200B;](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html)
* [&#x200B; Opzoekings API van het Profiel &#x200B;](https://www.adobe.io/apis/experienceplatform/home/api-reference.html)
