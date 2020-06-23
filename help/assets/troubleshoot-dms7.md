---
title: Het oplossen van problemen - Dynamic Media Scene7 wijze
description: De Dynamic Media van het oplossen van problemen op Scene7 runmode.
uuid: 77e04ccf-33dc-4d2f-8950-318d4b008f74
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 0d48c031-d3ee-4143-b739-a79ba28fd63a
docset: aem65
translation-type: tm+mt
source-git-commit: e916f70549197ac9f95443e972401a78735b0560
workflow-type: tm+mt
source-wordcount: '1280'
ht-degree: 0%

---


# Het oplossen van problemen - Dynamic Media Scene7 wijze{#troubleshooting-dynamic-media-scene-mode}

In het volgende document wordt het oplossen van problemen voor Dynamic Media met de uitvoermodus **dynamicmedia_scene7** beschreven.

## Instellen en configureren {#setup-and-configuration}

Ervoor zorgen dat de Dynamic Media op de juiste wijze zijn ingesteld door het volgende te doen:

* Opstartopdracht bevat het `-r dynamicmedia_scene7` runmode-argument.
* Om het even welke AEM 6.4 cumulatieve fixfixpakken (GFPs) zijn geïnstalleerd eerst *vóór* om het even welke beschikbare Packs van de Eigenschap van Dynamic Media.
* Optioneel Feature Pack 18912 is geïnstalleerd.

   Dit facultatieve eigenschappak is voor de steun van FTP of als u activa aan Dynamic Media van Dynamic Media Klassiek (Scene7) migreert.

* Navigeer naar de gebruikersinterface van Cloud Servicen en bevestig dat de provisioned account onder verschijnt **[!UICONTROL Available Configurations.]**
* Zorg ervoor dat de `Dynamic Media Asset Activation (scene7)` replicatieagent is ingeschakeld.

   Deze replicatieagent wordt gevonden onder Medewerkers op Auteur.

## Algemeen (alle activa) {#general-all-assets}

Hier volgen enkele algemene tips en trucs voor alle elementen.

### Eigenschappen voor de synchronisatie van bedrijfsmiddelen {#asset-synchronization-status-properties}

De volgende eigenschappen van elementen kunnen in CRXDE Lite worden herzien om de succesvolle synchronisatie van de activa van AEM aan Dynamic Media te bevestigen:

| **Eigenschap** | **Voorbeeld** | **Beschrijving** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a|364266`** | Algemene indicator dat de knoop met Dynamic Media wordt verbonden. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **PublishComplete** - of fouttekst | Status van het uploaden van middelen naar Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Moet worden gevuld om URLs aan ver middel van Dynamic Media te produceren. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **geslaagd** of **mislukt:`<error text>`** | Synchronisatiestatus van sets (centrifuges, afbeeldingssets, enzovoort), voorinstellingen voor afbeeldingen, voorinstellingen voor viewers, updates van afbeeldingen met hyperlinks voor een element of afbeeldingen die zijn bewerkt. |

### Synchronisatie-logboekregistratie {#synchronization-logging}

Synchronisatiefouten en -problemen worden aangemeld `error.log` (AEM-servermap `/crx-quickstart/logs/`). Er is voldoende logboekregistratie beschikbaar om de hoofdoorzaak van de meeste problemen te bepalen. U kunt echter het logbestand voor DEBUG op het `com.adobe.cq.dam.ips` pakket verhogen via de Sling Console ([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog)) om meer informatie te verzamelen.

### Verplaatsen, kopiëren, verwijderen {#move-copy-delete}

Voer de volgende handelingen uit voordat u een bewerking Verplaatsen, Kopiëren of Verwijderen uitvoert:

* Voor afbeeldingen en video&#39;s moet u controleren of er een `<object_node>/jcr:content/metadata/dam:scene7ID` waarde bestaat voordat u bewerkingen voor verplaatsen, kopiëren of verwijderen uitvoert.
* Bevestig voor voorinstellingen voor afbeeldingen en viewers dat er een `https://<server>/crx/de/index.jsp#/etc/dam/presets/viewer/testpreset/jcr%3Acontent/metadata` waarde bestaat voordat u bewerkingen voor verplaatsen, kopiëren of verwijderen uitvoert.
* Als de bovenstaande metagegevenswaarde ontbreekt, moet u elementen opnieuw uploaden voordat u bewerkingen verplaatst, kopieert of verwijdert.

