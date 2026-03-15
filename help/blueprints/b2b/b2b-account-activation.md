---
title: B2B-account activeren naar Advertising-doelen en -bestandsdoelen
description: Gebruik een op account gebaseerde betrokkenheid om een publiek te maken en dit via doelen te richten.
solution: Real-Time Customer Data Platform
exl-id: 578c0019-6133-4508-ae9d-8a8a463376f0
source-git-commit: a632042b3a7434dd88f52804e15e30fa06057e3b
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---

# B2B-account activeren voor advertentiedoelen en bestandsdoelen

Met een op account gebaseerde betrokkenheid kunnen B2B-marketers een publiek van accounts maken (d.w.z. lijsten van bedrijven) en die bedrijven richten via bestemmingen als LinkedIn die lijsten van bedrijven accepteren als input of export naar cloudopslagbestemmingen voor het zoeken naar doelen en verkopen.

## Gebruiksscenario&#39;s

Marketers kunnen drie belangrijke gebruiksgevallen ontgrendelen door op hun account gebaseerde betrokkenheid:

* **Vul het kopen groepshiaten:** Een teller kan op rekeningen adverteren waar zij nog geen contacten voor de rollen van CMO of CIO hebben. Zij kunnen eerst een publiek van rekeningen zonder een contact met de titel &quot;CMO&quot;of &quot;CIO&quot;bouwen en dan het publiek op LinkedIn activeren. Binnen de bestemming, LinkedIn, kunnen zij dan een campagne lanceren gericht op dat publiek en specifieke mensen met &quot;CMO&quot;of &quot;CIO&quot;baantitels om deze nieuwe contacten te bereiken en de voordelen van hun dienstenaanbod te benadrukken.
* **Upsell of dwars-verkoopt aan andere afdelingen van een bedrijf dat een bestaande klant is:** Een marktleider kan een rekeningspubliek bouwen dat product X tussen 3 en 9 maanden geleden maar nog niet het product Y kocht. Vervolgens kunnen ze het programma activeren en de voordelen van product Y voor dat doelpubliek benadrukken.
* **de bedrijven van het doel die concurrerende producten gebruiken:** A de marktleider kan aan rekeningen in de handel brengen om de producten van een concurrent, zelfs zonder enige contacten bij die rekeningen te verplaatsen. Zij kunnen een publiek van rekeningen tot stand brengen die op partnergegevens worden gebaseerd die eigendom of gebruik van het product van een concurrent tonen, dan via LinkedIn activeren aan broncontacten bij doelrekeningen voor uitbreiding.

## Applicaties

* Real-time Customer Data Platform B2B edition

## Integratiepatronen

* B2B-gegevensbronnen (Marketo, Salesforce, enz.) -> Real-time Customer Data Platform B2B edition -> Doelen.
* Verschillende B2B-gegevensbronnen kunnen worden gebruikt om account-, lood-, opportunitegegevens en personengegevens toe te wijzen aan de B2B edition of Real-time Customer Data Platform.

## Architectuur

![ de architectuur van de Verwijzing voor B2B de Blauwdruk van Audience Activation van de Rekening ](assets/b2b-blueprint-account-audience-activation.png)

## Doelstellingen voor accountpubliek

* (Bedrijven) LinkedIn Gelijkend publiek
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
* [ B2B het Profiel &amp; de Gidsen van de Segmentatie ](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-guardrails).

## Implementatiestappen voor Real-time Customer Data Platform B2B edition, het creëren van een accountpubliek en activering

* Voor implementatiestappen van het Platform van Gegevens van de Klant in real time B2B edition, zie [ Begonnen worden met Real-Time Customer Data Platform B2B Editiond ](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-tutorial) documentatie.
* Voor de stappen van de Aanmaak van het Publiek van de Rekening, zie de [ documentatie van het publiek van de Rekening ](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences).
* Voor de stappen van Audience Activation van de Rekening, zie [ accountpubliek ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences) documentatie activeren.
   * Vereiste afbeelding voor [ (Bedrijven) doel LinkedIn Gelijke Soorten van publiek ](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences#required-mappings).

## Implementatieoverwegingen

LinkedIn-publiek heeft een aantal vereisten, waaronder de minimale doelgrootte van 300 overeenkomende leden. Als het accountpubliek dat voor de gekoppelde overeenkomende doelgroep van het bedrijf is geactiveerd, niet aan de vereiste voldoet, moet de publieksdefinitie worden gewijzigd om de doelgroep groter te maken en een LinkedIn-campagne te starten.

## Verwante documentatie

* [B2B edition of Real-Time Customer Data Platform](https://experienceleague.adobe.com/en/docs/experience-platform/rtcdp/intro/rtcdpb2b-intro/b2b-overview)
* [Zelfstudie voor accountpubliek maken en activeren](https://experienceleague.adobe.com/en/docs/platform-learn/tutorials/audiences/create-audiences-with-b2b-data)
* [Accountsoorten maken](https://experienceleague.adobe.com/en/docs/experience-platform/segmentation/ui/account-audiences)
* [Accountsoorten activeren](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/ui/activate/activate-account-audiences)
* [Adobe Experience Platform - LinkedIn-bestemmingsconnector](https://experienceleague.adobe.com/en/docs/experience-platform/destinations/catalog/social/linkedin)
