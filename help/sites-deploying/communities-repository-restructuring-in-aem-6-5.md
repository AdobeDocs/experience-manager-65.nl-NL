---
title: Repositoregeling voor AEM Communities in punt 6.4
description: Leer hoe u de noodzakelijke wijzigingen aanbrengt om te migreren naar de nieuwe dataopslagstructuur in AEM 6.4 voor Communities.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: repo_restructuring
feature: Upgrading
exl-id: 4d2bdd45-a29a-4936-b8da-f7e011d81e83
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1003'
ht-degree: 0%

---

# Repositoregeling voor de herstructurering van AEM Communities in punt 6.5 {#repository-restructuring-for-aem-communities-in}

Zoals beschreven op het bovenliggende element [Herstructurering van de depositaris in AEM 6.4](/help/sites-deploying/repository-restructuring.md) op de pagina, moeten klanten die een upgrade uitvoeren naar AEM 6.5 deze pagina gebruiken om de werkinspanning te beoordelen die gepaard gaat met wijzigingen in de opslagplaats die gevolgen hebben voor de AEM Communities-oplossing. Sommige veranderingen vereisen het werk inspanning tijdens het AEM 6.5 verbeteringsproces, terwijl anderen tot een toekomstige verbetering kunnen worden uitgesteld.

**Met 6,5-upgrade**