### Versiebeheer {#version-control}

Bij het vervangen van een bestaand Dynamic Media-element (dezelfde naam en locatie) kunt u beide elementen behouden of een versie vervangen/maken:

* Als u beide behoudt, wordt een nieuw element gemaakt met een unieke naam voor het gepubliceerde element-URL. Dit `image.jpg` is bijvoorbeeld het oorspronkelijke element en `image1.jpg` het nieuw geüploade element.

* Het creëren van een versie wordt niet gesteund in Dynamic Media - Scene7 wijzelevering. De nieuwe versie vervangt het bestaande element in levering.

## Afbeeldingen en sets {#images-and-sets}

Raadpleeg de volgende richtlijnen voor het oplossen van problemen als u problemen hebt met afbeeldingen en sets.

<table>
 <tbody>
  <tr>
   <td><strong>Probleem</strong></td>
   <td><strong>Foutopsporing</strong></td>
   <td><strong>Oplossing</strong></td>
  </tr>
  <tr>
   <td>Kan de knop Kopie-URL/Insluiten niet openen in de weergave met elementdetails</td>
   <td>
    <ol>
     <li><p>Ga naar CRX/DE:</p>
      <ul>
       <li>Controleer of de voorinstelling in het JCR is <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> gedefinieerd. Deze locatie is van toepassing als u een upgrade hebt uitgevoerd van AEM 6.x naar 6.4 en de migratie hebt uitgeschakeld. Anders is de locatie <code>/conf/global/settings/dam/dm/presets/viewer</code>.</li>
       <li>Controleer of het element in het JCR <code>dam:scene7FileStatus</code><strong> onder Metadata wordt weergegeven als </strong><code>PublishComplete</code>.</li>
      </ul> </li>
    </ol> </td>
   <td><p>Pagina vernieuwen/naar een andere pagina navigeren en terugkeren (JSP voor side rail moet opnieuw worden gecompileerd)</p> <p>Als dat niet werkt:</p>
    <ul>
     <li>Middelen publiceren.</li>
     <li>Elementen opnieuw uploaden en publiceren.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>De kiezer van het element in de seteditor is vastgelopen tijdens ononderbroken laden</td>
   <td><p>Bekend probleem dat in 6.4 moet worden opgelost</p> </td>
   <td><p>Sluit de kiezer en open deze opnieuw.</p> </td>
  </tr>
  <tr>
   <td><strong>De knop Selecteren</strong> is niet actief nadat u een element hebt geselecteerd als onderdeel van het bewerken van een set</td>
   <td><p> </p> <p>Bekend probleem dat in 6.4 moet worden opgelost</p> <p> </p> </td>
   <td><p>Klik eerst op een andere map in de Asset Selector en ga terug om het element te selecteren.</p> </td>
  </tr>
  <tr>
   <td>De carrouselhotspot beweegt zich rond na het schakelen tussen dia's</td>
   <td><p>Controleer of alle dia's even groot zijn.</p> </td>
   <td><p>Gebruik voor de carrousel alleen afbeeldingen met dezelfde grootte.</p> </td>
  </tr>
  <tr>
   <td>Afbeelding geeft geen voorbeeld weer met de Dynamic Media-viewer</td>
   <td><p>Controleren of het element <code>dam:scene7File</code> in de metagegevenseigenschappen (CRXDE Lite) staat</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>Geüpload element wordt niet weergegeven in elementkiezer</td>
   <td><p>Element controleren heeft eigenschap <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>In de weergave Banner op kaart wordt <strong>Nieuw</strong> weergegeven wanneer het element nog niet is verwerkt</td>
   <td>Activeer element <code>jcr:content</code> &gt; <code>dam:assetState</code> = als <code>unprocessed</code> dit niet is opgepikt in de workflow.</td>
   <td>Wacht tot asset is opgehaald via workflow.</td>
  </tr>
  <tr>
   <td>In afbeeldingen of sets wordt de URL van de viewer of de insluitcode niet weergegeven</td>
   <td>Controleer of de viewervoorinstelling is gepubliceerd.</td>
   <td><p>Ga naar <strong>Gereedschappen</strong> &gt; <strong>Middelen</strong> &gt; Voorinstellingen <strong></strong> viewer en publiceer de voorinstelling van de viewer.</p> </td>
  </tr>
 </tbody>
