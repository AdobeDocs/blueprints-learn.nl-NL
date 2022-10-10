---
title: Journey Optimizer met Adobe Campaign-blauwdruk
description: Toont aan hoe Adobe Journey Optimizer met Adobe Campaign kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in Campagne te gebruiken
solution: Journey Optimizer, Campaign, Campaign v8, Campaign Classic v7, Campaign Standard
exl-id: 076446a9-dfb9-464c-a04f-6864b8cb7b48
source-git-commit: 6901596cbb661ffa8cf57c6ae958db1978bf1520
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 0%

---

# Journey Optimizer met Adobe Campaign

Toont aan hoe Adobe Journey Optimizer met Adobe Campaign kan worden gebruikt om berichten te verzenden door de overseinenserver in real time in Campaign te gebruiken.

<br>

## Architectuur

<img src="assets/ajo-campaign-architecture.svg" alt="Referentiearchitectuur Journey Optimizer-blauwdruk" style="width:100%; border:1px solid #4a4a4a" />

>[!IMPORTANT]
>Het gebruik van zowel Journey Optimizer als Campagne om berichten onafhankelijk van elkaar te verzenden is mogelijk, maar bevat enkele technische overwegingen die moeten worden doorgelicht. Als u deze route wilt nastreven, gelieve met uw Architect van de Onderneming van de pre-Verkoop samen te werken om ervoor te zorgen dat u een inzicht in hebt wat zal worden vereist om de implementatie te steunen.

<br>

## Vereisten

### Adobe Experience Platform

* De schema&#39;s en de datasets moeten in het systeem worden gevormd alvorens u de gegevensbronnen van Journey Optimizer kunt vormen
* Voor op klasse-gebaseerde schema&#39;s van de Gebeurtenis van de Ervaring voegen &quot;Orchestration eventID gebiedsgroep toe wanneer u een gebeurtenis teweeggebracht wilt hebben die geen op regel-gebaseerde gebeurtenis is
* Voeg voor op individuele profielklassen gebaseerde schema&#39;s de veldgroep &#39;Profielgegevens&#39; toe, zodat testprofielen kunnen worden geladen voor gebruik met Journey Optimizer
* Journey Optimizer en Campagne worden geleverd in dezelfde IMS Org

### Campagne v7/v8 of Campaign Standard

* De instantie van de uitvoering van de dienst van het overseinen in real time (d.w.z. het Centrum van het Bericht) moet door Adobe Beheerde Cloud Services worden ontvangen
* Alle bericht authoring wordt uitgevoerd binnen de Campagne-instantie zelf

<br>

## Guardrails

[Journey Optimizer Guardrails Product Link](https://experienceleague.adobe.com/docs/journeys/using/starting-with-journeys/limitations.html?lang=en)

### Extra Journey Optimizer Guardrails

* Het maximum is vandaag via API beschikbaar om ervoor te zorgen dat het bestemmingssysteem niet aan het punt van mislukking wordt verzadigd. Dit betekent dat berichten die het maximum overschrijden volledig worden verwijderd en nooit worden verzonden. Het roteren wordt niet ondersteund.
   * Max. verbindingen - maximumaantal http/s-verbindingen dat een doel kan afhandelen
   * Max. aantal oproepen - maximumaantal oproepen dat in periodInMp paramater kan worden gedaan
   * periodInMS - tijd in milliseconden
* Op gang gebrachte reizen met het lidmaatschap van een segment kunnen in twee modi worden uitgevoerd:
   * Batchsegmenten (elke 24 uur vernieuwd)
   * Streaming segmenten (&lt;5mins kwalificatie)
* Batchsegmenten - zorg dat u het dagelijkse volume van gekwalificeerde gebruikers begrijpt en ervoor zorgt dat het doelsysteem de burst-doorvoer per reis en over alle reizen kan verwerken
* Streamingsegmenten - moeten ervoor zorgen dat de eerste uitbarsting van profielkwalificaties kan worden afgehandeld samen met het dagelijks streaming kwalificatievolume per reis en over alle reizen
* Beslissingsbeheer wordt niet ondersteund
* Zakelijke gebeurtenissen worden niet ondersteund
* Uitgaande integratie in systemen van derden
   * Geen steun voor één enkele Statische IPs aangezien onze infrastructuur multi-huurder is (moet alle datacenter IPs lijsten van gewenste personen)
   * Alleen methoden voor POSTEN en PUTTEN worden ondersteund voor aangepaste handelingen
   * Verificatieondersteuning: token | wachtwoord | OAuth2
* Kan afzonderlijke componenten van Adobe Experience Platform of Journey Optimizer niet verpakken en verplaatsen tussen verschillende sandboxen. Moet opnieuw worden geïmplementeerd in nieuwe omgevingen

<br>

### Campagne-integratie

Voor hulp bij integratie met uw specifieke versie van Adobe Campaign en Adobe Journey Optimizer raadpleegt u de bijbehorende handleiding voor elke Adobe Campaign-versie.

* [Adobe Journey Optimizer &amp; Campagne v7](ajo-and-campaign-v7.md)
* [Adobe Journey Optimizer &amp; Campagne v8](ajo-and-campaign-v8.md)