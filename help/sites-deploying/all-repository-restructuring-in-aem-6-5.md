---
title: Herstructurering van de gemeenschappelijke opslagplaats in AEM 6.5
seo-title: Herstructurering van de gemeenschappelijke opslagplaats in AEM 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe opslagstructuur in AEM 6.5 die algemeen gelden voor alle AEM.
seo-description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe opslagstructuur in AEM 6.5 die algemeen gelden voor alle AEM.
uuid: a4bb64e5-387b-4084-9258-54e68db12f3b
contentOwner: chaikels
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 80bd707f-c02d-4616-9b45-90f6c726abea
translation-type: tm+mt
source-git-commit: 8d6818d0f2d90482f930f8e98682670ed6d0dd28
workflow-type: tm+mt
source-wordcount: '2724'
ht-degree: 1%

---


# Herstructurering van de gemeenschappelijke opslagplaats in AEM 6.5 {#common-repository-restructuring-in-aem}

Zoals beschreven op de moederpagina [Herstructurering van opslagplaats in AEM 6.5](/help/sites-deploying/repository-restructuring.md), moeten klanten die een upgrade uitvoeren naar AEM 6.5 deze pagina gebruiken om de werkinspanning te beoordelen die gepaard gaat met wijzigingen in opslagplaatsen die mogelijk van invloed zijn op alle oplossingen. Sommige veranderingen vereisen het werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**Met 6,5-upgrade**