</table>

## Video {#video}

Raadpleeg de volgende richtlijnen voor het oplossen van problemen als u problemen hebt met video.

<table>
 <tbody>
  <tr>
   <td><strong>Probleem</strong></td>
   <td><strong>Foutopsporing</strong></td>
   <td><strong>Oplossing</strong></td>
  </tr>
  <tr>
   <td>Video kan niet worden voorvertoond</td>
   <td>
    <ul>
     <li>Controleer of aan de map een videoprofiel is toegewezen (als de bestandsindeling niet wordt ondersteund). Als deze optie niet wordt ondersteund, wordt alleen een afbeelding weergegeven.</li>
     <li>Het videoprofiel moet meer dan één coderingsvoorinstelling bevatten om een AVS-set te genereren (enkele coderingen worden behandeld als video-inhoud voor MP4-bestanden). voor niet-ondersteunde bestanden, op dezelfde manier behandeld als niet-verwerkte bestanden).</li>
     <li>Controleer of de video klaar is met verwerken door <code>dam:scene7FileAvs</code> <code>dam:scene7File</code> de metagegevens te bevestigen.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Wijs een videoprofiel toe aan de map.</li>
     <li>Bewerk het videoprofiel om meerdere coderingsvoorinstellingen op te nemen.</li>
     <li>Wacht tot de video is verwerkt.</li>
     <li>Als u de video opnieuw laadt, moet u ervoor zorgen dat de workflow Video coderen van Dynamic Media niet wordt uitgevoerd.<br /> </li>
     <li>Upload de video opnieuw.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Video is niet gecodeerd</td>
   <td>
    <ul>
     <li>Controleer of de runmode <code>dynamicmedia_scene7</code>is.</li>
     <li>Controleer of de cloudservice van Dynamic Media is geconfigureerd.</li>
     <li>Controleer of een videoprofiel is gekoppeld aan de uploadmap.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Controleer uw AEM-instantie met <code>-r dynamicmedia_scene7</code></li>
     <li>Controleer of de Configuratie van Dynamic Media onder Cloud Servicen behoorlijk opstelling is.</li>
     <li>Controleer of de map een videoprofiel heeft. Controleer ook het videoprofiel.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Videoverwerking duurt te lang</td>
   <td><p>U kunt als volgt bepalen of videocodering nog wordt uitgevoerd of dat er een foutstatus is ingevoerd:</p>
    <ul>
     <li>Controleer de videostatus <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
     <li>Controleer de video vanaf de workflowconsole <code>https://localhost:4502/libs/cq/workflow/content/console.html</code> &gt; Tabbladen Instanties, Archiveren en Mislukt.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Video-uitvoering ontbreekt</td>
   <td><p>Wanneer video wordt geüpload, maar er geen gecodeerde vertoningen zijn:</p>
    <ul>
     <li>Controleer of aan de map een videoprofiel is toegewezen.</li>
     <li>Controleer of de video klaar is met verwerken door <code>dam:scene7FileAvs</code> de metagegevens te bevestigen.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Wijs een videoprofiel toe aan de map.</li>
     <li>Wacht tot de video is verwerkt.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

## Viewers {#viewers}

Raadpleeg de volgende richtlijnen voor het oplossen van problemen als u problemen hebt met viewers.

