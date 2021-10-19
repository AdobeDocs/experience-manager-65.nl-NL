---
title: '[!DNL Assets] HTTP-API.'
description: Digitale middelen maken, lezen, bijwerken, verwijderen en beheren met HTTP API in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
role: Developer
feature: APIs,Assets HTTP API,Developer Tools
exl-id: 6bc10f4e-a951-49ba-9c71-f568a7f2e40d
source-git-commit: b841eb8d1820c1e42d966547280ae9743e773812
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 0%

---

# [!DNL Assets] HTTP-API {#assets-http-api}

## Overzicht {#overview}

De [!DNL Assets] Met de HTTP-API kunt u CRUD-bewerkingen (read-read-update-delete) maken voor digitale elementen, waaronder metagegevens, uitvoeringen en opmerkingen, en voor gestructureerde inhoud met gebruik van [!DNL Experience Manager] Inhoudsfragmenten. Het wordt blootgesteld bij `/api/assets` en is geïmplementeerd als REST API. Hieronder vallen [ondersteuning voor inhoudsfragmenten](/help/assets/assets-api-content-fragments.md).

Toegang krijgen tot de API:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json`.
1. Volg de [!DNL Assets] servicekoppeling die leidt naar `https://[hostname]:[server]/api/assets.json`.

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

Na de [!UICONTROL Off Time], een actief en de uitleveringen ervan niet beschikbaar zijn via de [!DNL Assets] webinterface en via de HTTP-API. De API geeft een foutbericht van 404 als de [!UICONTROL On Time] in de toekomst is of [!UICONTROL Off Time] is in het verleden.

