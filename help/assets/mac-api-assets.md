---
title: '[!DNL Assets] HTTP-API.'
description: Digitale elementen maken, lezen, bijwerken, verwijderen en beheren met de HTTP API in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: c3ae4447581d946554d792c68d31b47a6b67d5df
workflow-type: tm+mt
source-wordcount: '1715'
ht-degree: 0%

---


# [!DNL Assets] HTTP-API  {#assets-http-api}

## Overzicht {#overview}

Met de HTTP-API [!DNL Assets] kunt u CRUD-bewerkingen (read-read-update-delete) maken op digitale elementen, waaronder metagegevens, uitvoeringen en opmerkingen, en op gestructureerde inhoud met behulp van [!DNL Experience Manager] Inhoudsfragmenten. Deze wordt weergegeven op `/api/assets` en wordt geïmplementeerd als REST API. Het omvat [steun voor Inhoudsfragmenten](/help/assets/assets-api-content-fragments.md).

Toegang krijgen tot de API:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json`.
1. Volg de [!DNL Assets] de dienstverbinding die aan `https://[hostname]:[server]/api/assets.json` leidt.

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

Na [!UICONTROL Off Time] zijn een middel en zijn vertoningen niet beschikbaar via de [!DNL Assets] Webinterface en door HTTP API. De API retourneert een foutbericht van 404 als [!UICONTROL On Time] in de toekomst is of als [!UICONTROL Off Time] in het verleden is.