* [ContextHub-configuraties](#contexthub-6.5)
* [Workflowinstanties](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-instances)
* [Workflowmodellen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-models)
* [Workflowstartprogramma&#39;s](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-launchers)
* [Workflowscripts](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-scripts)

**Voorafgaand aan toekomstige upgrade**

* [ContextHub-configuraties](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#contexthub-configurations)
* [Klassieke Cloud Services ontwerpen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#classic-cloud-services-designs)
* [Klassieke dashboards ontwerpen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#classic-dashboards-designs)
* [Klassieke rapportontwerpen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#classic-reports-designs)
* [Standaardontwerpen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#default-designs)
* [Adobe DTM JavaScript-eindpunt](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#adobe-dtm-javascript-endpoint)
* [Adobe DTM Web-Hook Eindpunt](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#adobe-dtm-web-hook-endpoint)
* [Inbox-taken](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#inbox-tasks)
* [Configuraties van blauwdruk voor beheer op meerdere locaties](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#multi-site-manager-blueprint-configurations)
* [Gadget-configuraties AEM projecten](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#aem-projects-dashboard-gadget-configurations)
* [E-mailsjabloon voor replicatiemelding](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#replication-notification-e-mail-template)
* [Tags](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tags)
* [Cloud Services voor vertalingen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-cloud-services)
* [Talen voor vertaling](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-languages)
* [Vertaalregels](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-rules)
* [Widget-clientbibliotheek voor vertaling](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#translation-widget-client-library)
* [Webconsole voor activering van boomstructuur](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#tree-activation-web-console)
* [Cloud Services van leverancier-vertalingsconnector](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#vendor-translation-connector-cloud-services)
* [E-mailsjablonen voor workflowmeldingen](/help/sites-deploying/all-repository-restructuring-in-aem-6-5.md#workflow-notification-email-templates)

## Met 6.5-upgrade {#with-upgrade}

### ContextHub Configurations {#contexthub-6.5}

Vanaf AEM 6.4, is er geen standaardconfiguratie ContextHub. Daarom op het wortelniveau van de plaats zou een `cq:contextHubPathproperty` moeten worden geplaatst om te wijzen op welke configuratie zou moeten worden gebruikt.

1. Navigeer naar de hoofdmap van de site.
1. Open de pagina-eigenschappen van de basispagina en selecteer het tabblad Aanpassing.
1. Op het gebied van de Weg Contexthub ga uw eigen ContextHub configuratiepad in.

Bovendien op de configuratie ContextHub, moet `sling:resourceType` worden bijgewerkt om relatief en niet absoluut te zijn.

1. Open de eigenschappen van de ContextHub configuratieknooppunt in CRX DE Lite, bijvoorbeeld `/apps/settings/cloudsettings/legacy/contexthub`
1. Wijzigen `sling:resourceType` van `/libs/granite/contexthub/cloudsettings/components/baseconfiguration` in `granite/contexthub/cloudsettings/components/baseconfiguration`

D.w.z. `sling:resourceType` van de configuratie ContextHub moet relatief eerder dan absoluut zijn.

### Workflowmodellen {#workflow-models}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/workflow/models</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/workflow/models</code></p> <p><code>/conf/global/settings/workflow/models</code></p> <p><code>/var/workflow/models</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Nieuwe of gewijzigde workflowmodellen moeten worden gemigreerd naar /conf/global/workflow/modellen.</p>
    <ol>
     <li>Stel de gewijzigde Modellen van het Werkschema in een lokale AEM 6.5 ontwikkelingsinstantie op, zodat zij in de Vorige plaats bestaan.</li>
     <li>Bewerk het workflowmodel met AEM Workflow Model Editor op AEM &gt; Extra &gt; Workflow &gt; Modellen.</li>
     <li>Bij het migreren van aangepaste AEM-geleverde workflowmodellen
      <ol>
       <li>Met de open Redacteur van het Model van het Werkschema, wijzig het browser adres URL, en vervang het wegsegment /libs/settings/workflow/modellen met /etc/workflow/modellen.
        <ul>
         <li>Bijvoorbeeld: change: <em>http://localhost:4502/editor.html<strong>/libs/settings/workflow/models</strong>/dam/update_asset.html</em> naar <em>http://localhost:4502/editor.html<strong>/etc/workflow/models</strong>/dam/update_asset.html</em></li>
        </ul> </li>
      </ol> </li>
     <li>Schakel de modus Bewerken in de Workflowmodeleditor in, waarmee de definitie van het workflowmodel wordt gekopieerd naar /conf/global/workflow/models.</li>
     <li>Tik op de knop Sync om de wijzigingen in het workflowmodel voor uitvoering te synchroniseren onder /var/workflow/modellen.</li>
     <li>Exporteer zowel het workflowmodel (/conf/global/workflow/models/&lt;workflow-model&gt;) als het workflowmodel voor uitvoering (/var/workflow/models/&lt;workflow-model&gt;) en integreer het in het AEM project.
      <ol>
       <li>Bijvoorbeeld exporteren:
        <ul>
         <li><code>/config/settings/workflow/models/dam/my_workflow_model</code> and </li>
         <li><code>/var/workflow/models/dam/my_workflow_model</code></li>
        </ul> </li>
      </ol> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De oplossing van het workflowmodel vindt plaats in de volgende volgorde:</p>
    <ol>
     <li><code>/conf/global/settings/workflow/models</code></li>
     <li><code>/libs/settings/workflow/models</code></li>
     <li><code>/etc/workflow/models</code></li>
    </ol> <p>Daarom moeten om het even welke aanpassingen van AEM-verstrekte Modellen van het Werkschema die in de Vorige plaats worden voortgeduurd naar /conf/global/settings/workflow/modellen worden verplaatst als zij moeten worden behouden, anders zullen zij door de AEM-Verstrekte definitie van het Model van het Werkschema in /libs/settings/workflow/modellen worden vervangen.</p> </td>
  </tr>
 </tbody>
</table>

### Workflowinstanties {#workflow-instances}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/workflow/instances</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/var/workflow/instances</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Er is geen actie vereist om uit te lijnen met de nieuwe locatie.</p> <p>Historische Werkstroominstanties kunnen veilig blijven in de Vorige Plaats verblijven, en de nieuwe Instanties van het Werkschema zullen in de Nieuwe Plaats worden gecreeerd.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>Alle expliciete padverwijzingen in
    <code>
     custom
    </code> code aan de Vorige Plaats zou ook met de Nieuwe Plaats moeten rekening houden. Het wordt geadviseerd dat deze code refactored is om de AEM Werkstroom APIs te gebruiken.</td>
  </tr>
 </tbody>
</table>

### Workflow Launchers {#workflow-launchers}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/workflow/launcher/config</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/workflow/launcher/config</code></p> <p><code>/conf/global/settings/workflow/launcher/config</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Nieuwe of gewijzigde werkstroomopstarters moeten worden gemigreerd naar <code>/conf/global/workflow/launcher/config</code>.</p>
    <ol>
     <li>Kopieer om het even welke nieuwe of gewijzigde configuraties van de Lanceerinrichting van het Werkschema van de Vorige Plaats aan Nieuwe Plaats (<code>/conf/global</code>).</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De werkstroom starten wordt in de volgende volgorde opgelost:</p>
    <ol>
     <li><code>/conf/global/settings/workflow/launcher</code></li>
     <li><code>/libs/settings/workflow/launcher</code></li>
     <li><code>/etc/workflow/launcher</code></li>
    </ol> <p>Aldus, moeten om het even welke aanpassingen van AEM-Geleverde Startprogramma van het Werkschema in de Vorige plaats worden voortgeduurd naar de Nieuwe Plaats (<code>/conf/global/settings/workflow/launcher</code> als zij moeten worden behouden, anders zullen zij door de AEM-Geleverde definitie van de Lanceerinrichting van het Werkschema in <code>/libs/settings/workflow/launcher</code> worden vervangen.</p> </td>
  </tr>
 </tbody>
</table>

### Workflowscripts {#workflow-scripts}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/workflow/scripts</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/workflow/scripts</code></p> <p><code>/apps/workflow/scripts</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Nieuwe of gewijzigde workflowscripts moeten worden gemigreerd naar de nieuwe locatie en de referentiestroommodellen moeten worden bijgewerkt om de nieuwe locatie te weerspiegelen.</p>
    <ol>
     <li>Kopieer alle nieuwe of gewijzigde workflowscripts van de vorige locatie naar de nieuwe locatie.<br />
      <ul>
       <li><code>/apps/workflow/scripts</code> dient in de SCM te worden gehandhaafd.</li>
      </ul> </li>
     <li>Werk alle verwijzingen naar de workflowscripts op de vorige locatie in workflowmodellen bij om naar de nieuwe locaties te verwijzen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>AEM 6.4 SP1, wanneer het wordt vrijgegeven, maakt het zodat deze herstructurering kan worden uitgesteld tot 6.5
     <code>
      upgrade
     </code>.</p> <p>Als een upgrade naar AEM 6.4 plaatsvindt voordat AEM 6.4 SP1 wordt uitgebracht, dient deze herstructurering als onderdeel van het verbeteringsproject te worden uitgevoerd. Zonder dit te doen, zal het uitgeven van en het bewaren van de Stappen van het Werkschema die op manuscripten in de Vorige Plaats verwijzen de verwijzing van het Manuscript van het Werkschema volledig uit de Stap van de Werkstroom verwijderen, en slechts zullen de Manuscripten van het Werkschema in Nieuwe Plaatsen beschikbaar zijn in de drop-down manuscriptselectie.</p> </td>
  </tr>
 </tbody>
</table>

## V????r toekomstige upgrade {#prior-to-upgrade}

### ContextHub Configurations {#contexthub-configurations}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudsettings</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/cloudsettings</code></p> <p><code>/conf/global/settings/cloudsettings</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudsettings</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Om het even welke nieuwe of gewijzigde Configuraties ContextHub moeten aan de nieuwe plaats worden gemigreerd en de verwijzende pagina's van AEM Sites moeten worden bijgewerkt om op de nieuwe plaats te wijzen.</p>
    <ol>
     <li>Kopieer om het even welke nieuwe of gewijzigde Configuraties ContextHub van de vorige plaats aan de nieuwe plaats.</li>
     <li>Koppel de toepasselijke AEM configuraties aan de hi??rarchie??n van AEM inhoud.
      <ol>
       <li><strong>AEM Sites-paginabereiken via AEM Sites &gt; Pagina-eigenschappen &gt; Geavanceerd tabblad &gt; Cloudinstellingen</strong>.</li>
      </ol> </li>
     <li>Koppel om het even welke gemigreerde configuraties van de erfenis ContextHub van de bovengenoemde AEM inhoudshi??rarchie??n los.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Klassieke Cloud Services ontwerpen {#classic-cloud-services-designs}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/cloudservices</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/wcm/designs/cloudservices</code></p> <p><code>/apps/settings/wcm/designs/cloudservices</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime via de Dialogen van het Ontwerp worden geschreven.</p>
    <ol>
     <li>Kopieer de ontwerpen van de Vorige Plaats aan de Nieuwe Plaats (<code>/apps</code>).</li>
     <li>Converteer alle CSS-, JavaScript- en statische bronnen in het ontwerp naar een <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client Library</a> met <code>allowProxy = true</code>.</li>
     <li>Verwijzingen naar de vorige locatie bijwerken in <span class="code">
       <code>
        cq
       </code>:
       <code>
        designPath
       </code></span> eigenschap.</li>
     <li>Werk pagina's bij die naar de vorige locatie verwijzen om de nieuwe categorie Clientbibliotheek te kunnen gebruiken (hiervoor moet de code voor de implementatie van de pagina worden bijgewerkt).</li>
     <li>Werk AEM Dispatcher-regels bij om het serveren van clientbibliotheken toe te staan via de map /etc.clientlibs/.. proxyservlet.</li>
    </ol> <p>Voor om het even welke Ontwerpen die NIET in SCM, en gewijzigde runtime via de Dialogen van het Ontwerp beheerde.</p>
    <ul>
     <li>Verplaats ontwerpbare ontwerpen niet uit <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Klassieke dashboards ontwerpen {#classic-dashboards-designs}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/dashboards</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/wcm/designs/dashboards</code></p> <p><code>/apps/settings/wcm/designs/dashboards</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime via de Dialogen van het Ontwerp worden geschreven.</p>
    <ol>
     <li>Kopieer de ontwerpen van de vorige locatie naar de nieuwe locatie (/apps).</li>
     <li>Converteer alle CSS-, JavaScript- en statische bronnen in het ontwerp naar een <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client Library</a> met <code>allowProxy = true</code>.</li>
     <li>Verwijzingen naar de vorige locatie bijwerken in het dialoogvenster
      <code>
       cq
      </code>:
      <code>
       designPath
      </code> eigenschap.</li>
     <li>Werk pagina's bij die naar de vorige locatie verwijzen om de nieuwe categorie Clientbibliotheek te kunnen gebruiken (hiervoor moet de code voor de implementatie van de pagina worden bijgewerkt).</li>
     <li>Werk AEM Dispatcher-regels bij om het serveren van clientbibliotheken toe te staan via de map /etc.clientlibs/.. proxyservlet.</li>
    </ol> <p>Voor om het even welke Ontwerpen die NIET in SCM, en gewijzigde runtime via de Dialogen van het Ontwerp beheerde.</p>
    <ul>
     <li>Verplaats ontwerpbare ontwerpen niet uit <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Klassieke rapportontwerpen {#classic-reports-designs}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/reports</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/wcm/designs/reports</code></p> <p><code>/apps/settings/wcm/designs/reports</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime via de Dialogen van het Ontwerp worden geschreven.</p>
    <ol>
     <li>Kopieer de ontwerpen van de vorige locatie naar de nieuwe locatie (/apps).</li>
     <li>Converteer alle CSS-, JavaScript- en statische bronnen in het ontwerp naar een <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client Library</a> met <code>allowProxy = true</code>.</li>
     <li>Verwijzingen naar de vorige locatie bijwerken in het dialoogvenster
      <code>
       cq
      </code>:
      <code>
       designPath
      </code> eigenschap.</li>
     <li>Werk pagina's bij die naar de vorige locatie verwijzen om de nieuwe categorie Clientbibliotheek te kunnen gebruiken (hiervoor moet de code voor de implementatie van de pagina worden bijgewerkt).</li>
     <li>Werk AEM Dispatcher-regels bij om het serveren van clientbibliotheken toe te staan via de map /etc.clientlibs/.. proxyservlet.</li>
    </ol> <p>Voor om het even welke Ontwerpen die NIET in SCM, en gewijzigde runtime via de Dialogen van het Ontwerp beheerde.</p>
    <ul>
     <li>Verplaats ontwerpbare ontwerpen niet uit <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Standaardontwerpen {#default-designs}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/default</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/wcm/designs/default</code></p> <p><code>/apps/settings/wcm/designs/default</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime via de Dialogen van het Ontwerp worden geschreven.</p>
    <ol>
     <li>Kopieer de ontwerpen van de vorige locatie naar de nieuwe locatie (/apps).</li>
     <li>Converteer alle CSS-, JavaScript- en statische bronnen in het ontwerp naar een <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client Library</a> met <code>allowProxy = true</code>.</li>
     <li>Verwijzingen naar de vorige locatie bijwerken in het dialoogvenster
      <code>
       cq
      </code>:
      <code>
       designPath
      </code> eigenschap.</li>
     <li>Werk pagina's bij die naar de vorige locatie verwijzen om de nieuwe categorie Clientbibliotheek te kunnen gebruiken (hiervoor moet de code voor de implementatie van de pagina worden bijgewerkt).</li>
     <li>Werk AEM Dispatcher-regels bij om het serveren van clientbibliotheken toe te staan via de map /etc.clientlibs/.. proxyservlet.</li>
    </ol> <p>Voor om het even welke Ontwerpen die NIET in SCM, en gewijzigde runtime via de Dialogen van het Ontwerp beheerde.</p>
    <ul>
     <li>Verplaats ontwerpbare ontwerpen niet uit <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Adobe DTM JavaScript-eindpunt {#adobe-dtm-javascript-endpoint}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/clientlibs/dtm</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/var/cq/dtm/clientlibs</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Geen actie vereist.</p> <p>De openbare vorige plaats doet dienst als volmachtseindpunt voor de priv?? nieuwe plaats.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Adobe DTM Web-Hook Eindpunt {#adobe-dtm-web-hook-endpoint}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/dtm-hook</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/var/cq/dtm/web-hook</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Geen actie vereist.</p> <p>De openbare vorige plaats doet dienst als volmachtseindpunt voor de priv?? nieuwe plaats.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Inbox Taken {#inbox-tasks}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/taskmanagement</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/var/taskmanagement</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>Met de <strong>Inbox Purge Maintenance Task</strong> kunt u zo nodig oude taken verwijderen van de vorige locatie.</td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Er is geen actie vereist voor het migreren van taken naar de nieuwe locatie.</p>
    <ul>
     <li>Taken die zich bevinden op de vorige locatie, blijven beschikbaar en functioneren.</li>
     <li>De nieuwe Taken worden gecreeerd in de Nieuwe Plaats.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Configuraties {#multi-site-manager-blueprint-configurations} voor beheer van meerdere locaties

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong><em></em>Vorige locatie</strong></td>
   <td><code>/etc/blueprints</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/msm</code></p> <p><code>/apps/msm</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>
    <ol>
     <li>Kopieer aangepaste configuraties van <code>/etc/blueprints</code> naar <code>/apps/msm</code>.</li>
     <li>Verwijderen <code>/etc/blueprints</code>.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Gadget-configuraties voor AEM projecten {#aem-projects-dashboard-gadget-configurations}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/projects/dashboard/gadgets</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/cq/core/content/projects/dashboard/gadgets</code></p> <p><code>/apps/cq/core/content/projects/dashboard/gadgets</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Nieuwe of gewijzigde AEM Projecten moeten worden gemigreerd naar de nieuwe locatie (<code>/apps</code>).</p>
    <ol>
     <li>Kopieer eventuele nieuwe of gewijzigde AEM Gadget-configuraties van het dashboard voor projecten van de vorige locatie naar de nieuwe locatie (<code>/apps</code>).
      <ol>
       <li>Kopieer niet ongewijzigde AEM Gadget-configuraties van het dashboard van projecten, omdat deze nu bestaan op de nieuwe locatie (<code>/libs</code>).</li>
      </ol> </li>
     <li>Werk om het even welke AEM malplaatjes bij van Projecten die de Vorige Plaats van verwijzingen voorzien om aan de aangewezen nieuwe plaats te richten.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>Als het compatibiliteitspakket AEM 6.4 wordt toegepast, moet de uitlijning van de repository worden uitgevoerd op het moment dat het compatibiliteitspakket wordt verwijderd.</td>
  </tr>
 </tbody>
</table>

### E-mailsjabloon voor replicatiemelding {#replication-notification-e-mail-template}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/notification/email/default/com.day.cq.replication</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/notification-templates/com.day.cq.replication</code></p> <p><code>/apps/settings/notification-templates/com.day.cq.replication</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Nieuwe of gewijzigde E-mailsjablonen voor replicatiemeldingen moeten naar de nieuwe locatie worden gemigreerd (<code>/apps</code>)</p>
    <ol>
     <li>Kopieer om het even welke nieuwe of gewijzigde E-mailMalplaatjes van het Bericht van de Replicatie van de vorige plaats aan nieuwe plaats (<code>/apps</code>).</li>
     <li>Verwijder om het even welke gemigreerde E-mailMalplaatjes van het Bericht van de Replicatie van de vorige plaats.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De enige gesteunde nieuwe E-mailMalplaatjes van het Bericht van de Replicatie moeten nieuwe sc??nes steunen.</p> <p>De resolutie van het E-mailmalplaatje van het bericht van de replicatie komt in de volgende orde voor:</p>
    <ol>
     <li><code>/etc/notification/email/default/com.day.cq.replication</code></li>
     <li><code class="code">/apps/settings/notification-templates/com.day.cq.replication
        </code></li>
     <li><code>/libs/settings/notification-templates/com.day.cq.replication</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Labels {#tags}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/tags</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/content/cq:tags</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle labels moeten worden gemigreerd naar <code>/content/cq:tags</code>.</p>
    <ol>
     <li>Kopieer alle tags van de vorige locatie naar de nieuwe locatie.</li>
     <li>Alle tags verwijderen van de vorige locatie.</li>
     <li>Via de AEM webconsole start u de bundel Day Communique 5 Tagging OSGi op <em>https://serveraddress:serverport/system/console/bundles/com.day.cq.cq-tagging</em> opnieuw om AEM te herkennen dat de nieuwe locatie inhoud bevat en moet worden gebruikt.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Als u de bundel Dagcommunique Tagging OSGi opnieuw start, wordt de nieuwe locatie alleen geregistreerd als de hoofdcode als de vorige locatie leeg is.</p> <p>Verwijzingen naar de vorige locatie blijven werken na het migreren naar nieuwe locatie voor alle functies die gebruikmaken van AEM API voor tagbeheer voor het oplossen van tags.</p> <p>Elke aangepaste code die expliciet naar het pad <code>/etc/tags</code> verwijst, moet worden bijgewerkt naar <span class="code">/content/
      <code>
       cq
      </code>
      <code>
       :tags
      </code></span>, of bij voorkeur herschreven om de Java API van TagManager te gebruiken, in combinatie met deze migratie.</p> </td>
  </tr>
 </tbody>
</table>

### Cloud Services voor vertalingen {#translation-cloud-services}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/translation</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/cloudconfigs/translation/translationcfg</code></p> <p><code>/apps/settings/cloudconfigs/translation/translationcfg</code></p> <p><code>/conf/global/settings/cloudconfigs/translation/translationcfg</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translation/translationcfg</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Nieuwe Cloud Services voor vertaling moeten worden gemigreerd naar de nieuwe locatie (<code>/apps</code>, <code>/conf/global</code> of <code>/conf/&lt;tenant&gt;</code>).</p>
    <ol>
     <li>Bestaande configuraties in de vorige locatie migreren naar de nieuwe locatie.
      <ul>
       <li>Maak handmatig nieuwe configuraties van Cloud Services voor vertaling opnieuw via de AEM ontwerpinterface op <strong>Gereedschappen &gt; Cloud Services &gt; Cloud Services voor vertaling</strong>.<br /> OF </li>
       <li>Kopieer eventuele nieuwe configuraties van Cloud Services voor vertaling van de vorige locatie naar de nieuwe locatie (<code>/apps</code>, <code>/conf/global</code> of <code>/conf/&lt;tenant&gt;</code>).</li>
      </ul> </li>
     <li>Koppel de toepasselijke AEM configuraties aan de hi??rarchie??n van AEM inhoud.
      <ol>
       <li>AEM Sites page hi??rarchies via <strong>AEM Sites &gt; Page Properties &gt; Advanced Tab &gt; Cloud Configuration</strong>.</li>
       <li>AEM de hi??rarchie??n van het Fragment van de Ervaring via <strong>AEM de Fragmenten van de Ervaring &gt; het Fragment van de Ervaring &gt; Eigenschappen &gt; het Lusje van Cloud Services &gt; de Configuratie van de Wolk</strong>.</li>
       <li>AEM de hi??rarchie??n van de Omslagen van het Fragment van de Ervaring via <strong>AEM de Fragmenten van de Ervaring &gt; Omslag &gt; Eigenschappen &gt; het Lusje van Cloud Services &gt; de Configuratie van de Wolk</strong>.<br /> </li>
       <li>AEM Assets-maphi??rarchie??n via <strong>AEM Assets &gt; Map &gt; Mapeigenschappen &gt; Tabblad Cloud Services &gt; Configuration</strong>.</li>
       <li>AEM Projecten via <strong>AEM Projecten &gt; Projecteigenschappen &gt; Geavanceerd tabblad &gt; Cloudinstellingen</strong>.</li>
      </ol> </li>
     <li>Koppel eventuele gemigreerde verouderde Cloud Services voor vertaling los van de bovenstaande AEM inhoudhi??rarchie??n.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De Cloud Services van de vertaling komt in de volgende orde voor:</p>
    <ol>
     <li><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/conf/global/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/apps/settings/cloudconfigs/translations/translationcfg</code></li>
     <li><code>/libs/settings/cloudconfigs/translations/translationcfg</code></li>
    </ol> <p>Gemigreerde Cloud Services voor vertaling moeten compatibel zijn met AEM 6.4.</p> </td>
  </tr>
 </tbody>
</table>

### Vertaal talen {#translation-languages}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/translation/supportedLanguages</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/translation/supportedLanguages</code></p> <p><code>/apps/settings/translation/supportedLanguages</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor alle nieuwe of gewijzigde taaldefinities is een migratie van alle taaldefinities naar de nieuwe locatie vereist (<code>/apps</code>).</p>
    <ol>
     <li>Als de taaldefinities voor vertaling zijn uitgebreid of gewijzigd, kopieert u alle taaldefinities van de vorige locatie naar de nieuwe locatie (<code>/apps</code>).</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De resolutie van het vertaalpad vindt plaats in de volgende volgorde:</p>
    <ol>
     <li><code>/etc/translation/supportedLanguages</code></li>
     <li><code>/apps/settings/translation/supportedLanguage</code></li>
     <li><code>/libs/settings/translation/supportedLanguages</code></li>
    </ol> <p>Deze resolutie ondersteunt geen overlay voor samenvoegen. Dit betekent dat het opgeloste pad alle ondersteunde talen moet bevatten en geen ondersteunde talen van resoluties met een hogere volgorde mag overnemen.</p> </td>
  </tr>
 </tbody>
</table>

### Vertaalregels {#translation-rules}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/workflow/models/translation/translation_rules.xml</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/translation/rules/translation_rules.xml</code></p> <p><code>/apps/settings/translation/rules/translation_rules.xml</code></p> <p><code>/conf/global/settings/translation/rules/translation_rules.xml</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Een gewijzigd XML-bestand met vertaalregels moet naar de nieuwe locatie (<code>/apps</code> of <code>/conf/global</code>) worden gemigreerd.</p> <p>1. Kopieer het XML-bestand met gewijzigde vertaalregels van de vorige locatie naar de nieuwe locatie.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De resolutie van XML van de Regels van de replicatie komt in de volgende orde voor:</p>
    <ol>
     <li><code>/conf/global/settings/translation/rules/translation_rules.xml</code></li>
     <li><code class="code">/apps/settings/translation/rules/translation_rules.xml
        </code></li>
     <li><code class="code">/etc/workflow/models/translation/translation_rules.xml
        </code></li>
     <li><code>/libs/settings/translation/rules/translation_rules.xml</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Widget-clientbibliotheek voor vertaling {#translation-widget-client-library}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/translation/translationwidget</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/wcm/designs/translation/translationwidget</code></p> <p><code>/apps/settings/wcm/designs/translation/translationwidget</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime via de Dialogen van het Ontwerp worden geschreven.</p>
    <ol>
     <li>Kopieer de ontwerpen van de vorige locatie naar de nieuwe locatie (/apps).</li>
     <li>Converteer alle CSS-, JavaScript- en statische bronnen in het ontwerp naar een <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client Library</a> met <code>allowProxy = true</code>.</li>
     <li>Verwijzingen naar de vorige locatie bijwerken in het dialoogvenster
      <code>
       cq
      </code>:
      <code>
       designPath
      </code> eigenschap.</li>
     <li>Werk pagina's bij die naar de vorige locatie verwijzen om de nieuwe categorie Clientbibliotheek te kunnen gebruiken (hiervoor moet de code voor de implementatie van de pagina worden bijgewerkt).</li>
     <li>Werk AEM Dispatcher-regels bij om het serveren van clientbibliotheken toe te staan via de map /etc.clientlibs/.. proxyservlet.</li>
    </ol> <p>Voor om het even welke Ontwerpen die NIET in SCM, en gewijzigde runtime via de Dialogen van het Ontwerp beheerde.</p>
    <ul>
     <li>Verplaats ontwerpbare ontwerpen niet uit <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.</td>
  </tr>
 </tbody>
</table>

### Webconsole voor activering van boomstructuur {#tree-activation-web-console}

| **Vorige locatie** | `/etc/replication/treeactivation` |
|---|---|
| **Nieuwe locatie(s)** | `/libs/replication/treeactivation` |
| **Herstructureringsrichtsnoeren** | Geen actie vereist. |
| **Opmerkingen** | De Web-console van de Activering van de Boom is nu beschikbaar via **Hulpmiddelen > Plaatsing > Replicatie > Activate Tree**. |

{style=&quot;table-layout:auto&quot;}

### Cloud Services Vertaalaansluiting leverancier {#vendor-translation-connector-cloud-services}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/&lt;vendor&gt;</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/cloudconfigs/translation/&lt;vendor&gt;</code></p> <p><code class="code">/apps/settings/cloudconfigs/translation/&lt;vendor&gt;
       </code></p> <p><code class="code">/conf/global/settings/cloudconfigs/translation/&lt;vendor&gt;
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translation/&lt;vendor&gt;</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Nieuwe Cloud Services voor de vertalingsconnector van de leverancier moeten naar de nieuwe locatie worden gemigreerd (<code>/apps</code>, <code>/conf/global</code> of <code>/conf/&lt;tenant&gt;</code>).</p>
    <ol>
     <li>Bestaande configuraties in de vorige locatie migreren naar de nieuwe locatie.
      <ul>
       <li>Cre??er manueel netto-nieuwe Cloud Services van de Schakelaar van de Vertaling van de Leverancier via <strong>AEM auteursUI bij Hulpmiddelen &gt; Cloud Services &gt; Vertaling Cloud Services</strong>.<br /> OF </li>
       <li>Kopieer eventuele nieuwe configuraties van Cloud Services voor de vertaalaansluiting van leveranciers van vorige locatie naar de nieuwe locatie (<code>/apps</code>, <code>/conf/global </code>of <code>/conf/&lt;tenant&gt;</code>).</li>
      </ul> </li>
     <li>Koppel de toepasselijke AEM configuraties aan de hi??rarchie??n van AEM inhoud.
      <ol>
       <li>AEM Sites page hi??rarchies via <strong>AEM Sites &gt; Page Properties &gt; Advanced Tab &gt; Cloud Configuration</strong>.</li>
       <li>AEM de hi??rarchie??n van het Fragment van de Ervaring via <strong>AEM de Fragmenten van de Ervaring &gt; het Fragment van de Ervaring &gt; Eigenschappen &gt; het Lusje van Cloud Services &gt; de Configuratie van de Wolk</strong>.</li>
       <li>AEM Ervaar de hi??rarchie??n van de Omslagen van het Fragment via <strong>AEM Ervaar Fragmenten &gt; Omslag &gt; Eigenschappen &gt; Lusje van Cloud Services &gt; de Configuratie van de Wolk</strong>.</li>
       <li>AEM Assets-maphi??rarchie??n via <strong>AEM Assets &gt; Map &gt; Mapeigenschappen &gt; Tabblad Cloud Services &gt; Configuration</strong>.</li>
       <li>AEM Projecten via <strong>AEM Projecten &gt; Projecteigenschappen &gt; Geavanceerd tabblad &gt; Cloudinstellingen</strong>.</li>
      </ol> </li>
     <li>Koppel eventuele gemigreerde verouderde Cloud Services voor vertaling los van de bovenstaande AEM inhoudhi??rarchie??n.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De Cloud Services van de vertaling komt in de volgende orde voor:</p>
    <ol>
     <li><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translations/&lt;vendor&gt;</code></li>
     <li><code>/conf/global/settings/cloudconfigs/translations/&lt;vendor&gt;</code></li>
     <li><code>/apps/settings/cloudconfigs/translations/&lt;vendor&gt;</code></li>
     <li><code>/libs/settings/cloudconfigs/translations/&lt;vendor&gt;</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### E-mailsjablonen voor workflowmelding {#workflow-notification-email-templates}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/workflow/notification</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/workflow/notification</code></p> <p><code>/conf/global/settings/workflow/notification</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Elke gewijzigde e-mailsjablonen voor workflowmeldingen moeten naar de nieuwe locatie (<code>/conf/global</code>) worden gemigreerd.</p>
    <ol>
     <li>Kopieer eventuele gewijzigde e-mailsjablonen voor workflowmeldingen van de vorige locatie naar de nieuwe locatie.</li>
     <li>E-mailsjablonen voor gemigreerde workflowmeldingen verwijderen van de vorige locatie.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>E-mailsjabloonresolutie voor workflowmelding vindt in de volgende volgorde plaats:</p>
    <ol>
     <li><code>/etc/workflow/notification</code></li>
     <li><code>/conf/global/settings/workflow/notification</code></li>
     <li><code>/libs/settings/workflow/notification</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Workflowpakketten {#workflow-packages}

<table style="table-layout:auto">
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/workflow/packages</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/var/workflow/packages</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Bestaande Workflowpakketten op de vorige locatie moeten naar de nieuwe locatie worden gemigreerd.</p>
    <ol>
     <li>Verwijder om het even welke Pakketten van het Werkschema in de vorige plaats die niet door andere inhoud van verwijzingen worden voorzien en anders niet vereist zijn.</li>
     <li>Verplaats om het even welke Pakketten van het Werkschema in de vorige plaats die niet door andere inhoud van verwijzingen worden voorzien maar anders vereist in de nieuwe plaats.</li>
     <li>Verlaat om het even welke Pakketten van het Werkschema die door andere inhoud in de vorige plaats van verwijzingen worden voorzien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Workflowpakketten die zijn gemaakt via de Classic UI Miscadmin-console blijven behouden op de vorige locatie, terwijl alle andere pakketten worden voortgezet naar de nieuwe locatie.</p> <p>De pakketten van het werkschema die in of de vorige of lagere plaatsen worden opgeslagen kunnen via de Klassieke console UI Miscadmin worden beheerd.</p> </td>
  </tr>
 </tbody>
</table>

