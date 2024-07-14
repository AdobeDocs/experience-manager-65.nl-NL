---
title: Omleidingspagina configureren
description: Nadat u een adaptief formulier hebt ingevuld, kunnen gebruikers worden omgeleid naar een webpagina die formulierauteurs kunnen configureren tijdens het maken van het formulier.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: be1a774f-5681-443f-b195-28e89a020547
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '303'
ht-degree: 1%

---

# Omleidingspagina configureren{#configuring-redirect-page}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-redirect-page.html) |
| AEM 6,5 | Dit artikel |

Formulierauteurs kunnen een pagina configureren voor elk formulier, waarnaar de formuliergebruikers worden omgeleid na het verzenden van een formulier.

1. Op geef wijze uit, selecteer een component, dan klik ![ gebied-niveau ](assets/field-level.png) > **Aangepaste Container van de Vorm**, en klik dan ![ cmp ](assets/cmppr.png).

1. In sidebar, klik **Verzending**.

1. Geef de URL van de omleidingspagina op onder Vorige pagina in de sectie Verzending.
1. Naar keuze, onder Verzenden Actie, voor Submit aan de het eindpuntactie van REST, kunt u de parameter vormen die tot de omleidingspagina wordt overgegaan.

![ Richt paginasonfiguratie ](assets/thank-you-setting-1.png) opnieuw

Pagina-configuratie omleiden

Auteurs van formulieren kunnen de volgende parameters gebruiken die worden doorgegeven aan de pagina Bedankt. Voor alle beschikbare verzendacties worden de parameters `status` en `owner` doorgegeven. Naast deze twee parameters worden enkele aanvullende parameters doorgegeven voor de volgende verzendacties:

* **de inhoudshandeling van de Opslag** (afgekeurd): `contentPath` - de weg van de knoop in de bewaarplaats waar het voorgelegde gegeven wordt opgeslagen-wordt overgegaan.

* **de actie van de Opslag PDF** (afgekeurd): `contentPath` - van de voorgelegde gegevens en weg aan de knoop die het dossier van de PDF opslaan in bewaarplaats-wordt overgegaan.

* **voorleggen aan het werkschema van Forms**: De parameters van de Output die van vormenwerkschema zijn teruggekeerd worden overgegaan.

* **legt aan REST eindpunt** voor: De parameters die voor binnen-gebied aan parameterafbeelding worden toegevoegd worden overgegaan. `status` - en `owner` -parameters worden niet doorgegeven in deze verzendactie. Voor meer informatie, zie [ Vormend Submit aan REST eindpunt voorlegt actie ](../../forms/using/configuring-submit-actions.md) voor.
