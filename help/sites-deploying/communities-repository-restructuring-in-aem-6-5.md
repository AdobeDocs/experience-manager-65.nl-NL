---
title: Repositoregeling voor de herstructurering van AEM Communities in punt 6.4
seo-title: Repositoregeling voor de herstructurering van AEM Communities in punt 6.4
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe dataopslagstructuur in AEM 6.4 voor Gemeenschappen.
seo-description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe dataopslagstructuur in AEM 6.4 voor Gemeenschappen.
uuid: d161655f-4074-44a7-8d69-38e80934c58b
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
discoiquuid: 7383265b-0ed4-4ea7-b741-0a417d187bdd
feature: Upgrading
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1038'
ht-degree: 1%

---


# Herstructurering van de opslagplaats voor AEM Communities in 6.5 {#repository-restructuring-for-aem-communities-in}

Zoals beschreven op de bovenliggende [Repository Reform in AEM 6.4](/help/sites-deploying/repository-restructuring.md)-pagina, moeten klanten die een upgrade uitvoeren naar AEM 6.5 deze pagina gebruiken om de werkinspanning te beoordelen die gepaard gaat met wijzigingen in de opslagplaats die gevolgen hebben voor de AEM Communities-oplossing. Sommige veranderingen vereisen het werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**Met 6,5-upgrade**

