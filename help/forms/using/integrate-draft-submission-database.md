---
title: Voorbeeld voor het integreren van concepten en verzendingen in de database
description: Referentie-implementatie van aangepaste gegevens- en metagegevensservices om concepten en verzendingscomponenten te integreren in een database.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
exl-id: 2e4f8f51-df02-4bbb-99bb-30181facd1e0
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1448'
ht-degree: 0%

---

# Voorbeeld voor het integreren van concepten en verzendingen in de database {#sample-for-integrating-drafts-submissions-component-with-database}

## Voorbeeldoverzicht {#sample-overview}

Met concepten en verzendingscomponenten van AEM Forms-portaalsites kunnen gebruikers hun formulieren opslaan als concepten en later verzenden vanaf elk apparaat. Gebruikers kunnen hun ingevulde formulieren ook via een portal bekijken. Om deze functionaliteit in te schakelen, biedt AEM Forms gegevens- en metagegevensservices waarmee de gegevens die een gebruiker heeft ingevuld, worden opgeslagen in het formulier en de metagegevens van het formulier die zijn gekoppeld aan concepten en verzonden formulieren. Deze gegevens worden standaard opgeslagen in de CRX-opslagplaats. Als gebruikers echter via AEM publicatieexemplaar met formulieren werken, wat doorgaans buiten de bedrijfsfirewall valt, willen organisaties wellicht gegevensopslag aanpassen om deze beter te beveiligen en betrouwbaarder te maken.

Het voorbeeld, dat in dit document wordt besproken, is een referentie-implementatie van aangepaste gegevens en metagegevensservices om concepten en verzendingscomponenten te integreren in een database. Het gegevensbestand dat in de steekproefimplementatie wordt gebruikt is **MySQL 5.6.24**. U kunt echter de concepten en verzendingscomponent integreren met elke database van uw keuze.

