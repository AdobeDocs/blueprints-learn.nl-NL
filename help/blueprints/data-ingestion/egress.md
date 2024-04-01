---
title: Blauwdruk voor gegevenstoegang en exporteren
description: Leer hoe u gegevens kunt openen en exporteren vanuit Adobe Experience Platform en toepassingen.
product: adobe experience platform
solution: Experience Platform, Journey Optimizer, Real-Time Customer Data Platform, Data Collection
exl-id: 2ca51a29-2db2-468f-8688-fc8bc061b47b
source-git-commit: 2b555728ddf570e236c0c54a8c17f85a6942618f
workflow-type: tm+mt
source-wordcount: '1838'
ht-degree: 0%

---

# Blauwdruk voor gegevenstoegang en exporteren

In het blauwdruk voor gegevenstoegang en export worden alle mogelijke methoden beschreven waarmee gegevens kunnen worden benaderd of geëxporteerd [!DNL Experience Platform] en toepassingen.

De blauwdruk is opgedeeld in twee categorieën voor gegevenstoegang van [!DNL Experience Platform] en toepassingen.

Het eerste omvat benaderingen voor het verwijderen van gegevens uit Experience Platform en toepassingen. Dit zou als een _duwen_ type methode van gegevensuitgang.

Het tweede omvat benaderingen voor toegangsgegevens van Experience Platform en toepassingen. Dit zou als een _trekken_ type methode van gegevenstoegang.

Methoden voor gegevenstoegang:

