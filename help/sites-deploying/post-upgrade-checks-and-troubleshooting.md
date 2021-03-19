---
title: Controles en probleemoplossing na upgrade
seo-title: Controles en probleemoplossing na upgrade
description: Leer hoe te om kwesties problemen op te lossen die na een verbetering zouden kunnen verschijnen.
seo-description: Leer hoe te om kwesties problemen op te lossen die na een verbetering zouden kunnen verschijnen.
uuid: 3f525f2c-8d25-4bb8-a57e-3adf667edde8
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
discoiquuid: 5a67aa9f-e5eb-4d7e-89da-2ee1a45eb8ce
docset: aem65
feature: Bijwerken
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '1830'
ht-degree: 0%

---


# Controles en probleemoplossing na upgrade{#post-upgrade-checks-and-troubleshooting}

## Controles na upgrade {#post-upgrade-checks}

Na [In-Place Verbetering](/help/sites-deploying/in-place-upgrade.md) zouden de volgende activiteiten moeten worden uitgevoerd om de verbetering te voltooien. Men veronderstelt AEM is begonnen met 6.5 jar en dat de promotiecode basis is opgesteld.

* [Logbestanden controleren voor een upgrade](#main-pars-header-290365562)

* [OSGi-bundels verifiëren](#main-pars-header-1637350649)

* [Oak-versie verifiëren](#main-pars-header-1293049773)

* [Inspect de map PreUpgradeBackup](#main-pars-header-988995987)

* [Eerste validatie van pagina&#39;s](#main-pars-header-20827371)
* [AEM servicepacks toepassen](#main-pars-header-215142387)

* [AEM migreren](#main-pars-header-1434457709)

* [Configuraties voor gepland onderhoud controleren](#main-pars-header-1552730183)

* [Replication-agents inschakelen](#main-pars-header-823243751)

* [Aangepaste geplande taken inschakelen](#main-pars-header-244535083)

* [Testplan uitvoeren](#main-pars-header-1167972233)

### Logboeken controleren voor upgradesucces {#verify-logs-for-upgrade-success}

**upgrade.log**

In het verleden was voor het inspecteren van de status van uw instantie na de upgrade zorgvuldige inspectie vereist van verschillende logbestanden, onderdelen van de opslagplaats en het startpad. Het genereren van een rapport na de upgrade kan u helpen defecte upgrades te detecteren voordat u live gaat.

Het belangrijkste doel van deze functie is om de behoefte aan handmatige interpretatie of complexe parseringslogica over veelvoudige eindpunten te verminderen die worden vereist om het succes van een verbetering te kwalificeren. De oplossing is bedoeld om ondubbelzinnige informatie te verschaffen aan externe automatiseringssystemen die reageren op het welslagen of de vastgestelde mislukking van een update.

Meer specifiek zorgt het ervoor dat:

* De mislukkingen van de verbetering die door het verbeteringskader worden ontdekt kunnen in één enkel verbeteringsrapport worden gecentraliseerd;
* Het verbeteringsrapport bevat indicatoren voor noodzakelijke handmatige interventie.

Om dit bij te voegen, zijn de veranderingen aangebracht in de manier het logboeken in het `upgrade.log` dossier worden geproduceerd.

Hier is een steekproefrapport dat geen fouten tijdens verbetering toont:

![1487887443006](assets/1487887443006.png)

Hier is een steekproefrapport dat een bundel toont die niet tijdens het verbeteringsproces werd geïnstalleerd:

![1487887532730](assets/1487887532730.png)

**error.log**

error.log zou zorgvuldig tijdens en na de aanvang van AEM moeten worden herzien gebruikend de jar van de doelversie. Alle waarschuwingen of fouten moeten worden herzien. In het algemeen is het beter om op kwesties aan het begin van het logboek te zoeken. Fouten die zich later in het logbestand voordoen, kunnen in feite bijwerkingen zijn van een hoofdoorzaak die vroeg in het bestand wordt aangeroepen. Zie [Problemen analyseren met de upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade) als zich herhaalde fouten en waarschuwingen voordoen.

### OSGi-bundels verifiëren {#verify-osgi-bundles}

Navigeer aan de console OSGi `/system/console/bundles` en kijk of om het even welke bundels niet zijn begonnen. Raadpleeg `error.log` als er bundels in een geïnstalleerde status zijn om het hoofdprobleem te bepalen.

### Oak-versie {#verify-oak-version} verifiëren

Na de verbetering zou u moeten zien dat de versie van eikel is bijgewerkt aan **1.10.2**. Om de versie te verifiëren van de eik navigeer aan de console OSGi en bekijk de versie verbonden aan de bundels van de eik: eiken kern, eiken komma&#39;s, eiken segmentteer.

### Inspect PreUpgradeBackup-map {#inspect-preupgradebackup-folder}

Tijdens de upgrade probeert AEM een back-up te maken van aanpassingen en deze onder `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>` op te slaan. Als u deze map in CRXDE Lite wilt weergeven, moet u mogelijk [tijdelijk CRXDE Lite](/help/sites-administering/enabling-crxde-lite.md) inschakelen.

De map met het tijdstempel moet een eigenschap met de naam `mergeStatus` hebben met de waarde `COMPLETED`. De **to-process** omslag zou leeg moeten zijn en de **overwritten** knoop wijst op welke knopen tijdens de verbetering werden beschreven. Inhoud onder de **leftovers**-node geeft inhoud aan die niet veilig kan worden samengevoegd tijdens de upgrade. Als uw implementatie afhankelijk is van een van de onderliggende knooppunten (en nog niet is geïnstalleerd door het aangepaste codepakket), moeten deze handmatig worden samengevoegd.

Schakel CRXDE Lite uit na deze bewerking als u een werkgebied of productieomgeving hebt.

### Eerste validatie van pagina&#39;s {#initial-validation-of-pages}

Voer een eerste validatie uit op meerdere pagina&#39;s in AEM. Als u een auteur-omgeving wilt bijwerken, opent u de startpagina en welkomstpagina ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). In zowel auteur- als publicatieomgevingen worden enkele toepassingspagina&#39;s en rooktests geopend die correct worden weergegeven. Als er problemen optreden, raadpleegt u `error.log` om problemen op te lossen.

### AEM servicepacks toepassen {#apply-aem-service-packs}

Pas alle relevante AEM 6.5-servicepacks toe als deze zijn vrijgegeven.

### AEM {#migrate-aem-features} migreren

Verscheidene eigenschappen in AEM vereisen extra stappen na de verbetering. Een volledige lijst van deze eigenschappen en stappen om hen in AEM 6.5 te migreren kunnen op [Upgraden Code en Klanten](/help/sites-deploying/upgrading-code-and-customizations.md) pagina worden gevonden.

### Configuraties voor gepland onderhoud controleren {#verify-scheduled-maintenance-configurations}

#### Afvalverzameling van gegevensopslag inschakelen {#enable-data-store-garbage-collection}

Als het gebruiken van een Opslag van de Gegevens van het Dossier ervoor zorgt dat de taak van de Inzameling van de Opslag van Gegevens wordt toegelaten en aan de Wekelijkse lijst van het Onderhoud toegevoegd. De instructies worden geschetst [hier](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Dit wordt niet geadviseerd voor de installaties van de douanegegevensopslag van S3 of wanneer het gebruiken van een gedeelde gegevensopslag.

#### Onlinerevisie-opruiming {#enable-online-revision-cleanup} inschakelen

Als u MongoMK of de nieuwe TarMK-segmentindeling gebruikt, zorgt u ervoor dat de taak Opruimen voor revisie is ingeschakeld en wordt toegevoegd aan de lijst Dagelijks onderhoud. Instructies [hier](/help/sites-deploying/revision-cleanup.md).

### Testplan uitvoeren {#execute-test-plan}

Gedetailleerd testplan uitvoeren op basis van de definitie [Code en aanpassingen upgraden](/help/sites-deploying/upgrading-code-and-customizations.md) onder de sectie **Testprocedure**.

### Replicatieagents {#enable-replication-agents} inschakelen

Zodra publicatiemilieu volledig is bevorderd en bevestigd, laat replicatieagenten op het Milieu van de Auteur toe. Verifieer dat de agenten met respectieve Publish instanties kunnen verbinden. Zie U [Procedure upgraden](/help/sites-deploying/upgrade-procedure.md) voor meer informatie over de volgorde van gebeurtenissen.

### Aangepaste geplande taken inschakelen {#enable-custom-scheduled-jobs}

Om het even welke geplande banen als deel van de codebasis kunnen op dit punt worden toegelaten.

## Problemen analyseren met de upgrade {#analyzing-issues-with-upgrade}

Deze sectie bevat sommige probleemscenario&#39;s één langs de verbeteringsprocedure aan AEM 6.3 zou kunnen worden geconfronteerd.

Deze scenario&#39;s zouden moeten helpen om de worteloorzaak van kwesties met betrekking tot verbetering te volgen en zouden moeten helpen om project of productspecifieke kwesties te identificeren.

### Migratie van opslagplaats mislukt {#repository-migration-failing-}

De gegevensmigratie van CRX2 naar eiken moet haalbaar zijn voor elk scenario dat begint met Broninstanties op basis van CQ 5.4. Zorg ervoor dat u de verbeteringsinstructies in dit document precies volgt die de voorbereiding van `repository.xml` omvatten, ervoor zorgt geen douaneauthentiek wordt begonnen via JAAS en de instantie is gecontroleerd op inconsistenties alvorens de migratie te beginnen.

Als de migratie nog ontbreekt kunt u erachter komen wat de worteloorzaak door `upgrade.log` te inspecteren is. Als het probleem nog niet bekend is, meld dit dan aan Customer Support.

### De upgrade is niet uitgevoerd {#the-upgrade-did-not-run}

Voordat u de voorbereidingsstappen start, moet u de **source**-instantie eerst uitvoeren door deze uit te voeren met de opdracht java -jar aem-quickstart.jar. Dit is vereist om ervoor te zorgen dat het bestand quickstart.properties op de juiste wijze wordt gegenereerd. Als deze ontbreekt, werkt de upgrade niet. U kunt ook controleren of het bestand aanwezig is door onder `crx-quickstart/conf` in de installatiemap van de broninstantie te kijken. Wanneer u AEM start om de upgrade uit te voeren, moet deze worden uitgevoerd met de opdracht java -jar aem-quickstart.jar. Het opstarten vanaf een beginscript start niet AEM in de upgrademodus.

### Pakketten en bundels kunnen niet worden bijgewerkt {#packages-and-bundles-fail-to-update-}

Als pakketten niet tijdens de upgrade worden geïnstalleerd, worden de bundels in de pakketten ook niet bijgewerkt. Deze categorie van kwesties wordt gewoonlijk veroorzaakt door wanconfiguratie van de gegevensopslag. Zij zullen ook als **ERROR** en **WARN** berichten in error.log verschijnen. Aangezien in de meeste van deze gevallen standaardlogin kan ontbreken om te werken, kunt u CRXDE direct gebruiken om de configuratieproblemen te inspecteren en te vinden.

### Sommige AEM Bundels schakelen niet naar de Actieve Staat {#some-aem-bundles-are-not-switching-to-the-active-state}

Als bundels niet beginnen zou u om het even welke ontevreden gebiedsdelen moeten controleren.

Als dit probleem zich voordoet, maar het is gebaseerd op een mislukte pakketinstallatie die ertoe heeft geleid dat bundels niet werden bijgewerkt, worden zij onverenigbaar geacht voor de nieuwe versie. Voor meer informatie over hoe te om dit problemen op te lossen, zie **Pakken en Bundels ontbreken aan Update** hierboven.

Het wordt ook aanbevolen de bundellijst van een nieuwe AEM 6.5-instantie te vergelijken met de bijgewerkte versie om de bundels te detecteren die niet zijn bijgewerkt. Dit zal een dichtere werkingsgebied van wat aan onderzoek in `error.log` verstrekken.

### Aangepaste bundels die niet overschakelen op de actieve status {#custom-bundles-not-switching-to-the-active-state}

Als uw aangepaste bundels niet naar de actieve status overschakelen, is het zeer waarschijnlijk dat er code is die geen wijziging-API importeert. Dit zal meestal leiden tot ontevreden afhankelijkheden.

API die is verwijderd, moet worden gemarkeerd als afgekeurd in een van de vorige releases. In dit bericht vindt u mogelijk instructies over een directe migratie van uw code. Adobe is bedoeld voor semantische versioning waar mogelijk, zodat de versies kunnen aangeven dat er wijzigingen zijn opgetreden.

Het is ook het beste om te controleren of de verandering die het probleem heeft veroorzaakt absoluut noodzakelijk was en het zo niet te herstellen. Controleer ook of de versieverhoging van de pakketexport meer dan nodig is, na strikte semantische versiebewerking.

### Onjuiste interface van Platform {#malfunctioning-platform-ui}

In het geval van bepaalde functionaliteit UI die niet behoorlijk na de verbetering werkt, zou u eerst douaneoverlays van de interface moeten controleren. Sommige structuren zijn mogelijk gewijzigd en de overlay moet mogelijk worden bijgewerkt of is verouderd.

Controleer vervolgens of er JavaScript-fouten optreden die kunnen worden bijgehouden bij aangepaste, toegevoegde extensies die zijn gekoppeld aan clientbibliotheken. Hetzelfde kan gelden voor aangepaste CSS die problemen kan veroorzaken voor de AEM-indeling.

Tot slot controleer misconfiguration dat Javascript niet zou kunnen behandelen. Dit is meestal het geval bij onjuist gedeactiveerde extensies.

### Onjuist functionerende aangepaste componenten, sjablonen of UI-extensies {#malfunctioning-custom-components-templates-or-ui-extensions}

In de meeste gevallen, zijn de worteloorzaken voor deze kwesties het zelfde als voor bundels die niet begonnen zijn of pakketten die niet met het enige verschil worden geïnstalleerd dat de kwesties beginnen op te duiken wanneer eerst het gebruiken van de componenten.

De manier om met onjuiste aangepaste code om te gaan is eerst rooktests uit te voeren om de oorzaak te achterhalen. Zodra u het vindt, bekijk de aanbevelingen in deze [link] sectie van het artikel voor manieren om hen te bevestigen.

### Ontbrekende aanpassingen onder /etc {#missing-customizations-under-etc}

`/apps` en  `/libs` worden goed afgehandeld door de upgrade, maar wijzigingen in de upgrade moeten  `/etc` mogelijk handmatig worden hersteld  `/var/upgrade/PreUpgradeBackup` na de upgrade. Controleer deze locatie op alle inhoud die handmatig moet worden samengevoegd.

### Het bestand error.log en upgrade.log {#analyzing-the-error.log-and-upgrade.log} analyseren

In de meeste gevallen moeten de logboeken worden geraadpleegd voor fouten om de oorzaak van een probleem te vinden. In het geval van upgrades is het echter ook nodig om afhankelijkheidskwesties te controleren, aangezien oude bundels mogelijk niet correct worden bijgewerkt.

De beste manier om dit te doen is onderaan error.log door van alle berichten te verwijderen die van geen verband met de kwestie worden verwacht u onder ogen ziet. U kunt dit doen door middel van hulpmiddel zoals grep, door te gebruiken:

```shell
grep -v UnrelatedErrorString
```

Sommige foutberichten zijn mogelijk niet direct expliciet. In dit geval kunt u door de context te bekijken waarin de fouten zich voordoen, beter begrijpen waar de fout is gemaakt. U kunt de fout scheiden met:

* `grep -B` voor het toevoegen van regels vóór de fout;

or

* `grep -A` voor het toevoegen van regels na.

In een paar gevallen kunnen er ook fouten worden gevonden in WARN-berichten, omdat er geldige gevallen kunnen zijn die tot deze status leiden en de toepassing niet altijd kan beslissen of dit een werkelijke fout is. Zorg ervoor dat u deze berichten ook raadpleegt.

### Contact opnemen met Adobe-ondersteuning {#contacting-adobe-support}

Als u het advies op deze pagina hebt doorgenomen en nog steeds problemen ziet, kunt u contact opnemen met de Adobe Support. Om zoveel mogelijk informatie aan de steuningenieur te verstrekken die aan uw geval werkt, te zorgen gelieve ervoor om het upgrade.log dossier van uw verbetering te omvatten.