>[!CAUTION]
>
>[HTTP API werkt de meta-](#update-asset-metadata) eigenschappen in  `jcr` namespace bij. Nochtans, werkt het gebruikersinterface van de Experience Manager de meta-gegevenseigenschappen in `dc` namespace bij.

## Contentfragmenten {#content-fragments}

Een [inhoudsfragment](/help/assets/content-fragments/content-fragments.md) is een speciaal type element. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn met `standard` elementen (zoals afbeeldingen of documenten), zijn enkele aanvullende regels van toepassing op de afhandeling van inhoudsfragmenten.

Zie [Ondersteuning van inhoudsfragmenten in de HTTP API](/help/assets/assets-api-content-fragments.md) van de Experience Manager Assets voor meer informatie.

## Gegevensmodel {#data-model}

De [!DNL Assets] HTTP API stelt twee belangrijke elementen, omslagen en activa (voor standaardactiva) bloot.

Bovendien, stelt het meer gedetailleerde elementen voor de modellen van douanegegevens bloot die gestructureerde inhoud in de Fragments van de Inhoud beschrijven. Zie [Gegevensmodellen van inhoudsfragmenten](/help/assets/assets-api-content-fragments.md#content-fragments) voor meer informatie.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen in traditionele bestandssystemen. Het zijn containers voor andere mappen of berichten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een map zijn onderliggende elementen, mappen en elementen.

**Eigenschappen**:

* `name` is de naam van de map. Dit is het zelfde als het laatste segment in de weg URL zonder de uitbreiding.
* `title` is een optionele titel van de map die in plaats van de naam kan worden weergegeven.

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. Het voorvoegsel `jcr` van `jcr:title`, `jcr:description` en `jcr:language` worden vervangen door voorvoegsel `dc`. Daarom bevatten `dc:title` en `dc:description` in de geretourneerde JSON de waarden van respectievelijk `jcr:title` en `jcr:description`.

**** LinksMappen maken drie koppelingen zichtbaar:

* `self`: Koppeling naar zichzelf.
* `parent`: Koppeling naar de bovenliggende map.
* `thumbnail`: (Optioneel) koppeling naar een miniatuurafbeelding van een map.

### Assets {#assets}

In Experience Manager bevat een element de volgende elementen:

* De eigenschappen en metagegevens van het element.
* Meerdere uitvoeringen, zoals de oorspronkelijke uitvoering (het oorspronkelijk geüploade element), een miniatuur en verschillende andere uitvoeringen. Extra uitvoeringen kunnen afbeeldingen van verschillende grootten, videocoderingen of pagina&#39;s uit PDF- of [!DNL Adobe InDesign]-bestanden zijn.
* Optionele opmerkingen.

Zie [Ondersteuning van inhoudsfragmenten in HTTP API](/help/assets/assets-api-content-fragments.md#content-fragments) voor informatie over elementen in inhoudsfragmenten.

In [!DNL Experience Manager] heeft een map de volgende componenten:

* Entiteiten: De onderliggende elementen van activa zijn de uitvoeringen.
* Eigenschappen.
* Koppelingen.

De [!DNL Assets] HTTP-API bevat de volgende functies:

* [Haal een mappenlijst](#retrieve-a-folder-listing) op.
* [Maak een map](#create-a-folder).
* [Maak een element](#create-an-asset).
* [Binair](#update-asset-binary) element bijwerken.
* [Metagegevens](#update-asset-metadata) van elementen bijwerken.
* [Een elementuitvoering](#create-an-asset-rendition) maken.
* [Een elementuitvoering](#update-an-asset-rendition) bijwerken.
* [Maak een middelenopmerking](#create-an-asset-comment).
* [Kopieer een map of element](#copy-a-folder-or-asset).
* [Een map of element](#move-a-folder-or-asset) verplaatsen.
* [Een map, element of uitvoering](#delete-a-folder-asset-or-rendition) verwijderen.

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notatie weggelaten. In feite correleert de notatie wel met [Resty](https://github.com/micha/resty). Dit is een scriptwrapper voor `cURL`.

**Vereisten**

* Ga naar `https://[aem_server]:[port]/system/console/configMgr`.
* Ga naar **[!UICONTROL Adobe Granite CSRF Filter]**.
* Zorg ervoor dat de eigenschap **[!UICONTROL Filter Methods]** het volgende bevat: `POST`, `PUT`, `DELETE`.

## Een map ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**:  `GET /api/assets/myFolder.json`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - succes.
* 404 - NIET GEVONDEN - map bestaat niet of is niet toegankelijk.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

**Reactie**: De klasse van de geretourneerde entiteit is een middel of een map. De eigenschappen van ingesloten entiteiten vormen een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige vertegenwoordiging van de entiteit te verkrijgen, zouden de cliënten de inhoud van URL moeten terugwinnen die door de verbinding met een `rel` van `self` wordt gericht.

## Een map {#create-a-folder} maken

Hiermee maakt u een nieuwe `sling`: `OrderedFolder` op het opgegeven pad. Als een `*` in plaats van een knoopnaam wordt verstrekt, gebruikt servlet de parameternaam als knooppuntnaam. Gegevens die worden geaccepteerd als aanvraaggegevens zijn ofwel een Sirene-representatie van de nieuwe map of een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form`- `data`. Dit is handig als u een map rechtstreeks vanuit een HTML-formulier wilt maken. Bovendien kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

Een API-aanroep mislukt met een `500`-antwoordcode als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Een aanroep retourneert een antwoordcode `409` als de map al bestaat.

**Parameters**:  `name` is de mapnaam.

**Verzoek**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - over succesvol maken.
* 409 - CONFLICT - als de map al bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Elementen {#create-an-asset} maken

Plaats het opgegeven bestand op het opgegeven pad om een element te maken in de DAM-opslagplaats. Als een `*` in plaats van een knooppuntnaam wordt verstrekt, gebruikt servlet de parameternaam of de dossiernaam als knooppuntnaam.

**Parameters**: De parameters zijn  `name` voor de elementnaam en  `file` voor de bestandsverwijzing.

**Verzoek**

* `POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"`
* `POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als Asset is gemaakt.
* 409 - CONFLICT - als Activum al bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Elementbinair {#update-asset-binary} bijwerken

Hiermee werkt u de binaire waarde (uitvoering met de oorspronkelijke naam) van een element bij. Een update activeert de standaardworkflow voor middelenverwerking om deze uit te voeren, als deze is geconfigureerd.

**Verzoek**:  `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Metagegevens van element {#update-asset-metadata} bijwerken

Werkt de eigenschappen van de elementmetagegevens bij. Als u een eigenschap bijwerkt in de naamruimte `dc:`, werkt de API dezelfde eigenschap bij in de naamruimte `jcr`. De API synchroniseert de eigenschappen niet onder de twee naamruimten.

**Verzoek**:  `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"jcr:title":"My Asset"}}'`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

### Update van metagegevens synchroniseren tussen `dc` en `jcr` naamruimte {#sync-metadata-between-namespaces}

De API methode werkt de meta-gegevenseigenschappen in `jcr` namespace bij. De updates die worden uitgevoerd via de gebruikersinterface wijzigen de eigenschappen van metagegevens in de naamruimte `dc`. Als u de waarden van metagegevens wilt synchroniseren tussen `dc` en `jcr` naamruimte, kunt u een workflow maken en Experience Manager configureren om de workflow uit te voeren bij het bewerken van elementen. Gebruik een ECMA-script om de vereiste eigenschappen van metagegevens te synchroniseren. In het volgende voorbeeldscript wordt de titeltekenreeks gesynchroniseerd tussen `dc:title` en `jcr:title`.

```javascript
var workflowData = workItem.getWorkflowData();
if (workflowData.getPayloadType() == "JCR_PATH")
{
 var path = workflowData.getPayload().toString();
 var node = workflowSession.getSession().getItem(path);
 var metadataNode = node.getNode("jcr:content/metadata");
 var jcrcontentNode = node.getNode("jcr:content");
if (jcrcontentNode.hasProperty("jcr:title"))
{
 var jcrTitle = jcrcontentNode.getProperty("jcr:title");
 metadataNode.setProperty("dc:title", jcrTitle.toString());
 metadataNode.save();
}
}
```

## Een elementuitvoering maken {#create-an-asset-rendition}

Maak een nieuwe elementuitvoering voor een element. Als de naam van de parameter request niet wordt opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**: De parameters zijn  `name` voor naam van de vertoning en  `file` als dossierverwijzing.

**Verzoek**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de vertoning is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Elementuitvoering {#update-an-asset-rendition} bijwerken

Updates vervangen een elementuitvoering door de nieuwe binaire gegevens.

**Verzoek**:  `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als de vertoning correct is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Opmerking toevoegen aan een element {#create-an-asset-comment}

Hiermee maakt u een nieuwe middelenopmerking.

**Parameters**: De parameters zijn  `message` voor de berichttekst van de opmerking en  `annotationData` voor de annotatiegegevens in JSON-indeling.

**Verzoek**:  `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als Opmerking is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element kopiëren {#copy-a-folder-or-asset}

Hiermee kopieert u een map of element die beschikbaar is op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - hetzij  `infinity` hetzij  `0`. Wanneer u `0` gebruikt, worden alleen de bron en de eigenschappen ervan gekopieerd en niet de onderliggende elementen.
* `X-Overwrite` - Gebruik deze optie  `F` om te voorkomen dat een element op de bestaande bestemming wordt overschreven.

**Verzoek**:  `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element verplaatsen {#move-a-folder-or-asset}

Hiermee verplaatst u een map of element op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - hetzij  `infinity` hetzij  `0`. Wanneer u `0` gebruikt, worden alleen de bron en de eigenschappen ervan gekopieerd en niet de onderliggende elementen.
* `X-Overwrite` - Gebruik deze optie  `T` om bestaande bronnen te verwijderen of  `F` om te voorkomen dat bestaande bronnen worden overschreven.

**Verzoek**:  `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

Gebruik `/content/dam` niet in URL. Een voorbeeldopdracht voor het verplaatsen van elementen en het overschrijven van bestaande elementen is:

```shell
curl -u admin:admin -X MOVE https://[aem_server]:[port]/api/assets/source/file.png -H "X-Destination: http://[aem_server]:[port]/api/assets/destination/file.png" -H "X-Overwrite: T"
```

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map, element of uitvoering {#delete-a-folder-asset-or-rendition} verwijderen

Hiermee verwijdert u een resource (-tree) bij het opgegeven pad.

**Verzoek**

* `DELETE /api/assets/myFolder`
* `DELETE /api/assets/myFolder/myAsset.png`
* `DELETE /api/assets/myFolder/myAsset.png/renditions/original`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als de map is verwijderd.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Tips en beperkingen {#tips-best-practices-limitations}

* [HTTP API werkt de meta-](#update-asset-metadata) eigenschappen in  `jcr` namespace bij. Nochtans, werkt het gebruikersinterface van de Experience Manager de meta-gegevenseigenschappen in `dc` namespace bij.

* Asset API retourneert de volledige metagegevens niet. In de API zijn de naamruimten gecodeerd en worden deze alleen geretourneerd. Als u volledige meta-gegevens nodig hebt, dan bekijk de elementenweg `/jcr_content/metadata.json`.