* [E-mailmeldingssjablonen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#e-mail-notification-templates)
* [Subscription Configurations](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#subscription-configurations)

**Voorafgaand aan toekomstige upgrade**

* [Badgingconfiguraties](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#badging-configurations)
* [Consoleontwerpen van klassieke gemeenschappen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#classic-communities-console-designs)
* [Facebook Social Login Configurations](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#facebook-social-login-configurations)
* [Configuraties taalopties](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#language-options-configurations)

* [Pinterest Social Login Configurations](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#pinterest-social-login-configurations)
* [Scoringconfiguraties](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#scoring-configurations)
* [Twitter Social Login Configurations](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#twitter-social-login-configurations)
* [Dic](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#misc)

## Met 6.5-upgrade {#with-upgrade}

### E-mailmeldingssjablonen {#e-mail-notification-templates}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/community/notifications</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/settings/community/notifications</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Handmatige migratie is nodig als u naar een nieuw pad wilt gaan onder "<code>/apps/settings</code>". U kunt de Manager van de Configuratie van Granite gebruiken om de migratie uit te voeren.</p> <p>U kunt de migratie uitvoeren door het bezit <code>mergeList</code> aan <code>true</code> op "<code>/libs/settings/community/subscriptions</code>"knoop te plaatsen en een <code>nt:unstructured</code> kindknoop toe te voegen.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Abonnementsconfiguraties {#subscription-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/community/subscriptions</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/settings/community/subscriptions</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Handmatige migratie is nodig als u naar een nieuw pad wilt gaan onder "<code>/apps/settings</code>". U kunt de Manager van de Configuratie van Granite gebruiken om de migratie uit te voeren.</p> <p>U kunt de migratie uitvoeren door het bezit <code>mergeList</code> aan <code>true</code> op "<code>/libs/settings/community/subscriptions</code>"knoop te plaatsen en een <code>nt:unstructured</code> kindknoop toe te voegen.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Watchwords-configuraties {#watchwords-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td>/etc/watchwords</td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td>/libs/community/watchwords</td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>Er is een uitgestelde migratietaak beschikbaar voor het opschonen van de Community Configurations.<br /> <p>De Taak beweegt controlewoorden van <code>/etc/watchwords</code> naar <code>/conf/global/settings/community/watchwords</code>.</p> <p>Als de aangepaste watchwords in SCM worden opgeslagen, dan zouden zij aan <code>/apps/settings/...</code> moeten worden opgesteld en u moet ervoor zorgen dat er geen het bedekken <code>/conf/global/settings/...</code> configuratie is die belangrijkheid zou nemen.</p> <p>De taak van de migratie verwijdert <code>/etc</code> plaatsen.</p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

## Vóór toekomstige upgrade {#prior-to-upgrade}

### Badgingconfiguraties {#badging-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/community/badging</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><strong>Badge-regels:</strong></p> <p><code>/libs/settings/community/badging</code></p> <p><strong>Badge-afbeeldingen:</strong></p> <p>Voor standaardafbeeldingen: <code>/etc/community/badging/images are moved to /libs/community/badging/images</code></p> <p>Voor aangepaste afbeeldingen: <code>/content/community/badging/images</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Handmatige migratie is vereist.</p> <p>Als uw instantie de regels voor badging/scoring heeft aangepast, is er geen geautomatiseerde manier om alle regels onder een emmertje te plaatsen. De input van de klant vereist waarop conf emmer (globaal of specifiek) u voor uw plaats wilt gebruiken.</p> <p>Er is geen interface beschikbaar voor het configureren van de badging en scoring voor een site.</p> <p>Uitlijnen met nieuwe repository structuur:</p>
    <ol>
     <li>Maak een sitecontextemmertje met behulp van de <strong>Configuration Browser</strong> onder <strong>Tools</strong></li>
     <li>Ga naar de hoofdmap van de site</li>
     <li>Stel <code>cq:confproperty</code> in op het emmerpad waar u al uw instellingen wilt opslaan. Hetzelfde kan worden ingesteld via de site <strong>Wizard Bewerken - Cloud config-invoer instellen</strong>.</li>
     <li>Verplaats relevante regels voor badging en scoring van <code>/etc/community/*</code> naar het sitecontextemmertje dat in de vorige stap is gemaakt.</li>
     <li>Pas de regels van het badging en het schrapen eigenschappen van Regels op plaatshroot aan om relatieve verwijzingen naar nieuwe regelplaatsen te hebben.
      <ol>
       <li>Als de eigenschap voor <code>cq:conf = /conf/we-retail</code> bijvoorbeeld, <code>badgingRules [] = community/badging/rules</code> is als de regels nu naar dit nieuwe emmertje worden verplaatst.</li>
      </ol> </li>
     <li>Pas op dezelfde manier de verwijzingen naar het schrapen van regels in een merkende regelknoop aan om een relatief pad te hebben.</li>
    </ol> <p> </p> <p>Tot slot kunt u opschonen door de resource te verwijderen <code>/etc/community/badging</code></p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Consoleontwerpen voor klassieke gemeenschappen {#classic-communities-console-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/social/console</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code>/libs/settings/wcm/designs/social/console</code></p> <p><code>/apps/settings/wcm/designs/social/console</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>N.v.t.</td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Facebook Social Login Configurations {#facebook-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/facebookconnect</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/facebookconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/facebookconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle nieuwe Facebook Cloud Configurations moeten naar de nieuwe locatie worden gemigreerd.</p>
    <ol>
     <li>Bestaande configuraties in de vorige locatie migreren naar de nieuwe locatie.
      <ol>
       <li>Maak handmatig nieuwe Facebook Social Login Configurations opnieuw via de AEM ontwerpinterface op <strong>Extra &gt; Cloud Services &gt; Configuratie van sociale aanmelding via Facebook</strong>.<br /> or <br /> </li>
       <li>Kopieer eventuele nieuwe Facebook Cloud Configurations van Vorige Locatie naar de juiste nieuwe locatie onder <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Werk een AEM Communities Site-hoofdmap bij om naar de nieuwe Facebook Social Login Configuration te verwijzen door de eigenschap <code>[cq:Page]/jcr:content@cq:conf</code> in te stellen op het absolute pad in de Nieuwe Locatie.</li>
     <li>Koppel de oudere Facebook Connect-Cloud Service los van alle hoofdmappen van de AEM Communities-site die zijn bijgewerkt om naar de nieuwe locatie te verwijzen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Taalopties Configuraties {#language-options-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/social/config/languageOpts</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/social/translation/languageOpts</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Pinterest Social Login Configurations {#pinterest-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/pinterestconnect</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/pinterestconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/pinterestconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle nieuwe Pinterest Cloud Configurations moeten naar de nieuwe locatie worden gemigreerd.</p>
    <ol>
     <li>Bestaande configuraties in de vorige locatie migreren naar de nieuwe locatie.
      <ol>
       <li>Maak handmatig nieuwe Pinterest Social Login Configurations (Pinterest Social Login Configurations) via de AEM ontwerpinterface op <strong>Extra &gt; Cloud Services &gt; Pinterest Social Login Configuration</strong>.<br /> or</li>
       <li>Kopieer eventuele nieuwe Pinterest Cloud Configurations van Vorige locatie naar de juiste nieuwe locatie onder <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Werk om het even welke wortel van de Plaats van AEM Communities bij om de nieuwe Pinterest Sociale Login Configuratie door montages te verwijzen het <code>[cq:Page]/jcr:content@cq:conf</code> bezit aan de absolute weg in de Nieuwe Plaats.</li>
     <li>Koppel de verouderde Pinterest Connect-Cloud Service los van de hoofdmappen van de AEM Communities-site die zijn bijgewerkt om naar de nieuwe locatie te verwijzen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Scoringconfiguraties {#scoring-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/community/scoring</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/settings/community/scoring</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Om uit te lijnen met de nieuwe repository structuur, kunnen scoringregels worden opgeslagen in <code>/apps/settings/</code> of /<code>conf/.../settings</code></p>
    <ol>
     <li>Voor <code>/apps/settings</code>, zou dit als globale of standaardregels dienst doen die in SCM worden beheerd.</li>
    </ol> <p>Creeer context-bewuste vormen in <code>/conf/</code> door CRXDELite te gebruiken:</p>
    <ol>
     <li>Creeer vormen in de gewenste <code>/conf/.../settings</code> plaats<br /> </li>
     <li>Voor de site van een Gemeenschappen moet de eigenschap <code>cq:conf </code>ingesteld zijn.
      <ol>
       <li>Als er geen <code>cq:conf</code> is ingesteld, worden de scoreregels rechtstreeks gelezen vanuit het opgegeven pad voor eigenschap '<code>scoringRules</code>' op het hoofdknooppunt van de site, bijvoorbeeld: <code>/content/we-retail/us/en/community/jcr:content</code></li>
      </ol> </li>
    </ol> <p>Overbodig verwijderen: De bron verwijderen <code>/etc/community/scoring</code></p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Twitter Social Login Configurations {#twitter-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/twitterconnect</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/twitterconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/twitterconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle nieuwe Twitter Cloud Configurations moeten naar de nieuwe locatie worden gemigreerd.</p>
    <ol>
     <li>Bestaande configuraties in de vorige locatie migreren naar de nieuwe locatie.
      <ol>
       <li>Maak handmatig nieuwe Twitter Social Login Configurations opnieuw via de AEM ontwerpinterface op <strong>Extra &gt; Cloud Services &gt; Configuratie van Twitter Social Login</strong>.<br /> of  <br /> </li>
       <li>Kopieer eventuele nieuwe Twitter Cloud Configurations van Vorige locatie naar de juiste nieuwe locatie onder <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Werk een AEM Communities-hoofdmap van de site bij om naar de nieuwe Twitter Social Login Configuration te verwijzen door de eigenschap <code>[cq:Page]/jcr:content@cq:conf</code> in te stellen op het absolute pad in de Nieuwe Locatie.</li>
     <li>Koppel de oudere Twitter Connect-Cloud Service los van de hoofdmappen van de AEM Communities-site die zijn bijgewerkt en die naar de nieuwe locatie verwijzen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>N.v.t.<br /> </td>
  </tr>
 </tbody>
</table>

### Diverse {#misc}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/community/templates</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie(s)</strong></td>
   <td><code>/libs/settings/community/templates</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Adobe heeft een migratiehulpprogramma beschikbaar gesteld op:</p> <p><a href="https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration">https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration</a></p> </td>
  </tr>
  <tr>
   <td><strong>Opmerkingen</strong></td>
   <td>De bestaande aangepaste sjablonen worden verplaatst naar <code>/conf/global/settings/community/template/&lt;groups/sites/functions&gt;</code></td>
  </tr>
 </tbody>
</table>

