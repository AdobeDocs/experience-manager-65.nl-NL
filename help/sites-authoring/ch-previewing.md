---
title: Pagina's voorvertonen met ContextHub-gegevens
description: De ContextHub toolbarvertoningen gegevens van Opslag ContextHub en laat u toe om opslaggegevens te veranderen en is nuttig om inhoud te previewing
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: 78673609-8cbc-4b4b-953e-56c31ea1b4ea
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 0%

---

# Pagina&#39;s voorvertonen met ContextHub-gegevens{#previewing-pages-using-contexthub-data}

De [&#x200B; ContextHub &#x200B;](/help/sites-developing/contexthub.md) toolbarvertoningen gegevens van opslag ContextHub en laat u toe om opslaggegevens te veranderen. De toolbar ContextHub is nuttig om inhoud te previewing die door gegevens in een opslag ContextHub wordt bepaald.

De werkbalk bestaat uit een reeks UI-modi die een of meer UI-modules bevatten.

* UI-modi zijn pictogrammen die aan de linkerkant van de werkbalk worden weergegeven. Als u op een pictogram klikt, worden op de werkbalk de UI-modules weergegeven die erin staan.
* UI de modules tonen gegevens van één of meerdere opslag ContextHub. Sommige modules UI laten u ook toe om opslaggegevens te manipuleren.

ContextHub installeert verscheidene wijzen UI en modules UI. Uw beheerder kan [&#x200B; gevormde ContextHub &#x200B;](/help/sites-developing/ch-configuring.md) hebben om verschillende degenen te tonen.

![&#x200B; screen_shot_2018-03-23at093446 &#x200B;](assets/screen_shot_2018-03-23at093446.png)

## De werkbalk ContextHub weergeven {#revealing-the-contexthub-toolbar}

De toolbar ContextHub is beschikbaar op de wijze van de Voorproef. De werkbalk is alleen beschikbaar voor auteur-exemplaren en alleen als uw beheerder deze heeft ingeschakeld.

![&#x200B; screen_shot_2018-03-23at093730 &#x200B;](assets/screen_shot_2018-03-23at093730.png)

1. Open de pagina en klik op Voorvertoning op de werkbalk terwijl u deze wilt bewerken.

   ![&#x200B; chlimage_1-219 &#x200B;](assets/chlimage_1-219.png)

1. Om de toolbar te openbaren, klik het pictogram ContextHub.

   ![&#x200B; de Hub van de Context &#x200B;](do-not-localize/screen_shot_2018-03-23at093621.png)

## Functies van de UI-module {#ui-module-features}

Elke UI-module biedt verschillende functies, maar de volgende typen functies zijn gebruikelijk. Omdat de modules UI verlengbaar zijn, kan uw ontwikkelaar andere eigenschappen uitvoeren zoals vereist.

### Werkbalkinhoud {#toolbar-content}

UI de modules kunnen gegevens van één of meerdere opslag ContextHub in de toolbar tonen. UI-modules gebruiken een pictogram en een titel om zichzelf te identificeren.

![&#x200B; screen_shot_2018-03-23at093936 &#x200B;](assets/screen_shot_2018-03-23at093936.png)

### Inhoud pop-up {#popup-content}

Sommige modules UI tonen popup bekleed wanneer geklikt of getikt. Het pop-upmenu bevat doorgaans aanvullende informatie dan die op de werkbalk wordt weergegeven.

![&#x200B; screen_shot_2018-03-23at094003 &#x200B;](assets/screen_shot_2018-03-23at094003.png)

### Popup-Forms {#popup-forms}

De popup bekleding van een module kan vormelementen omvatten die u toelaten om de gegevens in de opslag te veranderen ContextHub. Als de pagina-inhoud wordt bepaald door de opslaggegevens, kunt u het formulier gebruiken en de wijzigingen in de pagina-inhoud observeren.

### Modus Volledig scherm {#fullscreen-mode}

Popup overlays kunnen een pictogram omvatten dat u klikt om popup inhoud uit te breiden om het volledige browser venster of het scherm te behandelen.

![&#x200B; Volledig scherm &#x200B;](do-not-localize/chlimage_1-18.png)
