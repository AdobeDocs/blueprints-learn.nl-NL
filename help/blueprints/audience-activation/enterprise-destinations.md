---
title: Activering van publiek en profiel naar streaming doelen voor bestanden en bedrijven (blauwdruk)
description: Activering van doelgroepen en profielen naar Enterprise-bestemmingen
solution: Real-Time Customer Data Platform
kt: 7475
exl-id: 32133174-eb28-44ce-ab2a-63fcb5b51cb5
source-git-commit: de447727048098ecc0bf8598fe3bca386779f543
workflow-type: tm+mt
source-wordcount: '308'
ht-degree: 3%

---

# Activering van publiek en profiel naar streaming doelen voor bestanden en bedrijven (blauwdruk)

Het profiel van het aandeel en publieksveranderingen en gebeurtenissen in het stromen of partij van [!UICONTROL  Real-time Platform van de Gegevens van de Klant ] aan de opslag en de toepassingen van ondernemingsgegevens. Deze profiel en publieksgebeurtenissen kunnen worden gebruikt om een verkoop of steunactie aan de klant zoals follow-up op een verlaten toepassingsproces of webinar registratie in werking te stellen of ondernemingstoepassingen met de recentste klantenattributen en intelligentie van [!UICONTROL  Real-time het Platform van Gegevens van de Klant ] bij te werken.

## Gebruiksscenario&#39;s

* Profiel- en publieksactivering voor cloudopslagdoelen of streamingdoelen voor het bijhouden, opslaan, analyseren en activeren van klantgegevens en -inzichten op bedrijfsniveau.

## Applicaties

* Adobe Experience Platform-activering

## Architectuur

<img src="assets/known_activation.svg" alt="Referentiearchitectuur voor het scenario van de activering van de onderneming" style="width:90%; border:1px solid #4a4a4a" class="modal-image" />


## Beveiligingsmechanismen

[ verwijs naar de guardrails zoals die op de guardrails pagina worden geschetst.](../experience-platform/deployment/guardrails.md)

## Implementatiestappen

1. [ creeer schema&#39;s ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden opgenomen.
1. [ creeer datasets ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html) voor gegevens die moeten worden opgenomen.
1. [ vorm de correcte identiteiten en de identiteit namespaces ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html) op het schema om zeker te zijn dat de ingebedde gegevens in een verenigd profiel kunnen vastmaken.
1. [ laat de schema&#39;s en datasets voor profiel ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html) toe.
1. [ Ingest gegevens ](https://experienceleague.adobe.com/?recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in Experience Platform.
1. [!UICONTROL  Realtime het 2} segment delend van de Gegevens van de Klant van de Voorziening [ in real time ](https://www.adobe.com/go/audiences) tussen Experience Platform en Audience Manager voor publiek dat in Experience Platform wordt bepaald om aan Audience Manager worden gedeeld.]
1. [ creeer segmenten ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html) in Experience Platform. Het systeem bepaalt automatisch of het segment als partij of het stromen wordt geëvalueerd.
1. [ vormt bestemmingen ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/destinations/create-destinations-and-activate-data.html) voor het delen van profielattributen en publiekslidmaatschappen aan gewenste bestemmingen.

## Gerelateerde documentatie

* [ documentatie van Doelen ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/overview.html)
* [ overzicht van de de opslagbestemmingen van de Wolk ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/cloud-storage/overview.html?lang=en#catalog)
* [ HTTP- Bestemming ](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/http-destination.html?lang=en#overview)
* ] Beschrijving van het Product ](https://helpx.adobe.com/legal/product-descriptions/real-time-customer-data-platform.html) in real time van de Gegevens van de Klant[[!UICONTROL 
* [ van het Profiel en segmentatie richtlijnen ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)
* [ documentatie van de Segmentatie ](https://experienceleague.adobe.com/docs/experience-platform/segmentation/api/streaming-segmentation.html)

## Verwante video&#39;s en zelfstudies

* ] overzicht ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/understanding-the-real-time-customer-data-platform.html) van het Platform van Gegevens in real time van de Klant[[!UICONTROL 
* [ Demo van [!UICONTROL  Real-time Platform van Gegevens van de Klant ] ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/application-services/rtcdp/demo.html)
* [ creeer segmenten ](https://experienceleague.adobe.com/docs/platform-learn/tutorials/segments/create-segments.html)
