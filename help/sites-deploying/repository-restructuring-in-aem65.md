---
title: Repositoregeling herstructurering in AEM 6.5
seo-title: Repositoregeling herstructurering in AEM 6.5
description: Meer informatie over de herstructurering van de opslagplaats in AEM 6.5
seo-description: Meer informatie over de herstructurering van de opslagplaats in AEM 6.5
uuid: bc577c82-3279-4ddd-898c-607864868db0
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 274a7f5a-d509-4ca9-9ae5-30e48f34f171
docset: aem65
redirecttarget: /content/help/en/experience-manager/6-5/help/sites-deploying/repository-restructuring.html
translation-type: tm+mt
source-git-commit: bd0dc09ea230416ad3544d14440b7b74b80ec406

---


# Repositoregeling herstructurering in AEM 6.5 {#repository-restructuring-in-aem}

## Inleiding {#introduction}

Vóór AEM 6.5, werd de klantencode opgesteld in onvoorspelbare gebieden van JCR die onderhevig waren aan verandering op verbeteringen. Daarom was het gebruikelijk voor formele AEM-releases (grote versies, functiepakketten, servicepacks of hotfixes) om aangepaste code, configuratie of inhoud te overschrijven. Bovendien overschrijven wijzigingen door klanten soms de AEM-productcode of -inhoud, waardoor de productfunctionaliteit wordt verbroken.

Deze conflicten konden niet altijd automatisch worden opgelost, waardoor aanzienlijke verwerkingstijd nodig was om te markeren, en waarvoor menselijke interventie nodig was om op te lossen, waarvan de oplossing niet altijd duidelijk was. Door hiërarchieën voor AEM productcode en klantencode duidelijk te bepalen, kunnen deze conflicten worden vermeden.

Te dien einde, vanaf AEM 6.5 en om in toekomstige versies te worden voortgezet, wordt de inhoud geherstructureerd uit andere mappen in de opslagplaats, samen met richtlijnen over waar de inhoud naartoe gaat, met inachtneming van de volgende regels op hoog niveau: `/etc`

* AEM-productcode wordt altijd in geplaatst `/libs`, die niet mag worden overschreven door aangepaste code
* De aangepaste code moet worden geplaatst in `/apps`, `/content`en `/conf`

Dit artikel is in drie secties onderverdeeld, die het type inhoud vertegenwoordigen dat is verplaatst van `/etc`:

1. Configuratie
1. Client-Side bibliotheken
1. Overig

Elk gedeelte omvat:

* een tabel met de geherstructureerde locaties en de aanvullende context. In de nabije toekomst wordt verwacht dat de tabellen zullen worden opgemaakt in een platte structuur voor een betere leesbaarheid.
* een uitbreidingsstrategie die aangepaste code toestaat om AEM-toepassingscode onder uit te breiden. `/libs`

## Achterwaartse compatibiliteit {#backwards-compatibility}

In de meeste gevallen wordt achterwaartse compatibiliteit met de oude locaties gehandhaafd na de upgrade naar AEM 6.5. Dit wordt bereikt door de oude locaties die worden behouden en gerespecteerd door productcode, naast de nieuwe locaties die worden toegevoegd. In de meeste gevallen wordt voorwaardelijke logica gebruikt om te controleren of de oudere map bestaat en om inhoud van die map te lezen in plaats van de nieuwe locatie.

Op hun eigen chronologie na de verbetering 6.5, worden de klanten aangemoedigd om de oude plaatsen te verwijderen zodat wordt de inhoud in de nieuwe plaatsen gebruikt. In de onderstaande tabellen vindt u instructies om de nieuwe inhoudstructuur per locatie te volgen.

>[!NOTE]
>
>Een opgewaardeerde instantie ter plekke bevat naast de nieuwe locaties ook oude inhoudslocaties. Een nieuwe ontwikkelaarsinstallatie zal slechts de nieuwe plaatsen omvatten.

## De tabellen lezen {#how-to-read-the-tables}

De tabel in elke sectie bevat:

* de AEM-oplossing (sites, middelen, formulieren, enz.) waarvoor deze inhoud relevant is
* de oude locatie (6.4 en eerder)
* de nieuwe locatie 6.5
* Instructies voor het uitlijnen met de nieuwe inhoudsstructuur. Het kan bijvoorbeeld nodig zijn een script uit te voeren of bestanden handmatig te verplaatsen in de weken of maanden na een upgrade van 6.5
* De benadering die AEM heeft gebruikt om achterwaartse verenigbaarheid van oude inhoudsplaatsen voor klanten te handhaven die aan AEM 6.5 van een vorige versie bevorderen

## Configuratie {#configuration}

De inhoudsplaatsen in deze sectie verwijzen over het algemeen naar inhoud die onder een `/settings` omslag onder `/libs`, `/apps`of `/conf`.

### Uitbreidingsstrategie {#extensibility-strategy}

Over het algemeen, maar met een paar uitzonderingen, kan de inhoud onder deze sectie worden uitgebreid gebruikend de [ eigenschap van de Configuratie](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html) van de Context Apache Sling.

In een notendop staat Context Aware Configuration toe dat inhoud in één deel van de repository meerdere keren wordt overschreven door inhoud in andere delen van de repository. Inhoud in `/libs` kan bijvoorbeeld worden overschreven door inhoud in `/apps`, die vervolgens kan worden overschreven door inhoud in `/conf`. Bovendien kan inhoud in een algemene map onder `/conf` worden overschreven door een specifieke &quot;huurder&quot; of &quot;site&quot; (bijvoorbeeld `/conf/we-retail/settings`).

Typisch, wordt de Context Aware Configuratie gebruikt als strategie om eigenschapconfiguraties uit te breiden, maar er zijn gevallen waar het door andere inhoudstypes wordt gebruikt.

De lijst omvat hieronder een extra kolom genoemd &quot;Type van Configuratie&quot;om te verklaren in welke mate een configuratie kan worden bedekt. Hier is extra detail op deze configuratietypen:

**niet contextgevoelig**

* Bronnen bevinden zich toevallig in context-bewuste mapstructuren (zoals `/libs/settings`), maar worden altijd via het absolute pad vermeld, zodat contextbewustzijn niet van kracht is.
* De middelen zouden overal kunnen zijn. U kunt DRM-licenties voor middelen bijvoorbeeld instellen op `/content/my-customer/licenses/creative-commons.html`
* Voorbeelden:

   * Workflowscripts -> `/apps/settings/workflow/scripts/noop.ecma`
   * Middelen-DRM-licenties -> `/apps/settings/dam/drm/my-license`

**alleen wereldwijd**

* Functie met alleen globale configuratie
* Neem als referentiepunt de prioriteit van instellingen in dit voorbeeld: `/libs/settings` &lt; `/apps/settings` &lt; `/conf/global`

* AEM steunt slechts globale configuratie, en niet huurde configuraties
* AEM zal altijd beginnen configuraties op /conf/global niveau eerst op te zoeken

* Voorbeelden:

   * Workflow Launchers -> `/libs/settings/workflow/launcher`
   * Workflowmodellen -> `/conf/global/settings/workflow/models`

**huurder**

* Voor huurdersbewuste configuraties, zie dit voorbeeld voor de belangrijkheid van configuratiepaden: `/libs/settings` &lt; `/apps/settings` &lt; `/conf/global` &lt; `/conf/we-retail`, waarbij wij-retail de huurnaam is. Configuraties waarbij rekening wordt gehouden met huurders ondersteunen ook subhuurders.

