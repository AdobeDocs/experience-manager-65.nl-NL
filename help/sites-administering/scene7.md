---
title: Adobe Experience Manager integreren met Dynamic Media Classic
description: Leer hoe u Adobe Experience Manager kunt integreren met Dynamic Media Classic.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: f244cfb5-5550-4f20-92f0-bb296e2bf76e
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: f96b178ae84b4b930b59e36d4994970682c53dbd
workflow-type: tm+mt
source-wordcount: '5216'
ht-degree: 0%

---

# Adobe Experience Manager integreren met Dynamic Media Classic {#integrating-with-dynamic-media-classic-scene}

Adobe Dynamic Media Classic is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media-elementen aan Web, mobiel, e-mail en displays en drukwerk via internet.

Als u Dynamic Media Classic wilt gebruiken, moet u de cloudconfiguratie zodanig configureren dat Dynamic Media Classic en Adobe Experience Manager Assets met elkaar kunnen communiceren. In dit document wordt beschreven hoe u Experience Manager en Dynamic Media Classic kunt configureren.

Voor informatie bij het gebruiken van alle componenten van Dynamic Media Classic op een pagina en het werken met video, zie [ Dynamic Media Classic van het Gebruik ](../assets/scene7.md).

>[!NOTE]
>
>* Dynamic Media Classic&#39;s DHTML-viewerplatform bereikte officieel het einde van de levensduur op 31 januari 2014. Voor meer informatie, zie [ Veelgestelde vragen van het eind-van-leven DHTML van de kijker ](../sites-administering/dhtml-viewer-endoflifefaqs.md).
>* Alvorens Dynamic Media Classic te vormen om met Experience Manager te werken, zie [ Beste praktijken ](#best-practices-for-integrating-scene-with-aem) voor het integreren van Dynamic Media Classic met Experience Manager.
>* Als u Dynamic Media Classic gebruikt met een aangepaste proxyconfiguratie, moet u beide proxyconfiguraties van de HTTP-client configureren, omdat sommige functies van Experience Manager de 3.x-API&#39;s gebruiken en andere de 4.x-API&#39;s. 3.x wordt gevormd met [ http://localhost:4502/system/console/configMgr/com.day.commons.httpclient ](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient) en 4.x wordt gevormd met [ http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator ](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator).
>

## Experience Manager/Dynamic Media Classic-integratie versus Dynamic Media {#aem-scene-integration-versus-dynamic-media}

Experience Manager-gebruikers kunnen kiezen uit twee oplossingen om met Dynamic Media te werken. U kunt een van de volgende opties gebruiken:

* Integreer uw exemplaar van Experience Manager met Dynamic Media Classic.
* Dynamische media gebruiken die in Experience Manager is geïntegreerd.

Gebruik de volgende criteria om te bepalen welke oplossing moet worden gekozen:

* Bent u een **bestaande** klant van Dynamic Media Classic de van wie activa in Dynamic Media Classic voor het publiceren en levering verblijven, maar u wilt die activa met het auteursrecht van Plaatsen (WCM), of Experience Manager Assets, of allebei integreren? Als zo, gebruik [ Experience Manager/Dynamic Media Classic punt om integratie ](#aem-scene-point-to-point-integration) te richten die in dit document wordt beschreven.

* Als u a **nieuwe** klant van Experience Manager bent die rijke media leveringsbehoeften heeft, selecteer de [ Dynamische optie van Media ](#aem-dynamic-media). Deze optie heeft de meeste zin als u geen bestaande S7-account hebt en veel middelen die in dat systeem zijn opgeslagen.

* Gebruik in bepaalde gevallen beide oplossingen. Het [ dubbel-gebruikscenario ](/help/sites-administering/scene7.md#dual-use-scenario) beschrijft dat scenario.

### Experience Manager/Dynamic Media Classic point-to-point integratie {#aem-scene-point-to-point-integration}

Wanneer u met middelen in deze oplossing werkt, doet u één van het volgende:

* Upload activa direct aan Dynamic Media Classic en dan toegang als **Dynamic Media Classic** inhoudsbrowser voor paginaontwerp of
* Upload aan Experience Manager Assets en laat dan automatisch het publiceren aan Dynamic Media Classic toe; u hebt toegang via **Assets** inhoudbrowser voor paginaontwerp

De componenten u voor deze integratie gebruikt worden gevonden in het **** componentengebied van Dynamic Media Classic op [ wijze van het Ontwerp ](/help/sites-authoring/author-environment-tools.md#page-modes).

### Experience Manager Dynamic Media {#aem-dynamic-media}

Experience Manager Dynamic Media is de samenvoeging van Dynamic Media Classic-functies die rechtstreeks binnen het Experience Manager-platform plaatsvindt.

Wanneer u met middelen in deze oplossing werkt, volgt u deze workflow:

1. Eén afbeelding en video-elementen rechtstreeks uploaden naar Experience Manager.
1. Video&#39;s rechtstreeks coderen in Experience Manager.
1. Stel sets op basis van afbeeldingen rechtstreeks samen in Experience Manager.
1. Voeg indien van toepassing interactiviteit toe aan afbeeldingen of video&#39;s.

De componenten u voor Dynamische Media gebruikt worden gevonden op het **[!UICONTROL Dynamic Media]** componentengebied op [ wijze van het Ontwerp ](/help/sites-authoring/author-environment-tools.md#page-modes). Hieronder vallen onder meer:

* **[!UICONTROL Dynamic Media]** - De component **[!UICONTROL Dynamic Media]** is slim. Afhankelijk van het feit of u een afbeelding of video toevoegt, hebt u verschillende opties. De component ondersteunt voorinstellingen voor afbeeldingen, op afbeeldingen gebaseerde viewers, zoals afbeeldingssets, centrifuges, gemengde mediasets en video. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

* **[!UICONTROL Interactive Media]** - De component **[!UICONTROL Interactive Media]** is bedoeld voor elementen zoals carrouselbanners, interactieve afbeeldingen en interactieve video. Dergelijke elementen bevatten interactiviteit, zoals hotspots of afbeeldingen met hyperlinks. Deze component is slim. Afhankelijk van of u een afbeelding of video toevoegt, hebt u verschillende opties. Bovendien reageert de viewer snel. De grootte van het scherm verandert automatisch op basis van de schermgrootte. Alle viewers zijn HTML5-viewers.

### Scenario voor tweeërlei gebruik {#dual-use-scenario}

U kunt zowel de integratiefuncties van Dynamic Media als die van Dynamic Media Classic van Experience Manager tegelijk gebruiken. In de volgende tabel met gebruiksgevallen wordt beschreven wanneer u bepaalde gebieden in- en uitschakelt.

Dynamische media en Dynamic Media Classic tegelijk gebruiken:

1. Vorm [ Dynamic Media Classic ](#creating-a-cloud-configuration-for-scene) in de Diensten van de Wolk.
1. Volg de specifieke instructies voor uw gebruiksgeval op:

   <table>
    <tbody>
    <tr>
    <td> </td>
    <td> </td>
    <td><strong>Dynamische media</strong></td>
    <td> </td>
    <td><strong>Dynamic Media Classic-integratie</strong></td>
    <td> </td>
    </tr>
    <tr>
    <td><strong>Als u ...</strong></td>
    <td><strong>Hoofdlettergebruik</strong></td>
    <td><strong>Afbeeldingen/video</strong></td>
    <td><strong>Dynamische media-component</strong></td>
    <td><strong>S7 Inhoudsbrowser en -componenten</strong></td>
    <td><strong>Automatisch uploaden van Assets naar S7</strong></td>
    </tr>
    <tr>
    <td>Nieuw bij sites en dynamische media</td>
    <td>Elementen uploaden naar Experience Manager en Experience Manager Dynamic Media-component gebruiken om elementen op sitepagina's te maken</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Aan</a></td>
    <td>Uit</td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>In de detailhandel, en nieuw aan Plaatsen en Dynamische Media</td>
    <td>Niet-productmiddelen uploaden naar Experience Manager voor beheer en levering. Upload PRODUCT-middelen naar Dynamic Media Classic en gebruik Dynamic Media Classic-inhoudbrowser in Experience Manager en onderdeel om productdetailpagina's op sites te maken.</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Aan</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Nieuw bij Assets en Dynamic Media</td>
    <td>Elementen uploaden naar Experience Manager Assets en gepubliceerde URL-/insluitcode van Dynamic Media gebruiken</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td>Uit</td>
    <td>Uit</td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Nieuw bij dynamische media en sjablonen</td>
    <td>Dynamische media gebruiken voor beeldbewerking en video. Auteur afbeeldingssjablonen in Dynamic Media Classic en gebruik Dynamic Media Classic content finder om sjablonen op te nemen in sitepagina's.</td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td><a href="/help/assets/adding-dynamic-media-assets-to-pages.md">Aan</a></td>
    <td><a href="/help/assets/scene7.md#scene-content-browser">Aan</a></td>
    <td>Uit</td>
    </tr>
    <tr>
    <td>Een bestaande Dynamic Media Classic-klant en is nieuw voor Sites</td>
    <td>Elementen uploaden naar Dynamic Media Classic en elementen op sitepagina's zoeken en schrijven met de Experience Manager Dynamic Media Classic-inhoudbrowser</td>
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
    <td>Bestaande Dynamic Media Classic-klant en nieuw voor Assets</td>
    <td><p>Elementen uploaden naar Experience Manager en gebruik Dynamic Media om uitvoeringen te genereren voor downloaden/delen. Publiceer Experience Manager-middelen automatisch naar Dynamic Media Classic voor levering.</p> <p><strong> Belangrijk:</strong> neemt dubbele die verwerking op en de vertoningen in Experience Manager worden geproduceerd worden niet gesynchroniseerd aan Dynamic Media Classic</p> </td>
    <td><p>Aan</p> <p>(Zie stap 3)</p> </td>
    <td>Uit</td>
    <td>Uit</td>
    <td><p><a href="#configuringautouploadingfromaemassets">Aan</a></p> <p>(Zie stap 4)</p> </td>
    </tr>
    </tbody>
    </table>

1. (Facultatief; zie gebruikscase lijst) - opstelling de [ Dynamische de wolkenconfiguratie van Media ](/help/assets/config-dynamic.md) en [ laat de Dynamische server van Media ](/help/assets/config-dynamic.md) toe.
1. (Optioneel; zie tabel met hoofdletters/kleine letters) - Als u Automatisch uploaden van Assets naar Dynamic Media Classic wilt inschakelen, moet u het volgende toevoegen:

   1. Automatisch uploaden naar Dynamic Media Classic instellen.
   1. Voeg de **Dynamic Media Classic** stap na alle Dynamische het werkschemastappen van Media *aan het eind van* **Activa van de Update van het Dam** toe ( `https://<server>:<host>/cf#/etc/workflow/models/dam/update_asset.html)`
   1. (Facultatief) Beperk Dynamic Media Classic activa uploaden door MIME type in [ https://&lt;server>:&lt;port>/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl ](http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7AssetMimeTypeServiceImpl). Elementen MIME-typen die niet in deze lijst voorkomen, worden niet geüpload naar de Dynamic Media Classic-server.
   1. (Optioneel) Stel video in Dynamic Media Classic-configuratie in. U kunt videocodering voor of zowel Dynamic Media als Dynamic Media Classic tegelijk inschakelen. Dynamische uitvoeringen worden gebruikt voor lokale voorvertoning en afspelen in Experience Manager-instantie, terwijl Dynamic Media Classic-video-uitvoeringen worden gegenereerd en opgeslagen op Dynamic Media Classic-servers. Wanneer het plaatsen van de video het coderen de diensten voor zowel Dynamische Media als Dynamic Media Classic, a [ videoverwerkingsprofiel ](/help/assets/video-profiles.md) op de de activaomslag van Dynamic Media Classic toepassen.
   1. (Facultatief) [ vorm Veilige voorproef in Dynamic Media Classic ](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene).

#### Beperkingen {#limitations}

Wanneer u zowel Dynamic Media Classic als Dynamic Media hebt ingeschakeld, gelden de volgende beperkingen:

* Het handmatig uploaden naar Dynamic Media Classic door een element te selecteren en naar een Dynamic Media Classic-component op een Experience Manager-pagina te slepen, werkt niet.
* Hoewel gesynchroniseerde elementen van Experience Manager-Dynamic Media Classic automatisch worden bijgewerkt naar Dynamic Media Classic wanneer het element wordt bewerkt in Assets, wordt een terugdraaiactie niet geactiveerd om een nieuwe upload te starten. Als zodanig krijgt Dynamic Media Classic niet onmiddellijk na een terugdraaiing de nieuwste versie. Als tussenoplossing kunt u het terugdraaien opnieuw uitvoeren.
* Is het nodig dat u Dynamic Media gebruikt voor het ene gebruik en Dynamic Media Classic-integratie voor het andere, zodat Dynamic Media-elementen niet met het Dynamic Media Classic-systeem communiceren? Als dat het geval is, moet u de Dynamic Media Classic-configuratie niet toepassen op de map Dynamic Media. En pas de Dynamic Media-configuratie (verwerkingsprofiel) niet toe op een Dynamic Media Classic-map.

## Aanbevolen procedures voor de integratie van Dynamic Media Classic met Experience Manager {#best-practices-for-integrating-scene-with-aem}

Bij de integratie van Dynamic Media Classic met Experience Manager zijn er enkele belangrijke beste praktijken die in acht moeten worden genomen op de volgende gebieden:

* Uw integratie testen
* Voor bepaalde scenario&#39;s wordt het uploaden van middelen rechtstreeks vanuit Dynamic Media Classic aanbevolen

Zie [ gekende beperkingen ](#known-limitations-and-design-implications).

### Test uw integratie {#test-driving-your-integration}

Adobe raadt u aan uw integratie te testen en te sturen door uw hoofdmap alleen naar een submap te laten verwijzen in plaats van naar een volledig bedrijf.

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan veel tijd in beslag nemen om weer te geven in Experience Manager. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat (de hoofdmap bevat bijvoorbeeld vaak te veel elementen en kan uw systeem vastlopen).

### Elementen uploaden van Experience Manager Assets naar Dynamic Media Classic {#uploading-assets-from-aem-assets-versus-from-scene}

U kunt elementen uploaden met behulp van de Assets-functionaliteit (digital asset management) of door Dynamic Media Classic rechtstreeks in Experience Manager te openen via de Dynamic Media Classic-inhoudbrowser. Welke optie u kiest, is afhankelijk van de volgende factoren:

* Dynamic Media Classic-elementtypen die Experience Manager Assets nog niet ondersteunt, moeten rechtstreeks vanuit Dynamic Media Classic aan een Experience Manager-website worden toegevoegd via de Dynamic Media Classic-inhoudbrowser. Bijvoorbeeld afbeeldingssjablonen.
* Voor de typen elementen die zowel door Experience Manager Assets als door Dynamic Media Classic worden ondersteund, is het van het volgende afhankelijk hoe u deze kunt uploaden:

   * Waar de activa zich vandaag bevinden, EN
   * Hoe belangrijk is het beheer ervan in een gemeenschappelijke gegevensopslagplaats?

Veronderstel dat de activa reeds in Dynamic Media Classic zijn en die in een gemeenschappelijke bewaarplaats beheren is niet belangrijk. Als dat het geval is, is het exporteren van de activa naar Experience Manager Assets om deze alleen weer te synchroniseren naar Dynamic Media Classic voor levering een overbodige retourvlucht. Adobe raadt u aan uw middelen in één opslagplaats te bewaren en ze voor levering alleen te synchroniseren met Dynamic Media Classic.

## Dynamic Media Classic-integratie configureren {#configuring-scene-integration}

U kunt Experience Manager configureren om elementen te uploaden naar Dynamic Media Classic. Assets vanuit een CQ-doelmap kan (automatisch of handmatig) vanuit Experience Manager worden geüpload naar een Dynamic Media Classic-bedrijfsaccount.

>[!NOTE]
>
>Adobe raadt u aan alleen de toegewezen doelmap te gebruiken voor het importeren van Dynamic Media Classic-elementen. Digitale middelen die zich buiten de doelmap bevinden, kunnen alleen worden gebruikt in Dynamic Media Classic-componenten op pagina&#39;s waarop de Dynamic Media Classic-configuratie is ingeschakeld. Bovendien worden ze in een map op aanvraag in Dynamic Media Classic geplaatst. De map op aanvraag is niet gesynchroniseerd met Experience Manager (maar elementen zijn te vinden in de Dynamic Media Classic-inhoudbrowser).

**om Dynamic Media Classic te vormen om met Experience Manager te integreren:**

1. [ bepaal een wolkenconfiguratie ](#creating-a-cloud-configuration-for-scene) - bepaalt de afbeelding tussen een omslag van Dynamic Media Classic en een omslag van Assets. Voltooi deze stap, zelfs als u synchronisatie in één richting (Experience Manager Assets naar Dynamic Media Classic) wilt uitvoeren.
1. [ laat **toe CQ s7dam de Listener van het Dam van Adobe**](#enabling-the-adobe-cq-scene-dam-listener) - Gedaan in de [!UICONTROL OSGi] console.
1. Als u wilt dat Experience Manager Assets automatisch naar Dynamic Media Classic uploadt, moet u die optie inschakelen en Dynamic Media Classic toevoegen aan de [!UICONTROL DAM Update Asset] -workflow. U kunt ook handmatig elementen uploaden.
1. Dynamic Media Classic-componenten toevoegen aan het hulpwerkstation. Met deze functionaliteit kunnen gebruikers Dynamic Media Classic-componenten op hun Experience Manager-pagina&#39;s gebruiken.
1. [ Kaart de configuratie aan de pagina in Experience Manager ](#enabling-scene-for-wcm) - Deze stap wordt vereist om het even welke video te bekijken vooraf instelt die u in Dynamic Media Classic hebt gecreeerd. Dit is ook vereist als u een middel van buiten de CQ-doelmap naar Dynamic Media Classic moet publiceren.

In deze sectie wordt beschreven hoe u al deze stappen uitvoert en worden belangrijke beperkingen weergegeven.

### Hoe synchronisatie tussen Dynamic Media Classic en Experience Manager Assets werkt {#how-synchronization-between-scene-and-aem-assets-works}

Bij het instellen van Experience Manager Assets- en Dynamic Media Classic-synchronisatie is het belangrijk dat u het volgende begrijpt:

#### Uploaden naar Dynamic Media Classic vanuit Experience Manager Assets {#uploading-to-scene-from-aem-assets}

* Er is een toegewezen synchronisatiemap in Experience Manager voor Dynamic Media Classic-uploads.
* Uploads naar Dynamic Media Classic kunnen worden geautomatiseerd als de digitale middelen in de aangewezen synchronisatiemap worden geplaatst.
* De map- en submappenstructuur in Experience Manager wordt gerepliceerd in Dynamic Media Classic.

>[!NOTE]
>
>Experience Manager sluit alle metagegevens in als XMP voordat deze naar Dynamic Media Classic worden geüpload. Alle eigenschappen op het metagegevensknooppunt zijn dus beschikbaar in Dynamic Media Classic als XMP.

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
   <td>U kunt per bedrijf slechts één toegewezen map hebben in Experience Manager voor uploads naar Dynamic Media Classic. U kunt meerdere configuraties maken als u toegang moet hebben tot meer dan één bedrijfsaccount in Dynamic Media Classic.</td>
  </tr>
  <tr>
   <td>Mapstructuur</td>
   <td>Als u een gesynchroniseerde map met middelen verwijdert, worden alle externe Dynamic Media Classic-middelen verwijderd, maar blijft de map ongewijzigd.</td>
  </tr>
  <tr>
   <td>Map op aanvraag</td>
   <td>Assets die zich buiten de doelmap bevindt en die handmatig in WCM naar Dynamic Media Classic worden geüpload, wordt automatisch in een aparte map op aanvraag in Dynamic Media Classic geplaatst. U configureert deze map in de cloudconfiguratie in Experience Manager.</td>
  </tr>
  <tr>
   <td>Gemengde media</td>
   <td>Gemengde mediasets worden weergegeven in Experience Manager, maar worden niet ondersteund in Experience Manager.</td>
  </tr>
  <tr>
   <td>PDF's</td>
   <td>Gegenereerde PDF's van eCatalogs in Dynamic Media Classic worden geïmporteerd in de CQ-doelmap.</td>
  </tr>
  <tr>
   <td>interface vernieuwen</td>
   <td>Bij het synchroniseren tussen Experience Manager en Dynamic Media Classic moet u de gebruikersinterface vernieuwen om de wijzigingen weer te geven. </td>
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

Als u Experience Manager achter een proxy uitvoert of speciale firewallinstellingen hebt, moet u de hosts van de verschillende gebieden expliciet inschakelen. Servers worden beheerd in inhoud in `/etc/cloudservices/scene7/endpoints` en kunnen naar wens worden aangepast. Selecteer een URL en bewerk deze vervolgens om de URL indien nodig te wijzigen. In eerdere versies van Experience Manager waren deze waarden vastgelegd in harde codes.

Als u naar `/etc/cloudservices/scene7/endpoints.html` navigeert, worden de servers weergegeven (en kunt u deze bewerken door op de URL te tikken):

![ chlimage_1-296 ](assets/chlimage_1-296.png)

### Een cloudconfiguratie voor Dynamic Media Classic maken {#creating-a-cloud-configuration-for-scene}

Een wolkenconfiguratie bepaalt de afbeelding tussen een omslag van Dynamic Media Classic en een omslag van Experience Manager Assets. Deze moet zijn geconfigureerd om Experience Manager Assets met Dynamic Media Classic te synchroniseren. Zie Hoe de Synchronisatie voor meer informatie werkt.

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan veel tijd in beslag nemen om weer te geven in Experience Manager. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat. De hoofdmap bevat bijvoorbeeld vaak te veel elementen.
>
>Als u de integratie wilt testen en besturen, moet u de hoofdmap alleen verwijzen naar een submap in plaats van naar het hele bedrijf.

>[!NOTE]
>
>U kunt meerdere configuraties hebben: één cloudconfiguratie vertegenwoordigt één gebruiker in een Dynamic Media Classic-bedrijf. Als u andere Dynamic Media Classic-bedrijven of -gebruikers wilt openen, moet u meerdere configuraties maken.

**om een wolkenconfiguratie voor Dynamic Media Classic tot stand te brengen:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]** , zodat u toegang hebt tot Adobe Dynamic Media Classic.

1. Selecteer **[!UICONTROL Configure now]** .

   ![ chlimage_1-297 ](assets/chlimage_1-297.png)

1. Voer in het veld **[!UICONTROL Title]** en eventueel in het veld **[!UICONTROL Name]** de juiste gegevens in. Selecteer **[!UICONTROL Create]** .

   >[!NOTE]
   >
   >Als u meer configuraties maakt, wordt het veld **[!UICONTROL parent configuration]** weergegeven.
   >
   >Wijzig **niet** de ouderconfiguratie. Het wijzigen van de bovenliggende configuratie kan de integratie onderbreken.

1. Voer het e-mailadres, het wachtwoord en de regio van uw Dynamic Media Classic-account in en selecteer **[!UICONTROL Connect to Dynamic Media Classic]** . U hebt verbinding met de Dynamic Media Classic-server en het dialoogvenster wordt uitgebreid met meer opties.

1. Voer de naam **[!UICONTROL Company]** en **[!UICONTROL Root Path]** in. Dit is de naam van de gepubliceerde server en het pad dat u wilt opgeven. Als u de naam van de gepubliceerde server niet kent, gaat u in Dynamic Media Classic naar **[!UICONTROL Setup > Application Setup]** .)

   >[!NOTE]
   >
   >Het Dynamic Media Classic-hoofdpad is de Dynamic Media Classic-map waarmee Experience Manager verbinding maakt. U kunt de map verkleinen tot een specifieke map.

   >[!CAUTION]
   >
   >Afhankelijk van de grootte van de Dynamic Media Classic-map kan het importeren van een hoofdmap lang duren. Bovendien kunnen Dynamic Media Classic-gegevens de Experience Manager-opslag overschrijden. Controleer of u de juiste map importeert. Door te veel gegevens te importeren, kan uw systeem worden gestopt.

   ![ chlimage_1-298 ](assets/chlimage_1-298.png)

1. Selecteer **[!UICONTROL OK]**. Experience Manager slaat uw configuratie op.

>[!NOTE]
>
>Als u opnieuw verbinding maakt:
>
>* Wanneer u bij het publiceren opnieuw verbinding maakt met Dynamic Media Classic, kunt u het wachtwoord opnieuw instellen bij het publiceren of opnieuw verbinden. Dit werkt niet (geen probleem in de instantie Auteur).
>* Als u waarden wijzigt, zoals uw regio of bedrijfsnaam, moet u opnieuw verbinding maken met Dynamic Media Classic. Als de configuratieopties zijn gewijzigd maar niet zijn opgeslagen, geeft Experience Manager ten onrechte nog aan dat de configuratie geldig is. Zorg ervoor dat u opnieuw verbinding maakt.
>

### Adobe CQ Dynamic Media Classic Dam Listener inschakelen {#enabling-the-adobe-cq-scene-dam-listener}

Schakel de Adobe CQ Dynamic Media Classic Dam Listener in, die standaard is uitgeschakeld.

**om de Listener van het Dam van Adobe toe te laten CQ Dynamic Media Classic:**

1. Selecteer het pictogram [!UICONTROL Tools] en navigeer naar **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** .
1. Navigeer in de webconsole naar **[!UICONTROL Adobe CQ Dynamic Media Classic Dam Listener]** en selecteer het selectievakje **[!UICONTROL Enabled]** .

   ![ chlimage_1-299 ](assets/chlimage_1-299.png)

1. Selecteer **[!UICONTROL Save]** .

### Aanpasbare time-out toevoegen aan Dynamic Media Classic Upload-workflow {#adding-configurable-timeout-to-scene-upload-workflow}

Wanneer een Experience Manager-instantie is geconfigureerd om videocodering af te handelen via Dynamic Media Classic, is er standaard een time-out van 35 minuten voor elke uploadtaak. U kunt deze instelling configureren om taken voor videocodering die mogelijk langer worden uitgevoerd, aan te passen.

1. Navigeer aan **http://localhost:4502/system/console/configMgr/com.day.cq.dam.scene7.impl.Scene7UploadServiceImpl**.

   ![ chlimage_1-300 ](assets/chlimage_1-300.png)

1. Wijzig het nummer naar wens in het veld **[!UICONTROL Active job timeout]** . Alle niet-negatieve getallen worden in seconden met de maateenheid geaccepteerd. Standaard is dit aantal ingesteld op 2100.

   >[!NOTE]
   >
   >Tips en trucs: de meeste elementen worden maximaal minuten ingesloten (bijvoorbeeld afbeeldingen). Maar in bepaalde gevallen - grotere video&#39;s bijvoorbeeld - verhoogt u de time-outwaarde tot 7200 seconden (twee uur) om ruimte te maken voor lange verwerkingstijd. Anders wordt deze Dynamic Media Classic-uploadtaak gemarkeerd als **[!UICONTROL UploadFailed]** in de metagegevens van de JCR (Java™ Content Repository).

1. Selecteer **[!UICONTROL Save]** .

### Automatisch uploaden vanuit Experience Manager Assets {#autouploading-from-aem-assets}

Vanaf Experience Manager 6.3.2 is Experience Manager Assets zo geconfigureerd dat geüploade digitale elementen naar Dynamic Media Classic worden bijgewerkt als de elementen zich in een CQ-doelmap bevinden.

Wanneer een element aan Experience Manager Assets wordt toegevoegd, wordt het automatisch geüpload en gepubliceerd naar Dynamic Media Classic.

>[!NOTE]
>
>De maximale bestandsgrootte voor automatisch uploaden van Experience Manager Assets naar Dynamic Media Classic is 500 MB.

**om van Experience Manager Assets te uploaden:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]** .
1. Selecteer onder Dynamische media onder Beschikbare configuraties **[!UICONTROL dms7 (Dynamic Media]**).
1. Selecteer de tab **[!UICONTROL Advanced]** , selecteer het selectievakje **[!UICONTROL Enable Automatic Upload]** en selecteer vervolgens **[!UICONTROL OK]** . Configureer de DAM Asset-workflow om het uploaden naar Dynamic Media Classic op te nemen.

   >[!NOTE]
   >
   >Zie [ Vormend de staat (gepubliceerd/unpublished) van activa die aan Dynamic Media Classic ](#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) voor informatie worden geduwd bij het duwen van activa aan Dynamic Media Classic in een niet gepubliceerde staat.

   ![ screen_shot_2018-03-15at52501pm ](assets/screen_shot_2018-03-15at52501pm.jpg)

1. Ga terug naar de welkomstpagina van Experience Manager en selecteer **[!UICONTROL Workflows]** . Dubbelklik het **werkschema van de Activa van de Update van 0} DAM {zodat opent het.**
1. Navigeer in de assistent naar de **[!UICONTROL Workflow]** -componenten en selecteer **[!UICONTROL Dynamic Media Classic]** . Sleep **[!UICONTROL Dynamic Media Classic]** naar de workflow en selecteer **[!UICONTROL Save]** . Assets die in de doelmap aan Experience Manager Assets is toegevoegd, wordt automatisch naar Dynamic Media Classic geüpload.

   ![ chlimage_1-301 ](assets/chlimage_1-301.png)

   >[!NOTE]
   >
   >* Wanneer u na het automatiseren elementen toevoegt die niet in de CQ-doelmap staan, worden deze niet naar Dynamic Media Classic geüpload.
   >* Experience Manager sluit alle metagegevens in als XMP voordat deze naar Dynamic Media Classic worden geüpload. Alle eigenschappen op het metagegevensknooppunt zijn dus beschikbaar in Dynamic Media Classic als XMP.

### De status (gepubliceerd/niet gepubliceerd) van aan Dynamic Media Classic geduwde middelen configureren {#configuring-the-state-published-unpublished-of-assets-pushed-to-scene}

Als u middelen van Experience Manager Assets naar Dynamic Media Classic duwt, kunt u of hen publiceren automatisch (standaardgedrag) of hen duwen aan Dynamic Media Classic in een niet gepubliceerde staat.

Het is mogelijk dat u elementen niet direct op Dynamic Media Classic wilt publiceren als u ze in een testomgeving wilt testen voordat u live gaat. U kunt Experience Manager met de Secure Test-omgeving van Dynamic Media Classic gebruiken om middelen rechtstreeks van Assets naar Dynamic Media Classic te verplaatsen in een niet-gepubliceerde status.

Dynamic Media Classic-elementen blijven beschikbaar via een beveiligde voorvertoning. Alleen wanneer de activa in Experience Manager worden gepubliceerd, worden de Dynamic Media Classic-activa ook in productie genomen.

Als u elementen direct wilt publiceren wanneer u ze naar Dynamic Media Classic duwt, hoeft u geen opties te configureren. Deze functionaliteit is het standaardgedrag.

Als u echter niet wilt dat elementen die aan Dynamic Media Classic worden doorgegeven, automatisch worden gepubliceerd, wordt in deze sectie beschreven hoe u Experience Manager en Dynamic Media Classic kunt configureren om deze functionaliteit uit te voeren.

#### Vereisten om elementen naar Dynamic Media Classic te verzenden zonder publicatie {#prerequisites-to-push-assets-to-scene-unpublished}

Voordat u elementen naar Dynamic Media Classic kunt duwen zonder ze te publiceren, moet u het volgende instellen:

1. [ Gebruik Admin Console om een steungeval ](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/support-for-experience-cloud.ug.html) tot stand te brengen. In het geval van ondersteuning kunt u vragen of een beveiligde voorvertoning voor uw Dynamic Media Classic-account is ingeschakeld.
1. [ Opstelling veilige voorproef voor uw rekening van Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html).

Dit zijn dezelfde stappen die u zou volgen om een veilige testinstallatie in Dynamic Media Classic te maken.

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

**om de staat van activa te plaatsen die aan Dynamic Media Classic als niet gepubliceerd worden geduwd:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]** .
1. Selecteer **[!UICONTROL Dynamic Media Classic]** .
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer de tab **[!UICONTROL Advanced]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Enable Secure View]** de optie **[!UICONTROL Upon AEM Publish Activation]** om elementen naar Dynamic Media Classic te verplaatsen zonder ze te publiceren. (Deze waarde wordt standaard ingesteld op **[!UICONTROL Immediately]** , waarbij Dynamic Media Classic-elementen direct worden gepubliceerd.)

   Zie {de documentatie van 0} Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/testing-assets-making-them-public.html) voor meer informatie over het testen van activa alvorens hen openbaar te maken.[

   ![ chlimage_1-302 ](assets/chlimage_1-302.png)

1. Selecteer **[!UICONTROL OK]** .

Als u Beveiligde voorvertoning inschakelt, worden uw elementen naar de beveiligde voorvertoningsserver geduwd zonder deze te publiceren.

Navigeer naar een Dynamic Media Classic-component op een pagina in Experience Manager om te zien of **[!UICONTROL Secure Preview]** is ingeschakeld. Selecteer **[!UICONTROL Edit]**. Het element heeft de beveiligde voorvertoningsserver die in de URL wordt vermeld. Na publicatie in Experience Manager wordt het serverdomein in de bestandsverwijzing bijgewerkt van de voorbeeld-URL naar de productie-URL.

### Dynamic Media Classic inschakelen voor WCM {#enabling-scene-for-wcm}

Dynamic Media Classic inschakelen voor WCM is om twee redenen vereist:

* Hiermee wordt de vervolgkeuzelijst met universele videoprofielen ingeschakeld voor het ontwerpen van pagina&#39;s. Zonder deze lijst is de vervolgkeuzelijst **[!UICONTROL Universal Video Preset]** leeg en kan deze niet worden ingesteld.
* Als een digitaal element niet in de doelmap staat, kunt u het element uploaden naar Dynamic Media Classic als u Dynamic Media Classic voor die pagina inschakelt in de pagina-eigenschappen. Vervolgens sleept u het element naar een Dynamic Media Classic-component. Normale overervingsregels zijn van toepassing (dat wil zeggen dat onderliggende pagina&#39;s de configuratie overnemen van de bovenliggende pagina).

Wanneer het toelaten van Dynamic Media Classic voor WCM, zoals met andere configuraties, zijn de overervingsregels van toepassing. U kunt Dynamic Media Classic for WCM inschakelen in de geoptimaliseerde aanraakinterface of in de klassieke gebruikersinterface.

#### Dynamic Media Classic for WCM inschakelen in de gebruikersinterface voor geoptimaliseerde aanrakingen {#enabling-scene-for-wcm-in-the-touch-optimized-user-interface}

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Sites]** , gevolgd door de hoofdpagina van uw website (niet taalspecifiek).

1. Selecteer in de werkbalk het pictogram [!UICONTROL settings] en selecteer **[!UICONTROL Open Properties]** .

1. Selecteer **[!UICONTROL Cloud Services]** en selecteer **[!UICONTROL Add Configuration]** en selecteer **[!UICONTROL Dynamic Media Classic]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Adobe Dynamic Media Classic]** de gewenste configuratie en selecteer **[!UICONTROL OK]** .

   ![ chlimage_1-303 ](assets/chlimage_1-303.png)

   De video stelt van die configuratie van Dynamic Media Classic zijn beschikbaar voor gebruik in Experience Manager met de videocomponent van Dynamic Media Classic op die pagina en kindpagina&#39;s.

#### Dynamic Media Classic for WCM inschakelen in de klassieke gebruikersinterface {#enabling-scene-for-wcm-in-the-classic-user-interface}

1. Selecteer **[!UICONTROL Websites]** in Experience Manager en navigeer naar de hoofdpagina van uw website (niet taalspecifiek).

1. Selecteer in het zijpaneel het pictogram **[!UICONTROL Page]** en selecteer **[!UICONTROL Page Properties]** .

1. Selecteer **[!UICONTROL Cloud Services]** > **[!UICONTROL Add services]** > **[!UICONTROL Dynamic Media Classic]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Adobe Dynamic Media Classic]** de gewenste configuratie en selecteer **[!UICONTROL OK]** .

   De video stelt van die configuratie van Dynamic Media Classic zijn beschikbaar voor gebruik in Experience Manager met de videocomponent van Dynamic Media Classic op die pagina en kindpagina&#39;s.

### Een standaardconfiguratie configureren {#configuring-a-default-configuration}

Als u meerdere Dynamic Media Classic-configuraties hebt, kunt u een van deze configuraties als standaard opgeven voor de Dynamic Media Classic-inhoudbrowser.

Er kan slechts één Dynamic Media Classic-configuratie op een bepaald moment als standaard worden gemarkeerd. De standaardconfiguratie is de bedrijfsactiva die door gebrek in Browser van de Inhoud van Dynamic Media Classic tonen.

**om een standaardconfiguratie te vormen:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]** .
1. Selecteer **[!UICONTROL Dynamic Media Classic]** .
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer **[!UICONTROL Edit]** om de configuratie te openen.

1. Schakel op het tabblad **[!UICONTROL General]** het selectievakje **[!UICONTROL Default Configuration]** in om dit in te stellen als standaardbedrijf en basispad dat wordt weergegeven in de Dynamic Media Classic-inhoudbrowser.

   ![ chlimage_1-304 ](assets/chlimage_1-304.png)

   >[!NOTE]
   >
   >Als er slechts één configuratie is, heeft het selecteren van het selectievakje **[!UICONTROL Default Configuration]** geen effect.

### De map Ad hoc configureren {#configuring-the-ad-hoc-folder}

U kunt de map op aanvraag configureren waarnaar elementen in Dynamic Media Classic worden geüpload wanneer het element zich niet in de CQ-doelmap bevindt. Zie Elementen publiceren van buiten de CQ-doelmap.

**om de Ad hoc omslag te vormen:**

1. Selecteer het Experience Manager-pictogram en navigeer naar **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]** .
1. Selecteer **[!UICONTROL Dynamic Media Classic]** .
1. Selecteer uw configuratie in Dynamic Media Classic.
1. Selecteer **[!UICONTROL Edit]** om de configuratie te openen.

1. Selecteer de tab **[!UICONTROL Advanced]** . Op het **[!UICONTROL Ad-hoc Folder]** gebied, kunt u de **ad hoc** omslag wijzigen. Door gebrek, is het **name_of_the_company/CQ5_adhoc**.

   ![ chlimage_1-305 ](assets/chlimage_1-305.png)

### Universele videovoorinstellingen configureren {#configuring-universal-presets}

Om universele videovoorinstellingen voor de videocomponent te vormen, zie [ Video ](/help/assets/s7-video.md).

## Ondersteuning voor MIME-taakparameters op basis van Assets/Dynamic Media Classic-typen inschakelen {#enabling-mime-type-based-assets-scene-upload-job-parameter-support}

U kunt configureerbare parameters voor uploadtaken voor Dynamic Media Classic inschakelen die worden geactiveerd door de synchronisatie van Digital Asset Manager/Dynamic Media Classic-middelen.

Specifiek, vormt u het erkende dossierformaat door MIME type in het OSGi (Open het initiatief van de Gateway van de Dienst) gebied van het paneel van de Configuratie van de Console van Experience Manager Web. Vervolgens kunt u de afzonderlijke taakparameters voor uploaden aanpassen die worden gebruikt voor elk MIME-type in de JCR (Java™ Content Repository).

**om MIME op type-gebaseerde activa toe te laten:**

1. Selecteer het Experience Manager-pictogram en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** .
1. Selecteer **[!UICONTROL Configuration]** in het menu **[!UICONTROL OSGi]** in het deelvenster Configuratie van de Adobe Experience Manager-webconsole.
1. Zoek en selecteer onder de kolom Naam **[!UICONTROL Adobe CQ Dynamic Media Classic Asset MIME type Service]** om de configuratie te bewerken.
1. Selecteer in het gebied MIME-typetoewijzing een plusteken (+) om een MIME-type toe te voegen.

   Zie [ Gesteunde types MIME ](/help/assets/assets-formats.md#supported-mime-types).

1. Typ de nieuwe naam van het MIME-type in het tekstveld.

   U kunt bijvoorbeeld een `<file_extension>=<mime_type>` typen zoals in `EPS=application/postscript` OR `PSD=image/vnd.adobe.photoshop` .

1. Selecteer **[!UICONTROL Save]** in de rechterbenedenhoek van het configuratievenster.
1. Ga terug naar Experience Manager en selecteer **[!UICONTROL CRXDE Lite]** in het linkerspoor.
1. Navigeer op de CRXDE Lite-pagina in de linkertrack naar `/etc/cloudservices/scene7/<environment>` (vervang `<environment>` door de eigenlijke naam).
1. Vouw `<environment>` uit (vervang `<environment>` de eigenlijke naam) om het knooppunt `mimeTypes` weer te geven.
1. Selecteer het mimeType dat u zojuist hebt toegevoegd.

   Bijvoorbeeld `mimeTypes > application_postscript` OR `mimeTypes > image_vnd.adobe.photoshop` .

1. Selecteer rechts van de CRXDE Lite-pagina de tab **[!UICONTROL Properties]** .
1. Geef een Dynamic Media Classic-taakparameter voor uploaden op in het veld **[!UICONTROL jobParam]** value.

   Bijvoorbeeld `psprocess="rasterize"&psresolution=120` .

   Zie [ het Systeem API van de Productie van het Beeld van Adobe Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/c-overview.html) voor meer uploadbaanparameters u kunt gebruiken.

   >[!NOTE]
   >
   >Als u PSD-bestanden uploadt en u wilt deze als sjablonen met laagextracties verwerken, voert u het volgende in het veld **[!UICONTROL jobParam]** Waarde in:
   >
   >`process=MaintainLayers&layerNaming=AppendName&createTemplate=true`
   >
   >Zorg ervoor dat uw PSD-bestand &#39;lagen&#39; heeft. Als het strikt genomen één afbeelding of een afbeelding met een masker is, wordt de afbeelding verwerkt als een afbeelding omdat er geen lagen zijn om te verwerken.

1. Selecteer **[!UICONTROL Save All]** in de linkerbovenhoek van de CRXDE Lite-pagina.

## Problemen met de integratie tussen Dynamic Media Classic en Experience Manager oplossen {#troubleshooting-scene-and-aem-integration}

Als u problemen hebt met het integreren van Experience Manager met Dynamic Media Classic, raadpleegt u de volgende scenario&#39;s voor oplossingen.

**als uw digitale activa die aan Dynamic Media Classic publiceren ontbreekt:**

* Controleer of het element dat u uploadt zich in de map **[!UICONTROL CQ target]** bevindt (u geeft deze map op in de Dynamic Media Classic-cloudconfiguratie).
* Als dit niet het geval is, moet u de cloudconfiguratie in **[!UICONTROL Page Properties]** voor die pagina configureren om uploaden naar de map **[!UICONTROL CQ ad hoc]** toe te staan.

* Controleer de logboeken voor om het even welke informatie.

**als uw video vooraf instelt niet verschijnt:**

* Zorg ervoor dat u de wolkenconfiguratie van die pagina door **[!UICONTROL Page Properties]** hebt gevormd. Videovoorinstellingen zijn beschikbaar in de Dynamic Media Classic-videocomponent.

**als uw videoactiva niet in Experience Manager spelen:**

* Controleer of u de juiste videocomponent hebt gebruikt. Dynamic Media Classic video component is verschillend van de stichting Video component. Zie [ de Videecomponent van de Stichting tegenover de Videomponent van Dynamic Media Classic ](/help/assets/s7-video.md).

**als de nieuwe of gewijzigde activa in Experience Manager niet automatisch aan Dynamic Media Classic uploaden:**

* Zorg ervoor dat de elementen zich in de CQ-doelmap bevinden. Alleen elementen in de CQ-doelmap worden automatisch bijgewerkt (op voorwaarde dat u Experience Manager Assets hebt geconfigureerd voor het automatisch uploaden van middelen).
* Zorg ervoor dat u de configuratie voor Cloud Services zodanig hebt geconfigureerd dat Automatisch uploaden is ingeschakeld en dat u de workflow voor DAM-middelen hebt bijgewerkt en opgeslagen, zodat deze ook het uploaden van Dynamic Media Classic omvat.
* Wanneer u een afbeelding uploadt naar een submap van de Dynamic Media Classic-doelmap, moet u een van de volgende handelingen uitvoeren:

   * Zorg ervoor dat de namen van alle elementen, ongeacht de locatie, uniek zijn. Anders wordt het element in de hoofddoelmap verwijderd en blijft alleen het element in de submap over.
   * Wijzig de manier waarop Dynamic Media Classic elementen overschrijft in het gedeelte Setup van de Dynamic Media Classic-account. Stel Dynamic Media Classic niet in om elementen te overschrijven, ongeacht de locatie als u elementen met dezelfde naam in submappen gebruikt.

**als uw geschrapte activa of omslagen niet tussen Dynamic Media Classic en Experience Manager worden gesynchroniseerd:**

* Assets en mappen die zijn verwijderd uit Experience Manager Assets, worden nog steeds weergegeven in de gesynchroniseerde map in Dynamic Media Classic. Verwijder deze handmatig.

**als uw video uploadt ontbreekt:**

* Als uw video uploadt ontbreekt en u Experience Manager gebruikt om video door de integratie van Dynamic Media Classic te coderen, zie [ configureerbare onderbreking aan Dynamic Media Classic toevoegen uploadt werkschema ](#adding-configurable-timeout-to-scene-upload-workflow).

>[!CAUTION]
>
>Het importeren van activa van een bestaande Dynamic Media Classic-bedrijfsaccount kan veel tijd in beslag nemen om weer te geven in Experience Manager. Zorg ervoor dat u een map in Dynamic Media Classic aanwijst die niet te veel elementen bevat. De hoofdmap bevat bijvoorbeeld vaak te veel elementen.
>
>Als u de integratie wilt testen, moet u het hoofdmappunt alleen naar een submap laten verwijzen in plaats van naar het hele bedrijf.
