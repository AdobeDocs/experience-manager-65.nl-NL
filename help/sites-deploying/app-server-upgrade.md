---
title: Upgradestappen voor installatie van toepassingsservers
seo-title: Upgradestappen voor installatie van toepassingsservers
description: Leer hoe te om instanties van AEM te bevorderen die via de Servers van de Toepassing worden opgesteld.
seo-description: Leer hoe te om instanties van AEM te bevorderen die via de Servers van de Toepassing worden opgesteld.
uuid: e4020966-737c-40ea-bfaa-c63ab9a29cee
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 1876d8d6-bffa-4a1c-99c0-f6001acea825
docset: aem65
feature: Bijwerken
exl-id: 86dd10ae-7f16-40c8-84b6-91ff2973a523
translation-type: tm+mt
source-git-commit: d99f4ce072688f8e7d453199742618f0b2357d07
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# De stappen van de verbetering voor de Installaties van de Server van de Toepassing{#upgrade-steps-for-application-server-installations}

Deze sectie beschrijft de procedure die moet worden gevolgd om AEM voor de installaties van de Server van de Toepassing bij te werken.

Alle voorbeelden in deze procedure gebruiken Tomcat als de Server van de Toepassing en impliceren dat u een werkende versie van AEM reeds opgesteld hebt. De procedure is bedoeld om upgrades te documenteren die worden uitgevoerd van **AEM versie 6.4 tot 6.5**.

1. Start eerst TomCat. In de meeste situaties, kunt u dit doen door het `./catalina.sh` startmanuscript in werking te stellen, door dit bevel van de terminal in werking te stellen:

   ```shell
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Als AEM 6.4 al is geïmplementeerd, controleert u of de bundels correct werken door toegang te krijgen tot:

   ```shell
   https://<serveraddress:port>/cq/system/console/bundles
   ```

1. Verwijder vervolgens AEM 6.4. Dit kan worden gedaan vanuit de TomCat App Manager (`http://serveraddress:serverport/manager/html`)

1. Migreer nu de opslagplaats met het crx2oak-migratiehulpprogramma. Hiervoor downloadt u de nieuwste versie van crx2oak van [deze locatie](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak).

   ```shell
   SLING_HOME= $AEM-HOME/crx-quickstart java -Xmx4096m -XX:MaxPermSize=2048M -jar crx2oak.jar --load-profile segment-fds
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

   * De **startmap**. U kunt het schrappen door het volgende bevel in de terminal in werking te stellen: `rm -rf crx-quickstart/launchpad/startup`

   * Het **base.jar-bestand**: `find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \`

   * Het bestand **BootstrapCommandFile_timestamp.txt**: `rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt`

   * **sling.options.file** verwijderen door uit te voeren: `find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf`

1. Creëer nu de knoopopslag en de gegevensopslag die met AEM 6.5 zullen worden gebruikt. U kunt dit doen door twee dossiers met de volgende namen onder `crx-quickstart\install` te creëren:

   * `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.cfg`
   * `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.cfg`

   Deze twee dossiers zullen AEM vormen om een TarMK knoopopslag en een de gegevensopslag van het Dossier te gebruiken.

1. Bewerk de configuratiebestanden om deze gebruiksklaar te maken. Meer specifiek:

   * Voeg de volgende regel toe aan `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config`:

      ```customBlobStore=true```

   * Voeg vervolgens de volgende regels toe aan `org.apache.jackrabbit.oak.plugins.blob.datastore.FileDataStore.config`:

      ```
      path=./crx-quickstart/repository/datastore
      minRecordLength=4096
      ```

1. U moet nu de uitvoeringswijzen in het AEM 6.5 oorlogsdossier veranderen. Hiertoe maakt u eerst een tijdelijke map waarin de oorlog van AEM 6.5 wordt ondergebracht. De naam van de map in dit voorbeeld is `temp`. Nadat het oorlogsbestand is gekopieerd, pakt u de inhoud uit door de inhoud uit te voeren vanuit de tijdelijke map:

   ```
   jar xvf aem-quickstart-6.5.0.war
   ```

1. Nadat de inhoud is uitgepakt, gaat u naar de map **WEB-INF** en bewerkt u het bestand web.xml om de uitvoermodi te wijzigen. Als u de locatie wilt zoeken waar deze in de XML zijn ingesteld, zoekt u de tekenreeks `sling.run.modes`. Als u deze eenmaal hebt gevonden, wijzigt u de uitvoeringsmodi in de volgende coderegel, die standaard is ingesteld op auteur:

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
