---
title: Sites Repositoregeling Herstructurering AEM 6.5
seo-title: Sites Repositoregeling Herstructurering AEM 6.5
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe opslagstructuur in AEM 6.5 voor sites.
seo-description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe opslagstructuur in AEM 6.5 voor sites.
uuid: 6dc5f8bd-1680-40af-9b8f-26c1f4bc3304
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 3eccb2d5-c325-43a6-9c03-5f93f7e30712
feature: Upgrading
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1601'
ht-degree: 0%

---


# Sites Repository Herstructurering in AEM 6.5 {#sites-repository-restructuring-in-aem}

Zoals beschreven op de bovenliggende [Repository Reform in AEM 6.5](/help/sites-deploying/repository-restructuring.md)-pagina, moeten klanten die een upgrade uitvoeren naar AEM 6.5 deze pagina gebruiken om de werkinspanning te beoordelen die gepaard gaat met wijzigingen in de opslagplaats die gevolgen hebben voor de AEM Sites-oplossing. Sommige veranderingen vereisen het werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**Met 6,5-upgrade**

* [ContextHub-segmenten](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#contexthub-segments)

**Voorafgaand aan toekomstige upgrade**

* [Adobe Analytics-clientbibliotheken](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#adobe-analytics-client-libraries)
* [Klassieke Microsoft Word-naar-webpaginamodellen](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#classic-microsoft-word-to-web-page-designs)
* [Emulatorconfiguraties voor mobiele apparaten](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#mobile-device-emulator-configurations)
* [Configuraties van blauwdruk voor beheer op meerdere locaties](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#multi-site-manager-blueprint-configurations)
* [Uitrolconfiguraties voor beheer op meerdere locaties](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#multi-site-manager-rollout-configurations)
* [E-mailsjabloon voor melding van paginagebeurtenis](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#page-event-notification-e-mail-template)
* [Paginastructuur](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#page-scaffolding)
* [Responsief raster MINDER](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#responsive-grid-less)
* [Statische sjabloonontwerpen](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#static-template-designs)
* [Adobe zoek en promoot de Bibliotheken van de Cliënt van de Integratie](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#adobe-search-and-promote-integration-client-libraries)
* [Adobe Target Integration Client Libraries](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#adobe-target-integration-client-libraries)
* [WCM Foundation-clientbibliotheken](/help/sites-deploying/sites-repository-restructuring-in-aem-6-5.md#wcm-foundation-client-libraries)

## Met 6.5-upgrade {#with-upgrade}

### ContextHub-segmenten {#contexthub-segments}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/segmentation/contexthub</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/apps/settings/wcm/segments</code> </p> <p><code>/conf/settings/settings/wcm/segments</code> </p> <p><code>/conf/&lt;tenant&gt;/settings/wcm/segments</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Als om het even welke nieuwe of gewijzigde Segmenten ContextHub bedoeld zijn om in broncontrole eerder dan wordt uitgegeven in AEM worden uitgegeven, moeten zij aan de nieuwe plaats worden gemigreerd:</p>
    <ol>
     <li>Kopieer om het even welke nieuwe of gewijzigde Segmenten ContextHub van de vorige plaats aan de aangewezen nieuwe plaats (/<code>apps</code>, <code>/conf/global</code> of <code>/conf/&lt;tenant&gt;</code>)</li>
     <li>Verwijzingen van de update naar Segmenten ContextHub in de vorige plaats aan de gemigreerde Segmenten ContextHub in de nieuwe plaatsen (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li>
    </ol> <p>De volgende vraag QueryBuilder bepaalt de plaats van alle verwijzingen naar Segmenten ContextHub in de Vorige Plaatsen.<br /> <br /> <code class="code">path=/content
       property=cq:segments
       property.operation=like
       property.value=/etc/segmentation/contexthub/%</code><br /> <br /> Dit kan via  <a href="/help/sites-developing/querybuilder-api.md" target="_blank">AEM Foutopsporingsinterface</a> QueryBuilder worden uitgevoerd. Merk op dat dit een het doorlopen vraag is, zodat stel het niet tegen productie in werking, en verzeker traversale grenzen aangepast zoals nodig.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De Segmenten van ContextHub persisteerden aan de vorige plaatsvertoning als read-only in <strong>AEM &gt; Personalisering &gt; Soorten </strong>.</p> <p>Als de Segmenten ContextHub in AEM editable moeten zijn, moeten zij aan de nieuwe plaats (<code>/conf/global</code> of <code>/conf/&lt;tenant&gt;</code>) worden gemigreerd. Om het even welke nieuwe die segmenten ContentHub in AEM worden gecreeerd worden voortgeduurd aan de nieuwe plaats (<code>/conf/global</code> of <code>/conf/&lt;tenant&gt;</code>).</p> <p>Met AEM Sites-pagina-eigenschappen kan alleen de vorige locatie (<code>/etc</code>) of één nieuwe locatie (<code>/apps</code>, <code>/conf/global</code> of <code>/conf/&lt;tenant&gt;</code>) worden geselecteerd. ContextHub-segmenten moeten daarom dienovereenkomstig worden gemigreerd.</p> <p>Om het even welke ongebruikte Segmenten ContextHub van AEM verwijzingsplaatsen kunnen worden verwijderd en niet aan de Nieuwe Plaats worden gemigreerd:</p>
    <ul>
     <li>/etc/segmentation/geometrixx/</li>
     <li>/etc/segmentation/geometrixx-outdoor</li>
    </ul> <p>Opmerking: Als ClientContext in gebruik is, wordt het geadviseerd om in ContextHub om te zetten.</p> </td>
  </tr>
 </tbody>
</table>

## Vóór toekomstige upgrade {#prior-to-upgrade}

### Adobe Analytics-clientbibliotheken {#adobe-analytics-client-libraries}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/clientlibs/foundation/sitecatalyst</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/cq/analytics/clientlibs/analytics</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Elk aangepast gebruik van deze clientbibliotheken moet verwijzen naar de clientbibliotheek per categorie en niet per pad:</p>
    <ol>
     <li>Om het even welke verwijzingen naar de Bibliotheek van de Cliënt door weg bij de Vorige Plaats zouden moeten worden bijgewerkt om <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM de Bibliotheek van de Cliënt te gebruiken verwijzend kader</a>.</li>
     <li>Als AEM Client Library-verwijzingsframework niet kan worden gebruikt, kan naar het absolute pad van de Client Libraries worden verwezen via AEM Client Library Proxy servlet.
      <ul>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/appmeasurement.js</code></li>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/plugins.js</code></li>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst.js</code></li>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/tracking.js</code></li>
       <li><code>/etc.clientlibs/cq/analytics/clientlibs/sitecatalyst/util.js</code></li>
      </ul> </li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Het bewerken van deze clientbibliotheken is nooit ondersteund.</p> <p>Om de categorieën van de Bibliotheek van de Cliënt te verkrijgen, bezoek elk <code>cq:ClientLIbraryFolder</code> knoop via CRXDELite en inspecteer het categoriebezit.</p>
    <ul>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/appmeasurement</code></li>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/plugins</code></li>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/sitecatalyst</code></li>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/tracking</code></li>
     <li><code>/libs/cq/analytics/clientlibs/sitecatalyst/util</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Klassiek Microsoft Word-naar-webpaginamodellen {#classic-microsoft-word-to-web-page-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/wordDesign</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/wcm/designs/wordDesign</code></p> <p><code>/apps/settings/wcm/designs/wordDesign</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime via de Dialogen van het Ontwerp worden geschreven.</p>
    <ol>
     <li>Kopieer de ontwerpen van de Vorige Plaats aan de Nieuwe Plaats (<code>/apps</code>).</li>
     <li>Converteer alle CSS-, JavaScript- en statische bronnen in het ontwerp naar een <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client Library</a> met <code>allowProxy = true</code>.</li>
     <li>Verwijzingen naar de vorige locatie bijwerken in de eigenschap cq:designPath.</li>
     <li>Werk pagina's bij die naar de vorige locatie verwijzen om de nieuwe categorie Clientbibliotheek te kunnen gebruiken (hiervoor moet de code voor de implementatie van de pagina worden bijgewerkt).</li>
     <li>Werk AEM Dispatcher-regels bij om het gebruik van clientbibliotheken via de proxyserver <code>/etc.clientlibs/</code> toe te staan.</li>
    </ol> <p>Voor om het even welke Ontwerpen die NIET in SCM, en gewijzigde runtime via de Dialogen van het Ontwerp beheerde:</p>
    <ul>
     <li>Verplaats ontwerpbare ontwerpen niet uit <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Emulatorconfiguraties voor mobiele apparaten {#mobile-device-emulator-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/mobile</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/mobile</code></p> <p><code>/apps/settings/mobile</code></p> <p><code>/conf/global/settings/mobile</code></p> <p><code>/conf/&lt;tenant&gt;/settings/mobile</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>Alle nieuwe emulatorconfiguraties voor mobiele apparaten moeten worden gemigreerd naar de nieuwe locatie.
    <ol>
     <li>Kopieer eventuele nieuwe emulatorconfiguraties voor mobiele apparaten van de vorige locatie naar de nieuwe locatie (<code>/apps</code>, <code>/conf/global</code>, <code>/conf/&lt;tenant&gt;</code>).</li>
     <li>Voor alle AEM Sites-pagina's die afhankelijk zijn van deze emulatorconfiguraties voor mobiele apparaten, werkt u <span class="code"> van de pagina bij
       <code>
        jcr
       </code>
       <code>
        :content
       </code></span>-knooppunt: <br /> <span class="code">[cq:Page]/jcr:content@cq:
       <code>
        deviceGroups
       </code> = String[ mobile/groups/responsive ]</span></li>
     <li>Voor alle bewerkbare sjablonen die afhankelijk zijn van deze emulatorconfiguraties voor mobiele apparaten werkt u de bewerkbare sjablonen bij en wijst u <span class="code">
       <code>
        cq
       </code>:
       <code>
        deviceGroups
       </code></span> naar de nieuwe locatie.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>De resolutie van de Configuraties van de Emulator van het Mobiel Apparaat komt in de volgende orde voor:</p>
    <ol>
     <li><code>/conf/&lt;tenant&gt;/settings/mobile</code></li>
     <li><code>/conf/global/settings/mobile</code></li>
     <li><code>/apps/settings/mobile</code></li>
     <li><code>/libs/settings/mobile</code></li>
     <li><code>/etc/mobile</code></li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Configuraties {#multi-site-manager-blueprint-configurations} voor beheer van meerdere locaties

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/blueprints</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/apps/msm</code> (Klantblauwdrukconfiguraties)</p> <p><code>/libs/msm</code> (Configuratie Vervaging buiten kader voor schermen, handel)</p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle nieuwe of gewijzigde configuraties van de Vervaging van de Manager van de multi-site moeten aan de Nieuwe Plaats (<code>/apps</code>) worden gemigreerd.</p>
    <ol>
     <li>Kopieer eventuele nieuwe of gewijzigde configuraties van de Vervaging van de Manager van de Multisite Manager van de Vorige Plaats aan de Nieuwe Plaats (<code>/apps</code>).</li>
     <li>Verwijder alle gemigreerde configuraties voor beheer van meerdere sites uit de vorige locatie.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Alle AEM bieden configuraties voor beheer op meerdere locaties in de sectie New Location in <code>/libs</code>.</p> <p>De inhoud verwijst niet naar de Blauwe Configuraties van de Manager van de Multisite daarom zijn er geen inhoudsverwijzingen om aan te passen.</p> </td>
  </tr>
 </tbody>
</table>

### Configuratie {#multi-site-manager-rollout-configurations} voor implementatie van meerdere beheersites

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/msm/rolloutConfigs</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/msm/wcm/rolloutconfigs</code></p> <p><code>/apps/msm/wcm/rolloutconfigs</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Nieuwe of gewijzigde configuraties voor de implementatie van meerdere beheersites moeten naar de nieuwe locatie worden gemigreerd.</p>
    <ol>
     <li>Kopieer eventuele nieuwe of gewijzigde implementatieconfiguraties voor meerdere sites van Manager van de vorige locatie naar de nieuwe locatie (<code>/apps</code>).</li>
     <li>Werk om het even welke verwijzingen op AEMPagina's aan de Configuraties van de Output van de Manager van de Multisite in de Vorige Plaats bij, om aan hun tegenhangers in de Nieuwe Plaatsen (<code>/libs</code> of <code>/apps</code>) te richten.</li>
    </ol> <p>Verwijder gemigreerde configuraties voor de implementatie van meerdere sites uit de vorige locatie.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>Als u de gemigreerde implementatieconfiguraties voor beheer op meerdere sites niet verwijdert van de vorige locatie, resulteert dit in dubbele implementatieopties die worden weergegeven aan AEM auteurs.</td>
  </tr>
 </tbody>
</table>

### E-mailsjabloon voor paginagebeurtenis {#page-event-notification-e-mail-template}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></p> <p><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>De enige ondersteunde nieuwe e-mailsjablonen voor gebeurtenismeldingen voor de pagina zijn de ondersteuning van nieuwe landinstellingen.</p> <p>De resolutie van het E-mailsjabloon voor paginagebeurtenissen vindt plaats in de volgende volgorde:</p>
    <ol>
     <li><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></li>
     <li><code>/apps/settings/notification-templates/com.day.cq.wcm.core.page</code></li>
     <li><code>/libs/settings/notification-templates/com.day.cq.wcm.core.page</code></li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Nieuwe of gewijzigde E-mailsjablonen voor gebeurtenismeldingen voor de pagina moeten naar de nieuwe locatie worden gemigreerd onder <code>/apps</code>:</p>
    <ol>
     <li>Kopieer alle nieuwe of gewijzigde e-mailsjablonen voor gebeurtenismeldingen voor de pagina van de vorige locatie naar de nieuwe locatie (<code>/apps</code>).</li>
     <li>Verwijder alle sjablonen voor meldingen van gemigreerde paginagebeurtenissen uit de vorige locatie.</li>
    </ol> </td>
  </tr>
 </tbody>
</table>

### Paginastructuur {#page-scaffolding}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/scaffolding</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><span class="code">/libs/settings/
      <code>
       wcm
      </code>/template-types/steigers/steigers</span></p> <p><span class="code">/apps/settings/
      <code>
       wcm
      </code>/template-types/steigers/steigers</span></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>Basisstructuur die onder de vorige locatie is gemaakt, gebruikt het oudere framework voor segmentering en kan niet naar de nieuwe locatie worden gemigreerd. Om met de Nieuwe Plaats te richten moet om het even welke erfenisBasisstructuur opnieuw worden ontwikkeld gebruikend het gesteunde Kader van de Basisstructuur.</td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Responsief raster, LESS {#responsive-grid-less}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/clientlibs/wcm/foundation/grid/grid_base.less</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/wcm/foundation/clientlibs/grid/grid_base.less</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle verwijzingen naar de vorige locatie in aangepaste LESS-bestanden moeten worden bijgewerkt om te kunnen importeren vanaf de nieuwe locatie.</p>
    <ul>
     <li>Werk om het even welke van verwijzingen voorzien van douaneLESS dossiers bij die net_base.less in de Vorige Plaats van verwijzingen voorzien om de nieuwe plaats te verwijzen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>Wanneer wordt verwezen naar een niet-bestaand <code>grid_base.less</code>-bestand, werkt de lay-outmodus van de Pagina- en de Sjablooneditor niet en is de paginalay-out beschadigd.</td>
  </tr>
 </tbody>
</table>

### Statische sjabloonontwerpen {#static-template-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/&lt;custom-site&gt;</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/apps/settings/wcm/designs/&lt;custom-site&gt;</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Voor om het even welke Ontwerpen die in SCM worden beheerd, en niet aan in runtime via de Dialogen van het Ontwerp worden geschreven.</p>
    <ol>
     <li>Kopieer de ontwerpen van de Vorige Plaats aan de Nieuwe Plaats (<code>/apps</code>).</li>
     <li>Converteer alle CSS-, JavaScript- en statische bronnen in het ontwerp naar een <a href="/help/sites-developing/clientlibs.md#creating-client-library-folders" target="_blank">Client Library</a> met <code>allowProxy = true</code>.</li>
     <li>Verwijzingen naar de vorige locatie in de eigenschap <code>cq:designPath</code> bijwerken via <strong>AEM &gt; Sites &gt; Aangepaste sitepagina's &gt; Pagina-eigenschappen &gt; Geavanceerd tabblad &gt; Ontwerpveld</strong>.</li>
     <li>Werk pagina's bij die naar de vorige locatie verwijzen om de nieuwe categorie Clientbibliotheek te kunnen gebruiken (hiervoor moet de code voor de implementatie van de pagina worden bijgewerkt).</li>
     <li>Werk AEM Dispatcher-regels bij om het serveren van clientbibliotheken via de proxyserver <code>/etc.clientlibs/</code> toe te staan.</li>
    </ol> <p>Voor om het even welke Ontwerpen die NIET in SCM, en gewijzigde runtime via de Dialogen van het Ontwerp beheerde:</p>
    <ul>
     <li>Verplaats ontwerpbare ontwerpen niet uit <code>/etc</code>.</li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>De aanbevolen aanpak is om AEM Sites en Pagina's samen te stellen met Bewerkbare sjablonen die Structuurelementen en -beleid gebruiken in plaats van Ontwerpen.</td>
  </tr>
 </tbody>
</table>

### Adobe zoek en promoot de Bibliotheken van de Cliënt van de Integratie {#adobe-search-and-promote-integration-client-libraries}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/clientlibs/foundation/searchpromote</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Elk aangepast gebruik van deze clientbibliotheken moet verwijzen naar de clientbibliotheek per categorie en niet per pad.</p>
    <ol>
     <li>Om het even welke verwijzingen naar de Bibliotheek van de Cliënt door weg bij de Vorige Plaats zouden moeten worden bijgewerkt om <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM de Bibliotheek van de Cliënt te gebruiken verwijzend kader</a>.</li>
     <li>Als AEM Client Library-verwijzingsframework niet kan worden gebruikt, kan naar het absolute pad van de Client Libraries worden verwezen via AEM Client Library Proxy servlet:</li>
    </ol>
    <ul>
     <li><code>/etc.clientlibs/cq/searchpromote/clientlibs/searchpromotei.js</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Het bewerken van deze clientbibliotheken is nooit ondersteund.</p> <p>Om de categorieën van de Bibliotheek van de Cliënt te verkrijgen, bezoek elk knoop cq:ClientLILibraryFolder via CRXDELite en inspecteer het categoriebezit:</p>
    <ul>
     <li><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### Adobe Target Integration Client Libraries {#adobe-target-integration-client-libraries}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/clientlibs/foundation/target</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/cq/testandtarget/clientlibs/testandtarget</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Elk aangepast gebruik van deze clientbibliotheken moet verwijzen naar de clientbibliotheek per categorie en niet per pad.</p>
    <ol>
     <li>Om het even welke verwijzingen naar de Bibliotheek van de Cliënt door weg bij de Vorige Plaats zouden moeten worden bijgewerkt om <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM de Bibliotheek van de Cliënt te gebruiken verwijzend kader</a>.</li>
     <li>Als AEM Client Library-verwijzingsframework niet kan worden gebruikt, kan naar het absolute pad van de Client Libraries worden verwezen via AEM Client Library Proxy servlet:</li>
    </ol>
    <ul>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/testandtarget.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/atjs.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/atjs-integration.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/init.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/mbox.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/parameters.js</code></li>
     <li><code>/etc.clientlibs/cq/testandtarget/clientlibs/testandtarget/util.js</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Het bewerken van deze clientbibliotheken is nooit ondersteund.</p> <p>Om de categorieën van de Bibliotheek van de Cliënt te verkrijgen, bezoek elk knoop cq:ClientLILibraryFolder via CRXDELite en inspecteer het categoriebezit:</p>
    <ul>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/testandtarget</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/atjs</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/atjs-integration</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/init</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/mbox</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/parameters</code></li>
     <li><code>/libs/cq/testandtarget/clientlibs/testandtarget/util</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>

### WCM Foundation-clientbibliotheken {#wcm-foundation-client-libraries}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><p><code>/etc/clientlibs/wcm/foundation</code></p> </td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/wcm/foundation/clientlibs</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Elk aangepast gebruik van deze clientbibliotheken moet verwijzen naar de clientbibliotheek per categorie en niet per pad.</p>
    <ol>
     <li>Om het even welke verwijzingen naar de Bibliotheek van de Cliënt door weg bij de Vorige Plaats zouden moeten worden bijgewerkt om <a href="/help/sites-developing/clientlibs.md#referencing-client-side-libraries" target="_blank">AEM de Bibliotheek van de Cliënt te gebruiken verwijzend kader</a>.</li>
     <li>Als AEM Client Library-verwijzingsframework niet kan worden gebruikt, kan naar het absolute pad van de Client Libraries worden verwezen via AEM Client Library Proxy servlet.</li>
    </ol>
    <ul>
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/accessibility.css</code></li>
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/main.css</code></li>
     <li><code>/etc.clientlibs/wcm/foundation/clientlibs/main.js</code></li>
    </ul> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td><p>Het bewerken van deze clientbibliotheken is nooit ondersteund.</p> <p>Om de categorieën van de Bibliotheek van de Cliënt te verkrijgen, bezoek elk <code>cq:ClientLIbraryFolder</code> knoop via CRXDELite en inspecteer het categoriebezit:</p>
    <ul>
     <li><code>/libs/wcm/foundation/clientlibs/accessibility</code></li>
     <li><code>/libs/wcm/foundation/clientlibs/main</code></li>
    </ul> </td>
  </tr>
 </tbody>
</table>

