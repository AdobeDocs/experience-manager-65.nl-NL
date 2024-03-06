---
title: De handeling Verzenden configureren
description: Met Forms kunt u een verzendactie configureren om te definiëren hoe een adaptief formulier na verzending wordt verwerkt. U kunt ingebouwde verzendacties gebruiken of zelf schrijven.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 04efb4ad-cff6-4e05-bcd2-98102f052452
source-git-commit: 0aa929021aa724e4ec18d49fea26f8c0b0538bdc
workflow-type: tm+mt
source-wordcount: '2556'
ht-degree: 0%

---

# De handeling Verzenden configureren {#configuring-the-submit-action}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html) |
| AEM 6,5 | Dit artikel |


## Inleiding om acties in te dienen {#introduction-to-submit-actions}

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. U kunt de verzendactie configureren voor een adaptief formulier. Adaptieve formulieren bevatten een paar elementen uit het vak Acties verzenden. U kunt de standaardverzendacties kopiëren en uitbreiden om uw eigen verzendactie te maken. Op basis van uw vereisten kunt u echter uw eigen verzendactie schrijven en registreren om gegevens in het verzonden formulier te verwerken. De verzendactie kan worden gebruikt [synchrone of asynchrone verzending](../../forms/using/asynchronous-submissions-adaptive-forms.md).

U kunt een verzendactie configureren in het dialoogvenster **Indiening** in de zijbalk van de eigenschappen van de container voor adaptieve formulieren.

![Verzendhandeling configureren](assets/thank-you-setting.png)

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
>Zorg ervoor dat de [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM
>bestaat. De map is vereist om bijlagen tijdelijk op te slaan. Als de map niet bestaat, maakt u deze.

>[!CAUTION]
>
>Als u [voorvoegsel](../../forms/using/prepopulate-adaptive-form-fields.md) een formuliersjabloon, formuliergegevensmodel of op schema gebaseerd adaptief formulier met XML- of JSON-gegevensklacht voor een schema (XML-schema, JSON-schema, formuliersjabloon of formuliergegevensmodel) dat geen gegevens bevat &lt;afdata>, &lt;afbounddata>, en &lt;/afunbounddata> -tags, dan worden de gegevens van niet-omsloten velden (Niet-omlijnde velden zijn adaptieve formuliervelden zonder [bindref](../../forms/using/prepopulate-adaptive-form-fields.md) eigenschap) van het adaptieve formulier verloren gaat.

U kunt een aangepaste verzendactie schrijven voor aangepaste formulieren om aan uw gebruiksscenario te voldoen. Zie voor meer informatie [Aangepaste verzendactie schrijven voor adaptieve formulieren](../../forms/using/custom-submit-action-form.md).

## Verzenden naar REST-eindpunt {#submit-to-rest-endpoint}

De **Verzenden naar REST-eindpunt** Met deze optie worden de gegevens die in het formulier zijn ingevuld, doorgegeven aan een geconfigureerde bevestigingspagina als onderdeel van de HTTP-aanvraag. U kunt de naam toevoegen van de velden die u wilt aanvragen. De indeling van het verzoek is:

`{fieldName}={request parameter name}`

Zoals in de onderstaande afbeelding wordt getoond: `param1` en `param2` worden doorgegeven als parameters met waarden die zijn gekopieerd uit de **textbox** en **numeriek vak** velden voor de volgende actie.

U kunt **Aanvraag POST inschakelen** en geef een URL op om de aanvraag te posten. Als u gegevens wilt verzenden naar de server van de Experience Manager die als host fungeert voor het formulier, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de server van de Experience Manager. Bijvoorbeeld /content/forms/af/SampleForm.html. Gebruik absoluut pad om gegevens naar een andere server te verzenden.

![Rest Endpoint-verzendhandeling configureren](assets/action-config.png)

Rest Endpoint-verzendhandeling configureren

>[!NOTE]
>
Als u de velden als parameters in een REST-URL wilt doorgeven, moeten alle velden verschillende elementnamen hebben, zelfs als de velden op verschillende deelvensters zijn geplaatst.

### Gegevens naar een bron of een extern eindpunt voor de rusttijd verzenden  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Gebruik de **Verzenden naar REST-eindpunt** actie om de verzonden gegevens op een rest-URL te plaatsen. De URL kan van een interne (de server waarop het formulier wordt gegenereerd) of van een externe server zijn.

Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld /content/restEndPoint. Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

Geef een URL op om gegevens naar een externe server te posten. De indeling van de URL is https://host:port/path_to_rest_end_point. Zorg ervoor dat u de weg vormt om het verzoek van de POST anoniem te behandelen.

![Toewijzing voor veldwaarden die zijn doorgegeven als parameters voor de pagina Bedankt](assets/post-enabled-actionconfig.png)

In het bovenstaande voorbeeld heeft de gebruiker informatie ingevoerd in `textbox` wordt vastgelegd met parameter `param1`. Syntaxis om gegevens te posten die zijn vastgelegd met `param1` is:

`String data=request.getParameter("param1");`

Ook parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen zijn `dataXml` en `attachments`.

U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

In dit voorbeeld: `data` de XML-gegevens worden opgeslagen, en `att` slaat gehechtheidsgegevens op.

## E-mail verzenden {#send-email}

De **E-mail verzenden** Met een handeling verzenden wordt een e-mail naar een of meer ontvangers verzonden wanneer het formulier met succes is verzonden. Het gegenereerde e-mailbericht kan formuliergegevens in een vooraf gedefinieerde indeling bevatten.

>[!NOTE]
>
Alle formuliervelden moeten verschillende elementnamen hebben, zelfs als ze op verschillende deelvensters zijn geplaatst), om formuliergegevens op te nemen in een e-mailbericht.

