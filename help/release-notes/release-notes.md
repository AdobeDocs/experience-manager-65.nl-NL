---
title: Opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: '"[!DNL Adobe Experience Manager] 6.5 notities waarin de releasegegevens, de nieuwe functies, de installatie en gedetailleerde lijsten met wijzigingen worden beschreven."'
exl-id: 0288aa12-8d9d-4cec-9a91-7a4194dd280a
source-git-commit: 498e00ab7838de675771224204726a51e68d4a57
workflow-type: tm+mt
source-wordcount: '2631'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Laatste Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

## Gegevens vrijgeven {#release-information}

| Producten | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.12.0. |
| Type | Service Pack-release |
| Date | 24 februari 2022 |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.12.0.zip) |

## Wat is inbegrepen in [!DNL Adobe Experience Manager] 6.5.12.0. {#what-is-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.12.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het de dienstpak wordt geïnstalleerd op [!DNL Adobe Experience Manager] 6.5

De belangrijkste functies en verbeteringen die zijn geïntroduceerd in [!DNL Adobe Experience Manager] 6.5.12.0 zijn:

* Nadat u een verbinding tussen externe DAM- en Sites-implementaties hebt geconfigureerd, worden de middelen op externe DAM beschikbaar gesteld op de implementatie van Sites. U kunt de update uitvoeren, verwijderen, hernoemen en bewerkingen verplaatsen op de externe DAM-middelen of -mappen. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen (NPR-37816).

* Push-rollouts van een live-kopiebron naar meerdere live kopieën is nu standaard mogelijk, zonder dat een blauwdrukconfiguratie nodig is (CQ-4259951).
* De status van asynchrone bewerkingen in uitvoering wordt nu weergegeven in de gebruikersinterface om te voorkomen dat gebruikers per ongeluk meerdere asynchrone bewerkingen op hetzelfde pad activeren (NPR-37611).
* Ondersteuning voor op IMS gebaseerde verificatie wordt verleend voor API&#39;s van Analytics 2.0 (CQ-4285474, NPR-37803, NPR-37701, NPR-37702, NPR-37703).
* API-ondersteuning voor JSON biedt type Experience-fragment (NPR-37796).
* Aanbiedingsaanvraag is nu beschikbaar voor de functie Verwijderen (Experience Fragment API) in IMS (NPR-37668).
* De ingebouwde opslagplaats (Apache Jackrabbit Oak) staat nog steeds op 1.22.9.

Hieronder volgt een lijst met oplossingen die u vindt in [!DNL Experience Manager] 6.5.12.0-release.

### [!DNL Sites] {#sites-65120}

De volgende problemen zijn opgelost in [!DNL Sites]:

