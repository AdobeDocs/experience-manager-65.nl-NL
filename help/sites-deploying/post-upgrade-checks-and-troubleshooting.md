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
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Controles en probleemoplossing na upgrade{#post-upgrade-checks-and-troubleshooting}

## Controles na upgrade {#post-upgrade-checks}

Na de [In-Place Verbetering](/help/sites-deploying/in-place-upgrade.md) zouden de volgende activiteiten moeten worden uitgevoerd om de verbetering te voltooien. Men veronderstelt AEM is begonnen met 6.5 jar en dat de promotiecode basis is opgesteld.

* [Logbestanden controleren voor een upgrade](#main-pars-header-290365562)

* [OSGi-bundels verifiëren](#main-pars-header-1637350649)

* [Oak-versie verifiëren](#main-pars-header-1293049773)

* [Inspecteer de map PreUpgradeBackup](#main-pars-header-988995987)

* [Eerste validatie van pagina&#39;s](#main-pars-header-20827371)
* [AEM-servicepacks toepassen](#main-pars-header-215142387)

* [AEM-functies migreren](#main-pars-header-1434457709)

* [Configuraties voor gepland onderhoud controleren](#main-pars-header-1552730183)

* [Replication-agents inschakelen](#main-pars-header-823243751)

* [Aangepaste geplande taken inschakelen](#main-pars-header-244535083)

* [Testplan uitvoeren](#main-pars-header-1167972233)

### Logboeken controleren voor upgrade voltooid {#verify-logs-for-upgrade-success}

**upgrade.log**

In het verleden was voor het inspecteren van de status van uw instantie na de upgrade zorgvuldige inspectie vereist van verschillende logbestanden, onderdelen van de opslagplaats en het startpad. Het genereren van een rapport na de upgrade kan u helpen defecte upgrades te detecteren voordat u live gaat.

Het belangrijkste doel van deze functie is om de behoefte aan handmatige interpretatie of complexe parseringslogica over veelvoudige eindpunten te verminderen die worden vereist om het succes van een verbetering te kwalificeren. De oplossing is bedoeld om ondubbelzinnige informatie te verschaffen aan externe automatiseringssystemen die reageren op het welslagen of de vastgestelde mislukking van een update.

Meer specifiek zorgt het ervoor dat:

* De mislukkingen van de verbetering die door het verbeteringskader worden ontdekt kunnen in één enkel verbeteringsrapport worden gecentraliseerd;
* Het verbeteringsrapport bevat indicatoren voor noodzakelijke handmatige interventie.

Hiervoor zijn wijzigingen aangebracht in de manier waarop logbestanden in het `upgrade.log` bestand worden gegenereerd.

Hier is een steekproefrapport dat geen fouten tijdens verbetering toont:

![1487887443006](assets/1487887443006.png)

Hier is een steekproefrapport dat een bundel toont die niet tijdens het verbeteringsproces werd geïnstalleerd:

![1487887532730](assets/1487887532730.png)

**error.log**

Het error.log moet tijdens en na het opstarten van AEM zorgvuldig worden gecontroleerd met behulp van de jar met de doelversie. Alle waarschuwingen of fouten moeten worden herzien. In het algemeen is het beter om op kwesties aan het begin van het logboek te zoeken. Fouten die zich later in het logbestand voordoen, kunnen in feite bijwerkingen zijn van een hoofdoorzaak die vroeg in het bestand wordt aangeroepen. Zie hieronder voor [Analyseren van problemen met de upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade)als zich herhaalde fouten en waarschuwingen voordoen.

### OSGi-bundels verifiëren {#verify-osgi-bundles}

Navigeer aan de console OSGi `/system/console/bundles` en kijk of zijn om het even welke bundels niet begonnen. Als er bundels zijn geïnstalleerd, raadpleegt u het `error.log` onderwerp om het hoofdprobleem te bepalen.

### Oak-versie verifiëren {#verify-oak-version}

Na de upgrade moet u zien dat de eikenversie is bijgewerkt naar **1.10.2**. Om de versie te verifiëren van de eik navigeer aan de console OSGi en bekijk de versie verbonden aan de bundels van de eik: eiken kern, eiken komma&#39;s, eiken segmentteer.

### PreUpgradeBackup-map controleren {#inspect-preupgradebackup-folder}

Tijdens de upgrade probeert AEM back-ups te maken van aanpassingen en deze onder te slaan `/var/upgrade/PreUpgradeBackup/<time-stamp-of-upgrade>`. Om deze omslag in CRXDE Lite te bekijken kunt u CRXDE Lite [tijdelijk moeten toelaten](/help/sites-administering/enabling-crxde-lite.md).

De map met het tijdstempel moet een eigenschap hebben met de naam `mergeStatus` met de waarde `COMPLETED`. De **te verwerken** map moet leeg zijn en het **overschreven** knooppunt geeft aan welke knooppunten tijdens de upgrade zijn overschreven. Inhoud onder het **restknooppunt** geeft aan dat inhoud niet veilig kan worden samengevoegd tijdens de upgrade. Als uw implementatie afhankelijk is van een van de onderliggende knooppunten (en nog niet is geïnstalleerd door het aangepaste codepakket), moeten deze handmatig worden samengevoegd.

Schakel CRXDE Lite na deze oefening uit als op een Stadium of een milieu van de Productie.

### Eerste validatie van pagina&#39;s {#initial-validation-of-pages}

Voer een eerste validatie uit op meerdere pagina&#39;s in AEM. Als u een auteur-omgeving wilt bijwerken, opent u de startpagina en de welkomstpagina ( `/aem/start.html`, `/libs/cq/core/content/welcome.html`). In zowel auteur- als publicatieomgevingen worden enkele toepassingspagina&#39;s en rooktests geopend die correct worden weergegeven. Als er problemen optreden, raadpleegt u de `error.log` om problemen op te lossen.

### AEM-servicepacks toepassen {#apply-aem-service-packs}

Pas relevante AEM 6.5-servicepacks toe als deze zijn vrijgegeven.

### AEM-functies migreren {#migrate-aem-features}

Voor verschillende functies in AEM zijn na de upgrade aanvullende stappen vereist. Een volledige lijst van deze eigenschappen en stappen om hen in AEM 6.5 te migreren kan op de [Upgraden Code en de pagina van Aanpassingen](/help/sites-deploying/upgrading-code-and-customizations.md) worden gevonden.

### Configuraties voor gepland onderhoud controleren {#verify-scheduled-maintenance-configurations}

#### Opruiming gegevensopslag inschakelen {#enable-data-store-garbage-collection}

Als het gebruiken van een Opslag van de Gegevens van het Dossier ervoor zorgt dat de taak van de Inzameling van de Opslag van Gegevens wordt toegelaten en aan de Wekelijkse lijst van het Onderhoud toegevoegd. Instructies worden [hier](/help/sites-administering/data-store-garbage-collection.md)beschreven.

>[!NOTE]
>
>Dit wordt niet geadviseerd voor de installaties van de douanegegevensopslag van S3 of wanneer het gebruiken van een gedeelde gegevensopslag.

#### Onlinerevisie-opruiming inschakelen {#enable-online-revision-cleanup}

Als u MongoMK of de nieuwe TarMK-segmentindeling gebruikt, zorgt u ervoor dat de taak Opruimen voor revisie is ingeschakeld en wordt toegevoegd aan de lijst Dagelijks onderhoud. Hier [beschreven instructies](/help/sites-deploying/revision-cleanup.md).

### Testplan uitvoeren {#execute-test-plan}

Uitvoeren van gedetailleerd testplan tegen zoals bepaald [Bevorderen Code en Aanpassingen](/help/sites-deploying/upgrading-code-and-customizations.md) onder de sectie van de Procedure **van de** Test.

### Replication-agents inschakelen {#enable-replication-agents}

Zodra publicatiemilieu volledig is bevorderd en bevestigd, laat replicatieagenten op het Milieu van de Auteur toe. Verifieer dat de agenten met respectieve Publish instanties kunnen verbinden. Zie Procedure [van](/help/sites-deploying/upgrade-procedure.md) niveau U voor meer informatie over de volgorde van gebeurtenissen.

### Aangepaste geplande taken inschakelen {#enable-custom-scheduled-jobs}

Om het even welke geplande banen als deel van de codebasis kunnen op dit punt worden toegelaten.

## Problemen analyseren met de upgrade {#analyzing-issues-with-upgrade}

Deze sectie bevat enkele probleemscenario&#39;s waarmee u tijdens de upgradeprocedure naar AEM 6.3 wordt geconfronteerd.

Deze scenario&#39;s zouden moeten helpen om de worteloorzaak van kwesties met betrekking tot verbetering te volgen en zouden moeten helpen om project of productspecifieke kwesties te identificeren.

### Migratie opslagplaats mislukt {#repository-migration-failing-}

De gegevensmigratie van CRX2 naar eiken moet haalbaar zijn voor elk scenario dat begint met Broninstanties op basis van CQ 5.4. Zorg ervoor dat u precies de verbeteringsinstructies in dit document volgt die de voorbereiding van `repository.xml`omvatten, ervoor zorgt geen douane authentificator via JAAS wordt begonnen en de instantie is gecontroleerd op inconsistenties alvorens de migratie te beginnen.

Als de migratie nog ontbreekt kunt u uitzoeken wat de worteloorzaak door het `upgrade.log`te inspecteren is. Als het probleem nog niet bekend is, meld dit dan aan Customer Support.

### De upgrade is niet uitgevoerd {#the-upgrade-did-not-run}

Voordat u de voorbereidingsstappen start, moet u eerst de **broninstantie** uitvoeren door deze uit te voeren met de opdracht java -jar aem-quickstart.jar. Dit is vereist om ervoor te zorgen dat het bestand quickstart.properties op de juiste wijze wordt gegenereerd. Als deze ontbreekt, werkt de upgrade niet. U kunt ook controleren of het bestand aanwezig is door onder `crx-quickstart/conf` de installatiemap van de broninstantie te kijken. Wanneer u AEM start om de upgrade uit te voeren, moet deze worden uitgevoerd met de opdracht java -jar aem-quickstart.jar. Als u begint met een beginscript, wordt AEM niet gestart in de upgrademodus.

### Pakketten en pakketten kunnen niet worden bijgewerkt {#packages-and-bundles-fail-to-update-}

Als pakketten niet tijdens de upgrade worden geïnstalleerd, worden de bundels in de pakketten ook niet bijgewerkt. Deze categorie van kwesties wordt gewoonlijk veroorzaakt door wanconfiguratie van de gegevensopslag. Zij zullen ook als **FOUT** en **WARN** berichten in error.log verschijnen. Aangezien in de meeste van deze gevallen standaardlogin kan ontbreken om te werken, kunt u CRXDE direct gebruiken om de configuratieproblemen te inspecteren en te vinden.

### Sommige AEM-bundels schakelen niet naar de actieve status {#some-aem-bundles-are-not-switching-to-the-active-state}

Als bundels niet beginnen zou u om het even welke ontevreden gebiedsdelen moeten controleren.

Als dit probleem zich voordoet, maar het is gebaseerd op een mislukte pakketinstallatie die ertoe heeft geleid dat bundels niet werden bijgewerkt, worden zij onverenigbaar geacht voor de nieuwe versie. Voor meer informatie over hoe te om dit problemen op te lossen, zie de Ontslagen van **Pakken en van Bundels hierboven bijwerken** .

Het wordt ook aanbevolen de bundellijst van een nieuwe AEM 6.5-instantie te vergelijken met de bijgewerkte versie om de bundels te detecteren die niet zijn bijgewerkt. Dit zal een nauwer bereik van verstrekken wat in de `error.log`te zoeken.

### Aangepaste bundels die niet overschakelen op de actieve staat {#custom-bundles-not-switching-to-the-active-state}

Als uw aangepaste bundels niet naar de actieve status overschakelen, is het zeer waarschijnlijk dat er code is die geen wijziging-API importeert. Dit zal meestal leiden tot ontevreden afhankelijkheden.

API die is verwijderd, moet worden gemarkeerd als afgekeurd in een van de vorige releases. In dit bericht vindt u mogelijk instructies over een directe migratie van uw code. Adobe streeft ernaar waar mogelijk semantische versies te maken, zodat de versies kunnen aangeven dat de wijzigingen zijn verbroken.

Het is ook het beste om te controleren of de verandering die het probleem heeft veroorzaakt absoluut noodzakelijk was en het zo niet terug te draaien. Controleer ook of de versieverhoging van de pakketexport meer dan nodig is, na strikte semantische versiebewerking.

### Gebruikersinterface van platform met storing {#malfunctioning-platform-ui}

In het geval van bepaalde functionaliteit UI die niet behoorlijk na de verbetering werkt, zou u eerst douaneoverlays van de interface moeten controleren. Sommige structuren zijn mogelijk gewijzigd en de overlay moet mogelijk worden bijgewerkt of is verouderd.

Controleer vervolgens of er JavaScript-fouten optreden die kunnen worden bijgehouden bij aangepaste, toegevoegde extensies die zijn gekoppeld aan clientbibliotheken. Hetzelfde kan gelden voor aangepaste CSS die problemen kan veroorzaken voor de AEM-lay-out.

Tot slot controleer misconfiguration dat Javascript niet zou kunnen behandelen. Dit is meestal het geval bij onjuist gedeactiveerde extensies.

### Onjuist functionerende aangepaste componenten, sjablonen of UI-extensies {#malfunctioning-custom-components-templates-or-ui-extensions}

In de meeste gevallen, zijn de worteloorzaken voor deze kwesties het zelfde als voor bundels die niet begonnen zijn of pakketten die niet met het enige verschil worden geïnstalleerd dat de kwesties beginnen op te duiken wanneer eerst het gebruiken van de componenten.

De manier om met onjuiste aangepaste code om te gaan is eerst rooktests uit te voeren om de oorzaak te achterhalen. Wanneer u het vindt, bekijk de aanbevelingen in deze [verbindingssectie] van het artikel voor manieren om hen te bevestigen.

### Ontbrekende aanpassingen onder /etc {#missing-customizations-under-etc}

`/apps` en `/libs` worden goed afgehandeld door de upgrade, maar wijzigingen onder `/etc` `/var/upgrade/PreUpgradeBackup` kunnen na de upgrade handmatig moeten worden hersteld. Controleer deze locatie op alle inhoud die handmatig moet worden samengevoegd.

### De parameters error.log en upgrade.log analyseren {#analyzing-the-error.log-and-upgrade.log}

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

### Contact opnemen met de ondersteuning van Adobe {#contacting-adobe-support}

Neem contact op met de ondersteuning van Adobe als u het advies op deze pagina hebt doorlopen en nog steeds problemen ziet. Om zoveel mogelijk informatie aan de steuningenieur te verstrekken die aan uw geval werkt, te zorgen gelieve ervoor om het upgrade.log dossier van uw verbetering te omvatten.
