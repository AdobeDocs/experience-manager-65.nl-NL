---
title: Integreer  [!DNL Assets]  met  [!DNL InDesign Server]
description: Leer hoe te om  [!DNL Adobe Experience Manager Assets]  met  [!DNL Adobe InDesign Server] te integreren.
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

# [!DNL Adobe Experience Manager Assets] integreren met [!DNL Adobe InDesign Server] {#integrating-aem-assets-with-indesign-server}

[!DNL Adobe Experience Manager Assets] gebruikt:

* Een proxy om het laden van bepaalde verwerkingstaken te verdelen. Een proxy is een [!DNL Experience Manager] -instantie die communiceert met een proxy-worker om een specifieke taak uit te voeren en andere [!DNL Experience Manager] -instanties om de resultaten te leveren.
* Een volmachtsarbeider om een specifieke taak te bepalen en te beheren.
Deze kunnen een groot aantal taken bestrijken, bijvoorbeeld het gebruik van een [!DNL InDesign Server] voor het verwerken van bestanden.

Voor het volledig uploaden van bestanden naar [!DNL Experience Manager Assets] die u met [!DNL Adobe InDesign] hebt gemaakt, wordt een proxy gebruikt. Dit gebruikt een volmachtsarbeider om met [!DNL Adobe InDesign Server] te communiceren, waar [ manuscripten ](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) in werking worden gesteld om meta-gegevens te halen en diverse vertoningen voor [!DNL Experience Manager Assets] te produceren. De proxyworker maakt de communicatie in twee richtingen mogelijk tussen de [!DNL InDesign Server] en de [!DNL Experience Manager] -instanties in een cloudconfiguratie.

