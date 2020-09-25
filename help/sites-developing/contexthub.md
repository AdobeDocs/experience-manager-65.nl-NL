---
title: ContextHub
seo-title: ContextHub
description: ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens
seo-description: ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens
uuid: 14e6ff4f-ffbe-454a-b2ec-a35333526e27
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: acf5c17a-95b7-43ba-9734-241e20f4f374
translation-type: tm+mt
source-git-commit: a8ba56849f6bb9f0cf6571fc51f4b5cae71620e0
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 1%

---


# ContextHub{#contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. Met de JavaScript-API aan de clientzijde hebt u toegang tot de gegevens voor het aanpassen van de inhoud.

>[!NOTE]
>
>De [Wij.Retail verwijzingsimplementatie](/help/sites-developing/we-retail.md) voert ContextHub uit en kan als verwijzing dienen aangezien u ContextHub in uw eigen project integreert.

>[!CAUTION]
>
>De weg die de configuratie bevat van steekproefContextHub die door de [Wij.Retail verwijzingsimplementatie](/help/sites-developing/we-retail.md) ( `/libs/settings/cloudsettings/legacy`) wordt gebruikt zou slechts als verwijzing voor het creëren van uw eigen configuratie moeten worden gebruikt.
>
>Het zou niet in een project als uw eigen configuratie ContextHub moeten worden gebruikt.

## Persistentie {#persistence}

De opslag ContextHub handhaaft contextgegevens over de cliënt. De JavaScript API van ContextHub laat u toe om tot opslag toegang te hebben om, gegevens tot stand te brengen bij te werken en te schrappen zonodig. Als dusdanig, vertegenwoordigt ContextHub een gegevenslaag op uw pagina&#39;s.

Elke opslag ContextHub is een geval van een vooraf bepaald opslagtype:

* ContextHub verstrekt verscheidene types [van](/help/sites-developing/ch-samplestores.md)steekproefopslag.
* Gebruik AEM consoles om winkels te [maken](ch-configuring.md#creating-a-contexthub-store).
* Ontwikkelaars kunnen aangepaste winkeltypen [maken](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).
* Ontwikkelaars hebben [toegang tot opslaggegevens](/help/sites-developing/ch-adding.md#interacting-with-contexthub-stores) via JavaScript.

## Segmentering {#segmentation}

ContextHub omvat een segmenteringsmotor die segmenten beheert en bepaalt welke segmenten voor de huidige context worden opgelost. Verschillende segmenten zijn gedefinieerd. U kunt de Javascript API gebruiken om opgeloste segmenten [te](/help/sites-developing/ch-adding.md#determining-resolved-contexthub-segments)bepalen.

## Presentatie {#presentation}

De [toolbar](/help/sites-authoring/ch-previewing.md) ContextHub laat marketers en auteurs toe om opslaggegevens te zien en te manipuleren voor het simuleren van de gebruikerservaring wanneer het ontwerpen van pagina&#39;s. De toolbar bestaat uit groepen modules UI die toegang tot winkels verlenen ContextHub.

Elke module ContextHub UI is een geval van een vooraf bepaald moduletype:

* ContextHub verstrekt verscheidene types [van](/help/sites-developing/ch-samplemodules.md)steekproefmodule.
* Gebruik AEM consoles om UI-modules [toe te](ch-configuring.md#adding-a-ui-module)voegen en deze [te groeperen in UI-modi](ch-configuring.md#adding-a-ui-mode).

* Ontwikkelaars kunnen aangepaste moduletypen [](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types)maken.

De ontwikkelaars moeten de component ContextHub aan de pagina [](/help/sites-developing/ch-adding.md)toevoegen.
