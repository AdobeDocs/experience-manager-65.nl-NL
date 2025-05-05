---
title: Onderhoudstaken vóór upgrade
description: Meer informatie over de aanbevolen taken voor AEM.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
exl-id: 37d4aee4-15eb-41ab-ad71-dfbd5c7910f8
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '2014'
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

Bij het uitvoeren van de upgrade moet, naast de activiteiten voor het upgraden van de inhoud en code, een migratie naar de opslagplaats worden uitgevoerd. Tijdens de migratie wordt een kopie van de opslagplaats gemaakt in de nieuwe indeling Segment Tar. Hierdoor hebt u voldoende schijfruimte nodig om een tweede, mogelijk grotere versie van uw opslagplaats te behouden.

## Volledige back-up AEM {#fully-back-up-aem}

Er moet een volledige back-up van AEM worden gemaakt voordat de upgrade wordt gestart. Maak indien van toepassing een back-up van de opslagplaats, de installatie van de toepassing, de datastore en de Mongo-exemplaren. Voor meer informatie bij het steunen van en het herstellen van een AEM instantie, zie [ Steun en herstel ](/help/sites-administering/backup-and-restore.md).

## Back-up maken van wijzigingen in /etc {#backup-changes-etc}

Het upgradeproces biedt een goede manier om bestaande inhoud en configuraties te onderhouden en samen te voegen vanuit de paden onder `/apps` en `/libs` in de opslagplaats. Voor veranderingen die aan de `/etc` weg, met inbegrip van de configuraties van de Hub van de Context worden aangebracht, is het vaak noodzakelijk om deze veranderingen na de verbetering opnieuw toe te passen. Terwijl de upgrade een reservekopie maakt van alle wijzigingen die niet kunnen worden samengevoegd onder `/var` , raadt de Adobe u aan om vóór het starten van de upgrade handmatig een back-up van deze wijzigingen te maken.

## Het bestand quickstart.properties genereren {#generate-quickstart-properties}

Wanneer AEM wordt gestart vanuit het jar-bestand, wordt een `quickstart.properties` -bestand gegenereerd onder `crx-quickstart/conf` . Als AEM in het verleden alleen met het beginscript is gestart, is dit bestand niet aanwezig en mislukt de upgrade. Controleer of dit bestand bestaat en start AEM opnieuw vanaf het jar-bestand als dit niet aanwezig is.

## Werkstroom- en controlelogbestanden leegmaken configureren {#configure-wf-audit-purging}

De `WorkflowPurgeTask` en `com.day.cq.audit.impl.AuditLogMaintenanceTask` taken vereisen afzonderlijke configuraties OSGi en kunnen niet zonder hen werken. Als ze tijdens de uitvoering van een pre-upgrade-taak mislukken, is het ontbreken van configuraties de meest waarschijnlijke reden. Daarom zorg ervoor om configuraties OSGi voor deze taken toe te voegen of hen volledig te verwijderen uit de lijst van pre-verbeteringstaken als u niet wenst om hen in werking te stellen. De documentatie voor het vormen werkschemazuiveringstaken kan bij [ het Beheer de Instanties van het Werkschema ](/help/sites-administering/workflows-administering.md) en de configuratie van de de onderhoudstaak van het controlelogboek kunnen bij [ het Onderhoud van het Logboek van de Controle in AEM 6 ](/help/sites-administering/operations-audit-log.md) worden gevonden.

