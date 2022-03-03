---
title: ' [!DNL Adobe Experience Manager] '
description: '[!DNL Adobe Experience Manager]'
exl-id: 0288aa12-8d9d-4cec-9a91-7a4194dd280a
source-git-commit: 37e7f2552ae712bc23eb3ce1af1b41808f4d1810
workflow-type: tm+mt
source-wordcount: '2633'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] {#aem-service-pack-release-notes}

## Release information {#release-information}

| Producten | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Versie | 6.5.12.0 |
| Type | Service Pack Release |
| Date | February 24, 2022 |
| Download URL | [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.12.0.zip) |

## [!DNL Adobe Experience Manager] {#what-is-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.12.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het de dienstpak wordt geïnstalleerd op [!DNL Adobe Experience Manager] 6.5

De belangrijkste functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.12.0 zijn:

* Nadat u een verbinding tussen externe DAM- en Sites-implementaties hebt geconfigureerd, worden de middelen op externe DAM beschikbaar gesteld op de implementatie van Sites. U kunt de update uitvoeren, verwijderen, hernoemen en bewerkingen verplaatsen op de externe DAM-middelen of -mappen. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen (NPR-37816).

* Push-rollouts van een live-kopiebron naar meerdere live kopieën is nu standaard mogelijk, zonder dat een blauwdrukconfiguratie nodig is (CQ-4259951).
* The status of in-progress async operations is now shown in the user interface to help prevent users from accidentally triggering multiple async operations on the same path (NPR-37611).
* Support for IMS-based authentication is provided for Analytics 2.0 APIs (CQ-4285474, NPR-37803, NPR-37701, NPR-37702, NPR-37703).
* API support for JSON offer type experience fragment (NPR-37796).
* Offer request is now provided for Delete offer (Experience Fragment API) in IMS (NPR-37668).
* The built-in repository (Apache Jackrabbit Oak) still remains at 1.22.9.

[!DNL Experience Manager]

### [!DNL Sites] {#sites-65120}

[!DNL Sites]

* Layout of the content fragment Properties is broken as Basic and Advance tabs have no margins to the left (SITES-4484).
* Option to close banner on content fragments, that are referenced on various sites pages, is not working. This banner informs the users that the content fragment is referenced on one or more pages (SITES-4173).
* The checkboxes are not aligned in Revert Inheritance dialog box (SITES-3514).
* The template page on we-retail and wknd sites is broken, as components don&#39;t load and structure option is not available, as pageinfo.json servlet is stuck on LaunchManagerImpl.getLaunchStream (SITES-3489).
* User node publishing from Author to Publish environment is not working (NPR-38005).
* Attempt to create an experience fragment using an edited template doesn’t show the edits made to the initial page properties (NPR-37962).
* The page move operation on Experience Manager is slow (NPR-37961).
* Experience fragment translation does not update references to language copy paths (NPR-37953).
* Users without replication permissions are not able to delete or move pages, even if the pages are not activated (NPR-37936).
* Random org.apache.felix.metatype errors are observed on server (NPR-37935).
* References in Sites admin touch user interface are not displaying incoming links correctly (NPR-37934).
* Launch path to add new pages or assets is not available when selecting pages in a translation job (NPR-37912).
* Reference pages in a list component added in experience fragments are not updated to destination page when promoting the launch (NPR-37886).
* Author environment has user interface issues—such as Edit mode page title is not centered and allowed components selector on policy editor: group checkbox takes entire width of the container, so the label is rendered in the next line (NPR-37878).
* []
* Errors are observed and pages fail to move when trying to a page (NPR-37864).
* []
* Authors are able to apply tags that are outside of the configured root path when using tag field in a dialog(NPR-37834).
* Multifield does not render correctly in layout container and gives error (NPR-37811).
* Attempt to resize component layout in page editor doesn’t work in mobile layout (NPR-37805).
* Experience Fragment translation does not update cyclic references to language copy paths (NPR-37745).
* Use of cq-msm-lockable rich text field in page properties does not disable the field on rolling out the page and it can be modified by the authors (NPR-37714).
* On activating an experience fragment, publisher sends many activation requests to Dispatcher (NPR-37707).
* On topology change, the Sling job for asset processing gets reset resulting in the jobs that are in progress at the time of topology change getting ignored (NPR-37706).
* Quotation marks, cross, and dash are not exported to CSV when users of MacOS export sites and assets URLs (NPR-37698).
* Layout container in SPA page template is not able to register the custom CSS classes defined in the Template Policy when running react SPA pages (NPR-37697).
* Background image is not visible when user selects targeting on an experience fragment that has background in the container (NPR-37662).
* Translation job on an experience fragment is not translating all the components on that experience fragment (NPR-37660).
* Translation of experience fragments and the page containing the experience fragment does not update the launch path in the experience fragment link (NPR-37659).
* File Upload widget does not show the file name, when a file is uploaded, and dialog is saved (NPR-37634).
* The scheduled activation (publishing) of asset does not trigger on the scheduled time if the folder containing that asset is moved (NPR-37621).
* [][!DNL Adobe Experience Manager]
* Content fragment editor does not work correctly when capital case letters are used in tag names when editing tags in the editor (NPR-37601).
* Classic user interface editor doesn&#39;t show mark up as in compare view of touch user interface (NPR-37588).
* Intermittent 500 error is logged on adding an experience fragment to translation jobs (NPR-37587).
* Authors are able to select and use date picker date even on disabled date picker (NPR-37583).
* []
* The paths in libs folder get deleted on installing previous service packs (NPR-36815).
* [][!DNL Experience Manager Commerce]
* [][!DNL Adobe Experience Manager]
* []
* []
* [][!DNL Experience Manager][!DNL Adobe Experience Manager]

### [!DNL Assets] {#assets-65120}

<!--
The following accessibility enhancements are available in [!DNL Assets]:

* enhancement 1
-->

[!DNL Assets]

* `single quote`
* When adding watermark to an asset, the watermark is always displayed in black color irrespective of the color defined by the user (NPR-37720).
* When using Connected Assets, a non-admin user is able to search for an asset even when the non-admin users are restricted to access the DAM repository (NPR-37644).
* Wanneer u metagegevens van elementen bijwerkt met behulp van bulkbewerking, worden de wijzigingen die zijn toegepast op de vervolgkeuzelijsten niet opgeslagen en teruggezet naar de standaardwaarden (NPR-37345).
* Het verwijderen van een map in een te lange periode die invloed heeft op de algehele prestaties (NPR-37107).
* Wanneer de gebruiker regels toepast in meta-gegevensschema, kan de gebruiker niet de volledige waarde voor dropdown bekijken `Field Value` en `Field Choices` als de waarde groter is dan het tekstvak (CQ-4338074).
* Na de upgrade naar versie 6.5.10.0 geeft de pagina met elementeigenschappen een weerspiegeling van een onnodig HTML-renderingbericht (CQ-4336994).
* Elementen sorteren in `List View` werkt niet effectief (CQ-4335298).
* Wanneer u elementen deelt via een koppeling voor delen, worden de elementen gedownload in aparte mappen (CQ-4335000).
* [!DNL Experience Manager]`Inbox``Share``Out of office`

* The following fixes are related to cascading metadata in asset properties.
   * A mandatory dropdown reflects multiple error messages for each selection in the multivalue field (NPR-37859).
   * Only the last selection of the parent field is saved for the dependent uneditable field (NPR-37858).
   * The dependent dropdown (multivalue field) reflects the default value intermittently for the selected parent dropdown (NPR-37791).


### [!DNL Dynamic Media] {#dynamic-media-65120}

[!DNL Dynamic Media]

* `renditions``Dynamic Media`
* `tiff``jpeg`
* `Progressive JPEG Scan``auto`
* `mxf`
* When reprocessing the video assets, the AVS (Adaptive Video Set) and video renditions are unpublished from the Publish server (CQ-4335461).
* De gegenereerde miniaturen van PDF zijn anders dan de eerste pagina van de werkelijke PDF. Sommige delen van de afbeelding ontbreken in de miniatuur (CQ-4315554).
* CDN-validatie mislukt als de URL niet goed reageert `companyName` en `companyRoot` verschillen (CQ-4339896).

### Workflows {#workflows-65120}

* Schuiven werkt niet zoals verwacht als u een filter toepast op items in Postvak IN (CQ-4333594).


### [!DNL Forms] {#forms-65120}


>[!NOTE]
>
>* [!DNL Experience Manager Forms] geeft toe:voegen-on pakketten één week na gepland vrij [!DNL Experience Manager] Releasedatum van Service Pack.


<!--

**Adaptive Forms**

* Accessibility – When you set the `Wizard` layout for a panel in an adaptive form, the navigation buttons do not have Aria labels and role (NPR-37613).

* Validations on a date field in an adaptive form does not work, as expected (NPR-37556).

* When the label text for the Checkbox and Radio Button components is long, the text does not fit appropriately (NPR-37294).

* When you apply styling changes to the Thank You message of the AEM Forms Container component, the changes do not replicate in the source adaptive form (NPR-37284).

* Differences in the value of the `Switch` component on the user interface and in the backend (NPR-37268).

* When you use the keyboard keys to navigate to the `Submit` option and press the `Enter` key, you can submit the adaptive form multiple times (CQ-4333993).

* The Remove operation for the File Attachment component does not work, as expected (NPR-37376).

* When a label for a field exceeds 1000 characters in an adaptive form that translates to various languages, the dictionary fails to retrieve the translation of the label (CQ-4329290).

**Document Services**

* An error displays while using the Assembler service (NPR-37606):

  ```TXT
    500 Internal Server Error
  ```

* When the document attachments are passed to the Assembler service, the following exception displays (NPR-37582):

  ```TXT
    com.adobe.livecycle.assembler.client.ProcessingException: ⁪: Failed to execute the DDX
  ```

* Missing closing parenthesis from data after converting a PDF document to a PDF-A/1B PDF document (NPR-37608).

**HTML5 Forms**

* When you install AEM 6.5.10.0, the HTML preview for an XDP form does not work (NPR-37503, CQ-4331926).

* Text overlapping issues while migrating the PDF forms to HTML 5 forms in various languages (NPR-37173).

**Letters**

* When you submit a letter and reopen it in HTML view, the position of text document fragments does not remain the same (NPR-37307).

**Forms Workflow**

* In case of embedded container workflow, you get multiple workflow completion emails even after selecting the `Notify on Complete of Container Workflow` option (NPR-37280).

**Foundation JEE**

* After installing AEM 6.5 Forms Service Pack 9, the CRX repository URLs are no longer available (NPR-37592).

**Issues fixed in AEM Forms 6.5.11.1**

>[!NOTE]
>
>If you have not upgraded to AEM 6.5.11.0 Forms, install the AEM Forms 6.5.11.1 add-on package directly. If you have installed AEM 6.5.11.0 Forms, Adobe recommends to upgrade to AEM 6.5.11.1 Forms.

* Submit actions, Send Email and Invoke an AEM Workflow stop working after installing the Forms 6.5.11.0 add-on package.
* CreatePDF operation stops converting Microsoft Word documents to PDF documents after installing the Forms 6.5.11.0 add-on package.
* (JEE Only) Critical security vulnerabilities (CVE-2021-44228 and CVE-2021-45046) reported for Apache Log4j2.
* (JEE only) Assembler DSC in 6.5.11.0 patch contains incorrect metainfo like specification version and impl version.

-->


[[!DNL Experience Manager] ](https://helpx.adobe.com/security/products/experience-manager.html)

## Install 6.5.12.0 {#install}

****

* [](/help/sites-deploying/upgrade.md)
* [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html)
* On a deployment with MongoDB and multiple instances, install Experience Manager 6.5.12.0 on one of the Author instances using the Package Manager.

>[!NOTE]
>
>[!DNL Adobe Experience Manager]

### Install the service pack {#install-service-pack}

[!DNL Adobe Experience Manager]

1. Restart the instance before installation if the instance is in update mode (when the instance was updated from an earlier version). Adobe recommends a restart if the current uptime for an instance is high.

1. [!DNL Experience Manager]

1. [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.12.0.zip)

1. **[!UICONTROL Upload Package]** [](/help/sites-administering/package-manager.md)

1. **[!UICONTROL Install]**

1. To update the S3 connector, stop the instance after installation of the Service Pack, replace the existing connector with a new binary file provided in the install folder, and restart the instance. [](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector)

>[!NOTE]
>
>Dialog on Package Manager UI sometimes exits during the installation of the service pack. Adobe recommends that you wait for error logs to stabilize before accessing the deployment. Wait for the specific logs related to the uninstall of the updater bundle before being assured that the installations is successful. [!DNL Safari]

****

[!DNL Experience Manager]

`../crx-quickstart/install` The package is automatically installed.

[](/help/sites-administering/package-manager.md#package-share) `cmd=install&recursive=true`

>[!NOTE]
>
>Adobe Experience Manager 6.5.12.0 does not support Bootstrap installation.

****

1. `/system/console/productinfo``Adobe Experience Manager (6.5.12.0)`[!UICONTROL Installed Products]

1. **[!UICONTROL ACTIVE]****[!UICONTROL FRAGMENT]**`/system/console/bundles`

1. `org.apache.jackrabbit.oak-core``/system/console/bundles`

[](/help/sites-deploying/technical-requirements.md)

<!-- 

### Install Adobe Experience Manager Forms add-on package {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Skip if you are not using Experience Manager Forms. Fixes in Experience Manager Forms are delivered through a separate add-on package a week after the scheduled [!DNL Experience Manager] Service Pack release.

1. Ensure that you have installed the Adobe Experience Manager Service Pack.
1. Download the corresponding Forms add-on package listed at [AEM Forms releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) for your operating system.
1. Install the Forms add-on package as described in [Installing AEM Forms add-on packages](/help/forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).

>[!NOTE]
>
>Experience Manager 6.5.10.0 includes a new version of [AEM Forms Compatibility Package](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#aem-65-forms-releases). If you are using an older version of AEM Forms Compatibility Package and updating to Experience Manager 6.5.10.0, install the latest version of the package post installation of Forms Add-On Package.

### Install Adobe Experience Manager Forms on JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Skip if you are not using AEM Forms on JEE. Fixes in Adobe Experience Manager Forms on JEE are delivered through a separate installer.

For information about installing the cumulative installer for Experience Manager Forms on JEE and post-deployment configuration, see the [release notes](jee-patch-installer-65.md).

>[!NOTE]
>
>After installing the cumulative installer for Experience Manager Forms on JEE, install the latest Forms add-on package, delete the Forms add-on package from the `crx-repository\install` folder, and restart the server.

-->

### UberJar {#uber-jar}

[](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.12/)

[](/help/sites-developing/ht-projects-maven.md)

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.12</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>`repo.adobe.com` `uber-jar-<version>.jar` `classifier``apis``dependency`

## Deprecated features {#removed-deprecated-features}

[!DNL Experience Manager] An alternate option is provided.

Review if you use a feature or a capability in a deployment. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Feature | Replacement |
|---|---|---|
| Integrations | **[!UICONTROL AEM Cloud Services Opt-In]**[!DNL Experience Manager][!DNL Adobe Target] [!DNL Adobe I/O][!DNL Experience Manager] | [!DNL Adobe I/O][!DNL Experience Manager] |
| Connectors | The Adobe JCR Connector for Microsoft® SharePoint 2010 and Microsoft® SharePoint 2013 is deprecated for Experience Manager 6.5. | N/A |

## Known issues {#known-issues}

* If you are using Content Fragments and GraphQL then it is recommended that you install the following packages on top of 6.5.12.0:

   * [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fhotfix%2Faem-service-pkg-6.5.12.0-NPR-38144-B0002.zip)

   * [](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcfm-graphql-index-def-1.0.4.zip)

* [!DNL Microsoft Windows Server 2019][!DNL MySQL 5.7][!DNL JBoss EAP 7.1][!DNL Microsoft Windows Server 2019][!DNL AEM Forms 6.5.10.0]

* [!DNL Experience Manager]`RRD4JReporter``error.log` To resolve the issue, restart the instance.

* Als u [!DNL Experience Manager] 6.5 Service Pack 10 of een vorig de dienstpak op [!DNL Experience Manager] 6.5, de runtime kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) wordt geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De titel van de map wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Selecting to configure some other field of the adaptive form in the same editor resolves the issue.

* The following errors and warning messages may display during installation of Experience Manager 6.5.x.x:
   * “When the Adobe Target integration is configured in Experience Manager using the Target Standard API (IMS authentication), then exporting Experience Fragments to Target results in wrong offer types getting created. Instead of type “Experience Fragment”/source “Adobe Experience Manager,” Target creates several offers with type “HTML”/source “Adobe Target Classic.”
   * `com.adobe.granite.maintenance.impl.TaskScheduler`
   * Adaptive Form server-side validation fails when aggregate functions such as SUM, MAX, and MIN are used (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler`
   * Hotspot in a Dynamic Media interactive image is not visible when previewing the asset through Shoppable Banner viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]`

* When trying to move/delete/publish either Content Fragments or Sites/Pages, there is an issue when Content Fragment references are fetched, as the background query fails; i.e. the functionality does not work.
`/oak:index/damAssetLucene`

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi bundles and content packages included {#osgi-bundles-and-content-packages-included}

[!DNL Experience Manager]

* [List of OSGi bundles included in Experience Manager 6.5.12.0](assets/65120_bundles.txt)

* [List of Content Packages included in Experience Manager 6.5.12.0](assets/65120_packages.txt)

## Restricted websites {#restricted-sites}

These websites are only available to customers. If you are a customer and need access, contact your Adobe account manager.

* [](https://licensing.adobe.com/)
* [](https://experienceleague.adobe.com/docs/customer-one/using/home.html)

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] ](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] ](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [](https://www.adobe.com/subscription/priority-product-update.html)

