---
title: portalcomponenten voor formulieren inschakelen
seo-title: portalcomponenten voor formulieren inschakelen
description: Forms Portal-componenten zijn uitgeschakeld. Schakel Document Services en Document Services Predicates-groepen in om Forms Portal-componenten in te schakelen.
seo-description: Forms Portal-componenten zijn uitgeschakeld. Schakel Document Services en Document Services Predicates-groepen in om Forms Portal-componenten in te schakelen.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
feature: Forms Portal
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Formulierportonderdelen inschakelen {#enabling-forms-portal-components}

De onderdelen van de portal Formulieren zijn niet beschikbaar voor gebruik. Voer de volgende stappen uit om de componenten weer te geven in de lijst met beschikbare componenten in AEM sidekick:

1. Meld u aan bij de auteur van uw website en open een AEM Sites-pagina.

1. Voer de volgende stappen uit voor de pagina&#39;s die een statische sjabloon gebruiken:

   1. Tik in de paginakoptekst op ![canvas-drop-down](assets/canvas-drop-down.png) > **Design** om de pagina in de ontwerpmodus te openen.
   1. Tik op een component (met een blauwe rand) en tik op ![veldniveau](assets/field-level.png) om het alineasysteem met de huidige component te selecteren.
   1. Tik in het alineasysteem op ![settings_icon](assets/settings_icon.png) om het dialoogvenster Bewerken voor het alineasysteem te openen.
   1. Schakel in de lijst met **[!UICONTROL Allowed Components]** selectievakjes in voor **[!UICONTROL Document Services]**- en **[!UICONTROL Document Services Predicates]**-componenten. Tik op **[!UICONTROL OK]**.

1. Voer de volgende stappen uit voor de pagina&#39;s die een dynamische sjabloon gebruiken:

   1. Tik in de paginakoptekst op ![eigenschappen](assets/properties.png) > **Sjabloon bewerken** om de sjabloon van de pagina te openen.
   1. Tik **Container voor lay-out** en tik ![FeedManagement](/help/forms/using/assets/feedmanagement.png). Schakel op het tabblad **Toegestane componenten** de opties **Documentservices en Voorspelden documentservices** in en tik op ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>U kunt ook specifieke componenten van deze categorieën inschakelen door de componenten te selecteren. Zie [Een pagina voor een formulierportal maken](/help/forms/using/creating-form-portal-page.md) en [Koppelingscomponent insluiten in een pagina](/help/forms/using/embedding-link-component-page.md) voor meer informatie over de componenten en hun gebruik.

De componentcategorieën Document Services en Document Services Predicates zijn nu beschikbaar in de componentbrowser. De componenten worden ingeschakeld voor alle pagina&#39;s die dezelfde sjabloon gebruiken.

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
