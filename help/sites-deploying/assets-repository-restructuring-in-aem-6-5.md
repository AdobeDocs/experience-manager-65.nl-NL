---
title: Assets Repositoregeling Herstructurering in AEM 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe repository structuur in Adobe Experience Manager (AEM) 6.5 voor Assets.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: 28ddd23c-5907-4356-af56-ebc7589a2b5d
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 0%

---

# Assets Repositoregeling Herstructurering in AEM 6.5 {#assets-repository-restructuring-in-aem}

Zoals die op de ouder [&#x200B; Herstructurering van de Bewaarplaats in AEM 6.5 &#x200B;](/help/sites-deploying/repository-restructuring.md) pagina wordt beschreven, zouden de klanten die aan Adobe Experience Manager (AEM) 6.5 bevorderen deze pagina moeten gebruiken om de het werkinspanning te beoordelen verbonden aan bewaarplaatsveranderingen die de Oplossing van AEM Assets beïnvloeden. Sommige veranderingen vereisen het werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**met 6.5 Verbetering**

* [Dic](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#misc)

**vóór Toekomstige Verbetering**

* [E-mailmeldingssjabloon voor element-/verzamelingsgebeurtenis](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#asset-collection-event-e-mail-notification-template)
* [Klassieke elementen delen](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#classic-asset-share-designs)
* [E-mailmeldingssjabloon voor middelen downloaden](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#download-asset-e-mail-notification-template)
* [Voorbeeld-DRM-licenties](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#example-drm-licenses)
* [E-mailmeldingssjabloon voor delen van koppeling](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#link-share-e-mail-notification-template)
* [Workflowscripts voor InDesign](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#indesign-workflow-scripts)
* [Configuraties voor videotransformatie](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#video-transcoding-configurations)
* [Dic](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#misc2)

## Met 6,5-upgrade {#with-upgrade}

### Dic {#misc}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td>/etc/dam/job</td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td>/var/dam/job</td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als om het even welke douanecode van deze plaats-dat afhangt, baseert de code zich uitdrukkelijk op dit weg-dan moet de code worden bijgewerkt om de nieuwe plaats te gebruiken alvorens te bevorderen. In het ideale geval worden Java™ API's gebruikt wanneer deze beschikbaar zijn om afhankelijkheden van een specifiek pad in de JCR te verminderen.</p> <p>Tijdelijke locatie voor het bewaren van een ZIP-bestand dat de client moet downloaden. Er hoeft geen update te worden uitgevoerd omdat de client het element wil downloaden. Er wordt een bestand op de nieuwe locatie gegenereerd.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT</td>
  </tr>
 </tbody>
</table>

## Voor toekomstige upgrade {#prior-to-upgrade}

### E-mailmeldingssjabloon voor element-/verzamelingsgebeurtenis {#asset-collection-event-e-mail-notification-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/notification/email/default</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code>/libs/settings/dam/notification</code></p> <p><code>/apps/settings/dam/notification</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als de e-mailsjablonen door de klant zijn gewijzigd, voert u de volgende handelingen uit om deze uit te lijnen met de nieuwe repository-structuur:</p>
    <ol>
     <li>De <code>/libs/settings/dam/notification</code> e-mailsjabloon moet worden gekopieerd van <strong><code>/etc/notification/email/default</code></strong> naar <strong><code>/apps/settings/notification/email/default</code></strong>
      <ol>
       <li>Omdat de bestemming in <strong> <code>/apps</code></strong> is, zou deze verandering in SCM moeten worden voortgeduurd.</li>
      </ol> </li>
     <li>Verwijder de map: <strong><code>/etc/dam/notification/email/default</code></strong> nadat de e-mailsjablonen in de map zijn verplaatst.<br />
      <ol>
       <li>Als de e-mailsjabloon niet is bijgewerkt onder <strong> <code>/etc/notification/email/default</code></strong> , kan de map worden verwijderd omdat de oorspronkelijke e-mailsjabloon onder <strong><code>/libs/settings/notification/email/default</code></strong> staat als onderdeel van AEM 4-installatie.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>N.v.t. <br /> </td>
  </tr>
 </tbody>
</table>

### Klassieke elementen delen {#classic-asset-share-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/assetshare</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code>/libs/settings/wcm/designs/assetshare</code></p> <p><code>/apps/settings/wcm/designs/assetshare</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime als Dialogen van het Ontwerp worden geschreven, voer de volgende acties uit om aan het recentste model te richten:</p>
    <ol>
     <li>Kopieer de ontwerpen van de vorige locatie naar de nieuwe locatie onder <code>/apps</code> .</li>
     <li>Converteer om het even welke CSS, JavaScript, en statische middelen in het Ontwerp in de Bibliotheek van de a <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank"> Cliënt </a> met <code>allowProxy = true</code>.</li>
     <li>De verwijzingen van de update naar de Vorige Plaats in het <code>cq:designPath</code> bezit door als <strong> AEM &gt; Admin DAM &gt; de Pagina van het Aandeel van Activa &gt; de Eigenschappen van de Pagina &gt; Geavanceerd Lusje &gt; het Gebied van het Ontwerp </strong>.</li>
     <li>Als u de nieuwe categorie Clientbibliotheek wilt gebruiken, werkt u de pagina's bij die naar de vorige locatie verwijzen. Hiervoor moet de code voor pagina-implementatie worden bijgewerkt.</li>
     <li>Werk de Dispatcher-regels bij, zodat u het gebruik van clientbibliotheken via het proxyservlet van <code>/etc.clientlibs/</code> kunt toestaan.</li>
    </ol> <p>Voor om het even welke Ontwerpen die niet in SCM, en gewijzigde runtime door de Dialogen van het Ontwerp worden beheerd, beweeg authorable ontwerpen niet uit <code>/etc</code>.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>N.v.t. <br /> </td>
  </tr>
 </tbody>
</table>

### E-mailmeldingssjabloon voor middelen downloaden {#download-asset-e-mail-notification-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/workflow/notification/email/downloadasset</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code>/libs/settings/dam/workflownotification/email/downloadasset</code></p> <p><code>/apps/settings/dam/workflownotification/email/downloadasset</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als de e-mailmalplaatjes (<strong> downloadasset </strong> of <strong> transientworkflowcompleted </strong>) zijn gewijzigd, dan volg de hieronder procedure om aan de nieuwe structuur te richten:</p>
    <ol>
     <li>De bijgewerkte e-mailsjabloon moet worden gekopieerd van <strong><code>/etc/dam/workflow/notification/email/downloadasset</code></strong> naar <strong><code>/apps/settings/dam/workflow/notification/email/downloadasset</code></strong>
      <ol>
       <li>Omdat de bestemming in <strong> <code>/apps</code></strong> is, zou deze verandering in SCM moeten worden voortgeduurd.</li>
      </ol> </li>
     <li>Verwijder de omslag: <code>/etc/dam/workflow/notification/email/downloadasset </code> nadat de e-mailmalplaatjes binnen het zijn bewogen.<br />
      <ol>
       <li>Als de e-mailsjabloon niet is bijgewerkt onder <strong> <code>/etc</code></strong> , kan de map worden verwijderd omdat de oorspronkelijke e-mailsjabloon onder <strong><code>/libs/settings/dam/workflownotification/email/downloadasset</code></strong> staat als onderdeel van AEM 6.4-installatie.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>Hoewel <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> technisch wordt ondersteund voor opzoeken (heeft voorrang vóór /apps als gebruikelijke opzoekopdracht voor Sling CAConfig, maar na <code>/etc</code> ), kan de sjabloon in <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> worden geplaatst. Dit wordt echter niet aanbevolen omdat er geen runtime-interface is om het bewerken van de e-mailsjabloon te vergemakkelijken.</td>
  </tr>
 </tbody>
</table>

### Voorbeeld-DRM-licenties {#example-drm-licenses}

| **Vorige plaats** | `/etc/dam/drm/licenses/` |
|---|---|
| **Nieuwe plaats(en)** | `/libs/settings/dam/drm` |
| **begeleiding van de Herstructurering** | NVT |
| **Nota&#39;s** | NVT |

### E-mailmeldingssjabloon voor delen van koppeling {#link-share-e-mail-notification-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/adhocassetshare</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code>/libs/settings/dam/adhocassetshare</code></p> <p><code>/apps/settings/dam/adhocassetshare</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als het e-mailmalplaatje door de klant werd gewijzigd, dan om zich aan de nieuwe bewaarplaatsstructuur te richten:</p>
    <ol>
     <li>De bijgewerkte e-mailsjabloon moet worden gekopieerd van <strong><code>/etc/dam/adhocassetshare</code></strong> naar <strong><code>/apps/settings/dam/adhocassetshare</code></strong>
      <ol>
       <li>Omdat de bestemming in <strong><code>/apps</code></strong> is, zou deze verandering in SCM moeten worden voortgeduurd.</li>
      </ol> </li>
     <li>Verwijder de map: <strong><code>/etc/dam/adhocassetshare</code></strong> nadat de e-mailsjablonen in de map zijn verplaatst.<br />
      <ol>
       <li>Als de e-mailsjabloon niet is bijgewerkt onder <strong> <code>/etc</code></strong> , kan de map worden verwijderd omdat de oorspronkelijke e-mailsjabloon onder <strong><code>/libs/settings/dam/adhocassetshare</code></strong> staat als onderdeel van AEM 6.4-installatie.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>Hoewel <code>/conf/global/settings/dam/adhocassetshare</code> technisch wordt ondersteund voor opzoeken (het heeft voorrang voor <code>/apps</code> via de gebruikelijke opzoekopdracht voor CAConfig, maar na <code>/etc</code> ), kan de sjabloon in <code>/conf/global/settings/dam/adhocassetshare</code> worden geplaatst. Dit wordt echter niet aanbevolen omdat er geen runtime-interface is om het bewerken van de e-mailsjabloon te vergemakkelijken</td>
  </tr>
 </tbody>
</table>

### Workflowscripts voor InDesign {#indesign-workflow-scripts}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/indesign/scripts</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code>/libs/settings/dam/indesign</code></p> <p><code>/apps/settings/dam/indesign</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Uitlijnen met de nieuwe repository structuur:</p>
    <ol>
     <li>Alle aangepaste of gewijzigde scripts van <strong><code>/etc/dam/indesign/scripts</code></strong> naar <strong><code>/apps/settings/dam/indesign/scripts</code></strong><br /> kopiëren
      <ol>
       <li>Alleen nieuwe of gewijzigde scripts kopiëren als ongewijzigde scripts die door AEM worden geleverd, zijn beschikbaar als <strong><code>/libs/settings</code></strong> in AEM 6.5</li>
      </ol> </li>
     <li>Zoek alle workflowmodellen die gebruikmaken van de Media Extraction Process WF Step en
      <ol>
       <li>Voor elke instantie van de Stap van de Werkstroom, werk de wegen in config bij om uitdrukkelijk bij de juiste manuscripten onder <strong> <code>/apps/settings/dam/indesign/scripts</code></strong> of <strong><code>/libs/settings/dam/indesign/scripts</code></strong> te richten zoals aangewezen.</li>
      </ol> </li>
     <li>Verwijder <strong> <code>/etc/dam/indesign/scripts</code></strong> volledig.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>Het wordt aanbevolen aangepaste scripts op te slaan onder <code>/apps</code> , omdat dat de locatie is waar code moet worden opgeslagen.</td>
  </tr>
 </tbody>
</table>

### Configuraties voor videotransformatie {#video-transcoding-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/video</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code>/libs/settings/dam/video</code></p> <p><code>/apps/settings/dam/video</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Aanpassingen op projectniveau moeten worden geknipt en geplakt onder gelijkwaardige <code>/apps</code> - of <code>/conf</code> -paden, al naar gelang van toepassing.</p> <p>Uitlijnen met de AEM 6.4-opslagruimtestructuur:</p>
    <ol>
     <li>Kopieer eventuele gewijzigde videoconfiguraties van <code>/etc/dam/video</code> naar <code>/apps/settings/dam/video</code></li>
     <li>Verwijderen <code>/etc/dam/video</code></li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT</td>
  </tr>
 </tbody>
</table>

### Configuraties van voorinstellingen van viewer {#viewer-preset-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/presets/viewer</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code>/libs/settings/dam/dm/presets/viewer</code></p> <p><code>/conf/global/settings/dam/dm/presets/viewer</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor de voorinstelling van de buitenste viewer is deze alleen beschikbaar op de nieuwe locatie.</p> <p>Voor de voorinstelling Aangepaste viewer:</p>
    <ul>
     <li>Voer een migratiescript uit zodat kunt u de knoop van <code>/etc</code> naar <code>/conf</code> bewegen. Het manuscript is in <em> https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
     <li>of u kunt de configuratie bewerken en deze worden automatisch opgeslagen op de nieuwe locatie.</li>
    </ul> <p>U hoeft de code copyURL/embed niet aan te passen om naar <code>/conf</code> te wijzen. De bestaande aanvraag naar <code>/etc</code> wordt vanuit <code>/conf</code> omgeleid naar de juiste inhoud.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT</td>
  </tr>
 </tbody>
</table>

### Dic {#misc2}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/clientlibs/foundation/asseteditor</code></p> <p><code>/etc/clientlibs/foundation/assetshare</code></p> <p><code>/etc/clientlibs/foundation/assetinsights</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><code>/libs/dam/clientlibs</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Pas verwijzingen naar punten naar de nieuwe bronnen onder <code>/libs</code> aan met het voorvoegsel van de proxy van <code>/etc.clientlibs/</code> toestaan.</p> <p>Tot slot kunt u het bestand opschonen door de mappen voor de gemigreerde clientlibs te verwijderen <code>/etc/clientlibs/foundation/</code></p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>N.v.t. <br /> </td>
  </tr>
 </tbody>
</table>
