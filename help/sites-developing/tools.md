---
title: Gereedschappen voor testen en bijhouden
seo-title: Testing and Tracking Tools
description: AEM biedt een raamwerk voor het testen van de interface van componenten en een mechanisme voor het testen en opsporen van fouten in componenten
seo-description: AEM provides a framework for testing component UI and a mechanism for testing and debugging components
uuid: 12abedb5-4ee7-4389-9340-e628adbbc053
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: 3cf0fd8d-7fc8-468a-bb1e-1debb68a82a5
docset: aem65
exl-id: bb5d1c7c-56ce-4d1e-a3cb-4e74d6922137
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---

# Gereedschappen voor testen en bijhouden{#testing-and-tracking-tools}

## Testen {#testing}

AEM biedt:

* [een raamwerk voor het testen van de gebruikersinterface voor componenten](/help/sites-developing/hobbes.md).
* [een mechanisme voor het testen van en het opsporen van fouten in componenten](/help/sites-developing/developer-mode.md).

Hieronder vindt u twee Open Source Testing-gereedschappen:

**Selenium**

Selenium wordt gebruikt voor functietests in een browser met één gebruiker per activiteit. Hierbij worden teststappen (klikken) vastgelegd als HTML-tabellen of Java-klassen.

Zie voor meer informatie [https://www.seleniumhq.org/](https://www.seleniumhq.org/).

**JMeter**

JMeter wordt gebruikt om aanvragen te volgen en kan worden gebruikt voor functionele, prestatie- en stresstests.

Zie voor meer informatie [https://jakarta.apache.org/jmeter/](https://jakarta.apache.org/jmeter).

Er zijn ook veel bedrijfseigen instrumenten om tests te automatiseren en testplannen te beheren.

### Tekstspatiëring {#tracking}

De volgende gereedschappen zijn gemakkelijk beschikbaar. Nochtans is een zeer belangrijke kwestie in alle gevallen de beschikbaarheid van de gegevens aan alle leden van het projectteam - partner en klant.

**Bugzilla**

Een bug-volgsysteem dat aan uw eigen vereisten kan worden gevormd.

**Werkbladen**

Hoewel spreadsheets niet specifiek een tool voor het bijhouden van fouten zijn, *mis* gebruikt voor dit doel omdat zij gemakkelijk te begrijpen zijn en de meeste gebruikers ervaring met hun functionaliteit hebben.

Als deze voor het volgen dan worden gebruikt:

* zij moeten eenvoudig worden gehouden .
* het aantal afzonderlijke spreadsheets moet tot een minimum worden beperkt .
* zij moeten regelmatig worden bijgewerkt .
* slechts één master kopie moet worden bewaard en iedereen moet weten waar de master kopie is.
* zij moeten toegankelijk zijn voor alle projectleden .
* als de veiligheid een kwestie is ( vaak voorkomt bij grote bedrijven ) en gemeenschappelijke toegang niet mogelijk is , kunnen kopieën worden verspreid zolang iedereen begrijpt dat het kopieën zijn en niet kunnen worden bijgewerkt .

Ook hier zijn er veel bedrijfseigen hulpmiddelen voor het bijhouden van fouten en eigenschapvereisten.
