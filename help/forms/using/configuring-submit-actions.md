---
title: De handeling Verzenden configureren
seo-title: Configuring the Submit action
description: Met Forms kunt u een verzendactie configureren om te definiëren hoe een adaptief formulier na verzending wordt verwerkt. U kunt ingebouwde verzendacties gebruiken of zelf schrijven.
uuid: 4368d648-88ea-4f84-a051-46296a1a084e
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 9d8d7044-ffce-4ab4-9543-a2d2f9da31e3
docset: aem65
feature: Adaptive Forms
exl-id: 04efb4ad-cff6-4e05-bcd2-98102f052452
source-git-commit: d9608d584e822accc0c198fcf1d1b706d065938e
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 0%

---

# De handeling Verzenden configureren{#configuring-the-submit-action}

## Inleiding om acties te verzenden {#introduction-to-submit-actions}

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. U kunt de verzendactie configureren op het aangepaste formulier. Adaptieve formulieren bevatten een paar elementen uit het vak Acties verzenden. U kunt de standaardverzendacties kopiëren en uitbreiden om uw eigen verzendactie te maken. Op basis van uw vereisten kunt u echter uw eigen verzendactie schrijven en registreren om gegevens in het verzonden formulier te verwerken. De verzendactie kan worden gebruikt [synchrone of asynchrone verzending](../../forms/using/asynchronous-submissions-adaptive-forms.md).

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

>[!NOTE]
>
>PDF verzenden via e-mail verzenden is alleen van toepassing op adaptieve formulieren die XFA-sjabloon gebruiken als formuliermodel.

>[!NOTE]
>
>Zorg ervoor dat de [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>bestaat. De map is vereist om bijlagen tijdelijk op te slaan. Als de map niet bestaat, maakt u deze.

>[!CAUTION]
>
>Als u [prefill](../../forms/using/prepopulate-adaptive-form-fields.md) een formuliersjabloon, formuliergegevensmodel of op schema gebaseerd adaptief formulier met XML- of JSON-gegevensklacht voor een schema (XML-schema, JSON-schema, formuliersjabloon of formuliergegevensmodel) dat geen gegevens bevat &lt;afdata>, &lt;afbounddata>, en &lt;/afunbounddata> -tags, dan worden de gegevens van niet-omsloten velden (Niet-omlijnde velden zijn adaptieve formuliervelden zonder [bindref](../../forms/using/prepopulate-adaptive-form-fields.md) eigenschap) van het adaptieve formulier verloren gaat.

U kunt een aangepaste verzendactie schrijven voor aangepaste formulieren om aan uw gebruiksscenario te voldoen. Zie voor meer informatie [Aangepaste verzendactie schrijven voor adaptieve formulieren](../../forms/using/custom-submit-action-form.md).

## Verzenden naar REST-eindpunt {#submit-to-rest-endpoint}

De **Verzenden naar REST-eindpunt** Met deze optie worden de gegevens die in het formulier zijn ingevuld, doorgegeven aan een geconfigureerde bevestigingspagina als onderdeel van de HTTP-aanvraag. U kunt de naam toevoegen van de velden die u wilt aanvragen. De indeling van het verzoek is:

`{fieldName}={request parameter name}`

Zoals in de onderstaande afbeelding wordt getoond: `param1` en `param2` worden doorgegeven als parameters met waarden die zijn gekopieerd uit de **textbox** en **numeriek vak** velden voor de volgende actie.

U kunt ook **Aanvraag POST inschakelen** en geef een URL op om de aanvraag te posten. Als u gegevens wilt verzenden naar de server van de Experience Manager die als host fungeert voor het formulier, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de server van de Experience Manager. Bijvoorbeeld /content/forms/af/SampleForm.html. Gebruik absoluut pad om gegevens naar een andere server te verzenden.

![Rest Endpoint-verzendhandeling configureren](assets/action-config.png)

Rest Endpoint-verzendhandeling configureren

>[!NOTE]
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
Alle formuliervelden moeten verschillende elementnamen hebben, zelfs als ze op verschillende deelvensters zijn geplaatst), om formuliergegevens op te nemen in een e-mailbericht.

## PDF verzenden via e-mail {#send-pdf-via-email}

De **PDF verzenden via e-mail** Met een verzendactie wordt een e-mail met een PDF met formuliergegevens verzonden naar een of meer ontvangers wanneer het formulier met succes is verzonden.

>[!NOTE]
Deze verzendactie is beschikbaar voor op XFA gebaseerde adaptieve formulieren en op XSD gebaseerde aanpassingsformulieren die de sjabloon Document of Record hebben.