## PDF verzenden via e-mail {#send-pdf-via-email}

De **PDF verzenden via e-mail** Met een verzendactie wordt een e-mail met een PDF met formuliergegevens verzonden naar een of meer ontvangers wanneer het formulier met succes is verzonden.

>[!NOTE]
>
Deze verzendactie is beschikbaar voor op XFA gebaseerde adaptieve formulieren en op XSD gebaseerde aanpassingsformulieren die de sjabloon Document of Record hebben.

## Een Forms Workflow aanroepen {#invoke-a-forms-workflow}

De **Verzenden naar Forms Workflow** Met de optie Verzenden worden een gegevens-xml en bestandsbijlagen (indien aanwezig) naar een bestaand Adobe-LiveCycle of AEM Forms verzonden tijdens JEE-proces.

Voor informatie over hoe te om Submit aan Forms Workflow te vormen verzend actie, zie [Uw formuliergegevens verzenden en verwerken met behulp van formulierworkflows](../../forms/using/submit-form-data-livecycle-process.md).

## Verzenden met gebruik van formuliergegevensmodel {#submit-using-form-data-model}

De **Verzenden met gebruik van formuliergegevensmodel** Met deze handeling worden verzonden verzonden verzonden aangepaste formuliergegevens voor het opgegeven gegevensmodelobject in een formuliergegevensmodel naar de gegevensbron ervan. Wanneer het vormen van voorlegt actie, kunt u een voorwerp van het gegevensmodel kiezen waarvan voorgelegde gegevens u terug naar zijn gegevensbron wilt schrijven.

Daarnaast kunt u een formulierbijlage verzenden met behulp van een formuliergegevensmodel en een Document of Record (DoR) naar de gegevensbron.

Zie voor informatie over het formuliergegevensmodel [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md).

## Forms Portal-verzendactie {#forms-portal-submit-action}

De **Forms Portal-verzendactie** maakt formuliergegevens beschikbaar via een AEM Forms Portal.

Ga voor meer informatie over de Forms Portal en verzend actie naar [Concepten en verzendingen](../../forms/using/draft-submission-component.md).

## Een AEM-workflow aanroepen {#invoke-an-aem-workflow}

De **[!UICONTROL Invoke an AEM Workflow]** Een adaptief formulier wordt gekoppeld aan een [AEM](/help/sites-developing/workflows-models.md). Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart bij de instantie Auteur. U kunt het gegevensbestand, de gehechtheid, en het Document van Verslag aan de omslag met betrekking tot of onder de lading van het werkschema of aan een variabele opslaan. Als de workflow is gemarkeerd voor externe gegevensopslag, is de optie Variabele beschikbaar en niet de optie voor laden. U kunt uit de lijst van variabelen selecteren beschikbaar voor het werkschemamodel. Als de workflow later wordt gemarkeerd voor externe gegevensopslag en niet op het moment dat de workflow wordt gemaakt, moet u ervoor zorgen dat de vereiste variabele configuraties aanwezig zijn.

