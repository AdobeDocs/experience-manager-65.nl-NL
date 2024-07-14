---
title: De handeling Verzenden configureren
description: Met Forms kunt u een verzendactie configureren om te definiëren hoe een adaptief formulier na verzending wordt verwerkt. U kunt ingebouwde verzendacties gebruiken of zelf schrijven.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 04efb4ad-cff6-4e05-bcd2-98102f052452
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 0%

---

# De handeling Verzenden configureren {#configuring-the-submit-action}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html) |
| AEM 6,5 | Dit artikel |


## Inleiding om acties in te dienen {#introduction-to-submit-actions}

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. U kunt de verzendactie configureren voor een adaptief formulier. Adaptieve formulieren bevatten een paar elementen uit het vak Acties verzenden. U kunt de standaardverzendacties kopiëren en uitbreiden om uw eigen verzendactie te maken. Op basis van uw vereisten kunt u echter uw eigen verzendactie schrijven en registreren om gegevens in het verzonden formulier te verwerken. Verzenden actie kan [ synchrone of asynchrone voorlegging ](../../forms/using/asynchronous-submissions-adaptive-forms.md) gebruiken.

U kunt een verzendactie in de **sectie van de Verzending** van de Adaptieve eigenschappen van de Container van de Vorm vormen, in sidebar.

![ vormen voorleggen Actie ](assets/thank-you-setting.png)

Verzendhandeling configureren

De standaardverzendacties die beschikbaar zijn in aangepaste formulieren zijn:

* Verzenden naar REST-eindpunt
* E-mail verzenden
* PDF verzenden via e-mail
* Een Forms Workflow aanroepen
* Verzenden met gebruik van formuliergegevensmodel
* Forms Portal-verzendactie
* Een AEM-workflow aanroepen
* Verzenden naar Power Automate

>[!NOTE]
>
>PDF verzenden via e-mail verzenden is alleen van toepassing op adaptieve formulieren die XFA-sjabloon gebruiken als formuliermodel.

>[!NOTE]
>
>Zorg ervoor dat de {] \crx-quickstart\temp\datamanager\ASM omslag 0} AEM_Installation_Directory[
>bestaat. De map is vereist om bijlagen tijdelijk op te slaan. Als de map niet bestaat, maakt u deze.

>[!CAUTION]
>
>Als u [ ](../../forms/using/prepopulate-adaptive-form-fields.md) een vormmalplaatje, model van vormgegevens, of schema gebaseerde adaptieve vorm met XML of JSON gegevensklacht aan een schema (het schema van XML, JSON schema, vormmalplaatje, of model van vormgegevens) vooraf instelt dat geen gegevens &lt;afData>, &lt;afBoundData>, en &lt;/afUnboundData> markeringen bevat, dan zijn de gegevens van onbegrensde gebieden De actieve vormgebieden zonder [ bindref ](../../forms/using/prepopulate-adaptive-form-fields.md) bezit) van de adaptieve vorm wordt verloren.

U kunt een aangepaste verzendactie schrijven voor aangepaste formulieren om aan uw gebruiksscenario te voldoen. Voor meer informatie, zie [ het Schrijven van douane verzendt actie voor adaptieve vormen ](../../forms/using/custom-submit-action-form.md).

## Verzenden naar REST-eindpunt {#submit-to-rest-endpoint}

**legt aan REST eindpunt** voor voorlegt optie gaat de gegevens die in de vorm aan een gevormde bevestigingspagina als deel van het verzoek van de GET van HTTP worden gevuld over. U kunt de naam toevoegen van de velden die u wilt aanvragen. De indeling van het verzoek is:

`{fieldName}={request parameter name}`

Zoals aangetoond in het beeld hieronder, `param1` en `param2` worden overgegaan als parameters met waarden die van **worden gekopieerd textbox** en **numerieke doos** gebieden voor de volgende actie.

U kunt **verzoek van de POST** ook toelaten en URL verstrekken om het verzoek te posten. Als u gegevens wilt verzenden naar de server van de Experience Manager die als host fungeert voor het formulier, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de server van de Experience Manager. Bijvoorbeeld /content/forms/af/SampleForm.html. Gebruik absoluut pad om gegevens naar een andere server te verzenden.

![ Vormend Rest Eindpunt legt Actie ](assets/action-config.png) voor

Rest Endpoint-verzendhandeling configureren

