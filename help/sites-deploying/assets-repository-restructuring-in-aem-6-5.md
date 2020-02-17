---
title: Herstructurering van activa Bewaarinstelling in AEM 6.5
seo-title: Herstructurering van activa Bewaarinstelling in AEM 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe opslagplaats in AEM 6.5 for Assets.
seo-description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe opslagplaats in AEM 6.5 for Assets.
uuid: 0e3d8163-6274-4d1b-91c7-32ca927fb83c
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 212930fc-3430-4a0a-842c-2fb613ef981f
translation-type: tm+mt
source-git-commit: d20ddba254c965e1b0c0fc84a482b7e89d4df5cb

---


# Herstructurering van activa Bewaarinstelling in AEM 6.5 {#assets-repository-restructuring-in-aem}

Zoals beschreven op de pagina &quot;parent [Repository Herstructurering&quot; in AEM 6.5](/help/sites-deploying/repository-restructuring.md) zouden klanten die een upgrade naar AEM 6.5 uitvoeren, deze pagina moeten gebruiken om de werkinspanning te beoordelen die gepaard gaat met wijzigingen in de opslagplaats die van invloed zijn op de AEM Assets Solution. Sommige veranderingen vereisen werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**Met 6,5-upgrade**

* [Dic](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#misc)

**Voorafgaand aan toekomstige upgrade**

* [E-mailmeldingssjabloon voor element-/verzamelingsgebeurtenis](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#asset-collection-event-e-mail-notification-template)
* [Klassieke elementen delen](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#classic-asset-share-designs)
* [E-mailmeldingssjabloon voor middelen downloaden](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#download-asset-e-mail-notification-template)
* [Voorbeeld-DRM-licenties](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#example-drm-licenses)
* [E-mailmeldingssjabloon voor delen van koppeling](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#link-share-e-mail-notification-template)
* [InDesign-workflowscripts](/help/sites-deploying/assets-repository-restructuring-in-aem-6-5.md#indesign-workflow-scripts)
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
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td>/var/dam/job</td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als een aangepaste code afhankelijk is van deze locatie (dat wil zeggen: de code baseert zich uitdrukkelijk op dit weg) dan moet de code worden bijgewerkt om de nieuwe plaats te gebruiken alvorens te bevorderen; In het ideale geval worden Java-API's gebruikt wanneer deze beschikbaar zijn om afhankelijkheden van een specifiek pad in de JCR te verminderen.</p> <p>Tijdelijke locatie om ZIP-bestand op te slaan zodat de client het kan downloaden. Er hoeft geen update te worden uitgevoerd omdat de client het element wil downloaden. Er wordt een bestand op de nieuwe locatie gegenereerd.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

## Voorafgaand aan toekomstige upgrade {#prior-to-upgrade}

### E-mailmeldingssjabloon voor element-/verzamelingsgebeurtenis {#asset-collection-event-e-mail-notification-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/notification/email/default</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/dam/notification</code></p> <p><code>/apps/settings/dam/notification</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als de e-mailsjablonen door de klant zijn gewijzigd, voert u de volgende handelingen uit om deze uit te lijnen op de nieuwe repository structuur:</p>
    <ol>
     <li>De <code>/libs/settings/dam/notification</code> e-mailsjabloon moet worden gekopieerd van <strong><code>/etc/notification/email/default</code></strong> naar <strong><code>/apps/settings/notification/email/default</code></strong>
      <ol>
       <li>Omdat de bestemming in<strong> deze verandering is zou <code>/apps</code></strong> in SCM moeten worden voortgeduurd.</li>
      </ol> </li>
     <li>De map verwijderen: <strong><code>/etc/dam/notification/email/default</code></strong> nadat de e-mailsjablonen in de sjablonen zijn verplaatst.<br />
      <ol>
       <li>Als de e-mailsjabloon onder<strong> geen updates heeft ontvangen, kan de map worden verwijderd omdat de oorspronkelijke e-mailsjabloon onder <code>/etc/notification/email/default</code></strong>AEM 4 <strong><code>/libs/settings/notification/email/default</code></strong> valt.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N/A<br /> </td>
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
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/wcm/designs/assetshare</code></p> <p><code>/apps/settings/wcm/designs/assetshare</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime via de Dialogen van het Ontwerp worden geschreven, voer de volgende acties uit om aan het recentste model te richten:</p>
    <ol>
     <li>Kopieer de ontwerpen van de vorige locatie naar de nieuwe locatie onder <code>/apps</code>.</li>
     <li>Alle CSS-, JavaScript- en statische bronnen in het ontwerp converteren naar een <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">clientbibliotheek</a> met <code>allowProxy = true</code>.</li>
     <li>Verwijzingen naar de vorige locatie in de <code>cq:designPath</code> eigenschap bijwerken via <strong>AEM &gt; DAM Admin &gt; Pagina-eigenschappen voor delen van element &gt; tabblad Geavanceerd &gt; Ontwerpveld</strong>.</li>
     <li>Werk pagina's bij die naar de vorige locatie verwijzen om de nieuwe categorie Clientbibliotheek te gebruiken. Hiervoor moet de code voor pagina-implementatie worden bijgewerkt.</li>
     <li>Werk de regels van de Verzender bij om het dienen van de Bibliotheken van de Cliënt via <code>/etc.clientlibs/</code> volmachtsservlet toe te staan.</li>
    </ol> <p>Voor om het even welke Ontwerpen die niet in SCM, en gewijzigde runtime via de Dialogen van het Ontwerp worden beheerd, verplaats geen authorable ontwerpen uit <code>/etc</code>.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N/A<br /> </td>
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
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/dam/workflownotification/email/downloadasset</code></p> <p><code>/apps/settings/dam/workflownotification/email/downloadasset</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als de e-mailsjablonen (<strong>downloadmiddel</strong> of <strong>transientworkflow voltooid</strong>) zijn gewijzigd, volgt u de onderstaande procedure om deze uit te lijnen op de nieuwe structuur:</p>
    <ol>
     <li>De bijgewerkte e-mailsjabloon moet worden gekopieerd van <strong><code>/etc/dam/workflow/notification/email/downloadasset</code></strong> naar <strong><code>/apps/settings/dam/workflow/notification/email/downloadasset</code></strong>
      <ol>
       <li>Omdat de bestemming in<strong> deze verandering is zou <code>/apps</code></strong> in SCM moeten worden voortgeduurd.</li>
      </ol> </li>
     <li>De map verwijderen: <code>/etc/dam/workflow/notification/email/downloadasset </code>nadat de e-mailsjablonen in de sjablonen zijn verplaatst.<br />
      <ol>
       <li>Als de e-mailsjabloon onder<strong> geen updates heeft ontvangen, kan de map worden verwijderd omdat de oorspronkelijke e-mailsjabloon onder <code>/etc</code></strong>AEM 6.4 <strong><code>/libs/settings/dam/workflownotification/email/downloadasset</code></strong> wordt geïnstalleerd.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>Terwijl <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code> technisch voor raadpleging (neemt belangrijkheid vóór /apps via het gebruikelijke Sling CAConfig raadplegingsup, maar na <code>/etc</code>) het malplaatje zou kunnen worden geplaatst in <code>/conf/global/settings/dam/workflownotification/email/downloadasset</code>. Dit wordt echter niet aanbevolen omdat er geen runtime-interface is om het bewerken van de e-mailsjabloon te vergemakkelijken.</td>
  </tr>
 </tbody>
</table>

### Voorbeeld-DRM-licenties {#example-drm-licenses}

| **Vorige locatie** | `/etc/dam/drm/licenses/` |
|---|---|
| **Nieuwe locatie(s)** | `/libs/settings/dam/drm` |
| **Herstructureringsrichtsnoeren** | N.v.t. |
| **Opmerkingen** | N.v.t. |

### E-mailmeldingssjabloon voor delen van koppeling {#link-share-e-mail-notification-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/adhocassetshare</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/dam/adhocassetshare</code></p> <p><code>/apps/settings/dam/adhocassetshare</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als het e-mailmalplaatje door de klant werd gewijzigd, dan om zich aan de nieuwe bewaarplaatsstructuur te richten:</p>
    <ol>
     <li>De bijgewerkte e-mailsjabloon moet worden gekopieerd van <strong><code>/etc/dam/adhocassetshare</code></strong> naar <strong><code>/apps/settings/dam/adhocassetshare</code></strong>
      <ol>
       <li>Omdat de bestemming in<strong> deze verandering is zou <code>/apps</code></strong> in SCM moeten worden voortgeduurd.</li>
      </ol> </li>
     <li>De map verwijderen: <strong><code>/etc/dam/adhocassetshare</code></strong> nadat de e-mailsjablonen in de sjablonen zijn verplaatst.<br />
      <ol>
       <li>Als de e-mailsjabloon onder<strong> geen updates heeft ontvangen, kan de map worden verwijderd omdat de oorspronkelijke e-mailsjabloon onder <code>/etc</code></strong>AEM 6.4 <strong><code>/libs/settings/dam/adhocassetshare</code></strong> wordt geïnstalleerd.</li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>Terwijl <code>/conf/global/settings/dam/adhocassetshare</code> technisch voor raadpleging (het neemt belangrijkheid vóór <code>/apps</code> via het gebruikelijke Sling CAConfig raadpleging, maar na <code>/etc</code>) wordt gesteund, kan het malplaatje worden geplaatst in <code>/conf/global/settings/dam/adhocassetshare</code>. Dit wordt echter niet aanbevolen omdat er geen runtime-interface is om het bewerken van de e-mailsjabloon te vergemakkelijken</td>
  </tr>
 </tbody>
</table>

### InDesign-workflowscripts {#indesign-workflow-scripts}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dam/indesign/scripts</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/dam/indesign</code></p> <p><code>/apps/settings/dam/indesign</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Uitlijnen met de nieuwe repository structuur:</p>
    <ol>
     <li>Alle aangepaste of gewijzigde scripts kopiëren van <strong><code>/etc/dam/indesign/scripts</code></strong> naar <strong><code>/apps/settings/dam/indesign/scripts</code></strong><br />
      <ol>
       <li>Alleen nieuwe of gewijzigde scripts als ongewijzigde scripts die door AEM worden aangeboden, zijn beschikbaar via <strong><code>/libs/settings</code></strong> AEM 6.5</li>
      </ol> </li>
     <li>Zoek alle workflowmodellen die gebruikmaken van de Media Extraction Process WF Step en
      <ol>
       <li>Voor elke instantie van de Stap van het Werkschema, werk de wegen in config bij om uitdrukkelijk bij de juiste manuscripten onder<strong> of <code>/apps/settings/dam/indesign/scripts</code></strong> <strong><code>/libs/settings/dam/indesign/scripts</code></strong> zoals aangewezen te richten.</li>
      </ol> </li>
     <li>Volledig verwijderen<strong> <code>/etc/dam/indesign/scripts</code></strong> .</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>Het wordt aanbevolen aangepaste scripts onder op te slaan, <code>/apps</code>omdat dat de locatie is waar code moet worden opgeslagen.</td>
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
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/dam/video</code></p> <p><code>/apps/settings/dam/video</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Aanpassingen op projectniveau moeten worden geknipt en geplakt onder gelijkwaardige <code>/apps</code> of <code>/conf</code> paden, naargelang het geval.</p> <p>Uitlijnen op de AEM 6.4-opslagstructuur:</p>
    <ol>
     <li>Gewijzigde videoconfiguraties kopiëren van <code>/etc/dam/video</code> naar <code>/apps/settings/dam/video</code></li>
     <li>Verwijderen <code>/etc/dam/video</code></li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
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
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/dam/dm/presets/viewer</code></p> <p><code>/conf/global/settings/dam/dm/presets/viewer</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor de voorinstelling van de buitenste viewer is deze alleen beschikbaar op de nieuwe locatie.</p> <p>Voor de voorinstelling Aangepaste viewer:</p>
    <ul>
     <li>u zult een migratiescript moeten in werking stellen om de knoop van <code>/etc</code> naar <code>/conf</code>te bewegen. Het script bevindt zich op <em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
     <li>of u kunt de configuratie bewerken en deze worden automatisch opgeslagen op de nieuwe locatie.</li>
    </ul> <p>Merk op dat u hun copyURL/embed code niet moet aanpassen om aan te wijzen <code>/conf</code>. Het bestaande verzoek aan <code>/etc</code> zal aan de correcte inhoud van worden opnieuw verpletterd <code>/conf</code>.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
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
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/dam/clientlibs</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Pas om het even welke verwijzingen aan punt aan de nieuwe middelen onder <code>/libs</code> het gebruiken van toe <code>/etc.clientlibs/</code> staan volmachtsprefix.</p> <p>Tot slot kunt u het bestand opschonen door de mappen voor de gemigreerde clientlibs te verwijderen <code>/etc/clientlibs/foundation/</code></p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N/A<br /> </td>
  </tr>
 </tbody>
</table>

