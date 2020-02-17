---
title: De Bulkeditor
seo-title: De Bulkeditor
description: Leer hoe u de Bulk-editor kunt gebruiken.
seo-description: Leer hoe u de Bulk-editor kunt gebruiken.
uuid: 5f5e4190-d9b2-40a6-8cf4-4b7aebe35ad3
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 3649cffb-418a-4ad6-862f-56346a831b0b
docset: aem65
translation-type: tm+mt
source-git-commit: 743512254850698a32fd77151e2278dd8cc4ce7d

---


# De Bulkeditor{#the-bulk-editor}

Met de Bulkeditor kunt u op zeer efficiënte wijze pagina&#39;s bewerken als de context van de visuele pagina niet nodig is, omdat u hiermee de volgende mogelijkheden hebt:

* zoeken naar (en weergeven) inhoud van meerdere pagina&#39;s; dit gebeurt met GQL (Google Query Language)
* deze inhoud rechtstreeks in de bulkeditor bewerken
* de wijzigingen opslaan (op de pagina&#39;s die beginnen)
* deze inhoud exporteren naar een spreadsheetbestand met tabs als scheidingsteken (.tsv)

>[!NOTE]
>
>U kunt ook inhoud importeren in de opslagplaats, maar dit is standaard uitgeschakeld voor de Bulk-editor, zoals beschikbaar in de **Tools** -console.

Deze sectie beschrijft hoe te met de bulkredacteur in de console van **Hulpmiddelen** te werken. Gewoonlijk gebruiken beheerders de bulkeditor om meerdere items te zoeken en bewerken. Dit wordt gedaan door de lijst te bevolken gebruikend een vraag GQL en dan door de inhoudspunten te selecteren om aan te werken. Auteurs gebruiken de bulkeditor doorgaans als onderdeel van een aangepaste bulkbewerkingstoepassing die toegankelijk is via de [productcode](/help/sites-authoring/default-components.md#productlist) .

>[!CAUTION]
>
>Met de [afgekeurde klassieke gebruikersinterface](/help/release-notes/deprecated-removed-features.md) in AEM 6.4 is de Bulk-editor ook afgekeurd en daarom is Adobe niet van plan de Bulk-editor verder te verbeteren.

## Voorbeeld van hoofdletters/kleine letters voor de Bulkeditor {#example-use-case-for-the-bulk-editor}

Als u bijvoorbeeld alle namen en e-mailadressen nodig hebt van gebruikers die een bepaalde enquête hebben ingevuld, kan de Bulk-editor die informatie verschaffen en kunt u deze naar een werkblad exporteren.

In de Geometrixx-website vindt u een voorbeeld van een dergelijk geval van gebruik:

1. Navigeer naar de pagina **Support** en vervolgens naar de enquête **Customer Service Satisfaction** .
1. **Bewerk** de alinea **Begin van formulier** . **Klik in het dialoogvenster op het tabblad** Geavanceerd **, vouw de configuratie** van de **handeling uit en klik vervolgens op Gegevens** weergeven... .

   ![](assets/custsatsurvey.png)

1. De Bulk-editor is volledig aanpasbaar. In dit voorbeeld staat de bulkeditor gebruikers echter niet toe de inhoud te bewerken, maar laat ze de informatie alleen exporteren naar een spreadsheet.

   ![](assets/bulkeditor.png)

## De Bulkeditor gebruiken {#how-to-use-the-bulk-editor}

Met de bulkeditor kunt u:

* [zoeken naar inhoud die op vraagparameters wordt gebaseerd, om gespecificeerde eigenschappen van de resultaten in kolommen te tonen, deze inhoud uit te geven en de veranderingen te bewaren](#searching-and-editing-content)
* [om deze inhoud te exporteren naar een spreadsheet met tabs als scheidingsteken](#exporting-content)

* [inhoud importeren uit een spreadsheet met tabs als scheidingsteken](#importing-content)

### Inhoud zoeken en bewerken {#searching-and-editing-content}

Om de bulkredacteur te gebruiken om veelvoudige punten gelijktijdig uit te geven:

1. Klik in de **gereedschapsconsole** op de map **Importers** om deze uit te vouwen.
1. Dubbelklik op de **Bulk-editor** om deze te openen.
1. Voer uw selectievereisten in:

<table>
 <tbody>
  <tr>
   <td>Veld</td>
   <td>Eigenschap</td>
  </tr>
  <tr>
   <td>Hoofdpad</td>
   <td>Wijst op de wortelweg de bulkredacteursonderzoeken.<br /> Bijvoorbeeld, <code>/content/geometrixx/en</code>. De bulkbewerker zoekt naar alle onderliggende knooppunten.</td>
  </tr>
  <tr>
   <td>Zoekparameters</td>
   <td>Gebruikend parameters GQL, ga het onderzoekskoord in u de bulkredacteur wilt zoeken in de bewaarplaats; zoekt bijvoorbeeld naar alle pagina's in het hoofdpad, <code>type:Page</code> zoekt naar alle pagina's met het woord "professioneel" in de pagina's en <code>text:professional</code> <code>"jcr:title":English</code> zoekt naar alle pagina's met "Engels" als titel. U kunt alleen naar tekenreeksen zoeken.</td>
  </tr>
  <tr>
   <td>Inhoudsmodus, selectievakje</td>
   <td>Schakel dit selectievakje in om de eigenschappen in het <code>jcr:content</code> subknooppunt van de zoekresultaten te lezen, indien aanwezig. Alleen gebruiken voor pagina's. Namen van eigenschappen beginnen met <code>"jcr:content/"</code></td>
  </tr>
  <tr>
   <td>Eigenschappen/kolommen</td>
   <td>Schakel de selectievakjes in voor de eigenschappen die de bulkeditor moet retourneren. De eigenschappen die u selecteert, zijn de kolomkoppen in het resultatenvenster. Standaard wordt het knooppuntpad weergegeven in de resultaten.</td>
  </tr>
  <tr>
   <td>Aangepaste eigenschappen/kolommen</td>
   <td>Voer andere eigenschappen in die niet worden vermeld in het veld <strong>Eigenschappen/kolommen</strong> . Deze aangepaste eigenschappen worden weergegeven in het resultatenvenster. U kunt meerdere eigenschappen toevoegen door een komma te gebruiken om eigenschappen te scheiden. <i></i> Opmerking: Als u een aangepaste eigenschap toevoegt die nog niet bestaat, geeft AEM WCM een lege cel weer. Wanneer u de lege cel wijzigt en deze opslaat, wordt de eigenschap toegevoegd aan het knooppunt. De nieuwe eigenschap moet beperkingen van het knooppunttype en naamruimten van eigenschappen respecteren.</td>
  </tr>
 </tbody>
</table>

Bijvoorbeeld:

![](assets/searchfilter.png)

1. Klik op **Zoeken**. De resultaten worden weergegeven in de Bulk-editor.
In het bovenstaande voorbeeld worden alle pagina&#39;s die voldoen aan uw zoekcriteria geretourneerd en weergegeven met de gevraagde kolommen.

   ![](assets/chlimage_1-39.png)

1. Breng de gewenste wijzigingen aan door in een cel te dubbelklikken.

   ![](assets/srchresultedit.png)

1. Klik op **Opslaan** om de wijzigingen op te slaan (de knop **Opslaan** wordt geactiveerd nadat u een cel hebt bewerkt).

   >[!CAUTION]
   >
   >De wijzigingen die u hier aanbrengt, worden geschreven naar de inhoud van de opslagplaats. bijvoorbeeld de pagina waarnaar wordt verwezen in **Path**.

#### Aanvullende GQL-zoekparameters {#additional-gql-query-parameters}

* **** pad: alleen zoekknooppunten onder dit pad. Als u meer dan één termijn met een wegprefix specificeert, slechts zal laatste worden overwogen.
* **** type: alleen retourknooppunten van de opgegeven knooppunttypen. Dit omvat zowel primaire als gemengde typen. U kunt meerdere knooppunttypen opgeven die door komma&#39;s worden gescheiden. GQL retourneert knooppunten van een van de opgegeven typen.
* **** bestelling: het resultaat van de opgegeven eigenschappen te bepalen. U kunt meerdere door komma&#39;s gescheiden eigenschapsnamen opgeven. Als u het resultaat in aflopende volgorde wilt rangschikken, plaatst u gewoon een minteken voor de naam van de eigenschap. Bijvoorbeeld: order:-name. Als u een plusteken gebruikt, wordt het resultaat in oplopende volgorde geretourneerd. Dit is ook de standaardinstelling.
* **** limiet: Hiermee beperkt u het aantal resultaten met een interval. Bijvoorbeeld: limit:10..20 Let op: het interval is op nul gebaseerd, het begin is inclusief en het einde is exclusief. U kunt ook een open interval opgeven:limit:10. of limit:..20 Als de punten worden weggelaten en er slechts één waarde is opgegeven, retourneert GQL maximaal dit aantal resultaten. Bijvoorbeeld limit:10 (retourneert de eerste 10 resultaten)

### Inhoud exporteren {#exporting-content}

U moet mogelijk inhoud exporteren en er wijzigingen in aanbrengen in een Excel-spreadsheet. Bijvoorbeeld, kunt u een postingslijst willen uitvoeren en de gebiedscode van alle vermelde telefoonaantallen direct in Excel veranderen, extra lijnen toevoegen, etc.

Inhoud exporteren:

1. Zoeken naar inhoud zoals wordt beschreven in Inhoud [](#searching-and-editing-content)zoeken en bewerken.
1. Klik op **Exporteren** om de wijzigingen te exporteren naar een Excel-werkblad met tabs als scheidingsteken. AEM WCM vraagt u waar u het dossier wilt downloaden.

   >[!NOTE]
   >
   >Wijzigingen worden standaard gecodeerd in [Windows-1252](https://en.wikipedia.org/wiki/Windows-1252) (ook wel CP-1252 genoemd). U kunt UTF-8 controleren om de wijzigingen in UTF-8 te exporteren.

   ![](assets/srchrsesultexport.png)

1. Selecteer de locatie en bevestig dat u het bestand wilt downloaden.
1. Nadat u het bestand hebt gedownload, kunt u het openen vanuit het spreadsheetprogramma, bijvoorbeeld Microsoft Excel. Het spreadsheetprogramma importeert het bestand en zet het om in een spreadsheetindeling.

   ![](assets/exportinexcel.png)

### Inhoud importeren {#importing-content}

Standaard is de importfunctionaliteit verborgen wanneer u de Bulk-editor opent. Als u de parameter `hib=false` aan de URL toevoegt, wordt de knop **Importeren** weergegeven op de pagina van de Bulk-editor. U kunt inhoud importeren uit elk bestand met tabs als scheidingsteken ( `.tsv`). Importeren werkt alleen correct als de kolomkoppen (eerste rij cellen) overeenkomen met de kolomkoppen van de tabel waarnaar u importeert.

>[!NOTE]
>
>Wanneer u inhoud opnieuw importeert, wist u eventuele vorige inhoud voor die knooppunten. Zorg ervoor dat u belangrijke informatie niet overschrijft.

Inhoud importeren:

1. Open de Bulk-editor.
1. Toevoegen `?hib=false` aan de URL, bijvoorbeeld:
   `https://localhost:4502/etc/importers/bulkeditor.html?hib=false`
1. Klik op **Importeren**.
1. Select the `.tsv` file. De gegevens worden geïmporteerd in de opslagplaats.