>[!NOTE]
>
Als u de velden als parameters in een REST-URL wilt doorgeven, moeten alle velden verschillende elementnamen hebben, zelfs als de velden op verschillende deelvensters zijn geplaatst.

### Post heeft gegevens naar een bron of een extern eindpunt voor de rusttijd verzonden  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Gebruik **voorleggen aan REST Endpoint** actie om de voorgelegde gegevens aan een rest URL te posten. De URL kan van een interne (de server waarop het formulier wordt gegenereerd) of van een externe server zijn.

Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld /content/restEndPoint. Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

Geef een URL op om gegevens naar een externe server te posten. De indeling van de URL is https://host:port/path_to_rest_end_point. Zorg ervoor dat u de weg vormt om het verzoek van de POST anoniem te behandelen.

![ Toewijzing voor gebiedswaarden die als Dank worden overgegaan de parameters van de Pagina ](assets/post-enabled-actionconfig.png)

In het bovenstaande voorbeeld wordt door de gebruiker ingevoerde informatie in `textbox` vastgelegd met parameter `param1` . De syntaxis voor het posten van gegevens die zijn vastgelegd met `param1` is:

`String data=request.getParameter("param1");`

Op dezelfde manier zijn de parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen `dataXml` en `attachments` .

U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

In dit voorbeeld slaat `data` de XML-gegevens op en slaat `att` de gegevens in de bijlage op.

## E-mail verzenden {#send-email}

**verzendt E-mail** verzendt actie verzendt een e-mail naar één of meerdere ontvangers op succesvolle voorlegging van de vorm. Het gegenereerde e-mailbericht kan formuliergegevens in een vooraf gedefinieerde indeling bevatten.

>[!NOTE]
>
Alle formuliervelden moeten verschillende elementnamen hebben, zelfs als ze op verschillende deelvensters zijn geplaatst), om formuliergegevens op te nemen in een e-mailbericht.

## PDF verzenden via e-mail {#send-pdf-via-email}

**verzendt PDF via E-mail** verzendt actie een e-mail met een PDF die vormgegevens bevat, naar één of meerdere ontvangers op succesvolle voorlegging van de vorm.

>[!NOTE]
>
Deze verzendactie is beschikbaar voor op XFA gebaseerde adaptieve formulieren en op XSD gebaseerde aanpassingsformulieren die de sjabloon Document of Record hebben.

## Een Forms Workflow aanroepen {#invoke-a-forms-workflow}

**voorlegt aan Forms Workflow** voorlegt optie verzendt een gegevens xml en dossiergehechtheid (als om het even welk) naar een bestaand LiveCycle van de Adobe of AEM Forms op JEE proces.

