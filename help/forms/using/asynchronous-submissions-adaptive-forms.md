---
title: Asynchrone indiening van adaptieve formulieren
seo-title: Asynchrone indiening van adaptieve formulieren
description: Leer asynchrone verzending voor adaptieve formulieren te configureren.
seo-description: Leer asynchrone verzending voor adaptieve formulieren te configureren.
uuid: 6555ac63-4d99-4b39-a2d0-a7e61909106b
contentOwner: vishgupt
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 0a0d2109-ee1f-43f6-88e5-1108cd215da6
docset: aem65
feature: Adaptieve Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 0%

---


# Asynchrone indiening van adaptieve formulieren{#asynchronous-submission-of-adaptive-forms}

Webformulieren zijn meestal geconfigureerd voor synchroon verzenden. Bij synchrone verzending worden gebruikers die een formulier verzenden, omgeleid naar een bevestigingspagina, een pagina voor bedankt of een pagina voor een fout bij het verzenden. De moderne webervaringen, zoals toepassingen met één pagina, worden echter steeds populairder, omdat de webpagina statisch blijft terwijl interactie tussen client en server op de achtergrond plaatsvindt. U kunt deze ervaring nu voorzien van adaptieve formulieren door asynchrone verzending te configureren.

Wanneer een gebruiker een formulier verzendt bij asynchrone verzending, voegt de ontwikkelaar een aparte ervaring in, zoals het omleiden naar een ander formulier of een aparte sectie van de website. De auteur kan ook aparte services insluiten, zoals het verzenden van gegevens naar een andere gegevensopslagruimte of het toevoegen van een aangepaste engine voor analyse. In geval van asynchrone verzending gedraagt een adaptief formulier zich als een toepassing van één pagina, aangezien het formulier niet opnieuw wordt geladen of de URL niet verandert wanneer de verzonden formuliergegevens op de server worden gevalideerd.

Lees verder voor meer informatie over asynchrone verzending in adaptieve formulieren.

## asynchrone verzending {#configure} configureren

Om asynchrone voorlegging voor een adaptief formulier te configureren:

1. Selecteer in de modus Aangepast formulier het object Form Container en tik op ![cmp1](assets/cmppr1.png) om de eigenschappen ervan te openen.
1. Schakel in de sectie **[!UICONTROL Submission]** eigenschappen **[!UICONTROL Use asynchronous submission]** in.
1. Selecteer in de sectie **[!UICONTROL On Submit]** een van de volgende opties voor het verzenden van formulieren.

   * **[!UICONTROL Redirect to URL]**: Hiermee wordt de opgegeven URL of pagina bij het verzenden van het formulier gebruikt. U kunt een URL opgeven of bladeren om het pad naar een pagina te kiezen in het veld **[!UICONTROL Redirect URL/Path]**.
   * **[!UICONTROL Show Message]**: Hiermee wordt een bericht weergegeven bij het verzenden van het formulier. U kunt een bericht schrijven in het tekstveld onder de optie Bericht tonen. Het tekstveld ondersteunt RTF-opmaak.

1. Tik ![check-button1](assets/check-button1.png) om de eigenschappen op te slaan.

## Hoe de asynchrone voorlegging {#how-asynchronous-submission-works} werkt

AEM Forms biedt offline succeshandlers en foutafhandelaars voor het verzenden van formulieren. Handlers zijn client-side functies die worden uitgevoerd op basis van de serverreactie. Wanneer een formulier wordt verzonden, worden de gegevens voor validatie naar de server verzonden, die een reactie op de client retourneert met informatie over de gebeurtenis &#39;success&#39; of &#39;error&#39; voor de verzending. De informatie wordt als parameters doorgegeven aan de relevante handler om de functie uit te voeren.

Bovendien kunnen auteurs en ontwikkelaars van formulieren regels op formulierniveau schrijven om standaardhandlers te overschrijven. Zie [Standaardhandlers negeren met behulp van rules](#custom) voor meer informatie.

Laat ons eerst de serverreactie voor succes en foutengebeurtenissen herzien.

### Serverreactie voor gebeurtenis {#server-response-for-submission-success-event} met succes voor verzending

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

### Serverreactie voor gebeurtenis {#server-response-for-submission-error-event} van verzendfout

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

Formulierontwikkelaars en auteurs kunnen regels schrijven op formulierniveau in de code-editor om standaardhandlers te overschrijven. De serverreactie voor geluids- en foutgebeurtenissen wordt weergegeven op formulierniveau, waartoe ontwikkelaars toegang hebben met `$event.data` in regels.

Voer de volgende stappen uit om regels in coderedacteur te schrijven om succes en foutengebeurtenissen te behandelen.

1. Open het aangepaste formulier in de ontwerpmodus, selecteer een formulierobject en tik ![edit-rules1](assets/edit-rules1.png) om de regeleditor te openen.
1. Selecteer **[!UICONTROL Form]** in de structuur Formulierobjecten en tik **[!UICONTROL Create]**.
1. Selecteer **[!UICONTROL Code Editor]** van de drop-down wijze selectie.
1. Tik in de code-editor op **[!UICONTROL Edit Code]**. Tik op **[!UICONTROL Edit]** in het bevestigingsdialoogvenster.
1. Kies **[!UICONTROL Successful Submission]** of **[!UICONTROL Error in Submission]** in de vervolgkeuzelijst **[!UICONTROL Event]**.
1. Schrijf een regel voor de geselecteerde gebeurtenis en tik **[!UICONTROL Done]** om de regel op te slaan.

