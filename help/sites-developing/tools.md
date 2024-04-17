---
title: Gereedschappen voor testen en bijhouden
description: AEM biedt een raamwerk voor het testen van de interface van componenten en een mechanisme voor het testen en opsporen van fouten in componenten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
docset: aem65
exl-id: bb5d1c7c-56ce-4d1e-a3cb-4e74d6922137
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Gereedschappen voor testen en bijhouden{#testing-and-tracking-tools}

## Testen {#testing}

AEM biedt:

* [een raamwerk voor het testen van de gebruikersinterface voor componenten](/help/sites-developing/hobbes.md).
* [een mechanisme voor het testen van en het opsporen van fouten in componenten](/help/sites-developing/developer-mode.md).

Hieronder vindt u twee Open Source Testing-gereedschappen:

**Selenium**

Selenium wordt gebruikt voor functietests in een browser met één gebruiker per activiteit. Het registreert teststappen (kliks) als of HTML lijsten of klassen Java™.

Zie voor meer informatie [https://www.selenium.dev/](https://www.selenium.dev/).

**JMeter**

JMeter wordt gebruikt om verzoeken bij te houden en kan worden gebruikt voor functionele, prestatie- en stresstests.

Zie voor meer informatie [https://jmeter.apache.org/](https://jmeter.apache.org/).

Er zijn ook veel bedrijfseigen instrumenten voor het automatiseren van tests en het beheren van testplannen.

### Tekstspatiëring {#tracking}

De volgende gereedschappen zijn gemakkelijk beschikbaar. Nochtans is een zeer belangrijke kwestie in alle gevallen de beschikbaarheid van de gegevens aan alle leden van het projectteam - partner en klant.

**Bugzilla**

Een bug-volgsysteem dat aan uw eigen vereisten kan worden gevormd.

**Werkbladen**

Hoewel spreadsheets niet specifiek een tool voor het bijhouden van fouten zijn, *mis* gebruikt voor dit doel omdat zij gemakkelijk te begrijpen zijn en de meeste gebruikers ervaring met hun functionaliteit hebben.

Als deze spreadsheets worden gebruikt voor tracering, geldt het volgende:

* zij moeten eenvoudig worden gehouden .
* het aantal afzonderlijke spreadsheets moet tot een minimum worden beperkt .
* zij moeten regelmatig worden bijgewerkt .
* slechts één primaire kopie moet worden bewaard en iedereen moet weten waar de primaire kopie is.
* zij moeten toegankelijk zijn voor alle projectleden .
* als de veiligheid een kwestie (vaak voorkomt bij grote bedrijven) is en gemeenschappelijke toegang niet mogelijk is, dan kunnen de exemplaren worden verdeeld zolang iedereen begrijpt dat deze spreadsheets kopieën zijn en niet kunnen worden bijgewerkt.

Ook hier zijn er veel bedrijfseigen hulpmiddelen voor het bijhouden van fouten en eigenschapvereisten.
