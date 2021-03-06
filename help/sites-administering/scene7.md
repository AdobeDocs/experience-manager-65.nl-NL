---
title: Adobe Experience Manager integreren met Dynamic Media Classic
description: Leer hoe u Adobe Experience Manager kunt integreren met Dynamic Media Classic.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: f244cfb5-5550-4f20-92f0-bb296e2bf76e
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '5295'
ht-degree: 0%

---

# Adobe Experience Manager integreren met Dynamic Media Classic {#integrating-with-dynamic-media-classic-scene}

Adobe Dynamic Media Classic is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media-elementen aan web, mobiele apparaten, e-mail en displays en drukwerk via internet.

Als u Dynamic Media Classic wilt gebruiken, moet u de cloudconfiguratie zodanig configureren dat Dynamic Media Classic en Adobe Experience Manager Assets met elkaar kunnen communiceren. In dit document wordt beschreven hoe u Experience Manager en Dynamic Media Classic configureert.

Zie [Dynamic Media Classic](../assets/scene7.md) gebruiken voor informatie over het gebruik van alle Klassieke Dynamic Media-componenten op een pagina en het werken met video.

>[!NOTE]
>
>* Het DHTML-viewerplatform van Dynamic Media Classic bereikte op 31 januari 2014 officieel het einde van de levensduur. Zie [Veelgestelde vragen over einde levensduur van DHTML-viewer](../sites-administering/dhtml-viewer-endoflifefaqs.md) voor meer informatie.
>* Alvorens Dynamic Media Klassiek te vormen om met Experience Manager te werken, zie [Beste praktijken](#best-practices-for-integrating-scene-with-aem) voor het integreren van Klassiek Dynamic Media met Experience Manager.
>* Als u Dynamic Media Classic met een aangepaste proxyconfiguratie gebruikt, moet u beide proxyconfiguraties van de HTTP-client configureren, omdat sommige functies van de Experience Manager de 3.x-API&#39;s gebruiken en andere de 4.x-API&#39;s. 3.x wordt gevormd met [http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) en 4.x wordt gevormd met [http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator).

>



## Experience Manager/Dynamic Media Klassieke integratie versus Dynamic Media {#aem-scene-integration-versus-dynamic-media}

Gebruikers van Experience Managers kunnen kiezen uit twee oplossingen om met Dynamic Media te werken. U kunt een van de volgende opties gebruiken:

* Integreer uw exemplaar van Experience Manager met Dynamic Media Classic.
* Gebruik Dynamic Media die is ge??ntegreerd in de Experience Manager.

Gebruik de volgende criteria om te bepalen welke oplossing moet worden gekozen:

* Bent u een **bestaande** Klassieke klant van Dynamic Media de waarvan activa in de Klassiek van Dynamic Media voor publicatie en levering verblijven, maar u wilt die activa met het auteursrecht van Plaatsen (WCM), of de Activa van de Experience Manager, of allebei integreren? Als dat het geval is, gebruikt u de [Experience Manager/Dynamic Media Classic point-to-point integratie](#aem-scene-point-to-point-integration) die in dit document wordt beschreven.

* Als u een **nieuwe** klant bent die rijke media leveringsbehoeften heeft, selecteer [de optie van Dynamic Media](#aem-dynamic-media). Deze optie heeft de meeste zin als u geen bestaande S7-account hebt en veel middelen die in dat systeem zijn opgeslagen.

* Gebruik in bepaalde gevallen beide oplossingen. Het [scenario voor twee??rlei gebruik](/help/sites-administering/scene7.md#dual-use-scenario) beschrijft dat scenario.

### Experience Manager/Dynamic Media Klassieke point-to-point integratie {#aem-scene-point-to-point-integration}

Wanneer u met middelen in deze oplossing werkt, doet u ????n van het volgende:

* Upload middelen rechtstreeks naar Dynamic Media Classic en open vervolgens via de **Dynamic Media Classic**-inhoudbrowser voor het ontwerpen van pagina&#39;s of
* Uploaden naar Experience Manager Assets en vervolgens automatisch publiceren naar Dynamic Media Classic inschakelen; via de inhoudbrowser **Middelen** voor het ontwerpen van pagina&#39;s

De componenten die u voor deze integratie gebruikt, bevinden zich in het gebied **Dynamic Media Classic** in [Ontwerpmodus](/help/sites-authoring/author-environment-tools.md#page-modes).

### Experience Manager Dynamic Media {#aem-dynamic-media}

Experience Manager Dynamic Media is de hereniging van de Klassieke eigenschappen van Dynamic Media direct binnen het platform van de Experience Manager.

Wanneer u met middelen in deze oplossing werkt, volgt u deze workflow:

1. Upload afzonderlijke afbeeldings- en video-elementen rechtstreeks naar de Experience Manager.
1. Video&#39;s rechtstreeks in Experience Manager coderen.
1. Stel op afbeeldingen gebaseerde sets rechtstreeks samen binnen de Experience Manager.
1. Voeg, indien van toepassing, interactiviteit toe aan afbeeldingen of video&#39;s.

De componenten die u voor Dynamic Media gebruikt, bevinden zich in het componentgebied **[!UICONTROL Dynamic Media]** in [Ontwerpmodus](/help/sites-authoring/author-environment-tools.md#page-modes). Deze omvatten:

* **[!UICONTROL Dynamic Media]** - De  **[!UICONTROL Dynamic Media]** component is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

* **[!UICONTROL Interactive Media]** - De  **[!UICONTROL Interactive Media]** component is bedoeld voor elementen zoals carrouselbanners, interactieve afbeeldingen en interactieve video. Dergelijke elementen bevatten interactiviteit, zoals hotspots of afbeeldingen met hyperlinks. Deze component is slim. Afhankelijk van of u een afbeelding of video toevoegt, hebt u verschillende opties. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

### Scenario voor twee??rlei gebruik {#dual-use-scenario}

U kunt zowel de Dynamic Media- als de Dynamic Media Classic-integratiefuncties van Experience Manager tegelijk gebruiken. In de volgende tabel met gebruiksgevallen wordt beschreven wanneer u bepaalde gebieden in- en uitschakelt.

Dynamic Media en Dynamic Media Classic gelijktijdig gebruiken:

1. Configureer [Dynamic Media Classic](#creating-a-cloud-configuration-for-scene) in Cloud Services.
1. Volg de specifieke instructies voor uw gebruiksgeval op:

   <table>
    <tbody>
    <tr>
    <td> </td>
    <td> </td>
    <td><strong> Dynamic Media </strong></td>
    <td> </td>
    <td><strong>Dynamic Media Klassieke integratie</strong></td>
    <td> </td>
    </tr>
    <tr>
    <td><strong>Als u ...</strong></td>
    <td><strong>Hoofdletterwerkstroom gebruiken</strong></td>
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
    <td>Niet-productmiddelen uploaden naar Experience Manager voor beheer en levering. Upload PRODUCT-middelen naar Dynamic Media Classic en gebruik Dynamic Media Classic-inhoudsbrowser in Experience Manager en onderdeel om productdetailpagina's op sites te maken.</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Aan</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Nieuw bij Middelen en Dynamic Media</td>
    <td>Elementen uploaden naar Experience Manager Assets en gepubliceerde URL/insluitcode van Dynamic Media gebruiken</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td>Uit</td>
    <td>Uit</td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Nieuw bij Dynamic Media en Sjabloon</td>
    <td>Gebruik Dynamic Media voor beeldbewerking en video. Auteur afbeeldingssjablonen in Dynamic Media Classic en gebruik Dynamic Media Classic Content Finder om sjablonen op te nemen in sitepagina's.</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Aan</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Een bestaande Dynamic Media Classic-klant en is nieuw voor sites</td>
    <td>Elementen uploaden naar Dynamic Media Classic en Experience Manager Dynamic Media Classic-inhoudbrowser gebruiken om elementen op sitepagina's te zoeken en te ontwerpen</td>
    <td>Uit</td>
    <td>Uit</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Een bestaande Dynamic Media Classic-klant en is nieuw voor sites en middelen</td>
    <td>Elementen uploaden naar DAM en automatisch publiceren naar Dynamic Media Classic voor levering. Gebruik Experience Manager Dynamic Media Classic-inhoudbrowser om elementen op sitepagina's te zoeken en te ontwerpen.</td>
    <td>Uit</td>
    <td>Uit</td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td><p><a href="#configuringautouploadingfromaemassets">Aan</a></p> <p>(Zie stap 4)</p> </td>
    </tr>
    <tr>
    <td>Bestaande Dynamic Media Classic-klant en nieuw voor middelen</td>
    <td><p>Elementen uploaden naar Experience Manager en Dynamic Media gebruiken om uitvoeringen te genereren voor downloaden/delen. Publiceer automatisch Experience Manager-elementen naar Dynamic Media Classic voor levering.</p> <p><strong>Belangrijk: dubbele verwerkingen </strong> en uitvoeringen die in Experience Manager worden gegenereerd, worden niet gesynchroniseerd met Dynamic Media Classic</p> </td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td>Uit</td>
    <td>Uit</td>
    <td><p><a href="#configuringautouploadingfromaemassets">Aan</a></p> <p>(Zie stap 4)</p> </td>
    </tr>
    </tbody>
    </table>

1. (facultatief; zie gebruikscase table) - Stel de [Dynamic Media cloud configuration](/help/assets/config-dynamic.md) en [enable de Dynamic Media server](/help/assets/config-dynamic.md) in.
1. (facultatief; Zie use case table) - Als u Automatisch uploaden van middelen naar Dynamic Media Classic wilt inschakelen, moet u het volgende toevoegen:

   1. Automatische upload instellen op Dynamic Media Classic.
   1. Voeg de stap **Dynamic Media Klassieke upload** toe na alle Dynamic Media-workflowstappen *aan het einde van* **Dam Update Asset**-workflow ( `https://<server>:<host>/cf#/etc/workflow/models/dam/update_asset.html)`
   1. (Optioneel) Beperk het uploaden van klassieke Dynamic Media-elementen door MIME-type in [https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl](http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl). Elementen MIME-typen die niet in deze lijst voorkomen, worden niet ge??pload naar de Dynamic Media Classic-server.
   1. (Optioneel) Stel video in de Klassieke Dynamic Media-configuratie in. U kunt videocodering voor zowel Dynamic Media als Dynamic Media Classic tegelijk inschakelen. Dynamische uitvoeringen worden gebruikt voor voorvertoning en lokaal afspelen in Experience Manager-instantie, terwijl Dynamic Media Classic-video-uitvoeringen worden gegenereerd en opgeslagen op Dynamic Media Classic-servers. Wanneer u videocoderingsservices instelt voor zowel Dynamic Media als Dynamic Media Classic, past u een [videoverwerkingsprofiel](/help/assets/video-profiles.md) toe op de map met klassieke Dynamic Media-elementen.
   1. (Optioneel) [Beveiligde voorvertoning configureren in Dynamic Media Classic](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene).

#### Beperkingen {#limitations}

Wanneer u zowel Dynamic Media Classic als Dynamic Media hebt ingeschakeld, gelden de volgende beperkingen:

* Het handmatig uploaden naar Dynamic Media Classic door een element te selecteren en naar een Classic Dynamic Media-component op een Experience Manager-pagina te slepen, werkt niet.
* Hoewel Experience Manager-Dynamic Media Classic gesynchroniseerde elementen automatisch worden bijgewerkt naar Dynamic Media Classic wanneer het element wordt bewerkt in Elementen, wordt een terugdraaiactie niet geactiveerd om een nieuwe upload te starten. Als zodanig krijgt Dynamic Media Classic niet meteen na een terugdraaiactie de nieuwste versie. Als tussenoplossing kunt u het terugdraaien opnieuw uitvoeren.
* Is het nodig dat u Dynamic Media gebruikt voor ????n gebruiksgeval en Dynamic Media Classic voor een andere, zodat Dynamic Media-activa niet in wisselwerking staan met het Klassieke Dynamic Media-systeem? Als dat het geval is, moet u de Klassieke Dynamic Media-configuratie niet toepassen op de Dynamic Media-map. En pas de Dynamic Media-configuratie (verwerkingsprofiel) niet toe op een Classic-map van Dynamic Media.

## Aanbevolen procedures voor de integratie van Dynamic Media Classic met Experience Manager {#best-practices-for-integrating-scene-with-aem}

Bij de integratie van Dynamic Media Classic met Experience Manager zijn er enkele belangrijke beste praktijken die in acht moeten worden genomen op de volgende gebieden:

* Uw integratie testen
* Het rechtstreeks uploaden van middelen vanuit Dynamic Media Classic wordt aanbevolen voor bepaalde scenario&#39;s

Zie [bekende beperkingen](#known-limitations-and-design-implications).

### Test uw integratie {#test-driving-your-integration}

Adobe raadt u aan de integratie te testen door uw hoofdmap alleen naar een submap te laten verwijzen in plaats van naar een volledig bedrijf.

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan lang duren voordat deze in Experience Manager worden weergegeven. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat (de hoofdmap bevat bijvoorbeeld vaak te veel elementen en het systeem kan vastlopen).

### Elementen uploaden vanaf Experience Manager Assets versus vanuit Dynamic Media Classic {#uploading-assets-from-aem-assets-versus-from-scene}

U kunt elementen uploaden met behulp van de functionaliteit voor middelenbeheer (digital asset management) of door Dynamic Media Classic rechtstreeks in Experience Manager te openen via de Dynamic Media Classic-inhoudbrowser. Welke optie u kiest, is afhankelijk van de volgende factoren:

* Dynamic Media Classic-elementtypen die Experience Manager Assets nog niet ondersteunt, moeten rechtstreeks vanuit Dynamic Media Classic aan een website voor Experience Managers worden toegevoegd via de Dynamic Media Classic-inhoudbrowser. Bijvoorbeeld afbeeldingssjablonen.
* Voor elementtypen die zowel door Experience Manager Assets als door Dynamic Media Classic worden ondersteund, is het van het volgende afhankelijk hoe u deze kunt uploaden:

   * Waar de activa vandaag zijn, EN
   * Hoe belangrijk is het beheer ervan in een gemeenschappelijke gegevensopslagplaats?

Veronderstel dat de activa reeds in Dynamic Media Classic zijn en het beheren van hen in een gemeenschappelijke bewaarplaats is niet belangrijk. Als dat het geval is, dan is het exporteren van de activa naar Experience Manager Assets alleen om deze weer te synchroniseren naar Dynamic Media Classic voor levering een overbodige tijdelijke conversie. Adobe raadt u aan uw middelen in ????n opslagplaats te bewaren en ze alleen voor levering te synchroniseren met Dynamic Media Classic.

## Dynamic Media Classic-integratie configureren {#configuring-scene-integration}

U kunt Experience Manager configureren om elementen te uploaden naar Dynamic Media Classic. Middelen uit een CQ-doelmap kunnen (automatisch of handmatig) van Experience Manager naar een Classic-bedrijfsaccount van Dynamic Media worden ge??pload.

>[!NOTE]
>
>Adobe raadt u aan alleen de toegewezen doelmap te gebruiken voor het importeren van Klassieke Dynamic Media-elementen. Digitale middelen die zich buiten de doelmap bevinden, kunnen alleen worden gebruikt in Klassieke Dynamic Media-componenten op pagina&#39;s waarop de Klassieke Dynamic Media-configuratie is ingeschakeld. Bovendien worden ze in een map op aanvraag in Dynamic Media Classic geplaatst. De map op aanvraag is niet gesynchroniseerd met Experience Manager (maar elementen zijn wel te vinden in de browser met klassieke inhoud van Dynamic Media).

**Dynamic Media Classic configureren voor integratie met Experience Manager:**

1. [Definieer een wolkenconfiguratie](#creating-a-cloud-configuration-for-scene)  - Definieert de toewijzing tussen een klassieke Dynamic Media-map en een map Middelen. Voltooi deze stap zelfs als u slechts ????nrichtingssynchronisatie (middelen van de Experience Manager aan de Klassieke Dynamic Media) wilt.
1. [Schakel de  **Adobe CQ s7dam Dam Listener**](#enabling-the-adobe-cq-scene-dam-listener)  - Done in de  [!UICONTROL OSGi] console in.
1. Als u Experience Manager Assets automatisch wilt uploaden naar Dynamic Media Classic, moet u die optie inschakelen en Dynamic Media Classic toevoegen aan de [!UICONTROL DAM Update Asset]-workflow. U kunt ook handmatig elementen uploaden.
1. Dynamic Media Classic-componenten toevoegen aan het hulpwerkstation. Met deze functionaliteit kunnen gebruikers Dynamic Media Classic-componenten gebruiken op hun pagina&#39;s met Experience Managers.
1. [De configuratie in Experience Manager](#enabling-scene-for-wcm)  toewijzen aan de pagina - Deze stap is vereist voor het weergeven van videovoorinstellingen die u in Dynamic Media Classic hebt gemaakt. Dit is ook vereist als u een middel van buiten de CQ-doelmap naar Dynamic Media Classic moet publiceren.

In deze sectie wordt beschreven hoe u al deze stappen uitvoert en worden belangrijke beperkingen weergegeven.

### Hoe synchronisatie tussen Dynamic Media Classic en Experience Manager Assets werkt {#how-synchronization-between-scene-and-aem-assets-works}

Het is belangrijk dat u het volgende begrijpt wanneer u Experience Manager Assets en Dynamic Media Classic-synchronisatie instelt:

#### Uploaden naar Dynamic Media Classic vanaf Experience Manager Assets {#uploading-to-scene-from-aem-assets}

* Er is een toegewezen synchronisatiemap in Experience Manager voor Dynamic Media Classic-uploads.
* Uploads naar Dynamic Media Classic kunnen worden geautomatiseerd als de digitale elementen in de toegewezen synchronisatiemap worden geplaatst.
* De map- en submapstructuur in Experience Manager wordt gerepliceerd in Dynamic Media Classic.

>[!NOTE]
>
>Experience Manager sluit alle metagegevens in zoals XMP voordat deze naar Dynamic Media Classic worden ge??pload. Alle eigenschappen op het metagegevensknooppunt zijn dus beschikbaar in Dynamic Media Classic als XMP.

#### Bekende beperkingen en gevolgen voor het ontwerp {#known-limitations-and-design-implications}

Bij de synchronisatie tussen Experience Manager Assets en Dynamic Media Classic zijn er momenteel de volgende beperkingen/ontwerpimplicaties:

<table>
 <tbody>
  <tr>
   <td><strong>Beperking/gevolgen van ontwerp</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>E??n toegewezen synchronisatiemap (doel)</td>
   <td>U kunt per bedrijf slechts ????n toegewezen map in Experience Manager gebruiken voor Dynamic Media Classic-uploads. U kunt meerdere configuraties maken als u toegang moet hebben tot meer dan ????n bedrijfsaccount in Dynamic Media Classic.</td>
  </tr>
  <tr>
   <td>Mapstructuur</td>
   <td>Als u een gesynchroniseerde map met middelen verwijdert, worden alle Dynamic Media Classic externe middelen verwijderd, maar blijft de map ongewijzigd.</td>
  </tr>
  <tr>
   <td>Map op aanvraag</td>
   <td>Elementen die zich buiten de doelmap bevinden en die handmatig in WCM naar Dynamic Media Classic worden ge??pload, worden automatisch in een aparte map op aanvraag in Dynamic Media Classic geplaatst. U configureert deze map in de cloudconfiguratie in Experience Manager.</td>
  </tr>
  <tr>
   <td>Gemengde media</td>
   <td>Gemengde mediasets worden in de Experience Manager weergegeven, maar niet in de Experience Manager.</td>
  </tr>
  <tr>
   <td>PDF's</td>
   <td>Gegenereerde PDF's van eCatalogs in Dynamic Media Classic worden ge??mporteerd in de CQ-doelmap.</td>
  </tr>
  <tr>
   <td>interface vernieuwen</td>
   <td>Wanneer het synchroniseren tussen Experience Manager en Klassiek Dynamic Media, ben zeker om het gebruikersinterface te verfrissen om veranderingen te bekijken. </td>
  </tr>
  <tr>
   <td>Videominiaturen</td>
   <td>Als u een video uploadt naar Experience Manager Assets voor codering via Dynamic Media Classic, kan het enige tijd duren voordat de videominiaturen en gecodeerde video's beschikbaar zijn in Experience Manager Assets, afhankelijk van de videoverwerkingstijd.</td>
  </tr>
  <tr>
   <td>Doelsubmappen</td>
   <td><p>Als u submappen in de doelmap gebruikt, moet u ervoor zorgen dat u voor elk element unieke namen gebruikt (ongeacht de locatie). Ook, zorg ervoor u de Klassieke van Dynamic Media (in het gebied van de Opstelling) vormt om activa, ongeacht plaats niet te overschrijven.</p> <p>Anders worden elementen met dezelfde naam die naar een Classic-doelsubmap van Dynamic Media zijn ge??pload, wel ge??pload, maar wordt het element met dezelfde naam in de doelmap verwijderd. </p> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media Classic-servers configureren {#configuring-scene-servers}

Als u Experience Manager achter een volmacht in werking stelt of speciale firewallmontages hebt, moet u de gastheren van de verschillende gebieden uitdrukkelijk toelaten. De servers worden beheerd in inhoud in `/etc/cloudservices/scene7/endpoints` en kunnen worden aangepast zoals vereist. Selecteer een URL en bewerk deze vervolgens om de URL indien nodig te wijzigen. In vorige versies van Experience Manager waren deze waarden hard-gecodeerd.

Als u naar `/etc/cloudservices/scene7/endpoints.html` navigeert, worden de servers weergegeven (en kunt u ze bewerken door op de URL te tikken):

![chlimage_1-296](assets/chlimage_1-296.png)

### Een cloudconfiguratie maken voor Dynamic Media Classic {#creating-a-cloud-configuration-for-scene}

Een wolkenconfiguratie bepaalt de afbeelding tussen een Klassieke omslag van Dynamic Media en een omslag van de Middelen van de Experience Manager. Het moet worden gevormd om de Middelen van de Experience Manager met Dynamic Media Klassiek te synchroniseren. Zie Hoe de Synchronisatie voor meer informatie werkt.

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan lang duren voordat deze in Experience Manager worden weergegeven. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat. De hoofdmap bevat bijvoorbeeld vaak te veel elementen.
>
>Als u de integratie wilt testen en besturen, moet u de hoofdmap alleen verwijzen naar een submap in plaats van naar het hele bedrijf.

>[!NOTE]
>
>U kunt meerdere configuraties hebben: ????n wolkenconfiguratie vertegenwoordigt ????n gebruiker bij een Klassiek bedrijf van Dynamic Media. Als u toegang wilt tot andere Klassieke bedrijven of gebruikers van Dynamic Media, moet u veelvoudige configuraties tot stand brengen.

**Een cloudconfiguratie maken voor Dynamic Media Classic:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]** zodat u toegang hebt tot Adobe Dynamic Media Classic.

1. Selecteer **[!UICONTROL Configure now]**.

   ![chlimage_1-297](assets/chlimage_1-297.png)

1. Voer in het veld **[!UICONTROL Title]** en eventueel in het veld **[!UICONTROL Name]** de juiste gegevens in. Selecteer **[!UICONTROL Create]**.

   >[!NOTE]
   >
   >Als u meer configuraties maakt, wordt het veld **[!UICONTROL parent configuration]** weergegeven.
   >
   >Wijzig de bovenliggende configuratie niet **niet**. Het wijzigen van de bovenliggende configuratie kan de integratie onderbreken.

1. Voer het e-mailadres, het wachtwoord en de regio van uw Dynamic Media Classic-account in en selecteer **[!UICONTROL Connect to Dynamic Media Classic]**. U hebt verbinding met de Klassieke Dynamic Media-server en het dialoogvenster wordt uitgebreid met meer opties.

1. Voer de naam **[!UICONTROL Company]** en **[!UICONTROL Root Path]** in. Dit is de naam van de gepubliceerde server en het pad dat u wilt opgeven. Als u de gepubliceerde servernaam niet kent, gaat u in Dynamic Media Classic naar **[!UICONTROL Setup > Application Setup]**).

   >[!NOTE]
   >
   >Het klassieke Dynamic Media-hoofdpad is het pad van de Classic-map van Dynamic Media waarmee de Experience Manager verbinding maakt. U kunt de map verkleinen tot een specifieke map.

   >[!CAUTION]
   >
   >Afhankelijk van de grootte van de klassieke Dynamic Media-map kan het importeren van een hoofdmap lang duren. Bovendien zouden de Klassieke gegevens van Dynamic Media de opslag van de Experience Manager kunnen overschrijden. Controleer of u de juiste map importeert. Door te veel gegevens te importeren, kan uw systeem worden gestopt.

   ![chlimage_1-298](assets/chlimage_1-298.png)

1. Selecteer **[!UICONTROL OK]**. Experience Manager slaat uw configuratie op.

>[!NOTE]
>
>Als u opnieuw verbinding maakt:
>
>* Wanneer u bij het publiceren opnieuw verbinding maakt met Dynamic Media Classic, kunt u het wachtwoord bij het publiceren of opnieuw verbinden niet opnieuw instellen (geen probleem voor de instantie Auteur).
>* Als u waarden wijzigt, zoals uw regio of bedrijfsnaam, moet u opnieuw verbinding maken met Dynamic Media Classic. Als de configuratieopties zijn gewijzigd maar niet opgeslagen, geeft de Experience Manager ten onrechte nog aan dat de configuratie geldig is. Zorg ervoor dat u opnieuw verbinding maakt.

>



### Adobe CQ Dynamic Media Classic Dam Listener inschakelen {#enabling-the-adobe-cq-scene-dam-listener}

Schakel de Klassieke Dam Listener van Adobe CQ Dynamic Media in, die standaard is uitgeschakeld.

**Adobe CQ Dynamic Media Classic Dam Listener inschakelen:**

1. Selecteer het pictogram [!UICONTROL Tools] en navigeer naar **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Navigeer in de webconsole naar **[!UICONTROL Adobe CQ Dynamic Media Classic Dam Listener]** en selecteer het selectievakje **[!UICONTROL Enabled]**.

   ![chlimage_1-299](assets/chlimage_1-299.png)

1. Selecteer **[!UICONTROL Save]**.

### Aanpasbare time-out toevoegen aan Dynamic Media Classic Upload-workflow {#adding-configurable-timeout-to-scene-upload-workflow}

Wanneer een instantie van de Experience Manager wordt gevormd om videocodering door Dynamic Media Classic te behandelen, door gebrek, is er een onderbreking van 35 minuten op om het even welke uploadbaan. U kunt deze instelling configureren om taken voor videocodering die mogelijk langer worden uitgevoerd, aan te passen.

1. Navigeer naar **http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl**.

   ![chlimage_1-300](assets/chlimage_1-300.png)

1. Wijzig het nummer naar wens in het veld **[!UICONTROL Active job timeout]**. Alle niet-negatieve getallen worden in seconden met de maateenheid geaccepteerd. Standaard is dit aantal ingesteld op 2100.

   >[!NOTE]
   >
   >Beste praktijken: De meeste elementen worden maximaal minuten ingesloten (bijvoorbeeld afbeeldingen). Maar in bepaalde gevallen - grotere video&#39;s bijvoorbeeld - verhoog de time-outwaarde tot 7200 seconden (twee uur) om ruimte te maken voor lange verwerkingstijd. Anders wordt deze klassieke Dynamic Media-uploadtaak gemarkeerd als **[!UICONTROL UploadFailed]** in de metagegevens van de JCR (Java??? Content Repository).

1. Selecteer **[!UICONTROL Save]**.

### Automatisch laden van Experience Manager-elementen {#autouploading-from-aem-assets}

Vanaf Experience Manager 6.3.2 is de Experience Manager Assets zo geconfigureerd dat ge??ploade digitale elementen worden bijgewerkt naar Dynamic Media Classic als de elementen zich in een CQ-doelmap bevinden.

Wanneer een element wordt toegevoegd aan Experience Manager Assets, wordt het automatisch ge??pload en gepubliceerd naar Dynamic Media Classic.

>[!NOTE]
>
>De maximale bestandsgrootte voor automatisch uploaden van Experience Manager Assets naar Dynamic Media Classic is 500 MB.

**Automatisch laden vanaf Experience Manager-elementen:**

1. Selecteer het pictogram Experience Manager en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteer onder de kop Dynamic Media onder Beschikbare configuraties **[!UICONTROL dms7 (Dynamic Media]**).
1. Selecteer het **[!UICONTROL Advanced]** lusje, selecteer **[!UICONTROL Enable Automatic Upload]** controlevakje, dan uitgezocht **[!UICONTROL OK]**. U moet nu de DAM Asset-workflow zodanig configureren dat het uploaden naar Dynamic Media Classic wordt opgenomen.

   >[!NOTE]
   >
   >Zie [De status (gepubliceerd/niet gepubliceerd) configureren van elementen die naar Dynamic Media Classic worden geduwd](#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) voor informatie over het doorsturen van elementen naar Dynamic Media Classic in een niet-gepubliceerde status.

   ![screen_shot_2018-03-15at52501pm](assets/screen_shot_2018-03-15at52501pm.jpg)

1. Navigeer terug naar de welkomstpagina van de Experience Manager en selecteer **[!UICONTROL Workflows]**. Dubbelklik op de **DAM Update Asset**-workflow zodat deze wordt geopend.
1. Navigeer in het hulpwerkgebied naar de **[!UICONTROL Workflow]**-componenten en selecteer **[!UICONTROL Dynamic Media Classic]**. Sleep **[!UICONTROL Dynamic Media Classic]** aan het werkschema en selecteer **[!UICONTROL Save]**. Middelen die in de doelmap aan Experience Manager Assets worden toegevoegd, worden automatisch ge??pload naar Dynamic Media Classic.

   ![chlimage_1-301](assets/chlimage_1-301.png)

   >[!NOTE]
   >
   >* Wanneer u na het automatiseren elementen toevoegt die niet in de CQ-doelmap staan, worden deze niet ge??pload naar Dynamic Media Classic.
   >* Experience Manager sluit alle metagegevens in zoals XMP voordat deze naar Dynamic Media Classic worden ge??pload. Alle eigenschappen op het metagegevensknooppunt zijn dus beschikbaar in Dynamic Media Classic als XMP.


### Configureer de status (gepubliceerd/niet gepubliceerd) van middelen die naar Dynamic Media Classic worden geduwd {#configuring-the-state-published-unpublished-of-assets-pushed-to-scene}

Als u middelen van de Activa van de Experience Manager aan de Klassiek van Dynamic Media duwt, kunt u of hen automatisch publiceren (standaardgedrag) of hen duwen aan de Klassiek van Dynamic Media in een niet gepubliceerde staat.

Het is mogelijk dat u elementen niet direct op Dynamic Media Classic wilt publiceren als u ze in een testomgeving wilt testen voordat u live gaat. U kunt Experience Manager met de Veilige omgeving van de Test van Dynamic Media Classic gebruiken om activa van Activa in de Klassiek van Dynamic Media in een niet gepubliceerde staat direct te duwen.

Dynamic Media Klassieke elementen blijven beschikbaar via een beveiligde voorvertoning. Alleen wanneer de activa binnen de Experience Manager worden gepubliceerd, worden de Klassieke activa van Dynamic Media ook in productie genomen.

Als u elementen direct wilt publiceren wanneer u ze naar Dynamic Media Classic duwt, hoeft u geen opties te configureren. Deze functionaliteit is het standaardgedrag.

Als u echter niet wilt dat elementen die aan Dynamic Media Classic worden doorgegeven, automatisch worden gepubliceerd, wordt in deze sectie beschreven hoe u Experience Manager en Dynamic Media Classic kunt configureren om deze functionaliteit uit te voeren.

#### Vereisten om elementen naar Dynamic Media Classic te verzenden zonder publicatie {#prerequisites-to-push-assets-to-scene-unpublished}

Voordat u elementen naar Dynamic Media Classic kunt verzenden zonder ze te publiceren, moet u het volgende instellen:

1. [Gebruik de Admin Console om een steungeval](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) tot stand te brengen. In het geval van ondersteuning kunt u vragen of een beveiligde voorvertoning voor uw Dynamic Media Classic-account is ingeschakeld.
1. [Beveiligde voorvertoning instellen voor uw Dynamic Media Classic-account](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html?lang=en).

Dit zijn dezelfde stappen die u zou volgen om een veilige testinstallatie te maken in Dynamic Media Classic.

>[!NOTE]
>
>Als uw installatieomgeving een 64-bits UNIX??-besturingssysteem is, raadpleegt u [https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html) betreffende andere configuratieopties die u moet instellen.

#### Bekende beperkingen voor het doorduwen van elementen in niet-gepubliceerde toestand  {#known-limitations-for-pushing-assets-in-unpublished-state}

Houd rekening met de volgende beperkingen als u deze functie gebruikt:

* Er is geen ondersteuning voor versiebeheer.
* Als een element al in Experience Manager is gepubliceerd en er een volgende versie wordt gemaakt, wordt die nieuwe versie onmiddellijk live gepubliceerd voor productie. Publiceren bij activering werkt alleen met de eerste publicatie van een element.

>[!NOTE]
>
>Als u elementen direct wilt publiceren, kunt u het beste **[!UICONTROL Enable Secure Preview]** ingesteld houden op **[!UICONTROL Immediately]** en de functie **[!UICONTROL Enable Automatic Upload]** gebruiken.

### De status van naar Dynamic Media Classic geduwde elementen instellen als niet-gepubliceerd {#setting-the-state-of-assets-pushed-to-scene-as-unpublished}

>[!NOTE]
>
>Als een gebruiker het element in Experience Manager publiceert, wordt het S7-element automatisch geactiveerd voor de productie/het actieve element (het element bevindt zich niet meer in een beveiligde voorvertoning/is niet gepubliceerd).

**De status van elementen die naar Dynamic Media Classic worden geduwd, instellen als niet-gepubliceerd:**

1. Selecteer het pictogram Experience Manager en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteer **[!UICONTROL Dynamic Media Classic]**.
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer het tabblad **[!UICONTROL Advanced]**.
1. Selecteer **[!UICONTROL Upon AEM Publish Activation]** in het vervolgkeuzemenu **[!UICONTROL Enable Secure View]** om elementen naar Dynamic Media Classic te verzenden zonder te publiceren. (Deze waarde wordt standaard ingesteld op **[!UICONTROL Immediately]**, waarbij Klassieke Dynamic Media-elementen direct worden gepubliceerd.)

   Zie [Klassieke documentatie van Dynamic Media](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html) voor meer informatie over testmiddelen alvorens hen openbaar te maken.

   ![chlimage_1-302](assets/chlimage_1-302.png)

1. Selecteer **[!UICONTROL OK]**.

Als u Beveiligde voorvertoning inschakelt, worden uw elementen naar de beveiligde voorvertoningsserver geduwd zonder deze te publiceren.

Als u wilt zien of **[!UICONTROL Secure Preview]** is ingeschakeld, navigeert u naar een klassieke Dynamic Media-component op een pagina in de Experience Manager. Selecteer **[!UICONTROL Edit]**. Het element heeft de beveiligde voorvertoningsserver die in de URL wordt vermeld. Na publicatie in Experience Manager wordt het serverdomein in de bestandsverwijzing bijgewerkt van de voorbeeld-URL naar de productie-URL.

### Dynamic Media Classic inschakelen voor WCM {#enabling-scene-for-wcm}

U moet Dynamic Media Classic voor WCM inschakelen om twee redenen:

* Hiermee wordt de vervolgkeuzelijst met universele videoprofielen ingeschakeld voor het ontwerpen van pagina&#39;s. Zonder deze lijst, is **[!UICONTROL Universal Video Preset]** drop-down leeg en kan niet worden geplaatst.
* Als een digitaal element niet in de doelmap staat, kunt u het element uploaden naar Dynamic Media Classic als u Dynamic Media Classic voor die pagina in de pagina-eigenschappen inschakelt. Vervolgens sleept u het element naar een klassieke Dynamic Media-component. Normale overervingsregels zijn van toepassing (dat wil zeggen dat onderliggende pagina&#39;s de configuratie overnemen van de bovenliggende pagina).

Wanneer het toelaten van de Klassiek van Dynamic Media voor WCM, zoals met andere configuraties, zijn de overervingsregels van toepassing. U kunt Dynamic Media Classic voor WCM inschakelen in de geoptimaliseerde aanraakinterface of in de klassieke gebruikersinterface.

#### Dynamic Media Classic voor WCM inschakelen in de gebruikersinterface met geoptimaliseerde aanrakingen {#enabling-scene-for-wcm-in-the-touch-optimized-user-interface}

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Sites]** en vervolgens naar de hoofdpagina van uw website (niet taalspecifiek).

1. Selecteer in de werkbalk het pictogram [!UICONTROL settings] en selecteer **[!UICONTROL Open Properties]**.

1. Selecteer **[!UICONTROL Cloud Services]**, selecteer **[!UICONTROL Add Configuration]** en selecteer **[!UICONTROL Dynamic Media Classic]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Adobe Dynamic Media Classic]** de gewenste configuratie en selecteer **[!UICONTROL OK]**.

   ![chlimage_1-303](assets/chlimage_1-303.png)

   Videovoorinstellingen uit die configuratie van Dynamic Media Classic zijn beschikbaar voor gebruik in Experience Manager met de Klassieke Dynamic Media-videocomponent op die pagina en onderliggende pagina&#39;s.

#### Dynamic Media Classic inschakelen voor WCM in de klassieke gebruikersinterface {#enabling-scene-for-wcm-in-the-classic-user-interface}

1. Selecteer **[!UICONTROL Websites]** in Experience Manager en navigeer naar de hoofdpagina van uw website (niet taalspecifiek).

1. Selecteer in de assistent het pictogram **[!UICONTROL Page]** en selecteer **[!UICONTROL Page Properties]**.

1. Selecteer **[!UICONTROL Cloud Services]** > **[!UICONTROL Add services]** > **[!UICONTROL Dynamic Media Classic]**.
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Adobe Dynamic Media Classic]** de gewenste configuratie en selecteer **[!UICONTROL OK]**.

   Videovoorinstellingen uit die configuratie van Dynamic Media Classic zijn beschikbaar voor gebruik in Experience Manager met de Klassieke Dynamic Media-videocomponent op die pagina en onderliggende pagina&#39;s.

### Een standaardconfiguratie configureren {#configuring-a-default-configuration}

Als u meerdere Klassieke Dynamic Media-configuraties hebt, kunt u er een als standaard opgeven voor de Dynamic Media Klassieke-inhoudbrowser.

Slechts ????n Klassieke configuratie van Dynamic Media kan als gebrek op een bepaald ogenblik worden gemerkt. De standaardconfiguratie is de bedrijfsactiva die door gebrek in de Browser van de Inhoud van Dynamic Media Klassieke tonen.

**Een standaardconfiguratie configureren:**

1. Selecteer het pictogram Experience Manager en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteer **[!UICONTROL Dynamic Media Classic]**.
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer **[!UICONTROL Edit]** om de configuratie te openen.

1. Schakel op het tabblad **[!UICONTROL General]** het selectievakje **[!UICONTROL Default Configuration]** in om dit het standaardbedrijf en basispad te maken dat wordt weergegeven in de Dynamic Media Klassieke inhoudbrowser.

   ![chlimage_1-304](assets/chlimage_1-304.png)

   >[!NOTE]
   >
   >Als er slechts ????n configuratie is, heeft het selecteren van **[!UICONTROL Default Configuration]** controledoos geen effect.

### De map Ad hoc configureren {#configuring-the-ad-hoc-folder}

U kunt de map op aanvraag configureren waarnaar elementen worden ge??pload in Dynamic Media Classic wanneer het element niet in de CQ-doelmap staat. Zie Elementen publiceren van buiten de CQ-doelmap.

**De map Ad hoc configureren:**

1. Selecteer het pictogram Experience Manager en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**.
1. Selecteer **[!UICONTROL Dynamic Media Classic]**.
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer **[!UICONTROL Edit]** om de configuratie te openen.

1. Selecteer het tabblad **[!UICONTROL Advanced]**. In het veld **[!UICONTROL Ad-hoc Folder]** kunt u de map **Ad-hoc** wijzigen. Standaard is dit de **naam_van_het_bedrijf/CQ5_adhoc**.

   ![chlimage_1-305](assets/chlimage_1-305.png)

### Universele videovoorinstellingen configureren {#configuring-universal-presets}

Zie [Video](/help/assets/s7-video.md) om universele videovoorinstellingen voor de videocomponent te configureren.

## Op MIME gebaseerde Middelen/Dynamic Media Classic uploadtaakparameterondersteuning inschakelen {#enabling-mime-type-based-assets-scene-upload-job-parameter-support}

U kunt configureerbare Dynamic Media Classic-uploadtaakparameters inschakelen die worden geactiveerd door de synchronisatie van Digital Asset Manager/Dynamic Media Classic-middelen.

Specifiek, vormt u het erkende dossierformaat door MIME type in het OSGi (Open het initiatief van de Gateway van de Dienst) gebied van het paneel van de Configuratie van de Console van het Web van de Experience Manager. Vervolgens kunt u de afzonderlijke taakparameters voor uploaden aanpassen die worden gebruikt voor elk MIME-type in de JCR (Java??? Content Repository).

**Op MIME gebaseerde elementen inschakelen:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Selecteer **[!UICONTROL Configuration]** in het menu **[!UICONTROL OSGi]** in het deelvenster Configuratie van de Adobe Experience Manager-webconsole.
1. Zoek en selecteer **[!UICONTROL Adobe CQ Dynamic Media Classic Asset MIME type Service]** onder de kolom Naam om de configuratie te bewerken.
1. Selecteer in het gebied MIME-typetoewijzing een plusteken (+) om een MIME-type toe te voegen.

   Zie [Ondersteunde MIME-typen](/help/assets/assets-formats.md#supported-mime-types).

1. Typ de nieuwe naam van het MIME-type in het tekstveld.

   U kunt bijvoorbeeld een `<file_extension>=<mime_type>` typen zoals in `EPS=application/postscript` OF `PSD=image/vnd.adobe.photoshop`.

1. Selecteer **[!UICONTROL Save]** in de rechterbenedenhoek van het configuratievenster.
1. Ga terug naar de Experience Manager en selecteer **[!UICONTROL CRXDE Lite]** in de linkerrails.
1. Navigeer op de pagina CRXDE Lite in de linkertrack naar `/etc/cloudservices/scene7/<environment>` (vervang `<environment>` voor de eigenlijke naam).
1. Breid `<environment>` (substitueer `<environment>` voor de daadwerkelijke naam) uit om de `mimeTypes` knoop te openbaren.
1. Selecteer het mimeType dat u zojuist hebt toegevoegd.

   Bijvoorbeeld `mimeTypes > application_postscript` OF `mimeTypes > image_vnd.adobe.photoshop`.

1. Selecteer rechts van de pagina CRXDE Lite de tab **[!UICONTROL Properties]**.
1. Geef een klassieke Dynamic Media-taakparameter voor uploaden op in het waardeveld **[!UICONTROL jobParam]**.

   Bijvoorbeeld, `psprocess="rasterize"&psresolution=120` .

   Zie [Adobe Classic Image Production System API](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-overview.html) voor meer uploadtaakparameters die u kunt gebruiken.

   >[!NOTE]
   >
   >Als u PSD-bestanden uploadt en u wilt deze als sjablonen met laagextracties verwerken, voert u het volgende in het waardeveld **[!UICONTROL jobParam]** in:
   >
   >`process=MaintainLayers&layerNaming=AppendName&createTemplate=true`
   >
   >Zorg ervoor dat uw PSD-bestand &#39;lagen&#39; heeft. Als het strikt genomen ????n afbeelding of een afbeelding met een masker is, wordt de afbeelding verwerkt als een afbeelding omdat er geen lagen zijn om te verwerken.

1. Selecteer **[!UICONTROL Save All]** in de linkerbovenhoek van de pagina CRXDE Lite.

## Problemen met de integratie van Dynamic Media Classic en Experience Manager oplossen {#troubleshooting-scene-and-aem-integration}

Als u problemen hebt met het integreren van Experience Manager met Dynamic Media Classic, raadpleegt u de volgende scenario&#39;s voor oplossingen.

**Als het publiceren van uw digitale middelen naar Dynamic Media Classic mislukt:**

* Controleer of het element dat u uploadt zich in de map **[!UICONTROL CQ target]** bevindt (u geeft deze map op in de Classic-cloudconfiguratie van Dynamic Media).
* Als dit niet het geval is, moet u de wolkenconfiguratie in **[!UICONTROL Page Properties]** voor die pagina vormen om het uploaden naar **[!UICONTROL CQ ad hoc]** omslag toe te staan.

* Controleer de logboeken voor om het even welke informatie.

**Als uw videovoorinstellingen niet worden weergegeven:**

* Zorg ervoor dat u de wolkenconfiguratie van die pagina door **[!UICONTROL Page Properties]** hebt gevormd. Videovoorinstellingen zijn beschikbaar in de klassieke Dynamic Media-videocomponent.

**Als uw video-elementen niet in Experience Manager worden afgespeeld:**

* Controleer of u de juiste videocomponent hebt gebruikt. Dynamic Media Klassieke videocomponent is anders dan de basis-videocomponent. Zie [Elementaire videocomponent versus Dynamic Media Klassieke videocomponent](/help/assets/s7-video.md).

**Als nieuwe of gewijzigde middelen in Experience Manager niet automatisch naar Dynamic Media Classic worden ge??pload:**

* Zorg ervoor dat de elementen zich in de CQ-doelmap bevinden. Alleen elementen in de CQ-doelmap worden automatisch bijgewerkt (op voorwaarde dat u Experience Manager-elementen hebt geconfigureerd voor het automatisch uploaden van elementen).
* Zorg ervoor dat u de configuratie Cloud Services zodanig hebt geconfigureerd dat Automatisch uploaden is ingeschakeld en dat u de DAM Asset-workflow hebt bijgewerkt en opgeslagen, zodat deze ook Dynamic Media Classic-uploaden omvat.
* Wanneer u een afbeelding uploadt naar een submap van de Dynamic Media Classic-doelmap, moet u een van de volgende handelingen uitvoeren:

   * Zorg ervoor dat de namen van alle elementen, ongeacht de locatie, uniek zijn. Anders wordt het element in de hoofddoelmap verwijderd en blijft alleen het element in de submap over.
   * Wijzig de manier waarop Dynamic Media Classic elementen overschrijft in het gedeelte Setup van de Dynamic Media Classic-account. Stel Dynamic Media Classic niet in om elementen te overschrijven, ongeacht de locatie als u elementen met dezelfde naam in submappen gebruikt.

**Als uw verwijderde elementen of mappen niet zijn gesynchroniseerd tussen Dynamic Media Classic en Experience Manager:**

* Elementen en mappen die zijn verwijderd uit Experience Manager Assets, worden nog steeds weergegeven in de gesynchroniseerde map in Dynamic Media Classic. Verwijder deze handmatig.

**Als het uploaden van de video mislukt:**

* Als uw video uploadt ontbreekt en u gebruikt Experience Manager om video door de Klassieke integratie van Dynamic Media te coderen, zie [configureerbare onderbreking toevoegen aan Klassieke de uploadworkflow van Dynamic Media](#adding-configurable-timeout-to-scene-upload-workflow).

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan lang duren voordat deze in Experience Manager worden weergegeven. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat. De hoofdmap bevat bijvoorbeeld vaak te veel elementen.
>
>Als u de integratie wilt testen, moet u het hoofdmappunt alleen naar een submap laten verwijzen in plaats van naar het hele bedrijf.
