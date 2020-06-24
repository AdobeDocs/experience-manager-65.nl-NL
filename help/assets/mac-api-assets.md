---
title: Elementen van HTTP-API in [!DNL-Adobe Experience Manager].
description: Digitale elementen maken, lezen, bijwerken, verwijderen en beheren met de HTTP-API in [!DNL Adobe Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 307a1db2e5bbb72d730c89ba14f5ce02b96c108d
workflow-type: tm+mt
source-wordcount: '1563'
ht-degree: 0%

---


# HTTP-API voor assets {#assets-http-api}

## Overzicht {#overview}

Met de HTTP-API voor middelen kunt u CRUD-bewerkingen (read-read-update-delete) maken voor digitale elementen, waaronder metagegevens, vertoningen en opmerkingen, en voor gestructureerde inhoud met behulp van [!DNL Experience Manager] Content Fragments. Deze wordt weergegeven op `/api/assets` en geïmplementeerd als REST API. Dit omvat [ondersteuning voor inhoudsfragmenten](/help/assets/assets-api-content-fragments.md).

Toegang krijgen tot de API:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json`.
1. Volg de koppelingen van de service Middelen die naar `https://[hostname]:[server]/api/assets.json`leiden.

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

Na de gebeurtenis [!UICONTROL Off Time]zijn een middel en de uitvoeringen ervan niet beschikbaar via de [!DNL Assets] webinterface en via de HTTP-API. De API retourneert een foutbericht van 404 als het in de toekomst [!UICONTROL On Time] is of in het verleden [!UICONTROL Off Time] is.

## Contentfragmenten {#content-fragments}

Een [inhoudsfragment](/help/assets/content-fragments/content-fragments.md) is een speciaal type element. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn tussen `standard` elementen (zoals afbeeldingen of documenten), zijn enkele aanvullende regels van toepassing op de afhandeling van inhoudsfragmenten.

Zie Ondersteuning van [inhoudsfragmenten in de HTTP-API](/help/assets/assets-api-content-fragments.md)van Experience Manager Assets voor meer informatie.

## Gegevensmodel {#data-model}

De HTTP-API voor middelen stelt twee belangrijke elementen, mappen en elementen beschikbaar (voor standaardelementen).

Bovendien, stelt het meer gedetailleerde elementen voor de modellen van douanegegevens bloot die gestructureerde inhoud in de Fragments van de Inhoud beschrijven. Zie Gegevensmodellen [van](/help/assets/assets-api-content-fragments.md#content-fragments) inhoudsfragmenten voor meer informatie.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen in traditionele bestandssystemen. Het zijn containers voor andere mappen of berichten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een map zijn onderliggende elementen, mappen en elementen.

**Eigenschappen**:

* `name` is de naam van de map. Dit is het zelfde als het laatste segment in de weg URL zonder de uitbreiding.
* `title` is een optionele titel van de map die in plaats van de naam kan worden weergegeven.

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. Het `jcr` voorvoegsel van `jcr:title`, `jcr:description`en `jcr:language` worden vervangen door het `dc` voorvoegsel. Daarom in de geretourneerde JSON `dc:title` en `dc:description` bevatten deze de waarden van respectievelijk `jcr:title` en `jcr:description`.

**Er zijn drie koppelingen beschikbaar in Koppelingsmappen** :

* `self`: Koppeling naar zichzelf.
* `parent`: Koppeling naar de bovenliggende map.
* `thumbnail`: (Optioneel) koppeling naar een miniatuurafbeelding van een map.

### Assets {#assets}

In Experience Manager bevat een element de volgende elementen:

* De eigenschappen en metagegevens van het element.
* Meerdere uitvoeringen, zoals de oorspronkelijke uitvoering (het oorspronkelijk geüploade element), een miniatuur en verschillende andere uitvoeringen. Extra uitvoeringen kunnen afbeeldingen van verschillende grootten, videocoderingen of uit PDF- of [!DNL Adobe InDesign] bestandsbestanden geëxtraheerde pagina&#39;s zijn.
* Optionele opmerkingen.

Zie Ondersteuning van [inhoudsfragmenten in de HTTP-API](/help/assets/assets-api-content-fragments.md#content-fragments)van Experience Manager Assets voor informatie over elementen in Content Fragments.

In [!DNL Experience Manager] een map zijn de volgende componenten beschikbaar:

* Entiteiten: De onderliggende elementen van activa zijn de uitvoeringen.
* Eigenschappen.
* Koppelingen.

De HTTP-API voor middelen bevat de volgende functies:

* Haal een mappenlijst op.
* Maak een map.
* Maak een element.
* Binair element bijwerken.
* Metagegevens van elementen bijwerken.
* Een elementuitvoering maken.
* Een elementuitvoering bijwerken.
* Maak een middelenopmerking.
* Kopieer een map of element.
* Een map of element verplaatsen.
* Een map, element of uitvoering verwijderen.

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notatie weggelaten. In feite heeft de notatie een correlatie met [Resty](https://github.com/micha/resty) , een scriptwrapper voor `cURL`.

**Vereisten**

* Ga naar `https://[aem_server]:[port]/system/console/configMgr`.
* Ga naar **[!UICONTROL Adobe Granite CSRF Filter]**.
* Zorg ervoor dat de eigenschap het volgende **[!UICONTROL Filter Methods]** bevat: `POST`, `PUT`, `DELETE`.

## Een mappenlijst ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**: `GET /api/assets/myFolder.json`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - succes.
* 404 - NIET GEVONDEN - map bestaat niet of is niet toegankelijk.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

**Reactie**: De klasse van de geretourneerde entiteit is een middel of een map. De eigenschappen van ingesloten entiteiten vormen een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige vertegenwoordiging van de entiteit te verkrijgen, zouden de cliënten de inhoud van URL moeten terugwinnen waarnaar door de verbinding met een `rel` van `self`. wordt verwezen.

## Een map maken {#create-a-folder}

Hiermee maakt u een nieuwe `sling`: `OrderedFolder` op het opgegeven pad. Als een knooppunt in plaats van een knooppuntnaam `*` wordt opgegeven, gebruikt servlet de parameternaam als knooppuntnaam. Gegevens die worden geaccepteerd als aanvraaggegevens zijn een Sirene-weergave van de nieuwe map of een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form`- `data`, handig om een map te maken die rechtstreeks afkomstig is van een HTML-formulier. Bovendien kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

Een API-aanroep mislukt met een `500` antwoordcode als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Een aanroep retourneert een antwoordcode `409` als de map al bestaat.

**Parameters**: `name` is de mapnaam.

**Verzoek**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"title=My Folder"`

**Antwoordcodes**: De responscodes zijn:

* 201 - GEMAAKT - over succesvol maken.
* 409 - CONFLICT - als de map al bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een element maken {#create-an-asset}

Plaats het opgegeven bestand op het opgegeven pad om een element te maken in de DAM-opslagplaats. Als een knooppunt wordt opgegeven in plaats van een knooppuntnaam, gebruikt de servlet de parameternaam of de bestandsnaam als knooppuntnaam. `*`

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

Werkt de metagegevenseigenschappen van het element bij. Als u een eigenschap in de `dc:` naamruimte bijwerkt, werkt de API dezelfde eigenschap in de `jcr` naamruimte bij. De API synchroniseert de eigenschappen niet onder de twee naamruimten.

**Verzoek**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"dc:title":"My Asset"}}'`

**Antwoordcodes**: De responscodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering maken {#create-an-asset-rendition}

Maak een nieuwe elementuitvoering voor een element. Als de naam van de parameter request niet wordt opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**: De parameters zijn `name` voor naam van de vertoning en `file` als dossierverwijzing.

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

**Parameters**: De parameters zijn `message` voor de berichttekst van de opmerking en `annotationData` voor de annotatiegegevens in JSON-indeling.

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
* `X-Depth` - hetzij `infinity` hetzij `0`. Het gebruiken kopieert `0` slechts het middel en zijn eigenschappen en niet zijn kinderen.
* `X-Overwrite` - Gebruik deze optie `F` om te voorkomen dat een element op de bestaande bestemming wordt overschreven.

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
* `X-Depth` - hetzij `infinity` hetzij `0`. Het gebruiken kopieert `0` slechts het middel en zijn eigenschappen en niet zijn kinderen.
* `X-Overwrite` - Gebruik deze optie `T` `F` om bestaande bronnen te verwijderen of om te voorkomen dat bestaande bronnen worden overschreven.

**Verzoek**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

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
