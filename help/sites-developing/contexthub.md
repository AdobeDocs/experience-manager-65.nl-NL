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
>De [ Wij.Retail verwijzingsimplementatie ](/help/sites-developing/we-retail.md) voert ContextHub uit en kan als verwijzing dienen aangezien u ContextHub in uw eigen project integreert.

>[!CAUTION]
>
>De weg die de configuratie bevat van steekproefContextHub die door [ wordt gebruikt Wij.Retail verwijzingsimplementatie ](/help/sites-developing/we-retail.md) ( `/libs/settings/cloudsettings/legacy`) zou slechts als verwijzing voor het creëren van uw eigen configuratie moeten worden gebruikt.
>
>Gebruik niet in een project als uw eigen configuratie ContextHub.

## Persistentie {#persistence}

De opslag ContextHub handhaaft contextgegevens over de cliënt. De API van ContextHub JavaScript laat u toe om tot opslag toegang te hebben om, gegevens tot stand te brengen bij te werken en te schrappen zonodig. Als dusdanig, vertegenwoordigt ContextHub een gegevenslaag op uw pagina&#39;s.

Elke opslag ContextHub is een geval van een vooraf bepaald opslagtype:

* ContextHub verstrekt verscheidene [ types van steekproefopslag ](/help/sites-developing/ch-samplestores.md).
* Het gebruik AEM consoles aan [ creeert opslag ](ch-configuring.md#creating-a-contexthub-store).
* De ontwikkelaars kunnen [ tot de types van douaneopslag ](/help/sites-developing/ch-extend.md#creating-custom-store-candidates) leiden.
* De ontwikkelaars kunnen [ tot opslaggegevens ](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) via JavaScript toegang hebben.

## Segmentering {#segmentation}

ContextHub omvat een segmenteringsmotor die segmenten beheert en bepaalt welke segmenten voor de huidige context worden opgelost. Verschillende segmenten zijn gedefinieerd. U kunt JavaScript API gebruiken om [ bepaalde opgeloste segmenten ](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments) te bepalen.

## Presentatie {#presentation}

De [ toolbar ContextHub ](/help/sites-authoring/ch-previewing.md) laat tellers en auteurs toe om opslaggegevens te zien en te manipuleren voor het simuleren van de gebruikerservaring wanneer het ontwerpen van pagina&#39;s. De toolbar bestaat uit groepen modules UI die toegang tot winkels verlenen ContextHub.

Elke module ContextHub UI is een geval van een vooraf bepaald moduletype:

* ContextHub verstrekt verscheidene [ types van steekproefmodule ](/help/sites-developing/ch-samplemodules.md).
* Het gebruik AEM consoles aan [ voegt modules UI ](ch-configuring.md#adding-a-ui-module) toe, en aan [ groepeert hen in wijzen UI ](ch-configuring.md#adding-a-ui-mode).

* De ontwikkelaars kunnen [ de types van douanemodule ](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types) tot stand brengen.

De ontwikkelaars moeten [ de component ContextHub aan de pagina ](/help/sites-developing/ch-adding.md) toevoegen.
