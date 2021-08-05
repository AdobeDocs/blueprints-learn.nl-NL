---
title: Activering publiek en profiel
description: Zorg voor activering van het publiek en profilering van centrale klantervaringen met Real-time ​ van klantgegevens.
solution: Experience Platform, Real-time Customer Data Platform
kt: null
thumbnail: null
exl-id: eeeb4325-d0e8-4fd8-86ab-0b8afdd0b69f
source-git-commit: 8f1d76c317dbe4c7e916b4513960b4549a2d3424
workflow-type: tm+mt
source-wordcount: '970'
ht-degree: 0%

---


# Activering publiek en profiel

Activering van publiek en profiel is de sleutel tot succes in een wereld van gegevensgestuurde marketing. Veel merken richten zich echter nog steeds op activering via het kanaal, wat vaak leidt tot inconsistente bereikbaarheid en personalisatie.

Met een kanaal-eerste benadering, handelt elk kanaal als silo waarin de verpersoonlijkingsinspanningen slechts de klanten richten die met het merk op dat kanaal interactie aangaan. Deze benadering weerspiegelt niet de realiteit dat klanten op verschillende aanraakpunten met merken communiceren. Activering van publiek en profiel maakt het voor merken mogelijk om klanteninteracties via meerdere kanalen te verbinden, zodat zij een gecentraliseerd profiel en publiek leveren dat op alle kanalen kan worden geactiveerd.

| Blauwdruk | Beschrijving | Experience Cloud-toepassingen |
|---|---|---|
| **[Anoniem Audience Activation](anonymous.md)** | <ul><li>Doelpubliek via internet en reclamekanalen voor anonieme en gedragsgegevens van klanten.</li><li>Integreren met publieksgegevens van derden voor een betere personalisatie.</li></ul> | <ul><li>Adobe Audience Manager</li></ul> |
| **[Activering met online en offline gegevens](online-offline.md)** | <ul><li>Activeer naar bekende, op profielen gebaseerde bestemmingen, zoals e-mailproviders, sociale netwerken en reclamebestemmingen. </li><li>Gebruik offlinekenmerken en -gebeurtenissen, zoals offlinebestellingen, transacties, CRM of loyaliteitsgegevens, samen met onlinegedrag voor het online aanwijzen en personaliseren.</li></ul> | <ul><li>Adobe Experience Platform</li><li> [!UICONTROL Real-time Platform voor klantgegevens]</li><li>Adobe Audience Manager (optioneel)</li></ul> |
| **[Activering voor streaming van bestanden en bedrijven](enterprise-destinations.md)** | <ul><li>Replicatie en update van profiel- en publiekswijzigingen naar bedrijfsgegevensopslagsystemen voor activering en rapportage van gebruiksgevallen. </li></ul><ul><li>Een verkoop- of ondersteuningsactie aan de klant initiëren via een kennisgeving van een actie van de klant van het [!UICONTROL Real-time Platform van klantgegevens] aan bedrijfssystemen en toepassingen.</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Real-time Platform voor klantgegevens]</li><li>Experience Platform activeren</li><li>Adobe Audience Manager (optioneel)</li></ul> |
| **[Activering van publiek en profiel met Experience Cloud-toepassingen](platform-and-applications.md)** | <ul><li>Profielen en publiek in Experience Platform beheren en deze delen met Experience Cloud-toepassingen</li><li>Bouw en deel rijke klantensegmenten en inzichten in Experience Platform en deel hen met de Toepassingen van de Experience Cloud</li></ul> | <ul><li>Adobe Experience Platform</li><li>[!UICONTROL Real-time Platform voor klantgegevens]</li><li>Experience Platform activeren</li><li>Experience Cloud-toepassingen</li></ul> |
| **[Hub voor klantactiviteiten](customer-activity.md)** | <ul><li>Verbeter de context van de consument aan agent-gesteunde interactie, zoals steun en verkoopervaringen. Gebruikend het profielraadpleging in Experience Platform, kunnen de agenten meer context over de consument, zoals recente aankopen, campagneinteractie, eigenschappen, publiekslidmaatschappen, en andere attributen en inzichten ontvangen die in het klantenprofiel in real time worden opgeslagen.</li></ul> | <ul><li>Adobe Experience Platform</li></ul> |

## Architectuur van het Profiel van de Klant in real time

In de onderstaande afbeelding worden de kernonderdelen van het realtime klantprofiel van het Experience Platform beschreven.

<img src="assets/profile_architecture.jpg" alt="Referentiearchitectuur voor het Real-time Klantprofiel" style="border:1px solid #4a4a4a" width="90%"/>

De eerste gegevensbronnen worden opgenomen in Experience Platform. Als de gegevensbron voor profielverwerking wordt gevormd zal het in het Profiel van de Klant in real time voeren. Er wordt één profielfragment of document gemaakt voor elke gegevensbron en elke primaire id-record die voor elke gegevensbron is geconfigureerd. Aangezien gegevens aan het profiel worden toegevoegd, worden deze ook verwerkt door de identiteitsservice. Om het even welk verslag van de gegevensbronnen die meer dan één identiteit duidelijk in het schema en met de overeenkomstige waarden hebben die in het verslag worden bevolkt zal als identiteitsverhouding binnen de identiteitsdienst worden verwerkt.

