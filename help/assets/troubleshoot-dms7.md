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

In het volgende document worden de problemen beschreven die optreden bij Dynamic Media **dynamicmedia_scene7** uitvoeringsmodus.

## Instellen en configureren {#setup-and-configuration}

Zorg ervoor dat Dynamic Media op de juiste wijze is ingesteld door het volgende te doen:

* Opstarten bevat de opdracht `-r dynamicmedia_scene7` argument voor uitvoermodus.
* Alle Adobe Experience Manager 6.4-pakketten met cumulatieve oplossingen (GFP&#39;s) zijn eerst geïnstalleerd *voor* alle beschikbare Dynamic Media Feature Packs.
* Optioneel Feature Pack 18912 is geïnstalleerd.

  Dit optionele functiepakket is bedoeld voor FTP-ondersteuning of als u middelen van Dynamic Media Classic naar Dynamic Media migreert.

* Navigeer naar de gebruikersinterface van Cloud Servicen en bevestig dat de provisioned account onder verschijnt **[!UICONTROL Available Configurations]**.
* Zorg ervoor dat de `Dynamic Media Asset Activation (scene7)` replicatieagent is ingeschakeld.

  Deze replicatieagent wordt gevonden onder Medewerkers op Auteur.

## Algemeen (alle activa) {#general-all-assets}

Hier volgen enkele algemene tips en trucs voor alle elementen.

### Eigenschappen voor de synchronisatie van bedrijfsmiddelen {#asset-synchronization-status-properties}

De volgende eigenschappen van elementen kunnen in CRXDE Lite worden gecontroleerd om te bevestigen dat het element correct is gesynchroniseerd van Experience Manager naar Dynamic Media:

| **Eigenschap** | **Voorbeeld** | **Beschrijving** |
|---|---|---|
| `<object_node>/jcr:content/metadata/dam:scene7ID` | **`a\|364266`** | Algemene indicator dat de knoop met Dynamic Media wordt verbonden. |
| `<object_node>/jcr:content/metadata/dam:scene7FileStatus` | **PublishComplete** of fouttekst | Status van het uploaden van middelen naar Dynamic Media. |
| `<object_node>/jcr:content/metadata/dam:scene7File` | **myCompany/myAssetID** | Moet zijn gevuld om URL&#39;s te genereren naar externe middelen van Dynamic Media. |
| `<object_node>/jcr:content/dam:lastSyncStatus` | **succes** of **mislukt:`<error text>`** | Synchronisatiestatus van sets (centrifuges, afbeeldingssets, enzovoort), voorinstellingen voor afbeeldingen, voorinstellingen voor viewers, updates van afbeeldingen met hyperlinks voor een element of afbeeldingen die zijn bewerkt. |

### Synchronisatie-logboekregistratie {#synchronization-logging}

Synchronisatiefouten en problemen worden aangemeld `error.log` (Servermap Experience Manager `/crx-quickstart/logs/`). Er is voldoende logboekregistratie beschikbaar om de hoofdoorzaak van de meeste problemen te bepalen, maar u kunt het logbestand voor DEBUG op het tabblad `com.adobe.cq.dam.ips` pakket maken via de Sling Console ([https://localhost:4502/system/console/slinglog](https://localhost:4502/system/console/slinglog)) om meer informatie te verzamelen.

### Verplaatsen, kopiëren, verwijderen {#move-copy-delete}

Voer de volgende handelingen uit voordat u een bewerking Verplaatsen, Kopiëren of Verwijderen uitvoert:

* Bevestig voor afbeeldingen en video&#39;s dat een `<object_node>/jcr:content/metadata/dam:scene7ID` Deze waarde bestaat voordat u bewerkingen voor verplaatsen, kopiëren of verwijderen uitvoert.
* Controleer voor voorinstellingen voor afbeeldingen en viewers of `https://<server>/crx/de/index.jsp#/etc/dam/presets/viewer/testpreset/jcr%3Acontent/metadata` Deze waarde bestaat voordat u bewerkingen voor verplaatsen, kopiëren of verwijderen uitvoert.
* Als de bovenstaande metagegevenswaarde ontbreekt, moet u de elementen opnieuw uploaden voordat u bewerkingen verplaatst, kopieert of verwijdert.

### Versiebeheer {#version-control}

Wanneer u een bestaand Dynamic Media-element vervangt (dezelfde naam en locatie), kunt u beide elementen behouden of een versie vervangen/maken:

* Als u beide instellingen behoudt, wordt een element gemaakt met een unieke naam voor de URL van het gepubliceerde element. Bijvoorbeeld: `image.jpg` het oorspronkelijke middel is en `image1.jpg` is het nieuw geüploade element.

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
       <li>Controleren of de voorinstelling in het JCR <code>/etc/dam/presets/viewer/&lt;preset&gt; has lastReplicationAction</code> gedefinieerd. Deze locatie is van toepassing als u een upgrade hebt uitgevoerd van Experience Manager 6.x naar 6.4 en de migratie hebt uitgeschakeld. Anders is de locatie <code>/conf/global/settings/dam/dm/presets/viewer</code>.</li>
       <li>Controleer of het element in de JCR <code>dam:scene7FileStatus</code><strong> </strong>onder Metagegevens wordt weergegeven als <code>PublishComplete</code>.</li>
      </ul> </li>
    </ol> </td>
   <td><p>Pagina vernieuwen/naar een andere pagina navigeren en terugkeren (JSP voor side rail moet opnieuw worden samengesteld)</p> <p>Als dat niet werkt:</p>
    <ul>
     <li>Middelen publiceren.</li>
     <li>Elementen opnieuw laden en publiceren.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>De kiezer van het element in de seteditor is vastgelopen tijdens ononderbroken laden</td>
   <td><p>Bekend probleem dat in 6.4 moet worden opgelost</p> </td>
   <td><p>Sluit de kiezer en open deze opnieuw.</p> </td>
  </tr>
  <tr>
   <td><strong>Selecteren</strong> De knop is niet actief nadat u een element hebt geselecteerd als onderdeel van het bewerken van een set</td>
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
   <td><p>Controleren of het element bevat <code>dam:scene7File</code> in de eigenschappen van metagegevens (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>Geüpload element wordt niet weergegeven in elementkiezer</td>
   <td><p>Element controleren heeft eigenschap <code>jcr:content</code> &gt; <strong><code>dam:assetState</code></strong> = <code>processed</code> (CRXDE Lite)</p> </td>
   <td><p>Controleer of alle elementen zijn verwerkt.</p> </td>
  </tr>
  <tr>
   <td>Banner op kaartpresentaties <strong>Nieuw</strong> wanneer de verwerking van het element niet is begonnen</td>
   <td>Element controleren <code>jcr:content</code> &gt; <code>dam:assetState</code> = if <code>unprocessed</code> het is niet opgepikt door de workflow.</td>
   <td>Wacht tot asset is opgehaald via workflow.</td>
  </tr>
  <tr>
   <td>In afbeeldingen of sets wordt de URL van de viewer of de insluitcode niet weergegeven</td>
   <td>Controleer of de viewervoorinstelling is gepubliceerd.</td>
   <td><p>Ga naar <strong>Gereedschappen</strong> &gt; <strong>Activa</strong> &gt; <strong>Voorinstellingen viewer</strong> en publiceert u de viewervoorinstelling.</p> </td>
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
     <li>Controleer of de video is verwerkt door te bevestigen <code>dam:scene7FileAvs</code> van <code>dam:scene7File</code> in metagegevens.</li>
    </ul> </td>
   <td>
    <ol>
     <li>Wijs een videoprofiel toe aan de map.</li>
     <li>Bewerk het videoprofiel om meerdere coderingsvoorinstellingen op te nemen.</li>
     <li>Wacht tot de video is verwerkt.</li>
     <li>Als u de video opnieuw laadt, moet u ervoor zorgen dat de Dynamic Media Encode Video-workflow niet wordt uitgevoerd.<br /> </li>
     <li>Laad de video opnieuw.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Video is niet gecodeerd</td>
   <td>
    <ul>
     <li>Controleer of de uitvoermodus <code>dynamicmedia_scene7</code>.</li>
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
     <li>De videostatus controleren <code>https://localhost:4502/crx/de/index.jsp#/content/dam/folder/videomp4/jcr%3Acontent</code> &gt; <code>dam:assetState</code></li>
     <li>De video controleren vanaf de workflowconsole <code>https://localhost:4502/libs/cq/workflow/content/console.html</code> &gt; Instanties, Archiveren, tabbladen mislukt.</li>
    </ul> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Video-uitvoering ontbreekt</td>
   <td><p>Wanneer video wordt geüpload, maar er geen gecodeerde vertoningen zijn:</p>
    <ul>
     <li>Controleer of aan de map een videoprofiel is toegewezen.</li>
     <li>Controleer of de video is verwerkt door te bevestigen <code>dam:scene7FileAvs</code> in metagegevens.</li>
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

**Foutopsporing**

1. Ga door naar de diagnostische pagina van de voorbeeldmanager: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`.
1. Bekijk berekende waarden. Wanneer correct werkend, ziet u het volgende: `_DMSAMPLE status: 0 unsyced assets - activation not necessary _OOTB status: 0 unsyced assets - 0 unactivated assets`.

   >[!NOTE]
   >
   >Het kan ongeveer 10 minuten duren nadat de Dynamic Media-cloudinstellingen zijn geconfigureerd voor synchronisatie van de viewerelementen.

1. Als er niet-geactiveerde elementen overblijven, selecteert u een van de **Alle niet-geactiveerde elementen weergeven** knoppen om details weer te geven.

**Oplossing**

1. Navigeer naar de lijst met voorinstellingen voor viewers in de beheerprogramma&#39;s: `https://localhost:4502/libs/dam/gui/content/s7dam/samplemanager/samplemanager.html`
1. Selecteer alle voorinstellingen van de viewer en selecteer **Publiceren**.
1. Navigeer terug naar voorbeeldbeheer en controleer of het aantal niet-geactiveerde elementen nu nul is.

### Probleem: met vooraf ingestelde illustraties van de viewer wordt 404 geretourneerd vanuit Voorvertoning in gegevens over elementen of via URL kopiëren/code insluiten {#viewer-preset-404}

**Foutopsporing**

Ga als volgt te werk bij CRXDE Lite:

1. Navigeren naar `<sync-folder>/_CSS/_OOTB` map in uw Dynamic Media-synchronisatiemap (bijvoorbeeld `/content/dam/_CSS/_OOTB`).
1. Zoek het metagegevensknooppunt van het problematische element (bijvoorbeeld `<sync-folder>/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png/jcr:content/metadata/`).
1. Controleren op de aanwezigheid van `dam:scene7*` eigenschappen. Als het element is gesynchroniseerd en gepubliceerd, ziet u de `dam:scene7FileStatus` set is to **PublishComplete**.
1. Poging om de illustratie rechtstreeks via Dynasmic Media aan te vragen door de waarden van de volgende eigenschappen en letterlijke tekenreeksen samen te voegen:

   * `dam:scene7Domain`
   * `"is/content"`
   * `dam:scene7Folder`
   * `<asset-name>`
Voorbeeld: `https://<server>/is/content/myfolder/_CSS/_OOTB/CarouselDotsLeftButton_dark_sprite.png`

**Oplossing**

Als de voorbeeldbestanden of de vooraf ingestelde illustratie van de viewer niet zijn gesynchroniseerd of gepubliceerd, start u het gehele kopiëren/synchronisatieproces opnieuw:

1. Navigeer naar CRXDE Lite.
1. Verwijderen `<sync-folder>/_CSS/_OOTB`.
1. Navigeer naar de CRX Package Manager: `https://localhost:4502/crx/packmgr/`.
1. Zoeken naar een viewerpakket in de lijst; het begint met `cq-dam-scene7-viewers-content`.
1. Selecteren **Opnieuw installeren**.
1. Onder Cloud Servicen, navigeer aan de pagina van de Configuratie van Dynamic Media, dan open de doos van de configuratiedialoog voor uw configuratie Dynamic Media - S7.
1. Geen wijzigingen aanbrengen, selecteer **Opslaan**.
Deze opslaghandeling activeert de logica opnieuw om de voorbeeldelementen, de CSS met voorinstellingen voor viewers en de illustraties te maken en te synchroniseren.

### Probleem: Voorvertoning van afbeelding wordt niet geladen in ontwerpvoorinstellingen van viewer {#image-preview-not-loading}

**Oplossing**

1. Selecteer in Experience Manager het logo van de Experience Manager voor toegang tot de algemene navigatieconsole en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]**.
1. Navigeer in de linkertrack naar de map met voorbeeldinhoud op de volgende locatie:

   `/content/dam/_DMSAMPLE`

1. Verwijder de `_DMSAMPLE` map.
1. Navigeer in de linkertrack naar de map met voorinstellingen op de volgende locatie:

   `/conf/global/settings/dam/dm/presets/viewer`

1. Verwijder de `viewer` map.
1. Selecteer in de linkerbovenhoek van de pagina CRXDE Lite de optie **[!UICONTROL Save All]**.
1. Selecteer in de linkerbovenhoek van de pagina CRXDE Lite de optie **Terug naar startpunt** pictogram.
1. Maak opnieuw een [Dynamic Media-configuratie in Cloud Servicen](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services).