* De lay-out van de eigenschappen van het inhoudsfragment wordt verbroken omdat de tabbladen Standaard en Geavanceerd links geen marges hebben (SITES-4484).
* De optie om een banner te sluiten op inhoudsfragmenten waarnaar op verschillende sitepagina&#39;s wordt verwezen, werkt niet. Deze banner informeert de gebruikers dat er op een of meer pagina&#39;s naar het inhoudsfragment wordt verwezen (SITES-4173).
* De selectievakjes worden niet uitgelijnd in het dialoogvenster Overerving herstellen (SITES-3514).
* De malplaatjepagina op wij-kleinhandel en websites is gebroken, aangezien de componenten niet laden en de structuuroptie niet beschikbaar is, aangezien pageinfo.json servlet op LaunchManagerImpl.getLaunchStream (SITES-3489) blijft.
* Publiceren van gebruikersknooppunten vanuit de omgeving Auteur naar Publiceren werkt niet (NPR-38005).
* Wanneer u een ervaringsfragment maakt met een bewerkte sjabloon, worden de bewerkingen aan de eigenschappen van de eerste pagina niet weergegeven (NPR-37962).
* De paginabeweging op de Experience Manager gaat langzaam (NPR-37961).
* De vertaling van het fragment van de ervaring werkt geen verwijzingen naar taalexemplaarwegen bij (NPR-37953).
* Gebruikers zonder replicatiemachtigingen kunnen geen pagina&#39;s verwijderen of verplaatsen, zelfs niet als de pagina&#39;s niet zijn geactiveerd (NPR-37936).
* Er worden willekeurige org.apache.felix.metatype fouten waargenomen op de server (NPR-37935).
* Referenties in de Sites admin touch-gebruikersinterface geven inkomende koppelingen niet correct weer (NPR-37934).
* Het startpad voor het toevoegen van nieuwe pagina&#39;s of elementen is niet beschikbaar wanneer u pagina&#39;s selecteert in een vertaaltaak (NPR-37912).
* Referentiepagina&#39;s in een lijstcomponent die in ervaringsfragmenten wordt toegevoegd, worden niet bijgewerkt naar de doelpagina wanneer de introductie wordt bevorderd (NPR-37886).
* De omgeving van de auteur heeft gebruikersinterface kwesties-zoals Edit de titel van de wijzepagina wordt niet gecentreerd en toegelaten componentenselecteur op beleidsredacteur: het selectievakje voor groepen neemt de volledige breedte van de container in beslag, zodat het label op de volgende regel wordt weergegeven (NPR-37878).
* [Platform] Het versienummer van xmlns:metatype in het bestand metatype.xml van commons-httpclient is &quot;http://www.osgi.org/xmlns/metatype/v1.0.0&quot; in plaats van &quot;http://www.osgi.org/xmlns/metatype/v1.2.0&quot; (NPR-37865).
* Er worden fouten waargenomen en pagina&#39;s worden niet verplaatst wanneer u naar een pagina probeert te gaan (NPR-37864).
* [RTF-editor] Afbeelding wordt niet weergegeven in de klassieke gebruikersinterface wanneer de afbeelding wordt toegevoegd als lijstitem in de Rich Text Editor (NPR-37835).
* Auteurs kunnen tags toepassen die zich buiten het geconfigureerde hoofdpad bevinden wanneer het tagveld in een dialoogvenster wordt gebruikt (NPR-37834).
* Multifield wordt niet correct weergegeven in de container van de layout en geeft een fout (NPR-37811).
* Poging om het formaat van de componentlay-out in de pagina-editor te wijzigen, werkt niet in mobiele lay-out (NPR-37805).
* Bij het vertalen van fragmenten in Experience Fragment worden geen cyclische verwijzingen naar kopieerpaden voor talen bijgewerkt (NPR-37745).
* Het gebruik van cq-msm-lockable rijke tekstgebied in paginaeigenschappen maakt niet het gebied bij het opstellen van de pagina onbruikbaar en het kan door de auteurs worden gewijzigd (NPR-37714).
* Bij het activeren van een ervaringsfragment verzendt de uitgever veel activeringsaanvragen naar Dispatcher (NPR-37707).
* Op topologieverandering, wordt het Verschuiven baan voor activa verwerking teruggesteld resulterend in de banen die in uitvoering zijn op het tijdstip van topologieverandering die worden genegeerd (NPR-37706).
* Aanhalingstekens, kruis en streepje worden niet naar CSV geëxporteerd wanneer gebruikers van MacOS-exportsites en -middelen-URL&#39;s (NPR-37698).
* De container van de lay-out in SPA paginamalplaatje kan niet de aangepaste CSS klassen registreren die in het Beleid van het Malplaatje worden bepaald wanneer het runnen van reacties SPA pagina&#39;s (NPR-37697).
* Achtergrondafbeelding is niet zichtbaar wanneer de gebruiker een doelfragment selecteert dat een achtergrond heeft in de container (NPR-37662).
* De vertaalbaan op een ervaringsfragment vertaalt niet alle componenten op dat ervaringsfragment (NPR-37660).
* Door het vertalen van ervaringsfragmenten en de pagina met het ervaringsfragment wordt het startpad niet bijgewerkt in de ervaringsfragmentkoppeling (NPR-37659).
* De bestands-uploadwidget geeft niet de bestandsnaam weer wanneer een bestand wordt geüpload en het dialoogvenster wordt opgeslagen (NPR-37634).
* De geplande activering (publicatie) van het middel wordt niet op de geplande tijd geactiveerd als de map met dat middel wordt verplaatst (NPR-37621).
* [Platform] Het dashboard voor externe koppelingencontrole kan geen resultaten weergeven in [!DNL Adobe Experience Manager] WCM (NPR-37614).
* Inhoudsfragmenteditor werkt niet correct wanneer hoofdletters en kleine letters worden gebruikt in tagnamen bij het bewerken van tags in de editor (NPR-37601).
* In de klassieke gebruikersinterface-editor wordt geen markering weergegeven zoals in de vergelijkingsweergave van de aanraakgebruikersinterface (NPR-37588).
* Intermitterende fout 500 wordt geregistreerd op het toevoegen van een ervaringsfragment aan vertaalbanen (NPR-37587).
* Auteurs kunnen de datum van de datumkiezer selecteren en gebruiken, zelfs op de kiezer voor een uitgeschakelde datum (NPR-37583).
* [Stichting] Auteurs kunnen bepaalde decimale waarden niet invoeren in het brontype van het nummerveld in een componentdialoogstructuur voor de aanraakgebruikersinterface (NPR-37059).
* De paden in de map libs worden verwijderd bij het installeren van vorige servicepacks (NPR-36815).
* [Handel] De deactivering van een hoofdmap wijzigt de deactiveringsstatus van onderliggende producten in [!DNL Experience Manager Commerce] console; bovendien wordt het aantal onderliggende mappen van een hoofdmap op het moment van deactivering onjuist weergegeven in de gebruikersinterface (CQ-4338261).
* [Lokalisatieworkflow] De inhoud voor de aanpassing van kolommen en de aanpassing van de branding is niet gelokaliseerd in het dialoogvenster Beheer—bij het selecteren van het pictogram onder het profielpictogram in [!DNL Adobe Experience Manager] in box (CQ-4334864).
* [Gemeenschappen] Op de inhoud in de tabel voor groepsleden kan niet worden geklikt (CQ-4334404).
* [Eik] Het Cold-Standby-synchronisatieproces werkt niet en registreert een fout (CQ-4333868).
* [UI Platform Foundation] [!DNL Experience Manager] De startpagina wordt opnieuw weergegeven wanneer de gebruiker de optie [!DNL Adobe Experience Manager] pictogram staat al op de startpagina (CQ-4317409).

