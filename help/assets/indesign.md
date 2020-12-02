---
title: Integreer [!DNL Assets] met [!DNL InDesign Server]
description: Leer hoe te om [!DNL Adobe Experience Manager Assets] met [!DNL Adobe InDesign Server] te integreren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 117208c634613559bb13556e12f094add70006e2
workflow-type: tm+mt
source-wordcount: '1528'
ht-degree: 1%

---


# [!DNL Adobe Experience Manager Assets] integreren met [!DNL Adobe InDesign Server] {#integrating-aem-assets-with-indesign-server}

[!DNL Adobe Experience Manager Assets] gebruik:

* Een proxy om het laden van bepaalde verwerkingstaken te verdelen. Een volmacht is een [!DNL Experience Manager] instantie die met een volmachtsarbeider communiceert om een specifieke taak te vervullen, en andere [!DNL Experience Manager] instanties om de resultaten te leveren.
* Een proxyworker om een specifieke taak te definiëren en te beheren.
Deze kunnen betrekking hebben op een groot aantal verschillende taken; bijvoorbeeld met een [!DNL InDesign Server] bestanden verwerken.

Als u bestanden volledig wilt uploaden naar [!DNL Experience Manager Assets] die u met [!DNL Adobe InDesign] hebt gemaakt, wordt een proxy gebruikt. Dit gebruikt een volmachtsarbeider om met [!DNL Adobe InDesign Server] te communiceren, waar [manuscripten](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) worden in werking gesteld om meta-gegevens te halen en diverse vertoningen voor [!DNL Experience Manager Assets] te produceren. De volmachtsarbeider laat de bidirectionele communicatie tussen [!DNL InDesign Server] en [!DNL Experience Manager] instanties in een wolkenconfiguratie toe.

