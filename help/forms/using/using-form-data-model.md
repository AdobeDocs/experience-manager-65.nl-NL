---
title: Formuliergegevensmodel gebruiken
seo-title: Formuliergegevensmodel gebruiken
description: Leer hoe u het formuliergegevensmodel kunt gebruiken om adaptieve formulieren en interactieve communicatie te maken en te gebruiken.
seo-description: Leer hoe u het formuliergegevensmodel kunt gebruiken om adaptieve formulieren en interactieve communicatie te maken en te gebruiken.
uuid: 9d8d8f43-9a50-4905-a6ef-a5ea3b9c11f7
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
discoiquuid: 87f5f9f5-2d03-4565-830e-eacc3757e542
docset: aem65
translation-type: tm+mt
source-git-commit: ebf3f34af7da6b1a659ac8d8843152b97f30b652
workflow-type: tm+mt
source-wordcount: '1212'
ht-degree: 0%

---


# Formuliergegevensmodel gebruiken{#use-form-data-model}

![](do-not-localize/data-integeration.png)

Dankzij de gegevensintegratie van AEM Forms kunt u verschillende back-endgegevensbronnen gebruiken om een formuliergegevensmodel te maken dat u als schema kunt gebruiken in verschillende adaptieve formulieren en interactieve communicatieworkflows. Hiervoor moeten gegevensbronnen worden geconfigureerd en een formuliergegevensmodel worden gemaakt op basis van gegevensmodelobjecten en -services die beschikbaar zijn in gegevensbronnen. Raadpleeg de volgende secties voor meer informatie:

* [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md)
* [Gegevensbronnen configureren](../../forms/using/configure-data-sources.md)
* [Formuliergegevensmodel maken](../../forms/using/create-form-data-models.md)
* [Werken met formuliergegevensmodel](../../forms/using/work-with-form-data-model.md)

Een formuliergegevensmodel is een uitbreiding van het JSON-schema waarmee u:

