---
title: Hoe maakt u een adaptief formulier?
description: Leer hoe u een adaptief formulier maakt met [!DNL Experience Manager Forms]. Adaptieve Forms zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen. Dig dieper in op het maken van een adaptief formulier op basis van een formuliergegevensmodel en een XML- of JSON-schema.
Keywords: create adaptive form core component, create core component based adaptive form, creare adaptive form
products: SG_EXPERIENCEMANAGER/6.5/FORMS
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
feature: Adaptive Forms, Core Components
solution: Experience Manager, Experience Manager Forms
source-git-commit: d2be8d93c64ca18352a0e811605c526a8dae488f
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 0%

---

# Op Adaptieve Forms gebaseerde Core Components maken {#creating-an-adaptive-form-core-components}


<span class="preview"> Adobe raadt u aan Core Components te gebruiken voor [Adaptieve Forms toevoegen aan een AEM Sites-pagina](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md) of aan [standalone adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md). </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html) |
| AEM 6,5 | Dit artikel |

<!--**Applies to:** ✅ Adaptive Form Core Components ❎ [Adaptive Form Foundation Components](/help/forms/using/create-adaptive-form.md).-->

Met Adaptive Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een gebruiksvriendelijke gebruikersvriendelijke gebruikersinterface om snel een Adaptive Forms te maken. De gebruikersinterface biedt snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en): Dit zijn gestandaardiseerde componenten voor het vastleggen van gegevens. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijving. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. Adobe beveelt aan deze moderne en uitbreidbare componenten te gebruiken om Adaptive Forms te ontwikkelen.

* [Aangepaste Forms Foundation-componenten](creating-adaptive-form.md): Dit zijn klassieke (oude) componenten voor gegevensvastlegging. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Als u formulieren maakt, wordt het door de Adobe aanbevolen  [Adaptieve Forms Core-componenten](/help/forms/using/create-adaptive-form.md) om een Adaptieve Forms te maken.

## Voorwaarden

U hebt het volgende nodig om een adaptief formulier te maken:

* **Adaptieve Forms Core-componenten inschakelen voor uw omgeving**: AEM Projectversie 41 of hoger van Archetype is vereist voor [Core Components voor uw omgeving inschakelen](/help/forms/using/enable-adaptive-forms-core-components.md). Als u de Core Components voor uw omgeving inschakelt, **Adaptieve Forms (Core Component)** sjabloon en Canvasthema worden toegevoegd aan uw omgeving.

* **Een adaptieve formuliersjabloon**: Een sjabloon biedt een basisstructuur en definieert de vormgeving (lay-outs en stijlen) van een adaptief formulier. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. U kunt ook [voorbeeldsjablonen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) naar uw omgeving. Hiermee kunt u snel formulieren maken.

  >[!NOTE]
  >
  > Als u dat niet doet, **Adaptieve Forms (Core Component)** sjabloon op uw omgeving, [Adaptieve Forms Core-componenten inschakelen voor uw omgeving](/help/forms/using/enable-adaptive-forms-core-components.md). Als u de Core Components voor uw omgeving inschakelt, **Adaptieve Forms (Core Component)** sjabloon wordt toegevoegd aan uw omgeving.

