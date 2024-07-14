---
title: Hoe maakt u een adaptief formulier?
description: Leer hoe te om een Aangepast Vorm tot stand te brengen gebruikend  [!DNL Experience Manager Forms]. Adaptieve Forms zijn responsieve HTML5-formulieren die het verzamelen en verwerken van informatie stroomlijnen. Dig dieper in op het maken van een adaptief formulier op basis van een formuliergegevensmodel en een XML- of JSON-schema.
Keywords: create adaptive form core component, create core component based adaptive form, creare adaptive form
products: SG_EXPERIENCEMANAGER/6.5/FORMS
contentOwner: Khushwant Singh
topic-tags: Adaptive Forms
docset: aem65
role: Admin, Developer
feature: Adaptive Forms,Core Components
solution: Experience Manager, Experience Manager Forms
exl-id: ee596672-b0b5-42e9-a139-72f90287bf3b
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1729'
ht-degree: 0%

---

# Op Adaptieve Forms gebaseerde Core Components maken {#creating-an-adaptive-form-core-components}


<span class="preview"> Adobe adviseert het gebruiken van de Componenten van de Kern [ Aangepaste Forms aan een Pagina van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md) toe te voegen of [ standalone Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) tot stand te brengen. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form-core-components.html) |
| AEM 6,5 | Dit artikel |

<!--**Applies to:** ✅ Adaptive Form Core Components ❎ [Adaptive Form Foundation Components](/help/forms/using/create-adaptive-form.md).-->

Met Adaptive Forms kunt u aantrekkelijke, responsieve, dynamische en adaptieve formulieren maken. AEM Forms biedt een gebruiksvriendelijke gebruikersvriendelijke gebruikersinterface om snel een Adaptive Forms te maken. De gebruikersinterface biedt snelle tabnavigatie waarmee u eenvoudig vooraf geconfigureerde sjablonen, stijlen, velden en verzendopties kunt selecteren om een adaptief formulier te maken.

Voordat u begint, moet u meer weten over het type Forms-componenten waarover u beschikt:

* [ Aangepaste Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en): Dit zijn gestandaardiseerde gegevens vangen componenten. Deze componenten bieden aanpassingsmogelijkheden, kortere ontwikkelingstijd en lagere onderhoudskosten voor uw digitale inschrijving. Een ontwikkelaar kan deze componenten eenvoudig aanpassen en opmaken. Adobe beveelt aan deze moderne en uitbreidbare componenten te gebruiken om Adaptive Forms te ontwikkelen.

* [ Aangepaste Componenten van de Stichting van Forms ](creating-adaptive-form.md): Dit zijn klassieke (oude) gegevens vangen componenten. U kunt deze blijven gebruiken om uw bestaande basiscomponenten te bewerken op basis van adaptief formulier. Als u vormen creeert, adviseert de Adobe gebruikend [ Aangepaste Componenten van de Kern van Forms ](/help/forms/using/create-adaptive-form.md) om een Aangepaste Forms tot stand te brengen.

## Voorwaarden

U hebt het volgende nodig om een adaptief formulier te maken:

* **laat de Aangepaste Componenten van de Kern van Forms voor uw milieu** toe: AEM Versie van het Archetype project 41 of recenter wordt vereist om [ de Componenten van de Kern voor uw milieu ](/help/forms/using/enable-adaptive-forms-core-components.md) toe te laten. Bij het toelaten van de Componenten van de Kern voor uw milieu, worden het **Aangepaste Forms (de Component van de Kern)** malplaatje en het thema van het Canvas toegevoegd aan uw milieu.

* **een Adaptief malplaatje van de Vorm**: Een malplaatje verstrekt een basisstructuur en bepaalt verschijning (lay-outs en stijlen) van een Aangepast Vorm. Het heeft vooraf opgemaakte componenten die bepaalde eigenschappen en inhoudsstructuur bevatten. Het biedt ook de opties om een thema en een verzendactie te definiëren. In het thema wordt de actie look and feel and submit gedefinieerd voor de actie die moet worden ondernomen bij het verzenden van een adaptief formulier. U kunt [ steekproefmalplaatjes ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) aan uw milieu ook opstellen. Hiermee kunt u snel formulieren maken.

  >[!NOTE]
  >
  > Als u niet hebt, **Aangepaste Forms (de Component van de Kern)** malplaatje op uw milieu, [ laat de Aangepaste Componenten van de Kern van Forms voor uw milieu ](/help/forms/using/enable-adaptive-forms-core-components.md) toe. Bij het toelaten van de Componenten van de Kern voor uw milieu, wordt het **Aangepaste Forms (de Component van de Kern)** malplaatje toegevoegd aan uw milieu.

