---
title: De handeling Verzenden configureren
seo-title: De handeling Verzenden configureren
description: Met AEM Forms kunt u een verzendactie configureren om te definiëren hoe een adaptief formulier na verzending wordt verwerkt. U kunt ingebouwde verzendacties gebruiken of zelf schrijven.
seo-description: Met AEM Forms kunt u een verzendactie configureren om te definiëren hoe een adaptief formulier na verzending wordt verwerkt. U kunt ingebouwde verzendacties gebruiken of zelf schrijven.
uuid: 4368d648-88ea-4f84-a051-46296a1a084e
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
discoiquuid: 9d8d7044-ffce-4ab4-9543-a2d2f9da31e3
docset: aem65
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# De handeling Verzenden configureren{#configuring-the-submit-action}

## Inleiding om acties te verzenden {#introduction-to-submit-actions}

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. U kunt de verzendactie configureren op het aangepaste formulier. Adaptieve formulieren bevatten een paar elementen uit het vak Acties verzenden. U kunt de standaardverzendacties kopiëren en uitbreiden om uw eigen verzendactie te maken. Op basis van uw vereisten kunt u echter uw eigen verzendactie schrijven en registreren om gegevens in het verzonden formulier te verwerken. De verzendactie kan [synchrone of asynchrone verzending](../../forms/using/asynchronous-submissions-adaptive-forms.md)gebruiken.

U kunt een verzendactie configureren in de sectie **Verzending** van de eigenschappen van de container van adaptieve formulieren, in de zijbalk.

![Verzendhandeling configureren](assets/thank-you-setting.png)

Verzendhandeling configureren

De standaardverzendacties die beschikbaar zijn in aangepaste formulieren zijn:

* Verzenden naar REST-eindpunt
* E-mail verzenden
* PDF verzenden via e-mail
* Een formulierworkflow aanroepen
* Verzenden met gebruik van formuliergegevensmodel
* Formulierportal Handeling verzenden
* AEM-workflow aanroepen

>[!NOTE]
>
>PDF verzenden via e-mail verzenden is alleen van toepassing op adaptieve formulieren die XFA-sjabloon gebruiken als formuliermodel.

>[!NOTE]
>
>Zorg ervoor dat [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>bestaat. De map is vereist om bijlagen tijdelijk op te slaan. Als de map niet bestaat, maakt u deze.

>[!CAUTION]
>
>Als u een formuliersjabloon, formuliergegevensmodel of op schema gebaseerd adaptief formulier met XML- of JSON-gegevensklacht [vooraf instelt](../../forms/using/prepopulate-adaptive-form-fields.md) in een schema (XML-schema, JSON-schema, formuliersjabloon of formuliergegevensmodel) dat geen &lt;afData>-, &lt;afBoundData>- en &lt;/afUnboundData>-tags bevat, worden de gegevens van niet-gebonden velden aangepast velden zonder [bindref](../../forms/using/prepopulate-adaptive-form-fields.md) eigenschap) van het adaptieve formulier verloren gaan.

U kunt een aangepaste verzendactie schrijven voor aangepaste formulieren om aan uw gebruiksscenario te voldoen. Zie Aangepaste verzendactie [schrijven voor adaptieve formulieren](../../forms/using/custom-submit-action-form.md)voor meer informatie.

## Verzenden naar REST-eindpunt {#submit-to-rest-endpoint}

Met de optie **Verzenden naar REST-eindpunt** worden de gegevens die in het formulier zijn ingevuld, doorgegeven aan een geconfigureerde bevestigingspagina als onderdeel van de HTTP GET-aanvraag. U kunt de naam toevoegen van de velden die u wilt aanvragen. De indeling van het verzoek is:

`{fieldName}={request parameter name}`

Zoals in de onderstaande afbeelding wordt getoond, `param1` en `param2` worden doorgegeven als parameters met waarden die zijn gekopieerd uit de velden **textbox** en **numeriek** vak voor de volgende actie.

U kunt POST-aanvraag **ook** inschakelen en een URL opgeven om de aanvraag te posten. Als u gegevens wilt verzenden naar de AEM-server die als host fungeert voor het formulier, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM-server. Bijvoorbeeld /content/forms/af/SampleForm.html. Gebruik absoluut pad om gegevens naar een andere server te verzenden.

![Rest Endpoint-verzendhandeling configureren](assets/action-config.png)

