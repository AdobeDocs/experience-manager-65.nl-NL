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
source-git-commit: c74d9e86727f2deda62b8d1eb105b28ef4b6d184
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---


# De handeling Verzenden configureren{#configuring-the-submit-action}

## Inleiding om acties {#introduction-to-submit-actions} te verzenden

Een verzendactie wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. U kunt de verzendactie configureren op het aangepaste formulier. Adaptieve formulieren bevatten een paar elementen uit het vak Acties verzenden. U kunt de standaardverzendacties kopiëren en uitbreiden om uw eigen verzendactie te maken. Op basis van uw vereisten kunt u echter uw eigen verzendactie schrijven en registreren om gegevens in het verzonden formulier te verwerken. De verzendactie kan [synchrone of asynchrone verzending](../../forms/using/asynchronous-submissions-adaptive-forms.md) gebruiken.

U kunt een verzendactie configureren in de sectie **Verzending** van de eigenschappen van de container van de adaptieve vorm, in de zijbalk.

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
>Zorg ervoor dat [AEM_Installation_Directory]\crx-quickstart\temp\datamanager\ASM folder
>bestaat. De map is vereist om bijlagen tijdelijk op te slaan. Als de map niet bestaat, maakt u deze.

>[!CAUTION]
>
>Als u [een formuliersjabloon, formuliergegevensmodel of op schema gebaseerd adaptief formulier met XML- of JSON-gegevensklacht vooraf invult in een schema (XML-schema, JSON-schema, formuliersjabloon of formuliergegevensmodel) dat geen &lt;afData>-, &lt;afBoundData>- en &lt;/afUnboundData>-tags bevat, dan de gegevens van niet-omsloten velden (Niet-omsloten) Gemengde velden zijn adaptieve formuliervelden zonder [bindref](../../forms/using/prepopulate-adaptive-form-fields.md) eigenschap) van het adaptieve formulier dat verloren gaat.](../../forms/using/prepopulate-adaptive-form-fields.md)

U kunt een aangepaste verzendactie schrijven voor aangepaste formulieren om aan uw gebruiksscenario te voldoen. Zie [Aangepaste handeling Verzenden schrijven voor adaptieve formulieren](../../forms/using/custom-submit-action-form.md) voor meer informatie.

## Verzenden naar REST-eindpunt {#submit-to-rest-endpoint}

Met de optie **Verzenden naar REST-eindpunt** worden de gegevens die in het formulier zijn ingevuld, doorgegeven aan een geconfigureerde bevestigingspagina als onderdeel van het HTTP-verzoek. U kunt de naam toevoegen van de velden die u wilt aanvragen. De indeling van het verzoek is:

`{fieldName}={request parameter name}`

Zoals u in de onderstaande afbeelding ziet, worden `param1` en `param2` doorgegeven als parameters met waarden die zijn gekopieerd uit de velden **textbox** en **numericbox** voor de volgende actie.

U kunt **verzoek van de POST ook toelaten** en een URL verstrekken om het verzoek te posten. Als u gegevens wilt verzenden naar de AEM server waarop het formulier zich bevindt, gebruikt u een relatief pad dat overeenkomt met het hoofdpad van de AEM server. Bijvoorbeeld /content/forms/af/SampleForm.html. Gebruik absoluut pad om gegevens naar een andere server te verzenden.

![Rest Endpoint-verzendhandeling configureren](assets/action-config.png)

Rest Endpoint-verzendhandeling configureren

>[!NOTE]
Als u de velden als parameters in een REST-URL wilt doorgeven, moeten alle velden verschillende elementnamen hebben, zelfs als de velden op verschillende deelvensters zijn geplaatst.

### Gegevens naar een bron of een extern eindpunt voor de rusttijd verzenden  {#post-submitted-data-to-a-resource-or-external-rest-end-point-nbsp}

Gebruik de handeling **Verzenden naar REST Endpoint** om de verzonden gegevens naar een rest-URL te verzenden. De URL kan van een interne (de server waarop het formulier wordt gegenereerd) of van een externe server zijn.

Om gegevens aan een interne server te posten, verstrek weg van het middel. De gegevens worden gepost de weg van het middel. Bijvoorbeeld /content/restEndPoint. Voor dergelijke postverzoeken wordt de authenticatieinformatie van het verzendverzoek gebruikt.