* [Toegang-API voor gebruikersprofiel in realtime](#rtcp-profile-access-api)
* [API voor gegevenstoegang](#data-access-api)
* [Query-service](#query-service)

Methoden voor het exporteren van gegevens:

* [Client Side Tags](#client-side-tags-extensions)
* [Gebeurtenis doorsturen](#event-forwarding)
* [Real-time Customer Data Platform-doelen](#RTCDP-destinations)
* [Aangepaste Journey Optimizer-handelingen](#jo-custom-actions)

## De toegang van gegevens en de architectuur van het uitvoeroverzicht

<img src="../experience-platform/assets/aep_data_flow.svg" alt="Referentiearchitectuur voor de blauwdruk voor gegevensvoorbereiding en insluiting" style="width:90%; border:1px solid #4a4a4a; margin-bottom: 15px;" class="modal-image" />

## Toegang tot gegevens en exportmethoden

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1133px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:39px; vertical-align:top; width:1133px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Streaming doelen</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Methode</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Vaak voorkomende gevallen</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protocollen</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Overwegingen</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en" style="color:#0563c1; text-decoration:underline">Gebeurtenis doorsturen</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Doorsturen van onbewerkte gegevens die zijn verzameld bij Adobe-SDK's voor analyse en verzameling naar bedrijfssystemen</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Lichtgewicht labelen voor 3<sup>rd</sup> gegevensverzameling van partijen via extensies</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Raw-gebeurtenissen op laag niveau</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Geen samenvoegings- of eerdere recordcontext toegevoegd</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=en#:~:text=containing%20profile%20exports.-,Streaming%20segment%20export%20bestemmingen,-Segment%20export%20bestemmingen" style="color:#0563c1; text-decoration:underline">RTCDP - Het stromen Segment voert uit</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activeer het publiek van RTCDP tot marketing en reclame, systemen..</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Geaggregeerde gegevens die het lidmaatschap van het publiek vertegenwoordigen</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Geen activering van onbewerkte ervaringsgebeurtenisgegevens</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-types.html?lang=en#:~:text=file%2Dbased)%20destinations-,Streaming%20profile%20export%20destinations%20(enterprise%20destinations),-IMPORTANT" style="color:#0563c1; text-decoration:underline">RTCDP - Profielen exporteren</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Gebruik RTCDP-rijke gedragsprofielen en -soorten om de ervaringen en marketing van consumenten te verbeteren.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activeer publiek- en profielkenmerken van RTCDP tot marketing en reclame, systemen die op publiek en profielkenmerken werken. </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activeer AEP-profielen voor leveranciers van e-mailservices, systemen voor het verzorgen van leads en CRM.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Geaggregeerde gegevens over publiekslidmaatschap en kenmerken van profielrecords</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Geen activering van onbewerkte ervaringsgebeurtenisgegevens</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en" style="color:#0563c1; text-decoration:underline">RTCDP - Aanpassingsdoelen</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Toegang tot het profiel van de Klant in real time in browser en cliëntervaring om cliëntzijpersonalisatie te verrijken. </span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Vereist plaatsing van WebSDK</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/destination-sdk/overview.html?lang=en" style="color:#0563c1; text-decoration:underline">RTCDP - Destination SDK</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Vorm een aangepaste bestemmingskaart in de bestemmingen RTCDP.</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Ondersteunt bestands- en streamingdoelen</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">CSV</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Staat partners en merken toe om de kaarten van de douanebestemming te vormen</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en" style="color:#0563c1; text-decoration:underline">RTCDP - Profile Lookup Hub API</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Het profiel van de toegang om de ervaringen van de consument voor agent bijgewoonde ervaringen zoals steun of verkoopagent interactie te verrijken.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Draaien</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">De raadpleging van de hub ideaal voor &gt;500ms+ gebruiksgevallen slechts</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">RTCDP - Fase API* Beta voor pagina opzoeken van profiel</span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Open het profiel aan de rand om de ervaringen van de consument in real-time &lt;200ms-ervaringen zoals personalisatie te verrijken of beslissingen op het web en mobiel aan te bieden.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Draaien</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:27px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Voor real time ervaringen en server aan serverintegratie</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:240px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en" style="color:#0563c1; text-decoration:underline">Aangepaste Journey Optimizer-handelingen</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:467px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activering van 1:1-reisgebeurtenissen en triggers om een extern systeem op de hoogte te brengen. Winkelbakken, toepassing wordt verlaten, registratie.</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">JSON</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:282px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Activering van één gebeurtenis voor een bepaald profiel. Niet voor aggregatie- of bulkbewerkingen</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>

<p> </p>

<table cellspacing="0" class="Table" style="border-collapse:collapse; width:1132px">
<tbody>
<tr>
<td colspan="4" style="background-color:#308fff; border-bottom:4px solid white; border-left:1px solid white; border-right:1px solid white; border-top:1px solid white; height:39px; vertical-align:top; width:1132px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><strong><span style="color:black">Batchbestemmingen</span></strong></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Methode</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Vaak voorkomende gevallen</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Protocollen</span></span></span></p>
</td>
<td style="background-color:#969696; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Overwegingen</span></span></span></p>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/data-access/api.html?lang=en" style="color:#0563c1; text-decoration:underline">API voor gegevenstoegang</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Toegang tot onbewerkte gegevens voor gegevenswetenschap en XML-workflows buiten het Experience Platform.</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Draaien</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Parketbestanden</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Vereist ontwikkelingsprocessen om tot parketdossiers in bruikbare datasets toegang te hebben en te verwerken</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/query/home.html?lang=en" style="color:#0563c1; text-decoration:underline">Query-service</a></span></span></span></p>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Blijft vraagresultaten van datasets, voor samengevoegde inzicht en rapportering. </span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Draaien</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">PostgreSQL </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">SQL-client</span></span></span></li>
</ul>
</td>
<td style="background-color:#cddbff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Alleen geaggregeerde gegevens. Zoeklimiet van 10 minuten.</span></span></span></li>
</ul>
</td>
</tr>
<tr>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:1px solid white; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:245px">
<p><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black"><a href="https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/export-datasets.html?lang=en" style="color:#0563c1; text-decoration:underline">Dataset exporteren* bèta</a></span></span></span></p>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:462px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">De gebeurtenisgegevens van het Experience Platform van de uitvoer voor toegang in externe rapportering, analyse, en de hulpmiddelen van de gegevenswetenschap. </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Uitvoer van samengevoegde profielinzichten en publiekslidmaatschap voor externe rapportering, analyse, en de hulpmiddelen van de gegevenswetenschap. </span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:144px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Push</span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">REST API </span></span></span></li>
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">CSV</span></span></span></li>
</ul>
</td>
<td style="background-color:#e8eeff; border-bottom:1px solid white; border-left:none; border-right:1px solid white; border-top:none; height:39px; vertical-align:top; width:281px">
<ul style="list-style-type:square">
<li><span style="font-size:12pt"><span style="font-family:Calibri,sans-serif"><span style="color:black">Momenteel in bèta, beginnend met ondergroep van datasettypes</span></span></span></li>
</ul>
</td>
</tr>
</tbody>
</table>



## Benadering voor gegevenstoegang

### Toegang-API voor gebruikersprofiel in realtime {#rtcp-profile-access-api}

Klanten kunnen toegang krijgen tot één enkel verenigd profiel vanuit de Real-time opslag van het Profiel van de Klant, met inbegrip van alle profielidentiteiten, publiekslidmaatschappen, attributen en ervaringsgebeurtenissen die de Toegang API van het Profiel van de Klant in real time gebruiken.

Zie de [Toegang-API voor gebruikersprofiel in realtime](https://experienceleague.adobe.com/docs/experience-platform/profile/api/entities.html?lang=en) aanvullende informatie.

#### Gebruik hoofdletters

* Zoek één enkel profiel om context aan de interactie van de agentenklant zoals steuninteractie door praatje en vraagcentrum, of een verkoopinteractie op het verkooppunt toe te voegen.
* Toegevoegde context toestaan aan een verpersoonlijkingsbesluit dat door een extern systeem, bijvoorbeeld een systeem van de Webverpersoonlijking of een systeem van de aanbiedingsbeslissing wordt gemaakt.

#### Overwegingen

* Klantprofiel in realtime [guardrails](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) van toepassing.
* Ontworpen voor één profielzoekopdracht tegelijk. Niet gebruikt voor bulkprofieltoegang of download van de volledige profielpopulatie voor het gebruik van analyse of gegevenswetenschap.
* De responstijd van de opzoekopdracht van het profiel wordt gekoppeld aan de profielinstructies. Eisen voor realtime lage latentie: voor dezelfde vereisten voor paginagrootte moet u het Edge-profiel gebruiken van de naar [Adobe Target-verbinding](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-target-connection.html?lang=en) of de [Aangepaste aanpassingsverbinding](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/custom-personalization.html?lang=en) voor realtime profieltoegang voor in browser en in app-personalisatie.

### API voor gegevenstoegang {#data-access-api}

De gebruikers van de API voor gegevenstoegang kunnen rechtstreeks toegang krijgen tot de onbewerkte gegevenssetbestanden die in het gegevenspeer van het Experience Platform zijn opgeslagen.

* Voor meer informatie over het gebruik van de API voor gegevenstoegang raadpleegt u de [documentatie](https://experienceleague.adobe.com/docs/experience-platform/data-access/home.html?lang=en).

#### Gebruik hoofdletters

* Trek ruwe en verwerkte gegevensdossiers van Experience Platform voor opslag en evaluatie in ondernemingsmilieu&#39;s.

#### Overwegingen

* Aangezien de gegevens op een batch asynchrone manier worden betreden, zal de toegang tot de gegevens inherent latent in vergelijking met het stromen van de benaderingen van de gegevensuitgang zoals het gebruiken van Markeringen, Gebeurtenis door:sturen, of RTCDP Doelen zijn.
* Gegevensbestanden die naar Experience Platform worden verwerkt, worden als verzamelingen van bestanden in batches opgeslagen en worden gecomprimeerd en opgeslagen in parketindeling. Als dusdanig wanneer het toegang tot van en het downloaden van de dossiers aan een verschillend milieu moeten zij systematisch door hun partij en dossier worden betreden zoals tegengesteld aan een volledige dataset en om het even welke verrichtingen op de gegevens moeten rekenschap geven voor de dossiers die in parquetformaat worden gecomprimeerd.

### Query-service {#query-service}

Gebruikend de klanten van de Dienst van de Vraag van het ervaringsplatform kunnen datasets binnen Experience Platform vragen en de resultaten van de vraag voortzetten. Een SQL Cliënt kan worden gebruikt om de vraagreactie in de gewenste opslagbestemming te vragen en voort te zetten die de SQL cliënt kan steunen. De dienst UI van de Vraag kan worden gebruikt om het SQL resultaat in een doeldataset in het Experience Platform op te slaan of de resultaten kunnen aan de lokale machine worden bewaard.

* Voor extra details over verbinding met SQL cliënten om SQL resultaten van de Dienst van de Vraag van het Experience Platform voort te zetten zie het volgende [documentatie](https://experienceleague.adobe.com/docs/experience-platform/query/clients/overview.html?lang=en).

#### Gebruik hoofdletters

* Vraag ruwe gegevens van de Experience Platform datasets en stelt de vraagresultaten voort.
* Vraag de dataset van de profielmomentopname om inzichten op het Profiel van de Klant in real time te halen. [Documentatie](https://experienceleague.adobe.com/docs/experience-platform/dashboards/query.html?lang=en#profile-attribute-datasets).
* De vraagresultaten van de opslag in een afzonderlijke dataset voor toegang of in een profiel toegelaten dataset die later door RTCDP en andere toepassingen van het Experience Cloud kan worden geïntegreerd die tot het Profiel van de Klant in real time toegang hebben.

#### Overwegingen

* Aangezien de gegevens op een batch asynchrone manier worden gevraagd, zal de toegang tot de gegevens inherent latent zijn in vergelijking met het stromen van de benaderingen van de gegevensuitgang zoals het gebruiken van Markeringen, Gebeurtenis door:sturen, of RTCDP Doelen.
* Slechts kunnen de gegevens die in het de gegevensmeer van de Experience Platform beschikbaar zijn worden gevraagd gebruikend de Dienst van de Vraag. De opslag van het Profiel van de Klant in real time, de identiteitsgrafiek, de Customer Journey Analytics kan niet direct worden gevraagd gebruikend de Dienst van de Vraag. Slechts wanneer de datasets aan het gegevenshoek worden uitgevoerd kan deze datasets worden gevraagd, zoals in het voorbeeld van de dataset van de profielmomentopname.
* Merk op dat de gidsen voor het aantal vraagresultaten en vraagonderbreking zoals die in worden geschetst van toepassing zijn [Query Services-handleidingen](https://experienceleague.adobe.com/docs/experience-platform/query/guardrails.html?lang=en) documentatie.

## Methoden voor het exporteren van gegevens

### Tagextensies aan de clientzijde {#client-side-tags-extensions}

Extensies kunnen worden geïmplementeerd met de oplossing Tags van de Adobe. Zodra een uitbreiding wordt opgesteld worden de gegevensverzoeken opgesteld direct op cliëntbrowser of toepassing en een verzoek kan worden aangehaald om gegevens en verzoeken naar de gewenste bestemming te verzenden.

Zie de [Overzicht van tags](https://experienceleague.adobe.com/docs/experience-platform/tags/home.html?lang=en) aanvullende informatie.

#### Gebruik hoofdletters

* Verzamel onbewerkte streaminggegevens rechtstreeks vanuit clientomgevingen met behulp van tags.

#### Overwegingen

* Geen directe toegang tot informatie aan de serverzijde, zoals het Experience Platform in real time het Profiel van de Klant en publieksleden.
* Als u extra labels voor gegevensverzameling aan de pagina toevoegt, kunnen de laadtijden van de pagina toenemen.
* De mogelijkheid om regels in te stellen om alleen gegevens te vragen wanneer aan bepaalde criteria wordt voldaan.
* Gegevens worden rechtstreeks van de client verzameld, waardoor de typen transformaties en verrijking worden beperkt die kunnen worden uitgevoerd voordat de gegevens worden verzameld.

### Gebeurtenis doorsturen {#event-forwarding}

Verzoeken om gegevensverzameling worden rechtstreeks bij de Adobe verzameld [!DNL Edge Network]. Van de [!DNL Edge Network] De verzoeken aan externe RESTful eindpoints kunnen worden gevormd om deze verzoeken op de externe bestemming door te sturen.

Raadpleeg het volgende: [Gebeurtenis doorsturen](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en) aanvullende informatie.

#### Gebruik hoofdletters

* Verzamel ruwe het stromen informatie van cliënt zijmilieu&#39;s aan een ondernemingseindpunt direct gebruikend de server van de Adobe gebeurtenis door:sturen.

#### Overwegingen

* Als u Gebeurtenis doorsturen wilt gebruiken, moeten gegevens naar de [!DNL Edge Network] het gebruiken van de SDK van het Web of MobileSDK.
* De methode voor het doorsturen van gebeurtenissen verkort de laadtijd en het gewicht van de pagina omdat er extra codes op de pagina worden toegevoegd.
* Er wordt momenteel geen verrijking van het randprofiel of andere gegevensbronnen ondersteund.
* Beperkte gegevensfiltering en eenvoudige toewijzingstransformaties worden ondersteund.

### Real-time Customer Data Platform-bestemmingen {#RTCDP-destinations}

De gegevens van de profielattributen en van het publiekslidmaatschap kunnen aan onderneming en reclamebestemmingen worden geactiveerd. Dit betekent dat de gegevens moeten worden opgenomen in het Experience Platform Real-time Klantprofiel.

Zie de [Real-time Customer Data Platform-doelen](https://experienceleague.adobe.com/docs/experience-platform/destinations/home.html?lang=en) aanvullende informatie.

#### Gebruik hoofdletters

* Activeer profielkenmerkinformatie, waaronder het lidmaatschap van het publiek voor een interne bedrijfsgegevensopslagruimte, analyseprogramma&#39;s, e-mailsystemen of supportsystemen.
* Activeer het lidmaatschap van het profielpubliek voor een externe advertentiemap om inhoud aan het profiel te richten en te personaliseren.

#### Overwegingen

* Profielkenmerken en publiek lidmaatschap kunnen worden geactiveerd. Gebeurtenissen met een ruwe ervaring kunnen momenteel niet worden geactiveerd als onderdeel van RTCDP-doelen.
* Activaties worden uitgevoerd in streaming of batch, afhankelijk van de aard van de segmentevaluatie en de aard van het inslieprotocollen die de bestemming accepteert.

### Aangepaste Journey Optimizer-acties {#jo-custom-actions}

Het gebruiken van de klanten van Journey Optimizer kan een douaneactie van het reiscanvas aanhalen om een lading of een bericht naar een extern API eindpunt te verzenden dat wordt gevormd. Een actie kan aan om het even welke dienst van om het even welke leverancier worden gevormd die door REST API met een JSON-Geformatteerde lading kan worden geroepen. Deze nuttige lading kan gebeurtenisinformatie, profielattributen en vroegere gebeurtenisgegevens, transformaties en verrijkingen omvatten die in de reis worden gevormd.

Zie de [Aangepaste Journey Optimizer-acties](https://experienceleague.adobe.com/docs/journey-optimizer/using/orchestrate-journeys/about-journey-building/using-custom-actions.html?lang=en) aanvullende informatie.

#### Gebruik hoofdletters

* Activeringsgebeurtenissen van Experience Platform en Journey Optimizer die aanvullende informatie van het Real-time Klantprofiel bevatten.
* Externe systemen op de hoogte stellen wanneer een klant een specifiek punt van een reis heeft bereikt.

#### Overwegingen

* Guardrails op de doorvoer ondersteund door [Journey Optimizer](https://experienceleague.adobe.com/docs/journey-optimizer/using/get-started/guardrails.html?lang=en) en door de [Klantprofiel in realtime](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en) van toepassing.
* Aangepaste acties kunnen voor elke gebeurtenis of elk profiel op een reis één voor één worden gestreamd. Bulkbewerkingen of bulkgegevensegress in de vorm van bestanden of geaggregeerde verzoeken over klantreizen kunnen niet worden uitgevoerd.
* Streaming toegang tot kenmerken van het realtime-klantprofiel en ervaringsgebeurtenissen die kunnen worden opgenomen in de activeringslading.
* Gebeurtenisgegevens kunnen worden gefilterd en eenvoudige toewijzingstransformaties kunnen worden toegepast voordat gebeurtenissen naar externe doelen worden verzonden.
