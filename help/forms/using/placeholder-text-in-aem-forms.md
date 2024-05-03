---
title: Plaatsaanduidingstekst in AEM Forms
description: Plaatsaanduidingstekst is bedoeld om de gebruiker te helpen bij het invoeren van gegevens wanneer het besturingselement geen waarde heeft. Dit kan een samplewaarde of een korte beschrijving van de verwachte indeling zijn.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 6b6e27b5-8b4e-489c-9e72-4d256692c1ca
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Plaatsaanduidingstekst in AEM Forms {#placeholder-text-in-aem-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

De plaatsaanduidingstekst vertegenwoordigt een woord of korte woordgroep. Het is bedoeld om de gebruiker van gegevensingang te helpen wanneer de controle geen waarde heeft. Een plaatsaanduidingstekst kan een voorbeeldwaarde of een korte beschrijving van de verwachte indeling zijn. De tekst van de plaatsaanduiding wordt weergegeven voordat de gebruiker een waarde invoert. De tekst wordt verwijderd wanneer de gebruiker een waarde invoert of selecteert.

>[!NOTE]
>
>De plaatsaanduidingstekst moet, indien opgegeven, een waarde hebben die geen nieuwe regeltekens bevat.

![Datumcomponent met en zonder plaatsaanduidingstekst](assets/dat-picker-place-holder-text.png)

**A.** De component van de datum met placeholder tekst **B.** Datumcomponent zonder plaatsaanduidingstekst

AEM Forms biedt ondersteuning voor plaatsaanduidingstekst voor de velden Wachtwoord, Datumkiezer, Numeriek vak en Tekstvak.\
Plaatsaanduidingsteksten worden niet ondersteund voor de native HTML5-datumwidget. Een plaatsaanduidingstekst opgeven:

1. Klik met de rechtermuisknop op een component die plaatsaanduidingstekst ondersteunt en klik op **Bewerken**. Het dialoogvenster Component bewerken wordt geopend.

1. Open de **Titel en tekst** tab.
1. Geef een woord of korte woordgroep op in het dialoogvenster **Tekstvak voor plaatsaanduiding**. Klikken **OK**.

>[!NOTE]
>
>Plaatsaanduidingstekst wordt niet ondersteund in Microsoft Internet Explorer 9.
