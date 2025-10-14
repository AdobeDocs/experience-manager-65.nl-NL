---
title: Problemen met Dynamic Media oplossen - Scene7-modus
description: Leer hoe u installatie-, configuratie- en algemene problemen in Dynamic Media kunt oplossen en oplossen wanneer deze in de Scene7-modus worden uitgevoerd.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: d4507059-a54d-4dc9-a263-e55dfa27eeb1
feature: Troubleshooting
mini-toc-levels: 3
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1385'
ht-degree: 0%

---

# Problemen met Dynamic Media oplossen - Scene7-modus{#troubleshooting-dynamic-media-scene-mode}

Het volgende document beschrijft het oplossen van problemen voor Dynamic Media die **in werking stellen dynamicmedia_scene7** wijze.

## Instellen en configureren {#setup-and-configuration}

Zorg ervoor dat Dynamic Media op de juiste wijze is ingesteld door het volgende te doen:

* Opstartopdracht bevat het argument voor de uitvoermodus van `-r dynamicmedia_scene7` .
* Om het even welke Adobe Experience Manager 6.4 cumulatieve fixpakken (GFPs) zijn eerst geïnstalleerd *vóór* om het even welke beschikbare Packs van de Eigenschap van Dynamic Media.
* Optioneel Feature Pack 18912 is geïnstalleerd.

  Dit optionele functiepakket is bedoeld voor FTP-ondersteuning of als u middelen van Dynamic Media Classic naar Dynamic Media migreert.

* Navigeer naar de gebruikersinterface van Cloud Servicen en bevestig dat de provisioned account onder **[!UICONTROL Available Configurations]** wordt weergegeven.
* Controleer of de replicatieagent van `Dynamic Media Asset Activation (scene7)` is ingeschakeld.

  Deze replicatieagent wordt gevonden onder Medewerkers op Auteur.

## Algemeen (alle Assets) {#general-all-assets}

Hier volgen enkele algemene tips en trucs voor alle elementen.

### Eigenschappen voor de synchronisatie van bedrijfsmiddelen {#asset-synchronization-status-properties}

De volgende eigenschappen van elementen kunnen in CRXDE Lite worden gecontroleerd om te bevestigen dat het element correct is gesynchroniseerd van Experience Manager naar Dynamic Media:

| **Bezit** | **Voorbeeld** | **Beschrijving** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a\|364266`** | Algemene indicator dat de knoop met Dynamic Media wordt verbonden. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **PublishComplete** of foutentekst | Status van het uploaden van middelen naar Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Moet zijn gevuld om URL&#39;s te genereren naar externe middelen van Dynamic Media. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **succes** of **ontbroken:`<error text>`** | Synchronisatiestatus van sets (centrifuges, afbeeldingssets, enzovoort), voorinstellingen voor afbeeldingen, voorinstellingen voor viewers, updates van afbeeldingen met hyperlinks voor een element of afbeeldingen die zijn bewerkt. |

### Synchronisatie-logboekregistratie {#synchronization-logging}

Synchronisatiefouten en -problemen worden aangemeld `error.log` (servermap Experience Manager `/crx-quickstart/logs/` ). Het voldoende registreren is beschikbaar om de worteloorzaak van de meeste kwesties te bepalen, nochtans kunt u het registreren aan DEBUG op het `com.adobe.cq.dam.ips` pakket door de Verschuivende Console ([&#x200B; https://localhost:4502/system/console/slinglog &#x200B;](https://localhost:4502/system/console/slinglog)) verhogen om meer informatie te verzamelen.

### Verplaatsen, kopiëren, verwijderen {#move-copy-delete}

Voer de volgende handelingen uit voordat u een bewerking Verplaatsen, Kopiëren of Verwijderen uitvoert:

* Voor afbeeldingen en video&#39;s moet u controleren of er een `<object_node>/jcr:content/metadata/dam:scene7ID` -waarde bestaat voordat u bewerkingen voor verplaatsen, kopiëren of verwijderen uitvoert.
* Voor voorinstellingen voor afbeeldingen en viewers controleert u of er een `https://<server>/crx/de/index.jsp#/etc/dam/presets/viewer/testpreset/jcr%3Acontent/metadata` -waarde bestaat voordat u bewerkingen voor verplaatsen, kopiëren of verwijderen uitvoert.
* Als de bovenstaande metagegevenswaarde ontbreekt, moet u de elementen opnieuw uploaden voordat u bewerkingen verplaatst, kopieert of verwijdert.

### Versiebeheer {#version-control}

Wanneer u een bestaand Dynamic Media-element vervangt (dezelfde naam en locatie), kunt u beide elementen behouden of een versie vervangen/maken:

* Als u beide instellingen behoudt, wordt een element gemaakt met een unieke naam voor de URL van het gepubliceerde element. `image.jpg` is bijvoorbeeld het oorspronkelijke element en `image1.jpg` is het net geüploade element.

