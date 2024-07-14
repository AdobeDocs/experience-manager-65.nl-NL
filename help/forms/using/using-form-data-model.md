---
title: Formuliergegevensmodel gebruiken
description: Leer hoe u het formuliergegevensmodel kunt gebruiken om adaptieve formulieren en interactieve communicatie te maken en te gebruiken.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integration
docset: aem65
feature: Form Data Model
exl-id: 9a73a643-7ad4-49aa-a971-08d52679158d
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1207'
ht-degree: 0%

---

# Formuliergegevensmodel gebruiken{#use-form-data-model}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/using-form-data-model.html) |
| AEM 6,5 | Dit artikel |


![ held-beeld ](do-not-localize/data-integration.png)

Met AEM Forms-gegevensintegratie kunt u verschillende backendgegevensbronnen gebruiken om een formuliergegevensmodel te maken dat u als schema kunt gebruiken in verschillende adaptieve formulieren en interactieve communicatieworkflows. Hiervoor moeten gegevensbronnen worden geconfigureerd en een formuliergegevensmodel worden gemaakt op basis van gegevensmodelobjecten en -services die beschikbaar zijn in gegevensbronnen. Raadpleeg de volgende secties voor meer informatie:

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

U kunt [ adaptieve vormen ](../../forms/using/creating-adaptive-form.md) en [ adaptieve vormfragmenten ](../../forms/using/adaptive-form-fragments.md) tot stand brengen die op een model van vormgegevens worden gebaseerd. Ga als volgt te werk om een formuliergegevensmodel te gebruiken bij het maken van een adaptief formulier of adaptief formulierfragment:

1. Selecteer op het tabblad Formuliermodel in het scherm Eigenschappen toevoegen de optie **[!UICONTROL Form Data Model]** in de vervolgkeuzelijst **[!UICONTROL Select From]** .

   ![ creeer-af-1-1 ](assets/create-af-1-1.png)

1. Selecteer deze optie om **[!UICONTROL Select Form Data Model]** uit te vouwen. Alle beschikbare formuliergegevensmodellen worden weergegeven.

   Selecteer een gegevensmodel.

   ![ creeer-af-2-1 ](assets/create-af-2-1.png)

1. (**de Aanpassings slechts fragmenten van de vorm**) U kunt een adaptief vormfragment tot stand brengen dat op slechts één voorwerp van het gegevensmodel in een model van vormgegevens wordt gebaseerd. Vouw de vervolgkeuzelijst **[!UICONTROL Form Data Model Definitions]** uit. Hiermee worden alle gegevensmodelobjecten in het opgegeven formuliergegevensmodel weergegeven. Selecteer een gegevensmodelobject in de lijst.

   ![ create-af-3 ](assets/create-af-3.png)

Zodra het adaptieve formulier of het adaptieve formulierfragment op basis van een formuliergegevensmodel is gemaakt, worden formuliergegevensmodelobjecten weergegeven op het tabblad **[!UICONTROL Data Model Objects]** van de inhoudbrowser in de adaptieve formuliereditor.

>[!NOTE]
>
>Voor een adaptief formulierfragment worden alleen het gegevensmodelobject dat is geselecteerd op het moment van ontwerpen en de bijbehorende gegevensmodelobjecten weergegeven op het tabblad Gegevensmodelobjecten.

![ gegeven-model-voorwerpen-lusje ](assets/data-model-objects-tab.png)

U kunt gegevensmodelobjecten naar het aangepaste formulier of fragment slepen om formuliervelden toe te voegen. De toegevoegde formuliervelden behouden de eigenschappen van de metagegevens en de binding met de eigenschappen van gegevensmodelobjecten. De binding zorgt ervoor dat de veldwaarden bij het verzenden van het formulier worden bijgewerkt in de bijbehorende gegevensbronnen en dat deze worden voorgevuld wanneer het formulier wordt gegenereerd.

## Interactieve communicatie maken {#create-ic}

