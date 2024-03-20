---
title: Integreren [!DNL Assets] with [!DNL InDesign Server]
description: Leer hoe u kunt integreren [!DNL Adobe Experience Manager Assets] with [!DNL Adobe InDesign Server].
contentOwner: AG
role: Admin
feature: Publishing
exl-id: 5ba020a3-c36c-402b-a11b-d6b0426b03bf
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1523'
ht-degree: 0%

---

# Integreren [!DNL Adobe Experience Manager Assets] with [!DNL Adobe InDesign Server] {#integrating-aem-assets-with-indesign-server}

[!DNL Adobe Experience Manager Assets] gebruik:

* Een proxy om het laden van bepaalde verwerkingstaken te verdelen. Een proxy is een [!DNL Experience Manager] instantie die communiceert met een proxyworker om een specifieke taak uit te voeren, en andere [!DNL Experience Manager] instanties om de resultaten te leveren.
* Een volmachtsarbeider om een specifieke taak te bepalen en te beheren.
Deze kunnen betrekking hebben op een groot aantal verschillende taken, zoals het gebruik van een [!DNL InDesign Server] om bestanden te verwerken.

Bestanden volledig uploaden naar [!DNL Experience Manager Assets] die u hebt gemaakt [!DNL Adobe InDesign] er wordt een proxy gebruikt. Dit gebruikt een volmachtsarbeider om met te communiceren [!DNL Adobe InDesign Server], waarbij [scripts](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) worden uitgevoerd om metagegevens te extraheren en verschillende uitvoeringen te genereren voor [!DNL Experience Manager Assets]. De volmachtsarbeider laat de bidirectionele communicatie tussen toe [!DNL InDesign Server] en de [!DNL Experience Manager] instanties in een cloudconfiguratie.

