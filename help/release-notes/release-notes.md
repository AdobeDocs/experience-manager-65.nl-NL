---
title: Opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: Zoek naar releasegegevens, wat is nieuw, installeer hoe kan worden gewijzigd en een gedetailleerde wijzigingslijst voor [!DNL Adobe Experience Manager] 6.5
mini-toc-levels: 3
source-git-commit: 0bce05571590bc09e2b65f6bd6c1f387c71fba3a
workflow-type: tm+mt
source-wordcount: '2609'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Laatste Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/Documents/issue_tracker_sp_cfp_updates.xlsx?d=w3ea81ae4e6054153b132f2698c86f84e&csf=1&web=1&e=7yhrWb&nav=MTVfe0U0RjdDQUM3LTZCQ0EtNDk1Qy04Mjc1LTM2MUJEMzE1OEVGN30 -->

<!-- DO NOT DELETE THIS HIDDEN NOTE      DO NOT DELETE THIS HIDDEN NOTE
>[!NOTE]
>
>Fixes in [!DNL Experience Manager] Forms are delivered through a separate add-on package one week after the scheduled [!DNL Experience Manager] Service Pack release date. In this case, the add-on packages release Thursday, June 1, 2023. In addition, a list of Forms fixes and enhancements is added to this section. -->

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6.5 |
| -------- | ---------------------------- |
| Versie | 6.5.17.0 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Datum | Donderdag 25 mei 2023 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.17.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.17.0. {#what-is-included-in-aem-6517}

[!DNL Experience Manager] 6.5.17.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, insectenmoeilijke situaties, en prestaties, stabiliteit, en veiligheidsverbeteringen die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 hebben vrijgegeven. [Dit servicepack installeren](#install) op [!DNL Experience Manager] 6.5 <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_ -->

Enkele belangrijke functies en verbeteringen in deze release zijn:

* **Verbeterde zoekervaring** - U kunt nu snel de volgende bewerkingen uitvoeren op de elementen die in de zoekresultaten worden weergegeven:
   * Een workflow maken
   * Een versie maken
   * Relatieve of niet-gerelateerde elementen

   U hoeft niet naar de middelenlocatie te navigeren en de eigenschappen ervan te bekijken om deze bewerkingen uit te voeren.
* **Dynamic Media _Opname_**- Experimenteer met testafbeeldingen of Dynamic Media-URL&#39;s om de uitvoer van verschillende afbeeldingsmodifiers en Smart Imaging-optimalisaties voor de bestandsgrootte (met WebP- en AVIF-levering), de netwerkbandbreedte en de pixelverhouding van het apparaat te bekijken. Zie [Dynamic Media-momentopname](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html).
* **DASH-streaming met Dynamic Media** - Ondersteuning voor het nieuwe protocol (DASH - Dynamic Adaptive Streaming via HTTP) dat wordt gestart voor Adaptive streaming in Dynamic Media-video (met CMAF ingeschakeld). Nu beschikbaar voor alle regio&#39;s, [ingeschakeld via een ondersteuningsticket](/help/assets/video.md#enable-dash-on-your-account-enable-dash).

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## [!DNL Assets]{#assets-6517}

* Wanneer u meer dan 40 PDF tegelijk publiceert, [!DNL Experience Manager] reageert niet meer en is enige tijd niet meer beschikbaar. (ACTIVA-21789)
* Als u bent aangemeld als testgebruiker, kunt u de Middelen met betrekking tot een bepaald middel niet zien wanneer u op eigenschappen van een Element klikt. (ACTIVA-21648)
* Elementen bewerken met `Desktop Actions`, als u probeert meer dan vijf elementen tegelijk in te checken, `Limit Reached` Er wordt een fout weergegeven en de geselecteerde elementen zijn uitgecheckt. (ACTIVA-21121)
* Kan elementen niet op naam sorteren in een verzameling. (ACTIVA-20924)
* Kan geen afmetingen instellen voor elementen met een afbeeldingsindeling. (ACTIVA-20835)
* De knopinfo en de achtergrond ervan in het veld Zoeken/E-mailadres toevoegen geven geen juiste contrastverhouding weer tijdens het delen van een koppeling. (ACTIVA-17347)
* Wanneer u uitvouwt `Notifications`, wordt de tekst niet correct weergegeven vanwege alinea-afstand. (ACTIVA-17345)
* Wanneer u een middel in Inzameling kopieert, `Public Collection` het selectievakje wordt niet correct weergegeven. (ACTIVA-17343)
* Elementen gebruiken ARIA-kenmerken zonder een rol. (ACTIVA-17325,ACTIVA-17323)
* De koppeling is niet beschrijvend wanneer u uitvouwt `Notifications`. (ACTIVA-17283)
* Wanneer u door de [!DNL Smart Crop] wordt de inhoud weergegeven als een lijst, maar niet gemarkeerd als een ongeordende lijst. Hierdoor herkent de schermlezer de ongeordende lijst niet en wordt deze als onbewerkte tekst gelezen. (ACTIVA-17247)
* De `Sort By` het label is niet gekoppeld aan de desbetreffende vervolgkeuzelijst. Hierdoor herkent de schermlezer de vervolgkeuzemogelijkheden niet. (ACTIVA-17239)
* Kan niet naar voren of naar achteren gaan met het toetsenbord of de pijltoetsen wanneer u een gebruiker probeert toe te voegen met het gereedschap `Add user` keuzelijst met invoervak. (ACTIVA-17233)
* Schermlezer geeft de informatie voor de stap Workflows (ASSETS-17285) niet correct door.
* Wanneer u navigeert naar `Saved Searches` keuzelijst met invoervak, naam en rol hebben geen toegewezen labels. (ACTIVA-17329)
* Wanneer u navigeert `Collection` en de muis boven de tekst houden *Leden*, wordt de tekst niet weergegeven als gemarkeerd. Hierdoor herkent de schermlezer de koptekst niet en wordt deze gelezen als onbewerkte tekst. (ACTIVA-17245)
* Geen toegang `View Settings` met de toets omlaag of omhoog van het toetsenbord. (ACTIVA-17257)
* Kan geen workflow activeren voor meerdere geselecteerde elementen die zijn gevonden met zoekfilters. (ACTIVA-7689)
* Wanneer u een element (of meerdere elementen) selecteert in de zoekresultaten, is de optie Relatief of Niet-gerelateerd niet zichtbaar. Maar de optie is beschikbaar, anders. (ACTIVA-7679)
* Het deelvenster Zoekfilters wordt slechts eenmaal geopend na de aanmelding en wordt niet geopend als u de zoekpagina afsluit en de zoekopdracht opnieuw uitvoert. (ACTIVA-7671)
* De keuzelijst met e-mailadressen geeft geen juiste contrastverhouding weer tijdens het delen van een koppeling. (ACTIVA-17349)

<!-- REMOVED BY ENGINEERING FROM TOTAL RELEASE CANDIDATE LIST 
* When you select any file in a Collection and click `Download`, and then navigate to the email checkbox and expand it, regular text and email link is not recognizable due to background color. (ASSETS-17349) 
* When you navigate to `Smart Crop` option, the screen reader does not announce the expand or collapse state of the button. (ASSETS-17335)-->

## [!DNL Assets] - [!DNL Dynamic Media]{#dm-6517}

* De verbinding met Dynamic Media wordt verbroken wanneer er al een Dynamic Media Cloud Configuration bestaat. (ACTIVA-23057)
* Verbeterde prestaties tijdens het bladeren in mappen met veel Dynamic Media-video&#39;s en het probleem is niet geladen in de weergave Mapkaart. (ACTIVA-23016)
* Voorbeeldtokens worden verwijderd uit `error.log` die kunnen worden gebruikt om veilige inhoud van de veilige testservers aan te vragen. (ACTIVA-22685)
* Met een PDF-miniatuurweergave voegt u een schaduw toe. Bijgewerkte versie van Gibson lib 4.0.1680232194 voor het oplossen van het probleem van de PDF-miniatuurrendering. (ACTIVA-22585)
* De Dynamic Media Hybrid-modus is nu compatibel met versie 8.0.1 van de New Relic Agent (ASSETS-22578).
* ACLs van de Experience Manager (de Lijsten van het Toegangsbeheer) wordt nu gerespecteerd wanneer het previewing van de dossiers van Dynamic Media op Experience Manager. (ACTIVA-21628)
* Schermlezers navigeren niet naar een verborgen element wanneer de gebruiker probeert te navigeren met de toets Pijl-omlaag of Tab. (ACTIVA-5617)
* De gebruikersinterface van het Profiel van het beeld beperkt voor slimme gewassen met de zelfde naam, of de zelfde dimensie, of allebei. (ACTIVA-16997)
* De standaardbreedte en -hoogte zijn nu ingesteld op 50 pixels voor de gebruikersinterface van Slim uitsnijden in afbeeldingsprofiel. (ACTIVA-16997)

## [!DNL Commerce]{#commerce-6517}

* Verplaatste tags worden opgeschoond, maar er wordt nog steeds naar verwezen door producten onder `/var`. (CQ-4351337)

## [!DNL Forms]{#forms-6517}

>[!NOTE]
>
>Oplossingen in [!DNL Experience Manager] Forms wordt één week na de geplande levering geleverd via een afzonderlijk invoegpakket [!DNL Experience Manager] Releasedatum van Service Pack. In dit geval worden de invoegpakketten op donderdag 1 juni 2023 uitgebracht. Daarnaast wordt een lijst met Forms-correcties en -verbeteringen toegevoegd aan deze sectie.

## Integrations{#integrations-6517}

* Wanneer u een Adobe Target IMS-configuratie omzet in een gebruikersreferentie in configuraties in verouderde cloud, wordt de `connectedWhen` wordt niet gewijzigd. Deze kwestie maakt alle vraag gaan alsof de configuratie nog op IMS-Gebaseerd was. (CQ-4352810)
* Toevoegen `modifyProperties` toestemming om `fd-cloudservice` systeemgebruiker voor Adobe Sign-configuratie. (FORMS-6164)
* Met Experience Manager die met Adobe Target wordt geïntegreerd, wanneer u een de testactiviteit van AB creeert, synchroniseert het niet omhoog het publiek verbonden aan het, aan Doel. (NPR-40085)

## Platform{#platform-6517}

* In de Experience Manager Tag Management-gebruikersinterface (/aem/tags/) worden de naamruimten en -tags weergegeven in de volgorde waarin ze zijn gemaakt. Als er echter veel naamruimten en tags zijn, is het moeilijk deze weer te geven en te beheren. Dit probleem is omdat ze op geen enkele andere manier kunnen worden gesorteerd. (NPR-39620)
* Google closure version update required because Minification js werkt niet voor alle clientbibliotheken. (NPR-40043)

## [!DNL Sites]{#sites-6517}

* De daling van prestaties in LinkCheckerTransformer. (SITES-11661)
* Er worden geen taalkopieën van een pagina bijgewerkt zoals u had verwacht. (SITES-11191)
* Aanroep van niet-campagnepagina&#39;s openen `targeteditor.html` onnodig. Verwijder de `targeteditor` vraag wanneer niet nodig. (SITES-12469)
* Er kunnen geen actieve kopieën worden gemaakt voor pagina&#39;s met annotaties. (SITES-12154)
* De rollout van pagina&#39;s werkt aan Experience Manager 6.5.16. (SITES-12008)
* Onvoldoende geheugen; hoge opruimactiviteit door `NotificationManagerImpl`. `NotificationManager` bundelupgrade naar AEM 6.5. (SITES-11440)
* Vaste WCM IT tests die de dienstverpakking blokkeerden 17. (SITES-13089)
* Het ophalen van verwijzingen naar sites mislukt op servlet. (SITES-10901)

### [!DNL Sites] - Gebruikersinterface Admin{#sites-adminui-6517}

* Het voorvertoningsvenster voor de miniatuurafbeeldingskiezer kan niet worden gesloten. (SITES-10459)

### [!DNL Sites] - [!DNL Content Fragments]{#sites-contentfragments-6517}

* Configuratie voor het verbinden met de dienstvoorwerp van Polaris (URL, geloofsbrieven, callback, etc.). (SITES-12149)
* Gebruik van `SemanticDataType.REFERENCE` moet &quot;Remote-Asset-ID&#39;s&quot; ondersteunen. (SITES-12127)
* Integreer Polaris Asset Selector in Inhoudsfragmenteditor. (SITES-12125)
* Een verplichte HTTP-header was nodig om toegang te krijgen tot het eindpunt van de metagegevensservice. (SITES-13068)
* De GraphQL-implementatie van 6,5 was niet gelijk aan Cloud Service (primair). de vastgestelde problemen zijn opgelost . (SITES-13096)
* Op AEM 6.5/AMS moeten paginering/sortering en hybride filtering beschikbaar zijn. (SITES-9154)

### [!DNL Sites] - Basiscomponenten{#sites-core-components-6517}

* De eigenschap `cq-msm-lockable` heeft de verkeerde omleidingswaarde in de de paginacomponent van de Stichting. (SITES-10904)
* De verre Plukker van Activa richt altijd aan het werkgebiedmilieu IMS. (SITES-13433)

### [!DNL Sites] - [!DNL Experience Fragments]{#sites-experiencefragments-6517}

* Als u een configuratie ExternalAlizer in een Experience-fragment selecteert wanneer u exporteert naar Adobe Target, wordt de onjuiste externe URL verzonden. (SITES-12402)
* Niet-inclusieve termen verwijderen; algemene richtlijnen voor termen toepassen. (SITES-11244)

### [!DNL Sites] - Pagina-editor{#sites-pageeditor-6517}

* Er wordt geen miniatuur weergegeven voor een carrousel die is ingesteld in de Experience Manager content finder side rail. (SITES-8593)

## Sling{#sling-6517}

* Sling `ResourceMerger` verbruikt een hoge hoeveelheid cpu wanneer voorzien van een fictieve weg, die een ontkenning van de dienst veroorzaakt. (NPR-40338)

## Vertaalprojecten{#translation-6517}

<!-- REMOVED BY ENGINEERING FROM TOTAL RELEASE CANDIDATE LIST * The `translationrules.xml` is sorted poorly when adding a rule to a property by way of the translation configuration user interface. (NPR-40431) -->
* Taalkopie wordt niet gemaakt wanneer de gebruiker geen niet-verplichte velden configureert. (NPR-40036)

## Gebruikersinterface{#ui-6517}

* De knop Annuleren in Pagina-eigenschappen is inactief. u moet naar de gebruikersinterface van Sitebeheer gaan. (NPR-40501)

<!-- ## WCM{#wcm-6517}

* TEXT -->

## Workflow{#workflow-6517}

* Wijzigingen in de workflowconsole. (NPR-40502)
* `SegmentNotfound errors` in de logboeken op een instantie van de productiepauteur die door unclosed resolver van het Middel in klasse wordt veroorzaakt `com.day.cq.workflow.impl.email.EMailNotificationServic`. (NPR-40187)
* Een gesloten, niet-gesloten `ResourceResolver` de uitzondering wordt geregistreerd. (ACTIVA-22495)
* De auteur van de Experience Manager crasht wanneer PSD/PDF met enorme `DocumentAncestors` metagegevenskenmerken worden geüpload. (ACTIVA-22966)
* Sessielek in klasse `InboxSharingCache` with `user-reader-service`. (CQ-4352513)
* Een onvolledige lijst met gebruikers en groepen wordt weergegeven wanneer de stap Deelnemer werkstroominitiator een lijst weergeeft met de gebruikers en groepen voor de stap Deelnemer. Deze kwestie kwam voor toen één groep ook lid van een andere groep was. (NPR-40055)
* Verbeterde leegloop van workflows. (NPR-40459)

## Installeren [!DNL Experience Manager] 6.5.17.0.{#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.17.0 vereist [!DNL Experience Manager] 6.5 Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies. <!-- UPDATE FOR EACH NEW RELEASE -->
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.17.0.zip).
* Bij een implementatie met MongoDB en meerdere exemplaren, installeert u [!DNL Experience Manager] 6.5.17.0 op één van de instanties van de Auteur die de Manager van het Pakket gebruiken.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!IMPORTANT]
>
> Adobe raadt u niet aan de [!DNL Experience Manager] 6.5.17.0-pakket. Voordat u het pakket installeert, moet u daarom een back-up maken van het `crx-repository` voor het geval u het terug moet rollen. <!-- UPDATE FOR EACH NEW RELEASE -->
<!-- For instructions to install Service Pack for AEM Forms, see [AEM Forms Service Pack installation instructions](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md). -->


