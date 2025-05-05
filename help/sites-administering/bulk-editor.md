---
title: De Bulkeditor
description: Leer hoe u de Bulk-editor kunt gebruiken voor efficiënte bewerkingen wanneer de visuele paginacontext niet nodig is.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
exl-id: c63e044c-4d2a-44d3-853b-8e7337e1ee03
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 0%

---


# De Bulkeditor{#the-bulk-editor}

Met de Bulkeditor kunt u op efficiënte wijze pagina&#39;s bewerken wanneer de context van de visuele pagina niet nodig is, omdat u hiermee de volgende mogelijkheden hebt:

* zoeken naar (en weergeven) inhoud van meerdere pagina&#39;s; dit gebeurt met GQL (Google Query Language)
* deze inhoud rechtstreeks in de Bulkeditor bewerken
* de wijzigingen opslaan (op de pagina&#39;s die beginnen)
* deze inhoud exporteren naar een spreadsheetbestand met tabs als scheidingsteken (.tsv)

>[!NOTE]
>
>U kunt inhoud in de bewaarplaats ook invoeren, maar door gebrek is dit gehandicapt voor de BulkRedacteur zoals beschikbaar in de **console van Hulpmiddelen**.

Deze sectie beschrijft hoe te met de BulkRedacteur in de **console van Hulpmiddelen** te werken. Gewoonlijk gebruiken beheerders de Bulk-editor om meerdere items te zoeken en bewerken. Dit wordt gedaan door de lijst te bevolken gebruikend een vraag GQL en dan door de inhoudspunten te selecteren om aan te werken. De auteurs gebruiken over het algemeen de Redacteur van het Bulk als deel van een aangepaste toepassing van de Redacteur van het Bulk die door de [&#128279;](/help/sites-authoring/default-components.md#productlist) component van de lijst van 0&rbrace; product &lbrace;toegankelijk is.

>[!CAUTION]
>
>Met de [ afschrijving van Klassieke UI ](/help/release-notes/deprecated-removed-features.md) in AEM 6.4, is de Redacteur van het Bulk ook afgekeurd en zo is de Adobe niet van plan om de Redacteur van het Bulk verder te verbeteren.

## Voorbeeld van hoofdletters/kleine letters voor de Bulkeditor {#example-use-case-for-the-bulk-editor}

Als u bijvoorbeeld alle namen en e-mailadressen nodig hebt van gebruikers die een bepaalde enquête hebben ingevuld, kan de Bulk-editor die informatie verschaffen en kunt u deze naar een werkblad exporteren.

Een voorbeeld om een dergelijk gebruiksgeval te illustreren is opgenomen in de website van de Geometrixx:

1. Navigeer aan de **pagina van de Steun** en dan aan het **Tevredenheid van de Dienst van de Klant** onderzoek.
1. **geeft** het **Begin van Vorm** paragraaf uit. In de dialoogdoos, klik het **Geavanceerde** lusje, breid de **Configuratie van de Actie** uit, dan klik **Gegevens van de Mening...**.

   ![ het onderzoeksvoorbeeld van de Tevredenheid van de Klant ](assets/custsatsurvey.png)

1. De Bulkeditor is volledig aanpasbaar, maar in dit voorbeeld staat de Bulkeditor gebruikers niet toe de inhoud te bewerken, maar laat ze de informatie alleen exporteren naar een spreadsheet.

   ![ Bulk redacteursconsole ](assets/bulkeditor.png)

## De Bulkeditor gebruiken {#how-to-use-the-bulk-editor}

Met de Bulkeditor kunt u:

* [zoeken naar inhoud die op vraagparameters wordt gebaseerd, om gespecificeerde eigenschappen van de resultaten in kolommen te tonen, deze inhoud uit te geven en de veranderingen te bewaren](#searching-and-editing-content)
* [om deze inhoud naar een door tabs gescheiden spreadsheet te exporteren](#exporting-content)

* [inhoud importeren uit een spreadsheet met tabs als scheidingsteken](#importing-content)

### Inhoud zoeken en bewerken {#searching-and-editing-content}

De Bulkeditor gebruiken om meerdere items tegelijk te bewerken:

1. In de **console van Hulpmiddelen**, klik de **omslag van Importeurs** om het uit te breiden.
1. Dubbelklik de **Redacteur van het Bulk**.
1. Voer uw selectievereisten in:

<table>
 <tbody>
  <tr>
   <td>Veld</td>
   <td>Eigenschap</td>
  </tr>
  <tr>
   <td>Hoofdpad</td>
   <td>Hiermee geeft u het hoofdpad aan dat door de Bulk-editor wordt gezocht.<br /> Bijvoorbeeld <code>/content/geometrixx/en</code> . De Bulk-editor zoekt naar alle onderliggende knooppunten.</td>
  </tr>
  <tr>
   <td>Zoekparameters</td>
   <td>Gebruikend parameters GQL, ga het onderzoekskoord in u de BulkRedacteur wilt zoeken in de bewaarplaats. <code>type:Page</code> zoekt bijvoorbeeld naar alle pagina's in het hoofdpad, <code>text:professional</code> zoekt naar alle pagina's met het woord 'professioneel' in de pagina's en <code>"jcr:title":English</code> zoekt naar alle pagina's met 'Engels' als titel. U kunt alleen naar tekenreeksen zoeken.</td>
  </tr>
  <tr>
   <td>Inhoudsmodus, selectievakje</td>
   <td>Schakel dit selectievakje in zodat u eigenschappen kunt lezen in het subknooppunt <code>jcr:content</code> van de zoekresultaten, indien aanwezig. Alleen gebruiken voor pagina's. Namen van eigenschappen beginnen met <code>"jcr:content/"</code></td>
  </tr>
  <tr>
   <td>Eigenschappen/kolommen</td>
   <td>Schakel de selectievakjes in voor de eigenschappen die de Bulk-editor moet retourneren. De eigenschappen die u selecteert, zijn de kolomkoppen in het resultatenvenster. Standaard wordt het knooppuntpad weergegeven in de resultaten.</td>
  </tr>
  <tr>
   <td>Aangepaste eigenschappen/kolommen</td>
   <td>Ga om het even welke andere eigenschappen in die niet vermeld op het <strong> Eigenschappen/Kolommen </strong> gebied zijn. Deze aangepaste eigenschappen worden weergegeven in het resultatenvenster. U kunt meerdere eigenschappen toevoegen door een komma te gebruiken om eigenschappen te scheiden. <i> Nota:</i> als u een douanebezit toevoegt dat nog niet bestaat, AEM WCM toont een lege cel. Wanneer u de lege cel wijzigt en deze opslaat, wordt de eigenschap toegevoegd aan het knooppunt. De nieuwe eigenschap moet beperkingen van het knooppunttype en naamruimten van eigenschappen respecteren.</td>
  </tr>
 </tbody>
</table>

Bijvoorbeeld:

![ de opties van de redacteursfilter van de Bulk ](assets/searchfilter.png)

1. Klik **Onderzoek**. De resultaten worden weergegeven in de Bulk-editor.
In het bovenstaande voorbeeld worden alle pagina&#39;s die voldoen aan uw zoekcriteria geretourneerd en weergegeven met de gevraagde kolommen.

   ![ Bulk redacteursresultaten ](assets/chlimage_1-39.png)

1. Dubbelklik op een cel zodat u wijzigingen kunt aanbrengen.

   ![ het Uitgeven in bulk ](assets/srchresultedit.png)

1. Klik **sparen** om uw veranderingen (**sparen** knoop wordt geactiveerd nadat u een cel) hebt uitgegeven.

   >[!CAUTION]
   >
   >De veranderingen u hier aanbrengt worden geschreven aan de bewaarplaatsinhoud; bijvoorbeeld, de pagina die in **Weg** van verwijzingen wordt voorzien.

#### Aanvullende GQL-zoekparameters {#additional-gql-query-parameters}

* **weg:** slechts onderzoeksknopen onder dit weg. Als u meer dan één termijn met een wegprefix specificeert, slechts wordt het laatste overwogen.
* **type:** slechts terugkeerknopen van het bepaalde knooptype. Dit omvat primaire en mixintypes. U kunt meerdere knooppunttypen opgeven die door komma&#39;s worden gescheiden. GQL retourneert knooppunten van een van de opgegeven typen.
* **orde:** orde het resultaat door de bepaalde eigenschappen. U kunt meerdere door komma&#39;s gescheiden eigenschapsnamen opgeven. Als u het resultaat in aflopende volgorde wilt rangschikken, plaatst u gewoon een minteken voor de naam van de eigenschap. Bijvoorbeeld de volgorde:-name. Als u een plusteken gebruikt, wordt het resultaat in oplopende volgorde geretourneerd. Dit is ook de standaardinstelling.
* **grens:** beperkt het aantal resultaten gebruikend een interval. Limiet:10..20 Het interval is op nul gebaseerd, het begin is inclusief en het einde is exclusief. U kunt ook een open `interval:limit:10..` of `limit:..20` opgeven
Als de punten worden weggelaten en slechts één waarde wordt gespecificeerd, GQL keert hoogstens dit aantal resultaten terug. Bijvoorbeeld `limit:10` (retourneert de eerste tien resultaten).

### Inhoud exporteren {#exporting-content}

Exporteer inhoud indien nodig naar een Excel-werkblad om wijzigingen aan te brengen. U kunt bijvoorbeeld een mailinglijst exporteren en de gebiedscode van alle vermelde telefoonnummers rechtstreeks in Excel wijzigen, of extra regels toevoegen.

Inhoud exporteren:

1. Onderzoek naar inhoud zoals die in [ wordt beschreven het Zoeken en het Uitgeven Inhoud ](#searching-and-editing-content).
1. Klik **Uitvoer** zodat kunt u de veranderingen in een lusje-gescheiden spreadsheet van Excel uitvoeren. AEM WCM vraagt u waar u het bestand wilt downloaden.

   >[!NOTE]
   >
   >Door gebrek, worden de veranderingen gecodeerd in [ vensters-1252 ](https://en.wikipedia.org/wiki/Windows-1252) (die ook als CP-1252 wordt bekend). U kunt UTF-8 controleren om de wijzigingen in UTF-8 te exporteren.

   ![ het Uitvoeren resultaten ](assets/srchrsesultexport.png)

1. Selecteer de locatie en bevestig dat u het bestand wilt downloaden.
1. Nadat u het bestand hebt gedownload, kunt u het openen vanuit uw spreadsheetprogramma, bijvoorbeeld Microsoft® Excel. Het spreadsheetprogramma importeert het bestand en zet het om in een spreadsheetindeling.

   ![ Geëxporteerde resultaten in een spreadsheet ](assets/exportinexcel.png)

### Inhoud importeren {#importing-content}

Standaard is de importfunctionaliteit verborgen wanneer u de Bulk-editor opent. Eenvoudig toevoegend de parameter `hib=false` aan URL toont de **Invoer** knoop op de Bulk pagina van de Redacteur. U kunt inhoud importeren uit elk bestand met tabs als scheidingsteken ( `.tsv` ). Importeren werkt alleen correct als de kolomkoppen (eerste rij cellen) overeenkomen met de kolomkoppen van de tabel waarnaar u importeert.

>[!NOTE]
>
>Wanneer u inhoud opnieuw importeert, wist u eventuele vorige inhoud voor die knooppunten. Zorg ervoor dat u belangrijke informatie niet overschrijft.

Inhoud importeren:

1. Open de Bulk-editor.
1. Voeg `?hib=false` toe aan de URL, bijvoorbeeld:
   `https://localhost:4502/etc/importers/bulkeditor.html?hib=false`
1. Klik **Invoer**.
1. Selecteer het `.tsv` -bestand. De gegevens worden geïmporteerd in de opslagplaats.