Rest Endpoint-verzendhandeling configureren

>[!NOTE]
Als u de velden als parameters in een REST-URL wilt doorgeven, moeten alle velden verschillende elementnamen hebben, zelfs als de velden op verschillende deelvensters zijn geplaatst.

### Gegevens naar een bron of een extern eindpunt voor de rusttijd verzenden {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Gebruik de actie **Verzenden naar REST Endpoint** om de verzonden gegevens naar een rest-URL te posten. De URL kan van een interne (de server waarop het formulier wordt gegenereerd) of van een externe server zijn.

Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld /content/restEndPoint. Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

Geef een URL op om gegevens naar een externe server te posten. De indeling van de URL is https://host:port/path_to_rest_end_point. Zorg ervoor dat u de weg vormt om het POST- verzoek anoniem te behandelen.

![Toewijzing voor veldwaarden die zijn doorgegeven als parameters voor de pagina Bedankt](assets/post-enabled-actionconfig.png)

In het bovenstaande voorbeeld `textbox` wordt door de gebruiker ingevoerde informatie vastgelegd met behulp van parameter `param1`. De syntaxis voor het posten van gegevens die zijn vastgelegd met `param1` is:

`String data=request.getParameter("param1");`

Ook parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen, zijn `dataXml` en `attachments`.

U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

In dit voorbeeld worden de XML-gegevens `data` opgeslagen en worden de bijlagegegevens `att` opgeslagen.

## E-mail verzenden {#send-email}

Met de handeling E-mail **** verzenden wordt een e-mail naar een of meer ontvangers verzonden wanneer het formulier met succes is verzonden. Het gegenereerde e-mailbericht kan formuliergegevens in een vooraf gedefinieerde indeling bevatten.

>[!NOTE]
Alle formuliervelden moeten verschillende elementnamen hebben, zelfs als ze op verschillende deelvensters zijn geplaatst), om formuliergegevens op te nemen in een e-mailbericht.

## PDF verzenden via e-mail {#send-pdf-via-email}

Met de handeling PDF **verzenden via e-mail** verzendt u een e-mail met een PDF met formuliergegevens naar een of meer ontvangers wanneer het formulier is verzonden.

>[!NOTE]
Deze verzendactie is beschikbaar voor op XFA gebaseerde adaptieve formulieren en op XSD gebaseerde aanpassingsformulieren die de sjabloon Document of Record hebben.

## Een formulierwerkstroom aanroepen {#invoke-a-forms-workflow}

Met de optie **Verzenden naar Forms-workflow** verzendt u een gegevens-xml en eventuele bestandsbijlagen naar een bestaand Adobe LiveCycle- of AEM-formulier voor JEE-proces.

Zie [Formuliergegevens verzenden en verwerken met behulp van formulierwerkstromen](../../forms/using/submit-form-data-livecycle-process.md)voor informatie over het configureren van de verzendactie Verzenden naar formulierwerkstroom.

## Verzenden met gebruik van formuliergegevensmodel {#submit-using-form-data-model}

Met de handeling **Verzenden met gebruik van het formuliergegevensmodel** schrijft u verzonden adaptieve formuliergegevens voor het opgegeven gegevensmodelobject in een formuliergegevensmodel naar de gegevensbron ervan. Wanneer het vormen van voorlegt actie, kunt u een voorwerp van het gegevensmodel kiezen waarvan voorgelegde gegevens u terug naar zijn gegevensbron wilt schrijven.

Daarnaast kunt u een formulierbijlage verzenden met behulp van een formuliergegevensmodel en een Document of Record (DoR) naar de gegevensbron.

Voor informatie over het model van vormgegevens, zie de Integratie [van Gegevens van](../../forms/using/data-integration.md)Vormen AEM.

## Formulierportal Handeling verzenden {#forms-portal-submit-action}

Met de optie Handeling **verzenden voor** Forms Portal worden formuliergegevens beschikbaar via een AEM Forms-portal.

Zie [Concepten en verzendingen voor meer informatie over de Forms Portal en de verzendactie](../../forms/using/draft-submission-component.md).

## AEM-workflow aanroepen {#invoke-an-aem-workflow}

De **actie Een AEM-workflow** verzenden associeert een adaptief formulier met een AEM-workflow. Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart op het verwerkingsknooppunt. Bovendien worden het gegevensbestand, de bijlagen, en het document van Verslag, indien van toepassing, bij de ladingsplaats van het werkschema geplaatst.

