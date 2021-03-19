---
title: Een op locatie uitgevoerde upgrade uitvoeren
seo-title: Een op locatie uitgevoerde upgrade uitvoeren
description: Leer hoe u een upgrade op locatie kunt uitvoeren.
seo-description: Leer hoe u een upgrade op locatie kunt uitvoeren.
uuid: 478cb9db-1ea8-4bdb-b333-411dcbf2d927
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
discoiquuid: fcb17227-ff1f-4b47-ae94-6b7f60923876
docset: aem65
feature: Bijwerken
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1276'
ht-degree: 0%

---


# Een op locatie uitgevoerde upgrade uitvoeren{#performing-an-in-place-upgrade}

>[!NOTE]
>
>Deze pagina schetst de verbeteringsprocedure voor AEM 6.5. Als u een installatie hebt die aan een toepassingsserver wordt opgesteld, zie [Stappen van de verbetering voor de Installaties van de Server van de Toepassing](/help/sites-deploying/app-server-upgrade.md).

## Pre-upgrade stappen {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [Code en aanpassingen bijwerken](/help/sites-deploying/upgrading-code-and-customizations.md) en [Onderhoudstaken vóór upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Zorg er bovendien voor dat uw systeem voldoet aan de vereisten voor de nieuwe versie van AEM. Zie hoe de Detector van het Patroon u kan helpen de ingewikkeldheid van uw verbetering schatten en ook de sectie van het Toepassingsgebied en van de Vereisten van de Verbetering van [Planning van Uw Verbetering](/help/sites-deploying/upgrade-planning.md) voor meer informatie zien.

