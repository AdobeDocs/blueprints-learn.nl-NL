---
title: Het gebeurtenis-door:sturen van meerdere sandbox gegevensinzameling
description: Leer hoe de gegevens die met het Web van het Experience Platform en Mobiele SDKs worden verzameld kunnen worden gevormd om één enkele gebeurtenis te verzamelen en aan veelvoudige zandbakken van het Experience Platform door:sturen.
solution: Data Collection
kt: 7202
source-git-commit: e9a9abeaa722bb2f9a232f4e861b1b5eae86edd1
workflow-type: tm+mt
source-wordcount: '819'
ht-degree: 0%

---


# Het gebeurtenis-door:sturen van meerdere sandbox gegevensinzameling

Deze blauwdruk toont hoe de gegevens die met het Web van het Experience Platform en Mobiele SDKs worden verzameld kunnen worden gevormd om één enkele gebeurtenis te verzamelen en aan veelvoudige zandbakken van AEP door:sturen. Deze blauwdruk is specifiek voor gegevensverzameling met meerdere sandboxen die [!UICONTROL Gebeurtenis doorsturen] om dit doel te bereiken.

Naast het repliceren van de gebeurtenis met [!UICONTROL Gebeurtenis doorsturen] kunt u de oorspronkelijk verzamelde gegevens die voldoen aan de vereisten voor andere sandboxen toevoegen, filteren of bewerken.

[!UICONTROL Gebeurtenis doorsturen] gebruikt een afzonderlijke eigenschap die het [!UICONTROL Gegevenselementen], [!UICONTROL Regels], en [!UICONTROL Extensies] nodig zijn voor uw gegevensvereisten. Met een binnenkomende gebeurtenis [!UICONTROL Gebeurtenis doorsturen] het bezit kan de gegevens verzamelen en beheren zoals nodig alvorens door:sturen.

Voor uw doelsandbox is een HTTP-streamingeindpunt vereist dat door de Adobe wordt gebruikt [!UICONTROL Cloud Connector] extensie.

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

[!UICONTROL Gebeurtenis doorsturen] wordt niet beschouwd als HIPAA Ready en mag niet worden gebruikt in HIPAA-gebruiksgevallen waarin HIPAA-gegevens worden verzameld. De voor [!UICONTROL Gebeurtenis doorsturen] wordt als HIPAA-klaar beschouwd en uitsluitend naar goeddunken van de klant. Terwijl uw [!UICONTROL Gebeurtenis doorsturen] Tageigenschap bevindt zich in het deelvenster [!UICONTROL Gebeurtenis doorsturen] het systeem, wordt de volledige verzamelde gegevens verzonden naar [!UICONTROL Gebeurtenis doorsturen] verwerkingssysteem. Het is dit proces dat [!UICONTROL Gebeurtenis doorsturen] met betrekking tot HIPAA-gebruiksgevallen. Met de volledige lading die aan wordt verscheept [!UICONTROL Gebeurtenis doorsturen] systeem, zou dit om het even welke waarden van HIPAA omvatten. Hoewel de [!UICONTROL Gebeurtenis doorsturen] De regels zullen die gegevens filtreren alvorens naar zijn bestemming te verzenden, dat het gegeven HIPAA nog wordt verscheept aan een niet HIPAA klaar infrastructuur. Nochtans, worden de ladingsgegevens nooit opgeslagen en is eenvoudig een pas door.

### Verschillende gegevensstromen en het stromen eindpunten

Als de gegevens door gegevensstromen van [!UICONTROL Platform Edge Network], bij gebruik [!UICONTROL Gebeurtenis doorsturen] naar een andere AEP-sandbox, is het vereist dat u nooit dezelfde gegevensstroom of hetzelfde streamingeindpunt gebruikt als de gegevensstroom die de oorspronkelijke verzameling maakt. Dit kan schadelijk zijn voor het AEP-exemplaar en kan een DoS-situatie veroorzaken.

### Geraamde verkeersvolumes

Verkeersvolumes zijn vereist voor herziening met elk geval van gebruik. Dit is belangrijk omdat grote volumes kunnen leiden tot een vertragingssituatie en klanten worden op de hoogte gesteld als dit gebeurt.

## Architectuur

![Meerdere sandboxen [!UICONTROL Gebeurtenis doorsturen]](assets/multi-sandbox-data-collection.png)

1. Gebeurtenisgegevens verzamelen en verzenden naar de [!UICONTROL Platform Edge Network] is vereist voor gebruik [!UICONTROL Gebeurtenis doorsturen]. Klanten kunnen Adobe-tags gebruiken voor de client of de [!UICONTROL Platform Edge Network Server-API] voor server-aan-server gegevensinzameling. De [!UICONTROL Platform Edge Network API] kan een server-aan-server inzamelingsvermogen verstrekken. Hiervoor is echter wel een ander programmeringsmodel nodig. Zie [Overzicht van Edge Network Server API](https://experienceleague.adobe.com/docs/experience-platform/edge-network-server-api/overview.html?lang=en).

1. Verzamelde ladingen worden vanuit de implementatie van tags verzonden naar de [!UICONTROL Platform Edge Network] aan de [!UICONTROL Gebeurtenis doorsturen] diensten en door haar zelf worden verwerkt [!UICONTROL Gegevenselementen], [!UICONTROL Regels] en [!UICONTROL Handelingen]. U kunt meer lezen over de verschillen tussen [Tags en [!UICONTROL Gebeurtenis doorsturen]](https://experienceleague.adobe.com/docs/experience-platform/tags/event-forwarding/overview.html?lang=en#differences-from-tags).

1. An [!UICONTROL Gebeurtenis doorsturen] eigenschap is ook vereist voor het ontvangen van verzamelde gebeurtenisgegevens van de [!UICONTROL Platform Edge Network]. Of die gebeurtenisgegevens naar het Netwerk van de Rand van het Platform door een opgestelde implementatie van Markeringen of een server-aan-server inzameling werden verzonden. Auteurs definiëren de gegevenselementen, regels en handelingen die worden gebruikt om de gebeurtenisgegevens te verrijken voordat deze naar de tweede sandbox worden doorgestuurd. Gebruik de aangepaste code [!DNL JavaScript] gegevenselement voor het structureren van uw gegevens voor het opnemen van sandboxen. In combinatie met de mogelijkheden voor prep-gegevens van Platforms hebt u verschillende opties voor het beheer van uw gegevensstructuur.

1. Momenteel wordt de Adobe gebruikt [!UICONTROL Extensie Cloud Connector] is vereist binnen de [!UICONTROL Gebeurtenis doorsturen] Eigenschap. Zodra de regels de gebeurtenisgegevens verwerken of verrijken, wordt de Verbinding van de Wolk gebruikt binnen een haalvraag die voor een POST wordt gevormd die de nuttige lading naar de tweede zandbak verzendt

1. Voor de tweede sandbox is een streamingeindpunt voor gegevensinvoer vereist. U kunt ook de mogelijkheden van de Prep van Gegevens in AEP aan hulp bij het opnemen en in kaart brengen van [!UICONTROL Gebeurtenis doorsturen] laden naar XDM. Raadpleeg de AEP-documentatie Maak een [HTTP API streamingverbinding met de gebruikersinterface](https://experienceleague.adobe.com/docs/experience-platform/sources/ui-tutorials/create/streaming/http.html?lang=en)