>[!NOTE]
>
>* De voorbeelden en configuraties die in dit document worden uitgelegd, zijn in overeenstemming met MySQL 5.6.24 en u moet deze op de juiste wijze vervangen voor uw databasesysteem.
>* Controleer of u de nieuwste versie van het AEM Forms-invoegpakket hebt geïnstalleerd. Voor de lijst van beschikbare pakketten, zie de [&#x200B; versies van AEM Forms &#x200B;](https://helpx.adobe.com/nl/aem-forms/kb/aem-forms-releases.html) artikel.
>* Het voorbeeldpakket werkt alleen met verzendacties voor Adaptive Forms.

## Het voorbeeld instellen en configureren {#set-up-and-configure-the-sample}

Voer de volgende stappen uit, op alle auteur en publiceer instanties, om de steekproef te installeren en te vormen:

1. Download het volgende **aem-fp-db-integratie-sample-pkg-6.1.2.zip** pakket aan uw dossiersysteem.

   Voorbeeldpakket voor databaseintegratie

[Bestand ophalen](assets/aem-fp-db-integration-sample-pkg-6.1.2.zip)

1. Ga naar AEM pakketmanager in https:// [*gastheer*]:[*haven*]/crx/packmgr/.
1. Klik op **[!UICONTROL Upload Package]**.

1. Blader naar het **aem-fp-db-integratie-sample-pkg-6.1.2.zip** pakket en klik **[!UICONTROL OK]**.
1. Klik op **[!UICONTROL Install]** naast het pakket om het pakket te installeren.
1. Ga naar **[!UICONTROL AEM Web Console Configuration]**
pagina in https:// [*gastheer*]:[*haven*]/system/console/configMgr.
1. Klik om **[!UICONTROL Forms Portal Draft and Submission Configuration]** te openen in bewerkingsmodus.

1. Geef de waarden voor de eigenschappen op zoals in de volgende tabel wordt beschreven:

   | **Bezit** | **Beschrijving** | **Waarde** |
   |---|---|---|
   | Forms Portal Conceptgegevensservice | Id voor conceptgegevensservice | formsportal.sampledataservice |
   | Forms Portal Draft Metadata Service | Identificatiecode voor service met metagegevens van concept | formsportal.samplemetadataservice |
   | Forms Portal verzendt Data Service | Id voor verzendgegevensservice | formsportal.sampledataservice |
   | Forms Portal verzendt metagegevensservice | Id voor verzendmetagegevensservice | formsportal.samplemetadataservice |
   | Forms Portal in afwachting van Sign Data Service | Identifier voor de dataservice in afwachting van ondertekening | formsportal.sampledataservice |
   | Forms Portal in afwachting van Sign Metadata Service | Identificatiecode voor de metagegevensservice in afwachting van ondertekening | formsportal.samplemetadataservice |

   >[!NOTE]
   >
   >De services worden als volgt opgelost door hun namen die als waarde voor de sleutel `aem.formsportal.impl.prop` worden vermeld:

   ```java
   @Service(value = {SubmitDataService.class, DraftDataService.class})
   @Property(name = "aem.formsportal.impl.prop", value = "formsportal.sampledataservice")
   @Service(value = { SubmitMetadataService.class, DraftMetadataService.class })
   @Property(name = "aem.formsportal.impl.prop", value = "formsportal.samplemetadataservice")
   ```

   U kunt namen van de gegevens en meta-gegevenslijsten veranderen.

   Een andere naam opgeven voor de metagegevenstabel:

   * Zoek in de webconsoleconfiguratie naar en klik op Voorbeeldimplementatie van Forms Portal Metadata Service. U kunt de waarden van gegevensbron, meta-gegevens/extra naam van de meta-gegevenslijst veranderen.

   Een andere naam voor de gegevenstabel opgeven:

   * Zoek en klik in de webconsoleconfiguratie op Voorbeeldimplementatie van Forms Portal Data Service. U kunt de waarden van gegevensbron en naam van de gegevenslijst veranderen.

   >[!NOTE]
   >
   >Als u de tabelnamen wijzigt, geeft u deze op in de configuratie Formulierportal.

1. Andere configuraties ongewijzigd laten en op **[!UICONTROL Save]** klikken.

1. De databaseverbinding kan worden uitgevoerd via Apache Sling Connection Pooled Data Source.
1. Voor Apache Sling-verbinding zoekt en klikt u om **[!UICONTROL Apache Sling Connection Pooled DataSource]** te openen in de bewerkingsmodus in de webconsoleconfiguratie. Geef de waarden voor de eigenschappen op zoals in de volgende tabel wordt beschreven:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Waarde</strong></td>
  </tr>
  <tr>
   <td>Naam gegevensbron</td>
   <td><p>Een gegevensbronnaam voor het filtreren bestuurders van de gegevensbronpool</p> <p><strong> Nota: </strong> <em> de steekproefimplementatie gebruikt FormsPortal als naam van de gegevensbron.</em></p> </td>
  </tr>
  <tr>
   <td>JDBC-stuurprogrammaklasse</td>
   <td>com.mysql.jdbc.Driver</td>
  </tr>
  <tr>
   <td>URI met JDBC-verbinding <br /> </td>
   <td>jdbc :mysql://[ <em> gastheer </em>]:[<em> haven </em>]/[<em> schema_name </em>]</td>
  </tr>
  <tr>
   <td>Gebruikersnaam</td>
   <td>Een gebruikersnaam om handelingen voor databasetabellen te verifiëren en uit te voeren</td>
  </tr>
  <tr>
   <td>Wachtwoord</td>
   <td>Aan de gebruikersnaam gekoppeld wachtwoord</td>
  </tr>
  <tr>
   <td>Transactieisolatie</td>
   <td>READ_COMTED</td>
  </tr>
  <tr>
   <td>Max. actieve verbindingen</td>
   <td>1000</td>
  </tr>
  <tr>
   <td>Max. aantal inactieve verbindingen</td>
   <td>100</td>
  </tr>
  <tr>
   <td>Min. onbelaste verbindingen</td>
   <td>10</td>
  </tr>
  <tr>
   <td>Oorspronkelijke grootte</td>
   <td>10</td>
  </tr>
  <tr>
   <td>Max. wachttijd</td>
   <td>100000</td>
  </tr>
  <tr>
   <td>Testen op lenen</td>
   <td>Ingeschakeld</td>
  </tr>
  <tr>
   <td>Testen tijdens inactiviteit</td>
   <td>Ingeschakeld</td>
  </tr>
  <tr>
   <td>Validatiezoekopdracht</td>
   <td>Voorbeelden zijn SELECT 1(mysql), select 1 vanuit dual (oracle), SELECT 1 (MS Sql Server) (validationQuery)</td>
  </tr>
  <tr>
   <td>Time-out voor validatiezoekopdracht</td>
   <td>10000</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Het JDBC-stuurprogramma voor MySQL wordt niet bij het voorbeeld geleverd. Zorg ervoor dat u daarvoor de provisioned hebt en verstrek de vereiste informatie om de JDBC verbindingspool te vormen.
>* Wijs de auteur aan en publiceer instanties om het zelfde gegevensbestand te gebruiken. De waarde van het veld URI van de JDBC-verbinding moet gelijk zijn voor alle auteur- en publicatie-instanties.

1. Andere configuraties ongewijzigd laten en op **[!UICONTROL Save]** klikken.

1. Als u al een lijst in het gegevensbestandschema hebt, sla aan de volgende stap over.

   Anders, als u nog geen lijst in het gegevensbestandschema hebt, voer de volgende SQL verklaringen uit om afzonderlijke lijsten voor gegevens, meta-gegevens, en extra meta-gegevens in het gegevensbestandschema tot stand te brengen:

   >[!NOTE]
   >
   >U hebt geen verschillende databases nodig voor auteur- en publicatieinstanties. Gebruik dezelfde database voor alle auteurs en publiceer instanties.

   **SQL verklaring voor gegevenslijst**

   ```sql
   CREATE TABLE `data` (
   `owner` varchar(255) DEFAULT NULL,
   `data` longblob,
   `metadataId` varchar(45) DEFAULT NULL,
   `id` varchar(45) NOT NULL,
   PRIMARY KEY (`id`)
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

   **SQL verklaring voor meta-gegevenslijst**

   ```sql
   CREATE TABLE `metadata` (
   `formPath` varchar(1000) DEFAULT NULL,
   `formType` varchar(100) DEFAULT NULL,
   `description` text,
   `formName` varchar(255) DEFAULT NULL,
   `owner` varchar(255) DEFAULT NULL,
   `enableAnonymousSave` varchar(45) DEFAULT NULL,
   `renderPath` varchar(1000) DEFAULT NULL,
   `nodeType` varchar(45) DEFAULT NULL,
   `charset` varchar(45) DEFAULT NULL,
   `userdataID` varchar(45) DEFAULT NULL,
   `status` varchar(45) DEFAULT NULL,
   `formmodel` varchar(45) DEFAULT NULL,
   `markedForDeletion` varchar(45) DEFAULT NULL,
   `showDorClass` varchar(255) DEFAULT NULL,
   `sling:resourceType` varchar(1000) DEFAULT NULL,
   `attachmentList` longtext,
   `draftID` varchar(45) DEFAULT NULL,
   `submitID` varchar(45) DEFAULT NULL,
   `id` varchar(60) NOT NULL,
   `profile` varchar(255) DEFAULT NULL,
   `submitUrl` varchar(1000) DEFAULT NULL,
   `xdpRef` varchar(1000) DEFAULT NULL,
   `agreementId` varchar(255) DEFAULT NULL,
   `nextSigners` varchar(255) DEFAULT NULL,
   `eSignStatus` varchar(45) DEFAULT NULL,
   `pendingSignID` varchar(45) DEFAULT NULL,
   `agreementDataId` varchar(255) DEFAULT NULL,
   `enablePortalSubmit` varchar(45) DEFAULT NULL,
   `submitType` varchar(45) DEFAULT NULL,
   `dataType` varchar(45) DEFAULT NULL,
   `jcr:lastModified` varchar(45) DEFAULT NULL,
   PRIMARY KEY (`id`),
   UNIQUE KEY `ID_UNIQUE` (`id`)
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

   **SQL verklaring voor extra metadatable**

   ```sql
   CREATE TABLE `additionalmetadatatable` (
   `value` text,
   `key` varchar(255) NOT NULL,
   `id` varchar(60) NOT NULL,
   PRIMARY KEY (`id`,`key`),
   CONSTRAINT 'additionalmetadatatable_fk' FOREIGN KEY (`id`) REFERENCES `metadata` (`id`) ON DELETE CASCADE
   ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
   ```

   **SQL verklaring voor commentaarlijst**

   ```sql
   CREATE TABLE `commenttable` (
   `commentId` varchar(255) DEFAULT NULL,
   `comment` text DEFAULT NULL,
   `ID` varchar(255) DEFAULT NULL,
   `commentowner` varchar(255) DEFAULT NULL,
   `time` varchar(255) DEFAULT NULL);
   ```

1. Als u reeds de lijsten (gegevens, meta-gegevens, en extra metatable) in het gegevensbestandschema hebt, voer de volgende veranderlijke lijstvragen uit:

   **SQL verklaring voor het veranderen van de gegevenslijst**

   ```sql
   ALTER TABLE `data` CHANGE `owner` `owner` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL;
   ```

   **SQL verklaring voor het veranderen van de meta-gegevenslijst**

   ```sql
   ALTER TABLE metadata add markedForDeletion varchar(45) DEFAULT NULL
   ```

   >[!NOTE]
   >
   >De metagegevens van de ALTER-TABEL kunnen niet worden toegevoegd als u deze al hebt uitgevoerd en de kolom MarkedforDeletion in de tabel staat.

   ```sql
   ALTER TABLE metadata add agreementId varchar(255) DEFAULT NULL,
   add nextSigners varchar(255) DEFAULT NULL,
   add eSignStatus varchar(45) DEFAULT NULL,
   add pendingSignID varchar(45) DEFAULT NULL,
   add agreementDataId varchar(255) DEFAULT NULL,
   add enablePortalSubmit varchar(45) DEFAULT NULL,
   add submitType varchar(45) DEFAULT NULL,
   add dataType varchar(45) DEFAULT NULL;
   ```

   ```sql
   ALTER TABLE `metadata` CHANGE `formPath` `formPath` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `formType` `formType` VARCHAR(100) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `description` `description` TEXT CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `formName` `formName` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `owner` `owner` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `renderPath` `renderPath` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `showDorClass` `showDorClass` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `sling:resourceType` `sling:resourceType` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `profile` `profile` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `submitUrl` `submitUrl` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL,
   CHANGE `xdpRef` `xdpRef` VARCHAR(1000) CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL;
   ```

   **SQL verklaring voor het veranderen van de extra metadatable lijst**

   ```sql
   ALTER TABLE `additionalmetadatatable` CHANGE `value` `value` TEXT CHARACTER SET utf8 COLLATE utf8_general_ci NULL DEFAULT NULL, CHANGE `key` `key` VARCHAR(255) CHARACTER SET utf8 COLLATE utf8_general_ci NOT NULL;
   ```

De voorbeeldimplementatie is nu geconfigureerd, waarmee u concepten en verzendingen kunt weergeven terwijl u alle gegevens en metagegevens in een database opslaat. Laten wij nu zien hoe de gegevens en de meta-gegevensdiensten in de steekproef worden gevormd.

## Het bestand mysql-connector-java-5.1.39-bin.jar installeren {#install-mysql-connector-java-bin-jar-file}

Voer de volgende stappen uit op alle auteur- en publicatieinstanties om het bestand mysql-connector-java-5.1.39-bin.jar te installeren:

1. Ga naar `https://'[server]:[port]'/system/console/depfinder` en zoek naar het pakket com.mysql.jdbc.
1. Controleer in de kolom Geëxporteerd door of het pakket wordt geëxporteerd door een willekeurige bundel.

   Ga door als het pakket niet door enige bundel wordt uitgevoerd.

1. Ga naar `https://'[server]:[port]'/system/console/bundles` en klik op **[!UICONTROL Install/Update]** .
1. Klik op **[!UICONTROL Choose File]** en blader naar het bestand mysql-connector-java-5.1.39-bin.jar en selecteer dit. Selecteer ook de selectievakjes **[!UICONTROL Start Bundle]** en **[!UICONTROL Refresh Packages]** .
1. Klik op **[!UICONTROL Install or Update]**. Start de server opnieuw als de bewerking is voltooid.
1. (*Vensters slechts*) zet de systeemfirewall voor uw werkend systeem uit.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Voorbeeldcode voor poortgegevens en metagegevensservice voor formulieren {#sample-code-for-forms-portal-data-and-metadata-service}

Het volgende ZIP-bestand bevat `FormsPortalSampleDataServiceImpl` en `FormsPortalSampleMetadataServiceImpl` (implementatieklassen) voor gegevens- en metagegevensservice-interfaces. Bovendien bevat deze klasse alle klassen die vereist zijn voor de compilatie van de bovengenoemde implementatieklassen.

[Bestand ophalen](assets/sample_package.zip)

## De lengte van de bestandsnaam controleren  {#verify-length-of-the-file-name}

De implementatie van de database van Forms Portal maakt gebruik van extra metagegevenstabel. De tabel heeft een samengestelde primaire sleutel die is gebaseerd op de kolommen Key en id van de tabel. MySQL staat primaire sleutels tot de lengte van 255 karakters toe. U kunt het volgende validatiescript aan de clientzijde gebruiken om de lengte te controleren van de bestandsnaam die aan de bestandswidget is gekoppeld. De validatie wordt uitgevoerd wanneer een bestand wordt gekoppeld. Het script dat in de volgende procedure wordt weergegeven, geeft een bericht weer wanneer de bestandsnaam groter is dan 150 (inclusief de extensie). U kunt het script wijzigen om te controleren op een ander aantal tekens.

Voer de volgende stappen uit om [&#x200B; een cliëntbibliotheek &#x200B;](/help/sites-developing/clientlibs.md) tot stand te brengen en het manuscript te gebruiken:

1. Meld u aan bij CRXDE en navigeer naar /etc/clientlibs/
1. Creeer een knoop van type **cq:ClientLibraryFolder** en verstrek naam van de knoop. Bijvoorbeeld `validation` .

   Klik op **[!UICONTROL Save All]**.

1. Klik met de rechtermuisknop op het knooppunt, klik op **[!UICONTROL create new file]** en maak een bestand met de extensie .txt. Bijvoorbeeld, `js.txt` voeg de volgende code aan het pas gecreëerde .txt dossier toe en klik **[!UICONTROL Save All]**.

   ```javascript
   #base=util
    util.js
   ```

   In de bovenstaande code is `util` de naam van de map en `util.js` de naam van het bestand in de map `util` . De map `util` en het bestand `util.js` worden gemaakt in volgende stappen.

1. Klik met de rechtermuisknop op het knooppunt `cq:ClientLibraryFolder` dat in stap 2 is gemaakt, en selecteer Maken > Map maken. Maak een map met de naam `util` . Klik op **[!UICONTROL Save All]**. Klik met de rechtermuisknop op de map `util` en selecteer Maken > Bestand maken. Maak een bestand met de naam `util.js` . Klik op **[!UICONTROL Save All]**.

1. Voeg de volgende code toe aan het bestand util.js en klik op **[!UICONTROL Save All]** . De code valideert de lengte van de bestandsnaam.

   ```javascript
   /*
    * ADOBE CONFIDENTIAL
    * ___________________
    *
    * Copyright 2016 Adobe Systems Incorporated
    * All Rights Reserved.
    *
    * NOTICE:  All information contained herein is, and remains
    * the property of Adobe Systems Incorporated and its suppliers,
    * if any.  The intellectual and technical concepts contained
    * herein are proprietary to Adobe Systems Incorporated and its
    * suppliers and may be covered by U.S. and Foreign Patents,
    * patents in process, and are protected by trade secret or copyright law.
    * Dissemination of this information or reproduction of this material
    * is strictly forbidden unless prior written permission is obtained
    * from Adobe Systems Incorporated.
    *
    */
   (function () {
       var connectWithGuideBridge = function (gb) {
           gb.connect(function () {
               //For first time load
               window.guideBridge.on("elementValueChanged" , function(event, payload) {
           var component = payload.target; // Field whose value has changed
                   if(component.name == 'fileAttachment' && component.parent) {
                       var fileItems = $('#'+payload.target.parent.id).find(".guide-fu-fileItem");
                       for (i = 0;i<fileItems.length;i++) {
                           var filename = $(fileItems[i]).find(".guide-fu-fileName").text();
                           //check whether it is previously attached file or a newly  attached one
                           if(filename.length > 150 && filename.indexOf("fp.attach.jsp") < 0) {
                               window.alert("filename is larger than 150 : "+filename);
                                $(fileItems[i]).find(".guide-fu-fileClose.close").click();
                           }
                       }
                   }
   
      });
           });
       };
   
       if (window.guideBridge) {
           connectWithGuideBridge(window.guideBridge);
       } else {
           window.addEventListener("bridgeInitializeStart", function (event) {
               connectWithGuideBridge(event.detail.guideBridge);
           });
       }
   })();
   ```

   >[!NOTE]
   >
   >Het script is bedoeld voor de widgetcomponent voor bijlagen buiten de doos. Als u de uit-van-de-doos gehechtheid widget hebt aangepast dan verander het bovengenoemde manuscript om respectieve veranderingen op te nemen.

1. Voeg de volgende eigenschap toe aan de map die in stap 2 is gemaakt en klik op **[!UICONTROL Save All]** .

   * **[!UICONTROL Name:]** categorieën

   * **[!UICONTROL Type:]** String

   * **[!UICONTROL Value:]** fp.validation

   * **[!UICONTROL multi option:]** Ingeschakeld

1. Navigeer naar `/libs/fd/af/runtime/clientlibs/guideRuntime` en voeg de `fp.validation` -waarde toe aan de eigenschap embed.

1. Navigeer naar /libs/fd/af/runtime/clientlibs/guideRuntimeWithXFA en voeg de waarde `fp.validation` toe aan de eigenschap embed.

   >[!NOTE]
   >
   >Als u aangepaste clientbibliotheken gebruikt in plaats van guideRuntime en guideRuntimeWithXfa-clientbibliotheken, gebruikt u de categorienaam om de clientbibliotheek die in deze procedure is gemaakt, in te sluiten in uw aangepaste bibliotheken die tijdens runtime worden geladen.

1. Klik op **[!UICONTROL Save All.]** Nu wordt een bericht weergegeven wanneer de bestandsnaam groter is dan 150 tekens (inclusief extensies).