Voor werkschema en controlelogboek het zuiveren op CQ 5.6 en controlelogboek het zuiveren op AEM 6.0, zie {het werkschema van 0} zuiveren en controleknopen [&#128279;](https://helpx.adobe.com/experience-manager/kb/howtopurgewf.html).

## De taken vóór de upgrade installeren, configureren en uitvoeren {#install-configure-run-pre-upgrade-tasks}

Vanwege de mate van aanpassing die AEM toestaat, passen omgevingen gewoonlijk niet op dezelfde manier upgrades uit. Als zodanig is het moeilijk om een gestandaardiseerde procedure voor upgrades in te voeren.

In vorige versies was het ook moeilijk voor AEM upgrades die zijn gestopt of die niet veilig zijn hervat. Dit leidde tot situaties waarin het opnieuw opstarten van de volledige upgradeprocedure noodzakelijk was of waarin defecte upgrades werden uitgevoerd zonder dat dit tot waarschuwingen leidde.

Om deze kwesties te behandelen, heeft de Adobe verscheidene verhogingen aan het verbeteringsproces toegevoegd, die het veerkrachtiger en gebruikersvriendelijker maken. De onderhoudstaken die vóór de upgrade moesten worden uitgevoerd, worden geoptimaliseerd en geautomatiseerd. Ook zijn er ná de upgrade-rapporten toegevoegd, zodat het proces volledig kan worden onderzocht in de hoop dat eventuele problemen gemakkelijker kunnen worden gevonden.

Onderhoudstaken vóór de upgrade worden momenteel verspreid over verschillende interfaces die gedeeltelijk of volledig handmatig worden uitgevoerd. De pre-verbeterings onderhoudsoptimalisering die in AEM 6.3 wordt geïntroduceerd laat een verenigde manier toe om deze taken teweeg te brengen en hun resultaat op bestelling te kunnen inspecteren.

Alle taken die zijn opgenomen in de optimaliseringsstap vóór de upgrade zijn compatibel met alle versies vanaf AEM 6.0.

### Procedure voor instellen {#how-to-set-it-up}

In AEM 6.3 en later worden de optimalisatietaken voor het onderhoud van de upgrade opgenomen in de snelstartjar.

<!-- URLs below are all 404s. This content should probably be removed because it is entirely obsolete.

If you are upgrading from an older version of AEM 6, they are made available through separate packages that you can download from the Package Manager.

You can find the packages at these locations:

* [For upgrading from AEM 6.0](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq600/product/pre-upgrade-tasks-content-cq60)

* [For upgrading from AEM 6.1](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq610/product/pre-upgrade-tasks-content-cq61)

* [For upgrading from AEM 6.2](https://www.adobeaemcloud.com/content/marketplace/marketplaceProxy.html?packagePath=/content/companies/public/adobe/packages/cq620/product/pre-upgrade-tasks-content-cq62) -->

### Hoe wordt het gebruikt {#how-to-use-it}

De `PreUpgradeTasksMBean` component OSGI wordt vooraf geconfigureerd met een lijst van pre-upgrade onderhoudstaken die allemaal tegelijk kunnen worden uitgevoerd. U kunt de taken vormen door de hieronder procedure te volgen:

1. Ga naar de Console van het Web door aan *https://serveraddress:serverport/system/console/configMgr* te doorbladeren

1. Onderzoek naar &quot;**preupgradetasks**&quot;, dan klik de eerste passende component. De volledige naam van de component is `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`

1. Wijzig de lijst met onderhoudstaken die moet worden uitgevoerd zoals hieronder wordt weergegeven:

   ![ 1487758925984 ](assets/1487758925984.png)

De takenlijst verschilt afhankelijk van de uitvoeringsmodus die wordt gebruikt om de instantie te starten. Hieronder volgt een beschrijving van de uitvoeringsmodus waarvoor elke onderhoudstaak is ontworpen.

<table>
 <tbody>
  <tr>
   <td><strong>Taak</strong></td>
   <td><strong>Run-modus</strong></td>
   <td><strong>Notities</strong></td>
  </tr>
  <tr>
   <td><code>TarIndexMergeTask</code></td>
   <td>crx2</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>DataStoreGarbageCollectionTask</code></td>
   <td>crx2</td>
   <td>Voert markering en vegen uit. Voor gedeelde datastores, verwijder deze stap en de looppas <br /> manueel of behoorlijk voorbereidt instanties alvorens uit te voeren.</td>
  </tr>
  <tr>
   <td><code>ConsistencyCheckTask</code></td>
   <td>crx2</td>
   <td> </td>
  </tr>
  <tr>
   <td><code>WorkflowPurgeTask</code></td>
   <td>crx2/crx3</td>
   <td>Moet de Configuratie OSGi van de Opschoonmachine van de Werkstroom van de Adobe vormen Granite alvorens te lopen.</td>
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
   <td>Moet de configuratie vormen van OSGi van de Planner van de Woorden van het Logboek van de Controle alvorens in werking te stellen.</td>
  </tr>
 </tbody>
</table>

>[!CAUTION]
>
>`DataStoreGarbageCollectionTask` roept een verrichting van de Inzameling van het Schuin van de Datastore met het teken en de slagfase indien gebruikt. Voor plaatsingen die een gedeelde datastore gebruiken, zorg ervoor of het behoorlijk opnieuw vormt of de instantie voorbereidt om schrapping van punten te vermijden die door een andere instantie van verwijzingen worden voorzien. Voor dit proces kan het nodig zijn de markeringsfase handmatig op alle instanties uit te voeren voordat deze pre-upgradetaak wordt geactiveerd.

### Standaardconfiguratie van de health checks vóór de upgrade {#default-configuration-of-the-pre-upgrade-health-checks}

De `PreUpgradeTasksMBeanImpl` OSGI-component wordt vooraf geconfigureerd met een lijst met tags die voorafgaand aan de upgrade moeten worden uitgevoerd wanneer de `runAllPreUpgradeHealthChecks` -methode wordt aangeroepen:

* **systeem** - de markering die door de granietcontroles van de onderhoudsgezondheid wordt gebruikt

* **pre-verbetering** - een douanetag die aan alle gezondheidscontroles kon worden toegevoegd die u kunt plaatsen om vóór een verbetering te lopen

De lijst kan worden bewerkt. U kunt de plus **(+) gebruiken** en minus **(-)** behalve de markeringen om meer douanetags toe te voegen, of standaarddegenen te verwijderen.

**MBean Methods**

De beheerde boonfunctionaliteit kan worden betreden gebruikend de [ Console JMX ](/help/sites-administering/jmx-console.md).

U kunt tot MBeans toegang hebben door:

1. Ga naar de Console JMX in *https://serveraddress:serverport/system/console/jmx*
1. Onderzoek naar **PreUpgradeTasks** en klik het resultaat

1. Selecteer om het even welke methode van de **sectie van Verrichtingen** en selecteer **aanhalen** in het volgende venster.

Hieronder vindt u een lijst met alle beschikbare methoden die door de `PreUpgradeTasksMBeanImpl` worden beschreven:

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
   <td>Controleert of de <code>runAllPreUpgradeTasksmaintenance</code> -taak wordt uitgevoerd.</td>
  </tr>
  <tr>
   <td><code>getAnyPreUpgradeTaskRunning()</code></td>
   <td>ACTION_INFO</td>
   <td>Controleert of om het even welke pre-verbeterings onderhoudstaak loopt en <br /> keert een serie terug die de namen van momenteel lopende taken bevat.</td>
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
   <td><p>Voert alle gezondheidscontroles uit die vóór de upgrade worden uitgevoerd en slaat de status op in een bestand met de naam <code>preUpgradeHCStatus.properties</code> dat zich in het pad naar de installatiekopie bevindt. Wanneer de parameter <code>shutDownOnSuccess</code> op <code>true</code> is ingesteld, wordt de AEM afgesloten, maar alleen als alle gezondheidscontroles vóór de upgrade de status OK hebben.</p> <p>Het eigenschappendossier wordt gebruikt als voorwaarde voor om het even welke toekomstige verbetering <br /> en het verbeteringsproces wordt tegengehouden als de pre-verbeteringsgezondheidscontrole <br /> mislukte uitvoering. Als u het resultaat van de pre-verbeterings <br /> gezondheidscontroles wilt negeren en hoe dan ook de verbetering lanceren, kunt u het dossier schrappen.</p> </td>
  </tr>
  <tr>
   <td><code>detectUsageOfUnavailableAPI(aemVersion)</code></td>
   <td>ACTIE</td>
   <td>Maakt een lijst van alle ingevoerde pakketten die niet meer tevredenstellen wanneer <br /> bevordering aan de gespecificeerde AEM versie. De doel AEM versie moet <br /> worden gegeven als parameter.</td>
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

De manier waarop Aangepast `LoginModules` wordt geconfigureerd voor verificatie op het niveau van de opslagplaats is fundamenteel gewijzigd in Apache Oak.

In AEM versies die CRX2-configuratie gebruikten, is het bestand `repository.xml` geplaatst, en vanaf AEM 6 gebeurt dit in de service Configuratie van Apache Felix JAAS via de webconsole.

Daarom moeten bestaande configuraties na de upgrade worden uitgeschakeld en opnieuw worden gemaakt voor Apache Oak.

Als u de aangepaste modules die zijn gedefinieerd in de JAAS-configuratie van `repository.xml` wilt uitschakelen, moet u de configuratie bewerken om de standaardwaarde `LoginModule` te gebruiken, zoals in het volgende voorbeeld:

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
>Voor meer informatie, zie [ Authentificatie met de Externe Login Module ](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).
>
>Voor een voorbeeld van `LoginModule` configuratie in AEM 6, zie [ Vormend LDAP met AEM 6 ](/help/sites-administering/ldap-config.md).

## Updates verwijderen uit de map /install {#remove-updates-install-directory}

>[!NOTE]
>
>Verwijder alleen pakketten uit de map crx-quickstart/install NA het afsluiten van de AEM. Deze stap is één van het laatste alvorens de op zijn plaats verbeteringsprocedure te beginnen.

Verwijder alle servicepacks, functiepakketten of hotfixes die via de map `crx-quickstart/install` in het lokale bestandssysteem zijn geïmplementeerd. Hierdoor wordt voorkomen dat oude hotfixes en servicepacks onbedoeld boven op de nieuwe AEM worden geïnstalleerd nadat de update is voltooid.

## Koude stand-byinstanties stoppen {#stop-tarmk-coldstandby-instance}

Als u TarMK koude stand-by gebruikt, moet u eventuele koude stand-byinstanties stoppen. Dit garandeert een efficiënte manier om online terug te keren als er problemen zijn in de upgrade. Nadat de verbetering met succes heeft voltooid, moeten de koude standby instanties van de promotieprimaire instanties worden herbouwd.

## Aangepaste geplande taken uitschakelen {#disable-custom-scheduled-jobs}

Schakel geplande OSGi-taken uit die in uw toepassingscode zijn opgenomen.

## Offline revisie opschonen uitvoeren {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Deze stap is alleen nodig voor TarMK-installaties

Als u TarMK gebruikt, moet u de functie Offline revisie opschonen uitvoeren voordat u de upgrade uitvoert. Hierdoor worden de migratie naar de opslagplaats en de daarop volgende upgradetaken veel sneller uitgevoerd en wordt ervoor gezorgd dat Online revisie-opschoning met succes kan worden uitgevoerd nadat de upgrade is voltooid. Voor informatie bij het in werking stellen van de Opruiming van de Off-line Revisie, zie [ het Uitvoeren van de Opruiming van de Offline Revisie ](/help/sites-deploying/storage-elements-in-aem-6.md#performing-offline-revision-cleanup).

## Verzameling van afval uit datastore uitvoeren {#execute-datastore-garbage-collection}

>[!NOTE]
>
>Deze stap is alleen nodig voor instanties met crx3

Nadat u de revisie hebt opgeschoond op CRX3-instanties, moet u de afvalverzameling van de datastore uitvoeren om eventuele niet-gerefereerde balken in de gegevensopslag te verwijderen. Voor instructies, zie de documentatie op [ de Inzameling van het huisvuil van de Opslag van Gegevens ](/help/sites-administering/data-store-garbage-collection.md).

## Upgrade het databaseschema indien nodig {#upgrade-the-database-schema-if-needed}

Gewoonlijk zorgt de onderliggende Apache Oak-stack die AEM gebruikt voor persistentie ervoor dat het databaseschema wordt bijgewerkt, indien nodig.

Er kunnen zich echter gevallen voordoen wanneer het schema niet automatisch kan worden bijgewerkt. Dergelijke gevallen zijn meestal omgevingen met hoge beveiliging waarin de database wordt uitgevoerd onder een gebruiker met beperkte rechten. Als een dergelijke situatie voorkomt, blijft AEM het oude schema gebruiken.

Om zulk een scenario te verhinderen te gebeuren, bevorder het schema door het volgende te doen:

1. Sluit de AEM instantie die moet worden bijgewerkt.
1. Upgrade het databaseschema. Raadpleeg de documentatie bij het databasetype om te zien welke gereedschappen nodig zijn om het resultaat te bereiken.

   Voor meer informatie over hoe Oak schemaverbeteringen behandelt, zie [ deze pagina op de website Apache ](https://jackrabbit.apache.org/oak/docs/nodestore/document/rdb-document-store.html#upgrade).

1. Ga verder met het upgraden van AEM.

## Gebruikers verwijderen die de upgrade mogelijk kunnen blokkeren {#delete-users-that-might-hinder-the-upgrade}

>[!NOTE]
>
>Deze onderhoudstaak voorafgaand aan de upgrade is alleen nodig als:
>
>* U voert een upgrade uit vanaf AEM oudere versies dan AEM 6.3
>* Tijdens de upgrade worden de hieronder vermelde fouten aangetroffen.
>

In uitzonderlijke gevallen kunnen servicegebruikers in een oudere versie van AEM niet correct zijn gecodeerd als normale gebruikers.

Als een dergelijke situatie gebeurt, ontbreekt de verbetering met een bericht als het volgende:

```
ERROR [Apache Sling Repository Startup Thread] com.adobe.granite.repository.impl.SlingRepositoryManager Exception in a SlingRepositoryInitializer, SlingRepository service registration aborted
java.lang.RuntimeException: Unable to create service user [communities-utility-reader]:java.lang.RuntimeException: Existing user communities-utility-reader is not a service user.
```

U kunt dit probleem omzeilen door het volgende te doen:

1. De instantie loskoppelen van het productieverkeer
1. Maak een back-up van een of meer gebruikers die het probleem veroorzaken. U kunt deze taak uitvoeren via Package Manager. Voor meer informatie, zie [ hoe te met Pakketten werken.](/help/sites-administering/package-manager.md)
1. Verwijder een of meer gebruikers die het probleem veroorzaken. Hieronder volgt een lijst met gebruikers die mogelijk onder deze categorie vallen:

   1. `dynamic-media-replication`
   1. `communities-ugc-writer`
   1. `communities-utility-reader`
   1. `communities-user-admin`
   1. `oauthservice`
   1. `sling-scripting`

## Logbestanden roteren {#rotate-log-files}

Adobe raadt u aan uw huidige logbestanden te archiveren voordat u begint met de upgrade. Zo kunt u logbestanden tijdens en na de upgrade gemakkelijker controleren en scannen om eventuele problemen op te sporen en op te lossen.