Merk op dat de verslagen die slechts één identiteit hebben niet door de identiteitsdienst worden verwerkt aangezien dergelijke verslagen geen identiteitsverbindingen hebben om de grafiek met verder te bevolken. De identiteitsdienst maakt geen onderscheid tussen primaire identiteiten en secundaire identiteiten. Het is gewoon het verwerken van identiteitsrelaties tussen identiteiten.

Het samenvoegen van profielfragmenten gebeurt als de identiteitsgrafiek de relaties tussen de verschillende bronprofielfragmenten biedt die verwant zijn. Het samenvoegbeleid bepaalt welke bronfragmenten en welke identiteitsgrafiek wordt gebruikt als de fragmenten worden samengevoegd. Telkens wanneer het profiel wordt geopend, wordt de samenvoeging van de profielfragmenten uitgevoerd om ervoor te zorgen dat de meest recente gecombineerde weergave van het profiel is. Regels voor bestuur en beleid zorgen ervoor dat alleen de toegestane segmenten en kenmerken kunnen worden geactiveerd voor de opgegeven doelen.

## Overzicht van segmentatie en bestemming

In de onderstaande afbeelding worden de verschillende segmentatiemethoden en de verschillende activeringspatronen voor profielen en doelgroepen beschreven.

<img src="assets/segmentation_destination_overview.png" alt="Referentiearchitectuur voor het Real-time Klantprofiel" style="border:1px solid #4a4a4a" width="90%"/>

## Instructies voor doelgroep en activering van profiel

* [Richtlijnen voor profiel en segmentatie](https://experienceleague.adobe.com/docs/experience-platform/profile/guardrails.html?lang=en)


### Kenmerken en identiteiten activeren

* [!UICONTROL Het ] platform van de Gegevens van de Klant in real time kan publiekslidmaatschappen evenals attributen en identiteitsveranderingen activeren die voor profielen voorkomen die leden van segmenten zijn die voor activering worden geselecteerd. Als u attributen of identiteiten wilt activeren, moet u een globaal segment definiëren dat alle profielen bevat waarnaar kenmerken en identiteitsupdates worden verzonden. Op dat punt, kunt u het segment en gewenste attributen selecteren om als deel van de bestemmingsconfiguratie te activeren.
* Merk op dat de partijbestemmingen activering van attribuut-slechts veranderingsgebeurtenissen niet steunen. Het volledige of stijgende publiekslidmaatschap kan samen met de geselecteerde attributen voor activering worden verzonden, maar u kunt geen attribuut-enige veranderingsgebeurtenissen via partijbestemmingen activeren.

### Batchsegmenten activeren voor streamingdoelen

* Activering van batchsegmenten naar streaming doelen wordt ondersteund. De banen van het segment van de partij plaatsen berichten op de pijpleiding zodra de segmentbaan voor het stromen activering volledig is

### Streaming segmenten activeren naar batchbestemmingen

* Activering van streaming segmenten naar batchbestemmingen wordt ondersteund. Het de segmentlidmaatschap van de de uitvoer van het de partijbestemmingsprogramma van de uitvoer op het programma van de partijbestemming wordt gebaseerd. Dit omvat zowel segmentlidmaatschap dat via het stromen en partijmethodes wordt bepaald.

### Activering van ervaringsgebeurtenissen

* Het activeren van gebeurtenissen voor onbewerkte ervaring wordt niet ondersteund. Om tegen ervaringsgebeurtenissen te activeren, moet een segment met de noodzakelijke regels worden gecreeerd die de logica van de ervaringsgebeurtenis omvatten of uitsluiten. Dit leidt tot een segment dat tegen ervaringsgebeurtenissen wordt bepaald, en het segmentlidmaatschap kan als volmacht voor het activeren van ruwe ervaringsgebeurtenissen worden geactiveerd. Overweeg ook het gebruik van [!UICONTROL Server Side starten] om onbewerkte ervaringsgebeurtenissen te activeren die via SDK zijn verzameld.


## Verwante blogberichten

* [[!DNL Blueprints for Audience Activation in Adobe Experience Platform]](https://medium.com/adobetech/a-blueprint-for-audience-activation-in-adobe-experience-platform-b2b30fae90fd)
* [[!DNL How Adobe Experience Platform Predictive Audiences improves Personalized Experiences]](https://medium.com/adobetech/how-adobe-experience-platform-predictive-audiences-improves-personalized-experiences-1f75a60cb7a3)
* [[!DNL Adobe Experience Platform Web SDK for Audience Management]](https://medium.com/adobetech/adobe-experience-platform-web-sdk-for-audience-management-751fa6d063bc)
