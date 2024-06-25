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

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-redirect-page.html) |
| AEM 6,5 | Dit artikel |

Formulierauteurs kunnen een pagina configureren voor elk formulier, waarnaar de formuliergebruikers worden omgeleid na het verzenden van een formulier.

1. Selecteer in de bewerkingsmodus een component en klik vervolgens op ![op veldniveau](assets/field-level.png) > **Aangepaste formuliercontainer** en klik vervolgens op ![cmppr](assets/cmppr.png).

1. Klik in de zijbalk op **Indiening**.

1. Geef de URL van de omleidingspagina op onder Vorige pagina in de sectie Verzending.
1. Naar keuze, onder Verzenden Actie, voor Submit aan de het eindpuntactie van REST, kunt u de parameter vormen die tot de omleidingspagina wordt overgegaan.

![Pagina-configuratie omleiden](assets/thank-you-setting-1.png)

Pagina-configuratie omleiden

Auteurs van formulieren kunnen de volgende parameters gebruiken die worden doorgegeven aan de pagina Bedankt. Voor alle beschikbare verzendacties: `status` en `owner` parameters worden doorgegeven. Naast deze twee parameters worden enkele aanvullende parameters doorgegeven voor de volgende verzendacties:

* **Winkelinhoud, actie** (afgekeurd) : `contentPath`—het pad van het knooppunt in de gegevensopslagruimte waar de verzonden gegevens worden opgeslagen—wordt doorgegeven.

* **PDF opslaan** (afgekeurd) : `contentPath`—van de voorgelegde gegevens en de weg aan de knoop die het PDF dossier in bewaart in bewaarplaats-wordt overgegaan.

* **Verzenden naar Forms-workflow**: Uitvoerparameters die worden geretourneerd uit de formulierwerkstroom, worden doorgegeven.

* **Verzenden naar REST-eindpunt**: Parameters die voor parametertoewijzing in het veld zijn toegevoegd, worden doorgegeven. `status` en `owner` parameters worden niet doorgegeven in deze verzendactie. Zie voor meer informatie [Het vormen van Submit aan het eindpunt REST legt actie voor](../../forms/using/configuring-submit-actions.md).
