---
title: Omleidingspagina configureren
seo-title: Omleidingspagina configureren
description: Nadat u een adaptief formulier hebt ingevuld, kunnen gebruikers worden omgeleid naar een webpagina die formulierauteurs kunnen configureren tijdens het maken van het formulier.
seo-description: Nadat u een adaptief formulier hebt ingevuld, kunnen gebruikers worden omgeleid naar een webpagina die formulierauteurs kunnen configureren tijdens het maken van het formulier.
uuid: f9d304b4-920d-4e50-a674-40eca48c530c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 0ffbb4d3-9371-4705-8496-f98e22d9c4a6
docset: aem65
translation-type: tm+mt
source-git-commit: 8e724af4d69cb859537dd088119aaca652ea3931
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---


# Omleidingspagina configureren{#configuring-redirect-page}

Formulierauteurs kunnen een pagina configureren voor elk formulier, waarnaar de formuliergebruikers worden omgeleid na het verzenden van een formulier.

1. Selecteer in de bewerkingsmodus een component en klik op ![veldniveau](assets/field-level.png) > **Aangepaste formuliercontainer**. Klik vervolgens op ![cmp](assets/cmppr.png).

1. Klik in de zijbalk op **Verzending**.

1. Geef de URL van de omleidingspagina op onder Vorige pagina in de sectie Verzending.
1. Naar keuze, onder Verzenden Actie, voor Submit aan de het eindpuntactie van REST, kunt u de parameter vormen die tot de omleidingspagina wordt overgegaan.

![Pagina-configuratie omleiden](assets/thank-you-setting-1.png)

Pagina-configuratie omleiden

Auteurs van formulieren kunnen de volgende parameters gebruiken die worden doorgegeven aan de pagina Bedankt. Voor alle beschikbare verzendacties worden `status`- en `owner`-parameters doorgegeven. Naast deze twee parameters worden enkele aanvullende parameters doorgegeven voor de volgende verzendacties:

* **Handeling**  voor inhoud opslaan (afgekeurd):  `contentPath`—het pad van het knooppunt in de gegevensopslagruimte waar de verzonden gegevens worden opgeslagen—wordt doorgegeven.

* **PDF-handeling**  opslaan (afgekeurd):  `contentPath`—van de verzonden gegevens en het pad naar het knooppunt dat het PDF-bestand in de gegevensopslagruimte opslaat—wordt doorgegeven.

* **Verzenden naar Forms-workflow**: Uitvoerparameters die worden geretourneerd uit de formulierwerkstroom, worden doorgegeven.

* **Verzenden naar REST-eindpunt**: Parameters die voor parametertoewijzing in het veld worden toegevoegd, worden doorgegeven. `status` en er worden geen  `owner` parameters doorgegeven in deze verzendactie. Voor meer informatie, zie [Vormend Submit aan het eindpunt REST verzenden actie](../../forms/using/configuring-submit-actions.md).