### [!DNL Assets] {#assets-65120}

<!--
The following accessibility enhancements are available in [!DNL Assets]:

* enhancement 1
-->

De volgende problemen zijn opgelost in [!DNL Assets]:

* Bij het toevoegen van een element of map (met `single quote` in the name) in Connected Assets, the reference path failed and results as an exception (NPR-37712).
* Wanneer u een watermerk aan een element toevoegt, wordt het watermerk altijd in zwarte kleur weergegeven, ongeacht de kleur die door de gebruiker is gedefinieerd (NPR-37720).
* Bij gebruik van Connected Assets kan een gebruiker die geen beheerder is, naar een middel zoeken, zelfs als gebruikers die geen beheerder zijn, beperkt zijn tot toegang tot de DAM-gegevensopslagruimte (NPR-37644).
* Wanneer u metagegevens van elementen bijwerkt met behulp van bulkbewerking, worden de wijzigingen die zijn toegepast op de vervolgkeuzelijsten niet opgeslagen en teruggezet naar de standaardwaarden (NPR-37345).
* Het verwijderen van een map in een te lange periode die invloed heeft op de algehele prestaties (NPR-37107).
* Wanneer de gebruiker regels toepast in meta-gegevensschema, kan de gebruiker niet de volledige waarde voor dropdown bekijken `Field Value` en `Field Choices` als de waarde groter is dan het tekstvak (CQ-4338074).
* Na de upgrade naar versie 6.5.10.0 geeft de pagina met elementeigenschappen een weerspiegeling van een onnodig HTML-renderingbericht (CQ-4336994).
* Elementen sorteren in `List View` werkt niet effectief (CQ-4335298).
* Wanneer u elementen deelt via een koppeling voor delen, worden de elementen gedownload in aparte mappen (CQ-4335000).
* Wanneer u de [!DNL Experience Manager] `Inbox` instellingen, de `Share` en `Out of office` tabbladen weerspiegelen niet-vertaalde inhoud (CQ-4334858).

* De volgende correcties hebben betrekking op trapsgewijze metagegevens in eigenschappen van elementen.
   * Een verplichte vervolgkeuzelijst bevat meerdere foutberichten voor elke selectie in het veld met meerdere waarden (NPR-37859).
   * Alleen de laatste selectie van het bovenliggende veld wordt opgeslagen voor het afhankelijke niet-bewerkbare veld (NPR-37858).
   * Het afhankelijke vervolgkeuzemenu (veld met meerdere waarden) geeft periodiek de standaardwaarde weer voor het geselecteerde bovenliggende vervolgkeuzemenu (NPR-37791).


### [!DNL Dynamic Media] {#dynamic-media-65120}

De volgende problemen zijn opgelost in [!DNL Dynamic Media]:

* De elementen van een map die `renditions` in de map wordt de naam niet gesynchroniseerd in `Dynamic Media` (CQ-4338428).
* Wanneer u een voorinstelling voor een afbeelding maakt in `tiff` de voorinstelling wordt gemaakt, maar de indeling wordt gewijzigd in `jpeg` (CQ-4335985).
* Bij het wijzigen van de `Progressive JPEG Scan` waarde in de Voorinstellingseditor voor afbeeldingen, de vervolgkeuzelijst wordt altijd opnieuw ingesteld op `auto`(CQ-4335971).
* De videometagegevens zijn niet zichtbaar voor de `mxf` video&#39;s op de pagina met eigenschappen van elementen (CQ-4335499).
* Bij het opnieuw verwerken van de video-elementen worden de AVS (Adaptive Video Set) en video-uitvoeringen niet gepubliceerd vanaf de publicatieserver (CQ-4335461).
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


