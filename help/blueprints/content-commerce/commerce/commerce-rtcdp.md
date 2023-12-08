---
title: Adobe Commerce - RTCDP-vervaging
description: Adobe Experience Platform-integratie met Adobe Commerce om één weergave van klanten te maken en op intelligente wijze ervaringen aan te passen aan een digitale winkel en aan verschillende kanalen.
solution: Real-Time Customer Data Platform, Commerce
exl-id: e2fc5e1c-c865-4c24-9b82-861a34aba487
source-git-commit: 8a47b73065a5591673804301c61a73947346813c
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---

# Adobe Commerce &amp; RTCDP

De [!DNL Data Connection] Met deze extensie kunnen Adobe Commerce-klanten naadloos communiceren met Adobe Experience Platform om het profiel van de klant te verrijken en hun ervaringen op het gebied van digitale opslag en andere kanalen aan te passen.

## Technische mogelijkheden ingeschakeld

* Storefront-gegevens (clientgegevens, zoals toevoegen aan winkelwagentje, achterlaten van winkelwagentjes, enzovoort) die zijn verzameld en verzonden naar elk Adobe Experience Cloud-product.
* Status van bestelling op kantoor naar elk Adobe Experience Cloud-product
* Historische bestellingen voor back-office kunnen naar Adobe Experience Platform worden verzonden
* RTCDP-publiek delen en personaliseren naar Adobe Commerce

## Voorwaarden

Als u de opdracht [!DNL Data Connection] extensie hebt, moet u het volgende hebben:

* Adobe Commerce 2.4.4 of hoger
* Adobe ID- en organisatie-id
* Adobe Experience Platform/RTCDP
* [Adobe Client Data Layer (ACDL)](https://experienceleague.adobe.com/docs/experience-platform/tags/extensions/client/client-data-layer/overview.html). ACDL is vereist om storefront-gebeurtenisgegevens te verzamelen.

## Stappen aan boord

### Gegevensverzameling van Adobe Commerce naar Adobe Experience Platform

* [Installeren](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/install.html) de [!DNL Data Connection] extensie.
* [Aanmelden](https://helpx.adobe.com/manage-account/using/access-adobe-id-account.html) naar uw Adobe-account en weergave om uw organisatie-id te bevestigen. De organisatie-id is de id die is gekoppeld aan uw bedrijf voor het geleverde Experience Cloud. Deze id is een alfanumerieke tekenreeks van 24 tekens, gevolgd door (en moet bevatten) @AdobeOrg.
* [Maken of bijwerken](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/update-xdm.html) uw schema XDM met handel-specifieke gebiedsgroepen.
* [Een gegevensset maken](https://experienceleague.adobe.com/docs/platform-learn/implement-mobile-sdk/experience-cloud/platform.html#create-a-dataset) gebaseerd op het schema dat u hebt gemaakt of bijgewerkt. Deze dataset zal de gegevens bevatten van de Handel u verzendt.
* [Een gegevensstroom maken](https://experienceleague.adobe.com/docs/experience-platform/edge/datastreams/overview.html) en selecteer het XDM-schema dat de handel-specifieke gebiedsgroepen bevat.
* [Verbinden met de Diensten van de Handel](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html).
* [Verbinding maken met Adobe Experience Platform](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/fundamentals/connect-data.html).

### Verbinden met de Bestemming van de Handel van Adobe Experience Platform voor het Delen van het Publiek

Verbinding maken met de Adobe Commerce-bestemming:

* In de [Adobe Experience Platform-interface](https://experience.adobe.com/platform/), ga naar Doelen > Catalogus.
* Selecteer Personalisatie.
* Selecteer de Adobe Commerce-bestemming om deze te markeren en selecteer Instellen.
* Voer de stappen uit die in het dialoogvenster [zelfstudie over doelconfiguratie](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/connect-destination.html).

## Gegevens buiten vak

* Storefront-gebeurtenissen (browser/app)
* Back office evenementen
* Historische ordegegevens

Voor een volledige lijst met ondersteunde gebeurtenissen raadpleegt u [Commerce Events](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/event-forwarding/events.html)

## Architectuur

<img src="../commerce/assets/commerce_rtcdp.png" alt="Adobe Commerce RTCDP-architectuur" style="width:100%; border:1px solid #4a4a4a" class="modal-image" />

## Verwante implementatiehulplijnen

| Hulplijn | Koppeling |
|:----|:----|
| Platformaansluiting | [Overzicht Adobe Commerce Experience Platform connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/data-connection/overview.html) |
| Koopbestemming | [Adobe Commerce-verbinding in RTCDP](https://experienceleague.adobe.com/docs/experience-platform/destinations/catalog/personalization/adobe-commerce.html) |
| Edge-personalisatie | [Het publiek activeren voor verpersoonlijkingsdoelen van randen](https://experienceleague.adobe.com/docs/experience-platform/destinations/ui/activate/activate-edge-personalization-destinations.html) | |