* **Een adaptief formulierthema**: Een thema bevat opmaakgegevens voor de componenten en deelvensters. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten.  De `Canvas` thema wordt standaard toegevoegd wanneer u kerncomponenten voor uw omgeving inschakelt. U kunt  [de standaardthema&#39;s downloaden en aanpassen](create-or-customize-themes-for-adaptive-forms-core-components.md). Voor **uit de doos** thema&#39;s die u kunt implementeren [voorbeeldthema&#39;s](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) naar uw omgeving. Deze hulp u begint uw vormen te stileren en een basisstructuur te verstrekken om een thema tot stand te brengen of aan te passen volgens uw bedrijfsvereisten.

* **Machtigingen**: Voeg uw gebruikers toe aan [!DNL forms-users] groep. De leden van de [!DNL forms-users] groep heeft machtigingen om een adaptief formulier te maken. Zie voor een gedetailleerde lijst met formulierspecifieke gebruikersgroepen [Groepen en machtigingen](forms-groups-privileges-tasks.md).

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

## Een adaptief formulier maken {#create-an-adaptive-form}

1. Aanmelden bij uw lokale [AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=en#author-and-publish-installs).

1. Ga uw geloofsbrieven op de Experience Manager login pagina in. Nadat u bent aangemeld, selecteert u in de linkerbovenhoek de optie **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. Selecteren **[!UICONTROL Create]**  > **[!UICONTROL Create Adaptive Forms]**.

1. Selecteer een adaptieve Forms Core Components-sjabloon en klik op **[!UICONTROL Next]**.

1. De **[!UICONTROL Add Properties]** wordt weergegeven. Geef de waarden op voor de volgende eigenschapvelden. De velden Titel en Naam zijn verplicht:

   * **[!UICONTROL Title:]** Hier geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in het dialoogvenster [!DNL Experience Manager Forms] gebruikersinterface.
   * **[!UICONTROL Name:]** Hier geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten.
   * **[!UICONTROL Description:]** Hier geeft u gedetailleerde informatie over het formulier op.
   * **[!UICONTROL Theme Client Library]:** Hiermee geeft u het thema voor een adaptief formulier op. Standaard worden de `adaptiveform.theme.canvas3` thema is geselecteerd. U kunt ook een ander thema kiezen in het menu **[!UICONTROL Theme Client Library]** vervolgkeuzelijst.
   * **[!UICONTROL Configuration Container:]**  Definieert een locatie waar configuratiebestanden voor Adaptive Forms worden opgeslagen. Deze configuratiebestanden bevatten instellingen en eigenschappen die verwant zijn aan het gedrag en de weergave van Adaptive Forms.
   * **[!UICONTROL Tags:]** Hiermee geeft u codes op om het adaptieve formulier op unieke wijze te identificeren. Tags helpen u bij het zoeken naar het formulier. Als u tags wilt maken, typt u nieuwe tagnamen in het dialoogvenster **[!UICONTROL Tags]** doos.
1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking.


1. Selecteren **[!UICONTROL Edit]** om het nieuwe formulier te openen op een nieuw tabblad. Het formulier wordt geopend voor bewerking en geeft de inhoud weer die beschikbaar is in de sjabloon. De zijbalk wordt ook weergegeven om het nieuwe formulier aan te passen.


## Gebruik Adaptieve Forms Core-componenten om uw formulier te maken

Nadat u het formulier hebt geopend voor bewerking, kunt u met de beschikbare Adaptive Forms Core Components formuliervelden toevoegen aan uw formulier. U kunt slepen en neerzetten of + gebruiken [component insert] om deze componenten aan een formulier toe te voegen. Zie AEM de documentatie van de Componenten van de Kern voor meer informatie over beschikbaar [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#components). U kunt ook [https://aemcomponents.dev/](https://aemcomponents.dev/) om beschikbare kerncomponenten in actie te bekijken.

## Handeling verzenden voor een adaptief formulier configureren {#configure-submit-action-for-form}

Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd in een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. Aangepaste formulieren bevatten enkele van de verzendacties. U kunt ook een standaardverzendactie uitbreiden om uw eigen aangepaste verzendactie te maken. Een handeling verzenden voor uw formulier configureren:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.

1. Klik op de knop  **[!UICONTROL Submission]** tab.

   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een verzendactie te configureren](/help/forms/using/assets/adaptive-forms-submit-message.png)

1. Selecteer en vorm een **[!UICONTROL Submit action]**, op basis van uw vereisten. Zie voor meer informatie over Handelingen verzenden [Handeling Adaptief verzenden van formulier](/help/forms/using/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Leid de gebruiker om naar een pagina of toon een dank u bericht bij de vormverzending

Bij het verzenden van een formulier kunt u de gebruiker omleiden naar een andere webpagina of een bericht. Om de gebruiker om te leiden of het dank u bericht te vormen:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de **[!UICONTROL Submission]** tab.

   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een omleidingspagina of een bedankbericht te configureren](/help/forms/using/assets/adaptive-forms-submit-message.png)

   * Als u een omleidings-URL wilt configureren, selecteert u bij Verzenden de optie **[!UICONTROL Redirect to URL]** en een AEM Sites-pagina selecteren of een URL van een externe pagina opgeven.

   * Als u een aangepast bericht of een bedankbericht wilt configureren, selecteert u bij Verzenden de optie **[!UICONTROL Show Message]** en geef een bericht op in het dialoogvenster **[!UICONTROL Message content]** doos. Het is een tekstvak met tekstopmaak. U kunt de optie Volledig scherm gebruiken om alle beschikbare tekstitems weer te geven.

## Een schema of formuliergegevensmodel configureren voor een adaptief formulier {#configure-schema-or-data-model-for-form}

Met het formuliergegevensmodel kunt u een formulier verbinden met een gegevensbron om gegevens te verzenden en te ontvangen op basis van gebruikersacties. U kunt een formulier ook verbinden met een JSON-schema om de verzonden gegevens in een vooraf gedefinieerde indeling te ontvangen. Afhankelijk van de vereiste verbinding, sluit uw formulier aan op een JSON-schema of formuliergegevensmodel:

* [Een JSON-schema maken en uploaden naar uw omgeving](/help/forms/using/adaptive-form-json-schema-form-model.md)
* [Een formuliergegevensmodel maken](/help/forms/using/create-form-data-models.md)

### Een JSON-schema of formuliergegevensmodel voor uw formulier configureren

Een JSON-schema of formuliergegevensmodel configureren voor uw formulier:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de **[!UICONTROL Data Model]** tab.

   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een JSON-schema of formuliergegevensmodel te configureren](/help/forms/using/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Selecteer en configureer een JSON-schema of formuliergegevensmodel op basis van uw vereisten:

   * Wanneer u **[!UICONTROL Form Model]** gebruiken **[!UICONTROL Select Form Data Model]** om een vooraf geconfigureerd formuliergegevensmodel te selecteren.
   * Wanneer u **[!UICONTROL Schema]** gebruiken **[!UICONTROL Schema]** Selecteer een JSON-schema voor uw formulier.

1. Klik op **[!UICONTROL Done]**.

>[!NOTE]
>
> U kunt het JSON-schema of het formuliergegevensmodel voor een adaptief formulier bewerken met de eigenschappen van de Guide Container.

## Een prefill-service configureren  {#configure-prefill-service-for-form}

U kunt de Prefill-service gebruiken om automatisch velden van een adaptief formulier in te vullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. U kunt:

* [Een aangepaste prefill-service maken](/help/forms/using/prepopulate-adaptive-form-fields.md)
* [Vooraf ingevulde service Formuliergegevensmodel gebruiken](#fdm-prefill-service)

### De service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen {#fdm-prefill-service}

U kunt de service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen met een formuliergegevensmodel of een aangepaste voorinvulservice. De service Vooraf invullen formuliergegevensmodel gebruikt de [De service van het geconfigureerde formuliergegevensmodel ophalen](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) om gegevens op te halen. Als u de service Vooraf invullen van formuliergegevensmodel wilt gebruiken voor een adaptief formulier:

1. Open de Inhoudsbrowser en selecteer de **[!UICONTROL Guide Container]** van uw adaptieve formulier.
1. Klik op de eigenschappen van de container van de hulplijn ![Eigenschappen van hulplijnen](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik op de eigenschappen van de container van het adaptieve formulier ![Eigenschappen van adaptieve formuliercontainers](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![Klik op het pictogram Sleutel om het dialoogvenster Aangepaste formuliercontainer te openen om een omleidingspagina of een bedankbericht te configureren](/help/forms/using/assets/adaptive-forms-container-prefill-service.png)
1. Selecteer een formuliergegevensmodel. Open de **[!UICONTROL Basic]** tab. Selecteer in de service Prefill de optie **[!UICONTROL Form Data Model Prefill Service]**.
1. Klik op **[!UICONTROL Done]**. Uw adaptieve formulier is nu geconfigureerd voor vooraf invullen van formuliergegevensmodel. U kunt nu de [regeleditor](rule-editor.md) om regels te maken voor het vooraf invullen van velden van het formulier.

## Hoe wijzigt u de naam van een AEM adaptief formulier?{#rename-an-AEM-Adaptive-Form}

Voer de volgende stappen uit om de naam van een adaptief formulier te wijzigen:

1. Selecteer een adaptief formulier in uw AEM Forms-gebruikersinterface.
1. Klik op de knop **Eigenschappen** op de bovenste spoorstaaf.

   ![Eigenschappen](/help/forms/using/assets/rename-form-properties.png)

1. Wijzig de naam van het formulier in het dialoogvenster **Titel** zoals weergegeven in de onderstaande afbeelding.
1. Klikken **Opslaan en sluiten**.

   ![De naam van een AEM adaptief formulier wijzigen](/help/forms/using/assets/rename-form-title.png)


<!--
## Edit Form Model properties of an Adaptive Form {#edit-form-model}

1. Select the Adaptive Form and select ![Page information](/help/forms/using/assets/configure-icon.svg) > **[!UICONTROL Open Properties]**. The Form Properties page opens. 

1. Go to the **[!UICONTROL Form Model]** tab and choose a form model. If the Adaptive Form is without a form model, you have the freedom to choose either a JSON schema or a form data model. On the other hand, if the Adaptive Form is already based on a form model, you have the option to switch to another form model of the same type. For instance, if the form is using a JSON schema, you can easily switch to another JSON schema, and similarly if the form is using a Form Data Model, you can switch to another Form Data Model. 

1. Select **[!UICONTROL Save]** to save the properties.
-->

## Volgende functies

* [Regeleditor gebruiken om dynamisch gedrag aan formulier toe te voegen](rule-editor.md)
* [Thema&#39;s maken of aanpassen voor adaptieve Forms op basis van Core Components](create-or-customize-themes-for-adaptive-forms-core-components.md)


## Zie ook

* [Een adaptief formulier op basis van kerncomponenten maken](create-an-adaptive-form-core-components.md)
* [Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina of -ervaringsfragment](create-or-add-an-adaptive-form-to-aem-sites-page.md)
* [Voorbeeldthemasjablonen en formuliergegevensmodellen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)
