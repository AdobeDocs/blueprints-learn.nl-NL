---
title: Adobe Experience Platform- & Applications-architectuurdiagram
description: Dit architectuurdiagram toont hoe Adobe Experience Platform op andere toepassingen en toepassingsdiensten van Adobe Experience Cloud betrekking heeft.
solution: Experience Platform, Campaign, Analytics, Target, Customer Journey Analytics, Journey Orchestration, Offer Decisioning, Real-time Customer Data Platform
kt: 7199
thumbnail: null
exl-id: 9b12cd7a-5e5f-443a-91a1-44273cdabc2d
source-git-commit: f323d2deee5547abd0ccc8247a23ac7a144b2f07
workflow-type: tm+mt
source-wordcount: '939'
ht-degree: 0%

---

# Adobe Experience Platform en toepassingen

## Adobe Experience Platform- &amp; Applications-architectuurdiagram

Dit architectuurdiagram toont hoe Adobe Experience Platform op de toepassingen en de toepassingsdiensten van Adobe Experience Cloud betrekking heeft.

<img src="assets/aep+apps_vertical.svg" alt="Experience Platform en toepassingen" style="border:1px solid #4a4a4a; width:80%;" />

>[!VIDEO](https://video.tv.adobe.com/v/32456/?quality=12&learn=on)

## Gedetailleerd architectuurdiagram voor Adobe Experience Platform en toepassingen

<img src="assets/aep+apps_horizontal.svg" alt="Experience Platform en toepassingen" style="border:1px solid #4a4a4a; width:80%;" />

## Integratie van Adobe Experience Platform- en Experience Cloud-toepassingen

<table class="relative-table wrapped" style="width: 100%;" >
   <colgroup>
    <col style="width: 16.0202%;"/>
    <col style="width: 29.3423%;"/>
    <col style="width: 33.5582%;"/>
    <col style="width: 21.0793%;"/>
  </colgroup>
  <tbody>
    <tr>
      <th>Toepassing</th>
      <th>Experience Platform naar toepassing</th>
      <th>Toepassing op Experience Platform</th>
      <th>Verwante blauwdrukken</th>
    </tr>
    <tr>
      <td colspan="1">Ad Cloud</td>
      <td colspan="1">
        <ul>
          <li>In Real-time Customer Data Platform gedefinieerde doelgroepen kunnen aan Ad Cloud worden doorgegeven voor doelgroepen via Audience Manager.</li>
        </ul>
      </td>
      <td colspan="1">Geen huidige integratie</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Anoniem Audience Activation</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online/offline Audience Activation</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activering met Experience Platform en toepassingen</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td>Analyse</td>
      <td>Geen huidige integratie</td>
      <td>
        <ul>
          <li>De gegevens die door Analytics worden verzameld kunnen naar de gegevens van het Experience Platform meer en profielopslag worden verzonden. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/analytics.html?lang=en">Gegevensconnector Analytics</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/architecture-overview/platform-data-flow.html?lang=en">Gegevensstromen Experience Platform</a>
          </li>
        </ul>
        <p>
          <br/>
        </p>
      </td>
    </tr>
    <tr>
      <td>Audience Manager</td>
      <td>
        <ul>
          <li>Soorten publiek dat in Real-time Customer Data Platform is gedefinieerd, kunnen worden gedeeld met de Audience Manager voor activering naar cookie-doelen van derden.</li>
        </ul>
      </td>
      <td>
        <ul>
          <li>Gegevens verzameld en geëvalueerd publiekslidmaatschap kunnen worden gedeeld aan de gegevens van het Experience Platform meer en profielopslag. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/audience-manager.html?lang=en">Audience Manager Source Connector</a>
          </li>
        </ul>
      </td>
      <td>
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/anonymous.html?lang=en">Anoniem Audience Activation</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online/offline Audience Activation</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activering met Experience Platform en toepassingen</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Classic</td>
      <td colspan="1">
        <ul>
          <li>In Real-time Customer Data Platform gedefinieerde doelgroepen kunnen worden gedeeld met Campaign Classic als publiek om campagnes te starten.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>De interactie en campagnegegevens die door Campaign worden verzameld kunnen aan Experience Platform als gegevensbron voor verdere gebruik in publieksopbouw via Real-time Customer Data Platform en analyse via de Dienst van de Vraag van de Customer Journey Analytics en van het Experience Platform en de Werkruimte van de Wetenschap van Gegevens worden opgenomen.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/batch-messaging.html?lang=en">Batchberichten</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Campaign Standard</td>
      <td colspan="1">
        <ul>
          <li>In Real-time Customer Data Platform gedefinieerde doelgroepen kunnen worden gedeeld met Campaign Standard als publiek om campagnes te starten.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>De interactie en campagnegegevens die door Campaign worden verzameld kunnen aan Experience Platform als gegevensbron voor verdere gebruik in publieksopbouw via Real-time Customer Data Platform en analyse via de Dienst van de Vraag van de Customer Journey Analytics en van het Experience Platform en de Werkruimte van de Wetenschap van Gegevens worden opgenomen.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/batch-messaging.html?lang=en">Batchberichten</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Customer Journey Analytics</td>
      <td colspan="1">
        <ul>
          <li>Gegevens verzameld en opgenomen in het Experience Platform data Lake worden beschikbaar gemaakt voor verwerking tot Customer Journey Analytics. </li>
        </ul>
      </td>
      <td colspan="1">Geen huidige integratie beschikbaar. De capaciteit om publieksresultaten aan Experience Platform van Customer Journey Analytics te delen is op de roadmap.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journey-analytics/overview.html?lang=en">Customer Journey Analytics</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Experience Manager</td>
      <td colspan="1">
        <ul>
          <li>Het profiel van het Experience Platform kan direct tot serverkant aan macht gepersonaliseerde ervaringen worden betreden die door Experience Manager worden geleverd. Merk op dat de verpersoonlijkingsactiviteiten meestal via Experience Manager door de integratie van het Doel worden geleverd. </li>
        </ul>
      </td>
      <td colspan="1">Geen huidige integratie, gedrag en interactie die op de plaatsen van de Experience Manager worden uitgevoerd worden verzameld direct via het Web van het Experience Platform en Mobiele SDK.</td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online/offline Audience Activation</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Journey Optimizer</td>
      <td colspan="1">
        <ul>
          <li>Gegevensgebeurtenissen en profielen die in Experience Platform worden opgenomen, worden aan Journey Optimizer ter beschikking gesteld om ritten in Journey Optimizer te starten en uit te voeren.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Interactie- en campagnegegevens die door Journey Optimizer worden geproduceerd, worden in Experience Platform verzameld voor verder gebruik in publieksopbouw via Real-time Customer Data Platform en analyse via Customer Journey Analytics, Experience Platform Query Service en Data Science Workspace.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/customer-journeys/journey-optimizer.html?lang=en">Journey Optimizer</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Magento</td>
      <td colspan="1">Geen huidige integratie</td>
      <td colspan="1">Geen huidige integratie</td>
      <td colspan="1">Geen huidige integratie</td>
    </tr>
    <tr>
      <td colspan="1">Marketo</td>
      <td colspan="1">
        <ul>
          <li>In Real-time Customer Data Platform gedefinieerde doelgroepen kunnen worden gedeeld met Marketo als publiek om Marketo-campagnes te starten en Marketo-objecten bij te werken.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Marketo-accounts, contactpersonen en opportuniteitsgegevens, samen met interactie- en campagnegegevens die door Marketo worden geproduceerd, worden in Experience Platform opgenomen voor verder gebruik in publieksopbouw via B2B-CDP en analyse via Customer Journey Analytics, Experience Platform Query Service en Data Science Workspace. <a href="https://experienceleague.adobe.com/docs/experience-platform/sources/connectors/adobe-applications/marketo/marketo.html?lang=en">Marketo Engage Connector</a>
          </li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>B2B-activering - in ontwikkeling</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Real-time CDP</td>
      <td colspan="1">
        <ul>
          <li>Gegevens die in Experience Platform worden ingevoerd en verzameld, zijn de gegevensbron voor het samenstellen van realtime klantprofielen die de Real-time Customer Data Platform van kracht maken.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>Metriek van het publiek en van het Profiel worden verzonden naar het de gegevensmeer van het Experience Platform om profielinzicht rapporterend dashboards te aandrijven.</li>
          <li>De gegevens van het Publiek en van het Profiel in het gegevensmeer kunnen voor verdere inzichten via de Dienst van de Vraag, de Werkruimte van de Wetenschap van Gegevens, en Customer Journey Analytics worden gebruikt.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online/offline Audience Activation</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activering met Experience Platform en toepassingen</a>
          </li>
        </ul>
      </td>
    </tr>
    <tr>
      <td colspan="1">Doel</td>
      <td colspan="1">
        <ul>
          <li>De in Real-time Customer Data Platform gedefinieerde doelgroepen kunnen worden gedeeld met Target en worden gebruikt in door Target geleverde verpersoonlijkings- en doelgerichte ervaringen. </li>
          <li>De directe integratie van de Rand van de Ervaring met Doel voor segmentlidmaatschap in real time en profielkenmerktoegang is op de roadmap.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>De gegevens die voor de ervaringen en de interactie van het Doel worden verzameld kunnen aan Experience Platform via het Web SDK van het Experience Platform worden verzameld. Deze gegevens kunnen worden gebruikt in publieksopbouw via de Real-time Customer Data Platform en voor analyse via Customer Journey Analytics, de Dienst van de Vraag van het Experience Platform en de Werkruimte van de Wetenschap van Gegevens.</li>
        </ul>
      </td>
      <td colspan="1">
        <ul>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/online-offline.html?lang=en">Online/offline Audience Activation</a>
          </li>
          <li>
            <a href="https://experienceleague.adobe.com/docs/blueprints-learn/architecture/audience-activation/platform-and-applications.html?lang=en">Activering met Experience Platform en toepassingen</a>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>
