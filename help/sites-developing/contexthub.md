---
title: ContextHub
description: ContextHub is een kader om, contextgegevens op te slaan te manipuleren en voor te stellen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 3fd50655-7461-4900-a3b8-c01b04c7ba7a
solution: Experience Manager, Experience Manager Sites
feature: Developing,Personalization
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# ContextHub{#contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. Met de client-side JavaScript API hebt u toegang tot de gegevens voor het aanpassen van inhoud.

>[!NOTE]
>
>De [&#x200B; Wij.Retail verwijzingsimplementatie &#x200B;](/help/sites-developing/we-retail.md) voert ContextHub uit en kan als verwijzing dienen aangezien u ContextHub in uw eigen project integreert.

>[!CAUTION]
>
>De weg die de configuratie bevat van steekproefContextHub die door [&#x200B; wordt gebruikt Wij.Retail verwijzingsimplementatie &#x200B;](/help/sites-developing/we-retail.md) ( `/libs/settings/cloudsettings/legacy`) zou slechts als verwijzing voor het creëren van uw eigen configuratie moeten worden gebruikt.
>
>Gebruik niet in een project als uw eigen configuratie ContextHub.

## Persistentie {#persistence}

De opslag ContextHub handhaaft contextgegevens over de cliënt. De API van ContextHub JavaScript laat u toe om tot opslag toegang te hebben om, gegevens tot stand te brengen bij te werken en te schrappen zonodig. Als dusdanig, vertegenwoordigt ContextHub een gegevenslaag op uw pagina&#39;s.

Elke opslag ContextHub is een geval van een vooraf bepaald opslagtype:

* ContextHub verstrekt verscheidene [&#x200B; types van steekproefopslag &#x200B;](/help/sites-developing/ch-samplestores.md).
* Het gebruik AEM consoles aan [&#x200B; creeert opslag &#x200B;](ch-configuring.md#creating-a-contexthub-store).
* De ontwikkelaars kunnen [&#x200B; tot de types van douaneopslag &#x200B;](/help/sites-developing/ch-extend.md#creating-custom-store-candidates) leiden.
* De ontwikkelaars kunnen [&#x200B; tot opslaggegevens &#x200B;](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) via JavaScript toegang hebben.

## Segmentering {#segmentation}

ContextHub omvat een segmenteringsmotor die segmenten beheert en bepaalt welke segmenten voor de huidige context worden opgelost. Verschillende segmenten zijn gedefinieerd. U kunt JavaScript API gebruiken om [&#x200B; bepaalde opgeloste segmenten &#x200B;](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments) te bepalen.

## Presentatie {#presentation}

De [&#x200B; toolbar ContextHub &#x200B;](/help/sites-authoring/ch-previewing.md) laat tellers en auteurs toe om opslaggegevens te zien en te manipuleren voor het simuleren van de gebruikerservaring wanneer het ontwerpen van pagina&#39;s. De toolbar bestaat uit groepen modules UI die toegang tot winkels verlenen ContextHub.

Elke module ContextHub UI is een geval van een vooraf bepaald moduletype:

* ContextHub verstrekt verscheidene [&#x200B; types van steekproefmodule &#x200B;](/help/sites-developing/ch-samplemodules.md).
* Het gebruik AEM consoles aan [&#x200B; voegt modules UI &#x200B;](ch-configuring.md#adding-a-ui-module) toe, en aan [&#x200B; groepeert hen in wijzen UI &#x200B;](ch-configuring.md#adding-a-ui-mode).

* De ontwikkelaars kunnen [&#x200B; de types van douanemodule &#x200B;](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types) tot stand brengen.

De ontwikkelaars moeten [&#x200B; de component ContextHub aan de pagina &#x200B;](/help/sites-developing/ch-adding.md) toevoegen.
