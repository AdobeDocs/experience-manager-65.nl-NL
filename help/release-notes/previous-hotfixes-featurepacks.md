---
title: Opmerkingen bij de release AEM 6.5 Service Pack
description: Opmerkingen bij de release specifiek voor Adobe Experience Manager 6.5 Service Pack 3.
uuid: c7bc3705-3d92-4e22-ad84-dc6002f6fa6c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5
discoiquuid: 25542769-84d1-459c-b33f-eabd8a535462
docset: aem65
translation-type: tm+mt
source-git-commit: 95d9ed8a0ccfa7651b83058d337511dd6b15665f

---


# Hotfixes en de Pakken van de Eigenschap inbegrepen in vorige Packs van de Dienst {#hotfixes-and-feature-packs-included-in-previous-service-packs}

## AEM 6.5.2.0

AEM 6.5.2.0 is een belangrijke versie die prestaties, stabiliteit, veiligheid, en belangrijkste klantenmoeilijke situaties en verhogingen omvat die sinds de algemene beschikbaarheid van AEM 6.5 in **april 2019** worden vrijgegeven. Het kan bovenop AEM 6.5 worden geïnstalleerd.

Enkele belangrijke hoogtepunten van deze service pack-release zijn:

* De ingebouwde opslagplaats (Apache Jackrabbit Oak) wordt bijgewerkt naar versie 1.10.3.
* Er is een configuratie-eigenschap toegevoegd waarmee u Experience Fragments rechtstreeks kunt exporteren naar door de gebruiker gedefinieerde werkruimten voor Adobe Target.
* Met middelen kunnen gebruikers visueel vergelijkbare afbeeldingen zoeken. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visuele zoekopdracht](../assets/search-assets.md#visualsearch).

* Verbeterde functionaliteit Connected Assets om ondersteuning toe te voegen voor het ophalen van documenten van externe DAM-implementaties. Siteauteurs kunnen nu ondersteunde documenttypen zoeken en filteren in de Inhoudszoeker. De externe documenten kunnen worden toegevoegd aan de component Download op webpagina&#39;s. Zie [Gekoppelde elementen](../assets/use-assets-across-connected-assets-instances.md)gebruiken.

* Filters van het type Document verbeteren met meer types MIME om multi-getaxeerde opties te steunen.
* Introduceerde een externe workflow voor herverwerking voor ondersteuning van meerdere bronnen.
* Optimaliseerde de prestaties van Dynamische Media door standaard activafilters voor replicatie te gebruiken.
* Opties voor het bewerken van middelen voor uitsnijden en roteren zijn hersteld voor DMS7.
* Een optie geïmplementeerd om een video te dempen tijdens het laden in VideoPlayer.
* Repareren om ervoor te zorgen dat de de kolommening van Activa slechts huurdersspecifieke inhoud toont.
* Oplossing voor wijzigingen in stijlaccordeon in zoekresultaten.

### Activa {#assets}

**Verbeteringen voor producten**

* Verbeterde functionaliteit Connected Assets om ondersteuning toe te voegen voor het ophalen van documenten van externe DAM-implementaties. Siteauteurs kunnen nu ondersteunde documenttypen zoeken en filteren in de Inhoudszoeker. De externe documenten kunnen worden toegevoegd aan de component Download op webpagina&#39;s. Hotfix voor CQ-4270245. Zie [Gekoppelde elementen](/help/assets/use-assets-across-connected-assets-instances.md)gebruiken.

* Met middelen kunnen gebruikers visueel vergelijkbare afbeeldingen zoeken. AEM geeft de slimme getagde afbeeldingen uit de DAM-opslagplaats weer die lijken op een door de gebruiker geselecteerde afbeelding. Zie [visuele zoekopdracht](../assets/search-assets.md#visualsearch).

**Oplossingen**

* Elementpaden in URL&#39;s en mapmetagegevens die door de ACS-API worden gegenereerd, worden niet via URL gecodeerd. GRANITE-26198: Hotfix voor CQ-4271814
* Het uitpakken van een archief met een map met een procentteken (%) in de naam kan niet worden geopend via de interface Middelen. NPR-29989: Hotfix voor CQ-4270467
* Aanraakinterface: Tijdens de wizard Publiceren beheren worden verwijzingen toegevoegd na de pagina in de hoofdtekst van het postverzoek, waardoor alle elementen na de pagina worden gepubliceerd. Wanneer de pagina wordt weergegeven, worden sommige elementen in de publicatieinstantie overgeslagen. NPR-29985: Hotfix voor CQ-4270724
* De functie Niet-gerelateerd element Element werkt niet voor gerelateerde elementen die speciale tekens (tekens die door URI worden gecodeerd) in de naam hebben. NPR-30387: Hotfix voor CQ-4274446
* Wanneer u een inhoudsfragment bewerkt, wordt de versie gemaakt met de verkeerde gebruiker.
* Mislukking tijdens het creëren van inzamelingen op het Gebaseerde systeem van de Aannemer. NPR-30114: Hotfix voor CQ-4272948
* De de kolommening van activa UI respecteert niet de de damwortel van de huidige huurder maar de toegang tot van alle paden van de huurdersdam. NPR-30636: Hotfix voor CQ-4275481
* Mogelijke XSS-aanval (cross-site scripting) via een beperkt waarschuwingsvenster voor bestanden, aangezien de geïnjecteerde afbeelding zichtbaar is. NPR-30617: Hotfix voor CQ-4270133
* MultiTenant: Bij huurders die mapeigenschappen opslaan, wordt zowel een melding met de succesmelding als een foutbericht weergegeven waarin de handeling wordt beschreven. &quot;Kan de eigenschappen niet bewerken. Onvoldoende rechten.&quot; dat leidt tot verwarring . NPR-30545: Hotfix voor CQ-4275333
* In het dialoogvenster Asset Selector is het selecteren van elementen niet toegestaan. De bron kan daarom niet worden bijgewerkt met de desbetreffende functie voor bronvervanging. NPR-30502: Hotfix voor CQ-4275029
* DAM Update Asset Workflow - In de toestand van het stadium van het uploaden van grote MP4-bestanden. NPR-30480: Hotfix voor CQ-4271352
* De functie Revisietaak maken werkt niet omdat de payload null is en alle volgende aan een revisie gerelateerde handelingen mislukken. NPR-30468: Hotfix voor CQ-4274263
* Verbindingsprobleem met Adobe Smart Tag via Datapower. NPR-30026: Hotfix voor CQ-4269457
* In de kolomweergave van elementen wordt een fout gegenereerd wanneer wordt geprobeerd de filters te openen zonder rails. NPR-30501: Hotfix voor CQ-4273862
* Wanneer u groepen toevoegt die via LDAP zijn gesynchroniseerd in de CUG-eigenschappen (Closed User Group) van een map Asset, wordt de groep niet opgeslagen en opgehaald. NPR-30615: Hotfix voor CQ-4274689
* De de onderzoeksstijl en richtingsgebieden van het filter passen niet de autocompleted waarde op de onderzoeksvraag toe. NPR-30620: Hotfix voor CQ-4275724
* Koppeling voor het delen van middelen van een map met spatie en &quot;&amp;&quot;-teken in de naam geeft lege grijze kaarten voor bepaalde elementen weer. NPR-30557: Hotfix voor CQ-4270187
* Het metagegevensschema van mappen detecteert het gegevenstype niet automatisch en maakt dus geen gerelateerde TypeHint in de vorm van het verzenden van formulieren. NPR-30599: Hotfix voor CQ-4275227
* Opties voor het bewerken van elementen uitsnijden en roteren zijn uitgeschakeld in de DMS7-ontwerpinterface. NPR-30118: Hotfix voor CQ-4273221
* De functie Koppeling delen werkt niet aan een AEM-instantie met DMS7-configuratie. NPR-30080, NPR-30492: Hotfix voor CQ-4273651
* Het toevoegen van de Dynamische component van Media Scene7 aan de pagina, en dan het publiceren van de pagina brengt niet de configuratie dmscene7 telkens teweeg. NPR-30641: Hotfix voor CQ-4275962
* Er is een IPSJobJournal toegevoegd in AEM om slechts één IPS-taak (Intrusion Prevention Systems) per verwerkingsprofiel te maken. NPR-30490: Hotfix voor CQ-4273614
* Dynamische media: Er zijn standaardfilters toegevoegd om te voorkomen dat elementen worden gerepliceerd naar het publicatieknooppunt van AEM. NPR-30538: Hotfix voor CQ-4274678
* Introduceerde een externe werkstroom van het Herproces voor multi-middelsteun om omslag als lading toe te staan. De werkstroom heeft twee stappen - verwerkt activa zonder handvatten via meta-gegevenskaart aan volgende stap opnieuw en uploadt alle activa zonder activa handvat aan S7 in één enkele IPS baan. Zie Dynamic Media Cloud Services configureren voor meer informatie. NPR-30489: Hotfix voor CQ-4272903
* Het uploaden van onjuiste CSV na correcte CSV wipes uit correcte CSV. Hotfix voor CQ-4277694, CQ-4277814
* Het onjuiste pictogram dat specifiek is voor de bijdragemappen die moeten worden verwijderd. Hotfix voor CQ-4277580
* Als u een gebruiker selecteert in de gebruikerskiezer op het tabblad Asset Contribution, wordt de naam van de gebruiker niet weergegeven in de tabel en wordt in het dialoogvenster Gebruikers verwijderen op de eigenschappenpagina een onjuiste tekst weergegeven. Hotfix voor CQ-4277875
* Medewerkers kunnen niet vanuit de gebruikerskiezer worden toegevoegd aan de map Asset Contributor door een gebruiker te selecteren en op Toevoegen te klikken. Hotfix voor CQ-4277824, CQ-4278087
* Zoeken in kleine letters werkt niet in de gebruikerskiezer. Hotfix voor CQ-4277958, CQ-4277930
* Niet-beheerders kunnen elementen publiceren in een nieuwe map in de map Asset Contribution. Hotfix voor CQ-4278200
* de gebruiker van de dam (niet-admin) heeft geen optie om contribuanten aan de omslag van de inbreng van Activa toe te voegen. Hotfix voor CQ-4278192
* De knop Maken is zichtbaar in de map Asset Contribution. Hotfix voor CQ-4277560
* Als u zoekquery op relevantie sorteert, worden InDesign-documenten samen met InDesign-sjablonen geretourneerd. Hotfix voor CQ-4273864
* Als de gebruiker een e-mailadres in hoofdletters heeft, kunnen gebruikers niet inchecken voor de elementen die eerder zijn uitgecheckt. Hotfix voor CQ-4276575
* De bewerking Verwijderen is alleen van toepassing op voorinstellingen die zijn geselecteerd. Als de lijst na de bewerking automatisch wordt vernieuwd op het scherm, worden andere voorinstellingen weergegeven die al zijn vernieuwd. Hotfix voor CQ-4261461
* Het vormen van de Dynamische Diensten van de Wolk van Media op wijze DMHybrid resulteert in veelvoudige lege rapportreeksen die in Analytics worden gecreeerd, en zonder rapportsuite id die in AEM wordt opgeslagen, resulterend in rapportsuite duplicatie. Hotfix voor CQ-4249780
* Het anders noemen van verrichting in activa AEM aan gedupliceerde naam ontbreekt om aan Scene7 te synchroniseren. Hotfix voor CQ-4276763
* Door de gebruiker gegenereerde inhoud wordt onjuist weergegeven in het deelvenster met zoekfilters. Hotfix voor CQ-4273875
* De optie Vergelijkbare zoeken is niet beschikbaar voor TIFF-afbeeldingen. Hotfix voor CQ-4278238
* Geïmplementeerde optie om video te dempen bij het laden in VideoPlayer. Hotfix voor CQ-4266465
* Viewers - VideoViewer: poster=none werkt onjuist als een externe video wordt gebruikt. Hotfix voor CQ-4265536
* Het pictogram Wachten is zichtbaar tijdens het afspelen van video in IE11- en MS Edge-browsers. Hotfix voor CQ-4251539
* 3.8 SDK- en 5.13 README-bestanden voor viewers worden niet bijgewerkt en bevatten informatie uit eerdere releases. Hotfix voor CQ-4273737
* Inhoudsfragment wordt versieeerd, zelfs voordat de wijzigingen worden opgeslagen. NPR-30616: Hotfix voor CQ-4273088
* Vervang Asset#getMetadata(String) door Asset#getMetadataValueFromJcr(String) in het miniatuurproces. NPR-30491: Hotfix voor CQ-4273067
* Bij het uploaden van jpg wordt het bericht op meerdere plaatsen weergegeven: &quot;ReplicateOnModifyWorker Replicating UPDATED&quot; voor elk element, waardoor de prestaties afnemen.
* Als u het ZIP-archief uitpakt met de functie Archiveren uitpakken, ontstaan er problemen met mappen waarvan de naam een percentage (%) in de titel bevat. NPR-29990: Hotfix voor CQ-4270467

### Sites {#sites-6520}

* Als de overerving van LiveCopy is verbroken, worden op live kopieerpagina&#39;s links voor taalkopieën weergegeven in plaats van LiveCopy-koppelingen. (NPR-30980)
* Voor een nieuwe blauwdruk worden alleen de eerste 40 records weergegeven als het aantal records groter is dan 40. Met Vervagen worden lege regels weergegeven voor de rest van de records. (NPR-31182)
* Plug-in Rich Text Editor (RTE) van de tekstcomponent geeft vervormde tekens voor Japanse en Koreaanse tekst weer. (NPR-31331)
* De Rich Text Editor (RTE) staat niet toe om een ingesloten tabel in te voegen als lijstitem. (NPR-30879)
* Buiten het vak wordt onverwachts de inline tekengrootte toegepast op elementen met de basisstructuur Rich Text Editor (RTE). (NPR-31284)
* Wanneer een gebruiker de linkerspoorgebieden concentreert en toetsenbordkortere weg gebruikt om inhoud te kleven, kleeft het inhoud van pagina redacteurs klembord in plaats van de inhoud die van linkerspoorgebieden wordt gekopieerd. (NPR-31172)
* Wanneer een gebruiker een veld Bestand uploaden toevoegt aan een veld met meerdere velden, wordt het afbeeldingspad opgeslagen in het componentknooppunt in plaats van het knooppunt met meerdere velden. (NPR-30882)
* De API ResponsiveGridExporter retourneert de interface com.day.cq.wcm.foundation.model.impl.export.AllowedComponentsExporter niet. Het pakket com.day.cq.wcm.foundation.model.impl wordt gedeclareerd als een privépakket. (NPR-31398)
* Wanneer een pagina die sommige ExperienceFragments bevat op niet redacteurswijze (of in Auteur zonder de `editor.html` prefix en `wcmmode=disabled`, of in Uitgever) wordt geopend, beëindigt het verzoek in code 500 van de de statusfout van HTTP. (NPR-30743)

### WCM - Pagina-editor {#wcm-page-editor-6520}

**Verbeteringen voor producten**

* Verbeter documenttype filters met meer MIME Types om multi-getaxeerde opties te steunen. Hotfix voor CQ-4270694

### Beheer van inhoudsfragmenten {#content-fragment-management-6520}

* De query die wordt gebruikt door de gebruikersinterface van Content Fragment-modellen is erg langzaam en resulteert uiteindelijk in een fout. Hotfix voor CQ-4270807

### UI - Foundation {#ui-foundation}

* Sneltoetsen die voorkomen dat de gebruiker &#39;m,&#39; &#39;p,&#39; &#39;e&#39; gebruikt in specifieke gebruikersinterfaces. NPR-30355: Hotfix voor GRANITE-26346
* Als u de zoekinterface voor elementen sluit, wordt de linkerrail niet opnieuw ingesteld op Content selectie, waardoor de gebruiker de filterrail niet de tweede keer kan openen. NPR-30509: Hotfix voor CQ-4274716
* Omgeving met meerdere gebruikers: Bovenste navigatie van de Asset UI is niet beschikbaar en er wordt een JavaScript-fout gegenereerd. NPR-30104: Hotfix voor GRANITE-26344

### Vertaling {#translation-6520}

* Probleem met vertaling - Slechts een paar componenten worden vertaald met behulp van Machine Translation. NPR-30079: Hotfix voor CQ-4273764

### Platform {#platform-6520}

* De Standaard afzender van de Post van AEM kan geen post naar een verre server SMTP over TLS v1.2 verzenden. NPR-30476: Hotfix voor GRANITE-26605

### Projecten {#projects-6520}

* dam:folderThumbnailPaths de waarden worden niet vernieuwd en tonen oude duimnagels zelfs na het schrappen van de activa binnen de omslag. NPR-30424: Hotfix voor CQ-4273667
* Als u de optie &quot;verplaatsen&quot; voltooit, blijven de titel en de naam van het element ongewijzigd. NPR-30647: Hotfix voor CQ-4276265

### Gemeenschappen {#communities-6520}

* Diagnostiek voor gebruikerssynchronisatie is volledig verbroken en werkt niet. NPR-30004, NPR-29943: Hotfix voor CQ-4270287, CQ-4271348

### Sling {#sling}

* De bijgewerkte instantie van 6.3.3.2 tot 6.5 resulteert in dubbele configuraties OSGi. NPR-30130: Hotfix voor CQ-4274016

### Integratie {#integration}

* De aangepaste inhoud wordt pas correct weergegeven op de publicatieversie als de instantie opnieuw is gestart. NPR-30377: Hotfix voor CQ-4273706
* Wanneer u Starten op een website configureert, wordt voor het bibliotheekadres een schuine streep (/) toegevoegd, zodat u telkens handmatig kunt ingrijpen. NPR-30694: Hotfix voor CQ-4275501

### Formulieren {#forms-6520}

>[!NOTE]
>
>AEM Service Pack bevat geen oplossingen voor AEM-formulieren. Ze worden geleverd met behulp van een apart Forms add-on pakket. Daarnaast wordt een cumulatief installatieprogramma uitgebracht dat oplossingen voor AEM Forms in JEE bevat. Zie AEM Forms add-on [installeren en AEM Forms JEE-installatieprogramma](#install-aem-forms-add-on-package) voor meer informatie [](#forms-jee-installer)installeren.

De belangrijkste kenmerken voor AEM 6.5.2.0-formulieren zijn:

* Instelling Automatisch toegevoegd aan `RenderAtClient` `PDFFormRenderOptions` de API voor AEM Forms OSGi.

#### Formulierinvoegpakket {#forms-add-on-package}

**Back-end integratie**

* Kan het formuliergegevensmodel niet configureren met een door AWS gehoste taakgebalanceerde URL. NPR-30123: Hotfix voor CQ-4273359
* Tijdens het creëren van het Model van de Gegevens van de Vorm (FDM) met de Taal van de Definitie van de Dienst van het Web (WSDL), `Caused by: com.adobe.aem.dermis.exception.DermisException: java.lang.Exception: Unable to handle content type` is het foutenbericht teruggekeerd: NPR-30477: Hotfix voor CQ-4272921

**Correspondentenbeheer**

* De vertoning van de &quot;van de Correspondentie UI van de Making (CCR UI) ontbreekt periodiek met hieronder fout in console:
   `- Uncaught Error: variable [object Object]is already known the letter`- NPR-30127

**Interactieve communicatie**

* Een veld dat is gemarkeerd als vereist in het formuliergegevensmodel, wordt weergegeven als vereist in de interface Correspondentie maken (CCR UI). NPR-30623: Hotfix voor CQ-4274902

**Formulieren - workflow**

* Niet-toegewezen uitvoervariabelen op Gecontroleerde mappen zorgen ervoor dat de activering mislukt. Hotfix voor CQ-4264451

**HTML5-formulieren**

* Wanneer de douanecode of het project voor de tweede keer wordt opgesteld, geeft de pagina niet terug en de volgende fout komt voor:

   `org.apache.sling.scripting.sightly.SightlyException.`

   NPR-30539: Hotfix voor CQ-4272509

* Wanneer u in de modus Bladeren een HTML5-formulier leest met toegang tot niet-visuele desktops, wordt in de Chrome-browser vóór elke SVG (Scalable Vector Graphic) in het formulierontwerp &quot;graphic&quot; gelezen. NPR-30449: Hotfix voor CQ-4274732

#### Forms JEE-installatieprogramma {#forms-jee-installer}

**Formulieren - Documentbeveiliging**

* Het toepassen van een handtekening met tijdstempel mislukt vanwege een fout: ALC-DSC-003-000: com.adobe.idp.dsc.DSCInvocationException: Inroepfout. NPR-30820: Hotfix voor CQ-4275852

**Formulieren - Document Services**

* Als &quot;SubmitURL&quot;een en-teken (&amp;) bevat, worden de parseringsfouten gezien in het logbestand wanneer de POST-aanvraag wordt ingediend voor renderpdf servlet. NPR-30865: Hotfix voor CQ-4278232

**Formulieren - Foundation JEE**

* De HTMLtoPDF-service geeft maxReuseCount niet weer in de JMX-console. NPR-30134, NPR-30304: Hotfix voor CQ-4273763
* Als u een verbinding met een webservice toevoegt of bewerkt door webservices aan te roepen vanuit AEM Forms Workbench, treedt er een fout op: ClassNotFoundException org.apache.axis.message.SOAPBodyElement. NPR-30105: Hotfix voor CQ-4273217

### Inclusief functiepakketten {#feature-packs-included}

>[!NOTE]
>
>Voor klanten van AEM Forms, is het essentieel om toe:voegen-op pakket van Vormen AEM te installeren na het installeren van om het even welk AEM Service Pack, Cumulative Fix Pack, of het Pak van de Eigenschap.

#### Sites {#sites-feature-packs-included}

* Er is een configuratie-eigenschap toegevoegd waarmee u Experience Fragments rechtstreeks kunt exporteren naar door de gebruiker gedefinieerde werkruimten voor Adobe Target. NPR-29189: Hotfix voor CQ-4249782

#### Formulieren - Document Services {#forms-document-services-1}

* Instelling Automatisch toegevoegd aan `RenderAtClient` `PDFFormRenderOptions` de API voor AEM Forms OSGi. NPR-30759: Hotfix voor CQ-4278193

## AEM 6.5.1.0 {#release-6510}

AEM 6.5.1.0 is een belangrijke versie die prestaties, stabiliteit, veiligheid, en belangrijkste klantenmoeilijke situaties en verhogingen omvat die sinds de algemene beschikbaarheid van AEM 6.5 in *april 2019 worden vrijgegeven.* Het kan bovenop AEM 6.5 worden geïnstalleerd.

Enkele belangrijke hoogtepunten van deze service pack-release zijn:

* De opname van de status dynamic-UI in het bijhouden van gebeurtenissen als aangepaste kenmerken ingeschakeld.
* Inclusief ondersteuning voor de levering van video-elementen van 360 graden in Dynamic Media Scene 7.
* De functie *Japanse omloop* van Word is ingeschakeld via de stijlplug-in van de Rich Text Editor. Voor meer informatie, zie Japanse woordomslag [vormen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#jpwordwrap)

### Activa

* Bijgewerkte interface DAM DMGateway voor S3 multipart steun. NPR-29740: Hotfix voor CQ-4226303
* Voorvertoning van uitvoeringen genereert `Only empty tenantId is currently supported` fout na upgrade naar AEM 6.5\. NPR-29986: Hotfix voor CQ-4272353
* Dialoogvenster Verwijderen is niet zichtbaar om het verwijderen van taken toe te staan. NPR-29720: Hotfix voor CQ-4271074
* Nadat een elementtitel is toegevoegd aan de eigenschappenpagina, wordt de eigenschappenpagina opnieuw geopend wanneer een gebruiker de pagina probeert te sluiten. NPR-29627: Hotfix voor CQ-4264929
* VersioningTimelineEventProvider moet een hoofdversie leveren samen met het knooppunt van het type nt: versie. Hotfix voor GRANITE-26063
* Implementeerde de mogelijkheid om 360 bolvormige video&#39;s te uploaden en af te spelen in de modus AEM DM-Scene7. Hotfix voor CQ-4265131
* Met Live kopie wordt een onjuiste status opgehaald als de bron wordt bewerkt. Hotfix voor CQ-4265451
* Ondersteuning voor beheer van meerdere sites ingeschakeld voor middelen. Hotfix voor CQ-4271453, CQ-4268621, CQ-4257491
* In de AEM-interface moet een extra vermelding voor de huidige versie van het element in de tijdlijngeschiedenis worden weergegeven, waarin de laatste opmerking over inchecken van Adobe Asset Link wordt weergegeven. Hotfix voor CQ-4262864
* In de tijdlijn van het inhoudsfragment wordt een foutbericht weergegeven wanneer eigenschappen ontbreken. Hotfix voor CQ-4272560
* Een probleem met de videospeler van Scene 7 wanneer uitgevouwen aan volledig scherm. Hotfix voor CQ-4266700
* ZoomVerticalViewer: Panknoppen mogen niet worden weergegeven als één afbeeldingselement wordt gebruikt. Hotfix voor CQ-4264795
* Als u een onderliggende node in de live kopie verwijdert, moet de liveRelationship worden losgekoppeld. Hotfix voor CQ-4270395
* Het meta-gegevensschema bevat slechts punten van de globale configuratie en mist degenen van de actieve huurder. De URL-waarde van het formPath wordt weer ingesteld op de standaardwaarde, zelfs als deze wordt gewijzigd. NPR-29945: Hotfix voor CQ-4262898
* Publiceren van voorinstellingen voor afbeeldingen naar Brand Portal mislukt met 500 foutcode. NPR-29510: Hotfix voor CQ-4268659

### Sites

* Lege eigenschappen en meerdere eigenschappen verspreiden zich niet van blauwdruk tijdens de rollout. Actieve kopie herstellen met blauwdruk werkt niet voor componenten. NPR-29253: Hotfix voor CQ-4264928, CQ-4264926, CQ-4267722
* CoralUI, wanneer gebruikt met `Multifield`, slaat het `fileReferenceParameter` op componentenniveau in plaats van multifield niveau op. NPR-29537: Hotfix voor CQ-4266129
* Verbetering van AEM-tekstcomponent en Teksteditor naar Japans. NPR-29785: Hotfix voor CQ-4265090
* De pagina die wordt teruggezet met Timewarp, moet naar het correcte beeld op het tijdstip van versioning verwijzen. NPR-29431: Hotfix voor CQ-4262638
* An issue with the inheritance of Style System nodes from parent to child. NPR-29516: Hotfix voor CQ-4270330
* Een foutbericht tijdens het instellen van het sociaal posten op Facebook-verificatie. NPR-29211: Hotfix voor CQ-4266630
* De weergegeven miniatuur op Inhoudsfragment toont de interne kalenderrepresentatie voor het veld Datum en tijd. NPR-29531: Hotfix voor CQ-4269362
* De knoppen worden niet weergegeven wanneer u het tabblad met machtigingen opent in de implementatie van Coral2. Hotfix voor CQ-4269419

### Handel

* RestrictionViolationException, when running lazy content migration for e-commerce. NPR-29247: Hotfix voor CQ-4264383

### Beheer van inhoudsfragmenten

* Parseerfout bij het openen van een inhoudsfragment met de tekens dollar `($)` en open accolade `({)`. Hotfix voor CQ-4270266

### Ervaar fragmenten

* Exporteer AEM Experience Fragments naar Adobe Target. Hotfix voor CQ-4265469
* De uitvoer van de Fragmenten van de ervaring naar doel ontbreekt met slimme beeld. Hotfix voor CQ-4269606

* De gebruiker raakt een doodlopende weg wanneer het proberen om de Fragmenten van de Ervaring door Onderzoek in kaartmening te bewegen. Hotfix voor CQ-4263848

### WCM - Pagina-editor

* Gespiegeld XSS (Cross-site scripting) bij gebruik van een ongeldige kiezer. Hotfix voor CQ-4270397

### Replicatie

* Door de gebruiker opgegeven gegevens worden niet beschermd bij uitvoer in de `cq/replication/components/agent` component, wat resulteert in een opgeslagen XSS-kwetsbaarheid (Cross-site scripting). Hotfix voor CQ-4266263

### Workflow

* Het veld Kalenderkiezer van deelnemer in dialoogvenster is verbroken. NPR-29727: Hotfix voor CQ-4270423

### WCM - SPA-editor

* Toegelaten het halen van pre-teruggegeven inhoud van een ver eindpunt. Hotfix voor CQ-4270238
* Waarschuwingen in logboeken wanneer het openen van een Pagina van het Malplaatje van het KUUROORD server-kant teruggegeven. Hotfix voor CQ-4270238

### WCM - MSM

* Door een upgrade naar AEM 6.4.3 duurt het implementeren van beheer voor meerdere sites lang. Hotfix voor CQ-4271410

### Integratie

* BrightEdge-referenties zijn mislukt vanwege een verbindingsfout. NPR-29168: Hotfix voor CQ-4265872

* Er wordt een uitzonderingsbericht weergegeven wanneer u de AEM-startconfiguratie probeert te bewerken en op te slaan. NPR-29176: Hotfix voor CQ-4265782/CQ-4266153

### Gebruikersinterface

* Toegevoegde ondersteuning voor het bijhouden van dynamische UI-statussen als aangepaste kenmerken bij het bijhouden van bepaalde gebeurtenissen in de API voor het bijhouden van stichtingen. Hotfix voor GRANITE-26283
* Kan de functie voor bijhouden niet instellen op de verzendknop. Hotfix voor GRANITE-26326
* De wizard kan de functie voor bijhouden niet instellen op de verzendknop. NPR-29995, NPR-30025: Hotfix voor CQ-4264289

### Gemeenschappen

* Kan geen nieuwe badges uitlijnen in de vervolgkeuzelijst op de pagina voor het lidprofiel. NPR-29381: Hotfix voor CQ-4267987
* Bezoekers en leden zonder moderatorrechten kunnen niet-goedgekeurde/hangende berichten zien door de URL te plakken. NPR-29724: Hotfix voor CQ-4271124, CQ-4271441
* Hoge responstijd tot 40-50 seconden wordt waargenomen bij het aanmelden bij de gebruiker voor de Gemeenschap. NPR-29677: Hotfix voor CQ-4269444

### Replicatie

* De component van de Agent van de replicatie is vatbaar voor een kwetsbaarheid die gevoelige informatie aan onbevoegde gebruikers openbaart. NPR-29611: Hotfix voor GRANITE-25070

* Sessielek tijdens OAuth voor elke replicatie naar Brand Portal. NPR-30001: Hotfix voor GRANITE-26196

### Projecten

* Publiceer middelen van AEM Auteur /content/dam/mac folder aan het Portaal van het Merk werkt niet. NPR-29819: Hotfix voor CQ-4271118

### Platform

* HtmlLibraryManager verwijdert alle inhoud van crx-quickstart bij cachevalidatie. NPR-29863: Hotfix voor GRANITE-26197

### Felix

* Gegevens over geheugengebruik worden niet weergegeven in de systeemconsole bij gebruik van Java11\. NPR-29669

### Formulieren

De belangrijkste kenmerken voor AEM 6.5.1.0-formulieren zijn:

* Alleen OSGi: Er is een nieuw kenmerk toegevoegd `PAGECOUNT` in de service Uitvoer en Formulieren.

* Alleen OSGI: Ondersteuning ingeschakeld voor het maken van statische PDF-bestanden met Forms Service.
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers.
* Ondersteuning ingeschakeld voor ADFS v3.0 for Dynamics on-premise integratie.

#### Formulierinvoegpakket

**Backend-integratie**

* Fout bij het ophalen van de beveiligde Web Service Definition Language (WSDL). NPR-29944: Hotfix voor CQ-4270777
* Wanneer AEM Forms op IBM WebSphere is geïnstalleerd, mislukt het maken van een formuliergegevensmodel op basis van SOAP. Hotfix voor CQ-4251134
* Toegelaten steun voor de Actieve Diensten van de Federatie van de Folder (ADFS) v3.0 voor de Integratie van de Dynamiek van Microsoft op-gebouw. Hotfix voor CQ-4270586
* Als de titel van een gegevensbron wordt gewijzigd, wordt de bijgewerkte titel niet weergegeven in het formuliergegevensmodel. Hotfix voor CQ-4265599
* Als de naam van een entiteit of kenmerk afbreekstreepjes of spaties bevat, worden dergelijke entiteiten en kenmerken niet door expressies geëvalueerd. Hotfix voor CQ-4225129

* Er wordt een onjuiste uitvoer waargenomen wanneer een dubbele punt aanwezig is in de primitieve uitvoer van de tekenreeks. Hotfix voor CQ-4260825

* Zelfs als er geen inhoud wordt verwacht van de REST API-uitvoer, genereert de aanroepbewerking van het formuliergegevensmodel een fout. Hotfix voor CQ-4268828

**Adaptieve formulieren**

* Unable to add new instance in Adaptive Form Fragment during lazy loading. NPR-29818: Hotfix voor CQ-4269875
* Verify component registreert of toont geen fout voor Document van de malplaatjes van het Verslag. Hotfix voor CQ-4272999
* Toegevoegde ondersteuning voor het uitschakelen van de layouteditor voor Adaptieve formulieren. Hotfix voor CQ-4270810
* De stap Verifiëren voor Adaptive Forms is hersteld in AEM 6.5\. Hotfix voor CQ-4269583

* Validatiefout van adaptieve formuliervelden breekt Adobe Sign. Hotfix voor CQ-4269463
* Wanneer een instantie van AEM Forms meer dan 20 adaptieve formulierfragmenten heeft en de naam van alle formulierfragmenten begint met dezelfde tekenreeks, retourneert de zoekopdracht niet of alleen naar recente 20 gemaakte fragmenten. Hotfix voor CQ-4264414, CQ-4264914

* Prestatieproblemen wanneer de toepassing Adaptive Forms wordt gebruikt met een grote dataset. . Hotfix voor CQ-4235310

* Wanneer betreden door anonieme rekening op een publicatie instantie, ontbreekt GuideRuntime manuscript om te laden. Hotfix voor CQ-4268679

**Formulieren - Interactieve communicatie**

* De interactieve Communicatie malplaatje maakt geen lijst van kopbal en footer componenten in toegestane componentenlijst. Hotfix voor CQ-4237895
* Wanneer u een interactieve sjabloon voor communicatie-afdrukken maakt die een afbeeldingsveld bevat, wordt de titel van het diagram ingesteld op leeg. Hotfix voor CQ-4264772
* De lijnkleur van een diagram wordt, wanneer deze wordt verwijderd, ingesteld op ongedefinieerd. Hotfix voor CQ-4264762
* Wijzigingen in de lay-outlaag die zijn aangebracht op documentfragment, verdwijnen bij het uitvoeren van de wijzigingen en blijven synchroon. Hotfix voor CQ-4266054
* Het formuliergegevensmodelelement in een documentfragment dat aan een tekstveld is gebonden, geeft geen overervingspictogram weer en staat binding toe. Hotfix voor CQ-4261089
* De printerkanaal-render-API heeft geen optie om gegevens als parameter door te geven in de API. Hotfix voor CQ-4263540
* De montages van de agent zijn niet zichtbaar aangezien Editable door de controledoos van de Agent wordt ongecontroleerd wanneer het bindingstype van het Fragment van de Tekst in niets/het ModelVoorwerp van Gegevens voor het gebied van het Koord/variabele wordt veranderd. Hotfix voor CQ-4261953
* Voor de voorlegging van de UI van de Agent, slaat het resulterende dossier van Webgegevens informatie voor erving-geannuleerde niet gebonden gebieden op. Hotfix voor CQ-4265621

**Formulieren - workflow**

* Wanneer een formulier opnieuw wordt verzonden vanuit de Postvak UIT de app voor adaptieve formulieren, gaan er gegevens verloren. NPR-28345: Hotfix voor CQ-4260929
* Documenten worden niet gesloten tijdens het opslaan voor niet-variabele gevallen. Hotfix voor CQ-4269784
* De app Adaptive Forms heeft de ondersteuning voor Microsoft Windows 8.1\ ingetrokken. Hotfix voor CQ-4265274
* Wanneer een afbeelding van meer dan 2 MB als een bijlage op veldniveau aan een formulier wordt gekoppeld in de Android-versie van de app AEM Forms, loopt de app vast. Hotfix voor CQ-4265578

* Toegelaten pre-populatieopties voor Interactieve Communicatie Kanaal van de Druk in Assign taak. Hotfix voor CQ-4265577
* De gebruikers kunnen geen gedeelde taak bekijken tot zij lid van de groep worden waaraan de taak wordt toegewezen. Hotfix voor CQ-4248733
* Het opslaan of verzenden van JEE-toepassingen in de app Adaptief formulier is geblokkeerd in Windows. Hotfix voor CQ-4268704
* Het formuliergegevensmodel dat is gekoppeld aan de variabele van het formuliergegevensmodel is niet zichtbaar. Hotfix voor CQ-4266554
* Geen ondersteuning voor de statusvariabele van het documentteken met variabele ondersteuning. Hotfix voor CQ-4266312
* Verzending vanuit werkruimte mislukt met een umlaut-teken. Hotfix voor CQ-4263172
* Als de workflow tijdens een upgrade wordt geopend voor bewerking, wordt in de gebruikersinterface van de controlemap (UI) een fout weergegeven in plaats van de naam van de workflow. Hotfix voor CQ-4238579

**Formulieren - Beheer**

* Wanneer een andere extensie dan xsd of schema.json wordt geüpload, vindt uploaden niet plaats en wordt er geen foutbericht gegenereerd. Hotfix voor CQ-4266716

**Formulieren - Correspondentenbeheer**

* AEM 6.5 Forms Create Correspondence UI (CCR UI) kan geen correspondentie openen die is gemaakt met AEM 6.3 Forms. Hotfix voor CQ-4266392
* De functie Som in XDP werkt niet als het DDE gegevenstype van type aantal is. Hotfix voor CQ-4227403
* Letters voor de invalidatielogica voor de cache in het geheugen die moeten worden bijgewerkt, omdat de laatste gewijzigde tijd van een element niet wordt bijgewerkt wanneer een element wordt gepubliceerd. Hotfix voor CQ-4250465
* Kan documentfragment, DD &amp; letters niet publiceren. Hotfix voor CQ-4272893

#### Forms JEE-installatieprogramma

**PDF Generator**

* CAD-bestanden naar PDF-conversie mislukken met 64-bits JDK. NPR-29924, NPR-29925: Hotfix voor CQ-4272113
* De naam van PhantomJS is vervangen door WebToPDF voor conversie van HTML naar PDF. NPR-29933: Hotfix voor CQ-4234545
* Er wordt een fout gegenereerd bij het converteren van het ZIP-bestand naar PDF. Hotfix voor CQ-4268628

**Formulieren - Designer**

* Wanneer een volledige toegankelijkheidscontrole wordt uitgevoerd op het statische PDF-bestand dat is gemaakt met AEM Form Designer, mislukt de controle van de primaire taal omdat het taalkenmerk ontbreekt. Hotfix voor CQ-4272923, CQ-4271002

**Formulieren - Documentbeveiliging**

* Digital Signature with Hardware Security Module (HSM) werkt niet op OSGi Linux op Java 11 en Java 8\. NPR-29838: Hotfix voor CQ-4270441
* Digital Signature with Hardware Security Module (HSM) werkt niet op JEE Linux en op alle ondersteunde toepassingsservers, zoals JBoss en Websphere. NPR-29839: Hotfix voor CQ-4266721
* Als u de handtekeningen in een PDF verifieert met behulp van PDF Advanced Electronic Signatures (PAdES), wordt InvalidOperationException gegenereerd. NPR-29842: Hotfix voor CQ-4244837
* Extra ondersteuning voor documentbeveiliging voor Office 2019\. Hotfix voor CQ-4254369, CQ-4259764

**Formulieren - Document Services**

* PDF kan niet worden geconverteerd naar PDF/A-1b met formulierveld heeft geen weergavewoordenboek. NPR-29940: Hotfix voor CQ-4269618

* OSGi: Kan het aantal pagina&#39;s dat tijdens het renderen is gegenereerd niet bepalen. NPR-28922: Hotfix voor CQ-4270870
* Ondersteuning ingeschakeld voor statische PDF-bestanden met Forms Service in AEM Forms OSGi. NPR-28572: Hotfix voor CQ-4270869
* Kan de machtigingen voor XMLForm.exe niet wijzigen. NPR-29828, NPR-29237: Hotfix voor Q-4267080
* Het statische PDF-bestand dat is gemaakt in de uitvoermodule van de AEM Forms-server, vult het taalkenmerk/de taaltag niet met de taal van het gemaakte document. NPR-27332: Hotfix voor CQ-4271002

**Formulieren - Foundation JEE**

* Niet-beschikbare pdfg_srt in definitieve artefacten veroorzaakt het installatieprogramma om te ontbreken. NPR-29854: Hotfix voor CQ-4270137
* LCBackupMode.sh werkt niet. NPR-29840: Hotfix voor CQ-4269424
* De UDP havenverwijzing zou uit gebruikersinterface (UI) voor WebSphere moeten worden verwijderd. Hotfix voor CQ-4264782

### Inclusief functiepakketten

#### Activa - opgenomen

* Ondersteuning voor beheer van meerdere sites ingeschakeld voor middelen. Zie [Elementen hergebruiken met MSM voor Elementen](https://helpx.adobe.com/experience-manager/6-5/help/assets/reuse-assets-using-msm.html)voor meer informatie. NPR-29199: Hotfix voor CQ-4259922

#### Sites - inbegrepen

* Exporteer AEM Experience Fragments naar Adobe Target. Zie [de Experience Fragment Link Rewriter Provider - HTML](https://helpx.adobe.com/experience-manager/6-5/help/sites-developing/experience-fragments.html#TheExperienceFragmentLinkRewriterProviderHTML)voor meer informatie. Hotfix voor CQ-4265469

#### Formulieren - Document Services - inbegrepen

* Alleen OSGi: Een nieuw kenmerk PAGECOUNT toegevoegd in Output and Forms Service. NPR-28922: Hotfix voor CQ-4270870
* Alleen OSGi: Ondersteuning ingeschakeld voor het maken van statische PDF-bestanden met Forms Service. NPR-28572: Hotfix voor CQ-4270869
* Toegelaten toestemmingen op XMLForm.exe voor beheerder en wortelgebruikers. NPR-29237: Hotfix voor CQ-4267080

### OSGi-bundels en inhoudspakketten

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in AEM 6.5.1.0

Lijst van OSGi-bundels opgenomen in AEM 6.5.1.0

[Bestand ophalen](assets/6_5-bundle-list.txt)

Lijst met inhoudspakketten die zijn opgenomen in AEM 6.5.1.0

[Bestand ophalen](assets/6_5-content-package-list.txt)
