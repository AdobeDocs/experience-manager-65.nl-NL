---
title: Een op locatie uitgevoerde upgrade uitvoeren
description: Leer hoe u een upgrade ter plekke uitvoert voor AEM 6.5.
topic-tags: upgrading
feature: Upgrading
exl-id: aef6ef00-993c-4252-b0ad-ddc4917beaf7
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 0%

---

# Een op locatie uitgevoerde upgrade uitvoeren{#performing-an-in-place-upgrade}

>[!NOTE]
>
>Deze pagina schetst de verbeteringsprocedure voor AEM 6.5. Als u een installatie hebt die aan een toepassingsserver wordt opgesteld, zie [ de Stappen van de Verbetering voor de Installaties van de Server van de Toepassing ](/help/sites-deploying/app-server-upgrade.md).

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [ Bevorderend Code en Aanpassingen ](/help/sites-deploying/upgrading-code-and-customizations.md) en [ pre-Verbeterde Taken van het Onderhoud ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Zorg er bovendien voor dat uw systeem voldoet aan de vereisten voor de nieuwe versie van AEM. Zie hoe de Detector van het Patroon u kan helpen de ingewikkeldheid van uw upgarde schatten en ook de sectie van het Bereik en van de Vereisten van de Verbetering van [ zien die Uw Verbetering ](/help/sites-deploying/upgrade-planning.md) voor meer informatie plannen.

<!--Finally, the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Migratievereisten {#migration-prerequisites}

* **Minimaal Vereiste versie van Java:** het migratiehulpmiddel werkt slechts met versies 7 van Java en omhoog. Voor AEM 6.3 en hoger zijn JRE 8 en IBM JRE 7 en 8 van Oracle de enige ondersteunde versies.

* **Verbeterde Instantie:** als u van een versie **ouder dan 5.6** bevordert, zorg ervoor dat u een verbetering op zijn plaats aan AEM 6.0 door de procedure te volgen hebt uitgevoerd die in de 6.0 versie van de documentatie van de Verbetering wordt beschreven.

## Voorbereiding van het AEM QuickStart-jar-bestand {#prep-quickstart-file}

1. Stop de instantie als deze wordt uitgevoerd.

1. Download het nieuwe AEM jar-bestand en gebruik dit om het oude bestand buiten de map `crx-quickstart` te vervangen.

1. Pak de nieuwe QuickStart-jar uit door deze uit te voeren:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

## Migratie van opslagplaats voor inhoud {#content-repository-migration}

Deze migratie is niet vereist als u een upgrade uitvoert vanaf AEM 6.3. Voor versies ouder dan 6.3, verstrekt de Adobe een hulpmiddel dat kan worden gebruikt om de bewaarplaats aan de nieuwe versie van de Tar van het Segment van Oak in AEM 6.3 te migreren. Deze wordt geleverd als onderdeel van het pakket quickstart en is verplicht voor alle upgrades die TarMK zullen gebruiken. Voor upgrades voor omgevingen die gebruikmaken van MongoMK is geen migratie naar opslagplaats vereist. Voor meer informatie over wat de voordelen van het nieuwe formaat van Tar van het Segment zijn, zie [ migrerend aan de Veelgestelde vragen van Tar van het Segment van Oak ](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

De werkelijke migratie wordt uitgevoerd met het standaard AEM QuickStart-jar-bestand, uitgevoerd met een nieuwe `-x crx2oak` -optie die het crx2oak-gereedschap uitvoert om de upgrade te vereenvoudigen en robuuster te maken.

>[!NOTE]
>
>Als u de migratie van de Inhoud van de bewaarplaats TarMK gebruikend de uitbreiding van Quickstart CRX2Oak uitvoert, zou u de **steekproefinhoud** kunnen verwijderen runmode door het volgende aan de lijn van het migratiebevel toe te voegen:
>
>* `--promote-runmode nosamplecontent`
>

Gebruik de volgende opdracht om te bepalen welke opdracht u moet uitvoeren:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Waar `<<YOUR_PROFILE>>` en `<<ADDITIONAL_FLAGS>>` worden vervangen door het profiel en de markeringen in de volgende tabel:

<table>
 <tbody>
  <tr>
   <td><strong>Source-opslagplaats</strong></td>
   <td><strong>Doelopslagplaats</strong></td>
   <td><strong>Profiel</strong></td>
   <td><strong> Extra Vlaggen </strong><br /> </td>
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

**waar:**

* `mongo-host` is de IP van de MongoDB-server (bijvoorbeeld 127.0.0.1)

* `mongo-port` is de MongoDB-serverpoort (bijvoorbeeld: 27017)

* `mongo-database-name` staat voor de naam van de database (bijvoorbeeld: aem-auteur)

**u kunt extra schakelaars voor de volgende scenario&#39;s ook vereisen:**

* Als u de upgrade uitvoert op een Windows-systeem waar Java-geheugentoewijzing niet correct wordt verwerkt, voegt u de parameter `--disable-mmap` toe aan de opdracht.

Voor extra instructies bij het gebruiken van het crx2oak hulpmiddel, zie het Gebruiken van het [ CRX2Oak Hulpmiddel van de Migratie ](/help/sites-deploying/using-crx2oak.md). U kunt indien nodig handmatig een upgrade uitvoeren van de crx2oak-hulplijn door deze handmatig te vervangen door nieuwere versies nadat u de snelstart hebt uitgenomen. De locatie in de installatiemap van AEM is: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar` . De nieuwste versie van het CRX2Oak migratiehulpmiddel is beschikbaar voor download van de Bewaarplaats van de Adobe bij: [ https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/ ](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

Als de migratie is voltooid, wordt het gereedschap afgesloten met de afsluitcode nul. Controleer bovendien op WAARSCHUWING- en FOUTberichten in het `upgrade.log` -bestand, dat zich onder `crx-quickstart/logs` in de installatiemap van AEM bevindt, omdat deze kunnen wijzen op niet-fatale fouten die tijdens de migratie zijn opgetreden.

Controleer de configuratiebestanden onder de map `crx-quickstart/install` . Als er een migratie nodig was, worden deze bijgewerkt om de doelopslagplaats te weerspiegelen.

**Nota van A op datastores:**

Hoewel `FileDataStore` de nieuwe standaardinstelling is voor AEM 6.3-installaties, is het gebruik van een externe datastore niet vereist. Terwijl het gebruiken van een externe datastore als beste praktijken voor productielokaties wordt geadviseerd, is het geen eerste vereiste om te bevorderen. Vanwege de complexiteit die al aanwezig is bij de upgrade van AEM, raadt Adobe aan de upgrade uit te voeren zonder een datastore-migratie uit te voeren. Indien gewenst, kan een datastore migratie achteraf als afzonderlijke inspanning worden uitgevoerd.

## Problemen met migratie oplossen {#troubleshooting-migration-issues}

Sla deze sectie over als u een upgrade uitvoert vanaf 6.3. Hoewel de aangeboden crx2oak-profielen aan de behoeften van de meeste klanten moeten voldoen, zijn er momenten waarop extra parameters nodig zullen zijn. Als u tijdens de migratie een fout tegenkomt, is het mogelijk dat er aspecten van uw omgeving zijn waarvoor aanvullende configuratieopties moeten worden opgegeven. Als dat het geval is, treedt waarschijnlijk de volgende fout op:

**controlepunten worden niet gekopieerd, omdat geen externe datastore is gespecificeerd. Dit zal ertoe leiden dat de volledige opslagplaats opnieuw aan de eerste start wordt onderworpen. Gebruik - overslaan-controlepunten om de migratie te dwingen of https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration voor meer info te zien.**

Om een of andere reden heeft het migratieproces toegang tot binaire bestanden in de datastore nodig en kan het proces niet vinden. Neem de volgende markeringen op in het gedeelte `<<ADDITIONAL_FLAGS>>` van uw migratieopdracht om uw datastore-configuratie op te geven:

**voor S3 datastores:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Waar `/path/to/SharedS3DataStore.config` het pad naar uw S3 datastore config-bestand vertegenwoordigt en `/path/to/datastore` het pad naar uw S3 datastore.

**voor de datastores van het Dossier:**

```shell
--src-datastore=/path/to/datastore
```

Waar `/path/to/datastore` het pad naar de datastore van het bestand vertegenwoordigt.

## De upgrade uitvoeren {#performing-the-upgrade}

**als het gebruiken van S3:**

1. Verwijder eventuele potten onder `crx-quickstart/install` die zijn gekoppeld aan een eerdere versie van de S3-connector.

1. Download de recentste versie van de schakelaar 1.10.x S3 van [ https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/ ](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/)

1. Extraheer het pakket naar een tijdelijke map en kopieer de inhoud van `jcr_root/libs/system/install` naar de map `crx-quickstart/install` .

### Bepaal het correcte bevel van het verbeteringsbegin {#determining-the-correct-upgrade-start-command}

Als u de upgrade wilt uitvoeren, is het belangrijk dat u AEM het jar-bestand gaat gebruiken om de instantie op te roepen. Voor bevordering aan 6.5, zie andere inhoudsherstructurering en migratieopties in [ Uitgestelde Migratie van de Inhoud ](/help/sites-deploying/lazy-content-migration.md) die u met het verbeteringsbevel kunt kiezen.

>[!IMPORTANT]
>
>Als u Oracle Java 11 (of over het algemeen versies van Java nieuwer dan 8) in werking stelt, moeten de extra schakelaars aan uw bevellijn worden toegevoegd wanneer het beginnen van AEM. Voor meer informatie, zie [ Java 11 Overwegingen ](/help/sites-deploying/custom-standalone-install.md#java-considerations).

Merk op dat het beginnen van AEM van het beginmanuscript niet de verbetering zal beginnen. De meeste klanten beginnen AEM het beginmanuscript te gebruiken en hebben dit beginmanuscript aangepast om schakelaars voor omgevingsconfiguraties zoals geheugenmontages, veiligheidscertificaten, etc. te omvatten. Om deze reden, adviseert de Adobe na deze procedure om het juiste verbeteringsbevel te bepalen:

1. Voer bij een actieve AEM de volgende handelingen uit vanaf de opdrachtregel:

   ```shell
   ps -ef | grep java
   ```

1. Zoek naar het AEM. Het zal er ongeveer als volgt uitzien:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.5.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Wijzig de opdracht door het pad naar de bestaande jar ( `crx-quickstart/app/aem-quickstart*.jar` in dit geval) te vervangen door de nieuwe jar die op hetzelfde niveau staat als de map `crx-quickstart` . Gebruikend ons vorige bevel als voorbeeld, zou ons bevel zijn:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar cq-quickstart-6.5.0.jar -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Hierdoor worden alle juiste geheugeninstellingen, aangepaste runmodi en andere omgevingsparameters voor de upgrade toegepast. Nadat de upgrade is voltooid, kan de instantie met het beginscript worden gestart in de toekomst.

## Bijgewerkte Codebase implementeren {#deploy-upgraded-codebase}

Zodra het op zijn plaats verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in [ de Code en de pagina van Aanpassingen van de Verbetering ](/help/sites-deploying/upgrading-code-and-customizations.md) worden gevonden.

## Post-upgradecontroles en probleemoplossing uitvoeren {#perform-post-upgrade-check-troubleshooting}

Zie [ de Controles van de Verbetering van Post en het Oplossen van problemen ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
