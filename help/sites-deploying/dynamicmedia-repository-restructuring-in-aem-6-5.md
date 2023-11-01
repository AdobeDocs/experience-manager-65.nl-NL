---
title: Herstructurering van Dynamic Media-opslagplaats in Adobe Experience Manager 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe repository structuur in Experience Manager 6.5 voor Dynamic Media.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: 4e736924-74ea-431a-be19-1c4ff022f464
source-git-commit: 1807919078996b1cf1cbd1f2d90c3b14cb660e2c
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Herstructurering van Dynamic Media-opslagplaats in Adobe Experience Manager 6.5 {#dynamic-media-repository-restructuring-in-aem}

Zoals beschreven op het bovenliggende element [Herstructurering van de depositaris in Adobe Experience Manager 6.5](/help/sites-deploying/repository-restructuring.md) op de pagina, moeten klanten die een upgrade uitvoeren naar Experience Manager 6.5 deze pagina gebruiken om de werkinspanning te beoordelen die gepaard gaat met wijzigingen in de opslagplaats die gevolgen hebben voor Dynamic Media. Sommige veranderingen vereisen het werk inspanning tijdens het Experience Manager 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**Voor toekomstige upgrade**

* [Aangepaste configuraties voor adaptieve videocodering](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#custom-adaptive-video-encoding-configurations)
* [Dynamic Media (DMS7) Cloud Configuration](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#dynamic-media-dms-cloud-configuration)
* [Configuratie van Dynamic Media (DM Hybrid)-Cloud Service](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#cloudserviceconfiguration)
* [Dynamic Media - YouTube Cloud Service Configuration](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#youtubecloudserviceconfiguration)
* [Dic](/help/sites-deploying/dynamicmedia-repository-restructuring-in-aem-6-5.md#misc)

## Voor toekomstige upgrade {#prior-to-upgrade}

### Aangepaste configuraties voor adaptieve videocodering  {#custom-adaptive-video-encoding-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/video/dynamicmedia</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locaties</strong></td>
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>U kunt het volgende migratiescript in werking stellen om aan de nieuwe plaats te migreren:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>U kunt de configuratie ook bewerken in de gebruikersinterface van de Experience Manager en de wijzigingen worden opgeslagen op de nieuwe locatie.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media (DMS7) Cloud-configuratie {#dynamic-media-dms-cloud-configuration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/dmscene7</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locaties</strong></td>
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>De klant kan een migratiescript bij deze plaats in werking stellen:<br /> </p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
     <li>Start de Dynamic Media OSGi-bundel opnieuw.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT</td>
  </tr>
 </tbody>
</table>

### Dynamic Media (DM Hybrid) configuratie van de Cloud Service {#cloudserviceconfiguration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locaties</strong></td>
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>U kunt het migratiescript hieronder in werking stellen om zich aan het recentste model te richten:</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.jso</em></p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Dynamic Media - configuratie YouTube-Cloud Service  {#youtubecloudserviceconfiguration}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/youtube</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locaties</strong></td>
   <td><code>/libs/settings/dam/dm/youtube</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>1. Publiceer alle video's van YouTube ongedaan<br /> 2. De YouTube-configuratie maken met de nieuwe TouchUI (van <code>/conf</code>) inclusief het kopiëren van alle kanalen van de oude locatie<br /> 3. Publiceer alle video's terug naar YouTube.</p> <p>Deze workflow resulteert in nieuwe YouTube-URL's. Als u de publicatie niet ongedaan maakt voordat u een TouchUI YouTube-config maakt, worden onder Eigenschappen meerdere YouTube-URL's weergegeven, omdat de opnieuw gemaakte kanalen opnieuw worden gepubliceerd, als dit de kans is. Deze functionaliteit houdt in dat u nutteloze URL's hebt die onder Eigenschappen worden vermeld.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Dic {#misc}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/imageserver/macros</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locaties</strong></td>
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>De klant kan het onderstaande migratiescript uitvoeren.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p>U kunt de configuratie ook bewerken in de gebruikersinterface van de Experience Manager en de wijzigingen worden opgeslagen op de nieuwe locatie.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT</td>
  </tr>
 </tbody>
</table>

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/presets/analytics</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locaties</strong></td>
   <td><code>/libs/settings/dam/dm/analytics</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>De klant kan het onderstaande migratiescript uitvoeren.</p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT</td>
  </tr>
 </tbody>
</table>