Voordat u de **Een AEM-workflow aanroepen** actie indienen; [configureren van de Experience Manager DS-instellingen](../../forms/using/configuring-the-processing-server-url.md). Voor informatie over het creëren van een AEM- Werkstroom, zie [Formuliergerichte workflows op OSGi](../../forms/using/aem-forms-workflow.md).

Met de handeling Verzenden wordt het volgende op de laadlocatie van de workflow geplaatst. Houd er echter rekening mee dat alleen de optie Variabele wordt weergegeven als het workflowmodel is gemarkeerd voor externe gegevensopslag, en niet de optie voor laden.

* **Gegevensbestand**: Het bevat gegevens die naar het adaptieve formulier worden verzonden. U kunt de **[!UICONTROL Data File Path]** om de naam van het bestand en het pad van het bestand ten opzichte van de laadbewerking op te geven. Bijvoorbeeld de `/addresschange/data.xml` pad maakt een map met de naam `addresschange` en plaatst deze ten opzichte van de lading. U kunt ook alleen `data.xml` om alleen verzonden gegevens te verzenden zonder een maphiërarchie te maken. Gebruik de optie Variabele en selecteer de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

>[!NOTE]
>
Variabelen kunnen worden gebruikt, ongeacht of het workflowmodel is gemarkeerd voor externe gegevensopslag.

* **Bijlagen**: U kunt de opdracht **[!UICONTROL Attachment Path]** om de mapnaam op te geven waarin de bijlagen worden opgeslagen die naar het adaptieve formulier zijn geüpload. De map wordt gemaakt ten opzichte van de lading. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

* **Document van record**: Het bevat het Document of Record dat is gegenereerd voor het adaptieve formulier. U kunt de **[!UICONTROL Document of Record Path]** Hiermee geeft u de naam op van het bestand Document of Record en het pad van het bestand ten opzichte van de laadbewerking. Bijvoorbeeld de `/addresschange/DoR.pdf` pad maakt een map met de naam `addresschange` ten opzichte van de lading en plaatst het `DoR.pdf` ten opzichte van de lading. U kunt ook alleen `DoR.pdf` alleen Document of Record opslaan zonder een mappenhiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

## Verzenden naar Power Automate {#microsoft-power-automate}

U kunt een adaptief formulier configureren om een Microsoft® Power Automate Cloud Flow uit te voeren bij verzending. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren. Hier volgen enkele voorbeelden van wat u kunt doen na de integratie van een adaptief formulier met Microsoft® Power Automate:

* Adaptieve Forms-gegevens gebruiken in een Power Automate-bedrijfsprocessen
* Gebruik Power Automate om vastgelegde gegevens naar meer dan 500 gegevensbronnen of een openbaar beschikbare API te verzenden
* Complexe berekeningen uitvoeren op vastgelegde gegevens
* Adaptieve Forms-gegevens opslaan naar opslagsystemen volgens een vooraf bepaald schema

De Adaptive Forms-editor biedt de **Een Microsoft® Power Automate-flow aanroepen** verzenden actie om adaptieve formuliergegevens, bijlagen en Document of Record naar Power Automate Cloud Flow te verzenden. De handeling Verzenden gebruiken om vastgelegde gegevens naar Microsoft® Power Automate te verzenden, [Sluit uw AEM Forms-instantie aan met Microsoft® Power Automate](/help/forms/using/forms-microsoft-power-automate-integration.md)