Voor informatie over hoe te om Submit aan Forms Workflow te vormen verzend actie, zie [ Verzenden en verwerkend uw vormgegevens gebruikend vormwerkschema&#39;s ](../../forms/using/submit-form-data-livecycle-process.md).

## Verzenden met gebruik van formuliergegevensmodel {#submit-using-form-data-model}

**voorleggen gebruikend het Model van de Gegevens van de Vorm** voorlegt actie schrijft voorgelegde adaptieve vormgegevens voor het gespecificeerde voorwerp van het gegevensmodel in een model van vormgegevens aan zijn gegevensbron. Wanneer het vormen van voorlegt actie, kunt u een voorwerp van het gegevensmodel kiezen waarvan voorgelegde gegevens u terug naar zijn gegevensbron wilt schrijven.

Daarnaast kunt u een formulierbijlage verzenden met behulp van een formuliergegevensmodel en een Document of Record (DoR) naar de gegevensbron.

Voor informatie over het model van vormgegevens, zie [ de Integratie van Gegevens van AEM Forms ](../../forms/using/data-integration.md).

## Forms Portal-verzendactie {#forms-portal-submit-action}

De **Portaal van Forms legt Actie** optie voor maakt vormgegevens beschikbaar door een Portaal van AEM Forms.

Voor meer informatie over het Portaal van Forms en voorlegt actie, zie [ Concepten en voorleggingscomponent ](../../forms/using/draft-submission-component.md).

## Een AEM-workflow aanroepen {#invoke-an-aem-workflow}

**[!UICONTROL Invoke an AEM Workflow]** legt Actie associeert een Aangepaste Vorm met een [ AEM Werkschema ](/help/sites-developing/workflows-models.md) voor. Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart bij de instantie Auteur. U kunt het gegevensbestand, de gehechtheid, en het Document van Verslag aan de omslag met betrekking tot of onder de lading van het werkschema of aan een variabele opslaan. Als de workflow is gemarkeerd voor externe gegevensopslag, is de optie Variabele beschikbaar en niet de optie voor laden. U kunt uit de lijst van variabelen selecteren beschikbaar voor het werkschemamodel. Als de workflow later wordt gemarkeerd voor externe gegevensopslag en niet op het moment dat de workflow wordt gemaakt, moet u ervoor zorgen dat de vereiste variabele configuraties aanwezig zijn.

Alvorens te gebruiken **aanvoed een AEM van het Werkschema** voorlegt actie, [ vormt de Experience Manager DS montages ](../../forms/using/configuring-the-processing-server-url.md). Voor informatie over het creëren van een AEMWerkschema, zie [ vorm-centric werkschema&#39;s op OSGi ](../../forms/using/aem-forms-workflow.md).

Met de handeling Verzenden wordt het volgende op de laadlocatie van de workflow geplaatst. Houd er echter rekening mee dat alleen de optie Variabele wordt weergegeven als het workflowmodel is gemarkeerd voor externe gegevensopslag, en niet de optie voor laden.

* **dossier van Gegevens**: Het bevat gegevens die aan de Aangepaste Vorm worden voorgelegd. Met de optie **[!UICONTROL Data File Path]** kunt u de naam van het bestand en het pad van het bestand ten opzichte van de laadbewerking opgeven. Het pad `/addresschange/data.xml` maakt bijvoorbeeld een map met de naam `addresschange` en plaatst deze relatief ten opzichte van de laadbewerking. U kunt ook alleen `data.xml` opgeven om alleen verzonden gegevens te verzenden zonder een maphiërarchie te maken. Gebruik de optie Variabele en selecteer de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

>[!NOTE]
>
Variabelen kunnen worden gebruikt, ongeacht of het workflowmodel is gemarkeerd voor externe gegevensopslag.

* **Gehechtheid**: U kunt de **[!UICONTROL Attachment Path]** optie gebruiken om de omslagnaam te specificeren om de gehechtheid op te slaan die aan de Aangepaste Vorm wordt geupload. De map wordt gemaakt ten opzichte van de lading. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

* **Document van Verslag**: Het bevat het Document van Verslag dat voor de Adaptieve Vorm wordt geproduceerd. U kunt de optie **[!UICONTROL Document of Record Path]** gebruiken om de naam van het document van het dossier van het Verslag en weg van dossier met betrekking tot de lading te specificeren. Het pad `/addresschange/DoR.pdf` maakt bijvoorbeeld een map met de naam `addresschange` ten opzichte van de laadbewerking en plaatst de map `DoR.pdf` ten opzichte van de laadbewerking. U kunt ook alleen `DoR.pdf` opgeven om alleen Document of Record op te slaan zonder een maphiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

## Verzenden naar Power Automate {#microsoft-power-automate}

U kunt een adaptief formulier configureren om een Microsoft® Power Automate Cloud Flow uit te voeren bij verzending. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren. Hier volgen enkele voorbeelden van wat u kunt doen na de integratie van een adaptief formulier met Microsoft® Power Automate:

* Adaptieve Forms-gegevens gebruiken in een Power Automate-bedrijfsprocessen
* Gebruik Power Automate om vastgelegde gegevens naar meer dan 500 gegevensbronnen of een openbaar beschikbare API te verzenden
* Complexe berekeningen uitvoeren op vastgelegde gegevens
* Adaptieve Forms-gegevens opslaan naar opslagsystemen volgens een vooraf bepaald schema

De adaptieve redacteur van Forms verstrekt **roept een stroom van de Macht Microsoft®** verzendt actie om adaptieve vormengegevens, gehechtheid, en Document van Verslag te verzenden aan Macht de Stroom van de Wolk van de Automatisering. Om de Submit actie te gebruiken om gevangen gegevens naar Microsoft® Power Automate te verzenden, [ verbind uw instantie van AEM Forms met Microsoft® Macht ](/help/forms/using/forms-microsoft-power-automate-integration.md)

Na een succesvolle configuratie, gebruik [ aanhaalt een Macht Microsoft® stroom ](/help/forms/using/forms-microsoft-power-automate-integration.md#use-the-invoke-a-microsoft&reg;-power-automate-flow-submit-action-to-send-data-to-a-power-automate-flow-use-the-invoke-microsoft-power-automate-flow-submit-action) verzendt actie om gegevens naar een Macht te verzenden automatisch Stroom.

## Verzenden naar Microsoft® SharePoint List{#submit-to-sharedrive}

>[!NOTE]
>
De functie Verzenden naar Microsoft® SharePoint List is geïntroduceerd met AEM 6.5 Forms Service Pack 19 (6.5.19.0).

Met de handeling **[!UICONTROL Submit to SharePoint]** Verzenden wordt een adaptief formulier verbonden met een Microsoft® SharePoint-opslag. U kunt het bestand met formuliergegevens, bijlagen of het document met records verzenden naar de aangesloten Microsoft® SharePoint-opslag.

### Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst {#connect-af-sharepoint-list}

Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst:

1. [ creeer een Configuratie van de Lijst van SharePoint ](#create-sharepoint-list-configuration): Het verbindt AEM Forms met uw Opslag van de Lijst van SharePoint Microsoft®.
1. [ gebruik **voorlegt gebruikend het Model van de Gegevens van de Vorm** voorlegt actie in een Aangepaste Vorm ](#use-submit-using-fdm): Het verzendt uw Aangepaste gegevens van de Vorm naar gevormde Microsoft® SharePoint.

#### Een SharePoint List-configuratie maken {#create-sharepoint-list-configuration}

AEM Forms verbinden met uw Microsoft® SharePoint-lijst:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft® SharePoint]** .
1. Selecteer de Container van de a **Configuratie**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klik op **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** in de vervolgkeuzelijst. De configuratietovenaar van SharePoint verschijnt.
1. Geef de waarden **[!UICONTROL Title]** , **[!UICONTROL Client ID]** , **[!UICONTROL Client Secret]** en **[!UICONTROL OAuth URL]** op. Voor informatie over hoe te om identiteitskaart van de Cliënt terug te winnen, Geheime cliënt, identiteitskaart van de Aannemer voor OAuth URL, zie [ Documentatie Microsoft® ](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * U kunt de `Client ID` en `Client Secret` van uw app ophalen via de Microsoft® Azure-portal.
   * Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html` . Vervang `[author-instance]` door de URL van de instantie Auteur.
   * Voeg de API toestemmingen `offline_access` en `Sites.Manage.All` in het **Microsoft® Grafiek** lusje toe om lees-schrijftoestemmingen te verstrekken. Voeg `AllSites.Manage` toestemming in het **SharePoint** lusje toe om ver met de gegevens van SharePoint in wisselwerking te staan.
   * Gebruik OAuth URL: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervang `<tenant-id>` door `tenant-id` van uw app via de Microsoft® Azure-portal.

     >[!NOTE]
     >
     Het **cliënt geheime** gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt het bericht `Connection Successful` weergegeven.
1. Selecteer **[!UICONTROL SharePoint Site]** en **[!UICONTROL SharePoint List]** in de vervolgkeuzelijst.
1. Tik op **[!UICONTROL Create]** om de cloudconfiguratie voor de Microsoft® SharePointList te maken.

#### Verzenden met gebruik van het formuliergegevensmodel in een adaptief formulier gebruiken {#use-submit-using-fdm}

U kunt de gemaakte SharePoint List-configuratie in een adaptief formulier gebruiken om gegevens of het gegenereerde Document of Record in een SharePoint-lijst op te slaan. Voer de volgende stappen uit om een SharePoint List-opslagconfiguratie in een adaptief formulier te gebruiken als:

1. [Een formuliergegevensmodel maken met Microsoft](/help/forms/using/create-form-data-model.md)
1. [Het formuliergegevensmodel configureren voor het ophalen en verzenden van gegevens](/help/forms/using/work-with-form-data-model.md#configure-services)
1. [ creeer een AanpassingsVorm ](/help/forms/using/create-adaptive-form.md).
1. [Verzendactie configureren met een formuliergegevensmodel](/help/forms/using/configuring-submit-actions.md#submit-using-form-data-model-submit)

Wanneer u het formulier verzendt, worden de gegevens opgeslagen in de opgegeven Microsoft® Sharepoint List Storage.

>[!NOTE]
>
In Microsoft® SharePoint List worden de volgende kolomtypen niet ondersteund:
* afbeeldingskolom
* metagegevenskolom
* persoonlijke kolom
* kolom externe gegevens


>[!NOTE]
>
Om waarden van een configuratie te plaatsen, [ produceer OSGi Configuraties gebruikend de AEM SDK ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [ stel de configuratie ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) aan uw instantie van de Cloud Service op.

## Revalidatie op de server in adaptieve vorm {#server-side-revalidation-in-adaptive-form}

In elk onlinesysteem voor gegevensvastlegging plaatsen ontwikkelaars doorgaans bepaalde JavaScript-validaties op de client om een aantal bedrijfsregels af te dwingen. Maar in moderne browsers, moeten de eindgebruikers die bevestigingen omzeilen en manueel bijdragen gebruikend diverse technieken, zoals Browser van het Web DevTools Console indienen. Dergelijke technieken zijn ook geldig voor adaptieve formulieren. Een formulierontwikkelaar kan verschillende validatielogboeken maken, maar technisch kunnen eindgebruikers die validatielogboeken omzeilen en ongeldige gegevens naar de server verzenden. Ongeldige gegevens zouden de bedrijfsregels overtreden die een auteur van formulieren heeft afgedwongen.

Met de functie voor opnieuw valideren aan de serverzijde kunt u ook de validaties uitvoeren die door de auteur van een adaptief formulier zijn verstrekt tijdens het ontwerpen van een adaptief formulier op de server. Hierdoor wordt voorkomen dat bij het verzenden van gegevens en bij het valideren van formulieren inbreuk wordt gemaakt op de bedrijfsregels.

### Wat moet u op de server valideren? {#what-to-validate-on-server-br}

Alle buiten-de-box veldvalidaties van een adaptief formulier die opnieuw worden uitgevoerd op de server zijn:

* Vereist
* Clausule voor validatie
* Validatie-expressie

### Validatie op de server inschakelen {#enabling-server-side-validation-br}

Gebruik **Revalidate op server** onder de Aangepaste Container van de Vorm in sidebar om server-zijbevestiging voor de huidige vorm toe te laten of onbruikbaar te maken.

![ toelatend server-zijBevestiging ](assets/revalidate-on-server.png)

Validatie op de server inschakelen

Als de eindgebruiker deze validaties overslaat en de formulieren verzendt, wordt de validatie opnieuw uitgevoerd door de server. Als de validatie aan het einde van de server mislukt, wordt de verzendtransactie gestopt. De eindgebruiker krijgt het oorspronkelijke formulier opnieuw te zien. De vastgelegde gegevens en verzonden gegevens worden als een fout aan de gebruiker gepresenteerd.

>[!NOTE]
>
Servervalidatie valideert het formuliermodel. Het wordt aanbevolen een aparte clientbibliotheek voor validaties te maken en deze niet te mengen met andere elementen, zoals HTML styling en DOM-bewerking in dezelfde clientbibliotheek.

### Aangepaste functies ondersteunen in validatie-expressies {#supporting-custom-functions-in-validation-expressions-br}

Als er soms complexe validatieregels zijn, bevindt het exacte validatiescript zich in aangepaste functies en roept de auteur deze aangepaste functies aan vanuit de expressie voor veldvalidatie. Om deze bibliotheek van de douanefunctie te maken gekend en beschikbaar terwijl het uitvoeren van server-zijbevestigingen, kan de vormauteur de naam van AEM cliëntbibliotheek onder het **Basis** lusje van de Eigenschappen van de Container van de Vorm de Adaptieve zoals hieronder getoond vormen.

![ ondersteunend de functies van de Douane in Uitdrukkingen van de Bevestiging ](assets/clientlib-cat.png)

Aangepaste functies ondersteunen in validatie-expressies

Auteurs kunnen de aangepaste JavaScript-bibliotheek per adaptief formulier configureren. Houd in de bibliotheek alleen de herbruikbare functies die afhankelijk zijn van bibliotheken van derden jquery en underscore.js.

## Foutafhandeling bij verzendactie {#error-handling-on-submit-action}

Als deel van de veiligheid van de Experience Manager en het verharden richtlijnen, vorm de pagina&#39;s van de douanefout zoals 404.jsp en 500.jsp. Deze handlers worden aangeroepen wanneer bij het verzenden van een formulier 404 of 500 fouten worden weergegeven. De handlers worden ook geroepen wanneer deze foutencodes op de knoop van Publish worden teweeggebracht.

Voor meer informatie, zie [ Aanpassen Pagina&#39;s die door de Handler van de Fout ](/help/sites-developing/customizing-errorhandler-pages.md) worden getoond.
