---
title: Compatibiliteitspakket
description: Als u het compatibiliteitspakket op AEM Forms 6.5 installeert, kunt u de Correspondentenbeheermiddelen van AEM Forms 6.4 en eerdere versies en afgekeurde adaptieve formuliersjablonen en pagina's gebruiken
contentOwner: gtalwar
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management, installing
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin,User
exl-id: bb16017c-a1bf-40d8-a78d-827c05b7ee2e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '355'
ht-degree: 0%

---

# Compatibiliteitspakket{#compatibility-package}

## Overzicht {#overview}

De interactieve mededeling is het gebrek en geadviseerde benadering om klantenmededelingen in AEM Forms 6.5 tot stand te brengen. Om brieven in AEM Forms 6.5 te blijven gebruiken, moet u het recentste [&#x200B; pakket van de Verenigbaarheid AEMFD &#x200B;](https://helpx.adobe.com/nl/aem-forms/kb/aem-forms-releases.html) installeren.

Het pakket van de Verenigbaarheid AEMFD laat u [&#x200B; ook de volgende activa van AEM Forms 6.4, 6.3 en 6.2 op AEM Forms 6.5 gebruiken:](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms)

* Documentfragmenten
* Letters
* Gegevenswoordenboeken
* Afgekeurde sjablonen en pagina&#39;s voor adaptieve formulieren

Voor meer informatie, zie [&#x200B; Assets compatibel gemaakt met AEM Forms 6.5 door het pakket van de Verenigbaarheid &#x200B;](../../forms/using/compatibility-package.md#assetsmadecompatible) te installeren.

## Voeg ondersteuning toe voor AEM Forms 6.4-, 6.3- en 6.2-middelen in AEM Forms 6.5 {#add-support-for-aem-forms-and-assets-in-aem-forms}

Nadat u een upgrade hebt uitgevoerd, voert u de volgende handelingen uit om het compatibiliteitspakket voor AEMFD te installeren en uw elementen compatibel te maken met 6.5:

Zorg ervoor dat u [&#x200B; AEM het pakket van de Verenigbaarheid &#x200B;](https://helpx.adobe.com/nl/aem-forms/kb/aem-forms-releases.html) vooraf geïnstalleerd hebt.

1. Installeer het recentste 6.5 [&#x200B; pakket van de Verenigbaarheid &#x200B;](https://helpx.adobe.com/nl/aem-forms/kb/aem-forms-releases.html).

   Voor meer informatie bij het uploaden en het installeren van het pakket, zie [&#x200B; hoe te met pakketten &#x200B;](/help/sites-administering/package-manager.md) werken.

1. Start de server opnieuw nadat de logbestanden zijn gestabiliseerd.
1. Gebruik het migratiehulpprogramma om uw middelen compatibel te maken met 6.5.

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

   Voor meer informatie, zie [&#x200B; migratienut &#x200B;](../../forms/using/migration-utility.md).

## Assets is compatibel gemaakt met AEM Forms 6.5 door het compatibiliteitspakket te installeren {#assetsmadecompatible}

Door het compatibiliteitspakket te installeren, kunt u de volgende elementen en sjablonen compatibel maken met AEM Forms 6.5:

* Correspondentenbeheer Assets van AEM 6.4 en eerder:

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