* **een Adaptief thema van de Vorm**: Een thema bevat het stileren details voor de componenten en de panelen. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u een thema toepast, weerspiegelt de opgegeven stijl de corresponderende componenten.  Het thema `Canvas` wordt standaard toegevoegd wanneer u kerncomponenten inschakelt voor uw omgeving. U kunt [ de standaardthema&#39;s ](create-or-customize-themes-for-adaptive-forms-core-components.md) downloaden en aanpassen. Voor **uit de doos** thema&#39;s kunt u [ steekproefthema&#39;s ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) aan uw milieu opstellen. Deze hulp u begint uw vormen te stileren en een basisstructuur te verstrekken om een thema tot stand te brengen of aan te passen volgens uw bedrijfsvereisten.

* **Toestemmingen**: Voeg uw gebruikers aan [!DNL forms-users] groep toe. De leden van de groep [!DNL forms-users] hebben machtigingen om een adaptief formulier te maken. Voor gedetailleerde lijst van vorm-specifieke gebruikersgroepen, zie [ Groepen en toestemmingen ](forms-groups-privileges-tasks.md).

<!--
>[!NOTE]
>
>
> In addition to the given themes and templates when you enable Core Components, you can also deploy the latest out-of-the box [sample themes and templates](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html) to your AEM environment for use in Core Components based Adaptive Forms.
-->

## Een adaptief formulier maken {#create-an-adaptive-form}

1. Login aan uw lokale [ AEM auteursinstantie ](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html?lang=en#author-and-publish-installs).

1. Ga uw geloofsbrieven op de Experience Manager login pagina in. Nadat u zich hebt aangemeld, selecteert u in de linkerbovenhoek **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL Create Adaptive Forms]** .

1. Selecteer een sjabloon voor Adaptieve Forms Core-componenten en klik op **[!UICONTROL Next]** .

1. De lus **[!UICONTROL Add Properties]** wordt weergegeven. Geef de waarden op voor de volgende eigenschapvelden. De velden Titel en Naam zijn verplicht:

   * **[!UICONTROL Title:]** Hiermee geeft u de weergavenaam van het formulier op. Met de titel kunt u het formulier identificeren in de gebruikersinterface van [!DNL Experience Manager Forms] .
   * **[!UICONTROL Name:]** Hiermee geeft u de naam van het formulier op. Er wordt een knooppunt met de opgegeven naam gemaakt in de repository. Wanneer u een titel begint te typen, wordt automatisch een waarde voor het naamveld gegenereerd. U kunt de voorgestelde waarde wijzigen. Het naamveld mag alleen alfanumerieke tekens, afbreekstreepjes en onderstrepingstekens bevatten.
   * **[!UICONTROL Description:]** Hiermee geeft u gedetailleerde informatie over het formulier op.
   * **[!UICONTROL Theme Client Library]:** Specificeert het thema voor een Aangepast Vorm. Standaard is het thema `adaptiveform.theme.canvas3` geselecteerd. U kunt ook een ander thema kiezen in het keuzemenu **[!UICONTROL Theme Client Library]** .
   * **[!UICONTROL Configuration Container:]** Definieert een locatie waar configuratiebestanden voor Adaptive Forms worden opgeslagen. Deze configuratiebestanden bevatten instellingen en eigenschappen die verwant zijn aan het gedrag en de weergave van Adaptive Forms.
   * **[!UICONTROL Tags:]** Hiermee geeft u codes op om het adaptieve formulier op unieke wijze te identificeren. Tags helpen u bij het zoeken naar het formulier. Als u tags wilt maken, typt u nieuwe tagnamen in het vak **[!UICONTROL Tags]** .
1. Selecteer **[!UICONTROL Create]**. Er wordt een adaptief formulier gemaakt en er wordt een dialoogvenster weergegeven om het formulier te openen voor bewerking.


1. Selecteer **[!UICONTROL Edit]** om het nieuwe formulier op een nieuw tabblad te openen. Het formulier wordt geopend voor bewerking en geeft de inhoud weer die beschikbaar is in de sjabloon. De zijbalk wordt ook weergegeven om het nieuwe formulier aan te passen.


## Gebruik Adaptieve Forms Core-componenten om uw formulier te maken

Nadat u het formulier hebt geopend voor bewerking, kunt u met de beschikbare Adaptive Forms Core Components formuliervelden toevoegen aan uw formulier. U kunt slepen-en-daling of gebruiken + [ tussenvoegselcomponent ] optie om deze componenten aan een vorm toe te voegen. Zie, AEM de documentatie van de Componenten van de Kern om over beschikbare [ Aangepaste Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en#components) te leren. U kunt [ https://aemcomponents.dev/ ](https://aemcomponents.dev/) ook bezoeken om beschikbare kerncomponenten in actie te bekijken.

## Handeling verzenden voor een adaptief formulier configureren {#configure-submit-action-for-form}

Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd in een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. Aangepaste formulieren bevatten enkele van de verzendacties. U kunt ook een standaardverzendactie uitbreiden om uw eigen aangepaste verzendactie te maken. Een handeling verzenden voor uw formulier configureren:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.

1. Klik op de tab **[!UICONTROL Submission]** .

   ![ klik het pictogram van de Sleutel om de Adaptieve de dialoogdoos van de Container van de Vorm te openen om een verzendactie te vormen ](/help/forms/using/assets/adaptive-forms-submit-message.png)

1. Selecteer en configureer een **[!UICONTROL Submit action]** op basis van uw vereisten. Voor gedetailleerde informatie over Submit Acties, zie [ Aangepaste Vorm verzenden Actie ](/help/forms/using/configuring-submit-actions.md)

<!--
    
    ![Click the Wrench icon to open Adaptive Form Container dialog box to configure Data Models for the Adaptive Form Container component](/help/forms/assets/adaptive-forms-container.png)

-->

## Leid de gebruiker om naar een pagina of toon een dank u bericht bij de vormverzending

Bij het verzenden van een formulier kunt u de gebruiker omleiden naar een andere webpagina of een bericht. Om de gebruiker om te leiden of het dank u bericht te vormen:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de tab **[!UICONTROL Submission]** .

   ![ klik het pictogram van de Sleutel om de Aangepaste de dialoogdoos van de Container van de Vorm te openen om een omleidingspagina te vormen of u te danken bericht ](/help/forms/using/assets/adaptive-forms-submit-message.png)

   * Als u een omleidings-URL wilt configureren, bijvoorbeeld bij Verzenden, selecteert u de optie **[!UICONTROL Redirect to URL]** en bladert en selecteert u een AEM Sites-pagina of geeft u de URL van een externe pagina op.

   * Als u een aangepast bericht of een bedankbericht wilt configureren, bijvoorbeeld bij Verzenden, selecteert u de optie **[!UICONTROL Show Message]** en geeft u een bericht op in het vak **[!UICONTROL Message content]** . Het is een tekstvak met tekstopmaak. U kunt de optie Volledig scherm gebruiken om alle beschikbare tekstitems weer te geven.

## Een schema of formuliergegevensmodel configureren voor een adaptief formulier {#configure-schema-or-data-model-for-form}

Met het formuliergegevensmodel kunt u een formulier verbinden met een gegevens-Source en gegevens verzenden en ontvangen op basis van gebruikersacties. U kunt een formulier ook verbinden met een JSON-schema om de verzonden gegevens in een vooraf gedefinieerde indeling te ontvangen. Afhankelijk van de vereiste verbinding, sluit uw formulier aan op een JSON-schema of formuliergegevensmodel:

* [ creeer een Schema JSON en upload aan uw milieu ](/help/forms/using/adaptive-form-json-schema-form-model.md)
* [ creeer een Model van de Gegevens van de Vorm ](/help/forms/using/create-form-data-models.md)

### Een JSON-schema of formuliergegevensmodel voor uw formulier configureren

Een JSON-schema of formuliergegevensmodel configureren voor uw formulier:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Open de tab **[!UICONTROL Data Model]** .

   ![ klik het pictogram van de Sleutel om de Adaptieve de dialoogdoos van de Container van de Vorm te openen om een JSON- schema of model van vormgegevens te vormen ](/help/forms/using/assets/adaptive-forms-select-form-data-model-or-json-schema.png)

1. Selecteer en configureer een JSON-schema of formuliergegevensmodel op basis van uw vereisten:

   * Als u de optie **[!UICONTROL Form Model]** selecteert, gebruikt u de optie **[!UICONTROL Select Form Data Model]** om een vooraf geconfigureerd formuliergegevensmodel te selecteren.
   * Als u de optie **[!UICONTROL Schema]** selecteert, gebruikt u de optie **[!UICONTROL Schema]** om een JSON-schema voor uw formulier te selecteren.

1. Klik op **[!UICONTROL Done]**.

>[!NOTE]
>
> U kunt het JSON-schema of het formuliergegevensmodel voor een adaptief formulier bewerken met de eigenschappen van de Guide Container.

## Een prefill-service configureren  {#configure-prefill-service-for-form}

U kunt de Prefill-service gebruiken om automatisch velden van een adaptief formulier in te vullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. U kunt:

* [Een aangepaste prefill-service maken](/help/forms/using/prepopulate-adaptive-form-fields.md)
* [Vooraf ingevulde service Formuliergegevensmodel gebruiken](#fdm-prefill-service)

### De service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen {#fdm-prefill-service}

U kunt de service Vooraf invullen van formuliergegevensmodel gebruiken om velden van een adaptief formulier vooraf in te vullen met een formuliergegevensmodel of een aangepaste voorinvulservice. Het model van Gegevens van de Vorm Prefill de dienst gebruikt [ krijgt Dienst van het gevormde Model van Gegevens van de Vorm ](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) om gegevens terug te winnen. Als u de service Vooraf invullen van formuliergegevensmodel wilt gebruiken voor een adaptief formulier:

1. Open de browser Inhoud en selecteer de component **[!UICONTROL Guide Container]** van het adaptieve formulier.
1. Klik de eigenschappen van de Container van de Gids ![ eigenschappen van de Gids ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer wordt geopend.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![ klik het pictogram van de Sleutel om de Aangepaste de dialoogdoos van de Container van de Vorm te openen om een omleidingspagina te vormen of u te danken bericht ](/help/forms/using/assets/adaptive-forms-container-prefill-service.png)
1. Selecteer een formuliergegevensmodel. Open de tab **[!UICONTROL Basic]** . Selecteer **[!UICONTROL Form Data Model Prefill Service]** in de service Prefill.
1. Klik op **[!UICONTROL Done]**. Uw adaptieve formulier is nu geconfigureerd voor vooraf invullen van formuliergegevensmodel. U kunt nu, de [ regelredacteur ](rule-editor.md) gebruiken om regels tot stand te brengen om gebieden van de vorm vooraf in te vullen.

## Hoe wijzigt u de naam van een AEM adaptief formulier?{#rename-an-AEM-Adaptive-Form}

Voer de volgende stappen uit om de naam van een adaptief formulier te wijzigen:

1. Selecteer een adaptief formulier in uw AEM Forms-gebruikersinterface.
1. Klik op **Eigenschappen** die op de hogere spoorstaaf wordt gevestigd.

   ![ Eigenschappen ](/help/forms/using/assets/rename-form-properties.png)

1. Verander de naam van de vorm op het **lusje van de Titel**, zoals aangetoond in het hieronder beeld.
1. Klik **sparen en Sluiten**.

   ![ noem een AEM Aanpassings Vorm ](/help/forms/using/assets/rename-form-title.png) anders


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
* [ de themasjablonen van de Steekproef en modellen van vormgegevens ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/sample-themes-templates-form-data-models-core-components.html)
