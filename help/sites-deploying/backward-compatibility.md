---
title: Achterwaartse compatibiliteit in AEM 6.5
seo-title: Achterwaartse compatibiliteit in AEM 6.5
description: Leer hoe u uw apps en configuraties compatibel kunt houden met AEM 6.5
seo-description: Leer hoe u uw apps en configuraties compatibel kunt houden met AEM 6.5
uuid: 81dc2771-f59b-4b24-8932-9e938cba05e0
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: f3b4ec1d-9054-47d4-afcb-0a0121b94190
docset: aem65
translation-type: tm+mt
source-git-commit: 303841896717448947aa48ece7ae86519a5450d5
workflow-type: tm+mt
source-wordcount: '502'
ht-degree: 0%

---


# Achterwaartse Verenigbaarheid in AEM 6.5{#backward-compatibility-in-aem}

## Overzicht {#overview}

>[!NOTE]
>
>Voor een lijst van inhoud en configuratieveranderingen die niet onder het werkingsgebied het Pakket van de Verenigbaarheid vallen, zie [Herstructurering van de Bewaarplaats in AEM](/help/sites-deploying/repository-restructuring.md).

In AEM 6.5 zijn alle functies ontwikkeld met achterwaartse compatibiliteit voor ogen.

In de meeste gevallen, zouden de klanten die AEM 6.3 in werking stellen niet de code of aanpassingen moeten veranderen wanneer het doen van de verbetering. Voor AEM 6.1 en 6.2 klanten zijn er geen extra breekveranderingen dan tijdens een verbetering aan 6.3 zouden worden geconfronteerd.

Voor uitzonderingen waar de eigenschappen niet achteruit compatibel konden worden gehouden, kunnen de achterwaartse onverenigbaarheidskwesties voor bundels en inhoud worden verlicht door een Pakket van de Verenigbaarheid voor 6.4 te installeren (te zien hoe te opstelling hieronder voor details over waar te om te downloaden). Dit compatpakket helpt in de meeste gevallen de compatibiliteit te herstellen voor toepassingen die voldoen aan AEM 6.4.

Met het compatibiliteitspakket kunt u AEM uitvoeren in de compatibiliteitsmodus en de aangepaste ontwikkeling uitstellen tegen nieuwe AEM:

>[!NOTE]
>
>Houd er rekening mee dat het compatibiliteitspakket slechts een tijdelijke oplossing is om de ontwikkeling uit te stellen die nodig is om AEM 6.5-compatibel te zijn. De oplossing wordt alleen aanbevolen als laatste optie als u compatibiliteitsproblemen niet direct na de upgrade kunt oplossen via ontwikkeling. Het wordt ten zeerste aanbevolen om over te schakelen op de native modus en het compatibiliteitspakket te verwijderen wanneer u besluit verder te gaan met aangepaste ontwikkeling op basis van 6.5 en gebruik te maken van de volledige 6.5-functionaliteit.

![verkorten](assets/sase.png)

Het compatibiliteitspakket heeft twee modi: **Verpletterend Toegelaten** en **Verpletterend Gehandicapten**.

Hierdoor kan AEM 6.5 in drie modi worden uitgevoerd:

**Modus Native:**

De modus Native is bedoeld voor klanten die alle nieuwe functies van AEM 6.5 willen gebruiken en die klaar zijn om enige ontwikkeling uit te voeren om hun aanpassingen met alle nieuwe functies te laten werken.

Dit betekent dat u mogelijk aanpassingen in uw toepassing moet aanbrengen direct na de upgrade.

**Compatibiliteitsmodus: Het Pakket van de verenigbaarheid dat met Toegelaten Verpletteren wordt geïnstalleerd**

De Wijze van de verenigbaarheid is voor klanten die aanpassingen van interfaces hebben die niet achterwaarts compatibel zijn. Dit staat AEM toe om op verenigbaarheidswijze te lopen en douaneontwikkeling uit te stellen die tegen nieuwe AEMEigenschappen wordt vereist die niet met sommige van uw douanecode compatibel zijn.

**Oudere modus: Compatiblity Package Geïnstalleerd met het Verpletteren van Gehandicapten**

De verouderde wijze is voor klanten die douaneinterfaces hebben die op erfenis of verouderde code van AEM worden gebaseerd die uit in het verenigingspakket is bewogen.

![sapte](assets/sapte.png)

## Instellen {#how-to-set-up}

Het AEM 6.3 compatibiliteitspakket kan als een pakket worden geïnstalleerd met de Package Manager. U kunt het [AEM 6.3 compatibiliteitspakket downloaden van de plaats van de Distributie van de Software](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq640/compatpack/aem-compat-cq64-to-cq63).

Zodra het Pakket van de Verenigbaarheid wordt geïnstalleerd, kan het verpletteren worden toegelaten of worden onbruikbaar gemaakt gebruikend een schakelaar in de configuratie OSGI zoals hieronder getoond:

![screen_shot_2017-11-27at122421pm](assets/screen_shot_2017-11-27at122421pm.png)

Nadat het compatibiliteitspakket is geïnstalleerd en ingesteld, worden de functies gebruikt op basis van de gekozen compatibiliteitsmodus.
