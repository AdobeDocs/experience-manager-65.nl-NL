---
title: Dag
seo-title: Dag
description: De test van de Dag van de Stevige simuleert de dagelijkse lading van ongeveer 1000 auteurs in een worstcasescenario met alle verrichtingen die tezelfdertijd gebeuren.
seo-description: De test van de Dag van de Stevige simuleert de dagelijkse lading van ongeveer 1000 auteurs in een worstcasescenario met alle verrichtingen die tezelfdertijd gebeuren.
uuid: 1b672182-40f5-4580-b038-2e3c8fbfb8b7
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
discoiquuid: ea6b40fe-b6e1-495c-b34f-8815a4e2e42e
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Dag{#tough-day}

## Wat is Hoest Dag 2 {#what-is-tough-day}

&quot;Tough Day 2&quot; is een toepassing waarmee u de limieten van uw AEM-instantie kunt testen. Het kan uit de doos met de standaardtestreeks worden gelopen of het kan worden gevormd om aan uw testende behoeften te passen. U kunt [deze opname](https://docs.adobe.com/ddc/en/gems/Toughday2---A-new-and-improved-stress-testing-and-benchmarking-tool.html) bekijken voor een presentatie van de toepassing.

## Hoe wordt Tough Day 2 uitgevoerd {#how-to-run-tough-day}

Download de nieuwste versie van Tough Day 2 uit de [Adobe Repository](https://repo.adobe.com/nexus/content/repositories/releases/com/adobe/qe/toughday2/). Nadat u de toepassing hebt gedownload, kunt u deze uit het vak uitvoeren door de `host` parameter op te geven. In het volgende voorbeeld wordt de AEM-instantie lokaal uitgevoerd, zodat de `localhost` waarde wordt gebruikt:

```xml
java -jar toughday2.jar --host=localhost
```

De standaardreeks die na het toevoegen van de parameters loopt wordt genoemd `toughday`. Het bevat de volgende gebruiksgevallen:

* Pagina&#39;s en live kopieën maken voor deze pagina&#39;s (inclusief rollouts)
* Homepage ophalen
* Zoekopdrachten uitvoeren in querybuilder
* Elementhiërarchieën maken
* Elementen verwijderen

De suite bevat 15% handelingen voor schrijven en 85% handelingen voor lezen.

Tough Day 2 installeert het standaard inhoudspakket om de suite-tests uit te voeren. Dit kan worden vermeden door de `installsamplecontent`parameter te plaatsen aan `false`, maar herinner dat u ook de standaardwegen voor de tests zou moeten veranderen die u van plan bent te lopen. Als de pot zonder parameters in werking wordt gesteld, toont Tough Dag 2 de [hulpinformatie](/help/sites-developing/tough-day.md#getting-help).

In het algemeen kunt u de toepassing gebruiken door dit patroon te volgen:

```xml
java -jar toughday2.jar [--help | --help_full | --help_tests | --help_publish]  [<global arguments> | <actions> | --runmode | --publishmode]
```

>[!NOTE]
>
>Dag 2 van de oude dag heeft geen opschoonstap. Als gevolg hiervan wordt aangeraden Dag 2 te gebruiken op een gekloonde staging-instantie en niet op de hoofdproductie-instantie. De testinstantie moet na de tests worden verwijderd.


### Help opvragen {#getting-help}

Dag 2 van de tijd biedt een brede waaier van hulpopties die van de bevellijn kunnen worden betreden. Bijvoorbeeld:

```xml
java -jar toughday2.jar --help_full
```

In de onderstaande tabel vindt u de relevante Help-parameters.

<table>
 <tbody>
  <tr>
   <td><strong>Parameter</strong></td>
   <td><strong>Beschrijving</strong></td>
   <td><strong>Voorbeeld</strong></td>
  </tr>
  <tr>
   <td>—help</td>
   <td>Hiermee wordt algemene informatie afgedrukt, bijvoorbeeld: de beschikbare acties, de vooraf gedefinieerde suites, de uitvoeringsmodi en de algemene parameters.</td>
   <td> </td>
  </tr>
  <tr>
   <td>—help_publish</td>
   <td>Hiermee worden alle beschikbare uitgevers afgedrukt.</td>
   <td> </td>
  </tr>
  <tr>
   <td>—help_tests</td>
   <td>Drukt de testklassen en hun beschrijving af.</td>
   <td> </td>
  </tr>
  <tr>
   <td>—help_full</td>
   <td>Drukt alle bovenstaande, plus tests, uitgevers en suite-onderdelen af.</td>
   <td> </td>
  </tr>
  <tr>
   <td> —help —runmode/publishmode type=&lt;Mode&gt;</td>
   <td>Hiermee geeft u informatie weer over de opgegeven run- of publicatiemodus.</td>
   <td><p>java -jar toughday2.jar —help —runmode type=constantload</p> <p>java -jar toughday2.jar —help —publishmode type=intervallen</p> </td>
  </tr>
  <tr>
   <td>—help —suite=&lt;SuiteName&gt;</td>
   <td>Vermeldt alle tests van een bepaalde reeks en hun respectieve configureerbare eigenschappen.</td>
   <td><br /> java -jar toughday2.jar —help —suite=get_tests</td>
  </tr>
  <tr>
   <td> —help —tag=&lt;Tag&gt;</td>
   <td><br /> Hiermee geeft u alle items weer die de opgegeven tag hebben.</td>
   <td>java -jar toughday2.jar —help —tag=publish</td>
  </tr>
  <tr>
   <td>—help &lt;TestClass/PublisherClass&gt;</td>
   <td><br /> Vermeldt alle configureerbare eigenschappen voor de bepaalde test of uitgever.</td>
   <td><p>java -jar toughday2.jar —help UploadPDFTest</p> <p>java -jar toughday2.jar —help CSVPublisher</p> </td>
  </tr>
 </tbody>
</table>

### Algemene parameters {#global-parameters}

Dag 2 biedt globale parameters die de omgeving voor de tests instellen of veranderen. Deze omvatten de gastheer die wordt gericht, het havenaantal, het gebruikte protocol, gebruiker en wachtwoord voor de instantie en vele meer. Bijvoorbeeld:

```xml
java -jar toughday2.jar --host=host --protocol=https --port=4502 --duration=30m --dryrun=true
```

U vindt de relevante parameters in de onderstaande lijst:

| **Parameter** | **Beschrijving** | **Standaardwaarde** | **Mogelijke waarden** |
|---|---|---|---|
| `--installsamplecontent=<Val>` | Installeert of slaat het standaard Tough Day 2 inhoudspakket over. | true |  true of false |
| `--protocol=<Val>` | Het protocol dat voor de gastheer wordt gebruikt. | http | http of https |
| `--host=<Val>` | De hostnaam of IP die als doel zal worden ingesteld. |  |  |
| `--port=<Val>` | De poort van de host. | 4502 |  |
| `--user=<Val>` | De gebruikersnaam voor de instantie. |  beheerder |  |
| `--password=<Val>` | Wachtwoord voor de opgegeven gebruiker. |  beheerder |  |
| `--duration=<Val>` | De duur van de tests. Kan worden uitgedrukt in (**s**)seconden, (**m**)minuten, (**h**)uren en (**d**)dagen. | 1d |  |
| `--timeout=<Val>` | Hoe lang een test zal lopen alvorens het zal worden onderbroken en als ontbroken gemerkt. Uitgedrukt in seconden. | 180 |  |
| `--suite=<Val>` | De waarde kan één of een lijst (gescheiden door komma&#39;s) van vooraf bepaalde testsuites zijn. | nachtmerrie |  |
| `--configfile=<Val>` | Het doelafbeeldingsconfiguratiebestand. |  |  |
| `--contextpath=<Val>` | Contextpad van instantie. |  |  |
| `--loglevel=<Val>` | Het logniveau voor de Tough Day 2-motor. | INFO | ALLES, FOUTOPSPORING, INFO, WAARSCHUWING, FOUT, FATAAL, UIT |
| `--dryrun=<Val>` | Indien waar (true), wordt de resulterende configuratie afgedrukt en worden geen tests uitgevoerd. | false |  true of false |

## Aanpassen {#customizing}

De aanpassing kan op twee manieren worden bereikt: opdrachtregelparameters of normale configuratiebestanden. **De dossiers van de configuratie worden over het algemeen gebruikt voor grote douanereeksen en zij zullen de standaardparameters van Dag 2 van de Hoek met voeten treden. De de lijnparameters van het bevel treden zowel configuratiedossiers als standaardparameters met voeten.**

De enige manier om een testconfiguratie op te slaan is het in uw formaat te kopiëren. Voor extra details, zie deze configuratie [toughday.yaml](https://repo.adobe.com/nexus/service/local/repositories/releases/content/com/adobe/qe/toughday2/0.2.1/toughday2-0.2.1.yaml) en de voorbeelden van de yaml configuratie in de hieronder secties.

### Een nieuwe test toevoegen {#adding-a-new-test}

Als u niet de standaardreeks wilt gebruiken, kunt u een test van uw kiezen toevoegen door de `toughday` `add` parameter te gebruiken. De voorbeelden tonen hieronder hoe te om de `CreateAssetTreeTest` test toe te voegen of door de parameters van de bevellijn of een yaml configuratiedossier te gebruiken.

Door opdrachtregelparameters te gebruiken:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest
```

Door een geldig configuratiebestand te gebruiken:

```xml
globals:
  host : localhost
tests:
  - add : CreateAssetTreeTest
```

### Meerdere exemplaren van dezelfde test toevoegen {#adding-multiple-instances-of-the-same-test}

U kunt ook meerdere exemplaren van dezelfde test toevoegen en uitvoeren, maar elke instantie moet een unieke naam hebben. De voorbeelden tonen hieronder hoe te om twee instanties van de zelfde test toe te voegen of door bevellijnparameters of een yaml configuratiedossier te gebruiken.

Door opdrachtregelparameters te gebruiken:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest name=FirstAssetTree --add CreateAssetTreeTest name=SecondAssetTree
```

Door een geldig configuratiebestand te gebruiken:

```xml
globals:
  host : localhost
tests:
  - add : CreateAssetTreeTest
    properties:
      name : FirstAssetTree
  - add : CreateAssetTreeTest
    properties:
      name : SecondAssetTree
```

### De testeigenschappen wijzigen {#changing-the-test-properties}

Als u een of meer testeigenschappen moet wijzigen, kunt u die eigenschap toevoegen aan de opdrachtregel of het originele configuratiebestand. Om alle beschikbare testeigenschappen te zien voeg de `--help <TestClass/PublisherClass>` parameter aan de bevellijn toe, bijvoorbeeld:

```xml
java -jar toughday2.jar --help CreatePageTreeTest
```

Houd er rekening mee dat uw configuratiebestanden de standaardparameters van Dag 2 overschrijven en dat opdrachtregelparameters zowel de configuratiebestanden als de standaardwaarden overschrijven.

De voorbeelden tonen hieronder hoe te om het `template` bezit voor de `CreatePageTreeTest` test te veranderen of door of bevellijnparameters of een yaml configuratiedossier te gebruiken.

Door opdrachtregelparameters te gebruiken:

```xml
java -jar toughday2.jar --host=localhost --add CreatePageTreeTest template=/conf/toughday-templates/settings/wcm/templates/toughday-template
```

Door een geldig configuratiebestand te gebruiken:

```xml
globals:
  host : localhost
tests:
  - add : CreatePageTreeTest
    properties:
      template : /conf/toughday-templates/settings/wcm/templates/toughday-template
```

### Werken met vooraf gedefinieerde testsuites {#working-with-predefined-test-suites}

De voorbeelden tonen hieronder hoe te om een test aan een vooraf bepaalde reeks toe te voegen en hoe te om een bestaande test van een vooraf bepaalde reeks opnieuw te vormen en uit te sluiten.

U kunt een nieuwe test aan een vooraf bepaalde reeks toevoegen gebruikend de `add` parameter en het specificeren van de gerichte vooraf bepaalde reeks.

Door opdrachtregelparameters te gebruiken:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest
```

Door een geldig configuratiebestand te gebruiken:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - add : CreatePageTreeTest
```

Bestaande tests in een bepaalde suite kunnen ook opnieuw worden geconfigureerd met de parameter `config`* *. U moet ook de naam van de suite en de werkelijke naam van de test opgeven (niet de naam van de testklasse). U kunt de testnaam in het `name` bezit van de Klasse van de Test vinden. Lees voor meer informatie over het zoeken naar testeigenschappen de sectie [Testeigenschappen](/help/sites-developing/tough-day.md#changing-the-test-properties) wijzigen.

In het voorbeeld onder de standaardtitel van het element voor de `CreatePageTreeTest` (benoemd `UploadAsset`) wordt gewijzigd in &quot;NewAsset&quot;.

Door opdrachtregelparameters te gebruiken:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --config UploadAsset title=NewAsset
```

Door een geldig configuratiebestand te gebruiken:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - config : UploadAsset
    properties :
      title : NewAsset
```

Bovendien kunt u tests ook verwijderen uit vooraf gedefinieerde suites of uitgevers uit de standaardconfiguratie met behulp van de `exclude` parameter. U moet ook de naam van de suite en de werkelijke naam van de test opgeven (niet de `lass` naam van Test C). U kunt de testnaam in het `name` bezit van de testklasse vinden. In het onderstaande voorbeeld wordt de `CreatePageTreeTest` (benoemde `UploadAsset`) test verwijderd uit de toughday-suite.

Door opdrachtregelparameters te gebruiken:

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --exclude UploadAsset
```

Door een geldig configuratiebestand te gebruiken:

```xml
globals:
  host : localhost
  suite : toughday
tests:
  - exclude : UploadAsset
```

### Modi uitvoeren {#run-modes}

Dag 2 van de tijd kan in één van de volgende wijzen lopen: **normale** en **constante belasting**.

De **normale** uitvoeringsmodus heeft twee parameters:

* `concurrency` - gelijktijdige uitvoering staat voor het aantal threads dat op Tough Day 2 wordt uitgevoerd. Op deze draden, zullen de tests worden uitgevoerd tot of de duur of er geen meer uit te voeren tests is.

* `waittime` - de wachttijd tussen twee opeenvolgende testuitvoeringen op dezelfde draad. De waarde moet in milliseconden worden uitgedrukt.

In het onderstaande voorbeeld ziet u hoe u de parameters kunt toevoegen met behulp van een van de opdrachtregels:

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest --runmode=normal concurrency=20
```

of door een geldig configuratiebestand te gebruiken:

```xml
runmode:
  type : normal
  waittime : 300
  concurrency : 200
```

De **constante ladingloopwijze** verschilt van de normale looppaswijze door een constant aantal begonnen testuitvoeringen, eerder dan een constant aantal draden te produceren. U kunt het laden instellen met de parameter voor de uitvoeringsmodus met dezelfde naam.

### Selectie testen {#test-selection}

Het testselectieproces is hetzelfde voor beide uitvoermodi en gaat als volgt te werk: alle tests hebben een `weight` bezit, dat de waarschijnlijkheid van uitvoering in een draad bepaalt. Als we bijvoorbeeld twee tests hebben, één met een gewicht van 5 en één met een gewicht van 10, is de kans dat de laatste twee keer zo groot is als de eerste.

Bovendien kunnen tests een `count` eigendom hebben, waardoor het aantal executies tot een bepaald aantal wordt beperkt. Nadat dit aantal wordt overgegaan, zullen geen verdere uitvoeringen van de test voorkomen. Alle testinstanties die reeds lopen zullen de looppas zoals gevormd beëindigen. Het volgende voorbeeld toont hoe te om deze parameters of bij de bevellijn toe te voegen of door een yaml configuratiedossier te gebruiken.

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest weight=5 --add CreatePageTreeTest weight=10 count=100 --runmode=normal concurrency=20
```

or

```xml
- add : CreateAssetTreeTest
    properties :
      name : UploadAsset
      weight : 5
      base : 3
      foldertitle : IAmAFolder
      assettitle : IAmAnAsset
      count : 100
```

>[!NOTE]
>
>Wegens parallelle uitvoeringen, zal het daadwerkelijke aantal testlooppas niet precies de hoeveelheid zijn die in de `count` parameter wordt gevormd. Verwacht een afwijking evenredig aan het aantal lopende draden (die door `concurrency parameter`) worden gecontroleerd.

### Droog {#dry-run}

Een droge looppas ontleedt alle bepaalde input (bevellijnparameters of configuratiedossiers), die het met de gebreken samenvoegen en dan de resultaten uitvoert. Geen van de tests wordt uitgevoerd.

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest --dryrun=true
```

## Output {#output}

Langzame Dag 2 output zowel testmetriek als logboeken. Lees de volgende secties voor meer informatie.

### Metrisch testen {#test-metrics}

Op Tough Day 2 worden momenteel 9 testmetriek gerapporteerd die u kunt evalueren. Metrische gegevens met het symbool ***** worden alleen gerapporteerd nadat de uitvoering is gelukt:

| **Naam** | **Beschrijving** |
|---|---|
| Tijdstempel | Tijdstempel van de laatste voltooide testrun. |
| Geslaagd | Aantal succesvolle looppas. |
| Mislukt | Aantal mislukte looppas. |
| Min* | Laagste uitvoeringstijd van de test. |
| Max* | Hoogste duur van de uitvoering van de test. |
| Mediaan * | Berekende mediane duur van alle testuitvoeringen. |
| Gemiddelde* | Berekende gemiddelde duur van alle testuitvoeringen. |
| StdDev* | De standaardafwijking. |
| 90p* | 90 percentiel. |
| 99p* | 99 percentiel. |
| 99,9p* | 99,9 percentiel. |
| Reële doorvoer* | Het aantal regels gedeeld door de verstreken uitvoeringstijd. |

Deze metriek wordt geschreven met de hulp van uitgevers die met de `add` parameter (gelijkaardig aan het toevoegen van tests) kunnen worden toegevoegd. Er zijn momenteel twee opties:

* **CSVPublisher** - de uitvoer is een CSV-bestand.
* **ConsolePublisher** - de uitvoer wordt weergegeven in de console.

Standaard zijn beide uitgevers ingeschakeld.

Bovendien zijn er twee wijzen waarin de metriek worden gemeld:

* De **eenvoudige** publicatiemodus - rapporteert de resultaten vanaf het begin van de uitvoering tot het moment van publicatie.
* De publicatiemodus **voor intervallen** - rapporteert de resultaten in een bepaald tijdframe. U kunt het tijdkader met de parameter van de **interval** plaatsen publiceert wijze.

Het volgende voorbeeld toont hoe te om de `intervals` parameter of bij de bevellijn of door een yaml configuratiedossier te vormen.

Door opdrachtregelparameters te gebruiken:

```xml
java -jar toughday2.jar --host=localhost --add CreatePageTreeTest --publishmode type=intervals interval=10s
```

Door een geldig configuratiebestand te gebruiken:

```xml
publishmode:
     type : intervals
     interval : 10s
     tests:
        -add : CreatePageTreeTest
```

### Logboekregistratie {#logging}

Tough Day 2 maakt een logmap in dezelfde map als waar u Tough Day 2 hebt uitgevoerd. Deze map bevat twee typen logbestanden:

* **toughday.log**: bevat berichten met betrekking tot de toepassingsstatus, foutopsporingsinformatie en globale berichten.
* **day_&lt;testname>.log**: berichten met betrekking tot de opgegeven test.

De logboeken worden niet overschreven, de verdere looppas zal berichten aan de bestaande logboeken toevoegen. De logboeken hebben verscheidene niveaus, voor meer informatie zie ` [loglevel parameter](/help/sites-developing/tough-day.md#global-parameters)`.

#### Voorbeeldgebruik {#example-usage}

#### Bekende problemen {#known-issues}

[Bestand ophalen](assets/toughday-6_1.jar)
