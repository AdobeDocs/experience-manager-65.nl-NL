---
title: Asynchrone indiening van adaptieve formulieren
description: Leer asynchrone verzending voor adaptieve formulieren te configureren.
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: bd0589e2-b15a-4f0e-869c-2da4760b1ff4
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 0%

---

# Asynchrone indiening van adaptieve formulieren{#asynchronous-submission-of-adaptive-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/asynchronous-submissions-adaptive-forms.html) |
| AEM 6,5 | Dit artikel |

Webformulieren zijn meestal geconfigureerd voor synchroon verzenden. Bij synchrone verzending worden gebruikers die een formulier verzenden, omgeleid naar een bevestigingspagina, een pagina voor dankbetuigingen of een pagina met foutmeldingen als gevolg van een mislukte verzending. De moderne webervaringen, zoals toepassingen met één pagina, worden echter steeds populairder, omdat de webpagina statisch blijft terwijl interactie tussen client en server op de achtergrond plaatsvindt. U kunt deze ervaring nu voorzien van adaptieve formulieren door asynchrone verzending te configureren.

Wanneer een gebruiker een formulier verzendt bij asynchrone verzending, voegt de ontwikkelaar een aparte ervaring in, zoals het omleiden naar een ander formulier of een aparte sectie van de website. De auteur kan ook afzonderlijke services insluiten, zoals het verzenden van gegevens naar een andere gegevensopslagruimte of het toevoegen van een aangepaste analytische engine. Als er asynchrone verzending is, gedraagt een adaptief formulier zich als een toepassing op één pagina, aangezien het formulier niet opnieuw wordt geladen of de URL niet verandert wanneer de verzonden formuliergegevens op de server worden gevalideerd.

Lees verder voor meer informatie over asynchrone verzending in adaptieve formulieren.

## asynchrone verzending configureren {#configure}

Om asynchrone voorlegging voor een adaptief formulier te configureren:

1. Selecteer in de ontwerpmodus het object Form Container en selecteer ![cmppr1](assets/cmppr1.png) om de eigenschappen te openen.
1. In de **[!UICONTROL Submission]** eigenschappensectie, inschakelen **[!UICONTROL Use asynchronous submission]**.
1. In de **[!UICONTROL On Submit]** selecteert u een van de volgende opties voor het verzenden van formulieren.

   * **[!UICONTROL Redirect to URL]**: leidt bij het verzenden van het formulier naar de opgegeven URL of pagina. U kunt een URL opgeven of bladeren naar het pad naar een pagina in het dialoogvenster **[!UICONTROL Redirect URL/Path]** veld.
   * **[!UICONTROL Show Message]**: geeft een bericht weer bij het verzenden van het formulier. U kunt een bericht schrijven in het tekstveld onder de optie Bericht tonen. Het tekstveld ondersteunt RTF-opmaak.

1. Selecteren ![check-button1](assets/check-button1.png) om de eigenschappen op te slaan.

## Hoe asynchrone verzending werkt {#how-asynchronous-submission-works}

AEM Forms biedt offline succeshandlers en foutafhandelaars voor het verzenden van formulieren. Handlers zijn client-side functies die worden uitgevoerd op basis van de serverreactie. Wanneer een formulier wordt verzonden, worden de gegevens voor validatie naar de server verzonden, die een reactie op de client retourneert met informatie over de gebeurtenis &#39;success&#39; of &#39;error&#39; voor de verzending. De informatie wordt als parameters doorgegeven aan de relevante handler om de functie uit te voeren.

Bovendien kunnen auteurs en ontwikkelaars van formulieren regels op formulierniveau schrijven om standaardhandlers te overschrijven. Zie voor meer informatie [Standaardhandlers negeren met behulp van regels](#custom).

Laat ons eerst de serverreactie voor succes en foutengebeurtenissen herzien.

### Serverreactie voor gebeurtenis met succes voor verzending {#server-response-for-submission-success-event}

De structuur voor de serverreactie voor het indienen van succesgebeurtenissen is als volgt:

```json
{
  contentType : "<xmlschema or jsonschema>",
  data : "<dataXML or dataJson>" ,
  thankYouOption : <page/message>,
  thankYouContent : "<thank you page url/thank you message>"
}
```

De reactie van de server als het formulier met succes is verzonden, is onder meer:

* Formuliergegevensindelingstype: XML of JSON
* Formuliergegevens in XML- of JSON-indeling
* Geselecteerde optie om naar een pagina om te leiden of een bericht te tonen zoals die in vorm wordt gevormd
* Pagina-URL of inhoud van bericht zoals geconfigureerd in het formulier

De succesmanager leest de serverreactie en richt dienovereenkomstig aan de gevormde pagina URL of toont een bericht opnieuw.

### Serverreactie voor verzendfoutgebeurtenis {#server-response-for-submission-error-event}

De structuur voor de serverreactie voor de gebeurtenis van de voorleggingsfout is als volgt:

```json
{
   errorCausedBy : "<CAPTCHA_VALIDATION or SERVER_SIDE_VALIDATION>",

   errors : [
               { "somExpression" : "<SOM Expression>",
                 "errorMessage"  : "<Error Message>"
               },
               ...
             ]
 }
```

De reactie van de server als er een fout optreedt bij het verzenden van het formulier, omvat:

* Reden voor de fout, mislukte CAPTCHA- of servervalidatie
* Lijst met foutobjecten, die de SOM-expressie bevat van het veld waarvan de validatie is mislukt en het bijbehorende foutbericht

De fouthandler leest de serverreactie en geeft dienovereenkomstig het foutbericht op het formulier weer.

## Standaardhandlers negeren met behulp van regels {#custom}

Formulierontwikkelaars en auteurs kunnen regels schrijven op formulierniveau in de code-editor om standaardhandlers te overschrijven. De serverreactie voor geluids- en foutgebeurtenissen wordt weergegeven op formulierniveau, waartoe ontwikkelaars toegang hebben via `$event.data` in regels.

Voer de volgende stappen uit om regels in coderedacteur te schrijven om succes en foutengebeurtenissen te behandelen.

1. Open het adaptieve formulier in de ontwerpmodus, selecteer een willekeurig formulierobject en selecteer ![edit-rules1](assets/edit-rules1.png) om de regeleditor te openen.
1. Selecteren **[!UICONTROL Form]** in de structuur Formulierobjecten en selecteer **[!UICONTROL Create]**.
1. Selecteren **[!UICONTROL Code Editor]** in het vervolgkeuzemenu Modus selecteren.
1. Selecteer in de code-editor de optie **[!UICONTROL Edit Code]**. Selecteren **[!UICONTROL Edit]** in het bevestigingsdialoogvenster.
1. Kies **[!UICONTROL Successful Submission]** of **[!UICONTROL Error in Submission]** van de **[!UICONTROL Event]** vervolgkeuzelijst.
1. Schrijf een regel voor de geselecteerde gebeurtenis en selecteer **[!UICONTROL Done]** om de regel op te slaan.
