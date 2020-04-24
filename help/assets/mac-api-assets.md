---
title: HTTP-API voor assets
description: Leer over de implementatie, het gegevensmodel, en de eigenschappen van Activa HTTP API. Met de HTTP-API Middelen kunt u verschillende taken uitvoeren met betrekking tot elementen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: abc4821ec3720969bf1c2fb068744c07477aca46

---


# HTTP-API voor assets {#assets-http-api}

## Overzicht {#overview}

Met de HTTP-API voor Middelen kunt u CRUD-bewerkingen (read-read-update-delete) maken voor Elementen, zoals binaire elementen, metagegevens, uitvoeringen en opmerkingen, en voor gestructureerde inhoud met behulp van AEM Content Fragments. Deze wordt weergegeven op `/api/assets` en geïmplementeerd als REST API. Dit omvat [ondersteuning voor inhoudsfragmenten](/help/assets/assets-api-content-fragments.md).

Toegang krijgen tot de API:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json`.
1. Volg de koppelingen van de service Middelen die naar `https://[hostname]:[server]/api/assets.json`leiden.

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

Na de [!UICONTROL Off Time]zijn een middel en zijn vertoningen niet beschikbaar of via de Webinterface van Middelen of door HTTP API. De API retourneert een foutbericht van 404 als de [!UICONTROL Aan-tijd] in de toekomst is of de [!UICONTROL Uit-tijd] in het verleden is.

## Contentfragmenten {#content-fragments}

Een [inhoudsfragment](/help/assets/content-fragments.md) is een speciaal type element. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn tussen `standard` elementen (zoals afbeeldingen of documenten), zijn enkele aanvullende regels van toepassing op de afhandeling van inhoudsfragmenten.

Zie Ondersteuning van [inhoudsfragmenten in de HTTP-API](/help/assets/assets-api-content-fragments.md)van AEM Assets voor meer informatie.

## Gegevensmodel {#data-model}

De HTTP-API voor middelen stelt twee belangrijke elementen, mappen en elementen beschikbaar (voor standaardelementen).

