---
title: Opmerkingen bij de release [!DNL Adobe Experience Manager] 6,5
description: '"Zoek naar releasegegevens, wat is nieuw, installeer hoe kan worden gewijzigd en een gedetailleerde wijzigingslijst voor [!DNL Adobe Experience Manager] 6.5."'
mini-toc-levels: 3
source-git-commit: 783edcdf0f96426008b6f824a7aa0aa0deb5c613
workflow-type: tm+mt
source-wordcount: '2548'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] 6.5 Laatste Opmerkingen bij de release Service Pack {#aem-service-pack-release-notes}

<!-- For an itemized list of all issues found in these release notes, see the following spreadsheet: https://adobe-my.sharepoint.com/:x:/r/personal/anujkapo_adobe_com/_layouts/15/Doc.aspx?sourcedoc=%7B3ea81ae4-e605-4153-b132-f2698c86f84e%7D&action=edit&wdinitialsession=d8c7b903-87fc-4f2d-9ef2-542a82169570&wdrldsc=3&wdrldc=1&wdrldr=SessionMemoryQuotaExceededDuringSession&cid=a915e87c-369a-480c-9daf-d13efc766798 -->

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.14.0. <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Date | 25 augustus 2022 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.14.0.zip) <!-- UPDATE FOR EACH NEW RELEASE --> |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5.14.0. {#what-is-included-in-aem-6514}

[!DNL Experience Manager] 6.5.14.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, insectenmoeilijke situaties, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de aanvankelijke beschikbaarheid van 6.5 in April 2019 worden vrijgegeven. [Dit servicepack installeren](#install) op [!DNL Experience Manager] 6.5 <!-- UPDATE FOR EACH NEW RELEASE -->

<!-- Some of the key features and improvements are the following:

* _REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS YOU WANT TO HIGHLIGHT IN THIS RELEASE?_

* Added support for password reset for Dynamic Media Classic users within Experience Manager. (ASSETS-10298) -->

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

## [!DNL Assets] {#assets-6514}

* Kan geen codes toevoegen of weergeven voor PDF-bestanden. (NPR-38452)
* Wanneer u Aangesloten Middelen vormt, sparen de configuratie, heropent de configuratiepagina, en test de reeds bewaarde configuratie, ontbreekt de testverbinding. (NPR-38507)
* Kan gebruikers met een numerieke gebruikersnaam niet toevoegen aan verzamelingen. (NPR-38538)
* Experience Manager kan het op de auteurinstantie geïnstalleerde MPEG-bestand niet verwerken. (NPR-38568)
* PDF-verwerking mislukt met een `NoClassDefFoundError` foutbericht. (NPR-38741)
* De knop Toevoegen onder Aangepaste kolommen wordt niet correct weergegeven wanneer u een elementrapport maakt voor `de_DE` landinstelling. (ACTIVA-10641)
* Wanneer u een dubbel middel uploadt naar de gegevensopslagplaats van Digital Asset Management en Experience Manager detecteert en een optie biedt om het dubbele element te verwijderen, wordt het oorspronkelijke middel ook verwijderd uit de gegevensopslagruimte. (ACTIVA-10826)
* Experience Manager slaat de metagegevens van de map niet correct op wanneer u speciale tekens in meerdere velden opgeeft. (ACTIVA-10721)
* Kan de eigenschappen van het element niet opslaan totdat u klikt **[!UICONTROL Save & Close]** twee keer. (ACTIVA-12040)
* De schermlezer kondigt alleen het `Relate` knop. De `Relate` Deze knop bevat ook een submenu en kan worden uitgevouwen en samengevouwen. (ACTIVA-6938)
* Vereiste ARIA-kenmerken (Toegankelijke Rich Internet Applications) `aria-expanded` for `role="combo box"` ontbreekt. (ACTIVA-6928)
* In de kaartweergave, in het navigatiegebied voor het hoofdbestand, de tekstinhoud **[!UICONTROL Sort by]** heeft niet minstens een contrastverhouding van 4,5:1 tegen de achtergrondkleur. (ACTIVA-6926)
* Experience Manager identificeert niet **[!UICONTROL Select a Workflow model]** vervolgkeuzelijst als een vereist veld tijdens het maken van een workflowmodel. (ACTIVA-6871)

>[!NOTE]
>
>Smart Content Services is niet beschikbaar voor nieuwe Experience Manager Assets On-Premise-klanten vanaf 1 september 2022. Geen invloed op bestaande klanten op locatie en Adobe Managed Services die deze mogelijkheid al hebben ingeschakeld.

### [!DNL Dynamic Media] {#dynamic-media-6514}

* Voeg ondersteuning toe voor het opnieuw instellen van wachtwoorden voor Dynamic Media Classic-gebruikers binnen de Experience Manager. (ACTIVA-10298)
* Slimme uitsnijdingen die worden gegenereerd voor afbeeldingen met een transparante achtergrond, hebben een witte achtergrond. (ACTIVA-13148)
* Dynamic Media genereert geen miniaturen voor EPS-bestanden. (ACTIVA-10959)
* Elementen die niet naar een Dynamic Media-account worden geüpload omdat er een parameter voor uploaden ontbreekt. (ACTIVA-13165)
* Sta toe dat elementen met namen groter dan 127 tekens naar Dynamic Media worden geüpload. (ACTIVA-9991)
* Inschakelen van JavaScript ES6 (ECMAScript 6) voor Dynamic Media Viewers op Experience Manager 6.5.14.0. (NPR-38393)
* Opties configureren in Dynamic Media **[!UICONTROL General Settings]** en **[!UICONTROL Publish Setup]** niet toegankelijk moeten zijn voor gebruikers die geen beheerder zijn. (ACTIVA-8628)
* Dynamic Media **[!UICONTROL General settings]** de reeds gevormde uploadparameters niet correct tonen. (ACTIVA-10245)
* De gebruikersinterface van de Experience Manager toont geen mislukkingsbericht in het geval de vastgestelde verwezenlijking/de update ontbreekt. (ACTIVA-10264)
* Kan een opgeslagen beleid niet toepassen op een van de containers van een bewerkbare sjabloon om Dynamic Media-componenten toe te voegen. (ACTIVA-11044)
* Middelen die niet naar Dynamic Media-account worden geüpload nadat de Dynamic Media Reprocess Assets-workflow is uitgevoerd op middelen met een onjuiste taakhandgreep. (ACTIVA-12084, ACTIVA-9877)
* Gebruikers van schermlezers worden beïnvloed door de `title` kenmerk niet opgegeven `<frame>` en `<iframe>` in de **[!UICONTROL Type to Search]** in. (ACTIVA-5483)
* In schermlezers, verwant en zinvol `alt=` waarde moet worden opgegeven voor meerdere afbeeldingen die aanwezig zijn onder **[!UICONTROL Assets]** in het linkervenster. (ACTIVA-5644)
* Schermlezer kan niet worden gelezen **[!UICONTROL Mute]** en **[!UICONTROL Unmute]** op video met Dynamic Media-component. (ACTIVA-10169)

## Handel {#commerce-6514}

* De producten van de handel worden niet gesorteerd gebruikend de kolomkopbal en het gebruikt _extern_ sorteermodus; in plaats daarvan, zouden de producten van de Handel gesorteerd moeten worden gebruikend kolomkopballen met _lokaal_ sorteermodus. (CQ-4343750, NPR-38498)

## [!DNL Forms] {#forms-6514}

>[!NOTE]
>
>* [!DNL Experience Manager Forms] geeft toe:voegen-on pakketten één week na gepland vrij [!DNL Experience Manager] Releasedatum van Service Pack. In dit geval worden de invoegpakketten op donderdag 1 september 2022 uitgebracht. Daarnaast wordt een lijst met Forms-correcties en -verbeteringen toegevoegd aan deze sectie.


## Integrations {#integrations-6514}

* Ondersteuning voor JavaScript ES6-compilatie (ECMAScript6-modus of hoger) inschakelen voor minificatie van de `/libs/cq/analytics/widgets.js` bibliotheek. (NPR-38433)
* Ondersteuning voor JavaScript ES6-compilatie (ESMAScript6-modus of hoger) inschakelen voor minificatie van de `/libs/cq/testandtarget/clientlibs/testandtarget/util.js` bibliotheek. (NPR-38435)
* Hoe meer inhoud er is in `/content/campaigns`, langer de vraag aan `targeteditor.html` (`/libs/cq/personalization/touch-ui/content/targeteditor.html`) wordt uitgevoerd wanneer u de Pagina-editor opent. (NPR-38663)

## Platform {#platform-6514}

* Kan zich niet aanmelden bij Package Manager om updates te implementeren. (NPR-38646)
* In de gebruikersinterface van de tagkiezer voor middelen worden tags weergegeven in de volgorde waarin ze zijn gemaakt. Als er echter veel tags zijn, is het moeilijk de tags weer te geven en te beheren, omdat ze niet kunnen worden gesorteerd. (CQ-4344279)
* Creeer een bericht in het gebruikersinterface wanneer een gebruiker die door een beheerder of iemand anders wordt nagedacht gebruikend **[!UICONTROL Impersonate as]** veld. (CQ-4345288)
* In een Slimme Inzameling, werden alle activa getoond wanneer het filtreren gebruikend een bewaarde onderzoek. (CQ-4345326)
* Er wordt een onjuist aantal geselecteerde elementen weergegeven voor **[!UICONTROL Add to collection]** wanneer **[!UICONTROL Select All]** is geselecteerd. (CQ-4345424)
* Er is een uitzonderingsbericht opgetreden bij het gebruik van de **[!UICONTROL Impersonate as]** veld met een groep of een niet-bestaande gebruiker. (CQ-4346098)

## [!DNL Sites] {#sites-6514}

* Onverwachte wegschrappingen kwamen voor terwijl het bevorderen van Experience Manager van 6.5.12.0 aan 6.5.13.0. (NPR-38532)

### Toegankelijkheid {#access-6514}

* Wanneer u in Experience Manager Sites de **[!UICONTROL Switch display format and adjust display setting]** selecteert u vervolgens **[!UICONTROL List View]** de **[!UICONTROL Drag and Drop]** ontbreekt een toegankelijke naam. (SITES-2863, NPR-38760)
* Schermlezer moet de toegankelijke naam, zoals `Show description for Archive` of `Show description for mini shopping cart`. De huidige toegankelijke naam wordt echter aangekondigd als `Info Circle button show description` for _alles_ de knoppen met informatie over knoppen voor knopinfo. (SITES-3104)
* Verbeter ongedaan maken voor componenten die geen inlineEditing of dropTarget eigenschap in hebben `cq:editConfig`. (NPR-38361) <!-- version 2 (old) of the description above * When out of the box components that don't have inlineEditing or dropTarget feature in the _cq_editConfig file (navigation, breadcrumb, embed) are deleted > undeleted (by way of Undo), all configurations are lost and empty placeholder reappears. Component must be reconfigured from scratch. (NPR-38361) -->
* De vervolgkeuzelijst Stijlsysteem kan boven aan de pagina zijn geplaatst in plaats van in de context van de component - voor componenten die `cq:editConfig` &quot;afteredit: REFRESH_PAGE&quot;. (NPR-38384) <!-- version 2 (old) of description above* When selecting a style option on a component, the Styles box shifts to the upper left corner of the screen, rather than staying put below the style icon. Happens for components that have  cq:editConfig "afteredit: REFRESH_PAGE". (NPR-38384) -->
* De tekstcomponent wordt verkeerd uitgelijnd wanneer deze wordt toegevoegd aan geneste lay-outcontainers. (NPR-38193)
* Een leeg stijllusje werd getoond wanneer er geen configuratie van het Systeem van de Stijl voor een component was. Het tabblad is nu verborgen wanneer er geen configuratie aanwezig is. (NPR-38218) <!-- version 2 (old) of description above * Style tab is blank on components without styles/policies. (NPR-38218) -->
* De eigenschap `useLegacyResponsiveBehaviour` werkt alleen wanneer dit is geverifieerd. (NPR-37996)
* Als u jquery-ui bijwerkte naar de laatste versie, is de Editor verbroken. (SITES-5647)

### [!DNL Content Fragments] {#sites-contentfragments-6514}

* Validatie van het veld voor opsommingsfragmenten voor inhoud geeft de eerste keer dat het inhoudsfragment wordt geladen. (SITES-7140)
* Behoefte om de verpersoonlijkingsgebieden van de Campagne in de Rich Text Redacteur van de redacteur van de Fragments van de Inhoud toe te voegen. (NPR-38526)
* Bij het maken of bewerken van een nieuw inhoudsfragment in de Content Fragment-editor via de Dispatcher wordt het model van het inhoudsfragment niet opgeslagen. Bovendien is de editor voor inhoudsfragmenten niet gesloten en wordt een fout weergegeven in het browserlogboek. (NPR-38691)
* Validatiefout voor continue query. (NPR-38523)
* In het dialoogvenster Inhoudsfragment, onder **[!UICONTROL Properties]** de **[!UICONTROL Content Fragment]** het opgeslagen pad in het pop-upmenu Selectie niet behouden. (NPR-38632)
* Wanneer u een model van het inhoudsfragment creeert en een opsommingsgebied van het drop-down type toevoegt, de correcte bevestiging voor _`is required`_mislukt. (NPR-38237)

### Kernonderdelen {#sites-corecomponents-6514}

* De nieuwe pagina-e-mailcomponent mag u niet dwingen in de klassieke gebruikersinterface tijdens het bewerken `/etc`. (NPR-38648)

### Pagina-editor {#sites-pageeditor-6514}

* De gebruiker kan de grootte van de component niet aanpassen aan het gewenste aantal kolommen. (NPR-38688)

### Sjablooneditor {#sites-templateeditor-6514}

* Ontbreekt **[!UICONTROL Delete]** en **[!UICONTROL Cut]** knoppen op de menubalk in een bewerkbare sjabloon na een `cq:actions` eigenschap is aangepast. (NPR-38521)
* Als een component een andere component bevat, is het niet mogelijk de component binnen de sjabloonstructuur te verwijderen omdat de component **[!UICONTROL Delete]** ontbreekt in de menubalk. (NPR-38585)

## Sling {#sling-6514}

* Er is een toename opgetreden in het aantal geopende bestanden op productie als gevolg van een geheugenlek in de module `DiscoveryLiteDescriptor` in `org.apache.sling.discovery.commons`, versie 1.0.20. (NPR-38288)
* In Experience Manager, van **[!UICONTROL Operations]** > **[!UICONTROL Diagnosis]** een fout ondervindt wanneer u **[!UICONTROL Download Status ZIP]** > **[!UICONTROL Download]**. (NPR-38514)

## Vertaalprojecten {#translation-6514}

* Starten voor subpagina&#39;s die als verwijzing in een bovenliggende pagina zijn toegevoegd, werd niet bevorderd toen de pagina `isDeep` eigenschap is ingesteld op `false`. (NPR-38531)

## Gebruikersinterface {#ui-6514}

* Wanneer u **[!UICONTROL Select All]** > **[!UICONTROL Quick Publish]**, publiceerde Experience Manager niet alle activa of toonde niet aan in hoeveel activa **[!UICONTROL Card]** of **[!UICONTROL List]** weergeven. (NPR-38546)
* Onjuist aantal geselecteerde elementen wordt weergegeven voor **[!UICONTROL Add to collection]** in **[!UICONTROL Select All]** zaak. (NPR-38633)
* Uitgeschakelde gebruikers kunnen nog steeds worden toegevoegd aan verzamelingen en projecten. (NPR-38651)
* Als u een filter verwijdert zonder het zoekformulier op te slaan, treedt er een fout op. (NPR-38698)
* Een gebruikerssessie kan geen `ModifiableValueMap` bijvoorbeeld voor de groepen om het rechtstreekse groepslidmaatschap tot stand te brengen. (NPR-38710)

## Workflow {#workflow-6514}

* Ondersteuning voor JavaScript ES6-compilatie (ESMAScript6-modus of hoger) inschakelen voor minificatie van de `/libs/cq/inbox/gui/components/inbox/clientlibs/commons.js` bibliotheek. (NPR-38304)
* Nadat de werkstroom is uitgevoerd en de processtappen zijn voltooid, wordt dezelfde opmerking meerdere keren herhaald. (NPR-38364)

## Installeren [!DNL Experience Manager] 6.5.14.0. {#install}

<!-- Remaining content from here to bottom stays the same except for version updating as needed as per update team feedback. -->

* [!DNL Experience Manager] 6.5.14.0 vereist [!DNL Experience Manager] 6.5 Zie [upgradedocumentatie](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies. <!-- UPDATE FOR EACH NEW RELEASE -->
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Bij een implementatie met MongoDB en meerdere exemplaren, installeert u [!DNL Experience Manager] 6.5.14.0 op één van de instanties van de Auteur die de Manager van het Pakket gebruiken.<!-- UPDATE FOR EACH NEW RELEASE -->

>[!NOTE]
>
>Adobe raadt u niet aan de installatie van de [!DNL Experience Manager] 6.5.14.0-pakket. <!-- UPDATE FOR EACH NEW RELEASE -->

### Installeer het de dienstpak op [!DNL Experience Manager] 6,5 {#install-service-pack}

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager] -instantie.

1. Download het servicepack van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.14.0.zip). <!-- UPDATE FOR EACH NEW RELEASE -->

1. Pakketbeheer openen en vervolgens selecteren **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie voor meer informatie [Pakketbeheer](/help/sites-administering/package-manager.md).

1. Selecteer het pakket en selecteer vervolgens **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit probleem treedt meestal op in [!DNL Safari] browser, maar kan soms voorkomen op om het even welke browser.

**Automatische installatie**

Er zijn twee verschillende methoden die u automatisch kunt installeren [!DNL Experience Manager] 6.5.14.0.<!-- UPDATE FOR EACH NEW RELEASE -->

* Plaats het pakket in `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.
* Gebruik de [HTTP-API van Package Manager](/help/sites-administering/package-manager.md#package-share). Gebruiken `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Experience Manager 6.5.14.0 ondersteunt geen Bootstrap-installatie. <!-- UPDATE FOR EACH NEW RELEASE -->

**De installatie valideren**

Als u wilt weten welke platformen gecertificeerd zijn voor deze release, raadpleegt u de [technische voorschriften](/help/sites-deploying/technical-requirements.md).

1. De pagina met productinformatie (`/system/console/productinfo`) geeft de bijgewerkte versietekenreeks weer `Adobe Experience Manager (6.5.14.0)` krachtens [!UICONTROL Installed Products]. <!-- UPDATE FOR EACH NEW RELEASE -->

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De OSGi-bundel `org.apache.jackrabbit.oak-core` is versie 1.2.2.12 of hoger (webconsole gebruiken: `/system/console/bundles`). <!-- NPR-38747 -->


### Installeren [!DNL Experience Manager] Forms-invoegtoepassing {#install-aem-forms-add-on-package}

>[!NOTE]
>
>Overslaan als u dit niet gebruikt [!DNL Experience Manager] Forms. Oplossingen in [!DNL Experience Manager] Forms wordt één week na de geplande levering geleverd via een afzonderlijk invoegpakket [!DNL Experience Manager] Service Pack-release.

1. Controleer of u de [!DNL Experience Manager] Service Pack.
1. Download het overeenkomstige Forms-add-on-pakket dat is vermeld op [AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates) voor uw besturingssysteem.
1. Het Forms-invoegtoepassingspakket installeren zoals beschreven in [AEM Forms-add-onpakketten installeren](/help/forms/using/installing-configuring-aem-forms-osgi.md#install-aem-forms-add-on-package).
1. Als u letters gebruikt in Experience Manager 6.5 Forms, installeert u de [nieuwste AEMFD-compatibiliteitspakket](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html#forms-updates).

### Installeren [!DNL Experience Manager] Forms op JEE {#install-aem-forms-jee-installer}

>[!NOTE]
>
>Sla dit over als u AEM Forms niet gebruikt op JEE. Oplossingen in [!DNL Experience Manager] Forms op JEE wordt via een afzonderlijk installatieprogramma geleverd.

Voor informatie over het installeren van het cumulatieve installatieprogramma voor [!DNL Experience Manager] Forms op JEE en configuratie na implementatie, zie [releaseopmerkingen](jee-patch-installer-65.md).

>[!NOTE]
>
>Na installatie van het cumulatieve installatieprogramma voor [!DNL Experience Manager] Forms on JEE, installeer het nieuwste Forms add-on pakket, verwijder het Forms add-on pakket uit het `crx-repository\install` en start de server opnieuw op.

### UberJar {#uber-jar}

The UberJar for [!DNL Experience Manager] 6.5.13.0 is beschikbaar in de [Maven Central-opslagplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.13/). <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

>[!NOTE]
>
>Houd er in Experience Manager 6.5.14.0 rekening mee dat de UberJar-versie (6.5.13.0) hetzelfde blijft als de vorige versie.

Om UberJar in een Geweven project te gebruiken, zie [gebruiken van UberJar](/help/sites-developing/ht-projects-maven.md) en neem het volgende gebiedsdeel in uw project POM op: <!-- CHECK FOR UPDATE EACH NEW RELEASE -->

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.13</version>
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
| Integraties | De **[!UICONTROL AEM Cloud Services Opt-In]** het scherm is verouderd sinds [!DNL Experience Manager] en [!DNL Adobe Target] integratie wordt bijgewerkt in [!DNL Experience Manager] 6.5 De integratie ondersteunt de Adobe Target Standard API. De API gebruikt verificatie via Adobe IMS en [!DNL Adobe I/O Runtime]. Het ondersteunt de groeiende rol van Adobe Launch naar instrument [!DNL Experience Manager] De optiewizard is functioneel niet relevant op pagina&#39;s voor analyse en personalisatie. | Systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O Runtime] integratie via de respectieve [!DNL Experience Manager] cloudservices. |
| Connectors | De Adobe JCR Connector voor Microsoft® SharePoint 2010 en Microsoft® SharePoint 2013 is vervangen voor [!DNL Experience Manager] 6.5 | N.v.t. |

## Bekende problemen {#known-issues}

<!-- THESE KNOWN ISSUES CARRY OVER EACH RELEASE. THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THE LIST.
 -->

* [Inhoudsfragment AEM met GraphQL Index Package 1.0.3](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Ffeaturepack%2Fcfm-graphql-index-def-1.0.3.zip)

* Als [!DNL Microsoft® Windows Server 2019] ondersteunt niet [!DNL MySQL 5.7] en [!DNL JBoss® EAP 7.1], [!DNL Microsoft® Windows Server 2019] ondersteunt geen kant-en-klare installaties voor [!DNL AEM Forms 6.5.10.0].

* Als u een upgrade uitvoert op uw [!DNL Experience Manager] van 6.5 tot 6.5.10.0 versie, kunt u bekijken `RRD4JReporter` uitzonderingen in de `error.log` bestand. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 10 of een vorig de dienstpak op [!DNL Experience Manager] 6.5, de runtime kopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) wordt geschrapt.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Gebruikers kunnen de naam wijzigen van een map in een hiërarchie in [!DNL Assets] en publiceer een geneste map naar [!DNL Brand Portal]. De titel van de map wordt echter niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van [!DNL Experience Manager] 6.5.x.x:
   * &quot;Wanneer de Adobe Target-integratie is geconfigureerd in [!DNL Experience Manager] Als u de standaard-API (IMS-verificatie) van het doel gebruikt, leidt het exporteren van ervaringsfragmenten naar Doel tot onjuiste aanbiedingstypen die worden gemaakt. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/bron &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De validatie aan de adaptieve formulierserver-side mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt (CQ-4274424).
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.
   * `com.adobe.cq.social.cq-social-jcr-provider bundle com.adobe.cq.social.cq-social-jcr-provider:1.3.5 (395)[com.adobe.cq.social.provider.jcr.impl.SpiSocialJcrResourceProviderImpl(2302)]` : Time-out bij wachten op wijziging van register is niet-geregistreerd.

* Wanneer u probeert inhoudsfragmenten of sites/pagina&#39;s te verplaatsen/verwijderen/publiceren, is er een probleem wanneer verwijzingen naar inhoudsfragmenten worden opgehaald, omdat de achtergrondquery mislukt. De functionaliteit werkt dus niet.
Om correcte verrichting te verzekeren, moet u de volgende eigenschappen aan de knoop van de indexdefinitie toevoegen `/oak:index/damAssetLucene` (opnieuw indexeren is niet vereist):

   ```xml
   "tags": [
       "visualSimilaritySearch"
     ]
   "refresh": true
   ```

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.14.0: <!-- UPDATE FOR EACH NEW RELEASE -->

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.14.0](/help/release-notes/assets/65140_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [Lijst van inhoudspakketten opgenomen in Experience Manager 6.5.14.0](/help/release-notes/assets/65140_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* [Contact opnemen met de Adobe Klantenondersteuning](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] productpagina](https://business.adobe.com/products/experience-manager/adobe-experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