## Een Forms Workflow aanroepen {#invoke-a-forms-workflow}

De **Verzenden naar Forms Workflow** Met de optie Verzenden worden een gegevens-xml en bestandsbijlagen (indien aanwezig) naar een bestaande Adobe LiveCycle of AEM Forms verzonden bij JEE-proces.

Voor informatie over hoe te om Submit aan Forms Workflow te vormen verzend actie, zie [Uw formuliergegevens verzenden en verwerken met behulp van formulierworkflows](../../forms/using/submit-form-data-livecycle-process.md).

## Verzenden met gebruik van formuliergegevensmodel {#submit-using-form-data-model}

De **Verzenden met gebruik van formuliergegevensmodel** Met deze handeling worden verzonden verzonden verzonden aangepaste formuliergegevens voor het opgegeven gegevensmodelobject in een formuliergegevensmodel naar de gegevensbron ervan. Wanneer het vormen van voorlegt actie, kunt u een voorwerp van het gegevensmodel kiezen waarvan voorgelegde gegevens u terug naar zijn gegevensbron wilt schrijven.

Daarnaast kunt u een formulierbijlage verzenden met behulp van een formuliergegevensmodel en een Document of Record (DoR) naar de gegevensbron.

Voor informatie over het formuliergegevensmodel raadpleegt u [AEM Forms-gegevensintegratie](../../forms/using/data-integration.md).

## Forms Portal-verzendactie {#forms-portal-submit-action}

De **Forms Portal-verzendactie** maakt formuliergegevens beschikbaar via een AEM Forms Portal.

Ga voor meer informatie over de Forms Portal en verzend actie naar [Concepten en verzendingen](../../forms/using/draft-submission-component.md).

## Een AEM-workflow aanroepen {#invoke-an-aem-workflow}

De **[!UICONTROL Invoke an AEM Workflow]** Bij Actie verzenden wordt een adaptief formulier gekoppeld aan een [AEM](/help/sites-developing/workflows-models.md). Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart bij de instantie Auteur. U kunt het gegevensbestand, de gehechtheid, en het Document van Verslag aan de omslag met betrekking tot of onder de lading van het werkschema of aan een variabele opslaan. Als de workflow is gemarkeerd voor externe gegevensopslag, is de optie Variabele beschikbaar en niet de optie voor laden. U kunt uit de lijst van variabelen selecteren beschikbaar voor het werkschemamodel. Als de workflow later wordt gemarkeerd voor externe gegevensopslag en niet op het moment dat de workflow wordt gemaakt, moet u ervoor zorgen dat de vereiste variabele configuraties aanwezig zijn.

Voordat u de **Een AEM-workflow aanroepen** actie indienen; [vorm de Experience Manager DS montages](../../forms/using/configuring-the-processing-server-url-.md). Voor informatie over het creëren van een AEM- Werkstroom, zie [Formuliergerichte workflows op OSGi](../../forms/using/aem-forms-workflow.md).

Met de handeling Verzenden wordt het volgende op de laadlocatie van de workflow geplaatst. Houd er echter rekening mee dat alleen de optie Variabele wordt weergegeven als het workflowmodel is gemarkeerd voor externe gegevensopslag, en niet de optie voor laden.

* **Gegevensbestand**: Het bevat gegevens die naar het adaptieve formulier worden verzonden. U kunt de **[!UICONTROL Data File Path]** om de naam van het bestand en het pad van het bestand ten opzichte van de lading op te geven. De `/addresschange/data.xml` pad maakt een map met de naam `addresschange` en plaatst deze ten opzichte van de lading. U kunt ook alleen `data.xml` om alleen verzonden gegevens te verzenden zonder een maphiërarchie te maken. Gebruik de optie Variabele en selecteer de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

>[!NOTE]
Variabelen kunnen worden gebruikt, ongeacht of het workflowmodel is gemarkeerd voor externe gegevensopslag.

* **Bijlagen**: U kunt de **[!UICONTROL Attachment Path]** om de mapnaam op te geven waarin de bijlagen worden opgeslagen die naar het adaptieve formulier zijn geüpload. De map wordt gemaakt ten opzichte van de lading. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

* **Document van record**: Het bevat het Document van Verslag dat voor het Aangepaste Vorm wordt geproduceerd. U kunt de **[!UICONTROL Document of Record Path]** Hiermee geeft u de naam op van het bestand Document of Record en het pad van het bestand ten opzichte van de laadbewerking. De `/addresschange/DoR.pdf` pad maakt een map met de naam `addresschange` ten opzichte van de lading en plaatst het `DoR.pdf` ten opzichte van de lading. U kunt ook alleen `DoR.pdf` alleen Document of Record opslaan zonder een mappenhiërarchie te maken. Als de workflow is gemarkeerd voor externe gegevensopslag, gebruikt u de optie Variabele en selecteert u de variabele in de lijst met variabelen die beschikbaar zijn voor het workflowmodel.