* Het maken van een versie wordt niet ondersteund in de Dynamic Media- Scene7-modus. De nieuwe versie vervangt het bestaande element in levering.

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
       <li>Controleer of de voorinstelling in het JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> is gedefinieerd. Deze locatie is van toepassing als u een upgrade hebt uitgevoerd van Experience Manager 6.x naar 6.4 en de migratie hebt uitgeschakeld. Anders is de locatie <code>/conf/global/settings/dam/dm/presets/viewer</code> .</li>
       <li>Controleer of het element in het JCR <code>dam:scene7FileStatus</code><strong> </strong> onder Metagegevens bevat als <code>PublishComplete</code> .</li>
      </ul> </li>
    </ol> </td>
   <td><p>Pagina vernieuwen/naar een andere pagina navigeren en terugkeren (JSP voor side rail moet opnieuw worden samengesteld)</p> <p>Als dat niet werkt:</p>
    <ul>
     <li>Publish asset.</li>
     <li>Elementen opnieuw laden en publiceren.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>De kiezer van het element in de seteditor is vastgelopen tijdens ononderbroken laden</td>
   <td><p>Bekend probleem dat in 6.4 moet worden opgelost</p> </td>
   <td><p>Sluit de kiezer en open deze opnieuw.</p> </td>
  </tr>
  <tr>
   <td><strong> Uitgezochte </strong> knoop is niet actief na het selecteren van activa als deel van het uitgeven van een reeks</td>
   <td><p> </p> <p>Bekend probleem dat in 6.4 moet worden opgelost</p> <p> </p> </td>
   <td><p>Selecteer eerst een andere map in de Asset Selector en ga terug om het element te selecteren.</p> </td>
  </tr>
  <tr>
   <td>De carrouselhotspot beweegt zich rond na het schakelen tussen dia's</td>
   <td><p>Controleer of alle dia's even groot zijn.</p> </td>
   <td><p>Gebruik voor de carrousel alleen afbeeldingen met dezelfde grootte.</p> </td>
  </tr>
  <tr>
   <td>De afbeelding wordt niet voorvertoond met de Dynamic Media-viewer</td>
   <td><p>Controleer of het element <code>dam:scene7File</code> bevat in de eigenschappen van metagegevens (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>Geüpload element wordt niet weergegeven in elementkiezer</td>
   <td><p>Element controleren heeft eigenschap <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>De banner op kaartmening toont <strong> Nieuw </strong> wanneer de activa niet begonnen zijn met verwerking</td>
   <td>Selecteer element <code>jcr:content</code> &gt; <code>dam:assetState</code> = als <code>unprocessed</code> het niet is opgepikt door de workflow.</td>
   <td>Wacht tot asset is opgehaald via workflow.</td>
  </tr>
  <tr>
   <td>In afbeeldingen of sets wordt de URL van de viewer of de insluitcode niet weergegeven</td>
   <td>Controleer of de viewervoorinstelling is gepubliceerd.</td>
   <td><p>Ga naar <strong> Hulpmiddelen </strong> &gt; <strong> Assets </strong> &gt; <strong> de Kijker stelt </strong> vooraf in en publiceert de kijker vooraf ingestelde.</p> </td>
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
     <li>Videoprofiel moet meer dan één coderingsvoorinstelling bevatten om een AVS-set te genereren (afzonderlijke coderingen worden behandeld als video-inhoud voor MP4-bestanden; voor niet-ondersteunde bestanden wordt deze voorinstelling op dezelfde manier behandeld als niet-verwerkte bestanden).</li>
     <li>Controleer of de video is verwerkt door <code>dam:scene7FileAvs</code> van <code>dam:scene7File</code> in metagegevens te bevestigen.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Wijs een videoprofiel toe aan de map.</li>
     <li>Bewerk het videoprofiel om meerdere coderingsvoorinstellingen op te nemen.</li>
     <li>Wacht tot de video is verwerkt.</li>
     <li>Als u de video opnieuw laadt, zorg ervoor dat de Dynamic Media Encode Video werkschema niet loopt.<br /> </li>
     <li>Laad de video opnieuw.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Video is niet gecodeerd</td>
   <td>
    <ul>
     <li>Controleer of de uitvoermodus <code>dynamicmedia_scene7</code> is.</li>
     <li>Controleer of Dynamic Media-cloudservice is geconfigureerd.</li>
     <li>Controleer of een videoprofiel is gekoppeld aan de uploadmap.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Controleer de Experience Manager-instantie met <code>-r dynamicmedia_scene7</code></li>
     <li>Controleer of de Dynamic Media Configuration onder Cloud Servicen correct is ingesteld.</li>
     <li>Controleer of de map een videoprofiel heeft. Controleer ook het videoprofiel.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Videoverwerking duurt te lang</td>
   <td><p>U kunt als volgt bepalen of videocodering nog wordt uitgevoerd of dat er een foutstatus is ingevoerd:</p>
    <ul>
     <li>Controleer de videostatus <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
     <li>Controleer de video via de workflowconsole <code>https://localhost:4502/libs/cq/workflow/content/console.html</code> &gt; Tabbladen Instanties, Archiveren, Mislukken.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Video-uitvoering ontbreekt</td>
   <td><p>Wanneer video wordt geüpload, maar er geen gecodeerde vertoningen zijn:</p>
    <ul>
     <li>Controleer of aan de map een videoprofiel is toegewezen.</li>
     <li>Controleer of de video is verwerkt door <code>dam:scene7FileAvs</code> in metagegevens te bevestigen.</li>
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

### Probleem: viewervoorinstellingen worden niet gepubliceerd {#viewers-not-published}

**hoe te om** te zuiveren

1. Ga naar diagnostische pagina voor voorbeeldbeheer: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html` .
1. Bekijk berekende waarden. Wanneer u correct werkt, ziet u het volgende: `_DMSAMPLE status: 0 unsyced assets - activation not necessary _OOTB status: 0 unsyced assets - 0 unactivated assets` .

   >[!NOTE]
   >
   >Het kan ongeveer 10 minuten duren nadat de Dynamic Media-cloudinstellingen zijn geconfigureerd voor synchronisatie van de viewerelementen.

1. Als de niet-geactiveerde activa blijven, selecteer één van beide **Lijst alle Unactivated knopen van Assets** om details te zien.

**Oplossing**

1. Navigeer naar de lijst met voorinstellingen voor viewers in beheergereedschappen: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`
1. Selecteer alle kijker vooraf instelt, dan uitgezochte **Publish**.
1. Navigeer terug naar voorbeeldbeheer en controleer of het aantal niet-geactiveerde elementen nu nul is.

### Probleem: met vooraf ingestelde illustraties van de viewer wordt 404 geretourneerd vanuit Voorvertoning in gegevens over elementen of via URL kopiëren/code insluiten {#viewer-preset-404}

**hoe te om** te zuiveren

Ga als volgt te werk bij CRXDE Lite:

1. Navigeer naar de map `<sync-folder>/_CSS/_OOTB` in de Dynamic Media-synchronisatiemap (bijvoorbeeld `/content/dam/_CSS/_OOTB` ).
1. Zoek het metagegevensknooppunt van het problematische element (bijvoorbeeld `<sync-folder>/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/` ).
1. Controleer op de aanwezigheid van `dam:scene7*` -eigenschappen. Als de activa met succes werden gesynchroniseerd en gepubliceerd, ziet u `dam:scene7FileStatus` reeks is aan **PublishComplete**.
1. Poging om de illustratie rechtstreeks via Dynasmic Media aan te vragen door de waarden van de volgende eigenschappen en letterlijke tekenreeksen samen te voegen:

   * `dam:scene7Domain`
   * `"is/content"`
   * `dam:scene7Folder`
   * `<asset-name>`
Voorbeeld: `https://<server>/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png`

**Oplossing**

Als de voorbeeldbestanden of de vooraf ingestelde illustratie van de viewer niet zijn gesynchroniseerd of gepubliceerd, start u het gehele kopiëren/synchronisatieproces opnieuw:

1. Navigeer naar CRXDE Lite.
1. Verwijderen `<sync-folder>/_CSS/_OOTB` .
1. Ga naar CRX Package Manager: `https://localhost:4502/crx/packmgr/` .
1. Zoeken naar een viewerpakket in de lijst; het begint met `cq-dam-scene7-viewers-content` .
1. Selecteer **opnieuw installeren**.
1. Onder Cloud Servicen, navigeer aan de pagina van de Configuratie van Dynamic Media, dan open de doos van de configuratiedialoog voor uw configuratie Dynamic Media - S7.
1. Breng geen veranderingen aan, uitgezocht **sparen**.
Deze opslaghandeling activeert de logica opnieuw om de voorbeeldelementen, de CSS met voorinstellingen voor viewers en de illustraties te maken en te synchroniseren.

### Probleem: Voorvertoning van afbeelding wordt niet geladen in ontwerpvoorinstellingen van viewer {#image-preview-not-loading}

**Oplossing**

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]** .
1. Navigeer in de linkertrack naar de map met voorbeeldinhoud op de volgende locatie:

   `/content/dam/_DMSAMPLE`

1. Verwijder de map `_DMSAMPLE` .
1. Navigeer in de linkertrack naar de map met voorinstellingen op de volgende locatie:

   `/conf/global/settings/dam/dm/presets/viewer`

1. Verwijder de map `viewer` .
1. Selecteer **[!UICONTROL Save All]** in de linkerbovenhoek van de pagina CRXDE Lite.
1. In de upper-left hoek van de pagina van de CRXDE Lite, selecteer het **Terug Home** pictogram.
1. Maak de Configuratie van a [&#x200B; Dynamic Media in Cloud Servicen &#x200B;](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) opnieuw.