<table>
 <tbody>
  <tr>
   <td><strong>Probleem</strong></td>
   <td><strong>Foutopsporing</strong></td>
   <td><strong>Oplossing</strong></td>
  </tr>
  <tr>
   <td>Voorinstellingen van viewer worden niet gepubliceerd</td>
   <td><p>Ga door naar de diagnostische pagina van de voorbeeldmanager: <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></p> <p>Berekende waarden observeren. Als u correct werkt, ziet u het volgende:</p> <p><code>_DMSAMPLE status: 0 unsyced assets - activation not necessary
       _OOTB status: 0 unsyced assets - 0 unactivated assets</code></p> <p><strong>Opmerking</strong>: Het kan ongeveer 10 minuten duren nadat de instellingen voor de cloud van Dynamic Media zijn geconfigureerd voor synchronisatie van de viewerelementen.</p> <p>Als er niet-geactiveerde elementen overblijven, klikt u op een van de knoppen <strong>Alle niet-geactiveerde elementen</strong> weergeven om details weer te geven.</p> </td>
   <td>
    <ol>
     <li>Navigeer naar de lijst met voorinstellingen voor viewers in de beheerprogramma's: <code>https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html</code></li>
     <li>Selecteer alle viewervoorinstellingen en klik op <strong>Publiceren</strong>.</li>
     <li>Navigeer terug naar voorbeeldbeheer en controleer of het aantal niet-geactiveerde elementen nu nul is.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Vooraf ingestelde illustraties van de viewer retourneren 404 vanaf de voorvertoning in elementdetails of kopiëren, URL- en insluitcode</td>
   <td><p>Voer in CRXDE Lite de volgende handelingen uit:</p>
    <ol>
     <li>Navigeer naar de <code>&lt;sync-folder&gt;/_CSS/_OOTB</code> map in de synchronisatiemap voor Dynamic Media (bijvoorbeeld <code>/content/dam/_CSS/_OOTB</code>).</li>
     <li>Zoek het metagegevensknooppunt van het problematische element (bijvoorbeeld <code>&lt;sync-folder&gt;/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/</code>).</li>
     <li>Controleer of er <code>dam:scene7*</code> eigenschappen zijn. Als het element is gesynchroniseerd en gepubliceerd, ziet u dat de <code>dam:scene7FileStatus</code> set is ingesteld op <strong>PublishComplete</strong>.</li>
     <li>Poging om de illustratie rechtstreeks van Dynamic Media aan te vragen door de waarden van de volgende eigenschappen en letterlijke tekenreeksen samen te voegen
      <ul>
       <li><code>dam:scene7Domain</code></li>
       <li><code>"is/content"</code></li>
       <li><code>dam:scene7Folder</code></li>
       <li><code>&lt;asset-name&gt;</code></li>
       <li>Voorbeeld: <code>https://&lt;server&gt;/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png</code></li>
      </ul> </li>
    </ol> </td>
   <td><p>Als de voorbeeldbestanden of voorinstellingsillustraties van de viewer niet zijn gesynchroniseerd of gepubliceerd, start u het gehele kopiëren/synchronisatieproces opnieuw:</p>
    <ol>
     <li>Navigeer naar CRXDE Lite.
      <ul>
       <li>Verwijderen <code>&lt;sync-folder&gt;/_CSS/_OOTB</code>.</li>
      </ul> </li>
     <li>Ga naar het CRX-pakketbeheer: <code>https://localhost:4502/crx/packmgr/</code><a href="https://localhost:4502/crx/packmgr/"></a>
      <ol>
       <li>Zoeken naar viewerpakket in lijst (het begint met <code>cq-dam-scene7-viewers-content</code>)</li>
       <li>Klik op <strong>Opnieuw installeren</strong>.</li>
      </ol> </li>
     <li>Onder Cloud Servicen, navigeer aan de pagina van de Configuratie van Dynamic Media, dan open de doos van de configuratiedialoog voor uw Dynamic Media - S7 configuratie.
      <ul>
       <li>Breng geen veranderingen aan, klik <strong>sparen</strong>. Hierdoor wordt de logica opnieuw geactiveerd om de voorbeeldelementen, de CSS met voorinstellingen voor viewers en illustraties te maken en te synchroniseren.<br />  </li>
      </ul> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>