### Installeer het de dienstpak op [!DNL Experience Manager] 6,5{#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.17.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem treedt meestal op in [!DNL Safari] browser, maar kan soms voorkomen op om het even welke browser.

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL Experience Manager] 6.5.17.0.<!-- UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Experience Manager 6.5.17.0 ondersteunt geen Bootstrap-installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (6.5.17.0)` krachtens [!UICONTROL Installed Products]. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.22.15 of hoger (webconsole gebruiken: `/system/console/bundles`). <!-- NPR-40398 for 6.5.17.0 --> <!-- OAK Oak oak VERSION -MAY- NEED TO BE UPDATED FOR EACH NEW RELEASE -->

### Service Pack installeren voor [!DNL Experience Manager] Forms{#install-aem-forms-add-on-package}

Voor instructies voor het installeren van het servicepakket op AEM Forms raadpleegt u [Installatie-instructies voor AEM Forms Service Pack](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md).

### GraphQL-indexpakket voor Experience Manager-inhoudsfragmenten installeren{#install-aem-graphql-index-add-on-package}

Klanten die GraphQL gebruiken, moeten de [Inhoudsfragment AEM met GraphQL Index Package 1.1.1](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/cfm-graphql-index-def-1.1.1.zip).

Zo kunt u de vereiste indexdefinitie toevoegen op basis van de functies die ze daadwerkelijk gebruiken.

Als u dit pakket niet installeert, kan dit leiden tot trage of mislukte GraphQL-query&#39;s.

>[!NOTE]
>
>Installeer dit pakket slechts eenmaal per instantie; het hoeft niet opnieuw te worden geïnstalleerd met elk Service Pack.

### UberJar{#uber-jar}

The UberJar for [!DNL Experience Manager] 6.5.17.0 is beschikbaar in de [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.17/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.17</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op de Centrale Bewaarplaats van de Adobe Openbare Maven bewaarplaats (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als de waarde voor de `dependency` tag.

## Verouderde functies{#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd met [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Er is een alternatieve optie opgegeven.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integrations | Het scherm **[!UICONTROL AEM Cloud Services Opt-In]** is vervangen sinds de [!DNL Experience Manager] en [!DNL Adobe Target] integratie wordt bijgewerkt in [!DNL Experience Manager] 6.5 De integratie ondersteunt de Adobe Target Standard API. De API gebruikt verificatie via Adobe IMS en [!DNL Adobe I/O Runtime]. Het ondersteunt de groeiende rol van Adobe Launch naar instrument [!DNL Experience Manager] De optiewizard is functioneel niet relevant op pagina&#39;s voor analyse en personalisatie. | Systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O Runtime] integratie via de respectieve [!DNL Experience Manager] cloudservices. |
| Connectors | De Adobe JCR Connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is vervangen voor [!DNL Experience Manager] 6.5 | N.v.t. |

## Bekende problemen{#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST.
 -->
<!-- REMOVED AS PER CQDOC-20022, JANUARY 23, 2023 * If you install [!DNL Experience Manager] 6.5 Service Pack 10 or a previous service pack on [!DNL Experience Manager] 6.5, the runtime copy of your assets custom workflow model (created in `/var/workflow/models/dam`) is deleted.
To retrieve your runtime copy, Adobe recommends to synchronize the design-time copy of the custom workflow model with its runtime copy using the HTTP API:
`<designModelPath>/jcr:content.generate.json`. -->

* Werk uw GraphQL-query&#39;s die mogelijk een aangepaste API-naam voor uw inhoudsmodel hebben gebruikt bij om in plaats daarvan de standaardnaam van het inhoudsmodel te gebruiken.

* Een GraphQL-query kan de opdracht `damAssetLucene` index in plaats van de `fragments` index. Deze handeling kan resulteren in GraphQL-query&#39;s die mislukken of die lang duren.

   Om het probleem te verhelpen, `damAssetLucene` moet worden gevormd om de volgende twee eigenschappen te omvatten:

   * `contentFragment`
   * `model`

   Nadat de indexdefinitie is gewijzigd, is opnieuw indexeren vereist (`reindex` = `true`).

   Na deze stappen zouden de vragen van GraphQL sneller moeten presteren.

* Als [!DNL Microsoft® Windows Server 2019] ondersteunt niet [!DNL MySQL 5.7] en [!DNL JBoss® EAP 7.1], [!DNL Microsoft® Windows Server 2019] ondersteunt geen kant-en-klare installaties voor [!DNL AEM Forms 6.5.10.0].

* Als u uw [!DNL Experience Manager] -exemplaar van 6.5.0 - 6.5.4 naar het nieuwste servicepakket op Java™ 11, zie `RRD4JReporter` uitzonderingen in de `error.log` bestand. Start de instantie van [!DNL Experience Manager]. <!-- THIS BULLET POINT WAS UPDATED AS PER CQDOC-20021, JANUARY 23, 2023 -->

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De titel van de map wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] Als u de standaard-API (IMS-verificatie) van het doel gebruikt, leidt het exporteren van ervaringsfragmenten naar Doel tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van register is niet-geregistreerd.

* Wanneer u probeert inhoudsfragmenten, sites of pagina&#39;s te verplaatsen, te verwijderen of te publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald, omdat de achtergrondquery mislukt. De functionaliteit werkt dus niet.
Om correcte verrichting te verzekeren, moet u de volgende eigenschappen aan de knoop van de indexdefinitie toevoegen `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

* In AEM Forms werkt het POP3-protocol niet met e-maileindpunten voor Microsoft® Office 365.
* Op JBoss® 7.1.4-platform, wanneer de gebruiker AEM 6.5.16.0-servicepack installeert, `adobe-livecycle-jboss.ear` implementatie mislukt.

## OSGi-bundels en inhoudspakketten inbegrepen{#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.17.0: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.17.0](/help/release-notes/assets/65170_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lijst van inhoudspakketten opgenomen in Experience Manager 6.5.17.0](/help/release-notes/assets/65170_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Contact opnemen met de Adobe Klantenondersteuning](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