Bovendien, stelt het meer gedetailleerde elementen voor de modellen van douanegegevens bloot die gestructureerde inhoud in de Fragments van de Inhoud beschrijven. Zie Gegevensmodellen [van](/help/assets/assets-api-content-fragments.md#content-fragments) inhoudsfragmenten voor meer informatie.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen in traditionele bestandssystemen. Het zijn containers voor andere mappen of berichten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een map zijn onderliggende elementen, mappen en elementen.

**Eigenschappen**:
* `name`  — Naam van de map. Dit is hetzelfde als het laatste segment in het URL-pad zonder de extensie
* `title` — Optionele titel van de map die kan worden weergegeven in plaats van de naam ervan

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. Het `jcr` voorvoegsel van `jcr:title`, `jcr:description`en `jcr:language` worden vervangen door het `dc` voorvoegsel. Daarom in de geretourneerde JSON `dc:title` en `dc:description` bevatten deze de waarden van respectievelijk `jcr:title` en `jcr:description`.

**Er zijn drie koppelingen beschikbaar in Koppelingsmappen** :
* `self`: Koppeling naar zichzelf
* `parent`: Koppeling maken naar de bovenliggende map
* `thumbnail`: (Optioneel) koppeling naar een miniatuurafbeelding van een map

### Assets {#assets}

In AEM bevat een element de volgende elementen:

* De eigenschappen en metagegevens van het element
* Meerdere uitvoeringen, zoals de oorspronkelijke uitvoering (het oorspronkelijk geüploade element), een miniatuur en verschillende andere uitvoeringen. Extra uitvoeringen kunnen afbeeldingen van verschillende grootten, videocoderingen of uit PDF of InDesign geëxtraheerde pagina&#39;s zijn.
* Optionele opmerkingen

Zie Ondersteuning van [inhoudsfragmenten in HTTP-API](/help/assets/assets-api-content-fragments.md#content-fragments)van AEM-elementen voor informatie over elementen in inhoudsfragmenten.

In AEM heeft een map de volgende componenten:

* Entiteiten: De onderliggende elementen van Elementen zijn de uitvoeringen.
* Eigenschappen
* Koppelingen

De HTTP-API voor middelen bevat de volgende functies:

* Een mappenlijst ophalen
* Een map maken
* Een element maken
* Binair element bijwerken
* Metagegevens van elementen bijwerken
* Een elementuitvoering maken
* Een elementuitvoering bijwerken
* Een middelenopmerking maken
* Een map of element kopiëren
* Een map of element verplaatsen
* Een map, element of uitvoering verwijderen

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notatie weggelaten. In feite heeft de notatie een correlatie met [Resty](https://github.com/micha/resty) , een scriptwrapper voor `cURL`.

**Vereisten**

* Ga naar `https://[aem_server]:[port]/system/console/configMgr`.
* Navigeer naar **Adobe Granite CSRF-filter**.
* Zorg ervoor dat de eigenschap **Filter Methoden** bevat: POST, PUT, DELETE.

## Een mappenlijst ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**

```
GET /api/assets/myFolder.json
```

**Antwoordcodes**

```
200 - OK - success
404 - NOT FOUND - folder does not exist or is not accessible
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

**Antwoord**

De klasse van de geretourneerde entiteit is assets/folder.

Eigenschappen van ingesloten entiteiten zijn een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige vertegenwoordiging van de entiteit te verkrijgen, zouden de cliënten de inhoud van URL moeten terugwinnen waarnaar door de verbinding met een `rel` van `self`. wordt verwezen.

## Een map maken {#create-a-folder}

Hiermee maakt u een nieuwe `sling`: op `OrderedFolder` het opgegeven pad. Als * in plaats van een knoopnaam wordt gegeven gebruikt servlet de parameternaam als knooppuntnaam. Gegevens die worden geaccepteerd als aanvraaggegevens zijn een Sirene-weergave van de nieuwe map of een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form`- `data`, handig om een map te maken die rechtstreeks afkomstig is van een HTML-formulier. Bovendien kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

De bewerking zal mislukken met een `500` antwoordcode als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Als de map al bestaat, wordt een `409` antwoordcode geretourneerd.

**Parameters**

* `name` - Mapnaam

**Verzoek**

```
POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'
```

or

```
POST /api/assets/* -F"name=myfolder" -F"title=My Folder"
```

**Antwoordcodes**

```
201 - CREATED - on successful creation
409 - CONFLICT - if folder already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een element maken {#create-an-asset}

Maakt een DAM-element op het opgegeven pad met het opgegeven bestand. Als * wordt gegeven in plaats van een knoopnaam zal servlet de parameternaam of de dossier - naam als knooppuntnaam gebruiken.

**Parameters**

* `name` - Elementnaam
* `file` - Bestandsverwijzing

**Verzoek**

```
POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"
```

or

```
POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"
```

**Antwoordcodes**

```
201 - CREATED - if Asset has been created successfully
409 - CONFLICT - if Asset already exist
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Binair element bijwerken {#update-asset-binary}

Hiermee werkt u een binair element met elementen bij (uitvoering met de oorspronkelijke naam). Dit zal de standaardwerkschema van Activa indien gevormd teweegbrengen.

**Verzoek**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png
```

**Antwoordcodes**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Metagegevens van elementen bijwerken {#update-asset-metadata}

Werkt de metagegevenseigenschappen van het element bij. Als u een eigenschap in de `dc:` naamruimte bijwerkt, werkt de API dezelfde eigenschap in de `jcr` naamruimte bij. De API synchroniseert de eigenschappen niet onder de twee naamruimten.

**Verzoek**

```
PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'
```

**Antwoordcodes**

```
200 - OK - if Asset has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Vertoning van element maken {#create-an-asset-rendition}

Hiermee maakt u een nieuwe uitvoering van elementen voor een element. Als er geen naam voor de parameter request is opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**

* `name` - Naam van vertoning
* `file` - Bestandsverwijzing

**Verzoek**

```
POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"
```

or

```
POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"
```

**Antwoordcodes**

```
201 - CREATED - if Rendition has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Vertoning van element bijwerken {#update-an-asset-rendition}

Updates vervangen een elementuitvoering door de nieuwe binaire gegevens.

**Verzoek**

```
PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png
```

**Antwoordcodes**

```
200 - OK - if Rendition has been updated successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een Asset-opmerking maken {#create-an-asset-comment}

Hiermee maakt u een nieuwe middelenopmerking.

**Parameters**

* `message` - Bericht
* `annotationData` - Annotatiegegevens (JSON)

**Verzoek**

```
POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"
```

**Antwoordcodes**

```
201 - CREATED - if Comment has been created successfully
404 - NOT FOUND - if Asset could not be found or accessed at the provided URI
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een map of element kopiëren {#copy-a-folder-or-asset}

Kopieert een map of element op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - 'F' to prevent overwriting an existing destination
```

**Verzoek**

```
COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"
```

**Antwoordcodes**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een map of element verplaatsen {#move-a-folder-or-asset}

Hiermee verplaatst u een map of element op het opgegeven pad naar een nieuwe bestemming.

**Aanvraagkoppen**

```
X-Destination - a new destination URI within the API solution scope to copy the resource to
X-Depth - either 'infinity' or '0'. The value '0' only copies the resource and its properties, no children.
X-Overwrite - either 'T' to force deletion of existing resources or 'F' to prevent overwriting an existing resource.
```

**Verzoek**

```
MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"
```

**Antwoordcodes**

```
201 - CREATED - if folder/asset has been copied to a non-existing destination
204 - NO CONTENT - if the folder/asset has been copied to an existing destination
412 - PRECONDITION FAILED - if a request header is missing or
500 - INTERNAL SERVER ERROR - if something else goes wrong
```

## Een map, element of uitvoering verwijderen {#delete-a-folder-asset-or-rendition}

Hiermee verwijdert u een resource (-tree) bij het opgegeven pad.

**Verzoek**

```
DELETE /api/assets/myFolder
```

or

```
DELETE /api/assets/myFolder/myAsset.png
```

or

```xml
DELETE /api/assets/myFolder/myAsset.png/renditions/original
```

**Antwoordcodes**

```
200 - OK - if folder has been deleted successfully
412 - PRECONDITION FAILED - if root collection cannot be found or accessed
500 - INTERNAL SERVER ERROR - if something else goes wrong
```
