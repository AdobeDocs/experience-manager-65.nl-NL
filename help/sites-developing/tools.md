---
title: Gereedschappen voor testen en bijhouden
seo-title: Gereedschappen voor testen en bijhouden
description: AEM biedt een raamwerk voor het testen van de interface van componenten en een mechanisme voor het testen en opsporen van fouten in componenten
seo-description: AEM biedt een raamwerk voor het testen van de interface van componenten en een mechanisme voor het testen en opsporen van fouten in componenten
uuid: 12abedb5-4ee7-4389-9340-e628adbbc053
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 3cf0fd8d-7fc8-468a-bb1e-1debb68a82a5
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Gereedschappen voor testen en bijhouden{#testing-and-tracking-tools}

## Testen {#testing}

AEM biedt:

* [een framework voor het testen van de gebruikersinterface](/help/sites-developing/hobbes.md)van componenten.
* [een mechanisme voor het testen van en het opsporen van fouten in componenten](/help/sites-developing/developer-mode.md).

Hieronder vindt u twee Open Source Testing-gereedschappen:

**Selenium**

Selenium wordt gebruikt voor functietests in een browser met één gebruiker per activiteit. Hierbij worden teststappen (klikken) vastgelegd als HTML-tabellen of Java-klassen.

Zie [https://www.seleniumhq.org/](https://www.seleniumhq.org/)voor meer informatie.

**JMeter**

JMeter wordt gebruikt om aanvragen te volgen en kan worden gebruikt voor functionele, prestatie- en stresstests.

Zie [https://jakarta.apache.org/jmeter/](https://jakarta.apache.org/jmeter)voor meer informatie.

Er zijn ook veel bedrijfseigen instrumenten om tests te automatiseren en testplannen te beheren.

### Tekstspatiëring {#tracking}

De volgende gereedschappen zijn gemakkelijk beschikbaar. Nochtans is een zeer belangrijke kwestie in alle gevallen de beschikbaarheid van de gegevens aan alle leden van het projectteam - partner en klant.

**Bugzilla**

Een bug-volgsysteem dat aan uw eigen vereisten kan worden gevormd.

**Werkbladen**

Hoewel spreadsheets niet specifiek voor foutopsporing worden gebruikt, worden deze spreadsheets vaak ** misbruikt omdat ze gemakkelijk te begrijpen zijn en de meeste gebruikers ervaring hebben met hun functionaliteit.

Als deze voor het volgen dan worden gebruikt:

* zij moeten eenvoudig worden gehouden .
* het aantal afzonderlijke spreadsheets moet tot een minimum worden beperkt .
* zij moeten regelmatig worden bijgewerkt .
* er mag slechts één origineel worden bewaard en iedereen moet weten waar de originele kopie zich bevindt .
* zij moeten toegankelijk zijn voor alle projectleden .
* als de veiligheid een kwestie is ( vaak voorkomt bij grote bedrijven ) en gemeenschappelijke toegang niet mogelijk is , kunnen kopieën worden verspreid zolang iedereen begrijpt dat het kopieën zijn en niet kunnen worden bijgewerkt .

Ook hier zijn er veel bedrijfseigen hulpmiddelen voor het bijhouden van fouten en eigenschapvereisten.