<!--Finally, note that the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Migratievereisten {#migration-prerequisites}

* **Minimaal vereiste Java-versie:** het migratiehulpprogramma werkt alleen met Java versies 7 en hoger. Voor AEM 6.3 en hoger zijn JRE 8 en JRE 7 &amp; 8 van IBM de enige ondersteunde versies.

* **Bijgewerkte Instantie:** Als u van een versie  **ouder dan 5.6** bevordert, zorg ervoor dat u een op-plaats verbetering aan AEM 6.0 door de procedure hebt uitgevoerd te volgen die in versie 6.0 van de documentatie van de Verbetering wordt beschreven.

## Voorbereiding van het AEM QuickStart-jar-bestand {#prep-quickstart-file}

1. Stop de instantie als deze wordt uitgevoerd.

1. Download het nieuwe AEM jar-bestand en gebruik dit om het oude bestand buiten de map `crx-quickstart` te vervangen.

1. Pak de nieuwe QuickStart-jar uit door deze uit te voeren:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

## Migratie van opslagplaats voor inhoud {#content-repository-migration}

Deze migratie is niet vereist als u een upgrade uitvoert vanaf AEM 6.3. Voor versies ouder dan 6.3, verstrekt Adobe een hulpmiddel dat kan worden gebruikt om de bewaarplaats aan de nieuwe versie van de Tar van het Segment van het Eak in AEM 6.3 te migreren. Deze wordt geleverd als onderdeel van het pakket quickstart en is verplicht voor alle upgrades die TarMK zullen gebruiken. Voor upgrades voor omgevingen die gebruikmaken van MongoMK is geen migratie naar opslagplaats vereist. Voor meer informatie over wat de voordelen van het nieuwe formaat van de Tar van het Segment zijn, zie [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

De werkelijke migratie wordt uitgevoerd met het standaard AEM QuickStart-jar-bestand, uitgevoerd met een nieuwe `-x crx2oak`-optie die het crx2oak-gereedschap uitvoert om de upgrade te vereenvoudigen en robuuster te maken.

>[!NOTE]
>
>Als u de migratie van TarMK-opslagplaats uitvoert met de CRX2Oak QuickStart-extensie, kunt u de **samplcontent** runtime mode verwijderen door het volgende toe te voegen aan de migratie opdrachtregel:
>
>* `--promote-runmode nosamplecontent`

>



Gebruik de volgende opdracht om te bepalen welke opdracht u moet uitvoeren:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Waarbij `<<YOUR_PROFILE>>` en `<<ADDITIONAL_FLAGS>>` worden vervangen door het profiel en de markeringen in de volgende tabel:

<table>
 <tbody>
  <tr>
   <td><strong>Bronopslagplaats</strong></td>
   <td><strong>Doelopslagplaats</strong></td>
   <td><strong>Profiel</strong></td>
   <td><strong>Aanvullende markeringen</strong><br /> </td>
  </tr>
  <tr>
   <td>crx2 of TarMK met <code>FileDataStore</code></td>
   <td>TarMK</td>
   <td>segment-fds</td>
   <td>Zie de sectie Problemen oplossen hieronder</td>
  </tr>
  <tr>
   <td>crx2</td>
   <td>MongoMK</td>
   <td>mongo-from-crx2 </td>
   <td><code>-T mongo-uri=mongo://mongo-host:mongo-port -T mongo-db=mongo-database-name</code></td>
  </tr>
  <tr>
   <td>TarMK of crx2 met <code>S3DataStore</code></td>
   <td>TarMK</td>
   <td>segment-douane-ds</td>
   <td>Zie de sectie Problemen oplossen hieronder</td>
  </tr>
  <tr>
   <td>TarMK zonder datastore</td>
   <td>TarMK</td>
   <td>segment-geen-ds</td>
   <td> </td>
  </tr>
  <tr>
   <td>MongoMK</td>
   <td>MongoMK</td>
   <td>Er is geen migratie nodig</td>
   <td> </td>
  </tr>
 </tbody>
</table>

**Waar:**

* `mongo-host` is de IP van de MongoDB-server (bijvoorbeeld 127.0.0.1)

* `mongo-port` is de MongoDB-serverpoort (bijvoorbeeld: (27017)

* `mongo-database-name` vertegenwoordigt de naam van de database (bijvoorbeeld: auteur)

**U kunt extra schakelaars voor de volgende scenario&#39;s ook vereisen:**

* Als u de verbetering op een systeem van Vensters uitvoert waar het geheugenafbeelding van Java niet correct wordt behandeld, te voegen gelieve de `--disable-mmap` parameter aan het bevel toe.

* Als u Java 7 gebruikt, voegt u de parameter `-XX:MaxPermSize=2048m` net na de parameter `-Xmx` toe.

Voor extra instructies bij het gebruiken van het crx2oak hulpmiddel, zie het Gebruiken van [CRX2Oak Hulpmiddel van de Migratie](/help/sites-deploying/using-crx2oak.md). U kunt indien nodig handmatig een upgrade uitvoeren van de crx2oak-hulplijn door deze handmatig te vervangen door nieuwere versies nadat u de snelstart hebt uitgenomen. De installatiemap van AEM bevindt zich op de volgende locatie: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. De nieuwste versie van het CRX2Oak-migratiehulpprogramma kan worden gedownload van de Adobe Repository op: [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/crx2oak/)

Als de migratie is voltooid, wordt het gereedschap afgesloten met de afsluitcode nul. Bovendien, controleer WARN en FOUTberichten in het `upgrade.log` dossier, dat onder `crx-quickstart/logs` in de AEM installatiemap wordt gevestigd, aangezien deze op niet-fatale fouten konden wijzen die tijdens de migratie voorkwamen.

Controleer de configuratiebestanden onder `crx-quickstart/install` map. Als er een migratie nodig was, worden deze aangepast aan de doelopslagplaats.

**Een opmerking over datastores:**

Hoewel `FileDataStore` de nieuwe standaardinstelling is voor AEM 6.3-installaties, is het gebruik van een externe datastore niet vereist. Terwijl het gebruiken van een externe datastore als beste praktijken voor productielokaties wordt geadviseerd, is het geen eerste vereiste om te bevorderen. Vanwege de complexiteit die al aanwezig is bij de upgrade van AEM, raden we u aan de upgrade uit te voeren zonder een datastore-migratie uit te voeren. Indien gewenst, kan een datastore migratie achteraf als afzonderlijke inspanning worden uitgevoerd.

## Problemen met migratie oplossen {#troubleshooting-migration-issues}

Sla deze sectie over als u een upgrade uitvoert vanaf 6.3. Hoewel de aangeboden crx2oak-profielen aan de behoeften van de meeste klanten moeten voldoen, zijn er momenten waarop extra parameters nodig zullen zijn. Als u tijdens de migratie een fout tegenkomt, is het mogelijk dat er aspecten van uw omgeving zijn waarvoor aanvullende configuratieopties moeten worden opgegeven. Als dat het geval is, treedt waarschijnlijk de volgende fout op:

**Controlepunten worden niet gekopieerd omdat er geen externe datastore is opgegeven. Dit zal ertoe leiden dat de volledige opslagplaats opnieuw aan de eerste start wordt onderworpen. Gebruik —skip-checkpoints om de migratie te dwingen of https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration voor meer info te zien.**

Om een of andere reden heeft het migratieproces toegang tot binaire bestanden in de datastore nodig en kan het proces niet vinden. Om uw datastore configuratie te specificeren, omvat de volgende vlaggen in het `<<ADDITIONAL_FLAGS>>` gedeelte van uw migratiebevel:

**Voor S3-datastores:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Waar `/path/to/SharedS3DataStore.config` de weg aan uw S3 datastore configuratiedossier vertegenwoordigt en `/path/to/datastore` de weg aan uw S3 datastore vertegenwoordigt.

**Voor datastores van bestand:**

```shell
--src-datastore=/path/to/datastore
```

Waarbij `/path/to/datastore` het pad naar de datastore van uw bestand vertegenwoordigt.

## De upgrade {#performing-the-upgrade} uitvoeren

**Bij gebruik van S3:**

1. Verwijder om het even welke potten onder `crx-quickstart/install` verbonden aan een vroegere versie van de S3 schakelaar.

1. Download de recentste versie van de 1.10.x S3 schakelaar van [https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo.adobe.com/nexus/content/groups/public/com/adobe/granite/com.adobe.granite.oak.s3connector/)

1. Extraheer het pakket naar een tijdelijke map en kopieer de inhoud van `jcr_root/libs/system/install` naar de map `crx-quickstart/install`.

### Het bepalen van het correcte bevel van het verbeteringsbegin {#determining-the-correct-upgrade-start-command}

Als u de upgrade wilt uitvoeren, is het belangrijk dat u AEM het jar-bestand gaat gebruiken om de instantie op te roepen. Voor een upgrade naar 6.5 kunt u ook andere opties voor het herstructureren en migreren van inhoud bekijken in [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) die u kunt kiezen met de upgradeopdracht.

>[!IMPORTANT]
>
>Als u Oracle Java 11 (of over het algemeen versies van Java nieuwer dan 8) in werking stelt, zullen de extra schakelaars aan uw bevellijn moeten worden toegevoegd wanneer het beginnen AEM. Zie [Java 11 Overwegingen](/help/sites-deploying/custom-standalone-install.md#java-considerations) voor meer informatie.

Merk op dat het beginnen van AEM van het beginmanuscript niet de verbetering zal beginnen. De meeste klanten beginnen AEM het beginmanuscript te gebruiken en hebben dit beginmanuscript aangepast om schakelaars voor omgevingsconfiguraties zoals geheugenmontages, veiligheidscertificaten, enz. te omvatten. Om deze reden, adviseren wij na deze procedure om het juiste verbeteringsbevel te bepalen:

1. Voer bij een actieve AEM de volgende handelingen uit vanaf de opdrachtregel:

   ```shell
   ps -ef | grep java
   ```

1. Zoek het AEM. Het zal er ongeveer als volgt uitzien:

   ```shell
   /usr/bin/java -server -Xmx1024m -XX:MaxPermSize=256M -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.2.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Wijzig de opdracht door het pad naar de bestaande jar ( `crx-quickstart/app/aem-quickstart*.jar` in dit geval) te vervangen door de nieuwe jar die op hetzelfde niveau staat als de map `crx-quickstart`. Gebruikend ons vorige bevel als voorbeeld, zou ons bevel zijn:

   ```shell
   /usr/bin/java -server -Xmx1024m -XX:MaxPermSize=256M -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar cq-quickstart-6.5.0.jar -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Hierdoor worden alle juiste geheugeninstellingen, aangepaste runmodi en andere omgevingsparameters voor de upgrade toegepast. Nadat de upgrade is voltooid, kan de instantie met het beginscript worden gestart in de toekomst.

## Bijgewerkte codebase {#deploy-upgraded-codebase} implementeren

Zodra het op zijn plaats verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in [de pagina van de Code en van Aanpassingen van de Verbetering worden gevonden ](/help/sites-deploying/upgrading-code-and-customizations.md).

## Controle en probleemoplossing na upgrade uitvoeren {#perform-post-upgrade-check-troubleshooting}

Zie [Controle en probleemoplossing na upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