>[!NOTE]
>
>[!DNL Adobe InDesign] wordt aangeboden als twee afzonderlijke aanbiedingen. [Adobe ](https://www.adobe.com/products/indesign.html) InDesign-bureaubladtoepassing waarmee u paginalay-outs voor afdrukken en digitale distributie kunt ontwerpen. [Met Adobe InDesign ](https://www.adobe.com/products/indesignserver.html) Server kunt u programmatisch geautomatiseerde documenten maken op basis van wat u hebt gemaakt  [!DNL InDesign]. Het werkt als dienst die een interface aan zijn [ExtendScript](https://www.adobe.com/devnet/scripting.html) motor aanbiedt. De manuscripten worden geschreven in [!DNL ExtendScript], die aan [!DNL JavaScript] gelijkaardig is. Voor informatie over [!DNL InDesign] manuscripten zie [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

## Hoe de extractie werkt {#how-the-extraction-works}

De [!DNL Adobe InDesign Server] kan met [!DNL Experience Manager Assets] worden geïntegreerd zodat INDD-bestanden die met [!DNL InDesign] zijn gemaakt, kunnen worden geüpload, uitvoeringen worden gegenereerd, alle media kunnen worden uitgepakt (bijvoorbeeld video) en kunnen worden opgeslagen als elementen:

>[!NOTE]
>
>In eerdere versies van [!DNL Experience Manager] konden XMP en de miniatuur worden opgehaald. Alle media kunnen nu worden uitgepakt.

1. Upload uw INDD-bestand naar [!DNL Experience Manager Assets].
1. Een framework verzendt opdrachtscript(s) naar de [!DNL InDesign Server] via SOAP (Simple Object Access Protocol).
Dit opdrachtscript:

   * Haal het INDD-bestand op.
   * [!DNL InDesign Server]-opdrachten uitvoeren:

      * De structuur, de tekst en alle mediabestanden worden geëxtraheerd.
      * Er worden PDF- en JPG-uitvoeringen gegenereerd.
      * HTML- en IDML-uitvoeringen worden gegenereerd.
   * Plaats de resulterende bestanden weer op [!DNL Experience Manager Assets].

   >[!NOTE]
   >
   >IDML is een op XML gebaseerde indeling die alle inhoud van het [!DNL InDesign]-bestand rendert. Het wordt opgeslagen als samengeperst pakket gebruikend [ZIP](https://www.techterms.com/definition/zip) compressie. Zie [InDesign Interchange Formats INX en IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8) voor meer informatie.

   >[!CAUTION]
   >
   >Als [!DNL InDesign Server] niet geïnstalleerd of niet gevormd is, dan kunt u een INDD dossier in [!DNL Experience Manager] nog uploaden. De gegenereerde uitvoeringen zijn echter beperkt tot PNG en JPEG. U kunt geen HTML-, idml- of paginauitvoeringen genereren.

1. Na de extractie en uitvoering:

   * De structuur wordt gerepliceerd naar een `cq:Page` (type vertoning).
   * De geëxtraheerde tekst en bestanden worden opgeslagen in [!DNL Experience Manager Assets].
   * Alle uitvoeringen worden opgeslagen in [!DNL Experience Manager Assets], in het element zelf.

## De [!DNL InDesign Server] integreren met Experience Manager {#integrating-the-indesign-server-with-aem}

Om [!DNL InDesign Server] voor gebruik met [!DNL Experience Manager Assets] en na het vormen van uw volmacht te integreren, moet u:

1. [Installeer de InDesign Server](#installing-the-indesign-server).
1. Indien nodig [configureer de Workflow voor Experience Manager Assets](#configuring-the-aem-assets-workflow).
Dit is alleen nodig als de standaardwaarden niet geschikt zijn voor uw instantie.
1. Configureer een [proxyworker voor de InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### [!DNL InDesign Server] {#installing-the-indesign-server} installeren

[!DNL InDesign Server] installeren en starten voor gebruik met [!DNL Experience Manager]:

1. Download en installeer [!DNL InDesign Server].

1. Indien nodig, kunt u de configuratie van uw [!DNL InDesign Server] instantie aanpassen.

1. Start de server vanaf de opdrachtregel:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Hierdoor start u de server met de SOAP-insteekmodule die luistert op poort 8080. Alle logboekberichten en output worden geschreven direct aan het bevelvenster.

   >[!NOTE]
   >
   >Als u de outputberichten aan een dossier wilt bewaren dan gebruik redirection; bijvoorbeeld onder Windows:
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### De [!DNL Experience Manager Assets]-workflow {#configuring-the-aem-assets-workflow} configureren

[!DNL Experience Manager Assets] beschikt over een vooraf geconfigureerde workflow  **[!UICONTROL DAM Update Asset]** met specifieke verschillende processtappen voor  [!DNL InDesign]:

* [Media extraheren](#media-extraction)
* [Pagina uitnemen](#page-extraction)

Dit werkschema is opstelling met standaardwaarden die voor uw opstelling op de diverse auteursinstanties (dit is een standaardwerkschema, zodat is de verdere informatie beschikbaar onder [het Uitgeven van een Werkschema](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)) kunnen worden aangepast. Als u de standaardwaarden (met inbegrip van de haven van de ZEEP) gebruikt, dan is geen configuratie nodig.

Na de installatie wordt het uploaden van [!DNL InDesign] bestanden naar [!DNL Experience Manager Assets] (met een van de gebruikelijke methoden) de workflow gestart om het element te verwerken en de verschillende uitvoeringen voor te bereiden. Test uw configuratie door een INDD-bestand te uploaden naar [!DNL Experience Manager Assets] om te bevestigen dat de verschillende uitvoeringen die door IDS onder `<*your_asset*>.indd/Renditions` zijn gemaakt, worden weergegeven

#### Media-extractie {#media-extraction}

Deze stap bepaalt de extractie van media uit het INDD-bestand.

Als u een document wilt aanpassen, kunt u het tabblad **[!UICONTROL Arguments]** van de stap **[!UICONTROL Media Extraction]** bewerken.

![Argumenten voor het uitnemen van media en scriptpaden](assets/media_extraction_arguments_scripts.png)

Argumenten voor het uitnemen van media en scriptpaden

* **ExtendScript-bibliotheek**: Dit is een eenvoudige http-methodebibliotheek, vereist door de andere scripts.

* **Scripts** uitbreiden: Hier kunt u verschillende scriptcombinaties opgeven. Als u uw eigen manuscripten op [!DNL InDesign Server] wilt worden uitgevoerd, sparen de manuscripten bij `/apps/settings/dam/indesign/scripts`.

Voor informatie over [!DNL Adobe InDesign] manuscripten, zie [InDesign ontwikkelaardocumentatie](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)

>[!CAUTION]
>
>Wijzig de ExtendScript-bibliotheek niet. Deze bibliotheek biedt de HTTP-functionaliteit die nodig is voor communicatie met Sling. Deze instelling geeft de bibliotheek aan die naar [!DNL InDesign Server] moet worden verzonden voor gebruik daar.

Met het `ThumbnailExport.jsx`-script dat wordt uitgevoerd door de workflowstap Media Extraction, wordt een miniatuuruitvoering in JPG-indeling gegenereerd. Deze vertoning wordt gebruikt door de werkstroomstap Miniaturen verwerken om de statische uitvoeringen te genereren die worden vereist door [!DNL Experience Manager].

U kunt de workflowstap Miniaturen verwerken zodanig configureren dat statische uitvoeringen van verschillende grootten worden gegenereerd. Zorg ervoor dat u niet de gebreken verwijdert, omdat zij door de [!DNL Experience Manager Assets] interface worden vereist. Tot slot verwijdert de werkstroomstap Voorvertoning van afbeelding verwijderen de uitvoering van de JPG-miniatuur, omdat deze niet langer nodig is.

#### Pagina-extractie {#page-extraction}

Hiermee maakt u een [!DNL Experience Manager]-pagina van de geëxtraheerde elementen. Een extractiemanager wordt gebruikt om gegevens uit een vertoning (momenteel HTML of IDML) te halen. Deze gegevens worden vervolgens gebruikt om een pagina te maken met de PageBuilder.

Als u een document wilt aanpassen, kunt u het tabblad **[!UICONTROL Arguments]** van de stap **[!UICONTROL Page Extraction]** bewerken.

![chlimage_1-96](assets/chlimage_1-289.png)

* **Handler voor** uitpakken van pagina: Selecteer in de keuzelijst de handler die u wilt gebruiken. Een extractiehandler werkt op een specifieke uitvoering, die door een verwante `RenditionPicker` (zie de `ExtractionHandler`-API) wordt gekozen.
In een standaard [!DNL Experience Manager] installatie is het volgende beschikbaar:
   * IDML Handgreep Extractie: Werkt op de `IDML` vertoning die in de stap MediaExtract wordt geproduceerd.

* **Paginanaam**: Geef de naam op die u aan de resulterende pagina wilt toewijzen. Als deze optie leeg blijft, is de naam &quot;page&quot; (of een derivaat als &quot;page&quot; al bestaat).

* **Paginatitel**: Geef de titel op die u aan de resulterende pagina wilt toewijzen.

* **Basispad** pagina: Het pad naar de hoofdlocatie van de resulterende pagina. Als dit leeg wordt gelaten, wordt het knooppunt gebruikt dat de uitvoeringen van het element bevat.

* **Paginasjabloon**: De sjabloon die moet worden gebruikt bij het genereren van de resulterende pagina.

* **Paginaontwerp**: Het paginaontwerp dat moet worden gebruikt bij het genereren van de resulterende pagina.

### De proxyworker configureren voor [!DNL InDesign Server] {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>De worker bevindt zich op de proxyinstantie.

1. Vouw **[!UICONTROL Cloud Services Configurations]** in het linkerdeelvenster van de gereedschapsconsole uit. Vouw vervolgens **[!UICONTROL Cloud Proxy Configuration]** uit.

1. Dubbelklik op **[!UICONTROL IDS worker]** om de configuratie te openen.

1. Klik **[!UICONTROL Edit]** om het configuratiedialoogvenster te openen en de vereiste instellingen te definiëren:

   ![proxy_disworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS**
PoolHet (de) eindpunt(en) van de ZEEP die voor het communiceren met  [!DNL InDesign Server]. U kunt items toevoegen, verwijderen en bestellen.

1. Klik op OK om op te slaan.

### De ExtensionAlizer {#configuring-day-cq-link-externalizer} van de Verbinding van Dag CQ vormen

Als [!DNL InDesign Server] en [!DNL Experience Manager] op verschillende gastheren of één van beide of beide toepassingen niet op standaardhavens lopen, vorm [!UICONTROL Day CQ Link Externalizer] om de gastheernaam, de haven, en de inhoudspad voor [!DNL InDesign Server] te plaatsen.

1. Open de webconsole op `https://[aem_server]:[port]/system/console/configMgr`.
1. Zoek de configuratie **[!UICONTROL Day CQ Link Externalizer]** en klik **[!UICONTROL Edit]** om deze te openen.
1. Geef de hostnaam en het contextpad op voor [!DNL Adobe InDesign Server] en klik op **Opslaan**.

   ![chlimage_1-97](assets/chlimage_1-290.png)

### Parallelle taakverwerking inschakelen voor [!DNL InDesign Server] {#enabling-parallel-job-processing-for-indesign-server-s}

U kunt nu parallelle taakverwerking inschakelen voor IDS. Bepaal het maximumaantal parallelle banen (`x`) en [!DNL InDesign Server] kan verwerken:

* Op één multiprocessorcomputer is het maximumaantal parallelle taken (`x`) dat een [!DNL InDesign Server] kan verwerken één minder dan het aantal processors met IDS.
* Wanneer u IDS op veelvoudige machines in werking stelt moet u het totale aantal beschikbare bewerkers (dat wil zeggen op alle machines) tellen dan het totale aantal machines aftrekken.

Om het aantal parallelle banen te vormen IDS:

1. Open het tabblad **[!UICONTROL Configurations]** van de Felix-console; bijvoorbeeld: `https://[aem_server]:[port]/system/console/configMgr`.

1. Selecteer de IDS verwerkingsrij onder `Apache Sling Job Queue Configuration`.

1. Set:

   * **Type** -  `Parallel`
   * **Maximale parallelle taken** -  `<*x*>` (zoals hierboven berekend)

1. Sla deze wijzigingen op.
1. Schakel het selectievakje `enable.multisession.name` onder `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuratie in om ondersteuning voor meerdere sessies voor Adobe CS6 en hoger in te schakelen.
1. Maak een [pool van `x` IDS-workers door SOAP-eindpunten toe te voegen aan de IDS Worker-configuratie](#configuring-the-proxy-worker-for-indesign-server).

   Als er meerdere computers zijn waarop [!DNL InDesign Server] wordt uitgevoerd, voegt u SOAP-eindpunten (aantal processors per computer -1) toe voor elke computer.

<!-- 
TBD: Make updates to configurations for allow and block list after product updates are done.
-->

>[!NOTE]
>
>Wanneer u werkt met een groep workers, kunt u de lijst van afgewezen personen van IDS-workers inschakelen.
>
>Om dit te doen, laat **[!UICONTROL enable.retry.name]** checkbox, onder de `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuratie toe, die IDS baanterugwinning toelaat.
>
>Ook, onder de `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configuratie, plaats een positieve waarde voor `max.errors.to.blacklist` parameter die aantal baanterugwinnen alvorens een IDS van de lijst van baanmanagers bepaalt.
>
>Door gebrek, na configureerbare (`retry.interval.to.whitelist.name`) tijd in notulen wordt de IDS worker opnieuw bevestigd. Als de worker online wordt gevonden, wordt deze uit de lijst van afgewezen personen verwijderd.

## Ondersteuning inschakelen voor [!DNL InDesign Server] 10.0 of hoger {#enabling-support-for-indesign-server-or-later}

Voer voor [!DNL InDesign Server] 10.0 of hoger de volgende stappen uit om ondersteuning voor meerdere sessies in te schakelen.

1. Open Configuration Manager vanuit uw [!DNL Experience Manager Assets]-instantie `https://[aem_server]:[port]/system/console/configMgr`.
1. Bewerk de configuratie `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selecteer de optie **[!UICONTROL ids.cc.enable]** en klik op **[!UICONTROL Save]**.

>[!NOTE]
>
>Voor [!DNL InDesign Server] integratie met [!DNL Experience Manager Assets], gebruik een multi-core bewerker omdat de zittingssteuneigenschap noodzakelijk voor de integratie niet op single core systemen wordt gesteund.

## [!DNL Experience Manager] aanmeldingsgegevens {#configure-aem-credentials} configureren

U kunt de standaardbeheerdergeloofsbrieven (gebruikersnaam en wachtwoord) veranderen om tot [!DNL InDesign Server] van uw [!DNL Experience Manager] plaatsing toegang te hebben zonder de integratie met [!DNL InDesign Server] te breken.

1. Ga naar `/etc/cloudservices/proxy.html`.
1. Geef in het dialoogvenster de nieuwe gebruikersnaam en het nieuwe wachtwoord op.
1. Sla de referenties op.

>[!MORELIKETHIS]
>
>* [Informatie over Adobe InDesign Server](https://www.adobe.com/products/indesignserver/faq.html)

