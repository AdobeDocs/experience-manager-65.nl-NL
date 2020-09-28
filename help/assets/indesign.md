---
title: ' [!DNL Assets] Integreren met [!DNL InDesign Server]'
description: Leer hoe u kunt [!DNL Adobe Experience Manager Assets] integreren met [!DNL Adobe InDesign Server].
contentOwner: AG
translation-type: tm+mt
source-git-commit: 5069c2cd26e84866d72a61d36de085dadd556cdd
workflow-type: tm+mt
source-wordcount: '1528'
ht-degree: 1%

---


# Integreren [!DNL Adobe Experience Manager Assets] met [!DNL Adobe InDesign Server] {#integrating-aem-assets-with-indesign-server}

[!DNL Adobe Experience Manager Assets] gebruik:

* Een proxy om het laden van bepaalde verwerkingstaken te verdelen. Een volmacht is een [!DNL Experience Manager] geval dat met een volmachtsarbeider communiceert om een specifieke taak te vervullen, en andere [!DNL Experience Manager] instanties om de resultaten te leveren.
* Een proxyworker om een specifieke taak te definiëren en te beheren.
Deze kunnen betrekking hebben op een groot aantal verschillende taken; bijvoorbeeld bestanden verwerken [!DNL InDesign Server] met behulp van een .

Voor het volledig uploaden van bestanden [!DNL Experience Manager Assets] die u met [!DNL Adobe InDesign] een proxy hebt gemaakt, wordt gebruikgemaakt. Dit gebruikt een volmachtsarbeider om met het te communiceren [!DNL Adobe InDesign Server], waar de [manuscripten](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) worden in werking gesteld om meta-gegevens te halen en diverse vertoningen voor te produceren [!DNL Experience Manager Assets]. De volmachtsarbeider laat de bidirectionele communicatie tussen de [!DNL InDesign Server] en de [!DNL Experience Manager] instanties in een wolkenconfiguratie toe.