>[!CAUTION]
>
>[HTTP API werkt de eigenschappen van metagegevens bij](#update-asset-metadata) in de `jcr` naamruimte. De gebruikersinterface van de Experience Manager werkt echter de metagegevenseigenschappen in de `dc` naamruimte.

## Contentfragmenten {#content-fragments}

A [inhoudsfragment](/help/assets/content-fragments/content-fragments.md) is een speciaal soort actief. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn tussen `standard` elementen (zoals afbeeldingen of documenten), zijn enkele aanvullende regels van toepassing op het verwerken van inhoudsfragmenten.

Zie voor meer informatie [Ondersteuning voor inhoudsfragmenten in de Experience Manager Assets HTTP API](/help/assets/assets-api-content-fragments.md).

## Gegevensmodel {#data-model}

De [!DNL Assets] HTTP API stelt twee belangrijke elementen, omslagen en activa (voor standaardactiva) bloot.

Bovendien, stelt het meer gedetailleerde elementen voor de modellen van douanegegevens bloot die gestructureerde inhoud in de Fragments van de Inhoud beschrijven. Zie [Gegevensmodellen inhoudsfragment](/help/assets/assets-api-content-fragments.md#content-fragments) voor nadere informatie.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen in traditionele bestandssystemen. Het zijn containers voor andere mappen of berichten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een map zijn onderliggende elementen, mappen en elementen.

**Eigenschappen**:

* `name` is de naam van de map. Dit is het zelfde als het laatste segment in de weg URL zonder de uitbreiding.
* `title` is een optionele titel van de map die in plaats van de naam kan worden weergegeven.

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. De `jcr` voorvoegsel van `jcr:title`, `jcr:description`, en `jcr:language` worden vervangen door `dc` voorvoegsel. Vandaar in de geretourneerde JSON, `dc:title` en `dc:description` bevatten de waarden van `jcr:title` en `jcr:description`, respectievelijk.

**Koppelingen** Mappen maken drie koppelingen zichtbaar:

* `self`: Koppeling naar zichzelf.
* `parent`: Koppeling naar de bovenliggende map.
* `thumbnail`: (Optioneel) koppeling naar een miniatuurafbeelding van een map.

### Assets {#assets}

In Experience Manager bevat een element de volgende elementen:

* De eigenschappen en metagegevens van het element.
* Meerdere uitvoeringen, zoals de oorspronkelijke uitvoering (het oorspronkelijk geüploade element), een miniatuur en verschillende andere uitvoeringen. Extra vertoningen kunnen afbeeldingen van verschillende grootten, verschillende videocoderingen, of pagina&#39;s uit PDF of zijn geëxtraheerd [!DNL Adobe InDesign] bestanden.
* Optionele opmerkingen.

Voor informatie over elementen in inhoudsfragmenten raadpleegt u [Ondersteuning voor inhoudsfragmenten in Experience Manager Assets HTTP API](/help/assets/assets-api-content-fragments.md#content-fragments).

In [!DNL Experience Manager] een map bevat de volgende componenten:

* Entiteiten: De onderliggende elementen van activa zijn de uitvoeringen.
* Eigenschappen.
* Koppelingen.

De [!DNL Assets] HTTP API bevat de volgende functies:

* [Een mappenlijst ophalen](#retrieve-a-folder-listing).
* [Een map maken](#create-a-folder).
* [Een element maken](#create-an-asset).
* [Binair element bijwerken](#update-asset-binary).
* [Metagegevens van elementen bijwerken](#update-asset-metadata).
* [Een elementuitvoering maken](#create-an-asset-rendition).
* [Een elementuitvoering bijwerken](#update-an-asset-rendition).
* [Een middelenopmerking maken](#create-an-asset-comment).
* [Een map of element kopiëren](#copy-a-folder-or-asset).
* [Een map of element verplaatsen](#move-a-folder-or-asset).
* [Een map, element of uitvoering verwijderen](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notatie weggelaten. In feite heeft de notatie een correlatie met [Herstellen](https://github.com/micha/resty) dat een scriptwrapper is voor `cURL`.

**Vereisten**

* Ga naar `https://[aem_server]:[port]/system/console/configMgr`.
* Ga naar **[!UICONTROL Adobe Granite CSRF Filter]**.
* Controleer of de eigenschap **[!UICONTROL Filter Methods]** omvat: `POST`, `PUT`, `DELETE`.

## Een mappenlijst ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**: `GET /api/assets/myFolder.json`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - succes.
* 404 - NIET GEVONDEN - map bestaat niet of is niet toegankelijk.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

**Antwoord**: De klasse van de geretourneerde entiteit is een middel of een map. De eigenschappen van ingesloten entiteiten vormen een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige vertegenwoordiging van de entiteit te verkrijgen, zouden de cliënten de inhoud van URL moeten terugwinnen waarop de verbinding met `rel` van `self`.

## Een map maken {#create-a-folder}

Hiermee maakt u een nieuwe `sling`: `OrderedFolder` op het opgegeven pad. Indien een `*` wordt verstrekt in plaats van een knoopnaam, gebruikt servlet de parameternaam als knooppuntnaam. Gegevens die worden geaccepteerd als aanvraaggegevens zijn een Sirene-weergave van de nieuwe map of een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form`- `data`Deze optie is handig als u een map rechtstreeks vanuit een HTML-formulier wilt maken. Bovendien kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

Een API-aanroep mislukt met een `500` antwoordcode als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Een vraag keert een reactiecode terug `409` als de map al bestaat.

**Parameters**: `name` is de mapnaam.

**Verzoek**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"jcr:title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"jcr:title=My Folder"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - over succesvol maken.
* 409 - CONFLICT - als de map al bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een element maken {#create-an-asset}

Plaats het opgegeven bestand op het opgegeven pad om een element te maken in de DAM-opslagplaats. Indien een `*` wordt opgegeven in plaats van een knooppuntnaam, gebruikt servlet de parameternaam of de bestandsnaam als knooppuntnaam.

**Parameters**: De parameters zijn `name` voor de elementnaam en `file` voor de bestandsverwijzing.

**Verzoek**

* `POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"`
* `POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als Asset is gemaakt.
* 409 - CONFLICT - als Activum al bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Elementbinair bijwerken {#update-asset-binary}

Hiermee werkt u de binaire waarde (uitvoering met de oorspronkelijke naam) van een element bij. Een update activeert de standaardworkflow voor middelenverwerking om deze uit te voeren, als deze is geconfigureerd.

**Verzoek**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Metagegevens van elementen bijwerken {#update-asset-metadata}

Werkt de eigenschappen van de elementmetagegevens bij. Als u een eigenschap in het dialoogvenster `dc:` naamruimte, wordt dezelfde eigenschap in de API bijgewerkt `jcr` naamruimte. De API synchroniseert de eigenschappen niet onder de twee naamruimten.

**Verzoek**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"jcr:title":"My Asset"}}'`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

### Metagegevens synchroniseren tussen `dc` en `jcr` namespace {#sync-metadata-between-namespaces}

De API-methode werkt de metagegevenseigenschappen in de `jcr` naamruimte. De updates die worden uitgevoerd via de gebruikersinterface wijzigen de eigenschappen van de metagegevens in het dialoogvenster `dc` naamruimte. De metagegevenswaarden synchroniseren tussen `dc` en `jcr` naamruimte, kunt u een workflow maken en Experience Manager configureren om de workflow uit te voeren bij het bewerken van elementen. Gebruik een ECMA-script om de vereiste eigenschappen van metagegevens te synchroniseren. In het volgende voorbeeldscript wordt de titeltekenreeks gesynchroniseerd tussen `dc:title` en `jcr:title`.

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

**Parameters**: De parameters zijn `name` voor de naam van de vertoning en `file` als bestandsverwijzing.

**Verzoek**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de vertoning is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering bijwerken {#update-an-asset-rendition}

Updates vervangen een elementuitvoering door de nieuwe binaire gegevens.

**Verzoek**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als de vertoning correct is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een opmerking toevoegen aan een element {#create-an-asset-comment}

Hiermee maakt u een nieuwe middelenopmerking.

**Parameters**: De parameters zijn `message` voor de berichttekst van de opmerking en `annotationData` voor de Annotatiegegevens in JSON-indeling.

**Verzoek**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als Opmerking is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element kopiëren {#copy-a-folder-or-asset}

Hiermee kopieert u een map of element die beschikbaar is op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - hetzij `infinity` of `0`. Gebruiken `0` kopieert alleen de bron en zijn eigenschappen en niet zijn kinderen.
* `X-Overwrite` - Gebruik `F` om te voorkomen dat een actief op de bestaande bestemming wordt overschreven.

**Verzoek**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element verplaatsen {#move-a-folder-or-asset}

Hiermee verplaatst u een map of element op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - hetzij `infinity` of `0`. Gebruiken `0` kopieert alleen de bron en zijn eigenschappen en niet zijn kinderen.
* `X-Overwrite` - Gebruik beide `T` bestaande bronnen te verwijderen of `F` om te voorkomen dat een bestaande bron wordt overschreven.

**Verzoek**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

Niet gebruiken `/content/dam` in de URL. Een voorbeeldopdracht voor het verplaatsen van elementen en het overschrijven van bestaande elementen is:

```shell
curl -u admin:admin -X MOVE https://[aem_server]:[port]/api/assets/source/file.png -H "X-Destination: http://[aem_server]:[port]/api/assets/destination/file.png" -H "X-Overwrite: T"
```

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map, element of uitvoering verwijderen {#delete-a-folder-asset-or-rendition}

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

* [HTTP API werkt de eigenschappen van metagegevens bij](#update-asset-metadata) in de `jcr` naamruimte. De gebruikersinterface van de Experience Manager werkt echter de metagegevenseigenschappen in de `dc` naamruimte.

* De HTTP-API van middelen retourneert de volledige metagegevens niet. De naamruimten zijn gecodeerd en alleen die naamruimten worden geretourneerd. Zie het middelenpad voor volledige metagegevens `/jcr_content/metadata.json`.
