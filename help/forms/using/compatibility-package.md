---
title: Compatibiliteitspakket
seo-title: Compatibiliteitspakket
description: Als u het compatibiliteitspakket op AEM Forms 6.5 installeert, kunt u de Correspondence Management-middelen van AEM Forms 6.4 en eerdere versies en afgekeurde adaptieve formuliersjablonen en pagina's gebruiken
seo-description: Als u het compatibiliteitspakket op AEM Forms 6.4 installeert, kunt u de Correspondence Management-middelen van AEM Forms 6.4 en afgekeurde aangepaste formuliersjablonen en pagina's gebruiken
uuid: b49633d6-2cb3-422c-a314-25f3b8a37b7f
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: 73e8ccc6-f857-493e-b6e3-878f93e2a356
docset: aem65
translation-type: tm+mt
source-git-commit: a929252a13f66da8ac3e52aea0655b12bdd1425f
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---


# Compatibiliteitspakket{#compatibility-package}

## Overzicht {#overview}

De interactieve mededeling is het gebrek en geadviseerde benadering om klantenmededelingen in AEM Forms 6.5 tot stand te brengen. Als u letters wilt blijven gebruiken in AEM Forms 6.5, moet u het nieuwste [compatibiliteitspakket](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html)voor AEMFD installeren.

Met het compatibiliteitspakket voor AEMFD kunt u ook de volgende middelen van AEM Forms 6.4, 6.3 en 6.2 op AEM Forms 6.5 [gebruiken:](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms)

* Documentfragmenten
* Letters
* Gegevenswoordenboeken
* Afgekeurde sjablonen en pagina&#39;s voor adaptieve formulieren

Zie [Activa die compatibel zijn gemaakt met AEM Forms 6.5 door het compatibiliteitspakket](../../forms/using/compatibility-package.md#assetsmadecompatible)te installeren voor meer informatie.

## Voeg ondersteuning toe voor AEM Forms 6.4-, 6.3- en 6.2-middelen in AEM Forms 6.5 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Nadat u een upgrade hebt uitgevoerd, voert u de volgende handelingen uit om het compatibiliteitspakket voor AEMFD te installeren en uw elementen compatibel te maken met 6.5:

Zorg ervoor dat u [AEM compatibiliteitspakket](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) vooraf hebt geïnstalleerd.

1. Installeer het nieuwste 6.5- [compatibiliteitspakket](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html).

   Zie [Werken met pakketten](/help/sites-administering/package-manager.md)voor meer informatie over het uploaden en installeren van het pakket.

1. Start de server opnieuw nadat de logbestanden zijn gestabiliseerd.
1. Gebruik het migratiehulpprogramma om uw middelen compatibel te maken met 6.5.

   Zie [migratiehulpprogramma](../../forms/using/migration-utility.md)voor meer informatie.

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