## Revalidatie op de server in adaptieve vorm {#server-side-revalidation-in-adaptive-form}

In elk onlinesysteem voor gegevensvastlegging plaatsen ontwikkelaars doorgaans bepaalde JavaScript-validaties op de client om een aantal bedrijfsregels af te dwingen. Maar in moderne browsers, moeten de eindgebruikers die bevestigingen omzeilen en manueel bijdragen gebruikend diverse technieken, zoals Browser van het Web DevTools Console indienen. Dergelijke technieken zijn ook geldig voor adaptieve formulieren. Een formulierontwikkelaar kan verschillende validatielogboeken maken, maar technisch kunnen eindgebruikers die validatielogboeken omzeilen en ongeldige gegevens naar de server verzenden. Ongeldige gegevens zouden de bedrijfsregels overtreden die een auteur van formulieren heeft afgedwongen.

Met de functie voor opnieuw valideren aan de serverzijde kunt u ook de validaties uitvoeren die door de auteur van een adaptief formulier zijn verstrekt tijdens het ontwerpen van een adaptief formulier op de server. Hierdoor wordt voorkomen dat bij het verzenden van gegevens en bij het valideren van formulieren inbreuk wordt gemaakt op de bedrijfsregels.

### Wat moet u op de server valideren? {#what-to-validate-on-server-br}

Alle OOTB-veldvalidaties (out-of-box) van een adaptief formulier die opnieuw worden uitgevoerd op de server zijn:

* Vereist
* Clausule voor validatie
* Validatie-expressie

### Validatie op de server inschakelen {#enabling-server-side-validation-br}

Gebruik de **Revalidate op server** onder Adaptieve formuliercontainer in de zijbalk om validatie aan de serverzijde voor het huidige formulier in of uit te schakelen.

![Validatie op de server inschakelen](assets/revalidate-on-server.png)

Validatie op de server inschakelen

Als de eindgebruiker deze validaties overslaat en de formulieren verzendt, wordt de validatie opnieuw uitgevoerd door de server. Als de validatie op het servereinde mislukt, wordt de verzendtransactie gestopt. De eindgebruiker krijgt het oorspronkelijke formulier opnieuw te zien. De vastgelegde gegevens en verzonden gegevens worden als een fout aan de gebruiker gepresenteerd.

>[!NOTE]
Servervalidatie valideert het formuliermodel. Het wordt aanbevolen een aparte clientbibliotheek voor validaties te maken en deze niet te mengen met andere elementen, zoals HTML styling en DOM-bewerking in dezelfde clientbibliotheek.

### Aangepaste functies ondersteunen in validatie-expressies {#supporting-custom-functions-in-validation-expressions-br}

Als er soms complexe validatieregels zijn, bevindt het exacte validatiescript zich in aangepaste functies en roept de auteur deze aangepaste functies aan vanuit de expressie voor veldvalidatie. Als u deze aangepaste functiebibliotheek bekend en beschikbaar wilt maken tijdens het uitvoeren van validaties aan de serverzijde, kan de auteur van het formulier de naam van AEM clientbibliotheek configureren onder de **Basis** tabblad Adaptieve formuliercontainereigenschappen, zoals hieronder weergegeven.

![Aangepaste functies ondersteunen in validatie-expressies](assets/clientlib-cat.png)

Aangepaste functies ondersteunen in validatie-expressies

Auteurs kunnen de aangepaste JavaScript-bibliotheek per adaptief formulier configureren. Houd in de bibliotheek alleen de herbruikbare functies die afhankelijk zijn van bibliotheken van derden jquery en underscore.js.

## Foutafhandeling bij verzendactie {#error-handling-on-submit-action}

Als deel van de veiligheid van de Experience Manager en het verharden richtlijnen, vorm de pagina&#39;s van de douanefout zoals 404.jsp en 500.jsp. Deze handlers worden aangeroepen wanneer een formulier 404- of 500-fouten worden verzonden. De handlers worden ook geroepen wanneer deze foutencodes op de Publish knoop worden teweeggebracht.

Zie voor meer informatie [Pagina&#39;s aanpassen die worden weergegeven door de fouthandler](/help/sites-developing/customizing-errorhandler-pages.md).
