---
title: Asynchrone indiening van adaptieve formulieren
seo-title: Asynchronous submission of adaptive forms
description: Leer asynchrone verzending voor adaptieve formulieren te configureren.
seo-description: Learn to configure asynchronous submission for adaptive forms.
uuid: 6555ac63-4d99-4b39-a2d0-a7e61909106b
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 0a0d2109-ee1f-43f6-88e5-1108cd215da6
docset: aem65
feature: Adaptive Forms
exl-id: bd0589e2-b15a-4f0e-869c-2da4760b1ff4
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---

# Asynchrone indiening van adaptieve formulieren{#asynchronous-submission-of-adaptive-forms}

Webformulieren zijn meestal geconfigureerd voor synchroon verzenden. Bij synchrone verzending worden gebruikers die een formulier verzenden, omgeleid naar een bevestigingspagina, een pagina voor bedankt of een pagina voor een fout bij het verzenden. De moderne webervaringen, zoals toepassingen met één pagina, worden echter steeds populairder, omdat de webpagina statisch blijft terwijl interactie tussen client en server op de achtergrond plaatsvindt. U kunt deze ervaring nu voorzien van adaptieve formulieren door asynchrone verzending te configureren.

Wanneer een gebruiker een formulier verzendt bij asynchrone verzending, voegt de ontwikkelaar een aparte ervaring in, zoals het omleiden naar een ander formulier of een aparte sectie van de website. De auteur kan ook aparte services insluiten, zoals het verzenden van gegevens naar een andere gegevensopslagruimte of het toevoegen van een aangepaste engine voor analyse. In geval van asynchrone verzending gedraagt een adaptief formulier zich als een toepassing van één pagina, aangezien het formulier niet opnieuw wordt geladen of de URL niet verandert wanneer de verzonden formuliergegevens op de server worden gevalideerd.

Lees verder voor meer informatie over asynchrone verzending in adaptieve formulieren.

## asynchrone verzending configureren {#configure}

Om asynchrone voorlegging voor een adaptief formulier te configureren:

1. Selecteer in de modus Aangepast formulier voor het schrijven van programmacode het object Form Container en tik op ![cmppr1](assets/cmppr1.png) om de eigenschappen te openen.
1. In de **[!UICONTROL Submission]** eigenschappensectie, inschakelen **[!UICONTROL Use asynchronous submission]**.
1. In de **[!UICONTROL On Submit]** selecteert u een van de volgende opties voor het verzenden van formulieren.

   * **[!UICONTROL Redirect to URL]**: Hiermee wordt de opgegeven URL of pagina bij het verzenden van het formulier gebruikt. U kunt een URL opgeven of bladeren naar het pad naar een pagina in het dialoogvenster **[!UICONTROL Redirect URL/Path]** veld.
   * **[!UICONTROL Show Message]**: Hiermee wordt een bericht weergegeven bij het verzenden van het formulier. U kunt een bericht schrijven in het tekstveld onder de optie Bericht tonen. Het tekstveld ondersteunt RTF-opmaak.

1. Tikken ![check-button1](assets/check-button1.png) om de eigenschappen op te slaan.

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

De reactie van de server in het geval van een geslaagde verzending van het formulier omvat:

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

De reactie van de server in het geval van een fout bij het verzenden van het formulier omvat:

* Reden voor de fout, mislukte CAPTCHA- of servervalidatie
* Lijst met foutobjecten, die de SOM-expressie bevat van het veld waarvan de validatie is mislukt en het bijbehorende foutbericht

De fouthandler leest de serverreactie en geeft dienovereenkomstig het foutbericht op het formulier weer.

## Standaardhandlers negeren met behulp van regels {#custom}

Formulierontwikkelaars en auteurs kunnen regels schrijven op formulierniveau in de code-editor om standaardhandlers te overschrijven. De serverreactie voor geluids- en foutgebeurtenissen wordt weergegeven op formulierniveau, waartoe ontwikkelaars toegang hebben via `$event.data` in regels.

Voer de volgende stappen uit om regels in coderedacteur te schrijven om succes en foutengebeurtenissen te behandelen.

1. Open het adaptieve formulier in de ontwerpmodus, selecteer een willekeurig formulierobject en tik op ![edit-rules1](assets/edit-rules1.png) om de regeleditor te openen.
1. Selecteren **[!UICONTROL Form]** in de structuur Formulierobjecten en tik op **[!UICONTROL Create]**.
1. Selecteren **[!UICONTROL Code Editor]** in het vervolgkeuzemenu Modus selecteren.
1. Tik in de code-editor op **[!UICONTROL Edit Code]**. Tikken **[!UICONTROL Edit]** in het bevestigingsdialoogvenster.
1. Kies **[!UICONTROL Successful Submission]** of **[!UICONTROL Error in Submission]** van de **[!UICONTROL Event]** vervolgkeuzelijst.
1. Schrijf een regel voor de geselecteerde gebeurtenis en tik op **[!UICONTROL Done]** om de regel op te slaan.