>[!NOTE]
>
>[!DNL Adobe InDesign] wordt aangeboden als twee afzonderlijke aanbiedingen. [Adobe InDesign](https://www.adobe.com/products/indesign.html) -bureaubladtoepassing waarmee u paginalay-outs voor afdrukken en digitale distributie kunt ontwerpen. [Met Adobe InDesign Server](https://www.adobe.com/products/indesignserver.html) kunt u via programmacode geautomatiseerde documenten maken op basis van wat u hebt gemaakt [!DNL InDesign]. Het werkt als dienst die een interface aan zijn motor van [ExtendScript](https://www.adobe.com/devnet/scripting.html) aanbiedt.De manuscripten worden geschreven in [!DNL ExtendScript], die aan [!DNL JavaScript]. gelijkaardig is. Zie [!DNL InDesign] https://www.adobe.com/devnet/indesign/documentation.html#idscripting voor meer informatie over [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

## Hoe de extractie werkt {#how-the-extraction-works}

Het [!DNL Adobe InDesign Server] kan worden geïntegreerd met [!DNL Experience Manager Assets] zodat INDD-bestanden die zijn gemaakt met [!DNL InDesign] , kunnen worden geüpload, gegenereerde uitvoeringen, alle media die zijn uitgepakt (bijvoorbeeld video) en kunnen worden opgeslagen als elementen:

>[!NOTE]
>
>In eerdere versies van [!DNL Experience Manager] konden XMP en de miniatuur worden opgehaald. Alle media kunnen nu worden uitgepakt.

1. Upload het INDD-bestand naar [!DNL Experience Manager Assets].
1. Een framework verzendt opdrachtscript(s) naar de SOAP [!DNL InDesign Server] (Simple Object Access Protocol).
Dit opdrachtscript:

   * Haal het INDD-bestand op.
   * Opdrachten uitvoeren [!DNL InDesign Server] :

      * De structuur, de tekst en alle mediabestanden worden geëxtraheerd.
      * Er worden PDF- en JPG-uitvoeringen gegenereerd.
      * HTML- en IDML-uitvoeringen worden gegenereerd.
   * Plaats de resulterende bestanden terug naar [!DNL Experience Manager Assets].

   >[!NOTE]
   >
   >IDML is een op XML gebaseerde indeling die alle inhoud van het [!DNL InDesign] bestand rendert. Het wordt opgeslagen als een gecomprimeerd pakket met [ZIP](https://www.techterms.com/definition/zip) -compressie. Voor meer informatie, zie de Formaten INX en IDML van de [Uitwisseling van InDesign](http://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8).

   >[!CAUTION]
   >
   >Als het bestand niet [!DNL InDesign Server] is geïnstalleerd of niet is geconfigureerd, kunt u nog steeds een INDD-bestand uploaden naar [!DNL Experience Manager]. De gegenereerde uitvoeringen zijn echter beperkt tot PNG en JPEG. U kunt geen HTML-, idml- of paginauitvoeringen genereren.

1. Na de extractie en uitvoering:

   * De structuur wordt gerepliceerd naar een `cq:Page` (type vertoning).
   * De geëxtraheerde tekst en bestanden worden opgeslagen in [!DNL Experience Manager Assets].
   * Alle uitvoeringen worden opgeslagen in [!DNL Experience Manager Assets], in het element zelf.

## De [!DNL InDesign Server] Experience Manager integreren {#integrating-the-indesign-server-with-aem}

Om het [!DNL InDesign Server] voor gebruik met [!DNL Experience Manager Assets] en na het vormen van uw volmacht te integreren, moet u:

1. [Installeer de InDesign Server](#installing-the-indesign-server).
1. Indien nodig, [vorm de Workflow](#configuring-the-aem-assets-workflow)van de Activa van de Experience Manager.
Dit is alleen nodig als de standaardwaarden niet geschikt zijn voor uw instantie.
1. Configureer een [proxyworker voor de InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installeer de [!DNL InDesign Server] {#installing-the-indesign-server}

De toepassing installeren en starten [!DNL InDesign Server] met [!DNL Experience Manager]:

1. Download en installeer de [!DNL InDesign Server].

1. Indien nodig, kunt u de configuratie van uw [!DNL InDesign Server] instantie aanpassen.

1. Start de server vanaf de opdrachtregel:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Hierdoor start u de server met de SOAP-insteekmodule die luistert op poort 8080. Alle logboekberichten en output worden geschreven direct aan het bevelvenster.

   >[!NOTE]
   >
   >Als u de outputberichten aan een dossier wilt bewaren dan gebruik redirection; bijvoorbeeld onder Windows:
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### De [!DNL Experience Manager Assets] workflow configureren {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager Assets] beschikt over een vooraf geconfigureerde workflow **[!UICONTROL DAM Update Asset]** met specifieke verschillende processtappen voor [!DNL InDesign]:

* [Media extraheren](#media-extraction)
* [Pagina uitnemen](#page-extraction)

Dit werkschema is opstelling met standaardwaarden die voor uw opstelling op de diverse auteursinstanties (dit is een standaardwerkschema, zodat is de verdere informatie beschikbaar onder het [Uitgeven van een Werkschema](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)) kunnen worden aangepast. Als u de standaardwaarden (met inbegrip van de haven van de ZEEP) gebruikt, dan is geen configuratie nodig.

Na de installatie zorgt het uploaden van [!DNL InDesign] bestanden naar [!DNL Experience Manager Assets] (een van de gebruikelijke methoden) ervoor dat de workflow het element verwerkt en de verschillende uitvoeringen voorbereidt. Test uw configuratie door een INDD-bestand te uploaden naar [!DNL Experience Manager Assets] om te bevestigen dat de verschillende uitvoeringen die onder IDS zijn gemaakt, worden weergegeven `<*your_asset*>.indd/Renditions`

#### Media-extractie {#media-extraction}

Deze stap bepaalt de extractie van media uit het INDD-bestand.

U kunt het **[!UICONTROL Arguments]** tabblad van de **[!UICONTROL Media Extraction]** stap aanpassen.

![Argumenten voor het uitnemen van media en scriptpaden](assets/media_extraction_arguments_scripts.png)

Argumenten voor het uitnemen van media en scriptpaden

* **ExtendScript-bibliotheek**: Dit is een eenvoudige http-methodebibliotheek, vereist door de andere scripts.

* **Scripts** uitbreiden: Hier kunt u verschillende scriptcombinaties opgeven. Als u wilt dat uw eigen scripts op de computer worden uitgevoerd [!DNL InDesign Server], slaat u de scripts op `/apps/settings/dam/indesign/scripts`.

Zie de documentatie voor ontwikkelaars van [!DNL Adobe InDesign] InDesign voor informatie over [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting)

>[!CAUTION]
>
>Wijzig de ExtendScript-bibliotheek niet. Deze bibliotheek biedt de HTTP-functionaliteit die nodig is voor communicatie met Sling. Met deze instelling geeft u de bibliotheek op die naar de bibliotheek moet worden verzonden [!DNL InDesign Server] voor gebruik daar.

Het `ThumbnailExport.jsx` script dat wordt uitgevoerd door de workflowstap Media Extraction, genereert een miniatuuruitvoering in de JPG-indeling. Deze vertoning wordt gebruikt door de werkstroomstap Miniaturen verwerken om de statische uitvoeringen te genereren die vereist zijn door [!DNL Experience Manager].

U kunt de workflowstap Miniaturen verwerken zodanig configureren dat statische uitvoeringen van verschillende grootten worden gegenereerd. Zorg ervoor dat u niet de gebreken verwijdert, omdat zij door de [!DNL Experience Manager Assets] interface worden vereist. Tot slot verwijdert de werkstroomstap Voorvertoning van afbeelding verwijderen de uitvoering van de JPG-miniatuur, omdat deze niet langer nodig is.

#### Pagina uitnemen {#page-extraction}

Hiermee maakt u een [!DNL Experience Manager] pagina van de geëxtraheerde elementen. Een extractiemanager wordt gebruikt om gegevens uit een vertoning (momenteel HTML of IDML) te halen. Deze gegevens worden vervolgens gebruikt om een pagina te maken met de PageBuilder.

To customize, you can edit the **[!UICONTROL Arguments]** tab of the **[!UICONTROL Page Extraction]** step.

![chlimage_1-96](assets/chlimage_1-289.png)

* **Handler voor** uitpakken van pagina: Selecteer in de keuzelijst de handler die u wilt gebruiken. Een extractiehandler werkt op een specifieke uitvoering, die door een verwante `RenditionPicker` (zie de `ExtractionHandler`-API) wordt gekozen.
In a standard [!DNL Experience Manager] installation the following is available:
   * IDML Handgreep Extractie: Werkt op de vertoning die in de stap MediaExtract wordt geproduceerd. `IDML`

* **Paginanaam**: Geef de naam op die u aan de resulterende pagina wilt toewijzen. Als deze optie leeg blijft, is de naam &quot;page&quot; (of een derivaat als &quot;page&quot; al bestaat).

* **Paginatitel**: Geef de titel op die u aan de resulterende pagina wilt toewijzen.

* **Basispad** pagina: Het pad naar de hoofdlocatie van de resulterende pagina. Als dit leeg wordt gelaten, wordt het knooppunt gebruikt dat de uitvoeringen van het element bevat.

* **Paginasjabloon**: De sjabloon die moet worden gebruikt bij het genereren van de resulterende pagina.

* **Paginaontwerp**: Het paginaontwerp dat moet worden gebruikt bij het genereren van de resulterende pagina.

### De proxyworker configureren voor [!DNL InDesign Server] {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>De worker bevindt zich op de proxyinstantie.

1. Vouw in het linkerdeelvenster van de gereedschapsconsole **[!UICONTROL Cloud Services Configurations]** uit. Vouw vervolgens uit **[!UICONTROL Cloud Proxy Configuration]**.

1. Dubbelklik op het bestand **[!UICONTROL IDS worker]** dat u wilt openen voor configuratie.

1. Klik **[!UICONTROL Edit]** om het configuratiedialoogvenster te openen en de vereiste instellingen te definiëren:

   ![proxy_disworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS-pool** Het/de SOAP-eindpunt(en) dat/die moet/moeten worden gebruikt voor communicatie met de [!DNL InDesign Server]. U kunt items toevoegen, verwijderen en bestellen.

1. Klik op OK om op te slaan.

### vorm de Verbinding van CQ van de Dag uiterlijk {#configuring-day-cq-link-externalizer}

Als [!DNL InDesign Server] en [!DNL Experience Manager] lopen op verschillende gastheren of één van beiden of beide toepassingen niet op standaardhavens lopen, vorm [!UICONTROL Day CQ Link Externalizer] om de gastheernaam, de haven, en de inhoudspad voor [!DNL InDesign Server]. te plaatsen.

1. Open de webconsole op `https://[aem_server]:[port]/system/console/configMgr`.
1. Zoek de configuratie **[!UICONTROL Day CQ Link Externalizer]** en klik **[!UICONTROL Edit]** om deze te openen.
1. Geef de hostnaam en het contextpad voor de toepassing op [!DNL Adobe InDesign Server] en klik op **Opslaan**.

   ![chlimage_1-97](assets/chlimage_1-290.png)

### Parallelle verwerking van taken inschakelen voor [!DNL InDesign Server] {#enabling-parallel-job-processing-for-indesign-server-s}

U kunt nu parallelle taakverwerking inschakelen voor IDS. Bepaal het maximumaantal parallelle banen (`x`) een [!DNL InDesign Server] kan verwerken:

* Op één multiprocessorcomputer is het maximumaantal parallelle taken (`x`[!DNL InDesign Server] ) dat een processor kan verwerken één kleiner dan het aantal processors met IDS.
* Wanneer u IDS op veelvoudige machines in werking stelt moet u het totale aantal beschikbare bewerkers (dat wil zeggen op alle machines) tellen dan het totale aantal machines aftrekken.

Om het aantal parallelle banen te vormen IDS:

1. Open het **[!UICONTROL Configurations]** tabblad van de Felix-console; bijvoorbeeld: `https://[aem_server]:[port]/system/console/configMgr`.

1. Selecteer de IDS verwerkingsrij onder `Apache Sling Job Queue Configuration`.

1. Set:

   * **Type** - `Parallel`
   * **Maximale parallelle taken** - `<*x*>` (zoals hierboven berekend)

1. Sla deze wijzigingen op.
1. Schakel het selectievakje onder `enable.multisession.name` `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuratie in om ondersteuning voor meerdere sessies voor Adobe CS6 en hoger in te schakelen.
1. Creeer een [pool van de arbeiders van `x` IDS door de eindpunten van de ZEEP aan de configuratie](#configuring-the-proxy-worker-for-indesign-server)van de Arbeider IDS toe te voegen.

   Als er meerdere computers actief zijn [!DNL InDesign Server], voegt u SOAP-eindpunten (aantal processors per computer -1) toe voor elke computer.

<!-- 
TBD: Make updates to configurations for allow and block list after product updates are done.
-->

>[!NOTE]
>
>Wanneer u werkt met een groep workers, kunt u de lijst van afgewezen personen van IDS-workers inschakelen.
>
>Om dit te doen, laat **[!UICONTROL enable.retry.name]** checkbox, onder de `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuratie toe, die IDS baanterugwinning toelaat.
>
>Ook, onder de `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configuratie, plaats een positieve waarde voor `max.errors.to.blacklist` parameter die aantal baanterugwinnen alvorens IDS van de lijst van baanmanagers bepaalt.
>
>De IDS-worker wordt standaard opnieuw gevalideerd nadat de configureerbare (`retry.interval.to.whitelist.name`) tijd in minuten is verstreken. Als de worker online wordt gevonden, wordt deze uit de lijst van afgewezen personen verwijderd.

## Ondersteuning inschakelen voor [!DNL InDesign Server] 10.0 of hoger {#enabling-support-for-indesign-server-or-later}

Voer voor [!DNL InDesign Server] 10.0 of hoger de volgende stappen uit om ondersteuning voor meerdere sessies mogelijk te maken.

1. Open Configuration Manager van uw [!DNL Experience Manager Assets] instantie `https://[aem_server]:[port]/system/console/configMgr`.
1. Bewerk de configuratie `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selecteer de **[!UICONTROL ids.cc.enable]** optie en klik op **[!UICONTROL Save]**.

>[!NOTE]
>
>Voor [!DNL InDesign Server] integratie met [!DNL Experience Manager Assets], gebruik een multi-core bewerker omdat de zittingssteuneigenschap noodzakelijk voor de integratie niet op single-core systemen wordt gesteund.

## Referenties [!DNL Experience Manager] configureren {#configure-aem-credentials}

U kunt de standaardbeheerdersgeloofsbrieven (gebruikersnaam en wachtwoord) voor de toegang tot van uw plaatsing veranderen [!DNL InDesign Server] zonder de integratie met het [!DNL Experience Manager] uit te breken [!DNL InDesign Server].

1. Go to `/etc/cloudservices/proxy.html`.
1. Geef in het dialoogvenster de nieuwe gebruikersnaam en het nieuwe wachtwoord op.
1. Sla de referenties op.

>[!MORELIKETHIS]
>
>* [Informatie over Adobe InDesign Server](https://www.adobe.com/products/indesignserver/faq.html)

