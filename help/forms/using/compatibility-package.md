---
title: Compatibiliteitspakket
seo-title: Compatibility Package
description: Als u het compatibiliteitspakket op AEM Forms 6.5 installeert, kunt u de Correspondentenbeheermiddelen van AEM Forms 6.4 en eerdere versies en afgekeurde adaptieve formuliersjablonen en pagina's gebruiken
seo-description: Installing the Compatibility package on AEM Forms 6.4 lets you use the Correspondence Management assets from AEM Forms 6.4 and deprecated adaptive forms templates and pages
uuid: b49633d6-2cb3-422c-a314-25f3b8a37b7f
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 73e8ccc6-f857-493e-b6e3-878f93e2a356
docset: aem65
role: Admin
exl-id: bb16017c-a1bf-40d8-a78d-827c05b7ee2e
source-git-commit: 50d29c967a675db92e077916fb4adef6d2d98a1a
workflow-type: tm+mt
source-wordcount: '314'
ht-degree: 0%

---

# Compatibiliteitspakket{#compatibility-package}

## Overzicht {#overview}

De interactieve mededeling is het gebrek en geadviseerde benadering om klantenmededelingen in AEM Forms 6.5 tot stand te brengen. Als u letters wilt blijven gebruiken in AEM Forms 6.5, moet u de nieuwste [AEMFD-compatibiliteitspakket](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html).

Met het pakket AEMFD-compatibiliteit kunt u ook [gebruik de volgende activa van AEM Forms 6.4, 6.3 en 6.2 op AEM Forms 6.5:](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms)

* Documentfragmenten
* Letters
* Gegevenswoordenboeken
* Afgekeurde sjablonen en pagina&#39;s voor adaptieve formulieren

Zie voor meer informatie [Activa die compatibel zijn gemaakt met AEM Forms 6.5 door het compatibiliteitspakket te installeren](../../forms/using/compatibility-package.md#assetsmadecompatible).

## Voeg ondersteuning toe voor AEM Forms 6.4-, 6.3- en 6.2-middelen in AEM Forms 6.5 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Nadat u een upgrade hebt uitgevoerd, voert u de volgende handelingen uit om het compatibiliteitspakket voor AEMFD te installeren en uw elementen compatibel te maken met 6.5:

Zorg ervoor dat u [Compatibiliteitspakket AEM](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) vooraf geïnstalleerd.

1. De nieuwste versie 6.5 installeren [Verenigbaarheidspakket](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html).

   Voor meer informatie over het uploaden en installeren van het pakket raadpleegt u [Werken met pakketten](/help/sites-administering/package-manager.md).

1. Start de server opnieuw nadat de logbestanden zijn gestabiliseerd.
1. Gebruik het migratiehulpprogramma om uw middelen compatibel te maken met 6.5.

   Zie voor meer informatie [migratiehulpprogramma](../../forms/using/migration-utility.md).

## Activa die compatibel zijn gemaakt met AEM Forms 6.5 door het compatibiliteitspakket te installeren {#assetsmadecompatible}

Door het compatibiliteitspakket te installeren, kunt u de volgende elementen en sjablonen compatibel maken met AEM Forms 6.5:

* Correspondentenbeheeractiva uit AEM 6.4 en eerder:

   * [Letters](../../forms/using/create-letter.md)
   * [Gegevenswoordenboeken](/help/forms/using/data-dictionary.md)
   * Documentfragmenten

* Afgekeurde sjablonen voor adaptieve formulieren:

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Afgekeurde pagina&#39;s voor adaptieve formulieren:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedRolment
