---
title: '[!DNL Assets] HTTP API.'
description: Creeer, lees, update, schrap, beheer digitale activa gebruikend HTTP API in  [!DNL Adobe Experience Manager Assets].
contentOwner: AG
role: Developer
feature: Assets HTTP API,Developer Tools
exl-id: 6bc10f4e-a951-49ba-9c71-f568a7f2e40d
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1763'
ht-degree: 0%

---

# [!DNL Assets] HTTP-API {#assets-http-api}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/mac-api-assets.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

## Overzicht {#overview}

Met de HTTP-API van [!DNL Assets] kunt u CRUD-bewerkingen (read-read-update-delete) maken voor digitale elementen, waaronder metagegevens, vertoningen en opmerkingen, en voor gestructureerde inhoud met behulp van [!DNL Experience Manager] Inhoudsfragmenten. Deze wordt weergegeven in `/api/assets` en wordt geïmplementeerd als REST API. Het omvat [&#x200B; steun voor de Fragmenten van de Inhoud &#x200B;](/help/assets/assets-api-content-fragments.md).

De API openen:

1. Open het API-servicedocument op `https://[hostname]:[port]/api.json` .
1. Volg de servicekoppeling [!DNL Assets] naar `https://[hostname]:[server]/api/assets.json` .

De API-reactie is een JSON-bestand voor sommige MIME-typen en een antwoordcode voor alle MIME-typen. Het JSON-antwoord is optioneel en is mogelijk niet beschikbaar, bijvoorbeeld voor PDF-bestanden. Vertrouw op de antwoordcode voor verdere analyse of acties.

Na [!UICONTROL Off Time] zijn een element en de bijbehorende uitvoeringen niet beschikbaar via de [!DNL Assets] -webinterface en via de HTTP-API. De API retourneert een foutbericht van 404 als de [!UICONTROL On Time] in de toekomst is of als [!UICONTROL Off Time] in het verleden is.

>[!CAUTION]
>
>[&#x200B; HTTP API werkt de meta-gegevenseigenschappen &#x200B;](#update-asset-metadata) in `jcr` namespace bij. De gebruikersinterface van de Experience Manager werkt echter de eigenschappen van metagegevens in de naamruimte `dc` bij.

## Inhoudsfragmenten {#content-fragments}

A [&#x200B; inhoudsfragment &#x200B;](/help/assets/content-fragments/content-fragments.md) is een speciaal type van activa. Het kan worden gebruikt om tot gestructureerde gegevens, zoals teksten, aantallen, data toegang te hebben. Aangezien er verschillende verschillen zijn tussen `standard` -elementen (zoals afbeeldingen of documenten), zijn er enkele aanvullende regels van toepassing op de afhandeling van inhoudsfragmenten.

Voor verdere informatie zie [&#x200B; de Steun van de Fragmenten van de Inhoud in Experience Manager Assets HTTP API &#x200B;](/help/assets/assets-api-content-fragments.md).

## Gegevensmodel {#data-model}

De [!DNL Assets] HTTP API stelt twee belangrijke elementen, omslagen en activa (voor standaardactiva) bloot.

Bovendien, stelt het meer gedetailleerde elementen voor de modellen van douanegegevens bloot die gestructureerde inhoud in de Fragments van de Inhoud beschrijven. Zie [&#x200B; Modellen van de Gegevens van het Fragment van de Inhoud &#x200B;](/help/assets/assets-api-content-fragments.md#content-fragments) voor verdere informatie.

### Mappen {#folders}

Mappen zijn vergelijkbaar met mappen in traditionele bestandssystemen. Het zijn containers voor andere mappen of berichten. Mappen hebben de volgende componenten:

**Entiteiten**: De entiteiten van een omslag zijn zijn kindelementen, die omslagen en activa kunnen zijn.

**Eigenschappen**:

* `name` is de naam van de map. Dit is het zelfde als het laatste segment in de weg URL zonder de uitbreiding.
* `title` is een optionele titel van de map die kan worden weergegeven in plaats van de naam ervan.

>[!NOTE]
>
>Sommige eigenschappen van map of element worden toegewezen aan een ander voorvoegsel. Het voorvoegsel `jcr` van `jcr:title` , `jcr:description` en `jcr:language` wordt vervangen door het voorvoegsel `dc` . Daarom bevatten `dc:title` en `dc:description` in de geretourneerde JSON de waarden van respectievelijk `jcr:title` en `jcr:description` .

**de Omslagen van Verbindingen** stellen drie verbindingen bloot:

* `self`: Koppeling naar zichzelf.
* `parent`: Koppeling naar de bovenliggende map.
* `thumbnail`: (Optioneel) koppel de miniatuurafbeelding van een map.

### Assets {#assets}

In Experience Manager bevat een element de volgende elementen:

* De eigenschappen en metagegevens van het element.
* Meerdere uitvoeringen, zoals de oorspronkelijke uitvoering (het oorspronkelijk geüploade element), een miniatuur en verschillende andere uitvoeringen. Extra uitvoeringen kunnen afbeeldingen van verschillende grootten, videocoderingen of uitgenomen pagina&#39;s uit PDF- of [!DNL Adobe InDesign] -bestanden zijn.
* Optionele opmerkingen.

Voor informatie over elementen in de Fragmenten van de Inhoud zie [&#x200B; de Steun van de Fragmenten van de Inhoud in HTTP van Experience Manager Assets API &#x200B;](/help/assets/assets-api-content-fragments.md#content-fragments).

In [!DNL Experience Manager] heeft een map de volgende componenten:

* Entiteiten: De onderliggende elementen van activa zijn de uitvoeringen.
* Eigenschappen.
* Koppelingen.

De [!DNL Assets] HTTP API bevat de volgende functies:

* [&#x200B; wint een omslaglijst &#x200B;](#retrieve-a-folder-listing) terug.
* [&#x200B; creeer een omslag &#x200B;](#create-a-folder).
* [&#x200B; creeer een activa &#x200B;](#create-an-asset).
* [&#x200B; de activa binaire van de Update &lbrace;](#update-asset-binary).
* [&#x200B; de activameta-gegevens van de Update &#x200B;](#update-asset-metadata).
* [&#x200B; creeer een activa vertoning &#x200B;](#create-an-asset-rendition).
* [&#x200B; werk een activavertoning &#x200B;](#update-an-asset-rendition) bij.
* [&#x200B; creeer een activacommentaar &#x200B;](#create-an-asset-comment).
* [&#x200B; Kopieer een omslag of activa &#x200B;](#copy-a-folder-or-asset).
* [&#x200B; Beweeg een omslag of activa &#x200B;](#move-a-folder-or-asset).
* [&#x200B; Schrap een omslag, activa, of vertoning &#x200B;](#delete-a-folder-asset-or-rendition).

>[!NOTE]
>
>Om de leesbaarheid te verbeteren, worden in de volgende voorbeelden de volledige cURL-notatie weggelaten. In feite correleert de aantekening met [&#x200B; Herstel &#x200B;](https://github.com/micha/resty) dat een manuscriptomslag voor `cURL` is.

**Eerste vereisten**

* Toegang `https://[aem_server]:[port]/system/console/configMgr`.
* Navigeer naar **[!UICONTROL Adobe Granite CSRF Filter]** .
* Zorg ervoor dat de eigenschap **[!UICONTROL Filter Methods]** het volgende bevat: `POST`, `PUT`, `DELETE` .

## Een mappenlijst ophalen {#retrieve-a-folder-listing}

Haalt een Siren-weergave op van een bestaande map en van de onderliggende entiteiten (submappen of elementen).

**Verzoek**: `GET /api/assets/myFolder.json`

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - succes.
* 404 - NIET GEVONDEN - map bestaat niet of is niet toegankelijk.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

**Reactie**: De klasse van de teruggekeerde entiteit is activa of een omslag. De eigenschappen van ingesloten entiteiten vormen een subset van de volledige reeks eigenschappen van elke entiteit. Om een volledige weergave van de entiteit te verkrijgen, moeten clients de inhoud ophalen van de URL waarnaar de koppeling verwijst met een `rel` van `self` .

## Een map maken {#create-a-folder}

Maakt een nieuwe `sling`: `OrderedFolder` op het opgegeven pad. Als een `*` wordt verstrekt in plaats van een knooppuntnaam, gebruikt servlet de parameternaam als knooppuntnaam. Gegevens die worden geaccepteerd als aanvraaggegevens zijn een Sirene-weergave van de nieuwe map of een set naam-waardeparen, gecodeerd als `application/www-form-urlencoded` of `multipart`/ `form` - `data` , nuttig om een map te maken die rechtstreeks afkomstig is van een HTML-formulier. Bovendien kunnen eigenschappen van de map worden opgegeven als URL-queryparameters.

Een API-aanroep mislukt met een antwoordcode `500` als het bovenliggende knooppunt van het opgegeven pad niet bestaat. Een aanroep retourneert een antwoordcode `409` als de map al bestaat.

**Parameters**: `name` is de omslagnaam.

**Verzoek**

* `POST /api/assets/myFolder -H"Content-Type: application/json" -d '{"class":"assetFolder","properties":{"jcr:title":"My Folder"}}'`
* `POST /api/assets/* -F"name=myfolder" -F"jcr:title=My Folder"`

**de codes van de Reactie**: De antwoordcodes zijn:

* 201 - GEMAAKT - over succesvol maken.
* 409 - CONFLICT - als de map al bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een element maken {#create-an-asset}

Plaats het opgegeven bestand op het opgegeven pad om een element te maken in de DAM-opslagplaats. Als een `*` wordt verstrekt in plaats van een knooppuntnaam, gebruikt servlet de parameternaam of de dossiernaam als knooppuntnaam.

**Parameters**: De parameters zijn `name` voor de activa naam en `file` voor de dossierverwijzing.

**Verzoek**

* `POST /api/assets/myFolder/myAsset.png -H"Content-Type: image/png" --data-binary "@myPicture.png"`
* `POST /api/assets/myFolder/* -F"name=myAsset.png" -F"file=@myPicture.png"`

**de codes van de Reactie**: De antwoordcodes zijn:

* 201 - GEMAAKT - als Asset is gemaakt.
* 409 - CONFLICT - als Activum al bestaat.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Elementbinair bijwerken {#update-asset-binary}

Hiermee werkt u de binaire waarde (uitvoering met de oorspronkelijke naam) van een element bij. Een update activeert de standaardworkflow voor middelenverwerking om deze uit te voeren, als deze is geconfigureerd.

**Verzoek**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: image/png" --data-binary @myPicture.png`

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Metagegevens van elementen bijwerken {#update-asset-metadata}

Werkt de eigenschappen van de elementmetagegevens bij. Als u een eigenschap in de naamruimte `dc:` bijwerkt, werkt de API dezelfde eigenschap in de naamruimte `jcr` bij. De API synchroniseert de eigenschappen niet onder de twee naamruimten.

**Verzoek**: `PUT /api/assets/myfolder/myAsset.png -H"Content-Type: application/json" -d '{"class":"asset", "properties":{"jcr:title":"My Asset"}}'`

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - als Asset met succes is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

### Update van metagegevens synchroniseren tussen `dc` en `jcr` namespace {#sync-metadata-between-namespaces}

De API-methode werkt de eigenschappen van metagegevens in de naamruimte `jcr` bij. De updates die worden uitgevoerd via de gebruikersinterface wijzigen de eigenschappen van metagegevens in de naamruimte `dc` . Als u de waarden van metagegevens wilt synchroniseren tussen `dc` en `jcr` -naamruimte, kunt u een workflow maken en Experience Manager configureren om de workflow uit te voeren bij het bewerken van elementen. Gebruik een ECMA-script om de vereiste eigenschappen van metagegevens te synchroniseren. In het volgende voorbeeldscript wordt de titeltekenreeks gesynchroniseerd tussen `dc:title` en `jcr:title` .

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

Een elementuitvoering voor een element maken. Als de naam van de parameter request niet wordt opgegeven, wordt de bestandsnaam gebruikt als naam voor de vertoning.

**Parameters**: De parameters zijn `name` voor naam van de vertoning en `file` als dossierverwijzing.

**Verzoek**

* `POST /api/assets/myfolder/myasset.png/renditions/web-rendition -H"Content-Type: image/png" --data-binary "@myRendition.png"`
* `POST /api/assets/myfolder/myasset.png/renditions/* -F"name=web-rendition" -F"file=@myRendition.png"`

**de codes van de Reactie**: De antwoordcodes zijn:

* 201 - GEMAAKT - als de vertoning is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een elementuitvoering bijwerken {#update-an-asset-rendition}

Updates vervangen een elementuitvoering door de nieuwe binaire gegevens.

**Verzoek**: `PUT /api/assets/myfolder/myasset.png/renditions/myRendition.png -H"Content-Type: image/png" --data-binary @myRendition.png`

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - als de vertoning correct is bijgewerkt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een opmerking toevoegen aan een element {#create-an-asset-comment}

Hiermee maakt u een nieuwe middelenopmerking.

**Parameters**: De parameters zijn `message` voor het berichtlichaam van de commentaar en `annotationData` voor de gegevens van de Annotatie in formaat JSON.

**Verzoek**: `POST /api/assets/myfolder/myasset.png/comments/* -F"message=Hello World." -F"annotationData={}"`

**de codes van de Reactie**: De antwoordcodes zijn:

* 201 - GEMAAKT - als Opmerking is gemaakt.
* 404 - NIET GEVONDEN - als Asset niet kon worden gevonden of betreden op de verstrekte URI.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element kopiëren {#copy-a-folder-or-asset}

Hiermee kopieert u een map of element die beschikbaar is op het opgegeven pad naar een nieuwe bestemming.

**Kopballen van het Verzoek**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - ofwel `infinity` of `0` . Wanneer u `0` gebruikt, worden alleen de bron en de eigenschappen ervan gekopieerd en niet de onderliggende elementen.
* `X-Overwrite` - Gebruik `F` om te voorkomen dat een element op het bestaande doel wordt overschreven.

**Verzoek**: `COPY /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-copy"`

**de codes van de Reactie**: De antwoordcodes zijn:

* 201 - GEMAAKT - als de map/het element naar een niet-bestaand doel is gekopieerd.
* 204 - GEEN INHOUD - als de map of het middel naar een bestaande bestemming is gekopieerd.
* 412 - PRECONDITION MISLUKT - als een aanvraagkoptekst ontbreekt.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Een map of element verplaatsen {#move-a-folder-or-asset}

Hiermee verplaatst u een map of element op het opgegeven pad naar een nieuwe bestemming.

**Kopballen van het Verzoek**: De parameters zijn:

* `X-Destination` - een nieuwe doel-URI binnen het bereik van de API-oplossing waarnaar de bron moet worden gekopieerd.
* `X-Depth` - ofwel `infinity` of `0` . Wanneer u `0` gebruikt, worden alleen de bron en de eigenschappen ervan gekopieerd en niet de onderliggende elementen.
* `X-Overwrite` - Gebruik `T` om een bestaande bron te verwijderen of `F` om te voorkomen dat een bestaande bron wordt overschreven.

**Verzoek**: `MOVE /api/assets/myFolder -H"X-Destination: /api/assets/myFolder-moved"`

Gebruik `/content/dam` niet in de URL. Een voorbeeldopdracht voor het verplaatsen van elementen en het overschrijven van bestaande elementen is:

```shell
curl -u admin:admin -X MOVE https://[aem_server]:[port]/api/assets/source/file.png -H "X-Destination: https://[aem_server]:[port]/api/assets/destination/file.png" -H "X-Overwrite: T"
```

**de codes van de Reactie**: De antwoordcodes zijn:

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

**de codes van de Reactie**: De antwoordcodes zijn:

* 200 - OK - als de map is verwijderd.
* 412 - VOORWAARDE MISLUKT - als de wortelinzameling niet kan worden gevonden of worden betreden.
* 500 - INTERNE SERVERFOUT - als iets anders fout gaat.

## Tips en beperkingen {#tips-best-practices-limitations}

* [&#x200B; HTTP API werkt de meta-gegevenseigenschappen &#x200B;](#update-asset-metadata) in `jcr` namespace bij. De gebruikersinterface van de Experience Manager werkt echter de eigenschappen van metagegevens in de naamruimte `dc` bij.

* Assets HTTP API retourneert de volledige metagegevens niet. De naamruimten zijn gecodeerd en alleen die naamruimten worden geretourneerd. Zie het elementpad `/jcr_content/metadata.json` voor volledige metagegevens.