Na een succesvolle configuratie, gebruik [Een Microsoft® Power Automate-flow aanroepen](/help/forms/using/forms-microsoft-power-automate-integration.md#use-the-invoke-a-microsoft&reg;-power-automate-flow-submit-action-to-send-data-to-a-power-automate-flow-use-the-invoke-microsoft-power-automate-flow-submit-action) verzenden actie om gegevens naar een Power Automate Flow te verzenden.

## Verzenden naar Microsoft® SharePoint List{#submit-to-sharedrive}

>[!NOTE]
>
De functie Verzenden naar Microsoft® SharePoint List is geïntroduceerd met AEM 6.5 Forms Service Pack 19 (6.5.19.0).

De **[!UICONTROL Submit to SharePoint]** Met de verzendactie wordt een adaptief formulier verbonden met een Microsoft® SharePoint Storage. U kunt het bestand met formuliergegevens, bijlagen of het document met records verzenden naar de aangesloten Microsoft® SharePoint-opslag.

### Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst {#connect-af-sharepoint-list}

Een adaptief formulier verbinden met de Microsoft® SharePoint-lijst:

1. [Een SharePoint List-configuratie maken](#create-sharepoint-list-configuration): AEM Forms wordt aangesloten op uw Microsoft® Sharepoint List Storage.
1. [Gebruik de **Verzenden met gebruik van formuliergegevensmodel** actie verzenden in een adaptief formulier](#use-submit-using-fdm): Het verzendt uw Adaptive Form-gegevens naar de geconfigureerde Microsoft® SharePoint.

#### Een SharePoint List-configuratie maken {#create-sharepoint-list-configuration}

AEM Forms verbinden met uw Microsoft® SharePoint-lijst:

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** >  **[!UICONTROL Microsoft® SharePoint]**.
1. Selecteer een **Configuratie-container**. De configuratie wordt opgeslagen in de geselecteerde Container van de Configuratie.
1. Klikken **[!UICONTROL Create]** > **[!UICONTROL SharePoint List]** in de vervolgkeuzelijst. De configuratietovenaar van SharePoint verschijnt.
1. Geef de **[!UICONTROL Title]**, **[!UICONTROL Client ID]**, **[!UICONTROL Client Secret]** en **[!UICONTROL OAuth URL]**. Voor informatie over hoe te om identiteitskaart van de Cliënt terug te winnen, Geheim, identiteitskaart van de Aannemer voor OAuth URL, zie [Microsoft®-documentatie](https://learn.microsoft.com/en-us/graph/auth-register-app-v2).
   * U kunt de `Client ID` en `Client Secret` van uw app via de Microsoft® Azure-portal.
   * Voeg in de Microsoft® Azure-portal de Redirect URI toe als `https://[author-instance]/libs/cq/sharepointlist/content/configurations/wizard.html`. Vervangen `[author-instance]` met de URL van uw instantie Auteur.
   * API-machtigingen toevoegen `offline_access` en `Sites.Manage.All` in de **Microsoft® Graph** om lees-/schrijfmachtigingen te bieden. Toevoegen `AllSites.Manage` toestemming in de **Sharepoint** -tabbladen gebruiken om op afstand te werken met de SharePoint-gegevens.
   * OAuth-URL gebruiken: `https://login.microsoftonline.com/tenant-id/oauth2/v2.0/authorize`. Vervangen `<tenant-id>` met de `tenant-id` van uw app via de Microsoft® Azure-portal.

     >[!NOTE]
     >
     De **clientgeheim** het gebied is verplicht of facultatief hangt van uw Azure Actieve de toepassingsconfiguratie van de Folder af. Als uw toepassing wordt gevormd om een cliëntgeheim te gebruiken, is het verplicht om het cliëntgeheim te verstrekken.

1. Klik op **[!UICONTROL Connect]**. Bij een geslaagde verbinding wordt de `Connection Successful` wordt weergegeven.
1. Selecteren **[!UICONTROL SharePoint Site]** en **[!UICONTROL SharePoint List]** in de vervolgkeuzelijst.
1. Tikken **[!UICONTROL Create]** om de cloudconfiguratie voor de Microsoft® SharePointList te maken.

#### Verzenden met gebruik van het formuliergegevensmodel in een adaptief formulier gebruiken {#use-submit-using-fdm}

U kunt de gemaakte SharePoint List-configuratie in een adaptief formulier gebruiken om gegevens of het gegenereerde Document of Record in een SharePoint-lijst op te slaan. Voer de volgende stappen uit om een SharePoint List-opslagconfiguratie in een adaptief formulier te gebruiken als:

1. [Een formuliergegevensmodel maken met Microsoft](/help/forms/using/create-form-data-model.md)
1. [Het formuliergegevensmodel configureren voor het ophalen en verzenden van gegevens](/help/forms/using/work-with-form-data-model.md#configure-services)
1. [Een adaptief formulier maken](/help/forms/using/create-adaptive-form.md).
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
Om waarden van een configuratie te plaatsen, [OSGi-configuraties genereren met de AEM SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#generating-osgi-configurations-using-the-aem-sdk-quickstart), en [stel de configuratie op](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=en#deployment-process) naar de instantie Cloud Service.

## Revalidatie op de server in adaptieve vorm {#server-side-revalidation-in-adaptive-form}

In elk onlinesysteem voor gegevensvastlegging plaatsen ontwikkelaars doorgaans bepaalde JavaScript-validaties op de client om een aantal bedrijfsregels af te dwingen. Maar in moderne browsers, moeten de eindgebruikers die bevestigingen omzeilen en manueel bijdragen gebruikend diverse technieken, zoals Browser van het Web DevTools Console indienen. Dergelijke technieken zijn ook geldig voor adaptieve formulieren. Een formulierontwikkelaar kan verschillende validatielogboeken maken, maar technisch kunnen eindgebruikers die validatielogboeken omzeilen en ongeldige gegevens naar de server verzenden. Ongeldige gegevens zouden de bedrijfsregels overtreden die een auteur van formulieren heeft afgedwongen.

Met de functie voor opnieuw valideren aan de serverzijde kunt u ook de validaties uitvoeren die door de auteur van een adaptief formulier zijn verstrekt tijdens het ontwerpen van een adaptief formulier op de server. Hierdoor wordt voorkomen dat bij het verzenden van gegevens en bij het valideren van formulieren inbreuk wordt gemaakt op de bedrijfsregels.

### Wat moet u op de server valideren? {#what-to-validate-on-server-br}

Alle buiten-de-box veldvalidaties van een adaptief formulier die opnieuw worden uitgevoerd op de server zijn:

* Vereist
* Clausule voor validatie
* Validatie-expressie

### Validatie op de server inschakelen {#enabling-server-side-validation-br}

Gebruik de **Revalidate op server** onder Adaptieve formuliercontainer in de zijbalk om validatie aan de serverzijde voor het huidige formulier in of uit te schakelen.

![Validatie op de server inschakelen](assets/revalidate-on-server.png)

Validatie op de server inschakelen

Als de eindgebruiker deze validaties overslaat en de formulieren verzendt, wordt de validatie opnieuw uitgevoerd door de server. Als de validatie aan het einde van de server mislukt, wordt de verzendtransactie gestopt. De eindgebruiker krijgt het oorspronkelijke formulier opnieuw te zien. De vastgelegde gegevens en verzonden gegevens worden als een fout aan de gebruiker gepresenteerd.

>[!NOTE]
>
Servervalidatie valideert het formuliermodel. Het wordt aanbevolen een aparte clientbibliotheek voor validaties te maken en deze niet te mengen met andere elementen, zoals HTML styling en DOM-bewerking in dezelfde clientbibliotheek.

### Aangepaste functies ondersteunen in validatie-expressies {#supporting-custom-functions-in-validation-expressions-br}

Als er soms complexe validatieregels zijn, bevindt het exacte validatiescript zich in aangepaste functies en roept de auteur deze aangepaste functies aan vanuit de expressie voor veldvalidatie. Als u deze aangepaste functiebibliotheek bekend en beschikbaar wilt maken tijdens het uitvoeren van validaties aan de serverzijde, kan de auteur van het formulier de naam van AEM clientbibliotheek configureren onder de **Basis** tabblad Adaptieve formuliercontainereigenschappen, zoals hieronder weergegeven.

![Aangepaste functies ondersteunen in validatie-expressies](assets/clientlib-cat.png)

Aangepaste functies ondersteunen in validatie-expressies

Auteurs kunnen de aangepaste JavaScript-bibliotheek per adaptief formulier configureren. Houd in de bibliotheek alleen de herbruikbare functies die afhankelijk zijn van bibliotheken van derden jquery en underscore.js.

## Foutafhandeling bij verzendactie {#error-handling-on-submit-action}

Als deel van de veiligheid van de Experience Manager en het verharden richtlijnen, vorm de pagina&#39;s van de douanefout zoals 404.jsp en 500.jsp. Deze handlers worden aangeroepen wanneer bij het verzenden van een formulier 404 of 500 fouten worden weergegeven. De handlers worden ook geroepen wanneer deze foutencodes op de Publish knoop worden teweeggebracht.

Zie voor meer informatie [Pagina&#39;s aanpassen die worden weergegeven door de fouthandler](/help/sites-developing/customizing-errorhandler-pages.md).