* AEM ondersteunt getenantiseerde configuraties. Eigenschap wordt `cq:conf` in hiërarchie gerespecteerd
* Voorbeelden:

   * Bewerkbare sjablonen -> `/conf/we-retail/settings/wcm/templates`
   * Cloud Configs -> `/conf/we-retail/settings/cloudsettings`

<table>
 <tbody>
  <tr>
   <td><strong>Oplossing</strong></td>
   <td><strong>Vorige locatie</strong><br /> </td>
   <td><strong>Nieuwe locatie</strong></td>
   <td><strong>Contextgevoelig configuratietype</strong><br /> </td>
   <td><strong>Achterwaartse-compatibiliteitsbenadering</strong></td>
   <td><strong>Vereisten om op het recentste model te richten</strong></td>
  </tr>
  <tr>
   <td>AEM-sites/AEM-formulieren</td>
   <td><p><code>/etc/cloudservices/typekit</code></p> <p><code>/etc/cloudservices/recaptcha</code></p> <p><code>/etc/cloudservices/echosign</code></p> </td>
   <td><p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/typekit</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/recaptcha</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/echosign</code></p> </td>
   <td>huurder</td>
   <td><p>Oudere cloudservices.</p> <p>Blijft op een verbetering ter plaatse. Code voor het weergeven en lezen van de bestanden die nog in AEM aanwezig zijn als fallback.</p> </td>
   <td>Het Lazy-hulpprogramma voor inhoudsmigratie kan worden geactiveerd door de gebruikersinterface van Forms Migration om het bestand automatisch om te zetten in het nieuwe pad.<br /> </td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/cloudservices/fdm</code></td>
   <td><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/fdm</code></td>
   <td>huurder</td>
   <td><p>Oudere cloudservices.</p> <p>Blijft op een op zijn plaats bevorderde opstelling. Code voor het weergeven en lezen van de bestanden die nog in AEM aanwezig zijn als fallback.</p> </td>
   <td>Het Lazy-hulpprogramma voor inhoudsmigratie kan worden geactiveerd door de gebruikersinterface van Forms Migration om het bestand automatisch om te zetten in het nieuwe pad.</td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/adhocassetshare</code></td>
   <td><code>/libs/settings/dam/adhocassetshare</code></td>
   <td>huurder</td>
   <td>Oudere inhoudstructuren krijgen een hogere prioriteit dan nieuwe, OTB-structuren.</td>
   <td>Aanpassingen op projectniveau moeten worden geknipt en geplakt in het equivalent <code>/apps</code> of de <code>/conf</code> paden.</td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/workflow/notification/email/downloadasset</code></td>
   <td><code>/libs/settings/dam/workflow</code></td>
   <td>huurder</td>
   <td>Oudere inhoudstructuren krijgen een hogere prioriteit dan nieuwe, OTB-structuren.</td>
   <td>Aanpassingen op projectniveau moeten worden geknipt en geplakt in het equivalent <code>/apps</code> of de <code>/conf</code> paden.</td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/drm/licenses/</code></td>
   <td><code>/libs/settings/dam/drm</code></td>
   <td>niet contextgevoelig</td>
   <td>Oudere inhoudstructuren krijgen een hogere prioriteit dan nieuwe, OTB-structuren.</td>
   <td>Aanpassingen op projectniveau moeten worden geknipt en geplakt in het equivalent <code>/apps</code> of de <code>/conf</code> paden.</td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/indesign/scripts</code></td>
   <td><code>/libs/settings/dam/indesign</code></td>
   <td>huurder</td>
   <td>Oudere inhoudstructuren krijgen een hogere prioriteit dan nieuwe, OTB-structuren.</td>
   <td><p>Aanpassingen op projectniveau moeten worden geknipt en geplakt onder het equivalent <code>/apps</code> of de <code>/conf</code> paden.</p> <p>Wanneer het runnen van het aangepaste werkschema van de Ingestie van Activa, zouden verwijzingen naar de oude plaats in /etc nog bestaan in de Configuratie van het Proces van de Extractie van Media. Samen met het bewegen van de manuscripten uit /etc naar de gelijkwaardige /apps en /conf wegen, moeten de aangepaste het procesargumenten van het Proces van de Extractie van Media van absolute in relatieve wegen worden veranderd, om voor de veranderingen aan te passen.</p> <p>Zie <a href="https://helpx.adobe.com/experience-manager/6-2/help/assets/indesign.html">deze pagina</a>voor meer informatie.</p> <p> </p> </td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/video</code></td>
   <td><code>/libs/settings/dam/video</code></td>
   <td>huurder</td>
   <td>Oudere inhoudstructuren krijgen een hogere prioriteit dan nieuwe, van de box-structuren.</td>
   <td>Aanpassingen op projectniveau moeten worden geknipt en geplakt in het equivalent <code>/apps</code> of de <code>/conf</code> paden.</td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/notification/email/default</code></td>
   <td><code>/libs/settings/dam/notification</code></td>
   <td>huurder</td>
   <td>Oudere inhoudstructuren krijgen een hogere prioriteit dan nieuwe, van de box-structuren.</td>
   <td>Aanpassingen op projectniveau moeten worden geknipt en geplakt in het equivalent <code>/apps</code> of de <code>/conf</code> paden.</td>
  </tr>
  <tr>
   <td>AEM-sites/AEM-middelen</td>
   <td><code>/etc/designs</code> </td>
   <td><code>/libs/settings/wcm/designs</code></td>
   <td>niet contextgevoelig</td>
   <td><p>De gebruikers van de Diensten zijn zich van oude plaats bewust.</p> <p>Configuraties vanaf de oude locatie worden in overweging genomen</p> </td>
   <td><br /> Verplaats aangepaste inhoud van <code>/etc/design</code> naar <code>/apps/settings/wcm/design</code> voor uitlijning met de nieuwe repository structuur. Overweeg in de toekomst een upgrade van uw sites uit te voeren om de functionaliteit voor bewerkbare sjablonen te gebruiken, die de ontwerpmodus en dus ook deze inhoud vervangt.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/scaffolding</code></td>
   <td><p><code>/libs/settings/wcm/template-types/scaffolding/scaffolding</code></p> <p><code>/apps/settings/wcm/template-types/scaffolding/scaffolding</code></p> </td>
   <td>niet met behoud van context</td>
   <td>De componenten op de oude locatie onder <code>/etc/scaffolding</code> blijven functioneren, maar zijn afgekeurd.</td>
   <td>Adobe raadt u aan de nieuwe basiscomponenten onder de nieuwe locatie te gebruiken.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/blueprints</code></td>
   <td><p>/libs/msm voor uit de doosSchermen en de blauwdruk van de Handel configuraties</p> <p> </p> </td>
   <td>niet contextgevoelig</td>
   <td><p>De gebruikers van de Diensten zijn zich van de oude plaats bewust.</p> <p>Configuraties vanaf de oude locatie worden in overweging genomen.</p> </td>
   <td>De configuraties moeten naar de nieuwe locaties worden gekopieerd.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/mobile</code></td>
   <td><code>/libs/settings/mobile</code></td>
   <td>huurder</td>
   <td>De eigenschap hefboomwerkingen de Manager van de Configuratie en steunt nog de oude plaats als reserve.</td>
   <td>
    <ol>
     <li>De configuraties verplaatsen van <code>/etc</code> naar <code>/conf/&lt;tenant&gt;/settings/mobile</code></li>
     <li>Werk vervolgens de verwijzing in de inhoud als volgt bij:</li>
    </ol> <p><code>/content/&lt;tenant&gt;/jcr:content/cq:deviceGroups{String[]}=mobile/groups/responsive</code></p> </td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/msm/rolloutConfigs</code></td>
   <td><code>/libs/msm/wcm/rolloutconfigs</code></td>
   <td>N.v.t.</td>
   <td><p>De verbruikende diensten zijn zich van de oude plaats bewust.</p> <p>Als configuraties worden gedetecteerd op de oude locatie, worden deze gebruikt.</p> </td>
   <td>Om zich aan het nieuwe model te richten, moeten de configuraties in de nieuwe plaatsen worden gecreeerd, en de oude onder <code>/etc</code> moeten worden geschrapt.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/segmentation/contexthub</code></td>
   <td><code>/conf/we-retail/settings/wcm/segments</code></td>
   <td>huurder</td>
   <td><p>Segmenten van de oude locatie:</p>
    <ul>
     <li>Blijf in de alleen-lezen modus in de publieksconsole.</li>
     <li>Nog steeds geladen op de pagina (als het opgegeven pad is geselecteerd in <strong>Pagina-eigenschappen &gt; Aanpassing &gt; Pad</strong>segmenten).</li>
     <li>Kan worden gebruikt voor doelinhoud.</li>
    </ul> </td>
   <td>Met het migratiehulpprogramma <a href="/help/sites-deploying/upgrading-code-and-customizations.md#migrateconfigurations">voor</a> segmenten kunt u migreren naar de nieuwe locatie.</td>
  </tr>
  <tr>
   <td>AEM-gemeenschappen</td>
   <td><code>/etc/social/config/languageOpts</code></td>
   <td><code>/libs/social/translation/languageOpts</code></td>
   <td>N.v.t.</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>AEM-gemeenschappen</td>
   <td><code>/etc/community/templates</code></td>
   <td><code>/libs/settings/community/templates</code></td>
   <td> </td>
   <td><p>De code is zich bewust van de plaats van het oude malplaatje. Bestaande sjablonen blijven doorverwijzen en lezen/schrijven van <code>/etc</code>.</p> <p><br /> Voor e-mailmalplaatjes, als de klant reeds zijn douanesjablonen bij een andere weg door de wortelweg <strong>van</strong> Malplaatjes in de Configuratie <strong></strong> van het E-mailAntwoord van de Gemeenschappen AEM had te vormen zou het blijven zoals het is.</p> </td>
   <td><p>Een <a href="https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/master/bundles/communities-template-migration" target="_blank">migratiehulpprogramma</a> kan worden uitgelijnd op het nieuwste AEM Communities-sjabloonmodel.</p> </td>
  </tr>
  <tr>
   <td>AEM-gemeenschappen</td>
   <td><code>/etc/community/badging</code></td>
   <td><p><strong>Badge-regels:</strong></p> <p><code>/libs/settings/community/badging</code></p> <p><strong>Badge-afbeeldingen:</strong></p> <p>De afbeeldingen in het vak 'Uit' op de oude locatie <code>/etc/community/badging/images</code> worden verplaatst naar <code>/libs/community/badging/images </code> </p> <p> </p> <p>Aangepaste afbeeldingen worden verplaatst naar <code>/content/community/badging/images</code>.</p> <p> </p> </td>
   <td>huurder</td>
   <td><p>De code is zich bewust van de oude badging wegen.</p> <p><br /> Eerst wordt gecontroleerd of er oudere paden<br /> bestaan. Als ze niet aanwezig zijn, worden de nieuwe paden gebruikt.</p> </td>
   <td><p>Handmatige migratie is vereist om te kunnen worden uitgelijnd op het nieuwste model. Volg onderstaande stappen om dit te bereiken:</p>
    <ol>
     <li>Maak een sitecontextemmertje met gebruik van de configuratiebrowser onder <strong>Gereedschappen</strong></li>
     <li>Ga naar de hoofdmap van de site</li>
     <li>Stel de <code>cq:conf</code> eigenschap in op het emmerpad waar u alle configuraties wilt opslaan. Hetzelfde kan worden ingesteld via de wizard <strong>Site bewerken - Cloud Config Input</strong>instellen en de wijzigingen vervolgens opslaan</li>
     <li>Verplaats de relevante regels voor badging en scoring van <code>etc/community/*</code> naar het sitecontextemmertje dat in de vorige stap is gemaakt</li>
     <li>Pas de eigenschappen <code>badgingRules</code> en <code>scoringRules</code> eigenschappen in de hoofdmap van de site aan om relatieve verwijzingen naar de nieuwe regellocaties te bevatten. Als <code>cq:conf</code> bijvoorbeeld is ingesteld op <code>/conf/we-retail</code>, <code>badgingRules</code> wordt de waarde voor <code>community/badging/rules</code> als de regels nu naar dit nieuwe emmertje worden verplaatst</li>
     <li>Pas op dezelfde manier de verwijzingen naar het noteren van regels in een merkingsregelknoop aan om een relatieve weg te hebben.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><p><code>/etc/cloudservices/facebookconnect</code></p> <p><code>/etc/cloudservices/twitterconnect</code></p> <p><code>/etc/cloudservices/pinterestconnect</code></p> </td>
   <td><p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/facebookconnect</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/twitterconnect</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/pinterestconnect</code></p> </td>
   <td>huurder</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>AEM-gemeenschappen</td>
   <td><code>/etc/community/scoring</code></td>
   <td><code>/libs/settings/community/scoring</code></td>
   <td> </td>
   <td><p>De code is zich bewust van de oude badging wegen.</p> <p><br /> Eerst wordt gecontroleerd of er oudere paden<br /> bestaan. Als ze niet aanwezig zijn, worden de nieuwe paden gebruikt.</p> </td>
   <td><p>Handmatige migratiestappen zijn vereist voor uitlijning met het nieuwste model.</p> <p>De stappen zijn hetzelfde in de bovenstaande badgingregels.</p> </td>
  </tr>
  <tr>
   <td>AEM-gemeenschappen</td>
   <td><code>/etc/community/notifications</code></td>
   <td><code>/libs/settings/community/notifications</code></td>
   <td>niet contextgevoelig</td>
   <td><p>Deze configuraties zijn niet compatibel met oudere versies. Zie de kolom "Vereisten voor uitlijning op het meest recente model" voor stappen voor het migreren naar de nieuwe locaties.<br /> </p> <br /> </td>
   <td><p>Een handmatige migratie is vereist om zich aan het recentste model te richten. U kunt de Manager van de Configuratie van Granite gebruiken om de configuraties naar de nieuwe weg onder te bewegen <code>/apps/settings</code>.</p> <p>Daarom moet u het <code>mergeList</code> bezit aan waar op de <code>/libs/settings/community/subscriptions</code> knoop plaatsen en dan een <code>nt:unstructured</code> kindknoop toevoegen.<br /> </p> </td>
  </tr>
  <tr>
   <td>AEM-gemeenschappen</td>
   <td><code>/etc/community/subscriptions</code></td>
   <td><code>/libs/settings/community/subscriptions</code></td>
   <td>niet contextgevoelig</td>
   <td>Deze configuraties zijn niet compatibel met oudere versies. Zie de kolom "Vereisten voor uitlijning op het meest recente model" voor stappen voor het migreren naar de nieuwe locaties.</td>
   <td><p>Een handmatige migratie is vereist om zich aan het recentste model te richten. U kunt de Manager van de Configuratie van Granite gebruiken om de configuraties naar de nieuwe weg onder te bewegen <code>/apps/settings</code>.</p> <p>Daarom moet u het <code>mergeList</code> bezit aan waar op de <code>/libs/settings/community/subscriptions</code> knoop plaatsen en dan een <code>nt:unstructured</code> kindknoop toevoegen.</p> </td>
  </tr>
  <tr>
   <td>AEM-gemeenschappen</td>
   <td><code>/etc/socialconfig/srpc/defaultconfiguration</code></td>
   <td><code>/conf/global/settings/community/srpc/defaultconfiguration</code></td>
   <td>global</td>
   <td>Deze configuraties zijn achterwaarts compatibel. Als de oude paden worden gevonden, worden deze gebruikt. Anders hebben de nieuwe paden voorrang.</td>
   <td><p>Lazy Content Migration Task is beschikbaar in de vorm van <code>CQ64CommunitiesConfigsCleanupTask</code>.</p> <p>Raadpleeg de documentatie bij <a href="/help/sites-deploying/lazy-content-migration.md" target="_blank"></a>Lazy Migration voor meer informatie.</p> </td>
  </tr>
  <tr>
   <td>AEM-gemeenschappen</td>
   <td><code>/etc/watchwords</code></td>
   <td><code>/libs/community/watchwords</code></td>
   <td>N.v.t.</td>
   <td>Deze configuraties zijn achterwaarts compatibel. Als de oude paden worden gevonden, worden deze gebruikt. Anders hebben de nieuwe paden voorrang.</td>
   <td><p>Lazy Content Migration Task is beschikbaar in de vorm van <code>CQ64CommunitiesConfigsCleanupTask</code>.</p> <p>Wachtwoorden moeten handmatig van <code>/etc/watchwords</code> naar <code>/conf/global/settings/community/watchwords</code>.</p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/models</code></td>
   <td><p><code>/libs/settings/workflow/models</code></p> <p><code>/conf/global/settings/workflow/models</code> </p> <p><code>/var/workflow/models</code></p> </td>
   <td>global</td>
   <td><p>De oude locatie wordt gebruikt als deze aanwezig is en er geen configuratie bestaat in <code>/libs</code> of <code>/conf</code>.</p> <p>Bij het bewerken van OTB-workflowmodellen moeten contextbewuste overlays worden gemaakt om ze te kunnen wijzigen. <code>/conf</code></p> <p>Het exporteren van pakketten moet het model in <code>/libs</code> of <code>/conf</code> en het runtimemodel in <code>/var/workflow/models.</code></p> </td>
   <td><p>Nieuw gemaakte modellen worden op de <code>/conf/global/settings</code> locatie gemaakt.</p> <p>Alle bewerkingen in <code>/etc</code> of <code>/libs</code> <code>/conf/global/settings</code> vereisen dat u expliciet een overschrijving maakt voordat u kunt bewerken. De knop Bewerken moet zijn geselecteerd. Hierdoor <code>/conf</code> wordt de overschrijving gemaakt en kan deze worden bewerkt.</p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/launcher</code></td>
   <td><p><code>/libs/settings/workflow/launcher</code></p> <p><code>/conf/global/settings/workflow/launcher</code></p> </td>
   <td>global</td>
   <td>De verouderde plaats wordt gebruikt als heden en geen configuratie<br /> bestaat in <code>/libs</code> of <code>/conf</code> plaatsen. Op deze manier blijven aangepaste draagraketten behouden.</td>
   <td><p>Nieuw gemaakte of bewerkte startconfiguraties bevinden zich op de <code>/conf</code> locatie.</p> <p>Alle draagraketten moeten van de oude <code>/etc</code> locatie naar<code> /conf/global/settings/workflow/launcher.</code></p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/models</code></td>
   <td><p><code>/libs/settings/workflow/models</code></p> <p><code>/conf/global/settings/workflow/models</code></p> </td>
   <td>global</td>
   <td>De verouderde plaats wordt gebruikt als heden en geen configuratie<br /> bestaat in <code>/libs</code> of <code>/conf</code> plaatsen. Op deze manier blijven aangepaste workflowmodellen behouden.</td>
   <td><p>Alle workflowmodellen moeten worden verplaatst van de oude <code>/etc</code> locatie naar <code>/conf/global/settings/workflow/models</code>.</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/notification</code></td>
   <td><p><code>/libs/settings/workflow/notification</code></p> <p><code>/conf/global/settings/workflow/notification</code></p> </td>
   <td>niet contextgevoelig</td>
   <td><p>Voor achterwaartse verenigbaarheid, wordt de erfenisplaats gebruikt als heden.</p> <p>Eerder moesten sjablonen uit het vak worden overschreven door ze in te bewerken <code>/etc</code>. Overschrijving moet nu worden opgeslagen in <code>/conf/global</code>.</p> </td>
   <td>Raadpleeg de documentatie bij de workflow voor meer informatie.<br /> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/cloudservices/translation</code></td>
   <td><p><code>/libs/settings/cloudconfigs/translation/translationcfg</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translation/translationcfg</code></p> <p> </p> </td>
   <td>huurder</td>
   <td>Oudere cloudservices. Wordt gecontinueerd op een installatie die op de plaats is geüpgraded. Code om ze te vermelden en te lezen is nog steeds aanwezig in het product als fallback.</td>
   <td><p>Als u cloudconfiguraties wilt verplaatsen naar <code>/conf</code>:</p>
    <ul>
     <li>Configuraties maken met de nieuwe aanraakinterface<br /> of<br /> </li>
     <li>De configuraties kopiëren van <code>/etc/cloudservices/translation</code> naar de respectievelijke nieuwe locatie(s)</li>
    </ul> <p>Zodra dit wordt gedaan, moeten de configuraties met Plaatsen via <strong>Plaatsen &gt; Eigenschappen</strong> in het gebruikersinterface worden geassocieerd.</p> <p><em>Opmerking: Dit werkt alleen als de vertaal-connectors compatibel zijn met AEM 6.5.</em></p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/cloudservices/msft-translation</code></td>
   <td><p><code>/libs/settings/cloudconfigs/translation/msft-translation</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudconfigs/translation/msft-translation</code></p> </td>
   <td>huurder</td>
   <td>Oudere cloudservices. Wordt gecontinueerd op een installatie die op de plaats is geüpgraded. Code om ze te vermelden en te lezen is nog steeds aanwezig in het product als fallback.</td>
   <td><p>Als u cloudconfiguraties wilt verplaatsen naar <code>/conf</code>:</p>
    <ul>
     <li>Configuraties maken met de nieuwe aanraakinterface of<br /> </li>
     <li>Oudere configuraties kopiëren van <code>/etc/cloudservices/translation</code> naar de respectievelijke nieuwe locatie(s)</li>
    </ul> <p>Zodra dit wordt gedaan, moeten de configuraties met Plaatsen via <strong>Plaatsen &gt; Eigenschappen</strong> in het gebruikersinterface worden geassocieerd.</p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/cloudsettings</code></td>
   <td><p><code>/libs/settings/cloudsettings</code></p> <p><code>/conf/&lt;tenant&gt;/settings/cloudsettings</code></p> </td>
   <td>huurder</td>
   <td><p>Bestaande vermeldingen onder <code>/etc</code> blijven van kracht bij het upgraden van het exemplaar.</p> <p>Als u na de upgrade toegang krijgt tot de interface voor cloudinstellingen, kopieert u de bestaande cloudinstellingen naar de nieuwe opslagplaats en behoudt u de bestaande inhoud voor achterwaartse compatibiliteit.</p> </td>
   <td><p>Inhoudsmodellen zijn hetzelfde, alleen de locatie is gewijzigd en uitgelijnd op contextgevoelige configuraties.</p> <p>De <a href="/help/sites-deploying/lazy-content-migration.md">Lazy-migratietaak</a> die deze wolkenmontages behandelt zal de volgende acties uitvoeren:</p>
    <ul>
     <li>Bestaande wolkeninstellingen kopiëren naar <code>/etc/cloudsettings</code> <code>/conf/global/settings/cloudsettings</code></li>
     <li>Alle onderliggende items verwijderen van <code>/etc/cloudsettings</code></li>
    </ul> <p>Er zijn echter handmatige stappen vereist na de upgrade en voordat de lazy migratietaken worden uitgevoerd:</p>
    <ul>
     <li>Alle verwijzingen waarnaar wordt verwezen, <code>/etc/cloudsettings/*</code> moeten worden bijgewerkt om naar <code>/conf/global</code></li>
    </ul> <p>Voorbehoud:</p>
    <ul>
     <li>De <code>/etc/cloudsettings</code> container moet bewaard blijven</li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/cloudservices/dmscene7</code></td>
   <td><code>/conf/global/settings/cloudservices/dmscene7</code></td>
   <td>alleen wereldwijd</td>
   <td><p>De configuratie van de wolk voor Dynamische Media - Scene7 (<code>dynamicmedia_scene7</code> runmode) opstelling zal bij de zelfde plaats blijven. Het proces werkt zoals het is. Als u de waarde van de wolkenconfiguratie moet aanpassen, dan zijn er twee opties om dat te doen:</p>
    <ol>
     <li>Werk een bestaande configuratie bij via de oude interface voor cloudconfiguratie.</li>
     <li>Maak een nieuwe cloudconfiguratie via de nieuwe aanraakinterface. Dit heeft een hogere prioriteit dan de oude.</li>
    </ol> </td>
   <td><p>Als u wilt uitlijnen op het meest recente model, moet u het script uitvoeren dat zich bevindt op:</p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/presets/viewer</code></td>
   <td><p><code>/libs/settings/dam/dm/presets/viewer</code></p> <p><code>/conf/global/settings/dam/dm/presets/viewer</code></p> </td>
   <td>alleen wereldwijd</td>
   <td><p>De voorinstellingen voor de OTB-viewer zijn alleen beschikbaar op de nieuwe locatie, terwijl de aangepaste viewer-voorinstelling nog steeds actief is <code>/etc</code> totdat een wijziging is doorgevoerd.</p> <p>Nadat deze is gewijzigd, wordt deze via Lazy Migration op de nieuwe locatie opgeslagen. De insluitingsafbeeldingsserver bekijkt zowel het oude als het nieuwe pad bij ontvangst van een aanvraag. Daarom is het niet nodig om hun insluitcode of URL te wijzigen.</p> </td>
   <td><p>De voorinstelling voor de viewer buiten het vak is alleen beschikbaar op de nieuwe locatie. Voor de aangepaste viewer-voorinstelling moet u het migratiescript op deze locatie uitvoeren:</p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> <p>Net als bij het geval van achterwaartse compatibiliteit hoeft u de code copyURL/embed niet aan te passen om naar te wijzen <code>/conf</code>. Het bestaande verzoek aan <code>/etc</code> zal onder de kap aan de correcte inhoud van worden opnieuw verpletterd <code>/conf</code>.</p> </td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/imageserver/macros</code></td>
   <td><code>/conf/global/settings/dam/dm/presets/macro</code></td>
   <td>alleen wereldwijd</td>
   <td>De onderliggende macro <code>/etc</code> is nog steeds geldig. Als u het wijzigt, wordt het gewijzigde knooppunt naar de nieuwe locatie onder <code>/conf</code> via een Lazy Migration-taak verplaatst.</td>
   <td><p>U moet het migratiescript bij deze plaats in werking stellen:</p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> <p> </p> </td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/video/dynamicmedia/Adaptive Video Encoding</code></td>
   <td><code>/libs/settings/dam/dm/presets/video/jcr:content/Adaptive Video Encoding</code></td>
   <td>N.v.t.</td>
   <td><p>Het videoprofiel in het vak Uit wordt verwijderd zonder dat de eigenschap voor elementmappen wordt bijgewerkt naar de koppeling met het profiel.</p> <p>Het coderingsproces heeft ingebouwde vertaling tussen de oude en nieuwe locatie. Het oude pad wordt omgezet in het nieuwe profielpad.</p> </td>
   <td>Geen wijzigingen vereist.</td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/video/dynamicmedia</code></td>
   <td><code>/conf/global/settings/dam/dm/presets/video/jcr:content</code></td>
   <td>alleen wereldwijd</td>
   <td><p>Het aangepaste videoprofiel blijft ongewijzigd totdat u het wijzigt.</p> <p>Vervolgens wordt het bestand naar de nieuwe locatie verplaatst via een Lazy Migration-taak. Dit is vergelijkbaar met de voorinstelling voor video buiten het vak bij het coderen van opzoekopdrachten. Het coderingsproces beschikt over een ingebouwde padconvertor die eerst naar een oude locatie zoekt en vervolgens naar de nieuwe locatie voor het videoprofiel.</p> </td>
   <td><p>Als u wilt uitlijnen op het meest recente model, kunt u het migratiescript uitvoeren onder:</p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> <p> </p> </td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/cloudservices/dynamicmediaservices</code></td>
   <td><code>/conf/global/settings/dam/dm/cloudservices/dynamicmediaservices</code></td>
   <td>alleen wereldwijd</td>
   <td><p>Deze wolkenconfiguratie voor Dynamische Media hybride opstelling (<code>dynamicmedia</code> runmode) zal bij de zelfde plaats blijven. Het proces werkt zoals het is. Als u de configuratiewaarde moet aanpassen, kunt u het op twee manieren doen.</p>
    <ol>
     <li>Werk een bestaande config via de oude UI van de wolkenconfiguratie bij.</li>
     <li>Maak een nieuwe cloudconfiguratie via de nieuwe aanraakinterface. Dit heeft een hogere prioriteit dan de oude.</li>
    </ol> </td>
   <td><p>U moet het migratiescript in werking stellen om zich aan het recentste model te richten. U kunt het script op deze locatie vinden:<br /> </p>
    <ul>
     <li><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/cloudservices/youtube</code></td>
   <td><code>/libs/settings/dam/dm/youtube</code></td>
   <td>alleen wereldwijd</td>
   <td><p>De wolkenconfig voor de opstelling DM-Youtube zal bij de zelfde plaats blijven. Het proces werkt zoals het is. Als u de configuratiewaarde van de cloud moet aanpassen, kunt u dit op twee manieren doen:</p>
    <ol>
     <li>Werk een bestaande config via oude wolkenconfig UI bij.</li>
     <li>Maak een nieuwe cloud config via de nieuwe aanraakinterface. Dit heeft een hogere prioriteit dan de oude.</li>
    </ol> </td>
   <td><p>U kunt een migratiescript in werking stellen om zich aan het recentste model te richten. Het script is beschikbaar op de volgende locatie:<br /> </p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> <p> </p> <p> </p> </td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/presets/analytics</code></td>
   <td><code>/libs/settings/dam/dm/analytics</code></td>
   <td>alleen wereldwijd</td>
   <td>Geen actie vereist.</td>
   <td><p>U kunt een migratiescript in werking stellen om zich aan de recentste wijze te richten. Het script is beschikbaar op de volgende locatie:<br /> </p> <p><em>https://serveraddress:serverport/libs/settings/dam/dm/presets.migratedmcontent.json</em></p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><p><code>/etc/notification/email/default/com.day.cq.replication</code></p> <p><code>/etc/notification/email/default/com.day.cq.wcm.core.page</code></p> </td>
   <td><code>/libs/settings/notification-templates</code></td>
   <td>alleen wereldwijd</td>
   <td>De sjablonen in <code>/etc/notification/email/default/</code> krijgen voorrang op de sjablonen in <code>/libs/settings/notification-templates</code>.</td>
   <td>Om zich aan het recentste model te richten, kunt u nieuwe malplaatjes onder creëren <code>/apps/settings/notification-templates</code> en nieuwe wijzigingen daar uitvoeren.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><p><code>/etc/msm/rolloutconfigs/launch</code></p> <p><code>/etc/msm/rolloutconfigs/pushonmodifyshallow</code></p> </td>
   <td><p><code>/libs/msm/launches/rolloutconfigs/launch</code></p> <p><code>/libs/msm/launches/rolloutconfigs/pushonmodifyshallow</code></p> </td>
   <td>N.v.t.</td>
   <td><p>De gebruikers van de Diensten zijn zich van de oude plaats bewust.</p> <p>Als configuraties worden gedetecteerd op de oude locatie, worden deze gebruikt.</p> </td>
   <td>Om zich aan het nieuwe model te richten, moeten de configuraties in de nieuwe plaatsen worden gecreeerd, en de oude onder <code>/etc</code> moeten worden geschrapt.</td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/translation/supportedLanguages</code></td>
   <td><p><code>/libs/settings/translation/supportedLanguages</code></p> <p><code>/apps/settings/translation/supportedLanguages</code></p> </td>
   <td>niet contextgevoelig</td>
   <td>Een voorbehoud is dat aangepaste talen aan de lijst moeten worden toegevoegd.<br /> </td>
   <td>Bedek de nieuwe lijst en werk deze bij met extra talen (indien van toepassing). Het kopiëren van de oude lijst naar de <code>/apps</code> locatie werkt ook.</td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/models/translation/translation_rules.xml</code></td>
   <td><p><code>/libs/settings/translation/rules/translation_rules.xml</code></p> <p><code>/apps/settings/translation/rules/translation_rules.xml</code></p> <p><code>/conf/global/settings/translation/rules/translation_rules.xml</code></p> </td>
   <td>alleen wereldwijd</td>
   <td>Wordt voortgezet op een opgewaardeerde installatie. Code om ze weer te geven en te lezen die nog in het product aanwezig zijn.</td>
   <td>Kopieer het XML-bestand van <code>/etc</code> naar <code>/libs</code> of <code>/conf</code>. U kunt ook<strong> het bestand </strong>verwijderen uit <code>/etc</code>.</td>
  </tr>
 </tbody>
</table>

## Client-Side bibliotheken {#client-side-libraries}

[Client-Side Libraries](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/clientlibs.html) zijn javascript- en CSS-code die in de browser worden verwerkt.

### Uitbreidingsstrategie {#extensibility-strategy-1}

AEM biedt een uitbreidbaarheidsframework om meerdere JavaScript-bestanden toe te voegen. Elk bestand met dezelfde eigenschap ‘categorieën’ wordt toegevoegd, zodat aangepaste code de AEM-code kan uitbreiden die zich onder `/libs`bevindt.

<table>
 <tbody>
  <tr>
   <td><strong>Oplossing</strong></td>
   <td><strong>Vorige locatie</strong><br /> </td>
   <td><strong>Nieuwe locatie</strong></td>
   <td><strong>Achterwaartse-compatibiliteitsbenadering</strong></td>
   <td><strong>Vereisten om op het recentste model te richten</strong></td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/clientlibs/fd/fp</code></td>
   <td><code>/libs/fd/fp/components</code></td>
   <td><p>Verouderde clientlib die op een geval zal voortbestaan dat via een op zijn plaats verbetering is bevorderd.</p> <p>Nieuwe clientlibs hebben dezelfde categorienamen en de eigenschap "<strong><code>replaces</code></strong>" om te voorkomen dat oude en nieuwe clientlibs worden samengevoegd.</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/clientlibs/fd/rte</code></td>
   <td><code>/libs/fd/rte</code></td>
   <td><p>Verouderde clientlibs die op een instantie zullen worden voortgeduurd die via een plaatsverbetering is bevorderd.</p> <p>Nieuwe clientlibs hebben dezelfde categorienamen en de eigenschap "<strong><code>replaces</code></strong>" om te voorkomen dat oude en nieuwe clientlibs worden samengevoegd.</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/clientlibs/fd/af</code></td>
   <td><code>/libs/fd/af/authoring/clientlibs</code></td>
   <td>Oudere clientlibs. Wordt voortgezet op een instantie die is bijgewerkt via een upgrade op plaats. Nieuwe clientlibs hebben dezelfde categorienamen en de eigenschap "<strong><code>replaces</code></strong>" om te voorkomen dat oude en nieuwe clientlibs worden samengevoegd.</td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/clientlibs/fd/themes/themeLibrary</code></td>
   <td>Dit onderdeel maakt geen deel meer uit van de AEM 6.5-verpakking.</td>
   <td><p>Buiten-de-box thema's in Adaptieve formulieren.</p> <p>Wordt voortgezet op een opgewaardeerde installatie.</p> </td>
   <td>Dit is gedeeltelijk door de gebruiker gegenereerde inhoud. Dit wordt geleverd als een referentiemateriaal met de <code>aem-forms-reference-themes</code> naam.</td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/clientlibs/fd/expeditor</code></td>
   <td><code>/libs/fd/expeditor/clientlibs</code></td>
   <td>Oudere clientlibs. Wordt voortgezet op een instantie die is bijgewerkt via een upgrade op plaats. Nieuwe clientlibs hebben dezelfde categorienamen en de eigenschap "<strong><code>replaces</code></strong>" om te voorkomen dat oude en nieuwe clientlibs worden samengevoegd.</td>
   <td>Geen actie vereist.<p> </p> </td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/clientlibs/fd/fmaddon</code></td>
   <td><code>/libs/fd/fmaddon</code></td>
   <td>Verouderde analyse en doelclientlibs die niet rechtstreeks worden verbruikt. </td>
   <td>Na de upgrade opschonen met een opschoonfilter.</td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><p><code>/etc/clientlibs/foundation/asseteditor</code></p> <p><code>/etc/clientlibs/foundation/assetshare</code></p> <p><code>/etc/clientlibs/foundation/assetinsights</code></p> </td>
   <td><code>/libs/dam/clientlibs</code></td>
   <td>Oudere clientlibs hebben verschillende namen van clientcategorieën.</td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td> </td>
   <td><code>/etc/clientlibs/ckeditor</code></td>
   <td><code>/libs/clientlibs/ckeditor</code></td>
   <td>Dit zijn oudere clientlibs. Ze zullen worden voortgezet op een opgewaardeerde installatie ter plaatse. Nieuwe clientlibs hebben dezelfde categorienamen en de eigenschap "<code>replaces</code>" om te voorkomen dat oude en nieuwe clientlibs worden samengevoegd.</td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/clientlibs/foundation/sitecatalyst</code></td>
   <td><code>/libs/cq/analytics/clientlibs/analytics</code></td>
   <td><p>Dit zijn oudere clientlibs. Wordt voortgezet op een opgewaardeerde installatie.</p> <p>Nieuwe clientlibs hebben dezelfde categorienamen.</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/clientlibs/foundation/personalization</code></td>
   <td><code>/libs/cq/personalization/clientlibs/personalization</code></td>
   <td><p>Dit zijn oudere clientlibs. Wordt voortgezet op een opgewaardeerde installatie.</p> <p>Nieuwe clientlibs hebben dezelfde categorienamen.</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/clientlibs/foundation/searchpromote</code></td>
   <td><code>/libs/cq/searchpromote/clientlibs/searchpromote</code></td>
   <td><p>Dit zijn oudere clientlibs. Wordt voortgezet op een opgewaardeerde installatie.</p> <p>Nieuwe clientlibs hebben dezelfde categorienamen</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/clientlibs/foundation/target</code></td>
   <td><code>/libs/cq/target/clientlibs/target</code></td>
   <td><p>Dit zijn oudere clientlibs. Wordt voortgezet op een opgewaardeerde installatie.</p> <p>Nieuwe clientlibs hebben dezelfde categorienamen.</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/clientlibs/address</code></td>
   <td><code>/libs/cq/address/clientlibs</code></td>
   <td>Nieuwe clientlibs hebben dezelfde categorienamen.</td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/clientlibs/wcm/foundation</code></td>
   <td><code>/libs/wcm/foundation/clientlibs</code></td>
   <td>Oudere clientlibs. Wordt voortgezet op een opgewaardeerde installatie. Nieuwe clientlibs hebben dezelfde categorienamen en de eigenschap "<strong>replaces</strong>" om te voorkomen dat oude en nieuwe clientlibs worden samengevoegd.</td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-sites</td>
   <td><code>/etc/clientlibs/wcm/foundation/grid/grid_base.less</code></td>
   <td><p><code>/libs/wcm/foundation/clientlibs/grid/grid_base.less</code></p> </td>
   <td><p>Bij een upgrade op plaats blijft het oudere bestand (/etc/clientlibs/wcm/..._) behouden en wordt het niet automatisch verwijderd. Verwijzingen naar de verouderde versie /etc/clientlibs/wcm/foundation/grid/grid_base.less blijven dus gestasificeerd.</p> <p><em>Merk op dat het een uitbijter geval is waar dit LESS dossier door absolute weg via LESS @import verklaringen, en NIET door clientlib categorie wordt van verwijzingen voorzien.</em></p> <p>Als de klant LESS die "grid_base.less"van verwijzingen voorziet naar een niet bestaand dossier aanwijst, zal de Bewerkbare wijze van de Lay-out van het Malplaatje breken, en om het even welke aanpassingen die met het worden aangebracht zullen niet aanwezig zijn (dat wil zeggen. alle componenten zijn de volledige breedte van de pagina).</p> </td>
   <td>Verwijzingen in aangepaste code bijwerken (bijvoorbeeld in LESS-bestanden die verwijzen naar het verplaatste bestand grid_base.less) naar de nieuwe locatie en de verouderde locatie verwijderen.</td>
  </tr>
 </tbody>
</table>

Dit zijn andere herstructureringen die niet onder de vorige secties vallen.

### Uitbreidingsstrategie {#extensibility-strategy-2}

Zie elke tabelrij voor elk ondersteund uitbreidingsmodel. Inhoud in deze sectie wordt gewoonlijk niet uitgebreid.

## Overig {#miscellaneous}

<table>
 <tbody>
  <tr>
   <td><strong>Oplossing</strong></td>
   <td><strong>Vorige locatie</strong><br /> </td>
   <td><strong>Nieuwe locatie</strong></td>
   <td><strong>Achterwaartse-compatibiliteitsbenadering</strong></td>
   <td><strong>Vereisten om op het recentste model te richten</strong></td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/designs/fd/fp</code></td>
   <td><code>/libs/fd/fp</code></td>
   <td><p>Verouderde AEM Forms Portal OOTB-sjablonen. Deze malplaatjes zullen in /etc na een op zijn plaats bevorderde opstelling blijven.</p> <p>In de sjabloonlijst wordt het woord<em> "afgekeurd</em>" toegevoegd aan de sjabloontitel om deze te onderscheiden van de nieuwere sjablonen.</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-formulieren</td>
   <td><code>/etc/aep</code></td>
   <td><code>/var/fd/content/annotations</code></td>
   <td>Oudere annotatiebestanden voor Correspondentiebeheer. Niet bedoeld om direct te worden verbruikt. Wordt na de upgrade opgeschoond met een opschoonfilter.</td>
   <td>Verouderde locatie na de upgrade opgeschoond met een opschoonfilter.</td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/tags</code></td>
   <td><code>/content/cq:tags</code></td>
   <td>De API voor tagbeheer ondersteunt zowel de oude als de nieuwe locatie. Wanneer de Factory OSGi Component van de Manager van de Markering JCR begint, ontdekt het of het op een promotieinstantie of erfenis loopt, en gebruikt de aangewezen plaats.<br /> </td>
   <td><p>Voor een juiste uitlijning met het nieuwe model:</p>
    <ol>
     <li>Vervang de verwijzingen naar het oude model (<code>/etc/tags</code>) door het nieuwe (<code>/content/cq:tags</code>) door het gebruiken van <code>tagID.</code></li>
     <li>Aanmelden bij CRXDE Lite</li>
     <li>De tags verplaatsen van <code>/etc/tags</code> naar <code>/content/cq:tags</code></li>
     <li>Start de OSGi-component opnieuw <code class="code">com.day.cq.tagging.impl.JcrTagManagerFactoryImpl.
        </code></li>
    </ol> <p> </p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/instances</code></td>
   <td><code>/var/workflow/instances</code></td>
   <td>Verouderde locatie die wordt gebruikt bij de verwerking van<br /> werkstromen tijdens de vlucht. Nieuwe workflows gebruiken de nieuwe locatie in <code>/var.</code></td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/scripts</code></td>
   <td><p><code>/libs/workflow/scripts</code></p> <p><code>/apps/workflow/scripts</code></p> </td>
   <td><p>De bestaande Stappen van het Model van het Werkschema die werkschemascripts in de erfenisplaats bij van verwijzingen voorzien <code>/etc/workflow/scripts</code> zullen aan deze manuscripten na de verbetering blijven richten, en behoorlijk uitvoeren.</p> <p>Noteer de AEM-gebruikersinterface voor het ontwerpen van de workflowstappen" (Proces, Splits, enz.) worden niet langer scripts vermeld onder <code>/etc/workflow/scripts</code> in de vervolgkeuzelijst die wordt gebruikt voor het uitvoeren van workflowscripts.</p> </td>
   <td><p>Workflows die gebruikmaken van deze scripts blijven werken zoals u had verwacht als de bijbehorende stap voor het workflowproces niet wordt bewerkt in AEM.</p> <p>Voor volledige achterwaartse compatibiliteit, ook wanneer de stappen worden bewerkt, is echter handmatige actie van de klant na de upgrade vereist:</p>
    <ul>
     <li>De scripts moeten van <code>/etc/workflow/scripts</code> naar <code>/apps/workflow/scripts.</code></li>
     <li>Alle<strong> </strong>verwijzingen naar <code>/etc/workflow/scripts</code> de stappen in het workflowmodel moeten worden bijgewerkt om naar de nieuwe <code>/apps/workflow/scripts</code> locatie te verwijzen.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/replication/treeactivation</code></td>
   <td><code>/libs/replication/treeactivation</code></td>
   <td>De nutspagina van ClassicUI blijft op zijn plaats bij verbetering.</td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM-middelen</td>
   <td><code>/etc/dam/jobs</code></td>
   <td><code>/var/dam/jobs</code></td>
   <td><p>Tijdelijke locatie voor het vasthouden van zip-bestanden die zijn gegenereerd voor AEM Assets-downloadactie.</p> <p>Het is niet nodig het bestand bij te werken omdat het bestand op de nieuwe locatie wordt gegenereerd wanneer de client om het element vraagt.</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/products</code></td>
   <td><code>/var/commerce/products</code></td>
   <td><p>De oude inhoud blijft op zijn plaats en kan na de upgrade worden gebruikt.</p> <p>Er is een uitgestelde migratietaak beschikbaar voor de migratie naar de nieuwe locatie.</p> </td>
   <td><p>De migratie wordt uitgevoerd via een Lazy Migration-taak: <code>CQ64CommerceMigrationTask.</code></p> <p>De volgende stappen worden uitgevoerd:</p>
    <ul>
     <li>Hiermee wijzigt u verwijzingen van de oude locatie naar de nieuwe locatie</li>
     <li>Hiermee verplaatst u inhoud van de oude locatie naar de nieuwe locatie</li>
     <li><p>Verwijdert de oude locatie om uiteindelijk het gebruik van de nieuwe locatie in het hele systeem te activeren</p> </li>
    </ul> <p>De locaties waarop de taak betrekking heeft, zijn:</p>
    <ul>
     <li>/etc/commerce/products</li>
     <li>/etc/commerce/collections<br /> </li>
     <li>/etc/commerce/orders<br /> </li>
     <li>/etc/commerce/payment-methods<br /> </li>
     <li>/etc/commerce/Shipping-methods<br /> </li>
    </ul> <p>Voor grotere catalogi is het raadzaam de handelsmigratietaak afzonderlijk uit te voeren door de volgende Java-systeemeigenschap aan AEM door te geven:</p>
    <ul>
     <li>eigenschapsnaam: <code>com.adobe.upgrade.forcemigration</code></li>
     <li>eigenschapswaarde: <code>com.day.cq.compat.codeupgrade.impl.cq64.CQ64CommerceMigrationTask</code></li>
    </ul> <p>Na de migratie moet AEM opnieuw worden opgestart.</p> </td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/orders</code></td>
   <td><code>/var/commerce/orders</code></td>
   <td><p>De oude inhoud blijft op zijn plaats en kan na de upgrade worden gebruikt.</p> <p>Er is een uitgestelde migratietaak beschikbaar voor de migratie naar de nieuwe locatie.</p> </td>
   <td>Zie bovenstaande beschrijving voor <code>/etc/commerce/products</code>.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/collections</code></td>
   <td><code>/var/commerce/collections</code></td>
   <td><p>De oude inhoud blijft op zijn plaats en kan na de upgrade worden gebruikt.</p> <p>Er is een uitgestelde migratietaak beschikbaar voor de migratie naar de nieuwe locatie.</p> </td>
   <td>Zie bovenstaande beschrijving voor <code>/etc/commerce/products</code>.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/classifications</code></td>
   <td><code>/var/commerce/classifications</code></td>
   <td>Geen actie vereist.</td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/shipping-methods</code></td>
   <td><code>/var/commerce/shipping-methods</code></td>
   <td><p>De oude inhoud blijft op zijn plaats en kan na de upgrade worden gebruikt.</p> <p>Er is een uitgestelde migratietaak beschikbaar voor de migratie naar de nieuwe locatie.</p> </td>
   <td>Zie bovenstaande beschrijving voor <code>/etc/commerce/products</code>.</td>
  </tr>
  <tr>
   <td>AEM Commerce</td>
   <td><code>/etc/commerce/payment-methods</code></td>
   <td><code>/var/commerce/payment-methods</code></td>
   <td><p>De oude inhoud blijft op zijn plaats en kan na de upgrade worden gebruikt.</p> <p>Er is een uitgestelde migratietaak beschikbaar voor de migratie naar de nieuwe locatie.</p> </td>
   <td>Zie bovenstaande beschrijving voor <code>/etc/commerce/products</code>.</td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/taskmanagement</code></td>
   <td><code>/var/taskmanagement</code></td>
   <td><p>Nieuwe taken worden gemaakt onder <code>/var/taskmanagement</code></p> <p>Bestaande taken op de verouderde locatie blijven zichtbaar in het AEM-Postvak.</p> </td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/packages</code></td>
   <td><code>/var/workflow/packages</code></td>
   <td><p>AEM-pakketten die zijn gemaakt met AEM Package Manager worden nog opgeslagen in <code>/etc/workflow/packages.</code></p> <p>Andere pakketten die via AEM-sites en -workflows zijn gemaakt, worden nog steeds opgeslagen in<code>/var/workflow/packages.</code></p> <p>Pakketten die in zowel <code>/etc/workflow/packages</code> als <code>/var/workflow/packages</code> kunnen worden gevonden, kunnen nog steeds worden bewerkt via Pakketbeheer van AEM. </p> </td>
   <td><p>Geen actie vereist.</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/workflow/instances</code></td>
   <td><code>/var/workflow/instances</code></td>
   <td>Nieuwe workflowinstanties worden <code>/var</code> automatisch onder gemaakt.</td>
   <td>Geen actie vereist.</td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/commerce/searchpromote</code></td>
   <td><code>/var/cq/searchpromote</code></td>
   <td><p>Nieuwe locatie voor zoeken en bevorderen van inhoud van feed.</p> <p>De oude URL blijft werken en het verzoek wordt door een ServletFilter naar de nieuwe locatie doorgestuurd.</p> </td>
   <td><br /> Geen actie vereist. <br /> </td>
  </tr>
  <tr>
   <td>Alles</td>
   <td><code>/etc/dtm-hook</code></td>
   <td><code>/var/cq/dtm/web-hook</code></td>
   <td><p>Nieuwe locatie voor DTM Web-Hooks.</p> <p>De oude URL blijft werken en het verzoek wordt door een ServletFilter naar de nieuwe locatie doorgestuurd.</p> </td>
   <td><br /> Geen actie vereist. <br /> </td>
  </tr>
 </tbody>
</table>

