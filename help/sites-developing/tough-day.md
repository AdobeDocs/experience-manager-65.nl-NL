---
title: Grove dag
description: De test van de Dag van de Stevige simuleert de dagelijkse lading van ongeveer 1000 auteurs in een worstcasescenario met alle verrichtingen die tezelfdertijd gebeuren.
topic-tags: testing
content-type: reference
exl-id: ceb9671c-57f9-4d81-94c0-0dbccd4d90a2
source-git-commit: f349c8fd9c370ba589d217cd3b1d0521ae5c5597
workflow-type: tm+mt
source-wordcount: '1825'
ht-degree: 0%

---

# Grove dag{#tough-day}

## Wat is Hoest Dag 2 {#what-is-tough-day}

&quot;Tough Day 2&quot; is een toepassing waarmee u de grenzen van uw AEM kunt testen. Het kan uit de doos met de standaardtestreeks worden gelopen of het kan worden gevormd om aan uw testende behoeften te passen. U kunt [deze opname](https://experienceleague.adobe.com/docs/events/experience-manager-gems-recordings/gems2017/aem-toughday2-stress-testing-benchmarking-tool.html) voor een presentatie van de aanvraag.

>[!CAUTION]
>
>Voor Dag 2 is Java™ 8 vereist.

## Hoe wordt Tough Day 2 uitgevoerd {#how-to-run-tough-day}

Download de nieuwste versie van Tough Day 2 van de [Opslagplaats Adobe](https://repo1.maven.org/maven2/com/adobe/qe/toughday2/). Nadat u de toepassing hebt gedownload, kunt u deze uit het vak uitvoeren door de `host` parameter. In het volgende voorbeeld wordt de AEM-instantie lokaal uitgevoerd, zodat de `localhost` waarde wordt gebruikt:

```xml
java -jar toughday2.jar --host=localhost
```

De standaardsuite die wordt uitgevoerd nadat de parameters zijn toegevoegd, krijgt de naam `toughday`. Het bevat de volgende gebruiksgevallen:

* Pagina&#39;s en live kopieën maken voor deze pagina&#39;s (inclusief rollouts)
* Homepage ophalen
* Zoekopdrachten uitvoeren in querybuilder
* Elementhiërarchieën maken
* Elementen verwijderen

De suite bevat 15% handelingen voor schrijven en 85% handelingen voor lezen.

Tough Day 2 installeert het standaard inhoudspakket om de suite-tests uit te voeren. Dit kan worden voorkomen door het instellen van de `installsamplecontent`parameter to `false`, maar vergeet niet dat u ook de standaardpaden moet wijzigen voor de tests die u wilt uitvoeren. Als de pot zonder parameters in werking wordt gesteld, toont Dag 2 [Help-informatie](/help/sites-developing/tough-day.md#getting-help).

U kunt de toepassing doorgaans gebruiken door dit patroon te volgen:

```xml
java -jar toughday2.jar [--help | --help_full | --help_tests | --help_publish]  [<global arguments> | <actions> | --runmode | --publishmode]
```

>[!NOTE]
>
>Dag 2 van de oude dag heeft geen opschoningsmaatregel. Als gevolg hiervan wordt aangeraden Dag 2 te gebruiken op een gekloonde staging-instantie en niet op de hoofdproductie-instantie. De testinstantie moet na de tests worden verwijderd.
>

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
   <td>Hiermee wordt algemene informatie afgedrukt, bijvoorbeeld: de beschikbare handelingen, vooraf gedefinieerde suites, uitvoeringsmodi en algemene parameters.</td>
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
   <td> —help —runmode/publishmode type=&lt;mode&gt;</td>
   <td>Hiermee geeft u informatie weer over de opgegeven run- of publicatiemodus.</td>
   <td><p>Java™ -jar toughday2.jar —help —runmode type=constantload</p> <p>Java™ -jar toughday2.jar —help —publishmode type=intervallen</p> </td>
  </tr>
  <tr>
   <td>—help —suite=&lt;suitename&gt;</td>
   <td>Vermeldt alle tests van een bepaalde reeks en hun respectieve configureerbare eigenschappen.</td>
   <td><br /> Java™ -jar toughday2.jar —help —suite=get_tests</td>
  </tr>
  <tr>
   <td> —help —tag=&lt;tag&gt;</td>
   <td><br /> Hiermee geeft u alle items weer met het opgegeven label.</td>
   <td>Java™ -jar toughday2.jar —help —tag=publish</td>
  </tr>
  <tr>
   <td>—help &lt;testclass publisherclass=""&gt;</td>
   <td><br /> Vermeldt alle configureerbare eigenschappen voor de bepaalde test of uitgever.</td>
   <td><p>Java™ -jar toughday2.jar —help UploadPDFTest</p> <p>Java™ -jar toughday2.jar —help CSVPublisher</p> </td>
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
| `--installsamplecontent=<Val>` | Installeert of slaat het standaard Tough Day 2 inhoudspakket over. | true | true of false |
| `--protocol=<Val>` | Het protocol dat voor de gastheer wordt gebruikt. | http | http of https |
| `--host=<Val>` | De hostnaam of IP die als doel zal worden ingesteld. |  |  |
| `--port=<Val>` | De poort van de host. | 4502 |  |
| `--user=<Val>` | De gebruikersnaam voor de instantie. | admin |  |
| `--password=<Val>` | Wachtwoord voor de opgegeven gebruiker. | admin |  |
| `--duration=<Val>` | De duur van de tests. Kan worden uitgedrukt in **s** seconden, **m** minuten, **h** de onze, en **d** dagen. | 1 quinquies |  |
| `--timeout=<Val>` | Hoe lang een test zal lopen alvorens het zal worden onderbroken en als ontbroken gemerkt. Uitgedrukt in seconden. | 180 |  |
| `--suite=<Val>` | De waarde kan één of een lijst (gescheiden door komma&#39;s) van vooraf bepaalde testsuites zijn. | nachtmerrie |  |
| `--configfile=<Val>` | Het doelafbeeldingsconfiguratiebestand. |  |  |
| `--contextpath=<Val>` | Contextpad van instantie. |  |  |
| `--loglevel=<Val>` | Het logniveau voor de Tough Day 2-motor. | INFO | ALLES, FOUTOPSPORING, INFO, WAARSCHUWING, FOUT, FATAAL, UIT |
| `--dryrun=<Val>` | Indien waar (true), wordt de resulterende configuratie afgedrukt en worden geen tests uitgevoerd. | false | true of false |

## Aanpassen {#customizing}

De aanpassing kan op twee manieren worden bereikt: bevel-lijn parameters of uw configuratiedossiers. **De dossiers van de configuratie worden gebruikt voor grote douanereeksen en zij treden de standaardparameters van Dag 2 van de Hoek met voeten. De bevel-lijn parameters treden zowel configuratiedossiers als standaardparameters met voeten.**

De enige manier om een testconfiguratie op te slaan is het in uw formaat te kopiëren.

### Een nieuwe test toevoegen {#adding-a-new-test}

Als u de standaardinstelling niet wilt gebruiken `toughday` kunt u een test naar keuze toevoegen met de `add` parameter. In de onderstaande voorbeelden ziet u hoe u de `CreateAssetTreeTest` test of door bevel-lijn parameters of een yaml configuratiedossier te gebruiken.

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

### Meerdere exemplaren van dezelfde test toevoegen  {#adding-multiple-instances-of-the-same-test}

U kunt ook meerdere exemplaren van dezelfde test toevoegen en uitvoeren, maar elke instantie moet een unieke naam hebben. De voorbeelden tonen hieronder hoe te om twee instanties van de zelfde test toe te voegen of door bevel-lijn parameters of een yaml configuratiedossier te gebruiken.

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

Als u een of meer testeigenschappen moet wijzigen, kunt u die eigenschap toevoegen aan de opdrachtregel of het originele configuratiebestand. Als u alle beschikbare testeigenschappen wilt weergeven, voegt u de opdracht `--help <TestClass/PublisherClass>` parameter aan de bevellijn, bijvoorbeeld:

```xml
java -jar toughday2.jar --help CreatePageTreeTest
```

Onthoud dat uw configuratiebestanden de standaardparameters van Dag 2 van Ononderbroken overschrijven en dat opdrachtregelparameters zowel de configuratiebestanden als de standaardwaarden overschrijven.

In de onderstaande voorbeelden ziet u hoe u de `template` eigenschap voor de `CreatePageTreeTest` test of door of bevel-lijn parameters of een yaml configuratiedossier te gebruiken.

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

U kunt een nieuwe test aan een vooraf bepaalde reeks toevoegen gebruikend `add` en het opgeven van de beoogde voorgedefinieerde suite.

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

Bestaande tests in een bepaalde suite kunnen ook opnieuw worden geconfigureerd met de `config`* *parameter. Geef ook de naam van de suite en de werkelijke naam van de test op (niet de naam van de klasse Test). U kunt de testnaam vinden in het dialoogvenster `name` eigenschap van de klasse Test. Voor meer informatie over het zoeken naar testeigenschappen leest u de [Testeigenschappen wijzigen](/help/sites-developing/tough-day.md#changing-the-test-properties) sectie.

In het voorbeeld onder de standaardelementtitel voor de `CreatePageTreeTest` (benoemd `UploadAsset`) is gewijzigd in &quot;NewAsset&quot;.

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

Ook, kunt u tests uit vooraf bepaalde reeksen of uitgevers van de standaardconfiguratie met het gebruik van verwijderen `exclude` parameter. Geef ook de naam van de suite en de werkelijke naam van de test op (niet de test C) `lass` naam). U kunt de testnaam vinden in het dialoogvenster `name` eigenschap van de testklasse. In het onderstaande voorbeeld wordt `CreatePageTreeTest` (benoemd `UploadAsset`) wordt verwijderd uit de toughday-suite.

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

Dag 2 van de tijd kan in één van de volgende wijzen lopen: **normaal** en **constante belasting**.

De **normaal** De uitvoermodus heeft twee parameters:

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

De **constante belasting** De looppaswijze verschilt van de normale looppaswijze door een constant aantal begonnen testuitvoeringen, eerder dan een constant aantal draden te produceren. U kunt het laden instellen met de parameter voor de uitvoeringsmodus met dezelfde naam.

### Selectie testen {#test-selection}

Het testselectieproces is hetzelfde voor beide uitvoermodi en het gaat als volgt: alle tests hebben een `weight` eigenschap, die de waarschijnlijkheid van uitvoering in een thread bepaalt. Als u bijvoorbeeld twee tests hebt, één met een gewicht van 5 en één met een gewicht van 10, is de kans dat de laatste twee keer zo groot is als de eerste.

Bovendien kunnen tests een `count` eigenschap, die het aantal uitvoeringen tot een bepaald aantal beperkt. Nadat dit aantal wordt overgegaan, zullen geen verdere uitvoeringen van de test voorkomen. Alle testinstanties die reeds lopen zullen de looppas zoals gevormd beëindigen. Het volgende voorbeeld toont hoe te om deze parameters of bij de bevellijn toe te voegen of door een yaml configuratiedossier te gebruiken.

```xml
java -jar toughday2.jar --host=localhost --add CreateAssetTreeTest weight=5 --add CreatePageTreeTest weight=10 count=100 --runmode=normal concurrency=20
```

of

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
>Als gevolg van parallelle uitvoeringen is het werkelijke aantal testuitvoeringen niet precies het bedrag dat is geconfigureerd in de `count` parameter. Verwacht een afwijking evenredig aan het aantal lopende draden (die door `concurrency parameter`).

### Droog {#dry-run}

Een droge looppas ontleedt alle bepaalde input (bevel-lijn parameters of config dossiers), die het met de gebreken samenvoegen en dan de resultaten. Geen van de tests wordt uitgevoerd.

```xml
java -jar toughday2.jar --host=localhost --suite=toughday --add CreatePageTreeTest --dryrun=true
```

## Uitvoer {#output}

Langzame Dag 2 output zowel testmetriek als logboeken. Lees de volgende secties voor meer informatie.

### Metrische gegevens testen {#test-metrics}

Op ruwe Dag 2 worden momenteel negen testmetriek gerapporteerd die u kunt evalueren. Statistieken met de **&#42;** Het symbool wordt alleen gemeld na geslaagde uitvoering:

| **Naam** | **Beschrijving** |
|---|---|
| Tijdstempel | Tijdstempel van de laatste voltooide testrun. |
| Geslaagd | Aantal succesvolle looppas. |
| Mislukt | Aantal mislukte looppas. |
| Min&#42; | Laagste uitvoeringstijd van de test. |
| Max&#42; | Hoogste duur van de uitvoering van de test. |
| Mediaan&#42; | Berekende mediane duur van alle testuitvoeringen. |
| Gemiddeld&#42; | Berekende gemiddelde duur van alle testuitvoeringen. |
| StdDev&#42; | De standaardafwijking. |
| 90p&#42; | 90 percentiel. |
| 99p&#42; | 99 percentiel. |
| 99,9p&#42; | 99,9 percentiel. |
| Reële doorvoer&#42; | Het aantal regels gedeeld door de verstreken uitvoeringstijd. |

Deze metriek wordt geschreven met behulp van uitgevers die met de `add` parameter (vergelijkbaar met het toevoegen van tests). Er zijn momenteel twee opties:

* **CSVPublisher** - de uitvoer bestaat uit een CSV-bestand.
* **ConsolePublisher** - de uitvoer wordt weergegeven in de console.

Standaard zijn beide uitgevers ingeschakeld.

Er zijn ook twee modi waarin de metriek wordt gerapporteerd:

* De **eenvoudig** publicatiemodus - hiermee worden de resultaten vanaf het begin van de uitvoering tot het moment van publicatie gerapporteerd.
* De **intervallen** publicatiemodus - hiermee worden de resultaten in een bepaald tijdpad gerapporteerd. U kunt het tijdframe instellen met de **interval** parameter publicatiemodus.

Het volgende voorbeeld toont hoe te om te vormen `intervals` parameter of bij de bevellijn of door een leeg configuratiedossier te gebruiken.

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

Tough Day 2 maakt een logmap in dezelfde map waarin u Dag 2 hebt uitgevoerd. Deze map bevat twee typen logbestanden:

* **toughday.log**: bevat berichten met betrekking tot de toepassingsstatus, foutopsporingsinformatie en globale berichten.
* **toughday_&lt;testname>.log**: berichten met betrekking tot de opgegeven test.

De logboeken worden niet overschreven, de verdere looppas voegt berichten aan de bestaande logboeken toe. De logboeken hebben verscheidene niveaus, voor meer informatie zie [loglevel-parameter.](#global-parameters).

<!--
#### Example Usage {#example-usage}

#### Known Issues {#known-issues}

[Get File](assets/toughday-6_1.jar)
-->
