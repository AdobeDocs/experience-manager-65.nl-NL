---
title: Omleidingspagina configureren
seo-title: Configuring redirect page
description: Nadat u een adaptief formulier hebt ingevuld, kunnen gebruikers worden omgeleid naar een webpagina die formulierauteurs kunnen configureren tijdens het maken van het formulier.
seo-description: After filling an adaptive form, users can be redirected to a webpage that form authors can configure while creating the form.
uuid: f9d304b4-920d-4e50-a674-40eca48c530c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 0ffbb4d3-9371-4705-8496-f98e22d9c4a6
docset: aem65
feature: Adaptive Forms
exl-id: be1a774f-5681-443f-b195-28e89a020547
source-git-commit: 1683338f02d01d5d9843368955fa42f309718f26
workflow-type: tm+mt
source-wordcount: '260'
ht-degree: 1%

---

# Omleidingspagina configureren{#configuring-redirect-page}

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

* **Verzenden naar REST-eindpunt**: Parameters die voor parametertoewijzing in het veld worden toegevoegd, worden doorgegeven. `status` en `owner` parameters worden niet doorgegeven in deze verzendactie. Zie voor meer informatie [Het vormen van Submit aan het eindpunt REST legt actie voor](../../forms/using/configuring-submit-actions.md).
