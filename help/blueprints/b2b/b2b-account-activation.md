---
title: B2B-account activeren naar Advertising-doelen en -bestandsdoelen
description: Gebruik een op account gebaseerde betrokkenheid om een publiek te maken en dit via doelen te richten.
solution: Real-Time Customer Data Platform
source-git-commit: 074edca2f061459935d5f8b5e59e8cbd69b0fe4f
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 1%

---

# B2B-account activeren voor advertentiedoelen en bestandsdoelen

Door middel van een op account gebaseerde betrokkenheid kunnen B2B-marketers een publiek van accounts maken (d.w.z. lijsten van bedrijven) en zich richten op die bedrijven via bestemmingen als LinkedIn die lijsten van bedrijven accepteren als input of export naar cloudopslagbestemmingen voor het zoeken naar doelen en verkopen.

## Gebruiksscenario&#39;s

Marketers kunnen drie belangrijke gebruiksgevallen ontgrendelen door op hun account gebaseerde betrokkenheid:

* **Vul het kopen groepshiaten:** Een teller kan op rekeningen adverteren waar zij nog geen contacten voor de rollen van CMO of CIO hebben. Zij kunnen eerst een publiek van rekeningen zonder een contact met de titel &quot;CMO&quot;of &quot;CIO&quot;bouwen en dan het publiek op LinkedIn activeren. Binnen de bestemming, LinkedIn, kunnen zij een campagne lanceren die op dat publiek en specifieke mensen met &quot;CMO&quot;of &quot;CIO&quot;baantitels richt om deze nieuwe contacten te bereiken en de voordelen van hun dienstenaanbod te benadrukken.
* **Upsell of dwars-verkoopt aan andere afdelingen van een bedrijf dat een bestaande klant is:** Een marktleider kan een rekeningspubliek bouwen dat product X tussen 3 en 9 maanden geleden maar nog niet het product Y kocht. Vervolgens kunnen ze het programma activeren en de voordelen van product Y voor dat doelpubliek benadrukken.
* **de bedrijven van het doel die concurrerende producten gebruiken:** A de marktleider kan aan rekeningen in de handel brengen om de producten van een concurrent, zelfs zonder enige contacten bij die rekeningen te verplaatsen. Zij kunnen een publiek van rekeningen tot stand brengen die op partnergegevens worden gebaseerd die eigendom of gebruik van het product van een concurrent tonen, dan via LinkedIn activeren om contacten bij doelrekeningen voor uitbreiding te bron.

## Applicaties

* Real-time Customer Data Platform B2B Edition

## Integratiepatronen

* B2B-gegevensbronnen (Marketo, Salesforce, enz.) -> Real-time Customer Data Platform B2B Edition -> Doelen.
* Verschillende B2B-gegevensbronnen kunnen worden gebruikt om account-, lead-, opportunity- en personengegevens toe te wijzen aan de B2B Edition van Real-time Customer Data Platform.

## Architectuur

![ architectuur van de Verwijzing voor de Vervaging van het Audience Activation van de Rekening B2B ](assets/b2b-blueprint-account-audience-activation.png)

## Doelstellingen voor accountpubliek

* (Bedrijven) LinkedIn Gelijktijdig publiek
* Cloud Storage-bestemmingen
   * Azure Data Lake
   * Gegevenslandingszone
   * SFTP
   * Azure Blob
   * AWS S3

## Beveiligingsmechanismen

* Maximaal 50 accountsegmenten per sandbox.
* Evaluatie van batchsegmentatie.
   * Automatisch om de 24 uur na voltooiing van de batchdoelrun en profielexporttaken evalueren.
   * Geen ondersteuning voor randen, streaming of ad-hocevaluaties.
* Accountkenmerken kunnen worden geëxporteerd.
* Gebeurtenissen van mensen.
   * Tot 30 dagen van gebeurtenis terugblik, bepaalt geen het ordenen van gebeurtenis.
   * AND/OR worden ondersteund (dus je kunt zeggen: &quot;A en B moeten gebeuren&quot;,  maar je kunt niet zeggen: &quot;A moet 3 dagen voor B gebeuren&quot;).
* Voor de bestemmingen van de wolkenopslag, steunt het uitvoerprogramma de &quot;Na segmentevaluatie&quot;optie.
* [ B2B het Profiel &amp; de Gidsen van de Segmentatie ](https://experienceleague.adobe.com/nl/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails).

## Implementatiestappen voor Real-time Customer Data Platform B2B Edition, het maken van een accountpubliek en activering

* Voor implementatiestappen van de Uitgave van Real-time Customer Data Platform B2B, zie [ Begonnen het worden met Real-time Customer Data Platform B2B Editiond ](https://experienceleague.adobe.com/nl/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial) documentatie.
* Voor de stappen van de Aanmaak van het Publiek van de Rekening, zie de [ documentatie van het publiek van de Rekening ](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/account-audiences).
* Voor de stappen van het Audience Activation van de Rekening, zie [ accountpubliek ](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-account-audiences) documentatie activeren.
   * Vereiste toewijzing voor [ (Bedrijven) de Gelijke bestemming van het publiek van LinkedIn ](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings).

## Implementatieoverwegingen

LinkedIn heeft een aantal vereisten waaraan iedereen moet voldoen, waaronder de minimale doelgrootte van 300 overeenkomende leden. Als het accountpubliek dat voor de gekoppelde overeenkomende doelgroep van het bedrijf is geactiveerd, niet aan de vereiste voldoet, moet de publieksdefinitie worden gewijzigd om het publiek groter te maken om een LinkedIn-campagne te starten.

## Verwante documentatie

* [ B2B Uitgave van Real-time Customer Data Platform ](https://experienceleague.adobe.com/nl/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [ creeer en activeer de Video van het Leerprogramma van het Publiek van de Rekening ](https://experienceleague.adobe.com/nl/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [ creeer de Soorten van de Rekening ](https://experienceleague.adobe.com/nl/docs/experience-platform/segmentation/ui/account-audiences)
* [ activeer de Soorten van de Rekening ](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [ Adobe Experience Platform - de Schakelaar van de Bestemming van LinkedIn ](https://experienceleague.adobe.com/nl/docs/experience-platform/destinations/catalog/social/linkedin)
