---
title: Een op locatie uitgevoerde upgrade uitvoeren
description: Leer hoe u een upgrade ter plekke uitvoert voor AEM 6.5.
topic-tags: upgrading
feature: Upgrading
exl-id: aef6ef00-993c-4252-b0ad-ddc4917beaf7
source-git-commit: 9d497413d0ca72f22712581cf7eda1413eb8d643
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 0%

---

# Een op locatie uitgevoerde upgrade uitvoeren{#performing-an-in-place-upgrade}

>[!NOTE]
>
>Deze pagina schetst de verbeteringsprocedure voor AEM 6.5. Als u een installatie hebt die aan een toepassingsserver wordt opgesteld, zie [Upgradestappen voor installatie van toepassingsservers](/help/sites-deploying/app-server-upgrade.md).

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [Code en aanpassingen bijwerken](/help/sites-deploying/upgrading-code-and-customizations.md) en [Onderhoudstaken vóór upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie . Zorg er bovendien voor dat uw systeem voldoet aan de vereisten voor de nieuwe versie van AEM. Zie hoe u de complexiteit van uw upgrade kunt inschatten met behulp van Patroondetector en ook de sectie Upgradebereik en -vereisten van [Uw upgrade plannen](/help/sites-deploying/upgrade-planning.md) voor meer informatie .

<!--Finally, the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Migratievereisten {#migration-prerequisites}

* **Minimale vereiste Java-versie:** Het migratiehulpprogramma werkt alleen met Java versies 7 en hoger. Voor AEM 6.3 en hoger zijn JRE 8 en IBM JRE 7 en 8 van Oracle de enige ondersteunde versies.

* **Bijgewerkte instantie:** Als u een upgrade uitvoert vanaf een versie **ouder dan 5,6**, zorg ervoor dat u een op zijn plaats verbetering aan AEM 6.0 door de procedure te volgen hebt uitgevoerd die in versie 6.0 van de documentatie van de Verbetering wordt beschreven.

## Voorbereiding van het AEM QuickStart-jar-bestand {#prep-quickstart-file}

1. Stop de instantie als deze wordt uitgevoerd.

1. Download het nieuwe AEM jar-bestand en gebruik dit om het oude bestand buiten de `crx-quickstart` map.

1. Pak de nieuwe QuickStart-jar uit door deze uit te voeren:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

## Migratie van opslagplaats voor inhoud {#content-repository-migration}

Deze migratie is niet vereist als u een upgrade uitvoert vanaf AEM 6.3. Voor versies ouder dan 6.3, verstrekt de Adobe een hulpmiddel dat kan worden gebruikt om de bewaarplaats aan de nieuwe versie van de Tar van het Segment van het Eak in AEM 6.3 te migreren. Deze wordt geleverd als onderdeel van het pakket quickstart en is verplicht voor alle upgrades die TarMK zullen gebruiken. Voor upgrades voor omgevingen die gebruikmaken van MongoMK is geen migratie naar opslagplaats vereist. Zie voor meer informatie over de voordelen van de nieuwe indeling Segment Tar de [Veelgestelde vragen over migreren naar eikensegment](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

De werkelijke migratie wordt uitgevoerd met het standaard AEM quickstart jar-bestand, uitgevoerd met een nieuw `-x crx2oak` die het crx2oak-gereedschap uitvoert om de upgrade te vereenvoudigen en robuuster te maken.

>[!NOTE]
>
>Als u de migratie van TarMK-inhoud in de repository uitvoert met de CRX2Oak QuickStart-extensie, kunt u mogelijk de **samplinginhoud** runmode door het volgende aan de lijn van het migratiebevel toe te voegen:
>
>* `--promote-runmode nosamplecontent`
>

Gebruik de volgende opdracht om te bepalen welke opdracht u moet uitvoeren:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Wanneer `<<YOUR_PROFILE>>` en `<<ADDITIONAL_FLAGS>>` worden vervangen door het profiel en de markeringen in de volgende tabel:

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

**Waarbij:**

* `mongo-host` is de IP van de MongoDB-server (bijvoorbeeld 127.0.0.1)

* `mongo-port` is de MongoDB-serverpoort (bijvoorbeeld: 27017)

* `mongo-database-name` staat voor de naam van de database (bijvoorbeeld: aem-auteur)

**U kunt extra schakelaars voor de volgende scenario&#39;s ook vereisen:**

* Als u de upgrade uitvoert op een Windows-systeem waar Java-geheugentoewijzing niet correct wordt verwerkt, voegt u de opdracht `--disable-mmap` aan het bevel.

Voor meer instructies over het gebruik van het crx2oak-gereedschap raadpleegt u het dialoogvenster [CRX2Oak-migratiehulpmiddel](/help/sites-deploying/using-crx2oak.md). U kunt indien nodig handmatig een upgrade uitvoeren van de crx2oak-hulplijn door deze handmatig te vervangen door nieuwere versies nadat u de snelstart hebt uitgenomen. De installatiemap van AEM bevindt zich op de volgende locatie: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. De nieuwste versie van het CRX2Oak-migratiehulpprogramma kan worden gedownload van de opslagplaats voor Adoben op: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

Als de migratie is voltooid, wordt het gereedschap afgesloten met de afsluitcode nul. Controleer bovendien op WAARSCHUWING- en FOUTberichten in het dialoogvenster `upgrade.log` bestand, zich onder `crx-quickstart/logs` in de AEM installatiemap, aangezien deze kunnen wijzen op niet-fatale fouten die zich tijdens de migratie hebben voorgedaan.

Controleer de onderstaande configuratiebestanden `crx-quickstart/install` map. Als er een migratie nodig was, worden deze bijgewerkt om de doelopslagplaats te weerspiegelen.

**Een opmerking over datastores:**

while `FileDataStore` is het nieuwe gebrek voor AEM 6.3 installaties, wordt het gebruiken van een externe datastore niet vereist. Terwijl het gebruiken van een externe datastore als beste praktijken voor productielokaties wordt geadviseerd, is het geen eerste vereiste om te bevorderen. Vanwege de complexiteit die al aanwezig is bij de upgrade van AEM, raadt Adobe aan de upgrade uit te voeren zonder een datastore-migratie uit te voeren. Indien gewenst, kan een datastore migratie achteraf als afzonderlijke inspanning worden uitgevoerd.

## Problemen met migratie oplossen {#troubleshooting-migration-issues}

Sla deze sectie over als u een upgrade uitvoert vanaf 6.3. Hoewel de aangeboden crx2oak-profielen aan de behoeften van de meeste klanten moeten voldoen, zijn er momenten waarop extra parameters nodig zullen zijn. Als u tijdens de migratie een fout tegenkomt, is het mogelijk dat er aspecten van uw omgeving zijn waarvoor aanvullende configuratieopties moeten worden opgegeven. Als dat het geval is, treedt waarschijnlijk de volgende fout op:

**Controlepunten worden niet gekopieerd omdat er geen externe datastore is opgegeven. Dit zal ertoe leiden dat de volledige opslagplaats opnieuw aan de eerste start wordt onderworpen. Gebruik —skip-checkpoints om de migratie te dwingen of https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration voor meer informatie te zien.**

Om een of andere reden heeft het migratieproces toegang tot binaire bestanden in de datastore nodig en kan het proces niet vinden. Neem de volgende markeringen op in het dialoogvenster `<<ADDITIONAL_FLAGS>>` gedeelte van uw migratieopdracht:

**Voor S3-datastores:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Wanneer `/path/to/SharedS3DataStore.config` vertegenwoordigt de weg aan uw S3 datastore configuratiedossier en `/path/to/datastore` vertegenwoordigt de weg aan uw S3 datastore.

**Voor datastores van bestand:**

```shell
--src-datastore=/path/to/datastore
```

Wanneer `/path/to/datastore` geeft het pad naar uw gegevensopslagruimte voor bestanden aan.

## De upgrade uitvoeren {#performing-the-upgrade}

**Bij gebruik van S3:**

1. Eventuele onderliggende potten verwijderen `crx-quickstart/install` gekoppeld aan een eerdere versie van de S3-connector.

1. Download de recentste versie van de 1.10.x S3 schakelaar van [https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/)

1. Extraheer het pakket naar een tijdelijke map en kopieer de inhoud van `jcr_root/libs/system/install` aan de `crx-quickstart/install` map.

### Bepaal het correcte bevel van het verbeteringsbegin {#determining-the-correct-upgrade-start-command}

Als u de upgrade wilt uitvoeren, is het belangrijk dat u AEM het jar-bestand gaat gebruiken om de instantie op te roepen. Voor een upgrade naar 6.5 raadpleegt u de overige opties voor het herstructureren van inhoud en migratie in [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md) die u met het verbeteringsbevel kunt kiezen.

>[!IMPORTANT]
>
>Als u Oracle Java 11 (of over het algemeen versies van Java nieuwer dan 8) in werking stelt, moeten de extra schakelaars aan uw bevellijn worden toegevoegd wanneer het beginnen van AEM. Zie voor meer informatie [Overwegingen bij Java 11](/help/sites-deploying/custom-standalone-install.md#java-considerations).

Merk op dat het beginnen van AEM van het beginmanuscript niet de verbetering zal beginnen. De meeste klanten beginnen AEM het beginmanuscript te gebruiken en hebben dit beginmanuscript aangepast om schakelaars voor omgevingsconfiguraties zoals geheugenmontages, veiligheidscertificaten, etc. te omvatten. Om deze reden, adviseert de Adobe na deze procedure om het juiste verbeteringsbevel te bepalen:

1. Voer bij een actieve AEM de volgende handelingen uit vanaf de opdrachtregel:

   ```shell
   ps -ef | grep java
   ```

1. Zoek naar het AEM. Het zal er ongeveer als volgt uitzien:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.5.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Wijzig het bevel door de weg aan het bestaande kruis te vervangen ( `crx-quickstart/app/aem-quickstart*.jar` in dit geval ) met de nieuwe jar die een zusterbeweging is van de `crx-quickstart` map. Gebruikend ons vorige bevel als voorbeeld, zou ons bevel zijn:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar cq-quickstart-6.5.0.jar -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Hierdoor worden alle juiste geheugeninstellingen, aangepaste runmodi en andere omgevingsparameters voor de upgrade toegepast. Nadat de upgrade is voltooid, kan de instantie met het beginscript worden gestart in de toekomst.

## Bijgewerkte Codebase implementeren {#deploy-upgraded-codebase}

Zodra het op zijn plaats verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in [Pagina Code en aanpassingen bijwerken](/help/sites-deploying/upgrading-code-and-customizations.md).

## Controles achteraf en probleemoplossing uitvoeren {#perform-post-upgrade-check-troubleshooting}

Zie [Controles en probleemoplossing na upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
