---
title: portalcomponenten voor formulieren inschakelen
seo-title: Enabling forms portal components
description: Forms Portal-componenten zijn uitgeschakeld. Schakel Document Services en Document Services Predicates-groepen in om Forms Portal-componenten in te schakelen.
seo-description: Out of the box, Forms Portal components are disabled. Enable Document Services and Document Services Predicates groups to enable Forms Portal components.
uuid: 92d25da6-f1df-4ac0-bf84-2edf9e2722b3
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
discoiquuid: 4d318908-c724-4582-a82b-6e9b1c55705b
feature: Forms Portal
exl-id: 572194b7-063b-4c38-af43-aba78e9c51c6
source-git-commit: bd86d647fdc203015bc70a0f57d5b94b4c634bf9
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 1%

---

# portalcomponenten voor formulieren inschakelen {#enabling-forms-portal-components}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html) |
| AEM 6,5 | Dit artikel |

De onderdelen van de portal Formulieren zijn niet beschikbaar voor gebruik. Voer de volgende stappen uit om de componenten weer te geven in de lijst met beschikbare componenten in AEM sidekick:

1. Meld u aan bij de auteur van uw website en open een AEM Sites-pagina.

1. Voer de volgende stappen uit voor de pagina&#39;s die een statische sjabloon gebruiken:

   1. Selecteer in de koptekst van de pagina de optie ![canvas-drop-down](assets/canvas-drop-down.png) > **Ontwerp** om de pagina in de ontwerpmodus te openen.
   1. Selecteer een component (met een blauwe rand) en selecteer vervolgens ![op veldniveau](assets/field-level.png) om het alineasysteem te selecteren dat de huidige component bevat.
   1. Selecteer in het alineasysteem ![settings_icon](assets/settings_icon.png) om het dialoogvenster Bewerken voor het alineasysteem te openen.
   1. Uit de lijst met **[!UICONTROL Allowed Components]** Schakel selectievakjes in voor **[!UICONTROL Document Services]** en **[!UICONTROL Document Services Predicates]** componenten. Selecteren **[!UICONTROL OK]**.

1. Voer de volgende stappen uit voor de pagina&#39;s die een dynamische sjabloon gebruiken:

   1. Selecteer in de koptekst van de pagina de optie ![eigenschappen](assets/properties.png) > **Sjabloon bewerken** om de sjabloon van de pagina te openen.
   1. Selecteren **Layout Container** en selecteert u ![FeedManagement](/help/forms/using/assets/feedmanagement.png). In de **Toegestane componenten** tabblad, schakelt u de **Documentservices en prognoses voor documentservices** en selecteert u ![aem_6_3_forms_save](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>U kunt ook specifieke componenten van deze categorieën inschakelen door de componenten te selecteren. Voor meer informatie over de componenten en hun gebruik, zie [Een pagina met een formulierportal maken](/help/forms/using/creating-form-portal-page.md) en [Koppelingscomponent insluiten in een pagina](/help/forms/using/embedding-link-component-page.md).

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