Geef een URL op om gegevens naar een externe server te posten. De indeling van de URL is https://host:port/path_to_rest_end_point. Zorg ervoor dat u de weg vormt om het verzoek van de POST anoniem te behandelen.

![Toewijzing voor veldwaarden die zijn doorgegeven als parameters voor de pagina Bedankt](assets/post-enabled-actionconfig.png)

In het bovenstaande voorbeeld wordt door de gebruiker ingevoerde informatie in `textbox` vastgelegd met parameter `param1`. De syntaxis voor het posten van gegevens die zijn vastgelegd met `param1` is:

`String data=request.getParameter("param1");`

De parameters die u gebruikt voor het posten van XML-gegevens en -bijlagen zijn `dataXml` en `attachments`.

U gebruikt deze twee parameters in uw script bijvoorbeeld om gegevens te parseren op een eindpunt in de rest. U gebruikt de volgende syntaxis om de gegevens op te slaan en te ontleden:

`String data=request.getParameter("dataXml");`
`String att=request.getParameter("attachments");`

In dit voorbeeld slaat `data` de XML-gegevens op en `att` slaat bijlagegegevens op.

## E-mail {#send-email} verzenden

Met de verzendactie **E-mail verzenden** wordt een e-mail verzonden naar een of meer ontvangers wanneer het formulier met succes is verzonden. Het gegenereerde e-mailbericht kan formuliergegevens in een vooraf gedefinieerde indeling bevatten.

>[!NOTE]
Alle formuliervelden moeten verschillende elementnamen hebben, zelfs als ze op verschillende deelvensters zijn geplaatst), om formuliergegevens op te nemen in een e-mailbericht.

## PDF verzenden via e-mail {#send-pdf-via-email}

Met de handeling **PDF verzenden via e-mail** wordt een e-mail met een PDF met formuliergegevens verzonden naar een of meer ontvangers wanneer het formulier is verzonden.

>[!NOTE]
Deze verzendactie is beschikbaar voor op XFA gebaseerde adaptieve formulieren en op XSD gebaseerde aanpassingsformulieren die de sjabloon Document of Record hebben.

## Een formulierwerkstroom aanroepen {#invoke-a-forms-workflow}

Met de optie **Verzenden naar Forms-workflow** worden een gegevens-xml en bestandsbijlagen (indien aanwezig) naar een bestaande Adobe-LiveCycle of AEM Forms verzonden tijdens een JEE-proces.

Zie [Formulierwerkstromen verzenden en de formuliergegevens verwerken met werkstromen](../../forms/using/submit-form-data-livecycle-process.md) voor informatie over het configureren van de verzendactie Verzenden naar formulieren.

## Verzenden met gebruik van formuliergegevensmodel {#submit-using-form-data-model}

Met de handeling **Verzenden met gebruik van formuliergegevensmodel** wordt de verzonden verzonden adaptieve formuliergegevens voor het opgegeven gegevensmodelobject in een formuliergegevensmodel naar de gegevensbron geschreven. Wanneer het vormen van voorlegt actie, kunt u een voorwerp van het gegevensmodel kiezen waarvan voorgelegde gegevens u terug naar zijn gegevensbron wilt schrijven.

Daarnaast kunt u een formulierbijlage verzenden met behulp van een formuliergegevensmodel en een Document of Record (DoR) naar de gegevensbron.

Zie [AEM Forms Data Integration](../../forms/using/data-integration.md) voor informatie over het formuliergegevensmodel.

## Forms Portal verzendt handeling {#forms-portal-submit-action}

Met de optie **Forms Portal Handeling verzenden** worden formuliergegevens beschikbaar via een AEM Forms-portal.

Zie [Concepten en verzendingscomponent](../../forms/using/draft-submission-component.md) voor meer informatie over de Forms Portal en de verzendactie.

## Een AEM-workflow {#invoke-an-aem-workflow} aanroepen

Met de **Invoke an AEM Workflow** submit-handeling wordt een adaptief formulier gekoppeld aan een AEM workflow. Wanneer een formulier wordt verzonden, wordt de bijbehorende workflow automatisch gestart op het verwerkingsknooppunt. Bovendien worden het gegevensbestand, de bijlagen, en het document van Verslag, indien van toepassing, bij de ladingsplaats van het werkschema geplaatst.