>[!NOTE]
>
>[!DNL Adobe InDesign] wordt aangeboden als twee aparte aanbiedingen. [ Adobe InDesign ](https://www.adobe.com/products/indesign.html) Desktop app die wordt gebruikt om paginalay-outs voor druk en digitale distributie te ontwerpen. [ Adobe InDesign Server ](https://www.adobe.com/products/indesignserver.html) laat u toe programmatically om geautomatiseerde documenten tot stand te brengen die op wat u met [!DNL InDesign] hebt gecreeerd worden gebaseerd. Het werkt als dienst die een interface aan zijn [ ExtendScript ](https://www.adobe.com/devnet/indesign/documentation.html#idscripting) motor aanbieden.De manuscripten worden geschreven in [!DNL ExtendScript], die aan [!DNL JavaScript] gelijkaardig is. Voor informatie over [!DNL InDesign] manuscripten zie [ https://www.adobe.com/devnet/indesign/documentation.html#idscripting ](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).

## Hoe de extractie werkt {#how-the-extraction-works}

[!DNL Adobe InDesign Server] kan worden geïntegreerd met [!DNL Experience Manager Assets] , zodat INDD-bestanden die met [!DNL InDesign] zijn gemaakt, kunnen worden geüpload, vertoningen kunnen worden gegenereerd, alle media kunnen worden uitgepakt (bijvoorbeeld video) en kunnen worden opgeslagen als elementen:

>[!NOTE]
>
>In eerdere versies van [!DNL Experience Manager] konden XMP en de miniatuur worden opgehaald. Alle media kunnen nu worden opgepakt.

1. Upload het INDD-bestand naar [!DNL Experience Manager Assets] .
1. Een framework verzendt opdrachtscripts naar de [!DNL InDesign Server] via SOAP (Simple Object Access Protocol).
Met dit opdrachtscript wordt:

   * Haal het INDD-bestand op.
   * Opdrachten [!DNL InDesign Server] uitvoeren:

      * De structuur, de tekst en alle mediabestanden worden geëxtraheerd.
      * PDF- en JPG-uitvoeringen worden gegenereerd.
      * HTML- en IDML-uitvoeringen worden gegenereerd.

   * Post de resulterende bestanden terug naar [!DNL Experience Manager Assets] .

   >[!NOTE]
   >
   >IDML is een op XML gebaseerde indeling die alle inhoud van het [!DNL InDesign] -bestand rendert. Het wordt opgeslagen als samengeperst pakket gebruikend [ ZIP ](https://www.techterms.com/definition/zip) compressie. Voor meer informatie, zie {de Formaten INX en IDML van de Uitwisseling van het InDesign 0} ](https://www.peachpit.com/articles/article.aspx?p=1381880&amp;seqNum=8).[

   >[!CAUTION]
   >
   >Als [!DNL InDesign Server] niet geïnstalleerd of niet gevormd is, kunt u een INDD- dossier in [!DNL Experience Manager] nog uploaden. De gegenereerde uitvoeringen zijn echter beperkt tot PNG en JPEG. U kunt geen HTML-, idml- of paginauitvoeringen genereren.

1. Na de extractie en uitvoering:

   * De structuur wordt gerepliceerd naar een `cq:Page` (type vertoning).
   * De geëxtraheerde tekst en bestanden worden opgeslagen in [!DNL Experience Manager Assets] .
   * Alle uitvoeringen worden opgeslagen in [!DNL Experience Manager Assets] in het element zelf.

## De [!DNL InDesign Server] integreren met Experience Manager {#integrating-the-indesign-server-with-aem}

Als u [!DNL InDesign Server] wilt integreren voor gebruik met [!DNL Experience Manager Assets] en nadat u de proxy hebt geconfigureerd, moet u:

1. [ installeer het InDesign Server ](#installing-the-indesign-server).
1. Indien noodzakelijk, [ vormen het Werkschema van Experience Manager Assets ](#configuring-the-aem-assets-workflow).
Dit is alleen nodig als de standaardwaarden niet geschikt zijn voor uw instantie.
1. Vorm a [ volmachtsarbeider voor het InDesign Server ](#configuring-the-proxy-worker-for-indesign-server).

### De [!DNL InDesign Server] installeren {#installing-the-indesign-server}

Als u de [!DNL InDesign Server] voor gebruik met [!DNL Experience Manager] wilt installeren en starten:

1. Download en installeer de [!DNL InDesign Server] .

1. Indien nodig, kunt u de configuratie van uw [!DNL InDesign Server] instantie aanpassen.

1. Start de server vanaf de opdrachtregel:

   `<*ids-installation-dir*>/InDesignServer.com -port 8080`

   Hierdoor wordt de server gestart met de SOAP insteekmodule die luistert op poort 8080. Alle logboekberichten en output worden geschreven direct aan het bevelvenster.

   >[!NOTE]
   >
   >Als u de uitvoerberichten in een bestand wilt opslaan, gebruikt u een andere richting, bijvoorbeeld onder Windows:
   >`<ids-installation-dir>/InDesignServer.com -port 8080 > ~/temp/INDD-logfile.txt 2>&1`

### De [!DNL Experience Manager Assets] -workflow configureren {#configuring-the-aem-assets-workflow}

[!DNL Experience Manager Assets] heeft een vooraf geconfigureerde workflow **[!UICONTROL DAM Update Asset]** met specifieke verschillende processtappen voor [!DNL InDesign] :

* [Media extraheren](#media-extraction)
* [Pagina uitnemen](#page-extraction)

Dit werkschema is opstelling met standaardwaarden die voor uw opstelling op de diverse auteursinstanties kunnen worden aangepast (dit is een standaardwerkschema, zodat is de verdere informatie beschikbaar onder [ het Uitgeven van een Werkschema ](/help/sites-developing/workflows-models.md#configuring-a-workflow-step)). Als u de standaardwaarden (met inbegrip van de SOAP haven) gebruikt, dan is geen configuratie nodig.

Na het uploaden van [!DNL InDesign] bestanden naar [!DNL Experience Manager Assets] (volgens een van de gebruikelijke methoden) wordt de workflow geactiveerd om het element te verwerken en de verschillende uitvoeringen voor te bereiden. Test uw configuratie door een INDD-bestand te uploaden naar [!DNL Experience Manager Assets] om te bevestigen dat de verschillende uitvoeringen die door IDS zijn gemaakt, worden weergegeven onder `<*your_asset*>.indd/Renditions`

#### Media-extractie {#media-extraction}

Deze stap bepaalt de extractie van media uit het INDD-bestand.

U kunt het tabblad **[!UICONTROL Arguments]** van de stap **[!UICONTROL Media Extraction]** bewerken om het item aan te passen.

![ de extractieargumenten van Media en manuscriptwegen ](assets/media_extraction_arguments_scripts.png)

Argumenten voor het uitnemen van media en scriptpaden

* **de bibliotheek van ExtendScript**: Dit is een eenvoudige http get/post methodebibliotheek, die door de andere manuscripten wordt vereist.

* **breidt Manuscripten** uit: U kunt verschillende manuscriptcombinaties hier specificeren. Als u uw eigen scripts wilt uitvoeren op de [!DNL InDesign Server] , slaat u de scripts op `/apps/settings/dam/indesign/scripts` op.

<!-- TBD: Hiding this link since ADC is not available anymore. 
For information about [!DNL Adobe InDesign] scripts, see [InDesign developer documentation](https://www.adobe.com/devnet/indesign/documentation.html#idscripting).
-->

>[!CAUTION]
>
>Wijzig de ExtendScript-bibliotheek niet. Deze bibliotheek biedt de HTTP-functionaliteit die nodig is voor communicatie met Sling. Met deze instelling wordt opgegeven welke bibliotheek naar de [!DNL InDesign Server] moet worden verzonden voor gebruik daar.

Het script `ThumbnailExport.jsx` dat wordt uitgevoerd door de workflowstap Media Extraction, genereert een miniatuuruitvoering in JPG indeling. Deze vertoning wordt gebruikt door de werkstroomstap Miniaturen verwerken om de statische uitvoeringen te genereren die door [!DNL Experience Manager] worden vereist.

U kunt de workflowstap Miniaturen verwerken zodanig configureren dat statische uitvoeringen van verschillende grootten worden gegenereerd. Zorg ervoor dat u de standaardwaarden niet verwijdert, omdat deze vereist zijn voor de interface van [!DNL Experience Manager Assets] . Tot slot verwijdert de werkstroomstap Voorvertoning van afbeelding verwijderen de uitvoering van JPG miniatuur, omdat deze niet langer nodig is.

#### Pagina uitnemen {#page-extraction}

Hiermee maakt u een [!DNL Experience Manager] -pagina van de geëxtraheerde elementen. Een extractiemanager wordt gebruikt om gegevens uit een vertoning (momenteel HTML of IDML) te halen. Deze gegevens worden vervolgens gebruikt om een pagina te maken met de PageBuilder.

Als u aanpassingen wilt maken, kunt u het tabblad **[!UICONTROL Arguments]** van de stap **[!UICONTROL Page Extraction]** bewerken.

![ chlimage_1-96 ](assets/chlimage_1-289.png)

* **Handler van de Uitwinning van de Pagina**: Van popup lijst, selecteer de manager die u wilt gebruiken. Een extractiemanager werkt op een specifieke uitvoering, die wordt gekozen door een verwante `RenditionPicker` (zie de `ExtractionHandler` API). In een standaardinstallatie van [!DNL Experience Manager] is het volgende beschikbaar:
   * IDML Handle voor Extractie van de Uitvoer: werkt op de `IDML` vertoning die in de stap MediaExtract wordt geproduceerd.

* **Naam van de Pagina**: Specificeer de naam u aan de resulterende pagina wilt toegewezen. Als deze optie leeg blijft, is de naam &quot;page&quot; (of een derivaat als &quot;page&quot; al bestaat).

* **Titel van de Pagina**: Specificeer de titel u aan de resulterende pagina wilt hebben toegewezen.

* **Weg van de Weg van de Wortel van de Pagina**: De weg aan de wortelplaats van de resulterende pagina. Indien leeg gelaten, wordt het knooppunt gebruikt dat de uitvoeringen van het element bevat.

* **Malplaatje van de Pagina**: Het malplaatje te gebruiken wanneer het produceren van de resulterende pagina.

* **Ontwerp van de Pagina**: Het paginaontwerp dat moet worden gebruikt wanneer het produceren van de resulterende pagina.

### De proxy-worker voor [!DNL InDesign Server] configureren {#configuring-the-proxy-worker-for-indesign-server}

>[!NOTE]
>
>De worker bevindt zich op de proxyinstantie.

1. Vouw **[!UICONTROL Cloud Services Configurations]** in het linkerdeelvenster van de gereedschapsconsole uit. Vouw vervolgens **[!UICONTROL Cloud Proxy Configuration]** uit.

1. Dubbelklik op de **[!UICONTROL IDS worker]** om de configuratie te openen.

1. Klik op **[!UICONTROL Edit]** om het configuratiedialoogvenster te openen en de vereiste instellingen te definiëren:

   ![ proxy_idsworkerconfig ](assets/proxy_idsworkerconfig.png)

   * **Pool IDS**
Het (de) SOAP eindpunt(en) die moeten worden gebruikt voor communicatie met de [!DNL InDesign Server] . U kunt items toevoegen, verwijderen en bestellen.

1. Klik op OK om op te slaan.

### vorm de Verbinding van CQ van de Dag uiterlijk {#configuring-day-cq-link-externalizer}

Als de [!DNL InDesign Server] en [!DNL Experience Manager] zich op verschillende hosts bevinden of als een van deze toepassingen niet op standaardpoorten werkt, configureert u [!UICONTROL Day CQ Link Externalizer] om de hostnaam, poort en inhoudsweg voor [!DNL InDesign Server] in te stellen.

1. Open de webconsole op `https://[aem_server]:[port]/system/console/configMgr` .
1. Zoek de configuratie **[!UICONTROL Day CQ Link Externalizer]** . Klik op **[!UICONTROL Edit]** om te openen.
1. Met de instellingen voor Extern koppelen kunt u absolute URL&#39;s maken voor de [!DNL Experience Manager] -implementatie en voor de [!DNL InDesign Server] -toepassing. Gebruik het veld **[!UICONTROL Domains]** om de hostnaam voor de [!DNL Adobe InDesign Server] op te geven. Klik **sparen**.

   Gebruik `localhost` in absolute URL&#39;s als hostnaam voor uw lokale (auteur)instantie en hostnaam of IP-adres voor de publicatie-instantie, zoals in de volgende afbeelding wordt getoond.

   ![ Verbinding externalizer die ](assets/link-externalizer-config.png) plaatst

### Parallelle taakverwerking inschakelen voor [!DNL InDesign Server] {#enabling-parallel-job-processing-for-indesign-server}

U kunt nu parallelle taakverwerking inschakelen voor IDS. Bepaal het maximumaantal parallelle taken (`x`) dat een [!DNL InDesign Server] kan verwerken:

* Op één multiprocessorcomputer is het maximumaantal parallelle taken (`x`) dat een [!DNL InDesign Server] kan verwerken één minder dan het aantal processors met IDS.
* Wanneer u IDS op veelvoudige machines in werking stelt moet u het totale aantal beschikbare bewerkers (dat wil zeggen op alle machines) tellen dan het totale aantal machines aftrekken.

Om het aantal parallelle banen te vormen IDS:

1. Open het tabblad **[!UICONTROL Configurations]** van de Felix-console, bijvoorbeeld: `https://[aem_server]:[port]/system/console/configMgr` .

1. Selecteer de verwerkingswachtrij van IDS onder `Apache Sling Job Queue Configuration` .

1. Instellen:

   * **Type** - `Parallel`
   * **Maximum Parallelle Banen** - `<*x*>` (zoals hierboven berekend)

1. Sla deze wijzigingen op.
1. Schakel het selectievakje `enable.multisession.name` in onder `com.day.cq.dam.ids.impl.IDSJobProcessor.name` configuratie als u ondersteuning voor meerdere sessies voor Adobe CS6 en hoger wilt inschakelen.
1. Creeer a [ pool van `x` arbeiders IDS door SOAP eindpunten aan de configuratie van de Arbeider IDS ](#configuring-the-proxy-worker-for-indesign-server) toe te voegen.

   Als er meerdere computers met [!DNL InDesign Server] werken, voegt u SOAP eindpunten (aantal processors per computer -1) toe voor elke computer.

<!-- 
TBD: Make updates to configurations for allow and block list after product updates are done.
-->

>[!NOTE]
>
>Wanneer u werkt met een groep workers, kunt u de lijst van gewezen personen van IDS-workers inschakelen.
>
>Hiervoor schakelt u het selectievakje **[!UICONTROL enable.retry.name]** in onder de `com.day.cq.dam.ids.impl.IDSJobProcessor.name` -configuratie, waarmee IDS-taakophaalbewerkingen kunnen worden uitgevoerd.
>
>Stel onder de `com.day.cq.dam.ids.impl.IDSPoolImpl.name` -configuratie ook een positieve waarde in voor de `max.errors.to.blacklist` -parameter die het aantal taakophaalbewerkingen bepaalt voordat een id uit de lijst met taakhandlers wordt verwijderd.
>
>Door gebrek, na configureerbare (`retry.interval.to.whitelist.name`) tijd in notulen wordt de worker IDS opnieuw bevestigd. Als de worker online wordt gevonden, wordt deze uit de lijst van gewezen personen verwijderd.

## Ondersteuning inschakelen voor [!DNL InDesign Server] 10.0 of hoger {#enabling-support-for-indesign-server-or-later}

Voer voor [!DNL InDesign Server] 10.0 of hoger de volgende stappen uit om ondersteuning voor meerdere sessies in te schakelen.

1. Open Configuration Manager via uw [!DNL Experience Manager Assets] -instantie `https://[aem_server]:[port]/system/console/configMgr` .
1. Bewerk de configuratie `com.day.cq.dam.ids.impl.IDSJobProcessor.name`.
1. Selecteer de optie **[!UICONTROL ids.cc.enable]** en klik op **[!UICONTROL Save]** .

>[!NOTE]
>
>Voor [!DNL InDesign Server] integratie met [!DNL Experience Manager Assets] gebruikt u een multicore-processor omdat de functie voor sessieondersteuning die nodig is voor de integratie niet wordt ondersteund op single core-systemen.

## [!DNL Experience Manager] gebruikersgegevens configureren {#configure-aem-credentials}

U kunt de standaardbeheerdersreferenties (gebruikersnaam en wachtwoord) wijzigen om [!DNL InDesign Server] vanuit uw [!DNL Experience Manager] -implementatie te openen zonder de integratie met [!DNL InDesign Server] te verbreken.

1. Ga naar `/etc/cloudservices/proxy.html` .
1. Geef in het dialoogvenster de nieuwe gebruikersnaam en het nieuwe wachtwoord op.
1. Sla de referenties op.

>[!MORELIKETHIS]
>
>* [ Ongeveer Adobe InDesign Server ](https://www.adobe.com/products/indesignserver/faq.html)
