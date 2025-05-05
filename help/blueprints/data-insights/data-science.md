---
title: Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking
description: Leer hoe u op wetenschap gebaseerde inzichten in gegevens kunt opnemen [!DNL Experience Platform] om het profiel van de Klant in real time te verrijken.
solution: Data Collection
kt: 7203
exl-id: e5ec6886-4fa4-4c9b-a2d8-e843d7758669,f0efaf3c-6c4f-47c3-ab8a-e8e146dd071c
source-git-commit: 7f3bc307f74aa88a7a73f3e50cc48bd16f58b37f
workflow-type: tm+mt
source-wordcount: '455'
ht-degree: 0%

---

# Aangepaste gegevenswetenschap voor blauwdruk van profielverrijking

De aangepaste gegevenswetenschap voor profielverrijkingsblauwdruk illustreert hoe gegevens kunnen worden gebruikt om modellen te trainen, te implementeren en te scoren om machinaal leerinzicht te bieden in [!DNL Experience Platform] en de [!DNL Real-Time Customer Data Platform] van hulpmiddelen voor het leren van gegevens en machines.

Modelleerde inzichten kunnen worden opgenomen in [!DNL Experience Platform] om het profiel van de klant in real time te verrijken. Voorbeelden van leerinzicht in machines zijn levenslange waardeschaling, product- en categoriaffiniteit, conversiesnelheid of churn.

## Gebruik hoofdletters

* Haal inzicht uit en ontdek patronen van klantengegevens, trein en score modellen van deze gegevens.
* Verrijken de [!UICONTROL Klantprofiel in realtime] met modelgestuurde inzichten en kenmerken voor meer korrelige personalisatie en geoptimaliseerde reizen.
* Train- en Score-modellen om de inzichten van klanten te bepalen, zoals de levenslange waarde van de klant, de neiging om te converteren of te klonen, de affiniteit van producten en inhoud, en servicescore.

## Architectuur

<img src="assets/data_science.svg" alt="Referentiearchitectuur voor de Custom Data Science for Profile Enrichment Blueprint" style="width:90%; border:1px solid #4a4a4a" />

## Guardrails

* Voor gedetailleerde instructies en end-to-end latentie bij het inslikken van gegevens resulteert wetenschap in [!DNL Experience Platform] en het Real-time Klantprofiel verwijst naar de instructies voor gegevensinvoer en het latentiediagram waarnaar wordt verwezen in het [document met implementatiehandleidingen](../experience-platform/deployment/guardrails.md).

## Implementatiestappen

1. [Schema&#39;s maken](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2021.1.xdm) voor gegevens die moeten worden ingevoerd.
1. [Gegevenssets maken](https://experienceleague.adobe.com/docs/platform-learn/tutorials/data-ingestion/create-datasets-and-ingest-data.html?lang=nl-NL) voor gegevens die moeten worden ingevoerd.
1. [Samenvattingsgegevens](https://experienceleague.adobe.com/?lang=nl&recommended=ExperiencePlatform-D-1-2020.1.dataingestion) in [!DNL Experience Platform].

Voor modelresultaten die in het Profiel van de Klant in real time moeten worden opgenomen ben zeker om het volgende te doen alvorens gegevens in te voeren:

1. [De juiste identiteiten en naamruimten configureren](https://experienceleague.adobe.com/docs/platform-learn/tutorials/identities/label-ingest-and-verify-identity-data.html?lang=nl-NL) op het schema om ervoor te zorgen dat ingesloten gegevens in een verenigd profiel kunnen vastmaken.
1. [De schema&#39;s en datasets voor profiel inschakelen](https://experienceleague.adobe.com/docs/platform-learn/tutorials/profiles/bring-data-into-the-real-time-customer-profile.html?lang=nl-NL).

## Implementatieoverwegingen

* In de meeste gevallen moet het modelresultaat worden opgenomen als profielkenmerken en hoeven er geen gebeurtenissen te worden ervaren. De modelresultaten kunnen eenvoudige kenmerktekenreeksen zijn. Als er meerdere modelresultaten zijn die moeten worden opgenomen, is het raadzaam een array- of kaarttekstveld te gebruiken.
* De gegevensset met momentopnamen voor dagelijkse profielen, die een dagelijkse export is van de gegevens van de verenigde profielkenmerken, kan worden gebruikt om modellen voor profielkenmerkgegevens op te leiden. De document van de de momentopnamesdataset van het profiel kan worden betreden [hier](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=nl-NL#profile-attribute-datasets).
* Voor het extraheren van gegevens uit [!DNL Experience Platform] de volgende methoden kunnen worden gebruikt
   * SDK voor gegevenstoegang
      * Gegevens worden opgeslagen in Raw-bestandsformulier
      * De gebeurtenisgegevens van de profielervaring blijven in onverenigde onbewerkte toestand staan.
   * RTCDP-doelen
      * Profielkenmerken en segmentlidmaatschappen kunnen worden ingedrukt.

## Gerelateerde documentatie

* [Adobe [!DNL Experience Platform] Omschrijving van het inlichtingenproduct](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-experience-platform-intelligence---product-description.html)
* [Adobe [!DNL Experience Platform] Query-service](https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=nl-NL)

## Gerelateerde blogberichten

* [AI voor inhoud en handel: uw interactie met klanten aanpassen via Inhoudsintelligentie](https://medium.com/adobetech/content-and-commerce-ai-personalizing-your-interactions-with-customers-through-content-intelligence-dc182601deab)
* [Een Inleiding bekijkt de Verkennende Analyse van Gegevens over Adobe [!DNL Experience Platform]](https://medium.com/adobetech/an-introductory-look-at-exploratory-data-analysis-on-adobe-experience-platform-1bfce7501d9a)
* [De producten van de Ervaring van de Adobe met de Leermachine aan Verhoogde Ervaring van de Gebruiker](https://medium.com/adobetech/cutting-across-adobe-experience-products-with-machine-learning-to-elevated-user-experience-7c85000510d1)
* [Segmentation.AI: Automated Audience-Clustering-as-a-Service in Adobe [!DNL Experience Platform]](https://medium.com/adobetech/segmentation-ai-automated-audience-clustering-as-a-service-in-adobe-experience-platform-261f4099462c)