---
title: Het gebeurtenis-door:sturen van meerdere sandbox gegevensinzameling
description: Leer hoe de gegevens die met het Web van het Experience Platform en Mobiele SDKs worden verzameld kunnen worden gevormd om één enkele gebeurtenis te verzamelen en aan veelvoudige zandbakken van het Experience Platform door:sturen.
solution: Data Collection
kt: 7202
exl-id: ecc94fc8-9fad-4b88-a153-3d0fc00d8d58
source-git-commit: 72eb4e2ff276279a2fc88ead0b17d77cc8e99b97
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---

# Het gebeurtenis-door:sturen van meerdere sandbox gegevensinzameling

Deze blauwdruk laat zien hoe gegevens zijn verzameld met [!DNL Experience Platform] Web en Mobiele SDKs kan worden gevormd om één enkele gebeurtenis te verzamelen en aan veelvoudige zandbakken door:sturen AEP. Deze blauwdruk is specifiek voor gegevensverzameling met meerdere sandboxen die [!UICONTROL Gebeurtenis doorsturen] om dit doel te bereiken.

Naast het repliceren van de gebeurtenis met [!UICONTROL Gebeurtenis doorsturen] kunt u de oorspronkelijk verzamelde gegevens die voldoen aan de vereisten voor andere sandboxen toevoegen, filteren of bewerken.

[!UICONTROL Gebeurtenis doorsturen] gebruikt een afzonderlijke eigenschap die de eigenschap [!UICONTROL Gegevenselementen], [!UICONTROL Regels], en [!UICONTROL Extensies] nodig zijn voor uw gegevensvereisten. Met een binnenkomende gebeurtenis [!UICONTROL Gebeurtenis doorsturen] het bezit kan de gegevens verzamelen en beheren zoals nodig alvorens door:sturen.

Uw doelsandbox vereist een HTTP-streamingeindpunt dat door de Adobe wordt gebruikt [!UICONTROL Cloud Connector] extensie.

## Gebruik hoofdletters

* Globale gegevensrapportage - Bij het gebruik van meerdere sandboxen om besturingsomgevingen te isoleren en de noodzaak om gegevensverzameling te consolideren naar één sandbox voor cross-sandboxrapportage. Het verpletteren van een Gebeurtenis van de Rand van de Ervaring door [!UICONTROL Gebeurtenis doorsturen] naar een rapportsandbox kan elke sandbox-besturingsomgeving gegevens verzenden terwijl deze in real-time worden verzameld naar een rapportsandbox.

* De gegevensverzameling in verschillende sandboxen beheren op basis van verschillende gegevensregels voor elke sandbox-besturingsomgeving.

## Toepassingen

* [!DNL Experience Platform] Gegevensverzameling
* [!UICONTROL Gebeurtenis doorsturen]
* AEP [!UICONTROL Extensie]
* [!UICONTROL Extensie Cloud Connector]

## Overwegingen

Met [!UICONTROL Gebeurtenis doorsturen] als benadering van het verzenden van gegevens naar veelvoudige zandbakken, zijn er overwegingen die met uw oplossingsarchitectuur moeten worden in overweging genomen.

### Geen HIPAA-gegevens

[!UICONTROL Gebeurtenis doorsturen] wordt niet beschouwd als HIPAA Ready en mag niet worden gebruikt in HIPAA-gebruiksgevallen waarin HIPAA-gegevens worden verzameld.

De infrastructuur die voor [!UICONTROL Gebeurtenis doorsturen] wordt beschouwd als HIPAA-klaar en is uitsluitend naar goeddunken van de klant. Terwijl uw [!UICONTROL Gebeurtenis doorsturen] Tageigenschap bevindt zich in het deelvenster [!UICONTROL Gebeurtenis doorsturen] het systeem, wordt de volledige verzamelde gegevens verzonden naar [!UICONTROL Gebeurtenis doorsturen] verwerkingssysteem. Dit proces maakt [!UICONTROL Gebeurtenis doorsturen] met betrekking tot HIPAA-gebruiksgevallen. Met de volledige lading die aan wordt verscheept [!UICONTROL Gebeurtenis doorsturen] systeem, zou dit proces om het even welke waarden van HIPAA omvatten. Hoewel de [!UICONTROL Gebeurtenis doorsturen] De filter van regels die gegevens voorafgaand aan het verzenden naar zijn bestemming, dat het gegeven HIPAA nog wordt verscheept aan een niet-HIPAA-Klaar infrastructuur. Nochtans, worden de ladingsgegevens nooit opgeslagen en is eenvoudig een doorgang.

