---
title: Upgradestappen voor installatie van toepassingsservers
description: Leer hoe te om instanties van AEM te bevorderen die via de Servers van de Toepassing worden opgesteld.
feature: Upgrading
exl-id: 86dd10ae-7f16-40c8-84b6-91ff2973a523
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---

# Upgradestappen voor installatie van toepassingsservers{#upgrade-steps-for-application-server-installations}

Deze sectie beschrijft de procedure die moet worden gevolgd om AEM voor de installaties van de Server van de Toepassing bij te werken.

Alle voorbeelden in deze procedure gebruiken Tomcat als de Server van de Toepassing en impliceren dat u een werkende versie van AEM reeds opgesteld hebt. De procedure is bedoeld om upgrades te documenteren die zijn uitgevoerd vanaf **AEM versie 6.4 t/m 6.5**.

1. Start eerst TomCat. In de meeste gevallen kunt u dit doen door de `./catalina.sh` start startscript, door dit bevel uit te voeren vanaf de terminal:

   ```shell
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Als AEM 6.4 reeds wordt opgesteld, controleer dat de bundels correct functioneren door tot:

   ```shell
   https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Verwijder vervolgens AEM 6.4. Dit kan worden gedaan vanuit de TomCat App Manager (`http://serveraddress:serverport/manager/html`)

1. Migreer nu de opslagplaats met het crx2oak-migratiehulpprogramma. Download hiertoe de nieuwste versie van crx2oak van [deze locatie](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/).

   ```shell
   SLING_HOME= $AEM-HOME/crx-quickstart java -Xmx4096m -jar crx2oak.jar --load-profile segment-fds
   ```

1. Verwijder de benodigde eigenschappen in het bestand sling.properties door het volgende te doen:

   1. Open het bestand op `crx-quickstart/launchpad/sling.properties`
   1. Staptekst Verwijder de volgende eigenschappen en sla het bestand op:

      1. `sling.installer.dir`

      1. `felix.cm.dir`

      1. `granite.product.version`

      1. `org.osgi.framework.system.packages`

      1. `osgi-core-packages`

      1. `osgi-compendium-services`

      1. `jre-*`

      1. `sling.run.mode.install.options`

1. Verwijder de bestanden en mappen die u niet meer nodig hebt. De items die u specifiek moet verwijderen zijn:

   * De **startblok/startmap**. U kunt het schrappen door het volgende bevel in de terminal in werking te stellen: `rm -rf crx-quickstart/launchpad/startup`

   * De **base.jar, bestand**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`

   * De **BootstrapCommandFile_timestamp.txt, bestand**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

   * Verwijderen **sling.options.file** door uitvoering: `find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf`

1. Creëer nu de knoopopslag en gegevensopslag die met AEM 6.5 wordt gebruikt. U kunt dit doen door twee bestanden te maken met de volgende namen onder `crx-quickstart\install`:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`
   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Deze twee dossiers zullen AEM vormen om een TarMK knoopopslag en een de gegevensopslag van het Dossier te gebruiken.

1. Bewerk de configuratiebestanden om deze gebruiksklaar te maken. Meer specifiek:

   * Voeg de volgende regel toe aan `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`:

     `customBlobStore=true`

   * Voeg vervolgens de volgende regels toe aan `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`:

     ```
     path=./crx-quickstart/repository/datastore
     minRecordLength=4096
     ```

1. U moet nu de uitvoeringswijzen in het AEM 6.5 oorlogsdossier veranderen. Hiertoe maakt u eerst een tijdelijke map waarin de oorlog van AEM 6.5 wordt ondergebracht. De naam van de map in dit voorbeeld wordt `temp`. Nadat het oorlogsbestand is gekopieerd, pakt u de inhoud uit door de inhoud uit te voeren vanuit de tijdelijke map:

   ```
   jar xvf aem-quickstart-6.5.0.war
   ```

1. Als de inhoud is geëxtraheerd, gaat u naar de **WEB-INF** en bewerk het bestand web.xml om de uitvoermodi te wijzigen. Als u de locatie wilt zoeken waar deze in de XML zijn ingesteld, zoekt u de `sling.run.modes` tekenreeks. Als u deze eenmaal hebt gevonden, wijzigt u de uitvoeringsmodi in de volgende coderegel, die standaard is ingesteld op auteur:

   ```bash
   <param-value >author</param-value>
   ```

1. Wijzig de bovenstaande auteurwaarde en stel de uitvoeringsmodi in op: `author,crx3,crx3tar`. Het laatste codeblok moet er als volgt uitzien:

   ```
   <init-param>
   <param-name>sling.run.modes</param-name>
   <param-value>author,crx3,crx3tar</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

1. De pot opnieuw maken met de gewijzigde inhoud:

   ```bash
   jar cvf aem65.war
   ```

1. Ten slotte, zet het nieuwe oorlogsdossier in TomCat op.
