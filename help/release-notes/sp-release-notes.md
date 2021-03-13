---
title: '[!DNL Experience Manager] Opmerkingen bij de release van 6.5 servicepack'
description: Opmerkingen bij de release specifiek voor  [!DNL Adobe Experience Manager] 6.5 service pack 8
docset: aem65
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 89b037fbde6003ccf86336c4467df415e233986b
workflow-type: tm+mt
source-wordcount: '2760'
ht-degree: 0%

---


# [!DNL Adobe Experience Manager] Opmerkingen bij de release van 6.5 servicepack  {#aem-service-pack-release-notes}

## Informatie {#release-information} opheffen

| Producten | [!DNL Adobe Experience Manager] 6,5 |
| -------- | ---------------------------- |
| Versie | 6.5.8.0. |
| Type | Service Pack-release |
| Date | 11 maart 2021 |
| URL downloaden | [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.8.zip) |

<!-- TBD: Update the SD link when SP8 is available. Same link is duplicated below in install -->

## Wat is inbegrepen in [!DNL Adobe Experience Manager] 6.5.8.0 {#what-s-included-in-aem}

[!DNL Adobe Experience Manager] 6.5.8.0 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en prestaties, stabiliteit, en veiligheidsverbeteringen, die sinds de beschikbaarheid van 6.5 versie in April 2019 worden vrijgegeven. Het servicepack is geïnstalleerd op [!DNL Adobe Experience Manager] 6.5.

De belangrijkste eigenschappen en de verhogingen die in [!DNL Adobe Experience Manager] 6.5.8.0 worden geïntroduceerd zijn:

<!-- TBD:
* Using the Connected Assets functionality, it is now possible to connect up to 3 [!DNL Sites] instances with 1 [!DNL Assets] instances. The configuration user interface now allows the administrators to provide the details of these [!DNL Sites] instances. -->

* Wanneer u [Functionaliteit voor verbonden elementen](/help/assets/use-assets-across-connected-assets-instances.md) gebruikt, kunt u nu een lijst weergeven met alle [!DNL Sites] pagina&#39;s die het element gebruiken. Deze verwijzingen naar een element zijn beschikbaar op de pagina [!UICONTROL Properties] van een element. Op deze manier kunnen beheerders, marketers en bibliothecarissen een volledig overzicht van het gebruik van bedrijfsmiddelen krijgen, zodat ze het bedrijfsmerk beter kunnen bijhouden, beheren en het merk consistenter zijn.