>[!NOTE]
>
>[!DNL Adobe InDesign] wordt aangeboden als twee afzonderlijke aanbiedingen. [Adobe InDesign](https://www.adobe.com/products/indesign.html) bureaubladtoepassing die wordt gebruikt voor het ontwerpen van paginalay-outs voor afdrukken en digitale distributie. [Adobe InDesign Server](https://www.adobe.com/products/indesignserver.html) laat u toe om geautomatiseerde documenten programmatically tot stand te brengen die op wat u met hebt gecreeerd [!DNL InDesign]. Het werkt als dienst die een interface aan zijn aanbiedt [ExtendScript](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) engine.De scripts zijn geschreven in [!DNL ExtendScript], die vergelijkbaar is met [!DNL JavaScript]. Voor informatie over [!DNL InDesign] scripts zie [https://www.adobe.com/devnet/indesign/documentation.html#idscripting](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

## Hoe de extractie werkt {#how-the-extraction-works}

De [!DNL Adobe InDesign Server] kan worden geïntegreerd met [!DNL Experience Manager Assets] zodat INDD-bestanden zijn gemaakt met [!DNL InDesign] kan worden geüpload, vertoningen worden gegenereerd, alle media kunnen worden uitgepakt (bijvoorbeeld video) en kunnen worden opgeslagen als elementen:

>[!NOTE]
>
>Eerdere versies van [!DNL Experience Manager] konden XMP en de miniatuur extraheren, nu kunnen alle media worden geëxtraheerd.

1. Het INDD-bestand uploaden naar [!DNL Experience Manager Assets].
1. Een framework verzendt opdrachtscript(s) naar de [!DNL InDesign Server] via SOAP (Simple Object Access Protocol).
Met dit opdrachtscript wordt:

   * Haal het INDD-bestand op.
   * Uitvoeren [!DNL InDesign Server] opdrachten:

      * De structuur, de tekst en alle mediabestanden worden geëxtraheerd.
      * PDF- en JPG-uitvoeringen worden gegenereerd.
      * HTML- en IDML-uitvoeringen worden gegenereerd.

   * De resulterende bestanden opnieuw plaatsen naar [!DNL Experience Manager Assets].

   >[!NOTE]
   >
   >IDML is een op XML gebaseerd formaat dat alle inhoud van [!DNL InDesign] bestand. Het wordt opgeslagen als een gecomprimeerd pakket met [ZIP](https://www.techterms.com/definition/zip) compressie. Zie voor meer informatie [InDesign Interchange Formats INX en IDML](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8).

   >[!CAUTION]
   >
   >Als de [!DNL InDesign Server] is niet geïnstalleerd of niet geconfigureerd, kunt u nog steeds een INDD-bestand uploaden naar [!DNL Experience Manager]. De gegenereerde uitvoeringen zijn echter beperkt tot PNG en JPEG. U kunt geen HTML-, idml- of paginauitvoeringen genereren.

1. Na de extractie en uitvoering:

   * De structuur wordt gerepliceerd naar een `cq:Page` (type vertoning).
   * De geëxtraheerde tekst en bestanden worden opgeslagen in [!DNL Experience Manager Assets].
   * Alle uitvoeringen worden opgeslagen in [!DNL Experience Manager Assets], in het actief zelf.

## De [!DNL InDesign Server] met Experience Manager {#integrating-the-indesign-server-with-aem}

Om de [!DNL InDesign Server] voor gebruik met [!DNL Experience Manager Assets] en nadat u de proxy hebt geconfigureerd, moet u:

1. [Het InDesign Server installeren](#installing-the-indesign-server).
1. Indien nodig [De Experience Manager Assets-workflow configureren](#configuring-the-aem-assets-workflow).
Dit is alleen nodig als de standaardwaarden niet geschikt zijn voor uw instantie.
1. Een [proxyworker voor het InDesign Server](#configuring-the-proxy-worker-for-indesign-server).

### Installeer de [!DNL InDesign Server] {#installing-the-indesign-server}

Als u de [!DNL InDesign Server] voor gebruik met [!DNL Experience Manager]:

1. Download en installeer de [!DNL InDesign Server].

1. Indien nodig, kunt u de configuratie van uw [!DNL InDesign Server] -instantie.

1. Start de server vanaf de opdrachtregel:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Hierdoor start u de server met de SOAP-insteekmodule die luistert op poort 8080. Alle logboekberichten en output worden geschreven direct aan het bevelvenster.

   >[!NOTE]
   >
   >Als u de uitvoerberichten in een bestand wilt opslaan, gebruikt u een andere richting, bijvoorbeeld onder Windows:
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### Vorm [!DNL Experience Manager Assets] werkstroom {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager Assets] beschikt over een vooraf geconfigureerde workflow **[!UICONTROL DAM Update Asset]**, die verschillende processtappen bevat die specifiek voor [!DNL InDesign]:

* [Media extraheren](#media-extraction)
* [Pagina uitnemen](#page-extraction)

Dit werkschema is opstelling met standaardwaarden die voor uw opstelling op de diverse auteursinstanties (dit is een standaardwerkschema, zodat is de verdere informatie beschikbaar onder [Een workflow bewerken](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Als u de standaardwaarden (met inbegrip van de haven van de ZEEP) gebruikt, dan is geen configuratie nodig.

Na de installatie uploaden [!DNL InDesign] bestanden in [!DNL Experience Manager Assets] (met een van de gebruikelijke methoden) activeert de workflow om het element te verwerken en de verschillende uitvoeringen voor te bereiden. Test uw configuratie door een INDD-bestand te uploaden naar [!DNL Experience Manager Assets] om te bevestigen dat u de verschillende vertoningen ziet die door IDS onder worden gecreeerd `<*your_asset*>.indd/Renditions`

#### Media-extractie {#media-extraction}

Deze stap bepaalt de extractie van media uit het INDD-bestand.

Als u deze wilt aanpassen, kunt u **[!UICONTROL Arguments]** tabblad van het **[!UICONTROL Media Extraction]** stap.

![Argumenten voor het uitnemen van media en scriptpaden](assets/media_extraction_arguments_scripts.png)

Argumenten voor het uitnemen van media en scriptpaden

* **ExtendScript-bibliotheek**: Dit is een eenvoudige http-methodebibliotheek, vereist door de andere scripts.

* **Scripts uitbreiden**: U kunt hier verschillende scriptcombinaties opgeven. Als u uw eigen scripts wilt uitvoeren op het tabblad [!DNL InDesign Server], sla de scripts op `/apps/settings/dam/indesign/scripts`.

<!-- TBD: Hiding this link since ADC is not available anymore. 
For information about [!DNL Adobe InDesign] scripts, see [InDesign developer documentation](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
-->

>[!CAUTION]
>
>Wijzig de ExtendScript-bibliotheek niet. Deze bibliotheek biedt de HTTP-functionaliteit die nodig is voor communicatie met Sling. Met deze instelling wordt opgegeven welke bibliotheek naar de [!DNL InDesign Server] voor gebruik daar.

De `ThumbnailExport.jsx` een script uitvoeren dat wordt uitgevoerd door de workflowstap Media Extraction, genereert een miniatuuruitvoering in de JPG-indeling. Deze vertoning wordt gebruikt door de workflowstap Miniaturen verwerken om de statische vertoningen te genereren die worden vereist door [!DNL Experience Manager].

U kunt de workflowstap Miniaturen verwerken zodanig configureren dat statische uitvoeringen van verschillende grootten worden gegenereerd. Zorg ervoor dat u de standaardinstellingen niet verwijdert, omdat deze vereist zijn voor de [!DNL Experience Manager Assets] interface. Tot slot verwijdert de werkstroomstap Voorvertoning van afbeelding verwijderen de uitvoering van de JPG-miniatuur, omdat deze niet langer nodig is.

#### Pagina uitnemen {#page-extraction}

Hiermee maakt u een [!DNL Experience Manager] pagina uit de geëxtraheerde elementen. Een extractiemanager wordt gebruikt om gegevens uit een vertoning (momenteel HTML of IDML) te halen. Deze gegevens worden vervolgens gebruikt om een pagina te maken met de PageBuilder.

Als u de **[!UICONTROL Arguments]** tabblad van het **[!UICONTROL Page Extraction]** stap.

![chlimage_1-96](assets/chlimage_1-289.png)

* **Handler voor pagina-uitname**: Selecteer in de keuzelijst de handler die u wilt gebruiken. Een extractiemanager werkt op een specifieke uitvoering, gekozen door een verwante `RenditionPicker` (zie de `ExtractionHandler` API). Standaard [!DNL Experience Manager] installatie het volgende is beschikbaar:
   * IDML Handgreep Extractie: werkt op de `IDML` vertoning die in de stap MediaExtract wordt geproduceerd.

* **Paginanaam**: Geef de naam op die u aan de resulterende pagina wilt toewijzen. Als deze optie leeg blijft, is de naam &quot;page&quot; (of een derivaat als &quot;page&quot; al bestaat).

* **Paginatitel**: Geef de titel op die u aan de resulterende pagina wilt toewijzen.

* **Basispad pagina**: Het pad naar de hoofdlocatie van de resulterende pagina. Indien leeg gelaten, wordt het knooppunt gebruikt dat de uitvoeringen van het element bevat.

* **Paginasjabloon**: De sjabloon die moet worden gebruikt bij het genereren van de resulterende pagina.

* **Paginaontwerp**: Het paginaontwerp dat moet worden gebruikt bij het genereren van de resulterende pagina.

### De proxyworker configureren voor [!DNL InDesign Server] {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>De worker bevindt zich op de proxyinstantie.

1. Vouw in de console Tools de **[!UICONTROL Cloud Services Configurations]** in het linkerdeelvenster. Vouw vervolgens uit **[!UICONTROL Cloud Proxy Configuration]**.

1. Dubbelklik op de knop **[!UICONTROL IDS worker]** om te openen voor configuratie.

1. Klikken **[!UICONTROL Edit]** om het configuratiedialoogvenster te openen en de vereiste instellingen te definiëren:

   ![proxy_disworkerconfig](assets/proxy_idsworkerconfig.png)

   * **IDS Pool**
Het (de) eindpunt(en) van de ZEEP die moeten worden gebruikt voor de communicatie met de [!DNL InDesign Server]. U kunt items toevoegen, verwijderen en bestellen.

1. Klik op OK om op te slaan.

### vorm de Verbinding van CQ van de Dag uiterlijk {#configuring-day-cq-link-externalizer}

Als de [!DNL InDesign Server] en [!DNL Experience Manager] zijn op verschillende gastheren of één van beide toepassingen werken niet aan standaardhavens, dan vormen [!UICONTROL Day CQ Link Externalizer] om de hostnaam, poort en inhoudspad voor de [!DNL InDesign Server].

1. Toegang tot de webconsole op `https://[aem_server]:[port]/system/console/configMgr`.
1. De configuratie zoeken **[!UICONTROL Day CQ Link Externalizer]**. Klikken **[!UICONTROL Edit]** openen.
1. Met de instellingen voor Extern koppelen kunt u absolute URL&#39;s maken voor de [!DNL Experience Manager] en voor de [!DNL InDesign Server]. Gebruiken **[!UICONTROL Domains]** veld om de hostnaam voor het [!DNL Adobe InDesign Server]. Klikken **Opslaan**.

   In absolute URL&#39;s gebruikt u `localhost` als de hostnaam voor uw lokale (auteur)instantie en de hostnaam of het IP-adres voor de publicatie-instantie, zoals in de volgende afbeelding wordt getoond.

   ![Instellingen voor extern hulpprogramma koppelen](assets/link-externalizer-config.png)

### Parallelle verwerking van taken inschakelen voor [!DNL InDesign Server] {#enabling-parallel-job-processing-for-indesign-server}

U kunt nu parallelle taakverwerking inschakelen voor IDS. Het maximumaantal parallelle taken bepalen (`x`) [!DNL InDesign Server] kan verwerken:

* Op één multiprocessorcomputer is het maximumaantal parallelle taken (`x`) dat [!DNL InDesign Server] kan één minder verwerken dan het aantal processors met IDS.
* Wanneer u IDS op veelvoudige machines in werking stelt moet u het totale aantal beschikbare bewerkers (dat wil zeggen op alle machines) tellen dan het totale aantal machines aftrekken.

Om het aantal parallelle banen te vormen IDS:

1. Open de **[!UICONTROL Configurations]** tabblad van Felix Console, bijvoorbeeld: `https://[aem_server]:[port]/system/console/configMgr`.

1. Selecteer de verwerkingsrij IDS onder `Apache Sling Job Queue Configuration`.

1. Instellen:

   * **Type** - `Parallel`
   * **Maximale parallelle taken** - `<*x*>` (zoals hierboven berekend)

1. Sla deze wijzigingen op.
1. Als u ondersteuning voor meerdere sessies wilt inschakelen voor Adobe CS6 en hoger, schakelt u `enable.multisession.name` selectievakje, onder `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuratie.
1. Een [pool van `x` IDS de arbeiders door de eindpunten van de ZEEP aan de configuratie van de Arbeider IDS toe te voegen](#configuring-the-proxy-worker-for-indesign-server).

   Als er meerdere computers actief zijn [!DNL InDesign Server]voegt u SOAP-eindpunten (aantal processors per computer -1) toe voor elke computer.

<!-- 
TBD: Make updates to configurations for allow and block list after product updates are done.
-->

>[!NOTE]
>
>Wanneer u werkt met een groep workers, kunt u de lijst van gewezen personen van IDS-workers inschakelen.
>
>Om dit te doen, laat **[!UICONTROL enable.retry.name]** selectievakje, onder `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuratie, waardoor IDS-taken kunnen worden opgehaald.
>
>Onder de `com.day.cq.dam.ids.impl.IDSPoolImpl.name` configuratie, een positieve waarde instellen voor `max.errors.to.blacklist` parameter die het aantal taakterugwinnen alvorens een IDS van de lijst van baanmanagers bepaalt.
>
>Door gebrek, na configureerbaar (`retry.interval.to.whitelist.name`) in minuten wordt de IDS-worker opnieuw gevalideerd. Als de worker online wordt gevonden, wordt deze uit de lijst van gewezen personen verwijderd.

## Ondersteuning inschakelen voor [!DNL InDesign Server] 10.0 of hoger {#enabling-support-for-indesign-server-or-later}

Voor [!DNL InDesign Server] 10.0 of hoger, voer de volgende stappen uit om ondersteuning voor meerdere sessies mogelijk te maken.

1. Configuratiebeheer openen vanuit uw [!DNL Experience Manager Assets] instance `https://[aem_server]:[port]/system/console/configMgr`.
1. De configuratie bewerken `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selecteer de **[!UICONTROL ids.cc.enable]** en klik op **[!UICONTROL Save]**.

>[!NOTE]
>
>Voor [!DNL InDesign Server] integratie met [!DNL Experience Manager Assets], gebruik een multicore-processor omdat de functie voor sessieondersteuning die nodig is voor de integratie niet wordt ondersteund op single core-systemen.

## Configureren [!DNL Experience Manager] geloofsbrieven {#configure-aem-credentials}

U kunt de standaardbeheerdersreferenties (gebruikersnaam en wachtwoord) wijzigen voor toegang tot de [!DNL InDesign Server] van uw [!DNL Experience Manager] implementatie zonder de integratie met de [!DNL InDesign Server].

1. Ga naar `/etc/cloudservices/proxy.html`.
1. Geef in het dialoogvenster de nieuwe gebruikersnaam en het nieuwe wachtwoord op.
1. Sla de referenties op.

>[!MORELIKETHIS]
>
>* [Informatie over Adobe InDesign Server](https://www.adobe.com/products/indesignserver/faq.html)