U kunt een interactieve communicatie tot stand brengen die op een model van vormgegevens wordt gebaseerd dat u kunt gebruiken om interactieve mededeling met gegevens van gevormde gegevensbronnen vooraf in te vullen. Bovendien kunnen de bouwstenen van een interactieve communicatie, zoals tekst, lijst, en de fragmenten van het voorwaardendocument op een model van vormgegevens worden gebaseerd.

U kunt een formuliergegevensmodel kiezen wanneer u een interactieve communicatie of een documentfragment maakt. In de volgende afbeelding ziet u het tabblad Algemeen van het dialoogvenster Interactieve communicatie maken.

![ creeer-ic ](assets/create-ic.png)

Tabblad Algemeen van dialoogvenster Interactieve communicatie maken

Zie voor meer informatie:

[Een interactieve communicatie maken](../../forms/using/create-interactive-communication.md)

[Tekst in interactieve communicatie](/help/forms/using/texts-interactive-communications.md)

[Voorwaarden voor interactieve communicatie](/help/forms/using/conditions-interactive-communications.md)

[Fragmenten weergeven](/help/forms/using/lists.md)

## Voorvertonen met voorbeeldgegevens {#preview-ic}

Met de formuliergegevensmodeleditor kunt u voorbeeldgegevens voor gegevensmodelobjecten in het formuliergegevensmodel genereren en bewerken. U kunt deze gegevens gebruiken om interactieve communicatie en adaptieve formulieren voor te vertonen en te testen. Produceer de steekproefgegevens alvorens te previewing zoals die in [ wordt beschreven Werk met model van vormgegevens ](../../forms/using/work-with-form-data-model.md#sample).

Een voorvertoning weergeven van een interactieve communicatie met voorbeeldgegevens van het formuliergegevensmodel:

1. Navigeer naar **[!UICONTROL Forms > Forms & Documents]** bij AEM auteurinstantie.
1. Selecteer een interactieve communicatie en selecteer **[!UICONTROL Preview]** in de werkbalk om **[!UICONTROL Web Channel]** , **[!UICONTROL Print Channel]** of **[!UICONTROL Both Channels]** te selecteren voor een voorvertoning van de interactieve communicatie.
1. In de 2} dialoog van de Voorproef [*kanaal*], zorg ervoor dat **[!UICONTROL Test Data of Form Data Model]** wordt geselecteerd en **[!UICONTROL Preview]** selecteert.

De interactieve communicatie wordt geopend met vooraf ingevulde voorbeeldgegevens.

![ web-preview ](assets/web-preview.png)

Als u een voorbeeld van een adaptief formulier met voorbeeldgegevens wilt bekijken, opent u het adaptieve adaptieve formulier in de modus Ontwerpen en selecteert u **[!UICONTROL Preview]** .

## Vooraf invullen met service voor formuliergegevensmodellen {#prefill}

AEM Forms biedt een vooraf ingevulde service voor het out-of-the-box formuliergegevensmodel die u kunt inschakelen voor adaptieve formulieren en interactieve communicatie op basis van het formuliergegevensmodel. De Prefill-service zoekt naar gegevensbronnen voor gegevensmodelobjecten in het adaptieve formulier en de interactieve communicatie en vult daarom gegevens aan tijdens het weergeven van het formulier of de communicatie.

Als u de service Vooraf invullen formuliergegevensmodel wilt inschakelen voor een adaptief formulier, opent u de eigenschappen van de container van het adaptieve formulier en selecteert u **[!UICONTROL Form Data Model Prefill service]** in de vervolgkeuzelijst **[!UICONTROL Prefill Service]** in de basisaccordeon. Sla vervolgens de eigenschappen op.

![ prefill-service ](assets/prefill-service.png)

Als u de service voor het vooraf invullen van het formuliergegevensmodel wilt configureren in een interactieve communicatie, kunt u de service Vooraf invullen van formuliergegevensmodel selecteren in de vervolgkeuzelijst Prefill Service tijdens het maken of later door de eigenschappen te wijzigen.

![ geef-ic-props uit ](assets/edit-ic-props.png)

Dialoogvenster Eigenschappen bewerken voor interactieve communicatie

## Ingediende adaptieve formuliergegevens naar gegevensbronnen schrijven {#write-af}