### Verschillende gegevensstromen en het stromen eindpunten

Als de gegevens door gegevensstromen van [!DNL Platform Edge Network], bij gebruik [!UICONTROL Gebeurtenis doorsturen] naar een andere AEP-sandbox, is het vereist dat u nooit dezelfde gegevensstroom of hetzelfde streamingeindpunt gebruikt als de gegevensstroom die de oorspronkelijke verzameling maakt. Dit kan schadelijk zijn voor het AEP-exemplaar en kan een DoS-situatie veroorzaken.

### Geraamde verkeersvolumes

Verkeersvolumes zijn vereist voor herziening met elk geval van gebruik. Dit is belangrijk omdat grote volumes kunnen leiden tot een vertragingssituatie en klanten worden op de hoogte gesteld als dit gebeurt.

## Architectuur

![Multisandbox [!UICONTROL Gebeurtenis doorsturen]](assets/multi-sandbox-data-collection.png)

1. Gebeurtenisgegevens verzamelen en verzenden naar de [!DNL Platform Edge Network] is vereist voor gebruik [!UICONTROL Gebeurtenis doorsturen]. U kunt Adobe-tags gebruiken voor de client of de [!DNL Platform Edge Network Server API] voor server-aan-server gegevensinzameling.

   De [!DNL Platform Edge Network API] kan een server-aan-server inzamelingsvermogen verstrekken. Hiervoor is echter een ander programmeringsmodel nodig. Zie [Overzicht van Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en).

1. Verzamelde ladingen worden vanuit de implementatie van tags verzonden naar de [!DNL Platform Edge Network] aan de [!UICONTROL Gebeurtenis doorsturen] diensten en door haar zelf worden verwerkt [!UICONTROL Gegevenselementen], [!UICONTROL Regels], en [!UICONTROL Handelingen]. Zie voor meer informatie over de verschillen [Tags en [!UICONTROL Gebeurtenis doorsturen]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. An [!UICONTROL Gebeurtenis doorsturen] eigenschap is ook vereist voor het ontvangen van verzamelde gebeurtenisgegevens van de [!DNL Platform Edge Network], of die gebeurtenisgegevens naar de [!DNL Platform Edge Network] door een opgesteld implementatie van Markeringen of een server-aan-server inzameling.

   Auteurs definiëren de gegevenselementen, regels en handelingen die worden gebruikt om de gebeurtenisgegevens te verrijken voordat deze naar de tweede sandbox worden doorgestuurd. Gebruik de aangepaste code [!DNL JavaScript] gegevenselement voor het structureren van uw gegevens voor het opnemen van sandboxen. In combinatie met de mogelijkheden voor platformgegevensprep beschikt u over verschillende opties voor het beheer van uw gegevensstructuur.

1. Momenteel wordt de Adobe gebruikt [!UICONTROL Extensie Cloud Connector] is vereist binnen de [!UICONTROL Gebeurtenis doorsturen] Eigenschap. Nadat de regels de gebeurtenisgegevens verwerken of verrijken, [!UICONTROL Cloud Connector] wordt gebruikt binnen een haalvraag die voor een POST wordt gevormd, die de nuttige lading naar de tweede zandbak verzendt.

1. Voor de tweede sandbox is een streamingeindpunt voor gegevensinvoer vereist. U kunt ook [!UICONTROL Gegevensprep] mogelijkheden in AEP om te helpen bij het opnemen en in kaart brengen van [!UICONTROL Gebeurtenis doorsturen] laden naar XDM. Raadpleeg de AEP-documentatie Maak een [HTTP API streamingverbinding met de gebruikersinterface](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=en)