Voordat u de handeling Een AEM-workflow **aanroepen gebruikt,** configureert u de AEM DS-instellingen [](../../forms/using/configuring-the-processing-server-url-.md). Voor informatie over het creëren van een AEM- Werkschema, zie [vorm-centric werkschema&#39;s op OSGi](../../forms/using/aem-forms-workflow.md).

## Revalidatie op de server in adaptieve vorm {#server-side-revalidation-in-adaptive-form}

Doorgaans plaatsen ontwikkelaars in elk onlinesysteem voor het vastleggen van gegevens enkele JavaScript-validaties aan de clientzijde om een aantal bedrijfsregels af te dwingen. Maar in moderne browsers, moeten de eindgebruikers die bevestigingen omzeilen en manueel bijdragen gebruikend diverse technieken, zoals Browser van het Web DevTools Console indienen. Dergelijke technieken zijn ook geldig voor adaptieve formulieren. Een formulierontwikkelaar kan verschillende validatielogboeken maken, maar technisch kunnen eindgebruikers die validatielogboeken omzeilen en ongeldige gegevens naar de server verzenden. Ongeldige gegevens zouden de bedrijfsregels overtreden die een auteur van formulieren heeft afgedwongen.

Met de functie voor opnieuw valideren aan de serverzijde kunt u ook de validaties uitvoeren die door de auteur van een adaptief formulier zijn verstrekt tijdens het ontwerpen van een adaptief formulier op de server. Hierdoor wordt voorkomen dat bij het verzenden van gegevens en bij het valideren van formulieren inbreuk wordt gemaakt op de bedrijfsregels.

### Wat moet u op de server valideren? {#what-to-validate-on-server-br}

Alle OOTB-veldvalidaties (out-of-box) van een adaptief formulier die opnieuw op de server worden uitgevoerd, zijn:

* Vereist
* Clausule voor validatie
* Validatie-expressie

### Validatie op de server inschakelen {#enabling-server-side-validation-br}

Gebruik Revalidate **op de server** onder Adaptieve formuliercontainer in de zijbalk om validatie op de server in of uit te schakelen voor het huidige formulier.

![Validatie op de server inschakelen](assets/revalidate-on-server.png)

Validatie op de server inschakelen

Als de eindgebruiker deze validaties overslaat en de formulieren verzendt, wordt de validatie opnieuw uitgevoerd door de server. Als de validatie op het servereinde mislukt, wordt de verzendtransactie gestopt. De eindgebruiker krijgt het oorspronkelijke formulier opnieuw te zien. De vastgelegde gegevens en verzonden gegevens worden als een fout aan de gebruiker gepresenteerd.

### Aangepaste functies ondersteunen in validatie-expressies {#supporting-custom-functions-in-validation-expressions-br}

In het geval van **complexe validatieregels** bevindt het exacte validatiescript zich soms in aangepaste functies en de auteur roept deze aangepaste functies aan vanuit de expressie voor veldvalidatie. Om deze aangepaste functiebibliotheek bekend te maken en beschikbaar te maken tijdens het uitvoeren van servervalidaties, kan de auteur van het formulier de naam van de AEM-clientbibliotheek configureren onder het tabblad **Standaard** van de adaptieve eigenschappen van de formuliercontainer, zoals hieronder wordt weergegeven.

![Aangepaste functies ondersteunen in validatie-expressies](assets/clientlib-cat.png)

Aangepaste functies ondersteunen in validatie-expressies

Auteurs kunnen aangepaste javascript-bibliotheek configureren per adaptief formulier. Houd in de bibliotheek alleen de herbruikbare functies die afhankelijk zijn van bibliotheken van derden jquery en underscore.js.

## Foutafhandeling bij verzendactie {#error-handling-on-submit-action}

Als onderdeel van de beveiligingsrichtlijnen en de richtlijnen voor het verharden van AEM, configureert u aangepaste foutpagina&#39;s zoals 404.jsp en 500.jsp. Deze handlers worden aangeroepen wanneer een formulier 404- of 500-fouten worden verzonden. De handlers worden ook geroepen wanneer deze foutencodes op de Publish knoop worden teweeggebracht.

Voor meer informatie, zie het [Aanpassen van Pagina&#39;s die door de Handler](/help/sites-developing/customizing-errorhandler-pages.md)van de Fout worden getoond.
