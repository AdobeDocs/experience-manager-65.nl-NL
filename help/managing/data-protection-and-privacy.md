---
title: Regels voor gegevensbescherming en gegevensbescherming - Adobe Experience Manager-gereedheid
description: Meer informatie over Adobe Experience Manager-ondersteuning voor de verschillende Data Protection and Data Privacy Regulations. Het omvat de algemene gegevensbeschermingsverordening van de EU (GDPR), de California Consumer Privacy Act en hoe te om te voldoen wanneer het uitvoeren van een nieuw AEM project.
contentOwner: AEM Docs
topic-tags: introduction, grdp
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
docset: aem65
exl-id: 46c1ca14-78f6-4b33-9fdf-1b90a9875f66
solution: Experience Manager, Experience Manager 6.5
source-git-commit: 1751bfb32386685e3a159939113b9667b5e17f0e
workflow-type: tm+mt
source-wordcount: '890'
ht-degree: 0%

---

# Adobe Experience Manager Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>De inhoud van dit document is geen juridisch advies en is niet bedoeld als vervanging van juridisch advies.
>
>Raadpleeg de juridische afdeling van uw bedrijf voor advies over regelgeving inzake gegevensbescherming en gegevensbescherming.

>[!NOTE]
>
>Voor meer informatie over de reactie van de Adobe op privacykwesties, en wat het voor u als Adobe klant betekent, zie [Privacy Center van Adobe](https://www.adobe.com/privacy.html).

De Adobe verstrekt documentatie en procedures (met APIs wanneer beschikbaar), voor de beheerder van de klantenprivacy of AEM beheerder om de verzoeken van de gegevensbescherming en van de gegevensprivacy te behandelen. Het kan u helpen om aan deze verordeningen te voldoen. De gedocumenteerde procedures laten klanten de regelgevende verzoeken manueel in werking stellen of door in APIs, waar beschikbaar, van een extern portaal of de dienst te roepen.

>[!CAUTION]
>
>De hier gedocumenteerde details zijn beperkt tot Adobe Experience Manager.
>
>Gegevens van een andere Adobe On-demand-dienst, samen met eventuele gerelateerde privacyverzoeken, vereisen dat op die dienst maatregelen worden genomen.
>
>Zie voor meer informatie [Privacy Center van Adobe](https://www.adobe.com/privacy.html).

## Inleiding {#introduction}

Instanties van Adobe Experience Manager en de toepassingen die erop worden uitgevoerd, zijn eigendom van en worden geëxploiteerd door Adobe klanten.

Bijgevolg vallen gegevensbeschermingsvoorschriften, zoals GDPR, CCPA en andere, grotendeels onder de verantwoordelijkheid van de klanten.

In een korte inleiding bevatten de verordeningen betreffende de privacy en bescherming van gegevens nieuwe regels die moeten worden gevolgd door de taken van:

* Bedrijfsentiteiten (CCPA) en/of gegevensverwerkingsverantwoordelijken (GDPR)

* Dienstverleners (CCPA) en/of gegevensverwerkers (GDPR)

De belangrijkste bepalingen van deze verordeningen zijn:

1. Uitgebreide definitie van persoonsgegevens zodat deze alle unieke id&#39;s omvat, zoals direct en indirect identificeerbare gegevens.

2. Versterking van de toestemmingseisen.

3. Meer aandacht voor verwijderingsrechten (gegevenswissing).

4. Uitschakelen van verkoop van gegevens.

Voor Adobe Experience Manager:

* De instanties en toepassingen die erop worden uitgevoerd, zijn eigendom van en worden beheerd door de klant.

   * De klant beheert de regulerende rollen, met inbegrip van BedrijfsEntiteiten en Dienstverlener, het Controlemechanisme van Gegevens, en de Bewerker van Gegevens, onder andere.

   * De Adobe Experience Platform Privacy Service maakt geen deel uit van de workflow voor AEM, zoals in het onderstaande diagram wordt geïllustreerd.

* AEM omvat documentatie en procedures voor de privacybeheerder en/of AEM beheerder van de klant om de verzoeken van de privacyverordening uit te voeren; of manueel of door APIs, indien beschikbaar.

* Er is geen nieuwe service of interface toegevoegd.

   * In plaats daarvan worden procedures en APIs gedocumenteerd voor gebruik door klant UIs/portals die verzoeken van de privacyverordening behandelen.

* AEM bevat geen out-of-the-box gereedschappen ter ondersteuning van de workflow voor privacyverzoeken.

   * Adobe verstrekt documentatie en procedures voor de de privacybeheerder van de klant en AEM beheerder, die hen manueel verzoeken met betrekking tot de privacyverordeningen laat in werking stellen.

Adobe biedt procedures voor het verwerken van privacyverzoeken met betrekking tot Access, Delete en Opt-Out voor Adobe Experience Manager. Soms zijn er API&#39;s beschikbaar die kunnen worden aangeroepen via een door de klant ontwikkeld portaal of scripts om te helpen met automatisering.

In het volgende diagram ziet u hoe een workflow voor privacyverzoeken eruit kan zien (geïllustreerd met Adobe Experience Manager 6.5):

![Gegevensbescherming en privacy](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager en gereedheid voor regelgeving {#aem-and-regulatory-readiness}

Zie de onderstaande secties voor documentatie over regelgeving voor productgebieden van AEM.

## AEM stichting {#aem-foundation}

Zie [Behandeling van verzoeken om gegevensbescherming en privacy voor de AEM Stichting](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

## AEM kiezen voor aggregatie van verbruiksstatistieken {#aem-opting-into-aggregate-usage-statistics-collection}

Zie [Samengevoegde verzameling verbruiksstatistieken](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

## AEM Sites {#aem-sites}

Zie [AEM Sites - Gereedheid voor gegevensbescherming en privacy.](/help/sites-administering/gdpr-compliance-sites.md)

## AEM {#aem-commerce}

Zie [AEM handel - Gegevensbescherming en privacy gereedheid](/help/sites-administering/gdpr-compliance-commerce.md).

## AEM Mobile {#aem-mobile}

Zie [AEM Mobile - Gereedheid voor gegevensbescherming en privacy](/help/mobile/aem-mobile-gdpr-compliance.md).

## AEM integratie met Adobe Target en Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Deze Adobe Experience Manager-integratie is mogelijk met services die geschikt zijn voor gegevensbescherming en privacy (bijvoorbeeld GDPR of CCPA). Er worden geen persoonsgegevens van Adobe Target of Adobe Analytics in AEM opgeslagen met betrekking tot de integratie.

Raadpleeg de volgende secties voor meer informatie:

* [Adobe Target - Overzicht van privacy](https://developer.adobe.com/target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation/?lang=en)

* [Adobe Analytics Data Privacy Workflow](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html)

## AEM Communities {#aem-communities}

AEM Communities geeft de betrokkenen recht op hun gegevensportabiliteit, recht op toegang en recht om vergeten te worden [out-of-the-box API&#39;s](/help/communities/user-ugc-management-service.md). Deze APIs laat bulkschrapping en bulkuitvoer van gebruiker-geproduceerde inhoud toe, en het onbruikbaar maken van gebruikersrekeningen die door hun erkende IDs worden geïdentificeerd. Nochtans, is de permanente schrapping van gebruikersrekening realiseerbaar door gebruikersknoop in CRXDE Lite te schrappen, die de behoefte van gemakkelijke Opt-out van het systeem richt.

Bovendien biedt AEM Communities privacy door ontwerp toe te schrijven aan zijn BulkModeration console, die bevoorrechte leden toestaat om de bijdragen en de details van de gebruikers te vinden en te schrappen. De beheerconsole van Leden laat het beperken tot het punt van het verbieden van een medewerker toe. Bovendien worden de betrokkenen gemachtigd de door hen geautoriseerde bijdragen te schrappen.

## AEM Forms {#aem-forms}

AEM Forms omvat componenten en workflows die gegevens vastleggen, verwerken en opslaan om bedrijfsprocessen te ordenen en digitale transacties te voltooien. De verschillende componenten gebruiken verschillende gegevensopslag en staan integratie met douanegegevensopslag eveneens toe. In de volgende documentatie worden de procedures en richtlijnen beschreven voor de toegang tot en de verwerking van gebruikersgegevens ter ondersteuning van gegevensbeveiliging en privacyworkflows (bijvoorbeeld GDPR of CCPA) voor een component.

* [Forms Portal](/help/forms/using/forms-portal-handling-user-data.md)
* [Correspondentenbeheer](/help/forms/using/correspondence-management-handling-user-data.md)
* [Integratie met Adobe Sign](/help/forms/using/integration-adobe-sign-handling-user-data.md)
* [Forms-gecentreerde workflows op OSGi](/help/forms/using/forms-workflow-osgi-handling-user-data.md)
* [Forms JEE-workflows](/help/forms/using/forms-workflow-jee-handling-user-data.md) (alleen AEM Forms JEE)
* [Documentbeveiliging](/help/forms/using/document-security-handling-user-data.md) (alleen AEM Forms JEE)
* [Gebruikersbeheer](/help/forms/using/user-management-handling-user-data.md) (alleen AEM Forms JEE)