Wanneer een gebruiker een formulier verzendt dat is gebaseerd op een formuliergegevensmodel, kunt u het formulier zo configureren dat de verzonden gegevens voor een gegevensmodelobject naar de bijbehorende gegevensbronnen worden geschreven. Om dit gebruiksgeval te bereiken, verstrekt AEM Forms [ Model van de Gegevens van de Vorm voorlegt actie ](../../forms/using/configuring-submit-actions.md), beschikbaar uit-van-de-doos slechts voor adaptieve vormen die op een model van vormgegevens worden gebaseerd. Het schrijft voorgelegde gegevens voor een voorwerp van het gegevensmodel in zijn gegevensbron.

Als u de verzendactie Formuliergegevensmodel wilt configureren, opent u de eigenschappen van de container voor adaptieve formulieren en selecteert u **[!UICONTROL Submit using Form Data Model]** in de vervolgkeuzelijst Handeling verzenden onder de verzendingaccordion. Blader vervolgens naar een gegevensmodelobject en selecteer dit in de vervolgkeuzelijst **[!UICONTROL Name of the data model object to submit]** . Sla de eigenschappen op.

Bij het verzenden van formulieren worden gegevens voor het geconfigureerde gegevensmodelobject naar de desbetreffende gegevensbron geschreven.

![ gegeven-voorlegging ](assets/data-submission.png)

U kunt ook formulierbijlagen verzenden naar een gegevensbron met binaire objecteigenschappen van gegevensmodellen. Ga als volgt te werk om bijlagen naar een JDBC-gegevensbron te verzenden:

1. Voeg een gegevensmodelobject dat een binaire eigenschap bevat toe aan het formuliergegevensmodel.
1. Sleep in het adaptieve formulier de component **[!UICONTROL File Attachment]** van de browser Components naar het adaptieve formulier.
1. Selecteer om de toegevoegde component te selecteren en ![ settings_icon ](assets/settings_icon.png) te selecteren om browser van Eigenschappen voor de component te openen.
1. Op het Bind gebied van de Verwijzing, uitgezochte ![ folder_search_18 ](assets/foldersearch_18.png) en navigeer om het binaire bezit te selecteren u in het model van vormgegevens toevoegde. Configureer desgewenst andere eigenschappen.

   Selecteer ![ controle-knoop ](assets/check-button.png) om de eigenschappen te bewaren. Het bijslagveld is nu gebonden aan de binaire eigenschap van het formuliergegevensmodel.

1. Schakel **[!UICONTROL Submit Form Attachments]** in het gedeelte Verzending van de eigenschappen van de container van adaptieve formulieren in. De bijlage in het binaire-eigenschapveld wordt naar de gegevensbron verzonden bij het verzenden van het formulier.

## Invoers van diensten in adaptieve formulieren met behulp van regels {#invoke-services}

In een adaptieve vorm die op een model van vormgegevens wordt gebaseerd, kunt u [ regels ](../../forms/using/rule-editor.md) creëren om de diensten aan te halen die in het model van vormgegevens worden gevormd. De bewerking **[!UICONTROL Invoke Services]** in een regel bevat een lijst met alle beschikbare services in het formuliergegevensmodel en u kunt invoer- en uitvoervelden voor de service selecteren. U kunt het **Reeks Type van de Waarde** regel ook gebruiken om de modeldienst van vormgegevens aan te halen en de waarde van een gebied aan de output te plaatsen die door de dienst is teruggekeerd.

Bijvoorbeeld, haalt de volgende regel de dienst aan die Werknemeridentiteitskaart als input neemt en de teruggekeerde waarden in overeenkomstige Afhankelijke identiteitskaart, Familienaam, Voornaam, en Gendergebieden in de vorm worden bevolkt.

![ aanhalen-dienst ](assets/invoke-service.png)

Bovendien kunt u de `guidelib.dataIntegrationUtils.executeOperation` API gebruiken om een JavaScript in de coderedacteur voor de regelredacteur te schrijven. Voor API details, zie [ API om de modeldienst van vormgegevens ](/help/forms/using/invoke-form-data-model-services.md) aan te halen.
