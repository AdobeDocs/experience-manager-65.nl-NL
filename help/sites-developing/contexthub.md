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
>De [We.Retail-referentieimplementatie](/help/sites-developing/we-retail.md) Voert ContextHub uit en kan als verwijzing dienen aangezien u ContextHub in uw eigen project integreert.

>[!CAUTION]
>
>De weg die de configuratie bevat van steekproefContextHub die door wordt gebruikt [We.Retail-referentieimplementatie](/help/sites-developing/we-retail.md) ( `/libs/settings/cloudsettings/legacy`) alleen gebruiken als referentie voor het maken van uw eigen configuratie.
>
>Gebruik niet in een project als uw eigen configuratie ContextHub.

## Persistentie {#persistence}

De opslag ContextHub handhaaft contextgegevens over de cliënt. Met de JavaScript-API van ContextHub hebt u toegang tot opslagruimten om gegevens te maken, bij te werken en te verwijderen. Als dusdanig, vertegenwoordigt ContextHub een gegevenslaag op uw pagina&#39;s.

Elke opslag ContextHub is een geval van een vooraf bepaald opslagtype:

* ContextHub biedt verschillende [voorbeeldwinkeltypen](/help/sites-developing/ch-samplestores.md).
* Consoles AEM gebruiken voor [opslaan maken](ch-configuring.md#creating-a-contexthub-store).
* Ontwikkelaars kunnen [aangepaste winkeltypen maken](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* Ontwikkelaars kunnen [toegang opslaggegevens](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) via JavaScript.

## Segmentering {#segmentation}

ContextHub omvat een segmenteringsmotor die segmenten beheert en bepaalt welke segmenten voor de huidige context worden opgelost. Verschillende segmenten zijn gedefinieerd. U kunt de JavaScript-API gebruiken om [omgezette segmenten bepalen](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments).

## Presentatie {#presentation}

De [ContextHub-werkbalk](/help/sites-authoring/ch-previewing.md) stelt marketers en auteurs in staat om opslaggegevens te bekijken en te manipuleren om de gebruikerservaring bij het ontwerpen van pagina&#39;s te simuleren. De toolbar bestaat uit groepen modules UI die toegang tot winkels verlenen ContextHub.

Elke module ContextHub UI is een geval van een vooraf bepaald moduletype:

* ContextHub biedt verschillende [voorbeeldmoduletypen](/help/sites-developing/ch-samplemodules.md).
* Consoles AEM gebruiken voor [UI-modules toevoegen](ch-configuring.md#adding-a-ui-module), en [groeperen hen in wijzen UI](ch-configuring.md#adding-a-ui-mode).

* Ontwikkelaars kunnen [aangepaste moduletypen maken](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

Ontwikkelaars moeten [Voeg de component ContextHub aan de pagina toe](/help/sites-developing/ch-adding.md).