* [Templates voor e-mailmeldingen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#e-mail-notification-templates)
* [Subscription Configurations](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#subscription-configurations)

**Voorafgaand aan toekomstige upgrade**

* [Badgingconfiguraties](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#badging-configurations)
* [Consoleontwerpen van klassieke gemeenschappen](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#classic-communities-console-designs)
* [Configuraties voor sociale aanmelding in facebook](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#facebook-social-login-configurations)
* [Configuraties taalopties](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#language-options-configurations)

* [Configuraties voor sociale aanmelding in pinterest](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#pinterest-social-login-configurations)
* [Scoringconfiguraties](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#scoring-configurations)
* [Configuraties voor sociale aanmelding voor twitters](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#twitter-social-login-configurations)
* [Dic](/help/sites-deploying/communities-repository-restructuring-in-aem-6-5.md#misc)

## Met 6,5-upgrade {#with-upgrade}

### Templates voor e-mailmeldingen {#e-mail-notification-templates}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/community/notifications</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><code>/libs/settings/community/notifications</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Handmatige migratie is nodig als u naar een nieuw pad wilt gaan onder "<code>/apps/settings</code>". U kunt de Manager van de Configuratie van Granite gebruiken om de migratie uit te voeren.</p> <p>U kunt de migratie uitvoeren door de eigenschap in te stellen <code>mergeList</code> tot <code>true</code> op de "<code>/libs/settings/community/subscriptions</code>" en voeg een <code>nt:unstructured</code> onderliggende node.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Subscription Configurations {#subscription-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/community/subscriptions</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><code>/libs/settings/community/subscriptions</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Handmatige migratie is nodig als u naar een nieuw pad wilt gaan onder "<code>/apps/settings</code>". U kunt de Manager van de Configuratie van Granite gebruiken om de migratie uit te voeren.</p> <p>U kunt de migratie uitvoeren door de eigenschap in te stellen <code>mergeList</code> tot <code>true</code> op de "<code>/libs/settings/community/subscriptions</code>" en voeg een <code>nt:unstructured</code> onderliggende node.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Configuraties controlewoorden {#watchwords-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td>/etc/watchwords</td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td>/libs/community/watchwords</td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>Er is een "Lazy Migration Task" beschikbaar om de Community Configurations op te schonen.<br /> <p>De taak verplaatst wachtwoorden van <code>/etc/watchwords</code> tot <code>/conf/global/settings/community/watchwords</code>.</p> <p>Als de aangepaste wachtwoorden in SCM worden opgeslagen, dan zouden zij aan moeten worden opgesteld <code>/apps/settings/...</code> en u moet ervoor zorgen dat er geen sprake is van een bedekking <code>/conf/global/settings/...</code> configuratie die voorrang zou krijgen.</p> <p>Migratietaak wordt verwijderd <code>/etc</code> locaties.</p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

## Voorafgaand aan toekomstige upgrade {#prior-to-upgrade}

### Badgingconfiguraties {#badging-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/community/badging</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><strong>Badge-regels:</strong></p> <p><code>/libs/settings/community/badging</code></p> <p><strong>Badge-afbeeldingen:</strong></p> <p>Voor standaardafbeeldingen: <code>/etc/community/badging/images are moved to /libs/community/badging/images</code></p> <p>Voor aangepaste afbeeldingen: <code>/content/community/badging/images</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Handmatige migratie is vereist.</p> <p>Als uw instantie de regels voor badging/scoring heeft aangepast, is er geen geautomatiseerde manier om alle regels onder een emmertje te plaatsen. De input van de klant vereist waarop conf emmer (globaal of specifiek) u voor uw plaats wilt gebruiken.</p> <p>Er is geen interface beschikbaar voor het configureren van de badging en scoring voor een site.</p> <p>Uitlijnen met nieuwe repository structuur:</p>
    <ol>
     <li>Maak een sitecontextemmertje met het gereedschap <strong>Configuratiebrowser</strong> krachtens <strong>Gereedschappen</strong></li>
     <li>Ga naar de hoofdmap van de site</li>
     <li>Set <code>cq:confproperty</code> naar het emmerpad waar u al uw instellingen wilt opslaan. Hetzelfde kan worden ingesteld via de site <strong>Wizard Bewerken - Cloudconfiguratie-invoer instellen</strong>.</li>
     <li>Verplaats relevante regels voor badging en scores van <code>/etc/community/*</code> naar het sitecontextemmertje dat in de vorige stap is gemaakt.</li>
     <li>Pas de regels van het badging en het schrapen eigenschappen van Regels op plaatshroot aan om relatieve verwijzingen naar nieuwe regelplaatsen te hebben.
      <ol>
       <li>Als de eigenschap bijvoorbeeld <code>cq:conf = /conf/we-retail</code>vervolgens <code>badgingRules [] = community/badging/rules</code> als de regels nu naar dit nieuwe emmertje worden verplaatst .</li>
      </ol> </li>
     <li>Pas op dezelfde manier de verwijzingen naar het schrapen van regels in een merkende regelknoop aan om een relatief pad te hebben.</li>
    </ol> <p> </p> <p>Tot slot schoon door het middel te verwijderen <code>/etc/community/badging</code></p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Consoleontwerpen van klassieke gemeenschappen {#classic-communities-console-designs}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/designs/social/console</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code>/libs/settings/wcm/designs/social/console</code></p> <p><code>/apps/settings/wcm/designs/social/console</code></p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>NVT</td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Configuraties voor sociale aanmelding in facebook {#facebook-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/facebookconnect</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/facebookconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/facebookconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle nieuwe Facebook Cloud Configurations moeten naar de nieuwe locatie worden gemigreerd.</p>
    <ol>
     <li>Bestaande configuraties in de vorige locatie migreren naar de nieuwe locatie.
      <ol>
       <li>Nieuwe Facebook Social Login Configurations handmatig opnieuw maken via de AEM-ontwerpinterface op <strong>Gereedschappen &gt; Cloud Servicen &gt; Configuratie van sociale aanmelding voor Facebook</strong>.<br /> of <br /> </li>
       <li>Kopieer nieuwe Facebook Cloud Configurations van vorige locatie naar de juiste nieuwe locatie, onder <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Als u de hoofdmap van de AEM Communities-site wilt bijwerken en wilt verwijzen naar de nieuwe configuratie voor sociale aanmelding van Facebook, stelt u de optie <code>[cq:Page]/jcr:content@cq:conf</code> eigenschap naar het absolute pad in de nieuwe locatie.</li>
     <li>Koppel de verouderde Facebook Connect-Cloud Service los van de basis van de AEM Communities-site die is bijgewerkt om naar de nieuwe locatie te verwijzen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Configuraties taalopties {#language-options-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/social/config/languageOpts</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><code>/libs/social/translation/languageOpts</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td>NVT<br /> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Configuraties voor sociale aanmelding in pinterest {#pinterest-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/pinterestconnect</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/pinterestconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/pinterestconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle nieuwe Pinterest Cloud Configurations moeten naar de nieuwe locatie worden gemigreerd.</p>
    <ol>
     <li>Bestaande configuraties in de vorige locatie migreren naar de nieuwe locatie.
      <ol>
       <li>Nieuwe Pinterest Social Login Configurations handmatig opnieuw maken via de AEM-ontwerpinterface op <strong>Gereedschappen &gt; Cloud Servicen &gt; Configuratie van sociale aanmelding voor Pinterest</strong>.<br /> of</li>
       <li>Kopieer nieuwe Pinterest Cloud Configurations van vorige locatie naar de juiste nieuwe locatie onder <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Als u een AEM Communities Site-hoofdmap wilt bijwerken, verwijst u naar de nieuwe Pinterest Social Login Configuration op basis van de instellingen in het dialoogvenster <code>[cq:Page]/jcr:content@cq:conf</code> eigenschap naar het absolute pad in de nieuwe locatie.</li>
     <li>Koppel de verouderde Pinterest Connect-Cloud Service los van de basis van de AEM Communities-site die is bijgewerkt om naar de nieuwe locatie te verwijzen.</li>
    </ol> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
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
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><code>/libs/settings/community/scoring</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Om met nieuwe bewaarplaatsstructuur te richten, kan het schrapen regels in worden opgeslagen <code>/apps/settings/</code> of /<code>conf/.../settings</code></p>
    <ol>
     <li>Voor <code>/apps/settings</code>, zou dit als globale of standaardregels handelen die in SCM worden beheerd.</li>
    </ol> <p>Contextbewuste configuraties maken in <code>/conf/</code> met CRXDELite:</p>
    <ol>
     <li>Maak de configuraties in de gewenste <code>/conf/.../settings</code> locatie<br /> </li>
     <li>De site van de Gemeenschappen moet <code>cq:conf </code>eigenschap ingesteld.
      <ol>
       <li>Indien niet <code>cq:conf</code> is ingesteld, worden scoringregels rechtstreeks gelezen van het opgegeven pad voor eigenschap '<code>scoringRules</code>' in het hoofdknooppunt van de site, bijvoorbeeld: <code>/content/we-retail/us/en/community/jcr:content</code></li>
      </ol> </li>
    </ol> <p>Overbodig verwijderen: de bron verwijderen <code>/etc/community/scoring</code></p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>NVT<br /> </td>
  </tr>
 </tbody>
</table>

### Configuraties voor sociale aanmelding voor twitters {#twitter-social-login-configurations}

<table>
 <tbody>
  <tr>
   <td><strong>Vorige locatie</strong></td>
   <td><code>/etc/cloudservices/twitterconnect</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><p><code class="code">/conf/global/settings/cloudconfigs/twitterconnect
       </code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/twitterconnect</code></p> <p> </p> </td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Alle nieuwe Twitter Cloud Configurations moeten naar de nieuwe locatie worden gemigreerd.</p>
    <ol>
     <li>Bestaande configuraties in de vorige locatie migreren naar de nieuwe locatie.
      <ol>
       <li>Nieuwe configuraties voor sociale aanmelding voor Twitters handmatig opnieuw maken via de AEM-ontwerpinterface op <strong>Gereedschappen &gt; Cloud Servicen &gt; Configuratie van sociale aanmelding Twitters</strong>.<br /> of <br /> </li>
       <li>Kopieer alle nieuwe Twitter Cloud Configurations van Vorige Locatie naar de juiste nieuwe locatie, onder <code>/conf/global or /conf/&lt;tenant&gt;</code>.</li>
      </ol> </li>
     <li>Werk om het even welke wortel van de Plaats van AEM Communities bij om naar de nieuwe Configuratie van de Sociale Aanmelding van de Twitter te verwijzen door te plaatsen <code>[cq:Page]/jcr:content@cq:conf</code> eigenschap naar het absolute pad in de nieuwe locatie.</li>
     <li>Koppel de oudere Twitter Connect-Cloud Service los van de hoofdmappen van de AEM Communities-site die zijn bijgewerkt om naar de nieuwe locatie te verwijzen.</li>
    </ol> </td>
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
   <td><code>/etc/community/templates</code></td>
  </tr>
  <tr>
   <td><strong>Nieuwe locatie of locaties</strong></td>
   <td><code>/libs/settings/community/templates</code></td>
  </tr>
  <tr>
   <td><strong>Herstructureringsrichtsnoeren</strong></td>
   <td><p>Adobe heeft een migratiehulpprogramma beschikbaar gesteld op:</p> <p><a href="https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration">https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration</a></p> </td>
  </tr>
  <tr>
   <td><strong>Notities</strong></td>
   <td>De bestaande aangepaste sjablonen worden verplaatst naar <code>/conf/global/settings/community/template/&lt;groups/sites/functions&gt;</code></td>
  </tr>
 </tbody>
</table>
