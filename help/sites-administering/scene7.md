---
title: Adobe Experience Manager integreren met Dynamic Media Classic
description: Leer hoe u Adobe Experience Manager kunt integreren met Dynamic Media Classic.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: f244cfb5-5550-4f20-92f0-bb296e2bf76e
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '5236'
ht-degree: 0%

---

# Adobe Experience Manager integreren met Dynamic Media Classic {#integrating-with-dynamic-media-classic-scene}

Adobe Dynamic Media Classic is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media-elementen aan Web, mobiel, e-mail en displays en drukwerk via internet.

Als u Dynamic Media Classic wilt gebruiken, moet u de cloudconfiguratie zodanig configureren dat Dynamic Media Classic en Adobe Experience Manager Assets met elkaar kunnen communiceren. In dit document wordt beschreven hoe u Experience Manager en Dynamic Media Classic kunt configureren.

Ga voor informatie over het gebruik van alle Dynamic Media Classic-componenten op een pagina en het werken met video naar [Dynamic Media Classic gebruiken](../assets/scene7.md).

>[!NOTE]
>
>* Dynamic Media Classic&#39;s DHTML-viewerplatform bereikte officieel het einde van de levensduur op 31 januari 2014. Zie de klasse [Veelgestelde vragen over eindversie van DHTML-viewer](../sites-administering/dhtml-viewer-endoflifefaqs.md).
>* Voordat u Dynamic Media Classic configureert voor gebruik met Experience Manager, raadpleegt u [Aanbevolen procedures](#best-practices-for-integrating-scene-with-aem) voor de integratie van Dynamic Media Classic met Experience Manager.
>* Als u Dynamic Media Classic met een configuratie van de douanevolmacht gebruikt, moet u beide de volmachtsconfiguraties van de Cliënt van HTTP vormen omdat sommige functionaliteiten van Experience Manager 3.x APIs gebruiken en anderen 4.x APIs gebruiken. 3.x wordt geconfigureerd met [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) en 4.x wordt geconfigureerd met [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator).
>

## Integratie van Experience Manager/Dynamic Media Classic versus Dynamic Media {#aem-scene-integration-versus-dynamic-media}

Gebruikers van Experience Managers kunnen kiezen uit twee oplossingen om met Dynamic Media te werken. U kunt een van de volgende opties gebruiken:

* Integreer uw exemplaar van Experience Manager met Dynamic Media Classic.
* Gebruik Dynamic Media die is geïntegreerd in de Experience Manager.

Gebruik de volgende criteria om te bepalen welke oplossing moet worden gekozen:

* Ben je **bestaand** De klant van Dynamic Media Classic van wie activa in Dynamic Media Classic voor publicatie en levering verblijven, maar u wilt die activa met de creatie van Plaatsen (WCM), of Experience Manager Assets, of allebei integreren? Indien dit het geval is, gebruikt u de [Experience Manager/Dynamic Media Classic point-to-point integratie](#aem-scene-point-to-point-integration) beschreven in dit document.

* Als u een **new** De klant van de Experience Manager die rijke media leveringsbehoeften heeft, selecteert [Dynamic Media, optie](#aem-dynamic-media). Deze optie heeft de meeste zin als u geen bestaande S7-account hebt en veel middelen die in dat systeem zijn opgeslagen.

* Gebruik in bepaalde gevallen beide oplossingen. De [scenario voor dubbel gebruik](/help/sites-administering/scene7.md#dual-use-scenario) beschrijft dat scenario.

### Experience Manager/Dynamic Media Classic point-to-point integratie {#aem-scene-point-to-point-integration}

Wanneer u met middelen in deze oplossing werkt, doet u één van het volgende:

* Upload elementen rechtstreeks naar Dynamic Media Classic en open ze vervolgens via de **Dynamic Media Classic** inhoudbrowser voor het ontwerpen van pagina&#39;s of
* Uploaden naar Experience Manager Assets en vervolgens automatisch publiceren naar Dynamic Media Classic inschakelen; toegang tot via **Activa** inhoudbrowser voor paginaontwerp

De componenten die u voor deze integratie gebruikt, vindt u in het dialoogvenster **Dynamic Media Classic** componentgebied in [Ontwerpmodus](/help/sites-authoring/author-environment-tools.md#page-modes).

### Experience Manager Dynamic Media {#aem-dynamic-media}

Experience Manager Dynamic Media is de hereniging van Dynamic Media Classic-functies die direct binnen het Experience Manager platform plaatsvindt.

Wanneer u met middelen in deze oplossing werkt, volgt u deze workflow:

1. Upload afzonderlijke afbeeldings- en video-elementen rechtstreeks naar de Experience Manager.
1. Video&#39;s rechtstreeks in Experience Manager coderen.
1. Stel op afbeeldingen gebaseerde sets rechtstreeks samen binnen de Experience Manager.
1. Voeg indien van toepassing interactiviteit toe aan afbeeldingen of video&#39;s.

De componenten die u voor Dynamic Media gebruikt, vindt u in het dialoogvenster **[!UICONTROL Dynamic Media]** componentgebied in [Ontwerpmodus](/help/sites-authoring/author-environment-tools.md#page-modes). Hieronder vallen onder meer:

* **[!UICONTROL Dynamic Media]** - de **[!UICONTROL Dynamic Media]** is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

* **[!UICONTROL Interactive Media]** - de **[!UICONTROL Interactive Media]** is bedoeld voor elementen zoals carrouselbanners, interactieve afbeeldingen en interactieve video. Dergelijke elementen bevatten interactiviteit, zoals hotspots of afbeeldingen met hyperlinks. Deze component is slim. Afhankelijk van of u een afbeelding of video toevoegt, hebt u verschillende opties. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

### Scenario voor tweeërlei gebruik {#dual-use-scenario}

U kunt de integratiefuncties van Experience Manager zowel voor Dynamic Media als voor Dynamic Media Classic tegelijk gebruiken. In de volgende tabel met gebruiksgevallen wordt beschreven wanneer u bepaalde gebieden in- en uitschakelt.

Dynamic Media en Dynamic Media Classic tegelijk gebruiken:

1. Configureren [Dynamic Media Classic](#creating-a-cloud-configuration-for-scene) in Cloud Servicen.
1. Volg de specifieke instructies voor uw gebruiksgeval op:

   <table>
    <tbody>
    <tr>
    <td> </td>
    <td> </td>
    <td><strong>Dynamic Media</strong></td>
    <td> </td>
    <td><strong>Dynamic Media Classic-integratie</strong></td>
    <td> </td>
    </tr>
    <tr>
    <td><strong>Als u ...</strong></td>
    <td><strong>Hoofdlettergebruik</strong></td>
    <td><strong>Afbeeldingen/video</strong></td>
    <td><strong>Dynamic Media-component</strong></td>
    <td><strong>S7 Inhoudsbrowser en -componenten</strong></td>
    <td><strong>Automatisch uploaden van middelen naar S7</strong></td>
    </tr>
    <tr>
    <td>Nieuw bij sites en Dynamic Media</td>
    <td>Elementen uploaden naar Experience Manager en Experience Manager Dynamic Media-component gebruiken om elementen op sitepagina's te maken</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Aan</a></td>
    <td>Uit</td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>In de detailhandel, en nieuw aan Plaatsen en Dynamic Media</td>
    <td>Niet-productmiddelen uploaden naar Experience Manager voor beheer en levering. Upload PRODUCT-middelen naar Dynamic Media Classic en gebruik Dynamic Media Classic-inhoudbrowser in Experience Manager en onderdeel om productdetailpagina's op sites te maken.</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Aan</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Nieuw bij Middelen en Dynamic Media</td>
    <td>Elementen uploaden naar Experience Manager Assets en gepubliceerde URL-/insluitcode van Dynamic Media gebruiken</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td>Uit</td>
    <td>Uit</td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Nieuw bij Dynamic Media en Sjabloon</td>
    <td>Gebruik Dynamic Media voor beeldbewerking en video. Auteur afbeeldingssjablonen in Dynamic Media Classic en gebruik Dynamic Media Classic content finder om sjablonen op te nemen in sitepagina's.</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Aan</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Een bestaande Dynamic Media Classic-klant en is nieuw voor Sites</td>
    <td>Elementen uploaden naar Dynamic Media Classic en Experience Manager Dynamic Media Classic-inhoudsbrowser gebruiken om elementen op sitepagina's te zoeken en te ontwerpen</td>
    <td>Uit</td>
    <td>Uit</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Een bestaande Dynamic Media Classic-klant en is nieuw voor Sites en Assets</td>
    <td>Elementen uploaden naar DAM en automatisch publiceren naar Dynamic Media Classic voor levering. Gebruik de Experience Manager Dynamic Media Classic-inhoudbrowser om elementen op sitepagina's te zoeken en te ontwerpen.</td>
    <td>Uit</td>
    <td>Uit</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td><p><a href="#configuringautouploadingfromaemassets">Aan</a></p> <p>(Zie stap 4)</p> </td>
    </tr>
    <tr>
    <td>Bestaande Dynamic Media Classic-klant en nieuw op Middelen</td>
    <td><p>Elementen uploaden naar Experience Manager en Dynamic Media gebruiken om uitvoeringen te genereren voor downloaden/delen. Publiceer automatisch Experience Manager-elementen naar Dynamic Media Classic voor levering.</p> <p><strong>Belangrijk:</strong> Gelijktijdige verwerking en uitvoeringen die worden gegenereerd in Experience Manager, worden niet gesynchroniseerd met Dynamic Media Classic</p> </td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td>Uit</td>
    <td>Uit</td>
    <td><p><a href="#configuringautouploadingfromaemassets">Aan</a></p> <p>(Zie stap 4)</p> </td>
    </tr>
    </tbody>
    </table>

1. (Optioneel; zie tabel met gebruiksscenario&#39;s) - Stel de [Dynamic Media-cloudconfiguratie](/help/assets/config-dynamic.md) en [de Dynamic Media-server inschakelen](/help/assets/config-dynamic.md).
1. (Optioneel; zie tabel met hoofdletters/kleine letters) - Als u Automatisch uploaden van middelen naar Dynamic Media Classic wilt inschakelen, moet u het volgende toevoegen:

   1. Automatisch uploaden naar Dynamic Media Classic instellen.
   1. Voeg de **Dynamic Media Classic-upload** stap na alle Dynamic Media-workflowstappen *aan het einde van* **Dam Update-element** workflow ( `https://<server>:<host>/cf#/etc/workflow/models/dam/update_asset.html)`
   1. (Optioneel) Beperk het uploaden van Dynamic Media Classic-elementen op basis van het MIME-type in [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl). Elementen MIME-typen die niet in deze lijst voorkomen, worden niet geüpload naar de Dynamic Media Classic-server.
   1. (Optioneel) Stel video in Dynamic Media Classic-configuratie in. U kunt videocodering voor zowel Dynamic Media als Dynamic Media Classic tegelijk inschakelen. Dynamische uitvoeringen worden gebruikt voor voorvertoning en lokaal afspelen in Experience Manager-instantie, terwijl Dynamic Media Classic-video-uitvoeringen worden gegenereerd en opgeslagen op Dynamic Media Classic-servers. Wanneer u videocoderingsservices instelt voor zowel Dynamic Media als Dynamic Media Classic, past u een [videoverwerkingsprofiel](/help/assets/video-profiles.md) naar de map met Dynamic Media Classic-middelen.
   1. (Optioneel) [Beveiligde voorvertoning configureren in Dynamic Media Classic](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene).

#### Beperkingen {#limitations}

Als u zowel Dynamic Media Classic als Dynamic Media hebt ingeschakeld, gelden de volgende beperkingen:

* Het handmatig uploaden naar Dynamic Media Classic door een element te selecteren en naar een Dynamic Media Classic-component op een pagina met Experience Managers te slepen, werkt niet.
* Hoewel de gesynchroniseerde elementen van Experience Manager-Dynamic Media Classic automatisch worden bijgewerkt naar Dynamic Media Classic wanneer het element wordt bewerkt in Elementen, wordt een terugdraaiactie niet geactiveerd om een nieuwe upload te starten. Als zodanig krijgt Dynamic Media Classic niet onmiddellijk na een terugdraaiing de nieuwste versie. Als tussenoplossing kunt u het terugdraaien opnieuw uitvoeren.
* Is het nodig dat u Dynamic Media gebruikt voor één gebruiksgeval en Dynamic Media Classic-integratie voor een andere, zodat Dynamic Media-middelen niet in wisselwerking staan met het Dynamic Media Classic-systeem? Als dat het geval is, moet u de Dynamic Media Classic-configuratie dan niet toepassen op de Dynamic Media-map. En pas de Dynamic Media-configuratie (verwerkingsprofiel) niet toe op een Dynamic Media Classic-map.

## Aanbevolen procedures voor de integratie van Dynamic Media Classic met Experience Manager {#best-practices-for-integrating-scene-with-aem}

Bij de integratie van Dynamic Media Classic met Experience Manager zijn er enkele belangrijke beste praktijken die in acht moeten worden genomen op de volgende gebieden:

* Uw integratie testen
* Voor bepaalde scenario&#39;s wordt het uploaden van middelen rechtstreeks vanuit Dynamic Media Classic aanbevolen

Zie [bekende beperkingen](#known-limitations-and-design-implications).

### Test uw integratie {#test-driving-your-integration}

De Adobe adviseert dat u test-aandrijving uw integratie door uw wortelomslag te hebben die aan subfolder slechts eerder dan een volledig bedrijf richt.

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan lang duren voordat deze in Experience Manager worden weergegeven. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat (de hoofdmap bevat bijvoorbeeld vaak te veel elementen en kan uw systeem vastlopen).

### Elementen uploaden van Experience Manager Assets naar Dynamic Media Classic {#uploading-assets-from-aem-assets-versus-from-scene}

U kunt elementen uploaden met behulp van de functionaliteit voor middelenbeheer (digital asset management) of door Dynamic Media Classic rechtstreeks in Experience Manager te openen via de Dynamic Media Classic-inhoudbrowser. Welke optie u kiest, is afhankelijk van de volgende factoren:

* Dynamic Media Classic-elementtypen die Experience Manager Assets nog niet ondersteunt, moeten rechtstreeks vanuit Dynamic Media Classic via de Dynamic Media Classic-inhoudbrowser aan een website van een Experience Manager worden toegevoegd. Bijvoorbeeld afbeeldingssjablonen.
* Voor de typen elementen die zowel door Experience Manager Assets als door Dynamic Media Classic worden ondersteund, is het van het volgende afhankelijk hoe u deze kunt uploaden:

   * Waar de activa zich vandaag bevinden, EN
   * Hoe belangrijk is het beheer ervan in een gemeenschappelijke gegevensopslagplaats?

Veronderstel dat de activa reeds in Dynamic Media Classic zijn en die in een gemeenschappelijke bewaarplaats beheren is niet belangrijk. Als dat het geval is, is het exporteren van de activa naar Experience Manager Assets om deze alleen weer te synchroniseren naar Dynamic Media Classic voor levering een overbodige retourvlucht. Adobe raadt u aan uw middelen in één opslagplaats te bewaren en ze alleen voor levering te synchroniseren met Dynamic Media Classic.

## Dynamic Media Classic-integratie configureren {#configuring-scene-integration}

U kunt Experience Manager configureren om elementen te uploaden naar Dynamic Media Classic. Middelen uit een CQ-doelmap kunnen (automatisch of handmatig) van Experience Manager naar een Dynamic Media Classic-bedrijfsaccount worden geüpload.

>[!NOTE]
>
>Adobe raadt u aan alleen de toegewezen doelmap te gebruiken voor het importeren van Dynamic Media Classic-elementen. Digitale middelen die zich buiten de doelmap bevinden, kunnen alleen worden gebruikt in Dynamic Media Classic-componenten op pagina&#39;s waarop de Dynamic Media Classic-configuratie is ingeschakeld. Bovendien worden ze in een map op aanvraag in Dynamic Media Classic geplaatst. De map op aanvraag wordt niet gesynchroniseerd met Experience Manager (maar elementen zijn te vinden in de Dynamic Media Classic-inhoudbrowser).

**Dynamic Media Classic configureren voor integratie met Experience Manager:**

1. [Een cloudconfiguratie definiëren](#creating-a-cloud-configuration-for-scene) - Definieert de toewijzing tussen een Dynamic Media Classic-map en een Assets-map. Voltooi deze stap, zelfs als u synchronisatie in één richting (Experience Manager Assets naar Dynamic Media Classic) wilt uitvoeren.
1. [De optie **Adobe CQ s7dam Dam Listener**](#enabling-the-adobe-cq-scene-dam-listener) - Gereed in het [!UICONTROL OSGi] console.
1. Als u wilt dat Experience Manager Assets automatisch naar Dynamic Media Classic uploadt, moet u die optie inschakelen en Dynamic Media Classic toevoegen aan de [!UICONTROL DAM Update Asset] workflow. U kunt ook handmatig elementen uploaden.
1. Dynamic Media Classic-componenten toevoegen aan het hulpwerkstation. Met deze functionaliteit kunnen gebruikers Dynamic Media Classic-componenten gebruiken op hun pagina&#39;s met Experience Managers.
1. [De configuratie toewijzen aan de pagina in Experience Manager](#enabling-scene-for-wcm) - Deze stap is vereist om videovoorinstellingen weer te geven die u in Dynamic Media Classic hebt gemaakt. Dit is ook vereist als u een middel van buiten de CQ-doelmap naar Dynamic Media Classic moet publiceren.

In deze sectie wordt beschreven hoe u al deze stappen uitvoert en worden belangrijke beperkingen weergegeven.

### Hoe synchronisatie tussen Dynamic Media Classic en Experience Manager Assets werkt {#how-synchronization-between-scene-and-aem-assets-works}

Bij het instellen van Experience Manager Assets- en Dynamic Media Classic-synchronisatie is het belangrijk dat u het volgende begrijpt:

#### Uploaden naar Dynamic Media Classic vanuit Experience Manager Assets {#uploading-to-scene-from-aem-assets}

* Er is een toegewezen synchronisatiemap in Experience Manager voor Dynamic Media Classic-uploads.
* Uploads naar Dynamic Media Classic kunnen worden geautomatiseerd als de digitale middelen in de aangewezen synchronisatiemap worden geplaatst.
* De map- en submapstructuur in Experience Manager wordt gerepliceerd in Dynamic Media Classic.

>[!NOTE]
>
>Experience Manager sluit alle metagegevens in zoals XMP voordat deze naar Dynamic Media Classic worden geüpload. Alle eigenschappen op het metagegevensknooppunt zijn dus in Dynamic Media Classic als XMP beschikbaar.

#### Bekende beperkingen en gevolgen voor het ontwerp {#known-limitations-and-design-implications}

Bij de synchronisatie tussen Experience Manager Assets en Dynamic Media Classic zijn er momenteel de volgende beperkingen/ontwerpimplicaties:

<table>
 <tbody>
  <tr>
   <td><strong>Beperking/gevolgen van ontwerp</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Eén toegewezen synchronisatiemap (doel)</td>
   <td>U kunt per bedrijf slechts één toegewezen map in de Experience Manager voor Dynamic Media Classic-uploads gebruiken. U kunt meerdere configuraties maken als u toegang moet hebben tot meer dan één bedrijfsaccount in Dynamic Media Classic.</td>
  </tr>
  <tr>
   <td>Mapstructuur</td>
   <td>Als u een gesynchroniseerde map met middelen verwijdert, worden alle externe Dynamic Media Classic-middelen verwijderd, maar blijft de map ongewijzigd.</td>
  </tr>
  <tr>
   <td>Map op aanvraag</td>
   <td>Elementen die zich buiten de doelmap bevinden en die handmatig in WCM naar Dynamic Media Classic worden geüpload, worden automatisch in een aparte map op aanvraag in Dynamic Media Classic geplaatst. U configureert deze map in de cloudconfiguratie in Experience Manager.</td>
  </tr>
  <tr>
   <td>Gemengde media</td>
   <td>Gemengde mediasets worden in de Experience Manager weergegeven, maar niet in de Experience Manager.</td>
  </tr>
  <tr>
   <td>PDF</td>
   <td>Gegenereerde PDF van eCatalogs in Dynamic Media Classic worden geïmporteerd in de CQ-doelmap.</td>
  </tr>
  <tr>
   <td>interface vernieuwen</td>
   <td>Wanneer het synchroniseren tussen Experience Manager en Dynamic Media Classic, ben zeker om het gebruikersinterface te verfrissen om veranderingen te bekijken. </td>
  </tr>
  <tr>
   <td>Videominiaturen</td>
   <td>Als u een video naar Experience Manager Assets uploadt voor codering via Dynamic Media Classic, kan het enige tijd duren voordat de videominiaturen en gecodeerde video's beschikbaar zijn in Experience Manager Assets, afhankelijk van de verwerkingstijd van de video.</td>
  </tr>
  <tr>
   <td>Doelsubmappen</td>
   <td><p>Als u submappen in de doelmap gebruikt, moet u ervoor zorgen dat u voor elk element unieke namen gebruikt (ongeacht de locatie). Ook, zorg ervoor u Dynamic Media Classic (in het gebied van de Opstelling) vormt om activa, ongeacht plaats niet te beschrijven.</p> <p>Anders worden elementen met dezelfde naam die naar een Dynamic Media Classic-doelsubmap zijn geüpload, wel geüpload, maar het element met dezelfde naam in de doelmap wordt verwijderd. </p> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media Classic-servers configureren {#configuring-scene-servers}

Als u Experience Manager achter een volmacht in werking stelt of speciale firewallmontages hebt, moet u de gastheren van de verschillende gebieden uitdrukkelijk toelaten. Servers worden beheerd in inhoud in `/etc/cloudservices/scene7/endpoints` en kan naar wens worden aangepast. Selecteer een URL en bewerk deze vervolgens om de URL indien nodig te wijzigen. In vorige versies van Experience Manager waren deze waarden hard-gecodeerd.

Als u naar `/etc/cloudservices/scene7/endpoints.html`U ziet de weergegeven servers (en kunt deze bewerken door op de URL te tikken):

![chlimage_1-296](assets/chlimage_1-296.png)

### Een cloudconfiguratie voor Dynamic Media Classic maken {#creating-a-cloud-configuration-for-scene}

Een wolkenconfiguratie bepaalt de afbeelding tussen een omslag van Dynamic Media Classic en een omslag van Experience Manager Assets. Deze moet zijn geconfigureerd om Experience Manager Assets met Dynamic Media Classic te synchroniseren. Zie Hoe de Synchronisatie voor meer informatie werkt.

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan lang duren voordat deze in Experience Manager worden weergegeven. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat. De hoofdmap bevat bijvoorbeeld vaak te veel elementen.
>
>Als u de integratie wilt testen en besturen, moet u de hoofdmap alleen verwijzen naar een submap in plaats van naar het hele bedrijf.

>[!NOTE]
>
>U kunt meerdere configuraties hebben: één cloudconfiguratie vertegenwoordigt één gebruiker in een Dynamic Media Classic-bedrijf. Als u andere Dynamic Media Classic-bedrijven of -gebruikers wilt openen, moet u meerdere configuraties maken.

**Een cloudconfiguratie voor Dynamic Media Classic maken:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]** zodat je toegang hebt tot Adobe Dynamic Media Classic.

1. Selecteren **[!UICONTROL Configure now]**.

   ![chlimage_1-297](assets/chlimage_1-297.png)

1. In de **[!UICONTROL Title]** en eventueel in het veld **[!UICONTROL Name]** Voer de juiste gegevens in. Selecteren **[!UICONTROL Create]**.

   >[!NOTE]
   >
   >Als u meer configuraties maakt, **[!UICONTROL parent configuration]** wordt weergegeven.
   >
   >Do **niet** de bovenliggende configuratie wijzigen. Het wijzigen van de bovenliggende configuratie kan de integratie onderbreken.

1. Voer het e-mailadres, het wachtwoord en de regio van uw Dynamic Media Classic-account in en selecteer **[!UICONTROL Connect to Dynamic Media Classic]**. U hebt verbinding met de Dynamic Media Classic-server en het dialoogvenster wordt uitgebreid met meer opties.

1. Voer de **[!UICONTROL Company]** naam en **[!UICONTROL Root Path]**. Dit is de naam van de gepubliceerde server en het pad dat u wilt opgeven. Als u de naam van de gepubliceerde server in Dynamic Media Classic niet kent, gaat u naar **[!UICONTROL Setup > Application Setup]**).

   >[!NOTE]
   >
   >Het Dynamic Media Classic-hoofdpad is het pad waarmee de Experience Manager van de Dynamic Media Classic-map verbinding maakt. U kunt de map verkleinen tot een specifieke map.

   >[!CAUTION]
   >
   >Afhankelijk van de grootte van de Dynamic Media Classic-map kan het importeren van een hoofdmap lang duren. Bovendien zouden de gegevens van Dynamic Media Classic de opslag van de Experience Manager kunnen overschrijden. Controleer of u de juiste map importeert. Door te veel gegevens te importeren, kan uw systeem worden gestopt.

   ![chlimage_1-298](assets/chlimage_1-298.png)

1. Selecteer **[!UICONTROL OK]**. Experience Manager slaat uw configuratie op.

>[!NOTE]
>
>Als u opnieuw verbinding maakt:
>
>* Wanneer u bij het publiceren opnieuw verbinding maakt met Dynamic Media Classic, kunt u het wachtwoord opnieuw instellen bij het publiceren of opnieuw verbinden. Dit werkt niet (geen probleem in de instantie Auteur).
>* Als u waarden wijzigt, zoals uw regio of bedrijfsnaam, moet u opnieuw verbinding maken met Dynamic Media Classic. Als de configuratieopties zijn gewijzigd maar niet opgeslagen, geeft de Experience Manager ten onrechte nog aan dat de configuratie geldig is. Zorg ervoor dat u opnieuw verbinding maakt.
>

### Adobe CQ Dynamic Media Classic Dam Listener inschakelen {#enabling-the-adobe-cq-scene-dam-listener}

Schakel de Adobe CQ Dynamic Media Classic Dam Listener in, die standaard is uitgeschakeld.

**De Adobe CQ Dynamic Media Classic Dam Listener inschakelen:**

1. Selecteer de [!UICONTROL Tools] pictogram, navigeer vervolgens naar **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Navigeer in de webconsole naar **[!UICONTROL Adobe CQ Dynamic Media Classic Dam Listener]** en selecteert u de **[!UICONTROL Enabled]** selectievakje.

   ![chlimage_1-299](assets/chlimage_1-299.png)

1. Selecteren **[!UICONTROL Save]**.

### Aanpasbare time-out toevoegen aan Dynamic Media Classic Upload-workflow {#adding-configurable-timeout-to-scene-upload-workflow}

Wanneer een instantie van de Experience Manager wordt gevormd om videocodering door Dynamic Media Classic te behandelen, door gebrek, is er een 35 minieme onderbreking op om het even welke uploadbaan. U kunt deze instelling configureren om taken voor videocodering die mogelijk langer worden uitgevoerd, aan te passen.

1. Navigeren naar **http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl**.

   ![chlimage_1-300](assets/chlimage_1-300.png)

1. Wijzig het gewenste nummer in het dialoogvenster **[!UICONTROL Active job timeout]** veld. Alle niet-negatieve getallen worden in seconden met de maateenheid geaccepteerd. Standaard is dit aantal ingesteld op 2100.

   >[!NOTE]
   >
   >Tips en trucs: de meeste elementen worden maximaal minuten ingesloten (bijvoorbeeld afbeeldingen). Maar in bepaalde gevallen - grotere video&#39;s bijvoorbeeld - verhoogt u de time-outwaarde tot 7200 seconden (twee uur) om ruimte te maken voor lange verwerkingstijd. Anders wordt deze Dynamic Media Classic-uploadtaak gemarkeerd als **[!UICONTROL UploadFailed]** in de JCR-metagegevens (Java™ Content Repository).

1. Selecteren **[!UICONTROL Save]**.

### Automatisch uploaden vanuit Experience Manager Assets {#autouploading-from-aem-assets}

Vanaf Experience Manager 6.3.2 is Experience Manager Assets zo geconfigureerd dat geüploade digitale elementen naar Dynamic Media Classic worden bijgewerkt als de elementen zich in een CQ-doelmap bevinden.

Wanneer een element aan Experience Manager Assets wordt toegevoegd, wordt het automatisch geüpload en gepubliceerd naar Dynamic Media Classic.

>[!NOTE]
>
>De maximale bestandsgrootte voor automatisch uploaden van Experience Manager Assets naar Dynamic Media Classic is 500 MB.

**To autoupload from Experience Manager Assets:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Onder de rubriek van Dynamic Media, onder Beschikbare Configuraties, selecteer **[!UICONTROL dms7 (Dynamic Media]**).
1. Selecteer de **[!UICONTROL Advanced]** selecteert u de **[!UICONTROL Enable Automatic Upload]** selectievakje en selecteer vervolgens **[!UICONTROL OK]**. Configureer de DAM Asset-workflow om het uploaden naar Dynamic Media Classic op te nemen.

   >[!NOTE]
   >
   >Zie [De status (gepubliceerd/niet gepubliceerd) van naar Dynamic Media Classic geduwde middelen configureren](#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) voor informatie over het ongepubliceerd naar Dynamic Media Classic duwen van activa.

   ![screen_shot_2018-03-15at52501pm](assets/screen_shot_2018-03-15at52501pm.jpg)

1. Ga terug naar de welkomstpagina van de Experience Manager en selecteer **[!UICONTROL Workflows]**. Dubbelklik op de knop **DAM Update-element** zodat deze wordt geopend.
1. Navigeer in de assistent naar de knop **[!UICONTROL Workflow]** en selecteert u **[!UICONTROL Dynamic Media Classic]**. Slepen **[!UICONTROL Dynamic Media Classic]** naar de workflow en selecteer **[!UICONTROL Save]**. Middelen die in de doelmap aan Experience Manager Assets worden toegevoegd, worden automatisch naar Dynamic Media Classic geüpload.

   ![chlimage_1-301](assets/chlimage_1-301.png)

   >[!NOTE]
   >
   >* Wanneer u na het automatiseren elementen toevoegt die niet in de CQ-doelmap staan, worden deze niet naar Dynamic Media Classic geüpload.
   >* Experience Manager sluit alle metagegevens in zoals XMP voordat deze naar Dynamic Media Classic worden geüpload. Alle eigenschappen op het metagegevensknooppunt zijn dus in Dynamic Media Classic als XMP beschikbaar.

### De status (gepubliceerd/niet gepubliceerd) van aan Dynamic Media Classic geduwde middelen configureren {#configuring-the-state-published-unpublished-of-assets-pushed-to-scene}

Als u middelen van Experience Manager Assets naar Dynamic Media Classic duwt, kunt u of hen publiceren automatisch (standaardgedrag) of hen duwen aan Dynamic Media Classic in een niet gepubliceerde staat.

Het is mogelijk dat u elementen niet direct op Dynamic Media Classic wilt publiceren als u ze in een testomgeving wilt testen voordat u live gaat. U kunt Experience Manager met de Veilige omgeving van de Test van Dynamic Media Classic gebruiken om activa van Activa in Dynamic Media Classic in een niet gepubliceerde staat direct te duwen.

Dynamic Media Classic-elementen blijven beschikbaar via een beveiligde voorvertoning. Alleen wanneer de activa binnen de Experience Manager worden gepubliceerd, worden de activa van Dynamic Media Classic ook in productie.

Als u elementen direct wilt publiceren wanneer u ze naar Dynamic Media Classic duwt, hoeft u geen opties te configureren. Deze functionaliteit is het standaardgedrag.

Als u echter niet wilt dat elementen die aan Dynamic Media Classic worden doorgegeven, automatisch worden gepubliceerd, wordt in deze sectie beschreven hoe u Experience Manager en Dynamic Media Classic kunt configureren om deze functionaliteit uit te voeren.

#### Vereisten om elementen naar Dynamic Media Classic te verzenden zonder publicatie {#prerequisites-to-push-assets-to-scene-unpublished}

Voordat u elementen naar Dynamic Media Classic kunt duwen zonder ze te publiceren, moet u het volgende instellen:

1. [Gebruik de Admin Console om een steungeval te creëren](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html). In het geval van ondersteuning kunt u vragen of een beveiligde voorvertoning voor uw Dynamic Media Classic-account is ingeschakeld.
1. [Beveiligde voorvertoning voor uw Dynamic Media Classic-account instellen](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html).

Dit zijn dezelfde stappen die u zou volgen om een veilige testinstallatie in Dynamic Media Classic te maken.

>[!NOTE]
>
>Als uw installatieomgeving een UNIX® 64-bits besturingssysteem is, raadpleegt u [https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html) met betrekking tot andere configuratieopties moet u plaatsen.

#### Bekende beperkingen voor het doorduwen van elementen in niet-gepubliceerde toestand  {#known-limitations-for-pushing-assets-in-unpublished-state}

Houd rekening met de volgende beperkingen als u deze functie gebruikt:

* Er is geen ondersteuning voor versiebeheer.
* Als een element al in Experience Manager is gepubliceerd en er een volgende versie wordt gemaakt, wordt die nieuwe versie onmiddellijk live gepubliceerd voor productie. Publiceren bij activering werkt alleen met de eerste publicatie van een element.

>[!NOTE]
>
>Als u elementen direct wilt publiceren, kunt u het beste de volgende methoden gebruiken: **[!UICONTROL Enable Secure Preview]** instellen op **[!UICONTROL Immediately]** en gebruiken de **[!UICONTROL Enable Automatic Upload]** gebruiken.

### De status van naar Dynamic Media Classic geduwde elementen instellen als niet-gepubliceerd {#setting-the-state-of-assets-pushed-to-scene-as-unpublished}

>[!NOTE]
>
>Als een gebruiker het element in Experience Manager publiceert, wordt het S7-element automatisch geactiveerd voor de productie/het actieve element (het element bevindt zich niet meer in een beveiligde voorvertoning/is niet gepubliceerd).

**De status van aan Dynamic Media Classic geduwde middelen instellen als niet-gepubliceerd:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteren **[!UICONTROL Dynamic Media Classic]**.
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer de **[!UICONTROL Advanced]** tab.
1. In de **[!UICONTROL Enable Secure View]** vervolgkeuzelijst, selecteert u **[!UICONTROL Upon AEM Publish Activation]** om elementen naar Dynamic Media Classic te verzenden zonder te publiceren. (Deze waarde is standaard ingesteld op **[!UICONTROL Immediately]**, waarbij Dynamic Media Classic-activa onmiddellijk worden gepubliceerd.)

   Zie [Dynamic Media Classic-documentatie](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html) voor meer informatie over het testen van bedrijfsmiddelen alvorens deze openbaar te maken.

   ![chlimage_1-302](assets/chlimage_1-302.png)

1. Selecteren **[!UICONTROL OK]**.

Als u Beveiligde voorvertoning inschakelt, worden uw elementen naar de beveiligde voorvertoningsserver geduwd zonder deze te publiceren.

Controleren of **[!UICONTROL Secure Preview]** is ingeschakeld, navigeert u naar een Dynamic Media Classic-component op een pagina in de Experience Manager. Selecteer **[!UICONTROL Edit]**. Het element heeft de beveiligde voorvertoningsserver die in de URL wordt vermeld. Na publicatie in Experience Manager wordt het serverdomein in de bestandsverwijzing bijgewerkt van de voorbeeld-URL naar de productie-URL.

### Dynamic Media Classic inschakelen voor WCM {#enabling-scene-for-wcm}

Dynamic Media Classic inschakelen voor WCM is om twee redenen vereist:

* Hiermee wordt de vervolgkeuzelijst met universele videoprofielen ingeschakeld voor het ontwerpen van pagina&#39;s. Zonder deze lijst **[!UICONTROL Universal Video Preset]** drop-down is leeg en kan niet worden geplaatst.
* Als een digitaal element niet in de doelmap staat, kunt u het element uploaden naar Dynamic Media Classic als u Dynamic Media Classic voor die pagina inschakelt in de pagina-eigenschappen. Vervolgens sleept u het element naar een Dynamic Media Classic-component. Normale overervingsregels zijn van toepassing (dat wil zeggen dat onderliggende pagina&#39;s de configuratie overnemen van de bovenliggende pagina).

Wanneer het toelaten van Dynamic Media Classic voor WCM, zoals met andere configuraties, zijn de overervingsregels van toepassing. U kunt Dynamic Media Classic for WCM inschakelen in de geoptimaliseerde aanraakinterface of in de klassieke gebruikersinterface.

#### Dynamic Media Classic for WCM inschakelen in de gebruikersinterface voor geoptimaliseerde aanrakingen {#enabling-scene-for-wcm-in-the-touch-optimized-user-interface}

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Sites]** en vervolgens de hoofdpagina van uw website (niet taalspecifiek).

1. Selecteer in de werkbalk de optie [!UICONTROL settings] pictogram en selecteer **[!UICONTROL Open Properties]**.

1. Selecteren **[!UICONTROL Cloud Services]** en selecteert u **[!UICONTROL Add Configuration]** en selecteert u **[!UICONTROL Dynamic Media Classic]**.
1. In de **[!UICONTROL Adobe Dynamic Media Classic]** vervolgkeuzelijst, selecteert u de gewenste configuratie en selecteert u **[!UICONTROL OK]**.

   ![chlimage_1-303](assets/chlimage_1-303.png)

   De video stelt van die configuratie van Dynamic Media Classic zijn beschikbaar voor gebruik in Experience Manager met de videocomponent van Dynamic Media Classic op die pagina en kindpagina&#39;s.

#### Dynamic Media Classic for WCM inschakelen in de klassieke gebruikersinterface {#enabling-scene-for-wcm-in-the-classic-user-interface}

1. Selecteer in Experience Manager **[!UICONTROL Websites]** en navigeer naar de hoofdpagina van uw website (niet taalspecifiek).

1. Selecteer in het zijpaneel de optie **[!UICONTROL Page]** pictogram en selecteer **[!UICONTROL Page Properties]**.

1. Selecteren **[!UICONTROL Cloud Services]** > **[!UICONTROL Add services]** > **[!UICONTROL Dynamic Media Classic]**.
1. In de **[!UICONTROL Adobe Dynamic Media Classic]** vervolgkeuzelijst, selecteert u de gewenste configuratie en selecteert u **[!UICONTROL OK]**.

   De video stelt van die configuratie van Dynamic Media Classic zijn beschikbaar voor gebruik in Experience Manager met de videocomponent van Dynamic Media Classic op die pagina en kindpagina&#39;s.

### Een standaardconfiguratie configureren {#configuring-a-default-configuration}

Als u meerdere Dynamic Media Classic-configuraties hebt, kunt u een van deze configuraties als standaard opgeven voor de Dynamic Media Classic-inhoudbrowser.

Er kan slechts één Dynamic Media Classic-configuratie op een bepaald moment als standaard worden gemarkeerd. De standaardconfiguratie is de bedrijfsactiva die door gebrek in Browser van de Inhoud van Dynamic Media Classic tonen.

**Een standaardconfiguratie configureren:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteren **[!UICONTROL Dynamic Media Classic]**.
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer **[!UICONTROL Edit]**.

1. In de **[!UICONTROL General]** selecteert u de **[!UICONTROL Default Configuration]** Schakel dit selectievakje in om het als standaardbedrijf en basispad in te stellen dat in de Dynamic Media Classic-inhoudbrowser wordt weergegeven.

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!NOTE]
   >
   >Als er slechts één configuratie is, selecteert u **[!UICONTROL Default Configuration]** selectievakje heeft geen effect.

### De map Ad hoc configureren {#configuring-the-ad-hoc-folder}

U kunt de map op aanvraag configureren waarnaar elementen in Dynamic Media Classic worden geüpload wanneer het element zich niet in de CQ-doelmap bevindt. Zie Elementen publiceren van buiten de CQ-doelmap.

**De map Ad hoc configureren:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteren **[!UICONTROL Dynamic Media Classic]**.
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer **[!UICONTROL Edit]**.

1. Selecteer de **[!UICONTROL Advanced]** tab. In de **[!UICONTROL Ad-hoc Folder]** veld kunt u de **Ad hoc** map. Standaard is dit de **name_of_the_company/CQ5_adhoc**.

   ![chlimage_1-305](assets/chlimage_1-305.png)

### Universele videovoorinstellingen configureren {#configuring-universal-presets}

Als u universele videovoorinstellingen voor de videocomponent wilt configureren, raadpleegt u [Video](/help/assets/s7-video.md).

## Ondersteuning voor MIME-taakparameters op basis van type inschakelen/Dynamic Media Classic-upload {#enabling-mime-type-based-assets-scene-upload-job-parameter-support}

U kunt configureerbare parameters voor uploadtaken voor Dynamic Media Classic inschakelen die worden geactiveerd door de synchronisatie van Digital Asset Manager/Dynamic Media Classic-middelen.

Specifiek, vormt u het erkende dossierformaat door MIME type in het OSGi (Open het initiatief van de Gateway van de Dienst) gebied van het paneel van de Configuratie van de Console van het Web van de Experience Manager. Vervolgens kunt u de afzonderlijke taakparameters voor uploaden aanpassen die worden gebruikt voor elk MIME-type in de JCR (Java™ Content Repository).

**Op MIME gebaseerde elementen inschakelen:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. In het configuratiescherm van de Adobe Experience Manager-webconsole, op het tabblad **[!UICONTROL OSGi]** menu, selecteert u **[!UICONTROL Configuration]**.
1. Zoek en selecteer onder de kolom Naam **[!UICONTROL Adobe CQ Dynamic Media Classic Asset MIME type Service]** om de configuratie te bewerken.
1. Selecteer in het gebied MIME-typetoewijzing een plusteken (+) om een MIME-type toe te voegen.

   Zie [Ondersteunde MIME-typen](/help/assets/assets-formats.md#supported-mime-types).

1. Typ de nieuwe naam van het MIME-type in het tekstveld.

   U kunt bijvoorbeeld een `<file_extension>=<mime_type>` zoals in `EPS=application/postscript` OF `PSD=image/vnd.adobe.photoshop`.

1. Selecteer in de rechterbenedenhoek van het configuratievenster de optie **[!UICONTROL Save]**.
1. Terugkeren naar Experience Manager en in de linkerspoorstaaf, selecteer **[!UICONTROL CRXDE Lite]**.
1. Navigeer op de pagina CRXDE Lite in het linkerspoor naar `/etc/cloudservices/scene7/<environment>` (vervanging `<environment>` voor de werkelijke naam).
1. Uitbreiden `<environment>` (vervanging `<environment>` voor de eigenlijke naam) `mimeTypes` knooppunt.
1. Selecteer het mimeType dat u zojuist hebt toegevoegd.

   Bijvoorbeeld: `mimeTypes > application_postscript` OF `mimeTypes > image_vnd.adobe.photoshop`.

1. Selecteer rechts van de pagina CRXDE Lite de optie **[!UICONTROL Properties]** tab.
1. Een Dynamic Media Classic-taakparameter voor uploaden opgeven in het dialoogvenster **[!UICONTROL jobParam]** waardeveld.

   Bijvoorbeeld: `psprocess="rasterize"&psresolution=120` .

   Zie de [Adobe Dynamic Media Classic Image Production System API](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-overview.html) voor meer uploadtaakparameters die u kunt gebruiken.

   >[!NOTE]
   >
   >Als u PSD-bestanden uploadt en u wilt deze als sjablonen met laagextracties verwerken, voert u het volgende in het dialoogvenster **[!UICONTROL jobParam]** waardeveld:
   >
   >`process=MaintainLayers&layerNaming=AppendName&createTemplate=true`
   >
   >Zorg ervoor dat het PSD-bestand &#39;lagen&#39; heeft. Als het strikt genomen één afbeelding of een afbeelding met een masker is, wordt de afbeelding verwerkt als een afbeelding omdat er geen lagen zijn om te verwerken.

1. Selecteer in de linkerbovenhoek van de pagina CRXDE Lite de optie **[!UICONTROL Save All]**.

## Problemen met de integratie van Dynamic Media Classic en Experience Managers oplossen {#troubleshooting-scene-and-aem-integration}

Als u problemen hebt met het integreren van Experience Manager met Dynamic Media Classic, raadpleegt u de volgende scenario&#39;s voor oplossingen.

**Als het publiceren van uw digitale middelen naar Dynamic Media Classic mislukt:**

* Controleer of het element dat u uploadt zich in het deelvenster **[!UICONTROL CQ target]** (u geeft deze map op in de Dynamic Media Classic-cloudconfiguratie).
* Als dit niet het geval is, moet u de cloudconfiguratie configureren in **[!UICONTROL Page Properties]** voor die pagina uploaden naar de **[!UICONTROL CQ ad hoc]** map.

* Controleer de logboeken voor om het even welke informatie.

**Als uw videovoorinstellingen niet worden weergegeven:**

* Zorg ervoor dat u de wolkenconfiguratie van die pagina door hebt gevormd **[!UICONTROL Page Properties]**. Videovoorinstellingen zijn beschikbaar in de Dynamic Media Classic-videocomponent.

**Als uw video-elementen niet in Experience Manager worden afgespeeld:**

* Controleer of u de juiste videocomponent hebt gebruikt. Dynamic Media Classic video component is verschillend van de stichting Video component. Zie [Foundation Video Component versus Dynamic Media Classic Video Component](/help/assets/s7-video.md).

**Als nieuwe of gewijzigde middelen in Experience Manager niet automatisch naar Dynamic Media Classic worden geüpload:**

* Zorg ervoor dat de elementen zich in de CQ-doelmap bevinden. Alleen elementen in de CQ-doelmap worden automatisch bijgewerkt (op voorwaarde dat u Experience Manager Assets hebt geconfigureerd voor het automatisch uploaden van middelen).
* Zorg ervoor dat u de configuratie van de Cloud Servicen hebt geconfigureerd voor Automatisch uploaden inschakelen en dat u de workflow voor DAM-middelen hebt bijgewerkt en opgeslagen, zodat deze ook het uploaden van Dynamic Media Classic omvat.
* Wanneer u een afbeelding uploadt naar een submap van de Dynamic Media Classic-doelmap, moet u een van de volgende handelingen uitvoeren:

   * Zorg ervoor dat de namen van alle elementen, ongeacht de locatie, uniek zijn. Anders wordt het element in de hoofddoelmap verwijderd en blijft alleen het element in de submap over.
   * Wijzig de manier waarop Dynamic Media Classic elementen overschrijft in het gedeelte Setup van de Dynamic Media Classic-account. Stel Dynamic Media Classic niet in om elementen te overschrijven, ongeacht de locatie als u elementen met dezelfde naam in submappen gebruikt.

**Als uw verwijderde elementen of mappen niet worden gesynchroniseerd tussen Dynamic Media Classic en Experience Manager:**

* Middelen en mappen die zijn verwijderd uit Experience Manager Assets, worden nog steeds weergegeven in de gesynchroniseerde map in Dynamic Media Classic. Verwijder deze handmatig.

**Als het uploaden van de video mislukt:**

* Als het uploaden van uw video mislukt en u Experience Manager gebruikt om video te coderen via de Dynamic Media Classic-integratie, raadpleegt u [Aanpasbare time-out toevoegen aan Dynamic Media Classic Upload-workflow](#adding-configurable-timeout-to-scene-upload-workflow).

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan lang duren voordat deze in Experience Manager worden weergegeven. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat. De hoofdmap bevat bijvoorbeeld vaak te veel elementen.
>
>Als u de integratie wilt testen, moet u het hoofdmappunt alleen naar een submap laten verwijzen in plaats van naar het hele bedrijf.
