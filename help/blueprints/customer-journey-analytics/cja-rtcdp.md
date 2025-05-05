---
title: Customer Journey Analytics met Real-time Customer Data Platform-blauwdruk
description: Gegevens en klantgedrag van over de klantenreis in Customer Journey Analytics verenigen en analyseren, publiek van CJA aan RTCDP publiceren
solution: Customer Journey Analytics
kt: null
thumbnail: null
exl-id: 9e1ba723-63f2-4622-ba67-f2a315c3ba0c
source-git-commit: 9fe44d93dcc05711c77ce1325b6549bb6c27a860
workflow-type: tm+mt
source-wordcount: '305'
ht-degree: 0%

---

# Customer Journey Analytics met Real-time Customer Data Platform-blauwdruk

Creeer en publiceer publiek dat in Customer Journey Analytics (CJA) aan het Profiel van de Klant in real time in Adobe Experience Platform wordt geïdentificeerd voor klant richt en verpersoonlijking. Ideaal voor het maken van soorten publiek met behulp van historische gegevens of meer verfijnde doelgroepen van korrelfilteren en berekende velden in de Customer Journey Analytics.

## Publicatiehandleiding voor publiek Customers Journey Analytics

Zie de volgende documentatie voor richtlijnen over implementatie en configuratie bij de publicatie van publiek van Customer Journey Analytics naar Real-time Customer Data Platform. [ Documentatie ](https://experienceleague.adobe.com/docs/analytics-platform/using/cja-components/audiences/publish.html?lang=nl-NL)

## Architectuur voor blauwdrukken van Customers Journey Analytics

![ diagram van de Architectuur ](assets/CJA.svg){zoomable="yes"}

## Guardrail-diagram voor blauwdrukken voor Customers Journey Analytics

* Voor gedetailleerde gidsen en eind om latentie te beëindigen verwijs naar het [ document van de plaatsingsgidsen ](../experience-platform/deployment/guardrails.md)

![ Grafiek van de Grafiek ](../experience-platform/deployment/assets/CJA_guardrails.svg){zoomable="yes"}

## Veelgestelde vragen

* Als er geen corresponderend profiel bestaat in een RTCDP-bestand dat door CJA is verzonden, wordt dan een nieuw profiel gemaakt of worden alleen publiek opgenomen van CJA voor profielen die al aanwezig zijn? Ja, er wordt een nieuw profiel gemaakt. Dientengevolge als uw implementatie RTCDP voor bekende klanten slechts is, zouden de CJA publieksregels aan filter voor slechts profielen met bekende identiteiten moeten worden geschreven. Zo voorkomt u dat het aantal RTCDP-profielen desgewenst toeneemt ten opzichte van anonieme profielen.

* Welke identiteiten verzendt CJA? CJA verzendt over welke identiteiten als &quot;persoonsidentiteitskaart&quot;tijdens configuratie CJA werden gevormd.

* Wat wordt ingesteld als de primaire identiteit? Welke identiteit de gebruiker ook selecteerde toen hij CJA als primaire &quot;persoon&quot;identiteitskaart opstelde

* Verwerkt de identiteitsdienst ook de CJA- berichten? Kan CJA bijvoorbeeld identiteiten toevoegen aan een profielidentiteitsgrafiek door het delen van het publiek? Nee, de identiteitsservice verwerkt de CJA-berichten niet.