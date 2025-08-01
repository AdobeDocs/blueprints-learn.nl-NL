---
title: Experience Platform- en toepassingsinstructies
description: In de handleidingen worden de prestatieverwachtingen en de gevolgen voor de componenten en services in Adobe Experience Platform en Applications gedefinieerd
solution: Experience Platform
thumbnail: null
exl-id: b64cf3e4-cc5d-4984-8a0f-4736d432b8e1
source-git-commit: 75a0f2a77f39a4320dc4c4b0db918879be099dd3
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---


# Beveiligingsmechanismen

De gidsen weerspiegelen systeembeperkingen, verwachte latentie, en prestatiesverwachtingen om klantenarchitectuur te optimaliseren en case prestaties te gebruiken en de stabiliteit te verzekeren, fouten of onverwachte resultaten te vermijden.

## Typen ardrails

| Het type Guardrail | Beschrijving |
|---|---|
| Prestatiegarantie (Zachte limiet) | Prestatiegaranties zijn gebruikslimieten die betrekking hebben op het bereik van uw gebruiksgevallen en een overzicht van de verwachte prestaties onder normale omstandigheden. Als deze waarde wordt overschreden, kunnen de prestaties achteruitgaan en de latentie toenemen. Prestatiehandleidingen worden gedocumenteerd in de Experience League-documenten onder de secties voor elke oplossing, zoals hieronder beschreven. |
| Statische limiet (harde limiet) | Dit zijn door het systeem opgelegde beperkingen die niet mogen worden overschreden. De statische grenzen zijn typisch contractueel gebonden en geschetst in het klantencontract en de [ Beschrijvingen van het Product ](https://helpx.adobe.com/nl/legal/product-descriptions.html). |

>[!NOTE]
>
> De begeleiding is niet bedoeld om de Overeenkomsten van het Niveau van de Dienst te zijn, maar eerder begeleiding voor optimale configuraties en verwacht systeemgedrag. Alle garanties die systeem- of contractuele limieten of serviceniveau-overeenkomsten zijn, worden specifiek in de klantencontracten en productbeschrijvingen vermeld. Als u meer wilt weten over aangepaste limieten, neemt u contact op met uw medewerker van de klantenservice.

>[!NOTE]
>
> Voor gebruiksgevallen met strikte latentie- of prestatiebehoeften stelt Adobe voor de details te bespreken met uw Adobe-accountteam en uw Implementatiepartner. Elke klantenopstelling kan over de patronen van de gegevensopname, profieltellingen en rijkdom, segmentregels, en activeringskanalen variëren. Daarom is het belangrijk om uw gebruiksscenario te ontwerpen en te testen om de prestaties te optimaliseren en de verwachte prestatiekenmerken volledig te begrijpen.

## Referentiedocumentatie voor instructies voor Adobe Experience Platform en toepassingen

De volgende pagina&#39;s bevatten informatie over hulplijnen voor Adobe Experience Platform-functies, -services en -toepassingen:

**de toepassingen van Experience Platform**

* [ Real-Time CDP guardrails overzicht ](https://experienceleague.adobe.com/docs/experience-platform/rtcdp/guardrails/overview.html?lang=nl-NL)
* [ het publiek dat van Customer Journey Analytics guardrails deelt ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=nl-NL#latency)
* [ de gegevensInname van Customer Journey Analytics guardrails ](https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=nl-NL#what-is-the-expected-latency-for-analytics-data-on-platform%3F)
* [ de guardrails van Journey Optimizer ](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=nl-NL)

**de diensten van Experience Platform**

* [ de guardrails van de Inname van Gegevens ](https://experienceleague.adobe.com/docs/experience-platform/ingestion/guardrails.html?lang=nl-NL)
* [[!DNL Edge Network]  API Guardrails ](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/guardrails.html?lang=nl-NL)
* [ Realtime Gidsen van het Profiel en van de Segmentatie van de Klant ](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=nl-NL)
* [ De Grafieken van de Identiteit ](https://experienceleague.adobe.com/docs/experience-platform/identity/guardrails.html?lang=nl-NL)
* [ Guardrails van de Dienst van de Vraag ](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=nl-NL)
* [ Guardrails van de Activering van de Bestemming ](https://experienceleague.adobe.com/docs/experience-platform/destinations/guardrails.html?lang=nl-NL)

## Diagrammen met latentie van begin tot eind {#end-to-end-latency}

### Experience Platform Edge Network en Hub Primaire Waargenomen Latenties {#edge-hub-latencies}

Het volgende diagram toont de primaire rand en de hub waargenomen latentie om zich van bewust te zijn wanneer het architect gebruiksgeval op Experience Platform en Toepassingen.

![ Experience Platform [!DNL Edge Network] en hub primaire waargenomen latentie.](/help/blueprints/experience-platform/assets/aep_edge_hub_latency_v1.svg " Experience Platform Edge Network en hub primaire waargenomen latentie "){width="1000" zoomable="yes"}