* [Aangepaste formulieren en fragmenten maken](#create-af)
* [Interactieve communicatie en bouwstenen maken, zoals tekst-, lijst- en voorwaardelijke fragmenten](#create-ic)
* [Interactieve communicatie voorvertonen met voorbeeldgegevens](#preview-ic)
* [Aangepaste formulieren en interactieve communicatie vooraf invullen](#prefill)
* [Verzonden adaptieve formuliergegevens terugschrijven naar gegevensbronnen](#write-af)
* [Invoers van services met behulp van adaptieve formulierregels](#invoke-services)

## Aangepaste formulieren en fragmenten maken {#create-af}

U kunt [adaptieve formulieren](../../forms/using/creating-adaptive-form.md) en [adaptieve formulierfragmenten](../../forms/using/adaptive-form-fragments.md) maken op basis van een formuliergegevensmodel. Ga als volgt te werk om een formuliergegevensmodel te gebruiken bij het maken van een adaptief formulier of adaptief formulierfragment:

1. Selecteer op het tabblad Formuliermodel in het scherm Eigenschappen toevoegen **[!UICONTROL Form Data Model]** de optie in de **[!UICONTROL Select From]** vervolgkeuzelijst.

   ![create-af-1-1](assets/create-af-1-1.png)

1. Tik om uit te breiden **[!UICONTROL Select Form Data Model]**. Alle beschikbare formuliergegevensmodellen worden weergegeven.

   Selecteer een gegevensmodel.

   ![create-af-2-1](assets/create-af-2-1.png)

1. (Alleen **** adaptieve formulierfragmenten) U kunt een adaptief formulierfragment maken op basis van slechts één gegevensmodelobject in een formuliergegevensmodel. Vergroot de **[!UICONTROL Form Data Model Definitions]** vervolgkeuzelijst. Hiermee worden alle gegevensmodelobjecten in het opgegeven formuliergegevensmodel weergegeven. Selecteer een gegevensmodelobject in de lijst.

   ![create-af-3](assets/create-af-3.png)

Zodra het adaptieve formulier of het adaptieve formulierfragment op basis van een formuliergegevensmodel is gemaakt, worden formuliergegevensmodelobjecten weergegeven op het **[!UICONTROL Data Model Objects]** tabblad van de inhoudbrowser in de adaptieve formuliereditor.

>[!NOTE]
>
>Voor een adaptief formulierfragment worden alleen het gegevensmodelobject dat is geselecteerd op het moment van ontwerpen en de bijbehorende gegevensmodelobjecten weergegeven op het tabblad Gegevensmodelobjecten.

![data-model-objects-tab](assets/data-model-objects-tab.png)

U kunt gegevensmodelobjecten naar het aangepaste formulier of fragment slepen om formuliervelden toe te voegen. De toegevoegde formuliervelden behouden de eigenschappen van de metagegevens en de binding met de eigenschappen van gegevensmodelobjecten. De binding zorgt ervoor dat de veldwaarden bij het verzenden van het formulier worden bijgewerkt in de bijbehorende gegevensbronnen en dat deze worden voorgevuld wanneer het formulier wordt gegenereerd.

## Interactieve communicatie maken {#create-ic}

U kunt een interactieve communicatie tot stand brengen die op een model van vormgegevens wordt gebaseerd dat u kunt gebruiken om interactieve mededeling met gegevens van gevormde gegevensbronnen vooraf in te vullen. Bovendien kunnen de bouwstenen van een interactieve communicatie, zoals tekst, lijst, en de fragmenten van het voorwaardendocument op een model van vormgegevens worden gebaseerd.

U kunt een formuliergegevensmodel kiezen wanneer u een interactieve communicatie of een documentfragment maakt. In de volgende afbeelding ziet u het tabblad Algemeen van het dialoogvenster Interactieve communicatie maken.

![create-ic](assets/create-ic.png)

Tabblad Algemeen van dialoogvenster Interactieve communicatie maken

Meer informatie:

[Een interactieve communicatie maken](../../forms/using/create-interactive-communication.md)

[Tekst in interactieve communicatie](/help/forms/using/texts-interactive-communications.md)

[Voorwaarden voor interactieve communicatie](/help/forms/using/conditions-interactive-communications.md)

[Fragmenten weergeven](/help/forms/using/lists.md)

## Voorvertonen met voorbeeldgegevens {#preview-ic}

Met de formuliergegevensmodeleditor kunt u voorbeeldgegevens voor gegevensmodelobjecten genereren en bewerken in het formuliergegevensmodel. U kunt deze gegevens gebruiken om interactieve communicatie en adaptieve formulieren voor te vertonen en te testen. U moet de voorbeeldgegevens genereren voordat u een voorbeeld weergeeft, zoals beschreven in [Werken met formuliergegevensmodel](../../forms/using/work-with-form-data-model.md#sample).

Een voorvertoning weergeven van een interactieve communicatie met voorbeeldgegevens van het formuliergegevensmodel:

1. Navigeer naar de AEM-auteurinstantie. **[!UICONTROL Forms > Forms & Documents]**
1. Selecteer een interactieve communicatie en tik op **[!UICONTROL Preview]** de werkbalk om een voorvertoning van de interactieve communicatie te selecteren **[!UICONTROL Web Channel]****[!UICONTROL Print Channel]** of **[!UICONTROL Both Channels]** weer te geven.
1. Controleer of u [*Kanaal*] voorvertonen hebt geselecteerd en tik op de knop **[!UICONTROL Test Data of Form Data Model]** **[!UICONTROL Preview]**.

De interactieve communicatie wordt geopend met vooraf ingevulde voorbeeldgegevens.

![webvoorvertoning](assets/web-preview.png)

Als u een voorbeeld van een adaptief formulier met voorbeeldgegevens wilt bekijken, opent u het adaptieve adaptieve formulier in de modus Schrijven en tikt u op **[!UICONTROL Preview]**.

## Vooraf invullen met service voor formuliergegevensmodellen {#prefill}

AEM Forms bieden de service Prefill-service voor het out-of-the-box formuliergegevensmodel die u kunt inschakelen voor adaptieve formulieren en interactieve communicatie op basis van het formuliergegevensmodel. De Prefill-service zoekt naar gegevensbronnen voor gegevensmodelobjecten in het adaptieve formulier en de interactieve communicatie en vult daarom gegevens aan tijdens het weergeven van het formulier of de communicatie.

Als u de voorkeursservice Formuliergegevensmodel wilt inschakelen voor een adaptief formulier, opent u de eigenschappen van de container van het adaptieve formulier en selecteert u deze in de **[!UICONTROL Form Data Model Prefill service]** **[!UICONTROL Prefill Service]** vervolgkeuzelijst in de basisaccordeon. Sla vervolgens de eigenschappen op.

![Prefill-service](assets/prefill-service.png)

Als u de service voor het vooraf invullen van het formuliergegevensmodel wilt configureren in een interactieve communicatie, kunt u de service Vooraf invullen van formuliergegevensmodel selecteren in de vervolgkeuzelijst Prefill Service tijdens het maken of later door de eigenschappen te wijzigen.

![bewerken-ic-props](assets/edit-ic-props.png)

Dialoogvenster Eigenschappen bewerken voor interactieve communicatie

## Ingediende adaptieve formuliergegevens naar gegevensbronnen schrijven {#write-af}

Wanneer een gebruiker een formulier verzendt dat is gebaseerd op een formuliergegevensmodel, kunt u het formulier zo configureren dat de verzonden gegevens voor een gegevensmodelobject naar de bijbehorende gegevensbronnen worden geschreven. Met het oog op dit gebruik bieden AEM Forms de verzendactie [van het](../../forms/using/configuring-submit-actions.md)formuliergegevensmodel. Deze actie is alleen beschikbaar buiten het vak voor adaptieve formulieren op basis van een formuliergegevensmodel. Het schrijft voorgelegde gegevens voor een voorwerp van het gegevensmodel in zijn gegevensbron.

Als u de handeling Verzenden van het formuliergegevensmodel wilt configureren, opent u de eigenschappen van de container voor adaptieve formulieren en selecteert u een optie in de vervolgkeuzelijst Handeling verzenden onder de verzendingaccordion. **[!UICONTROL Submit using Form Data Model]** Blader vervolgens naar een gegevensmodelobject en selecteer dit in de **[!UICONTROL Name of the data model object to submit]** vervolgkeuzelijst. Sla de eigenschappen op.

Bij het verzenden van formulieren worden gegevens voor het geconfigureerde gegevensmodelobject naar de desbetreffende gegevensbron geschreven.

![gegevensverzending](assets/data-submission.png)

U kunt ook formulierbijlagen verzenden naar een gegevensbron met binaire objecteigenschappen van gegevensmodellen. Ga als volgt te werk om bijlagen naar een JDBC-gegevensbron te verzenden:

1. Voeg een gegevensmodelobject dat een binaire eigenschap bevat toe aan het formuliergegevensmodel.
1. Sleep de **[!UICONTROL File Attachment]** component in het adaptieve formulier van de browser Components naar het adaptieve formulier.
1. Tik op de toegevoegde component en tik op ![settings_icon](assets/settings_icon.png) om de eigenschappenbrowser voor de component te openen.
1. Tik in het veld Bindverwijzing op ![map search_18](assets/foldersearch_18.png) en selecteer de binaire eigenschap die u in het formuliergegevensmodel hebt toegevoegd. Configureer desgewenst andere eigenschappen.

   Tik op de ![knop](assets/check-button.png) om de eigenschappen op te slaan. Het bijslagveld is nu gebonden aan de binaire eigenschap van het formuliergegevensmodel.

1. Schakel in de sectie Verzending van de eigenschappen van de container van het adaptieve formulier in **[!UICONTROL Submit Form Attachments]**. De bijlage in het binaire-eigenschapveld wordt naar de gegevensbron verzonden bij het verzenden van het formulier.

## Invoers van diensten in adaptieve formulieren met behulp van regels {#invoke-services}

In een adaptief formulier dat is gebaseerd op een formuliergegevensmodel, kunt u regels [](../../forms/using/rule-editor.md) maken om services aan te roepen die zijn geconfigureerd in het formuliergegevensmodel. De **[!UICONTROL Invoke Services]** bewerking in een regel bevat een lijst met alle beschikbare services in het formuliergegevensmodel en u kunt invoer- en uitvoervelden voor de service selecteren. U kunt ook het regeltype **Waarde** instellen gebruiken om een service van een formuliergegevensmodel aan te roepen en de waarde van een veld in te stellen op de uitvoer die door de service wordt geretourneerd.

Bijvoorbeeld, haalt de volgende regel de dienst aan die Werknemeridentiteitskaart als input neemt en de teruggekeerde waarden in overeenkomstige Afhankelijke identiteitskaart, Familienaam, Voornaam, en Gendergebieden in de vorm worden bevolkt.

![oproepdienst](assets/invoke-service.png)

Bovendien kunt u de `guidelib.dataIntegrationUtils.executeOperation` API gebruiken om een JavaScript in de coderedacteur voor de regelredacteur te schrijven. Zie de [API voor het oproepen van de service](/help/forms/using/invoke-form-data-model-services.md)van het formuliergegevensmodel voor API-details.
