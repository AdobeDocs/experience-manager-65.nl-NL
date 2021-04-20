---
title: Onderhoudstaken vóór upgrade
seo-title: Onderhoudstaken vóór upgrade
description: Leer meer over de pre-verbeteringstaken in AEM.
seo-description: Leer meer over de pre-verbeteringstaken in AEM.
uuid: 5da1cfc7-8a10-47b1-aafb-2cd112e3f818
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: 291c91e5-65ff-473d-ac11-3da480239e76
docset: aem65
feature: Upgrading
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '2159'
ht-degree: 0%

---


# Onderhoudstaken vóór upgrade{#pre-upgrade-maintenance-tasks}

Voordat u begint met de upgrade, is het belangrijk dat u de volgende onderhoudstaken uitvoert om ervoor te zorgen dat het systeem klaar is en kan worden teruggedraaid als zich problemen voordoen:

* [Zorgen voor voldoende schijfruimte](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Volledige back-up AEM](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Back-up maken van wijzigingen in /etc](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#backup-changes-etc)
* [Het bestand quickstart.properties genereren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Werkstroom- en controlelogbestanden leegmaken configureren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [De taken vóór de upgrade installeren, configureren en uitvoeren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Aangepaste aanmeldingsmodules uitschakelen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-login-modules)
* [Updates verwijderen uit de map /install](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Koude stand-byinstanties stoppen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Aangepaste geplande taken uitschakelen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Offline revisie opschonen uitvoeren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Verzameling van afval uit datastore uitvoeren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Upgrade het databaseschema indien nodig](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#upgradethedatabaseschemaifneeded)
* [Gebruikers verwijderen die de upgrade mogelijk kunnen blokkeren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#delete-users-that-might-hinder-the-upgrade)

* [Logbestanden roteren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Zorgen voor voldoende schijfruimte {#ensure-sufficient-disk-space}

Bij het uitvoeren van de upgrade moet, naast de activiteiten voor het bijwerken van de inhoud en code, een migratie naar de opslagplaats worden uitgevoerd. De migratie zal een exemplaar van de bewaarplaats in het nieuwe formaat van de Tar van het Segment tot stand brengen. Hierdoor hebt u voldoende schijfruimte nodig om een tweede, mogelijk grotere versie van uw opslagplaats te behouden.

## Volledige back-up AEM {#fully-back-up-aem}

Er moet een volledige back-up van AEM worden gemaakt voordat de upgrade wordt gestart. Maak indien van toepassing een back-up van de opslagplaats, de installatie van de toepassing, de datastore en de Mongo-exemplaren. Zie [Back-up en herstel](/help/sites-administering/backup-and-restore.md) voor meer informatie over het maken van back-ups en het herstellen van een AEM.

## Back-up maken van wijzigingen in /etc {#backup-changes-etc}

Het upgradeproces is een goede manier om bestaande inhoud en configuraties te onderhouden en samen te voegen vanuit de paden `/apps` en `/libs` in de repository. Voor veranderingen die aan de `/etc` weg, met inbegrip van de configuraties van de Hub van de Context worden aangebracht, is het vaak noodzakelijk om deze veranderingen na de verbetering opnieuw toe te passen. Terwijl de verbetering een reservekopie van om het even welke veranderingen zal maken die het niet onder `/var` kan samenvoegen, adviseren wij manueel het steunen van deze veranderingen alvorens met de verbetering te beginnen.

## Het bestand quickstart.properties {#generate-quickstart-properties} genereren

Wanneer AEM wordt gestart vanuit het jar-bestand, wordt een `quickstart.properties`-bestand gegenereerd onder `crx-quickstart/conf`. Als AEM in het verleden alleen is gestart met het beginscript, is dit bestand niet aanwezig en mislukt de upgrade. Controleer of dit bestand bestaat en start AEM opnieuw vanaf het jar-bestand als dit niet aanwezig is.

## Werkstroom- en controlelogbestand {#configure-wf-audit-purging} opschonen

De `WorkflowPurgeTask` en `com.day.cq.audit.impl.AuditLogMaintenanceTask` taken vereisen afzonderlijke configuraties OSGi en zullen niet zonder hen werken. Als ze tijdens de uitvoering van een pre-upgrade-taak mislukken, is het ontbreken van configuraties de meest waarschijnlijke reden. Daarom zorg ervoor om configuraties OSGi voor deze taken toe te voegen of hen volledig te verwijderen uit de lijst van pre-verbeteringstaken als u niet wenst om hen in werking te stellen. Documentatie voor het configureren van taken voor het zuiveren van werkstromen vindt u op [Workflowinstanties beheren](/help/sites-administering/workflows-administering.md) en de configuratie van controlelogonderhoudstaken vindt u op [Onderhoud controlelogbestand in AEM 6](/help/sites-administering/operations-audit-log.md).

Zie [Werkstroom- en auditknooppunten wissen en controlelogboeken leegmaken op AEM 6.0 voor werkstroom- en controlelogboekzuivering op CQ 5.6.](https://helpx.adobe.com/experience-manager/kb/howtopurgewf.html)

## De {#install-configure-run-pre-upgrade-tasks}-taken vóór de upgrade installeren, configureren en uitvoeren

Vanwege de mate van aanpassing die AEM toestaat, passen omgevingen gewoonlijk niet op dezelfde manier upgrades uit. Dit maakt het tot stand brengen van een gestandaardiseerde procedure voor verbeteringen een moeilijk proces.

In vorige versies was het ook moeilijk voor AEM upgrades die waren gestopt of die niet veilig zijn hervat. Dit leidde tot situaties waarin het opnieuw opstarten van de volledige upgradeprocedure noodzakelijk was of waarin defecte upgrades werden uitgevoerd zonder dat dit tot waarschuwingen leidde.

Om deze problemen aan te pakken, heeft Adobe het upgradeproces verschillende verbeteringen aangebracht, waardoor het robuuster en gebruiksvriendelijker wordt. De onderhoudstaken die vóór de upgrade moesten worden uitgevoerd, worden geoptimaliseerd en geautomatiseerd. Ook zijn er ná de upgrade-rapporten toegevoegd, zodat het proces volledig kan worden onderzocht in de hoop dat eventuele problemen gemakkelijker kunnen worden gevonden.

De preupgrade onderhoudstaken worden momenteel verspreid over verschillende interfaces die gedeeltelijk of volledig manueel worden uitgevoerd. De pre-verbeterings onderhoudsoptimalisering die in AEM 6.3 wordt geïntroduceerd laat een verenigde manier toe om deze taken teweeg te brengen en hun resultaat op bestelling te kunnen inspecteren.

Alle taken die zijn opgenomen in de optimaliseringsstap vóór de upgrade zijn compatibel met alle versies vanaf AEM 6.0.

### Hoe stelt u {#how-to-set-it-up} in

In AEM 6.3 en later worden de optimalisatietaken voor het onderhoud van de upgrade opgenomen in de snelstartjar. Als u een upgrade uitvoert vanaf een oudere versie van AEM 6, worden deze beschikbaar gesteld via afzonderlijke pakketten die u kunt downloaden van Package Manager.

U vindt de pakketten op de volgende locaties:

* [Voor upgrade vanaf AEM 6.0](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq600/product/pre-upgrade-tasks-content-cq60)

* [Voor upgrade vanaf AEM 6.1](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/product/pre-upgrade-tasks-content-cq61)

* [Voor upgrade vanaf AEM 6.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/product/pre-upgrade-tasks-content-cq62)

### Hoe wordt het {#how-to-use-it} gebruikt

De `PreUpgradeTasksMBean` component OSGI komt vooraf gevormd met een lijst van pre-verbeterings onderhoudstaken die allen in één keer kunnen worden in werking gesteld. U kunt de taken vormen door de hieronder procedure te volgen:

1. Ga naar de webconsole door naar *https://serveraddress:serverport/system/console/configMgr* te bladeren

1. Zoek naar &quot;**preupgradetasks**&quot;, dan klik op de eerste passende component. De volledige naam van de component is `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`

1. Wijzig de lijst van onderhoudstaken die zoals hieronder getoond moeten lopen:

   ![1487758925984](assets/1487758925984.png)

De takenlijst is afhankelijk van de uitvoeringsmodus die wordt gebruikt om de instantie te starten. Hieronder volgt een beschrijving van de uitvoeringsmodus waarvoor elke onderhoudstaak is ontworpen.

<table>
 <tbody>
  <tr>
   <td><strong>Taak</strong></td>
   <td><strong>Run-modus</strong></td>
   <td><strong>Opmerkingen</strong></td>
  </tr>
  <tr>
   <td><code>TarIndexMergeTask</code></td>
   <td>crx2</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>DataStoreGarbageCollectionTask</code></td>
   <td>crx2</td>
   <td>Voert markering en vegen uit. Voor gedeelde datastores, verwijder deze stap en stel <br /> manueel of behoorlijk voor instanties alvorens uit te voeren voor.</td>
  </tr>
  <tr>
   <td><code>ConsistencyCheckTask</code></td>
   <td>crx2</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>WorkflowPurgeTask</code></td>
   <td>crx2/crx3</td>
   <td>Moet de Adobe Granite Workflow zuivert Configuratie OSGi vormen alvorens te lopen.</td>
  </tr>
  <tr>
   <td><code>GenerateBundlesListFileTask</code></td>
   <td>crx2/crx3</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>RevisionCleanupTask</code></td>
   <td>crx3</td>
   <td>Voor instanties TarMK op AEM 6.0 tot 6.2, stel in plaats daarvan manueel Off-line de Correctie van de Revisie in werking.</td>
  </tr>
  <tr>
   <td><code>com.day.cq.audit.impl.AuditLogMaintenanceTask</code></td>
   <td>crx3</td>
   <td>Moet de configuratie vormen van OSGi van de Planner van de Woorden van het Logboek van de Controle alvorens te lopen.</td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>`DataStoreGarbageCollectionTask` Roept een verrichting van de Inzameling van het Afval Datastore met het teken en de slagfase indien gebruikt. Voor plaatsingen die een gedeelde datastore gebruiken zorg ervoor om of het opnieuw te vormen of behoorlijk of de instantie voor te bereiden om schrapping van punten te vermijden die door een andere instantie van verwijzingen worden voorzien. Hiervoor kan het nodig zijn de markeringsfase handmatig op alle instanties uit te voeren voordat deze pre-upgradetaak wordt geactiveerd.

### Standaardconfiguratie van de health checks vóór upgrade {#default-configuration-of-the-pre-upgrade-health-checks}

De `PreUpgradeTasksMBeanImpl` OSGI-component wordt vooraf geconfigureerd met een lijst met pre-upgrade health check-tags die moeten worden uitgevoerd wanneer de `runAllPreUpgradeHealthChecks`-methode wordt aangeroepen:

* **systeem** - de tag die wordt gebruikt door de gezondheidscontroles van granietonderhoud

* **pre-upgrade**  - dit is een aangepaste tag die kan worden toegevoegd aan alle gezondheidscontroles die u kunt instellen om te worden uitgevoerd vóór een upgrade

De lijst kan worden bewerkt. U kunt de plus **(+)** en minus **(-)** knopen naast de markeringen gebruiken om meer douanetags toe te voegen, of de standaarddegenen te verwijderen.

**MBean-methoden**

De beheerde boonfunctionaliteit kan worden betreden gebruikend [JMX Console](/help/sites-administering/jmx-console.md).

U kunt tot MBeans toegang hebben door:

1. Ga naar de JMX Console op *https://serveraddress:serverport/system/console/jmx*
1. Zoek naar **PreUpgradeTasks** en klik het resultaat

1. Selecteer een methode in de sectie **Bewerkingen** en selecteer **Invoke** in het volgende venster.

Hieronder volgt een lijst van alle beschikbare methodes die `PreUpgradeTasksMBeanImpl` blootstelt:

<table>
 <tbody>
  <tr>
   <td><strong>Naam methode</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><code>getAvailablePreUpgradeTasksNames()</code></td>
   <td>INFO</td>
   <td>Hiermee geeft u de lijst met beschikbare namen voor preupgradeonderhoudstaken weer.</td>
  </tr>
  <tr>
   <td><code>getAvailablePreUpgradeHealthChecksTagNames()</code></td>
   <td>INFO</td>
   <td>Hiermee geeft u de lijst met labelnamen voor aan de upgrade voorafgaande gezondheidscontroles weer.</td>
  </tr>
  <tr>
   <td><code>runAllPreUpgradeTasks()</code></td>
   <td>ACTIE</td>
   <td>Voert alle preupgradeonderhoudstaken in de lijst uit.</td>
  </tr>
  <tr>
   <td><code>runPreUpgradeTask(preUpgradeTaskName)</code></td>
   <td>ACTIE</td>
   <td>Hiermee wordt de onderhoudstaak vóór de upgrade uitgevoerd met de naam die als parameter is opgegeven.</td>
  </tr>
  <tr>
   <td><code>isRunAllPreUpgradeTaskRunning()</code></td>
   <td>ACTION_INFO</td>
   <td>Controleert of de <code>runAllPreUpgradeTasksmaintenance</code> taak momenteel loopt.</td>
  </tr>
  <tr>
   <td><code>getAnyPreUpgradeTaskRunning()</code></td>
   <td>ACTION_INFO</td>
   <td>Controleert of een preupgrade-onderhoudstaak momenteel wordt uitgevoerd en<br /> retourneert een array met de namen van taken die momenteel worden uitgevoerd.</td>
  </tr>
  <tr>
   <td><code>getPreUpgradeTaskLastRunTime(preUpgradeTaskName)</code></td>
   <td>ACTIE</td>
   <td>Toont de nauwkeurige lopende tijd van de pre-verbeterings onderhoudstaak met de naam die als parameter wordt gegeven.</td>
  </tr>
  <tr>
   <td><code>getPreUpgradeTaskLastRunState(preUpgradeTaskName)</code></td>
   <td>ACTIE</td>
   <td>Toont de laatste lopende staat van de pre-verbeterings onderhoudstaak met de naam die als parameter wordt gegeven.</td>
  </tr>
  <tr>
   <td><code>runAllPreUpgradeHealthChecks(shutDownOnSuccess)</code></td>
   <td>ACTIE</td>
   <td><p>Voert alle controles van de pre-verbeteringsgezondheid in werking en bewaart hun status in een dossier genoemd <code>preUpgradeHCStatus.properties</code> dat in de sling huisweg wordt gevestigd. Als de <code>shutDownOnSuccess</code> parameter aan <code>true</code> wordt geplaatst, zal de AEM instantie worden gesloten, maar slechts als alle pre-verbeteringscontroles een O.K. status hebben.</p> <p>Het eigenschappenbestand wordt gebruikt als een voorwaarde voor een toekomstige upgrade<br /> en het upgradeproces wordt gestopt als de uitvoering van de health check van vóór de upgrade<br /> is mislukt. Als u het resultaat van de voorafgaande upgrade wilt negeren<br /> gezondheidscontroles en de upgrade toch wilt starten, kunt u het bestand verwijderen.</p> </td>
  </tr>
  <tr>
   <td><code>detectUsageOfUnavailableAPI(aemVersion)</code></td>
   <td>ACTIE</td>
   <td>Hiermee worden alle geïmporteerde pakketten weergegeven waaraan niet meer wordt voldaan wanneer <br /> de upgrade naar de opgegeven AEM uitvoert. De doel AEM versie moet <br /> als parameter worden gegeven zijn.</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>De methodes MBean kunnen worden aangehaald via:
>
>* De JMX-console
>* Een externe toepassing die verbinding maakt met JMX
>* cURL

>



## Aangepaste aanmeldingsmodules uitschakelen {#disable-custom-login-modules}

>[!NOTE]
>
>Deze stap is alleen vereist als u een upgrade uitvoert vanaf een versie van AEM 5. Het kan volledig voor verbeteringen van oudere AEM 6 versies worden overgeslagen.

De manier waarop aangepaste `LoginModules` zijn geconfigureerd voor verificatie op het niveau van de opslagplaats is fundamenteel gewijzigd in Apache Oak.

In AEM versies die CRX2 configuratie gebruikten werd geplaatst in het `repository.xml` dossier, terwijl vanaf AEM 6 het in de dienst van de Fabriek van de Configuratie van Apache Felix JAAS via de Console van het Web wordt gedaan.

Daarom moeten bestaande configuraties na de upgrade worden uitgeschakeld en opnieuw worden gemaakt voor Apache Oak.

Om de douanemodules onbruikbaar te maken die in de configuratie JAAS van `repository.xml` worden bepaald, moet u de configuratie wijzigen om gebrek `LoginModule`, zoals in dit voorbeeld te gebruiken:

```xml
<Security >
             ....
          <!--
                 Use LoginModule authenticating against repository itself
                 -->
                 <LoginModule class = "com.day.crx.core.CRXLoginModule" >
                     <param name = "anonymousId" value = "anonymous" />
                     <param name = "adminId" value ="admin" />
                     <param name = "disableNTLMAuth" value = "true" />
                     <param name = "tokenExpiration" value = "43200000" />
                     <!-- param name="trust_credentials_attribute" value="d5b9167e95dad6e7d3b5d6fa8df48af8"/
                -->
                 </LoginModule >
         </ Security>
```

>[!NOTE]
>
>Zie [Verificatie met de externe aanmeldingsmodule](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html) voor meer informatie.
>
>Voor een voorbeeld van `LoginModule` configuratie in AEM 6, zie [Het Vormen LDAP met AEM 6](/help/sites-administering/ldap-config.md).

## Updates verwijderen uit de map /install {#remove-updates-install-directory}

>[!NOTE]
>
>Verwijder alleen pakketten uit de map crx-quickstart/install NA het afsluiten van de AEM. Dit zal één van de laatste stappen zijn alvorens de op zijn plaats verbeteringsprocedure te beginnen.

Verwijder om het even welke de dienstpakken, eigenschapspakken of hotfixes die door `crx-quickstart/install` folder op het lokale dossiersysteem zijn opgesteld. Hierdoor wordt voorkomen dat oude hotfixes en servicepacks onbedoeld boven op de nieuwe AEM worden geïnstalleerd nadat de update is voltooid.

## Een Cold Standby-instantie {#stop-tarmk-coldstandby-instance} stoppen

Als u TarMK koude stand-by gebruikt, moet u eventuele koude stand-byinstanties stoppen. Deze zullen een efficiënte manier waarborgen om online terug te komen in het geval van kwesties in de verbetering. Nadat de verbetering met succes heeft voltooid, zullen de koude standby instanties van de promotieprimaire instanties moeten worden herbouwd.

## Aangepaste geplande taken {#disable-custom-scheduled-jobs} uitschakelen

Schakel geplande OSGi-taken uit die in uw toepassingscode zijn opgenomen.

## Offline revisie opschonen uitvoeren {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Deze stap is alleen nodig voor TarMK-installaties

Als u TarMK gebruikt, moet u de optie Offline revisie opschonen uitvoeren voordat u de upgrade uitvoert. Hierdoor worden de migratie naar de opslagplaats en de daarop volgende upgradetaken veel sneller uitgevoerd en wordt ervoor gezorgd dat Online revisie-opschoning met succes kan worden uitgevoerd nadat de upgrade is voltooid. Voor informatie bij het runnen van de Off-line Opruiming van de Revisie, zie [Het uitvoeren van de Off-line Opruiming van de Revisie](/help/sites-deploying/storage-elements-in-aem-6.md#performing-offline-revision-cleanup).

## Afvalophaling datastore uitvoeren {#execute-datastore-garbage-collection}

>[!NOTE]
>
>Deze stap is alleen nodig voor instanties waarop crx3 wordt uitgevoerd

Na het runnen van revisie schoonmaakbeurt op CRX3 instanties, zou u de Inzameling van het huisvuil van de Datastore moeten in werking stellen om het even welke niet referenced vlekken in de gegevensopslag te verwijderen. Voor instructies, zie de documentatie op [de Inzameling van het huisvuil van de Opslag van Gegevens](/help/sites-administering/data-store-garbage-collection.md).

## Upgrade het databaseschema indien nodig {#upgrade-the-database-schema-if-needed}

Gewoonlijk zorgt de onderliggende Apache Oak-stapel AEM voor persistentie ervoor dat het databaseschema indien nodig wordt bijgewerkt.

Er kunnen zich echter gevallen voordoen wanneer het schema niet automatisch kan worden bijgewerkt. Dit zijn meestal hoge beveiligingsomgevingen waarin de database wordt uitgevoerd onder een gebruiker met zeer beperkte bevoegdheden. Als dit gebeurt, blijft AEM het oude schema gebruiken.

Om dit te verhinderen, moet u het schema bevorderen door de hieronder procedure te volgen:

1. Sluit de AEM instantie die moet worden bijgewerkt.
1. Voer een upgrade uit op het databaseschema. Raadpleeg de documentatie bij het databasetype om te zien welke gereedschappen u nodig hebt om dit te bereiken.

   Zie [deze pagina op de Apache-website](https://jackrabbit.apache.org/oak/docs/nodestore/document/rdb-document-store.html#upgrade) voor meer informatie over de manier waarop het schema-upgrades door een eik worden afgehandeld.

1. Ga verder met het upgraden van AEM.

## Gebruikers verwijderen die de upgrade mogelijk {#delete-users-that-might-hinder-the-upgrade} verbergen

>[!NOTE]
>
>Deze onderhoudstaak voorafgaand aan de upgrade is alleen nodig als:
>
>* U voert een upgrade uit vanaf AEM oudere versies dan AEM 6.3
>* Tijdens de upgrade worden de hieronder vermelde fouten aangetroffen.

>



Er zijn uitzonderlijke gevallen wanneer de de dienstgebruikers in een oudere AEM versies zouden kunnen uiteindelijk verkeerd geëtiketteerd worden als regelmatige gebruikers.

Als dit gebeurt, zal de verbetering met een bericht als dit ontbreken:

```
ERROR [Apache Sling Repository Startup Thread] com.adobe.granite.repository.impl.SlingRepositoryManager Exception in a SlingRepositoryInitializer, SlingRepository service registration aborted
java.lang.RuntimeException: Unable to create service user [communities-utility-reader]:java.lang.RuntimeException: Existing user communities-utility-reader is not a service user.
```

Om dit probleem te verhelpen, moet u het volgende doen:

1. De instantie loskoppelen van het productieverkeer
1. Maak een back-up van de gebruiker(s) die het probleem heeft veroorzaakt. U kunt dit doen via Package Manager. Voor meer informatie, zie [Hoe te met Pakketten werken.](/help/sites-administering/package-manager.md)
1. Verwijder de gebruiker(s) die het probleem heeft veroorzaakt. Hieronder volgt een lijst met gebruikers die mogelijk onder deze categorie vallen:

   1. `dynamic-media-replication`
   1. `communities-ugc-writer`
   1. `communities-utility-reader`
   1. `communities-user-admin`
   1. `oauthservice`
   1. `sling-scripting`

## Logbestanden roteren {#rotate-log-files}

We raden u aan uw huidige logbestanden te archiveren voordat u begint met de upgrade. Hierdoor kunt u logbestanden tijdens en na de upgrade gemakkelijker controleren en scannen om eventuele problemen op te sporen en op te lossen.
