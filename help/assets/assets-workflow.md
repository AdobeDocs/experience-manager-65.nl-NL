---
title: De activa van het proces om bedrijfsprocessen te verwezenlijken, controles te doen, naleving te bereiken, en basishygiëne te handhaven
description: Middelenverwerking voor het converteren van indelingen, het maken van uitvoeringen, het beheren van elementen, het valideren van elementen en het uitvoeren van workflows.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Digitale middelen verwerken {#process-assets}

[!DNL Adobe Experience Manager Assets] kunt u op verschillende manieren werken aan uw digitale elementen, zodat u robuuste elementen kunt verwerken. U kunt de standaard of aangepaste verwerkingsmethodes gebruiken om bedrijfsprocesvoltooiing, controles en naleving, ontdekking en distributie, en basishygiëne van uw digitale activa te verzekeren. U kunt de taken voor middelenbeheer uitvoeren en tegelijkertijd de vereiste schaal en aanpassing realiseren.

## Workflows begrijpen {#understand-workflows}

Voor middelenverwerking [!DNL Experience Manager] worden workflows gebruikt. Workflows helpen de bedrijfslogica of -activiteiten te automatiseren. De korrelige stappen om specifieke taken te verwezenlijken worden verstrekt door gebrek en de ontwikkelaars kunnen hun eigen douanestappen tot stand brengen. Deze stappen kunnen in een logische volgorde worden gecombineerd om workflows te maken. Een workflow kan bijvoorbeeld watermerken toepassen op geüploade afbeeldingen op basis van specifieke criteria, zoals de map waarnaar de afbeelding is geüpload, de resolutie van de afbeelding, enzovoort. Een ander voorbeeld is een workflow die is geconfigureerd voor watermerken en die tegelijkertijd metagegevens toevoegt, uitvoeringen maakt, intelligente tags toevoegt en publiceert naar een datastore.

## Standaardworkflows beschikbaar in [!DNL Experience Manager]{#default-workflows}

Standaard worden alle geüploade elementen verwerkt met de workflow [!UICONTROL DAM Update Asset] . De workflow wordt uitgevoerd voor elk geüpload element en voert basistaken voor middelenbeheer uit, zoals het genereren van uitvoeringen, het terugsturen van metagegevens, het uitnemen van pagina&#39;s, het uitnemen van media en het transcoderen.

Zie **[!UICONTROL Opties > Workflow > Modellen]** in voor informatie over de verschillende workflowmodellen die standaard beschikbaar zijn [!DNL Experience Manager].

![Een deel van de standaardworkflow](assets/aem-default-workflows.png)

*Afbeelding: Enkele standaardworkflows beschikbaar in[!DNL Experience Manager].*

## Workflows toepassen om elementen te verwerken {#applying-workflows-to-assets}

Workflows toepassen op digitale elementen is hetzelfde als voor websitepagina&#39;s. Zie workflows [starten voor een complete handleiding over het maken en gebruiken van workflows](/help/sites-authoring/workflows-participating.md).

Gebruik workflows in digitale elementen om het element te activeren of watermerken te maken. Veel van de workflows voor elementen worden automatisch ingeschakeld. De workflow die automatisch een uitvoering maakt nadat een afbeelding is bewerkt, wordt bijvoorbeeld automatisch ingeschakeld.

>[!NOTE]
>
>Zie workflowmodellen [!UICONTROL maken als er geen workflow beschikbaar is in de klassieke gebruikersinterface die Touch ondersteunt, zoals] Verzoek om activering [!UICONTROL en]Verzoek om deactivering [](/help/sites-developing/workflows-models.md#classic2touchui).

## Een workflow toepassen op een element {#apply-a-workflow-to-an-asset}

<!-- 
TBD: Add animated GIF for these steps instead of all these screenshots.
-->
Voer de volgende stappen uit om een workflow toe te passen op een element:

1. Navigeer naar de locatie van het element waarvoor u een workflow wilt starten en klik op het element om de elementpagina te openen. Selecteer **[!UICONTROL Tijdlijn]** in het menu om de tijdlijn weer te geven.

   ![timeline-1](assets/timeline.png)

1. Klik op **[!UICONTROL Handelingen]** onderaan om de lijst met acties te openen die beschikbaar zijn voor het element.

1. Klik in de lijst op Workflow **** starten.

1. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-254](assets/chlimage_1-50.png)

1. (Optioneel) Geef een titel op voor de workflow die kan worden gebruikt om naar de instantie van de workflow te verwijzen.

   ![chlimage_1-255](assets/chlimage_1-51.png)

1. Klik op **[!UICONTROL Start]** en vervolgens op **[!UICONTROL Doorgaan]**. Elke stap van de workflow wordt als een gebeurtenis in de tijdlijn weergegeven.

   ![chlimage_1-256](assets/chlimage_1-52.png)

## Een workflow toepassen op meerdere elementen {#applying-a-workflow-to-multiple-assets}

1. Navigeer in de middelenconsole naar de locatie van de elementen waarvoor u een workflow wilt starten en selecteer de elementen. Selecteer **[!UICONTROL Tijdlijn]** in het menu om de tijdlijn weer te geven.

   ![screen_shot_2019-03-06at123325pm](assets/chlimage_1-136.png)

1. Klik op **[!UICONTROL Handelingen]** onderaan.

   ![chlimage_1-30](assets/chlimage_1-137.png)

1. Klik op Workflow **** starten. In the **[!UICONTROL Start Workflow]** dialog, select a workflow model from the list.

   ![chlimage_1-31](assets/chlimage_1-138.png)

1. (Optioneel) Geef een titel voor de workflow op, die kan worden gebruikt om naar de instantie van de workflow te verwijzen.
1. Click **[!UICONTROL Start]** and then click **[!UICONTROL Confirm]** in the dialog. De workflow wordt uitgevoerd op alle assets die u hebt geselecteerd.

## Een workflow toepassen op meerdere mappen {#applying-a-workflow-to-multiple-folders}

De procedure voor het toepassen van een workflow op meerdere mappen is vergelijkbaar met de procedure voor het toepassen van een workflow op meerdere elementen. Selecteer de mappen in de [!DNL Assets] interface en voer stap 2-7 van de procedure uit om een workflow op meerdere elementen [toe te](/help/assets/assets-workflow.md#applying-a-workflow-to-multiple-assets)passen.

## Een workflow toepassen op een verzameling {#applying-a-workflow-to-a-collection}

Zie een workflow [toepassen op een verzameling](/help/assets/managing-collections-touch-ui.md#running-a-workflow-on-a-collection).

## Een workflow automatisch starten om elementen voorwaardelijk te verwerken {#auto-execute-workflow-on-some-assets}

Beheerders kunnen de workflow zodanig configureren dat elementen automatisch worden uitgevoerd en verwerkt op basis van vooraf gedefinieerde voorwaarden. De functionaliteit is bijvoorbeeld handig voor zakelijke gebruikers en marketers om een aangepaste workflow voor specifieke mappen te maken. Alle elementen van de foto&#39;s van een agentschap kunnen van een watermerk zijn voorzien of alle elementen die door een freelancer zijn geüpload, kunnen worden verwerkt om specifieke uitvoeringen te maken.

Voor een workflowmodel kunnen gebruikers een workflowstartprogramma maken dat deze uitvoert. Een werkstroomopstarter bewaakt wijzigingen in de inhoudsopslagplaats en voert de werkstroom uit wanneer aan de vooraf gedefinieerde voorwaarden is voldaan. Beheerders kunnen toegang verlenen tot marketers om de workflows te maken en de starcher te configureren. Gebruikers kunnen de standaard [!UICONTROL DAM Update Asset] -workflow wijzigen en zo de extra stappen toevoegen die nodig zijn om specifieke elementen te verwerken. De workflow wordt uitgevoerd op alle nieuw geüploade elementen. Gebruik een van de volgende methoden om de uitvoering van de extra stappen voor specifieke elementen te beperken:

* Maak een kopie van de workflow [!UICONTROL DAM Update Asset] en wijzig deze om uit te voeren in een specifieke maphiërarchie. Deze aanpak is handig voor een aantal mappen.
* De extra verwerkingsstappen kunnen worden toegevoegd met behulp van een [OR-splitsing](/help/sites-developing/workflows-step-ref.md#or-split) , afhankelijk van wat er nodig is voor zoveel mappen.

>[!MORELIKETHIS]
>
>* [Toepassen en deelnemen aan workflows](/help/sites-authoring/workflows.md)
>* [Workflowmodellen maken en workflowfunctionaliteit uitbreiden](/help/sites-developing/workflows.md)
>* [Methoden voor het uitvoeren van workflows](/help/sites-administering/workflows-starting.md)
>* [Best practices voor workflows](/help/sites-developing/workflows-best-practices.md)
>* [Communautair artikel over het wijzigen van elementen met behulp van workflow](https://helpx.adobe.com/experience-manager/using/modify_asset_workflow.html)