Voor informatie over beveiligingsupdates raadpleegt u [[!DNL Experience Manager] beveiligingspagina met opsommingstekens](https://helpx.adobe.com/security/products/experience-manager.html).

## Installeer 6.5.12.0 {#install}

**Instellingsvereisten en meer informatie**

* Experience Manager 6.5.12.0 vereist Experience Manager 6.5. Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer Experience Manager 6.5.12.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.

>[!NOTE]
>
>Adobe raadt u niet aan de installatie van de [!DNL Adobe Experience Manager] 6.5.12.0-pakket.

### Het servicepack installeren {#install-service-pack}

Om het de dienstpak op een [!DNL Adobe Experience Manager] 6.5-instantie voert u de volgende stappen uit:

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.12.0.zip).

1. Pakketbeheer openen en klikken **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem treedt meestal op in [!DNL Safari] browser, maar kan soms voorkomen op om het even welke browser.

**Automatische installatie**

Er zijn twee manieren om automatisch te installeren [!DNL Experience Manager] 6.5.12.0 op een werkexemplaar:

A. Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik de [HTTP-API van Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Adobe Experience Manager 6.5.12.0 biedt geen ondersteuning voor Bootstrap-installatie.

**De installatie valideren**

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (6.5.12.0)` krachtens [!UICONTROL Installed Products].

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.2.2.3 of hoger (Webconsole gebruiken: `/system/console/bundles`).

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

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

UberJar voor Experience Manager 6.5.12.0 is beschikbaar in [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.12/).

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op:

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
>UberJar en de andere verwante artefacten zijn beschikbaar op de Centrale Bewaarplaats van de Adobe Openbare Maven bewaarplaats (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als de waarde voor de `dependency` tag.

## Verouderde functies {#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd met [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Er is een alternatieve optie opgegeven.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integrations | De **[!UICONTROL AEM Cloud Services Opt-In]** het scherm is verouderd sinds [!DNL Experience Manager] en [!DNL Adobe Target] de integratie wordt bijgewerkt in Experience Manager 6.5. De integratie ondersteunt de Adobe Target Standard API. De API gebruikt verificatie via Adobe IMS en [!DNL Adobe I/O] en steunt de groeiende rol van Adobe Launch naar instrument [!DNL Experience Manager] De optiewizard is functioneel niet relevant op pagina&#39;s voor analyse en personalisatie. | Systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O] integratie via de respectieve [!DNL Experience Manager] cloudservices. |
| Connectors | De Adobe JCR Connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is afgekeurd voor Experience Manager 6.5. | N.v.t. |

## Bekende problemen {#known-issues}

* Wanneer u AEM 6.5 Service Pack 12 installeert en het ZIP-bestand met de status probeert te downloaden, downloadt Experience Manager een beschadigd bestand.

   >[!CAUTION]
   >
   >Er wordt een nieuwe versie van het pakket &quot;indexdefinitie&quot; ontwikkeld. De onderstaande koppeling wordt gepubliceerd zodra deze beschikbaar is.
   >
   >Neem tot dan contact op met de klantenservice voor de hotfix.

   <!--
  Download and install [AEM Sites SEO Index Package](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/sites-seo-index-content-1.0.0.zip) on your AEM instance before downloading the ZIP file to resolve the issue.
  -->

   Download en installeer AEM Sites SEO Index Package op uw AEM voordat u het ZIP-bestand downloadt om het probleem op te lossen.

* Als [!DNL Microsoft Windows Server 2019] ondersteunt niet [!DNL MySQL 5.7] en [!DNL JBoss EAP 7.1], [!DNL Microsoft Windows Server 2019] ondersteunt geen kant-en-klare installaties voor [!DNL AEM Forms 6.5.10.0].

* Als u een upgrade uitvoert op uw [!DNL Experience Manager] van 6.5 tot 6.5.10.0 versie, kunt u bekijken `RRD4JReporter` uitzonderingen in de `error.log` bestand. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 10 of een vorig de dienstpak op [!DNL Experience Manager] 6.5, de runtime kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) wordt geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De titel van de map wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van reg om niet-geregistreerd te voltooien.

* Wanneer u probeert inhoudsfragmenten of sites/pagina&#39;s te verplaatsen/verwijderen/publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald, omdat de achtergrondquery mislukt. De functionaliteit werkt dus niet.
Om correcte verrichting te verzekeren, moet u de volgende eigenschappen aan de knoop van de indexdefinitie toevoegen `/oak:index/damAssetLucene` (indexering hoeft niet opnieuw te worden uitgevoerd) :

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.12.0:

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.12.0](assets/65120_bundles.txt)

* [Lijst met inhoudspakketten die zijn opgenomen in Experience Manager 6.5.12.0](assets/65120_packages.txt)

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* Zie [hoe contact op te nemen met de Adobe Klantenondersteuning](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

