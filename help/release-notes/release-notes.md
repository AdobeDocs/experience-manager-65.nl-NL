---
title: Opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: Zoek naar releasegegevens, wat is nieuw, installeer hoe kan worden gewijzigd en een gedetailleerde wijzigingslijst voor [!DNL Adobe Experience Manager] 6.5
mini-toc-levels: 4
source-git-commit: 19fe527ce44d8ec5be50ebd32b46f13df96c52cc
workflow-type: tm+mt
source-wordcount: '2900'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Laatste Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, November 30, 2023. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.20,0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Datum | Donderdag 22 februari 2024 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.20,0 {#what-is-included-in-aem-6520}

[!DNL Experience Manager] 6.5.20.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, insectenmoeilijke situaties, en prestaties, stabiliteit, en veiligheidsverbeteringen die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 zijn vrijgegeven. [Dit servicepack installeren](#install) op [!DNL Experience Manager] 6.5

<!-- UPDATE FOR EACH NEW RELEASE -->

## Belangrijke functies en verbeteringen

<!-- * _6.5.20.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Enkele belangrijke functies en verbeteringen in deze release zijn onder andere:

* Dynamic Media ondersteunt nu HEIC-afbeeldingsindeling zonder verlies voor Apple iOS/iPadOS. Zie [fmt](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html?lang=en) in de Dynamic Media Image Serving and Rendering API.

* Multisite Manager (MSM) ondersteunt nu de structuren van het Fragment van de Ervaring met inbegrip van omslagen en subfolders, voor efficiënte bulkimplementatie van de Fragmenten van de Ervaring aan Levende Kopieën.

<!-- ### [!DNL Forms]

* text -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Opgeloste problemen in Service Pack 20 {#fixed-issues}

### [!DNL Sites]{#sites-6520}

<!--#### Accessibility{#sites-accessibility-6520}

* text -->

#### Gebruikersinterface Admin{#sites-adminui-6520}

* De `Workflow Title` veld is gemarkeerd met `*` , maar er is geen validatie. (SITES-16491) NORMAAL

<!--#### Classic UI{#sites-classicui-6520}

* text -->

#### [!DNL Content Fragments]{#sites-contentfragments-6520}

* Geneste configuratiemappen worden niet meer ondersteund en de mappen met het inhoudsfragmentmodel zijn niet meer zichtbaar na de upgrade naar AEM 6.5.18 of naar AEM 6.5.19. (SITES-18110) BELANGRIJK
* Sommige submappen kunnen niet kiezen uit overerfde modellen voor inhoudsfragmenten. Mappen moeten worden ondersteund zonder een `jcr:content` eigenschap, zelfs als de DAM-mappen die via de gebruikersinterface zijn gemaakt, een dergelijk knooppunt hebben. (SITES-17943) NORMAAL

#### [!DNL Content Fragments] - GRAPHQL API {#sites-graphql-api-6520}

<!-- REMOVED AS PER EMAIL FROM SAMEER DHAWAN FEBRUARY 19, 2024 * When upgrading AEM from 6.5.19.0 to 6.5.20.0, the path `/libs/cq/graphql/sites/graphiql` was getting deleted. (SITES-19530) CRITICAL -->
* Bij het uitvoeren van een GraphQL-query op [filterresultaten](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md#filtering) met behulp van optionele variabelen, als een specifieke waarde **niet** Wordt opgegeven voor de optionele variabele, dan wordt de variabele genegeerd in de filterevaluatie. (SITES-17051) NORMAAL

<!--#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6520}

* text -->

#### [!DNL Content Fragments] - REST API{#sites-restapi-6520}

* Met de upgrade van de `org.json` bibliotheek, was er een verandering in hoe de decimale aantallen werden gedeserialiseerd. Voordat ze &#39;standaard&#39; werden omgezet in Dubbels en nu in BigDecimals. In plaats daarvan, zouden de waarden van het meta-gegevensbezit, die door REST API worden opgeslagen, in Dubbel van BigDecimal moeten worden omgezet. (SITES-16857) NORMAAL

#### Core Backend{#sites-core-backend-6520}

* Wanneer Snel publiceren van een inhoudsfragment wordt gebruikt, wordt het verder geladen en niet gepubliceerd. Met andere woorden, Snel publiceren werkt niet voor inhoudsfragmenten na een servicepack-upgrade van AEM 6.5.7 naar AEM 6.5.17. Toen de gebruiker beheerde publicatie probeerde, werkte het. Maar toen ze Snel publiceren probeerden, werd het niet gepubliceerd. Specifiek: `com.day.cq.wcm.core.impl.reference.ActivationReferenceSearchBuilder` heeft het systeem ontstoken. (SITES-17311) BELANGRIJK
* Inhoudsfragmenten kunnen niet van serienummering worden voorzien met Jackson-exportfunctie: het laden van de pagina wordt onderbroken wanneer er een inhoudsfragment is waarnaar wordt verwezen in een pagina (maakt gebruik van Jackson-exportcode) en elke tag die wordt toegevoegd aan een inhoudsfragment. (SITES-18096) NORMAAL

#### Kernonderdelen{#sites-core-components-6520}

* Installatie van CIF Core Components-pakket op AEM oorzaken `:type` waarde van bestaande componenten die moeten worden gewijzigd. De wijziging betekent dat ze niet meer worden weergegeven op pagina&#39;s waaraan ze zijn toegevoegd. (SITES-17601) BELANGRIJK

#### Campagne-integratie{#sites-campaign-integration-6520}

* AEM gebruikte een lijst van gewenste personen-ook gekend als a `whitelist`-vanwege een kwetsbaarheidsrapport. De lijst van gewenste personen verhinderde klanten vereiste functionaliteit te gebruiken. (SITES-16822) KRITIEK

#### Ervaar fragmenten{#sites-experiencefragments-6520}

* MSM for Experience Fragments ondersteunt nu bulksgewijs implementeren om de structuur van fragmentinhoud, inclusief mappen en submappen, te ervaren. (SITES-16004)

<!--#### Foundation Components (Legacy){#sites-foundation-components-legacy-6520}

* text

#### Launches{#sites-launches-6520}

* text -->

#### MSM - Actieve kopieën{#sites-msm-live-copies-6520}

* Een &quot;`Is not modifiable`Er wordt een uitzondering gegenereerd bij het uitrollen van een component. Met name een `org.apache.sling.servlets.post.impl.operations.ModifyOperation` Er is een uitzondering opgetreden tijdens de responsverwerking. (SITES-18809) MAJOR
* Kan geen wijzigingen doorvoeren in specifieke live kopieën van ervaringsfragmenten. (SITES-17930)
* Wanneer een gebruiker een annotatie toevoegt aan een component op een blauwdrukpagina en deze vervolgens uitrolt, wordt het aantal annotaties op Live Copy onjuist weergegeven. (SITES-17099)
* De MSM-uitrolknop van de bovenliggende pagina naar de onderliggende pagina wordt verbroken in de grafische gebruikersinterface met aanraakbediening. Als deze optie is geselecteerd, wordt de volgende fout weergegeven: `Uncaught TypeError: _g.shared is undefined`. (SITES-16991)

#### Pagina-editor{#sites-pageeditor-6520}

* De voorvertoning van de Forms-themaeditor is verbroken. Wanneer Voorvertoning is geselecteerd, is alleen een laadpictogram zichtbaar. (SITES-17164) BLOKKER

### [!DNL Assets]{#assets-6520}

* Kan op regels gebaseerde velden niet valideren in de Help van de metagegevenseditor en geeft een foutbericht &quot;Ontbrekende vereiste velden&quot; weer. (ACTIVA-31396)
* Nadat een PDF naar een andere plaats wordt verplaatst, **[!UICONTROL View Page]** verdwijnt. (ACTIVA-30538)
* Kan geen afbeelding selecteren met leesmachtigingen. (ACTIVA-32199) NORMAAL
* Kan de kaartgrootte niet wijzigen in de weergave-instellingen. (ACTIVA-31667) NORMAAL
* Uploaden mislukt tijdens uploaden van .oft-bestandstype. (ACTIVA-30109) NORMAAL
* Wanneer u probeert om een gebied van douanemetagegevens als extra kolom aan het rapport toe te voegen, worden checkboxes niet geselecteerd. (ACTIVA-31671) MINDER
* Het verplaatsen van middelen werkt niet correct in Experience Manager Service Pack 16. (ACTIVA-30598) MINDER

#### [!DNL Dynamic Media]{#assets-dm-6520}

* Wanneer een element naar AEM wordt geüpload, `Update_asset` de workflow wordt geactiveerd. De workflow wordt echter nooit voltooid. De workflow wordt alleen voltooid tot de uploadprocedure voor het product. De volgende stap is de Scene7 batch upload, maar dat proces wordt niet in AEM gehaald. (ACTIVA-30443)
* U hebt een betere manier nodig om niet-Dynamic Media video&#39;s netjes af te handelen in de Dynamic Media-component. Deze kwestie gaf een uitzondering concretiseren `dynamicmedia_sly.js`. (ACTIVA-31301) BELANGRIJK
* Voorvertonen werkt voor alle elementen, adaptieve videosets en video&#39;s. Er treedt echter een fout van 403 op voor `.m3u8` bestanden (die overigens nog steeds via openbare koppelingen werken). (ACTIVA-31882) BELANGRIJK
* De `scene7SmartCropProcessingStatus` status gecorrigeerd. Metagegevens van video voor SmartCrop die worden gebruikt om een fout weer te geven, zelfs wanneer dit gelukt was. (ACTIVA-31255) MINDER

### [!DNL Forms]{#forms-6520}

Oplossingen in [!DNL Experience Manager] Forms wordt één week na de geplande levering geleverd via een afzonderlijk invoegpakket [!DNL Experience Manager] Releasedatum van Service Pack. In dit geval is de AEM 6.5.20.0 Forms add-on pakketrelease gepland voor donderdag 29 februari 2024. Er wordt een lijst met Forms-correcties en -verbeteringen toegevoegd aan deze sectie na de release.

<!-- #### [!DNL Adaptive Forms] -->

<!--LEFT BULLET LIST HERE IN CASE OF REUSE BY FORMS IN THE FUTURE 
* **Document Services**
  * text
* **Adaptive Forms** 
  * text
* **Accessibility**
  * text
* **Interactive Communications**
  * text -->

<!--### Commerce{#commerce-6520}

* text -->

#### [!DNL Forms Designer]{#forms-designer-6520}

* text

<!-- ### Foundation{#foundation-6520}

* text -->

#### Gemeenschappen {#communities-6520}

* Diagnostische gegevens voor gebruikerssynchronisatie zijn mislukt nadat gebruikerssynchronisatie is voltooid. (NPR-41693) NORMAL

<!-- #### Content distribution{#foundation-content-distribution-6520}

* text -->

#### Integrations{#integrations-6520}

* Verwijder alle code en gebiedsdelen van de Search&amp;Promote van de Adobe uit AEM 6.5. (NPR-40856) NORMAL

#### Lokalisatie{#localization-6520}

* Het label ‘close’ is niet gelokaliseerd in **[!UICONTROL Assets]** > **[!UICONTROL Files]** selecteert u een map en selecteert u vervolgens op de werkbalk de optie **[!UICONTROL Properties]** > **[!UICONTROL Permissions]** tab > lidnaam. (NPR-41705) MAJOR
* De knopinfo voor de **[!UICONTROL Key Store Password]** op de pagina SSL Setup voor landinstellingen ENG, FRA, KOR, DEU en PTB. (NPR-41367) NORMAL

<!-- #### Oak{#oak-6520}

* text -->

#### Platform{#foundation-platform-6520}

* Probleem met het integreren van Campagne met AEM die wordt veroorzaakt door /api servlet die niet het correcte schema in href json terugkeert. De reden daarvoor was dat AEM de X-Forward-Proto-header niet ontving, waardoor de aanvraag moest reageren met een HTTP-schema in plaats van met HTTPS. Daarom moet de mogelijkheid worden toegevoegd om de selectie van schema&#39;s op basis van een OSGI-configuratie in- en uit te schakelen. (GRANITE-48454) MAJOR

<!-- #### Replication{#foundation-replication-6520}

* text -->

#### Sling{#foundation-sling-6520}

* De `org.apache.sling.resourceMerger` bundel 1.4.2 werpt een uitzondering van AEM 6.5, Service Pack 17 en later. The Sling resource merge 1.4.4 should be included in Service Pack 20. (NPR-41630) NORMAL

#### Vertaling{#foundation-translation-6520}

* Na plaatsing van AEM 6.5 Service Pack 18, was er een kwestie met het lusje van Filters in de Redacteur van de Regels van de Vertaling. Wanneer een Context is geselecteerd en u op Bewerken > Opslaan klikt, verschijnt een dubbel aanhalingsteken als HTML-teken wanneer u dezelfde Context opnieuw opent. In feite werden de vertaalregels niet correct opgeslagen. (NPR-41624) MAJOR
* Problemen in verband met vertalingen van inhoudsfragmenten, waarbij de vertaalde tekenreeksen van de vertaalprovider worden teruggestuurd naar AEM, maar die bij de `/content/projects` en de inhoudsfragmenten niet bijwerken. (NPR-41516) MAJOR
* Er wordt een foutbericht weergegeven wanneer u een taalkopie maakt. Deze komt voor op een pagina die een inhoudsfragment heeft dat in een paginabezit van verwijzingen wordt voorzien, gebruikend de modellen van het inhoudsfragment. (NPR-41441) MAJOR
* De verbindingen in de Fragmenten van de Ervaring worden niet aangepast aan de correcte taal tijdens het Exemplaar van de Taal. In plaats daarvan wijst het fragment van de Ervaring naar de primaire landinstelling. (NPR-41343) NORMAL

#### Gebruikersinterface{#foundation-ui-6520}

* De fout van de console wordt ervaren na een verbetering aan AEM 6.5, Service Pack 18. De fout bevindt zich in de `coralUI3.js` en dit gebeurt wanneer u een vervolgkeuzelijst in AEM selecteert. Het gebeurt met een `onOverlayToggle` gebeurtenis. De fout `Uncaught TypeError: Cannot read properties of null (reading 'innerText')` wordt weergegeven. (NPR-41467) MAJOR
* In AEM **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Tagging]** > **[!UICONTROL Create]** > **[!UICONTROL Create Tag]**, het invoeren van niet-Latijnse tekens in het dialoogvenster **Titel** veld veroorzaakt de **Naam** veld dat alleen met het afbreekstreepje moet worden gevuld ( `-` ). (NPR-41623) NORMAL
* Het copyrightjaar is onjuist in het dialoogvenster `About Adobe Experience Manager` in. (NPR-41526) NORMAL
* Er zijn geen vertalingen **[!UICONTROL Profile Properties]** tekenreeksen bij het bewerken van gebruikersinstellingen. Vindt plaats in alle landinstellingen. (NPR-41365) NORMAL

<!-- #### WCM{#wcm-6520}

* text

#### Workflow{#foundation-workflow-6520}

* text -->

## Installeren [!DNL Experience Manager] 6.5.20,0{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.20.0 vereist [!DNL Experience Manager] 6.5. Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies. <!-- UPDATE FOR EACH NEW RELEASE -->
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip).
* Bij een implementatie met MongoDB en meerdere exemplaren, installeert u [!DNL Experience Manager] 6.5.20.0 op één van de instanties van de Auteur die de Manager van het Pakket gebruiken.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe raadt u niet aan de [!DNL Experience Manager] 6.5.20.0-pakket. Voordat u het pakket installeert, moet u daarom een back-up maken van het `crx-repository` voor het geval u het terug moet rollen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installeer het de dienstpak op [!DNL Experience Manager] 6,5{#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.20.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en selecteer **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. De Adobe adviseert dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installatie succesvol is. Dit probleem treedt meestal op in het dialoogvenster [!DNL Safari] browser, maar kan soms voorkomen op om het even welke browser.

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL Experience Manager] 6.5.20.0.<!-- UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Experience Manager 6.5.20.0 ondersteunt geen installatie van Bootstrappen. <!-- UPDATE FOR EACH NEW RELEASE -->

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (6.5.20.0)` krachtens [!UICONTROL Installed Products]. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-pakketten zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.18 of hoger (webconsole gebruiken: `/system/console/bundles`). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Service Pack installeren voor [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Voor instructies voor het installeren van het servicepakket op Experience Manager Forms raadpleegt u [Installatie-instructies voor Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>De functie Adaptive Forms is beschikbaar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/deploying/deploy.html), is uitsluitend ontworpen voor exploratie en evaluatie. Voor productiegebruik is het van essentieel belang een geldige licentie voor AEM Forms te verkrijgen, aangezien voor de adaptieve Forms-functionaliteit een correcte licentie vereist is.

### GraphQL-indexpakket voor Experience Manager-inhoudsfragmenten installeren{#install-aem-graphql-index-add-on-package}

Klanten die GraphQL gebruiken, moeten de [Experience Manager-inhoudsfragment met GraphQL Index-pakket 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip).

Zo kunt u de vereiste indexdefinitie toevoegen op basis van de functies die ze daadwerkelijk gebruiken.

Als u dit pakket niet installeert, kan dit leiden tot trage of mislukte GraphQL-query&#39;s.

>[!NOTE]
>
>Installeer dit pakket slechts eenmaal per instantie; het hoeft niet opnieuw te worden geïnstalleerd met elk Service Pack.

### UberJar{#uber-jar}

The UberJar for [!DNL Experience Manager] 6.5.20.0 is beschikbaar in de [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.20/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.20</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op Maven Central Repository in plaats van Adobe Public Maven repository (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als de waarde voor de `dependency` -tag.

## Verouderde en verwijderde functies{#removed-deprecated-features}

Zie [Verouderde en verwijderde functies](/help/release-notes/deprecated-removed-features.md/).

## Bekende problemen{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.-->

<!-- * **Page publishing not working in Page Editor after upgrading to Service Pack 18 (6.5.18.0)** -->

<!-- https://jira.corp.adobe.com/browse/SITES-15856 REMOVE FOR 6.5.19.0 -->
<!-- After you upgrade an instance of AEM 6.5.0.0&mdash;6.5.17.0 to AEM 6.5.19.0, when you click **Publish Page** inside the Page Editor, you are redirected to a URL that does not exist.

  To work around this issue, do one of the following:

  * Remove the following "path" property.

       `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/publish/granite:data`

  * Paste the correct URL directly into the browser.

       `http://localhost:4504/editor.html/libs/wcm/core/content/sites/publishpagewizard.html?item=/content/we-retail/language-masters/en/about-us.html` -->



* **Verwant aan eikenhout**
Van Service Pack 13 en hierboven, is het volgende foutenlogboek begonnen te verschijnen dat het persistentiegeheime voorgeheugen beïnvloedt:

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.0.202/5]
  at org.h2.mvstore.DataUtils.newMVStoreException(DataUtils.java:1004)
      at org.h2.mvstore.MVStore.getUnsupportedWriteFormatException(MVStore.java:1059)
      at org.h2.mvstore.MVStore.readStoreHeader(MVStore.java:878)
      at org.h2.mvstore.MVStore.<init>(MVStore.java:455)
      at org.h2.mvstore.MVStore$Builder.open(MVStore.java:4052)
      at org.h2.mvstore.db.Store.<init>(Store.java:129)
  ```

  of

  ```shell
  org.h2.mvstore.MVStoreException: The write format 1 is smaller than the supported format 2 [2.1.214/5].
  ```

  U kunt deze uitzondering als volgt oplossen:

   1. De volgende twee mappen verwijderen uit `crx-quickstart/repository/`

      * `cache`
      * `diff-cache`

   1. Installeer het Service Pack of start de Experience Manager as a Cloud Service opnieuw.
Nieuwe mappen van `cache` en `diff-cache` automatisch worden gemaakt en er is geen uitzondering meer die betrekking heeft op `mvstore` in de `error.log`.

* Werk uw GraphQL-query&#39;s bij die mogelijk een aangepaste API-naam voor uw inhoudsmodel hebben gebruikt om in plaats daarvan de standaardnaam van het inhoudsmodel te gebruiken.

* Een GraphQL-query kan de opdracht `damAssetLucene` index in plaats van de `fragments` index. Deze handeling kan resulteren in GraphQL-query&#39;s die mislukken of die lang duren.

  Om het probleem te verhelpen, `damAssetLucene` moet worden geconfigureerd om de volgende twee eigenschappen op te nemen onder `/indexRules/dam:Asset/properties`:

   * `contentFragment`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/contentFragment"`
      * `propertyIndex="{Boolean}true"`
      * `type="Boolean"`
   * `model`
      * `jcr:primaryType="nt:unstructured"`
      * `name="jcr:content/data/cq:model"`
      * `ordered="{Boolean}true"`
      * `propertyIndex="{Boolean}true"`
      * `type="String"`

  Nadat de indexdefinitie is gewijzigd, is opnieuw indexeren vereist (`reindex` = `true`).

  Na deze stappen zouden de vragen van GraphQL sneller moeten presteren.

* Wanneer u probeert inhoudsfragmenten, sites of pagina&#39;s te verplaatsen, te verwijderen of te publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald, omdat de achtergrondquery mislukt. De functionaliteit werkt dus niet.
Om correcte verrichting te verzekeren, moet u de volgende eigenschappen aan de knoop van de indexdefinitie toevoegen `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

  ```xml
  "tags": [
      "visualSimilaritySearch"
    ]
  "refresh": true
  ```

* Als u uw [!DNL Experience Manager] -exemplaar van 6.5.0 - 6.5.4 naar het nieuwste servicepakket op Java™ 11, zie `RRD4JReporter` uitzonderingen in de `error.log` bestand. Als u de uitzonderingen wilt stoppen, start u de instantie van [!DNL Experience Manager]. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De maptitel wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] Als u de standaard-API (IMS-verificatie) van het doel gebruikt, leidt het exporteren van ervaringsfragmenten naar Doel tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging register is niet-geregistreerd.

* Vanaf AEM 6.5.15 wordt de Rhino JavaScript Engine geleverd door de ```org.apache.servicemix.bundles.rhino``` bundle heeft een nieuw hoistinggedrag. Scripts die de strikte modus gebruiken (```use strict;```) moeten hun variabelen correct declareren, anders worden ze niet uitgevoerd, maar wordt er een runtimefout gegenereerd.

### Bekende problemen voor AEM Forms

#### Ondersteunde platforms

* JDK 11.0.20 wordt niet ondersteund voor de installatie van AEM Forms op JEE Installer. Alleen JDK 11.0.19 of eerdere versies worden ondersteund voor de installatie van AEM Forms op JEE Installer. (FORMS-10659)

#### Installatie

* Op het JBoss® 7.1.4-platform, wanneer de gebruiker Experience Manager 6.5.16.0 of hoger servicepack installeert, `adobe-livecycle-jboss.ear` implementatie mislukt. (CQ-4351522, CQDOC-20159)

<!-- 
* After upgrading to AEM Forms 6.5.18.0 JBoss&reg; Turnkey full installer environment on Windows Server 2022, when compiling Output client application code using Java&trade; 11, the following compilation error may occur:
  
  ```
  error: error reading [AEM_Forms_Installation_dir]\sdk\client-libs\common\adobe-output-client.jar; java.net.URISyntaxException: 
  Illegal character in path at index 70: file:/[AEM_Forms_Installation_dir]/sdk/client-libs/common/${clover.jar.name} 1 error
  
  ```
  
  To resolve the issue, perform the following steps:
    1. Navigate to `[AEM_Forms_Installation_dir]\sdk\client-libs\common\` and unzip `adobe-output-client.jar` to extract the `Manifest.mf` file.
    1. Update the `Manifest.mf` file by removing the entry `${clover.jar.name}` from the class-path attribute. 

        >[!NOTE]
        >
        > You can also use an in-place editing tool, for example, 7-zip, to update the `Manifest.mf` file.  

    1. Save the updated the `Manifest.mf` in the `adobe-output-client.jar` archive. 
    1. Save the modified `adobe-output-client.jar` file and rerun the setup. (CQDOC-20878) -->

* Nadat u AEM Service Pack 6.5.20.0 volledig installatieprogramma hebt geïnstalleerd, mislukt de EAR-implementatie op JEE met JBoss® Turnkey. <!-- UPDATE FOR EACH NEW RELEASE -->

Als u het probleem wilt oplossen, zoekt u de `<AEM_Forms_Installation_dir>\jboss\bin\standalone.bat` bestand en update `Adobe_Adobe_JAVA_HOME` tot `Adobe_JAVA_HOME` voor alle instanties alvorens de configuratiemanager in werking te stellen. (CQDOC-20803)

#### Installeer het serverfragment (AEM Service Pack 6.5.14.0 of eerder)

* Als u aan AEM Service Pack 6.5.15.0 of hoger bevordert, en uw AEM instantie werkt op Tomcat 8.5.88, is het verplicht dat u het servletfragment installeert. Deze installatie uitvoeren *voor* u gaat verder met de installatie van Service Pack 6.5.15.0 of hoger.
* Het is verplicht het servletfragment te installeren voor alle toepassingsservers behalve voor servers die op JBoss® EAP 7.4.0 worden uitgevoerd.

**U installeert als volgt het servletfragment:**

1. Het serverfragment downloaden van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar).
1. Start de toepassingsserver.
1. Wacht tot de logbestanden zijn gestabiliseerd en controleer de toestand van de bundel.
1. Open Web Console-bundels. De standaard-URL is `http://[Server]:[Port]/system/console/bundles`.
1. Selecteren **[!UICONTROL Install]** of **[!UICONTROL Update]**.
1. Het gedownloade fragment selecteren
   `org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar`
1. Selecteren **[!UICONTROL Install]** of **[!UICONTROL Update]**.
1. Wacht tot de toepassingsserver is gestabiliseerd.
1. Stop de toepassingsserver.

#### Adaptieve Forms

* Wanneer een adaptief formulier wordt gepubliceerd, worden alle afhankelijkheden, inclusief het beleid, opnieuw gepubliceerd, zelfs als er geen wijzigingen in zijn aangebracht. (FORMS-10454)
* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.
* Wanneer gebruikers de verzendactie uitvoeren, mislukt de verzending met een fout:
  `javax.servlet.ServletException: java.lang.NoSuchMethodError`
Om het probleem op te lossen, [Compileer de Sling-scripts, zoals JSP, Java™ en Sighy opnieuw](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html#resolution). (FORMS-8542)
* Na het installeren van AEM Service Pack 6.5.14.0 en daarna, kunnen de gebruikers geen doopvont van JEE Admin UI voor de documenten van PDF selecteren wanneer het navigeren aan `Home` > `Services` > `PDF Generator` > `Adobe PDF Settings`, omdat de lettertypenlijst leeg lijkt. (FORMS-12095)
<!-- When a form is signed using the OOTB Scribble Signature component, it appears in the image dialogue but does not preview and appears blank when you click on it. (FORMS-12073). A hotfix is available for this issue. To download and install the hotfix, see [Adobe Experience Manager Forms Hotfixes](/help/release-notes/aem-forms-hotfix.md) -->
* In AEM Forms op JEE kan de HTML5 Forms die het contextpad gebruikt, niet renderen. (FORMS-12485, FORMS-12691). Er is een hotfix beschikbaar voor dit probleem. Zie voor informatie over het downloaden en installeren van de hotfix [Adobe Experience Manager Forms Hotfixes](/help/release-notes/aem-forms-hotfix.md).
* Met Adaptive Forms kunt u aangepaste functies gebruiken met ECMAScript versie 5 of lager. Wanneer een douanefunctie ECMAScript versie 6 of later, zoals &quot;laat&quot;, &quot;const&quot;, of pijlfuncties gebruikt, zou de regelredacteur niet behoorlijk kunnen openen.

#### AEM Forms op JEE

* Er zijn kritieke beveiligingskwetsbaarheden gemeld voor Struts 2 RCE, een populair en open-source webtoepassingsframework voor het ontwikkelen van Java™ EE-webtoepassingen. Adobe is vrijgegeven [AEM 6.5 Service Pack 19.1 (6.5.19.1)](/help/forms/using/mitigating-struts-2-rce-vulnerabilities-for-experience-manager-manager-form.md) om de kwetsbaarheid in AEM Forms op JEE te verhelpen.

<!--The font enumeration fails due to the missing Ps2Pdf service file.-->

## OSGi-bundels en inhoudspakketten inbegrepen{#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in dit [!DNL Experience Manager] 6.5 Service Pack-release:

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.20.0](/help/release-notes/assets/65200-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lijst met inhoudspakketten opgenomen in Experience Manager 6.5.20.0](/help/release-notes/assets/65200-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw accountmanager van de Adobe.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Contact opnemen met de klantenondersteuning van de Adobe](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op Adobe prioritaire productupdates](https://www.adobe.com/subscription/priority-product-update.html)