Voordat u de **Invoke an AEM Workflow** submit action, [configure de AEM DS settings](../../forms/using/configuring-the-processing-server-url-.md). Voor informatie over het creëren van een AEMWerkschema, zie [Formulier-centric werkschema&#39;s op OSGi](../../forms/using/aem-forms-workflow.md).

## Revalidatie op de server in adaptieve vorm {#server-side-revalidation-in-adaptive-form}

In elk onlinesysteem voor gegevensvastlegging plaatsen ontwikkelaars doorgaans bepaalde JavaScript-validaties op de client om een aantal bedrijfsregels af te dwingen. Maar in moderne browsers, moeten de eindgebruikers die bevestigingen omzeilen en manueel bijdragen gebruikend diverse technieken, zoals Browser van het Web DevTools Console indienen. Dergelijke technieken zijn ook geldig voor adaptieve formulieren. Een formulierontwikkelaar kan verschillende validatielogboeken maken, maar technisch kunnen eindgebruikers die validatielogboeken omzeilen en ongeldige gegevens naar de server verzenden. Ongeldige gegevens zouden de bedrijfsregels overtreden die een auteur van formulieren heeft afgedwongen.

Met de functie voor opnieuw valideren aan de serverzijde kunt u ook de validaties uitvoeren die door de auteur van een adaptief formulier zijn verstrekt tijdens het ontwerpen van een adaptief formulier op de server. Hierdoor wordt voorkomen dat bij het verzenden van gegevens en bij het valideren van formulieren inbreuk wordt gemaakt op de bedrijfsregels.

### Wat moet u op de server valideren? {#what-to-validate-on-server-br}

Alle OOTB-veldvalidaties (out-of-box) van een adaptief formulier die opnieuw op de server worden uitgevoerd, zijn:

* Vereist
* Clausule voor validatie
* Validatie-expressie

### Servervalidatie {#enabling-server-side-validation-br} inschakelen

Gebruik **Revalidate op server** onder Adaptieve formuliercontainer in de zijbalk om validatie op de server in of uit te schakelen voor het huidige formulier.

![Validatie op de server inschakelen](assets/revalidate-on-server.png)

Validatie op de server inschakelen

Als de eindgebruiker deze validaties overslaat en de formulieren verzendt, wordt de validatie opnieuw uitgevoerd door de server. Als de validatie op het servereinde mislukt, wordt de verzendtransactie gestopt. De eindgebruiker krijgt het oorspronkelijke formulier opnieuw te zien. De vastgelegde gegevens en verzonden gegevens worden als een fout aan de gebruiker gepresenteerd.

### Aangepaste functies ondersteunen in validatie-expressies {#supporting-custom-functions-in-validation-expressions-br}

In het geval van **complexe validatieregels** bevindt het exacte validatiescript zich soms in aangepaste functies en de auteur roept deze aangepaste functies aan vanuit de expressie voor veldvalidatie. Als u deze aangepaste functiebibliotheek bekend en beschikbaar wilt maken tijdens het uitvoeren van validaties op de server, kan de auteur van het formulier de naam van AEM clientbibliotheek configureren onder het tabblad **Standaard** van Adaptief formuliercontainereigenschappen, zoals hieronder wordt weergegeven.

![Aangepaste functies ondersteunen in validatie-expressies](assets/clientlib-cat.png)

Aangepaste functies ondersteunen in validatie-expressies

Auteurs kunnen de aangepaste JavaScript-bibliotheek per adaptief formulier configureren. Houd in de bibliotheek alleen de herbruikbare functies die afhankelijk zijn van bibliotheken van derden jquery en underscore.js.

## Foutafhandeling bij verzendactie {#error-handling-on-submit-action}

Als deel van AEM veiligheid en het verharden richtlijnen, vorm de pagina&#39;s van de douanefout zoals 404.jsp en 500.jsp. Deze handlers worden aangeroepen wanneer een formulier 404- of 500-fouten worden verzonden. De handlers worden ook geroepen wanneer deze foutencodes op de Publish knoop worden teweeggebracht.

Zie [Pagina&#39;s aanpassen die worden weergegeven door de fouthandler](/help/sites-developing/customizing-errorhandler-pages.md) voor meer informatie.
