---
title: Opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: Zoek naar releasegegevens, wat is nieuw, installeer hoe kan worden gewijzigd en een gedetailleerde wijzigingslijst voor [!DNL Adobe Experience Manager] 6.5
mini-toc-levels: 4
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 6bf2d6409a15be02a247fab84caa743e8542da13
workflow-type: tm+mt
source-wordcount: '3009'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Laatste Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in this release information, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, November 30, 2023. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.21.0. <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Datum | Donderdag 6 juni 2024 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.21.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.21.0. {#what-is-included-in-aem-6521}

[!DNL Experience Manager] 6.5.21.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en insectenmoeilijke situaties. Het omvat ook prestaties, stabiliteit, en veiligheidsverbeteringen die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 worden vrijgegeven. [Dit Service Pack installeren](#install) op [!DNL Experience Manager] 6.5

<!-- UPDATE FOR EACH NEW RELEASE -->

## Belangrijke functies en verbeteringen

<!-- * _6.5.21.0 REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Enkele belangrijke functies en verbeteringen in deze release zijn onder andere:

* Een nieuwe en eenvoudigere referentie voor server-aan-server authentificatie, die de bestaande referentie van de Rekening van de Dienst (JWT) vervangt. (NPR-41994)

### [!DNL Assets]

#### Verbeteringen

Hier volgt een lijst met verbeteringen die zijn opgenomen in deze release:

* Het IPTC-tabblad wordt nu ondersteund [!UICONTROL Alt Text] en [!UICONTROL Extended Description] tekstvelden. (ACTIVA-34918)

#### Oplossingen voor toegankelijkheid

Hieronder volgt een lijst met toegankelijkheidsoplossingen in deze release:

* Als de verwerkingsstatus van een element is mislukt of Metagegevens zijn mislukt, werkt de interface voor bijschriften en audiotracks niet correct. (ACTIVA-37281)
* Wanneer u metagegevens van middelen opslaat en deze probeert te bewerken, wordt de taalnaam niet weergegeven. (ACTIVA-37281)

<!-- ### [!DNL Forms]
* A -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## Opgeloste problemen in Service Pack 21 {#fixed-issues}

### [!DNL Sites]{#sites-6521}

#### Toegankelijkheid {#sites-accessibility-6521}

* De **[!UICONTROL Saved Searches]** label is niet blijvend. De tijdelijke aanduiding wordt gebruikt als het enige visuele label voor een tekstveld. (SITES-3050)

#### Gebruikersinterface Admin{#sites-adminui-6521}

* Wanneer u op **[!UICONTROL Sites]** > **[!UICONTROL Core Core Components]** > **[!UICONTROL Properties]** > **[!UICONTROL Permissions]** tab > **[!UICONTROL Effective Permission]** de **Effectieve machtigingen** wordt niet geopend in. (SITES-17378)

<!-- #### Classic UI{#sites-classicui-6521} 

* A -->

#### [!DNL Content Fragments]{#sites-contentfragments-6521}

* Oplossing voor de dubbele opname van de formulierelementen. (SITES-21109)
* Wanneer u een inhoudsfragment maakt, reageert de knop Sluiten soms niet meer, waardoor de hele pagina vastloopt en de pagina moet worden vernieuwd om het inhoudsfragment te sluiten. Het systeem maakt momenteel een nieuwe versie van een inhoudsfragment. Deze kwestie komt zelfs voor wanneer de gebruiker geen veranderingen heeft aangebracht, eenvoudig door met RTE of een tekstgebied in wisselwerking te staan. (SITES-21187)

#### [!DNL Content Fragments] - GRAPHQL API {#sites-graphql-api-6521}

* Tijdens het upgraden van Adobe Experience Manager van 6.5.19.0 naar 6.5.20.0, wordt het pad `/libs/cq/graphql/sites/graphiql` werd verwijderd. (SITES-20098)

<!-- #### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-6521}

* W -->

<!-- #### [!DNL Content Fragments] - REST API{#sites-restapi-6521}

* W -->

<!-- #### Core Backend{#sites-core-backend-6521}

* W -->

<!-- #### Core Components{#sites-core-components-6521}

* I -->

<!-- #### Campaign integration{#sites-campaign-integration-6521}

* A -->

#### Ervaar fragmenten{#sites-experiencefragments-6521}

* Uitrol van ervaringsfragmenten uit `masters/language` tot `country/language` werkt kruisverwijzingen niet bij. (SITES-21172)
* Niet alleen in de sectie `cq:allowedTemplates`, maar sjablonen met `allowedPaths` geconfigureerd op sjabloonniveau, worden weergegeven als opties bij het maken van een nieuw ervaringsfragment. (SITES-20855)

<!-- #### Foundation Components (Legacy){#sites-foundation-components-legacy-6521}

* T -->

<!-- #### Launches{#sites-launches-6521} -->

<!-- DELETED MAY 22, 2024 FROM TOTAL RELEASE CANDIDATE ISSUES * The `sourceRootResource` configured in the Launch configuration within CRXDE Lite points to content that no longer exists, leading to a malfunction when attempts are made to delete launches. Delete launches even if the page is deleted or if the path is not the same. (SITES-20750) -->

#### MSM - Actieve kopieën{#sites-msm-live-copies-6521}

* De component Pagina wordt bedekt om tabbladen toe te voegen in pagina-eigenschappen. Een van deze fragmenten is paginaconfiguratie en heeft een eigenschap om een URL van het fragment van de ervaring toe te voegen. De koppeling die in de pagina-eigenschappen voor het ervaringsfragment wordt geconfigureerd, wordt niet gewijzigd voor alle taalkopieën die voor die pagina worden gemaakt. De gevormde verbinding zou met het taalexemplaar URL moeten veranderen. (SITES-19580)

#### Pagina-editor{#sites-pageeditor-6521}

* In de bewerkingsmodus wordt een grijze achtergrond inconsistent toegepast, omdat deze niet voldoet aan de WCAG-standaarden (Web Content Accessibility Guidelines) voor kleurcontrast. (SITES-20060)

### [!DNL Assets]{#assets-6521}

* Als een middel naar Brand Portal wordt gepubliceerd, blijft de publicatiestatus inconsistent. (ACTIVA-36807)
* Elementen worden niet verwijderd wanneer u ze uit een instantie verwijdert via een API-aanroep. (ACTIVA-35131)
* Wanneer u metagegevens probeert te importeren, kunt u een `question mark (?)` vervangt de invoeging van tekens in een andere taal dan het Engels.  (ACTIVA-35091)
* Wanneer `dc:title` eigenschap wordt gebruikt bij een tekenreeks met het gegevenstype data, de structuur met de inhoud van de elementen werkt niet naar behoren na de installatie van Service Pack 6.5.19. (ACTIVA-34684)
* Er wordt een fout weergegeven als de naam van een element een speciaal teken bevat. (ACTIVA-33248)

#### [!DNL Dynamic Media]{#assets-dm-6521}

* In AEM 6.5.18 worden niet alle hotspots weergegeven die aan een element zijn toegevoegd wanneer u de hotspots bewerkt. Alle hotspots werken echter in een gepubliceerd middel, maar u kunt ze later niet bewerken als dat nodig is. (ACTIVA-33609)
* De meest recente EPS-bestanden die worden geüpload, genereren geen miniaturen nadat ze opnieuw zijn verwerkt. (ACTIVA-32617)
* Kies in Gereedschappen > Middelen > Dynamic Media Publication > Request Attributes tab de invoer `Width(px)` en `Height(px)` ziet er anders uit in het Spaans, Italiaans en Portugees. Voor deze locaties worden ze niet met elkaar uitgelijnd. (ACTIVA-31896)
* Vanaf 1 mei 2024 beëindigde Adobe Dynamic Media de ondersteuning voor:
   * SSL (Secure Socket Layer) 2.0
   * SSL 3.0
   * TLS (Transport Layer Security) 1.0 en 1.1
   * De volgende zwakke ciphers in TLS 1.2:
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384`
      * `TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_RSA_WITH_AES_256_GCM_SHA384`
      * `TLS_RSA_WITH_AES_256_CBC_SHA256`
      * `TLS_RSA_WITH_AES_256_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_AES_128_GCM_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA256`
      * `TLS_RSA_WITH_AES_128_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_256_CBC_SHA`
      * `TLS_RSA_WITH_CAMELLIA_128_CBC_SHA`
      * `TLS_ECDHE_RSA_WITH_3DES_EDE_CBC_SHA`
      * `TLS_RSA_WITH_SDES_EDE_CBC_SHA`

### [!DNL Forms]{#forms-6521}

Oplossingen in [!DNL Experience Manager] Forms wordt één week na de geplande levering geleverd via een afzonderlijk invoegpakket [!DNL Experience Manager] Releasedatum van Service Pack. In dit geval is de AEM 6.5.21.0 Forms-invoegtoepassing gepland voor donderdag 13 juni 2024. Er wordt een lijst met Forms-correcties en -verbeteringen toegevoegd aan deze sectie na de release.

<!-- #### [!DNL Adaptive Forms]

* THIS BUG WAS ALREADY REPORTED IN THE 6.5.20.0 RELEASE NOTES. IS IT NEEDED AGAIN IN THE 6.5.21.0 RELEASE NOTES? (AEM Forms on JEE Only) The PDF Generator service fails to enumerate the fonts available on the server. Consequently, the font selection panel on the Adobe PDF Settings page in the PDFG Admin UI remains empty, effectively preventing (un)embedding of chosen fonts. (FORMS-12095) -->


<!-- #### [!DNL Forms Designer] {#forms-designer-6521}

* W -->

### Stichting {#foundation-6521}

#### Apache Felix {#foundation-apachefelix-6521}

* De kwestie van de verbetering met AEM 6.5 Service Pack 19 (SP19) waarin de de servercontext-wortelweg van de Toepassing voor ongeoorloofde verzoeken aan Apache Felix na de installatie van SP19 mist. Update naar Apache Felix Web Management Console 4.9.8. (NPR-41933)

#### Campagne{#foundation-campaign-6521}

* AEM 6.5 Service Pack 15 produceert ononderbroken foutenlogboeken met significante ingangen. De volgende problemen zijn gemeld:

   * 404 INFO-fout voor ontbrekende resource op pad `/libs/granite/ui/content/shell/start.html`
   * Foutlogbestandvermelding voor een niet-afgevangen SlingException vanwege `NullPointerException` om `CampaignsDataSourceServlet.java:147`

  Foutenlogbestanden moeten niet worden gevuld met frequente en omvangrijke foutmeldingen en de AEM instantie moet werken zonder problemen met betrekking tot ontbrekende bronnen of uitzonderingen. (CQ-4357064)

#### Cloud Servicen{#foundation-cloudservices-6521}

* Verwijder Google Guava uit AEM Cloud Servicen. (CQ-4356436)

<!-- #### Communities {#foundation-communities-6521}

* U -->

<!-- #### Content distribution{#foundation-content-distribution-6521}

* T -->

#### Graniet{#foundation-granite-6521}

* U kunt niet **Verwijderen** of **Wijzigen** zonder **Bladeren** toestemming in browser van de Configuratie. (GRANITE-51002)

#### Integrations{#foundation-integrations-6521}

* Betreffende `cq-target-integration`moet niet-testgebruik van Google Guava worden verwijderd. (CQ-4357101)
* Vervanging van de geloofsbrieven van de Rekening van de Dienst (JSON Web Token of JWT) met OAuth2 server-aan-Server (ook genoemd geworden Belangrijkste die als de Dienst). (NPR-41994)
* Aanvraag voor publiek maken mislukt bij configuratie IMS (Identity Management System). (NPR-41888)
* Wanneer een klant de pagina Payload probeert weer te geven, wordt de inhoud niet correct weergegeven als gevolg van een onjuiste URL. Er wordt een fout van 404 weergegeven. De fout is veroorzaakt door een ontbrekend symbool van het vraagteken in de URL, vóór de queryparameters. Voor dit probleem moet de klant het symbool van het vraagteken invoegen om de pagina Payload correct weer te geven. (NPR-41957)
* Verwijder code en afhankelijkheid van Adobe Search&amp;Promote van AEM 6.5, die eind van leven op bereikte [september 2022 volgens opzegtermijn](https://experienceleague.adobe.com/en/docs/discontinued/using/search-promote). (NPR-41855)

#### Lokalisatie{#foundation-localization-6521}

* In de redacteur van Malplaatjes, het tekstkoord *`No video available.`* is niet gelokaliseerd. (SITES-13190)
* Tekenreeks na activering of deactivering van een gebruiker wordt niet gelokaliseerd in **Gereedschappen** > **Beveiliging** > **Gebruikers** > *any_user_name* > **Activeren** > **OK** en selecteert u *any_user_name* > **Deactiveren** > **OK**. (NPR-41737)

#### Platform{#foundation-platform-6521}

* De `Unclosed resource resolver` fout wordt ervaren voor `com.day.cq.mailer.impl.DefaultMailService`. De `MessageGatewayService` de klasse, die uit-van-de-doos is, werd gebruikt zonder middeloplosser. De uitgave is opgetreden op elke pagina met een knop voor het verzenden van formulieren die een e-mail verzendt met deze klasse. (NPR-41853)
* In de **Informatie over Adobe Experience Manager** het copyrightjaar is nog steeds 2023 . (CQ-4356349)


<!-- #### Sling{#foundation-sling-6521}

* T -->

#### Vertaling{#foundation-translation-6521}

* Een probleem met AEM 6.5.19 uit-van-de-doos vertaalstatus die niet zoals verwacht voor een lancering bijwerkt. Na het importeren van een vertaald bestand in een vertaaltaak die is gekoppeld aan een AEM-opstart, werd verwacht dat de status zou veranderen in `Approved`. In plaats daarvan is de status gewijzigd in `Ready for Review`, wat niet het verwachte gedrag is. (NPR-41756)
* Wanneer het creëren van veelvoudige configuraties en het gaan naar de configuraties van de Cloud Servicen van de Vertaling, niet worden alle elementen getoond in UI. Alleen de eerste 40 elementen/map worden weergegeven. Het laden wordt vertraagd, maar er wordt geen inhoud toegevoegd. (NPR-41829)
* Er treden onjuiste tekens op als de machtigingspagina in de Touch-gebruikersinterface Japans bevat. (NPR-41794)
* AEM 6.5.14 en 6.5.9 verzenden geen emoji voor vertaling. (CQ-4357000)

#### Gebruikersinterface{#foundation-ui-6521}

* In Gereedschappen > Beveiliging > Gebruikers > &lt;user_name> > Profielen, in het dialoogvenster **Gebruikersinstellingen bewerken** als u op Annuleren klikt, wordt het dialoogvenster niet gesloten. (NPR-41793)
* Graniet `pathfield` component bij `/libs/granite/ui/components/coral/foundation/form/pathfield` kan de **[!UICONTROL Select]** als een element is geselecteerd. Nadat het veld Pad is uitgevouwen en de gebruiker het selectievakje voor het element heeft ingeschakeld, wordt het **[!UICONTROL Select]** is niet ingeschakeld, maar verandert niet van grijs in blauw. (NPR-41970)
* Er is een probleem met het referentieveld CFM (Content Fragment Model) in AEM. Hoewel het CFM-referentieveld is ingesteld als verplicht, kunnen gebruikers met het systeem op Opslaan klikken om inhoud met niet-CFM-waarden in bepaalde scenario&#39;s op te slaan. De knop Opslaan moet grijs worden weergegeven (niet beschikbaar). (NPR-41894)
* De standaarddialoogvensters van de Coral-gebruikersinterface die de `successresponse` Actie moet een Succesreactie na de actie teweegbrengen. Maar in AEM 6.5 Service Pack 19, wordt de herladenactie niet aangehaald en geen bericht wordt getoond. (NPR-41797)
* AEM de verbindingen van Berichten werken niet in AEM 6.5 Service Pack 18. Wanneer het bevorderen aan Service Pack 18, werken de verbindingen van de Berichten van de AEM niet wanneer het selecteren van de berichten als berichtenknoop. (NPR-41792)

<!-- #### WCM{#foundation-wcm-6521}

* T -->

#### Workflow{#foundation-workflow-6521}

* In AEM 6.5.18 worden tijdens het leegmaken herhaalde fouten aangetroffen in het verwijderen uit de cache van metagegevens van de gebruiker. (NPR-41762)

## Installeren [!DNL Experience Manager] 6.5.21.0.{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.21.0 vereist [!DNL Experience Manager] 6.5. Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies. <!-- UPDATE FOR EACH NEW RELEASE -->
* De download Service Pack is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.21.0.zip).
* Bij een implementatie met MongoDB en meerdere exemplaren, installeert u [!DNL Experience Manager] 6.5.21.0 op één van de instanties van de Auteur die de Manager van het Pakket gebruiken.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe raadt u niet aan de [!DNL Experience Manager] 6.5.21.0-pakket. Voordat u het pakket installeert, moet u daarom een back-up maken van het `crx-repository` voor het geval u het terug moet rollen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for Experience Manager Forms, see [Experience Manager Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Service Pack installeren op [!DNL Experience Manager] 6,5{#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download de servicesack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.21.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en selecteer **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het Service Pack. De Adobe adviseert dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installatie succesvol is. Dit probleem treedt meestal op in het dialoogvenster [!DNL Safari] browser, maar kan soms voorkomen in om het even welke browser.

**Automatische installatie**

Er zijn twee verschillende methoden die u kunt gebruiken om te installeren [!DNL Experience Manager] 6.5.21.0.<!-- UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Experience Manager 6.5.21.0 ondersteunt geen installatie van Bootstrappen. <!-- UPDATE FOR EACH NEW RELEASE -->

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (6.5.21.0)` krachtens [!UICONTROL Installed Products]. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-pakketten zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.2.20 of hoger (webconsole gebruiken: `/system/console/bundles`). <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Service Pack installeren voor [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Voor instructies voor het installeren van het Service Pack op Experience Manager Forms raadpleegt u [Installatie-instructies voor Experience Manager Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

>[!NOTE]
>
>De functie Adaptive Forms is beschikbaar in [AEM 6.5 QuickStart](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/deploying/deploy), is uitsluitend ontworpen voor exploratie en evaluatie. Voor productiegebruik is het van essentieel belang een geldige licentie voor AEM Forms te verkrijgen, aangezien voor de adaptieve Forms-functionaliteit een correcte licentie vereist is.

### GraphQL-indexpakket voor Experience Manager-inhoudsfragmenten installeren{#install-aem-graphql-index-add-on-package}

Klanten die GraphQL gebruiken, moeten de [Experience Manager-inhoudsfragment met GraphQL Index-pakket 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip).

Zo kunt u de vereiste indexdefinitie toevoegen op basis van de functies die ze daadwerkelijk gebruiken.

Als u dit pakket niet installeert, kan dit leiden tot trage of mislukte GraphQL-query&#39;s.

>[!NOTE]
>
>Installeer dit pakket slechts eenmaal per instantie; het hoeft niet opnieuw te worden geïnstalleerd met elk Service Pack.

### UberJar{#uber-jar}

The UberJar for [!DNL Experience Manager] 6.5.21.0 is beschikbaar in de [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.21/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
  <dependency>
  <groupId>com.adobe.aem</groupId>
  <artifactId>uber-jar</artifactId>
  <version>6.5.21</version>
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

* Wanneer u probeert inhoudsfragmenten, sites of pagina&#39;s te verplaatsen, te verwijderen of te publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald. De achtergrondquery is mislukt. De functionaliteit werkt dus niet.
Om correcte verrichting te verzekeren, moet u de volgende eigenschappen aan de knoop van de indexdefinitie toevoegen `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

  ```xml
  "tags": [
      "visualSimilaritySearch"
    ]
  "refresh": true
  ```

* Als u uw [!DNL Experience Manager] -exemplaar van 6.5.0 - 6.5.4 naar het nieuwste Service Pack op Java™ 11, zie `RRD4JReporter` uitzonderingen in de `error.log` bestand. Als u de uitzonderingen wilt stoppen, start u de instantie van [!DNL Experience Manager]. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De maptitel wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] Als u de standaard-API (IMS-verificatie) van het doel gebruikt, leidt het exporteren van ervaringsfragmenten naar Doel tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` : Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging register is niet-geregistreerd.

* Vanaf AEM 6.5.15 wordt de Rhino JavaScript Engine geleverd door de ```org.apache.servicemix.bundles.rhino``` bundle heeft een nieuw hoistinggedrag. Scripts die de strikte modus gebruiken (```use strict;```) moeten de juiste variabelen aangeven. Anders worden ze niet uitgevoerd en wordt er een runtimefout gegenereerd.

* Als u labelen van verwant kant-en-klare inhoud via een officieel updatepakket installeert, wordt de eigenschap languages van het deelvenster `/content/cq:tags` node to default. Deze actie is waar voor de Packs van de Dienst, de Pakketten van de Dienst van de Veiligheid, de Uitgebreide Packs van de Eigenschap, de Cumulatieve Packs van de Eigenschap, de flarden, etc. Daarom is het noodzakelijk om het uit de eigenschappen vóór installatie toe te voegen.

### Bekend probleem voor AEM Sites {#known-issues-aem-sites-6521}

* SITES-17934 - Inhoudsfragmenten - Voorvertoning mislukt vanwege DoS-bescherming voor grote boomstructuur met fragmenten. Zie de [KB-artikel over configuratieopties voor standaard GraphQL Query Exec](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-23945)

### Bekende problemen voor AEM Forms {#known-issues-aem-forms-6521}

* In een adaptief formulier dat is gebaseerd op een XDP met ingesloten scripts in selectievakjes, worden de scripts niet uitgevoerd voor elementen na dergelijke selectievakjes. (FORMS-14244)
* Gebruikers kunnen geen correspondentiebeheerbrief maken. Wanneer een gebruiker een brief creeert, een fout met beschrijving &quot;`Object Object`&quot; weergegeven en de letter is niet gemaakt. Miniaturen voor lay-outs kunnen ook niet worden geladen op het scherm voor het maken van letters. U kunt de [nieuwste AEM 6.5 Form Service Pack 20 (6.5.20.0)](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) om het probleem op te lossen. (FORMS-13496)
* De dienst Interactive Communications maakt het PDF-document, maar de gegevens van de gebruiker worden niet automatisch ingevuld in de formuliervelden. De Prefill-service werkt niet zoals u had verwacht. U kunt de [nieuwste AEM 6.5 Form Service Pack 20 (6.5.20.0)](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) om het probleem op te lossen. (FORMS-13413, FORMS-13493)
* De controle en Correct (RnC) redacteur van de dienst van de automatede form conversion kan niet laden. U kunt de [nieuwste AEM 6.5 Form Service Pack 20 (6.5.20.0)](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) om het probleem op te lossen. (FORMS-13491)
* Na het bijwerken van AEM 6.5 Forms Service Pack 18 (6.5.18.0) of AEM 6.5 Forms Service Pack 19 (6.5.19.0) aan AEM 6.5 Forms Service Pack 20 (6.5.20.0), ontmoeten de gebruikers een fout van de JSP compilatie. Ze kunnen geen adaptieve formulieren openen of maken en fouten met andere AEM interfaces, zoals de pagina-editor, de AEM Forms-gebruikersinterface en de AEM Workfloweditor. U kunt de [nieuwste AEM 6.5 Form Service Pack 20 (6.5.20.0)](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) om het probleem op te lossen. (FORMS-13492)
* Rijen in de datumkiezer-widget worden afgebroken tijdens het doorlopen van maanden in de pop-upwidget voor velden met het bewerkings-/weergavepatroon. (FORMS-13620)
* Formulierverzendingen mislukken wanneer wordt geprobeerd de DOR-service (Document of Record) op de achtergrond te gebruiken. Het foutbericht dat wordt aangetroffen, is: &quot;Handeling verzenden kan niet worden voltooid omdat de formulierbron niet correct is toegewezen.&quot; (FORMS-13798)
* Wanneer een adaptief formulier van een Adobe Experience Manager-publicatie-instantie naar een Adobe Experience Manager-workflow wordt verzonden, kunnen de bijlagen niet in de workflow worden opgeslagen. (FORMS-14209)
* Bij het installeren van AEM 6.5 Forms Service Pack 20-pakket (AEM Forms add-on pakket voor SP20), vertoont de AEM Sites-gebruikersinterface (UI) een aanzienlijke verslechtering van de prestaties. (FORMS-13791)
* De prefill dienst ontbreekt met een ongeldige wijzeruitzondering in Interactieve Mededelingen. (CQDOC-21355)
* Met Adaptive Forms kunt u aangepaste functies gebruiken met ECMAScript versie 5 of lager. Wanneer een aangepaste functie ECMAScript versie 6 of hoger gebruikt, zoals `let`, `const`, of pijlfuncties, de regelredacteur zou niet behoorlijk kunnen openen.

## OSGi-bundels en inhoudspakketten inbegrepen{#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in dit [!DNL Experience Manager] 6.5 Service Pack-release:

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.21.0](/help/release-notes/assets/65210-bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lijst met inhoudspakketten opgenomen in Experience Manager 6.5.21.0](/help/release-notes/assets/65210-packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw accountmanager van de Adobe.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Contact opnemen met de klantenondersteuning van de Adobe](https://experienceleague.adobe.com/en/docs/customer-one/using/home).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/en/docs/experience-manager-65)
>* [Abonneren op Adobe Priority-productupdates](https://www.adobe.com/subscription/priority-product-update.html)