* Als u een element verwijdert waarnaar in een webpagina wordt verwezen, wordt [!DNL Experience Manager] [een waarschuwing ](/help/assets/use-assets-across-connected-assets-instances.md#asset-usage-references) weergegeven. U kunt een element waarnaar wordt verwezen, forceren verwijderen of de verwijzingen controleren en wijzigen die op de pagina [!DNL Properties] van het element worden weergegeven. Als u op de referenties klikt, worden de lokale en externe [!DNL Sites] pagina&#39;s geopend.

* De pagina&#39;s van Live Copy die beschikbaar zijn voor rollout sorteren met de eigenschappen [!UICONTROL Name], [!UICONTROL Last modified date,] en [!UICONTROL Last rollout date].

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar 1.2.2.6. <!-- TBD: Mention the version -->

Voor een volledige lijst van eigenschappen en verhogingen die in [!DNL Experience Manager] 6.5.8.0 worden geïntroduceerd, zie [nieuw in  [!DNL Adobe Experience Manager] 6.5 Service Pack 8](new-features-latest-service-pack.md).

Hieronder volgt een lijst met oplossingen die is opgenomen in [!DNL Experience Manager] 6.5.8.0-release.

### [!DNL Sites] {#sites-6580}

* Wanneer een pagina naar een blauwdruk wordt verplaatst, wordt de bestemming van koppelingen niet bijgewerkt (NPR-35724).
* Op Tizen gebaseerde speler kan niet worden geverifieerd voor bepaalde browsers. Het probleem treedt op bij browsers die het kenmerk samesite=none niet ondersteunen (NPR-35589).
* Een niet-vergrendelde responsieve container geeft geen toegestane onderdelen weer (NPR-35565).
* Wanneer u een live kopie van een zojuist toegevoegde pagina maakt, maakt de master taal twee kopieën voor elk domein (NPR-35545).
* Deadlock in de SCR Registratie van de Component wanneer vele draden wegens `org.apache.felix.scr.impl.ComponentRegistry` tijdopnemer worden geblokkeerd. Als gevolg hiervan reageert [!DNL Experience Manager] niet langer voor onbepaalde tijd (GRANITE-33125,FELIX-6252).
* Wanneer u een specifiek middel in de zijspoorstaaf zoekt, bevat het resultaat sommige niet-gezochte activa (NPR-35524).
* Wanneer u SSL voor een instantie van de Experience Manager toelaat, wordt de contextweg verwijderd (NPR-35477).
* Wanneer u een lijst creeert, voeg wat tekst als eerste element toe, voeg een lijst als tweede element toe, en voeg een lijst binnen de lijst toe, vervormt de ouderlijst (NPR-35465).
* Wanneer u verschillende plug-ins gebruikt op opeenvolgende lijstitems, wordt een extra <br>-tag toegevoegd aan de lijstitems (NPR-35464).
* Wanneer een lijst tussen twee paragrafen wordt geplaatst, kunt u geen lijst aan de lijst (NPR-35356) toevoegen.
* Wanneer u een AEM instantieverbetering van AEM 6.3 tot AEM 6.5 begint, duurt de verbeteringsinstantie langer om (NPR-35323) te beginnen.
* Wanneer u een AEM element dupliceert dat een haakje () bevat. in de naam, ontbreekt de replicatie (GRANITE-27004, NPR-35315).
* Wanneer u koppen toevoegt aan een RTF-editor, is de alineaknop uitgeschakeld (NPR-35256).
* Wanneer u een punt aan een bestaande lijst toevoegt, schrapt het het opvouwen of knevellijst (NPR-35206).
* Als de optie Pagina uitrollen is geselecteerd, wordt een dialoogvenster weergegeven met alle beschikbare live kopieën en wordt de functie automatisch uitrollen uitgevoerd. De live kopieën van pagina&#39;s worden zonder tussenkomst van de gebruiker naar alle geografische gebieden uitgerold (NPR-35138).
* Wanneer u de optie Inclusief onderliggende pagina&#39;s gebruikt, worden niet alle pagina&#39;s vermeld met de optie Publicatie beheren. Er worden slechts 22 pagina&#39;s vermeld (NPR-35086).
* Wanneer een beleid wordt uitgegeven, behoudt de tekstcomponent niet de beleidsveranderingen (NPR-35070).
* Wanneer u een aantal items in een genummerde lijst inspringt, behouden alle items hetzelfde nummer, maar de nummering moet beginnen bij 1 voor items met dezelfde inspringing (CQ-4313011).
* Wanneer minificatie is ingeschakeld, kunt u geen enkele pagina of component bewerken. De kwesties begonnen na het installeren AEM 6.5 Service Pack 7 (CQ-4311133).
* Universeel zoek- en assetfilters retourneren irrelevant of geen resultaten (CQ-4312322, NPR-35793).
* Wanneer meerdere pagina&#39;s tegelijk toegang krijgen tot een clientbibliotheek, kan de HTML-bibliotheekbeheerder de clientbibliotheek niet laden. Dit leidt tot een onjuiste weergave van pagina&#39;s (NPR-35538).
* Het contextpad wordt automatisch verwijderd wanneer u een SSL instelt in [!DNL Experience Manager] (NPR-35294).
* De manager van het pakket registreert geen gebruikers na het klikken van de Logout optie (NPR-35160).

### [!DNL Assets] {#assets-6580}

[!DNL Adobe Experience Manager] 6.5.8.0  [!DNL Assets] verhelpt de volgende problemen en biedt de volgende verbeteringen.

* Na het herstellen van een vorige versie van activa, wordt de gebeurtenis DamEvent.Type RESTORED niet teweeggebracht in de console OSGi (NPR-35789).
* `IndexWriter.merge` veroorzaakt  `OutOfMemoryError` fout aangezien de slimme etiketteringsfunctionaliteit grote  `/oak:index/lucene` en  `/oak:index/ntBaseLucene` indexen (NPR-35651) leidt.
* Er wordt een foutbericht weergegeven wanneer u een tekstmap [!UICONTROL Asset Contribution] met multibyte-tekens in de naam probeert op te slaan (NPR-35605).
* Wanneer trapsgewijze subtypevelden voor metagegevens worden gebruikt, treedt de fout &#39;Dit veld invullen&#39; op (NPR-35643).
* Wanneer een bestaand element wordt gesleept in de [!DNL Assets]-gebruikersinterface en er wordt een nieuwe versie gemaakt, zijn de wijzigingen in de metagegevens niet blijvend (NPR-34940).
* Wanneer het creëren van regels in de redacteur van het meta-gegevensschema voor een trapsgewijs menu, herhaalt de [!UICONTROL Dependant On] optie de zelfde naam (NPR-35596).
* Het zoeken op basis van gelijkenis werkt niet nadat u [!UICONTROL Assets Admin Search Rail] (NPR-35588) hebt bewerkt.
* Als u vanuit een map de zoekopdracht naar elementen opent in de linkertrack door op [!UICONTROL Filter] te klikken, werkt het filter in [!UICONTROL Status] > [!UICONTROL Checkout] > [!UICONTROL Checked out] niet (NPR-35530).
* Als u probeert alle slimme tags van een element te verwijderen en de wijzigingen op te slaan, worden de tags niet verwijderd. De gebruikersinterface geeft echter aan dat de wijzigingen worden opgeslagen (NPR-35519).
* Gebruikers kunnen elementen in de lijstweergave niet opnieuw rangschikken of sorteren in een bestelbare map (NPR-35516).
* Als u het standaardmetagegevensschema bewerkt, verandert het tagveld op de pagina [!UICONTROL Properties] van het element in een tekstveld. Door de wijziging kunnen onbewuste gebruikers tags op aanvraag toevoegen en worden de tags als een tekenreeks opgeslagen in de opslagplaats (NPR-35478).
* Als u tijdens het downloaden van een element een naam opgeeft die geen geldig e-mailadres heeft, is de downloadoptie niet beschikbaar. Als er echter een andere optie in het dialoogvenster Downloaden is geselecteerd, wordt de knop ingeschakeld, maar wordt geen e-mail verzonden (NPR-35365).
* Gebruikers kunnen hun middelen niet inchecken nadat ze de middelen in [!DNL Adobe InDesign] hebben bewerkt en een fout over een gebrek aan machtigingen ontvangen (NPR-35341).
* Handlebars JavaScript bibliotheek wordt bevorderd aan v4.7.6 (NPR-35333).
* De interface van de metagegevenseditor werkt niet meer zoals u had verwacht wanneer u begint met het bewerken van bulkmetagegevens en items deselecteert totdat één item geselecteerd blijft (NPR-35144).
* De globale navigatie opent niet de correcte console wanneer geklikt binnen `assets.html` pagina (CQ-4312311).
* [!DNL Assets] geeft geen RGB-uitvoering weer voor een element met RGB-uitvoering (CQ-4310190).
* De optie [!UICONTROL Relate] in het menu wordt niet correct weergegeven op de pagina [!UICONTROL Properties] (CQ-4310188).
* Als filetype filter voor documenten wordt gebruikt om activa te zoeken en een Slimme Inzameling tot stand te brengen, wordt de filter niet toegepast wanneer de inzameling wordt betreden. In plaats daarvan worden alle typen elementen weergegeven in de zoekopdracht (NPR-35759).
* U kunt geen activa in een Lichtbak van [!DNL Assets] gebruikersinterface (NPR-35901) slepen en toevoegen.
* Wanneer een nieuwe versie van een bestaand element wordt gemaakt nadat het naamconflict is opgelost, worden de metagegevens van het oorspronkelijke element overschreven (CQ-4313594).
* Wanneer u het zoeken van elementen filtert met een zoekfilter of voorspeld, een element opent om het te bekijken of te bewerken en teruggaat naar de pagina met zoekresultaten, werkt het filter niet. Alle gezochte activa zijn vermeld ongefilterd (NPR-35913).

#### [!DNL Dynamic Media] {#dynamic-media-6580}

* De optie URL voor de voorinstelling van een RESS-afbeelding wordt ingeschakeld op de pagina met elementdetails. Nu zijn zowel URL- als RESS-opties beschikbaar op de pagina met elementdetails wanneer de RESS-voorinstelling is geselecteerd in de sectie met dynamische uitvoeringen. (CQ-4311241)
* Interactieve mediacomponent - interactieve video werkt niet als de gebruiker [!DNL Experience Manager] met selectieve publicatieconfiguratie heeft (CQ-4311054).
* Als u middelen over omslagen beweegt, is de synchronisatie tussen [!DNL Experience Manager] en [!DNL Dynamic Media–Scene7] via API zeer langzaam (CQ-4310001).
* Bij gebruik van Omnissearch neemt de grootte van de logs aanzienlijk toe (CQ-4309153).
* Wanneer selectieve synchronisatie is ingeschakeld en een element wordt gekopieerd (niet verplaatst) naar een synchronisatiemap, wordt het niet gesynchroniseerd zoals u had verwacht (CQ-4307122).
* Voor geüploade elementen die automatisch naar DM worden gepubliceerd, wordt de status niet weergegeven bij AEM. Bovendien wordt in de statuskolom Dynamic Media Publish niet de juiste gepubliceerde status weergegeven (CQ-4306415).
* Als een element wordt gepubliceerd op [!DNL Experience Manager] en bij activering wordt ingesteld om naar [!DNL Dynamic Media] te publiceren, wordt de metagegevenswaarde `scene7FileStatus` niet naar behoren bijgewerkt (CQ-4308269).
* Als u het videoprofiel bewerkt, worden de hoogte- en bitsnelheidwaarden die zijn ingesteld voor de videovoorinstelling niet weergegeven in [!DNL Experience Manager]. De velden worden leeg weergegeven (CQ-4311828).

### [!DNL Commerce] {#commerce-6580}

* Kan geen aangepaste tag maken voor alle producten in de handel (CQ-4310682).

* De update van de verwijzing van het productelement veroorzaakt replicatiedraden om in de wachtstand te zijn tot de draad ProductAssetListener zijn verplichtingen aan JCR voltooit (NPR-35269).

### Platform {#platform-6580}

* Wanneer u een component van de Mening van het Lusje van het Koraal zonder lusjes gebruikt en dan een validator van de Stichting teweegbrengt, komt de volgende fout voor (NPR-35636):

   ```TXT
    Uncaught TypeError: Cannot set property 'invalid' of undefined
     at enable (foundation.js:10703)
     at foundation.js:10710
   ```

* SCD door:sturen replicatie ontbreekt voor de gebeurtenissen van de Schrapping voor knopen die een komma in de naam (NPR-35191) omvatten.

* Nadat u aan AEM 6.5.7 bevordert, beginnen de bouwstijlen te ontbreken. De reden hiervoor is dat een oude versie of geen cola van de nakker is ingebed in de uber-jar (GRANITE-33006).

### Gebruikersinterface {#ui-6580}

* Wanneer u van de mening van de Kaart aan de mening van de Lijst voor documenten in een omslag in de console van Activa overschakelt, werkt het sorteren niet geschikt (NPR-35842).

* Wanneer u tekst in een tekstcomponent hyperlinkt, geeft de zoekfunctie niet de juiste resultaten weer (NPR-35849).

* Wanneer geen waarde wordt verstrekt aan een verborgen gebied dat wordt gemerkt vereist, verhindert het u een component (NPR-35219) op te slaan.

### Integrations {#integrations-6580}

* Wanneer u verschillende waarden voor IMS huurder ID en de code van de Cliënt van het Doel gebruikt, [!DNL Experience Manager] kan niet integreren met [!DNL Adobe Target] (NPR-35342).

### Omzettingsprojecten {#translation-6580}

* Problemen bij het exporteren of importeren van een vertaaltaak in [!DNL Experience Manager] (NPR-35259).

### Campagne {#campaign-6580}

* Wanneer u een campagnepagina maakt met een out-of-the-box-sjabloon in Touch UI en het tabblad E-mail opent in het dialoogvenster met pagina-eigenschappen, blijft de variabele voor de personalisatie van het onderwerp en de tekstvelden uitgeschakeld (CQ-4312388).

### [!DNL Communities] {#communities-6580}

* Bij het toevoegen van een paginastructuur aan een communautaire groep, wordt de [!UICONTROL Group] titel in de broodkruimel veranderd in de titel van eerste [!UICONTROL Page] (NPR-35803).
* In tegenstelling tot moderatoren is een standaardlid van de community geen toegang tot een ontwerppost (NPR-35339) en kan het deze niet bewerken.
* Verbroken toegangscontrole en ontkenning van de dienst met DSRPReindexServlet die de plaats van gemeenschappen neer brengt tot het indexeren volledig is (NPR-35591).
* Als u [!UICONTROL All Users] uit het veld [!UICONTROL Administrators] verwijdert, worden deze niet daadwerkelijk uit het achterste gedeelte verwijderd (NPR-35592, NPR-35611).
* De component [!UICONTROL Compose Message] retourneert geen resultaat wanneer de ingevoerde tekst gedeeltelijk overeenkomt (NPR-35666).

### [!DNL Brand Portal] {#brandportal-6580}

* Als u een lid toevoegt aan een [!UICONTROL Asset Contribution]-typemap, wordt het bijschrift [!UICONTROL Add User or Group] weergegeven in de gebruikersinterface, hoewel alleen actieve gebruikers van het Brand Portal worden ondersteund en geen groepen (NPR-35332).

### [!DNL Forms] {#forms-6580}

>[!NOTE]
>
>[!DNL Experience Manager Forms] geeft toe:voegen-op pakketten één week na de geplande de versiedatum van het  [!DNL Experience Manager] Service Pack vrij.

Voor informatie over veiligheidsupdates, zie [pagina van de veiligheidsbulletins van de Experience Manager](https://helpx.adobe.com/security/products/experience-manager.html).

## Installatie 6.5.8.0 {#install}

**Instellingsvereisten en meer informatie**

* Experience Manager 6.5.8.0 vereist Experience Manager 6.5. Zie [upgrade documentation](/help/sites-deploying/upgrade.md) voor gedetailleerde instructies.
* De download van het de dienstpak is beschikbaar op Adobe [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html).
* Voor een plaatsing met MongoDB en veelvoudige instanties, installeer Experience Manager 6.5.8.0 op één van de instanties van de Auteur gebruikend de Manager van het Pakket.

>[!NOTE]
>
>Adobe raadt u niet aan het [!DNL Adobe Experience Manager] 6.5.8.0-pakket te verwijderen of te verwijderen.

### Installeren van het servicepack {#install-service-pack}

Voer de volgende stappen uit om het servicepack te installeren op een [!DNL Adobe Experience Manager] 6.5-exemplaar:

1. Start de instantie opnieuw vóór de installatie als de updatemodus voor de instantie is geactiveerd (dit is het geval wanneer de instantie is bijgewerkt vanaf een eerdere versie). Adobe raadt ook aan de toepassing opnieuw te starten als de huidige uptime voor een instantie hoog is.

1. Maak voordat u gaat installeren een momentopname of een nieuwe back-up van uw [!DNL Experience Manager]-exemplaar.

1. Download het servicepakket van [Softwaredistributie](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.8.zip).

1. Open Package Manager en klik **[!UICONTROL Upload Package]** om het pakket te uploaden. Zie [Pakketbeheer](/help/sites-administering/package-manager.md) voor meer informatie.

1. Selecteer het pakket en klik **[!UICONTROL Install]**.

1. Om de S3 schakelaar bij te werken, stop de instantie na installatie van het Service Pack, vervang de bestaande schakelaar met een nieuw binair dossier dat in de installatiemap wordt verstrekt, en begin de instantie opnieuw. Zie [Amazon S3 Data Store](/help/sites-deploying/data-store-config.md#upgrading-to-a-new-version-of-the-s-connector).

>[!NOTE]
>
>De dialoog over de Manager UI van het Pakket bestaat soms tijdens de installatie van het de dienstpak. Adobe raadt aan dat u op foutenlogboeken wacht om zich te stabiliseren alvorens tot de plaatsing toegang te hebben. Wacht op de specifieke logboeken met betrekking tot het verwijderen van de updaterbundel alvorens wordt verzekerd dat de installaties succesvol zijn. Dit gebeurt gewoonlijk op [!DNL Safari] maar kan periodiek op om het even welke browser gebeuren.

**Automatische installatie**

Er zijn twee manieren om Adobe Experience Manager 6.5.8.0 automatisch op een werkexemplaar te installeren:

A. Plaats het pakket in de map `../crx-quickstart/install` als de server online beschikbaar is. Het pakket wordt automatisch geïnstalleerd.

B. Gebruik [HTTP API van de Manager van het Pakket](https://docs.adobe.com/content/docs/en/crx/2-3/how_to/package_manager.html). Gebruik `cmd=install&recursive=true` zodat de geneste pakketten worden geïnstalleerd.

>[!NOTE]
>
>Adobe Experience Manager 6.5.8.0 biedt geen ondersteuning voor Bootstrap-installatie.

**Installatie valideren**

1. Op de pagina met productinformatie (`/system/console/productinfo`) wordt de bijgewerkte versietekenreeks `Adobe Experience Manager (6.5.8.0)` weergegeven onder [!UICONTROL Installed Products].

1. Alle OSGi-bundels zijn **[!UICONTROL ACTIVE]** of **[!UICONTROL FRAGMENT]** in de Console OSGi (de Console van het Gebruik: `/system/console/bundles`).

1. De bundel OSGi `org.apache.jackrabbit.oak-core` is versie 1.22.3 of later (de Console van het Gebruik: `/system/console/bundles`).

Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md) voor meer informatie over de platforms die zijn gecertificeerd voor deze release.

### UberJar {#uber-jar}

UberJar voor Experience Manager 6.5.8.0 is beschikbaar in [Maven Centrale bewaarplaats](https://repo.maven.apache.org/maven2/com/adobe/aem/uber-jar/6.5.8/).

Om UberJar in een Geweven project te gebruiken, zie [hoe te UberJar](/help/sites-developing/ht-projects-maven.md) gebruiken en omvat de volgende gebiedsdeel in uw projectPOM:

```shell
<dependency>
     <groupId>com.adobe.aem</groupId>
     <artifactId>uber-jar</artifactId>
     <version>6.5.8</version>
     <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>UberJar en de andere verwante artefacten zijn beschikbaar op Maven Central Repository in plaats van Adobe Public Maven repository (`repo.adobe.com`). De naam van het hoofdbestand van UberJar wordt gewijzigd in `uber-jar-<version>.jar`. Er is dus geen `classifier`, met `apis` als waarde, voor de tag `dependency`.

## Verouderde functies {#removed-deprecated-features}

Hieronder vindt u een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd met [!DNL Experience Manager] 6.5.7.0. Functies worden in eerste instantie gemarkeerd als afgekeurd en in een toekomstige versie verwijderd. Een alternatieve optie wordt gewoonlijk verstrekt.

Herzie als u een eigenschap of een vermogen in een plaatsing gebruikt. Ook, ben van plan om de implementatie te veranderen om een afwisselende optie te gebruiken.

| Gebied | Functie | Vervanging |
|---|---|---|
| Integrations | Het scherm **[!UICONTROL AEM Cloud Services Opt-In]** is verouderd. Met de Experience Manager en de integratie van Adobe Target die in Experience Manager 6.5 wordt bijgewerkt om de norm API van Adobe Target te steunen, die authentificatie via Adobe IMS en I/O gebruikt, en de groeiende rol van de Lancering van Adobe voor het van instrumenten voorzien van de pagina&#39;s van de Experience Manager voor analyse en verpersoonlijking, is de Opt-In tovenaar functioneel irrelevant geworden. | Configureer systeemverbindingen, Adobe IMS-verificatie en [!DNL Adobe I/O]-integratie via de respectievelijke cloudservices voor Experience Managers. |
| Connectors | De Adobe JCR-connector voor Microsoft SharePoint 2010 en Microsoft SharePoint 2013 is afgekeurd voor Experience Manager 6.5. | N.v.t. |

## Bekende problemen {#known-issues}

* Als u uw [!DNL Experience Manager] instantie van versie 6.5 aan versie 6.5.8.0 bevordert, kunt u `RRD4JReporter` uitzonderingen in het `error.log` dossier bekijken. Start de instantie opnieuw om het probleem op te lossen.

* Als u [!DNL Experience Manager] 6.5 Service Pack 5 of een eerder servicepakket installeert op [!DNL Experience Manager] 6.5, wordt de runtimekopie van het aangepaste workflowmodel voor uw middelen (gemaakt in `/var/workflow/models/dam`) verwijderd.
Om uw runtime exemplaar terug te winnen, adviseert Adobe om het ontwerp-tijd exemplaar van het model van het douanewerkschema met zijn runtime exemplaar te synchroniseren gebruikend HTTP API:
   `<designModelPath>/jcr:content.generate.json`.

* Neem contact op met de klantenservice van Adobe als u problemen ondervindt bij het bewerken en maken van trapsgewijze regels in [!UICONTROL Folder Metadata Schema Forms Editor] en [!UICONTROL Metadata Schema Forms Editor] via het dialoogvenster [!UICONTROL Define Rule]. De regels die al zijn gemaakt en opgeslagen, werken zoals u had verwacht.

* Als de naam van een map in de hiërarchie wordt gewijzigd in [!DNL Experience Manager Assets] en de geneste map met een element wordt gepubliceerd naar [!DNL Brand Portal], wordt de titel van de map niet bijgewerkt in [!DNL Brand Portal] totdat de hoofdmap opnieuw wordt gepubliceerd.

* Wanneer een gebruiker een veld voor het eerst in een adaptief formulier configureert, wordt de optie voor het opslaan van een configuratie niet weergegeven in de eigenschappenbrowser. Als u een ander veld van het adaptieve formulier in dezelfde editor selecteert, wordt het probleem opgelost.

* Als de wizard [!UICONTROL Connected assets configuration] na de installatie een foutbericht van 404 retourneert, installeert u de pakketten `cq-remotedam-client-ui-content` en `cq-remotedam-client-ui-components` handmatig opnieuw met de Package Manager.

* De volgende fouten en waarschuwingsberichten kunnen tijdens de installatie van Experience Manager 6.5.x.x worden weergegeven:
   * &quot;Wanneer de integratie van Adobe Target in Experience Manager gebruikend de StandaardAPI van het Doel (authentificatie IMS) wordt gevormd, dan leidt het uitvoeren van de Fragmenten van de Ervaring naar Doel in verkeerde aanbiedingstypes die worden gecreeerd. In plaats van het type &quot;Experience Fragment&quot;/bron &quot;Adobe Experience Manager&quot; maakt Target verschillende aanbiedingen met het type &quot;HTML&quot;/source &quot;Adobe Target Classic&quot;.
   * `com.adobe.granite.maintenance.impl.TaskScheduler`: Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * De adaptieve servervalidatie van het formulier mislukt wanneer statistische functies zoals SUM, MAX en MIN worden gebruikt. CQ-4274424
   * `com.adobe.granite.maintenance.impl.TaskScheduler` - Geen onderhoudsvensters gevonden bij graniet/bediening/onderhoud.
   * Hotspot in een interactieve Dynamic Media-afbeelding is niet zichtbaar wanneer u een voorvertoning van het element weergeeft via de Shopable Banner-viewer.

## OSGi-bundels en inhoudspakketten inbegrepen {#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5.8.0:

* [Lijst van OSGi-bundels opgenomen in Experience Manager 6.5.8.0](assets/6580_bundles.txt)

* [Lijst met inhoudspakketten die zijn opgenomen in Experience Manager 6.5.8.0](assets/6580_packages.txt)

## Beperkte websites {#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Als u een klant bent en toegang nodig hebt, neemt u contact op met uw Adobe-accountmanager.

* [Productdownload op licensing.adobe.com](https://licensing.adobe.com/)
* Zie [hoe u contact opneemt met de klantenservice van Adobe](https://experienceleague.adobe.com/docs/customer-one/using/home.html).

>[!MORELIKETHIS]
>
>* [[!DNL Experience Manager] Opmerkingen bij de release 6.5](/help/release-notes/release-notes.md)
>* [[!DNL Experience Manager] productpagina](https://www.adobe.com/marketing/experience-manager.html)
>* [[!DNL Experience Manager] 6.5 Documentatie](https://experienceleague.adobe.com/docs/experience-manager-65.html)
>* [Abonneren op updates van prioritaire Adobe-producten](https://www.adobe.com/subscription/priority-product-update.html)

